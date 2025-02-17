---
title: Centre d'administration Microsoft 365 rapports d’activité par e-mail
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
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
description: Découvrez comment obtenir un rapport d’activité de messagerie et comprendre les tendances des e-mails des utilisateurs à l’aide du tableau de bord Rapports Microsoft 365 dans le Centre d'administration Microsoft 365.
ms.openlocfilehash: 94ae5e27e6ce95b28be587834731642f24c3b182
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68724922"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-activity"></a>Rapports Microsoft 365 dans le Centre d’administration - activité Email

Le tableau de bord Rapports Microsoft 365 vous montre la vue d’ensemble de l’activité dans les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, vous pouvez obtenir une vue d'ensemble du trafic de courrier au sein de votre organisation à partir de la page Rapports, puis utiliser le widget Activité de courrier électronique pour mieux comprendre les tendances et les détails de l'activité de courrier de l'utilisateur.

## <a name="how-to-get-to-the-email-activity-report"></a>Comment accéder au rapport d'activité de courrier

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Sélectionnez **Afficher plus** sous **Email’activité**. 
3. Dans la liste déroulante **Activité Email**, sélectionnez **Activité Email Exchange**\>.
  
## <a name="interpret-the-email-activity-report"></a>Interpréter le rapport d'activité de courrier

Vous pouvez visualiser l'activité de courrier d'un utilisateur à l'aide des graphiques **Activité** et **Utilisateurs**. 
  
![Email rapport d’activité.](../../media/5eb1d9e9-8106-4843-acb7-c0238c0da816.png)

Le rapport **Activité de courrier** permet d'observer des tendances sur les 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, la table affiche les données pendant jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré). Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures.

Le graphique **Activité** permet de comprendre la tendance quantitative de l'activité de courrier au sein de votre organisation. Vous pouvez comprendre la répartition des activités d’envoi d’e-mails, de lecture d’e-mails, d’e-mails reçus, de réunion créée ou d’interaction de réunion. 

Le graphique **Utilisateur** vous permet de comprendre la tendance du nombre d’utilisateurs uniques qui génèrent les activités de messagerie. Vous pouvez examiner la tendance des utilisateurs à effectuer des activités d’envoi, de lecture, de réception d’e-mails, de création de réunion ou d’interaction de réunion. 

Dans le graphique Activité, l’axe Y correspond au nombre d’activités du type e-mail envoyé, e-mail reçu, e-mail lu, réunion créée et réunion interagissante. 

Dans le graphique d’activité Utilisateurs, l’axe Y correspond à l’activité de l’utilisateur qui effectue le type d’e-mail envoyé, d’e-mail reçu, de lecture d’e-mail, de réunion créée ou de réunion interagissante. 

L'axe X sur les deux graphiques représente la plage de dates sélectionnée pour ce rapport particulier. 

Vous pouvez filtrer la série que vous voyez sur le graphique en sélectionnant un élément dans la légende.

 Le tableau présente la répartition des activités de courrier par utilisateur. Il répertorie tous les utilisateurs auxquels un produit Exchange est affecté, ainsi que les activités de courrier de chacun d'eux.

  
|Élément|Description|
|:-----|:-----|
|Nom d’utilisateur  |Adresse e-mail de l’utilisateur. |
|Nom |Nom complet de l’utilisateur. |
|Deleted |Fait référence à l’utilisateur dont l’état actuel est supprimé, mais qui était actif pendant une partie de la période de création de rapports du rapport. |
|Date de suppression |Date à laquelle l’utilisateur a été supprimé. |
|Date de la dernière activité  | Dernière fois que l’utilisateur a effectué une activité de lecture ou d’envoi d’e-mails. |
|Envoyer des actions |Nombre de fois où une action d’envoi d’e-mail a été enregistrée pour l’utilisateur.  |
|Recevoir des actions  |Nombre de fois où une action d’e-mail a été enregistrée pour l’utilisateur. |
|Actions de lecture |Nombre de fois où une action de lecture d’e-mail a été enregistrée pour l’utilisateur. |
|Actions créées par la réunion  |Nombre de fois où une action d’envoi de demande de réunion a été enregistrée pour l’utilisateur. |
|Actions interagissantes de réunion |Nombre de fois où une action d’acceptation, de tentative, de refus ou d’annulation d’une demande de réunion a été enregistrée pour l’utilisateur. |
|Produit affecté  |Produits attribués à cet utilisateur.  |


Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **Comment faire masquer les détails au niveau de l’utilisateur ?** dans les [rapports d’activité dans le Centre d'administration Microsoft 365](activity-reports.md).

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.  

![Email rapport d’activité : choisissez des colonnes.](../../media/80ffa0ad-61c5-4a6f-8a1d-5f6730ff7da9.png)

Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. 
   
> [!NOTE]
> Le rapport d’activité Email est disponible uniquement pour les boîtes aux lettres associées aux utilisateurs disposant de licences.
