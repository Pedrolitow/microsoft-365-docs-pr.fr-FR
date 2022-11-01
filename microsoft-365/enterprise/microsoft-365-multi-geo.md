---
title: Microsoft 365 Multi-Geo
ms.reviewer: anfra
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Dans cet article, découvrez comment développer votre présence Microsoft 365 dans plusieurs régions géographiques avec Microsoft 365 Multigéographie.
ms.openlocfilehash: f663d95b6d1d714b0b144d32736013885a7aad87
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68804945"
---
# <a name="microsoft-365-multi-geo"></a>Microsoft 365 Multi-Geo

Le module complémentaire Fonctionnalités multigéographiques Microsoft 365 offre aux clients la possibilité d’étendre leur présence Microsoft 365 à plusieurs régions ou comtés géographiques au sein d’un seul _locataire_ Microsoft 365 existant. Multigéographique permet aux clients de gérer les emplacements de données au repos à un niveau précis pour leurs utilisateurs, sites SharePoint, Groupes Microsoft 365 et équipes Microsoft Teams. Multigéographique est destiné aux clients qui ont besoin de stocker des données client dans plusieurs zones géographiques en même temps pour répondre à leurs exigences de résidence des données et dont les besoins peuvent changer au fil du temps.
  
Microsoft 365 Multi-Geo est conçu pour répondre aux exigences de résidence des données des clients et permettre la collaboration entre et entre l’emplacement satellite des clients et les emplacements de données préférés. Si le client a besoin de fonctionnalités d’optimisation des performances pour Microsoft 365, consultez <a href="https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848" target="_blank">Planification réseau et réglage des performances pour Microsoft 365</a> ou contactez votre groupe de support.

>[!NOTE]
>Exchange Online, SharePoint Online, OneDrive Entreprise et Microsoft Teams sont disponibles pour la configuration multigéographique. Pour plus d’informations, consultez les sections Engagement de résidence des données pour [Exchange Online](m365-dr-workload-exo.md), [SharePoint Online et OneDrive Entreprise](m365-dr-workload-spo.md) et [Microsoft Teams](m365-dr-workload-teams.md#data-residency-commitments-available).

Pour consulter une vidéo de présentation sur Microsoft 365 Multigéographie, voir [SharePoint Online et OneDrive multigéographique pour contrôler l’emplacement où résident vos données](https://www.youtube.com/watch?v=Do9U3JuROhk).

## <a name="multi-geo-architecture"></a>Architecture multigéographique

Dans un environnement multigéographique, votre _client_ Microsoft 365 se compose d’un emplacement central (où votre abonnement Microsoft 365 a été initialement approvisionné) et d’un ou plusieurs emplacements satellites. Dans un _locataire_ multigéographique, les informations sur les emplacements géographiques, les groupes et les informations utilisateur sont maîtrisées dans Azure Active Directory (Azure AD). Étant donné que vos informations _de locataire_ sont maîtrisées de manière centralisée et synchronisées dans chaque emplacement géographique, le partage et les expériences impliquant toute personne de votre entreprise contiennent une prise de conscience globale.

![Capture d'écran de la carte multi-géo depuis le centre d'administration SharePoint.](../media/multi-geo-world-map.png)

## <a name="licensing"></a>Licences

Microsoft 365 Multi-Geo est disponible en tant que module complémentaire aux plans d’abonnement Microsoft 365 suivants pour Accord Entreprise clients. Les clients doivent acheter un nombre de licences multigéographiques égal ou supérieur à 5 % du total de leurs sièges éligibles. Les licences d’abonnement utilisateur doivent se trouver sur le même Contrat Entreprise que les licences multigéographiques. Pour plus d’informations, contactez l’équipe de votre compte Microsoft.

- Microsoft 365 F1, F3, E3 ou E5
- Office 365 F3, E1, E3 ou E5
- Exchange Online (plan 1) ou plan 2
- OneDrive entreprise (plan 1 ou plan 2)
- SharePoint Online Plan 1 ou Plan 2

Notez que les _fonctionnalités multigéographiques dans le plan Microsoft 365_ sont une licence de module complémentaire au niveau de l’utilisateur. Vous avez besoin d’une licence pour chaque utilisateur que vous souhaitez héberger dans un emplacement _géographique satellite_ . Vous pouvez ajouter des licences supplémentaires au fil du temps à mesure que vous ajoutez des utilisateurs dans des emplacements _géographiques satellites_ .

Il n’existe aucune licence multigéographique spécifique aux ressources partagées telles que les sites SharePoint, les Groupes Microsoft 365 ou les équipes Microsoft Teams. Si suffisamment de licences utilisateur multigéographiques ont été acquises, les clients peuvent utiliser multigéographique avec des sites SharePoint, des Groupes Microsoft 365 et des équipes Microsoft Teams sans limitation.

## <a name="microsoft-365-multi-geo-availability"></a>Disponibilité de Microsoft 365 Multi-Geo

Microsoft 365 Multi-Geo est actuellement disponible dans les régions et pays suivants :

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="getting-started"></a>Prise en main

Suivez ces étapes pour commencer à utiliser multigéographique :

1. Travailler avec votre équipe de compte pour ajouter le plan de services des _fonctionnalités multigéographiques dans Microsoft 365_. Ils vous guident pour ajouter le nombre de licences nécessaires. La fonctionnalité multigéographique est disponible pour Accord Entreprise clients.

2. Avant de pouvoir commencer à utiliser Microsoft 365 Multi-Geo, Microsoft doit configurer votre _Exchange Online Locataire_ pour la prise en charge multigéographique. Ce processus de configuration unique est déclenché une fois que vous avez ordonné le plan _de service Fonctionnalités multigéographiques dans Microsoft 365_ et que les licences s’affichent dans votre _locataire_. Vous recevrez des notifications spécifiques à la charge de travail dans le centre de messages [Microsoft 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) une fois que votre _locataire_ aura terminé le processus de configuration de chaque charge de travail, puis vous pourrez commencer à configurer et à utiliser vos fonctionnalités microsoft 365 multigéographiques. Le temps nécessaire à la configuration d’un _locataire_ pour la prise en charge multigéographique varie d’un _locataire_ _à_ l’autre, mais la plupart des locataires se terminent dans le mois suivant la réception des _licences_ de fonctionnalité. _Les locataires plus volumineux ou plus complexes_ peuvent nécessiter plus de temps pour terminer le processus de configuration. Contactez votre équipe de compte pour plus d’informations sur votre _locataire_ spécifique si vous en avez besoin.

3. Lisez [Planifier votre environnement multigéographique](plan-for-multi-geo.md).

4. Découvrez [comment administrer un environnement multigéographique](administering-a-multi-geo-environment.md) et [comment vos utilisateurs feront l’expérience de cet environnement](multi-geo-user-experience.md).

5. Lorsque vous êtes prêt à configurer Microsoft 365 Multi-Geo, [configurez votre client pour une utilisation multigéographique](multi-geo-tenant-configuration.md).

6. [Configurez la recherche](configure-search-for-multi-geo.md).
  
> [!NOTE]
> Pour plus d’informations sur les services Microsoft 365 qui prennent en charge multigéographique, consultez les pages de résidence des données de charge de travail [EXO](m365-dr-workload-exo.md), [ODSP](m365-dr-workload-spo.md) et [Teams](m365-dr-workload-teams.md) pour plus d’informations.


## <a name="see-also"></a>Voir aussi

[Géo multiple dans Exchange Online et OneDrive](https://Aka.ms/GoMultiGeo)

[Fonctionnalités multigéographiques dans OneDrive et SharePoint Online](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)

[Fonctionnalités multi-localisés dans Exchange Online](multi-geo-capabilities-in-exchange-online.md)

[Expérience Teams dans un environnement multigéographique](/microsoftteams/teams-experience-o365odb-spo-multi-geo)
