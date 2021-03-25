---
title: Gérer Microsoft Defender for Endpoint à l’aide de Configuration Manager
description: Découvrez comment gérer Microsoft Defender pour Endpoint avec Configuration Manager
keywords: post-migration, gérer, opérations, maintenance, utilisation, Configuration Manager, windows defender – Protection avancée contre les menaces, atp, edr
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
ms.date: 09/22/2020
ms.reviewer: chventou
ms.openlocfilehash: 36599d830ac737b112df9f7c948e65829d6a7ce6
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51066838"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>Gérer Microsoft Defender for Endpoint avec Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


Nous vous recommandons d’utiliser [Microsoft Endpoint Manager,](https://docs.microsoft.com/mem)qui inclut [Microsoft Intune (Intune)](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune) et [Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/mem/configmgr/core/understand/introduction) (Configuration Manager) pour gérer les fonctionnalités de protection contre les menaces de votre organisation pour les appareils (également appelés points de terminaison). 
- [En savoir plus sur endpoint Manager](https://docs.microsoft.com/mem/endpoint-manager-overview)
- [Co-gérer Microsoft Defender pour endpoint sur les appareils Windows 10 avec Configuration Manager et Intune](manage-atp-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>Configurer Microsoft Defender pour endpoint avec Configuration Manager

|Tâche  |Ressources pour en savoir plus  |
|---------|---------|
|**Installer la console Configuration Manager si** vous ne l’avez pas déjà<br/><br/>*Si vous ne disposez pas déjà de la console Gestionnaire de configuration, utilisez ces ressources pour obtenir les bits et l’installer.* |[Obtenir le support d’installation](https://docs.microsoft.com/mem/configmgr/core/servers/deploy/install/get-install-media)<br/><br/>[Installer la console Configuration Manager](https://docs.microsoft.com/mem/configmgr/core/servers/deploy/install/install-consoles)  |
|**Utiliser Configuration Manager pour intégrer des appareils** à Microsoft Defender pour le point de terminaison <br/><br/> *Si vous avez des appareils (ou points de terminaison) qui ne sont pas déjà intégrés à Microsoft Defender pour Endpoint, vous pouvez le faire avec Configuration Manager.*   |[Intégration à Microsoft Defender pour endpoint avec Configuration Manager](https://docs.microsoft.com/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)      |
|**Gérer les stratégies anti-programme malveillant et la sécurité du Pare-feu Windows** pour les ordinateurs clients (points de terminaison)<br/><br/>*Configurez les fonctionnalités de protection des points de terminaison, notamment Microsoft Defender pour le point de terminaison, Exploit Protection, le contrôle d’application, le logiciel anti-programme malveillant, les paramètres de pare-feu, etc.*  |[Configuration Manager : Endpoint Protection](https://docs.microsoft.com/mem/configmgr/protect/deploy-use/endpoint-protection)       |
|Choisir les méthodes de mise à jour des mises à jour **du logiciel anti-programme** malveillant sur les appareils de votre organisation <br/><br/>*Avec Endpoint Protection dans Configuration Manager, vous pouvez choisir parmi plusieurs méthodes pour maintenir les définitions de logiciels anti-programme malveillant à jour sur les appareils de votre organisation.* |[Configurer les mises à jour des définitions pour Endpoint Protection](https://docs.microsoft.com/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/>[Utiliser Configuration Manager pour fournir des mises à jour de définition](https://docs.microsoft.com/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr) |
|**Activer la Protection du réseau** pour empêcher les employés d’utiliser des applications qui utilisent du contenu malveillant sur Internet <br/><br/>*Nous vous recommandons d’utiliser d’abord le [mode audit](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/evaluate-network-protection) pour la protection du réseau dans un environnement de test pour voir quelles applications seront bloquées avant le déploiement.* |[Activer la protection du réseau avec Configuration Manager](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)  |
|**Configurer l’accès contrôlé aux dossiers pour** la protection contre les ransomware <br/><br/>*L’accès contrôlé aux dossiers est également appelé protection antiransomware.*   |[Protection des points de terminaison : accès contrôlé aux dossiers](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/>[Activer l’accès contrôlé aux dossiers dans Microsoft Endpoint Configuration Manage](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager) |

## <a name="configure-your-microsoft-defender-security-center"></a>Configurer votre Centre de sécurité Microsoft Defender

Si vous ne l’avez pas déjà fait, configurez votre Centre de sécurité **Microsoft Defender** ( ) pour afficher les alertes, configurer les fonctionnalités de protection contre les menaces et afficher des informations détaillées sur la posture de sécurité globale de votre [https://securitycenter.windows.com](https://securitycenter.windows.com) organisation. 

Vous pouvez également configurer si et quelles fonctionnalités les utilisateurs finaux peuvent voir dans le Centre de sécurité Microsoft Defender.

- [Vue d’ensemble du Centre de sécurité Microsoft Defender](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/use)

- [Protection des points de terminaison : Centre de sécurité Microsoft Defender](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Étapes suivantes

- [Obtenir une vue d’ensemble de la gestion des menaces et des vulnérabilités](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)

- [Visiter le tableau de bord opérations de sécurité du Centre de sécurité Microsoft Defender](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/security-operations-dashboard)

- [Gérer Microsoft Defender pour le point de terminaison avec Intune](manage-atp-post-migration-intune.md)
