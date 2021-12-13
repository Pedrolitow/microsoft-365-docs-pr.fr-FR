---
title: Autoriser les membres à envoyer en tant que ou de la part d’un groupe
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
ms.custom: admindeeplinkEXCHANGE
search.appverid:
- MET150
ms.assetid: 0ad41414-0cc6-4b97-90fb-06bec7bcf590
recommendations: false
description: Découvrez comment autoriser les membres d’un groupe à envoyer des messages électroniques en tant que Microsoft 365 groupe ou à envoyer du courrier électronique au nom d’Microsoft 365 groupe.
ms.openlocfilehash: a21e30ef613f557d1206ada5bc9ab4be8a083834
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2021
ms.locfileid: "61421581"
---
# <a name="allow-members-to-send-as-or-send-on-behalf-of-a-group"></a>Autoriser les membres à envoyer en tant que ou de la part d’un groupe

Un membre d’un groupe Microsoft 365 qui  a obtenu  des autorisations Envoyer en tant que ou Envoyer de la part de peut envoyer des messages électroniques en tant que groupe ou au nom du groupe. (Ces autorisations ne peuvent pas être accordées aux invités du groupe.)

Cet article explique comment un administrateur général ou Exchange peut définir ces autorisations.
  
Par exemple, si Megan Bowen fait partie du groupe  formation **Microsoft 365** et dispose des autorisations Envoyer en tant que sur  le groupe, si elle envoie un e-mail en tant que groupe, il semblera que le groupe de formation a envoyé le message électronique. 
  
L’autorisation Envoyer de **la part de** permet à un utilisateur d’envoyer des messages électroniques au nom d’Microsoft 365 groupe. Par exemple, si Alex Wilber fait partie du groupe **Marketing** Microsoft 365, dispose des autorisations Envoyer de la part de et envoie un e-mail en tant que groupe, le message électronique semble avoir été envoyé par **Alex Wilber** pour le compte de Marketing. 

> [!IMPORTANT]
> Vous pouvez configurer **Envoyer en tant** que ou Envoyer de la part **d’un** utilisateur donné, mais pas les deux. Si vous configurez les deux, la valeur par défaut est **Envoyer en tant que**.

> [!TIP]
> Pour découvrir [comment](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b) utiliser Outlook et Outlook sur le Web pour envoyer des messages électroniques à partir d’un groupe, voir Envoyer des courriers électroniques depuis ou pour le compte d’un groupe Microsoft 365.
    
## <a name="allow-members-to-send-email-as-a-group"></a>Autoriser les membres à envoyer des messages électroniques en tant que groupe

Cette section explique comment autoriser les utilisateurs à envoyer des messages électroniques en tant que groupe dans le Centre d’administration<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange (EAC)</a> dans Exchange Online.
  
1. Dans le centre Exchange’administration, allez à **Groupes de** \> <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**destinataires.**</a>
    
2. Sélectionnez **Modifier** ![ l’icône Modifier le groupe.  ](../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) sur le groupe que vous souhaitez autoriser les utilisateurs à envoyer en tant que. 
    
3. Sélectionnez **délégation de groupe.**
    
4. Dans la section **Envoyer en tant** que, sélectionnez le signe pour ajouter les utilisateurs que vous souhaitez envoyer en tant que **+** groupe. 
    
    ![Capture d’écran de la boîte de dialogue Envoyer en tant que.](../media/1df167f6-1eff-4f98-9ecd-4230fab46557.png)
  
5. Tapez pour rechercher ou sélectionner un utilisateur dans la liste. Sélectionnez **OK** et **Enregistrez.**
    
    ![Tapez pour rechercher ou sélectionner un utilisateur dans la liste.](../media/522919cf-664c-4a25-8076-c51c8c9fbe43.png)
  
## <a name="allow-members-to-send-email-on-behalf-of-a-group"></a>Autoriser les membres à envoyer des courriers électroniques au nom d’un groupe

Cette section explique comment autoriser les utilisateurs à envoyer des messages électroniques au nom d’un groupe dans le Centre d’administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange (EAC)</a> dans Exchange Online.
  
1. Dans le centre Exchange’administration, allez à **Groupes de** \> <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**destinataires.**</a>
    
2. Sélectionnez **Modifier** ![ l’icône Modifier le groupe.](../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) sur le groupe que vous souhaitez autoriser les utilisateurs à envoyer en tant que. 
    
3. Sélectionnez **délégation de groupe.**
    
4. Dans la section Envoyer de la part de, sélectionnez le signe pour ajouter les utilisateurs que vous souhaitez **+** envoyer en tant que groupe. 
    
    ![Capture d’écran de la boîte de dialogue Envoyer de la part de.](../media/2bae0579-8907-4d6b-8920-ddd6555897b4.png)
  
5. Tapez pour rechercher ou sélectionner un utilisateur dans la liste. Sélectionnez **OK** et **Enregistrez.**
    
    ![Tapez pour rechercher ou sélectionner un utilisateur dans la liste.](../media/522919cf-664c-4a25-8076-c51c8c9fbe43.png)

## <a name="related-articles"></a>Articles connexes

[Recommandations en matière de planification de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[En savoir plus sur Microsoft 365 groupes](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission)

[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup)