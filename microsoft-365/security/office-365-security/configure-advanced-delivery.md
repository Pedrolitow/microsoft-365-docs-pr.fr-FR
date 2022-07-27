---
title: Configurer la remise de simulations d’hameçonnage tierces aux utilisateurs et de messages non filtrés dans les boîtes aux lettres SecOps
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Les administrateurs peuvent apprendre à utiliser la stratégie de remise avancée dans Exchange Online Protection (EOP) pour identifier les messages qui ne doivent pas être filtrés dans des scénarios pris en charge spécifiques (simulations d’hameçonnage tierces et messages remis aux boîtes aux lettres d’opérations de sécurité (SecOps).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b69e143ecae2974db249a64d32d18cb5ead32aa6
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2022
ms.locfileid: "67051181"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a>Configurer la remise de simulations d’hameçonnage tierces aux utilisateurs et de messages non filtrés dans les boîtes aux lettres SecOps

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Pour assurer la [sécurité de votre organisation par défaut](secure-by-default.md), Exchange Online Protection (EOP) n’autorise pas les listes sécurisées ou le contournement du filtrage pour les messages identifiés comme des programmes malveillants ou un hameçonnage à haut niveau de confiance. Toutefois, il existe des scénarios spécifiques qui nécessitent la remise de messages non filtrés. Par exemple :

- **Simulations d’hameçonnage tierces : les attaques** simulées peuvent vous aider à identifier les utilisateurs vulnérables avant qu’une attaque réelle n’affecte votre organisation.
- Boîtes **aux lettres d’opérations de sécurité (SecOps)** : boîtes aux lettres dédiées utilisées par les équipes de sécurité pour collecter et analyser les messages non filtrés (bons et mauvais).

Vous utilisez la _stratégie de remise avancée_ dans Microsoft 365 pour empêcher le filtrage <sup>\*</sup> des messages _entrants dans ces scénarios spécifiques_. La stratégie de remise avancée garantit que les messages dans ces scénarios obtiennent les résultats suivants :

- Les filtres dans EOP et Microsoft Defender pour Office 365 n’agissent pas sur ces messages.<sup>\*</sup>
- [Le vidage de zéro heure (ZAP)](zero-hour-auto-purge.md) pour le courrier indésirable et le hameçonnage n’effectue aucune action sur ces messages<sup>\*\*</sup>.
- [Les alertes système par défaut](/microsoft-365/compliance/alert-policies#default-alert-policies) ne sont pas déclenchées pour ces scénarios.
- [AIR et le clustering dans Defender pour Office 365](office-365-air.md) ignorent ces messages.
- Spécifiquement pour les simulations d’hameçonnage tierces :
  - [Administration les soumissions](admin-submission.md) génèrent une réponse automatique indiquant que le message fait partie d’une campagne de simulation d’hameçonnage et qu’il ne constitue pas une menace réelle. Les alertes et AIR ne seront pas déclenchés. L’expérience des soumissions d’administrateurs affiche ces messages sous la forme d’une menace simulée.
  - Lorsqu’un utilisateur signale un message de simulation de hameçonnage à l’aide du message de rapport [ou des compléments report phishing](enable-the-report-message-add-in.md), le système ne génère pas d’alerte, d’investigation ou d’incident. Les liens ou fichiers ne seront pas détonés, mais le message s’affiche également sous **l’onglet Messages signalés par l’utilisateur** de la page **Soumissions** .
  - [Les liens sécurisés dans Defender pour Office 365](safe-links.md) ne bloquent ni ne détonent les URL spécifiquement identifiées dans ces messages au moment du clic. Les URL sont toujours encapsulées, mais elles ne sont pas bloquées.
  - [Les pièces jointes sécurisées dans Defender pour Office 365](safe-attachments.md) ne détonent pas les pièces jointes dans ces messages.

<sup>\*</sup> Vous ne pouvez pas contourner le filtrage des programmes malveillants.

<sup>\*\*</sup> Vous pouvez contourner ZAP pour les programmes malveillants en créant une stratégie anti-programme malveillant pour la boîte aux lettres SecOps où ZAP pour les programmes malveillants est désactivé. Pour obtenir des instructions, consultez [Configurer des stratégies anti-programme malveillant dans EOP](configure-anti-malware-policies.md).

Les messages identifiés par la stratégie de remise avancée ne sont pas des menaces de sécurité. Les messages sont donc marqués avec des remplacements système. Administration expériences affichent ces messages en raison d’un remplacement du système de **simulation d’hameçonnage** ou d’un remplacement du système de **boîte aux lettres SecOps**. Les administrateurs peuvent filtrer et analyser ces remplacements système dans les expériences suivantes :

- [Détections en temps réel/Explorateur de menaces dans Defender pour Office 365 plan 2](threat-explorer.md) : Administration pouvez filtrer sur la **source de remplacement du système** et sélectionner la **simulation d’hameçonnage** ou **la boîte aux lettres SecOps**.
- La [page d’entité Email dans l’Explorateur de menaces/Détections en temps réel](mdo-email-entity-page.md) : Administration pouvez afficher un message autorisé par la stratégie d’organisation par la **boîte aux lettres SecOps** ou la **simulation d’hameçonnage** sous **Remplacement de locataire** dans la section **Remplacements**.
- Rapport [d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report) : Administration pouvez filtrer en **affichant les données par remplacement du système** dans le menu déroulant et sélectionner pour afficher les messages autorisés en raison d’un remplacement du système de simulation d’hameçonnage. Pour afficher les messages autorisés par le remplacement de la boîte aux lettres SecOps, vous pouvez sélectionner **la répartition du graphique par emplacement de livraison** dans le menu déroulant de **répartition du graphique par raison** .
- [Repérage avancé dans Microsoft Defender pour point de terminaison](../defender-endpoint/advanced-hunting-overview.md) : La simulation d’hameçonnage et les remplacements de système de boîte aux lettres SecOps s’affichent en tant qu’options dans OrgLevelPolicy dans EmailEvents.
- [Vues de campagne](campaigns.md) : Administration pouvez filtrer sur la **source de remplacement du système** et sélectionner la **simulation d’hameçonnage** ou **la boîte aux lettres SecOps**.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Livraison avancée** , ouvrez <https://security.microsoft.com/advanceddelivery>.

- Pour vous connecter à Security & Compliance PowerShell, consultez [Connect to Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

- Vous devez disposer d’autorisations pour pouvoir effectuer les procédures décrites dans cet article :
  - Pour créer, modifier ou supprimer des paramètres configurés dans la stratégie de remise avancée, vous devez être membre du groupe de **rôles Administrateur** de la sécurité dans le **portail Microsoft 365 Defender** et membre du groupe de **rôles Gestion de l’organisation** dans **Exchange Online**.
  - Pour accéder en lecture seule à la stratégie de remise avancée, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité** .

  Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md) et [Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  > L’ajout d’utilisateurs au rôle Azure Active Directory correspondant donne aux utilisateurs les autorisations requises dans le portail Microsoft 365 Defender _et_ les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a>Utiliser le portail Microsoft 365 Defender pour configurer des boîtes aux lettres SecOps dans la stratégie de remise avancée

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies de **menace** \> **de règles** \> **avancées** dans la section **Règles**. Pour accéder directement à la page **Livraison avancée** , utilisez <https://security.microsoft.com/advanceddelivery>.

2. Dans la page **De remise avancée** , vérifiez que l’onglet Boîte **aux lettres SecOps** est sélectionné, puis effectuez l’une des étapes suivantes :
   - Cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Édition**.
   - S’il n’existe aucune boîte aux lettres SecOps configurée, cliquez sur **Ajouter**.

3. Dans le menu volant **Modifier les boîtes aux lettres SecOps** qui s’ouvre, entrez une boîte aux lettres Exchange Online existante que vous souhaitez désigner comme boîte aux lettres SecOps en effectuant l’une des étapes suivantes :
   - Cliquez dans la zone, laissez la liste des boîtes aux lettres résoudre, puis sélectionnez la boîte aux lettres.
   - Cliquez dans la zone de saisie d’un identificateur pour la boîte aux lettres (nom, nom d’affichage, alias, adresse e-mail, nom de compte, etc.), puis sélectionnez la boîte aux lettres (nom complet) dans les résultats.

     Répétez cette étape autant de fois que nécessaire. Les groupes de distribution ne sont pas autorisés.

     Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

Les entrées de boîte aux lettres SecOps que vous avez configurées s’affichent sous l’onglet **Boîte aux lettres SecOps** . Pour apporter des modifications, cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Modifier** sous l’onglet.

## <a name="use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Utiliser le portail Microsoft 365 Defender pour configurer des simulations d’hameçonnage tierces dans la stratégie de remise avancée

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies de **menace** \> **de règles** \> **avancées** dans la section **Règles**. Pour accéder directement à la page **Livraison avancée** , utilisez <https://security.microsoft.com/advanceddelivery>.

2. Dans la page **Livraison avancée** , sélectionnez l’onglet **Simulation d’hameçonnage** , puis effectuez l’une des étapes suivantes :
   - Cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Édition**.
   - S’il n’existe aucune simulation de hameçonnage configurée, cliquez sur **Ajouter**.

3. Dans le menu volant **Modifier la simulation d’hameçonnage tiers** qui s’ouvre, configurez les paramètres suivants :

   - **Domaine** : développez ce paramètre et entrez au moins un domaine d’adresse e-mail (par exemple, contoso.com) en cliquant dans la zone, en entrant une valeur, puis en appuyant sur Entrée ou en sélectionnant la valeur affichée sous la zone. Répétez cette étape autant de fois que nécessaire. Vous pouvez ajouter jusqu’à 20 entrées.

     > [!NOTE]
     > Utilisez le domaine de l’adresse `5321.MailFrom` (également appelée adresse **MAIL FROM** , expéditeur P1 ou expéditeur d’enveloppe) utilisée dans la transmission SMTP du message **ou** un domaine DKIM (DomainKeys Identified Mail), comme spécifié par votre fournisseur de simulation de hameçonnage.

   - **Envoi d’adresse IP** : développez ce paramètre et entrez au moins une adresse IPv4 valide en cliquant dans la zone, en entrant une valeur, puis en appuyant sur Entrée ou en sélectionnant la valeur affichée sous la zone. Répétez cette étape autant de fois que nécessaire. Vous pouvez ajouter jusqu’à 10 entrées. Les valeurs valides sont les suivantes :
     - Adresse IP unique : par exemple, 192.168.1.1.
     - Plage d’adresses IP : par exemple, 192.168.0.1-192.168.0.254.
     - ADRESSE IP CIDR : par exemple, 192.168.0.1/25.

   - **URL de simulation pour autoriser** : développez ce paramètre et entrez éventuellement des URL spécifiques qui font partie de votre campagne de simulation d’hameçonnage qui ne doivent pas être bloquées ou détonées en cliquant dans la zone, en entrant une valeur, puis en appuyant sur Entrée ou en sélectionnant la valeur affichée sous la zone. Vous pouvez ajouter jusqu’à 10 entrées. Pour le format de syntaxe d’URL, consultez [la syntaxe d’URL de la liste d’autorisations/de blocs du locataire](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list). Ces URL sont encapsulées au moment du clic, mais elles ne sont pas bloquées.

   Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

   > [!NOTE]
   > Pour configurer une simulation d’hameçonnage tierce dans Advanced Delivery, vous devez fournir les informations suivantes :
   >
   > - Au moins un **domaine** provenant de l’une des sources suivantes :
   >   - Adresse `5321.MailFrom` (également appelée adresse MAIL FROM, expéditeur P1 ou expéditeur d’enveloppe).
   >   - Domaine DKIM.
   > - Au moins une **adresse IP d’envoi**.
   >
   > Vous pouvez éventuellement inclure **des URL de simulation pour vous** assurer que les URL des messages de simulation ne sont pas bloquées.
   > Vous pouvez spécifier jusqu’à 10 entrées pour chaque champ.
   > Il doit y avoir une correspondance sur au moins un **domaine** et une **adresse IP d’envoi**, mais aucune association entre les valeurs n’est conservée.

4. Lorsque vous avez terminé, effectuez l’une des étapes suivantes :
   - **Première fois** : cliquez sur **Ajouter**, puis sur **Fermer**.
   - **Modifier l’existant** : cliquez sur **Enregistrer** , puis sur **Fermer**.

Les entrées de simulation d’hameçonnage tierces que vous avez configurées s’affichent sous l’onglet **Simulation de hameçonnage** . Pour apporter des modifications, cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Modifier** sous l’onglet.

## <a name="additional-scenarios-that-require-filtering-bypass"></a>Scénarios supplémentaires nécessitant un contournement du filtrage

En plus des deux scénarios que la stratégie de remise avancée peut vous aider, il existe d’autres scénarios qui peuvent nécessiter le contournement du filtrage :

- **Filtres tiers** : si l’enregistrement MX de votre domaine _ne pointe pas_ vers Office 365 (les messages sont routées ailleurs en premier), [la sécurité par défaut](secure-by-default.md) _n’est pas disponible_. Si vous souhaitez ajouter une protection, vous devez activer le filtrage amélioré pour les connecteurs (également appelé _liste d’ignorer_). Pour plus d’informations, consultez [Gérer le flux de messagerie à l’aide d’un service cloud tiers avec Exchange Online](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud). Si vous ne souhaitez pas un filtrage amélioré pour les connecteurs, utilisez des règles de flux de messagerie (également appelées règles de transport) pour contourner le filtrage Microsoft pour les messages qui ont déjà été évalués par un filtrage tiers. Pour plus d’informations, consultez [Utiliser des règles de flux de messagerie pour définir la liste de contrôle de contrôle d’accès dans les messages](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

- **Faux positifs en cours d’examen** : vous souhaiterez peut-être autoriser temporairement certains messages qui sont toujours analysés par Microsoft via [des soumissions d’administrateurs](admin-submission.md) à signaler les messages connus qui sont incorrectement marqués comme mauvais pour Microsoft (faux positifs). Comme pour tous les remplacements, nous recommandons _**vivement**_ que ces allocations soient temporaires.

## <a name="security--compliance-powershell-procedures-for-secops-mailboxes-in-the-advanced-delivery-policy"></a>Procédures PowerShell de sécurité & conformité pour les boîtes aux lettres SecOps dans la stratégie de remise avancée

Dans Security & Compliance PowerShell, les éléments de base des boîtes aux lettres SecOps dans la stratégie de remise avancée sont les suivants :

- **Stratégie de remplacement SecOps** : contrôlée par les **\*applets de commande -SecOpsOverridePolicy** .
- **Règle de remplacement SecOps** : contrôlée par les **\*applets de commande -SecOpsOverrideRule** .

Ce comportement a les résultats suivants :

- Vous créez d’abord la stratégie, puis vous créez la règle qui identifie la stratégie à laquelle la règle s’applique.
- Lorsque vous supprimez une stratégie de PowerShell, la règle correspondante est également supprimée.
- Lorsque vous supprimez une règle de PowerShell, la stratégie correspondante n’est pas supprimée. Vous devez supprimer la stratégie correspondante manuellement.

### <a name="use-powershell-to-configure-secops-mailboxes"></a>Utiliser PowerShell pour configurer des boîtes aux lettres SecOps

La configuration d’une boîte aux lettres SecOps dans la stratégie de remise avancée dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de remplacement SecOps.
2. Créez la règle de remplacement SecOps qui spécifie la stratégie à laquelle la règle s’applique.

#### <a name="step-1-use-powershell-to-create-the-secops-override-policy"></a>Étape 1 : Utiliser PowerShell pour créer la stratégie de remplacement SecOps

Pour créer la stratégie de remplacement SecOps, utilisez la syntaxe suivante :

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>
```

> [!NOTE]
> Quelle que soit la valeur name que vous spécifiez, le nom de la stratégie sera _SecOpsOverridePolicy_. Vous pouvez donc utiliser cette valeur.

Cet exemple crée la stratégie de boîte aux lettres SecOps.

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo secops@contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-SecOpsOverridePolicy](/powershell/module/exchange/new-secopsoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-secops-override-rule"></a>Étape 2 : Utiliser PowerShell pour créer la règle de remplacement SecOps

Cet exemple crée la règle de boîte aux lettres SecOps avec les paramètres spécifiés.

```powershell
New-SecOpsOverrideRule -Name SecOpsOverrideRule -Policy SecOpsOverridePolicy
```

> [!NOTE]
> Quelle que soit la valeur name que vous spécifiez, le nom de la règle est _SecOpsOverrideRule_\<GUID\> , où \<GUID\> il s’agit d’une valeur GUID unique (par exemple, 6fed4b63-3563-495d-a481-b24a3111f8329).

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-SecOpsOverrideRule](/powershell/module/exchange/new-secopsoverriderule).

### <a name="use-powershell-to-view-the-secops-override-policy"></a>Utiliser PowerShell pour afficher la stratégie de remplacement SecOps

Cet exemple retourne des informations détaillées sur la seule stratégie de boîte aux lettres SecOps.

```powershell
Get-SecOpsOverridePolicy
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-SecOpsOverridePolicy](/powershell/module/exchange/get-secopsoverridepolicy).

### <a name="use-powershell-to-view-secops-override-rules"></a>Utiliser PowerShell pour afficher les règles de remplacement SecOps

Cet exemple retourne des informations détaillées sur les règles de remplacement SecOps.

```powershell
Get-SecOpsOverrideRule
```

Bien que la commande précédente ne retourne qu’une seule règle, toutes les règles en attente de suppression peuvent également être incluses dans les résultats.

Cet exemple identifie la règle valide (une) et toutes les règles non valides.

```powershell
Get-SecOpsOverrideRule | Format-Table Name,Mode
```

Après avoir identifié les règles non valides, vous pouvez les supprimer à l’aide de l’applet de commande **Remove-SecOpsOverrideRule** , comme décrit [plus loin dans cet article](#use-powershell-to-remove-secops-override-rules).

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-SecOpsOverrideRule](/powershell/module/exchange/get-secopsoverriderule).

### <a name="use-powershell-to-modify-the-secops-override-policy"></a>Utiliser PowerShell pour modifier la stratégie de remplacement SecOps

Pour modifier la stratégie de remplacement SecOps, utilisez la syntaxe suivante :

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy [-AddSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>] [-RemoveSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>]
```

Cet exemple ajoute `secops2@contoso.com` à la stratégie de remplacement SecOps.

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy -AddSentTo secops2@contoso.com
```

> [!NOTE]
> Si une règle de remplacement SecOps associée et valide existe, les adresses e-mail de la règle sont également mises à jour.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-SecOpsOverridePolicy](/powershell/module/exchange/set-secopsoverridepolicy).

### <a name="use-powershell-to-modify-a-secops-override-rule"></a>Utiliser PowerShell pour modifier une règle de remplacement SecOps

L’applet **de commande Set-SecOpsOverrideRule** ne modifie pas les adresses e-mail dans la règle de remplacement SecOps. Pour modifier les adresses e-mail dans la règle de remplacement SecOps, utilisez l’applet **de commande Set-SecOpsOverridePolicy** .

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-SecOpsOverrideRule](/powershell/module/exchange/set-secopsoverriderule).

### <a name="use-powershell-to-remove-the-secops-override-policy"></a>Utiliser PowerShell pour supprimer la stratégie de remplacement SecOps

Cet exemple supprime la stratégie de boîte aux lettres SecOps et la règle correspondante.

```powershell
Remove-SecOpsOverridePolicy -Identity SecOpsOverridePolicy
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Remove-SecOpsOverridePolicy](/powershell/module/exchange/remove-secopsoverridepolicy).

### <a name="use-powershell-to-remove-secops-override-rules"></a>Utiliser PowerShell pour supprimer les règles de remplacement SecOps

Pour supprimer une règle de remplacement SecOps, utilisez la syntaxe suivante :

```powershell
Remove-SecOpsOverrideRule -Identity <RuleIdentity>
```

Cet exemple supprime la règle de remplacement SecOps spécifiée.

```powershell
Remove-SecOpsOverrideRule -Identity SecOpsOverrideRule6fed4b63-3563-495d-a481-b24a311f8329
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Remove-SecOpsOverrideRule](/powershell/module/exchange/remove-secopsoverriderule).

## <a name="security--compliance-powershell-procedures-for-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Sécurité & procédures PowerShell de conformité pour les simulations d’hameçonnage tierces dans la stratégie de remise avancée

Dans Security & Compliance PowerShell, les éléments de base des simulations d’hameçonnage tierces dans la stratégie de remise avancée sont les suivants :

- **Stratégie de remplacement de simulation d’hameçonnage** : contrôlée par les **\*applets de commande -PhishSimOverridePolicy** .
- **Règle de substitution de simulation d’hameçonnage** : contrôlée par les **\*applets de commande -PhishSimOverrideRule** .
- **URL de simulation d’hameçonnage autorisées (débloquées) : contrôlées** par les **\*applets de commande -TenantAllowBlockListItems** .

Ce comportement a les résultats suivants :

- Vous créez d’abord la stratégie, puis vous créez la règle qui identifie la stratégie à laquelle la règle s’applique.
- Vous modifiez les paramètres de la stratégie et de la règle séparément.
- Lorsque vous supprimez une stratégie de PowerShell, la règle correspondante est également supprimée.
- Lorsque vous supprimez une règle de PowerShell, la stratégie correspondante n’est pas supprimée. Vous devez supprimer la stratégie correspondante manuellement.

### <a name="use-powershell-to-configure-third-party-phishing-simulations"></a>Utiliser PowerShell pour configurer des simulations d’hameçonnage tierces

La configuration d’une simulation d’hameçonnage tierce dans PowerShell est un processus en plusieurs étapes :

1. Créez la stratégie de remplacement de simulation d’hameçonnage.
2. Créez la règle de remplacement de simulation d’hameçonnage qui spécifie :
   - Stratégie à laquelle la règle s’applique.
   - Adresse IP source des messages de simulation d’hameçonnage.
3. Si vous le souhaitez, identifiez les URL de simulation de hameçonnage qui doivent être autorisées (autrement dit, non bloquées ou analysées).

#### <a name="step-1-use-powershell-to-create-the-phishing-simulation-override-policy"></a>Étape 1 : Utiliser PowerShell pour créer la stratégie de remplacement de simulation d’hameçonnage

Cet exemple crée la stratégie de remplacement de simulation d’hameçonnage.

```powershell
New-PhishSimOverridePolicy -Name PhishSimOverridePolicy
```

**Remarque** : quelle que soit la valeur name que vous spécifiez, le nom de la stratégie sera _PhishSimOverridePolicy_. Vous pouvez donc utiliser cette valeur.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-PhishSimOverridePolicy](/powershell/module/exchange/new-phishsimoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-phishing-simulation-override-rule"></a>Étape 2 : Utiliser PowerShell pour créer la règle de remplacement de simulation d’hameçonnage

Utilisez la syntaxe suivante :

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains <Domain1>,<Domain2>,...<Domain10> -SenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntry10>
```

Quelle que soit la valeur name que vous spécifiez, le nom de la règle sera _PhishSimOverrideRule_\<GUID\> , où \<GUID\> il s’agit d’une valeur GUID unique (par exemple, a0eae53e-d755-4a42-9320-b9c6b55c5011).

Une entrée d’adresse IP valide est l’une des valeurs suivantes :

- Adresse IP unique : par exemple, 192.168.1.1.
- Plage d’adresses IP : par exemple, 192.168.0.1-192.168.0.254.
- ADRESSE IP CIDR : par exemple, 192.168.0.1/25.

Cet exemple crée la règle de remplacement de simulation d’hameçonnage avec les paramètres spécifiés.

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains fabrikam.com,wingtiptoys.com -SenderIpRanges 192.168.1.55
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-PhishSimOverrideRule](/powershell/module/exchange/new-phishsimoverriderule).

#### <a name="step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow"></a>Étape 3 : (Facultatif) Utiliser PowerShell pour identifier les URL de simulation d’hameçonnage à autoriser

Utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries "<URL1>","<URL2>",..."<URL10>" <[-NoExpiration] | [-ExpirationDate <DateTime>]>
```

Pour plus d’informations sur la syntaxe d’URL, consultez [la syntaxe d’URL pour la liste d’autorisations/de blocs de locataire](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list).

Cet exemple montre comment ajouter une entrée d’autorisation d’URL pour l’URL de simulation d’hameçonnage tierce spécifiée sans expiration.

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries *.fabrikam.com -NoExpiration
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="use-powershell-to-view-the-phishing-simulation-override-policy"></a>Utiliser PowerShell pour afficher la stratégie de remplacement de simulation d’hameçonnage

Cet exemple retourne des informations détaillées sur la seule stratégie de remplacement de simulation d’hameçonnage.

```powershell
Get-PhishSimOverridePolicy
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-PhishSimOverridePolicy](/powershell/module/exchange/get-phishsimoverridepolicy).

### <a name="use-powershell-to-view-phishing-simulation-override-rules"></a>Utiliser PowerShell pour afficher les règles de remplacement de simulation d’hameçonnage

Cet exemple retourne des informations détaillées sur les règles de remplacement de simulation d’hameçonnage.

```powershell
Get-PhishSimOverrideRule
```

Bien que la commande précédente ne retourne qu’une seule règle, toutes les règles en attente de suppression peuvent également être incluses dans les résultats.

Cet exemple identifie la règle valide (une) et toutes les règles non valides.

```powershell
Get-PhishSimOverrideRule | Format-Table Name,Mode
```

Après avoir identifié les règles non valides, vous pouvez les supprimer à l’aide de l’applet de commande **Remove-PhishSimOverrideRule** , comme décrit [plus loin dans cet article](#use-powershell-to-remove-phishing-simulation-override-rules).

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-PhishSimOverrideRule](/powershell/module/exchange/get-phishsimoverriderule).

### <a name="use-powershell-to-view-the-allowed-phishing-simulation-url-entries"></a>Utiliser PowerShell pour afficher les entrées d’URL de simulation d’hameçonnage autorisées

Pour afficher les URL de simulation d’hameçonnage autorisées, exécutez la commande suivante :

```powershell
Get-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

### <a name="use-powershell-to-modify-the-phishing-simulation-override-policy"></a>Utiliser PowerShell pour modifier la stratégie de remplacement de simulation d’hameçonnage

Pour modifier la stratégie de remplacement de simulation d’hameçonnage, utilisez la syntaxe suivante :

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy [-Comment "<DescriptiveText>"] [-Enabled <$true | $false>]
```

Cet exemple désactive la stratégie de remplacement de simulation d’hameçonnage.

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy -Enabled $false
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-PhishSimOverridePolicy](/powershell/module/exchange/set-phishsimoverridepolicy).

### <a name="use-powershell-to-modify-phishing-simulation-override-rules"></a>Utiliser PowerShell pour modifier les règles de remplacement de simulation d’hameçonnage

Pour modifier la règle de remplacement de simulation d’hameçonnage, utilisez la syntaxe suivante :

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 [-Comment "<DescriptiveText>"] [-AddSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-RemoveSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-AddSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>] [-RemoveSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>]
```

Cet exemple modifie la règle de remplacement de simulation d’hameçonnage spécifiée avec les paramètres suivants :

- Ajoutez l’blueyonderairlines.com d’entrée de domaine.
- Supprimez l’entrée d’adresse IP 192.168.1.55.

Notez que ces modifications n’affectent pas les entrées existantes.

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 -AddSenderDomainIs blueyonderairlines.com -RemoveSenderIpRanges 192.168.1.55
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-PhishSimOverrideRule](/powershell/module/exchange/set-phishsimoverriderule).

### <a name="use-powershell-to-modify-the-allowed-phishing-simulation-url-entries"></a>Utiliser PowerShell pour modifier les entrées d’URL de simulation d’hameçonnage autorisées

Vous ne pouvez pas modifier directement les valeurs d’URL. Vous pouvez [supprimer les entrées d’URL existantes](#use-powershell-to-remove-the-allowed-phishing-simulation-url-entries) et [ajouter de nouvelles entrées d’URL](#step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow) , comme décrit dans cet article.

Pour modifier d’autres propriétés d’une entrée d’URL de simulation d’hameçonnage autorisée (par exemple, la date d’expiration ou les commentaires), utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery <[-NoExpiration] | [-ExpirationDate <DateTime>]> [-Notes <String>]
```

Vous identifiez l’entrée à modifier par ses valeurs d’URL (le paramètre _Entries_ ) ou la valeur Identity à partir de la sortie de l’applet de commande **Get-TenantAllowBlockListItems** (paramètre _Ids_ ).

Cet exemple a modifié la date d’expiration de l’entrée spécifiée.

```powershell
Set-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery -Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="use-powershell-to-remove-a-phishing-simulation-override-policy"></a>Utiliser PowerShell pour supprimer une stratégie de remplacement de simulation d’hameçonnage

Cet exemple supprime la stratégie de remplacement de simulation d’hameçonnage et la règle correspondante.

```powershell
Remove-PhishSimOverridePolicy -Identity PhishSimOverridePolicy
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Remove-PhishSimOverridePolicy](/powershell/module/exchange/remove-phishsimoverridepolicy).

### <a name="use-powershell-to-remove-phishing-simulation-override-rules"></a>Utiliser PowerShell pour supprimer les règles de remplacement de simulation d’hameçonnage

Pour supprimer une règle de remplacement de simulation d’hameçonnage, utilisez la syntaxe suivante :

```powershell
Remove-PhishSimOverrideRule -Identity <RuleIdentity>
```

Cet exemple supprime la règle de remplacement de simulation d’hameçonnage spécifiée.

```powershell
Remove-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Remove-PhishSimOverrideRule](/powershell/module/exchange/remove-phishsimoverriderule).

### <a name="use-powershell-to-remove-the-allowed-phishing-simulation-url-entries"></a>Utiliser PowerShell pour supprimer les entrées d’URL de simulation d’hameçonnage autorisées

Pour supprimer une entrée d’URL de simulation de hameçonnage existante, utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery
```

Vous identifiez l’entrée à modifier par ses valeurs d’URL (le paramètre _Entries_ ) ou la valeur Identity à partir de la sortie de l’applet de commande **Get-TenantAllowBlockListItems** (paramètre _Ids_ ).

Cet exemple a modifié la date d’expiration de l’entrée spécifiée.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery -Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).
