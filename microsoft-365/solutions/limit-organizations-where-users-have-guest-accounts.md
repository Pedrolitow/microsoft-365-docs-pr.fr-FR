---
title: Limiter les organisations où les utilisateurs peuvent avoir des comptes invités
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
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
description: Découvrez comment spécifier les organisations dans lesquelles vos utilisateurs peuvent avoir des comptes invités.
ms.openlocfilehash: 5e5a989aa2175f8af00630bdb1abcf0735656a40
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67986705"
---
# <a name="limit-organizations-where-users-can-have-guest-accounts"></a>Limiter les organisations où les utilisateurs peuvent avoir des comptes invités

Par défaut, d’autres organisations Microsoft 365 et Azure Active Directory peuvent inviter vos utilisateurs à participer à leur organisation en tant qu’invités. Cela inclut l’invitation à des équipes dans l’équipe Microsoft, les sites SharePoint et le partage de fichiers et de dossiers individuels avec eux.

Si vous souhaitez uniquement que vos utilisateurs participent en tant qu’invités avec des organisations spécifiques, vous pouvez spécifier ces organisations dans les paramètres d’accès multilocataire Azure Active Directory pour [B2B Collaboration](/azure/active-directory/external-identities/what-is-b2b).

> [!NOTE]
> La prise en compte des modifications apportées aux paramètres d’accès entre locataires peut prendre deux heures.

## <a name="set-the-default-b2b-collaboration-settings-to-block-users-from-being-guests"></a>Définir les paramètres de collaboration B2B par défaut pour empêcher les utilisateurs d’être invités

Étant donné que la participation en tant qu’invités est activée par défaut, la limitation de la participation des invités à certaines organisations nécessite le blocage de la collaboration B2B sortante par défaut.

Pour bloquer la collaboration B2B sortante par défaut
1. Connectez-vous à [Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte Administrateur général ou Administrateur de la sécurité.
1. Sélectionnez **Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (prévisualisation).**
1. Sélectionnez l’onglet **Paramètres par défaut** .
1. Sous **Paramètres d’accès sortant**, **sélectionnez Modifier les valeurs par défaut du trafic sortant**.
1. Sélectionnez l’onglet **Collaboration B2B** et l’onglet **Utilisateurs et groupes** .
1. Sous **État Access**, choisissez **Bloquer l’accès**.
1. Sélectionnez l’onglet **Accès externe** .
1. Sous **État Access**, choisissez **Bloquer l’accès**.
1. Sélectionnez **Enregistrer**.
1. Fermez le panneau **Paramètres par défaut** .

## <a name="add-an-organization"></a>Ajouter une organisation

Ensuite, ajoutez les organisations dans lesquelles vous souhaitez autoriser vos utilisateurs à collaborer en tant qu’invités dans la liste d’accès interlocataire Azure AD.

Pour ajouter une organisation
1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (préversion)**.
1. Sélectionnez **Paramètres de l’organisation**.
1. Sélectionnez **Ajouter une organisation**.
1. Dans le volet **Ajouter une organisation**, tapez le nom de domaine complet (ou l’ID de locataire) de l’organisation.
1. Sélectionnez l’organisation dans les résultats de la recherche, puis sélectionnez **Ajouter**.
1. L’organisation apparaît dans la liste **Paramètres de l’organisation**.

À ce stade, tous les paramètres d’accès de cette organisation sont hérités de vos paramètres par défaut.

## <a name="configure-the-organizations-outbound-setting-to-allow-all-users"></a>Configurer le paramètre sortant de l’organisation pour autoriser tous les utilisateurs

Une fois que vous avez ajouté l’organisation, vous devez mettre à jour les paramètres sortants de l’organisation pour permettre l’ajout d’utilisateurs B2B Collaboration en tant qu’invités. Effectuez cette opération pour chaque organisation dans laquelle vous souhaitez autoriser l’ajout de vos utilisateurs en tant qu’invités.

Pour autoriser les utilisateurs à collaborer avec des invités B2B dans une organisation
1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (préversion)**.
1. Sélectionnez le lien d’accès sortant pour l’organisation que vous souhaitez modifier.
1. Sous l’onglet **Collaboration B2B** , choisissez **Personnaliser les paramètres**.
1. Sous **État d’Accès**, choisissez **Autoriser l’accès**.
1. Sous **Cible**, choisissez d’autoriser tous les utilisateurs.
1. Sélectionnez **Enregistrer** et fermez le panneau **Paramètres d’accès sortant** .

## <a name="related-topics"></a>Voir aussi

[Vue d’ensemble de la connexion directe B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Configurer les paramètres d’accès entre locataires pour la connexion directe B2B](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[Limiter les personnes pouvant être invitées par une organisation](limit-invitations-from-specific-organization.md)

[Limiter le partage d’invités à des organisations spécifiques](limit-guest-sharing-to-specific-organization.md)