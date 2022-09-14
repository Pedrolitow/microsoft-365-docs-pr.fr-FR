---
title: 'Circonscrire le contenu des sites '
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
description: Dans cet article, découvrez comment limiter les sites SharePoint à un emplacement géographique spécifié dans un environnement multigéographique.
ms.openlocfilehash: 03e1738b88d10717892152655a9e4f3de7a2d847
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67673038"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>Circonscrire le contenu des sites 

Dans certaines circonstances, vous pouvez choisir d’appliquer un site et son contenu de fichier pour qu’il reste à l’emplacement géographique où le site a été créé, soit en empêchant le déplacement du site, soit en empêchant la mise en cache du contenu du fichier du site dans un autre emplacement géographique.

Vous pouvez effectuer cette tâche à l’aide de l’applet de commande [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) avec le paramètre **RestrictedToGeo** . Ce paramètre a la valeur null par défaut, mais vous pouvez la remplacer par l’une des restrictions suivantes :

|Restriction|Description|
|:----------|:----------|
|NoRestriction|Le site peut être déplacé vers un autre emplacement géographique.|
|BlockMoveOnly|Le site ne peut pas être déplacé vers un autre emplacement géographique, mais son contenu peut être mis en cache dans d’autres emplacements géographiques.|
|BlockFull|Le site ne peut pas être déplacé vers un autre emplacement géographique, et les fichiers qu’il contient ne sont pas mis en cache dans d’autres emplacements géographiques. Les titres (extraits du contenu), les noms et d’autres propriétés des fichiers peuvent toujours être mis en cache dans d’autres emplacements géographiques.<br>Le contenu stocké sur le site avant la définition du paramètre RestrictedToGeo sur BlockFull peut rester en cache dans d’autres emplacements géographiques.|

Utilisez la syntaxe suivante :

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

Par exemple :

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
