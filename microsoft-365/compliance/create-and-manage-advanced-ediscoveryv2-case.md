---
title: Créer et gérer des cas eDiscovery (Premium) dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-aed
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Cet article explique comment créer et gérer des cas Microsoft Purview eDiscovery (Premium). La première étape consiste à créer un cas et à commencer à utiliser les fonctionnalités et fonctionnalités eDiscovery (Premium).
ms.openlocfilehash: 585404a6ab7b3327f4b58dd011eb1f4ac6723b01
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67817684"
---
# <a name="create-and-manage-an-ediscovery-premium-case"></a>Créer et gérer un cas eDiscovery (Premium)

Après avoir configuré Microsoft Purview eDiscovery (Premium) et [affecté des autorisations aux responsables eDiscovery](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions) de votre organisation pour gérer les cas, l’étape suivante consiste à créer et gérer un cas.

Cet article fournit également une vue d’ensemble générale de l’utilisation des cas pour gérer le flux de travail eDiscovery (Premium) pour une affaire juridique ou d’autres types d’enquêtes.

## <a name="create-a-case"></a>Créer un cas

Effectuez les étapes suivantes pour créer un cas et ajouter des membres. L’utilisateur qui crée le cas est automatiquement ajouté en tant que membre. Les membres du cas peuvent accéder au cas dans le portail de conformité Microsoft Purview et effectuer des tâches eDiscovery (Premium).

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité</a> et connectez-vous à l’aide des informations d’identification du compte d’utilisateur qui a reçu des autorisations eDiscovery. Les membres du groupe de rôles Gestion de l’organisation peuvent également créer des cas eDiscovery (Premium).

2. Dans le volet de navigation gauche du portail de conformité, cliquez sur **Afficher tout**, puis sélectionnez **eDiscovery** > **Advanced**, puis sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2173764" target="_blank">l’onglet **Cas**</a>.

3. Sélectionnez **Créer un cas**.

4. Dans la page de menu volant **Nouveau cas eDiscovery** , donnez un nom (obligatoire) au cas, puis tapez un numéro de cas et une description facultatifs. Le nom du cas doit être unique dans votre organisation.

5. Cliquez sur **Enregistrer** pour créer le cas.

   Le nouveau cas est créé et l’onglet **Paramètres** du nouveau cas s’affiche.

6. Dans la vignette **Accès & autorisations** sous l’onglet **Paramètres** , cliquez sur **Sélectionner**.

7. Dans la page de menu volant **Gérer ce cas** , sous **Gérer les membres**, cliquez sur **Ajouter** pour ajouter des membres au cas.

8. Dans la liste des personnes, activez la case à cocher en regard des noms des personnes que vous souhaitez ajouter au cas. Comme expliqué précédemment, assurez-vous que les personnes que vous ajoutez au cas ont reçu les autorisations eDiscovery appropriées.

9. Une fois que vous avez sélectionné les personnes à ajouter en tant que membres du cas, cliquez sur **Ajouter**.

10. Dans la page de garde **Gérer ce cas**, cliquez sur **Enregistrer** pour enregistrer la nouvelle liste des membres de cas.

11. Cliquez sur l’onglet **Accueil** pour accéder à la page d’accueil du cas.

## <a name="manage-the-workflow"></a>Gérer le flux de travail

Pour commencer à utiliser eDiscovery (Premium), voici un flux de travail de base qui s’aligne sur les [pratiques courantes d’eDiscovery](advanced-ediscovery-edrm.md). Dans chacune de ces étapes, nous allons également mettre en évidence certaines fonctionnalités eDiscovery (Premium) étendues que vous pouvez explorer.

![Flux de travail eDiscovery (Premium).](../media/AeDWorkflow.png)

1. **[Ajoutez des consignatateurs et des](add-custodians-to-case.md) [sources de données non gardiennes](non-custodial-data-sources.md) au cas**. La première étape après la création d’un cas consiste à ajouter des consignatateurs. Un *gardien* est une personne ayant le contrôle administratif d’un document ou d’un fichier électronique qui peut être pertinent dans le cas. En outre, vous pouvez ajouter des sources de données qui ne sont pas associées à un utilisateur spécifique, mais qui peuvent être pertinentes pour le cas.

   Voici certaines choses qui se produisent (ou que vous pouvez faire) lorsque vous ajoutez des consignatateurs à un cas :

   - Les données de la boîte aux lettres Exchange du consignateur, du compte OneDrive et de tous les groupes Microsoft Teams ou Yammer dont le consignateur est membre peuvent être « marquées » comme données de garde dans le cas présent.
  
   - Les données de consignation sont réindexées (par un processus appelé *indexation avancée*). Cela permet d’optimiser sa recherche à l’étape suivante.
  
   - Vous pouvez placer une conservation sur les données des consignats. Cela préserve les données susceptibles d’être pertinentes pour le cas au cours de l’enquête.
  
   - Vous pouvez associer d’autres sources de données à un consignateur (par exemple, vous pouvez associer un site SharePoint ou un groupe Microsoft 365 à un consignateur) afin que ces données puissent être réindexées, mises en attente et recherchées, tout comme les données dans la boîte aux lettres ou le compte OneDrive du consignateur.

   - Vous pouvez utiliser le [flux de travail de communication](managing-custodian-communications.md) dans eDiscovery (Premium) pour envoyer une notification de conservation légale aux consignatateurs.

2. **[Collectez du contenu pertinent à partir de sources de données](create-draft-collection.md)**. Après avoir ajouté des consignatateurs et des sources de données non liées à la garde à un cas, utilisez l’outil de collecte intégré pour rechercher dans ces sources de données du contenu qui peut être pertinent pour le cas. Vous utilisez des mots clés, des propriétés et des conditions pour [créer des requêtes de recherche](building-search-queries.md) qui retournent des résultats de recherche avec les données les plus susceptibles d’être pertinentes pour le cas. Vous pouvez également :

   - Affichez [les statistiques de collection](collection-statistics-reports.md) qui peuvent vous aider à affiner une collection pour affiner les résultats.

   - Affichez un aperçu d’un échantillon de la collection pour vérifier rapidement si les données pertinentes sont trouvées.

   - Modifiez une requête et réexécutez la collection.

3. **[Validez la collecte dans un jeu de révisions](commit-draft-collection.md)**. Une fois que vous avez configuré et vérifié qu’une recherche retourne les données souhaitées, l’étape suivante consiste à ajouter les résultats de la recherche à un ensemble de révisions. Lorsque vous ajoutez des données à un jeu de révision, les éléments sont copiés à partir de leur emplacement d’origine vers un emplacement de stockage Azure sécurisé. Les données sont réindexées pour les optimiser pour des recherches approfondies et rapides lors de l’examen et de l’analyse des éléments du jeu de révision. En outre, vous pouvez également [ajouter des données non Office 365 dans un ensemble de révisions](load-non-office-365-data-into-a-review-set.md).

   Il existe également un type spécial d’ensemble de révision auquel vous pouvez ajouter des données, appelé ensemble de *révisions de conversation*. Ces types d’ensembles de révisions fournissent des fonctionnalités de reconstruction de conversation pour reconstruire, examiner et exporter des conversations thread comme celles de Microsoft Teams. Pour plus d’informations, consultez [La révision des conversations dans eDiscovery (Premium).](conversation-review-sets.md)

4. **Passez en revue et analysez les données d’un ensemble de révisions**. Maintenant que les données sont dans un ensemble de révisions, vous pouvez utiliser un large éventail d’outils et de fonctionnalités pour afficher et analyser les données de cas dans le but de réduire le jeu de données à ce qui est le plus pertinent pour le cas que vous examinez. Voici une liste de certains outils et fonctionnalités que vous pouvez utiliser pendant ce processus.

   - [Afficher les documents](view-documents-in-review-set.md). Cela inclut l’affichage des métadonnées de chaque document dans un ensemble de révisions et l’affichage du document dans sa version native ou sa version texte.

   - [Créez des requêtes et des filtres](review-set-search.md). Vous créez des requêtes de recherche à l’aide de différents critères de recherche (y compris la possibilité de rechercher toutes les [propriétés de métadonnées de fichier](document-metadata-fields-in-advanced-ediscovery.md) pour affiner et éliminer les données de cas en fonction de ce qui est le plus pertinent pour le cas. Vous pouvez également utiliser des filtres de jeu de révision pour appliquer rapidement d’autres conditions aux résultats d’une requête de recherche afin d’affiner ces résultats. 

   - [Créez et utilisez des balises](tagging-documents.md). Vous pouvez appliquer des balises aux documents d’un jeu de révision pour identifier ceux qui sont réactifs (ou non réactifs au cas), puis utiliser ces balises lors de la création de requêtes de recherche pour inclure ou exclure les documents étiquetés. Vous pouvez également marquer pour déterminer les documents à exporter.

   - [Annoter et répéter des documents](view-documents-in-review-set.md#annotate-view). Vous pouvez utiliser l’outil d’annotation dans une révision pour annoter des documents et rétablir le contenu des documents en tant que produit de travail. Nous générons une version PDF d’un document annoté ou redécoupé pendant l’examen afin de réduire le risque d’exportation de la version native non édictée du document.

   - [Analyser les données de cas](analyzing-data-in-review-set.md). Les fonctionnalités d’analytique dans eDiscovery (Premium) sont puissantes. Une fois que vous avez exécuté des analyses sur les données du jeu de révision, nous effectuons une analyse telle que la détection des doublons, le thread de messagerie et les thèmes qui peuvent aider à réduire le volume de documents que vous devez examiner. Nous générons également des rapports Analytics qui résument le résultat de l’exécution de l’analytique. Comme expliqué précédemment, l’exécution d’analytique exécute également [le modèle de détection des privilèges entre avocats et clients](attorney-privilege-detection.md#use-the-attorney-client-privilege-detection-model).

5. **Exporter et télécharger des données de cas**. Une dernière étape après la collecte, l’examen et l’analyse des données de cas consiste à les exporter à partir d’eDiscovery (Premium) pour examen externe ou pour examen par des personnes extérieures à l’équipe d’investigation. L’exportation de données est un processus en deux étapes. La première étape consiste à [exporter](export-documents-from-review-set.md) des données hors du jeu de révision et à les copier vers un autre emplacement de stockage Azure (un emplacement fourni par Microsoft ou un autre géré par votre organisation). Vous utilisez ensuite Explorateur Stockage Azure pour [télécharger](download-export-jobs.md) les données sur un ordinateur local. Outre les fichiers de données exportés, le package d’exportation contient également un rapport d’exportation, un rapport récapitulatif et un rapport d’erreur.

## <a name="ediscovery-premium-architecture"></a>Architecture eDiscovery (Premium)

Voici un diagramme d’architecture qui montre le flux de travail eDiscovery (Premium) de bout en bout dans un environnement géo unique et dans un environnement multigéographique, ainsi que le flux de données de bout en bout aligné sur le [modèle de référence de découverte électronique](overview-ediscovery-20.md#ediscovery-premium-alignment-with-the-electronic-discovery-reference-model).

[![Affiche du modèle : architecture eDiscovery (Premium) dans Microsoft 365.](../media/solutions-architecture-center/ediscovery-poster-thumb.png)](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Afficher en tant qu’image](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Télécharger en tant que fichier PDF](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.pdf)

[Télécharger en tant que fichier Visio](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.vsdx)
