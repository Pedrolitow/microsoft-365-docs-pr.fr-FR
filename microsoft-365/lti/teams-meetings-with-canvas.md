---
title: Utiliser des réunions Microsoft Teams avec Canvas
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: sovaish
audience: admin
ms.topic: article
ms.service: microsoft-365-business
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Intégrer des réunions Microsoft Teams à Canvas
ms.openlocfilehash: c26d094740d75156cef10ac703f116106614616c
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68210347"
---
# <a name="use-microsoft-teams-meetings-with-canvas"></a>Utiliser des réunions Microsoft Teams avec Canvas

Les réunions Microsoft Teams sont une application d’interopérabilité des outils d’apprentissage (LTI) qui permet aux enseignants et aux étudiants de naviguer facilement entre leur système de gestion de l’apprentissage (LMS) et Teams. Les utilisateurs peuvent accéder à leurs équipes de classe associées à leur cours directement à partir de leur LMS.

## <a name="prerequisites-before-deployment"></a>Prérequis avant le déploiement

> [!NOTE]
> L’interface LTI Teams Meetings actuelle prend uniquement en charge la synchronisation des utilisateurs canvas avec Microsoft Azure Active Directory (AAD) dans une étendue limitée.
>
> - Votre locataire doit disposer d’une licence Microsoft Éducation.
> - Un seul locataire Microsoft peut être utilisé pour le mappage des utilisateurs entre Canvas et Microsoft.
> - Si vous envisagez d’utiliser la fonctionnalité Microsoft Teams Sync de Canvas simultanément avec SDS (School Data Sync) de Microsoft, n’incluez pas les données de liste de classes et de classes dans votre synchronisation SDS. Vous pouvez continuer à utiliser SDS pour synchroniser toutes les autres données, notamment les utilisateurs, les organisations, les contacts parents et les données démographiques.
> - Vous pouvez utiliser l’interface LTI réunions Teams sans activer **la synchronisation des cours**. Toutefois, vous ne pourrez pas utiliser l’option **Ajouter une classe entière** . Vous pouvez taper ou copier et coller les adresses e-mail des participants, ou ajouter des canaux d’équipes existantes aux réunions.

## <a name="microsoft-office-365-admin"></a>Microsoft Office 365 Administration

Avant de gérer l’intégration de Microsoft Teams dans Instructure Canvas, il est important que l’application **Azure Microsoft-Teams-Sync-for-Canvas** de Canvas soit approuvée par l’administrateur Microsoft Office 365 de votre établissement dans votre locataire Microsoft Azure avant de terminer la configuration de l’administrateur Canvas.

1. Connectez-vous à Canvas.

2. Sélectionnez le lien **Administration** dans la navigation globale, puis sélectionnez votre compte.

3. Dans la navigation de l’administrateur, sélectionnez le lien **Paramètres** , puis l’onglet **Intégrations** .

   ![Canvas Teams Sync Mise à jour png.](https://user-images.githubusercontent.com/87142492/128552407-78cb28e9-47cf-4026-954d-12dc3553af6f.png)

4. Entrez le nom de votre locataire Microsoft, l’attribut de connexion, le suffixe de domaine et l’attribut de recherche AAD. Ces champs seront utilisés pour mettre en correspondance des utilisateurs dans Canvas avec des utilisateurs dans Microsoft Azure Active Directory.
   - L’attribut login est l’attribut utilisateur Canvas utilisé pour la correspondance.
   - Le champ Suffixe est facultatif et vous permet de spécifier un domaine lorsqu’il n’existe pas de mappage exact entre les attributs Canvas et les champs Microsoft AAD. Par exemple, si votre e-mail Canvas est « name@example.edu » alors que l’UPN dans Microsoft AAD est « name », vous pouvez faire correspondre les utilisateurs en entrant « example.edu » dans le champ de suffixe.
   - L’attribut recherche Active Directory est le champ côté Microsoft auquel les attributs Canvas sont mis en correspondance. Sélectionnez entre l’UPN, l’adresse e-mail principale ou l’alias de messagerie.

5. Sélectionnez **Mettre à jour les paramètres** une fois terminé.

6. Pour approuver l’accès à l’application **Azure Microsoft-Teams-Sync-for-Canvas** de Canvas, sélectionnez le lien **Accorder l’accès au locataire** . Vous êtes redirigé vers le point de terminaison de consentement de la plateforme d’identités Microsoft Administration.

   ![Autorisations.](media/permissions.png)

7. Sélectionnez **Accepter**.

   > [!NOTE]
   > La synchronisation est une fonctionnalité gérée par le partenaire LMS et utilisée pour synchroniser l’appartenance à un niveau de cours avec l’équipe Teams à l’aide des API Microsoft Graph. Il s’agit principalement d’une fonctionnalité activée par un enseignant au niveau du cours. Par la suite, tout changement d’appartenance effectué côté LMS pour l’ajout ou la suppression des membres est reflété à l’aide de la synchronisation implémentée par le partenaire LMS. Même avant que ce processus ne soit activé pour un enseignant, l’administrateur de l’institut d’éducation M365 permet à ses enseignants d’accéder à la synchronisation à l’aide du modal d’autorisation de synchronisation ci-dessous. Ces autorisations sont accordées au partenaire LMS pour permettre aux enseignants de synchroniser l’appartenance entre le cours LMS et les équipes de classe Teams.

8. Activez la synchronisation Microsoft Teams en activant le bouton bascule.

   ![synchronisation d’équipes.](media/teams-sync.png)

## <a name="canvas-admin"></a>Administration de canevas

Configurez l’intégration de Microsoft Teams LTI 1.3.

En tant que Administration canvas, vous devez ajouter l’application LTI de réunions Microsoft Teams dans votre environnement. Notez l’ID client LTI de l’application.

- Réunions Microsoft Teams - 170000000000703

1. Accéder **aux applications de paramètres** >  Administration.

2. Sélectionnez **+ Application** pour ajouter les applications LTI Teams.

   ![external-apps.](media/external-apps.png)

3. Sélectionnez **par ID client** pour le type de configuration.

   ![ajouter une application.](media/add-app.png)

4. Entrez l’ID client fourni, puis **sélectionnez Envoyer**.

   Vous remarquerez le nom de l’application LTI des réunions Microsoft Teams pour l’ID client pour confirmation.

5. Sélectionnez **Installer**.

   L’application LTI de réunions Microsoft Teams sera ajoutée à la liste des applications externes.

6. Activez l’application en accédant aux clés de développeur dans le compte d’administrateur Canvas, en sélectionnant hérité et en activant le bouton bascule « activé » pour les réunions Microsoft Teams.

## <a name="enable-for-canvas-courses"></a>Activer pour les cours de canevas

Pour pouvoir utiliser l’interface LTI dans un cours, un instructeur du cours Canvas doit activer la synchronisation des intégrations. Chaque cours doit être activé par un instructeur pour qu’un Teams correspondant soit créé ; il n’existe aucun mécanisme global pour la création de Teams. Ceci est conçu par précaution pour empêcher la création de Teams indésirables.

Reportez-vous à la [documentation](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) de vos formateurs pour activer l’intégration LTI pour chaque cours et terminer la configuration de l’intégration.
