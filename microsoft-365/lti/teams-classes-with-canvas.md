---
title: Utiliser Microsoft Teams classes avec Canvas
ms.author: v-cichur
author: cichur
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
description: Intégrer Microsoft Teams classes à Canvas
ms.openlocfilehash: 8e28cc8401dbf37d6e780b8f56dc300982abd0cc
ms.sourcegitcommit: 410f6e1c6cf53c3d9013b89d6e0b40a050ee9cad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53137678"
---
# <a name="use-microsoft-teams-classes-with-canvas"></a>Utiliser Microsoft Teams classes avec Canvas

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Microsoft Teams classes est une application Learning Tools Interoperability (LTI) qui permet aux enseignants et aux étudiants de naviguer facilement entre leur système de gestion Learning (LMS) et leur Teams. Les utilisateurs peuvent accéder à leurs équipes de cours associées à leur cours directement à partir de leur LMS.

## <a name="microsoft-office-365-admin"></a>Microsoft Office 365 Administrateur

Avant de gérer l’intégration Microsoft Teams dans Instructure Canvas, il est important que l’application **Microsoft-Teams-Sync-for-Canvas** Azure de Canvas soit approuvée par l’administrateur Microsoft Office 365 de votre établissement dans votre client Microsoft Azure avant de terminer la configuration de l’administrateur canvas.

1. Connectez-vous à Canvas.
 
2. Sélectionnez **le lien** Administrateur dans la navigation globale, puis sélectionnez votre compte.

3. Dans la navigation de l’administrateur, **sélectionnez Paramètres** lien, puis l’onglet **Intégrations.** 

4. Activez Microsoft Teams synchronisation en activer le basculement.

   ![teams-sync](media/teams-sync.png)

5. Entrez le nom de votre client Microsoft et l’attribut de connexion. 

   L’attribut de connexion sera utilisé pour associer l’utilisateur Canvas à un Azure Active Directory utilisateur. 

6. Sélectionnez **Mettre à jour Paramètres** une fois terminé.

7. Pour approuver l’accès à l’application **Azure Microsoft-Teams-Sync-for-Canvas de Canvas,** sélectionnez le lien Accorder l’accès **client.** Vous serez redirigé vers le point de terminaison de consentement de l’administrateur de la plateforme d’identités Microsoft.

   ![autorisations](media/permissions.png)

8. Sélectionnez **Accepter**.
 
## <a name="canvas-admin"></a>Administrateur de zone de dessin

Configurer l’Microsoft Teams’intégration LTI 1.3.

En tant qu’administrateur de zone de dessin, vous devez ajouter l’application Microsoft Teams classes LTI dans votre environnement. Notez l’ID client LTI de l’application.

 - Microsoft Teams classes - 17000000000570

1. Access **Admin settings**  >  **Apps**.

2. Sélectionnez **+ Application** pour ajouter Teams applications LTI. 
 
   ![external-apps](media/external-apps.png)

3. Sélectionnez **par ID client pour** le type de configuration.

   ![ajouter une application](media/add-app.png)

4. Entrez l’ID client fourni, puis sélectionnez **Envoyer.**
   
   Vous remarquerez que le nom Microsoft Teams’application LTI des classes pour l’ID client pour confirmation. 

5. Sélectionnez **Installer**.

   L Microsoft Teams’application LTI des classes sera ajoutée à la liste des applications externes.
