---
title: Récupérer les données de création de rapports client avec Windows PowerShell pour les partenaires DAP
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Résumé : Utilisez Remote Windows PowerShell pour Microsoft Exchange Online pour récupérer des rapports à partir de locataires de clients individuels.'
ms.openlocfilehash: 88d23874b3dbf3d392937c11365870acc85ea9f7
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68195520"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Récupération des données des rapports du locataire d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Utilisez des Windows PowerShell distantes pour Microsoft Exchange Online afin de récupérer des rapports auprès de locataires clients individuels.

Les partenaires de syndication et de fournisseur de solutions cloud (CSP) peuvent accéder aux données qui composent les rapports client directement via des Windows PowerShell distants pour Exchange Online PowerShell. Cette méthode permet aux partenaires de collecter et d’enregistrer les données de création de rapports, puis d’effectuer d’autres opérations dessus. Après avoir ouvert une connexion à distance, la récupération des données de création de rapports sur une location client est identique à l'exécution de n'importe quelle cmdlet sur la location d'un client.

Cet article explique comment utiliser des Windows PowerShell distantes pour Exchange Online pour vous connecter à une location client unique et récupérer un rapport. Par défaut, Windows PowerShell ne prend pas en charge le regroupement des données des rapports à partir de plusieurs locations de clients. Les rapports que vous récupérez avec cette procédure ne sont destinés qu'aux organisations déléguées ( _DelegatedOrg_) auxquelles vous vous connectez.

## <a name="before-you-begin"></a>Avant de commencer

- Connectez-vous à votre locataire Exchange Online à l’aide de Windows PowerShell distantes. Pour obtenir des instructions, consultez [Se connecter à des locataires Exchange Online avec des Windows PowerShell distants pour les partenaires d’autorisations d’accès délégué (DAP)](/powershell/exchange/connect-to-exchange-online-powershell)

## <a name="run-the-get-stalemailboxreport-sample"></a>Exécution de l’exemple Get-StaleMailboxReport

Une fois que vous avez ouvert une session à distance pour Exchange Online, exécutez la commande suivante pour récupérer **get-StaleMailboxReport** pour la plage de dates du 25/03/2015 au 31/03/2015.

```powershell
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

De nombreuses autres applets de commande de création de rapports sont disponibles pour Exchange Online, Lync Online, SharePoint Online et d’autres services pour le suivi des messages que vous pouvez utiliser. Pour en savoir plus sur les applets de commande de création de rapports disponibles, consultez les articles répertoriés dans la section suivante.

## <a name="see-also"></a>Voir aussi

[Service web de création de rapports Office 365](/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15))

[Cmdlets de création de rapports dans Exchange Online](/powershell/module/exchange/get-csclientdevicedetailreport)

[Aide pour les partenaires](https://go.microsoft.com/fwlink/p/?LinkID=533477)
