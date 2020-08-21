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
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 23b47b57-0eec-46a3-a03b-366ea014ab31
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à exécuter un rapport de groupe de rôles d’administrateur dans Exchange Online Protection (EOP). Ce rapport enregistre les journaux lorsqu’un administrateur ajoute ou supprime des membres de groupes de rôles d’administrateur, EOP journalise chaque occurrence.
ms.openlocfilehash: db1934c7865209d358d164ff5165bb23026589cc
ms.sourcegitcommit: e12fa502bc216f6083ef5666f693a04bb727d4df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "46827504"
---
# <a name="run-an-administrator-role-group-report-in-standalone-eop"></a>Exécuter un rapport de groupe de rôles d’administrateur dans EOP autonome

Dans les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, lorsqu’un administrateur ajoute ou supprime des membres de groupes de rôles d’administration, le service journalise chaque occurrence. Pour plus d’informations sur les groupes de rôles dans la version autonome d’EOP, consultez la rubrique [Permissions in standalone EOP](feature-permissions-in-eop.md).

Lorsque vous exécutez un rapport de groupe de rôles d’administrateur dans le centre d’administration Exchange, les entrées s’affichent sous la forme de résultats de recherche et incluent les groupes de rôles affectés, la personne qui a modifié l’appartenance au groupe de rôles et le moment, ainsi que les mises à jour d’appartenance. Utilisez ce rapport pour surveiller les modifications aux autorisations administratives attribuées aux utilisateurs dans votre organisation.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le centre d’administration Exchange, consultez la rubrique [Exchange Admin Center in standalone EOP](exchange-admin-center-in-exchange-online-protection-eop.md).

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. Plus précisément, vous avez besoin du rôle journaux d’audit ou journaux d’audit en affichage seul, qui sont attribués aux groupes de rôles ComplianceManagement, OrganizationManagement (administrateurs globaux) et SecurityAdministrator par défaut. Pour plus d’informations, consultez la rubrique [autorisations dans EOP autonome](feature-permissions-in-eop.md) et utiliser le centre d’administration Exchange pour [modifier la liste des membres dans les groupes de rôles](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups).

- Pour plus d’informations sur les raccourcis clavier applicables aux procédures de cette rubrique, voir [raccourcis clavier pour le centre d’administration Exchange dans Exchange Online](https://docs.microsoft.com/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Vous rencontrez des difficultés ? Demandez de l’aide dans le Forum [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351) .

## <a name="use-the-eac-to-run-an-administrator-role-group-report"></a>Utiliser le Centre d'administration Exchange (CAE) pour exécuter un rapport de groupe de rôles d'administrateur

Exécutez le rapport de groupe de rôles d’administrateur pour rechercher les modifications apportées aux groupes de rôles de gestion dans votre organisation dans un intervalle de temps donné.

1. Dans le centre d’administration Exchange, accédez à audit de **gestion de la conformité** \> **Auditing**, puis choisissez **exécuter un rapport de groupe de rôles d’administrateur**.

2. Dans la page **Rechercher les modifications apportées aux groupes de rôles d’administrateur** qui s’ouvre, configurez les paramètres suivants :

   - **Date de début** et **Date de fin**: entrez une plage de dates. Par défaut, le rapport recherche toutes les modifications apportées aux groupes de rôles d'administrateur au cours des deux semaines passées.

   - **Sélectionner des groupes de rôles**: par défaut, tous les groupes de rôles sont recherchés. Pour filtrer les résultats par groupes de rôles spécifiques, cliquez sur **Sélectionner des groupes de rôles**. Dans la boîte de dialogue qui s’affiche, sélectionnez un groupe de rôles, puis cliquez sur **Ajouter->**. Répétez cette étape autant de fois que nécessaire, puis cliquez sur **OK** lorsque vous avez terminé.

3. Lorsque vous avez terminé, cliquez sur **Rechercher**.

Si des modifications correspondent aux critères que vous avez spécifiés, elles seront affichées dans le volet des résultats. Cliquez sur un groupe de rôles dans les résultats de la recherche pour afficher les modifications dans le volet d'informations.

## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Si vous avez bien exécuté un rapport de groupe de rôles d'administrateur, les groupes de rôles qui ont été modifiés dans la plage de dates s'affichent dans le volet des résultats de la recherche. En cas d'absence de résultats, cela signifie qu'aucune modification aux groupes de rôles n'a eu lieu dans la plage de dates indiquée. Si vous pensez que des résultats devraient apparaître, modifiez la plage de dates et réexécutez le rapport.

## <a name="monitor-changes-to-role-group-membership"></a>Surveillances des modifications apportées à l'appartenance à des groupes de rôles

Lorsque des membres sont ajoutés ou supprimés dans groupe de rôles, les résultats de la recherche affichés dans le volet d'informations indiquent que l'appartenance à un groupe de rôles a été mise à jour et répertorient les membres actuels. Les résultats n'indiquent pas explicitement quel utilisateur a été ajouté ou supprimé.

Pour déterminer si un utilisateur a été ajouté ou supprimé, vous devez comparer deux entrées séparées dans le rapport. Par exemple, examinons les entrées de journal suivantes pour le groupe de rôles **Support technique**:

> 1/27/2018 4:43 PM <br> Administrateur <br> Membres mis à jour : Administrateur;annb,florencef;pilarp <br> 2/06/2018 10:09 AM <br> Administrateur <br> Membres mis à jour : Administrator;annb;florencef;pilarp;tonip <br> 2/19/2018 2:12 PM <br> Administrateur <br> Membres mis à jour : Administrator;annb;florencef;tonip

Dans cet exemple, le compte d'utilisateur Administrateur a apporté les modifications suivantes :

- Le 2/06/2018, il a ajouté l’utilisateur tonip.

- Le 2/19/2018, il a supprimé l’utilisateur pilarp.

## <a name="use-standalone-exchange-online-powershell-to-search-for-audit-log-entries"></a>Utiliser Exchange Online PowerShell autonome pour rechercher des entrées du journal d’audit

Vous pouvez utiliser Exchange Online PowerShell pour rechercher des entrées du journal d’audit qui correspondent aux critères que vous spécifiez. Pour obtenir la liste des critères de recherche, voir [Search-AdminAuditLog Search Criteria](https://docs.microsoft.com/Exchange/policy-and-compliance/admin-audit-logging/admin-audit-logging#search-adminauditlog-cmdlet). Cette procédure utilise la cmdlet **Search-AdminAuditLog** et affiche les résultats de la recherche dans Exchange Online PowerShell. Vous pouvez utiliser cette cmdlet si vous devez renvoyer un ensemble de résultats au-delà des limites définies dans la cmdlet **New-AdminAuditLogSearch** ou dans les rapports d'audit du Centre d'administration Exchange.

Pour effectuer une recherche dans le journal d'audit d'après les critères que vous avez définis, utilisez la syntaxe suivante.

```PowerShell
Search-AdminAuditLog - Cmdlets <cmdlet 1, cmdlet 2, ...> -Parameters <parameter 1, parameter 2, ...> -StartDate <start date> -EndDate <end date> -UserIds <user IDs> -ObjectIds <object IDs> -IsSuccess <$True | $False >
```

> [!NOTE]
> Par défaut, la cmdlet **Search-AdminAuditLog** renvoie un maximum de 1 000 entrées du journal. Utilisez le paramètre _result_ pour spécifier jusqu’à 250 000 entrées de journal. Vous pouvez utiliser la valeur `Unlimited` pour renvoyer toutes les entrées.

Cet exemple effectue une recherche portant sur toutes les entrées du journal d'audit avec les critères suivants :

- **Date de début**: 08/04/2018

- **Date de fin**: 10/03/2018

- **ID d’utilisateur**: Davids, chrisd, kima

- **Cmdlets**: **Set-Mailbox**

- **Paramètres**: _ProhibitSendQuota_, _ProhibitSendReceiveQuota_, _IssueWarningQuota_, _MaxSendSize_, _MaxReceiveSize_

```PowerShell
Search-AdminAuditLog -Cmdlets Set-Mailbox -Parameters ProhibitSendQuota,ProhibitSendReceiveQuota,IssueWarningQuota,MaxSendSize,MaxReceiveSize -StartDate 08/04/2018 -EndDate 10/03/2018 -UserIds davids,chrisd,kima
```

Cet exemple recherche les modifications apportées à une boîte aux lettres spécifique. Ceci est utile si vous effectuez des opérations de dépannage ou devez fournir des informations à des fins d'investigation. Les critères suivants sont définis :

- **Date de début**: 05/01/2018

- **Date de fin**: 10/03/2018

- **ID d’objet**: contoso.com/users/Davids

```PowerShell
Search-AdminAuditLog -StartDate 05/01/2018 -EndDate 10/03/2018 -ObjectID contoso.com/Users/DavidS
```

Si vos recherches renvoient de nombreuses entrées de journal, nous vous recommandons d’utiliser la procédure décrite dans la rubrique **utiliser Exchange Online PowerShell pour rechercher des entrées du journal d’audit et envoyer les résultats à un destinataire** plus loin dans cette rubrique. La procédure décrite dans cette section a pour objet d'envoyer aux destinataires que vous spécifiez un fichier XML sous forme de pièce jointe à un message électronique, ce qui vous permet d'extraire plus aisément les données qui vous intéressent.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Search-AdminAuditLog](https://docs.microsoft.com/powershell/module/exchange/search-adminauditlog).

### <a name="view-details-of-audit-log-entries"></a>Afficher le détail des entrées du journal d’audit

L’applet de commande **Search-AdminAuditLog** renvoie les champs décrits dans le [contenu du journal d’audit](https://docs.microsoft.com/Exchange/policy-and-compliance/admin-audit-logging/admin-audit-logging#audit-log-contents). Parmi les champs renvoyés par la cmdlet, deux champs ( **CmdletParameters** et **ModifiedProperties** ) comportent des données supplémentaires qu'il est impossible de visualiser par défaut.

Pour afficher le contenu des champs **CmdletParameters** et **ModifiedProperties**, suivez la procédure ci-après. Vous pouvez utiliser la procédure décrite dans **utiliser Exchange Online PowerShell pour rechercher des entrées du journal d’audit et envoyer les résultats à un destinataire** plus loin dans cette rubrique pour créer un fichier XML.

Cette procédure exploite les concepts suivants :

- [about_Arrays](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays)

- [about_Variables](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables)

1. Déterminez les critères sur lesquels doivent porter vos recherches, exécutez la cmdlet **Search-AdminAuditLog** et stockez les résultats dans une variable au moyen de la commande suivante.

    ```PowerShell
    $Results = Search-AdminAuditLog <search criteria>
    ```

2. Chaque entrée du journal d’audit est stockée sous la forme d’un élément de tableau dans la variable `$Results` . Vous pouvez sélectionner un élément de tableau en précisant son index. Les index des éléments de tableau commencent à zéro (0) pour le premier élément du tableau. Par exemple, pour extraire le cinquième élément de tableau dont l'index est 4, utilisez la commande suivante.

    ```PowerShell
    $Results[4]
    ```

3. La commande précédente renvoie l'entrée du journal stockée dans l'élément de tableau 4. Pour afficher le contenu des champs **CmdletParameters** et **ModifiedProperties** pour cette entrée du journal, utilisez les commandes suivantes.

    ```PowerShell
    $Results[4].CmdletParameters
    $Results[4].ModifiedProperties
    ```

4. Pour afficher le contenu des champs **CmdletParameters** ou **ModifiedParameters** dans une autre entrée du journal, modifiez l'index de l'élément de tableau.
