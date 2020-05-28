---
title: Rapports Microsoft 365 dans le centre d’administration-utilisation des applications de messagerie
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: c2ce12a2-934f-4dd4-ba65-49b02be4703d
description: Découvrez comment obtenir des rapports d’utilisation des applications de messagerie électronique à propos des applications de messagerie qui se connectent à Exchange Online et à la version d’Outlook utilisée par les utilisateurs.
ms.openlocfilehash: 80f05e4b356655c859536a46868e7ffde7cdebdb
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44387764"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-apps-usage"></a>Rapports Microsoft 365 dans le centre d’administration-utilisation des applications de messagerie

Le tableau de bord **rapports** Microsoft 365 affiche une vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md). Dans le rapport d’utilisation des applications de messagerie, vous pouvez voir le nombre d’applications de messagerie qui se connectent à Exchange Online. Vous pouvez également afficher les informations relatives à la version des applications Outlook utilisées, ce qui vous permet d'assurer le suivi des personnes utilisant des versions non prises en charge pour installer les versions prises en charge d'Outlook.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, teams, Team communications ou Skype entreprise pour afficher des rapports.  
 
## <a name="how-to-get-to-the-email-apps-report"></a>Comment accéder au rapport des applications de messagerie

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la liste déroulante **Sélectionner un rapport** , **Exchange** sélectionnez utilisation des \> **applications de messagerie**Exchange.
  
## <a name="interpret-the-email-apps-report"></a>Interpréter le rapport des applications de messagerie

Vous pouvez obtenir une vue d’activité des applications de messagerie en examinant les graphiques **utilisateurs** et **clients** . 
  
![Clients de messagerie utilisés](../../media/2a775e46-750f-4fa6-8197-de4b24614bd7.png)
  
|||
|:-----|:-----|
|1.  <br/> |Le rapport d' **utilisation des applications de messagerie** peut être consulté pour connaître les tendances des 7, 30, 90 ou 180. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours après la date actuelle (pas la date de génération du rapport).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement les 24 à 48 heures.  <br/> |
|3.  <br/> |L'affichage **Utilisateurs** indique le nombre d'utilisateurs uniques connectés à Exchange Online à l'aide d'une application de messagerie.  <br/> |
|4.  <br/> |L'affichage **Applications** indique le nombre d'utilisateurs uniques par application sur la période sélectionnée.  <br/> |
|5.  <br/> |La vue **versions** indique le nombre d’utilisateurs uniques pour chaque version d’Outlook dans Windows.  <br/> |
|6.  <br/> | Sur le graphique **Utilisateurs**, l'axe Y représente le nombre total d'utilisateurs uniques connectés à une application n'importe quel jour de la période du rapport.  <br/>  Sur le graphique **Utilisateurs**, l'axe X représente le nombre d'utilisateurs uniques à avoir utilisé l'application pendant la période du rapport.  <br/>  Sur le graphique **Applications**, l'axe Y représente le nombre total d'utilisateurs uniques à avoir utilisé une application spécifique pendant la période du rapport.  <br/>  Sur le graphique **Applications**, l'axe X répertorie les applications de votre organisation.  <br/>  Sur le graphique **Versions**, l'axe Y représente le nombre total d'utilisateurs uniques utilisant une version de bureau spécifique d'Outlook. Si le rapport ne parvient pas à déterminer le nombre de versions d'Outlook, la quantité apparaîtra comme indéterminée.  <br/>  Sur le graphique **Versions**, l'axe X répertorie les applications de votre organisation.  <br/> |
|7.  <br/> |Vous pouvez filtrer la série que vous voyez sur le graphique par selectingan élément dans la légende. Par exemple, dans le graphique **utilisateurs** , sélectionnez **courrier Mac** ou liste **Outlook** ![ de clients de messagerie. Sélectionnez le client de messagerie pour obtenir des données de rapport supplémentaires sur ce client.](../../media/19b9da1b-7b69-4a04-8527-38349f859e84.png) pour afficher uniquement les informations correspondantes. La modification de cette sélection ne modifie pas les informations de la table. Mac Mail, Outlook pour Mac, Outlook Mobile, Outlook Desktop et Outlook sur le web sont des exemples d'applications de messagerie dont vous pouvez disposer dans votre organisation.  <br/> |
|8.  <br/> | Vous ne voyez pas forcément tous les éléments dans la liste en dessous des colonnes jusqu'à ce que vous les ajoutiez.<br/> **Username** est le nom du propriétaire de l’application de messagerie.  <br/> **Date de la dernière activité** correspond à la date la plus récente à laquelle l’utilisateur a lu ou envoyé un message électronique.  <br/> **Mac Mail**, **Mac Outlook**, **Outlook**, **Outlook Mobile** et **Outlook sur le web** sont des exemples d'applications de messagerie dont vous pouvez disposer dans votre organisation.  <br/>  Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **comment masquer les détails au niveau de l’utilisateur ?** dans les [rapports d’activité du centre d’administration 365 de Microsoft](activity-reports.md).  <br/> |
|9.  <br/> |Sélectionnez **gérer les colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Rapport d’utilisation des applications de messagerie-choisir les colonnes](../../media/c17b2a5c-db41-474a-8334-0e5a621b2f16.png)|
|10.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier. csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   

