---
title: Choisir entre les modes guidés et avancés pour la chasse dans Microsoft 365 Defender
description: La chasse guidée dans Microsoft 365 Defender ne nécessite pas de connaissances KQL, tandis que la chasse avancée vous permet d’écrire une requête à partir de zéro.
keywords: mode guidé, repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto
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
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 45bc2edc940c5681302c1d9266b437b0406913af
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67471813"
---
# <a name="choose-between-guided-and-advanced-modes-to-hunt-in-microsoft-365-defender"></a>Choisissez entre les modes guidés et avancés pour chasser dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Vous pouvez trouver la page de **chasse avancée** en accédant à la barre de navigation gauche dans Microsoft 365 Defender et en sélectionnant **Repérage** > **avancé**. Si la barre de navigation est réduite, sélectionnez l’icône de chasse d’icône ![](../../media/guided-hunting/hunting-icon.png)de chasse. 

Dans la page **de chasse avancée** , deux modes sont pris en charge :
- **Mode guidé** : pour interroger à l’aide du générateur de requêtes
- **Mode avancé** : pour interroger à l’aide de l’éditeur de requête à l’aide de Langage de requête Kusto (KQL)

La principale différence entre les deux modes est que le mode guidé *ne nécessite pas* que le chasseur connaisse KQL pour interroger la base de données, tandis que le mode avancé nécessite des connaissances KQL. 

Le mode guidé dispose d’un générateur de requêtes qui a un style de bloc de construction visuel facile à utiliser qui permet de construire des requêtes par le biais de menus déroulants contenant des filtres et des conditions disponibles. Pour utiliser le mode guidé, consultez [Prise en main du mode de chasse guidé](advanced-hunting-modes.md#get-started-with-guided-hunting-mode).

Le mode avancé dispose d’une zone d’éditeur de requête dans laquelle les utilisateurs peuvent créer des requêtes à partir de zéro. Pour utiliser le mode avancé, consultez [Prise en main du mode de chasse avancé](advanced-hunting-modes.md#get-started-with-advanced-hunting-mode).

## <a name="get-started-with-guided-hunting-mode"></a>Prise en main du mode de chasse guidé

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Lorsque vous ouvrez la page de chasse avancée pour la première fois après la mise à votre disposition de la chasse guidée, vous êtes invité à faire le tour pour en savoir plus sur les différentes parties de la page, telles que les onglets et les zones de requête. 

Pour effectuer la visite guidée, **sélectionnez Prendre une visite guidée** lorsque cette bannière s’affiche :


[![bannière invitant l’utilisateur à faire le tour](../../media/guided-hunting/1-guided-hunting-banner-tb.png) ](../../media/guided-hunting/1-guided-hunting-banner.png#lightbox)

Suivez les bulles d’enseignement bleues qui apparaissent dans la page et sélectionnez **Suivant** pour passer d’une étape à l’autre.

Vous pouvez reprendre la visite à tout moment en accédant aux ressources  > **d’aide****En savoir plus** et en sélectionnant **Prendre la visite guidée**.

![Capture d’écran des ressources d’aide](../../media/guided-hunting/help-resources.png)


Vous pouvez ensuite commencer à créer votre requête pour rechercher des menaces. Les articles suivants peuvent vous aider à tirer le meilleur parti de la chasse en mode guidé :


| Objectif d’apprentissage | Description | Ressource |
|--|--|--|
| **Créer votre première requête** | Découvrez les principes de base du générateur de requêtes, tels que la spécification du domaine de données et l’ajout de conditions et de filtres pour vous aider à créer une requête significative. Pour en savoir plus, exécutez des exemples de requêtes. | [Générer des requêtes de chasse à l’aide du mode guidé](advanced-hunting-query-builder.md) |
| **Découvrir les différentes fonctionnalités du générateur de requêtes** |  Découvrez les différents types de données pris en charge et les fonctionnalités de mode guidé pour vous aider à affiner votre requête en fonction de vos besoins. | [Affiner votre requête en mode guidé](advanced-hunting-query-builder-details.md) |
| **Découvrez ce que vous pouvez faire avec les résultats de la requête** | Familiarisez-vous avec la vue Résultats et ce que vous pouvez faire avec les résultats générés, par exemple comment prendre des mesures à leur sujet ou les lier à un incident. | - [Utiliser les résultats de la requête en mode guidé](advanced-hunting-query-builder-results.md)<br /> - [Agir sur les résultats de la requête](advanced-hunting-take-action.md) <br /> - [Lier les résultats de la requête à un incident](advanced-hunting-link-to-incident.md) |
| **Créer les règles de détection personnalisées** | Découvrez comment utiliser des requêtes de chasse avancées pour déclencher des alertes et effectuer automatiquement des actions de réponse. | - [Vue d’ensemble des détections personnalisées](custom-detections-overview.md) <br />- [Règles de détection personnalisées](custom-detection-rules.md) |

## <a name="get-started-with-advanced-hunting-mode"></a>Prise en main du mode de chasse avancé
Nous vous recommandons de suivre ces étapes pour commencer rapidement avec la chasse avancée : 

| Objectif d’apprentissage | Description | Ressource |
|--|--|--|
| **Apprendre la langue** | La chasse avancée est basée sur le [langage de requête Kusto](/azure/kusto/query/), prenant en charge la même syntaxe et les mêmes opérateurs. Commencez à découvrir le langage de requête en exécutant votre première requête. | [Vue d'ensemble du language de requête](advanced-hunting-query-language.md) |
| **Découvrez comment utiliser les résultats de la requête** | Découvrez les graphiques et les différentes façons d’afficher ou d’exporter vos résultats. Découvrez comment modifier rapidement les requêtes, explorer les détails pour obtenir des informations plus détaillées et prendre des mesures de réponse. | - [Utiliser les résultats de la requête en mode avancé](advanced-hunting-query-results.md)<br /> - [Agir sur les résultats de la requête](advanced-hunting-take-action.md) <br /> - [Lier les résultats de la requête à un incident](advanced-hunting-link-to-incident.md)  |
| **Comprendre le schéma** | Obtenez une compréhension optimale des tableaux du schéma et de leurs colonnes. Découvrez où rechercher des données lors de la construction de vos requêtes. | - [Référence de schéma](advanced-hunting-schema-tables.md) <br />- [Transition à partir de Microsoft Defender pour point de terminaison](advanced-hunting-migrate-from-mde.md) |
| **Obtenir des conseils et des exemples d’experts** | Entraînez-vous gratuitement avec des guides d’experts Microsoft. Explorez les collections de requêtes prédéfinies couvrant différents scénarios de repérage de menaces. | - [Obtenir une formation d’expert](advanced-hunting-expert-training.md) <br />- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md) <br />- [Aller à la chasse](advanced-hunting-go-hunt.md) <br />- [Rechercher les menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md) |
| **Optimiser les requêtes et gérer les erreurs** | Découvrez comment créer des requêtes efficaces et sans erreur. | - [Meilleures pratiques de requête](advanced-hunting-best-practices.md)<br />- [Gérer les erreurs](advanced-hunting-errors.md) |
| **Créer les règles de détection personnalisées** | Découvrez comment utiliser des requêtes de chasse avancées pour déclencher des alertes et effectuer automatiquement des actions de réponse. | - [Vue d’ensemble des détections personnalisées](custom-detections-overview.md) <br />- [Règles de détection personnalisées](custom-detection-rules.md)|

## <a name="see-also"></a>Voir aussi
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Générer des requêtes de chasse à l’aide du mode guidé](advanced-hunting-query-builder.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)