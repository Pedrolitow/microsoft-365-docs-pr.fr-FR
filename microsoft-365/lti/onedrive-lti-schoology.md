---
title: Intégrer Microsoft OneDrive LTI à Schoology Learning
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
ms.collection:
- M365-modern-desktop
- m365initiative-edu
ms.localizationpriority: medium
description: Créez et classez des devoirs, créez et organisez du contenu de cours et collaborez sur des fichiers en temps réel avec la nouvelle application d’interopérabilité des outils d’apprentissage Microsoft OneDrive pour PowerSchool Unified Classroom® Schoology Learning.
ms.openlocfilehash: ab3c732127cc614d0540974591e8f2847fc0d26c
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68804705"
---
# <a name="integrate-microsoft-onedrive-lti-with-schoology-learning"></a>Intégrer Microsoft OneDrive LTI à Schoology Learning

Ce guide fournit aux administrateurs informatiques les étapes d’inscription de l’application OneDrive LTI pour PowerSchool Unified Classroom® Schoology Learning.

Pour obtenir une vue d’ensemble de Microsoft LTI, consultez [Intégration de produits Microsoft à votre système de gestion de l’apprentissage (LMS).](index.md)

La personne qui effectue cette intégration doit être un administrateur de Schoology Learning et un administrateur du locataire Microsoft 365.

## <a name="recommended-browser-settings"></a>Paramètres de navigateur recommandés

- Les cookies doivent être autorisés pour Microsoft OneDrive.
- Les fenêtres contextuelles ne doivent pas être bloquées pour Microsoft OneDrive.

> [!NOTE]
> Les cookies ne sont pas autorisés par défaut dans le mode incognito du navigateur Chrome et doivent être autorisés.
>
> Microsoft OneDrive LTI fonctionne en mode privé dans le navigateur Microsoft Edge. Vérifiez que vous n’avez pas bloqué les cookies (qui sont autorisés par défaut).

## <a name="register-a-new-microsoft-onedrive-lti-app-for-your-microsoft-365-tenant"></a>Inscrire une nouvelle application Microsoft OneDrive LTI pour votre client Microsoft 365

1. Connectez-vous au [portail d’inscription Microsoft OneDrive LTI](https://onedrivelti.microsoft.com/admin) à l’aide d’une Office 365 informations d’identification global Administration.
1. Sélectionnez le bouton **Consentement Administration** et acceptez les autorisations.
    1. Si cette étape n’est pas terminée avec succès, l’étape suivante vous donnera une erreur et vous ne pourrez peut-être pas effectuer cette étape pendant une heure une fois que vous avez obtenu l’erreur. Si le consentement échoue, vérifiez que vous êtes connecté en tant que global Administration et répétez cette étape.
1. Sélectionnez le bouton **Créer un locataire LTI** .
1. Dans la liste **Plateforme de consommateurs LTI** , sélectionnez **Schoology**.
1. Dans le champ **URL de base de schoology** , entrez l’URL de votre base d’apprentissage scolaire, par exemple `https://testschool.schoology.com`.
1. Sélectionnez le bouton **Suivant**. La page **Inscrire l’application LTI 1.3** se charge.

## <a name="deploy-the-onedrive-lti-app-in-schoology-learning"></a>Déployer l’application OneDrive LTI dans Schoology Learning

1. Connectez-vous à votre instance Schoology Learning en tant qu’administrateur avec un accès pour installer et configurer des applications.
1. Accédez à l’application **Microsoft OneDrive** dans le [**Centre**](https://app.schoology.com/apps) d’application en ouvrant ce lien direct [Microsoft OneDrive sur Schoology Learning](https://app.schoology.com/apps/profile/5910037138).
1. Sélectionnez le bouton **Installer l’application LTI 1.3** pour commencer le processus d’installation.
1. Sélectionnez le bouton **J’accepte** .
1. Vous serez invité à partager les informations requises avec l’application et à confirmer l’accès aux *services LTI Advantage*, tels que **la liaison approfondie**, **les noms et les rôles**, et **les affectations et la notation**. Sélectionnez le bouton **Continuer**.
1. Vous serez invité à savoir s’il doit être installé pour l’ensemble de votre organisation, ou simplement pour vous. Sélectionnez **Ajouter à l’organisation**, et vous serez redirigé vers la page **Applications de l’organisation** pour terminer la configuration.
1. Dans la [**liste Applications d’organisation**](https://app.schoology.com/apps/school_apps), recherchez l’application **Microsoft OneDrive** et sélectionnez le bouton **Configurer** .
    1. Copiez **l’ID de déploiement** affecté à votre déploiement de l’application.
        1. Cet ID sera utilisé dans le processus **de configuration de la passerelle Microsoft LMS** .
1. Dans la [**liste Applications d’organisation**](https://app.schoology.com/apps/school_apps), recherchez l’application **Microsoft OneDrive** et sélectionnez le bouton **Installer/Supprimer** .
    1. Pour installer l’application pour tous les cours, cochez la case **Tous les cours** .
        1. Ne cochez pas l’option **Administrateurs du cours uniquement** pour vous assurer que l’application est disponible pour tous les membres du cours.

> [!NOTE]
> Si vous choisissez de ne pas installer l’application pour tous les cours, *les administrateurs* de cours doivent installer l’application pour eux-mêmes :
>
> 1. Accédez à la [liste Applications d’organisation](https://app.schoology.com/apps/school_apps), sélectionnez le bouton **Installer/Supprimer** , puis choisissez les cours dans lesquels installer l’application.
> 1. Ils peuvent également sélectionner le lien **Installer votre ou vos applications** en bas du menu de navigation sur rail gauche du cours, puis sélectionner l’application **Microsoft OneDrive** à installer.
