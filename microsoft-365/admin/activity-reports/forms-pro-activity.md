---
title: Rapports Microsoft 365 dans le Centre d’administration - Activité Voix Client Dynamics 365
ms.author: sirkkuw
author: sirkkuw
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
description: Découvrez comment obtenir un rapport d’activité Microsoft Dynamics 365 Customer Voice à l’aide du tableau de bord Rapports Microsoft 365 dans le Centre d’administration Microsoft 365.
ms.openlocfilehash: de03067197c80634f02318b35a79eb84e33c4b86
ms.sourcegitcommit: 82d8be71c5861a501ac62a774b306a3fc1d4e627
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "48988551"
---
# <a name="microsoft-365-reports-in-the-admin-center---dynamics-365-customer-voice-activity"></a>Rapports Microsoft 365 dans le Centre d’administration - Activité Voix Client Dynamics 365

Le tableau de  bord Rapports Microsoft 365 vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, vous pouvez comprendre l’activité de chaque utilisateur titulaire d’une licence d’utilisation de Microsoft Dynamics 365 Customer Voice en regardant leurs interactions avec Dynamics 365 Customer Voice. Il vous permet également de comprendre le niveau de collaboration en cours en regardant le nombre d’enquêtes pro créées et d’enquêtes pour les professionnels à laquelle les utilisateurs ont répondu. 
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, Teams Service, Teams Communications ou Skype Entreprise pour voir les rapports. 

## <a name="how-to-get-to-the-forms-pro-activity-report"></a>Comment obtenir le rapport d’activité Forms Pro

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la **drop-down Sélectionner un** rapport, sélectionnez Activité Dynamics **365 Customer Voice** \> .

## <a name="interpret-the-dynamics-365-customer-voice-activity-report"></a>Interpréter le rapport d’activité de Dynamics 365 Customer Voice

Vous pouvez obtenir une vue de l’activité Voix client Dynamics 365 de votre utilisateur en regardant les graphiques Activité **et** **Utilisateurs.** 

![Rapport d’activité des formulaires](../../media/formsproactivity.png)

|Item|Description|
|:-----|:-----|
|1.  <br/> |Le rapport d’activité de **Dynamics 365 Customer Voice** permet d’afficher les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).   <br/> |
|2.  <br/> |Les données de chaque rapport sont généralement aussi récentes que les dernières 48 heures.  <br/> |
|3.  <br/> |La **vue** Utilisateurs vous permet de comprendre la tendance du nombre d’utilisateurs Dynamics 365 Customer Voice actifs. Un utilisateur est considéré comme actif s’il a exécuté une activité autour d’une enquête professionnelle (créer, modifier, afficher, etc.) au cours de la période spécifique.  <br/> |
|4.  <br/> |**L’affichage** Activité vous permet de comprendre la tendance du nombre d’utilisateurs actifs. Un utilisateur est considéré comme actif s'il a eu une activité de fichier (enregistrer, synchroniser, modifier ou partager) ou consulté une page au cours de la période spécifiée.<br/> REMARQUE : une activité peut se produire plusieurs fois pour une seule enquête, mais ne compte qu’en tant qu’enquête active. Par exemple, vous pouvez créer une enquête professionnel et continuer à modifier la même enquête plusieurs fois sur une période spécifiée, elle ne compte qu’en tant qu’enquête unique. <br>|
|5.<br/>|Dans le **graphique Utilisateurs,** l’axe Y indique le nombre d’utilisateurs uniques. L’axe X est la date à laquelle les utilisateurs uniques sont actifs. Les légendes sont les suivantes :<br/><br/>**Les concepteurs** signifient que l’utilisateur a créé ou modifié une enquête Dynamics 365 Customer Voice Survey.<br><br>Dans le **graphique d’activité,** l’axe Y est le nombre de réponses Dynamics 365 Customer Voice par enquête. L’axe X est la date à laquelle l’activité Enquête ou Réponse s’est produite. Les légendes sont les suivantes :<br/><br/>**Les enquêtes créées** sont le nombre d’enquêtes Dynamics 365 Customer Voice uniques créées par les utilisateurs<br>**Les** réponses sont le nombre de réponses anonymes ou non anonymes envoyées par les utilisateurs qui ont reçu l’enquête. |
|6.<br/>|Vous pouvez filtrer les séries que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique Utilisateurs, sélectionnez les concepteurs, les répondeurs ou le nombre total d’utilisateurs pour voir uniquement les informations relatives à chacun d’eux. La modification de cette sélection ne modifie pas les informations du tableau de grille en dessous.|
|7.<br/>|Le tableau présente une répartition des activités au niveau de chaque utilisateur. Les légendes sont les suivantes :<br/><br/>**Le nom** d’utilisateur est l’adresse e-mail de l’utilisateur qui a effectué l’activité sur Microsoft Forms.<br/>**La date de la dernière activité (UTC)** est la date la plus récente à laquelle une activité de formulaire a été effectuée par l’utilisateur pour la plage de dates sélectionnée. Pour voir l'activité qui s'est produite à une date spécifique, sélectionnez celle-ci directement dans le graphique.<br/>Cela permet de filtrer le tableau pour afficher les données d’activité des fichiers uniquement pour les utilisateurs qui ont effectué l’activité ce jour-là.<br/><br/>**Le nombre d’enquêtes** créées est le nombre d’enquêtes créées par l’utilisateur.<br/> **Le nombre de réponses d’enquête** est le nombre de réponses des répondeurs auxquels l’enquête a été distribuée.|
|8.<br/>|Sélectionnez **l’icône Gérer les** colonnes pour ajouter ou supprimer des colonnes dans le rapport.|
|9.<br/>|Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant **le** lien Exporter. Cela exporte les données pour tous les utilisateurs et vous permet d’obtenir une agrégation, un tri et un filtrage simples pour une analyse plus approfondie. Si vous avez moins de 100 utilisateurs, vous pouvez trier et filtrer dans le tableau du rapport lui-même. Si vous avez plus de 100 utilisateurs, pour filtrer et trier, vous devez exporter les données.|