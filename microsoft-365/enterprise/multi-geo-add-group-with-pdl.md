---
title: Créer un groupe Microsoft 365 avec un emplacement de données préféré spécifique
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
f1.keywords:
- NOCSH
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
description: Découvrez comment créer un groupe Microsoft 365 avec un emplacement de données préféré spécifié dans un environnement multigéographique.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 03a83da1d39debee28dc53c88794a1fb822b0532
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805011"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>Créer un groupe Microsoft 365 avec un emplacement de données préféré spécifique

Lorsque les utilisateurs d’un environnement multigéographique créent un groupe Microsoft 365, l’emplacement de données préféré (PDL) du groupe est automatiquement défini sur celui de l’utilisateur. Les administrateurs généraux, SharePoint et Exchange peuvent créer des groupes dans n’importe quelle _zone géographique_ qu’ils sélectionnent. 

Si vous avez besoin de créer un groupe avec un pdL spécifique, vous pouvez le faire à partir du <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">Centre d’administration SharePoint</a> ou via l’applet de commande Exchange Online New-UnifiedGroup Microsoft PowerShell. Lorsque vous procédez de la sorte, la boîte aux lettres de groupe et le site SharePoint associé à celui-ci sont configurés dans l’emplacement par défaut des données spécifié.

Pour créer un groupe Microsoft 365 avec le PDL que vous spécifiez, accédez au <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">Centre d’administration SharePoint</a> dans l’emplacement _Geography_ où vous souhaitez créer le site de groupe.

Par exemple :

Si vous souhaitez créer un site de groupe à partir de votre emplacement en Australie, vous pouvez aller à `https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement`

1. Sélectionnez **+ Créer**.
2. Suivez le processus pour créer un site de groupe.

Votre site de groupe sera approvisionné à l’emplacement _Geography_ correspondant au centre d’administration SharePoint à partir duquel vous avez lancé la demande de création de site. 

Utilisation d’Exchange PowerShell

Connectez-vous à Exchange Online PowerShell en transmettant le paramètre _-MailBoxRegion_ avec le code d’emplacement géographique.

Par exemple :

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Capture d’écran de New-UnifiedGroup applet de commande PowerShell avec la syntaxe.](../media/multi-geo-new-group-with-pdl-powershell.png)

> [!NOTE]
> L’approvisionnement de sites de groupe SharePoint est à la demande. Le site est approvisionné la première fois qu’un propriétaire ou un membre du groupe tente d’y accéder.

## <a name="geo-location-codes"></a>Codes d’emplacement géographique

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="related-topics"></a>Voir aussi

[Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

[Créer des groupes avec un emplacement de données préféré spécifique à l’aide de API Graph](/graph/api/group-post-groups)
