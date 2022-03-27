---
title: Limiter les organisations où les utilisateurs peuvent avoir des comptes invités
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
description: Découvrez comment spécifier les organisations dans lesquelles vos utilisateurs peuvent avoir des comptes invités.
ms.openlocfilehash: 00db14560c491461435e41e30c106c2554d9ad61
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63715998"
---
# <a name="limit-organizations-where-users-can-have-guest-accounts"></a>Limiter les organisations où les utilisateurs peuvent avoir des comptes invités

Par défaut, les autres Microsoft 365 et Azure Active Directory peuvent inviter vos utilisateurs à participer à leur organisation en tant qu’invités. Cela inclut l’invitation à des équipes dans Microsoft Team, la SharePoint sites et le partage de fichiers et de dossiers individuels avec eux.

Si vous souhaitez uniquement que vos utilisateurs participent en tant qu’invités avec des organisations spécifiques, vous pouvez spécifier ces organisations dans les paramètres d’accès entre clients Azure Active Directory pour la [collaboration B2B](/azure/active-directory/external-identities/what-is-b2b).

> [!NOTE]
> L’application des modifications apportées aux paramètres d’accès entre locataires peut prendre deux heures.

## <a name="set-the-default-b2b-collaboration-settings-to-block-users-from-being-guests"></a>Définir les paramètres de collaboration B2B par défaut pour empêcher les utilisateurs d’être invités

Étant donné que la participation en tant qu’invités est activée par défaut, la limitation de la participation des invités à certaines organisations nécessite le blocage de la collaboration B2B sortante par défaut.

Pour bloquer la collaboration B2B sortante par défaut
1. Connectez-vous [à Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte d’administrateur général ou d’administrateur de sécurité.
1. **Sélectionnez Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (prévisualisation).**
1. Sélectionnez **l’onglet Paramètres par** défaut.
1. Sous **Paramètres d’accès sortant**, **sélectionnez Modifier les paramètres par défaut du trafic sortant**.
1. Sélectionnez **les onglets Collaboration B2B** et **Utilisateurs et** groupes.
1. Sous **État d’accès**, **sélectionnez Bloquer l’accès**.
1. Sélectionnez **l’onglet Accès** externe.
1. Sous **État d’accès**, **sélectionnez Bloquer l’accès**.
1. Sélectionnez **Enregistrer**.
1. Fermez le **lame Paramètres par** défaut.

## <a name="add-an-organization"></a>Ajouter une organisation

Ensuite, ajoutez les organisations où vous souhaitez autoriser vos utilisateurs à collaborer en tant qu’invités à la Azure AD’accès entre clients.

Pour ajouter une organisation
1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez Paramètres d’accès entre **locataires (prévisualisation).**
1. Sélectionnez **Paramètres organisationnels**.
1. Sélectionnez **Ajouter une organisation**.
1. Dans le **volet Ajouter une organisation** , tapez le nom de domaine complet (ou ID de client) de l’organisation.
1. Sélectionnez l’organisation dans les résultats de la recherche, puis sélectionnez **Ajouter**.
1. L’organisation apparaît dans la liste **Paramètres organisationnels** .

À ce stade, tous les paramètres d’accès de cette organisation sont hérités de vos paramètres par défaut.

## <a name="configure-the-organizations-outbound-setting-to-allow-all-users"></a>Configurer le paramètre sortant de l’organisation pour autoriser tous les utilisateurs

Une fois que vous avez ajouté l’organisation, vous devez mettre à jour les paramètres sortants de l’organisation pour permettre aux utilisateurs de collaboration B2B d’être ajoutés en tant qu’invités. Faites-le pour chaque organisation où vous souhaitez autoriser vos utilisateurs à être ajoutés en tant qu’invités.

Pour permettre aux utilisateurs d’invités de collaboration B2B dans une organisation
1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez Paramètres d’accès entre **locataires (prévisualisation).**
1. Sélectionnez le lien d’accès sortant pour l’organisation que vous souhaitez modifier.
1. Sous **l’onglet Collaboration B2B** , choisissez **Personnaliser les paramètres**.
1. Sous **État d’accès**, **sélectionnez Autoriser l’accès**.
1. Sous **Cible**, choisissez d’autoriser tous les utilisateurs.
1. **Sélectionnez Enregistrer** et fermez le **blade des paramètres d’accès sortant**.

## <a name="related-topics"></a>Sujets associés

[Vue d’ensemble de la connexion directe B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Configurer les paramètres d’accès entre locataires pour la connexion directe B2B](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[Limiter les personnes qui peuvent être invitées par une organisation](limit-invitations-from-specific-organization.md)

[Limiter le partage d’invités à des organisations spécifiques](limit-guest-sharing-to-specific-organization.md)