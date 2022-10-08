---
title: Intégrer Microsoft OneDrive LTI à Desire2Learn Brightspace
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: microsoft-365-business
ms.collection: m365initiative-edu
ms.localizationpriority: medium
description: Créez et classez des affectations, générez et organisez du contenu de cours, et collaborez sur des fichiers en temps réel avec la nouvelle interopérabilité des outils d’apprentissage Microsoft OneDrive pour Desire2Learn Brightspace.
ms.openlocfilehash: 9c03ee2f46e77d8d24f7c731ac2e32b1dfc9cef2
ms.sourcegitcommit: 2ff545246fec060ea7829da5afbc1cdc698d51ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68363011"
---
# <a name="integrate-microsoft-onedrive-lti-with-desire2learn-brightspace"></a>Intégrer Microsoft OneDrive LTI à Desire2Learn Brightspace

Ce guide fournit aux administrateurs informatiques les étapes d’inscription de l’application LTI OneDrive pour Desire2Learn (D2L) Brightspace LMS.

Pour obtenir une vue d’ensemble de Microsoft LTI, consultez [Intégration des produits Microsoft à votre système de gestion de l’apprentissage (LMS).](index.md)

Les étapes à suivre pour ajouter l’application LTI OneDrive sont les suivantes :

1. [Étape 1 : Ajouter la nouvelle application LTI Microsoft OneDrive](#step-1-add-the-new-microsoft-onedrive-lti-app).
1. [Étape 2 : Déployer l’application LTI dans l’expérience Brightspace des utilisateurs](#step-2-deploy-the-lti-app-in-users-brightspace-experience).
1. [Étape 3 : Activez la nouvelle application LTI OneDrive dans la barre d’activité Liens rapides](#step-3-turn-on-the-new-onedrive-lti-app-on-the-quicklinks-activity-bar).

> [!NOTE]
> La personne qui effectue cette intégration doit être un administrateur de Brightspace et un administrateur du locataire Microsoft 365.
>
> La documentation source pour les paramètres LTI 1.3 se trouve dans le [guide LTI Advantage - Administrator](https://community.brightspace.com/s/article/LTI-Advantage-Administrator-Guide).

## <a name="step-1-add-the-new-microsoft-onedrive-lti-app"></a>Étape 1 : Ajouter la nouvelle application LTI Microsoft OneDrive

### <a name="register-a-new-microsoft-onedrive-lti-app"></a>Inscrire une nouvelle application LTI Microsoft OneDrive

1. Connectez-vous au [portail d’inscription LTI Microsoft OneDrive](https://onedrivelti.microsoft.com/admin).
1. Sélectionnez le bouton **Administration Consentement** et acceptez les autorisations.
   >[!IMPORTANT]
   >Si **Administration consentement** n’est pas accepté, l’étape suivante vous donnera une erreur et vous devrez attendre une heure avant de pouvoir continuer.
1. Sélectionnez le bouton **Créer un locataire LTI** .
1. Dans la liste **LTI Consumer Platform** , sélectionnez **D2L Brightspace**.
1. Dans le champ **URL de base D2L Brightspace** , entrez votre URL de base Brightspace, comme `https://myschool.brightspace.com`.
1. Sélectionnez le bouton **Suivant**. La page **Inscrire l’application LTI 1.3** se charge. \
   Laissez cette page ouverte dans son propre onglet lors de l’exécution de l’ensemble d’étapes suivant. Les valeurs requises seront générées dans les étapes suivantes.

### <a name="add-microsoft-lti-app-to-brightspace"></a>Ajouter une application Microsoft LTI à Brightspace

1. Dans un nouvel onglet de navigateur, connectez-vous à votre LMS Brightspace avec un compte *Administrateur* ou *Super Administrateur* pour l’organisation à laquelle vous souhaitez ajouter l’application LTI OneDrive.
1. Sélectionnez l’icône d’engrenage en haut à droite pour accéder à **Administration Tools**.
1. Dans la catégorie **Liée à l’organisation** , **recherchez Gérer l’extensibilité**. \
   L’URL doit ressembler à cet exemple : `https://<yourbrightspacedomain>/d2l/le/ltiadvantage/registrations/home`.
1. Sélectionnez l’onglet **Avantage LTI** en haut, puis **sélectionnez Inscrire un outil**.
1. Sélectionnez la case d’option **Standard** pour le **type d’inscription de l’outil**.
1. Entrez un nom pour l’application, par exemple `Microsoft OneDrive LTI App`.
1. Dans le champ **Domaine** , entrez `https://onedrivelti.microsoft.com`.
1. Accédez à l’onglet du navigateur avec le portail d’inscription LTI Microsoft OneDrive pour copier les autres valeurs requises :
    1. Collez la `ToolOIDCLaunchRedirectUri` valeur dans le champ **URL de redirection** .  
       >[!IMPORTANT] 
       >Vous utiliserez cette valeur **d’URL de redirection** dans les étapes ultérieures.
    1. Collez la valeur « OIDCLoginInitiationUri » dans le champ URL de connexion **OpenID Connect** .
    1. Collez la `ToolPublicJwksUri` valeur dans le champ **URL du jeu de clés** .
1. Sous **Extensions**, cochez la case **Liaison profonde** .
1. Sélectionnez le bouton **Inscrire** en bas de la page. \
   Les détails de l’inscription de l’application Brightspace s’affichent. Laissez cette page ouverte dans son propre onglet tout en suivant l’ensemble des étapes suivantes.

### <a name="add-brightspace-lti-platform-registration-details-to-the-microsoft-onedrive-lti-registration-portal"></a>Ajouter les détails de l’inscription de la plateforme LTI Brightspace au portail d’inscription LTI Microsoft OneDrive

Une fois l’application inscrite dans Brightspace, vous allez copier des valeurs à partir du portail d’inscription de Brightspace dans le portail d’inscription LTI de Microsoft.

1. Revenez à l’onglet de votre navigateur ouvert de la page portail d’inscription OneDrive LTI de Microsoft.
1. Copiez la page de détails d’inscription d’application Brightspace requise et collez-les dans le portail d’inscription LTI de Microsoft.
    1. Collez la valeur **Issuer** de Brightspace dans le champ **Émetteur LTI** de Microsoft.
    2. Collez la valeur du point de terminaison **d’authentification OpenID Connect** de Brightspace dans le champ **URL d’autorisation LTI** de Microsoft.
    3. Collez la valeur **d’URL du jeu de clés Brightspace de Brightspace** dans le champ **URL Jwks public LTI** de Microsoft.
    4. Collez la valeur **d’URL du jeton d’accès Brightspace OAuth2 de Brightspace** dans le champ **URL du jeton d’accès LTI** de Microsoft.
    5. Collez la valeur **d’ID client** de Brightspace dans le champ **ID client LTI** de Microsoft.
1. Sélectionnez **Enregistrer suivant** > **.** \
   Un message s’affiche indiquant que *le consommateur LTI a été créé avec succès.* \
   Facultatif : vous pouvez consulter les détails de l’inscription en sélectionnant le bouton **Afficher les locataires LTI** sur la page d’accueil.

## <a name="step-2-deploy-the-lti-app-in-users-brightspace-experience"></a>Étape 2 : Déployer l’application LTI dans l’expérience Brightspace des utilisateurs

Une fois que Microsoft OneDrive LTI et Brightspace sont connectés, vous devez déployer l’application LTI OneDrive dans l’expérience Brightspace des utilisateurs.

1. Sous l’onglet avec votre expérience d’administrateur Brightspace, accédez à **Administration Tools** > **Manage Extensibility** > **LTI Advantage** pour afficher la liste des applications LTI Advantage.
1. Sélectionnez le nom de l’application LTI Advantage que vous avez créée à l’étape précédente.
1. Faites défiler vers le bas de la page et sélectionnez le lien **Afficher les déploiements** . \
   L’URL doit ressembler à cet exemple : `https://<yourbrightspacedomain>/d2l/le/ltiadvantage/deployments/home`
1. Sélectionnez **Nouveau déploiement**.
1. Sélectionnez l’application par le nom que vous avez entré lors de la création de l’inscription de l’application Brightspace, comme `Microsoft OneDrive LTI App`.
1. Entrez un nom de déploiement pour ce déploiement, par exemple `Microsoft OneDrive Deployment`.
1. Dans la section **Extensions** , sélectionnez **Liaison profonde**.
1. Cochez toutes les cases des paramètres de sécurité, à l’exception de **Classlist** et **Anonymous**.
1. Ne sélectionnez pas les paramètres de configuration, les paramètres de substitution ou les paramètres client.
1. Sélectionnez **Ajouter des unités d’organisation** et choisissez les unités d’organisation que vous souhaitez utiliser la nouvelle application LTI.  \
   Vous pouvez sélectionner:
   - **L’organisation racine** avec l’option **Tous les descendants** pour inclure tout le monde.
   - Unités d’organisation individuelles pour inclure uniquement ces unités.
   - **Toutes les unités descendantes** utilisant les cases d’option dans la colonne **Options** .
1. Sélectionnez **Créer un déploiement**. \
   Votre nouveau déploiement s’affiche dans la liste. Conservez cette option d’onglet et passez aux étapes suivantes.

### <a name="create-links-to-the-onedrive-lti-app-in-brightspace"></a>Créer des liens vers l’application LTI OneDrive dans Brightspace

Cette étape ajoute l’application LTI OneDrive aux menus du LMS Brightspace où les utilisateurs sélectionnent pour insérer des fichiers OneDrive.

1. Sous l’onglet avec votre expérience d’administrateur Brightspace, accédez à **Administration Tools** > **Manage Extensibility** > **LTI Advantage** pour afficher la liste des applications LTI Advantage.
1. Sélectionnez le nom de l’application LTI Advantage que vous avez créée.
1. Faites défiler vers le bas de la page et sélectionnez le lien **Afficher les déploiements** .
1. Sélectionnez le nom du déploiement que vous avez créé à l’étape précédente.
1. Faites défiler vers le bas de la page et sélectionnez **Afficher les liens**.

#### <a name="create-a-deep-linking-quicklink-for-the-app-that-will-appear-in-the-quicklinks-menu"></a>Créer un **lien rapide de liaison profonde** pour l’application qui apparaîtra dans le menu **Liens rapides**

1. Dans la page **Afficher les liens** , sélectionnez **Nouveau lien**.
1. Entrez un nom pour le lien, par exemple `Microsoft OneDrive`. \
   Ce nom sera visible par les utilisateurs dans leur expérience Brightspace.
1. Collez **l’URL de redirection** dans le champ **URL** . \
   Il s’agit de **l’URL de redirection** utilisée dans les étapes précédentes, répertoriée dans le `ToolOIDCLaunchRedirectUri` portail d’inscription OneDrive LTI de Microsoft.
1. Définissez le **type** sur Lien **rapide de liaison profonde**.
1. Sélectionnez **+Ajouter un paramètre client** et entrez `launchType` le champ **Nom** et `linkSelection` le champ **Valeur** .
1. Sélectionnez le bouton **Enregistrer et fermer** .

#### <a name="create-a-deep-linking-insert-stuff-link-for-the-app-that-will-appear-in-the-insert-stuff-menu"></a>Créer un lien **insérer des éléments de liaison profonde** pour l’application qui apparaîtra dans le menu **Insérer des éléments**

1. Dans la page **Afficher les liens** , sélectionnez **Nouveau lien**.
1. Entrez un nom pour le lien, par exemple `Microsoft OneDrive`. \
   Ce nom sera visible par les utilisateurs dans leur expérience Brightspace.
1. Collez **l’URL de redirection** dans le champ **URL** . \
   Il s’agit de **l’URL de redirection** utilisée dans les étapes précédentes, répertoriée dans le `ToolOIDCLaunchRedirectUri` portail d’inscription OneDrive LTI de Microsoft.
1. Définissez le **type** sur **Des éléments d’insertion de liaison profonde**.
1. Sélectionnez le bouton **Enregistrer et fermer** .

## <a name="step-3-turn-on-the-new-onedrive-lti-app-on-the-quicklinks-activity-bar"></a>Étape 3 : Activer la nouvelle application LTI OneDrive dans la barre d’activité Liens rapides

L’application OneDrive LTI est désormais disponible pour les utilisateurs, mais l’ancienne application OneDrive doit maintenant être désactivée.

1. Connectez-vous à votre portail d’administration Brightspace.
1. Accédez à **Administration** >  **Config Variable Browser**
1. Recherchez la variable intitulée **d2l.3rdParty.OneDrive.EnableOneDrivePicker** et définissez la valeur sur **désactivée**.

Pour ajouter l’application LTI OneDrive à la barre d’activités de Brightspace pour un accès rapide, vous devez définir une **variable de configuration** d’unité d’organisation sur l’ID de lien de l’application LTI.

> [!NOTE]
> Vous devez répéter ces étapes pour chaque ID d’organisation (ou ID d’organisation parent) où vous souhaitez que l’application LTI OneDrive apparaisse dans la barre d’activité.

### <a name="collect-the-link-id"></a>Collecter l’ID de lien

1. Connectez-vous à Brightspace en tant qu’administrateur ou super administrateur.
1. Accédez à **Administration Tools** en sélectionnant l’icône d’engrenage en haut à droite.
1. Sélectionnez **Gérer l’extensibilité** pour afficher la liste **des déploiements de l’avantage LTI** .
1. Sélectionnez le nom de l’application LTI Advantage que vous avez créée.
1. Faites défiler jusqu’en bas de la page et sélectionnez **Afficher les déploiements**.
1. Sélectionnez le nom du déploiement d’application que vous avez créé.
1. Faites défiler vers le bas de la page et sélectionnez **Afficher les liens**.
1. Sélectionnez le nom du lien avec le type de **lien rapide de liaison profonde** .
1. Déplacez votre souris vers la barre d’adresses URL dans votre navigateur.
1. Copiez les chiffres numériques après la finale `/` dans l’URL. \
   Par exemple, si l’URL du lien est `https://example.desire2learn.com/d2l/le/ltiadvantage/deployments/3bfcc0b7-2fb6-4ffe-b353-95b520d4bae6/links/details/259`, copiez la `259` valeur numérique.

### <a name="update-the-config-variables"></a>Mettre à jour les variables de configuration

1. Dans le portail d’administration Brightspace, accédez à **Administration Tools** en sélectionnant l’icône d’engrenage en haut à droite.
1. Sélectionnez **Config Variable Browser**.
1. Dans le menu **Toutes les variables** à gauche, accédez à **3rdParty** > **Microsoft** > et sélectionnez **OneDriveLTI**. \
   Le nom `3rdparty.microsoft.onedriveLTI.linkId` de la variable doit apparaître dans le volet droit.
1. Sélectionnez le nom de la **variable LinkId** .
1. Dans l’écran **de configuration LinkId** , sélectionnez **Ajouter une valeur** pour sélectionner une **unité d’organisation** et collez la valeur d’ID **de lien** numérique que vous avez collectée précédemment.  \
   Vous devez répéter cette opération pour chaque unité d’organisation que vous souhaitez utiliser la **barre d’activité Liens rapides**.
1. Pour appliquer ce paramètre aux types d’organisation descendants de ceux que vous avez ajoutés, vous pouvez modifier les **types d’unités d’organisation en cascade** et sélectionner les types et l’ordre dans lequel les paramètres s’appliqueront.

L’application OneDrive LTI s’affiche désormais dans les menus **Ajouter du contenu existant**, **Liens rapides** et **Insertion de contenu** dans Brightspace.

Les utilisateurs verront une icône de lien générique plutôt qu’une icône de cloud OneDrive. Le nom indiqué dans le menu est le nom fourni dans les paramètres de lien LTI de l’application.  

Ces liens peuvent être désactivés et activés comme vous le souhaitez et destinés à des organisations et des décedents spécifiques par configuration.

Pour plus d’informations sur la configuration des applications dans Brightspace, consultez [l’aide de Brightspace](https://documentation.brightspace.com).

## <a name="common-questions-concerning-the-onedrive-lti-app"></a>Questions courantes concernant l’application LTI OneDrive

### <a name="does-the-new-onedrive-lti-filepicker-support-personal-accounts"></a>Le nouveau FilePicker OneDrive LTI prend-il en charge les comptes personnels ?

Oui, les comptes personnels sont autorisés à ouvrir OneDrive pour charger les fichiers. Il existe une case à cocher dans l’application dans le portail d’inscription onedrive LTI pour autoriser ou non plusieurs comptes. S’il est vérifié, les comptes personnels sont autorisés.

### <a name="does-the-filepicker-support-multiple-languages"></a>FilePicker prend-il en charge plusieurs langues ?

OneDrive LTI FilePicker examine le paramètre de langage LTI passé à partir du LMS et (en tant que sauvegarde) le paramètre de navigateur (étant donné que le premier est une revendication facultative) pour déterminer la langue à utiliser.
