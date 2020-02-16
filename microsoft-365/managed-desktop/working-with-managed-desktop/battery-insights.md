---
title: Informations sur la batterie
description: ''
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 056685cbd49e6fb247a92357b3483b479d705c90
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42085727"
---
# <a name="battery-insights"></a>Informations sur la batterie
Cette vue fournit des mesures d’utilisation de l’alimentation, de la batterie et de l’application pour vos appareils de bureau gérés par Microsoft. À cette fin, une application est considérée « en cours d’utilisation » si elle est en cours d’exécution et en focus.

Pour afficher les données d’utilisation, sélectionnez l’onglet **batterie** .

![Volet de la batterie : durée de vie de la batterie prévisible par modèle d’appareil dans le coin supérieur gauche, consommateurs de l’énergie de haut niveau (par application) dans le coin supérieur droit, tableau Insights en bas. Lien vers la documentation en haut à droite.](../../media/insights_battery.png)

## <a name="predicted-battery-life"></a>Durée de vie de la batterie prévisible

Dans la zone de **durée de vie** de la batterie prévue, nous fournissons des prévisions pour la durée de vie de la batterie attendue pour vos appareils, organisés par modèle d’appareil.

> [!NOTE]
> Ces données proviennent de l’échantillonnage de l’utilisation de l’énergie, du temps d’utilisation et de la capacité de la batterie à partir d’une <em>sélection</em> aléatoire des appareils dans votre déploiement de bureau géré Microsoft qui sont également des données de rapport.

Le tableau indique la durée de vie de la batterie prévue (en heures), la durée de vie moyenne de la batterie pour les mêmes modèles dans d’autres déploiements de bureau géré Microsoft et le nombre d’appareils qui signalent ces données dans votre environnement. Triez les données en sélectionnant les en-têtes de colonne.



## <a name="top-energy-consumers"></a>Principaux consommateurs énergétiques

Dans la zone **Consumer Energy Top** , vous trouverez les applications de votre environnement qui consomment le plus d’énergie en milliwatt-Hours (MWh). Les applications affichées sont déterminées par un appareil spécifique, que vous sélectionnez dans la section **durée de vie** de la batterie à gauche. Par exemple, pour voir la consommation par application de vos appareils de la surface de votre site, sélectionnez cette ligne dans la zone autonomie de la batterie. Si vous ne sélectionnez aucun modèle, les données de consommation de l’application affichées s’affichent pour toutes les applications pour lesquelles nous disposons de données collectives.

 Pour chaque application, les segments colorés vous montrent la distribution de l’utilisation de l’énergie de l’application dans les catégories suivantes :

- UC
- Display
- Réseau
- Autres

« Other » peut inclure la consommation d’énergie par diverses sources, telles que l’activité du disque, l’utilisation du haut débit mobile et l’énergie perdue à la résistance interne. 

Vous pouvez filtrer cet affichage pour n’afficher que les applications de premier plan, les applications d’arrière-plan ou les deux à l’aide du menu en haut à droite. Les applications de premier plan sont celles qui ont eu une interaction avec l’utilisateur au cours des 28 derniers jours, comme la sélection d’un article à l’aide d’une souris.

## <a name="insights"></a>Informations

La zone **Insights** présente les trois principaux consommateurs énergétiques dans les catégories d’UC et de réseau. Ces éléments consomment une consommation supérieure à la moyenne par rapport à tous les déploiements de bureau gérés par Microsoft. Nous n’affichons pas la ressource d’affichage, car elle dépend étroitement de la durée d’utilisation de l’appareil et des paramètres de luminosité de l’écran. 

Pour plus d’informations, sélectionnez les listes dans la colonne **Détails** .

## <a name="battery-optimization"></a>Optimisation de la batterie

Windows 10 offre de nombreux [paramètres d’appareil](https://support.microsoft.com/help/20443/windows-10-battery-saving-tips) pour améliorer la consommation d’énergie et augmenter la durée de vie de la batterie de vos appareils de bureau gérés par Microsoft. Certains de ces paramètres peuvent réduire d’autres fonctionnalités de Windows, de sorte que vous devrez également prendre en compte d’autres facteurs, tels que le rôle de l’appareil dans votre organisation. Le support Windows conserve une liste de ces [conseils d’économie de batterie](https://support.microsoft.com/help/20443/windows-10-battery-saving-tips).

Les utilisateurs peuvent ajuster certains paramètres sans avoir besoin d’une élévation ou d’une prise en charge de l’administrateur. D’autres paramètres doivent être pris en charge par l’administrateur informatique de votre organisation.
