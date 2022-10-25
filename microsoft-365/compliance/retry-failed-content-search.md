---
title: Réessayer une recherche de contenu pour résoudre une erreur d’emplacement de contenu
description: Pendant une investigation, vous pouvez utiliser le bouton Réessayer pour résoudre les recherches de contenu qui comportent des erreurs d’emplacement de contenu.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
- content-search
search.appverid:
- MOE150
- MET150
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 213340f424ef708de352b7b2d8c50648fefc6087
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688268"
---
# <a name="retry-a-content-search-to-resolve-a-content-location-error"></a>Réessayer une recherche de contenu pour résoudre une erreur d’emplacement de contenu

Lorsque vous utilisez la recherche de contenu dans le portail de conformité pour rechercher un grand nombre de boîtes aux lettres, vous pouvez obtenir des erreurs de recherche similaires à l’erreur :

```text
Error

The search on the following locations failed:
User1@contoso.com: Problem in processing the request. Please try again later. If you keep getting this error, contact your admin. (CS008-009)
User2@contoso.com: Application error occurred. Please try again later. (CS012-002)
```

Ces erreurs (avec les codes d’erreur CS001-002, CS003-002, CS008-009, CS012-002 et d’autres erreurs au format CS0XX-0XX) indiquent que la recherche de contenu n’a pas pu rechercher des emplacements de contenu spécifiques. Dans cet exemple, deux boîtes aux lettres n’ont pas fait l’objet d’une recherche. Ces erreurs sont affichées dans la page de menu volant détails d’état de la recherche de contenu.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="cause-of-content-location-errors"></a>Cause des erreurs d’emplacement du contenu

Lors de la recherche d’un grand nombre de boîtes aux lettres, la recherche est distribuée sur des milliers de serveurs dans un centre de données Microsoft. À tout moment, des serveurs spécifiques peuvent être en état de redémarrage ou en cours de basculement vers des copies redondantes. Dans l’un ou l’autre de ces cas, la demande de la recherche de contenu pour récupérer des données expirera. Dans l’exemple précédent, les erreurs pour les boîtes aux lettres qui ont échoué sont le résultat de l’expiration de la recherche.

## <a name="resolving-content-location-errors"></a>Résolution des erreurs d’emplacement du contenu

Le redémarrage de la recherche entraîne souvent des erreurs similaires sur différents serveurs. Au lieu de redémarrer la recherche, sélectionnez le bouton **Réessayer** qui s’affiche en haut de la page des résultats de la recherche.

![Sélectionnez le bouton Réessayer pour résoudre les erreurs d’emplacement du contenu.](../media/retrycontentsearch3.png)

Cela entraîne la nouvelle tentative de recherche uniquement pour les boîtes aux lettres qui ont échoué. Lorsque vous réessayez la recherche, les autres résultats qui ont été retournés avec succès sont conservés.

## <a name="tips-to-avoid-content-location-errors"></a>Conseils pour éviter les erreurs d’emplacement du contenu

Voici quelques causes supplémentaires d’erreurs d’emplacement du contenu et quelques conseils pour vous aider à les éviter lors de la recherche d’un grand nombre de boîtes aux lettres.

- La boîte aux lettres recherchée peut être occupée en raison de l’activité de l’utilisateur. Dans ce cas, le service de recherche peut se limiter lui-même pour éviter que la boîte aux lettres ne devienne indisponible. Pour éviter cela, essayez d’exécuter des recherches pendant les heures d’ouverture.
- La requête de recherche peut récupérer trop de contenu à partir de la boîte aux lettres. Si possible, essayez de limiter l’étendue de la recherche à l’aide de mots clés, de plages de dates et de conditions de recherche.
- Trop de mots clés ou d’expressions clés lorsque vous créez une requête de recherche à l’aide de la [liste de mots clés](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches). Lorsque vous exécutez une requête de recherche qui utilise la liste de mots clés, le service exécute essentiellement une recherche distincte pour chaque ligne de la liste de mots clés afin que des statistiques puissent être générées. Si vous utilisez la liste de mots clés dans les requêtes de recherche, réduisez le nombre de lignes dans la liste de mots clés ou divisez le nombre de mots clés en listes plus petites et créez une recherche différente pour chaque liste de mots clés.

  > [!NOTE]
  > Pour réduire les problèmes causés par les listes de mots clés volumineuses, vous êtes maintenant limité à un maximum de 20 lignes dans la liste de mots clés d’une requête de recherche.

- Trop de recherches sont effectuées sur la même boîte aux lettres en même temps. Si possible, essayez d’exécuter une recherche à la fois sur une boîte aux lettres.
- Recherche d’un trop grand nombre de boîtes aux lettres dans une seule recherche. La probabilité d’erreurs d’emplacement du contenu augmente lors de la recherche d’un grand nombre de boîtes aux lettres. Si possible, essayez d’exécuter plusieurs recherches afin que chaque recherche inclue un sous-ensemble de boîtes aux lettres dans votre organisation.
- La maintenance requise est effectuée sur la boîte aux lettres. Bien que cette cause se produise probablement rarement, patientez un peu après avoir reçu l’erreur d’emplacement du contenu, puis réessayez la recherche.
