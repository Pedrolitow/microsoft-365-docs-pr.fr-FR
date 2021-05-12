---
title: Symantec vers Microsoft Defender pour le point de terminaison - Phase 1, Préparation
description: Il s’agit de la phase 1, Préparation, de la migration de Symantec vers Microsoft Defender pour Endpoint.
keywords: migration, Microsoft Defender pour point de terminaison, edr
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-symantecmigrate
ms.topic: article
ms.date: 03/03/2021
ms.custom: migrationguides
ms.reviewer: depicker, yongrhee, chriggs
ms.openlocfilehash: bba48803863cd330b371c24600239462b1ca9250
ms.sourcegitcommit: 68383240ef7a673d5f28e2ecfab9f105bf1d8c8f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "52327413"
---
# <a name="migrate-from-symantec---phase-1-prepare-for-your-migration"></a>Migrer à partir de Symantec - Phase 1 : Préparer votre migration

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|![Phase 1 : préparation](images/phase-diagrams/prepare.png)<br/>Phase 1 : préparation |[![Phase 2 : configuration](images/phase-diagrams/setup.png)](symantec-to-microsoft-defender-atp-setup.md)<br/>[Phase 2 : configuration](symantec-to-microsoft-defender-atp-setup.md) |[![Phase 3 : intégration](images/phase-diagrams/onboard.png)](symantec-to-microsoft-defender-atp-onboard.md)<br/>[Phase 3 : intégration](symantec-to-microsoft-defender-atp-onboard.md) |
|--|--|--|
|*Vous êtes là !*| | |


**Bienvenue dans la phase de préparation [de la migration de Symantec vers Microsoft Defender pour point de terminaison.](symantec-to-microsoft-defender-endpoint-migration.md#the-migration-process)** 

Cette phase de migration comprend les étapes suivantes :
1. [Obtenir Microsoft Defender pour le point de terminaison.](#get-microsoft-defender-for-endpoint)
2. [Accorder l’accès au Centre de sécurité Microsoft Defender.](#grant-access-to-the-microsoft-defender-security-center)
3. [Configurer les paramètres de proxy et de connectivité Internet de l’appareil.](#configure-device-proxy-and-internet-connectivity-settings)

## <a name="get-microsoft-defender-for-endpoint"></a>Obtenir Microsoft Defender pour le point de terminaison

Pour commencer, vous devez avoir Microsoft Defender pour point de terminaison, avec des licences attribuées et provisionées.

1. Achetez ou essayez Microsoft Defender pour Endpoint dès aujourd’hui. [Visitez Microsoft Defender for Endpoint pour démarrer une version d’évaluation gratuite ou demander un devis.](https://aka.ms/mdatp) 
2. Vérifiez que vos licences sont correctement provisionées. [Vérifiez l’état de votre licence.](production-deployment.md#check-license-state)
3. En tant qu’administrateur général ou administrateur de sécurité, vous pouvez configurer votre instance cloud dédiée de Microsoft Defender pour Endpoint. Voir [Configuration de Microsoft Defender pour endpoint : configuration du client.](production-deployment.md#tenant-configuration)
4. Si les points de terminaison (tels que les appareils) de votre organisation utilisent un proxy pour accéder à Internet, voir Microsoft Defender pour l’installation du point de [terminaison](production-deployment.md#network-configuration): configuration réseau .
 
À ce stade, vous êtes prêt à accorder l’accès à vos administrateurs de sécurité et opérateurs de sécurité qui utiliseront le Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ). 

> [!NOTE]
> Le Centre de sécurité Microsoft Defender est parfois appelé portail Microsoft Defender pour points de terminaison. 

## <a name="grant-access-to-the-microsoft-defender-security-center"></a>Accorder l’accès au Centre de sécurité Microsoft Defender

Le Centre de sécurité Microsoft Defender ( ) est l’endroit où vous accédez et configurez les fonctionnalités et fonctionnalités de [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) Microsoft Defender pour point de terminaison. Pour plus d’informations, voir [Vue d’ensemble du Centre de sécurité Microsoft Defender.](use.md)

Les autorisations sur le Centre de sécurité Microsoft Defender peuvent être accordées à l’aide d’autorisations de base ou d’un contrôle d’accès basé sur un rôle (RBAC). Nous vous recommandons d’utiliser RBAC afin de contrôler plus granulairement les autorisations.

1. Planifiez les rôles et les autorisations de vos administrateurs de sécurité et opérateurs de sécurité. Voir [Contrôle d’accès basé sur un rôle.](prepare-deployment.md#role-based-access-control)
2. Configurez et configurez le RBAC. Nous vous recommandons d’utiliser [Intune](/mem/intune/fundamentals/what-is-intune) pour configurer le RBAC, en particulier si votre organisation utilise une combinaison d’appareils Windows 10, macOS, iOS et Android. Voir [la configuration du RBAC à l’aide d’Intune.](/mem/intune/fundamentals/role-based-access-control)<br/>
   Si votre organisation nécessite une méthode autre qu’Intune, choisissez l’une des options suivantes :
    - [Gestionnaire de configuration](/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)
    - [Gestion avancée des stratégies de groupe](/microsoft-desktop-optimization-pack/agpm)
    - [Windows Admin Center](/windows-server/manage/windows-admin-center/overview)
3. Accorder l’accès au Centre de sécurité Microsoft Defender. (Vous avez besoin d’aide ? Voir [Gérer l’accès au portail à l’aide de RBAC](rbac.md)).

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Configurer les paramètres de proxy d’appareil et de connectivité Internet

Pour activer la communication entre vos appareils et Microsoft Defender pour le point de terminaison, configurez les paramètres proxy et Internet. Le tableau suivant inclut des liens vers des ressources que vous pouvez utiliser pour configurer vos paramètres proxy et Internet pour différents systèmes d’exploitation et fonctionnalités :

|Fonctionnalités  | Système d’exploitation | Ressources |
|:----|:----|:---|
|[Détection et réponse des points de terminaison](overview-endpoint-detection-response.md) (EDR) |- [Windows 10](/windows/release-health/release-information/) <br/>- [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/>- [Windows Server 1803 ou une ultérieure](/windows-server/get-started/whats-new-in-windows-server-1803)  |[Configurer les paramètres de connectivité Internet et proxy de l’ordinateur](configure-proxy-internet.md) |
|EDR |- [Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016) <br/>- [Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/>- [Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/>- [Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/>- [Windows 7 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |[Configurer les paramètres de proxy et de connectivité Internet](onboard-downlevel.md#configure-proxy-and-internet-connectivity-settings) |
|EDR  |macOS : <br/>- 10.15 (Îles)<br/>- 10.14 (Mojave) <br/>- 10.13 (High Sierra)  |[Microsoft Defender pour point de terminaison sur macOS : connexions réseau](microsoft-defender-endpoint-mac.md#network-connections) |
|[Antivirus Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md) |- [Windows 10](/windows/release-health/release-information/) <br/>- [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/>- [Windows Server 1803 ou une ultérieure](/windows-server/get-started/whats-new-in-windows-server-1803) <br/>- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016) |[Configurer et valider les connexions réseau à un antivirus Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md)<br/> |
|Antivirus |macOS : <br/>- 11.3.1 (Big Sur)<br/>- 10.15 (Îles)<br/>- 10.14 (Mojave)  |[Microsoft Defender pour point de terminaison sur Mac : connexions réseau](microsoft-defender-endpoint-mac.md#network-connections) |
|Antivirus |Linux : <br/>- RHEL 7.2+<br/>- CentOS Linux 7.2+<br/>- Ubuntu 16 LTS ou un LTS supérieur<br/>- SLES 12+<br/>- Debian 9+<br/>- Oracle Linux 7.2 |[Microsoft Defender pour point de terminaison sur Linux : connexions réseau](microsoft-defender-endpoint-linux.md#network-connections)  |

## <a name="next-step"></a>Étape suivante

**Félicitations**! Vous avez terminé la phase **de** préparation [de la migration de Symantec vers Microsoft Defender pour endpoint](symantec-to-microsoft-defender-endpoint-migration.md#the-migration-process)!
- [Procédez à la mise en place de Microsoft Defender pour endpoint.](symantec-to-microsoft-defender-atp-setup.md)
