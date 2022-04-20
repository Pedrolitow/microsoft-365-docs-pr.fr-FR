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
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: aaca8987-5b62-458b-9882-c28476a66918
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: La journalisation de l’audit de boîte aux lettres est activée par défaut dans Microsoft 365 (également appelé « audit de boîte aux lettres par défaut » ou « audit de boîte aux lettres activé par défaut »). Cette configuration signifie que certaines actions effectuées par les propriétaires de boîtes aux lettres, les délégués et les administrateurs sont automatiquement enregistrées dans un journal d’audit de boîte aux lettres, où vous pouvez rechercher les activités effectuées sur la boîte aux lettres.
ms.openlocfilehash: d5d966cf4d5b7c58c15df4ce8d4039331ebca8c4
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972626"
---
# <a name="manage-mailbox-auditing"></a>Gérer l’audit de boîte aux lettres

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

À compter de janvier 2019, Microsoft active la journalisation de l’audit de boîte aux lettres par défaut pour toutes les organisations. Cela signifie que certaines actions effectuées par les propriétaires de boîtes aux lettres, les délégués et les administrateurs sont automatiquement journalisées, et les enregistrements d’audit de boîte aux lettres correspondants sont disponibles lorsque vous les recherchez dans le journal d’audit de boîte aux lettres. Avant d’activer l’audit de boîte aux lettres par défaut, vous deviez l’activer manuellement pour chaque boîte aux lettres utilisateur de votre organisation.

Voici quelques avantages de l’audit de boîte aux lettres activé par défaut :

- L’audit est automatiquement activé lorsque vous créez une boîte aux lettres. Vous n’avez pas besoin de l’activer manuellement pour les nouveaux utilisateurs.
- Vous n’avez pas besoin de gérer les actions de boîte aux lettres auditées. Un ensemble prédéfini d’actions de boîte aux lettres est audité par défaut pour chaque type d’ouverture de session (administrateur, délégué et propriétaire).
- Lorsque Microsoft publie une nouvelle action de boîte aux lettres, l’action peut être automatiquement ajoutée à la liste des actions de boîte aux lettres qui sont auditées par défaut (sous réserve que l’utilisateur dispose de la licence appropriée). Cela signifie que vous n’avez pas besoin de surveiller l’ajout de nouvelles actions sur les boîtes aux lettres.
- Vous disposez d’une stratégie d’audit de boîte aux lettres cohérente au sein de votre organisation (car vous auditez les mêmes actions pour toutes les boîtes aux lettres).

> [!NOTE]
>
> - La chose importante à retenir au sujet de la publication de l’audit de boîte aux lettres est par défaut : vous n’avez rien à faire pour gérer l’audit de boîte aux lettres. Toutefois, pour en savoir plus, personnalisez l’audit de boîte aux lettres à partir des paramètres par défaut ou désactivez-le complètement. Cet article peut vous aider.
> - Par défaut, seuls les événements d’audit de boîte aux lettres pour les utilisateurs E5 sont disponibles dans les recherches dans le journal d’audit dans le portail de conformité Microsoft Purview ou via l’API d’activité de gestion Office 365. Pour plus d’informations, consultez la section [Plus d’informations](#more-information) de cet article.

## <a name="verify-mailbox-auditing-on-by-default-is-turned-on"></a>Vérifier l’audit des boîtes aux lettres activé par défaut est activé

Pour vérifier que l’audit de boîte aux lettres activé par défaut est activé pour votre organisation, exécutez la commande suivante dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) :

```PowerShell
Get-OrganizationConfig | Format-List AuditDisabled
```

La valeur **False** indique que l’audit de boîte aux lettres activé par défaut est activé pour l’organisation. Par défaut, la valeur organisationnelle remplace le paramètre d’audit de boîte aux lettres sur des boîtes aux lettres spécifiques. Par exemple, si l’audit de boîte aux lettres est désactivé pour une boîte aux lettres (la propriété *AuditEnabled* est **False** sur la boîte aux lettres), les actions de boîte aux lettres par défaut sont toujours auditées pour la boîte aux lettres, car l’audit de boîte aux lettres activé par défaut est activé pour l’organisation.

Pour que l’audit des boîtes aux lettres soit désactivé pour des boîtes aux lettres spécifiques, vous configurez le contournement de l’audit de boîte aux lettres pour le propriétaire de la boîte aux lettres et les autres utilisateurs qui ont été délégués à la boîte aux lettres. Pour plus d’informations, consultez la section [Ignorer la journalisation d’audit de boîte aux lettres](#bypass-mailbox-audit-logging) plus loin dans cet article.

> [!NOTE]
> Lorsque l’audit de boîte aux lettres activé par défaut est activé pour l’organisation, la propriété *AuditEnabled* pour les boîtes aux lettres affectées ne passe pas de **False** à **True**. En d’autres termes, l’audit de boîte aux lettres activé par défaut ignore la propriété *AuditEnabled* sur les boîtes aux lettres.

## <a name="supported-mailbox-types"></a>Types de boîtes aux lettres pris en charge

Le tableau suivant présente les types de boîtes aux lettres actuellement pris en charge par l’audit de boîte aux lettres par défaut :

|Type de boîte aux lettres|Pris en charge|
|---|:---:|
|Boîtes aux lettres utilisateur|![Coche.](../media/checkmark.png)|
|Boîtes aux lettres partagées|![Coche.](../media/checkmark.png)|
|boîtes aux lettres de groupe Microsoft 365|![Coche.](../media/checkmark.png)|
|Boîtes aux lettres de ressources||
|Boîtes aux lettres de dossiers publics||

## <a name="logon-types-and-mailbox-actions"></a>Types d’ouverture de session et actions de boîte aux lettres

Les types d’ouverture de session classent l’utilisateur qui a effectué les actions auditées sur la boîte aux lettres. La liste suivante décrit les types d’ouverture de session utilisés dans la journalisation d’audit de boîte aux lettres :

- **Propriétaire** : propriétaire de la boîte aux lettres (compte associé à la boîte aux lettres).
- **Délégué** :
  - Un utilisateur qui a reçu l’autorisation SendAs, SendOnBehalf ou FullAccess sur une autre boîte aux lettres.
  - Administrateur qui a reçu l’autorisation FullAccess sur la boîte aux lettres d’un utilisateur.
- **Administrateur** :
  - La boîte aux lettres est recherchée avec l’un des outils Microsoft eDiscovery suivants :
    - Recherche de contenu dans le Centre de conformité.
    - eDiscovery ou eDiscovery (Premium) dans le Centre de conformité.
    - In-Place eDiscovery dans Exchange Online.
  - La boîte aux lettres est accessible à l’aide de l’éditeur MAPI Microsoft Exchange Server.

### <a name="mailbox-actions-for-user-mailboxes-and-shared-mailboxes"></a>Actions de boîte aux lettres pour les boîtes aux lettres utilisateur et les boîtes aux lettres partagées

Le tableau suivant décrit les actions de boîte aux lettres disponibles dans la journalisation d’audit de boîte aux lettres pour les boîtes aux lettres utilisateur et les boîtes aux lettres partagées.

- Une coche (![Marque de vérification.](../media/checkmark.png)) indique que l’action de boîte aux lettres peut être journalisée pour le type d’ouverture de session (toutes les actions ne sont pas disponibles pour tous les types d’ouverture de session).
- Un astérisque ( <sup>\*</sup> ) après la coche indique que l’action de boîte aux lettres est journalisée par défaut pour le type d’ouverture de session.
- N’oubliez pas qu’un administrateur disposant de l’autorisation d’accès total à une boîte aux lettres est considéré comme un délégué.

|Action de boîte aux lettres|Description|Administrateur|Délégué|Propriétaire|
|---|---|:---:|:---:|:---:|
|**AddFolderPermissions**|Bien que cette valeur soit acceptée comme action de boîte aux lettres, elle est déjà incluse dans l’action **UpdateFolderPermissions** et n’est pas auditée séparément. En d’autres termes, n’utilisez pas cette valeur.||||
|**ApplyRecord**|Un élément est étiqueté en tant qu’enregistrement.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|
|**Copier**|Un message a été copié dans un autre dossier.|![Coche.](../media/checkmark.png)|||
|**Create**|Un élément a été créé dans le dossier Calendrier, Contacts, Brouillon, Notes ou Tâches de la boîte aux lettres (par exemple, une demande de réunion est créée). Notez que la création, l’envoi ou la réception d’un message ne sont pas audités. De même, la création d’un dossier de boîte aux lettres n’est pas auditée.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Marque de vérification.](../media/checkmark.png)|
|**FolderBind**|Un utilisateur a accédé au dossier de boîte aux lettres. Cette action est également enregistrée lorsque l’administrateur ou un délégué ouvre la boîte aux lettres.<br/><br/> **Remarque** : les enregistrements d’audit pour les actions de liaison de dossier effectuées par les délégués sont consolidés. Un enregistrement d’audit est généré pour l’accès individuel aux dossiers au cours d’une période de 24 heures.|![Coche.](../media/checkmark.png)|![Marque de vérification.](../media/checkmark.png)||
|**HardDelete**|Un message a été purgé du dossier Éléments récupérables.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|
|**MailboxLogin**|L’utilisateur s’est connecté à sa boîte aux lettres.|||![Coche](../media/checkmark.png)|
|**MailItemsAccessed**|**Remarque** : cette valeur est disponible uniquement pour les utilisateurs disposant de licences E5/A5/G5. Pour plus d’informations, consultez [Configurer l’audit Microsoft Purview (Premium).](set-up-advanced-audit.md) <br/><br/> Les données de messagerie sont accessibles par les protocoles de messagerie et les clients.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**MessageBind**|**Remarque** : cette valeur est disponible uniquement pour les utilisateurs *sans* licence E5/A5/G5. <br/><br/> Un message a été affiché dans le volet d’aperçu ou ouvert par un administrateur.|![Coche](../media/checkmark.png)|||
|**ModifyFolderPermissions**|Bien que cette valeur soit acceptée comme action de boîte aux lettres, elle est déjà incluse dans l’action **UpdateFolderPermissions** et n’est pas auditée séparément. En d’autres termes, n’utilisez pas cette valeur.||||
|**Déplacer**|Un message a été déplacé vers un autre dossier.|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|
|**MoveToDeletedItems**|Un message a été supprimé et déplacé vers le dossier Éléments supprimés.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**RecordDelete**|Un élément étiqueté en tant qu’enregistrement a été supprimé de manière réversible (déplacé vers le dossier Éléments récupérables). Les éléments étiquetés en tant qu’enregistrements ne peuvent pas être supprimés définitivement (supprimés du dossier Éléments récupérables).|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|
|**RemoveFolderPermissions**|Bien que cette valeur soit acceptée comme action de boîte aux lettres, elle est déjà incluse dans l’action **UpdateFolderPermissions** et n’est pas auditée séparément. En d’autres termes, n’utilisez pas cette valeur.||||
|**SearchQueryInitiated**|**Remarque** : cette valeur est disponible uniquement pour les utilisateurs disposant de licences E5/A5/G5. Pour plus d’informations, consultez [Configurer l’audit Microsoft Purview (Premium).](set-up-advanced-audit.md) <br/><br/> Une personne utilise Outlook (Windows, Mac, iOS, Android ou Outlook sur le web) ou l’application Courrier pour Windows 10 pour rechercher des éléments dans une boîte aux lettres.|||![Coche](../media/checkmark.png)|
|**Send**|**Remarque** : cette valeur est disponible uniquement pour les utilisateurs disposant de licences E5/A5/G5. Pour plus d’informations, consultez [Configurer l’audit Microsoft Purview (Premium).](set-up-advanced-audit.md) <br/><br/> L’utilisateur envoie un e-mail, répond à un e-mail ou transfère un e-mail.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>||![Coche](../media/checkmark.png)<sup>\*</sup>|
|**SendAs**|Un message a été envoyé à l’aide de l’autorisation SendAs. Cela signifie qu’un autre utilisateur a envoyé le message comme s’il provenait du propriétaire de la boîte aux lettres.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|Un message a été envoyé à l’aide de l’autorisation SendOnBehalf. Cela signifie qu’un autre utilisateur a envoyé le message de la part du propriétaire de la boîte aux lettres. Le message indique au destinataire de la part de qui le message a été envoyé et qui a envoyé réellement le message.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>||
|**SoftDelete**|Un message a été définitivement supprimé ou supprimé (récupérable) du dossier Éléments supprimés. Les éléments supprimés récupérables sont déplacés vers le dossier Éléments récupérables.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**Mettre à jour**|Un message ou l’une de ses propriétés a été modifié.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**UpdateCalendarDelegation**|Une délégation de calendrier a été affectée à une boîte aux lettres. La délégation de calendrier donne à une autre personne les mêmes autorisations d’organisation pour gérer le calendrier du propriétaire de la boîte aux lettres.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>||![Coche](../media/checkmark.png)<sup>\*</sup>|
|**UpdateComplianceTag**|Une autre étiquette de rétention est appliquée à un élément de courrier (un élément ne peut avoir qu’une seule étiquette de rétention qui lui est affectée).|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|
|**UpdateFolderPermissions**|Une autorisation de dossier a été modifiée. Les autorisations de dossier contrôlent quels utilisateurs de votre organisation peuvent accéder aux dossiers dans une boîte aux lettres et aux messages situés dans ces dossiers.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**UpdateInboxRules**|Une règle de boîte de réception a été ajoutée, supprimée ou modifiée. Les règles de boîte de réception sont utilisées pour traiter les messages dans la boîte de réception de l’utilisateur en fonction des conditions spécifiées et prendre des mesures lorsque les conditions d’une règle sont remplies, telles que le déplacement d’un message vers un dossier spécifié ou la suppression d’un message.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|

> [!IMPORTANT]
> Si vous avez personnalisé les actions de boîte aux lettres à auditer pour tout type d’ouverture de session *avant* que l’audit de boîte aux lettres par défaut n’ait été activé dans votre organisation, les paramètres personnalisés sont conservés sur la boîte aux lettres et ne sont pas remplacés par les actions de boîte aux lettres par défaut, comme décrit dans cette section. Pour rétablir les valeurs par défaut des actions de boîte aux lettres d’audit (ce que vous pouvez faire à tout moment), consultez la section [Restaurer les actions de boîte aux lettres par défaut](#restore-the-default-mailbox-actions) plus loin dans cet article.

### <a name="mailbox-actions-for-microsoft-365-group-mailboxes"></a>Actions de boîte aux lettres pour les boîtes aux lettres de groupe Microsoft 365

Par défaut, l’audit de boîte aux lettres permet de journaliser l’audit des boîtes aux lettres Microsoft 365 les boîtes aux lettres de groupe, mais vous ne pouvez pas personnaliser ce qui est journalisé (vous ne pouvez pas ajouter ou supprimer des actions de boîte aux lettres journalisées pour n’importe quel type de connexion).

Le tableau suivant décrit les actions de boîte aux lettres journalisées par défaut sur Microsoft 365 boîtes aux lettres de groupe pour chaque type d’ouverture de session.

N’oubliez pas qu’un administrateur disposant de l’autorisation d’accès total à une boîte aux lettres de groupe Microsoft 365 est considéré comme délégué.

|Action de boîte aux lettres|Description|Administrateur|Délégué|Propriétaire|
|---|---|:---:|:---:|:---:|
|**Create**|Création d’un élément de calendrier. Notez que la création, l’envoi ou la réception d’un message ne sont pas audités.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>||
|**HardDelete**|Un message a été purgé du dossier Éléments récupérables.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**MoveToDeletedItems**|Un message a été supprimé et déplacé vers le dossier Éléments supprimés.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**SendAs**|Un message a été envoyé à l’aide de l’autorisation Envoyer en tant que.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|Un message a été envoyé à l’aide de l’autorisation Envoyer de la part de.|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>||
|**SoftDelete**|Un message a été définitivement supprimé ou supprimé (récupérable) du dossier Éléments supprimés. Les éléments supprimés récupérables sont déplacés vers le dossier Éléments récupérables.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|
|**Mettre à jour**|Un message ou une de ses propriétés a été modifié.|![Marque de vérification](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|![Coche](../media/checkmark.png)<sup>\*</sup>|

### <a name="verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type"></a>Vérifier que les actions de boîte aux lettres par défaut sont journalisées pour chaque type d’ouverture de session

L’audit de boîte aux lettres par défaut ajoute une nouvelle propriété *DefaultAuditSet* à toutes les boîtes aux lettres. La valeur de cette propriété indique si les actions de boîte aux lettres par défaut (gérées par Microsoft) sont auditées sur la boîte aux lettres.

Pour afficher la valeur sur les boîtes aux lettres utilisateur ou les boîtes aux lettres partagées, remplacez-la \<MailboxIdentity\> par le nom, l’alias, l’adresse e-mail ou le nom d’utilisateur principal (nom d’utilisateur) de la boîte aux lettres et exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Format-List DefaultAuditSet
```

Pour afficher la valeur sur Microsoft 365 boîtes aux lettres de groupe, remplacez \<MailboxIdentity\> par le nom, l’alias ou l’adresse e-mail de la boîte aux lettres partagée et exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> -GroupMailbox | Format-List DefaultAuditSet
```

La valeur `Admin, Delegate, Owner` indique :

- Les actions de boîte aux lettres par défaut pour les trois types d’ouverture de session sont auditées. Il s’agit de la seule valeur que vous verrez sur Microsoft 365 boîtes aux lettres de groupe.
- Un administrateur *n’a pas* modifié les actions de boîte aux lettres auditées pour tout type d’ouverture de session sur une boîte aux lettres utilisateur ou une boîte aux lettres partagée. Notez qu’il s’agit de l’état par défaut après l’activation initiale de l’audit de boîte aux lettres dans votre organisation.

Si un administrateur a déjà modifié les actions de boîte aux lettres auditées pour un type d’ouverture de session (à l’aide des paramètres *AuditAdmin*, *AuditDelegate* ou *AuditOwner* sur l’applet de commande **Set-Mailbox** ), la valeur de la propriété sera différente.

Par exemple, la valeur `Owner` de la propriété *DefaultAuditSet* sur une boîte aux lettres utilisateur ou une boîte aux lettres partagée indique :

- Les actions de boîte aux lettres par défaut pour le propriétaire de la boîte aux lettres sont auditées.
- Les actions de boîte aux lettres auditées pour les types de connexion et `Admin` de `Delegate` connexion ont été modifiées par rapport aux actions par défaut.

Une valeur vide pour la propriété *DefaultAuditSet* indique que les actions de boîte aux lettres des trois types d’ouverture de session ont été modifiées sur la boîte aux lettres utilisateur ou une boîte aux lettres partagée.

Pour plus d’informations, consultez la section [Modifier ou restaurer les actions de boîte aux lettres journalisées par défaut](#change-or-restore-mailbox-actions-logged-by-default) dans cet article

### <a name="display-the-mailbox-actions-that-are-being-logged-on-mailboxes"></a>Afficher les actions de boîte aux lettres en cours de journalisation sur les boîtes aux lettres

Pour afficher les actions de boîte aux lettres en cours de journalisation sur les boîtes aux lettres utilisateur ou les boîtes aux lettres partagées, remplacez \<MailboxIdentity\> par le nom, l’alias, l’adresse e-mail ou le nom d’utilisateur principal (nom d’utilisateur) de la boîte aux lettres, puis exécutez une ou plusieurs des commandes suivantes dans Exchange Online PowerShell.

> [!NOTE]
> Bien que vous puissiez ajouter le `-GroupMailbox` commutateur aux commandes **Get-Mailbox** suivantes pour Microsoft 365 boîtes aux lettres de groupe, ne croyez pas les valeurs retournées. Les actions de boîte aux lettres statiques et par défaut qui sont auditées pour les boîtes aux lettres de groupe Microsoft 365 sont décrites dans la section Actions de boîte [aux lettres de Microsoft 365 Groupe](#mailbox-actions-for-microsoft-365-group-mailboxes) plus haut dans cet article.

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

## <a name="change-or-restore-mailbox-actions-logged-by-default"></a>Modifier ou restaurer des actions de boîte aux lettres journalisées par défaut

Comme expliqué précédemment, l’un des principaux avantages de l’audit de boîte aux lettres par défaut est que vous n’avez pas besoin de gérer les actions de boîtes aux lettres auditées. Microsoft effectue cette opération pour vous et nous ajouterons automatiquement de nouvelles actions de boîte aux lettres à auditer par défaut lors de leur publication.

Toutefois, votre organisation peut être tenue d’auditer un autre ensemble d’actions de boîte aux lettres pour les boîtes aux lettres utilisateur et les boîtes aux lettres partagées. Les procédures de cette section vous montrent comment modifier les actions de boîte aux lettres auditées pour chaque type d’ouverture de session et comment revenir aux actions par défaut gérées par Microsoft.

> [!IMPORTANT]
> Si vous utilisez les procédures suivantes pour personnaliser les actions de boîte aux lettres qui sont enregistrées sur les boîtes aux lettres utilisateur ou les boîtes aux lettres partagées, les nouvelles actions de boîte aux lettres par défaut publiées par Microsoft ne seront pas automatiquement auditées sur ces boîtes aux lettres. Vous devez ajouter manuellement toutes les nouvelles actions de boîte aux lettres à votre liste personnalisée d’actions.

### <a name="change-the-mailbox-actions-to-audit"></a>Modifier les actions de boîte aux lettres pour l’audit

Vous pouvez utiliser les paramètres *AuditAdmin*, *AuditDelegate* ou *AuditOwner* sur l’applet de commande **Set-Mailbox** pour modifier les actions de boîte aux lettres auditées pour les boîtes aux lettres utilisateur et les boîtes aux lettres partagées (les actions auditées pour Microsoft 365 boîtes aux lettres de groupe ne peuvent pas être personnalisées).

Vous pouvez utiliser deux méthodes différentes pour spécifier les actions de boîte aux lettres :

- *Remplacez* (remplacez) les actions de boîte aux lettres existantes à l’aide de la syntaxe suivante : `action1,action2,...actionN`.
- *Ajoutez ou supprimez* des actions de boîte aux lettres sans affecter d’autres valeurs existantes à l’aide de cette syntaxe : `@{Add="action1","action2",..."actionN"}` ou `@{Remove="action1","action2",..."actionN"}`.

Cet exemple modifie les actions de boîte aux lettres d’administration pour la boîte aux lettres nommée « Gabriela Laureano » en remplaçant les actions par défaut par SoftDelete et HardDelete.

```PowerShell
Set-Mailbox -Identity "Gabriela Laureano" -AuditAdmin HardDelete,SoftDelete
```

Cet exemple montre comment ajouter l’action du propriétaire MailboxLogin à la boîte aux lettres laura@contoso.onmicrosoft.com.

```PowerShell
Set-Mailbox -Identity laura@contoso.onmicrosoft.com -AuditOwner @{Add="MailboxLogin"}
```

Cet exemple supprime l’action de délégué MoveToDeletedItems pour la boîte aux lettres Discussion d’équipe.

```PowerShell
Set-Mailbox -Identity "Team Discussion" -AuditDelegate @{Remove="MoveToDeletedItems"}
```

Quelle que soit la méthode que vous utilisez, la personnalisation des actions de boîte aux lettres auditées sur les boîtes aux lettres utilisateur ou les boîtes aux lettres partagées a les résultats suivants :

- Pour le type d’ouverture de session que vous avez personnalisé, les actions de boîte aux lettres auditées ne sont plus gérées par Microsoft.
- Le type d’ouverture de session que vous avez personnalisé n’est plus affiché dans la valeur de propriété *DefaultAuditSet* de la boîte aux lettres, comme [décrit précédemment](#verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type).

### <a name="restore-the-default-mailbox-actions"></a>Restaurer les actions de boîte aux lettres par défaut

> [!NOTE]
> Les procédures suivantes ne s’appliquent pas aux boîtes aux lettres de groupe Microsoft 365 (elles sont limitées aux actions par défaut, comme décrit [ici](#mailbox-actions-for-microsoft-365-group-mailboxes)).

Si vous avez personnalisé les actions de boîte aux lettres auditées sur une boîte aux lettres utilisateur ou une boîte aux lettres partagée, vous pouvez restaurer les actions de boîte aux lettres par défaut pour un ou tous les types de connexion à l’aide de cette syntaxe :

```PowerShell
Set-Mailbox -Identity <MailboxIdentity> -DefaultAuditSet <Admin | Delegate | Owner>
```

Vous pouvez spécifier plusieurs valeurs *DefaultAuditSet* séparées par des virgules

Cet exemple restaure les actions de boîte aux lettres auditées par défaut pour tous les types d’ouverture de session sur la boîte aux lettres mark@contoso.onmicrosoft.com.

```PowerShell
Set-Mailbox -Identity mark@contoso.onmicrosoft.com -DefaultAuditSet Admin,Delegate,Owner
```

Cet exemple restaure les actions de boîte aux lettres auditées par défaut pour le type d’ouverture de session Administrateur sur la boîte aux lettres chris@contoso.onmicrosoft.com, mais laisse les actions de boîte aux lettres auditées personnalisées pour les types d’ouverture de session Délégué et Propriétaire.

```PowerShell
Set-Mailbox -Identity chris@contoso.onmicrosoft.com -DefaultAuditSet Admin
```

La restauration des actions de boîte aux lettres auditées par défaut pour un type d’ouverture de session a les résultats suivants :

- La liste actuelle des actions de boîte aux lettres est remplacée par les actions de boîte aux lettres par défaut pour le type d’ouverture de session.
- Toutes les nouvelles actions de boîte aux lettres publiées par Microsoft sont automatiquement ajoutées à la liste des actions auditées pour le type d’ouverture de session.
- La valeur de la propriété *DefaultAuditSet* de la boîte aux lettres est mise à jour pour inclure le type d’ouverture de session restauré.

## <a name="turn-off-mailbox-auditing-on-by-default-for-your-organization"></a>Désactiver l’audit de boîte aux lettres par défaut pour votre organisation

Vous pouvez désactiver l’audit de boîte aux lettres par défaut pour l’ensemble de votre organisation en exécutant la commande suivante dans Exchange Online PowerShell :

```PowerShell
Set-OrganizationConfig -AuditDisabled $true
```

La désactivation de l’audit de boîte aux lettres par défaut a les résultats suivants :

- L’audit de boîte aux lettres est désactivé pour votre organisation.
- À partir du moment où vous avez désactivé l’audit de boîte aux lettres par défaut, aucune action de boîte aux lettres n’est auditée, même si l’audit est activé sur une boîte aux lettres (la propriété *AuditEnabled* sur la boîte aux lettres a la **valeur True**).
- L’audit de boîte aux lettres n’est pas activé pour les nouvelles boîtes aux lettres et la définition de la propriété *AuditEnabled* sur une boîte aux lettres nouvelle ou existante sur **True** est ignorée.
- Tous les paramètres d’association de contournement d’audit de boîte aux lettres (configurés à l’aide de l’applet **de commande Set-MailboxAuditBypassAssociation** ) sont ignorés.
- Les enregistrements d’audit de boîte aux lettres existants sont conservés jusqu’à ce que la limite d’âge du journal d’audit pour l’enregistrement expire.

### <a name="turn-on-mailbox-auditing-on-by-default"></a>Activer l’audit de boîte aux lettres par défaut

Pour réactiver l’audit de boîte aux lettres pour votre organisation, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Set-OrganizationConfig -AuditDisabled $false
```

## <a name="bypass-mailbox-audit-logging"></a>Ignorer l’enregistrement d’audit de boîte aux lettres :

Pour l’instant, vous ne pouvez pas désactiver l’audit de boîte aux lettres pour les boîtes aux lettres spécifiques lorsque l’audit de boîte aux lettres activé par défaut est activé dans votre organisation. Par exemple, la définition de la propriété de boîte aux *lettres AuditEnabled* sur **False** est ignorée.

Toutefois, vous pouvez toujours utiliser l’applet de commande **Set-MailboxAuditBypassAssociation** dans Exchange Online PowerShell pour empêcher *toutes les* actions de boîte aux lettres des utilisateurs spécifiés d’être journalisées, quel que soit l’endroit où les actions se produisent. Par exemple :

- Les actions du propriétaire de boîte aux lettres effectuées par les utilisateurs contournés ne sont pas journalisées.
- Les actions déléguées effectuées par les utilisateurs contournés sur les boîtes aux lettres d’autres utilisateurs (y compris les boîtes aux lettres partagées) ne sont pas journalisées.
- Les actions d’administration effectuées par les utilisateurs contournés ne sont pas journalisées.

Pour ignorer la journalisation d’audit de boîte aux lettres pour un utilisateur spécifique, remplacez \<MailboxIdentity\> par le nom, l’adresse de courrier, l’alias ou le nom d’utilisateur principal (nom d’utilisateur) de l’utilisateur, puis exécutez la commande suivante :

```PowerShell
Set-MailboxAuditBypassAssociation -Identity <MailboxIdentity> -AuditByPassEnabled $true
```

Pour vérifier que l’audit est contourné pour l’utilisateur spécifié, exécutez la commande suivante :

```PowerShell
Get-MailboxAuditBypassAssociation -Identity <MailboxIdentity> | Format-List AuditByPassEnabled
```

La valeur **True** indique que la journalisation de l’audit de boîte aux lettres est contournée pour l’utilisateur.

## <a name="more-information"></a>Plus d’informations

- Bien que la journalisation de l’audit de boîte aux lettres soit activée par défaut pour toutes les organisations, seuls les utilisateurs disposant de licences E5 retournent des événements de journal d’audit de boîte aux lettres dans [les recherches dans le journal d’audit dans le portail de conformité Microsoft Purview](search-the-audit-log-in-security-and-compliance.md) ou via [l’API d’activité de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-reference) **par défaut**.

  Pour récupérer les entrées du journal d’audit de boîte aux lettres pour les utilisateurs sans licence E5/A5/G5, vous pouvez utiliser l’une des solutions de contournement suivantes :

  - Activez manuellement l’audit de boîte aux lettres sur des boîtes aux lettres individuelles (exécutez la commande). `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true` Après cela, vous pouvez utiliser les recherches dans le journal d’audit dans le portail de conformité Microsoft Purview ou via l’API d’activité de gestion Office 365.

    > [!NOTE]
    > Si l’audit de boîte aux lettres semble déjà être activé sur la boîte aux lettres, mais que vos recherches ne retournent aucun résultat, remplacez la valeur du paramètre `$false` `$true`*AuditEnabled* par .

  - Utilisez les applets de commande suivantes dans Exchange Online PowerShell :
    - [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) pour rechercher des utilisateurs spécifiques dans le journal d’audit de boîte aux lettres.
    - [New-MailboxAuditLogSearch](/powershell/module/exchange/new-mailboxauditlogsearch) pour rechercher des utilisateurs spécifiques dans le journal d’audit de boîte aux lettres et envoyer les résultats par e-mail aux destinataires spécifiés.

  - Utilisez le centre d’administration Exchange (EAC) dans Exchange Online pour effectuer les actions suivantes :
    - [Exporter les journaux d’audit de boîte aux lettres](/Exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs)
    - [Exécuter un rapport d’accès aux boîtes aux lettres par des non-propriétaires](/Exchange/security-and-compliance/exchange-auditing-reports/non-owner-mailbox-access-report)

- Par défaut, les enregistrements du journal d’audit de boîte aux lettres sont conservés pendant 90 jours avant leur suppression. Vous pouvez modifier la limite d’âge des enregistrements de journal d’audit à l’aide du paramètre *AuditLogAgeLimit* sur l’applet **de commande Set-Mailbox** dans Exchange Online PowerShell. Toutefois, l’augmentation de cette valeur ne vous permet pas de rechercher des événements antérieurs à 90 jours dans le journal d’audit.

  Si vous augmentez la limite d’âge, vous devez utiliser l’applet de commande [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) dans Exchange Online PowerShell pour rechercher des enregistrements antérieurs à 90 jours dans le journal d’audit de la boîte aux lettres de l’utilisateur.

- Si vous avez modifié la propriété *AuditLogAgeLimit* d’une boîte aux lettres avant que l’audit de boîte aux lettres soit activé par défaut pour l’organisation, la limite d’âge du journal d’audit existante de la boîte aux lettres n’est pas modifiée. En d’autres termes, l’audit de boîte aux lettres activé par défaut n’affecte pas la limite d’âge actuelle pour les enregistrements d’audit de boîte aux lettres.

- Pour modifier la valeur *AuditLogAgeLimit* sur une boîte aux lettres de groupe Microsoft 365, vous devez inclure le `-GroupMailbox` commutateur dans la commande **Set-Mailbox**.

- Les enregistrements du journal d’audit de boîte aux lettres sont stockés dans un sous-dossier (nommé Audits) dans le dossier Éléments récupérables de la boîte aux *lettres* de chaque utilisateur. Gardez à l’esprit les éléments suivants concernant les enregistrements d’audit de boîte aux lettres et le dossier Éléments récupérables :

  - Les enregistrements d’audit de boîte aux lettres sont comptabilisés par rapport au quota de stockage du dossier Éléments récupérables, qui est de 30 Go par défaut (le quota d’avertissement est de 20 Go). Le quota de stockage est automatiquement porté à 100 Go (avec un quota d’avertissement de 90 Go) dans les cas suivants :
    - Une conservation est placée sur une boîte aux lettres.
    - La boîte aux lettres est affectée à une stratégie de rétention dans le Centre de conformité.

  - Les enregistrements d’audit de boîte aux lettres sont également comptabilisés par rapport à la [limite de dossiers pour le dossier Éléments récupérables](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-folder-limits). Un maximum de 3 millions d’éléments (enregistrements d’audit) peut être stocké dans le sous-dossier Audits.

    > [!NOTE]
    > Il est peu probable que l’audit de boîte aux lettres ait un impact par défaut sur le quota de stockage ou la limite de dossiers pour le dossier Éléments récupérables.

    - Vous pouvez exécuter la commande suivante dans Exchange Online PowerShell pour afficher la taille et le nombre d’éléments dans le sous-dossier Audits du dossier Éléments récupérables :

      ```PowerShell
      Get-MailboxFolderStatistics -Identity <MailboxIdentity> -FolderScope RecoverableItems | Where-Object {$_.Name -eq 'Audits'} | Format-List FolderPath,FolderSize,ItemsInFolder
      ```

    - Vous ne pouvez pas accéder directement à un enregistrement de journal d’audit dans le dossier Éléments récupérables ; Au lieu de cela, vous utilisez l’applet **de commande Search-MailboxAuditLog** ou recherchez le journal d’audit pour rechercher et afficher les enregistrements d’audit de boîte aux lettres.

- Si une boîte aux lettres est mise en attente ou affectée à une stratégie de rétention dans le Centre de conformité, les enregistrements du journal d’audit sont conservés pendant la durée définie par la propriété *AuditLogAgeLimit* de la boîte aux lettres (90 jours par défaut). Pour conserver les enregistrements de journal d’audit plus longtemps pour les boîtes aux lettres en attente, vous devez augmenter la valeur *AuditLogAgeLimit* de la boîte aux lettres.

- Dans un environnement multi-géographique, l’audit de boîte aux lettres inter-géographique n’est pas pris en charge. Par exemple, si un utilisateur se voit attribuer les autorisations d’accès à une boîte aux lettres partagée dans un autre emplacement géographique, les actions de boîte aux lettres effectuées par cet utilisateur ne sont pas enregistrées dans le journal d’audit de la boîte aux lettres partagée. Exchange événements d’audit administrateur sont actuellement disponibles uniquement pour l’emplacement par défaut.
