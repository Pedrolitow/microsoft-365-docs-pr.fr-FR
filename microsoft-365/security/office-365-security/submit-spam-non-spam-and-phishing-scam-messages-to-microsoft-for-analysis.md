---
title: Envoi manuel de messages à Microsoft pour analyse
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: dad30e2f-93fe-4d21-9a36-21c87ced85c1
ms.collection:
- M365-security-compliance
description: 'Vous et vos utilisateurs pouvez soumettre des messages indésirables faux positifs et faux positifs à Microsoft pour analyse. '
ms.openlocfilehash: f6dbd808fac54ae273c21773bf8caeabce09b7fb
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43631240"
---
# <a name="manually-submit-messages-to-microsoft-for-analysis"></a>Envoi manuel de messages à Microsoft pour analyse

> [!NOTE]
> Si vous êtes administrateur d’une organisation Microsoft 365 avec des boîtes aux lettres Exchange Online, nous vous recommandons d’utiliser le portail d’envoi du centre de sécurité & conformité. Pour plus d’informations, consultez la rubrique [utiliser la soumission de l’administrateur pour envoyer des courriers indésirables, des hameçons, des URL et des fichiers à Microsoft](admin-submission.md).

Il peut être frustrant lorsque les utilisateurs de votre organisation reçoivent des courriers indésirables (spam) ou des messages de hameçonnage dans leur boîte de réception, ou s’ils ne reçoivent pas de message électronique légitime, car il est marqué comme courrier indésirable. Nous ajustons constamment les filtres de courrier indésirable pour qu’ils soient plus précis.

Vous et vos utilisateurs pouvez aider ce processus en soumettant des faux positifs (courrier électronique marqué comme incorrect), des faux négatifs (courrier incorrect) et des messages de hameçonnage à Microsoft pour analyse.

> [!NOTE]
> En raison du volume élevé des envois que nous recevons, il se peut que nous ne parvenons pas à répondre à toutes les demandes d’analyse.

## <a name="submit-false-negatives-to-microsoft"></a>Soumettre des faux négatifs à Microsoft

> [!TIP]
> Au lieu d’utiliser les procédures suivantes pour signaler les faux négatifs, les utilisateurs dans Outlook et Outlook sur le Web (anciennement appelé Outlook Web App) peuvent utiliser le complément de message de rapport pour Microsoft Outlook. Pour plus d’informations sur l’installation et l’utilisation de cet outil, voir [activer le complément de message de rapport](enable-the-report-message-add-in.md).

Si vous recevez un message transmis par le biais du filtrage du courrier indésirable qui aurait dû être identifié comme courrier indésirable ou hameçonnage, vous pouvez envoyer le message aux équipes analyse du courrier indésirable et Microsoft Phishing Analysis, selon le cas. Les analystes examineront le message et l’ajouteront aux filtres à l’échelle du service s’il répond aux critères de classification.

1. Créez un message électronique vide avec l’un des destinataires suivants :

   - **Courrier indésirable**:`junk@office365.microsoft.com`

   - **Hameçonnage**:`phish@office365.microsoft.com`

2. Faites glisser et déposez le message de courrier indésirable dans le nouveau message. Cette opération permet d’enregistrer le message de courrier indésirable ou de hameçonnage en tant que pièce jointe dans le nouveau message. Ne copiez pas et ne collez pas le contenu du message ou transférez le message (nous avons besoin du message d’origine pour pouvoir inspecter les en-têtes des messages).

   > [!NOTE]
   > <ul><li>Vous pouvez joindre plusieurs messages dans le nouveau message. Assurez-vous que tous les messages sont du même type : les messages de hameçonnage ou les messages électroniques de courrier indésirable.</li><li>Laissez le corps du message vide.</li><li>Utilisez les formats. MSG (format Outlook par défaut) ou. eml (Outlook sur le format Web par défaut) pour les messages joints.</li></ul>

3. Lorsque vous avez terminé, cliquez sur **Envoyer**.

> [!TIP]
> Les administrateurs disposent de différentes manières de bloquer des messages spécifiques identifiés comme courrier indésirable. Pour plus d’informations, consultez la rubrique [créer des listes d’expéditeurs bloqués dans Office 365](create-block-sender-lists-in-office-365.md).

## <a name="submit-false-positives-to-microsoft"></a>Soumettre des faux positifs à Microsoft

> [!TIP]
> Au lieu d’utiliser les procédures suivantes pour signaler les faux positifs, les utilisateurs dans Outlook et Outlook sur le Web peuvent utiliser le complément de message de rapport pour Microsoft Outlook. Pour plus d’informations sur l’installation et l’utilisation de cet outil, voir [activer le complément de message de rapport](enable-the-report-message-add-in.md).

Si un message a été identifié de manière incorrecte comme courrier indésirable, vous pouvez envoyer le message à l’équipe d’analyse du courrier indésirable de Microsoft. Les analystes évaluent le message et (en fonction des résultats de l’analyse) les filtres à l’échelle du service peuvent être ajustés pour autoriser le message.

1. Créez un message électronique vide avec `not_junk@office365.microsoft.com` comme destinataire :

2. Faites glisser et déposez le message qui a été identifié dans le nouveau message. Cette opération permet d’enregistrer le message identifié de manière indéterminée en tant que pièce jointe dans le nouveau message. Ne copiez pas et ne collez pas le contenu du message ou transférez le message (nous avons besoin du message d’origine pour pouvoir inspecter les en-têtes des messages).

   > [!NOTE]
   > <ul><li>Vous pouvez joindre plusieurs messages dans le nouveau message. Assurez-vous que tous les messages sont du même type : les messages de hameçonnage ou les messages électroniques de courrier indésirable.</li><li>Laissez le corps du message vide.</li><li>Utilisez les formats. MSG (format Outlook par défaut) ou. eml (Outlook sur le format Web par défaut) pour les messages joints.</li></ul>

3. Lorsque vous avez terminé, cliquez sur **Envoyer**.

> [!TIP]
> Les administrateurs disposent de différentes manières d’autoriser des messages spécifiques à ignorer le filtrage du courrier indésirable. Pour plus d’informations, consultez la rubrique [créer des listes d’expéditeurs approuvés dans Office 365](create-safe-sender-lists-in-office-365.md).

## <a name="create-a-mail-flow-rule-to-receive-copies-of-messages-that-are-reported-to-microsoft"></a>Créer une règle de flux de messagerie pour recevoir des copies des messages signalés à Microsoft

Vous pouvez créer une règle de flux de messagerie (également appelée règle de transport) qui recherche les messages électroniques envoyés à Microsoft à l’aide des méthodes décrites dans cette rubrique, et vous pouvez configurer les destinataires CCI de sorte qu’ils reçoivent des copies de ces messages signalés.

Vous pouvez créer la règle de flux de messagerie dans le centre d’administration Exchange et PowerShell (Exchange Online PowerShell pour les clients Microsoft 365 ; Exchange Online Protection PowerShell pour les clients EOP autonomes).

### <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour pouvoir effectuer ces procédures, vous devez disposer d’autorisations dans Exchange Online. Plus précisément, vous devez disposer du rôle **de règles de transport** , qui est affecté aux rôles de gestion de l' **organisation**, de gestion de **la conformité**et de **gestion des enregistrements** par défaut. Pour plus d’informations, voir [Gérer les groupes de rôles dans Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/role-groups).

- Pour ouvrir le centre d’administration Exchange dans Exchange Online, consultez la rubrique [Exchange Admin Center in Exchange Online](https://docs.microsoft.com/Exchange/exchange-admin-center).

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection autonome, voir [Se connecter à PowerShell d’Exchange Online Protection](https://docs.microsoft.com/powershell/exchange/exchange-eop/connect-to-exchange-online-protection-powershell).

- Pour plus d’informations sur les règles de flux de messagerie dans Exchange Online et dans la version autonome d’EOP, consultez les rubriques suivantes :

  - [Règles de flux de messagerie (règles de transport) dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)

  - [Conditions de règle de flux de messagerie et exceptions (prédicats) dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions)

  - [Actions de règle de flux de messagerie dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)

### <a name="use-the-eac-to-create-a-mail-flow-rule-to-receive-copies-of-reported-messages"></a>Utiliser le centre d’administration Exchange pour créer une règle de flux de messagerie pour recevoir des copies des messages signalés

1. Dans le CAE, accédez à **Flux de messagerie** \> **Règles**.

2. Cliquez sur **Ajouter** ![une](../../media/ITPro-EAC-AddIcon.png) icône Ajouter, puis sélectionnez **créer une nouvelle règle**.

3. Dans la page **Nouvelle règle** qui s'ouvre, configurez les paramètres suivants :

   - **Nom**: entrez un nom unique et descriptif pour la règle. Par exemple, les messages CCI signalés à Microsoft.

   - Cliquez sur **Autres options**.

   - **Appliquer cette règle si**: sélectionnez **l’adresse du destinataire** \> **contient l’un des mots**suivants : dans la boîte de dialogue **spécifier des mots ou des expressions** qui s’affiche, entrez l’une des valeurs suivantes, puis cliquez sur **Ajouter** ![une icône](../../media/ITPro-EAC-AddIcon.png)et répétez l’opération jusqu’à ce que vous ayez entré toutes les valeurs.

     - `junk@office365.microsoft.com`
     - `abuse@messaging.microsoft.com`
     - `phish@office365.microsoft.com`
     - `false_positive@messaging.microsoft.com`

     Pour modifier une entrée, sélectionnez-la et **Edit** ![cliquez sur modifier](../../media/ITPro-EAC-EditIcon.png)l’icône modifier. Pour supprimer une entrée, sélectionnez-la et **Remove** ![cliquez sur supprimer](../../media/ITPro-EAC-DeleteIcon.png)l’icône Supprimer.

     Lorsque vous avez terminé, cliquez sur **OK**.

   - **Procédez comme suit**: sélectionnez **Ajouter des destinataires** \> **dans le champ CCI**. Dans la boîte de dialogue qui s’affiche, recherchez et sélectionnez les destinataires que vous souhaitez ajouter. Lorsque vous avez terminé, cliquez sur **OK**.

4. Vous pouvez effectuer des sélections supplémentaires pour auditer la règle, tester la règle, activer la règle pendant une période spécifique, ainsi que d’autres paramètres. Nous vous recommandons de tester la règle avant de l’appliquer.

5. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

### <a name="use-powershell-to-create-a-mail-flow-rule-to-receive-copies-of-reported-messages"></a>Utiliser PowerShell pour créer une règle de flux de messagerie pour recevoir des copies des messages signalés

Cet exemple crée une règle de flux de messagerie nommée CCI messages signalés à Microsoft qui recherche les messages électroniques signalés à Microsoft à l’aide des méthodes décrites dans cette rubrique, et ajoute les utilisateurs laura@contoso.com et julia@contoso.com en tant que destinataires CCI.

```powershell
New-TransportRule -Name "Bcc Messages Reported to Microsoft" -RecipientAddressContainsWords "junk@office365.microsoft.com","abuse@messaging.microsoft.com","phish@office365.microsoft.com","false_positive@messaging.microsoft.com" -BlindCopyTo "laura@contoso.com","julia@contoso.com".
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TransportRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-transportrule).

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez configuré des règles de flux de messagerie pour recevoir des copies de messages signalés, effectuez l’une des opérations suivantes :

- Dans le centre d’administration Exchange, accédez à **règles** \> de **flux** \> de **Edit** ![messagerie sélectionnez la](../../media/ITPro-EAC-EditIcon.png)règle \> , cliquez sur modifier l’icône d’édition et vérifiez les paramètres.

- Dans PowerShell, exécutez la commande suivante pour vérifier les paramètres :

  ```powershell
  Get-TransportRule -Identity "Bcc Messages Reported to Microsoft" | Format-List
  ```

- Envoyez un message de test à l’une des adresses de messagerie de création de rapports et vérifiez les résultats.
