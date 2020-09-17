---
title: Vue d’ensemble de la gouvernance de collaboration dans Microsoft 365
ms.reviewer: mmclean
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
ms.custom:
- M365solutions
f1.keywords: NOCSH
description: Découvrez comment régir les fonctionnalités associées dans les groupes Microsoft 365, teams, SharePoint et Yammer.
ms.openlocfilehash: b217dc089eb150d01eed9cd720b2caa290d54bf1
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47950711"
---
# <a name="overview-of-collaboration-governance-in-microsoft-365"></a>Vue d’ensemble de la gouvernance de collaboration dans Microsoft 365

Microsoft 365 dispose d’un ensemble complet d’outils permettant d’implémenter les fonctionnalités de gouvernance dont votre organisation peut avoir besoin. Cet article guide les professionnels de l’informatique pour poser les bonnes questions afin de déterminer leurs besoins en matière de gouvernance et comment les répondre en fonction de leur profil organisationnel.

## <a name="what-are-microsoft-365-groups"></a>Qu’est-ce que les groupes Microsoft 365 ?

Nous connaissons que les organisations utilisent aujourd’hui un ensemble d’outils diversifiés. Il existe une équipe de développeurs qui utilisent la conversation d’équipe, les cadres qui envoient du courrier électronique et l’ensemble de l’organisation qui se connecte via le réseau social de l’entreprise. Plusieurs outils de collaboration sont en cours d’utilisation, car chaque groupe est unique et possède ses propres besoins fonctionnels et son propre style de travail. Certains utiliseront uniquement le courrier électronique, tandis que d’autres seront principalement en conversation. 

Si les utilisateurs dispensent que les outils fournis par le service informatique ne répondent pas à leurs besoins, ils téléchargeront probablement leur application de consommateur favorite qui prend en charge leurs scénarios. Bien que ce processus permette aux utilisateurs de commencer rapidement, il se traduit par une expérience utilisateur frustrante au sein de l’organisation avec plusieurs connexions, des difficultés de partage et des emplacements uniques pour afficher du contenu. Ce concept est appelé « détourage » et représente un risque significatif pour les organisations. Elle réduit la possibilité de gérer uniformément l’accès utilisateur, de garantir la sécurité et les besoins en matière de conformité des services.

Les services, tels que les groupes Microsoft 365, les équipes et Yammer permettent aux utilisateurs d’effectuer des clichés instantanés en fournissant les outils nécessaires à la collaboration. Les groupes Microsoft 365 vous permettent de choisir un ensemble de personnes avec lesquelles vous souhaitez collaborer, et de configurer facilement une collection de ressources à partager pour ces personnes. L’ajout de membres au groupe accorde automatiquement les autorisations nécessaires à tous les biens fournis par le groupe. Teams et Yammer utilisent des groupes Microsoft 365 pour gérer leur appartenance.

![Diagramme illustrant les groupes Microsoft 365 et les services associés](../media/microsoft-365-groups-hub-spoke.png)

Les groupes Microsoft 365 incluent divers contrôles de gouvernance, notamment une stratégie d’expiration, des conventions d’affectation de noms et une stratégie de mots bloqués, pour vous aider à gérer les groupes dans votre organisation. Pour plus d’informations, voir [planifier l’organisation et le cycle de vie des groupes microsoft 365 et Microsoft teams](plan-organization-lifecycle-governance.md) .

## <a name="technical-architecture"></a>Architecture technique

Il existe trois méthodes de communication principales prises en charge par Microsoft 365 :

- Outlook : collaboration par courrier électronique avec une boîte aux lettres et un calendrier de groupe partagé
- Microsoft teams : un espace de travail de conversation permanente dans lequel vous pouvez avoir des conversations informelles, en temps réel, autour de plusieurs sujets, organisés par sous-groupes spécifiques
- Yammer : expérience sociale d’entreprise pour la collaboration

> [!NOTE]
> La création d’un groupe via d’autres applications d’équipe, telles que SharePoint, Planner ou Stream-, crée un groupe avec une boîte de réception Outlook et la possibilité de se connecter à Teams.

En fonction de l’emplacement de création d’un groupe, certaines ressources sont configurées automatiquement, telles que :
- [Boîte de réception](https://support.office.com/article/have-a-group-conversation-in-outlook-a0482e24-a769-4e39-a5ba-a7c56e828b22) -pour les conversations par courrier électronique entre les membres du groupe. Cette boîte de réception dispose d’une adresse de messagerie et peut être configurée pour accepter les messages provenant de personnes extérieures au groupe et même en dehors de votre organisation, comme une liste de distribution traditionnelle.
 - [Calendrier](https://support.office.com/article/schedule-a-meeting-on-a-group-calendar-in-outlook-0cf1ad68-1034-4306-b367-d75e9818376a) : pour la planification des événements associés au groupe.
- [Site d’équipe SharePoint](https://support.office.com/article/what-is-a-sharepoint-team-site-75545757-36c3-46a7-beed-0aaa74f0401e) : référentiel central d’informations, de liens et de contenu concernant votre groupe
- [Bloc-notes OneNote](https://support.office.com/article/get-started-with-onenote-e768fafa-8f9b-4eac-8600-65aa10b2fe97) : pour rassembler des idées, des recherches et des informations
- [Planificateur](https://support.office.com/article/microsoft-planner-help-4a9a13c6-3adf-4a60-a6fc-15c0b15e16fc) : pour l’affectation et la gestion des tâches de projet entre les membres de votre groupe
- [Groupe Yammer](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2) : un emplacement commun pour les conversations et les informations de partage
- Teams : un espace de travail de conversation dans Microsoft 365
- Stream-service de diffusion en continu vidéo

> [!NOTE]
> Lorsqu’un nouveau groupe Office 365 est créé via Yammer ou Teams, le groupe n’est pas visible dans Outlook ou dans le carnet d’adresses, car la communication principale entre ces utilisateurs se produit dans leurs clients respectifs. Les groupes Yammer ne peuvent pas être connectés à Teams.

## <a name="collaboration-options"></a>Options de collaboration

Il existe plusieurs emplacements de collaboration et des conversations dans Microsoft 365. La compréhension de l’emplacement de démarrage d’une conversation peut vous aider à définir une stratégie de communication.

![Diagramme indiquant quand utiliser Teams, Yammer et Outlook](../media/inner-loop-outer-loop.png)

- Équipes : espace de travail de conversation (collaboration à haute vitesse) – boucle interne
  - Conçu pour la collaboration avec les personnes avec lesquelles vous travaillez tous les jours
  - Met des informations à portée de main sur les utilisateurs en une seule expérience
  - Ajouter des onglets, des connecteurs et des bots
  - Conversation en direct, conférence audio/vidéo, réunions enregistrées

- Yammer : se connecter à l’échelle de l’organisation (entreprise social) – boucle externe
  - Communautés de personnes : groupes interfonctionnels de personnes qui partagent un intérêt ou une expertise commune, mais qui ne travaillent pas nécessairement ensemble sur une base quotidienne
  - Connexion de leadership, formation de communautés, communautés basées sur des rôles

- Boîte aux lettres et calendrier (collaboration par messagerie électronique)
  - Utilisation pour une communication ciblée avec un groupe de personnes
  - Calendrier partagé pour les réunions avec d’autres membres du groupe
 
Chaque groupe obtient un site d’équipe SharePoint connecté où les utilisateurs peuvent partager du contenu, créer des pages personnalisées et créer des actualités. Vous pouvez également [connecter des sites d’équipe SharePoint existants à de nouveaux groupes Microsoft 365](https://docs.microsoft.com/sharepoint/dev/features/groupify/groupify-overview).

## <a name="illustrations"></a>Illustre

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams et services de productivité connexes dans Microsoft 365 pour les architectes informatique
L’architecture logique de services de productivité dans Microsoft 365, fonctionnant avec Microsoft Teams.

|**Item**|**Description**|
|:-----|:-----|
|[![Image miniature représentant le poster architecture logique Teams](../downloads/msft-teams-logical-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)  <br>Mise à jour d’avril 2019   |Microsoft fournit une suite de services de productivité qui fonctionnent ensemble pour fournir une expérience de collaboration avec la gouvernance des données, la sécurité et la conformité. <br/> <br/>Cette série d’illustrations fournit une visibilité de l’architecture logique de services de productivité pour les architectes d’entreprise, fonctionnant avec Microsoft Teams.|


### <a name="groups-in-microsoft-365-for-it-architects"></a>Groupes dans Microsoft 365 pour les architectes informatique
Quels sont les besoins des architectes informatique concernant les groupes dans Microsoft 365

|**Item**|**Description**|
|:-----|:-----|
|[![Image miniature pour les groupes infographie](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) <br> Mise à jour de juin 2019|Ces illustrations décrivent les différents types de groupes, la manière dont ceux-ci sont créés et gérés et quelques recommandations en matière de gouvernance.|

## <a name="conference-sessions"></a>Sessions de conférence

Regardez ces sessions de conférence pour en savoir plus sur la gouvernance pour les groupes et les équipes Microsoft 365.

**Notions**

Découvrez les notions de base et les nouvelles innovations dans les groupes Microsoft 365, y compris la gestion et la gouvernance à l’envergure, les meilleures pratiques en matière d’utilisation et d’adoption, ainsi que en libre-service.

- [Adopter les groupes Microsoft 365](https://www.youtube.com/watch?v=dAamBF1gb7M)

**Governance**

Découvrez comment configurer le cycle de vie de vos groupes, les stratégies d’attribution de noms, les étiquettes de classification, la collaboration avec des invités externes et la gestion des autorisations de création de groupe.

- [Transformation de la collaboration et lutter contre l’ombre avec les groupes Office 365](https://www.youtube.com/watch?v=Bhf_bKx3lAg)

**Exemple de client**

Retrouvez un exemple en arrière-plan illustrant la façon dont les groupes Microsoft 365, SharePoint, teams et Yammer travaillent ensemble pour fournir une plateforme de collaboration globale.

- [Recherche de votre collaboration sur les groupes Office 365, SharePoint, teams et Yammer](https://www.youtube.com/watch?v=Rx9eVwqXeQk)
