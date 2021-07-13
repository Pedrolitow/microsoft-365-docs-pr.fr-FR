---
title: Configurer la remise de simulations de hameçonnage tiers aux utilisateurs et de messages non filtrés dans des boîtes aux lettres SecOps
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Les administrateurs peuvent apprendre à utiliser la stratégie de remise avancée dans Exchange Online Protection (EOP) pour identifier les messages qui ne doivent pas être filtrés dans des scénarios pris en charge spécifiques (simulations d’hameçonnage tiers et messages remis à des boîtes aux lettres d’opérations de sécurité (SecOps).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b989b11739b5418ad14e147f76dde0e0dd7b1b1a
ms.sourcegitcommit: 233989a02a3fc6db33c995ad06b1f820f08f8f0a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "53383449"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a>Configurer la remise de simulations de hameçonnage tiers aux utilisateurs et de messages non filtrés dans des boîtes aux lettres SecOps

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> La fonctionnalité décrite dans cet article est en prévisualisation, n’est pas disponible pour tout le monde et peut faire l’objet de changements.

Pour sécuriser votre organisation par [défaut,](secure-by-default.md)Exchange Online Protection (EOP) n’autorise pas les listes sécurisées ou le contournement de filtrage pour les messages identifiés comme programmes malveillants ou hameçonnage à haut niveau de confiance. Toutefois, il existe des scénarios spécifiques qui nécessitent la remise de messages non filtrés. Par exemple :

- **Simulations de hameçonnage tierces**: les attaques simulées peuvent vous aider à identifier les utilisateurs vulnérables avant qu’une attaque réelle n’impacte votre organisation.
- Boîtes aux lettres d’opérations de sécurité **(SecOps)**: boîtes aux lettres dédiées utilisées par les équipes de sécurité pour collecter et analyser les messages non filtrés (bonnes et mauvaises).

Vous utilisez la _stratégie de remise_ avancée dans Microsoft 365 pour empêcher le filtrage de ces messages dans ces _scénarios spécifiques._ <sup>\*</sup> La stratégie de remise avancée garantit que les messages dans ces scénarios atteignent les résultats suivants :

- Les filtres dans EOP et Microsoft Defender Office 365 aucune action sur ces messages.<sup>\*</sup>
- [La purge zéro heure (ZAP) pour](zero-hour-auto-purge.md) le courrier indésirable et le hameçonnage n’a aucune action sur ces messages.<sup>\*</sup>
- [Les alertes système par](alerts.md) défaut ne sont pas déclenchées pour ces scénarios.
- [Air and clustering in Defender for Office 365](office-365-air.md) ignores these messages.
- Plus spécifiquement pour les simulations de hameçonnage tierces :
  - [Les soumissions d’administrateur](admin-submission.md) génèrent une réponse automatique qui dit que le message fait partie d’une campagne de simulation de hameçonnage et qu’il ne constitue pas une menace réelle. Les alertes et air ne sont pas déclenchés.
  - [Coffre dans Defender pour Office 365](safe-links.md) ne bloque pas ou ne désaxique pas les URL spécifiquement identifiées dans ces messages.
  - [Coffre pièces jointes dans Defender pour Office 365](safe-attachments.md) les pièces jointes de ces messages ne sont pas détonation.

<sup>\*</sup> Vous ne pouvez pas contourner le filtrage des programmes malveillants ou zap pour les programmes malveillants.

Les messages identifiés par la stratégie de remise avancée ne sont pas des menaces de sécurité. Les messages sont donc marqués comme étant des remplacements système. Les administrateurs peuvent filtrer et analyser ces substitutions système dans les expériences suivantes :

- [Détections de l’Explorateur de menaces/En temps réel dans Defender Office 365 plan 2](threat-explorer.md)
- Page [Entité de messagerie dans l’Explorateur de menaces/Détections en temps réel](mdo-email-entity-page.md)
- Rapport [d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Recherche avancée dans Microsoft Defender pour point de terminaison](../defender-endpoint/advanced-hunting-overview.md)
- [Vues de campagne](campaigns.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour aller directement à la page **de remise avancée,** ouvrez <https://security.microsoft.com/advanceddelivery> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir suivre les procédures de cet article :
  - Pour créer, modifier ou supprimer des paramètres configurés dans la stratégie  de remise avancée, vous devez être membre du  groupe de rôles Administrateur de la sécurité dans le portail **Microsoft 365 Defender** et membre du groupe de rôles Gestion de l’organisation **dans Exchange Online**.
  - Pour un accès en lecture seule à la stratégie de  remise  avancée, vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité.

  Pour plus d’informations, [voir Autorisations dans le portail Microsoft 365 Defender et](permissions-microsoft-365-security-center.md) [autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  > L’ajout d’utilisateurs au rôle Azure Active Directory leur donne les autorisations  requises dans le portail Microsoft 365 Defender et les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a>Utiliser le portail Microsoft 365 Defender pour configurer les boîtes aux lettres SecOps dans la stratégie de remise avancée

1. In the Microsoft 365 Defender portal, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** page \> **Rules** section \> **Advanced delivery**.

2. Dans la page **Remise** avancée, vérifiez que l’onglet Boîte aux lettres **SecOps** est sélectionné, puis faites l’une des étapes suivantes :
   - Cliquez sur ![ Modifier ](../../media/m365-cc-sc-edit-icon.png) **l’icône Modifier.**
   - S’il n’existe aucune simulation de hameçonnage configurée, cliquez sur **Ajouter.**

3. Dans le volant modifier les boîtes aux lettres **SecOps** qui s’ouvre, entrez une boîte aux lettres Exchange Online existante que vous souhaitez désigner comme boîte aux lettres SecOps en suivant l’une des étapes suivantes :
   - Cliquez dans la zone, laissez la liste des boîtes aux lettres résoudre, puis sélectionnez la boîte aux lettres.
   - Cliquez dans la zone commencer à taper un identificateur pour la boîte aux lettres (nom, nom complet, alias, adresse e-mail, nom de compte, etc.), puis sélectionnez la boîte aux lettres (nom complet) dans les résultats.

     Répétez cette étape autant de fois que nécessaire. Les groupes de distribution ne sont pas autorisés.

     Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Suppression](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

Les entrées de boîte aux lettres SecOps que vous avez configurées sont affichées sous l’onglet Boîte aux lettres **SecOps.** Pour apporter des modifications, cliquez ![ sur Modifier ](../../media/m365-cc-sc-edit-icon.png) **l’icône Modifier** sous l’onglet.

## <a name="use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Utiliser le portail Microsoft 365 Defender pour configurer des simulations de hameçonnage tiers dans la stratégie de remise avancée

1. In the Microsoft 365 Defender portal, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** page \> **Rules** section \> **Advanced delivery**.

2. Dans la page **Remise avancée,** sélectionnez l’onglet **Simulation** de hameçonnage, puis faites l’une des étapes suivantes :
   - Cliquez sur ![ Modifier ](../../media/m365-cc-sc-edit-icon.png) **l’icône Modifier.**
   - S’il n’existe aucune simulation de hameçonnage configurée, cliquez sur **Ajouter.**

3. Dans le **flyout de simulation** de hameçonnage tiers qui s’ouvre, configurez les paramètres suivants :

   - **Domaine** d’envoi : développez ce paramètre et entrez au moins un domaine d’adresse de messagerie (par exemple, contoso.com) en cliquant dans la zone, en entrant une valeur, puis en appuyant sur Entrée ou en sélectionnant la valeur affichée sous la zone. Répétez cette étape autant de fois que nécessaire. Vous pouvez ajouter jusqu’à 10 entrées.
   - **Adresse IP** d’envoi : développez ce paramètre et entrez au moins une adresse IPv4 valide en cliquant dans la zone, en entrant une valeur, puis en appuyant sur Entrée ou en sélectionnant la valeur affichée sous la zone. Répétez cette étape autant de fois que nécessaire. Vous pouvez ajouter jusqu’à 10 entrées. Les valeurs valides sont les suivantes :
     - Adresse IP unique : par exemple, 192.168.1.1.
     - Plage d’adresses IP : par exemple, 192.168.0.1-192.168.0.254.
     - ADRESSE IP CIDR : par exemple, 192.168.0.1/25.
   - URL de simulation pour autoriser : développez ce paramètre et entrez éventuellement des URL spécifiques qui font partie de votre campagne de simulation de hameçonnage qui ne doivent pas être bloquées ou désaxées en cliquant dans la zone, en entrant une valeur, puis en appuyant sur Entrée ou en sélectionnant la valeur affichée sous la zone. Vous pouvez ajouter jusqu’à 10 entrées. Pour le format de syntaxe d’URL, voir [la syntaxe d’URL pour la liste d’adresses client autoriser/bloquer](/microsoft-365/security/office-365-security/tenant-allow-block-list#url-syntax-for-the-tenant-allowblock-list).

   Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Suppression](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

4. Lorsque vous avez terminé, faites l’une des étapes suivantes :
   - **Première fois**: cliquez **sur Ajouter,** puis sur **Fermer.**
   - **Modifier une version existante**: cliquez sur **Enregistrer,** puis sur **Fermer.**

Les entrées de simulation de hameçonnage tierces que vous avez configurées sont affichées sous l’onglet **Simulation de hameçonnage.** Pour apporter des modifications, cliquez ![ sur Modifier ](../../media/m365-cc-sc-edit-icon.png) **l’icône Modifier** sous l’onglet.

## <a name="additional-scenarios-that-require-filtering-bypass"></a>Scénarios supplémentaires nécessitant le contournement du filtrage

Outre les deux scénarios que la stratégie de remise avancée peut vous aider, il existe d’autres scénarios qui peuvent nécessiter que vous contourniez le filtrage :

- **Filtres tiers**: si l’enregistrement MX de votre domaine ne pointe pas vers Office 365 (les messages sont d’abord acheminés [ailleurs),](secure-by-default.md) la sécurité par défaut *n’est* *pas disponible.* Si vous souhaitez ajouter une protection, vous devez activer le filtrage amélioré pour les connecteurs (également appelé ignorer la *liste).* Pour plus d’informations, voir [Gérer le flux de messagerie](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud)à l’aide d’un service cloud tiers Exchange Online . Si vous ne souhaitez pas que le filtrage amélioré pour les connecteurs soit utilisé, utilisez des règles de flux de messagerie (également appelées règles de transport) pour contourner le filtrage Microsoft pour les messages qui ont déjà été évalués par un filtrage tiers. Pour plus d’informations, voir [Utiliser des règles de flux de messagerie pour définir le SCL dans les messages.](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl.md)

- **Faux positifs** en cours d’examen : vous souhaitez peut-être autoriser temporairement certains messages en cours d’analyse par Microsoft via des [envois](admin-submission.md) d’administrateur à signaler les messages de bonne qualité connus qui sont marqués à tort comme incorrects pour Microsoft (faux positifs). Comme pour toutes les substitutions, il est **_vivement_** recommandé que ces allocations soient temporaires.

## <a name="exchange-online-powershell-procedures-for-secops-mailboxes-in-the-advanced-delivery-policy"></a>Exchange Online Procédures PowerShell pour les boîtes aux lettres SecOps dans la stratégie de remise avancée

Dans Exchange Online PowerShell, les éléments de base des boîtes aux lettres SecOps dans la stratégie de remise avancée sont :

- Stratégie de remplacement **SecOps**: contrôlée par les cmdlets **\* -SecOpsOverridePolicy.**
- **Règle de remplacement SecOps**: contrôlée par les cmdlets **\* -SecOpsOverrideRule.**

Ce comportement a les résultats suivants :

- Vous créez d’abord la stratégie, puis la règle qui identifie la stratégie à qui la règle s’applique.
- Lorsque vous supprimez une stratégie de PowerShell, la règle correspondante est également supprimée.
- Lorsque vous supprimez une règle de PowerShell, la stratégie correspondante n’est pas supprimée. Vous devez supprimer manuellement la stratégie correspondante.

### <a name="use-powershell-to-configure-secops-mailboxes"></a>Utiliser PowerShell pour configurer des boîtes aux lettres SecOps

La configuration d’une boîte aux lettres SecOps dans la stratégie de remise avancée dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de remplacement SecOps.
2. Créez la règle de remplacement SecOps qui spécifie la stratégie à qui la règle s’applique.

#### <a name="step-1-use-powershell-to-create-the-secops-override-policy"></a>Étape 1 : Utiliser PowerShell pour créer la stratégie de remplacement SecOps

Pour créer la stratégie de remplacement SecOps, utilisez la syntaxe suivante :

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>
```

**Remarque**: quelle que soit la valeur de nom que vous spécifiez, le nom de la stratégie sera SecOpsOverridePolicy. Vous pouvez donc également utiliser cette valeur.

Cet exemple crée la stratégie de boîte aux lettres SecOps.

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo secops@contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-SecOpsOverridePolicy](/powershell/module/exchange/new-secopsoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-secops-override-rule"></a>Étape 2 : Utiliser PowerShell pour créer la règle de remplacement SecOps

Cet exemple crée la règle de boîte aux lettres SecOps avec les paramètres spécifiés.

```powershell
New-SecOpsOverrideRule -Name SecOpsOverrideRule -Policy SecOpsOverridePolicy
```

**Remarque**: **Quelle que soit la valeur de nom que vous spécifiez, le nom de la règle sera SecOpsOverrideRule, où est une valeur \<GUID\> GUID unique \<GUID\> (par exemple, 6fed4b63-3563-495d-a481-b24a311f8329).

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-SecOpsOverrideRule](/powershell/module/exchange/new-secopsoverriderule).

### <a name="use-powershell-to-view-the-secops-override-policy"></a>Utiliser PowerShell pour afficher la stratégie de remplacement SecOps

Cet exemple renvoie des informations détaillées sur la seule stratégie de boîte aux lettres SecOps.

```powershell
Get-SecOpsOverridePolicy
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-SecOpsOverridePolicy](/powershell/module/exchange/get-secopsoverridepolicy).

### <a name="use-powershell-to-view-secops-override-rules"></a>Utiliser PowerShell pour afficher les règles de remplacement secOps

Cet exemple renvoie des informations détaillées sur les règles de remplacement SecOps.

```powershell
Get-SecOpsOverrideRule
```

Bien que la commande précédente ne retourne qu’une seule règle, toutes les règles en attente de suppression peuvent également être incluses dans les résultats.

Cet exemple identifie la règle valide (une) et toutes les règles non valides.

```powershell
Get-SecOpsOverrideRule | Format-Table Name,Mode
```

Après avoir identifié les règles non valides, vous pouvez les supprimer à l’aide de l’cmdlet **Remove-SecOpsOverrideRule,** comme décrit plus loin [dans cet article.](#use-powershell-to-remove-secops-override-rules)

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-SecOpsOverrideRule](/powershell/module/exchange/get-secopsoverriderule)

### <a name="use-powershell-to-modify-the-secops-override-policy"></a>Utiliser PowerShell pour modifier la stratégie de remplacement SecOps

Pour modifier la stratégie de remplacement SecOps, utilisez la syntaxe suivante :

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy [-AddSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>] [-RemoveSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>]
```

Cet exemple ajoute secops2@contoso.com la stratégie de remplacement SecOps.

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy -AddSentTo secops2@contoso.com
```

**Remarque**: s’il existe une règle de remplacement SecOps associée valide, les adresses de messagerie de la règle sont également mises à jour.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-SecOpsOverridePolicy](/powershell/module/exchange/set-secopsoverridepolicy).

### <a name="use-powershell-to-modify-a-secops-override-rule"></a>Utiliser PowerShell pour modifier une règle de remplacement SecOps

La cmdlet **Set-SecOpsOverrideRule** ne modifie pas les adresses de messagerie dans la règle de remplacement SecOps. Pour modifier les adresses de messagerie dans la règle de remplacement SecOps, utilisez l’cmdlet **Set-SecOpsOverridePolicy.**

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-SecOpsOverrideRule](/powershell/module/exchange/set-secopsoverriderule).

### <a name="use-powershell-to-remove-the-secops-override-policy"></a>Utiliser PowerShell pour supprimer la stratégie de remplacement SecOps

Cet exemple supprime la stratégie de boîte aux lettres SecOps et la règle correspondante.

```powershell
Remove-SecOpsOverridePolicy -Identity SecOpsOverridePolicy
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-SecOpsOverridePolicy](/powershell/module/exchange/remove-secopsoverridepolicy).

### <a name="use-powershell-to-remove-secops-override-rules"></a>Utiliser PowerShell pour supprimer des règles de remplacement SecOps

Pour supprimer une règle de remplacement SecOps, utilisez la syntaxe suivante :

```powershell
Remove-SecOpsOverrideRule -Identity <RuleIdentity>
```

Cet exemple supprime la règle de remplacement SecOps spécifiée.

```powershell
Remove-SecOpsOverrideRule -Identity SecOpsOverrideRule6fed4b63-3563-495d-a481-b24a311f8329
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-SecOpsOverrideRule](/powershell/module/exchange/remove-secopsoverriderule).

## <a name="exchange-online-powershell-procedures-for-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Exchange Online Procédures PowerShell pour les simulations de hameçonnage tiers dans la stratégie de remise avancée

Dans Exchange Online PowerShell, les éléments de base des simulations de hameçonnage tiers dans la stratégie de remise avancée sont les éléments ci-après :

- **Stratégie de remplacement de simulation de** hameçonnage : contrôlée par les cmdlets **\* -PhishSimOverridePolicy.**
- **Règle de remplacement de simulation d’hameçonnage**: contrôlée par les cmdlets **\* -PhishSimOverrideRule.**

Ce comportement a les résultats suivants :

- Vous créez d’abord la stratégie, puis la règle qui identifie la stratégie à qui la règle s’applique.
- Vous modifiez séparément les paramètres de la stratégie et de la règle.
- Lorsque vous supprimez une stratégie de PowerShell, la règle correspondante est également supprimée.
- Lorsque vous supprimez une règle de PowerShell, la stratégie correspondante n’est pas supprimée. Vous devez supprimer manuellement la stratégie correspondante.

### <a name="use-powershell-to-configure-third-party-phishing-simulations"></a>Utiliser PowerShell pour configurer des simulations de hameçonnage tierces

La configuration d’une simulation de hameçonnage tierce dans la stratégie de remise avancée dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de remplacement de simulation d’hameçonnage.
2. Créez la règle de remplacement de simulation de hameçonnage qui spécifie la stratégie à appliquer à la règle.

#### <a name="step-1-use-powershell-to-create-the-phishing-simulation-override-policy"></a>Étape 1 : Utiliser PowerShell pour créer la stratégie de remplacement de simulation de hameçonnage

Cet exemple crée la stratégie de remplacement de simulation de hameçonnage.

```powershell
New-PhishSimOverridePolicy -Name PhishSimOverridePolicy
```

**Remarque**: quelle que soit la valeur de nom que vous spécifiez, le nom de la stratégie sera PhishSimOverridePolicy. Vous pouvez donc également utiliser cette valeur.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-PhishSimOverridePolicy](/powershell/module/exchange/new-phishsimoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-phishing-simulation-override-rule"></a>Étape 2 : Utiliser PowerShell pour créer la règle de remplacement de simulation de hameçonnage

Utilisez la syntaxe suivante :

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -SenderDomainIs <Domain1>,<Domain2>,...<DomainN> -SenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>
```

Quelle que soit la valeur name que vous spécifiez, le nom de la règle sera PhishSimOverrideRule, où est une valeur \<GUID\> \<GUID\> GUID unique (par exemple, a0eae53e-d755-4a42-9320-b9c6b55c5011).

Une entrée d’adresse IP valide est l’une des valeurs suivantes :

- Adresse IP unique : par exemple, 192.168.1.1.
- Plage d’adresses IP : par exemple, 192.168.0.1-192.168.0.254.
- ADRESSE IP CIDR : par exemple, 192.168.0.1/25.

Cet exemple crée la règle de remplacement de simulation de hameçonnage avec les paramètres spécifiés.

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -SenderDomainIs fabrikam.com,wingtiptoys.com -SenderIpRanges 192.168.1.55
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-PhishSimOverrideRule](/powershell/module/exchange/new-phishsimoverriderule).

### <a name="use-powershell-to-view-the-phishing-simulation-override-policy"></a>Utiliser PowerShell pour afficher la stratégie de remplacement de simulation de hameçonnage

Cet exemple renvoie des informations détaillées sur la seule stratégie de remplacement de simulation de hameçonnage.

```powershell
Get-PhishSimOverridePolicy
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-PhishSimOverridePolicy](/powershell/module/exchange/get-phishsimoverridepolicy).

### <a name="use-powershell-to-view-phishing-simulation-override-rules"></a>Utiliser PowerShell pour afficher les règles de remplacement de simulation de hameçonnage

Cet exemple renvoie des informations détaillées sur les règles de remplacement de simulation de hameçonnage.

```powershell
Get-PhishSimOverrideRule
```

Bien que la commande précédente ne retourne qu’une seule règle, toutes les règles en attente de suppression peuvent également être incluses dans les résultats.

Cet exemple identifie la règle valide (une) et toutes les règles non valides.

```powershell
Get-PhishSimOverrideRule | Format-Table Name,Mode
```

Après avoir identifié les règles non valides, vous pouvez les supprimer à l’aide de la cmdlet **Remove-PhisSimOverrideRule,** comme décrit plus loin [dans cet article.](#use-powershell-to-remove-phishing-simulation-override-rules)

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-PhishSimOverrideRule](/powershell/module/exchange/get-phishsimoverriderule).

### <a name="use-powershell-to-modify-the-phishing-simulation-override-policy"></a>Utiliser PowerShell pour modifier la stratégie de remplacement de simulation de hameçonnage

Pour modifier la stratégie de remplacement de simulation de hameçonnage, utilisez la syntaxe suivante :

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy [-Comment "<DescriptiveText>"] [-Enabled <$true | $false>]
```

Cet exemple désactive la stratégie de remplacement de simulation de hameçonnage.

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy -Enabled $false
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-PhishSimOverridePolicy](/powershell/module/exchange/set-phishsimoverridepolicy).

### <a name="use-powershell-to-modify-a-phishing-simulation-override-rule"></a>Utiliser PowerShell pour modifier une règle de remplacement de simulation de hameçonnage

Pour modifier la règle de remplacement de simulation de hameçonnage, utilisez la syntaxe suivante :

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 [-Comment "<DescriptiveText>"] [-AddSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-RemoveSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-AddSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>] [-RemoveSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>]
```

Cet exemple modifie la règle de remplacement de simulation de hameçonnage spécifiée avec les paramètres suivants :

- Ajoutez l’entrée de domaine blueyonderairlines.com.
- Supprimez l’entrée d’adresse IP 192.168.1.55.

Notez que ces modifications n’affectent pas les entrées existantes.

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 -AddSenderDomainIs blueyonderairlines.com -RemoveSenderIpRanges 192.168.1.55
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-PhishSimOverrideRule](/powershell/module/exchange/set-phishsimoverriderule).

### <a name="use-powershell-to-remove-a-phishing-simulation-override-policy"></a>Utiliser PowerShell pour supprimer une stratégie de remplacement de simulation de hameçonnage

Cet exemple supprime la stratégie de remplacement de simulation de hameçonnage et la règle correspondante.

```powershell
Remove-PhishSimOverridePolicy -Identity PhishSimOverridePolicy
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-PhishSimOverridePolicy](/powershell/module/exchange/remove-phishsimoverridepolicy).

### <a name="use-powershell-to-remove-phishing-simulation-override-rules"></a>Utiliser PowerShell pour supprimer les règles de remplacement de simulation de hameçonnage

Pour supprimer une règle de remplacement de simulation de hameçonnage, utilisez la syntaxe suivante :

```powershell
Remove-PhishSimOverrideRule -Identity <RuleIdentity>
```

Cet exemple supprime la règle de remplacement de simulation de hameçonnage spécifiée.

```powershell
Remove-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-PhishSimOverrideRule](/powershell/module/exchange/remove-phishsimoverriderule).
