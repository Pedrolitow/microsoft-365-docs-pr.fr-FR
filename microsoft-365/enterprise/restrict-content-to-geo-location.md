---
title: 'Circonscrire le contenu des sites '
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
localization_priority: Normal
description: Dans cet article, découvrez comment limiter SharePoint sites à un emplacement géographique spécifié dans un environnement multigéogé.
ms.openlocfilehash: 74255db19b2ecf9b333d33208c63da260b2bd747
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50927263"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>Circonscrire le contenu des sites 

Dans certaines circonstances, vous pouvez imposer qu’un site et les fichiers qu’il contient restent dans l’emplacement géographique où le site a été créé, soit en empêchant le déplacement du site, soit en empêchant la mise en cache des fichiers qu’il contient dans un autre emplacement géographique.

Pour ce faire, vous pouvez utiliser la cmdlet [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) avec le paramètre **RestrictedToGeo**. La valeur par défaut de ce paramètre est NULL, mais vous pouvez la remplacer par l’une des valeurs suivantes :

|Restriction|Description|
|:----------|:----------|
|NoRestriction|Le site peut être déplacé vers un autre emplacement géographique.|
|BlockMoveOnly|Le site ne peut pas être déplacé vers un autre emplacement géographique, mais son contenu peut être mis en cache dans d’autres emplacements géographiques.|
|BlockFull|Le site ne peut pas être déplacé vers un autre emplacement géographique, et les fichiers qu’il contient ne sont pas mis en cache dans d’autres emplacements géographiques. Les titres (extraits du contenu), les noms et d’autres propriétés des fichiers peuvent toujours être mis en cache dans d’autres emplacements géographiques.<br>Le contenu stocké sur le site avant la définition du paramètre RestrictedToGeo sur BlockFull peut rester en cache dans d’autres emplacements géographiques.|

Utilisez la syntaxe suivante :

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

Par exemple :

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`