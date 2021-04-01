---
title: Tester et déployer microsoft 365 Apps par des partenaires dans le portail Applications intégrées
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
description: Recherchez, testez et déployez des applications partenaires Microsoft et Microsoft pour les utilisateurs et les groupes de votre organisation à partir du portail Applications intégrées dans le Centre d’administration Microsoft 365.
ms.openlocfilehash: f806d48e0ed582b1b5c1ee262058ce987125bd99
ms.sourcegitcommit: 7ebed5810480d7c49f8ca03207b5ea84993d253f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "51488288"
---
# <a name="test-and-deploy-microsoft-365-apps-by-partners-in-the-integrated-apps-portal"></a>Tester et déployer microsoft 365 Apps par des partenaires dans le portail Applications intégrées

Le Centre d’administration Microsoft 365 vous offre la flexibilité nécessaire pour déployer des applications de magasin unique, des applications métier personnalisées et des applications partenaires Microsoft 365 à partir d’un seul emplacement. L’emplacement est accessible dans le Centre d’administration Microsoft > Paramètres > applications intégrées. La possibilité de rechercher, tester et déployer entièrement des applications achetées et sous licence par des partenaires Microsoft à partir du portail d’applications intégrées offre la commodité et les avantages dont votre organisation a besoin pour maintenir les services professionnels mis à jour régulièrement et efficacement.

Pour plus d’informations sur l’achat et la gestion des licences d’applications Microsoft 365 auprès de partenaires de votre organisation, voir Gérer et déployer Microsoft 365 Apps à partir du Centre d’administration [Microsoft 365.](https://techcommunity.microsoft.com/t5/microsoft-365-blog/manage-and-deploy-microsoft-365-apps-from-the-microsoft-365/ba-p/1194324)

Pour plus d’informations sur la façon dont les partenaires créent ces applications, voir Comment planifier une offre [SaaS pour le marché commercial](https://go.microsoft.com/fwlink/?linkid=2158277)

Le portail des applications intégrées est uniquement accessible aux administrateurs globaux et disponible uniquement pour les clients WorldWide. Cette fonctionnalité n’est pas disponible dans les clouds souverains et du gouvernement.

Le portail Applications intégrées affiche une liste d’applications, qui inclut des applications individuelles et des applications Microsoft 365 provenant de partenaires déployés dans votre organisation. Seules les applications web, les applications SPFx, les applications Office et les applications Teams sont répertoriées. Pour les applications web, nous pouvons voir 2 types d’applications.

- Applications SaaS disponibles dans appsource.microsoft.com, et qui peuvent être déployées par les administrateurs accordant leur consentement au nom de l’organisation.
- Applications de galerie SAML liées aux applications Office.

## <a name="manage-apps-in-the-integrated-apps-portal"></a>Gérer les applications dans le portail Applications intégrées

Vous pouvez gérer les tests et le déploiement des applications Microsoft 365 achetées et sous licence auprès de partenaires.

1. Dans le centre d’administration, dans le navigation de gauche, choisissez **Paramètres,** puis choisissez **Applications intégrées.**

2. Choisissez une application avec **l’état** **d’autres applications disponibles** pour ouvrir **le volet** Gérer. L’état **d’autres** applications disponibles vous permet de savoir qu’il existe davantage d’intégrations des isv qui ne sont pas encore déployées.

3. Sous **l’onglet Vue** d’ensemble, **sélectionnez Déployer.** Certaines applications nécessitent que vous ajoutiez des utilisateurs avant de pouvoir sélectionner Déployer.

4. Sélectionnez **Utilisateurs,** **sélectionnez Est-ce un déploiement de test,** puis choisissez Toute l’organisation , **Utilisateurs/groupes spécifiques** ou **Simplement moi**.  Vous pouvez également choisir **de tester le déploiement** si vous préférez attendre le déploiement de l’application dans toute l’organisation. Des utilisateurs ou des groupes spécifiques peuvent être un groupe Microsoft 365, un groupe de sécurité ou un groupe de distribution.

5. Sélectionnez **Mettre à** jour, puis **Terminé.** Vous pouvez maintenant sélectionner Déployer sous l’onglet Vue d’ensemble.

6. Examinez les informations de l’application, puis sélectionnez **Déployer.**

7. Sélectionnez **Terminé** sur la page Déploiement terminé et examinez les détails du test ou du déploiement complet sous l’onglet **Vue d’ensemble.**

8. Si l’état de l’application est Mise à jour en **attente,** vous pouvez cliquer sur l’application pour ouvrir le volet Gérer et mettre à jour l’application.

## <a name="find-published-apps-for-testing-and-full-deployment"></a>Rechercher des applications publiées pour le test et le déploiement complet

Vous pouvez rechercher, tester et déployer entièrement des applications publiées qui n’apparaissent pas déjà dans la liste de la page Applications intégrées. En achetant et en accordant des licences aux applications à partir du Centre d’administration, vous pouvez ajouter des applications partenaires Microsoft et Microsoft à votre liste à partir d’un emplacement unique.

1. Dans le centre d’administration, dans le navigation de gauche, choisissez **Paramètres,** puis choisissez **Applications intégrées.**

2. Sélectionnez **Obtenir des** applications pour obtenir une vue des applications.

3. Dans la page **Applications microsoft 365** publiées, sélectionnez l’application que vous souhaitez déployer en choisissant **Obtenir maintenant.** Les applications affichées sont principalement Word, PowerPoint, Excel, les applications Outlook, l’application Teams et les applications SharePoint (intégrées à la technologie SharePoint Framework). Acceptez les autorisations et sélectionnez **Continuer**.

5. **Sélectionnez** Déployer en haut de la page en haut du message qui fait référence à l’attente de déploiement.

    Si l’application sélectionnée est liée à une offre SaaS par un isv, toutes les autres applications faisant partie de cette offre liée apparaissent sur la page Configuration. Si vous choisissez de déployer toutes les applications, sélectionnez **Suivant**. Dans le cas contraire, **sélectionnez** Modifier et choisissez les applications que vous souhaitez déployer. Certaines applications nécessitent que vous ajoutiez des utilisateurs avant de pouvoir sélectionner **Déployer.**

6. Sélectionnez **Ajouter des** utilisateurs, choisissez **Est-ce qu’il s’agit** d’un déploiement de test, puis choisissez Toute l’organisation ou des utilisateurs/groupes spécifiques ou Simplement **moi**.  

    Des utilisateurs/groupes spécifiques peuvent être un groupe Microsoft 365, un groupe de sécurité ou un groupe distribué. Vous pouvez également choisir **de tester le déploiement** si vous préférez attendre le déploiement de l’application dans toute l’organisation.

7. Sélectionnez **Suivant** pour obtenir la page **Accepter la demande d’autorisation.** Les fonctionnalités et autorisations de chacune des applications sont répertoriées. Si l’application a besoin de consentement, **sélectionnez Accepter les autorisations.** Seul un administrateur général peut donner son consentement.

8. Sélectionnez **Suivant** pour passer en revue le déploiement et choisissez **Terminer le déploiement.** Vous pouvez afficher le déploiement à partir de l’onglet **Vue** d’ensemble en **choisissant Afficher ce déploiement.** Dans le Centre d’administration Microsoft 365, vous pouvez voir l’état de chaque application déployée et la date à laquelle vous avez déployé l’application.

> [!NOTE]
> Si une application a été précédemment déployée à partir d’un autre portail que le portail Applications intégrées, le **type de** déploiement est **personnalisé.**

## <a name="unsupported-scenarios"></a>Scénarios non pris en place

Vous ne pourrez pas déployer une seule application store ou microsoft 365 Apps par partenaire à partir du portail d’applications intégrées pour les scénarios suivants.

- Le même add-in est lié à plusieurs offres SaaS.
- L’offre SaaS est liée aux applications, mais elle ne s’intègre pas à Microsoft Graph et aucun ID d’application AAD n’est fourni.
- L’offre SaaS est liée aux applications, mais l’ID d’application AAD fourni pour l’intégration de Microsoft Graph est partagé entre plusieurs offres SaaS.

## <a name="upload-custom-line-of-business-apps-for-testing-and-full-deployment"></a>Charger une gamme personnalisée d’applications métiers pour le test et le déploiement complet

1. Dans le centre d’administration, dans le navigation gauche, choisissez **Paramètres,** puis **Applications intégrées.**

2. Sélectionnez **Télécharger des applications personnalisées.** Seule une ligne personnalisée d’applications pour Word, PowerPoint, Excel et Outlook est prise en charge.

3. Téléchargez le fichier manifeste à partir de votre appareil ou ajoutez un lien URL. Certaines applications nécessitent que vous ajoutiez des utilisateurs avant de pouvoir sélectionner Déployer.

4. Sélectionnez **Ajouter des** utilisateurs, choisissez **Est-ce un déploiement de test** et choisissez Toute l’organisation ou des **utilisateurs/groupes** spécifiques ou **Moi uniquement**. 

    Des utilisateurs/groupes spécifiques peuvent être un groupe Microsoft 365, un groupe de sécurité ou un groupe distribué. Vous pouvez également choisir **De tester le déploiement** si vous souhaitez attendre le déploiement de l’application dans l’ensemble de l’organisation.

5. Sélectionnez **Suivant** pour obtenir la page **Accepter la demande d’autorisation.** Les fonctionnalités et autorisations des applications sont répertoriées. Si l’application a besoin de consentement, **sélectionnez Accepter les autorisations.** Seul un administrateur général peut donner son consentement.

6. Sélectionnez **Suivant** pour passer en revue le déploiement et choisissez **Terminer le déploiement.** Vous pouvez afficher le déploiement à partir de l’onglet **Vue** d’ensemble en **choisissant Afficher ce déploiement.**

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="which-administrator-role-do-i-need-to-access-integrated-apps"></a>Quel rôle d’administrateur ai-je besoin pour accéder aux applications intégrées ?

Seuls les administrateurs globaux peuvent accéder aux applications intégrées. Les applications intégrées ne s’affichent pas dans le navigation gauche pour les autres administrateurs.

### <a name="why-do-i-see-add-in-in-the-left-nav-under-setting-but-not-integrated-apps"></a>Pourquoi le module de navigation de gauche s’insérait-il dans la partie paramètre, mais pas dans les applications intégrées ?

Il peut y avoir plusieurs raisons :

- L’administrateur connecté est un administrateur Exchange.
- Le client est dans un cloud souverain et l’expérience des applications intégrées est encore disponible pour les clients cloud souverains.

### <a name="what-apps-can-i-deploy-from-integrated-apps"></a>Quelles applications puis-je déployer à partir d’applications intégrées ?

Les applications intégrées permettent le déploiement d’applications web, d’applications Teams, d’Excel, de PowerPoint, de Word, de add-ins Outlook et d’applications SPFx. Pour les applications intégrées, les applications intégrées prend en charge le déploiement vers les boîtes aux lettres Exchange Online et non dans les boîtes aux lettres Exchange sur site.

### <a name="can-administrators-delete-or-remove-apps"></a>Les administrateurs peuvent-ils supprimer ou supprimer des applications ?

Oui. Les administrateurs globaux peuvent supprimer ou supprimer des applications.

- Sélectionnez une application dans l’affichage Liste. Sous **l’onglet Configuration,** sélectionnez les applications à supprimer.  

### <a name="is-integrated-apps-available-in-sovereign-cloud"></a>Les applications intégrées sont-ils disponibles dans le cloud souverain ?

Non. Les applications intégrées ne sont pas disponibles pour les clients cloud souverains.

### <a name="is-integrated-apps-available-in-government-clouds"></a>Les applications intégrées sont-ils disponibles dans les clouds pour le gouvernement ?

Non. Les applications intégrées ne sont pas disponibles pour les clients cloud du gouvernement.
