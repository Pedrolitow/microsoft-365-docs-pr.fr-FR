---
title: Utiliser l OneDrive Learning opérabilité des outils de gestion
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
description: Créez et classez des devoirs, créez et organisez du contenu de cours et collaborez sur des fichiers en temps réel avec la nouvelle application d’interopérabilité OneDrive Learning Tools.
ms.openlocfilehash: 0e437ed4b05b9968ee1e853f668787eed5351fb5
ms.sourcegitcommit: a4c93a4c7d7db08fe3b032b58d5c7dbbb9476e90
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "53256953"
---
# <a name="use-microsoft-onedrive-lti-with-canvas"></a>Utiliser Microsoft OneDrive LTI avec Canvas

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

## <a name="integrate-with-canvas"></a>Intégration à Canvas

La personne qui effectue cette intégration doit être un administrateur de Canvas et un administrateur du Microsoft 365 client.

1. Connectez-vous au portail Microsoft Azure avec le compte d’administrateur client. L’administrateur client Azure doit également avoir le rôle d’administrateur de groupe.

    ![Administrateur de groupe mis en surbrill](../media/lti-media/lti-group-admin.png)

2. Connectez-vous au portail Microsoft [OneDrive LTI.](https://odltiappnl.azurewebsites.net/admin)

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
    Il sert d’ID client dans Microsoft OneDrive portail LTI.

5. Collez le texte dans le **champ ID client** Microsoft OneDrive portail LTI, puis sélectionnez **Suivant**.

6. Sélectionnez **Enregistrer**.

7. Affichez les paramètres en sélectionnant **Afficher les locataires LTI.**
