---
title: Back up data before changing plans
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- commerce_subscriptions
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
description: Sauvegardez Outlook, OneDrive, Yammer et SharePoint contenu avant de modifier Microsoft 365 plans.
ms.date: 03/17/2021
ms.openlocfilehash: 86953f3235d8725ecdd6b5294611c0e5a378b17d
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59208012"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>Back up data before switching Microsoft 365 for business plans

Si un utilisateur est basculé vers un autre abonnement qui a moins de services liés aux données ou si un utilisateur quitte l’organisation, une copie de ses données stockées dans Microsoft 365 peut être téléchargée avant d’être basculée vers le nouvel abonnement.

Si vous souhaitez déplacer un utilisateur vers un abonnement qui dispose du même ou de plusieurs services, vous n’avez pas besoin de le faire. Voir [Déplacer des utilisateurs vers un autre abonnement.](./move-users-different-subscription.md)
  
## <a name="save-a-copy-of-outlook-information"></a>Enregistrer une copie des informations Outlook données

Si les utilisateurs Outlook, ils peuvent exporter ou sauvegarder le courrier électronique, les contacts et le calendrier vers un [fichier .pst Outlook avant](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) que leur plan ne change.
  
Une fois le basculement vers la nouvelle offre terminé, les utilisateurs peuvent importer le courrier électronique, les contacts et le calendrier à partir d Outlook [fichier .pst .](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac)
  
## <a name="save-files-stored-in-onedrive-for-business"></a>Enregistrer les fichiers stockés dans OneDrive Entreprise

Avant de passer à un autre abonnement, les utilisateurs peuvent télécharger des fichiers et des [dossiers](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) depuis OneDrive ou SharePoint vers un autre emplacement, tel qu’un dossier sur le disque dur de leur ordinateur ou un partage de fichiers sur le réseau de l’organisation.
  
## <a name="save-yammer-information"></a>Enregistrer les Yammer données

Les administrateurs peuvent exporter tous les messages, notes, fichiers, rubriques, utilisateurs et groupes vers .zip fichier. Pour plus d’informations, [voir Exporter des données à partir Yammer Entreprise](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Les développeurs peuvent également [utiliser Yammer API](https://go.microsoft.com/fwlink/p/?linkid=842495) pour ce faire.
  
## <a name="how-to-save-sharepoint-information"></a>Comment enregistrer des SharePoint de données

Si un utilisateur passe d’un abonnement SharePoint Online à un abonnement qui ne l’a pas, la vignette **SharePoint** n’apparaît plus dans son menu Microsoft 365.
  
Toutefois, tant que le nouvel abonnement est au sein de la même organisation que celle à partir de celle-ci, les utilisateurs pourront toujours accéder au site d SharePoint’équipe. Ils peuvent afficher et mettre à jour des blocs-notes, des documents, des tâches et des calendriers à l’aide de l’URL directe vers le site d’équipe.
  
> [!TIP]
> Nous recommandons aux utilisateurs d’accéder au site d’équipe avant de changer d’abonnement et d’enregistrer l’URL en tant que favori ou signet dans leur navigateur.
  
Par défaut, l’URL du site web de l’équipe se trouve sous la forme suivante :
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

où  _\<orgDomain\>_ se trouve l’URL de l’organisation.
  
Par exemple, si le domaine de l’organisation est contoso.onmicrosoft.com, l’URL directe vers le site d’équipe sera `https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx` .
  
Bien entendu, les utilisateurs peuvent également télécharger SharePoint documents en ligne à partir du site d’équipe SharePoint sur leur ordinateur local ou à un autre emplacement à tout moment.
