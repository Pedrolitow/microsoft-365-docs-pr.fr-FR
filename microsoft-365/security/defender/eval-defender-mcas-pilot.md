---
title: Pilotez Microsoft Cloud App Security avec Microsoft 365 Defender, créez des groupes pilotes, configurez le contrôle d’accès conditionnel, testez les fonctionnalités, configurez l’installation dans le cadre Microsoft 365 Defender
description: Configurer votre laboratoire d Microsoft 365 Defender d’essai ou votre environnement pilote pour tester et tester la solution de sécurité conçue pour protéger les appareils, l’identité, les données et les applications.
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: e061bf213ee929f91a48b03c71b9654a7ea76b8c
ms.sourcegitcommit: 718759c7146062841f7eb4a0a9a8bdddce0139b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2021
ms.locfileid: "53457759"
---
# <a name="pilot-microsoft-cloud-app-security-with-microsoft-365-defender"></a>Pilote Microsoft Cloud App Security avec Microsoft 365 Defender


**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 3 sur 3](eval-defender-mcas-overview.md) dans le processus de configuration de l’environnement d’évaluation pour Microsoft Cloud App Security. Pour plus d’informations sur ce processus, voir [l’article de présentation.](eval-defender-mcas-overview.md)

Utilisez les étapes suivantes pour configurer et configurer le pilote pour Microsoft Cloud App Security.


![Étapes de pilotage des Microsoft Cloud App Security](../../media/defender/m365-defender-mcas-pilot-steps.png)

- Étape 1. [Créer le groupe pilote : étendue de votre déploiement pilote à certains groupes d’utilisateurs](#step-1-create-the-pilot-group--scope-your-pilot-deployment-to-certain-user-groups)
- [Étape 2. Configurer la protection — Contrôle d’application d’accès conditionnel](#step-2-configure-protection--conditional-access-app-control)
- [Étape 3. Tester les fonctionnalités : parcourir les didacticiels pour protéger votre environnement](#step-3-try-out-capabilities--walk-through-tutorials-for-protecting-your-environment) 


## <a name="step-1-create-the-pilot-group--scope-your-pilot-deployment-to-certain-user-groups"></a>Étape 1. Créer le groupe pilote : étendue de votre déploiement pilote à certains groupes d’utilisateurs

Microsoft Cloud App Security vous permet d’élargir l’étendue de votre déploiement. L’application d’une portée vous permet de sélectionner certains groupes d’utilisateurs à surveiller pour les applications ou à exclure de la surveillance. Vous pouvez inclure ou exclure des groupes d’utilisateurs. Pour l’étendue de votre déploiement pilote, voir [Déploiement dans l’étendue.](/cloud-app-security/scoped-deployment)


## <a name="step-2-configure-protection--conditional-access-app-control"></a>Étape 2. Configurer la protection — Contrôle d’application d’accès conditionnel

L’une des protections les plus puissantes que vous pouvez configurer est le contrôle d’application d’accès conditionnel. Cela nécessite une intégration avec Azure Active Directory (Azure AD). Il vous permet d’appliquer des stratégies d’accès conditionnel, y compris des stratégies associées (comme la nécessité d’appareils sains), aux applications cloud que vous avez prises en compte. 

La première étape de l’Microsoft Cloud App Security gérer les applications SaaS consiste à les découvrir, puis à les ajouter à votre client Azure AD. Si vous avez besoin d’aide pour la découverte, [consultez Découvrir et gérer les applications SaaS dans votre réseau.](/cloud-app-security/tutorial-shadow-it) Une fois que vous avez découvert les applications, [ajoutez-les à votre client Azure AD.](/azure/active-directory/manage-apps/add-application-portal)

Vous pouvez commencer à les gérer en suivant les mesures suivantes :

- Tout d’abord, dans Azure AD, créez une stratégie d’accès conditionnel et configurez-la pour « Utiliser le contrôle d’application d’accès conditionnel ». Cela redirige la demande vers Sécurité des applications cloud. Vous pouvez créer une stratégie et ajouter toutes les applications SaaS à cette stratégie.
- Ensuite, dans Sécurité des applications cloud, créez des stratégies de session. Créez une stratégie pour chaque contrôle que vous souhaitez appliquer.

Pour plus d’informations, notamment sur les applications et les clients pris en charge, voir Protéger les applications [Microsoft Cloud App Security contrôle d’application d’accès conditionnel.](/cloud-app-security/proxy-intro-aad) 

Par exemple, les [stratégies recommandées Microsoft Cloud App Security pour les applications SaaS.](../office-365-security/mcas-saas-access-policies.md) Ces stratégies s’appuient sur un ensemble de stratégies communes d’accès aux identités et aux appareils qui sont recommandées comme point de départ pour tous les clients. [](../office-365-security/microsoft-365-policies-configurations.md) 

## <a name="step-3-try-out-capabilities--walk-through-tutorials-for-protecting-your-environment"></a>Étape 3. Tester les fonctionnalités : parcourir les didacticiels pour protéger votre environnement 

La documentation Microsoft Cloud App Security comprend une série de didacticiels pour vous aider à découvrir les risques et à protéger votre environnement. 

Essayez les Sécurité des applications cloud didacticiels suivants :

- [Détecter les activités suspectes de l’utilisateur](/cloud-app-security/tutorial-suspicious-activity)
- [Examiner les utilisateurs à risque](/cloud-app-security/tutorial-ueba)
- [Examiner les applications OAuth risquées](/cloud-app-security/investigate-risky-oauth)
- [Découvrir et protéger les informations sensibles](/cloud-app-security/tutorial-dlp)
- [Protéger n’importe quelle application de votre organisation en temps réel](/cloud-app-security/tutorial-proxy)
- [Bloquer les téléchargements d’informations sensibles](/cloud-app-security/use-case-proxy-block-session-aad)
- [Protéger vos fichiers avec la mise en quarantaine de l’administrateur](/cloud-app-security/use-case-admin-quarantine)
- [Exiger l’authentification par étapes en cas d’action risquée](/cloud-app-security/tutorial-step-up-authentication)

## <a name="next-steps"></a>Étapes suivantes

[Examiner et répondre à l’Microsoft 365 Defender dans un environnement pilote](eval-defender-investigate-respond.md)

Revenir à la vue d’ensemble [de l’Microsoft Cloud App Security](eval-defender-mcas-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md)