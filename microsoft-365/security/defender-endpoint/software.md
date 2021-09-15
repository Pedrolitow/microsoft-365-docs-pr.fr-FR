---
title: Méthodes et propriétés du logiciel
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 85b162cce8655c7942a341326ff08ec112ace100
ms.sourcegitcommit: f88a0ec621e7d9bc5f376eeaf70c8a9800711f88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59356560"
---
# <a name="software-resource-type"></a>Type de ressource logicielle

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Méthodes

<br>

****

|Méthode|Type renvoyé|Description|
|---|---|---|
|[Répertorier les logiciels](get-software.md)|Collection de logiciels|Liste de l’inventaire logiciel de l’organisation.|
|[Obtenir un logiciel par ID](get-software-by-id.md)|Logiciels|Obtenez un logiciel spécifique par son ID logiciel.|
|[Répertorier la distribution de versions du logiciel](get-software-ver-distribution.md)|Collection de distribution|Liste de la distribution des versions des logiciels par ID logiciel.|
|[Répertorier les ordinateurs par logiciel](get-machines-by-software.md)|Collection MachineRef|Récupérez la liste des appareils associés à l’ID logiciel.|
|[Répertorier les vulnérabilités par logiciel](get-vuln-by-software.md)|[Collection de vulnérabilités](vulnerability.md)|Récupérez la liste des vulnérabilités associées à l’ID logiciel.|
|[Obtenir des Ko manquants](get-missing-kbs-software.md)|Collection KB|Obtenir la liste des ko manquants associés à l’ID logiciel|
|

## <a name="properties"></a>Propriétés

<br>

****

|Propriété|Type|Description|
|---|---|---|
|id|Chaîne|ID logiciel|
|Nom|String|Nom du logiciel|
|Fournisseur|Chaîne|Nom du fournisseur de logiciels|
|Faiblesses|Entier long|Nombre de vulnérabilités découvertes|
|publicExploit|Boolean|Une exploitation publique existe pour certaines vulnérabilités|
|activeAlert|Boolean|L’alerte active est associée à ce logiciel|
|exposedMachines|Entier long|Nombre d’appareils exposés|
|impactScore|Double|Impact du score d’exposition de ce logiciel|
|
