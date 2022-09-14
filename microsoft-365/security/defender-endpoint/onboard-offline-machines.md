---
title: Intégrer des appareils sans accès Internet à Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Intégrer des appareils sans accès Internet afin qu’ils puissent envoyer des données de capteur au capteur Microsoft Defender pour point de terminaison
keywords: onboard, servers, vm, on-premises, oms gateway, log analytics, azure log analytics, mma
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
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 4581b3a635fdb37f359d20e547aed1893f794252
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67691956"
---
# <a name="onboard-devices-without-internet-access-to-microsoft-defender-for-endpoint"></a>Intégrer des appareils sans accès Internet à Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Pour les appareils sans connexion Internet directe, l’utilisation d’une solution proxy est l’approche recommandée. Pour les anciens appareils Windows intégrés à l’aide de la solution MMA précédente, l’utilisation de la solution de passerelle OMS offre une autre approche. Pour plus d’informations sur les méthodes d’intégration, consultez les articles suivants :
- [Intégrer des versions antérieures de Windows](/microsoft-365/security/defender-endpoint/onboard-downlevel)
- [Intégrer des serveurs au service Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2008-r2-sp1--windows-server-2012-r2-and-windows-server-2016)

> [!IMPORTANT]
> - Windows ou Windows Server dans des environnements déconnectés doit être en mesure de mettre à jour les listes d’approbation de certificats hors connexion via un fichier interne ou un serveur web.
> - Pour plus d’informations sur la mise à jour des listes CTL hors connexion, consultez [Configurer un fichier ou un serveur web pour télécharger les fichiers CTL](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn265983(v=ws.11)#configure-a-file-or-web-server-to-download-the-ctl-files).

## <a name="devices-running-windows-10-or-later-windows-server-2012-r2-or-later-linux-and-macos"></a>Appareils exécutant Windows 10 ou version ultérieure, Windows Server 2012 R2 ou version ultérieure, Linux et macOS

Selon le système d’exploitation, le proxy à utiliser pour Microsoft Defender pour point de terminaison peut être configuré automatiquement, généralement à l’aide de la découverte automatique ou d’un fichier de configuration automatique, ou statiquement spécifique aux services Defender pour point de terminaison exécutés sur l’appareil.

- Pour les appareils Windows, consultez [Configurer le proxy d’appareil et les paramètres de connectivité Internet](/microsoft-365/security/defender-endpoint/configure-proxy-internet)
- Pour les appareils Linux, consultez [Configurer Microsoft Defender pour point de terminaison sur Linux pour la découverte de proxy statique](/microsoft-365/security/defender-endpoint/linux-static-proxy-configuration)
- Pour les appareils macOS, veuillez référencer [Microsoft Defender pour point de terminaison sur Mac](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac#network-connections)

## <a name="windows-devices-running-the-previous-mma-based-solution"></a>Appareils Windows exécutant la solution MMA précédente

> [!NOTE]
> - Un serveur de passerelle OMS ne peut pas être utilisé comme proxy pour les appareils Windows ou Windows Server déconnectés lorsqu’il est configuré via le registre « TelemetryProxyServer » ou l’objet de stratégie de groupe.
> - Pour Windows ou Windows Server , bien que vous puissiez utiliser TelemetryProxyServer, il doit pointer vers un appareil proxy standard ou une appliance.

- Configurez Azure Log Analytics (anciennement passerelle OMS) pour agir en tant que proxy ou hub :
  - [Azure Log Analytics Agent](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
  - [Installer et configurer Microsoft Monitoring Agent (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) pointent vers la clé de l’espace de travail Defender pour point de terminaison & ID

[Intégrer des versions antérieures de Windows](onboard-downlevel.md)

### <a name="azure-virtual-machines"></a>Machines virtuelles Azure

- Pour les appareils exécutant la solution MMA précédente, configurez la passerelle Azure Log Analytics (anciennement passerelle OMS) pour agir en tant que proxy ou hub :
    - [Passerelle Azure Log Analytics](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
    - [Installer et configurer Microsoft Monitoring Agent (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) pointent vers la clé de l’espace de travail Defender pour point de terminaison & ID
- Machines virtuelles Azure hors connexion dans le même réseau de passerelle OMS
    - Configurer l’adresse IP Azure Log Analytics en tant que proxy
    - ID & clé de l’espace de travail Azure Log Analytics
- Microsoft Defender pour le cloud
    - [Espace de travail Log Analytics de la stratégie \> de sécurité](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)
    - [Détection des menaces \> Autoriser Defender pour point de terminaison à accéder à mes données](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)

    Pour plus d’informations, consultez [Utilisation des stratégies de sécurité](/azure/security-center/tutorial-security-policy).

> [!NOTE]
> Tout client qui n’a pas accès à Internet ne peut pas être intégré au point de terminaison Microsoft Defender. Un client doit avoir accès directement aux URL requises, ou il doit avoir accès via un proxy.
