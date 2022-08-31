---
title: Microsoft 365 Defender les API d’incidents et le type de ressource incidents
description: En savoir plus sur les méthodes et les propriétés du type de ressource Incidents dans Microsoft 365 Defender
keywords: incident, incidents, api
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.custom: api
ms.openlocfilehash: 8531a2f647f9f8adaeb952c08cae596142fc884f
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67471365"
---
# <a name="microsoft-365-defender-incidents-api-and-the-incidents-resource-type"></a>Microsoft 365 Defender l’API incidents et le type de ressource incidents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Un [incident](incidents-overview.md) est une collection d’alertes associées qui aident à décrire une attaque. Les événements de différentes entités de votre organisation sont automatiquement agrégés par Microsoft 365 Defender. Vous pouvez utiliser l’API incidents pour accéder par programmation aux incidents de votre organisation et aux alertes associées.

## <a name="quotas-and-resource-allocation"></a>Quotas et allocation de ressources

Vous pouvez demander jusqu’à 50 appels par minute ou 1 500 appels par heure. Chaque méthode a également ses propres quotas. Pour plus d’informations sur les quotas spécifiques à la méthode, consultez l’article correspondant pour la méthode que vous souhaitez utiliser.

Un `429` code de réponse HTTP indique que vous avez atteint un quota, soit par nombre de demandes envoyées, soit par temps d’exécution alloué. Le corps de la réponse inclut le temps jusqu’à ce que le quota que vous avez atteint soit réinitialisé.

## <a name="permissions"></a>Autorisations

L’API incidents nécessite différents types d’autorisations pour chacune de ses méthodes. Pour plus d’informations sur les autorisations requises, consultez l’article de la méthode correspondante.

## <a name="methods"></a>Méthodes

Méthode | Type renvoyé | Description
-|-|-
[Répertorier les incidents](api-list-incidents.md) | [Liste des incidents](api-incident.md) | Obtenir la liste des incidents.
[Incident de mise à jour](api-update-incidents.md) | [Incident](api-incident.md) | Mettre à jour un incident spécifique.
[Obtenir un incident](api-get-incident.md) | [Incident](api-incident.md) | Obtenez un seul incident.

## <a name="request-body-response-and-examples"></a>Corps de la demande, réponse et exemples

Reportez-vous aux articles de méthode respectifs pour plus d’informations sur la construction d’une demande ou l’analyse d’une réponse, et pour obtenir des exemples pratiques.

## <a name="common-properties"></a>Propriétés courantes

Propriété | Type | Description
-|-|-
incidentId | long | ID unique de l’incident.
redirectIncidentId | valeur nullable long | ID d’incident vers lequel l’incident actuel a été fusionné.
incidentName | chaîne | Nom de l’incident.
createdTime | DateTimeOffset | Date et heure (en UTC) de création de l’incident.
lastUpdateTime | DateTimeOffset | Date et heure (UTC) de la dernière mise à jour de l’incident.
assignedTo | chaîne | Propriétaire de l’incident.
Sévérité  | Énum | Gravité de l’incident. Les valeurs possibles sont : ```UnSpecified```, ```Informational```, ```Low```, ```Medium```et ```High```.
status | Énum | Spécifie l’état actuel de l’incident. Les valeurs possibles sont : ```Active```, ```InProgress```, ```Resolved```, et ```Redirected```
classification | Énum | Spécification de l’incident. Les valeurs possibles sont ```Unknown```, ```FalsePositive``` et ```TruePositive```.
Détermination | Énum | Spécifie la détermination de l’incident. Les valeurs possibles sont les suivantes : ```NotAvailable```, ```Apt```, ```Malware```, ```SecurityPersonnel```, ```SecurityTesting```, ```UnwantedSoftware``` et ```Other```.
étiquettes | string List | Liste des balises d’incident.
commentaires | Liste des commentaires d’incident | L’objet Commentaire d’incident contient : chaîne de commentaire, chaîne createdBy et heure de date createTime.
alertes | Liste des alertes | Liste des alertes associées. Consultez des exemples dans la documentation [de l’API List incidents](api-list-incidents.md) .

>[!NOTE]
>Vers le 29 août 2022, les valeurs de détermination d’alerte précédemment prises en charge (« Apt » et « SecurityPersonnel ») seront déconseillées et ne seront plus disponibles via l’API.

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble des API Microsoft 365 Defender](api-overview.md)
- [Vue d’ensemble des incidents](incidents-overview.md)
- [Répertorier l’API d’incidents](api-list-incidents.md)
- [Mettre à jour l’API d’incident](api-update-incidents.md)
