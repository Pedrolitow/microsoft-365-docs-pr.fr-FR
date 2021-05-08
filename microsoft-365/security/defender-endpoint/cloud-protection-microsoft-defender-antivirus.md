---
title: Protection par le cloud et antivirus Microsoft Defender
description: En savoir plus sur la protection et les Antivirus Microsoft Defender
keywords: Antivirus Microsoft Defender, technologies de nouvelle génération, antivirus de nouvelle génération, apprentissage automatique, logiciel anti-programme malveillant, sécurité, defender, cloud, protection cloud
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.reviewer: shwjha
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.openlocfilehash: d95f8dec433f29dea0fd5f7f718f34f571b790d4
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52274807"
---
# <a name="use-next-generation-technologies-in-microsoft-defender-antivirus-through-cloud-delivered-protection"></a>Utiliser les technologies de nouvelle génération dans Antivirus Microsoft Defender via une protection cloud

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)
- Antivirus Microsoft Defender

Les technologies microsoft de nouvelle génération Antivirus Microsoft Defender fournissent une protection automatisée et quasi instantanée contre les menaces nouvelles et émergentes. Pour identifier de façon dynamique les nouvelles menaces, ces technologies fonctionnent avec de grands ensembles de données interconnectées dans Microsoft intelligent Security Graph et des systèmes d’intelligence artificielle (IA) performants basés sur des modèles d’apprentissage automatique.  

Antivirus Microsoft Defender utilise plusieurs technologies de détection et de prévention pour offrir une protection précise, en temps réel et intelligente. Faire connaître les technologies avancées au cœur de Microsoft Defender pour la protection nouvelle génération de point de [terminaison.](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)
![Liste des moteurs de Microsoft Defender AV](images/microsoft-defender-atp-next-generation-protection-engines.png)  

Pour tirer parti de la puissance et de la vitesse de ces technologies de nouvelle génération, Antivirus Microsoft Defender fonctionne en toute transparence avec les services cloud de Microsoft. Ces services de protection cloud, également appelés Microsoft Advanced Protection Service (MAPS), améliorent la protection en temps réel standard, offrant sans doute la meilleure défense antivirus. 

>[!NOTE]
>Le Antivirus Microsoft Defender cloud est un mécanisme permettant de fournir une protection mise à jour à votre réseau et points de terminaison. Bien qu’il soit appelé service cloud, il ne s’agit pas simplement de la protection des fichiers stockés dans le cloud, mais plutôt de l’utilisation de ressources distribuées et d’apprentissage automatique pour fournir une protection à vos points de terminaison à une vitesse beaucoup plus rapide que les mises à jour d’informations de sécurité traditionnelles.

Grâce à la protection fournie par le cloud, les technologies de nouvelle génération permettent d’identifier rapidement les nouvelles menaces, parfois même avant l’infection d’un seul ordinateur. Regardez la vidéo suivante sur Microsoft AI et Antivirus Microsoft Defender en action : 
 
<iframe 
src="https://www.microsoft.com/videoplayer/embed/RE1Yu4B" width="768" height="432" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>

Pour comprendre comment les technologies de nouvelle génération raccourcissent le temps de livraison de la protection via le cloud, regardez la vidéo suivante : 
 
<iframe 
src="https://videoplayercdn.osi.office.net/embed/c2f20f59-ca56-4a7b-ba23-44c60bc62c59" width="768" height="432" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>

Lisez les billets de blog suivants pour obtenir des informations détaillées sur la protection du cloud et l’IA Microsoft : 

- [Pourquoi Antivirus Microsoft Defender est le plus déployé dans l’entreprise](https://www.microsoft.com/security/blog/2018/03/22/why-windows-defender-antivirus-is-the-most-deployed-in-the-enterprise) 
- [La surveillance du comportement combinée à l’apprentissage automatique a pour effet de dérégléer une campagne d’exploration de pièces dofoils massive](https://www.microsoft.com/security/blog/2018/03/07/behavior-monitoring-combined-with-machine-learning-spoils-a-massive-dofoil-coin-mining-campaign)
- [Comment l’intelligence artificielle a arrêté une épidémie d’emotet](https://www.microsoft.com/security/blog/2018/02/14/how-artificial-intelligence-stopped-an-emotet-outbreak)
- [Désa malfaiteur : défenses Antivirus Microsoft Defender d’apprentissage machine à couches](https://www.microsoft.com/security/blog/2017/12/11/detonating-a-bad-rabbit-windows-defender-antivirus-and-layered-machine-learning-defenses)
- [Antivirus Microsoft Defender service de protection cloud : défense avancée en temps réel contre les programmes malveillants jamais vus](https://www.microsoft.com/security/blog/2017/07/18/windows-defender-antivirus-cloud-protection-service-advanced-real-time-defense-against-never-before-seen-malware) 
 
## <a name="get-cloud-delivered-protection"></a>Obtenir une protection cloud 

La protection cloud est activée par défaut. Toutefois, vous devrez peut-être le réactiver s’il a été désactivé dans le cadre des stratégies organisationnelles précédentes.

Les organisations exécutant Windows 10 E5 peuvent également tirer parti des mises à jour d’urgence de l’intelligence dynamique, qui offrent une protection quasi en temps réel contre les menaces émergentes. Lorsque vous mettez en place la protection cloud, les correctifs aux problèmes de programmes malveillants peuvent être remis via le cloud en quelques minutes, au lieu d’attendre la prochaine mise à jour.

>[!TIP]
>Vous pouvez également consulter le site web Windows Defender Testground sur [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que la fonctionnalité fonctionne et voir comment elle fonctionne.

Le tableau suivant décrit les différences entre les versions récentes d’Windows et configuration Manager en matière de protection dans le cloud.

|Version du système d’exploitation ou application de service |Étiquette de service de protection cloud  |Niveau de rapport (niveau d’appartenance MAPS)  |Délai d’attente de blocage du cloud  |
|---------|---------|---------|---------|
|Windows 8.1 (stratégie de groupe)     |Microsoft Advanced Protection Service   |De base, avancé   |Non         |
|Windows 10, version 1607 (stratégie de groupe)  |Microsoft Advanced Protection Service      |Avancé         |Non         |
|Windows 10, version 1703 ou supérieure (stratégie de groupe)      |Protection basée sur le cloud      |Avancé         |Configurable         |
|Gestionnaire de configuration System Center 2012  |      S/O         |Dépendant de Windows version         |Non configurable |
|Microsoft Endpoint Manager (Current Branch)         |Service de protection cloud         |Dépendant de Windows version          |Configurable         |
|Microsoft Intune     |Microsoft Advanced Protection Service         |Dépendant de Windows version         |Configurable         |

Vous pouvez également configurer Antivirus Microsoft Defender pour recevoir automatiquement de nouvelles mises à jour de protection basées sur les [rapports de notre service cloud.](manage-event-based-updates-microsoft-defender-antivirus.md#cloud-report-updates)


## <a name="tasks"></a>Tâches

- [Activer la protection cloud.](enable-cloud-protection-microsoft-defender-antivirus.md) Vous pouvez activer la protection cloud avec les cmdlets Microsoft Endpoint Configuration Manager, stratégie de groupe, Microsoft Intune et PowerShell.

- [Spécifiez le niveau de protection remis par le cloud.](specify-cloud-protection-level-microsoft-defender-antivirus.md) Vous pouvez spécifier le niveau de protection proposé par le cloud avec la stratégie de groupe et Microsoft Endpoint Configuration Manager. Le niveau de protection affecte la quantité d’informations partagées avec le cloud et le blocage agressif des nouveaux fichiers.

- [Configurez et validez les connexions réseau pour Antivirus Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md). Votre réseau et vos points de terminaison doivent pouvoir se connecter à certaines URL Microsoft pour que la protection cloud fonctionne efficacement. Cet article répertorie les URL qui doivent être autorisées via le pare-feu ou les règles de filtrage réseau, et des instructions pour vérifier que votre réseau est correctement inscrit dans la protection cloud.

- [Configurez la fonctionnalité bloquer à la première vue.](configure-block-at-first-sight-microsoft-defender-antivirus.md) La fonctionnalité « Bloquer à la première vue » peut bloquer les nouveaux programmes malveillants en quelques secondes, sans avoir à attendre les heures d’attente des renseignements de sécurité traditionnels. Vous pouvez l’activer et le configurer à l’Microsoft Endpoint Manager stratégie de groupe.

- [Configurez le délai d’attente du blocage du cloud.](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md) Antivirus Microsoft Defender bloquer l’exécution de fichiers suspects pendant qu’il interroge notre service de protection livré par le cloud. Vous pouvez configurer la durée d’exécution du fichier avec les stratégies Microsoft Endpoint Manager groupe.