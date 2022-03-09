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
description: Découvrez comment autoriser les membres d’un groupe à envoyer des messages électroniques en tant que Microsoft 365 ou à envoyer du courrier électronique au nom d’Microsoft 365 groupe.
ms.openlocfilehash: 588008669359629f5b59498bb7dbf776112d5408
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63401005"
---
# <a name="allow-members-to-send-as-or-send-on-behalf-of-a-group"></a>Autoriser les membres à envoyer en tant que ou de la part d’un groupe

Un membre d’un groupe Microsoft 365 qui a obtenu des autorisations  Envoyer en tant  que ou Envoyer de la part de peut envoyer des messages électroniques en tant que groupe ou au nom du groupe. (Ces autorisations ne peuvent pas être accordées aux invités du groupe.)

Cet article explique comment un administrateur général ou Exchange peut définir ces autorisations.
  
Par exemple, si Megan Bowen fait partie du groupe **formation Microsoft 365 et** dispose des autorisations Envoyer en  tant que sur le groupe, si elle envoie un e-mail en tant que groupe, il semblera que le  groupe de formation a envoyé le message électronique. 
  
L’autorisation Envoyer de **la part de** permet à un utilisateur d’envoyer des messages électroniques au nom d’Microsoft 365 groupe. Par exemple, si Alex Wilber fait partie du groupe **Marketing** Microsoft 365, dispose des autorisations Envoyer de la  part de et envoie un e-mail en tant que groupe, le message semble avoir été envoyé par **Alex Wilber** pour le compte du service marketing.

> [!IMPORTANT]
> Vous pouvez configurer **Envoyer en tant** que ou **Envoyer de la part d’un** utilisateur donné, mais pas les deux. Si vous configurez les deux, la valeur par défaut **est Envoyer en tant que**.

> [!NOTE]
> **Envoyer en** tant **que et Envoyer de la part de ne** sont pas pris en charge Outlook pour Mac dans les configurations Exchange hybrides.
    
## <a name="allow-members-to-send-email-as-a-group"></a>Autoriser les membres à envoyer des messages électroniques en tant que groupe

Cette section explique comment autoriser les utilisateurs à envoyer des messages électroniques en tant que groupe dans le Centre <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">d’administration Exchange dans</a> Exchange Online.
  
1. Dans le centre Exchange’administration, allez à **Groupes de destinataires**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>
    
2. Sélectionnez le groupe que vous souhaitez autoriser les utilisateurs à envoyer en tant que. 
    
3. **Sélectionnez Paramètres** >  **Gérer les délégués**.
    
4. Dans la section **Ajouter un délégué** , entrez l’adresse e-mail de l’utilisateur que vous souhaitez voir **envoyer en tant qu’accès** .
  
5. **Sélectionnez Type d’autorisation** **Envoyer comme** dans la drop-down.

6.  Sélectionnez **Enregistrer les modifications**.
    
    
## <a name="allow-members-to-send-email-on-behalf-of-a-group"></a>Autoriser les membres à envoyer des courriers électroniques au nom d’un groupe

Cette section explique comment autoriser les utilisateurs à envoyer des messages électroniques au nom d’un groupe dans le Centre d’administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange (EAC)</a> dans Exchange Online.
  
1. Dans le centre Exchange’administration, allez à **Groupes de destinataires**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>
    
2. Sélectionnez le groupe dont vous souhaitez autoriser les utilisateurs à envoyer des messages au nom de. 
    
3. **Sélectionnez Paramètres** >  **Gérer les délégués**.
    
4. Dans la section **Ajouter un délégué** , entrez l’adresse e-mail de l’utilisateur que vous souhaitez voir **envoyer en tant qu’accès** .
  
5. **Sélectionnez Type d’autorisation** **Envoyer de la part de** dans la drop-down.

6.  Sélectionnez **Enregistrer les modifications**.

## <a name="related-articles"></a>Articles connexes

[Envoyer des courriers électroniques à partir d’un groupe de Microsoft 365 ou de la part d’un autre](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b)

[Recommandations en matière de planification de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[En savoir plus sur Microsoft 365 groupes](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission)

[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup)
