---
title: Afficher les erreurs de synchronisation d’annuaires dans Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
- admindeeplinkMAC
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
description: Découvrez comment afficher les erreurs de synchronisation d’annuaires et les correctifs possibles dans Centre d'administration Microsoft 365.
ms.openlocfilehash: 1aa6a9208c9ae3091c2490a003eaabb841b78dc5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096499"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Afficher les erreurs de synchronisation d’annuaires dans Microsoft 365

Vous pouvez afficher les erreurs de synchronisation d’annuaires dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>. Seules les erreurs d’objet Utilisateur sont affichées. Pour afficher les erreurs avec PowerShell, consultez [Identifier les objets avec DirSyncProvisioningErrors](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>Afficher les erreurs de synchronisation d’annuaires dans le Centre d'administration Microsoft 365

Pour afficher les erreurs dans le Centre d'administration Microsoft 365 :
  
1. Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) avec un compte d’administrateur général. 
    
2. Sur la page **d’accueil** , vous verrez la carte de **gestion des utilisateurs** . 
    
    ![Carte de gestion des utilisateurs dans le Centre d'administration Microsoft 365.](../media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. Sur la carte, choisissez **Erreurs de synchronisation** sous **Azure AD Connecter** pour afficher les erreurs dans la page **Erreurs de synchronisation d’annuaire**.   
    
    ![Exemple de page d’erreurs de synchronisation d’annuaires.](../media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. Choisissez l’une des erreurs pour afficher le volet d’informations avec des informations sur l’erreur et des conseils sur la façon de la corriger.

   ![Exemple de détails d’une erreur de synchronisation d’annuaire.](../media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
Après l’affichage, consultez [la résolution des problèmes de synchronisation d’annuaires pour Microsoft 365](fix-problems-with-directory-synchronization.md) afin de corriger les problèmes identifiés.