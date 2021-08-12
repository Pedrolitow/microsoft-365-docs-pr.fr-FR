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
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
description: Intégrer Microsoft Teams réunions avec Canvas
ms.openlocfilehash: 5ba812ba2f5694dd7860131479f01fceaba9ab2a040d1ba828306aa022665f74
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53819284"
---
# <a name="use-microsoft-teams-meetings-with-canvas"></a>Utiliser Microsoft Teams réunions avec Canvas

Microsoft Teams réunions est une application Learning Tools Interoperability (LTI) qui permet aux enseignants et aux étudiants de naviguer facilement entre leur système de gestion Learning (LMS) et leur Teams. Les utilisateurs peuvent accéder à leurs équipes de cours associées à leur cours directement à partir de leur LMS.

## <a name="microsoft-office-365-admin"></a>Microsoft Office 365 Administrateur

Avant de gérer l’intégration Microsoft Teams dans Instructure Canvas, il est important que l’application **Microsoft-Teams-Sync-for-Canvas** Azure de Canvas soit approuvée par l’administrateur Microsoft Office 365 de votre établissement dans votre client Microsoft Azure avant de terminer la configuration de l’administrateur canvas.

1. Connectez-vous à Canvas.

2. Sélectionnez **le lien** Administrateur dans la navigation globale, puis sélectionnez votre compte.

3. Dans la navigation de l’administrateur, sélectionnez **Paramètres** lien, puis l’onglet **Intégrations.**

4. Entrez le nom de votre client Microsoft et l’attribut de connexion.

   L’attribut de connexion sera utilisé pour associer l’utilisateur Canvas à un Azure Active Directory utilisateur.

5. Sélectionnez **Mettre à jour Paramètres** une fois terminé.

6. Pour approuver l’accès à l’application **Azure Microsoft-Teams-Sync-for-Canvas de Canvas,** sélectionnez le lien Accorder l’accès **client.** Vous serez redirigé vers le point de terminaison de consentement de l’administrateur de la plateforme d’identités Microsoft.

   ![autorisations](media/permissions.png)

7. Sélectionnez **Accepter**.

8. Activez la synchronisation Microsoft Teams l’utilisateur en activer le basculement.

   ![teams-sync](media/teams-sync.png)

## <a name="canvas-admin"></a>Administrateur de zone de dessin

Configurer l’Microsoft Teams’intégration LTI 1.3.

En tant qu’administrateur de zone de dessin, vous devez ajouter l’application LTI Microsoft Teams réunions au sein de votre environnement. Notez l’ID client LTI de l’application.

 - Microsoft Teams réunions - 170000000000703

1. Access **Admin settings**  >  **Apps**.

2. Sélectionnez **+ Application** pour ajouter Teams applications LTI.

   ![external-apps](media/external-apps.png)

3. Sélectionnez **par ID client pour** le type de configuration.

   ![ajouter une application](media/add-app.png)

4. Entrez l’ID client fourni, puis sélectionnez **Envoyer.**

   Vous remarquerez que le nom Microsoft Teams’application LTI des réunions pour l’ID client pour confirmation.

5. Sélectionnez **Installer**.

   L Microsoft Teams l’application LTI de réunions sera ajoutée à la liste des applications externes.
   
## <a name="enable-for-canvas-courses"></a>Activer pour les cours de canevas

Pour utiliser le LTI dans un cours, un instructeur du cours Canvas doit activer la synchronisation des intégrations. Chaque cours doit être activé par un instructeur pour qu’un Teams soit créé . il n’existe pas de mécanisme global pour Teams création. Il est conçu par précaution pour empêcher la création de Teams indésirables.

Consultez la [documentation](https://support.microsoft.com/en-us/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) de vos instructeurs pour activer l’LTI pour chaque cours et terminer la configuration de l’intégration.
