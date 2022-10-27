---
title: Se connecter aux données Microsoft 365 Government Community Cloud (GCC) avec Usage Analytics
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: Découvrez comment vous connecter à des données dans votre locataire Microsoft 365 Government Community Cloud (GCC) à l’aide de l’application modèle Analyse de l’utilisation Microsoft 365 dans Power BI.
ms.openlocfilehash: 751ef7e0b0834b13fbdb863f37249b27cd4781aa
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68729388"
---
# <a name="connect-to-microsoft-365-government-community-cloud-gcc-data-with-usage-analytics"></a>Se connecter aux données Microsoft 365 Government Community Cloud (GCC) avec Usage Analytics

Utilisez les procédures suivantes pour vous connecter à vos données avec le rapport Analyse de l’utilisation de Microsoft 365 dans un locataire Microsoft 365 Government Community Cloud (GCC). 

> [!NOTE]
> Ces instructions s’adressent spécifiquement aux locataires Microsoft 365 GCC. 

## <a name="before-you-begin"></a>Avant de commencer

Pour configurer initialement Microsoft 365 Usage Analytics : 

- Vous devez être un administrateur général Microsoft 365 pour activer la collecte de données. 
- Vous avez besoin de [l’application Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/) pour utiliser le fichier de modèle. 
- Vous avez besoin d’une [licence Power BI Pro](https://go.microsoft.com/fwlink/p/?linkid=845347) ou d’une capacité Premium pour publier et afficher le rapport. 

## <a name="step-1-make-you-organizations-data-available-for-the-microsoft-365-usage-analytics-report"></a>Étape 1 : Rendre les données de votre organisation disponibles pour le rapport Analyse de l’utilisation de Microsoft 365

1. Dans le Centre d'administration Microsoft 365, développez le menu de navigation, sélectionnez **Rapports**, puis **Utilisation**. 
2. Dans la page **Rapports d’utilisation** , dans la section Microsoft 365 Usage Analytics, sélectionnez **Prise en main**. 
3. Sous **Activer Power BI pour l’analyse de l’utilisation**, sélectionnez **Rendre les données d’utilisation organisationnelles disponibles pour l’analyse de l’utilisation de Microsoft pour Power BI**, puis **sélectionnez Enregistrer**.

    ![Rendre vos données de locataire disponibles.](../../media/usage-analytics/make-data-available.png) 



    Cela démarre un processus pour rendre les données de votre organisation accessibles pour ce rapport, et vous verrez un message indiquant que **nous préparons vos données pour l’analytique de l’utilisation de Microsoft 365**. Notez que ce processus peut prendre 24 heures. 

4. Lorsque les données de votre organisation sont prêtes, l’actualisation de la page affiche un message indiquant que vos données sont désormais disponibles et indique également votre numéro **d’ID de locataire** . Vous devrez utiliser l’ID de locataire dans une étape ultérieure lorsque vous tenterez de vous connecter à vos données de locataire. 
 
    ![ID de locataire.](../../media/usage-analytics/tenant-id-gcc.png) 
 
    > [!IMPORTANT]
    > Lorsque vos données sont disponibles, ne sélectionnez pas **Accéder à Power BI**, ce qui vous amènera à la Place de marché Power BI.  L’application modèle pour ce rapport requise par les locataires GCC n’est pas disponible sur la Place de marché Power BI.  


## <a name="step-2-download-the-power-bi-template-connect-to-your-data-and-publish-the-report"></a>Étape 2 : Télécharger le modèle Power BI, se connecter à vos données et publier le rapport

Les utilisateurs de Microsoft 365 GCC peuvent télécharger et utiliser le fichier de modèle de rapport Microsoft 365 Usage Analytics pour se connecter à leurs données. Vous aurez besoin Power BI Desktop pour ouvrir et utiliser le fichier de modèle. 

 > [!NOTE]
 > Actuellement, une application modèle pour le rapport Microsoft 365 Usage Analytics n’est pas disponible pour les locataires GCC dans la Place de marché Power BI.  

1. Après avoir téléchargé le [modèle Power BI](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit), ouvrez-le à l’aide de Power BI Desktop. 
2. Lorsque vous êtes invité à entrer un **TenantID**, entrez l’ID de locataire que vous avez reçu lorsque vous avez préparé les données de votre organisation pour ce rapport à l’étape 1. Sélectionnez ensuite **Charger**. Le chargement de vos données prend plusieurs minutes. 

    ![Entrez l’ID de locataire.](../../media/usage-analytics/add-tenant-id.png) 



3. Une fois le chargement terminé, votre rapport s’affiche et vous verrez un résumé de vos données. 

    ![Résumé.](../../media/usage-analytics/exec-summary.png) 
 

4. Enregistrez vos modifications dans le rapport. 
5. Sélectionnez **Publier** dans le menu Power BI Desktop pour publier le rapport sur le service Power BI Online où il peut être consulté. Cela nécessite une licence Power BI Pro ou une capacité Power BI Premium. Dans le cadre du [processus de publication](/power-bi/create-reports/desktop-upload-desktop-files#to-publish-a-power-bi-desktop-dataset-and-reports), vous devez sélectionner une destination à publier dans un espace de travail disponible dans le service en ligne Power BI.

## <a name="related-content"></a>Contenu associé

[À propos de l’Analyse de l’utilisation](usage-analytics.md) </br>
[Obtenir la dernière version d’analyse d’utilisation](get-the-latest-version-of-usage-analytics.md) </br>
[Naviguer et utiliser les rapports dans Microsoft 365 analyse de l’utilisation](navigate-and-utilize-reports.md) </br>