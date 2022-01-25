---
title: En savoir plus sur les boîtes aux lettres inactives
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
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
ms.openlocfilehash: 5aa20b780ed49edcbd46770c9f7f470bf9bb0db1
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2022
ms.locfileid: "62202136"
---
# <a name="learn-about-inactive-mailboxes"></a>En savoir plus sur les boîtes aux lettres inactives

Votre organisation peut avoir besoin de conserver le courrier électronique des anciens employés après leur départ. En fonction des exigences de rétention de votre organisation, il se peut que vous deviez conserver le contenu de la boîte aux lettres pendant quelques mois ou quelques années après la fin du contrat, ou indéfiniment. Quel que soit le temps nécessaire pour conserver les messages électroniques, vous pouvez créer des boîtes aux lettres inactives pour conserver la boîte aux lettres des anciens employés.

## <a name="what-are-inactive-mailboxes"></a>Que sont les boîtes aux lettres inactives ?

Lorsqu’un employé quitte votre organisation (ou part en congé prolongé), vous pouvez supprimer Microsoft 365 compte. Les données de boîte aux lettres de l’employé sont conservées pendant 30 jours après la suppression du compte. Pendant cette période, vous pouvez toujours récupérer les données de boîte aux lettres en supprimant le compte. Après 30 jours, les données sont définitivement supprimées.

Toutefois, si une attente est appliquée à la boîte aux lettres avant la suppression du compte Microsoft 365, la boîte aux lettres est convertie en boîte aux lettres inactive. Les sections suivantes contiennent des informations sur les conservations qui peuvent être appliquées avec Microsoft 365 rétention et les conservations eDiscovery.

Les boîtes aux lettres inactives sont utiles lorsque votre organisation doit conserver le contenu des boîtes aux lettres des anciens employés pour des raisons réglementaires ou autres. Bien que tout type de conservation répertorié dans ce document force l’inactivité d’une boîte aux lettres lorsqu’un objet utilisateur est supprimé, nous vous recommandons d’appliquer une stratégie ou des étiquettes de rétention [Microsoft 365,](#confirming-a-hold-is-applied-to-a-mailbox)de confirmer que la conservation est appliquée, puis de supprimer le compte Microsoft 365 correspondant. À ce stade, le contenu de la boîte aux lettres inactive est conservé pendant la période de rétention spécifiée avant la suppression du compte d’utilisateur. Vous pouvez toujours récupérer le compte d’utilisateur correspondant pendant une période de 30 jours, mais après 30 jours, la boîte aux lettres est conservée dans Microsoft 365 en tant que boîte aux lettres inactive jusqu’à ce que la stratégie de rétention ou les étiquettes de rétention soient supprimées.

> [!IMPORTANT]
> Comme nous l’avons mentionné précédemment, nous vous recommandons d’utiliser Microsoft 365 rétention pour créer une boîte aux lettres inactive :
> - In-Place les Exchange du centre d’administration sont désormais retirés. Depuis le 1er juillet 2020, les nouvelles In-Place de la Exchange Online. À compter du 1er octobre 2020, la durée de la durée des attentes in place n’a plus pu être modifiée. Toute boîte aux lettres inactive dont la In-Place est appliquée ne peut être supprimée qu’en supprimant la In-Place de la boîte aux lettres. Les boîtes aux lettres inactives existantes qui sont In-Place conservation continueront d’être conservées jusqu’à ce que la conservation soit supprimée. Pour plus d’informations sur In-Place retrait de la découverte électronique héritée, voir Retrait des [outils eDiscovery hérités.](legacy-ediscovery-retirement.md)
> 
> - [La rétention pour](create-a-litigation-hold.md) litige reste prise en charge en tant que méthode alternative pour conserver le contenu d’une boîte aux lettres et le rendre inactif après la suppression d’un compte d’utilisateur. Toutefois, en tant qu’ancienne technologie, nous vous recommandons d’utiliser Microsoft 365 rétention à la place.

Lorsqu’il existe plusieurs conservations [](retention.md#the-principles-of-retention-or-what-takes-precedence) sur le même contenu, le principe de rétention s’applique et le contenu est conservé pendant la période la plus longue.

### <a name="confirming-a-hold-is-applied-to-a-mailbox"></a>Confirmation de l’application d’une attente à une boîte aux lettres

Que vous appliquiez une stratégie de rétention Microsoft 365, des étiquettes de rétention, une conservation eDiscovery, une conservation pour litige ou une conservation In-Place existante, vous pouvez confirmer que la conservation est correctement appliquée à la boîte aux lettres à l’aide de PowerShell. Si vous avez récemment configuré la boîte aux lettres, vous devrez peut-être patienter jusqu’à ce qu’elle soit appliquée à la boîte aux lettres.

Pour éviter toute suppression accidentelle ou involontaire, nous vous recommandons de confirmer la conserver avant de supprimer le compte d’utilisateur. Si la boîte aux lettres n’est pas appliquée, la boîte aux lettres ne sera pas convertie en boîte aux lettres inactive.

Pour obtenir des instructions, voir Comment identifier le type de mise en attente placée sur [une boîte aux lettres Exchange Online de données.](identify-a-hold-on-an-exchange-online-mailbox.md)

## <a name="inactive-mailboxes-and-microsoft-365-retention"></a>Boîtes aux lettres inactives et rétention Microsoft 365 rétention

Si une stratégie de rétention Microsoft 365 est appliquée à une boîte aux lettres, ou si une étiquette de rétention est appliquée à un ou plusieurs éléments de messagerie d’une boîte aux lettres, puis que le compte d’utilisateur Microsoft 365 est supprimé, la boîte aux lettres est convertie en boîte aux lettres inactive. Pour la boîte aux lettres inactive à créer :

- Les paramètres de rétention doivent être configurés pour conserver [le contenu, ou conserver, puis supprimer le contenu.](retention-settings.md#settings-for-retaining-and-deleting-content) Si l’action de rétention est configurée pour supprimer uniquement du contenu, la boîte aux lettres ne devient pas inactive lorsque le compte d’utilisateur est supprimé. Pour les boîtes aux lettres inactives, nous vous recommandons d’utiliser l’option conserver puis supprimer.

- Les paramètres de rétention doivent être appliqués à un emplacement [de](retention-settings.md#locations) rétention associé à une boîte aux Exchange de rétention :
    - La messagerie électronique Exchange
    - Groupes Microsoft 365
    - Skype Entreprise
    - Dossiers publics Exchange
    - Messages du canal Teams
    - Conversations Teams
    - Messages du canal privé Teams
    - Messages communautaires Yammer
    - Messages utilisateur de Yammer

Pour plus d’informations sur la rétention Microsoft, voir [En savoir plus sur les stratégies de rétention et les étiquettes de rétention.](retention.md)

Si Microsoft 365 rétention est utilisée pour créer une boîte aux lettres inactive, les paramètres de rétention de la stratégie de rétention ou des étiquettes de rétention continuent de s’appliquer à la boîte aux lettres inactive. Cela signifie que si les paramètres de rétention sont configurés pour conserver puis supprimer du contenu, les éléments sont déplacés vers le dossier Éléments récupérables à l’expiration de la durée de rétention, puis purgés de la boîte aux lettres inactive. Si les paramètres de rétention ne sont pas configurés pour les éléments supprimés, les éléments qui n’ont pas été supprimés définitivement par l’utilisateur (avant que la boîte aux lettres ne devienne inactive) ne sont pas déplacés vers le dossier Éléments récupérables et sont conservés indéfiniment une fois que la boîte aux lettres devient inactive.

> [!TIP]
> Vous pouvez utiliser la *propriété ComplianceTagHoldApplied* pour déterminer si une boîte aux lettres possède des éléments dont une ou plusieurs étiquettes de rétention sont appliquées pour conserver, ou conserver puis supprimer du contenu. Pour plus d’informations, voir Identification des boîtes aux lettres en attente, car une étiquette de rétention a été appliquée à un dossier [ou à un élément.](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item)

### <a name="using-adaptive-policy-scopes-to-manage-retention-of-inactive-mailboxes"></a>Utilisation d’étendues de stratégie adaptative pour gérer la rétention des boîtes aux lettres inactives

Avec [les étendues de stratégie adaptative,](retention.md#adaptive-or-static-policy-scopes-for-retention)vous pouvez appliquer des paramètres de rétention spécifiquement aux boîtes aux lettres inactives. Les avantages de cette configuration sont les suivants :

- Vous pouvez respecter les réglementations ou stratégies de votre organisation qui nécessitent des périodes de rétention différentes pour les employés actifs et les anciens employés.

- Vous pouvez configurer les paramètres de rétention pour conserver le contenu des boîtes aux lettres uniquement aussi longtemps que nécessaire pour répondre aux exigences de votre organisation pour les anciens employés.

- Vous pouvez rapidement identifier la stratégie de rétention attribuée aux boîtes aux lettres inactives de votre organisation, ce qui facilite la modification des paramètres de rétention si nécessaire. 

- Il est plus facile de supprimer définitivement une boîte aux [](retention-settings.md#to-configure-an-adaptive-scope) lettres inactive, car vous pouvez la supprimer de la stratégie en configurant l’étendue adaptative pour l’exclure, en fonction des attributs ou des propriétés de la boîte aux lettres inactive. Sinon, vous devez utiliser [Exchange Online PowerShell](delete-an-inactive-mailbox.md#remove-an-inactive-mailbox-from-a-retention-policy) avant [de supprimer la boîte aux lettres.](delete-an-inactive-mailbox.md#before-you-delete-an-inactive-mailbox)

> [!NOTE]
> Selon la configuration de votre étendue de stratégie adaptative, les boîtes aux lettres inactives peuvent être incluses ou non.  Pour cibler ou exclure spécifiquement des boîtes aux lettres inactives d’une étendue de stratégie adaptative, consultez les informations de configuration Exchange courrier électronique et [Exchange dossiers publics.](retention-settings.md#locations)

### <a name="using-static-policy-scopes-and-inactive-mailboxes"></a>Utilisation d’étendues de stratégie statiques et de boîtes aux lettres inactives

Si vous n’utilisez pas d’étendues de stratégie adaptative avec Microsoft 365 rétention, et utilisez plutôt une étendue [statique,](retention.md#adaptive-or-static-policy-scopes-for-retention)envisagez les choses suivantes : [](retention.md#adaptive-or-static-policy-scopes-for-retention)

- Les étendues de stratégie statique incluent les boîtes aux lettres inactives lorsque vous utilisez la configuration par défaut Tous les **destinataires,** mais ne sont pas pris en charge pour des [inclusions ou des exclusions spécifiques.](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) Toutefois, si vous incluez ou excluez un destinataire qui possède une boîte aux lettres active au moment où la stratégie est appliquée et que la boîte aux lettres devient inactive par la suite, les paramètres de rétention continuent d’être appliqués ou exclus. Dans ce scénario, des [limites spécifiques d’inclusion et d’exclusion](retention-limits.md) s’appliquent toujours.
    
    > [!NOTE]
    > Cela signifie également que les nouveaux paramètres de rétention Microsoft 365 à l’aide d’une étendue statique appliquée à la sélection par défaut de Tous les **destinataires** incluront automatiquement toutes les boîtes aux lettres inactives existantes.

- Si vous modifiez la sélection par défaut de Tous les **destinataires** pour inclure des destinataires spécifiques, les paramètres de rétention de la stratégie ne s’appliqueront plus aux boîtes aux lettres inactives, qui peuvent désormais être automatiquement supprimées.

- Si vous souhaitez libérer une stratégie de rétention qui est appliquée à une boîte aux lettres inactive, voir [Publication d’une](retention.md#releasing-a-policy-for-retention)stratégie pour la rétention.

> [!CAUTION]
> Lorsque vous utilisez la rétention Microsoft 365 pour rendre une boîte aux lettres inactive, ne modifiez pas ou ne supprimez pas le nom d’utilisateur principal (UPN) de la boîte aux lettres avant de supprimer le compte d’utilisateur correspondant. En outre, ne modifiez pas l’adresse SMTP principale (dérivée de l’UPN) ni ne supprimez cette adresse de messagerie de la liste des adresses SMTP secondaires associées à la boîte aux lettres avant de rendre la boîte aux lettres inactive.
> 
> Si vous modifiez l’UPN ou les adresses de messagerie (qui étaient affectées à la boîte aux lettres au moment où les paramètres de rétention ont été appliqués), puis supprimez le compte d’utilisateur pour rendre la boîte aux lettres inactive, vous ne pourrez pas supprimer la boîte aux lettres inactive si vous n’avez plus besoin de la conserver. Cela est dû au fait que vous ne pouvez pas supprimer la boîte aux lettres inactive de la stratégie à l’aide d’un UPN ou d’une adresse de messagerie (pour identifier la boîte aux lettres inactive) qui est différente de celle qui existait lorsque les paramètres de rétention ont été initialement appliqués à la boîte aux lettres. Pour plus d’informations sur la suppression de boîtes aux lettres inactives, voir Supprimer une boîte aux lettres [inactive dans Office 365](delete-an-inactive-mailbox.md).

## <a name="inactive-mailboxes-and-ediscovery-case-holds"></a>Boîtes aux lettres inactives et conservations eDiscovery

Si une mise en attente associée à un cas [eDiscovery](./get-started-core-ediscovery.md) dans Centre de conformité Microsoft 365 est placée sur une boîte aux lettres, puis que la boîte aux lettres ou le compte de l’utilisateur est supprimé, la boîte aux lettres devient inactive. However, we don't recommend using eDiscovery case holds to make a mailbox inactive. That's because eDiscovery cases are intended for specific, time-bound cases related to a legal issue. At some point, a legal case will probably end and the holds associated with the case will be removed and the eDiscovery case will be closed. In fact, if a hold that's placed on an inactive mailbox is associated with an eDiscovery case, and then the hold is released or the eDiscovery case is closed (or deleted), the inactive mailbox will be permanently deleted. En outre, vous ne pouvez pas créer une attente eDiscovery basée sur le temps. Cela signifie que le contenu d’une boîte aux lettres inactive est conservé définitivement ou jusqu’à ce que la boîte aux lettres inactive soit supprimée. Par conséquent, nous vous recommandons d’Microsoft 365 rétention pour les boîtes aux lettres inactives.

Pour plus d’informations sur les différences entre les conservations eDiscovery et la rétention Microsoft 365, voir Quand utiliser des stratégies de rétention et des étiquettes de rétention ou des conservations [eDiscovery](retention.md#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds).

## <a name="inactive-mailboxes-and-auto-expanding-archives"></a>Boîtes aux lettres inactives et archives à extension automatique

Une boîte aux lettres inactive configurée avec une archive à extension automatique ne peut pas être récupérée ou restaurée. Dans les situations où il est nécessaire de récupérer des données à partir d’une boîte aux lettres inactive avec une archive à extension automatique, nous vous recommandons d’utiliser l’outil de recherche de contenu pour exporter les données de la boîte aux lettres, puis les importer vers une autre boîte aux lettres. Pour obtenir des instructions détaillées sur la recherche dans une boîte aux lettres inactive et l’exportation des résultats de la recherche, voir :

- [Recherche de contenu](content-search.md)

- [Exporter les résultats de recherche de contenu](export-search-results.md)

## <a name="inactive-mailboxes-and-exchange-mrm-retention-policies"></a>Boîtes aux lettres inactives et stratégies de rétention Exchange MRM

L’application d’une stratégie de rétention Exchange (fonctionnalité de gestion des enregistrements de messagerie ou MRM dans Exchange Online) ne crée pas de boîte aux lettres inactive lorsque le compte d’utilisateur est supprimé.

Toutefois, si cette stratégie de rétention MRM **a** été appliquée à une boîte aux lettres avant qu’elle ne soit inactive, toutes les stratégies de suppression (balises de rétention MRM configurées avec une action de suppression) continueront d’être traitées sur la boîte aux lettres inactive. Cela signifie que les éléments marqués avec une stratégie de suppression MRM sont déplacés vers le dossier Éléments [récupérables](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) à l’expiration de la période de rétention. Ces éléments sont supprimés définitivement de la boîte aux lettres inactive à l'expiration de la durée de la conservation. Si aucune durée de conservation n'est spécifiée pour la boîte aux lettres inactive, les éléments du dossier Éléments récupérables seront conservés indéfiniment.

À l’inverse, toutes les stratégies d’archivage (balises de rétention MRM configurées avec une action **MoveToArchive)** incluses dans la stratégie de rétention MRM affectée à une boîte aux lettres inactive sont ignorées. Cela signifie que les éléments dans une boîte aux lettres inactive qui sont marqués avec une stratégie d'archivage restent dans la boîte aux lettres principale à l'expiration de la période de rétention. Ils ne sont pas déplacés vers la boîte aux lettres d'archivage ni vers le dossier Éléments récupérables dans la boîte aux lettres d'archivage. Ils seront conservés indéfiniment.

## <a name="next-steps"></a>Étapes suivantes

Pour rendre une boîte aux lettres inactive et la gérer, telle que la récupération, la restauration et la suppression, voir Créer et gérer des boîtes aux lettres [inactives.](create-and-manage-inactive-mailboxes.md)
