---
title: Créer et utiliser un modèle pour ajouter des utilisateurs
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
description: Vous pouvez créer et utiliser un modèle pour gagner du temps et normaliser les paramètres lorsque vous ajoutez plusieurs utilisateurs dans le Centre d'administration Microsoft 365.
ms.openlocfilehash: b316b5e30a98258ccf0ee6dcf4afd5d190b0faa0
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68722041"
---
# <a name="create-and-use-a-template-to-add-users"></a>Créer et utiliser un modèle pour ajouter des utilisateurs

Vous pouvez créer et utiliser un modèle pour gagner du temps et normaliser les paramètres lorsque vous ajoutez plusieurs utilisateurs. Les modèles sont particulièrement utiles si vous avez des utilisateurs qui partagent de nombreuses propriétés communes, comme ceux qui ont le même rôle et travaillent au même emplacement et ceux qui ont besoin du même logiciel. Par exemple, vous pouvez avoir une équipe d’ingénieurs du support technique qui travaillent dans le même bureau.  

## <a name="create-a-template"></a>Créer un modèle

Les modèles sont faciles à créer&mdash;, vous pouvez sélectionner **Utilisateurs** > **Utilisateurs** >  actifs **Modèles** d’utilisateur, puis **ajouter un modèle** dans la liste déroulante, ou vous pouvez ajouter un nouvel utilisateur et, lorsque vous avez terminé, vous aurez la possibilité d’enregistrer l’entrée en tant que modèle.

Lorsque vous créez un modèle après avoir ajouté un utilisateur, les valeurs que vous choisissez pour les paramètres suivants sont enregistrées dans le modèle :

- Nom du domaine
- Choix des paramètres de mot de passe : vous pouvez choisir de créer des mots de passe ou de les générer automatiquement
- Choix de mot de passe à usage unique : vous pouvez demander à l’utilisateur de créer un mot de passe après la première connexion
- Emplacement de la licence
- Choix de licences
- Choix d’applications
- Rôle
- La plupart des informations de profil, telles que **profil d’emploi**, **département**, **bureau**, **téléphone de bureau** et **adresse postale** 

Les informations suivantes sont spécifiques à l’utilisateur et ne sont pas enregistrées dans le modèle :

- Prénom et nom
- Nom d’affichage
- Nom d'utilisateur
- Choix d’envoyer le mot de passe par e-mail et à qui l’e-mail de mot de passe est envoyé
- Numéro de téléphone mobile

Si vous choisissez de ne pas entrer d’informations pour un paramètre dans une section, cette valeur sera vide et ce paramètre ne s’affichera pas dans le modèle. Par exemple, si vous laissez le **titre de l’emploi** vide, lorsque vous passez en revue votre modèle et que vous utilisez votre modèle, le **titre du** poste n’apparaît pas du tout. Si vous laissez tous les paramètres de la section **Profil** vides, la section **Profil** affiche **Aucun fourni** dans votre modèle final.

Lorsque vous créez un modèle en sélectionnant l’option **Ajouter un modèle** , vous pouvez choisir les valeurs à compléter. Tout ce qui est laissé vide s’affiche sous **la forme Aucun fourni** dans le modèle.

## <a name="use-a-template-to-add-a-user"></a>Utiliser un modèle pour ajouter un utilisateur

Pour utiliser un modèle existant pour ajouter un utilisateur :

1. Dans le centre d’administration, sélectionnez **Utilisateurs Utilisateurs** > **utilisateurs actifs**.

2. Sélectionnez **Modèles utilisateur**, puis sélectionnez un modèle dans la liste déroulante. (La liste contient uniquement les modèles que vous avez créés, et non ceux créés par d’autres administrateurs.)

   > [!NOTE]
   > Vous pouvez également utiliser un modèle pour ajouter un utilisateur en sélectionnant Modèles  > **d’utilisateur****Gérer les modèles**, en sélectionnant un modèle, puis En **sélectionnant Utiliser le modèle**.

3. Suivez les étapes pour créer un utilisateur à partir du modèle que vous avez sélectionné.

   > [!NOTE]
   > Si vous n’avez pas suffisamment de licences disponibles pour un utilisateur que vous ajoutez et que vos informations de paiement sont disponibles, nous tenterons d’acheter une autre licence à l’aide de vos informations de paiement existantes. Si vos informations de paiement ne sont pas disponibles, l’utilisateur est créé en tant qu’utilisateur sans licence.

## <a name="manage-templates"></a>Gérer les modèles

Vous pouvez uniquement supprimer les modèles dont vous n’avez plus besoin et en ajouter de nouveaux. Pour supprimer un modèle :

1. Dans le centre d’administration, sélectionnez **Utilisateurs Utilisateurs** > **utilisateurs actifs**.

2. Sélectionnez **Modèles**, puis **Gérer les modèles** dans la liste déroulante.

3. Une liste de modèles s’affiche. Vous pouvez supprimer un modèle en effectuant l’une des opérations suivantes :
    - Sélectionnez un ou plusieurs modèles, puis **sélectionnez Supprimer**. 
    - Sélectionnez les trois points à droite du nom du modèle, puis sélectionnez **Supprimer**.
    - Sélectionnez le nom du modèle. Lorsque les détails du modèle s’affichent sur le côté droit de votre écran, sélectionnez **Supprimer le modèle**.

## <a name="related-articles"></a>Articles connexes

[Ajouter des utilisateurs et attribuer des licences simultanément](add-users.md)

[Supprimer un ancien employé de Microsoft 365](remove-former-employee.md)
  
