---
title: Rapport d’intégrité et de conformité des appareils dans Microsoft Defender pour point de terminaison
description: Suivre les détections d’état d’intégrité des appareils, l’état antivirus, la plateforme du système d’exploitation et les versions Windows 10 à l’aide du rapport d’intégrité et de conformité de l’appareil
keywords: état d’intégrité, antivirus, plateforme de système d’exploitation, version windows 10, version, intégrité, conformité, état
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d171db0d5009cc32c34c3bf95da907221f275410
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789269"
---
# <a name="device-health-and-compliance-report-in-microsoft-defender-for-endpoint"></a>Rapport d’intégrité et de conformité des appareils dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender 

**Plateformes**
- Windows
- Mac OS
- Linux
- iOS
- Android

Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Le rapport d’état des appareils fournit des informations générales sur les appareils de votre organisation. Le rapport inclut des informations de tendance indiquant l’état d’intégrité du capteur, l’état antivirus, les plateformes de système d’exploitation et les versions Windows 10 (et Windows 11).

Le tableau de bord est structuré en deux sections :

:::image type="content" source="images/device-reports.png" alt-text="Rapport sur l’appareil" lightbox="images/device-reports.png":::


<br>

****

|Section|Description|
|---|---|
|1|Tendances des appareils|
|2|Résumé de l’appareil (jour actuel)|
|||

## <a name="device-trends"></a>Tendances des appareils

Par défaut, les tendances des appareils affichent les informations sur les appareils de la période de 30 jours se terminant par la dernière journée complète. Pour obtenir une meilleure perspective des tendances qui se produisent dans votre organisation, vous pouvez affiner la période de rapport en ajustant la période indiquée. Pour ajuster la période, sélectionnez un intervalle de temps dans les options de liste déroulante :

- 30 jours
- Trois mois
- Six mois
- Personnalisé

> [!NOTE]
> Ces filtres sont appliqués uniquement à la section Tendances des appareils. Cela n’affecte pas la section récapitulative de l’appareil.

## <a name="device-summary"></a>Récapitulatif de l’appareil

Tandis que les tendances des appareils indiquent les informations de tendance des appareils, le récapitulatif de l’appareil affiche les informations de l’appareil limitées au jour actuel.

> [!NOTE]
> Les données reflétées dans la section récapitulative sont limitées à 180 jours avant la date actuelle. Par exemple, si la date du jour est le 27 mars 2019, les données de la section récapitulative reflètent les nombres entre le 28 septembre 2018 et le 27 mars 2019.
>
> Le filtre appliqué à la section Tendances n’est pas appliqué à la section récapitulative.

La section Tendances des appareils vous permet d’explorer la liste des appareils avec le filtre correspondant qui lui est appliqué. Par exemple, si vous cliquez sur la barre Inactive dans la carte d’état d’intégrité du capteur, la liste des appareils affiche uniquement les appareils dont l’état du capteur est inactif.

## <a name="device-attributes"></a>Attributs de l’appareil

Le rapport est constitué de cartes qui affichent les attributs d’appareil suivants :

- **État d’intégrité** : affiche des informations sur l’état du capteur sur les appareils, fournissant une vue agrégée des appareils actifs, présentant des communications altérées, inactifs ou où aucune donnée de capteur n’est visible.
- **État de l’antivirus pour les appareils Windows 10 actifs** : indique le nombre d’appareils et l’état de Antivirus Microsoft Defender.
- **Plateformes** de système d’exploitation : affiche la distribution des plateformes de système d’exploitation qui existent au sein de votre organisation.
- **Windows 10 versions** : affiche la distribution des appareils Windows 10 et de leurs versions dans votre organisation.

## <a name="filter-data"></a>Filtrer les données

Utilisez les filtres fournis pour inclure ou exclure des appareils avec certains attributs.

Vous pouvez sélectionner plusieurs filtres à appliquer à partir des attributs de l’appareil.

> [!NOTE]
> Ces filtres s’appliquent à **toutes les** cartes du rapport.

Par exemple, pour afficher des données sur Windows 10 appareils avec l’état d’intégrité du capteur actif :

1. Sous **Filtres > l’état d’intégrité du capteur > Actif**.
2. Sélectionnez ensuite **les plateformes de système d’exploitation > Windows 10**.
3. Sélectionnez **Appliquer**.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison sur les fonctionnalités Android](android-configure.md)
> - [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-topic"></a>Rubrique connexe

- [Rapport de protection contre les menaces](threat-protection-reports.md)
