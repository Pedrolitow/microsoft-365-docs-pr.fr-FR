---
title: Autoriser les membres à envoyer en tant que ou pour le compte d’un groupe
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
ms.custom: admindeeplinkEXCHANGE
search.appverid:
- MET150
ms.assetid: 0ad41414-0cc6-4b97-90fb-06bec7bcf590
recommendations: false
description: Découvrez comment autoriser les membres du groupe à envoyer des e-mails en tant que groupe Microsoft 365 ou à envoyer des e-mails au nom d’un groupe Microsoft 365.
ms.openlocfilehash: 8945d61c3ed855b5415a41b0aa56cb8592645cc0
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67985386"
---
# <a name="allow-members-to-send-as-or-send-on-behalf-of-a-group"></a>Autoriser les membres à envoyer en tant que ou pour le compte d’un groupe

Un membre d’un groupe Microsoft 365 qui a reçu des autorisations **Envoyer en tant que** ou **Envoyer pour le compte** peut envoyer des e-mails en tant que groupe ou au nom du groupe. (Les invités du groupe ne peuvent pas recevoir ces autorisations.)

Cet article explique comment un administrateur général ou Exchange peut définir ces autorisations.
  
Par exemple, si Megan Bowen fait partie du groupe **Formation** Microsoft 365 et dispose des autorisations **Envoyer en tant qu’autorisations** sur le groupe, si elle envoie un e-mail en tant que groupe, elle ressemblera au groupe **de formation** qui a envoyé l’e-mail. 
  
L’autorisation **Envoyer au nom** permet à un utilisateur d’envoyer un e-mail au nom d’un groupe Microsoft 365. Par exemple, si Alex Wilber fait partie du groupe **Marketing** Microsoft 365, dispose d’autorisations **d’envoi en nom** et envoie un e-mail en tant que groupe, l’e-mail semble avoir été envoyé par **Alex Wilber pour le compte de Marketing**.

> [!IMPORTANT]
> Vous pouvez configurer **Envoyer en tant que** ou **envoyer pour le compte** d’un utilisateur donné, mais pas les deux. Si vous configurez les deux, la valeur par défaut est **Envoyer sous**.

> [!NOTE]
> **L’envoi en tant que** et **l’envoi pour le compte** ne sont pas pris en charge sur Outlook pour Mac dans les configurations Exchange hybrides.
    
## <a name="allow-members-to-send-email-as-a-group"></a>Autoriser les membres à envoyer des e-mails en tant que groupe

Cette section explique comment autoriser les utilisateurs à envoyer des e-mails en tant que groupe dans le<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange (EAC)</a> dans Exchange Online.
  
1. Dans le Centre d’administration Exchange, accédez aux <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**groupes**</a> **de destinataires**\>.
    
2. Sélectionnez le groupe que vous souhaitez autoriser les utilisateurs à envoyer. 
    
3. Sélectionnez **Paramètres****Modifier la gestion des** >  délégués.
    
4. Dans la section **Ajouter un délégué**, entrez l’adresse e-mail de l’utilisateur auquel vous **souhaitez accéder.**
  
5. Sélectionnez **Type d’autorisation** **en tant qu’envoi dans** la liste déroulante.

6.  Sélectionnez **Enregistrer les modifications**.
    
    
## <a name="allow-members-to-send-email-on-behalf-of-a-group"></a>Autoriser les membres à envoyer des e-mails au nom d’un groupe

Cette section explique comment autoriser les utilisateurs à envoyer des e-mails au nom d’un groupe dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange (EAC)</a> dans Exchange Online.
  
1. Dans le Centre d’administration Exchange, accédez aux <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**groupes**</a> **de destinataires**\>.
    
2. Sélectionnez le groupe que vous souhaitez autoriser les utilisateurs à envoyer au nom de. 
    
3. Sélectionnez **Paramètres****Modifier la gestion des** >  délégués.
    
4. Dans la section **Ajouter un délégué**, entrez l’adresse e-mail de l’utilisateur auquel vous **souhaitez accéder.**
  
5. Sélectionnez **Le type d’autorisation** **Envoyer pour le compte** dans la liste déroulante.

6.  Sélectionnez **Enregistrer les modifications**.

## <a name="related-articles"></a>Articles connexes

[Envoyer un e-mail à partir ou au nom d’un groupe Microsoft 365](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b)

[Recommandations en matière de planification de la gouvernance de collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[En savoir plus sur les groupes Microsoft 365](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission)

[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup)
