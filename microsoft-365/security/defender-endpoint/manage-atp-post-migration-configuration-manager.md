---
title: Gérer Microsoft Defender for Endpoint à l’aide de Configuration Manager
description: Découvrez comment gérer Microsoft Defender pour Endpoint avec Configuration Manager
keywords: post-migration, manage, operations, maintenance, utilization, Configuration Manager, Microsoft Defender for Endpoint, edr
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
- m365solution-scenario
ms.topic: article
ms.date: 06/11/2021
ms.reviewer: chventou
ms.openlocfilehash: 5fde3bfad69a5851dd94b76afb262f8be12d0360
ms.sourcegitcommit: 3e197d1ff7d8100faeaf1f5a33f1ad4ed2f72e99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2021
ms.locfileid: "52908256"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>Gérer Microsoft Defender for Endpoint avec Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


Nous vous recommandons d’utiliser [Microsoft Endpoint Manager,](/mem)qui inclut [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (Intune) et [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction) (Configuration Manager) pour gérer les fonctionnalités de protection contre les menaces de votre organisation pour les appareils (également appelés points de terminaison). 
- [En savoir plus sur Endpoint Manager](/mem/endpoint-manager-overview)
- [Co-gérer Microsoft Defender for Endpoint sur Windows 10 appareils avec Configuration Manager et Intune](manage-atp-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>Configurer Microsoft Defender pour endpoint avec Configuration Manager

|Tâche  |Ressources pour en savoir plus  |
|---------|---------|
|**Installer la console Configuration Manager si** vous ne l’avez pas déjà<br/><br/>*Si vous ne disposez pas déjà de la console Gestionnaire de configuration, utilisez ces ressources pour obtenir les bits et l’installer.* |[Obtenir le support d’installation](/mem/configmgr/core/servers/deploy/install/get-install-media)<br/><br/>[Installer la console Configuration Manager](/mem/configmgr/core/servers/deploy/install/install-consoles)  |
|**Utiliser Configuration Manager pour intégrer des appareils** à Microsoft Defender pour le point de terminaison <br/><br/> *Si vous avez des appareils (ou points de terminaison) qui ne sont pas déjà intégrés à Microsoft Defender pour Endpoint, vous pouvez le faire avec Configuration Manager.*   |[Intégration à Microsoft Defender pour endpoint avec Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)      |
|**Gérer les stratégies anti-programme malveillant** et la sécurité Windows pare-feu pour les ordinateurs clients (points de terminaison)<br/><br/>*Configurez les fonctionnalités de protection des points de terminaison, notamment Microsoft Defender pour le point de terminaison, Exploit Protection, le contrôle d’application, les logiciels anti-programme malveillant, les paramètres de pare-feu, etc.*  |[Configuration Manager : Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection)       |
|Choisir les méthodes de mise à jour des mises à jour **anti-programme** malveillant sur les appareils de votre organisation <br/><br/>*Avec Endpoint Protection configuration Manager, vous pouvez choisir parmi plusieurs méthodes pour maintenir les définitions de logiciels anti-programme malveillant à jour sur les appareils de votre organisation.* |[Configurer les mises à jour des définitions pour Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/>[Utiliser Configuration Manager pour fournir des mises à jour de définition](/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr) |
|**Activer la Protection du réseau** pour empêcher les employés d’utiliser des applications qui utilisent du contenu malveillant sur Internet <br/><br/>*Nous vous recommandons d’utiliser d’abord le [mode audit](/microsoft-365/security/defender-endpoint/evaluate-network-protection) pour la protection du réseau dans un environnement de test pour voir quelles applications seront bloquées avant le déploiement.* |[Activer la protection réseau avec Configuration Manager](/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)  |
|**Configurer l’accès contrôlé aux dossiers pour** la protection contre les ransomware <br/><br/>*L’accès contrôlé aux dossiers est également appelé protection antiransomware.*   |[Protection des points de terminaison : accès contrôlé aux dossiers](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/>[Activer l’accès contrôlé aux dossiers dans Microsoft Endpoint Configuration Manage](/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager) |

## <a name="configure-your-microsoft-defender-security-center"></a>Configurer votre Centre de sécurité Microsoft Defender

Si ce n’est pas déjà fait, configurez votre portail Microsoft 365 Defender pour afficher les alertes, configurer les fonctionnalités de protection contre les menaces et afficher des informations détaillées sur la posture de sécurité globale de votre organisation. Voir [Centre de sécurité Microsoft Defender](microsoft-defender-security-center.md). Vous pouvez également configurer si et quelles fonctionnalités les utilisateurs finaux peuvent voir dans le portail Microsoft 365 Defender.

- [Vue d’ensemble du Centre de sécurité Microsoft Defender](/microsoft-365/security/defender-endpoint/use)

- [Protection des points de terminaison : Centre de sécurité Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Étapes suivantes

- [Obtenir une vue d’ensemble des Gestion des menaces et des vulnérabilités](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)

- [Visiter le tableau de bord Centre de sécurité Microsoft Defender opérations de sécurité de l’utilisateur](/microsoft-365/security/defender-endpoint/security-operations-dashboard)

- [Gérer Microsoft Defender pour le point de terminaison avec Intune](manage-atp-post-migration-intune.md)
