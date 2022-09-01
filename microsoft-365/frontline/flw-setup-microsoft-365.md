---
title: Configurer Microsoft 365 pour les travailleurs de première ligne
author: samanro
ms.author: samanro
ms.reviewer: samanro
manager: pamgreen
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez comment configurer Microsoft 365 avec les services et fonctionnalités dont vous avez besoin pour vos employés de première ligne.
ms.localizationpriority: high
ms.collection:
- m365-frontline
- m365solution-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: ad81e7f7f04247be406d77cc54f8d31bd44c187f
ms.sourcegitcommit: ecc04b5b8f84b34255a2d5e90b5ab596af0d16c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67497624"
---
# <a name="set-up-microsoft-365-for-frontline-workers"></a>Configurer Microsoft 365 pour les travailleurs de première ligne

Pour configurer Microsoft 365 pour les employés de première ligne, suivez ce processus global :

1. **[Identifiez vos scénarios](#step-1-identify-your-scenarios)** : quels scénarios souhaitez-vous implémenter pour vos employés de première ligne ? Une fois que vous avez déterminé les scénarios souhaités, utilisez le tableau ci-dessous pour identifier les applications et services requis pour chaque scénario que vous souhaitez implémenter.
1. **[Configurer votre environnement et la base de Microsoft 365](#step-2-set-up-your-environment-and-core-microsoft-365)** : suivez les guides d’installation dans le Centre d'administration Microsoft 365 pour configurer Microsoft 365. Continuez à lire pour découvrir comment accéder à ces guides.
1. **[Configurer Microsoft Teams](#step-3-set-up-microsoft-teams)** : utilisez l’Assistant Intégration ou le processus Déployer des équipes à grande échelle pour configurer le service et créer vos équipes.
1. **[Configurez tous les autres services nécessaires à votre scénario](#step-4-set-up-other-services)** : suivez les instructions des sections ci-dessous pour configurer ces services.
1. **[Configurer des applications](#step-5-configure-apps-for-your-scenario)** : une fois que tout est configuré et configuré dans le Centre d’administration, vous pouvez suivre les instructions de vos scénarios pour configurer davantage les applications dont vous avez besoin pour chaque scénario.
1. **[Appareils](#step-6-set-up-devices)** : configurez des appareils partagés et personnels pour qu’ils fonctionnent avec Microsoft 365 et Microsoft Teams et pour permettre à vos employés de première ligne de communiquer plus en toute sécurité au sein de votre organisation.

:::image type="content" source="media/m365-frontline-setup-steps.png" alt-text="Étapes de configuration des Microsoft 365 pour les travailleurs de première ligne." lightbox="media/m365-frontline-setup-steps.png":::

## <a name="step-1-identify-your-scenarios"></a>Étape 1 : Identifiez vos scénarios

Le tableau suivant répertorie les scénarios de vos employés de première ligne. Vous pouvez lire un résumé de chaque scénario dans [choisir vos scénarios](flw-choose-scenarios.md) et déterminer exactement ce que vous devez configurer en suivant les liens vers chaque scénario et vers chaque application ou service requis.

| Scénario | Services nécessaires |
|  ------- | -------  |
| [Communication et collaboration en équipe](flw-team-collaboration.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[Email avec Exchange Online](#set-up-email-with-exchange-online) |
| [Communications d’entreprise](flw-corp-comms.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[SharePoint](#set-up-sites-with-sharepoint-in-microsoft-365) <br>[Connexions Microsoft Viva](#set-up-viva-connections) <br>[Yammer](#set-up-your-organizations-social-network-with-yammer) |
| [Rendez-vous virtuels](virtual-appointments.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) |
| [Impliquez vos employés et concentrez-vous sur le bien-être des employés](flw-wellbeing-engagement.md)| [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[SharePoint](#set-up-sites-with-sharepoint-in-microsoft-365) <br>[Connexions Microsoft Viva](#set-up-viva-connections) <br>[Yammer](#set-up-your-organizations-social-network-with-yammer) |
| [Planifier votre équipe avec Shifts](shifts-for-teams-landing-page.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) |
| [Intégrer de nouveaux employés dans votre organisation](/sharepoint/onboard-employees)| [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[SharePoint](#set-up-sites-with-sharepoint-in-microsoft-365) <br>[Connexions Microsoft Viva](#set-up-viva-connections) <br>[Viva Learning](#set-up-viva-learning)|
| [Formation continue](flw-onboarding-training.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[Viva Learning](#set-up-viva-learning) |
| [Simplifiez les processus d’entreprise](simplify-business-processes.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[Power Apps, Power Automate et Power BI](#set-up-power-apps-power-automate-and-power-bi) |

Certains services sont inclus uniquement avec des licences F3, telles que la messagerie électronique et le Power Platform. Consultez [Comprendre les types d’utilisateurs worker de première ligne et les licences](flw-licensing-options.md) pour déterminer le type de licences dont vous aurez besoin pour vos utilisateurs.

## <a name="step-2-set-up-your-environment-and-core-microsoft-365"></a>Étape 2 : Configurer votre environnement et le cœur de Microsoft 365

Le Centre d’administration Microsoft 365 propose un ensemble de [guides d’installation](/microsoft-365/enterprise/setup-guides-for-microsoft-365) qui vous guident tout au long des étapes de configuration des produits, des fonctionnalités de sécurité et des outils de collaboration dans Microsoft 365. Les guides d’installation sont accessibles à partir de la [page d’aide à l’installation](https://aka.ms/setupguidance) dans le Centre d'administration Microsoft 365.

1. Utilisez le guide [Préparer votre environnement](https://aka.ms/prepareyourenvironment) pour préparer l’environnement de votre organisation pour les services Microsoft 365 et Office 365.
1. Utilisez le guide [d’installation de Microsoft 365](https://aka.ms/microsoft365setupguide) pour configurer des outils de productivité, des stratégies de sécurité et des fonctionnalités de gestion des appareils. Vous pouvez également utiliser ce conseiller pour configurer et configurer les appareils de votre organisation.

## <a name="step-3-set-up-microsoft-teams"></a>Étape 3 : Configurer Microsoft Teams

Pour un projet pilote, vous pouvez utiliser l’Assistant Intégration de worker de première ligne pour configurer une seule équipe, configurée pour vos employés de première ligne. Pour obtenir des conseils pas à pas, consultez [l’Assistant Intégration des employés de première ligne pour mettre votre personnel de première ligne opérationnel](flw-onboarding-wizard.md).

Pour les déploiements complets, suivez les instructions de [Deploy Teams à grande échelle pour les employés de première ligne](deploy-teams-at-scale.md).

## <a name="step-4-set-up-other-services"></a>Étape 4 : Configurer d’autres services

### <a name="set-up-email-with-exchange-online"></a>Installer l'e-mail avec échange en ligne

Si vous souhaitez que vos responsables et employés de première ligne aient accès à la messagerie électronique, vous devez configurer le courrier électronique dans Microsoft 365. Les utilisateurs doivent disposer d’une licence F3 pour accéder à l’e-mail. Suivez le [guide d’installation Email](https://aka.ms/office365setup) pour le configurer.

Notez que vos utilisateurs peuvent également installer l’application Outlook à utiliser pour leur courrier électronique. Vous devez donc vous assurer de partager l’emplacement de téléchargement de l’application Outlook avec eux.

### <a name="set-up-sites-with-sharepoint-in-microsoft-365"></a>Configurer des sites avec SharePoint dans Microsoft 365

[SharePoint](/sharepoint/sharepoint-online) vous permet de partager des documents et de créer des sites. Utilisez le [guide d’installation de SharePoint](https://aka.ms/spoguidance) dans le Centre d'administration Microsoft 365 pour le configurer.

### <a name="set-up-employee-experiences-with-viva-modules"></a>Configurer les expériences des employés avec les modules Viva

[Microsoft Viva](/viva/microsoft-viva-overview) permet de connecter les employés à une expérience d’employé intégrée qui regroupe les communications, les connaissances, l’apprentissage, les ressources et les insights dans le flux de travail. Microsoft Viva propose plusieurs modules qui peuvent être utilisés avec Microsoft Teams pour créer des expériences d’employés.

#### <a name="set-up-viva-connections"></a>Configurer les connexions Viva pour bureau

Utilisez [Viva Connections](/viva/connections/viva-connections-overview) pour créer un tableau de bord qui vous aide à impliquer et à informer vos employés de première ligne. Viva Connections est une application personnalisable dans Microsoft Teams qui offre à chacun une destination personnalisée pour découvrir des nouvelles pertinentes, des conversations et les outils dont ils ont besoin pour réussir. 

Suivez le [guide de configuration de l’expérience de génération de votre employé](https://aka.ms/EmployeeExperienceDashboard) pour le configurer. En savoir plus sur la [configuration des connexions Viva](/viva/connections/guide-to-setting-up-viva-connections).

#### <a name="set-up-viva-learning"></a>Configurer Viva Learning

[Viva Learning](/viva/learning/) est une application de Microsoft Teams qui permet aux employés de faire de l’apprentissage une partie naturelle de la journée en intégrant l’apprentissage dans le flux de travail au sein des outils et plateformes qu’ils utilisent déjà. Consultez [Configurer Microsoft Viva Learning dans le Centre d’administration Teams](/viva/learning/set-up-viva-learning) pour savoir comment configurer Viva Learning.

### <a name="set-up-your-organizations-social-network-with-yammer"></a>Configurer le réseau social de votre organisation avec Yammer

[Yammer](/yammer) vous aide à connecter votre personnel au sein de votre entreprise. Utilisez le [conseiller de déploiement Yammer](https://aka.ms/yammerdeploymentguide) pour le configurer.

### <a name="set-up-power-apps-power-automate-and-power-bi"></a>Configurer Power Apps, Power Automate et Power BI

Vous pouvez utiliser toutes ces applications dans Microsoft Teams. Pour plus d'informations sur la manière de les configurer, voir :

- Informations complémentaires : [Power Apps et Intégration de Power Apps et Microsoft Teams](/powerapps/teams/overview).
- [Power Automate : utiliser des flux dans Microsoft Teams](/power-automate/teams/overview)
- Informations complémentaires : [Collaborer dans Microsoft Teams avec Power BI](/power-bi/collaborate-share/service-collaborate-microsoft-teams).
- ‎[Capture d’écran d’utilisation de Power Virtual Agents dans Microsoft Teams](/power-virtual-agents/teams/fundamentals-what-is-power-virtual-agents-teams)
- [Power Apps](/microsoftteams/manage-power-platform-apps)

## <a name="step-5-configure-apps-for-your-scenario"></a>Étape 5 : Configurer des applications pour votre scénario

Une fois que tout est configuré et configuré dans le Centre d’administration, vous pouvez suivre les instructions de vos scénarios pour configurer davantage les applications dont vous avez besoin pour chaque scénario.

Scénarios et applications

| Scénario | Approbations | Réservations | Listes | Compliment | Shifts | Tâches | Mises à jour |
| :---- | :----: | :----: | :----: | :----: | :----: | :----: | :----: |
| [Communication et collaboration en équipe](flw-team-collaboration.md) | &#x2705; | &nbsp; | &#x2705; | &#x2705; | &nbsp; | &#x2705; | &#x2705; |
| [Communications d’entreprise](flw-corp-comms.md) |  &nbsp; |  &nbsp; |  &nbsp; |  &nbsp; |  &nbsp; |  &nbsp; |  &nbsp; |
| [Rendez-vous virtuels avec Microsoft Teams et l’application Bookings](bookings-virtual-visits.md) |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; |  &nbsp;|  &nbsp; |
| Bien-être et engagement |  &nbsp; |  &nbsp; |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; |
| [Planifier votre équipe avec Shifts](shifts-for-teams-landing-page.md) |  &nbsp; | &nbsp; | &#x2705; |  &nbsp; | &#x2705; | &#x2705; | &#x2705; |
| [Formation : Intégrer de nouveaux employés](/sharepoint/onboard-employees) |  &nbsp; |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; | &#x2705; |
| Formation continue |  &nbsp; |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; | &#x2705; |
| [Simplifiez les processus d’entreprise](simplify-business-processes.md) | &#x2705; |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; | &#x2705; |
| Gérer les sites, les magasins et les projets | &#x2705; |  &nbsp; | &#x2705; |  &nbsp; | &nbsp; | &#x2705; | &#x2705; |

## <a name="step-6-set-up-devices"></a>Étape 6 : Configurer des appareils

Pour configurer des appareils partagés et personnels afin qu’ils fonctionnent avec Microsoft 365 et Microsoft Teams et pour permettre à vos employés de terrain de communiquer plus en toute sécurité au sein de votre organisation, consultez [Gérer les appareils mobiles pour les employés de première ligne](flw-devices.md).
