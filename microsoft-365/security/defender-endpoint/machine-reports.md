---
title: Rapport d’intégrité et de conformité des appareils dans Microsoft Defender pour point de terminaison
description: Suivre les détections d’état de l’appareil, l’état antivirus, la plateforme de système d’exploitation et les versions Windows 10 à l’aide du rapport d’état et de conformité de l’appareil
keywords: état d’état d’état, antivirus, plateforme de système d’exploitation, version de Windows 10, version, santé, conformité, état
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
ms.openlocfilehash: 9efd1b6785c711855e32f80580d567a2d0befa93
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61121170"
---
# <a name="device-health-and-compliance-report-in-microsoft-defender-for-endpoint"></a>Rapport d’intégrité et de conformité des appareils dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Le rapport d’état des appareils fournit des informations de haut niveau sur les appareils de votre organisation. Le rapport inclut des informations de tendance montrant l’état d’état du capteur, l’état antivirus, les plateformes de système d’exploitation et les versions Windows 10 (et Windows 11).

Le tableau de bord est structuré en deux sections :

:::image type="content" alt-text="Image du rapport de périphérique." source="images/device-reports.png" lightbox="images/device-reports.png":::


<br>

****

|Section|Description|
|---|---|
|1|Tendances des appareils|
|2|Résumé de l’appareil (jour actuel)|
|||

## <a name="device-trends"></a>Tendances des appareils

Par défaut, les tendances des appareils affichent les informations sur les appareils de la période de 30 jours se terminant par la dernière journée entière. Pour mieux prendre en compte les tendances qui se produisent dans votre organisation, vous pouvez affiner la période de rapport en ajustant la période indiquée. Pour ajuster la période, sélectionnez une plage de temps dans les options de la baisse :

- 30 jours
- Trois mois
- Six mois
- Personnalisé

> [!NOTE]
> Ces filtres sont appliqués uniquement à la section Tendances des appareils. Elle n’affecte pas la section récapitulatif de l’appareil.

## <a name="device-summary"></a>Récapitulatif de l’appareil

Alors que les tendances des appareils indiquent les tendances des appareils, le résumé de l’appareil affiche les informations d’appareil limitées au jour actuel.

> [!NOTE]
> Les données reflétées dans la section récapitulatif sont limitées à 180 jours avant la date actuelle. Par exemple, si la date du jour est le 27 mars 2019, les données de la section récapitulatif reflétera les chiffres du 28 septembre 2018 au 27 mars 2019.
>
> Le filtre appliqué à la section tendances n’est pas appliqué à la section récapitulatif.

La section Tendances des appareils vous permet d’aller jusqu’à la liste des appareils avec le filtre correspondant qui lui est appliqué. Par exemple, si vous cliquez sur la barre inactive de la carte d’état d’état du capteur, la liste des appareils affiche uniquement les appareils dont l’état du capteur est inactif.

## <a name="device-attributes"></a>Attributs d’appareil

Le rapport est composé de cartes qui affichent les attributs d’appareil suivants :

- **État d’état**: affiche des informations sur l’état du capteur sur les appareils, en fournissant une vue agrégée des appareils actifs, qui rencontrent des problèmes de communication, qui sont inactifs ou où aucune donnée de capteur n’est visible.
- **État antivirus des appareils Windows 10 actifs**: indique le nombre d’appareils et l’état des Antivirus Microsoft Defender.
- **Plateformes de système d’exploitation**: affiche la distribution des plateformes de système d’exploitation qui existent au sein de votre organisation.
- **Windows 10 versions**: affiche la distribution des Windows 10 et leurs versions dans votre organisation.

## <a name="filter-data"></a>Filtrer les données

Utilisez les filtres fournis pour inclure ou exclure des appareils avec certains attributs.

Vous pouvez sélectionner plusieurs filtres à appliquer à partir des attributs d’appareil.

> [!NOTE]
> Ces filtres **s’appliquent à toutes** les cartes du rapport.

Par exemple, pour afficher des données sur les Windows 10 avec l’état d’état d’état du capteur actif :

1. Sous **Filtres > l’état d'> du capteur actif.**
2. Sélectionnez ensuite **les plateformes de système d'> Windows 10**.
3. Sélectionnez **Appliquer**.

## <a name="related-topic"></a>Rubrique connexe

- [Rapport de protection contre les menaces](threat-protection-reports.md)
