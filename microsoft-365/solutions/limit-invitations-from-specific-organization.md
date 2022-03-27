---
title: Limiter les personnes qui peuvent être invitées par une organisation
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
description: Découvrez comment limiter les utilisateurs qui peuvent être invités en tant que participant à un canal partagé ou invité à une organisation spécifique.
ms.openlocfilehash: 599f83a4464498f7a964f02a955f802cb8545432
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716065"
---
# <a name="limit-who-can-be-invited-by-an-organization"></a>Limiter les personnes qui peuvent être invitées par une organisation

Si vous collaborez avec une autre organisation et que vous souhaitez limiter les personnes qui peuvent y être invitées en tant qu’invité ou membre de canal partagé dans Teams, vous pouvez spécifier qui peut être invité dans les paramètres d’accès entre clients dans Azure Active Directory.

> [!NOTE]
> L’application des modifications apportées aux paramètres d’accès entre locataires peut prendre deux heures.

## <a name="create-a-security-group"></a>Créer un groupe de sécurité

Le moyen le plus simple de spécifier qui peut être invité à une autre organisation consiste à utiliser un groupe de sécurité. Vous pouvez utiliser un groupe de sécurité avec une appartenance définie ou un groupe de sécurité dynamique. Vous pouvez utiliser un groupe de sécurité existant ou en créer un à cet effet.

Pour créer un groupe de sécurité
1. Connectez-vous [à Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte d’administrateur général ou d’administrateur de sécurité.
1. Dans la page **Active Directory** , sélectionnez **Groupes** , puis **Nouveau groupe**.
1. Choisissez **Sécurité** pour le **type de groupe**.
1. Tapez un **nom de groupe.** 
1. Vous pouvez éventuellement ajouter une description pour le groupe.
1. Pour **Azure AD rôles peuvent être affectés au groupe**, choisissez **Non**.
1. Sélectionnez un type d’appartenance **prédéfiny (obligatoire).**
1. Ajoutez des propriétaires et des membres de groupe ou [une](/azure/active-directory/enterprise-users/groups-dynamic-membership) requête dynamique si vous utilisez l’appartenance utilisateur dynamique.
1. Sélectionnez **Créer**. Votre groupe est créé et prêt pour que vous ajoutiez des membres.

## <a name="add-an-organization"></a>Ajouter une organisation

Pour définir des règles de collaboration avec une autre organisation, vous devez l’ajouter aux paramètres Azure AD’accès entre les locataires. Si vous n’avez pas encore ajouté l’organisation, suivez cette procédure pour l’ajouter.

Pour ajouter une organisation
1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez Paramètres d’accès entre locataires **(prévisualisation)**.1. Sélectionnez **Paramètres organisationnels**.
1. Sélectionnez **Ajouter une organisation**.
1. Dans le **volet Ajouter une organisation** , tapez le nom de domaine complet (ou ID de client) de l’organisation.
1. Sélectionnez l’organisation dans les résultats de la recherche, puis sélectionnez **Ajouter**.
1. L’organisation apparaît dans la liste **Paramètres organisationnels** . À ce stade, tous les paramètres d’accès de cette organisation sont hérités de vos paramètres par défaut.

## <a name="choose-who-can-be-invited-by-an-organization"></a>Choisir les personnes qui peuvent être invitées par une organisation

Il existe deux options pour limiter les personnes qui peuvent être invitées à une organisation :

- Limiter les personnes qui peuvent être invitées en tant qu’invité. Cela empêche l’ajout d’utilisateurs au compte de l’autre Azure AD en tant qu’invité. Cela empêche le partage de fichiers, dossiers, sites, équipes et groupes Microsoft 365 avec des personnes qui ne font pas partie du groupe de sécurité.
- Limiter les personnes qui peuvent être ajoutées à un canal partagé externe. Cela empêche les personnes qui ne font pas du groupe de sécurité d’être ajoutées aux canaux partagés de l’autre organisation.

Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez Paramètres d’accès entre **locataires (prévisualisation).**

Pour limiter les personnes qui peuvent être invitées en tant qu’invité
1. Sélectionnez le lien d’accès sortant pour l’organisation que vous souhaitez modifier.
1. Sous **l’onglet Collaboration B2B** , choisissez **Personnaliser les paramètres**.
1. Sous **État d’accès**, **sélectionnez Autoriser l’accès**.
1. Sous **Cible**, **sélectionnez Sélectionner des utilisateurs externes et des groupes**.
1. Sélectionnez le lien pour ajouter des utilisateurs et des groupes.
1. Recherchez et sélectionnez le groupe de sécurité que vous souhaitez utiliser.
1. Choisissez **Sélectionner**.
1. **Sélectionnez Enregistrer** et fermez le **blade des paramètres d’accès sortant**.


Pour limiter les personnes qui peuvent être invitées en tant que participant au canal partagé
1. Sélectionnez le lien d’accès sortant pour l’organisation que vous souhaitez modifier.
1. Sous **l’onglet Connexion directe B2B** , choisissez **Personnaliser les paramètres**.
1. Sous **État d’accès**, **sélectionnez Autoriser l’accès**.
1. Sous **Cible**, **sélectionnez Sélectionner des utilisateurs externes et des groupes**.
1. Sélectionnez le lien pour ajouter des utilisateurs et des groupes.
1. Recherchez et sélectionnez le groupe de sécurité que vous souhaitez utiliser.
1. Choisissez **Sélectionner**.
1. **Sélectionnez Enregistrer** et fermez le **blade des paramètres d’accès sortant**.

## <a name="related-topics"></a>Sujets associés

[Vue d’ensemble de la connexion directe B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Configurer les paramètres d’accès entre locataires pour la connexion directe B2B](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[Limiter les organisations où les utilisateurs peuvent avoir des comptes invités](limit-organizations-where-users-have-guest-accounts.md)

[Limiter le partage d’invités à des organisations spécifiques](limit-guest-sharing-to-specific-organization.md)