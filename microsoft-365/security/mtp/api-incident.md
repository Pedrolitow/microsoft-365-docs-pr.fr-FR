---
title: API d’incidents Microsoft 365 Defender et type de ressource d’incident
description: En savoir plus sur les méthodes et les propriétés du type de ressource Incident dans Microsoft 365 Defender
keywords: incident, incidents, api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 37413c3c7458527e90d4657ddfb3afb058e1dfaa
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49928353"
---
# <a name="microsoft-365-defender-incidents-api-and-the-incident-resource-type"></a>API d’incidents Microsoft 365 Defender et type de ressource incident

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations concernent des produits pré-publiés qui peuvent être considérablement modifiés avant leur commercialisation. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Un [incident est](incidents-overview.md) un ensemble d’alertes associées qui permettent de décrire une attaque. Les événements de différentes entités de votre organisation sont automatiquement agrégés par Microsoft 365 Defender. Vous pouvez utiliser l’API d’incidents pour accéder par programmation aux incidents de votre organisation et aux alertes associées.

## <a name="quotas-and-resource-allocation"></a>Quotas et allocation de ressources

Vous pouvez demander jusqu’à 50 appels par minute ou 1 500 appels par heure. Chaque méthode possède également ses propres quotas. Pour plus d’informations sur les quotas propres aux méthodes, consultez l’article respectif de la méthode que vous souhaitez utiliser.

Un code de réponse HTTP indique que vous avez atteint un quota, soit par nombre de demandes envoyées, soit par temps `429` d’exécution alloué. Le corps de la réponse inclut la durée jusqu’à ce que le quota que vous avez atteint soit réinitialisé.

## <a name="permissions"></a>Autorisations

L’API incidents nécessite différents types d’autorisations pour chacune de ses méthodes. Pour plus d’informations sur les autorisations requises, consultez l’article de la méthode respective.

## <a name="methods"></a>Méthodes

Méthode | Type renvoyé | Description
-|-|-
[Répertorier les incidents](api-list-incidents.md) | [Liste des incidents](api-incident.md) | Obtenir la liste des incidents.
[Incident de mise à jour](api-update-incidents.md) | [Incident](api-incident.md) | Mettre à jour un incident spécifique.

## <a name="request-body-response-and-examples"></a>Corps de la demande, réponse et exemples

Reportez-vous aux articles de méthode respectifs pour plus d’informations sur la construction d’une demande ou l’analyse d’une réponse, et pour obtenir des exemples pratiques.

## <a name="common-properties"></a>Propriétés courantes

Propriété | Type | Description
-|-|-
incidentId | long | ID unique de l’incident.
redirectIncidentId | nullable long | L’ID d’incident dans le cas de l’incident en cours a été fusionné.
incidentName | string | Nom de l’incident.
createdTime | DateTimeOffset | Date et heure (en UTC) de création de l’incident.
lastUpdateTime | DateTimeOffset | Date et heure (en UTC) de la dernière mise à jour de l’incident.
assignedTo | string | Propriétaire de l’incident.
Sévérité  | Énum | Gravité de l’incident. Les valeurs possibles ```UnSpecified``` sont : , , et ```Informational``` ```Low``` ```Medium``` ```High``` .
status | Énum | Spécifie l’état actuel de l’incident. Les valeurs possibles ```Active``` sont : , et ```Resolved``` ```Redirected``` .
classification | Énum | Spécification de l’incident. Les valeurs possibles sont ```Unknown```, ```FalsePositive``` et ```TruePositive```.
détermination | Énum | Spécifie la détermination de l’incident. Les valeurs possibles sont les suivantes : ```NotAvailable```, ```Apt```, ```Malware```, ```SecurityPersonnel```, ```SecurityTesting```, ```UnwantedSoftware``` et ```Other```.
étiquettes | string List | Liste des balises d’incident.
alerts | Liste des alertes | Liste des alertes associées. Consultez des exemples dans la documentation [de l’API d’incidents](api-list-incidents.md) de liste.

## <a name="related-articles"></a>Articles connexes

- [Présentation des API Microsoft 365 Defender](api-overview.md)
- [Vue d’ensemble des incidents](incidents-overview.md)
- [API de liste des incidents](api-list-incidents.md)
- [API de mise à jour de l’incident](api-update-incidents.md)
