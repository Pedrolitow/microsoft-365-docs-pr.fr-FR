---
title: Stratégies d’accès aux identités et appareils pour autoriser l’accès B2B des utilisateurs invités et externes - Microsoft 365 pour entreprise | Documents Microsoft
description: Décrit l’accès conditionnel recommandé et les stratégies associées pour la protection de l’accès des invités et des utilisateurs externes.
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.author: josephd
author: JoeDavies-MSFT
manager: Laurawi
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.openlocfilehash: 4ee6cb93e5c943d704950e28ba4dc70a246429a6
ms.sourcegitcommit: 89097fb648987567b9493b9d94c85c5990562874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "49845075"
---
# <a name="policies-for-allowing-guest-access-and-b2b-external-user-access"></a>Stratégies d’accès invité et d’accès des utilisateurs externes B2B

Cet article traite de l’ajustement des stratégies d’accès aux appareils et aux identités recommandées pour autoriser l’accès aux invités et aux utilisateurs externes qui ont un compte Azure Active Directory (Azure AD) Business-to-Business (B2B). Ces instructions s’appuient sur les stratégies [communes d’accès aux appareils et aux identités.](identity-access-policies.md)

Ces recommandations sont conçues pour s’appliquer au **niveau de** protection de référence. Mais vous pouvez également ajuster les recommandations  en fonction de vos besoins spécifiques en matière de protection sensible et **hautement réglementée.**

Le fait de fournir un chemin d’accès aux comptes B2B pour s’authentifier auprès de votre client Azure AD ne permet pas à ces comptes d’accéder à l’ensemble de votre environnement. Les utilisateurs B2B et leurs comptes ont accès à des services et des ressources, tels que des fichiers, partagés avec eux par la stratégie d’accès conditionnel.

## <a name="updating-the-common-policies-to-allow-and-protect-guests-and-external-user-access"></a>Mise à jour des stratégies courantes pour autoriser et protéger les invités et l’accès des utilisateurs externes

Ce diagramme montre les stratégies à ajouter ou à mettre à jour parmi les stratégies d’accès aux identités et appareils courantes, pour l’accès des invités B2B et des utilisateurs externes.

[![Résumé des mises à jour de stratégie pour la protection de l’accès invité](../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png)

[Voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png)

Le tableau suivant répertorie les stratégies que vous devez créer et mettre à jour. Les stratégies courantes sont liées aux instructions de configuration associées dans l’article [Stratégies](identity-access-policies.md) communes d’identité et d’accès aux appareils.

|Niveau de protection|Stratégies|Informations supplémentaires|
|---|---|---|
|**Baseline**|[Exiger l’mf toujours pour les invités et les utilisateurs externes](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Créez cette stratégie et configurez : <ul><li>Pour **les affectations > utilisateurs** et groupes > inclure, sélectionnez Sélectionner des utilisateurs et des **groupes,** puis sélectionnez Tous les utilisateurs **invités et externes.**</li><li>Pour **les affectations > conditions >** se connectez, laissez toutes les options désactivées pour toujours appliquer l’authentification multifacteur (MFA).</li></ul>|
||[Exiger l’mf lorsque le risque de se connecte *est moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Modifiez cette stratégie pour exclure les invités et les utilisateurs externes.|
||[Exiger des PC conformes](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Modifiez cette stratégie pour exclure les invités et les utilisateurs externes.|

Pour inclure ou exclure des invités et des utilisateurs externes dans les stratégies d’accès conditionnel, pour affectations > Utilisateurs et groupes > Inclure ou exclure, vérifier tous les **utilisateurs invités** et **externes.**

![capture d’écran des contrôles pour l’exclusion des invités et des utilisateurs externes](../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png)

## <a name="more-information"></a>Informations supplémentaires

### <a name="guests-and-external-user-access-with-microsoft-teams"></a>Invités et accès des utilisateurs externes avec Microsoft Teams

Microsoft Teams définit les utilisateurs suivants :

- **L’accès invité** utilise un compte Azure AD B2B qui peut être ajouté en tant que membre d’une équipe et qui a accès aux communications et aux ressources de l’équipe.

- **L’accès** externe est pour un utilisateur externe qui n’a pas de compte B2B. L’accès des utilisateurs externes inclut les invitations, les appels, les conversations et les réunions, mais n’inclut pas l’appartenance à une équipe et l’accès aux ressources de l’équipe.

Pour plus d’informations, voir la [comparaison entre les invités et l’accès des utilisateurs externes pour teams.](https://docs.microsoft.com/microsoftteams/communicate-with-users-from-other-organizations#compare-external-and-guest-access)

Pour plus d’informations sur la sécurisation des stratégies d’accès aux identités et aux appareils pour Teams, voir recommandations de stratégie pour la [sécurisation des conversations, des groupes et des fichiers Teams.](teams-access-policies.md)

### <a name="require-mfa-always-for-guest-and-external-users"></a>Exiger toujours l’ment MFA pour les utilisateurs invités et externes

Cette stratégie invite les invités à s’inscrire à l’mf auprès de votre client, qu’ils soient inscrits ou non à l’mf dans leur client d’accueil. Lorsque vous accédez à des ressources dans votre client, les invités et les utilisateurs externes doivent utiliser l’ation MFA pour chaque demande.

### <a name="excluding-guests-and-external-users-from-risk-based-mfa"></a>Exclusion des invités et des utilisateurs externes de l’fa MFA basée sur les risques

Bien que les organisations peuvent appliquer des stratégies basées sur les risques pour les utilisateurs B2B à l’aide d’Azure AD Identity Protection, il existe des limitations dans l’implémentation d’Azure AD Identity Protection pour les utilisateurs de collaboration B2B dans un répertoire de ressources en raison de leur identité existante dans leur annuaire d’accueil. En raison de ces limitations, Microsoft vous recommande d’exclure les invités des stratégies DFA basées sur les risques et d’exiger que ces utilisateurs utilisent toujours l’mffa.

Pour plus d’informations, voir [Limitations of Identity Protection for B2B collaboration users](https://docs.microsoft.com/azure/active-directory/identity-protection/concept-identity-protection-b2b#limitations-of-identity-protection-for-b2b-collaboration-users).

### <a name="excluding-guests-and-external-users-from-device-management"></a>Exclusion des invités et des utilisateurs externes de la gestion des appareils

Une seule organisation peut gérer un appareil. Si vous n’excluez pas les invités et les utilisateurs externes des stratégies qui nécessitent la conformité des appareils, ces stratégies bloqueront ces utilisateurs.

## <a name="next-step"></a>Étape suivante

![Étape 4 : Stratégies pour les applications cloud Microsoft 365](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

Configurer des stratégies d’accès conditionnel pour :

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
