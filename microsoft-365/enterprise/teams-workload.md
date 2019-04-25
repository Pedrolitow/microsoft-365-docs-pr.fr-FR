---
title: Déploiement de Microsoft Teams pour Microsoft 365 Entreprise
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-collaboration
- Strat_O365_Enterprise
ms.custom: ''
description: Suivez le processus de planification, de déploiement et de création de valeur de Microsoft Teams dans Microsoft 365 Entreprise au sein de votre organisation.
ms.openlocfilehash: 646062babf525be176386264b4ef3c4a3a21647a
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32291658"
---
# <a name="deploy-microsoft-teams-for-microsoft-365-enterprise"></a>Déploiement de Microsoft Teams pour Microsoft 365 Entreprise

*Cette charge de travail est incluse dans les versions E3 et E5 de Microsoft 365 Entreprise*

Microsoft Teams réunit la conversation instantanée, les conférences, le partage de documents et les conversations thématiques de façon à simplifier la création et le partage de contenu au sein de groupes. Microsoft Teams vous permet de travailler en équipe et de collaborer pour Microsoft 365 Entreprise, et constitue un élément clé de la valeur Built for Teamwork de Microsoft 365. Si vous débutez avec Microsoft Teams, consultez l’article [Présentation de Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview).
 
Si vous utilisez actuellement Skype Entreprise, sachez que nous sommes en train de créer des fonctionnalités Skype Entreprise dans Microsoft Teams. Cela se fait petit à petit, mais Microsoft Teams deviendra à terme la seule expérience client. En tant que client important de Skype Entreprise, Microsoft est là pour vous aider. Consultez l’article [Transition de Skype Entreprise à Microsoft Teams](https://docs.microsoft.com/microsoftteams/journey-skypeforbusiness-teams) pour obtenir plus d’informations.

Les phases et les étapes suivantes vous permettent de comprendre le rôle de Microsoft Teams dans votre organisation, d’intégrer votre organisation à Microsoft Teams à travers une série de déploiements progressifs, et de sensibiliser vos utilisateurs finaux à l’utilisation de Microsoft Teams et de sa valeur. 

Avant de commencer, vérifiez que vous avez configuré les phases d’[infrastructure de base](deploy-foundation-infrastructure.md) appropriées pour que vos équipes disposent des fonctionnalités de sécurité nécessaires.

## <a name="phase-1-envision"></a>Phase 1 : Comprendre

Dans cette phase, vous allez rassembler les personnes pour effectuer votre déploiement de Microsoft Teams et déterminer comment votre organisation utilisera Microsoft Teams afin de traiter les besoins d’entreprise.

### <a name="step-1-gather-your-teams-deployment-members"></a>Étape 1 : rassembler les membres de votre déploiement Microsoft Teams
Pour un déploiement réussi de Microsoft Teams par-dessus l’[infrastructure de base](deploy-foundation-infrastructure.md) de Microsoft 365, vous devez rassembler les bonnes personnes en vue d’obtenir leurs commentaires et leurs réactions. Les personnes clés incluent les décideurs d’entreprise, le service informatique (architectes et implémenteurs), et les défenseurs de vos utilisateurs finaux. 

Ces trois groupes veillent à ce que votre déploiement de Microsoft Teams inclue des considérations qui répondent aux besoins professionnels, aux aspects techniques des licences et de sécurité, et à ce que Microsoft Teams soit utilisé par vos utilisateurs types.

#### <a name="result"></a>Résultat

Liste des personnes qui représentent les aspects professionnels, techniques et des utilisateurs finaux de votre organisation.

### <a name="step-2-determine-and-prioritize-your-teams-business-scenarios"></a>Étape 2 : déterminer et définir les priorités des scénarios d’entreprise Microsoft Teams
Microsoft Teams peut être utilisé pour de nombreux objectifs différents. Vous devez déterminer les objectifs qui correspondent à vos besoins professionnels à chacun des niveaux de votre organisation, de vos groupes d’entreprise, de vos services, ainsi qu’au travail individuel et aux équipes de projets. Consultez l’article [Bibliothèque de productivité Microsoft 365](https://www.microsoft.com/en-us/microsoft-365/success/?rtc=1) pour obtenir des exemples afin de vous aider à définir des scénarios Teams. 

Vous devez cibler Microsoft Teams pour traiter les équipes particulièrement collaboratives et à évolution rapide qui travaillent étroitement ensemble et nécessitent bien plus de fonctionnalités que ce que peut fournir la messagerie électronique avec Exchange Online. Il peut s’agir, par exemple, de conversations instantanées de groupes en direct avec un historique enregistré et un emplacement commun et facile à trouver pour stocker des fichiers et des notes. 

Pour se rendre compte des avantages de Microsoft Teams, observez la façon dont une équipe ou une équipe v interagit aujourd’hui, puis recherchez un scénario de Microsoft Teams approprié qui remplace l’interaction et offre des moyens plus faciles de collaborer et de fournir des fonctionnalités supplémentaires.

Microsoft Teams permet de mettre en place les scénarios d’entreprise stratégiques suivants pour Microsoft 365 Entreprise :

- Communiquer avec votre équipe afin de rester informé, de demander des informations et de créer une cohésion et un consensus
- Impliquer vos employés de terrain pour favoriser votre transformation numérique.
- Comprendre vos habitudes de travail pour améliorer votre impact et votre influence

Pour plus d’informations, reportez-vous à la page relative à la [transformation numérique avec Microsoft 365](http://transform.microsoft.com). 

#### <a name="microsoft-teams-for-highly-regulated-data"></a>Microsoft Teams pour les données hautement réglementées

Le terme « données hautement réglementées » désigne les données soumises à des réglementations régionales ou les données les plus précieuses pour votre organisation, telles que les secrets commerciaux, les informations financières ou relatives aux ressources humaines, et votre stratégie d’entreprise. Vous pouvez configurer un site Teams de manière à restreindre l’accès à ces données, à les classer, à en éviter la perte et à les chiffrer. Pour plus d’informations, consultez l’article [Sites SharePoint Online et Microsoft Teams pour les données hautement réglementées](teams-sharepoint-online-sites-highly-regulated-data.md).

#### <a name="result"></a>Résultat

Liste des scénarios de Microsoft Teams qui répondent aux besoins de votre organisation pour le travail en équipe et la collaboration.

## <a name="phase-2-onboard"></a>Phase 2 : intégration

Dans cette phase, vous allez planifier les aspects techniques d’un déploiement de Microsoft Teams et commencer à le déployer sur des groupes d’utilisateurs sélectionnés.

### <a name="prerequisites-identity-and-device-access-configuration"></a>Conditions préalables : configuration des identités et de l’accès aux appareils

Pour protéger l’accès aux équipes, vérifiez que vous avez configuré les [stratégies pour les identités et l’accès aux appareils](identity-access-policies.md) ainsi que les [stratégies d’accès à SharePoint Online recommandées](sharepoint-file-access-policies.md).

### <a name="step-1-complete-your-technical-planning"></a>Étape 1 : finaliser la planification technique

Avant de commencer la planification technique, déterminez si vous voulez utiliser FastTrack. Si votre organisation compte plus de 50 utilisateurs et participe à un [plan éligible](https://technet.microsoft.com/library/dn783224.aspx), vous pouvez utiliser [FastTrack pour Microsoft 365](https://fasttrack.microsoft.com/microsoft365), disponible sans frais supplémentaires, pour vous guider dans la planification, le déploiement et l’adoption du service. Vous pouvez aussi effectuer cette tâche vous-même à l’aide de nos Assistants Intégration FastTrack, disponibles auprès de [FastTrack](https://fasttrack.microsoft.com/) une fois que vous vous êtes connecté avec votre compte Office 365.

Si vous effectuez votre propre planification (ou conjointement avec FastTrack), vous devez déterminer si votre réseau et l’organisation sont déjà prêts pour Microsoft Teams. Il est particulièrement important que vous répondiez aux critères de sortie réseau dans votre [infrastructure de base](deploy-foundation-infrastructure.md), avec une attention particulière accordée à la bande passante, au débit et aux retards du trafic afin d’optimiser les performances pour les réunions Microsoft Teams.

Utilisez ces ressources pour préparer les aspects techniques de votre organisation en vue d’un déploiement Microsoft Teams : 

- [Vérifier la préparation de votre environnement pour Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/environment-readiness)
- [Préparer le réseau de votre organisation pour Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/prepare-network)
- [URL et plages d’adresses IP Office 365](https://docs.microsoft.com/MicrosoftTeams/office-365-urls-ip-address-ranges)

Pour une meilleure compréhension de la sécurité dans Microsoft Teams, passez en revue les ressources supplémentaires suivantes :

- [Présentation de la sécurité et de la conformité dans Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/security-compliance-overview)
- [Groupes Office 365 et Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/office-365-groups)
- [Accès invité dans Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/office-365-groups)

Utilisez ensuite les ressources suivantes pour comprendre la gestion des licences Microsoft Teams et pour configurer Microsoft Teams pour votre organisation :

- [Licences Office 365 pour Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/office-365-licensing)
- [Gérer l’accès des utilisateurs à Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/user-access)
- [Obtenir des clients pour Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/get-clients)
- [Activer Microsoft Teams dans votre organisation Office 365](https://docs.microsoft.com/MicrosoftTeams/office-365-set-up)
- [Gérer les fonctionnalités Microsoft Teams dans votre organisation Office 365](https://docs.microsoft.com/microsoftteams/enable-features-office-365)

#### <a name="result"></a>Résultat

La planification de votre réseau, de la sécurité et des licences Office 365 est terminée et vous êtes prêt à déployer Microsoft Teams pour des groupes sélectionnés dans votre organisation.

### <a name="step-2-run-an-it-pilot"></a>Étape 2 : exécuter une session pilote

Dans la plupart des moyennes et grandes organisations, nous vous conseillons d’exécuter une session pilote avec vos parties prenantes de la phase 1, les adeptes précoces et les amateurs de technique. Pendant la session pilote :

- Choisissez un scénario d’entreprise Microsoft Teams dans lequel les participants de votre session pilote peuvent s’exercer. Consultez le [kit de prise en main de Microsoft Teams](http://microsoft.com/download/56505) pour vous inspirer.
- Donnez aux participants de votre session pilote un ensemble d’exercices pour tester les fonctions de conversation instantanée, de stockage de fichiers, de réunion et les autres fonctionnalités de Microsoft Teams.
- Déterminez votre stratégie de gestion des modifications et fournissez des supports pour faire adopter le système aux utilisateurs à l’échelle de l’organisation. Les supports de gestion des modifications peuvent inclure un texte d’annonce par e-mail, des plans de formation interne, des affiches et des présentations. Ces supports permettront d’informer votre organisation sur Microsoft Teams et ses avantages avec pour objectifs de sensibiliser les utilisateurs et de promouvoir l’utilisation de Teams. Consultez l’article [Élaborer une stratégie de gestion des modifications pour Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/change-management-strategy) pour découvrir quelques suggestions.
- Demandez aux participants de votre session pilote de passer en revue les supports de stratégie de gestion des modifications en fonction de leurs expériences. Ils peuvent fournir des astuces sur les meilleures pratiques et des conseils sur la meilleure façon de décrire les avantages de Microsoft Teams et sur son utilisation pour le travail en équipe et la collaboration.

#### <a name="result"></a>Résultat

Votre session pilote Microsoft Teams est terminée et les supports de gestion des modifications de départ ont été développés, révisés et améliorés.

### <a name="step-3-roll-out-to-a-business-group"></a>Étape 3 : déployer pour un groupe d’entreprise

Une fois votre session pilote terminée, déployez Microsoft Teams pour un groupe d’entreprise ou un service de votre organisation. Ce processus de déploiement doit inclure les éléments suivants :

- Identification des scénarios d’entreprise clés pour Microsoft Teams au sein du groupe d’entreprise.
- Annonces pour informer les utilisateurs des attentes et du calendrier pour l’utilisation de Microsoft Teams pour les équipes de service, de travail ou de projet.
- Formation directe à Microsoft Teams pour les utilisateurs ou liens vers des ressources pour présenter Microsoft Teams et son utilisation.
- Un mécanisme de commentaires, comme une équipe centrale composée de tous les membres du groupe d’entreprise, pour recueillir les commentaires et les problèmes des utilisateurs du groupe d’entreprise.

Pendant le déploiement, vous pouvez améliorer vos supports de gestion des modifications en vue du processus de déploiement à l’échelle de l’organisation.

#### <a name="result"></a>Résultat

Un groupe d’entreprise est opérationnel avec Microsoft Teams et les supports de gestion des modifications ont été testés et améliorés.

## <a name="phase-3-drive-value"></a>Phase 3 : créer de la valeur

Dans cette phase, vous allez terminer le processus de déploiement de Microsoft Teams dans votre organisation et soutenir vos utilisateurs pour qu’ils se rendent compte de ses avantages.

### <a name="step-1-roll-out-teams-to-the-rest-of-your-organization"></a>Étape 1 : déployer Microsoft Teams dans le reste de votre organisation

Après avoir terminé votre déploiement pour un groupe d’entreprise ciblé, déployez Microsoft Teams dans le reste de votre organisation. Ce processus de déploiement doit inclure les éléments suivants :

- Identification des scénarios d’entreprise clés pour Microsoft Teams au sein de vos groupes d’entreprise distincts.
- Utilisation de vos supports de gestion des modifications améliorés pour les annonces afin d’informer votre organisation des attentes et du calendrier pour l’utilisation de Microsoft Teams pour les équipes de service, de travail ou de projet.
- Dispense d’une formation de Microsoft Teams pour les utilisateurs ou fourniture de liens vers des ressources pour présenter Microsoft Teams et son utilisation. Consultez les ressources de formation sur [Formation à Microsoft Teams pour les utilisateurs finaux](https://docs.microsoft.com/microsoftteams/enduser-training).
- Un mécanisme de commentaires, comme une équipe centrale composée de tous les membres du groupe, pour recueillir les commentaires et traiter les problèmes des utilisateurs de l’organisation. Si votre organisation possède moins de 2 500 collaborateurs, utilisez un canal public dans Microsoft Teams. Sinon, utilisez un groupe public dans Yammer.

#### <a name="result"></a>Résultat

Votre organisation est opérationnelle et votre stratégie de gestion des modifications est en place pour informer, former et permettre aux utilisateurs de commencer à utiliser Microsoft Teams.

### <a name="step-2-measure-usage-manage-satisfaction-and-drive-adoption"></a>Étape 2 : mesurer l’utilisation, gérer la satisfaction et favoriser l’adoption

Après avoir déployé Microsoft Teams pour toute votre organisation, vous devez continuer à utiliser votre stratégie de gestion des modifications pour :

- Inciter votre équipe de direction à promouvoir Microsoft Teams comme outil de collaboration et de travail d’équipe pour l’organisation.
- Encourager les collaborateurs à l’utiliser pour le groupe d’entreprise, la collaboration et les communications des équipes de service, de travail et de projet.

Voici des suggestions d’activités :

- Consultez la page [Conseils sur l’adoption d’Office 365](https://aka.ms/successfactors) pour en savoir plus sur les meilleures pratiques générales relatives à l’adoption du service cloud. 
- Consultez l’article [Rapports d’activité Office 365](https://support.office.com/article/Activity-Reports-in-the-Office-365-admin-center-0d6dfb17-8582-4172-a9a9-aed798150263) pour comprendre l’utilisation des services Office 365 au sein de votre organisation. Si vous n’êtes pas administrateur général Office 365 pour votre organisation, demandez à la personne habilitée de vous accorder les autorisations d’accès en lecture aux rapports pour que vous puissiez accéder aux rapports d’activité.
- Surveillez votre site de commentaires (un canal public dans une équipe centrale ou Yammer) pour identifier les problèmes et les commentaires des utilisateurs concernant leur expérience avec Microsoft Teams. Résolvez les doutes et les problèmes rencontrés aussi rapidement que possible pour prévenir toute frustration et tout abandon de Microsoft Teams par les membres.
- Identifiez et encouragez vos spécialistes de chaque groupe d’entreprise et soulignez leurs réussites et leurs meilleures pratiques grâce à l’utilisation de Microsoft Teams. Communiquez leurs réussites à l’organisation pour montrer le succès et l’adoption du projet. La validation des responsables techniques au sein d’un groupe d’entreprise peut exercer une grande influence sur les responsables et les collègues.

#### <a name="result"></a>Résultat

Votre organisation a adopté Microsoft Teams en tant qu’outil de collaboration et de travail d’équipe.

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Pour bénéficier d’un aperçu des coulisses de Microsoft et découvrir comment l’entreprise a déployé et utilise Microsoft Teams pour booster la collaboration, consultez les ressources suivantes :

- [Le déploiement de Microsoft Teams facilite la collaboration et améliore le travail d’équipe](https://www.microsoft.com/itshowcase/Article/Content/1013/Deploying-Microsoft-Teams-streamlines-collaboration-and-improves-teamwork)
- [Microsoft Teams améliore la collaboration dans l’espace de travail moderne chez Microsoft](https://www.microsoft.com/itshowcase/Article/Content/1012/Microsoft-Teams-increases-collaboration-in-the-modern-workplace-at-Microsoft)

## <a name="next-steps"></a>Étapes suivantes

- [Gérer les fonctionnalités Microsoft Teams dans votre organisation Office 365](https://docs.microsoft.com/microsoftteams/enable-features-office-365)
- [Formation à Microsoft Teams pour les administrateurs](https://docs.microsoft.com/microsoftteams/itadmin-readiness)
