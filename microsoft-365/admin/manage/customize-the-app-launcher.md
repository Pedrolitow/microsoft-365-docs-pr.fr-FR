---
title: Ajouter des vignettes personnalisées au lanceur d'applications
f1.keywords:
- CSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 1136115a-75af-4497-b693-640c4ce70bc6
description: Créez des liens rapides vers vos e-mails, documents, applications, sites SharePoint, sites externes et autres ressources en ajoutant des vignettes personnalisées au lanceur d’applications.
ms.openlocfilehash: b7e23f8f21ea99232f7051b0cbeaaad5ad699095
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68166744"
---
# <a name="add-custom-tiles-to-the-app-launcher"></a>Ajouter des vignettes personnalisées au lanceur d'applications

Dans Microsoft 365, vous pouvez accéder rapidement et facilement à vos courriers électroniques, calendriers, documents et applications à l’aide du lanceur d’applications ([en savoir plus](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a)). Il s’agit d’applications que vous obtenez avec Microsoft 365, ainsi que d’applications personnalisées que vous ajoutez à partir du [SharePoint Store](https://support.microsoft.com/office/dd98e50e-d3db-4ecb-9bb7-82b189822d43) ou [d’Azure AD](/previous-versions/office/office-365-api/).
  
You can add your own custom tiles to the app launcher that point to SharePoint sites, external sites, legacy apps, and more. The custom tile appears under the app launcher's **All** apps, but you can pin it to the **Home** apps and instruct your users to do the same. This makes it easy to find the relevant sites, apps, and resources to do your job. In the below example, a custom tile called "Contoso Portal" is used to access an organization's SharePoint intranet site. 
  
![Lanceur d'applications.](../../media/7acc06cc-ac7a-4c6e-8ea7-81570a5bdbab.png)
  
## <a name="add-a-custom-tile-to-the-app-launcher"></a>Ajouter une vignette personnalisée au lanceur d'applications

1. Connectez-vous au centre d’administration en tant qu’administrateur général, accédez à **Paramètres** > **de l’organisation,** puis choisissez l’onglet **Profil de l’organisation** .
    
2. Sous l’onglet **Profil de l’organisation** , choisissez **vignettes de lanceur d’applications personnalisées**.
  
3. Sélectionnez **Ajouter une vignette personnalisée**. 
  
4. Attribuez un **nom** à la nouvelle vignette. Le nom s'affiche alors dans la vignette. 
    
5. Entrez une **URL de site web** pour la vignette. Il s’agit de l’emplacement où vous souhaitez que vos utilisateurs se rendent lorsqu’ils sélectionnent la vignette sur le lanceur d’applications. Utilisez HTTPS dans l’URL.

    > [!TIP]
    > Si vous créez une vignette pour un site SharePoint, accédez à ce site, copiez son adresse URL et collez-la à cet endroit. L’URL de votre site d’équipe par défaut ressemble à ceci : `https://<company_name>.sharepoint.com` 
  
6. Entrez une **URL de l’image** pour la vignette. Cette image apparaît sur la page Mes applications et le lanceur d'applications.

    > [!TIP]
    > L’image doit être de 60 x 60 pixels et être disponible pour tous les membres de votre organisation sans nécessiter d’authentification.

7. Entrez la **description** de la vignette. Vous le voyez lorsque vous sélectionnez la vignette dans la page Mes applications et sélectionnez **Les détails de l’application**. 
  
8. Sélectionnez **Enregistrer les modifications** pour créer la vignette personnalisée. 
    
    Votre vignette personnalisée apparaîtra dans les prochaines 24 heures dans le lanceur d’applications sous l’onglet **Tout** pour vous et vos utilisateurs. 

    > [!NOTE]
    > Si la vignette personnalisée créée aux étapes précédente n'apparaît pas, vérifiez qu'une boîte aux lettres Exchange Online vous est affectée et que vous vous y êtes connecté au moins une fois. Ces étapes sont requises pour les vignettes personnalisées dans Microsoft 365. 
  
## <a name="edit-or-delete-a-custom-tile"></a>Edit or delete a custom tile

1. Dans le centre d’administration, accédez à l’onglet Profil **d’organisation** **paramètres** > **de l’organisation paramètres** >  de l’organisation.
    
2. Dans la page **Profil de l’organisation** , accédez aux **vignettes du lanceur d’applications personnalisées**, si vous sélectionnez les trois points en regard de votre **vignette personnalisée** et sélectionnez **Modifier la vignette personnalisée**.

3. Mettez à jour les champs **Nom de la vignette**, **URL**, **Description** ou **URL de l'image** de la vignette personnalisée (voir la [Ajouter une vignette personnalisée au lanceur d'applications](#add-a-custom-tile-to-the-app-launcher)).
    
4. Sélectionnez **Fermer la mise à jour** \> **.** 
    
Pour supprimer une vignette personnalisée, dans la fenêtre **Vignettes personnalisées** , sélectionnez la vignette, **sélectionnez Supprimer la vignette** > **Supprimer**. 
  
## <a name="next-steps"></a>Prochaines étapes

 Pour personnaliser l’apparence de Microsoft 365 en fonction de la marque de votre organisation, consultez [Personnaliser le thème Microsoft 365](../setup/customize-your-organization-theme.md).

## <a name="related-content"></a>Contenu associé

[Épingler des applications au lanceur d’applications de vos utilisateurs](pin-apps-to-app-launcher.md) (article)\
[Mettre à niveau vos utilisateurs Microsoft 365 pour les entreprises vers le dernier client Office](../setup/upgrade-users-to-latest-office-client.md) (article)\
[Gérer les compléments dans le centre d’administration](../manage/manage-addins-in-the-admin-center.md) (article)
