---
title: Méthodes et propriétés de l’action d'amélioration
description: Récupère les principales alertes récentes.
keywords: api, api graphe, api prises en charge, get, alertes, recent
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: ad1864850b8953be424836b270349821d6fe3783
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68632599"
---
# <a name="recommendation-resource-type"></a>Type de ressource de recommandation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Méthodes

<br>

****

|Méthode|Type renvoyé|Description|
|---|---|---|
|[Répertorier toutes les actions d’amélioration](get-all-recommendations.md)|Collection de recommandations|Récupère une liste de toutes les recommandations de sécurité affectant l’organisation|
|[Obtenir des recommandations par ID](get-recommendation-by-id.md)|Recommandation|Récupère une recommandation de sécurité par son ID|
|[Obtenir un logiciel de recommandation](list-recommendation-software.md)|[Logiciels](software.md)|Récupère une recommandation de sécurité liée à un logiciel spécifique|
|[Obtenir des appareils de recommandation](get-recommendation-machines.md)|Collection MachineRef|Récupère une liste d’appareils associés à la recommandation de sécurité|
|[Obtenir les vulnérabilités de recommandation](get-recommendation-vulnerabilities.md)|[Collection de vulnérabilités](vulnerability.md)|Récupère une liste des vulnérabilités associées à la recommandation de sécurité|
|

## <a name="properties"></a>Propriétés

<br>

****

|Propriété|Type|Description|
|---|---|---|
|id|Chaîne|ID de recommandation|
|productName|Chaîne|Nom du logiciel associé|
|recommendationName|Chaîne|Nom de la recommandation|
|Faiblesses|Entier long|Nombre de vulnérabilités découvertes|
|Fournisseur|Chaîne|Nom du fournisseur associé|
|recommendedVersion|Chaîne|Version recommandée|
|recommendedProgram|Chaîne|Programme recommandé|
|recommendedVendor|Chaîne|Fournisseur recommandé|
|recommendationCategory|Chaîne|Catégorie de recommandation. Les valeurs possibles sont : « Accounts », « Application », « Network », « OS », « SecurityControls »|
|Sous-catégorie|Chaîne|Sous-catégorie de recommandation|
|severityScore|Double|Impact potentiel de la configuration sur le degré de sécurisation Microsoft de l’organisation pour les appareils (1-10)|
|publicExploit|Boolean|Exploit public disponible|
|activeAlert|Boolean|L’alerte active est associée à cette recommandation|
|associatedThreats|String collection|Le rapport Analyse des menaces est associé à cette recommandation|
|remediationType|Chaîne|Type de correction. Les valeurs possibles sont : « ConfigurationChange », « Update », « Upgrade », « Uninstall »|
|État|Énum|État de l’exception de recommandation. Les valeurs possibles sont : « Active » et « Exception »|
|configScoreImpact|Double|Impact du score de sécurité Microsoft pour les appareils|
|exposureImpact|Double|Impact du score d’exposition|
|totalMachineCount|Entier long|Nombre d’appareils installés|
|exposedMachinesCount|Entier long|Nombre d’appareils installés exposés à des vulnérabilités|
|nonProductivityImpactedAssets|Entier long|Nombre d’appareils qui ne sont pas affectés|
|relatedComponent|Chaîne|Composant logiciel associé|
|
