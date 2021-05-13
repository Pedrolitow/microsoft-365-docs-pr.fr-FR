---
title: Basculer vers Microsoft Defender pour le point de terminaison - Préparer
description: Il s’agit de la phase 1, Préparer, pour la migration vers Microsoft Defender pour point de terminaison.
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
- m365solution-migratetomdatp
ms.topic: article
ms.custom: migrationguides
ms.date: 05/11/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 265f32f5a24b982933ac6a876b244b10802cdd60
ms.sourcegitcommit: 94e64afaf12f3d8813099d8ffa46baba65772763
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52345811"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-1-prepare"></a>Basculer vers Microsoft Defender pour le point de terminaison - Phase 1 : Préparer

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| ![Phase 1 : préparation](images/phase-diagrams/prepare.png)<br/>Phase 1 : préparation | [![Phase 2 : configuration](images/phase-diagrams/setup.png)](switch-to-microsoft-defender-setup.md)<br/>[Phase 2 : configuration](switch-to-microsoft-defender-setup.md) | [![Phase 3 : intégration](images/phase-diagrams/onboard.png)](switch-to-microsoft-defender-onboard.md)<br/>[Phase 3 : intégration](switch-to-microsoft-defender-onboard.md) |
|--|--|--|
|*Vous êtes là !*| | |

**Bienvenue dans la phase de préparation [du basculement vers Microsoft Defender pour le point de terminaison.](switch-to-microsoft-defender-migration.md#the-migration-process)** 

Cette phase de migration comprend les étapes suivantes :

1. [Obtenir et déployer des mises à jour sur les appareils de votre organisation](#get-and-deploy-updates-across-your-organizations-devices)

2. [Obtenir Microsoft Defender pour le point de terminaison.](#get-microsoft-defender-for-endpoint)

3. [Accorder l’accès au Centre de sécurité Microsoft Defender](#grant-access-to-the-microsoft-defender-security-center).

4. [Configurer les paramètres de proxy et de connectivité Internet de l’appareil.](#configure-device-proxy-and-internet-connectivity-settings)

## <a name="get-and-deploy-updates-across-your-organizations-devices"></a>Obtenir et déployer des mises à jour sur les appareils de votre organisation

Il est préférable de maintenir à jour les appareils et points de terminaison de votre organisation. Assurez-vous que votre solution antivirus et de protection de point de terminaison existante est à jour et que les systèmes d’exploitation et les applications de votre organisation ont également les dernières mises à jour. Cela permet d’éviter les problèmes plus tard lors de la migration vers Microsoft Defender pour endpoint et Antivirus Microsoft Defender.

### <a name="make-sure-your-existing-solution-is-up-to-date"></a>Assurez-vous que votre solution existante est à jour

Maintenez votre solution de protection de point de terminaison existante à jour et assurez-vous que les appareils de votre organisation ont les dernières mises à jour de sécurité. 

Besoin d’aide ? Consultez la documentation de votre fournisseur de solutions.

### <a name="make-sure-your-organizations-devices-are-up-to-date"></a>Assurez-vous que les appareils de votre organisation sont à jour

Vous avez besoin d’aide pour mettre à jour les appareils de votre organisation ? Consultez les ressources suivantes :

|SYSTÈME D’EXPLOITATION | Resource |
|:--|:--|
|Windows |[Microsoft Update](https://www.update.microsoft.com) |
|macOS | [Comment mettre à jour le logiciel sur votre Mac](https://support.apple.com/HT201541)|
|iOS |[Mettre à jour iPhone, iPad ou iPod touch](https://support.apple.com/HT204204)|
|Android |[Vérifier & mettre à jour votre version Android](https://support.google.com/android/answer/7680439) |
|Linux | [Linux 101 : mise à jour de votre système](https://www.linux.com/training-tutorials/linux-101-updating-your-system) |

## <a name="get-microsoft-defender-for-endpoint"></a>Obtenir Microsoft Defender pour le point de terminaison

Maintenant que vous avez mis à jour les appareils de votre organisation, l’étape suivante consiste à obtenir Microsoft Defender pour le point de terminaison, à attribuer des licences et à vous assurer que le service est mis en service.

1. Achetez ou essayez Microsoft Defender pour Endpoint dès aujourd’hui. [Démarrez une version d’essai gratuite ou demandez un devis.](https://aka.ms/mdatp) 

2. Vérifiez que vos licences sont correctement provisionées. [Vérifiez l’état de votre licence.](production-deployment.md#check-license-state)

3. En tant qu’administrateur général ou administrateur de sécurité, vous pouvez configurer votre instance cloud dédiée de Microsoft Defender pour Endpoint. Voir [Configuration de Microsoft Defender pour endpoint : configuration du client.](production-deployment.md#tenant-configuration)

4. Si les points de terminaison (tels que les appareils) de votre organisation utilisent un proxy pour accéder à Internet, voir Microsoft Defender pour l’installation du point de [terminaison](production-deployment.md#network-configuration): configuration réseau .
 
À ce stade, vous êtes prêt à accorder l’accès à vos administrateurs de sécurité et opérateurs de sécurité qui utiliseront le Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ). 

> [!NOTE]
> Le Centre de sécurité Microsoft Defender est parfois appelé portail Microsoft Defender pour points de terminaison et est accessible à l':. [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) 

## <a name="grant-access-to-the-microsoft-defender-security-center"></a>Accorder l’accès au Centre de sécurité Microsoft Defender

Le Centre de sécurité Microsoft Defender ( ) est l’endroit où vous accédez et configurez les fonctionnalités et fonctionnalités de [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) Microsoft Defender pour point de terminaison. Pour plus d’informations, voir [Vue d’ensemble Centre de sécurité Microsoft Defender](use.md).

Les autorisations sur le Centre de sécurité Microsoft Defender peuvent être accordées à l’aide d’autorisations de base ou d’un contrôle d’accès basé sur un rôle (RBAC). Nous vous recommandons d’utiliser RBAC afin de contrôler plus granulairement les autorisations.

1. Planifiez les rôles et les autorisations de vos administrateurs de sécurité et opérateurs de sécurité. Voir [Contrôle d’accès basé sur un rôle.](prepare-deployment.md#role-based-access-control)

2. Configurez et configurez le RBAC. Nous vous recommandons d’utiliser [Intune](/mem/intune/fundamentals/what-is-intune) pour configurer le RBAC, en particulier si votre organisation utilise une combinaison d’appareils Windows 10, macOS, iOS et Android. Voir [la configuration du RBAC à l’aide d’Intune.](/mem/intune/fundamentals/role-based-access-control)

    Si votre organisation nécessite une méthode autre qu’Intune, choisissez l’une des options suivantes :

    - [Gestionnaire de configuration](/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)

    - [Gestion avancée des stratégies de groupe](/microsoft-desktop-optimization-pack/agpm)

    - [Windows Centre d’administration](/windows-server/manage/windows-admin-center/overview)

3. Accorder l’accès au Centre de sécurité Microsoft Defender. (Vous avez besoin d’aide ? Voir [Gérer l’accès au portail à l’aide de RBAC](rbac.md)).

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Configurer les paramètres de proxy d’appareil et de connectivité Internet

Pour activer la communication entre vos appareils et Microsoft Defender pour le point de terminaison, configurez les paramètres proxy et Internet. Le tableau suivant inclut des liens vers des ressources que vous pouvez utiliser pour configurer vos paramètres proxy et Internet pour différents systèmes d’exploitation et fonctionnalités :

|Fonctionnalités  | Système d’exploitation | Ressources |
|--|--|--|
|[Détection et réponse des points](overview-endpoint-detection-response.md) de terminaison (PEPT) |[Windows 10](/windows/release-health/release-information) <p>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<p>[Windows Serveur 1803 ou ultérieur](/windows-server/get-started/whats-new-in-windows-server-1803)  |[Configurer les paramètres de connectivité Internet et proxy de l’ordinateur](configure-proxy-internet.md) |
|PEPT |[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016) <p>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<p>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<p>[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<p>[Windows 7 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |[Configurer les paramètres de proxy et de connectivité Internet](onboard-downlevel.md#configure-proxy-and-internet-connectivity-settings) |
|PEPT  |macOS : <br/>- 11.3.1 (Big Sur)<br/>- 10.15 (Îles)<br/>- 10.14 (Mojave)   |[Microsoft Defender pour point de terminaison sur macOS : connexions réseau](microsoft-defender-endpoint-mac.md#network-connections)  |
|[Antivirus Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md) |[Windows 10](/windows/release-health/release-information) <p>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<p>[Windows Serveur 1803 ou ultérieur](/windows-server/get-started/whats-new-in-windows-server-1803) <p>[Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016) |[Configurer et valider les connexions réseau à un antivirus Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md)<br/> |
|Antivirus |macOS : <br/>- 11.3.1 (Big Sur)<br/>- 10.15 (Îles)<br/>- 10.14 (Mojave) |[Microsoft Defender pour point de terminaison sur macOS : connexions réseau](microsoft-defender-endpoint-mac.md#network-connections) |
|Antivirus |Linux : <br/>- RHEL 7.2+<br/>- CentOS Linux 7.2+<br/>- Ubuntu 16 LTS ou un LTS supérieur<br/>- SLES 12+<br/>- Debian 9+<br/>- Oracle Linux 7.2 |[Microsoft Defender pour point de terminaison sur Linux : connexions réseau](microsoft-defender-endpoint-linux.md#network-connections) |

## <a name="next-step"></a>Étape suivante

**Félicitations**! Vous avez terminé la phase **de** préparation [du basculement vers Microsoft Defender pour le point de terminaison](switch-to-microsoft-defender-migration.md#the-migration-process)!

- [Procédez à la mise en place de Microsoft Defender pour endpoint.](switch-to-microsoft-defender-setup.md)
