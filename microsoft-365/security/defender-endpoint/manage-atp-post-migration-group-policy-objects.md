---
title: Gérer Microsoft Defender pour le point de terminaison à l’aide d’objets de stratégie de groupe
description: Découvrez comment gérer Microsoft Defender pour le point de terminaison à l’aide d’objets de stratégie de groupe
keywords: post-migration, manage, operations, maintenance, utilization, PowerShell, Microsoft Defender for Endpoint, edr
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
ms.topic: article
ms.date: 09/23/2021
ms.reviewer: chventou
ms.openlocfilehash: 94eb6e7bf031a9c59fa66eb24b64298ea9a0465c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60191730"
---
# <a name="manage-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Gérer Microsoft Defender pour le point de terminaison avec des objets de stratégie de groupe

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Nous vous recommandons [d’Microsoft Endpoint Manager](/mem) pour gérer les fonctionnalités de protection contre les menaces de votre organisation pour les appareils (également appelés points de terminaison). Endpoint Manager inclut [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) et [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction). **[En savoir plus sur Endpoint Manager](/mem/endpoint-manager-overview)**.

Vous pouvez utiliser les objets de stratégie de groupe dans Azure Active Directory Domain Services pour gérer certains paramètres dans Microsoft Defender for Endpoint.

## <a name="configure-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Configurer Microsoft Defender pour le point de terminaison avec des objets de stratégie de groupe

Le tableau suivant répertorie les différentes tâches que vous pouvez effectuer pour configurer Microsoft Defender pour endpoint avec des objets de stratégie de groupe.

<br/><br/>

|Tâche|Ressources pour en savoir plus|
|---|---|
|**Gérer les paramètres des objets utilisateur et ordinateur** <br/><br/> *Personnalisez les objets de stratégie de groupe intégrés ou créez des objets de stratégie de groupe personnalisés et des unités d’organisation en fonction des besoins de votre organisation.*|[Administrer la stratégie de groupe dans un domaine Azure Active Directory services de domaine](/azure/active-directory-domain-services/manage-group-policy)|
|**Configurer Antivirus Microsoft Defender** <br/><br/> *Configurez les fonctionnalités antivirus & fonctionnalités, notamment les paramètres de stratégie, les exclusions, les corrections et les analyses programmées sur les appareils de votre organisation (également appelés points de terminaison).*|[Utiliser les paramètres de stratégie de groupe pour configurer et gérer les Antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus) <br/><br/> [Utiliser une stratégie de groupe pour activer la protection cloud](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-group-policy-to-enable-cloud-delivered-protection)|
|**Gérer les règles de réduction de la surface d’attaque de votre organisation** <br/><br/> *Personnalisez vos règles de réduction de la surface d’attaque en excluant les fichiers & dossiers, ou en ajoutant du texte personnalisé aux alertes de notification qui apparaissent sur les appareils des utilisateurs.*|[Personnaliser les règles de réduction de la surface d’attaque avec des objets de stratégie de groupe](/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction#use-group-policy-to-exclude-files-and-folders)|
|**Gérer les paramètres Exploit Protection** <br/><br/> *Vous pouvez personnaliser vos paramètres Exploit Protection, importer un fichier de configuration, puis utiliser la stratégie de groupe pour déployer ce fichier de configuration.*|[Personnaliser les paramètres Exploit Protection](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [Importer, exporter et déployer des configurations de protection contre les codes malveillants exploitant une faille de sécurité](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml) <br/><br/> [Utiliser une stratégie de groupe pour distribuer la configuration](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml#use-group-policy-to-distribute-the-configuration)|
|**Activer la Protection du réseau** pour empêcher les employés d’utiliser des applications malveillantes sur Internet <br/><br/> *Nous vous recommandons d’utiliser d’abord le [mode audit](/microsoft-365/security/defender-endpoint/evaluate-network-protection) pour la protection du réseau dans un environnement de test pour voir quelles applications seront bloquées avant le déploiement.*|[Activer la protection du réseau à l’aide de la stratégie de groupe](/microsoft-365/security/defender-endpoint/enable-network-protection#group-policy)|
|**Configurer l’accès contrôlé aux dossiers pour** la protection contre les ransomware <br/><br/> *[L’accès contrôlé aux](/microsoft-365/security/defender-endpoint/controlled-folders) dossiers est également appelé protection anti-programme malveillant.*|[Activer l’accès contrôlé aux dossiers à l’aide de la stratégie de groupe](/microsoft-365/security/defender-endpoint/enable-controlled-folders#group-policy)|
|**Configurez Microsoft Defender SmartScreen** pour vous protéger contre les sites et fichiers malveillants sur Internet.|[Configurer Microsoft Defender SmartScreen stratégie de groupe et les paramètres de gestion des périphériques mobiles (MDM) à l’aide de la stratégie de groupe](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#group-policy-settings)|
|**Configurer le chiffrement et BitLocker pour** protéger les informations sur les appareils de votre organisation en cours d’exécution Windows|[Paramètres de stratégie de groupe BitLocker](/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings)|
|**Configurer Microsoft Defender Credential Guard pour vous** protéger contre les attaques par vol d’informations d’identification|[Activer Windows Defender Credential Guard à l’aide de la stratégie de groupe](/windows/security/identity-protection/credential-guard/credential-guard-manage#enable-windows-defender-credential-guard-by-using-group-policy)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Configurer votre portail Microsoft 365 Defender client

Si ce n’est pas déjà fait, configurez votre portail Microsoft 365 Defender pour afficher les alertes, configurer les fonctionnalités de protection contre les menaces et afficher des informations détaillées sur la posture de sécurité globale de votre organisation. Voir [Microsoft 365 Defender](microsoft-defender-security-center.md). Vous pouvez également configurer si les fonctionnalités que les utilisateurs finaux peuvent voir et quelles fonctionnalités peuvent être Microsoft 365 Defender portail.

- [Vue d’ensemble Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Protection des points de terminaison : Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Étapes suivantes

- [Obtenir une vue d’ensemble de la gestion des menaces et des vulnérabilités](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Visiter le tableau de bord Microsoft 365 Defender de sécurité du portail d’entreprise](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Gérer Microsoft Defender pour le point de terminaison avec Intune](manage-atp-post-migration-intune.md)
