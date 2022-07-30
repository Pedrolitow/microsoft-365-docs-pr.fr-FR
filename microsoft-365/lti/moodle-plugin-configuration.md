---
title: Configurer et configurer les plug-ins Moodle LMS
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
description: Préparez-vous à intégrer Moodle et Microsoft Teams en configurant et en configurant les plug-ins Moodle LMS.
ms.openlocfilehash: 5c986022923fe2322ad0e24f2e455d6fc502154e
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2022
ms.locfileid: "67084782"
---
# <a name="set-up-the-moodle-lms-plugins"></a>Configurer les plug-ins Moodle LMS

Dans cet article, vous allez apprendre à installer et à configurer les plug-ins Moodle LMS pour intégrer Microsoft Teams à votre expérience Moodle.

## <a name="prerequisites"></a>Configuration requise

Voici les conditions préalables à la configuration d’un Moodle installé pour qu’il fonctionne avec Microsoft Teams :

- Informations d’identification de l’administrateur Moodle.
- Informations d’identification de l’administrateur Azure AD.
- Un abonnement Azure dans lequel vous pouvez créer des ressources.

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Installer les plug-ins Moodle Microsoft 365

L’intégration de Moodle à Microsoft Teams est optimisée par le open source jeu [de plug-ins Moodle Microsoft 365](https://moodle.org/plugins/browse.php?list=set&id=72).

### <a name="requisite-applications-and-plugins"></a>Applications et plug-ins requis

Téléchargez et installez les éléments suivants :

1. Version [stable actuelle de Moodle](https://download.moodle.org/releases/latest/).

    > [!IMPORTANT]
    > Si vous n’avez pas de site Moodle existant, accédez au référentiel [Moodle sur Azure](https://github.com/azure/moodle) , déployez rapidement une instance Moodle et personnalisez-la en fonction de vos besoins.

1. Téléchargez et enregistrez moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) et les plug-ins [Microsoft 365 Integration](https://moodle.org/plugins/local_o365) sur votre ordinateur local.

    > [!NOTE]
    > L’installation des plug-ins OpenID Connect et Microsoft 365 Integration est nécessaire pour l’intégration teams.
    >
    > En outre, nous vous recommandons d’installer le plug-in [Thème Microsoft 365 Teams](https://moodle.org/plugins/theme_boost_o365teams) .

### <a name="install-plugins"></a>Installer des plug-ins

1. Téléchargez les plug-ins, extrayez-les et chargez-les dans leurs dossiers correspondants.
    - Extrayez le plug-in OpenID Connect (auth_oidc) dans un dossier appelé **oidc**, puis chargez-le dans le dossier **d’authentification** de la racine de votre document Moodle.
    - Extrayez le plug-in Microsoft 365 Integration (local_o365) dans un dossier appelé **o365**, puis chargez-le dans le dossier **local** de la racine de votre document Moodle.
1. Connectez-vous à votre site Moodle en tant qu’administrateur et sélectionnez **Administration du site**.
1. Lors de la détection de nouveaux plug-ins à installer, Moodle doit vous rediriger vers la page installer les nouveaux plug-ins. Si cela ne se produit pas, dans la page **Administration du site** , sélectionnez **Notifications** sous l’onglet **Général** . Cette action doit déclencher l’installation des plug-ins.
1. Une fois les nouveaux plug-ins installés, Moodle affiche une page avec toutes les nouvelles configurations des plug-ins installés. Vous pouvez ignorer cette page en toute sécurité en appliquant les paramètres par défaut. Les plug-ins seront configurés dans les étapes suivantes.

## <a name="2-enable-the-openid-connect-authentication-plugin"></a>2. Activer le plug-in d’authentification OpenID Connect

Pour que les plug-ins Moodle communiquent avec les services Microsoft, le plug-in d’authentification OpenID Connect doit être activé et configuré.

1. Accédez à **l’authentification** **des plug-ins** >  **d’administration** >  de site, puis **sélectionnez Gérer l’authentification**.
1. Recherchez le plug-in **d’authentification OpenID Connect** et sélectionnez *l’icône d’œil* pour l’activer.
1. Sélectionnez **Paramètres** du plug-in pour vérifier les points de terminaison **d’autorisation** et de **jeton** .
    1. Les valeurs par défaut doivent être les suivantes :
        1. Point de terminaison d’autorisation : ``https://login.microsoftonline.com/common/oauth2/authorize``.
        1. Point de terminaison de jeton : ``https://login.microsoftonline.com/common/oauth2/token``.
1. Enregistrez **l’URI de redirection** pour une utilisation ultérieure.

    > [!NOTE]
    > Il n’est pas obligatoire pour tous les utilisateurs Moodle du plug-in d’authentification OpenID Connect comme méthode d’authentification ; toutefois, s’ils utilisent d’autres méthodes d’authentification, leurs comptes Moodle doivent être *connectés* à leurs comptes Microsoft correspondants avant de pouvoir utiliser certaines fonctionnalités de l’intégration Teams, telles que la synchronisation de la propriété et de l’appartenance à Teams.

## <a name="3-configure-the-connection-between-the-microsoft-365-plugins-and-microsoft-services"></a>3. Configurer la connexion entre les plug-ins Microsoft 365 et les services Microsoft

Vous devez configurer la connexion entre les plug-ins Microsoft 365 et les services Microsoft pour qu’ils puissent fonctionner ensemble.

> [!NOTE]
> Lors de la configuration de l’intégration, laissez votre page de configuration d’intégration Moodle Microsoft 365 ouverte dans un onglet de navigateur distinct, car vous devez revenir à cet ensemble de pages tout au long du processus.

### <a name="create-azure-app"></a>Créer une application Azure

1. Accédez aux **plug-ins** > **locaux** **d’administration** >  de site, puis sélectionnez **Microsoft 365 Integration**. La page de configuration de l’intégration de Microsoft 365 s’ouvre.

1. Dans la page de configuration de l’intégration de Microsoft 365, sélectionnez l’onglet **Configuration** .

1. Sélectionnez le bouton **Télécharger le script PowerShell** et enregistrez-le sous forme de dossier ZIP sur votre ordinateur local.

    > [!NOTE]
    > L’exécution du script crée une application Azure AD dans le locataire Microsoft 365, qui configure les URL de réponse et les autorisations requises, donne les autorisations requises et retourne les `AppID` et `Key`.
    >
    > Le script PowerShell fonctionne uniquement sur les systèmes d’exploitation Windows.

1. Préparez le script PowerShell à partir du fichier ZIP comme suit :
    1. Téléchargez et extrayez le `Moodle-AzureAD-Powershell.zip` fichier.
    1. Ouvrez le dossier extrait.
    1. Cliquez avec le bouton droit sur le `Moodle-AzureAD-Script.ps1` fichier et sélectionnez **Propriétés**.
    1. Sous l’onglet **Général** de l’Fenêtre Propriétés, cochez la `Unblock` case en regard de l’attribut **Sécurité** situé en bas de la fenêtre.
    1. Sélectionnez **OK**.
    1. Copiez le chemin d’accès au répertoire dans le dossier extrait.

1. Exécutez PowerShell en tant qu’administrateur :
    1. Dans Windows, **sélectionnez Démarrer**.
    1. Tapez `PowerShell`.
    1. Cliquez avec le bouton droit sur **Windows PowerShell**.
    1. Sélectionnez **Exécuter en tant qu’administrateur**.

1. Accédez au répertoire décompressé en tapant `cd .../.../Moodle-AzureAD-Powershell` où `.../...` se trouve le chemin d’accès au répertoire.

1. Exécutez le script PowerShell :
    1. Entrez `./Moodle-AzureAD-Script.ps1`.
    1. Lorsque vous y êtes invité, connectez-vous à votre compte d’administrateur Microsoft 365 dans la fenêtre contextuelle.
    1. Lorsque vous y êtes invité, entrez le nom de l’application Azure AD, par exemple, les plug-ins Moodle ou Moodle.
    1. Lorsque vous y êtes invité, entrez l’URL de votre serveur Moodle.
    1. Lorsque vous y êtes invité, entrez l’URL de réponse copiée à partir de la page de configuration du plug-in d’authentification OpenID Connect. Il s’agit essentiellement de l’URL de votre site Moodle, suivie de `\auth\oidc\`.
    1. Vous pouvez être invité à vous reconnecter à votre compte Microsoft 365 dans une fenêtre contextuelle du processus. Il s’agit de fournir un consentement administrateur aux autorisations ajoutées à l’application pour votre organisation.
    1. Une fois l’exécution du script terminée, copiez **l’ID d’application (`AppID`)** et la **clé d’application(`Key`)** générés par le script et enregistrez-les.

### <a name="set-azure-app-details-in-moodle"></a>Définir les détails de l’application Azure dans Moodle

1. Revenez à la page de configuration du plug-in d’authentification OpenID Connect.
1. Collez la `AppID` valeur dans la zone **ID d’application** et la `Key` valeur dans la zone **Clé** , puis **sélectionnez Enregistrer les modifications**.

### <a name="configure-connection-between-microsoft-plugins-and-microsoft-services"></a>Configurer la connexion entre les plug-ins Microsoft et les services Microsoft

1. Dans la page de configuration de l’intégration de Microsoft 365, sélectionnez l’onglet **Configuration** .
1. Dans **Choisir la méthode de connexion**, sélectionnez **Accès à l’application**, puis **sélectionnez Enregistrer à nouveau les modifications** .
1. Une fois la page actualisée, vous pouvez voir une autre nouvelle section **Administration consentement & des informations supplémentaires**.
    1. Sélectionnez **Fournir Administration lien De consentement**, entrez vos informations d’identification d’administrateur général Microsoft 365, puis **Acceptez** d’accorder les autorisations.
    1. En regard du champ **Locataire Azure AD** , sélectionnez le bouton **Détecter** .
    1. En regard de **l’URL OneDrive Entreprise**, sélectionnez le bouton **Détecter**.
    1. Une fois les champs renseignés, sélectionnez à nouveau le bouton **Enregistrer les modifications** .
1. Sélectionnez le bouton **Mettre à jour** pour vérifier l’installation. Si aucune erreur n’est signalée à ce stade, cela signifie que les plug-ins Microsoft peuvent communiquer avec le serveur Microsoft via les API Microsoft Graph.

### <a name="configure-user-and-course-synchronization"></a>Configurer la synchronisation des utilisateurs et des cours

1. Synchronisez les utilisateurs entre votre serveur Moodle et Azure AD. En fonction de votre environnement, vous pouvez sélectionner différentes options au cours de cette étape. Pour commencer :
    1. Dans la page de configuration de Microsoft 365 Integration, sélectionnez l’onglet **Paramètres de synchronisation** .

    1. Dans le paramètre **Synchroniser les utilisateurs avec Azure AD** , cochez les cases qui s’appliquent à votre environnement. Vous devez sélectionner les options suivantes :  
        ✔ Créez des comptes dans Moodle pour les utilisateurs dans Azure AD.
       ✔ Mettez à jour tous les comptes dans Moodle pour les utilisateurs dans Azure AD.

    1. Dans la section **Restriction de création** d’utilisateurs, vous pouvez configurer un filtre pour limiter les utilisateurs Azure AD synchronisés avec Moodle.

    > [!NOTE]
    > Il n’est pas nécessaire d’activer la synchronisation utilisateur ; toutefois, cela facilitera considérablement la connexion des utilisateurs Moodle avec les comptes Microsoft 365.
    >
    > La synchronisation utilisateur est effectuée en exécutant les **utilisateurs de synchronisation avec la tâche planifiée Azure AD** .

1. Dans la section **Synchronisation des cours** , vous pouvez sélectionner l’option de **personnalisation de synchronisation** de cours pour activer la création automatique de Teams pour certains ou tous vos cours Moodle existants.

    > [!NOTE]
    > La synchronisation des cours est effectuée en exécutant les **cours Sync Moodle sur la tâche planifiée de Microsoft Teams** .

1. Enregistrez les modifications.

1. Pour valider la configuration de synchronisation, vous devez exécuter les tâches planifiées manuellement pour la première fois, puis accéder aux **tâches planifiées** >  du **serveur** >  **d’administration** >  de site.

    1. Faites défiler vers le bas et recherchez les **utilisateurs de synchronisation de tâches avec Azure AD** , puis sélectionnez **Exécuter maintenant**.
        1. Cela synchronise les utilisateurs Azure AD avec votre site Moodle en fonction des options de synchronisation utilisateur.
    1. Ensuite, recherchez les **cours Sync Moodle sur la tâche Microsoft Teams** , puis sélectionnez **Exécuter maintenant**.
        1. Cette tâche crée des groupes pour tous les cours Moodle avec l’option de synchronisation activée, ainsi que Teams si un **propriétaire d’équipe** se trouve dans le cours.
        1. La tâche synchronisera également les utilisateurs Moodle inscrits au cours avec Teams en tant que propriétaires ou membres.
            1. Un **propriétaire** d’équipe est un utilisateur Moodle qui
                1. est connecté à un compte Microsoft 365, AND
                2. est inscrit au cours, AND
                3. a la `local/o365:teamowner` capacité dans le contexte du cours.
            1. De même, un **membre** de l’équipe est un utilisateur Moodle qui
                1. est connecté à un compte Microsoft 365, AND
                2. est inscrit au cours, AND
                3. a la `local/o365:teamember` capacité dans le contexte du cours.
            1. Le rôle *d’enseignant* par défaut a la `local/o365:teamowner` capacité, et le rôle *Étudiant* par défaut en a la `local/o365:teammember` capacité.

> [!NOTE]
> Les tâches planifiées sont déclenchées par [Moodle Cron](https://docs.moodle.org/400/en/Cron), qui doit être configuré pour s’exécuter fréquemment. Chaque tâche planifiée peut avoir une planification par défaut, qui peut être personnalisée.
>
> - La planification par défaut des **utilisateurs de synchronisation avec la tâche Azure AD** est toutes les minutes.
> - La planification par défaut des **cours De synchronisation moodle avec la tâche Microsoft Teams** est quotidienne à 1h00 dans le fuseau horaire par défaut du serveur Moodle.

Une fois les plug-ins installés et configurés, vous pouvez :

- [Déployez moodle Assistant Bot sur Azure](/microsoftteams/install-moodle-integration#step-3-deploy-the-moodle-assistant-bot-to-azure).
- [Ajoutez des onglets Moodle aux classes Teams](/microsoftteams/install-moodle-integration#step-4-deploy-your-microsoft-teams-app).
- [Ajoutez des classes et des réunions Teams au moodle LMS](teams-classes-meetings-with-moodle.md).

## <a name="extra-moodle-plugin-documentation"></a>Documentation du plug-in Moodle supplémentaire

Si vous souhaitez consulter les guides d’intégration microsoft 365 et les notes de publication de Moodle, consultez les ressources suivantes :

- [Documentation sur l’intégration de Microsoft 365 sur Moodle Docs](https://docs.moodle.org/400/en/Microsoft_365).
