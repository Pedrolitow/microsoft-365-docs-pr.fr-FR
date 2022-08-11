---
title: notes de publication de l’API Microsoft Defender pour point de terminaison
description: Notes de publication pour les mises à jour apportées à l’ensemble Microsoft Defender pour point de terminaison d’API.
keywords: Microsoft Defender pour point de terminaison notes de publication de l’API, mde, API, API Microsoft Defender pour point de terminaison, mises à jour, notes, publication
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 3087d5cb22f7cc8ef1afedad73de027caf00771e
ms.sourcegitcommit: 414682b9bf42dc19a89c893d3c515aee9765b6e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2022
ms.locfileid: "67280440"
---
# <a name="microsoft-defender-for-endpoint-api-release-notes"></a>notes de publication de l’API Microsoft Defender pour point de terminaison

**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

>Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Les informations suivantes répertorient les mises à jour apportées aux API Microsoft Defender pour point de terminaison et les dates de leur création.

> [!TIP]
> Flux RSS : recevez une notification lorsque cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux :
>
> ```http
> /api/search/rss?search=%22Release+notes+for+updates+made+to+the+Microsoft+Defender+for+Endpoint+set+of+APIs%22&locale=en-us&facet=&%24filter=scopes%2Fany%28t%3A+t+eq+%27Windows+10%27%29
> ```

## <a name="release-notes---newest-to-oldest-ddmmyyyy"></a>Notes de publication - la plus récente à la plus ancienne (dd.mm.yyyy)

### <a name="08082022"></a>08.08.2022

- Ajout d’une nouvelle méthode d’API Export Device Health - GET /api/public/avdeviceshealth [Export device health methods and properties](device-health-api-methods-properties.md)

### <a name="06102021"></a>06.10.2021

- Ajout d’une nouvelle méthode d’API d’évaluation d’exportation - _Delta Export software vulnerabilities assessment (réponse JSON)_ [Export assessment methods and properties per device](get-assessment-methods-properties.md).

### <a name="05252021"></a>05.25.2021

- Ajout de nouvelles [méthodes et propriétés d’évaluation d’exportation](get-assessment-methods-properties.md) d’API par appareil.

### <a name="03052021"></a>03.05.2021

- Ajout d’une nouvelle API : [méthodes et propriétés de l’activité de correction](get-remediation-methods-properties.md).

### <a name="10022021"></a>10.02.2021

- Ajout d’une nouvelle API : [alertes de mise à jour par lot](batch-update-alerts.md).

### <a name="25012021"></a>25.01.2021

- Mise à jour des limitations de débit pour [l’API De chasse avancée](run-advanced-query-api.md) de 15 à 45 demandes par minute.

### <a name="21012021"></a>21.01.2021

- Ajout d’une nouvelle API : [Rechercher des appareils par balise](machine-tags.md).
- Ajout d’une nouvelle API : [Importer des indicateurs](import-ti-indicators.md).

### <a name="03012021"></a>03.01.2021

- Mise à jour de la preuve d’alerte : ajout des propriétés ***detectionStatus** _, _*_parentProcessFilePath_*_ et _ *_parentProcessFileName_**.
- Entité [Alert](alerts.md) mise à jour : ajout de ***la propriété detectorId*** .

### <a name="15122020"></a>15.12.2020

- Entité [d’appareil](machine.md) mise à jour : ajout de la liste ***IpInterfaces*** . Voir [Répertorier les appareils](get-machines.md).

### <a name="04112020"></a>04.11.2020

- Ajout d’une nouvelle API : [définissez la valeur de l’appareil](set-device-value.md).
- Entité [d’appareil](machine.md) mise à jour : propriété ***deviceValue*** ajoutée.

### <a name="01092020"></a>01.09.2020

- Ajout de l’option permettant de développer l’entité Alert avec sa preuve associée. Voir [Alertes de liste](get-alerts.md).
