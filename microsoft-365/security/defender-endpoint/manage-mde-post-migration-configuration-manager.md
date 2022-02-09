---
title: Gérer Microsoft Defender for Endpoint à l’aide de Configuration Manager
description: Découvrez comment gérer Microsoft Defender pour Endpoint avec Configuration Manager
keywords: post-migration, manage, operations, maintenance, utilization, Configuration Manager, Microsoft Defender for Endpoint, edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 40bac47a4c22e3a8706ed4b38b479fff5d500410
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2022
ms.locfileid: "62465227"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>Gérer Microsoft Defender for Endpoint avec Configuration Manager

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Nous vous recommandons [d’Microsoft Endpoint Manager](/mem), qui inclut [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (Intune) et [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction) (Configuration Manager) pour gérer les fonctionnalités de protection contre les menaces de votre organisation pour les appareils ( également appelés points de terminaison).

- [En savoir plus sur Endpoint Manager](/mem/endpoint-manager-overview)
- [Co-gérer Microsoft Defender for Endpoint sur Windows 10 et Windows 11 avec Configuration Manager et Intune](manage-mde-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>Configurer Microsoft Defender pour endpoint avec Configuration Manager

<br/><br/>

|Tâche|Ressources pour en savoir plus|
|---|---|
|**Installer la console Configuration Manager si** vous ne l’avez pas déjà <br/><br/> *Si vous ne disposez pas déjà de la console Gestionnaire de configuration, utilisez ces ressources pour obtenir les bits et l’installer.*|[Obtenir le support d’installation](/mem/configmgr/core/servers/deploy/install/get-install-media) <br/><br/> [Installer la console Configuration Manager](/mem/configmgr/core/servers/deploy/install/install-consoles)|
|**Utiliser Configuration Manager pour intégrer des appareils** à Microsoft Defender pour le point de terminaison <br/><br/> *Si vous avez des appareils (ou points de terminaison) qui ne sont pas déjà intégrés à Microsoft Defender pour Endpoint, vous pouvez le faire avec Configuration Manager.*|[Intégration à Microsoft Defender pour endpoint avec Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)|
|**Gérer les stratégies anti-programme malveillant et la sécurité Windows pare-feu** pour les ordinateurs clients (points de terminaison) <br/><br/> *Configurez les fonctionnalités de protection des points de terminaison, notamment Microsoft Defender pour le point de terminaison, Exploit Protection, le contrôle d’application, le logiciel anti-programme malveillant, les paramètres de pare-feu, etc.*|[Configuration Manager : Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection)|
|**Choisir les méthodes de mise à jour des mises à jour anti-programme** malveillant sur les appareils de votre organisation <br/><br/> *Avec Endpoint Protection configuration manager, vous pouvez choisir parmi plusieurs méthodes pour maintenir les définitions de logiciels anti-programme malveillant à jour sur les appareils de votre organisation.*|[Configurer les mises à jour de définition pour Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/> [Utiliser Configuration Manager pour fournir des mises à jour de définition](/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr)|
|**Activer la Protection du réseau** pour empêcher les employés d’utiliser des applications qui utilisent du contenu malveillant sur Internet <br/><br/> *Nous vous recommandons d’utiliser d’abord le [mode audit](/microsoft-365/security/defender-endpoint/evaluate-network-protection) pour la protection du réseau dans un environnement de test pour voir quelles applications seront bloquées avant le déploiement.*|[Activer la protection du réseau avec Configuration Manager](/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)|
|**Configurer l’accès contrôlé aux dossiers pour** la protection contre les ransomware <br/><br/> *L’accès contrôlé aux dossiers est également appelé protection antiransomware.*|[Protection des points de terminaison : accès contrôlé aux dossiers](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Activer l’accès contrôlé aux dossiers dans Microsoft Endpoint Configuration Manage](/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Configurer votre portail Microsoft 365 Defender client

Si ce n’est pas déjà fait, configurez votre portail Microsoft 365 Defender pour afficher les alertes, configurer les fonctionnalités de protection contre les menaces et afficher des informations détaillées sur la posture de sécurité globale de votre organisation. Voir Si l’attaque a été détectée et arrêtée, des alertes, telles qu’une « alerte d’accès initial », ont été déclenchées et sont apparus dans [le portail Microsoft 365 Defender.](/microsoft-365/security/defender/microsoft-365-defender) Vous pouvez également configurer si les fonctionnalités que les utilisateurs finaux peuvent voir et quelles fonctionnalités peuvent être Microsoft 365 Defender portail.

- [Vue d’ensemble Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Protection des points de terminaison : Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Prochaines étapes

- [Obtenir une vue d’ensemble de la gestion des menaces et des vulnérabilités](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Visiter le tableau de bord Microsoft 365 Defender de sécurité du portail d’entreprise](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Gérer Microsoft Defender pour le point de terminaison avec Intune](manage-mde-post-migration-intune.md)
