---
title: Prise en charge de la fonctionnalité CJC/double octet pour Advanced eDiscovery
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
description: Découvrez comment Advanced eDiscovery dans Microsoft 365 prend en charge les langues chinoise, japonaise et coréenne (CJK), qui utilisent un jeu de caractères codés sur deux octets.
ms.openlocfilehash: cef91001f48512545ce528d6f43de97c28c4c495
ms.sourcegitcommit: e17fd18b01d70e6428263c20cbce4b92e2a97765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "48626934"
---
# <a name="cjk-language-support-for-advanced-ediscovery"></a>Prise en charge de la langue CJC pour Advanced eDiscovery

Advanced eDiscovery prend en charge les langues de jeu de caractères codés sur deux octets (notamment le chinois simplifié, le chinois traditionnel, le japonais et le coréen, qui sont appelés « langues *CJK* ») pour les scénarios avancés suivants dans un jeu de révision :

- Lorsque vous [interrogez les données d’un ensemble de révision](review-set-search.md).

- Lorsque vous [balisez des documents dans un ensemble de révision](tagging-documents.md).

- Lorsque vous [analysez les données de cas dans un jeu de révision](analyzing-data-in-review-set.md) à l’aide de la détection à proximité, du Threading de messagerie électronique et de l’analyse des thèmes.

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

**Comment puis-je créer une recherche pour collecter des éléments qui contiennent des caractères CJK ?**

Vous pouvez utiliser les caractères CJK pour les [recherches par Mots clés](building-search-queries.md#keyword-searches), [les requêtes de mot clé et les conditions de recherche](keyword-queries-and-search-conditions.md) lors de la recherche de contenu dans Advanced eDiscovery. La recherche de caractères CJK est également prise en charge lors de la recherche de contenu dans la recherche de contenu et eDiscovery de base.

Nous fournissons la prise en charge CJK pour tous les [opérateurs de recherche](keyword-queries-and-search-conditions.md#search-operators) et toutes les [conditions de recherche](keyword-queries-and-search-conditions.md#search-conditions), y compris les opérateurs booléens **and**, **or**, **not**et **near**.

Si vous êtes certain que les emplacements de contenu ou les éléments contiennent des caractères CJK, mais que les recherches ne renvoient pas de résultats, cliquez sur l’icône langue de la requête-pays/région. ![Icône de langue de requête pays/région dans la recherche de contenu](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) et sélectionnez la valeur de code de culture du pays correspondant à la recherche. La langue/région par défaut est neutre.

**Puis-je Rechercher plusieurs langues en même temps ?**

Cela dépend de votre scénario de recherche.

- Lorsque vous [interrogez des données dans un jeu de réexamen](review-set-search.md) dans Advanced eDiscovery, vous pouvez rechercher plusieurs langues.

- Lorsque vous [créez une recherche pour collecter des données](create-search-to-collect-data.md), créez une recherche distincte pour chaque langue que vous ciblez. Par exemple, si vous recherchez un document qui contient à la fois chinois et coréen, sélectionnez chinois pour votre première requête et sélectionnez coréen pour votre deuxième requête.

**Je ne vois pas l’icône de langue de requête pays/région pour sélectionner une langue pour les requêtes dans un jeu de révision. Comment puis-je spécifier un langage de requête dans une recherche de jeu de révision ?**

Pour les requêtes de jeu de révision, il n’est pas nécessaire de spécifier une langue de document. Advanced eDiscovery détecte automatiquement les langues de document lorsque vous ajoutez du contenu à un jeu de révision. Cela vous permet d’optimiser les résultats de votre requête dans un jeu de révision.

**Puis-je voir les langues détectées dans les [métadonnées de fichier](view-documents-in-review-set.md#file-metadata)?**

Non, vous ne pouvez pas voir les langues détectées dans les métadonnées de fichier.

**Puis-je filtrer par langue de document dans un jeu de révision**?

Non, vous ne pouvez pas filtrer, trier ou Rechercher par langue de document dans un jeu de révision.

**Cette version CJC pour les scénarios d’ensembles de révision aura-t-elle une incidence sur l’ensemble des recherches existantes et sur les ensembles de révision ?**

Non, aucune de vos recherches existantes et de vos ensembles de révision ne change. Vous n’avez pas besoin de réindexer les données existantes, et les résultats de recherche pour le texte anglais seront identiques.

**Comment puis-je modifier ma langue d’affichage pour le chinois, le japonais ou le coréen ?**

Pour plus d’informations sur la façon de modifier la langue d’affichage et le fuseau horaire, consultez [la rubrique relative à la définition des paramètres de langue et de région pour Office 365](https://docs.microsoft.com/office365/troubleshoot/access-management/set-language-and-region).

## <a name="known-issues"></a>Problèmes connus

- La reconnaissance optique de caractères ne prend pas en charge les caractères CJK des fichiers image

- Les fichiers de messagerie (par exemple, *. eml et *. MSG) dans les [Annotations](view-documents-in-review-set.md#annotate-view) ne sont pas pris en charge pour les langues CJK.

- La mise en surbrillance des recherches dans l' [affichage de texte](view-documents-in-review-set.md#text-view) n’est pas prise en charge pour les langues CJK.

- Le [module de pertinence](using-relevance.md) utilisé pour analyser les données ne prend pas en charge les langues CJK.

- Les [conservations basées sur une requête](managing-holds.md#manage-non-custodial-holds) ne sont pas prises en charge pour les langues CJK. 
