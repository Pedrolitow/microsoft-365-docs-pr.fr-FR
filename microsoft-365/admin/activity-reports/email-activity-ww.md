---
title: Microsoft 365 Rapports dans le Centre d’administration - Activité de messagerie
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 1cbe2c00-ca65-4fb9-9663-1bbfa58ebe44
description: Découvrez comment obtenir un rapport d’activité de messagerie à l’aide Microsoft 365 tableau de bord rapports dans le Centre d'administration Microsoft 365.
ms.openlocfilehash: 95742f5a8a2c410d0f9c7a526d565d8eb62b13a5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60156029"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-activity"></a>Microsoft 365 Rapports dans le Centre d’administration - Activité de messagerie

Le tableau Microsoft 365 **de rapports de** gestion des données vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, vous pouvez obtenir une vue d'ensemble du trafic de courrier au sein de votre organisation à partir de la page Rapports, puis utiliser le widget Activité de courrier électronique pour mieux comprendre les tendances et les détails de l'activité de courrier de l'utilisateur.
  
> [!NOTE]
> Vous devez être administrateur général, lecteur général ou lecteur de rapports dans Microsoft 365 ou administrateur Exchange, SharePoint, service Teams, Teams Communications ou administrateur Skype Entreprise pour consulter les rapports. 

## <a name="how-to-get-to-the-email-activity-report"></a>Comment accéder au rapport d'activité de courrier

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Sélectionnez **Afficher plus sous** Activité de **messagerie.** 
3. Dans la liste **de listes** de listes de l’activité de messagerie, **sélectionnez Exchange** \> **activité de messagerie.**
  
## <a name="interpret-the-email-activity-report"></a>Interpréter le rapport d'activité de courrier

Vous pouvez visualiser l'activité de courrier d'un utilisateur à l'aide des graphiques **Activité** et **Utilisateurs**. 
  
![Rapport d’activité du courrier électronique.](../../media/5eb1d9e9-8106-4843-acb7-c0238c0da816.png)
  
|Élément|Description|
|:-----|:-----|
|1.  <br/> |Le rapport **Activité de courrier** permet d'observer des tendances sur les 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures.  <br/> |
|3.  <br/> |Le graphique **Activité** permet de comprendre la tendance quantitative de l'activité de courrier au sein de votre organisation. Vous pouvez comprendre la répartition des activités d’envoi, de lecture d’e-mail, de réception de courrier électronique, de création de réunion ou d’interaction de réunion.  <br/> |
|4.  <br/> |La graphique **Utilisateur** permet de comprendre la tendance du nombre d'utilisateurs uniques qui génèrent les activités de courrier. Vous pouvez examiner la tendance des utilisateurs qui envoient des messages électroniques, lisent des messages électroniques, reçoivent des messages électroniques, créent des réunions ou interagissent avec des activités.  <br/> |
|5.  <br/> | Dans le **graphique d’activité,** l’axe Y indique le nombre d’activités du type d’e-mail envoyé, de courrier électronique reçu, de lecture d’e-mail, de création de réunion et d’interaction de réunion.  <br/>  Dans le graphique **d’activité** Utilisateurs, l’axe Y est l’activité d’activité de l’utilisateur du type de courrier électronique envoyé, e-mail reçu, lecture d’e-mail, création de réunion ou interaction de réunion.  <br/>  L'axe X sur les deux graphiques représente la plage de dates sélectionnée pour ce rapport particulier.  <br/> |
|6.  <br/> |Vous pouvez filtrer les séries que vous voyez sur le graphique en sélectionnant un élément dans la légende.  <br/> |
|7.  <br/> | Le tableau présente la répartition des activités de courrier par utilisateur. Il répertorie tous les utilisateurs auxquels un produit Exchange est affecté, ainsi que les activités de courrier de chacun d'eux. <br/> <br/> **Nom d'utilisateur** indique l'adresse de courrier de l'utilisateur.  <br/> **Le nom complet** est le nom complet si l’utilisateur.  <br/> **Supprimé** se réfère aux utilisateurs dont l'état actuel est supprimé, mais qui ont été actifs durant une partie de la période du rapport.  <br/> **Date de suppression** est la date à laquelle l'utilisateur a été supprimé.  <br/> **Date de la dernière activité** indique à quand remonte la dernière activité de lecture ou d'envoi de courrier électronique de l'utilisateur.  <br/> **Actions d'envoi** est le nombre de fois qu'une action d'envoi de courrier a été enregistrée pour l'utilisateur.  <br/> **Actions de réception** est le nombre de fois qu'une action de réception de courrier a été enregistrée pour l'utilisateur.  <br/> **Actions de lecture** est le nombre de fois qu'une action de lecture de courrier a été enregistrée pour l'utilisateur.  <br/> **Les actions créées pour** la réunion sont le nombre de fois qu’une action d’envoi de demande de réunion a été enregistrée pour l’utilisateur.  <br/> **Les actions de réunion interagies** sont le nombre de fois qu’une demande de réunion accepte, provisoire, refuse ou annule une action a été enregistrée pour l’utilisateur.  <br/> **Le produit affecté** est les produits qui sont affectés à cet utilisateur.  <br/>  Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **Comment puis-je masquer les détails** au niveau de l’utilisateur ? dans les rapports d’activité [du Centre d'administration Microsoft 365](activity-reports.md).  <br/> |
|8.  <br/> |Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Rapport d’activité de courrier électronique : choisissez des colonnes.](../../media/80ffa0ad-61c5-4a6f-8a1d-5f6730ff7da9.png)|
|9.  <br/> |Vous pouvez également exporter les données du rapport dans un Excel .csv, en sélectionnant le lien **Exporter.** Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   
> [!NOTE]
> Le rapport d’activité de messagerie est disponible uniquement pour les boîtes aux lettres associées à des utilisateurs titulaires d’une licence.
