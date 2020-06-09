---
title: Utiliser des règles de transport pour bloquer le signalement des courriers indésirables à Microsoft
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 8401f520-8e7c-467b-9e06-4a9fdb2ba548
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à utiliser des règles de flux de messagerie (également appelées règles de transport) pour recevoir des copies de messages que les utilisateurs signalent à Microsoft.
ms.openlocfilehash: d50a0f02dd3d65b8576261fc2332aba86d55df56
ms.sourcegitcommit: 73b2426001dc5a3f4b857366ef51e877db549098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "44616789"
---
# <a name="use-mail-flow-rules-to-see-what-your-users-are-reporting-to-microsoft"></a>Utiliser des règles de transport pour bloquer le signalement des courriers indésirables à Microsoft

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online, les utilisateurs peuvent signaler des messages à Microsoft pour analyse, comme décrit dans la section [rapports de messages et de fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

Vous pouvez créer une règle de flux de messagerie (également appelée règle de transport) qui recherche les messages que les utilisateurs signalent à Microsoft, et vous pouvez configurer les destinataires CCI de sorte qu’ils reçoivent des copies de ces messages signalés.

Vous pouvez créer la règle de flux de messagerie dans le centre d’administration Exchange et PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ; environnement de ligne de commande Exchange (PowerShell) autonome pour les organisations sans boîtes aux lettres Exchange Online).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour pouvoir effectuer ces procédures, vous devez disposer d’autorisations dans Exchange Online ou EOP. Plus précisément, vous devez disposer du rôle **de règles de transport** , qui est affecté aux rôles de gestion de l' **organisation**, de gestion de **la conformité**et de **gestion des enregistrements** par défaut. Pour plus d’informations, voir [Gérer les groupes de rôles dans Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/role-groups).

- Pour ouvrir le centre d’administration Exchange, consultez la rubrique [Centre d’administration Exchange dans Exchange Online](https://docs.microsoft.com/Exchange/exchange-admin-center) ou [Centre d’administration Exchange dans la version autonome EOP](exchange-admin-center-in-exchange-online-protection-eop.md).

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Pour plus d’informations sur les règles de flux de messagerie dans Exchange Online et dans la version autonome d’EOP, consultez les rubriques suivantes :

  - [Règles de flux de messagerie (règles de transport) dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)

  - [Conditions de règle de flux de messagerie et exceptions (prédicats) dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions)

  - [Actions de règle de flux de messagerie dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)

## <a name="use-the-eac-to-create-a-mail-flow-rule-to-receive-copies-of-reported-messages"></a>Utiliser le centre d’administration Exchange pour créer une règle de flux de messagerie pour recevoir des copies des messages signalés

1. Dans le CAE, accédez à **Flux de messagerie** \> **Règles**.

2. Cliquez sur **Ajouter** ![ une icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) , puis sélectionnez **créer une nouvelle règle**.

3. Dans la page **Nouvelle règle** qui s'ouvre, configurez les paramètres suivants :

   - **Nom**: entrez un nom unique et descriptif pour la règle. Par exemple, les messages CCI signalés à Microsoft.

   - Cliquez sur **Autres options**.

   - **Appliquer cette règle si**: sélectionnez **l’adresse du destinataire** contient l’un \> **des mots**suivants : dans la boîte de dialogue **spécifier des mots ou des expressions** qui s’affiche, entrez l’une des valeurs suivantes, puis cliquez sur **Ajouter** une ![ icône ](../../media/ITPro-EAC-AddIcon.png) et répétez l’opération jusqu’à ce que vous ayez entré toutes les valeurs.

     - `junk@office365.microsoft.com`
     - `abuse@messaging.microsoft.com`
     - `phish@office365.microsoft.com`
     - `false_positive@messaging.microsoft.com`

     Pour modifier une entrée, sélectionnez-la et cliquez sur **modifier** l' ![ icône modifier ](../../media/ITPro-EAC-EditIcon.png) . Pour supprimer une entrée, sélectionnez-la et cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/ITPro-EAC-DeleteIcon.png) .

     Lorsque vous avez terminé, cliquez sur **OK**.

   - **Procédez comme suit**: sélectionnez **Ajouter des destinataires** \> **dans le champ CCI**. Dans la boîte de dialogue qui s’affiche, recherchez et sélectionnez les destinataires que vous souhaitez ajouter. Lorsque vous avez terminé, cliquez sur **OK**.

4. Vous pouvez effectuer des sélections supplémentaires pour auditer la règle, tester la règle, activer la règle pendant une période spécifique, ainsi que d’autres paramètres. Nous vous recommandons de tester la règle avant de l’appliquer.

5. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-powershell-to-create-a-mail-flow-rule-to-receive-copies-of-reported-messages"></a>Utiliser PowerShell pour créer une règle de flux de messagerie pour recevoir des copies des messages signalés

Cet exemple crée une règle de flux de messagerie nommée CCI messages signalés à Microsoft qui recherche les messages électroniques signalés à Microsoft à l’aide des méthodes décrites dans cette rubrique, et ajoute les utilisateurs laura@contoso.com et julia@contoso.com en tant que destinataires CCI.

```powershell
New-TransportRule -Name "Bcc Messages Reported to Microsoft" -RecipientAddressContainsWords "junk@office365.microsoft.com","abuse@messaging.microsoft.com","phish@office365.microsoft.com","false_positive@messaging.microsoft.com" -BlindCopyTo "laura@contoso.com","julia@contoso.com".
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TransportRule](https://docs.microsoft.com/powershell/module/exchange/new-transportrule).

## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez configuré des règles de flux de messagerie pour recevoir des copies de messages signalés, effectuez l’une des opérations suivantes :

- Dans le centre d’administration Exchange, accédez à règles de **flux de messagerie** \> **Rules** \> Sélectionnez la règle \> , cliquez sur **modifier** ![ l’icône d’édition ](../../media/ITPro-EAC-EditIcon.png) et vérifiez les paramètres.

- Dans PowerShell, exécutez la commande suivante pour vérifier les paramètres :

  ```powershell
  Get-TransportRule -Identity "Bcc Messages Reported to Microsoft" | Format-List
  ```

- Envoyez un message de test à l’une des adresses de messagerie de création de rapports et vérifiez les résultats.
