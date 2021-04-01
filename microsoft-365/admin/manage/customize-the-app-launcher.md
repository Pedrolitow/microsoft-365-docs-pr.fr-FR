---
title: Ajouter des vignettes personnalisées au lanceur d'applications
f1.keywords:
- CSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 1136115a-75af-4497-b693-640c4ce70bc6
description: 'Créez des liens rapides vers vos e-mails, documents, applications, sites SharePoint, sites externes et autres ressources en ajoutant des vignettes personnalisées au lanceur d’applications. '
ms.openlocfilehash: b6ae4deed1566492574e30cf8cb66a750c9858c8
ms.sourcegitcommit: d4604e333507c6f57d5bf327531a241b649052de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "51470630"
---
# <a name="add-custom-tiles-to-the-app-launcher"></a>Ajouter des vignettes personnalisées au lanceur d'applications

Dans Microsoft 365, vous pouvez rapidement et facilement vous rendre sur votre messagerie, vos calendriers, vos documents et vos applications à l’aide du lanceur d’applications (en[savoir plus).](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a) Il s’agit des applications que vous obtenez avec Microsoft 365, ainsi que des applications personnalisées que vous ajoutez à partir du [SharePoint Store](https://support.microsoft.com/office/dd98e50e-d3db-4ecb-9bb7-82b189822d43) ou [d’Azure AD.](/previous-versions/office/office-365-api/)
  
Vous pouvez ajouter vos propres vignettes au lanceur d'applications pointant vers des sites SharePoint, des sites externes, des applications existantes, etc. La vignette personnalisée apparaît dans l'onglet **Toutes** les applications du lanceur d'applications. Vous pouvez également l'épingler aux applications de l'onglet **Accueil** et inviter vos utilisateurs à faire de même. Il sera ainsi plus facile de repérer les sites, les applications et les ressources dont vous avez besoin pour effectuer votre travail. Dans l'exemple ci-dessous, une vignette personnalisée nommée « Portail Contoso » permet d'accéder au site intranet SharePoint d'une organisation. 
  
![Lanceur d’applications](../../media/7acc06cc-ac7a-4c6e-8ea7-81570a5bdbab.png)
  
## <a name="add-a-custom-tile-to-the-app-launcher"></a>Ajouter une vignette personnalisée au lanceur d'applications

1. Connectez-vous au Centre d’administration en tant qu’administrateur général, sélectionnez **Paramètres** de l’organisation paramètres et choisissez l’onglet  >  Profil **de l’organisation.**
    
2. Sous **l’onglet Profil de** l’organisation, choisissez **Vignettes de lancement d’application personnalisées.**
  
3. Sélectionnez **Ajouter une vignette personnalisée.** 
  
4. Attribuez un **nom** à la nouvelle vignette. Le nom s'affiche alors dans la vignette. 
    
5. Entrez **l’URL du site web** pour la vignette. Il s’agit de l’emplacement où vous souhaitez que vos utilisateurs se lancent lorsqu’ils sélectionnent la vignette dans le lanceur d’applications. Utilisez HTTPS dans l’URL.<br/>CONSEIL : si vous créez une vignette pour un site SharePoint, accédez à ce site, copiez l’URL et collez-la ici. L’URL de votre site d’équipe par défaut ressemble à ceci : `https://<company_name>.sharepoint.com` 
  
6. Entrez une **URL de l’image** pour la vignette. Cette image apparaît sur la page Mes applications et le lanceur d'applications.<br/>CONSEIL : l’image doit être de 60 x 60 pixels et être disponible pour tous les membres de votre organisation sans nécessiter d’authentification.

7. Entrez la **description** de la vignette. Cela s’affiche lorsque vous sélectionnez la vignette dans la page Mes applications et que vous sélectionnez **Détails de l’application.** 
  
8. Sélectionnez **Enregistrer les modifications** pour créer la vignette personnalisée. 
    
Celle-ci apparaît désormais dans l'onglet **Toutes** du lanceur d'applications pour vous et vos utilisateurs. 
  
## <a name="edit-or-delete-a-custom-tile"></a>Edit or delete a custom tile

1. Dans le centre d’administration, allez dans **l’onglet** Profil d’organisation  >  **Paramètres de** l’organisation paramètres de  >  **l’organisation.** </a>
    
2. Dans la page **Profil de l’organisation,** en plus d’ajouter des   **vignettes personnalisées pour votre organisation,** sélectionnez **Modifier**.

3. Mettez à jour les champs **Nom de la vignette**, **URL**, **Description** ou **URL de l'image** de la vignette personnalisée (voir la [Ajouter une vignette personnalisée au lanceur d'applications](#add-a-custom-tile-to-the-app-launcher)).
    
4. Sélectionnez **Mettre à** \> **jour fermer**. 
    
Pour supprimer une vignette  personnalisée, dans la fenêtre Vignettes personnalisées, sélectionnez la vignette, **sélectionnez Supprimer la vignette**  >  **Supprimer.** 
  
## <a name="whats-next"></a>Étape suivante

En plus d’ajouter des vignettes au lanceur d’applications, vous pouvez ajouter des vignettes de lanceur d’applications à la barre de navigation[(en savoir plus).](https://support.microsoft.com/office/eb34a21b-52fa-4fbf-a8d5-146132242985) Pour personnaliser l’apparence de Microsoft 365 afin qu’elle corresponde à la marque de votre organisation, voir Personnaliser le [thème Microsoft 365.](../setup/customize-your-organization-theme.md)
