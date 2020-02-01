---
title: Découvrez le langage de requête de repérage avancé dans la Protection Microsoft contre les menaces
description: Créez votre première requête de repérage de menace et découvrez les opérateurs communs et les autres aspects du langage de requête de repérage avancé
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, langue, apprentissage, première requête, télémétrie, événements, télémétrie, détections personnalisées, schéma, Kusto, opérateurs, types de données
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
ms.openlocfilehash: 586b887c9c5c1e4c19623c89dd08ed62ba0d4bb2
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41600341"
---
# <a name="learn-the-advanced-hunting-query-language"></a>Découvrir le langage de requête de repérage avancé

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le repérage avancé est basé sur le [langage de requête Kusto](https://docs.microsoft.com/azure/kusto/query/). Vous pouvez utiliser la syntaxe et les opérateurs Kusto pour créer des requêtes qui recherchent des informations dans le [schéma](advanced-hunting-schema-tables.md) spécifiquement structuré pour un repérage avancé. Pour mieux comprendre ces concepts, exécutez votre première requête.

## <a name="try-your-first-query"></a>Essayez votre première requête

dans le Centre de sécurité Microsoft 365, placez-vous dans **Repérage** pour exécuter votre première requête. Consultez l’exemple qui suit :

```kusto
// Finds PowerShell execution events that could involve a download.
DeviceProcessEvents 
| where Timestamp > ago(7d)
| where FileName in ("powershell.exe", "POWERSHELL.EXE", "powershell_ise.exe", "POWERSHELL_ISE.EXE") 
| where ProcessCommandLine has "Net.WebClient"
        or ProcessCommandLine has "DownloadFile"
        or ProcessCommandLine has "Invoke-WebRequest"
        or ProcessCommandLine has "Invoke-Shellcode"
        or ProcessCommandLine contains "http:"
| project Timestamp, DeviceName, InitiatingProcessFileName, FileName, ProcessCommandLine
| top 100 by Timestamp
```

Voici son futur aspect dans le repérage avancé.

![Image de la requête de repérage avancé Microsoft Defender – Protection avancée contre les menaces](../images/advanced-hunting-query-example.png)

La requête commence par un bref commentaire décrivant sa fonction. Cela vous permet de choisir ultérieurement d’enregistrer votre requête et de la partager avec d’autres dans votre organisation.

```kusto
// Finds PowerShell execution events that could involve a download.
DeviceProcessEvents
```

La requête elle-même commence généralement par un nom de table suivi d’une série d’éléments commençant par une barre verticale (`|`). Dans cet exemple, nous commençons par ajouter avec le nom de la table `DeviceProcessEvents` et ajoutons des éléments redirigés le cas échéant.

Le premier élément redirigé est un filtre de temps étendu dans les sept jours précédents. La conservation d’un intervalle de temps le plus étroit possible permet de s’assurer que les requêtes fonctionnent bien, renvoient des résultats gérables et n’expirent pas.

```kusto
| where Timestamp > ago(7d)
```

L’intervalle de temps est immédiatement suivi d’une recherche de fichiers représentant l’application PowerShell.

```kusto
| where FileName in ("powershell.exe", "POWERSHELL.EXE", "powershell_ise.exe", "POWERSHELL_ISE.EXE")
```

Par la suite, la requête recherche les lignes de commande généralement utilisées avec PowerShell pour télécharger les fichiers.

```kusto
| where ProcessCommandLine has "Net.WebClient"
        or ProcessCommandLine has "DownloadFile"
        or ProcessCommandLine has "Invoke-WebRequest"
        or ProcessCommandLine has "Invoke-Shellcode"
        or ProcessCommandLine contains "http:"
```

Maintenant que votre requête identifie clairement les données que vous recherchez, vous pouvez ajouter des éléments qui définissent l’apparence des résultats. `project` renvoie des colonnes spécifiques et `top` limite le nombre de résultats. De ce fait, les résultats sont bien mis en forme et raisonnablement volumineux et faciles à traiter.

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, FileName, ProcessCommandLine
| top 100 by Timestamp
```

Cliquez sur **Exécuter la requête** pour afficher les résultats. Vous pouvez développer l’affichage à l’écran pour pouvoir vous concentrer sur votre requête de repérage et sur les résultats.

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

## <a name="use-sample-queries"></a>Utiliser des exemples de requêtes

La section **Prise en main** fournit quelques requêtes simples utilisant des opérateurs fréquemment utilisés. Essayez d’exécuter ces requêtes et de leur apporter de légères modifications.

![Image d’une fenêtre de repérage avancé](../images/advanced-hunting-get-started.png)

>[!NOTE]
>Hormis les exemples de requête de base, vous pouvez également accéder à des [requêtes partagées](advanced-hunting-shared-queries.md) pour des scénarios de repérage de menace spécifiques. Explorez les requêtes partagées sur le côté gauche de la page ou le référentiel de requête GitHub.

## <a name="access-query-language-documentation"></a>Documentation sur le langage de requête Access

Pour plus d’informations sur le langage de requête Kusto et les opérateurs pris en charge, voir [documentation sur le langage de requête Kusto](https://docs.microsoft.com/azure/kusto/query/).

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)