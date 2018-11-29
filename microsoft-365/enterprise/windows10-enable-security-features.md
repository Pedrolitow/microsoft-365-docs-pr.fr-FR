---
title: Déployer les fonctionnalités de sécurité Windows 10 Entreprise
description: Fournit un guide de haut niveau sur les étapes à suivre pour déployer Windows 10 Entreprise sur les ordinateurs dans le cadre de Microsoft 365 Entreprise.
keywords: Sécurité de documentation, Windows 10 entreprise, Microsoft 365, Microsoft 365 pour entreprises, Microsoft 365
author: greg-lindsay
localization_priority: Normal
audience: microsoft-business
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 06/01/2018
ms.author: greglin
ms.openlocfilehash: d051f9e56d8e9986fbe0975c2bdc6c606b32a444
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867479"
---
# <a name="step-5-deploy-windows-10-enterprise-security-features"></a>Étape 5 : Déployer des fonctionnalités de sécurité Windows 10 Entreprise

![](./media/deploy-foundation-infrastructure/win10enterprise_icon-small.png)

Windows 10 fournit des fonctionnalités pour vous aider à protéger contre les menaces, aide sécuriser vos périphériques et vous aider avec contrôle d’accès. 

Pour en savoir plus sur ces technologies, voir :
* [Protection d’accès](https://docs.microsoft.com/windows/access-protection/) : en savoir plus sur l’accès au contrôle S/MIME, des certificats numériques, protection des informations d’identification, contrôle de compte d’utilisateur, virtuel cartes à puce, Windows Hello pour l’entreprise, le pare-feu Windows avec fonctions avancées de sécurité et bien plus encore
* [Sécurité des périphériques](https://docs.microsoft.com/windows/device-security/) - AppLocker inclut, BitLocker, Guard périphérique et TPM
* [Protection contre les menaces](https://docs.microsoft.com/windows/threat-protection/) - inclut le centre de sécurité Windows Defender, contre les menaces avancées Windows Defender, Windows Defender Antivirus, Windows Defender Application Guard, Windows Defender actives écran et Protection des informations

Cette étape vous montre comment déployer, gérer, configurer et résoudre les problèmes à l’aide de ces fonctionnalités de sécurité :

* [Antivirus Windows Defender](#windows-defender-antivirus)
* [Windows Defender Exploit Guard](#windows-defender-exploit-guard)
* [Windows Defender Advanced Threat Protection](#windows-defender-advanced-threat-protection)

<a name="windows10-sec-av"></a>
## <a name="windows-defender-antivirus"></a>Antivirus Windows Defender
Windows Defender Antivirus (AV) est une solution anti-programme malveillant intégrée à Windows 10. Il fournit la sécurité et gestion de logiciels anti-programmes malveillants pour les ordinateurs de bureau, des ordinateurs portables et serveurs. Pour plus d’informations sur Windows Defender AV, la configuration minimale requise et comment vous pouvez gérer cette fonctionnalité, voir [Windows Defender Antivirus dans 10 Windows et Windows Server 2016](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10).

Si vous n’utilisez pas Windows Defender AV comme client principal antiviru, ou si vous utilisez également Windows Defender DAV, il existe certaines considérations, vous devez prendre en compte. Pour plus d’informations, voir [compatibilité Windows Defender AV](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-compatibility).

### <a name="deployment-and-management"></a>Déploiement et gestion
Pour déployer et gérer Windows Defender AV, suivez les instructions ici :

* [Déployer, gérer et créer des rapports sur Windows Defender AV](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/deploy-manage-report-windows-defender-antivirus)
* [Rubriques de référence pour les outils de gestion et de configuration](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/configuration-management-reference-windows-defender-antivirus)

### <a name="configuration"></a>Configuration
Les utilisateurs peuvent configurer un certain nombre de fonctionnalités. Pour plus d’informations, consultez les ressources suivantes :

* [Configurer les fonctionnalités Windows Defender AV](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)
* [Rubriques de référence pour les outils de gestion et de configuration](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/configuration-management-reference-windows-defender-antivirus)

Pour vous aider à comprendre les options de configuration, reportez-vous à la liste de tous les paramètres (tel que défini par leur configuration de la stratégie de groupe) : [paramètres d’utiliser la stratégie de groupe pour configurer et gérer Windows Defender AV](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/use-group-policy-windows-defender-antivirus)

Vous pouvez utiliser la [protection Windows Defender AV Guide d’évaluation](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/evaluate-windows-defender-antivirus) pour aider à évaluer le niveau de protection et l’impact de Windows Defender AV sur votre réseau. Cela peut également être utile lors de la création d’une configuration initiale ou en tant que « guide de démarrage rapide » et est régulièrement mis à jour pour fournir les recommandations les plus utiles pour la configuration et l’activation des fonctionnalités assurer une protection maximale.

### <a name="reporting"></a>Création de rapports
Vous pouvez obtenir la création de rapports à l’aide d’un outil de configuration, tel que System Center Configuration Manager ou Microsoft Intune. Vous pouvez également obtenir la création de rapports à partir de la mise à jour de conformité (OMS) ou à l’utilisation des journaux des événements Windows dans votre SIEM. Si vous disposez d’une licence pour Windows Defender DAV, vous pouvez également obtenir la création de rapports à des détections de Windows Defender AV et conversion de base. Pour plus d’informations, consultez les ressources suivantes :
* [Déployer, gérer et créer des rapports sur Windows Defender AV](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/deploy-manage-report-windows-defender-antivirus)
* [Créer des rapports sur la protection de Windows Defender AV](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/report-monitor-windows-defender-antivirus)
* [Vue d’ensemble du portail Windows Defender DAV](https://go.microsoft.com/fwlink/?linkid=861596)

### <a name="troubleshooting"></a>Résolution des problèmes
Pour obtenir des informations sur le dépannage de base des codes d’erreur et d’événements, voir [codes d’erreur pour résoudre les problèmes liés à Windows Defender AV et de passer en revue les journaux des événements](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

Vous pouvez également envoyer des problèmes (tels que le nombre de faux positifs) en utilisant le système de soumission d’aide à la décision de Windows Defender sécurité. Pour en savoir plus, voir [problèmes envoyer à Microsoft](https://www.microsoft.com/wdsi/filesubmission).

<a name="windows10-sec-eg"></a>
## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard
Protection contre les exploiter Windows Defender est un nouvel ensemble de fonctionnalités de prévention des intrusions hôte pour Windows 10. Pour plus d’informations sur Windows Defender exploiter Guard, la configuration minimale requise et comment vous pouvez gérer cette fonctionnalité, voir [Windows Defender exploiter Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard).

### <a name="deployment-management-and-configuration"></a>Déploiement et gestion de configuration
Pour déployer, gérer et configurer Windows Defender exploiter Guard, suivez les instructions ici :
* [Protection contre les risques](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/exploit-protection-exploit-guard)
* [Protection de surface d’attaque](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard?ocid=cx-docs-msa4053440)
* [Protection du réseau](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/network-protection-exploit-guard)
* [Sous contrôle d’accès au dossier](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard)

Vous pouvez utiliser une série de rubriques d’évaluation pour aider à évaluer le niveau de protection et l’impact de la protection contre les exploiter Windows Defender sur votre réseau. Cela peut également être utile lors de la création d’une configuration initiale ou en tant que « guide de démarrage rapide » et les rubriques et les conseils sont régulièrement mis à jour pour fournir les recommandations les plus utiles pour la configuration et l’activation des fonctionnalités assurer une protection maximale. Pour plus d’informations, [Guard d’exploiter Windows Defender évaluer](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/evaluate-windows-defender-exploit-guard).

### <a name="reporting"></a>Création de rapports
Vous pouvez obtenir la création de rapports à l’aide d’un outil de configuration, tel que System Center Configuration Manager ou Intune. Vous pouvez également obtenir la création de rapports en consommant des journaux des événements Windows dans votre SIEM. Si vous disposez d’une licence pour Windows Defender DAV, vous pouvez également obtenir la création de rapports à des détections de Windows Defender AV et conversion de base. Pour plus d’informations, consultez les ressources suivantes :
* [Afficher les événements de Windows Defender exploiter Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/event-views-exploit-guard)
* [Vue d’ensemble du portail Windows Defender DAV](https://go.microsoft.com/fwlink/?linkid=861596)

### <a name="troubleshooting"></a>Résolution des problèmes
Vous pouvez résoudre des problèmes de base ou éventuellement fournir à Microsoft les fichiers .cab et signaler les problèmes (tels que le nombre de faux positifs) en utilisant le système de soumission d’aide à la décision de Windows Defender sécurité. Pour en savoir plus, voir [problèmes envoyer à Microsoft](https://www.microsoft.com/wdsi/filesubmission).


<a name="windows10-sec-atp"></a>
## <a name="windows-defender-advanced-threat-protection"></a>Windows Defender Advanced Threat Protection
Disponible uniquement avec le plan de Microsoft 365 entreprise E5, Windows Defender DAV est un service de sécurité qui permet aux clients d’entreprise à détecter, examiner et répondre aux menaces sur leurs réseaux. Pour plus d’informations sur Windows Defender DAV, la configuration minimale requise et comment vous pouvez gérer cette fonctionnalité, voir :

* [Windows Defender ATP](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)
* [Configuration minimale requise](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/minimum-requirements-windows-defender-advanced-threat-protection)

### <a name="deployment-management-and-configuration"></a>Déploiement et gestion de configuration
Pour déployer Windows Defender DAV, vous devez disposer le droit de licence de Windows. Après avoir vérifié que vous disposez de la licence de droite, vous devez décider de la géolocalisation pour où vos données seront stockées. Après cela, vous pouvez démarrer l’intégration des points de terminaison du service.

Pour plus d’informations sur ces étapes, voir les rubriques principales : 

* [Valider la mise en service de gestion des licences et terminée](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/licensing-windows-defender-advanced-threat-protection)
* [Confidentialité et stockage des données](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/data-storage-privacy-windows-defender-advanced-threat-protection)
* [Points de terminaison intégrées et l’accès du programme d’installation](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/onboard-configure-windows-defender-advanced-threat-protection)

### <a name="detect-investigate-respond"></a>Détecter, examiner, répondre
Après avoir correctement embarquement points de terminaison au service, vous pouvez démarrer examen aux alertes dans les tableaux de bord différents. Une fois que vous avez examiné les alertes, vous pouvez effectuer les actions de réponse sur alertes. 

Pour plus d’informations sur la façon d’effectuer les opérations suivantes, voir :
* [Vue d’ensemble du portail Windows Defender DAV](https://go.microsoft.com/fwlink/?linkid=861596)
* [Utiliser le portail Windows Defender DAV](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/use-windows-defender-advanced-threat-protection)
* [Effectuer des actions de réponse](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/response-actions-windows-defender-advanced-threat-protection)

### <a name="integrate-with-other-products-and-tools"></a>Intégration avec d’autres produits et les outils
Windows Defender DAV intègre et prend en charge divers autres outils pour étendre ses fonctionnalités de sécurité et produits. 

Pour plus d’informations sur les outils et d’autres produits, voir :
* [Outils SIEM](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/configure-siem-windows-defender-advanced-threat-protection)
* [Créer des alertes personnalisées](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/use-custom-ti-windows-defender-advanced-threat-protection)
* [Utilisation des API](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/exposed-apis-windows-defender-advanced-threat-protection)
* [Générer des rapports Power BI](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/powerbi-reports-windows-defender-advanced-threat-protection)

### <a name="troubleshooting"></a>Résolution des problèmes
Vous pouvez rencontrer des problèmes pendant embarquement ou l’utilisation du produit. Pour plus d’informations sur la façon de résoudre les problèmes, consultez :
* [Résolution des problèmes d’intégration](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/troubleshoot-onboarding-windows-defender-advanced-threat-protection)
* [Dépannage de Windows Defender DAV](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/troubleshoot-windows-defender-advanced-threat-protection)

## <a name="next-step"></a>Étape suivante

[Critères de sortie de l’infrastructure Windows 10 Enterprise](windows10-exit-criteria.md)
