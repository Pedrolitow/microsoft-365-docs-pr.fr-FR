---
title: Prise en main des cas de découverte électronique de base dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Cet article explique comment commencer à utiliser la découverte électronique de base dans Microsoft 365. Une fois que vous avez affecté des autorisations eDiscovery et créé un cas, vous pouvez ajouter des membres, créer des suspensions eDiscovery, puis Rechercher et exporter des données pertinentes pour votre enquête.
ms.openlocfilehash: c9c3d8c3832703e8dbbcf8b2c04a566af0f5eb6b
ms.sourcegitcommit: 60c1932dcca249355ef7134df0ceb0e57757dc81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "43943383"
---
# <a name="get-started-with-core-ediscovery"></a>Prise en main de la découverte électronique de base

La découverte électronique de base dans Microsoft 365 fournit un outil eDiscovery de base que les organisations peuvent utiliser pour rechercher et exporter du contenu dans Microsoft 365 et Office 365. Vous pouvez également utiliser la découverte électronique de base pour mettre en place une conservation eDiscovery sur des emplacements de contenu, tels que des boîtes aux lettres Exchange, des sites SharePoint, des comptes OneDrive et Microsoft Teams. Rien n’est nécessaire pour déployer la découverte électronique de base, mais il existe des tâches préalables à effectuer par un administrateur informatique et un gestionnaire eDiscovery pour que votre organisation puisse commencer à utiliser le service eDiscovery de base pour rechercher, exporter et conserver du contenu.

Cet article décrit les étapes nécessaires à la configuration de base eDiscovery. Cela inclut la garantie de la bonne licence requise pour accéder à la découverte électronique principale et la mise en attente de la découverte électronique sur les emplacements de contenu, ainsi que l’attribution d’autorisations à votre équipe informatique, légale et d’enquête afin qu’elle puisse accéder aux incidents et les gérer. Cet article fournit également une vue d’ensemble de l’utilisation des cas pour rechercher et exporter du contenu.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Étape 1 : vérifier et affecter les licences appropriées

La gestion des licences pour la découverte électronique principale nécessite l’abonnement de l’organisation et la gestion des licences par utilisateur appropriés.

- **Abonnement à l’Organisation :** Pour accéder à Core eDiscovery dans le centre de conformité Microsoft 365 ou le centre de sécurité & de la sécurité d’Office 365 et utiliser les fonctionnalités de blocage et d’exportation, votre organisation doit avoir un abonnement Microsoft 365 E3 ou Office 365 E3 ou une version ultérieure.

- Gestion **des licences par utilisateur :** Pour placer une conservation eDiscovery sur les boîtes aux lettres et les sites, l’une des licences suivantes doit être attribuée à un utilisateur, en fonction de l’abonnement à votre organisation :

  - Une licence Microsoft 365 E3 ou Office 365 E3 ou supérieure

   OR

  - Une licence Microsoft 365 E1 ou Office 365 E1 avec une licence de module complémentaire Exchange Online plan 2 ou Exchange Online Archiving

  AND

  - Une licence Microsoft 365 E1 ou Office 365 E1 avec une licence de module complémentaire SharePoint Online plan 2 ou OneDrive entreprise plan 2
  
  Pour plus d’informations sur l’attribution des licences, voir [attribuer des licences à des utilisateurs](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).

Pour plus d’informations sur la gestion des licences :

- Téléchargez et consultez la solution « détecter & répondre » dans la [comparaison des licences de conformité de Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/downloads/microsoft-365-compliance-licensing-comparison.xlsx).

- Consultez la rubrique [Description du service Security & Compliance Center](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-securitycompliance-center).

## <a name="step-2-assign-ediscovery-permissions"></a>Étape 2 : attribuer des autorisations eDiscovery

Pour accéder à Core eDiscovery ou être ajouté en tant que membre d’un cas de découverte électronique de base, les autorisations appropriées doivent être attribuées à un utilisateur. Plus précisément, un utilisateur doit être ajouté en tant que membre du groupe de rôles gestionnaire eDiscovery dans le centre de conformité Office 365 Security &. Les membres de ce groupe de rôles peuvent créer et gérer des cas eDiscovery principaux. Ils peuvent ajouter et supprimer des membres, mettre un blocage eDiscovery sur les utilisateurs, créer et modifier des recherches et exporter du contenu à partir d’un cas de découverte électronique principale.

Procédez comme suit pour ajouter des utilisateurs au groupe de rôles gestionnaire eDiscovery :

1. Accédez à [https://protection.office.com/permissions](https://protection.office.com/permissions) et connectez-vous à l’aide des informations d’identification d’un compte d’administrateur de votre organisation Microsoft 365 ou Office 365.

2. Sur la page **autorisations** , sélectionnez le groupe de rôles **Gestionnaire de découverte électronique** .

3. Sur la page de menu volant du gestionnaire eDiscovery, cliquez sur **modifier** en regard de la section **Gestionnaire eDiscovery** .

4. Dans la page **choisir le gestionnaire eDiscovery** dans l’Assistant modifier le groupe de rôles, cliquez sur **choisir le gestionnaire de découverte**.

5. Cliquez sur **Ajouter** , puis activez la case à cocher de tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Cliquez sur **Ajouter** pour ajouter les utilisateurs sélectionnés, puis sur **Terminer**.

7. Cliquez sur **Enregistrer** pour ajouter les utilisateurs au groupe de rôles, puis cliquez sur **Fermer** pour terminer l’étape.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Plus d’informations sur le groupe de rôles gestionnaire eDiscovery

Il existe deux sous-groupes dans le groupe de rôles gestionnaire de découverte électronique. Ces sous-groupes ont différents rôles.

- **Gestionnaire eDiscovery :** Permet d’afficher et de gérer les cas de découverte électronique principaux qu’ils créent ou dont ils sont membres. Si un autre gestionnaire eDiscovery crée un cas mais n’ajoute pas de deuxième gestionnaire eDiscovery en tant que membre de ce dernier, le deuxième gestionnaire eDiscovery ne pourra pas afficher ou ouvrir le cas dans la page de découverte électronique principale dans le centre de conformité. En règle générale, la plupart des utilisateurs de votre organisation peuvent être ajoutés au sous-groupe gestionnaire eDiscovery.

- **administrateur eDiscovery :** Peut effectuer toutes les tâches de gestion des dossiers qu’un gestionnaire eDiscovery peut effectuer. De plus, un administrateur de découverte électronique peut :

  - Afficher tous les cas répertoriés sur la page de découverte électronique principale.
  
  - Gérez tous les cas dans l’organisation une fois qu’ils ont été ajoutés en tant que membre du cas.

  - Accéder à des données de cas et les exporter pour n’importe quel cas dans l’organisation.

  En raison du large éventail d’accès, une organisation ne doit avoir que quelques administrateurs membres du sous-groupe administrateurs eDiscovery.

Pour plus d’informations sur les autorisations de découverte électronique, ainsi qu’une description de chaque rôle affecté au groupe de rôles gestionnaire de découverte électronique, consultez la rubrique [attribution d’autorisations eDiscovery](assign-ediscovery-permissions.md).

## <a name="step-3-create-a-core-ediscovery-case"></a>Étape 3 : créer un cas de découverte électronique principale

L’étape suivante consiste à créer un cas et à commencer à utiliser la découverte électronique principale. Procédez comme suit pour créer un cas et ajouter des membres. L’utilisateur qui crée le cas est automatiquement ajouté en tant que membre.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) et connectez-vous à l’aide des informations d’identification d’un compte d’utilisateur disposant des autorisations eDiscovery appropriées. Les membres du groupe de rôles gestion de l’organisation peuvent également créer des cas de découverte électronique principaux.

2. Dans le volet de navigation de gauche du centre de conformité Microsoft 365, cliquez sur **Afficher tout**, puis sur **découverte électronique > Core**.

3. Sur la page de **découverte électronique principale** , cliquez sur **créer un cas**.

4. Sur la page flyout **New case** , attribuez un nom (obligatoire) à la demande, puis tapez un numéro de cas et une description facultatifs. Le nom du cas doit être unique dans votre organisation.

5. Cliquez sur **Enregistrer** pour créer le cas.

   Le nouvel incident est créé et affiché dans la page de découverte électronique principale. Vous devrez peut-être cliquer sur **Actualiser** pour afficher le nouveau cas. 

## <a name="step-4-optional-add-members-to-a-core-ediscovery-case"></a>Étape 4 (facultative) : ajouter des membres à un cas de découverte électronique principale

Si vous créez un cas à l’étape 3 et que vous êtes la seule personne qui utilisera le cas, vous n’avez pas à effectuer cette étape. Vous pouvez commencer à utiliser le cas pour créer des suspensions eDiscovery, Rechercher du contenu ou exporter des résultats de recherche. Effectuez cette étape si vous souhaitez accorder à d’autres utilisateurs (ou groupes de rôles) un accès à l’incident.

1. Sur la page de **découverte électronique principale** dans le centre de conformité Microsoft 365, cliquez sur le nom de l’incident auquel vous souhaitez ajouter des membres.

2. Sur la page de menu contextuel **gérer ce cas** , sous **gérer les membres**, cliquez sur **Ajouter** pour ajouter des membres à la demande de devis. 

    Vous pouvez également choisir d’ajouter un groupe de rôles en tant que membres d’un cas. Sous **gérer les groupes de rôles**, cliquez sur **Ajouter**. Vous pouvez uniquement affecter les groupes de rôles dont vous êtes membre à un cas. Cela est dû au fait que les groupes de rôles contrôlent les personnes qui peuvent assigner des membres à un cas eDiscovery.

3. Dans la liste des personnes ou des groupes de rôles qui peuvent être ajoutés en tant que membres de la case, activez la case à cocher en regard des noms des personnes (ou des groupes de rôles) que vous souhaitez ajouter. Si vous avez une grande liste de personnes pouvant être ajoutées en tant que membres, utilisez la zone de **recherche** pour rechercher une personne spécifique dans la liste.
  
4. Une fois que vous avez sélectionné les personnes ou les groupes de rôles à ajouter en tant que membres de la demande, cliquez sur **Ajouter**.

5. Cliquez sur **Enregistrer** pour enregistrer la nouvelle liste de membres de cas.

## <a name="explore-the-core-ediscovery-workflow"></a>Explorer le flux de travail eDiscovery principal

Pour commencer à utiliser la découverte électronique de base, voici un simple flux de travail qui consiste à créer des suspensions eDiscovery pour les personnes concernées, à rechercher du contenu pertinent à votre enquête, puis à exporter ces données à des fins de révision. Dans chacune de ces étapes, nous allons également mettre en évidence une fonctionnalité eDiscovery de base étendue que vous pouvez explorer.

![Flux de travail eDiscovery principal](../media/CoreEdiscoveryWorkflow.png)

1. **[Créez un blocage eDiscovery](create-ediscovery-holds.md)**. La première étape après la création d’un cas consiste à placer une conservation (également appelée *conservation eDiscovery*) sur les emplacements de contenu des personnes concernées par votre enquête. Les emplacements de contenu incluent les boîtes aux lettres Exchange, les sites SharePoint, les comptes OneDrive, ainsi que les boîtes aux lettres et les sites associés aux groupes Microsoft teams et Office 365. Bien que cette étape soit facultative, la création d’une conservation eDiscovery préserve le contenu qui peut être pertinent pour le cas au cours de l’enquête. Lorsque vous créez une conservation de découverte électronique, vous pouvez conserver tout le contenu dans des emplacements de contenu spécifiques ou vous pouvez créer une conservation basée sur une requête pour conserver uniquement le contenu qui correspond à une requête de suspension. En plus de la préservation du contenu, une bonne raison de créer des suspensions eDiscovery consiste à rechercher rapidement les emplacements de contenu en conservation (au lieu de sélectionner chaque emplacement de recherche) lorsque vous créez et exécutez des recherches à l’étape suivante. Une fois que vous avez terminé votre enquête, vous pouvez libérer la conservation que vous avez créée.

2. **[Rechercher du contenu](search-for-content-in-core-ediscovery.md)**. Une fois que vous avez créé des suspensions eDiscovery, utilisez l’outil de recherche intégré pour rechercher les emplacements de contenu en conservation. Vous pouvez également rechercher dans d’autres emplacements de contenu des données qui peuvent être pertinentes pour le cas. Vous pouvez créer et exécuter différentes recherches associées au cas. Vous utilisez des mots clés, des propriétés et des conditions pour [créer des requêtes de recherche](keyword-queries-and-search-conditions.md) qui renvoient des résultats de recherche avec les données les plus pertinentes pour le cas. Vous pouvez également effectuer les actions suivantes :

   - Afficher les statistiques de recherche qui peuvent vous aider à affiner une requête de recherche pour affiner les résultats.

   - Affichez un aperçu des résultats de la recherche pour vérifier rapidement si les données pertinentes sont trouvées.

   - Réviser une requête et relancer la recherche.

3. **[Exporter et télécharger les résultats de la recherche](export-content-in-core-ediscovery.md)**. Une fois que vous avez trouvé et trouvé des données pertinentes pour votre enquête, vous pouvez les exporter en dehors d’Office 365 pour les revérifier par des personnes en dehors de l’équipe d’enquête. L’exportation de données est un processus en deux étapes. La première étape consiste à exporter les résultats d’une recherche dans le cas d’Office 365. Pour ce faire, vous pouvez copier les résultats d’une recherche dans un emplacement de stockage Azure fourni par Microsoft. L’étape suivante consiste à utiliser l’outil d’exportation de découverte électronique pour télécharger le contenu sur un ordinateur local. Outre les fichiers de données exportés, les Contains du package d’exportation contiennent également un rapport d’exportation, un rapport de synthèse et un rapport d’erreurs.
