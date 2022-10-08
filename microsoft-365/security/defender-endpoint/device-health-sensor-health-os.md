---
title: Rapport sur l’intégrité du capteur d’intégrité de l’appareil & système d’exploitation
description: Utilisez le rapport d’intégrité de l’appareil pour suivre l’intégrité des appareils, les plateformes de système d’exploitation et les versions Windows 10.
keywords: état d’intégrité, antivirus, plateforme de système d’exploitation, version windows 10, version, intégrité, conformité, état
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
ms.date: 09/06/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.subservice: mde
ms.reviewer: mkaminska
ms.openlocfilehash: 611fa76162094b8dd24a56c92f7f3b9b6e75a635
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68168398"
---
# <a name="device-health-sensor-health--os-report"></a>Intégrité de l’appareil, rapport sur l’intégrité du capteur & système d’exploitation

**S’applique à :**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/mdb-overview.md)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Le rapport Intégrité des appareils fournit des informations sur les appareils de votre organisation. Le rapport inclut des informations de tendance indiquant l’état d’intégrité du capteur, l’état de l’antivirus, les plateformes de système d’exploitation, les versions Windows 10 et Microsoft Defender versions de mise à jour antivirus.

> [!IMPORTANT]
> Pour que Windows&nbsp;Server&nbsp;2012&nbsp;R2 et Windows&nbsp;Server&nbsp;2016 apparaissent dans les rapports d’intégrité des appareils, ces appareils doivent être intégrés à l’aide du package de solution unifié moderne. Pour plus d’informations, consultez [Nouvelles fonctionnalités de la solution unifiée moderne pour Windows Server 2012 R2 et 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution).

Dans le panneau de navigation du tableau de bord Sécurité Microsoft 365, sélectionnez **Rapports**, puis ouvrez **Intégrité et conformité de l’appareil**.

- [L’onglet **Intégrité du capteur & système d’exploitation**](#sensor-health--os-tab) fournit des informations générales sur le système d’exploitation, divisées en trois cartes qui affichent les attributs d’appareil suivants :
  - [Carte d’intégrité du capteur](#sensor-health-card)
  - [Carte des systèmes d’exploitation et des plateformes](#operating-systems-and-platforms-card)
  - [Carte des versions de Windows](#windows-versions-card)

## <a name="report-access-permissions"></a>Autorisations d’accès aux rapports

Pour accéder au rapport de conformité de l’intégrité des appareils et des antivirus dans le tableau de bord Sécurité Microsoft 365, les autorisations suivantes sont requises :

| Nom de l’autorisation | Type d’autorisation |
|:---|:---|
| Afficher les données | Gestion des menaces et des vulnérabilités (TVM) |

Pour attribuer ces autorisations :

1. Connectez-vous à Microsoft 365 Defender à l’aide <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">d’un</a> compte avec un rôle d’administrateur de sécurité ou de Administrateur général attribué.
1. Dans le volet de navigation, sélectionnez **Paramètres des rôles** \> **de points de terminaison** \> (sous **Autorisations**).
1. Sélectionnez le rôle que vous souhaitez modifier.
1. Sélectionnez **Modifier**.
1. Dans **Modifier le rôle**, sous l’onglet **Général** , dans **le nom** du rôle, tapez un nom pour le rôle.
1. Dans **Description** , tapez un bref résumé du rôle.
1. Dans **Autorisations**, sélectionnez **Afficher les données**, puis sous **Afficher les données** , sélectionnez **Gestion des menaces et des vulnérabilités** (TVM).

Pour plus d’informations sur la gestion des rôles d’utilisateur, consultez [Créer et gérer des rôles pour le contrôle d’accès en fonction du rôle](user-roles.md).

## <a name="sensor-health--os-tab"></a>Onglet Intégrité du capteur & système d’exploitation

L’intégrité des capteurs et les cartes de système d’exploitation indiquent l’intégrité générale du système d’exploitation, ce qui inclut l’intégrité du capteur de détection, les systèmes d’exploitation à jour et les systèmes d’exploitation obsolètes et les versions Windows 10.

>:::image type="content" source="images/device-health-sensor-health-os-tab.png" alt-text="Affiche les informations sur l’intégrité du capteur et le système d’exploitation." lightbox="images/device-health-sensor-health-os-tab.png":::

Chacune des trois cartes de l’onglet **Intégrité du capteur** comporte deux sections de création de rapports, _l’état actuel_ et _les tendances des appareils_, présentées sous forme de graphiques :

### <a name="current-state-graph"></a>Graphique d’état actuel

Dans chaque carte, l’état actuel (référencé dans une documentation sous le nom _de Résumé de l’appareil_) est le graphique à barres horizontales supérieur. L’état actuel est un instantané qui affiche les informations collectées sur les appareils de votre organisation, limitées au jour actuel. Ce graphique représente la distribution des appareils dans votre organisation qui signalent l’état ou qui sont détectés comme étant dans un état spécifique.

>:::image type="content" source="images/device-health-sensor-health-os-current-state-graph.png" alt-text="Affiche le graphique d’état actuel." lightbox="images/device-health-sensor-health-os-current-state-graph.png":::

### <a name="device-trends-graph"></a>Graphique des tendances des appareils

Le graphique inférieur de chacune des trois cartes n’est pas nommé, mais il est communément appelé _tendances des appareils_. Le graphique des tendances des appareils représente la collection d’appareils au sein de votre organisation, tout au long de l’intervalle de temps indiqué directement au-dessus du graphique.
Par défaut, le graphique des tendances des appareils affiche les informations de l’appareil de la période de 30 jours, se terminant par la dernière journée complète. Pour obtenir une meilleure perspective des tendances qui se produisent dans votre organisation, vous pouvez affiner la période de rapport en ajustant la période indiquée. Pour ajuster la période, ouvrez le filtre et sélectionnez un jour de début et de fin.

>:::image type="content" source="images/device-health-sensor-health-os-device-trends-graph.png" alt-text="Affiche le graphique des tendances des versions de Device Health." lightbox="images/device-health-sensor-health-os-device-trends-graph.png":::

### <a name="filtering-data"></a>Filtrage des données

Utilisez les filtres fournis pour inclure ou exclure des appareils avec certains attributs. Vous pouvez sélectionner plusieurs filtres à appliquer à partir des attributs de l’appareil. Lorsqu’ils sont appliqués, les filtres s’appliquent aux trois cartes du rapport.

Par exemple, pour afficher des données sur Windows 10 appareils avec l’état d’intégrité du capteur actif :

1. Sous **Filtres** > **État d’intégrité** >  du capteur **Actif**.
2. Sélectionnez ensuite **les plateformes** >  **de système d’exploitation Windows 10**.
3. Sélectionnez **Appliquer**.

### <a name="sensor-health-card"></a>Carte d’intégrité du capteur

La carte d’intégrité du capteur affiche des informations sur l’état du capteur sur les appareils. L’intégrité du capteur fournit une vue d’ensemble des appareils qui sont les suivants :

- Active
- Inactif
- des communications altérées;
- ou où aucune donnée de capteur n’est signalée

Les appareils qui connaissent des communications altérées ou les appareils à partir desquels aucune donnée de capteur n’est détectée peuvent exposer votre organisation à des risques et justifier une enquête. De même, les appareils inactifs pendant de longues périodes peuvent exposer votre organisation à des menaces en raison de logiciels obsolètes. Les appareils inactifs pendant de longues périodes justifient également une enquête.

> [!NOTE]
>
> Dans un petit pourcentage de cas, les nombres et les distributions signalés lorsque vous cliquez sur le graphique horizontal de la barre d’intégrité du capteur ne sont pas synchronisés avec les valeurs affichées dans la page **Inventaire des appareils** . La disparité des valeurs peut se produire, car la cadence d’actualisation des rapports d’intégrité des capteurs est différente de celle de la page Inventaire des appareils.

### <a name="operating-systems-and-platforms-card"></a>Carte des systèmes d’exploitation et des plateformes

Cette carte affiche la distribution des systèmes d’exploitation et des plateformes qui existent au sein de votre organisation.
_Les systèmes et plateformes_ de système d’exploitation peuvent fournir des insights utiles sur l’exécution des systèmes d’exploitation actuels ou obsolètes dans votre organisation. Lorsque de nouveaux systèmes d’exploitation sont introduits, des améliorations de sécurité sont fréquemment incluses qui améliorent la posture de votre organisation face aux menaces de sécurité.

Par exemple, le démarrage sécurisé (introduit dans Windows 8) a pratiquement éliminé la menace de certains des types de programmes malveillants les plus dangereux. Les améliorations apportées à Windows 10 offrent aux fabricants de PC la possibilité d’empêcher les utilisateurs de désactiver le démarrage sécurisé. Empêcher les utilisateurs de désactiver le démarrage sécurisé supprime presque toutes les chances que des rootkits malveillants ou d’autres programmes malveillants de bas niveau infectent le processus de démarrage.

Dans l’idéal, le graphique « État actuel » montre que le nombre de systèmes d’exploitation est pondéré en faveur d’un système d’exploitation plus actuel que les versions antérieures. Dans le cas contraire, le graphique des tendances indique que de nouveaux systèmes sont adoptés et/ou des systèmes plus anciens sont mis à jour ou remplacés.

### <a name="windows-versions-card"></a>Carte des versions de Windows

La carte des versions Windows 10 affiche la distribution des appareils Windows et de leurs versions dans votre organisation.
De la même façon qu’une mise à niveau de Windows 8 vers Windows 10 améliore la sécurité dans votre organisation, passer des versions antérieures de Windows à des versions plus récentes améliore votre posture face aux menaces possibles.

Le graphique de tendance des versions de Windows peut vous aider à déterminer rapidement si votre organisation est à jour en mettant à jour vers les versions les plus récentes et les plus sécurisées de Windows 10.

## <a name="see-also"></a>Voir aussi

[Microsoft Defender l’intégrité de l’antivirus](device-health-microsoft-defender-antivirus-health.md#microsoft-defender-antivirus-health-tab)
