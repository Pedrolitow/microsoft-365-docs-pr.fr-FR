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
localization_priority: Normal
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
description: Découvrez comment utiliser des stratégies de gestion des informations pour contrôler et suivre des éléments tels que la durée de rétention du contenu ou les actions que les utilisateurs peuvent prendre avec ce contenu.
ms.openlocfilehash: fc3bfe1c0da54ccf4cb2c59589647cb396a5081e
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58567423"
---
# <a name="introduction-to-information-management-policies"></a>Introduction aux stratégies de gestion des informations

Une stratégie de gestion des informations constitue un ensemble de règles pour un type de contenu. Les stratégies de gestion des informations permettent aux organisations de contrôler et de suivre des événements tels que la durée de rétention des contenus ou les actions que les utilisateurs sont autorisés à effectuer sur ces contenus. Les stratégies de gestion des informations peuvent aider les organisations à se conformer aux réglementations légales ou administratives, ou elles peuvent simplement appliquer les processus d’entreprise internes. 
  
Par exemple, une organisation qui doit respecter les réglementations gouvernementales exigeant qu’elle démontre des « contrôles adéquats » de ses états financiers peut créer une ou plusieurs stratégies de gestion des informations qui auditent des actions spécifiques dans le processus de création et d’approbation pour tous les documents liés aux classements financiers.
  
Pour plus d’informations sur les procédures, voir [Créer et appliquer des stratégies de gestion des informations.](create-info-mgmt-policies.md)
  
## <a name="features-of-information-management-policies"></a>Fonctionnalités des stratégies de gestion des informations
<a name="__top"> </a>

Il existe quatre catégories de base de fonctionnalités de stratégie prédéfines que les organisations peuvent utiliser individuellement ou ensemble pour gérer le contenu et les processus. 
  
![Types de stratégies de contenu.](../media/19fcb8a3-974b-40d3-a13f-b76088d122f8.png)
  
La fonctionnalité de stratégie Audit permet aux organisations d’analyser l’utilisation de leurs systèmes de gestion de contenu par la journalisation des événements et des opérations effectuées sur les documents et les éléments de liste. Vous pouvez configurer la fonctionnalité de stratégie d’audit pour journaliser les événements tels que la modification, l’affichage, l’audit, l’extrait, la suppression ou la modification des autorisations d’un document ou d’un élément. Toutes les informations d’audit sont stockées dans un journal d’audit unique sur le serveur, et les administrateurs de site peuvent y exécuter des rapports. 
  
La fonctionnalité de stratégie d’expiration permet aux organisations de supprimer du contenu périmé de leurs sites de manière cohérente et accessible. Cela vous permet de gérer à la fois le coût et le risque associés à la rétention de contenu à jour. Vous pouvez configurer une stratégie d’expiration pour spécifier que certains types de contenu expirent à une date donnée ou dans un délai après la création ou la dernière modification du document.
  
Les organisations peuvent également créer et déployer des fonctionnalités de stratégie personnalisées afin de répondre à des besoins spécifiques. Par exemple, une organisation de fabrication peut définir une stratégie de gestion des informations pour tous les documents de spécification de conception de produit provisoires qui empêchent les utilisateurs d’imprimer des copies de ces documents sur des imprimantes non confidentielles. Pour définir ce type de stratégie de gestion des informations, vous pouvez créer et déployer une fonctionnalité de stratégie de restriction d’impression qui peut être ajoutée à la stratégie de gestion des informations pertinente pour le type de contenu de spécification de conception de produit.
  
## <a name="locations-to-use-an-information-management-policy"></a>Emplacements d’utilisation d’une stratégie de gestion des informations
<a name="__toc340213528"> </a>

Pour implémenter une stratégie de gestion des informations, vous devez l’ajouter à une liste, une bibliothèque ou un type de contenu dans un site. L’emplacement où vous créez ou ajoutez une stratégie de gestion des informations affecte l’étendue de la stratégie ou la portée de son utilisation. Vous pouvez :
  
 **Créer une stratégie de collection de sites, puis ajouter cette stratégie à un type de contenu, une liste ou une bibliothèque** Vous pouvez créer une stratégie de collection de sites dans la liste Stratégies dans le site de niveau supérieur d’une collection de sites. Après avoir créé une stratégie de collection de sites, vous pouvez l’exporter afin que les administrateurs d’autres collections de sites peuvent l’importer dans leur liste Stratégies. La création d’une stratégie de collection de sites exportable vous permet de normaliser les stratégies de gestion des informations sur les sites de votre organisation. 
  
Lorsque vous ajoutez une stratégie de collection de sites à un type de contenu de site et qu’une instance de ce type de contenu de site est ajoutée à une liste ou une bibliothèque, le propriétaire de cette liste ou bibliothèque ne peut pas modifier la stratégie de collection de sites pour la liste ou la bibliothèque. L’ajout d’une stratégie de collection de sites à un type de contenu de site est un bon moyen de s’assurer que les stratégies de collection de sites sont appliquées à chaque niveau de votre hiérarchie de sites.
  
![Lien Modèle de stratégie de type de contenu sur la page Paramètres site.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)
  
 **Créer une stratégie** de gestion des informations pour un type de contenu de site dans la galerie de types de contenu de site du site de niveau supérieur, puis ajouter ce type de contenu à une ou plusieurs listes ou bibliothèques Vous pouvez également créer une stratégie de gestion des informations directement pour un type de contenu de site, puis associer une instance de ce type de contenu de site à plusieurs listes ou bibliothèques. Si vous créez une stratégie de gestion des informations de cette façon, chaque élément de la collection de sites de ce type de contenu ou un type de contenu qui hérite de ce type de contenu possède la stratégie. Toutefois, si vous créez une stratégie de gestion des informations directement pour un type de contenu de site, il est plus difficile de réutiliser cette stratégie de gestion des informations dans d’autres collections de sites, car les stratégies créées de cette façon ne peuvent pas être exportées. 
  
![Lien types de contenu de site sur la page Paramètres site.](../media/6f6fa51f-15d7-4782-b06f-a7b36e874cd3.png)
  
![Lien de stratégie de gestion des informations sur la page des paramètres pour un type de contenu de site.](../media/15d83a34-6c8f-4b6e-b6ee-e9b0a70cbb4b.png)
  
Remarque : pour contrôler les stratégies utilisées dans une collection de sites, les administrateurs de collections de sites peuvent désactiver la possibilité de définir des fonctionnalités de stratégie directement sur un type de contenu. Lorsque cette restriction est en vigueur, les utilisateurs qui créent des types de contenu sont limités à sélectionner des stratégies dans la liste Stratégies de collection de sites.
  
 **Créer une stratégie de gestion des informations pour une liste ou une bibliothèque** Si votre organisation doit appliquer une stratégie de gestion des informations spécifique à un ensemble de contenu très limité, vous pouvez créer une stratégie de gestion des informations qui s’applique uniquement à une liste ou bibliothèque individuelle. Cette méthode de création d’une stratégie de gestion des informations est la moins flexible, car elle ne s’applique qu’à un seul emplacement et ne peut pas être exportée ou réutilisée pour d’autres emplacements. Toutefois, il peut parfois être nécessaire de créer des stratégies de gestion des informations uniques avec une applicabilité limitée pour résoudre des situations spécifiques. 
  
![Lien des stratégies de gestion des informations sur la page paramètres de la bibliothèque de documents.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)
  
Notes 
  
Vous pouvez créer une stratégie de gestion des informations pour une liste ou une bibliothèque uniquement si cette liste ou bibliothèque ne prend pas en charge plusieurs types de contenu. Si une liste ou une bibliothèque prend en charge plusieurs types de contenu, vous devez définir une stratégie de gestion des informations pour chaque type de contenu de liste associé à cette liste ou bibliothèque. (Les instances d’un type de contenu de site associées à une liste ou bibliothèque spécifique sont appelées types de contenu de liste.)
  
Pour contrôler les stratégies utilisées dans une collection de sites, les administrateurs de collections de sites peuvent désactiver la possibilité de définir des fonctionnalités de stratégie directement sur une liste ou une bibliothèque. Lorsque cette restriction est en vigueur, les utilisateurs qui gèrent des listes ou des bibliothèques sont limités à sélectionner des stratégies dans la liste Stratégies de collection de sites.
  
[Une stratégie de gestion des informations est un ensemble de règles pour un type de contenu. Les stratégies de gestion des informations permettent aux organisations de contrôler et de suivre des éléments tels que la durée de rétention du contenu ou les actions que les utilisateurs peuvent prendre avec ce contenu. Les stratégies de gestion des informations peuvent aider les organisations à se conformer aux réglementations légales ou gouvernementales, ou simplement à appliquer des processus d’entreprise internes. Par exemple, une organisation qui doit respecter les réglementations gouvernementales exigeant qu’elle démontre des « contrôles adéquats » de ses états financiers peut créer une ou plusieurs stratégies de gestion des informations qui auditent des actions spécifiques dans le processus de création et d’approbation pour tous les documents liés aux classements financiers. Pour plus d’informations sur les procédures, voir Créer et appliquer des stratégies de gestion des informations.](intro-to-info-mgmt-policies.md#__top)
  

