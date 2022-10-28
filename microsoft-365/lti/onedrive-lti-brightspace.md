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
description: Créez et classez des devoirs, créez et organisez du contenu de cours et collaborez sur des fichiers en temps réel avec la nouvelle interopérabilité des outils d’apprentissage Microsoft OneDrive pour Desire2Learn Brightspace.
ms.openlocfilehash: d01a934d134ceb8b62658d81f0d6500c467f82b4
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68768498"
---
# <a name="integrate-microsoft-onedrive-lti-with-desire2learn-brightspace"></a>Intégrer Microsoft OneDrive LTI à Desire2Learn Brightspace

Ce guide fournit aux administrateurs informatiques les étapes d’inscription de l’application OneDrive LTI pour desire2Learn (D2L) Brightspace LMS.

Pour obtenir une vue d’ensemble de Microsoft LTI, consultez [Intégration de produits Microsoft à votre système de gestion de l’apprentissage (LMS).](index.md)

Les étapes pour ajouter l’application OneDrive LTI sont les suivantes :

1. [Étape 1 : Ajouter la nouvelle application Microsoft OneDrive LTI](#step-1-add-the-new-microsoft-onedrive-lti-app).
1. [Étape 2 : Déployer l’application LTI dans l’expérience Brightspace des utilisateurs](#step-2-deploy-the-lti-app-in-users-brightspace-experience).
1. [Étape 3 : Activer la nouvelle application OneDrive LTI sur la barre d’activité Des liens rapides](#step-3-turn-on-the-new-onedrive-lti-app-on-the-quicklinks-activity-bar).

> [!NOTE]
> La personne qui effectue cette intégration doit être un administrateur de Brightspace et un administrateur du locataire Microsoft 365.
>
> La documentation source pour les paramètres LTI 1.3 se trouve dans [LTI Advantage - Guide de l’administrateur](https://community.brightspace.com/s/article/LTI-Advantage-Administrator-Guide).

## <a name="step-1-add-the-new-microsoft-onedrive-lti-app"></a>Étape 1 : Ajouter la nouvelle application Microsoft OneDrive LTI

### <a name="register-a-new-microsoft-onedrive-lti-app"></a>Inscrire une nouvelle application Microsoft OneDrive LTI

1. Connectez-vous au [portail d’inscription Microsoft OneDrive LTI](https://onedrivelti.microsoft.com/admin).
1. Sélectionnez le bouton **Consentement Administration** et acceptez les autorisations.

   > [!IMPORTANT]
   > Si **Administration consentement** n’est pas accepté, l’étape suivante vous donnera une erreur et vous devrez attendre une heure avant de pouvoir continuer.

1. Sélectionnez le bouton **Créer un locataire LTI** .
1. Dans la liste **Plateforme de consommateurs LTI** , sélectionnez **D2L Brightspace**.
1. Dans le champ **URL de base D2L Brightspace** , entrez votre URL de base Brightspace, comme `https://myschool.brightspace.com`.
1. Sélectionnez le bouton **Suivant**. La page **Inscrire l’application LTI 1.3** se charge. \
   Gardez cette page ouverte dans son propre onglet lorsque vous effectuez les étapes suivantes. Les valeurs requises seront générées dans les étapes suivantes.

### <a name="add-microsoft-lti-app-to-brightspace"></a>Ajouter une application Microsoft LTI à Brightspace

1. Dans un nouvel onglet de navigateur, connectez-vous à votre brightspace LMS avec un compte *Administrateur* ou *Super Administrateur* pour la ou les organisations à laquelle vous souhaitez ajouter l’application OneDrive LTI.
1. Sélectionnez l’icône d’engrenage en haut à droite pour accéder à **Administration Tools**.
1. Sous la catégorie **Lié à l’organisation** , **recherchez Gérer l’extensibilité**. \
   L’URL doit ressembler à cet exemple : `https://<yourbrightspacedomain>/d2l/le/ltiadvantage/registrations/home`.
1. Sélectionnez l’onglet **Avantage LTI** en haut, puis sélectionnez **Inscrire un outil**.
1. Sélectionnez la case d’option **Standard** pour le **type d’inscription de l’outil**.
1. Entrez un nom pour l’application, par exemple `Microsoft OneDrive LTI App`.
1. Dans le champ **Domaine** , entrez `https://onedrivelti.microsoft.com`.
1. Accédez à l’onglet du navigateur avec le portail d’inscription Microsoft OneDrive LTI pour copier les autres valeurs requises :
    1. Collez la `ToolOIDCLaunchRedirectUri` valeur dans le champ **URL de redirection** .
       >[!IMPORTANT]
       >Vous utiliserez cette valeur **d’URL de redirection** dans les étapes ultérieures.
    1. Collez la valeur « OIDCLoginInitiationUri » dans le champ **URL de connexion OpenID Connect** .
    1. Collez la `ToolPublicJwksUri` valeur dans le champ **URL du jeu de clés** .
1. Sous **Extensions**, cochez la case **Liaison approfondie** .
1. Sélectionnez le bouton **Inscrire** en bas de la page. \
   Les détails de l’inscription de l’application Brightspace s’affichent. Laissez cette page ouverte dans son propre onglet lors de la réalisation des étapes suivantes.

### <a name="add-brightspace-lti-platform-registration-details-to-the-microsoft-onedrive-lti-registration-portal"></a>Ajouter les détails de l’inscription de la plateforme Brightspace LTI au portail d’inscription Microsoft OneDrive LTI

Une fois l’application inscrite dans Brightspace, vous copiez les valeurs du portail d’inscription de Brightspace dans le portail d’inscription LTI de Microsoft.

1. Revenez à l’onglet ouvert du navigateur de la page du portail d’inscription OneDrive LTI de Microsoft.
1. Copiez la page des détails d’inscription de l’application Brightspace requise et collez-les dans le portail d’inscription LTI de Microsoft.
    1. Collez la valeur **Issuer** de Brightspace dans le champ **LTI Issuer** de Microsoft.
    2. Collez la valeur du point de **terminaison d’authentification OpenID Connect** de Brightspace dans le champ **URL d’autorisation LTI** de Microsoft.
    3. Collez la valeur de **l’URL du jeu de clés Brightspace de Brightspace** dans le champ **LTI Public Jwks URL** de Microsoft.
    4. Collez la valeur de **l’URL du jeton d’accès Brightspace OAuth2 de Brightspace** dans le champ **URL du jeton d’accès LTI** de Microsoft.
    5. Collez la valeur **de l’ID client** de Brightspace dans le champ **ID client LTI** de Microsoft.
1. Sélectionnez **Enregistrer suivant** > . \
   Un message s’affiche indiquant que *le consommateur LTI a été créé avec succès.* \
   Facultatif : vous pouvez consulter les détails de l’inscription en sélectionnant le bouton **Afficher les locataires LTI** sur la page d’accueil.

## <a name="step-2-deploy-the-lti-app-in-users-brightspace-experience"></a>Étape 2 : Déployer l’application LTI dans l’expérience Brightspace des utilisateurs

Une fois que Microsoft OneDrive LTI et Brightspace sont connectés, vous devez déployer l’application OneDrive LTI dans l’expérience Brightspace des utilisateurs.

1. Dans l’onglet avec votre expérience d’administration Brightspace, accédez à **Administration Outils** > **Gérer l’avantage LTI d’extensibilité** >  pour afficher la liste des applications LTI Advantage.
1. Sélectionnez le nom de l’application LTI Advantage que vous avez créée à l’étape précédente.
1. Faites défiler vers le bas de la page et sélectionnez le lien **Afficher les déploiements** . \
   L’URL doit ressembler à cet exemple : `https://<yourbrightspacedomain>/d2l/le/ltiadvantage/deployments/home`
1. Sélectionnez **Nouveau déploiement**.
1. Sélectionnez l’application par le nom que vous avez entré lors de la création de l’inscription de l’application Brightspace, comme `Microsoft OneDrive LTI App`.
1. Entrez un nom de déploiement pour ce déploiement, par exemple `Microsoft OneDrive Deployment`.
1. Dans la section **Extensions** , sélectionnez **Liaison approfondie**.
1. Cochez toutes les cases des paramètres de sécurité, à l’exception **de Classlist** et **Anonymous**.
1. Ne sélectionnez pas de paramètres de configuration, de paramètres de substitution ou de paramètres client.
1. Sélectionnez **Ajouter des unités** d’organisation et choisissez les unités d’organisation que vous souhaitez utiliser la nouvelle application LTI.  \
   Vous pouvez sélectionner:
   - **L’organisation Racine** ainsi que l’option **Tous les descendants** pour inclure tout le monde.
   - Unités d’organisation individuelles pour inclure uniquement ces unités.
   - **Toutes les unités descendantes** utilisant les cases d’option dans la colonne **Options** .
1. Sélectionnez **Créer un déploiement**. \
   Votre nouveau déploiement s’affiche dans la liste. Laissez cette option d’onglet et passez aux étapes suivantes.

### <a name="create-links-to-the-onedrive-lti-app-in-brightspace"></a>Créer des liens vers l’application OneDrive LTI dans Brightspace

Cette étape ajoute l’application OneDrive LTI aux menus du brightspace LMS où les utilisateurs sélectionnent pour insérer des fichiers OneDrive.

1. Dans l’onglet avec votre expérience d’administration Brightspace, accédez à **Administration Outils** > **Gérer l’avantage LTI d’extensibilité** >  pour afficher la liste des applications LTI Advantage.
1. Sélectionnez le nom de l’application LTI Advantage que vous avez créée.
1. Faites défiler vers le bas de la page et sélectionnez le lien **Afficher les déploiements** .
1. Sélectionnez le nom du déploiement que vous avez créé à l’étape précédente.
1. Faites défiler vers le bas de la page et sélectionnez **Afficher les liens**.

#### <a name="create-a-deep-linking-quicklink-for-the-app-that-will-appear-in-the-quicklinks-menu"></a>Créer un **lien rapide de liaison** approfondie pour l’application qui s’affichera dans le menu **Liens rapides**

1. Dans la page **Afficher les liens** , sélectionnez **Nouveau lien**.
1. Entrez un nom pour le lien, par exemple `Microsoft OneDrive`. \
   Ce nom sera visible par les utilisateurs dans leur expérience Brightspace.
1. Collez **l’URL de redirection** dans le champ **URL** . \
   Il s’agit de la même **URL de redirection** que celle utilisée dans les étapes précédentes, répertoriée comme dans le `ToolOIDCLaunchRedirectUri` portail d’inscription OneDrive LTI de Microsoft.
1. Définissez le **type** sur **Lien rapide de liaison approfondie**.
1. Sélectionnez **+Ajouter un paramètre client** et entrez `launchType` pour le champ **Nom** et `linkSelection` pour le champ **Valeur** .
1. Sélectionnez le bouton **Enregistrer et fermer** .

#### <a name="create-a-deep-linking-insert-stuff-link-for-the-app-that-will-appear-in-the-insert-stuff-menu"></a>Créer un lien **Insérer des éléments de liaison approfondie** pour l’application qui s’affichera dans le menu **Insérer des éléments**

1. Dans la page **Afficher les liens** , sélectionnez **Nouveau lien**.
1. Entrez un nom pour le lien, par exemple `Microsoft OneDrive`. \
   Ce nom sera visible par les utilisateurs dans leur expérience Brightspace.
1. Collez **l’URL de redirection** dans le champ **URL** . \
   Il s’agit de la même **URL de redirection** que celle utilisée dans les étapes précédentes, répertoriée comme dans le `ToolOIDCLaunchRedirectUri` portail d’inscription OneDrive LTI de Microsoft.
1. Définissez type sur **Insertion** de **liens profonds**.
1. Sélectionnez le bouton **Enregistrer et fermer** .

## <a name="step-3-turn-on-the-new-onedrive-lti-app-on-the-quicklinks-activity-bar"></a>Étape 3 : Activer la nouvelle application OneDrive LTI sur la barre d’activité Des liens rapides

L’application OneDrive LTI est désormais disponible pour les utilisateurs, mais l’ancienne application OneDrive doit maintenant être désactivée.

1. Connectez-vous à votre portail d’administration Brightspace.
1. Accédez à **Administration** >  **Config Variable Browser**
1. Recherchez la variable intitulée **d2l.3rdParty.OneDrive.EnableOneDrivePicker** et définissez la valeur sur **off**.

Pour ajouter l’application OneDrive LTI à la barre d’activité de Brightspace pour un accès rapide, vous devez définir une **variable de configuration** d’unité d’organisation sur l’ID de lien de l’application LTI.

> [!NOTE]
> Vous devez répéter ces étapes pour chaque ID d’organisation (ou ID d’organisation parent) où vous souhaitez que l’application OneDrive LTI apparaisse dans la barre d’activité.

### <a name="collect-the-link-id"></a>Collecter l’ID de lien

1. Connectez-vous à Brightspace en tant qu’administrateur ou super administrateur.
1. Accédez à **Administration Outils** en sélectionnant l’icône d’engrenage en haut à droite.
1. Sélectionnez **Gérer l’extensibilité** pour afficher la liste **Déploiements LTI Advantage** .
1. Sélectionnez le nom de l’application LTI Advantage que vous avez créée.
1. Faites défiler vers le bas de la page et sélectionnez **Afficher les déploiements**.
1. Sélectionnez le nom du déploiement d’application que vous avez créé.
1. Faites défiler vers le bas de la page et sélectionnez **Afficher les liens**.
1. Sélectionnez le nom du lien avec le type **Lien rapide de liaison approfondie** .
1. Déplacez votre souris vers la barre d’adresse URL dans votre navigateur.
1. Copiez les chiffres numériques après la finale `/` dans l’URL. \
   Par exemple, si l’URL du lien est `https://example.desire2learn.com/d2l/le/ltiadvantage/deployments/3bfcc0b7-2fb6-4ffe-b353-95b520d4bae6/links/details/259`, copiez la `259` valeur numérique.

### <a name="update-the-config-variables"></a>Mettre à jour les variables de configuration

1. Dans le portail d’administration Brightspace, accédez à **Administration Outils** en sélectionnant l’icône d’engrenage en haut à droite.
1. Sélectionnez **Explorateur de variables de configuration**.
1. Dans le menu **Toutes les variables** à gauche, accédez à **3rdParty** > **Microsoft** > et sélectionnez **OneDriveLTI**. \
   Vous devez voir le nom `3rdparty.microsoft.onedriveLTI.linkId` de la variable dans le volet droit.
1. Sélectionnez le nom de **la variable LinkId** .
1. Dans l’écran **configuration de LinkId** , sélectionnez **Ajouter une valeur** pour sélectionner une **unité d’organisation** et collez la valeur numérique **ID de lien** que vous avez collectée précédemment.  \
   Vous devez répéter cette opération pour chaque unité d’organisation que vous souhaitez utiliser la **barre d’activité des liens rapides**.
1. Pour que ce paramètre soit appliqué aux types d’organisation décroissants de ceux que vous avez ajoutés, vous pouvez modifier les **types d’unités d’organisation en cascade** et sélectionner les types et l’ordre dans lequel les paramètres s’appliqueront.

L’application OneDrive LTI s’affiche désormais dans les menus **Ajouter du contenu existant**, **Liens rapides** et **Insérer des éléments** dans Brightspace.

Les utilisateurs verront une icône de lien générique plutôt qu’une icône de cloud OneDrive. Le nom affiché dans le menu sera le nom fourni dans les paramètres de lien LTI de l’application.

Ces liens peuvent être désactivés et activés comme vous le souhaitez et ciblés sur des organisations et des décedents spécifiques par configuration.

Pour plus d’informations sur la configuration des applications dans Brightspace, consultez [l’aide de Brightspace](https://documentation.brightspace.com).

## <a name="common-questions-concerning-the-onedrive-lti-app"></a>Questions courantes concernant l’application OneDrive LTI

### <a name="does-the-new-onedrive-lti-filepicker-support-personal-accounts"></a>Le nouveau OneDrive LTI FilePicker prend-il en charge les comptes personnels ?

Oui, les comptes personnels sont autorisés à ouvrir OneDrive pour charger les fichiers. Il existe une case à cocher dans l’application dans le portail d’inscription OneDrive LTI pour autoriser ou non plusieurs comptes. Si cette option est cochée, les comptes personnels sont autorisés.

### <a name="does-the-filepicker-support-multiple-languages"></a>FilePicker prend-il en charge plusieurs langues ?

Le Sélecteur de fichiers LTI OneDrive examine le paramètre de paramètre de langue LTI passé à partir du LMS et (en tant que sauvegarde) le paramètre de navigateur (car le premier est une revendication facultative) pour déterminer la langue à utiliser.
