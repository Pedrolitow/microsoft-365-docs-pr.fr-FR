---
title: Utiliser Microsoft Teams réunions avec Canvas
ms.author: v-cichur
author: cichur
manager: serdars
ms.reviewer: sovaish
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Intégrer Microsoft Teams réunions avec Canvas
ms.openlocfilehash: 2bd004c86a7d6d2ee5a671d30d98e0af71990a81
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60152489"
---
# <a name="use-microsoft-teams-meetings-with-canvas"></a>Utiliser Microsoft Teams réunions avec Canvas

Microsoft Teams réunions est une application Learning Tools Interoperability (LTI) qui permet aux enseignants et aux étudiants de naviguer facilement entre leur système de gestion Learning (LMS) et leur Teams. Les utilisateurs peuvent accéder à leurs équipes de cours associées à leur cours directement à partir de leur LMS.

## <a name="prerequisites-before-deployment"></a>Conditions préalables avant le déploiement

> [!NOTE]
> L’Teams meetings LTI prend uniquement en charge la synchronisation des utilisateurs canvas avec Microsoft Azure Active Directory (AAD) dans une étendue limitée. 
> - Votre client doit avoir une licence Microsoft Éducation.
> - Un seul client Microsoft peut être utilisé pour le mappage d’utilisateurs entre Canvas et Microsoft.
> - Vous devez désactiver le Synchronisation des données scolaires (SDS) avant d’utiliser l’Teams LTI de classe afin d’éviter la duplication des groupes.

## <a name="microsoft-office-365-admin"></a>Microsoft Office 365 Administrateur

Avant de gérer l’intégration Microsoft Teams dans Instructure Canvas, il est important que l’application **Microsoft-Teams-Sync-for-Canvas** Azure de Canvas soit approuvée par l’administrateur Microsoft Office 365 de votre établissement dans votre client Microsoft Azure avant de terminer la configuration de l’administrateur canvas.

1. Connectez-vous à Canvas.

2. Sélectionnez **le lien** Administrateur dans la navigation globale, puis sélectionnez votre compte.

3. Dans la navigation de l’administrateur, sélectionnez **Paramètres** lien, puis l’onglet **Intégrations.**

![Canvas Teams Sync Updated png.](https://user-images.githubusercontent.com/87142492/128552407-78cb28e9-47cf-4026-954d-12dc3553af6f.png)

4. Entrez le nom de votre client Microsoft, l’attribut de connexion, le suffixe de domaine et l’attribut de recherche AAD. Ces champs seront utilisés pour faire correspondre les utilisateurs de Canvas aux utilisateurs Microsoft Azure Active Directory. 
   * L’attribut de connexion est l’attribut utilisateur Canvas utilisé pour la correspondance.
   * Le champ Suffix est facultatif et vous permet de spécifier un domaine lorsqu’il n’existe pas de mappage exact entre les attributs canvas et les champs Microsoft AAD. Par exemple, si votre e-mail Canvas est « name@example.edu » alors que l’UPN dans Microsoft AAD est « nom » , vous pouvez faire correspondre les utilisateurs en entrant « example.edu » dans le champ de suffixe.
   * L’attribut de recherche Active Directory est le champ côté Microsoft auquel les attributs Canvas sont en correspondance. Sélectionnez l’UPN, l’adresse de messagerie principale ou l’alias de messagerie.

5. Sélectionnez **Mettre à jour Paramètres** une fois terminé.

6. Pour approuver l’accès à l’application **Azure Microsoft-Teams-Sync-for-Canvas de Canvas,** sélectionnez le lien Accorder l’accès **client.** Vous serez redirigé vers le point de terminaison de consentement de l’administrateur de la plateforme d’identités Microsoft.

   ![autorisations.](media/permissions.png)

7. Sélectionnez **Accepter**. 

> [!NOTE]
> La synchronisation est une fonctionnalité gérée par un partenaire LMS et utilisée pour synchroniser l’appartenance au niveau d’un cours avec l’équipe Teams à l’aide des API Microsoft Graph. Il s’agit principalement d’une fonctionnalité qu’un enseignant bascule comme vrai au niveau d’un cours. Par la suite, toute modification d’appartenance effectuée côté LMS pour l’ajout ou la suppression des membres est reflétée à l’aide de la synchronisation implémentée par le partenaire LMS. Avant même que ce processus ne soit activé pour un enseignant, l’administrateur de l’établissement d’enseignement M365 permet à ses enseignants d’accéder à la synchronisation à l’aide de la modale d’autorisation de synchronisation ci-dessous. Ces autorisations sont accordées au partenaire LMS pour permettre aux enseignants de synchroniser l’appartenance entre le cours LMS et les équipes Teams classe.

8. Activez la synchronisation Microsoft Teams l’utilisateur en activé le basculement.

   ![synchronisation des équipes.](media/teams-sync.png)

## <a name="canvas-admin"></a>Administrateur de zone de dessin

Configurer l’Microsoft Teams’intégration LTI 1.3.

En tant qu’administrateur de zone de dessin, vous devez ajouter l’application LTI Microsoft Teams réunions au sein de votre environnement. Notez l’ID client LTI de l’application.

 - Microsoft Teams réunions - 170000000000703

1. Access **Admin settings**  >  **Apps**.

2. Sélectionnez **+ Application** pour ajouter Teams applications LTI.

   ![external-apps.](media/external-apps.png)

3. Sélectionnez **par ID client pour** le type de configuration.

   ![ajouter une application.](media/add-app.png)

4. Entrez l’ID client fourni, puis sélectionnez **Envoyer.**

   Vous remarquerez que le nom Microsoft Teams’application LTI des réunions pour l’ID client pour confirmation.

5. Sélectionnez **Installer**.

   L Microsoft Teams l’application LTI de réunions sera ajoutée à la liste des applications externes.

6. Activez l’application en naviguant vers les clés de développeur dans le compte d’administrateur Canvas, en sélectionnant hérité et en activé le basculement pour Microsoft Teams réunions.
   
## <a name="enable-for-canvas-courses"></a>Activer pour les cours de canevas

Pour utiliser le LTI dans un cours, un instructeur du cours Canvas doit activer la synchronisation des intégrations. Chaque cours doit être activé par un instructeur pour qu’un Teams soit créé . il n’existe pas de mécanisme global pour Teams création. Il est conçu par précaution pour empêcher la création de Teams indésirables.

Consultez la [documentation](https://support.microsoft.com/en-us/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) de vos instructeurs pour activer l’LTI pour chaque cours et terminer la configuration de l’intégration.
