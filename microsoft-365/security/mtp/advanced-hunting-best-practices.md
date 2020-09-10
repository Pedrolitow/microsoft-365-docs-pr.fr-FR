---
title: Meilleures pratiques de recherche avancée de la recherche dans Microsoft Threat Protection
description: Découvrez comment créer des requêtes de recherche rapide, efficace et sans erreur avec la chasse avancée
keywords: chasse aux menaces, recherche de menace, recherche sur les menaces informatiques, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, schéma, Kusto, éviter le délai d’attente, lignes de commande, ID de processus, optimiser, meilleures pratiques, analyser, joindre, Résumé
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 3ca475ef6dbdbd66af47216c4130d748788730c2
ms.sourcegitcommit: 41fd71ec7175ea3b94f5d3ea1ae2c8fb8dc84227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "47419131"
---
# <a name="advanced-hunting-query-best-practices"></a>Pratiques recommandées pour la requête de repérage avancé

**S’applique à :**
- Protection Microsoft contre les menaces

Appliquez ces recommandations pour obtenir des résultats plus rapidement et éviter les délais d’attente lors de l’exécution de requêtes complexes. Si vous souhaitez en savoir plus sur l’amélioration des performances de requête, veuillez consulter [Meilleures pratiques de requête Kusto](https://docs.microsoft.com/azure/kusto/query/best-practices).

## <a name="general-guidance"></a>Directives générales

- **Taille des nouvelles requêtes**: Si vous pensez qu’une requête renverra un jeu de résultats volumineux, évaluez-la d’abord à l’aide de l' [opérateur Count](https://docs.microsoft.com/azure/data-explorer/kusto/query/countoperator). Utilisez la [limite](https://docs.microsoft.com/azure/data-explorer/kusto/query/limitoperator) ou son synonyme `take` pour éviter les jeux de résultats volumineux.
- **Appliquer des filtres plus tôt**: appliquer des filtres de temps et d’autres filtres pour réduire le jeu de données, en particulier avant d’utiliser les fonctions de transformation et d’analyse, telles que [Substring ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/substringfunction), [Replace (](https://docs.microsoft.com/azure/data-explorer/kusto/query/replacefunction)), [Trim ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/trimfunction), [ToUpper ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/toupperfunction)ou [parse_json ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/parsejsonfunction). Dans l’exemple ci-dessous, la fonction d’analyse [extractjson ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/extractjsonfunction) est utilisée après que les opérateurs de filtrage ont réduit le nombre d’enregistrements.

    ```kusto
    DeviceEvents
    | where Timestamp > ago(1d)
    | where ActionType == "UsbDriveMount" 
    | where DeviceName == "user-desktop.domain.com"
    | extend DriveLetter = extractjson("$.DriveLetter", AdditionalFields)
     ```

- **Contenant les temps contient**— pour éviter de Rechercher inutilement des sous-chaînes dans des mots, utilisez l' `has` opérateur au lieu de `contains` . [En savoir plus sur les opérateurs de chaîne](https://docs.microsoft.com/azure/data-explorer/kusto/query/datatypes-string-operators)
- **Rechercher dans des colonnes spécifiques**: recherchez une colonne spécifique au lieu d’exécuter des recherches de texte intégral dans toutes les colonnes. N’utilisez pas `*` pour vérifier toutes les colonnes.
- Respect **de la casse pour la vitesse**— les recherches sensibles à la casse sont plus spécifiques et généralement plus performantes. Les noms des opérateurs de [chaîne](https://docs.microsoft.com/azure/data-explorer/kusto/query/datatypes-string-operators)respectant la casse, tels que `has_cs` et `contains_cs` , se terminent généralement par `_cs` . Vous pouvez également utiliser l’opérateur Equals avec respect de la casse `==` et non `~=` .
- **Parse, ne pas extraire**: dans la mesure du possible, utilisez l' [opérateur d’analyse](https://docs.microsoft.com/azure/data-explorer/kusto/query/parseoperator) ou une fonction d’analyse telle que [parse_json ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/parsejsonfunction). Évitez l' `matches regex` opérateur String ou la [fonction Extract ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/extractfunction), qui utilisent les deux l’expression régulière. Réservez l’utilisation de l’expression régulière pour des scénarios plus complexes. [En savoir plus sur les fonctions d’analyse](#parse-strings)
- **Filtrer les tables et non les expressions**: ne filtrez pas une colonne calculée si vous pouvez filtrer une colonne de table.
- **Aucun caractère de trois caractères**— Évitez de comparer ou de filtrer à l’aide de termes de trois caractères maximum. Ces termes ne sont pas indexés et leur correspondance nécessitera davantage de ressources.
- **Project de manière sélective**: Rendez vos résultats plus faciles à comprendre en ne projetant que les colonnes dont vous avez besoin. La projection de colonnes spécifiques avant l’exécution d’opérations [join](https://docs.microsoft.com/azure/data-explorer/kusto/query/joinoperator) ou similaires permet également d’améliorer les performances.

## <a name="optimize-the-join-operator"></a>Optimiser l' `join` opérateur
L' [opérateur Join](https://docs.microsoft.com/azure/data-explorer/kusto/query/joinoperator) fusionne les lignes de deux tables en faisant correspondre les valeurs dans les colonnes spécifiées. Appliquez ces conseils pour optimiser les requêtes qui utilisent cet opérateur.

- **Petit tableau à gauche**: l' `join` opérateur fait correspondre les enregistrements de la table à gauche de votre instruction JOIN aux enregistrements à droite. En faisant en sorte que le tableau est plus petit sur la gauche, moins d’enregistrements doivent être mis en correspondance, ce qui accélère la requête. 

    Dans le tableau ci-dessous, nous allons réduire le tableau `DeviceLogonEvents` de gauche pour ne traiter que trois appareils spécifiques avant de les joindre à des `IdentityLogonEvents` SID de compte.
 
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

- **Utilisez la version INNER JOIN**: la version de [jointure](https://docs.microsoft.com/azure/data-explorer/kusto/query/joinoperator#join-flavors) par défaut ou la [innerunique-Join](https://docs.microsoft.com/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#innerunique-join-flavor) déduplique les lignes du tableau de gauche en fonction de la clé de jointure avant de renvoyer une ligne pour chaque correspondance à la table de droite. Si la table de gauche comporte plusieurs lignes avec la même valeur pour la `join` clé, ces lignes seront dédoublées afin de laisser une seule ligne aléatoire pour chaque valeur unique.

    Ce comportement par défaut peut ignorer des informations importantes de la table de gauche qui peuvent fournir des informations utiles. Par exemple, la requête ci-dessous n’affiche qu’un seul e-mail contenant une pièce jointe particulière, même si la même pièce jointe a été envoyée à l’aide de plusieurs messages électroniques :

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256 
    ```

    Pour résoudre cette limitation, nous appliquons la saveur [INNER-JOIN](https://docs.microsoft.com/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor) en spécifiant `kind=inner` d’afficher toutes les lignes de la table de gauche avec des valeurs correspondantes à droite :
    
    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256 
    ```
- **Joindre des enregistrements à partir d’une fenêtre temporelle**: lors de l’examen des événements de sécurité, les analystes recherchent des événements associés qui se produisent sur la même période. Appliquer la même approche lorsque `join` vous utilisez également les performances en réduisant le nombre d’enregistrements à vérifier.
    
    La requête ci-dessous vérifie les événements de connexion dans les 30 minutes suivant la réception d’un fichier malveillant :

    ```kusto
    EmailEvents
    | where Timestamp > ago(7d)
    | where MalwareFilterVerdict == "Malware" 
    | project EmailReceivedTime = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0])
    | join (
    DeviceLogonEvents 
    | where Timestamp > ago(7d)
    | project LogonTime = Timestamp, AccountName, DeviceName
    ) on AccountName 
    | where (LogonTime - EmailReceivedTime) between (0min .. 30min)
    ```
- **Appliquer des filtres de temps sur les deux côtés**— même si vous n’examinez pas une fenêtre de temps spécifique, l’application de filtres de temps sur les tables gauche et droite peut réduire le nombre d’enregistrements à vérifier et améliorer les `join` performances. La requête ci-dessous s’applique `Timestamp > ago(1h)` aux deux tables afin qu’elle ne rejoigne que les enregistrements de la dernière heure :

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256 
    ```  

- **Utiliser des conseils pour les performances**: utilisez des conseils avec l' `join` opérateur pour indiquer au serveur principal de distribuer la charge lors de l’exécution d’opérations gourmandes en ressources. [En savoir plus sur les conseils de jointure](https://docs.microsoft.com/azure/data-explorer/kusto/query/joinoperator#join-hints)

    Par exemple, l' **[indicateur de lecture aléatoire](https://docs.microsoft.com/azure/data-explorer/kusto/query/shufflequery)** permet d’améliorer les performances des requêtes lors de la jointure de tables à l’aide d’une clé à haute cardinalité, une clé avec de nombreuses valeurs uniques, telles que la `AccountObjectId` requête ci-dessous :

    ```kusto
    IdentityInfo
    | where JobTitle == "CONSULTANT"
    | join hint.shufflekey = AccountObjectId 
    (IdentityDirectoryEvents
        | where Application == "Active Directory"
        | where ActionType == "Private data retrieval")
    on AccountObjectId 
    ```
    
    L' **[indication de diffusion](https://docs.microsoft.com/azure/data-explorer/kusto/query/broadcastjoin)** est utile lorsque le tableau de gauche est de petite taille (jusqu’à 100 000 enregistrements) et que la table de droite est extrêmement volumineuse. Par exemple, la requête ci-dessous tente de joindre quelques e-mails contenant des objets spécifiques avec _tous les_ messages contenant des liens dans la `EmailUrlInfo` table :

    ```kusto
    EmailEvents 
    | where Subject in ("Warning: Update your credentials now", "Action required: Update your credentials now")
    | join hint.strategy = broadcast EmailUrlInfo on NetworkMessageId 
    ```

## <a name="optimize-the-summarize-operator"></a>Optimiser l' `summarize` opérateur
L' [opérateur de synthèse](https://docs.microsoft.com/azure/data-explorer/kusto/query/summarizeoperator) agrège le contenu d’un tableau. Appliquez ces conseils pour optimiser les requêtes qui utilisent cet opérateur.

- **Rechercher des valeurs distinctes**: en règle générale, utilisez `summarize` pour rechercher des valeurs distinctes pouvant être répétitives. Il peut s’avérer inutile de l’utiliser pour agréger des colonnes qui n’ont pas de valeurs répétitives.

    Bien qu’un seul courrier électronique puisse faire partie de plusieurs événements, l’exemple ci-dessous n’est _pas_ une utilisation efficace de, `summarize` car un ID de message réseau pour un e-mail individuel est toujours fourni avec une adresse d’expéditeur unique.
 
    ```kusto
    EmailEvents  
    | where Timestamp > ago(1h)
    | summarize by NetworkMessageId, SenderFromAddress   
    ```
    L' `summarize` opérateur peut être facilement remplacé par, ce qui peut `project` produire des résultats identiques tout en consommant moins de ressources :

    ```kusto
    EmailEvents  
    | where Timestamp > ago(1h)
    | project NetworkMessageId, SenderFromAddress   
    ```
    L’exemple suivant est une utilisation plus efficace de `summarize` , car il peut y avoir plusieurs instances distinctes d’une adresse d’expéditeur qui envoient des messages électroniques à la même adresse de destinataire. Ces combinaisons sont moins distinctes et sont susceptibles d’avoir des doublons.

    ```kusto
    EmailEvents  
    | where Timestamp > ago(1h)
    | summarize by SenderFromAddress, RecipientEmailAddress   
    ```

- **Lecture aléatoire de la requête**, bien qu' `summarize` il soit préférable de l’utiliser dans des colonnes avec des valeurs répétitives, les mêmes colonnes peuvent également avoir _une haute cardinalité_ ou un grand nombre de valeurs uniques. Comme l' `join` opérateur, vous pouvez également appliquer l' [indicateur de lecture aléatoire](https://docs.microsoft.com/azure/data-explorer/kusto/query/shufflequery) `summarize` pour répartir la charge de traitement et éventuellement améliorer les performances lors de l’utilisation de colonnes à haute cardinalité.

    La requête ci-dessous utilise `summarize` pour compter le nombre d’adresses de messagerie de destinataires distinctes, qui peut s’exécuter dans des centaines de milliers dans les grandes organisations. Pour améliorer les performances, il intègre les `hint.shufflekey` éléments suivants :

    ```kusto
    EmailEvents  
    | where Timestamp > ago(1h)
    | summarize hint.shufflekey = RecipientEmailAddress count() by Subject, RecipientEmailAddress
    ```

## <a name="query-scenarios"></a>Scénarios de requête

### <a name="identify-unique-processes-with-process-ids"></a>Identifier les processus uniques avec des ID de processus
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
Plusieurs méthodes s’offrent à vous pour créer une ligne de commande pour accomplir une tâche. Par exemple, un agresseur peut faire référence à un fichier image sans chemin d’accès, sans extension de fichier, à l’aide de variables d’environnement ou de guillemets. L’agresseur peut également modifier l’ordre des paramètres ou ajouter plusieurs guillemets et espaces.

Pour créer des requêtes plus durables sur les lignes de commande, appliquez les pratiques suivantes :

- Identifiez les processus connus (par exemple, *net.exe* ou *psexec.exe*) en faisant correspondre les champs de nom de fichier au lieu de filtrer sur la ligne de commande proprement dite.
- Analyser les sections de ligne de commande à l’aide de la [fonction parse_command_line ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/parse-command-line) 
- Lors de l’interrogation des arguments de la ligne de commande, ne recherchez pas une correspondance exacte de plusieurs arguments non liés dans un certain ordre. Au lieu de cela, vous devez utiliser des expressions régulières ou utiliser plusieurs opérateurs de contenu séparés..
- Utilisez des correspondances non respectées de casse. Par exemple, utilisez `=~` ,, `in~` et `contains` au lieu de `==` , `in` , et `contains_cs` .
- Pour atténuer les techniques d’obscurcissement de ligne de commande, envisagez de supprimer des guillemets, de remplacer des virgules par des espaces et de remplacer plusieurs espaces consécutifs par un seul espace. Il existe des techniques d’obscurcissement plus complexes qui nécessitent d’autres approches, mais ces ajustements peuvent aider à résoudre les problèmes courants.

Les exemples suivants illustrent différentes façons de créer une requête qui recherche le fichier *net.exe* pour arrêter le service pare-feu « mpssvc » :

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

### <a name="ingest-data-from-external-sources"></a>Données ingérées provenant de sources externes
Pour incorporer des listes longues ou des tables volumineuses dans votre requête, utilisez l' [opérateur ExternalData](https://docs.microsoft.com/azure/data-explorer/kusto/query/externaldata-operator) pour les données à partir d’un URI spécifié. Vous pouvez obtenir des données à partir de fichiers TXT, CSV, JSON ou d' [autres formats](https://docs.microsoft.com/azure/data-explorer/ingestion-supported-formats). L’exemple ci-dessous montre comment vous pouvez utiliser la liste exhaustive des hachages SHA-256 fournis par MalwareBazaar (abuse.ch) pour vérifier les pièces jointes dans les e-mails :

```kusto
let abuse_sha256 = (externaldata(sha256_hash: string )
[@"https://bazaar.abuse.ch/export/txt/sha256/recent/"]
with (format="txt"))
| where sha256_hash !startswith "#"
| project sha256_hash;
abuse_sha256
| join (EmailAttachmentInfo 
| where Timestamp > ago(1d) 
) on $left.sha256_hash == $right.SHA256
| project Timestamp,SenderFromAddress,RecipientEmailAddress,FileName,FileType,
SHA256,MalwareFilterVerdict,MalwareDetectionMethod
```

### <a name="parse-strings"></a>Analyser des chaînes
Il existe différentes fonctions que vous pouvez utiliser pour gérer efficacement les chaînes qui nécessitent une analyse ou une conversion. 

| Chaîne | Fonction | Exemple d'utilisation |
|--|--|--|
| Lignes de commande | [parse_command_line ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/parse-command-line) | Extrayez la commande et tous les arguments. | 
| Paths | [parse_path ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/parsepathfunction) | Extraire les sections d’un fichier ou d’un chemin d’accès de dossier. |
| Numéros de version | [parse_version ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/parse-versionfunction) | Déconstruisez un numéro de version avec un maximum de quatre sections et jusqu’à huit caractères par section. Utilisez les données analysées pour comparer l’âge de la version. |
| Adresses IPv4 | [parse_ipv4 ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/parse-ipv4function) | Convertissez une adresse IPv4 en entier long. Pour comparer des adresses IPv4 sans les convertir, utilisez [ipv4_compare ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/ipv4-comparefunction). |
| Adresses IPv6 | [parse_ipv6 ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/parse-ipv6function)  | Convertissez une adresse IPv4 ou IPv6 en notation IPv6 canonique. Pour comparer des adresses IPv6, utilisez [ipv6_compare ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/ipv6-comparefunction). |

Pour en savoir plus sur toutes les fonctions d’analyse prises en charge, consultez la rubrique [about Kusto String Functions](https://docs.microsoft.com/azure/data-explorer/kusto/query/scalarfunctions#string-functions). 

## <a name="related-topics"></a>Voir aussi
- [Documentation du langage de requête Kusto](https://docs.microsoft.com/azure/data-explorer/kusto/query/)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les emails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
