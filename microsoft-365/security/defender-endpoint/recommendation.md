---
title: Méthodes et propriétés de recommandation
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
ms.openlocfilehash: 6ab4d4e1acab0e4b837195f64c369057d7ceb417
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51198232"
---
# <a name="recommendation-resource-type"></a>Type de ressource Recommendation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Méthodes
Méthode |Type renvoyé |Description
:---|:---|:---
[Liste de toutes les recommandations](get-all-recommendations.md) | Collection Recommendation | Récupère une liste de toutes les recommandations de sécurité affectant l’organisation
[Obtenir une recommandation par ID](get-recommendation-by-id.md) | Recommandation | Récupère une recommandation de sécurité par son ID
[Obtenir un logiciel de recommandation](get-recommendation-software.md)| [Logiciels](software.md) | Récupère une recommandation de sécurité liée à un logiciel spécifique
[Obtenir des appareils de recommandation](get-recommendation-machines.md)|Collection MachineRef | Récupère la liste des appareils associés à la recommandation de sécurité
[Obtenir des vulnérabilités de recommandation](get-recommendation-vulnerabilities.md) | [Collection de vulnérabilités](vulnerability.md) | Récupère une liste des vulnérabilités associées à la recommandation de sécurité


## <a name="properties"></a>Propriétés
Propriété |   Type   |   Description
:---|:---|:---
id | Chaîne | ID de recommandation
productName | String | Nom du logiciel associé  
recommendationName | Chaîne | Nom de la recommandation
Faiblesses | Entier long | Nombre de vulnérabilités découvertes
Fournisseur | Chaîne | Nom du fournisseur associé
recommendedVersion | Chaîne | Version recommandée
recommendationCategory | Chaîne | Catégorie de recommandation. Les valeurs possibles sont : « Accounts », « Application », « Network », « OS », « SecurityStack »
sous-catégorie | Chaîne | Sous-catégorie de recommandation
severityScore | Double | Impact potentiel de la configuration sur le Score de sécurité Microsoft pour les appareils de l’organisation (1-10)
publicExploit | Boolean | Une exploitation publique est disponible 
activeAlert | Boolean | L’alerte active est associée à cette recommandation
associatedThreats | Collection de chaînes | Le rapport d’analyse des menaces est associé à cette recommandation
remediationType | Chaîne | Type de correction. Les valeurs possibles sont : « ConfigurationChange », « Update », « Upgrade », « Uninstall »
Statut | Énum | État de l’exception de recommandation. Les valeurs possibles sont : « Active » et « Exception »
configScoreImpact | Double | Impact du Score de sécurisation Microsoft pour les appareils
exposureImpacte | Double | Impact du score d’exposition
totalMachineCount | Entier long | Nombre d’appareils installés
exposedMachinesCount | Entier long | Nombre d’appareils installés exposés à des vulnérabilités
nonProductivityImpactedAssets | Entier long | Nombre d’appareils qui ne sont pas affectés  
relatedComponent | Chaîne |  Composant logiciel associé
