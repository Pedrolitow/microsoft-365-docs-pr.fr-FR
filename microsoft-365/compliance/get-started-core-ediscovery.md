---
title: Démarrage avec des cas eDiscovery (Standard) dans Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Décrit comment commencer à utiliser eDiscovery (Standard) dans Microsoft Purview. Après avoir affecté des autorisations eDiscovery et créé un cas, vous pouvez ajouter des membres, créer des conservations eDiscovery, puis rechercher et exporter du contenu pertinent pour votre enquête.
ms.openlocfilehash: 38e4d24405810293c9261c1c7f728ece0714cd66
ms.sourcegitcommit: 1c8f54f9e7a7665bc10b5ef4a3d8c36e3e48f44c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2022
ms.locfileid: "66078477"
---
# <a name="get-started-with-ediscovery-standard-in-microsoft-purview"></a>Démarrage avec eDiscovery (Standard) dans Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eDiscovery (Standard) dans Microsoft Purview fournit un outil eDiscovery de base que les organisations peuvent utiliser pour rechercher et exporter du contenu dans Microsoft 365 et Office 365. Vous pouvez également utiliser eDiscovery (Standard) pour placer une conservation eDiscovery sur des emplacements de contenu, tels que des boîtes aux lettres Exchange, des sites SharePoint, des comptes OneDrive et des Microsoft Teams. Rien n’est nécessaire pour déployer eDiscovery (Standard), mais un administrateur informatique et un responsable eDiscovery doivent effectuer certaines tâches préalables avant que votre organisation puisse commencer à utiliser eDiscovery (Standard) pour rechercher, exporter et conserver du contenu.

Cet article décrit les étapes nécessaires à la configuration d’eDiscovery (Standard). Cela inclut la garantie des licences appropriées requises pour accéder à eDiscovery (Standard) et placer une conservation eDiscovery sur les emplacements de contenu, ainsi que l’attribution d’autorisations à votre équipe informatique, juridique et d’enquête afin qu’elle puisse accéder aux cas et les gérer. Cet article fournit également une vue d’ensemble générale de l’utilisation de cas pour rechercher et exporter du contenu.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Étape 1 : Vérifier et attribuer les licences appropriées

La gestion des licences pour eDiscovery (Standard) nécessite l’abonnement de l’organisation et les licences par utilisateur appropriés.

- **Abonnement à l’organisation :** Pour accéder à eDiscovery (Standard) dans le portail de conformité Microsoft Purview et utiliser les fonctionnalités de conservation et d’exportation, votre organisation doit disposer d’un Exchange abonnement en ligne Plan 2 ou Microsoft 365 E3 ou Office 365 E3 ou supérieur. Microsoft 365 les organisations de première ligne doivent disposer d’un abonnement F5.

- **Licences par utilisateur :** Pour placer une conservation eDiscovery sur les boîtes aux lettres et les sites, les utilisateurs doivent se voir attribuer l’une des licences suivantes, en fonction de l’abonnement de votre organisation :

  - Une licence Microsoft 365 E3 ou Office 365 E3 ou ultérieure

   OR

  - Office 365 E1 licence avec une licence de module complémentaire Exchange Online Plan 2 ou Archivage Exchange Online

   OR

  - Microsoft 365 licence de module complémentaire conformité F5 ou F5 Security & Compliance  

  AND

  - Office 365 E1 licence avec une licence de module complémentaire SharePoint Online Plan 2 ou OneDrive Entreprise Plan 2
  
  Pour plus d’informations sur l’attribution de licences, consultez [Affecter des licences aux utilisateurs](../admin/manage/assign-licenses-to-users.md).

Pour obtenir des informations et des conseils sur la sécurité et la conformité :

- Téléchargez et consultez la section eDiscovery et audit dans la [table de comparaison Microsoft 365](https://aka.ms/M365EnterprisePlans).

- Consultez les [instructions Microsoft 365 relatives à la conformité des & de sécurité - Descriptions de service | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="step-2-assign-ediscovery-permissions"></a>Étape 2 : Attribuer des autorisations eDiscovery

Pour accéder à eDiscovery (Standard) ou être ajouté en tant que membre d’un cas eDiscovery (Standard), un utilisateur doit disposer des autorisations appropriées. Plus précisément, un utilisateur doit être ajouté en tant que membre du groupe de rôles eDiscovery Manager dans le portail de conformité. Les membres de ce groupe de rôles peuvent créer et gérer des cas eDiscovery (Standard). Ils peuvent ajouter et supprimer des membres, placer une conservation eDiscovery sur les utilisateurs, créer et modifier des recherches, et exporter du contenu à partir d’un cas eDiscovery (Standard).

Effectuez les étapes suivantes pour ajouter des utilisateurs au groupe de rôles gestionnaire eDiscovery :

1. Accédez au portail de conformité et connectez-vous à l’aide des informations d’identification d’un compte d’administrateur dans votre Microsoft 365 ou Office 365 organisation.

2. Dans la page Autorisations, sélectionnez le groupe de <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**rôles**</a> **gestionnaire eDiscovery** .

3. Dans la page de menu volant eDiscovery Manager, cliquez sur **Modifier** en regard de la section **gestionnaire eDiscovery** .

4. Dans la page **Choisir le gestionnaire eDiscovery** dans l’Assistant Modifier le groupe de rôles, cliquez sur **Choisir le gestionnaire de découverte**.

5. Cliquez sur **Ajouter** , puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Cliquez sur **Ajouter** pour ajouter les utilisateurs sélectionnés, puis cliquez sur **Terminé**.

7. Cliquez sur **Enregistrer** pour ajouter les utilisateurs au groupe de rôles, puis sur **Fermer** pour terminer l’étape.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Plus d’informations sur le groupe de rôles eDiscovery Manager

Il existe deux sous-groupes dans le groupe de rôles gestionnaire eDiscovery. Ces sous-groupes ont différents rôles.

- **Gestionnaire eDiscovery** : peut afficher et gérer les cas eDiscovery (Standard) qu’ils créent ou dont ils sont membres. Si un autre gestionnaire eDiscovery crée un cas mais n’ajoute pas de deuxième gestionnaire eDiscovery en tant que membre de ce cas, le deuxième gestionnaire eDiscovery ne peut pas afficher ou ouvrir le cas sur la page eDiscovery (Standard) dans le centre de conformité. En général, la plupart des membres de votre organisation peuvent être ajoutés au sous-groupe eDiscovery Manager.

- **Administrateur eDiscovery** : peut effectuer toutes les tâches de gestion de cas qu’un gestionnaire eDiscovery peut effectuer. De plus, un administrateur de découverte électronique peut :

  - Affichez tous les cas répertoriés dans la page eDiscovery (Standard).
  
  - Gérer tous les cas au sein l’organisation après s’être ajouté en tant que membre du cas.

  - Accéder et exporter des données de cas pour tout cas au sein de l’organisation.
  
  - Supprimez des membres d’un cas eDiscovery. Seul un administrateur eDiscovery peut supprimer des membres d’un cas. Les utilisateurs qui sont membres du sous-groupe eDiscovery Manager ne peuvent pas supprimer de membres d’un cas, même si l’utilisateur a créé le cas.

  En raison de l’étendue de l’accès, une organisation ne doit avoir que quelques administrateurs membres du sous-groupe administrateurs eDiscovery.

Pour plus d’informations sur les autorisations eDiscovery et une description de chaque rôle affecté au groupe de rôles eDiscovery Manager, consultez [Affecter des autorisations eDiscovery](assign-ediscovery-permissions.md).

## <a name="step-3-create-a-ediscovery-standard-case"></a>Étape 3 : Créer un cas eDiscovery (Standard)

L’étape suivante consiste à créer un cas et à commencer à utiliser eDiscovery (Standard). Effectuez les étapes suivantes pour créer un cas et ajouter des membres. L’utilisateur qui crée le cas est automatiquement ajouté en tant que membre.

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité</a> et connectez-vous à l’aide des informations d’identification d’un compte d’utilisateur qui a reçu les autorisations eDiscovery appropriées. Les membres du groupe de rôles Gestion de l’organisation peuvent également créer des cas eDiscovery (Standard).

2. Dans le volet de navigation gauche du portail de conformité, cliquez sur **Afficher tout**, puis sur **eDiscovery** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank">**Core**</a>.

3. Dans la page **eDiscovery (Standard),** cliquez sur **Créer un cas**.

4. Dans la page de menu volant **Nouveau cas** , donnez un nom (obligatoire) au cas, puis tapez une description facultative. Le nom du cas doit être unique dans votre organisation.

5. Cliquez sur **Enregistrer** pour créer le cas.

   Le nouveau cas est créé et affiché sur la page eDiscovery (Standard). Vous devrez peut-être cliquer sur **Actualiser** pour afficher le nouveau cas.

## <a name="step-4-optional-add-members-to-a-ediscovery-standard-case"></a>Étape 4 (facultatif) : Ajouter des membres à un cas eDiscovery (Standard)

Si vous créez un cas à l’étape 3 et que vous êtes la seule personne à utiliser le cas, vous n’êtes pas obligé d’effectuer cette étape. Vous pouvez commencer à utiliser le cas pour créer des conservations eDiscovery, rechercher du contenu et exporter les résultats de la recherche. Effectuez cette étape si vous souhaitez accorder à d’autres utilisateurs (ou groupe de rôles) l’accès au cas.

1. Dans la page **eDiscovery (Standard)** du portail de conformité, cliquez sur le nom du cas auquel vous souhaitez ajouter des membres.

2. Dans la page d’accueil du cas, sélectionnez l’onglet **Paramètres**, puis sélectionnez **Autorisations d’accès &**.

3. Dans la page de menu volant **Accès & autorisations** , sous **Membres**, cliquez sur **Ajouter** pour ajouter des membres au cas.

    Vous pouvez également choisir d’ajouter des groupes de rôles en tant que membres d’un cas. Sous **Groupes de rôles**, cliquez sur **Ajouter**. Vous pouvez uniquement affecter les groupes de rôles dont vous êtes membre à un cas. Cela est dû au fait que les groupes de rôles contrôlent qui peut affecter des membres à un cas eDiscovery.

4. Dans la liste des personnes ou groupes de rôles qui peuvent être ajoutés en tant que membres du cas, cliquez à gauche du nom des personnes (ou groupes de rôles) que vous souhaitez ajouter. Si vous avez une grande liste de personnes ou de groupes de rôles qui peuvent être ajoutés en tant que membres, utilisez la zone **de recherche** pour rechercher une personne ou un groupe de rôles spécifique dans la liste.
  
5. Après avoir sélectionné les personnes ou groupes de rôles à ajouter en tant que membres du cas, cliquez sur **Enregistrer** pour enregistrer les nouveaux membres ou groupes de rôles.

> [!IMPORTANT]
>
>- Si un rôle est ajouté ou supprimé d’un groupe de rôles que vous avez ajouté en tant que membre d’un cas, le groupe de rôles est automatiquement supprimé en tant que membre du cas (ou dans tous les cas dont le groupe de rôles est membre). La raison en est que votre organisation ne fournit pas par inadvertance des autorisations supplémentaires aux membres d’un cas. De même, si un groupe de rôles est supprimé, il sera supprimé de tous les cas dont il était membre. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases). 
>
>- Comme expliqué précédemment, seul un administrateur eDiscovery peut supprimer des membres d’un cas. Les utilisateurs qui sont membres du sous-groupe eDiscovery Manager ne peuvent pas supprimer de membres d’un cas, même si l’utilisateur a créé le cas.
>

## <a name="explore-the-ediscovery-standard-workflow"></a>Explorer le flux de travail eDiscovery (Standard)

Pour commencer à utiliser eDiscovery (Standard), voici un flux de travail simple qui consiste à créer des conservations eDiscovery pour les personnes intéressées, à rechercher du contenu pertinent pour votre enquête, puis à exporter ces données pour une révision ultérieure. Dans chacune de ces étapes, nous allons également mettre en évidence certaines fonctionnalités eDiscovery (Standard) étendues que vous pouvez explorer.

![Flux de travail eDiscovery (Standard).](../media/CoreEdiscoveryWorkflow.png)

1. **[Créez une conservation eDiscovery](create-ediscovery-holds.md)**. La première étape après la création d’un cas consiste à placer une conservation (également appelée conservation *eDiscovery*) sur les emplacements de contenu des personnes intéressées par votre enquête. Les emplacements de contenu incluent les boîtes aux lettres Exchange, les sites SharePoint, les comptes OneDrive, ainsi que les boîtes aux lettres et les sites associés à Microsoft Teams et Groupes Microsoft 365. Bien que cette étape soit facultative, la création d’une conservation eDiscovery conserve le contenu qui peut être pertinent pour le cas pendant l’enquête. Lorsque vous créez une conservation eDiscovery, vous pouvez conserver tout le contenu dans des emplacements de contenu spécifiques ou créer une conservation basée sur une requête pour conserver uniquement le contenu qui correspond à une requête de conservation. Outre la conservation du contenu, une autre bonne raison de créer des conservations eDiscovery consiste à rechercher rapidement les emplacements de contenu en attente (au lieu d’avoir à sélectionner chaque emplacement à rechercher) lorsque vous créez et exécutez des recherches à l’étape suivante. Une fois que vous avez terminé votre investigation, vous pouvez libérer n’importe quelle conservation que vous avez créée.

2. **[Recherchez du contenu](search-for-content-in-core-ediscovery.md)**. Une fois que vous avez créé des conservations eDiscovery, utilisez l’outil de recherche intégré pour rechercher les emplacements de contenu en attente. Vous pouvez également rechercher des données pertinentes pour le cas dans d’autres emplacements de contenu. Vous pouvez créer et exécuter différentes recherches associées au cas. Vous utilisez des mots clés, des propriétés et des conditions pour [créer des requêtes de recherche](keyword-queries-and-search-conditions.md) qui retournent des résultats de recherche avec les données les plus susceptibles d’être pertinentes pour le cas. Vous pouvez également :

   - Affichez les statistiques de recherche qui peuvent vous aider à affiner une requête de recherche pour affiner les résultats.

   - Affichez un aperçu des résultats de la recherche pour vérifier rapidement si les données pertinentes sont trouvées.

   - Modifiez une requête et réexécutez la recherche.

3. **[Exportez et téléchargez les résultats de la recherche](export-content-in-core-ediscovery.md)**. Une fois que vous avez recherché et trouvé des données pertinentes pour votre enquête, vous pouvez les exporter hors de Office 365 pour examen par des personnes extérieures à l’équipe d’enquête. L’exportation de données est un processus en deux étapes. La première étape consiste à exporter les résultats d’une recherche dans le cas de Office 365. Pour ce faire, copiez les résultats d’une recherche dans un emplacement stockage Azure fourni par Microsoft. L’étape suivante consiste à utiliser l’outil d’exportation eDiscovery pour télécharger le contenu sur un ordinateur local. En plus des fichiers de données exportés, le package d’exportation contient un rapport d’exportation, un rapport récapitulatif et un rapport d’erreur.
