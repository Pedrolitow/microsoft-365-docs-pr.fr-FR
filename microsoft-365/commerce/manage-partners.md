---
title: Utiliser les fournisseurs de solutions
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration <!-- need to figure out what this value should be -->
localization_priority: Normal
ms.collection:
- commerce <!-- probably need to change this -->
ms.custom: ''
search.appverid:
- MET150
description: Vous pouvez collaborer avec des fournisseurs de solutions certifiés Microsoft pour acheter et gérer des produits et des services pour votre organisation ou votre établissement scolaire.
keywords: partenaire, fournisseur de solutions
ms.openlocfilehash: bb78e1a704529fd2d12ff49639913fe80b75be7a
ms.sourcegitcommit: a7edd3840226e67e82126bb9dee423b3458fef4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "36994075"
---
# <a name="working-with-solution-providers-in-microsoft-store-for-business"></a>Utilisation des fournisseurs de solutions dans Microsoft Store pour les entreprises

Vous pouvez collaborer avec des fournisseurs de solutions certifiés Microsoft pour acheter et gérer des produits et des services pour votre organisation ou votre établissement scolaire. Voici quelques étapes à suivre pour obtenir les éléments configurés. 

Le processus se présente comme suit :
- Les administrateurs trouver et contacter un fournisseur de solutions à l’aide de **la recherche d’un fournisseur de solutions** dans Microsoft Store pour les entreprises. 
- Les fournisseurs de solutions envoient une demande du centre partenaire aux clients pour devenir leur fournisseur de solutions.
- Les clients acceptent l’invitation dans Microsoft Store pour les entreprises et commencent à travailler avec le fournisseur de solutions.
- Les clients peuvent gérer les paramètres de la relation avec le partenaire dans Microsoft Store pour les entreprises. 

## <a name="what-can-a-solution-provider-do-for-my-organization-or-school"></a>Que peut faire un fournisseur de solutions pour mon organisation ou votre établissement scolaire ?

Un fournisseur de solutions peut vous permettre d’utiliser plusieurs méthodes. Les fournisseurs de solutions choisiront l’un de ces éléments lorsqu’ils envoient leur demande de travail en tant que partenaire avec vous.

| Fonction de fournisseur de solution | Description | 
| ------ | ------------------- | 
| Détaillant | Les fournisseurs de solutions vendent des produits Microsoft à votre organisation ou votre établissement scolaire. |
| Administrateur délégué | Le fournisseur de solutions gère les produits et les services pour votre organisation ou votre établissement scolaire. Dans Azure Active Directory (AD), le partenaire sera un administrateur général pour le client. Cela leur permet de gérer des services, tels que la création de comptes d’utilisateur, l’affectation et la gestion de licences, ainsi que la réinitialisation des mots de passe. |
| Revendeur délégué & administrateur délégué | Fournisseurs de solutions qui vendent et gèrent les produits et services Microsoft dans votre organisation ou votre établissement scolaire. |
| Partenaire | Vous pouvez donner à votre fournisseur de solutions un compte d’utilisateur dans votre client et travailler en votre nom avec d’autres services Microsoft. |
| Partenaire Microsoft Products & Services Agreement (MPSA) | Si vous avez travaillé avec plusieurs fournisseurs de solutions via le programme MPSA, vous pouvez autoriser les partenaires à afficher les achats effectués les uns avec les autres. |
| Partenaire PC OEM | Les fournisseurs de solutions peuvent charger des ID de périphérique pour des PC que vous [Gérez avec AutoPilot](https://docs.microsoft.com/microsoft-store/add-profile-to-devices).   |
| Partenaire métier (LOB) | Les fournisseurs de solutions peuvent développer, soumettre et gérer des applications métier spécifiques pour votre organisation ou votre établissement scolaire. |

## <a name="find-a-solution-provider"></a>Trouver un fournisseur de solutions

Vous pouvez trouver un partenaire dans Microsoft Store pour les entreprises et l’éducation. 

1. Connectez-vous à [Microsoft Store pour les entreprises](https://businessstore.microsoft.com/) ou à [Microsoft Store pour l’éducation](https://educationstore.microsoft.com/).
2. Sélectionnez **Rechercher un fournisseur de solutions**.
<!---
    ![Image shows Find a solution provider option in Microsoft Store for Business.](images/msfb-find-partner.png)
-->
3. Affinez la liste ou recherchez un fournisseur de solutions. 
<!---
    ![Image shows Find a solution provider option in Microsoft Store for Business.](images/msfb-provider-list.png)
-->
4. Lorsque vous trouvez un fournisseur de solutions que vous souhaitez utiliser, cliquez sur **contact**.
5. Complétez et envoyez le formulaire.

Le fournisseur de solutions sera en contact avec vous. Vous aurez la possibilité d’en savoir plus à ce sujet. Si vous décidez d’utiliser le fournisseur de solutions, il vous enverra une invitation par courrier électronique auprès du centre de partenaires. 

## <a name="work-with-a-solution-provider"></a>Utiliser un fournisseur de solutions

Une fois que vous avez trouvé un fournisseur de solutions et décidé de l’utiliser, il vous enverra une invitation à collaborer à partir du centre de partenaires. Dans Microsoft Store pour les entreprises ou l’éducation, vous devez accepter l’invitation. Après cela, vous pouvez gérer leurs autorisations.

**Pour accepter une invitation de fournisseur de solution**
1. **Suivre le lien du courrier électronique** : vous recevrez un courrier électronique avec un lien pour accepter l’invitation de fournisseur de solution de votre fournisseur de solutions. Le lien vous permet d’accéder à Microsoft Store pour les entreprises ou à l’éducation.
2. **Accepter** l’invitation de **partenaire accepter**l’invitation, sélectionnez **autoriser** pour accepter l’invitation, accepter les termes du contrat de Cloud Microsoft et commencer à travailler avec le fournisseur de solutions. 
<!---
![Image shows accepting an invitation from a solution provider in Microsoft Store for Business.](images/msft-accept-partner.png)
--> 
## <a name="delegate-admin-privileges"></a>Déléguer des privilèges d’administrateur

En fonction de la demande effectuée par le fournisseur de solutions, une partie de l’acceptation de l’invitation inclut l’acceptation d’accorder des privilèges d’administrateur délégués au fournisseur de solutions. Cela se produit lorsque la demande de fournisseur de solution inclut agir en tant qu’administrateur délégué. Pour plus d’informations, consultez la rubrique [privilèges d’administrateur délégués dans Azure ad](https://docs.microsoft.com/partner-center/customers_revoke_admin_privileges#delegated-admin-privileges-in-azure-ad). 

Si vous ne souhaitez pas déléguer les privilèges d’administrateur au fournisseur de solutions, vous devrez annuler l’invitation au lieu de l’accepter. 

Si vous déléguez les privilèges d’administrateur à un fournisseur de solutions, vous pouvez le supprimer ultérieurement. 

**Pour supprimer les privilèges d’administrateur de délégués**
1. Connectez-vous à [Microsoft Store pour les entreprises](https://businessstore.microsoft.com/) ou à [Microsoft Store pour l’éducation](https://educationstore.microsoft.com/).
2. Sélectionner un **partenaire**
3. Choisissez le partenaire que vous souhaitez gérer.
4. Sélectionnez **Supprimer les autorisations déléguées**. 

Le fournisseur de solutions sera toujours en mesure de travailler avec vous, par exemple en tant que revendeur. 
