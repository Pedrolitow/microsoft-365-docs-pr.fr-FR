---
title: Créer et utiliser un modèle pour ajouter des utilisateurs
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
description: Vous pouvez créer et utiliser un modèle pour gagner du temps et normaliser les paramètres lorsque vous ajoutez plusieurs utilisateurs.
ms.openlocfilehash: aef5085da603c38b37544b76c5336c9bfe4edd24
ms.sourcegitcommit: 2d3e85173c65a9e0ce92624a80ed7a9839f5b8bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "49123416"
---
# <a name="create-and-use-a-template-to-add-users"></a>Créer et utiliser un modèle pour ajouter des utilisateurs

Vous pouvez créer et utiliser un modèle pour gagner du temps et normaliser les paramètres lorsque vous ajoutez plusieurs utilisateurs. Les modèles sont particulièrement utiles si vous avez des utilisateurs qui partagent de nombreuses propriétés communes, comme ceux qui ont le même rôle et travaillent au même emplacement et ceux qui ont besoin du même logiciel. Par exemple, vous pouvez avoir une équipe d’ingénieurs de support technique qui travaillent dans le même bureau.  

## <a name="create-a-template"></a>Créer un modèle

Les modèles sont faciles à créer. Vous pouvez sélectionner des &mdash;   >    >  **modèles Utilisateurs actifs utilisateurs,**  puis ajouter un modèle dans la liste de listes. Vous pouvez également ajouter un nouvel utilisateur et, lorsque vous avez terminé, vous avez la possibilité d’enregistrer l’entrée en tant que modèle.

Lorsque vous créez un modèle après avoir ajouté un utilisateur, les valeurs que vous choisissez pour les paramètres suivants sont enregistrées dans le modèle :

- Nom du domaine
- Choix des paramètres de mot de passe : vous pouvez choisir de créer des mots de passe ou de les faire générer automatiquement
- Choix de mot de passe unique : vous pouvez demander à l’utilisateur de créer un mot de passe après la première signature
- Emplacement de la licence
- Choix de licence
- Choix de l’application
- Role
- La plupart des informations de profil, telles que profil **de** travail, **service,** **bureau,** **téléphone office** et adresse **de rue** 

Les informations suivantes sont propres à l’utilisateur et ne sont pas enregistrées dans le modèle :

- Prénom et nom
- Nom d’affichage
- Nom d'utilisateur
- Choix d’envoyer le mot de passe par courrier électronique et à qui le message électronique de mot de passe est envoyé
- Numéro de téléphone mobile

Si vous choisissez de ne pas entrer d’informations pour un paramètre dans une section, cette valeur sera vide et ce paramètre ne s’affichera pas dans le modèle. Par exemple, si vous laissez la **fonction** vide, lorsque vous examinez votre modèle et que vous l’utilisez,  la fonction n’apparaît pas du tout. Si vous laissez tous les paramètres **de** section Profil vides, la section **Profil** affiche **Aucun** fourni dans votre modèle final.

Lorsque vous créez un modèle en sélectionnant **l’option** Ajouter un modèle, vous pouvez choisir les valeurs à compléter. Tout ce qui reste vide s’affiche comme **aucun fourni** dans le modèle.

## <a name="use-a-template-to-add-a-user"></a>Utiliser un modèle pour ajouter un utilisateur

Pour utiliser un modèle existant afin d’ajouter un utilisateur :

1. Dans le Centre d’administration, sélectionnez **Utilisateurs**  >  **actifs.**

2. Sélectionnez **les modèles utilisateur,** puis sélectionnez un modèle dans la liste de listes. (La liste contient uniquement les modèles que vous avez créés, et non ceux créés par d’autres administrateurs.)

   > [!NOTE]
   > Vous pouvez également utiliser un modèle pour ajouter un utilisateur en sélectionnant **Modèles** utilisateur Gérer les  >  **modèles,** sélection d’un modèle, puis utilisation **du modèle.**

3. Suivez les étapes pour créer un utilisateur à partir du modèle que vous avez sélectionné.

   > [!NOTE]
   > Si vous disposez de licences insuffisantes pour un utilisateur que vous ajoutez et que vos informations de paiement sont disponibles, nous tenterons d’acheter une autre licence à l’aide de vos informations de paiement existantes. Si vos informations de paiement ne sont pas disponibles, l’utilisateur est créé en tant qu’utilisateur sans permis.

## <a name="manage-templates"></a>Gérer les modèles

Vous pouvez uniquement supprimer des modèles dont vous n’avez plus besoin et en ajouter de nouveaux. Pour supprimer un modèle :

1. Dans le Centre d’administration, sélectionnez **Utilisateurs**  >  **actifs.**

2. Sélectionnez **Modèles,** puis **Gérez les modèles** dans la liste de listes.

3. Une liste de modèles s’affiche. Vous pouvez supprimer un modèle en faisant l’une des choses suivantes :
    - Sélectionnez un ou plusieurs modèles, puis sélectionnez **Supprimer.** 
    - Sélectionnez les trois points à droite du nom du modèle, puis sélectionnez **Supprimer.**
    - Sélectionnez le nom du modèle. Lorsque les détails du modèle apparaissent sur le côté droit de votre écran, sélectionnez **Supprimer le modèle.**

## <a name="related-articles"></a>Articles connexes

[Ajouter des utilisateurs et attribuer des licences en même temps](add-users.md)

[Supprimer un ancien employé de Microsoft 365](remove-former-employee.md)
  
