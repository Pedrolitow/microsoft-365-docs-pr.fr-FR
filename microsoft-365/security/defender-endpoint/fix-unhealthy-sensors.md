---
title: Corriger les capteurs défectueux dans Microsoft Defender pour le point de terminaison
description: Corrigez les capteurs d’appareil qui indiquent qu’ils sont mal configurés ou inactifs afin que le service reçoie les données de l’appareil.
keywords: mal configuré, inactif, corriger le capteur, l’état du capteur, aucune donnée de capteur, données du capteur, communications altérées, communication
ms.prod: m365-security
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
ms.technology: mde
ms.openlocfilehash: e801776001b79bf1ae3e6e8a220c5e4c395896db
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61941971"
---
# <a name="fix-unhealthy-sensors-in-microsoft-defender-for-endpoint"></a>Corriger les capteurs défectueux dans Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-fixsensor-abovefoldlink)

Les appareils peuvent être classés comme étant mal configurés ou inactifs et signalés pour différentes causes. Cette section fournit des explications sur ce qui peut avoir entraîné la catégorisation d’un appareil comme inactif ou mal configuré.

## <a name="inactive-devices"></a>Appareils inactifs

Un appareil inactif n’est pas nécessairement signalé en raison d’un problème. Les actions suivantes sur un appareil peuvent entraîner la catégorisation d’un appareil comme inactif :

### <a name="device-is-not-in-use"></a>L’appareil n’est pas en cours d’utilisation

Tout appareil qui n’est pas utilisé pendant plus de sept jours conservera l’état « Inactif » dans le portail.

### <a name="device-was-reinstalled-or-renamed"></a>L’appareil a été réinstallé ou renommé
Une nouvelle entité d’appareil est générée dans Microsoft 365 Defender pour les appareils réinstallés ou renommés. L’entité d’appareil précédente reste, avec l’état « Inactif » dans le portail. Si vous avez réinstallé un appareil et déployé le package Defender for Endpoint, recherchez le nouveau nom de l’appareil pour vérifier que l’appareil envoie des rapports normalement.

### <a name="device-was-offboarded"></a>L’appareil a été offboarded
Si l’appareil a été offboarded, il apparaîtra toujours dans la liste des appareils. Au bout de sept jours, l’état d’état de l’appareil doit être inactif.

### <a name="device-is-not-sending-signals"></a>L’appareil n’envoie pas de signaux
Si l’appareil n’envoie aucun signal à des canaux Microsoft Defender pour les points de terminaison pendant plus de sept jours pour une raison quelconque, un appareil peut être considéré comme inactif . Cela inclut les conditions qui relèvent d’une classification d’appareils mal configurée.

Attendez-vous à ce qu’un appareil soit à l’état « Actif » ? [Ouvrez un ticket de support.](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636206786382823561)

## <a name="misconfigured-devices"></a>Appareils mal configurés
Les appareils mal configurés peuvent également être classés sur :
- Communications compromises
- Aucune donnée de capteur

### <a name="impaired-communications"></a>Communications compromises
Cet état indique qu’il existe une communication limitée entre l’appareil et le service.

Les suggestions d’actions suivantes peuvent aider à résoudre les problèmes liés à un appareil mal configuré avec des communications mal configurées :

- [Vérifier que l’appareil dispose d’une connexion Internet](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Le capteur Microsoft Defender pour point de terminaison requiert Microsoft Windows HTTP (WinHTTP) pour signaler les données du capteur et communiquer avec le service Microsoft Defender pour point de terminaison.

- [Vérifier la connectivité du client aux URL du service Microsoft Defender pour les points de terminaison](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Vérifiez que la configuration du proxy s’est correctement terminée, que WinHTTP peut découvrir et communiquer via le serveur proxy dans votre environnement, et que le serveur proxy autorise le trafic vers les URL du service Microsoft Defender for Endpoint.

Si vous avez pris des mesures correctives et que l’état de l’appareil est toujours mal configuré, [ouvrez un ticket de support.](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409)

### <a name="no-sensor-data"></a>Aucune donnée de capteur
Un appareil mal configuré avec l’état « Aucune donnée de capteur » a une communication avec le service, mais ne peut signaler que des données de capteur partielles.

Suivez ces actions pour corriger les problèmes connus liés à un appareil mal configuré avec l’état « Aucune donnée de capteur » :

- [Vérifier que l’appareil dispose d’une connexion Internet](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Le capteur Microsoft Defender pour point de terminaison requiert Microsoft Windows HTTP (WinHTTP) pour signaler les données du capteur et communiquer avec le service Microsoft Defender pour point de terminaison.

- [Vérifier la connectivité du client aux URL du service Microsoft Defender pour les points de terminaison](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Vérifiez que la configuration du proxy s’est correctement terminée, que WinHTTP peut découvrir et communiquer via le serveur proxy dans votre environnement, et que le serveur proxy autorise le trafic vers les URL du service Microsoft Defender for Endpoint.

- [Vérifier que le service de données de diagnostic est activé](troubleshoot-onboarding.md#ensure-the-diagnostics-service-is-enabled)</br>
Si les appareils ne sont pas correctement signalés, vous devez vérifier que le service Windows données de diagnostic est définie pour démarrer automatiquement. Vérifiez également que le service Windows données de diagnostic est en cours d’exécution sur le point de terminaison.

- [S’assurer que Antivirus Microsoft Defender n’est pas désactivé par la stratégie](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)</br>
Si vos appareils exécutent un client de logiciel anti-programme malveillant tiers, l’agent Defender for Endpoint exige que le pilote ELAM (Antivirus Microsoft Defender Early Launch Antimalware) soit activé.

Si vous avez pris des mesures correctives et que l’état de l’appareil est toujours mal configuré, [ouvrez un ticket de support.](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409)

## <a name="see-also"></a>Voir aussi
- [Vérifier l’état d’état du capteur dans Microsoft Defender pour le point de terminaison](check-sensor-status.md)
- [Vue d’ensemble de l’analyseur client](overview-client-analyzer.md)
- [Télécharger et exécuter l’analyseur client](download-client-analyzer.md)
- [Exécuter l’analyseur client sur Windows](run-analyzer-windows.md)
- [Exécuter l’analyseur client sur macOS ou Linux](run-analyzer-macos-linux.md)
- [Collecte de données pour la résolution avancée des problèmes sur Windows](data-collection-analyzer.md)

