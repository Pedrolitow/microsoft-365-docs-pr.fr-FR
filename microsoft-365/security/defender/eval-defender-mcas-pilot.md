---
title: Pilote Microsoft Defender for Cloud Apps avec Microsoft 365 Defender
description: Configurez votre laboratoire d’essai Microsoft 365 Defender ou votre environnement pilote pour tester et tester la solution de sécurité conçue pour protéger les appareils, l’identité, les données et les applications.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 7dbf9154769ab4b97c15dc5fc67593b376ab2f6d
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750339"
---
# <a name="pilot-microsoft-defender-for-cloud-apps-with-microsoft-365-defender"></a>Pilote Microsoft Defender for Cloud Apps avec Microsoft 365 Defender


**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 3 sur 3](eval-defender-mcas-overview.md) du processus de configuration de l’environnement d’évaluation pour Microsoft Defender for Cloud Apps. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-mcas-overview.md).

Utilisez les étapes suivantes pour configurer et configurer le pilote pour Microsoft Defender for Cloud Apps.


:::image type="content" source="../../media/defender/m365-defender-mcas-pilot-steps.png" alt-text="Étapes de la mise à l’essai de la Microsoft Defender for Cloud Apps" lightbox="../../media/defender/m365-defender-mcas-pilot-steps.png":::
- [Étape 1. Créer le groupe pilote : étendre votre déploiement pilote à certains groupes d’utilisateurs](#step-1-create-the-pilot-groupscope-your-pilot-deployment-to-certain-user-groups)
- [Étape 2. Configurer la protection : contrôle d’application d’accès conditionnel](#step-2-configure-protectionconditional-access-app-control)
- [Étape 3. Tester des fonctionnalités : suivez des didacticiels pour protéger votre environnement](#step-3-try-out-capabilitieswalk-through-tutorials-for-protecting-your-environment) 

## <a name="step-1-create-the-pilot-groupscope-your-pilot-deployment-to-certain-user-groups"></a>Étape 1. Créer le groupe pilote : étendre votre déploiement pilote à certains groupes d’utilisateurs

Microsoft Defender for Cloud Apps vous permet d’étendre votre déploiement. L’étendue vous permet de sélectionner certains groupes d’utilisateurs à surveiller pour les applications ou de les exclure de la surveillance. Vous pouvez inclure ou exclure des groupes d’utilisateurs. Pour définir l’étendue de votre déploiement pilote, consultez [Déploiement délimité](/cloud-app-security/scoped-deployment).


## <a name="step-2-configure-protectionconditional-access-app-control"></a>Étape 2. Configurer la protection : contrôle d’application d’accès conditionnel

L’une des protections les plus puissantes que vous pouvez configurer est le contrôle d’application d’accès conditionnel. Cette protection nécessite une intégration à Azure Active Directory (Azure AD). Il vous permet d’appliquer des stratégies d’accès conditionnel, y compris des stratégies connexes (par exemple, exiger des appareils sains) aux applications cloud que vous avez approuvées. 

La première étape de l’utilisation de Microsoft Defender for Cloud Apps pour gérer les applications SaaS consiste à découvrir ces applications, puis à les ajouter à votre locataire Azure AD. Si vous avez besoin d’aide pour la découverte, consultez [Découvrir et gérer les applications SaaS dans votre réseau](/cloud-app-security/tutorial-shadow-it). Une fois que vous avez découvert des applications, [ajoutez-les à votre locataire Azure AD](/azure/active-directory/manage-apps/add-application-portal).

Vous pouvez commencer à gérer ces applications en exécutant les tâches suivantes :

- Tout d’abord, dans Azure AD, créez une stratégie d’accès conditionnel et configurez-la pour « Utiliser le contrôle d’application d’accès conditionnel ». Cette configuration permet de rediriger la demande vers Defender pour Cloud Apps. Vous pouvez créer une stratégie et ajouter toutes les applications SaaS à cette stratégie.
- Ensuite, dans Defender pour Cloud Apps, créez des stratégies de session. Créez une stratégie pour chaque contrôle que vous souhaitez appliquer.

Pour plus d’informations, notamment les applications et les clients pris en charge, consultez [Protéger les applications avec Microsoft Defender for Cloud Apps contrôle d’application d’accès conditionnel](/cloud-app-security/proxy-intro-aad). 

Pour obtenir des exemples de stratégies, consultez [Stratégies de Microsoft Defender for Cloud Apps recommandées pour les applications SaaS](../office-365-security/mcas-saas-access-policies.md). Ces stratégies s’appuient sur un ensemble de stratégies [d’identité et d’accès aux appareils communes](../office-365-security/microsoft-365-policies-configurations.md) qui sont recommandées comme point de départ pour tous les clients. 

## <a name="step-3-try-out-capabilitieswalk-through-tutorials-for-protecting-your-environment"></a>Étape 3. Tester des fonctionnalités : suivez des didacticiels pour protéger votre environnement 

La documentation Microsoft Defender for Cloud Apps comprend une série de didacticiels pour vous aider à découvrir les risques et à protéger votre environnement. 

Essayez les didacticiels Defender pour Cloud Apps :

- [Détecter l’activité suspecte des utilisateurs](/cloud-app-security/tutorial-suspicious-activity)
- [Examiner les utilisateurs à risque](/cloud-app-security/tutorial-ueba)
- [Examiner les applications OAuth à risque](/cloud-app-security/investigate-risky-oauth)
- [Découvrir et protéger des informations sensibles](/cloud-app-security/tutorial-dlp)
- [Protéger n’importe quelle application de votre organisation en temps réel](/cloud-app-security/tutorial-proxy)
- [Bloquer les téléchargements d’informations sensibles](/cloud-app-security/use-case-proxy-block-session-aad)
- [Protéger vos fichiers avec la quarantaine d’administrateurs](/cloud-app-security/use-case-admin-quarantine)
- [Exiger une authentification par étapes lors d’une action risquée](/cloud-app-security/tutorial-step-up-authentication)

Pour plus d’informations sur la chasse avancée dans Microsoft Defender for Cloud Apps données, consultez la [vidéo](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa).

## <a name="next-steps"></a>Prochaines étapes

[Examiner et répondre à l’aide de Microsoft 365 Defender dans un environnement pilote](eval-defender-investigate-respond.md)

Revenir à la vue d’ensemble de [Evaluate Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)
