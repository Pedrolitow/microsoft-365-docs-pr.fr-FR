---
title: Centre d'administration Microsoft 365 rapports d’utilisation des applications de messagerie
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
ms.assetid: c2ce12a2-934f-4dd4-ba65-49b02be4703d
description: Découvrez comment obtenir un rapport d’utilisation des applications de messagerie pour connaître le nombre d’applications de messagerie qui se connectent à Exchange Online et quelle version des utilisateurs d’Outlook utilisent.
ms.openlocfilehash: a2bc937e0282c13f68f71b08cdd5d07850a649da
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68724856"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-apps-usage"></a>Rapports Microsoft 365 dans le Centre d’administration - Utilisation des applications Email

Le tableau de bord Rapports Microsoft 365 vous montre la vue d’ensemble de l’activité dans les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md). Dans le rapport d’utilisation des applications de messagerie, vous pouvez voir le nombre d’applications de messagerie qui se connectent à Exchange Online. Vous pouvez également afficher les informations relatives à la version des applications Outlook utilisées, ce qui vous permet d'assurer le suivi des personnes utilisant des versions non prises en charge pour installer les versions prises en charge d'Outlook.
  
## <a name="how-to-get-to-the-email-apps-report"></a>Comment accéder au rapport des applications de messagerie

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Sélectionnez **Afficher plus** sous **Email’activité**. 
3. Dans la liste déroulante **Activité Email**, sélectionnez Utilisation **des applications** **Exchange** \> Email.
  
## <a name="interpret-the-email-apps-report"></a>Interpréter le rapport des applications de messagerie

Vous pouvez obtenir une vue de l’activité des applications de messagerie en examinant les **graphiques Utilisateurs** et **Clients** . 
  
![Email clients utilisés.](../../media/d78af7db-2b41-4d37-8b6e-bc7e47edd1dd.png)

Le rapport **d’utilisation des applications Email** peut être consulté pour connaître les tendances des 7 derniers jours, 30 jours, 90 jours ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, la table affiche les données pendant jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré). Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures.

L'affichage **Utilisateurs** indique le nombre d'utilisateurs uniques connectés à Exchange Online à l'aide d'une application de messagerie. 

L'affichage **Applications** indique le nombre d'utilisateurs uniques par application sur la période sélectionnée. 

La vue **Versions** vous indique le nombre d’utilisateurs uniques pour chaque version d’Outlook dans Windows. 

Sur le graphique Utilisateurs, l'axe Y représente le nombre total d'utilisateurs uniques connectés à une application n'importe quel jour de la période du rapport. Et l’axe X est le nombre d’utilisateurs uniques qui ont utilisé l’application pour cette période de rapport. 

Sur le graphique Applications, l'axe Y représente le nombre total d'utilisateurs uniques à avoir utilisé une application spécifique pendant la période du rapport. Et l’axe X est la liste des applications de votre organisation. 

Sur le graphique Versions, l'axe Y représente le nombre total d'utilisateurs uniques utilisant une version de bureau spécifique d'Outlook. Si le rapport ne peut pas résoudre le numéro de version d’Outlook, la quantité s’affiche comme **non déterminée**. Et l’axe X est la liste des applications de votre organisation.

Vous pouvez filtrer la série que vous voyez sur le graphique en sélectionnant un élément dans la légende. Vous ne voyez pas forcément tous les éléments dans la liste en dessous des colonnes jusqu'à ce que vous les ajoutiez.
 
|Élément|Description|
|:-----|:-----|
|Nom d’utilisateur | Nom du propriétaire de l’application de messagerie. |
|Date de la dernière activité | Date la plus récente à laquelle l’utilisateur a lu ou envoyé un e-mail. |
|Messagerie Mac, Mac Outlook, Outlook, Outlook mobile et Outlook sur le web | Exemples d’applications de messagerie que vous pouvez avoir dans votre organisation. |
   
Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **Comment faire masquer les détails au niveau de l’utilisateur ?** dans les [rapports d’activité dans le Centre d'administration Microsoft 365](activity-reports.md). 

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.  

![Email rapport d’utilisation des applications : choisissez des colonnes.](../../media/041bd6ff-27e8-409d-9608-282edcfa2316.png)

Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. 