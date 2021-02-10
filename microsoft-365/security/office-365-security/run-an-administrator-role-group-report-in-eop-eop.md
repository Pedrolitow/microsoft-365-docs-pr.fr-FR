---
title: Exécuter un rapport de groupe de rôles d’administrateur dans EOP autonome
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
ms.assetid: 23b47b57-0eec-46a3-a03b-366ea014ab31
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à exécuter un rapport de groupe de rôles d’administrateur dans Exchange Online Protection (EOP) autonome. Ce rapport enregistre lorsqu’un administrateur ajoute des membres à des groupes de rôles d’administrateur ou en supprime.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 507fbe6fb6c99677cf91b6eb824bf110f1c826f3
ms.sourcegitcommit: a1846b1ee2e4fa397e39c1271c997fc4cf6d5619
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50166626"
---
# <a name="run-an-administrator-role-group-report-in-standalone-eop"></a>Exécuter un rapport de groupe de rôles d’administrateur dans EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
-  [Exchange Online Protection autonome](https://go.microsoft.com/fwlink/?linkid=2148611)

Dans les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, lorsqu’un administrateur ajoute des membres à des groupes de rôles d’administration ou en supprime, le service enregistre chaque occurrence. Pour plus d’informations sur les groupes de rôles dans EOP autonome, voir [Autorisations dans EOP autonome.](feature-permissions-in-eop.md)

Lorsque vous exécutez un rapport de groupe de rôles d’administrateur dans le Centre d’administration Exchange (EAC), les entrées sont affichées en tant que résultats de recherche et incluent les groupes de rôles affectés, qui a modifié l’appartenance au groupe de rôles et quand et quelles mises à jour d’appartenance ont été réalisées. Utilisez ce rapport pour surveiller les modifications aux autorisations administratives attribuées aux utilisateurs dans votre organisation.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Centre d’administration Exchange, consultez le [Centre d’administration Exchange dans EOP autonome.](exchange-admin-center-in-exchange-online-protection-eop.md)

- Des autorisations doivent vous être attribuées dans Exchange Online Protection avant de pouvoir suivre les procédures de cet article. Plus précisément, vous avez besoin du rôle Journaux  d’audit ou Journaux d’audit en affichage seul, qui sont attribués par défaut aux groupes de **rôles** Gestion de l’organisation, Gestion de la conformité et Administrateur de la sécurité.   Pour plus d’informations, voir [Autorisations](feature-permissions-in-eop.md) dans EOP autonome et utiliser le CAE pour modifier la liste des membres des groupes [de rôles.](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups)

- Pour plus d’informations sur les raccourcis clavier qui peuvent s’appliquer aux procédures de cet article, voir raccourcis clavier pour le Centre d’administration [Exchange dans Exchange Online.](https://docs.microsoft.com/Exchange/accessibility/keyboard-shortcuts-in-admin-center)

> [!TIP]
> Vous rencontrez des difficultés ? Demandez de l’aide dans le Forum [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351) .

## <a name="use-the-eac-to-run-an-administrator-role-group-report"></a>Utiliser le Centre d'administration Exchange (CAE) pour exécuter un rapport de groupe de rôles d'administrateur

Exécutez le rapport de groupe de rôles d’administrateur pour rechercher les modifications apportées aux groupes de rôles de gestion dans un délai particulier.

1. Dans le EAC, sélectionnez **Audit** de la gestion de la conformité, puis exécutez un rapport de groupe de \>  **rôles d’administrateur.**

2. Dans la page **Rechercher les modifications apportées** aux groupes de rôles d’administrateur qui s’ouvre, configurez les paramètres suivants :

   - **Date de début** et **date de fin**: entrez une plage de dates. Par défaut, le rapport recherche toutes les modifications apportées aux groupes de rôles d'administrateur au cours des deux semaines passées.

   - **Sélectionner des groupes de rôles**: par défaut, tous les groupes de rôles sont recherchés. Pour filtrer les résultats par groupes de rôles spécifiques, cliquez **sur Sélectionner des groupes de rôles.** Dans la boîte de dialogue qui s’affiche, sélectionnez un groupe de rôles et cliquez **sur Ajouter ->**. Répétez cette étape autant de fois que nécessaire, puis cliquez sur **OK** lorsque vous avez terminé.

3. Lorsque vous avez terminé, cliquez sur **Rechercher.**

Si des modifications correspondent aux critères que vous avez spécifiés, elles seront affichées dans le volet des résultats. Cliquez sur un groupe de rôles dans les résultats de la recherche pour afficher les modifications dans le volet d'informations.

## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Si vous avez bien exécuté un rapport de groupe de rôles d'administrateur, les groupes de rôles qui ont été modifiés dans la plage de dates s'affichent dans le volet des résultats de la recherche. En cas d'absence de résultats, cela signifie qu'aucune modification aux groupes de rôles n'a eu lieu dans la plage de dates indiquée. Si vous pensez que des résultats devraient apparaître, modifiez la plage de dates et réexécutez le rapport.

## <a name="monitor-changes-to-role-group-membership"></a>Surveillances des modifications apportées à l'appartenance à des groupes de rôles

Lorsque des membres sont ajoutés ou supprimés dans groupe de rôles, les résultats de la recherche affichés dans le volet d'informations indiquent que l'appartenance à un groupe de rôles a été mise à jour et répertorient les membres actuels. Les résultats n'indiquent pas explicitement quel utilisateur a été ajouté ou supprimé.

Pour déterminer si un utilisateur a été ajouté ou supprimé, vous devez comparer deux entrées séparées dans le rapport. Par exemple, examinons les entrées de journal suivantes pour le groupe de rôles **Support technique**:

> 27/1/2018 16:43 <br> Administrateur <br> Membres mis à jour : Administrateur;annb,florencef;pilarp <br> 06/02/2018 10:09 <br> Administrateur <br> Membres mis à jour : Administrator;annb;florencef;pilarp;tonip <br> 19/2/2018 14:12 <br> Administrateur <br> Membres mis à jour : Administrator;annb;florencef;tonip

Dans cet exemple, le compte d'utilisateur Administrateur a apporté les modifications suivantes :

- Le 06/02/2018, l’utilisateur a ajouté le tonip.
- Le 19/02/2018, l’utilisateur pilarp a été supprimé.

## <a name="use-standalone-exchange-online-powershell-to-search-for-audit-log-entries"></a>Utiliser Exchange Online PowerShell autonome pour rechercher des entrées du journal d’audit

Vous pouvez utiliser Exchange Online PowerShell pour rechercher des entrées du journal d’audit qui répondent aux critères que vous spécifiez. Pour obtenir la liste des critères de recherche, voir Les critères de [recherche Search-AdminAuditLog.](https://docs.microsoft.com/Exchange/policy-and-compliance/admin-audit-logging/admin-audit-logging#search-adminauditlog-cmdlet) Cette procédure utilise la cmdlet **Search-AdminAuditLog** et affiche les résultats de recherche dans Exchange Online PowerShell. Vous pouvez utiliser cette cmdlet si vous devez renvoyer un ensemble de résultats au-delà des limites définies dans la cmdlet **New-AdminAuditLogSearch** ou dans les rapports d'audit du Centre d'administration Exchange.

Pour effectuer une recherche dans le journal d'audit d'après les critères que vous avez définis, utilisez la syntaxe suivante.

```PowerShell
Search-AdminAuditLog - Cmdlets <cmdlet 1, cmdlet 2, ...> -Parameters <parameter 1, parameter 2, ...> -StartDate <start date> -EndDate <end date> -UserIds <user IDs> -ObjectIds <object IDs> -IsSuccess <$True | $False >
```

> [!NOTE]
> Par défaut, la cmdlet **Search-AdminAuditLog** renvoie un maximum de 1 000 entrées du journal. Utilisez le _paramètre ResultSize_ pour spécifier jusqu’à 250 000 entrées de journal. Vous pouvez également utiliser la valeur `Unlimited` pour renvoyer toutes les entrées.

Cet exemple effectue une recherche portant sur toutes les entrées du journal d'audit avec les critères suivants :

- **Date de** début : 04/08/2018
- **Date de** fin : 03/10/2018
- **ID utilisateur :** `davids` , `chrisd` , `kima`
- **Cmdlets**: **Set-Mailbox**
- **Paramètres**: _ProhibitSendQuota_, _ProhibitSendReceiveQuota_, _IssueWarningQuota_, _MaxSendSize_, _MaxReceiveSize_

```PowerShell
Search-AdminAuditLog -Cmdlets Set-Mailbox -Parameters ProhibitSendQuota,ProhibitSendReceiveQuota,IssueWarningQuota,MaxSendSize,MaxReceiveSize -StartDate 08/04/2018 -EndDate 10/03/2018 -UserIds davids,chrisd,kima
```

Cet exemple recherche les modifications apportées à une boîte aux lettres spécifique. Ceci est utile si vous effectuez des opérations de dépannage ou devez fournir des informations à des fins d'investigation. Les critères suivants sont définis :

- **Date de** début : 01/05/2018
- **Date de** fin : 03/10/2018
- **ID d’objet**: contoso.com/Users/DavidS

```PowerShell
Search-AdminAuditLog -StartDate 05/01/2018 -EndDate 10/03/2018 -ObjectID contoso.com/Users/DavidS
```

Si vos recherches renvoient de nombreuses entrées de journal, nous vous recommandons d’utiliser la procédure fournie dans **Exchange Online PowerShell** pour rechercher des entrées du journal d’audit et envoyer des résultats à un destinataire plus loin dans cet article. La procédure décrite dans cette section a pour objet d'envoyer aux destinataires que vous spécifiez un fichier XML sous forme de pièce jointe à un message électronique, ce qui vous permet d'extraire plus aisément les données qui vous intéressent.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Search-AdminAuditLog](https://docs.microsoft.com/powershell/module/exchange/search-adminauditlog).

### <a name="view-details-of-audit-log-entries"></a>Afficher le détail des entrées du journal d’audit

La cmdlet **Search-AdminAuditLog renvoie** les champs décrits dans le contenu [du journal d’audit.](https://docs.microsoft.com/Exchange/policy-and-compliance/admin-audit-logging/admin-audit-logging#audit-log-contents) Parmi les champs renvoyés par la cmdlet, deux champs ( **CmdletParameters** et **ModifiedProperties** ) comportent des données supplémentaires qu'il est impossible de visualiser par défaut.

Pour afficher le contenu des champs **CmdletParameters** et **ModifiedProperties**, suivez la procédure ci-après. Vous pouvez également utiliser la procédure de l’utilisation **d’Exchange Online PowerShell** pour rechercher des entrées du journal d’audit et envoyer des résultats à un destinataire plus loin dans cet article pour créer un fichier XML.

Cette procédure exploite les concepts suivants :

- [about_Arrays](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays)

- [about_Variables](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables)

1. Déterminez les critères sur lesquels doivent porter vos recherches, exécutez la cmdlet **Search-AdminAuditLog** et stockez les résultats dans une variable au moyen de la commande suivante.

   ```PowerShell
   $Results = Search-AdminAuditLog <search criteria>
   ```

2. Chaque entrée du journal d’audit est stockée en tant qu’élément de tableau dans la `$Results` variable. Vous pouvez sélectionner un élément de tableau en précisant son index. Les index des éléments de tableau commencent à zéro (0) pour le premier élément du tableau. Par exemple, pour extraire le cinquième élément de tableau dont l'index est 4, utilisez la commande suivante.

   ```PowerShell
   $Results[4]
   ```

3. La commande précédente renvoie l'entrée du journal stockée dans l'élément de tableau 4. Pour afficher le contenu des champs **CmdletParameters** et **ModifiedProperties** pour cette entrée du journal, utilisez les commandes suivantes.

   ```PowerShell
   $Results[4].CmdletParameters
   $Results[4].ModifiedProperties
   ```

4. Pour afficher le contenu des champs **CmdletParameters** ou **ModifiedParameters** dans une autre entrée du journal, modifiez l'index de l'élément de tableau.
