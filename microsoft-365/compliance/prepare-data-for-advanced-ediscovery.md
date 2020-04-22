---
title: Préparation des données pour Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
titleSuffix: Office 365
ms.date: 9/14/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 2fb94c23-1846-4a0e-994d-da6d02445f15
description: 'Découvrez comment utiliser le centre de &amp; sécurité conformité pour préparer les données à analyser avec Advanced eDiscovery. '
ms.openlocfilehash: edc92aeac0c76e64d1d2dcfd6ceae08d766b9397
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43626658"
---
# <a name="prepare-data-for-advanced-ediscovery-classic"></a>Préparation des données pour Advanced eDiscovery (classique)

Cette rubrique décrit comment charger les résultats d’une recherche de contenu dans dans un cas dans Advanced eDiscovery (classique). 
  
> [!IMPORTANT]
> À mesure que nous continuons à investir dans les versions plus récentes de Advanced eDiscovery, nous annonçaons le retrait de la fonctionnalité eDiscovery avancée, également appelée *Advanced eDiscovery (Classic)* ou *Advanced eDiscovery v 1.0*. Si vous utilisez Advanced eDiscovery v 1.0, veuillez faire la transition vers [Advanced eDiscovery v2.0](overview-ediscovery-20.md) (également connu sous le nom de *solution eDiscovery avancée dans Microsoft 365*) dès que possible. Advanced eDiscovery 2.0 contient des fonctionnalités similaires à celles de Advanced eDiscovery v1.0, et elle offre également de nombreuses fonctions inédites telles que la gestion des consignataires, la gestion des communications et les jeux à réviser. Pour en savoir plus sur le retrait d’Advanced eDiscovery v1.0, voir la [Suppression des outils hérités eDiscovery](legacy-ediscovery-retirement.md#advanced-ediscovery-v10).  
  
## <a name="step-1-prepare-data-for-advanced-ediscovery"></a>Étape 1 : préparer les données pour Advanced eDiscovery

Pour analyser les données avec Advanced eDiscovery, vous pouvez utiliser les résultats d’une recherche de contenu que vous exécutez dans le centre &amp; de sécurité conformité Microsoft 365 (qui se trouve sur la page **recherche** de &amp; contenu dans le centre de sécurité conformité de Microsoft 365) ou dans une recherche associée à un cas de &amp; découverte électronique (dans la page **eDiscovery** du centre de sécurité conformité). 
  
Pour obtenir la procédure détaillée sur la préparation des résultats de recherche pour analyse dans Advanced eDiscovery, reportez-vous à [Prepare Search Results for Advanced eDiscovery](prepare-search-results-for-advanced-ediscovery.md).
  
> [!NOTE]
> Si vous disposez de données en dehors de Microsoft 365 et que vous souhaitez les importer dans Microsoft 365 afin de pouvoir les préparer et les analyser dans Advanced eDiscovery, voir [Overview of Import PST Files to microsoft 365](https://support.office.com/article/ba688e0a-0fcb-4bd7-8e57-2b669564ea84) and [Archiving tiers Data](https://go.microsoft.com/fwlink/p/?linkid=716918). 
  
## <a name="step-2-load-search-result-data-in-to-a-case-in-advanced-ediscovery"></a>Étape 2 : chargement des données de résultats de recherche dans dans un cas dans Advanced eDiscovery

Une fois que vous avez préparé les résultats de &amp; la recherche dans le centre de sécurité conformité pour analyse, l’étape suivante consiste à charger les résultats de la recherche dans un cas dans Advanced eDiscovery. Pour plus d’informations, consultez [la rubrique exécuter le module de processus](run-the-process-module-in-advanced-ediscovery.md).
  
1. Accédez à [https://protection.office.com](https://protection.office.com).
    
2. Connectez-vous à l’aide de votre compte professionnel ou scolaire.
    
3. Dans le Centre de sécurité &amp; conformité, cliquez sur **Recherches &amp; enquêtes** \> **eDiscovery** pour afficher la liste des cas de votre organisation. 
    
4. Cliquez sur **ouvrir** en regard du cas dans lequel vous souhaitez charger les données dans Advanced eDiscovery. 
    
5. Sur la page **Accueil** du cas, cliquez sur **Advanced eDiscovery**. 
    
    ![Cliquez sur basculer vers Advanced eDiscovery pour ouvrir le cas dans Advanced eDiscovery](../media/8e34ba23-62e3-4e68-a530-b6ece39b54be.png)
  
    La barre **de progression de la connexion à Advanced eDiscovery** s’affiche. Lorsque vous êtes connecté à Advanced eDiscovery, une liste de conteneurs apparaît dans la page de configuration de l’incident. 
    
    ![Le cas est affiché dans Advanced eDiscovery](../media/8036e152-70dc-4bb7-9379-61c1ed8326b4.png)
  
     Ces conteneurs représentent les résultats de recherche que vous avez préparés pour l’analyse dans Advanced eDiscovery à l’étape 1. Notez que le nom du conteneur porte le même nom que la recherche de contenu dans le centre de sécurité &amp; conformité. Les conteneurs de la liste sont ceux que vous avez préparés. Si un autre utilisateur a préparé des résultats de recherche pour Advanced eDiscovery, les conteneurs correspondants ne seront pas inclus dans la liste. 
    
6. Pour charger les données de résultats de recherche à partir d’un conteneur dans le cas dans Advanced eDiscovery, sélectionnez un conteneur, puis cliquez sur **traiter**.
    
Une fois que les résultats de la &amp; recherche du centre de sécurité conformité sont ajoutés à l’incident dans Advanced eDiscovery, l’étape suivante consiste à utiliser les outils dans Advanced eDiscovery pour analyser et rechercher les données pertinentes pour le cas. 
  
## <a name="see-also"></a>Voir aussi

[Advanced eDiscovery (classique)](office-365-advanced-ediscovery.md)
  
[Configurer des utilisateurs et des cas](set-up-users-and-cases-in-advanced-ediscovery.md)
  
[Analyse des données d’un cas](analyze-case-data-with-advanced-ediscovery.md)
  
[Gestion de la configuration de la pertinence](manage-relevance-setup-in-advanced-ediscovery.md)
  
[Utilisation du module de pertinence](use-relevance-in-advanced-ediscovery.md)
  
[Exportation des données d’un cas](export-case-data-in-advanced-ediscovery.md)

