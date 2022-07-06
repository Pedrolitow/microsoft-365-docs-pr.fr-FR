---
title: Réessayer une recherche de contenu pour résoudre une erreur d’emplacement de contenu
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: ''
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Au cours d’une enquête, vous pouvez utiliser le bouton Nouvelle tentative pour résoudre les recherches de contenu qui comportent des erreurs d’emplacement de contenu.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c524be95ac72f44e58b03958694d26c52a401e40
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638166"
---
# <a name="retry-a-content-search-to-resolve-a-content-location-error"></a>Réessayer une recherche de contenu pour résoudre une erreur d’emplacement de contenu

Lorsque vous utilisez la recherche de contenu dans le Centre de sécurité et de conformité pour rechercher un grand nombre de boîtes aux lettres, vous pouvez obtenir des erreurs de recherche similaires à l’erreur :

```text
Error


The search on the following locations failed:

User1@contoso.com: Problem in processing the request. Please try again later. If you keep getting this error, contact your admin. (CS008-009)

User2@contoso.com: Application error occurred. Please try again later. (CS012-002)
```

Ces erreurs (avec les codes d’erreur CS001-002, CS003-002, CS008-009, CS012-002 et autres erreurs du formulaire CS0XX-0XX) indiquent que la recherche de contenu n’a pas pu rechercher des emplacements de contenu spécifiques ; Dans cet exemple, deux boîtes aux lettres n’ont pas été recherchées. Ces erreurs sont affichées dans la page de menu volant détails de l’état de la recherche de contenu.

## <a name="cause-of-content-location-errors"></a>Cause d’erreurs d’emplacement de contenu

Lors de la recherche d’un grand nombre de boîtes aux lettres, la recherche est distribuée sur des milliers de serveurs dans un centre de données Microsoft. À tout moment, des serveurs spécifiques peuvent être en état de redémarrage ou en cours de basculement vers des copies redondantes. Dans l’un de ces cas, la demande de recherche de contenu pour récupérer des données expire. Dans l’exemple précédent, les erreurs pour les boîtes aux lettres qui ont échoué sont le résultat du délai d’expiration de la recherche.

## <a name="resolving-content-location-errors"></a>Résolution des erreurs d’emplacement de contenu

Le redémarrage de la recherche entraîne souvent des erreurs similaires sur différents serveurs. Au lieu de redémarrer la recherche, cliquez sur le bouton **Nouvelle tentative** qui s’affiche en haut de la page des résultats de la recherche.

![Cliquez sur le bouton Nouvelle tentative pour résoudre les erreurs d’emplacement de contenu.](../media/retrycontentsearch3.png)

Cela entraîne la nouvelle tentative de recherche uniquement pour les boîtes aux lettres qui ont échoué. Lorsque vous réessayez la recherche, les autres résultats qui ont été retournés avec succès sont conservés.

## <a name="tips-to-avoid-content-location-errors"></a>Conseils pour éviter les erreurs d’emplacement de contenu

Voici quelques causes supplémentaires d’erreurs d’emplacement de contenu et quelques conseils pour vous aider à les éviter lors de la recherche d’un grand nombre de boîtes aux lettres.

- La boîte aux lettres recherchée peut être occupée en raison de l’activité de l’utilisateur. Dans ce cas, le service de recherche peut se limiter pour empêcher l’indisponibilité de la boîte aux lettres. Pour éviter cela, essayez d’exécuter des recherches pendant les heures creuses.

- La requête de recherche peut récupérer trop de contenu à partir de la boîte aux lettres. Si possible, essayez de limiter l’étendue de la recherche à l’aide de mots clés, de plages de dates et de conditions de recherche.

- Trop de mots clés ou d’expressions clés lorsque vous créez une requête de recherche à l’aide de la [liste de mots clés](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches). Lorsque vous exécutez une requête de recherche qui utilise la liste de mots clés, le service exécute essentiellement une recherche distincte pour chaque ligne de la liste de mots clés afin que les statistiques puissent être générées. Si vous utilisez la liste de mots clés dans les requêtes de recherche, réduisez le nombre de lignes dans la liste de mots clés ou divisez les mots clés numériques en listes plus petites et créez une recherche différente pour chaque liste de mots clés.

  > [!NOTE]
  > Pour réduire les problèmes causés par les listes de mots clés volumineux, vous êtes désormais limité à un maximum de 20 lignes dans la liste de mots clés d’une requête de recherche.

- Trop de recherches sont effectuées simultanément sur la même boîte aux lettres. Si possible, essayez d’exécuter une recherche à la fois sur une boîte aux lettres.

- Recherche d’un trop grand nombre de boîtes aux lettres dans une seule recherche. La probabilité d’erreurs d’emplacement de contenu augmente lors de la recherche d’un grand nombre de boîtes aux lettres. Si possible, essayez d’exécuter plusieurs recherches afin que chaque recherche inclue un sous-ensemble de boîtes aux lettres dans votre organisation.

- La maintenance requise est en cours sur la boîte aux lettres. Bien que cette cause se produise probablement rarement, attendez un peu après avoir reçu l’erreur d’emplacement de contenu, puis réessayez la recherche.
