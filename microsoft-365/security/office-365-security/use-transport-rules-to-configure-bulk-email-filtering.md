---
title: Utiliser des règles de flux de messagerie pour filtrer les messages électroniques en masse
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
ms.assetid: 2889c82e-fab0-4e85-87b0-b001b2ccd4f7
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à utiliser des règles de flux de messagerie (règles de transport) pour identifier et filtrer les messages en masse (courrier gris) dans Exchange Online Protection (EOP).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fa2c13aed1fd7f9c34872d05693f88577bbbc9c5
ms.sourcegitcommit: 40ec697e27b6c9a78f2b679c6f5a8875dacde943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "44352395"
---
# <a name="use-mail-flow-rules-to-filter-bulk-email-in-eop"></a>Utiliser des règles de flux de courrier pour filtrer les messages électroniques en bloc dans EOP

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online, EOP utilise des stratégies de blocage du courrier indésirable (également appelées stratégies de filtrage du courrier indésirable) pour analyser les messages entrants pour le courrier indésirable et le courrier en nombre (également appelé courrier gris). Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

Si vous souhaitez utiliser davantage d’options pour filtrer les messages en masse, vous pouvez créer des règles de flux de messagerie (également appelées règles de transport) pour rechercher des modèles de texte ou des expressions fréquemment trouvées dans le courrier en nombre et marquer ces messages comme courrier indésirable. Pour plus d’informations sur le courrier en nombre, consultez [la rubrique quelle est la différence entre courrier indésirable et courrier électronique en masse ?](what-s-the-difference-between-junk-email-and-bulk-email.md) et [BCL (Bulk Complaint Level) dans EOP](bulk-complaint-level-values.md).

Cette rubrique explique comment créer ces règles de flux de messagerie dans le centre d’administration Exchange et PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ; environnement de ligne de commande Exchange.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour pouvoir effectuer ces procédures, vous devez disposer des autorisations suivantes :

  - Dans Exchange Online, consultez l’entrée « flux de messagerie » dans [autorisations des fonctionnalités dans Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/feature-permissions).
  
  - Dans EOP autonome, vous avez besoin du rôle de règles de transport, qui est affecté par défaut aux rôles OrganizationManagement, ComplianceManagement et RecordsManagement. Pour plus d’informations, consultez la rubrique [autorisations dans EOP autonome](feature-permissions-in-eop.md) et utiliser le centre d’administration Exchange pour [modifier la liste des membres dans les groupes de rôles](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups).

- Pour ouvrir le centre d’administration Exchange dans Exchange Online, consultez la rubrique [Exchange Admin Center in Exchange Online](https://docs.microsoft.com/Exchange/exchange-admin-center). Pour ouvrir le centre d’administration Exchange en mode autonome EOP, consultez la rubrique [Exchange Admin Center in standalone EOP](exchange-admin-center-in-exchange-online-protection-eop.md).

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-eop/connect-to-exchange-online-protection-powershell).

- Pour plus d’informations sur les règles de flux de messagerie dans Exchange Online et dans la version autonome d’EOP, consultez les rubriques suivantes :

  - [Règles de flux de messagerie (règles de transport) dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)

  - [Conditions de règle de flux de messagerie et exceptions (prédicats) dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions)

  - [Actions de règle de flux de messagerie dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)

- La liste des mots et des modèles de texte utilisés pour identifier le courrier en nombre dans les exemples n’est pas exhaustive ; vous pouvez ajouter et supprimer des entrées si nécessaire. Toutefois, ils constituent un point de départ approprié.

- La recherche de mots clés ou de modèles de texte dans l’objet ou dans d’autres champs d’en-tête du message est effectuée *après* que le codage utilisé avec la méthode MIME pour transmettre le message binaire entre les serveurs SMTP a été décodé en texte ASCII. Vous ne pouvez pas utiliser de conditions ou d’exceptions pour rechercher les valeurs codées brutes (en règle générale, en base 64) dans l’objet ou d’autres champs d’en-tête des messages.

- Les procédures suivantes marquent un message en bloc comme courrier indésirable pour l’ensemble de votre organisation. Toutefois, vous pouvez ajouter une autre condition pour appliquer ces règles à des destinataires spécifiques, de sorte que vous pouvez utiliser un filtrage agressif sur quelques utilisateurs hautement ciblés, tandis que les autres utilisateurs (qui obtiennent principalement le courrier en nombre auquel ils étaient inscrits) ne sont pas concernés.

## <a name="use-the-eac-to-create-mail-flow-rules-that-filter-bulk-email"></a>Utiliser le centre d’administration Exchange pour créer des règles de flux de messagerie qui filtrent les messages électroniques en masse

1. Dans le CAE, accédez à **Flux de messagerie** \> **Règles**.

2. Cliquez sur **Ajouter** ![ une icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) , puis sélectionnez **créer une nouvelle règle**.

3. Dans la page **Nouvelle règle** qui s'ouvre, configurez les paramètres suivants :

   - **Nom**: entrez un nom unique et descriptif pour la règle.

   - Cliquez sur **Autres options**.

   - **Appliquer cette règle si**: configurez l’un des paramètres suivants pour rechercher du contenu dans les messages à l’aide d’expressions régulières (Regex) ou de mots ou d’expressions :

     - **L’objet ou le corps** \> l' **objet ou le corps correspond à ces modèles de texte**: dans la boîte de dialogue **spécifier des mots ou des expressions** qui s’affiche, entrez l’une des valeurs suivantes, puis cliquez sur **Ajouter** une ![ icône ](../../media/ITPro-EAC-AddIcon.png) et répétez l’opération jusqu’à ce que vous entriez toutes les valeurs.

       - `If you are unable to view the content of this email\, please`
       - `\>(safe )?unsubscribe( here)?\</a\>`
       - `If you do not wish to receive further communications like this\, please`
       - `\<img height\="?1"? width\="?1"? sr\c=.?http\://`
       - `To stop receiving these+emails\:http\://`
       - `To unsubscribe from \w+ (e\-?letter|e?-?mail|newsletter)`
       - `no longer (wish )?(to )?(be sent|receive) w+ email`
       - `If you are unable to view the content of this email\, please click here`
       - `To ensure you receive (your daily deals|our e-?mails)\, add`
       - `If you no longer wish to receive these emails`
       - `to change your (subscription preferences|preferences or unsubscribe)`
       - `click (here to|the) unsubscribe`

      Pour modifier une entrée, sélectionnez-la et cliquez sur **modifier** l' ![ icône modifier ](../../media/ITPro-EAC-EditIcon.png) . Pour supprimer une entrée, sélectionnez-la et cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/ITPro-EAC-DeleteIcon.png) .

       Lorsque vous avez terminé, cliquez sur **OK**.

     - **L’objet ou le corps** \> **Subject ou Body comprend l’un des mots**suivants : dans la boîte de dialogue **spécifier des mots ou des expressions** qui s’affiche, entrez l’une des valeurs suivantes, puis cliquez sur **Ajouter** une ![ icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) et répétez l’opération jusqu’à ce que vous ayez entré toutes les valeurs.

       - `to change your preferences or unsubscribe`
       - `Modify email preferences or unsubscribe`
       - `This is a promotional email`
       - `You are receiving this email because you requested a subscription`
       - `click here to unsubscribe`
       - `You have received this email because you are subscribed`
       - `If you no longer wish to receive our email newsletter`
       - `to unsubscribe from this newsletter`
       - `If you have trouble viewing this email`
       - `This is an advertisement`
       - `you would like to unsubscribe or change your`
       - `view this email as a webpage`
       - `You are receiving this email because you are subscribed`

      Pour modifier une entrée, sélectionnez-la et cliquez sur **modifier** l' ![ icône modifier ](../../media/ITPro-EAC-EditIcon.png) . Pour supprimer une entrée, sélectionnez-la et cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/ITPro-EAC-DeleteIcon.png) .

       Lorsque vous avez terminé, cliquez sur **OK**.

   - **Procédez comme suit**: sélectionnez **modifier les propriétés du message** \> **définir le seuil de probabilité de courrier indésirable (SCL)**. Dans la boîte de dialogue spécifier la valeur **SCL** qui s’affiche, configurez l’un des paramètres suivants :

     - Pour marquer les messages comme **courrier indésirable**, sélectionnez **6**. L’action que vous avez configurée pour le filtrage du **courrier indésirable** dans vos stratégies de blocage du courrier indésirable est appliquée aux messages (la valeur par défaut est **déplacer le message vers le dossier courrier indésirable**).

     - Pour marquer les messages comme **courriers indésirables à niveau de confiance élevé** , sélectionnez **9**. L’action que vous avez configurée pour le filtrage du **courrier indésirable à niveau de confiance élevé** est appliquée aux messages dans vos stratégies de blocage du courrier indésirable (la valeur par défaut est **déplacer le message vers le dossier courrier indésirable**).

    Pour plus d’informations sur les valeurs SCL, voir [taux de probabilité de courrier indésirable (SCL) dans EOP](spam-confidence-levels.md).

   Lorsque vous avez terminé, cliquez sur **Enregistrer** .

## <a name="use-powershell-to-create-mail-flow-rules-that-filter-bulk-email"></a>Utiliser PowerShell pour créer des règles de flux de messagerie qui filtrent les messages électroniques en masse

Utilisez la syntaxe suivante pour créer une des règles de flux de messagerie ou les deux (expressions régulières et mots) :

```powershell
New-TransportRule -Name "<UniqueName>" [-SubjectOrBodyMatchesPatterns "<RegEx1>","<RegEx2>"...] [-SubjectOrBodyContainsWords "<WordOrPrhase1>","<WordOrPhrase2>"...] -SetSCL <6 | 9>
```

Cet exemple crée une nouvelle règle nommée « Bulk Email Filtering-RegEx » qui utilise la même liste d’expressions régulières que celle décrite plus haut dans la rubrique pour définir les messages comme **courrier indésirable**.

```powershell
New-TransportRule -Name "Bulk email filtering - RegEx" -SubjectOrBodyMatchesPatterns "If you are unable to view the content of this email\, please","\>(safe )?unsubscribe( here)?\</a\>","If you do not wish to receive further communications like this\, please","\<img height\="?1"? width\="?1"? sr\c=.?http\://","To stop receiving these+emails\:http\://","To unsubscribe from \w+ (e\-?letter|e?-?mail|newsletter)","no longer (wish )?(to )?(be sent|receive) w+ email","If you are unable to view the content of this email\, please click here","To ensure you receive (your daily deals|our e-?mails)\, add","If you no longer wish to receive these emails","to change your (subscription preferences|preferences or unsubscribe)","click (here to|the) unsubscribe"... -SetSCL 6
```

Cet exemple crée une règle nommée « filtrage des courriers électroniques en bloc » qui utilise la même liste de mots que précédemment dans la rubrique pour définir les messages comme **courrier indésirable à niveau de confiance élevé**.

```powershell
New-TransportRule -Name "Bulk email filtering - Words" -SubjectOrBodyContainsWords "to change your preferences or unsubscribe","Modify email preferences or unsubscribe","This is a promotional email","You are receiving this email because you requested a subscription","click here to unsubscribe","You have received this email because you are subscribed","If you no longer wish to receive our email newsletter","to unsubscribe from this newsletter","If you have trouble viewing this email","This is an advertisement","you would like to unsubscribe or change your","view this email as a webpage","You are receiving this email because you are subscribed" -SetSCL 9
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TransportRule](https://docs.microsoft.com/powershell/module/exchange/new-transportrule).

## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez configuré les règles de flux de messagerie pour filtrer les messages électroniques en masse, effectuez l’une des opérations suivantes :

- Dans le centre d’administration Exchange, accédez à règles de **flux de messagerie** \> **Rules** \> Sélectionnez la règle \> , cliquez sur **modifier** ![ l’icône d’édition ](../../media/ITPro-EAC-EditIcon.png) et vérifiez les paramètres.

- Dans PowerShell, remplacez \< nom \> de la règle par le nom de la règle, puis exécutez la commande suivante pour vérifier les paramètres :

  ```powershell
  Get-TransportRule -Identity "<Rule Name>" | Format-List
  ```

- À partir d’un compte externe, envoyez un message de test à un destinataire affecté qui contient l’une des expressions ou des modèles de texte, puis vérifiez les résultats.
