---
title: Configurer Apprentissage Microsoft Viva (prévisualisation) dans le centre Teams’administration
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: chrisarnoldmsft
ms.date: ''
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-learning
localization_priority: None
description: Découvrez comment configurer Apprentissage Microsoft Viva (prévisualisation) dans le centre Teams’administration.
ms.openlocfilehash: 0db999306cc9cf7153d649e7ca49aca709425d6f
ms.sourcegitcommit: b05b107774e8bca36c9ee19fdc4719d17e302f11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2021
ms.locfileid: "58483390"
---
# <a name="set-up-microsoft-viva-learning-preview-in-the-teams-admin-center"></a>Configurer Apprentissage Microsoft Viva (prévisualisation) dans le centre Teams’administration

> [!NOTE]
> Les informations de cet article concernent un produit d’aperçu qui peut être considérablement modifié avant sa publication commerciale. 

L’administrateur Teams doit effectuer certaines étapes pour activer Learning (Prévisualisation) pour ses utilisateurs dans le client. Ces étapes varient en fonction de la façon dont le client est activé : prévisualisation [*publique*](set-up-teams-admin-center.md#public-preview-tenants) ou [ *prévisualisation privée* (ou bêta).](set-up-teams-admin-center.md#private-preview-tenants)

## <a name="public-preview-tenants"></a>Locataires de la prévisualisation publique

### <a name="administrator-steps-for-public-preview-tenants"></a>Étapes de l’administrateur pour les locataires de la prévisualisation publique

Étant donné que le Learning (prévisualisation) n’est pas encore disponible, certaines étapes sont nécessaires pour activer les fonctionnalités et définir des autorisations pour des utilisateurs ou des groupes spécifiques. 

1. Activez les fonctionnalités de prévisualisation publique pour les utilisateurs Learning (prévisualisation).

    a. Modifiez Teams de mise à jour pour activer les fonctionnalités de prévisualisation publique. Voir [Microsoft Teams prévisualisation publique.](/microsoftteams/public-preview-doc-updates)

    b. Activez la stratégie de mise à jour pour les utilisateurs ou les groupes qui effectueront le test Learning (prévisualisation). Voir [Attribuer des stratégies à des utilisateurs et des groupes.](/microsoftteams/assign-policies-users-and-groups)

2. Modifiez la stratégie d’autorisation d’application pour les utilisateurs Learning (prévisualisation).

    a. Sauf si elle fait actuellement partie de la stratégie globale, autorisez toutes les applications Microsoft dans la stratégie d’autorisation de l’application. Voir [Gérer les stratégies d’autorisation d’application dans Microsoft Teams](/microsoftteams/teams-app-permission-policies). 

    b. Activez la stratégie d’autorisation d’application pour les utilisateurs ou les groupes qui effectueront le test Learning (Prévisualisation). Voir [Attribuer des stratégies à des utilisateurs et des groupes.](/microsoftteams/assign-policies-users-and-groups)

3. Informez les utilisateurs qui testent Le Learning (prévisualisation) pour basculer leur client de build vers la [prévisualisation](set-up-teams-admin-center.md#user-steps-for-public-preview-tenants)publique pour Teams .

> [!IMPORTANT]
> Pour les locataires de la prévisualisation publique, Learning  (prévisualisation) ne sera pas affiché dans les applications gérées dans le Centre d’administration Teams jusqu’à la publication finale du produit. Toutefois, les utilisateurs de la prévisualisation publique activée peuvent trouver Domaine Learning (prévisualisation) dans le magasin d’applications Teams et l’utiliser, une fois que les stratégies et autorisations correctes ont été définies.

### <a name="user-steps-for-public-preview-tenants"></a>Étapes utilisateur pour les locataires de la prévisualisation publique

Les utilisateurs qui ont été activés pour le test [](/microsoftteams/public-preview-doc-updates#enable-public-preview) de prévisualisation publique, en activant les stratégies décrites précédemment, [](set-up-teams-admin-center.md#administrator-steps-for-public-preview-tenants) doivent basculer vers la prévisualisation publique dans leur client Teams client.

1. Les utilisateurs doivent sélectionner leur image de profil > **à propos de** la  >  **prévisualisation publique.**

    ![Navigation supérieure dans l’application Teams affichant le profil de l’utilisateur](../media/learning/learning-app-select-profile-teams.png)

2. Les utilisateurs doivent accepter les conditions générales de la prévisualisation publique.

    ![Basculer vers la version d’aperçu public](../media/learning/learning-app-switch-to-public-preview.png)

3. Les utilisateurs peuvent désormais trouver Learning (prévisualisation) dans le Teams’application store et commencer à l’utiliser.

## <a name="private-preview-tenants"></a>Locataires de la prévisualisation privée

### <a name="administrator-steps-for-private-preview-or-beta-tenants"></a>Étapes de l’administrateur pour les locataires de prévisualisation privée (ou bêta)

Pour les locataires de la prévisualisation privée, aucune stratégie supplémentaire ne doit être activée. Toutefois, Le Learning (prévisualisation) doit être mis à la disposition des utilisateurs de votre organisation.

1. Dans le navigation gauche du centre d’administration Teams, Teams **applications Gérer**  >  **les applications.**

   ![Navigation gauche dans le centre d Teams d’administration affichant Teams applications et la section Gérer les applications.](../media/learning/learning-app-teams-manage-apps-nav.png)

2. Dans **la** page Gérer les applications, dans la zone de recherche, tapez *Contrôle Learning,* puis sélectionnez **Learning (Prévisualisation).**

   ![Page Gérer les applications dans le centre Teams’administration affichant la zone de recherche.](../media/learning/learning-app-teams-manage-apps-page.png)

3. Dans la page **Contrôle Learning (Prévisualisation),** sous **État,** sélectionnez Autorisé à activer Learning (Aperçu). 

   ![Learning page dans le centre d Teams’administration affichant la section Paramètres d’état et d’application.](../media/learning/learning-app-teams-learning-page.png)

<!---
The Teams admin installs Viva Learning (Preview) and applies permission policies through the Teams admin center.

1. For Viva Learning (Preview), you must first set the Update policy in Teams. For more information, see [Microsoft Teams Public Preview](/MicrosoftTeams/public-preview-doc-updates).

    1. Sign in to the Teams admin center.

    2. Select **Teams** > **Update policies**.

    3. Select **Add**. 

    4. Name the update policy, add a policy, and turn on **Show preview features**.

2. The admin must notify users of the policy update so that they move their build into the Public Preview for Teams. 

    1. Users must select their profile image > **About** > **Public Preview**.
   
        ![Upper navigation in the Teams application showing user's profile](../media/learning/learning-app-select-profile-teams.png)
    
    2. Users must accept the **Public preview** terms and conditions.

        ![Switch to public preview build](../media/learning/learning-app-switch-to-public-preview.png)
 
3. For organizations that have restrictive policies and need to enable Viva Learning (Preview), follow the process in the next section.

## Manage settings for Viva Learning (Preview)

You must be an administrator in the Teams admin center to perform these tasks.

To make Viva Learning (Preview) available for users in your organization, follow these steps:

1. In the left navigation of the Teams admin center, go to **Teams apps** > **Manage apps**.

   ![Left navigation in the Teams admin center showing Teams apps and Manage apps section.](../media/learning/learning-app-teams-manage-apps-nav.png)

2. On the **Manage apps** page, in the search box, type *Viva learning*, and then select **Viva Learning (Preview)**.

   ![Manage apps page in the Teams admin center showing the search box.](../media/learning/learning-app-teams-manage-apps-page.png)

3. On the **Viva Learning (Preview)** page:

   1. Under **Status**, select **Allowed** to turn on Viva Learning (Preview).

   2. On the **Settings** tab, under **App settings**, go to the Microsoft 365 admin center to [configure learning content sources](content-sources-365-admin-center.md).

   ![Learning page in the Teams admin center showing Status and App settings section.](../media/learning/learning-app-teams-learning-page.png)

4. After **Manage app** settings, go to **Permission policies** and **Setup policies** to grant permission to employees who should have access to Viva Learning (Preview) as part of your organization's participation in the preview.

> [!NOTE]
>  If your organization is in Ring 4.0 as part of Teams TAP100 program, you might need to enable approved users in Ring 3.0 to access Viva Learning (Preview). <br><br>As part of the preview, Viva Learning (Preview) is released in Ring 3.0. If your organization is in Ring 4.0, you won’t see Viva Learning (Preview) on the **Manage apps** page. To test the app, you need to create a custom apps permission policy, set it to **Allow all apps**, and assign it to Ring 3.0 approved users. <br><br>   ![TAP-AppsPermission-Plcy page showing Allow all apps selected.](../media/learning/learning-app-tap-appspermission-plcy.png)

--->

## <a name="next-step"></a>Étape suivante

[Configurer des sources de contenu d’apprentissage pour Learning (prévisualisation) dans le Centre d’administration Microsoft 365](content-sources-365-admin-center.md)
