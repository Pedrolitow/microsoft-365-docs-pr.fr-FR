---
title: Réessayer une recherche de contenu pour résoudre une erreur d’emplacement de contenu
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: ''
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Au cours d’un examen, vous pouvez utiliser le bouton Nouvelle tentative pour résoudre les recherches de contenu qui ont des erreurs d’emplacement de contenu.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ee60ab8aa5dad32360303f31924995f110ed99cc
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59202326"
---
# <a name="retry-a-content-search-to-resolve-a-content-location-error"></a>Réessayer une recherche de contenu pour résoudre une erreur d’emplacement de contenu

Lorsque vous utilisez la recherche de contenu dans le centre de sécurité et conformité pour rechercher un grand nombre de boîtes aux lettres, vous pouvez obtenir des erreurs de recherche similaires à l’erreur :

```text
Error


The search on the following locations failed:

User1@contoso.com: Problem in processing the request. Please try again later. If you keep getting this error, contact your admin. (CS008-009)

User2@contoso.com: Application error occurred. Please try again later. (CS012-002)
```

Ces erreurs (avec des codes d’erreur de CS001-002, CS003-002, CS008-009, CS012-002 et d’autres erreurs de la forme CS0XX-0XX) indiquent que la recherche de contenu n’a pas réussi à rechercher des emplacements de contenu spécifiques ; dans cet exemple, deux boîtes aux lettres n’ont pas été recherchés. Ces erreurs s’affichent dans la page de présentation des détails de l’état de la recherche de contenu.

## <a name="cause-of-content-location-errors"></a>Cause des erreurs d’emplacement de contenu

Lorsque vous recherchez un grand nombre de boîtes aux lettres, la recherche est distribuée sur des milliers de serveurs dans un centre de données Microsoft. À tout moment, des serveurs spécifiques peuvent être en état de redémarrage ou en cours de rerouillage vers des copies redondantes. Dans l’un ou l’autre de ces cas, la demande de la recherche de contenu pour récupérer des données va prendre du temps. Dans l’exemple précédent, les erreurs des boîtes aux lettres qui ont échoué étaient le résultat du délai d’insétion de la recherche.

## <a name="resolving-content-location-errors"></a>Résolution des erreurs d’emplacement de contenu

Le redémarrage de la recherche entraîne souvent des erreurs similaires sur différents serveurs. Au lieu de redémarrer la  recherche, cliquez sur le bouton Nouvelle tentative qui s’affiche en haut de la page des résultats de la recherche.

![Cliquez sur le bouton Nouvelle tentative pour résoudre les erreurs d’emplacement de contenu.](../media/retrycontentsearch3.png)

Cela entraîne une nouvelle tentative de recherche uniquement pour les boîtes aux lettres qui ont échoué. Lorsque vous retentez la recherche, les autres résultats renvoyés avec succès sont conservés.

## <a name="tips-to-avoid-content-location-errors"></a>Astuces éviter les erreurs d’emplacement de contenu

Voici quelques causes supplémentaires des erreurs d’emplacement de contenu et quelques conseils pour vous aider à les éviter lors de la recherche d’un grand nombre de boîtes aux lettres.

- La boîte aux lettres à rechercher peut être occupée en raison de l’activité de l’utilisateur. Dans ce cas, le service de recherche peut se limiter lui-même pour empêcher l’indisponibilité de la boîte aux lettres. Pour éviter cela, essayez d’effectuer des recherches en de autres heures d’ouverture.

- La requête de recherche peut récupérer trop de contenu de la boîte aux lettres. Si possible, essayez de restreindre l’étendue de la recherche à l’aide de mots clés, de plages de dates et de conditions de recherche.

- Trop de mots clés ou d’expressions de mots clés lorsque vous créez une requête de recherche à l’aide de la liste [de mots clés.](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches) Lorsque vous exécutez une requête de recherche qui utilise la liste de mots clés, le service exécute essentiellement une recherche distincte pour chaque ligne de la liste de mots clés afin que des statistiques soient générées. Si vous utilisez la liste de mots clés dans les requêtes de recherche, réduisez le nombre de lignes dans la liste de mots clés ou divisez les mots clés numériques en listes plus petites et créez une recherche différente pour chaque liste de mots clés.

  > [!NOTE]
  > Pour réduire les problèmes causés par les grandes listes de mots clés, vous êtes maintenant limité à 20 lignes au maximum dans la liste des mots clés d’une requête de recherche.

- Trop de recherches sont effectuées sur la même boîte aux lettres en même temps. Si possible, essayez d’exécuter une recherche à la fois sur une seule boîte aux lettres.

- Recherche d’un trop grand nombre de boîtes aux lettres dans une seule recherche. La probabilité d’erreurs d’emplacement de contenu augmente lorsque vous recherchez un grand nombre de boîtes aux lettres. Si possible, essayez d’exécuter plusieurs recherches afin que chaque recherche inclut un sous-ensemble de boîtes aux lettres dans votre organisation.

- La maintenance requise est en cours sur la boîte aux lettres. Bien que cette cause se produise probablement rarement, patientez un peu après la réception de l’erreur d’emplacement de contenu, puis réessayez la recherche.
