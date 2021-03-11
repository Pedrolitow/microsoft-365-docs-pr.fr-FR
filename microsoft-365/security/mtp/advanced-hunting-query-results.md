---
title: Travailler avec les résultats de requête de recherche avancée dans Microsoft 365 Defender
description: Exploitation des résultats de requête renvoyés par le recherche avancée dans Microsoft 365 Defender
keywords: repérage avancé, repérage de menace, repérage de cybermenace, protection microsoft contre les menaces, microsoft 365, mtp, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto, microsoft 365, Protection Microsoft contre les menaces, visualisation, graphique, filtres, drill-down
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
ms.technology: m365d
ms.openlocfilehash: 3481190a615cfa8914b3623f09d4079468bd431f
ms.sourcegitcommit: 88ab08c0fa1acbc9e066009e131b9f2b0d506c64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2021
ms.locfileid: "50712113"
---
# <a name="work-with-advanced-hunting-query-results"></a>Travailler avec les résultats de requête de recherche avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Bien que vous [](advanced-hunting-overview.md) pouvez construire vos requêtes de recherche avancées pour renvoyer des informations très précises, vous pouvez également travailler avec les résultats de la requête pour obtenir des informations plus précises et examiner des activités et des indicateurs spécifiques. Vous pouvez prendre les mesures suivantes sur les résultats de votre requête :

- Afficher les résultats sous la mesure d’un tableau ou d’un graphique
- Exporter des tableaux et des graphiques
- Accès aux informations détaillées sur l’entité
- Ajustez vos requêtes directement à partir des résultats ou appliquez des filtres

## <a name="view-query-results-as-a-table-or-chart"></a>Afficher les résultats d’une requête sous la mesure d’un tableau ou d’un graphique
Par défaut, le recherche avancée affiche les résultats de la requête sous la mesure de données tabulaires. Vous pouvez également afficher les mêmes données qu’un graphique. Le recherche avancée prend en charge les affichages suivants :

| Type d’affichage | Description |
| -- | -- |
| **Tableau** | Affiche les résultats de la requête au format tabulaire |
| **Graphique en colonnes** | Restituer une série d’éléments uniques sur l’axe des x sous forme de barres verticales dont les hauteurs représentent des valeurs numériques d’un autre champ |
| **Graphique en colonnes empilées** | Restituer une série d’éléments uniques sur l’axe des X sous forme de barres verticales empilées dont les hauteurs représentent des valeurs numériques d’un ou plusieurs autres champs |
| **Graphique en secteurs** | Restituer les secteurs de section représentant des éléments uniques. La taille de chaque secteur représente les valeurs numériques d’un autre champ. |
| **Graphique de donut** | Restituer les arcs sectionnels représentant des éléments uniques. La longueur de chaque arc représente les valeurs numériques d’un autre champ. |
| **Graphique en lignes** | Trace les valeurs numériques d’une série d’éléments uniques et connecte les valeurs tracées |
| **Graphique en nuages de points** | Trace les valeurs numériques d’une série d’éléments uniques |
| **Graphique en zone** | Trace les valeurs numériques d’une série d’éléments uniques et remplit les sections sous les valeurs tracées |

### <a name="construct-queries-for-effective-charts"></a>Créer des requêtes pour des graphiques efficaces
Lors du rendu des graphiques, le recherche avancée identifie automatiquement les colonnes d’intérêt et les valeurs numériques à agréger. Pour obtenir des graphiques significatifs, construisez vos requêtes pour renvoyer les valeurs spécifiques que vous souhaitez visualiser. Voici quelques exemples de requêtes et les graphiques qui en résultent.

#### <a name="alerts-by-severity"></a>Alertes par gravité
Utilisez `summarize` l’opérateur pour obtenir un nombre numérique des valeurs que vous souhaitez graphiquer. La requête ci-dessous utilise `summarize` l’opérateur pour obtenir le nombre d’alertes par gravité.

```kusto
AlertInfo
| summarize Total = count() by Severity
```
Lors de l’affichage des résultats, un graphique en colonnes affiche chaque valeur de gravité en tant que colonne distincte :

![Image des résultats de requête de recherche avancée affichés en tant que résultats d’une requête dans un graphique en colonnes pour les alertes par gravité affichée sous la direction ](../../media/advanced-hunting-column-chart.jpg)
 *d’un graphique en colonnes*

#### <a name="alert-severity-by-operating-system"></a>Gravité des alertes par système d’exploitation
Vous pouvez également utiliser `summarize` l’opérateur pour préparer les résultats pour la graphique des valeurs de plusieurs champs. Par exemple, vous souhaitez peut-être comprendre comment les gravités des alertes sont distribuées entre les systèmes d’exploitation. 

La requête ci-dessous utilise un opérateur pour tirer les informations du système d’exploitation à partir du tableau, puis pour compter les valeurs à la fois dans `join` `DeviceInfo` les `summarize` `OSPlatform` colonnes et dans les `Severity` colonnes :

```kusto
AlertInfo
| join AlertEvidence on AlertId
| join DeviceInfo on DeviceId
| summarize Count = count() by OSPlatform, Severity 
```
Ces résultats sont mieux visualisés à l’aide d’un graphique en colonnes empilées :

![Image des résultats de requête de recherche avancée affichés sous la mesure d’un graphique empilé Résultats de requête pour les alertes par système d’exploitation et gravité affichées sous la mesure ](../../media/advanced-hunting-stacked-chart.jpg)
 *d’un graphique empilé*

#### <a name="phishing-emails-across-top-ten-sender-domains"></a>Courriers électroniques de hameçonnage sur les dix principaux domaines d’expéditeurs
Si vous avez affaire à une liste de valeurs qui n’est pas finie, vous pouvez utiliser l’opérateur pour graphiquer uniquement les valeurs avec le plus grand nombre `Top` d’instances. Par exemple, pour obtenir les dix principaux domaines d’expéditeurs avec le plus de messages de hameçonnage, utilisez la requête ci-dessous :

```kusto
EmailEvents
| where ThreatTypes has "Phish" 
| summarize Count = count() by SenderFromDomain 
| top 10 by Count
```
Utilisez l’affichage graphique en secteurs pour afficher efficacement la distribution dans les principaux domaines :

![Image des résultats de requête de recherche avancée affichés sous la la figure d’un graphique en secteurs affichant la distribution des e-mails de hameçonnage sur les principaux ](../../media/advanced-hunting-pie-chart.jpg)
 *domaines des expéditeurs*

#### <a name="file-activities-over-time"></a>Activités de fichier au fil du temps
À `summarize` l’aide de l’opérateur avec la fonction, vous pouvez vérifier les événements `bin()` impliquant un indicateur particulier au fil du temps. La requête ci-dessous compte les événements impliquant le fichier à intervalles de 30 minutes pour afficher les pics d’activité `invoice.doc` liés à ce fichier :

```kusto
AppFileEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```
Le graphique en lignes ci-dessous met clairement en évidence les périodes avec une activité plus importante impliquant `invoice.doc` : 

![Image des résultats de requête de recherche avancée affichés sous la la mesure d’un graphique en lignes montrant le nombre d’événements impliquant ](../../media/advanced-hunting-line-chart.jpg)
 *un fichier au fil du temps*


## <a name="export-tables-and-charts"></a>Exporter des tableaux et des graphiques
Après avoir exécute une requête, **sélectionnez Exporter** pour enregistrer les résultats dans le fichier local. L’affichage choisi détermine la façon dont les résultats sont exportés :

- **Mode Tableau** : les résultats de la requête sont exportés sous forme tabulaire en tant que workbook Microsoft Excel
- **N’importe** quel graphique : les résultats de la requête sont exportés en tant qu’image JPEG du graphique rendu

## <a name="drill-down-from-query-results"></a>Descendre des résultats de requête
Pour inspecter rapidement un enregistrement dans les résultats de votre requête, sélectionnez la ligne correspondante pour ouvrir le panneau Inspecter **l’enregistrement.** Le panneau fournit les informations suivantes en fonction de l’enregistrement sélectionné :

- Ressources : vue récapitulée des principaux biens (boîtes aux lettres, appareils et **utilisateurs)** trouvés dans l’enregistrement, enrichis d’informations disponibles, telles que les niveaux de risque et d’exposition
- **Arborescence de processus** : générée pour les enregistrements avec des informations de processus et enrichie à l’aide des informations contextuelles disponibles ; en règle générale, les requêtes qui retournent plus de colonnes peuvent entraîner des arbre de processus plus riches.
- **Tous les détails** : toutes les valeurs des colonnes de l’enregistrement  

![Image de l’enregistrement sélectionné avec panneau pour l’inspection de l’enregistrement](../../media/mtp-ah/inspect-record.png)

Pour afficher plus d’informations sur une entité spécifique dans les résultats de votre requête, telles qu’un ordinateur, un fichier, un utilisateur, une adresse IP ou une URL, sélectionnez l’identificateur d’entité pour ouvrir une page de profil détaillée pour cette entité.

## <a name="tweak-your-queries-from-the-results"></a>Adaptez vos requêtes à partir des résultats
Cliquez avec le bouton droit de la souris sur une valeur du jeu de résultats pour améliorer rapidement votre requête. Vous pouvez utiliser les options suivantes pour :

- Rechercher explicitement la valeur sélectionnée (`==`)
- Exclure la valeur sélectionnée de la requête (`!=`)
- Obtenez des opérateurs plus avancés pour ajouter la valeur à votre requête (par exemple, `contains`, `starts with` et `ends with`) 

![Image du jeu de résultats de recherche avancée](../../media/advanced-hunting-results-filter.png)

## <a name="filter-the-query-results"></a>Filtrer les résultats de la requête
Les filtres de droite fournissent un résumé du jeu de résultats. Chaque colonne possède sa propre section qui répertorie les valeurs distinctes trouvées pour cette colonne et le nombre d’instances.

Affinez votre requête en sélectionnant le ou les boutons sur les valeurs que vous souhaitez inclure ou exclure, puis en sélectionnant `+` `-` Exécuter la **requête**.

![Image du filtre de repérage avancé](../../media/advanced-hunting-filter.png)

Une fois le filtre appliqué pour modifier la requête, puis exécuter la requête, les résultats sont mis à jour en conséquence.

## <a name="related-topics"></a>Sujets associés
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)
