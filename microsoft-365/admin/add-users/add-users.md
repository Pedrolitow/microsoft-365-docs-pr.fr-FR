---
title: Ajouter des utilisateurs et attribuer des licences
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_O365_TOC
ms.custom:
- okr_smb
- AdminSurgePortfolio
- manage_licenses
search.appverid:
- MET150
description: Découvrez comment ajouter des utilisateurs et attribuer des licences Microsoft 365 simultanément.
ms.date: 07/01/2020
ms.openlocfilehash: a7c5fcf1a129a1d434b6e641688ce4c5d234817d
ms.sourcegitcommit: 223a36a86753fe9cebee96f05ab4c9a144133677
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51760001"
---
# <a name="add-users-and-assign-licenses-at-the-same-time"></a>Ajouter des utilisateurs et attribuer des licences simultanément

Les membres de votre équipe doivent disposer d'un compte d'utilisateur pour se connecter et accéder à [Microsoft 365 for business](https://www.microsoft.com/microsoft-365/business). La façon la plus simple d'ajouter des comptes d'utilisateurs consiste à les ajouter individuellement dans le centre d'administration Microsoft 365. Une fois cette étape effectuée, les utilisateurs disposeront de licences Microsoft 365, d’informations d'identification et de boîtes aux lettres Microsoft 365.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être un administrateur général, de licences ou d’utilisateurs pour attribuer des licences. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="watch-add-users-in-the-admin-center"></a>Vidéo : Ajouter des utilisateurs dans le centre d’administration

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfN?autoplay=false]

> [!NOTE]
> Les étapes illustrées dans la vidéo partent d’un point différent pour procéder à l’ajout d’utilisateurs, cependant les étapes restantes sont les mêmes que celles décrites ci-dessous.

## <a name="add-users-one-at-a-time"></a>Ajouter des utilisateurs un par un

 ::: moniker range="o365-worldwide"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Accédez à **Utilisateurs**  >  **Utilisateurs actifs** puis sélectionnez **Ajouter un utilisateur**.
3. Dans le volet **Configurer les informations de base**, renseignez les informations de base de l’utilisateur, puis sélectionnez **Suivant**.
    - **Nom** Renseignez le nom complet, le nom d'affichage et le nom d'utilisateur.
    - **Domaine** Choisissez le domaine pour le compte de l’utilisateur. Par exemple, pour un nom d'utilisateur Jérôme et un domaine contoso.com, l’utilisateur pourra se connecter en utilisant jerome@contoso.com.
    - **Paramètres du mot de passe** Choisissez d’utiliser un mot de passe généré automatiquement ou un mot de passe fort que vous aurez créé pour l’utilisateur.
    - L’utilisateur devra modifier son mot de passe après 90 jours. Vous pouvez aussi choisir de **demander à cet utilisateur de modifier son mot de passe lors de sa première connexion**.
    - Indiquez si le mot de passe doit être envoyé par e-mail lorsque l’utilisateur est ajouté.
4. Dans le volet **Attribuer des licences de produits**, sélectionnez l’emplacement et la licence adaptée à l’utilisateur. Si vous n’avez pas de licence disponible, vous pouvez toujours ajouter un utilisateur et acheter des licences supplémentaires. Développez l’onglet **Applications** et sélectionnez ou désélectionnez les applications pour lesquelles attribuer les licences à l’utilisateur. Sélectionnez **Suivant**.
5. Dans le volet **Paramètres facultatifs**, développez l’onglet **Rôles** et promouvez cet utilisateur au rôle d’administrateur. Développez l’onglet **Informations du profil** pour ajouter plus d’informations sur l’utilisateur.
6. Sélectionnez **Suivant**, passez en revue les paramètres du nouvel utilisateur, effectuez les changements que vous souhaitez, puis sélectionnez **Finaliser l’ajout**, puis **Fermer**.

## <a name="add-multiple-users-at-the-same-time"></a>Ajouter plusieurs utilisateurs simultanément

Toutes les méthodes suivantes permettent d’ajouter de multiples utilisateurs simultanément :

- **Utiliser une feuille de calcul pour ajouter des utilisateurs en bloc.** Consultez la rubrique [Ajouter plusieurs utilisateurs simultanément](../../enterprise/add-several-users-at-the-same-time.md).
- **Automatiser l'ajouter de comptes et l'attribution de licences.** Consultez la rubrique [Créer des comptes d'utilisateurs avec Microsoft 365 PowerShell](../../enterprise/create-user-accounts-with-microsoft-365-powershell.md). Choisissez cette méthode si vous êtes déjà familiarisé avec l’utilisation des applets de commande Windows PowerShell.
- **Si vous utilisez ActiveDirectory** [Configurer la synchronisation d’annuaires pour Microsoft 365](../../enterprise/set-up-directory-synchronization.md). Utilisez l'outil Azure AD Connect pour répliquer les comptes d'utilisateur Active Directory (et d’autres objets Active Directory) dans Microsoft 365. La synchronisation ajoute uniquement les comptes d'utilisateurs. Vous devez attribuer des licences aux utilisateurs synchronisés pour qu'ils puissent utiliser le courrier et les autres applications Office.
- **Si vous effectuez une migration depuis Exchange** Consultez la rubrique [Méthodes de migration de comptes de messagerie multiples vers Office 365](/Exchange/mailbox-migration/mailbox-migration). Lorsque vous migrez plusieurs boîtes aux lettres vers Microsoft 365 en utilisant une méthode de migration à basculement, intermédiaire ou Exchange hybride, vous ajoutez automatiquement des utilisateurs dans le cadre de la migration. La migration ajoute uniquement les comptes d'utilisateurs. Vous devrez attribuer des licences aux utilisateurs pour qu'ils puissent utiliser le courrier et les autres applications Office. Si vous n’attribuez pas de licence à un utilisateur, sa boîte aux lettres est désactivée à la fin de la période de grâce de 30 jours. Découvrez comment [attribuer des licences à des utilisateurs](../manage/assign-licenses-to-users.md) dans le centre d'administration Microsoft 365.

## <a name="next-steps"></a>Étapes suivantes

Après avoir ajouté un utilisateur, vous recevez une notification par courrier de Microsoft. Ce courrier électronique contient l’identifiant de l’utilisateur et son mot de passe à lui faire parvenir pour qu’il puisse se connecter à Microsoft 365. Nous vous conseillons d'utiliser le processus habituel pour communiquer les nouveaux mots de passe. Partagez le [guide de démarrage rapide pour les employés](https://support.microsoft.com/office/b9700090-ce64-4046-ab92-ce8488a7bc0f) avec vos nouveaux utilisateurs pour mettre certaines choses en place, en leur faisant par exemple découvrir [comment télécharger et installer des applications Office sur un PC ou Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) ou [comment configurer les applications Office et la messagerie électronique sur un appareil mobile](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>Contenu connexe

[Ajouter un nouvel employé dans Microsoft 365](add-new-employee.md) (article)\
[Ajouter plusieurs utilisateurs simultanément dans Microsoft 365](../../enterprise/add-several-users-at-the-same-time.md) (article)\
[Rétablir un utilisateur dans Microsoft 365](restore-user.md) (article)\
[Attribuer des licences aux utilisateurs](../manage/assign-licenses-to-users.md) (article)\
[Supprimer un utilisateur de votre organisation](delete-a-user.md) (article)