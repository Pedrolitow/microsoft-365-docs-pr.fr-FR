---
title: Sauvegarder les données avant de basculer vers Microsoft 365 pour les offres professionnelles
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- commerce
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
ms.assetid: a1da52c9-2167-4973-9e6d-492314a79b87
description: Sauvegardez les contenus Outlook, OneDrive, Yammer et SharePoint avant de basculer entre les abonnements Microsoft 365 ou si un utilisateur quitte l’organisation.
ms.openlocfilehash: fbebe72ec47fb6745cee6a12d81117ad08c50846
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43636079"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>Sauvegarder les données avant de basculer vers Microsoft 365 pour les offres professionnelles

Si un utilisateur est basculé vers un autre abonnement qui a moins de services liés aux données ou un utilisateur quitte l’organisation, une copie de ses données stockées dans Microsoft 365 peut être téléchargée avant d’être basculée vers le nouvel abonnement.
  
## <a name="save-a-copy-of-outlook-information"></a>Enregistrer une copie des informations Outlook

Si les utilisateurs disposent d’Outlook, ils peuvent [exporter ou sauvegarder le courrier, les contacts et le calendrier vers un fichier. pst Outlook](https://support.office.com/article/14252b52-3075-4e9b-be4e-ff9ef1068f91) avant que leur plan ne soit basculé.
  
Une fois le nouveau plan terminé, les utilisateurs peuvent [importer des courriers électroniques, des contacts et un calendrier à partir d’un fichier. pst Outlook](https://support.office.com/article/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
## <a name="save-files-stored-in-onedrive-for-business"></a>Enregistrer des fichiers stockés dans OneDrive entreprise

Avant de passer à un autre abonnement, les utilisateurs peuvent [Télécharger des fichiers et des dossiers à partir de OneDrive ou de SharePoint](https://support.office.com/article/5c7397b7-19c7-4893-84fe-d02e8fa5df05) vers un autre emplacement, tel qu’un dossier sur le disque dur de l’ordinateur ou un partage de fichiers sur le réseau de l’organisation.
  
## <a name="save-yammer-information"></a>Enregistrer les informations Yammer

Les administrateurs peuvent exporter tous les messages, notes, fichiers, rubriques, utilisateurs et groupes dans un fichier. zip. Pour plus d’informations, consultez la rubrique [exporter des données à partir de Yammer Enterprise](https://docs.microsoft.com/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Les développeurs peuvent également utiliser l' [API Yammer](https://go.microsoft.com/fwlink/p/?linkid=842495) pour y parvenir.
  
## <a name="how-to-save-sharepoint-information"></a>Enregistrement des informations SharePoint

Si un utilisateur passe d’un abonnement doté de SharePoint Online à un utilisateur qui n’en a pas, la vignette **SharePoint** n’apparaîtra plus dans son menu Microsoft 365.
  
Toutefois, tant que le nouvel abonnement est au sein de la même organisation que celle à partir de laquelle il est commuté, les utilisateurs pourront toujours accéder au site d’équipe SharePoint. Ils peuvent afficher et mettre à jour des blocs-notes, des documents, des tâches et des calendriers à l’aide de l’URL directe vers le site d’équipe.
  
> [!TIP]
> Nous recommandons aux utilisateurs d’accéder au site d’équipe avant que leur abonnement ne soit commuté et d’enregistrer l’URL en tant que favori ou signet dans leur navigateur.
  
Par défaut, l’URL du site Web d’équipe se présente comme suit :
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

où _ \<orgDomain\> _ est l’URL de l’organisation.
  
Par exemple, si le domaine de l’organisation est contoso.onmicrosoft.com, l’URL directe vers le site d’équipe serait https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx.
  
Bien entendu, les utilisateurs peuvent également télécharger des documents SharePoint Online à partir du site d’équipe SharePoint vers leur ordinateur local ou vers un autre emplacement à tout moment.