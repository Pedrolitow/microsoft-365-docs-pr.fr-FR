---
title: Un cadre de gouvernance de collaboration pour Microsoft 365
ms.reviewer: mmclean
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-overview
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Découvrez les meilleures pratiques de gouvernance pour Microsoft 365 outils de collaboration, notamment Groupes Microsoft 365, Teams, SharePoint et Yammer.
ms.openlocfilehash: f4afed27fa6d40f7f6967583bcfd3f43c69c7963
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65284993"
---
# <a name="what-is-collaboration-governance"></a>Qu'est-ce que la gouvernance de collaboration ?

La gouvernance de la collaboration vous permet de gérer l’accès des utilisateurs aux ressources, de respecter les normes de votre entreprise et de garantir la sécurité de vos données.

Aujourd’hui, les organisations utilisent un ensemble d’outils variés. Il existe l’équipe de développeurs qui utilisent la conversation d’équipe, les cadres qui envoient des messages électroniques et l’ensemble de l’organisation qui se connecte via les réseaux sociaux d’entreprise. Plusieurs outils de collaboration sont utilisés, car chaque groupe est unique et a ses propres besoins fonctionnels et son propre style de travail. Certains utilisent uniquement l’e-mail, tandis que d’autres vivent principalement dans la conversation. 

Si les utilisateurs estiment que les outils fournis par l’informatique ne répondent pas à leurs besoins, ils téléchargeront probablement leur application consommateur favorite qui prend en charge leurs scénarios. Bien que ce processus permette aux utilisateurs de commencer rapidement, cela entraîne une expérience utilisateur frustrante au sein de l’organisation avec plusieurs connexions, des difficultés de partage et aucun emplacement unique pour afficher le contenu. Ce concept est appelé « Shadow IT » et présente un risque significatif pour les organisations. Il réduit la possibilité de gérer uniformément l’accès des utilisateurs, de garantir la sécurité et les besoins en conformité des services.

Les services tels que les groupes Microsoft 365, les Teams et les Yammer autonomisent les utilisateurs et réduisent le risque d’informatique fantôme en fournissant les outils nécessaires pour collaborer. Microsoft 365 dispose d’un ensemble complet d’outils permettant d’implémenter toutes les fonctionnalités de gouvernance dont votre organisation peut avoir besoin. 

![Graphique montrant les options de gouvernance de collaboration dans Microsoft 365.](../media/collaboration-governance-overview.png)

Cette série d’articles vous aidera à comprendre comment les groupes, les équipes et les paramètres SharePoint interagissent, les fonctionnalités de gouvernance disponibles et comment créer et implémenter une infrastructure de gouvernance pour les fonctionnalités de collaboration dans Microsoft 365.

### <a name="setting-up-secure-collaboration-with-microsoft-365"></a>Configuration d’une collaboration sécurisée avec Microsoft 365

Il existe de nombreuses options pour déployer des Groupes Microsoft 365 et des Teams pour une collaboration sécurisée au sein de votre organisation. Nous vous recommandons d’utiliser ce contenu de gouvernance en même temps que [configurer le partage de fichiers sécurisé et la collaboration avec Microsoft Teams](setup-secure-collaboration-with-teams.md) et ses articles associés pour créer la meilleure solution de collaboration pour votre organisation.

### <a name="data-residency-governance"></a>Gouvernance de la résidence des données

Si votre organisation est multinationale et que vous avez des exigences de résidence des données pour différentes zones géographiques, incluez [Microsoft 365 multigéographique](/microsoft-365/enterprise/microsoft-365-multi-geo) dans le cadre de votre plan de gouvernance de collaboration.

## <a name="why-microsoft-365-groups-are-important-in-collaboration-governance"></a>Pourquoi Microsoft 365 groupes sont importants dans la gouvernance de la collaboration

Microsoft 365 groupes vous permet de choisir un ensemble de personnes avec lesquelles vous souhaitez collaborer et de configurer facilement une collection de ressources que ces personnes peuvent partager. L’ajout de membres au groupe accorde automatiquement les autorisations nécessaires à toutes les ressources fournies par le groupe. Les Teams et les Yammer utilisent Microsoft 365 groupes pour gérer leur appartenance.

Microsoft 365 groupes incluent une suite de ressources liées que les utilisateurs peuvent utiliser pour la communication et la collaboration. Les groupes incluent toujours un site SharePoint, un planificateur, un espace de travail Power BI, une boîte aux lettres et un calendrier, et Stream. Selon la façon dont vous créez le groupe, vous pouvez éventuellement ajouter d’autres services tels que Teams, Yammer et Project.

![Diagramme montrant Groupes Microsoft 365 et les services associés.](../media/microsoft-365-groups-hub-spoke.png)

|Resource|Description|
|:------|:----------|
|[Calendar](https://support.office.com/article/schedule-a-meeting-on-a-group-calendar-in-outlook-0cf1ad68-1034-4306-b367-d75e9818376a)|Pour planifier des événements liés au groupe|
|[Boîte de réception](https://support.office.com/article/have-a-group-conversation-in-outlook-a0482e24-a769-4e39-a5ba-a7c56e828b22)|Pour les conversations par e-mail entre les membres du groupe. Cette boîte de réception a une adresse e-mail et peut être configurée pour accepter les messages de personnes extérieures au groupe et même en dehors de votre organisation, un peu comme une liste de distribution traditionnelle.|
|[notebook OneNote](https://support.office.com/article/get-started-with-onenote-e768fafa-8f9b-4eac-8600-65aa10b2fe97)|Pour recueillir des idées, des recherches et de l’information|
|[Planner](https://support.office.com/article/microsoft-planner-help-4a9a13c6-3adf-4a60-a6fc-15c0b15e16fc)|Pour affecter et gérer des tâches de projet parmi les membres de votre groupe|
|[espace de travail Power BI](/power-bi/collaborate-share/service-new-workspaces)|Espace de collaboration de données avec des tableaux de bord et des rapports|
|[Project et feuille de route](https://support.microsoft.com/project)|Outils de gestion de projet web|
|[site d’équipe SharePoint ;](https://support.office.com/article/what-is-a-sharepoint-team-site-75545757-36c3-46a7-beed-0aaa74f0401e)|Un référentiel central pour les informations, les liens et le contenu relatifs à votre groupe|
|[Stream](https://support.microsoft.com/microsoft-stream)|Un service de streaming vidéo|
|[Teams](https://support.microsoft.com/teams)|Un espace de travail basé sur une conversation dans Microsoft 365|
|[groupe Yammer](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)|Un lieu commun pour avoir des conversations et partager des informations|

Groupes Microsoft 365 inclut divers contrôles de gouvernance, notamment une stratégie d’expiration, des conventions de nommage et une stratégie de mots bloqués, pour vous aider à gérer les groupes de votre organisation. Étant donné que les groupes contrôlent l’appartenance et l’accès à cette suite de ressources, la gestion des groupes est un élément clé de la gouvernance de la collaboration dans Microsoft 365.

## <a name="define-collaboration-governance-best-practices-for-your-organization"></a>Définir les meilleures pratiques de gouvernance de la collaboration pour votre organisation

Il existe plusieurs emplacements pour collaborer et avoir des conversations dans Microsoft 365. Comprendre où les utilisateurs peuvent démarrer des conversations peut vous aider à définir une stratégie de communication.

Il existe trois méthodes de communication principales prises en charge par Microsoft 365 :

- Outlook : collaboration par e-mail avec une boîte de réception et un calendrier de groupe partagés
- Microsoft Teams : espace de travail basé sur une conversation permanente dans lequel vous pouvez avoir des conversations informelles en temps réel autour de diverses rubriques, organisées par des sous-groupes spécifiques
- Yammer : expérience sociale d’entreprise pour la collaboration

![Diagramme montrant quand utiliser Teams, Yammer et Outlook.](../media/inner-loop-outer-loop.png)

- Teams : espace de travail basé sur la conversation (collaboration à haute vitesse) – boucle interne
  - Conçu pour la collaboration avec les personnes avec lesquelles vos utilisateurs travaillent chaque jour
  - Met les informations à portée de main des utilisateurs dans une expérience unique
  - Ajouter des onglets, des connecteurs et des bots
  - Conversation en direct, audio/vidéoconférence, réunions enregistrées

- Yammer : se connecter à travers l’organisation (entreprise sociale) – boucle externe
  - Communautés de pratique - Groupes interfonctionnels de personnes qui partagent un intérêt commun ou une expertise commune, mais qui ne travaillent pas nécessairement ensemble au quotidien
  - Connexion de leadership, communautés d’apprentissage, communautés basées sur des rôles

- Boîte aux lettres et calendrier (collaboration basée sur l’e-mail)
  - Utilisé pour la communication ciblée avec un groupe de personnes
  - Calendrier partagé pour les réunions avec d’autres membres du groupe
 
Lorsque vous déterminez comment utiliser les fonctionnalités de collaboration dans Microsoft 365, envisagez ces méthodes de communication et celles que vos utilisateurs sont susceptibles d’utiliser dans différents scénarios.

> [!NOTE]
> Lorsqu’un groupe Office 365 est créé via Yammer ou Teams, le groupe n’est pas visible dans Outlook ou le carnet d’adresses, car la communication principale entre ces utilisateurs se produit dans leurs clients respectifs. Yammer groupes ne peuvent pas être connectés à Teams.

## <a name="collaboration-governance-best-practices-checklist"></a>Liste de contrôle des meilleures pratiques de gouvernance de la collaboration

Lorsque vous démarrez votre processus de planification de la gouvernance, gardez à l’esprit les bonnes pratiques suivantes :

- **Parlez à vos utilisateurs** : identifiez vos plus grands utilisateurs de fonctionnalités de collaboration et rencontrez-les pour comprendre leurs principales exigences métier et leurs scénarios de cas d’utilisation.

- **Équilibrer les risques et les avantages** : passez en revue vos besoins métier, réglementaires, juridiques et de conformité et planifiez une solution qui optimise tous les résultats.

- **Adaptez-vous à différentes organisations et différents types de contenu et de scénarios** : prenez en compte les différents besoins pour différents groupes ou services et différents types de contenu, tels que le contenu intranet par rapport au contenu OneDrive d’un utilisateur.

- **Aligner sur les priorités métier : les** objectifs métier vous aideront à définir le temps et l’énergie dont vous avez besoin pour investir dans la gouvernance.

- **Incorporez les décisions de gouvernance directement dans les solutions que vous créez** : de nombreuses décisions de gouvernance peuvent être implémentées en activant ou en désactivant les fonctionnalités dans Microsoft 365.


- **Utilisez une approche progressive : commencez** par déployer les fonctionnalités de collaboration sur un petit groupe d’utilisateurs. Obtenez des commentaires de leur part, recherchez des tickets de support technique et mettez à jour les paramètres ou processus nécessaires avant de passer à un groupe plus important.

- **Renforcer avec la formation** : adaptez des solutions telles que [Microsoft 365 parcours d’apprentissage](/office365/customlearning) pour vous assurer que les attentes spécifiques à votre organisation sont renforcées par une formation fournie par Microsoft.

- **Disposer d’une stratégie de communication des stratégies et des instructions de gouvernance au sein de votre organisation** : créez un centre d’adoption Microsoft 365 dans un site de communication SharePoint pour communiquer les stratégies et procédures.

- **Définissez les rôles et les responsabilités** : identifiez votre équipe principale de gouvernance et travaillez d’abord sur les décisions de gouvernance clés relatives à l’approvisionnement, au nommage et à l’accès externe, puis aux décisions restantes.

- **Réexaminez vos décisions à mesure que l’entreprise et la technologie évoluent** . Rencontrez-vous régulièrement pour passer en revue les nouvelles fonctionnalités et les nouvelles attentes de l’entreprise.

Pour en savoir plus sur ces pratiques, consultez [Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md).

## <a name="end-user-impact-and-change-management"></a>Impact de l’utilisateur final et gestion des modifications

Étant donné que les groupes et les équipes peuvent être créés de plusieurs façons, nous vous recommandons d’entraîner vos utilisateurs à utiliser la méthode qui convient le mieux à votre organisation :

- Si votre organisation effectue la plupart de ses communications à l’aide de l’e-mail, demandez à vos utilisateurs de créer des groupes dans Outlook.
- Si votre organisation utilise fortement SharePoint ou migre à partir d’SharePoint localement, demandez à vos utilisateurs de créer SharePoint sites d’équipe pour la collaboration.
- Si votre organisation a déployé Teams, demandez à vos utilisateurs de créer une équipe lorsqu’ils ont besoin d’un espace de collaboration.

Cela permet d’éviter toute confusion si les utilisateurs ne sont pas familiarisés avec la façon dont les groupes sont liés à leurs services associés. Pour plus d’informations sur la façon de parler à vos utilisateurs des groupes, consultez [Expliquer Groupes Microsoft 365 à vos utilisateurs](../admin/create-groups/explain-groups-knowledge-worker.md).

## <a name="key-collaboration-governance-capabilities-and-licensing-requirements"></a>Principales fonctionnalités de gouvernance de la collaboration et exigences en matière de licences

Les fonctionnalités de gouvernance pour la collaboration dans Microsoft 365 incluent des fonctionnalités dans Microsoft 365, Teams, SharePoint et Azure Active Directory.

| Fonctionnalité | Description | Licence |
|:----------------------|:------------|:----------|
|Partage d’équipe et de site|Contrôlez si les équipes, les groupes et les sites peuvent être partagés avec des personnes extérieures à votre organisation.|Microsoft 365 E5 ou E3|
|Autorisation/bloc de domaine|Limitez le partage avec des personnes extérieures à votre organisation à des personnes provenant de domaines spécifiques.|Microsoft 365 E5 ou E3|
|Création de sites libre-service|Autoriser ou empêcher les utilisateurs de créer leurs propres sites SharePoint.|Microsoft 365 E5 ou E3|
|Partage de sites et de fichiers restreint|Limitez le partage de sites, de fichiers et de dossiers aux membres d’un groupe de sécurité spécifique.|Microsoft 365 E5 ou E3|
|Création de groupe restreinte|Limitez la création d’équipe et de groupe aux membres d’un groupe de sécurité spécifique.|Microsoft 365 E5 ou E3 avec des licences EDU de base Azure AD Premium ou Azure AD|
|Stratégie de noms de groupes|Appliquez des préfixes ou des suffixes sur les noms de groupe et d’équipe.|Microsoft 365 E5 ou E3 avec des licences EDU de base Azure AD Premium ou Azure AD|
|Stratégie d’expiration de groupe|Définissez les groupes inactifs et les équipes pour qu’ils expirent et soient supprimés après une période spécifiée.|Microsoft 365 E5 ou E3 avec des licences Azure AD Premium|
|Accès invité par groupe|Autorisez ou empêchez le partage d’équipe et de groupe avec des personnes extérieures à votre organisation par groupe.|Microsoft 365 E5 ou E3|

## <a name="collaboration-governance-planning-recommendations"></a>Recommandations en matière de planification de la gouvernance de collaboration

Suivez les étapes de base suivantes pour créer votre plan de gouvernance :

1. Prenez en compte les principaux objectifs et processus métier : [créez votre plan de gouvernance](collaboration-governance-first.md) pour répondre aux besoins de votre entreprise.
2. Comprendre les paramètres dans les services : [les paramètres dans les groupes et les SharePoint](groups-sharepoint-governance.md) interagir entre eux, tout comme [les paramètres dans les groupes, les SharePoint et les Teams](groups-sharepoint-teams-governance.md) et [d’autres services](groups-services-interactions.md). N’oubliez pas de comprendre ces interactions lorsque vous planifiez votre stratégie de gouvernance.
3. Planifier la gestion de l’accès utilisateur : planifiez [le niveau d’accès que vous souhaitez accorder aux utilisateurs dans des groupes, des SharePoint et des Teams](groups-teams-access-governance.md).
4. Planifier la gestion des paramètres de conformité : passez en revue les options de conformité disponibles [pour Microsoft 365 groupes, Teams et SharePoint collaboration](groups-teams-compliance-governance.md).
5. Planifier la gestion des communications : passez en revue les [options de gouvernance des communications disponibles pour les scénarios de collaboration](groups-teams-communication-governance.md).
6. Planifier la gouvernance de l’organisation et du cycle de vie : choisissez [les stratégies que vous souhaitez utiliser pour la création de groupes et d’équipes, le nommage, l’expiration et l’archivage](plan-organization-lifecycle-governance.md). Comprenez également les [options de fin de cycle de vie pour les groupes, les équipes et les Yammer](end-life-cycle-groups-teams-sites-yammer.md)

![Illustration des étapes de gouvernance recommandées.](../media/collaboration-governance-steps.png)

## <a name="training-for-administrators"></a>Formation pour les administrateurs

Ces modules de formation de Microsoft Learn peuvent vous aider à découvrir les fonctionnalités de gouvernance dans Microsoft 365.

#### <a name="information-protection"></a>Protection des informations

|Formation :|Gérer la protection et gouvernance des informations|
|:---|:---|
|![Icône d’entraînement de la protection des informations.](../media/information-protection-governance.svg)|La quantité de données générées aujourd’hui croît plus rapidement que jamais, les employés souhaitent travailler partout et le paysage réglementaire évolue en permanence. Les solutions de Microsoft pour la protection et la gouvernance des informations aident les organisations à obtenir le bon équilibre entre la protection de leurs données et la productivité de leurs employés. Cette rubrique d’apprentissage peut vous aider à vous préparer aux certifications Certification Microsoft 365 : Administrateur de sécurité associé et Certification Microsoft 365 : Administration entreprise expert.<br><br>5 h 13 min - chemin Learning - 7 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/m365-compliance-information-governance/introduction/)

<br><br>

|Formation :|Protéger les informations d’entreprise avec Microsoft 365|
|:---|:---|
|![Teams icône d’entraînement.](../media/protect-enterprise-information-microsoft-365.svg)|La protection et la sécurisation des informations de votre organisation sont plus exigeantes que jamais. Le chemin d'accès de l’apprentissage Protéger une entreprise à l’aide de Microsoft 365 explique comment protéger vos informations sensibles contre tout partage excessif accidentel ou utilisation incorrecte, comment découvrir et classifier des données, comment les protéger à l’aide d’étiquettes de confidentialité, et comment surveiller et analyser vos informations sensibles pour prévenir leurs perte.<br><br>1 heure - chemin d’accès Learning - 5 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/m365-security-info-overview/introduction/)

#### <a name="security-and-compliance"></a>Sécurité et conformité

|Formation :|Faire preuve de connaissances fondamentales des fonctionnalités de sécurité et de conformité Microsoft 365|
|:---|:---|
|![Icône d’apprentissage de la sécurité et de la conformité.](../media/microsoft-365-security-and-compliance-capabilities.svg)|Découvrez les domaines des solutions de sécurité et de conformité Microsoft 365 et les fonctionnalités disponibles pour aider les entreprises à sécuriser leur entreprise et à respecter les obligations réglementaires. Si vous n’êtes pas familiarisé avec les concepts de base du cloud computing, nous vous recommandons de suivre [les concepts cloud - Principes du cloud computing](/learn/modules/principles-cloud-computing/index).<br><br>3 h 11 min - chemin Learning - 8 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/what-is-m365/1-introduction/)

## <a name="illustrations"></a>Illustrations

Ces illustrations vous aideront à comprendre comment les groupes et les équipes interagissent avec d’autres services dans Microsoft 365 et les fonctionnalités de gouvernance et de conformité disponibles pour vous aider à gérer ces services au sein de votre organisation.

### <a name="groups-in-microsoft-365-for-it-architects"></a>Groupes dans Microsoft 365 pour les architectes informatique
Quels sont les besoins des architectes informatique concernant les groupes dans Microsoft 365

|**Item**|**Description**|
|:-----|:-----|
|[![Image miniature pour l’infographie des groupes.](../downloads/msft-m365-groups-architecture-thumb.png)](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf) <br/> [PDF](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf) \| [Visio](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.vsdx) <br> Mise à jour de mai 2022|Ces illustrations décrivent les différents types de groupes, la manière dont ceux-ci sont créés et gérés et quelques recommandations en matière de gouvernance.|

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams et services de productivité connexes dans Microsoft 365 pour les architectes informatique
L’architecture logique de services de productivité dans Microsoft 365, fonctionnant avec Microsoft Teams.

|**Item**|**Description**|
|:-----|:-----|
|[![Image miniature pour Teams affiche d’architecture logique.](../downloads/msft-teams-logical-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)  <br>Mise à jour d’avril 2019   |Microsoft fournit une suite de services de productivité qui fonctionnent ensemble pour fournir une expérience de collaboration avec la gouvernance des données, la sécurité et la conformité. <br/> <br/>Cette série d’illustrations fournit une visibilité de l’architecture logique de services de productivité pour les architectes d’entreprise, fonctionnant avec Microsoft Teams.|

### <a name="microsoft-365-information-protection-and-compliance-capabilities"></a>Microsoft 365 fonctionnalités de protection et de conformité des informations

Microsoft 365 comprend un large éventail de fonctionnalités de protection et de conformité des informations. Avec les outils de productivité de Microsoft, ces fonctionnalités sont conçues pour aider les organisations à collaborer en temps réel tout en respectant des frameworks de conformité réglementaire stricts. 

Cet ensemble d’illustrations utilise l’une des industries les plus réglementées, les services financiers, pour montrer comment ces fonctionnalités peuvent être appliquées pour répondre aux exigences réglementaires courantes. N’hésitez pas à les adapter à votre usage personnel. 


| Élément | Description |
|:-----|:-----|
|[![Affiche du modèle : Fonctionnalités de protection et de conformité des informations Microsoft Purview.](../media/solutions-architecture-center/m365-compliance-illustrations-thumb.png)](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf) <br/> Anglais : [Télécharger au format PDF](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf)  \| [Télécharger en tant que Visio](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.vsdx) <br/> Japonais : [Télécharger au format PDF](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.pdf)  \| [Télécharger en tant que Visio](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.vsdx) <br/> Mise à jour : novembre 2020|Inclus : <ul><li>  Microsoft Purview Information Protection et Microsoft Purview Data Loss Prevention</li><li>Stratégies de rétention et étiquettes de rétention </li><li>Obstacles aux informations</li><li>Conformité des communications</li><li>Gestion des risques internes</li><li>Réception de données tierces</li>|

## <a name="conference-sessions"></a>Sessions de conférence

Regardez ces sessions de conférence pour en savoir plus sur la gouvernance des Groupes Microsoft 365 et des Teams.

**Principes fondamentaux**

Découvrez les principes de base et les nouvelles innovations de Groupes Microsoft 365, notamment la gestion et la gouvernance à grande échelle, les meilleures pratiques pour favoriser l’utilisation et l’adoption, et le libre-service.

- [Adopter Groupes Microsoft 365](https://www.youtube.com/watch?v=dAamBF1gb7M)

**Governance**

Découvrez comment configurer le cycle de vie d’expiration de vos groupes, les stratégies de nommage, les étiquettes de classification, la collaboration avec des invités externes et gérer les autorisations de création de groupe.

- [Transformer la collaboration et lutter contre l’informatique fantôme avec des groupes Office 365](https://www.youtube.com/watch?v=Bhf_bKx3lAg)

**Exemple de client**

Consultez un exemple en arrière-plan de la façon dont les Groupes Microsoft 365, les SharePoint, les Teams et les Yammer fonctionnent ensemble pour fournir une plateforme de collaboration mondiale.

- [Trouver votre point de collaboration avec Groupes Microsoft 365, SharePoint, Teams et Yammer](https://www.youtube.com/watch?v=Rx9eVwqXeQk)

## <a name="see-also"></a>Voir aussi

[Documentation de sécurité Office 365](../security/index.yml)

[Documentation Microsoft Purview](../compliance/index.yml)
