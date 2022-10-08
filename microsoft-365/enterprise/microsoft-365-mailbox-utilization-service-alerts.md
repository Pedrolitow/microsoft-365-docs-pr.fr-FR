---
title: Alertes du service d’utilisation de la boîte aux lettres
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
f1.keywords:
- NOCSH
description: Utilisez les conseils du service d’utilisation des boîtes aux lettres pour surveiller les boîtes aux lettres en attente qui atteignent leur quota de boîtes aux lettres.
ms.openlocfilehash: 35bff697727a77abc27555898e48106bc7070142
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68185400"
---
# <a name="service-advisories-for-mailbox-utilization-in-exchange-online-monitoring"></a>Conseils de service pour l’utilisation des boîtes aux lettres dans Exchange Online surveillance

Nous avons publié un nouvel avis de service Exchange Online qui vous informe des boîtes aux lettres en attente qui risquent d’atteindre ou de dépasser leur quota. Ces avis de service fournissent une visibilité sur le nombre de boîtes aux lettres de votre organisation qui peuvent nécessiter une intervention de l’administrateur.

Ces avis de service sont affichés dans le Centre d'administration Microsoft 365. Pour afficher ces avis de service, accédez à **Health** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**État des services**</a> >  **Exchange Online**, puis cliquez sur l’onglet **Problèmes actifs**. Voici un exemple d’avis de service d’utilisation de boîte aux lettres.

:::image type="content" alt-text="Alerte du service d’utilisation des boîtes aux lettres." source="../media/MailboxUtilizationServiceAlert.png" lightbox="../media/MailboxUtilizationServiceAlert.png":::

Pour afficher la liste des boîtes aux lettres qui approchent de leur quota de stockage, sélectionnez le lien mis en surbrillance dans la capture d’écran suivante pour accéder au rapport d’utilisation de votre boîte aux lettres. Ce lien s’affiche dans l’avis de service.

:::image type="content" alt-text="Lien vers le rapport d’utilisation de la boîte aux lettres." source="../media/LinkToMailboxUsageReport.png" lightbox="../media/LinkToMailboxUsageReport.png":::

Sinon, l’URL directe vers le rapport d’utilisation de la boîte aux lettres est <https://admin.microsoft.com/Adminportal/Home?source=applauncher#/reportsUsage/MailboxUsage>.

> [!NOTE]
> Les informations du rapport d’utilisation de la boîte aux lettres peuvent être 24 heures de retard sur l’alerte d’avis du service d’utilisation de votre boîte aux lettres.

## <a name="what-do-these-service-advisories-indicate"></a>Que indiquent ces avis de service ?

Les conseils de service relatifs à l’utilisation des boîtes aux lettres informent les administrateurs des boîtes aux lettres en attente qui approchent du quota de stockage de boîte aux lettres. Le type de conservation qui peut être placé sur les boîtes aux lettres inclut les conservations de litige, la conservation eDiscovery et les stratégies de rétention Microsoft 365 (configurées pour conserver les données). Lorsqu’une boîte aux lettres est en attente, les utilisateurs (ou les processus automatisés) ne peuvent pas supprimer définitivement des données de leur boîte aux lettres. Au lieu de cela, les administrateurs doivent configurer des stratégies de rétention MRM dans Exchange Online (en ligne avec les stratégies de conformité de leur organisation liées à la conservation des données) pour déplacer les données de la boîte aux lettres principale d’un utilisateur vers leur boîte aux lettres d’archivage. Si ce n’est pas le cas et qu’une boîte aux lettres en attente atteint un état critique ou d’avertissement, les administrateurs doivent [activer les boîtes aux lettres d’archivage](../compliance/enable-archive-mailboxes.md) et [activer l’archivage à extension automatique](../compliance/enable-autoexpanding-archiving.md) , puis s’assurer que la période de rétention de la stratégie d’archivage affectée à la boîte aux lettres (qui déplace le courrier de la boîte aux lettres principale vers la boîte aux lettres d’archivage) est suffisamment courte. Si rien n’est fait pour résoudre les problèmes de quota identifiés par l’avis du service d’utilisation des boîtes aux lettres, les utilisateurs peuvent ne pas être en mesure d’envoyer ou de recevoir des e-mails ou des invitations à une réunion.

Un avis de service pour l’utilisation des boîtes aux lettres contient des tableaux sur le nombre de boîtes aux lettres qui approchent de leur quota. Les sections suivantes décrivent les informations contenues dans ces tables et les actions que les administrateurs peuvent effectuer pour s’assurer que ces boîtes aux lettres ne dépassent pas leur quota.

> [!NOTE]
> Les avis de service contiennent des descriptions des propriétés de quota de boîte aux lettres qui apparaissent dans les colonnes des tables décrites dans les sections suivantes.

### <a name="mailboxes-on-hold-without-an-archive"></a>Boîtes aux lettres en attente sans archive

Le tableau suivant répertorie le nombre de boîtes aux lettres en attente qui approchent de leur quota, mais n’ont pas de boîte aux lettres d’archivage activée. Chaque colonne de la table identifie le quota spécifique et le nombre de boîtes aux lettres proches de ce quota.

| # Mailboxes ProhibitSendReceiveQuota (Avertissement)| # Mailboxes ProhibitSendReceiveQuota (Critique)** |# Mailboxes RecoverableItemsQuota (Avertissement)|# Mailboxes RecoverableItemsQuota (Critique)** |
|:--------------|:--------------|:------------------|:--------------- |
| 2             | 2             | 1                 | 0               |
||||

L’action que les administrateurs peuvent effectuer pour ces boîtes aux lettres consiste à activer la boîte aux lettres d’archivage et à s’assurer qu’une stratégie d’archivage MRM (qui est une stratégie de rétention MRM dans Exchange Online qui déplace les éléments vers la boîte aux lettres d’archivage) est appliquée à la boîte aux lettres afin que les éléments soient déplacés vers la boîte aux lettres d’archivage. Pour plus d’informations, consultez [Configurer une stratégie d’archivage et de suppression pour les boîtes aux lettres](../compliance/set-up-an-archive-and-deletion-policy-for-mailboxes.md).

Après avoir activé une boîte aux lettres d’archivage, nous vous recommandons d’augmenter le quota pour le dossier Éléments récupérables. Cela permet d’éviter de dépasser le quota du dossier Éléments récupérables pour les boîtes aux lettres qui sont mises en attente. Pour plus d’informations, consultez [Augmenter le quota d’éléments récupérables pour les boîtes aux lettres en attente](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

### <a name="mailboxes-on-hold-with-an-archive"></a>Boîtes aux lettres en attente avec une archive

Le tableau suivant répertorie le nombre de boîtes aux lettres en attente qui approchent de leur quota et dont une boîte aux lettres d’archivage est activée.

|# Mailboxes ProhibitSendReceiveQuota (Avertissement) |# Mailboxes ProhibitSendReceiveQuota (Critique) |# Mailboxes RecoverableItemsQuota (Avertissement) |# Mailboxes RecoverableItemsQuota (Critique)** |
|:--------------|:--------------|:------------------|:--------------- |
| 1             | 1             | 6                 | 0               |
||||

L’action que les administrateurs peuvent effectuer pour ces boîtes aux lettres consiste à augmenter le quota pour le dossier Éléments récupérables. Pour plus d’informations, consultez [Augmenter le quota d’éléments récupérables pour les boîtes aux lettres en attente](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

Les administrateurs doivent également s’assurer qu’une stratégie d’archivage MRM qui déplace des éléments vers la boîte aux lettres d’archivage est également appliquée aux boîtes aux lettres et que la période de rétention de la stratégie d’archivage est suffisamment courte pour que les éléments ne soient pas conservés trop longtemps dans la boîte aux lettres principale avant d’être déplacés vers l’archive.

> [!NOTE]
> Les stratégies d’archivage MRM déplacent également les éléments du dossier Éléments récupérables de la boîte aux lettres principale vers le dossier Éléments récupérables dans la boîte aux lettres d’archive correspondante. Cette fonctionnalité permet d’empêcher la boîte aux lettres de dépasser le quota pour le quota Éléments récupérables.

### <a name="mrm-retention-policies-in-your-organization"></a>Stratégies de rétention MRM dans votre organisation

Les avis de service pour l’utilisation des boîtes aux lettres peuvent également contenir une table contenant des informations sur les stratégies de rétention MRM dans votre organisation et si les boîtes aux lettres qui sont une stratégie de rétention ont ou non une boîte aux lettres d’archivage. Pour plus d’informations sur les stratégies de rétention, consultez [balises de rétention et stratégies de rétention dans Exchange Online](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies).

| RetentionPolicyGuid | MailboxType | HasMoveDumpsterToArchiveTag | HasMovePrimaryToArchiveTag | HasPersonalArchiveTag |  Boîtes aux lettres |
|:--------------|:--------------|:---------------|:---------------|:---------------|:--------------- |
| 6c041498-1611-5011-a058-1156ce60890c | PrimaryWithArchive | Vrai | Faux | Vrai | 398 |
| 6c041498-1611-5011-a058-1156ce60890c | Primaire | Vrai | Faux | Vrai | 10 |
| 749ceecc-d49d-4000-a9d5-594dbaea1e56 | PrimaryWithArchive | Faux | Vrai | Faux | 7  |
| 269f6a85-1234-4648-8cde-59bbc7bc67d0 | PrimaryWithArchive | True | True | True | 1 |
| 13fb778d-e1cb-4c44-5768-ad4282906c1f | PrimaryWithArchive | True | Vrai  | Faux | 1 |
|||||||

La liste suivante décrit chaque colonne du tableau précédent.

- **RetentionPolicyGuid** : GUID de la stratégie de rétention affectée aux boîtes aux lettres de votre organisation. Dans l’exemple précédent, il existe deux lignes distinctes pour la même stratégie de rétention. La première ligne indique le nombre de boîtes aux lettres avec une archive qui sont affectées à la stratégie. La deuxième ligne indique le nombre de boîtes aux lettres sans archive qui se voient attribuer la même stratégie.

   Pour obtenir plus d’informations sur la stratégie de rétention répertoriée dans cette colonne, exécutez la commande suivante dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-RetentionPolicy <GUID> | FL
   ```

   La valeur de la propriété **Name** est le nom de la stratégie de rétention qui s’affiche sur la page **Stratégies de rétention** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>.

- **MailboxType** : spécifie le type de boîte aux lettres à laquelle la stratégie est affectée. Les valeurs incluent *Primary* (boîtes aux lettres sans archive) ou *PrimaryWithArchive* (boîtes aux lettres avec une archive). Si la valeur de cette colonne est *Primary*, vous devez activer l’archive pour les boîtes aux lettres (la colonne **Boîte aux** lettres indique le nombre de ces boîtes aux lettres) qui sont affectées à la stratégie. Sinon, une stratégie d’archive ou une balise d’archive personnelle ne fonctionnera pas, car il n’y a pas d’archive vers qui déplacer des éléments.

- **HasMoveDumpsterToArchiveTag** : indique que la stratégie de rétention inclut une balise de rétention qui déplace les éléments du dossier Éléments récupérables (également appelé *dumpster*) dans la boîte aux lettres primaire vers le dossier Éléments récupérables dans l’archive. Ce type de balise de rétention est défini par un administrateur. Si la période de rétention de la balise Éléments récupérables est trop longue, la réduction de la période de rétention devrait empêcher les boîtes aux lettres d’approcher le quota du dossier Éléments récupérables. Par exemple, si la période de rétention est définie sur 30 jours, la réduire à trois ou cinq jours peut vous aider.  Pour plus d’informations, consultez [Augmenter le quota d’éléments récupérables pour les boîtes aux lettres en attente](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

- **HasMovePrimaryToArchiveTag** : indique s’il existe une balise de rétention par défaut « déplacer vers l’archive » (également appelée stratégie *d’archivage*) incluse dans la stratégie de rétention. Dans ce cas, les messages sont déplacés des dossiers standard de la boîte aux lettres principale vers la boîte aux lettres d’archivage. Ce type de balise de rétention est défini par un administrateur. Là encore, si la période de rétention de cette balise est trop courte, les utilisateurs peuvent avoir des problèmes avec l’atteinte continue du quota pour leur boîte aux lettres principale. La réduction de la période de rétention d’une stratégie d’archive peut aider à résoudre ce problème.

- **HasPersonalArchiveTag** : indique si la stratégie de rétention inclut une balise personnelle « déplacer vers l’archive ». Si la stratégie de rétention inclut une balise « déplacer vers l’archive » personnelle, les utilisateurs peuvent appliquer cette balise aux dossiers et aux messages de leur boîte aux lettres pour déplacer des éléments vers l’archive. Les utilisateurs peuvent également configurer une règle de boîte de réception pour déplacer des messages vers un dossier avec ce balisage appliqué. Dans les deux cas, cela peut aider à déplacer des éléments vers l’archive afin d’éviter d’atteindre le quota de leur boîte aux lettres principale.

- **Boîtes aux lettres** : indique le nombre de boîtes aux lettres (celles avec ou sans archive, indiquées dans la colonne **MailboxType** ) auxquelles la stratégie de rétention est affectée.

## <a name="how-often-will-i-see-these-service-advisories"></a>À quelle fréquence vais-je voir ces avis de service ?

Si vous ne prenez pas d’action pour résoudre les problèmes de quota, vous pouvez vous attendre à voir ce type d’avis de service tous les sept jours. Les avis de service suivants peuvent contenir des nombres de boîtes aux lettres plus élevés pour les autres boîtes aux lettres qui approchent de leur quota. Si vous prenez des mesures pour résoudre les problèmes de quota, cet avis de service se produit uniquement lorsqu’une autre boîte aux lettres avec des problèmes de quota est identifiée.

## <a name="more-information"></a>Plus d’informations

- Pour plus d’informations sur la résolution et la résolution des problèmes de boîte aux lettres d’archivage, consultez [la résolution des problèmes de Microsoft Purview](/office365/troubleshoot/microsoft-365-compliance-welcome).

- Pour obtenir des conseils sur l’identification des conservations placées sur une boîte aux lettres, consultez [Comment identifier le type de conservation placé sur une boîte aux lettres](../compliance/identify-a-hold-on-an-exchange-online-mailbox.md).
