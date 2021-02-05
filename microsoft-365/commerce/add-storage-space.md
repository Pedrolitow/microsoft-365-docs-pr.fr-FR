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
description: Découvrez comment ajouter et réduire le stockage de fichiers dans votre abonnement Microsoft 365. Avec un espace de stockage de fichiers supplémentaire, vous pouvez stocker davantage de contenu dans SharePoint Online et OneDrive.
ms.date: ''
ms.openlocfilehash: fd59de31a27a1dd29800ae1d081e1f509f399124
ms.sourcegitcommit: 0d709e9ab0d8d56c5fc11a921298f82e40e122c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2021
ms.locfileid: "50114906"
---
# <a name="add-storage-space-for-your-subscription"></a>Ajouter de l’espace de stockage pour votre abonnement

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet&preserve-view=true).

::: moniker-end

Si vous commencez à manquer d’espace de stockage pour vos collections de sites SharePoint Online et si votre plan est éligible, vous pouvez en ajouter à votre abonnement.  Si le stockage de fichiers supplémentaire **Office 365** ne figure pas dans la liste des modules supplémentaires disponibles, cela signifie que votre plan n’est pas éligible. Pour plus d’informations, voir [Mon plan est-il éligible ?](#is-my-plan-eligible-for-office-365-extra-file-storage)

> [!NOTE]
> Si vous avez acheté votre abonnement par le biais de licences en volume ou d’un programme CSP, vous ne pouvez pas acheter de stockage de fichiers supplémentaire **Office 365** pour votre organisation directement auprès de Microsoft. Contactez votre représentant ou partenaire pour obtenir de l’aide.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être un administrateur global ou SharePoint pour effectuer les tâches de cet article. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../admin/add-users/about-admin-roles.md).

## <a name="view-available-storage"></a>Afficher le stockage disponible

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration SharePoint, rendez-vous sur la page <a href="https://admin.microsoft.com/sharepoint?page=siteManagement&modern=true" target="_blank">Sites actifs</a> et connectez-vous avec un compte qui dispose des [autorisations](https://docs.microsoft.com/sharepoint/sharepoint-admin-role) d’administrateur pour votre organisation.

2. Dans le coin supérieur droit de la page, consultez la quantité d’espace de stockage utilisé sur tous les sites, ainsi que l’espace de stockage total de votre abonnement. Si votre organisation a configuré Multi-Géo dans Office 365, la barre indique également la quantité de stockage utilisée dans tous les emplacements géographiques.

   ![Barre de stockage sur la page des sites actifs](https://docs.microsoft.com/sharepoint/sharepointonline/media/active-sites-storage-bar.png)

   > [!NOTE]
   > L’espace de stockage utilisé n’inclut pas les modifications apportées au cours des 24 à 48 dernières heures.

::: moniker-end

::: moniker range="o365-germany"

1. Connectez-vous en tant qu’administrateur global ou SharePoint, puis sélectionnez la vignette Administrateur https://portal.office.de pour ouvrir le Centre d’administration. Si vous voyez un message vous that you don’t have permission to access the page, it means that you don’t have Microsoft 365 administrator permissions in your organization.

2. Dans le volet gauche, sous **Centres d’administration,** **sélectionnez SharePoint.** Si la version classique du Centre d’administration SharePoint s’affiche, en haut de la page, sélectionnez **Ouvrir maintenant** pour ouvrir la nouvelle version du Centre d’administration SharePoint.

3. Dans le volet gauche du Centre d’administration SharePoint, cliquez sur **Activer des sites**.

4. Dans le coin supérieur droit de la page, consultez la quantité d’espace de stockage utilisé sur tous les sites, ainsi que l’espace de stockage total de votre abonnement.

   ![Barre de stockage sur la page des sites actifs](https://docs.microsoft.com/sharepoint/sharepointonline/media/active-sites-storage-bar.png)

   > [!NOTE]
   > L’espace de stockage utilisé n’inclut pas les modifications apportées au cours des 24 à 48 dernières heures.

::: moniker-end

::: moniker range="o365-21vianet"

1. Connectez-vous en tant qu’administrateur global ou SharePoint, puis sélectionnez la vignette Administrateur https://login.partner.microsoftonline.cn/ pour ouvrir le Centre d’administration. (Si vous voyez un message vous that you don’t have permission to access the page, it means that you don’t have Microsoft 365 administrator permissions in your organization.

2. Dans le volet gauche, sous **Centres d’administration,** **sélectionnez SharePoint.** Si la version classique du Centre d’administration SharePoint s’affiche, en haut de la page, sélectionnez **Ouvrir maintenant** pour ouvrir la nouvelle version du Centre d’administration SharePoint.

3. Dans le volet gauche du Centre d’administration SharePoint, cliquez sur **Activer des sites**.

4. Dans le coin supérieur droit de la page, consultez la quantité d’espace de stockage utilisé sur tous les sites, ainsi que l’espace de stockage total de votre abonnement.  

   ![Barre de stockage sur la page des sites actifs](https://docs.microsoft.com/sharepoint/sharepointonline/media/active-sites-storage-bar.png)

   > [!NOTE]
   > L’espace de stockage utilisé n’inclut pas les modifications apportées au cours des 24 à 48 dernières heures.

::: moniker-end

Une fois que vous avez déterminé la quantité de stockage utilisée, vous pouvez ajouter ou supprimer de l'espace de stockage pour votre abonnement. Pour connaître le coût d’ajout d’espace de stockage, suivez les étapes de cet article et examinez les informations tarifaires avant d’acheter.
  
Pour plus d’informations sur la définition des limites de stockage des collections de sites, voir [Gérer les limites de stockage des collections de sites.](https://docs.microsoft.com/sharepoint/manage-site-collection-storage-limits)
  
## <a name="add-storage-to-your-subscription"></a>Ajouter du stockage à votre abonnement

Si vous n’avez pas encore acheté de stockage supplémentaire pour votre abonnement, vous pouvez le faire.

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">Acheter des services</a>.
2. En bas de la page **Acheter des services,** sélectionnez **Modules.**
3. Sélectionnez **le stockage de fichiers supplémentaire Office 365.**
4. Dans la page Stockage de fichiers supplémentaire **Office 365,** si vous l’affichez, choisissez l’abonnement de base, puis entrez le nombre de gigaoctets de stockage que vous souhaitez ajouter.
5. Sélectionnez **Check out maintenant.**
6. Dans la page À quoi cela ressemble-t-il **?** Vérifiez le nombre de gigaoctets de stockage que vous avez sélectionné, examinez les informations de tarification, puis sélectionnez **Suivant**.
7. Dans la page **Commande complète,** vérifiez le total. Si vous devez apporter des modifications, sélectionnez **Modifier l’ordre.** Si la commande nécessite une vérification de solvabilité, cochez la case. Lorsque vous avez terminé, sélectionnez **Passer une commande** à La page \> **d’accueil de l’administrateur.**

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, allez sur la page  \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Abonnements de facturation.</a>  

2. Dans la page **Abonnements,** choisissez l’abonnement auquel vous souhaitez ajouter de l’espace de stockage, puis sélectionnez **Modules.**

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > Si vous ne voyez pas les **modules** et que votre abonnement a été acheté par l’intermédiaire d’un partenaire, sélectionnez Centre de gestion des licences en **volume (VLSC).**
  
3. Sélectionnez **Acheter des modules.**

    ![Lien Acheter des modules add-on sur la page Abonnements du Centre d’administration.](../media/f5cbc3fa-90f7-4299-976d-2482f2c69755.png)
  
4. Dans la page **Acheter des services,** pointez avec la souris ou appuyez sur Stockage de fichiers **supplémentaire Office 365,** puis **sélectionnez Acheter maintenant.**
  
5. Entrez le nombre de licences utilisateur dont vous avez besoin et, si vous le souhaitez, choisissez un abonnement de base. Sélectionnez **Check out maintenant.**
  
6. Dans la page À quoi cela ressemble-t-il **?** Vérifiez le nombre de gigaoctets de stockage que vous avez sélectionné, examinez les informations de tarification, puis sélectionnez **Suivant**.

7. Dans la page **Commande complète,** sélectionnez **Commande par ordre.**

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Abonnements</a>.

2. Dans la page **Abonnements,** choisissez l’abonnement auquel vous souhaitez ajouter de l’espace de stockage, puis sélectionnez **Modules.**

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > Si vous ne voyez pas les **modules** et que votre abonnement a été acheté par l’intermédiaire d’un partenaire, sélectionnez Centre de gestion des licences en **volume (VLSC).**
  
3. Sélectionnez **Acheter des modules.**

    ![Lien Acheter des modules add-on sur la page Abonnements du Centre d’administration.](../media/f5cbc3fa-90f7-4299-976d-2482f2c69755.png)
  
4. Dans la page **Acheter des services,** pointez avec la souris ou appuyez sur Stockage de fichiers **supplémentaire Office 365,** puis **sélectionnez Acheter maintenant.**
  
5. Entrez le nombre de licences utilisateur dont vous avez besoin et, si vous le souhaitez, choisissez un abonnement de base. Sélectionnez **Check out maintenant.**
  
6. Dans la page À quoi cela ressemble-t-il **?** Vérifiez le nombre de gigaoctets de stockage que vous avez sélectionné, examinez les informations de tarification, puis sélectionnez **Suivant**.

7. Dans la page **Commande complète,** sélectionnez **Commande par ordre.**

::: moniker-end

## <a name="increase-or-decrease-storage"></a>Augmenter ou diminuer l’espace de stockage

Si vous avez déjà acheté du stockage de fichiers supplémentaire via le module supplémentaire stockage de fichiers **Office 365,** vous pouvez suivre ces étapes pour augmenter ou réduire l’espace de stockage supplémentaire pour votre abonnement. Vous pouvez réduire le stockage jusqu’à 1 gigaoctet. Pour supprimer tout l’espace de stockage supplémentaire, [contactez le support technique.](../admin/contact-support-for-business-products.md)

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous **l’onglet** Produits, sélectionnez l’abonnement qui contient le module supplémentaire de stockage de fichiers **Office 365.**
3. Dans la page détails du produit, dans la section **Modules,** sélectionnez **Gérer les modules.**
4. In the **Manage add-ons** pane, from the **Add-on** list, choose **Office 365 Extra File Storage**.
5. Dans la **zone de texte** Quantité, entrez le nombre de GB d’espace de stockage que vous souhaitez pour l’abonnement.
6. Sélectionnez **Enregistrer**.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Abonnements</a>.

2. Dans la page **Abonnements,** **sélectionnez Modules.**

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > Si vous ne voyez pas les **modules** et que votre abonnement a été acheté par l’intermédiaire d’un partenaire, sélectionnez Centre de gestion des licences en **volume (VLSC).**
  
3. Sous **Stockage de fichiers supplémentaire Office 365,** sélectionnez Modifier la **quantité.**

    ![Lien Modifier la quantité.](../media/96473f2b-6ff6-45ec-b1a3-d7b204ac1f6e.png)
  
4. Dans le volet droit, entrez le nombre total de gigaoctets dont vous avez besoin, puis sélectionnez **Envoyer.**

    Par exemple, si vous disposez actuellement de 200 Go d'espace de stockage supplémentaire, mais que vous n'avez besoin que de 100 Go, entrez **100** dans la zone.

5. Sélectionnez **Fermer**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Abonnements</a>.

2. Dans la page **Abonnements,** **sélectionnez Modules.**

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > Si vous ne voyez pas les **modules** et que votre abonnement a été acheté par l’intermédiaire d’un partenaire, sélectionnez Centre de gestion des licences en **volume (VLSC).**
  
3. Sous **Stockage de fichiers supplémentaire Office 365,** sélectionnez Modifier la **quantité.**

    ![Lien Modifier la quantité.](../media/96473f2b-6ff6-45ec-b1a3-d7b204ac1f6e.png)
  
4. Dans le volet droit, entrez le nombre total de gigaoctets dont vous avez besoin, puis sélectionnez **Envoyer.**

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

- Office pour le web avec SharePoint Plan 1

- Office pour le web avec SharePoint Plan 2

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

[Gérer les limites de stockage de](ttps://docs.microsoft.com/sharepoint/manage-site-collection-storage-limits) site (article)\
[Définir l’espace de stockage par défaut pour les utilisateurs de OneDrive](https://docs.microsoft.com/onedrive/set-default-storage-space)(article)
