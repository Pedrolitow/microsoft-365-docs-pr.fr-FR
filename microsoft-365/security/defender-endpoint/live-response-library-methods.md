---
title: Les méthodes et les propriétés de la bibliothèque de réponse en direct
description: Découvrez comment utiliser les méthodes et les propriétés de la bibliothèque de réponses actives.
keywords: api, api graphe, api prises en charge, get, appareils
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
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
ms.collection:
- m365-security
- tier3
ms.topic: reference
ms.subservice: mde
ms.openlocfilehash: bf9c43caf1dc520b14d923b78a8696be258f2439
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68226688"
---
#  <a name="live-response-library-methods-and-properties"></a>Les méthodes et les propriétés de la bibliothèque de réponse en direct

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="methods"></a>Méthodes

| **Méthode**          | **Type renvoyé**         | **Description**                         |
|---------------------|-------------------------|-----------------------------------------|
| Répertorier les fichiers d’une bibliothèque  | Collection de fichiers de bibliothèque | Répertorier les entités de fichier de bibliothèque              |
| Charger dans la bibliothèque   | Entité de fichier de bibliothèque     | Charger un fichier dans la bibliothèque de réponses dynamiques |
| Supprimer de la bibliothèque | Aucun contenu              | Supprimer l’entité de fichier de bibliothèque              |

## <a name="properties"></a>Propriétés

| **Propriété** | **Type**                         | **Description**                                        |
|--------------|----------------------------------|--------------------------------------------------------|
| Commandes     | Collection de commandes Live Response | Tableau d’objets Command. Consultez [les commandes de réponse en direct](live-response.md#live-response-commands). |

