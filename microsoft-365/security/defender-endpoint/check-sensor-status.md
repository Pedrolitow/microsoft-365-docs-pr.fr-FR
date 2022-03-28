---
title: Vérifier l’état d’état du capteur auprès de Microsoft Defender for Endpoint
description: Vérifiez l’état du capteur sur les appareils pour identifier ceux qui sont mal configurés, inactifs ou qui ne rapportent pas de données de capteur.
keywords: capteur, état du capteur, mal configuré, inactif, aucune donnée de capteur, données du capteur, communications altérées, communication
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
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: bba5fde870b2916501f4154c6ff628a0d2e3ff1f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465469"
---
# <a name="check-sensor-health-state-at-microsoft-defender-for-endpoint"></a>Vérifier l’état d’état du capteur sur Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-checksensor-abovefoldlink)

La vignette **Appareils avec problèmes de** capteur se trouve dans le tableau de bord Opérations de sécurité. Cette vignette fournit des informations sur la capacité de chaque appareil à fournir des données de capteur et à communiquer avec le service Defender for Endpoint. Elle indique le nombre d’appareils qui nécessitent une attention particulière et vous aide à identifier les appareils problématiques et à prendre des mesures pour les corriger.

Il existe deux indicateurs d’état sur la vignette qui fournissent des informations sur le nombre d’appareils qui ne sont pas correctement signalés au service :

- **Mal configuré :** ces appareils peuvent signaler partiellement des données de capteur au service Defender for Endpoint et peuvent avoir des erreurs de configuration qui doivent être corrigées.
- **Inactif** : appareils qui ont cessé de signaler au service Defender for Endpoint pendant plus de sept jours au cours du mois précédent.

Le fait de cliquer sur l’un des groupes vous dirige **vers la liste** Appareils, filtrée en fonction de votre choix.

:::image type="content" source="images/atp-devices-with-sensor-issues-tile.png" alt-text="Vignette des appareils avec problèmes de capteur" lightbox="images/atp-devices-with-sensor-issues-tile.png":::

Dans **la liste Appareils**, vous pouvez filtrer la liste d’état selon l’état suivant :

- **Actif** : appareils qui font activement des rapports au service Defender for Endpoint.
- **Mal configuré :** ces appareils peuvent signaler partiellement des données de capteur au service Defender for Endpoint, mais ont des erreurs de configuration qui doivent être corrigées. Les appareils mal configurés peuvent avoir l’un ou l’autre des problèmes suivants :
  - **Aucune donnée de capteur** : les appareils ont cessé d’envoyer des données de capteur. Des alertes limitées peuvent être déclenchées à partir de l’appareil.
  - **Communications réduites** : la capacité de communication avec l’appareil est réduite. Il est possible que l'envoi de fichiers pour une analyse approfondie, le blocage de fichiers, l'isolement de l'appareil du réseau et d'autres actions qui nécessitent une communication avec l'appareil ne fonctionnent pas.
- **Inactif** : appareils qui ont cessé de signaler au service Defender for Endpoint.

Vous pouvez également télécharger la liste entière au format CSV à l’aide de la **fonctionnalité d’exportation** . Pour plus d’informations sur les filtres, voir [Afficher et organiser la liste Appareils](machines-view-overview.md).

> [!NOTE]
> Exportez la liste au format CSV pour afficher les données non filtrées. Le fichier CSV inclut tous les appareils de l’organisation, quel que soit le filtrage appliqué dans l’affichage lui-même et peut prendre beaucoup de temps à télécharger, en fonction de la taille de votre organisation.

:::image type="content" source="images/atp-devices-list-page.png" alt-text="Onglet Exporter dans la page Liste des appareils" lightbox="images/atp-devices-list-page.png":::

Vous pouvez afficher les détails de l’appareil lorsque vous cliquez sur un appareil mal configuré ou inactif.

## <a name="see-also"></a>Voir aussi

- [Corriger les capteurs défectueux dans Defender pour le point de terminaison](fix-unhealthy-sensors.md)
- [Vue d’ensemble de l’analyseur client](overview-client-analyzer.md)
- [Télécharger et exécuter l’analyseur client](download-client-analyzer.md)
- [Exécuter l’analyseur client sur Windows](run-analyzer-windows.md)
- [Exécuter l’analyseur client sur macOS ou Linux](run-analyzer-macos-linux.md)
- [Collecte de données pour la résolution avancée des problèmes sur Windows](data-collection-analyzer.md)
