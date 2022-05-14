---
title: Configurer et configurer le plug-in Moodle
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
description: Préparez-vous à intégrer Moodle et Microsoft Teams en configurant et en configurant le plug-in Moodle.
ms.openlocfilehash: c6c022ee2f567dc917a0be164daf4f39a74996b1
ms.sourcegitcommit: 4e7ff69f4d7d27c2d419f763cfcb069e3b0d0d9f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2022
ms.locfileid: "65403209"
---
# <a name="set-up-and-configure-the-moodle-plugin"></a>Configurer et configurer le plug-in Moodle

Dans cet article, vous allez apprendre à installer et à configurer le plug-in Moodle LMS pour incorporer Microsoft Teams à votre expérience Moodle.

> [!NOTE]
> Actuellement, les intégrations Moodle et Microsoft Teams LTI sont disponibles uniquement en préversion privée.
>
>Si vous souhaitez participer au programme de préversion privée, [inscrivez-vous ici](https://m365crmedu.powerappsportals.com/LMSSignup)

## <a name="prerequisites"></a>Conditions préalables

Voici les conditions préalables à l’installation de Moodle :

* Informations d’identification de l’administrateur Moodle.
* Informations d’identification de l’administrateur Azure AD.
* Un abonnement Azure dans lequel vous pouvez créer des ressources.

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Installer les plug-ins moodle Microsoft 365

L’intégration moodle dans Microsoft Teams est optimisée par le jeu de [plug-ins moodle Microsoft 365 open source](https://moodle.org/plugins/browse.php?list=set&id=72).

### <a name="requisite-applications-and-plugins"></a>Applications et plug-ins requis

Installez et téléchargez les éléments suivants avant de poursuivre l’installation des plug-ins moodle Microsoft 365 :

1. Version [stable actuelle de Moodle](https://download.moodle.org/releases/latest/).
1. Téléchargez et enregistrez le [Connecter Moodle OpenID](https://moodle.org/plugins/auth_oidc) et les [plug-ins d’intégration Microsoft 365](https://moodle.org/plugins/local_o365) sur votre ordinateur local.

    > [!NOTE]
    > L’installation des plug-ins d’intégration OpenID Connecter et Microsoft 365 est requise pour l’intégration Teams.
    >
    > Le [plug-in thème Microsoft 365 Teams](https://moodle.org/plugins/theme_boost_o365teams) est recommandé.

### <a name="microsoft-365-moodle-plugins"></a>plug-ins Microsoft 365 Moodle

#### <a name="install-plugins"></a>Installer des plug-ins

1. Téléchargez les plug-ins, extrayez-les et chargez-les dans leurs dossiers correspondants. Par exemple, extrayez le plug-in OpenID Connecter (auth_oidc) dans un dossier appelé **oidc**, puis chargez-le dans le dossier **d’authentification** de la racine de votre document Moodle.
2. Connectez-vous à votre site Moodle en tant qu’administrateur et sélectionnez **Administration du site**.
3. Lors de la détection de nouveaux plug-ins à installer, Moodle doit vous rediriger vers la page installer les nouveaux plug-ins. Si cela ne se produit pas, dans la page **Administration du site** , sélectionnez **Notifications** sous l’onglet **Général** , ce qui doit déclencher l’installation des plug-ins.

    > [!IMPORTANT]
    >
    > * Laissez votre Microsoft 365 page de configuration des plug-ins Moodle ouverte dans un onglet de navigateur distinct, car vous devez revenir à cet ensemble de pages tout au long du processus.  
    >
    > * Si vous n’avez pas de site Moodle existant, accédez au référentiel [Moodle sur Azure](https://github.com/azure/moodle) , déployez rapidement une instance Moodle et personnalisez-la en fonction de vos besoins.

#### <a name="enable-the-openid-connect-authentication-plugin"></a>Activer le plug-in d’authentification OpenID Connecter

1. Accédez à **Site** **AdministrationPluginsAuthentication** >  > , puis **sélectionnez Gérer l’authentification**.
1. Recherchez le **plug-in d’authentification OpenID Connecter** et sélectionnez l’icône *d’œil* pour l’activer.
1. Sélectionnez **Paramètres** pour le plug-in afin de vérifier les points de terminaison **d’autorisation** et de **jeton**.
    1. Les valeurs par défaut doivent être les suivantes :
        1. Point de terminaison d’autorisation : ``https://login.microsoftonline.com/common/oauth2/authorize``.
        1. Point de terminaison de jeton : ``https://login.microsoftonline.com/common/oauth2/token``.
1. Enregistrez **l’URI de redirection** pour une utilisation ultérieure.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-ad"></a>2. Configurer la connexion entre les plug-ins Microsoft 365 et Azure AD

Vous devez configurer la connexion entre les plug-ins Microsoft 365 et Azure AD.

### <a name="requisites"></a>Accessoires

Inscrivez Moodle en tant qu’application dans Azure AD à l’aide du script PowerShell. Le script provisionne les éléments suivants :

* Nouvelle application Azure AD pour votre locataire Microsoft 365, qui est utilisée par les plug-ins moodle Microsoft 365.
* L’application de votre locataire Microsoft 365 configure les URL de réponse et les autorisations requises pour l’application approvisionnée et retourne le `AppID` et `Key`.

Utilisez la page de configuration des plug-ins Moodle générée `AppID` et `Key` dans votre Microsoft 365 pour configurer votre site serveur Moodle avec Azure AD.

> [!IMPORTANT]
> * Pour plus d’informations sur l’inscription manuelle de votre instance Moodle, consultez [Inscrire votre instance Moodle en tant qu’application](https://docs.moodle.org/400/en/Microsoft_365#Azure_App_Creation_and_Configuration).

### <a name="the-teams-for-moodle-set-up-process"></a>Processus de configuration Teams pour Moodle

1. Dans la page des plug-ins d’intégration Microsoft 365, sélectionnez l’onglet **Configuration**.

1. Sélectionnez le bouton **Télécharger le script PowerShell** et enregistrez-le sous forme de dossier ZIP sur votre ordinateur local.

1. Préparez le script PowerShell à partir du fichier ZIP comme suit :

    1. Téléchargez et extrayez le `Moodle-AzureAD-Powershell.zip` fichier.
    1. Ouvrez le dossier extrait.
    1. Cliquez avec le bouton droit sur le `Moodle-AzureAD-Script.ps1` fichier et sélectionnez **Propriétés**.
    1. Sous l’onglet **Général** de l’Fenêtre Propriétés, cochez la `Unblock` case en regard de l’attribut **Sécurité** situé en bas de la fenêtre.
    1. Sélectionnez **OK**.
    1. Copiez le chemin d’accès au répertoire dans le dossier extrait.

1. Exécutez PowerShell en tant qu’administrateur :

    1. Sélectionnez Démarrer.
    1. Tapez PowerShell.
    1. Cliquez avec le bouton droit sur **Windows PowerShell**.
    1. Sélectionnez **Exécuter en tant qu’administrateur**.

1. Accédez au répertoire décompressé en tapant `cd .../.../Moodle-AzureAD-Powershell` où `.../...` se trouve le chemin d’accès au répertoire.

1. Exécutez le script PowerShell :

    1. Entrez `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.
    1. Entrez `./Moodle-AzureAD-Script.ps1`.
    1. Connectez-vous à votre compte d’administrateur Microsoft 365 dans la fenêtre contextuelle.
    1. Entrez le nom de l’application Azure AD, par exemple, les plug-ins Moodle ou Moodle.
    1. Entrez l’URL de votre serveur Moodle.
    1. Copiez **l’ID d’application (`AppID`)** et la **clé d’application(`Key`)** générés par le script et enregistrez-les.

1. Revenez à la page d’administration des plug-ins, **Site** **administrationPluginsAuthenticationOpenID** >  >  >  **Connecter**.

1. Collez la `AppID` valeur dans la zone **ID d’application** et la `Key` valeur dans la zone **Clé** , puis **sélectionnez Enregistrer les modifications**.

1. Accédez aux **plug-ins** **Site** **administrationPluginsLocal** >  >  et sélectionnez **Microsoft 365 Integration**.

1. Dans **Choisir la méthode de connexion**, sélectionnez **Accès à l’application**, puis **sélectionnez Enregistrer à nouveau les modifications** .

1. Une fois la page actualisée, vous pouvez voir un autre **nouveau consentement de l’administrateur de section & des informations supplémentaires**.
    1. Sélectionnez **Le lien Fournir le consentement de l’administrateur**, entrez vos informations d’identification d’administrateur général Microsoft 365, puis **acceptez** d’accorder les autorisations.
    1. En regard du champ **Locataire Azure AD** , sélectionnez le bouton **Détecter** .
    1. En regard de **l’URL OneDrive Entreprise**, sélectionnez le bouton **Détecter**.
    1. Une fois les champs renseignés, sélectionnez à nouveau le bouton **Enregistrer les modifications** .

1. Sélectionnez le bouton **Mettre à jour** pour vérifier l’installation, puis **sélectionnez Enregistrer les modifications**.

1. Synchronisez les utilisateurs entre votre serveur Moodle et Azure AD. En fonction de votre environnement, vous pouvez sélectionner différentes options au cours de cette étape. Pour commencer :
    1. Basculez vers **l’onglet Synchroniser Paramètres**.

    1. Dans la section **Synchroniser les utilisateurs avec Azure AD** , cochez les cases qui s’appliquent à votre environnement. Vous devez sélectionner les options suivantes :  

        ✔ Créez des comptes dans Moodle pour les utilisateurs dans Azure AD.
        
        ✔ Mettez à jour tous les comptes dans Moodle pour les utilisateurs dans Azure AD.
        

    1. Dans la section **Restriction de création** d’utilisateurs, vous pouvez configurer un filtre pour limiter les utilisateurs Azure AD synchronisés avec Moodle.
    1. Dans la section **Synchronisation des cours**, vous pouvez sélectionner l’option de **personnalisation de synchronisation de cours** pour activer la création automatique de groupes et de Teams pour une partie ou la totalité de vos cours Moodle existants.

1. Pour valider les tâches [cron](https://docs.moodle.org/400/en/Cron) et les exécuter manuellement pour la première fois, accédez aux tâches **d’administration** >  **de** siteServerTasksScheduled >  > .

    1. Faites défiler vers le bas et recherchez les **utilisateurs de synchronisation de tâches avec Azure AD** , puis sélectionnez **Exécuter maintenant**.
        1. Cela synchronise l’utilisateur AAD avec votre site Moodle.
    1. Ensuite, recherchez les **cours Sync Moodle pour Microsoft Teams** tâche, puis sélectionnez **Exécuter maintenant**.
        1. Cette tâche crée des groupes et des Teams si un propriétaire est trouvé.
        1. Si l’utilisateur dispose `local/o365:teamowner` d’une fonctionnalité dans le contexte du cours, il est propriétaire de l’équipe. Si l’utilisateur dispose `local/o365:teammember` d’une fonctionnalité dans le contexte du cours, il est membre de l’équipe.  
        1. Le rôle *d’enseignant* par défaut a la `local/o365:teamowner" capability`fonctionnalité , et le rôle *Étudiant* par défaut en a la `local/o365:teammember` capacité.

    > [!NOTE]
    >
    > Moodle [Cron](https://docs.moodle.org/400/en/Scheduled_tasks) s’exécute selon la planification des tâches. La planification par défaut est une fois par jour à 1h00 dans le fuseau horaire local de votre serveur. Toutefois, le cron doit s’exécuter plus fréquemment pour que tout reste synchronisé.

1. Accédez à **l’onglet Administration** >  **du sitePluginsLocal** >  >  **Microsoft 365'intégration** >  **Teams Paramètres**.

1. Cliquez sur le bouton **Vérifier les paramètres moodle** pour mettre à jour toutes les configurations requises pour que l’intégration Teams fonctionne.
        

Une fois les plug-ins installés et configurés, vous pouvez :

* [Déployez moodle Assistant Bot sur Azure](/microsoftteams/install-moodle-integration#step-3-deploy-the-moodle-assistant-bot-to-azure).
* [Ajoutez des onglets Moodle à Teams classes](/microsoftteams/install-moodle-integration#step-4-deploy-your-microsoft-teams-app).
* [Ajoutez Teams classes et réunions au moodle LMS](teams-classes-meetings-with-moodle.md).

## <a name="extra-moodle-plugin-documentation"></a>Documentation du plug-in Moodle supplémentaire

Si vous souhaitez consulter les guides d’intégration Microsoft 365 moodle et les notes de publication, consultez les ressources suivantes :

* [Microsoft 365 documentation d’intégration sur Moodle Docs](https://docs.moodle.org/400/en/Microsoft_365).
