---
title: Créer un groupe Microsoft 365 avec un emplacement de données préféré spécifique
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
description: Découvrez comment créer un groupe Microsoft 365 avec un emplacement de données préféré spécifié dans un environnement multigéogé.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 7de00ad0d94cda0a47f4981d78ebc07cedab6ada
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318800"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>Créer un groupe Microsoft 365 avec un emplacement de données préféré spécifique

Lorsque les utilisateurs d’un environnement multigéogé créent un groupe Microsoft 365, l’emplacement de données par favori du groupe (PDL) est automatiquement définie sur celui de l’utilisateur. Les administrateurs Exchange, SharePoint et généraux peuvent créer des groupes dans n’importe quelle région sélectionnée. 

Si vous devez créer un groupe avec un PDL spécifique, vous pouvez le faire à l’aide du Centre d’administration <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint</a> ou via l’Exchange Online New-UnifiedGroup cmdlet Microsoft PowerShell. Lorsque vous procédez de la sorte, la boîte aux lettres de groupe et le site SharePoint associé à celui-ci sont configurés dans l’emplacement par défaut des données spécifié.

Pour créer un groupe Microsoft 365 avec la PDL que vous spécifiez, allez au Centre d’administration <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint</a> dans l’emplacement géographique où vous souhaitez créer le site de groupe.

Par exemple :

Si vous souhaitez créer un site de groupe à partir de votre emplacement en Australie, vous pouvez aller à https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement

1. Sélectionnez **+ Créer**.
2. Suivez le processus pour créer un site de groupe.

Votre site de groupe est configuré dans l’emplacement géographique correspondant au Centre d’administration SharePoint à partir duquel vous avez initié la demande de création de site. 

Utilisation d’Exchange PowerShell 

Connectez-vous à Exchange Online PowerShell en transmettant le paramètre *-MailBoxRegion* avec le code d’emplacement géographique.

Par exemple : 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Capture d’écran New-UnifiedGroup cmdlet PowerShell avec une syntaxe.](../media/multi-geo-new-group-with-pdl-powershell.png)

Notez que l’approvisionnement du site du groupe SharePoint est à la demande. Le site est approvisionné la première fois qu’un propriétaire ou un membre du groupe tente d’y accéder.

## <a name="geo-location-codes"></a>Codes d’emplacement géographique

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="related-topics"></a>Voir aussi

[Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

[Créer des groupes avec un emplacement de données préféré spécifique à l’aide Graph API](/graph/api/group-post-groups)
