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
ms.date: 05/14/2021
ms.custom: migrationguides
ms.reviewer: depicker, yongrhee, chriggs
ms.openlocfilehash: 7fe0eb8adc90c259d31f237082effc80c5e8622c
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52537978"
---
# <a name="migrate-from-symantec---phase-1-prepare-for-your-migration"></a>Migrer à partir de Symantec - Phase 1 : Préparer votre migration

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|![Phase 1 : préparation](images/phase-diagrams/prepare.png)<br/>Phase 1 : préparation |[![Phase 2 : configuration](images/phase-diagrams/setup.png)](symantec-to-microsoft-defender-atp-setup.md)<br/>[Phase 2 : configuration](symantec-to-microsoft-defender-atp-setup.md) |[![Phase 3 : intégration](images/phase-diagrams/onboard.png)](symantec-to-microsoft-defender-atp-onboard.md)<br/>[Phase 3 : intégration](symantec-to-microsoft-defender-atp-onboard.md) |
|--|--|--|
|*Vous êtes là !*| | |


**Bienvenue dans la phase de préparation [de la migration de Symantec vers Defender pour point de terminaison.](symantec-to-microsoft-defender-endpoint-migration.md#the-migration-process)** 

Cette phase de migration comprend les étapes suivantes :

1. [Mettez à jour les appareils de votre organisation.](#update-your-organizations-devices)

2. [Obtenir Microsoft Defender pour le point de terminaison.](#get-microsoft-defender-for-endpoint)

3. [Accorder l’accès au Centre de sécurité Microsoft Defender](#grant-access-to-the-microsoft-defender-security-center).

4. [Configurer les paramètres de proxy d’appareil et de connectivité Internet](#configure-device-proxy-and-internet-connectivity-settings)

## <a name="update-your-organizations-devices"></a>Mettre à jour les appareils de votre organisation

En tant que meilleure pratique, maintenez à jour les appareils et points de terminaison de votre organisation. Assurez-vous que votre solution antivirus et de protection de point de terminaison existante est à jour et que les systèmes d’exploitation et les applications de votre organisation ont également les dernières mises à jour. Cela permet d’éviter les problèmes ultérieurement lors de la migration vers Defender pour Endpoint.

### <a name="make-sure-symantec-is-up-to-date"></a>Assurez-vous que Symantec est à jour

Maintenez votre solution de protection de point de terminaison existante à jour et assurez-vous que les appareils de votre organisation ont les dernières mises à jour de sécurité.

Besoin d’aide ? Voir la documentation de Broadcom : [Guide d’installation et d’administration](https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-protection/all.html) de Symantec Endpoint Protection

### <a name="make-sure-your-endpoints-are-up-to-date"></a>Assurez-vous que vos points de terminaison sont à jour

Vous avez besoin d’aide pour mettre à jour les appareils de votre organisation ? Consultez les ressources suivantes :


|SYSTÈME D’EXPLOITATION  |Resource  |
|---------|---------|
|Windows     | [Microsoft Update](https://www.update.microsoft.com/)        |
|macOS     | [Comment mettre à jour le logiciel sur votre Mac](https://support.apple.com/HT201541)         |
|iOS     | [Mettre à jour iPhone, iPad ou iPod touch](https://support.apple.com/HT204204)         |
|Android     | [Vérifier & mise à jour de votre version Android](https://support.google.com/android/answer/7680439)        |
|Linux     | [Linux 101 : mise à jour de votre système](https://www.linux.com/training-tutorials/linux-101-updating-your-system)        |


## <a name="get-microsoft-defender-for-endpoint"></a>Obtenir Microsoft Defender pour le point de terminaison

Maintenant que vous avez mis à jour les appareils de votre organisation, l’étape suivante consiste à obtenir Defender pour le point de terminaison, à attribuer des licences et à vous assurer que le service est mis en service.

1. Achetez ou essayez Defender pour Point de terminaison dès aujourd’hui. [Visitez Defender pour le point de terminaison pour démarrer une version d’évaluation gratuite ou demander un devis.](https://aka.ms/mdatp) 

2. Vérifiez que vos licences sont correctement provisionées. [Vérifiez l’état de votre licence.](production-deployment.md#check-license-state)

3. En tant qu’administrateur général ou administrateur de sécurité, vous pouvez configurer votre instance cloud dédiée de Defender for Endpoint. Voir [Configuration de Defender pour le point de terminaison : configuration du client.](production-deployment.md#tenant-configuration)

4. Si les points de terminaison (tels que les appareils) de votre organisation utilisent un proxy pour accéder à Internet, voir Defender pour l’installation du point de [terminaison](production-deployment.md#network-configuration): configuration réseau .
 
À ce stade, vous êtes prêt à accorder l’accès à vos administrateurs de sécurité et opérateurs de sécurité qui utiliseront le Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ). 

> [!NOTE]
> Le Centre de sécurité Microsoft Defender est parfois appelé le portail Defender pour point de terminaison. 

## <a name="grant-access-to-the-microsoft-defender-security-center"></a>Accorder l’accès au Centre de sécurité Microsoft Defender

Le Centre de sécurité Microsoft Defender ( ) est l’endroit où vous accédez aux fonctionnalités et aux fonctionnalités de Defender for Endpoint et les [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) configurez. Pour plus d’informations, voir [Vue d’ensemble Centre de sécurité Microsoft Defender](use.md).

Les autorisations sur le Centre de sécurité Microsoft Defender peuvent être accordées à l’aide d’autorisations de base ou d’un contrôle d’accès basé sur un rôle (RBAC). Nous vous recommandons d’utiliser RBAC afin de contrôler plus granulairement les autorisations.

1. Planifiez les rôles et les autorisations de vos administrateurs de sécurité et opérateurs de sécurité. Voir [Contrôle d’accès basé sur un rôle.](prepare-deployment.md#role-based-access-control)

2. Configurez et configurez le RBAC. Nous vous recommandons d’utiliser [Intune](/mem/intune/fundamentals/what-is-intune) pour configurer le RBAC, en particulier si votre organisation utilise une combinaison d’appareils Windows 10, macOS, iOS et Android. Voir [la configuration du RBAC à l’aide d’Intune.](/mem/intune/fundamentals/role-based-access-control)

   Si votre organisation nécessite une méthode autre qu’Intune, choisissez l’une des options suivantes :

    - [Gestionnaire de configuration](/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)

    - [Gestion avancée des stratégies de groupe](/microsoft-desktop-optimization-pack/agpm)

    - [Windows Centre d’administration](/windows-server/manage/windows-admin-center/overview)

3. Accorder l’accès au Centre de sécurité Microsoft Defender. (Vous avez besoin d’aide ? Voir [Gérer l’accès au portail à l’aide de RBAC](rbac.md)).

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Configurer les paramètres de proxy d’appareil et de connectivité Internet

Pour activer la communication entre vos appareils et Defender pour le point de terminaison, configurez les paramètres proxy et Internet. Le tableau suivant inclut des liens vers des ressources que vous pouvez utiliser pour configurer vos paramètres proxy et Internet pour différents systèmes d’exploitation et fonctionnalités :

|Fonctionnalités  | Système d’exploitation | Ressources |
|:----|:----|:---|
|[Détection et réponse des points](overview-endpoint-detection-response.md) de terminaison (PEPT) | [Windows 10](/windows/release-health/release-information/) <p> [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<p>[Windows Serveur 1803 ou ultérieur](/windows-server/get-started/whats-new-in-windows-server-1803)  |[Configurer les paramètres de connectivité Internet et proxy de l’ordinateur](configure-proxy-internet.md) |
|PEPT | [Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016) <p>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<p>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<p>[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<p>[Windows 7 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |[Configurer les paramètres de proxy et de connectivité Internet](onboard-downlevel.md#configure-proxy-and-internet-connectivity-settings) |
|PEPT  |macOS : <p>11.3.1 (Big Sur)<p>10.15 (Îles)<p>10.14 (Mojave) |[Defender pour le point de terminaison sur macOS : connexions réseau](microsoft-defender-endpoint-mac.md#network-connections) |
|[Antivirus Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md) |[Windows 10](/windows/release-health/release-information/)<p>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<p>[Windows Serveur 1803 ou ultérieur](/windows-server/get-started/whats-new-in-windows-server-1803)<p>[Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016) |[Configurer et valider les connexions réseau à un antivirus Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md) |
|Antivirus |macOS : <p>11.3.1 (Big Sur)<p>10.15 (Îles)<p>10.14 (Mojave)  |[Defender pour le point de terminaison sur Mac : connexions réseau](microsoft-defender-endpoint-mac.md#network-connections) |
|Antivirus |Linux : <p>RHEL 7.2+<p>CentOS Linux 7.2+<p>Ubuntu 16 LTS ou un LTS supérieur<p>SLES 12+<p>Debian 9+<p>Oracle Linux 7.2 |[Defender pour point de terminaison sur Linux : connexions réseau](microsoft-defender-endpoint-linux.md#network-connections)  |

## <a name="next-step"></a>Étape suivante

**Félicitations**! Vous avez terminé la phase **de** préparation de [la migration de Symantec vers Defender pour Endpoint](symantec-to-microsoft-defender-endpoint-migration.md#the-migration-process)!
- [Procédez à la mise en place de Defender pour Endpoint](symantec-to-microsoft-defender-atp-setup.md).
