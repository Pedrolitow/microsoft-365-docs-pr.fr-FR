---
title: Vérifier l’état d’intégrité du capteur à Microsoft Defender pour point de terminaison
description: Vérifiez l’intégrité du capteur sur les appareils pour identifier celles qui sont mal configurées, inactives ou qui ne signalent pas les données de capteur.
keywords: capteur, intégrité du capteur, mal configuré, inactif, aucune donnée de capteur, données de capteur, communications altérées, communication
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.date: 04/24/2018
search.appverid: met150
ms.openlocfilehash: 4763b5dd37510b1d63fac67dd764fc2b0a0f135a
ms.sourcegitcommit: b9282493c371d59c2e583b9803825096499b5e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68157455"
---
# <a name="check-sensor-health-state-at-microsoft-defender-for-endpoint"></a>Vérifier l’état d’intégrité du capteur à Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-checksensor-abovefoldlink)

La vignette **Appareils présentant des problèmes de capteur** fournit des informations sur la capacité de chaque appareil à fournir des données de capteur et à communiquer avec le service Defender pour point de terminaison. Elle indique le nombre d’appareils qui nécessitent une attention particulière et vous aide à identifier les appareils problématiques et à prendre des mesures pour les corriger.

La vignette comporte deux indicateurs d’état qui fournissent des informations sur le nombre d’appareils qui ne sont pas correctement signalés au service :

- **Mal configurés** : ces appareils peuvent en partie signaler des données de capteur au service Defender pour point de terminaison et présenter des erreurs de configuration qui doivent être corrigées.
- **Inactif** : appareils qui ont cessé de faire rapport au service Defender pour point de terminaison pendant plus de sept jours au cours du dernier mois.

Le fait de cliquer sur l’un des groupes vous dirige vers la **liste Des appareils**, filtré selon votre choix.

:::image type="content" source="images/atp-devices-with-sensor-issues-tile.png" alt-text="Vignette Appareils présentant des problèmes de capteur" lightbox="images/atp-devices-with-sensor-issues-tile.png":::

Dans **la liste Des appareils**, vous pouvez filtrer la liste des états d’intégrité en fonction de l’état suivant :

- **Actif** : appareils qui signalent activement au service Defender pour point de terminaison.
- **Mal configurés** : ces appareils peuvent signaler partiellement les données de capteur au service Defender pour point de terminaison, mais présentent des erreurs de configuration qui doivent être corrigées. Les appareils mal configurés peuvent avoir l’un ou l’autre des problèmes suivants :
  - **Aucune donnée de capteur** : les appareils ont cessé d’envoyer des données de capteur. Des alertes limitées peuvent être déclenchées à partir de l’appareil.
  - **Communications altérées** : la capacité de communiquer avec l’appareil est altérée. Il est possible que l'envoi de fichiers pour une analyse approfondie, le blocage de fichiers, l'isolement de l'appareil du réseau et d'autres actions qui nécessitent une communication avec l'appareil ne fonctionnent pas.
- **Inactif** : appareils qui ont cessé de faire rapport au service Defender pour point de terminaison.

Vous pouvez également télécharger la liste entière au format CSV à l’aide de la fonctionnalité **Exporter** . Pour plus d’informations sur les filtres, consultez [Afficher et organiser la liste des appareils](machines-view-overview.md).

> [!NOTE]
> Exportez la liste au format CSV pour afficher les données non filtrées. Le fichier CSV inclut tous les appareils de l’organisation, quel que soit le filtrage appliqué dans la vue elle-même et peut prendre beaucoup de temps à télécharger, en fonction de la taille de votre organisation.

:::image type="content" source="images/atp-devices-list-page.png" alt-text="Onglet Exporter dans la page Liste des appareils" lightbox="images/atp-devices-list-page.png":::

Vous pouvez afficher les détails de l’appareil lorsque vous cliquez sur un appareil mal configuré ou inactif.

## <a name="see-also"></a>Voir aussi

- [Correction des capteurs défectueux dans Defender pour point de terminaison](fix-unhealthy-sensors.md)
- [Vue d’ensemble de l’analyseur client](overview-client-analyzer.md)
- [Télécharger et exécuter l’analyseur client](download-client-analyzer.md)
- [Exécuter l’analyseur client sur Windows](run-analyzer-windows.md)
- [Exécuter l’analyseur client sur macOS ou Linux](run-analyzer-macos-linux.md)
- [Collecte de données pour la résolution avancée des problèmes sur Windows](data-collection-analyzer.md)
