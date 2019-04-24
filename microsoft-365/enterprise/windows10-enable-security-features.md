---
title: Déployer les fonctionnalités de sécurité Windows 10 Entreprise
description: Fournit un guide de haut niveau sur les étapes à suivre pour déployer Windows 10 Entreprise sur les ordinateurs dans le cadre de Microsoft 365 Entreprise.
keywords: Microsoft 365, Microsoft 365 entreprise, documentation Microsoft 365, Windows 10 entreprise, sécurité
author: greg-lindsay
localization_priority: Normal
ms.collection: M365-modern-desktop
audience: microsoft-business
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 06/01/2018
ms.author: greglin
ms.openlocfilehash: 60145444a7fb2b4ddf2ea6a3606e04aa04a578af
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32291621"
---
# <a name="step-5-deploy-windows-10-enterprise-security-features"></a>Étape 5: déployer les fonctionnalités de sécurité Windows 10 entreprise

![](./media/deploy-foundation-infrastructure/win10enterprise_icon-small.png)

Windows 10 offre des fonctionnalités de sécurité pour protéger les utilisateurs de l'entreprise, arrêter Cyber et empêcher la perte de données. 

Pour en savoir plus sur ces technologies, consultez les informations suivantes:
* [Protection](https://docs.microsoft.com/windows/security/identity-protection/) des identités: Découvrez Windows Hello entreprise, Credential Guard et le contrôle d'accès.
* [Protection contre les menaces](https://docs.microsoft.com/windows/threat-protection/) : Découvrez Windows Defender Advanced Threat Protection, une plateforme unifiée pour la protection préventive, la détection après effraction, l'enquête automatisée et la réponse.
* [Protection des informations](https://docs.microsoft.com/windows/security/information-protection/) : Découvrez BitLocker, la protection des informations Windows et d'autres façons pour Windows 10 de protéger les données d'entreprise. 

Cette étape vous explique comment déployer, gérer, configurer et résoudre les problèmes à l'aide des fonctionnalités de sécurité suivantes:

* [Antivirus Windows Defender](#windows-defender-antivirus)
* [Windows Defender Exploit Guard](#windows-defender-exploit-guard)
* [Windows Defender Advanced Threat Protection](#windows-defender-advanced-threat-protection)

<a name="windows10-sec-av"></a>
## <a name="windows-defender-antivirus"></a>Antivirus Windows Defender
L'antivirus Windows Defender (AV) est une solution de logiciel anti-programme malveillant intégrée dans Windows 10. Il offre la gestion de la sécurité et du logiciel anti-programme malveillant pour les ordinateurs de bureau, les ordinateurs portables et les serveurs. Pour plus d'informations sur Windows Defender AV, la configuration minimale requise et la façon dont vous pouvez gérer cette fonctionnalité, voir [antivirus Windows Defender dans Windows 10 et Windows Server 2016](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10).

Si vous n'utilisez pas l'antivirus Windows Defender comme votre client antivirus principal, ou si vous utilisez également Windows Defender ATP, certaines considérations doivent être prises en compte. Pour en savoir plus, consultez la rubrique [Windows Defender AV Compatibility](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-compatibility).

### <a name="deployment-and-management"></a>Déploiement et gestion
Pour déployer et gérer l'antivirus Windows Defender, suivez les conseils ci-dessous:

* [Déployer, gérer et signaler sur les antivirus Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/deploy-manage-report-windows-defender-antivirus)
* [Rubriques de référence pour les outils de gestion et de configuration](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/configuration-management-reference-windows-defender-antivirus)

### <a name="configuration"></a>Configuration
Les utilisateurs peuvent configurer un certain nombre de fonctionnalités. Pour plus d'informations, consultez les ressources suivantes:

* [Configurer les fonctionnalités de l'antivirus Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)
* [Rubriques de référence pour les outils de gestion et de configuration](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/configuration-management-reference-windows-defender-antivirus)

Pour mieux comprendre les options de configuration, reportez-vous à la liste de tous les paramètres (tel que défini par la configuration de la stratégie de groupe): utiliser les paramètres de la [stratégie de groupe pour configurer et gérer l'antivirus Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/use-group-policy-windows-defender-antivirus)

Vous pouvez utiliser le [Guide d'évaluation de la protection antivirus Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/evaluate-windows-defender-antivirus) pour vous aider à évaluer le niveau de protection et l'impact de Windows Defender AV sur votre réseau. Cela peut également être utile lors de la création d'une configuration initiale ou d'un «guide de démarrage rapide» et est régulièrement mis à jour pour fournir les recommandations les plus utiles pour la configuration et l'activation des fonctionnalités afin de garantir une protection maximale.

### <a name="reporting"></a>Reporting
Vous pouvez obtenir des rapports à l'aide d'un outil de configuration, tel que System Center Configuration Manager ou Microsoft Intune. Vous pouvez également obtenir des rapports à partir de la conformité des mises à jour (OMS) ou en utilisant des journaux des événements Windows dans votre SIEM. Si vous disposez d'une licence pour Windows Defender ATP, vous pouvez également obtenir des rapports sur les détections AV Windows Defender et effectuer des corrections de base. Pour plus d'informations, consultez les ressources suivantes:
* [Déployer, gérer et signaler sur les antivirus Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/deploy-manage-report-windows-defender-antivirus)
* [Rapport sur la protection antivirus Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/report-monitor-windows-defender-antivirus)
* [Vue d'ensemble du portail Windows Defender ATP](https://go.microsoft.com/fwlink/?linkid=861596)

### <a name="troubleshooting"></a>Résolution des problèmes
Pour plus d'informations sur la résolution des problèmes de base des codes d'erreur et d'événement, consultez la rubrique [Review event logs and Error Codes to Troubleshoot Problems with Windows Defender AV](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

Vous pouvez également soumettre des problèmes (tels que des faux positifs) à l'aide du système de soumission Windows Defender Security Intelligence. Pour savoir comment procéder, consultez la rubrique [soumettre des problèmes à Microsoft](https://www.microsoft.com/wdsi/filesubmission).

<a name="windows10-sec-eg"></a>
## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard
Windows Defender exploit Guard est un nouvel ensemble de fonctionnalités de prévention des intrusions sur l'hôte pour Windows 10. Pour plus d'informations sur Windows Defender exploit Guard, la configuration minimale requise et la façon dont vous pouvez gérer cette fonctionnalité, voir [Windows Defender exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard).

### <a name="deployment-management-and-configuration"></a>Déploiement, gestion et configuration
Pour déployer, gérer et configurer Windows Defender exploit Guard, suivez les conseils ci-dessous:
* [Protection contre les attaques](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/exploit-protection-exploit-guard)
* [Protection de surface d'attaque](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard?ocid=cx-docs-msa4053440)
* [Protection réseau](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/network-protection-exploit-guard)
* [Accès contrôlé aux dossiers](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard)

Vous pouvez utiliser une série de rubriques d'évaluation pour évaluer le niveau de protection et l'impact de Windows Defender exploit Guard sur votre réseau. Cela peut également être utile lors de la création d'une configuration initiale ou d'un «guide de démarrage rapide», et les rubriques et conseils sont régulièrement mis à jour pour fournir les recommandations les plus utiles en matière de configuration et d'activation des fonctionnalités pour garantir une protection maximale. Pour plus d'informations, [évaluEz Windows Defender exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/evaluate-windows-defender-exploit-guard).

### <a name="reporting"></a>Reporting
Vous pouvez obtenir la création de rapports à l'aide d'un outil de configuration, tel que System Center Configuration Manager ou Intune. Vous pouvez également obtenir des rapports en utilisant des journaux des événements Windows dans votre SIEM. Si vous disposez d'une licence pour Windows Defender ATP, vous pouvez également obtenir des rapports sur les détections AV Windows Defender et effectuer des corrections de base. Pour plus d'informations, consultez les ressources suivantes:
* [Afficher les événements Windows Defender exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/event-views-exploit-guard)
* [Vue d'ensemble du portail Windows Defender ATP](https://go.microsoft.com/fwlink/?linkid=861596)

### <a name="troubleshooting"></a>Résolution des problèmes
Vous pouvez effectuer un dépannage de base ou éventuellement fournir à Microsoft des fichiers. cab et soumettre des problèmes (tels que des faux positifs) à l'aide du système de soumission Windows Defender Security Intelligence. Pour savoir comment procéder, consultez la rubrique [soumettre des problèmes à Microsoft](https://www.microsoft.com/wdsi/filesubmission).


<a name="windows10-sec-atp"></a>
## <a name="windows-defender-advanced-threat-protection"></a>Windows Defender Advanced Threat Protection
Windows Defender ATP (disponible uniquement avec le plan Microsoft 365 entreprise E5) est un service de sécurité qui permet aux clients d'entreprise de détecter, d'examiner et de répondre aux menaces avancées sur leurs réseaux. Pour plus d'informations sur Windows Defender ATP, la configuration minimale requise et la façon dont vous pouvez gérer cette fonctionnalité, voir:

* [Windows Defender ATP](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)
* [Configuration minimale requise](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/minimum-requirements-windows-defender-advanced-threat-protection)

### <a name="deployment-management-and-configuration"></a>Déploiement, gestion et configuration
Pour déployer Windows Defender ATP, vous devez vous assurer que vous disposez de la bonne licence Windows. Après avoir vérifié que vous disposez de la licence appropriée, vous devez décider de la géolocalisation de l'emplacement de stockage de vos données. Après cela, vous pouvez démarrer les points de terminaison d'intégration au service.

Pour plus d'informations sur ces étapes, consultez les rubriques principales suivantes: 

* [Validation de la mise en service et de la configuration complète des licences](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/licensing-windows-defender-advanced-threat-protection)
* [Stockage et confidentialité des données](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/data-storage-privacy-windows-defender-advanced-threat-protection)
* [Points de terminaison intégrés et accès au programme d'installation](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/onboard-configure-windows-defender-advanced-threat-protection)

### <a name="detect-investigate-respond"></a>Détecter, examiner, répondre
Après avoir correctement installé les points de terminaison sur le service, vous pouvez commencer à rechercher des alertes à partir des différents tableaux de bord. Une fois que vous avez analysé les alertes, vous pouvez prendre des mesures d'action sur les alertes. 

Pour plus d'informations sur la façon de procéder, voir:
* [Vue d'ensemble du portail Windows Defender ATP](https://go.microsoft.com/fwlink/?linkid=861596)
* [Utiliser le portail Windows Defender ATP](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/use-windows-defender-advanced-threat-protection)
* [Effectuer des actions de réponse](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/response-actions-windows-defender-advanced-threat-protection)

### <a name="integrate-with-other-products-and-tools"></a>Intégration à d'autres produits et outils
Windows Defender ATP intègre et prend en charge divers autres produits et outils pour développer ses fonctionnalités de sécurité. 

Pour plus d'informations sur les outils et les autres produits, consultez les articles suivants:
* [Outils SIEM](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/configure-siem-windows-defender-advanced-threat-protection)
* [Créer des alertes personnalisées](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/use-custom-ti-windows-defender-advanced-threat-protection)
* [Utiliser les API](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/exposed-apis-windows-defender-advanced-threat-protection)
* [Générer des rapports Power BI](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/powerbi-reports-windows-defender-advanced-threat-protection)

### <a name="troubleshooting"></a>Résolution des problèmes
Vous pouvez rencontrer des problèmes lors de l'intégration ou lors de l'utilisation du produit. Pour plus d'informations sur la résolution des problèmes, voir:
* [Résolution des problèmes d'intégration](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/troubleshoot-onboarding-windows-defender-advanced-threat-protection)
* [Dépannage de Windows Defender ATP](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/troubleshoot-windows-defender-advanced-threat-protection)

## <a name="next-step"></a>Étape suivante

[Critères de sortie de l'infrastructure Windows 10 entreprise](windows10-exit-criteria.md)
