---
title: Stratégies d’accès aux identités et appareils pour autoriser l’accès B2B des utilisateurs invités et externes - Microsoft 365 pour les | Documents Microsoft
description: Décrit l’accès conditionnel recommandé et les stratégies associées pour la protection de l’accès des invités et des utilisateurs externes.
ms.prod: m365-security
ms.topic: article
ms.author: dansimp
author: dansimp
audience: Admin
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
ms.technology: mdo
ms.openlocfilehash: 28b389292ed733318e5796a1be3ed9c11d2df462
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466606"
---
# <a name="policies-for-allowing-guest-access-and-b2b-external-user-access"></a>Stratégies d’accès invité et d’accès des utilisateurs externes B2B

Cet article traite de l’ajustement des stratégies d’accès aux appareils et aux identités De confiance zéro recommandées pour autoriser l’accès pour les invités et les utilisateurs externes qui ont un compte B2B Azure Active Directory (Azure AD). Ces instructions s’appuient sur les stratégies [communes d’accès aux identités et aux appareils](identity-access-policies.md).

Ces recommandations sont conçues pour s’appliquer au **niveau de départ** de la protection. Toutefois, vous pouvez également ajuster les recommandations en fonction de vos besoins spécifiques en matière de protection **de** la sécurité d’entreprise **et spécialisée** .

Le fait de fournir un chemin d’accès aux comptes B2B pour s’authentifier auprès de votre client Azure AD ne permet pas à ces comptes d’accéder à l’ensemble de votre environnement. Les utilisateurs B2B et leurs comptes ont accès à des services et des ressources, tels que des fichiers, partagés avec eux par la stratégie d’accès conditionnel.

## <a name="updating-the-common-policies-to-allow-and-protect-guests-and-external-user-access"></a>Mise à jour des stratégies courantes pour autoriser et protéger les invités et l’accès des utilisateurs externes

Ce diagramme montre les stratégies à ajouter ou à mettre à jour parmi les stratégies d’accès aux identités et appareils courantes, pour l’accès des invités B2B et des utilisateurs externes.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png" alt-text="Résumé des mises à jour de stratégie pour la protection de l’accès invité" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png":::

Le tableau suivant répertorie les stratégies que vous devez créer et mettre à jour. Les stratégies courantes sont liées aux instructions de configuration associées dans l’article Des stratégies communes d’accès aux appareils [et aux](identity-access-policies.md) identités.

|Niveau de protection|Stratégies|Informations supplémentaires|
|---|---|---|
|**Point de départ**|[Exiger l’mf toujours pour les invités et les utilisateurs externes](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Créez cette stratégie et configurez : <ul><li>Pour **les affectations > utilisateurs et groupes > inclure**, sélectionnez Sélectionner des utilisateurs et des **groupes, puis** sélectionnez Tous les utilisateurs **invités et externes**.</li><li>Pour **les affectations > conditions >** se connectez, laissez toutes les options désactivées pour toujours appliquer l’authentification multifacteur (MFA).</li></ul>|
||[Exiger une mfmf lorsque le risque de se connecte *est moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Modifiez cette stratégie pour exclure les invités et les utilisateurs externes.|

Pour inclure ou exclure des invités et des utilisateurs externes dans les stratégies d’accès **conditionnel, pour Affectations > Utilisateurs et groupes > Inclure** ou exclure **, vérifiez** Tous les utilisateurs invités **et externes**.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png" alt-text="Contrôles pour l’exclusion des invités et des utilisateurs externes" lightbox="../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png":::

## <a name="more-information"></a>Plus d’informations

### <a name="guests-and-external-user-access-with-microsoft-teams"></a>Invités et accès des utilisateurs externes avec Microsoft Teams

Microsoft Teams définit les utilisateurs suivants :

- **L’accès** invité utilise un Azure AD B2B qui peut être ajouté en tant que membre d’une équipe et qui a accès aux communications et aux ressources de l’équipe.

- **L’accès** externe est pour un utilisateur externe qui n’a pas de compte B2B. L’accès des utilisateurs externes inclut les invitations, les appels, les conversations et les réunions, mais n’inclut pas l’appartenance à une équipe et l’accès aux ressources de l’équipe.

Pour plus d’informations, voir la [comparaison entre les invités et l’accès des utilisateurs externes pour teams](/microsoftteams/communicate-with-users-from-other-organizations#compare-external-and-guest-access).

Pour plus d’informations sur la sécurisation des stratégies d’accès aux identités et aux appareils pour Teams, voir recommandations en matière de stratégie pour la [Teams conversations, les groupes et les fichiers](teams-access-policies.md).

### <a name="require-mfa-always-for-guest-and-external-users"></a>Exiger l’mf toujours pour les utilisateurs invités et externes

Cette stratégie invite les invités à s’inscrire à l’mf auprès de votre client, qu’ils soient inscrits ou non à l’mf dans leur client d’accueil. Lorsque vous accédez à des ressources dans votre client, les invités et les utilisateurs externes doivent utiliser l’ation MFA pour chaque demande.

### <a name="excluding-guests-and-external-users-from-risk-based-mfa"></a>Exclusion des invités et des utilisateurs externes de l’fa MFA basée sur les risques

Bien que les organisations peuvent appliquer des stratégies basées sur les risques pour les utilisateurs B2B à l’aide de Azure AD Identity Protection, il existe des limitations dans l’implémentation de Azure AD Identity Protection pour les utilisateurs de collaboration B2B dans un répertoire de ressources en raison de leur identité existante dans leur répertoire d’accueil. En raison de ces limitations, Microsoft vous recommande d’exclure les invités des stratégies DFA basées sur les risques et d’exiger que ces utilisateurs utilisent toujours l’mffa.

Pour plus d’informations, voir [Limitations of Identity Protection for B2B collaboration users](/azure/active-directory/identity-protection/concept-identity-protection-b2b#limitations-of-identity-protection-for-b2b-collaboration-users).

### <a name="excluding-guests-and-external-users-from-device-management"></a>Exclusion des invités et des utilisateurs externes de la gestion des appareils

Une seule organisation peut gérer un appareil. Si vous n’excluez pas les invités et les utilisateurs externes des stratégies qui nécessitent la conformité des appareils, ces stratégies bloqueront ces utilisateurs.

## <a name="next-step"></a>Étape suivante

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Stratégies pour les Microsoft 365 cloud et Microsoft Defender pour les applications cloud" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Configurer des stratégies d’accès conditionnel pour :

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
- [Microsoft Defender for Cloud Apps](mcas-saas-access-policies.md)
 
