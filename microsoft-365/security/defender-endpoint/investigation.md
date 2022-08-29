---
title: Type de ressource d’investigation
description: Microsoft Defender pour point de terminaison entité Investigation.
keywords: api, api graphe, api prises en charge, get, alertes, investigations
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: f7715c8711bfa479533afe2f0b69c9d3f7ad768f
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67326494"
---
# <a name="investigation-resource-type"></a>Type de ressource d’investigation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

Représente une entité d’investigation automatisée dans Defender pour point de terminaison.

Pour plus [d’informations, consultez Vue d’ensemble des enquêtes automatisées](automated-investigations.md).

## <a name="methods"></a>Méthodes

Méthode|Type renvoyé|Description
:---|:---|:---
[Répertorier les investigations](get-investigation-collection.md)|Collection d’investigations|Obtenir la collection d’investigations
[Obtenir une seule investigation](get-investigation-object.md)|Entité d’investigation|Obtient une seule entité Investigation.
[Démarrer l’examen](initiate-autoir-investigation.md)|Entité d’investigation|Démarre l’investigation sur un appareil.

## <a name="properties"></a>Propriétés

Propriété|Type|Description
:---|:---|:---
ID|Chaîne|Identité de l’entité d’investigation. 
startTime|DateTime Nullable|Date et heure de création de l’enquête.
endTime|DateTime Nullable|Date et heure de fin de l’enquête.
cancelledBy|Chaîne|ID de l’utilisateur/application qui a annulé cette enquête.
État|Énum|État actuel de l’enquête. Les valeurs possibles sont : ' Unknown', 'Terminateed', 'SuccessfullyRemediated', 'Benign', 'Failed', 'PartiallyRemediated', 'Running', 'PendingApproval', 'PendingResource', 'PartiallyInvestigated', 'TerminateedByUser', 'TerminateedBySystem', 'Queued', 'InnerFailure', 'PreexistingAlert', 'UnsupportedOs', 'UnsupportedAlertType', 'SuppressedAlert'.
statusDetails|Chaîne|Informations supplémentaires sur l’état de l’enquête.
machineId|Chaîne|ID de l’appareil sur lequel l’enquête est exécutée.
computerDnsName|Chaîne|Nom de l’appareil sur lequel l’investigation est exécutée.
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
