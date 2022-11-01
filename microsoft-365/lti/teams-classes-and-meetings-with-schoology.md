---
title: Intégrer des réunions Microsoft Teams à Schoology Learning
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
description: Créez et gérez des réunions Teams avec Microsoft Learning Tools Interoperability (LTI) pour PowerSchool Unified Classroom® Schoology Learning.
ms.openlocfilehash: 9fb0d513f3f6cc4148006abb01473d12210fbfbb
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68804595"
---
# <a name="integrate-microsoft-teams-meetings-with-schoology-learning"></a>Intégrer des réunions Microsoft Teams à Schoology Learning

Ce guide décrit les étapes de l’administrateur informatique pour l’inscription de l’application Teams Meetings LTI sur PowerSchool Unified Classroom® Schoology Learning.

Pour obtenir une vue d’ensemble de Microsoft LTI, consultez [Intégration de produits Microsoft à votre système de gestion de l’apprentissage (LMS).](index.md)

> [!NOTE]
> La personne qui effectue cette intégration doit être un administrateur de Schoology Learning. Toutefois, les utilisateurs de Schoology Learning ayant accès au **Centre d’application** Schoology Learning peuvent également installer l’application Microsoft Teams Meetings LTI.

## <a name="deploy-the-teams-meetings-lti-app-in-schoology-learning"></a>Déployer l’application Teams Meetings LTI dans Schoology Learning

1. Connectez-vous à votre instance Schoology Learning en tant qu’administrateur avec un accès pour installer et configurer des applications.
1. Accédez à l’application **Réunions Microsoft Teams** dans [**l’App Center**](https://app.schoology.com/apps) en ouvrant ce lien direct [Réunions Microsoft Teams sur Schoology Learning](https://app.schoology.com/apps/profile/6017478062).
1. Sélectionnez le bouton **Installer l’application LTI 1.3** pour commencer le processus d’installation.
1. Sélectionnez le bouton **J’accepte** .
1. Vous serez invité à savoir si cette application doit être installée pour l’ensemble de votre organisation, ou simplement pour vous. Sélectionnez **Ajouter à l’organisation**, et vous serez redirigé vers la page **Applications de l’organisation** pour terminer la configuration.
1. Dans la [**liste Applications d’organisation**](https://app.schoology.com/apps/school_apps), recherchez l’application **Réunions Microsoft Teams** et sélectionnez le bouton **Configurer** .
    1. Copiez **l’ID de déploiement** affecté à votre déploiement de l’application.
        1. Cet ID sera utilisé dans le processus de configuration de la **passerelle Microsoft LMS** .
1. Dans la [**liste Applications d’organisation**](https://app.schoology.com/apps/school_apps), recherchez l’application **Réunions Microsoft Teams** et sélectionnez le bouton **Installer/Supprimer** .
    1. Pour installer l’application pour tous les utilisateurs, cochez la case **Tous les utilisateurs** .
        1. Sélectionnez uniquement les rôles qui auront accès à Microsoft Teams dans votre organisation, comme les enseignants, les étudiants ou les administrateurs système.
    1. Pour installer l’application pour tous les cours, cochez la case **Tous les cours** .
        1. Ne cochez pas l’option **Administrateurs du cours uniquement** pour vous assurer que l’application est disponible pour tous les membres du cours.
    1. Pour installer l’application pour tous les groupes, cochez la case **Tous les groupes** .

> [!NOTE]
> Si vous choisissez de ne pas installer l’application pour tous les cours, *les administrateurs* de cours doivent installer l’application pour eux-mêmes :
>
> 1. Accédez à la [liste Applications d’organisation](https://app.schoology.com/apps/school_apps), sélectionnez le bouton **Installer/Supprimer** , puis choisissez les cours dans lesquels installer l’application.
> 1. Ils peuvent également sélectionner le lien **Installer votre ou vos applications** en bas du menu de navigation sur rail gauche du cours, puis sélectionner l’application **Réunions Microsoft Teams** à installer.
