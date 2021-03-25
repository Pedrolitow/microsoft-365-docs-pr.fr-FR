---
title: Utiliser des règles de flux de messagerie pour filtrer les messages électroniques en masse
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
ms.assetid: 2889c82e-fab0-4e85-87b0-b001b2ccd4f7
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à utiliser des règles de flux de messagerie (règles de transport) pour identifier et filtrer le courrier en nombre (courrier gris) dans Exchange Online Protection (EOP).
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c86f229d6c7371854878a67937cc38374ed00961
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204443"
---
# <a name="use-mail-flow-rules-to-filter-bulk-email-in-eop"></a>Utiliser des règles de flux de courriers pour filtrer les e-mails en bloc dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 ayant des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, EOP utilise des stratégies anti-courrier indésirable (également appelées stratégies de filtrage du courrier indésirable ou stratégies de filtrage de contenu) pour analyser les messages entrants à la recherche de courrier indésirable et de courrier en masse (également appelé courrier gris). Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

Si vous souhaitez plus d’options pour filtrer le courrier en nombre, vous pouvez créer des règles de flux de messagerie (également appelées règles de transport) pour rechercher des modèles de texte ou des expressions fréquemment trouvés dans les messages en nombre, et marquer ces messages comme courrier indésirable. Pour plus [d’informations](what-s-the-difference-between-junk-email-and-bulk-email.md) sur le courrier en nombre, voir Quelle est la différence entre le courrier indésirable et le courrier en masse ? et le niveau de réclamation en bloc [(BCL) dans EOP](bulk-complaint-level-values.md).

Cette rubrique explique comment créer ces règles de flux de messagerie dans le Centre d’administration Exchange (CAE) et PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Des autorisations doivent vous être attribuées dans Exchange Online ou Exchange Online Protection avant de pouvoir suivre les procédures de cet article. Plus précisément, vous avez besoin du rôle Règles de **transport,** qui est  attribué par défaut aux groupes de rôles Gestion de l’organisation, Gestion de la conformité **(administrateurs** globaux) et Gestion des enregistrements.

  Pour plus d’informations, voir les rubriques suivantes :

  - [Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo)
  - [Autorisations dans EOP autonome](feature-permissions-in-eop.md)
  - [Utiliser le EAC pour modifier la liste des membres dans les groupes de rôles](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups)

- Pour ouvrir le CENTRE d’administration Exchange dans Exchange Online, consultez le [Centre d’administration Exchange dans Exchange Online.](/Exchange/exchange-admin-center) Pour ouvrir le CAE dans EOP autonome, consultez le Centre [d’administration Exchange dans EOP autonome.](exchange-admin-center-in-exchange-online-protection-eop.md)

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Pour plus d’informations sur les règles de flux de messagerie dans Exchange Online et EOP autonome, consultez les rubriques suivantes :

  - [Règles de flux de messagerie (règles de transport) dans Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)

  - [Conditions de règle de flux de messagerie et exceptions (prédicats) dans Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions)

  - [Actions de règle de flux de courrier dans Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)

- La liste des mots et des modèles de texte utilisés pour identifier les messages en nombre dans les exemples n’est pas exhaustive . vous pouvez ajouter et supprimer des entrées si nécessaire. Toutefois, ils sont un bon point de départ.

- La recherche de mots clés ou de modèles de texte dans l’objet ou dans d’autres champs d’en-tête du message est effectuée *après* que le codage utilisé avec la méthode MIME pour transmettre le message binaire entre les serveurs SMTP a été décodé en texte ASCII. Vous ne pouvez pas utiliser de conditions ou d’exceptions pour rechercher les valeurs codées brutes (en règle générale, en base 64) dans l’objet ou d’autres champs d’en-tête des messages.

- Les procédures suivantes marquent un message en masse comme courrier indésirable pour l’ensemble de votre organisation. Toutefois, vous pouvez ajouter une autre condition pour appliquer ces règles uniquement à des destinataires spécifiques, afin que vous pouvez utiliser un filtrage agressif sur quelques utilisateurs hautement ciblés, tandis que le reste de vos utilisateurs (qui obtiennent principalement le courrier en nombre pour qui ils se sont inscrits) ne sont pas touchés.

## <a name="use-the-eac-to-create-mail-flow-rules-that-filter-bulk-email"></a>Utiliser le EAC pour créer des règles de flux de messagerie qui filtrent les messages électroniques en masse

1. Dans le CAE, accédez à **Flux de messagerie** \> **Règles**.

2. Cliquez **sur Ajouter** une icône ![ ](../../media/ITPro-EAC-AddIcon.png) Ajouter, puis **sélectionnez Créer une règle.**

3. Dans la page **Nouvelle règle** qui s'ouvre, configurez les paramètres suivants :

   - **Nom**: entrez un nom unique et descriptif pour la règle.

   - Cliquez sur **Autres options**.

   - **Appliquez cette règle si**: Configurez l’un des paramètres suivants pour rechercher du contenu dans les messages à l’aide d’expressions régulières (RegEx), de mots ou d’expressions :

     - **L’objet ou le corps** \> l’objet ou le corps correspond à ces **modèles** de texte : dans la  boîte de dialogue Spécifier des mots ou des expressions qui s’affiche, entrez l’une des **valeurs** suivantes, cliquez sur Icône Ajouter et répétez ![ jusqu’à ce que vous avez entré toutes les ](../../media/ITPro-EAC-AddIcon.png) valeurs.

       - `If you are unable to view the content of this email\, please`
       - `\>(safe )?unsubscribe( here)?\</a\>`
       - `If you do not wish to receive further communications like this\, please`
       - `<img height="?1"? width="?1"? src=.?http\://`
       - `To stop receiving these+emails\:http\://`
       - `To unsubscribe from \w+ (e\-?letter|e?-?mail|newsletter)`
       - `no longer (wish )?(to )?(be sent|receive) w+ email`
       - `If you are unable to view the content of this email\, please click here`
       - `To ensure you receive (your daily deals|our e-?mails)\, add`
       - `If you no longer wish to receive these emails`
       - `to change your (subscription preferences|preferences or unsubscribe)`
       - `click (here to|the) unsubscribe`

      Pour modifier une entrée, sélectionnez-la et cliquez **sur Modifier** ![ l’icône ](../../media/ITPro-EAC-EditIcon.png) Modifier. Pour supprimer une entrée, sélectionnez-la et cliquez **sur Supprimer** ![ l’icône ](../../media/ITPro-EAC-DeleteIcon.png) .

       Lorsque vous avez terminé, cliquez sur **OK**.

     - **L’objet ou le corps** \> **l’objet** ou le corps inclut l’un de ces mots : dans la  boîte de dialogue Spécifier des mots ou des expressions qui s’affiche, entrez l’une des **valeurs suivantes,** cliquez sur Ajouter une icône, puis répétez ![ jusqu’à ce que vous avez entré toutes les ](../../media/ITPro-EAC-AddIcon.png) valeurs.

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

      Pour modifier une entrée, sélectionnez-la et cliquez sur **Modifier** ![ ](../../media/ITPro-EAC-EditIcon.png) l’icône Modifier. Pour supprimer une entrée, sélectionnez-la et cliquez **sur Supprimer** ![ l’icône ](../../media/ITPro-EAC-DeleteIcon.png) .

       Lorsque vous avez terminé, cliquez sur **OK**.

   - **Pour ce faire,** **sélectionnez Modifier les propriétés du message** pour définir le niveau de \> **confiance du courrier indésirable (SCL).** Dans la **boîte de dialogue Spécifier le SCL** qui s’affiche, configurez l’un des paramètres suivants :

     - Pour marquer les messages comme **courrier indésirable,** **sélectionnez 6**. L’action que vous avez  configurée pour les verdicts de filtrage du courrier indésirable dans vos stratégies anti-courrier indésirable est appliquée aux messages (la valeur par défaut est Déplacer le message vers le dossier Courrier **indésirable).**

     - Pour marquer les messages comme courrier **indésirable à niveau de confiance élevé,** **sélectionnez 9**. L’action que vous avez  configurée pour les verdicts de filtrage du courrier indésirable à niveau de confiance élevé dans vos stratégies anti-courrier indésirable est appliquée aux messages (la valeur par défaut est Déplacer le message vers le dossier Courrier **indésirable).**

    Pour plus d’informations sur les valeurs SCL, voir Le niveau de confiance du courrier indésirable [(SCL) dans EOP.](spam-confidence-levels.md)

   Lorsque vous avez terminé, cliquez sur **Enregistrer**

## <a name="use-powershell-to-create-mail-flow-rules-that-filter-bulk-email"></a>Utiliser PowerShell pour créer des règles de flux de messagerie qui filtrent les messages électroniques en masse

Utilisez la syntaxe suivante pour créer une ou les deux règles de flux de messagerie (expressions régulières et mots) :

```powershell
New-TransportRule -Name "<UniqueName>" [-SubjectOrBodyMatchesPatterns "<RegEx1>","<RegEx2>"...] [-SubjectOrBodyContainsWords "<WordOrPhrase1>","<WordOrPhrase2>"...] -SetSCL <6 | 9>
```

Cet exemple crée une règle nommée « Bulk email filtering - RegEx » qui utilise la même liste d’expressions régulières plus tôt dans la rubrique pour définir les messages comme courrier **indésirable**.

```powershell
New-TransportRule -Name "Bulk email filtering - RegEx" -SubjectOrBodyMatchesPatterns "If you are unable to view the content of this email\, please","\>(safe )?unsubscribe( here)?\</a\>","If you do not wish to receive further communications like this\, please","\<img height\="?1"? width\="?1"? src=.?http\://","To stop receiving these+emails\:http\://","To unsubscribe from \w+ (e\-?letter|e?-?mail|newsletter)","no longer (wish )?(to )?(be sent|receive) w+ email","If you are unable to view the content of this email\, please click here","To ensure you receive (your daily deals|our e-?mails)\, add","If you no longer wish to receive these emails","to change your (subscription preferences|preferences or unsubscribe)","click (here to|the) unsubscribe"... -SetSCL 6
```

Cet exemple crée une règle nommée « Filtrage des messages électroniques en bloc - Mots » qui utilise la même liste de mots que celle de la rubrique précédente pour définir les messages comme courrier indésirable à niveau de confiance **élevé.**

```powershell
New-TransportRule -Name "Bulk email filtering - Words" -SubjectOrBodyContainsWords "to change your preferences or unsubscribe","Modify email preferences or unsubscribe","This is a promotional email","You are receiving this email because you requested a subscription","click here to unsubscribe","You have received this email because you are subscribed","If you no longer wish to receive our email newsletter","to unsubscribe from this newsletter","If you have trouble viewing this email","This is an advertisement","you would like to unsubscribe or change your","view this email as a webpage","You are receiving this email because you are subscribed" -SetSCL 9
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TransportRule](/powershell/module/exchange/new-transportrule).

## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez configuré des règles de flux de messagerie pour filtrer les messages électroniques en nombre, appliquez l’une des étapes suivantes :

- Dans le EAC, sélectionnez Règles de **flux** de messagerie et sélectionnez l’icône Modifier, puis \>  \> \> vérifiez les  ![ ](../../media/ITPro-EAC-EditIcon.png) paramètres.

- Dans PowerShell, remplacez-la par le nom de la règle et exécutez la commande suivante \<Rule Name\> pour vérifier les paramètres :

  ```powershell
  Get-TransportRule -Identity "<Rule Name>" | Format-List
  ```

- À partir d’un compte externe, envoyez un message de test à un destinataire affecté qui contient l’une des expressions ou des modèles de texte, puis vérifiez les résultats.