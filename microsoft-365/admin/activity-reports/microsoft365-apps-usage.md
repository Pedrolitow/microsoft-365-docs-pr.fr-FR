---
title: Rapports Microsoft 365 dans le Centre d’administration - Utilisation des applications Microsoft 365
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
description: Découvrez comment obtenir un rapport Microsoft 365 Apps for usage à l’aide du tableau de bord Rapports Microsoft 365 dans le Centre d’administration Microsoft 365.
ms.openlocfilehash: 362697ba8dd40a12107e1b2d9ad6ef1bededda7d
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579577"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-apps-usage"></a>Rapports Microsoft 365 dans le Centre d’administration - Utilisation des applications Microsoft 365

Le tableau de  bord Rapports Microsoft 365 vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md).

 Par exemple, vous pouvez comprendre l’activité de chaque utilisateur titulaire d’une licence pour utiliser les applications Microsoft 365 Apps en regardant leur activité dans les applications et la façon dont ils sont utilisés sur les plateformes.


 > [!NOTE]
 > Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint ou Skype Entreprise pour consulter les rapports.

## <a name="how-to-get-to-the-microsoft-365-apps-usage-report"></a>Comment obtenir le rapport d’utilisation de Microsoft 365 Apps

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

 2. Dans la **drop-down Sélectionner un rapport,** sélectionnez Utilisation d’Office **365**   \>  **Microsoft 365 Apps.**

## <a name="interpret-the-microsoft-365-apps-usage-report"></a>Interpréter le rapport d’utilisation de Microsoft 365 Apps

Vous pouvez obtenir une vue de l’activité des applications Microsoft  365 de votre utilisateur en regardant les graphiques Utilisateurs **et plateforme.**

![Rapport d’utilisation des applications Microsoft 365](../../media/proplususagenumbers.png)

|Élément|Description|
 |:-----|:-----|
 |1. <br/> |Le rapport d’utilisation de **Microsoft 365 Apps** permet d’afficher les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré). <br/> |
 |2. <br/> |Les données de chaque rapport couvrent généralement jusqu’aux sept derniers jours. <br/> |
 |3. <br/> |La **vue** Utilisateurs montre la tendance du nombre d’utilisateurs actifs pour chaque application ( Outlook, Word, Excel, PowerPoint, OneNote et Teams). Les « utilisateurs actifs » sont les personnes qui effectuent des actions intentionnelles au sein de ces applications. <br/> |
 |4. <br/> |**L’affichage Plateformes** affiche la tendance des utilisateurs actifs sur toutes les applications pour chaque plateforme (Windows, Mac, Web et Mobile). <br/> |
 |5.<br/>|Dans le **graphique Utilisateurs,** l’axe Y indique le nombre d’utilisateurs actifs uniques pour l’application respective. Dans le **graphique Plateformes,** l’axe Y est le nombre d’utilisateurs   uniques pour la plateforme respective. L’axe X des deux graphiques est la date à laquelle une application a été utilisée sur une plateforme donnée.<br/>|
 6.<br/>|Vous pouvez filtrer les séries que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique **Utilisateurs,** sélectionnez Outlook, Word, Excel, PowerPoint, OneDrive ou Teams pour voir uniquement les informations relatives à chacun d’eux. La modification de cette sélection ne modifie pas les informations du tableau de grille en dessous.|
 |7.<br/>|Le tableau présente une répartition des données au niveau utilisateur. Vous pouvez ajouter ou supprimer des colonnes. <br/><br/>**Le nom** d’utilisateur est l’adresse e-mail de l’utilisateur qui a effectué l’activité sur Microsoft Apps.<br><br/>**La date de dernière activation (UTC)** est la date la plus récente à laquelle l’utilisateur a activé son abonnement Microsoft 365 Apps.<br/><br/>**La date de la dernière activité (UTC)** est la date la plus récente à laquelle une activité intentionnelle a été effectuée par l’utilisateur. Pour voir l'activité qui s'est produite à une date spécifique, sélectionnez celle-ci directement dans le graphique.<br/><br/>Les colonnes suivantes correspondent à chaque application qui identifie si l’utilisateur a été actif sur cette application pendant la période sélectionnée :<br> <br>**Outlook** <br>**Word** <br>**Excel**<br>**PowerPoint** <br>**OneNote**<br><br> Les colonnes suivantes correspondent à chaque plateforme qui identifie si l’utilisateur était actif sur cette plateforme pour une application (dans Microsoft 365 Apps) pendant la période sélectionnée :<br><br>**Outlook (Windows)**<br>**Outlook (Mac)**<br>**Outlook (Web)** <br>**Outlook (Mobile)**<br> **Word (Windows)**<br> **Word (Mac)**<br> **Word (Web)**<br> **Word (mobile)**<br> **Excel (Windows)**<br> **Excel (Mac)**<br> **Excel (Web)**<br> **Excel (Mobile)**<br> **PowerPoint (Windows)**<br> **PowerPoint (Mac)**<br>**PowerPoint (Web)**<br> **PowerPoint (mobile)**<br> **OneNote (Windows)**<br> **OneNote (Mac)**<br> **OneNote (Web)**<br>**OneNote (Mobile)**<br> **Teams (Windows)**<br> **Teams (Mac)**<br> **Teams (Web)**<br>**Teams (mobile)** |
 |8.<br/>|Sélectionnez **l’icône Gérer les** colonnes pour ajouter ou supprimer des colonnes dans le rapport.|
 |9.<br/>|Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter.** Cela exporte les données pour tous les utilisateurs et vous permet d’obtenir une agrégation, un tri et un filtrage simples pour une analyse plus approfondie. Si vous avez moins de 100 utilisateurs, vous pouvez trier et filtrer dans le tableau dans le rapport lui-même. Si vous avez plus de 100 utilisateurs, pour filtrer et trier, vous devez exporter les données.|
