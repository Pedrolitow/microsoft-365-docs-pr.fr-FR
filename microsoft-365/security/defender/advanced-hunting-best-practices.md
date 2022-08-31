---
title: Meilleures pratiques de requête de chasse avancées dans Microsoft 365 Defender
description: Découvrez comment construire des requêtes de chasse aux menaces rapides, efficaces et sans erreur avec une chasse avancée
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, schéma, kusto, éviter le délai d’expiration, lignes de commande, ID de processus, optimiser, meilleure pratique, analyser, joindre, résumer
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.openlocfilehash: da7d8966744d13b05504cecaba7824887c057028
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67483077"
---
# <a name="advanced-hunting-query-best-practices"></a>Pratiques recommandées pour la requête de repérage avancé

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Appliquez ces recommandations pour obtenir des résultats plus rapidement et éviter les délais d’expiration lors de l’exécution de requêtes complexes. Si vous souhaitez en savoir plus sur l’amélioration des performances de requête, veuillez consulter [Meilleures pratiques de requête Kusto](/azure/kusto/query/best-practices).

## <a name="understand-cpu-resource-quotas"></a>Comprendre les quotas de ressources d’UC
Selon sa taille, chaque locataire a accès à une quantité définie de ressources UC allouées pour l’exécution de requêtes de repérage avancées. Pour plus d’informations sur les différents paramètres d’utilisation, [consultez les quotas de chasse avancés et les paramètres d’utilisation](advanced-hunting-limits.md).

Après avoir exécuté votre requête, vous pouvez voir le temps d’exécution et son utilisation des ressources (Faible, Moyen, Élevé). La valeur élevée indique que la requête a pris plus de ressources à exécuter et qu’elle pourrait être améliorée pour retourner les résultats plus efficacement.

:::image type="content" source="../../media/resource-usage.png" alt-text="Détails de la requête sous l’onglet **Résultats** dans le portail Microsoft 365 Defender" lightbox="../../media/resource-usage.png":::

Les clients qui exécutent régulièrement plusieurs requêtes doivent suivre la consommation et appliquer les conseils d’optimisation de cet article pour réduire les interruptions résultant du dépassement des quotas ou des paramètres d’utilisation.

Regardez [Optimisation des requêtes KQL](https://www.youtube.com/watch?v=ceYvRuPp5D8) pour voir quelques-unes des méthodes les plus courantes pour améliorer vos requêtes.  

## <a name="general-optimization-tips"></a>Conseils généraux sur l’optimisation

- **Dimensionner de nouvelles requêtes** : si vous pensez qu’une requête retournera un jeu de résultats volumineux, évaluez-la en premier à l’aide de [l’opérateur count](/azure/data-explorer/kusto/query/countoperator). Utilisez [la limite](/azure/data-explorer/kusto/query/limitoperator) ou son synonyme `take` pour éviter les jeux de résultats volumineux.
- **Appliquer les filtres tôt** : appliquer des filtres de temps et d’autres filtres pour réduire le jeu de données, en particulier avant d’utiliser des fonctions de transformation et d’analyse, telles que [substring()](/azure/data-explorer/kusto/query/substringfunction), [replace()](/azure/data-explorer/kusto/query/replacefunction), [trim()](/azure/data-explorer/kusto/query/trimfunction), [toupper()](/azure/data-explorer/kusto/query/toupperfunction)ou [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). Dans l’exemple ci-dessous, la fonction d’analyse [extractjson()](/azure/data-explorer/kusto/query/extractjsonfunction) est utilisée après que les opérateurs de filtrage ont réduit le nombre d’enregistrements.

    ```kusto
    DeviceEvents
    | where Timestamp > ago(1d)
    | where ActionType == "UsbDriveMount"
    | where DeviceName == "user-desktop.domain.com"
    | extend DriveLetter = extractjson("$.DriveLetter", AdditionalFields)
     ```

- **Contient des battements** : pour éviter de rechercher inutilement des sous-chaînes dans des mots, utilisez l’opérateur `has` au lieu de `contains`. [En savoir plus sur les opérateurs de chaîne](/azure/data-explorer/kusto/query/datatypes-string-operators)
- **Rechercher dans des colonnes spécifiques** : recherchez dans une colonne spécifique au lieu d’exécuter des recherches en texte intégral sur toutes les colonnes. Ne pas utiliser `*` pour vérifier toutes les colonnes.
- **Respect de la casse pour la vitesse** : les recherches respectant la casse sont plus spécifiques et généralement plus performantes. Les noms des [opérateurs de chaîne sensibles](/azure/data-explorer/kusto/query/datatypes-string-operators) à la casse, tels que `has_cs` et `contains_cs`, se terminent généralement par `_cs`. Vous pouvez également utiliser l’opérateur `==` equals sensible à la casse au lieu de `=~`.
- **Analysez, n’extrayez pas** : dans la mesure du possible, utilisez [l’opérateur d’analyse](/azure/data-explorer/kusto/query/parseoperator) ou une fonction d’analyse comme [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). Évitez l’opérateur `matches regex` de chaîne ou la [fonction extract(),](/azure/data-explorer/kusto/query/extractfunction) qui utilisent toutes les deux une expression régulière. Réservez l’utilisation de l’expression régulière pour des scénarios plus complexes. [En savoir plus sur les fonctions d’analyse](#parse-strings)
- **Filtrer les tables et non les expressions** : ne filtrez pas sur une colonne calculée si vous pouvez filtrer sur une colonne de table.
- **Aucun terme à trois caractères** : évitez de comparer ou de filtrer à l’aide de termes comportant trois caractères ou moins. Ces termes ne sont pas indexés et leur correspondance nécessite plus de ressources.
- **Projeter de manière sélective** : facilitez la compréhension de vos résultats en projetant uniquement les colonnes dont vous avez besoin. La projection de colonnes spécifiques avant l’exécution de [jointures](/azure/data-explorer/kusto/query/joinoperator) ou d’opérations similaires permet également d’améliorer les performances.



## <a name="optimize-the-join-operator"></a>Optimiser l’opérateur `join`
[L’opérateur de jointure](/azure/data-explorer/kusto/query/joinoperator) fusionne des lignes à partir de deux tables en mettant en correspondance des valeurs dans des colonnes spécifiées. Appliquez ces conseils pour optimiser les requêtes qui utilisent cet opérateur.

- **Table plus petite à gauche** : l’opérateur `join` correspond aux enregistrements de la table située à gauche de votre instruction de jointure aux enregistrements à droite. Si la table est plus petite à gauche, moins d’enregistrements doivent être mis en correspondance, ce qui accélère la requête.

    Dans le tableau ci-dessous, nous réduisons la table `DeviceLogonEvents` de gauche pour ne couvrir que trois appareils spécifiques avant de la joindre avec `IdentityLogonEvents` des SID de compte.

    ```kusto
    DeviceLogonEvents
    | where DeviceName in ("device-1.domain.com", "device-2.domain.com", "device-3.domain.com")
    | where ActionType == "LogonFailed"
    | join
        (IdentityLogonEvents
        | where ActionType == "LogonFailed"
        | where Protocol == "Kerberos")
    on AccountSid
    ```

- **Utilisez la saveur de jointure interne** : la [saveur de jointure](/azure/data-explorer/kusto/query/joinoperator#join-flavors) par défaut ou la [jointure innerunique](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#innerunique-join-flavor) déduplique les lignes dans la table de gauche par la touche de jointure avant de retourner une ligne pour chaque correspondance à la table de droite. Si la table de gauche comporte plusieurs lignes avec la même valeur pour la `join` clé, ces lignes sont dédupliquées pour laisser une seule ligne aléatoire pour chaque valeur unique.

    Ce comportement par défaut peut exclure des informations importantes de la table de gauche qui peuvent fournir des insights utiles. Par exemple, la requête ci-dessous n’affiche qu’un seul e-mail contenant une pièce jointe particulière, même si cette même pièce jointe a été envoyée à l’aide de plusieurs messages électroniques :

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

    Pour résoudre cette limitation, nous appliquons la saveur [de jointure interne](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor) en spécifiant d’afficher `kind=inner` toutes les lignes du tableau de gauche avec des valeurs correspondantes à droite :

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```
- **Joindre des enregistrements à partir d’une fenêtre de temps** : lors de l’examen des événements de sécurité, les analystes recherchent les événements connexes qui se produisent autour de la même période. L’application de la même approche lors de l’utilisation `join` bénéficie également de performances en réduisant le nombre d’enregistrements à vérifier.

    La requête ci-dessous recherche les événements d’ouverture de session dans les 30 minutes suivant la réception d’un fichier malveillant :

    ```kusto
    EmailEvents
    | where Timestamp > ago(7d)
    | where ThreatTypes has "Malware"
    | project EmailReceivedTime = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0])
    | join (
    DeviceLogonEvents
    | where Timestamp > ago(7d)
    | project LogonTime = Timestamp, AccountName, DeviceName
    ) on AccountName
    | where (LogonTime - EmailReceivedTime) between (0min .. 30min)
    ```
- **Appliquer des filtres de temps des deux côtés** : même si vous n’examinez pas une fenêtre de temps spécifique, l’application de filtres de temps sur les tables de gauche et de droite peut réduire le nombre d’enregistrements à vérifier et améliorer `join` les performances. La requête ci-dessous `Timestamp > ago(1h)` s’applique aux deux tables afin qu’elles joignent uniquement les enregistrements de la dernière heure :

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

- **Utiliser des indicateurs de performances** : utilisez des indicateurs avec l’opérateur `join` pour indiquer au back-end de distribuer la charge lors de l’exécution d’opérations gourmandes en ressources. [En savoir plus sur les indicateurs de jointure](/azure/data-explorer/kusto/query/joinoperator#join-hints)

    Par exemple, **[l’indicateur de lecture aléatoire](/azure/data-explorer/kusto/query/shufflequery)** permet d’améliorer les performances des requêtes lors de la `AccountObjectId` jointure de tables à l’aide d’une clé à cardinalité élevée(clé avec de nombreuses valeurs uniques), comme dans la requête ci-dessous :

    ```kusto
    IdentityInfo
    | where JobTitle == "CONSULTANT"
    | join hint.shufflekey = AccountObjectId
    (IdentityDirectoryEvents
        | where Application == "Active Directory"
        | where ActionType == "Private data retrieval")
    on AccountObjectId
    ```

    **[L’indicateur de diffusion](/azure/data-explorer/kusto/query/broadcastjoin)** est utile lorsque la table de gauche est petite (jusqu’à 100 000 enregistrements) et que la table de droite est extrêmement grande. Par exemple, la requête ci-dessous tente de joindre quelques e-mails qui ont des sujets spécifiques avec _tous les_ messages contenant des liens dans le `EmailUrlInfo` tableau :

    ```kusto
    EmailEvents
    | where Subject in ("Warning: Update your credentials now", "Action required: Update your credentials now")
    | join hint.strategy = broadcast EmailUrlInfo on NetworkMessageId
    ```

## <a name="optimize-the-summarize-operator"></a>Optimiser l’opérateur `summarize`
[L’opérateur summarize](/azure/data-explorer/kusto/query/summarizeoperator) agrège le contenu d’une table. Appliquez ces conseils pour optimiser les requêtes qui utilisent cet opérateur.

- **Rechercher des valeurs distinctes** : en général, utilisez cette option `summarize` pour rechercher des valeurs distinctes qui peuvent être répétitives. Il peut être inutile de l’utiliser pour agréger des colonnes qui n’ont pas de valeurs répétitives.

    Bien qu’un seul e-mail puisse faire partie de plusieurs événements, l’exemple ci-dessous _n’est pas_ une utilisation efficace, car un ID de `summarize` message réseau pour un e-mail individuel est toujours fourni avec une adresse d’expéditeur unique.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by NetworkMessageId, SenderFromAddress
    ```
    L’opérateur `summarize` peut être facilement remplacé par `project`, ce qui donne potentiellement les mêmes résultats tout en consommant moins de ressources :

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | project NetworkMessageId, SenderFromAddress
    ```
    L’exemple suivant est une utilisation plus efficace, `summarize` car il peut y avoir plusieurs instances distinctes d’une adresse d’expéditeur qui envoient des e-mails à la même adresse de destinataire. Ces combinaisons sont moins distinctes et sont susceptibles d’avoir des doublons.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by SenderFromAddress, RecipientEmailAddress
    ```

- **Mélangez la requête** : bien qu’elle `summarize` soit mieux utilisée dans les colonnes avec des valeurs répétitives, les mêmes colonnes peuvent également avoir une _cardinalité élevée_ ou un grand nombre de valeurs uniques. Comme l’opérateur`join`, vous pouvez également appliquer l’indicateur `summarize` de [lecture aléatoire](/azure/data-explorer/kusto/query/shufflequery) pour distribuer la charge de traitement et potentiellement améliorer les performances lors de l’exploitation sur des colonnes avec une cardinalité élevée.

    La requête ci-dessous permet de compter l’adresse `summarize` e-mail du destinataire distinct, qui peut s’exécuter dans les centaines de milliers dans les grandes organisations. Pour améliorer les performances `hint.shufflekey`, il intègre :

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize hint.shufflekey = RecipientEmailAddress count() by Subject, RecipientEmailAddress
    ```



## <a name="query-scenarios"></a>Scénarios de requête

### <a name="identify-unique-processes-with-process-ids"></a>Identifier des processus uniques avec des ID de processus

Les ID de processus (PID) sont recyclés dans Windows et réutilisés pour les nouveaux processus. Ils ne peuvent pas être utilisés comme identificateurs uniques pour des processus spécifiques.

Pour obtenir un identificateur unique pour un processus sur un ordinateur spécifique, utilisez l’ID de processus conjointement avec l’heure de création du processus. Lorsque vous rejoignez ou résumez des données autour des processus, incluez des colonnes pour l’identificateur de l’ordinateur (`DeviceId` ou `DeviceName`), l’ID de processus (`ProcessId` ou `InitiatingProcessId`) et l’heure de création du processus (`ProcessCreationTime` ou `InitiatingProcessCreationTime`).

L’exemple de requête suivant trouve les processus qui accèdent à plus de 10 adresses IP via le port 445 (SMB), qui peut rechercher des partages de fichiers.

Exemples de requête :

```kusto
DeviceNetworkEvents
| where RemotePort == 445 and Timestamp > ago(12h) and InitiatingProcessId !in (0, 4)
| summarize RemoteIPCount=dcount(RemoteIP) by DeviceName, InitiatingProcessId, InitiatingProcessCreationTime, InitiatingProcessFileName
| where RemoteIPCount > 10
```

La requête se résume par `InitiatingProcessId` et `InitiatingProcessCreationTime` de sorte qu’elle examine un seul processus, sans mélanger plusieurs processus ayant le même ID de processus.

### <a name="query-command-lines"></a>Lignes de commande de requête
Plusieurs méthodes s’offrent à vous pour créer une ligne de commande pour accomplir une tâche. Par exemple, un attaquant peut référencer un fichier image sans chemin d’accès, sans extension de fichier, à l’aide de variables d’environnement ou avec des guillemets. L’attaquant peut également modifier l’ordre des paramètres ou ajouter plusieurs guillemets et espaces.

Pour créer des requêtes plus durables autour des lignes de commande, appliquez les pratiques suivantes :

- Identifiez les processus connus (par exemple *,net.exe* ou *psexec.exe*) en effectuant une correspondance sur les champs de nom de fichier, au lieu de filtrer sur la ligne de commande elle-même.
- Analyser des sections de ligne de commande à l’aide de la [fonction parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line)
- Lors de l’interrogation des arguments de la ligne de commande, ne recherchez pas une correspondance exacte de plusieurs arguments non liés dans un certain ordre. Au lieu de cela, vous devez utiliser des expressions régulières ou utiliser plusieurs opérateurs de contenu séparés..
- Utilisez des correspondances non respectées de casse. Par exemple, utilisez `=~`, `in~`et `contains` au lieu de `==`, `in`et `contains_cs`.
- Pour atténuer les techniques d’obfuscation de ligne de commande, envisagez de supprimer les guillemets, de remplacer les virgules par des espaces et de remplacer plusieurs espaces consécutifs par un seul espace. Il existe des techniques d’obfuscation plus complexes qui nécessitent d’autres approches, mais ces ajustements peuvent aider à résoudre les problèmes courants.

Les exemples suivants montrent différentes façons de construire une requête qui recherche le *fichiernet.exe* pour arrêter le service de pare-feu « MpsSvc » :

```kusto
// Non-durable query - do not use
DeviceProcessEvents
| where ProcessCommandLine == "net stop MpsSvc"
| limit 10

// Better query - filters on file name, does case-insensitive matches
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe") and ProcessCommandLine contains "stop" and ProcessCommandLine contains "MpsSvc"

// Best query also ignores quotes
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe")
| extend CanonicalCommandLine=replace("\"", "", ProcessCommandLine)
| where CanonicalCommandLine contains "stop" and CanonicalCommandLine contains "MpsSvc"
```

### <a name="ingest-data-from-external-sources"></a>Ingérer des données à partir de sources externes
Pour incorporer des listes longues ou des tables volumineuses dans votre requête, utilisez [l’opérateur externaldata](/azure/data-explorer/kusto/query/externaldata-operator) pour ingérer des données à partir d’un URI spécifié. Vous pouvez obtenir des données à partir de fichiers dans TXT, CSV, JSON ou [d’autres formats](/azure/data-explorer/ingestion-supported-formats). L’exemple ci-dessous montre comment utiliser la liste complète des hachages SHA-256 de programmes malveillants fournis par MalwareBazaar (abuse.ch) pour vérifier les pièces jointes sur les e-mails :

```kusto
let abuse_sha256 = (externaldata(sha256_hash: string)
[@"https://bazaar.abuse.ch/export/txt/sha256/recent/"]
with (format="txt"))
| where sha256_hash !startswith "#"
| project sha256_hash;
abuse_sha256
| join (EmailAttachmentInfo
| where Timestamp > ago(1d)
) on $left.sha256_hash == $right.SHA256
| project Timestamp,SenderFromAddress,RecipientEmailAddress,FileName,FileType,
SHA256,ThreatTypes,DetectionMethods
```

### <a name="parse-strings"></a>Analyser des chaînes
Il existe différentes fonctions que vous pouvez utiliser pour gérer efficacement les chaînes qui nécessitent une analyse ou une conversion.

| Chaîne | Fonction | Exemple d'utilisation |
|--|--|--|
| Lignes de commande | [parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line) | Extrayez la commande et tous les arguments. |
| Paths | [parse_path()](/azure/data-explorer/kusto/query/parsepathfunction) | Extrayez les sections d’un chemin d’accès de fichier ou de dossier. |
| Numéros de version | [parse_version()](/azure/data-explorer/kusto/query/parse-versionfunction) | Déconstruit un numéro de version avec jusqu’à quatre sections et jusqu’à huit caractères par section. Utilisez les données analysées pour comparer l’âge de la version. |
| Adresses IPv4 | [parse_ipv4()](/azure/data-explorer/kusto/query/parse-ipv4function) | Convertissez une adresse IPv4 en entier long. Pour comparer les adresses IPv4 sans les convertir, utilisez [ipv4_compare()](/azure/data-explorer/kusto/query/ipv4-comparefunction). |
| Adresses IPv6 | [parse_ipv6()](/azure/data-explorer/kusto/query/parse-ipv6function)  | Convertissez une adresse IPv4 ou IPv6 en notation IPv6 canonique. Pour comparer les adresses IPv6, utilisez [ipv6_compare()](/azure/data-explorer/kusto/query/ipv6-comparefunction). |

Pour en savoir plus sur toutes les fonctions d’analyse prises en charge, [consultez les fonctions de chaîne Kusto](/azure/data-explorer/kusto/query/scalarfunctions#string-functions).

>[!NOTE]
>Certaines tables de cet article peuvent ne pas être disponibles dans Microsoft Defender pour point de terminaison. [Activez Microsoft 365 Defender](m365d-enable.md) pour rechercher des menaces à l’aide de sources de données supplémentaires. Vous pouvez déplacer vos flux de travail de chasse avancés de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender en suivant les étapes de migration [des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Voir aussi
- [Documentation sur le langage de requête Kusto](/azure/data-explorer/kusto/query/)
- [Paramètres d’utilisation et de quotas](advanced-hunting-limits.md)
- [Gérer les erreurs de repérage avancées](advanced-hunting-errors.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)