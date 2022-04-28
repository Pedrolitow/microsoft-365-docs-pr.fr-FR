---
title: Tester et déployer Microsoft 365 Apps par des partenaires dans le portail des applications intégrées
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Recherchez, testez et déployez des applications partenaires Microsoft et Microsoft pour les utilisateurs et les groupes de votre organisation à partir du portail des applications intégrées dans le Centre d'administration Microsoft 365.
ms.openlocfilehash: 491315b36a7698399bcd22c60173db8cec482148
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094657"
---
# <a name="test-and-deploy-microsoft-365-apps-by-partners-in-the-integrated-apps-portal"></a>Tester et déployer Microsoft 365 Apps par des partenaires dans le portail des applications intégrées

Le Centre d'administration Microsoft 365 vous offre la possibilité de déployer des applications mono-magasin, des applications métier personnalisées et des applications partenaires Microsoft 365 à partir d’un emplacement unique. L’emplacement est accessible dans les paramètres du Centre d’administration Microsoft, dans les applications intégrées. La possibilité de rechercher, de tester et de déployer entièrement des applications achetées et sous licence par des partenaires Microsoft à partir du portail des applications intégrées offre la commodité et les avantages dont votre organisation a besoin pour que les services métier soient régulièrement mis à jour et s’exécutent efficacement.

Pour plus d’informations sur l’achat et la gestion des licences Microsoft 365 applications auprès de partenaires de votre organisation, consultez [Gérer et déployer des Microsoft 365 Apps à partir du Centre d'administration Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/manage-and-deploy-microsoft-365-apps-from-the-microsoft-365/ba-p/1194324).

Pour plus d’informations sur la façon dont les partenaires créent ces applications, consultez [Comment planifier une offre SaaS pour la Place de marché commerciale](https://go.microsoft.com/fwlink/?linkid=2158277)

Le portail des applications intégrées est uniquement accessible aux administrateurs généraux et disponible uniquement pour les clients du monde entier. Cette fonctionnalité n’est pas disponible dans les clouds souverains et gouvernementaux.

Le portail des applications intégrées affiche une liste d’applications, qui inclut des applications uniques et des applications Microsoft 365 des partenaires déployés par votre organisation. Seules les applications web, les applications SPFx, les compléments Office et les applications Teams sont répertoriées. Pour les applications web, vous pouvez voir deux types d’applications.

- Applications SaaS disponibles dans appsource.microsoft.com et pouvant être déployées par des administrateurs qui donnent leur consentement pour le compte de l’organisation.
- Applications de la galerie SAML liées à des compléments Office.

## <a name="manage-apps-in-the-integrated-apps-portal"></a>Gérer les applications dans le portail des applications intégrées

Vous pouvez gérer les tests et le déploiement de Microsoft 365 Apps achetées et sous licence auprès de partenaires.

1. Dans le Centre d’administration, sélectionnez **Paramètres**, puis sélectionnez **Applications intégrées**.

2. Choisissez une application avec **l’état** **d’autres applications disponibles** pour ouvrir le volet **Gérer** . L’état **d’un plus grand nombre d’applications disponibles** vous permet de savoir qu’il y a plus d’intégrations des éditeurs de logiciels indépendants qui ne sont pas encore déployées.

3. Sous l’onglet **Vue d’ensemble** , sélectionnez **Déployer**. Certaines applications vous obligent à ajouter des utilisateurs avant de pouvoir sélectionner Déployer.

4. Sélectionnez  **Utilisateurs**, choisissez **Est-ce un déploiement de test**, puis choisissez **Organisation entière**, **Utilisateurs/groupes spécifiques** ou **Juste moi**. Vous pouvez également choisir **le déploiement de test** si vous préférez attendre pour déployer l’application sur l’ensemble de l’organisation. Des utilisateurs ou groupes spécifiques peuvent être un groupe Microsoft 365, un groupe de sécurité ou un groupe de distribution.

5. Sélectionnez **Mettre à jour** , puis **Terminé**. Vous pouvez maintenant sélectionner Déployer sous l’onglet Vue d’ensemble.

6. Passez en revue les informations de l’application, puis sélectionnez **Déployer**.

7. Sélectionnez **Terminé** dans la page Déploiement terminé et passez en revue les détails du test ou du déploiement complet sous l’onglet **Vue d’ensemble** .

8. Si l’application a l’état **Mise à jour en attente**, vous pouvez cliquer sur l’application pour ouvrir le volet Gérer et mettre à jour l’application.

## <a name="find-published-apps-for-testing-and-full-deployment"></a>Rechercher des applications publiées pour le test et le déploiement complet

Vous pouvez rechercher, tester et déployer entièrement des applications publiées qui n’apparaissent pas déjà dans la liste de la page Applications intégrées. En achetant et en concédant des licences aux applications à partir du Centre d’administration, vous pouvez ajouter des applications partenaires Microsoft et Microsoft à votre liste à partir d’un emplacement unique.

1. Dans le centre d’administration, dans le volet de navigation gauche, choisissez **Paramètres**, puis choisissez <a href="https://go.microsoft.com/fwlink/p/?linkid=2125823" target="_blank">**Applications intégrées**</a>.

2. Sélectionnez **Obtenir des applications** pour obtenir une vue des applications.

3. Dans la **page Microsoft 365 Apps** applications publiées, sélectionnez l’application que vous souhaitez déployer en choisissant **Obtenir maintenant**. Les applications affichées sont principalement word, PowerPoint, Excel, Outlook compléments, applications Teams et applications SharePoint (basées sur SharePoint Framework technologie). Acceptez les autorisations et **sélectionnez Continuer**.

5. Sélectionnez **Déployer** en haut de la page en regard du message qui fait référence à l’attente de déploiement.

    Si l’application sélectionnée est liée à une offre SaaS par un éditeur de logiciels indépendants, toutes les autres applications qui font partie de cette offre liée apparaissent sur la page Configuration. Si vous choisissez de déployer toutes les applications, sélectionnez **Suivant**. Sinon, **sélectionnez Modifier** et choisissez les applications que vous souhaitez déployer. Certaines applications vous obligent à ajouter des utilisateurs avant de pouvoir sélectionner **Déployer**.

6. Sélectionnez **Ajouter des utilisateurs**, choisissez **Est-ce un déploiement de test**, puis choisissez **Organisation entière** ou **Utilisateurs/groupes spécifiques** ou **Juste moi**.

    Des utilisateurs/groupes spécifiques peuvent être un groupe Microsoft 365, un groupe de sécurité ou un groupe distribué. Vous pouvez également choisir **le déploiement de test** si vous préférez attendre pour déployer l’application sur l’ensemble de l’organisation.

7. Sélectionnez **Suivant** pour accéder à la page **Accepter la demande d’autorisation** . Les fonctionnalités et les autorisations d’application de chacune des applications sont répertoriées. Si l’application a besoin d’un consentement, **sélectionnez Accepter les autorisations**. Seul un administrateur général peut donner son consentement.

8. Sélectionnez **Suivant** pour passer en revue le déploiement et choisir **Terminer le déploiement**. Vous pouvez afficher le déploiement à partir de l’onglet **Vue d’ensemble** en choisissant **Afficher ce déploiement**. Dans le Centre d'administration Microsoft 365, vous pouvez voir l’état de chaque application déployée et la date de déploiement de l’application.

> [!NOTE]
> Si une application a déjà été déployée à partir d’un autre emplacement que le portail Des applications intégrées, le **type de déploiement** est **personnalisé.**

## <a name="unsupported-scenarios"></a>Scénarios non pris en charge

Vous ne pourrez pas déployer une seule application ou Microsoft 365 Apps par partenaire à partir du portail des applications intégrées pour les scénarios suivants.

- Le même complément est lié à plusieurs offres SaaS.
- L’offre SaaS est liée à des compléments, mais elle ne s’intègre pas à Microsoft Graph et aucun ID d’application AAD n’est fourni.
- L’offre SaaS est liée à des compléments, mais AAD ID d’application fourni pour l’intégration de Microsoft Graph est partagé entre plusieurs offres SaaS.

## <a name="upload-custom-line-of-business-apps-for-testing-and-full-deployment"></a>Télécharger applications métier personnalisées pour le test et le déploiement complet

1. Dans le centre d’administration, dans le volet de navigation gauche, choisissez **Paramètres**, puis **applications intégrées**.

2. Sélectionnez **Télécharger applications personnalisées**. Seule une ligne personnalisée d’applications pour Word, PowerPoint, Excel et Outlook est prise en charge.

3. Télécharger le fichier manifeste à partir de votre appareil ou ajoutez un lien URL. Certaines applications vous obligent à ajouter des utilisateurs avant de pouvoir sélectionner Déployer.

4. Sélectionnez **Ajouter des utilisateurs**, choisissez **Est-ce un déploiement de test**, puis choisissez **Organisation entière** ou **Utilisateurs/groupes spécifiques** ou **Juste moi**.

    Des utilisateurs/groupes spécifiques peuvent être un groupe Microsoft 365, un groupe de sécurité ou un groupe distribué. Vous pouvez également choisir **Le déploiement de test** si vous souhaitez attendre de déployer l’application sur l’ensemble de l’organisation.

5. Sélectionnez **Suivant** pour accéder à la page **Accepter la demande d’autorisation** . Les fonctionnalités et autorisations des applications sont répertoriées. Si l’application a besoin d’un consentement, **sélectionnez Accepter les autorisations**. Seul un administrateur général peut donner son consentement.

6. Sélectionnez **Suivant** pour passer en revue le déploiement et choisir **Terminer le déploiement**. Vous pouvez afficher le déploiement à partir de l’onglet **Vue d’ensemble** en choisissant **Afficher ce déploiement**.

## <a name="prepare-to-deploy-add-ins-in-integrated-apps"></a>Préparer le déploiement de compléments dans des applications intégrées

Office compléments vous aident à personnaliser vos documents et à simplifier la façon dont vous accédez aux informations sur le web (voir Commencer à utiliser votre complément Office). 

Les compléments offrent les avantages suivants : 

- Lorsque l’application Office appropriée démarre, le complément se télécharge automatiquement. Si le complément prend en charge les commandes de complément, le complément apparaît automatiquement dans le ruban dans l’application Office. 

- Les compléments n’apparaissent plus pour les utilisateurs si l’administrateur désactive ou supprime le complément, ou si l’utilisateur est supprimé de Azure Active Directory ou d’un groupe auquel le complément est affecté. 

Les compléments sont pris en charge dans trois plateformes de bureau Windows, Mac et Online Office applications. Il est également pris en charge dans iOS et Android (compléments Outlook mobile uniquement). 

L’affichage d’un complément pour le client pour tous les utilisateurs peut prendre jusqu’à 24 heures. 

Aujourd’hui, les administrateurs Exchange et les administrateurs généraux peuvent déployer des compléments à partir d’applications intégrées.   

### <a name="before-you-begin"></a>Avant de commencer

Le déploiement de compléments nécessite que les utilisateurs utilisent des licences Microsoft 365 Business (Business Basic, Business Standard, Business Premium), des licences Office 365 Entreprise (E1/E3/E5/F3) ou des licences Microsoft 365 Entreprise (E3/E5/F3). Les utilisateurs doivent également être connectés Office à l’aide de leur ID d’organisation) et avoir des boîtes aux lettres Exchange Online et actives Exchange Online. Votre répertoire d’abonnement doit être dans ou fédéré pour Azure Active Directory. 

Le déploiement ne prend pas en charge les éléments suivants : 

- des compléments ciblant Word, Excel ou PowerPoint dans Office 2013 ; 
- un service d'annuaire local ; 
- Déploiement de complément dans une boîte aux lettres Exchange local 
- Déploiement de compléments COM (Component Object Model) ou Visual Studio Tools pour Office (VSTO). 
- Déploiements de Microsoft 365 qui n’incluent pas de Exchange Online tels que Microsoft 365 Apps pour Les Entreprises et Microsoft 365 Apps pour Enterprise.  

### <a name="office-requirements"></a>Exigences en matière de Office 

Pour Les compléments Word, Excel et PowerPoint, vos utilisateurs doivent utiliser l’une des options suivantes : 
- Sur un appareil Windows, version 1704 ou ultérieure des licences Microsoft 365 Business (Business Basic, Business Standard, Business Premium), des licences Office 365 Entreprise (E1/E3/E5/F3) ou des licences Microsoft 365 Entreprise (E3/E5/F3). 
- Sur un Mac, version 15.34 ou ultérieure. 

Pour Outlook, vos utilisateurs doivent utiliser l’une des options suivantes : 
- Version 1701 ou ultérieure des licences Microsoft 365 Business (Business Basic, Business Standard, Business Premium), des licences Office 365 Entreprise (E1/E3/E5/F3) ou des licences Microsoft 365 Entreprise (E3/E5/F3). 
- Version 1808 ou ultérieure de Office Professionnel Plus 2019 ou Office Standard 2019. 
- Version 16.0.4494.1000 ou ultérieure de Office Professionnel Plus 2016 (MSI) ou Office Standard 2016 (MSI).
    > [!NOTE]
    > Les versions MSI de Outlook affichent les compléments installés par l’administrateur dans le ruban Outlook approprié, et non dans la section « Mes compléments ».  
- Version 15.0.4937.1000 ou ultérieure de Office Professionnel Plus 2013 (MSI) ou Office Standard 2013 (MSI).
- Version 16.0.9318.1000 ou ultérieure de Office 2016 pour Mac. 
- Version 2.75.0 ou ultérieure de Outlook mobile pour iOS. 
- Version 2.2.145 ou ultérieure de Outlook mobile pour Android. 



### <a name="exchange-online-requirements"></a>exigences de Exchange Online 
Microsoft Exchange stocke les manifestes de complément dans le locataire de votre organisation. L’administrateur qui déploie des compléments et les utilisateurs qui reçoivent ces compléments doivent se trouver sur une version de Exchange Online qui prend en charge l’authentification OAuth. 

Pour connaître la configuration utilisée, consultez l'administrateur Exchange de votre organisation. Vous pouvez vérifier la connectivité OAuth de chaque utilisateur à l'aide de l'applet de commande PowerShell [Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity). 

### <a name="user-and-group-assignments"></a>Affectations à des utilisateurs et groupes
Le déploiement du complément est actuellement pris en charge dans la majorité des groupes pris en charge par Azure Active Directory, notamment les groupes Microsoft 365, les listes de distribution et les groupes de sécurité. Le déploiement prend en charge les utilisateurs des groupes de niveau supérieur ou sans groupes parents, mais pas les utilisateurs des groupes imbriqués ou des groupes qui ont des groupes parents. 

> [!NOTE]
> Les groupes de sécurité sans extension messagerie ne sont pas actuellement pas pris en charge. 

Dans l’exemple suivant, Sandra, Sheila et le groupe Sales Department sont affectés à un complément. Le Service des ventes Région ouest étant un groupe imbriqué, aucun complément n'est affecté à Noël et Jérôme. 

![Diagramme du service des ventes.](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

### <a name="find-out-if-a-group-contains-nested-groups"></a>Déterminer si un groupe contient des groupes imbriqués

La manière la plus simple de détecter si un groupe contient des groupes imbriqués consiste à afficher la carte de visite du groupe dans Outlook. Si vous entrez le nom du groupe dans le champ **À** d’un e-mail, puis sélectionnez le nom du groupe lorsqu’il sera résolu, il vous indiquera s’il contient des utilisateurs ou des groupes imbriqués. Dans l'exemple ci-dessous, l'onglet **Membres** de la carte de visite Outlook du groupe Test n'affiche aucun utilisateur et seulement deux sous-groupes. 

![Onglet Membres de Outlook carte de visite.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

Vous pouvez effectuer la requête inverse en résolvant le groupe pour voir s'il est membre d'un groupe. Dans l'exemple ci-dessous, vous pouvez voir sous l'onglet <b>Appartenance</b> de la carte de visite Outlook que le Sous-groupe 1 est membre du groupe Test. 

![Onglet Appartenance de la carte de visite Outlook.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

Notez que vous pouvez utiliser le Azure Active Directory API Graph pour exécuter des requêtes afin de rechercher la liste des groupes au sein d’un groupe. Pour plus d'informations, voir [Opérations sur les groupes | Référence de l'API Graph](/previous-versions/azure/ad/graph/api/groups-operations). 

## <a name="recommended-approach-for-deploying-office-add-ins"></a>Approche recommandée pour le déploiement des compléments Office 
Pour déployer des compléments à l’aide d’une approche progressive, nous vous recommandons les éléments suivants : 
1. Déployez le complément vers un petit groupe de parties intéressées et de membres du service informatique. Vous pouvez activer l’indicateur **S’agit-il d’un déploiement de test**. Si le déploiement réussit, passez à l’étape 2. 

2. Déployer le complément pour un plus grand nombre de personnes au sein de l’entreprise. Là encore, évaluez les résultats et, en cas de réussite, poursuivez le déploiement complet. 

3. Effectuez un déploiement complet pour tous les utilisateurs. Désactivez l’indicateur à partir de **s’il s’agit d’un déploiement de test**. 

Selon la taille de l’audience cible, vous pouvez ajouter ou supprimer des étapes de déploiement.  

## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Déployer un complément Office à l’aide du Centre d’administration 

1. Dans le Centre d’administration, sélectionnez **Paramètres**, puis sélectionnez **Applications intégrées**. 

2. Sélectionnez **Obtenir des applications** en haut de la page. AppSource se charge dans un format incorporé. Recherchez un complément ou recherchez-le en cliquant sur Produit dans le volet de navigation gauche.  Si le complément a été lié par l’éditeur de logiciels indépendant à une application SaaS ou à d’autres applications et compléments, et si l’application SaaS est une application payante, une boîte de dialogue s’affiche pour acheter la licence ou déployer. Que vous ayez acheté ou non la licence, vous pouvez poursuivre le déploiement. Sélectionnez **Déployer**.  

3. Vous verrez la page **Configuration** où toutes les applications sont répertoriées. Si vous n’avez pas d’autorisations ni d’accès approprié pour déployer l’application, les informations correspondantes sont mises en surbrillance. Vous pouvez sélectionner les applications que vous souhaitez déployer. En sélectionnant **Suivant**, vous allez afficher la page **Utilisateurs** . Si le complément n’a pas été lié par l’éditeur de logiciels indépendants, vous êtes routée vers la page Utilisateurs. 

4. Sélectionnez **Tout le monde**, **utilisateurs/groupes spécifiques** ou **Juste moi** pour spécifier à qui le complément est déployé. Utilisez la zone de recherche pour rechercher des utilisateurs ou des groupes spécifiques. Si vous testez le complément, sélectionnez **S’agit-il d’un déploiement de test**. 

5. Sélectionnez **Suivant**. Toutes les fonctionnalités et autorisations de l’application sont affichées dans un seul volet, ainsi que des informations de certification si l’application a Microsoft 365 certification. La sélection du logo de certification permet à l’utilisateur de voir plus de détails sur la certification.  

6. Passez en revue, puis sélectionnez **Terminer le déploiement**.  

7. Une icône verte « tick » s’affiche lorsque le complément est déployé. Suivez les instructions sur la page pour tester le complément. 

> [!NOTE]
> Les utilisateurs devront peut-être relancer Office pour afficher l’icône de complément sur le ruban de l’application. Outlook des applications peuvent prendre jusqu’à 24 heures pour apparaître sur les rubans de l’application. 

Il est recommandé d’informer les utilisateurs et les groupes que le complément déployé est disponible. Envisagez d’envoyer un e-mail qui décrit quand et comment utiliser le complément. Incluez ou créez un lien pour aider le contenu ou les FAQ susceptibles d’aider les utilisateurs s’ils rencontrent des problèmes avec le complément. 

## <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Points à considérer lors de l'affectation d'un complément à des utilisateurs et groupes 

Les administrateurs généraux et les administrateurs Exchange peuvent affecter un complément à tout le monde ou à des utilisateurs et groupes spécifiques. Chaque option a des conséquences spécifiques : 

- **Chacun** Cette option affecte le complément à chaque utilisateur de l’organisation. Utilisez-la avec parcimonie et uniquement pour les compléments qui sont réellement universels pour l'ensemble de votre organisation. 

- **Utilisateurs** Si vous affectez un complément à un utilisateur individuel, puis déployez le complément sur un nouvel utilisateur, vous devez d’abord ajouter le nouvel utilisateur. 

- **Groupes** Si vous affectez un complément à un groupe, les utilisateurs qui sont ajoutés au groupe sont automatiquement affectés au complément. Lorsqu’un utilisateur est supprimé d’un groupe, il perd l’accès au complément. Dans les deux cas, aucune action supplémentaire n’est requise de la part de l’administrateur. 

- **Juste moi** Si vous attribuez un complément à vous-même, le complément est affecté uniquement à votre compte, ce qui est idéal pour tester le complément. 

La bonne option pour votre organisation dépend de votre configuration. Toutefois, nous vous recommandons d’effectuer des affectations à l’aide de groupes. En tant qu’administrateur, il peut être plus facile de gérer les compléments en utilisant des groupes et en contrôlant l’appartenance à ces groupes plutôt que d’affecter des utilisateurs individuels à chaque fois. Dans certains cas, vous souhaiterez peut-être restreindre l’accès à un petit ensemble d’utilisateurs en effectuant des affectations à des utilisateurs spécifiques en les affectant manuellement. 

### <a name="more-about-office-add-ins-security"></a>En savoir plus sur la sécurité des compléments Office 
Office compléments combinent un fichier manifeste XML qui contient des métadonnées sur le complément, mais qui pointe surtout vers une application web qui contient tout le code et la logique. Les fonctionnalités des compléments peuvent varier. Par exemple, les compléments peuvent :
- afficher des données. 
- lire le document d'un utilisateur pour fournir des services contextuels. 
- lire et écrire des données vers le document d'un utilisateur et à partir de celui-ci pour fournir une valeur à cet utilisateur.  

Pour plus d’informations sur les types et les fonctionnalités des compléments Office, consultez [Office vue d’ensemble de la plateforme de compléments](/office/dev/add-ins/overview/office-add-ins), en particulier la section « Anatomie d’un complément Office ». 

Pour interagir avec le document de l'utilisateur, le complément doit déclarer les autorisations dont il a besoin dans le fichier manifeste. Un modèle d'autorisations d'accès d'une API JavaScript à cinq niveaux fournit la base de la confidentialité et de la sécurité pour les utilisateurs des compléments du volet Office. La plupart des compléments de l'Office Store sont au niveau ReadWriteDocument. Presque tous les compléments prennent en charge le niveau ReadDocument au minimum. Pour plus d'informations sur les niveaux d'autorisation, voir [Demande d'autorisations pour l'utilisation d'API dans les compléments de contenu et du volet Office](/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins). 

Lors de la mise à jour d'un manifeste, les modifications standard sont apportées à l'icône et au texte d'un complément. Les commandes de complément changent parfois, contrairement aux autorisations du complément. L'application web dans laquelle le code et la logique du complément sont exécutés peut changer à tout moment, ce qui est la nature même des applications web. 

Les mises à jour des compléments se produisent comme suit : 
- **Complément métier : dans** ce cas, lorsqu’un administrateur a chargé explicitement un manifeste, le complément requiert que l’administrateur charge un nouveau fichier manifeste pour prendre en charge les modifications de métadonnées. Le complément est mis à jour au démarrage suivant des applications Office concernées. L'application web peut changer à tout moment. 

- **Office Complément du Store** : lorsqu’un administrateur sélectionne un complément dans le Office Store, si un complément est mis à jour dans le Office Store, la prochaine fois que les applications Office appropriées démarrent, le complément est mis à jour. L'application web peut changer à tout moment. 

> [!NOTE]
> Pour Word, Excel et PowerPoint utiliser un [catalogue d’applications SharePoint](https://dev.office.com/docs/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) pour déployer des compléments sur des utilisateurs dans un environnement local sans connexion à Microsoft 365 et/ou prise en charge de SharePoint compléments requis. Pour Outlook utilisez Exchange panneau de configuration pour déployer dans un environnement local sans connexion à Microsoft 365.  

## <a name="add-in-states"></a>États de complément
Un complément peut être **activé ou** **désactivé** . 

| État | Comment l’état se produit | Impact |
|:-----|:-----|:-----|
|**Actif**  <br/> |L’administrateur a chargé le complément et l’a affecté à des utilisateurs ou des groupes.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté voient celui-ci dans les clients concernés.  <br/> |
|**Désactivé**  <br/> |Un administrateur a désactivé le complément.  <br/> |Les utilisateurs et les groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> Si l'état du complément est modifié en Actif, les utilisateurs et groupes ont de nouveau accès à celui-ci.  <br/> |
|**Deleted**  <br/> |Un administrateur a supprimé le complément.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> |
 
Envisagez de supprimer un complément si personne ne l’utilise plus. Par exemple, la désactivation d’un complément peut être logique si un complément n’est utilisé que pendant des périodes spécifiques de l’année. 

## <a name="manage-an-office-add-in-using-the-admin-center"></a>Gérer un complément Office à l’aide du Centre d’administration

Après le déploiement, les administrateurs peuvent également gérer l'accès des utilisateurs aux modules complémentaires. 

1. Dans le Centre d’administration, sélectionnez **Paramètres**, puis sélectionnez **Applications intégrées**. 
2. Dans la page Applications intégrées, une liste d’applications sera soit des compléments uniques, soit des compléments qui ont été liés à d’autres applications. 
3. Sélectionnez une application avec **l’état** **d’autres applications disponibles** pour ouvrir le volet **Gérer** . L’état **d’un plus grand nombre d’applications disponibles** vous permet de savoir qu’il y a plus d’intégrations des éditeurs de logiciels indépendants qui ne sont pas encore déployées. 
4. Sous l’onglet **Vue d’ensemble** , sélectionnez **Déployer**. Certaines applications vous obligent à ajouter des utilisateurs avant de pouvoir sélectionner Déployer. 
5. Sélectionnez **Utilisateurs**, **Sélectionnez Est-ce un déploiement de test**, puis sélectionnez **Organisation entière**, **Utilisateurs/groupes spécifiques** ou **Juste moi**. Vous pouvez également sélectionner **Tester le déploiement** si vous préférez attendre pour déployer l’application dans toute l’organisation. Des utilisateurs ou groupes spécifiques peuvent être un groupe Microsoft 365, un groupe de sécurité ou un groupe de distribution. 
6. Sélectionnez **Mettre à jour** , puis **Terminé**. Vous pouvez maintenant sélectionner **Déployer** sous l’onglet **Vue d’ensemble** . 
7. Passez en revue les informations de l’application, puis sélectionnez **Déployer**.
8. Sélectionnez **Terminé** dans la page **Déploiement terminé** , puis passez en revue les détails du test ou du déploiement complet sous l’onglet **Vue d’ensemble** . 
9. Si l’application a l’état **Mise à jour en attente**, vous pouvez cliquer sur l’application pour ouvrir le volet **Gérer** et mettre à jour l’application. 
10. Pour mettre à jour simplement les utilisateurs, sélectionnez l’onglet **Utilisateurs** et apportez la modification appropriée. Sélectionnez **Mettre à jour** après avoir apporté vos modifications.  

## <a name="delete-an-add-in"></a>Suppression d’un complément

Vous pouvez également supprimer un module qui a été déployé.

1. Dans le Centre d’administration, sélectionnez **Paramètres**, puis sélectionnez **Applications intégrées**.
2. Sélectionnez n’importe quelle ligne pour afficher le volet de gestion. 
3. Sélectionnez l’onglet **Configuration** . 
4. Sélectionnez le complément à supprimer, puis **sélectionnez Supprimer**.  

> [!NOTE]
>  Si le complément a été déployé par un autre administrateur, le bouton Supprimer est désactivé. Seul l’administrateur qui a déployé l’application ou un administrateur général peut supprimer le complément.

## <a name="scenarios-where-exchange-admin-cannot-deploy-an-add-in"></a>Scénarios où Exchange administrateur ne peut pas déployer un complément 

Il existe deux cas où un administrateur Exchange ne peut pas déployer un complément :
- Si un complément a besoin d’une autorisation sur MS Graph API et doit obtenir le consentement d’un administrateur général.
- Si un complément est lié à au moins deux compléments et applications web, et qu’au moins un de ces compléments est déployé par un autre administrateur (exchange/global) et que l’affectation de l’utilisateur n’est pas uniforme. Nous autorisons uniquement le déploiement de compléments lorsque l’affectation de l’utilisateur est identique pour toutes les applications déjà déployées.  


## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="which-administrator-role-do-i-need-to-access-integrated-apps"></a>Quel rôle d’administrateur dois-je accéder aux applications intégrées ?

Seuls les administrateurs généraux peuvent accéder aux applications intégrées. Les applications intégrées ne s’affichent pas dans la navigation de gauche pour les autres administrateurs.

### <a name="why-do-i-see-add-in-in-the-left-nav-under-setting-but-not-integrated-apps"></a>Pourquoi le complément s’affiche-t-il dans la navigation de gauche sous Paramètre, mais pas dans les applications intégrées ?

Il peut y avoir quelques raisons :

- L’administrateur connecté est un administrateur Exchange.
- Le client est dans le cloud souverain et l’expérience des applications intégrées est encore disponible pour les clients du cloud souverain.

### <a name="what-apps-can-i-deploy-from-integrated-apps"></a>Quelles applications puis-je déployer à partir d’applications intégrées ?

Les applications intégrées permettent le déploiement de Web Apps, d’applications Teams, de Excel, de PowerPoint, de Word, de compléments Outlook et d’applications SPFx. Pour les compléments, les applications intégrées prennent en charge le déploiement pour Exchange boîtes aux lettres en ligne et non des boîtes aux lettres Exchange locales.

### <a name="can-administrators-delete-or-remove-apps"></a>Les administrateurs peuvent-ils supprimer ou supprimer des applications ?

Oui. Les administrateurs généraux peuvent supprimer ou supprimer des applications.

- Sélectionnez une application dans l’affichage liste. Sous l’onglet **Configuration** , sélectionnez les applications à supprimer.  

### <a name="is-integrated-apps-available-in-sovereign-cloud"></a>Les applications intégrées sont-elles disponibles dans le cloud souverain ?

Non. Les applications intégrées ne sont pas disponibles pour les clients du cloud souverain.

### <a name="is-integrated-apps-available-in-government-clouds"></a>Les applications intégrées sont-elles disponibles dans les clouds gouvernementaux ?

Non. Les applications intégrées ne sont pas disponibles pour les clients cloud gouvernementaux.
