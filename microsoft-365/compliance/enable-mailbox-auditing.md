---
title: Gérer l’audit de boîte aux lettres
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: aaca8987-5b62-458b-9882-c28476a66918
ms.custom: seo-marvel-apr2020
description: L’enregistrement d’audit de boîte aux lettres est Microsoft 365 par défaut (également appelé audit de boîte aux lettres par défaut ou audit de boîte aux lettres par défaut). Cela signifie que certaines actions effectuées par les propriétaires de boîtes aux lettres, les délégués et les administrateurs sont automatiquement enregistrées dans un journal d’audit de boîte aux lettres, où vous pouvez rechercher les activités effectuées sur la boîte aux lettres.
ms.openlocfilehash: 859bd0dc633ece887fe11d57068fab4eb1395cdd
ms.sourcegitcommit: efb932db63ad3ab4af4b585428d567d069410e4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "52311171"
---
# <a name="manage-mailbox-auditing"></a>Gérer l’audit de boîte aux lettres

À compter de janvier 2019, Microsoft démarre l’enregistrement d’audit des boîtes aux lettres par défaut pour toutes les organisations. Cela signifie que certaines actions effectuées par les propriétaires de boîtes aux lettres, les délégués et les administrateurs sont automatiquement enregistrées et que les enregistrements d’audit de boîte aux lettres correspondants sont disponibles lorsque vous les recherchez dans le journal d’audit de la boîte aux lettres. Avant que l’audit de boîte aux lettres ne soit activé par défaut, vous deviez l’activer manuellement pour chaque boîte aux lettres utilisateur de votre organisation.

Voici quelques avantages de l’audit de boîte aux lettres par défaut :

- L’audit est automatiquement activé lorsque vous créez une boîte aux lettres. Vous n’avez pas besoin de l’activer manuellement pour les nouveaux utilisateurs.

- Vous n’avez pas besoin de gérer les actions de boîte aux lettres auditées. Un ensemble prédéféré d’actions de boîte aux lettres est audité par défaut pour chaque type d’accès (administrateur, délégué et propriétaire).

- Lorsque Microsoft publie une nouvelle action de boîte aux lettres, l’action peut être automatiquement ajoutée à la liste des actions de boîte aux lettres auditées par défaut (sous réserve que l’utilisateur puisse disposer de la licence appropriée). Cela signifie que vous n’avez pas besoin de surveiller l’ajout de nouvelles actions sur les boîtes aux lettres.

- Vous avez une stratégie d’audit de boîte aux lettres cohérente au sein de votre organisation (car vous auditez les mêmes actions pour toutes les boîtes aux lettres).

> [!NOTE]
>* Par défaut, il est important de se souvenir de la publication de l’audit de boîte aux lettres : vous n’avez rien à faire pour gérer l’audit des boîtes aux lettres. Toutefois, pour en savoir plus, personnalisez l’audit de boîte aux lettres à partir des paramètres par défaut ou le désactiver complètement, cette rubrique peut vous aider.
>- Par défaut, seuls les événements d’audit de boîte aux lettres pour les utilisateurs E5 sont disponibles dans les recherches du journal d’audit dans le Centre de sécurité & conformité ou via l’API Activité de gestion Office 365. Pour plus d’informations, consultez la section [Plus d’informations](#more-information) de cette rubrique.

## <a name="verify-mailbox-auditing-on-by-default-is-turned-on"></a>Vérifier l’audit des boîtes aux lettres activé par défaut est activé

Pour vérifier que l’audit de boîte aux lettres est allumé par défaut pour votre organisation, exécutez la commande suivante [dans Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```PowerShell
Get-OrganizationConfig | Format-List AuditDisabled
```

La valeur **False** indique que l’audit de boîte aux lettres activé par défaut est activé pour l’organisation. Cette valeur d’organisation remplace par défaut le paramètre d’audit de boîte aux lettres sur des boîtes aux lettres spécifiques. Par exemple, si l’audit de boîte aux lettres est désactivé pour une boîte aux lettres (la propriété *AuditEnabled* a la valeur **False** sur la boîte aux lettres), les actions de boîte aux lettres par défaut seront toujours auditées pour la boîte aux lettres, car l’audit de boîte aux lettres activé par défaut est activé pour l’organisation.

Pour que l’audit de boîte aux lettres reste désactivé pour des boîtes aux lettres spécifiques, vous configurez le contournement d’audit de boîte aux lettres pour le propriétaire de la boîte aux lettres et les autres utilisateurs qui ont reçu un accès délégué à la boîte aux lettres. Pour plus d’informations, consultez la section [d’enregistrement d’audit](#bypass-mailbox-audit-logging) de la boîte aux lettres de contournement dans cette rubrique.

> [!NOTE]
> Lorsque l’audit de boîte aux lettres est désactivé par défaut pour l’organisation, la propriété *AuditEnabled* des boîtes aux lettres concernées ne passe pas de **False** à **True**. En d’autres termes, l’audit de boîte aux lettres par défaut ignore la propriété *AuditEnabled* sur les boîtes aux lettres.

## <a name="supported-mailbox-types"></a>Types de boîtes aux lettres pris en charge

Le tableau suivant indique les types de boîtes aux lettres actuellement pris en charge par l’audit de boîte aux lettres par défaut :

|**Type de boîte aux lettres**|**Pris en charge**|**Non pris en charge**|
|:---------|:---------:|:---------:|
|Boîtes aux lettres utilisateur|![Coche](../media/checkmark.png)||
|Boîtes aux lettres partagées|![Coche](../media/checkmark.png)||
|Microsoft 365 Boîtes aux lettres de groupe|![Coche](../media/checkmark.png)||
|Boîtes aux lettres de ressources||![Coche](../media/checkmark.png)|
|Boîtes aux lettres de dossiers publics||![Coche](../media/checkmark.png)|

## <a name="logon-types-and-mailbox-actions"></a>Types d’logon et actions de boîte aux lettres

Les types de logo classifient l’utilisateur qui a fait les actions auditées sur la boîte aux lettres. La liste suivante décrit les types d’ouverture de session utilisés dans l’enregistrement d’audit des boîtes aux lettres :

- **Propriétaire**: propriétaire de la boîte aux lettres (compte associé à la boîte aux lettres).

- **Déléguer**:

  - Un utilisateur qui a reçu l’autorisation EnvoyerAs, SendOnBehalf ou FullAccess sur une autre boîte aux lettres.

  - Un administrateur qui a reçu l’autorisation Autorisation totale sur la boîte aux lettres d’un utilisateur.

- **Administrateur**:

  - La boîte aux lettres est recherché à l’aide de l’un des outils eDiscovery Microsoft suivants :

    - Recherche de contenu dans le Centre de conformité.

    - eDiscovery ou Advanced eDiscovery dans le centre de conformité.

    - In-Place eDiscovery dans Exchange Online.

  - La boîte aux lettres est accessible à l’aide Microsoft Exchange Server’éditeur MAPI.

### <a name="mailbox-actions-for-user-mailboxes-and-shared-mailboxes"></a>Actions de boîte aux lettres pour les boîtes aux lettres utilisateur et les boîtes aux lettres partagées

Le tableau suivant décrit les actions de boîte aux lettres disponibles dans l’enregistrement d’audit des boîtes aux lettres pour les boîtes aux lettres utilisateur et les boîtes aux lettres partagées.

- Une coche ( ![Coche](../media/checkmark.png)) indique que l’action de boîte aux lettres peut être enregistrée pour le type de session (toutes les actions ne sont pas disponibles pour tous les types de session).

- Un astérisque ( ) après la coche indique que l’action de boîte aux lettres est consignée par défaut pour <sup>\*</sup> le type de session.

- N’oubliez pas qu’un administrateur ayant une autorisation d’accès total à une boîte aux lettres est considéré comme délégué.

|**Action de boîte aux lettres**|**Description**|**Administrateur**|**Délégué**|**Owner**|
|:---------|:---------|:---------:|:---------:|:---------:|
|**AddFolderPermissions**|**Remarque**: bien que cette valeur soit acceptée comme action de boîte aux lettres, elle est déjà incluse dans l’action **UpdateFolderPermissions** et n’est pas auditée séparément. En d’autres termes, n’utilisez pas cette valeur.||||
|**ApplyRecord**|Un élément est étiqueté en tant qu’enregistrement.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**Copier**|Un message a été copié dans un autre dossier.|![Coche](../media/checkmark.png)|||
|**Create**|Un élément a été créé dans le dossier Calendrier, Contacts, Notes ou Tâches de la boîte aux lettres (par exemple, une nouvelle demande de réunion est créée). Notez que la création, l’envoi ou la réception d’un message ne sont pas audités. De même, la création d’un dossier de boîte aux lettres n’est pas auditée.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)|
|**Par défaut**||![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|
|**FolderBind**|Un utilisateur a accédé au dossier de boîte aux lettres. Cette action est également enregistrée lorsque l’administrateur ou un délégué ouvre la boîte aux lettres.<br/><br/> **Remarque**: les enregistrements d’audit pour les actions de liaison de dossier effectuées par les délégués sont consolidés. Un enregistrement d’audit est généré pour l’accès aux dossiers individuels au cours d’une période de 24 heures.|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|**HardDelete**|Un message a été purgé du dossier Éléments récupérables.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**MailItemsAccessed**|Les données de messagerie sont accessibles par les protocoles et clients de messagerie. Cette valeur est uniquement disponible pour les utilisateurs de l’abonnement au module de conformité E5 ou E5. Pour plus d’informations, voir [Configurer l’audit avancé. ](set-up-advanced-audit.md)|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**MailboxLogin**|L’utilisateur s’est inscrit à sa boîte aux lettres. |||![Coche](../media/checkmark.png)|
|**MessageBind**|Un message a été vu dans le volet d’aperçu ou ouvert par un **administrateur.** Remarque : bien que cette valeur soit acceptée en tant qu’action de boîte aux lettres, ces actions ne sont plus enregistrées.|![Coche](../media/checkmark.png)|||
|**ModifyFolderPermissions**|**Remarque**: bien que cette valeur soit acceptée comme action de boîte aux lettres, elle est déjà incluse dans l’action **UpdateFolderPermissions** et n’est pas auditée séparément. En d’autres termes, n’utilisez pas cette valeur.||||
|**Déplacer**|Un message a été déplacé vers un autre dossier.|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|
|**MoveToDeletedItems**|Un message a été supprimé et déplacé vers le dossier Éléments supprimés.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**RecordDelete**|Un élément étiqueté en tant qu’enregistrement a été supprimé (déplacé vers le dossier Éléments récupérables). Les éléments étiquetés en tant qu’enregistrements ne peuvent pas être supprimés définitivement (purgés du dossier Éléments récupérables).|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|
|**RemoveFolderPermissions**|**Remarque**: bien que cette valeur soit acceptée comme action de boîte aux lettres, elle est déjà incluse dans l’action **UpdateFolderPermissions** et n’est pas auditée séparément. En d’autres termes, n’utilisez pas cette valeur.||||
|**Send**|L’utilisateur envoie un message électronique, répond à un message électronique ou le renvoie. Cette valeur est uniquement disponible pour les utilisateurs de l’abonnement au module de conformité E5 ou E5. Pour plus d’informations, voir [Configurer l’audit avancé pour les utilisateurs.](set-up-advanced-audit.md)|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**SendAs**|Un message a été envoyé à l’aide de l’autorisation SendAs. Cela signifie qu’un autre utilisateur a envoyé le message comme s’il provenait du propriétaire de la boîte aux lettres.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|Un message a été envoyé à l’aide de l’autorisation SendOnBehalf. Cela signifie qu’un autre utilisateur a envoyé le message de la part du propriétaire de la boîte aux lettres. Le message indique au destinataire de la part de qui le message a été envoyé et qui a envoyé réellement le message.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>||
|**SoftDelete**|Un message a été définitivement supprimé ou supprimé (récupérable) du dossier Éléments supprimés. Les éléments supprimés récupérables sont déplacés vers le dossier Éléments récupérables.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**Mettre à jour**|Un message ou ses propriétés ont été modifiés.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**UpdateCalendarDelegation**|Une délégation de calendrier a été attribuée à une boîte aux lettres. La délégation de calendrier donne à une autre personne les mêmes autorisations d’organisation pour gérer le calendrier du propriétaire de la boîte aux lettres.|![Coche](../media/checkmark.png)<sup>\*</sup>||![Coche](../media/checkmark.png)<sup>\*</sup>|
|**UpdateComplianceTag**|Une étiquette de rétention différente est appliquée à un élément de courrier (une étiquette de rétention ne peut être affectée qu’à un élément).|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|
|**UpdateFolderPermissions**|Une autorisation de dossier a été modifiée. Les autorisations de dossier contrôlent quels utilisateurs de votre organisation peuvent accéder aux dossiers dans une boîte aux lettres et aux messages situés dans ces dossiers.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**UpdateInboxRules**|Une règle de boîte de réception a été ajoutée, supprimée ou modifiée. Les règles de boîte de réception sont utilisées pour traiter les messages dans la boîte de réception de l’utilisateur en fonction des conditions spécifiées et prendre des mesures lorsque les conditions d’une règle sont remplies, telles que le déplacement d’un message vers un dossier spécifié ou la suppression d’un message.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|

> [!IMPORTANT]
> Si vous avez personnalisé les actions de boîte aux lettres à auditer pour n’importe quel *type* d’accès avant que l’audit de boîte aux lettres ne soit activé par défaut dans votre organisation, les paramètres personnalisés sont conservés sur la boîte aux lettres et ne sont pas remplacés par les actions de boîte aux lettres par défaut, comme décrit dans cette section. Pour rétablir les valeurs par défaut des actions de boîte aux lettres d’audit (ce que vous pouvez faire à tout moment), consultez la section Restaurer les [actions](#restore-the-default-mailbox-actions) de boîte aux lettres par défaut plus loin dans cette rubrique.

### <a name="mailbox-actions-for-microsoft-365-group-mailboxes"></a>Actions de boîte aux lettres Microsoft 365 boîtes aux lettres de groupe

L’audit de boîte aux lettres est mis en place par défaut pour les boîtes aux lettres de groupe Microsoft 365, mais vous ne pouvez pas personnaliser ce qui est journalisé (vous ne pouvez pas ajouter ou supprimer des actions de boîte aux lettres enregistrées pour n’importe quel type d’ouverture de session).

Le tableau suivant décrit les actions de boîte aux lettres qui sont enregistrées par défaut sur Microsoft 365 boîtes aux lettres de groupe pour chaque type de session.

N’oubliez pas qu’un administrateur ayant une autorisation d’accès total Microsoft 365 boîte aux lettres de groupe est considéré comme délégué.

|**Action de boîte aux lettres**|**Description**|**Administrateur**|**Délégué**|**Owner**|
|:---------|:---------|:---------:|:---------:|:---------:|
|**Create**|Création d’un élément de calendrier. Notez que la création, l’envoi ou la réception d’un message ne sont pas audités.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>||
|**HardDelete**|Un message a été purgé du dossier Éléments récupérables.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**MoveToDeletedItems**|Un message a été supprimé et déplacé vers le dossier Éléments supprimés.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**SendAs**|Un message a été envoyé à l’aide de l’autorisation Envoyer en tant que.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|Un message a été envoyé à l’aide de l’autorisation Envoyer de la part de. |![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>||
|**SoftDelete**|Un message a été définitivement supprimé ou supprimé (récupérable) du dossier Éléments supprimés. Les éléments supprimés récupérables sont déplacés vers le dossier Éléments récupérables.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**Mettre à jour**|Un message ou ses propriétés ont été modifiés.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|

### <a name="verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type"></a>Vérifier que les actions de boîte aux lettres par défaut sont enregistrées pour chaque type de session

L’audit de boîte aux lettres par défaut ajoute une *nouvelle propriété DefaultAuditSet* à toutes les boîtes aux lettres. La valeur de cette propriété indique si les actions de boîte aux lettres par défaut (gérées par Microsoft) sont en cours d’audit sur la boîte aux lettres.

Pour afficher la valeur sur les boîtes aux lettres utilisateur ou les boîtes aux lettres partagées, remplacez-la par le nom, l’alias, l’adresse e-mail ou le nom d’utilisateur principal (nom d’utilisateur) de la boîte aux lettres et exécutez la commande suivante dans \<MailboxIdentity\> Exchange Online PowerShell :

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Format-List DefaultAuditSet
```

Pour afficher la valeur sur Microsoft 365 boîtes aux lettres de groupe, remplacez-la par le nom, l’alias ou l’adresse e-mail de la boîte aux lettres partagée et exécutez la commande suivante dans \<MailboxIdentity\> Exchange Online PowerShell :

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> -GroupMailbox | Format-List DefaultAuditSet
```

La valeur `Admin, Delegate, Owner` indique :

- Les actions de boîte aux lettres par défaut pour les trois types de logo sont en cours d’audit. Il s’agit de la seule valeur que vous verrez sur Microsoft 365 boîtes aux lettres de groupe.

- Un administrateur *n’a pas* modifié les actions de boîte aux lettres auditées pour tout type de logo sur une boîte aux lettres utilisateur ou une boîte aux lettres partagée. Notez qu’il s’agit de l’état par défaut une fois que l’audit de boîte aux lettres est initialement allumé dans votre organisation.

Si un administrateur a déjà modifié les actions de boîte aux lettres auditées pour un type de logo (à l’aide des paramètres *AuditAdmin,* *AuditDelegate* ou *AuditOwner* sur la cmdlet **Set-Mailbox),** la valeur de la propriété sera différente.

Par exemple, la valeur de la `Owner` *propriété DefaultAuditSet* sur une boîte aux lettres utilisateur ou une boîte aux lettres partagée indique :

- Les actions de boîte aux lettres par défaut pour le propriétaire de la boîte aux lettres sont en cours d’audit.

- Les actions de boîte aux lettres auditées pour les types d’adresses et de logo ont été modifiées `Delegate` par rapport aux actions par `Admin` défaut.

Une valeur vide pour la *propriété DefaultAuditSet* indique que les actions de boîte aux lettres pour les trois types d’ouverture de page ont été modifiées sur la boîte aux lettres utilisateur ou une boîte aux lettres partagée.

Pour plus d’informations, consultez la [section Modifier ou](#change-or-restore-mailbox-actions-logged-by-default) restaurer les actions de boîte aux lettres enregistrées par défaut dans cette rubrique.

### <a name="display-the-mailbox-actions-that-are-being-logged-on-mailboxes"></a>Afficher les actions de boîte aux lettres qui sont en cours de journal sur les boîtes aux lettres

Pour voir les actions de boîte aux lettres actuellement enregistrées dans les boîtes aux lettres utilisateur ou les boîtes aux lettres partagées, remplacez-les par le nom, l’alias, l’adresse e-mail ou le nom d’utilisateur principal (nom d’utilisateur) de la boîte aux lettres, puis exécutez une ou plusieurs des commandes suivantes dans \<MailboxIdentity\> Exchange Online PowerShell.

> [!NOTE]
> Bien que vous pouvez ajouter le commutateur aux commandes `-GroupMailbox` **Get-Mailbox** suivantes pour Microsoft 365 boîtes aux lettres de groupe, ne pensez pas aux valeurs renvoyées. Les actions de boîte aux lettres statiques et par défaut auditées pour les boîtes aux lettres de groupe Microsoft 365 sont décrites dans la section Actions de boîte aux lettres pour les boîtes aux lettres de groupe [Microsoft 365](#mailbox-actions-for-microsoft-365-group-mailboxes) plus tôt dans cette rubrique.

#### <a name="owner-actions"></a>Actions du propriétaire

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditOwner
```

#### <a name="delegate-actions"></a>Actions déléguées

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditDelegate
```

#### <a name="admin-actions"></a>Actions de l’administrateur

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditAdmin
```

## <a name="change-or-restore-mailbox-actions-logged-by-default"></a>Modifier ou restaurer les actions de boîte aux lettres enregistrées par défaut

Comme indiqué précédemment, l’un des principaux avantages de l’audit des boîtes aux lettres est par défaut : vous n’avez pas besoin de gérer les actions de boîtes aux lettres auditées. Microsoft le fait pour vous et nous ajouterons automatiquement de nouvelles actions de boîte aux lettres à auditer par défaut à mesure qu’elles sont publiées.

Toutefois, votre organisation peut être tenue d’auditer un ensemble différent d’actions de boîte aux lettres pour les boîtes aux lettres utilisateur et les boîtes aux lettres partagées. Les procédures de cette section vous montrent comment modifier les actions de boîte aux lettres qui sont auditées pour chaque type d’accès et comment revenir aux actions par défaut gérées par Microsoft.

> [!IMPORTANT]
> Si vous utilisez les procédures suivantes pour personnaliser les actions de boîte aux lettres qui sont enregistrées sur des boîtes aux lettres utilisateur ou des boîtes aux lettres partagées, les nouvelles actions de boîte aux lettres par défaut publiées par Microsoft ne seront pas automatiquement auditées sur ces boîtes aux lettres. Vous devez ajouter manuellement toutes les nouvelles actions de boîte aux lettres à votre liste personnalisée d’actions.

### <a name="change-the-mailbox-actions-to-audit"></a>Modifier les actions de boîte aux lettres en audit

Vous pouvez utiliser les paramètres *AuditAdmin,* *AuditDelegate* ou *AuditOwner* sur la cmdlet **Set-Mailbox** pour modifier les actions de boîte aux lettres auditées pour les boîtes aux lettres utilisateur et les boîtes aux lettres partagées (les actions auditées pour les boîtes aux lettres de groupe Microsoft 365 ne peuvent pas être personnalisées).

Vous pouvez utiliser deux méthodes différentes pour spécifier les actions de boîte aux lettres :

- *Remplacez* (remplacer) les actions de boîte aux lettres existantes à l’aide de la syntaxe suivante : `action1,action2,...actionN` .

- *Ajoutez ou supprimez des* actions de boîte aux lettres sans affecter les autres valeurs existantes à l’aide de cette syntaxe : `@{Add="action1","action2",..."actionN"}` ou `@{Remove="action1","action2",..."actionN"}` .

Cet exemple modifie les actions de la boîte aux lettres d’administration pour la boîte aux lettres nommée « Queta Laureano » en overwritant les actions par défaut avec SoftDelete et HardDelete.

```PowerShell
Set-Mailbox -Identity "Gabriela Laureano" -AuditAdmin HardDelete,SoftDelete
```

Cet exemple ajoute l’action propriétaire MailboxLogin à la boîte aux lettres laura@contoso.onmicrosoft.com.

```PowerShell
Set-Mailbox -Identity laura@contoso.onmicrosoft.com -AuditOwner @{Add="MailboxLogin"}
```

Cet exemple supprime l’action de délégué MoveToDeletedItems pour la boîte aux lettres de discussion d’équipe.

```PowerShell
Set-Mailbox -Identity "Team Discussion" -AuditDelegate @{Remove="MoveToDeletedItems"}
```

Quelle que soit la méthode que vous utilisez, la personnalisation des actions de boîte aux lettres auditées sur les boîtes aux lettres utilisateur ou les boîtes aux lettres partagées a les résultats suivants :

- Pour le type de logo que vous avez personnalisé, les actions de boîte aux lettres auditées ne sont plus gérées par Microsoft.

- Le type de logo que vous avez personnalisé n’est plus affiché dans la valeur de propriété *DefaultAuditSet* de la boîte aux lettres, comme décrit [précédemment.](#verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type)

### <a name="restore-the-default-mailbox-actions"></a>Restaurer les actions de boîte aux lettres par défaut

Si vous avez personnalisé les actions de boîte aux lettres qui sont auditées sur une boîte aux lettres utilisateur ou une boîte aux lettres partagée, vous pouvez restaurer les actions de boîte aux lettres par défaut pour un ou tous les types d’personnalisation à l’aide de la syntaxe suivante :

```PowerShell
Set-Mailbox -Identity <MailboxIdentity> -DefaultAuditSet <Admin | Delegate | Owner>
```

Vous pouvez spécifier plusieurs *valeurs DefaultAuditSet* séparées par des virgules

**Remarque**: les procédures suivantes ne s’appliquent pas Microsoft 365 boîtes aux lettres de groupe (elles sont limitées aux actions par défaut décrites [ici).](#mailbox-actions-for-microsoft-365-group-mailboxes)

Cet exemple restaure les actions de boîte aux lettres auditées par défaut pour tous les types d’mark@contoso.onmicrosoft.com.

```PowerShell
Set-Mailbox -Identity mark@contoso.onmicrosoft.com -DefaultAuditSet Admin,Delegate,Owner
```

Cet exemple restaure les actions de boîte aux lettres auditées par défaut pour le type d’chris@contoso.onmicrosoft.com de boîte aux lettres admin, mais laisse les actions de boîte aux lettres auditées personnalisées pour les types d’accès délégué et propriétaire.

```PowerShell
Set-Mailbox -Identity chris@contoso.onmicrosoft.com -DefaultAuditSet Admin
```

La restauration des actions de boîte aux lettres auditées par défaut pour un type d’utilisateur a les résultats suivants :

- La liste actuelle des actions de boîte aux lettres est remplacée par les actions de boîte aux lettres par défaut pour le type d’logo.

- Toutes les nouvelles actions de boîte aux lettres publiées par Microsoft sont automatiquement ajoutées à la liste des actions auditées pour le type d’accès.

- La *valeur de la propriété DefaultAuditSet* de la boîte aux lettres est mise à jour pour inclure le type d’ouverture de boîte aux lettres restauré.

## <a name="turn-off-mailbox-auditing-on-by-default-for-your-organization"></a>Désactiver l’audit des boîtes aux lettres par défaut pour votre organisation

Vous pouvez désactiver l’audit des boîtes aux lettres par défaut pour l’ensemble de votre organisation en exécutant la commande suivante dans Exchange Online PowerShell :

```PowerShell
Set-OrganizationConfig -AuditDisabled $true
```

La fonction d’audit des boîtes aux lettres est par défaut éteinte et présente les résultats suivants :

- L’audit de boîte aux lettres est désactivé pour votre organisation.

- À partir du moment où vous avez désactivé l’audit de boîte aux lettres par défaut, aucune action de boîte aux lettres n’est auditée, même si l’audit est activé sur une boîte aux lettres (la propriété *AuditEnabled* de la boîte aux lettres a la valeur **True).**

- L’audit de boîte aux lettres n’est pas activé pour les nouvelles boîtes aux lettres et la définition de la propriété *AuditEnabled* sur une boîte aux lettres nouvelle ou existante sur **True** sera ignorée.

- Tous les paramètres d’association de contournement d’audit de boîte aux lettres (configurés à l’aide de la cmdlet **Set-MailboxAuditBypassAssociation)** sont ignorés.

- Les enregistrements d’audit de boîte aux lettres existants sont conservés jusqu’à l’expiration de la durée de vie du journal d’audit de l’enregistrement.

### <a name="turn-on-mailbox-auditing-on-by-default"></a>Activer l’audit des boîtes aux lettres par défaut

Pour activer de nouveau l’audit de boîte aux lettres pour votre organisation, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Set-OrganizationConfig -AuditDisabled $false
```

## <a name="bypass-mailbox-audit-logging"></a>Ignorer l’enregistrement d’audit de boîte aux lettres :

Pour l’instant, vous ne pouvez pas désactiver l’audit de boîte aux lettres pour les boîtes aux lettres spécifiques lorsque l’audit de boîte aux lettres activé par défaut est activé dans votre organisation. Par exemple, la définition de la propriété de boîte aux lettres *AuditEnabled* sur **False** est ignorée.

Toutefois, vous pouvez toujours utiliser la cmdlet **Set-MailboxAuditBypassAssociation**  dans Exchange Online PowerShell pour empêcher la journalisation de toutes les actions de boîte aux lettres des utilisateurs spécifiés, quel que soit l’endroit où elles se produisent. Par exemple :

- Les actions du propriétaire de boîte aux lettres effectuées par les utilisateurs contourné ne sont pas enregistrées.

- Les actions de délégation effectuées par les utilisateurs contourné sur les boîtes aux lettres d’autres utilisateurs (y compris les boîtes aux lettres partagées) ne sont pas enregistrées.

- Les actions d’administration effectuées par les utilisateurs contourné ne sont pas enregistrées.

Pour contourner l’enregistrement d’audit de boîte aux lettres pour un utilisateur spécifique, remplacez-le par le nom, l’adresse e-mail, l’alias ou le nom d’utilisateur principal (nom d’utilisateur) de l’utilisateur et exécutez la \<MailboxIdentity\> commande suivante :

```PowerShell
Set-MailboxAuditBypassAssociation -Identity <MailboxIdentity> -AuditByPassEnabled $true
```

Pour vérifier que l’audit est contourné pour l’utilisateur spécifié, exécutez la commande suivante :

```PowerShell
Get-MailboxAuditBypassAssociation -Identity <MailboxIdentity> | Format-List AuditByPassEnabled
```

La valeur **True indique** que l’enregistrement d’audit de boîte aux lettres est contourné pour l’utilisateur.

## <a name="more-information"></a>Plus d’informations

- Bien que l’enregistrement d’audit de boîte aux lettres activé par défaut soit activé pour toutes les organisations, seuls les utilisateurs titulaires d’une licence E5 retourneront les événements du journal [d’audit](search-the-audit-log-in-security-and-compliance.md) des boîtes aux lettres dans les recherches du journal d’audit dans le Centre de sécurité & conformité ou via l’API activité de gestion [Office 365](/office/office-365-management-api/office-365-management-activity-api-reference) par **défaut.**

  Pour récupérer les entrées du journal d’audit des boîtes aux lettres pour les utilisateurs sans licence E5, vous pouvez :

  - Activez manuellement l’audit des boîtes aux lettres sur des boîtes aux lettres individuelles (exécutez la commande, `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true` ). Après cela, vous pouvez utiliser les recherches dans le journal d’audit dans le Centre de sécurité et conformité & ou via l’API Activité de gestion Office 365 de sécurité.
  
    > [!NOTE]
    > Si l’audit de boîte aux lettres semble déjà être activé sur la boîte aux lettres, mais que vos recherches ne retournent aucun résultat, modifiez la valeur du paramètre _AuditEnabled_ de et revenir à `$false` `$true` .
  
  - Utilisez les cmdlets suivantes dans Exchange Online PowerShell :

    - [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) pour rechercher des utilisateurs spécifiques dans le journal d’audit de la boîte aux lettres.

    - [New-MailboxAuditLogSearch](/powershell/module/exchange/new-mailboxauditlogsearch) pour rechercher des utilisateurs spécifiques dans le journal d’audit de la boîte aux lettres et envoyer les résultats par courrier électronique à des destinataires spécifiés.

  - Utilisez le Exchange d’administration Centrale (EAC) Exchange Online pour les actions suivantes :

    - [Exporter les journaux d’audit de boîte aux lettres](/Exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs)

    - [Exécuter un rapport d’accès aux boîtes aux lettres par des non-propriétaires](/Exchange/security-and-compliance/exchange-auditing-reports/non-owner-mailbox-access-report)

- Par défaut, les enregistrements du journal d’audit de boîte aux lettres sont conservés pendant 90 jours avant leur suppression. Vous pouvez modifier la limite d’âge pour les enregistrements du journal d’audit à l’aide du paramètre *AuditLogAgeLimit* de la cmdlet **Set-Mailbox** dans Exchange Online PowerShell. Toutefois, l’augmentation de cette valeur ne vous permet pas de rechercher des événements qui sont plus anciens que 90 jours dans le journal d’audit.

  Si vous augmentez la limite d’âge, vous devez utiliser la cmdlet [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) dans Exchange Online PowerShell pour rechercher dans le journal d’audit de la boîte aux lettres de l’utilisateur les enregistrements qui ont plus de 90 jours.

- Si vous avez modifié la propriété *AuditLogAgeLimit* d’une boîte aux lettres avant que l’audit de boîte aux lettres soit désactivé par défaut pour l’organisation, la durée de vie du journal d’audit existante de la boîte aux lettres n’est pas modifiée. En d’autres termes, l’audit de boîte aux lettres par défaut n’affecte pas la limite d’âge actuelle pour les enregistrements d’audit de boîte aux lettres.

- Pour modifier la valeur *AuditLogAgeLimit* sur une boîte aux lettres Microsoft 365 groupe, vous devez inclure le commutateur dans la commande `-GroupMailbox` **Set-Mailbox.**

- Les enregistrements du journal d’audit de boîte aux lettres sont stockés dans un sous-dossier (appelé *Audits)* dans le dossier Éléments récupérables de la boîte aux lettres de chaque utilisateur. Gardez les éléments suivants à l’esprit concernant les enregistrements d’audit de boîte aux lettres et le dossier Éléments récupérables :

  - Les enregistrements d’audit de boîte aux lettres sont comptabilisés par rapport au quota de stockage du dossier Éléments récupérables, qui est de 30 Go par défaut (le quota d’avertissement est de 20 Go). Le quota de stockage est automatiquement augmenté jusqu’à 100 Go (avec un quota d’avertissement de 90 Go) lorsque :

    - Une mise en attente est placée sur une boîte aux lettres.

    - La boîte aux lettres est affectée à une stratégie de rétention dans le Centre de conformité.

  - Les enregistrements d’audit de boîte aux lettres sont également comptabilisés dans la limite de [dossier pour le dossier Éléments récupérables.](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-folder-limits) Un maximum de 3 millions d’éléments (enregistrements d’audit) peuvent être stockés dans le sous-dossier Audits.

    > [!NOTE]
    > Il est peu probable que l’audit de boîte aux lettres sur par défaut aura un impact sur le quota de stockage ou la limite de dossier pour le dossier Éléments récupérables.

    - Vous pouvez exécuter la commande suivante dans Exchange Online PowerShell pour afficher la taille et le nombre d’éléments dans le sous-dossier Audits dans le dossier Éléments récupérables :

      ```PowerShell
      Get-MailboxFolderStatistics -Identity <MailboxIdentity> -FolderScope RecoverableItems | Where-Object {$_.Name -eq 'Audits'} | Format-List FolderPath,FolderSize,ItemsInFolder
      ```

    - Vous ne pouvez pas accéder directement à un enregistrement de journal d’audit dans le dossier Éléments récupérables ; Utilisez plutôt la cmdlet **Search-MailboxAuditLog** ou recherchez dans le journal d’audit pour rechercher et afficher les enregistrements d’audit de boîte aux lettres.

- Si une boîte aux lettres est placée en conservation ou affectée à une stratégie de rétention dans le Centre de conformité, les enregistrements du journal d’audit sont conservés pendant la durée définie par la propriété *AuditLogAgeLimit* de la boîte aux lettres (90 jours par défaut). Pour conserver les enregistrements du journal d’audit plus longtemps pour les boîtes aux lettres en attente, vous devez augmenter la valeur *AuditLogAgeLimit* de la boîte aux lettres.

- Dans un environnement multi-géographique, l’audit de boîte aux lettres inter-géographique n’est pas pris en charge. Par exemple, si un utilisateur se voit attribuer les autorisations d’accès à une boîte aux lettres partagée dans un autre emplacement géographique, les actions de boîte aux lettres effectuées par cet utilisateur ne sont pas enregistrées dans le journal d’audit de la boîte aux lettres partagée.