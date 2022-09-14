---
title: Gérer Microsoft Defender pour point de terminaison à l’aide d’objets stratégie de groupe
description: Découvrez comment gérer Microsoft Defender pour point de terminaison avec des objets stratégie de groupe
keywords: post-migration, gérer, opérations, maintenance, utilisation, PowerShell, Microsoft Defender pour point de terminaison, edr
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
- M365-security-compliance
ms.topic: article
ms.reviewer: chventou
search.appverid: met150
ms.openlocfilehash: 15b38fc6e667996a88a793ae25fcc4efdb14f890
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67688460"
---
# <a name="manage-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Gérer Microsoft Defender pour point de terminaison avec des objets stratégie de groupe

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Nous vous recommandons d’utiliser [Microsoft Endpoint Manager](/mem) pour gérer les fonctionnalités de protection contre les menaces de votre organisation pour les appareils (également appelés points de terminaison). Endpoint Manager inclut [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) et [Configuration Manager de point de terminaison Microsoft](/mem/configmgr/core/understand/introduction). **[En savoir plus sur Endpoint Manager](/mem/endpoint-manager-overview)**.

Vous pouvez utiliser stratégie de groupe Objects dans Azure services de domaine Active Directory pour gérer certains paramètres dans Microsoft Defender pour point de terminaison.

## <a name="configure-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Configurer Microsoft Defender pour point de terminaison avec des objets stratégie de groupe

> [!NOTE]
> Si vous utilisez [la nouvelle solution de Microsoft Defender pour point de terminaison unifiée pour Windows Server 2012 R2 et 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview), vérifiez que vous utilisez les derniers fichiers ADMX dans votre magasin central pour accéder au bon Microsoft Defender pour point de terminaison options de stratégie. Reportez-vous [à la rubrique How to create and manage the Central Store for stratégie de groupe Administrative Templates in Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) et téléchargez les derniers fichiers **à utiliser avec Windows 10**. 

Le tableau suivant répertorie les différentes tâches que vous pouvez effectuer pour configurer Microsoft Defender pour point de terminaison avec stratégie de groupe Objects.

|Tâche|Ressources pour en savoir plus|
|---|---|
|**Gérer les paramètres des objets utilisateur et ordinateur** <br/><br/> *Personnalisez les objets stratégie de groupe intégrés ou créez des objets stratégie de groupe personnalisés et des unités d’organisation en fonction des besoins de votre organisation.*|[Administrer stratégie de groupe dans un domaine managé Azure services de domaine Active Directory](/azure/active-directory-domain-services/manage-group-policy)|
|**Configurer l’antivirus Microsoft Defender** <br/><br/> *Configurez les fonctionnalités antivirus & fonctionnalités, notamment les paramètres de stratégie, les exclusions, les corrections et les analyses planifiées sur les appareils de votre organisation (également appelés points de terminaison).*|[Utiliser stratégie de groupe paramètres pour configurer et gérer l’antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus) <br/><br/> [Utiliser stratégie de groupe pour activer la protection fournie par le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-group-policy-to-enable-cloud-delivered-protection)|
|**Gérer les règles de réduction de la surface d’attaque de votre organisation** <br/><br/> *Personnalisez vos règles de réduction de la surface d’attaque en excluant les fichiers & dossiers ou en ajoutant du texte personnalisé aux alertes de notification qui apparaissent sur les appareils des utilisateurs.*|[Personnaliser les règles de réduction de la surface d’attaque avec des objets stratégie de groupe](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment-implement)|
|**Gérer les paramètres de protection contre les attaques** <br/><br/> *Vous pouvez personnaliser vos paramètres exploit protection, importer un fichier de configuration, puis utiliser stratégie de groupe pour déployer ce fichier de configuration.*|[Personnaliser les paramètres de protection contre les attaques](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [Importer, exporter et déployer des configurations de protection contre les codes malveillants exploitant une faille de sécurité](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml) <br/><br/> [Utiliser stratégie de groupe pour distribuer la configuration](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml#use-group-policy-to-distribute-the-configuration)|
|**Activer la protection réseau** pour empêcher les employés d’utiliser des applications qui utilisent du contenu malveillant sur Internet <br/><br/> *Nous vous recommandons d’utiliser d’abord le [mode audit](/microsoft-365/security/defender-endpoint/evaluate-network-protection) pour la protection réseau dans un environnement de test pour voir quelles applications seraient bloquées avant le déploiement.*|[Activer la protection réseau à l’aide de stratégie de groupe](/microsoft-365/security/defender-endpoint/enable-network-protection#group-policy)|
|**Configurer l’accès contrôlé aux dossiers** pour vous protéger contre les ransomware <br/><br/> *[L’accès contrôlé aux dossiers](/microsoft-365/security/defender-endpoint/controlled-folders) est également appelé protection antiransomware.*|[Activer l’accès contrôlé aux dossiers à l’aide de stratégie de groupe](/microsoft-365/security/defender-endpoint/enable-controlled-folders#group-policy)|
|**Configurez Microsoft Defender SmartScreen** pour vous protéger contre les sites et fichiers malveillants sur Internet.|[Configurer les paramètres de gestion des appareils mobiles et stratégie de groupe Microsoft Defender SmartScreen à l’aide de stratégie de groupe](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#group-policy-settings)|
|**Configurer le chiffrement et BitLocker** pour protéger les informations sur les appareils de votre organisation exécutant Windows|[Paramètres de stratégie de groupe BitLocker](/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings)|
|**Configurer Microsoft Defender Credential Guard** pour vous protéger contre les attaques par vol d’informations d’identification|[Activer Windows Defender Credential Guard à l’aide de stratégie de groupe](/windows/security/identity-protection/credential-guard/credential-guard-manage#enable-windows-defender-credential-guard-by-using-group-policy)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Configurer votre portail Microsoft 365 Defender

Si vous ne l’avez pas encore fait, configurez votre portail Microsoft 365 Defender pour afficher les alertes, configurer les fonctionnalités de protection contre les menaces et afficher des informations détaillées sur la posture de sécurité globale de votre organisation. Voir [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Vous pouvez également configurer si et quelles fonctionnalités les utilisateurs finaux peuvent voir dans le portail Microsoft 365 Defender.

- [Vue d’ensemble de Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Endpoint Protection : Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Prochaines étapes

- [Obtenir une vue d’ensemble de La gestion des vulnérabilités defender](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Visitez le tableau de bord des opérations de sécurité du portail Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Gérer Microsoft Defender pour point de terminaison avec Intune](manage-mde-post-migration-intune.md)
