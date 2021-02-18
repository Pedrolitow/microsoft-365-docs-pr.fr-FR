---
title: Configurer EOP pour le courrier indésirable dans les environnements hybrides
f1.keywords:
- NOCSH
ms.author: chrisda
author: MSFTTracyP
manager: chrisda
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0cbaccf8-4afc-47e3-a36d-a84598a55fb8
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à router le courrier indésirable vers les dossiers courrier indésirable de l’utilisateur dans un environnement hybride Exchange Online Protection.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b8fbc1b065e348f759806d80fd85421eb9d66098
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50288872"
---
# <a name="configure-standalone-eop-to-deliver-spam-to-the-junk-email-folder-in-hybrid-environments"></a>Configurer EOP autonome pour remettre le courrier indésirable dans le dossier Courrier indésirable dans les environnements hybrides

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
-  [Exchange Online Protection autonome](exchange-online-protection-overview.md)

> [!IMPORTANT]
> Cette rubrique s’adresse uniquement aux clients EOP autonomes dans les environnements hybrides. Cette rubrique ne s’applique pas aux clients Microsoft 365 ayant des boîtes aux lettres Exchange Online.

Si vous êtes un client Exchange Online Protection (EOP) autonome dans un environnement hybride, vous devez configurer votre organisation Exchange sur site pour reconnaître et traduire les verdicts de filtrage du courrier indésirable d’EOP, afin que la règle de courrier indésirable dans la boîte aux lettres sur site puisse déplacer les messages vers le dossier Courrier indésirable.

Plus précisément, vous devez créer des règles de flux de messagerie (également appelées règles de transport) dans votre organisation Exchange sur site avec des conditions qui recherchent des messages avec l’un des en-têtes et valeurs EOP anti-courrier indésirable suivants, ainsi que des actions qui définissent le niveau de confiance du courrier indésirable (SCL) de ces messages sur 6 :

- `X-Forefront-Antispam-Report: SFV:SPM` (message marqué comme courrier indésirable par filtrage du courrier indésirable)

- `X-Forefront-Antispam-Report: SFV:SKS` (message marqué comme courrier indésirable par des règles de flux de messagerie dans EOP avant le filtrage du courrier indésirable)

- `X-Forefront-Antispam-Report: SFV:SKB` (message marqué comme courrier indésirable par filtrage du courrier indésirable en raison de l’adresse de messagerie ou du domaine de messagerie de l’expéditeur se trouver dans la liste des expéditeurs bloqués ou la liste des domaines bloqués dans EOP)

Pour plus d’informations sur ces valeurs d’en-tête, consultez les [en-têtes de message anti-courrier indésirable.](anti-spam-message-headers.md)

Cette rubrique décrit comment créer ces règles de flux de messagerie dans le Centre d’administration Exchange (EAC) et dans l’Environnement de ligne de bord Exchange Management Shell (Exchange PowerShell) dans l’organisation Exchange sur site.

> [!TIP]
> Au lieu de remettre les messages dans le dossier Courrier indésirable de l’utilisateur local, vous pouvez configurer des stratégies anti-courrier indésirable dans EOP pour mettre en quarantaine les messages indésirables dans EOP. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Des autorisations doivent vous être attribuées dans l’environnement Exchange local avant de pouvoir suivre ces procédures. Plus précisément, vous devez avoir le rôle Règles de **transport,** qui est  attribué aux rôles Gestion de l’organisation, Gestion de la conformité et Gestion des enregistrements par défaut.  Pour plus d’informations, voir [Ajouter des membres à un groupe de rôles.](https://docs.microsoft.com/Exchange/permissions/role-group-members#add-members-to-a-role-group)

- Si et quand un message est remis au dossier Courrier indésirable dans une organisation Exchange sur site est contrôlé par une combinaison des paramètres suivants :

  - Valeur _du paramètre SCLJunkThreshold_ sur la cmdlet [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) dans l’Environnement de travail Exchange Management Shell. La valeur par défaut est 4, ce qui signifie qu’un SCL de 5 ou plus doit remettre le message dans le dossier Courrier indésirable de l’utilisateur.

  - Valeur _du paramètre SCLJunkThreshold_ sur la cmdlet [Set-Mailbox](https://docs.microsoft.com/powershell/module/exchange/set-mailbox) dans l’Environnement de travail Exchange Management Shell. La valeur par défaut est vide ($null), ce qui signifie que le paramètre de l’organisation est utilisé.

  Pour plus d’informations, consultez les seuils de seuil de confiance du courrier indésirable [Exchange (SCL).](https://docs.microsoft.com/Exchange/antispam-and-antimalware/antispam-protection/scl)

  - Si la règle de courrier indésirable est activée sur la boîte aux lettres (la valeur du paramètre _Enabled_ est $true sur la cmdlet [Set-MailboxJunkEmailConfiguration](https://docs.microsoft.com/powershell/module/exchange/set-mailboxjunkemailconfiguration) dans l’Environnement de messagerie Exchange Management Shell). C’est la règle de courrier indésirable qui déplace réellement le message vers le dossier Courrier indésirable après la remise. Par défaut, la règle de courrier indésirable est activée sur les boîtes aux lettres. Pour plus d’informations, consultez la rubrique [Configure Exchange antispam settings on mailboxes](https://docs.microsoft.com/Exchange/antispam-and-antimalware/antispam-protection/configure-antispam-settings).

- Pour ouvrir le CENTRE d’administration Exchange sur une Exchange Server, consultez le [Centre d’administration Exchange dans Exchange Server](https://docs.microsoft.com/Exchange/architecture/client-access/exchange-admin-center). Pour ouvrir l’environnement de ligne de commande Exchange Management Shell, consultez [Ouvrir l’environnement de ligne de commande Exchange Management Shell](https://docs.microsoft.com/powershell/exchange/open-the-exchange-management-shell).

- Pour plus d’informations sur les règles de flux de messagerie dans Exchange local, consultez les rubriques suivantes :

  - [Règles de flux de messagerie dans Exchange Server](https://docs.microsoft.com/Exchange/policy-and-compliance/mail-flow-rules/mail-flow-rules)

  - [Conditions et exceptions de règle de flux de messagerie (prédicats) dans Exchange Server](https://docs.microsoft.com/Exchange/policy-and-compliance/mail-flow-rules/conditions-and-exceptions)

  - [Actions de règle de flux de messagerie dans Exchange Server](https://docs.microsoft.com/Exchange/policy-and-compliance/mail-flow-rules/actions)

## <a name="use-the-eac-to-create-mail-flow-rules-that-set-the-scl-of-eop-spam-messages"></a>Utiliser le CAE pour créer des règles de flux de messagerie qui définissent le SCL des messages indésirables EOP

1. Dans le CAE, accédez à **Flux de messagerie** \> **Règles**.

2. Cliquez **sur** Ajouter une icône, puis sélectionnez Créer une règle dans la baisse ![ qui ](../../media/ITPro-EAC-AddIcon.png) s’affiche. 

3. Dans la page **Nouvelle règle** qui s'ouvre, configurez les paramètres suivants :

   - **Nom**: entrez un nom unique et descriptif pour la règle. Par exemple :

     - EOP SFV:SPM vers SCL 6

     - EOP SFV:SKS vers SCL 6

     - EOP SFV:SKB vers SCL 6

   - Cliquez sur **Autres options**.

   - **Appliquez cette règle si**: **Sélectionnez un en-tête de message** \> **inclut l’un de ces mots.**

     Dans **l’en-tête** Entrée de texte inclut la phrase Entrée de mots qui s’affiche, faites les étapes suivantes :

     - Cliquez **sur Entrée de texte**. Dans la **boîte de dialogue** Spécifier le nom d’en-tête qui s’affiche, entrez **X-Forefront-Antispam-Report,** puis cliquez sur **OK**.

     - Cliquez **sur Entrer des mots.** Dans la boîte de dialogue Spécifier des mots ou des expressions qui s’affiche, entrez l’une des **valeurs** d’en-tête de courrier indésirable EOP (**SFV:SPM**, **SFV:SKS** ou **SFV:SKB**), cliquez sur Ajouter une  ![ icône, puis cliquez sur ](../../media/ITPro-EAC-AddIcon.png) **OK**.

   - **Pour ce faire,** **sélectionnez Modifier les propriétés du message** Définir le niveau de \> **confiance du courrier indésirable (SCL).**

     Dans la **boîte de dialogue Spécifier le SCL** qui s’affiche, **sélectionnez 6** (la valeur par défaut **est 5**).

   Lorsque vous avez terminé, cliquez sur **Enregistrer**

Répétez ces étapes pour les valeurs restantes du verdict de courrier indésirable EOP (**SFV:SPM,** **SFV:SKS** ou **SFV:SKB**).

## <a name="use-the-exchange-management-shell-to-create-mail-flow-rules-that-set-the-scl-of-eop-spam-messages"></a>Utiliser l’Environnement de travail Exchange Management Shell pour créer des règles de flux de messagerie qui définissent le SCL des messages indésirables EOP

Utilisez la syntaxe suivante pour créer les trois règles de flux de messagerie :

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

Pour vérifier que vous avez correctement configuré EOP autonome pour remettre le courrier indésirable dans le dossier Courrier indésirable dans un environnement hybride, faites l’une des étapes suivantes :

- Dans le EAC, sélectionnez règles de **flux** de messagerie, sélectionnez la règle, puis cliquez sur Modifier l’icône \> Modifier pour vérifier les  ![ ](../../media/ITPro-EAC-EditIcon.png) paramètres.

- Dans l’Environnement de commande Exchange Management Shell, remplacez-le par le nom de la règle de flux de messagerie, puis rulez la commande suivante \<RuleName\> pour vérifier les paramètres :

  ```powershell
  Get-TransportRule -Identity "<RuleName>" | Format-List
  ```

- Dans un système de messagerie externe qui **n’analyse** pas les messages sortants à la recherche de courrier indésirable, envoyez un test générique pour le message GTUBE (Unsolicited Bulk Email) à un destinataire affecté et confirmez qu’il est remis à son dossier Courrier indésirable. Un message GTUBE est semblable au fichier texte EICAR (European Institute for Computer Virus Research) pour tester les paramètres des programmes malveillants.

  Pour envoyer un message GTUBE, incluez le texte suivant dans le corps d’un message électronique sur une seule ligne, sans espace ni coupure de ligne :

  ```text
  XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
  ```
