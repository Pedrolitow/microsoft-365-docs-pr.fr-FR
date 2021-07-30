---
title: Type de ressource Investigation
description: Entité Microsoft Defender for Endpoint Investigation.
keywords: api, api de graphique, api pris en charge, obtenir, alertes, enquêtes
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
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 0d15f90c155a6ed14ccb29e5ab634a02b01d52b1
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53651182"
---
# <a name="investigation-resource-type"></a>Type de ressource Investigation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Représente une entité d’investigation automatisée dans Defender pour le point de terminaison.

Pour plus [d’informations, voir Vue d’ensemble des enquêtes](automated-investigations.md) automatisées.

## <a name="methods"></a>Méthodes

Méthode|Type renvoyé|Description
:---|:---|:---
[Examens de liste](get-investigation-collection.md)|Collection d’examens|Obtenir une collection d’examens
[Obtenir un examen unique](get-investigation-object.md)|Entité Investigation|Obtient une entité Investigation unique.
[Démarrer l’examen](initiate-autoir-investigation.md)|Entité Investigation|Démarre l’examen sur un appareil.

## <a name="properties"></a>Propriétés

Propriété|Type|Description
:---|:---|:---
id|Chaîne|Identité de l’entité d’investigation. 
startTime|DateTime Nullable|Date et heure de création de l’enquête.
endTime|DateTime Nullable|Date et heure de fin de l’enquête.
cancelledBy|Chaîne|ID de l’utilisateur/de l’application qui a annulé cet examen.
investigationState|Énum|État actuel de l’enquête. Les valeurs possibles sont : « Unknown » (inconnu), « Terminated » (terminé), « SuccessfullyRemediated », 'Suppress', 'Failed', 'PartiallyRemediated', 'Running', 'PendingApproval', 'PendingResource', 'PartiallyExploigated', 'TerminatedByUser', 'TerminatedBySystem', 'Queued', 'InnerFailure', 'PreexistingAlert', 'UnsupportedOs', 'UnsupportedAlertType', 'SuppressedAlert'.
statusDetails|Chaîne|Informations supplémentaires sur l’état de l’enquête.
machineId|Chaîne|ID de l’appareil sur lequel l’enquête est exécutée.
computerDnsName|Chaîne|Nom de l’appareil sur lequel l’enquête est exécutée.
triggeringAlertId|Chaîne|ID de l’alerte qui a déclenché l’enquête.

## <a name="json-representation"></a>Représentation Json

```json
{
    "id": "63004",
    "startTime": "2020-01-06T13:05:15Z",
    "endTime": null,
    "state": "Running",
    "cancelledBy": null,
    "statusDetails": null,
    "machineId": "e828a0624ed33f919db541065190d2f75e50a071",
    "computerDnsName": "desktop-test123",
    "triggeringAlertId": "da637139127150012465_1011995739"
}
```
