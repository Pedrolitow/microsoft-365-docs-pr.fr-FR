---
title: Sauvegarder des données avant de modifier les plans
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
description: Sauvegardez le contenu Outlook, OneDrive, Yammer et SharePoint avant de modifier Microsoft 365 plans.
ms.date: 03/17/2021
ms.openlocfilehash: fd5239deb88fbf9b87df7e62d85a3d2cc18e1df7
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102501"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>Sauvegarder des données avant de basculer Microsoft 365 pour les plans d’entreprise

Si un utilisateur est basculé vers un autre abonnement qui a moins de services liés aux données ou si un utilisateur quitte l’organisation, une copie de ses données stockées dans Microsoft 365 peut être téléchargée avant de passer au nouvel abonnement.

Si vous déplacez un utilisateur vers un abonnement qui a les mêmes services ou plus, vous n’avez pas besoin de sauvegarder les données utilisateur. Consultez [Déplacer les utilisateurs vers un autre abonnement](./move-users-different-subscription.md).
  
## <a name="save-a-copy-of-outlook-information"></a>Enregistrer une copie des informations de Outlook

Si les utilisateurs ont Outlook, ils peuvent [exporter ou sauvegarder des e-mails, des contacts et du calendrier vers un fichier .pst Outlook](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) avant que leur plan ne soit basculé.
  
Une fois le basculement vers le nouveau plan terminé, les utilisateurs peuvent [importer des e-mails, des contacts et un calendrier à partir d’un fichier .pst Outlook](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
## <a name="save-files-stored-in-onedrive-for-business"></a>Enregistrer les fichiers stockés dans OneDrive Entreprise

Avant de basculer vers un autre abonnement, les [utilisateurs peuvent télécharger des fichiers et des dossiers à partir de OneDrive ou SharePoint](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) vers un autre emplacement, tel qu’un dossier sur le disque dur de leur ordinateur ou un partage de fichiers sur le réseau de l’organisation.
  
## <a name="save-yammer-information"></a>Enregistrer les informations de Yammer

Les administrateurs peuvent exporter tous les messages, notes, fichiers, rubriques, utilisateurs et groupes vers un fichier .zip. Pour plus d’informations, consultez [Exporter des données à partir de Yammer Entreprise](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Les développeurs peuvent également utiliser [l’API Yammer](https://go.microsoft.com/fwlink/p/?linkid=842495) pour ce faire.
  
## <a name="how-to-save-sharepoint-information"></a>Comment enregistrer des informations SharePoint

Si un utilisateur passe d’un abonnement qui a SharePoint Online à un abonnement qui ne l’a pas, la vignette **SharePoint** n’apparaît plus dans son menu Microsoft 365.
  
Toutefois, tant que le nouvel abonnement se trouve dans la même organisation que celui à partir de lequel ils sont basculés, les utilisateurs pourront toujours accéder au site d’équipe SharePoint. Ils peuvent afficher et mettre à jour des blocs-notes, des documents, des tâches et des calendriers à l’aide de l’URL directe vers le site d’équipe.
  
> [!TIP]
> Nous recommandons aux utilisateurs d’accéder au site d’équipe avant que leur abonnement ne soit basculé et d’enregistrer l’URL en tant que favori ou signet dans leur navigateur.
  
Par défaut, l’URL du site web de l’équipe se présente sous la forme suivante :
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

où  _\<orgDomain\>_ se trouve l’URL de l’organisation.
  
Par exemple, si le domaine de l’organisation est contoso.onmicrosoft.com, l’URL directe vers le site d’équipe est `https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx`.
  
Bien sûr, les utilisateurs peuvent également télécharger SharePoint documents en ligne à partir du site d’équipe SharePoint à leur ordinateur local ou à un autre emplacement à tout moment.
