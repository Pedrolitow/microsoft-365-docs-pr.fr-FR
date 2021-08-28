---
title: Interactions avec les services de groupes
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
recommendations: false
description: Interactions avec les services de groupes
ms.openlocfilehash: 54d8cd0ff31bad9af4269b3a4d8af23ccb618e16
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58563705"
---
# <a name="groups-services-interactions"></a>Interactions avec les services de groupes

Microsoft 365 Les groupes fournissent une structure commune à un certain nombre de services et de charges de travail au sein de la plateforme Microsoft 365 pour offrir une expérience connectée aux utilisateurs finaux. À la base, un groupe Microsoft 365 existe pour fournir :

- Un moyen de gérer l’appartenance (Azure AD)
- Un lieu de messagerie et de conversations (boîte aux lettres, Exchange, Microsoft Teams, Yammer)
- Un endroit où stocker des fichiers (SharePoint)
- Calendrier à planifier (Exchange)
- Un bloc-notes pour la capture de notes (OneNote)

Au moment de la création du groupe, un certain nombre d’autres ressources sont également mise en service, mais elles ne sont pas visibles tant qu’elles n’ont pas été accédées pour la première fois à partir du service :

- Un tableau pour la gestion des tâches de groupe (Planificateur)
- Espace de travail pour les rapports (Power BI)
- Une zone pour les vidéos partagées (Microsoft Stream)
- Une zone pour les formulaires partagés (formulaires)

Dans Microsoft 365, d’autres services peuvent interagir avec des groupes Microsoft 365 pour fournir des fonctionnalités et des fonctionnalités supplémentaires aux membres du groupe.
Voici quelques exemples :

- Power Apps applications
- Power Automate flux de travail
- Project sur le web et feuille de route pour la gestion de projet en cascade
- Teams pour les conversations basées sur un canal
- Yammer pour les communautés d’intérêt

## <a name="user-interactions-with-groups"></a>Interactions des utilisateurs avec les groupes

Microsoft 365 Les groupes peuvent être créés et gérés à partir d’une variété d’interfaces, à la fois par les administrateurs et les utilisateurs finaux. 

### <a name="administrative-experiences"></a>Expériences administratives

Les administrateurs peuvent créer et gérer des groupes Microsoft 365 à partir de plusieurs centres d’administration de charge de travail, des interfaces de ligne de commande qui gèrent les scripts, ainsi que des applications personnalisées qui interagissent avec l’API Graph. La seule exception à ce problème concerne Yammer groupes , qui doivent être créés à partir de l’interface Yammer web.

**Paramètres associés**

Dans les différentes interfaces d’administration qui peuvent gérer les paramètres de groupe, il existe plusieurs chevauchements que vous devez connaître.

**Centre d’administration Microsoft 365**

Dans la Centre d’administration Microsoft 365, l’accès invité aux groupes est activé par défaut, tout comme la possibilité d’autoriser les propriétaires à ajouter des invités. Aucun autre contrôle au niveau de l’organisation n’est disponible pour les groupes à partir de ce centre d’administration.

**Centre d’administration d’Azure AD**

Le Centre d’administration Azure AD permet de contrôler si les utilisateurs peuvent créer des groupes ou affecter des propriétaires dans les portails Azure, ainsi que des paramètres de stratégie d’expiration et d’affectation de noms.

Le Centre d’administration fournit également un certain nombre de mesures de contrôle d’invitation invité qui vont au-delà de celle du Centre d’administration Microsoft 365, telles que la possibilité de limiter si les non-propriétaires peuvent également inviter des invités

**SharePoint**

SharePoint sites sont créés avec les groupes de sécurité Propriétaire, Membre et Visiteur, les deux premiers correspondant à leurs équivalents Microsoft 365 groupe. Bien que l’appartenance SharePoint sites en ligne soit généralement gérée par le groupe Microsoft 365 associé, il ne s’agit pas d’une relation bidirectionnelle. Les modifications apportées à l’appartenance au niveau du groupe Microsoft 365 sont reflétées dans SharePoint. Toutefois, si l’appartenance est modifiée dans le groupe SharePoint, cela n’est pas reflété dans le groupe Microsoft 365 groupe.

### <a name="user-experiences"></a>Expériences utilisateur

Les utilisateurs finaux peuvent créer des groupes à partir de plusieurs services au sein Microsoft 365, et dans d’autres, ils peuvent uniquement partager avec un groupe.

Les services suivants permettent la création de groupes par les utilisateurs finaux :

- Outlook
- Planificateur
- Project pour le web
- SharePoint
- Flux
- Microsoft Teams
- Yammer

#### <a name="restriction-of-group-creation"></a>Restriction de la création de groupes

Une approche courante pour contrôler l’étendue des équipes consiste à limiter les utilisateurs qui peuvent les créer. Pour ce faire, vous ne pouvez le faire qu’en limitant la création de groupes. Cela a une incidence sur la possibilité de créer des groupes à partir d’autres services lorsque cela peut être nécessaire pour l’utilisateur final. Microsoft 365 Les groupes ne permettent pas de restreindre la création de groupes à partir de certaines applications ou services tout en le permettant à d’autres.

L’expérience de restriction de création de groupe varie selon les applications et les services :

|Application ou service|Expérience|
|---|---|
|Outlook|**L’option** Nouveau groupe est supprimée du menu Nouveau dans la page Personnes|
|Planificateur|**Le nouveau plan** explique que la création de groupe a été désactivée et propose d’ajouter le plan à un groupe existant|
|Project web et feuille de route|**Le** menu Créer un groupe explique que la création de groupe est restreinte et suggère l’utilisation d’un groupe existant.|
|SharePoint|Toujours en mesure de créer un site d’équipe qui n’est pas connecté à un groupe.|
|Flux|**L’option** groupe n’apparaît pas sous **le menu Créer.**|
|Teams|L’utilisateur ne peut pas créer d’équipe avec un nouveau groupe, mais peut toujours créer une équipe qui utilise un groupe existant.<br><br>**Créer un bouton d’équipe** est remplacé par **Créer une équipe à partir d’un groupe.**|
|Yammer|**L’option Créer un** groupe est supprimée de la navigation groupes/communautés principale.|

## <a name="services-interactions-with-groups"></a>Interactions des services avec les groupes

Consultez l’affiche Groupes Microsoft 365 pour plus d’informations sur les différents types de groupes, la façon dont ils sont créés et gérés, ainsi que quelques recommandations de gouvernance.

[![Image miniature pour l’infographie des groupes.](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf)

[PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx)

Le tableau suivant fournit une vue d’ensemble des interactions Microsoft 365 groupes avec différents services :

|Produit|Fonctionnalités|Fait le service<br>existe-t-il sans groupe ?|Le service peut-il<br>créer un groupe|La suppression de la<br>supprimer le groupe ?|
|---|---|---|---|---|
|Azure AD|Appartenance, contrôles de groupe, invités|Oui|Oui|Oui|
|Exchange|Calendrier, boîte aux lettres|Oui|Oui|Oui|
|Formulaires|Formulaire|Oui|Non|Non|
|OneNote|Bloc-notes|Oui|Non|Non|
|Planificateur|Tableau des tâches|Non|Oui|Oui|
|Power Apps application|Application|Oui|Non|Non|
|Power Automate|Flux de travail|Oui|Non|Non|
|Power BI (classique)|Espace de travail|Non|Oui|Oui|
|Power BI (nouveau)|Espace de travail|Oui|Non|Oui|
|Project pour le web|Project plan|Oui|Oui|Non|
|Feuille de route|Feuille de route|Oui|Oui|Non|
|SharePoint|Site|Oui|Oui|Oui|
|Flux|Canal, vidéo|Oui|Oui|Oui|
|Teams|Équipe|Non|Oui|Oui|
|Yammer|Group|Oui|Oui|Oui|

Bien que le tableau ci-dessus offre une vue d’ensemble des interactions de groupe avec les services Microsoft 365, il existe un certain nombre de nuances et de complexités que vous devez comprendre. Les sections suivantes analysent de façon plus approfondie les charges de travail spécifiques et leurs interactions avec les groupes.

## <a name="azure-ad"></a>Azure AD

Azure AD fournit les fonctionnalités de gestion des identités sous-jacentes dans Microsoft 365.

**Fonctionnalités clés fournies aux groupes**

- Appartenance aux groupes
- Stratégie d’attribution de noms
- Stratégie d’expiration
- Invités
- Restriction de la création de groupes

**Azure AD peut-il créer un groupe ?**

Oui, Microsoft 365 groupes peuvent être créés à partir d’Azure AD via le portail web d’administration, via PowerShell ou Graph API.

**Azure AD existe-t-il sans groupe ?**

Oui, Azure AD effectue un grand nombre de services qui n’ont aucune relation avec Microsoft 365 groupes. Chaque Microsoft 365 groupe est représenté en tant qu’objet dans Azure AD.

**Existe-t-il plusieurs instances d’Azure AD par groupe ?**

Non, il n’existe qu’une seule instance d’Azure AD.

**Azure AD peut-il être associé à plusieurs groupes ?**

Oui, car Azure AD est la plateforme sous-jacente qui fournit le service d’appartenance au groupe.

**L’association d’Azure AD à un groupe peut-elle changer ?**

Non, Azure AD est la plateforme sous-jacente où les groupes existent.

**La suppression de l’instance supprime-t-elle le groupe ?**

La suppression du groupe dans Azure AD supprimera les services et le contenu associés au groupe appropriés.

## <a name="teams"></a>Teams

Teams est un espace de travail centré sur la conversation visant à améliorer la collaboration en fournissant une interface unique permettant d’interagir avec divers services Microsoft et tiers.

Par défaut, lorsqu’une équipe est créée, la boîte aux lettres et le calendrier associés au groupe Microsoft 365 sont masqués à la fois dans la liste d’adresses globale dans Exchange, ainsi que dans Outlook. Un administrateur peut le faire manuellement si l’utilisateur souhaite utiliser à la fois Outlook et Teams sur le même groupe Microsoft 365 client.

**Fonctionnalités clés fournies aux groupes**

- Conversations
- Onglets & canaux
- Réunions

**Pouvez Teams créer un groupe ?**

Oui, la création d’une équipe crée un groupe Microsoft 365 groupe. Il est également possible de créer une équipe pour un groupe existant qui n’en possède pas actuellement.

**Les équipes existent-elles sans groupe ?**

Non, il n’est pas possible qu’une équipe existe sans groupe.

**Peut-il y avoir plusieurs équipes par groupe ?**

Non, la relation entre une équipe et un groupe est 1:1.

**Une équipe peut-elle être associée à plusieurs groupes ?**

Non, l’équipe elle-même ne peut être associée qu’à un seul groupe.

**L’association d’une équipe à un groupe peut-elle changer ?**

Non, l’équipe ne peut être associée qu’au groupe auquel elle a été initialement associée.

**La suppression de l’équipe supprime-t-elle le groupe ?**

Oui, la suppression de l’équipe dans Microsoft Teams supprimera le groupe, les services associés au groupe et le contenu.

## <a name="exchange"></a>Exchange

Exchange Online la messagerie, le calendrier, les contacts et les fonctionnalités associées. Dans le contexte d’un groupe, une seule ressource est associée, par opposition à une instance de service entière.

**Fonctionnalités clés fournies aux groupes**

- Boîte aux lettres et calendrier
- Possibilité d’envoyer un e-mail à tous les membres du groupe
- Stockage conversations Teams canal à des fins eDiscovery, commentaires du Planificateur

**Pouvez Exchange créer un groupe ?**

Oui, il est possible de créer un groupe à partir du centre d’administration Exchange Online, ainsi que de Outlook. Vous pouvez également convertir des listes Exchange distribution en listes Microsoft 365 groupes.

**Existe-Exchange existe-t-il sans groupe ?**

Oui, Exchange Online fournit un certain nombre de services, notamment des boîtes aux lettres et des calendriers partagés, sans association de groupe.

**Peut-il y avoir plusieurs instances de boîtes Exchange ou de calendriers par groupe ?**

Non, il ne peut y avoir qu’un seul Exchange Online boîte aux lettres et calendrier pour un groupe.

**Les Exchange boîtes aux lettres et les calendriers peuvent-ils être associés à plusieurs groupes ?**

Non, la boîte aux lettres et le calendrier ont une relation 1:1 avec le groupe. Il est possible de partager la boîte aux lettres avec d’autres utilisateurs ou groupes, mais cela n’établit aucune forme d’association de service.

**L’association Exchange boîte aux lettres ou du calendrier à un groupe peut-elle changer ?**

Non, la boîte aux lettres et le calendrier ne peuvent pas être modifiés dans un autre groupe. Toutefois, le contenu peut être déplacé d’une boîte aux lettres à une autre au sein Outlook ou à l’aide d’un outil tiers.

**La suppression de la boîte aux lettres supprime-t-elle le groupe ?**

Oui, la suppression de la boîte aux lettres dans Exchange supprimera le groupe, ainsi que les services et le contenu associés au groupe.

## <a name="forms"></a>Formulaires

Les formulaires fournissent des questionnaires et des enquêtes web.

**Fonctionnalités clés fournies aux groupes**

- Propriété des formulaires

**Les formulaires peuvent-ils créer un groupe ?**

Non, les formulaires ne peuvent pas créer de groupe.

**Les formulaires existent-ils sans groupe ?**

Oui, les enquêtes et les questionnaires peuvent être créés directement dans le compte d’un utilisateur final.

**Y a-t-il plusieurs formulaires par groupe ?**

Oui, plusieurs formulaires peuvent être associés à un groupe.

**Les formulaires peuvent-ils être associés à plusieurs groupes ?**

Non, un formulaire ne peut être associé qu’à un seul groupe.

**L’association d’un formulaire à un groupe peut-elle changer ?**

Non, une fois qu’un formulaire est associé à un groupe (créé directement dans ou propriété transférée à partir d’un individu), il ne peut pas être déplacé vers un autre groupe.

**La suppression du formulaire supprime-t-elle le groupe ?**

Non, il n’est pas possible de supprimer un groupe de l’interface Forms, uniquement des formulaires individuels.

## <a name="onenote"></a>OneNote

OneNote est une application de bloc-notes numérique. Le OneNote bloc-notes créé avec un groupe est un fichier dans le site SharePoint associé plutôt qu’un service connecté à un groupe.

**Fonctionnalités clés fournies aux groupes**

- Bloc-notes partagé (stocké dans la bibliothèque de SharePoint associée au groupe)

**Pouvez OneNote créer un groupe ?**

Non, l’application OneNote ne peut pas créer de groupe.

**Existe-OneNote blocs-notes sans groupe ?**

Oui, les blocs-notes peuvent être créés directement dans OneDrive ou dans d’autres emplacements partagés.

**Y a-t-il OneNote blocs-notes par groupe ?**

Oui, un bloc-notes est créé par défaut et d’autres peuvent être ajoutés, mais n’importe quel lien vers OneNote à partir des services associés à un groupe sera toujours vers le bloc-notes par défaut.

**Un bloc-OneNote peut-il être associé à plusieurs groupes ?**

Non, le bloc-notes est stocké dans la bibliothèque de SharePoint de sites associée au groupe et lié à partir de différentes interfaces. Il peut toutefois être partagé avec d’autres groupes de la même manière qu’avec des individus.

**L’association du bloc-notes à un groupe peut-elle changer ?**

Non, le bloc-notes lui-même est associé au groupe et est directement accessible à partir d’autres services connectés à un groupe, mais le contenu peut être déplacé d’un bloc-notes à un autre au sein de l’application OneNote.

**La suppression du bloc-notes supprime-t-elle le groupe ?**

Non, toutefois, si le bloc-OneNote est supprimé, il se peut que des liens rompus soient rompus dans certains services associés à un groupe.

## <a name="planner"></a>Planificateur

Le Planificateur est un service de gestion des tâches de groupe léger.

**Fonctionnalités clés fournies aux groupes**

- Tableau de gestion des tâches de groupe

**Le Planificateur peut-il créer un groupe ?**

Oui, la création d’un plan crée un groupe.

**Existe-t-il un tableau du Planificateur sans groupe ?**

Non, un plan doit être associé à un groupe.

**Existe-t-il plusieurs plans par groupe ?**

Oui, il peut y avoir plusieurs plans par groupe.

**Un plan peut-il être associé à plusieurs groupes ?**

Non, un plan s’appuie uniquement sur l’appartenance au groupe pour déterminer l’accès.

**L’association d’un plan à un groupe peut-elle changer ?**

Non, toutefois, la copie d’un plan crée un groupe.

> [!NOTE]
> Un groupe créé par une autre application ne s’affiche pas automatiquement dans le Planificateur pour un utilisateur. Pour accéder au tableau initialement, ils devront l’ouvrir à partir d’une autre interface basée sur un groupe telle que Outlook.

**La suppression du plan supprime-t-elle le groupe ?**

Oui, la suppression du plan supprimera les services et le contenu associés au groupe et au groupe.

## <a name="power-apps"></a>Power Apps

Power Apps fournit un canevas pour le développement d’applications sans code.

**Fonctionnalités clés fournies aux groupes**

- Les applications peuvent être partagées avec un groupe à exécuter et à modifier

**Pouvez Power Apps créer un groupe ?**

Non, Power Apps ne peut pas créer Microsoft 365 groupe.

**Existe-Power Apps existe-t-il sans groupe ?**

Oui, les applications peuvent être créées au sein Power Apps et résident dans le compte créateurs jusqu’à ce qu’elles soient partagées ou publiées.

**Y a-t-il plusieurs applications par groupe ?**

Oui, il peut y avoir plusieurs applications partagées avec un groupe.

**Les applications peuvent-ils être associées à plusieurs groupes ?**

Oui, une application peut être partagée avec plusieurs groupes.

**L’association d’une application à un groupe peut-elle changer ?**

Oui, car l’association entre Power Apps et un groupe Microsoft 365 partage uniquement : l’application réside toujours avec le créateur.

> [!IMPORTANT]
> [La sécurité des groupes doit être activée pour que les applications soient partagées avec eux.](/powerapps/maker/canvas-apps/share-app#share-an-app-with-office-365-groups)

**La suppression de l’application supprime-t-elle le groupe ?**

Non, les applications ne sont pas connectées au groupe autrement que d’être partagées avec eux.

## <a name="power-automate"></a>Power Automate

Power Automate (anciennement appelé Microsoft Flow) fournit des flux de travail et des services d’automatisation.

**Fonctionnalités clés fournies aux groupes**

- Les flux de travail peuvent être partagés avec un groupe à exécuter et à modifier.

**Pouvez Power Automate créer un groupe ?**

Non, Power Automate ne peut pas créer Microsoft 365 groupe dans le contexte d’être associé à un groupe.

Il est toutefois possible de créer un flux qui effectue diverses opérations, telles que la création d’un groupe de sécurité Azure AD ou la mise à jour de l’appartenance à un Microsoft 365 groupe.

**Existe-t-il des flux sans groupe ?**

Oui, les flux peuvent être créés au sein Power Automate et résider dans le compte créateurs jusqu’à ce qu’ils soient partagés ou publiés.

**Peut-il y avoir plusieurs flux par groupe ?**

Oui, il peut y avoir plusieurs flux partagés avec un groupe.

**Un flux peut-il être associé à plusieurs groupes ?**

Oui, un flux peut être partagé avec plusieurs groupes.

**L’association d’un flux à un groupe peut-elle changer ?**

Oui, car l’association entre Power Automate et un groupe Microsoft 365 partage uniquement : le flux réside toujours avec le créateur.

**La suppression d’un flux supprime-t-elle le groupe ?**

Non, comme Power Apps, les flux ne sont pas connectés au groupe autrement que d’être partagés avec eux.

## <a name="power-bi-classic"></a>Power BI (classique)

Power BI fournit des tableaux de bord et des rapports interactifs pilotés par les données.

**Fonctionnalités clés fournies aux groupes**

- Rapports de données

**Pouvez Power BI créer un groupe ?**

Oui, la création d’un espace de travail classique crée un Microsoft 365 groupe.

**Existe-t-Power BI un espace de travail classique sans groupe ?**

Non, [un espace de travail classique dans Power BI doit être associé à un groupe.](/power-bi/collaborate-share/service-collaborate-power-bi-workspace)

**Peut-il y avoir plusieurs Power BI de travail par groupe ?**

Non, la relation entre un espace de travail classique et un groupe est 1:1.

**Un espace de travail peut-il être associé à plusieurs groupes ?**

Techniquement non, alors que l’espace de travail classique est créé avec le groupe, le contenu peut être partagé en dehors du groupe avec des utilisateurs et des groupes de sécurité.

**L’association de l’espace de travail à un groupe peut-elle changer ?**

Non, l’espace de travail classique lui-même est associé au groupe, mais le contenu peut être déplacé d’un espace de travail à un autre au sein de l’interface Power BI ou en exportant du contenu localement.

**La suppression de l’espace de travail supprime-t-elle le groupe ?**

Oui, la suppression de l’espace de travail dans Power BI supprimera les services et le contenu associés aux groupes et aux groupes.

## <a name="power-bi-new"></a>Power BI (nouveau)

Power BI fournit des tableaux de bord et des rapports interactifs pilotés par les données.

Bien que la création d’un espace de travail dans Power BI ne crée pas de groupe Microsoft 365, la création d’un groupe par d’autres moyens crée un nouvel espace de travail (et non classique) dans Power BI.

**Fonctionnalités clés fournies aux groupes**

- Rapports de données

**Pouvez Power BI créer un groupe ?**

Non, il n’est pas possible de créer un groupe Microsoft 365 à partir de la nouvelle interface Power BI’interface.

**Le nouvel espace Power BI de travail existe-t-il sans groupe ?**

Oui, il est possible de créer des rapports et des espaces de travail dans des Power BI qui ne sont pas associés à Microsoft 365 groupes.

**Peut-il y avoir plusieurs espaces de travail par groupe ?**

Oui, [plusieurs espaces de travail créés par Power BI peuvent être partagés avec un seul groupe.](/power-bi/collaborate-share/service-create-the-new-workspaces#give-access-to-your-workspace)

**Un espace de travail peut-il être associé à plusieurs groupes ?**

Non, un espace de travail créé par Power BI ne peut être associé qu’à un seul groupe.

**L’association d’un espace de travail à un groupe peut-elle changer ?**

Oui et non. Un espace de travail créé par Power BI ne peut être associé qu’à un seul groupe à la fois, mais peut modifier l’association à tout moment. Un espace de travail créé dans Power BI par un groupe est associé définitivement à ce groupe.

**La suppression de l’espace de travail supprime-t-elle le groupe ?**

Oui, la suppression de l’espace de travail dans Power BI supprimera le groupe et les services et le contenu associés au groupe.

## <a name="project-for-the-web"></a>Project pour le web

Project web offre la possibilité de créer des plans de projet, des diagrammes de Gantt et des feuilles de route.
Fonctionnalités clés fournies aux groupes.

- Project plans

**Est-Project pour le web de créer un groupe ?**

Oui, il est possible de créer un groupe de Microsoft 365 directement à partir Project pour le web.

**Les projets existent-ils sans groupe ?**

Oui, les projets peuvent exister sans être associés à un groupe Microsoft 365, mais l’affectation de tâches nécessite une association de groupe.

**Peut-il y avoir plusieurs projets par groupe ?**

Oui, il est possible de connecter plusieurs projets dans un même groupe.

**Le projet peut-il être associé à plusieurs groupes ?**

Non, un projet ne peut être associé qu’à un seul groupe.

**L’association d’un projet à un groupe peut-elle changer ?**

Non, une fois l’association avec un groupe établie, elle ne peut pas changer.

**La suppression du projet supprime-t-elle le groupe ?**

Non, la suppression du projet dans Project web ne supprime pas le groupe.

## <a name="roadmap"></a>Feuille de route

La feuille de route offre la possibilité de créer des feuilles de route de projet Project pour le web et Project Online.

**Fonctionnalités clés fournies aux groupes**

- Project feuilles de route

**La feuille de route peut-elle créer un groupe ?**

Oui, il est possible de créer un groupe de Microsoft 365 directement à partir de la feuille de route.

**La feuille de route existe-t-elle sans groupe ?**

Oui, les feuilles de route peuvent exister sans être associées à un groupe Microsoft 365, mais le partage de la feuille de route nécessite une association de groupe.

**Peut-il y avoir plusieurs feuilles de route par groupe ?**

Oui, il est possible de connecter plusieurs feuilles de route à un seul groupe.

**Une feuille de route peut-elle être associée à plusieurs groupes ?**

Non, une feuille de route ne peut être associée qu’à un seul groupe.

**L’association d’une feuille de route à un groupe peut-elle changer ?**

Non, une fois l’association avec un groupe établie, elle ne peut pas changer.

**La suppression de la feuille de route supprime-t-elle le groupe ?**

Non, la suppression de la feuille de route ne supprime pas le groupe.

## <a name="sharepoint"></a>SharePoint

SharePoint est une plateforme de gestion de contenu web qui fournit, entre autres, des services de stockage pour un certain nombre de services Microsoft 365 web.

**Fonctionnalités clés fournies aux groupes**

- Bibliothèque de documents
- Bibliothèque pour le stockage du bloc-OneNote portable
- Stockage de Teams wiki

**Pouvez SharePoint créer un groupe ?**

Oui, la création d’un site d’équipe SharePoint créera un groupe Microsoft 365 par défaut. Il est également possible de créer un groupe et, éventuellement, une équipe pour un site existant.

**Existe-SharePoint sites sans groupe ?**

Oui, SharePoint offre un certain nombre de services et sites non associés à un groupe, tels que des sites de communication et de hub. 

**Peut-il y avoir plusieurs sites par groupe ?**

Non, il ne peut y avoir qu’un seul site par groupe. Les canaux privés Teams utiliser des sites supplémentaires qui ne sont pas connectés au groupe.

**Les sites peuvent-ils être associés à plusieurs groupes ?**

Techniquement non, mais pendant la création d’un site avec un groupe, le contenu peut être partagé avec d’autres groupes.

**L’association d’un site à un groupe peut-elle changer ?**

Non, le site lui-même est associé au groupe, mais le contenu peut être déplacé d’un site à un autre au sein de l’interface SharePoint, en exportant du contenu localement ou à l’aide d’un outil tiers.

**La suppression du site supprime-t-elle le groupe ?**

Oui, la suppression du site dans SharePoint supprimera les services et le contenu associés aux groupes et aux groupes.

## <a name="stream"></a>Flux

Microsoft Stream est une plateforme d’hébergement et de partage de vidéos.

**Fonctionnalités clés fournies aux groupes**

- Stockage vidéo
- Teams enregistrement de réunion
- Canaux vidéo

**Stream peut-il créer un groupe ?**

Oui, il est possible de créer un groupe de Microsoft 365 directement à partir de Stream.

**Stream existe-t-il sans groupe ?**

Oui, les canaux et vidéos vidéo peuvent exister dans Stream sans être associés à un groupe.

**Peut-il y avoir plusieurs vidéos et canaux par groupe ?**

Oui, il peut y avoir plusieurs vidéos et canaux dans chaque groupe.

**Une vidéo ou un canal peut-il être associé à plusieurs groupes ?**

Oui, alors qu’une vidéo ou un canal est créé avec un groupe, il peut être partagé avec d’autres groupes.

**Son association à un groupe peut-elle changer ?**

Oui et non ; Les vidéos dans Stream sont la propriété du téléchargeur ou de l’enregistreur de réunion d’origine et peuvent donc être associées à n’importe quel groupe, mais les canaux vidéo peuvent uniquement être associés au groupe dans qui ils ont été créés à l’origine.

**La suppression de vidéos ou de canaux supprime-t-elle le groupe ?**

Non, la suppression de vidéos ou de canaux ne supprime pas le groupe. Toutefois, la suppression du groupe lui-même dans Stream supprimera les services et le contenu associés au groupe, à l’exception des vidéos réelles.

## <a name="yammer"></a>Yammer

Yammer est une plateforme sociale d’entreprise conçue pour favoriser l’engagement de la communauté au sein et entre les organisations.

La création d’une communauté (anciennement appelée « groupe ») dans Yammer crée une boîte aux lettres, mais elle n’est pas utilisée pour le moment.

Un groupe Microsoft 365 associé à un Yammer ne peut pas être utilisé avec une équipe dans Microsoft Teams.

**Fonctionnalités clés fournies aux groupes**

- Zone de conversation

**Pouvez Yammer créer un groupe Microsoft 365'équipe ?**

Oui, la création d’un groupe dans Yammer crée un groupe Microsoft 365, si les plateformes sont connectées et si l’utilisateur a la possibilité de créer un groupe.

Un groupe Yammer avec un groupe Microsoft 365 associé ne peut pas être créé dans une interface ou un service autre que Yammer lui-même.

**Un groupe Yammer existe-t-il sans groupe Microsoft 365 de données ?**

Oui, il est possible de créer un groupe Yammer sans groupe Microsoft 365 groupe.

Si la plateforme Yammer n’est pas connectée à des groupes Microsoft 365 ou si les utilisateurs n’ont pas la possibilité de créer un groupe Microsoft 365, les groupes Yammer sont créés sans association Microsoft 365 groupe.

**Peut-il y avoir plusieurs groupes Yammer par Microsoft 365 groupe ?**

Non, la relation entre un groupe Yammer et un groupe Microsoft 365 est 1:1.

**Un groupe Yammer peut-il être associé à plusieurs groupes Microsoft 365'utilisateurs ?**

Non, le groupe Yammer ne peut être associé qu’à un seul Microsoft 365 groupe. Il est possible de partager des billets avec d’autres groupes de Yammer ou de les déplacer vers ceux-ci.

**L’association Yammer’un groupe de Microsoft 365 peut-elle changer ?**

Non, le groupe Yammer ne peut être associé qu’au groupe de Microsoft 365 auquel il a été initialement associé.

**La suppression du groupe de Yammer supprime-t-elle le Microsoft 365 groupe ?**

Oui, la suppression du groupe dans Yammer supprimera le contenu et les services associés au groupe Microsoft associés.

## <a name="related-topics"></a>Voir aussi

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)
