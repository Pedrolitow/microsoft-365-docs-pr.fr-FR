---
title: Stratégies d’accès aux identités et aux appareils pour autoriser l’accès B2B des utilisateurs invités et externes - Microsoft 365 pour les | Microsoft Docs
description: Décrit l’accès conditionnel recommandé et les stratégies associées pour protéger l’accès des invités et des utilisateurs externes.
ms.service: microsoft-365-security
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
- zerotrust-solution
- highpri
ms.subservice: mdo
search.appverid: met150
ms.openlocfilehash: 5ef7d48943ab33e9b148d51a651884f9b62943e5
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67687392"
---
# <a name="policies-for-allowing-guest-access-and-b2b-external-user-access"></a>Stratégies permettant d’autoriser l’accès invité et l’accès des utilisateurs externes B2B

Cet article décrit l’ajustement des stratégies d’identité et d’accès aux appareils Confiance nulle recommandées pour autoriser l’accès pour les invités et les utilisateurs externes disposant d’un compte Azure Active Directory (Azure AD) B2B (Business-to-Business). Ce guide s’appuie sur les stratégies [d’accès aux identités et aux appareils courantes](identity-access-policies.md).

Ces recommandations sont conçues pour s’appliquer au niveau de **protection du point de départ** . Toutefois, vous pouvez également ajuster les recommandations en fonction de vos besoins spécifiques en matière de protection **de la sécurité d’entreprise et spécialisée**.

Fournir un chemin d’accès pour que les comptes B2B s’authentifient auprès de votre locataire Azure AD ne donne pas à ces comptes l’accès à l’ensemble de votre environnement. Les utilisateurs B2B et leurs comptes ont accès à des services et des ressources, tels que des fichiers, partagés avec eux par la stratégie d’accès conditionnel.

## <a name="updating-the-common-policies-to-allow-and-protect-guests-and-external-user-access"></a>Mise à jour des stratégies courantes pour autoriser et protéger les invités et l’accès des utilisateurs externes

Ce diagramme montre les stratégies à ajouter ou à mettre à jour parmi les stratégies d’accès aux identités et aux appareils courantes, pour l’accès des utilisateurs invités et externes B2B.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png" alt-text="Récapitulatif des mises à jour de stratégie pour la protection de l’accès invité" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png":::

Le tableau suivant répertorie les stratégies que vous devez créer et mettre à jour. Les stratégies courantes sont liées aux instructions de configuration associées dans l’article [Stratégies d’accès aux appareils et aux identités communes](identity-access-policies.md) .

|Niveau de protection|Stratégies|Informations supplémentaires|
|---|---|---|
|**Point de départ**|[Exiger l’authentification multifacteur toujours pour les invités et les utilisateurs externes](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Créez cette stratégie et configurez : <ul><li>Pour **Affectations > Utilisateurs et groupes > Inclure**, **choisissez Sélectionner des utilisateurs et des groupes**, puis sélectionnez **Tous les utilisateurs invités et externes**.</li><li>Pour **les affectations > conditions >** connexion, laissez toutes les options désactivées pour appliquer toujours l’authentification multifacteur (MFA).</li></ul>|
||[Exiger l’authentification multifacteur lorsque le risque de connexion est *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Modifiez cette stratégie pour exclure les invités et les utilisateurs externes.|

Pour inclure ou exclure des invités et des utilisateurs externes dans les stratégies d’accès conditionnel, pour **affectations > utilisateurs et groupes > Inclure** ou **Exclure**, vérifiez **tous les utilisateurs invités et externes**.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png" alt-text="Contrôles d’exclusion des invités et des utilisateurs externes" lightbox="../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png":::

## <a name="more-information"></a>Plus d’informations

### <a name="guests-and-external-user-access-with-microsoft-teams"></a>Invités et accès utilisateur externe avec Microsoft Teams

Microsoft Teams définit les utilisateurs suivants :

- **L’accès invité** utilise un compte Azure AD B2B qui peut être ajouté en tant que membre d’une équipe et avoir accès aux communications et aux ressources de l’équipe.

- **L’accès externe** est destiné à un utilisateur externe qui n’a pas de compte B2B. L’accès des utilisateurs externes inclut des invitations, des appels, des conversations et des réunions, mais n’inclut pas l’appartenance à l’équipe et l’accès aux ressources de l’équipe.

Pour plus d’informations, consultez la [comparaison entre les invités et l’accès des utilisateurs externes pour les équipes](/microsoftteams/communicate-with-users-from-other-organizations#compare-external-and-guest-access).

Pour plus d’informations sur la sécurisation des stratégies d’identité et d’accès aux appareils pour Teams, consultez [les recommandations de stratégie pour la sécurisation des conversations, des groupes et des fichiers Teams](teams-access-policies.md).

### <a name="require-mfa-always-for-guest-and-external-users"></a>Exiger toujours l’authentification multifacteur pour les utilisateurs invités et externes

Cette stratégie invite les invités à s’inscrire à l’authentification multifacteur dans votre locataire, qu’ils soient inscrits ou non à l’authentification multifacteur dans leur locataire d’origine. Lors de l’accès aux ressources de votre locataire, les invités et les utilisateurs externes doivent utiliser l’authentification multifacteur pour chaque requête.

### <a name="excluding-guests-and-external-users-from-risk-based-mfa"></a>Exclusion des invités et des utilisateurs externes de l’authentification multifacteur basée sur les risques

Bien que les organisations puissent appliquer des stratégies basées sur les risques pour les utilisateurs B2B utilisant Azure AD Identity Protection, il existe des limitations dans l’implémentation d’Azure AD Identity Protection pour les utilisateurs B2B Collaboration dans un répertoire de ressources en raison de leur identité existante dans leur répertoire de base. En raison de ces limitations, Microsoft vous recommande d’exclure les invités des stratégies d’authentification multifacteur basées sur les risques et d’exiger que ces utilisateurs utilisent toujours l’authentification multifacteur.

Pour plus d’informations, consultez [Limitations de Identity Protection pour les utilisateurs B2B Collaboration](/azure/active-directory/identity-protection/concept-identity-protection-b2b#limitations-of-identity-protection-for-b2b-collaboration-users).

### <a name="excluding-guests-and-external-users-from-device-management"></a>Exclusion des invités et des utilisateurs externes de la gestion des appareils

Une seule organisation peut gérer un appareil. Si vous n’excluez pas les invités et les utilisateurs externes des stratégies qui nécessitent la conformité des appareils, ces stratégies bloquent ces utilisateurs.

## <a name="next-step"></a>Étape suivante

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Stratégies pour les applications cloud Microsoft 365 et Microsoft Defender for Cloud Apps" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Configurer des stratégies d’accès conditionnel pour :

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
- [Microsoft Defender for Cloud Apps](mcas-saas-access-policies.md)
 
