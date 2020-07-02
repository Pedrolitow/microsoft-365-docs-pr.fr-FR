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
description: Découvrez comment conserver le contenu des boîtes aux lettres supprimées à l’aide de la fonctionnalité de boîtes aux lettres inactives dans Office 365.
ms.openlocfilehash: c2a17a4ce4bf8fb175382fb236bbad6c1bbf2336
ms.sourcegitcommit: 3ddcf08e8deec087df1fe524147313f1cb12a26d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "45023357"
---
# <a name="create-and-manage-inactive-mailboxes"></a>Créer et gérer des boîtes aux lettres inactives

Microsoft 365 vous permet de conserver le contenu des boîtes aux lettres supprimées. Cette fonctionnalité est appelée [boîtes aux lettres inactives](inactive-mailboxes-in-office-365.md). Inactive mailboxes allow you to retain former employees' email after they leave your organization. Une boîte aux lettres devient inactive lorsqu’une conservation pour litige ou une stratégie de rétention (créée dans le centre de sécurité et de conformité dans Office 365 ou Microsoft 365) est appliquée à la boîte aux lettres avant la suppression du compte d’utilisateur correspondant. The contents of an inactive mailbox are retained for the duration of the hold that was placed on the mailbox before it was made inactive. Cela permet aux administrateurs, aux responsables de la mise en conformité et aux gestionnaires d’enregistrements d’utiliser la recherche de contenu pour rechercher et exporter le contenu d’une boîte aux lettres inactive. Les boîtes aux lettres inactives ne peuvent pas recevoir de courriers, et n'apparaissent pas dans le carnet d'adresses partagé de votre organisation ou d'autres listes.
  
> [!IMPORTANT]
> À mesure que nous continuons à investir de différentes manières pour conserver le contenu de la boîte aux lettres, nous annonçaons le retrait des conservations inaltérables dans le centre d’administration Exchange. Cela signifie que vous devez utiliser des conservations pour litige et des stratégies de rétention pour créer une boîte aux lettres inactive. À partir du 1er juillet 2020 vous ne pourrez pas créer de nouvelles conservations inaltérables dans Exchange Online. Toutefois, vous pourrez toujours modifier la durée de conservation d’un blocage sur place placé sur une boîte aux lettres inactive. Toutefois, à partir du 1er octobre 2020, vous ne pourrez pas modifier la durée de la conservation. Vous ne pourrez supprimer une boîte aux lettres inactive qu’en supprimant la conservation inaltérable. Les boîtes aux lettres inactives existantes qui sont en conservation inaltérable resteront conservées jusqu’à ce que la conservation soit supprimée. Pour plus d’informations sur le retrait des conservations inaltérables, consultez la rubrique [déclassement des outils eDiscovery hérités](legacy-ediscovery-retirement.md).
  
## <a name="preparations-before-creating-an-inactive-mailbox"></a>Préparations avant la création d’une boîte aux lettres inactive

- Pour désactiver une boîte aux lettres, vous devez lui avoir affecté une licence Exchange Online plan 2 de sorte qu’une conservation pour litige ou une stratégie de rétention puissent être appliquées à la boîte aux lettres avant sa suppression. Les licences Exchange Online plan 2 font partie d’un abonnement Office 365 entreprise E3 et E5. Si une boîte aux lettres est affectée à une licence Exchange Online plan 1 ou Exchange Online Kiosk (qui fait respectivement partie d’un abonnement Office 365 E1 et F1), vous devez lui attribuer une licence d’archivage Exchange Online distincte de sorte qu’une conservation puisse être appliquée à la boîte aux lettres avant d’être supprimée. Pour plus d'informations, consultez la page [Archivage Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=286153).

- Les licences associées à la boîte aux lettres Exchange Online supprimée seront disponibles une fois que vous aurez supprimé le compte d’utilisateur correspondant. Vous pouvez ensuite [attribuer ces licences à un autre utilisateur](../admin/manage/assign-licenses-to-users.md).

- Si une conservation pour litige ou une stratégie de rétention (configurée pour conserver ou conserver et supprimer du contenu) n’est pas appliquée à une boîte aux lettres avant sa suppression, le contenu de la boîte aux lettres n’est pas conservé ni découvrable. Cependant, la boîte aux lettres peut être récupérée dans les 30 jours suivant sa suppression, mais, à défaut de récupération, elle est définitivement supprimée avec son contenu à l'issue de cette période.

- For more information about Litigation Hold, see [In-Place Hold and Litigation Hold](https://go.microsoft.com/fwlink/p/?LinkId=846124). Pour plus d’informations sur les stratégies de rétention, voir [vue d’ensemble des stratégies de rétention dans Microsoft 365](retention-policies.md).
  
## <a name="create-an-inactive-mailbox"></a>Créer une boîte aux lettres inactive

La création d’une boîte aux lettres inactive implique deux étapes : 1) la mise en attente pour litige ou l’application d’une stratégie de rétention, et 2) pour supprimer la boîte aux lettres ou le compte d’utilisateur correspondant. Une fois la boîte aux lettres inactive, son contenu est conservé jusqu'au retrait de la conservation ou de la stratégie de rétention.
  
### <a name="step-1-place-a-mailbox-on-litigation-hold-or-apply-a-retention-policy"></a>Étape 1 : placement d’une boîte aux lettres en conservation pour litige ou application d’une stratégie de rétention

Placer une boîte aux lettres en conservation pour litige ou appliquer une stratégie de rétention (configurée pour conserver ou conserver, puis supprimer du contenu) conserve le contenu de la boîte aux lettres avant qu’elle ne soit supprimée. Ces deux types de conservation conservent l'ensemble du contenu de la boîte aux lettres, notamment les éléments supprimés et les versions d'origine des éléments modifiés. Les éléments supprimés et modifiés sont conservés dans la boîte aux lettres inactive pendant une période spécifiée, jusqu'à la suppression définitive de la boîte aux lettres inactive en supprimant la conservation ou la stratégie de rétention appliquée.
  
Si une boîte aux lettres est déjà placée sur une boîte aux lettres ou si une stratégie de rétention est déjà appliquée à une boîte aux lettres, il vous suffit de supprimer le compte d’utilisateur correspondant, comme expliqué à l’étape 2.
  
Pour obtenir des procédures pas à pas pour le placement d’une boîte aux lettres en conservation pour litige ou l’application d’une stratégie de rétention, voir :
  
- [Place a mailbox on Litigation Hold](https://go.microsoft.com/fwlink/?linkid=856286)
    
- [Vue d'ensemble des stratégies de rétention](retention-policies.md)
    
> [!NOTE]
> Pour les conservations pour litige et les stratégies de rétention, vous pouvez créer une conservation indéfinie ou sur une conservation basée sur le temps. En cas de conservation indéfinie, le contenu de la boîte aux lettres inactive est conservé pour une durée illimitée, ou jusqu'à la suppression de la conservation ou jusqu'à la modification de la durée de conservation. Une fois la conservation ou la stratégie de rétention supprimée (en supposant que la boîte aux lettres a été supprimée depuis plus de 30 jours), la boîte aux lettres inactive est définitivement supprimée et son contenu n'est plus conservé ni détectable. Dans une stratégie de rétention ou une conservation basée sur le temps, vous spécifiez la durée de la conservation. Cette durée s'applique à un élément et est calculée à partir de la date de réception ou de création de ce dernier. Après l'expiration de la conservation d'un élément de boîte aux lettres, si cet élément est déplacé vers, ou se trouve dans le dossier Éléments récupérables de la boîte aux lettres inactive, l'élément est supprimé définitivement (purgé) de la boîte aux lettres inactive après l'expiration de la période de rétention de l'élément supprimé. 
  
### <a name="step-2-delete-the-mailbox"></a>Étape 2 : Suppression de la boîte aux lettres

Une fois la boîte aux lettres placée en conservation ou une stratégie de rétention appliquée, l’étape suivante consiste à supprimer la boîte aux lettres. La meilleure façon de supprimer une boîte aux lettres est de supprimer le compte d’utilisateur correspondant dans le centre d’administration Microsoft 365. Pour plus d’informations sur la suppression des comptes d’utilisateur, consultez la rubrique [supprimer un utilisateur de votre organisation](https://docs.microsoft.com/microsoft-365/admin/add-users/delete-a-user).
  
> [!NOTE]
> Vous pouvez également supprimer la boîte aux lettres en utilisant la cmdlet **Remove-Mailbox** dans Exchange Online PowerShell. Pour plus d’informations, consultez la rubrique [supprimer ou restaurer des boîtes aux lettres utilisateur dans Exchange Online](https://go.microsoft.com/fwlink/?linkid=856287). 
  

## <a name="view-a-list-of-inactive-mailboxes"></a>Afficher la liste des boîtes aux lettres inactives

Pour afficher la liste des boîtes aux lettres inactives dans votre organisation, procédez comme suit :
  
1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation. 
    
2. Cliquez **Information governance**sur  >  **rétention**de gouvernance des informations.
    
3. Sur la page **rétention** , cliquez sur **autres** ![ barres d’ellipse de la barre de navigation, puis ](../media/9723029d-e5cd-4740-b5b1-2806e4f28208.gif) cliquez sur **boîtes aux lettres inactives**.
    
    ![Sur la page rétention, cliquez sur autres, puis cliquez sur boîtes aux lettres inactives pour afficher la liste des boîtes aux lettres inactives.](../media/761bd90c-3e37-48f9-b1b9-479e90fea267.png)
  
    La page **boîtes aux lettres inactives** s’affiche. Remarque le nombre total de boîtes aux lettres inactives dans votre organisation est affiché. 
    
    ![Une liste de toutes les boîtes aux lettres inactives de votre organisation s’affiche.](../media/57d9d183-0c6c-4bd8-82e7-115f7b7b6de7.png)
  
Vous pouvez également exécuter la commande suivante dans Exchange Online PowerShell pour afficher la liste des boîtes aux lettres inactives.

```powershell
 Get-Mailbox -InactiveMailboxOnly | FT DisplayName,PrimarySMTPAddress,WhenSoftDeleted
```

Vous pouvez cliquer sur Exporter ![ les résultats de la recherche ](../media/47205c65-babd-4b3a-bd7b-98dfd92883ba.png) **Exporter** pour afficher ou télécharger un fichier csv contenant des informations supplémentaires sur les boîtes aux lettres inactives dans votre organisation. 
  
Vous pouvez également exécuter la commande suivante pour exporter la liste des boîtes aux lettres inactives et d’autres informations dans un fichier CSV. Dans cet exemple, le fichier CSV est créé dans le répertoire actif.

```powershell
Get-Mailbox -InactiveMailboxOnly | Select Displayname,PrimarySMTPAddress,DistinguishedName,ExchangeGuid,WhenSoftDeleted | Export-Csv InactiveMailboxes.csv -NoType
```

> [!NOTE]
> Il est possible qu’une boîte aux lettres inactive ait la même adresse SMTP qu’une boîte aux lettres utilisateur active. Dans ce cas, la valeur de la propriété **distinguishedName** ou **ExchangeGuid** peut être utilisée pour identifier une boîte aux lettres inactive de manière unique. 
  
## <a name="search-and-export-the-contents-of-an-inactive-mailbox"></a>Recherche et exportation du contenu d'une boîte aux lettres inactive

Vous pouvez accéder au contenu de la boîte aux lettres inactive à l’aide de l’outil de recherche de contenu dans le centre de sécurité & conformité. When you search an inactive mailbox, you can create a keyword search query to search for specific items or you can return the entire contents of the inactive mailbox. You can preview the search results or export the search results to an Outlook Data (PST) file or as individual email messages. For step-by-step procedures for searching mailboxes and exporting search results, see the following topics:
  
- [Recherche de contenu dans Office 365](content-search.md)
    
- [Exporter les résultats de la recherche de contenu](export-search-results.md)
    
Voici quelques éléments à prendre en considération lors de la recherche de boîtes aux lettres inactives.
  
- Si une recherche de contenu inclut une boîte aux lettres utilisateur et que cette boîte aux lettres est devenue inactive, la recherche de contenu continue de rechercher la boîte aux lettres inactive lorsque vous réexécutez la recherche après qu’elle devient inactive.
    
- Dans certains cas, un utilisateur peut avoir une boîte aux lettres active et une boîte aux lettres inactive possédant la même adresse SMTP. Dans ce cas, seule la boîte aux lettres spécifique que vous sélectionnez comme emplacement pour une recherche de contenu fera l’objet d’une recherche. En d’autres termes, si vous ajoutez la boîte aux lettres d’un utilisateur à une recherche, vous ne pouvez pas supposer que leurs boîtes aux lettres actives et inactives seront recherchées ; seule la boîte aux lettres que vous ajoutez explicitement à la recherche sera recherchée.
    
- Nous vous déconseillons vivement d’utiliser une boîte aux lettres active et une boîte aux lettres inactive portant la même adresse SMTP. Si vous devez réutiliser l’adresse SMTP actuellement attribuée à une boîte aux lettres inactive, nous vous recommandons de récupérer la boîte aux lettres inactive ou de restaurer le contenu d’une boîte aux lettres inactive vers une boîte aux lettres active (ou l’archive d’une boîte aux lettres active), puis de supprimer la boîte aux lettres inactive.
    
## <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Modifier la durée de la conservation pour une boîte aux lettres inactive

Une fois qu’une boîte aux lettres est devenue inactive, vous pouvez modifier la durée de la conservation ou de la stratégie de rétention appliquée à la boîte aux lettres inactive. Pour obtenir des procédures pas à pas, consultez [la rubrique modifier la durée de la conservation pour une boîte aux lettres inactive dans Office 365](change-the-hold-duration-for-an-inactive-mailbox.md).
  
## <a name="recover-an-inactive-mailbox"></a>Récupérer une boîte aux lettres inactive

Si un ancien employé réintègre votre organisation, ou si un nouvel employé est embauché pour assumer les responsabilités d'un employé qui a quitté l'organisation, vous pouvez récupérer le contenu de la boîte aux lettres inactive. Lorsque vous récupérez une boîte aux lettres inactive, la boîte aux lettres est convertie en une nouvelle boîte aux lettres, le contenu et la structure de dossiers de la boîte aux lettres inactive sont conservés et la boîte aux lettres est liée à un nouveau compte d'utilisateur. Une fois récupérée, la boîte aux lettres inactive n'existe plus. Pour obtenir des procédures pas à pas et des informations supplémentaires sur le déroulement de la récupération d’une boîte aux lettres inactive, consultez la rubrique [récupérer une boîte aux lettres inactive dans Office 365](recover-an-inactive-mailbox.md).
  
## <a name="restore-the-contents-of-an-inactive-mailbox-to-another-mailbox"></a>Restaurer le contenu d'une boîte aux lettres inactive vers une autre boîte aux lettres

Si un autre employé assume les responsabilités de l'ancien employé, ou si un autre utilisateur doit accéder au contenu de la boîte aux lettres inactive, vous pouvez restaurer (ou fusionner) le contenu de la boîte aux lettres inactive vers une boîte aux lettres existante. Lorsque vous restaurez une boîte aux lettres inactive, le contenu est copié vers une autre boîte aux lettres. La boîte aux lettres inactive est conservée et reste une boîte aux lettres inactive. La boîte aux lettres inactive peut toujours faire l'objet d'une recherche à l'aide d'eDiscovery, son contenu peut être restauré vers une autre boîte aux lettres, ou il peut être récupéré ou supprimé ultérieurement. Pour obtenir des procédures pas à pas, reportez-vous à la rubrique [restaurer une boîte aux lettres inactive dans Office 365](restore-an-inactive-mailbox.md).
  
## <a name="delete-an-inactive-mailbox"></a>Suppression d’une boîte aux lettres inactive

Si vous n’avez plus besoin de conserver le contenu d’une boîte aux lettres inactive, vous pouvez supprimer définitivement la boîte aux lettres inactive en supprimant la conservation ou en supprimant la stratégie de rétention appliquée à la boîte aux lettres inactive. Si la boîte aux lettres a été supprimée depuis plus de 30 jours, la boîte aux lettres est marquée pour suppression définitive après la suppression de la conservation, et la boîte aux lettres devient non récupérable. Si la boîte aux lettres a été supprimée au cours des 30 derniers jours, vous pouvez toujours récupérer la boîte aux lettres après avoir supprimé la conservation ou la stratégie de rétention. Pour obtenir des procédures pas à pas pour supprimer une stratégie de rétention ou de conservation afin de supprimer définitivement une boîte aux lettres inactive, consultez la rubrique [supprimer une boîte aux lettres inactive](delete-an-inactive-mailbox.md).
