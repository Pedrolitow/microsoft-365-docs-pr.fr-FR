---
title: Déployer Exchange Online pour Microsoft 365 Entreprise
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/28/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
description: Parcourez le processus de planification, présentant et la valeur d’Exchange Online de conduite dans Microsoft 365 entreprise au sein de votre organisation.
ms.openlocfilehash: aafa1b28546eb77938bb3e4a5ebe9ccd60b9a60b
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867461"
---
# <a name="deploy-exchange-online-for-microsoft-365-enterprise"></a>Déployer Exchange Online pour Microsoft 365 Entreprise

Exchange Online est votre service cloud principale pour la messagerie et calendrier qui vous aide à vos utilisateurs collaborent de manière à ne nécessite pas d’une conversation en temps réel ou centralisés de stockage des documents. Exchange Online est comment communication de courte durée groupe individuels et de petite taille et de planification et un élément clé de l’est conçu pour la valeur de travail d’équipe de Microsoft 365 pour entreprises. Exchange Online vous permet de faire plus et travailler plus efficacement avec l’application Outlook connue, quel que soit le périphérique que vous êtes en.

Exchange Online avancées aux fonctionnalités de sécurité, y compris le filtrage anti-spam et anti-programme malveillant pour protéger les boîtes aux lettres et les fonctionnalités de prévention de perte de données qui empêchent les utilisateurs d’envoyer par erreur des informations sensibles à des personnes non autorisées. Sécurité Exchange Online est un élément clé de la valeur de la sécurité Intelligent de Microsoft 365 pour entreprises.

Si vous êtes novice en matière vers Exchange Online, voir [Microsoft Exchange Online](https://products.office.com/exchange/exchange-online).

Phases et étapes suivantes vous guideront dans le processus de prévision le rôle d’Exchange Online dans votre organisation, l’intégration de votre organisation vers Exchange Online à travers une série de déploiements progressifs et pour l’utilisation d’Exchange Online et son valeur à vos utilisateurs finaux.

>[!Note]
>Ces instructions de déploiement doivent être suivies uniquement une fois que vous avez terminé [Phase 2-Identity](identity-infrastructure.md) de l’infrastructure de base Microsoft 365 pour entreprises.
>

## <a name="phase-1-envision"></a>Phase 1 : comprendre

Durant cette phase, vous rassemblez les personnes de votre déploiement Exchange Online et déterminez la manière dont votre organisation utilise Exchange Online pour répondre aux besoins de son entreprise.

### <a name="step-1-gather-your-exchange-online-deployment-members"></a>Étape 1 : Collecter des membres de votre déploiement Exchange Online

Pour réussir le déploiement d’Exchange Online en haut de [Phase 2-Identity](identity-infrastructure.md) de l’infrastructure de base Microsoft 365 pour entreprises, vous devez obtenir les personnes appropriées pour les commentaires. Personnes clés sont les décideurs d’entreprise, les ressources informatiques nécessaires telles que les architectes et les implémenteurs et préconise pour vos utilisateurs finaux. 

Ces trois groupes de vous assurer que votre déploiement Exchange Online contient des observations sur qui traitent les besoins de l’entreprise, les aspects techniques de migration de boîtes aux lettres et de sécurité et que le résultat sera quelque chose que les utilisateurs classiques utilisera.

#### <a name="result"></a>Résultat

Liste des personnes qui représentent les aspects professionnels, techniques et des utilisateurs finaux de votre organisation.

### <a name="step-2-determine-and-prioritize-your-exchange-online-business-scenarios"></a>Étape 2 : Déterminer et classer par priorité vos scénarios d’entreprise Exchange Online

Exchange Online peut être utilisée à des fins différentes. Vous devez savoir quels objectifs mapper à vos besoins sur les différents niveaux de votre organisation, les groupes de votre entreprise, départements ou équipes individuelles de travail et de projet. Vous devriez cibler Exchange Online pour répondre à vos communications de courte durée groupe individuels et les petites et les besoins de planification. 

Permet de voir les avantages d’Exchange Online consiste à examiner comment personnes, une équipe ou v-team interagir aujourd'hui et pour trouver un scénario qui fournit à votre disposition pour planifier des réunions, communiquer et collaborer. N’oubliez pas que [Les équipes Microsoft](teams-workload.md) peut être un meilleur choix pour certains de vos scénarios de collaboration.

Exchange Online permet de mettre en place les scénarios d’entreprise stratégiques suivants pour Microsoft 365 Entreprise :

- Collaborer sur des documents en temps réel ou à votre rythme afin de simplifier le processus de co-création
- Gérer les projets, les tâches et les délais pour atteindre vos objectifs métiers
- Comprendre vos habitudes de travail pour améliorer votre impact et votre influence
- Communiquer avec votre équipe afin de rester informé, de demander des informations et de créer une cohésion et un consensus
- Stocker et partager des fichiers internes ou externes à votre entreprise pour travailler en toute transparence au-delà des frontières structurelles
- Travailler en toute sécurité avec votre appareil en tout lieu et à tout moment pour atteindre plus d’objectifs, en conservant une méthode de travail flexible
- Protéger vos informations et réduire le risque de perte de données
- Détecter et assurez la protection contre les menaces externes 
- Surveiller, signaler et analyser l’activité pour réagir rapidement pour fournir la sécurité de l’organisation
- Assurer pour votre organisation un niveau supérieur de confidentialité et de conformité au Règlement général sur la protection des données (RGPD)

Pour plus d’informations, reportez-vous à la page relative à la [transformation numérique avec Microsoft 365](http://transform.microsoft.com). 

#### <a name="result"></a>Résultat
Une liste de scénarios Exchange Online qui répondent aux besoins de votre organisation pour la communication, la planification et la collaboration de courte durée.

## <a name="phase-2-onboard"></a>Phase 2 : intégration

Durant cette phase, vous planifiez les aspects techniques d’un déploiement Exchange Online et lancer le déploiement à certains groupes d’utilisateurs.

### <a name="prerequisites-identity-and-device-access-configuration"></a>Conditions préalables : configuration des identités et de l’accès aux appareils

Pour protéger l’accès aux boîtes aux lettres Exchange Online, assurez-vous que vous avez configuré des [identités et des périphériques accès stratégies](identity-access-policies.md) et la [recommandé des stratégies d’accès Exchange Online](secure-email-recommended-policies.md).

### <a name="step-1-complete-your-technical-planning"></a>Étape 1 : finaliser la planification technique

Avant de commencer la planification technique, déterminez si vous souhaitez utiliser FastTrack. Si votre organisation a plus de 50 sièges et fait partie d’un [plan éligible](https://technet.microsoft.com/library/dn783224.aspx), vous pouvez utiliser [FastTrack pour 365 Microsoft](https://fasttrack.microsoft.com/microsoft365), disponible sans coût supplémentaire pour vous guider dans la planification, le déploiement et d’adoption du service. Ou bien, vous pouvez effectuer cette tâche à l’aide des Assistants FastTrack embarquement, qui sont disponibles auprès de [FastTrack](https://fasttrack.microsoft.com/) une fois que vous vous connectez à votre compte Office 365.

Si vous effectuez votre propre planification ou en association avec FastTrack, vous devez déterminer si votre réseau et votre organisation sont prêtes pour Exchange Online. Il est particulièrement important que vous répondent aux critères de sortie pour la mise en réseau dans votre infrastructure de base, avec une attention particulière aux retards de trafic d’optimiser les performances pour le trafic supplémentaire pour Exchange, le débit et la bande passante Internet Messagerie en ligne et les pièces jointes.

Utilisez ces ressources pour préparer les aspects techniques d’un déploiement Exchange Online : 

- [Méthodes de migration des comptes de courrier vers Office 365](https://docs.microsoft.com/Exchange/mailbox-migration/mailbox-migration)
- [Gestionnaire de migration de messagerie Office 365](https://portal.office.com/onboarding/mailsetupadvisor#/) (doit être connecté à votre abonnement Office 365)
- [Collaboration dans Exchange Online](https://technet.microsoft.com/library/jj983794(v=exchg.150).aspx)
- [Destinataires dans Exchange Online](https://technet.microsoft.com/library/jj200702(v=exchg.150).aspx)

Pour une meilleure compréhension de la sécurité dans Exchange Online, consultez les ressources suivantes :

- [Autorisations dans Exchange Online](https://technet.microsoft.com/library/jj200692(v=exchg.150).aspx) 
- [Sécurité et conformité pour Exchange Online](https://technet.microsoft.com/library/jj200706(v=exchg.150).aspx) 
- [Protection contre le courrier indésirable et les programmes malveillants](https://technet.microsoft.com/library/jj200731(v=exchg.150).aspx)

Ensuite, utilisez ces ressources pour apprendre à gérer les boîtes aux lettres Exchange Online :

- [Créer des boîtes aux lettres dans Exchange Online](https://technet.microsoft.com/library/jj907304(v=exchg.150).aspx)
- [Gérer des boîtes aux lettres utilisateur](https://technet.microsoft.com/library/bb123809(v=exchg.150).aspx) 
- [Création et gestion de groupes de distribution](https://technet.microsoft.com/library/bb124513%28v=exchg.150%29.aspx)

#### <a name="result"></a>Résultat

Vous comprenez la gestion, la sécurité et migration de boîtes aux lettres et vous êtes prêt à commencer le déploiement d’Exchange Online à des groupes sélectionnés dans votre organisation.

### <a name="step-2-run-an-it-pilot"></a>Étape 2 : exécuter une session pilote

Dans la plupart des moyennes et grandes organisations, nous vous conseillons d’exécuter une session pilote avec vos parties prenantes de la phase 1, les adeptes précoces et les amateurs de technique. Pendant la session pilote :

- Choisissez un scénario d’entreprise Exchange Online dans laquelle les participants pilotes informatique peuvent pratique.
- Indiquez votre pilotes participants licences Office 365 et migrer leurs boîtes aux lettres locales vers Exchange Online.
- Donnez à votre pilotes participants un ensemble d’exercices pour tester la messagerie Exchange Online, la planification et autres fonctionnalités.
- Déterminer votre stratégie de gestion des modifications et générer des documents pour encourager l’adoption d’Exchange Online utilisateur à l’échelle de l’organisation. Supports de gestion des modifications peuvent inclure la messagerie texte d’annonce, des plans de formation interne, affiches couloir et des présentations. Ces documents seront informer votre organisation Exchange Online et ses avantages avec les objectifs de sensibilisation déclenchement et utilisation de la commande. Consultez l’article [Modifier la stratégie de gestion pour les équipes Microsoft](https://docs.microsoft.com/MicrosoftTeams/change-management-strategy) pour certaines des idées.
- Demandez-leur de votre informatique pilote consultez les documents de gestion des modifications en fonction de leur expérience. Ils peuvent fournir des conseils sur les meilleures pratiques et conseils pour mieux décrire les avantages d’Exchange Online et comment l’utiliser pour la communication et la planification.

#### <a name="result"></a>Résultat

Votre pilote Exchange Online IT est terminée et que les documents de gestion du changement initial développés, révisées et affinées.

### <a name="step-3-roll-out-to-a-business-group"></a>Étape 3 : déployer pour un groupe d’entreprise

Une fois votre pilote informatique, déployer Exchange Online à un groupe d’entreprise ou un service dans votre organisation. Si votre organisation utilise un service de messagerie locaux tels que Exchange Server, ce déploiement se compose de migration de boîtes aux lettres. Ce déploiement doit inclure :

- Identification des scénarios d’entreprise clés pour Exchange Online dans le groupe d’entreprise.
- Activités d’annonce pour informer les utilisateurs les attentes et les chronologies pour Exchange Online d’utilisation pour les services et les équipes de travail ou un projet.
- Migration des boîtes aux lettres locales votre entreprise des membres du groupe vers Exchange Online.
- Formation des utilisateurs en dans Exchange Online ou liens vers des ressources d’introduire Exchange Online et comment l’utiliser.
- Mécanisme de commentaires, comme une équipe Microsoft Teams centrale composée de tous les membres du groupe d’entreprise, pour recueillir les commentaires et résoudre les problèmes des utilisateurs du groupe d’entreprise.

Pendant le déploiement, vous pouvez améliorer vos supports de gestion des modifications en vue du processus de déploiement à l’échelle de l’organisation.

#### <a name="result"></a>Résultat

Est un groupe et en cours d’exécution avec Exchange Online et les documents de gestion des modifications ont été testés et affinées.

## <a name="phase-3-drive-value"></a>Phase 3 : créer de la valeur

Durant cette phase, vous effectuez le déploiement d’Exchange Online et prend en charge les utilisateurs pour leur permettre de bénéficier de ses avantages.

### <a name="step-1-roll-out-exchange-online-to-the-rest-of-your-organization"></a>Étape 1 : Déployer Exchange Online à l’intégralité de votre organisation.

Le processus de déploiement dans le reste de votre organisation doit inclure les éléments suivants :

- Identification des scénarios d’entreprise clés pour Exchange Online dans des groupes d’activité distincts.
- Utilisation de vos documents de gestion de modification affinée des activités d’annonce informer votre organisation des attentes et un calendrier pour l’utilisation d’Exchange Online.
- Migration des boîtes aux lettres pour le reste de votre organisation vers Exchange Online.
- Proposer la formation des utilisateurs sur Exchange Online ou fournissent des liens vers des ressources d’introduire Exchange Online et comment l’utiliser.
- Mécanisme de commentaires, comme une équipe centrale composée de tous les membres du groupe, pour recueillir les commentaires et traiter les problèmes des utilisateurs de l’organisation. Si votre organisation possède moins de 2 500 collaborateurs, utilisez un canal public dans Teams. Sinon, utilisez un groupe public dans Yammer.

#### <a name="result"></a>Résultat

Votre organisation est actif et en cours d’exécution et votre stratégie de gestion du changement est en place pour informer, former et permettre aux utilisateurs d’utiliser Exchange Online.

### <a name="step-2-measure-usage-manage-satisfaction-and-drive-adoption"></a>Étape 2 : mesurer l’utilisation, gérer la satisfaction et favoriser l’adoption

Après le déploiement d’Exchange Online dans toute l’organisation, vous devez continuer à utiliser votre stratégie de gestion des modifications pour :

- Avoir vos cadres dirigeants promouvoir Exchange Online en tant que le principal outil pour la communication individuel et de courte durée et la planification.
- Encourager les personnes à l’utiliser pour le département par divisions, Professionnel et les communications d’équipe, du calendrier et de collaboration de projet.

Voici des suggestions d’activités :

- Consultez la page [Conseils sur l’adoption d’Office 365](https://aka.ms/successfactors) pour en savoir plus sur les meilleures pratiques générales relatives à l’adoption du service cloud. 
- Consultez l’article [Rapports d’activité Office 365](https://docs.microsoft.com/office365/admin/activity-reports/activity-reports) pour comprendre l’utilisation des services Office 365 au sein de votre organisation. Si vous n’êtes pas administrateur général Office 365 pour votre organisation, demandez à la personne habilitée de vous accorder les autorisations d’accès en lecture aux rapports pour que vous puissiez accéder aux rapports d’activité.
- Surveiller votre lieu de commentaires (un canal public d’une équipe d’équipes ou d’Yammer central) pour les problèmes et les commentaires des utilisateurs sur leurs expériences avec Exchange Online. Résoudre les questions et problèmes aussi rapidement que vous pouvez empêcher les personnes frustration et de démonstration de la prise en charge pour le déploiement.
- Identifier et entretenir champions dans chaque groupe d’entreprise et mettre en surbrillance les réalisations et les meilleures pratiques à l’aide d’Exchange Online. Refléter leurs succès out à l’organisation pour afficher d’adoption et de la réussite du projet. Implique par les responsables techniques au sein d’un groupe d’entreprises peut avoir une puissante influence sur leaders et des homologues.

#### <a name="result"></a>Résultat

Votre organisation a adopté Exchange Online en tant que sa communication de courte durée groupe individuels et de petites principal et l’outil de planification.

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Pour lire à l’intérieur de Microsoft et découvrez comment la société migrées vers Exchange Online et Exchange Online Protection utilise pour protéger contre les attaques informatiques, voir :

- [Microsoft migre 150 000 boîtes aux lettres vers Exchange Online](https://www.microsoft.com/itshowcase/Article/Content/577/Microsoft-migrates-150000-mailboxes-to-Exchange-Online)
- [Microsoft utilise l’intelligence des menaces pour se protéger contre les menaces, les détecter et y faire face](https://www.microsoft.com/itshowcase/Article/Content/934/Microsoft-uses-threat-intelligence-to-protect-detect-and-respond-to-threats)
- [Microsoft déjoue les tentatives d’hameçonnage grâce à Office 365](https://www.microsoft.com/itshowcase/Article/Content/956/Microsoft-thwarts-phishing-attempts-with-Office-365)

## <a name="next-steps"></a>Étapes suivantes

Consultez les ressources suivantes pour la maintenance d’Exchange Online en cours :

- [Centre d'administration Exchange dans Exchange Online](https://technet.microsoft.com/library/jj200743(v=exchg.150).aspx) 
- [Analyse, création de rapports et suivi des messages dans Exchange Online](https://technet.microsoft.com/library/jj200725(v=exchg.150).aspx)
- [Sauvegarde du courrier électronique dans Exchange Online](https://technet.microsoft.com/library/dn440734(v=exchg.150).aspx) 
