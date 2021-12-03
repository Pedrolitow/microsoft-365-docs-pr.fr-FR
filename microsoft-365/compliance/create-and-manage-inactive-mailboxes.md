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
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 296a02bd-ebde-4022-900e-547acf38ddd7
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
description: Créez et gérez des boîtes aux lettres inactives qui conservent le contenu des boîtes aux lettres supprimées dans Microsoft 365.
ms.openlocfilehash: 13b6d883c6c74b2bc674c4f0fd2bd84316d95179
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2021
ms.locfileid: "61283472"
---
# <a name="create-and-manage-inactive-mailboxes"></a>Créer et gérer des boîtes aux lettres inactives

Les boîtes aux lettres inactives vous permet de conserver le courrier électronique des anciens employés après leur départ de votre organisation et sont accessibles par des personnes autorisées qui ont reçu des [autorisations eDiscovery](assign-ediscovery-permissions.md) pour des raisons de conformité ou juridiques. Par exemple, les administrateurs, les responsables de la mise en conformité et les responsables des enregistrements qui peuvent ensuite utiliser la recherche de contenu pour rechercher et exporter le contenu d’une boîte aux lettres inactive. Les boîtes aux lettres inactives ne peuvent pas recevoir de courriers, et n'apparaissent pas dans le carnet d'adresses partagé de votre organisation ou d'autres listes.

Pour plus d’informations sur les boîtes aux lettres inactives, voir [En savoir plus sur les boîtes aux lettres inactives.](inactive-mailboxes-in-office-365.md)

## <a name="create-an-inactive-mailbox"></a>Créer une boîte aux lettres inactive

Rendre une boîte aux lettres inactive nécessite une mise en attente de la boîte aux lettres, puis la suppression de la boîte aux lettres ou du compte d’utilisateur correspondant.

Pour rendre une boîte aux lettres inactive, une licence Exchange Online Plan 2 (ou une licence Exchange Online Plan 1 avec une licence de module Archivage Exchange Online) doit lui être attribuée afin qu’une boîte aux lettres puisse être en attente avant sa suppression. Une fois le compte d’utilisateur supprimé, toute licence Exchange Online associée au compte d’utilisateur peut être assignée à un nouvel utilisateur.

Nous vous recommandons d’utiliser Microsoft 365 rétention pour appliquer la conservation à la boîte aux lettres. D’autres méthodes sont couvertes dans [En savoir plus sur les boîtes aux lettres inactives.](inactive-mailboxes-in-office-365.md)

La meilleure façon de supprimer une boîte aux lettres consiste à supprimer le compte d’utilisateur correspondant dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>. Pour plus d’informations sur la suppression de comptes d’utilisateurs, voir [Supprimer un utilisateur de votre organisation.](../admin/add-users/delete-a-user.md) Toutefois, vous pouvez également supprimer la boîte aux lettres à l’aide de la cmdlet **Remove-Mailbox** Exchange Online PowerShell. Pour plus d’informations, [voir Supprimer ou restaurer des](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes)boîtes aux lettres utilisateur dans Exchange Online .

Le tableau suivant résume le processus de création d'une boîte aux lettres inactive pour différents scénarios de rétention.

<br/>

|À...|Vous devez…|Résultat|
|---|---|---|
|Conserver le contenu de la boîte aux lettres indéfiniment après le départ d’un employé de l’organisation|1. Appliquez Microsoft 365 de rétention avec des actions de rétention pour la boîte aux lettres (une stratégie de rétention) ou des éléments de courrier spécifiques (une ou plusieurs étiquettes de rétention). <br /><br> 2. Attendez que les paramètres de rétention soient appliqués. <br /><br> 3. Supprimez le compte d’Microsoft 365 utilisateur.|Tout le contenu de la boîte aux lettres inactive dont les paramètres de rétention sont appliqués, y compris les éléments du dossier Éléments récupérables, est conservé indéfiniment.|
|Conserver tout le contenu de la boîte aux lettres pendant une période spécifique après le départ d’un employé de l’organisation, puis supprimer la boîte aux lettres|1. Appliquez une stratégie Microsoft 365 rétention à la boîte aux lettres avec des paramètres de rétention qui conservent puis suppriment des éléments à l’expiration de la période de rétention. <br /><br> 2. Attendez que les paramètres de rétention soient appliqués. <br /><br> 3. Supprimez le compte d’Microsoft 365 utilisateur.|Lorsque la période de rétention d’un élément de boîte aux lettres expire, l’élément est déplacé vers le dossier Éléments récupérables, puis supprimé définitivement (purgé) de la boîte aux lettres inactive à l’expiration de la période de rétention des éléments supprimés (pour les boîtes aux lettres Exchange). La période de rétention de la stratégie Microsoft 365 de rétention est toujours basée sur la date d’origine de réception ou de création d’un élément de boîte aux lettres.|


> [!NOTE]
> Si les paramètres de rétention de Microsoft 365 configurés pour conserver, ou conserver puis supprimer du contenu, sont déjà appliqués à la boîte aux lettres ou aux éléments de boîte aux lettres, ou si une conservation pour litige est déjà placée sur une boîte aux lettres, il vous s agit simplement de supprimer le compte d’utilisateur correspondant pour créer une boîte aux lettres inactive.


## <a name="view-a-list-of-inactive-mailboxes"></a>Afficher la liste des boîtes aux lettres inactives

Pour afficher la liste des boîtes aux lettres inactives de votre organisation :

1. Go to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centre de conformité Microsoft 365</a> and sign in using the credentials for a Global administrator or a Compliance administrator account in your organization.

2. Dans le volet de navigation de gauche, cliquez sur **Afficher tout,** puis sur Rétention **de gouvernance des**  >  **informations.**

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

Une fois qu’une boîte aux lettres est inactive, vous pourrez peut-être modifier la durée de la boîte aux lettres inactive.

Pour obtenir des procédures pas à pas, voir Modifier la durée de la boîte aux lettres [inactive.](change-the-hold-duration-for-an-inactive-mailbox.md)
  
## <a name="recover-an-inactive-mailbox"></a>Récupérer une boîte aux lettres inactive

Si un ancien employé réintègre votre organisation, ou si un nouvel employé est embauché pour assumer les responsabilités d'un employé qui a quitté l'organisation, vous pouvez récupérer le contenu de la boîte aux lettres inactive. 

Lorsque vous récupérez une boîte aux lettres inactive, la boîte aux lettres est convertie en une nouvelle boîte aux lettres, le contenu et la structure de dossiers de la boîte aux lettres inactive sont conservés et la boîte aux lettres est liée à un nouveau compte d'utilisateur. Une fois récupérée, la boîte aux lettres inactive n'existe plus. 

Pour obtenir des procédures pas à pas et plus d’informations sur la récupération d’une boîte aux lettres inactive, voir [Récupérer une boîte aux lettres inactive.](recover-an-inactive-mailbox.md)
  
## <a name="restore-the-contents-of-an-inactive-mailbox-to-another-mailbox"></a>Restaurer le contenu d'une boîte aux lettres inactive vers une autre boîte aux lettres

Si un autre employé assume les responsabilités de l'ancien employé, ou si un autre utilisateur doit accéder au contenu de la boîte aux lettres inactive, vous pouvez restaurer (ou fusionner) le contenu de la boîte aux lettres inactive vers une boîte aux lettres existante. 

Lorsque vous restaurez une boîte aux lettres inactive, le contenu est copié vers une autre boîte aux lettres. La boîte aux lettres inactive est conservée et reste une boîte aux lettres inactive. La boîte aux lettres inactive peut toujours faire l'objet d'une recherche à l'aide d'eDiscovery, son contenu peut être restauré vers une autre boîte aux lettres, ou il peut être récupéré ou supprimé ultérieurement. 

Pour obtenir des procédures pas à pas, voir [Restaurer une boîte aux lettres inactive.](restore-an-inactive-mailbox.md)
  
## <a name="delete-an-inactive-mailbox"></a>Suppression d’une boîte aux lettres inactive

Si vous n’avez plus besoin de conserver le contenu d’une boîte aux lettres inactive, vous pouvez supprimer définitivement la boîte aux lettres inactive en supprimant la boîte aux lettres inactive. La boîte aux lettres est conservée pendant 183 jours après la suppression de la conservation ou de la stratégie de rétention et est récupérable pendant cette période. Après 183 jours, la boîte aux lettres est marquée pour suppression définitive et la boîte aux lettres devient non récupérable. 

Pour obtenir des procédures pas à pas pour supprimer une conservation ou une stratégie de rétention pour supprimer définitivement une boîte aux lettres inactive, voir [Supprimer une boîte aux lettres inactive.](delete-an-inactive-mailbox.md)
