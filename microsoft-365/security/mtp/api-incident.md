---
title: API Microsoft 365 Defender incidents et type de ressource incident
description: En savoir plus sur les méthodes et les propriétés du type de ressource incident dans Microsoft 365 Defender
keywords: incident, incidents, API
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
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
ms.openlocfilehash: 372c939f5eed29832725e6b048735040ca7391d6
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719333"
---
# <a name="microsoft-365-defender-incidents-api-and-the-incident-resource-type"></a>API Microsoft 365 Defender incidents et type de ressource incident

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Un [incident](incidents-overview.md) est une collection d’alertes associées qui permettent de décrire une attaque. Les événements provenant de différentes entités de votre organisation sont automatiquement regroupés par Microsoft 365 Defender. Vous pouvez utiliser l’API incidents pour accéder par programmation aux incidents et alertes connexes de votre organisation.

## <a name="quotas-and-resource-allocation"></a>Quotas et allocation des ressources

Vous pouvez demander jusqu’à 50 appels par minute ou 1500 appels par heure. Chaque méthode possède également ses propres quotas. Pour plus d’informations sur les quotas spécifiques aux méthodes, reportez-vous à l’article correspondant à la méthode que vous souhaitez utiliser.

Un `429` Code de réponse http indique que vous avez atteint un quota, soit le nombre de demandes envoyées, soit le temps d’exécution alloué. Le corps de la réponse inclura le temps jusqu’à ce que le quota que vous avez atteint soit réinitialisé.

## <a name="permissions"></a>Autorisations

L’API incidents requiert différents types d’autorisations pour chacune de ses méthodes. Pour plus d’informations sur les autorisations requises, reportez-vous à l’article de la méthode correspondante.

## <a name="methods"></a>Méthodes

Méthode | Type renvoyé | Description
-|-|-
[Répertorier les incidents](api-list-incidents.md) | Liste des [incidents](api-incident.md) | Obtenir une liste d’incidents.
[Incident de mise à jour](api-update-incidents.md) | [Accessoire](api-incident.md) | Mettre à jour un incident spécifique.

## <a name="request-body-response-and-examples"></a>Corps de la demande, réponse et exemples

Reportez-vous aux Articles de la méthode pour obtenir plus de détails sur la façon de construire une requête ou d’analyser une réponse, ainsi que pour des exemples concrets.

## <a name="common-properties"></a>Propriétés courantes

Propriété | Type | Description
-|-|-
incidentId | long | ID unique de l’incident.
redirectIncidentId | long Nullable | ID d’incident vers lequel l’incident actuel a été fusionné.
incidentName | string | Nom de l’incident.
createdTime | DateTimeOffset | Date et heure (en UTC) de création de l’incident.
lastUpdateTime | DateTimeOffset | Date et heure de la dernière mise à jour de l’incident (en UTC).
assignedTo | string | Propriétaire de l’incident.
Sévérité  | Énum | Gravité de l’incident. Les valeurs possibles sont les suivantes : ```UnSpecified``` , ```Informational``` ,, ```Low``` ```Medium``` et ```High``` .
status | Énum | Indique l’état actuel de l’incident. Les valeurs possibles sont les suivantes : ```Active``` , ```Resolved``` et ```Redirected``` .
classification | Énum | Spécification de l’incident. Les valeurs possibles sont ```Unknown```, ```FalsePositive``` et ```TruePositive```.
indications | Énum | Indique la détermination de l’incident. Les valeurs possibles sont les suivantes : ```NotAvailable```, ```Apt```, ```Malware```, ```SecurityPersonnel```, ```SecurityTesting```, ```UnwantedSoftware``` et ```Other```.
étiquettes | Liste de chaînes | Liste des balises incident.
alerts | Liste des alertes | Liste des alertes associées. Voir des exemples dans la documentation de l’API des [incidents de liste](api-list-incidents.md) .

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble des API Microsoft 365 Defender](api-overview.md)
- [Vue d’ensemble des incidents](incidents-overview.md)
- [API de liste des incidents](api-list-incidents.md)
- [Mettre à jour l’API incident](api-update-incidents.md)
