---
title: Mc Antivirus vers Microsoft Defender pour le point de terminaison - Préparer
description: Il s’agit de la phase 1, Préparer, pour la migration de Mc Antivirus vers Microsoft Defender ATP.
keywords: migration, protection avancée contre les menaces Windows Defender, atp, edr
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
- m365solution-mcafeemigrate
- m365solution-scenario
ms.topic: article
ms.custom: migrationguides
ms.date: 03/03/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: adc8c1259be1e226bf1c2592090cf6008c976cf8
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51186628"
---
# <a name="migrate-from-mcafee---phase-1-prepare-for-your-migration"></a>Migrer à partir de Mc Antivirus - Phase 1 : Préparer votre migration

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|![Phase 1 : Préparer](images/phase-diagrams/prepare.png)<br/>Phase 1 : Préparer |[![Phase 2 : Configurer](images/phase-diagrams/setup.png)](mcafee-to-microsoft-defender-setup.md)<br/>[Phase 2 : Configurer](mcafee-to-microsoft-defender-setup.md) |[![Phase 3 : Intégration](images/phase-diagrams/onboard.png)](mcafee-to-microsoft-defender-onboard.md)<br/>[Phase 3 : Intégration](mcafee-to-microsoft-defender-onboard.md) |
|--|--|--|
|*Vous êtes là !*| | |


Bienvenue dans la phase de préparation de la migration de **[Mc Antivirus Endpoint Security (Mc Antivirus) vers Microsoft Defender for Endpoint](mcafee-to-microsoft-defender-migration.md#the-migration-process)**. 

Cette phase de migration comprend les étapes suivantes :
1. [Obtenir et déployer des mises à jour sur les appareils de votre organisation](#get-and-deploy-updates-across-your-organizations-devices)
2. [Obtenir Microsoft Defender pour le point de terminaison.](#get-microsoft-defender-for-endpoint)
3. [Accorder l’accès au Centre de sécurité Microsoft Defender.](#grant-access-to-the-microsoft-defender-security-center)
4. [Configurez les paramètres de proxy et de connectivité Internet de l’appareil.](#configure-device-proxy-and-internet-connectivity-settings)

## <a name="get-and-deploy-updates-across-your-organizations-devices"></a>Obtenir et déployer des mises à jour sur les appareils de votre organisation

En tant que meilleure pratique, maintenez à jour les appareils et points de terminaison de votre organisation. Assurez-vous que votre solution Mc Antivirus Endpoint Security (Mc Antivirus) est à jour et que les systèmes d’exploitation et les applications de votre organisation ont également les dernières mises à jour. Cette action permet d’éviter les problèmes ultérieurement lors de la migration vers Microsoft Defender pour Endpoint et l’Antivirus Microsoft Defender.

### <a name="make-sure-your-mcafee-solution-is-up-to-date"></a>Assurez-vous que votre solution Mc Antivirus est à jour

Maintenez Mc Antivirus à jour et assurez-vous que les appareils de votre organisation ont les dernières mises à jour de sécurité. Vous avez besoin d’aide ? Voici quelques ressources Mc Antivirus :

- [Documentation sur les produits Mc Antivirus Enterprise : fonctionnement de la sécurité des points de terminaison](https://docs.mcafee.com/bundle/endpoint-security-10.7.x-common-product-guide-windows/page/GUID-1207FF39-D1D2-481F-BBD9-E4079112A8DD.html)

- [Article technique du Centre de connaissances Mc Antivirus : Le Centre de sécurité Windows signale par intermittence que la sécurité des points de terminaison est désactivée lors de l’exécution sur Windows 10](https://kc.mcafee.com/corporate/index?page=content&id=KB91830) 

- [Article technique du Centre de connaissances Mc Antivirus : Le Centre de sécurité Windows signale que la sécurité des points de terminaison est désactivée lorsque endpoint Security est en cours d’exécution](https://kc.mcafee.com/corporate/index?page=content&id=KB91428)

- Votre Mc Antivirus prise en charge ServicePortal ( [http://mysupport.mcafee.com](http://mysupport.mcafee.com) )

### <a name="make-sure-your-organizations-devices-are-up-to-date"></a>Assurez-vous que les appareils de votre organisation sont à jour

Vous avez besoin d’aide pour mettre à jour les appareils de votre organisation ? Consultez les ressources suivantes :

|SYSTÈME D’EXPLOITATION | Ressource |
|:--|:--|
|Windows |[Microsoft Update](https://www.update.microsoft.com) |
|macOS | [Comment mettre à jour le logiciel sur votre Mac](https://support.apple.com/HT201541)|
|iOS |[Mettre à jour votre iPhone, iPad ou iPod touch](https://support.apple.com/HT204204)|
|Android |[Vérifier & mettre à jour votre version Android](https://support.google.com/android/answer/7680439) |
|Linux | [Linux 101 : mise à jour de votre système](https://www.linux.com/training-tutorials/linux-101-updating-your-system) |

## <a name="get-microsoft-defender-for-endpoint"></a>Obtenir Microsoft Defender pour le point de terminaison

Maintenant que vous avez mis à jour les appareils de votre organisation, l’étape suivante consiste à obtenir Microsoft Defender pour le point de terminaison, à attribuer des licences et à vous assurer que le service est mis en service.

1. Achetez ou essayez Microsoft Defender pour Endpoint dès aujourd’hui. [Démarrez une version d’essai gratuite ou demandez un devis.](https://aka.ms/mdatp) 

2. Vérifiez que vos licences sont correctement provisionées. [Vérifiez l’état de votre licence.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/production-deployment#check-license-state)

3. En tant qu’administrateur général ou administrateur de sécurité, vous pouvez configurer votre instance cloud dédiée de Microsoft Defender for Endpoint. Voir [Configuration de Microsoft Defender pour endpoint : configuration du client.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/production-deployment#tenant-configuration)

4. Si les points de terminaison (tels que les appareils) de votre organisation utilisent un proxy pour accéder à Internet, voir Microsoft Defender pour l’installation du point de [terminaison](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/production-deployment#network-configuration): configuration réseau .
 
À ce stade, vous êtes prêt à accorder l’accès à vos administrateurs de sécurité et opérateurs de sécurité qui utiliseront le Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ). 

> [!NOTE]
> Le Centre de sécurité Microsoft Defender est parfois appelé portail Microsoft Defender pour points de terminaison. 

## <a name="grant-access-to-the-microsoft-defender-security-center"></a>Accorder l’accès au Centre de sécurité Microsoft Defender

Le Centre de sécurité Microsoft Defender ( ) est l’endroit où vous accédez et configurez les fonctionnalités de [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) Microsoft Defender pour le point de terminaison. Pour plus d’informations, voir [Vue d’ensemble du Centre de sécurité Microsoft Defender.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/use)

Les autorisations sur le Centre de sécurité Microsoft Defender peuvent être accordées à l’aide d’autorisations de base ou d’un contrôle d’accès basé sur un rôle (RBAC). Nous vous recommandons d’utiliser RBAC afin de contrôler plus granulairement les autorisations.

1. Planifiez les rôles et les autorisations de vos administrateurs de sécurité et opérateurs de sécurité. Voir [Contrôle d’accès basé sur un rôle.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/prepare-deployment#role-based-access-control)

2. Configurez et configurez le RBAC. Nous vous recommandons d’utiliser [Intune](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune) pour configurer le RBAC, en particulier si votre organisation utilise une combinaison d’appareils Windows 10, macOS, iOS et Android. Voir [la configuration du RBAC à l’aide d’Intune.](https://docs.microsoft.com/mem/intune/fundamentals/role-based-access-control)

    Si votre organisation nécessite une méthode autre qu’Intune, choisissez l’une des options suivantes :
    - [Gestionnaire de configuration](https://docs.microsoft.com/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)
    - [Gestion avancée des stratégies de groupe](https://docs.microsoft.com/microsoft-desktop-optimization-pack/agpm)
    - [Windows Admin Center](https://docs.microsoft.com/windows-server/manage/windows-admin-center/overview)

3. Accorder l’accès au Centre de sécurité Microsoft Defender. (Vous avez besoin d’aide ? Voir [Gérer l’accès au portail à l’aide de RBAC](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/rbac)).

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Configurer les paramètres de proxy d’appareil et de connectivité Internet

Pour activer la communication entre vos appareils et Microsoft Defender pour le point de terminaison, configurez les paramètres proxy et Internet. Le tableau suivant inclut des liens vers des ressources que vous pouvez utiliser pour configurer vos paramètres proxy et Internet pour différents systèmes d’exploitation et fonctionnalités :

|Fonctionnalités  | Système d’exploitation | Ressources |
|--|--|--|
|[Détection et réponse des points de terminaison](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) (EDR) |- [Windows 10](https://docs.microsoft.com/windows/release-health/release-information) <br/>- [Windows Server 2019](https://docs.microsoft.com/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/>- [Windows Server 1803 ou une ultérieure](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1803)  |[Configurer les paramètres de proxy et de connectivité Internet de l’ordinateur](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-proxy-internet) |
|EDR |- [Windows Server 2016](https://docs.microsoft.com/windows/release-health/status-windows-10-1607-and-windows-server-2016) <br/>- [Windows Server 2012 R2](https://docs.microsoft.com/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/>- [Windows Server 2008 R2 SP1](https://docs.microsoft.com/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/>- [Windows 8.1](https://docs.microsoft.com/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/>- [Windows 7 SP1](https://docs.microsoft.com/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |[Configurer les paramètres de proxy et de connectivité Internet](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/onboard-downlevel#configure-proxy-and-internet-connectivity-settings) |
|EDR  |macOS : <br/>- 10.15 (Caserline)<br/>- 10.14 (Mojave) <br/>- 10.13 (High Sierra)  |[Microsoft Defender pour point de terminaison pour Mac : connexions réseau](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/microsoft-defender-atp-mac#network-connections) |
|[Antivirus Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) |- [Windows 10](https://docs.microsoft.com/windows/release-health/release-information) <br/>- [Windows Server 2019](https://docs.microsoft.com/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/>- [Windows Server 1803 ou une ultérieure](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1803) <br/>- [Windows Server 2016](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-2016) |[Configurer et valider les connexions réseau à un antivirus Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-network-connections-microsoft-defender-antivirus)<br/> |
|Antivirus |macOS : <br/>- 10.15 (Îles)<br/>- 10.14 (Mojave) <br/>- 10.13 (High Sierra) |[Microsoft Defender pour point de terminaison pour Mac : connexions réseau](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/microsoft-defender-atp-mac#network-connections) |
|Antivirus |Linux : <br/>- RHEL 7.2+<br/>- CentOS Linux 7.2+<br/>- Ubuntu 16 LTS ou un LTS supérieur<br/>- SLES 12+<br/>- Debian 9+<br/>- Oracle Linux 7.2 |[Microsoft Defender pour point de terminaison pour Linux : connexions réseau](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/microsoft-defender-atp-linux#network-connections) 

## <a name="next-step"></a>Étape suivante

**Félicitations**! Vous avez terminé la phase **de** préparation [de la migration de Mc Antivirus vers Microsoft Defender pour endpoint](mcafee-to-microsoft-defender-migration.md#the-migration-process)!

- [Procédez à la mise en place de Microsoft Defender pour endpoint.](mcafee-to-microsoft-defender-setup.md)