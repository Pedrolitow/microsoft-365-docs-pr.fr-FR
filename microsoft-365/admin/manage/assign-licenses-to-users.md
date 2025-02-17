---
title: Attribuer des licences utilisateur dans le Centre d’administration Microsoft 365
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- Tier1
- scotvorg
- highpri
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- commerce_licensing
- VSBFY23
- AdminSurgePortfolio
- TopSMBIssues
- SaRA
- business_assist
- okr_SMB
- manage_licenses
- AdminTemplateSet
search.appverid: MET150
description: Attribuez des licences selon que vous voulez attribuer des licences de produits à des utilisateurs spécifiques ou attribuer des licences d'utilisateurs à un produit spécifique.
ms.date: 07/12/2022
ms.openlocfilehash: e076ffaea87f8aba3cc7df46177c7132ff8ae210
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68731368"
---
# <a name="assign-microsoft-365-licenses-to-users"></a>Attribuer des licences Microsoft 365 aux utilisateurs

Vous pouvez attribuer des licences à des utilisateurs à partir de la page des **Utilisateurs actifs** ou de la page des **Licences**. La méthode utilisée dépend de votre souhait d’attribuer des licences de produit à des utilisateurs déterminés ou d’attribuer des licences aux utilisateurs pour un produit spécifique.

> [!NOTE]
> 
> - En tant qu’administrateur, vous ne pouvez pas attribuer ou annuler des attributions de licences pour un abonnement d’achat en libre-service acheté par un utilisateur de votre organisation. Vous pouvez [prendre le contrôle d’un abonnement d’achat en libre-service](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription), puis attribuer ou annuler des attributions de licences.
> - Pour certains abonnements, vous ne pouvez annuler l’abonnement que pendant une période limitée après l’achat ou le renouvellement de votre abonnement. Si la période d’annulation est écoulée, désactiver la facturation périodique pour annuler l’abonnement à la fin de sa période.

[Découvrez comment ajouter un utilisateur et attribuer une licence en même temps](../add-users/add-users.md).

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="before-you-begin"></a>Avant de commencer

- You must be a Global, License, or User admin to assign licenses. For more information, see [About Microsoft 365 admin roles](../add-users/about-admin-roles.md).
- Vous pouvez [attribuer des licences Microsoft 365 à des comptes utilisateurs avec PowerShell](../../enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell.md).
- Pour utiliser la gestion des licences basée sur les groupes, voir [Attribuer des licences aux utilisateurs par appartenance aux groupes dans Azure Active Directory](/azure/active-directory/users-groups-roles/licensing-groups-assign)
- Certains services, tels que Sway, sont automatiquement attribués aux utilisateurs et n’ont donc pas besoin d’être attribués individuellement.

## <a name="use-the-licenses-page-to-assign-licenses-to-users"></a>Utiliser la page licences pour attribuer des licences aux utilisateurs

La page **Licences** vous permet d’attribuer ou de désattribuer des licences pour jusqu’à 20 utilisateurs à la fois. La page affiche les produits que vous possédez, le nombre de licences disponibles pour chaque produit et le nombre de licences attribuées sur le nombre total de licences disponibles.

La page **Licences** affiche un total agrégé de licences pour tous les abonnements pour le même nom de produit. Par exemple, vous pouvez avoir un abonnement pour Microsoft 365 Business Premium qui a 5 licences et un autre abonnement qui a 8 licences pour le même produit. La page **Licences** indique que vous disposez d’un total de 13 licences pour Microsoft 365 Business Premium sur tous vos abonnements. Cela est différent de ce que vous voyez sur la page **Vos produits** , qui affiche une ligne pour chaque abonnement que vous possédez, même s’ils concernent le même produit.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Licences</a>.

::: moniker-end

2. Sélectionnez un produit.

3. Dans la page Détails du produit, sélectionnez **attribuer des licences**.

4. In the **Assign licenses to users** pane, begin typing a name, and then choose it from the results to add it to the list. You can add up to 20 users at a time.

5. Sélectionnez **Activer ou désactiver les applications et les services** pour attribuer ou supprimer l’accès à des éléments particuliers.

6. Lorsque vous avez terminé, sélectionnez **Affecter**, puis fermez le volet droit.

En cas de conflit, un message s’affiche pour vous indiquer ce qu’est le problème et comment le résoudre. Par exemple, si vous avez sélectionné des licences contenant des services en conflit, le message d’erreur indique de vérifier les services inclus dans chaque licence et de réessayer.

## <a name="change-the-apps-and-services-a-user-has-access-to"></a>Modifier les applications et les services auxquels un utilisateur a accès

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Licences</a>.

::: moniker-end

2. Dans la page **Licences**, sélectionnez la ligne d’un utilisateur spécifique.

3. Dans le volet droit, sélectionnez ou désélectionnez les applications et services auxquels vous voulez octroyer ou supprimer l'accès.

4. Une fois terminé, sélectionnez **Enregistrer**, puis choisissez **Fermer**.

## <a name="use-the-active-users-page-to-assign-licenses"></a>Utiliser la page utilisateurs actifs pour attribuer des licences

Lorsque vous utilisez la page **Utilisateurs actifs** pour attribuer des licences, vous attribuez des licences aux produits pour les utilisateurs.

### <a name="assign-licenses-to-multiple-users"></a>Attribuer des licences à plusieurs utilisateurs

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez les cercles en regard des noms d'utilisateurs auxquels vous voulez attribuer des licences.

3. Dans la partie supérieure, sélectionnez **Gérer des licences de produits**.

4. Dans le volet **Gérer les licences de produits**, sélectionnez **Affecter plus : conserver les licences existantes et en affecter d’autres** \> **Suivant**.

5. Sous **Licences**, sélectionnez la case pour la ou les licences que vous souhaitez attribuer aux utilisateurs sélectionnés.
    By default, all services associated with those licenses are automatically assigned to the users. You can limit which services are available to the users. Deselect the boxes for the services that you don't want the users to have.

6. Dans la partie inférieure du volet, sélectionnez **Enregistrer les modifications**.  
    Vous devrez peut-être acheter d’autres licences si leur nombre est insuffisant pour tout le monde.

> [!NOTE]
> Si vous voulez attribuer des licences à un grand nombre d’utilisateurs, utilisez [Attribuer des licences aux utilisateurs en les appartenance aux groupes dans Azure Active Directory.](/azure/active-directory/enterprise-users/licensing-groups-assign)

### <a name="assign-licenses-to-one-user"></a>Attribuer des licences à un utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez la ligne de l’utilisateur auquel vous voulez attribuer une licence.

3. Dans le volet de droite, sélectionnez **Licences et applications**.

4. Développez la section **Licences**, sélectionnez les cases des licences à attribuer, puis choisissez **Enregistrer les modifications**.

## <a name="assign-a-license-to-a-guest-user"></a>Attribuer une licence à un utilisateur invité

Vous pouvez inviter des utilisateurs invités à collaborer avec votre organisation dans le Centre d’administration Azure Active Directory. Pour en savoir plus sur l’estimation des utilisateurs, consultez[Qu’est-ce que l’accès utilisateur invité dans Azure Active Directory B2B ?](/azure/active-directory/external-identities/what-is-b2b). Si vous n’avez pas d’utilisateurs invités, consultez [Démarrage rapide : ajouter des utilisateurs invités à votre annuaire dans le portail Azure](/azure/active-directory/external-identities/b2b-quickstart-add-guest-users-portal).

> [!IMPORTANT]
> Vous devez être un administrateur général pour effectuer ces étapes.

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2067268" target="_blank">Centre d’administration Azure Active Directory</a>.

2. Dans le volet de navigation, sélectionnez **Utilisateurs**.

3. Dans la page **utilisateurs | Tous les utilisateurs (aperçu)**, sélectionnez **Ajouter des filtres**.

4. Dans le menu **Sélectionner un champ** , sélectionnez **Type d’utilisateur**, puis **Appliquer**.

5. Dans le menu suivant, sélectionnez **Invité**.

6. Dans la liste des résultats, sélectionnez l’utilisateur ayant besoin d’une licence.

7. Sous **Gérer**, sélectionnez **Licences**.

8. Sélectionnez **Devoirs**.

9. Sur la page **Mettre à jour les affectations de licence** , sélectionnez le produit pour lequel vous voulez affecter une licence.

10. Sur la droite, désactivez les cases à cocher des services auxquels vous ne voulez pas que l’utilisateur invité ait accès.

11. Sélectionnez **Enregistrer**.

## <a name="next-steps"></a>Étapes suivantes

Si les applications Office ne sont pas encore installées sur vos utilisateurs, vous pouvez partager le[Guide de démarrage rapide d’employées](../setup/employee-quick-setup.md) avec vos utilisateurs pour configurer des éléments, par [comment télécharger et installer Microsoft 365 ou Office 2019 sur un PC ou Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) et [comment configurer les applications Office et la messagerie électronique sur un appareil mobile](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>Contenu connexe

[Comprendre les abonnements et les licences](../../commerce/licenses/subscriptions-and-licenses.md) (article)\
[Déattribuer des licences aux utilisateurs](remove-licenses-from-users.md) (article)\
[Achetez ou supprimez des licences pour votre abonnement](../../commerce/licenses/buy-licenses.md) (article)
