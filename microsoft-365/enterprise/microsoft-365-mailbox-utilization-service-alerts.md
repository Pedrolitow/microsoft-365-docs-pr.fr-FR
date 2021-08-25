---
title: Alertes du service d’utilisation des boîtes aux lettres
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- NOCSH
description: Utilisez les alertes du service d’utilisation des boîtes aux lettres pour surveiller les boîtes aux lettres en attente qui atteignent leur quota de boîte aux lettres.
ms.openlocfilehash: f6ce0ad5d7f4affd5d0f4a108be0f0fbebe54766
ms.sourcegitcommit: f358e321f7e81eff425fe0f0db1be0f3348d2585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2021
ms.locfileid: "58508560"
---
# <a name="service-alerts-for-mailbox-utilization-in-exchange-online-monitoring"></a>Alertes de service pour l’utilisation des boîtes aux lettres Exchange Online surveillance

Nous avons publié une nouvelle alerte de service Exchange Online qui vous informe des boîtes aux lettres en attente qui risquent d’atteindre ou de dépasser leur quota. Ces alertes de service fournissent une visibilité sur le nombre de boîtes aux lettres dans votre organisation qui peuvent nécessiter une intervention de l’administrateur.

Ces alertes de service sont affichées dans le Centre d’administration Microsoft 365. Pour afficher ces alertes de service, Exchange Online l’onglet Problèmes  >    >   actifs.  Voici un exemple d’alerte de service d’utilisation de boîte aux lettres.

![Alerte du service d’utilisation des boîtes aux lettres](../media/MailboxUtilizationServiceAlert.png)

Pour afficher la liste des boîtes aux lettres qui approchent de leur quota de stockage (appelé rapport d’utilisation des boîtes aux *lettres),* cliquez sur le lien mis en surbrillant dans la capture d’écran suivante. Ce lien s’affiche dans l’alerte de service.

![Lien vers le rapport d’utilisation des boîtes aux lettres](../media/LinkToMailboxUsageReport.png)

Sinon, l’URL directe vers le rapport d’utilisation de la boîte aux lettres est <https://admin.microsoft.com/Adminportal/Home?source=applauncher#/reportsUsage/MailboxUsage> .

## <a name="what-do-these-service-alerts-indicate"></a>Qu’indiquent ces alertes de service ?

Les alertes de service pour l’utilisation des boîtes aux lettres informent les administrateurs des boîtes aux lettres en attente qui approchent du quota de stockage de boîte aux lettres. Le type de conservation qui peut être placé sur des boîtes aux lettres comprend les conservations pour litige, les conservations eDiscovery et les stratégies de rétention Microsoft 365 (configurées pour conserver les données). Lorsqu’une boîte aux lettres est en attente, les utilisateurs (ou processus automatisés) ne peuvent pas supprimer définitivement les données de leur boîte aux lettres. Au lieu de cela, les administrateurs doivent configurer des stratégies de rétention mrM dans Exchange Online (en ligne avec les stratégies de conformité de leur organisation liées à la rétention des données) pour déplacer les données de la boîte aux lettres principale d’un utilisateur vers sa boîte aux lettres d’archivage. Si ce n’est pas le cas et qu’une [](../compliance/enable-archive-mailboxes.md) boîte aux lettres [](../compliance/enable-unlimited-archiving.md) en conservation atteint un état critique ou d’avertissement, les administrateurs doivent activer les boîtes aux lettres d’archivage et activer l’archivage à extension automatique, puis s’assurer que la période de rétention de la stratégie d’archivage affectée à la boîte aux lettres (qui déplace le courrier de la boîte aux lettres principale vers la boîte aux lettres d’archivage) est suffisamment courte. Si rien n’est fait pour résoudre les problèmes de quota identifiés par les alertes du service d’utilisation des boîtes aux lettres, les utilisateurs peuvent ne pas être en mesure d’envoyer ou de recevoir des messages électroniques ou des invitations à une réunion.

Une alerte de service pour l’utilisation des boîtes aux lettres contient des tableaux sur le nombre de boîtes aux lettres qui approchent de leur quota. Les sections suivantes décrivent les informations de ces tableaux et les actions que les administrateurs peuvent prendre pour s’assurer que ces boîtes aux lettres ne dépassent pas leur quota.

> [!NOTE]
> Les alertes de service contiennent des descriptions des propriétés de quota de boîte aux lettres qui apparaissent dans les colonnes des tableaux décrits dans les sections suivantes.

### <a name="mailboxes-on-hold-without-an-archive"></a>Boîtes aux lettres en attente sans archive

Le tableau suivant répertorie le nombre de boîtes aux lettres en attente qui approchent de leur quota, mais n’ont pas de boîte aux lettres d’archivage activée. Chaque colonne du tableau identifie le quota spécifique et le nombre de boîtes aux lettres proches de ce quota.

| # Mailboxes ProhibitSendReceiveQuota (Avertissement)| # Mailboxes ProhibitSendReceiveQuota (Critical)** |# Mailboxes RecoverableItemsQuota (Avertissement)|# Mailboxes RecoverableItemsQuota (Critical)** |
|:--------------|:--------------|:------------------|:--------------- |
| 2              | 2              | 1                  | 0               |
||||

L’action que les administrateurs peuvent prendre pour ces boîtes aux lettres consiste à activer la boîte aux lettres d’archivage et à s’assurer qu’une stratégie d’archivage MRM (qui est une stratégie de rétention MRM dans Exchange Online qui déplace des éléments vers la boîte aux lettres d’archivage) est appliquée à la boîte aux lettres afin que les éléments soient déplacés vers la boîte aux lettres d’archivage. Pour plus d’informations, voir [Configurer une stratégie d’archivage](../compliance/set-up-an-archive-and-deletion-policy-for-mailboxes.md)et de suppression pour les boîtes aux lettres.

Après avoir activé une boîte aux lettres d’archivage, nous vous recommandons d’augmenter le quota pour le dossier Éléments récupérables. Cela permet d’éviter le dépassement du quota du dossier Éléments récupérables pour les boîtes aux lettres placées en attente. Pour plus d’informations, voir [Augmenter le quota d’éléments récupérables pour les boîtes aux lettres en attente.](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md)

### <a name="mailboxes-on-hold-with-an-archive"></a>Boîtes aux lettres en attente avec une archive

Le tableau suivant répertorie le nombre de boîtes aux lettres en attente qui approchent de leur quota et dont la boîte aux lettres d’archivage est activée.

|# Mailboxes ProhibitSendReceiveQuota (Avertissement) |# Mailboxes ProhibitSendReceiveQuota (Critical) |# Mailboxes RecoverableItemsQuota (Avertissement) |# Mailboxes RecoverableItemsQuota (Critical)** |
|:--------------|:--------------|:------------------|:--------------- |
| 1              | 1              | 6                  | 0               |
||||

L’action que les administrateurs peuvent prendre pour ces boîtes aux lettres consiste à augmenter le quota pour le dossier Éléments récupérables. Pour plus d’informations, voir [Augmenter le quota d’éléments récupérables pour les boîtes aux lettres en attente.](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md)

Les administrateurs doivent également s’assurer qu’une stratégie d’archivage MRM qui déplace des éléments vers la boîte aux lettres d’archivage est également appliquée aux boîtes aux lettres et que la période de rétention de la stratégie d’archivage est suffisamment courte pour que les éléments ne restent pas trop longtemps dans la boîte aux lettres principale avant d’être déplacés vers l’archive.

> [!NOTE]
> Les stratégies d’archivage MRM déplacent également les éléments du dossier Éléments récupérables de la boîte aux lettres principale vers le dossier Éléments récupérables de la boîte aux lettres d’archivage correspondante. Cette fonctionnalité permet d’empêcher la boîte aux lettres de dépasser le quota d’éléments récupérables.

### <a name="mrm-retention-policies-in-your-organization"></a>Stratégies de rétention MRM dans votre organisation

Les alertes de service pour l’utilisation des boîtes aux lettres peuvent également contenir un tableau contenant des informations sur les stratégies de rétention MRM de votre organisation et indiquent si les boîtes aux lettres qui sont une stratégie de rétention ont une boîte aux lettres d’archivage. Pour plus d’informations sur les stratégies de rétention, voir [Balises et stratégies](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies)de rétention dans Exchange Online .

| RetentionPolicyGuid | MailboxType | HasMoveDumpsterToArchiveTag | HasMovePrimaryToArchiveTag | HasPersonalArchiveTag |  Boîtes aux lettres |
|:--------------|:--------------|:---------------|:---------------|:---------------|:--------------- |
| 6c041498-1611-5011-a058-1156ce60890c | PrimaryWithArchive | Vrai | False | True | 398 |
| 6c041498-1611-5011-a058-1156ce60890c | Primaire | Vrai | False | True | 10  |
| 749ceecc-d49d-4000-a9d5-594dbaea1e56 | PrimaryWithArchive | False | True | Faux | 7  |
| 269f6a85-1234-4648-8cde-59bbc7bc67d0 | PrimaryWithArchive | True | True | True | 1  |
| 13fb778d-e1cb-4c44-5768-ad4282906c1f | PrimaryWithArchive | True | True  | Faux | 1  |
|||||||

La liste suivante décrit chaque colonne du tableau précédent.

- **RetentionPolicyGuid :** GUID de la stratégie de rétention attribuée aux boîtes aux lettres de votre organisation. Dans l’exemple précédent, il existe deux lignes distinctes pour la même stratégie de rétention. La première ligne indique le nombre de boîtes aux lettres dont la stratégie est affectée à une archive. La deuxième ligne indique le nombre de boîtes aux lettres sans archive affectées à la même stratégie.

   Pour obtenir plus d’informations sur la stratégie de rétention répertoriée dans cette colonne, exécutez la commande suivante [dans Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-RetentionPolicy <GUID> | FL
   ```

   La valeur de la **propriété Name** est le nom de la stratégie de rétention qui s’affiche sur la **page** Stratégies de rétention dans le Centre d’administration Exchange rétention.

- **MailboxType**: spécifie le type de boîtes aux lettres à qui la stratégie est affectée. Les valeurs *sont Primary* (boîtes aux lettres sans archive) ou *PrimaryWithArchive* (boîtes aux lettres avec archive). Si la valeur de cette colonne est *Primary,* vous devez activer l’archive pour les boîtes aux lettres (la colonne **Mailbox** indique le nombre de ces boîtes aux lettres) qui sont affectées à la stratégie. Dans le cas contraire, une stratégie d’archivage ou une balise d’archive personnelle ne fonctionne pas, car il n’existe pas d’archive vers qui déplacer des éléments.

- **HasMoveDumpsterToArchiveTag**: indique que la stratégie de rétention inclut une balise de rétention qui déplace les éléments du dossier Éléments récupérables (également appelé benne) de la boîte aux lettres principale vers le dossier Éléments récupérables de l’archive. Ce type de balise de rétention est définie par un administrateur. Si la période de rétention de la balise éléments récupérables est trop longue, la réduction de la période de rétention devrait aider à empêcher les boîtes aux lettres d’approcher le quota du dossier Éléments récupérables. Par exemple, si la période de rétention est définie sur 30 jours, le fait de la réduire à trois ou cinq jours peut vous aider.  Pour plus d’informations, voir [Augmenter le quota d’éléments récupérables pour les boîtes aux lettres en attente.](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md)

- **HasMovePrimaryToArchiveTag**: indique si une balise de rétention « déplacer vers l’archive » par défaut (également appelée stratégie *d’archivage)* est incluse dans la stratégie de rétention. Dans ce cas, les messages sont déplacés des dossiers ordinaires de la boîte aux lettres principale vers la boîte aux lettres d’archivage. Ce type de balise de rétention est définie par un administrateur. Là encore, si la période de rétention de cette balise est trop courte, les utilisateurs peuvent avoir des difficultés à atteindre continuellement le quota de leur boîte aux lettres principale. La réduction de la période de rétention d’une stratégie d’archivage peut aider à résoudre ce problème.

- **HasPersonalArchiveTag**: indique si la stratégie de rétention inclut une balise personnelle « déplacer vers l’archive ». Si la stratégie de rétention inclut une balise personnelle « déplacer vers l’archive », les utilisateurs peuvent appliquer cette balise aux dossiers et aux messages de leur boîte aux lettres pour déplacer des éléments vers l’archive. Les utilisateurs peuvent également configurer une règle de boîte de réception pour déplacer des messages vers un dossier avec cette balise appliquée. Dans les deux cas, cela peut aider à déplacer des éléments vers l’archive pour éviter d’atteindre le quota pour leur boîte aux lettres principale.

- **Boîtes aux** lettres : indique le nombre de boîtes aux lettres (celles avec ou sans archive, indiquées dans la colonne **MailboxType)** à laquelle la stratégie de rétention est affectée.

## <a name="how-often-will-i-see-these-service-alerts"></a>À quelle fréquence ces alertes de service seront-elles consultez-vous ?

Si vous ne prenez aucune mesure pour résoudre les problèmes de quota, vous pouvez vous attendre à voir ce type d’alerte de service tous les quatre jours. Les alertes de service suivantes peuvent contenir des nombres de boîtes aux lettres plus élevés pour les autres boîtes aux lettres qui approchent de leur quota. Si vous prenez des mesures pour résoudre les problèmes de quota, cette alerte de service se produit uniquement lorsqu’une autre boîte aux lettres avec des problèmes de quota est identifiée.

## <a name="more-information"></a>Plus d’informations

- Pour plus d’informations sur le dépannage et la résolution des problèmes de boîte aux lettres d’archivage, voir [Microsoft 365 de conformité.](/office365/troubleshoot/microsoft-365-compliance-welcome)

- Pour obtenir des instructions sur l’identification des mises en attente placées sur une boîte aux lettres, voir Comment identifier le type de mise en attente [placée sur une boîte aux lettres](../compliance/identify-a-hold-on-an-exchange-online-mailbox.md).
