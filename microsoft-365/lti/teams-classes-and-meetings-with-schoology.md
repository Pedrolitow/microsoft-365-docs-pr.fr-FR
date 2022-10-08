---
title: Intégrer des réunions Microsoft Teams à Schoology LMS
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: microsoft-365-business
ms.collection:
- M365-modern-desktop
- m365initiative-edu
ms.localizationpriority: medium
description: Créez et gérez des réunions Teams avec Microsoft Learning Tools Interoperability (LTI) pour Schoology LMS.
ms.openlocfilehash: 9a2aaf2780bfa79324b7292e0383e595cec2e0f1
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68471857"
---
# <a name="integrate-microsoft-teams-meetings-with-schoology-lms"></a>Intégrer des réunions Microsoft Teams à Schoology LMS

Ce guide fournit les étapes de l’administrateur informatique pour l’inscription de l’application Teams Meetings LTI sur Schoology.

Pour obtenir une vue d’ensemble de Microsoft LTI, consultez [Intégration des produits Microsoft à votre système de gestion de l’apprentissage (LMS).](index.md)

> [!NOTE]
> La personne qui effectue cette intégration doit être un administrateur de schoology. Toutefois, les utilisateurs de Schoology ayant accès au **Centre** d’applications Schoology peuvent également installer l’application LTI réunions Microsoft Teams.

## <a name="deploy-the-teams-meetings-lti-app-in-schoology"></a>Déployer l’application Teams Meetings LTI dans Schoology

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
