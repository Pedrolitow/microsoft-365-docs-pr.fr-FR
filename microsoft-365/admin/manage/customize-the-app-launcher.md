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
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 1136115a-75af-4497-b693-640c4ce70bc6
description: 'Créez des liens rapides vers vos courriers électroniques, vos documents, vos applications, vos sites SharePoint, vos sites externes et d’autres ressources en ajoutant des vignettes personnalisées au lanceur d’applications. '
ms.openlocfilehash: 705d45a2c26d3bd5e2d45d6d8f5a7c998c449f8d
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43628195"
---
# <a name="add-custom-tiles-to-the-app-launcher"></a>Ajouter des vignettes personnalisées au lanceur d'applications

Dans Microsoft 365, vous pouvez rapidement et facilement accéder à vos courriers électroniques, calendriers, documents et applications à l’aide du lanceur d’applications ([en savoir plus](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a.aspx)). Il s’agit des applications que vous obtenez avec Microsoft 365, ainsi que des applications personnalisées que vous ajoutez à partir de [SharePoint Store](https://support.office.com/article/dd98e50e-d3db-4ecb-9bb7-82b189822d43.aspx) ou [Azure ad](https://msdn.microsoft.com/office/office365/howto/connect-your-app-to-o365-app-launcher).
  
Vous pouvez ajouter vos propres vignettes au lanceur d'applications pointant vers des sites SharePoint, des sites externes, des applications existantes, etc. La vignette personnalisée apparaît dans l'onglet **Toutes** les applications du lanceur d'applications. Vous pouvez également l'épingler aux applications de l'onglet **Accueil** et inviter vos utilisateurs à faire de même. Il sera ainsi plus facile de repérer les sites, les applications et les ressources dont vous avez besoin pour effectuer votre travail. Dans l'exemple ci-dessous, une vignette personnalisée nommée « Portail Contoso » permet d'accéder au site intranet SharePoint d'une organisation. 
  
![Lanceur d’applications](../../media/7acc06cc-ac7a-4c6e-8ea7-81570a5bdbab.png)
  
## <a name="add-a-custom-tile-to-the-app-launcher"></a>Ajouter une vignette personnalisée au lanceur d'applications

1. Dans le centre d’administration, accédez à **Settings** > **paramètres** des paramètres et sélectionnez l’onglet Profil de l' **organisation** .
    
2. Sous l’onglet Profil de l' **organisation** , choisissez les **vignettes du lanceur d’applications personnalisé**.
  
3. Sélectionnez **Ajouter une vignette personnalisée**. 
  
4. Attribuez un **nom** à la nouvelle vignette. Le nom s'affiche alors dans la vignette. 
    
5. Entrez une **URL de site Web** pour la vignette. Il s’agit de l’emplacement où les utilisateurs doivent accéder lorsqu’ils sélectionnent la vignette sur le lanceur d’applications. Utilisez le protocole HTTPs dans l’URL.<br/>Conseil : Si vous créez une vignette pour un site SharePoint, accédez à ce site, copiez l’URL et collez-la ici. L’URL de votre site d’équipe par défaut se présente comme suit :`https://<company_name>.sharepoint.com` 
  
6. Entrez l' **URL de l’image** de la vignette. Cette image apparaît sur la page Mes applications et le lanceur d'applications.<br/>Conseil : l’image doit être 60x60 pixels et être disponible pour tous les membres de votre organisation sans nécessiter une authentification.

7. Entrez la **description** de la vignette. Cette option apparaît lorsque vous sélectionnez la vignette sur la page mes applications et que vous sélectionnez Détails de l' **application**. 
  
8. Sélectionnez **enregistrer les modifications** pour créer la vignette personnalisée. 
    
Celle-ci apparaît désormais dans l'onglet **Toutes** du lanceur d'applications pour vous et vos utilisateurs. 
  
## <a name="promote-the-tile-to-app-launcher"></a>Promouvoir la vignette sur le lanceur d’applications

1. Sélectionnez l’icône du lanceur d’applications et sélectionnez **toutes les applications**. 
    
2. Localisez la nouvelle vignette de votre application, sélectionnez les points de suspension, puis choisissez **code confidentiel pour le lanceur**.
  
    > [!NOTE]
    > Si la vignette personnalisée créée aux étapes précédente n'apparaît pas, vérifiez qu'une boîte aux lettres Exchange Online vous est affectée et que vous vous y êtes connecté au moins une fois. Ces étapes sont requises pour les vignettes personnalisées dans Microsoft 365. 
  
> [!IMPORTANT]
> Vous et vos utilisateurs devez suivre les étapes ci-dessous pour promouvoir les vignettes personnalisées de la page Mes applications dans le lanceur d'applications. 
  
## <a name="edit-or-delete-a-custom-tile"></a>Edit or delete a custom tile

1. Dans le centre d’administration, accédez à l’onglet<a href="https://go.microsoft.com/fwlink/p/?linkid=2067339" target="_blank">profil d’organisation</a> des**paramètres** > de **paramètres** > .
    
2. Sur la page profil de l' **organisation** , en regard de **Ajouter des vignettes personnalisées pour votre organisation**, sélectionnez **modifier**.

3. Mettez à jour les champs **Nom de la vignette**, **URL**, **Description** ou **URL de l'image** de la vignette personnalisée (voir la [Ajouter une vignette personnalisée au lanceur d'applications](#add-a-custom-tile-to-the-app-launcher)).
    
4. Sélectionnez **Fermer**la **mise à jour** \> . 
    
Pour supprimer une vignette personnalisée, dans la fenêtre **mosaïques personnalisées** , sélectionnez la vignette, sélectionnez Supprimer la**suppression**de **mosaïque** > . 
  
## <a name="whats-next"></a>Étape suivante

En plus d’ajouter des vignettes au lanceur d’applications, vous pouvez ajouter des vignettes du lanceur d’applications dans la barre de navigation ([en savoir plus](https://support.office.com/article/d536512c-b0f7-49fd-b8db-a8a967e23f23.aspx)). Pour personnaliser l’apparence de Microsoft 365 en fonction de la marque de votre organisation, consultez [la rubrique Customize the microsoft 365 Theme](../setup/customize-your-organization-theme.md).
  

