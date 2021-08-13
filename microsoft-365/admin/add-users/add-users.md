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
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Chaque membre de l’équipe a besoin d’un compte d’utilisateur avant de pouvoir se connecter et accéder à Microsoft 365 pour les entreprises. Apprenez comment ajouter des utilisateurs et attribuer des licences.
ms.date: 07/01/2020
ms.openlocfilehash: 5d18bfbd396bc13496cc06c80dcb5cc6fbf7f84e9432936c1d745877f0074141
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53815898"
---
# <a name="add-users-and-assign-licenses-at-the-same-time"></a>Ajouter des utilisateurs et attribuer des licences simultanément

Les membres de votre équipe ont besoin d'un compte d'utilisateur pour se connecter et accéder à [Microsoft 365 pour les entreprises](https://www.microsoft.com/microsoft-365/business). La façon la plus simple d'ajouter des comptes d'utilisateurs consiste à les ajouter individuellement dans le Centre d'administration Microsoft 365. Après avoir effectué cette étape, vos utilisateurs disposent de licences Microsoft 365, d'informations d'identification de connexion et de boîtes aux lettres Microsoft 365.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être un administrateur général, de licences ou d’utilisateurs pour attribuer des licences. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="add-a-user-in-the-admin-simplified-view"></a>Ajouter un utilisateur dans le mode simplifié administrateur

Si vous voyez cette page dans le Centre d'administration, vous êtes dans le **mode simplifié administrateur**. Suivez les étapes ci-dessous permettant d’ajouter un utilisateur.

:::image type="content" source="../../media/vsb-add-user-view.png" alt-text="Capture d’écran : mode simplifié du Centre d'administration":::

::: moniker range="o365-worldwide"

1. Accédez au centre d’administration sur <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-germany"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Sélectionnez **Créer un compte pour une autre personne**.
3. Sur la page **Ajouter un compte utilisateur**, remplissez le prénom et le nom, le nom d'affichage et le nom d'utilisateur qu’il utilisera pour se connecter.
4. Ajoutez l’adresse e-mail de l’utilisateur dans la zone de texte **Jusqu’à 5 adresses e-mail...**. Ceci permettra de s’assurer que le nouvel utilisateur reçoive les informations dont il a besoin pour se connecter aux services Microsoft 365.
5. Sélectionnez **Ajouter un utilisateur**, puis **Télécharger les informations de connexion** si vous souhaitez les enregistrer.

## <a name="watch-add-users-in-the-dashboard-view"></a>Vidéo : Ajouter des utilisateurs dans l’affichage du tableau de bord

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfN?autoplay=false]

> [!NOTE]
> Les étapes illustrées dans la vidéo partent d’un point différent pour procéder à l’ajout d’utilisateurs, cependant les étapes restantes sont les mêmes que celles décrites ci-dessous.

## <a name="add-users-one-at-a-time-in-the-dashboard-view"></a>Ajouter un utilisateur à la fois dans l’affichage du tableau de bord

:::image type="content" source="../../media/classic-admin-center.png" alt-text="Capture d’écran : affichage du tableau de bord du Centre d'administration":::

::: moniker range="o365-worldwide"

1. Accédez au centre d’administration sur<https://admin.microsoft.com>.

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
    - L’utilisateur devra modifier son mot de passe après 90 jours. Vous pouvez aussi choisir d’**Exiger de cet utilisateur qu’il modifie son mot de passe lors de sa première connexion**.
    - Indiquez si le mot de passe doit être envoyé par e-mail lorsque l’utilisateur est ajouté.
4. Dans le volet **Attribuer des licences de produits**, sélectionnez l’emplacement et la licence adaptée à l’utilisateur. Si vous n’avez pas de licence disponible, vous pouvez toujours ajouter un utilisateur et acheter des licences supplémentaires. Développez l’onglet **Applications** et sélectionnez ou désélectionnez les applications pour lesquelles attribuer les licences à l’utilisateur. Sélectionnez **Suivant**.
5. Dans le volet **Paramètres facultatifs**, développez l’onglet **Rôles** et promouvez cet utilisateur au rôle d’administrateur. Développez l’onglet **Informations du profil** pour ajouter plus d’informations sur l’utilisateur.
6. Sélectionnez **Suivant**, passez en revue les paramètres du nouvel utilisateur, effectuez les changements que vous souhaitez, puis sélectionnez **Finaliser l’ajout**, puis **Fermer**.

## <a name="add-multiple-users-at-the-same-time"></a>Ajouter plusieurs utilisateurs simultanément

Toutes les méthodes suivantes permettent d’ajouter de multiples utilisateurs simultanément :

- **Utiliser une feuille de calcul pour ajouter des utilisateurs en bloc.** Consultez la rubrique [Ajouter plusieurs utilisateurs simultanément](../../enterprise/add-several-users-at-the-same-time.md).
- **Automatiser l'ajouter de comptes et l'affectation de licences.** Voir [Créer des comptes d’utilisateur avec Microsoft 365 PowerShell](../../enterprise/create-user-accounts-with-microsoft-365-powershell.md). Choisissez cette méthode si vous êtes déjà familiarisé avec l'utilisation des applets de commande Windows PowerShell.
- **Vous utilisez ActiveDirectory ?**[Configurer la synchronisation de d’annuaire pour Microsoft 365](../../enterprise/set-up-directory-synchronization.md). Utilisez l'outil Azure Active Directory Connect . Utilisez l'outil Azure AD Connect pour répliquer les comptes d'utilisateur Active Directory (et autres objets Active Directory) dans Microsoft 365. La synchronisation ajoute uniquement les comptes d'utilisateurs. Vous devez attribuer des licences aux utilisateurs synchronisés pour qu'ils puissent utiliser le courrier et les autres applications Office.
- **Si vous effectuez une migration depuis Exchange** Consultez la rubrique [Méthodes de migration de comptes de messagerie multiples vers Office 365](/Exchange/mailbox-migration/mailbox-migration). Lorsque vous migrez plusieurs boîtes aux lettres vers Microsoft 365 en utilisant une méthode de migration à basculement, intermédiaire ou Exchange hybride, vous ajoutez automatiquement des utilisateurs dans le cadre de la migration. La migration ajoute uniquement les comptes d'utilisateurs. Vous devrez attribuer des licences aux utilisateurs pour qu'ils puissent utiliser le courrier et les autres applications Office. Si vous n’attribuez pas de licence à un utilisateur, sa boîte aux lettres est désactivée à la fin de la période de grâce de 30 jours. Découvrez comment [attribuer des licences à des utilisateurs](../manage/assign-licenses-to-users.md) dans le centre d'administration Microsoft 365.

## <a name="next-steps"></a>Étapes suivantes

Après avoir ajouté un utilisateur, vous recevez une notification par courrier de Microsoft. Ce courrier électronique contient l’identifiant de l’utilisateur et son mot de passe à lui faire parvenir pour qu’il puisse se connecter à Microsoft 365. Nous vous conseillons d'utiliser le processus habituel pour communiquer les nouveaux mots de passe. Partagez le [guide de démarrage rapide pour les employés](../../business-video/employee-quick-setup.md) avec vos nouveaux utilisateurs pour mettre certaines choses en place, en leur faisant par exemple découvrir [comment télécharger et installer des applications Office sur un PC ou Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) ou [comment configurer les applications Office et la messagerie électronique sur un appareil mobile](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>Contenu connexe

[Ajouter un nouvel employé dans Microsoft 365](add-new-employee.md) (article)\
[Ajouter plusieurs utilisateurs simultanément dans Microsoft 365](../../enterprise/add-several-users-at-the-same-time.md) (article)\
[Rétablir un utilisateur dans Microsoft 365](restore-user.md) (article)\
[Attribuer des licences aux utilisateurs](../manage/assign-licenses-to-users.md) (article)\
[Supprimer un utilisateur de votre organisation](delete-a-user.md) (article)
