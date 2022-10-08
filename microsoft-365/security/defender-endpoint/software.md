---
title: Méthodes et propriétés du logiciel
description: Récupère les alertes les plus récentes.
keywords: api, api graphe, api prises en charge, get, alertes, recent
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 7cb78b75563d45f1a61a45f03a68c947478a19c0
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68221783"
---
# <a name="software-resource-type"></a>Type de ressource logicielle

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Méthodes

<br>

****

|Méthode|Type renvoyé|Description|
|---|---|---|
|[Répertorier les logiciels](get-software.md)|Collection de logiciels|Répertorier l’inventaire logiciel de l’organisation|
|[Obtenir un logiciel par ID](get-software-by-id.md)|Logiciels|Obtenir un logiciel spécifique par son ID de logiciel|
|[Répertorier la distribution de versions du logiciel](get-software-ver-distribution.md)|Collection de distribution|Répertorier la distribution des versions logicielles par ID logiciel|
|[Répertorier les ordinateurs par logiciel](get-machines-by-software.md)|Collection MachineRef|Récupérer la liste des appareils associés à l’ID logiciel|
|[Répertorier les vulnérabilités par logiciel](get-vuln-by-software.md)|[Collection de vulnérabilités](vulnerability.md)|Récupérer une liste des vulnérabilités associées à l’ID logiciel|
|[Obtenir des Ko manquants](get-missing-kbs-software.md)|Collection de bases de connaissances|Obtenir la liste des bases de connaissances manquantes associées à l’ID logiciel|
|

## <a name="properties"></a>Propriétés

<br>

****

|Propriété|Type|Description|
|---|---|---|
|id|Chaîne|ID logiciel|
|Nom|Chaîne|Nom du logiciel|
|Fournisseur|Chaîne|Nom de l’éditeur de logiciels|
|Faiblesses|Entier long|Nombre de vulnérabilités découvertes|
|publicExploit|Boolean|L’exploitation publique existe pour certaines des vulnérabilités|
|activeAlert|Boolean|L’alerte active est associée à ce logiciel|
|exposedMachines|Entier long|Nombre d’appareils exposés|
|impactScore|Double|Impact du score d’exposition de ce logiciel|
|
