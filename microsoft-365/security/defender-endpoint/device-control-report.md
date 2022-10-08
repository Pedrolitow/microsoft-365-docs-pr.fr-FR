---
title: Protéger les données de votre organisation avec le contrôle d’appareil
description: Surveillez la sécurité des données de votre organisation par le biais de rapports de contrôle d’appareil.
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.author: deniseb
author: denisebmsft
ms.reviewer: dansimp
ms.topic: article
manager: dansimp
audience: ITPro
ms.subservice: mde
ms.collection:
- m365-security
- tier3
search.appverid: met150
ms.openlocfilehash: 245e49f22f4846c0a48a2ebfb0855a07d0b66841
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68210127"
---
# <a name="device-control-report"></a>Rapport de contrôle d’appareil

**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender pour point de terminaison contrôle d’appareil protège contre la perte de données en surveillant et en contrôlant l’utilisation des médias par les appareils de votre organisation, par exemple à l’aide d’appareils de stockage amovibles et de lecteurs USB.

Avec le rapport de contrôle d’appareil, vous pouvez afficher les événements liés à l’utilisation du média. Ces événements incluent :

- **Événements d’audit :** Affiche le nombre d’événements d’audit qui se produisent lorsque des médias externes sont connectés.
- **Événements de stratégie :** Affiche le nombre d’événements de stratégie qui se produisent lorsqu’une stratégie de contrôle d’appareil est déclenchée.

> [!NOTE]
> L’événement d’audit permettant de suivre l’utilisation du média est activé par défaut pour les appareils intégrés à Microsoft Defender pour point de terminaison.

## <a name="understanding-the-audit-events"></a>Présentation des événements d’audit

Les événements d’audit incluent :

- **Montage et démontage du lecteur USB :** Auditez les événements générés lorsqu’un lecteur USB est monté ou démonté.
- **PnP :** Plug-and-Play événements d’audit sont générés lorsque le stockage amovible, une imprimante ou un média Bluetooth est connecté.
- **Contrôle d’accès au stockage amovible :** Les événements sont générés lorsqu’une stratégie de contrôle d’accès au stockage amovible est déclenchée. Il peut s’agir de l’audit, du bloc ou de l’autorisation.

## <a name="monitor-device-control-security"></a>Surveiller la sécurité du contrôle d’appareil

Le contrôle d’appareil dans Defender pour point de terminaison permet aux administrateurs de sécurité d’utiliser des outils qui leur permettent de suivre la sécurité du contrôle des appareils de leur organisation par le biais de rapports. Vous trouverez le rapport de contrôle d’appareil dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Accédez au rapport Rapports  > **de sécurité** **générale** > . Recherchez **la carte de contrôle d’appareil** et sélectionnez le lien pour ouvrir le rapport. 

La carte de protection de l’appareil dans le tableau de bord **Rapports** affiche le nombre d’événements d’audit générés par type de média au cours des 180 derniers jours.

Le bouton **Afficher les détails** affiche d’autres données d’utilisation du média dans la page du **rapport de contrôle d’appareil** .

La page fournit un tableau de bord avec un nombre agrégé d’événements par type et une liste d’événements et affiche 500 événements par page, mais les administrateurs peuvent faire défiler vers le bas pour afficher plus d’événements et peuvent filtrer sur l’intervalle de temps, le nom de la classe multimédia et l’ID d’appareil.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Detaileddevicecontrolreport.png" alt-text="Page Détails du rapport de contrôle d’appareil dans le portail Microsoft 365 Defender" lightbox="images/Detaileddevicecontrolreport.png":::

Lorsque vous sélectionnez un événement, un menu volant s’affiche pour vous afficher plus d’informations :

- **Détails généraux :** Date, mode Action, stratégie et accès de cet événement.
- **Informations sur les médias :** Les informations multimédias incluent le nom du média, le nom de classe, le GUID de classe, l’ID d’appareil, l’ID du fournisseur, le numéro de série et le type de bus.
- **Détails de l’emplacement :** Nom de l’appareil, utilisateur et ID d’appareil MDATP.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/devicecontrolreportfilter.png" alt-text="Page Filtrer sur le rapport de contrôle d’appareil" lightbox="images/devicecontrolreportfilter.png":::

Pour afficher l’activité en temps réel de ce média au sein de l’organisation, sélectionnez le bouton **De chasse avancé ouvert** . Cela inclut une requête incorporée prédéfinie.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicecontrolreportquery.png" alt-text="Page Requête sur le rapport de contrôle d’appareil" lightbox="images/Devicecontrolreportquery.png":::

Pour afficher la sécurité de l’appareil, sélectionnez le bouton **Ouvrir la page de l’appareil** dans le menu volant. Ce bouton ouvre la page d’entité de l’appareil.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicesecuritypage.png" alt-text="Page Entité de l’appareil" lightbox="images/Devicesecuritypage.png":::

## <a name="reporting-delays"></a>Délais de création de rapports

Il peut y avoir un délai allant jusqu’à 12 heures entre le moment où une connexion multimédia se produit et le moment où l’événement est reflété dans la carte ou dans la liste de domaines.
