---
title: Interactions des services de groupes
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Interactions des services de groupes
ms.openlocfilehash: bac612841ca5fb61e27f633c5492f4b09426da1c
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67986793"
---
# <a name="groups-services-interactions"></a>Interactions des services de groupes

Groupes Microsoft 365 fournit une infrastructure commune pour plusieurs services et charges de travail au sein de la plateforme Microsoft 365 afin de fournir une expérience connectée pour les utilisateurs finaux. À la base, un groupe Microsoft 365 existe pour fournir :

- Un moyen de gérer l’appartenance (Azure AD)
- Lieu de messagerie et de conversations (boîte aux lettres Exchange, Microsoft Teams, Yammer)
- Emplacement de stockage des fichiers (SharePoint)
- Un calendrier pour la planification (Exchange)
- Bloc-notes pour la capture de notes (OneNote)

Au moment de la création du groupe, plusieurs autres ressources sont également approvisionnées, mais elles ne sont pas visibles tant qu’elles ne sont pas accessibles pour la première fois à partir du service :

- Tableau de gestion des tâches de groupe (Planificateur)
- Un espace de travail pour la création de rapports (Power BI)
- Zone pour les vidéos partagées (Microsoft Stream)
- Zone pour les formulaires partagés (formulaires)

Dans Microsoft 365, d’autres services sont en mesure d’interagir avec les groupes Microsoft 365 pour fournir des fonctionnalités et des fonctionnalités supplémentaires aux membres du groupe.
Voici quelques exemples :

- Power Apps pour les applications
- Power Automate pour les flux de travail
- Projet sur le web et feuille de route pour la gestion de projets en cascade
- Teams pour les conversations basées sur un canal
- Yammer pour les communautés d’intérêt

## <a name="user-interactions-with-groups"></a>Interactions utilisateur avec des groupes

Groupes Microsoft 365 peuvent être créés et gérés à partir de différentes interfaces, à la fois par les administrateurs et les utilisateurs finaux. 

### <a name="administrative-experiences"></a>Expériences administratives

Les administrateurs peuvent créer et gérer des groupes Microsoft 365 à partir de plusieurs centres d’administration de charge de travail, d’interfaces de ligne de commande qui prennent en charge les scripts, ainsi que d’applications personnalisées qui interagissent avec le API Graph. La seule exception à cela est les groupes Yammer, qui doivent être créés à partir de l’interface web Yammer.

**Paramètres associés**

Dans les différentes interfaces d’administration qui peuvent gérer les paramètres de groupe, il existe plusieurs chevauchements dont vous devez être conscient.

**Centre d’administration Microsoft 365**

Dans le Centre d'administration Microsoft 365, l’accès invité aux groupes est activé par défaut, tout comme la possibilité d’autoriser les propriétaires à ajouter des invités. Aucun autre contrôle au niveau de l’organisation n’est disponible pour les groupes à partir de ce centre d’administration.

**Centre d’administration Azure AD**

Le Centre d’administration Azure AD offre des contrôles sur la possibilité pour les utilisateurs de créer des groupes ou d’affecter des propriétaires dans les portails Azure, ainsi que des paramètres de stratégie d’expiration et de nommage.

Le centre d’administration fournit également plusieurs mesures de contrôle d’invitation invité qui vont au-delà de celle du Centre d'administration Microsoft 365, comme la possibilité de limiter si les non-propriétaires peuvent également inviter des invités.

**SharePoint**

Les sites SharePoint sont créés avec des groupes de sécurité Propriétaire, Membre et Visiteur, les deux premiers correspondant à leurs équivalents de groupe Microsoft 365. Bien que l’appartenance aux sites SharePoint Online soit généralement gérée par le groupe Microsoft 365 associé, il ne s’agit pas d’une relation bidirectionnelle. Les modifications apportées à l’appartenance au niveau du groupe Microsoft 365 sont répercutées dans SharePoint. Toutefois, si l’appartenance est modifiée dans le groupe SharePoint, cela n’est pas reflété dans le groupe Microsoft 365.

### <a name="user-experiences"></a>Expériences utilisateur

Les utilisateurs finaux peuvent créer des groupes à partir de plusieurs services dans Microsoft 365, et dans d’autres, ils peuvent uniquement partager avec un groupe.

Les services suivants permettent la création de groupes par les utilisateurs finaux :

- Outlook
- Planificateur
- Project pour le web
- SharePoint
- Flux
- Microsoft Teams
- Yammer

#### <a name="restriction-of-group-creation"></a>Restriction de la création de groupes

Une approche courante pour contrôler l’étalement des équipes consiste à limiter les utilisateurs qui peuvent les créer. Cela ne peut être fait qu’en limitant la création de groupes. Cela a un impact sur la possibilité de créer des groupes à partir d’autres services où cela peut être nécessaire pour l’utilisateur final. Groupes Microsoft 365 ne prend pas en charge la possibilité de restreindre la création de groupes à partir de certaines applications ou services tout en l’autorisant à partir d’autres.

L’expérience de la restriction de création de groupe varie entre les applications et les services :

|Application ou service|Expérience|
|---|---|
|Outlook|**L’option Nouveau groupe** est supprimée du menu Nouveau dans la page Contacts|
|Planificateur|**Le nouveau plan** explique que la création de groupes a été désactivée et propose d’ajouter le plan à un groupe existant.|
|Projet pour le web et feuille de route|**Le menu Créer un groupe** explique que la création de groupe est restreinte et suggère d’utiliser un groupe existant.|
|SharePoint|Toujours en mesure de créer un site d’équipe qui n’est pas connecté à un groupe.|
|Flux|**L’option Group** n’apparaît pas sous le **menu Créer**.|
|Teams|L’utilisateur ne peut pas créer d’équipe avec un nouveau groupe, mais peut toujours créer une équipe qui utilise un groupe existant.<br><br>**Le bouton Créer une équipe** est remplacé par **Créer une équipe à partir d’un groupe**.|
|Yammer|**L’option Créer un groupe** est supprimée de la navigation groupes/communautés principale.|

## <a name="services-interactions-with-groups"></a>Interactions de services avec des groupes

Consultez l’affiche Groupes dans Microsoft 365 pour plus d’informations sur les différents types de groupes, la façon dont ils sont créés et gérés, ainsi que quelques recommandations de gouvernance.

[![Image miniature pour l’infographie des groupes.](../downloads/msft-m365-groups-architecture-thumb.png)](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf)

[PDF](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf) \| [Visio](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.vsdx)

Le tableau suivant fournit une vue d’ensemble des interactions Groupes Microsoft 365 avec différents services :

|Produit|Fonctionnalités|Le service existe-t-il sans groupe ?|Le service peut-il créer un groupe ?|La suppression de l’instance supprime-t-elle le groupe ?|
|---|---|---|---|---|
|Azure AD|Appartenance, contrôles de groupe, invités|Oui|Oui|Oui|
|Exchange|Calendrier, boîte aux lettres|Oui|Oui|Oui|
|Formulaires|Formulaire|Oui|Non|Non|
|OneNote|Bloc-notes|Oui|Non|Non|
|Planificateur|Tableau des tâches|Non|Oui|Oui|
|Application Power Apps|Application|Oui|Non|Non|
|Power Automate|Flux de travail|Oui|Non|Non|
|Power BI (classique)|Espace de travail|Non|Oui|Oui|
|Power BI (nouveau)|Espace de travail|Oui|Non|Oui|
|Project pour le web|Plan de projet|Oui|Oui|Non|
|Feuille de route|Feuille de route|Oui|Oui|Non|
|SharePoint|Site|Oui|Oui|Oui|
|Flux|Canal, vidéo|Oui|Oui|Oui|
|Teams|Équipe|Non|Oui|Oui|
|Yammer|Group|Oui|Oui|Oui|

Bien que le tableau ci-dessus fournisse une vue d’ensemble générale des interactions de groupe avec les services Microsoft 365, il existe plusieurs nuances et complexités que vous devez comprendre. Les sections suivantes examinent plus en détail les charges de travail spécifiques et leurs interactions avec les groupes.

## <a name="azure-ad"></a>Azure AD

Azure AD fournit les fonctionnalités de gestion des identités sous-jacentes dans Microsoft 365.

**Principales fonctionnalités fournies aux groupes**

- Appartenance aux groupes
- Stratégie de nommage
- Stratégie d’expiration
- Invités
- Restriction de la création de groupes

**Azure AD peut-il créer un groupe ?**

Oui, Groupes Microsoft 365 pouvez être créé à partir d’Azure AD via le portail web d’administration, via PowerShell ou API Graph.

**Azure AD existe-t-il sans groupe ?**

Oui, Azure AD effectue un grand nombre de services qui n’ont aucun rapport avec Groupes Microsoft 365. Chaque groupe Microsoft 365 est représenté en tant qu’objet dans Azure AD.

**Existe-t-il plusieurs instances d’Azure AD par groupe ?**

Non, il n’existe qu’une seule instance d’Azure AD.

**Azure AD peut-il être associé à plusieurs groupes ?**

Oui, car Azure AD est la plateforme sous-jacente qui fournit le service d’appartenance au groupe.

**L’association d’Azure AD à un groupe peut-elle changer ?**

Non, Azure AD est la plateforme sous-jacente où existent des groupes.

**La suppression de l’instance supprime-t-elle le groupe ?**

La suppression du groupe dans Azure AD supprime le contenu et les services associés au groupe concernés.

## <a name="teams"></a>Teams

Teams est un espace de travail centré sur la conversation qui vise à améliorer la collaboration en fournissant une interface unique pour interagir avec différents services Microsoft et tiers.

Par défaut, lorsqu’une équipe est créée, la boîte aux lettres et le calendrier associés au groupe Microsoft 365 sont masqués à la fois dans la liste d’adresses globale dans Exchange et dans Outlook. Cela peut être remplacé manuellement par un administrateur si l’utilisateur souhaite utiliser Outlook et Teams sur le même groupe Microsoft 365.

**Principales fonctionnalités fournies aux groupes**

- Conversations
- Onglets & canaux
- Réunions

**Teams peut-il créer un groupe ?**

Oui, la création d’une équipe crée un groupe Microsoft 365. Il est également possible de créer une équipe pour un groupe existant qui n’en a pas actuellement.

**Les équipes existent-elles sans groupe ?**

Non, il n’est pas possible pour une équipe d’exister sans groupe.

**Peut-il y avoir plusieurs équipes par groupe ?**

Non, la relation entre une équipe et un groupe est 1:1.

**Une équipe peut-elle être associée à plusieurs groupes ?**

Non, l’équipe elle-même ne peut être associée qu’à un seul groupe.

**L’association d’une équipe à un groupe peut-elle changer ?**

Non, l’équipe ne peut être associée qu’au groupe auquel elle était initialement associée.

**La suppression de l’équipe supprime-t-elle le groupe ?**

Oui, la suppression de l’équipe dans Microsoft Teams supprime le groupe, les services associés au groupe et le contenu.

## <a name="exchange"></a>Exchange

Exchange Online fournit la messagerie, le calendrier, le contact et les fonctionnalités associées. Dans le contexte d’un groupe, une seule ressource est associée, par opposition à une instance de service entière.

**Principales fonctionnalités fournies aux groupes**

- Boîte aux lettres et calendrier
- Possibilité d’envoyer un e-mail à tous les membres du groupe
- Stockage des conversations de canal Teams à des fins eDiscovery, commentaires du Planificateur

**Exchange peut-il créer un groupe ?**

Oui, il est possible de créer un groupe à partir du centre d’administration Exchange Online, ainsi qu’à partir d’Outlook. Vous pouvez également convertir des listes de distribution Exchange en groupes Microsoft 365.

**Exchange existe-t-il sans groupe ?**

Oui, Exchange Online fournit plusieurs services, notamment des boîtes aux lettres partagées et des calendriers, sans association de groupe.

**Peut-il y avoir plusieurs instances de boîtes aux lettres ou de calendriers Exchange par groupe ?**

Non, il ne peut y avoir qu’une seule boîte aux lettres et un calendrier Exchange Online pour un groupe.

**Les boîtes aux lettres et les calendriers Exchange peuvent-ils être associés à plusieurs groupes ?**

Non, la boîte aux lettres et le calendrier ont une relation 1:1 avec le groupe. Il est possible de partager la boîte aux lettres avec d’autres utilisateurs ou groupes, mais cela n’établit aucune forme d’association de service.

**L’association de la boîte aux lettres Exchange ou du calendrier à un groupe peut-elle changer ?**

Non, la boîte aux lettres et le calendrier ne peuvent pas être remplacés par un autre groupe. Toutefois, le contenu peut être déplacé d’une boîte aux lettres à une autre dans Outlook ou à l’aide d’un outil tiers.

**La suppression de la boîte aux lettres supprime-t-elle le groupe ?**

Oui, la suppression de la boîte aux lettres dans Exchange supprime le groupe, ainsi que les services et le contenu associés au groupe.

## <a name="forms"></a>Formulaires

Les formulaires fournissent des enquêtes et des questionnaires basés sur le web.

**Principales fonctionnalités fournies aux groupes**

- Propriété des formulaires

**Les formulaires peuvent-ils créer un groupe ?**

Non, Forms ne peut pas créer de groupe.

**Les formulaires existent-ils sans groupe ?**

Oui, les enquêtes et les questionnaires peuvent être créés directement dans le compte d’un utilisateur final.

**Peut-il y avoir plusieurs formulaires par groupe ?**

Oui, plusieurs formulaires peuvent être associés à un groupe.

**Les formulaires peuvent-ils être associés à plusieurs groupes ?**

Non, un formulaire ne peut être associé qu’à un seul groupe.

**L’association d’un formulaire à un groupe peut-elle changer ?**

Non, une fois qu’un formulaire est associé à un groupe (créé directement à l’intérieur ou propriété transférée d’un individu), il ne peut pas être déplacé vers un autre groupe.

**La suppression du formulaire supprime-t-elle le groupe ?**

Non, il n’est pas possible de supprimer un groupe de l’interface Forms, uniquement des formulaires individuels.

## <a name="onenote"></a>OneNote

OneNote est une application de notebook numérique. Le bloc-notes OneNote créé avec un groupe est un fichier dans le site SharePoint associé plutôt qu’un service connecté à un groupe.

**Principales fonctionnalités fournies aux groupes**

- Bloc-notes partagé (stocké dans la bibliothèque SharePoint associée au groupe)

**OneNote peut-il créer un groupe ?**

Non, l’application OneNote ne peut pas créer de groupe.

**Les blocs-notes OneNote existent-ils sans groupe ?**

Oui, les blocs-notes peuvent être créés directement dans OneDrive ou dans d’autres emplacements partagés.

**Peut-il y avoir plusieurs blocs-notes OneNote par groupe ?**

Oui, un bloc-notes est créé par défaut et d’autres peuvent être ajoutés, mais tout lien vers OneNote à partir des services associés au groupe ira toujours au bloc-notes par défaut.

**Un bloc-notes OneNote peut-il être associé à plusieurs groupes ?**

Non, le bloc-notes est stocké dans la bibliothèque de sites SharePoint associée au groupe et lié à partir de différentes interfaces. Il peut toutefois être partagé avec d’autres groupes de la même façon qu’il peut être partagé avec des individus.

**L’association du bloc-notes à un groupe peut-elle changer ?**

Non, le bloc-notes lui-même est associé au groupe et est directement accessible à partir d’autres services connectés au groupe, mais le contenu peut être déplacé d’un bloc-notes vers un autre dans l’application OneNote.

**La suppression du bloc-notes supprime-t-elle le groupe ?**

Non, toutefois, si le bloc-notes OneNote est supprimé, il peut y avoir des liens rompus dans certains services associés au groupe.

## <a name="planner"></a>Planificateur

Planner est un service léger de gestion des tâches de groupe.

**Principales fonctionnalités fournies aux groupes**

- Tableau de gestion des tâches de groupe

**Le Planificateur peut-il créer un groupe ?**

Oui, la création d’un plan crée un groupe.

**Existe-t-il un tableau planificateur sans groupe ?**

Non, un plan doit être associé à un groupe.

**Existe-t-il plusieurs plans par groupe ?**

Oui, il peut y avoir plusieurs plans par groupe.

**Un plan peut-il être associé à plusieurs groupes ?**

Non, un plan s’appuie uniquement sur l’appartenance au groupe pour déterminer l’accès.

**L’association d’un plan à un groupe peut-elle changer ?**

Non, toutefois, la copie d’un plan crée un groupe.

> [!NOTE]
> Un groupe créé par une autre application ne s’affiche pas automatiquement dans le Planificateur pour un utilisateur. Pour accéder au tableau initialement, ils devront l’ouvrir à partir d’une autre interface basée sur un groupe telle qu’Outlook.

**La suppression du plan supprime-t-elle le groupe ?**

Oui, la suppression du plan entraîne la suppression des services et du contenu associés au groupe et au groupe.

## <a name="power-apps"></a>Power Apps

Power Apps fournit un canevas pour le développement d’applications sans code.

**Principales fonctionnalités fournies aux groupes**

- Les applications peuvent être partagées avec un groupe à exécuter et à modifier

**Power Apps peut-il créer un groupe ?**

Non, Power Apps ne peut pas créer de groupe Microsoft 365.

**Power Apps existe-t-il sans groupe ?**

Oui, les applications peuvent être créées dans Power Apps et résider dans le compte créateurs jusqu’à ce qu’elles soient partagées ou publiées.

**Peut-il y avoir plusieurs applications par groupe ?**

Oui, plusieurs applications peuvent être partagées avec un groupe.

**Les applications peuvent-elles être associées à plusieurs groupes ?**

Oui, une application peut être partagée avec plusieurs groupes.

**L’association d’une application à un groupe peut-elle changer ?**

Oui, car l’association entre Power Apps et un groupe Microsoft 365 est partagée uniquement : l’application réside toujours avec le créateur.

> [!IMPORTANT]
> [La sécurité des groupes doit être activée pour que les applications puissent être partagées avec eux](/powerapps/maker/canvas-apps/share-app#share-an-app-with-office-365-groups).

**La suppression de l’application supprime-t-elle le groupe ?**

Non, les applications ne sont pas connectées au groupe autre que d’être partagées avec elles.

## <a name="power-automate"></a>Power Automate

Power Automate (anciennement Microsoft Flow) fournit des flux de travail et des services d’automatisation.

**Principales fonctionnalités fournies aux groupes**

- Les flux de travail peuvent être partagés avec un groupe à exécuter et à modifier.

**Power Automate peut-il créer un groupe ?**

Non, Power Automate ne peut pas créer de groupe Microsoft 365 dans le contexte d’être associé à un groupe.

Il est toutefois possible de créer un flux qui effectue diverses opérations, telles que la création d’un groupe de sécurité Azure AD ou la mise à jour de l’appartenance à un groupe Microsoft 365.

**Les flux existent-ils sans groupe ?**

Oui, les flux peuvent être créés dans Power Automate et résider dans le compte creators jusqu’à ce qu’ils soient partagés ou publiés.

**Peut-il y avoir plusieurs flux par groupe ?**

Oui, plusieurs flux peuvent être partagés avec un groupe.

**Un flux peut-il être associé à plusieurs groupes ?**

Oui, un flux peut être partagé avec plusieurs groupes.

**L’association d’un flux à un groupe peut-elle changer ?**

Oui, car l’association entre Power Automate et un groupe Microsoft 365 est partagée uniquement : le flux réside toujours avec le créateur.

**La suppression d’un flux supprime-t-elle le groupe ?**

Non, comme Power Apps, les flux ne sont pas connectés au groupe autre que d’être partagés avec eux.

## <a name="power-bi-classic"></a>Power BI (classique)

Power BI fournit des tableaux de bord et des rapports interactifs pilotés par les données.

**Principales fonctionnalités fournies aux groupes**

- Création de rapports de données

**Power BI peut-il créer un groupe ?**

Oui, la création d’un espace de travail classique crée un groupe Microsoft 365.

**Existe-t-il un espace de travail Classique Power BI sans groupe ?**

Non, [un espace de travail classique dans Power BI doit être associé à un groupe](/power-bi/collaborate-share/service-collaborate-power-bi-workspace).

**Peut-il y avoir plusieurs espaces de travail Power BI par groupe ?**

Non, la relation entre un espace de travail classique et un groupe est 1:1.

**Un espace de travail peut-il être associé à plusieurs groupes ?**

Techniquement non, alors que l’espace de travail classique est créé avec le groupe, le contenu peut être partagé en dehors du groupe avec des utilisateurs et des groupes de sécurité.

**L’association de l’espace de travail à un groupe peut-elle changer ?**

Non, l’espace de travail classique lui-même est associé au groupe, mais le contenu peut être déplacé d’un espace de travail vers un autre au sein de l’interface Power BI ou en exportant le contenu localement.

**La suppression de l’espace de travail supprime-t-elle le groupe ?**

Oui, la suppression de l’espace de travail dans Power BI supprime les services et le contenu associés aux groupes et aux groupes.

## <a name="power-bi-new"></a>Power BI (nouveau)

Power BI fournit des tableaux de bord et des rapports interactifs pilotés par les données.

Bien que la création d’un espace de travail dans Power BI ne crée pas de groupe Microsoft 365, la création d’un groupe par d’autres moyens crée un espace de travail (non classique) dans Power BI.

**Principales fonctionnalités fournies aux groupes**

- Création de rapports de données

**Power BI peut-il créer un groupe ?**

Non, il n’est pas possible de créer un groupe Microsoft 365 à partir de la nouvelle interface Power BI.

**Le nouvel espace de travail Power BI existe-t-il sans groupe ?**

Oui, il est possible de créer des rapports et des espaces de travail dans Power BI qui ne sont pas associés à des groupes Microsoft 365.

**Peut-il y avoir plusieurs espaces de travail par groupe ?**

Oui, [plusieurs espaces de travail créés par Power BI peuvent être partagés avec un seul groupe](/power-bi/collaborate-share/service-create-the-new-workspaces#give-access-to-your-workspace).

**Un espace de travail peut-il être associé à plusieurs groupes ?**

Non, un espace de travail créé par Power BI ne peut être associé qu’à un seul groupe.

**L’association d’un espace de travail à un groupe peut-elle changer ?**

Oui et non. Un espace de travail créé par Power BI ne peut être associé qu’à un seul groupe à la fois, mais peut modifier l’association à tout moment. Un espace de travail créé dans Power BI par un groupe est associé définitivement à ce groupe.

**La suppression de l’espace de travail supprime-t-elle le groupe ?**

Oui, la suppression de l’espace de travail dans Power BI supprime les services et le contenu associés au groupe et au groupe.

## <a name="project-for-the-web"></a>Project pour le web

Project pour le web offre la possibilité de créer des plans de projet, des diagrammes de Gantt et des feuilles de route.
Fonctionnalités clés fournies aux groupes.

- Plans de projet

**Project pour le web peut-il créer un groupe ?**

Oui, il est possible de créer un groupe Microsoft 365 directement à partir de Project pour le web.

**Les projets existent-ils sans groupe ?**

Oui, les projets peuvent exister sans être associés à un groupe Microsoft 365, mais l’attribution de tâches nécessite une association de groupe.

**Peut-il y avoir plusieurs projets par groupe ?**

Oui, il est possible de connecter plusieurs projets dans un même groupe.

**Le projet peut-il être associé à plusieurs groupes ?**

Non, un projet ne peut être associé qu’à un seul groupe.

**L’association d’un projet à un groupe peut-elle changer ?**

Non, une fois l’association avec un groupe établie, elle ne peut pas changer.

**La suppression du projet supprime-t-elle le groupe ?**

Non, la suppression du projet dans Project pour le web ne supprime pas le groupe.

## <a name="roadmap"></a>Feuille de route

La feuille de route permet de créer des feuilles de route de projet avec Project pour le web et Project Online.

**Principales fonctionnalités fournies aux groupes**

- Feuilles de route du projet

**La feuille de route peut-elle créer un groupe ?**

Oui, il est possible de créer un groupe Microsoft 365 directement à partir de la feuille de route.

**La feuille de route existe-t-elle sans groupe ?**

Oui, les feuilles de route peuvent exister sans être associées à un groupe Microsoft 365, mais le partage de la feuille de route nécessite une association de groupe.

**Existe-t-il plusieurs feuilles de route par groupe ?**

Oui, il est possible de connecter plusieurs feuilles de route à un seul groupe.

**Une feuille de route peut-elle être associée à plusieurs groupes ?**

Non, une feuille de route ne peut être associée qu’à un seul groupe.

**L’association d’une feuille de route à un groupe peut-elle changer ?**

Non, une fois l’association avec un groupe établie, elle ne peut pas changer.

**La suppression de la feuille de route supprime-t-elle le groupe ?**

Non, la suppression de la feuille de route ne supprime pas le groupe.

## <a name="sharepoint"></a>SharePoint

SharePoint est une plateforme de gestion de contenu web qui fournit entre autres des services de stockage pour plusieurs services Microsoft 365.

**Principales fonctionnalités fournies aux groupes**

- Bibliothèque de documents
- Bibliothèque pour le stockage du bloc-notes OneNote
- Stockage de fichiers Wiki Teams

**SharePoint peut-il créer un groupe ?**

Oui, la création d’un site d’équipe dans SharePoint crée un groupe Microsoft 365 par défaut. Il est également possible de créer un groupe et, éventuellement, une équipe pour un site existant.

**Les sites SharePoint existent-ils sans groupe ?**

Oui, SharePoint offre plusieurs services et sites non associés à un groupe, tels que des sites de communication et de hub. 

**Peut-il y avoir plusieurs sites par groupe ?**

Non, il ne peut y avoir qu’un seul site par groupe. Les canaux privés et partagés dans Teams utilisent des sites supplémentaires qui ne sont pas connectés au groupe.

**Les sites peuvent-ils être associés à plusieurs groupes ?**

Techniquement non, mais lorsqu’un site est créé avec un groupe, le contenu peut être partagé avec d’autres groupes.

**L’association d’un site à un groupe peut-elle changer ?**

Non, le site lui-même est associé au groupe, mais le contenu peut être déplacé d’un site à un autre dans l’interface SharePoint, en exportant du contenu localement ou à l’aide d’un outil tiers.

**La suppression du site supprime-t-elle le groupe ?**

Oui, la suppression du site dans SharePoint supprime les services et le contenu associés au groupe et au groupe.

## <a name="stream"></a>Flux

Microsoft Stream est une plateforme d’hébergement et de partage de vidéos.

**Principales fonctionnalités fournies aux groupes**

- Stockage vidéo
- Enregistrement de réunion Teams
- Canaux vidéo

**Stream peut-il créer un groupe ?**

Oui, il est possible de créer un groupe Microsoft 365 directement à partir de Stream.

**Stream existe-t-il sans groupe ?**

Oui, les canaux vidéo et les vidéos peuvent exister dans Stream sans être associés à un groupe.

**Peut-il y avoir plusieurs vidéos et canaux par groupe ?**

Oui, il peut y avoir plusieurs vidéos et canaux dans chaque groupe.

**Une vidéo ou un canal peut-il être associé à plusieurs groupes ?**

Oui, lorsqu’une vidéo ou un canal est créé avec un groupe, il peut être partagé avec d’autres groupes.

**Son association à un groupe peut-elle changer ?**

Oui et non; Dans Stream, les vidéos appartiennent au chargeur ou à l’enregistreur de réunion d’origine et peuvent donc être associées à n’importe quel groupe, mais les canaux vidéo ne peuvent être associés qu’au groupe dans lequel ils ont été créés à l’origine.

**La suppression de vidéos ou de canaux supprime-t-elle le groupe ?**

Non, la suppression de vidéos ou de canaux ne supprime pas le groupe. Toutefois, la suppression du groupe lui-même dans Stream supprime les services et le contenu associés au groupe, à l’exception des vidéos réelles.

## <a name="yammer"></a>Yammer

Yammer est une plateforme sociale d’entreprise conçue pour favoriser l’engagement de la communauté au sein et entre les organisations.

La création d’une communauté (anciennement appelée « groupe ») dans Yammer crée une boîte aux lettres, mais à l’heure actuelle, elle n’est pas utilisée.

Un groupe Microsoft 365 associé à Yammer ne peut pas être utilisé avec une équipe dans Microsoft Teams.

Un groupe Yammer ne peut pas être utilisé avec un espace de travail PowerBI Pro.

**Principales fonctionnalités fournies aux groupes**

- Zone de conversation

**Yammer peut-il créer un groupe Microsoft 365 ?**

Oui, la création d’un groupe dans Yammer crée un groupe Microsoft 365, si les plateformes sont connectées et que l’utilisateur a la possibilité de créer un groupe.

Un groupe Yammer associé à un groupe Microsoft 365 ne peut pas être créé dans une interface ou un service autre que Yammer lui-même.

**Existe-t-il un groupe Yammer sans groupe Microsoft 365 ?**

Oui, il est possible de créer un groupe Yammer sans groupe Microsoft 365.

Si la plateforme Yammer n’est pas connectée à des groupes Microsoft 365 ou si les utilisateurs n’ont pas la possibilité de créer un groupe Microsoft 365, les groupes Yammer sont créés sans association de groupe Microsoft 365.

**Peut-il y avoir plusieurs groupes Yammer par groupe Microsoft 365 ?**

Non, la relation entre un groupe Yammer et un groupe Microsoft 365 est 1:1.

**Un groupe Yammer peut-il être associé à plusieurs groupes Microsoft 365 ?**

Non, le groupe Yammer ne peut être associé qu’à un seul groupe Microsoft 365. Il est possible de partager des publications avec d’autres groupes Yammer ou de les déplacer vers d’autres groupes Yammer.

**L’association d’un groupe Yammer à un groupe Microsoft 365 peut-elle changer ?**

Non, le groupe Yammer ne peut être associé qu’au groupe Microsoft 365 auquel il était initialement associé.

**La suppression du groupe Yammer supprime-t-elle le groupe Microsoft 365 ?**

Oui, la suppression du groupe dans Yammer supprime le contenu et les services associés au groupe Microsoft associés.

## <a name="related-topics"></a>Voir aussi

[Recommandations en matière de planification de la gouvernance de collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)
