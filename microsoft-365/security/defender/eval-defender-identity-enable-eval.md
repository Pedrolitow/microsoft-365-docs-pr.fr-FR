---
title: Activer l’environnement d’évaluation pour Microsoft Defender pour Identity
description: Configurez Microsoft Defender pour Identity dans Microsoft 365 Defender laboratoire d’essai ou un environnement pilote en installant & en configurant le capteur et en découvrant les administrateurs locaux sur d’autres ordinateurs.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
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
- highpri
ms.topic: conceptual
ms.openlocfilehash: 800410fe4faecde9a104242d5d4a1821ad8de86a
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67482249"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-identity"></a>Activer l’environnement d’évaluation pour Microsoft Defender pour Identity

**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 2 sur 2](eval-defender-identity-overview.md) du processus de configuration de l’environnement d’évaluation pour Microsoft Defender pour Identity. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-identity-overview.md).

Procédez comme suit pour configurer votre environnement Microsoft Defender pour Identity. 

:::image type="content" source="../../media/defender/m365-defender-identity-eval-enable-steps.png" alt-text="Étapes permettant d’activer Microsoft Defender pour Identity dans l’environnement d’évaluation Microsoft Defender" lightbox="../../media/defender/m365-defender-identity-eval-enable-steps.png":::

- [Étape 1. Configurer Defender pour Identity Instance](#step-1-set-up-the-defender-for-identity-instance)
- [Étape 2. Installer et configurer le capteur](#step-2-install-and-configure-the-sensor)
- [Étape 3. Configurer les paramètres du journal des événements et du proxy sur les machines avec le capteur](#step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor)
- [Étape 4. Autoriser Defender pour Identity à identifier les administrateurs locaux sur d’autres ordinateurs](#step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers)

## <a name="step-1-set-up-the-defender-for-identity-instance"></a>Étape 1. Configurer Defender pour Identity Instance

Connectez-vous au portail Defender pour Identity pour créer votre instance, puis connectez-la à votre environnement Active Directory. 

|  Étape | Description     |Plus d’informations  |
|---------|---------|---------|
|1     | Créer l’instance Defender pour Identity        | [Démarrage rapide : créer votre instance Microsoft Defender pour l’identité](/defender-for-identity/install-step1)        |
|2     | Connecter l’instance Defender pour Identity à votre forêt Active Directory   | [Démarrage rapide : Se connecter à votre forêt Active Directory](/defender-for-identity/install-step2)  |

## <a name="step-2-install-and-configure-the-sensor"></a>Étape 2. Installer et configurer le capteur

Ensuite, téléchargez, installez et configurez le capteur Defender pour Identity sur les contrôleurs de domaine et les serveurs AD FS dans votre environnement local.

|  Étape | Description     |Plus d’informations  |
|---------|---------|---------|
|1     | Déterminez le nombre de capteurs Microsoft Defender pour Identity dont vous avez besoin.        | [Planifier la capacité de Microsoft Defender pour l’identité](/defender-for-identity/capacity-planning)   |
|2     | Télécharger le package d’installation du capteur  |  [Démarrage rapide : Télécharger le package d’installation du capteur Microsoft Defender pour Identity](/defender-for-identity/install-step3)   |
|3     | Installer le capteur Defender pour Identity    |  [Démarrage rapide : Installer le capteur Microsoft Defender pour Identity](/defender-for-identity/install-step4)       |
|4     | Configurer le capteur       |  [Configurer Microsoft Defender pour Identity paramètres de capteur](/defender-for-identity/install-step5)   |

## <a name="step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor"></a>Étape 3. Configurer les paramètres du journal des événements et du proxy sur les machines avec le capteur

Sur les machines sur lesquelles vous avez installé le capteur, configurez la collecte des journaux des événements Windows et les paramètres de proxy Internet pour activer et améliorer les fonctionnalités de détection.

|  Étape | Description     |Plus d’informations  |
|---------|---------|---------|
|1     | Configurer la collecte des journaux des événements Windows         | [Configurer la collection d’événements Windows](/defender-for-identity/configure-windows-event-collection)        |
|2     | Configurer les paramètres de proxy Internet        | [Configurer les paramètres de proxy de point de terminaison et de connectivité Internet pour votre capteur d’identité Microsoft Defender](/defender-for-identity/configure-proxy)        |

## <a name="step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers"></a>Étape 4. Autoriser Defender pour Identity à identifier les administrateurs locaux sur d’autres ordinateurs

La détection du chemin de déplacement latéral de Microsoft Defender pour l’identité s’appuie sur des requêtes qui identifient les administrateurs locaux sur des ordinateurs spécifiques. Ces requêtes sont effectuées avec le protocole SAM-R, à l’aide du compte Defender for Identity Service. 

Pour vous assurer que les clients et serveurs Windows autorisent votre compte Defender pour Identity à effectuer SAM-R, une modification de stratégie de groupe doit être apportée pour ajouter le compte de service Defender pour Identity en plus des comptes configurés répertoriés dans la stratégie d’accès réseau. Veillez à appliquer des stratégies de groupe à tous les ordinateurs **à l’exception des contrôleurs de domaine**.

Pour obtenir des instructions sur la façon de procéder, consultez [Configurer Microsoft Defender pour Identity pour effectuer des appels distants vers SAM](/defender-for-identity/install-step8-samr). 

## <a name="next-steps"></a>Prochaines étapes

Étape 3 sur 3 : [Pilote Microsoft Defender pour Identity](eval-defender-identity-pilot.md)

Revenir à la vue d’ensemble de [Evaluate Microsoft Defender pour Identity](eval-defender-identity-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)
