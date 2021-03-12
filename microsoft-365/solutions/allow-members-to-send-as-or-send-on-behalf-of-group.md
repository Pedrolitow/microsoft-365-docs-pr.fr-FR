---
title: Autoriser les membres à envoyer en tant que ou de la part d’un groupe
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 0ad41414-0cc6-4b97-90fb-06bec7bcf590
description: Découvrez comment autoriser les membres du groupe à envoyer des courriers électroniques en tant que groupe Microsoft 365 ou à envoyer du courrier électronique au nom d’un groupe Microsoft 365.
ms.openlocfilehash: 44a0a7a690c8faa9fe00732e8154f36aa5a6fe6f
ms.sourcegitcommit: 3d48e198e706f22ac903b346cadda06b2368dd1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2021
ms.locfileid: "50727078"
---
# <a name="allow-members-to-send-as-or-send-on-behalf-of-a-group"></a>Autoriser les membres à envoyer en tant que ou de la part d’un groupe

Un membre d’un groupe Microsoft 365 qui  a reçu les autorisations Envoyer en tant que ou Envoyer de la part de peut envoyer des messages électroniques en tant que groupe ou au nom du groupe.  (Ces autorisations ne peuvent pas être accordées aux invités du groupe.)

Cet article explique comment un administrateur général ou Exchange peut définir ces autorisations.
  
Par exemple, si Megan Bowen fait partie du groupe **Formation** Microsoft 365 et dispose d’autorisations Envoyer en tant  que sur le groupe, si elle envoie un e-mail en tant que groupe, il semblera que le groupe de formation a envoyé le message électronique.  
  
L’autorisation Envoyer **de la part de** permet à un utilisateur d’envoyer des courriers électroniques au nom d’un groupe Microsoft 365. Par exemple, si Alex Wilber fait partie du groupe **Marketing**  Microsoft 365, dispose des autorisations Envoyer de la part de et envoie un e-mail en tant que groupe, le message semble avoir été envoyé par **Alex Wilber** pour le compte du marketing.

> [!IMPORTANT]
> Vous pouvez configurer **Envoyer en tant** que ou Envoyer de la part **d’un** utilisateur donné, mais pas les deux. Si vous configurez les deux, la valeur par défaut est **Envoyer en tant que**.

> [!TIP]
> Pour découvrir comment utiliser Outlook et Outlook sur le web pour envoyer du courrier électronique à partir d’un groupe, voir Envoyer des courriers électroniques à partir d’un groupe ou au nom d’un groupe [Microsoft 365.](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b)
    
## <a name="allow-members-to-send-email-as-a-group"></a>Autoriser les membres à envoyer des messages électroniques en tant que groupe

Cette section explique comment autoriser les utilisateurs à envoyer des messages électroniques en tant que groupe dans le Centre d’administration [Exchange](https://go.microsoft.com/fwlink/p/?linkid=2059104) (EAC) dans Exchange Online.
  
1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange,</a>allez à **Groupes de destinataires.** \> 
    
2. Sélectionnez **l’icône** Modifier le groupe sur le groupe que vous ![ ](../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) souhaitez autoriser les utilisateurs à envoyer en tant que.   
    
3. Sélectionnez **délégation de groupe.**
    
4. Dans la section **Envoyer en tant** que, sélectionnez le signe pour ajouter les utilisateurs que vous souhaitez envoyer en tant que **+** groupe. 
    
    ![Capture d’écran de la boîte de dialogue Envoyer en tant que](../media/1df167f6-1eff-4f98-9ecd-4230fab46557.png)
  
5. Tapez pour rechercher ou sélectionner un utilisateur dans la liste. Sélectionnez **OK** et **Enregistrez.**
    
    ![Tapez pour rechercher ou sélectionner un utilisateur dans la liste](../media/522919cf-664c-4a25-8076-c51c8c9fbe43.png)
  
## <a name="allow-members-to-send-email-on-behalf-of-a-group"></a>Autoriser les membres à envoyer des courriers électroniques au nom d’un groupe

Cette section explique comment autoriser les utilisateurs à envoyer des messages électroniques au nom d’un groupe dans le Centre d’administration Exchange (EAC) dans Exchange Online.
  
1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange,</a>allez à **Groupes de destinataires.** \> 
    
2. Sélectionnez **l’icône** Modifier le groupe sur le groupe que vous ![ ](../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) souhaitez autoriser les utilisateurs à envoyer en tant que. 
    
3. Sélectionnez **délégation de groupe.**
    
4. Dans la section Envoyer de la part de, sélectionnez le signe pour ajouter les utilisateurs que vous souhaitez **+** envoyer en tant que groupe. 
    
    ![Capture d’écran de la boîte de dialogue Envoyer de la part de](../media/2bae0579-8907-4d6b-8920-ddd6555897b4.png)
  
5. Tapez pour rechercher ou sélectionner un utilisateur dans la liste. Sélectionnez **OK** et **Enregistrer.**
    
    ![Tapez pour rechercher ou sélectionner un utilisateur dans la liste](../media/522919cf-664c-4a25-8076-c51c8c9fbe43.png)

## <a name="related-articles"></a>Articles connexes

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[En savoir plus sur les groupes Microsoft 365](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960)

[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189)
