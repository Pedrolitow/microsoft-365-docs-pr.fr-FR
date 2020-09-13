---
title: Configuration d’EOP pour le courrier indésirable dans les environnements hybrides
f1.keywords:
- NOCSH
ms.author: chrisda
author: MSFTTracyP
manager: chrisda
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0cbaccf8-4afc-47e3-a36d-a84598a55fb8
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à acheminer le courrier indésirable vers les dossiers de courrier indésirable de l’utilisateur dans un environnement hybride Exchange Online Protection.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 15acc9ad87fa0c785998895d026dae036d9ddd7b
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47547663"
---
# <a name="configure-standalone-eop-to-deliver-spam-to-the-junk-email-folder-in-hybrid-environments"></a>Configurer EOP autonome pour envoyer du courrier indésirable dans le dossier courrier indésirable dans des environnements hybrides

> [!IMPORTANT]
> Cette rubrique s’utilise uniquement pour les clients EOP autonomes dans les environnements hybrides. Cette rubrique ne s’applique pas aux clients Microsoft 365 avec des boîtes aux lettres Exchange Online.

Si vous êtes un client Exchange Online Protection (EOP) autonome dans un environnement hybride, vous devez configurer votre organisation Exchange locale pour qu’elle reconnaisse et traduise les verdicts de filtrage du courrier indésirable d’EOP, de sorte que la règle de courrier indésirable dans la boîte aux lettres locale puisse déplacer des messages vers le dossier courrier indésirable.

Plus précisément, vous devez créer des règles de flux de messagerie (également appelées règles de transport) dans votre organisation Exchange locale avec des conditions qui recherchent les messages avec l’un des en-têtes et valeurs de blocage du courrier indésirable EOP suivants, ainsi que les actions qui définissent le seuil de probabilité de courrier indésirable (SCL) de ces messages à 6 :

- `X-Forefront-Antispam-Report: SFV:SPM` (message marqué comme courrier indésirable par le filtrage du courrier indésirable)

- `X-Forefront-Antispam-Report: SFV:SKS` (message marqué comme courrier indésirable par les règles de flux de messagerie dans EOP avant le filtrage du courrier indésirable)

- `X-Forefront-Antispam-Report: SFV:SKB` (message marqué comme courrier indésirable par filtrage du courrier indésirable, car l’adresse de messagerie ou le domaine de messagerie de l’expéditeur se trouve dans la liste des expéditeurs bloqués ou dans la liste des domaines bloqués dans EOP)

Pour plus d’informations sur ces valeurs d’en-tête, consultez la rubrique [anti-spam message headers](anti-spam-message-headers.md).

Cette rubrique décrit comment créer ces règles de flux de messagerie le centre d’administration Exchange et l’environnement de commande Exchange Management Shell (Exchange PowerShell) dans l’organisation Exchange locale.

> [!TIP]
> Au lieu de transmettre les messages au dossier de courrier indésirable de l’utilisateur local, vous pouvez configurer des stratégies de blocage du courrier indésirable dans EOP pour mettre en quarantaine les messages de courrier indésirable dans EOP. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous devez disposer d’autorisations dans l’environnement Exchange local avant de pouvoir effectuer ces procédures. Plus précisément, vous devez disposer du rôle **de règles de transport** , qui est affecté aux rôles de gestion de l' **organisation**, de gestion de **la conformité**et de **gestion des enregistrements** par défaut. Pour plus d’informations, consultez [la rubrique ajouter des membres à un groupe de rôles](https://docs.microsoft.com/Exchange/permissions/role-group-members?view=exchserver-2019#add-members-to-a-role-group).

- Si et quand un message est remis dans le dossier courrier indésirable d’une organisation Exchange locale est contrôlé par une combinaison des paramètres suivants :

  - Valeur du paramètre _SCLJunkThreshold_ sur la cmdlet [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) dans l’environnement de commande Exchange Management Shell. La valeur par défaut est 4, ce qui signifie qu’une valeur SCL supérieure ou égale à 5 doit transmettre le message au dossier de courrier indésirable de l’utilisateur.

  - Valeur du paramètre _SCLJunkThreshold_ sur la cmdlet [Set-Mailbox](https://docs.microsoft.com/powershell/module/exchange/set-mailbox) dans l’environnement de commande Exchange Management Shell. La valeur par défaut est vide ($null), ce qui signifie que le paramètre de l’organisation est utilisé.

  Pour plus d’informations, consultez la rubrique [seuils de probabilité de courrier indésirable Exchange](https://docs.microsoft.com/Exchange/antispam-and-antimalware/antispam-protection/scl).

  - Si la règle de courrier indésirable est activée sur la boîte aux lettres (la valeur du paramètre _Enabled_ est $true sur la cmdlet [Set-MailboxJunkEmailConfiguration](https://docs.microsoft.com/powershell/module/exchange/set-mailboxjunkemailconfiguration) dans l’environnement de commande Exchange Management Shell). Il s’agit de la règle de courrier indésirable qui déplace le message vers le dossier courrier indésirable après la remise. Par défaut, la règle de courrier indésirable est activée sur les boîtes aux lettres. Pour plus d’informations, consultez la rubrique [Configure Exchange antispam settings on mailboxes](https://docs.microsoft.com/Exchange/antispam-and-antimalware/antispam-protection/configure-antispam-settings).

- Pour ouvrir le centre d’administration Exchange sur un serveur Exchange, consultez la rubrique [Exchange Admin Center in Exchange Server](https://docs.microsoft.com/Exchange/architecture/client-access/exchange-admin-center). Pour ouvrir l’environnement de commande Exchange Management Shell, consultez [la rubrique Open the Exchange Management Shell](https://docs.microsoft.com/powershell/exchange/open-the-exchange-management-shell).

- Pour plus d’informations sur les règles de flux de messagerie dans Exchange sur site, consultez les rubriques suivantes :

  - [Règles de flux de messagerie dans Exchange Server](https://docs.microsoft.com/Exchange/policy-and-compliance/mail-flow-rules/mail-flow-rules)

  - [Conditions de règle de flux de messagerie et exceptions (prédicats) dans Exchange Server](https://docs.microsoft.com/Exchange/policy-and-compliance/mail-flow-rules/conditions-and-exceptions)

  - [Actions de règle de flux de messagerie dans Exchange Server](https://docs.microsoft.com/Exchange/policy-and-compliance/mail-flow-rules/actions)

## <a name="use-the-eac-to-create-mail-flow-rules-that-set-the-scl-of-eop-spam-messages"></a>Utiliser le centre d’administration Exchange pour créer des règles de flux de messagerie qui définissent la valeur SCL des messages de courrier indésirable EOP

1. Dans le CAE, accédez à **Flux de messagerie** \> **Règles**.

2. Cliquez sur **Ajouter** ![ ](../../media/ITPro-EAC-AddIcon.png) une icône et sélectionnez **créer une nouvelle règle** dans la liste déroulante qui s’affiche.

3. Dans la page **Nouvelle règle** qui s'ouvre, configurez les paramètres suivants :

   - **Nom**: entrez un nom unique et descriptif pour la règle. Par exemple :

     - EOP SFV : SPM vers SCL 6

     - EOP SFV : SKS vers le niveau SCL 6

     - EOP SFV : SKB vers le niveau SCL 6

   - Cliquez sur **Autres options**.

   - **Appliquer cette règle si**: sélectionnez **un en-tête** \> **de message contient l’un de ces mots**.

     Dans la phrase entrez le texte de l' **en-tête saisissez les mots** , procédez comme suit :

     - Cliquez sur **entrer du texte**. Dans la boîte de dialogue spécifier le nom de l' **en-tête** qui s’affiche, entrez **X-Forefront-antispam-Report** , puis cliquez sur **OK**.

     - Cliquez sur  **Entrez les mots**. Dans la boîte de dialogue **spécifier des mots ou des expressions** qui s’affiche, entrez l’une des valeurs d’en-tête de courrier indésirable EOP (**SFV : SPM**, **SFV : SKS**ou **SFV : SKB**), cliquez sur **Ajouter** une ![ icône d’ajout, puis ](../../media/ITPro-EAC-AddIcon.png) cliquez sur **OK**.

   - **Procédez comme suit**: sélectionnez **modifier les propriétés du message** \> **définir le seuil de probabilité de courrier indésirable (SCL)**.

     Dans la boîte de dialogue spécifier la valeur **SCL** qui s’affiche, sélectionnez **6** (la valeur par défaut est **5**).

   Lorsque vous avez terminé, cliquez sur **Enregistrer** .

Répétez ces étapes pour les autres valeurs de verdict de courrier indésirable EOP (**SFV : SPM**, **SFV : SKS**ou **SFV : SKB**).

## <a name="use-the-exchange-management-shell-to-create-mail-flow-rules-that-set-the-scl-of-eop-spam-messages"></a>Utiliser l’environnement de commande Exchange Management Shell pour créer des règles de flux de messagerie qui définissent la valeur SCL des messages de courrier indésirable EOP

Utilisez la syntaxe suivante pour créer les trois règles de flux de messagerie :

```Powershell
New-TransportRule -Name "<RuleName>" -HeaderContainsMessageHeader "X-Forefront-Antispam-Report" -HeaderContainsWords "<EOPSpamFilteringVerdict>" -SetSCL 6
```

Par exemple :

```Powershell
New-TransportRule -Name "EOP SFV:SPM to SCL 6" -HeaderContainsMessageHeader "X-Forefront-Antispam-Report" -HeaderContainsWords "SFV:SPM" -SetSCL 6
```

```Powershell
New-TransportRule -Name "EOP SFV:SKS to SCL 6" -HeaderContainsMessageHeader "X-Forefront-Antispam-Report" -HeaderContainsWords "SFV:SKS" -SetSCL 6
```

```Powershell
New-TransportRule -Name "EOP SFV:SKB to SCL 6" -HeaderContainsMessageHeader "X-Forefront-Antispam-Report" -HeaderContainsWords "SFV:SKB" -SetSCL 6
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TransportRule](https://docs.microsoft.com/powershell/module/exchange/new-transportrule).

## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien configuré EOP autonome pour envoyer du courrier indésirable dans le dossier courrier indésirable dans un environnement hybride, effectuez l’une des opérations suivantes :

- Dans le centre d’administration Exchange, accédez à règles de **flux de messagerie** \> **Rules**, sélectionnez la règle, puis cliquez sur **modifier** ![ l’icône modifier ](../../media/ITPro-EAC-EditIcon.png) pour vérifier les paramètres.

- Dans l’environnement de commande Exchange Management Shell, remplacez \<RuleName\> par le nom de la règle de flux de messagerie et RUL la commande suivante pour vérifier les paramètres :

  ```powershell
  Get-TransportRule -Identity "<RuleName>" | Format-List
  ```

- Dans un système de messagerie externe **qui n’analyse pas les messages sortants pour le courrier indésirable**, envoie un test générique pour le message de courrier en masse non sollicité (GTUBE) à un destinataire affecté et confirme qu’il est remis dans son dossier de courrier indésirable. Un message GTUBE est semblable au fichier texte EICAR (European Institute for Computer Virus Research) pour tester les paramètres des programmes malveillants.

  Pour envoyer un message GTUBE, incluez le texte suivant dans le corps d’un message électronique sur une seule ligne, sans espaces ni sauts de ligne :

  ```text
  XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
  ```
