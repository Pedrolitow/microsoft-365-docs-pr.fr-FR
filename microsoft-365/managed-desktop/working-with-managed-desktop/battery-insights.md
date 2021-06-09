---
title: Aperçu de la batterie
description: Un rapport qui affiche des données sur l’autonomie prévue de la batterie et les principaux consommateurs d’énergie
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 32ab3a984d5ab46aac26989518cd3e570082d688
ms.sourcegitcommit: cebbdd393dcfd93ff43a1ab66ad70115853f83e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2021
ms.locfileid: "52739793"
---
# <a name="battery-insights"></a>Aperçu de la batterie
Cette vue fournit des mesures d’utilisation de l’alimentation, de la batterie et de l’application pour Bureau géré Microsoft appareils. À ces fins, une application est considérée comme « en cours d’utilisation » si elle est en cours d’exécution et en cours d’exécution.

Pour afficher les données d’utilisation, sélectionnez **l’onglet** Batterie.

![Volet de batterie : durée de vie prévue de la batterie par modèle d’appareil en haut à gauche, consommateurs d’énergie supérieurs (par application) en haut à droite, tableau d’informations en bas. Lien de documentation en haut à droite](../../media/insights_battery.png)

## <a name="predicted-battery-life"></a>Durée de vie prévue de la batterie

Dans la **zone d’autonomie prévue de** la batterie, nous fournissons des prévisions pour l’autonomie prévue de la batterie pour vos appareils, organisée par modèle d’appareil.

> [!NOTE]
> Ces données sont dérivées de l’échantillonnage de l’utilisation de l’énergie, du temps d’utilisation et de la capacité de la batterie à partir d’une sélection aléatoire des appareils de votre déploiement Bureau géré Microsoft qui sont également des données de rapport. <em></em>

Le tableau indique l’autonomie prévue de la batterie (en heures), l’autonomie moyenne de la batterie pour les mêmes modèles dans d’autres déploiements Bureau géré Microsoft et le nombre d’appareils signalant ces données dans votre environnement. Trie les données en sélectionnant les en-tête de colonne.



## <a name="top-energy-consumers"></a>Principaux consommateurs d’énergie

Dans la **zone Consommateurs** d’énergie les plus consommateurs d’énergie, vous trouverez les applications de votre environnement qui consomment le plus d’énergie en milliWatt-hours (mWh). Les applications affichées sont par appareil spécifique, que vous sélectionnez dans la section Durée de vie **prévue de la** batterie à gauche. Par exemple, pour voir la consommation par application pour vos appareils Microsoft Surface Book 2, sélectionnez cette ligne dans la zone d’autonomie de la batterie. Si vous ne sélectionnez aucun modèle, les données de consommation d’application affichées sont pour toutes les applications pour qui nous avons des données collectivement.

 Pour chaque application, les segments de couleur vous montrent la répartition de l’utilisation énergétique de l’application parmi ces catégories :

- UC
- Afficher
- Réseau
- Autre

Les « autres » peuvent inclure la consommation d’énergie par diverses sources, telles que l’activité du disque, l’utilisation du haut débit mobile et la perte d’énergie par la résistance interne. 

Vous pouvez filtrer cette vue pour afficher uniquement les applications de premier plan, les applications d’arrière-plan ou les deux à l’aide du menu dans le coin supérieur droit. Les applications de premier plan sont celles qui ont eu une interaction utilisateur au cours des 28 derniers jours, telles que la sélection d’un contenu à l’aide d’une souris.

## <a name="insights"></a>Informations

La **zone Insights** présente les trois premiers consommateurs d’énergie dans les catégories processeur et réseau. Ces éléments consomment plus d’énergie que la moyenne par rapport à tous Bureau géré Microsoft déploiements. Nous n’affichons pas la ressource d’affichage, car elle dépend fortement du temps d’utilisation de l’appareil et des paramètres de luminosité de l’écran. 

Sélectionnez les descriptions dans la **colonne Détails** pour plus d’informations.

## <a name="battery-optimization"></a>Optimisation de la batterie

Windows 10 offre de nombreux [paramètres d’appareil](https://support.microsoft.com/help/20443/windows-10-battery-saving-tips) pour améliorer l’utilisation de l’alimentation et augmenter l’autonomie de la batterie de Bureau géré Microsoft appareils. Certains de ces paramètres peuvent diminuer d’autres fonctionnalités Windows, vous devez donc également prendre en compte d’autres facteurs tels que le rôle de l’appareil dans votre organisation. Windows prise en charge conserve une liste de ces conseils d’économie [de batterie.](https://support.microsoft.com/help/20443/windows-10-battery-saving-tips)

Les utilisateurs peuvent ajuster certains paramètres eux-mêmes sans avoir besoin d’une élévation ou d’une prise en charge par l’administrateur. D’autres paramètres nécessitent la prise en charge de l’administrateur informatique de votre organisation.
