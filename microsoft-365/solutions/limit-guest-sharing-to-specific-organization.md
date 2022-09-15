---
title: Limiter le partage d’invités à des organisations spécifiques
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection:
- highpri
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Découvrez comment limiter le partage d’invités à des organisations Azure AD ou Microsoft 365 spécifiques.
ms.openlocfilehash: baad796304090844d379d9c924f10b94245c7796
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67727257"
---
# <a name="limit-guest-sharing-to-specific-organizations"></a>Limiter le partage d’invités à des organisations spécifiques

Par défaut, les utilisateurs peuvent inviter des personnes extérieures à l’organisation en tant qu’invités. Cela inclut l’invitation à des équipes dans l’équipe Microsoft, les sites SharePoint et le partage de fichiers et de dossiers individuels avec eux.

Si vous souhaitez que vos utilisateurs invitent uniquement des invités d’organisations spécifiques, vous pouvez spécifier ces organisations dans les paramètres d’accès multilocataire Azure Active Directory pour [B2B Collaboration](/azure/active-directory/external-identities/what-is-b2b).

## <a name="configure-cross-tenant-access-settings"></a>Configurer les paramètres d’accès entre locataires

La première étape de la limitation du partage d’invités consiste à modifier les paramètres par défaut dans les paramètres d’accès interlocataire Azure AD pour bloquer les invités invités invités par défaut. Vous pouvez ensuite autoriser les invitations d’invités pour des organisations spécifiques.

> [!NOTE]
> La prise en compte des modifications apportées aux paramètres d’accès entre locataires peut prendre deux heures.

### <a name="set-the-default-b2b-collaboration-settings-to-block-inviting-guests"></a>Définir les paramètres de collaboration B2B par défaut pour bloquer les invités invités

Étant donné que l’invitation d’invités est activée par défaut, la limitation des invitations d’invités à certaines organisations nécessite le blocage de la collaboration B2B entrante par défaut.

Pour bloquer la collaboration B2B entrante par défaut
1. Connectez-vous à [Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte Administrateur général ou Administrateur de la sécurité.
1. Sélectionnez **Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (prévisualisation).**
1. Sélectionnez l’onglet **Paramètres par défaut** .
1. Sous **Paramètres d’accès entrant**, **sélectionnez Modifier les valeurs par défaut entrantes**.
1. Sélectionnez l’onglet **Collaboration B2B** et l’onglet **Utilisateurs et groupes** .
1. Sous **État Access**, choisissez **Bloquer l’accès**.
1. Sélectionnez l’onglet **Accès externe** .
1. Sous **État Access**, choisissez **Bloquer l’accès**.
1. Sélectionnez **Enregistrer**.
1. Fermez le panneau **Paramètres par défaut** .

### <a name="add-the-organization-where-you-want-to-allow-guest-invitations"></a>Ajouter l’organisation dans laquelle vous souhaitez autoriser les invitations d’invités

Ensuite, ajoutez les organisations dans lesquelles vous souhaitez autoriser vos utilisateurs à inviter des invités dans la liste d’accès interlocataire Azure AD.

Pour ajouter une organisation
1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (préversion)**.
1. Sélectionnez **Paramètres de l’organisation**.
1. Sélectionnez **Ajouter une organisation**.
1. Dans le volet **Ajouter une organisation**, tapez le nom de domaine complet (ou l’ID de locataire) de l’organisation.
1. Sélectionnez l’organisation dans les résultats de la recherche, puis sélectionnez **Ajouter**.
1. L’organisation apparaît dans la liste **Paramètres de l’organisation**.

À ce stade, tous les paramètres d’accès de cette organisation sont hérités de vos paramètres par défaut.

### <a name="configure-inbound-settings-for-the-organization-to-allow-all-users"></a>Configurer les paramètres entrants pour l’organisation afin d’autoriser tous les utilisateurs

Une fois que vous avez ajouté l’organisation, vous devez mettre à jour les paramètres entrants de l’organisation pour permettre aux utilisateurs B2B Collaboration d’être invités en tant qu’invités. Effectuez cette opération pour chaque organisation dans laquelle vous souhaitez permettre à vos utilisateurs d’inviter des invités.

1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (préversion)**.
1. Sélectionnez le lien d’accès entrant pour l’organisation que vous souhaitez modifier.
1. Sous l’onglet **Collaboration B2B** , choisissez **Personnaliser les paramètres**.
1. Sous **État d’Accès**, choisissez **Autoriser l’accès**.
1. Sous **Cible**, choisissez d’autoriser tous les utilisateurs.
1. Sélectionnez **Enregistrer** et fermez le panneau **Paramètres d’accès sortant** .

## <a name="turn-off-one-time-passcode-authentication"></a>Désactiver l’authentification par code secret unique

Même après avoir limité la collaboration B2B à certaines organisations, les utilisateurs peuvent toujours partager des fichiers et des dossiers avec des personnes d’autres organisations . Ils ne reçoivent tout simplement pas de compte invité dans votre annuaire.

Si vous souhaitez empêcher le partage entièrement avec d’autres organisations, vous devez désactiver la fonctionnalité de code secret unique dans Azure AD. Cela empêchera les personnes extérieures à votre organisation d’envoyer un code secret unique pour l’authentification à des fichiers ou dossiers partagés.

Pour désactiver la fonctionnalité de code secret à usage unique par e-mail
1. Connectez-vous au [Portail Microsoft Azure](https://portal.azure.com/) en tant qu’administrateur général Azure AD.
1. Dans le volet de navigation, sélectionnez **Azure Active Directory**.
1. Sélectionnez **Identités externes** > **Tous les fournisseurs d’identité**.
1. Sélectionnez **Email code secret unique**, puis sous **Email code secret unique pour les invités**, sélectionnez Désactiver le code secret à **usage unique par e-mail pour les invités** (ou **Non** si la fonctionnalité a été précédemment activée, désactivée ou activée pendant la préversion).
1. Sélectionnez **Enregistrer**.

## <a name="related-topics"></a>Voir aussi

[Vue d’ensemble de la connexion directe B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Configurer les paramètres d’accès entre locataires pour la connexion directe B2B](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[Limiter les personnes pouvant être invitées par une organisation](limit-invitations-from-specific-organization.md)

[Limiter les organisations où les utilisateurs peuvent avoir des comptes invités](limit-organizations-where-users-have-guest-accounts.md)