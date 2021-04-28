---
title: Notes de publication de l'API Microsoft Defender for Endpoint
description: Notes de publication pour les mises à jour de l'ensemble d'API Microsoft Defender for Endpoint.
keywords: Notes de publication de l'API Microsoft Defender pour endpoint, mde, API, API Microsoft Defender pour point de terminaison, mises à jour, notes, publication
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
ms.technology: mde
ms.openlocfilehash: 7bae413028a0add7e5288e52bc3184e30f319c46
ms.sourcegitcommit: 9063c7a50a1d7dd6d2e1ca44f53d3c26f21f4ae8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52073837"
---
# <a name="microsoft-defender-for-endpoint-api-release-notes"></a>Notes de publication de l'API Microsoft Defender for Endpoint

**S'applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Les informations suivantes répertorient les mises à jour des API Microsoft Defender for Endpoint et les dates de leur mise à jour.

> [!TIP]
> Flux RSS : recevez une notification lorsque cette page est mise à jour en copiant et en coller l'URL suivante dans votre lecteur de flux :
>
> ```http
> https://docs.microsoft.com/api/search/rss?search=%22Release+notes+for+updates+made+to+the+Microsoft+Defender+for+Endpoint+set+of+APIs%22&locale=en-us&facet=&%24filter=scopes%2Fany%28t%3A+t+eq+%27Windows+10%27%29
> ```

## <a name="release-notes---newest-to-oldest"></a>Notes de publication - plus récent à plus ancien

### <a name="10022021"></a>10.02.2021

- Ajout d'une nouvelle API : [alertes de mise à jour par lot.](batch-update-alerts.md)

### <a name="25012021"></a>25.01.2021

- Limitations de taux mises à jour pour [l'API](run-advanced-query-api.md) de recherche avancée de 15 à 45 demandes par minute.

### <a name="21012021"></a>21.01.2021

- Ajout d'une nouvelle API : [rechercher des appareils par balise.](machine-tags.md)
- Ajout d'une nouvelle API : [importer des indicateurs.](import-ti-indicators.md)

### <a name="03012021"></a>03.01.2021

- Preuve d'alerte mise à jour : ajout des propriétés ***detectionStatus** _, _*_parentProcessFilePath_*_ et _ *_parentProcessFileName_** .
- Entité [Alert mise à jour :](alerts.md)ajout de la propriété ***détecteurId.***

### <a name="15122020"></a>15.12.2020

- Entité [Device](machine.md) mise à jour : liste ***IpInterfaces*** ajoutée. Voir [Les appareils de liste.](get-machines.md)

### <a name="04112020"></a>04.11.2020

- Ajout d'une nouvelle API : [définir la valeur de l'appareil.](set-device-value.md)
- Entité [Device](machine.md) mise à jour : ajout de ***la propriété deviceValue.***

### <a name="01092020"></a>01.09.2020

- Ajout d'une option pour développer l'entité Alerte avec sa preuve associée. Voir [Alertes de liste.](get-alerts.md)
