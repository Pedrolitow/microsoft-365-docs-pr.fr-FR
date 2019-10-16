---
title: Déploiement de Microsoft Teams pour Microsoft 365 Entreprise
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/14/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-collaboration
- Strat_O365_Enterprise
ms.custom: ''
description: Découvrez comment déployer Microsoft Teams au sein de votre organisation.
ms.openlocfilehash: 2e34c4fcada0f80c597faf89b221321ffa9183ba
ms.sourcegitcommit: 31392b9599f4b4e9981a1278d6beb9f0a2839ecf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "37503390"
---
# <a name="deploy-microsoft-teams-for-microsoft-365-enterprise"></a>Déploiement de Microsoft Teams pour Microsoft 365 Entreprise

*Cette charge de travail est incluse dans les versions E3 et E5 de Microsoft 365 Entreprise*

Microsoft Teams réunit la conversation instantanée, les conférences, le partage de documents et les conversations thématiques de façon à simplifier la création et le partage de contenu au sein de groupes. Microsoft Teams vous permet de travailler en équipe et de collaborer pour Microsoft 365 Entreprise, et constitue un élément clé de la valeur Built for Teamwork de Microsoft 365. 

Si vous êtes novice sur Teams, voir [Bienvenue sur Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview). 


## <a name="roll-out-teams-to-your-organization"></a>Déploiement de Teams dans votre organisation

Avant de commencer :

- Vérifiez que vous avez configuré les phases d’[infrastructure de base](deploy-foundation-infrastructure.md) appropriées pour que vos équipes disposent des comptes utilisateur et des fonctionnalités de sécurité nécessaires. Les phases d’identité et de protection des informations sont les plus importantes pour la connexion et l’utilisation de la sécurisation de la messagerie et des fichiers avec les étiquettes de rétention et de confidentialité.
- En savoir plus sur la sécurité et la conformité dans Teams avec [cet article](https://docs.microsoft.com/microsoftteams/security-compliance-overview).
- En savoir plus sur la gestion des licences Office 365 pour Teams avec [cet article](https://docs.microsoft.com/microsoftteams/office-365-licensing).

Pour déployer Teams au sein de votre organisation, consultez [Comment déployer Teams](https://docs.microsoft.com/microsoftteams/how-to-roll-out-teams).

Pour vos premières fonctionnalités Teams, voir [Conversation, équipes, canaux et applications dans Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/deploy-chat-teams-channels-microsoft-teams-landing-page).

Pour accéder à des fonctionnalités plus avancées de Teams, voir :

- [Réunions et conférence](https://docs.microsoft.com/microsoftteams/deploy-meetings-microsoft-teams-landing-page)
- [Voix Cloud](https://docs.microsoft.com/microsoftteams/cloud-voice-landing-page) (nécessite Microsoft 365 Entreprise E5)

Pour surveiller l’utilisation de Teams dans votre organisation, voir :

- [Analyses inter-équipes et par équipe dans Teams](https://docs.microsoft.com/microsoftteams/teams-analytics-and-reports/cross-team-per-team-analytics)
- [Analyses et rapports](https://docs.microsoft.com/microsoftteams/teams-analytics-and-reports/teams-reporting-reference)


## <a name="upgrade-to-teams"></a>Mise à niveau vers Teams

Si ce n’est pas déjà fait, vous devrez bientôt effectuer la mise à niveau de Skype Entreprise vers Microsoft Teams. Que vous débutiez avec Teams, que vous utilisiez déjà Teams en parallèle de Skype Entreprise, ou que vous soyez prêt à procéder à la mise à niveau, nous voulons nous assurer que vous disposez de tout ce dont vous avez besoin pour migrer efficacement vers Teams.

Que vous procédiez à une mise à niveau à partir de Skype Entreprise Online ou à partir d’un environnement local Skype Entreprise vers Teams, l’infrastructure de mise à niveau vous guidera tout au long du processus en fonction de votre situation.
 
Voir [Prise en main de votre mise à niveau de Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/upgrade-start-here) pour plus d’informations.

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Pour bénéficier d’un aperçu des coulisses de Microsoft et découvrir comment nous avons déployé et utilisé Teams pour booster la collaboration, consultez les ressources suivantes :

- [La stratégie d’adoption de Microsoft Teams prépare les employés à une nouvelle culture de travail](https://www.microsoft.com/fr-FR/itshowcase/microsoft-teams-adoption-strategy-prepares-employees-for-a-new-culture-of-work)
- [Avec les salles Microsoft Teams, découvrez une expérience de réunion moderne et adaptable à l’échelle mondiale](https://www.microsoft.com/fr-FR/itshowcase/with-microsoft-teams-rooms-comes-a-globally-scalable-modern-meeting-experience)

## <a name="next-steps"></a>Étapes suivantes

- [Gérer les paramètres de Microsoft Teams pour votre organisation](https://docs.microsoft.com/microsoftteams/enable-features-office-365)
- [Formation à Microsoft Teams pour les administrateurs](https://docs.microsoft.com/microsoftteams/itadmin-readiness)

<!--

## Phase 1: Envision

In this phase, you gather the people for your Teams deployment and determine how your organization will use Teams to address its business needs.

### Step 1: Gather your Teams deployment members

For a successful deployment of Teams on top of the Microsoft 365 [foundation infrastructure](deploy-foundation-infrastructure.md), you need to get the right people for input and feedback. Key people include business decision makers, IT staff such as architects and implementers, and advocates for your end users. 

These three groups ensure that your Teams deployment includes considerations that address business needs, technical aspects of licensing and security, and that Teams is something that your typical users will use.

#### Result

A list of people that represent the business, technical, and end user perspectives of your organization.

### Step 2: Determine and prioritize your Teams business scenarios
Teams can be used for many different purposes. You need to figure out which purposes map to your business needs on the separate levels of your organization, your business groups, your departments, and individual working and project teams. Take a look at the [Microsoft 365 Productivity Library](https://www.microsoft.com/microsoft-365/success/?rtc=1) for examples to help you define Teams scenarios. 

You should target Teams to address fast-moving and highly collaborative teams that work closely together and require many more facilities than just email with Exchange Online can provide. Examples are live group chats with a recorded history and a common and easy-to-find place to store files and notes. 

One way to see the benefits of Teams is to examine how a team or v-team interacts today, and then find an appropriate Teams scenario that replaces the interaction and provides easier ways to collaborate and provide additional capabilities.

#### Microsoft Teams for highly regulated data

Highly regulated data is subject to regional regulations or is the most valuable data for your organization, such as trade secrets, financial or human resources information, and organization strategy. You can configure a team for restricted access, data classification, data loss prevention, and encryption for this type of data. For the details, see [Microsoft Teams and SharePoint Online sites for highly regulated data](teams-sharepoint-online-sites-highly-regulated-data.md).

#### Result

A list of Teams scenarios that address your organization’s needs for collaboration and teamwork.

## Phase 2: Onboard

In this phase, you plan for the technical aspects of a Teams deployment and start rolling out Teams to selected groups of users.

### Prerequisites: Identity and device access configuration

To protect access to teams, ensure that you have configured [identity and device access policies](identity-access-policies.md) and the [recommended SharePoint Online access policies](sharepoint-file-access-policies.md).

### Step 1: Complete your technical planning

Before you begin technical planning, determine whether you want to use FastTrack. If your organization has over 50 seats and is participating in an [eligible plan](https://docs.microsoft.com/fasttrack/O365-fasttrack-benefit-for-office-365, you can use [FastTrack for Microsoft 365](https://fasttrack.microsoft.com/microsoft365), *available at no additional cost* to guide you through planning, deployment and service adoption. Or, you can complete this work yourself using our FastTrack Onboarding Wizards, which are available from [FastTrack](https://fasttrack.microsoft.com/) once you sign in with your Microsoft 365 account.

If you are doing your own planning (or in conjunction with FastTrack), you need to determine if your network and organization are ready for Teams. It is especially important that you meet the exit criteria for [networking](networking-infrastructure.md) in your foundation infrastructure for users connected to your organization network. Pay special attention to bandwidth, throughput, and traffic delays to maximize performance for Teams-based meetings.

Use these resources to prepare the technical aspects of your organization for a Teams rollout: 

- [Check your environment's readiness for Teams](https://docs.microsoft.com/MicrosoftTeams/environment-readiness)
- [Prepare your network for Teams](https://docs.microsoft.com/MicrosoftTeams/prepare-network)
- [Office 365 URLs and IP address ranges](https://docs.microsoft.com/MicrosoftTeams/office-365-urls-ip-address-ranges)

For a better understanding of security in Teams, review the following additional resources:

- [Overview of security and compliance in Teams](https://docs.microsoft.com/MicrosoftTeams/security-compliance-overview)
- [Office 365 groups and Teams](https://docs.microsoft.com/MicrosoftTeams/office-365-groups)
- [Guest access in Teams](https://docs.microsoft.com/microsoftteams/guest-access)

Next, use these resources to understand Teams licensing and to perform the setup of Teams for your organization:

- [Office 365 licensing for Teams](https://docs.microsoft.com/MicrosoftTeams/office-365-licensing)
- [Manage user access to Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/user-access)
- [Get clients for Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/get-clients)
- [Turn on Microsoft Teams in your organization](https://docs.microsoft.com/MicrosoftTeams/office-365-set-up)
- [Manage Microsoft Teams features for your organization](https://docs.microsoft.com/MicrosoftTeams/enable-features-office-365)

#### Result

Your network, security, and Microsoft 365 licensing planning are done and you are ready to begin rolling out Teams to selected groups in your organization.

### Step 2: Run an IT pilot

In most medium-sized and large organizations, you should run an IT pilot with your stakeholders from Phase 1, early adopters, and technical enthusiasts. During the IT pilot:

- Choose a Teams business scenario in which your IT pilot participants can practice. See the [Microsoft Teams getting started kit](http://microsoft.com/download/56505) for ideas.
- Give your pilot participants a set of exercises to test Teams-based chats, meetings, file storage, meetings, and other capabilities.
- Determine your change management strategy and produce materials to drive organization-wide user adoption. 

  Change management materials can include email announcement text, internal training plans, hallway posters, and presentations. These materials will inform your organization about Teams and its benefits with the goals of raising awareness and driving usage. See [change management strategy for Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/change-management-strategy) for some ideas.

- Have your IT pilot participants review the change management strategy materials based on their experiences. They can provide tips on best practices and advice on how to best describe the benefits of Teams and how to use it for collaboration.

#### Result

Your Teams IT pilot is complete and the initial change management materials have been developed, reviewed, and refined.

### Step 3: Roll out to a business group

After completing your IT pilot, roll out Teams to a business group or department in your organization. This rollout should include:

- Identification of key business scenarios for Teams within the business group.
- Announcement activities to inform users of the expectations and timelines for Teams usage for departmental, work, or project teams.
- Delivery of [user training on Teams](https://docs.microsoft.com/microsoftteams/training-microsoft-teams-landing-page) or links to resources to introduce Teams and how to use it.
- A feedback mechanism, such as a central team containing everyone in the business group, to collect comments and issues from users in the business group.

During the rollout, you can refine your change management materials in preparation for the organization-wide rollout.

#### Result

A business group is up and running with Teams and the change management materials have been tested and refined.

## Phase 3: Drive value

In this phase, you complete the rollout of Teams to your organization and support your users so that they are realizing its benefits.

### Step 1: Roll out Teams to the rest of your organization

After completing your rollout to a targeted business group, roll out Teams to the rest of your organization. This rollout should include:

- Identification of key business scenarios for Teams within your separate business groups.
- Use of your refined change management materials for announcement activities to inform your organization of the expectations and timelines for Teams usage for departmental, work, or project teams.
- Delivery of [user training on Teams](https://docs.microsoft.com/microsoftteams/training-microsoft-teams-landing-page) or links to resources to introduce Teams and how to use it.
- A feedback mechanism, such as a central team containing everyone, to collect comments and act on issues from organization users. If your organization has less than 2500 individuals, use a public team or channel in Teams. Otherwise, use a public group in Yammer.

#### Result

Your organization is up and running and your change management strategy is in place to inform, train, and enable users to begin using Teams.

### Step 2: Measure usage, manage satisfaction, and drive adoption

After rolling out Teams to your entire organization, you must continue to employ your change management strategy to:

- Have your leadership promote Teams as the teamwork and collaboration tool for the organization.
- Encourage individuals to use it for business group, departmental, work, and project team communications and collaboration.

Here are some suggested activities:

- See [Success factors for Office 365](https://aka.ms/successfactors) to learn about general best practices for cloud service adoption. 
- See [Office 365 activity reports](https://support.office.com/article/Activity-Reports-in-the-Office-365-admin-center-0d6dfb17-8582-4172-a9a9-aed798150263) to understand Office 365 service usage across your organization. If you aren’t an Office 365 global admin for your organization, ask someone who is to grant your user account Reports Reader permissions so you can access activity reports.
- Monitor your feedback venue (a public channel in a central team or a public Yammer group) for issues and feedback from individuals about their experiences with Teams. Address questions and issues as quickly as you can to prevent frustration and abandonment of Teams by individuals.
- Identify and nurture your champions in each business group and highlight their accomplishments and best practices using Teams. Reflect their successes out to the organization to show project success and adoption. Endorsement by technical leaders within a business group can exert a powerful influence over leaders and peers.

#### Result

Your organization has adopted Teams as its collaboration and teamwork tool.


--> 
