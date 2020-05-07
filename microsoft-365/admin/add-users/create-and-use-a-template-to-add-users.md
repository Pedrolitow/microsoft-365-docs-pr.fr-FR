---
title: Créer et utiliser un modèle pour ajouter des utilisateurs
f1.keywords:
- NOCSH
ms.author: v-sharos
author: shars
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
search.appverid:
- MET150
- MOE150
description: Vous pouvez créer et utiliser un modèle pour gagner du temps et normaliser les paramètres lors de l’ajout de plusieurs utilisateurs.
ms.openlocfilehash: a39ad3df7928e45f7cb93a13c6ffc40111f2ee48
ms.sourcegitcommit: 7ff75a0f45371b247d975fc61cfa286f5b6f42f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "44140651"
---
# <a name="create-and-use-a-template-to-add-users"></a>Créer et utiliser un modèle pour ajouter des utilisateurs

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux détails présentés ici, reportez-vous [à la rubrique à propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

Vous pouvez créer et utiliser un modèle pour gagner du temps et normaliser les paramètres lors de l’ajout de plusieurs utilisateurs. Les modèles sont particulièrement utiles si vous avez des utilisateurs qui partagent de nombreuses propriétés courantes, par exemple les utilisateurs qui ont le même rôle et travaillent au même endroit et ceux qui ont besoin du même logiciel. Par exemple, vous pouvez avoir une équipe d’ingénieurs du support technique qui travaille dans le même bureau.  

## <a name="create-a-template"></a>Créer un modèle

&mdash;Modèles faciles à créer vous pouvez sélectionner **les** > **modèles utilisateur**des utilisateurs**actifs** > , puis sélectionner **Ajouter un modèle** dans la liste déroulante, ou vous pouvez ajouter un nouvel utilisateur et lorsque vous avez terminé, vous aurez la possibilité d’enregistrer l’entrée en tant que modèle.

Lorsque vous créez un modèle après avoir ajouté un utilisateur, les valeurs que vous choisissez pour les paramètres suivants sont enregistrées dans le modèle :

- Nom du domaine
- Choix des paramètres de mot de passe : vous pouvez choisir de créer des mots de passe ou de les générer automatiquement.
- Choix du mot de passe à usage unique : vous pouvez demander à l’utilisateur de créer un nouveau mot de passe après la première connexion
- Emplacement de la licence
- Choix de licence
- Choix de l’application
- Role
- La plupart des informations de profil, telles que le **profil de travail**, le **service**, le **Bureau**, le **téléphone professionnel**et l' **adresse postale** ; 

Les informations suivantes sont propres à l’utilisateur et ne sont pas enregistrées dans le modèle :

- Prénom et nom
- Nom unique (DN)
- Nom d'utilisateur
- Choix d’envoi du mot de passe par courrier électronique et de l’adresse de messagerie du mot de passe
- Numéro de téléphone mobile

Si vous choisissez de ne pas entrer d’informations pour un paramètre dans une section, cette valeur est vide et ce paramètre ne s’affichera pas dans le modèle. Par exemple, si vous laissez le **titre du travail** vide, lorsque vous examinez votre modèle et lorsque vous utilisez votre modèle, la **fonction** ne s’affiche pas du tout. Si vous laissez tous les paramètres de section de **Profil** vides, la section **Profil** affiche **aucune fournie** dans votre modèle final.

Lorsque vous créez un modèle en sélectionnant l’option **Ajouter un modèle** , vous pouvez choisir les valeurs à effectuer. Tout ce qui reste vide apparaîtra comme **aucun fourni** dans le modèle.

## <a name="use-a-template-to-add-a-user"></a>Utiliser un modèle pour ajouter un utilisateur

Pour utiliser un modèle existant afin d’ajouter un utilisateur :

1. Dans le centre d’administration, **Sélectionnez** > utilisateurs**actifs**.

2. Sélectionnez **modèles utilisateur**, puis sélectionnez un modèle dans la liste déroulante. (La liste ne contient que les modèles que vous avez créés, pas ceux créés par les autres administrateurs.)

 > [!NOTE]
 > Vous pouvez également utiliser un modèle pour ajouter un utilisateur en sélectionnant **modèles** > utilisateur**gérer les modèles**, en sélectionnant un modèle, puis en sélectionnant **utiliser le modèle**.

3. Suivez les étapes pour créer un utilisateur à partir du modèle que vous avez sélectionné.

> [!NOTE]
> Si vous ne disposez pas de licences suffisantes pour un utilisateur que vous ajoutez et que vos informations de paiement sont disponibles, nous essaierons d’acheter une autre licence à l’aide de vos informations de paiement existantes. Si vos informations de paiement ne sont pas disponibles, l’utilisateur sera créé en tant qu’utilisateur sans licence.

## <a name="manage-templates"></a>Gérer les modèles

Vous pouvez facilement supprimer les modèles dont vous n’avez plus besoin et en ajouter de nouveaux. Pour supprimer un modèle :

1. Dans le centre d’administration, **Sélectionnez** > utilisateurs**actifs**.

2. Sélectionnez **modèles**, puis gérer les **modèles** dans la liste déroulante.

3. Une liste de modèles s’affiche. Vous pouvez supprimer un modèle en effectuant l’une des opérations suivantes :
    - Sélectionnez un ou plusieurs modèles, puis sélectionnez **supprimer**. 
    - Sélectionnez les trois points à droite du nom du modèle, puis sélectionnez **supprimer**.
    - Sélectionnez le nom du modèle. Lorsque les détails du modèle s’affichent sur le côté droit de l’écran, sélectionnez **supprimer le modèle**.

## <a name="related-articles"></a>Articles connexes

[Ajouter des utilisateurs individuellement ou en bloc à Microsoft 365](add-users.md)

[Supprimer un ancien employé de Microsoft 365](remove-former-employee.md)
  
