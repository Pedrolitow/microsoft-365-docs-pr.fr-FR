---
title: Autoriser les membres à envoyer en tant que ou envoyer de la part d’un groupe
ms.reviewer: arvaradh
f1.keywords:
- NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0ad41414-0cc6-4b97-90fb-06bec7bcf590
description: Découvrez comment autoriser les membres à envoyer des messages électroniques en tant que groupe Office 365 ou envoyer des courriers électroniques de la part d’un groupe Office 365.
ms.openlocfilehash: 0179dbd2e3093ce80929f6c5f9e689aece845a40
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42352755"
---
# <a name="allow-members-to-send-as-or-send-on-behalf-of-a-group"></a>Autoriser les membres à envoyer en tant que ou envoyer de la part d’un groupe

Un membre d’un groupe Office 365 auquel ont été accordées des autorisations **Envoyer en tant** que ou **Envoyer de la part** de peuvent désormais envoyer des courriers électroniques en tant que groupe ou au nom du groupe. Cette rubrique explique comment un administrateur peut définir ces autorisations.
  
Par exemple, si Megan Bowen fait partie du groupe **formation** Office 365 et qu’il dispose des autorisations **Envoyer en tant** que pour le groupe, si elle envoie un message électronique en tant que groupe, il ressemblera au groupe de **formation** qui a envoyé le message. 
  
L’autorisation **Envoyer de la part** de permet à un utilisateur d’envoyer des courriers électroniques de la part d’un groupe Office 365. Par exemple, si Alex Wilber fait partie du groupe Office **Marketing** 365 et qu’il dispose des autorisations **Envoyer de la part** de et qu’il envoie un message électronique en tant que groupe, le message électronique a été envoyé par **Alex Wilber pour le compte de marketing**.

> [!IMPORTANT]
> Vous pouvez configurer la fonction **Envoyer en tant que** ou **Envoyer de la part** de pour un utilisateur donné, mais pas les deux. Si vous configurez les deux, il s’agit par défaut de la valeur **Envoyer en tant que**.

> [!TIP]
> Consultez les étapes de la procédure [envoyer 365 un courrier électronique à partir de ou pour](https://support.office.com/article/0f4964af-aec6-484b-a65c-0434df8cdb6b.aspx) pour savoir comment utiliser Outlook et Outlook sur le Web pour envoyer des courriers électroniques à partir d’un groupe.
    
## <a name="allow-members-to-send-email-as-a-group"></a>Autoriser les membres à envoyer des messages électroniques en tant que groupe

Cette section explique comment autoriser les utilisateurs à envoyer des courriers électroniques en tant que groupe dans le [Centre d’administration Exchange](https://go.microsoft.com/fwlink/p/?linkid=2059104) dans Exchange Online.
  
1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>, accédez à **groupes**de **destinataires** \> .
    
2. Sélectionnez **modifier**![l’icône](../../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) du groupe de modification sur le groupe que vous souhaitez autoriser les utilisateurs à envoyer en tant que.   
    
3. Sélectionnez **délégation de groupe**.
    
4. Dans la section **Envoyer en tant que** , **+** sélectionnez le signe pour ajouter les utilisateurs que vous souhaitez envoyer en tant que groupe. 
    
    ![Sélectionnez le signe plus pour ajouter les utilisateurs que vous souhaitez envoyer en tant que groupe Office 365](../../media/1df167f6-1eff-4f98-9ecd-4230fab46557.png)
  
5. Tapez pour rechercher ou choisir un utilisateur dans la liste. Sélectionnez **OK** et **Enregistrer**.
    
    ![Type de recherche ou de sélection d’un utilisateur dans la liste](../../media/522919cf-664c-4a25-8076-c51c8c9fbe43.png)
  
## <a name="allow-members-to-send-email-on-behalf-of-a-group"></a>Autoriser les membres à envoyer des courriers électroniques pour le compte d’un groupe

Cette section explique comment autoriser les utilisateurs à envoyer des courriers électroniques de la part d’un groupe dans le centre d’administration Exchange dans Exchange Online.
  
1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>, accédez à **groupes**de **destinataires** \> .
    
2. Sélectionnez **modifier** ![l’icône](../../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) modifier le groupe dans le groupe que vous souhaitez autoriser les utilisateurs à envoyer en tant que. 
    
3. Sélectionnez **délégation de groupe**.
    
4. Dans la section envoyer de la part de, **+** sélectionnez le signe pour ajouter les utilisateurs que vous souhaitez envoyer en tant que groupe. 
    
    ![Sélectionnez le signe plus pour ajouter les utilisateurs que vous souhaitez envoyer en tant que groupe Office 365](../../media/2bae0579-8907-4d6b-8920-ddd6555897b4.png)
  
5. Tapez pour rechercher ou choisir un utilisateur dans la liste. Sélectionnez **OK** et **Enregistrer**.
    
    ![Type de recherche ou de sélection d’un utilisateur dans la liste](../../media/522919cf-664c-4a25-8076-c51c8c9fbe43.png)

## <a name="related-articles"></a>Articles connexes

[En savoir plus sur les groupes Office 365](https://support.office.com/article/3f780e8e-61aa-4287-830d-ff6209cbc192.aspx)

[Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960)

[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189)
