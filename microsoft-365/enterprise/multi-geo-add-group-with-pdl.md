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
description: Découvrez comment créer un groupe Microsoft 365 avec un emplacement de données préféré spécifié dans un environnement multigéographique.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: ff9b6ae6949ab1e6af1ee102abfcf2cb132fed9f
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940709"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>Créer un groupe Microsoft 365 avec un emplacement de données préféré spécifique

Lorsque les utilisateurs d’un environnement multigéographique créent un groupe Microsoft 365, l’emplacement de données préféré du groupe (PDL) est automatiquement défini sur celui de l’utilisateur. Les administrateurs Exchange, SharePoint et généraux peuvent créer des groupes dans n’importe quelle région sélectionnée. 

Si vous devez créer un groupe avec un fichier PDL spécifique, vous pouvez le faire à l’aide du <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">Centre d’administration SharePoint</a> ou de l’applet de commande Exchange Online New-UnifiedGroup Microsoft PowerShell. Lorsque vous procédez de la sorte, la boîte aux lettres de groupe et le site SharePoint associé à celui-ci sont configurés dans l’emplacement par défaut des données spécifié.

Pour créer un groupe Microsoft 365 avec le PDL que vous spécifiez, accédez au <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">Centre d’administration SharePoint</a> à l’emplacement géographique où vous souhaitez créer le site de groupe.

Par exemple :

Si vous souhaitez créer un site de groupe à partir de votre emplacement en Australie, vous pouvez aller à `https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement`

1. Sélectionnez **+ Créer**.
2. Suivez le processus pour créer un site de groupe.

Votre site de groupe est configuré dans l’emplacement géographique correspondant au Centre d’administration SharePoint à partir duquel vous avez initié la demande de création de site. 

Utilisation d’Exchange PowerShell 

Connectez-vous à Exchange Online PowerShell en transmettant le paramètre *-MailBoxRegion* avec le code d’emplacement géographique.

Par exemple : 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Capture d’écran de New-UnifiedGroup cmdlet PowerShell avec syntaxe.](../media/multi-geo-new-group-with-pdl-powershell.png)

> [!Note]
> L’approvisionnement de sites de groupe SharePoint est à la demande. Le site est approvisionné la première fois qu’un propriétaire ou un membre du groupe tente d’y accéder.

## <a name="geo-location-codes"></a>Codes d’emplacement géographique

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="related-topics"></a>Rubriques connexes

[Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

[Créer des groupes avec un emplacement de données préféré spécifique à l’aide de l’API Graph](/graph/api/group-post-groups)
