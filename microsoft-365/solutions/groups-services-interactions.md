---
title: Interactions des services de groupe
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
description: Interactions des services de groupe
ms.openlocfilehash: 6d5681b11cdbd837f784b6c8364cce23f964b167
ms.sourcegitcommit: a0cddd1f888edb940717e434cda2dbe62e5e9475
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49613225"
---
# <a name="groups-services-interactions"></a>Interactions des services de groupe

Les groupes Microsoft 365 fournissent un fabric commun pour un certain nombre de services et de charges de travail au sein de la plateforme Microsoft 365 pour offrir une expérience connectée aux utilisateurs finaux. Pour le moment, un groupe Microsoft 365 existe pour fournir les éléments suivants :

- Un moyen de gérer l’appartenance (Azure AD)
- Un emplacement pour la messagerie et les conversations à effectuer (boîte aux lettres Exchange, Microsoft Teams, Yammer)
- Emplacement pour les fichiers à stocker (SharePoint)
- Calendrier de planification (Exchange)
- Un bloc-notes pour la capture de notes (OneNote)

Au moment de la création de groupe, un certain nombre d’autres ressources sont également mises en service, mais elles ne sont pas visibles avant d’être consultées pour la première fois à partir du service :

- Une carte de gestion des tâches de groupe (planificateur)
- Un espace de travail pour la création de rapports (Power BI)
- Zone pour les vidéos partagées (Microsoft Stream)
- Zone pour les formulaires partagés (formulaires)

Dans Microsoft 365, les autres services peuvent interagir avec les groupes Microsoft 365 pour fournir des fonctionnalités et des fonctionnalités supplémentaires aux membres du groupe.
Voici des exemples :

- Applications puissantes pour les applications
- Automate d’alimentation pour les flux de travail
- Projet sur le Web et feuille de route pour la gestion de projet en cascade
- Teams pour les conversations basées sur des canaux
- Yammer pour les communautés d’intérêt

## <a name="user-interactions-with-groups"></a>Interactions entre les utilisateurs et les groupes

Les groupes Microsoft 365 peuvent être créés et gérés à partir d’une variété d’interfaces, que ce soit par les administrateurs et les utilisateurs finaux. 

### <a name="administrative-experiences"></a>Expériences administratives

Les administrateurs peuvent créer et gérer des groupes Microsoft 365 à partir de plusieurs centres d’administration de la charge de travail, des interfaces de ligne de commande qui prennent en charge les scripts, ainsi que des applications personnalisées qui interagissent avec l’API Graph. La seule exception concerne les groupes Yammer, qui doivent être créés à partir de l’interface Web Yammer.

**Paramètres associés**

Les différentes interfaces d’administration qui peuvent gérer les paramètres de groupe existent plusieurs chevauchements dont vous devez être conscient.

**Centre d’administration Microsoft 365**

Dans le centre d’administration Microsoft 365, l’accès invité aux groupes est activé par défaut, tout comme la possibilité d’autoriser les propriétaires à ajouter des invités. Il n’existe pas de contrôles supplémentaires au niveau de l’Organisation pour les groupes à partir de ce centre d’administration.

**Centre d’administration d’Azure AD**

Le centre d’administration Azure AD offre des contrôles qui déterminent si les utilisateurs peuvent créer des groupes ou attribuer des propriétaires dans les portails Azure, ainsi que les paramètres de stratégie d’expiration et d’attribution de noms.

Le centre d’administration fournit également un certain nombre de mesures de contrôle d’invitation invitées qui dépassent celle du centre d’administration Microsoft 365, comme la possibilité de limiter les personnes non propriétaires qui peuvent également inviter des invités.

**SharePoint**

Les sites SharePoint sont créés avec des groupes de sécurité propriétaire, membre et visiteur, les deux premières correspondant à leurs homologues de groupe 365 de Microsoft. Bien que l’appartenance aux sites SharePoint Online soit généralement gérée par le groupe Microsoft 365 associé, il ne s’agit pas d’une relation bidirectionnelle. Toutes les modifications apportées à l’appartenance au niveau du groupe Microsoft 365 sont reflétées dans SharePoint, mais si l’appartenance est modifiée dans le groupe SharePoint, cela n’est pas reflété dans le groupe Microsoft 365.

### <a name="user-experiences"></a>Expériences utilisateur

Les utilisateurs finaux peuvent créer des groupes à partir de plusieurs services au sein de Microsoft 365, et dans d’autres, ils peuvent uniquement partager avec un groupe.

Les services suivants permettent la création de groupes par les utilisateurs finaux :
                         
Projet de planificateur Outlook pour la diffusion Web SharePoint flux de Microsoft teams Yammer

**Restriction de création de groupe**

Une approche commune pour contrôler la prolifération des équipes est de limiter les utilisateurs qui peuvent les créer. Cette opération ne peut être réalisée qu’en limitant la création de groupes. Cela a un impact sur la possibilité de créer des groupes à partir d’autres services, où cela peut s’avérer nécessaire pour l’utilisateur final. Les groupes Microsoft 365 ne prennent pas en charge la possibilité de restreindre la création de groupes à partir de certaines applications ou services, tout en les autorisant à d’autres personnes.

L’expérience de la restriction de création de groupe varie selon les applications et les services :


|Application ou service|Expérience|
|:-------------|:---------|
|Outlook|La nouvelle option de **groupe** est supprimée du menu nouveau dans la page contacts.|
|Planificateur|**Nouveau plan** explique que la création de groupe a été désactivée et propose d’ajouter le plan à un groupe existant.|
|Projet pour le Web et feuille de route|Le menu **créer un groupe** explique que la création de groupe est restreinte et suggère l’utilisation d’un groupe existant.|
|SharePoint|Toujours en mesure de créer un site d’équipe qui n’est pas connecté à un groupe.|
|Stream|L’option de **groupe** ne s’affiche pas dans le **menu créer**.|
|Teams|L’utilisateur ne peut pas créer une équipe avec un nouveau groupe, mais il peut toujours créer une équipe qui utilise un groupe existant.<br><br>**Le bouton créer une équipe** est remplacé par **créer une équipe à partir d’un groupe**.|
|Yammer|**Créer une** option de groupe est supprimé de la navigation groupes/communautés principaux.|

## <a name="services-interactions-with-groups"></a>Interactions entre les services et les groupes

Consultez les groupes dans l’affiche de Microsoft 365 pour obtenir des informations sur les différents types de groupes, la façon dont ils sont créés et gérés, et quelques recommandations en matière de gouvernance.

[![Image miniature pour les groupes infographie](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf)

[PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx)

Le tableau suivant fournit une vue d’ensemble des interactions entre les groupes Microsoft 365 et divers services :

|Produit|Fonctionnalités|Le service est-il<br>existe-t-il sans groupe ?|Le service peut-il<br>créer un groupe ?|Supprime le<br>instance supprimer le groupe ?|
|:---|:---|:---|:---|:---|
|Azure AD|Appartenance, groupes de contrôles, invités|Oui|Oui|Oui|
|Exchange|Calendrier, boîte aux lettres|Oui|Oui|Oui|
|Formulaires|Formulaire|Oui|Non|Non|
|OneNote|Bloc-notes|Oui|Non|Non|
|Planificateur|Tableau des tâches|Non|Oui|Oui|
|Application d’applications puissantes|Application|Oui|Non|Non|
|Power Automate|Flux de travail|Oui|Non|Non|
|Power BI (classique)|Workspace|Non|Oui|Oui|
|Power BI (nouveauté)|Workspace|Oui|Non|Oui|
|Project pour le web|Plan de projet|Oui|Oui|Non|
|Feuille de route|Feuille de route|Oui|Oui|Non|
|SharePoint|Site|Oui|Oui|Oui|
|Stream|Canal, vidéo|Oui|Oui|Oui|
|Teams|Équipe|Non|Oui|Oui|
|Yammer|Group|Oui|Oui|Oui|

Bien que le tableau ci-dessus offre une vue d’ensemble de haut niveau des interactions de groupe avec les services Microsoft 365, il existe un certain nombre de nuances et de subtilités que vous devez comprendre. Les sections suivantes présentent de façon plus approfondie les charges de travail spécifiques et leurs interactions avec les groupes.

## <a name="azure-ad"></a>Azure AD

Azure AD fournit les fonctionnalités de gestion des identités sous-jacentes dans Microsoft 365.

**Fonctionnalités clés fournies aux groupes**

- Appartenance aux groupes
- Stratégie de noms
- Stratégie d’expiration
- Interdire
- Restriction de création de groupe

**Azure AD peut-il créer un groupe ?**

Oui, les groupes Microsoft 365 peuvent être créés à partir d’Azure AD via le portail Web d’administration, via PowerShell ou l’API Graph.

**Azure AD existe-t-il sans groupe ?**

Oui, Azure AD exécute un nombre important de services qui n’ont pas de relation avec les groupes Microsoft 365. Chaque groupe Microsoft 365 est représenté sous la forme d’un objet dans Azure AD.

**Est-ce qu’il peut y avoir plusieurs instances d’Azure AD par groupe ?**

Non, il n’y a qu’une seule instance d’Azure AD.

**Azure AD peut-il être associé à plusieurs groupes ?**

Oui, car Azure AD est la plateforme sous-jacente qui fournit le service d’appartenance au groupe.

**Est-il possible d’associer Azure AD à une modification de groupe ?**

Non, Azure AD est la plateforme sous-jacente où existent des groupes.

**La suppression de l’instance supprime-t-elle le groupe ?**

La suppression du groupe dans Azure AD entraîne la suppression des services et du contenu associés au groupe appropriés.

## <a name="teams"></a>Teams

Teams est un espace de travail centré sur la conversation visant à améliorer la collaboration en fournissant une interface singulière permettant d’interagir avec un grand nombre de services Microsoft et tiers.

Par défaut, lors de la création d’une équipe, la boîte aux lettres et le calendrier associés au groupe Microsoft 365 sont masqués dans la liste d’adresses globale d’Exchange, ainsi que dans Outlook. Cela peut être remplacé manuellement par un administrateur si l’utilisateur souhaite utiliser Outlook et teams sur le même groupe Microsoft 365.

**Fonctionnalités clés fournies aux groupes**

- Conversations
- Canaux & onglets
- Réunions

**Les équipes peuvent-elles créer un groupe ?**

Oui, la création d’une équipe crée un groupe Microsoft 365. Il est également possible de créer une équipe pour un groupe existant qui n’en a pas.

**Existe-t-il des équipes qui n’ont pas de groupe ?**

Non, il n’est pas possible qu’une équipe existe sans groupe.

**Est-ce qu’il peut y avoir plusieurs équipes par groupe ?**

Non, la relation entre une équipe et un groupe est de 1:1.

**Une équipe peut-elle être associée à plusieurs groupes ?**

Non, l’équipe elle-même ne peut être associée qu’à un seul groupe.

**L’Association d’une équipe à un groupe est-elle modifiée ?**

Non, l’équipe ne peut être associée qu’au groupe auquel elle était associée à l’origine.

**La suppression de l’équipe supprime-t-elle le groupe ?**

Oui, la suppression de l’équipe dans Microsoft teams supprimera le groupe, les services associés à un groupe et le contenu.

## <a name="exchange"></a>Exchange

Exchange Online fournit des fonctionnalités de messagerie, de calendrier, de contacts et associées. Dans le contexte d’un groupe, une seule ressource est associée à, par opposition à une instance de service entière.

**Fonctionnalités clés fournies aux groupes**

- Boîte aux lettres et calendrier
- Possibilité d’envoyer un courrier électronique à tous les membres du groupe
- Stockage des conversations de canal teams à des fins de découverte électronique, commentaires du planificateur

**Est-il possible de créer un groupe ?**

Oui, il est possible de créer un groupe à partir du centre d’administration Exchange Online, ainsi qu’à partir d’Outlook. Vous pouvez également convertir les listes de distribution Exchange en groupes Microsoft 365.

**Exchange existe-t-il sans groupe ?**

Oui, Exchange Online fournit un certain nombre de services, y compris les calendriers et les boîtes aux lettres partagées, sans aucune association de groupe.

**Existe-t-il plusieurs instances de boîtes aux lettres Exchange ou de calendriers par groupe ?**

Non, il ne peut y avoir qu’une seule boîte aux lettres et un seul calendrier Exchange Online pour un groupe.

**Est-ce que les boîtes aux lettres et les calendriers Exchange peuvent être associés à plusieurs groupes ?**

Non, la boîte aux lettres et le calendrier ont une relation 1:1 avec le groupe. Il est possible de partager la boîte aux lettres avec d’autres utilisateurs ou groupes, mais cela n’établit pas de type d’association de service.

**Est-ce que la boîte aux lettres Exchange ou l’Association du calendrier à un groupe est modifiée ?**

Non, la boîte aux lettres et le calendrier ne peuvent pas être modifiés en un autre groupe. Toutefois, le contenu peut être déplacé d’une boîte aux lettres à une autre dans Outlook ou à l’aide d’un outil tiers.

**La suppression de la boîte aux lettres supprime-t-elle le groupe ?**

Oui, la suppression de la boîte aux lettres dans Exchange supprime le groupe ainsi que les services et le contenu associés à un groupe.

## <a name="forms"></a>Formulaires

Les formulaires fournissent des enquêtes basées sur le Web et des questionnaires.

**Fonctionnalités clés fournies aux groupes**

- Propriétaire des formulaires

**Les formulaires peuvent-ils créer un groupe ?**

Non, les formulaires ne peuvent pas créer de groupe.

**Existe-t-il des formulaires sans groupe ?**

Oui, des enquêtes et des quiz peuvent être créés directement dans le compte d’un utilisateur final.

**Est-il possible d’utiliser plusieurs formulaires par groupe ?**

Oui, plusieurs formulaires peuvent être associés à un groupe.

**Les formulaires peuvent-ils être associés à plusieurs groupes ?**

Non, un formulaire ne peut être associé qu’à un seul groupe.

**L’Association d’un formulaire à un groupe est-elle modifiée ?**

Non, une fois qu’un formulaire est associé à un groupe (créé directement dans, ou propriétaire transféré à partir d’un individu), il ne peut pas être déplacé vers un autre groupe.

**La suppression du formulaire supprime-t-elle le groupe ?**

Non, il n’est pas possible de supprimer un groupe de l’interface formulaires, mais uniquement des formulaires individuels.

## <a name="onenote"></a>OneNote

OneNote est une application de bloc-notes numérique. Le bloc-notes OneNote créé avec un groupe est un fichier du site SharePoint associé au lieu d’un service connecté à un groupe.

**Fonctionnalités clés fournies aux groupes**

- Bloc-notes partagé (stocké dans la bibliothèque SharePoint associée à un groupe)

**OneNote peut-il créer un groupe ?**

Non, l’application OneNote ne peut pas créer de groupe.

**Existe-t-il des blocs-notes OneNote sans groupe ?**

Oui, les blocs-notes peuvent être créés directement dans OneDrive ou dans d’autres emplacements partagés.

**Existe-t-il plusieurs blocs-notes OneNote par groupe ?**

Oui, un bloc-notes est créé par défaut et d’autres peuvent être ajoutés, mais tout lien vers OneNote à partir de services associés à un groupe est toujours dirigé vers le bloc-notes par défaut.

**Un bloc-notes OneNote peut-il être associé à plusieurs groupes ?**

Non, le bloc-notes est stocké dans la bibliothèque de sites SharePoint associée à un groupe et lié à partir de différentes interfaces. Il peut toutefois être partagé avec d’autres groupes de la même manière qu’il peut être partagé avec des personnes.

**L’Association du bloc-notes avec un groupe est-elle modifiée ?**

Non, le bloc-notes lui-même est associé au groupe et est directement accessible à partir d’autres services connectés au groupe, mais le contenu peut être déplacé d’un bloc-notes vers un autre au sein de l’application OneNote.

**La suppression du bloc-notes supprime-t-elle le groupe ?**

Non, toutefois, si le bloc-notes OneNote est supprimé, certains liens peuvent être rompus dans certains services associés au groupe.

## <a name="planner"></a>Planificateur

Le planificateur est un service de gestion des tâches de groupe léger.

**Fonctionnalités clés fournies aux groupes**

- Carte de gestion des tâches de groupe

**Le planificateur peut-il créer un groupe ?**

Oui, la création d’un plan crée un groupe.

**Existe-t-il un tableau de planification sans groupe ?**

Non, un plan doit être associé à un groupe.

**Est-il possible d’avoir plusieurs plans par groupe ?**

Oui, il peut y avoir plusieurs plans par groupe.

**Un plan peut-il être associé à plusieurs groupes ?**

Non, un plan s’appuie uniquement sur l’appartenance au groupe pour déterminer l’accès.

**Est-il possible d’associer un plan à une modification de groupe ?**

Non, toutefois, la copie d’un plan crée un groupe.

> [!NOTE]
> Un groupe créé par une autre application n’apparaîtra pas automatiquement dans le planificateur pour un utilisateur. Pour accéder au premier Conseil, il faut l’ouvrir à partir d’une autre interface de groupe, telle qu’Outlook.

**La suppression du plan supprime-t-elle le groupe ?**

Oui, la suppression du plan supprimera les services et le contenu associés au groupe et au groupe.

## <a name="power-apps"></a>Power Apps

Les applications Power fournissent une zone de dessin pour le développement d’applications sans code.

**Fonctionnalités clés fournies aux groupes**

- Les applications peuvent être partagées avec un groupe pour être exécutées et modifiées

**Les applications Power peuvent-elles créer un groupe ?**

Non, les applications Power ne peuvent pas créer de groupe Microsoft 365.

**Existe-t-il des applications puissantes sans groupe ?**

Oui, les applications peuvent être créées au sein des applications d’alimentation et se trouver dans le compte de créateurs jusqu’à leur publication partagée ou publiée.

**Existe-t-il plusieurs applications par groupe ?**

Oui, il peut y avoir plusieurs applications partagées avec un groupe.

**Les applications peuvent-elles être associées à plusieurs groupes ?**

Oui, une application peut être partagée avec plusieurs groupes.

**Est-il possible d’associer une association d’application à un groupe ?**

Oui, comme l’association entre les applications d’alimentation et un groupe Microsoft 365 est le partage uniquement : l’application se trouve toujours avec le créateur.

> [!IMPORTANT]
> La [sécurité des groupes doit être activée pour que les applications puissent être partagées avec elles](https://docs.microsoft.com/powerapps/maker/canvas-apps/share-app#share-an-app-with-office-365-groups).

**La suppression de l’application supprime-t-elle le groupe ?**

Non, les applications ne sont pas connectées au groupe autrement qu’elles ne sont pas partagées avec elles.

## <a name="power-automate"></a>Power Automate

Power automate (anciennement connu sous le nom de Microsoft Flow) fournit des flux de travail et des services d’automatisation.

**Fonctionnalités clés fournies aux groupes**

- Les flux de travail peuvent être partagés avec un groupe pour être exécutés et modifiés.

**Est-il possible d’alimenter automate de créer un groupe ?**

Non, Power automate ne peut pas créer de groupe Microsoft 365 dans le contexte associé à un groupe.

Toutefois, il est possible de créer un flux qui effectue diverses opérations, telles que la création d’un groupe de sécurité Azure AD ou la mise à jour de l’appartenance à un groupe Microsoft 365.

**Existe-t-il des flux sans groupe ?**

Oui, les flux peuvent être créés au sein de Power automate et résider dans le compte de créateurs jusqu’à ce qu’ils soient partagés ou publiés.

**Existe-t-il plusieurs flux par groupe ?**

Oui, plusieurs flux peuvent être partagés avec un groupe.

**Un flux peut-il être associé à plusieurs groupes ?**

Oui, un flux peut être partagé avec plusieurs groupes.

**L’Association d’un flux à un groupe est-elle modifiée ?**

Oui, comme l’association entre Power Automated et un groupe Microsoft 365 est le partage uniquement, le flux se trouve toujours avec le créateur.

**La suppression d’un flux supprime-t-elle le groupe ?**

Non, comme les applications d’alimentation, les flux ne sont pas connectés au groupe autrement qu’être partagés avec eux.

## <a name="power-bi-classic"></a>Power BI (classique)

Power BI fournit des tableaux de bord et des rapports interactifs pilotés par les données.

**Fonctionnalités clés fournies aux groupes**

- Création de rapports de données

**Power BI peut-il créer un groupe ?**

Oui, la création d’un espace de travail classique crée un groupe Microsoft 365.

**Est-ce qu’un espace de travail Power BI classique existe sans groupe ?**

Non, [un espace de travail classique dans Power bi doit être associé à un groupe](https://docs.microsoft.com/power-bi/collaborate-share/service-collaborate-power-bi-workspace).

**Est-il possible d’utiliser plusieurs espaces de travail Power BI par groupe ?**

Non, la relation entre un espace de travail classique et un groupe est de 1:1.

**Un espace de travail peut-il être associé à plusieurs groupes ?**

Techniquement non, tandis que l’espace de travail classique est créé avec le groupe, le contenu peut être partagé en dehors du groupe avec des utilisateurs et des groupes de sécurité.

**L’Association de l’espace de travail à un groupe est-elle modifiée ?**

Non, l’espace de travail classique lui-même est associé au groupe, mais le contenu peut être déplacé d’un espace de travail à un autre au sein de l’interface Power BI ou en exportant le contenu localement.

**La suppression de l’espace de travail supprime-t-elle le groupe ?**

Oui, la suppression de l’espace de travail dans Power BI supprime les services et le contenu associés aux groupes et aux groupes.

## <a name="power-bi-new"></a>Power BI (nouveauté)

Power BI fournit des tableaux de bord et des rapports interactifs pilotés par les données.

Alors que la création d’un nouvel espace de travail dans Power BI ne crée pas de groupe Microsoft 365, la création d’un groupe par un autre moyen crée un nouvel espace de travail (pas classique) dans Power BI.

**Fonctionnalités clés fournies aux groupes**

- Création de rapports de données

**Power BI peut-il créer un groupe ?**

Non, il n’est pas possible de créer un groupe Microsoft 365 à partir de la nouvelle interface Power BI.

**Est-ce que le nouvel espace de travail Power BI existe sans groupe ?**

Oui, il est possible d’avoir des rapports et des espaces de travail créés dans Power BI qui ne sont pas associés à des groupes Microsoft 365.

**Existe-t-il plusieurs espaces de travail par groupe ?**

Oui, [plusieurs espaces de travail créés par Power bi peuvent être partagés avec un seul groupe](https://docs.microsoft.com/power-bi/collaborate-share/service-create-the-new-workspaces#give-access-to-your-workspace).

**Un espace de travail peut-il être associé à plusieurs groupes ?**

Non, un espace de travail créé par Power BI ne peut être associé qu’à un seul groupe.

**Est-il possible d’associer une modification de groupe à un espace de travail ?**

Oui et non. Un espace de travail créé par Power BI ne peut être associé qu’à un seul groupe à la fois, mais peut modifier l’Association à tout moment. Un espace de travail créé dans Power BI par un groupe est associé de façon permanente à ce groupe.

**La suppression de l’espace de travail supprime-t-elle le groupe ?**

Oui, la suppression de l’espace de travail dans Power BI supprime le groupe, ainsi que les services et le contenu associés à un groupe.

## <a name="project-for-the-web"></a>Project pour le web

Project pour le Web offre la possibilité de créer des plans de projet, des diagrammes de Gantt et des feuilles de route.
Fonctionnalités clés fournies aux groupes.

- Plans de projet

**Project pour le Web peut-il créer un groupe ?**

Oui, il est possible de créer un nouveau groupe Microsoft 365 directement à partir de Project pour le Web.

**Existe-t-il des projets sans groupe ?**

Oui, des projets peuvent exister sans être associés à un groupe Microsoft 365, toutefois, l’affectation de tâches nécessite une association de groupe.

**Est-il possible d’utiliser plusieurs projets par groupe ?**

Oui, il est possible de connecter plusieurs projets dans un seul groupe.

**Un projet peut-il être associé à plusieurs groupes ?**

Non, un projet ne peut être associé qu’à un seul groupe.

**L’Association d’un projet à un groupe est-elle modifiée ?**

Non, une fois que l’association avec un groupe est établie, elle ne peut plus être modifiée.

**La suppression du projet est-elle supprimée ?**

Non, la suppression du projet dans Project pour le Web ne supprime pas le groupe.

## <a name="roadmap"></a>Feuille de route

La feuille de route offre la possibilité de créer des feuilles de route pour Project pour le Web et Project online.

**Fonctionnalités clés fournies aux groupes**

- Feuilles de route de projet

**Une feuille de route peut-elle créer un groupe ?**

Oui, il est possible de créer un nouveau groupe Microsoft 365 directement à partir de la feuille de route.

**Existe-t-il une feuille de route sans groupe ?**

Oui, des feuilles de route peuvent exister sans être associées à un groupe Microsoft 365, toutefois le partage de la feuille de route nécessite une association de groupe.

**Existe-t-il plusieurs feuilles de route par groupe ?**

Oui, il est possible de connecter plusieurs feuilles de route à un seul groupe.

**Une feuille de route peut-elle être associée à plusieurs groupes ?**

Non, une feuille de route ne peut être associée qu’à un seul groupe.

**Est-il possible d’associer une feuille de route à une modification de groupe ?**

Non, une fois que l’association avec un groupe est établie, elle ne peut plus être modifiée.

**La suppression de la feuille de route supprime-t-elle le groupe ?**

Non, la suppression de la feuille de route ne supprime pas le groupe.

## <a name="sharepoint"></a>SharePoint

SharePoint est une plateforme de gestion de contenu basée sur le Web qui fournit entre autres des services de stockage pour un certain nombre de services Microsoft 365.

**Fonctionnalités clés fournies aux groupes**

- Bibliothèque de documents
- Bibliothèque pour le stockage du bloc-notes OneNote
- Stockage des fichiers wiki teams

**SharePoint peut-il créer un groupe ?**

Oui, la création d’un site d’équipe dans SharePoint crée un groupe Microsoft 365 par défaut. Il est également possible de créer un groupe et, éventuellement, une équipe pour un site existant.

**Existe-t-il des sites SharePoint sans groupe ?**

Oui, SharePoint propose un certain nombre de services et de sites qui ne sont pas associés à un groupe, tels que les sites de communication et Hub. 

**Existe-t-il plusieurs sites par groupe ?**

Non, il ne peut y avoir qu’un seul site par groupe. Les canaux privés dans teams utilisent des sites supplémentaires qui ne sont pas connectés au groupe.

**Des sites peuvent-ils être associés à plusieurs groupes ?**

Techniquement non, mais lorsqu’un site est créé avec un groupe, le contenu peut être partagé avec d’autres groupes.

**L’Association d’un site à un groupe est-elle modifiée ?**

Non, le site lui-même est associé au groupe, mais le contenu peut être déplacé d’un site à un autre au sein de l’interface SharePoint, en exportant le contenu localement ou à l’aide d’un outil tiers.

**Est-ce que la suppression du site est supprimée ?**

Oui, la suppression du site dans SharePoint entraîne la suppression des services et du contenu associés aux groupes et aux groupes.

## <a name="stream"></a>Stream

Microsoft Stream est une plateforme d’hébergement et de partage vidéo.

**Fonctionnalités clés fournies aux groupes**

- Stockage vidéo
- Enregistrement des réunions teams
- Canaux vidéo

**Est-il possible de créer un groupe en continu ?**

Oui, il est possible de créer un nouveau groupe Microsoft 365 directement à partir de Stream.

**Est-ce qu’un flux existe sans groupe ?**

Oui, les canaux vidéo et vidéos peuvent exister dans le flux sans être associés à un groupe.

**Est-il possible d’utiliser plusieurs vidéos et canaux par groupe ?**

Oui, il peut y avoir plusieurs vidéos et canaux dans chaque groupe.

**Une vidéo ou un canal peut-il être associé à plusieurs groupes ?**

Oui, tandis qu’une vidéo ou un canal est créé avec un groupe, il peut être partagé avec d’autres groupes.

**Son association avec un groupe est-elle modifiée ?**

Oui et non ; les vidéos dans le flux appartiennent au téléchargeur ou à l’enregistreur de réunions d’origine et peuvent être associées à n’importe quel groupe, mais les canaux vidéo ne peuvent être associés qu’au groupe dans lequel ils ont été créés à l’origine.

**La suppression des vidéos ou des canaux supprime-t-elle le groupe ?**

Non, la suppression des vidéos ou des canaux ne supprime pas le groupe. Toutefois, la suppression du groupe lui-même dans Stream supprimera les services et le contenu associés à un groupe, à l’exception des vidéos réelles.

## <a name="yammer"></a>Yammer

Yammer est une plateforme sociale d’entreprise conçue pour encourager les engagements de la Communauté au sein et entre les organisations.

La création d’une communauté (anciennement « Group ») dans Yammer crée une boîte aux lettres, mais, actuellement, cela n’est pas utilisé.

Un groupe Microsoft 365 associé à Yammer ne peut pas être utilisé avec une équipe dans Microsoft Teams.

**Fonctionnalités clés fournies aux groupes**

- Zone de conversation

**Est-ce que Yammer peut créer un groupe Microsoft 365 ?**

Oui, la création d’un groupe dans Yammer crée un groupe Microsoft 365, si les plateformes sont connectées et que l’utilisateur a la possibilité de créer un groupe.

Un groupe Yammer avec le groupe Microsoft 365 associé ne peut pas être créé dans une interface ou un service autre que Yammer lui-même.

**Un groupe Yammer existe sans groupe Microsoft 365 ?**

Oui, il est possible de créer un groupe Yammer sans groupe Microsoft 365.

Si la plateforme Yammer n’est pas connectée à des groupes Microsoft 365 ou si les utilisateurs n’ont pas la possibilité de créer un groupe Microsoft 365, les groupes Yammer sont créés sans association de groupe Microsoft 365.

**Existe-t-il plusieurs groupes Yammer par groupe Microsoft 365 ?**

Non, la relation entre un groupe Yammer et un groupe Microsoft 365 est de 1:1.

**Un groupe Yammer peut-il être associé à plusieurs groupes Microsoft 365 ?**

Non, le groupe Yammer ne peut être associé qu’à un seul groupe Microsoft 365. Il est possible que les publications soient partagées ou déplacées vers d’autres groupes Yammer.

**L’Association d’un groupe Yammer à un groupe Microsoft 365 peut-elle être modifiée ?**

Non, le groupe Yammer ne peut être associé qu’au groupe Microsoft 365 auquel il était initialement associé.

**La suppression du groupe Yammer supprime-t-elle le groupe Microsoft 365 ?**

Oui, la suppression du groupe dans Yammer entraîne la suppression des services et du contenu associés au groupe et au groupe Microsoft.

## <a name="related-topics"></a>Voir aussi

[Planification de la gouvernance de collaboration étape par étape](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Création de votre plan de gouvernance de collaboration](collaboration-governance-first.md)

