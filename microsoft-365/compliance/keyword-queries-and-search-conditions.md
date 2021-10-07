---
title: Requêtes par mot clé et conditions de recherche pour eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SearchQueryLearnMore
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: c4639c2e-7223-4302-8e0d-b6e10f1c3be3
ms.custom:
- seo-marvel-apr2020
description: Découvrez les propriétés de messagerie et de document que vous pouvez rechercher à l’aide des outils de recherche eDiscovery Microsoft 365.
ms.openlocfilehash: 1cc0423ce80fa5fe212397d03a040a5166dea133
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60193266"
---
# <a name="keyword-queries-and-search-conditions-for-ediscovery"></a>Requêtes par mot clé et conditions de recherche pour eDiscovery

Cette rubrique décrit les propriétés de courrier électronique et de document que vous pouvez rechercher dans les éléments de courrier électronique et les conversations Microsoft Teams en Exchange Online, ainsi que les documents stockés sur des sites SharePoint et OneDrive Entreprise à l’aide des outils de recherche eDiscovery du Centre de conformité Microsoft 365. Cela inclut la recherche de contenu, core eDiscovery et Advanced eDiscovery (les recherches eDiscovery dans Advanced eDiscovery sont appelées *collections*). Vous pouvez également utiliser les cmdlets **\* -ComplianceSearch** dans le Centre de sécurité & conformité PowerShell pour rechercher ces propriétés. Cette rubrique décrit également :

- Utilisation d’opérateurs de recherche booléens, de conditions de recherche et d’autres techniques de requête de recherche pour affiner vos résultats de recherche.
- Recherche de types de données sensibles et de types de données sensibles personnalisés dans SharePoint et OneDrive Entreprise.
- Recherche de contenu de site partagé avec des utilisateurs extérieurs à votre organisation

Pour obtenir des instructions détaillées sur la création de différentes recherches eDiscovery, voir :

- [Recherche de contenu](content-search.md)
- [Rechercher du contenu dans Core eDiscovery](search-for-content-in-core-ediscovery.md)
- [Créer un brouillon de collection dans Advanced eDiscovery](create-draft-collection.md)

> [!NOTE]
> Les recherches de découverte électronique dans le Centre de conformité Microsoft 365 et les cmdlets **\* -ComplianceSearch** correspondantes dans le Centre de sécurité & conformité PowerShell utilisent le langage KQL (Keyword Query Language). Pour plus d’informations, consultez la référence [de la syntaxe keyword Query Language.](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

## <a name="searchable-email-properties"></a>Propriétés de messagerie utilisables dans une requête

Le tableau suivant répertorie les propriétés des messages électroniques qui peuvent être recherchés à l’aide des outils de recherche eDiscovery dans le Centre de conformité Microsoft 365 ou à l’aide de la cmdlet **New-ComplianceSearch** ou **Set-ComplianceSearch.** Il inclut un exemple de syntaxe  _property:value_ pour chaque propriété et une description des résultats de recherche renvoyés par ces exemples. Vous pouvez taper ces paires dans la zone de mots clés pour une  `property:value` recherche de découverte électronique.

> [!NOTE]
> Lors de la recherche de propriétés de messagerie, il n’est pas possible de rechercher des éléments dans lesquels la propriété spécifiée est vide ou vide. Par exemple, l’utilisation de la paire *property:value* de **subject:" »** pour rechercher des messages électroniques avec une ligne d’objet vide retourne zéro résultat. Cela s’applique également lors de la recherche des propriétés de site et de contact.

<br>

****

|Propriété|Description de la propriété|Exemples|Résultats de recherche renvoyés par les exemples|
|---|---|---|---|
|AttachmentNames|Nom des fichiers joints à un message électronique.|`attachmentnames:annualreport.ppt` <p> `attachmentnames:annual*` <br/> `attachmentnames:.pptx`|Messages comportant un fichier joint nommé annualreport.ppt. Dans le deuxième exemple, l’utilisation du caractère générique ( * ) renvoie des messages avec le mot « annual » dans le nom de fichier d’une pièce jointe. Le troisième exemple renvoie toutes les pièces jointes avec l’extension de fichier pptx.|
|Cci|Champ Bcc d’un message électronique. <sup>1</sup>|`bcc:pilarp@contoso.com` <p> `bcc:pilarp` <p> `bcc:"Pilar Pinilla"`|Tous les exemples renvoient des messages dont « Pilar Pinilla » est en copie carbone invisible.|
|Category|Catégories à rechercher. Les catégories peuvent être définies par les utilisateurs à l’aide Outlook ou Outlook sur le web (anciennement Outlook Web App). Les valeurs possibles sont les suivantes : <ul><li>blue<li>green<li>orange<li>purple<li>red<li>yellow</li></ul>|`category:"Red Category"`|Messages auxquels a été attribuée la catégorie « red » dans les boîtes aux lettres source.|
|Cc|Champ Cc d’un message électronique. <sup>1</sup>|`cc:pilarp@contoso.com` <p> `cc:"Pilar Pinilla"`|Dans les deux exemples, messages avec Pilar Pinilla spécifié dans le champ Cc.|
|Folderid|ID de dossier (GUID) d’un dossier de boîte aux lettres spécifique. Si vous utilisez cette propriété, n’oubliez pas d’effectuer une recherche dans la boîte aux lettres dans qui se trouve le dossier spécifié. Seul le dossier spécifié sera recherché. Les sous-dossiers du dossier ne seront pas recherchés. Pour rechercher des sous-dossiers, vous devez utiliser la propriété Folderid pour le sous-dossier que vous souhaitez rechercher. <p> Pour plus d’informations sur la recherche de la propriété Folderid et l’utilisation d’un script pour obtenir les ID de dossier pour une boîte aux lettres spécifique, voir Utiliser la recherche de contenu pour les [collections ciblées.](use-content-search-for-targeted-collections.md)|`folderid:4D6DD7F943C29041A65787E30F02AD1F00000000013A0000` <p> `folderid:2370FB455F82FC44BE31397F47B632A70000000001160000 AND participants:garthf@contoso.com`|Le premier exemple renvoie tous les éléments du dossier de boîte aux lettres spécifié. Le deuxième exemple renvoie tous les éléments du dossier de boîte aux lettres spécifié qui ont été envoyés ou reçus par garthf@contoso.com.|
|From|Expéditeur d'un message électronique.<sup>1</sup>|`from:pilarp@contoso.com` <p> `from:contoso.com`|Messages envoyés par l'utilisateur indiqué ou à partir d'un domaine spécifié.|
|HasAttachment|Indique si un message a une pièce jointe. Utilisez les valeurs **true** ou **false**.|`from:pilar@contoso.com AND hasattachment:true`|Messages envoyés par l’utilisateur spécifié qui ont des pièces jointes.|
|Importance|Importance d'un message électronique, que l'expéditeur peut préciser lors de l'envoi. Par défaut, les messages sont envoyés avec une importance normale, à moins que l'expéditeur préfère une importance **haute** ou **faible**.  |`importance:high` <p> `importance:medium` <p> `importance:low`|Messages marqués comme ayant une importance haute, normale ou faible.|
|IsRead|Indique si les messages ont été lus. Utilisez les valeurs **true** ou **false**.|`isread:true` <p> `isread:false`|Le premier exemple renvoie des messages dont la propriété IsRead a la valeur **True**. Le deuxième exemple renvoie des messages dont la propriété IsRead a la valeur **False**.|
|ItemClass|Utilisez cette propriété pour rechercher des types de données tiers spécifiques que votre organisation a importés Office 365. Utilisez la syntaxe suivante pour cette propriété :  `itemclass:ipm.externaldata.<third-party data type>*`|`itemclass:ipm.externaldata.Facebook* AND subject:contoso` <p> `itemclass:ipm.externaldata.Twitter* AND from:"Ann Beebe" AND "Northwind Traders"`|Le premier exemple renvoie les éléments Facebook qui contiennent le mot « contoso » dans la propriété Subject. Le deuxième exemple renvoie les éléments Twitter qui ont été publiés par Ann Beebe et qui contiennent l’expression de mot clé « Northwind Traders ». <p> Pour obtenir la liste complète des valeurs à utiliser pour les types de données tiers pour la propriété ItemClass, voir Utiliser la recherche de contenu pour rechercher des données tierces importées dans [Office 365](use-content-search-to-search-third-party-data-that-was-imported.md).|
|Kind|Type de message électronique à rechercher. Valeurs possibles : <p>  contacts <p>  docs <p>  email <p>  externaldata <p>  faxes <p>  im <p>  journals <p>  meetings <p>  microsoftteams (renvoie des éléments de conversations, de réunions et d’appels Microsoft Teams) <p>  notes <p>  posts <p>  rssfeeds <p>  tasks <p>  voicemail|`kind:email` <p> `kind:email OR kind:im OR kind:voicemail` <p> `kind:externaldata`|Le premier exemple renvoie des messages électroniques qui répondent aux critères de recherche. Le deuxième exemple renvoie des messages électroniques, des conversations de messagerie instantanée (y compris Skype Entreprise conversations et conversations dans Microsoft Teams) et des messages vocaux qui répondent aux critères de recherche. Le troisième exemple renvoie les éléments qui ont été importés dans des boîtes aux lettres dans Microsoft 365 à partir de sources de données tierces, telles que Twitter, Facebook et Cisco Jabber, qui répondent aux critères de recherche. Pour plus d’informations, [voir l’archivage](https://www.microsoft.com/?ref=go)de données tierces dans Office 365 .|
|Participants|Tous les champs de personnes dans un message électronique. Ces champs sont De, À, Cc et<sup>Cci. 1</sup>|`participants:garthf@contoso.com` <p> `participants:contoso.com`|Messages envoyés par ou envoyés à garthf@contoso.com. Le deuxième exemple renvoie tous les messages envoyés par ou envoyés à un utilisateur dans le domaine contoso.com.|
|Received|Date à laquelle un message électronique a été reçu par un destinataire.|`received:04/15/2016` <p> `received>=01/01/2016 AND received<=03/31/2016`|Messages reçus le 15 avril 2016. Le deuxième exemple renvoie tous les messages reçus entre le 1er janvier 2016 et le 31 mars 2016.|
|Destinataires|Tous les champs de destinataire dans un message électronique. Ces champs sont À, Cc et<sup>Cci. 1</sup>|`recipients:garthf@contoso.com` <p> `recipients:contoso.com`|Messages envoyés à garthf@contoso.com. Le deuxième exemple renvoie les messages envoyés à tous les destinataires dans le domaine contoso.com.|
|Sent|Date à laquelle un message électronique a été envoyé par l'expéditeur.|`sent:07/01/2016` <p> `sent>=06/01/2016 AND sent<=07/01/2016`|Messages envoyés à la date indiquée ou entre les dates spécifiées.|
|Size|Taille d'un élément, en octets.|`size>26214400` <p> `size:1..1048567`|Messages dont la taille est supérieure à 25 Mo. Le deuxième exemple renvoie les messages dont la taille est comprise entre 1 et 1 048 567 octets (1 Mo).|
|Subject|Texte de la ligne d'objet d'un message électronique. <p> **Remarque :** Lorsque vous utilisez la propriété Subject dans une requête, la recherche renvoie tous les messages dans lesquels la ligne d’objet contient le texte que vous recherchez. En d’autres termes, la requête ne retourne pas uniquement les messages qui ont une correspondance exacte. Par exemple, si vous recherchez, vos résultats incluront des messages dont l’objet est «  `subject:"Quarterly Financials"` Quarterly Financials 2018 ».|`subject:"Quarterly Financials"` <p> `subject:northwind`|Messages contenant l’expression « Quarterly Financials » n’importe où dans le texte de la ligne d’objet. Le deuxième exemple renvoie tous les messages contenant le mot « northwind » dans la ligne d'objet.|
|To|Champ À d'un message électronique.<sup>1</sup>|`to:annb@contoso.com` <p> `to:annb ` <br/> `to:"Ann Beebe"`|Tous les exemples renvoient les messages dans lesquels « Ann Beebe » est indiqué sur la ligne À.|
|

> [!NOTE]
> <sup>1 Pour la</sup> valeur d’une propriété de destinataire, vous pouvez utiliser l’adresse de messagerie (également appelée nom *d’utilisateur principal* ou UPN), le nom d’affichage ou l’alias pour spécifier un utilisateur. Par exemple, vous pouvez utiliser annb@contoso.com, annb ou « Ann Beebe » pour spécifier l'utilisateur Ann Beebe.

### <a name="recipient-expansion"></a>Développement des destinataires

Lorsque vous recherchez l’une des propriétés de destinataire (De, À, Cc, Cci, Participants et Destinataires), Microsoft 365 tente de développer l’identité de chaque utilisateur en le recherchant dans Azure Active Directory (Azure AD).  Si l’utilisateur est trouvé dans Azure AD, la requête est étendue pour inclure l’adresse de messagerie (ou UPN), l’alias, le nom d’affichage et LegacyExchangeDN de l’utilisateur. Par exemple, une requête telle que `participants:ronnie@contoso.com` étendue à `participants:ronnie@contoso.com OR participants:ronnie OR participants:"Ronald Nelson" OR participants:"<LegacyExchangeDN>"` .

Pour empêcher l’expansion des destinataires, ajoutez un caractère de caractères wild card (astérisque) à la fin de l’adresse e-mail et utilisez un nom de domaine réduit ; Par exemple, `participants:"ronnie@contoso*"` n’oubliez pas de entourer l’adresse e-mail de guillemets doubles.

Toutefois, sachez que le fait d’empêcher l’extension des destinataires dans la requête de recherche peut entraîner le non-retour d’éléments pertinents dans les résultats de la recherche. Les messages électroniques Exchange peuvent être enregistrés dans différents formats de texte dans les champs du destinataire. Le développement des destinataires vise à atténuer ce fait en renvoyant des messages qui peuvent contenir différents formats de texte. Par conséquent, le fait d’empêcher l’expansion des destinataires peut entraîner le non-renvoi par la requête de recherche de tous les éléments qui peuvent être pertinents pour votre examen.

> [!NOTE]
> Si vous devez examiner ou réduire les éléments renvoyés par une requête de recherche en raison de l’extension des destinataires, envisagez d’utiliser Advanced eDiscovery. Vous pouvez rechercher des messages (en profitant de l’extension des destinataires), les ajouter à un jeu à réviser, puis utiliser des requêtes ou des filtres de jeu de révision pour examiner ou affiner les résultats. Pour plus d’informations, [voir Collecter des données pour un cas](collecting-data-for-ediscovery.md) et interroger les données dans un jeu à [réviser.](review-set-search.md)

## <a name="searchable-site-properties"></a>Propriétés de site utilisables dans une requête

Le tableau suivant répertorie certaines des propriétés SharePoint et OneDrive Entreprise qui peuvent être recherchés à l’aide des outils de recherche eDiscovery dans le Centre de conformité Microsoft 365 ou à l’aide de la cmdlet **New-ComplianceSearch** ou **Set-ComplianceSearch.** Il inclut un exemple de syntaxe  _property:value_ pour chaque propriété et une description des résultats de recherche renvoyés par ces exemples.

Pour obtenir la liste complète des propriétés SharePoint qui peuvent être recherchés, voir Vue d’ensemble des propriétés gérées et d’analyse [dans SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Les propriétés marquées **avec un oui** dans la colonne **Queryable** peuvent être recherchés.

<br>

****

|Propriété|Description de la propriété|Exemple|Résultats de recherche renvoyés par les exemples|
|---|---|---|---|
|Auteur|Champ Auteur des documents Office (subsiste si un document est copié). Par exemple, si un utilisateur crée un document et l’envoie par courrier électronique à une autre personne qui le télécharge ensuite sur SharePoint, le document conserve l’auteur d’origine. N’oubliez pas d’utiliser le nom complet de l’utilisateur pour cette propriété.|`author:"Garth Fort"`|Tous les documents créés par Garth Fort.|
|ContentType|Le SharePoint type de contenu d’un élément, tel que l’élément, le document ou la vidéo.|`contenttype:document`|Tous les documents sont renvoyés.|
|Créé|Date de création d’un élément.|`created>=06/01/2016`|Tous les éléments créés le 1er juin 2016 ou après.|
|CreatedBy|Personne qui a créé ou chargé un élément. N’oubliez pas d’utiliser le nom complet de l’utilisateur pour cette propriété.|`createdby:"Garth Fort"`|Tous les éléments créés ou chargés par Garth Fort.|
|DetectedLanguage|Langue d’un élément.|`detectedlanguage:english`|Tous les éléments en anglais.|
|DocumentLink|Chemin d’accès (URL) d’un dossier spécifique sur SharePoint site OneDrive Entreprise site. Si vous utilisez cette propriété, n’oubliez pas de rechercher dans le site où se trouve le dossier spécifié. <p> Pour renvoyer les éléments situés dans les sous-dossiers du dossier que vous spécifiez pour la propriété documentlink, vous devez ajouter / à l’URL du \* dossier spécifié ; par exemple, `documentlink: "https://contoso.sharepoint.com/Shared Documents/*"` <p> <br/>Pour plus d’informations sur la recherche de la propriété documentlink et l’utilisation d’un script pour obtenir les URL de documentlink pour les dossiers sur un site spécifique, voir Utiliser la recherche de contenu pour les [collections](use-content-search-for-targeted-collections.md)ciblées.|`documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Private"` <p> `documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Shared with Everyone/*" AND filename:confidential`|Le premier exemple renvoie tous les éléments du dossier OneDrive Entreprise spécifié. Le deuxième exemple renvoie les documents dans le dossier de site spécifié (et tous les sous-dossiers) qui contiennent le mot « confidentiel » dans le nom de fichier.|
|FileExtension|Extension d’un fichier ; par exemple, docx, 1, pptx ou xlsx.|`fileextension:xlsx`|Tous Excel fichiers (Excel 2007 et ultérieures)|
|FileName|Nom d’un fichier.|`filename:"marketing plan"` <p> `filename:estimate`|Le premier exemple renvoie les fichiers contenant l’expression « marketing plan » (plan marketing) dans le titre. Le second exemple renvoie les fichiers contenant le mot « estimate » (devis) dans le nom du fichier.|
|LastModifiedTime|Date à laquelle un élément a été modifié pour la dernière fois.|`lastmodifiedtime>=05/01/2016` <p> `lastmodifiedtime>=05/10/2016 AND lastmodifiedtime<=06/1/2016`|Le premier exemple renvoie les éléments qui ont été modifiés le ou après le 1er mai 2016. Le deuxième exemple renvoie les éléments modifiés entre le 1er mai 2016 et le 1er juin 2016.|
|ModifiedBy|Personne qui a apporté les dernières modifications. N’oubliez pas d’utiliser le nom complet de l’utilisateur pour cette propriété.|`modifiedby:"Garth Fort"`|Tous les éléments qui ont été modifiés en dernier par Garth Fort.|
|Chemin|Chemin d’accès (URL) d’un site spécifique dans un site SharePoint ou OneDrive Entreprise site. <p> Pour renvoyer des éléments uniquement à partir du site spécifié, vous devez ajouter la fin à la fin de `/` l’URL ; par exemple, `path: "https://contoso.sharepoint.com/sites/international/"` <p> Pour renvoyer les éléments situés dans les dossiers du site que vous spécifiez dans la propriété path, vous devez ajouter à la fin de `/*` l’URL ; par exemple,  `path: "https://contoso.sharepoint.com/Shared Documents/*"` <p> **Remarque :** L’utilisation de la propriété pour rechercher OneDrive emplacements ne retourne pas les fichiers multimédias, tels que les fichiers .png, .tiff ou .wav, dans les résultats de `Path` la recherche. Utilisez une propriété de site différente dans votre requête de recherche pour rechercher des fichiers multimédias OneDrive dossiers. <br/>|`path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/"` <p> `path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/*" AND filename:confidential`|Le premier exemple renvoie tous les éléments du site OneDrive Entreprise spécifié. Le deuxième exemple renvoie les documents du site spécifié (et les dossiers du site) qui contiennent le mot « confidentiel » dans le nom de fichier.|
|SharedWithUsersOWSUser|Documents qui ont été partagés avec l’utilisateur spécifié et affichés sur la **page** Partagé avec moi sur le site OneDrive Entreprise’utilisateur. Ce sont des documents qui ont été explicitement partagés avec l’utilisateur spécifié par d’autres personnes de votre organisation. Lorsque vous exportez des documents qui correspondent à une requête de recherche qui utilise la propriété SharedWithUsersOWSUser, les documents sont exportés à partir de l’emplacement de contenu d’origine de la personne qui a partagé le document avec l’utilisateur spécifié. Pour plus d’informations, voir [Recherche de contenu de site partagé au sein de votre organisation.](#searching-for-site-content-shared-within-your-organization)|`sharedwithusersowsuser:garthf` <p> `sharedwithusersowsuser:"garthf@contoso.com"`|Les deux exemples retournent tous les documents internes qui ont été explicitement partagés avec Garth Fort et qui apparaissent sur la **page** Partagé avec moi dans le compte OneDrive Entreprise de Garth Fort.|
|Site|URL d’un site ou d’un groupe de sites de votre organisation.|`site:"https://contoso-my.sharepoint.com"` <p> `site:"https://contoso.sharepoint.com/sites/teams"`|Le premier exemple renvoie des éléments à partir des sites OneDrive Entreprise pour tous les utilisateurs de l’organisation. Le second exemple renvoie les éléments de tous les sites d’équipe.|
|Size|Taille d'un élément, en octets.|`size>=1` <p> `size:1..10000`|Le premier exemple renvoie les éléments dont la taille est supérieure à 1 octet. Le deuxième exemple renvoie les éléments dont la taille est comprise entre 1 et 10 000 octets.|
|Titre|Titre du document. La propriété Title est une métadonnées spécifiée dans Microsoft Office documents. Il est différent du nom de fichier du document.|`title:"communication plan"`|Tout document qui contient l’expression « communication plan » (plan de communication) dans la propriété de métadonnées du titre d’un document Office.|
|

## <a name="searchable-contact-properties"></a>Propriétés de contact utilisables dans une recherche

Le tableau suivant répertorie les propriétés de contact qui sont indexées et que vous pouvez rechercher à l’aide des outils de recherche eDiscovery. Il s’agit des propriétés que les utilisateurs peuvent configurer pour les contacts (également appelés contacts personnels) qui se trouvent dans le carnet d’adresses personnel de la boîte aux lettres d’un utilisateur. Pour rechercher des contacts, vous pouvez sélectionner les boîtes aux lettres à rechercher, puis utiliser une ou plusieurs propriétés de contact dans la requête de mot clé.

> [!TIP]
> Pour rechercher des valeurs qui contiennent des espaces ou des caractères spéciaux, utilisez des guillemets doubles ( » « ) pour contenir l’expression ; par exemple, `businessaddress:"123 Main Street"` .

<br>

****

|Propriété|Description de la propriété|
|---|---|
|BusinessAddress|Adresse dans la **propriété Adresse** professionnelle. La propriété est également appelée **adresse** de travail sur la page des propriétés du contact.|
|BusinessPhone|Numéro de téléphone dans l’une des propriétés de numéro **Téléphone** entreprise.|
|CompanyName|Nom dans la propriété **Company.**|
|Service|Nom dans la **propriété Department.**|
|DisplayName|Nom complet du contact. Il s’agit du nom dans la **propriété Nom** complet du contact.|
|EmailAddress|Adresse de toute propriété d’adresse de messagerie du contact. Les utilisateurs peuvent ajouter plusieurs adresses de messagerie pour un contact. L’utilisation de cette propriété retournerait les contacts qui correspondent à l’une des adresses de messagerie du contact.|
|FileAs|Fichier **en tant que** propriété. Cette propriété est utilisée pour spécifier la façon dont le contact est répertorié dans la liste des contacts de l’utilisateur. Par exemple, un contact peut être répertorié en tant que  *FirstName, LastName*  ou  *LastName,FirstName*.|
|GivenName|Nom de la **propriété First** Name.|
|HomeAddress|Adresse dans l’une des propriétés **d’adresse** du domicile.|
|HomePhone|Numéro de téléphone de l’une des propriétés **du** numéro de téléphone famille.|
|IMAddress|Propriété d’adresse de messagerie instantanée, qui est généralement une adresse de messagerie électronique utilisée pour la messagerie instantanée.|
|MiddleName|Nom dans la **propriété Deuxième** prénom.|
|MobilePhone|Numéro de téléphone de la **propriété Numéro** de téléphone mobile.|
|Nickname|Nom dans la **propriété Nickname.**|
|OfficeLocation|Valeur de la **propriété Office** ou **Office’emplacement.**|
|OtherAddress|Valeur de la propriété **d’adresse Other.**|
|Surname|Nom dans la **propriété Nom** de famille.|
|Titre|Titre de la **propriété Fonction.**|
|

## <a name="searchable-sensitive-data-types"></a>Types de données sensibles utilisables dans une requête

Vous pouvez utiliser les outils de recherche de découverte électronique dans le Centre de conformité Microsoft 365 pour rechercher des données sensibles, telles que des numéros de carte de crédit ou des numéros de sécurité sociale, qui sont stockées dans des documents sur des sites SharePoint et OneDrive Entreprise. Pour ce faire, vous pouvez utiliser la propriété et le nom (ou ID) d’un type d’informations sensibles dans une requête `SensitiveType` de mot clé. Par exemple, la requête renvoie `SensitiveType:"Credit Card Number"` les documents qui contiennent un numéro de carte de crédit. La requête renvoie les documents qui contiennent un numéro  `SensitiveType:"U.S. Social Security Number (SSN)"` de sécurité sociale aux États-Unis.

Pour consulter la liste des types d’informations sensibles que vous pouvez rechercher, consultez Classifications des données Types d’informations **sensibles** dans la \>  Centre de conformité Microsoft 365. Vous pouvez également utiliser la cmdlet **Get-DlpSensitiveInformationType** dans le Centre de sécurité & conformité PowerShell pour afficher une liste des types d’informations sensibles.

Pour plus d’informations sur la création de requêtes à l’aide de la propriété, voir `SensitiveType` [Form a query to find sensitive data stored on sites](form-a-query-to-find-sensitive-data-stored-on-sites.md).

### <a name="limitations-for-searching-sensitive-data-types"></a>Limitations pour la recherche de types de données sensibles

- Pour rechercher des types d’informations sensibles personnalisés, vous devez spécifier l’ID du type d’informations sensibles dans la `SensitiveType` propriété. L’utilisation du nom d’un type d’informations sensibles personnalisé (comme illustré dans l’exemple pour les types d’informations sensibles intégrés dans la section précédente) ne retourne aucun résultat. Utilisez la **colonne Publisher** sur la page **Types** d’informations sensibles dans le centre de conformité (ou la propriété **Publisher** dans PowerShell) pour différencier les types d’informations sensibles intégrés et personnalisés. Les types de données sensibles intégrés ont une valeur `Microsoft Corporation` de Publisher propriété. 

  Pour afficher le nom et l’ID des types de données sensibles personnalisés dans votre organisation, exécutez la commande suivante dans le Centre de sécurité & conformité PowerShell :

  ```powershell
  Get-DlpSensitiveInformationType | Where-Object {$_.Publisher -ne "Microsoft Corporation"} | FT Name,Id
  ```

  Ensuite, vous pouvez utiliser l’ID dans la propriété de recherche pour renvoyer les documents qui contiennent le type de données sensibles personnalisé `SensitiveType` ; par exemple, `SensitiveType:7e13277e-6b04-3b68-94ed-1aeb9d47de37`

- Vous ne pouvez pas utiliser les types d’informations sensibles et la propriété de recherche pour rechercher des données sensibles au `SensitiveType` repos dans Exchange Online boîtes aux lettres. Cela inclut les messages de conversation 1:1, les messages de conversation de groupe 1:N et les conversations de canal d’équipe dans Microsoft Teams, car tout ce contenu est stocké dans les boîtes aux lettres. Toutefois, vous pouvez utiliser des stratégies de protection contre la perte de données (DLP) pour protéger les données électroniques sensibles en transit. Pour plus d’informations, voir [En savoir plus sur la](dlp-learn-about-dlp.md) protection contre la perte de données et rechercher et rechercher des données [personnelles.](/compliance/regulatory/gdpr)

## <a name="search-operators"></a>Opérateurs de recherche

Les opérateurs de recherche booléens, tels que **AND,** **OR** et **NOT,** vous aident à définir des recherches plus précises en incluant ou en excluant des mots spécifiques dans la requête de recherche. D’autres techniques, telles que l’utilisation d’opérateurs de propriété (tels que ou ), de guillemets, de parenthèses et de `>=` caractères génériques, vous aident à affiner une requête `..` de recherche. Le tableau suivant répertorie les opérateurs disponibles pour restreindre ou élargir les résultats de recherche.

<br>

****

|Opérateur|Utilisation|Description|
|---|---|---|
|AND|keyword1 AND keyword2|Renvoie les éléments qui incluent tous les mots clés ou  `property:value` expressions spécifiés. Par exemple, retournerait tous les messages envoyés par Ann Beebe contenant le mot « northwind » dans  `from:"Ann Beebe" AND subject:northwind` la ligne d’objet. <sup>2</sup>|
|+|keyword1 + keyword2 + keyword3|Renvoie les éléments qui contiennent  *soit*  `keyword2` soit  `keyword3` *, et*  qui contiennent également  `keyword1`. Par conséquent, cet exemple équivaut à la requête  `(keyword2 OR keyword3) AND keyword1`.  <p> La requête (avec un espace après le symbole) est identique à `keyword1 + keyword2` **+** l’utilisation de **l’opérateur AND.** Cette requête est équivalente à  `"keyword1 + keyword2"` et renvoie des éléments contenant l'expression exacte  `"keyword1 + keyword2"`.|
|OR|keyword1 OR keyword2|Renvoie les éléments qui incluent un ou plusieurs des mots clés ou  `property:value` expressions spécifiés. <sup>2</sup>|
|NOT|keyword1 NOT keyword2 <p> NOT from:"Ann Beebe" <p> NOT kind:im|Exclut les éléments spécifiés par un mot clé ou une  `property:value` expression. Dans le deuxième exemple, les messages envoyés par Ann Beebe sont exclus. Le troisième exemple exclut les conversations de messagerie instantanée, telles que Skype Entreprise conversations enregistrées dans le dossier de boîte aux lettres Historique des conversations. <sup>2</sup>|
|-|keyword1 -keyword2|Identique à l'opérateur **NOT**. Cette requête renvoie donc les éléments qui contiennent et  `keyword1` excluraient les éléments qui contiennent  `keyword2` .|
|NEAR|keyword1 NEAR(n) keyword2|Renvoie les éléments qui incluent des mots proches les uns des autres, n étant égal au nombre de mots. Par exemple, renvoie tout élément où le mot « worst » est `best NEAR(5) worst` à cinq mots de « best ». Si aucun nombre n'est spécifié, la distance par défaut est de huit mots. <sup>2</sup>|
|:|property:value|Deux-points (:) dans la syntaxe spécifie que la valeur de la propriété à  `property:value` rechercher contient la valeur spécifiée. Par exemple,  `recipients:garthf@contoso.com` renvoie les messages envoyés à garthf@contoso.com.|
|=|property=value|Identique à l’opérateur **:.**|
|\<|property\<value|Indique que la propriété recherchée est inférieure à la valeur spécifiée.<sup>1</sup>|
|\>|property\>value|Indique que la propriété recherchée est supérieure à la valeur spécifiée.<sup>1</sup>|
|\<=|property\<=value|Indique que la propriété recherchée est inférieure ou égale à la valeur spécifiée.<sup>1</sup>|
|\>=|property\>=value|Indique que la propriété recherchée est supérieure ou égale à la valeur spécifiée.<sup>1</sup>|
|..|property:value1.. value2|Indique que la propriété recherchée est supérieure ou égale à value1 et inférieure ou égale à value2.<sup>1</sup>|
|"  "|"fair value" <p> subject:"Quarterly Financials"|Utilisez des guillemets doubles ( » « ) pour rechercher une expression ou un terme exact dans les requêtes de recherche et de mot  `property:value` clé.|
|\*|cat\* <p> subject:set\*|Recherche le préfixe (également appelé correspondance de *préfixe)* où un caractère générique ( * ) est placé à la fin d’un mot dans des mots clés ou `property:value` des requêtes. Dans les recherches de préfixe, la recherche renvoie des résultats avec des termes qui contiennent le mot suivi de zéro ou plusieurs caractères. Par exemple, renvoie les documents qui contiennent les mots « set », « setup » et « setting » (et d’autres mots qui commencent par « set ») dans le `title:set*` titre du document. <p> **Remarque :** Vous pouvez utiliser uniquement des recherches de préfixe ; par exemple, **cat _ ou \* *_* set \* *_. Les recherches de suffixe (_* \* chat**), les recherches de préfixe (**c \* t**) et les recherches de sous-string (**\* cat \***) ne sont pas pris en charge. <p> En outre, ajout d’un point ( \. ) en une recherche de préfixe modifie les résultats qui sont renvoyés. Cela est dû au fait qu’un point est traité comme un mot-clé. Par exemple, la recherche de **cat _ et la recherche de \* *_* \* cat.** retournent des résultats différents. Nous vous recommandons de ne pas utiliser de point dans une recherche de préfixe.|
|(  )| (fair OR free) AND from:contoso.com <p> (IPO OR initial) AND (stock OR shares) <p> (quarterly financials)|Les parenthèses regroupent des expressions booléennes, des éléments  `property:value` et des mots-clés. Par exemple,  `(quarterly financials)` renvoie les éléments contenant les mots « quarterly » et « financials ».  |
|

> [!NOTE]
> <sup>1</sup> Utilisez cet opérateur pour les propriétés ayant des valeurs de date ou des valeurs numériques.<br/> <sup>2</sup> Les opérateurs booléens doivent être en majuscules, par exemple **AND**. Si vous utilisez un opérateur en minuscules, tel que et **,** il sera traité comme un mot clé dans la requête de recherche.

## <a name="search-conditions"></a>Conditions de recherche

Vous pouvez ajouter des conditions à une requête de recherche pour affiner une recherche et renvoyer un ensemble de résultats plus affiné. Chaque condition ajoute une clause à la requête de recherche KQL qui est créée et exécutée lorsque vous démarrez la recherche.

[Conditions de propriétés communes ](#conditions-for-common-properties)

[Conditions pour les propriétés de messagerie](#conditions-for-mail-properties)

[Conditions des propriétés de document](#conditions-for-document-properties)

[Opérateurs utilisés avec des conditions](#operators-used-with-conditions)

[Instructions relatives à l’utilisation des conditions](#guidelines-for-using-conditions)

[Exemples](#examples-of-using-conditions-in-search-queries)

### <a name="conditions-for-common-properties"></a>Conditions de propriétés communes

Créez une condition avec des propriétés communes lorsque vous recherchez des boîtes aux lettres et des sites dans la même recherche. Le tableau suivant répertorie les propriétés disponibles à utiliser lors de l’ajout d’une condition.

<br>

****

|Condition|Description|
|---|---|
|Date|Pour la messagerie électronique, date à laquelle un message a été reçu par un destinataire ou envoyé par l’expéditeur. Pour les documents, date de la dernière modification d’un document.|
|Sender/Author|Pour la messagerie électronique, personne ayant envoyé le message. Pour les documents, personne mentionnée dans le champ Auteur des documents Office. Vous pouvez saisir plusieurs noms, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur **OR**.|
|Taille (en octets)|Pour la messagerie électronique et les documents, taille de l’élément (en octets).|
|Objet/Titre|Pour la messagerie électronique, texte de la ligne d’objet d’un message. Pour les documents, titre du document. Comme indiqué précédemment, la propriété Title est une métadonnées spécifiée dans Microsoft Office documents. Vous pouvez taper le nom de plusieurs sujet/titre, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur **OR**.|
|Étiquette de rétention|Pour les messages électroniques et les documents, les étiquettes de rétention qui ont été attribuées automatiquement aux messages et aux documents par les stratégies d’étiquette automatique ou les étiquettes de rétention qui ont été attribuées manuellement par les utilisateurs. Les étiquettes de rétention sont utilisées pour classifier les e-mails et les documents pour la gouvernance des informations et appliquer des règles de rétention basées sur les paramètres définis par l’étiquette. Vous pouvez taper une partie du nom de l’étiquette de rétention et utiliser un caractère générique ou taper le nom complet de l’étiquette. Pour plus d’informations sur les étiquettes de rétention, voir [En savoir plus sur les stratégies de rétention et les étiquettes de rétention.](retention.md)|
|

### <a name="conditions-for-mail-properties"></a>Conditions pour les propriétés de messagerie

Créez une condition à l’aide des propriétés de messagerie lors de la recherche dans des boîtes aux lettres ou des dossiers publics. Le tableau suivant répertorie les propriétés de messagerie que vous pouvez utiliser pour une condition. Ces propriétés sont un sous-ensemble des propriétés de messagerie précédemment décrites. Ces descriptions sont répétées pour votre commodité.

<br>

****

|Condition|Description|
|---|---|
|Type de message|Type de message à rechercher. Il s’agit de la même propriété que la propriété de messagerie Kind. Valeurs possibles : <ul><li>contacts</li><li>docs</li><li>email</li><li>externaldata</li><li>faxe</li><li>im</li><li>journals</li><li>meetings</li><li>microsoftteams</li><li>notes</li><li>posts</li><li>rssfeeds</li><li>tasks</li><li>voicemail</li></ul>|
|Participants|Tous les champs de personnes dans un message électronique. Ces champs sont De, À, Cc et Cci.|
|Type|Propriété de classe de message pour un élément de courrier électronique. Il s’agit de la même propriété que la propriété de messagerie ItemClass. Il s’agit également d’une condition à valeurs multiples. Pour sélectionner plusieurs classes de messages, maintenez la touche **Ctrl** en main, puis cliquez sur deux ou plusieurs classes de message dans la liste de listes que vous souhaitez ajouter à la condition. Chaque classe de message que vous sélectionnez dans la liste est connectée logiquement par l’opérateur **OR** dans la requête de recherche correspondante. <p> Pour obtenir la liste des classes de message (et leur ID de classe de message  correspondant) qui sont utilisées par Exchange et que vous pouvez sélectionner dans la liste des classes de message, voir Types d’éléments et Classes de [messages.](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes)|
|Received|Date à laquelle un message électronique a été reçu par un destinataire. Il s’agit de la même propriété que la propriété de messagerie Received.|
|Destinataires|Tous les champs de destinataire dans un message électronique. Ces champs sont À, Cc et Cci.|
|Expéditeur|Expéditeur d’un message électronique.|
|Sent|Date à laquelle un message électronique a été envoyé par l’expéditeur. Il s’agit de la même propriété que la propriété de messagerie Sent.|
|Subject|Texte de la ligne d'objet d'un message électronique.|
|À|Destinataire d’un message électronique dans le champ À.|
|

### <a name="conditions-for-document-properties"></a>Conditions des propriétés de document

Créez une condition à l’aide des propriétés de document lors de la recherche de documents sur SharePoint sites OneDrive Entreprise sites. Le tableau suivant répertorie les propriétés de document que vous pouvez utiliser pour une condition. Ces propriétés sont un sous-ensemble des propriétés de site précédemment décrites. Ces descriptions sont répétées pour votre commodité.

<br>

****

|Condition|Description|
|---|---|
|Auteur|Champ Auteur des documents Office (subsiste si un document est copié). Par exemple, si un utilisateur crée un document et l’envoie par courrier électronique à une autre personne qui le télécharge ensuite sur SharePoint, le document conserve l’auteur d’origine.|
|Titre|Titre du document. Cette propriété correspond aux métadonnées spécifiées dans les documents Office. Il est différent du nom de fichier du document.|
|Créé|Date de création d’un document.|
|Dernière modification|Date de la dernière modification apportée à un document.|
|Type de fichier|Extension d’un fichier ; par exemple, docx, one, pptx ou xlsx. Il s’agit de la même propriété que la propriété de site FileExtension. <p> **Remarque :** Si vous incluez une condition de type de fichier à l’aide de l’opérateur **Equals** ou **Equals dans** une requête de recherche, vous ne pouvez pas utiliser une recherche de préfixe (en incluant le caractère générique ( ) à la fin du type de fichier) pour renvoyer toutes les versions d’un type de \* fichier. Si vous le faites, le caractère générique sera ignoré. Par exemple, si vous incluez la condition, seuls les fichiers avec `Equals any of doc*` une extension `.doc` seront renvoyés. Les fichiers avec une extension `.docx` de ne seront pas renvoyés. Pour renvoyer toutes les versions d’un type de fichier, la paire *property:value* a été utilisée dans une requête de mot clé ; par exemple, `filetype:doc*` .|
|

### <a name="operators-used-with-conditions"></a>Opérateurs utilisés avec des conditions

Lorsque vous ajoutez une condition, vous pouvez sélectionner un opérateur pertinent par rapport au type de propriété pour la condition. Le tableau suivant décrit les opérateurs qui sont utilisés avec les conditions et répertorie l’équivalent utilisé dans la requête de recherche.

<br>

****

|Opérateur|Équivalent dans la requête|Description|
|---|---|---|
|Après|`property>date`|Utilisé avec les conditions de date. Renvoie les éléments qui ont été envoyés, reçus ou modifiés après la date spécifiée. |
|Avant|`property<date`|Utilisé avec les conditions de date. Renvoie les éléments qui ont été envoyés, reçus ou modifiés avant la date spécifiée.|
|Between|`date..date`|Utilisé avec les conditions de date et de taille. Lorsqu’il est utilisé avec une condition de date, renvoie les éléments qui ont été envoyés, reçus ou modifiés dans la plage de dates spécifiée. Lorsqu’il est utilisé avec une condition de taille, renvoie les éléments dont la taille est comprise dans la plage spécifiée.|
|Contient l’un des éléments|`(property:value) OR (property:value)`|Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui contiennent une partie d’une ou plusieurs valeurs de chaîne spécifiées.|
|Ne contient pas|`-property:value` <p> `NOT property:value`|Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui ne contiennent aucune partie de la valeur de chaîne spécifiée.|
|N’est pas égal à|`-property=value` <p> `NOT property=value`|Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui ne contiennent pas la chaîne spécifique.|
|Égal à|`size=value`|Renvoie les éléments qui sont égaux à la taille spécifiée. <sup>1</sup>|
|Est égal à l’un des éléments|`(property=value) OR (property=value)`|Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui correspondent exactement à une ou plusieurs valeurs de chaîne spécifiées.|
|Supérieur|`size>value`|Renvoie les éléments dont la propriété spécifiée est supérieure à la valeur spécifiée. <sup>1</sup>|
|Supérieur ou égal|`size>=value`|Renvoie les éléments dont la propriété spécifiée est supérieure ou égale à la valeur spécifiée. <sup>1</sup>|
|Moins|`size<value`|Renvoie les éléments supérieurs ou égaux à la valeur spécifique. <sup>1</sup>|
|Inférieur ou égal|`size<=value`|Renvoie les éléments supérieurs ou égaux à la valeur spécifique. <sup>1</sup>|
|Différent de|`size<>value`|Renvoie les éléments qui ne sont pas égaux à la taille spécifiée. <sup>1</sup>|
|

> [!NOTE]
> <sup>1</sup> Cet opérateur est disponible uniquement pour les conditions qui utilisent la propriété Size.

### <a name="guidelines-for-using-conditions"></a>Instructions relatives à l’utilisation des conditions

Gardez les points suivants à l’esprit lorsque vous utilisez des critères de recherche.

- Une condition est connectée à la requête de mot-clé (spécifiée dans la zone de mot-clé) sur le plan logique par l’opérateur **AND**. Cela signifie que les éléments doivent satisfaire la requête de mot-clé et la condition pour être inclus dans les résultats. C’est ainsi que les conditions contribuent à affiner vos résultats.

- Si vous ajoutez au moins deux conditions uniques à une requête de recherche (des conditions qui spécifient des propriétés différentes), celles-ci sont connectées sur le plan logique par l’opérateur **ET**. Cela signifie que seuls les éléments qui répondent à toutes les conditions (en plus des requêtes de mot-clé) sont renvoyés.

- Si vous ajoutez plusieurs conditions pour la même propriété, celles-ci sont connectées sur le plan logique par l’opérateur **OR**. Cela signifie que les éléments renvoyés sont ceux qui satisfont la requête de mot-clé et l’une des conditions. Par conséquent, les groupes de mêmes conditions sont connectés par l’opérateur **OR** et les ensembles de conditions uniques sont connectés par l’opérateur **AND**.

- Si vous ajoutez plusieurs valeurs (séparées par des virgules ou des points-virgules) à une condition unique, ces valeurs sont connectées par l’opérateur **OU**. Les éléments renvoyés sont ceux qui contiennent l’une des valeurs spécifiées pour la propriété dans la condition.

- La requête de recherche créée à l’aide de la zone de mots clés et des conditions s’affiche dans la **page** Recherche, dans le volet d’informations de la recherche sélectionnée. Dans une requête, tout ce qui se place à droite de la notation indique les conditions qui  `(c:c)` sont ajoutées à la requête.

- Les conditions ajoutent uniquement des propriétés à la requête de recherche . n’ajoutez pas d’opérateurs. C’est pourquoi la requête affichée dans le volet d’informations n’affiche pas les opérateurs à droite de la  `(c:c)` notation. KQL ajoute les opérateurs logiques (conformément aux règles précédemment expliquées) lors de l’exécution de la requête.

- Vous pouvez utiliser le contrôle glisser-déposer pour resquencer l’ordre des conditions. Cliquez sur le contrôle d’une condition et déplacez-la vers le haut ou vers le bas.

- Comme indiqué précédemment, certaines propriétés de condition vous permettent de taper plusieurs valeurs (séparées par des points-virgules). Chaque valeur est connectée logiquement par **l’opérateur OR** et entraîne la `(filetype=docx) OR (filetype=pptx) OR (filetype=xlsx)` requête. L’illustration suivante montre un exemple de condition avec plusieurs valeurs.

    ![Une condition avec plusieurs valeurs.](../media/SearchConditions1.png)

  > [!NOTE]
  > Vous ne pouvez pas ajouter plusieurs conditions (en cliquant sur **Ajouter une condition** pour la même propriété. Au lieu de cela, vous devez fournir plusieurs valeurs pour la condition (séparées par des points-virgules), comme illustré dans l’exemple précédent.

### <a name="examples-of-using-conditions-in-search-queries"></a>Exemples

Les exemples suivants illustrent la version basée sur l’interface graphique d’une requête de recherche avec des conditions, la syntaxe de requête de recherche affichée dans le volet d’informations de la recherche sélectionnée (qui est également renvoyée par la cmdlet **Get-ComplianceSearch)** et la logique de la requête KQL correspondante.

#### <a name="example-1"></a>Exemple 1

Cet exemple renvoie des documents sur SharePoint sites OneDrive Entreprise qui contiennent un numéro de carte de crédit et qui ont été modifiés pour la dernière fois avant le 1er janvier 2021.

**INTERFACE GRAPHIQUE**:

![Premier exemple de conditions de recherche.](../media/SearchConditions2.png)

**Syntaxe de requête de recherche**:

`SensitiveType:"Credit Card Number"(c:c)(lastmodifiedtime<2021-01-01)`

**Logique de requête de recherche**:

`SensitiveType:"Credit Card Number" AND (lastmodifiedtime<2021-01-01)`

Notez que dans la capture d’écran précédente, l’interface utilisateur de recherche confirme que la requête et la condition de mot clé sont connectées par **l’opérateur AND.**

#### <a name="example-2"></a>Exemple 2

Cet exemple renvoie des éléments de courrier électronique ou des documents qui contiennent le mot clé « report », qui ont été envoyés ou créés avant le 1er avril 2021 et qui contiennent le mot « northwind » dans le champ d’objet des messages électroniques ou dans la propriété title des documents. La requête exclut les pages Web qui répondent à d’autres critères de recherche.

**INTERFACE GRAPHIQUE**:

![Deuxième exemple de conditions de recherche.](../media/SearchConditions3.png)

**Syntaxe de requête de recherche**:

`report(c:c)(date<2021-04-01)(subjecttitle:"northwind")(-filetype:aspx)`

**Logique de requête de recherche**:

`report AND (date<2021-04-01) AND (subjecttitle:"northwind") NOT (filetype:aspx)`

#### <a name="example-3"></a>Exemple 3

Cet exemple renvoie des messages électroniques ou des réunions de calendrier qui ont été envoyés entre le 1/12/2019 et le 30/11/2020 et qui contiennent des mots qui commencent par « phone » ou « smartphone ».

**INTERFACE GRAPHIQUE**:

![Troisième exemple de conditions de recherche.](../media/SearchConditions4.png)

**Syntaxe de requête de recherche**:

`phone* OR smartphone*(c:c)(sent=2019-12-01..2020-11-30)(kind="email")(kind="meetings")`

**Logique de requête de recherche**:

`phone* OR smartphone* AND (sent=2029-12-01..2020-11-30) AND ((kind="email") OR (kind="meetings"))`

## <a name="special-characters"></a>Caractères spéciaux

Certains caractères spéciaux ne sont pas inclus dans l’index de recherche et ne sont donc pas utilisables dans une recherche. Cela inclut également les caractères spéciaux qui représentent les opérateurs de recherche dans la requête de recherche. Voici une liste des caractères spéciaux qui sont remplacés par un espace vide dans la requête de recherche réelle ou qui provoquent une erreur de recherche.

`+ - = : ! @ # % ^ & ; _ / ? ( ) [ ] { }`

## <a name="searching-for-site-content-shared-with-external-users"></a>Rechercher du contenu de site partagé avec des utilisateurs externes

Vous pouvez également utiliser les outils de recherche eDiscovery dans le centre de conformité pour rechercher des documents stockés sur des sites SharePoint et OneDrive Entreprise qui ont été partagés avec des personnes extérieures à votre organisation. Ainsi, vous pouvez identifier les informations sensibles ou confidentielles qui sont partagées en dehors de votre organisation. Vous pouvez le faire à l’aide  `ViewableByExternalUsers` de la propriété dans une requête de mot clé. Cette propriété renvoie des documents ou des sites qui ont été partagés avec des utilisateurs externes à l’aide de l’une des méthodes de partage suivantes :

- Invitation de partage qui nécessite que les utilisateurs se connectent à votre organisation en tant qu’utilisateur authentifié.
- Un lien invité anonyme, qui permet à toute personne ayant ce lien d’accéder à la ressource sans avoir à être authentifiée.

Voici quelques exemples :

- La requête renvoie tous les éléments qui ont été partagés avec des personnes extérieures à votre organisation et  `ViewableByExternalUsers:true AND SensitiveType:"Credit Card Number"` contiennent un numéro de carte de crédit.
- La requête renvoie une liste de documents sur tous les sites d’équipe de l’organisation qui ont  `ViewableByExternalUsers:true AND ContentType:document AND site:"https://contoso.sharepoint.com/Sites/Teams"` été partagés avec des utilisateurs externes.

> [!TIP]
> Une requête de recherche telle que peut renvoyer un grand nombre de fichiers  `ViewableByExternalUsers:true AND ContentType:document` .aspx dans les résultats de la recherche. Pour éliminer ces derniers (ou d’autres types de fichiers), vous pouvez utiliser la propriété pour exclure des types de fichiers  `FileExtension` spécifiques ; par exemple  `ViewableByExternalUsers:true AND ContentType:document NOT FileExtension:aspx` .

Qu’est-ce qui est considéré comme du contenu partagé avec des personnes extérieures à votre organisation ? Documents dans les sites SharePoint et OneDrive Entreprise de votre organisation qui sont partagés en envoyant une invitation de partage ou qui sont partagés dans des emplacements publics. Par exemple, les activités utilisateur suivantes produisent du contenu visible par les utilisateurs externes :

- Un utilisateur partage un fichier ou un dossier avec une personne extérieure à votre organisation.
- Un utilisateur crée et envoie un lien vers un fichier partagé à une personne extérieure à votre organisation. Ce lien permet à l’utilisateur externe d’ouvrir (ou de modifier) le fichier.
- Un utilisateur envoie une invitation de partage ou un lien invité à une personne extérieure à votre organisation pour ouvrir (ou modifier) un fichier partagé.

### <a name="issues-using-the-viewablebyexternalusers-property"></a>Problèmes à l’aide de la propriété ViewableByExternalUsers

Bien que la propriété indique si un document ou un site est partagé avec des utilisateurs externes, il existe quelques avertissements quant à ce que cette propriété fait et ne reflète  `ViewableByExternalUsers` pas. Dans les scénarios suivants, la valeur de la propriété ne sera pas mise à jour et les résultats d’une requête de recherche qui utilise cette propriété peuvent  `ViewableByExternalUsers` être imprécis.

- Modifications apportées à la stratégie de partage, telles que la stratégie de non-partage externe pour un site ou pour l’organisation. La propriété affiche toujours les documents partagés précédemment comme étant accessibles en externe, même si l’accès externe a peut-être été révoqué.
- Modifications apportées à l’appartenance aux groupes, telles que l’ajout ou la suppression d’utilisateurs externes Microsoft 365 groupes de sécurité Microsoft 365 groupes de sécurité. La propriété ne sera pas automatiquement mise à jour pour les éléments à qui le groupe a accès.
- Envoi d’invitations de partage à des utilisateurs externes où le destinataire n’a pas accepté l’invitation et n’a donc pas encore accès au contenu.

Dans ces scénarios, la propriété ne reflète pas l’état de partage actuel tant que le site ou la bibliothèque de documents n’a pas été  `ViewableByExternalUsers` réaxé et réindexé.

## <a name="searching-for-site-content-shared-within-your-organization"></a>Recherche de contenu de site partagé au sein de votre organisation

Comme indiqué précédemment, vous pouvez utiliser la propriété afin de rechercher des documents qui ont été  `SharedWithUsersOWSUser` partagés entre des personnes de votre organisation. Lorsqu’une personne partage un fichier (ou un dossier) avec un autre utilisateur au sein de votre organisation, un lien vers le fichier partagé apparaît sur la **page** Partagé avec moi dans le compte OneDrive Entreprise de la personne avec qui le fichier a été partagé. Par exemple, pour rechercher les documents qui ont été partagés avec Sara Davis, vous pouvez utiliser la requête  `SharedWithUsersOWSUser:"sarad@contoso.com"` . Si vous exportez les résultats de cette recherche, les documents d’origine (situés dans l’emplacement de contenu de la personne qui a partagé les documents avec Sara) seront téléchargés.

Les documents doivent être explicitement partagés avec un utilisateur spécifique pour être renvoyés dans les résultats de la recherche lors de l’utilisation de la  `SharedWithUsersOWSUser` propriété. Par exemple, lorsqu’une personne partage un document dans son compte OneDrive, elle a la possibilité de le partager avec n’importe qui (à l’intérieur ou à l’extérieur de l’organisation), de le partager uniquement avec des personnes au sein de l’organisation ou de le partager avec une personne spécifique. Voici une capture d’écran de **la** fenêtre Partager dans OneDrive, qui présente les trois options de partage.

![Seuls les fichiers partagés avec des personnes spécifiques sont renvoyés par une requête de recherche qui utilise la propriété SharedWithUsersOWSUser.](../media/469a4b61-68bd-4ab0-b612-ab6302973886.png)

Seuls les documents partagés à l’aide de la troisième option (partagé avec des personnes **spécifiques)** seront renvoyés par une requête de recherche qui utilise la  `SharedWithUsersOWSUser` propriété.

## <a name="searching-for-skype-for-business-conversations"></a>Recherche de Skype Entreprise conversations

Vous pouvez utiliser la requête de mot clé suivante pour rechercher spécifiquement du contenu dans Skype Entreprise conversations :

```powershell
kind:im
```

La requête de recherche précédente renvoie également des conversations à partir Microsoft Teams. Pour éviter cela, vous pouvez affiner les résultats de la recherche pour inclure uniquement Skype Entreprise conversations en utilisant la requête de mot clé suivante :

```powershell
kind:im AND subject:conversation
```

La requête de mot clé précédente exclut les conversations dans Microsoft Teams car les conversations Skype Entreprise sont enregistrées en tant que messages électroniques avec une ligne Objet qui commence par le mot « Conversation ».

Pour rechercher des Skype Entreprise conversations qui se sont produites dans une plage de dates spécifique, utilisez la requête de mot clé suivante :

```powershell
kind:im AND subject:conversation AND (received=startdate..enddate)
```

## <a name="character-limits-for-searches"></a>Limites de caractères pour les recherches

Il existe une limite de 4 000 caractères pour les requêtes de recherche lors de la recherche de contenu dans SharePoint sites et OneDrive comptes.
Voici comment le nombre total de caractères dans la requête de recherche est calculé :

- Les caractères de la requête de recherche par mot clé (y compris les champs utilisateur et de filtre) comptent pour cette limite.
- Les caractères d’une propriété d’emplacement (telles que les URL de tous les sites SharePoint ou des emplacements OneDrive en cours de recherche) sont comptabilisés dans cette limite.
- Caractères de tous les filtres d’autorisations de recherche appliqués à l’utilisateur exécutant le nombre de recherches par rapport à la limite.

Pour plus d’informations sur les limites de caractères, voir les limites de recherche [eDiscovery.](limits-for-content-search.md#search-limits)

> [!NOTE]
> La limite de 4 000 caractères s’applique à la recherche de contenu, à la découverte électronique principale et aux Advanced eDiscovery.

## <a name="search-tips-and-tricks"></a>Conseils et astuces pour la recherche

- Les recherches par mots clés ne sont pas sensibles à la cas. Par exemple, **cat** et **CAT** renvoient les mêmes résultats.

- Les opérateurs booléens **AND**, **OR**, **NOT** et **NEAR** doivent être en minuscules.

- Un espace entre deux mots-clés ou deux expressions  `property:value` revient au même que d'utiliser l'opérateur **AND**. Par exemple, renvoie  `from:"Sara Davis" subject:reorganization` tous les messages envoyés par Sara Davis qui contiennent le mot réorganisation dans la ligne d’objet.

- Utilisez une syntaxe qui correspond au `property:value` format. Les valeurs ne respectent pas la casse et doivent être collées à l'opérateur. S’il existe un espace, votre valeur prévue sera une recherche en texte intégral. Par exemple, recherche « pilarp » comme mot clé, plutôt que pour les messages envoyés `to: pilarp` à pilarp.

- Lorsque vous lancez une recherche sur une propriété de destinataire, telle que To, From, Cc ou Recipients, vous pouvez utiliser une adresse SMTP, un alias ou un nom d'affichage pour désigner un destinataire. Par exemple, vous pouvez saisir pilarp@contoso.com, pilarp ou « Pilar Pinilla ».

- Vous pouvez utiliser uniquement des recherches de préfixe ; par exemple, **cat _ ou \* *_* set \* *_. Les recherches de suffixe (_* \* chat**), les recherches de préfixe (**c \* t**) et les recherches de sous-string (**\* cat \***) ne sont pas pris en charge.

- Lorsque vous recherchez une propriété, utilisez des guillemets doubles ( » « ) si la valeur de recherche est constituée de plusieurs mots. Par exemple, renvoie les messages qui contiennent un budget dans la ligne d’objet et qui contiennent Q1 n’importe où dans le message ou dans l’une `subject:budget Q1` des propriétés du message.   `subject:"budget Q1"`L’utilisation renvoie tous les messages qui contiennent le budget **T1** n’importe où dans la ligne d’objet.

- Pour exclure de vos résultats de recherche du contenu marqué avec une certaine valeur de propriété, placez un signe moins (-) avant le nom de la propriété. Par exemple, `-from:"Sara Davis"` exclut tous les messages envoyés par Sara Davis.

- Vous pouvez exporter des éléments en fonction du type de message. Par exemple, pour exporter Skype conversations et conversations dans Microsoft Teams, utilisez la syntaxe `kind:im` . Pour renvoyer uniquement les messages électroniques, utilisez `kind:email` . Pour retourner des conversations, des réunions et des appels dans Microsoft Teams, utilisez `kind:microsoftteams` .

- Comme indiqué précédemment, lors de la recherche de sites, vous devez ajouter la fin de l’URL lorsque vous utilisez la propriété pour renvoyer uniquement les éléments `/` `path` d’un site spécifié. Si vous n’incluez pas la fin, les éléments d’un site avec un nom de chemin `/` d’accès similaire seront également renvoyés. Par exemple, si vous utilisez des éléments `path:sites/HelloWorld` provenant de sites nommés ou qui `sites/HelloWorld_East` `sites/HelloWorld_West` seraient également renvoyés. Pour renvoyer des éléments uniquement à partir du site HelloWorld, vous devez utiliser `path:sites/HelloWorld/` .
