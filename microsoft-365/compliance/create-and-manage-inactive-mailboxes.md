---
title: Créer et gérer des boîtes aux lettres inactives
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
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
ms.assetid: 296a02bd-ebde-4022-900e-547acf38ddd7
ms.custom:
- seo-marvel-apr2020
description: Conserver le contenu des boîtes aux lettres supprimées à l’aide de la fonctionnalité de boîtes aux lettres inactives Microsoft 365.
ms.openlocfilehash: f0e95d5853580116db6f7c48396e601058e303e3
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58567771"
---
# <a name="create-and-manage-inactive-mailboxes"></a>Créer et gérer des boîtes aux lettres inactives

Microsoft 365 permet de conserver le contenu des boîtes aux lettres supprimées. Cette fonctionnalité est appelée [boîtes aux lettres inactives](inactive-mailboxes-in-office-365.md). Inactive mailboxes allow you to retain former employees' email after they leave your organization. Une boîte aux lettres devient inactive lorsqu’une conservation pour litige ou une stratégie de rétention (créée dans le centre de sécurité et conformité dans Office 365 ou Microsoft 365) est appliquée à la boîte aux lettres avant la suppression du compte d’utilisateur correspondant. The contents of an inactive mailbox are retained for the duration of the hold that was placed on the mailbox before it was made inactive. Cela permet aux administrateurs, aux responsables de la mise en conformité et aux gestionnaires d’enregistrements d’utiliser la recherche de contenu pour rechercher et exporter le contenu d’une boîte aux lettres inactive. Les boîtes aux lettres inactives ne peuvent pas recevoir de courriers, et n'apparaissent pas dans le carnet d'adresses partagé de votre organisation ou d'autres listes.
  
> [!IMPORTANT]
> À mesure que nous continuons d’investir de différentes façons pour conserver le contenu des boîtes aux lettres, nous anuons le retrait des conservations In-Place dans le Centre d’administration Exchange gestion. Cela signifie que vous devez utiliser des conservations pour litige et des stratégies de rétention pour créer une boîte aux lettres inactive. À compter du 1er juillet 2020, vous ne pourrez plus créer de In-Place de Exchange Online. Toutefois, vous pourrez toujours modifier la durée d’une In-Place placée sur une boîte aux lettres inactive. Toutefois, à compter du 1er octobre 2020, vous ne pourrez pas modifier la durée de la durée de la durée de la période de attente. Vous ne pourrez supprimer une boîte aux lettres inactive qu’en supprimant la In-Place de la boîte aux lettres. Les boîtes aux lettres inactives existantes qui sont en conservation In-Place sont conservées jusqu’à ce que la conservation soit supprimée. Pour plus d’informations sur le retrait des In-Place, voir [Retrait des outils eDiscovery hérités.](legacy-ediscovery-retirement.md)
  
## <a name="preparations-before-creating-an-inactive-mailbox"></a>Préparations avant la création d’une boîte aux lettres inactive

- Pour rendre une boîte aux lettres inactive, une licence Exchange Online Plan 2 doit lui être attribuée afin qu’une conservation pour litige ou une stratégie de rétention puisse être appliquée à la boîte aux lettres avant sa suppression. Exchange Online Les licences Plan 2 font partie d’un abonnement Office 365 Entreprise E3 et E5. Si une boîte aux lettres est affectée à une licence Exchange Online Plan 1 ou Exchange Online Kiosk (qui font partie d’un abonnement Office 365 E1 et F1 respectivement), vous devez lui attribuer une licence Archivage Exchange Online distincte afin qu’une boîte aux lettres puisse être en attente avant sa suppression. Pour plus d'informations, consultez la page [Archivage Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=286153).

- Les licences associées à la boîte aux lettres Exchange Online supprimée seront disponibles après la suppression du compte d’utilisateur correspondant. Vous pouvez ensuite [attribuer ces licences à un autre utilisateur.](../admin/manage/assign-licenses-to-users.md)

- Si une conservation pour litige ou une stratégie de rétention (configurée pour conserver ou conserver puis supprimer du contenu) n’est pas appliquée à une boîte aux lettres avant sa suppression, son contenu ne sera ni conservé ni découvrable. Cependant, la boîte aux lettres peut être récupérée dans les 30 jours suivant sa suppression, mais, à défaut de récupération, elle est définitivement supprimée avec son contenu à l'issue de cette période.

- Pour plus d’informations sur la attente pour litige, [consultez la procédure de attente pour litige.](/exchange/security-and-compliance/in-place-and-litigation-holds) Pour plus d’informations sur les stratégies de rétention, voir [En savoir plus sur les stratégies de rétention et les étiquettes de rétention.](retention.md)
  
## <a name="create-an-inactive-mailbox"></a>Créer une boîte aux lettres inactive

Rendre une boîte aux lettres inactive implique deux étapes : 1) placer la boîte aux lettres en conservation pour litige ou lui appliquer une stratégie de rétention, et 2) supprimer la boîte aux lettres ou le compte d’utilisateur correspondant. Une fois la boîte aux lettres inactive, son contenu est conservé jusqu'au retrait de la conservation ou de la stratégie de rétention.
  
### <a name="step-1-place-a-mailbox-on-litigation-hold-or-apply-a-retention-policy"></a>Étape 1 : Placer une boîte aux lettres en conservation pour litige ou appliquer une stratégie de rétention

Le placement d’une boîte aux lettres en conservation pour litige ou l’application d’une stratégie de rétention (configurée pour conserver ou conserver, puis supprimer du contenu) conserve le contenu de la boîte aux lettres avant sa suppression. Ces deux types de conservation conservent l'ensemble du contenu de la boîte aux lettres, notamment les éléments supprimés et les versions d'origine des éléments modifiés. Les éléments supprimés et modifiés sont conservés dans la boîte aux lettres inactive pendant une période spécifiée, jusqu'à la suppression définitive de la boîte aux lettres inactive en supprimant la conservation ou la stratégie de rétention appliquée.
  
Si une conservation est déjà appliquée à une boîte aux lettres ou si une stratégie de rétention est déjà appliquée à une boîte aux lettres, il vous s agit simplement de supprimer le compte d’utilisateur correspondant, comme expliqué à l’étape 2.
  
Pour obtenir des procédures pas à pas pour placer une boîte aux lettres en conservation pour litige ou appliquer une stratégie de rétention, voir :
  
- [Placer une boîte aux lettres en conservation pour litige](create-a-litigation-hold.md)

- [En savoir plus sur les stratégies et les balises de rétention](retention.md)

> [!NOTE]
> Pour les conservations pour litige et les stratégies de rétention, vous pouvez créer une conservation indéfinie ou une suspension basée sur le temps. En cas de conservation indéfinie, le contenu de la boîte aux lettres inactive est conservé pour une durée illimitée, ou jusqu'à la suppression de la conservation ou jusqu'à la modification de la durée de conservation. Une fois la conservation ou la stratégie de rétention supprimée (en supposant que la boîte aux lettres a été supprimée il y a plus de 183 jours), la boîte aux lettres inactive est marquée pour suppression définitive et son contenu n’est plus conservé ni découvrable. Dans une stratégie de conservation ou de rétention basée sur le temps, vous spécifiez la durée de la conservation. Cette durée s'applique à un élément et est calculée à partir de la date de réception ou de création de ce dernier. Après l'expiration de la conservation d'un élément de boîte aux lettres, si cet élément est déplacé vers, ou se trouve dans le dossier Éléments récupérables de la boîte aux lettres inactive, l'élément est supprimé définitivement (purgé) de la boîte aux lettres inactive après l'expiration de la période de rétention de l'élément supprimé. 
  
### <a name="step-2-delete-the-mailbox"></a>Étape 2 : Suppression de la boîte aux lettres

Une fois que la boîte aux lettres est placée en conservation ou qu’une stratégie de rétention lui est appliquée, l’étape suivante consiste à supprimer la boîte aux lettres. La meilleure façon de supprimer une boîte aux lettres consiste à supprimer le compte d’utilisateur correspondant dans le Centre d’administration Microsoft 365. Pour plus d’informations sur la suppression de comptes d’utilisateurs, voir [Supprimer un utilisateur de votre organisation.](../admin/add-users/delete-a-user.md)
  
> [!NOTE]
> Vous pouvez également supprimer la boîte aux lettres en utilisant la cmdlet **Remove-Mailbox** dans Exchange Online PowerShell. Pour plus d’informations, voir Supprimer ou restaurer des boîtes aux [lettres utilisateur dans Exchange Online](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes). 
  
## <a name="view-a-list-of-inactive-mailboxes"></a>Afficher la liste des boîtes aux lettres inactives

Pour afficher la liste des boîtes aux lettres inactives dans votre organisation :

1. Go to <https://compliance.microsoft.com> and sign in using the credentials for an Global administrator or a Compliance administrator account in your organization.

2. Dans le volet de navigation gauche du Centre de conformité Microsoft 365, cliquez sur Afficher **tout,** puis cliquez sur Gouvernance des informations **> rétention**.

   ![Cliquez sur le bouton Boîte aux lettres inactive dans la page Rétention.](../media/MCCInactiveMailboxes1.png)

3. Dans la page **Rétention,** cliquez sur **Boîte aux lettres inactive** pour afficher la liste des boîtes aux lettres inactives.

4. Sélectionnez une boîte aux lettres inactive pour afficher une page volante avec des informations sur la boîte aux lettres inactive.

   ![La page de présentation affiche des détails sur la boîte aux lettres inactive.](../media/MCCInactiveMailboxes2.png)  

Vous pouvez cliquer sur ![ Exporter les résultats de la recherche.](../media/47205c65-babd-4b3a-bd7b-98dfd92883ba.png) **Exportez** pour afficher ou télécharger un fichier CSV qui contient des informations supplémentaires sur les boîtes aux lettres inactives de votre organisation.

Vous pouvez également exécuter la commande suivante dans Exchange Online PowerShell pour afficher la liste des boîtes aux lettres inactives.

```powershell
 Get-Mailbox -InactiveMailboxOnly | FT DisplayName,PrimarySMTPAddress,WhenSoftDeleted
```

Vous pouvez également exécuter la commande suivante pour exporter la liste des boîtes aux lettres inactives et d’autres informations dans un fichier CSV. Dans cet exemple, le fichier CSV est créé dans le répertoire actuel.

```powershell
Get-Mailbox -InactiveMailboxOnly | Select Displayname,PrimarySMTPAddress,DistinguishedName,ExchangeGuid,WhenSoftDeleted | Export-Csv InactiveMailboxes.csv -NoType
```

> [!NOTE]
> Il est possible qu’une boîte aux lettres inactive puisse avoir la même adresse SMTP qu’une boîte aux lettres utilisateur active. Dans ce cas, la valeur de la **propriété DistinguishedName** ou **ExchangeGuid** peut être utilisée pour identifier de manière unique une boîte aux lettres inactive.
  
## <a name="search-and-export-the-contents-of-an-inactive-mailbox"></a>Recherche et exportation du contenu d'une boîte aux lettres inactive

Vous pouvez accéder au contenu de la boîte aux lettres inactive à l’aide de l’outil de recherche de contenu dans le Centre de conformité Microsoft 365. When you search an inactive mailbox, you can create a keyword search query to search for specific items or you can return the entire contents of the inactive mailbox. You can preview the search results or export the search results to an Outlook Data (PST) file or as individual email messages. For step-by-step procedures for searching mailboxes and exporting search results, see the following topics:
  
- [Recherche de contenu](content-search.md)

- [Exporter les résultats de la recherche](export-search-results.md)

Voici quelques éléments à prendre en considération lors de la recherche de boîtes aux lettres inactives.
  
- Si une recherche de contenu inclut une boîte aux lettres d’utilisateur et que cette boîte aux lettres devient inactive, la recherche de contenu continue d’effectuer une recherche dans la boîte aux lettres inactive lorsque vous réexécutez la recherche après qu’elle est devenue inactive.

- Dans certains cas, un utilisateur peut avoir une boîte aux lettres active et une boîte aux lettres inactive qui ont la même adresse SMTP. Dans ce cas, seule la boîte aux lettres spécifique que vous sélectionnez comme emplacement pour une recherche de contenu sera recherché. En d’autres termes, si vous ajoutez la boîte aux lettres d’un utilisateur à une recherche, vous ne pouvez pas supposer que leurs boîtes aux lettres actives et inactives feront l’être. seule la boîte aux lettres que vous ajoutez explicitement à la recherche sera recherché.

- Nous vous déconseillons vivement d’utiliser une boîte aux lettres active et une boîte aux lettres inactive portant la même adresse SMTP. Si vous devez réutiliser l’adresse SMTP actuellement attribuée à une boîte aux lettres inactive, nous vous recommandons de récupérer la boîte aux lettres inactive ou de restaurer le contenu d’une boîte aux lettres inactive dans une boîte aux lettres active (ou l’archive d’une boîte aux lettres active), puis de supprimer la boîte aux lettres inactive.

## <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Modifier la durée de la conservation pour une boîte aux lettres inactive

Une fois qu’une boîte aux lettres est inactive, vous pouvez modifier la durée de la conservation ou la stratégie de rétention appliquée à la boîte aux lettres inactive. Pour obtenir des procédures pas à pas, voir [Modifier](change-the-hold-duration-for-an-inactive-mailbox.md)la durée de la durée de la Office 365 .
  
## <a name="recover-an-inactive-mailbox"></a>Récupérer une boîte aux lettres inactive

Si un ancien employé réintègre votre organisation, ou si un nouvel employé est embauché pour assumer les responsabilités d'un employé qui a quitté l'organisation, vous pouvez récupérer le contenu de la boîte aux lettres inactive. Lorsque vous récupérez une boîte aux lettres inactive, la boîte aux lettres est convertie en une nouvelle boîte aux lettres, le contenu et la structure de dossiers de la boîte aux lettres inactive sont conservés et la boîte aux lettres est liée à un nouveau compte d'utilisateur. Une fois récupérée, la boîte aux lettres inactive n'existe plus. Pour obtenir des procédures pas à pas et plus d’informations sur la récupération d’une boîte aux lettres [inactive,](recover-an-inactive-mailbox.md)voir Récupérer une boîte aux lettres inactive dans Office 365 .
  
## <a name="restore-the-contents-of-an-inactive-mailbox-to-another-mailbox"></a>Restaurer le contenu d'une boîte aux lettres inactive vers une autre boîte aux lettres

Si un autre employé assume les responsabilités de l'ancien employé, ou si un autre utilisateur doit accéder au contenu de la boîte aux lettres inactive, vous pouvez restaurer (ou fusionner) le contenu de la boîte aux lettres inactive vers une boîte aux lettres existante. Lorsque vous restaurez une boîte aux lettres inactive, le contenu est copié vers une autre boîte aux lettres. La boîte aux lettres inactive est conservée et reste une boîte aux lettres inactive. La boîte aux lettres inactive peut toujours faire l'objet d'une recherche à l'aide d'eDiscovery, son contenu peut être restauré vers une autre boîte aux lettres, ou il peut être récupéré ou supprimé ultérieurement. Pour obtenir des procédures pas à pas, voir Restaurer une boîte aux lettres [inactive dans Office 365](restore-an-inactive-mailbox.md).
  
## <a name="delete-an-inactive-mailbox"></a>Suppression d’une boîte aux lettres inactive

Si vous n’avez plus besoin de conserver le contenu d’une boîte aux lettres inactive, vous pouvez supprimer définitivement la boîte aux lettres inactive en supprimant la conservation ou en supprimant la stratégie de rétention appliquée à la boîte aux lettres inactive. La boîte aux lettres est conservée pendant 183 jours après la suppression de la conservation ou de la stratégie de rétention. Après 183 jours, la boîte aux lettres est marquée pour suppression définitive et la boîte aux lettres devient non récupérable. Si la boîte aux lettres inactive a été supprimée au cours des 183 derniers jours, vous pouvez toujours la récupérer. Pour obtenir des procédures pas à pas pour supprimer une conservation ou une stratégie de rétention pour supprimer définitivement une boîte aux lettres inactive, voir [Supprimer une boîte aux lettres inactive.](delete-an-inactive-mailbox.md)
