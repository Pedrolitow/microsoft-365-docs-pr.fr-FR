---
title: Méthodes et propriétés de l’action d'amélioration
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
ms.openlocfilehash: 65486a046967ef3a3961220af0c9077a7d3fbd94
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58253414"
---
# <a name="recommendation-resource-type"></a>Type de ressource Recommendation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Méthodes
Méthode |Type renvoyé |Description
:---|:---|:---
[Répertorier toutes les actions d’amélioration](get-all-recommendations.md) | Collection Recommendation | Récupère une liste de toutes les recommandations de sécurité affectant l’organisation
[Obtenir les actions d’amélioration par ID](get-recommendation-by-id.md) | Recommandation | Récupère une recommandation de sécurité par son ID
[Obtenir un logiciel de recommandation](list-recommendation-software.md)| [Logiciels](software.md) | Récupère une recommandation de sécurité liée à un logiciel spécifique
[Obtenir des appareils de recommandation](get-recommendation-machines.md)|Collection MachineRef | Récupère la liste des appareils associés à la recommandation de sécurité
[Obtenir des vulnérabilités de recommandation](get-recommendation-vulnerabilities.md) | [Collection de vulnérabilités](vulnerability.md) | Récupère une liste des vulnérabilités associées à la recommandation de sécurité


## <a name="properties"></a>Propriétés
Propriété |   Type   |   Description
:---|:---|:---
id | String | ID de recommandation
productName | String | Nom du logiciel associé  
recommendationName | String
 | Nom de la recommandation
Faiblesses | Entier long | Nombre de vulnérabilités découvertes
Fournisseur | String
 | Nom du fournisseur associé
recommendedVersion | String
 | Version recommandée
recommendationCategory | String
 | Catégorie de recommandation. Les valeurs possibles sont : « Accounts », « Application », « Network », « OS », « SecurityStack »
sous-catégorie | String
 | Sous-catégorie de recommandation
severityScore | Double | Impact potentiel de la configuration sur le Score de sécurité Microsoft pour les appareils de l’organisation (1-10)
publicExploit | Booléen | Une exploitation publique est disponible 
activeAlert | Booléen | L’alerte active est associée à cette recommandation
associatedThreats | String collection | Le rapport d’analyse des menaces est associé à cette recommandation
remediationType | String
 | Type de correction. Les valeurs possibles sont : « ConfigurationChange », « Update », « Upgrade », « Uninstall »
Statut | Énum | État de l’exception de recommandation. Les valeurs possibles sont : « Active » et « Exception »
configScoreImpact | Double | Impact du Score de sécurisation Microsoft pour les appareils
exposureImpacte | Double | Impact du score d’exposition
totalMachineCount | Entier long | Nombre d’appareils installés
exposedMachinesCount | Entier long | Nombre d’appareils installés exposés aux vulnérabilités
nonProductivityImpactedAssets | Entier long | Nombre d’appareils qui ne sont pas affectés  
relatedComponent | String
 |  Composant logiciel associé
