---
title: Utiliser l’interopérabilité des outils d’apprentissage OneDrive
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
description: Créez et classez des devoirs, créez et organisez du contenu de cours et collaborez sur des fichiers en temps réel avec la nouvelle application d’interopérabilité des outils d’apprentissage OneDrive.
ms.openlocfilehash: 97baf3e524e483e879d00f5e0c8495b450e13c92
ms.sourcegitcommit: 68383240ef7a673d5f28e2ecfab9f105bf1d8c8f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "52327708"
---
# <a name="use-microsoft-onedrive-with-your-learning-management-system"></a>Utiliser Microsoft OneDrive avec votre système de gestion de l’apprentissage

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Découvrez les avantages de l’utilisation de Microsoft OneDrive avec votre système de gestion de l’apprentissage (LMS).

**Apporte Microsoft Office 365 directement dans vos flux de travail**

L’application Microsoft OneDrive Learning Tools Interoperability (LTI) s’intègre à votre LMS pour intégrer Microsoft OneDrive et Microsoft Office 365 directement dans vos flux de travail les plus importants, notamment :

- Attachement de ressources et organisation du contenu.
- Démarrage de documents collaboratifs.
- Création et notation d’affectations.

**Sécurisé et entièrement conforme aux dernières normes LTI**

L’application LTI Microsoft OneDrive est compatible avec LTI 1.3 et LTI Advantage. Cet avantage permet une expérience utilisateur hautement sécurisée et étroitement intégrée.

**Expérience utilisateur moderne et enrichie**

L’application LTI Microsoft OneDrive apporte le meilleur de Microsoft directement dans votre expérience LMS. Nous sommes en train d’améliorer l’intégration d’Office 365 existante dans votre LMS en offrent une expérience utilisateur plus moderne, avec un nouveau s picker de fichier Microsoft OneDrive développé et des expériences de modification plus riches pour les fichiers Office. Microsoft sera également propriétaire de l’application LTI Microsoft OneDrive à l’avenir, ce qui signifie que vous recevrez toujours automatiquement les dernières nouveautés de Microsoft.

L’application LTI Microsoft OneDrive vous permet de :

- Joindre des fichiers Office 365, y compris des documents Word, des présentations PowerPoint et Excel à partir de l’éditeur de contenu enrichi.

- Distribuer les affectations dans le cloud Office 365.

- Affichez et organisez vos fichiers Microsoft OneDrive personnels et de cours.

- Créez des collaborations où les membres du cours peuvent collaborer sur des documents partagés en temps réel.

- Accéder à plusieurs comptes Microsoft OneDrive, y compris les comptes personnels et scolaires.

- Intégrez des fichiers Office 365 à vos modules de cours.

- Utilisez votre compte Microsoft pour l' sign-on unique avec votre LMS.

## <a name="integrate-with-canvas"></a>Intégration à Canvas

La personne qui effectue cette intégration doit être un administrateur de Canvas et un administrateur du client Microsoft 365.

1. Connectez-vous au portail Microsoft Azure avec le compte d’administrateur client. L’administrateur client Azure doit également avoir le rôle d’administrateur de groupe.

    ![Administrateur de groupe mis en surbrill](../media/lti-media/lti-group-admin.png)

2. Connectez-vous au [portail Microsoft OneDrive LTI.](https://odltiappnl.azurewebsites.net/admin)

3. Acceptez les autorisations pour terminer la sign-in.

    ![accepter les autorisations](../media/lti-media/lti-permissions.png)

4. Sélectionnez **Ajouter un client LTI.**

     ![ajouter un client LTI](../media/lti-media/lti-add-tenant.png)

5. Sélectionnez **plateforme consommateur LTI** en **tant que zone** de dessin dans la zone de dropdown.

6. Sélectionnez **l’URL de base** de la zone de dessin, puis sélectionnez **Suivant.**

    ![sélectionner Canvas et ajouter une URL de base](../media/lti-media/lti-canvas-base-url.png)

   L’écran suivant affiche les champs qui vous sont confidentiels.

7. Sélectionner **Suivant** à partir de ?? page. LES RÉVISEURS PEUVENT-ILS REMPLIR LE VIDE ICI ?

8. Sélectionnez **Suivant** dans l’écran qui affiche les informations confidentielles pour vous.

   L’écran final du portail Azure affiche les étapes suivantes pour ajouter votre instance de canvas.

9. Copiez les clés de développeur à partir de cet écran. Vous l’utiliserez lorsque vous créerez l’instance canvas.

## <a name="add-the-canvas-instance"></a>Ajouter l’instance canvas

1. Dans votre instance de canvas, désélectionnez **les clés de** développeur  >  **d’administration.**

2. Choose **LTI Key** in the dropdown on **Developer Key**.

   ![Obtenir les clés de développement LTI](../media/lti-media/lti-developer-keys.png)

3. Collez les clés de développeur ici.

     ![Coller les clés de développeur](../media/lti-media/lti-developer-keys.png)

   La clé est créée en mode **OFF**

   ![Clés de développeur créées en mode Hors](../media/lti-media/lti-copy-developer-keys.png)

4. Copiez le texte mis en surbrillant.
    Il sert d’ID client dans le portail Microsoft OneDrive LTI.

5. Collez le texte dans le **champ ID client** dans le portail Microsoft OneDrive LTI, puis sélectionnez **Suivant**.

6. Sélectionnez **Enregistrer**.

7. Affichez les paramètres en sélectionnant **Afficher les locataires LTI.**
