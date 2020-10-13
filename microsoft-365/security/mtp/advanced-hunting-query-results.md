---
title: Utiliser les résultats de la recherche avancée dans Microsoft Threat Protection
description: Tirer le meilleur parti des résultats de la requête renvoyés par la recherche avancée dans Microsoft Threat Protection
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, détections personnalisées, schéma, Kusto, Microsoft 365, protection contre les menaces Microsoft, visualisation, graphique, filtres, exploration
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.openlocfilehash: e19859189b57bbc9a6a4bbfb87fb224b2735331b
ms.sourcegitcommit: de600339b08951d6dd3933288a8da2327a4b6ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48431074"
---
# <a name="work-with-advanced-hunting-query-results"></a>Utiliser les résultats de la recherche avancée de la chasse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Bien que vous puissiez construire vos requêtes de [chasse avancées](advanced-hunting-overview.md) pour renvoyer des informations très précises, vous pouvez également utiliser les résultats de la requête pour mieux comprendre et examiner des activités et des indicateurs spécifiques. Vous pouvez effectuer les actions suivantes sur les résultats de votre requête :

- Afficher les résultats sous la forme d’un tableau ou d’un graphique
- Exporter des tableaux et des graphiques
- Explorer les informations détaillées de l’entité
- Affiner vos requêtes directement à partir des résultats ou appliquer des filtres

## <a name="view-query-results-as-a-table-or-chart"></a>Afficher les résultats de la requête sous la forme d’un tableau ou d’un graphique
Par défaut, la chasse avancée affiche les résultats de la requête sous forme de données tabulaires. Vous pouvez également afficher les mêmes données sous la forme d’un graphique. La chasse avancée prend en charge les affichages suivants :

| Type d’affichage | Description |
| -- | -- |
| **Table** | Affiche les résultats de la requête sous forme de tableau |
| **Histogramme** | Affiche une série d’éléments uniques sur l’axe des x sous forme de barres verticales dont les hauteurs représentent les valeurs numériques d’un autre champ |
| **Histogramme empilé** | Affiche une série d’éléments uniques sur l’axe des x sous forme de barres verticales empilées dont les hauteurs représentent les valeurs numériques d’un ou plusieurs autres champs |
| **Graphique en secteurs** | Affiche les secteurs de section représentant des éléments uniques. La taille de chaque graphique représente les valeurs numériques d’un autre champ. |
| **Graphique en bouée** | Affiche les arcs de section représentant des éléments uniques. La longueur de chaque arc représente les valeurs numériques d’un autre champ. |
| **Graphique en courbes** | Trace les valeurs numériques d’une série d’éléments uniques et connecte les valeurs tracées |
| **Nuages de points** | Trace les valeurs numériques d’une série d’éléments uniques |
| **Graphique en aires** | Trace les valeurs numériques d’une série d’éléments uniques et remplit les sections sous les valeurs tracées. |

### <a name="construct-queries-for-effective-charts"></a>Créer des requêtes pour des graphiques efficaces
Lors du rendu des graphiques, la chasse avancée identifie automatiquement les colonnes d’intérêt et les valeurs numériques à agréger. Pour obtenir des graphiques significatifs, construisez vos requêtes pour renvoyer les valeurs spécifiques que vous souhaitez voir visibles. Voici quelques exemples de requêtes et les graphiques qui en résultent.

#### <a name="alerts-by-severity"></a>Alertes par gravité
Utilisez l' `summarize` opérateur pour obtenir le nombre de chiffres des valeurs que vous souhaitez graphiquer. La requête ci-dessous utilise l' `summarize` opérateur pour obtenir le nombre d’alertes par gravité.

```kusto
AlertInfo
| summarize Total = count() by Severity
```
Lors du rendu des résultats, un histogramme affiche chaque valeur de gravité sous la forme d’une colonne distincte :

![Image des résultats de la recherche avancée de la chasse affichés sous la forme d’un graphique en histogramme ](../../media/advanced-hunting-column-chart.jpg)
 *résultats de la requête pour les alertes par gravité affichée sous forme de graphique en histogrammes*

#### <a name="alert-severity-by-operating-system"></a>Gravité des alertes par système d’exploitation
Vous pouvez également utiliser l' `summarize` opérateur pour préparer les résultats pour les valeurs de graphique de plusieurs champs. Par exemple, vous souhaiterez peut-être comprendre comment les niveaux d’alerte sont distribués entre les systèmes d’exploitation (OS). 

La requête ci-dessous utilise un `join` opérateur pour extraire les informations du système d’exploitation à partir de la `DeviceInfo` table, puis utilise `summarize` pour compter les valeurs dans les `OSPlatform` `Severity` colonnes et :

```kusto
AlertInfo
| join AlertEvidence on AlertId
| join DeviceInfo on DeviceId
| summarize Count = count() by OSPlatform, Severity 
```
Ces résultats sont optimisés à l’aide d’un histogramme empilé :

![Image des résultats de la recherche avancée de la chasse affichés sous la forme d’un graphique empilé ](../../media/advanced-hunting-stacked-chart.jpg)
 *de résultats de requête pour les alertes par système d’exploitation et gravité affichées sous la forme d’un graphique empilé*

#### <a name="phishing-emails-across-top-ten-sender-domains"></a>Courriers électroniques de hameçonnage sur les dix principaux domaines d’expéditeur
Si vous avez affaire à une liste de valeurs qui n’est pas finie, vous pouvez utiliser l' `Top` opérateur pour graphiquer uniquement les valeurs avec le plus d’instances. Par exemple, pour obtenir les dix principaux domaines d’expéditeur avec le plus de courriers électroniques de hameçonnage, utilisez la requête ci-dessous :

```kusto
EmailEvents
| where PhishFilterVerdict == "Phish"
| summarize Count = count() by SenderFromDomain
| top 10 by Count
```
Utilisez la vue de graphique à secteurs pour afficher efficacement la distribution dans les domaines principaux :

![Image des résultats de la recherche avancée de la chasse affichée sous la forme d’un graphique en secteurs ](../../media/advanced-hunting-pie-chart.jpg)
 *illustrant la répartition des courriers électroniques de hameçonnage sur les domaines d’expéditeurs les plus fréquents*

#### <a name="file-activities-over-time"></a>Activités des fichiers dans le temps
À l’aide de l' `summarize` opérateur avec la `bin()` fonction, vous pouvez rechercher des événements impliquant un indicateur particulier dans le temps. La requête ci-dessous compte les événements impliquant le fichier `invoice.doc` à des intervalles de 30 minutes pour afficher les pics d’activité liés à ce fichier :

```kusto
AppFileEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```
Le graphique en courbes ci-dessous met clairement en évidence les périodes d’activité impliquant `invoice.doc` : 

![Image des résultats de la recherche avancée de la chasse affichée sous la forme d’un graphique en courbes ](../../media/advanced-hunting-line-chart.jpg)
 *illustrant le nombre d’événements impliquant un fichier dans le temps*


## <a name="export-tables-and-charts"></a>Exporter des tableaux et des graphiques
Après avoir exécuté une requête, sélectionnez **Exporter** pour enregistrer les résultats dans un fichier local. L’affichage choisi détermine la façon dont les résultats sont exportés :

- **Affichage tableau** : les résultats de la requête sont exportés sous forme de tableau sous forme de classeur Microsoft Excel
- **N’importe quel graphique** : les résultats de la requête sont exportés sous la forme d’une image JPEG du graphique affiché

## <a name="drill-down-from-query-results"></a>Explorer les résultats de la requête
Pour inspecter rapidement un enregistrement dans les résultats de votre requête, sélectionnez la ligne correspondante pour ouvrir le panneau **inspecter les enregistrements** . Le panneau fournit les informations suivantes en fonction de l’enregistrement sélectionné :

- **Ressources** : vue résumée des ressources principales (boîtes aux lettres, appareils et utilisateurs) figurant dans l’enregistrement, enrichie d’informations disponibles, telles que les niveaux de risque et d’exposition.
- **Arborescence de processus** : générée pour des enregistrements avec des informations de processus et enrichie à l’aide des informations contextuelles disponibles ; en règle générale, les requêtes qui renvoient plus de colonnes peuvent entraîner des arborescences de processus plus riches.
- **Tous les détails** : toutes les valeurs des colonnes de l’enregistrement  

![Image de l’enregistrement sélectionné avec le panneau pour inspecter l’enregistrement](../../media/mtp-ah/inspect-record.png)

Pour afficher plus d’informations sur une entité spécifique dans vos résultats de requête, comme une machine, un fichier, un utilisateur, une adresse IP ou une URL, sélectionnez l’identificateur d’entité pour ouvrir une page de profil détaillée pour cette entité.

## <a name="tweak-your-queries-from-the-results"></a>Adaptez vos requêtes à partir des résultats
Cliquez avec le bouton droit de la souris sur une valeur du jeu de résultats pour améliorer rapidement votre requête. Vous pouvez utiliser les options suivantes pour :

- Rechercher explicitement la valeur sélectionnée (`==`)
- Exclure la valeur sélectionnée de la requête (`!=`)
- Obtenez des opérateurs plus avancés pour ajouter la valeur à votre requête (par exemple, `contains`, `starts with` et `ends with`) 

![Image du jeu de résultats de la chasse avancée](../../media/advanced-hunting-results-filter.png)

## <a name="filter-the-query-results"></a>Filtrer les résultats de la requête
Les filtres de droite fournissent un résumé du jeu de résultats. Chaque colonne possède sa propre section qui répertorie les valeurs distinctes trouvées pour cette colonne et le nombre d’instances.

Affinez votre requête en sélectionnant `+` les `-` boutons ou sur les valeurs que vous souhaitez inclure ou exclure, puis en sélectionnant **exécuter la requête**.

![Image du filtre de repérage avancé](../../media/advanced-hunting-filter.png)

Une fois le filtre appliqué pour modifier la requête, puis exécuter la requête, les résultats sont mis à jour en conséquence.

## <a name="related-topics"></a>Sujets associés
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les emails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)
