---
title: Limiter le partage d’invités à des organisations spécifiques
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Découvrez comment limiter le partage d’invités à des organisations Azure AD ou Microsoft 365 spécifiques.
ms.openlocfilehash: 75cfe739e1cdde2e0bd959382b2444487ea726be
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716068"
---
# <a name="limit-guest-sharing-to-specific-organizations"></a>Limiter le partage d’invités à des organisations spécifiques

Par défaut, les utilisateurs peuvent inviter des personnes extérieures à l’organisation en tant qu’invités. Cela inclut l’invitation à des équipes dans Microsoft Team, la SharePoint sites et le partage de fichiers et de dossiers individuels avec eux.

Si vous souhaitez que vos utilisateurs invitent uniquement des invités d’organisations spécifiques, vous pouvez spécifier ces organisations dans les paramètres d’accès entre clients Azure Active Directory pour la [collaboration B2B](/azure/active-directory/external-identities/what-is-b2b).

## <a name="configure-cross-tenant-access-settings"></a>Configurer les paramètres d’accès entre les locataires

La première étape de la limitation du partage d’invités consiste à modifier les paramètres par défaut dans les paramètres d’accès entre clients Azure AD pour bloquer l’invitation d’invités par défaut. Vous pouvez ensuite autoriser les invitations invité pour des organisations spécifiques.

> [!NOTE]
> L’application des modifications apportées aux paramètres d’accès entre locataires peut prendre deux heures.

### <a name="set-the-default-b2b-collaboration-settings-to-block-inviting-guests"></a>Définir les paramètres de collaboration B2B par défaut pour bloquer l’invitation d’invités

Étant donné que l’invitation à des invités est activée par défaut, la limitation des invitations invité à certaines organisations nécessite le blocage de la collaboration B2B entrante par défaut.

Pour bloquer la collaboration B2B entrante par défaut
1. Connectez-vous [à Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte d’administrateur général ou d’administrateur de sécurité.
1. **Sélectionnez Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (prévisualisation).**
1. Sélectionnez **l’onglet Paramètres par** défaut.
1. Sous **Paramètres d’accès entrant**, **sélectionnez Modifier les valeurs par défaut du trafic entrant**.
1. Sélectionnez **les onglets Collaboration B2B** et **Utilisateurs et** groupes.
1. Sous **État d’accès**, **sélectionnez Bloquer l’accès**.
1. Sélectionnez **l’onglet Accès** externe.
1. Sous **État d’accès**, **sélectionnez Bloquer l’accès**.
1. Sélectionnez **Enregistrer**.
1. Fermez le **lame Paramètres par** défaut.

### <a name="add-the-organization-where-you-want-to-allow-guest-invitations"></a>Ajouter l’organisation dans laquelle vous souhaitez autoriser les invitations invité

Ensuite, ajoutez les organisations où vous souhaitez autoriser vos utilisateurs à inviter des invités à la Azure AD’accès entre clients.

Pour ajouter une organisation
1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez Paramètres d’accès entre **locataires (prévisualisation).**
1. Sélectionnez **Paramètres organisationnels**.
1. Sélectionnez **Ajouter une organisation**.
1. Dans le **volet Ajouter une organisation** , tapez le nom de domaine complet (ou ID de client) de l’organisation.
1. Sélectionnez l’organisation dans les résultats de la recherche, puis sélectionnez **Ajouter**.
1. L’organisation apparaît dans la liste **Paramètres organisationnels** .

À ce stade, tous les paramètres d’accès de cette organisation sont hérités de vos paramètres par défaut.

### <a name="configure-inbound-settings-for-the-organization-to-allow-all-users"></a>Configurer les paramètres entrants de l’organisation pour autoriser tous les utilisateurs

Une fois que vous avez ajouté l’organisation, vous devez mettre à jour les paramètres entrants de l’organisation pour permettre aux utilisateurs de collaboration B2B d’être invités en tant qu’invités. Faites-le pour chaque organisation où vous souhaitez autoriser vos utilisateurs à inviter des invités.

1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez Paramètres d’accès entre **locataires (prévisualisation).**
1. Sélectionnez le lien d’accès entrant pour l’organisation que vous souhaitez modifier.
1. Sous **l’onglet Collaboration B2B** , choisissez **Personnaliser les paramètres**.
1. Sous **État d’accès**, **sélectionnez Autoriser l’accès**.
1. Sous **Cible**, choisissez d’autoriser tous les utilisateurs.
1. **Sélectionnez Enregistrer** et fermez le **blade des paramètres d’accès sortant**.

## <a name="turn-off-one-time-passcode-authentication"></a>Désactiver l’authentification par code secret unique

Même après avoir limité la collaboration B2B à certaines organisations, les utilisateurs peuvent toujours partager des fichiers et des dossiers avec des personnes d’autres organisations . Ils ne se viennent pas d’un compte invité dans votre annuaire.

Si vous souhaitez empêcher le partage entièrement avec d’autres organisations, vous devez désactiver la fonctionnalité de code secret unique dans Azure AD. Cela empêche les personnes extérieures à votre organisation d’être envoyées à un code secret unique pour l’authentification aux fichiers ou dossiers partagés.

Pour désactiver la fonctionnalité de code secret à une seule heure du courrier électronique
1. Connectez-vous au [Portail Microsoft Azure](https://portal.azure.com/) en tant qu’administrateur général Azure AD.
1. Dans le volet de navigation, sélectionnez **Azure Active Directory**.
1. Sélectionnez **Les fournisseurs d’identité External IdentitiesAll** > .
1. Sélectionnez Code secret **e-mail** à une seule fois, puis sous Code secret à une seule fois pour les **invités**, sélectionnez Désactiver le code secret à une seule fois pour  les **invités** (ou Non si la fonctionnalité a été précédemment activée, désactivée ou activée pendant la prévisualisation).
1. Sélectionnez **Enregistrer**.

## <a name="related-topics"></a>Sujets associés

[Vue d’ensemble de la connexion directe B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Configurer les paramètres d’accès entre locataires pour la connexion directe B2B](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[Limiter les personnes qui peuvent être invitées par une organisation](limit-invitations-from-specific-organization.md)

[Limiter les organisations où les utilisateurs peuvent avoir des comptes invités](limit-organizations-where-users-have-guest-accounts.md)