---
title: Autoriser les membres à envoyer en tant que ou envoyer de la part d’un groupe
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
description: Découvrez comment autoriser les membres à envoyer des messages électroniques en tant que groupe Microsoft 365 ou envoyer des courriers électroniques de la part d’un groupe Microsoft 365.
ms.openlocfilehash: 6dff559eceec1b719f31d577d7fff8f604636a47
ms.sourcegitcommit: 47de4402174c263ae8d70c910ca068a7581d04ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "49663582"
---
# <a name="allow-members-to-send-as-or-send-on-behalf-of-a-group"></a>Autoriser les membres à envoyer en tant que ou envoyer de la part d’un groupe

Un membre d’un groupe Microsoft 365 auquel ont été accordées des autorisations **Envoyer en tant** que ou **Envoyer de la part** de peuvent envoyer des messages électroniques en tant que groupe ou pour le compte du groupe. Cet article explique comment un administrateur général ou Exchange peut définir ces autorisations.
  
Par exemple, si Megan Bowen fait partie du groupe **formation** Microsoft 365 et dispose des autorisations **Envoyer en tant** que pour le groupe, si elle envoie un message électronique en tant que groupe, il ressemblera au groupe **formation** qui a envoyé le message. 
  
L’autorisation **Envoyer de la part** de permet à un utilisateur d’envoyer des courriers électroniques de la part d’un groupe Microsoft 365. Par exemple, si Alex Wilber fait partie du groupe Microsoft 365 **marketing** et dispose des autorisations **Envoyer de la part** de, et envoie un message électronique en tant que groupe, le message électronique semble qu’il a été envoyé par **Alex Wilber pour le compte de marketing**.

> [!IMPORTANT]
> Vous pouvez configurer la fonction **Envoyer en tant que** ou **Envoyer de la part** de pour un utilisateur donné, mais pas les deux. Si vous configurez les deux, il s’agit par défaut de la valeur **Envoyer en tant que**.

> [!TIP]
> Pour savoir comment utiliser Outlook et Outlook sur le Web pour envoyer des courriers électroniques à partir d’un groupe, consultez la rubrique [Envoyer un courrier électronique à partir de ou pour le compte de Microsoft 365](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b) .
    
## <a name="allow-members-to-send-email-as-a-group"></a>Autoriser les membres à envoyer des messages électroniques en tant que groupe

Cette section explique comment autoriser les utilisateurs à envoyer des courriers électroniques en tant que groupe dans le [Centre d’administration Exchange](https://go.microsoft.com/fwlink/p/?linkid=2059104) dans Exchange Online.
  
1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>, accédez à groupes de **destinataires** \> .
    
2. Sélectionnez **modifier** ![ l’icône modifier ](../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) le groupe dans le groupe que vous souhaitez autoriser les utilisateurs à envoyer en tant que.   
    
3. Sélectionnez **délégation de groupe**.
    
4. Dans la section **Envoyer en tant que** , sélectionnez le **+** signe pour ajouter les utilisateurs que vous souhaitez envoyer en tant que groupe. 
    
    ![Capture d’écran de la boîte de dialogue Envoyer en tant que](../media/1df167f6-1eff-4f98-9ecd-4230fab46557.png)
  
5. Tapez pour rechercher ou choisir un utilisateur dans la liste. Sélectionnez **OK** et **Enregistrer**.
    
    ![Type de recherche ou de sélection d’un utilisateur dans la liste](../media/522919cf-664c-4a25-8076-c51c8c9fbe43.png)
  
## <a name="allow-members-to-send-email-on-behalf-of-a-group"></a>Autoriser les membres à envoyer des courriers électroniques pour le compte d’un groupe

Cette section explique comment autoriser les utilisateurs à envoyer des courriers électroniques de la part d’un groupe dans le centre d’administration Exchange dans Exchange Online.
  
1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>, accédez à groupes de **destinataires** \> .
    
2. Sélectionnez **modifier** ![ l’icône modifier ](../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) le groupe dans le groupe que vous souhaitez autoriser les utilisateurs à envoyer en tant que. 
    
3. Sélectionnez **délégation de groupe**.
    
4. Dans la section envoyer de la part de, sélectionnez le **+** signe pour ajouter les utilisateurs que vous souhaitez envoyer en tant que groupe. 
    
    ![Capture d’écran de la boîte de dialogue Envoyer de la part de](../media/2bae0579-8907-4d6b-8920-ddd6555897b4.png)
  
5. Tapez pour rechercher ou choisir un utilisateur dans la liste. Sélectionnez **OK** et **Enregistrer**.
    
    ![Type de recherche ou de sélection d’un utilisateur dans la liste](../media/522919cf-664c-4a25-8076-c51c8c9fbe43.png)

## <a name="related-articles"></a>Articles connexes

[Planification de la gouvernance de collaboration étape par étape](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Création de votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[En savoir plus sur les groupes Microsoft 365](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960)

[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189)
