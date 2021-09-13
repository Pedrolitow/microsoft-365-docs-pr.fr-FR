---
title: Tester et déployer des Microsoft 365 Apps par des partenaires dans le portail applications intégrées
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: ''
ms.custom: AdminSurgePortfolio
search.appverid: MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Recherchez, testez et déployez des applications partenaires Microsoft et Microsoft pour les utilisateurs et les groupes de votre organisation à partir du portail Des applications intégrées dans le Centre d'administration Microsoft 365.
ms.openlocfilehash: 13276923c55632145207b61032583a26e3553e06
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59178884"
---
# <a name="test-and-deploy-microsoft-365-apps-by-partners-in-the-integrated-apps-portal"></a>Tester et déployer des Microsoft 365 Apps par des partenaires dans le portail applications intégrées

Le Centre d'administration Microsoft 365 vous offre la flexibilité nécessaire pour déployer des applications de magasin unique, des applications métier personnalisées et Microsoft 365 applications partenaires à partir d’un seul emplacement. L’emplacement est accessible dans les paramètres du Centre d’administration Microsoft, dans les applications intégrées. La possibilité de rechercher, tester et déployer entièrement des applications achetées et sous licence par des partenaires Microsoft à partir du portail d’applications intégrées offre la commodité et les avantages dont votre organisation a besoin pour maintenir les services professionnels mis à jour régulièrement et efficacement.

Pour plus d’informations sur l’achat et les licences Microsoft 365 applications des partenaires de votre organisation, voir Gérer et déployer des Microsoft 365 Apps à partir du [Centre d'administration Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/manage-and-deploy-microsoft-365-apps-from-the-microsoft-365/ba-p/1194324).

Pour plus d’informations sur la façon dont les partenaires créent ces applications, voir Comment planifier une offre [SaaS pour le marché commercial](https://go.microsoft.com/fwlink/?linkid=2158277)

Le portail des applications intégrées est accessible uniquement aux administrateurs globaux et uniquement aux clients du monde entier. Cette fonctionnalité n’est pas disponible dans les clouds souverains et du gouvernement.

Le portail Applications intégrées affiche une liste d’applications, qui inclut des applications individuelles et Microsoft 365 applications provenant de partenaires déployés dans votre organisation. Seules les applications web, SPFx applications, Office et Teams applications sont répertoriées. Pour les applications web, vous pouvez voir deux types d’applications.

- Applications SaaS disponibles dans appsource.microsoft.com, et qui peuvent être déployées par les administrateurs accordant leur consentement au nom de l’organisation.
- Applications de galerie SAML liées aux applications Office.

## <a name="manage-apps-in-the-integrated-apps-portal"></a>Gérer les applications dans le portail Applications intégrées

Vous pouvez gérer les tests et le déploiement d’Microsoft 365 Apps achetés et sous licence auprès de partenaires.

1. Dans le Centre d’administration, **sélectionnez Paramètres,** puis sélectionnez **Applications intégrées.**

2. Choisissez une application avec **l’état** **d’autres applications disponibles** pour ouvrir **le volet** Gérer. L’état **d’autres** applications disponibles vous permet de savoir qu’il existe davantage d’intégrations des isv qui ne sont pas encore déployées.

3. Sous **l’onglet** Vue d’ensemble, **sélectionnez Déployer.** Certaines applications nécessitent que vous ajoutiez des utilisateurs avant de pouvoir sélectionner Déployer.

4. Sélectionnez **Utilisateurs,** **sélectionnez Est-ce un déploiement de test,** puis choisissez Toute l’organisation , **Utilisateurs/groupes spécifiques** ou **Simplement moi**.  Vous pouvez également choisir **de tester le déploiement** si vous préférez attendre le déploiement de l’application dans toute l’organisation. Des utilisateurs ou des groupes spécifiques peuvent être Microsoft 365 groupe de sécurité, un groupe de sécurité ou un groupe de distribution.

5. Sélectionnez **Mettre à** jour, puis **Terminé.** Vous pouvez maintenant sélectionner Déployer sous l’onglet Vue d’ensemble.

6. Examinez les informations de l’application, puis sélectionnez **Déployer.**

7. Sélectionnez **Terminé** sur la page Déploiement terminé et examinez les détails du test ou du déploiement complet sous l’onglet **Vue d’ensemble.**

8. Si l’état de l’application est Mise à jour en **attente,** vous pouvez cliquer sur l’application pour ouvrir le volet Gérer et mettre à jour l’application.

## <a name="find-published-apps-for-testing-and-full-deployment"></a>Rechercher des applications publiées pour le test et le déploiement complet

Vous pouvez rechercher, tester et déployer entièrement des applications publiées qui n’apparaissent pas déjà dans la liste de la page Applications intégrées. En achetant et en accordant des licences aux applications à partir du Centre d’administration, vous pouvez ajouter des applications partenaires Microsoft et Microsoft à votre liste à partir d’un emplacement unique.

1. Dans le centre d’administration, dans le navigation de gauche, **choisissez Paramètres,** puis choisissez <a href="https://go.microsoft.com/fwlink/p/?linkid=2125823" target="_blank">**Applications intégrées.**</a>

2. Sélectionnez **Obtenir des** applications pour obtenir une vue des applications.

3. Dans la page **Microsoft 365 Apps** applications publiées, sélectionnez l’application que vous souhaitez déployer en choisissant **Obtenir maintenant.** Les applications affichées sont principalement les applications Word, PowerPoint, Excel, Outlook, les applications Teams et les applications SharePoint (intégrées à la technologie SharePoint Framework). Acceptez les autorisations et sélectionnez **Continuer**.

5. **Sélectionnez** Déployer en haut de la page en haut du message qui fait référence à l’attente de déploiement.

    Si l’application sélectionnée est liée à une offre SaaS par un isv, toutes les autres applications faisant partie de cette offre liée apparaissent sur la page Configuration. Si vous choisissez de déployer toutes les applications, sélectionnez **Suivant**. Dans le cas contraire, **sélectionnez** Modifier et choisissez les applications que vous souhaitez déployer. Certaines applications nécessitent que vous ajoutiez des utilisateurs avant de pouvoir sélectionner **Déployer.**

6. Sélectionnez **Ajouter des** utilisateurs, choisissez **Est-ce qu’il s’agit** d’un déploiement de test, puis choisissez Toute l’organisation ou des utilisateurs/groupes spécifiques ou Simplement **moi**.  

    Des utilisateurs/groupes spécifiques peuvent être un Microsoft 365, un groupe de sécurité ou un groupe distribué. Vous pouvez également choisir **de tester le déploiement** si vous préférez attendre le déploiement de l’application dans toute l’organisation.

7. Sélectionnez **Suivant** pour obtenir la page **Accepter la demande d’autorisation.** Les fonctionnalités et autorisations de chacune des applications sont répertoriées. Si l’application a besoin de consentement, **sélectionnez Accepter les autorisations.** Seul un administrateur général peut donner son consentement.

8. Sélectionnez **Suivant** pour passer en revue le déploiement et choisissez **Terminer le déploiement.** Vous pouvez afficher le déploiement à partir de l’onglet **Vue** d’ensemble en **choisissant Afficher ce déploiement.** Dans la Centre d'administration Microsoft 365, vous pouvez voir l’état de chaque application déployée et la date à laquelle vous l’avez déployée.

> [!NOTE]
> Si une application a été précédemment déployée à partir d’un autre portail que le portail Applications intégrées, le **type de** déploiement est **personnalisé.**

## <a name="unsupported-scenarios"></a>Scénarios non pris en charge

Vous ne pourrez pas déployer une seule application ou une seule Microsoft 365 Apps store par partenaire à partir du portail d’applications intégrées pour les scénarios suivants.

- Le même add-in est lié à plusieurs offres SaaS.
- L’offre SaaS est liée aux applications, mais elle ne s’intègre pas à Microsoft Graph et aucun ID d’application AAD n’est fourni.
- L’offre SaaS est liée aux applications, mais l’ID d’application AAD fourni pour l’intégration de Microsoft Graph est partagé entre plusieurs offres SaaS.

## <a name="upload-custom-line-of-business-apps-for-testing-and-full-deployment"></a>Télécharger applications métier personnalisées pour le test et le déploiement complet

1. Dans le centre d’administration, dans le navigation de gauche, choisissez Paramètres puis **applications** **intégrées.**

2. Sélectionnez **Télécharger applications personnalisées.** Seule une ligne personnalisée d’applications pour Word, PowerPoint, Excel et Outlook est prise en charge.

3. Télécharger fichier manifeste à partir de votre appareil ou ajoutez un lien URL. Certaines applications nécessitent que vous ajoutiez des utilisateurs avant de pouvoir sélectionner Déployer.

4. Sélectionnez **Ajouter des** utilisateurs, choisissez **Est-ce un déploiement de test** et choisissez Toute l’organisation ou des **utilisateurs/groupes** spécifiques ou **Moi uniquement**. 

    Des utilisateurs/groupes spécifiques peuvent être un Microsoft 365, un groupe de sécurité ou un groupe distribué. Vous pouvez également choisir **De tester le déploiement** si vous souhaitez attendre le déploiement de l’application dans l’ensemble de l’organisation.

5. Sélectionnez **Suivant** pour obtenir la page **Accepter la demande d’autorisation.** Les fonctionnalités et autorisations des applications sont répertoriées. Si l’application a besoin de consentement, **sélectionnez Accepter les autorisations.** Seul un administrateur général peut donner son consentement.

6. Sélectionnez **Suivant** pour passer en revue le déploiement et choisissez **Terminer le déploiement.** Vous pouvez afficher le déploiement à partir de l’onglet **Vue** d’ensemble en **choisissant Afficher ce déploiement.**

## <a name="prepare-to-deploy-add-ins-in-integrated-apps"></a>Préparer le déploiement de add-ins dans les applications intégrées

Office vous aident à personnaliser vos documents et à simplifier la façon dont vous accédez aux informations sur le web (voir Démarrer à l’aide de votre Office de recherche). 

Les add-ins offrent les avantages suivants : 

- Lorsque l’application Office pertinente démarre, le add-in se télécharge automatiquement. Si le add-in prend en charge les commandes de Office, il apparaît automatiquement dans le ruban. 

- Les add-ins n’apparaissent plus pour les utilisateurs si l’administrateur le éteint ou le supprime, ou si l’utilisateur est supprimé de Azure Active Directory ou d’un groupe à qui le module est affecté. 

Les add-ins sont pris en charge dans trois plateformes de bureau Windows, Mac et Online Office applications. Il est également pris en charge dans iOS et Android (Outlook uniquement les applications mobiles). 

L’ouverture d’un client pour tous les utilisateurs peut prendre jusqu’à 24 heures. 

Aujourd’hui, Exchange administrateurs et les administrateurs globaux peuvent déployer des applications intégrées.   

### <a name="before-you-begin"></a>Avant de commencer

Le déploiement de ces derniers nécessite que les utilisateurs utilisent des licences Microsoft 365 Entreprise (E3/E5/F3) ou Microsoft 365 Business (Business Basic, Business Standard, Business Premium). Les utilisateurs doivent également être Office à l’aide de leur ID d’organisation) et avoir Exchange Online boîtes aux lettres Exchange Online actives. Votre annuaire d’abonnement doit être dans ou fédéré pour Azure Active Directory. 

Le déploiement ne prend pas en charge les suivantes : 

- des compléments ciblant Word, Excel ou PowerPoint dans Office 2013 ; 
- un service d'annuaire local ; 
- Déploiement de la mise en Exchange d’une boîte aux lettres sur place 
- Déploiement de composants COM (Component Object Model) ou de Visual Studio Tools pour Office (VSTO) de composants. 
- Déploiements de Microsoft 365 qui n’incluent pas de Exchange Online tels que Microsoft 365 Apps entreprise et Microsoft 365 Apps pour Enterprise.  

### <a name="office-requirements"></a>Office Conditions requises 

Pour word, Excel et les PowerPoint, vos utilisateurs doivent utiliser l’une des valeurs suivantes : 
- Sur un appareil Windows, version 1704 ou ultérieure des licences Microsoft 365 Entreprise (E3/E5/F3) ou Microsoft 365 Business (Business Basic, Business Standard, Business Premium). 
- Sur un Mac, version 15.34 ou ultérieure. 

Pour Outlook, vos utilisateurs doivent utiliser l’une des utilisations suivantes : 
- Version 1701 ou ultérieure des licences Microsoft 365 Entreprise (E3/E5/F3) ou Microsoft 365 Business (Business Basic, Business Standard, Business Premium). 
- Version 1808 ou ultérieure de Office Professionnel Plus 2019 ou Office Standard 2019. 
- Version 16.0.4494.1000 ou ultérieure de Office Professionnel Plus 2016 (MSI) ou de Office Standard 2016 (MSI).
    > [!NOTE]
    > Les versions MSI de Outlook les add-ins installés par l’administrateur dans le ruban Outlook approprié, et non dans la section « Mes modules ».  
- Version 15.0.4937.1000 ou ultérieure de Office Professionnel Plus 2013 (MSI) ou Office Standard 2013 (MSI).
- Version 16.0.9318.1000 ou ultérieure de Office 2016 pour Mac. 
- Version 2.75.0 ou ultérieure de Outlook mobile pour iOS. 
- Version 2.2.145 ou ultérieure de Outlook mobile pour Android. 



### <a name="exchange-online-requirements"></a>Exchange Online requise 
Microsoft Exchange les manifestes de votre organisation. L’administrateur déployant des applications et les utilisateurs qui les reçoivent doivent se trouver sur une version de Exchange Online qui prend en charge l’authentification OAuth. 

Pour connaître la configuration utilisée, consultez l'administrateur Exchange de votre organisation. La connectivité OAuth par utilisateur peut être vérifiée à l’aide de l’cmdlet [PowerShell Test-OAuthConnectivity.](/powershell/module/exchange/test-oauthconnectivity)   

### <a name="user-and-group-assignments"></a>Affectations à des utilisateurs et groupes
Le déploiement du module de mise en œuvre est actuellement pris en charge pour la majorité des groupes pris en charge par Azure Active Directory, notamment les groupes Microsoft 365, les listes de distribution et les groupes de sécurité. Le déploiement prend en charge les utilisateurs des groupes de niveau supérieur ou des groupes sans groupes parents, mais pas les utilisateurs de groupes imbrmbrés ou de groupes qui ont des groupes parents. 

> [!NOTE]
> Les groupes de sécurité sans extension messagerie ne sont pas actuellement pas pris en charge. 

Dans l’exemple suivant, le groupe Service des ventes est affecté à un module. Le Service des ventes Région ouest étant un groupe imbriqué, aucun complément n'est affecté à Noël et Jérôme. 

![Diagramme du service des ventes.](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

### <a name="find-out-if-a-group-contains-nested-groups"></a>Déterminer si un groupe contient des groupes imbriqués

La manière la plus simple de détecter si un groupe contient des groupes imbriqués consiste à afficher la carte de visite du groupe dans Outlook. Si vous entrez le nom du groupe dans le champ **À** d’un e-mail, puis sélectionnez le nom du groupe lorsqu’il est résolu, il vous indique s’il contient des utilisateurs ou des groupes   imbrmbrés. Dans l’exemple **** ci-dessous, l’onglet Membres de Outlook carte de visite du groupe de test n’affiche aucun utilisateur   et seulement deux sous-groupes. 

![Onglet Membres de la Outlook de contact.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

Vous pouvez effectuer la requête inverse en résolvant le groupe pour voir s'il est membre d'un groupe. Dans l’exemple ci-dessous, <b></b>vous pouvez voir sous l’onglet Appartenance de la carte de visite Outlook que le sous-groupe 1 est membre   du groupe de test. 

![Onglet Appartenance de la carte Outlook contact.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

Notez que vous pouvez utiliser l’API Azure Active Directory Graph pour exécuter des requêtes afin de trouver la liste des groupes au sein d’un groupe. Pour plus d’informations, voir [Opérations sur les groupes | Graph Référence d’API](/previous-versions/azure/ad/graph/api/groups-operations). 

## <a name="recommended-approach-for-deploying-office-add-ins"></a>Approche recommandée pour le déploiement de compléments Office 
Pour déployer des add-ins à l’aide d’une approche par phases, nous vous recommandons les étapes suivantes : 
1. Déployez le complément vers un petit groupe de parties intéressées et de membres du service informatique. Vous pouvez activer l’indicateur **« Est-ce qu’il s’agit d’un déploiement de test**». Si le déploiement réussit, passer à l’étape 2. 

2. Déployer le add-in à d’autres personnes au sein de l’entreprise. Là encore, évaluez les résultats et, en cas de réussite, poursuivez le déploiement complet. 

3. Effectuer un déploiement complet pour tous les utilisateurs. Désactiver l’indicateur « **Est-ce qu’il s’agit d’un déploiement de test**». 

Selon la taille de l’audience cible, vous pouvez ajouter ou supprimer des étapes de déploiement.  

## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Déploiement d’un complément Office à l’aide du centre d’administration 

1. Dans le Centre d’administration, **sélectionnez Paramètres,** puis sélectionnez **Applications intégrées.** 

2. Sélectionnez **Obtenir des applications** en haut de la page. AppSource se charge dans un format incorporé. Recherchez un add-in ou recherchez-le en cliquant sur Product dans le navigation gauche.  Si le add-in a été lié par l’isv à une application SaaS ou à d’autres applications et modules, et si l’application SaaS est une application payante, une boîte de dialogue s’affiche pour acheter la licence ou Déployer. Que vous avez acheté la licence ou non, vous pouvez continuer le déploiement. Sélectionnez **Déployer**.  

3. Vous verrez la page **Configuration** dans laquelle toutes les applications sont répertoriées. Si vous n’avez pas les autorisations ou l’accès qui vous permet de déployer l’application, les informations respectives sont mises en surbrillen. Vous pouvez sélectionner les applications que vous souhaitez déployer. En sélectionnant **Suivant,** vous allez afficher la page **Utilisateurs.** Si le add-in n’a pas été lié par l’isv, vous serez acheminé vers la page Utilisateurs. 

4.  **Sélectionnez** Tout le **monde, Utilisateurs/groupes** spécifiques ou Simplement **moi** pour spécifier vers qui le module est   déployé. Utilisez la zone de recherche pour rechercher des utilisateurs ou des groupes spécifiques. Si vous testez le module, sélectionnez **Est-ce qu’il s’agit d’un déploiement de test**. 

5. Sélectionnez **Suivant**. Toutes les fonctionnalités et autorisations de l’application sont affichées dans un seul volet avec des informations de certification si l’application Microsoft 365 certification. La sélection du logo de certification permet à l’utilisateur d’obtenir plus de détails sur la certification.  

6. Examinez, puis sélectionnez **Terminer le déploiement.**  

7. Une icône verte « tick » s’affiche lorsque le module est déployé. Suivez les instructions de la page pour tester le add-in. 

> [!NOTE]
> Les utilisateurs devront peut-être redémarrer Office pour afficher l’icône de la application sur le ruban de l’application. Outlook des applications peuvent prendre jusqu’à 24 heures pour apparaître sur les rubans de l’application. 

Il est bon d’informer les utilisateurs et les groupes que le add-in déployé est disponible. Envisagez d’envoyer un e-mail qui décrit quand et comment utiliser le add-in. Inclure ou lier du contenu d’aide ou des FAQ qui peuvent aider les utilisateurs en cas de problèmes avec le module. 

## <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Points à considérer lors de l'affectation d'un complément à des utilisateurs et groupes 

Les administrateurs globaux et Exchange administrateurs peuvent affecter un module à tout le monde ou à des utilisateurs et groupes spécifiques. Chaque option a des conséquences spécifiques : 

- **Tout le monde**   Cette option affecte le add-in à tous les utilisateurs de l’organisation. Utilisez-la avec parcimonie et uniquement pour les compléments qui sont réellement universels pour l'ensemble de votre organisation. 

- **Utilisateurs**   Si vous affectez un add-in à un utilisateur individuel, puis déployez le module sur un nouvel utilisateur, vous devez d’abord ajouter le nouvel utilisateur. 

- **Groupes**   Si vous affectez un add-in à un groupe, le module est automatiquement attribué aux utilisateurs ajoutés au groupe. Lorsqu’un utilisateur est supprimé d’un groupe, il perd l’accès au module. Dans les deux cas, aucune action supplémentaire n’est requise de la part de l’administrateur. 

- **Moi uniquement**   Si vous affectez un add-in à vous-même, il est affecté uniquement à votre compte, ce qui est idéal pour tester le module. 

L’option la plus efficace pour votre organisation dépend de votre configuration. Toutefois, nous vous recommandons d’effectuer des affectations à l’aide de groupes. En tant qu’administrateur, il peut être plus facile de gérer les modules en utilisant des groupes et en contrôlant l’appartenance à ces groupes plutôt que d’affecter des utilisateurs individuels à chaque fois. Dans certains cas, vous pouvez restreindre l’accès à un petit groupe d’utilisateurs en attribuant des affectations à des utilisateurs spécifiques en attribuant manuellement des utilisateurs. 

### <a name="more-about-office-add-ins-security"></a>En savoir plus Office sécurité des add-ins 
Les compléments Office combinent un fichier manifeste XML qui inclut certaines métadonnées sur le complément, mais surtout qui pointe vers une application web contenant tout le code et la logique. Les fonctionnalités des compléments peuvent varier. Par exemple, les compléments peuvent :
- afficher des données. 
- lire le document d'un utilisateur pour fournir des services contextuels. 
- lire et écrire des données vers le document d'un utilisateur et à partir de celui-ci pour fournir une valeur à cet utilisateur.  

Pour plus d’informations sur les types et fonctionnalités des Office, voir vue d’ensemble de la plateforme des Office [Add-ins,](/office/dev/add-ins/overview/office-add-ins)en particulier la section « Anatomie d’un Office ». 

Pour interagir avec le document de l’utilisateur, le add-in doit déclarer l’autorisation dont il a besoin dans le manifeste. Un modèle d’autorisations d’accès de l’API JavaScript à cinq niveaux constitue la base de la confidentialité et de la sécurité pour les utilisateurs de modules de développement de volet de tâches. La plupart des add-ins dans le Office Store sont de niveau ReadWriteDocument avec presque tous les modules qui la prise en charge au moins au niveau ReadDocument. Pour plus d’informations sur les niveaux d’autorisation, voir Demande [d’autorisations](/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins)pour l’utilisation des API dans les modules complémentaires de contenu et du volet Des tâches. 

Lors de la mise à jour d'un manifeste, les modifications standard sont apportées à l'icône et au texte d'un complément. Les commandes de complément changent parfois, contrairement aux autorisations du complément. L'application web dans laquelle le code et la logique du complément sont exécutés peut changer à tout moment, ce qui est la nature même des applications web. 

Les mises à jour des compléments se produisent comme suit : 
- **Add-in** métier : dans ce cas, lorsqu’un administrateur a téléchargé explicitement un manifeste, le add-in exige que l’administrateur charge un nouveau fichier manifeste pour prendre en charge les modifications de métadonnées. Le complément est mis à jour au démarrage suivant des applications Office concernées. L'application web peut changer à tout moment. 

- **Office** Store : lorsqu’un administrateur a sélectionné un add-in dans le Office Store, si un application est mise à jour dans le Office Store, lors du prochain démarrage des applications Office pertinentes, le add-in est mis à jour. L'application web peut changer à tout moment. 

> [!NOTE]
> Pour Word, Excel et PowerPoint utilisent un catalogue d’applications [SharePoint](https://dev.office.com/docs/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog)pour déployer des applications pour les utilisateurs dans un environnement local sans connexion à Microsoft 365 et/ou prise en charge des SharePoint de   l’application. Par Outlook utiliser Exchange panneau de Microsoft 365.  

## <a name="add-in-states"></a>États de complément
Un add-in peut être à **l’état On**   ou **Off.**   

| État | Comment l’état se produit | Impact |
|:-----|:-----|:-----|
|**Actif**  <br/> |L’administrateur a chargé le module et l’a affecté à des utilisateurs ou des groupes.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté voient celui-ci dans les clients concernés.  <br/> |
|**Désactivé**  <br/> |Un administrateur a désactivé le complément.  <br/> |Les utilisateurs et les groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> Si l'état du complément est modifié en Actif, les utilisateurs et groupes ont de nouveau accès à celui-ci.  <br/> |
|**Deleted**  <br/> |Un administrateur a supprimé le complément.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> |
 
Envisagez de supprimer un add-in si personne ne l’utilise plus. Par exemple, la turning off an add-in might make sense if an add-in is used only during specific times of the year. 

## <a name="manage-an-office-add-in-using-the-admin-center"></a>Gérer un Office à l’aide du Centre d’administration

Après le déploiement, les administrateurs peuvent également gérer l’accès des utilisateurs aux add-ins. 

1. Dans le Centre d’administration, **sélectionnez Paramètres,** puis sélectionnez **Applications intégrées.** 
2. Dans la page Applications intégrées, une liste d’applications s’affiche : des applications individuelles ou des applications qui ont été liées à d’autres applications. 
3. Sélectionnez une application avec **l’état**    **d’autres applications disponibles** pour ouvrir le    **volet**   Gérer. L’état **d’autres** applications disponibles vous permet de savoir qu’il existe davantage   d’intégrations des isv qui ne sont pas encore déployées. 
4. Sous **l’onglet**   Vue d’ensemble, **sélectionnez Déployer.** Certaines applications nécessitent que vous ajoutiez des utilisateurs avant de pouvoir sélectionner Déployer. 
5. Sélectionnez **Utilisateurs,** **sélectionnez Est-ce qu’il s’agit** d’un déploiement de test, puis sélectionnez Toute l’organisation, **** **Utilisateurs/Groupes**   spécifiques ou **Juste moi**. Vous pouvez également sélectionner **Tester le déploiement** si vous préférez attendre le déploiement de l’application dans   l’ensemble de l’organisation. Des utilisateurs ou des groupes spécifiques peuvent être Microsoft 365 groupe de sécurité, un groupe de sécurité ou un groupe de distribution. 
6. Sélectionnez  **Mise à**   jour, puis **Terminé**. Vous pouvez maintenant sélectionner **Déployer sous** l’onglet **Vue d’ensemble.** 
7. Examinez les informations de l’application, puis sélectionnez **Déployer.**
8. Sélectionnez **Terminé** sur la page Déploiement terminé, puis examinez les détails du test ou du déploiement complet sous   l’onglet Vue   ****   d’ensemble. 
9. Si l’état de l’application est Mise à jour  en **attente,** vous pouvez cliquer sur l’application pour ouvrir le volet Gérer et mettre à jour l’application. 
10. Pour simplement mettre à jour les utilisateurs, sélectionnez **l’onglet Utilisateurs** et a apporter les changements appropriés. Sélectionnez **Mettre à** jour après avoir apporté vos modifications.  

## <a name="delete-an-add-in"></a>Suppression d’un complément

Vous pouvez également supprimer un module qui a été déployé.

1. Dans le Centre d’administration, **sélectionnez Paramètres,** puis sélectionnez **Applications intégrées.**
2. Sélectionnez n’importe quelle ligne pour afficher le volet de gestion. 
3. Sélectionnez **l’onglet Configuration.** 
4. Sélectionnez le module que vous souhaitez supprimer, puis sélectionnez **Supprimer.**  

> [!NOTE]
>  Si le add-in a été déployé par un autre administrateur, le bouton Supprimer est désactivé. Seul l’administrateur qui a déployé l’application ou un administrateur général peut supprimer le module.

## <a name="scenarios-where-exchange-admin-cannot-deploy-an-add-in"></a>Scénarios dans Exchange’administrateur ne peut pas déployer un add-in 

Il existe deux cas dans lesquels un administrateur Exchange ne peut pas déployer un add-in :
- Si un add-in a besoin d’autorisations sur MS Graph API et a besoin du consentement d’un administrateur général.
- Si un add-in est lié à au moins deux applications et applications web, et qu’au moins l’un de ces modules est déployé par un autre administrateur (exchange/global) et que l’affectation de l’utilisateur n’est pas uniforme. Nous permettons uniquement le déploiement des applications lorsque l’affectation de l’utilisateur est la même pour toutes les applications déjà déployées.  


## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="which-administrator-role-do-i-need-to-access-integrated-apps"></a>Quel rôle d’administrateur ai-je besoin pour accéder aux applications intégrées ?

Seuls les administrateurs globaux peuvent accéder aux applications intégrées. Les applications intégrées ne s’affichent pas dans le navigation gauche pour les autres administrateurs.

### <a name="why-do-i-see-add-in-in-the-left-nav-under-setting-but-not-integrated-apps"></a>Pourquoi le module de navigation de gauche s’insérait-il dans la partie paramètre, mais pas dans les applications intégrées ?

Il peut y avoir plusieurs raisons :

- L’administrateur connecté est un administrateur Exchange administrateur.
- Le client est dans un cloud souverain et l’expérience des applications intégrées est encore disponible pour les clients cloud souverains.

### <a name="what-apps-can-i-deploy-from-integrated-apps"></a>Quelles applications puis-je déployer à partir d’applications intégrées ?

Les applications intégrées permettent le déploiement d’applications web, d’applications Teams, de Excel, de PowerPoint, de Word, de Outlook de SPFx applications. Pour les applications intégrées, les applications intégrées permettent le déploiement vers Exchange boîtes aux lettres en ligne et non sur site Exchange boîtes aux lettres.

### <a name="can-administrators-delete-or-remove-apps"></a>Les administrateurs peuvent-ils supprimer ou supprimer des applications ?

Oui. Les administrateurs globaux peuvent supprimer ou supprimer des applications.

- Sélectionnez une application dans l’affichage Liste. Sous **l’onglet Configuration,** sélectionnez les applications à supprimer.  

### <a name="is-integrated-apps-available-in-sovereign-cloud"></a>Les applications intégrées sont-ils disponibles dans le cloud souverain ?

Non. Les applications intégrées ne sont pas disponibles pour les clients cloud souverains.

### <a name="is-integrated-apps-available-in-government-clouds"></a>Les applications intégrées sont-ils disponibles dans les clouds pour le gouvernement ?

Non. Les applications intégrées ne sont pas disponibles pour les clients cloud du gouvernement.
