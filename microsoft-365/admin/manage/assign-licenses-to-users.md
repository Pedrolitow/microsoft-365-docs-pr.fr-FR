---
title: Attribuer des licences aux utilisateurs
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- TopSMBIssues
- SaRA
- okr_SMB
- manage_licenses
- commerce_licensing
- AdminTemplateSet
search.appverid: MET150
description: Attribuez des licences selon que vous voulez attribuer des licences de produits à des utilisateurs spécifiques ou attribuer des licences d'utilisateurs à un produit spécifique.
ms.date: 09/16/2021
ms.openlocfilehash: b9fb8a670b649437a894619369731a5085c36804
ms.sourcegitcommit: 24bff8a546491ff32ebf04d1f51abb3197035706
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2021
ms.locfileid: "59785938"
---
# <a name="assign-licenses-to-users"></a>Attribuer des licences aux utilisateurs

Vous pouvez attribuer des licences à des utilisateurs à partir de la page des **Utilisateurs actifs** ou de la page des **Licences**. La méthode utilisée dépend de votre souhait d’attribuer des licences de produit à des utilisateurs déterminés ou d’attribuer des licences aux utilisateurs pour un produit spécifique.

> [!NOTE]
> 
> - En tant qu’administrateur, vous ne pouvez pas attribuer ou annuler des attributions de licences pour un abonnement d’achat en libre-service acheté par un utilisateur de votre organisation. Vous pouvez [prendre le contrôle d’un abonnement d’achat en libre-service](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription), puis attribuer ou annuler des attributions de licences.
> - Pour certains abonnements, vous ne pouvez annuler l’abonnement que pendant une période limitée après l’achat ou le renouvellement de votre abonnement. Si la période d’annulation est écoulée, désactiver la facturation périodique pour annuler l’abonnement à la fin de sa période.

[Découvrez comment ajouter un utilisateur et attribuer une licence en même temps](../add-users/add-users.md).

## <a name="before-you-begin"></a>Avant de commencer

- Vous devez être un administrateur général, une licence ou un administrateur d’utilisateur pour attribuer des licences. Si vous souhaitez en savoir plus, consultez l’article [À propos des rôles d’administrateur Microsoft 365](../add-users/about-admin-roles.md).
- Vous pouvez [attribuer des licences Microsoft 365 à des comptes utilisateurs avec PowerShell](../../enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell.md).
- Pour utiliser la gestion des licences basée sur les groupes, voir [Attribuer des licences aux utilisateurs par appartenance aux groupes dans Azure Active Directory](/azure/active-directory/users-groups-roles/licensing-groups-assign)
- Certains services, tels que Sway, sont automatiquement attribués aux utilisateurs et n’ont donc pas besoin d’être attribués individuellement.


## <a name="use-the-licenses-page-to-assign-licenses-to-users"></a>Utiliser la page licences pour attribuer des licences aux utilisateurs

Lorsque vous utilisez la page **Licences** pour l'attribution de licences, vous attribuez des licences pour un produit spécifique à un maximum de 20 utilisateurs. Dans la page **Licences**, une liste de tous les produits auxquels vous avez des abonnements s’affiche. Vous pouvez également voir le nombre total de licences pour chaque produit, le nombre de licences attribuées et le nombre de licences disponibles.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=848038" target="_blank">Licences</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Licences</a>.

::: moniker-end

2. Sélectionnez un produit.

3. Dans la page Détails du produit, sélectionnez **attribuer des licences**.

4. Dans le volet **Attribuer des licences aux utilisateurs**, commencez à saisir un nom, puis sélectionnez-le dans les résultats pour l’ajouter à la liste. Vous pouvez ajouter jusqu'à 20 utilisateurs à la fois.

4. Sélectionnez **Activer ou désactiver les applications et les services** pour attribuer ou supprimer l’accès à des éléments particuliers.

6. Lorsque vous avez terminé, sélectionnez **Attribuer**, puis choisissez **Fermer**.

S’il existe un conflit, un message s’affiche, vous indiquant la nature du problème et comment le résoudre. Par exemple, si vous avez sélectionné des licences contenant des services en conflit, le message d’erreur indique de vérifier les services inclus dans chaque licence et de réessayer.

## <a name="change-the-apps-and-services-a-user-has-access-to"></a>Modifier les applications et les services auxquels un utilisateur a accès

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=848038" target="_blank">Licences</a>.

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

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez les cercles en regard des noms d'utilisateurs auxquels vous voulez attribuer des licences.

3. Dans la partie supérieure, sélectionnez **Gérer des licences de produits**.

4. Dans le volet **Gérer les licences de produits**, sélectionnez **Affecter plus : conserver les licences existantes et en affecter d’autres** \> **Suivant**.

5. Sous **Licences**, sélectionnez la case pour la ou les licences que vous souhaitez attribuer aux utilisateurs sélectionnés.
    Par défaut, tous les services associés à ces licences sont automatiquement attribués aux utilisateurs. Pour limiter les services auxquels peuvent accéder les utilisateurs, désactivez les cases correspondant aux services concernés.

6. Dans la partie inférieure du volet, sélectionnez **Enregistrer les modifications**.  
    Vous devrez peut-être acheter d’autres licences si leur nombre est insuffisant pour tout le monde.

> [!NOTE]
> Si vous voulez attribuer des licences à un grand nombre d’utilisateurs, utilisez [Attribuer des licences aux utilisateurs en les appartenance aux groupes dans Azure Active Directory.](/azure/active-directory/enterprise-users/licensing-groups-assign)

### <a name="assign-licenses-to-one-user"></a>Attribuer des licences à un utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

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

Si les applications Office ne sont pas encore installées sur vos utilisateurs, vous pouvez partager le[Guide de démarrage rapide d’employées](../../business-video/employee-quick-setup.md) avec vos utilisateurs pour configurer des éléments, par [comment télécharger et installer Microsoft 365 ou Office 2019 sur un PC ou Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) et [comment configurer les applications Office et la messagerie électronique sur un appareil mobile](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>Contenu connexe

[Comprendre les abonnements et les licences](../../commerce/licenses/subscriptions-and-licenses.md) (article)\
[Déattribuer des licences aux utilisateurs](remove-licenses-from-users.md) (article)\
[Achetez ou supprimez des licences pour votre abonnement](../../commerce/licenses/buy-licenses.md) (article)
