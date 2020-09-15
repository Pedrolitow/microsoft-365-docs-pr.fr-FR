---
title: Type de ressource d’incident dans l’API de protection contre les menaces Microsoft
description: En savoir plus sur les méthodes et les propriétés du type de ressource incident dans Microsoft Threat Protection
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
ms.openlocfilehash: 310e3105c973223ea79373d770eb10f7753b917e
ms.sourcegitcommit: 9a275a13af3e063e80ce1bd3cd8142a095db92d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "47650288"
---
# <a name="incident-resource-type"></a>Type de ressource d’incident

**S’applique à :**
- Protection Microsoft contre les menaces

>[!IMPORTANT] 
>Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

## <a name="methods"></a>Méthodes

Méthode |Type renvoyé |Description
:---|:---|:---
[Répertorier les incidents](api-list-incidents.md) | Liste des [incidents](api-incident.md) | Obtenir une liste d’incidents.
[Mettre à jour l’incident](api-update-incidents.md) | [Accessoire](api-incident.md) | Mettre à jour un incident spécifique.


## <a name="properties"></a>Propriétés

Propriété |    Type    |    Description
:---|:---|:---
incidentId | long | ID unique de l’incident.
redirectIncidentId | long Nullable | ID d’incident vers lequel l’incident actuel a été fusionné.
incidentName | string | Nom de l’incident.
createdTime | DateTimeOffset | Date et heure (en UTC) de création de l’incident.
lastUpdateTime | DateTimeOffset | Date et heure de la dernière mise à jour de l’incident (en UTC).
assignedTo | string | Propriétaire de l’incident.
Sévérité  | Énum | Gravité de l’incident. Les valeurs possibles sont les suivantes : ```UnSpecified``` , ```Informational``` , ```Low``` ```Medium``` et ```High``` .
statut | Énum | Indique l’état actuel de l’incident. Les valeurs possibles sont les suivantes : ```Active``` ```Resolved``` et ```Redirected``` .
classification | Énum | Spécification de l’incident. Les valeurs possibles sont les suivantes : ```Unknown```, ```FalsePositive``` et ```TruePositive```.
indications | Énum | Indique la détermination de l’incident. Les valeurs possibles sont les suivantes : ```NotAvailable```, ```Apt```, ```Malware```, ```SecurityPersonnel```, ```SecurityTesting```, ```UnwantedSoftware``` et ```Other```.
étiquettes | Liste de chaînes | Liste des balises incident.
alerts | Liste des alertes | Liste des alertes associées. Voir des exemples dans la documentation de l’API des [incidents de liste](api-list-incidents.md) .