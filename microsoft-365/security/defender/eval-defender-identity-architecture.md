---
title: Passer en revue les exigences d’architecture et l’infrastructure technique pour Microsoft Defender pour Identity
description: Le diagramme technique de Microsoft Defender pour Identity dans Microsoft 365 Defender vous aidera à comprendre l’identité dans Microsoft 365 avant de créer votre laboratoire d’essai ou votre environnement pilote.
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
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: e92fa629b49664b6f87c8e72c23a2f9cae74afe6
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750229"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-identity"></a>Passer en revue les exigences d’architecture et les concepts clés pour Microsoft Defender pour Identity


**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 1 sur 3](eval-defender-identity-overview.md) du processus de configuration de l’environnement d’évaluation pour Microsoft Defender pour Identity. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-identity-overview.md).

Avant d’activer Microsoft Defender pour Identity, veillez à bien comprendre l’architecture et à répondre aux exigences.

Microsoft Defender pour Identity utilise le Machine Learning et l’analytique comportementale pour identifier les attaques sur votre réseau local, ainsi que la détection et la prévention proactive des risques de connexion des utilisateurs associés aux identités cloud. Pour plus [d’informations, voir Qu’est-ce que Microsoft Defender pour Identity ?](/defender-for-identity/what-is)

Defender pour Identity protège vos Active Directory local utilisateurs et/ou utilisateurs synchronisés avec azure Active Directory (Azure AD). Pour protéger un environnement composé uniquement d’utilisateurs Azure AD, consultez [Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

## <a name="understand-the-architecture"></a>Comprendre l’architecture

Le diagramme suivant illustre l’architecture de base pour Defender pour Identity. 

:::image type="content" source="../../media/defender/m365-defender-identity-architecture.png" alt-text="Architecture d’identité pour Microsoft Defender pour Identity" lightbox="../../media/defender/m365-defender-identity-architecture.png":::

Dans cette illustration :

- Les capteurs installés sur les contrôleurs de domaine AD analysent les journaux et le trafic réseau et les envoient à Microsoft Defender pour Identity à des fins d’analyse et de création de rapports.
-  Les capteurs peuvent également analyser Services ADFS (AD FS) quand Azure AD est configuré pour utiliser l’authentification fédérée (ligne pointillée dans l’illustration). 
- Microsoft Defender pour Identity partage des signaux vers Microsoft 365 Defender pour la détection et la réponse étendues (XDR).

Les capteurs Defender pour Identity peuvent être installés directement sur les serveurs suivants :

- Contrôleurs de domaine : le capteur surveille directement le trafic des contrôleurs de domaine, sans avoir besoin d’un serveur dédié ni de configuration de la mise en miroir de ports.
- AD FS : le capteur surveille directement le trafic réseau et les événements d’authentification.

Pour une présentation plus approfondie de l’architecture de Defender pour Identity, notamment l’intégration à Defender pour Cloud Apps, consultez [Microsoft Defender pour Identity architecture](/defender-for-identity/architecture).


## <a name="understand-key-concepts"></a>Comprendre les concepts clés

Le tableau suivant a identifié des concepts clés qui sont importants à comprendre lors de l’évaluation, de la configuration et du déploiement de Microsoft Defender pour Identity.

|Concept  |Description |Plus d’informations  |
|---------|---------|---------|
| Activités surveillées | Defender pour Identity surveille les signaux générés à partir de votre organisation pour détecter les activités suspectes ou malveillantes et vous aide à déterminer la validité de chaque menace potentielle afin de pouvoir trier et répondre efficacement.  |  [activités surveillées Microsoft Defender pour Identity](/defender-for-identity/monitored-activities)       |
| Alertes de sécurité    | Les alertes de sécurité Defender pour Identity expliquent les activités suspectes détectées par les capteurs sur votre réseau, ainsi que les acteurs et les ordinateurs impliqués dans chaque menace.   | [alertes de sécurité Microsoft Defender pour Identity](/defender-for-identity/suspicious-activity-guide?tabs=external)    |
| Profils d’entité    | Les profils d’entité fournissent une investigation approfondie complète des utilisateurs, ordinateurs, appareils et ressources, ainsi que leur historique d’accès.   | [Présentation des profils d’entité](/defender-for-identity/entity-profiles)  |
| Chemins de mouvement latéral    | Un composant clé des insights de sécurité MDI consiste à identifier les chemins de mouvement latéral dans lesquels un attaquant utilise des comptes non sensibles pour accéder à des comptes ou machines sensibles sur l’ensemble de votre réseau.  | [Microsoft Defender pour Identity chemins de mouvement latéral (LPM)](/defender-for-identity/use-case-lateral-movement-path)  |
| Résolution de noms réseau    |  La résolution de noms réseau (NNR) est un composant de la fonctionnalité MDI qui capture les activités basées sur le trafic réseau, les événements Windows, ETW, etc. et met en corrélation ces données brutes avec les ordinateurs concernés par chaque activité.       | [Qu’est-ce que la résolution de noms réseau ?](/defender-for-identity/nnr-policy)      |
| Rapports    | Les rapports Defender pour Identity vous permettent de planifier ou de générer et de télécharger immédiatement des rapports qui fournissent des informations sur l’état du système et de l’entité.  Vous pouvez créer des rapports sur l’intégrité du système, les alertes de sécurité et les chemins de mouvement latéral potentiels détectés dans votre environnement.   | [rapports Microsoft Defender pour Identity](/defender-for-identity/reports)       |
| Groupes de rôles    | Defender pour Identity offre des groupes basés sur des rôles et un accès délégué pour protéger les données en fonction des besoins spécifiques de votre organisation en matière de sécurité et de conformité, notamment les administrateurs, les utilisateurs et les observateurs.        |  [Groupes de rôles dans Microsoft Defender pour Identity](/defender-for-identity/role-groups)       |
| Portail d’administration    |  En plus du portail Microsoft 365 Defender, le portail Defender pour Identity peut être utilisé pour surveiller et répondre aux activités suspectes.      | [Travailler avec le portail Microsoft Defender pour l’identité](/defender-for-identity/workspace-portal)        |
| intégration Microsoft Defender for Cloud Apps   | Microsoft Defender for Cloud Apps s’intègre à Microsoft Defender pour Identity pour fournir une analytique comportementale des entités utilisateur (UEBA) dans un environnement hybride , à la fois une application cloud et une application locale   | intégration Microsoft Defender pour Identity  |

## <a name="review-prerequisites"></a>Passer en revue les prérequis

Defender pour Identity nécessite un travail préalable pour garantir que vos composants d’identité et de mise en réseau locaux répondent aux exigences minimales. Utilisez cet article comme liste de vérification pour vous assurer que votre environnement est prêt : [Microsoft Defender pour Identity conditions préalables](/defender-for-identity/prerequisites).


## <a name="next-steps"></a>Prochaines étapes

Étape 2 sur 3 : [Activer l’environnement d’évaluation Defender pour Identity](eval-defender-identity-enable-eval.md)

Revenir à la vue d’ensemble de [Evaluate Microsoft Defender pour Identity](eval-defender-identity-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md) 
