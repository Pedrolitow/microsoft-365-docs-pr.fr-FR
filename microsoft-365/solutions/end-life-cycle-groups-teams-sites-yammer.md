---
title: Options de fin de cycle de vie pour les groupes, les équipes et les Yammer
ms.reviewer: mmclean
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Options de fin de cycle de vie pour les groupes, les équipes et les Yammer.
ms.openlocfilehash: f7774498047f74c27b21e45ed86b284a42325bb0
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973924"
---
# <a name="end-of-lifecycle-options-for-groups-teams-and-yammer"></a>Options de fin de cycle de vie pour les groupes, les équipes et les Yammer

Groupes Microsoft 365 et Microsoft Teams fonctionnent avec plusieurs services connectés. Lorsqu’un groupe ou une équipe est supprimé, la plupart des informations dans les services connectés sont également supprimées. Cet article décrit les options permettant de conserver les informations en les déplaçant hors du groupe ou de l’équipe avant leur suppression.

Une pratique courante pour les groupes ou les équipes qui ne sont plus nécessaires consiste à déplacer les fichiers hors de l’équipe et à les archiver dans un autre emplacement, tel qu’une bibliothèque de documents SharePoint. Cette pratique est basée sur un style hérité de travail où les informations sont stockées dans des fichiers et des dossiers, et les communications sont effectuées par e-mail.

Le tableau suivant décrit les services associés aux groupes et aux équipes, ainsi que les types de contenu clés trouvés dans chacun d’eux :

|Service|Types de contenu|
|:------|:---------------|
|Équipes|Conversations de canal, fichiers dans les canaux|
|Formulaires|Structure et résultats de l’enquête|
|OneNote|Bloc-notes|
|Outlook|Courrier et calendrier|
|Planificateur|Project l’état et les informations de tâche|
|Power Automate|Flux de travail|
|Power BI|Données, rapports et tableaux de bord|
|Project sur le web|plans Project|
|Feuille de route|Feuilles de route|
|SharePoint|Fichiers, listes Teams données wiki de canal|
|Flux|Vidéos|
|Yammer|Conversations|

Lors de la suppression d’un groupe ou d’une équipe, la plupart des ressources associées sont également supprimées. Les exceptions sont les suivantes :

- Les vidéos dans Stream restent et appartiennent à la personne qui les a chargées/enregistrées
- Les flux dans Power Automate restent et appartiennent à la personne qui les a créés.
- Project et les données de feuille de route dans Project sur le web restent dans le CDS et peuvent être restaurées séparément.

Les groupes et les équipes restent dans un état de suppression réversible pendant 30 jours et peuvent être restaurés à tout moment. Toutefois, après les 30 jours, elles et toutes les ressources associées, telles que les services et le contenu, sont purgées de l’environnement Microsoft 365. Tout contenu protégé par une stratégie de rétention reste disponible par le biais de recherches eDiscovery.

## <a name="end-of-life-cycle-considerations-for-group-connected-services"></a>Considérations relatives à la fin du cycle de vie pour les services connectés à un groupe

Il existe trois domaines clés que les propriétaires d’équipe et de groupe et les administrateurs informatiques doivent prendre en compte lors de la suppression d’un groupe ou d’une équipe.

**Content**

Le contenu doit-il être conservé une fois que l’équipe n’est plus là ? Est-il suffisant de s’appuyer sur les fonctionnalités de rétention de Microsoft 365, ou une partie du contenu dans les applications et services qui n’offrent pas de rétention ? Le contenu doit-il être conservé à des fins de gestion des enregistrements, d’archivage ou d’utilisation future et de référence ?

Pour éviter toute perte de données potentielle, ces questions doivent être posées avant que n’importe quelle équipe soit archivée ou supprimée.

**Services**

Le contenu doit-il rester dans sa forme de travail actuelle ? Par exemple, le rapport Power BI doit-il continuer à être accessible ? Les résultats du formulaire doivent-ils être disponibles dans l’affichage récapitulatif visuel ? Les listes dans SharePoint sont-elles liées ou incorporées n’importe où ?

Ces questions doivent être posées avant la suppression du groupe sous-jacent, car l’exportation du contenu peut ne pas être suffisante.

**Invités**

Lorsque les invités sont invités à une équipe, un compte invité est créé dans le Azure Active Directory de l’organisation hôte avant de les ajouter à l’équipe. Lorsqu’une équipe est supprimée, les invités ne sont pas supprimés de Azure Active Directory. Bien que les invités ne puissent pas accéder aux groupes, sites, équipes ou contenus qui n’ont pas été partagés avec eux, ils peuvent toujours utiliser des fonctionnalités dans Microsoft Teams telles que le démarrage de conversations, d’appels vocaux et vidéo et l’utilisation d’applications.

Un propriétaire d’équipe ou de groupe peut inviter quelqu’un de l’extérieur de l’organisation à devenir invité dans Azure Active Directory en l’ajoutant à une équipe. Toutefois, un propriétaire d’équipe ne peut pas supprimer l’invité de Azure Active Directory. La suppression de comptes ne peut être effectuée que par un administrateur général ou un administrateur d’utilisateurs.

Il est important d’effectuer des commentaires sur les invités et de comprendre si les invités doivent être supprimés de Azure Active Directory lors de la suppression de l’équipe. Il peut y avoir un cas valide pour que les invités restent dans l’annuaire, comme être membre d’autres équipes ou utiliser d’autres services Microsoft 365 ou Azure.

## <a name="teams"></a>Équipes

Teams contenu spécifique se présente principalement sous la forme de conversations.

Les conversations dans les canaux ne peuvent pas être copiées ou déplacées à l’aide de fonctionnalités de Microsoft Teams natives. Ils peuvent toutefois être exportés à l’aide de la API Graph.

En outre, si une stratégie de rétention est appliquée à Teams, les conversations sont conservées et disponibles via des recherches eDiscovery. À l’aide d’eDiscovery (Premium), vous pouvez [reconstruire une conversation Teams](/microsoft-365/compliance/conversation-review-sets) conversation.


### <a name="archiving-a-team"></a>Archivage d’une équipe

L’avantage de [l’archivage d’une équipe](/microsoftteams/archive-or-delete-a-team) est qu’elle fournit un accès complet à l’équipe telle qu’elle était. Les utilisateurs peuvent toujours parcourir les conversations de canal et ouvrir des fichiers même s’ils ne sont pas actifs. En outre, les équipes peuvent ne pas être archivées s’il est nécessaire de continuer à travailler dessus (par exemple, si un projet est étendu).

Lorsqu’une équipe est archivée par un propriétaire, elle est définie sur lecture seule pour les membres à la fois pour le contenu au sein de l’équipe et, s’il est sélectionné, le site SharePoint associé. L’objectif de cette action est de s’assurer que les conversations dans les canaux sont conservées dans leur état existant, ainsi que SharePoint contenu basé sur des fichiers et des wikis.

Dans le site SharePoint il n’y a aucune modification visible. Toutefois, aucune modification ne peut être apportée à des fichiers ou des listes, car les autorisations de SharePoint pour le groupe Microsoft 365 sont définies sur les **visiteurs du site**. Cela inclut le bloc-notes OneNote pour l’équipe, qui est stocké dans la bibliothèque Ressources du site dans le site SharePoint.

Lorsqu’une équipe est archivée, le groupe Microsoft 365 sous-jacent est toujours soumis à la stratégie d’expiration (si elle est définie) et, par conséquent, le propriétaire doit continuer à renouveler l’équipe.

Bien que les conversations de canal de l’équipe et le contenu du site SharePoint soient définis sur lecture seule, il n’en va pas de même pour les autres services associés :

- Les compartiments et tâches du planificateur peuvent toujours être créés, modifiés et supprimés.
- Les formulaires peuvent toujours recevoir des soumissions.
- La boîte aux lettres Outlook peut toujours recevoir des e-mails.
- Power BI tableaux de bord, rapports et données peuvent toujours être modifiés.
- Les projets et les feuilles de route peuvent toujours être modifiés dans Project sur le web.
- Les vidéos peuvent toujours être téléchargées, modifiées et supprimées dans Stream.
- Les flux dans Power Automate peuvent toujours être créés, modifiés, supprimés et continueront à s’exécuter. (Toutefois, elles échouent si nécessaire pour publier un message sur un canal de l’équipe archivée.)

## <a name="forms"></a>Formulaires

Bien qu’un formulaire puisse être déplacé d’un compte individuel vers un groupe, il ne peut pas être déplacé ou copié d’un groupe à un autre. Trois options sont disponibles pour un formulaire lorsqu’une équipe est supprimée.

**Dupliquer le formulaire**

Les [formulaires peuvent être partagés en tant que modèles](https://support.microsoft.com/office/82ea9d8a-260a-47a0-afdb-497f3d746e3f), ce qui permet à d’autres utilisateurs de les copier sur leur propre compte ou un groupe. Cela ne conserve pas les données des soumissions de résultats ; structure de formulaire uniquement, telle que les questions et les paramètres.

**Exporter les résultats vers une feuille de calcul**

Si les données des réponses de formulaire doivent être conservées, vous pouvez y parvenir [en exportant les résultats dans une feuille de calcul Excel](https://support.office.com/article/02859424-341d-406f-b32a-9a0fbaf357af). Cela n’exportera que les questions et leurs réponses en tant que données . Elle n’inclut pas les graphiques créés par forms.

**Supprimer le formulaire**

Bien que la suppression du groupe entraîne également la suppression de tous les formulaires associés, les membres du groupe peuvent [les supprimer directement](https://support.microsoft.com/office/2207e468-ce1b-4c4a-a256-caf631d87af0) sans être propriétaires du groupe. Toutefois, il s’agit d’une étape manuelle qui ne fournit aucun avantage supplémentaire.

## <a name="onenote"></a>OneNote

Le bloc-notes OneNote inclus dans un groupe est stocké dans la bibliothèque Ressources du site dans le site SharePoint associé. Bien que les fichiers notebook puissent parfois être répartis sur plusieurs fichiers individuels, ils ne peuvent pas être copiés et ouverts indépendamment. Au lieu de cela, le contenu du bloc-notes OneNote doit être déplacé ou exporté à l’aide de OneNote 2016.

**Déplacer des pages et des sections vers un autre bloc-notes**

[Le déplacement individuel de pages ou de sections vers un autre bloc-notes](https://support.office.com/article/c3c8b098-7f9c-4c2a-a0dc-ebb83bc76364) permet aux propriétaires de nettoyer leurs données et de prendre uniquement ce qui doit être conservé.

**Exporter l’intégralité du bloc-notes en tant que package**

Si l’intégralité du bloc-notes doit être conservée avec sa structure existante, il peut être [exporté en tant que fichier de package OneNote](https://support.office.com/article/a4b60da5-8f33-464e-b1ba-b95ce540f309), puis importé vers un nouvel emplacement. Au lieu de cela, cela peut être utilisé comme méthode pour conserver le contenu dans un seul fichier au lieu de la structure multi-fichiers existante.

**Imprimer au format PDF**

Dans les scénarios où une partie du contenu du bloc-notes doit uniquement être conservée pour référence ou en tant qu’enregistrements, des pages individuelles peuvent être [imprimées au format PDF et stockées ailleurs](https://support.office.com/article/13d173b5-7f4c-45a8-94eb-9354d63af5cd).

## <a name="mailbox-and-calendar"></a>Boîte aux lettres et calendrier

Il n’est pas rare que la boîte aux lettres associée au groupe soit utilisée, même si de nombreuses conversations peuvent avoir été effectuées dans des canaux d’équipe. La boîte aux lettres stocke uniquement les e-mails qui lui ont été envoyés directement et n’inclut pas les e-mails qui ont été envoyés directement aux canaux.

Dans certains cas, les e-mails stockés dans la boîte aux lettres peuvent être des notifications de réunions, de mises à jour des tâches du Planificateur et d’autres messages générés par l’application ou le système. il est important que le contenu de la boîte aux lettres soit examiné pour déterminer si le contenu doit être conservé ou supprimé.

Si une stratégie de rétention est appliquée dans Exchange, les e-mails et les éléments de calendrier sont conservés et disponibles par le biais de recherches eDiscovery.

**Exporter le courrier et le calendrier**

Les membres d’une équipe ou d’un groupe peuvent [exporter le contenu de la boîte aux lettres et du calendrier vers un fichier Outlook Data /Personal Stockage (PST).](https://support.office.com/article/14252b52-3075-4e9b-be4e-ff9ef1068f91) Ce fichier peut ensuite être stocké ailleurs, ou le contenu peut être importé dans une autre boîte aux lettres. Le premier n’est pas recommandé, car le contenu du fichier PST ne peut pas faire l’objet d’une recherche sans l’ouvrir dans Outlook, et le fichier lui-même peut être endommagé au fil du temps.

**Migration de contenu effectuée par l’informatique**

Les administrateurs peuvent utiliser des outils tiers pour migrer le contenu du courrier électronique et du calendrier entre les boîtes aux lettres sans intervention de l’utilisateur. Un emplacement de stockage potentiel peut être une boîte aux lettres partagée créée uniquement pour servir d'« archive » du contenu de la boîte aux lettres de groupe.

## <a name="planner"></a>Planificateur

Chaque groupe ou équipe peut avoir plusieurs plans. Il est important pendant le processus de désintégération de s’assurer que les exigences de rétention sont traitées pour chaque plan. Comme les autres services, il existe plusieurs approches de contenu hors-carte dans le Planificateur.

**Exporter le plan vers une feuille de calcul**

S’il est uniquement nécessaire de conserver une copie du plan à des fins de conservation des enregistrements, l’approche la plus simple consiste à [exporter le plan vers une feuille de calcul Excel](https://support.microsoft.com/office/4d850c6e-e548-4aab-83b4-b62b68662d2a). Il s’agit d’une action unidirectionnelle : il n’existe aucune option pour importer des plans à partir d’une feuille de calcul.

> [!IMPORTANT]
> L’exportation d’un plan vers Excel prend la plupart des informations dans le plan, mais n’inclut pas de commentaires, de liens ou de fichiers.

**Copier et déplacer des tâches vers un autre plan**

Lors de la copie ou du déplacement de tâches vers un autre plan semble être une solution, les tâches individuelles ne peuvent être [copiées ou déplacées qu’entre des plans](https://support.microsoft.com/office/ad43a5d8-c1ad-42fd-b3da-fe97d72c8a1b) au sein du même groupe. Cela ne sauvegardera pas les données si le groupe associé au plan est supprimé.

**Copier l’intégralité du plan**

Il est également possible de [copier l’intégralité du plan](https://support.microsoft.com/office/50401e13-a25f-40df-93c6-b608cc28c3d4). La copie ne peut pas être effectuée dans un groupe existant. La copie du plan crée un groupe. En outre, la copie de l’ensemble du plan n’inclut pas de commentaires, d’affectations, de liens, de pièces jointes ou de dates.

## <a name="power-automate"></a>Power Automate

Les flux créés dans Power Automate et associés à un groupe ou à une équipe n’appartiennent pas au groupe. Ils sont la propriété du créateur et simplement partagés avec d’autres utilisateurs et groupes. En tant que tels, ils ne sont pas affectés si un groupe ou une équipe est supprimé.

**Modifier la propriété du flux**

Si le flux doit continuer à fonctionner, tous les propriétaires peuvent ajouter d’autres utilisateurs ou groupes Microsoft 365 en tant que propriétaires.

**Exporter le flux**

Si le flux n’a pas besoin de continuer à fonctionner, mais qu’il doit être conservé pour une utilisation future potentielle, il peut être [exporté en tant que fichier](https://flow.microsoft.com/blog/import-export-bap-packages/) et importé à nouveau ultérieurement.

## <a name="power-bi"></a>Power BI

Power BI données et espaces de travail peuvent fonctionner indépendamment des groupes et des équipes, et comme d’autres charges de travail offrent différentes façons d’être désintégrés.

**Copier des rapports dans un autre espace de travail**

Si vous avez besoin du rapport une fois le groupe ou l’équipe supprimé, il peut être [copié à partir de l’espace de travail existant vers un autre espace de travail dans Power BI](/power-bi/connect-data/service-datasets-copy-reports).

**Exporter des données à partir d’un tableau de bord ou d’un rapport**

Au lieu de cela, si le rapport n’a plus besoin d’être actif mais que les données doivent être conservées, il peut être [exporté vers Excel](/power-bi/visuals/power-bi-visualization-export-data).

## <a name="project"></a>Project

Les projets et feuilles de route créés dans Project pour le web sont associés à Microsoft 365 groupes et ont des approches de désintégrage similaires à Power BI.

**Affecter le projet à un autre groupe**

Si le projet doit être conservé dans son état fonctionnel au-delà de la durée de vie du groupe ou de l’équipe, il peut être [affecté à un autre groupe Microsoft 365](/project-for-the-web/access-a-project-after-group-is-deleted#reassign-the-project). Pour ce faire, utilisez le Centre d’administration Dynamics 365.

**Exporter des données à partir du projet ou de la feuille de route**

À l’aide du Centre d’administration Dynamics 365, il est possible [d’exporter des données utilisateur du projet](/project-for-the-web/export-user-data-from-project-for-the-web) vers une feuille de calcul. Les données peuvent également être exportées vers Project fichier (. MPP) et les formats de fichier XML à l’aide de PowerShell.

## <a name="sharepoint"></a>SharePoint

Tous les fichiers des canaux d’équipe sont stockés dans le site SharePoint du groupe associé. Dans certains cas, du contenu autre que des documents peut exister dans des SharePoint, tels que des listes ou des pages.

Les fichiers sont généralement stockés dans trois emplacements principaux dans un site SharePoint :

- Pages - Bibliothèque de pages de site
- Images utilisées dans les pages – Bibliothèque de ressources de site
- Fichiers dans les canaux – Bibliothèque de documents
- Pages Wiki – Teams bibliothèque de données Wiki

Si le site comporte un ou plusieurs sous-sites, le processus de désintégrage doit être répété pour chaque sous-site. Si l’équipe contient des canaux privés ou partagés, il existe un site SharePoint distinct pour chaque canal.

Lors de la suppression de fichiers d’un groupe ou d’une équipe, il est important de considérer qu’ils peuvent être partagés avec des utilisateurs qui ne sont pas membres du groupe ou de l’équipe. Vous souhaiterez peut-être leur communiquer la modification imminente.

**Télécharger des fichiers**

Les fichiers stockés dans SharePoint dans l’une des bibliothèques mentionnées ci-dessus peuvent être [téléchargés sur un ordinateur local](https://support.office.com/article/5c7397b7-19c7-4893-84fe-d02e8fa5df05).

**Déplacer des fichiers**

En outre, les fichiers peuvent être [déplacés vers un autre emplacement dans SharePoint comme une bibliothèque dans un autre site](https://support.office.com/article/00e2f483-4df3-46be-a861-1f5f0c1a87bc).

**Exporter la liste**

Les données stockées dans SharePoint listes peuvent être [exportées vers une feuille de calcul Excel](https://support.office.com/article/bfb2ea48-6118-4fa9-abb6-cced9424e5d9) et importées à nouveau dans une liste d’un autre site.

Vous pouvez également utiliser un outil tiers pour migrer la liste entre les sites afin de conserver la fonction, les vues de liste, la mise en forme et d’autres attributs.

**« Exporter » des fichiers wiki**

Le contenu wiki dans les canaux d’équipe est stocké dans un fichier au format HTML dans une bibliothèque dédiée du site SharePoint associé. Ils ne peuvent pas être facilement exportés et importés vers un autre wiki de canal, mais peuvent être convertis en fichier HTML et ouverts en tant que page web.

## <a name="microsoft-stream"></a>Microsoft Stream

Comme Power Automate, les vidéos de Stream associées à un groupe ou à une équipe ne sont pas réellement détenues par le groupe et ne sont pas supprimées lorsque le groupe est supprimé. Les vidéos dans Stream appartiennent à la personne qui a chargé ou créé la vidéo, même si elle ajoute des utilisateurs ou des groupes en tant que propriétaires. Les réunions enregistrées dans un canal Teams appartiennent à la personne qui a démarré l’enregistrement.

**Ajout d’autres propriétaires**

Étant donné que la vidéo est conservée dans Stream lorsque le groupe est supprimé, le propriétaire d’origine peut [partager la vidéo avec d’autres utilisateurs et groupes, même en les ajoutant en tant que propriétaires](/stream/portal-edit-video).

**Télécharger la vidéo**

Dans les scénarios où la vidéo n’a pas besoin d’être conservée dans Stream ou doit être stockée dans un autre emplacement tel qu’un système de gestion des enregistrements, un propriétaire peut la [télécharger localement](/stream/portal-download-video).

## <a name="yammer"></a>Yammer

Contrairement aux conversations dans Microsoft Teams, Yammer offre aux utilisateurs et aux administrateurs des options pour déplacer ou exporter des conversations.

**Déplacer des conversations vers un autre groupe ou communauté**

Les conversations peuvent être déplacées vers un autre groupe Yammer par n’importe quel utilisateur, pas seulement par les propriétaires ou les administrateurs. Cela est possible à la fois dans les [Yammer classiques](https://support.office.com/article/149c6399-4ac1-4ced-84d7-e0660960a872) et dans les nouvelles interfaces [Yammer](https://support.office.com/article/d63debf1-1c90-4ec5-b5ae-8a00939a1680).

**Exporter des données réseau**

Yammer les administrateurs réseau [exportent les données réseau](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Toutefois, cela permet d’exporter toutes les conversations pour l’ensemble du réseau. L’exportation qui en résulte répertorie l’ID de groupe. Il est possible de filtrer les conversations en fonction de cet ID.

## <a name="related-topics"></a>Rubriques connexes

[Supprimer un ancien employé et sécuriser les données](/microsoft-365/admin/add-users/remove-former-employee)
