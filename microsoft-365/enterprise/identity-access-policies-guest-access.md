---
title: Stratégies d’accès aux identités et aux appareils pour autoriser l’accès B2B aux invités et externes-Microsoft 365 pour les entreprises | Microsoft docs
description: Décrit l’accès conditionnel et les stratégies connexes recommandées pour la protection de l’accès des utilisateurs invités et externes.
author: BrendaCarter
manager: johmar
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: bcarter
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.openlocfilehash: 0ab4a2d48a1ac90f48bbfee82239fc0c4c1d55d5
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46686825"
---
# <a name="policies-for-allowing-guest-and-external-b2b-access"></a>Stratégies d’autorisation d’accès B2B invité et externe
Cet article explique comment ajuster les stratégies courantes d’identité et d’accès aux appareils pour autoriser l’accès au compte B2B (utilisateurs invités et externes). Ce guide s’appuie sur les [stratégies courantes d’identité et d’accès aux appareils](identity-access-policies.md).

Ces recommandations sont conçues pour s’appliquer au niveau de **base** de protection. Toutefois, vous pouvez ajuster les recommandations en fonction de la granularité de vos besoins pour une protection **sensible** et **hautement réglementée** . 

Fournir un chemin d’accès permettant aux utilisateurs B2B de s’authentifier auprès de votre client Azure AD ne donne pas à ces utilisateurs un accès à l’ensemble de votre environnement. Les utilisateurs B2B ont uniquement accès aux ressources qui sont partagées avec eux (par exemple, des fichiers) dans les services accordés dans les stratégies d’accès conditionnel.

## <a name="updating-the-common-policies-to-allow-and-protect-guest-and-external-access"></a>Mise à jour des stratégies communes pour autoriser et protéger les accès invités et externes 

Le diagramme suivant illustre les stratégies courantes d’identité et d’accès aux appareils et indique (avec une icône en crayon) les stratégies à ajouter ou à mettre à jour pour protéger les accès invités et externes. 

![Résumé des mises à jour de stratégie pour la protection de l’accès invité](../media/identity-access-ruleset-guest.png)

Le tableau suivant répertorie les stratégies que vous devez mettre à jour ou créer. Les stratégies courantes lient aux instructions de configuration associées dans l’article [Common Identity and Device Access Policies](identity-access-policies.md) .

|Niveau de protection|Stratégies|Plus d’informations|
|:---------------|:-------|:----------------|
|**Baseline**|[Exiger MFA pour les utilisateurs invités et externes](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Créez cette nouvelle règle et appliquez-la uniquement aux invités et aux utilisateurs externes. Sous risque de connexion, laissez toutes les options désactivées pour toujours appliquer l’authentification multifacteur.|
|        |[Exiger l’authentification multifacteur lorsque le risque de connexion est *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Modifiez cette règle pour exclure les utilisateurs invités et externes.|
|        |[Exiger des PC conformes](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Modifiez cette règle pour exclure les utilisateurs invités et externes.|

Pour inclure ou exclure des invités et des utilisateurs externes dans les règles d’accès conditionnel, cliquez sur l’onglet inclure ou exclure et vérifiez **tous les invités et les utilisateurs externes**.

![capture d’écran des contrôles pour exclure des invités](../media/identity-access-exclude-guests-ui.png)

## <a name="more-information"></a>Plus d’informations

### <a name="guests-vs-external-users"></a>Invités et utilisateurs externes
Dans Azure AD, les utilisateurs invités et les utilisateurs externes sont les mêmes. Le type d’utilisateur pour les deux est Guest. Les utilisateurs invités sont des utilisateurs B2B.

Microsoft teams différencie les utilisateurs invités et les utilisateurs externes au sein de l’application, mais ils sont tous deux des utilisateurs B2B lors de l’authentification. Pour plus d’informations sur les utilisateurs de teams Guest et External, consultez la rubrique [Enabling Guest and External Access for teams](teams-access-policies.md#enabling-guest-and-external-access-for-teams).

### <a name="require-mfa-always-for-guest-and-external-users"></a>Exiger MFA pour les utilisateurs invités et externes
Cette règle invite les invités à s’inscrire à l’authentification multifacteur dans votre client, qu’ils soient inscrits pour l’authentification multifacteur dans leur client d’accueil. Lors de l’accès à des ressources dans votre client, les invités et les utilisateurs externes doivent utiliser l’authentification multifacteur pour chaque demande. 

### <a name="excluding-guest-and-external-users-from-risk-based-mfa"></a>Exclusion des utilisateurs invités et externes de l’authentification multifacteur basée sur les risques
Bien que les organisations puissent appliquer des stratégies basées sur les risques pour les utilisateurs B2B à l’aide de la protection des identités, il existe des limitations dans l’implémentation de la protection des identités pour les utilisateurs de la collaboration B2B dans un répertoire de ressources en raison de leur identité dans leur répertoire de base. En raison de ces limitations, Microsoft vous recommande d’exclure les utilisateurs invités des stratégies MFA à risque et de leur demander d’utiliser toujours l’authentification multifacteur. 

Pour plus d’informations, consultez la rubrique [limitations de la protection des identités pour les utilisateurs de collaboration B2B](https://docs.microsoft.com/azure/active-directory/identity-protection/concept-identity-protection-b2b#limitations-of-identity-protection-for-b2b-collaboration-users). 

### <a name="excluding-guest-and-external-users-from-device-management"></a>Exclusion des utilisateurs invités et externes de la gestion des appareils 
Une seule organisation peut gérer un appareil. Si vous n’excluez pas les utilisateurs invités et externes des stratégies qui nécessitent une conformité de l’appareil, ces stratégies bloqueront ces utilisateurs. 

## <a name="next-steps"></a>Étapes suivantes

[En savoir plus sur l’activation de l’accès conditionnel aux équipes](teams-access-policies.md)

