---
title: 'Informations sur les tableaux de bord : gestion des menaces et des vulnérabilités'
description: Le tableau de bord de gestion des menaces et des vulnérabilités peut aider SecOps et les administrateurs de sécurité à gérer les menaces de cybersécurité et à renforcer la résilience de sécurité de leur organisation.
keywords: Microsoft Defender pour Endpoint-tvm, tableau de bord Microsoft Defender pour Endpoint-tvm, gestion des vulnérabilités des & menaces, gestion des menaces et vulnérabilités, gestion des vulnérabilités des & menaces basée sur les risques, configuration de la sécurité, Degré de sécurisation Microsoft pour les appareils, score d'exposition
search.appverid: met150
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 82b6123a99eb406918708c6bf23b870ef3bc3d79
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51934140"
---
# <a name="dashboard-insights---threat-and-vulnerability-management"></a>Informations sur les tableaux de bord : gestion des menaces et des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l'expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

La gestion des menaces et des vulnérabilités est un composant de Defender pour point de terminaison et fournit aux administrateurs de sécurité et aux équipes d'opérations de sécurité une valeur unique, notamment :


- Informations sur la détection et la réponse au point de terminaison en temps réel (EDR) corrélées avec les vulnérabilités de point de terminaison
- Contexte de vulnérabilité d'appareil précieux pendant les enquêtes d'incident
- Processus de correction intégrés via Microsoft Intune et Microsoft Endpoint Configuration Manager  
  
Vous pouvez utiliser la fonctionnalité de gestion des menaces et des vulnérabilités dans le Centre de sécurité [Microsoft Defender](https://securitycenter.windows.com/) pour :

- Afficher le score d'exposition et le degré de sécurisation Microsoft pour les appareils, ainsi que les principales recommandations en matière de sécurité, la vulnérabilité logicielle, les activités de correction et les appareils exposés
- Corréler les informations EDR avec les vulnérabilités des points de terminaison et les traiter
- Sélectionner les options de correction à trier et suivre les tâches de correction
- Sélectionner des options d'exception et suivre les exceptions actives

> [!NOTE]
> Les appareils qui ne sont pas actifs au cours des 30 derniers jours ne sont pas factorés sur les données qui reflètent le score d'exposition à la gestion des menaces et des vulnérabilités de votre organisation et le Degré de sécurisation Microsoft pour les appareils.

Regardez cette vidéo pour obtenir une vue d'ensemble rapide du tableau de bord de gestion des menaces et des vulnérabilités.

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r1nv]

## <a name="threat-and-vulnerability-management-dashboard"></a>Tableau de bord de gestion des menaces et des vulnérabilités

 ![Portail Microsoft Defender pour les points de terminaison](images/tvm-dashboard-devices.png)

Domaine | Description
:---|:---
**Groupes d'appareils sélectionnés (#/#)**   | Filtrez les données de gestion des menaces et des vulnérabilités que vous souhaitez voir dans le tableau de bord et les cartes par groupes d'appareils. Ce que vous sélectionnez dans le filtre s'applique à l'ensemble des pages de gestion des menaces et des vulnérabilités.
[**Score d'exposition**](tvm-exposure-score.md)   | Consultez l'état actuel de l'exposition des appareils de votre organisation aux menaces et vulnérabilités. Plusieurs facteurs affectent le score d'exposition de votre organisation : faiblesses découvertes sur vos appareils, probabilité de violation de vos appareils, valeur des appareils pour votre organisation et alertes pertinentes découvertes avec vos appareils. L'objectif est de réduire le score d'exposition de votre organisation pour être plus sécurisé. Pour réduire le score, vous devez corriger les problèmes de configuration de sécurité associés répertoriés dans les recommandations de sécurité.
[**Niveau de sécurité Microsoft pour les appareils**](tvm-microsoft-secure-score-devices.md) | Découvrez la posture de sécurité du système d'exploitation, des applications, du réseau, des comptes et des contrôles de sécurité de votre organisation. L'objectif est de résoudre les problèmes de configuration de sécurité associés afin d'augmenter votre score pour les appareils. La sélection des barres vous permettra d'être sur la page **recommandations en matière de** sécurité.
**Distribution de l'exposition des appareils** | Voir le nombre d'appareils exposés en fonction de leur niveau d'exposition. Sélectionnez une section dans le graphique en doughnut pour aller à la **page** de liste Périphériques et afficher les noms des appareils concernés, le niveau d'exposition, le niveau de risque et d'autres détails tels que le domaine, la plateforme du système d'exploitation, son état d'état d'état, la dernière fois qu'il a été vu et ses balises.
**Recommandations de sécurité principales** | Consultez les recommandations de sécurité triées qui sont triées et hiérarchisées en fonction de l'exposition aux risques de votre organisation et de l'urgence dont elle a besoin. Sélectionnez **Afficher plus** pour afficher le reste des recommandations de sécurité dans la liste. Sélectionnez **Afficher les exceptions** pour la liste des recommandations qui ont une exception.
**Logiciels les plus vulnérables** | Obtenez une visibilité en temps réel de l'inventaire logiciel de votre organisation avec une liste de logiciels vulnérables installés sur les appareils de votre réseau et leur impact sur le score d'exposition de votre organisation. Sélectionnez un élément pour plus d'informations **ou** affichez plus pour afficher le reste de la liste des logiciels vulnérables dans la page **Inventaire logiciel.**
**Principales activités de correction** | Suivre les activités de correction générées à partir des recommandations de sécurité. Vous pouvez sélectionner chaque élément de la liste pour afficher  les détails dans la **page** Correction ou sélectionner Afficher plus pour afficher le reste des activités de correction et les exceptions actives.
**Appareils les plus exposés** | Afficher les noms des appareils exposés et leur niveau d'exposition. Sélectionnez un nom d'appareil dans la liste pour aller à la page de l'appareil où vous pouvez afficher les alertes, les risques, les incidents, les recommandations de sécurité, les logiciels installés et les vulnérabilités découvertes associées aux appareils exposés. Sélectionnez **Afficher plus** pour afficher le reste de la liste des appareils exposés. Dans la liste des appareils, vous pouvez gérer les balises, lancer des enquêtes automatisées, lancer une session de réponse en direct, collecter un package d'enquête, exécuter une analyse antivirus, restreindre l'exécution de l'application et isoler l'appareil.

Pour plus d'informations sur les icônes utilisées dans l'ensemble du portail, voir [Microsoft Defender pour les icônes de point de terminaison.](portal-overview.md#microsoft-defender-for-endpoint-icons)


## <a name="related-topics"></a>Voir aussi

- [Vue d'ensemble de la gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Score d'exposition](tvm-exposure-score.md)
- [Niveau de sécurité Microsoft pour les appareils](tvm-microsoft-secure-score-devices.md)
- [Recommandations de sécurité](tvm-security-recommendation.md)
- [Inventaire des logiciels](tvm-software-inventory.md)
- [Chronologie des événements](threat-and-vuln-mgt-event-timeline.md)

