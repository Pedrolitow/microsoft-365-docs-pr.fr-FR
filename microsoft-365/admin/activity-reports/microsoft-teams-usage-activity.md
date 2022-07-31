---
title: rapports d’activité d’utilisation Centre d'administration Microsoft 365 Teams
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Le rapport d’utilisation de Teams vous montre comment les utilisateurs communiquent et collaborent dans Teams, y compris le nombre d’utilisateurs actifs, de canaux et de messages.
ms.openlocfilehash: 700ceb8396224b27a29d34b9a84eb527a1dce956
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2022
ms.locfileid: "66992053"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-usage-activity"></a>Rapports Microsoft 365 dans le Centre d’administration - Activité d’utilisation de Microsoft Teams

Le tableau de bord Rapports Microsoft 365 affiche la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md).

Le tout nouveau **rapport d’utilisation de Teams** vous donne une vue d’ensemble de l’activité d’utilisation dans Teams, y compris le nombre d’utilisateurs actifs, de canaux et de messages pour vous permettre de voir rapidement combien d’utilisateurs de votre organisation utilisent Teams pour communiquer et collaborer.  Il inclut également d’autres activités spécifiques à Teams, telles que le nombre d’invités actifs, de réunions et de messages.

![Rapports Microsoft 365 - Rapport d’activité Microsoft Teams.](../../media/teams-usage.png)

## <a name="how-to-get-to-the-microsoft-teams-usage-activity-report"></a>Comment accéder au rapport d’activité d’utilisation de Microsoft Teams

1. Dans le centre d’administration, accédez aux **rapports**, puis sélectionnez **Utilisation**.
2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** dans la carte **d’activité Microsoft Teams** .

   ![Rapports Microsoft 365 - Carte d’activité Microsoft Teams.](../../media/teams-usage-card.png)<br/>

3. Dans la page rapports **Microsoft Teams** , sélectionnez l’onglet **Utilisation de Teams** .

## <a name="interpret-the-microsoft-teams-usage-activity-report"></a>Interpréter le rapport d’activité d’utilisation de Microsoft Teams

Vous pouvez afficher l’activité de l’utilisateur dans le rapport Teams en choisissant l’onglet **Utilisation de Teams** . Les graphiques suivants s’affichent :

- **Utilisation du canal** : suit le nombre d’utilisations de canal, par type d’activité, au fil du temps.

  ![Rapport d’activité d’utilisation teams - utilisation du canal.](../../media/teams-usage-channel.png)

- **Utilisation de l’équipe** : effectue le suivi du nombre d’équipes, par type et par activité, au fil du temps.

  ![Rapport d’activité d’utilisation teams - Utilisation de l’équipe.](../../media/teams-usage-usage.png)

En outre, le graphique inclut des détails d’utilisation pour des équipes individuelles, telles que la date de la dernière activité, les utilisateurs actifs, les canaux actifs et d’autres données.

![Rapports Microsoft 365 - Tableau d’activité d’utilisation de Microsoft Teams.](../../media/teams-usage-table.png)

Dans le tableau, **sélectionnez Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.

![Rapport d’activité d’utilisation teams : choisissez des colonnes.](../../media/teams-usage-columns.png)

Vous pouvez également exporter les données du rapport dans un fichier Excel .csv en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie.  Le format exporté pour **le temps audio**, **le temps vidéo** et le **temps de partage d’écran** suit le format de durée ISO8601.

Le rapport **d’activité d’utilisation de Microsoft Teams** peut être consulté pour les tendances des 7 derniers jours, 30 jours, 90 jours ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).

Pour garantir la qualité des données, nous effectuons des vérifications quotidiennes de validation des données au cours des trois derniers jours et nous comblerons les lacunes détectées. Vous remarquerez peut-être des différences dans les données historiques pendant le processus.

> [!Important]
> Les données d’un jour donné s’affichent dans les 48 heures. Par exemple, les données du 10 janvier doivent apparaître dans le rapport avant le 12 janvier.

### <a name="channel-usage-metrics"></a>Métriques d’utilisation du canal

Le graphique d’utilisation du canal affiche des données sur les métriques suivantes.

|Élément|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|Utilisateurs de canal actifs|Il s’agit du total des utilisateurs actifs internes, des invités actifs et des utilisateurs actifs externes.  <br/><br/> **Utilisateurs actifs internes** : utilisateurs qui ont au moins une action de panneau dans la période spécifiée. Cela exclut les invités.   <br/> **Invités actifs** - Invités qui ont au moins une action de panneau dans la période spécifiée. Un invité est une personne externe à votre organisation qui accède aux ressources partagées en se connectant à un compte invité dans mon annuaire.  <br/> **Utilisateur actif externe** : participants externes qui ont au moins une action de panneau au cours de la période spécifiée. Un participant externe est une personne externe à votre organisation qui participe à une ressource , telle qu’un canal partagé, en utilisant sa propre identité et non un compte invité dans votre annuaire.|
|Canaux actifs|Canaux valides dans les équipes actives qui ont au moins un utilisateur actif au cours de la période spécifiée. Cela inclut les canaux publics, privés ou partagés.|
|Messages de canal|Nombre de messages uniques que l’utilisateur a publiés dans une conversation privée pendant la période spécifiée.|

### <a name="team-usage-metrics"></a>Métriques d’utilisation de l’équipe

Le graphique d’utilisation de Teams affiche des données sur les métriques suivantes.

|Élément|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|Équipes privées|Une équipe privée active ou inactive.|
|Équipes publiques|Une équipe publique active ou inactive.|
|Équipes privées actives|Une équipe privée et active.|
|Équipes publiques actives|Une équipe publique et active.|

### <a name="teams-details"></a>Détails de Teams

Les données des métriques suivantes sont disponibles pour les équipes individuelles.

|Élément|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|ID d’équipe|Identificateur d’équipe|
|Utilisateurs actifs internes|Utilisateurs qui ont au moins une action de panneau dans la période spécifiée, y compris les invités. <br/> <br/> Utilisateurs internes et invités qui résident dans le même locataire. Les utilisateurs internes excluent les invités.|
|Invités actifs|Invités qui ont au moins une action de panneau dans la période spécifiée. <br/> <br/> Un invité est défini comme des personnes extérieures à votre organisation qui accèdent à des ressources partagées en se connectant à un compte invité dans mon annuaire.|
|Utilisateurs actifs externes|Participants externes qui ont au moins une action de panneau dans la période spécifiée.<br/><br/> Un participant externe est défini comme une personne externe à votre organisation qui participe à une ressource ( par exemple, un canal partagé ) en utilisant sa propre identité et non un compte invité dans votre annuaire.|
|Canaux actifs|Canaux valides dans les équipes actives qui ont au moins un utilisateur actif au cours de la période spécifiée. Cela inclut les canaux publics, privés ou partagés.|
|Canaux partagés actifs|Canaux partagés valides dans les équipes actives qui ont au moins un utilisateur actif au moment spécifié. <br/> <br/>Un canal partagé est défini comme un canal Teams qui peut être partagé avec des personnes extérieures à l’équipe. Ces personnes peuvent se trouver au sein de votre organisation ou d’autres organisations Azure AD.|
|Nombre total de réunions organisées|Somme des réunions ponctuelles planifiées, périodiques, ad hoc et non classifiées qu’un utilisateur a organisées pendant la période spécifiée.|
|Posts|Nombre de tous les messages postaux dans les canaux au cours de la période spécifiée.|
|Replies|Nombre de tous les messages de réponse dans les canaux au cours de la période spécifiée.|
|Mentions|Nombre de toutes les mentions effectuées au cours de la période spécifiée.|
|Réactions|Nombre de réactions qu’un utilisateur actif a faites au cours de la période spécifiée.|
|Messages urgents|Nombre de messages urgents dans la période spécifiée.|
|Messages de canal|Nombre de messages uniques que l’utilisateur a publiés dans une conversation d’équipe pendant la période spécifiée.|
|Date de la dernière activité|Date la plus récente à laquelle un membre de l’équipe a validé une action.|

## <a name="make-the-user-specific-data-anonymous"></a>Rendre les données spécifiques à l’utilisateur anonymes

Pour rendre les données du rapport d’activité utilisateur Teams anonymes, vous devez être administrateur général. Cela masque les informations d’identification (à l’aide de hachages MD5) telles que le nom d’affichage, l’e-mail et l’ID d’objet Azure Active Directory dans le rapport et leur exportation.

1. Dans Centre d'administration Microsoft 365, accédez aux **paramètres de l’organisation** **Paramètres** >  et, sous l’onglet **Services**, choisissez **Rapports**.

2. Sélectionnez **Rapports**, puis choisissez **d’afficher les identificateurs anonymes**. Ce paramètre est appliqué aux rapports d’utilisation dans Centre d'administration Microsoft 365 et au Centre d’administration Teams.

3. Sélectionnez **Enregistrer les modifications**.

## <a name="see-also"></a>Voir aussi

[Rapport d’utilisation des périphériques de Microsoft Teams](../activity-reports/microsoft-teams-device-usage-preview.md)

[Rapport d’activité des utilisateurs de Microsoft Teams](../activity-reports/microsoft-teams-user-activity-preview.md)
