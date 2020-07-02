---
title: Découvrez le langage de requête de repérage avancé dans la Protection Microsoft contre les menaces
description: Créez votre première requête de repérage de menace et découvrez les opérateurs communs et les autres aspects du langage de requête de repérage avancé
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, langue, apprentissage, première requête, télémétrie, événements, télémétrie, détections personnalisées, schéma, Kusto, opérateurs, types de données, téléchargement PowerShell, exemple de requête
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
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 250d19a09d79fc5fd8c69f2ebd24abadc642fafc
ms.sourcegitcommit: 634abe8a237e27dfe82376e6ef32280aab5d4a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "45005845"
---
# <a name="learn-the-advanced-hunting-query-language"></a>Découvrir le langage de requête de repérage avancé

**S’applique à :**
- Protection Microsoft contre les menaces

Le repérage avancé est basé sur le [langage de requête Kusto](https://docs.microsoft.com/azure/kusto/query/). Vous pouvez utiliser la syntaxe et les opérateurs Kusto pour créer des requêtes qui recherchent des informations dans le [schéma](advanced-hunting-schema-tables.md) spécifiquement structuré pour un repérage avancé. Pour mieux comprendre ces concepts, exécutez votre première requête.

## <a name="try-your-first-query"></a>Essayez votre première requête

Dans le centre de sécurité Microsoft 365, accédez à la **recherche pour exécuter** votre première requête. Consultez l’exemple qui suit :

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

Voici son futur aspect dans le repérage avancé.

![Image de la requête de recherche avancée Microsoft Threat Protection](../../media/advanced-hunting-query-example-2.png)

### <a name="describe-the-query-and-specify-the-tables-to-search"></a>Décrire la requête et spécifier les tables à rechercher
Un bref commentaire a été ajouté au début de la requête pour décrire sa fonction. Cela vous permet de décider ultérieurement d’enregistrer la requête et de la partager avec d’autres membres de votre organisation. 

```kusto
// Finds PowerShell execution events that could involve a download
```

La requête elle-même commence généralement par un nom de table suivi d’une série d’éléments commençant par une barre verticale (`|`). Dans cet exemple, nous commençons par créer une Union de deux tables, `DeviceProcessEvents` et `DeviceNetworkEvents` et ajoutons des éléments redirigés selon les besoins.

```kusto
union DeviceProcessEvents, DeviceNetworkEvents
```
### <a name="set-the-time-range"></a>Définir la plage horaire
Le premier élément Redirigé est un filtre temporel étendu aux sept jours précédents. La conservation d’un intervalle de temps le plus étroit possible permet de s’assurer que les requêtes fonctionnent bien, renvoient des résultats gérables et n’expirent pas.

```kusto
| where Timestamp > ago(7d)
```

### <a name="check-specific-processes"></a>Vérifier des processus spécifiques
La plage horaire est immédiatement suivie d’une recherche de noms de fichiers de processus représentant l’application PowerShell.

```kusto
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### <a name="search-for-specific-command-strings"></a>Rechercher des chaînes de commande spécifiques
Ensuite, la requête recherche des chaînes dans les lignes de commande qui sont généralement utilisées pour télécharger des fichiers à l’aide de PowerShell.

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

### <a name="customize-result-columns-and-length"></a>Personnaliser les colonnes de résultats et la longueur 
Maintenant que votre requête identifie clairement les données que vous recherchez, vous pouvez ajouter des éléments qui définissent l’apparence des résultats. `project`renvoie des colonnes spécifiques et `top` limite le nombre de résultats. Ces opérateurs permettent de s’assurer que les résultats sont bien formatés et raisonnablement volumineux et faciles à traiter.

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

Cliquez sur **Exécuter la requête** pour afficher les résultats. Sélectionnez l’icône développer en haut à droite de l’éditeur de requête pour vous concentrer sur votre requête de recherche et les résultats. 

![Image du contrôle Expand dans l’éditeur de requête de recherche avancée](../../media/advanced-hunting-expand.png)

>[!TIP]
>Vous pouvez afficher les résultats de la requête sous forme de graphiques et ajuster rapidement les filtres. Pour obtenir des instructions, consultez la rubrique [utilisation des résultats de requête](advanced-hunting-query-results.md)

## <a name="learn-common-query-operators-for-advanced-hunting"></a>Découvrir les opérateurs de requête courants pour le repérage avancé

Maintenant que vous avez exécuté votre première requête et que vous avez une idée générale de ses composants, il est temps de revenir en arrière pour découvrir quelques notions de base. Le langage de requête Kusto utilisé par le repérage avancé prend en charge divers opérateurs, notamment les opérateurs communs suivants.

| Opérateur | Description et utilisation |
|--|--|
| `where` | Filtre une table sur le sous-ensemble de lignes qui répondent à un prédicat. |
| `summarize` | Produit une table qui agrège le contenu de la table d’entrée. |
| `join` | Fusionne les lignes de deux tables pour former une nouvelle table en faisant correspondre les valeurs des colonnes spécifiées de chaque table. |
| `count` | Renvoie le nombre d’enregistrements dans le groupe d’enregistrements d’entrée. |
| `top` | Renvoie les N premiers enregistrements triés par les colonnes spécifiées. |
| `limit` | Renvoie jusqu’au nombre de lignes spécifié. |
| `project` | Sélectionne les colonnes à inclure, renommer ou déplacer et insère de nouvelles colonnes calculées. |
| `extend` | Crée des colonnes calculées et les ajoute au jeu de résultats. |
| `makeset` |  Renvoie un tableau dynamique (JSON) de l’ensemble de valeurs distinctes prise par Expr dans le groupe. |
| `find` | Recherche des lignes qui correspondent à un prédicat dans un ensemble de tables. |

Pour voir un exemple parlant de ces opérateurs, exécutez-les à partir de la section **Prise en main** du repérage avancé.

## <a name="understand-data-types-and-their-query-syntax-implications"></a>Comprendre les types de données et leurs implications dans la syntaxe de requête

Les données des tables de repérage avancé sont généralement classées dans les types de données suivants.

| Type de données | Description et implications dans les requêtes |
|--|--|
| `datetime` | Informations sur les données et les heures représentant généralement les horodatages d’événement |
| `string` | Chaîne de caractères |
| `bool` | True ou false |
| `int` | Valeur numérique de 32 bits  |
| `long` | Valeur numérique de 64 bits |

## <a name="get-help-as-you-write-queries"></a>Obtenez de l’aide lorsque vous rédigez des requêtes
Tirez parti des fonctionnalités suivantes pour rédiger des requêtes plus rapidement :
- **Suggestion** automatique : lors de l’écriture de requêtes, la recherche avancée fournit des suggestions d’IntelliSense. 
- **Référence de schéma** : une référence de schéma qui inclut la liste des tableaux et leurs colonnes est fournie à côté de votre espace de travail. Si vous souhaitez en savoir plus, veuillez placer le pointeur sur un élément. Double-cliquez sur un élément pour l’insérer dans l’éditeur de requête.

## <a name="use-sample-queries"></a>Utiliser des exemples de requêtes

La section **Prise en main** fournit quelques requêtes simples utilisant des opérateurs fréquemment utilisés. Essayez d’exécuter ces requêtes et de leur apporter de légères modifications.

![Image d’une fenêtre de repérage avancé](../../media/advanced-hunting-get-started.png)

>[!NOTE]
>Hormis les exemples de requête de base, vous pouvez également accéder à des [requêtes partagées](advanced-hunting-shared-queries.md) pour des scénarios de repérage de menace spécifiques. Explorez les requêtes partagées sur le côté gauche de la page ou le référentiel de requête GitHub.

## <a name="access-query-language-documentation"></a>Documentation sur le langage de requête Access

Pour plus d’informations sur le langage de requête Kusto et les opérateurs pris en charge, voir [documentation sur le langage de requête Kusto](https://docs.microsoft.com/azure/kusto/query/).

## <a name="related-topics"></a>Sujets associés
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
