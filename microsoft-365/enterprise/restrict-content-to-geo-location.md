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
description: Dans cet article, découvrez comment restreindre les sites SharePoint à un emplacement géographique spécifié dans un environnement multigéographique.
ms.openlocfilehash: dd7048ea6eba4c8de7a0566c67d6588f395004c6
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68803658"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>Circonscrire le contenu des sites 

Dans certaines circonstances, vous pouvez choisir de faire en sorte qu’un site et son contenu de fichier restent à l’emplacement _Geography_ où le site a été créé, soit en empêchant le déplacement du site, soit en empêchant la mise en cache du contenu du fichier du site dans un autre emplacement _Geography_ .

Vous pouvez effectuer cette tâche à l’aide de l’applet de commande [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) avec le paramètre **RestrictedToGeo** . Ce paramètre a la valeur par défaut NULL, mais vous pouvez le modifier en l’une des restrictions suivantes :

|Restriction|Description|
|:----------|:----------|
|NoRestriction|Le site peut être déplacé vers un autre emplacement _Geography_ .|
|BlockMoveOnly|Le site ne peut pas être déplacé vers un autre emplacement _Geography_ , mais le contenu du site peut être mis en cache dans d’autres emplacements _Geography_ .|
|BlockFull|Le site ne peut pas être déplacé vers un autre emplacement _Geography_ , et le contenu complet du fichier n’est pas mis en cache dans d’autres emplacements _Geography_ . Le titre des fichiers (collecté à partir du contenu), le nom du fichier et d’autres propriétés du fichier peuvent toujours être mis en cache dans d’autres emplacements _Geography_ .<br>Le contenu stocké dans le site avant sa configuration sur BlockFull peut continuer à être mis en cache dans d’autres emplacements _Geography_ .|

Utilisez la syntaxe suivante :

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

Par exemple :

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
