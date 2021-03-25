---
title: Gérer Microsoft Defender pour le point de terminaison à l’aide d’objets de stratégie de groupe
description: Découvrez comment gérer Microsoft Defender pour le point de terminaison à l’aide d’objets de stratégie de groupe
keywords: post-migration, gérer, opérations, maintenance, utilisation, PowerShell, protection avancée contre les menaces windows defender, atp, edr
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
ms.openlocfilehash: c21ac21f4369934375d44f5792afb874070ab074
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51068542"
---
# <a name="manage-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Gérer Microsoft Defender pour le point de terminaison avec des objets de stratégie de groupe

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


> [!NOTE]
> Nous vous recommandons [d’utiliser Microsoft Endpoint Manager](https://docs.microsoft.com/mem) pour gérer les fonctionnalités de protection contre les menaces de votre organisation pour les appareils (également appelés points de terminaison). Endpoint Manager inclut [Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune) et [Microsoft Endpoint Configuration Manager.](https://docs.microsoft.com/mem/configmgr/core/understand/introduction) **[En savoir plus sur endpoint Manager](https://docs.microsoft.com/mem/endpoint-manager-overview)**. 

Vous pouvez utiliser les objets de stratégie de groupe dans les services de domaine Azure Active Directory pour gérer certains paramètres dans Microsoft Defender pour point de terminaison.

## <a name="configure-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Configurer Microsoft Defender pour le point de terminaison avec des objets de stratégie de groupe

Le tableau suivant répertorie les différentes tâches que vous pouvez effectuer pour configurer Microsoft Defender pour endpoint avec des objets de stratégie de groupe.

|Tâche  |Ressources pour en savoir plus  |
|---------|---------|
|**Gérer les paramètres des objets utilisateur et ordinateur** <br/><br/>*Personnalisez les objets de stratégie de groupe intégrés ou créez des objets de stratégie de groupe et des unités d’organisation personnalisés en fonction des besoins de votre organisation.*     |[Administrer la stratégie de groupe dans un domaine géré Azure Active Directory Domain Services](https://docs.microsoft.com/azure/active-directory-domain-services/manage-group-policy)   |
|**Configurer l’Antivirus Microsoft Defender** <br/><br/>*Configurez les fonctionnalités antivirus & fonctionnalités, notamment les paramètres de stratégie, les exclusions, les corrections et les analyses programmées sur les appareils de votre organisation (également appelés points de terminaison).*   |[Utiliser les paramètres de stratégie de groupe pour configurer et gérer l’Antivirus Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus) <br/><br/>[Utiliser une stratégie de groupe pour activer la protection cloud](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-group-policy-to-enable-cloud-delivered-protection)      |
|**Gérer les règles de réduction de la surface d’attaque de votre organisation** <br/><br/>*Personnalisez vos règles de réduction de la surface d’attaque en excluant les fichiers & dossiers, ou en ajoutant du texte personnalisé aux alertes de notification qui apparaissent sur les appareils des utilisateurs.* |[Personnaliser les règles de réduction de la surface d’attaque avec des objets de stratégie de groupe](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction#use-group-policy-to-exclude-files-and-folders) |
|**Gérer les paramètres Exploit Protection**<br/><br/>*Vous pouvez personnaliser vos paramètres Exploit Protection, importer un fichier de configuration, puis utiliser la stratégie de groupe pour déployer ce fichier de configuration.*  |[Personnaliser les paramètres Exploit Protection](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/>[Importer, exporter et déployer des configurations Exploit Protection](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml)<br/><br/>[Utiliser une stratégie de groupe pour distribuer la configuration](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml#use-group-policy-to-distribute-the-configuration)  |
|**Activer la Protection du réseau** pour empêcher les employés d’utiliser des applications qui utilisent du contenu malveillant sur Internet <br/><br/>*Nous vous recommandons d’utiliser d’abord le [mode audit](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/evaluate-network-protection) pour la protection du réseau dans un environnement de test pour voir quelles applications seront bloquées avant le déploiement.* |[Activer la protection du réseau à l’aide de la stratégie de groupe](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/enable-network-protection#group-policy)  |
|**Configurer l’accès contrôlé aux dossiers pour** la protection contre les ransomware <br/><br/>*[L’accès contrôlé aux](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/controlled-folders) dossiers est également appelé protection antiransomware.*  |[Activer l’accès contrôlé aux dossiers à l’aide de la stratégie de groupe](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/enable-controlled-folders#group-policy) |
|**Configurez Microsoft Defender SmartScreen pour la** protection contre les sites et fichiers malveillants sur Internet.  |[Configurer les paramètres de stratégie de groupe et de gestion des périphériques mobiles (MDM) de Microsoft Defender SmartScreen à l’aide de la stratégie de groupe](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#group-policy-settings)  |
|**Configurer le chiffrement et BitLocker pour** protéger les informations sur les appareils de votre organisation exécutant Windows |[Paramètres de stratégie de groupe BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings) |
|**Configurer Microsoft Defender Credential Guard pour la** protection contre les attaques par vol d’informations d’identification |[Activer Credential Guard Windows Defender à l’aide de la stratégie de groupe](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard-manage#enable-windows-defender-credential-guard-by-using-group-policy) |

## <a name="configure-your-microsoft-defender-security-center"></a>Configurer votre Centre de sécurité Microsoft Defender

Si ce n’est pas déjà fait, configurez votre Centre de sécurité **Microsoft Defender** ( ) pour afficher les alertes, configurer les fonctionnalités de protection contre les menaces et afficher des informations détaillées sur la posture de sécurité globale de votre [https://securitycenter.windows.com](https://securitycenter.windows.com) organisation. 

Vous pouvez également configurer si et quelles fonctionnalités les utilisateurs finaux peuvent voir dans le Centre de sécurité Microsoft Defender.

- [Vue d’ensemble du Centre de sécurité Microsoft Defender](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/use)

- [Protection des points de terminaison : Centre de sécurité Microsoft Defender](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Étapes suivantes

- [Obtenir une vue d’ensemble de la gestion des menaces et des vulnérabilités](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)

- [Visiter le tableau de bord des opérations de sécurité du Centre de sécurité Microsoft Defender](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/security-operations-dashboard)

- [Gérer Microsoft Defender pour le point de terminaison avec Intune](manage-atp-post-migration-intune.md)
