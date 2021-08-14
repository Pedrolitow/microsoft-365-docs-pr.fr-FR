---
title: Notes de publication de l’API Microsoft Defender for Endpoint
description: Notes de publication pour les mises à jour de l’ensemble d’API Microsoft Defender for Endpoint.
keywords: Notes de publication de l’API Microsoft Defender pour endpoint, mde, API, API Microsoft Defender pour point de terminaison, mises à jour, notes, publication
search.product: eADQiWindows 10XVcnh
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 4967ba6ba0bc2fca6310e2a1347bfc1acd9e1bd726756b9599151a0eb3d30510
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53818754"
---
# <a name="microsoft-defender-for-endpoint-api-release-notes"></a>Notes de publication de l’API Microsoft Defender for Endpoint

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Les informations suivantes répertorient les mises à jour des API Microsoft Defender for Endpoint et les dates de leur mise à jour.

> [!TIP]
> Flux RSS : recevez une notification lorsque cette page est mise à jour en copiant et en coller l’URL suivante dans votre lecteur de flux :
>
> ```http
> /api/search/rss?search=%22Release+notes+for+updates+made+to+the+Microsoft+Defender+for+Endpoint+set+of+APIs%22&locale=en-us&facet=&%24filter=scopes%2Fany%28t%3A+t+eq+%27Windows+10%27%29
> ```

## <a name="release-notes---newest-to-oldest-ddmmyyyy"></a>Notes de publication - du plus récent au plus ancien (dd.mm.yyyy)

### <a name="06102021"></a>06.10.2021

- Ajout d’une nouvelle méthode d’API d’évaluation d’exportation - _Delta Export software vulnerabilities assessment (JSON response)_ Export assessment [methods and properties per device](get-assessment-methods-properties.md).

### <a name="05252021"></a>05.25.2021

- Ajout de nouvelles méthodes et propriétés d’évaluation d’exportation d’API [par appareil.](get-assessment-methods-properties.md)

### <a name="03052021"></a>03.05.2021

- Ajout d’une nouvelle API : [méthodes et propriétés d’activité de correction.](get-remediation-methods-properties.md)

### <a name="10022021"></a>10.02.2021

- Ajout d’une nouvelle API : [alertes de mise à jour par lot.](batch-update-alerts.md)

### <a name="25012021"></a>25.01.2021

- Limitations de taux mises à jour pour [l’API](run-advanced-query-api.md) de recherche avancée de 15 à 45 demandes par minute.

### <a name="21012021"></a>21.01.2021

- Ajout d’une nouvelle API : [rechercher des appareils par balise.](machine-tags.md)
- Ajout d’une nouvelle API : [indicateurs d’importation.](import-ti-indicators.md)

### <a name="03012021"></a>03.01.2021

- Preuve d’alerte mise à jour : ajout des propriétés ***detectionStatus** _, _*_parentProcessFilePath_*_ et _ *_parentProcessFileName_** .
- Entité [Alert mise à jour :](alerts.md)ajout de la propriété ***détecteurId.***

### <a name="15122020"></a>15.12.2020

- Entité [Device](machine.md) mise à jour : liste ***IpInterfaces*** ajoutée. Voir [Les appareils de liste.](get-machines.md)

### <a name="04112020"></a>04.11.2020

- Ajout d’une nouvelle API : [définir la valeur de l’appareil.](set-device-value.md)
- Entité [Device](machine.md) mise à jour : ajout de ***la propriété deviceValue.***

### <a name="01092020"></a>01.09.2020

- Ajout d’une option pour développer l’entité Alerte avec sa preuve associée. Voir [Alertes de liste.](get-alerts.md)
