---
title: Fonctionnalités multi-géographiques OneDrive et SharePoint Online
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
f1.keywords:
- NOCSH
ms.custom: admindeeplinkSPO
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
- highpri
ms.localizationpriority: medium
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Étendez votre présence Microsoft 365 à plusieurs régions géographiques grâce aux fonctionnalités multi-géographiques dans OneDrive Online.
ms.openlocfilehash: 9095aa419d234d3e00c608f866eeaee56a07a4d7
ms.sourcegitcommit: 674dfa2cb2f20546d2f7822e09bacf0e12e2718b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68043766"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>Fonctionnalités multi-géographiques OneDrive et SharePoint Online

Les fonctionnalités multigéographiques dans OneDrive et SharePoint Online permettent de contrôler les ressources partagées telles que les sites d’équipe SharePoint et les boîtes aux lettres de groupe Microsoft 365 stockées au repos dans un emplacement géographique spécifié.

Chaque utilisateur, boîte aux lettres de groupe et site SharePoint ont un emplacement de données préféré (PDL) qui indique l’emplacement géographique où les données associées doivent être stockées. Les donnée personnelle des utilisateurs (boîte aux lettres Exchange et OneDrive), ainsi que les sites de Groupes Microsoft 365 ou SharePoint qu’ils créent peuvent être stockées dans l’emplacement spécifié géographique pour répondre aux exigences de résidence de données. Vous pouvez[spécifier des différents administrateurs pour chaque emplacement géo](add-a-sharepoint-geo-admin.md).

Les utilisateurs profitent d’une expérience transparente lors de l’utilisation des services Microsoft 365, y compris les applications Office, OneDrive et Recherche. Voir [Expérience utilisateur dans un environnement multigéographique](multi-geo-user-experience.md) pour plus de détails.

## <a name="onedrive"></a>OneDrive

Le OneDrive de chaque utilisateur peut être configuré dans ou [déplacé par un administrateur](move-onedrive-between-geo-locations.md) vers un emplacement satellite conformément aux PDL de l’utilisateur. Les fichiers personnels sont alors conservés dans cet emplacement géo, même s’ils peuvent être partagés avec des utilisateurs dans d’autres emplacements géo.

## <a name="sharepoint-sites-and-groups"></a>Sites et groupes SharePoint

La gestion de la fonctionnalité multigéographique est disponible via le <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">Centre d’administration SharePoint</a>. Vous trouverez des informations détaillées dans le [ billet de blog correspondant](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).

Lorsqu’un utilisateur crée un site connecté à un groupe SharePoint dans un environnement multigéographique, son PDL est utilisé pour déterminer l’emplacement géographique où le site et sa boîte aux lettres de groupe associées sont créés. (Si une valeur PDL de l’utilisateur n’a pas été définie ou a été définie sur l’emplacement géo qui n’a pas été configuré comme un emplacement satellite, puis le site et la boîte aux lettres sont créés dans l’emplacement central.)

Les services Microsoft 365 autres qu’Exchange, OneDrive, SharePoint et Teams ne sont pas multigéographiques. Toutefois, Groupes Microsoft 365 qui sont créés par ces services seront configurés avec le fichier PDL du créateur et leur boîte aux lettres de groupe Exchange, le site SharePoint est approvisionné dans la zone géographique correspondante. 

## <a name="managing-the-multi-geo-environment"></a>Gestion de l’environnement multi-Géo

La configuration et la gestion de votre environnement multigéographique s’effectuent via le <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">Centre d’administration SharePoint</a>. 

![Capture d’écran de la page Emplacements géographiques dans le Centre d’administration SharePoint.](../media/sharepoint-multi-geo-admin-center.png)

(Certaines actions, telles que le déplacement d’un site SharePoint ou un site OneDrive nécessitent Microsoft PowerShell).

## <a name="see-also"></a>Voir aussi

[Multi-Geo dans les groupes SharePoint et Microsoft 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[Administration d’un environnement multi-géographique](administering-a-multi-geo-environment.md)

[Quotas de stockage SharePoint dans des environnements multi-géographiques](sharepoint-multi-geo-storage-quota.md)

[Administration des boîtes aux lettres Exchange Online dans un environnement multi-géographique](administering-exchange-online-multi-geo.md)
