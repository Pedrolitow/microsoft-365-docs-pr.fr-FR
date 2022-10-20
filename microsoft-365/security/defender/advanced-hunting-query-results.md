---
title: Utiliser des résultats de requête de chasse avancés dans Microsoft 365 Defender
description: Tirer le meilleur parti des résultats de requête retournés par la chasse avancée dans Microsoft 365 Defender
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto, visualisation, graphique, filtres, exploration
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
- m365-security
- tier1
ms.topic: conceptual
ms.openlocfilehash: 235baf126763989ca7168d72552029f4dc04216d
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68631103"
---
# <a name="work-with-advanced-hunting-query-results"></a>Utiliser des résultats de requête de chasse avancés

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Bien que vous puissiez construire vos requêtes de [chasse avancées](advanced-hunting-overview.md) pour retourner des informations précises, vous pouvez également utiliser les résultats de la requête pour obtenir des informations supplémentaires et examiner des activités et des indicateurs spécifiques. Vous pouvez effectuer les actions suivantes sur les résultats de votre requête :

- Afficher les résultats sous forme de tableau ou de graphique
- Exporter des tables et des graphiques
- Explorer les informations détaillées sur l’entité
- Ajuster vos requêtes directement à partir des résultats

## <a name="view-query-results-as-a-table-or-chart"></a>Afficher les résultats d’une requête sous forme de tableau ou de graphique

Par défaut, la chasse avancée affiche les résultats de la requête sous forme de données tabulaires. Vous pouvez également afficher les mêmes données qu’un graphique. La chasse avancée prend en charge les vues suivantes :

| Type d’affichage | Description |
|--|--|
| **Tableau** | Affiche les résultats de la requête au format tabulaire |
| **Histogramme** | Affiche une série d’éléments uniques sur l’axe des x sous forme de barres verticales dont les hauteurs représentent des valeurs numériques d’un autre champ |
| **Graphique** | Affiche des secteurs sectionnels représentant des éléments uniques. La taille de chaque secteur représente les valeurs numériques d’un autre champ. |
| **Graphique en courbes** | Trace des valeurs numériques pour une série d’éléments uniques et connecte les valeurs tracées |
| **Nuage de points** | Trace des valeurs numériques pour une série d’éléments uniques |
| **Graphique en aires** | Trace des valeurs numériques pour une série d’éléments uniques et remplit les sections sous les valeurs tracées |
| **Graphique en aires empilées** | Trace des valeurs numériques pour une série d’éléments uniques et empile les sections remplies sous les valeurs tracées  |
| **Graphique chronologique** | Trace les valeurs par nombre sur une échelle de temps linéaire |

### <a name="construct-queries-for-effective-charts"></a>Construire des requêtes pour des graphiques effectifs

Lors du rendu des graphiques, la recherche avancée identifie automatiquement les colonnes d’intérêt et les valeurs numériques à agréger. Pour obtenir des graphiques significatifs, construisez vos requêtes pour retourner les valeurs spécifiques que vous souhaitez visualiser. Voici quelques exemples de requêtes et les graphiques résultants.

#### <a name="alerts-by-severity"></a>Alertes par gravité

Utilisez l’opérateur `summarize` pour obtenir un nombre numérique des valeurs que vous souhaitez histifier. La requête ci-dessous utilise l’opérateur `summarize` pour obtenir le nombre d’alertes par gravité.

```kusto
AlertInfo
| summarize Total = count() by Severity
```

Lors du rendu des résultats, un histogramme affiche chaque valeur de gravité sous la forme d’une colonne distincte :

:::image type="content" source="../../media/advanced-hunting-column-chart-new.png" alt-text="Exemple d’un graphique qui affiche les résultats de repérage avancés dans le portail Microsoft 365 Defender" lightbox="../../media/advanced-hunting-column-chart-new.png":::
*Résultats de la requête pour les alertes par gravité affichées sous la forme d’un histogramme*

#### <a name="phishing-emails-across-top-ten-sender-domains"></a>E-mails d’hameçonnage dans les dix principaux domaines d’expéditeur

Si vous traitez d’une liste de valeurs qui n’est pas finie, vous pouvez utiliser l’opérateur `Top` pour représenter uniquement les valeurs avec le plus d’instances. Par exemple, pour obtenir les 10 principaux domaines d’expéditeur avec le plus d’e-mails de hameçonnage, utilisez la requête ci-dessous :

```kusto
EmailEvents
| where ThreatTypes has "Phish"
| summarize Count = count() by SenderFromDomain
| top 10 by Count
```

Utilisez la vue graphique en secteurs pour afficher efficacement la distribution entre les domaines principaux :

:::image type="content" source="../../media/advanced-hunting-pie-chart-new.png" alt-text="Graphique en secteurs qui affiche les résultats de repérage avancés dans le portail Microsoft 365 Defender" lightbox="../../media/advanced-hunting-pie-chart-new.png":::
*Graphique en secteurs qui montre la distribution des e-mails de hameçonnage entre les domaines d’expéditeur principaux*

#### <a name="file-activities-over-time"></a>Activités de fichiers au fil du temps
À l’aide de l’opérateur `summarize` avec la `bin()` fonction, vous pouvez rechercher les événements impliquant un indicateur particulier au fil du temps. La requête ci-dessous compte les événements impliquant le fichier `invoice.doc` à intervalles de 30 minutes pour afficher les pics d’activité liés à ce fichier :

```kusto
CloudAppEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```

Le graphique en courbes ci-dessous met clairement en évidence les périodes avec plus d’activité impliquant `invoice.doc`:

:::image type="content" source="../../media/line-chart-a.png" alt-text="Graphique en courbes qui affiche les résultats de repérage avancés dans le portail Microsoft 365 Defender" lightbox="../../media/line-chart-a.png":::
*Graphique en courbes montrant le nombre d’événements impliquant un fichier au fil du temps*

## <a name="export-tables-and-charts"></a>Exporter des tables et des graphiques

Après avoir exécuté une requête, sélectionnez **Exporter** pour enregistrer les résultats dans un fichier local. La vue choisie détermine la façon dont les résultats sont exportés :

- **Vue Table** : les résultats de la requête sont exportés sous forme tabulaire sous la forme d’un classeur Microsoft Excel
- **N’importe quel graphique** : les résultats de la requête sont exportés sous forme d’image JPEG du graphique rendu

## <a name="drill-down-from-query-results"></a>Explorer les résultats de la requête

Pour inspecter rapidement un enregistrement dans les résultats de votre requête, sélectionnez la ligne correspondante pour ouvrir le panneau **Inspecter l’enregistrement** . Le panneau fournit les informations suivantes en fonction de l’enregistrement sélectionné :

- **Ressources** : vue résumée des principales ressources (boîtes aux lettres, appareils et utilisateurs) figurant dans l’enregistrement, enrichie d’informations disponibles, telles que les niveaux de risque et d’exposition
- **Tous les détails** : toutes les valeurs des colonnes de l’enregistrement

:::image type="content" source="../../media/results-inspect-record.png" alt-text="Enregistrement sélectionné avec panneau permettant d’inspecter l’enregistrement dans le portail Microsoft 365 Defender" lightbox="../../media/results-inspect-record.png":::

Pour afficher plus d’informations sur une entité spécifique dans les résultats de votre requête, telles qu’une machine, un fichier, un utilisateur, une adresse IP ou une URL, sélectionnez l’identificateur d’entité pour ouvrir une page de profil détaillée pour cette entité.

## <a name="tweak-your-queries-from-the-results"></a>Adaptez vos requêtes à partir des résultats

Sélectionnez les trois points à droite d’une colonne dans le panneau **d’enregistrement Inspecter** . Vous pouvez utiliser les options suivantes pour :

- Rechercher explicitement la valeur sélectionnée (`==`)
- Exclure la valeur sélectionnée de la requête (`!=`)
- Obtenez des opérateurs plus avancés pour ajouter la valeur à votre requête, par `contains`exemple , `starts with`et `ends with`

:::image type="content" source="../../media/work-with-query-tweak-query.png" alt-text="Volet Type d’action sur la page Inspecter l’enregistrement dans le portail Microsoft 365 Defender" lightbox="../../media/work-with-query-tweak-query.png":::

> [!NOTE]
> Certaines tables de cet article peuvent ne pas être disponibles à Microsoft Defender pour point de terminaison. [Activez Microsoft 365 Defender](m365d-enable.md) pour rechercher des menaces à l’aide de sources de données supplémentaires. Vous pouvez déplacer vos flux de travail de chasse avancés de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender en suivant les étapes de migration [des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)
