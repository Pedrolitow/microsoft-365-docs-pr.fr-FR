---
title: Microsoft 365 Defender’API d’incidents et le type de ressource incidents
description: Découvrez les méthodes et les propriétés du type de ressource Incidents dans Microsoft 365 Defender
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
ms.custom: api
ms.openlocfilehash: a1a3f119e0aafe75b58df9c2330a950d5ab31ead
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2022
ms.locfileid: "62172306"
---
# <a name="microsoft-365-defender-incidents-api-and-the-incidents-resource-type"></a>Microsoft 365 Defender API des incidents et le type de ressource incidents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Un [incident est](incidents-overview.md) un ensemble d’alertes associées qui permettent de décrire une attaque. Les événements de différentes entités de votre organisation sont automatiquement regroupés par Microsoft 365 Defender. Vous pouvez utiliser l’API d’incidents pour accéder par programmation aux incidents de votre organisation et aux alertes associées.

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
[Obtenir un incident](api-get-incident.md) | [Incident](api-incident.md) | Obtenez un incident unique.

## <a name="request-body-response-and-examples"></a>Corps de la demande, réponse et exemples

Reportez-vous aux articles de méthode respectifs pour plus d’informations sur la construction d’une demande ou l’analyse d’une réponse, et pour obtenir des exemples pratiques.

## <a name="common-properties"></a>Propriétés courantes

Propriété | Type | Description
-|-|-
incidentId | long | ID unique de l’incident.
redirectIncidentId | nullable long | L’ID d’incident dans le cas de l’incident en cours a été fusionné.
incidentName | chaîne | Nom de l’incident.
createdTime | DateTimeOffset | Date et heure (en UTC) de création de l’incident.
lastUpdateTime | DateTimeOffset | Date et heure (en UTC) de la dernière mise à jour de l’incident.
assignedTo | chaîne | Propriétaire de l’incident.
Sévérité  | Énum | Gravité de l’incident. Les valeurs possibles ```UnSpecified``` sont : , , et ```Informational``` ```Low``` ```Medium``` ```High``` .
status | Énum | Spécifie l’état actuel de l’incident. Les valeurs possibles sont : ```Active```, ```InProgress```, ```Resolved```, et ```Redirected```
classification | Énum | Spécification de l’incident. Les valeurs possibles sont ```Unknown```, ```FalsePositive``` et ```TruePositive```.
détermination | Énum | Spécifie la détermination de l’incident. Les valeurs possibles sont les suivantes : ```NotAvailable```, ```Apt```, ```Malware```, ```SecurityPersonnel```, ```SecurityTesting```, ```UnwantedSoftware``` et ```Other```.
étiquettes | string List | Liste des balises d’incident.
commentaires | Liste des commentaires sur les incidents | L’objet Incident Comment contient : chaîne de commentaire, chaîne createdBy et heure de date createTime.
alertes | Liste des alertes | Liste des alertes associées. Consultez des exemples dans la documentation [de l’API d’incidents](api-list-incidents.md) de liste.

## <a name="related-articles"></a>Articles connexes

- [présentation Microsoft 365 Defender API de Microsoft 365 Defender’api](api-overview.md)
- [Vue d’ensemble des incidents](incidents-overview.md)
- [API de liste des incidents](api-list-incidents.md)
- [API de mise à jour de l’incident](api-update-incidents.md)
