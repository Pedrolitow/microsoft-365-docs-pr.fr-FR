---
title: Gérer Microsoft Defender pour point de terminaison à l’aide de Configuration Manager
description: Découvrez comment gérer Microsoft Defender pour point de terminaison avec Configuration Manager
keywords: post-migration, gérer, opérations, maintenance, utilisation, Configuration Manager, Microsoft Defender pour point de terminaison, edr
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
- tier2
ms.topic: article
ms.date: 07/01/2022
ms.reviewer: chventou
search.appverid: met150
ms.openlocfilehash: 43fb93dc01517372bdeeaba05c012aa5d4bb6a29
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68232933"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>Gérer Microsoft Defender pour point de terminaison avec Configuration Manager

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Nous vous recommandons d’utiliser [Microsoft Endpoint Manager](/mem), qui inclut [les Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (Intune) et les [Configuration Manager de point de terminaison Microsoft](/mem/configmgr/core/understand/introduction) (Configuration Manager ) pour gérer les fonctionnalités de protection contre les menaces de votre organisation pour les appareils (également appelés points de terminaison).

- [En savoir plus sur Endpoint Manager](/mem/endpoint-manager-overview)
- [Cogestion des Microsoft Defender pour point de terminaison sur les appareils Windows 10 et Windows 11 avec Configuration Manager et Intune](manage-mde-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>Configurer Microsoft Defender pour point de terminaison avec Configuration Manager

|Tâche|Ressources pour en savoir plus|
|---|---|
|**Installez la console Configuration Manager** si vous ne l’avez pas déjà <br/><br/> *Si vous n’avez pas encore la console Configuration Manager, utilisez ces ressources pour obtenir les bits et l’installer.*|[Obtenir le support d’installation](/mem/configmgr/core/servers/deploy/install/get-install-media) <br/><br/> [Installer la console Configuration Manager](/mem/configmgr/core/servers/deploy/install/install-consoles)|
|**Utiliser Configuration Manager pour intégrer des appareils** à Microsoft Defender pour point de terminaison <br/><br/> *Si des appareils (ou points de terminaison) ne sont pas déjà intégrés à Microsoft Defender pour point de terminaison, vous pouvez le faire avec Configuration Manager.*|[Intégrer à Microsoft Defender pour point de terminaison avec Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)|
|**Gérer les stratégies anti-programme malveillant et la sécurité du Pare-feu Windows** pour les ordinateurs clients (points de terminaison) <br/><br/> *Configurez les fonctionnalités endpoint protection, notamment Microsoft Defender pour point de terminaison, exploit protection, contrôle d’application, logiciel anti-programme malveillant, paramètres de pare-feu, etc.*|[Configuration Manager : Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection)|
|**Choisir des méthodes pour mettre à jour les mises à jour anti-programme malveillant** sur les appareils de votre organisation <br/><br/> *Avec Endpoint Protection dans Configuration Manager, vous pouvez choisir parmi plusieurs méthodes pour maintenir les définitions de logiciel anti-programme malveillant à jour sur les appareils de votre organisation.*|[Configurer les mises à jour de définition pour Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/> [Utiliser Configuration Manager pour fournir des mises à jour de définition](/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr)|
|**Activer la protection réseau** pour empêcher les employés d’utiliser des applications qui utilisent du contenu malveillant sur Internet <br/><br/> *Nous vous recommandons d’utiliser d’abord le [mode audit](/microsoft-365/security/defender-endpoint/evaluate-network-protection) pour la protection réseau dans un environnement de test pour voir quelles applications seraient bloquées avant le déploiement.*|[Activer la protection réseau avec Configuration Manager](/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)|
|**Configurer l’accès contrôlé aux dossiers** pour vous protéger contre les ransomware <br/><br/> *L’accès contrôlé aux dossiers est également appelé protection antiransomware.*|[Endpoint Protection : accès contrôlé aux dossiers](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Activer l’accès contrôlé aux dossiers dans Microsoft Endpoint Configuration Manage](/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Configurer votre portail Microsoft 365 Defender

Si vous ne l’avez pas encore fait, configurez votre portail Microsoft 365 Defender pour afficher les alertes, configurer les fonctionnalités de protection contre les menaces et afficher des informations détaillées sur la posture de sécurité globale de votre organisation. Consultez Bien que l’attaque ait été détectée et arrêtée, des alertes, telles qu’une « alerte d’accès initial », ont été déclenchées et affichées dans le [portail Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Vous pouvez également configurer si et quelles fonctionnalités les utilisateurs finaux peuvent voir dans le portail Microsoft 365 Defender.

- [Vue d’ensemble de Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Endpoint Protection : Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Prochaines étapes

- [Obtenir une vue d’ensemble de La gestion des vulnérabilités defender](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Gérer Microsoft Defender pour point de terminaison avec Intune](manage-mde-post-migration-intune.md)
