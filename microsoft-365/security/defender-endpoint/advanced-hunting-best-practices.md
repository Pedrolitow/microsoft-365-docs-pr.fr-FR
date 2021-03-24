---
title: Meilleures pratiques de requête pour le recherche avancée
description: Découvrez comment créer des requêtes de repérage de menace, efficace et sans erreur dans le cas d’un repérage avancé
keywords: repérage avancé, repérage de menace, repérage de cybermenace, mdatp, microsoft defender atp, recherche wdatp, requête, télémétrie, détections personnalisées, schéma, kusto, éviter le délai d’attente, lignes de commande, ID de processus
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 6259ac1c5804b244c825a1bb54401640fdefaf34
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064393"
---
# <a name="advanced-hunting-query-best-practices"></a>Pratiques recommandées pour la requête de repérage avancé

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)


>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-bestpractices-abovefoldlink)

## <a name="optimize-query-performance"></a>Optimiser la performance des requêtes

Appliquez ces recommandations pour obtenir des résultats plus rapidement et éviter les délai d’accès lors de l’exécution de requêtes complexes.

- Lorsque vous essayez de nouvelles requêtes, utilisez toujours `limit` pour éviter des jeux de résultats très volumineux. Vous pouvez également évaluer la taille du jeu de résultats à l’aide de `count`.
- Utilisez tout d’abord les filtres de temps. Dans l’idéal, limitez vos requêtes à sept jours.
- Placez les filtres qui sont censés supprimer la plupart des données au début de la requête, juste après le filtre de temps.
- Utilisez l’opérateur `has` sur `contains` pour rechercher des jetons complets.
- Consultez une colonne spécifique plutôt que d’exécuter des recherches de texte complet dans toutes les colonnes.
- Lorsque vous joignez des tableaux, vous devez d’abord spécifier le tableau comportant moins de lignes.
- `project` uniquement les colonnes nécessaires des tableaux que vous avez jointes.

>[!TIP]
>Si vous souhaitez en savoir plus sur l’amélioration des performances de requête, veuillez consulter [Meilleures pratiques de requête Kusto](https://docs.microsoft.com/azure/kusto/query/best-practices).

## <a name="query-tips-and-pitfalls"></a>Conseils et pièges de la requête

### <a name="queries-with-process-ids"></a>Requêtes avec ID de processus

Les ID de processus (PID) sont recyclés dans Windows et réutilisés pour les nouveaux processus. Ils ne peuvent pas être utilisés comme identificateurs uniques pour des processus spécifiques. Pour obtenir un identificateur unique pour un processus sur un appareil spécifique, utilisez l’ID de processus avec l’heure de création du processus. Lorsque vous joignez ou synthétiser des données autour des processus, incluez des colonnes pour l’identificateur de l’appareil (ou ), l’ID de processus ( ou ), et l’heure de création `DeviceId` du processus ( ou `DeviceName` `ProcessId` `InitiatingProcessId` `ProcessCreationTime` `InitiatingProcessCreationTime` ).

L’exemple de requête suivant trouve les processus qui accèdent à plus de 10 adresses IP via le port 445 (SMB), qui peut rechercher des partages de fichiers.

```kusto
DeviceNetworkEvents
| where RemotePort == 445 and Timestamp > ago(12h) and InitiatingProcessId !in (0, 4)
| summarize RemoteIPCount=dcount(RemoteIP) by DeviceName, InitiatingProcessId, InitiatingProcessCreationTime, InitiatingProcessFileName
| where RemoteIPCount > 10
```

La requête se résume par `InitiatingProcessId` et `InitiatingProcessCreationTime` de sorte qu’elle examine un seul processus, sans mélanger plusieurs processus ayant le même ID de processus.

### <a name="queries-with-command-lines"></a>Requêtes avec des lignes de commande

Les lignes de commande peuvent varier. Le cas échéant, filtrez sur les noms des fichiers et effectuez une correspondance approximative.

Plusieurs méthodes s’offrent à vous pour créer une ligne de commande pour accomplir une tâche. Par exemple, un attaquant peut référencer un fichier image avec ou sans chemin, sans extension de fichier, à l’aide de variables d’environnement ou de guillemets. De plus, l’attaquant peut également modifier l’ordre des paramètres ou ajouter plusieurs guillemets et espaces.

Pour créer des requêtes plus durables à l’aide de lignes de commande, appliquez les pratiques suivantes :

- Identifiez les processus connus (par exemple, *net.exe* ou *psexec.exe*) en faisant correspondre les champs de nom de fichier, au lieu de filtrer sur le champ de ligne de commande.
- Lors de l’interrogation des arguments de la ligne de commande, ne recherchez pas une correspondance exacte de plusieurs arguments non liés dans un certain ordre. Au lieu de cela, vous devez utiliser des expressions régulières ou utiliser plusieurs opérateurs de contenu séparés..
- Utilisez des correspondances non respectées de casse. Par exemple, utilisez `=~` , et non , `in~` `contains` `==` `in` et `contains_cs`
- Pour atténuer les techniques d’obscurcissement de lignes de commande, vous pouvez supprimer les guillemets, remplacer les virgules par des espaces et remplacer plusieurs espaces consécutifs par un seul espace. Notez qu'il existe des techniques d'obscurcissement DOS plus complexes qui nécessitent d'autres approches, mais celles-ci peuvent aider à résoudre les problèmes les plus fréquents.

Les exemples suivants illustrent différentes manières de créer une requête qui recherche le fichier *net.exe* pour arrêter le service Pare-feu Windows Defender :

```kusto
// Non-durable query - do not use
DeviceProcessEvents
| where ProcessCommandLine == "net stop MpsSvc"
| limit 10

// Better query - filters on filename, does case-insensitive matches
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe") and ProcessCommandLine contains "stop" and ProcessCommandLine contains "MpsSvc" 

// Best query also ignores quotes
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe")
| extend CanonicalCommandLine=replace("\"", "", ProcessCommandLine)
| where CanonicalCommandLine contains "stop" and CanonicalCommandLine contains "MpsSvc" 
```

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-bestpractices-belowfoldlink)

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Vue d’ensemble des détections personnalisées](overview-custom-detections.md)
