---
title: Utiliser Microsoft Teams classes avec Canvas
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
description: Intégrer Microsoft Teams classes à Canvas
ms.openlocfilehash: 44ba24e5c8bd7107f9cba199ce290c10b31e0806
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59203262"
---
# <a name="use-microsoft-teams-classes-with-canvas"></a>Utiliser Microsoft Teams classes avec Canvas

Microsoft Teams classes est une application Learning Tools Interoperability (LTI) qui permet aux enseignants et aux étudiants de naviguer facilement entre leur système de gestion Learning (LMS) et leur Teams. Les utilisateurs peuvent accéder à leurs équipes de cours associées à leur cours directement à partir de leur LMS.

## <a name="prerequisites-before-deployment"></a>Conditions préalables avant le déploiement

> [!NOTE]
> La classe actuelle Teams LTI prend uniquement en charge la synchronisation des utilisateurs canvas avec Microsoft Azure Active Directory (AAD) dans une étendue limitée. 
> - Votre client doit avoir une licence Microsoft Éducation.
> - Un seul client Microsoft peut être utilisé pour le mappage d’utilisateurs entre Canvas et Microsoft.
> - Vous devez désactiver le Synchronisation des données scolaires (SDS) avant d’utiliser l’Teams LTI de classe afin d’éviter la duplication des groupes.

## <a name="microsoft-office-365-admin"></a>Microsoft Office 365 Administrateur

Avant de gérer l’intégration Microsoft Teams dans Instructure Canvas, il est important que l’application **Microsoft Teams-Sync-for-Canvas** Azure de Canvas soit approuvée par l’administrateur Microsoft Office 365 de votre établissement dans votre client Microsoft Azure avant de terminer la configuration de l’administrateur canvas.

1. Connectez-vous à Canvas.

2. Sélectionnez **le lien** Administrateur dans la navigation globale, puis sélectionnez votre compte.

3. Dans la navigation de l’administrateur, sélectionnez **Paramètres** lien, puis l’onglet **Intégrations.**

4. Activez Microsoft Teams synchronisation en activé le basculement.
   
   ![Canvas Teams Sync Updated png.](https://user-images.githubusercontent.com/87142492/128225881-abdfc52d-dc9e-48ad-aec5-f6617c6436f3.png)

5. Entrez le nom de votre client Microsoft, l’attribut de connexion, le suffixe de domaine et l’attribut de recherche AAD.

   Ces champs seront utilisés pour faire correspondre les utilisateurs de Canvas aux utilisateurs Microsoft Azure Active Directory. 
   * L’attribut de connexion est l’attribut utilisateur Canvas utilisé pour la correspondance.
   * Le champ Suffix est facultatif et vous permet de spécifier un domaine lorsqu’il n’existe pas de mappage exact entre les attributs canvas et les champs Microsoft AAD. Par exemple, si votre e-mail Canvas est « name@example.edu » alors que l’UPN dans Microsoft AAD est « nom » , vous pouvez faire correspondre les utilisateurs en entrant « example.edu » dans le champ de suffixe.
   * L’attribut de recherche Active Directory est le champ côté Microsoft auquel les attributs Canvas sont en correspondance. Sélectionnez l’UPN, l’adresse de messagerie principale ou l’alias de messagerie.

6. Sélectionnez **Mettre à jour Paramètres** une fois terminé.

7. Pour approuver l’accès à l’application **Azure Microsoft-Teams-Sync-for-Canvas de Canvas,** sélectionnez le lien Accorder l’accès **client.** Vous serez redirigé vers le point de terminaison de consentement de l’administrateur de la plateforme d’identités Microsoft.

   ![autorisations.](media/permissions.png)

8. Sélectionnez **Accepter**.

## <a name="canvas-admin"></a>Administrateur de zone de dessin

Configurer l’Microsoft Teams’intégration LTI 1.3.

En tant qu’administrateur de zone de dessin, vous devez ajouter l’application Microsoft Teams classes LTI dans votre environnement. Accédez à la liste des clés du développeur dans le compte principal, basculez vers les clés héritées et activez l’outil Teams LTI. Notez l’ID client LTI de l’application.

 - Microsoft Teams classes - 170000000000570

1. Access **Admin settings**  >  **Apps**.

2. Sélectionnez **+ Application** pour ajouter Teams applications LTI.

   ![external-apps.](media/external-apps.png)

3. Sélectionnez **par ID client pour** le type de configuration.

   ![ajouter une application.](media/add-app.png)

4. Entrez l’ID client fourni, puis sélectionnez **Envoyer.**

   Vous remarquerez que le nom Microsoft Teams’application LTI des classes pour l’ID client pour confirmation.

5. Sélectionnez **Installer**.

   L Microsoft Teams’application LTI des classes sera ajoutée à la liste des applications externes.
   
## <a name="enabling-the-lti-app-for-canvas-courses"></a>Activation de l’application LTI pour les cours canvas

Pour utiliser l’application LTI dans un cours, un instructeur du cours Canvas doit activer la synchronisation des intégrations. Chaque cours doit être activé par un instructeur pour qu’une équipe correspondante soit créée . Il n’existe pas de mécanisme global pour la création d’équipes. Il s’agit d’une mesure de précaution pour empêcher la création d’équipes indésirables.

Consultez la [documentation](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) des instructeurs pour activer l’application LTI pour chaque cours et terminer la configuration de l’intégration.
