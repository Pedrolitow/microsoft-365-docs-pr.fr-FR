---
title: Prise en charge de LASK/Double byte pour Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment Advanced eDiscovery dans Microsoft 365 prend en charge les langues chinoise, japonaise et coréenne (JCK), qui utilisent un jeu de caractères sur deux caractères.
ms.openlocfilehash: ee47c5cd7f1a378ccfff05b8f7712e91092907cb
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50926600"
---
# <a name="cjk-language-support-for-advanced-ediscovery"></a>Prise en charge du langageJCK pour Advanced eDiscovery

Advanced eDiscovery prend en charge les langues de jeu de caractères sur deux sur deux caractères (notamment le chinois simplifié, le chinois traditionnel, le japonais et le coréen, qui sont collectivement appelées langues *DUK),* pour les scénarios avancés suivants dans un jeu à réviser :

- Lorsque vous [interrogez les données dans un jeu à réviser](review-set-search.md).

- Lorsque vous [balisez des documents dans un jeu à réviser.](tagging-documents.md)

- Lorsque vous [analysez des données de cas dans un jeu à réviser](analyzing-data-in-review-set.md) à l’aide de la détection des quasi-doublons, du thread de messagerie électronique et de l’analyse des thèmes.

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

**Comment créer une recherche pour collecter des éléments qui contiennent des caractères DUKS ?**

Vous pouvez utiliser des caractèresJC pour les recherches par mot [clé,](building-search-queries.md#keyword-searches)les requêtes par mot clé et les [conditions](keyword-queries-and-search-conditions.md) de recherche lors de la recherche de contenu dans Advanced eDiscovery. La recherche de caractères DUKS est également prise en charge lors de la recherche de contenu dans core eDiscovery et la recherche de contenu.

Nous fournissons la [](keyword-queries-and-search-conditions.md#search-operators) prise en charge DE LASK pour tous les opérateurs de recherche et [conditions](keyword-queries-and-search-conditions.md#search-conditions)de recherche, y compris les opérateurs booléens **ET**, **OU**, **NOT** et **NEAR**.

Si vous êtes certain que les emplacements de contenu ou les éléments contiennent des caractèresJC, mais que les recherches ne retournent aucun résultat, cliquez sur l’icône langue-pays/région de la requête ![Icône Langue-pays/région de requête dans la recherche de contenu](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) et sélectionnez la valeur de code de culture correspondant au pays/la langue pour la recherche. La langue/région par défaut est neutre.

**Puis-je rechercher plusieurs langues à la fois ?**

Cela dépend de votre scénario de recherche.

- Lorsque vous [interrogez des données dans un jeu à réviser](review-set-search.md) dans Advanced eDiscovery, vous pouvez rechercher plusieurs langues.

- Lorsque vous [créez une recherche pour collecter des données,](create-search-to-collect-data.md)créez une recherche distincte pour chaque langue que vous ciblez. Par exemple, si vous recherchez un document qui contient à la fois le chinois et le coréen, sélectionnez Chinois pour votre première requête et sélectionnez Coréen pour votre deuxième requête.

**Je ne vois pas l’icône langue-pays/région de la requête pour sélectionner une langue pour les requêtes dans un jeu à réviser. Comment puis-je spécifier un langage de requête dans une recherche de jeu à réviser ?**

Pour les requêtes de jeu à réviser, il n’est pas nécessaire de spécifier une langue de document. Advanced eDiscovery détecte automatiquement les langues de document lorsque vous ajoutez du contenu à un jeu à réviser. Cela vous permet d’optimiser les résultats de votre requête dans un jeu à réviser.

**Puis-je voir les langues détectées dans les [métadonnées de fichier](view-documents-in-review-set.md#file-metadata)?**

Non, vous ne pouvez pas voir les langues détectées dans les métadonnées de fichier.

**Puis-je filtrer par langues de document dans un jeu à réviser**?

Non, vous ne pouvez pas filtrer, trier ou rechercher par langues de document dans un jeu à réviser.

**Cette version DEMCS pour les scénarios d’ensemble de révision affectera-t-elle l’une de mes recherches et jeux de révision existants ?**

Non, aucune de vos recherches et jeux de révision existants ne change. Vous n’avez pas besoin de réindexer des données existantes et les résultats de recherche pour le texte en anglais seront les mêmes.

**Comment modifier ma langue d’affichage en chinois, japonais ou coréen ?**

Pour plus d’informations sur la modification de la langue d’affichage et du fuseau horaire, voir Comment définir les paramètres de langue et de région [pour Office 365](/office365/troubleshoot/access-management/set-language-and-region).

## <a name="known-issues"></a>Problèmes connus

- OcR ne prend pas en charge les caractères DUKS À partir de fichiers image

- Les fichiers e-mail (tels que *.eml et *.msg) en affichage [Annotate](view-documents-in-review-set.md#annotate-view) ne sont pas pris en charge pour les langues DUKCO.

- La mise en surbrillance des résultats de recherche [en affichage Texte](view-documents-in-review-set.md#text-view) n’est pas prise en charge pour les langues DUKS.

- Le [module de pertinence](using-relevance.md) utilisé pour analyser les données ne prend pas en charge les langues DUKCO.

- [Les prises en charge basées sur](managing-holds.md#manage-non-custodial-holds) des requêtes ne sont pas prises en charge pour les langues DUKS.