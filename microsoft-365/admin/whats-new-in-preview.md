---
title: Nouveautés du Centre d’administration Microsoft 365
f1.keywords:
- CSH
ms.author: anfowler
author: adefowler
manager: shohara
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- MET150
- MOE150
- FRP150
description: 'Centre d’administration Microsoft 365 : découvrez les fonctionnalités qui ont été ajoutées ce mois-ci.'
ms.custom:
- MACDashWhatsNew
- AdminSurgePortfolio
ms.openlocfilehash: 12b7dfd39a9cf8ac73e8f1c7f2297721c2d629bf
ms.sourcegitcommit: a76de3d1604d755b29053e7bf557c0008be6ad23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "49787878"
---
# <a name="whats-new-in-the-microsoft-365-admin-center"></a>Nouveautés du Centre d’administration Microsoft 365

::: moniker range="o365-21vianet"

> [!NOTE]
> Certaines des informations de cet article peuvent ne pas s’appliquer à Office 365 géré par 21Vianet.

::: moniker-end

Nous ajoutons en permanence de nouvelles fonctionnalités au Centre d’administration [Microsoft 365,](microsoft-365-admin-center-preview.md)corrigeons les problèmes que nous avons appris et apportant des modifications en fonction de vos commentaires. Consultez la vidéo ci-dessous pour voir ce qui est disponible pour vous aujourd’hui. Certaines fonctionnalités sont déployées à des vitesses différentes pour nos clients. Si vous ne voyez pas encore de fonctionnalité, essayez de vous [ajouter à la version ciblée.](manage/release-options-in-office-365.md)

Et si vous souhaitez savoir quelles sont les nouveautés des autres services cloud de Microsoft :

- [Nouveautés d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/whats-new)
- [Nouveautés du Centre d’administration Exchange](https://docs.microsoft.com/Exchange/whats-new)
- [Nouveautés de Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/whats-new)
- [Nouveautés du Centre de conformité Microsoft 365](https://docs.microsoft.com/Office365/SecurityCompliance/whats-new)
- [Nouveautés de Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/whats-new)
- [Nouveautés du Centre d’administration SharePoint](https://docs.microsoft.com/sharepoint/what-s-new-in-admin-center)
- [Mises à jour Office](https://docs.microsoft.com/OfficeUpdates/)

## <a name="ignite-2020-august--september"></a>Ignite 2020 (août & septembre)

Bienvenue dans Microsoft Ignite , notre premier Ignite en ligne uniquement. Nous espérons vous voir dans l’une de nos sessions : [Microsoft Ignite 2020 Session Catalog](https://myignite.microsoft.com/sessions). Voici quelques-uns des éléments dont nous parlerons à Ignite. 
> [!NOTE]
> Toutes les fonctionnalités ne seront pas disponibles immédiatement pour tout le monde. Si vous ne voyez pas les nouvelles fonctionnalités, [rejoignez la version ciblée.](manage/release-options-in-office-365.md)

### <a name="multi-tenant-management"></a>Gestion multi-locataires

Nous avons développé un ensemble de fonctionnalités pour les administrateurs multi-locataires comme vous pour que votre travail soit effectué plus rapidement et plus efficacement. Pour plus d’informations, [voir Gérer plusieurs locataires.](multi-tenant/manage.md)

- **Vos locataires :** basculez rapidement entre les locataires que vous gérez.
- **Tous** les clients : nouvelle page où vous pouvez voir rapidement l’état de tous les services de vos clients, les demandes de service ouvertes, vos produits et facturation, les tâches de configuration recommandées et le nombre d’utilisateurs dans ce client.
- **Programme d’installation**: la page d’installation multi-client vous donne un affichage liste de la page d’installation, mais elle est organisée pour de nombreux locataires. Vous pouvez voir quelles fonctionnalités ne sont pas désactivées, quelles tâches sont terminées pour tous les locataires, tâches que les locataires doivent encore effectuer. Cette vue vous aidera à effectuer le suivi de l’adoption des fonctionnalités et à vous assurer que les tâches de configuration de sécurité recommandées sont toujours réalisées.
- **État du** service : l’affichage d’état du service vous indique si des incidents ou des avis affectent les clients. Il vous indiquera même combien de vos locataires gérés sont affectés. Sélectionnez simplement un incident pour obtenir plus d’informations sous l’onglet Vue d’ensemble, puis basculez vers l’onglet Locataires affectés pour descendre et prendre en charge ce client.
- **Les migrations** de boîtes aux lettres entre clients sont un nouveau service, désormais en prévisualisation publique, qui vous permet de déplacer des boîtes aux lettres entre des clients sans avoir à retenter les boîtes aux lettres, puis à les intégrer. 
- **Partage de domaine entre** locataires : bientôt, vous pouvez rejoindre un aperçu privé pour les fonctionnalités qui vous permettent de partager un domaine entre plusieurs locataires. Par exemple, si Contoso acquiert Wingtip Toys, Contoso peut partager le domaine avec Wingtip Toys afin que les personnes des deux locataires peuvent utiliser « contoso.com » comme adresses de messagerie.

![Page État du service pour plusieurs locataires avec un incident sélectionné et onglet Clients affectés ouvert. Le menu de navigation présente l’état de tous les clients, du programme d’installation et du service comme seules options.](../media/MAC-WN-MTinServiceHealth.png)

### <a name="monitor-your-most-important-accounts"></a>Surveiller vos comptes les plus importants

Vous pouvez surveiller et suivre les messages électroniques ayant échoué ou différés envoyés à vos utilisateurs qui ont un impact important sur l’entreprise, comme votre PDG. Vous pouvez suivre les comptes prioritaires en ajoutant des utilisateurs à votre liste de comptes prioritaires dans le Centre d’administration Microsoft 365. Ajoutez des cadres, des responsables, des responsables ou d’autres utilisateurs ayant accès à des informations sensibles ou prioritaires.

Les comptes de priorité sont disponibles uniquement pour les organisations qui répondent aux deux exigences suivantes :

- Office 365 E3 ou Microsoft 365 E3, office 365 E5 ou Microsoft 365 E5.
- Au moins 10 000 licences et au moins 50 utilisateurs Exchange Online actifs mensuels.

![Page De configuration de la fonctionnalité : surveiller vos comptes les plus importants](../media/MAC-WN-PriorityAccounts.png)

Il existe deux façons de commencer :

- Go to **Users**, and then in the « more actions » menu select **Manage priority accounts** to add users to the list.
- Go to **Setup,** find the setup task **Monitor your most important accounts,** and then select Get **started**.

Pour plus d’informations sur les comptes prioritaires, consultez [La surveillance des comptes de priorité.](https://docs.microsoft.com/microsoft-365/admin/setup/priority-accounts)

### <a name="search-faster-and-get-better-results-from-any-page"></a>Recherchez plus rapidement et obtenez de meilleurs résultats à partir de n’importe quelle page

Nous avons commencé à déployer une nouvelle expérience de recherche pour le Centre d’administration et nous ne pouvons pas attendre que vous l’essayiez. ![La zone de recherche a été déplacée vers la zone bannière. Alt+S pour effectuer une recherche à partir d’une page quelconque.](../media/MAC-WN-GlobalSearch.png)

- La zone de recherche a été déplacée vers la zone d’en-tête dans laquelle il est indiqué « Centre d’administration Microsoft 365 » pour que vous recherchez maintenant à partir de n’importe quelle page, et pas seulement de la page d’accueil. Nous avons même un raccourci : **Alt+S**.
- La recherche est plus intelligente et vous donne de meilleurs résultats, encore plus rapidement. Essayez de taper « 2fa » pour commencer.
- Les résultats de la recherche sont organisés selon le type d’élément ou d’action que vous pouvez effectuer.
  - **Utilisateurs**: sélectionnez le nom de l’utilisateur et vous pouvez le modifier directement ici. Si vous sélectionnez le menu « Autres actions » en plus de leur nom, vous pouvez réinitialiser leur mot de passe. Vous pouvez effectuer une recherche par nom d’affichage, nom, prénom, nom d’utilisateur ou adresse de messagerie principale, et alias de messagerie. Toutefois, pour obtenir une correspondance exacte, recherchez par adresse de messagerie principale ou nom d’utilisateur.
  - **Groupes**: modifiez le groupe à partir de n’importe quelle page, ajoutez des membres, attribuez des propriétaires.
  - **Actions**: comme vous pouvez rechercher un utilisateur, puis réinitialiser son mot de passe, vous pouvez également rechercher « réinitialiser le mot de passe » à partir de n’importe quelle page, puis réinitialiser un ou plusieurs mots de passe pour les utilisateurs.
  - **Navigation**: les résultats sous Navigation peuvent rapidement vous aider à obtenir rapidement une page dans le Centre d’administration. Par exemple, la recherche de « rôles » vous permettra d’accès à la page Rôles pour les rôles Azure AD.
  - **Paramètres :** recherchez tous les paramètres liés à votre organisation, les services à qui vous vous abonnez, ainsi que les paramètres de sécurité et de confidentialité. 
  - **Domaines :** vous trouverez des liens rapides vers vos domaines, puis le lien vous permettra d’utiliser la page Vue d’ensemble et d’état de ce domaine.
  - **Documentation**: si nous ne pouvons pas trouver de résultat pour vous, nous allons essayer de trouver de la documentation pour vous aider. Il faut un peu plus de temps à la liste organisée d’articles pour trouver une correspondance, donc patientez une seconde pour que la recherche trouve les résultats. 
  - **Commentaires**: Vous n’avez pas trouvé ce que vous recherchiez ? Envoyez-nous des commentaires à partir de la recherche. Nous allons ajouter des fonctionnalités de recherche pour d’autres pages et d’autres fonctionnalités dans le Centre d’administration.

### <a name="microsoft-365-admin-mobile-app"></a>Application mobile d’administration Microsoft 365

L’application mobile d’administration [Microsoft 365,](https://www.microsoft.com/microsoft-365/business/manage-office-365-admin-app)incluse dans votre abonnement, vous permet de gérer Microsoft 365 à partir de votre appareil mobile afin de pouvoir vous absent de votre bureau pour effectuer des tâches quotidiennes. En fait, l’application comporte plus de 90 fonctionnalités et nous venons d’en ajouter quelques-unes :

- Prise en charge des stratégies de gestion des applications mobiles et d’accès conditionnel de **Microsoft Intune**: vous pouvez désormais utiliser votre appareil personnel pour gérer Microsoft 365, même si votre organisation a désactivé les stratégies de gestion des applications mobiles et d’accès conditionnel d’Intune.
- **Notifications du centre de messages**: activer les notifications du centre de messages sur les notifications de paramètres si vous souhaitez être averti des nouveaux **billets** du centre  >   de messages. Par le biais de notifications, nous voulons vous assurer que vous restez informé des informations et des événements importants au sein de votre client.
- **Alertes de facturation**: vous pouvez également activer les notifications de facturation à l’adresse **Settings** Notifications si vous souhaitez obtenir des notifications de facturation sur votre appareil si un abonnement est sur le point d’expirer.  >  
- **Mode sombre**: bienvenue sur le côté sombre de l’application mobile. Il s’agissait de l’une de nos fonctionnalités les plus demandées. Go to **Settings**  >  **Themes** to turn it on.
- **Signalez un problème**: vous pouvez maintenant signaler un problème dans l’application ou afficher les problèmes signalés par d’autres administrateurs. Visitez **l’état du** service pour l’consulter.

![Page Santé dans l’application d’administration Microsoft 365 avec des notifications pour le centre de messages, l’état du service et les alertes de facturation.](../media/MAC-WN-AdminMobileApp.png)

### <a name="usage-recommendations-for-small-and-medium-businesses"></a>Recommandations d’utilisation pour les petites et moyennes entreprises

Les petites et moyennes entreprises peuvent obtenir une recommandation sur la **page** d’accueil si certaines personnes de l’organisation n’utilisent pas activement teams, OneDrive ou les applications Office. Lorsque vous affichez la recommandation, vous pouvez rapidement envoyer un e-mail de formation Microsoft aux utilisateurs inactifs pour les aider à démarrer avec l’application et vous assurer que vous obtenez la valeur complète de vos abonnements.

### <a name="remote-work-collection"></a>Collection de travail à distance

En octobre, nous allons ajouter une collection de travail à distance pour aider les propriétaires des petites entreprises et leurs employés à se mettre en ligne et à travailler à distance.  **La configuration des éléments essentiels** du travail à distance est une liste organisée de toutes les fonctionnalités recommandées par Microsoft pour activer le travail à distance en toute sécurité et collaborer efficacement. Dans quelques semaines, vous pouvez l’essayer dans **setup**  >  **Remote work essentials**.

![Page Éléments essentiels du travail à distance dans le programme d’installation avec 7 tâches non démarrées.](../media/MAC-WN-RemoteWork.png)

Pour plus d’informations sur la façon d’autoriser en toute sécurité le travail à [distance](https://aka.ms/remote-business)et une adresse web pratique facile à mémoriser et à partager, aka.ms/remote-business .

### <a name="need-help-moving-to-more-admin-centers"></a>Vous avez besoin d’aide ? déplacement vers d’autres centres d’administration

Nous recherchons en permanence et mettons à jour le contenu et les outils pour suivre les modifications apportées au produit. Nous avons maintenant de nombreux autres outils de diagnostic en libre-service pour vous aider à résoudre les problèmes rapidement et efficacement. Voici quelques-unes qui ont été récemment ajoutées :

- Modifier votre stratégie de limitation du service web Exchange
- Vérification de l’état de l’approvisionnement et de la validation de Teams pour des utilisateurs spécifiques
- Résoudre les problèmes d’installation de DKIM
- Diagnostiquer les erreurs d’inscription des utilisateurs Intune

Nous allons également déployer l’expérience de support nouvelle et améliorée que vous voyez déjà dans le Centre d’administration Microsoft 365 dans certains autres centres d’administration. Le Centre d’administration Teams et les centres d’administration de sécurité et conformité ont déjà cette nouvelle expérience. Et bientôt, **le Centre d’administration Exchange,** le Centre d’administration **SharePoint** et **Office.com** seront mis à jour avec cette nouvelle expérience d’aide pour les administrateurs.

### <a name="manage-changes-with-microsoft-planner"></a>Gérer les modifications avec le Planificateur Microsoft

En mai, nous avons annoncé que vous serez bientôt en mesure de synchroniser les publications du Centre de messages avec le Planificateur Microsoft et qu’elle sera désormais disponible pour tout le monde.  Vous pouvez désormais créer des tâches à partir de messages, les affecter et les suivre jusqu’à leur achèvement. La première fois, vous sélectionnez **la synchronisation du** planificateur dont vous aurez besoin pour vous connecter au plan approprié.

![Page centre de messages avec « synchronisation du planificateur » mise en évidence dans la barre de commandes à côté du bouton préférences.](../media/MAC-WN-MCPlannerSync.png)

Pour en savoir plus à ce sujet, consultez cet article et cette vidéo pour voir comment cela fonctionne : Suivre les billets de votre centre [de messages dans le Planificateur](https://docs.microsoft.com/Office365/Planner/track-message-center-tasks-planner)

### <a name="documentation-training-and-videos"></a>Documentation, formation et vidéos

- Tout nouveau et juste à temps pour Microsoft Ignite :[le Hub virtuel.](https://adoption.microsoft.com/virtual-hub/) Une formation technique approfondie pour les professionnels de l’informatique et les développeurs. Recherchez rapidement environ 20 nouvelles vidéos dans #SIDETRACKED, le nom de la piste d’administration Ignite cette année.
- Nouveautés de la série de vidéos [Microsoft 365](https://www.youtube.com/watch?v=OVjb2lGJ4GU&t=2s) : ce mois-ci, nous allons vous parler des nouvelles fonctionnalités disponibles dans tableau blanc pour Teams et sur le web, de l’automatisation de l’approvisionnement des utilisateurs sur Azure AD, des nouveaux déclencheurs et actions Power Automate dans Teams, et bien plus encore. Et restez à l’écoute pour le mois prochain, où nous allons avoir un récapitulatif de tous les événements formidables qui se produisent à Ignite !
- Nous avons repensé la page de [documentation de Microsoft 365](https://docs.microsoft.com/microsoft-365) qui se concentre d’abord sur les solutions. Nous mettrons en évidence les nouvelles solutions dès qu’elles seront disponibles sur cette page, donc gardez un œil à l’œil.

![Nouvelle page d’accueil de la documentation sur les solutions Microsoft 365 avec des solutions telles que « Permettre aux travailleurs à distance de travailler à distance ».](../media/MAC-WN-M365Docspage.png)

## <a name="july-2020"></a>Juillet 2020

### <a name="getting-ready-for-ignite-2020"></a>Préparation pour Ignite 2020

Dans la mesure où nous allons passer à la période Ignite chez Microsoft, nous ne publions pas autant de fonctionnalités que nous avons beaucoup à discuter au cours de nos sessions.

La prochaine mise à jour de cet article aura lieu le jour d’ouverture de notre premier ignite en ligne uniquement. Et cette année, il est gratuit ! Check it out, get signed up: [Microsoft Ignite 2020](https://www.microsoft.com/ignite).

### <a name="your-products"></a>Vos produits

La gestion des abonnements a fait beaucoup de travail pour accélérer le chargement de la page, trouver plus rapidement ce que vous recherchez et respecter les normes d’accessibilité web (directives[WCAG 2.1).](http://www.w3.org/TR/WCAG21/)

- **Nouvelle conception du** tableau : le tableau a été repensé afin de pouvoir grouper des abonnements similaires. Go to **Billing**  >  **Your products**.
- **Détails du produit**: obtenez plus de détails que jamais sur vos abonnements en sélectionnant le produit dans la liste.
- **Faites tout à partir d’ici**: et vous n’avez pas besoin de vous déplacer sur plusieurs pages pour gérer un produit. Par exemple, si vous devez annuler un abonnement, le panneau s’ouvre pour y faire l’action.

![Page Produits avec le panneau Annuler l’abonnement ouvert.](../media/MAC-WN-SubscrDetails.png)

### <a name="domains"></a>Domaines

La gestion de domaine peut être compliquée et nous avons publié une nouvelle fonctionnalité pour faciliter cette tâche. Go to Settings > Domains and then select a domain to get more information about your domain and the domain’s health.

:::image type="content" source="../media/MAC-WN-DomainDNS.PNG" alt-text="Page de détails des domaines pour contoso.com":::

### <a name="docs-training-and-videos-july-2020"></a>Documentation, formation et vidéos (juillet 2020)

Nouveautés de la série de vidéos [Microsoft 365](https://youtu.be/m1Nu8WJgCDY) : ce mois-ci, nous abordons la nouvelle expérience Yammer pour le web et l’appareil mobile, l’intégration de l’application communautés Yammer pour Microsoft Teams, les nouveaux packages de stratégie pour prendre en charge les employés et responsables de première ligne, et bien plus encore.

## <a name="june-2020"></a>Juin 2020

### <a name="keeping-up-with-office-whats-new-management"></a>Prise en charge de la gestion des nouveautés d’Office

Il y a quelques mois, nous avons ajouté un paramètre qui vous permet de gérer les messages Nouveautés qui s’affiche dans les applications [Office d’un utilisateur.](#office-whats-new-management) Ce mois-ci, nous avons publié une nouvelle carte de page **d’accueil** qui vous aidera à agir rapidement et à suivre les messages nouveautés que vous souhaitez montrer aux utilisateurs de votre organisation.

### <a name="docs-training-and-videos-june"></a>Documentation, formation et vidéos (juin)

- [Mise en place de Teams](https://support.microsoft.com/office/184f1aba-2f91-43f0-86e1-9fae607e24f6)

## <a name="may-2020"></a>Mai 2020

### <a name="new-update-channel-for-office"></a>Nouveau canal de mise à jour pour Office

Le 12 mai, nous avons annoncé la disponibilité d’un nouveau canal de mise à jour pour Office : canal d’entreprise mensuel. Ce canal de mise à jour fournit à vos utilisateurs de nouvelles fonctionnalités Office une fois par mois, le deuxième mardi du mois.

Si vous autorisez vos utilisateurs à installer eux-mêmes Office à partir du portail, vous pouvez sélectionner le canal d’entreprise mensuel pour eux. Pour ce faire, connectez-vous au Centre d’administration Microsoft 365 et allez à Afficher tous les paramètres d’organisation   > **paramètres**  >    >  **Paramètres Services**  >  **Paramètres Logiciels Office**. Si vous **sélectionnez Une fois** par mois (canal d’entreprise mensuel), toutes les nouvelles installation autonomes d’Office seront configurées pour utiliser le canal d’entreprise mensuel.

Conjointement avec la publication du canal d’entreprise mensuel, nous révise également les noms des canaux de mise à jour existants. Par exemple, le canal mensuel est renommé Canal actuel. Les nouveaux noms prennent effet le 9 juin 2020.

Pour plus d’informations, voir [Modifications apportées aux canaux de mise à jour de Microsoft 365 Apps.](https://docs.microsoft.com/DeployOffice/update-channels-changes)

### <a name="new-admin-roles"></a>Nouveaux rôles d’administrateur

Nous avons ajouté de nouveaux rôles d’administrateur Azure Active Directory au Centre d’administration Microsoft 365.

- Le rôle d’administrateur d’identité hybride donne aux utilisateurs l’autorisation de gérer les services d’approvisionnement et d’authentification cloud.
- Le rôle d’administrateur réseau permet aux utilisateurs de gérer les emplacements réseau et de passer en revue les informations réseau pour les applications microsoft 365 Software as a Service.
- Le rôle d’administrateur d’imprimante accorde l’autorisation de gérer tous les aspects des imprimantes et des connexions d’imprimante.
- Le technicien d’imprimante est un sous-ensemble du rôle d’administrateur imprimante dans lequel ces utilisateurs peuvent inscrire et désins inscrire des imprimantes, et mettre à jour l’état de l’imprimante.
Pour en savoir plus sur ces rôles, voir [à propos des rôles d’administrateur.](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles)

### <a name="export-groups-list"></a>Exporter la liste des groupes

De nombreux administrateurs nous ont dit qu’ils ont besoin de partager des informations sur les groupes et leur utilisation aux personnes qui n’ont pas accès aux centres d’administration. Vous pouvez maintenant exporter la liste groupes vers un fichier CSV à des fins d’audit, ce qui signifie que vous pouvez faire sortir cet ancien script PowerShell. Pour l’essayer, sélectionnez **Groupes** de groupes, puis sélectionnez  >  Exporter **des groupes** dans la barre de commandes.

### <a name="microsoft-365-solution-and-architecture-center"></a>Centre de solutions et d'architecture Microsoft 365

Ce mois-ci, nous avons publié un nouveau site appelé Centre d’architecture et de [https://docs.microsoft.com](https://docs.microsoft.com) [solution Microsoft 365,](https://docs.microsoft.com/microsoft-365/solutions/solution-architecture-center)qui regroupe les conseils techniques dont vous avez besoin pour comprendre, planifier et implémenter des solutions Microsoft 365 intégrées pour une collaboration sécurisée et conforme. Dans ce centre, vous trouverez :

- Conseils sur les solutions de base
- Solutions de charge de travail et aide sur les scénarios
- Illustrations de solution et d’architecture (affiches!!!)
- Conseils spécifiques au secteur
- Principaux de conception d’architecture d’entreprise

### <a name="docs-training-and-videos-may"></a>Documentation, formation et vidéos (mai)

- Nouveautés de la série de vidéos **Microsoft 365**: ce mois-ci, nous allons découvrir la nouvelle expérience de support dans les centres d’administration et de sécurité et de conformité Teams, l’intégration du Planificateur au Centre de messages et la nouvelle disposition vidéo 3x3 dans Microsoft Teams. 
- La page du Centre d’administration [Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/) a été mise à jour pour vous aider à trouver ce dont vous avez besoin plus rapidement. Et si vous regardez cette page maintenant, nous avons ajouté une carte pour vous informer des mises à jour et modifications importantes.

## <a name="april-2020"></a>Avril 2020

### <a name="intune-roles-management"></a>Gestion des rôles Intune

[Avril 2020](#april-2020)

Nous l’avons fait ! Nous avons pris la deuxième étape vers une expérience de rôles unifiés et vous pouvez désormais gérer les rôles Intune dans le Centre d’administration Microsoft 365. Vous pouvez également tirer parti de fonctionnalités telles que la possibilité de rechercher des rôles et d’afficher les autorisations de rôle. Cela signifie que vous n’avez pas besoin de deux outils distincts pour gérer les rôles pour Microsoft 365 et Intune. Lorsque vous vous connectez au Centre d’administration Microsoft 365, vous voyez qu’il existe deux tableaux croisés dynamiques sur la page Rôles, un pour Azure AD et un pour Intune.

![Page Rôles avec le tableau croisé dynamique Intune sélectionné](../media/MAC-WN-IntuneRoles.png)

### <a name="sync-message-center-posts-to-planner"></a>Synchroniser les publications du Centre de messages avec le Planificateur

À partir du mois de mai, les administrateurs qui sont dans la version ciblée commenceront à voir le bouton « Synchronisation du planificateur » dans le centre de messages. Vous pouvez désormais suivre les messages qui ont besoin d’une action, sélectionner le type de messages que vous souhaitez suivre, affecter des messages à suivre en tant que tâches et marquer les messages pour une attention ultérieure.

[Rejoignez la publication ciblée](manage/release-options-in-office-365.md) pour commencer !

### <a name="need-help-launched-in-teams-admin-center--security-and-compliance-centers"></a>« Vous avez besoin d’aide ? » lancé dans le Centre d’administration Teams & de sécurité et conformité

Le Centre d’administration Teams, le Centre de sécurité et le Centre de conformité utilisent désormais le même « Besoin d’aide ? » fonctionnalité que le Centre d’administration Microsoft 365 utilise pour trouver de l’aide et contacter le support technique. Nous avons reçu de nombreux commentaires d’administrateurs qui vous ont fait part de votre souhait d’obtenir le même niveau d’aide et de support, et nous sommes heureux de vous en faire part. Essayez et faites-nous part de vos commentaires !

#### <a name="need-chat"></a>Vous avez besoin d’une conversation ?

Nos agents de support technique travaillent à domicile tout en prenant en charge les cas clients et les limitations sur la bande passante Internet tout en travaillant à domicile peuvent avoir un impact sur la qualité des appels des clients. Pour continuer à vous aider, nous avons lancé l’option de support de conversation en direct pour les clients commerciaux dans le Centre d’administration Microsoft 365.

Lors de la création d’une demande de service, vous verrez désormais la conversation en tant qu’option, en plus du téléphone et de la messagerie. Sélectionnez la conversation comme canal de communication favori et créez la demande. Une fois que vous avez créé la demande, vous pouvez démarrer la conversation lorsque vous êtes prêt à discuter avec des agents Microsoft.

### <a name="teams-updates"></a>Mises à jour teams

Avec l’utilisation accrue de Teams, nous avons ajouté quelques fonctionnalités pour vous aider à les gérer.

- Une nouvelle carte de recommandation sur la page d’accueil du Centre d’administration indique les utilisateurs qui n’ont pas activement utilisé Teams pendant 30 jours. Vous pouvez envoyer à ces utilisateurs un e-mail de formation pour les aider à commencer à utiliser Teams.
- Rassembler des personnes avec  des équipes : accédez au programme d’installation pour voir une nouvelle page pour vous aider à activer Teams pour les utilisateurs sous licence et autoriser l’accès invité, afin que vous pouvez travailler avec des clients externes dans Teams.
- Une carte Microsoft Teams est désormais épinglée par défaut à votre page d’accueil. Il indique si Teams est allumé et si l’accès invité est autorisé. Il vous permet également de vérifier l’état de configuration des utilisateurs de Teams nouvellement titulaires d’une licence et de vérifier si des problèmes réseau peuvent avoir un impact sur les utilisateurs de Teams.
- Enfin, Teams est désormais une étape du flux de mise en place initial si vous avez acheté une licence qui inclut Teams.

### <a name="productivity-score"></a>Score de productivité

Le Score de productivité fournit des informations sur la façon dont les utilisateurs utilisent les services cloud de Microsoft et les expériences technologiques qui les supportent. Le score reflète les performances de votre organisation par rapport aux mesures de l’expérience des employés et des technologies, et compare votre score avec les organisations telles que les vôtres. Ce mois-ci, nous introduisons les nouveaux concepts suivants dans l’expérience de prévisualisation :

- Vue de tendance des informations principales sur la page d’accueil et les pages de détails de catégorie - Catégories d’analyse de point de terminaison et de connectivité réseau ajoutées à l’expérience technologique
- Informations pertinentes sur l’expérience technologique présentées dans les catégories Expérience des employés
- Nouvelle catégorie communications dans le cadre de l’expérience des employés
- Détails utilisateur avec les métadonnées organisationnelles dans les catégories Expérience utilisateur

Si vous souhaitez en savoir plus, consultez le blog : Mesurer et améliorer l’expérience [Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/measure-and-improve-the-microsoft-365-experience-with-microsoft/ba-p/1348618)avec le Score de productivité Microsoft. Le score de productivité est actuellement en prévisualisation privée. [Rejoignez la prévisualisation privée du score de](https://aka.ms/productivityscorepreview) productivité pour commencer.

### <a name="groups-updates"></a>Mises à jour de groupes

Nous avons deux mises à jour pour les groupes ce mois-ci :

- Vous pouvez désormais modifier les adresses de messagerie pour les groupes Office 365 (également appelés groupes dans Outlook et bientôt appelés groupes Microsoft 365).
- Nous avons entendu vos commentaires et ajouté une messagerie d’erreur plus claire pour savoir pourquoi vous ne pouvez pas convertir un groupe en Équipe Microsoft.

### <a name="docs-videos-and-training-april"></a>Documents, vidéos et formation (avril)

Nouveautés de la série de vidéos **Microsoft 365**: ce mois-ci, nous couvrent des conseils et des ressources pour aider les petites entreprises à passer au travail à distance, notamment la mise en place de Microsoft Teams, les ressources de formation professionnelle à distance pour rester en contact avec les clients et les partenaires, ainsi que la nouvelle offre Microsoft 365 Business Voice. [Nouveautés de Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2118096)

#### <a name="for-your-users"></a>Pour vos utilisateurs

- [Planifier une réunion](https://support.microsoft.com/office/c61b4f61-ee62-4a06-8bf7-0a1cd302700a)
- [Participer à une réunion Teams](https://support.microsoft.com/office/078e9868-f1aa-4414-8bb9-ee88e9236ee4)
- [Créer une équipe à l’échelle de l’organisation dans Teams](https://support.microsoft.com/office/037bb27a-bcc9-48fe-8d72-44d9482420a3)
- [Créer une équipe avec des invités](https://support.microsoft.com/office/11fbb083-52ee-434d-8c6e-63711fdafac7)
- [Rejoindre une équipe en tant qu’invité](https://support.microsoft.com/office/928d1eef-61e2-49ec-b754-c2fe86b34824)
- [Créer une adresse e-mail de groupe](https://support.microsoft.com/office/ded875f9-a9de-437f-b559-2ae4f235bb2b)

#### <a name="for-admins-and-business-owners"></a>Pour les administrateurs et les propriétaires d’entreprise

- [Permettre à votre petite entreprise de travailler à distance ](https://support.microsoft.com/office/9b91a85a-39b4-40a6-a590-0f9bea0ba8e6)
- [Gestion d’une petite entreprise distante](https://support.microsoft.com/office/9ac1a0f1-789b-4143-b954-5821d5d89298)
- [S’inscrire à Microsoft Business Basic](https://support.microsoft.com/office/9ac1a0f1-789b-4143-b954-5821d5d89298)
- [Configuration de la sign-in à deux facteurs](https://support.microsoft.com/office/9ac1a0f1-789b-4143-b954-5821d5d89298)

## <a name="march-2020"></a>Mars 2020

### <a name="featured-feedback-fix-improve-add-user-reliability-for-licensing"></a>Correctif des commentaires : améliorer la fiabilité de l'« ajout d’utilisateur » pour la gestion des licences

Nous avons reçu de nombreux commentaires des administrateurs sur la difficulté d’attribuer des licences lors de l’ajout d’utilisateurs. Nous avons effectué la première mise à jour de ce correctif et nous avons migré vers un service en arrière-plan plus fiable pour traiter ces demandes. En cas de problème, vous recevrez maintenant un message d’erreur qui vous permet d’essayer à nouveau.

![Ajouter la page de confirmation de l’utilisateur avec l’erreur.](../media/MAC-WN-ImprovedLicensing.png)

### <a name="microsoft-teams-home-page-card"></a>Carte de page d’accueil Microsoft Teams

Avec la mise à jour de l’utilisation de Teams, certaines organisation obtiennent une carte de tableau de bord épinglée qui rend l’utilisation de Teams plus découvrable. La carte comprend également des liens vers des documents et des formations pour aider votre organisation à passer au travail à distance. Il vous suffit **d’aller sur la** page d’accueil pour voir la nouvelle carte.

![Carte de page d’accueil Microsoft Teams](../media/MAC-WN-TeamsCard.PNG)

### <a name="customize-your-organizations-sharepoint-mobile-app-theme"></a>Personnaliser le thème de l’application mobile SharePoint de votre organisation

À l’aide du Centre d’administration Microsoft 365, vous pouvez désormais personnaliser le thème de votre organisation dans l’application mobile SharePoint pour iOS et l’application mobile SharePoint pour Android. Cette fonctionnalité offre une expérience d’application intranet mobile qui peut correspondre à votre SharePoint Online pour les employés qui sont en action. La personnalisation de thème inclut l’image de votre logo, la couleur de la barre de navigation, les couleurs de texte et d’icône, ainsi que les couleurs d’accentuation, ce qui vous aide à faciliter la reconnaissance.

![Diagramme mappant les paramètres du Centre d’administration à l’application mobile.](../media/MAC-WN-CustThemeSP.png)

### <a name="improvements-to-the-add-a-group-wizard"></a>Améliorations apportées à l’Assistant « Ajouter un groupe »

Lorsque les administrateurs ont créé un nouveau groupe et en ont fait une équipe en même temps, ils peuvent affecter des propriétaires qui n’ont pas de licence qui inclut Teams. Et cela a créé des difficultés. Nous avons mis à jour le flux de l’Assistant pour vérifier que les propriétaires ont une licence Teams et s’ils n’ont pas la possibilité de transformer le groupe en équipe est désactivé.

### <a name="microsoft-365-offerings-for-small-and-medium-businesses"></a>Offres Microsoft 365 pour les petites et moyennes entreprises

Nous savons qu’il s’agit d’une annonce pour le mois prochain, mais nous voulons nous assurer que vous êtes prêt.

À compter du 21 avril, nous a apporté des modifications relatives à nos abonnements Office 365 pour les petites et moyennes entreprises et à Office 365 ProPlus. Ces produits utiliseront désormais la marque Microsoft 365.

Les nouveaux noms de produits entrent en vigueur le 21 avril 2020. Il s’agit d’une modification apportée au nom du produit uniquement, et il n’existe aucune modification de tarification ou de fonctionnalité pour le moment.

|Nom actuel |Nouveau nom  |
|---------|---------|
|Office 365 Business Essentials     |   Microsoft 365 Business Basic      |
|Office 365 Business Premium     |    Microsoft 365 Business Standard     |
|Microsoft 365 Business     |    Microsoft 365 Business Premium     |
|Applications Microsoft 365 pour les PME     |    Applications Microsoft 365 pour les entreprises       |
|Office 365 ProPlus    |   Applications Microsoft 365 pour les entreprises      |

### <a name="videos-training-and-docs"></a>Vidéos, formation et documents

Nouveautés de la série [web Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2118096): dans l’épisode de ce mois, nous mettons en évidence l’anniversaire de 3 ans de Microsoft Teams et abordons de nouvelles fonctionnalités, notamment l’amélioration de la qualité audio dans les réunions en ligne, les communications ciblées pour les responsables de première ligne avec l’application Shifts, Teams et l’interopérabilité client Skype, et bien plus encore.

## <a name="february-2020"></a>Février 2020

### <a name="featured-feedback-fix-multi-organization-switcher"></a>Correctif des commentaires mis en avant : s’il s’est multi-organisation

Nous avons reçu de nombreux commentaires de partenaires et d’administrateurs sur les défis liés à la gestion de plusieurs organisation cloud Microsoft. L’une de nos premières fonctionnalités de gestion multi-organisation est le s **switcher Organization,** qui vous permet de basculer entre les organisations que vous gérez en seulement 2 clics.
> [!TIP]
> Vous n’avez rien à faire pour faire apparaître le commutateur d’organisation tant que vous êtes le partenaire de registre d’au moins une organisation.

1. Dans le Centre d’administration Microsoft 365, sélectionnez le nom de l’organisation.
![Capture d’écran : en haut de la page d’accueil affichant le nom du profil de l’organisation avec l’icône du commutateur.](../media/MAC-Organization-switcher.png)

2. Dans le sélecateur d’organisation, sélectionnez l’organisation que vous souhaitez gérer.
![Capture d’écran : commutateur client de mes organisations avec client Consolidated Messenger mis en évidence](../media/MAC-OrgSwitcherSelected.png)

C’est littéralement cela!!!

### <a name="groups"></a>Groupes

Quelques modifications ont été apportées dans la zone des groupes ce mois-ci :

- **Trier par nom de groupe**: vous pouvez trier les groupes par ordre alphabétique, en sélectionnant la colonne Nom **du** groupe.
- Restaurer les groupes **Microsoft 365** supprimés : vous n’avez plus besoin d’aller au Centre d’administration Exchange pour restaurer les groupes Microsoft 365 supprimés. Go to **Microsoft 365 admin center** \> **Groups** \> **Deleted groups** \> (select a group from the list) \> **Restore group**. Il rétablit le groupe  dans la liste Groupes et restaure le courrier électronique, les conversations, le bloc-notes, les fichiers et le calendrier du groupe.

### <a name="videos-training-and-docs-february"></a>Vidéos, formation et documents (février)

- Nouveautés de la série de vidéos **Microsoft 365**: ce mois-ci, nous nous concentrons sur les fonctionnalités de recherche personnalisées pour SharePoint Online, la fonctionnalité de gestion « Nouveautés » d’Office qui vous permet d’afficher ou de masquer des fonctionnalités spécifiques aux utilisateurs finaux via le volet d’aide dans l’application, les dernières mises à jour de sécurité et de conformité dans Yammer, et bien plus encore. Voici le dernier épisode : [Nouveautés de Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2118096)

- **Déplacement de documents**: nous avons combiné les articles web de l’administrateur Office 365 avec le contenu Microsoft 365 et vous avez peut-être remarqué la nouvelle URL. Par exemple, cet article était hébergé sur **: docs.microsoft.com/Office365/Admin/whats-new-in-preview**, mais l’URL est maintenant **: docs.microsoft.com/microsoft-365/admin/whats-new-in-preview**. Si vous avez des pages avec signet, vous devez mettre à jour vos liens . toutefois, les liens de contenu sont redirigés vers le nouveau repo de contenu.

## <a name="january-2020---happy-new-year"></a>Janvier 2020 - Bonne année

> [!NOTE]
> Savez-vous qu’il existe une série de vidéos Nouveautés de [Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2118096) sur YouTube ? Il présente les dernières fonctionnalités que nous avons déployées pour les utilisateurs. Tous les mois, nous allons commencer à créer un lien vers le dernier épisode de la section [Vidéos, formation et documents.](#videos-training-and-docs) <br> <br> Voici le dernier épisode : [Nouveautés de Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2118096)

### <a name="dark-mode"></a>Mode sombre

Lorsque nous avons déployé le mode sombre pour la première fois, il était disponible uniquement sur la page d’accueil. Le mode Sombre n’est plus en mode aperçu et est dans la version ciblée sur la plupart des pages du Centre d’administration.

1. Tout d’abord, vous devez activer la publication ciblée : allez **aux** préférences de publication du profil d’organisation \>  \>  \> **paramètres des paramètres.**
1. Ensuite, pour activer le mode sombre, sélectionnez la **page** d’accueil, puis sélectionnez le **bouton mode** Sombre. (Il se place à côté du **champ Recherche** et du lien Nouveautés **de cet** article.)
1. Pour toute page en mode sombre disponible, le bouton se  trouve en haut de la page, à côté du nouveau bouton bascule centre d’administration.

### <a name="office-whats-new-management"></a>Gestion des nouveautés d’Office

Les administrateurs souhaitent contrôler la façon dont Microsoft communique « Nouveautés » à leurs utilisateurs dans les applications Office. Vous avez maintenant ce contrôle. Go to **Settings** \> **Office What’s New management Preview**. Sélectionnez une fonctionnalité pour afficher ses détails, puis vous pouvez sélectionner le bouton Masquer des utilisateurs si vous ne souhaitez pas que vos utilisateurs voient un message particulier « Nouveautés ».  Par exemple, votre organisation peut attendre d’en savoir plus sur une fonctionnalité jusqu’à ce que tous les membres de votre organisation y soient formés.

![Capture d’écran de l’aperçu des nouveautés d’Office avec le volet d’informations d’une fonctionnalité ouvert.](../media/whatsnew-officemgmt-preview.png)

Cette fonctionnalité a été publiée pour la première fois en prévisualisation en novembre, mais vous devez connaître quelques mises à jour de fonctionnalités : les mises à jour de la version d’aperçu de gestion [d’Office nouveautés](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-what-s-new-management-preview/ba-p/1020438) sont désormais disponibles.

### <a name="partners"></a>Partenaires

Howdy, Partners! (Je n’ai pas pu m’aider.) Nous avons également une mise à jour ce mois-ci. Il existe une nouvelle fonctionnalité qui permet aux partenaires de donner aux clients CSP la possibilité d’accepter leur contrat client Microsoft (MCA) dans la **section** Comptes de facturation du Centre d’administration. Dans cette nouvelle expérience :

1. Le client reçoit un e-mail d’invitation avec un lien pour accepter la relation de partenaire et le MCA.
2. Une fois que le client s’est abonné, il peut afficher et accepter les autorisations mca et partenaire, directement à partir du centre d’administration.

### <a name="resource-mailboxes"></a>Boîtes aux lettres de ressources

La liste des boîtes aux lettres de ressources a été mise à jour avec le nouveau style. Dans le Centre d’administration Microsoft 365, go to **Resources** \> **Rooms & equipment**.

### <a name="videos-training-and-docs-january"></a>Vidéos, formation et documents (janvier)

Consultez la formation pour les administrateurs de petite entreprise publiée en janvier :

- [Créer votre site web d’entreprise](https://support.microsoft.com/office/3325d50e-d131-403c-a278-7f3296fe33a9)
- [Trouver des réponses et de l’aide](https://support.microsoft.com/office/7f681212-c649-4a3e-a43b-32b1d1e58988)
- [Obtenir de l’aide ou une assistance technique](https://support.microsoft.com/office/18948a4c-3eb1-4b30-b1bc-a4cc29eb7655)
- [Supprimer un utilisateur](https://support.microsoft.com/office/6bcdad7b-732a-4260-997a-8c176bc3d9d6)
- [Choisir un abonnement Microsoft](https://support.microsoft.com/office/b9f7c78e-430f-4117-89ec-2eeb1dced2ca)
- [Vue d’ensemble de la sécurité de Microsoft 365 pour les entreprises](https://support.microsoft.com/office/3274b159-a825-46d7-9421-7d6e209389d1)

## <a name="november-and-december-2019"></a>Novembre et décembre 2019

Nous combinons les actualités de novembre et de décembre, car après Ignite, nous n’avions que très peu d’annonces à effectuer. Rendez-vous dans la nouvelle année !

### <a name="change-from-credit-card-to-invoice-payment"></a>Modification du paiement par carte bancaire en paiement par facture

Nous avons commencé à déployer la possibilité de modifier votre mode de paiement de carte bancaire en facture. Go to **Billing** \> **Your products,** select a subscription, and then select the **Edit** link next to the credit card payment.

![Capture d’écran : section Facturation de la carte d’abonnement avec une carte de crédit comme mode de paiement.](../media/MAC-BillingEditCreditCard.png)

Vous souhaitez en savoir plus à ce sujet ? [Passer du mode de paiement par carte bancaire ou compte bancaire au mode de paiement par facture](../commerce/billing-and-payments/change-payment-method.md)

### <a name="global-reader"></a>Lecteur général

Nous avons mentionné le rôle de lecteur global dans la version [d’octobre 2019 - Ignite,](#october-2019---ignite-edition)mais dans le cadre de son déploiement plus large, examinons quelques détails :

- Le rôle de lecteur global est l’équivalent en lecture seule du rôle d’administrateur général. Le lecteur global peut voir tout ce que l’administrateur global est autorisé à faire.
- À quelques exceptions près, comme certaines fonctionnalités de conformité et de sécurité, les lecteurs globaux ont accès à tous les centres d’administration cloud Microsoft que votre organisation dispose d’une licence d’utilisation.
- Attribuez le rôle de lecteur global aux utilisateurs qui en ont besoin pour la planification, les audits et les enquêtes.
- Vous pouvez également combiner le rôle de lecteur global avec un autre rôle qui dispose de moins d’autorisations. Par exemple, un propriétaire de petite entreprise peut se voir attribuer les rôles de lecteur global d’administrateur de facturation afin qu’il puisse payer les factures et rester au fait des modifications apportées à son  +   organisation cloud.
- Les lecteurs globaux peuvent se rendre sur n’importe quelle page du Centre d’administration Microsoft 365. Lorsqu’ils ouvrent une page modifiable, un avertissement s’ouvre en haut de la page leur signalant qu’ils n’ont pas l’autorisation d’enregistrer les modifications et que le bouton Enregistrer est désactivé.

Nous aimeriez obtenir vos commentaires sur le rôle de lecteur global et les autorisations basées sur les rôles que vous souhaitez voir à l’avenir. [Fournir des commentaires sur les autorisations basées sur les rôles](https://office365.uservoice.com/forums/273493-office-365-admin/suggestions/10115430-have-a-consistent-experience-when-assigning-admin)

### <a name="new-settings-page"></a>Page Nouveaux paramètres

Le **profil de** l’organisation, la sécurité **&** confidentialité et les pages de & services ont tous été **combinés** en une seule page avec 3 onglets verticaux. Et la meilleure partie : à partir d’un seul emplacement, vous pouvez désormais rechercher tous les paramètres.
![Capture d’écran : page paramètres avec le champ « Rechercher tous les paramètres » mis en évidence en haut de la page.](../media/MAC-SettingsMultiPivotSearch.png)

### <a name="training--docs"></a>Documents de & formation

Cette section est une nouvelle fonctionnalité de cet article, dans laquelle nous allons commencer à créer un lien vers une nouvelle formation et une nouvelle documentation que nous pensons intéressante.

En novembre, nous avons publié quelques parcours d’apprentissage sur le site [web Microsoft Learn](https://docs.microsoft.com/learn/) pour aider les professionnels de l’informatique à en savoir plus sur Microsoft 365 et à s’y former. Consultez-les :

- [Principes de base de Microsoft 365](https://docs.microsoft.com/learn/paths/m365-fundamentals/)
- [Étendre les principes de base d’Office](https://docs.microsoft.com/learn/paths/extend-office-fundamentals/)
- [Microsoft 365 - Moderniser votre déploiement d’entreprise avec Windows 10 et Microsoft 365 Apps for enterprise](https://docs.microsoft.com/learn/paths/m365-getmodern/)
- [Gérer le déploiement au sein de votre entreprise avec Microsoft 365](https://docs.microsoft.com/learn/paths/manage-enterprise-deployment-m365/)
- [Mettre à niveau Microsoft Office pour les services informatiques à l’échelle](https://docs.microsoft.com/learn/paths/m365-office-for-it/)
- [Fournir des applications et des bureaux à distance à partir d’Azure avec Windows Virtual Desktop ](https://docs.microsoft.com/learn/paths/m365-wvd/)
- [Moderniser votre lieu de travail avec Microsoft 365 et Surface pour les entreprises](https://docs.microsoft.com/learn/paths/modernize-workplace-with-m365-and-surface/)
- [Protéger les identités et accès avec Microsoft 365](https://docs.microsoft.com/learn/paths/m365-identity/)
- [Protéger les informations d’entreprise avec Microsoft 365](https://docs.microsoft.com/learn/paths/m365-information-protection/)
- [Gérer la sécurité avec Microsoft 365](https://docs.microsoft.com/learn/paths/m365-security-management/)
- [Se défendre contre les menaces avec Microsoft 365 Defender](https://docs.microsoft.com/learn/paths/m365-security-threat-protection/)
- [Gérer la collaboration en équipe avec Microsoft Teams](https://docs.microsoft.com/learn/paths/m365-manage-team-collaboration/)
- [Collaborer avec SharePoint dans Microsoft 365](https://docs.microsoft.com/learn/paths/m365-teams-sharepoint/)

## <a name="october-2019---ignite-edition"></a>Octobre 2019 - Ignite Edition

Bienvenue dans l’édition Ignite du Centre d’administration Microsoft 365. Bien entendu, il ne s’agit pas d’une liste complète d’annonces, mais voici quelques points forts. Consultez également les blogs Ignite pour plus d’informations sur les releases :

- [ADMIN - Améliorations en matière de sécurité, de productivité et de réseau pour Microsoft 365.](https://techcommunity.microsoft.com/t5/Microsoft-365-Blog/ADMIN-Security-Productivity-and-Network-Enhancements-for/ba-p/964019)
- [Nouveautés de Microsoft Teams - Ignite 2020](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/What-s-New-in-Microsoft-Teams-Ignite-2019/ba-p/937025).

### <a name="role-based-access-control"></a>Contrôle d'accès basé sur les rôles

De nombreuses modifications ont été apportées aux rôles dans le Centre d’administration depuis le début du déploiement en juin :

- **Comparer les rôles** : sélectionnez jusqu’à 3 rôles pour comparer les autorisations pour chacun d’eux. Cela vous aidera à trouver le rôle le moins permissif à attribuer aux utilisateurs. Go to **Roles**, use the multi-select checkbox in the first column to choose up to 3 roles, and then select **Compare roles**.

    ![Comparaison des rôles d’administrateur Exchange, d’administrateur du helpdesk et d’administrateur utilisateur.](../media/RBAC-CompareRoles.png)

- **Favoris :** vous pouvez ajouter une étoile à vos rôles favoris ou les plus utilisés, afin de pouvoir les trouver facilement en triant la colonne ou en créant un filtre.
- **Utilisateurs actifs**  >  **Gérer les rôles** : cette mise à jour a été mise à jour pour s’aligner sur les modifications apportées aux rôles. Comme pour la liste des rôles, nous avons étendu la liste par défaut des rôles aux rôles les plus utiles, mais vous pouvez voir tous les rôles en développez Afficher **tout par catégorie.**
- **Rôle de lecteur global** : vous l’avez demandé ! Compris! Le [rôle de lecteur](add-users/about-admin-roles.md) global !

### <a name="report-an-issue"></a>Signaler un problème

L’état du service a été mis à jour avec le nouveau style et si vous  êtes touché par un problème qui ne s’affiche pas dans votre tableau de bord d’état du service, vous pouvez signaler un problème pour le signaler à Microsoft. Go to **Health**  >  **Service health service**.

### <a name="viral-subscriptions"></a>Abonnements « Dont »

Comme vous le savez, les utilisateurs peuvent activer les abonnements gratuits pour un ensemble de produits tels que Power BI et App Connect. Vous pouvez maintenant voir les « abonnements de groupe » que vos utilisateurs tentent de faire. Go to **Billing**  >  **Your products**. Sélectionnez **le filtre Type de** compte sous l’onglet Abonnements pour voir les abonnements achetés par l’utilisateur. Si nécessaire, vous pouvez désormais supprimer ces abonnements de votre compte.

### <a name="user-templates"></a>Modèles de l'utilisateur

Les modèles vous permettent d’ajouter facilement de nombreux utilisateurs en enregistrer et en réutilisant les paramètres partagés pour ces utilisateurs. Vous pouvez enregistrer des valeurs pour les rôles, les licences attribuées, les informations de contact, l’emplacement, etc. Lorsque vous utilisez le modèle pour créer un utilisateur, il reçoit automatiquement la valeur enregistrée pour ces paramètres. Go to **Users**  >  **Active users,** and then select **User templates** to try it out.

### <a name="office-whats-new-management-preview"></a>Gestion des « nouveautés » d’Office (prévisualisation)

Lorsqu’une fonctionnalité Office importante est publiée dans une application Office, les utilisateurs obtiennent une carte « Nouveautés » pour en savoir plus sur la nouvelle fonctionnalité. Si vous ne souhaitez pas que les utilisateurs voient la carte, vous pouvez la masquer. Vous pouvez également choisir quand vous souhaitez que les utilisateurs voient la carte en l’affichant. Go to **Settings**  >  **Office What’s New management** to check it out.

### <a name="sharepoint-url-change"></a>Modification de l’URL SharePoint

Techniquement, il ne s’agit pas des actualités du Centre d’administration Microsoft 365, mais nous sommes ravis que nous voulions nous assurer que vous voyez ces actualités :
> [!IMPORTANT]
> Vous pouvez désormais accéder à VOTRE Centre d’administration SharePoint avec une URL régulière : [https://admin.microsoft.com/SharePoint](https://admin.microsoft.com/SharePoint)

Pour plus d’informations, voir Nouveautés du [Centre d’administration SharePoint.](https://docs.microsoft.com/sharepoint/what-s-new-in-admin-center)

## <a name="september-2019"></a>Septembre 2019

Nous sommes en train de monter en puissance pour quelques nouvelles fonctionnalités intéressantes d’Ignite 2019. Nous annonceons donc uniquement quelques nouvelles fonctionnalités publiées en septembre. Mais restez à l’écoute de l’article du mois suivant, il sera publié le premier jour d’Ignite !

### <a name="featured-feedback-fix--the-option-to-convert-the-deleted-users-mailbox-to-a-shared-mailbox-is-back"></a>Correctif des commentaires : l’option de conversion de la boîte aux lettres de l’utilisateur supprimé en boîte aux lettres partagée est de retour

Nous avons entendu vos commentaires haut et fort et nous avons permis de donner à quelqu’un d’autre l’accès à la boîte aux lettres d’un utilisateur supprimé en la convertissant en boîte **aux lettres partagée.** L’ajout de cette information à l’Assistant Suppression d’utilisateur vous permet de décider de l’utilisation des données :

- Courrier électronique : donner à quelqu’un d’autre accès à la boîte aux lettres de l’utilisateur supprimé en la convertissant en boîte aux lettres partagée.
- Fichiers : enregistrez leurs fichiers OneDrive et donnez l’accès à quelqu’un d’autre.
- Autorisations : supprimez les autorisations si d’autres personnes ont accès à cette boîte aux lettres.
- Alias : supprimez les alias de messagerie afin qu’ils soient immédiatement disponibles pour un autre utilisateur.
![Capture d’écran : Assistant Suppression d’utilisateurs avec les alias de messagerie, les autorisations, OneDrive et les options de messagerie affichées](../media/WhatsNew-DeleteUserWiz.png)

### <a name="initial-setup"></a>Configuration initiale

Nous avons mis à jour un autre de nos assistants de configuration initiale : Microsoft 365 pour les entreprises. Les étapes ont été simplifiées et nous avons déplacé deux des tâches de configuration dans la page d’installation :

- **Sécuriser les ordinateurs Windows 10** : configurer des stratégies pour mieux protéger vos appareils Windows 10 contre les virus, les programmes malveillants et les attaques par des pirates informatiques.
- **Installer** automatiquement Office : lorsque vous l’allumez et que les utilisateurs ont connecté leur PC à Microsoft 365 Business, leurs ordinateurs sont automatiquement mis à jour vers les dernières applications Office et restent à jour.

## <a name="august-2019"></a>Août 2019

### <a name="billing"></a>Facturation

Nous avons des mises à jour pour la facturation et les abonnements ce mois-ci :

- Abonnements basés sur les appareils : vous pouvez attribuer ou désattribuer des licences **Microsoft 365 Apps for Education (appareil)** à des appareils dans le Centre d’administration Microsoft 365. **Microsoft 365 Apps for Education (appareil)** est une licence de modules qui vous permet d’attribuer une licence à un appareil. Go to **Billing**  >  **Your products** to find and purchase the license.
- Gestion des licences basée sur l’utilisateur : nous avons mis à jour la façon dont vous attribuez des licences dans utilisateurs actifs utilisateurs  >   actifs au nouveau style. Pour plus d’informations, voir :
  - [Attribuer des licences aux utilisateurs](manage/assign-licenses-to-users.md)
  - [Annuler l'assignation des licences aux utilisateurs](manage/remove-licenses-from-users.md)

### <a name="setup-page-updates"></a>Mises à jour de la page d’installation

Le programme d’installation comporte désormais des catégories et des sections, y compris une **section** Recommandée pour vous, dans laquelle nous vous suggérons intelligemment l’étape suivante pour l’installation des fonctionnalités et la configuration de votre organisation. Nous avons également ajouté une nouvelle fonctionnalité pour configurer :

- **Microsoft Defender pour Office 365** : si votre organisation est titulaire d’une licence d’utilisation de Microsoft Defender pour Office 365 et que vous ne l’avez pas encore configuré ou que vous ne l’avez pas encore désactivé, cette page s’y trouve. Go to **Setup** to try it out.

### <a name="report-an-issue-august"></a>Signaler un problème (août)

Si vous êtes touché par un problème qui ne s’affiche pas dans votre tableau de bord d’état du service, la fonctionnalité Signaler un problème vous permet de nous en faire part rapidement et facilement.  Go to **Health**  >  **Service health service**.

## <a name="july-2019"></a>Juillet 2019

### <a name="message-center"></a>Centre de messages

Le centre de messages a été mis à jour avec la nouvelle conception et son apparence est incroyable !

![Capture d’écran : Centre de messages mis à jour avec l’onglet « Tous les messages actifs » sélectionné et le menu Filtre ouvert.](../media/MAC-MessageCenterUpdated.png)

- Vous pouvez désormais afficher **les messages par état.** Sélectionnez simplement l’un des onglets : Tous les **messages actifs,** Importance **haute,** **Messages** non lus et **Messages rejetés.**
- Vous pouvez également filtrer par **catégorie** Confidentialité des données, **Planifier les** **changements,** Empêcher ou résoudre les problèmes et Rester **informé** des catégories de messages.
- Sélectionnez un message dans la liste et vous avez  quelques options dans la barre de commandes : **Ignorer,** Marquer comme lu ou Marquer comme **non** lu, ou **Partager**.
- Lorsque vous ouvrez un message, vous avez encore plus d’options :
  - Copiez un lien du message dans le Presse-papiers pour l’enregistrer ultérieurement ou pour le partager avec vos collègues.
  - Marquez les messages **comme lus** **ou non lus.**
  - Faites part de vos  commentaires sur un message en sélectionnant J’aime ou J’aime, un volet de commentaires s’ouvre pour vous demander de fournir des commentaires spécifiques sur ce que vous avez aimé ou non sur ce message.

### <a name="navigation-pane-intelligence"></a>Informations sur le volet de navigation

 Le volet de navigation se rappelle maintenant de vos dernières actions et vous montre le volet dans le dernier état où vous l’avez laissé. Il rend également les éléments fréquemment utilisés visibles par défaut.

### <a name="initial-setup--the-setup-page"></a>Configuration initiale & page d’installation

Nous avons apporté des modifications intéressantes pour vous aider à configurer votre organisation. Tout d’abord, examinons la différence entre **l’installation** et la **page d’installation.** **Le programme** d’installation fait référence à l’Assistant d’installation initial que vous avez utilisé pour intégrer les services en ligne de Microsoft. Cela comprend généralement trois étapes spécifiques **: connecter un domaine,** **ajouter** des utilisateurs et **télécharger les applications Office.** La **page** d’installation est celle dans le Centre d’administration qui a recommandé de configurer des tâches pour vous assurer que vous exploitationz au mieux de vos abonnements, comme l’utilisation des fonctionnalités pour qui vous avez acheté des licences.

- **Programme d’installation** : l’Assistant Installation initiale a été mis à jour pour **les abonnements Microsoft 365 pour les** entreprises. Cette nouvelle conception permettra aux nouvelles organisations de passer par l’Assistant plus rapidement et avec un plus grand succès.
- **Page Installation** : la page **Installation** vous aide à terminer la configuration et la sécurisation des services qui sont offerts par vos abonnements. Vous pouvez également voir toutes les recommandations rejetées sur la page **d’installation.** Pour voir si elle est encore disponible pour vos abonnements, rendez-vous dans le programme d’installation du Centre **d’administration Microsoft 365.**  >  

### <a name="billing--subscriptions"></a>Abonnements & facturation

- **Type** de produit logiciel : vous pouvez désormais afficher les produits logiciels achetés via un fournisseur de services Cloud . Pour voir vos téléchargements et clés, rendez-vous sur **l’onglet**  >  **Facturation des logiciels** de vos  >  **produits.**
- Vous pouvez afficher les produits et services Azure modernes à partir du Centre d’administration Microsoft 365, que vous les avez achetés auprès de Microsoft ou d’un fournisseur tiers. Exemples de produits Azure modernes inclus :
  - Instances virtuelles azure réservées
  - Azure Support Plans
  - Azure Hybrid Use Benefits (AHUB)
  - Gérer les applications
  - Services d’appareil
  - Abonnements Azure

### <a name="simplify-multi-factor-authentication"></a>Simplifier l’authentification multifacteur

Les administrateurs ont accès à des informations sensibles dans votre organisation. Exiger que tous les administrateurs utilisent l’authentification multifacteur lors de la signature. Le nouvel Assistant vous aide à y arriver en une seule étape. Pour l’essayer, allez sur **Configurer** renforcer la sécurité  >  **de la signature.**

### <a name="users"></a>Utilisateurs

Les pages **Utilisateurs supprimés et** **Utilisateurs** invités ont été mises à jour avec le nouveau style.

- **Utilisateurs invités**: vous ajoutez des utilisateurs invités en les invitant à afficher ou partager des fichiers à partir de SharePoint ou OneDrive. Vous pouvez afficher les utilisateurs invités des  >  **utilisateurs invités des utilisateurs.**
- **Utilisateurs** supprimés : sur la **page** Utilisateurs supprimés mis à jour, vous pouvez faire toutes les actions que vous pouviez dans l’ancien centre d’administration, mais vous ajoutez et supprimez maintenant des colonnes. Nous avons également le choix entre un grand nombre d’options de colonne. En fait, il s’agit des mêmes colonnes que vous pouvez choisir sur la page **Utilisateurs** actifs.

## <a name="june-2019"></a>Juin 2019

### <a name="featured-feedback-request---dark-mode"></a>Demande de commentaires à l’écran - Mode sombre

L’affichage du Centre d’administration en mode sombre est en mode aperçu ! Vous ne pouvez le tester sur la page **d’accueil** que maintenant. Dans la page **d’accueil,** le bouton **mode** Sombre se trouve dans la barre de commandes en face du **lien** Nouveautés.

### <a name="roles-management"></a>Gestion des rôles

À la fin du mois de juin, nous avons commencé à déployer une nouvelle façon de gérer les rôles d’administrateur. Lorsqu’il est disponible pour vous, allez à  >  **Rôles**. En attendant, jetez un coup d’œil, c’est formidable !
<br> ![Capture d’écran : liste des rôles d’administrateur avec le volet d’informations sur les rôles d’administrateur utilisateur mis en évidence.](../media/MAC-AdminRoles-Featured.png) <br>

Cette nouvelle expérience permet de voir plus facilement qui dispose des autorisations d’administrateur et d’attribuer des rôles qui accordent le niveau d’accès droit à vos administrateurs. Nous avons également ajouté d’autres rôles à partir d’Azure AD afin que vous ne perdiez pas de temps à vous rendre dans plusieurs centres d’administration.
Que pouvez-vous faire d’autre ici ?

- Exportez une liste de tous les administrateurs de votre organisation qui se sont vus attribuer des rôles Azure Active Directory dans Microsoft 365.  
- Afficher tous les administrateurs affectés à un rôle spécifique, ajouter ou supprimer des administrateurs d’un rôle spécifique, rechercher des rôles par nom et mot clé, et en savoir plus sur ce que chaque rôle permet à un utilisateur de faire.
- Recherchez rapidement un rôle spécifique et créez des filtres.

### <a name="payment-method"></a>Mode de paiement

Nous avons mis à jour le paiement de vos abonnements. Go to **Billing**  >  **Bills & payments**  >  **Payment methods**. Vous pouvez voir vos modes de paiement dans un affichage Liste. Sélectionnez n’importe quel élément de la liste pour le supprimer, modifiez-le et consultez facilement l’abonnement auquel ce mode de paiement est associé.

## <a name="may-2019"></a>Mai 2019

### <a name="mays-featured-fix---case-sensitivity"></a>Correctif du mois de mai - Sensibilité à la cas

Maintenant, lorsque vous recherchez des boîtes aux lettres partagées, des contacts, des ressources et des autorisations de boîte aux lettres, vos termes de recherche ne doivent pas être sensibles à la cas.

**Gestion des utilisateurs et des groupes** Ce mois-ci, nous avons mis à jour  les pages Bloquer  l’utilisateur, Réinitialiser le mot de **passe,** Liste des **contacts,** Affichage liste des groupes et pages de détails Groupes dans le nouveau style centre d’administration.

- Avec la  nouvelle vue de liste Groupes, vous obtenez des données plus riches sur vos groupes et vous pouvez personnaliser la façon dont vous voyez vos données, et la liste des groupes se rappelle de la façon dont vous souhaitez voir vos données. Par exemple, vous pouvez désormais filtrer les groupes avec **Teams** pour voir si vos groupes font partie d’une équipe et vous pouvez ajouter la colonne d’état **Teams.**
- La liste des groupes apporte également toutes les améliorations que nous avons apportées à l’expérience de liste dans la gestion des utilisateurs, y compris les actions rapides et la barre de commandes contextuelle.

**Recommandations**<br>
Vous pouvez voir une nouvelle fenêtre de recommandation dans votre centre d’administration : nous venons d’en ajouter 4. Bien entendu, vous ne verrez des recommandations que si nous pensons qu’elles seront bénéfiques à votre organisation. Mais n’attendez pas que nous vous montrons la recommandation : vous pouvez l’ajouter à partir de la bibliothèque de cartes.

- **Expiration du mot de** passe : nous recommandons que les mots de passe ne **expirent jamais.** Et si votre organisation a un paramètre différent, il se peut que vous venons de voir cette recommandation.
- **Trop d’administrateurs** globaux : étant donné que le nombre d’administrateurs globaux trop élevé est une menace pour la sécurité, si vous avez plus de 4 administrateurs globaux, vous verrez cette recommandation. Nous vous suggérons d’accorder aux utilisateurs uniquement l’accès dont ils ont besoin pour faire leur travail.
- Protection des appareils **Intune** : si vos licences incluent Intune et que nous détectons que vous n’avez pas terminé la configuration d’Intune ou inscrit vos appareils, nous vous recommandons de créer une stratégie Intune pour protéger les fichiers de votre organisation lorsque les utilisateurs y accèdent à partir de leurs appareils mobiles.
- **Obtenir les mises à jour mensuelles des fonctionnalités d’Office** : nous avons reçu des commentaires de nos très petits clients qui nous ont indiqué que lorsqu’ils obtiennent des mises à jour mensuelles des fonctionnalités Office, leurs utilisateurs sont ravis. Ainsi, si vous êtes une très petite entreprise et que vous recevez actuellement vos mises à jour de fonctionnalités Office tous les six mois, vous verrez cette recommandation.

**Paramètres** <br>
En ce qui a été le cas des paramètres, il y a eu quelques modifications. La plupart du temps, il suffit de mettre à jour les paramètres existants vers le nouveau style du Centre d’administration. À mesure que nous avancerons et ajoutons de nouveaux paramètres que vous n’avez jamais vus auparavant, nous commencerons à les mentionner ici. Et nous avons un seul paramètre à annoncer : **l’authentification moderne.** Oui, il existe un nouveau paramètre pour activer **l’authentification moderne**! Pour l’consulter, rendez-vous sur **Paramètres**  >  **Services &'authentification** moderne des  >  **applications.**

## <a name="april-2019"></a>Avril 2019

Les choses sont très bien pour le Centre d’administration. Nous avons lu vos commentaires et suggestions, répondu à la plupart d’entre eux et nous avons vraiment pris tout ce que vous avez à dire à cœur. Bien entendu, nous faisons toujours le travail pour nous assurer que tout est à parité avec l’ancien centre d’administration. N’oubliez pas que lorsque nous allons déployer de nouvelles fonctionnalités, il est possible que vous ne les receviez pas immédiatement.

### <a name="featured-feature---add-users"></a>Fonctionnalité featured - Ajouter des utilisateurs

Pour avril, nous vous présentez **l’Assistant** Ajouter un utilisateur qui vous présente... attendez.... ajout d’utilisateurs. Il s’agit d’ajouter pas à pas les informations de base de l’utilisateur telles que le courrier électronique et le nom complet, l’attribution d’une licence et d’un rôle, l’ajout de ses informations de contact, puis la révision du compte de l’utilisateur avant de valider. **Pourquoi avons-nous fait cette modification ?** Nous avons entendu vos commentaires sur le fait que vous n’aimez pas le défilement quasi infini pour ajouter des utilisateurs dans l’expérience précédente.
<br> ![Capture d’écran de l’Assistant Ajouter un utilisateur.](../media/MAC-AddUserWizard.png) <br>

Il existe deux façons de l’utiliser : <br>

1. Dans la page **d’accueil,** **sélectionnez Ajouter un utilisateur** à partir de la **carte de gestion utilisateur.** L’Assistant s’ouvre directement ici, vous n’avez donc pas besoin  de naviguer à partir d’un travail que vous faites sur la page d’accueil.
2. Sélectionnez **Utilisateurs**  >  **actifs utilisateurs,** puis **sélectionnez Ajouter un utilisateur** dans la barre de commandes.
<br><br>

Nous avons apporté quelques modifications à la gestion des utilisateurs, voici une liste rapide :

- Le volet Gérer **les** rôles a été mis à jour avec le nouveau style et est accessible. Nous avons également mis à  jour les **volets** Bloquer l’utilisateur et Supprimer l’utilisateur sur le nouveau style.
- **Gestion des licences de produit** - Position modifiée dans la barre de commandes.
- Il est désormais plus facile de modifier la photo d’un utilisateur. Dans **les utilisateurs** actifs, sélectionnez un utilisateur, puis **modifiez la photo** sous leur image.

### <a name="but-wait-theres-more"></a>Mais attendez ! Il y a d’autres choses à faire

- Une nouvelle bannière d’installation s’affiche sur la **page** d’accueil si vous n’avez pas terminé les étapes de configuration, telles que l’ajout d’un domaine, l’ajout d’utilisateurs et le téléchargement des applications Office.
- La **liste** de groupes et le volet d’informations ont été mis à jour avec le nouveau style. Go to **Groups**  >  **Groups** to view the changes.
  - Concernant les groupes, nous avons également ajouté un onglet **Microsoft Teams** au volet d’informations des groupes dans lequel vous pouvez transformer n’importe quel groupe Microsoft 365 en équipe. Pour « teamify » un groupe, sélectionnez n’importe quel groupe Microsoft 365 dans la liste, sélectionnez **l’onglet Microsoft Teams,** puis **créez une équipe.** Si le groupe est déjà une équipe, vous obtenez un lien pour le gérer à partir du Centre **d’administration Teams.**
  - Enfin, vous pouvez ajouter l’état **Teams à** la **liste des** groupes. Dans l’en-tête de colonne, **sélectionnez Sélectionner l’état**  >  **des colonnes Teams**  >  **Enregistrer.**
- **Nouveaux rôles d’administrateur limités** : nous avons publié de nouveaux rôles d’administrateur afin que vous ne donnez aux utilisateurs que l’accès dont ils ont besoin.
  - **Administrateur Kaizala**: les utilisateurs de ce rôle sont autorisés à effectuer toutes les tâches de gestion dans Microsoft Kaizala, notamment créer et gérer des utilisateurs dans l’annuaire Kaizala, gérer des groupes Kaizala, gérer des cartes d’action et des connecteurs, et créer des demandes de service.
  - **Administrateur de recherche**: les utilisateurs de ce rôle ont un accès total à toutes les fonctionnalités de gestion de Microsoft Search (recherche Microsoft) dans le Centre d’administration Microsoft 365. Les administrateurs de recherche peuvent déléguer les rôles d’administrateur de recherche et d’éditeur de recherche aux utilisateurs, et créer et gérer du contenu, comme des signets, des éléments&A et des emplacements. En outre, ces utilisateurs peuvent afficher le centre de messages, surveiller l’état du service et créer des demandes de service.
  - **Éditeur** de recherche : les utilisateurs de ce rôle peuvent créer, gérer et supprimer du contenu pour Recherche Microsoft dans le Centre d’administration Microsoft 365, y compris des signets, des éléments Q&A et des emplacements.
- Il y a un bon nombre de modifications **de** facturation ce mois-ci...
  - Vous pouvez maintenant mettre à jour le CVV pour les cartes de crédit existantes sans avoir à le supprimer et à l’ajouter à nouveau. Vous pouvez mettre à jour le CVV en allant aux **modes de** paiement des  >  **factures.**
    - Nous avons permis de localiser plus facilement vos **factures** et de comprendre les problèmes de facturation que votre compte peut avoir. Vous pouvez désormais voir vos factures dans le navigateur web au lieu de télécharger le PDF. Go to  >  **Invoices**.
    - Dans la page **Vos produits,** nous agrégerons désormais les informations de votre abonnement si vous avez plusieurs abonnements du même type.

## <a name="march-2019---weve-officially-released-the-admin-center"></a>Mars 2019 - Nous avons officiellement publié le Centre d’administration

Si vous avez manqué cette nouvelle, nous avons officiellement publié le centre d’administration Microsoft 365 nouveau et amélioré ! Voici le billet de blog où nous l’avons annoncé : Le nouveau Centre d’administration [Microsoft 365 disponible aujourd’hui.](https://techcommunity.microsoft.com/t5/Microsoft-365-Blog/The-new-Microsoft-365-admin-center-available-today/ba-p/377870) For March, we’ll rely on the blog post for you to check out the features released - plus, you can also read the post for the features that are getting released in the near future, which we’re not allowed to do in core content.
<br> ![Capture d’écran de la page d’accueil du Centre d’administration Microsoft 365.](../media/M365AC-HomePage.png) <br>
Nous avons une modification à la zone **d’abonnements** & facturation que nous voulons mentionner. Je veux dire, vous n’avez pas tous pensé que nous n’avons pas terminé de l’améliorer, n’est-ce pas ? Ce n’est pas le cas ! En fait, ce mois-ci, nous avons ajouté la possibilité de gérer vos relations de partenaires **aux** comptes  >  **de facturation.** À partir de là, vous pouvez passer en revue vos relations de partenaires entre les revendeurs advisor, CSP et indirects. Vous pouvez également accepter de nouvelles demandes de relation de partenaire, y compris les autorisations d’administrateur délégué.

Comme toujours, vos commentaires sont importants pour nous, alors continuez ! Sur n’importe quelle page du Centre d’administration, vous pouvez faire part de vos commentaires en sélectionnant Donner des commentaires en bas à droite, en dessous de **Besoin d’aide ?** 

## <a name="february-2019---billing--subscriptions-edition"></a>Février 2019 - Facturation & Subscriptions Edition

Ce mois-ci, nous allons nous concentrer sur toutes les améliorations que nous avons apportées aux domaines appelés « Facturation et abonnements ». Dans le passé, vous n’avez probablement pas fait référence à ces éléments de manière err ment, mais nous pensons que vous allez maintenant...

- **Modes de paiement** : nous avons entendu vos commentaires sur le fait que la mise à jour de votre mode de paiement était difficile et que nous avons apporté de nombreuses modifications. Go to **Billing**  >  **Payment methods**. Vous pouvez facilement voir vos modes de paiement, tels que votre carte Visa, et l’abonnement auquel elle est associée. Dans votre liste de modes de paiement, sélectionnez le menu **Plus** (3 petits points en regard de la date d’expiration), puis sélectionnez **Afficher les abonnements.** Vous pouvez également modifier et supprimer vos modes de paiement à l’aide du menu **Plus.**
- **Compte de facturation** : les clients de publication ciblée voient d’abord la page nouveau compte de facturation, puis nous la déployerons dans le monde entier. Lorsqu’il est disponible pour vous, go to **Billing**  >  **Billing account**. Que pouvez-vous faire sur la page nouveau compte de facturation ? Je suis content que vous avez demandé :
  - Mettez à jour l’adresse et les autres informations de contact dans votre profil d’organisation directement à partir de cette page. Vous n’avez pas besoin d’aller au profil d’organisation **paramètres,**  >  sauf si vous le souhaitez.
  - Et nous facilitez la vie des clients directs ou de licences en volume, vous pouvez accepter et examiner les contrats client à partir de **comptes de facturation.** Vous pouvez également vous connecter à d’autres organisation, ce qui vous permet de les lier pour partager des licences et des ressources.
- Nous avons également effectué quelques améliorations et résolutions de bogues plus petites :
  - Réactiver un abonnement avec un paiement par facture
  - Modifier l’adresse d’utilisation du service pour vos abonnements
  - Et sur la page Détails de l’inventaire, nous avons ajouté des améliorations de notification, nous vous lier à la page réelle où vous pouvez faire le travail, et il existe d’autres actions sur la carte de détails d’inventaire. Go to **Billing**  >  **Invoice View**  >  **details** on any invoice.

## <a name="january-2019---happy-new-year"></a>Janvier 2019 - Bonne année

- Ajout de **&** services : nous avons mis à jour d’autres pages de > **services** & services. Essayez les applications ou rapports intégrés pour voir la dernière version.
- **Vous recherchez des améliorations ?** Ne recherchez pas plus loin que **la zone** De recherche dans la barre de commandes. Il a été mis à jour pour vous aider à rechercher des tâches. Par exemple, essayez « réinitialiser le mot de passe » ou « Ajouter un utilisateur ».

### <a name="featured-feedback-fix---licenses-and-apps"></a>Correctif des commentaires - Licences et applications

Nous avons ré-combiné **les licences et les applications** dans le volet d’informations de l’utilisateur en fonction de vos commentaires. Nous avons initialement séparé les deux fonctionnalités pour fournir de l’espace pour les détails de toutes les licences et de toutes les possibilités d’application. Nous vous avons dit que la séparation des licences et des applications en deux volets ajoutait de la confusion. Nous avons écouté et réuni les licences et les applications sous un seul onglet. Vous pouvez désormais vous assurer qu’une application est désactivée dans toutes les licences attribuées à un utilisateur dans un seul volet. Les cookies et les cookies. Licences et applications. Nous l’avons maintenant.

Consultez la vidéo : **Utilisateurs > utilisateurs actifs > modifier** ou ajouter des **licences** > utilisateur et des applications
