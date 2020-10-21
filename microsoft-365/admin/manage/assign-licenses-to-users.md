---
title: Attribuer des licences aux utilisateurs
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_TOC
- commerce
ms.custom:
- TopSMBIssues
- SaRA
- okr_SMB
- AdminSurgePortfolio
- manage_licenses
search.appverid:
- MET150
description: Découvrez comment attribuer des licences aux utilisateurs.
ms.date: 08/14/2020
ms.openlocfilehash: ec2f9ae2e580987266c636343a66d7c21138e4c3
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48645130"
---
# <a name="assign-licenses-to-users"></a>Attribuer des licences aux utilisateurs

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

::: moniker range="o365-worldwide"

Vous pouvez attribuer des licences à des utilisateurs à partir de la page des **Utilisateurs actifs** ou de la page des **Licences**. La méthode utilisée dépend de votre souhait d’attribuer des licences de produit à des utilisateurs déterminés ou d’attribuer des licences aux utilisateurs pour un produit spécifique.

::: moniker-end

[Découvrez comment ajouter un utilisateur et attribuer une licence en même temps](../add-users/add-users.md).

## <a name="before-you-begin"></a>Avant de commencer

- Vous devez être un administrateur général, une licence ou un administrateur d’utilisateur pour attribuer des licences. Si vous souhaitez en savoir plus, consultez l’article [À propos des rôles d’administrateur Microsoft 365](../add-users/about-admin-roles.md).
- Vous pouvez [attribuer des licences à des comptes utilisateurs avec Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=850410).
- Pour utiliser la gestion des licences basée sur les groupes, voir [Attribuer des licences aux utilisateurs par appartenance aux groupes dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-groups-assign)
- Certains services, tels que Sway, sont automatiquement attribués aux utilisateurs et n’ont donc pas besoin d’être attribués individuellement.

::: moniker range="o365-worldwide"

## <a name="use-the-licenses-page-to-assign-licenses-to-users"></a>Utiliser la page licences pour attribuer des licences aux utilisateurs

Lorsque vous utilisez la page **Licences** pour l'attribution de licences, vous attribuez des licences pour un produit spécifique à un maximum de 20 utilisateurs. Dans la page **Licences**, une liste de tous les produits auxquels vous avez des abonnements s’affiche. Vous pouvez également voir le nombre total de licences pour chaque produit, le nombre de licences attribuées et le nombre de licences disponibles.

1. Dans le Centre d’administration, choisissez la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>.
2. Sélectionnez un produit.
3. Dans la page Détails du produit, sélectionnez **attribuer des licences**.
4. Dans le volet **Attribuer des licences aux utilisateurs**, commencez à saisir un nom, puis sélectionnez-le dans les résultats pour l’ajouter à la liste. Vous pouvez ajouter jusqu'à 20 utilisateurs à la fois.
5. Sélectionnez **Activer ou désactiver les applications et les services** pour attribuer ou supprimer l’accès à des éléments particuliers.
6. Lorsque vous avez terminé, sélectionnez **Attribuer**, puis choisissez **Fermer**.

S’il existe un conflit, un message s’affiche, vous indiquant la nature du problème et comment le résoudre. Par exemple, si vous avez sélectionné des licences contenant des services en conflit, le message d’erreur indique de vérifier les services inclus dans chaque licence et de réessayer.

## <a name="change-the-apps-and-services-a-user-has-access-to"></a>Modifier les applications et les services auxquels un utilisateur a accès

1. Dans le Centre d’administration, choisissez la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>.
2. Dans la page **Licences**, sélectionnez la ligne d’un utilisateur spécifique.
3. Dans le volet droit, sélectionnez ou désélectionnez les applications et services auxquels vous voulez octroyer ou supprimer l'accès.
4. Une fois terminé, sélectionnez **Enregistrer**, puis choisissez **Fermer**.

::: moniker-end

::: moniker range="o365-worldwide"

## <a name="use-the-active-users-page-to-assign-licenses"></a>Utiliser la page utilisateurs actifs pour attribuer des licences

Lorsque vous utilisez la page **Utilisateurs actifs** pour attribuer des licences, vous attribuez des licences aux produits pour les utilisateurs.

### <a name="assign-licenses-to-multiple-users"></a>Attribuer des licences à plusieurs utilisateurs

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez les cercles en regard des noms d'utilisateurs auxquels vous voulez attribuer des licences.
3. Dans la partie supérieure, sélectionnez **Plus d'options (...)**, puis choisissez **Gérer les licences de produits**.
4. Dans le volet **Attribuer des licences de produits**, sélectionnez **Ajouter aux attributions de licence de produit existantes** \> **Suivant**.
5. Dans le volet **Ajouter aux produits existants**, positionnez le bouton bascule sur **Actif**correspondant à la licence que vous voulez attribuer aux utilisateurs sélectionnés.\
    Par défaut, tous les services associés à ces licences sont automatiquement attribués aux utilisateurs. Vous pouvez limiter les services mis à disposition des utilisateurs. Positionnez le bouton bascule sur **Inactif** pour les services que vous ne souhaitez pas attribuer aux utilisateurs.
6. Dans la partie inférieure du volet, sélectionnez **Ajouter** \> **Fermer**.  

::: moniker-end

::: moniker range="o365-germany"

## <a name="assign-licenses-to-multiple-users"></a>Attribuer des licences à plusieurs utilisateurs

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.
2. Cochez les cases en regard des noms des utilisateurs auxquels vous voulez attribuer des licences.
3. Dans le volet **Actions en bloc**, sélectionnez **Modifier les licences de produits**.
4. Dans le volet **Attribuer des produits**, sélectionnez **Ajouter aux attributions de licence de produit existantes** \> **Suivant**.
5. Positionnez le bouton bascule sur **Activer** pour les licences que vous voulez attribuer aux utilisateurs sélectionnés.\
    Par défaut, tous les services associés à ces licences sont automatiquement attribués aux utilisateurs. Vous pouvez limiter les services mis à disposition des utilisateurs. Positionnez le bouton bascule sur **Inactif** pour les services que vous ne souhaitez pas attribuer aux utilisateurs.
6. Dans la partie inférieure du volet **Ajouter aux produits existants**, sélectionnez **Ajouter** \> **Fermer** \> **Fermer**.

::: moniker-end

::: moniker range="o365-21vianet"

## <a name="assign-licenses-to-multiple-users"></a>Attribuer des licences à plusieurs utilisateurs

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.
2. Cochez les cases en regard des noms des utilisateurs auxquels vous voulez attribuer des licences.
3. Dans le volet **Actions en bloc**, sélectionnez **Modifier les licences de produits**.
4. Dans le volet **Attribuer des produits**, sélectionnez **Ajouter aux attributions de licence de produit existantes** \> **Suivant**.
5. Positionnez le bouton bascule sur **Activer** pour les licences que vous voulez attribuer aux utilisateurs sélectionnés.\
    Par défaut, tous les services associés à ces licences sont automatiquement attribués aux utilisateurs. Vous pouvez limiter les services mis à disposition des utilisateurs. Positionnez le bouton bascule sur **Inactif** pour les services que vous ne souhaitez pas attribuer aux utilisateurs.
6. Dans la partie inférieure du volet **Ajouter aux produits existants**, sélectionnez **Ajouter** \> **Fermer** \> **Fermer**.

::: moniker-end

::: moniker range="o365-worldwide"

### <a name="assign-licenses-to-one-user"></a>Attribuer des licences à un utilisateur

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez la ligne de l’utilisateur auquel vous voulez attribuer une licence.
3. Dans le volet de droite, sélectionnez **Licences et applications**.
4. Développez la section **Licences**, sélectionnez les cases des licences à attribuer, puis choisissez **Enregistrer les modifications**.

::: moniker-end

::: moniker range="o365-germany"

## <a name="assign-licenses-to-one-user"></a>Attribuer des licences à un utilisateur

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.
2. Cochez la case en regard du nom de l’utilisateur auquel vous voulez attribuer une licence.
3. Dans le volet de droite, sur la ligne **Licences de produits**, sélectionnez **Modifier**.
4. Dans le volet **Licences de produits**, **activez** le bouton bascule correspondant à la licence que vous voulez attribuer à cet utilisateur.\
    Par défaut, tous les services associés à cette licence sont automatiquement attribués à l'utilisateur. Vous pouvez limiter les services mis à disposition de l'utilisateur. Positionnez le bouton bascule sur **Inactif** pour les services que vous ne souhaitez pas attribuer à l'utilisateur.
5. En bas du volet **Licences de produits**, sélectionnez **Enregistrer** \> **Fermer** \> **Fermer**.

::: moniker-end

::: moniker range="o365-21vianet"

## <a name="assign-licenses-to-one-user"></a>Attribuer des licences à un utilisateur

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.
2. Cochez la case en regard du nom de l’utilisateur auquel vous voulez attribuer une licence.
3. Dans le volet de droite, sur la ligne **Licences de produits**, sélectionnez **Modifier**.
4. Dans le volet **Licences de produits**, **activez** le bouton bascule correspondant à la licence que vous voulez attribuer à cet utilisateur.\
    Par défaut, tous les services associés à cette licence sont automatiquement attribués à l'utilisateur. Vous pouvez limiter les services mis à disposition de l'utilisateur. Positionnez le bouton bascule sur **Inactif** pour les services que vous ne souhaitez pas attribuer à l'utilisateur.
5. En bas du volet **Licences de produits**, sélectionnez **Enregistrer** \> **Fermer** \> **Fermer**.

::: moniker-end

## <a name="assign-a-license-to-a-guest-user"></a>Attribuer une licence à un utilisateur invité

Vous pouvez inviter des utilisateurs invités à collaborer avec votre organisation dans le Centre d’administration Azure Active Directory. Pour en savoir plus sur l’estimation des utilisateurs, consultez[Qu’est-ce que l’accès utilisateur invité dans Azure Active Directory B2B ?](https://docs.microsoft.com/azure/active-directory/external-identities/what-is-b2b) Si vous n’avez pas d’utilisateurs invités, consultez [Démarrage rapide : ajouter des utilisateurs invités à votre annuaire dans le portail Azure](https://docs.microsoft.com/azure/active-directory/external-identities/b2b-quickstart-add-guest-users-portal).

> [!IMPORTANT]
> Vous devez être un administrateur général pour effectuer ces étapes.

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2067268" target="_blank">Centre d’administration Azure Active Directory</a>
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

Si les applications Office ne sont pas encore installées sur vos utilisateurs, vous pouvez partager le[Guide de démarrage rapide d’employées](https://support.microsoft.com/office/b9700090-ce64-4046-ab92-ce8488a7bc0f) avec vos utilisateurs pour configurer des éléments, par [comment télécharger et installer Microsoft 365 ou Office 2019 sur un PC ou Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) et [comment configurer les applications Office et la messagerie électronique sur un appareil mobile](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>Contenu connexe

[Comprendre les abonnements et les licences](../../commerce/licenses/subscriptions-and-licenses.md) (article)\
[Déattribuer des licences aux utilisateurs](remove-licenses-from-users.md) (article)\
[Achetez ou supprimez des licences pour votre abonnement](../../commerce/licenses/buy-licenses.md) (article)