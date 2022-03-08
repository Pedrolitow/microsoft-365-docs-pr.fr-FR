---
title: Méthodes et propriétés de la bibliothèque de réponses en direct
description: Découvrez comment utiliser les méthodes et propriétés de la bibliothèque de réponses en direct.
keywords: api, api de graphique, api pris en charge, obtenir, appareils
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: reference
ms.technology: m365d
ms.openlocfilehash: 74f4fbe69135433597492854428b34449fbd0260
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319143"
---
#  <a name="live-response-library-methods-and-properties"></a>Méthodes et propriétés de la bibliothèque de réponses en direct

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="methods"></a>Méthodes

| **Méthode**          | **Type renvoyé**         | **Description**                         |
|---------------------|-------------------------|-----------------------------------------|
| Lister les fichiers de bibliothèque  | Collection de fichiers bibliothèque | List library file entities              |
| Télécharger bibliothèque   | Entité de fichier bibliothèque     | Télécharger fichier dans la bibliothèque de réponses en direct |
| Supprimer de la bibliothèque | Aucun contenu              | Supprimer l’entité de fichier bibliothèque              |

## <a name="properties"></a>Propriétés

| **Propriété** | **Type**                         | **Description**                                        |
|--------------|----------------------------------|--------------------------------------------------------|
| Commandes     | Collection de commandes Live Response | Tableau d’objets Command. Voir les [commandes de réponse en direct](live-response.md#live-response-commands). |

