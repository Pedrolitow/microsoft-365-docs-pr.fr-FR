---
title: Introduction aux stratégies de gestion des informations
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 5/16/2014
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- WSU150
- SPO160
- OSU150
- MET150
ms.assetid: 63a0b501-ba59-44b7-a35c-999f3be057b2
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment utiliser des stratégies de gestion des informations pour contrôler et suivre des éléments tels que la durée de conservation du contenu ou les actions que les utilisateurs peuvent entreprendre avec ce contenu.
ms.openlocfilehash: 98eae2a08aa246a1f0ebe7d037103a82c132d060
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67680480"
---
# <a name="introduction-to-information-management-policies"></a>Introduction aux stratégies de gestion des informations

Une stratégie de gestion des informations constitue un ensemble de règles pour un type de contenu. Les stratégies de gestion des informations permettent aux organisations de contrôler et de suivre des événements tels que la durée de rétention des contenus ou les actions que les utilisateurs sont autorisés à effectuer sur ces contenus. Les stratégies de gestion des informations peuvent aider les organisations à se conformer aux réglementations légales ou administratives, ou elles peuvent simplement appliquer les processus d’entreprise internes. 
  
Par exemple, une organisation qui doit respecter les réglementations gouvernementales exigeant qu’elle démontre des « contrôles adéquats » de ses états financiers peut créer une ou plusieurs stratégies de gestion de l’information qui auditent des actions spécifiques dans le processus de création et d’approbation de tous les documents liés aux dépôts financiers.
  
Pour plus d’informations, consultez [Créer et appliquer des stratégies de gestion des informations](create-info-mgmt-policies.md).
  
## <a name="features-of-information-management-policies"></a>Fonctionnalités des stratégies de gestion des informations
<a name="__top"> </a>

Il existe quatre catégories de base de fonctionnalités de stratégie prédéfinies que les organisations peuvent utiliser individuellement ou en combinaison pour gérer le contenu et les processus. 
  
![Types de stratégies de contenu.](../media/19fcb8a3-974b-40d3-a13f-b76088d122f8.png)
  
La fonctionnalité de stratégie d’audit permet aux organisations d’analyser comment leurs systèmes de gestion de contenu sont utilisés par la journalisation des événements et des opérations effectués sur des documents et des éléments de liste. Vous pouvez configurer la fonctionnalité de stratégie d’audit pour journaliser des événements tels que la modification, l’affichage, l’archivage, l’extraction, la suppression ou la modification des autorisations d’un document ou d’un élément. Toutes les informations d’audit sont stockées dans un journal d’audit unique sur le serveur, et les administrateurs de site peuvent y exécuter des rapports. 
  
La fonctionnalité de stratégie d’expiration permet aux organisations de supprimer ou de supprimer du contenu obsolète de leurs sites de manière cohérente et traçable. Cela vous permet de gérer les coûts et les risques associés à la conservation du contenu obsolète. Vous pouvez configurer une stratégie d’expiration pour spécifier que certains types de contenu expirent à une date particulière ou dans un délai après la création ou la dernière modification du document.
  
Les organisations peuvent également créer et déployer des fonctionnalités de stratégie personnalisées afin de répondre à des besoins spécifiques. Par exemple, une organisation de fabrication peut vouloir définir une stratégie de gestion des informations pour tous les projets de documents de spécification de conception de produits qui empêchent les utilisateurs d’imprimer des copies de ces documents sur des imprimantes non sécurisées. Pour définir ce type de stratégie de gestion des informations, vous pouvez créer et déployer une fonctionnalité de stratégie de restriction d’impression qui peut être ajoutée à la stratégie de gestion des informations pertinente pour le type de contenu de spécification de conception de produit.
  
## <a name="locations-to-use-an-information-management-policy"></a>Emplacements pour utiliser une stratégie de gestion des informations
<a name="__toc340213528"> </a>

Pour implémenter une stratégie de gestion des informations, vous devez l’ajouter à une liste, une bibliothèque ou un type de contenu dans un site. L’emplacement où vous créez ou ajoutez une stratégie de gestion des informations affecte l’étendue de l’application de la stratégie ou l’étendue de son utilisation. Vous pouvez :
  
 **Créer une stratégie de collection de sites, puis ajouter cette stratégie à un type de contenu, une liste ou une bibliothèque** Vous pouvez créer une stratégie de collection de sites dans la liste Stratégies du site de niveau supérieur d’une collection de sites. Après avoir créé une stratégie de collection de sites, vous pouvez l’exporter afin que les administrateurs d’autres collections de sites puissent l’importer dans leur liste stratégies. La création d’une stratégie de collecte de sites exportable vous permet de normaliser les stratégies de gestion des informations sur les sites de votre organisation. 
  
Lorsque vous ajoutez une stratégie de collection de sites à un type de contenu de site et qu’une instance de ce type de contenu de site est ajoutée à une liste ou une bibliothèque, le propriétaire de cette liste ou bibliothèque ne peut pas modifier la stratégie de collection de sites pour la liste ou la bibliothèque. L’ajout d’une stratégie de collection de sites à un type de contenu de site est un bon moyen de s’assurer que les stratégies de collection de sites sont appliquées à chaque niveau de votre hiérarchie de sites.
  
![Lien du modèle de stratégie de type de contenu sur la page Paramètres du site.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)
  
 **Créer une stratégie de gestion des informations pour un type de contenu de site dans la galerie de types de contenu de site de niveau supérieur, puis ajouter ce type de contenu à une ou plusieurs listes ou bibliothèques** Vous pouvez également créer une stratégie de gestion des informations directement pour un type de contenu de site, puis associer une instance de ce type de contenu de site à plusieurs listes ou bibliothèques. Si vous créez une stratégie de gestion des informations de cette façon, chaque élément de la collection de sites de ce type de contenu ou d’un type de contenu qui hérite de ce type de contenu a la stratégie. Toutefois, si vous créez une stratégie de gestion des informations directement pour un type de contenu de site, il est plus difficile de réutiliser cette stratégie de gestion des informations dans d’autres collections de sites, car les stratégies créées de cette façon ne peuvent pas être exportées. 
  
![Lien types de contenu de site sur la page Paramètres du site.](../media/6f6fa51f-15d7-4782-b06f-a7b36e874cd3.png)
  
![Lien de stratégie de gestion des informations sur la page paramètres d’un type de contenu de site.](../media/15d83a34-6c8f-4b6e-b6ee-e9b0a70cbb4b.png)
  
Remarque Pour contrôler les stratégies utilisées dans une collection de sites, les administrateurs de collection de sites peuvent désactiver la possibilité de définir des fonctionnalités de stratégie directement sur un type de contenu. Lorsque cette restriction est en vigueur, les utilisateurs qui créent des types de contenu sont limités à la sélection de stratégies dans la liste des stratégies de collection de sites.
  
 **Créer une stratégie de gestion des informations pour une liste ou une bibliothèque** Si votre organisation doit appliquer une stratégie de gestion des informations spécifique à un ensemble très limité de contenu, vous pouvez créer une stratégie de gestion des informations qui s’applique uniquement à une liste ou bibliothèque individuelle. Cette méthode de création d’une stratégie de gestion des informations est la moins flexible, car elle ne s’applique qu’à un seul emplacement et ne peut pas être exportée ou réutilisée pour d’autres emplacements. Toutefois, vous devrez parfois créer des stratégies de gestion des informations uniques avec une applicabilité limitée pour résoudre des situations spécifiques. 
  
![Lien des stratégies de gestion des informations sur la page paramètres de la bibliothèque de documents.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)
  
Remarques 
  
Vous pouvez créer une stratégie de gestion des informations pour une liste ou une bibliothèque uniquement si cette liste ou cette bibliothèque ne prend pas en charge plusieurs types de contenu. Si une liste ou une bibliothèque prend en charge plusieurs types de contenu, vous devez définir une stratégie de gestion des informations pour chaque type de contenu de liste associé à cette liste ou bibliothèque. (Les instances d’un type de contenu de site associées à une liste ou bibliothèque spécifique sont appelées types de contenu de liste.)
  
Pour contrôler les stratégies utilisées dans une collection de sites, les administrateurs de collection de sites peuvent désactiver la possibilité de définir des fonctionnalités de stratégie directement sur une liste ou une bibliothèque. Lorsque cette restriction est appliquée, les utilisateurs qui gèrent des listes ou des bibliothèques sont limités à la sélection de stratégies dans la liste des stratégies de collection de sites.
  
[Une stratégie de gestion des informations est un ensemble de règles pour un type de contenu. Les stratégies de gestion des informations permettent aux organisations de contrôler et de suivre des éléments tels que la durée de conservation du contenu ou les actions que les utilisateurs peuvent entreprendre avec ce contenu. Les stratégies de gestion de l’information peuvent aider les organisations à se conformer aux réglementations légales ou gouvernementales, ou elles peuvent simplement appliquer des processus métier internes. Par exemple, une organisation qui doit respecter les réglementations gouvernementales exigeant qu’elle démontre des « contrôles adéquats » de ses états financiers peut créer une ou plusieurs stratégies de gestion de l’information qui auditent des actions spécifiques dans le processus de création et d’approbation de tous les documents liés aux dépôts financiers. Pour plus d’informations, consultez Créer et appliquer des stratégies de gestion des informations.](intro-to-info-mgmt-policies.md#__top)
  

