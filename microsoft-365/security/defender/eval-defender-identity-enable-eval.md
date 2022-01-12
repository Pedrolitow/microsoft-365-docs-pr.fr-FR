---
title: Activer l’environnement d’évaluation pour Microsoft Defender pour l’identité
description: Configurez Microsoft Defender pour l’identité dans Microsoft 365 Defender laboratoire d’essai ou environnement pilote en installant & le capteur et en découvrant les administrateurs locaux sur d’autres ordinateurs.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 184ec4dcdd5601585e046ced410141047fdfa24f
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61942667"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-identity"></a>Activer l’environnement d’évaluation pour Microsoft Defender pour l’identité

**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 2 sur 2](eval-defender-identity-overview.md) dans le processus de configuration de l’environnement d’évaluation de Microsoft Defender pour l’identité. Pour plus d’informations sur ce processus, voir [l’article de présentation.](eval-defender-identity-overview.md)

Utilisez les étapes suivantes pour configurer votre environnement Microsoft Defender pour l’identité. 

![Étapes permettant d’activer Microsoft Defender pour l’identité dans l’environnement d’évaluation de Microsoft Defender.](../../media/defender/m365-defender-identity-eval-enable-steps.png)

- [Étape 1. Configurer Defender pour l’instance d’identité](#step-1-set-up-the-defender-for-identity-instance)
- [Étape 2. Installer et configurer le capteur](#step-2-install-and-configure-the-sensor)
- [Étape 3. Configurer les paramètres du journal des événements et du proxy sur les ordinateurs avec le capteur](#step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor)
- [Étape 4. Autoriser Defender for Identity à identifier les administrateurs locaux sur d’autres ordinateurs](#step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers)

## <a name="step-1-set-up-the-defender-for-identity-instance"></a>Étape 1. Configurer Defender pour l’instance d’identité

Connectez-vous au portail Defender pour l’identité pour créer votre instance, puis connectez cette instance à votre environnement Active Directory. 

|  |Étape     |Plus d’informations  |
|---------|---------|---------|
|1     | Créer l’instance Defender for Identity        | [Démarrage rapide : créer votre instance Microsoft Defender pour l’identité](/defender-for-identity/install-step1)        |
|2     | Connecter’instance Defender for Identity à votre forêt Active Directory   | [Démarrage rapide : Connecter votre forêt Active Directory](/defender-for-identity/install-step2)  |
| | |

## <a name="step-2-install-and-configure-the-sensor"></a>Étape 2. Installer et configurer le capteur

Ensuite, téléchargez, installez et configurez le capteur Defender for Identity sur les contrôleurs de domaine et les serveurs AD FS de votre environnement local.

|  |Étape     |Plus d’informations  |
|---------|---------|---------|
|1     | Déterminez le nombre de capteurs Microsoft Defender pour l’identité dont vous avez besoin.        | [Planifier la capacité de Microsoft Defender pour l’identité](/defender-for-identity/capacity-planning)   |
|2     | Télécharger le package d’installation du capteur  |  [Démarrage rapide : télécharger le package de configuration du capteur Microsoft Defender pour l’identité](/defender-for-identity/install-step3)   |
|3     | Installer le capteur Defender for Identity    |  [Démarrage rapide : installer le capteur Microsoft Defender pour l’identité](/defender-for-identity/install-step4)       |
|4     | Configurer le capteur       |  [Configurer les paramètres du capteur d’identité Microsoft Defender ](/defender-for-identity/install-step5)   |
|   |         |         |

## <a name="step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor"></a>Étape 3. Configurer les paramètres du journal des événements et du proxy sur les ordinateurs avec le capteur

Sur les ordinateurs sur qui vous avez installé le capteur, configurez Windows collection de journaux d’événements et les paramètres proxy Internet pour activer et améliorer les fonctionnalités de détection.

|  |Étape     |Plus d’informations  |
|---------|---------|---------|
|1     | Configurer la Windows journal des événements         | [Configurer Windows collection d’événements](/defender-for-identity/configure-windows-event-collection)        |
|2     | Configurer les paramètres de proxy Internet        | [Configurer les paramètres de proxy de point de terminaison et de connectivité Internet pour votre capteur d’identité Microsoft Defender](/defender-for-identity/configure-proxy)        |
|   |         |         |

## <a name="step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers"></a>Étape 4. Autoriser Defender for Identity à identifier les administrateurs locaux sur d’autres ordinateurs

La détection du chemin de déplacement latéral de Microsoft Defender pour l’identité s’appuie sur des requêtes qui identifient les administrateurs locaux sur des ordinateurs spécifiques. Ces requêtes sont effectuées avec le protocole SAM-R, à l’aide du compte Defender for Identity Service. 

Pour vous assurer que Windows clients et serveurs autorisent votre compte Defender for Identity à effectuer sam-R, une modification de la stratégie de groupe doit être apportée pour ajouter le compte de service Defender for Identity en plus des comptes configurés répertoriés dans la stratégie d’accès réseau. Veillez à appliquer des stratégies de groupe à tous les **ordinateurs à l’exception des contrôleurs de domaine.**

Pour obtenir des instructions sur la façon de faire, voir Configurer Microsoft Defender pour l’identité pour effectuer des [appels distants à SAM.](/defender-for-identity/install-step8-samr) 

## <a name="next-steps"></a>Étapes suivantes

Étape 3 sur 3 : Piloter [Microsoft Defender pour l’identité](eval-defender-identity-pilot.md)

Revenir à la vue d’ensemble [de l’évaluation de Microsoft Defender pour l’identité](eval-defender-identity-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md)