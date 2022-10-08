---
title: Rendez votre personnel de première ligne opérationnel grâce à l’Assistant d’intégration
author: lanachin
ms.author: v-lanachin
ms.reviewer: aaglick
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez comment utiliser l’Assistant d’intégration du personnel de première ligne pour déployer rapidement une expérience Teams adaptée aux employés et gestionnaires de première ligne au sein de votre organisation.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
- highpri
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 9e9f12d13c5f6b7c1762857faa474cb831059bc4
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68066121"
---
# <a name="use-the-frontline-worker-onboarding-wizard-to-get-your-frontline-workforce-up-and-running"></a>Rendez votre personnel de première ligne opérationnel grâce à l’Assistant d’intégration

## <a name="overview"></a>Vue d’ensemble

L’Assistant d’intégration du personnel de première ligne dans le Centre d’administration Microsoft 365 simplifie l’intégration des employés de première ligne au sein de votre organisation. L’Assistant vous permet de déployer rapidement une expérience dans Microsoft Teams adaptée à votre personnel de première ligne. À l’aide de l’Assistant, vous pouvez lancer votre déploiement pilote de Teams en toute simplicité pour les employés de terrain dans votre organisation.

L’Assistant configure une équipe pour vos employés de première ligne et attribue des licences et [des packages de stratégie](/microsoftteams/policy-packages-flw?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json) à chaque membre de l’équipe. Vous pouvez créer votre équipe à partir de zéro ou à partir d’un [modèle d’équipe](/microsoftteams/get-started-with-teams-templates-in-the-admin-console), puis ajouter des utilisateurs et attribuer des rôles. Le rôle détermine le package de stratégie que l’Assistant attribue à chaque utilisateur.

Actuellement, l’Assistant prend en charge l’ajout de 100 utilisateurs à chaque exécution. Nous travaillons sur l’augmentation prochaine du nombre d’utilisateurs par exécution. Revenez ici pour obtenir les dernières mises à jour.

L’Assistant est disponible pour toutes les organisations qui disposent au moins d’une [licence F](https://www.microsoft.com/microsoft-365/enterprise/frontline). Vous pouvez exécuter l’Assistant autant de fois que nécessaire pour déployer Teams auprès de votre personnel de première ligne dans différents emplacements ou sites au sein de votre organisation.

Regardez cette courte vidéo pour obtenir une vue d’ensemble de l’exécution de l’Assistant afin intégrer votre personnel de première ligne.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWN6oh]

> [!NOTE]
> L’Assistant ne prend pas encore en charge [les étiquettes de confidentialité](/microsoftteams/sensitivity-labels) . Si votre organisation a besoin d’étiquettes de confidentialité pour créer une équipe, l’Assistant ne s’affichera pas dans le Centre d’administration Microsoft 365.

## <a name="run-the-wizard"></a>Lancer l’Assistant

1. Dans le volet de navigation gauche du [Centre d’administration Office 365](https://admin.microsoft.com/), sélectionnez **Configuration**. Accédez à la section **Applications et e-mail** , puis sous **Rendez votre personnel de première ligne opérationnel**, sélectionnez **Affichage**. Dans cette section, vous pouvez en savoir plus sur les fonctionnalités offertes par Microsoft 365 pour le personnel de première ligne.

    :::image type="content" source="media/flw-onboarding-wizard-get-started.png" alt-text="Capture d’écran de la page d’informations sur l’expérience d’intégration du personnel de première ligne dans le Centre d’administration Microsoft 365" lightbox="media/flw-onboarding-wizard-get-started.png":::

2. Lorsque vous êtes prêt, sélectionnez **Prise en main** pour exécuter l’Assistant.

3. Saisissez un nom pour votre équipe, ajoutez un ou plusieurs propriétaires d’équipe, puis sélectionnez un paramètre de confidentialité. Ensuite, choisissez de créer votre équipe à partir de zéro ou à partir d’un modèle d’équipe. Les modèles d’équipe incluent des canaux et des onglets prédéfinis qui optimisent l’organisation de l’équipe pour un projet ou un besoin métier particulier.

    :::image type="content" source="media/flw-onboarding-wizard-set-up-team.png" alt-text="Capture d’écran de la page Configurer une équipe de l’Assistant" lightbox="media/flw-onboarding-wizard-set-up-team.png":::

4. Ajoutez des utilisateurs à l’équipe. Vous pouvez également ajouter des groupes. Si vous ajoutez des groupes, gardez à l’esprit que les licences et les packages de stratégie sont directement attribués à chaque utilisateur du groupe, et non au groupe lui-même.

    :::image type="content" source="media/flw-onboarding-wizard-add-users.png" alt-text="Capture d’écran de la page Ajouter des utilisateurs de l’Assistant, où vous ajoutez des utilisateurs et des groupes à votre équipe" lightbox="media/flw-onboarding-wizard-add-users.png":::

5. Attribuez l’un des rôles suivants à chaque membre de l’équipe employé de première ligne: Employé de première ligne, Responsable de première ligne, Aucun. 
  
    :::image type="content" source="media/flw-onboarding-wizard-assign-roles.png" alt-text="Capture d’écran de la page Attribuer des rôles de travail de l’Assistant où vous attribuez des rôles, des lieux et des licences aux membres de l’équipe" lightbox="media/flw-onboarding-wizard-assign-roles.png":::

    Si vous attribuez un rôle Employé de première ligne ou Responsable de première ligne, l’utilisateur reçoit alors un package de stratégie. Le package de stratégie personnalise son expérience dans Teams en fonction de son rôle. Cette expérience inclut des applications et des stratégies pré-épinglées pour améliorer la communication et la collaboration professionnelles entre les employés et les responsables de première ligne.

    Ensuite, sélectionnez un emplacement et attribuez une licence Microsoft 365 F à chaque membre de l’équipe. Si vous n’avez pas suffisamment de licences, vous pouvez sélectionner **Acheter d’autres licences** pour en acquérir de nouvelles.  

6. Choisissez le destinataire de l’e-mail d’état une fois que les étapes de l’Assistant sont terminées. L’e-mail contient des informations sur la réussite ou l’échec du processus de l’Assistant&mdash; lors de la création de l’équipe, de l’ajout de membres de l’équipe et de l’attribution d’une licence et d’un package de stratégie à chaque membre de l’équipe. Utilisez ces informations pour résoudre les erreurs potentielles.

    :::image type="content" source="media/flw-onboarding-wizard-email-recipients.png" alt-text="Capture d’écran de la page Ajouter des destinataires à l’e-mail d’état de l’Assistant" lightbox="media/flw-onboarding-wizard-email-recipients.png":::

7. Vérifiez votre sélection et cliquez sur **Confirmer**.

    :::image type="content" source="media/flw-onboarding-wizard-review-team.png" alt-text="Capture d’écran de la page Examiner l’équipe de l’Assistant afin de passer en revue les paramètres de votre équipe" lightbox="media/flw-onboarding-wizard-review-team.png":::

    L’Assistant crée votre équipe et attribue des licences et des packages de stratégie aux membres de l’équipe. L’exécution peut prendre quelques minutes, après quoi les destinataires que vous avez choisis reçoivent un e-mail d’état.

8. Vous êtes sur la bonne voie, mais vous n’avez pas encore terminé ! Ensuite, consultez la section [Procédure à suivre après avoir exécuté l’Assistant](#what-to-do-after-running-the-wizard) dans cet article.

## <a name="what-to-do-after-running-the-wizard"></a>Procédure à suivre après l’exécution de l’Assistant

Après avoir exécuté l’Assistant, il est important de réaliser les actions suivantes.

- Informez vos employés et responsables de première ligne qu’ils se voient attribuer des licences Teams.
- Si votre organisation utilise des appareils partagés, assurez-vous que Teams est installé sur ces appareils. Les utilisateurs que vous avez ajoutés à l’équipe recevront un e-mail de bienvenue qui les invite à ouvrir Teams.
- Si votre organisation utilise un modèle BYOD (Apportez votre propre appareil), informez chaque utilisateur que vous avez ajouté à l’équipe qu’il doit télécharger et installer Teams sur ses appareils. Ils recevront également un e-mail de bienvenue qui les invite à télécharger Teams.

    > [!NOTE]
    > N’oubliez pas que les utilisateurs disposant de licences F1 ne recevront pas d’e-mail de bienvenue, car la licence F1 n’inclut pas l’accès aux e-mails.  

Lorsque l’employé de première ligne ouvre Teams pour la première fois, il bénéficie d’une expérience personnalisée dès la première exécution, qui inclut les conversations et les canaux, les appels et la gestion des tâches dans Teams.

## <a name="related-articles"></a>Articles connexes

- [Packages de stratégie Team pour les responsables et les travailleurs de première ligne](/microsoftteams/policy-packages-flw?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Gérer les packages de stratégie dans Teams](/microsoftteams/manage-policy-packages)
- [Utiliser les modèles d’équipe dans le Centre d’administration Teams](/microsoftteams/get-started-with-teams-templates-in-the-admin-console)
