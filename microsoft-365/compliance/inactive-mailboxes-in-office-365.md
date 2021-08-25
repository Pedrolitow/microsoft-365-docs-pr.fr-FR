---
title: Vue d’ensemble des boîtes aux lettres inactives
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 1fbd74e8-7a60-4157-afe8-fe79f05d2038
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment conserver le contenu de la boîte aux lettres pour les anciens employés en la transformant en boîte aux lettres inactive.
ms.openlocfilehash: 7c2e4ce0bb60d29652d66a778c16579646392d21
ms.sourcegitcommit: f358e321f7e81eff425fe0f0db1be0f3348d2585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2021
ms.locfileid: "58507255"
---
# <a name="overview-of-inactive-mailboxes"></a>Vue d’ensemble des boîtes aux lettres inactives

Votre organisation peut avoir besoin de conserver le courrier électronique des anciens employés après leur départ. En fonction des exigences de rétention de votre organisation, il se peut que vous deviez conserver le contenu de la boîte aux lettres pendant quelques mois ou quelques années après la fin du contrat, ou indéfiniment. Quel que soit le temps nécessaire pour conserver les messages électroniques, vous pouvez créer des boîtes aux lettres inactives pour conserver la boîte aux lettres des anciens employés.

## <a name="what-are-inactive-mailboxes"></a>Que sont les boîtes aux lettres inactives ?

Lorsqu’un employé quitte votre organisation (ou part en congé prolongé), vous pouvez supprimer Microsoft 365 compte. Les données de boîte aux lettres de l’employé sont conservées pendant 30 jours après la suppression du compte. Pendant cette période, vous pouvez toujours récupérer les données de boîte aux lettres en supprimant le compte. Après 30 jours, les données sont définitivement supprimées.

Toutefois, si votre organisation doit conserver le contenu de la boîte aux lettres pour les anciens employés, vous pouvez transformer la boîte aux lettres en boîte aux lettres inactive en plaçant la boîte aux lettres en conservation pour litige ou en appliquant une stratégie de rétention Microsoft 365 à la boîte aux lettres dans le Centre de conformité Microsoft 365, puis en supprimant le compte Microsoft 365 correspondant. Le contenu d’une boîte aux lettres inactive est conservé pendant toute la durée de la conservation pour litige appliquée à la boîte aux lettres ou de la période de rétention de la stratégie de rétention qui lui est appliquée avant la suppression de la boîte aux lettres. You can still recover the corresponding user account for a 30-day period. Toutefois, après 30 jours, la boîte aux lettres inactive est conservée dans Microsoft 365 jusqu’à la suppression de la conservation ou de la stratégie de rétention.

> [!IMPORTANT]
> À mesure que nous continuons d’investir de différentes façons pour conserver le contenu des boîtes aux lettres, nous annonceons le retrait des conservations In-Place dans le Centre d’administration Exchange gestion. Cela signifie que vous devez utiliser les conservations pour litige et Microsoft 365 rétention pour créer une boîte aux lettres inactive. À compter du 1er juillet 2020, vous ne pourrez plus créer de In-Place de Exchange Online. Toutefois, vous pourrez toujours modifier la durée d’une In-Place placée sur une boîte aux lettres inactive. Toutefois, à compter du 1er octobre 2020, vous ne pourrez pas modifier la durée de la durée de la durée de la période de attente. Vous ne pourrez supprimer une boîte aux lettres inactive qu’en supprimant la In-Place de la boîte aux lettres. Les boîtes aux lettres inactives existantes qui sont en conservation In-Place sont conservées jusqu’à ce que la conservation soit supprimée. Pour plus d’informations sur In-Place de la In-Place seront retirés, voir [Retrait des outils eDiscovery hérités.](legacy-ediscovery-retirement.md)

## <a name="inactive-mailboxes-and-microsoft-365-retention-policies"></a>Boîtes aux lettres inactives et stratégies Microsoft 365 rétention

Outre la conservation pour litige, l’utilisation de la nouvelle Microsoft 365 stratégie de rétention dans le Centre de conformité Microsoft 365 est une autre façon de rendre une boîte aux lettres inactive. To use a retention policy to make an inactive mailbox:

- Il doit être configuré pour conserver le contenu, puis le conserver, puis le supprimer. Si une stratégie de rétention est configurée pour supprimer uniquement du contenu, une boîte aux lettres à qui la stratégie est appliquée ne devient pas inactive lorsque le compte d’utilisateur est supprimé.

- La stratégie doit être appliquée aux boîtes aux lettres Exchange ou aux emplacements Skype Entreprise (car le contenu associé à Skype est stocké dans la boîte aux lettres de l'utilisateur).

- Elle peut reposer sur une requête pour conserver uniquement les éléments correspondant à une requête de recherche.

Pour plus d’informations sur les stratégies de rétention, voir [En savoir plus sur les stratégies de rétention et les étiquettes de rétention.](retention.md)

Si vous utilisez une stratégie de rétention pour rendre une boîte aux lettres inactive, Microsoft 365 continue de traiter la stratégie de rétention sur la boîte aux lettres inactive. En d'autres termes, si la stratégie de rétention est configurée pour conserver puis supprimer le contenu, les éléments sont déplacés vers le dossier Éléments récupérables à l'expiration de la durée de conservation avant d'être supprimés de la boîte aux lettres inactive. Si la stratégie de rétention n’est pas configurée pour supprimer des éléments, les éléments qui n’ont pas été supprimés définitivement par l’utilisateur (avant que la boîte aux lettres ne devienne inactive) ne sont pas déplacés vers le dossier Éléments récupérables et sont conservés indéfiniment une fois que la boîte aux lettres devient inactive.

Vous pouvez envisager de créer une stratégie Microsoft 365 rétention spécifique aux boîtes aux lettres inactives. Voici quelques bonnes raisons pour le faire et quelques éléments à garder à l'esprit.

- Vous pouvez configurer la stratégie de rétention pour conserver le contenu de la boîte aux lettres uniquement le temps de répondre aux exigences de votre organisation concernant les anciens employés.

- C’est un bon moyen d’identifier les boîtes aux lettres inactives, car la stratégie de rétention sera appliquée uniquement aux boîtes aux lettres inactives.

- Vous pouvez identifier rapidement la stratégie de rétention attribuée aux boîtes aux lettres inactives de votre organisation. Cela facilite la modification des paramètres de rétention (ou de suppression) si nécessaire. Cela facilite également la suppression définitive d’une boîte aux lettres inactive, car vous pouvez la supprimer de la stratégie à l’aide du Centre de conformité Microsoft 365. Dans le cas contraire, vous devez utiliser Exchange Online PowerShell pour supprimer une conservation pour litige d’une boîte aux lettres inactive ou utiliser le Centre de sécurité & conformité PowerShell pour exclure une boîte aux lettres inactive d’une stratégie de rétention Microsoft 365 à l’échelle de l’organisation.

- Si vous créez une stratégie de rétention Microsoft 365 spécifiquement pour les boîtes aux lettres inactives, vous pouvez ajouter un maximum de 1 000 boîtes aux lettres à la stratégie. Si vous êtes une grande organisation, vous de devez peut-être créer plusieurs stratégies Microsoft 365 rétention à utiliser pour les boîtes aux lettres inactives.

> [!CAUTION]
> Si vous utilisez une stratégie de rétention pour rendre une boîte aux lettres inactive, ne modifiez pas ou ne supprimez pas le nom d’utilisateur principal (UPN) de la boîte aux lettres avant de supprimer le compte d’utilisateur correspondant. En outre, ne modifiez pas l’adresse SMTP principale (dérivée de l’UPN) ni ne supprimez cette adresse de messagerie de la liste des adresses SMTP secondaires associées à la boîte aux lettres avant de rendre la boîte aux lettres inactive. Si vous modifiez l’UPN ou les adresses de messagerie (qui étaient affectées à la boîte aux lettres au moment où la stratégie de rétention lui a été appliquée), puis supprimez le compte d’utilisateur pour rendre la boîte aux lettres inactive, vous ne pourrez pas supprimer la boîte aux lettres inactive lorsque vous n’aurez plus besoin de la conserver. En raison du fait que vous ne pouvez pas supprimer la boîte aux lettres inactive de la stratégie de rétention à l’aide d’un UPN ou d’une adresse de messagerie (pour identifier la boîte aux lettres inactive) qui est différente de celles qui existaient lorsque la stratégie de rétention a été initialement appliquée à la boîte aux lettres. Pour plus d’informations sur la suppression de boîtes aux lettres inactives, voir Supprimer une boîte aux lettres [inactive dans Office 365](delete-an-inactive-mailbox.md).

## <a name="inactive-mailboxes-and-ediscovery-case-holds"></a>Boîtes aux lettres inactives et conservations eDiscovery

Si une mise en attente associée à un cas eDiscovery dans Centre de conformité Microsoft 365 est placée sur une boîte aux lettres, puis que la boîte aux lettres ou le compte de l’utilisateur est supprimé, la boîte aux lettres devient inactive. However, we don't recommend using eDiscovery case holds to make a mailbox inactive. That's because eDiscovery cases are intended for specific, time-bound cases related to a legal issue. At some point, a legal case will probably end and the holds associated with the case will be removed and the eDiscovery case will be closed. In fact, if a hold that's placed on an inactive mailbox is associated with an eDiscovery case, and then the hold is released or the eDiscovery case is closed (or deleted), the inactive mailbox will be permanently deleted. En outre, vous ne pouvez pas créer une attente eDiscovery basée sur le temps. Cela signifie que le contenu d’une boîte aux lettres inactive est conservé définitivement ou jusqu’à ce que la boîte aux lettres inactive soit supprimée. Par conséquent, nous vous recommandons d’utiliser une conservation pour litige ou une stratégie de rétention pour les boîtes aux lettres inactives.

Pour plus d’informations sur les cas et les cas de découverte électronique, consultez les cas [eDiscovery.](./get-started-core-ediscovery.md)

## <a name="inactive-mailboxes-and-labels"></a>Boîtes aux lettres et étiquettes inactives

Les étiquettes de rétention vous aident à classifier les données de courrier électronique de votre organisation pour la gouvernance et à appliquer des règles de rétention basées sur cette classification. Une étiquette de rétention peut être appliquée à un élément de courrier électronique manuellement par les utilisateurs ou automatiquement par les administrateurs, et un élément de courrier ne peut être affecté qu’à une seule étiquette. Si une étiquette est affectée à un seul élément de messagerie de la boîte aux lettres d’un utilisateur (et qu’elle est configurée pour conserver ou conserver puis supprimer l’élément) et que la boîte aux lettres ou le compte de l’utilisateur est supprimé, la boîte aux lettres devient inactive. Comme pour les conservations de cas eDiscovery, nous vous déconseillons d’utiliser des étiquettes de rétention pour rendre une boîte aux lettres inactive. Au lieu de cela, nous vous recommandons d’utiliser une conservation pour litige ou une stratégie de rétention. Dans le cas des étiquettes de rétention, il se peut que vous ne réalisez pas qu’une étiquette de rétention a été appliquée à un élément de courrier électronique, puis que vous rendiez par inadvertance une boîte aux lettres inactive lorsque vous supprimez le compte de l’utilisateur.

Pour plus d’informations sur les stratégies de rétention et les étiquettes de rétention, voir En savoir plus sur les stratégies de rétention et les étiquettes de [rétention dans Office 365](retention.md).

## <a name="inactive-mailboxes-and-auto-expanding-archives"></a>Boîtes aux lettres inactives et archives à extension automatique

Une boîte aux lettres inactive configurée avec une archive à extension automatique ne peut pas être récupérée ou restaurée. Dans les situations où il est nécessaire de récupérer des données à partir d’une boîte aux lettres inactive avec une archive à développement automatique, nous vous recommandons d’utiliser l’outil de recherche de contenu pour exporter les données de la boîte aux lettres, puis les importer vers une autre boîte aux lettres. Pour obtenir des instructions détaillées sur la recherche dans une boîte aux lettres inactive et l’exportation des résultats de la recherche, voir :

- [Recherche de contenu](content-search.md)

- [Exporter les résultats de recherche de contenu](export-search-results.md)

## <a name="inactive-mailboxes-and-exchange-mrm-retention-policies"></a>Boîtes aux lettres inactives et stratégies de rétention Exchange MRM

Si une stratégie de rétention Exchange (la fonctionnalité gestion des enregistrements de messagerie ou MRM dans Exchange Online) a été appliquée à la boîte aux  lettres lorsqu’elle est inactive, toutes les stratégies de suppression (qui sont des balises de rétention configurées avec une action de rétention Supprimer) continueront d’être traitées sur la boîte aux lettres inactive. En d'autres termes, les éléments marqués avec une stratégie de suppression seront déplacés vers le dossier Éléments récupérables à l'expiration de la période de rétention. Ces éléments sont supprimés définitivement de la boîte aux lettres inactive à l'expiration de la durée de la conservation. Si aucune durée de conservation n'est spécifiée pour la boîte aux lettres inactive, les éléments du dossier Éléments récupérables seront conservés indéfiniment.

À l'inverse, les stratégies d'archivage (qui sont des balises de rétention configurées avec une action de rétention **MoveToArchive** ) incluses dans la stratégie de rétention attribuée à une boîte aux lettres inactive sont ignorées. Cela signifie que les éléments dans une boîte aux lettres inactive qui sont marqués avec une stratégie d'archivage restent dans la boîte aux lettres principale à l'expiration de la période de rétention. Ils ne sont pas déplacés vers la boîte aux lettres d'archivage ni vers le dossier Éléments récupérables dans la boîte aux lettres d'archivage. Ils seront conservés indéfiniment.

## <a name="creating-an-inactive-mailbox"></a>Création d’une boîte aux lettres inactive

Pour rendre une boîte aux lettres inactive, une licence Exchange Online Plan 2 (ou une licence Exchange Online Plan 1 avec une licence de module Archivage Exchange Online) doit lui être attribuée afin qu’une conservation pour litige ou une stratégie de rétention Microsoft 365 puisse être appliquée à la boîte aux lettres avant sa suppression. Une fois le compte d’utilisateur supprimé, toute licence Exchange Online associée au compte d’utilisateur peut être assignée à un nouvel utilisateur.

Le tableau suivant résume le processus de création d'une boîte aux lettres inactive pour différents scénarios de rétention. Pour plus d’informations, voir [Gérer les boîtes aux lettres inactives.](create-and-manage-inactive-mailboxes.md)

****

|À...|Vous devez…|Résultat|
|---|---|---|
|Conserver le contenu de la boîte aux lettres indéfiniment après le départ d’un employé de l’organisation|Placez la boîte aux lettres en conservation pour litige ou appliquez une stratégie Microsoft 365 rétention (configurée pour conserver le contenu) à la boîte aux lettres. <br/> Ne spécifiez pas de durée de conservation pour la conservation pour litige ou ne configurez pas la stratégie de rétention pour supprimer des éléments. Vous pouvez également utiliser une stratégie de rétention qui conserve les éléments indéfiniment. <br/> Supprimez le compte d’Microsoft 365 utilisateur.|Tout le contenu de la boîte aux lettres inactive, y compris les éléments du dossier Éléments récupérables, est conservé indéfiniment.|
|Conserver le contenu de la boîte aux lettres pendant une période donnée après le départ d'un employé de l'organisation et le supprimer|Appliquer une stratégie Microsoft 365 rétention à la boîte aux lettres. <br/> Configurez la stratégie de rétention pour conserver puis supprimer des éléments à l’expiration de la période de rétention. <br/> Supprimez le compte d’Microsoft 365 utilisateur.|Lorsque la période de rétention d’un élément de boîte aux lettres expire, l’élément est déplacé vers le dossier Éléments récupérables, puis supprimé définitivement (purgé) de la boîte aux lettres inactive à l’expiration de la période de rétention des éléments supprimés (pour les boîtes aux lettres Exchange). La période de rétention de la stratégie de rétention Microsoft 365 peut être configurée en fonction de la date d’origine de réception ou de création d’un élément de boîte aux lettres, ou de sa dernière modification.|
|

**REMARQUE :** Si une conservation pour litige est déjà appliquée à une boîte aux lettres ou si une stratégie de rétention Microsoft 365 (configurée pour conserver ou conserver puis supprimer le contenu) est déjà appliquée à la boîte aux lettres, il vous s agit de supprimer le compte d’utilisateur correspondant pour créer une boîte aux lettres inactive.

## <a name="managing-inactive-mailboxes"></a>Gestion des boîtes aux lettres inactives

Une fois que la boîte aux lettres est inactive, vous pouvez effectuer différentes tâches de gestion.

- **Modifier la durée de la boîte aux lettres inactive.** Une fois qu’une boîte aux lettres est inactive, vous pouvez modifier la durée de la conservation pour litige ou Microsoft 365 stratégie de rétention appliquée à la boîte aux lettres inactive. Pour obtenir des procédures pas à pas, voir Modifier la durée de la boîte aux lettres [inactive.](change-the-hold-duration-for-an-inactive-mailbox.md)

  > [!NOTE]
  > Vous ne pouvez pas appliquer d’autres stratégies de rétention à une boîte aux lettres inactive. Vous pouvez uniquement modifier la durée de rétention d’une stratégie de rétention existante appliquée à la boîte aux lettres inactive.

- **Récupérer une boîte aux lettres inactive.** Si un ancien employé (ou un employé en congé) revient dans votre organisation, ou si un nouvel employé est embauché pour assumer les responsabilités de l’ancien employé, vous pouvez récupérer le contenu de la boîte aux lettres inactive. Lorsque vous récupérez une boîte aux lettres inactive, la boîte aux lettres est convertie en nouvelle boîte aux lettres, le contenu et la structure de dossiers de la boîte aux lettres inactive sont conservés et la boîte aux lettres est liée à un nouveau compte d’utilisateur. Une fois récupérée, la boîte aux lettres inactive n'existe plus. Pour obtenir des procédures pas à pas et des informations sur ce qui se produit lorsque vous récupérez une boîte aux lettres inactive, voir [Récupérer une boîte aux lettres inactive.](recover-an-inactive-mailbox.md)

  > [!NOTE]
  > Si vous récupérez une boîte aux lettres inactive affectée à une stratégie de rétention avec verrouillage de conservation (appelée stratégie de rétention verrouillée), la boîte aux lettres récupérée est affectée à la même stratégie de rétention verrouillée. Si vous récupérez une boîte aux lettres inactive affectée à une stratégie de rétention sans verrouillage de conservation, la boîte aux lettres récupérée est supprimée de la stratégie de rétention déverrouillée. Toutefois, la conservation pour litige est activée sur la boîte aux lettres récupérée pour empêcher la suppression de contenu de boîte aux lettres en fonction des stratégies de rétention à l’échelle de l’organisation qui suppriment du contenu plus ancien qu’un âge spécifique.

- **Restituer une boîte aux lettres inactive.** Si un autre employé assume les responsabilités de l'ancien employé, ou si un autre utilisateur doit accéder au contenu de la boîte aux lettres inactive, vous pouvez restaurer (ou fusionner) le contenu de la boîte aux lettres inactive vers une boîte aux lettres existante. Lorsque vous restaurez une boîte aux lettres inactive, le contenu est copié vers une autre boîte aux lettres. La boîte aux lettres inactive est conservée et reste une boîte aux lettres inactive. La boîte aux lettres inactive peut toujours faire l’être à l’aide des outils eDiscovery, son contenu peut être restauré dans une autre boîte aux lettres et il peut être récupéré ou supprimé ultérieurement. Pour obtenir des procédures pas à pas, voir [Restaurer une boîte aux lettres inactive.](restore-an-inactive-mailbox.md)

- **Supprimez une boîte aux lettres inactive.** Lorsque vous n’avez plus besoin de conserver le contenu d’une boîte aux lettres inactive, vous pouvez le supprimer définitivement en supprimant toutes les conservations ou stratégies de rétention Microsoft 365 appliquées à la boîte aux lettres inactive. Si une boîte aux lettres est devenue inactive depuis plus de 30 jours, elle est marquée pour suppression définitive après la suppression de la conservation. Si la boîte aux lettres est devenue inactive au cours des 30 derniers jours, vous pouvez la restaurer après avoir supprimé la conservation ou la stratégie de rétention. Pour obtenir des procédures pas à pas, voir [Supprimer une boîte aux lettres inactive.](delete-an-inactive-mailbox.md)