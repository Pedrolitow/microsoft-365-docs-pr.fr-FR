---
title: Intégrer des réunions Microsoft Teams à Schoology LMS
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
description: Créez et gérez des réunions Teams avec Microsoft Learning Tools Interoperability (LTI) pour Schoology LMS.
ms.openlocfilehash: 41f389e7a936f91928ea084dddb9688f8703c7bf
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67694440"
---
# <a name="integrate-microsoft-teams-meetings-with-schoology-lms"></a>Intégrer des réunions Microsoft Teams à Schoology LMS

Ce guide fournit les étapes de l’administrateur informatique pour l’inscription de l’application Teams Meetings LTI sur Schoology.

Pour obtenir une vue d’ensemble de Microsoft LTI, consultez [Intégration des produits Microsoft à votre système de gestion de l’apprentissage (LMS).](index.md)

> [!NOTE]
> La personne qui effectue cette intégration doit être un administrateur de schoology. Toutefois, les utilisateurs de Schoology ayant accès au **Centre** d’applications Schoology peuvent également installer l’application LTI réunions Microsoft Teams.

## <a name="register-the-teams-meetings-lti-app-for-schoology"></a>Inscrire l’application Teams Meetings LTI pour schoology

1. Connectez-vous à votre instance Schoology en tant qu’administrateur avec accès pour installer et configurer des applications.
1. Accédez à l’application **Réunions Microsoft Teams** dans [**l’App Center**](https://app.schoology.com/apps) en ouvrant ce lien direct [réunions Microsoft Teams sur la schoology](https://app.schoology.com/apps/profile/6017478062).
1. Sélectionnez le bouton **Installer l’application LTI 1.3** pour commencer le processus d’installation.
1. Sélectionnez le bouton **J’accepte** .
1. Vous serez invité à indiquer si cette application doit être installée pour l’ensemble de votre organisation ou uniquement pour vous. Sélectionnez **Ajouter à l’organisation** et vous êtes redirigé vers la page **Applications d’organisation** pour terminer la configuration.
1. Dans la [**liste Des applications d’organisation**](https://app.schoology.com/apps/school_apps), recherchez l’application **Réunions Microsoft Teams** et sélectionnez le bouton **Configurer** .
    1. Copiez **l’ID de déploiement** affecté à votre déploiement de l’application.
        1. Cet ID sera utilisé dans le processus de configuration de la **passerelle Microsoft LMS** .
1. Dans la [**liste Des applications**](https://app.schoology.com/apps/school_apps) d’organisation, recherchez l’application **Réunions Microsoft Teams** et **sélectionnez le bouton Installer/Supprimer** .
    1. Pour installer l’application pour tous les utilisateurs, cochez la case **Tous les utilisateurs** .
        1. Sélectionnez uniquement les rôles qui auront accès à Microsoft Teams dans votre organisation, tels que les enseignants, les étudiants ou les administrateurs système.
    1. Pour installer l’application pour tous les cours, cochez la case **Tous les cours** .
        1. Ne cochez pas l’option **Administrateurs** de cours uniquement pour vous assurer que l’application est disponible pour tous les membres du cours.
    1. Pour installer l’application pour tous les groupes, cochez la case **Tous les groupes** .

> [!NOTE]
> Si vous choisissez de ne pas installer l’application pour tous les cours, les *administrateurs de cours* doivent installer l’application pour eux-mêmes :
>
> 1. Accédez à la [liste Des applications](https://app.schoology.com/apps/school_apps) d’organisation, **sélectionnez le bouton Installer/Supprimer** et choisissez les cours dans lesquels installer l’application.
> 1. Ils peuvent également sélectionner le lien **Installer votre ou vos applications** en bas du menu de navigation sur rail gauche du cours, puis sélectionner l’application **Réunions Microsoft Teams** à installer.

## <a name="configure-the-teams-meetings-lti-app-to-work-with-schoology"></a>Configurer l’application Teams Meetings LTI pour qu’elle fonctionne avec Schoology

1. Visitez [la passerelle Microsoft LMS](https://lti.microsoft.com/) et **sélectionnez le bouton Accéder au portail d’inscription** .
1. Connectez-vous avec un compte d’administrateur Microsoft 365.
1. Sélectionnez le bouton **Administration Consentement** et acceptez les autorisations.
    1. Si cette étape n’est pas effectuée, l’étape suivante vous donnera une erreur, et vous ne pourrez pas effectuer cette étape pendant une heure une fois que vous avez reçu l’erreur.
1. Sélectionnez le bouton **Créer un locataire LTI** .
1. Dans la page Inscription LTI, choisissez **Schoology** dans la liste déroulante LTI Consumer Platform, puis sélectionnez le bouton **Suivant** .
1. Collez **l’ID de déploiement** que vous avez copié lors de l’inscription de l’outil dans Schoology, puis sélectionnez **Suivant**.
1. Passez en revue et enregistrez vos modifications. Un message s’affiche lors de l’inscription réussie.
1. Vous pouvez également consulter les détails de votre inscription en sélectionnant le bouton **Afficher les locataires LTI** sur la page d’accueil.

Une fois ces étapes effectuées, vos enseignants pourront utiliser l’application LTI Réunions Teams.
