---
title: Utiliser les résultats de la requête en mode guidé pour la chasse dans Microsoft 365 Defender
description: Utiliser et personnaliser les résultats des requêtes en mode guidé pour la chasse avancée dans Microsoft 365 Defender
keywords: mode guidé, repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.openlocfilehash: 7b14628c50e16c976471f3daf8764166f6cdd0a2
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67476081"
---
# <a name="work-with-query-results-in-guided-mode"></a>Utiliser les résultats de la requête en mode guidé
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Dans la chasse en mode guidé, les résultats de la requête apparaissent dans l’onglet **Résultats** . 

[![Capture d’écran de l’onglet](../../media/guided-hunting/results-view.png) Résultats ](../../media/guided-hunting/results-view.png#lightbox)

Vous pouvez travailler davantage sur les résultats en les exportant vers un fichier CSV en sélectionnant **Exporter**. Cela télécharge le fichier CSV pour votre utilisation.

Vous pouvez afficher d’autres informations dans la vue Résultats :
- Nombre d’enregistrements dans la liste des résultats (à côté du bouton Rechercher)
- Durée de l’exécution de la requête
- Utilisation des ressources de la requête

## <a name="view-more-columns"></a>Afficher d’autres colonnes

Quelques colonnes standard sont incluses dans les résultats pour faciliter l’affichage. 

Pour afficher d’autres colonnes :
1. Sélectionnez **Personnaliser les colonnes** dans la partie supérieure droite de l’affichage des résultats.
 

2. À partir de là, sélectionnez les colonnes à inclure dans l’affichage des résultats et désélectionnez les colonnes à masquer. 


[![Capture d’écran de la liste des colonnes que vous pouvez ajouter à la vue](../../media/guided-hunting/results-view-customize-columns.png) des résultats ](../../media/guided-hunting/results-view-customize-columns-tb.png#lightbox)

3. Sélectionnez **Appliquer** pour afficher les résultats avec les colonnes ajoutées. Utilisez les barres de défilement si nécessaire.


## <a name="see-also"></a>Voir aussi
- [Quotas de chasse avancés et paramètres d’utilisation](advanced-hunting-limits.md)
- [Passer en mode avancé](advanced-hunting-query-builder-details.md#switch-to-advanced-mode-after-building-a-query)
- [Affiner votre requête en mode guidé](advanced-hunting-query-builder-details.md)