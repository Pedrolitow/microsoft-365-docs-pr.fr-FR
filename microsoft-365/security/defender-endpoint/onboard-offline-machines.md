---
title: Appareils intégrés sans accès à Internet à Microsoft Defender pour le point de terminaison
ms.reviewer: ''
description: Intégrer des appareils sans accès à Internet afin qu’ils peuvent envoyer des données de capteur au capteur Microsoft Defender for Endpoint
keywords: onboard, servers, vm, on-premises, oms gateway, log analytics, azure log analytics, mma
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
ms.technology: mde
ms.openlocfilehash: e5f76505191b552450440917bf616f7678464524
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61110450"
---
# <a name="onboard-devices-without-internet-access-to-microsoft-defender-for-endpoint"></a>Appareils intégrés sans accès à Internet à Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Pour intégrer des appareils sans accès à Internet, vous devez suivre les étapes générales suivantes :

> [!IMPORTANT] 
> Les étapes ci-dessous s’appliquent uniquement aux appareils exécutant des versions antérieures de Windows tels que : Windows Server 2016 et versions antérieures ou antérieures ou Windows 8.1 et versions antérieures.

> [!NOTE]
> - Un serveur de passerelle OMS ne peut pas être utilisé comme proxy pour les périphériques Windows ou Windows Server déconnectés lorsqu’il est configuré via le Registre ou l’GPO « TelemetryProxyServer ».
> - Pour Windows ou Windows Server : alors que vous pouvez utiliser TelemetryProxyServer, il doit pointer vers un périphérique proxy ou une appliance standard.
> - En outre, Windows serveur Windows dans les environnements déconnectés doit être en mesure de mettre à jour les listes d’autorisation de certificat hors connexion via un fichier interne ou un serveur web.
> - Pour plus d’informations sur la mise à jour des fichiers CTL hors connexion, voir Configurer un fichier ou un serveur web pour [télécharger les fichiers CTL.](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn265983(v=ws.11)#configure-a-file-or-web-server-to-download-the-ctl-files)

Pour plus d’informations sur les méthodes d’intégration, consultez les articles suivants :
- [Intégrer des versions antérieures de Windows](/microsoft-365/security/defender-endpoint/onboard-downlevel)
- [Intégrer des serveurs au service Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2008-r2-sp1--windows-server-2012-r2-and-windows-server-2016)
- [Configurer les paramètres de proxy du dispositif et de connectivité Internet](/microsoft-365/security/defender-endpoint/configure-proxy-internet#configure-the-proxy-server-manually-using-a-registry-based-static-proxy)

## <a name="on-premises-devices"></a>Appareils locaux

- Configurer Azure Log Analytics (anciennement appelé passerelle OMS) pour qu’il agisse en tant que proxy ou hub :
  - [Azure Log Analytics Agent](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
  - [Installer et configurer un point Microsoft Monitoring Agent (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) vers la clé d’espace de travail Defender for Endpoint & ID

[Intégrer des versions antérieures de Windows](onboard-downlevel.md)

- Appareils hors connexion dans le même réseau d’Azure Log Analytics
  - Configurez MMA pour qu’il pointe vers :
    - Adresse IP Azure Log Analytics en tant que proxy
    - Clé d’espace de travail Defender for Endpoint & ID

## <a name="azure-virtual-machines"></a>Machines virtuelles Azure

- Configurer Azure Log Analytics Gateway (anciennement passerelle OMS) pour qu’elle agisse en tant que proxy ou hub :
    - [Passerelle Azure Log Analytics](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
    - [Installer et configurer un point Microsoft Monitoring Agent (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) vers la clé d’espace de travail Defender for Endpoint & ID
- Ordinateurs VM Azure hors connexion dans le même réseau de passerelle OMS
    - Configurer l’adresse IP Azure Log Analytics en tant que proxy
    - ID de clé d’espace de travail Azure Log Analytics & ID
- Microsoft Defender pour le cloud
    - [Espace de travail \> Analyse des journaux de stratégie de sécurité](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)
    - [Détection des \> menaces : autoriser Defender pour le point de terminaison à accéder à mes données](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)

    Pour plus d’informations, voir [Working with security policies](/azure/security-center/tutorial-security-policy).
