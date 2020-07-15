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
description: Découvrez comment conserver le contenu des boîtes aux lettres des anciens employés en transformant la boîte aux lettres en boîte aux lettres inactive.
ms.openlocfilehash: baa2daebe65142743df95762a3dcd780d5069c7f
ms.sourcegitcommit: e8b9a4f18330bc09f665aa941f1286436057eb28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "45126745"
---
# <a name="overview-of-inactive-mailboxes"></a>Vue d’ensemble des boîtes aux lettres inactives

Votre organisation peut avoir besoin de conserver le courrier électronique des anciens employés après leur départ. En fonction des exigences de rétention de votre organisation, il se peut que vous deviez conserver le contenu de la boîte aux lettres pendant quelques mois ou quelques années après la fin du contrat, ou indéfiniment. Quelle que soit la durée de conservation du courrier électronique, vous pouvez créer des boîtes aux lettres inactives pour conserver la boîte aux lettres des anciens employés. 
  
## <a name="what-are-inactive-mailboxes"></a>Que sont les boîtes aux lettres inactives ?

Lorsqu’un employé quitte votre organisation (ou passe à un congé prolongé), vous pouvez supprimer son compte Microsoft 365. Les données de boîte aux lettres de l’employé sont conservées pendant 30 jours après la suppression du compte. Pendant cette période, vous pouvez toujours récupérer les données de boîte aux lettres en désupprimant le compte. Après 30 jours, les données sont définitivement supprimées.
  
Toutefois, si votre organisation doit conserver le contenu des boîtes aux lettres des anciens employés, vous pouvez transformer la boîte aux lettres en boîte aux lettres inactive en plaçant la boîte aux lettres en conservation pour litige ou en appliquant une stratégie de rétention Microsoft 365 à la boîte aux lettres dans le centre de sécurité & en conformité, puis en supprimant le compte Microsoft 365 correspondant. Le contenu d’une boîte aux lettres inactive est conservé pendant la durée de la suspension pour litige placée sur la boîte aux lettres ou la période de rétention de la stratégie de rétention appliquée avant la suppression de la boîte aux lettres. You can still recover the corresponding user account for a 30-day period. Toutefois, après 30 jours, la boîte aux lettres inactive est conservée dans Microsoft 365 jusqu’à ce que la stratégie de conservation ou de rétention soit supprimée. 
  
> [!IMPORTANT]
> À mesure que nous continuons à investir de différentes manières pour conserver le contenu de la boîte aux lettres, nous annonçaons le retrait des conservations inaltérables dans le centre d’administration Exchange. Cela signifie que vous devez utiliser des conservations pour litige et des stratégies de rétention Microsoft 365 pour créer une boîte aux lettres inactive. À partir du 1er juillet 2020 vous ne pourrez pas créer de nouvelles conservations inaltérables dans Exchange Online. Toutefois, vous pourrez toujours modifier la durée de conservation d’un blocage sur place placé sur une boîte aux lettres inactive. Toutefois, à partir du 1er octobre 2020, vous ne pourrez pas modifier la durée de la conservation. Vous ne pourrez supprimer une boîte aux lettres inactive qu’en supprimant la conservation inaltérable. Les boîtes aux lettres inactives existantes qui sont en conservation inaltérable resteront conservées jusqu’à ce que la conservation soit supprimée. Pour plus d’informations sur les conservations inaltérables, consultez la rubrique [déclassement des outils eDiscovery hérités](legacy-ediscovery-retirement.md).
  
## <a name="inactive-mailboxes-and-microsoft-365-retention-policies"></a>Boîtes aux lettres inactives et stratégies de rétention 365 Microsoft

En plus de la conservation pour litige, l’utilisation de la nouvelle fonctionnalité de stratégie de rétention de Microsoft 365 dans le centre de sécurité & conformité est une autre façon de désactiver une boîte aux lettres. To use a retention policy to make an inactive mailbox: 
  
- Elle doit être configurée pour conserver le contenu ou conserver, puis supprimer le contenu. Si une stratégie de rétention est configurée pour supprimer uniquement le contenu, une boîte aux lettres à laquelle la stratégie est appliquée ne devient pas inactive lorsque la boîte aux lettres est supprimée.

- La stratégie doit être appliquée aux boîtes aux lettres Exchange ou aux emplacements Skype Entreprise (car le contenu associé à Skype est stocké dans la boîte aux lettres de l'utilisateur).
  
- Elle peut reposer sur une requête pour conserver uniquement les éléments correspondant à une requête de recherche.

Pour plus d’informations sur les stratégies de rétention, voir [en savoir plus sur les stratégies de rétention et les étiquettes de conservation](retention.md).
  
Si vous utilisez une stratégie de rétention pour créer une boîte aux lettres inactive, Microsoft 365 continue de traiter la stratégie de rétention sur la boîte aux lettres inactive. En d'autres termes, si la stratégie de rétention est configurée pour conserver puis supprimer le contenu, les éléments sont déplacés vers le dossier Éléments récupérables à l'expiration de la durée de conservation avant d'être supprimés de la boîte aux lettres inactive. Si la stratégie de rétention n’est pas configurée sur les éléments supprimés, les éléments qui n’ont pas été définitivement supprimés par l’utilisateur (avant la boîte aux lettres inactives) ne seront pas déplacés vers le dossier éléments récupérables et seront conservés indéfiniment après l’inactivité de la boîte aux lettres. 
  
Vous pouvez envisager de créer une stratégie de rétention Microsoft 365 spécifiquement pour les boîtes aux lettres inactives. Voici quelques bonnes raisons pour le faire et quelques éléments à garder à l'esprit.
  
- Vous pouvez configurer la stratégie de rétention pour conserver le contenu de la boîte aux lettres uniquement le temps de répondre aux exigences de votre organisation concernant les anciens employés.

- Il s’agit d’un moyen efficace pour identifier les boîtes aux lettres inactives, car la stratégie de rétention ne sera appliquée qu’aux boîtes aux lettres inactives.

- Vous pouvez rapidement identifier la stratégie de rétention affectée aux boîtes aux lettres inactives dans votre organisation. Cela permet de modifier plus facilement les paramètres de rétention (ou de suppression), le cas échéant. Il facilite également la suppression définitive d’une boîte aux lettres inactive car vous pouvez la supprimer de la stratégie à l’aide du centre de sécurité & conformité. Dans le cas contraire, vous devez utiliser Exchange Online PowerShell pour supprimer une suspension pour litige d’une boîte aux lettres inactive ou utiliser la sécurité & le centre de conformité PowerShell pour exclure une boîte aux lettres inactive d’une stratégie de rétention Microsoft 365 à l’échelle de l’organisation.
    
- Si vous créez une stratégie de rétention Microsoft 365 spécifiquement pour les boîtes aux lettres inactives, vous pouvez ajouter un maximum de 1 000 boîtes aux lettres à la stratégie. Si vous êtes une grande organisation, il se peut que vous deviez créer plusieurs stratégies de rétention Microsoft 365 à utiliser pour les boîtes aux lettres inactives.

> [!CAUTION]
> Si vous utilisez une stratégie de rétention pour désactiver une boîte aux lettres, ne modifiez pas ou ne supprimez pas le nom d’utilisateur principal (UPN) de la boîte aux lettres avant de supprimer le compte d’utilisateur correspondant. En outre, ne modifiez pas l’adresse SMTP principale (qui est dérivée de l’UPN) ou supprimez cette adresse de messagerie de la liste des adresses SMTP secondaires associées à la boîte aux lettres avant de rendre la boîte aux lettres inactive. Si vous modifiez le nom d’utilisateur principal ou les adresses de messagerie (qui ont été affectées à la boîte aux lettres lors de l’application de la stratégie de rétention), puis supprimez le compte d’utilisateur pour désactiver la boîte aux lettres, vous ne pouvez pas supprimer la boîte aux lettres inactive lorsque vous n’avez plus besoin de la conserver. Cela est dû au fait que vous ne pouvez pas supprimer la boîte aux lettres inactive de la stratégie de rétention à l’aide d’un UPN ou d’une adresse de messagerie (pour identifier la boîte aux lettres inactive) qui est différent de ceux qui existaient lors de l’application initiale de la stratégie de rétention à la boîte aux lettres. Pour plus d’informations sur la suppression des boîtes aux lettres inactives, consultez la rubrique [Suppression d’une boîte aux lettres inactive dans Office 365](delete-an-inactive-mailbox.md).
  
## <a name="inactive-mailboxes-and-ediscovery-case-holds"></a>Boîtes aux lettres inactives et conservations eDiscovery

Si un blocage associé à un cas eDiscovery dans le centre de sécurité & conformité est placé dans une boîte aux lettres et que la boîte aux lettres ou le compte de l’utilisateur est supprimé, la boîte aux lettres devient une boîte aux lettres inactive. However, we don't recommend using eDiscovery case holds to make a mailbox inactive. That's because eDiscovery cases are intended for specific, time-bound cases related to a legal issue. At some point, a legal case will probably end and the holds associated with the case will be removed and the eDiscovery case will be closed. In fact, if a hold that's placed on an inactive mailbox is associated with an eDiscovery case, and then the hold is released or the eDiscovery case is closed (or deleted), the inactive mailbox will be permanently deleted. En outre, vous ne pouvez pas créer de conservation eDiscovery basée sur l’heure. Cela signifie que le contenu d’une boîte aux lettres inactive est conservé indéfiniment ou jusqu’à ce que la conservation soit supprimée et que la boîte aux lettres inactive soit supprimée. Par conséquent, nous vous recommandons d’utiliser une conservation pour litige ou une stratégie de rétention pour les boîtes aux lettres inactives.
  
Pour plus d’informations sur les cas de découverte électronique et les conservations, consultez la rubrique [cas eDiscovery](ediscovery-cases.md).

## <a name="inactive-mailboxes-and-labels"></a>Boîtes aux lettres et étiquettes inactives

Les étiquettes de rétention vous permettent de classer les données de messagerie de votre organisation à des fins de gouvernance et d’appliquer des règles de rétention basées sur cette classification. Une étiquette de rétention peut être appliquée à un élément de courrier manuellement par les utilisateurs ou automatiquement par les administrateurs, et un élément de courrier électronique ne peut avoir qu’une seule étiquette affectée. Si une étiquette est attribuée à un seul élément de messagerie dans la boîte aux lettres d’un utilisateur (et qu’elle est configurée pour conserver ou conserver, puis supprimer l’élément) et que la boîte aux lettres ou le compte de l’utilisateur est supprimé, la boîte aux lettres devient une boîte aux lettres inactive. De la même manière que pour les conservations de cas eDiscovery, il n’est pas recommandé d’utiliser des étiquettes de rétention pour désactiver une boîte aux lettres. Au lieu de cela, nous vous recommandons d’utiliser une conservation pour litige ou une stratégie de rétention. Dans le cas d’étiquettes de rétention, il se peut que vous ne réalisiez pas qu’une étiquette de rétention a été appliquée à un élément de courrier électronique, puis qu’une boîte aux lettres inactive est exécutée par inadvertance lorsque vous supprimez le compte de l’utilisateur. 
  
Pour plus d’informations sur les stratégies de rétention et les étiquettes de rétention, voir [Découvrez les stratégies de rétention et les étiquettes de rétention dans Office 365](retention.md)
  
## <a name="inactive-mailboxes-and-auto-expanding-archives"></a>Boîtes aux lettres inactives et Archives à extension automatique

Une boîte aux lettres inactive configurée avec une archive à extension automatique ne peut pas être récupérée ou restaurée. Dans les situations où il est nécessaire de récupérer des données à partir d’une boîte aux lettres inactive avec une archive à extension automatique, nous vous recommandons d’utiliser l’outil de recherche de contenu pour exporter les données de la boîte aux lettres, puis les importer vers une autre boîte aux lettres. Pour obtenir des instructions pas à pas sur la recherche d’une boîte aux lettres inactive et sur l’exportation des résultats de la recherche, voir :

- [Recherche de contenu dans Office 365](https://docs.microsoft.com/microsoft-365/compliance/content-search)

- [Exporter les résultats de la recherche de contenu](https://docs.microsoft.com/microsoft-365/compliance/export-search-results)

## <a name="inactive-mailboxes-and-exchange-mrm-retention-policies"></a>Boîtes aux lettres inactives et stratégies de rétention Exchange MRM

Si une stratégie de rétention Exchange (la fonctionnalité de gestion des enregistrements de messagerie ou MRM, dans Exchange Online) a été appliquée à la boîte aux lettres lorsqu’elle était devenue inactive, les stratégies de suppression (qui sont des balises de rétention configurées avec une action de rétention de **suppression** ) continueront à être traitées sur la boîte aux lettres inactive. En d'autres termes, les éléments marqués avec une stratégie de suppression seront déplacés vers le dossier Éléments récupérables à l'expiration de la période de rétention. Ces éléments sont supprimés définitivement de la boîte aux lettres inactive à l'expiration de la durée de la conservation. Si aucune durée de conservation n'est spécifiée pour la boîte aux lettres inactive, les éléments du dossier Éléments récupérables seront conservés indéfiniment. 
  
À l'inverse, les stratégies d'archivage (qui sont des balises de rétention configurées avec une action de rétention **MoveToArchive** ) incluses dans la stratégie de rétention attribuée à une boîte aux lettres inactive sont ignorées. Cela signifie que les éléments dans une boîte aux lettres inactive qui sont marqués avec une stratégie d'archivage restent dans la boîte aux lettres principale à l'expiration de la période de rétention. Ils ne sont pas déplacés vers la boîte aux lettres d'archivage ni vers le dossier Éléments récupérables dans la boîte aux lettres d'archivage. Ils seront conservés indéfiniment. 
  
## <a name="creating-an-inactive-mailbox"></a>Création d’une boîte aux lettres inactive

Pour désactiver une boîte aux lettres, vous devez lui avoir affecté une licence Exchange Online plan 2 (ou une licence Exchange Online plan 1 avec une licence de module complémentaire d’archivage Exchange Online) de sorte qu’une conservation pour litige ou une stratégie de rétention Microsoft 365 puisse être appliquée à la boîte aux lettres avant d’être supprimée. Une fois la boîte aux lettres supprimée, toutes les licences Exchange Online associées seront disponibles pour les affecter à un nouvel utilisateur.
  
Le tableau suivant résume le processus de création d'une boîte aux lettres inactive pour différents scénarios de rétention. Pour plus d’informations, consultez la rubrique [gestion des boîtes aux lettres inactives](create-and-manage-inactive-mailboxes.md).
  
|**Pour...**|**Vous devez…**|**Résultat**|
|:-----|:-----|:-----|
|Conserver le contenu de la boîte aux lettres indéfiniment après le départ d'un employé de l'organisation  <br/> | Placez la boîte aux lettres en conservation pour litige ou appliquez une stratégie de rétention Microsoft 365 (configurée pour conserver le contenu) dans la boîte aux lettres.  <br/>  Ne spécifiez pas de durée de conservation pour litige ou ne configurez pas la stratégie de rétention pour supprimer des éléments. Vous pouvez également utiliser une stratégie de rétention qui conserve les éléments de façon infinie.  <br/>  Supprimez le compte Microsoft 365 de l’utilisateur.  <br/> |Tout le contenu de la boîte aux lettres inactive, y compris les éléments du dossier éléments récupérables, est conservé indéfiniment.  <br/> |
|Conserver le contenu de la boîte aux lettres pendant une période donnée après le départ d'un employé de l'organisation et le supprimer  <br/> | Appliquer une stratégie de rétention Microsoft 365 à la boîte aux lettres.  <br/>  Configurez la stratégie de rétention pour conserver, puis supprimer les éléments à l’expiration de la période de rétention.  <br/>  Supprimez le compte Microsoft 365 de l’utilisateur.  <br/> |Lorsque la période de rétention d’un élément de boîte aux lettres expire, l’élément est déplacé vers le dossier éléments récupérables, puis supprimé définitivement (purgé) de la boîte aux lettres inactive lors de l’expiration de la période de rétention des éléments supprimés (pour les boîtes aux lettres Exchange). La période de rétention de la stratégie de rétention Microsoft 365 peut être configurée en fonction de la date d’origine à laquelle un élément de boîte aux lettres a été reçu ou créé, ou lors de sa dernière modification.  <br/> |
   
**Remarque :** Si une mise en attente pour litige est déjà placée sur une boîte aux lettres ou si une stratégie de rétention Microsoft 365 (configurée pour conserver ou conserver et supprimer du contenu) est déjà appliquée à la boîte aux lettres, il vous suffit de supprimer le compte d’utilisateur correspondant pour créer une boîte aux lettres inactive. 
  
## <a name="managing-inactive-mailboxes"></a>Gestion des boîtes aux lettres inactives

Une fois que la boîte aux lettres est inactive, vous pouvez effectuer différentes tâches de gestion.
  
- **Modifier la durée de la conservation pour une boîte aux lettres inactive.** Une fois qu’une boîte aux lettres est devenue inactive, vous pouvez modifier la durée de la conservation pour litige ou la stratégie de rétention Microsoft 365 appliquée à la boîte aux lettres inactive. Pour obtenir des procédures pas à pas, consultez [la rubrique modifier la durée de la conservation pour une boîte aux lettres inactive](change-the-hold-duration-for-an-inactive-mailbox.md).

  > [!NOTE]
  > Vous ne pouvez pas appliquer d’autres stratégies de rétention à une boîte aux lettres inactive. Vous pouvez uniquement modifier la durée de rétention d’une stratégie de rétention existante appliquée à la boîte aux lettres inactive.
    
- **Récupérer une boîte aux lettres inactive.** Si un ancien employé (ou un employé en congé) revient à votre organisation ou si un nouvel employé est embauché pour prendre les responsabilités de l’ancien employé, vous pouvez récupérer le contenu de la boîte aux lettres inactive. Lorsque vous récupérez une boîte aux lettres inactive, la boîte aux lettres est convertie en une nouvelle boîte aux lettres, le contenu et la structure de dossiers de la boîte aux lettres inactive sont conservés, et la boîte aux lettres est liée à un nouveau compte d’utilisateur. Une fois récupérée, la boîte aux lettres inactive n'existe plus. Pour obtenir des procédures pas à pas et des informations sur ce qui se produit lorsque vous récupérez une boîte aux lettres inactive, consultez la rubrique [récupérer une boîte aux lettres inactive](recover-an-inactive-mailbox.md).

  > [!NOTE]
  > Si vous récupérez une boîte aux lettres inactive affectée à une stratégie de rétention avec un verrou de conservation (appelé *stratégie de rétention verrouillée*), la boîte aux lettres Récupérée est affectée à la même stratégie de rétention verrouillée. Si vous récupérez une boîte aux lettres inactive affectée à une stratégie de rétention sans verrouillage de conservation, la boîte aux lettres Récupérée est supprimée de la stratégie de rétention déverrouillée. Toutefois, la conservation pour litige est activée sur la boîte aux lettres Récupérée afin d’empêcher la suppression du contenu d’une boîte aux lettres basée sur des stratégies de rétention à l’échelle de l’organisation qui suppriment le contenu antérieur à un âge donné.

- **Restaurez une boîte aux lettres inactive.** Si un autre employé assume les responsabilités de l'ancien employé, ou si un autre utilisateur doit accéder au contenu de la boîte aux lettres inactive, vous pouvez restaurer (ou fusionner) le contenu de la boîte aux lettres inactive vers une boîte aux lettres existante. Lorsque vous restaurez une boîte aux lettres inactive, le contenu est copié vers une autre boîte aux lettres. La boîte aux lettres inactive est conservée et reste une boîte aux lettres inactive. La boîte aux lettres inactive peut toujours faire l’objet d’une recherche à l’aide des outils eDiscovery, son contenu peut être restauré vers une autre boîte aux lettres, et il peut être récupéré ou supprimé ultérieurement. Pour obtenir des procédures pas à pas, consultez la rubrique [restaurer une boîte aux lettres inactive](restore-an-inactive-mailbox.md).
    
- **Supprimez une boîte aux lettres inactive.** Lorsque vous n’avez plus besoin de conserver le contenu d’une boîte aux lettres inactive, vous pouvez le supprimer définitivement en supprimant toutes les suspensions ou les stratégies de rétention de Microsoft 365 appliquées à la boîte aux lettres inactive. Si une boîte aux lettres est devenue inactive depuis plus de 30 jours, elle est marquée pour suppression définitive après la suppression de la conservation. Si la boîte aux lettres est devenue inactive au cours des 30 derniers jours, vous pouvez la restaurer après avoir supprimé la conservation ou la stratégie de rétention. Pour obtenir des procédures pas à pas, consultez la rubrique [supprimer une boîte aux lettres inactive](delete-an-inactive-mailbox.md).
