---
title: Utiliser la recherche de contenu pour rechercher des données importées tierces
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection: M365-security-compliance
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: ec2677ff-c4d7-4363-a9e7-22c80e015688
description: Utilisez l’outil eDiscovery de recherche de contenu pour rechercher des éléments importés dans des boîtes aux lettres dans Microsoft 365 à partir d’une source de données tierce en créant des requêtes.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 916a780bccc3f24d509991e8ac72f31b374757d4
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44819094"
---
# <a name="use-content-search-to-search-third-party-data-imported-by-a-custom-partner-connector"></a>Utiliser la recherche de contenu pour rechercher des données tierces importées par un connecteur de partenaire personnalisé

Vous pouvez utiliser l' [outil eDiscovery](content-search.md) de la recherche de contenu dans le centre de sécurité & conformité pour rechercher des éléments importés dans des boîtes aux lettres dans Microsoft 365 à partir d’une source de données tierce. Vous pouvez créer une requête pour rechercher tous les éléments de données tiers importés ou créer une requête pour rechercher des éléments de données tiers spécifiques. Par ailleurs, vous pouvez également créer une stratégie de rétention basée sur une requête ou une conservation eDiscovery basée sur une requête pour conserver les données tierces.
  
Pour plus d’informations sur l’utilisation d’un partenaire pour importer des données tierces et la liste des types de données tierces que vous pouvez importer vers Microsoft 365, consultez [collaborer avec un partenaire pour archiver des données tierces dans Office 365](work-with-partner-to-archive-third-party-data.md).

> [!IMPORTANT]
> Les instructions de cet article s’appliquent uniquement aux données tierces qui ont été importées par un connecteur de partenaire personnalisé. Cet article ne s’applique pas aux données tierces importées à l’aide des [connecteurs de données tiers](archiving-third-party-data.md#third-party-data-connectors) dans le centre de conformité Microsoft.
  
## <a name="creating-a-query-to-search-all-third-party-data"></a>Création d’une requête pour rechercher toutes les données tierces

Pour rechercher (ou mettre en attente) tout type de données tierces que vous avez importées dans Office 365, vous pouvez utiliser la `kind:externaldata` paire message-valeur de la zone de mot clé pour une recherche de contenu ou lors de la création d’une conservation basée sur une requête. Par exemple, pour rechercher des éléments importés à partir d’une source de données tierce et qui contiennent le mot « Contoso » dans la propriété Subject de l’élément importé, utilisez la requête suivante : 
  
```powershell
kind:externaldata AND subject:contoso
```

L’exemple de requête de mot clé précédent inclut la propriété Subject. Pour obtenir la liste des autres propriétés des éléments de données tierces pouvant être inclus dans une requête de mot-clé, voir la section « plus d’informations » dans [utilisation d’un partenaire pour archiver des données tierces dans Office 365](work-with-partner-to-archive-third-party-data.md#more-information).
  
Lors de la création de requêtes de recherche et de conservation de données tierces, vous pouvez également utiliser des conditions pour affiner les résultats de la recherche. Pour plus d’informations sur la création de requêtes de recherche de contenu, consultez la rubrique [requêtes de mots clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md).
  
## <a name="creating-a-query-to-search-specific-types-of-third-party-data"></a>Création d’une requête pour rechercher des types spécifiques de données tierces

Au lieu de rechercher tous les types de données tierces, vous pouvez créer des requêtes qui recherchent uniquement un type précis de données tierces à l’aide de la paire de valeur de la *propriété* de message suivante dans la zone de mot clé pour une recherche de contenu :
  
```powershell
itemclass:ipm.externaldata.<third-party data type>* 
```

Par exemple, pour rechercher des données Facebook qui contiennent le mot « Contoso » dans la propriété Subject, vous devez utiliser la requête suivante :
  
```powershell
itemclass:ipm.externaldata.Facebook* AND subject:contoso
```

Le tableau suivant répertorie les types de données tiers que vous pouvez rechercher et la valeur à utiliser pour la `itemclass:` propriété message afin de Rechercher spécifiquement ce type de données tierces. La syntaxe de la requête ne respecte pas la casse. 
  
|**Type de données tiers**|**Valeur de la `itemclass:` propriété**|
|:-----|:-----|
|VISERA  <br/> | `ipm.externaldata.AIM*` <br/> |
|American Idol  <br/> | `ipm.externaldata.AmericanIdol*` <br/> |
|AOL avec client Pivot   <br/> | `ipm.externaldata.Pivot.IM` <br/> |
|Apple Juice  <br/> | `ipm.externaldata.AppleJuice*` <br/> |
|Tréma  <br/> | `ipm.externaldata.Ares*` <br/> |
|Axs Encrypted  <br/> | `ipm.externaldata.AxsEncrypted*` <br/> |
|Axs Exchange  <br/> | `ipm.externaldata.AxsExchange*` <br/> |
|Axs Local Archive  <br/> | `ipm.externaldata.AxsLocalArchive*` <br/> |
|Espace réservé ax  <br/> | `ipm.externaldata.AxsPlaceHolder*` <br/> |
|Axs Signed  <br/> | `ipm.externaldata.AxsSigned*` <br/> |
|Bazaarvoice  <br/> | `ipm.externaldata.Bazaarvoice*` <br/> |
|BearShare  <br/> | `ipm.externaldata.Bearshare*` <br/> |
|BitTorrent  <br/> | `ipm.externaldata.BitTorrent*` <br/> |
|BlackBerry  <br/> | `ipm.externaldata.Blackberry*` <br/> |
|Journaux d’appels BlackBerry  <br/> | `ipm.externaldata.BlackBerryCall*` <br/> |
|BlackBerry Messenger  <br/> | `ipm.externaldata.BlackBerryMessenger*` <br/> |
|Code confidentiel BlackBerry  <br/> | `ipm.externaldata.BlackBerryPIN*` <br/> |
|BlackBerry SMS  <br/> | `ipm.externaldata.BlackBerrySMS*` <br/> |
|Bloomberg  <br/> | `ipm.externaldata.Bloomberg*` <br/> |
|Bloomberg Mail  <br/> | `ipm.externaldata.BloombergMail*` <br/> |
|Messages Bloomberg  <br/> | `ipm.externaldata.BloombergMessaging*` <br/> |
|Box  <br/> | `ipm.externaldata.Box*` <br/> |
|Serveur de présence de messagerie instantanée Cisco &amp;  <br/> | `ipm.externaldata.Jabber.IM` <br/> |
|Cisco Jabber  <br/> | `ipm.externaldata.Jabber*` <br/> |
|CipherCloud for Salesforce Chatter  <br/> | `ipm.externaldata.Chatter.Post` <br/>  `ipm.externaldata.Chatter.Comment` <br/> |
|Direct Connect  <br/> | `ipm.externaldata.DirectConnect*` <br/> |
|Facebook  <br/> | `ipm.externaldata.Facebook*` <br/> |
|FastTrack  <br/> | `ipm.externaldata.FastTrack*` <br/> |
|FXConnect  <br/> | `ipm.externaldata.FXConnect.chat` <br/> |
|Flickr  <br/> | `ipm.externaldata.Flickr*` <br/> |
|Gnutella  <br/> | `ipm.externaldata.Gnutella*` <br/> |
|Google +  <br/> | `ipm.externaldata.GooglePlus*` <br/> |
|Google Talk  <br/> | `ipm.externaldata.GoogleTalk*` <br/> |
|GoToMyPC  <br/> | `ipm.externaldata.GoToMyPC*` <br/> |
|HipChat  <br/> | `ipm.externaldata.HipChat*` <br/> |
|Hopster  <br/> | `ipm.externaldata.Hopster*` <br/> |
|HubConnex  <br/> | `ipm.externaldata.HubConnex*` <br/> |
|Connexions IBM  <br/> | `ipm.externaldata.Connections*` <br/> |
|IBM SameTime  <br/> | `ipm.externaldata.Sametime*` <br/> |
|Conversation ICE  <br/> | `ipm.externaldata.ICEChat.Chat` <br/> |
|Indii Messenger  <br/> | `ipm.externaldata.Indii*` <br/> |
|Instagram  <br/> | `ipm.externaldata.Instagram*` <br/> |
|Instant Bloomberg  <br/> | `ipm.externaldata.InstantBloomberg*` <br/> |
|InvestEdge  <br/> | `ipm.externaldata.InvestEdge*` <br/> |
|SALLE  <br/> | `ipm.externaldata.IRC*` <br/> |
|Jive  <br/> | `ipm.externaldata.Jive*` <br/> |
|JiveApiRetention  <br/> | `ipm.externaldata.JiveApiRetention*` <br/> |
|JXTA  <br/> | `ipm.externaldata.JXTA*` <br/> |
|LinkedIn  <br/> | `ipm.externaldata.LinkedIn*` <br/> |
|MFTP  <br/> | `ipm.externaldata.MFTP*` <br/> |
|UC Microsoft  <br/> | `ipm.externaldata.MicrosoftUC*` <br/> |
|Correspondance des idées  <br/> | `ipm.externaldata.MindAlign*` <br/> |
|Mobile Guard  <br/> | `ipm.externaldata.MobileGuard*` <br/> |
|SYMPATICO  <br/> | `ipm.externaldata.MSN*` <br/> |
|MySpace  <br/> | `ipm.externaldata.MySpace*` <br/> |
|NEONetwork  <br/> | `ipm.externaldata.NEONetwork*` <br/> |
|OpenNap  <br/> | `ipm.externaldata.OpenNap*` <br/> |
|Pinterest  <br/> | `ipm.externaldata.Pinterest*` <br/> |
|Pivot  <br/> | `ipm.externaldata.Pivot*` <br/> |
|QQ  <br/> | `ipm.externaldata.QQ*` <br/> |
|Microsoft SharePoint  <br/> | `ipm.externaldata.SharePoint*` <br/> |
|Salesforce Chatter  <br/> | `ipm.externaldata.Chatter*` <br/> |
|Skype Entreprise  <br/> | `ipm.externaldata.Skype*` <br/> |
|Slack Enterprise Grid  <br/> | `ipm.externaldata.Slack.IM` <br/> |
|SoftEther  <br/> | `ipm.externaldata.SoftEther*` <br/> |
|Squawker  <br/> | `ipm.externaldata.Squawker*` <br/> |
|Concert  <br/> | `ipm.externaldata.Symphony*` <br/> |
|Thomson Reuters  <br/> | `ipm.externaldata.Reuters*` <br/> |
| Thomson Reuters Eikon Messenger  <br/> | `ipm.externaldata.ReutersEikon*` <br/> |
|Termes  <br/> | `ipm.externaldata.Tor*` <br/> |
|TTT  <br/> | `ipm.externaldata.TTT*` <br/> |
|Twitter  <br/> | `ipm.externaldata.Twitter*` <br/> |
|UBS Chat  <br/> | `ipm.externaldata.UBS*` <br/> |
|Vimeo  <br/> | `ipm.externaldata.Vimeo*` <br/> |
|WinMX  <br/> | `ipm.externaldata.WinMX*` <br/> |
|Winny  <br/> | `ipm.externaldata.Winny*` <br/> |
|Payant  <br/> | `ipm.externaldata.Yahoo!*` <br/> |
|Yammer  <br/> | `ipm.externaldata.Yammer*` <br/> |
|YellowJacket  <br/> | `ipm.externaldata.YellowJacket*` <br/> |
|YouTube  <br/> | `ipm.externaldata.YouTube*` <br/> |
