---
title: Ajouter de l’espace de stockage pour votre abonnement
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- commerce
- Adm_TOC
- SPO_Content
ms.custom:
- MAX_CampaignID
- okr_SMB
- AdminSurgePortfolio
search.appverid:
- MET150
description: Découvrez comment ajouter et réduire le stockage de fichiers dans votre abonnement Microsoft 365. Avec le stockage de fichiers supplémentaire, vous pouvez stocker davantage de contenu dans SharePoint Online et OneDrive.
ms.date: ''
ms.openlocfilehash: 7f9973054bfe97beae36e28b73a3eb2025a13e73
ms.sourcegitcommit: 25afc0c34edc7f8a5eb389d8c701175256c58ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "47324467"
---
# <a name="add-storage-space-for-your-subscription"></a>Ajouter de l’espace de stockage pour votre abonnement

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

Si vous commencez à manquer d’espace de stockage pour vos collections de sites SharePoint Online et si votre plan est éligible, vous pouvez en ajouter à votre abonnement.  Si le **stockage de fichiers supplémentaire Office 365** n’apparaît pas dans la liste des modules complémentaires disponibles, cela signifie que votre plan n’est pas éligible. Pour plus d’informations, consultez la rubrique [mon plan est-il éligible ?](#is-my-plan-eligible-for-office-365-extra-file-storage)

> [!NOTE]
> Si vous avez acheté votre abonnement via le gestionnaire de licences en volume ou un fournisseur de services cryptographiques, vous ne pouvez pas acheter **Office 365 supplémentaire de stockage de fichiers** pour votre organisation directement auprès de Microsoft. Contactez votre représentant ou votre partenaire pour obtenir de l’aide.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être un administrateur global ou SharePoint pour effectuer les tâches décrites dans cet article. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../admin/add-users/about-admin-roles.md).

## <a name="view-available-storage"></a>Afficher le stockage disponible

::: moniker range="o365-worldwide"

1. Dans le centre d’administration SharePoint, accédez à la page <a href="https://admin.microsoft.com/sharepoint?page=siteManagement&modern=true" target="_blank">sites actifs</a> , puis connectez-vous à l’aide d’un compte disposant d' [autorisations d’administrateur](https://docs.microsoft.com/sharepoint/sharepoint-admin-role) pour votre organisation.

2. Dans le coin supérieur droit de la page, reportez-vous à la quantité de stockage utilisée sur tous les sites, ainsi qu’à l’espace de stockage total de votre abonnement. Si votre organisation a configuré l’environnement multi-géo dans Office 365, la barre indique également la quantité de stockage utilisée dans tous les emplacements géographiques.

   ![Barre de stockage sur la page sites actifs](https://docs.microsoft.com/sharepoint/sharepointonline/media/active-sites-storage-bar.png)

   > [!NOTE]
   > Le stockage utilisé n’inclut pas les modifications apportées au cours des 24-48 dernières heures.

::: moniker-end

::: moniker range="o365-germany"

1. Connectez-vous à https://portal.office.de en tant qu’administrateur global ou SharePoint, puis sélectionnez la vignette admin pour ouvrir le centre d’administration. Si vous voyez un message indiquant que vous n’êtes pas autorisé à accéder à la page, cela signifie que vous ne disposez pas des autorisations d’administrateur 365 de Microsoft dans votre organisation.

2. Dans le volet gauche, sous **centres d’administration**, sélectionnez **SharePoint**. Si la version classique du Centre d’administration SharePoint s’affiche, en haut de la page, sélectionnez **Ouvrir maintenant** pour ouvrir la nouvelle version du Centre d’administration SharePoint.

3. Dans le volet gauche du Centre d’administration SharePoint, cliquez sur **Activer des sites**.

4. Dans le coin supérieur droit de la page, reportez-vous à la quantité de stockage utilisée sur tous les sites, ainsi qu’à l’espace de stockage total de votre abonnement.

   ![Barre de stockage sur la page sites actifs](https://docs.microsoft.com/sharepoint/sharepointonline/media/active-sites-storage-bar.png)

   > [!NOTE]
   > Le stockage utilisé n’inclut pas les modifications apportées au cours des 24-48 dernières heures.

::: moniker-end

::: moniker range="o365-21vianet"

1. Connectez-vous à https://login.partner.microsoftonline.cn/ en tant qu’administrateur global ou SharePoint, puis sélectionnez la vignette admin pour ouvrir le centre d’administration. (Si vous voyez un message indiquant que vous n’avez pas l’autorisation d’accéder à la page, cela signifie que vous ne disposez pas des autorisations d’administrateur 365 de Microsoft dans votre organisation.

2. Dans le volet gauche, sous **centres d’administration**, sélectionnez **SharePoint**. Si la version classique du Centre d’administration SharePoint s’affiche, en haut de la page, sélectionnez **Ouvrir maintenant** pour ouvrir la nouvelle version du Centre d’administration SharePoint.

3. Dans le volet gauche du Centre d’administration SharePoint, cliquez sur **Activer des sites**.

4. Dans le coin supérieur droit de la page, reportez-vous à la quantité de stockage utilisée sur tous les sites, ainsi qu’à l’espace de stockage total de votre abonnement.  

   ![Barre de stockage sur la page sites actifs](https://docs.microsoft.com/sharepoint/sharepointonline/media/active-sites-storage-bar.png)

   > [!NOTE]
   > Le stockage utilisé n’inclut pas les modifications apportées au cours des 24-48 dernières heures.

::: moniker-end

Une fois que vous avez déterminé la quantité de stockage utilisée, vous pouvez ajouter ou supprimer de l'espace de stockage pour votre abonnement. Pour savoir quel sera le coût de l’ajout d’espace de stockage, suivez les étapes décrites dans cet article, ainsi que les informations de tarification avant de l’achat.
  
Pour plus d’informations sur la définition des limites de stockage des collections de sites, voir [Manage site collection Storage Limits](https://docs.microsoft.com/sharepoint/manage-site-collection-storage-limits).
  
## <a name="add-storage-to-your-subscription"></a>Ajouter un espace de stockage à votre abonnement

Si vous n’avez pas encore acheté de stockage supplémentaire pour votre abonnement, vous pouvez le faire.

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **facturation ** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">Acheter des services</a>.
2. Au bas de la page **acheter des services** , sélectionnez **compléments**.
3. Sélectionnez le **stockage de fichiers supplémentaire Office 365**.
4. Sur la page **stockage de fichiers supplémentaire Office 365** , si vous le voyez, sélectionnez l’abonnement de base, puis entrez le nombre de gigaoctets de stockage que vous souhaitez ajouter.
5. Sélectionnez **Extraire maintenant**.
6. Sur la page **Comment effectue cette présentation ?** , vérifiez le nombre de gigaoctets de stockage que vous avez sélectionné, vérifiez les informations de tarification, puis cliquez sur **suivant**.
7. Sur la page **terminer la commande** , vérifiez le total. Si vous devez apporter des modifications, sélectionnez **modifier la commande**. Si la commande nécessite une vérification de solvabilité, activez la case à cocher. Lorsque vous avez terminé, sélectionnez **passer la commande** \> **sur Accueil de l’administration**.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à **Billing** la \> page <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">abonnements</a> de facturation.  

2. Sur la page **abonnements** , choisissez l’abonnement auquel vous voulez ajouter de l’espace de stockage, puis sélectionnez **composants additionnels**.

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > Si vous ne voyez pas les **modules**complémentaires et que votre abonnement a été acheté auprès d’un partenaire, sélectionnez Centre de gestion des **licences en volume (VLSC)**.
  
3. Sélectionnez **acheter des modules complémentaires**.

    ![Acheter le lien des modules complémentaires sur la page abonnements du centre d’administration.](../media/f5cbc3fa-90f7-4299-976d-2482f2c69755.png)
  
4. Sur la page **acheter des services** , pointez avec la souris ou appuyez sur le stockage de **fichiers supplémentaire Office 365**, puis sélectionnez **acheter maintenant**.
  
5. Entrez le nombre de licences utilisateur dont vous avez besoin et, si vous le souhaitez, choisissez un abonnement de base. Sélectionnez **Extraire maintenant**.
  
6. Sur la page **Comment effectue cette présentation ?** , vérifiez le nombre de gigaoctets de stockage que vous avez sélectionné, vérifiez les informations de tarification, puis cliquez sur **suivant**.

7. Sur la page **terminer la commande** , sélectionnez passer une **commande**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Abonnements</a>.

2. Sur la page **abonnements** , choisissez l’abonnement auquel vous voulez ajouter de l’espace de stockage, puis sélectionnez **composants additionnels**.

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > Si vous ne voyez pas les **modules**complémentaires et que votre abonnement a été acheté auprès d’un partenaire, sélectionnez Centre de gestion des **licences en volume (VLSC)**.
  
3. Sélectionnez **acheter des modules complémentaires**.

    ![Acheter le lien des modules complémentaires sur la page abonnements du centre d’administration.](../media/f5cbc3fa-90f7-4299-976d-2482f2c69755.png)
  
4. Sur la page **acheter des services** , pointez avec la souris ou appuyez sur le stockage de **fichiers supplémentaire Office 365**, puis sélectionnez **acheter maintenant**.
  
5. Entrez le nombre de licences utilisateur dont vous avez besoin et, si vous le souhaitez, choisissez un abonnement de base. Sélectionnez **Extraire maintenant**.
  
6. Sur la page **Comment effectue cette présentation ?** , vérifiez le nombre de gigaoctets de stockage que vous avez sélectionné, vérifiez les informations de tarification, puis cliquez sur **suivant**.

7. Sur la page **terminer la commande** , sélectionnez passer une **commande**.

::: moniker-end

## <a name="increase-or-decrease-storage"></a>Augmenter ou diminuer l’espace de stockage

Si vous avez déjà acheté le stockage de fichiers supplémentaire via le complément de **stockage de fichiers supplémentaire Office 365** , vous pouvez suivre ces étapes pour augmenter ou réduire l’espace de stockage supplémentaire pour votre abonnement. Vous pouvez réduire l’espace de stockage à 1 gigaoctet. Pour supprimer tout l’espace de stockage supplémentaire, [Contactez le support technique](../admin/contact-support-for-business-products.md).

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Produits</a>.
2. Dans l’onglet **produits** , sélectionnez l’abonnement qui contient le complément de **stockage de fichiers supplémentaire Office 365** .
3. Sur la page Détails du produit, dans la section **modules** complémentaires, sélectionnez **gérer les modules**complémentaires.
4. Dans le volet **gérer les modules** complémentaires, dans la liste **module complémentaire** , choisissez **stockage de fichiers supplémentaire Office 365**.
5. Dans la zone de texte **quantité** , entrez le nombre de Go d’espace de stockage que vous souhaitez pour l’abonnement.
6. Sélectionnez **Enregistrer**.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Abonnements</a>.

2. Sur la page **abonnements** , sélectionnez **composants additionnels**.

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > Si vous ne voyez pas les **modules**complémentaires et que votre abonnement a été acheté auprès d’un partenaire, sélectionnez Centre de gestion des **licences en volume (VLSC)**.
  
3. Sous **stockage de fichiers supplémentaire Office 365**, sélectionnez **modifier la quantité**.

    ![Lien Modifier la quantité.](../media/96473f2b-6ff6-45ec-b1a3-d7b204ac1f6e.png)
  
4. Dans le volet droit, entrez le nombre total de gigaoctets dont vous avez besoin, puis sélectionnez **Envoyer**.

    Par exemple, si vous disposez actuellement de 200 Go d'espace de stockage supplémentaire, mais que vous n'avez besoin que de 100 Go, entrez **100** dans la zone.

5. Sélectionnez **Fermer**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Abonnements</a>.

2. Sur la page **abonnements** , sélectionnez **composants additionnels**.

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > Si vous ne voyez pas les **modules**complémentaires et que votre abonnement a été acheté auprès d’un partenaire, sélectionnez Centre de gestion des **licences en volume (VLSC)**.
  
3. Sous **stockage de fichiers supplémentaire Office 365**, sélectionnez **modifier la quantité**.

    ![Lien Modifier la quantité.](../media/96473f2b-6ff6-45ec-b1a3-d7b204ac1f6e.png)
  
4. Dans le volet droit, entrez le nombre total de gigaoctets dont vous avez besoin, puis sélectionnez **Envoyer**.

    Par exemple, si vous disposez actuellement de 200 Go d'espace de stockage supplémentaire, mais que vous n'avez besoin que de 100 Go, entrez **100** dans la zone.

5. Sélectionnez **Fermer**.

::: moniker-end

## <a name="is-my-plan-eligible-for-office-365-extra-file-storage"></a>Mon plan est-il éligible au stockage de fichiers supplémentaire Office 365 ?

Le stockage de fichiers supplémentaire Office 365 est accessible aux abonnements suivants :
  
- Office 365 Entreprise E1

- Office 365 Entreprise E2

- Office 365 Entreprise E3

- Office 365 Entreprise E4

- Office 365 Entreprise E5

- Office pour le Web avec SharePoint plan 1

- Office pour le Web avec SharePoint plan 2

- SharePoint Online (plan 1)

- SharePoint Online (plan 2)

- Microsoft 365 Business Basic

- Microsoft 365 Business Standard

- Microsoft 365 Business Premium

- Microsoft 365 E3

- Microsoft 365 E5

- Microsoft 365 F1

> [!NOTE]
> Le stockage de fichiers supplémentaire Office 365 est également disponible pour les plans GCC, GCC High et DOD.

## <a name="related-content"></a>Contenu connexe

[Gérer les limites de stockage du site](ttps://docs.microsoft.com/sharepoint/manage-site-collection-storage-limits) (article) \
[Définir l’espace de stockage par défaut pour les utilisateurs de OneDrive](https://docs.microsoft.com/onedrive/set-default-storage-space)(article)
