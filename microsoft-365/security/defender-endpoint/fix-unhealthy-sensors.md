---
title: Corriger les capteurs défectueux dans Microsoft Defender pour point de terminaison
description: Corrigez les capteurs d’appareil qui signalent une configuration incorrecte ou inactive afin que le service reçoive les données de l’appareil.
keywords: mal configuré, inactif, capteur de correction, intégrité du capteur, aucune donnée de capteur, données de capteur, communications altérées, communication
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 11/23/2020
ms.subservice: mde
ms.openlocfilehash: e53e453bb60a203dfaf32669ad7995ec6e96a839
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67516409"
---
# <a name="fix-unhealthy-sensors-in-microsoft-defender-for-endpoint"></a>Corriger les capteurs défectueux dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-fixsensor-abovefoldlink)

Les appareils peuvent être classés comme étant mal configurés ou inactifs sont marqués pour différentes causes. Cette section fournit des explications sur ce qui a pu provoquer la catégorisation d’un appareil comme inactif ou mal configuré.

## <a name="inactive-devices"></a>Appareils inactifs

Un appareil inactif n’est pas nécessairement signalé en raison d’un problème. Les actions suivantes effectuées sur un appareil peuvent entraîner la catégorisation d’un appareil comme inactif :

- L’appareil n’est pas utilisé
- L’appareil a été réinstallé ou renommé
- L’appareil a été retiré de la carte
- L’appareil n’envoie pas de signaux


### <a name="device-isnt-in-use"></a>L’appareil n’est pas utilisé

Tout appareil qui n’est pas utilisé pendant plus de sept jours conserve l’état « Inactif » dans le portail.

### <a name="device-was-reinstalled-or-renamed"></a>L’appareil a été réinstallé ou renommé
Une nouvelle entité d’appareil est générée dans Microsoft 365 Defender pour les appareils réinstallés ou renommés. L’entité d’appareil précédente reste, avec l’état « Inactif » dans le portail. Si vous avez réinstallé un appareil et déployé le package Defender pour point de terminaison, recherchez le nouveau nom d’appareil pour vérifier que l’appareil signale normalement.

### <a name="device-was-offboarded"></a>L’appareil a été retiré de la carte
Si l’appareil a été désintégré, il apparaîtra toujours dans la liste des appareils. Après sept jours, l’état d’intégrité de l’appareil doit passer à inactif.

### <a name="device-isnt-sending-signals"></a>L’appareil n’envoie pas de signaux
Si l’appareil n’envoie aucun signal à des canaux Microsoft Defender pour point de terminaison pendant plus de sept jours pour une raison quelconque, un appareil peut être considéré comme inactif; cela inclut les conditions qui relèvent d’une classification incorrecte des appareils.

Vous attendez-vous à ce qu’un appareil soit dans l’état « Actif » ? [Ouvrez un ticket de support](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636206786382823561).

## <a name="misconfigured-devices"></a>Appareils mal configurés
Les appareils mal configurés peuvent être classés dans les catégories suivantes :
- Communications altérées
- Aucune donnée de capteur

### <a name="impaired-communications"></a>Communications altérées
Cet état indique qu’il existe une communication limitée entre l’appareil et le service.

Les actions suggérées suivantes peuvent aider à résoudre les problèmes liés à un appareil mal configuré avec des communications altérées :

- [Vérifier que l’appareil dispose d’une connexion Internet](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Le capteur Microsoft Defender pour point de terminaison requiert Microsoft Windows HTTP (WinHTTP) pour signaler les données du capteur et communiquer avec le service Microsoft Defender pour point de terminaison.

- [Vérifier la connectivité du client aux URL de service Microsoft Defender pour point de terminaison](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Vérifiez que la configuration du proxy s’est correctement déroulée, que WinHTTP peut découvrir et communiquer via le serveur proxy dans votre environnement, et que le serveur proxy autorise le trafic vers les URL de service Microsoft Defender pour point de terminaison.

Si vous avez pris des mesures correctives et que l’état de l’appareil est toujours mal configuré, [ouvrez un ticket de support](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

### <a name="no-sensor-data"></a>Aucune donnée de capteur
Un appareil mal configuré avec l’état « Aucune donnée de capteur » communique avec le service, mais ne peut signaler que des données de capteur partielles.

Suivez ces actions pour corriger les problèmes connus liés à un appareil mal configuré avec l’état « Aucune donnée de capteur » :

- [Vérifier que l’appareil dispose d’une connexion Internet](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Le capteur Microsoft Defender pour point de terminaison requiert Microsoft Windows HTTP (WinHTTP) pour signaler les données du capteur et communiquer avec le service Microsoft Defender pour point de terminaison.

- [Vérifier la connectivité du client aux URL de service Microsoft Defender pour point de terminaison](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Vérifiez que la configuration du proxy s’est correctement déroulée, que WinHTTP peut découvrir et communiquer via le serveur proxy dans votre environnement, et que le serveur proxy autorise le trafic vers les URL de service Microsoft Defender pour point de terminaison.

- [Vérifier que le service de données de diagnostic est activé](troubleshoot-onboarding.md#ensure-the-diagnostics-service-is-enabled)</br>
Si les appareils ne signalent pas correctement, vous devez vérifier que le service de données de diagnostic Windows est configuré pour démarrer automatiquement. Vérifiez également que le service de données de diagnostic Windows s’exécute sur le point de terminaison.

- [Vérifier que l’antivirus Microsoft Defender n’est pas désactivé par la stratégie](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)</br>
Si vos appareils exécutent un client anti-programme malveillant tiers, l’agent Defender pour point de terminaison requiert que le pilote ELAM (Early Launch Antimalware) antivirus Microsoft Defender soit activé.

Si vous avez pris des mesures correctives et que l’état de l’appareil est toujours mal configuré, [ouvrez un ticket de support](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

## <a name="see-also"></a>Voir aussi
- [Vérifier l’état d’intégrité du capteur dans Microsoft Defender pour point de terminaison](check-sensor-status.md)
- [Vue d’ensemble de l’analyseur client](overview-client-analyzer.md)
- [Télécharger et exécuter l’analyseur client](download-client-analyzer.md)
- [Exécuter l’analyseur client sur Windows](run-analyzer-windows.md)
- [Exécuter l’analyseur client sur macOS ou Linux](run-analyzer-macos-linux.md)
- [Collecte de données pour la résolution avancée des problèmes sur Windows](data-collection-analyzer.md)

