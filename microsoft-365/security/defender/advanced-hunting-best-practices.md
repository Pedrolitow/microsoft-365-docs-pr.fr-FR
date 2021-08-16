---
title: Meilleures pratiques en matière de requête de recherche avancée Microsoft 365 Defender
description: Découvrez comment créer des requêtes de recherche de menaces rapides, efficaces et sans erreur avec le hunting avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema, kusto, avoid timeout, command lines, process id, optimize, best practice, parse, join, summarize
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 20a9206574565b2a02e1dcf57545e7b40619beec212daf29d6d2cc571e08dffb
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53867750"
---
# <a name="advanced-hunting-query-best-practices"></a>Pratiques recommandées pour la requête de repérage avancé

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Appliquez ces recommandations pour obtenir des résultats plus rapidement et éviter les délai d’accès lors de l’exécution de requêtes complexes. Si vous souhaitez en savoir plus sur l’amélioration des performances de requête, veuillez consulter [Meilleures pratiques de requête Kusto](/azure/kusto/query/best-practices).

## <a name="understand-cpu-resource-quotas"></a>Comprendre les quotas de ressources de l’UC
En fonction de sa taille, chaque client a accès à une quantité définie de ressources processeur allouées pour l’exécution de requêtes de recherche avancées. Pour plus d’informations sur les différentes limites de service, voir les quotas de recherche avancés et [les paramètres d’utilisation.](advanced-hunting-limits.md)

Les clients qui exécutent plusieurs requêtes régulièrement doivent suivre la consommation et appliquer les recommandations d’optimisation de cet article afin de minimiser les perturbations résultant du dépassement des quotas ou des paramètres d’utilisation.

## <a name="general-optimization-tips"></a>Conseils généraux d’optimisation

- **Dimensioniser les nouvelles requêtes**— Si vous pensez qu’une requête retournera un jeu de résultats important, évaluez-la d’abord à l’aide de [l’opérateur de nombre.](/azure/data-explorer/kusto/query/countoperator) Utilisez [limit](/azure/data-explorer/kusto/query/limitoperator) ou son synonyme pour éviter les `take` jeux de résultats importants.
- Appliquer des filtres tôt — Appliquer des filtres de temps et d’autres filtres pour réduire le jeu de données, en particulier avant d’utiliser des fonctions de transformation et d’analyse, telles que sous-string() , [replace()](/azure/data-explorer/kusto/query/replacefunction), [](/azure/data-explorer/kusto/query/substringfunction) [trim()](/azure/data-explorer/kusto/query/trimfunction), [toupper()](/azure/data-explorer/kusto/query/toupperfunction)ou [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). Dans l’exemple ci-dessous, la fonction d’recherche [extractjson()](/azure/data-explorer/kusto/query/extractjsonfunction) est utilisée après que les opérateurs de filtrage ont réduit le nombre d’enregistrements.

    ```kusto
    DeviceEvents
    | where Timestamp > ago(1d)
    | where ActionType == "UsbDriveMount"
    | where DeviceName == "user-desktop.domain.com"
    | extend DriveLetter = extractjson("$.DriveLetter", AdditionalFields)
     ```

- **A des frappes contient**— Pour éviter inutilement de rechercher des sous-strations dans des mots, utilisez l’opérateur `has` au lieu de `contains` . [En savoir plus sur les opérateurs de chaîne](/azure/data-explorer/kusto/query/datatypes-string-operators)
- **Rechercher dans des colonnes spécifiques**: recherchez dans une colonne spécifique plutôt que d’effectuer des recherches en texte intégral dans toutes les colonnes. Ne pas utiliser pour `*` vérifier toutes les colonnes.
- **En ce qui concerne la vitesse, les** recherches sensibles à la cas sont plus spécifiques et généralement plus performantes. Les noms des opérateurs de chaîne [sensibles](/azure/data-explorer/kusto/query/datatypes-string-operators)à la cas, tels que `has_cs` et , se `contains_cs` terminent généralement par `_cs` . Vous pouvez également utiliser l’opérateur d’égalité sensible à la cas `==` au lieu de `=~` .
- **Parse, n’extrayez** pas : [](/azure/data-explorer/kusto/query/parseoperator) dans la mesure du possible, utilisez l’opérateur d’parse_json() . [](/azure/data-explorer/kusto/query/parsejsonfunction) Évitez `matches regex` l’opérateur de chaîne [ou la fonction extract(),](/azure/data-explorer/kusto/query/extractfunction)qui utilisent toutes deux une expression régulière. Réservez l’utilisation d’une expression régulière pour des scénarios plus complexes. [En savoir plus sur les fonctions d’différentes fonctions](#parse-strings)
- **Filtrer les tableaux et** non les expressions : ne filtrez pas sur une colonne calculée si vous pouvez filtrer sur une colonne de tableau.
- **Aucun terme à trois caractères**: évitez de comparer ou de filtrer à l’aide de termes de trois caractères ou moins. Ces termes ne sont pas indexés et leur mise en correspondance nécessitera davantage de ressources.
- **Project sélective :** faciliter la compréhension de vos résultats en projetant uniquement les colonnes dont vous avez besoin. Le fait de projeter des colonnes spécifiques avant [l’exécution](/azure/data-explorer/kusto/query/joinoperator) d’opérations de jointage ou d’opérations similaires permet également d’améliorer les performances.

## <a name="optimize-the-join-operator"></a>Optimiser `join` l’opérateur
[L’opérateur de jointeur](/azure/data-explorer/kusto/query/joinoperator) fusionne les lignes de deux tables en correspondant aux valeurs des colonnes spécifiées. Appliquez ces conseils pour optimiser les requêtes qui utilisent cet opérateur.

- **Table plus petite à gauche —** L’opérateur fait la correspondance entre les enregistrements de la table sur le côté gauche de votre instruction de jointeur et les enregistrements de `join` droite. En ayant la table plus petite à gauche, moins d’enregistrements devront être mis en correspondance, ce qui accélère la requête.

    Dans le tableau ci-dessous, nous réduisons le tableau de gauche pour couvrir uniquement trois appareils spécifiques avant de le joindre par `DeviceLogonEvents` `IdentityLogonEvents` des SID de compte.

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

- Utilisez la jointure interne [](/azure/data-explorer/kusto/query/joinoperator#join-flavors) : la jointure par défaut ou la jointure interne déduplique les lignes dans le tableau de gauche par la touche de jointure avant de renvoyer une ligne pour chaque correspondance à la table de droite. [](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#innerunique-join-flavor) Si le tableau de gauche possède plusieurs lignes avec la même valeur pour la clé, ces lignes sont déduplicées pour laisser une seule ligne aléatoire pour `join` chaque valeur unique.

    Ce comportement par défaut peut laisser de côté les informations importantes du tableau de gauche qui peuvent fournir des informations utiles. Par exemple, la requête ci-dessous affiche uniquement un e-mail contenant une pièce jointe particulière, même si cette même pièce jointe a été envoyée à l’aide de plusieurs messages électroniques :

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

    Pour résoudre cette limitation, [](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor) nous appliquons la couleur jointeur interne en spécifiant d’afficher toutes les lignes du tableau de gauche avec les `kind=inner` valeurs correspondantes à droite :

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```
- **Joindre des enregistrements à partir d’une fenêtre de** temps — Lorsque vous examinez des événements de sécurité, les analystes recherchent les événements connexes qui se produisent autour de la même période. L’application de la même approche lors de l’utilisation de cette méthode permet également d’améliorer les performances en `join` réduisant le nombre d’enregistrements à vérifier.

    La requête ci-dessous recherche les événements d’logo dans les 30 minutes suivant la réception d’un fichier malveillant :

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
- Appliquer des filtres d’heure des deux côtés — Même si vous n’examinez pas une fenêtre de temps spécifique, l’application de filtres de temps à la fois dans les tables de gauche et de droite peut réduire le nombre d’enregistrements à vérifier et améliorer les `join` performances. La requête ci-dessous s’applique aux deux tables afin qu’elle joint uniquement les enregistrements de `Timestamp > ago(1h)` l’heure passée :

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

- **Utiliser des conseils pour les performances**: utilisez des conseils avec l’opérateur pour indiquer au système backend de répartir la charge lors de l’exécution d’opérations qui utilisent beaucoup `join` de ressources. [En savoir plus sur les conseils d’adhésion](/azure/data-explorer/kusto/query/joinoperator#join-hints)

    Par exemple, **[](/azure/data-explorer/kusto/query/shufflequery)** le conseil de mélange permet d’améliorer les performances des requêtes lors de la jointation de tables à l’aide d’une clé avec une cardinalité élevée (clé avec de nombreuses valeurs uniques), comme dans la requête ci-dessous `AccountObjectId` :

    ```kusto
    IdentityInfo
    | where JobTitle == "CONSULTANT"
    | join hint.shufflekey = AccountObjectId
    (IdentityDirectoryEvents
        | where Application == "Active Directory"
        | where ActionType == "Private data retrieval")
    on AccountObjectId
    ```

    **[L’indication de diffusion](/azure/data-explorer/kusto/query/broadcastjoin)** est utile lorsque le tableau de gauche est petit (jusqu’à 100 000 enregistrements) et que la table de droite est extrêmement grande. Par exemple, la requête ci-dessous tente de joindre quelques e-mails ayant des sujets spécifiques avec tous les _messages_ contenant des liens dans le `EmailUrlInfo` tableau :

    ```kusto
    EmailEvents
    | where Subject in ("Warning: Update your credentials now", "Action required: Update your credentials now")
    | join hint.strategy = broadcast EmailUrlInfo on NetworkMessageId
    ```

## <a name="optimize-the-summarize-operator"></a>Optimiser `summarize` l’opérateur
[L’opérateur de synthèse](/azure/data-explorer/kusto/query/summarizeoperator) agrège le contenu d’un tableau. Appliquez ces conseils pour optimiser les requêtes qui utilisent cet opérateur.

- **Rechercher des valeurs distinctes**: en général, utilisez cette recherche pour `summarize` trouver des valeurs distinctes qui peuvent être répétitives. Il peut être inutile de l’utiliser pour agréger des colonnes qui n’ont pas de valeurs répétitives.

    Bien qu’un seul e-mail puisse faire  partie de plusieurs événements, l’exemple ci-dessous n’est pas une utilisation efficace, car un ID de message réseau pour un message électronique individuel est toujours fourni avec une adresse d’expéditeur `summarize` unique.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by NetworkMessageId, SenderFromAddress
    ```
    L’opérateur peut être facilement remplacé par , ce qui donne potentiellement les mêmes résultats `summarize` `project` tout en consommant moins de ressources :

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | project NetworkMessageId, SenderFromAddress
    ```
    L’exemple suivant est une utilisation plus efficace, car il peut y avoir plusieurs instances distinctes d’une adresse d’expéditeur envoyant des messages électroniques `summarize` à la même adresse de destinataire. Ces combinaisons sont moins distinctes et sont susceptibles d’avoir des doublons.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by SenderFromAddress, RecipientEmailAddress
    ```

- **Mélangez la requête —** Bien qu’il soit préférable d’utiliser les colonnes avec des valeurs répétitives, les mêmes colonnes peuvent également avoir une cardinalité élevée ou un grand nombre `summarize` de valeurs uniques.  Comme l’opérateur, vous pouvez également appliquer le conseil de mélange avec pour répartir la charge de traitement et potentiellement améliorer les performances lorsque vous fonctionnez sur des colonnes avec `join` une [](/azure/data-explorer/kusto/query/shufflequery) `summarize` cardinalité élevée.

    La requête ci-dessous permet de compter des adresses de messagerie de destinataire distinctes, qui peuvent s’exécuter par centaines de `summarize` milliers dans les grandes organisations. Pour améliorer les performances, elle intègre `hint.shufflekey` :

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
| summarize RemoteIPCount=dcount(RemoteIP) by DeviceName, InitiatingProcessId
InitiatingProcessCreationTime, InitiatingProcessFileName
| where RemoteIPCount > 10
```

La requête se résume par `InitiatingProcessId` et `InitiatingProcessCreationTime` de sorte qu’elle examine un seul processus, sans mélanger plusieurs processus ayant le même ID de processus.

### <a name="query-command-lines"></a>Lignes de commande de requête
Plusieurs méthodes s’offrent à vous pour créer une ligne de commande pour accomplir une tâche. Par exemple, un attaquant peut faire référence à un fichier image sans chemin d’accès, sans extension de fichier, à l’aide de variables d’environnement ou de guillemets. L’attaquant peut également modifier l’ordre des paramètres ou ajouter plusieurs guillemets et espaces.

Pour créer des requêtes plus durables autour des lignes de commande, appliquez les pratiques suivantes :

- Identifiez les processus connus (tels que *net.exe* ou *psexec.exe*) en correspondant sur les champs de nom de fichier, au lieu de filtrer sur la ligne de commande elle-même.
- Parse command-line sections using the [parse_command_line() function](/azure/data-explorer/kusto/query/parse-command-line)
- Lors de l’interrogation des arguments de la ligne de commande, ne recherchez pas une correspondance exacte de plusieurs arguments non liés dans un certain ordre. Au lieu de cela, vous devez utiliser des expressions régulières ou utiliser plusieurs opérateurs de contenu séparés..
- Utilisez des correspondances non respectées de casse. Par exemple, utilisez `=~` , et à la place de , et `in~` `contains` `==` `in` `contains_cs` .
- Pour atténuer les techniques d’obfuscation de ligne de commande, envisagez de supprimer des guillemets, de remplacer des virgules par des espaces et de remplacer plusieurs espaces consécutifs par un espace unique. Il existe des techniques d’obfuscation plus complexes qui nécessitent d’autres approches, mais ces ajustements peuvent aider à résoudre les problèmes courants.

Les exemples suivants montrent différentes façons de construire une requête qui recherche le fichier *net.exe* pour arrêter le service de pare-feu « MpsSvc » :

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

### <a name="ingest-data-from-external-sources"></a>Ing d’ing de données provenant de sources externes
Pour incorporer des listes longues ou de grandes tables dans votre requête, utilisez l’opérateur [externaldata](/azure/data-explorer/kusto/query/externaldata-operator) pour ingère les données d’un URI spécifié. Vous pouvez obtenir des données à partir de fichiers au format TXT, CSV, JSON ou [d’autres formats.](/azure/data-explorer/ingestion-supported-formats) L’exemple ci-dessous montre comment vous pouvez utiliser la liste complète des codes de hoche SHA-256 des programmes malveillants fournis par MalwareBazaar (abuse.ch) pour vérifier les pièces jointes sur les e-mails :

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

### <a name="parse-strings"></a>Parse strings
Il existe différentes fonctions que vous pouvez utiliser pour gérer efficacement les chaînes qui doivent être traitées ou converties.

| Chaîne | Fonction | Exemple d'utilisation |
|--|--|--|
| Lignes de commande | [parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line) | Extraire la commande et tous les arguments. |
| Paths | [parse_path()](/azure/data-explorer/kusto/query/parsepathfunction) | Extraire les sections d’un chemin d’accès à un fichier ou un dossier. |
| Numéros de version | [parse_version()](/azure/data-explorer/kusto/query/parse-versionfunction) | Déconstruire un numéro de version avec jusqu’à quatre sections et jusqu’à huit caractères par section. Utilisez les données analyse pour comparer l’âge de la version. |
| Adresses IPv4 | [parse_ipv4()](/azure/data-explorer/kusto/query/parse-ipv4function) | Convertissez une adresse IPv4 en un long integer. Pour comparer les adresses IPv4 sans les convertir, [utilisez ipv4_compare()](/azure/data-explorer/kusto/query/ipv4-comparefunction). |
| Adresses IPv6 | [parse_ipv6()](/azure/data-explorer/kusto/query/parse-ipv6function)  | Convertissez une adresse IPv4 ou IPv6 en notation IPv6 canonique. Pour comparer les adresses IPv6, [utilisez ipv6_compare()](/azure/data-explorer/kusto/query/ipv6-comparefunction). |

Pour en savoir plus sur toutes les fonctions d’parsage prise en charge, lisez la suite sur les fonctions [de chaîne Kusto.](/azure/data-explorer/kusto/query/scalarfunctions#string-functions)

>[!NOTE]
>Certains tableaux de cet article peuvent ne pas être disponibles dans Microsoft Defender pour Endpoint. [Activer Microsoft 365 Defender](m365d-enable.md) pour la recherche de menaces à l’aide de sources de données plus nombreuses. Vous pouvez déplacer vos flux de travail de recherche avancée de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender en suivant les étapes de la procédure de migration des requêtes de recherche avancée à partir de Microsoft Defender pour le point de [terminaison.](advanced-hunting-migrate-from-mde.md)

## <a name="related-topics"></a>Sujets connexes
- [Documentation sur le langage de requête Kusto](/azure/data-explorer/kusto/query/)
- [Paramètres d’utilisation et de quotas](advanced-hunting-limits.md)
- [Gérer les erreurs de recherche avancée](advanced-hunting-errors.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)