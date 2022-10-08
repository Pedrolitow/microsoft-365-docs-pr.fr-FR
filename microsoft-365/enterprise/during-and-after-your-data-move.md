---
title: Pendant et après le déplacement de vos données
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/02/2022
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection:
- scotvorg
- SPO_Content
search.appverid:
- MET150
ms.localizationpriority: medium
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
f1.keywords:
- NOCSH
description: Les déplacements de données sont des opérations back-end qui se produisent lorsque Microsoft déplace les services et les données associées de votre locataire vers une nouvelle zone géographique de centre de données.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9df2cbbf802dcba692bbd3e4033e15128ee2a1a9
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68171320"
---
# <a name="during-and-after-your-data-move"></a>Pendant et après le déplacement de vos données

Les déplacements de données sont une opération back-end avec un impact minimal sur les utilisateurs finaux. Aucune action de votre part n’est requise lorsque Microsoft déplace chaque service et les données associées pour votre client vers une nouvelle zone géographique de centres de données. Le transfert de données et la validation se déroulent en arrière-plan à l’avance, et n’ont qu’une incidence minimale sur les utilisateurs.
  
> [!NOTE]
> Moves occur at different times for each service. As a result, you'll see the described reduced functionality for each service at a different time.
  
Regardez le Centre de messages Microsoft 365 pour obtenir une confirmation lorsque les déplacements de chacun des Exchange Online, SharePoint Online et du service de conversation Teams sont terminés. Comme indiqué dans le tableau ci-dessous, il peut s’écouler jusqu’à 24 mois après la fin de la période d’inscription pour que les données client de base au repos passent à la nouvelle zone géographique du centre de données.

| Clients avec le pays d’inscription dans | Tous les déplacements terminés d’ici le |
|:-----|:-----|
|Australie, Nouvelle-Zélande, Fidji  <br/> |vendredi 1 juillet 2022  <br/> |
|Japon  <br/> |vendredi 1 juillet 2022  <br/> |
|Inde  <br/> |vendredi 1 juillet 2022  <br/> |
|Canada  <br/> |vendredi 1 juillet 2022  <br/> |
|Corée du Sud  <br/> |vendredi 1 juillet 2022  <br/> |
|Royaume-Uni  <br/> |vendredi 1 juillet 2022  <br/> |
|France  <br/> |vendredi 1 juillet 2022  <br/> |
|Émirats arabes unis  <br/> |vendredi 1 juillet 2022  <br/> |
|Afrique du Sud  <br/> |vendredi 1 juillet 2022  <br/> |
|Suisse, Liechtenstein  <br/> |vendredi 1 juillet 2022  <br/> |
|Norvège  <br/> |1er novembre 2022  <br/> |
|Allemagne  <br/> |1er mai 2023  <br/> |
|Brésil  <br/> |jeudi 1 juin 2023  <br/> |
|Suède  <br/> |1er juin 2024  <br/> |
|Qatar  <br/> |1er mars 2025  <br/> |

## <a name="exchange-online"></a>Exchange Online

Comme le déplacement de chaque utilisateur vers la nouvelle zone géographique de centres de données pour un seul client prend du temps, certains utilisateurs seront encore dans l’ancienne zone géographique de centres de données pendant le déplacement, tandis que d’autres seront dans la nouvelle. Cela signifie que certaines fonctionnalités qui impliquent l’accès à plusieurs boîtes aux lettres peuvent ne pas fonctionner entièrement pendant une période du processus de déplacement, qui peut durer des semaines. Ces fonctionnalités sont décrites dans les sections suivantes.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Ouvrez « Dossier partagé » dans Outlook Web Access 

Some users open a shared mail folder from another mailbox (that the user has read or write permissions to) in Outlook Web Access using the "Shared Folder" feature. The following table describes how access to shared folders works during a mailbox move. Please note that users with full permissions to a shared mailbox can open the mailbox by using Outlook Web Access during the move.
  
| Configuration | Description |
|:-----|:-----|
|L’utilisateur dispose d’autorisations de dossier de boîte aux lettres sur une autre boîte aux lettres  <br/> |Potentiellement limité.  <br/> Si l'utilisateur A et la boîte aux lettres B ne se trouvent pas dans la même zone géographique lors du déplacement de client, l'utilisateur A ne peut pas ouvrir le dossier la boîte aux lettres B dans Outlook Web Access s'il n'a de droit d'accès que pour un dossier spécifique de la boîte aux lettres B.  <br/> Pour ajouter un dossier partagé, cliquez avec le bouton droit de la souris sur le nom d'utilisateur dans le volet de navigation gauche, puis sélectionnez **Ajouter un dossier partagé**.  <br/> |
|Utilisateur disposant de droits d’accès complets sur une autre boîte aux lettres  <br/> |Entièrement pris en charge  <br/> Si l’utilisateur A dispose de l’autorisation « Accès total » à la boîte aux lettres B, l’utilisateur A peut cliquer sur le dossier partagé dans le panneau de navigation gauche dans Outlook Web Access pour ouvrir une fenêtre affichant la boîte aux lettres B.  Un utilisateur peut ouvrir une boîte aux lettres partagée à l’aide d’Outlook Web Access pendant le déplacement sans impact négatif. La limitation s’applique uniquement au partage au niveau du dossier dans une boîte aux lettres.           |
  
## <a name="sharepoint-online"></a>SharePoint Online

Lors du déplacement de SharePoint Online, les données des services suivants sont également déplacées :
  
- OneDrive Entreprise

- Services vidéo Microsoft 365

- Office dans un navigateur

- Applications Microsoft 365 pour les entreprises

- Visio Pro pour Microsoft 365

Une fois que nous avons terminé de déplacer vos données SharePoint Online, vous pouvez voir certains des effets suivants.
  
### <a name="microsoft-365-video-services"></a>Microsoft 365 Video Services

- Le déplacement de vidéos prend plus de temps que le déplacement d'autres contenus dans SharePoint Online.

- Une fois le contenu de SharePoint Online déplacé, vous ne pourrez pas lire les vidéos pendant une certaine période.

- Nous supprimons les copies transcodées du centre de données précédent et les transcodons à nouveau dans le nouveau centre de données.

### <a name="search"></a>Rechercher

Dans le cadre du déplacement de vos données SharePoint Online, nous migrons vos paramètres de recherche et d'index vers un nouvel emplacement. Jusqu'à la **fin** du déplacement de vos données SharePoint Online, nous continuons de desservir vos utilisateurs depuis l'index situé dans l'emplacement d'origine. Dans le nouvel emplacement, la fonction recherche démarre automatiquement une analyse de votre contenu une fois le déplacement de vos données SharePoint Online terminé. À ce moment-là, nous desservirons vos utilisateurs depuis l'index migré. Les modifications apportées à votre contenu après la migration ne sont pas prises en compte dans l’index migré tant que l’analyse ne les a pas récupérées. La plupart des clients ne remarquent pas que les résultats sont moins frais dès que nous avons terminé de déplacer leurs données SharePoint Online, mais certains clients peuvent rencontrer une actualisation réduite dans les 24 à 48 premières heures.
  
Les fonctionnalités de recherche suivantes sont concernées :
  
- Résultats de la recherche et composants WebPart de recherche : Les résultats n’incluent pas les modifications qui se sont produites après la migration jusqu’à ce que l’analyse les ait récupérées. 

- Delve : Delve n’inclut pas les modifications qui se sont produites après la migration jusqu’à ce que l’analyse les ait récupérées.

- Popularity and Search Reports for the site: Counts for Excel reports in the new location only include migrated counts and counts from usage reports that have run after we completed moving your SharePoint Online data. Any counts from the interim period are lost and can't be recovered. This period is typically a couple of days. Some customers might experience shorter or longer losses.

- Portail vidéo : les nombres et les statistiques de vue dépendent des statistiques des rapports Excel. Par conséquent, ils sont perdus pendant le même nombre de jours que les rapports Excel.

- eDiscovery (découverte électronique) : Les éléments modifiés au cours de la migration ne sont pas affichés avant que l’analyse n’ait récupéré les modifications.

- Protection contre la perte de données (DLP) : Les politiques ne sont pas appliquées sur les éléments qui changent avant que l’analyse n’ait récupéré les modifications.

Dans le cadre de la migration, la région par défaut change et tout le nouveau contenu est stocké au repos dans la nouvelle région par défaut. Le contenu existant se déplace en arrière-plan sans impact sur vous pendant 90 jours après la première modification de l’emplacement des données SharePoint Online dans le centre d’administration.

## <a name="microsoft-teams"></a>Microsoft Teams

### <a name="files-tab"></a>Onglet Fichiers

Une fois la migration terminée, l’onglet Fichiers peut prendre plus de temps (jusqu’à 7 secondes) pour être entièrement chargé lorsque l’utilisateur tente de l’utiliser pour la première fois. 

### <a name="read-only-period"></a>Période en lecture seule

Les services de conversation Teams déplacent chaque thread individuellement.  Le thread est verrouillé dans un état en lecture seule pendant le déplacement, qui dure quelques secondes par thread.  Les threads restent accessibles pendant la migration.

## <a name="skype-for-business"></a>Skype Entreprise

Skype Entreprise déplacements ne sont plus disponibles.  [Skype Entreprise Online sera mis hors service](/lifecycle/announcements/skype-for-business-online-retirement) le 31 juillet 2021. Après cette date, le service ne sera plus accessible.
  
## <a name="related-topics"></a>Voir aussi

[Procédure de demande d’un déplacement de données](request-your-data-move.md)

[FAQ général relatif au déplacement de données](data-move-faq.md)
  
[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Services Azure par région](https://azure.microsoft.com/regions/)
