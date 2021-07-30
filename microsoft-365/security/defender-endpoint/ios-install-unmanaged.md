---
title: Déployer Microsoft Defender pour le point de terminaison sur les fonctionnalités iOS
description: Décrit comment déployer Microsoft Defender pour Endpoint sur des appareils iOS non inscrits.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, ios, configurer, fonctionnalités, ios
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5f8caa7fa5379c32333ccdab807cca453cf49567
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53656414"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-unenrolled-ios-devices"></a>Déployer Microsoft Defender pour endpoint sur des appareils iOS non inscrits

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Defender pour le point de terminaison sur iOS utilise un VPN pour fournir la fonctionnalité de protection web. Il ne s’agit pas d’un VPN normal et d’un VPN local/en boucle autonome qui ne prend pas le trafic en dehors de l’appareil.

## <a name="configure-microsoft-defender-for-endpoint-risk-signals-in-app-protection-policy-mam"></a>Configurer Microsoft Defender pour les signaux de risque de point de terminaison dans la stratégie de protection des applications (MAM)

Microsoft Defender pour le point de terminaison peut être configuré pour envoyer des signaux de menace à utiliser dans les stratégies de protection des applications (APP, également appelée MAM) sur iOS/iPadOS. Avec cette fonctionnalité, vous pouvez également utiliser Microsoft Defender for Endpoint pour protéger l’accès aux données d’entreprise des appareils non inscrits.

Les étapes de configuration des stratégies de protection des applications avec Microsoft Defender pour Endpoint sont les suivantes :

1. Configurer la connexion de votre client Microsoft Endpoint Manager microsoft Defender pour le point de terminaison. Dans le Centre d’administration [Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)sélectionnez Connecteurs d’administration des clients et jetons Microsoft Defender pour le point de terminaison (sous Plateforme croisée) ou  >    >   **Endpoint Security** Microsoft Defender for Endpoint (sous Programme d’installation) et activer les boutons bascule sous App Protection Policy Paramètres pour  >   **iOS.**
1. Sélectionnez **Enregistrer**. Vous devriez voir **que l’état de** la connexion est désormais **activé.**
1. Créez la stratégie de protection des applications : une fois la configuration de votre connecteur Microsoft Defender pour point de terminaison terminée, accédez aux stratégies de protection des applications (sous Stratégie) pour créer une stratégie ou mettre à jour une stratégie  >   existante.
1. Sélectionnez les paramètres de plateforme, **d’applications, de protection** des données et d’accès requis par votre organisation pour votre stratégie.
1. Dans **les conditions de lancement**  >  **conditionnel de** l’appareil, vous trouverez le paramètre Niveau de menace maximum autorisé de **l’appareil.** Il doit être configuré sur Faible, Moyen, Élevé ou Sécurisé. Les actions à votre disposition seront **Bloquer** l’accès ou Effacer **les données.** Vous pouvez voir une boîte de dialogue d’information pour vous assurer que votre connecteur est bien installé avant que ce paramètre prenne effet. Si votre connecteur est déjà installé, vous pouvez ignorer cette boîte de dialogue.
1. Terminez avec Affectations et enregistrez votre stratégie.

Pour plus d’informations sur la stratégie de protection des applications ou de gestion des applications, voir les paramètres de stratégie de protection des [applications iOS.](/mem/intune/apps/app-protection-policy-settings-ios)

## <a name="deploy-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Déployer Microsoft Defender pour le point de terminaison pour MAM ou sur des appareils non inscrits

Microsoft Defender pour le point de terminaison sur iOS active le scénario de stratégie de protection des applications et est disponible dans l’App Store d’Apple.

Lorsque des stratégies de protection des applications sont configurées pour que les applications incluent les signaux de risque de l’appareil de Microsoft Defender pour le point de terminaison, les utilisateurs sont redirigés vers l’installation de Microsoft Defender pour le point de terminaison lors de l’utilisation de ces applications. Les utilisateurs peuvent également installer la dernière version de l’application directement à partir de l’App Store d’Apple.
