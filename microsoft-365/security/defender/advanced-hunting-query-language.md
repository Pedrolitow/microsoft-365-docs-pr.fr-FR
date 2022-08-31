---
title: Découvrez le langage de requête de chasse avancé dans Microsoft 365 Defender
description: Créez votre première requête de repérage de menace et découvrez les opérateurs communs et les autres aspects du langage de requête de repérage avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, langue, apprentissage, première requête, télémétrie, événements, télémétrie, détections personnalisées, schéma, kusto, opérateurs, types de données, téléchargement powershell, exemple de requête
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
ms.topic: article
ms.openlocfilehash: ee267084501fad28a0bff592f5c06d130f73a424
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67480797"
---
# <a name="learn-the-advanced-hunting-query-language"></a>Découvrir le langage de requête de repérage avancé

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**

- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

Le repérage avancé est basé sur le [langage de requête Kusto](/azure/kusto/query/). Vous pouvez utiliser des opérateurs et des instructions Kusto pour construire des requêtes qui recherchent des informations dans un [schéma](advanced-hunting-schema-tables.md) spécialisé. 

Regardez cette courte vidéo pour découvrir les principes de base du langage de requête Kusto.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfJ]
 
Pour mieux comprendre ces concepts, exécutez votre première requête.

## <a name="try-your-first-query"></a>Essayez votre première requête

Dans le portail Microsoft 365 Defender, accédez à **Hunting** pour exécuter votre première requête. Consultez l’exemple qui suit : 

```kusto
// Finds PowerShell execution events that could involve a download
union DeviceProcessEvents, DeviceNetworkEvents
| where Timestamp > ago(7d)
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
 "DownloadFile",
 "DownloadData",
 "DownloadString",
"WebRequest",
"Shellcode",
"http",
"https")
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

**[Exécuter cette requête dans la chasse avancée](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2TW0sCURSF93PQfxh8Moisp956yYIgQtLoMaYczJpbzkkTpN_et_dcdPQkcpjbmrXXWftyetKTQG5lKqmMpeB9IJksJJKZDOWdZ8wKeP5wvcm3OLgZbMXmXCmIxjnYIfcAVgYvRi8w3TnfsXEDGAG47pCCZXyP5ViO4KeNbt-Up-hEuJmB6lvButnY8XSL-cDl0M2I-GwxVX8Fe2H5zMzHiKjEVB0eEsnBrszfBIWuXOLrxCJ7VqEBfM3DWUYTkNKrv1p5y3X0jwetemzOQ_NSVuuXZ1c6aNTKRaN8VvWhY9n7OS-o6J5r7mYeQypdEKc1m1qfiqpjCSuspsDntt2J61bEvTlXls5AgQfFl5bHM_gr_BhO2RF1rztoBv2tWahrso_TtzkL93KGMGZVr2pe7eWR-xeZl91f_113UOsx3nDR4Y9j5R6kaCq8ajr_YWfFeedsd27L7it-Z6dAZyxsJq1d9-2ZOSzK3y2NVd8-zUPjtZaJnYsIH4Md7AmdeAcd2Cl1XoURc5PzXlfU8U9P54WcswL6t_TW9Q__qX-xygQAAA&runQuery=true&timeRangeId=week)**

### <a name="describe-the-query-and-specify-the-tables-to-search"></a>Décrire la requête et spécifier les tables à rechercher

Un bref commentaire a été ajouté au début de la requête pour décrire à quoi il sert. Ce commentaire permet de choisir ultérieurement d’enregistrer la requête et de la partager avec d’autres dans votre organisation. 

```kusto
// Finds PowerShell execution events that could involve a download
```

La requête elle-même commence généralement par un nom de table suivi de plusieurs éléments qui commencent par un canal (`|`). Dans cet exemple, nous commençons par créer une union de deux tables et`DeviceNetworkEvents`, si nécessaire, `DeviceProcessEvents` nous ajoutons des éléments rediriagés.

```kusto
union DeviceProcessEvents, DeviceNetworkEvents
```

### <a name="set-the-time-range"></a>Définir l’intervalle de temps

Le premier élément rediriagé est un filtre de temps limité aux sept jours précédents. La limitation d’un intervalle de temps permet de s’assurer que les requêtes fonctionnent bien, renvoient des résultats gérables et n’expirent pas.

```kusto
| where Timestamp > ago(7d)
```

### <a name="check-specific-processes"></a>Vérifier des processus spécifiques

L’intervalle de temps est immédiatement suivi d’une recherche de noms de fichiers de processus représentant l’application PowerShell.

```kusto
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### <a name="search-for-specific-command-strings"></a>Rechercher des chaînes de commandes spécifiques

Ensuite, la requête recherche les chaînes dans les lignes de commande qui sont généralement utilisées pour télécharger des fichiers à l’aide de PowerShell.

```kusto
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
    "DownloadFile",
    "DownloadData",
    "DownloadString",
    "WebRequest",
    "Shellcode",
    "http",
    "https")
```

### <a name="customize-result-columns-and-length"></a>Personnaliser les colonnes et la longueur des résultats 

Maintenant que votre requête identifie clairement les données que vous recherchez, vous pouvez définir l’apparence des résultats. `project` retourne des colonnes spécifiques et `top` limite le nombre de résultats. Ces opérateurs permettent de s’assurer que les résultats sont bien mis en forme et relativement volumineux et faciles à traiter.

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

Sélectionnez **Exécuter la requête** pour afficher les résultats.

>[!TIP]
>Vous pouvez afficher les résultats des requêtes sous forme de graphiques et ajuster rapidement les filtres. Pour obtenir des conseils, [consultez l’utilisation des résultats de la requête](advanced-hunting-query-results.md)



## <a name="learn-common-query-operators"></a>Découvrir les opérateurs de requête courants

Vous venez d’exécuter votre première requête et vous avez une idée générale de ses composants. Il est temps de revenir en arrière et d’apprendre quelques notions de base. Le langage de requête Kusto utilisé par le repérage avancé prend en charge divers opérateurs, notamment les opérateurs communs suivants.

| Opérateur | Description et utilisation |
|--|--|
| `where` | Filtre une table sur le sous-ensemble de lignes qui répondent à un prédicat. |
| `summarize` | Produit une table qui agrège le contenu de la table d’entrée. |
| `join` | Fusionne les lignes de deux tables pour former une nouvelle table en faisant correspondre les valeurs des colonnes spécifiées de chaque table. Regardez [Joindre des tables dans KQL](https://www.youtube.com/watch?v=8qZx7Pp5XgM) pour savoir comment faire.|
| `count` | Renvoie le nombre d’enregistrements dans le groupe d’enregistrements d’entrée. |
| `top` | Renvoie les N premiers enregistrements triés par les colonnes spécifiées. |
| `limit` | Renvoie jusqu’au nombre de lignes spécifié. |
| `project` | Sélectionne les colonnes à inclure, renommer ou déplacer et insère de nouvelles colonnes calculées. |
| `extend` | Crée des colonnes calculées et les ajoute au jeu de résultats. |
| `makeset` |  Renvoie un tableau dynamique (JSON) de l’ensemble de valeurs distinctes prise par Expr dans le groupe. |
| `find` | Recherche des lignes qui correspondent à un prédicat dans un ensemble de tables. |

Pour voir un exemple parlant de ces opérateurs, exécutez-les à partir de la section **Prise en main** du repérage avancé.

## <a name="understand-data-types"></a>Comprendre les types de données

La chasse avancée prend en charge les types de données Kusto, y compris les types courants suivants :

| Type de données | Description et implications dans les requêtes |
|--|--|
| `datetime` | Informations sur les données et les heures représentant généralement les timestamps d’événement. [Voir les formats datetime pris en charge](/azure/data-explorer/kusto/query/scalar-data-types/datetime) |
| `string` | Chaîne de caractères en UTF-8 entre guillemets simples (`'`) ou guillemets doubles (`"`). [En savoir plus sur les chaînes](/azure/data-explorer/kusto/query/scalar-data-types/string) |
| `bool` | Ce type de données prend en charge `true` ou `false` indique. [Voir les littéraux et opérateurs pris en charge](/azure/data-explorer/kusto/query/scalar-data-types/bool) |
| `int` | Valeur entière 32 bits.  |
| `long` | Valeur entière 64 bits. |

Pour en savoir plus sur ces types de données, [consultez les types de données scalaires Kusto](/azure/data-explorer/kusto/query/scalar-data-types/).

## <a name="get-help-as-you-write-queries"></a>Obtenez de l’aide lorsque vous rédigez des requêtes

Tirez parti des fonctionnalités suivantes pour rédiger des requêtes plus rapidement :
- **Suggestion automatique** : à mesure que vous écrivez des requêtes, la chasse avancée fournit des suggestions d’IntelliSense. 
- **Arborescence de schéma** : une représentation de schéma qui inclut la liste des tables et leurs colonnes est fournie en regard de votre zone de travail. Si vous souhaitez en savoir plus, veuillez placer le pointeur sur un élément. Double-cliquez sur un élément pour l’insérer dans l’éditeur de requête.
- **[Référence de schéma](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)** : référence dans le portail avec des descriptions de table et de colonne, ainsi que des types d’événements pris en charge (`ActionType` valeurs) et des exemples de requêtes

## <a name="work-with-multiple-queries-in-the-editor"></a>Utiliser plusieurs requêtes dans l’éditeur

Vous pouvez utiliser l’éditeur de requête pour expérimenter plusieurs requêtes. Pour utiliser plusieurs requêtes :

- Séparez chaque requête avec une ligne vide.
- Placez le curseur sur n’importe quelle partie d’une requête pour sélectionner cette requête avant de l’exécuter. Cette opération exécute uniquement la requête sélectionnée. Pour exécuter une autre requête, déplacez le curseur en conséquence et sélectionnez **Exécuter la requête**.

:::image type="content" source="../../media/multiple-queries.png" alt-text="Exemple d’exécution de plusieurs requêtes dans la page **Nouvelle requête** du portail Microsoft 365 Defender" lightbox="../../media/multiple-queries.png":::

Pour un espace de travail plus efficace, vous pouvez également utiliser plusieurs onglets dans la même page de chasse. Sélectionnez **Nouvelle requête** pour ouvrir un onglet pour votre nouvelle requête.

:::image type="content" source="../../media/multitab.png" alt-text="Ouverture d’un nouvel onglet en sélectionnant Créer dans la chasse avancée dans le portail Microsoft 365 Defender" lightbox="../../media/multitab.png":::

Vous pouvez ensuite exécuter différentes requêtes sans jamais ouvrir un nouvel onglet de navigateur. 

:::image type="content" source="../../media/multitab-examples.png" alt-text="Exécuter différentes requêtes sans jamais quitter la page de chasse avancée dans le portail Microsoft 365 Defender" lightbox="../../media/multitab-examples.png":::

>[!NOTE] 
> L’utilisation de plusieurs onglets de navigateur avec repérage avancé peut vous faire perdre vos requêtes non enregistrées. Pour éviter cela, utilisez la fonctionnalité d’onglet dans la chasse avancée au lieu d’onglets de navigateur distincts.

## <a name="use-sample-queries"></a>Utiliser des exemples de requêtes

La section **Prise en main** fournit quelques requêtes simples utilisant des opérateurs fréquemment utilisés. Essayez d’exécuter ces requêtes et de leur apporter de légères modifications.

:::image type="content" source="../../media/get-started-section.png" alt-text="Section **Prise en main** de la page **Repérage avancé** du portail Microsoft 365 Defender" lightbox="../../media/get-started-section.png":::

>[!NOTE]
>Hormis les exemples de requête de base, vous pouvez également accéder à des [requêtes partagées](advanced-hunting-shared-queries.md) pour des scénarios de repérage de menace spécifiques. Explorez les requêtes partagées sur le côté gauche de la page ou le [référentiel de requêtes GitHub](https://aka.ms/hunting-queries).

## <a name="access-query-language-documentation"></a>Documentation sur le langage de requête Access

Pour plus d’informations sur le langage de requête Kusto et les opérateurs pris en charge, voir [documentation sur le langage de requête Kusto](/azure/kusto/query/).

>[!NOTE]
>Certaines tables de cet article peuvent ne pas être disponibles dans Microsoft Defender pour point de terminaison. [Activez Microsoft 365 Defender](m365d-enable.md) pour rechercher des menaces à l’aide de sources de données supplémentaires. Vous pouvez déplacer vos flux de travail de chasse avancés de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender en suivant les étapes de migration [des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)