---
title: Limiter les personnes pouvant être invitées par une organisation
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
description: Découvrez comment limiter les utilisateurs qui peuvent être invités en tant que participant de canal invité ou partagé à une organisation spécifique.
ms.openlocfilehash: eac3d5d5a91a815bc8add458aceb43c849282bf6
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67728063"
---
# <a name="limit-who-can-be-invited-by-an-organization"></a>Limiter les personnes pouvant être invitées par une organisation

Si vous collaborez avec une autre organisation et souhaitez limiter qui peut être invité à cette organisation en tant qu’invité ou membre de canal partagé dans Teams, vous pouvez spécifier qui peut être invité dans les paramètres d’accès entre locataires dans Azure Active Directory.

> [!NOTE]
> La prise en compte des modifications apportées aux paramètres d’accès entre locataires peut prendre six heures.

## <a name="create-a-security-group"></a>Créer un groupe de sécurité

Le moyen le plus simple de spécifier qui peut être invité à une autre organisation consiste à utiliser un groupe de sécurité. Vous pouvez utiliser un groupe de sécurité avec une appartenance définie ou un groupe de sécurité dynamique. Vous pouvez utiliser un groupe de sécurité existant ou en créer un à cet effet.

Pour créer un groupe de sécurité
1. Connectez-vous à [Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte Administrateur général ou Administrateur de la sécurité.
1. Dans la page **Active Directory** , sélectionnez **Groupes** , puis **Nouveau groupe**.
1. Choisissez **Sécurité** pour le **type de groupe**.
1. Tapez un **nom de groupe.** 
1. Si vous le souhaitez, ajoutez une description pour le groupe.
1. Pour que les **rôles Azure AD puissent être attribués au groupe**, choisissez **Non**.
1. Sélectionnez un **type d’appartenance** prédéfini (obligatoire).
1. Ajoutez des propriétaires de groupe et des membres ou une [requête dynamique](/azure/active-directory/enterprise-users/groups-dynamic-membership) si vous utilisez l’appartenance utilisateur dynamique.
1. Sélectionnez **Créer**. Votre groupe est créé et prêt pour vous permettre d’ajouter des membres.

## <a name="add-an-organization"></a>Ajouter une organisation

Pour définir des règles de collaboration avec une autre organisation, vous devez ajouter cette organisation aux paramètres d’accès multilocataire Azure AD. Si vous n’avez pas encore ajouté l’organisation, suivez cette procédure pour l’ajouter.

Pour ajouter une organisation
1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis les **paramètres d’accès entre locataires (préversion)** 1. Sélectionnez **Paramètres de l’organisation**.
1. Sélectionnez **Ajouter une organisation**.
1. Dans le volet **Ajouter une organisation**, tapez le nom de domaine complet (ou l’ID de locataire) de l’organisation.
1. Sélectionnez l’organisation dans les résultats de la recherche, puis sélectionnez **Ajouter**.
1. L’organisation apparaît dans la liste **Paramètres de l’organisation**. À ce stade, tous les paramètres d’accès de cette organisation sont hérités de vos paramètres par défaut.

## <a name="choose-who-can-be-invited-by-an-organization"></a>Choisir qui peut être invité par une organisation

Il existe deux options pour limiter les personnes pouvant être invitées à une organisation :

- Limitez les personnes pouvant être invitées en tant qu’invité. Cela empêche les utilisateurs d’être ajoutés à Azure AD de l’autre organisation en tant qu’invité. Il empêche le partage de fichiers, dossiers, sites, équipes et groupes Microsoft 365 avec des personnes qui ne font pas partie du groupe de sécurité.
- Limitez les personnes qui peuvent être ajoutées à un canal partagé externe. Cela empêche les personnes qui ne sont pas dans le groupe de sécurité d’être ajoutées aux canaux partagés de l’autre organisation.

Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (préversion)**.

Pour limiter qui peut être invité en tant qu’invité
1. Sélectionnez le lien d’accès sortant pour l’organisation que vous souhaitez modifier.
1. Sous l’onglet **Collaboration B2B** , choisissez **Personnaliser les paramètres**.
1. Sous **État d’Accès**, choisissez **Autoriser l’accès**.
1. Sous **Cible**, **choisissez Sélectionner des utilisateurs et des groupes externes**.
1. Sélectionnez le lien pour ajouter des utilisateurs et des groupes.
1. Recherchez et sélectionnez le groupe de sécurité que vous souhaitez utiliser.
1. Choisir **Sélectionner**.
1. Sélectionnez **Enregistrer** et fermez le panneau **Paramètres d’accès sortant** .


Pour limiter les personnes pouvant être invitées en tant que participant de canal partagé
1. Sélectionnez le lien d’accès sortant pour l’organisation que vous souhaitez modifier.
1. Sous l’onglet **Connexion directe B2B**, choisissez **Personnaliser les paramètres**.
1. Sous **État d’Accès**, choisissez **Autoriser l’accès**.
1. Sous **Cible**, **choisissez Sélectionner des utilisateurs et des groupes externes**.
1. Sélectionnez le lien pour ajouter des utilisateurs et des groupes.
1. Recherchez et sélectionnez le groupe de sécurité que vous souhaitez utiliser.
1. Choisir **Sélectionner**.
1. Sélectionnez **Enregistrer** et fermez le panneau **Paramètres d’accès sortant** .

## <a name="related-topics"></a>Voir aussi

[Vue d’ensemble de la connexion directe B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Configurer les paramètres d’accès entre locataires pour la connexion directe B2B](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[Limiter les organisations où les utilisateurs peuvent avoir des comptes invités](limit-organizations-where-users-have-guest-accounts.md)

[Limiter le partage d’invités à des organisations spécifiques](limit-guest-sharing-to-specific-organization.md)
