---
title: Utiliser des règles de transport pour bloquer le signalement des courriers indésirables à Microsoft
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 8401f520-8e7c-467b-9e06-4a9fdb2ba548
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à utiliser des règles de flux de messagerie (également appelées règles de transport) pour recevoir des copies de messages que les utilisateurs signalent à Microsoft.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 40e87fec3bfd8ed4402713ca7ec45499bb50c68e
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50287604"
---
# <a name="use-mail-flow-rules-to-see-what-your-users-are-reporting-to-microsoft"></a>Utiliser des règles de flux de courriers pour afficher les comptes-rendus envoyés par les utilisateurs à Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou dans des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, il existe plusieurs façons pour les utilisateurs de signaler des messages à Microsoft pour analyse, comme décrit dans La description du rapport des messages et des fichiers à [Microsoft.](report-junk-email-messages-to-microsoft.md)

Vous pouvez créer une règle de flux de messagerie (également appelée règle de transport) qui recherche les messages que les utilisateurs signalent à Microsoft, et vous pouvez configurer les destinataires Bcc pour recevoir des copies de ces messages signalés.

Vous pouvez créer la règle de flux de messagerie dans le Centre d’administration Exchange (CAE) et PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Des autorisations doivent vous être attribuées dans Exchange Online ou Exchange Online Protection avant de pouvoir suivre les procédures de cet article. Plus précisément, vous avez besoin du rôle Règles de **transport,** qui est  attribué par défaut aux groupes de rôles Gestion de l’organisation, Gestion de la conformité **(administrateurs** globaux) et Gestion des enregistrements.

  Pour plus d’informations, voir les rubriques suivantes :

  - [Autorisations dans Exchange Online](https://docs.microsoft.com/exchange/permissions-exo/permissions-exo)
  - [Autorisations dans EOP autonome](feature-permissions-in-eop.md)
  - [Utiliser le EAC pour modifier la liste des membres dans les groupes de rôles](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups)

- Pour ouvrir le CENTRE d’administration Exchange dans Exchange Online, consultez le [Centre d’administration Exchange dans Exchange Online.](https://docs.microsoft.com/Exchange/exchange-admin-center) Pour ouvrir le CAE dans EOP autonome, consultez le Centre d’administration [Exchange dans EOP autonome.](exchange-admin-center-in-exchange-online-protection-eop.md)

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Pour plus d’informations sur les règles de flux de messagerie dans Exchange Online et EOP autonome, consultez les rubriques suivantes :
  - [Règles de flux de messagerie (règles de transport) dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)
  - [Conditions de règle de flux de messagerie et exceptions (prédicats) dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions)
  - [Actions de règle de flux de courrier dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)

## <a name="use-the-eac-to-create-a-mail-flow-rule-to-receive-copies-of-reported-messages"></a>Utiliser le EAC pour créer une règle de flux de messagerie afin de recevoir des copies des messages signalés

1. Dans le CAE, accédez à **Flux de messagerie** \> **Règles**.

2. Cliquez **sur Ajouter** une icône ![ ](../../media/ITPro-EAC-AddIcon.png) Ajouter, puis **sélectionnez Créer une règle.**

3. Dans la page **Nouvelle règle** qui s'ouvre, configurez les paramètres suivants :

   - **Nom**: entrez un nom unique et descriptif pour la règle. Par exemple, messages Bcc signalés à Microsoft.

   - Cliquez sur **Autres options**.

   - Appliquez cette règle  si : Sélectionnez L’adresse du destinataire inclut l’un de ces mots : dans la boîte de dialogue Spécifier des mots ou des expressions qui s’affiche, entrez l’une des valeurs suivantes, cliquez sur Ajouter une icône, puis répétez \>   l’utilisation jusqu’à ce que vous avez entré toutes les **valeurs.** ![ ](../../media/ITPro-EAC-AddIcon.png)

     - `junk@office365.microsoft.com`
     - `abuse@messaging.microsoft.com`
     - `phish@office365.microsoft.com`
     - `not_junk@office365.microsoft.com`

     Pour modifier une entrée, sélectionnez-la et cliquez sur **Modifier** ![ ](../../media/ITPro-EAC-EditIcon.png) l’icône Modifier. Pour supprimer une entrée, sélectionnez-la et cliquez **sur Supprimer** ![ l’icône ](../../media/ITPro-EAC-DeleteIcon.png) .

     Lorsque vous avez terminé, cliquez sur **OK**.

   - **Pour ce faire,** **sélectionnez Ajouter des destinataires** \> **dans la zone Bcc.** Dans la boîte de dialogue qui s’affiche, recherchez et sélectionnez les destinataires à ajouter. Lorsque vous avez terminé, cliquez sur **OK**.

4. Vous pouvez effectuer des sélections supplémentaires pour auditer la règle, la tester, activer la règle pendant une période spécifique et d’autres paramètres. Nous vous recommandons de tester la règle avant de l’appliquer.

5. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-powershell-to-create-a-mail-flow-rule-to-receive-copies-of-reported-messages"></a>Utiliser PowerShell pour créer une règle de flux de messagerie afin de recevoir des copies des messages signalés

Cet exemple crée une règle de flux de messagerie nommée Bcc Messages signalés à Microsoft qui recherche les messages électroniques signalés à Microsoft à l’aide des méthodes décrites dans cet article et ajoute les utilisateurs laura@contoso.com et julia@contoso.com en tant que destinataires Bcc.

```powershell
New-TransportRule -Name "Bcc Messages Reported to Microsoft" -RecipientAddressContainsWords "junk@office365.microsoft.com","abuse@messaging.microsoft.com","phish@office365.microsoft.com","false_positive@messaging.microsoft.com" -BlindCopyTo "laura@contoso.com","julia@contoso.com".
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TransportRule](https://docs.microsoft.com/powershell/module/exchange/new-transportrule).

## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez configuré une règle de flux de messagerie pour recevoir des copies des messages signalés, appliquez l’une des étapes suivantes :

- Dans le EAC, sélectionnez Règles de **flux** de messagerie et sélectionnez l’icône Modifier, puis \>  \> \> vérifiez les  ![ ](../../media/ITPro-EAC-EditIcon.png) paramètres.

- Dans PowerShell, exécutez la commande suivante pour vérifier les paramètres :

  ```powershell
  Get-TransportRule -Identity "Bcc Messages Reported to Microsoft" | Format-List
  ```

- Envoyez un message de test à l’une des adresses e-mail de rapport et vérifiez les résultats.
