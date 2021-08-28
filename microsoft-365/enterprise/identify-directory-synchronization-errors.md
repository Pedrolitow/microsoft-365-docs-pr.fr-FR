---
title: Afficher les erreurs de synchronisation d’annuaires dans Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Découvrez comment afficher les erreurs de synchronisation d’annuaires et les correctifs possibles dans Centre d’administration Microsoft 365.
ms.openlocfilehash: 0bdacf95e0f8534cb721496dc4edb1b49bba131f
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58570208"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Afficher les erreurs de synchronisation d’annuaires dans Microsoft 365

Vous pouvez afficher les erreurs de synchronisation d’annuaires dans le Centre d’administration Microsoft 365. Seules les erreurs de l’objet User sont affichées. Pour afficher les erreurs avec PowerShell, voir [Identifier les objets avec DirSyncProvisioningErrors](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>Afficher les erreurs de synchronisation d’annuaires dans le Centre d’administration Microsoft 365

Pour afficher les erreurs dans le Centre d’administration Microsoft 365 :
  
1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) avec un compte d’administrateur général. 
    
2. Dans  la page d’accueil, vous verrez la carte de **gestion utilisateur.** 
    
    ![Carte de gestion utilisateur dans le Centre d’administration Microsoft 365.](../media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. Sur la carte, sélectionnez **Erreurs de** synchronisation sous **Azure AD Connecter** pour voir les erreurs dans la page Erreurs de synchronisation **d’annuaires.**   
    
    ![Exemple de page d’erreurs de synchronisation d’annuaires.](../media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. Choisissez l’une des erreurs pour afficher le volet d’informations avec des informations sur l’erreur et des conseils sur la façon de la corriger.

   ![Exemple des détails d’une erreur de synchronisation d’annuaires.](../media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
Après l’affichage, voir [résoudre les problèmes liés à](fix-problems-with-directory-synchronization.md) la synchronisation d’annuaires pour Microsoft 365 résoudre les problèmes identifiés.