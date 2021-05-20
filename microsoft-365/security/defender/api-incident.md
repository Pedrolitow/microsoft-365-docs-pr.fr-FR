---
title: Microsoft 365 API d’incidents de défenseur et type de ressource d’incident
description: Renseignez-vous sur les méthodes et les propriétés du type de ressource incident dans Microsoft 365 Defender
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 5cc149668e49e21b38b5fb95ae3f40db6c296e1d
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572584"
---
# <a name="microsoft-365-defender-incidents-api-and-the-incident-resource-type"></a>Microsoft 365 API des incidents de défense et le type de ressource d’incident

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Un [incident](incidents-overview.md) est une collection d’alertes connexes qui aident à décrire une attaque. Les événements de différentes entités de votre organisation sont automatiquement regroupés par Microsoft 365 Defender. Vous pouvez utiliser l’API incidents pour accéder de façon programmatique aux incidents et aux alertes connexes de votre organisation.

## <a name="quotas-and-resource-allocation"></a>Quotas et allocation des ressources

Vous pouvez demander jusqu’à 50 appels par minute ou 1500 appels par heure. Chaque méthode a également ses propres quotas. Pour plus d’informations sur les quotas spécifiques à la méthode, consultez l’article respectif de la méthode que vous souhaitez utiliser.

Un `429` code de réponse HTTP indique que vous avez atteint un quota, soit par le nombre de demandes envoyées, soit par temps de fonctionnement alloué. L’organe d’intervention inclura le temps jusqu’à ce que le quota que vous avez atteint soit réinitialisé.

## <a name="permissions"></a>Autorisations

L’API incidents nécessite différents types d’autorisations pour chacune de ses méthodes. Pour plus d’informations sur les autorisations requises, consultez l’article de la méthode respective.

## <a name="methods"></a>Méthodes

Méthode | Type renvoyé | Description
-|-|-
[Répertorier les incidents](api-list-incidents.md) | [Liste des](api-incident.md) incidents | Obtenez une liste d’incidents.
[Incident de mise à jour](api-update-incidents.md) | [Incident](api-incident.md) | Mettez à jour un incident spécifique.

## <a name="request-body-response-and-examples"></a>Corps de demande, réponse, et exemples

Consultez les articles de méthode respectifs pour plus de détails sur la façon de construire une demande ou d’affiner une réponse, et pour des exemples pratiques.

## <a name="common-properties"></a>Propriétés courantes

Propriété | Type | Description
-|-|-
incidentId | long | Pièce d’identité unique incident.
redirectIncidentId | nullable long | L’ID incident de l’incident actuel a été fusionné.
incidentName | string | Le nom de l’incident.
createdTime (en) | DateTimeOffset | La date et l’heure (dans UTC) l’incident a été créé.
lastUpdateTime (en) | DateTimeOffset | La date et l’heure (dans UTC) l’incident a été mis à jour pour la dernière fois.
assignedTo | string | Propriétaire de l’incident.
Sévérité  | Énum | Gravité de l’incident. Les valeurs possibles sont : ```UnSpecified``` , , , , et ```Informational``` ```Low``` ```Medium``` ```High``` .
statut | Énum | Spécifie l’état actuel de l’incident. Les valeurs possibles sont: ```Active``` ```Resolved``` , , et ```Redirected``` .
classification | Énum | Spécification de l’incident. Les valeurs possibles sont les suivantes : ```Unknown```, ```FalsePositive``` et ```TruePositive```.
détermination | Énum | Précise la détermination de l’incident. Les valeurs possibles sont les suivantes : ```NotAvailable```, ```Apt```, ```Malware```, ```SecurityPersonnel```, ```SecurityTesting```, ```UnwantedSoftware``` et ```Other```.
étiquettes | liste des cordes | Liste des balises incidentes.
commentaires | Liste des commentaires sur les incidents | Incident Commentaire objet contient: chaîne de commentaires, crééPar chaîne, et créertime date time.
alerts | Liste d’alerte | Liste des alertes connexes. Voir les exemples de documentation [api sur les incidents](api-list-incidents.md) de liste.

## <a name="related-articles"></a>Articles connexes

- [Microsoft 365 Vue d’ensemble des API Defender](api-overview.md)
- [Vue d’ensemble des incidents](incidents-overview.md)
- [Liste des incidents API](api-list-incidents.md)
- [Mise à jour de l’API incident](api-update-incidents.md)
