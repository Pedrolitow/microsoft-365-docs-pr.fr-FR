---
title: Prise en charge de CJK/Double Octet pour eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment Microsoft Purview eDiscovery (Premium) dans Microsoft 365 prend en charge les langues chinoise, japonaise et coréenne (CJC), qui utilisent un jeu de caractères sur deux octets.
ms.openlocfilehash: 6877e089f1faae21593a0f63336663540d04f470
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67820523"
---
# <a name="cjk-language-support-for-ediscovery-premium"></a>Prise en charge du langage CJC pour eDiscovery (Premium)

Microsoft Purview eDiscovery (Premium) prend en charge les langues de jeu de caractères sur deux octets (notamment le chinois simplifié, le chinois traditionnel, le japonais et le coréen, qui sont collectivement appelés langues *CJC*) pour les scénarios avancés suivants dans un ensemble de révisions :

- Lorsque vous [interrogez les données dans un jeu de révision](review-set-search.md).

- Lorsque vous [étiquetez des documents dans un ensemble de révisions](tagging-documents.md).

- Lorsque vous [analysez des données de cas dans un ensemble de révisions](analyzing-data-in-review-set.md) à l’aide de la détection en quasi-double, du thread de messagerie et de l’analytique des thèmes.

## <a name="frequently-asked-questions"></a>Foire aux questions

**Comment faire créer une recherche pour collecter des éléments qui contiennent des caractères CJC ?**

Vous pouvez utiliser des caractères CJK pour [les recherches de mots clés](building-search-queries.md#keyword-searches), [les requêtes de mots clés et les conditions de recherche](keyword-queries-and-search-conditions.md) lors de la recherche de contenu dans eDiscovery (Premium). La recherche de caractères CJC est également prise en charge lors de la recherche de contenu dans Microsoft Purview eDiscovery (Standard) et recherche de contenu.

Nous fournissons la prise en charge de CJK pour tous les [opérateurs de recherche](keyword-queries-and-search-conditions.md#search-operators) et [conditions de recherche](keyword-queries-and-search-conditions.md#search-conditions), y compris les opérateurs booléens **AND**, **OR**, **NOT** et **NEAR**.

Si vous êtes certain que les emplacements de contenu ou les éléments contiennent des caractères CJC, mais que les recherches ne renvoient aucun résultat, cliquez sur l’icône langue/région de la requête ![Icône langue-pays/région de la requête dans la recherche de contenu.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) et sélectionnez la valeur de code de culture langue-pays correspondante pour la recherche. La langue/région par défaut est neutre.

**Puis-je rechercher plusieurs langues à la fois ?**

Cela dépend de votre scénario de recherche.

- Lorsque vous [interrogez des données dans un ensemble de révisions](review-set-search.md) dans eDiscovery (Premium), vous pouvez rechercher plusieurs langues.

- Lorsque vous [créez une recherche pour collecter des données](create-draft-collection.md), créez des collections distinctes pour chaque langue que vous ciblez. Par exemple, si vous recherchez un document qui contient à la fois le chinois et le coréen, sélectionnez Le chinois pour votre première collection et le coréen pour votre deuxième collection.

**Je ne vois pas l’icône langue/région de la requête pour sélectionner une langue pour les requêtes dans un ensemble de révisions. Comment spécifier un langage de requête dans une recherche d’ensemble de révisions ?**

Pour passer en revue les requêtes définies, vous n’avez pas besoin de spécifier une langue de document. eDiscovery (Premium) détecte automatiquement les langues de document lorsque vous ajoutez du contenu à un ensemble de révisions. Cela vous permet d’optimiser les résultats de votre requête dans un ensemble de révisions.

**Puis-je voir les langues détectées dans les [métadonnées de fichier](view-documents-in-review-set.md#file-metadata) ?**

Non, vous ne pouvez pas voir les langues détectées dans les métadonnées de fichier.

**Puis-je filtrer par langue de document dans un ensemble de révisions** ?

Non, vous ne pouvez pas filtrer, trier ou rechercher par langues de document dans un ensemble de révisions.

**Cette version de cjk pour les scénarios d’ensemble de révision affectera-t-elle l’une de mes recherches et ensembles de révision existants ?**

Non, aucune de vos recherches et jeux de révision existants ne change. Vous n’avez pas besoin de réindexer les données existantes, et les résultats de la recherche de texte en anglais seront les mêmes.

**Comment faire changer ma langue d’affichage en chinois, japonais ou coréen ?**

Pour plus d’informations sur la modification de la langue d’affichage et du fuseau horaire, consultez [Comment définir les paramètres de langue et de région pour Office 365](/office365/troubleshoot/access-management/set-language-and-region).

## <a name="known-issues"></a>Problèmes connus

- OCR ne prend pas en charge les caractères CJC des fichiers image

- Email fichiers (tels que *.eml et *.msg) en [mode Annotation](view-documents-in-review-set.md#annotate-view) ne sont pas pris en charge pour les langages CJK.

- La mise en surbrillance des correspondances de recherche en [mode Texte](view-documents-in-review-set.md#text-view) n’est pas prise en charge pour les langues CJC.

- Le [module Pertinence](using-relevance.md) utilisé pour analyser les données ne prend pas en charge les langages CJC.

- [Les conservations basées sur des requêtes](managing-holds.md#manage-non-custodial-holds) ne sont pas prises en charge pour les langages CJK.