---
title: Basculer vers Microsoft Defender pour point de terminaison - Préparer
description: Préparez-vous à passer à Microsoft Defender pour point de terminaison. Mettez à jour vos appareils et configurez vos connexions réseau.
keywords: migration, Microsoft Defender pour point de terminaison, bonnes pratiques
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-migratetomdatp
- highpri
- tier1
ms.topic: conceptual
ms.custom:
- migrationguides
- admindeeplinkDEFENDER
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
search.appverid: met150
ms.openlocfilehash: 518ddface2c94f8eafe8e81ea72486f3c1059ac0
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688493"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-1-prepare"></a>Passer à Microsoft Defender pour point de terminaison - Phase 1 : Préparation

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| ![Phase 1 : Préparation.](images/phase-diagrams/prepare.png#lightbox)<br/>Phase 1 : préparation | [![Phase 2 : configuration](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[Phase 2 : configuration](switch-to-mde-phase-2.md) | [![Phase 3 : intégration](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[Phase 3 : intégration](switch-to-mde-phase-3.md) |
|--|--|--|
|*Tu es là !*| | |

**Bienvenue dans la phase de préparation du [passage à Defender pour point de terminaison](switch-to-mde-overview.md#the-migration-process)**.

Cette phase de migration comprend les étapes suivantes :

1. [Obtenir et déployer des mises à jour sur les appareils de votre organisation](#get-and-deploy-updates-across-your-organizations-devices)
2. [Obtenez Defender pour point de terminaison](#get-microsoft-defender-for-endpoint).
3. [Accordez l’accès au portail Microsoft 365 Defender](#grant-access-to-the-microsoft-365-defender-portal).
4. [Configurez les paramètres de proxy d’appareil et de connectivité Internet](#configure-device-proxy-and-internet-connectivity-settings).

## <a name="get-and-deploy-updates-across-your-organizations-devices"></a>Obtenir et déployer des mises à jour sur les appareils de votre organisation

Il est recommandé de maintenir à jour les appareils et les points de terminaison de votre organisation. Assurez-vous que votre solution antivirus et de protection de point de terminaison existante est à jour, et que les systèmes d’exploitation et les applications de votre organisation disposent également des dernières mises à jour. Cette opération peut vous aider à éviter les problèmes ultérieurement lorsque vous migrez vers Defender pour point de terminaison et Microsoft Defender Antivirus.

### <a name="make-sure-your-existing-solution-is-up-to-date"></a>Vérifiez que votre solution existante est à jour

Conservez votre solution Endpoint Protection existante à jour et assurez-vous que les appareils de votre organisation disposent des dernières mises à jour de sécurité.

Besoin d’aide ? Consultez la documentation de votre fournisseur de solutions.

### <a name="make-sure-your-organizations-devices-are-up-to-date"></a>Vérifiez que les appareils de votre organisation sont à jour

Vous avez besoin d’aide pour mettre à jour les appareils de votre organisation ? Consultez les ressources suivantes :

|Système d’exploitation|Ressource|
|---|---|
|Windows|[Microsoft Update](/windows/deployment/update/how-windows-update-works)|
|macOS|[Comment mettre à jour le logiciel sur votre Mac](https://support.apple.com/HT201541)|
|iOS|[Mettre à jour votre iPhone, iPad ou iPod touch](https://support.apple.com/HT204204)|
|Android|[Vérifier & mettre à jour votre version d’Android](https://support.google.com/android/answer/7680439)|
|Linux|[Linux 101 : Mise à jour de votre système](https://www.linux.com/training-tutorials/linux-101-updating-your-system)|

## <a name="get-microsoft-defender-for-endpoint"></a>Obtenir Microsoft Defender pour point de terminaison

Maintenant que vous avez mis à jour les appareils de votre organisation, l’étape suivante consiste à obtenir Defender pour point de terminaison, à attribuer des licences et à vérifier que le service est approvisionné.

1. Achetez ou essayez Defender pour point de terminaison dès aujourd’hui. [Démarrez un essai gratuit ou demandez un devis](https://aka.ms/mdatp).

2. Vérifiez que vos licences sont correctement approvisionnées. [Vérifiez l’état de votre licence](production-deployment.md#check-license-state).

3. Configurez votre instance cloud dédiée de Defender pour point de terminaison. Consultez [Configuration de Defender pour point de terminaison : Configuration du locataire](production-deployment.md#tenant-configuration).

4. Si des points de terminaison (tels que des appareils) de votre organisation utilisent un proxy pour accéder à Internet, consultez [Configuration de Defender pour point de terminaison : Configuration réseau](production-deployment.md#network-configuration).

À ce stade, vous êtes prêt à accorder l’accès à vos administrateurs de sécurité et opérateurs de sécurité qui utiliseront le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>.

> [!NOTE]
> Le portail Microsoft 365 Defender est parfois appelé portail Defender pour point de terminaison et est accessible à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>. L’ancien Centre de sécurité Microsoft Defender (https://securitycenter.windows.com) sera bientôt redirigé vers le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Microsoft 365 Defender vue d’ensemble du portail](portal-overview.md).

## <a name="grant-access-to-the-microsoft-365-defender-portal"></a>Accorder l’accès au portail Microsoft 365 Defender

Le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> vous permet d’accéder aux fonctionnalités de Defender pour point de terminaison et de les configurer. Pour plus d’informations, consultez [Vue d’ensemble du portail Microsoft 365 Defender](use.md).

Les autorisations d’accès au portail Microsoft 365 Defender peuvent être accordées à l’aide des autorisations de base ou du contrôle d’accès en fonction du rôle (RBAC). Nous vous recommandons d’utiliser RBAC afin de disposer d’un contrôle plus précis sur les autorisations.

1. Planifiez les rôles et les autorisations de vos administrateurs de sécurité et opérateurs de sécurité. Consultez [Contrôle d’accès en fonction du rôle](prepare-deployment.md#role-based-access-control).

2. Configurez et configurez RBAC. Nous vous [recommandons](/mem/intune/fundamentals/what-is-intune) d’utiliser Intune pour configurer RBAC, en particulier si votre organisation utilise une combinaison d’appareils Windows 10, macOS, iOS et Android. Consultez [Configuration du contrôle d’accès en fonction du rôle à l’aide de Intune](/mem/intune/fundamentals/role-based-access-control).

    Si votre organisation a besoin d’une méthode autre que Intune, choisissez l’une des options suivantes :

    - [Configuration Manager](/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)

    - [Gestion avancée des stratégie de groupe](/microsoft-desktop-optimization-pack/agpm)
    
    - [Windows Admin Center](/windows-server/manage/windows-admin-center/overview)

3. Accordez l’accès au portail Microsoft 365 Defender. (Vous avez besoin d’aide ? Consultez [Gérer l’accès au portail à l’aide de RBAC](rbac.md).

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Configurer les paramètres de proxy d’appareil et de connectivité Internet

Pour activer la communication entre vos appareils et Defender pour point de terminaison, configurez les paramètres proxy et Internet. Le tableau suivant contient des liens vers des ressources que vous pouvez utiliser pour configurer vos paramètres proxy et Internet pour différents systèmes d’exploitation et fonctionnalités :

|Fonctionnalités|Système d’exploitation|Ressources|
|---|---|---|
|[Détection et réponse de point de terminaison](overview-endpoint-detection-response.md) (EDR)|[Windows 10](/windows/release-health/release-information) ou version ultérieure<br/><br/>Windows Server 2022 <br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/>[Windows Server 1803 ou version ultérieure](/windows-server/get-started/whats-new-in-windows-server-1803)<br/><br/>[Windows Server 2016*](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2*](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)|[Configurer les paramètres de proxy d’ordinateur et de connectivité Internet](configure-proxy-internet.md)|
|EDR |[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)|[Configurer les paramètres de connectivité proxy et Internet](onboard-downlevel.md#configure-proxy-and-internet-connectivity-settings)|
|EDR|macOS (voir [Configuration requise](microsoft-defender-endpoint-mac.md))|[Defender pour point de terminaison sur macOS : Connexions réseau](microsoft-defender-endpoint-mac.md#network-connections)|
|[Antivirus Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md)|[Windows 10](/windows/release-health/release-information) <br/><br/> [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/> Windows Server 2022 <br/><br/> [Windows Server 1803 ou version ultérieure](/windows-server/get-started/whats-new-in-windows-server-1803) <br/><br/> [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)<br/><br/>[Windows Server 2012 R2*](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)|[Configurer et valider les connexions réseau à un antivirus Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md)|
|Antivirus|macOS (voir [Configuration requise](microsoft-defender-endpoint-mac.md))|[Defender pour point de terminaison sur macOS : Connexions réseau](microsoft-defender-endpoint-mac.md#network-connections)|
|Antivirus|Linux (voir [Configuration requise](microsoft-defender-endpoint-linux.md#system-requirements))|[Defender pour point de terminaison sur Linux : Connexions réseau](microsoft-defender-endpoint-linux.md#network-connections)|

*Nécessite l’installation de la solution moderne et unifiée pour Windows Server 2012 R2 et 2016. Pour plus d’informations, consultez [Intégrer des serveurs Windows au service Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/configure-server-endpoints).

## <a name="next-step"></a>Étape suivante

**Félicitations** ! Vous avez terminé la phase **de préparation** du [passage à Defender pour point de terminaison](switch-to-mde-overview.md#the-migration-process) !

- [Passez à la configuration de Defender pour point de terminaison](switch-to-mde-phase-2.md).
