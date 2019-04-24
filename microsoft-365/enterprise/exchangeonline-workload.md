---
title: Déployer Exchange Online pour Microsoft 365 Enterprise
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/28/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-email-calendar
ms.custom:
- Strat_O365_Enterprise
description: Découvrez le processus de planification, de déploiement et de mise en œuvre de la valeur d'Exchange Online dans Microsoft 365 Enterprise au sein de votre organisation.
ms.openlocfilehash: 6efd94da7806b6268881f7eaabe5efacc8920f47
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32281204"
---
# <a name="deploy-exchange-online-for-microsoft-365-enterprise"></a>Déployer Exchange Online pour Microsoft 365 Enterprise

*Cette charge de travail est incluse dans les versions E3 et E5 de Microsoft 365 entreprise*

Exchange Online est votre service Cloud principal pour le courrier électronique et le calendrier qui permet aux utilisateurs de collaborer de manière à ne pas exiger une conversation en temps réel ou un stockage centralisé des documents. Exchange Online vous explique comment effectuer une communication et une planification de courte durée de vie des groupes et des groupes de petite taille, et constitue un élément clé de la valeur de création pour le travail d'équipe de Microsoft 365 entreprise. Exchange Online vous permet de travailler plus efficacement avec l'application Outlook bien connue, quel que soit le périphérique sur lequel vous vous trouvez.

Exchange Online dispose également de fonctionnalités de sécurité avancées, notamment le filtrage anti-programmes malveillants et le filtrage du courrier indésirable pour protéger les boîtes aux lettres et les fonctionnalités de protection contre la perte de données, qui empêchent les utilisateurs d'envoyer par erreur des informations sensibles à des personnes non autorisées. La sécurité d'Exchange Online est un élément clé de la valeur de sécurité intelligente de Microsoft 365 Enterprise.

Si vous êtes novice en matière d'Exchange Online, consultez la rubrique [Microsoft Exchange Online](https://products.office.com/exchange/exchange-online).

Les phases et les étapes suivantes vous guident tout au long du processus de prévision du rôle d'Exchange Online au sein de votre organisation, de l'intégration de votre organisation à Exchange Online via une série de déploiements progressifs et de l'utilisation d'Exchange Online et de ses valeur pour vos utilisateurs finaux.

>[!Note]
>Ces instructions de déploiement doivent être suivies uniquement après avoir terminé la [phase 2-identité](identity-infrastructure.md) de l'infrastructure de base de Microsoft 365 Enterprise Foundation.
>

## <a name="phase-1-envision"></a>Phase 1 : comprendre

Dans cette phase, vous recueillez les personnes pour votre déploiement Exchange Online et vous déterminez comment votre organisation utilisera Exchange Online pour répondre aux besoins de son entreprise.

### <a name="step-1-gather-your-exchange-online-deployment-members"></a>Étape 1: rassemblez vos membres de déploiement Exchange Online

Pour réussir un déploiement d'Exchange Online en [phase 2: identité](identity-infrastructure.md) de l'infrastructure de base de Microsoft 365 Enterprise Foundation, vous devez obtenir les personnes appropriées pour les commentaires et les commentaires. Les personnes clés incluent les décideurs d'entreprise, le personnel informatique tel que les architectes et les responsables de l'implémentation, et les avocats pour vos utilisateurs finaux. 

Ces trois groupes garantissent que votre déploiement Exchange Online inclut des considérations qui répondent aux besoins de l'entreprise, des aspects techniques de la migration et de la sécurité des boîtes aux lettres, et que le résultat sera utilisé par les utilisateurs habituels.

#### <a name="result"></a>Résultat

Liste des personnes qui représentent les aspects professionnels, techniques et des utilisateurs finaux de votre organisation.

### <a name="step-2-determine-and-prioritize-your-exchange-online-business-scenarios"></a>Étape 2: déterminer et classer par priorité vos scénarios d'entreprise Exchange Online

Exchange Online peut être utilisé à différentes fins. Vous devez déterminer les objectifs qui correspondent aux besoins de votre entreprise, ainsi que les différents niveaux de votre organisation, vos groupes d'entreprise, vos services ou des équipes de travail et de projets individuels. Vous devez cibler Exchange Online pour répondre à vos besoins en matière de communication et de planification de votre entreprise et de votre groupe de petite taille. 

L'une des façons de voir les avantages d'Exchange Online est d'examiner comment les personnes, une équipe ou une équipe v interagissent aujourd'hui, puis de trouver un scénario approprié qui offre des moyens plus simples de communiquer, de planifier des réunions et de collaborer. N'oubliez pas que [Microsoft teams](teams-workload.md) peut être un meilleur choix pour certains de vos scénarios de collaboration.

Exchange Online permet les scénarios d'entreprise stratégiques suivants pour Microsoft 365 Enterprise:

- Collaborer sur des documents en temps réel ou à votre rythme afin de simplifier le processus de co-création
- Gérer les projets, les tâches et les délais pour atteindre vos objectifs métiers
- Comprendre vos habitudes de travail pour améliorer votre impact et votre influence
- Communiquer avec votre équipe afin de rester informé, de demander des informations et de créer une cohésion et un consensus
- Stocker et partager des fichiers internes ou externes à votre entreprise pour travailler en toute transparence au-delà des frontières structurelles
- Travailler en toute sécurité avec votre appareil en tout lieu et à tout moment pour atteindre plus d’objectifs, en conservant une méthode de travail flexible
- Protéger vos informations et réduire le risque de perte de données
- Détecter et se protéger contre les menaces externes 
- Surveiller, signaler et analyser l'activité pour réagir rapidement afin de fournir une sécurité de l'Organisation
- Assurer pour votre organisation un niveau supérieur de confidentialité et de conformité au Règlement général sur la protection des données (RGPD)

Pour plus d’informations, reportez-vous à la page relative à la [transformation numérique avec Microsoft 365](http://transform.microsoft.com). 

#### <a name="result"></a>Résultat
Une liste de scénarios Exchange Online qui répondent aux besoins de votre organisation en matière de communication, de planification et de collaboration à courte durée de vie.

## <a name="phase-2-onboard"></a>Phase 2 : intégration

Dans cette phase, vous allez planifier les aspects techniques d'un déploiement Exchange Online et commencer à le déployer vers des groupes d'utilisateurs sélectionnés.

### <a name="prerequisites-identity-and-device-access-configuration"></a>Conditions préalables : configuration des identités et de l’accès aux appareils

Pour protéger l'accès aux boîtes aux lettres Exchange Online, vérifiez que vous avez configuré les [stratégies d'accès aux identités et aux appareils](identity-access-policies.md) et les stratégies d' [accès à Exchange Online recommandées](secure-email-recommended-policies.md).

### <a name="step-1-complete-your-technical-planning"></a>Étape 1 : finaliser la planification technique

Avant de commencer la planification technique, déterminez si vous voulez utiliser FastTrack. Si votre organisation a plus de 50 sièges et participe à un [plan éligible](https://technet.microsoft.com/library/dn783224.aspx), vous pouvez utiliser [FastTrack pour Microsoft 365](https://fasttrack.microsoft.com/microsoft365), disponible gratuitement pour vous guider dans la planification, le déploiement et l'adoption des services. Sinon, vous pouvez effectuer ce travail vous-même à l'aide des assistants d'intégration FastTrack, qui sont disponibles auprès de [FastTrack](https://fasttrack.microsoft.com/) une fois que vous vous êtes connecté avec votre compte Office 365.

Si vous effectuez votre propre planification ou conjointement avec FastTrack, vous devez déterminer si votre réseau et votre organisation sont prêts pour Exchange Online. Il est particulièrement important de respecter les critères de sortie pour la mise en réseau dans votre infrastructure de base, avec une attention particulière à la bande passante Internet, au débit et aux retards de trafic afin d'optimiser les performances pour le trafic supplémentaire pour Exchange. Courrier électronique et pièces jointes en ligne.

Utilisez ces ressources pour préparer les aspects techniques d'un déploiement Exchange Online: 

- [Méthodes de migration des comptes de courrier vers Office 365](https://docs.microsoft.com/Exchange/mailbox-migration/mailbox-migration)
- [Collaboration dans Exchange Online](https://technet.microsoft.com/library/jj983794(v=exchg.150).aspx)
- [Destinataires dans Exchange Online](https://technet.microsoft.com/library/jj200702(v=exchg.150).aspx)

Pour mieux comprendre la sécurité dans Exchange Online, consultez les ressources suivantes:

- [Autorisations dans Exchange Online](https://technet.microsoft.com/library/jj200692(v=exchg.150).aspx) 
- [Sécurité et conformité pour Exchange Online](https://technet.microsoft.com/library/jj200706(v=exchg.150).aspx) 
- [Protection contre le courrier indésirable et les programmes malveillants](https://technet.microsoft.com/library/jj200731(v=exchg.150).aspx)

Ensuite, utilisez ces ressources pour comprendre la gestion des boîtes aux lettres Exchange Online:

- [Créer des boîtes aux lettres utilisateur dans Exchange Online](https://technet.microsoft.com/library/jj907304(v=exchg.150).aspx)
- [Gérer des boîtes aux lettres utilisateur](https://technet.microsoft.com/library/bb123809(v=exchg.150).aspx) 
- [Création et gestion de groupes de distribution](https://technet.microsoft.com/library/bb124513%28v=exchg.150%29.aspx)

#### <a name="result"></a>Résultat

Vous comprenez la migration, la sécurité et la gestion des boîtes aux lettres, et vous êtes prêt à commencer à déployer Exchange Online dans des groupes sélectionnés dans votre organisation.

### <a name="step-2-run-an-it-pilot"></a>Étape 2 : exécuter une session pilote

Dans la plupart des moyennes et grandes organisations, nous vous conseillons d’exécuter une session pilote avec vos parties prenantes de la phase 1, les adeptes précoces et les amateurs de technique. Pendant la session pilote :

- Choisissez un scénario d'entreprise Exchange Online dans lequel vos participants peuvent s'exercer.
- Donnez aux participants du projet pilote des licences Office 365 et migrez leurs boîtes aux lettres locales vers Exchange Online.
- Donnez aux participants du projet pilote un ensemble d'exercices permettant de tester le courrier électronique, la planification et d'autres fonctionnalités Exchange Online.
- Déterminez votre stratégie de gestion des modifications et générez des documents pour conduire l'adoption par les utilisateurs à l'échelle de l'organisation d'Exchange Online. Les supports de gestion des modifications peuvent inclure le texte de l'annonce, des plans de formation interne, des affiches et des présentations. Ces documents informeront votre organisation d'Exchange Online et de ses avantages grâce aux objectifs de la sensibilisation et de l'utilisation. Pour en savoir plus, consultez l'article [stratégie de gestion des modifications pour Microsoft teams](https://docs.microsoft.com/MicrosoftTeams/change-management-strategy) .
- Demandez à vos participants responsables informatiques d'examiner les supports de gestion des modifications en fonction de leurs expériences. Ils peuvent fournir des conseils sur les meilleures pratiques et des conseils sur la façon de décrire au mieux les avantages d'Exchange Online et comment l'utiliser pour la communication et la planification.

#### <a name="result"></a>Résultat

Votre pilote informatique Exchange Online est complet et les ressources de gestion des modifications initiales ont été développées, revues et affinées.

### <a name="step-3-roll-out-to-a-business-group"></a>Étape 3 : déployer pour un groupe d’entreprise

Une fois votre pilote informatique terminé, déployez Exchange Online sur un groupe d'entreprise ou un service de votre organisation. Si votre organisation utilise un service de messagerie local tel qu'Exchange Server, ce déploiement est constitué de la migration de boîtes aux lettres. Ce déploiement doit inclure les éléments suivants:

- Identification des scénarios d'entreprise clés pour Exchange Online au sein du groupe d'entreprise.
- Annonces pour informer les utilisateurs des attentes et de la chronologie de l'utilisation d'Exchange Online pour les équipes de service, de travail ou de projet.
- Migration des boîtes aux lettres locales de vos membres de groupes d'entreprise vers Exchange Online.
- Fournir une formation aux utilisateurs sur Exchange Online ou des liens vers des ressources pour présenter Exchange Online et comment l'utiliser.
- Mécanisme de commentaires, comme une équipe Microsoft Teams centrale composée de tous les membres du groupe d’entreprise, pour recueillir les commentaires et résoudre les problèmes des utilisateurs du groupe d’entreprise.

Pendant le déploiement, vous pouvez améliorer vos supports de gestion des modifications en vue du processus de déploiement à l’échelle de l’organisation.

#### <a name="result"></a>Résultat

Un groupe d'entreprise est opérationnel avec Exchange Online et les supports de gestion des modifications ont été testés et améliorés.

## <a name="phase-3-drive-value"></a>Phase 3 : créer de la valeur

Dans cette phase, vous allez effectuer le déploiement d'Exchange Online et prendre en charge vos utilisateurs afin de les aider à tirer parti de ses avantages.

### <a name="step-1-roll-out-exchange-online-to-the-rest-of-your-organization"></a>Étape 1: déployer Exchange Online dans le reste de votre organisation

Le processus de déploiement dans le reste de votre organisation doit inclure les éléments suivants :

- Identification des scénarios d'entreprise clés pour Exchange Online au sein de groupes d'entreprise distincts.
- Utilisation de vos documents de gestion des modifications raffinés pour les activités d'annonce afin d'informer votre organisation des attentes et des délais pour l'utilisation d'Exchange Online.
- Migration des boîtes aux lettres pour le reste de votre organisation vers Exchange Online.
- La formation des utilisateurs sur Exchange Online ou des liens vers des ressources pour présenter Exchange Online et son utilisation.
- Mécanisme de commentaires, comme une équipe centrale composée de tous les membres du groupe, pour recueillir les commentaires et traiter les problèmes des utilisateurs de l’organisation. Si votre organisation possède moins de 2 500 collaborateurs, utilisez un canal public dans Teams. Sinon, utilisez un groupe public dans Yammer.

#### <a name="result"></a>Résultat

Votre organisation est active et votre stratégie de gestion des modifications est en place pour informer, former et permettre aux utilisateurs d'utiliser Exchange Online.

### <a name="step-2-measure-usage-manage-satisfaction-and-drive-adoption"></a>Étape 2 : mesurer l’utilisation, gérer la satisfaction et favoriser l’adoption

Après avoir déployé Exchange Online pour l'ensemble de votre organisation, vous devez continuer à utiliser votre stratégie de gestion des modifications pour:

- Faites en sorte que votre leadership encourage Exchange Online en tant qu'outil principal pour la communication et la planification individuelle et courte.
- EnCouragez les utilisateurs à l'utiliser pour les communications de groupe d'entreprise, de service, de travail et d'équipe de projet, de calendrier et de collaboration.

Voici des suggestions d’activités :

- Consultez la page [Conseils sur l’adoption d’Office 365](https://aka.ms/successfactors) pour en savoir plus sur les meilleures pratiques générales relatives à l’adoption du service cloud. 
- Consultez l’article [Rapports d’activité Office 365](https://docs.microsoft.com/office365/admin/activity-reports/activity-reports) pour comprendre l’utilisation des services Office 365 au sein de votre organisation. Si vous n’êtes pas administrateur général Office 365 pour votre organisation, demandez à la personne habilitée de vous accorder les autorisations d’accès en lecture aux rapports pour que vous puissiez accéder aux rapports d’activité.
- SurVeillez votre lieu de commentaire (un canal public dans une équipe de teams centrale ou Yammer) pour détecter les problèmes et les commentaires de personnes sur leur expérience avec Exchange Online. Traitez les questions et les problèmes aussi rapidement que vous le pouvez pour empêcher les personnes frustrées et démontrer la prise en charge du déploiement.
- Identifier et entretenir les champions de chaque groupe d'entreprise et mettre en évidence leurs réalisations et meilleures pratiques à l'aide d'Exchange Online. Refléter leur réussite à l'Organisation pour montrer la réussite et l'adoption du projet. Le visa des responsables techniques au sein d'un groupe d'entreprise peut exercer une influence considérable sur les dirigeants et les collègues.

#### <a name="result"></a>Résultat

Votre organisation a adopté Exchange Online en tant qu'outil de communication et de planification de courte durée et de groupe de petite taille.

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Pour lire le contenu de Microsoft et découvrir comment la société a migré vers Exchange Online et utilise Exchange Online Protection pour se protéger contre les attaques informatiques, voir:

- [Microsoft migre 150 000 boîtes aux lettres vers Exchange Online](https://www.microsoft.com/itshowcase/Article/Content/577/Microsoft-migrates-150000-mailboxes-to-Exchange-Online)
- [Microsoft utilise l’intelligence des menaces pour se protéger contre les menaces, les détecter et y faire face](https://www.microsoft.com/itshowcase/Article/Content/934/Microsoft-uses-threat-intelligence-to-protect-detect-and-respond-to-threats)
- [Microsoft déjoue les tentatives d’hameçonnage grâce à Office 365](https://www.microsoft.com/itshowcase/Article/Content/956/Microsoft-thwarts-phishing-attempts-with-Office-365)

## <a name="next-steps"></a>Étapes suivantes

Consultez ces ressources pour la maintenance en cours d'Exchange Online:

- [Centre d’administration Exchange dans Exchange Online](https://technet.microsoft.com/library/jj200743(v=exchg.150).aspx) 
- [Surveillance, création de rapports et suivi des messages dans Exchange Online](https://technet.microsoft.com/library/jj200725(v=exchg.150).aspx)
- [Sauvegarde du courrier électronique dans Exchange Online](https://technet.microsoft.com/library/dn440734(v=exchg.150).aspx) 
