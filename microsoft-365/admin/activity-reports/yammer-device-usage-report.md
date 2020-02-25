---
title: Rapports Microsoft 365 dans le centre d’administration-rapport d’utilisation de Yammer Device
ms.author: sirkkuw
author: Sirkkuw
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
ms.assetid: b793ffdd-effa-43d0-849a-b1ca2e899f38
description: 'Obtenir le rapport d’utilisation de Yammer sur les appareils sur lesquels vos utilisateurs utilisent Yammer. '
ms.openlocfilehash: 5202fd2ebe3e99182ecf7cd2d9bee77be0573cde
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42239449"
---
# <a name="microsoft-365-reports-in-the-admin-center---yammer-device-usage-report"></a>Rapports Microsoft 365 dans le centre d’administration-rapport d’utilisation de Yammer Device

Le tableau de bord **rapports** Microsoft 365 affiche une vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez [la rubrique Présentation des rapports](activity-reports.md).
  
Les rapports d'utilisation de Yammer sur les appareils vous donnent des informations sur les appareils sur lesquels vos utilisateurs utilisent Yammer. Vous pouvez afficher le nombre d'utilisateurs quotidiens par type d'appareil et le nombre d'utilisateurs par type d'appareil. Vous pouvez afficher les deux sur une période donnée. Vous pouvez également consulter les détails par utilisateur.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint ou Skype entreprise pour afficher des rapports. 
  
## <a name="how-do-i-get-to-the-yammer-device-usage-report"></a>Comment accéder au rapport d'utilisation de Yammer sur les appareils ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la liste déroulante **Sélectionner un rapport** , sélectionnez **utilisation de l’appareil** **Yammer** \> .
  
## <a name="interpret-the-yammer-activity-report"></a>Interpréter le rapport d'activité Yammer

Les graphiques **Utilisateurs** et **Distribution** donnent un aperçu de l'utilisation de Yammer sur les appareils par vos utilisateurs. 
  
Le rapport d'utilisation sur les appareils contient les informations suivantes.
  
- Utilisez les onglets jour pour afficher les tendances des rapports d’activité d' **utilisation de Yammer** sur les 7 derniers jours, 30 jours, 90 jours ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données de 28 jours maximum à compter de la date actuelle (pas la date à laquelle le rapport a été généré). 
    
- Chaque rapport mentionne la date à laquelle il a été généré. Les rapports reflètent généralement une latence de 24 à 48 heures par rapport à l'heure de l'activité rapportée.
    
- Le graphique **Utilisateurs** vous permet de consulter le nombre d'utilisateurs quotidiens par type d'appareil.<br/>![Affichage des utilisateurs dans le graphique utilisation des appareils Yammer](../media/ecfba1ec-fbea-4491-88da-1fb19b4d5629.png)<br/>![Rapport d’utilisation des appareils Yammer affichant l’affichage des utilisateurs](../media/f396865a-ad6e-4f8b-a145-cc3865b352f4.png)
  
- Le graphique **Distribution** vous permet de consulter le nombre d'utilisateurs par type d'appareil.<br/>![Affichage de la distribution dans le rapport d’utilisation de Yammer Device](../media/7a0b152e-2d2b-4d23-8dc2-046be53b724f.png)<br/>![Rapport d’utilisation de Yammer sur des appareils](../media/780c351d-7a1d-451d-8c16-4c454ef58aa8.png)
  
- Le tableau **Détails** sous le graphique affiche une répartition de l'utilisation de Yammer sur les appareils ventilée par utilisateur. 
    
    Vous pouvez également ajouter et supprimer des colonnes. Les colonnes disponibles sont les suivantes :
    
  - **Nom d'utilisateur** indique l'adresse de courrier de l'utilisateur. Vous pouvez afficher l'adresse de courrier réelle ou rendre ce champ anonyme. 
    
    Cette grille affiche les utilisateurs qui se sont connectés à Yammer à l’aide du compte Microsoft 365 ou qui ont ouvert une session sur le réseau à l’aide de l’authentification unique.
    
  - **Nom d'affichage** indique le nom complet de l'utilisateur. Vous pouvez afficher l'adresse de courrier réelle ou rendre ce champ anonyme. 
    
  - **État utilisateur** indique l'une des trois valeurs suivantes : Activé, Supprimé ou Suspendu. 
    
    Ces rapports affichent des données pour les utilisateurs actifs, suspendus et supprimés. Ils ne reflètent pas les utilisateurs en attente, car ceux-ci ne peuvent pas publier, lire ou aimer un message.
    
  - **Web** indique que l'utilisateur a utilisé Yammer sur le web. 
    
  - **Téléphone Windows** indique que l'utilisateur a utilisé Yammer sur un téléphone Windows. 
    
  - **Téléphone Android** indique que l'utilisateur a utilisé Yammer sur un téléphone Android. 
    
  - **iPhone** indique que l'utilisateur a utilisé Yammer sur un iPhone. 
    
  - **iPad** indique que l'utilisateur a utilisé Yammer sur un iPad. 
    
  - **Autres** indique que l'utilisateur a utilisé Yammer sur un autre appareil, non mentionné précédemment. 
    
    Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **comment masquer les détails au niveau de l’utilisateur ?** dans les [rapports d’activité du centre d’administration 365 de Microsoft](activity-reports.md).
    
- Vous pouvez également exporter les données du rapport dans un fichier. csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. 
    

