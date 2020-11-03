---
title: Nouveautés du centre d’administration 365 de Microsoft
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
description: Centre d’administration Microsoft 365-Découvrez les fonctionnalités qui ont été ajoutées ce mois-ci.
ms.custom:
- MACDashWhatsNew
- AdminSurgePortfolio
ms.openlocfilehash: f861b346b1dcf9bb0670f1b6ac480f727e97af34
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48845215"
---
# <a name="whats-new-in-the-microsoft-365-admin-center"></a>Nouveautés du centre d’administration Microsoft 365

::: moniker range="o365-21vianet"

> [!NOTE]
> Certaines des informations contenues dans cet article peuvent ne pas s’appliquer à Office 365 géré par 21Vianet.

::: moniker-end

Nous ajoutons constamment de nouvelles fonctionnalités au [Centre d’administration Microsoft 365](microsoft-365-admin-center-preview.md), à la résolution des problèmes que nous apprendons et en apportant des modifications en fonction de vos commentaires. Jetez un œil à ce qui est disponible dès aujourd’hui. Certaines fonctionnalités sont déployées à des vitesses différentes à nos clients. Si vous ne voyez pas encore de fonctionnalité, [essayez de vous ajouter à la version ciblée](manage/release-options-in-office-365.md).

Et si vous souhaitez connaître les nouveautés d’autres services Cloud de Microsoft :

- [Nouveautés d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/whats-new)
- [Nouveautés du centre d’administration Exchange](https://docs.microsoft.com/Exchange/whats-new)
- [Nouveautés de Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/whats-new)
- [Nouveautés du centre de conformité Microsoft 365](https://docs.microsoft.com/Office365/SecurityCompliance/whats-new)
- [Nouveautés de Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/whats-new)
- [Nouveautés du centre d’administration SharePoint](https://docs.microsoft.com/sharepoint/what-s-new-in-admin-center)
- [Mises à jour Office](https://docs.microsoft.com/OfficeUpdates/)

## <a name="ignite-2020-august--september"></a>Allumage 2020 (août & Septembre)

Bienvenue dans Microsoft enflamme-notre première inversion en ligne uniquement. Nous espérons vous voir dans l’une de nos sessions : [catalogue de sessions Microsoft enflamme 2020](https://myignite.microsoft.com/sessions). Voici quelques-unes des choses que nous parlerons lors de l’enflamme. 
> [!NOTE]
> Toutes les fonctionnalités ne sont pas disponibles pour tout le monde immédiatement. Si vous ne voyez pas les nouvelles fonctionnalités, [Rejoignez la version ciblée](manage/release-options-in-office-365.md).

### <a name="multi-tenant-management"></a>Gestion mutualisée

Nous avons développé un ensemble de fonctionnalités pour les administrateurs multi-clients comme vous pour faire en sorte que votre travail soit plus rapide et plus efficace.

- **Vos clients** : basculez rapidement entre les clients que vous gérez.
- **Tous les clients** : une nouvelle page, qui vous permet d’afficher rapidement l’état de tous les services de vos clients, les demandes de services ouverts, les produits et la facturation, les tâches de configuration recommandées et le nombre d’utilisateurs de ce client.
- **Configuration** : la page de configuration mutualisée vous donne un aperçu de liste de la page de configuration, mais est organisée pour de nombreux clients. Vous pouvez voir les fonctionnalités qui ne sont pas activées, les tâches qui sont terminées pour tous les clients, les tâches que les clients doivent encore effectuer. Cette vue vous permettra de suivre l’adoption des fonctionnalités et de vous assurer que les tâches de configuration de sécurité recommandées sont toujours effectuées.
- **État du service** : l’affichage de l’état du service vous indique si un incident ou un avis affecte les clients. Elle vous indiquera également le nombre de clients gérés affectés. Il vous suffit de sélectionner un incident pour obtenir plus d’informations sous l’onglet vue d’ensemble, puis de basculer vers l’onglet clients affectés pour explorer et prendre en charge ce client.
- Les **migrations de boîtes aux lettres interclientes** sont un nouveau service, maintenant en préversion publique, qui vous permet de déplacer des boîtes aux lettres entre des clients sans avoir à débarquement, puis à intégrer des boîtes aux lettres. 
- **Partage de domaine interclient** : vous pouvez bientôt rejoindre une préversion privée pour les fonctionnalités qui vous permettent de partager un domaine entre plusieurs clients. Par exemple, si contoso achète Wingtip Toys, contoso peut partager le domaine avec Wingtip Toys afin que les utilisateurs des deux clients puissent utiliser « contoso.com » comme adresses de messagerie.

![Page État du service pour les clients multiples lorsque l’option incident est sélectionnée et que l’onglet locataires affectées est ouvert. Le menu de navigation dispose de tous les clients, configuration et service Health comme les seules options.](../media/MAC-WN-MTinServiceHealth.png)

### <a name="monitor-your-most-important-accounts"></a>Surveiller vos comptes les plus importants

Vous pouvez surveiller et suivre les messages électroniques ayant échoué ou retardés envoyés à vos utilisateurs qui ont un impact élevé sur l’activité, comme votre PDG. Vous pouvez effectuer le suivi des comptes prioritaires en ajoutant des utilisateurs à votre liste des comptes prioritaires dans le centre d’administration 365 de Microsoft. Ajoutez des cadres, des dirigeants, des responsables ou d’autres utilisateurs qui ont accès à des informations sensibles ou de priorité élevée.

Les comptes prioritaires sont uniquement disponibles pour les organisations qui remplissent les deux conditions suivantes :

- Office 365 E3 ou Microsoft 365 E3 ou Office 365 E5 ou Microsoft 365 E5.
- Au moins 10 000 licences et au moins 50 utilisateurs Exchange Online actifs mensuels.

![Page de configuration de la fonctionnalité : surveiller vos comptes les plus importants](../media/MAC-WN-PriorityAccounts.png)

Il existe deux façons de commencer :

- Accédez à **utilisateurs** , puis dans le menu « autres actions », sélectionnez **gérer les comptes à priorité** pour ajouter des utilisateurs à la liste.
- Accédez au **programme d’installation** , recherchez la tâche de configuration **surveiller vos comptes les plus importants** , puis sélectionnez **prise en main**.

Pour plus d’informations sur les comptes de priorité, consultez la [surveillance des comptes prioritaires](https://docs.microsoft.com/microsoft-365/admin/setup/priority-accounts) et [des problèmes de messagerie pour les comptes prioritaires](https://docs.microsoft.com/Exchange/mail-flow-best-practices/mail-flow-insights/mfi-email-issues-for-priority-accounts).

### <a name="search-faster-and-get-better-results-from-any-page"></a>Effectuer des recherches plus rapidement et obtenir de meilleurs résultats à partir de n’importe quelle page

Nous avons commencé à déployer une nouvelle expérience de recherche pour le centre d’administration, et nous ne pouvons pas attendre que vous le testiez. ![La zone de recherche a été déplacée vers la zone de bannière. Alt + S pour effectuer une recherche à partir de n’importe quelle page.](../media/MAC-WN-GlobalSearch.png)

- La zone de recherche a été déplacée vers la zone d’en-tête où elle indique « Centre d’administration Microsoft 365 », vous pouvez donc effectuer des recherches à partir de n’importe quelle page, pas seulement dans la page d’accueil. Nous avons même un raccourci : **ALT + S**.
- La recherche est plus intelligente et vous donnera de meilleurs résultats, encore plus rapidement. Essayez de taper « 2FA » pour commencer.
- Les résultats de la recherche sont organisés selon le type d’élément ou d’action que vous pouvez effectuer.
  - **Utilisateurs** : sélectionnez le nom de l’utilisateur et vous pouvez modifier ce dernier. Si vous sélectionnez le menu « autres actions » en regard de leur nom, vous pouvez réinitialiser leur mot de passe. Vous pouvez effectuer une recherche par nom d’affichage, nom, prénom, nom d’utilisateur ou adresse de messagerie principale, ainsi que comme alias de messagerie. Mais pour obtenir une correspondance exacte, recherchez par adresse e-mail principale ou par nom d’utilisateur.
  - **Groupes** : modifiez le groupe à partir de n’importe quelle page, ajoutez des membres, affectez des propriétaires.
  - **Actions** : de la même façon que vous pouvez rechercher un utilisateur, puis réinitialiser son mot de passe, vous pouvez également rechercher « réinitialiser le mot de passe » à partir de n’importe quelle page, puis réinitialiser un ou plusieurs mots de passe pour les utilisateurs.
  - **Navigation** : les résultats sous la navigation peuvent rapidement vous aider à accéder rapidement à une page dans le centre d’administration. Par exemple, la recherche « rôles » vous permet d’accéder à la page rôles pour les rôles Azure AD.
  - **Paramètres** : recherchez tout paramètre lié à votre organisation, les services auxquels vous vous abonnez, ainsi que les paramètres de sécurité et de confidentialité. 
  - **Domaines** : vous trouverez des liens rapides vers vos domaines, puis le lien vous dirigera vers la page d’analyse et d’intégrité de ce domaine.
  - **Documentation** : si nous ne trouvons pas de résultat pour vous, nous allons essayer de trouver de la documentation pour vous aider. Il faut un peu plus de temps pour que la liste d’articles organisée trouve une correspondance, donc patientez une seconde pour permettre à la recherche de trouver les résultats. 
  - **Commentaires** : vous n’avez pas trouvé ce que vous recherchiez ? Envoyez-nous vos commentaires à partir de la recherche. Nous allons ajouter la fonctionnalité de recherche pour des pages supplémentaires et d’autres fonctionnalités dans le centre d’administration.

### <a name="microsoft-365-admin-mobile-app"></a>Application mobile d’administration Microsoft 365

L' [application mobile d’administration de microsoft 365](https://www.microsoft.com/microsoft-365/business/manage-office-365-admin-app), incluse avec votre abonnement, vous permet de gérer Microsoft 365 à partir de votre appareil mobile afin que vous puissiez vous sortir de votre bureau pour effectuer des tâches quotidiennes. En fait, il existe plus de 90 fonctionnalités dans l’application, et nous venons d’en ajouter quelques autres :

- **Prise en charge des stratégies de gestion des applications mobiles et d’accès conditionnel de Microsoft Intune** : vous pouvez désormais utiliser votre appareil personnel pour gérer Microsoft 365 même si votre organisation a activé les stratégies de gestion des applications mobiles et d’accès conditionnel de Intune.
- **Notifications du centre de messages** : activez les notifications du centre de messages aux **paramètres**  >  **notifications** si vous souhaitez être alerté concernant les nouveaux messages du centre de messages. Par le biais des notifications, nous souhaitons vous assurer que vous restez informé des informations et événements importants au sein de votre client.
- **Alertes de facturation** : vous pouvez également activer les notifications **Settings** de facturation sur  >  les **notifications** de paramètres si vous souhaitez obtenir des notifications de facturation sur votre appareil si un abonnement est sur le paragraphe expire.
- **Mode sombre** : Bienvenue dans la partie sombre de l’application mobile. Il s’agissait de l’une de nos fonctionnalités les plus demandées. Accédez aux **Settings**  >  **thèmes** de paramètres pour l’activer.
- **Signalez un problème** : vous pouvez désormais signaler un problème dans l’application ou afficher les problèmes signalés par d’autres administrateurs. Pour en savoir plus, consultez l' **État du service** .

![Page d’intégrité dans l’application d’administration 365 de Microsoft avec des notifications pour le centre de messages, l’état du service, les alertes de facturation.](../media/MAC-WN-AdminMobileApp.png)

### <a name="usage-recommendations-for-small-and-medium-businesses"></a>Recommandations d’utilisation pour les petites et moyennes entreprises

Les petites et moyennes entreprises peuvent avoir une recommandation sur la page d' **Accueil** si certaines personnes de l’organisation n’utilisent pas activement Teams, OneDrive ou les applications Office. Lorsque vous consultez la recommandation, vous pouvez envoyer rapidement un message électronique Microsoft formation aux utilisateurs inactifs pour les aider à se familiariser avec l’application et à vous assurer que vous obtenez la valeur complète de vos abonnements.

### <a name="remote-work-collection"></a>Collection de travail à distance

En octobre, nous ajoutons une collection de travail à distance pour aider les propriétaires de petites entreprises et leur personnel à se connecter et à travailler à distance.  Le programme d’installation de la configuration de **travail à distance** est une liste organisée de toutes les fonctionnalités que Microsoft recommande d’activer le travail à distance de façon sécurisée et de collaborer efficacement. Pendant quelques semaines, vous pouvez le tester dans **le programme d’installation**  >  **à distance**.

![Page des notions de travail à distance dans le programme d’installation avec 7 tâches non démarrées.](../media/MAC-WN-RemoteWork.png)

Pour plus d’informations sur la façon d’autoriser le travail à distance et une adresse Web pratique facile à mémoriser et à partager, accédez à [aka.ms/Remote-Business](https://aka.ms/remote-business).

### <a name="need-help-moving-to-more-admin-centers"></a>Vous avez besoin d’aide ? passer à un plus grand nombre de centres d’administration

Nous examinons et mettons à jour le contenu et les outils de façon continue afin de suivre les modifications apportées au produit. Nous disposons désormais de nombreux outils de diagnostic en libre-emploi pour vous aider à résoudre les problèmes rapidement et efficacement. Voici quelques-uns qui ont été récemment ajoutés :

- Modifier la stratégie de limitation de service Web Exchange
- Vérification de l’état de mise en service et de validation de teams pour des utilisateurs spécifiques
- Corriger les problèmes d’installation de DKIM
- Diagnostiquer les erreurs d’inscriptions utilisateur Intune

Nous déployons la nouvelle et l’amélioration de l’expérience de prise en charge que vous voyez déjà dans le centre d’administration 365 de Microsoft pour les autres centres d’administration. Le centre d’administration teams et les centres d’administration de la sécurité et de la conformité disposent déjà de cette nouvelle expérience. Et bientôt, le **Centre d’administration Exchange** , le **Centre d’administration SharePoint** et **Office.com** seront mis à jour avec cette nouvelle expérience d’aide pour les administrateurs.

### <a name="manage-changes-with-microsoft-planner"></a>Gérer les modifications à l’aide du planificateur Microsoft

Dans mai, nous avons annoncé que vous serez bientôt en mesure de synchroniser les publications du centre de messages avec le planificateur Microsoft et que tous les utilisateurs pourront les utiliser.  Vous pouvez désormais créer des tâches à partir de messages, les affecter et les suivre pour terminer l’opération. La première fois, vous sélectionnez la **synchronisation du planificateur** vous devez vous connecter au plan approprié.

![Page du centre de messages avec « synchronisation du planificateur » mise en surbrillance dans la barre de commandes en regard du bouton Préférences.](../media/MAC-WN-MCPlannerSync.png)

Pour en savoir plus à ce sujet, consultez cet article et la vidéo pour voir comment elle fonctionne : [effectuer le suivi des billets de votre centre de messages dans le planificateur](https://docs.microsoft.com/Office365/Planner/track-message-center-tasks-planner)

### <a name="documentation-training-and-videos"></a>Documentation, formation et vidéos

- Une marque Neuve et juste à temps pour Microsoft enflamme--[le Hub virtuel](https://adoption.microsoft.com/virtual-hub/). Présentation détaillée de la formation technique pour les professionnels de l’informatique et les développeurs. Trouvez rapidement plus de 20 nouvelles vidéos dans le cadre de #SIDETRACKED, le nom de l’administrateur de l’allumage de cette année.
- Nouveautés de la série de vidéos [Microsoft 365](https://www.youtube.com/watch?v=OVjb2lGJ4GU&t=2s) : ce mois-ci, nous décrivons les nouvelles fonctionnalités disponibles dans le tableau blanc pour teams et sur le Web, l’automatisation de la mise en service des utilisateurs dans Azure ad, la création automatique de nouveaux déclencheurs et d’actions dans Teams, et bien plus encore. Et restez informé le mois prochain, où nous aurons un récapitulatif de tous les événements qui se produisent à l’allumage.
- Nous avons fait une nouvelle conception de la page de [documentation Microsoft 365](https://docs.microsoft.com/microsoft-365) qui se concentre sur les solutions d’abord. Nous allons mettre en surbrillance les nouvelles solutions dès qu’elles seront disponibles sur cette page, donc gardez un œil.

![Nouvelle page d’accueil pour la documentation sur les solutions Microsoft 365 avec des solutions telles que « permettre aux travailleurs à distance ».](../media/MAC-WN-M365Docspage.png)

## <a name="july-2020"></a>Juillet 2020

### <a name="getting-ready-for-ignite-2020"></a>Préparation pour enflamme 2020

À mesure que nous passons à la saison d’enflamme chez Microsoft, nous ne publions pas autant de fonctionnalités afin que nous ayons beaucoup à parler pendant nos sessions.

La prochaine mise à jour de cet article se tiendra le jour de notre première inversion en ligne uniquement. Cette année, c’est gratuit. Pour en savoir plus, connectez-vous : [Microsoft enflamme 2020](https://www.microsoft.com/ignite).

### <a name="your-products"></a>Vos produits

La gestion des abonnements a fait l’objet d’une grande quantité de travail, ce qui permet de simplifier le chargement de la page, de trouver plus rapidement ce que vous recherchez et de respecter les normes d’accessibilité Web ([directives WCAG 2,1](http://www.w3.org/TR/WCAG21/)).

- **Reconception de tableau** : le tableau a été repensé afin que vous puissiez regrouper les abonnements similaires. Accédez à **facturation** de  >  **vos produits**.
- **Détails** sur le produit : Obtenez plus d’informations sur vos abonnements en sélectionnant le produit dans la liste.
- **Procédez** comme suit : vous n’avez pas à vous rendre sur plusieurs pages pour gérer un produit. Par exemple, si vous devez annuler un abonnement, le panneau s’ouvrira pour y effectuer l’action immédiatement.

![Page produits dans laquelle le panneau annuler l’abonnement est ouvert.](../media/MAC-WN-SubscrDetails.png)

### <a name="domains"></a>Domaines

La gestion de domaine peut être compliquée et nous avons publié une nouvelle fonctionnalité pour faciliter cette tâche. Accédez à paramètres > domaines, puis sélectionnez un domaine pour obtenir plus d’informations sur votre domaine et l’état du domaine.

:::image type="content" source="../media/MAC-WN-DomainDNS.PNG" alt-text="Page de détails des domaines pour contoso.com":::

### <a name="docs-training-and-videos-july-2020"></a>Documents, formation et vidéos (juillet 2020)

Nouveautés de la série de vidéos [Microsoft 365](https://youtu.be/m1Nu8WJgCDY) : ce mois-ci, nous allons aborder la nouvelle expérience Yammer pour le Web et mobile, comment intégrer l’application de communautés Yammer pour Microsoft Teams, les nouveaux packages de stratégie pour prendre en charge les utilisateurs et les responsables terrain, et bien plus encore.

## <a name="june-2020"></a>Juin 2020

### <a name="keeping-up-with-office-whats-new-management"></a>Restez au fait des nouveautés d’Office

Il y a quelques mois, nous avons ajouté un paramètre qui vous permet de gérer les [nouveautés qui s’affichent dans les applications Office d’un utilisateur](#office-whats-new-management). Ce mois-ci, nous avons publié une nouvelle carte de visite qui vous aidera à agir rapidement et à effectuer le suivi **des nouveautés que les messages que** vous souhaitez afficher pour les utilisateurs de votre organisation.

### <a name="docs-training-and-videos-june"></a>Documents, formation et vidéos (juin)

- [Prise en main de teams](https://support.microsoft.com/office/184f1aba-2f91-43f0-86e1-9fae607e24f6)

## <a name="may-2020"></a>Mai 2020

### <a name="new-update-channel-for-office"></a>Nouveau canal de mise à jour pour Office

Le 12 mai, nous avons annoncé la disponibilité d’un nouveau canal de mise à jour pour Office : canal d’entreprise mensuel. Ce canal de mise à jour fournit aux utilisateurs les nouvelles fonctionnalités Office une fois par mois, le deuxième mardi du mois.

Si vous autorisez vos utilisateurs à installer Office à partir du portail, vous pouvez sélectionner mensuel Enterprise Channel pour ceux-ci. Pour ce faire, connectez-vous au centre d’administration Microsoft 365 et accédez à la section **Afficher tous les**  > **paramètres**  >  **Org settings**  >  **services** de  >  **téléchargement de logiciels Office** des services Office. Si vous sélectionnez une **fois par mois (canal d’entreprise mensuel)** , toutes les nouvelles installations automatiques d’Office seront configurées pour utiliser le canal d’entreprise mensuel.

En association avec la version mensuelle de Channel Enterprise, nous recherchons également les noms des canaux de mise à jour existants. Par exemple, le canal mensuel est renommé en canal actuel. Les nouveaux noms prennent effet le 9 juin 2020.

Pour plus d’informations, consultez la rubrique [modifications apportées aux canaux de mise à jour pour les applications Microsoft 365](https://docs.microsoft.com/DeployOffice/update-channels-changes).

### <a name="new-admin-roles"></a>Nouveaux rôles d’administrateur

Nous avons ajouté de nouveaux rôles d’administrateur Azure Active Directory au centre d’administration Microsoft 365.

- Le rôle d’administrateur d’identité hybride donne aux utilisateurs l’autorisation de gérer les services de mise en service et d’authentification dans le Cloud.
- Le rôle d’administrateur réseau permet aux utilisateurs de gérer les emplacements réseau et de passer en revue les informations réseau pour le logiciel Microsoft 365 en tant qu’applications de service.
- Le rôle d’administrateur d’imprimantes accorde l’autorisation de gérer tous les aspects des imprimantes et des connexions aux imprimantes.
- Le technicien de l’imprimante est un sous-ensemble du rôle d’administrateur d’imprimantes où ces utilisateurs peuvent enregistrer et annuler l’inscription des imprimantes, ainsi que mettre à jour l’état de l’imprimante.
Pour en savoir plus sur ces rôles, consultez la rubrique [à propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).

### <a name="export-groups-list"></a>Liste exporter les groupes

De nombreux administrateurs ont besoin de partager des informations sur les groupes et leur utilisation pour les personnes qui n’ont pas accès aux centres d’administration. Vous pouvez désormais exporter la liste de groupes vers un fichier CSV à des fins d’audit, ce qui signifie que vous pouvez générer un ancien script PowerShell. Pour essayer, **accédez à groupes groupes**  >  **Groups** , puis sélectionnez **Exporter les groupes** dans la barre de commandes.

### <a name="microsoft-365-solution-and-architecture-center"></a>Centre de solutions et d'architecture Microsoft 365

Ce mois-ci, nous avons publié un nouveau site [https://docs.microsoft.com](https://docs.microsoft.com) nommé [Microsoft 365 solution and architecture Center](https://docs.microsoft.com/microsoft-365/solutions/solution-architecture-center), qui rassemble les conseils techniques dont vous avez besoin pour comprendre, planifier et implémenter des solutions Microsoft 365 intégrées pour une collaboration sécurisée et conforme. Dans ce centre, vous trouverez les éléments suivants :

- Guide de la solution de base
- Solutions de charge de travail et conseils de scénario
- Illustrations de la solution et de l’architecture (affiches !!!)
- Conseils spécifiques de l’industrie
- Principaux de conception de l’architecture d’entreprise

### <a name="docs-training-and-videos-may"></a>Documents, formation et vidéos (mai)

- **Nouveautés de la série de vidéos Microsoft 365** : ce mois-ci, nous allons aborder la nouvelle expérience de support dans les centres d’administration et de sécurité et de conformité de teams, l’intégration de planificateur avec le centre de messages et la nouvelle disposition vidéo 3x3 dans Microsoft Teams. 
- La page Hub [d’aide du centre d’administration 365 de Microsoft](https://docs.microsoft.com/microsoft-365/admin/) a été mise à jour pour vous aider à trouver plus rapidement ce dont vous avez besoin. Et si vous accédez à cette page pour le moment, nous avons ajouté une carte pour vous informer des mises à jour et des modifications importantes.

## <a name="april-2020"></a>Avril 2020

### <a name="intune-roles-management"></a>Gestion des rôles Intune

[Avril 2020](#april-2020)

Eh bien, nous l’avons fait ! Nous avons adopté la deuxième étape vers une expérience de rôles unifiée et vous pouvez désormais gérer les rôles Intune dans le centre d’administration 365 de Microsoft. Vous pouvez également utiliser des fonctionnalités telles que la possibilité de rechercher des rôles et d’afficher des autorisations de rôle. Cela signifie que vous n’avez pas besoin de disposer de deux outils distincts pour gérer les rôles pour Microsoft 365 et Intune. Lorsque vous vous connectez au centre d’administration Microsoft 365, vous verrez qu’il y a deux tableaux croisés dynamiques sur la page rôles, un pour Azure AD et un pour Intune.

![Page rôles avec le tableau croisé dynamique Intune sélectionné](../media/MAC-WN-IntuneRoles.png)

### <a name="sync-message-center-posts-to-planner"></a>Synchroniser les publications du centre de messages vers le planificateur

À partir de mai, les administrateurs qui se trouvent dans la version ciblée verront le bouton « synchronisation du planificateur » dans le centre de messages. Vous pouvez maintenant suivre les messages qui nécessitent une action, sélectionner le type de messages que vous souhaitez suivre, attribuer des messages pour le suivi en tant que tâches et marquer les messages pour une attention ultérieure.

[Rejoignez la version ciblée](manage/release-options-in-office-365.md) pour commencer !

### <a name="need-help-launched-in-teams-admin-center--security-and-compliance-centers"></a>« Besoin d’aide ? » lancé dans le centre d’administration teams & centres de sécurité et de conformité

Le centre d’administration Teams, le centre de sécurité et le centre de conformité utilisent désormais le même « besoin d’aide ? » fonctionnalité que le centre d’administration Microsoft 365 utilise pour trouver de l’aide et contacter le support technique. Nous avons reçu beaucoup de commentaires de la part des administrateurs qui souhaitaient le même niveau d’aide et de support, et nous sommes heureux de vous le faire. Essayez-le et faites-nous part de vos commentaires !

#### <a name="need-chat"></a>Vous avez besoin d’une conversation ?

Nos agents de support technique ont travaillé depuis leur domicile tout en continuant à prendre des cas de client et des limitations sur la bande passante Internet pendant que vous travaillez à domicile. Pour continuer à prendre en charge, nous avons lancé l’option de support live chat pour les clients commerciaux dans le centre d’administration 365 de Microsoft.

Lors de la création d’une demande de service, vous pouvez maintenant voir conversation en tant qu’option, en plus du téléphone et de la messagerie électronique. Sélectionnez conversation comme canal de communication préféré et créez la demande. Une fois que vous avez créé la demande, vous pouvez démarrer la conversation lorsque vous êtes prêt à discuter avec Microsoft agents.

### <a name="teams-updates"></a>Mises à jour de teams

Avec l’utilisation accrue de teams, nous avons ajouté quelques fonctionnalités pour vous aider à les gérer.

- Une nouvelle carte de recommandation sur la page d’accueil du centre d’administration indique les utilisateurs qui n’ont pas activement utilisé teams pendant 30 jours. Vous pouvez envoyer un courrier électronique de formation à ces utilisateurs à l’aide de teams.
- Associer **des personnes à teams** : accédez au **programme d’installation** pour afficher une nouvelle page afin de vous aider à activer teams pour les utilisateurs titulaires d’une licence et à autoriser l’accès invité, afin que vous puissiez travailler avec des clients externes dans Teams.
- Une carte Microsoft teams est désormais épinglée par défaut à votre page d’accueil. Elle indique si les équipes sont activées et si l’accès invité est autorisé. Il vous permet également de vérifier l’état de configuration des utilisateurs de teams nouvellement sous licence et de vérifier si les problèmes réseau peuvent affecter les utilisateurs de teams.
- Enfin, teams est maintenant une étape dans le flux de configuration initial si vous avez acheté une licence qui inclut Teams.

### <a name="productivity-score"></a>Score de productivité

Le score de productivité fournit des informations sur la façon dont les utilisateurs utilisent les services Cloud Microsoft et les expériences technologiques qui les prennent en charge. Le score reflète les performances de votre organisation par rapport aux mesures relatives aux employés et aux technologies et compare votre score avec les organisations comme les vôtres. Ce mois-ci, nous introduisons les nouveaux concepts suivants pour l’expérience d’aperçu :

- Affichage des tendances des informations principales sur la page d’accueil et les pages de détails de catégorie-analyse de point de terminaison et catégories de connectivité réseau ajoutées à l’expérience technologique
- Connaissance des technologies pertinentes indiquées dans les catégories d’expérience des employés
- Nouvelle catégorie de communications dans le cadre de l’expérience de l’employé
- Détails de l’utilisateur avec les métadonnées organisationnelles dans les catégories expérience des employés

Si vous souhaitez en savoir plus, consultez le blog : [mesurer et améliorer l’expérience microsoft 365 avec score de productivité Microsoft](https://techcommunity.microsoft.com/t5/microsoft-365-blog/measure-and-improve-the-microsoft-365-experience-with-microsoft/ba-p/1348618). La note de productivité est actuellement en préversion privée. [Participez à la](https://aka.ms/productivityscorepreview) préversion privée de la note de productivité pour commencer.

### <a name="groups-updates"></a>Mises à jour de groupes

Ce mois-ci, nous avons deux mises à jour pour les groupes :

- Vous pouvez désormais modifier des adresses de messagerie pour les groupes Office 365 (également appelés groupes dans Outlook et bientôt appelés groupes Microsoft 365).
- Nous avons fait part de vos commentaires et nous avons ajouté des messages d’erreur plus clairs pour expliquer pourquoi vous ne pouvez pas convertir un groupe en équipe Microsoft.

### <a name="docs-videos-and-training-april"></a>Documents, vidéos et formation (avril)

**Nouveautés de la série de vidéos Microsoft 365** : ce mois-ci, nous fournissons des conseils et des ressources pour aider les petites entreprises à passer au travail à distance, y compris comment déployer Microsoft Teams, les ressources de formation à distance pour rester connecté à des clients et des partenaires, et le nouveau plan de voix entreprise Microsoft 365. [Nouveautés de Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2118096)

#### <a name="for-your-users"></a>Pour vos utilisateurs

- [Planifier une réunion](https://support.microsoft.com/office/c61b4f61-ee62-4a06-8bf7-0a1cd302700a)
- [Participer à une réunion teams](https://support.microsoft.com/office/078e9868-f1aa-4414-8bb9-ee88e9236ee4)
- [Créer une équipe à l’échelle de l’Organisation](https://support.microsoft.com/office/037bb27a-bcc9-48fe-8d72-44d9482420a3)
- [Créer une équipe avec des invités](https://support.microsoft.com/office/11fbb083-52ee-434d-8c6e-63711fdafac7)
- [Rejoindre une équipe en tant qu’invité](https://support.microsoft.com/office/928d1eef-61e2-49ec-b754-c2fe86b34824)
- [Créer une adresse de messagerie de groupe](https://support.microsoft.com/office/ded875f9-a9de-437f-b559-2ae4f235bb2b)

#### <a name="for-admins-and-business-owners"></a>Pour les administrateurs et les propriétaires d’entreprise

- [Permettre à votre petite entreprise de travailler à distance ](https://support.microsoft.com/office/9b91a85a-39b4-40a6-a590-0f9bea0ba8e6)
- [Exécution d’une petite entreprise à distance](https://support.microsoft.com/office/9ac1a0f1-789b-4143-b954-5821d5d89298)
- [S’inscrire à Microsoft Business Basic](https://support.microsoft.com/office/9ac1a0f1-789b-4143-b954-5821d5d89298)
- [Configuration de la connexion à deux facteurs](https://support.microsoft.com/office/9ac1a0f1-789b-4143-b954-5821d5d89298)

## <a name="march-2020"></a>Mars 2020

### <a name="featured-feedback-fix-improve-add-user-reliability-for-licensing"></a>Correctif de commentaires en vedette : amélioration de la fiabilité de l’ajout d’utilisateur pour les licences

Nous avons reçu beaucoup de commentaires des administrateurs sur la façon dont il est difficile d’attribuer des licences lors de l’ajout d’utilisateurs. Nous avons effectué la première mise à jour de ce correctif et nous avons migré vers un service en arrière-plan plus fiable pour traiter ces demandes. En cas de problème, vous recevrez un message d’erreur qui vous permettra de réessayer.

![Ajoutez la page de confirmation de l’utilisateur avec l’erreur.](../media/MAC-WN-ImprovedLicensing.png)

### <a name="microsoft-teams-home-page-card"></a>Fiche de page d’accueil de Microsoft teams

Avec la mise à niveau de l’utilisation de teams, certaines développées obtiendront une carte de tableau de bord épinglée qui rend les équipes de tournage plus détectables. La carte comporte également des liens vers des formations et des documents pour aider votre organisation à travailler à distance. Il vous suffit d’accéder à la page d' **Accueil** pour afficher la nouvelle carte.

![Fiche de page d’accueil de Microsoft teams](../media/MAC-WN-TeamsCard.PNG)

### <a name="customize-your-organizations-sharepoint-mobile-app-theme"></a>Personnaliser le thème de l’application mobile SharePoint de votre organisation

À l’aide du centre d’administration Microsoft 365, vous pouvez désormais personnaliser le thème de votre organisation dans l’application mobile SharePoint pour iOS et l’application mobile SharePoint pour Android. Cette fonctionnalité offre une expérience d’application intranet mobile qui peut correspondre à votre SharePoint Online pour les employés en déplacement. La personnalisation de thème inclut votre image de logo, la couleur de la barre de navigation, les couleurs du texte et des icônes, ainsi que les couleurs d’accentuation, ce qui facilite la reconnaissance.

![Diagramme mappant les paramètres du centre d’administration vers l’application mobile.](../media/MAC-WN-CustThemeSP.png)

### <a name="improvements-to-the-add-a-group-wizard"></a>Améliorations apportées à l’Assistant Ajout d’un groupe

Lorsque les administrateurs ont créé un nouveau groupe et lui ont fait une équipe en même temps, ils peuvent affecter des propriétaires qui n’ont pas de licence incluant Teams. Et cela a créé quelques maux de casse. Nous avons mis à jour le flux de l’Assistant pour vérifier que les propriétaires disposent d’une licence teams et qu’ils n’ont pas la possibilité de transformer le groupe en équipe est désactivé.

### <a name="microsoft-365-offerings-for-small-and-medium-businesses"></a>Offres Microsoft 365 pour petites et moyennes entreprises

Nous sommes conscients qu’il s’agit d’une annonce pour le mois prochain, mais nous souhaitons s’assurer que vous êtes prêt.

À partir du 21 avril, nous apportons des modifications liées à nos abonnements Office 365 pour petites et moyennes entreprises, et à Office 365 ProPlus. Ces produits utiliseront désormais la marque Microsoft 365.

Les nouveaux noms de produits entrent en vigueur le 21 avril 2020. Il s’agit d’une modification apportée au nom de produit uniquement et aucune modification de prix ou de fonctionnalité n’existe pour le moment.

|Nom actuel |Nouveau nom  |
|---------|---------|
|Office 365 Business Essentials     |   Microsoft 365 Business Basic      |
|Office 365 Business Premium     |    Microsoft 365 Business Standard     |
|Microsoft 365 Business     |    Microsoft 365 Business Premium     |
|Office 365 Business     |    Applications Microsoft 365 pour les entreprises       |
|Office 365 ProPlus    |   Applications Microsoft 365 pour les entreprises      |

### <a name="videos-training-and-docs"></a>Vidéos, formation et documents

[Nouveautés de la série Web microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2118096): dans l’épisode de ce mois-ci, nous mettons en avant les 3 ans anniversaires de Microsoft teams et couvrent de nouvelles fonctionnalités, notamment une meilleure qualité audio dans les réunions en ligne, les communications ciblées pour les responsables terrain avec l’application équipes, les équipes et l’interopérabilité de Skype client, et bien plus encore.

## <a name="february-2020"></a>Février 2020

### <a name="featured-feedback-fix-multi-organization-switcher"></a>Correctif de commentaires proposé : mélangeur à plusieurs organisations

Nous avons reçu beaucoup de commentaires de la part des partenaires et des administrateurs concernant les défis de la gestion de plusieurs développées de Microsoft Cloud. L’une de nos premières fonctionnalités de gestion multi-organisationnelle est le commutateur de l' **organisation** , qui vous permet de modifier le développées que vous gérez dans simplement 2 clics.
> [!TIP]
> Vous n’avez rien à faire pour faire apparaître le commutateur de l’organisation tant que vous n’êtes pas le partenaire de l’enregistrement d’au moins une organisation.

1. Dans le centre d’administration Microsoft 365, sélectionnez le nom de l’organisation.
![Capture d’écran : en haut de la page d’accueil affichant le nom du profil de l’organisation avec l’icône du sélecteur.](../media/MAC-Organization-switcher.png)

2. Dans le sélecteur d’organisation, sélectionnez l’organisation que vous souhaitez gérer.
![Capture d’écran : commutateur client mon organisation avec un client Messenger consolidé mis en évidence](../media/MAC-OrgSwitcherSelected.png)

C’est littéralement !!!

### <a name="groups"></a>Groupes

Voici quelques-unes des modifications apportées à la zone groupes du mois :

- **Trier par nom de groupe** : vous pouvez trier la liste de groupes par ordre alphabétique en sélectionnant la colonne **nom du groupe** .
- **Restaurer les groupes microsoft 365 supprimés** : vous n’avez plus besoin d’accéder au centre d’administration Exchange pour restaurer les groupes Microsoft 365 supprimés. Accédez à groupes du **Centre d’administration Microsoft 365** \> **Groups** \> les **groupes supprimés** \> (sélectionnez un groupe dans la liste) \> **groupe de restauration**. Il restaure le groupe dans la liste **groupes** et restaure le courrier électronique, les conversations, le bloc-notes, les fichiers et le calendrier du groupe.

### <a name="videos-training-and-docs-february"></a>Vidéos, formation et documents (février)

- **Nouveautés de la série de vidéos Microsoft 365** : ce mois-ci, nous nous concentrerons sur les fonctionnalités de recherche personnalisées pour SharePoint Online, la fonctionnalité de gestion Office « what’s New » qui vous permet d’afficher ou de masquer des fonctionnalités spécifiques des utilisateurs finaux via le volet d’aide dans l’application, les dernières mises à jour de sécurité et de conformité dans Yammer, et bien plus. Voici le dernier épisode : [Nouveautés de Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2118096)

- **Documents Move** : nous avons combiné les articles du site Web d’administration d’Office 365 avec le contenu Microsoft 365 et vous avez peut-être remarqué la nouvelle URL. Par exemple, cet article est utilisé pour être hébergé à l’adresse : **docs.Microsoft.com/office365/admin/Whats-New-in-Preview** , mais l’URL est désormais : **docs.Microsoft.com/Microsoft-365/admin/Whats-New-in-Preview**. Si vous avez des pages avec des signets, vous devez mettre à jour vos liens ; Toutefois, les liens de contenu sont redirigés vers le nouveau contenu référentiel.

## <a name="january-2020---happy-new-year"></a>Janvier 2020-bonne année

> [!NOTE]
> Saviez-vous qu’il existe des [Nouveautés dans](https://go.microsoft.com/fwlink/p/?linkid=2118096) la série de vidéos de Microsoft 365 sur YouTube ? Il met en évidence les dernières fonctionnalités que nous avons déployées pour les utilisateurs. Tous les mois, nous allons commencer à établir un lien vers le dernier épisode dans la section [vidéos, formation et docs](#videos-training-and-docs) . <br> <br> Voici le dernier épisode : [Nouveautés de Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2118096)

### <a name="dark-mode"></a>Mode sombre

Lors du premier déploiement du mode sombre, il n’était disponible que sur la page d’accueil. Le mode sombre est maintenant en dehors de l’aperçu et est dans la version ciblée sur la plupart des pages du centre d’administration.

1. Tout d’abord, vous devez activer la publication ciblée : accédez **à paramètres paramètres** \> organisation **paramètres** de la version des \> **profils d’organisation** \> **Release preferences**.
1. Puis, pour activer le mode sombre, accédez à la page d' **Accueil** , puis sélectionnez le bouton **mode sombre** . (Il se trouve en regard du champ de **recherche** , et de cet article lien vers **les** nouveautés.)
1. Pour toute page dont le mode foncé est disponible, le bouton est en haut de la page, en regard **du nouveau centre d’administration** bascule.

### <a name="office-whats-new-management"></a>Nouvelle gestion d’Office

Les administrateurs souhaitent contrôler la façon dont Microsoft communique « What’s New » à leurs utilisateurs dans les applications Office, et vous disposez maintenant de ce contrôle. Accédez aux **paramètres** \> **Office what’s New Management Preview**. Sélectionnez une fonctionnalité pour afficher ses détails, puis sélectionnez le bouton **masquer à partir des utilisateurs** si vous ne souhaitez pas que vos utilisateurs voient un message « what’s New » particulier. Par exemple, il est possible que votre organisation attende que les utilisateurs connaissent une fonctionnalité jusqu’à ce que tous les membres de votre organisation soient formés sur celle-ci.

![Capture d’écran de l’aperçu d’Office nouveautés dans le volet d’informations d’une fonctionnalité ouverte.](../media/whatsnew-officemgmt-preview.png)

Cette fonctionnalité a été publiée pour la première fois en novembre, mais il existe quelques mises à jour de fonctionnalités que vous devez connaître : [Nouveautés de l’aperçu des nouveautés de la gestion Office nouveautés disponibles](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-what-s-new-management-preview/ba-p/1020438)

### <a name="partners"></a>Partenaires

Howdy, partenaires ! (Je n’ai pas pu m’aider.) Nous disposons également d’une mise à jour de ce mois-ci. Il existe une nouvelle fonctionnalité qui permet aux partenaires de donner aux clients CSP la possibilité d’accepter leur contrat de client Microsoft (MCA) dans la section **comptes de facturation** du centre d’administration. Dans cette nouvelle expérience :

1. Le client reçoit un e-mail d’invitation avec un lien pour accepter la relation partenaire et MCA.
2. Une fois que le client se connecte, il peut afficher et accepter les autorisations MCA et Partner-Right à partir du centre d’administration.

### <a name="resource-mailboxes"></a>Boîtes aux lettres de ressources

La liste des boîtes aux lettres de ressources a été mise à jour avec le nouveau style. Dans le centre d’administration 365 de Microsoft, accédez à **ressources** \> **salles & équipements**.

### <a name="videos-training-and-docs-january"></a>Vidéos, formation et documents (janvier)

Consultez la formation pour les administrateurs de petite entreprise publiée en janvier :

- [Créer votre site Web professionnel](https://support.microsoft.com/office/3325d50e-d131-403c-a278-7f3296fe33a9)
- [Trouver des réponses et de l’aide](https://support.microsoft.com/office/7f681212-c649-4a3e-a43b-32b1d1e58988)
- [Obtenir de l’aide ou de l’assistance](https://support.microsoft.com/office/18948a4c-3eb1-4b30-b1bc-a4cc29eb7655)
- [Supprimer un utilisateur](https://support.microsoft.com/office/6bcdad7b-732a-4260-997a-8c176bc3d9d6)
- [Choisir un abonnement Microsoft](https://support.microsoft.com/office/b9f7c78e-430f-4117-89ec-2eeb1dced2ca)
- [Vue d’ensemble de Microsoft 365 pour la sécurité des entreprises](https://support.microsoft.com/office/3274b159-a825-46d7-9421-7d6e209389d1)

## <a name="november-and-december-2019"></a>Novembre et décembre 2019

Nous combinons les nouveautés de novembre et de décembre car, après s’enflamme, nous avions très peu d’annonces à effectuer. Consultez la nouvelle année !

### <a name="change-from-credit-card-to-invoice-payment"></a>Passer de la carte de crédit au paiement de la facture

Nous commençons par déployer la fonctionnalité de changement de votre mode de paiement par carte bancaire. Accédez à **facturation** de \> **vos produits** , sélectionnez un abonnement, puis cliquez sur le lien **modifier** en regard du paiement par carte de crédit.

![Capture d’écran : section facturation de la carte d’abonnement avec une carte de crédit comme mode de paiement.](../media/MAC-BillingEditCreditCard.png)

Vous souhaitez en savoir plus à ce sujet ? [Passer du mode de paiement par carte bancaire ou compte bancaire au mode de paiement par facture](../commerce/billing-and-payments/change-payment-method.md)

### <a name="global-reader"></a>Lecteur général

Nous avons mentionné le rôle de lecteur global dans l' [édition d’octobre 2019](#october-2019---ignite-edition), mais dans la mesure où il se présente plus largement, examinons quelques détails :

- Le rôle de lecteur global est l’équivalent en lecture seule du rôle d’administrateur global. Le lecteur global peut voir tout ce que l’administrateur général est autorisé à faire.
- À quelques exceptions près, comme certaines fonctionnalités de conformité et de sécurité, les lecteurs globaux ont accès à tous les centres d’administration Microsoft Cloud pour lesquels votre organisation est autorisée à utiliser.
- Attribuez le rôle de lecteur global aux utilisateurs qui en ont besoin pour la planification, les audits et les enquêtes.
- Vous pouvez également combiner le rôle de lecteur global avec un autre rôle qui dispose de moins d’autorisations. Par exemple, un propriétaire de petite entreprise peut se voir attribuer les rôles de lecteur global d' **administration de facturation**  +  **Global reader** afin qu’ils puissent payer les factures et rester au fait des modifications apportées à leur organisation en nuage.
- Les lecteurs globaux peuvent accéder à n’importe quelle page du centre d’administration 365 de Microsoft. Lorsqu’ils ouvrent une page modifiable, un avertissement s’affiche en haut indiquant qu’ils n’ont pas l’autorisation d’enregistrer les modifications et que le bouton enregistrer est désactivé.

Nous serions ravis de vous faire part de vos commentaires sur le rôle de lecteur global et sur les autorisations basées sur les rôles que vous aimeriez voir ultérieurement. [Fournir des commentaires pour les autorisations basées sur les rôles](https://office365.uservoice.com/forums/273493-office-365-admin/suggestions/10115430-have-a-consistent-experience-when-assigning-admin)

### <a name="new-settings-page"></a>Page nouveaux paramètres

Les pages **profil d’organisation** , **sécurité & confidentialité** et **services & des compléments** ont toutes été regroupées en une page avec 3 onglets verticaux. Et la meilleure partie--à partir d’un seul emplacement, vous pouvez maintenant rechercher tous les paramètres.
![Capture d’écran : page paramètres avec le champ « Rechercher dans tous les paramètres » en surbrillance en haut de la page.](../media/MAC-SettingsMultiPivotSearch.png)

### <a name="training--docs"></a>Documentation de formation &

Cette section est une nouvelle fonctionnalité de cet article, dans laquelle nous allons commencer à établir un lien vers de nouvelles formations et de la documentation que vous jugerez intéressantes.

En novembre, nous avons publié un grand nombre de chemins d’apprentissage vers le site Web [Microsoft](https://docs.microsoft.com/learn/) Learning pour aider les professionnels de l’informatique à se familiariser avec Microsoft 365. Extrayez-les :

- [Principes fondamentaux de Microsoft 365](https://docs.microsoft.com/learn/paths/m365-fundamentals/)
- [Étendre les notions de base d’Office](https://docs.microsoft.com/learn/paths/extend-office-fundamentals/)
- [Microsoft 365-moderniser votre déploiement d’entreprise avec les applications Windows 10 et Microsoft 365 pour les entreprises](https://docs.microsoft.com/learn/paths/m365-getmodern/)
- [Gérer le déploiement au sein de votre entreprise avec Microsoft 365](https://docs.microsoft.com/learn/paths/manage-enterprise-deployment-m365/)
- [Mettre à niveau Microsoft Office pour les services informatiques à l’échelle](https://docs.microsoft.com/learn/paths/m365-office-for-it/)
- [Mettre à disposition des applications et des bureaux distants à partir d’Azure avec le bureau virtuel Windows ](https://docs.microsoft.com/learn/paths/m365-wvd/)
- [Moderniser votre lieu de travail avec Microsoft 365 et Surface pour les entreprises](https://docs.microsoft.com/learn/paths/modernize-workplace-with-m365-and-surface/)
- [Protéger les identités et accès avec Microsoft 365](https://docs.microsoft.com/learn/paths/m365-identity/)
- [Protéger les informations d’entreprise avec Microsoft 365](https://docs.microsoft.com/learn/paths/m365-information-protection/)
- [Gérer la sécurité avec Microsoft 365](https://docs.microsoft.com/learn/paths/m365-security-management/)
- [Défense contre les menaces liées à Microsoft 365 Defender](https://docs.microsoft.com/learn/paths/m365-security-threat-protection/)
- [Gérer la collaboration en équipe avec Microsoft Teams](https://docs.microsoft.com/learn/paths/m365-manage-team-collaboration/)
- [Collaborer avec SharePoint dans Microsoft 365](https://docs.microsoft.com/learn/paths/m365-teams-sharepoint/)

## <a name="october-2019---ignite-edition"></a>Octobre 2019-allume Edition

Bienvenue dans l’édition d’allumage des nouveautés du centre d’administration Microsoft 365 ! Bien entendu, il ne s’agit pas d’une liste d’annonces complète, mais voici quelques points forts. Consultez également les blogs pour plus d’informations sur les versions :

- [Administration-sécurité, productivité et améliorations réseau pour Microsoft 365](https://techcommunity.microsoft.com/t5/Microsoft-365-Blog/ADMIN-Security-Productivity-and-Network-Enhancements-for/ba-p/964019).
- [Nouveautés de Microsoft teams-allumez 2020](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/What-s-New-in-Microsoft-Teams-Ignite-2019/ba-p/937025).

### <a name="role-based-access-control"></a>Contrôle d'accès basé sur les rôles

De nombreuses modifications ont été apportées aux rôles dans le centre d’administration depuis que nous avons commencé à déployer en juin :

- **Comparer les rôles** : sélectionnez jusqu’à 3 rôles pour comparer les autorisations pour chacune d’entre elles. Cela vous permettra de trouver le rôle le moins permissif à attribuer aux utilisateurs. Accédez à **rôles** , utilisez la case à cocher sélection multiple dans la première colonne pour choisir jusqu’à 3 rôles, puis sélectionnez **comparer les rôles**.

    ![Comparaison des rôles Administrateur Exchange, administrateur du support technique et administrateur d’utilisateurs.](../media/RBAC-CompareRoles.png)

- **Favoris** : vous pouvez ajouter une étoile à vos rôles préférés ou les plus utilisés, afin de pouvoir les trouver facilement en triant la colonne ou en créant un filtre.
- **Utilisateurs actifs**  >  **Manage Roles** -il a été mis à jour pour s’aligner sur les modifications apportées aux rôles. Comme avec la liste de rôles, nous avons défini l’étendue de la liste de rôles par défaut sur le plus utile, mais vous pouvez voir tous les rôles en développant **Afficher tout par catégorie**.
- **Rôle de lecteur global** : vous avez demandé à le faire ! Compris! Le rôle de [lecteur global](add-users/about-admin-roles.md) !

### <a name="report-an-issue"></a>Signaler un problème

L’état du service a été mis à jour vers le nouveau style et, si vous êtes concerné par un problème qui ne s’affiche pas sur votre tableau de bord d’État du service, vous pouvez **signaler un problème** pour informer Microsoft. Accédez à **Health**  >  **intégrité du service** d’intégrité.

### <a name="viral-subscriptions"></a>Abonnements « viraux »

Comme vous le souhaitez, les utilisateurs peuvent activer des abonnements gratuits à une myriade de produits tels que Power BI et App Connect. Vous pouvez maintenant voir les « abonnements viraux » que vos utilisateurs ont essayés. Accédez à **facturation** de  >  **vos produits**. Sélectionnez le filtre de **type de compte** sous l’onglet abonnements pour afficher les abonnements achetés par l’utilisateur. Si nécessaire, vous pouvez maintenant supprimer ces abonnements de votre compte.

### <a name="user-templates"></a>Modèles de l'utilisateur

Les modèles vous permettent d’ajouter facilement de nombreux utilisateurs en enregistrant et réutilisant les paramètres partagés de ces utilisateurs. Vous pouvez enregistrer des valeurs pour les rôles, les licences affectées, les informations de contact, l’emplacement, et bien plus encore. Lorsque vous utilisez le modèle pour créer un utilisateur, il obtient automatiquement la valeur enregistrée pour ces paramètres. Accédez à **utilisateurs**  >  **actifs** , puis sélectionnez **modèles utilisateur** pour essayer.

### <a name="office-whats-new-management-preview"></a>Office "What’s New" Management (aperçu)

Lorsqu’une fonctionnalité Office importante est publiée dans une application Office, les utilisateurs reçoivent une carte « What’s New » pour en savoir plus sur la nouvelle fonctionnalité. Si vous ne voulez pas que les utilisateurs voient la carte, vous pouvez la masquer. Vous pouvez également choisir si vous souhaitez que les utilisateurs voient la carte en l’affichant. Accédez à **paramètres**  >  **Office nouveautés** en matière de gestion pour l’extraire.

### <a name="sharepoint-url-change"></a>Modification de l’URL SharePoint

Techniquement, il ne s’agit pas des nouveautés du centre d’administration Microsoft 365, mais nous sommes tellement enthousiastes que nous souhaitions vous assurer que vous voyez cette nouvelle information :
> [!IMPORTANT]
> Vous pouvez désormais accéder à votre centre d’administration SharePoint avec une URL normale : [https://admin.microsoft.com/SharePoint](https://admin.microsoft.com/SharePoint)

Pour plus d’informations, consultez [la rubrique what’s New in the SharePoint Admin Center](https://docs.microsoft.com/sharepoint/what-s-new-in-admin-center).

## <a name="september-2019"></a>Septembre 2019

Nous mettons en place des versions intéressantes de fonctionnalités sur le allume 2019, nous n’apportons donc que quelques nouvelles fonctionnalités publiées en septembre. Mais restez informé pour l’article du mois prochain, il sera publié le premier jour de flamme.

### <a name="featured-feedback-fix--the-option-to-convert-the-deleted-users-mailbox-to-a-shared-mailbox-is-back"></a>Correctif de commentaires en vedette : l’option permettant de convertir la boîte aux lettres de l’utilisateur supprimé en boîte aux lettres partagée est restaurée.

Nous avons entendu vos commentaires à haute voix, et nous avons rétabli la possibilité d’accorder à d’autres personnes l’accès à la boîte aux lettres d’un utilisateur supprimé en la convertissant en **boîte aux lettres partagée**. L’ajout de ce dernier à l’Assistant Suppression d’utilisateur vous permet de décider de la marche à suivre pour les données :

- Courrier électronique : accorder à une autre personne l’accès à la boîte aux lettres de l’utilisateur supprimé en la convertissant en boîte aux lettres partagée.
- Files : enregistrer leurs fichiers OneDrive et accorder à d’autres personnes un accès.
- Autorisations : supprimer les autorisations si d’autres utilisateurs ont eu accès à cette boîte aux lettres.
- Alias : supprimez les alias de messagerie afin qu’ils soient disponibles pour un autre utilisateur immédiatement.
![Capture d’écran : Assistant Suppression d’utilisateur avec alias de messagerie, autorisations, OneDrive et options de courrier électronique affichés](../media/WhatsNew-DeleteUserWiz.png)

### <a name="initial-setup"></a>Configuration initiale

Une mise à jour a été mise à jour vers l’un des assistants d’installation initiaux suivants : Microsoft 365 for Business. Les étapes ont été rationalisées et nous avons déplacé deux des tâches de configuration dans la page de configuration :

- **Sécurisez les ordinateurs Windows 10** : configurez des stratégies pour mieux protéger vos appareils Windows 10 contre les virus, les programmes malveillants et les attaques des pirates.
- **Installer automatiquement Office** : lorsque vous activez cette fonction et que les utilisateurs ont connecté leurs PC à Microsoft 365 Business, leurs ordinateurs sont automatiquement mis à jour vers les dernières applications Office et restent à jour.

## <a name="august-2019"></a>Août 2019

### <a name="billing"></a>Facturation

Nous disposons de mises à jour pour la facturation et les abonnements ce mois-ci :

- Abonnements basés sur des appareils : vous pouvez attribuer ou annuler l’affectation de licences **Microsoft 365 Apps for Education (Device)** à des appareils dans le centre d’administration Microsoft 365. **Microsoft 365 Apps for Education (Device)** est une licence de module complémentaire qui vous permet d’attribuer une licence à un appareil. Accédez à **facturation** de  >  **vos produits** pour trouver et acheter la licence.
- Gestion des licences basées sur les utilisateurs : nous avons mis à jour la manière dont vous attribuez des licences aux utilisateurs actifs des **utilisateurs dans**  >  **Active users** le nouveau style. Pour plus d’informations, voir :
  - [Attribuer des licences aux utilisateurs](manage/assign-licenses-to-users.md)
  - [Annuler l'assignation des licences aux utilisateurs](manage/remove-licenses-from-users.md)

### <a name="setup-page-updates"></a>Mises à jour de la page de configuration

Le programme d’installation dispose maintenant de catégories et de sections, y compris une section **recommandée pour vous** , dans laquelle nous suggérons intelligemment votre prochaine étape pour activer les fonctionnalités et configurer votre organisation. Nous avons également ajouté une nouvelle fonctionnalité à configurer :

- **Microsoft Defender pour office 365** -si votre organisation est autorisée à utiliser Microsoft Defender pour Office 365 et que vous ne l’avez pas encore configurée ou que vous ne l’avez pas encore activée, vous verrez cette page. Accédez au **programme d’installation pour le** tester.

### <a name="report-an-issue-august"></a>Signaler un problème (août)

Si vous êtes concerné par un problème qui ne s’affiche pas sur votre tableau de bord d’État du service, la fonctionnalité **rapport d’un problème** vous permettra de nous le faire rapidement et facilement. Accédez à **Health**  >  **intégrité du service** d’intégrité.

## <a name="july-2019"></a>Juillet 2019

### <a name="message-center"></a>Centre de messages

Le centre de messages a été mis à jour vers la nouvelle conception et semble incroyable !

![Capture d’écran : Centre de messages mis à jour avec l’onglet « tous les messages actifs » sélectionné et le menu filtre ouvert.](../media/MAC-MessageCenterUpdated.png)

- Vous pouvez désormais afficher **les messages par État**. Il vous suffit de sélectionner l’un des onglets : **tous les messages actifs** , **haute importance** , **messages non lus** et **messages ignorés**.
- Vous pouvez également filtrer par **confidentialité des données** de catégorie, **planifier des modifications** , **prévenir ou résoudre des problèmes** et **rester informé** des catégories de messages.
- Sélectionnez un message dans la liste et vous disposez de plusieurs options dans la barre de commandes : **Ignorer** , **marquer comme lu** ou **marquer comme non lu** ou **partager**.
- Lorsque vous ouvrez un message, vous disposez encore d’options supplémentaires :
  - Copiez un lien du message dans votre presse-papiers pour l’enregistrer pour une version ultérieure ou pour le partager avec des collègues.
  - Marquer les messages comme **lus** ou non **lus**.
  - Faire part de vos commentaires sur un message en sélectionnant **Like** ou n' **aiment** pas, un volet de commentaires s’ouvre et vous demande de fournir des commentaires spécifiques sur ce que vous aimez ou n’aimez pas ce message.

### <a name="navigation-pane-intelligence"></a>Intelligence du volet de navigation

 Le volet de navigation mémorise maintenant vos dernières actions et affiche le volet dans le dernier État dans lequel vous l’avez laissé. Il rendra également les éléments fréquemment utilisés visibles par défaut.

### <a name="initial-setup--the-setup-page"></a>Configuration initiale & la page de configuration

Nous avons des modifications passionnantes pour vous aider à configurer votre organisation. Tout d’abord, nous allons étudier la différence entre le **programme d’installation** et la **page de configuration**. Le **programme d’installation** fait référence à l’Assistant d’installation initial que vous avez utilisé pour l’intégration aux services en ligne de Microsoft. Cela comprend généralement trois étapes spécifiques : **connecter un domaine** , **Ajouter des utilisateurs** et **Télécharger les applications Office**. La **page de configuration** est la page dans le centre d’administration qui a recommandé des tâches de configuration pour vous assurer que vous bénéficiez de tous les abonnements, comme l’activation des fonctionnalités pour lesquelles vous avez acheté des licences.

- **Programme d’installation** : l’Assistant installation initiale a été mis à jour pour les abonnements **Microsoft 365 pour les entreprises** . Cette nouvelle conception permettra aux nouvelles organisations de passer plus rapidement de l’Assistant à un plus grand succès.
- **Page de configuration** : la page de **configuration** vous permet de terminer la configuration et la sécurisation des services qui accompagnent vos abonnements. Vous pouvez également consulter les recommandations ignorées sur la page de **configuration** . Pour voir si elle est encore disponible pour vos abonnements, accédez au **Centre d’administration de Microsoft 365**  >  **Setup**.

### <a name="billing--subscriptions"></a>Abonnements aux & de facturation

- Type de produit **logiciel** -vous pouvez désormais consulter les logiciels achetés par le biais d’un fournisseur de services Cloud (CSP). Pour afficher vos téléchargements et clés, accédez à **Billing**  >  **l’onglet facturation de votre**  >  **logiciel** produits.
- Vous pouvez afficher les produits et services Azure modernes à partir du centre d’administration Microsoft 365, que vous les achetiez auprès de Microsoft ou d’un fournisseur tiers. Exemples de produits Azure modernes inclus :
  - Instances virtuelles réservées Azure
  - Plans de prise en charge Azure
  - Avantages de l’utilisation hybride Azure (AHUB)
  - Gérer les applications
  - Services d’appareil
  - Abonnements Azure

### <a name="simplify-multi-factor-authentication"></a>Simplifier l’authentification multifacteur

Les administrateurs ont accès aux informations sensibles de votre organisation. Exige que tous les administrateurs utilisent l’authentification multifacteur lors de la connexion. Le nouvel Assistant vous permet de le faire en une seule étape. Pour le tester, accédez à **configuration** renforcement de la  >  **sécurité de la connexion**.

### <a name="users"></a>Utilisateurs

Les pages utilisateurs et **invités** **supprimés** ont été mises à jour avec le nouveau style.

- **Utilisateurs invités** : vous pouvez ajouter des utilisateurs invités en les invitant à afficher ou partager des fichiers à partir de SharePoint ou de OneDrive. Vous pouvez afficher les utilisateurs invités **à partir des utilisateurs**  >  **invités**.
- **Utilisateurs supprimés** : sur la page **utilisateurs supprimés** mis à jour, vous pouvez effectuer toutes les actions de l’ancien centre d’administration, mais maintenant ajouter et supprimer des colonnes. Nous disposons d’un grand nombre d’options de colonne parmi lesquelles choisir. En fait, il s’agit des mêmes colonnes que vous pouvez choisir sur la page **utilisateurs actifs** .

## <a name="june-2019"></a>Juin 2019

### <a name="featured-feedback-request---dark-mode"></a>Demande de commentaires en vedette-mode sombre

L’affichage du centre d’administration en mode sombre est en préversion ! Vous pouvez le tester sur la page d' **Accueil** uniquement pour le moment. Sur la page d' **Accueil** , le bouton **en mode sombre** se trouve dans la barre de commandes en regard du lien **what’s New** .

### <a name="roles-management"></a>Gestion des rôles

À la fin du 1er juin, nous avons commencé à déployer un nouveau moyen de gérer les rôles d’administrateur. Lorsqu’elle est disponible pour vous, accédez à rôles de **rôles**  >  **Roles**. Jusqu’à présent, jetez un œil !
<br> ![Capture d’écran : liste des rôles d’administrateur avec le volet des détails du rôle d’administrateur d’utilisateur mis en surbrillance.](../media/MAC-AdminRoles-Featured.png) <br>

Cette nouvelle expérience permet de voir plus facilement qui dispose des autorisations d’administrateur et d’affecter des rôles qui accordent le niveau d’accès approprié à vos administrateurs. Nous avons également ajouté des rôles supplémentaires à partir d’Azure AD afin de ne pas perdre de temps à passer à plusieurs centres d’administration.
Que pouvez-vous faire d’autre ici ?

- Exportez la liste de tous les administrateurs de votre organisation qui sont affectés à des rôles Azure Active Directory dans Microsoft 365.  
- Afficher tous les administrateurs affectés à un rôle spécifique, ajouter ou supprimer des administrateurs d’un rôle spécifique, Rechercher des rôles par nom et par mot clé, et en savoir plus sur ce que chaque rôle autorise un utilisateur.
- Recherchez rapidement un rôle spécifique et créez des filtres.

### <a name="payment-method"></a>Mode de paiement

Nous avons mis à jour votre mode de paiement pour vos abonnements. Accédez à **facturation**  >  **&**  >  **paiement** des paiements. Vous pouvez voir vos modes de paiement dans un affichage de liste. Sélectionnez un élément dans la liste pour le supprimer, le modifier et voir facilement l’abonnement auquel ce mode de paiement est associé.

## <a name="may-2019"></a>Mai 2019

### <a name="mays-featured-fix---case-sensitivity"></a>Correctifs proposés pour les majuscules et les minuscules

À présent, lorsque vous recherchez des boîtes aux lettres, des contacts, des ressources et des autorisations de boîte aux lettres partagées, vos termes de recherche n’ont pas à respecter la casse.

**Gestion des utilisateurs et des groupes** Ce mois-ci, nous avons mis à jour **bloquer l’utilisateur** , **Réinitialiser le mot de passe** , le mode liste de **contacts** , l’affichage liste de **groupes** et les pages de détails du **groupe** sur le nouveau style Centre d’administration.

- L’affichage liste des nouveaux **groupes** vous permet d’obtenir des données plus riches sur vos groupes, et vous pouvez personnaliser le mode d’affichage de vos données, et la liste des groupes, le mode d’affichage de vos données. Par exemple, vous pouvez désormais filtrer sur des **groupes avec** teams pour déterminer si vos groupes font partie d’une équipe et vous pouvez ajouter la colonne **État des équipes** .
- La liste de groupes fournit également toutes les améliorations que nous avons apportées à l’expérience de liste dans la gestion des utilisateurs, y compris les actions rapides et la barre de commandes contextuelle.

**Recommandations**<br>
Vous pouvez voir une nouvelle recommandation dans votre centre d’administration : nous avons ajouté 4 nouveaux. Bien entendu, vous ne verrez des recommandations que si nous pensons qu’elle sera avantageuse pour votre organisation. Mais n’attendez pas que nous affichions la recommandation : vous pouvez l’ajouter à partir de la bibliothèque de cartes.

- **Expiration du mot de passe** : nous recommandons que les mots de passe soient configurés pour **ne jamais expirer**. Si votre organisation a un paramètre différent, vous pouvez voir cette recommandation.
- **Administrateurs globaux trop nombreux** : étant donné qu’un trop grand nombre d’administrateurs globaux est une menace de sécurité, si vous avez plus de 4 administrateurs globaux, vous verrez cette recommandation. Nous vous suggérons de donner aux utilisateurs uniquement l’accès dont ils ont besoin pour effectuer leur travail.
- Fonctionnalité **Intune Device protection** : si vos licences incluent Intune et que vous n’avez pas fini de configurer Intune ou inscrit vos appareils, nous vous recommandons de créer une stratégie Intune afin de protéger les fichiers de votre organisation lorsque les utilisateurs y accèdent à partir de leurs appareils mobiles.
- **Obtenir les mises à jour mensuelles des fonctionnalités Office** : nous avons reçu des commentaires de nos très petits clients qui, lorsqu’ils reçoivent les mises à jour mensuelles des fonctionnalités Office, leurs utilisateurs sont plus heureux. Par conséquent, si vous êtes une très petite entreprise et que vous obtenez actuellement vos mises à jour de fonctionnalité Office tous les six mois, vous verrez cette recommandation.

**Paramètres** <br>
En ce qui concerne les paramètres, il y a eu quelques modifications. Il suffit de mettre à jour les paramètres existants vers le nouveau style du centre d’administration. Lors de la progression et de l’ajout de nouveaux paramètres que vous n’avez jamais vus auparavant, nous commencerons à les mentionner ici. Et nous disposons d’un paramètre unique pour annoncer : **authentification moderne**. Oui, il existe un nouveau paramètre pour activer **l’authentification moderne** ! Pour l’extraire, accédez à **paramètres**  >  **services &**  >  **l’authentification moderne** des compléments.

## <a name="april-2019"></a>Avril 2019

Les choses sont idéales pour le centre d’administration. Nous avons lu vos commentaires et suggestions, répondez à la plupart d’entre eux et vous avez tout le temps de dire à cœur. Bien entendu, nous effectuons toujours le travail pour s’assurer que tout dépend de l’ancien centre d’administration. Et n’oubliez pas de déployer de nouvelles fonctionnalités, vous risquez de ne pas s’y trouver immédiatement.

### <a name="featured-feature---add-users"></a>Fonctionnalité proposée-ajouter des utilisateurs

Pour avril, nous proposons l’Assistant **Ajout** d’un utilisateur qui vous guide... Patientez... Ajout d’utilisateurs. Il s’agit d’une étape par étape pour ajouter les informations de base de l’utilisateur, telles que le courrier électronique et le nom d’affichage, l’affectation d’une licence et d’un rôle, l’ajout de leurs informations de contact, puis l’examen du compte de l’utilisateur avant la validation. **Pourquoi avons-nous effectué cette modification ?** Nous avons appris que vous n’aimez pas le défilement presque infini pour ajouter des utilisateurs dans l’expérience précédente.
<br> ![Capture d’écran de l’Assistant Ajout d’utilisateur.](../media/MAC-AddUserWizard.png) <br>

Vous pouvez procéder de deux manières : <br>

1. À partir de la page d' **Accueil** , sélectionnez **Ajouter un utilisateur** à partir de la carte de **gestion des utilisateurs** . L’Assistant s’ouvre directement à cet emplacement, vous n’avez donc pas à vous rendre à partir d’un travail que vous effectuez sur la page d' **Accueil** .
2. Accédez à **utilisateurs**  >  **actifs** , puis sélectionnez Ajouter un **utilisateur** à partir de la barre de commandes.
<br><br>

Nous avons apporté quelques modifications supplémentaires à la **gestion des utilisateurs** , voici une liste rapide :

- Le volet **gérer les rôles** a été mis à jour vers le nouveau style et est accessible. Nous avons également mis à jour les volets **bloquer l’utilisateur** et **Supprimer l’utilisateur** avec le nouveau style.
- Gérer la position des **licences produit** modifiées dans la barre de commandes.
- Il est désormais plus facile de modifier la photo d’un utilisateur. Dans **utilisateurs actifs** , sélectionnez un utilisateur, puis **Modifiez la photo** sous son image.

### <a name="but-wait-theres-more"></a>Mais attendez ! Il y a plus

- Il y a une nouvelle bannière de configuration sur la page d' **Accueil** qui s’affiche si vous n’avez pas terminé les étapes de configuration, comme l’ajout d’un domaine, l’ajout d’utilisateurs et le téléchargement d’applications Office.
- La liste de **groupes** et le volet d’informations ont été mis à jour avec le nouveau style. Accédez à **groupes groupes**  >  **Groups** pour afficher les modifications.
  - En parlant de groupes, nous avons également ajouté un onglet **Microsoft teams** au volet d’informations groupes, dans lequel vous pouvez transformer n’importe quel groupe Microsoft 365 en équipe. Pour « teamify » un groupe, sélectionnez un groupe Microsoft 365 dans la liste, sélectionnez l’onglet **Microsoft** Teams, puis **créer une équipe**. Si le groupe est déjà une équipe, vous obtiendrez un lien pour le gérer à partir du **Centre d’administration teams**.
  - Enfin, vous pouvez ajouter l' **État teams** à la liste des **groupes** . Dans l’en-tête de colonne, sélectionnez **choisir** les États des équipes, puis  >  **Teams status**  >  **Enregistrer**.
- **Nouveaux rôles d’administrateur limité** : nous avons publié certains nouveaux rôles d’administrateur afin que vous puissiez donner aux utilisateurs uniquement l’accès dont ils ont besoin.
  - **Administrateur Kaizala** : les utilisateurs de ce rôle sont autorisés à effectuer toutes les tâches de gestion dans Microsoft Kaizala, notamment la création et la gestion des utilisateurs dans Kaizala Directory, la gestion des groupes de Kaizala, la gestion des cartes d’action et des connecteurs, ainsi que la création de demandes de service.
  - **Administrateur de recherche** : les utilisateurs de ce rôle ont un accès total à toutes les fonctionnalités de gestion de la recherche Microsoft dans le centre d’administration 365 de Microsoft. Les administrateurs de la recherche peuvent déléguer les rôles d’administrateur de recherche et d’éditeur de recherche aux utilisateurs, et créer et gérer du contenu, comme les signets, Q&des éléments et des emplacements. En outre, ces utilisateurs peuvent afficher le centre de messages, surveiller l’état du service et créer des demandes de service.
  - **Éditeur de recherche** : les utilisateurs de ce rôle peuvent créer, gérer et supprimer du contenu pour Microsoft Search dans le centre d’administration 365 de Microsoft, y compris les signets, Q&des éléments et des emplacements.
- Ce mois-ci contient une Bonanza des modifications de **facturation** ...
  - Vous pouvez maintenant mettre à jour le CVV pour les cartes de crédit existantes sans avoir à le supprimer et à le rajouter. Vous pouvez mettre à jour le CVV en accédant à **Bill**  >  **Payment Methods**.
    - Nous avons facilité la localisation de vos **factures** et comprenons les problèmes de facturation que votre compte peut rencontrer. À présent, vous pouvez voir vos factures dans le navigateur Web au lieu de télécharger le PDF. Accédez à **factures**  >  **et factures**.
    - Sur la page **vos produits** , nous regroupons maintenant vos informations d’abonnement si vous avez plusieurs abonnements du même type.

## <a name="march-2019---weve-officially-released-the-admin-center"></a>Mars 2019-nous avons officiellement publié le centre d’administration

Si vous avez manqué les nouvelles, nous avons publié officiellement le nouveau centre d’administration 365 de Microsoft. Voici le billet de blog où nous l’avons annoncé : [le nouveau centre d’administration Microsoft 365 disponible aujourd’hui](https://techcommunity.microsoft.com/t5/Microsoft-365-Blog/The-new-Microsoft-365-admin-center-available-today/ba-p/377870). Pour mars, nous allons compter sur le billet de blog pour vous permettre de consulter les fonctionnalités publiées-plus, vous pouvez également lire le billet pour les fonctionnalités qui sont publiées dans un avenir proche, ce que nous ne pouvons pas faire dans le contenu principal.
<br> ![Capture d’écran de la page d’accueil du centre d’administration Microsoft 365.](../media/M365AC-HomePage.png) <br>
Nous avons une modification à la zone de **facturation & abonnements** que nous souhaitons mentionner. Je veux dire que y’all n’avait pas pensé que nous avons pu l’améliorer, vous avez fait ? Étant donné que nous ne sommes pas ! Ce mois-ci, nous avons ajouté la possibilité de gérer vos relations de partenaires vers les comptes **de**  >  **facturation** de facturation. À partir de là, vous pouvez passer en revue vos relations partenaires entre un conseiller, un fournisseur de services cryptographiques et des revendeurs indirects. Vous pouvez également accepter les nouvelles demandes de relations avec les partenaires, y compris les autorisations d’administrateur délégué.

Comme toujours, vos commentaires sont importants pour nous, donc conservez-le ! Sur n’importe quelle page du centre d’administration, vous pouvez fournir des commentaires en sélectionnant envoyer des **Commentaires** en bas à droite, à côté de **besoin d’aide ?** .

## <a name="february-2019---billing--subscriptions-edition"></a>2019 février-facturation de l’édition des abonnements &

Ce mois-ci, nous allons nous concentrer sur toutes les améliorations que nous avons apportées aux domaines Affectionately, appelées « facturation et abonnements ». Par le passé, vous n’avez probablement pas fait référence à ces éléments Affectionately, mais nous pensons que vous allez maintenant...

- **Modes de paiement** -nous avons appris que la mise à jour de votre mode de paiement était difficile et que nous ayons apporté beaucoup de modifications. Accédez à **Billing**  >  **modes de paiement** de facturation. Vous pouvez facilement voir vos modes de paiement, comme votre carte Visa, et l’abonnement auquel elle est associée. Dans votre liste de modes de paiement, sélectionnez le menu **plus** (3 petits points en regard de la date d’expiration), puis sélectionnez **afficher les abonnements**. Vous pouvez également modifier et supprimer vos modes de paiement à l’aide du menu **plus** .
- **Compte de facturation** : les clients disposant d’une publication ciblée voient d’abord la page nouveau compte de facturation, puis nous les déroulerons vers le monde entier. Lorsqu’elle est disponible pour vous, accédez au **Billing**  >  **compte de facturation** de facturation. Que pouvez-vous faire dans la page nouveau compte de facturation ? Je suis heureux de vous demander :
  - Mettez à jour l’adresse et les autres informations de contact dans votre profil d’organisation directement à partir de cette page. Vous n’avez pas besoin d' **Settings** accéder au profil de l'  >  **organisation** paramètres, sauf si vous le souhaitez.
  - Et nous simplifions la vie pour les clients de licences directes ou en volume, vous pouvez accepter et passer en revue les accords des clients à partir des **comptes de facturation**. Vous pouvez également vous connecter à d’autres développées, ce qui vous permet de lier les développées pour partager des licences et des ressources.
- Nous avons également réalisé quelques améliorations plus petites et quelques correctifs de bogues :
  - Réactiver un abonnement avec un paiement de facture
  - Modifier l’adresse d’utilisation du service pour vos abonnements
  - Et sur la page Inventory Details, nous avons ajouté des améliorations de notification, nous vous avons lié à la page réelle où vous pouvez effectuer le travail, et il y a plus d’actions sur la carte Inventory details. Accédez à **facturation** -  >  **Bills**  >  **afficher les détails** sur toute facture.

## <a name="january-2019---happy-new-year"></a>Janvier 2019-bonne année

- Toujours en cours d’ajout de **services & compléments** -nous avons mis à jour davantage les **paramètres > services &** les pages de compléments. Essayez les applications ou les rapports intégrés pour afficher les derniers.
- **Vous recherchez des améliorations ?** Ne pas Rechercher plus que la zone de **recherche** dans la barre de commandes. Il a été mis à jour pour vous permettre de rechercher des tâches. Par exemple, essayez « réinitialisation du mot de passe » ou « ajouter un utilisateur ».

### <a name="featured-feedback-fix---licenses-and-apps"></a>Correctifs de commentaires en vedette-licences et applications

Nous avons regroupé les **licences et les applications** dans le volet des détails de l’utilisateur en fonction de vos commentaires. Nous avons initialement séparé les deux fonctionnalités pour fournir de l’espace pour les détails de toutes les licences et les possibilités de toutes les applications. Nous avons appris que le fait de séparer les licences et les applications en deux volets a ajouté la confusion. Nous avons écouté et avons rassemblé les licences et les applications dans un seul onglet. À présent, vous pouvez vous assurer qu’une application est désactivée dans toutes les licences affectées à un utilisateur dans un volet. Lait et les cookies. Licences et applications. Nous obtenons maintenant.

Découvrez : **les utilisateurs > des utilisateurs actifs > modifier** ou **Ajouter des licences utilisateur > des licences et des applications**
