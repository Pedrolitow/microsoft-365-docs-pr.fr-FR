---
title: Prise en main de Advanced eDiscovery dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-aed
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Cet article explique comment commencer à utiliser Advanced eDiscovery dans Microsoft 365. Une fois que vous avez effectué quelques étapes rapides, l’outil eDiscovery avancé est prêt à être utilisé. La première étape consiste à créer un cas, puis à commencer à utiliser les fonctionnalités avancées de découverte électronique.
ms.openlocfilehash: 59537499ed52f44a9d32b8921fd297c5cd7c0d3f
ms.sourcegitcommit: dab50e1cc5bba920720b80033c93457f5ca1c330
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "48944332"
---
# <a name="get-started-with-advanced-ediscovery"></a>Prise en main Advanced eDiscovery

Advanced eDiscovery dans Microsoft 365 fournit un [flux de travail de bout en bout](overview-ediscovery-20.md#advanced-ediscovery-architecture) pour conserver, collecter, examiner, analyser et exporter les données qui répondent aux investigations internes et externes de votre organisation. Rien n’est nécessaire pour déployer Advanced eDiscovery, mais il existe des tâches préalables à effectuer par un administrateur informatique et un gestionnaire eDiscovery pour que votre organisation puisse commencer à créer et à utiliser des cas avancés de découverte électronique pour gérer vos recherches.

Cet article décrit les étapes nécessaires pour configurer Advanced eDiscovery. Cela inclut la garantie de la bonne licence requise pour accéder à Advanced eDiscovery et ajouter des dépositaires aux incidents, ainsi que l’attribution d’autorisations à vos équipes juridiques et d’enquête afin qu’ils puissent accéder aux incidents et les gérer. Cet article fournit également une vue d’ensemble de l’utilisation des cas pour gérer le flux de travail eDiscovery avancé pour une enquête légale.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Étape 1 : vérifier et affecter les licences appropriées

La gestion des licences pour Advanced eDiscovery nécessite l’abonnement de l’organisation et la gestion des licences par utilisateur appropriés.

- **Abonnement à l’Organisation :** Pour accéder à Advanced eDiscovery dans le centre de conformité Microsoft 365 ou le centre de sécurité & conformité, votre organisation doit avoir l’un des éléments suivants :

  - Abonnement Microsoft 365 E5 ou Office 365 E5
  
  - Abonnement Microsoft 365 E3 avec le module complémentaire E5 conformité

  - Microsoft 365 E3 subscription avec E5 eDiscovery and audit Add-on

  Si vous ne disposez pas d’un plan Microsoft 365 E5 existant et que vous souhaitez essayer Advanced eDiscovery, vous pouvez [Ajouter microsoft 365](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou [vous inscrire pour obtenir une version d’évaluation](https://www.microsoft.com/microsoft-365/enterprise) de Microsoft 365 E5.

- Gestion **des licences par utilisateur :** Pour ajouter un utilisateur en tant que dépositaire dans un cas de découverte électronique anticipée, l’utilisateur doit disposer de l’une des licences suivantes, en fonction de l’abonnement de votre organisation :

  - Microsoft 365 : les utilisateurs doivent disposer d’une licence Microsoft 365 E5, d’une licence de module complémentaire de conformité E5 ou d’une licence de module complémentaire de découverte électronique E5 E5.

  - Office 365 : une licence Office 365 E5 doit être affectée aux utilisateurs.

   Pour plus d’informations sur l’attribution des licences, voir [attribuer des licences à des utilisateurs](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).

> [!NOTE]
> Les utilisateurs ont uniquement besoin d’une licence E5 (ou la licence de module complémentaire appropriée) pour être ajoutés en tant que dépositaires à un cas avancé de découverte électronique avancée. Les administrateurs informatiques, les gestionnaires eDiscovery, les avocats, les parajuridiquess ou les enquêteurs qui utilisent la découverte électronique avancée pour gérer les incidents et vérifier les données des cas n’ont pas besoin d’une licence E5 ou de complément.

## <a name="step-2-assign-ediscovery-permissions"></a>Étape 2 : attribuer des autorisations eDiscovery

Pour accéder à la découverte électronique avancée ou ajoutée en tant que membre d’un cas avancé de découverte électronique, un utilisateur doit disposer des autorisations appropriées. Plus précisément, un utilisateur doit être ajouté en tant que membre du groupe de rôles gestionnaire de découverte électronique dans le centre de sécurité & conformité. Les membres de ce groupe de rôles peuvent créer et gérer des cas de découverte électronique avancée. Ils peuvent ajouter et supprimer des membres, placer des dépositaires et des emplacements de contenu en conservation, gérer des notifications de conservation légale, créer et modifier des recherches associées à un cas, ajouter des résultats de recherche à un jeu de réexamen, analyser des données dans un jeu de vérification, exporter et télécharger à partir d’un cas avancé de découverte électronique.

Procédez comme suit pour ajouter des utilisateurs au groupe de rôles gestionnaire eDiscovery :

1. Accédez à [https://protection.office.com/permissions](https://protection.office.com/permissions) et connectez-vous à l’aide des informations d’identification d’un compte d’administrateur de votre organisation Microsoft 365.

2. Sur la page **autorisations** , sélectionnez le groupe de rôles **Gestionnaire de découverte électronique** .

3. Sur la page de menu volant du gestionnaire eDiscovery, cliquez sur **modifier** en regard de la section **Gestionnaire eDiscovery** .

4. Dans la page **choisir le gestionnaire eDiscovery** dans l’Assistant modifier le groupe de rôles, cliquez sur **choisir le gestionnaire de découverte**.

5. Cliquez sur **Ajouter** , puis activez la case à cocher de tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Cliquez sur **Ajouter** pour ajouter les utilisateurs sélectionnés, puis sur **Terminer**.

7. Cliquez sur **Enregistrer** pour ajouter les utilisateurs au groupe de rôles, puis cliquez sur **Fermer** pour terminer l’étape.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Plus d’informations sur le groupe de rôles gestionnaire eDiscovery

Il existe deux sous-groupes dans le groupe de rôles gestionnaire de découverte électronique. Ces sous-groupes ont différents rôles.

- **Gestionnaire eDiscovery :** Permet d’afficher et de gérer les cas avancés eDiscovery qu’ils créent ou dont ils sont membres. Si un autre gestionnaire eDiscovery crée un cas mais n’ajoute pas de deuxième gestionnaire eDiscovery en tant que membre de ce dernier, le deuxième gestionnaire eDiscovery ne pourra pas afficher ou ouvrir le cas dans la page Advanced eDiscovery du centre de conformité. En règle générale, la plupart des utilisateurs de votre organisation peuvent être ajoutés au sous-groupe gestionnaire eDiscovery.

- **administrateur eDiscovery :** Peut effectuer toutes les tâches de gestion des dossiers qu’un gestionnaire eDiscovery peut effectuer. De plus, un administrateur de découverte électronique peut :

  - Afficher tous les cas répertoriés sur la page Advanced eDiscovery.
  
  - Gérer tous les cas au sein l’organisation après s’être ajouté en tant que membre du cas.

  - Accéder et exporter des données de cas pour tout cas au sein de l’organisation.

  En raison de l’étendue de l’accès, une organisation ne doit avoir que quelques administrateurs membres du sous-groupe administrateurs eDiscovery.

Pour plus d’informations sur les autorisations de découverte électronique, ainsi qu’une description de chaque rôle affecté au groupe de rôles gestionnaire de découverte électronique, consultez la rubrique [attribution d’autorisations eDiscovery](assign-ediscovery-permissions.md).

## <a name="step-3-configure-global-settings-for-advanced-ediscovery"></a>Étape 3 : configurer les paramètres globaux pour Advanced eDiscovery

La dernière étape à effectuer avant que les personnes de votre organisation commencent à créer et à utiliser des cas, la configuration des paramètres globaux qui s’appliquent à tous les cas de votre organisation. Pour l’instant, le seul paramètre global est *avocat-détection des privilèges client* (des paramètres globaux seront disponibles prochainement). Ce paramètre permet au modèle de privilège avocat-client de s’exécuter lorsque vous analysez les données d’un jeu de révision. Le modèle utilise l’apprentissage automatique d’ordinateur pour déterminer si un document contient du contenu juridique. Il compare également les participants des documents avec une liste de juristes (que vous envoyez lors de la configuration du modèle) afin de déterminer si un document a au moins un participant qui est un avocat.

Pour plus d’informations sur la configuration et l’utilisation du modèle de détection des privilèges du client avocat, voir [set up avocat-client privilege detection in Advanced eDiscovery](attorney-privilege-detection.md).

> [!NOTE]
> Il s’agit d’une étape facultative que vous pouvez effectuer à tout moment. Ne pas implémenter le modèle de détection des privilèges du client avocat ne vous empêche pas de créer et d’utiliser des cas avancés de découverte électronique.

## <a name="step-4-create-an-advanced-ediscovery-case"></a>Étape 4 : créer un cas eDiscovery avancé

L’étape suivante consiste à créer un cas et à commencer à utiliser Advanced eDiscovery. Procédez comme suit pour créer un cas et ajouter des membres. L’utilisateur qui crée le cas est automatiquement ajouté en tant que membre.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) et connectez-vous à l’aide des informations d’identification du compte d’utilisateur auquel ont été attribuées les autorisations eDiscovery appropriées. Les membres du groupe de rôles gestion de l’organisation peuvent également créer des cas avancés eDiscovery.

2. Dans le volet de navigation gauche du centre de conformité Microsoft 365, cliquez sur **Tout afficher** , puis cliquez sur **eDiscovery >avancée**.

3. Sur la page **découverte électronique avancée** , cliquez sur l’onglet **incidents** , puis cliquez sur **créer un cas**.

4. Sur la page de la nouvelle boîte de réception de **cas eDiscovery** , attribuez un nom (obligatoire) à la demande, puis tapez un numéro de cas et une description facultatifs. Le nom du cas doit être unique dans votre organisation.

5. Cliquez sur **Enregistrer** pour créer le cas.

   Le nouvel incident est créé et l’onglet **paramètres** dans le nouvel incident s’affiche. 

6. Dans la vignette **accès & autorisations** sous l’onglet **paramètres** , cliquez sur **Sélectionner** , puis sur **mettre à jour**.

7. Cliquez sur **Mise à jour**.

8. Sur la page de menu contextuel **gérer ce cas** , sous **gérer les membres** , cliquez sur **Ajouter** pour ajouter des membres à la demande de devis.

9. Dans la liste des personnes, activez la case à cocher en regard des noms des personnes que vous souhaitez ajouter à la demande de devis. Comme indiqué précédemment, assurez-vous que les personnes que vous ajoutez au cas ont reçu les autorisations eDiscovery appropriées.

10. Une fois que vous avez sélectionné les personnes à ajouter en tant que membres de la demande, cliquez sur **Ajouter**.

11. Dans la page de garde **Gérer ce cas** , cliquez sur **Enregistrer** pour enregistrer la nouvelle liste des membres de cas.

12. Cliquez sur l’onglet **Accueil** pour accéder à la page d’accueil du dossier.

## <a name="explore-the-advanced-ediscovery-workflow"></a>Explorer le flux de travail eDiscovery avancé

Pour commencer à utiliser Advanced eDiscovery, voici un flux de travail simple qui s’aligne sur les [pratiques eDiscovery courantes](overview-ediscovery-20.md#alignment-with-edrm). Dans chacune de ces étapes, nous allons également mettre en évidence certaines fonctionnalités avancées avancées de découverte électronique que vous pouvez explorer.

![Flux de travail eDiscovery avancé](../media/AeDWorkflow.png)

1. **[Ajouter des dépositaires à un cas](add-custodians-to-case.md)**. La première étape après la création d’un cas consiste à ajouter des dépositaires. Un *dépositaire* est une personne ayant le contrôle administratif d’un document ou d’un fichier électronique qui peut être pertinent pour le cas. Voici quelques éléments qui se produisent (ou que vous pouvez faire) lorsque vous ajoutez des dépositaires à un cas :

   - Les données de la boîte aux lettres Exchange du dépositaire, le compte OneDrive et tous les groupes Microsoft teams ou Yammer dont le dépositaire est membre peuvent être « marquées » comme étant des données privatives dans le cas.
  
   - Les données des dépositaires sont réindexées (par un processus appelé *indexation avancée* ). Cela permet d’optimiser la recherche dans l’étape suivante.
  
   - Vous pouvez placer un blocage sur les données des dépositaires. Cela permet de conserver les données qui peuvent être pertinentes pour le cas lors de l’enquête.
  
   - Vous pouvez associer d’autres sources de données à un dépositaire (par exemple, vous pouvez associer un site SharePoint ou un groupe Microsoft 365 à un dépositaire) afin que ces données puissent être réindexées, mises en attente et recherchées, de la même manière que les données de la boîte aux lettres ou du compte OneDrive du dépositaire.

   - Vous pouvez utiliser le [flux de travail de communication](managing-custodian-communications.md) dans Advanced eDiscovery pour envoyer une notification de suspension légale aux dépositaires.

2. **[Recherchez des sources de données privatives de Troie pour les données pertinentes pour le cas](collecting-data-for-ediscovery.md)**. Une fois que vous avez ajouté des dépositaires à un cas, utilisez l’outil de recherche intégré pour rechercher des données susceptibles de concerner les emplacements de données des dépositaires. Vous utilisez des mots clés, des propriétés et des conditions pour [créer des requêtes de recherche](building-search-queries.md) qui renvoient des résultats de recherche avec les données les plus pertinentes pour le cas. Vous pouvez également :

   - Afficher les [statistiques de recherche](search-statistics.md) qui peuvent vous aider à affiner une requête de recherche pour affiner les résultats.

   - Affichez un aperçu des résultats de la recherche pour vérifier rapidement si les données pertinentes sont trouvées.

   - Réviser une requête et relancer la recherche.

3. **[Ajouter des données à un ensemble de révision](add-data-to-review-set.md)**. Une fois que vous avez configuré et vérifié qu’une recherche renvoie les données souhaitées, l’étape suivante consiste à ajouter les résultats de la recherche à un jeu de révision. Lorsque vous ajoutez des données à un ensemble de vérification, les éléments sont copiés de leur emplacement d’origine vers un emplacement de stockage Azure sécurisé. Les données sont réindexées pour les optimiser pour les recherches rapides et rapides lors de l’examen et de l’analyse des éléments de l’ensemble de révision. En outre, vous pouvez également [Ajouter des données non-Office 365 dans un jeu de révision](load-non-office-365-data-into-a-review-set.md).

   Il existe également un type particulier de jeu d’analyse auquel vous pouvez ajouter des données, appelé « *révision de conversation* ». Ces types d’ensembles de révisions fournissent des fonctionnalités de reconstruction de conversation pour reconstruire, examiner et exporter des conversations thématiques comme celles de Microsoft Teams. Pour plus d’informations, consultez la rubrique [Review conversations in Advanced eDiscovery](conversation-review-sets.md).

4. **Examinez et analysez les données dans un jeu de révision**. À présent que les données se trouvent dans un ensemble de révision, vous pouvez utiliser un large éventail d’outils et de fonctionnalités pour afficher et analyser les données de cas afin de réduire la quantité de données la plus pertinente pour le cas que vous étudiez. Voici une liste de certains outils et fonctionnalités que vous pouvez utiliser pendant ce processus.

   - [Afficher des documents](view-documents-in-review-set.md). Cela inclut l’affichage des métadonnées pour chaque document dans un jeu de révision et l’affichage du document dans sa version native ou sa version textuelle.

   - [Créez des requêtes et des filtres](review-set-search.md). Vous pouvez créer des requêtes de recherche à l’aide d’un grand nombre de critères de recherche (y compris la possibilité d’effectuer une recherche dans toutes les [Propriétés de métadonnées de fichier](document-metadata-fields-in-advanced-ediscovery.md)) pour affiner et affiner les données de cas les plus pertinentes pour le cas. Vous pouvez également utiliser les filtres Set Set pour appliquer rapidement des conditions supplémentaires aux résultats d’une requête de recherche afin d’affiner ces résultats. 

   - [Créez et utilisez des balises](tagging-documents.md). Vous pouvez appliquer des balises aux documents dans un ensemble de révision pour identifier les réponses (ou celles qui ne répondent pas à la casse), puis utiliser ces balises lors de la création de requêtes de recherche pour inclure ou exclure les documents balisés. Vous pouvez également marquer les documents à exporter.

   - [Annoter et biffer des documents](view-documents-in-review-set.md#annotate-view). Vous pouvez utiliser l’outil d’annotation dans un examen pour annoter des documents et biffer du contenu dans des documents en tant que produit de travail. Nous générons une version PDF d’un document annoté ou rédigé lors de la révision afin de réduire le risque d’exporter la version native de unredacted du document.

   - [Analyser les données de cas](analyzing-data-in-review-set.md). La fonctionnalité d’analyse dans Advanced eDiscovery est puissante. Une fois que vous avez exécuté l’analyse sur les données dans l’ensemble de révision, nous effectuons des analyses telles que la détection des doublons, le Threading de messagerie électronique et les thèmes qui permettent de réduire le volume des documents à examiner. Nous générons également un rapport d’analyse qui résume le résultat de l’exécution d’Analytics. Comme expliqué précédemment, l’exécution d’Analytics exécute également [le modèle de détection des privilèges du client avocat](attorney-privilege-detection.md#use-the-attorney-client-privilege-detection-model).

5. **Exporter et télécharger des données de cas**. Une dernière étape de la collecte, de l’examen et de l’analyse des données de cas consiste à l’exporter de Advanced eDiscovery pour une révision externe ou pour une révision par des personnes en dehors de l’équipe d’enquête. L’exportation de données est un processus en deux étapes. La première étape consiste à [Exporter](export-documents-from-review-set.md) les données de l’ensemble de révision et à les copier dans un autre emplacement de stockage Azure (fourni par Microsoft ou un de ceux gérés par votre organisation). Ensuite, vous utilisez l’Explorateur de stockage Azure pour [Télécharger](download-export-jobs.md) les données sur un ordinateur local. Outre les fichiers de données exportés, les Contains du package d’exportation contiennent également un rapport d’exportation, un rapport de synthèse et un rapport d’erreurs.
