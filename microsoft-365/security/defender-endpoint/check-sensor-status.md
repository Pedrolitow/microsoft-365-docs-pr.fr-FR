---
title: Vérifier l’état d’état du capteur dans Microsoft Defender pour le point de terminaison
description: Vérifiez l’état du capteur sur les appareils pour identifier ceux qui sont mal configurés, inactifs ou qui ne rapportent pas de données de capteur.
keywords: capteur, état du capteur, mal configuré, inactif, aucune donnée de capteur, données du capteur, communications altérées, communication
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 12762d9872c6a260e1a410c183387391e0c1aa7f
ms.sourcegitcommit: af575ade7b187af70f94db904b03f0471f56452a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2021
ms.locfileid: "53591030"
---
# <a name="check-sensor-health-state-in-microsoft-defender-for-endpoint"></a>Vérifier l’état d’état du capteur dans Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-checksensor-abovefoldlink)

La vignette **Appareils avec problèmes de** capteur se trouve dans le tableau de bord Opérations de sécurité. Cette vignette fournit des informations sur la capacité de chaque appareil à fournir des données de capteur et à communiquer avec le service Defender for Endpoint. Elle indique le nombre d’appareils qui nécessitent une attention particulière et vous aide à identifier les appareils problématiques et à prendre des mesures pour les corriger.

Il existe deux indicateurs d’état sur la vignette qui fournissent des informations sur le nombre d’appareils qui ne sont pas correctement signalés au service :
- **Mal configuré :** ces appareils peuvent signaler partiellement des données de capteur au service Defender for Endpoint et peuvent avoir des erreurs de configuration qui doivent être corrigées.
- **Inactif** : appareils qui ont cessé de signaler au service Defender for Endpoint pendant plus de sept jours au cours du mois précédent.

Cliquer sur l’un des groupes vous dirige vers la liste **Appareils,** filtrée en fonction de votre choix.

![Capture d’écran de la vignette Appareils avec problèmes de capteur](images/atp-devices-with-sensor-issues-tile.png)

Dans **la liste Appareils,** vous pouvez filtrer la liste d’état en fonction de l’état suivant :
- **Actif** : appareils qui font activement des rapports au service Defender for Endpoint.
- **Mal configuré :** ces appareils peuvent partiellement signaler des données de capteur au service Defender for Endpoint, mais ont des erreurs de configuration qui doivent être corrigées. Les appareils mal configurés peuvent avoir l’un ou l’autre des problèmes suivants :
  - **Aucune donnée de capteur** : les appareils ont cessé d’envoyer des données de capteur. Des alertes limitées peuvent être déclenchées à partir de l’appareil.
  - **Communications réduites** : la capacité de communication avec l’appareil est réduite. Il est possible que l'envoi de fichiers pour une analyse approfondie, le blocage de fichiers, l'isolement de l'appareil du réseau et d'autres actions qui nécessitent une communication avec l'appareil ne fonctionnent pas.
- **Inactif** : appareils qui ont cessé de signaler au service Defender for Endpoint.

Vous pouvez également télécharger la liste entière au format CSV à l’aide de la **fonctionnalité d’exportation.** Pour plus d’informations sur les filtres, voir [Afficher et organiser la liste des appareils.](machines-view-overview.md)

>[!NOTE]
>Exportez la liste au format CSV pour afficher les données non filtrées. Le fichier CSV inclut tous les appareils de l’organisation, quel que soit le filtrage appliqué dans l’affichage lui-même et peut prendre beaucoup de temps à télécharger, en fonction de la taille de votre organisation.

![Capture d’écran de la page liste Appareils](images/atp-devices-list-page.png)

Vous pouvez afficher les détails de l’appareil lorsque vous cliquez sur un appareil mal configuré ou inactif.

## <a name="related-topic"></a>Rubrique connexe
- [Corriger les capteurs défectueux dans Defender pour le point de terminaison](fix-unhealthy-sensors.md)
