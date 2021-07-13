---
title: Microsoft 365 Rapports dans le Centre d’administration - Utilisation SharePoint site
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Obtenez le rapport SharePoint’utilisation du site pour connaître le nombre de fichiers stockés par les utilisateurs dans les sites SharePoint, le nombre d’utilisateurs activement utilisés et le stockage total utilisé.
ms.openlocfilehash: d2c549dbb5ab456dddedf0422cd8aebafab1987d
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "53393330"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-site-usage"></a>Microsoft 365 Rapports dans le Centre d’administration - Utilisation SharePoint site

En tant qu’administrateur Microsoft 365, le tableau de bord **Rapports** vous présente la vue d’ensemble de l’activité sur différents produits de votre organisation. Il vous permet d'explorer pour obtenir des informations plus précises sur les activités spécifiques de chaque produit. Par exemple, vous pouvez obtenir une vue d'ensemble de la valeur que vous apporte SharePoint, en termes de nombre total de fichiers que les utilisateurs stockent sur les sites SharePoint, de nombre de fichiers activement utilisés, et de stockage utilisé sur ces sites. Ensuite, vous pouvez explorer le rapport de l'utilisation du site SharePoint pour comprendre les tendances et les détails par niveau de site pour tous les sites. 
  
> [!NOTE]
> Vous devez être administrateur général, lecteur général ou lecteur de rapports dans Microsoft 365 ou administrateur Exchange, SharePoint, service Teams, Teams Communications ou administrateur Skype Entreprise pour consulter les rapports.
Microsoft 365 Les rapports dans le Centre d’administration ne sont pas pris en charge Cloud de la communauté du secteur public les locataires Élevé et DoD.
 
## <a name="how-to-get-to-the-sharepoint-site-usage-report"></a>Comment accéder au Rapport Utilisation du site SharePoint

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. Dans la page d’accueil du tableau de bord, cliquez sur **le** bouton Afficher plus sur la SharePoint tableau de bord.
  
## <a name="interpret-the-sharepoint-site-usage-report"></a>Interpréter le rapport SharePoint’utilisation du site

Vous pouvez afficher l’utilisation du site dans le rapport SharePoint en choisissant l’onglet **Utilisation du** site.<br/>![Microsoft 365- Rapport d’utilisation SharePoint site Microsoft.](../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png)

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![SharePoint d’utilisation du site : choisir des colonnes](../../media/71ac3195-c494-40c1-9346-a858125ef6df.png)

Vous pouvez également exporter les données du rapport dans un Excel .csv en sélectionnant **le** lien Exporter. Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. 
  
|Élément|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|URL du site  <br/> |URL complète du site. <br/> |
|Deleted  <br/> |État de suppression du site. La suppression effective des sites prend au minimum 7 jours.  <br/> |
|Propriétaire du site  <br/> |Nom d’utilisateur du propriétaire principal du site.   <br/> |
|Nom principal du propriétaire du site  <br/> |Adresse de messagerie du propriétaire du site. <br/> |
|Date de la dernière activité (UTC)  <br/> | Date de la dernière détection de l’activité de fichier ou de l’affichage d’une page sur le site.  <br/> |
|ID d’étiquette de sensibilité du site  <br/> | Étiquette de niveau de sensibilité sur le site.  <br/> |
|Partage externe  <br/> | Paramètres partageables externes sur le site.  <br/> |
|Stratégie d’appareil non gestion  <br/> | Stratégie d’accès au site pour les appareils non utilisés.  <br/> |
|Emplacement géographique  <br/> | Emplacement géographique du site.  <br/> |
|Fichiers  <br/> |Nombre de fichiers sur le site. <br/>|
|Fichiers actifs  <br/> | Nombre de fichiers actifs sur le site.<br/> REMARQUE : si des fichiers ont été supprimés pendant la période spécifiée pour le rapport, le nombre de fichiers actifs affichés dans le rapport peut être supérieur au nombre actuel de fichiers sur le site.  <br/> |
|Stockage utilisé (Mo)  <br/> |Quantité de stockage actuellement utilisée sur le site.  <br/>|
|Stockage alloués (Mo)  <br/> |Quantité maximale de stockage allouée au site.  <br/>|
|Vues de page  <br/> |Nombre de fois que des pages ont été vues sur le site.  <br/>|
|Pages visitées  <br/> |Nombre de pages uniques visitées sur le site.  <br/>|
|Nombre de liens anonymes  <br/> |Nombre de fois que des documents ou des dossiers sont partagés à l’aide de « Tout le monde avec le lien » sur le site.  <br/>|
|Nombre de liens d’entreprise  <br/> |Nombre de fois que des documents ou des dossiers sont partagés à l’aide de « Personnes de l’organisation avec le lien » sur le site.  <br/>|
|Lien sécurisé pour le nombre d’invités  <br/> |Nombre de fois que des documents ou des dossiers sont partagés à l’aide de « personnes spécifiques » sur le site.  <br/>|
|Lien sécurisé pour le nombre de membres  <br/> |Nombre de fois que des documents ou des dossiers sont partagés à l’aide de « personnes spécifiques » sur le site.  <br/>|
|Modèle web racine  <br/> |Modèle utilisé pour créer le site.  <br/> REMARQUE : si vous souhaitez filtrer les données par différents types de sites, exportez les données et utilisez la colonne Modèle Web racine. |
|||