---
title: Protéger les données de votre organisation avec le contrôle d’appareil
description: Surveillez la sécurité des données de votre organisation via des rapports de contrôle des appareils.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
ms.author: deniseb
author: denisebmsft
ms.reviewer: dansimp
ms.topic: article
manager: dansimp
audience: ITPro
ms.technology: mde
ms.openlocfilehash: 9309d0b1bc5a83495af344b699b45e6e21d7e1d65dab6511e31880ee11ec4bfb
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53811304"
---
# <a name="protect-your-organizations-data-with-device-control"></a>Protéger les données de votre organisation avec le contrôle d’appareil

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2069559)

Le contrôle d’appareil Microsoft Defender for Endpoint protège contre la perte de données en surveillant et en contrôlant l’utilisation des supports par les appareils de votre organisation, tels que l’utilisation de périphériques de stockage amovibles et de lecteurs USB.

Avec le rapport de contrôle d’appareil, vous pouvez afficher les événements liés à l’utilisation des médias, tels que :

- **Événements d’audit :** Indique le nombre d’événements d’audit qui se produisent lorsque des médias externes sont connectés.
- **Événements de stratégie :** Indique le nombre d’événements de stratégie qui se produisent lorsqu’une stratégie de contrôle d’appareil est déclenchée.

> [!NOTE]
> L’événement d’audit permettant de suivre l’utilisation des médias est activé par défaut pour les appareils intégrés à Microsoft Defender for Endpoint.

## <a name="understanding-the-audit-events"></a>Comprendre les événements d’audit

Les événements d’audit sont les suivants :

- **Montage et démontage du lecteur USB :** Auditer les événements générés lorsqu’un lecteur USB est monté ou démonté.
- **PnP :** Les événements d’audit plug-and-play sont générés lorsque le stockage amovible, une imprimante ou Bluetooth multimédia est connecté.

## <a name="monitor-device-control-security"></a>Surveiller la sécurité des contrôles d’appareil

Le contrôle d’appareil dans Microsoft Defender pour point de terminaison permet aux administrateurs de sécurité d’utiliser des outils qui leur permettent de suivre la sécurité des contrôles d’appareil de leur organisation via des rapports. Vous pouvez trouver le rapport de contrôle d’appareil dans le centre Microsoft 365 sécurité en allant dans **Rapports > Protection des appareils.**

La carte de  protection des appareils du tableau de bord Rapports indique le nombre d’événements d’audit générés par type de média au cours des 180 derniers jours.

> [!div class="mx-imgBorder"]
> ![DeviceControlReportCard](images/devicecontrolcard.png)

Le **bouton Afficher les détails** affiche davantage de données d’utilisation des médias dans la page de rapport de contrôle **d’appareil.**

La page fournit un tableau de bord avec un nombre agrégé d’événements par type et une liste d’événements. Les administrateurs peuvent filtrer sur la plage de temps, le nom de la classe multimédia et l’ID de l’appareil.

> [!div class="mx-imgBorder"]
> ![DeviceControlReportDetails](images/Detaileddevicecontrolreport.png)

Lorsque vous sélectionnez un événement, un flyout s’affiche pour vous fournir plus d’informations :

- **Détails généraux :** Date, mode Action et stratégie de cet événement.
- **Informations multimédias :** Les informations multimédias incluent le nom du média, le nom de la classe, le GUID de classe, l’ID de l’appareil, l’ID du fournisseur, le volume, le numéro de série et le type de bus.
- **Détails de l’emplacement :** Nom de l’appareil et ID de l’appareil MDATP.

> [!div class="mx-imgBorder"]
> ![FilterOnDeviceControlReport](images/devicecontrolreportfilter.png)

Pour voir l’activité en temps réel de ce média au sein de l’organisation, sélectionnez le bouton de recherche **Open Advanced.** Cela inclut une requête prédéfinie incorporée.

> [!div class="mx-imgBorder"]
> ![QueryOnDeviceControlReport](images/Devicecontrolreportquery.png)

Pour voir la sécurité de l’appareil, sélectionnez le bouton Ouvrir la **page** de l’appareil dans le volant. Ce bouton ouvre la page d’entité de l’appareil.

> [!div class="mx-imgBorder"]
> ![DeviceEntityPage](images/Devicesecuritypage.png)

## <a name="reporting-delays"></a>Signalement des retards

Le rapport de contrôle d’appareil peut avoir un délai de 12 heures entre le moment où une connexion multimédia se produit et le moment où l’événement est reflété dans la carte ou dans la liste des domaines.
