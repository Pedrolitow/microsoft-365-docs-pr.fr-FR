---
title: Afficher et organiser la liste des appareils Microsoft Defender pour les points de terminaison
description: Découvrez les fonctionnalités disponibles que vous pouvez utiliser dans la liste Appareils, telles que le tri, le filtrage et l’exportation de la liste pour améliorer les examens.
keywords: sort, filter, export, csv, device name, domain, last seen, internal IP, health state, active alerts, active malware detections, threat category, review alerts, network, connection, malware, type, password stealer, ransomware, exploit, threat, general malware, unwanted software
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
ms.openlocfilehash: 51b55a92a88dfa5faf89df89bfc3351b97571feb
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60588324"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-devices-list"></a>Afficher et organiser la liste Microsoft Defender pour les appareils de point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-machinesview-abovefoldlink)

La **liste Appareils affiche** la liste des appareils de votre réseau sur lequel des alertes ont été générées. Par défaut, la file d’attente affiche les appareils visibles au cours des 30 derniers jours.

En un coup d’œil, vous verrez des informations telles que le domaine, le niveau de risque, la plateforme du système d’exploitation et d’autres détails pour faciliter l’identification des appareils les plus exposés.

Vous pouvez choisir parmi plusieurs options pour personnaliser l’affichage liste des appareils. Dans la barre de navigation supérieure, vous pouvez :

- Ajouter ou supprimer des colonnes
- Exporter la liste entière au format CSV
- Sélectionner le nombre d’éléments à afficher par page
- Appliquer des filtres

Pendant le processus d’intégration, la liste **Appareils** est progressivement remplie avec les appareils qui commencent à signaler les données de capteur. Utilisez cette vue pour suivre vos points de terminaison intégrés lors de leur mise en ligne ou téléchargez la liste complète des points de terminaison en tant que fichier CSV pour l’analyse hors connexion.

> [!NOTE]
> Si vous exportez la liste des appareils, elle contiendra tous les appareils de votre organisation. Le téléchargement peut prendre beaucoup de temps, en fonction de la taille de votre organisation. L’exportation de la liste au format CSV affiche les données de manière non filtrée. Le fichier CSV inclut tous les appareils de l’organisation, quel que soit le filtrage appliqué dans l’affichage lui-même.

![Image de la liste des appareils avec liste d’appareils.](images/device-inventory.png)

## <a name="sort-and-filter-the-device-list"></a>Trier et filtrer la liste des appareils

Vous pouvez appliquer les filtres suivants pour limiter la liste des alertes et obtenir une vue plus centrée.

### <a name="device-name"></a>Nom du périphérique

Sélectionnez le nom de l’appareil que vous souhaitez examiner.

### <a name="domain"></a>Domaine

Sélectionnez le domaine qui vous intéresse.

### <a name="risk-level"></a>Niveau de risque

Le niveau de risque reflète l’évaluation globale des risques de l’appareil en fonction d’une combinaison de facteurs, notamment les types et la gravité des alertes actives sur l’appareil. La résolution des alertes actives, l’approbation des activités de correction et la suppression des alertes suivantes peuvent réduire le niveau de risque.

### <a name="exposure-level"></a>Niveau d’exposition

Le niveau d’exposition reflète l’exposition actuelle de l’appareil en fonction de l’impact cumulé de ses recommandations de sécurité en attente. Les niveaux possibles sont faibles, moyens et élevés. Une faible exposition signifie que vos appareils sont moins vulnérables à l’exploitation.

Si le niveau d’exposition indique « Aucune donnée disponible », il existe plusieurs raisons pour lesquelles cela peut être le cas :

- L’appareil a cessé de signaler pendant plus de 30 jours. Dans ce cas, il est considéré comme inactif et l’exposition n’est pas calculée.
- Le système d’exploitation de l’appareil n’est pas pris en charge : consultez les conditions [minimales requises pour Microsoft Defender pour endpoint.](minimum-requirements.md)
- Appareil avec agent obsolète (peu probable).

### <a name="os-platform"></a>Plateforme du système d’exploitation

Sélectionnez uniquement les plateformes de système d’exploitation qui vous intéressent.

### <a name="windows-versions"></a>Windows versions

Sélectionnez uniquement les Windows versions que vous souhaitez examiner.

### <a name="health-state"></a>État d’intégrité

Filtrez selon les états d’état d’état d’appareil suivants :

- **Actif**: appareils qui rapportent activement des données de capteur au service.
- **Inactif**: appareils qui ont cessé d’envoyer des signaux pendant plus de 7 jours.
- **Mal configuré : appareils** dont les communications avec le service sont réduites ou qui ne peuvent pas envoyer de données de capteur. Les appareils mal configurés peuvent également être classés sur :
  - Aucune donnée de capteur
  - Communications compromises

  Pour plus d’informations sur la façon de résoudre les problèmes sur les appareils mal configurés, voir corriger les [capteurs défectueux.](fix-unhealthy-sensors.md)

### <a name="onboarding-status"></a>État de l’intégration

L’état d’intégration indique si l’appareil est actuellement intégré à Microsoft Defender pour le point de terminaison ou non. Vous pouvez filtrer selon les états suivants :

- **Intégré :** le point de terminaison est intégré à Microsoft Defender pour le point de terminaison.

- **Peut être intégré :** le point de terminaison a été découvert dans le réseau en tant qu’appareil pris en charge, mais il n’est pas actuellement intégré. Microsoft recommande vivement l’intégration de ces appareils.

- **Non pris en charge**: le point de terminaison a été découvert dans le réseau, mais n’est pas pris en charge par Microsoft Defender pour endpoint.

- **Informations insuffisantes**: le système n’a pas pu déterminer la prise en charge de l’appareil.

### <a name="last-device-update"></a>Dernière mise à jour de périphérique

Filtrez votre affichage en fonction de la dernière mise à jour de l’appareil.

### <a name="first-seen"></a>Première vue

Filtrez votre affichage en fonction du moment où l’appareil a été vu pour la première fois sur le réseau ou de la première fois qu’il a été signalé par le capteur Microsoft Defender for Endpoint.

### <a name="tags"></a>Balises

Filtrez la liste en fonction du regroupement et du marquage que vous avez ajoutés à des appareils individuels. Voir [Créer et gérer des balises d’appareil.](machine-tags.md)

## <a name="related-topics"></a>Voir aussi

- [Examiner les appareils de la liste Microsoft Defender pour les appareils de point de terminaison](investigate-machines.md)
