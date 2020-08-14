---
title: Fin des options de cycle de vie pour les groupes, les équipes et Yammer
ms.reviewer: mmclean
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
ms.custom:
- M365solutions
f1.keywords: NOCSH
description: Fin des options de cycle de vie pour les groupes, les équipes et Yammer.
ms.openlocfilehash: ab06f06cc65614ee313892a026c2f482d641791f
ms.sourcegitcommit: 66f1f430b3dcae5f46cb362a32d6fb7da4cff5c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "46662595"
---
# <a name="end-of-lifecycle-options-for-groups-teams-and-yammer"></a>Fin des options de cycle de vie pour les groupes, les équipes et Yammer

Les groupes Microsoft 365 et Microsoft teams fonctionnent avec un grand nombre de services connectés. Lors de la suppression d’un groupe ou d’une équipe, la plupart des informations des services connectés sont également supprimées. Cet article décrit les options de conservation des informations en les déplacant du groupe ou de l’équipe avant la suppression.

Une pratique courante pour les groupes ou les équipes qui ne sont plus nécessaires est de déplacer les fichiers de l’équipe et de les stocker à un autre emplacement, tel qu’une bibliothèque de documents SharePoint qui fait office de référentiel ou d’archive. Cette pratique est basée sur un style hérité de travail où les informations sont stockées dans des fichiers et des dossiers, et les communications sont effectuées par courrier électronique.

Le tableau suivant décrit les services associés aux groupes et aux équipes et les types de contenu clés trouvés dans chacun d’eux :

|Service|Types de contenu|
|:------|:---------------|
|Teams|Conversations de canal, fichiers dans les canaux|
|Formulaires|Structure et résultats de l’enquête|
|OneNote|Bloc-notes|
|Outlook|Courrier et calendrier|
|Planificateur|Informations sur l’État et la tâche du projet|
|Power Automate|Flux de travail|
|Power BI|Données, rapports et tableaux de bord|
|Projet sur le Web|Plans de projet|
|Feuille de route|Feuilles de route|
|SharePoint|Fichiers, listes, teams wiki Channel Data|
|Stream|Vidéos|
|Yammer|Conversations|

Lors de la suppression d’un groupe ou d’une équipe, la plupart des ressources associées sont également supprimées. Parmi les exceptions, citons les vidéos en flux, dont elles sont conservées et qui sont toujours détenues par la personne qui les a chargées/enregistrées, à l’instar des flux de puissance automatique. Les données de projet et de feuille de route dans Project sur le Web sont conservées dans les CD et peuvent être restaurées séparément.

Les groupes et les équipes demeurent dans un état de suppression récupérable pendant 30 jours et peuvent être restaurés à tout moment. Toutefois, au bout des 30 jours, les ressources associées, telles que les services et le contenu, sont entièrement purgées de l’environnement Microsoft 365. Tout contenu protégé par une stratégie de rétention reste disponible via des recherches de découverte électronique.

## <a name="end-of-life-cycle-considerations-for-group-connected-services"></a>Considérations relatives à la fin du cycle de vie des services connectés à un groupe

Les propriétaires d’équipes et de groupes et les administrateurs informatiques doivent prendre en compte trois éléments clés lors de la suppression d’un groupe ou d’une équipe.

**Content**

Le contenu doit-il être conservé une fois que l’équipe n’est plus fonctionnelle ou en présence ? Est-il suffisant de reposer sur les capacités de rétention de Microsoft 365, ou est-ce qu’il s’agit d’une partie du contenu dans les applications et les services qui n’offrent pas de rétention ? Le contenu doit-il être conservé à des fins de gestion des enregistrements, à des fins d’archivage ou à des fins d’utilisation ultérieure et de référence ?

Ces questions doivent être posées avant l’archivage ou la suppression d’une équipe, afin d’éviter toute perte de données potentielle.

**Services**

Sur le contenu de plusieurs applications et services, doivent-ils rester dans leur formulaire de travail actuel ? Par exemple, le rapport Power BI doit continuer à être accessible, les résultats de formulaire doivent être disponibles dans l’affichage de synthèse visuelle, les listes dans SharePoint sont-elles liées ou incorporées n’importe où ?

À l’instar des considérations de contenu, ces questions doivent être posées avant la suppression du groupe sous-jacent, car l’exportation du contenu n’est peut-être pas suffisante.

**Interdire**

Lorsque les invités sont invités à une équipe, le flux de travail crée leur identité dans Azure Active Directory de l’organisation hôte avant de les ajouter à l’équipe. Lorsqu’une équipe est supprimée, les invités ne sont pas supprimés d’Azure Active Directory et, en tant que tel, existent toujours dans l’environnement Microsoft Teams. Alors que les invités ne peuvent pas accéder à des groupes, des sites, des équipes ou du contenu qui n’a pas été partagé avec eux, ils peuvent toujours utiliser les fonctionnalités de Microsoft Teams, telles que l’initiation des conversations, les appels vocaux et vidéo et l’utilisation des applications.

Un propriétaire d’équipe ou de groupe peut inviter un utilisateur externe à devenir invité dans Azure Active Directory, à l’ajouter à l’équipe, ainsi qu’à le supprimer de l’équipe. Toutefois, un propriétaire d’équipe ne peut pas supprimer l’invité d’Azure Active Directory : cela peut être effectué uniquement par un administrateur général ou un administrateur d’utilisateur.

Par conséquent, il est important d’effectuer des révisions invitées, mais aussi de savoir si les invités doivent être supprimés d’Azure Active Directory lors de la suppression de l’équipe. Il peut y avoir un cas valide que les invités restent dans l’annuaire, comme s’ils sont membres d’une ou plusieurs autres équipes ou si vous utilisez d’autres services Microsoft 365 ou Azure.

## <a name="teams"></a>Teams

Le contenu spécifique à teams est principalement sous la forme de conversations.

Les conversations dans les canaux ne peuvent pas être copiées ou déplacées à l’aide de la fonctionnalité Microsoft teams native. Elles peuvent toutefois être exportées à l’aide de l’API Graph.

En outre, si une stratégie de rétention est appliquée à Teams, les conversations sont conservées et disponibles via des recherches de découverte électronique. (Les éléments trouvés dans les recherches de découverte électronique peuvent être exportés, mais il n’existe aucun contexte ni structure de leur source d’origine, mais il s’agit simplement de messages individuels.)

### <a name="archiving-a-team"></a>Archivage d’une équipe

L’avantage de l' [archivage d’une équipe](https://docs.microsoft.com/microsoftteams/archive-or-delete-a-team) est qu’elle offre un accès complet à l’équipe tel qu’elle était, afin que les utilisateurs puissent toujours parcourir les conversations de canal et ouvrir des fichiers même s’ils ne sont pas actifs. En outre, les équipes peuvent ne pas être archivées s’il est nécessaire de continuer à les utiliser (comme dans le cas d’une extension de projet).

Lorsqu’une équipe est archivée par un propriétaire, elle est définie en lecture seule pour les membres à la fois pour le contenu au sein de l’équipe et, si cette option est sélectionnée, le site SharePoint associé. L’objectif de cette action est de s’assurer que les conversations dans les canaux sont conservées dans leur état actuel, ainsi qu’avec du contenu SharePoint tel que des fichiers et des wikis.

Dans le site SharePoint, il n’y a pas de modifications visibles, cependant aucune modification ne peut être apportée à des fichiers ou des listes, car le groupe d’autorisations SharePoint pour le groupe Microsoft 365 est défini sur le niveau des visiteurs du site. Cela inclut le bloc-notes OneNote pour l’équipe, car il est stocké dans la bibliothèque d’éléments de site dans le site SharePoint.

Lorsqu’une équipe est archivée, le groupe Microsoft 365 sous-jacent est toujours soumis à la stratégie d’expiration (si elle est définie) et, en tant que tel, le propriétaire doit continuer à renouveler l’équipe.

Lorsque les conversations de canal de l’équipe et le contenu du site SharePoint sont définis en lecture seule, le même n’est pas appliqué à d’autres services associés :

- Les compartiments et les tâches du planificateur peuvent toujours être créés, modifiés et supprimés.
- Les formulaires peuvent toujours recevoir des envois
- La boîte aux lettres Outlook peut toujours recevoir des courriers électroniques
- Les tableaux de bord, les rapports et les données Power BI peuvent toujours être modifiés
- Les projets et les feuilles de route peuvent toujours être modifiés dans Project sur le Web
- Les vidéos peuvent toujours être téléchargées, modifiées et supprimées dans Stream
- Les flux de Power automate peuvent toujours être créés, modifiés, supprimés et continuer à être exécutés (ils échoueront Toutefois, si nécessaire pour publier un message sur un canal de l’équipe archivée).

## <a name="forms"></a>Formulaires

Lorsqu’un formulaire peut être déplacé d’un compte individuel vers un groupe, il ne peut pas être déplacé ou copié d’un groupe à un autre. Il existe trois options pour un formulaire lorsqu’une équipe est supprimée.

**Dupliquer le formulaire**

Les formulaires peuvent être [partagés sous forme de modèles](https://support.microsoft.com/office/82ea9d8a-260a-47a0-afdb-497f3d746e3f), ce qui permet à d’autres utilisateurs de le copier dans leur propre compte ou dans un groupe. Cette opération ne conserve pas les données des envois de résultats ; seule structure de formulaire, comme des questions et des paramètres.

**Exporter les résultats vers une feuille de calcul**

Si les données des réponses de formulaire doivent être conservées, vous pouvez les obtenir en [exportant les résultats vers une feuille de calcul Excel](https://support.office.com/article/02859424-341d-406f-b32a-9a0fbaf357af). Cette opération exportera uniquement les questions et leurs réponses sous forme de données : elle n’inclut pas les graphiques créés par les formulaires.


**Supprimer le formulaire**

Alors que la suppression du groupe entraînera également la suppression de tous les formulaires associés, les membres du groupe peuvent [directement les supprimer](https://support.microsoft.com/office/2207e468-ce1b-4c4a-a256-caf631d87af0) sans être propriétaires du groupe, mais il s’agit d’une étape manuelle qui ne fournit pas d’autres avantages.

## <a name="onenote"></a>OneNote

Le bloc-notes OneNote inclus dans un groupe est stocké dans la bibliothèque d’éléments de site dans le site SharePoint associé. Alors que les fichiers de bloc-notes peuvent parfois être répartis entre plusieurs fichiers individuels, ils ne peuvent pas être simplement copiés et ouverts indépendamment. Au lieu de cela, le contenu du bloc-notes OneNote doit être déplacé ou exporté à l’aide de OneNote 2016.

**Déplacer des pages et des sections vers un autre bloc-notes**

Le [transfert individuel de pages ou de sections vers un autre bloc-notes](https://support.office.com/article/c3c8b098-7f9c-4c2a-a0dc-ebb83bc76364) permet aux propriétaires de nettoyer leurs données et de ne prendre que les éléments qui doivent être conservés.

**Exporter l’intégralité du bloc-notes en tant que package**

Si l’intégralité du bloc-notes doit être conservée avec sa structure existante, il peut être [exporté en tant que fichier de package OneNote](https://support.office.com/article/a4b60da5-8f33-464e-b1ba-b95ce540f309) , puis importé dans un nouvel emplacement. Vous pouvez également utiliser cette méthode pour conserver le contenu d’un fichier unique au lieu de la structure à plusieurs fichiers existante.

**Imprimer au format PDF**

Dans les scénarios où une partie du contenu du bloc-notes doit uniquement être conservée pour référence ou en tant qu’enregistrements, des pages individuelles peuvent être [imprimées au format PDF et stockées ailleurs](https://support.office.com/article/13d173b5-7f4c-45a8-94eb-9354d63af5cd).

## <a name="mailbox-and-calendar"></a>Boîte aux lettres et calendrier

Il n’est pas rare que la boîte aux lettres associée à un groupe soit utilisée, même si de nombreuses conversations ont pu être menées au sein des canaux d’équipe. La boîte aux lettres ne stocke que les messages électroniques qui lui ont été directement adressés et qui n’inclut pas les courriers électroniques envoyés directement aux canaux.

Dans certains cas, les courriers électroniques stockés dans la boîte aux lettres peuvent simplement être des notifications de réunions, de mises à jour de tâches du planificateur et d’autres messages générés par l’application ou par le système. Il est important que le contenu de la boîte aux lettres soit révisé pour déterminer si le contenu doit être conservé ou supprimé.

Si une stratégie de rétention est appliquée à Exchange, les messages électroniques et les éléments de calendrier sont conservés et disponibles via des recherches de découverte électronique.

**Exporter le courrier et le calendrier**

Les membres d’équipe ou [de groupe peuvent exporter le contenu de la boîte aux lettres et du calendrier vers un fichier de stockage de données/personnel Outlook (PST)](https://support.office.com/article/14252b52-3075-4e9b-be4e-ff9ef1068f91). Ce fichier peut ensuite être stocké ailleurs ou le contenu peut être importé dans une autre boîte aux lettres. Le premier n’est pas recommandé, car le contenu du fichier PST ne peut pas faire l’objet d’une recherche dans Outlook, et le fichier lui-même peut être endommagé au fil du temps.

**Migration de contenu effectuée par le service informatique**

Les administrateurs peuvent utiliser des outils tiers pour migrer le contenu des courriers électroniques et des calendriers entre des boîtes aux lettres sans aucune intervention de l’utilisateur. Un emplacement de stockage potentiel peut être une boîte aux lettres partagée créée uniquement pour servir d’archive du contenu de la boîte aux lettres de groupe.

## <a name="planner"></a>Planificateur

Chaque groupe ou équipe peut avoir plusieurs plans. Au cours du processus par débarquement, il est important de s’assurer que chaque plan est traité sur la conservation de son contenu. Comme les autres produits, il existe plusieurs approches pour le contenu débarquement dans le planificateur.

**Exporter le plan vers une feuille de calcul**

S’il est nécessaire de conserver une copie du plan à des fins d’archivage uniquement, l’approche la plus simple consiste à [Exporter le plan vers une feuille de calcul Excel](https://support.microsoft.com/office/4d850c6e-e548-4aab-83b4-b62b68662d2a). Il s’agit d’une action unidirectionnelle, car il n’existe pas d’option permettant d’importer des plans à partir d’une feuille de calcul.

> [!IMPORTANT]
> L’exportation d’un plan vers Excel prend en compte la plupart des informations dans le plan, mais n’inclut pas de commentaires, de liens ou de fichiers.

**Copier et déplacer des tâches vers un autre plan**

Bien qu’il semble une solution, les tâches individuelles peuvent uniquement être [copiées ou déplacées entre les plans](https://support.microsoft.com/office/ad43a5d8-c1ad-42fd-b3da-fe97d72c8a1b) au sein du même groupe, ce qui annule l’avantage dans si le groupe associé au plan est supprimé.

**Copier tout le plan**

Il est également possible de [copier l’ensemble du plan](https://support.microsoft.com/office/50401e13-a25f-40df-93c6-b608cc28c3d4). Toutefois, il ne peut pas s’agir d’un groupe existant, ni même au sein du même groupe. La copie du plan crée un groupe. En outre, la copie de l’intégralité du plan n’inclut pas les commentaires, les affectations, les liens, les pièces jointes ou les dates.

## <a name="power-automate"></a>Power Automate

Les flux créés dans Power Automated et associés à un groupe ou une équipe n’appartiennent pas au groupe et sont détenus par le créateur et partagés avec d’autres utilisateurs et groupes. En tant que tels, ils ne sont pas affectés si un groupe ou une équipe est supprimée.

**Modifier la propriété du flux**

Si le flux de travail doit continuer à fonctionner, tous les propriétaires peuvent simplement ajouter d’autres utilisateurs ou des groupes Microsoft 365 en tant que propriétaires.

**Exporter le flux**

Si le flux de travail n’a pas besoin de continuer à fonctionner, mais qu’il doit être conservé pour une utilisation future potentielle, il peut être [exporté sous forme de fichier](https://flow.microsoft.com/blog/import-export-bap-packages/) et importé ultérieurement.

## <a name="power-bi"></a>Power BI

Les données et espaces de travail Power BI peuvent fonctionner indépendamment des groupes et des équipes et comme les autres charges de travail offrent différentes façons d’être offboarded.

**Copier des rapports dans un autre espace de travail**

Si le rapport doit être conservé dans son état fonctionnel au-delà de la durée de vie du groupe ou de l’équipe, il peut être [copié à partir de l’espace de travail existant vers un autre espace de travail dans Power bi](https://docs.microsoft.com/power-bi/connect-data/service-datasets-copy-reports).

**Exporter des données à partir d’un tableau de bord ou d’un rapport**

Sinon, si le rapport n’a plus besoin d’être actif mais que les données doivent être conservées, il peut être [exporté vers Excel](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-export-data).

## <a name="project"></a>Project

Les projets et les feuilles de route créés dans Project sur le Web peuvent être associés à des groupes Microsoft 365 et proposent des approches similaires à Power BI.

**Affecter le projet à un autre groupe**

Si le projet doit être conservé en état de fonctionnement au-delà de la durée de vie du groupe ou de l’équipe, il peut être [attribué à un autre groupe Microsoft 365](https://docs.microsoft.com/project-for-the-web/access-a-project-after-group-is-deleted#reassign-the-project) à l’aide du centre d’Administration Dynamics 365.

**Exporter des données à partir du projet ou de la feuille de route**

À l’aide du centre d’administration Dynamics 365, il est possible d' [Exporter les données utilisateur du projet](https://docs.microsoft.com/project-for-the-web/export-user-data-from-project-for-the-web) vers une feuille de calcul, ou si vous utilisez un script PowerShell, les données peuvent être exportées vers le fichier de projet (. MPP) et les formats de fichier XML.

## <a name="sharepoint"></a>SharePoint
Tous les fichiers des canaux d’équipe sont stockés dans la bibliothèque de documents sur le site SharePoint du groupe associé. Dans certains cas, un contenu autre que des documents peut exister dans SharePoint, comme des listes ou des pages.
Les fichiers sont généralement stockés dans trois emplacements principaux dans un site SharePoint :

- Pages-bibliothèque de pages de site
- Images utilisées dans les pages – bibliothèque d’éléments de site
- Fichiers dans Channels-bibliothèque de documents
- Pages wiki – bibliothèque de données wiki teams

Si un ou plusieurs sous-sites sont imbriqués dans le site, le processus par débarquement doit être répété pour chaque sous-site. Si l’équipe contient des canaux privés, il existe un site SharePoint distinct pour chaque canal.

Lorsque vous supprimez des fichiers d’un groupe ou d’une équipe, il est important de considérer qu’ils peuvent être partagés avec des utilisateurs qui ne sont pas membres du groupe ou de l’équipe (interne ou externe à l’organisation), et en tant que tel, il peut être utile de communiquer les modifications imminentes.

**Télécharger des fichiers**

Dans le cas de fichiers stockés dans SharePoint dans l’une des bibliothèques mentionnées ci-dessus, ceux-ci peuvent être [téléchargés sur un ordinateur local](https://support.office.com/article/5c7397b7-19c7-4893-84fe-d02e8fa5df05).

**Déplacer des fichiers**

De plus, les fichiers peuvent être déplacés vers un autre emplacement au sein de SharePoint, tel qu’une bibliothèque dans un site différent.
Aide https://support.office.com/en-us/article/move-or-copy-files-in-sharepoint-00e2f483-4df3-46be-a861-1f5f0c1a87bc

**Exporter la liste** Les données stockées dans des listes SharePoint peuvent être exportées dans [une feuille de calcul Excel](https://support.office.com/article/bfb2ea48-6118-4fa9-abb6-cced9424e5d9)et importées à nouveau dans une liste dans un autre site.

Vous pouvez également utiliser un outil tiers pour migrer la liste entre les sites afin de conserver les fonctions, les vues de liste, la mise en forme et d’autres attributs.

**« Exporter » les fichiers wiki**

Le contenu de wiki au sein des canaux d’équipe est stocké dans un fichier au format HTML dans une bibliothèque dédiée du site SharePoint associé. Elles ne peuvent pas être immédiatement exportées et importées vers un autre wiki de canal, mais peuvent être converties en fichier HTML et ouvertes en tant que page Web.

## <a name="microsoft-stream"></a>Microsoft Stream

Comme l’automate de puissance, les vidéos en flux associés à un groupe ou une équipe ne sont pas détenues par le groupe et ne sont pas supprimées lors de la suppression du groupe. Les vidéos en flux sont la propriété de la personne qui a chargé ou créé la vidéo, même si elles ajoutent des utilisateurs ou des groupes en tant que propriétaires. C’est également le cas pour les réunions enregistrées dans un canal d’équipe ; ils appartiennent à la personne qui a initié l’enregistrement.

**Ajout d’autres propriétaires**

Comme la vidéo est conservée en flux quelle que soit la suppression du groupe, le propriétaire d’origine peut [partager la vidéo avec d’autres utilisateurs et groupes, même les ajouter en tant que propriétaires](https://docs.microsoft.com/stream/portal-edit-video).

**Télécharger la vidéo**

Dans les scénarios où la vidéo n’a pas besoin d’être conservée en flux ou qui doit être stockée dans un autre emplacement, tel qu’un système de gestion des enregistrements, un propriétaire peut être [téléchargé localement](https://docs.microsoft.com/stream/portal-download-video) .

## <a name="yammer"></a>Yammer

Contrairement aux conversations dans Microsoft Teams, Yammer offre aux utilisateurs et aux administrateurs les options permettant de déplacer ou d’exporter des conversations.

**Déplacer des conversations vers un autre groupe ou une autre communauté**

Les conversations peuvent être déplacées vers un autre groupe Yammer par n’importe quel utilisateur, pas seulement les propriétaires ou les administrateurs. Cela est possible dans le [Yammer classique](https://support.office.com/article/149c6399-4ac1-4ced-84d7-e0660960a872), ainsi que dans les [nouvelles interfaces Yammer](https://support.office.com/article/d63debf1-1c90-4ec5-b5ae-8a00939a1680) .

**Exporter des données réseau**

Les administrateurs de réseau Yammer peuvent effectuer une [exportation des données réseau](https://docs.microsoft.com/yammer/manage-security-and-compliance/export-yammer-enterprise-data), mais cela a pour effet d’exporter toutes les conversations pour l’ensemble du réseau. Étant donné que l’exportation obtenue répertorie l’ID de groupe, il est possible de filtrer les conversations en fonction de ce.
