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
- M365-security-compliance
ms.topic: reference
ms.subservice: mde
ms.openlocfilehash: b130a3166db16d36c43e15545cf0f6c14d432e08
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67736803"
---
#  <a name="live-response-library-methods-and-properties"></a>Les méthodes et les propriétés de la bibliothèque de réponse en direct

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Pertahanan Microsoft untuk Titik Akhir](https://go.microsoft.com/fwlink/?linkid=2154037)

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

