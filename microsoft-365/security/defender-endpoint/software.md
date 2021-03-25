---
title: Méthodes et propriétés logicielles
description: Récupère les principales alertes récentes.
keywords: api, api de graphique, api pris en charge, obtenir, alertes, récent
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 9bfec2c4e65a390189556c14347eaf17236fb95e
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51187199"
---
# <a name="software-resource-type"></a>Type de ressource logicielle

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Méthodes

Méthode |Type renvoyé |Description
:---|:---|:---
[List software](get-software.md) | Collection de logiciels | Liste de l’inventaire logiciel de l’organisation.
[Obtenir le logiciel par ID](get-software-by-id.md) | Logiciels | Obtenez un logiciel spécifique par son ID logiciel.
[Liste de la distribution des versions des logiciels](get-software-ver-distribution.md)| Collection de distribution | Liste de la distribution des versions des logiciels par ID logiciel.
[Lister les ordinateurs par logiciel](get-machines-by-software.md)| Collection MachineRef | Récupérez la liste des appareils associés à l’ID logiciel.
[Liste des vulnérabilités par logiciel](get-vuln-by-software.md) | [Collection de vulnérabilités](vulnerability.md) | Récupérez la liste des vulnérabilités associées à l’ID logiciel.
[Obtenir les ko manquants](get-missing-kbs-software.md) | Collection KB | Obtenir la liste des ko manquants associés à l’ID logiciel

## <a name="properties"></a>Propriétés

Propriété |   Type   |   Description
:---|:---|:---
id | Chaîne | ID logiciel
Nom | Chaîne | Nom du logiciel
Fournisseur | Chaîne | Nom du fournisseur de logiciels
Faiblesses | Entier long | Nombre de vulnérabilités découvertes
publicExploit | Booléen | Une exploitation publique existe pour certaines vulnérabilités
activeAlert | Booléen | L’alerte active est associée à ce logiciel
exposedMachines | Entier long | Nombre d’appareils exposés
impactScore | Double | Impact du score d’exposition de ce logiciel
