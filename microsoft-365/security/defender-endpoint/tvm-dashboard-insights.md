---
title: 'Informations sur le tableau de bord : Gestion des menaces et des vulnérabilités'
description: Le tableau Gestion des menaces et des vulnérabilités de bord peut aider SecOps et les administrateurs de sécurité à faire face aux menaces de cybersécurité et à renforcer la résilience de sécurité de leur organisation.
keywords: Microsoft Defender pour Endpoint-tvm, tableau de bord Microsoft Defender pour Endpoint-tvm, & gestion des vulnérabilités menaces, Gestion des menaces et des vulnérabilités, & gestion des vulnérabilités menaces basées sur les risques, configuration de la sécurité, Score de sécurité Microsoft pour les appareils, score d’exposition
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
ms.openlocfilehash: ee7cffc2c7b52e67fe5b82e4d6ee3def45cdf079
ms.sourcegitcommit: 4ea16de333421e24b15dd1f164963bc9678653fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2021
ms.locfileid: "60010056"
---
# <a name="dashboard-insights---threat-and-vulnerability-management"></a>Informations sur le tableau de bord : Gestion des menaces et des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Menaces et gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Threat and gestion des vulnérabilités is a component of Defender for Endpoint, and provides both security administrators and security operations teams with unique value, including:

- Informations sur la détection et la réponse au point de terminaison en temps réel (EDR) corrélées avec les vulnérabilités de point de terminaison
- Contexte de vulnérabilité d’appareil précieux pendant les enquêtes d’incident
- Processus de correction intégrés par le biais Microsoft Intune et Microsoft Endpoint Configuration Manager

Vous pouvez utiliser la fonctionnalité Gestion des menaces et des vulnérabilités dans [Microsoft 365 Defender portail pour](https://security.microsoft.com/) :

- Afficher le score d’exposition et le degré de sécurisation Microsoft pour les appareils, ainsi que les principales recommandations en matière de sécurité, la vulnérabilité logicielle, les activités de correction et les appareils exposés
- Corréler PEPT informations sur les vulnérabilités des points de terminaison et les traiter
- Sélectionner les options de correction à trier et suivre les tâches de correction
- Sélectionner des options d’exception et suivre les exceptions actives

> [!NOTE]
> Les appareils qui ne sont pas actifs au cours des 30 derniers jours ne sont pas factorés sur les données qui reflètent le score d’exposition Gestion des menaces et des vulnérabilités de votre organisation et le score de sécurité Microsoft pour les appareils.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide de ce qui se trouve dans Gestion des menaces et des vulnérabilités tableau de bord.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r1nv]

## <a name="threat-and-vulnerability-management-dashboard"></a>Tableau de bord des menaces gestion des vulnérabilités de sécurité

:::image type="content" source="../../media/tvmdashboard.png" lightbox="../../media/tvmdashboard.png" alt-text="Tableau de bord de gestion des menaces et des vulnérabilités pour les appareils.":::

<br>

****

|Zone|Description|
|---|---|
|**Groupes d’appareils sélectionnés (#/#)**|Filtrez les Gestion des menaces et des vulnérabilités que vous souhaitez voir dans le tableau de bord et les cartes par groupes d’appareils. Ce que vous sélectionnez dans le filtre s’applique à l’ensemble Gestion des menaces et des vulnérabilités pages.|
|[**Score d'exposition**](tvm-exposure-score.md)|Consultez l’état actuel de l’exposition des appareils de votre organisation aux menaces et vulnérabilités. Plusieurs facteurs affectent le score d’exposition de votre organisation : faiblesses découvertes sur vos appareils, probabilité de violation de vos appareils, valeur des appareils pour votre organisation et alertes pertinentes découvertes avec vos appareils. L’objectif est de réduire le score d’exposition de votre organisation pour être plus sécurisé. Pour réduire le score, vous devez corriger les problèmes de configuration de sécurité associés répertoriés dans les recommandations de sécurité.|
|[**Niveau de sécurité Microsoft pour les appareils**](tvm-microsoft-secure-score-devices.md)|Découvrez la posture de sécurité du système d’exploitation, des applications, du réseau, des comptes et des contrôles de sécurité de votre organisation. L’objectif est de résoudre les problèmes de configuration de sécurité associés afin d’augmenter votre score pour les appareils. La sélection des barres vous permettra d’être sur la page **recommandations en matière de** sécurité.|
|**Distribution de l’exposition des appareils**|Voir le nombre d’appareils exposés en fonction de leur niveau d’exposition. Sélectionnez une section dans le graphique en doughnut pour aller à la **page** de liste Périphériques et afficher les noms des appareils concernés, le niveau d’exposition, le niveau de risque et d’autres détails tels que le domaine, la plateforme du système d’exploitation, son état d’état d’état, la dernière fois qu’il a été vu et ses balises.|
|**Recommandations de sécurité principales**|Consultez les recommandations de sécurité triées qui sont triées et hiérarchisées en fonction de l’exposition aux risques de votre organisation et de l’urgence dont elle a besoin. Sélectionnez **Afficher plus** pour afficher le reste des recommandations de sécurité dans la liste. Sélectionnez **Afficher les exceptions** pour la liste des recommandations qui ont une exception.|
|**Logiciels les plus vulnérables**|Obtenez une visibilité en temps réel de l’inventaire logiciel de votre organisation avec une liste de logiciels vulnérables installés sur les appareils de votre réseau et leur impact sur le score d’exposition de votre organisation. Sélectionnez un élément pour plus d’informations **ou** affichez plus pour afficher le reste de la liste des logiciels vulnérables dans la page **Inventaire logiciel.**|
|**Principales activités de correction**|Suivre les activités de correction générées à partir des recommandations de sécurité. Vous pouvez sélectionner chaque élément de la liste pour afficher  les détails dans la **page** Correction ou sélectionner Afficher plus pour afficher le reste des activités de correction et les exceptions actives.|
|**Appareils les plus exposés**|Afficher les noms des appareils exposés et leur niveau d’exposition. Sélectionnez un nom d’appareil dans la liste pour aller à la page de l’appareil où vous pouvez afficher les alertes, les risques, les incidents, les recommandations de sécurité, les logiciels installés et les vulnérabilités découvertes associées aux appareils exposés. Sélectionnez **Afficher plus** pour afficher le reste de la liste des appareils exposés. Dans la liste des appareils, vous pouvez gérer les balises, lancer des enquêtes automatisées, lancer une session de réponse en direct, collecter un package d’enquête, exécuter une analyse antivirus, restreindre l’exécution de l’application et isoler l’appareil.|
|

Pour plus d’informations sur les icônes utilisées dans l’ensemble du portail, voir [Microsoft Defender pour les icônes de point de terminaison.](portal-overview.md#microsoft-defender-for-endpoint-icons)

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble gestion des vulnérabilités menaces et gestion des vulnérabilités menaces](next-gen-threat-and-vuln-mgt.md)
- [Score d'exposition](tvm-exposure-score.md)
- [Niveau de sécurité Microsoft pour les appareils](tvm-microsoft-secure-score-devices.md)
- [Recommandations de sécurité](tvm-security-recommendation.md)
- [Inventaire des logiciels](tvm-software-inventory.md)
- [Chronologie des événements](threat-and-vuln-mgt-event-timeline.md)
