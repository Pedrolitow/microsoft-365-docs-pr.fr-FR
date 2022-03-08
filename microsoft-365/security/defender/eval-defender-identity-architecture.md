---
title: Passer en revue les exigences en matière d’architecture et l’infrastructure technique de Microsoft Defender pour l’identité
description: Le diagramme technique de Microsoft Defender pour l’identité dans Microsoft 365 Defender vous aidera à comprendre l’identité dans Microsoft 365 avant de créer votre laboratoire d’essai ou votre environnement pilote.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: e534211008ea560642ba306844b9223170ac0140
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323218"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-identity"></a>Passer en revue les exigences en matière d’architecture et les concepts clés de Microsoft Defender pour l’identité


**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 1 sur 3 dans](eval-defender-identity-overview.md) le processus de configuration de l’environnement d’évaluation de Microsoft Defender pour l’identité. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-identity-overview.md).

Avant d’activer Microsoft Defender pour l’identité, veillez à bien comprendre l’architecture et à répondre aux exigences.

Microsoft Defender pour l’identité utilise l’apprentissage automatique et l’analyse comportementale pour identifier les attaques sur votre réseau local, ainsi que pour détecter et empêcher de manière proactive les risques de connecteur des utilisateurs associés aux identités cloud. Pour plus d’informations, [voir Qu’est-ce que Microsoft Defender pour l’identité ?](/defender-for-identity/what-is)

Defender pour l’identité protège vos utilisateurs Active Directory locaux et/ou les utilisateurs synchronisés avec Azure Active Directory (Azure AD). Pour protéger un environnement composé uniquement d’Azure AD utilisateurs, voir [Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

## <a name="understand-the-architecture"></a>Comprendre l’architecture

Le diagramme suivant illustre l’architecture de base de Defender for Identity. 

![Architecture de Microsoft Defender pour l’identité.](../../media/defender/m365-defender-identity-architecture.png)

Dans cette illustration :
- Les capteurs installés sur les contrôleurs de domaine AD analysent les journaux et le trafic réseau et les envoient à Microsoft Defender pour identité pour analyse et rapport.
-  Les capteurs peuvent également utiliser les services AD FS (Active Directory Federation Services) lorsque Azure AD est configuré pour utiliser l’authentification fédérée (ligne pointillée dans l’illustration). 
- Microsoft Defender pour l’identité partage des signaux Microsoft 365 Defender pour la détection et la réponse étendues (XDR).


Les capteurs Defender for Identity peuvent être installés directement sur les serveurs suivants :

- Contrôleurs de domaine : le capteur surveille directement le trafic du contrôleur de domaine, sans avoir besoin d’un serveur dédié, ni de configuration de la mise en miroir des ports.
- AD FS : le capteur surveille directement le trafic réseau et les événements d’authentification.

Pour une analyse plus approfondie de l’architecture de Defender pour l’identité, y compris l’intégration à Defender pour les applications cloud, voir [Microsoft Defender pour l’architecture de l’identité](/defender-for-identity/architecture).


## <a name="understand-key-concepts"></a>Comprendre les concepts clés

Le tableau suivant a identifié les concepts clés à comprendre lors de l’évaluation, de la configuration et du déploiement de Microsoft Defender pour l’identité.


|Concept  |Description |Plus d’informations  |
|---------|---------|---------|
| Activités surveillées | Defender for Identity surveille les signaux générés au sein de votre organisation pour détecter les activités suspectes ou malveillantes et vous aide à déterminer la validité de chaque menace potentielle afin de pouvoir trier et répondre efficacement.  |  [Activités surveillées de Microsoft Defender pour l’identité](/defender-for-identity/monitored-activities)       |
| Alertes de sécurité    | Les alertes de sécurité Defender for Identity expliquent les activités suspectes détectées par les capteurs sur votre réseau, ainsi que les acteurs et ordinateurs impliqués dans chaque menace.   | [Microsoft Defender pour les alertes de sécurité des identités](/defender-for-identity/suspicious-activity-guide?tabs=external)    |
| Profils d’entité    | Les profils d’entité fournissent une enquête approfondie complète sur les utilisateurs, les ordinateurs, les appareils et les ressources, ainsi que leur historique d’accès.   | [Comprendre les profils d’entité](/defender-for-identity/entity-profiles)  |
| Chemins de déplacement latéral    | Un composant clé des informations de sécurité MDI consiste à identifier les chemins de déplacement latéral dans lesquels un attaquant utilise des comptes non sensibles pour accéder à des comptes ou des ordinateurs sensibles dans l’ensemble de votre réseau.  | [Microsoft Defender for Identity Lateral Movement Paths (LMP)](/defender-for-identity/use-case-lateral-movement-path)  |
| Résolution des noms réseau    |  La résolution de noms réseau (NNR) est un composant de la fonctionnalité MDI qui capture les activités basées sur le trafic réseau, les événements Windows, ETW, etc. et met en corrélation ces données brutes avec les ordinateurs concernés impliqués dans chaque activité.       | [Qu’est-ce que la résolution de nom de réseau ?](/defender-for-identity/nnr-policy)      |
| Rapports    | Les rapports Defender for Identity vous permettent de planifier ou de générer et de télécharger immédiatement des rapports qui fournissent des informations sur l’état du système et de l’entité.  Vous pouvez créer des rapports sur l’état du système, les alertes de sécurité et les chemins de déplacement latéral potentiels détectés dans votre environnement.   | [Microsoft Defender pour les rapports d’identité ](/defender-for-identity/reports)       |
| Groupes de rôles    | Defender pour l’identité offre des groupes basés sur des rôles et un accès délégué pour protéger les données en fonction des besoins spécifiques de votre organisation en matière de sécurité et de conformité, notamment les administrateurs, les utilisateurs et les visiteurs.        |  [Groupes de rôles dans Microsoft Defender pour Identity](/defender-for-identity/role-groups)       |
| Portail d’administration    |  Outre le portail Microsoft 365 Defender, le portail Defender pour l’identité peut être utilisé pour surveiller les activités suspectes et y répondre.      | [Travailler avec le portail Microsoft Defender pour l’identité](/defender-for-identity/workspace-portal)        |
| Intégration de Microsoft Defender pour les applications cloud   | Microsoft Defender pour les applications cloud s’intègre à Microsoft Defender pour l’identité pour fournir l’analyse comportementale de l’entité utilisateur (UEBA) dans un environnement hybride : application cloud et local   | Intégration de Microsoft Defender pour l’identité  |
| | | |


## <a name="review-prerequisites"></a>Examiner les conditions préalables

Defender pour l’identité nécessite un travail prérequis pour vous assurer que vos composants d’identité et de réseau locaux répondent aux exigences minimales. Utilisez cet article comme liste de vérification pour vous assurer que votre environnement est prêt : [conditions préalables de Microsoft Defender pour l’identité](/defender-for-identity/prerequisites).


## <a name="next-steps"></a>Étapes suivantes

Étape 2 sur 3 : activer [l’environnement d’évaluation Defender for Identity](eval-defender-identity-enable-eval.md)

Revenir à la vue d’ensemble [de l’évaluation de Microsoft Defender pour l’identité](eval-defender-identity-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md) 
