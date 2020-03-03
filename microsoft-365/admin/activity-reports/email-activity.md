---
title: Rapports Microsoft 365 dans le centre d’administration-activité de courrier électronique
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
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 1cbe2c00-ca65-4fb9-9663-1bbfa58ebe44
description: Découvrez comment obtenir un rapport d’activité de courrier électronique à l’aide du tableau de bord des rapports Microsoft 365 dans le centre d’administration Microsoft 365.
ms.openlocfilehash: 34cacd3a1c4682a53fdefd8f3fe26c38651676df
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42353845"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-activity"></a>Rapports Microsoft 365 dans le centre d’administration-activité de courrier électronique

Le tableau de bord **rapports** Microsoft 365 affiche une vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, vous pouvez obtenir une vue d'ensemble du trafic de courrier au sein de votre organisation à partir de la page Rapports, puis utiliser le widget Activité de courrier électronique pour mieux comprendre les tendances et les détails de l'activité de courrier de l'utilisateur.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint ou Skype entreprise pour afficher des rapports. 

## <a name="how-to-get-to-the-email-activity-report"></a>Comment accéder au rapport d'activité de courrier

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la liste déroulante **Sélectionner un rapport** , sélectionnez **activité de courrier** **Exchange** \> .
  
## <a name="interpret-the-email-activity-report"></a>Interpréter le rapport d'activité de courrier

Vous pouvez visualiser l'activité de courrier d'un utilisateur à l'aide des graphiques **Activité** et **Utilisateurs**. 
  
![Rapport d’activité de courrier électronique](../../media/21c1e082-317e-4b5e-b736-661ca5744def.png)
  
|||
|:-----|:-----|
|1.  <br/> |Le rapport **Activité de courrier** permet d'observer des tendances sur les 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours après la date actuelle (pas la date de génération du rapport).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement les 24 à 48 heures.  <br/> |
|3.  <br/> |Le graphique **Activité**permet de comprendre la tendance quantitative de l'activité de courrier au sein de votre organisation. Vous pouvez de comprendre la ventilation des activités d'envoi, de lecture ou de réception de courrier électronique.  <br/> |
|4.  <br/> |La graphique **Utilisateur** permet de comprendre la tendance du nombre d'utilisateurs uniques qui génèrent les activités de courrier. Vous pouvez consulter la tendance d'utilisateurs ayant des activités d'envoi, de lecture ou de réception de courriers.  <br/> |
|5.  <br/> | Dans le graphique **Activité**, l'axe Y indique le nombre d'activités de type envoi, réception et lecture de courrier électronique.  <br/>  Dans le graphique d'activités **Utilisateurs**, l'axe Y indique l'activité d'envoi, de réception et de lecture de courriers de l'utilisateur.  <br/>  L'axe X sur les deux graphiques représente la plage de dates sélectionnée pour ce rapport particulier.  <br/> |
|6.  <br/> |Vous pouvez filtrer la série que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique **activité** , sélectionnez les graphiques de filtre **envoyés**, **reçus**ou **lus** ![pour des données](../../media/a3a9cb3d-b8b1-4c6a-9f6f-18aebf74c3a0.png) connexes spécifiques afin de n’afficher que les informations liées à chacun d’eux. Cette sélection ne modifie nullement les informations figurant dans le tableau grille.  <br/> |
|7.  <br/> | Le tableau présente la répartition des activités de courrier par utilisateur. Il répertorie tous les utilisateurs auxquels un produit Exchange est affecté, ainsi que les activités de courrier de chacun d'eux. <br/> <br/> **Nom d'utilisateur** indique l'adresse de courrier de l'utilisateur.  <br/> **Nom** complet est le nom complet de l’utilisateur.  <br/> **Supprimé** se réfère aux utilisateurs dont l'état actuel est supprimé, mais qui ont été actifs durant une partie de la période du rapport.  <br/> **Date de suppression** est la date à laquelle l'utilisateur a été supprimé.  <br/> **Date de la dernière activité** indique à quand remonte la dernière activité de lecture ou d'envoi de courrier électronique de l'utilisateur.  <br/> **Actions d'envoi** est le nombre de fois qu'une action d'envoi de courrier a été enregistrée pour l'utilisateur.  <br/> **Actions de réception** est le nombre de fois qu'une action de réception de courrier a été enregistrée pour l'utilisateur.  <br/> **Actions de lecture** est le nombre de fois qu'une action de lecture de courrier a été enregistrée pour l'utilisateur.  <br/> Le **produit affecté** est celui qui est affecté à cet utilisateur.  <br/>  Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **comment masquer les détails au niveau de l’utilisateur ?** dans les [rapports d’activité du centre d’administration 365 de Microsoft](activity-reports.md).  <br/> |
|8.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier. csv Excel en sélectionnant **** ![le lien exporter](../../media/816a224b-6ca7-4967-a135-4f6427f64dc8.JPG) le bouton Exporter. Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   
Remarque : le rapport d’activité de messagerie est uniquement disponible pour les boîtes aux lettres associées à des utilisateurs disposant de licences.
