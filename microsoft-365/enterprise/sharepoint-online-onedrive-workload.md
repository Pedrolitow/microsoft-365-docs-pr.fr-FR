---
title: Déployer SharePoint et OneDrive pour Microsoft 365 Entreprise
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/30/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-collaboration
- Strat_O365_Enterprise
ms.custom: ''
description: Suivez le processus de planification, de déploiement et de création de valeur de SharePoint au sein de votre organisation.
ms.openlocfilehash: d8a61a6bc6b4dae431d94e7ccfb9fb0ea8019427
ms.sourcegitcommit: a77c4889c5b7d3b8f16e74917079300e8f222941
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "37329204"
---
# <a name="deploy-sharepoint-and-onedrive-for-microsoft-365-enterprise"></a>Déployer SharePoint et OneDrive pour Microsoft 365 Entreprise

*Cette charge de travail est incluse dans les versions E3 et E5 de Microsoft 365 Entreprise*

SharePoint et Microsoft Teams vous permettent de stocker et partager des fichiers, de gérer le contenu et de travailler en collaboration. Il s’agit d’éléments clés de la valeur du travail d’équipe de Microsoft 365 Entreprise. 

SharePoint offre également des fonctionnalités avancées de sécurité, y compris le contrôle d’accès, avec les autorisations et le chiffrement de données en transit et au repos. Dans SharePoint, la sécurité est un élément clé de la valeur de sécurité intelligente de Microsoft 365 Entreprise.

Si vous débutez sur SharePoint, consultez les articles [SharePoint](https://products.office.com/sharepoint/sharepoint-online-collaboration-software) et [Prise en main de SharePoint](https://support.office.com/article/Get-started-with-SharePoint-3a26444b-08c5-46ad-b80a-cda82b11b27b#ID0EAABAAA=Basics).

Les phases et les étapes suivantes vous permettent de comprendre le rôle de SharePoint et de OneDrive Entreprise dans votre organisation, d’intégrer votre organisation à travers une série de déploiements progressifs, et de sensibiliser vos utilisateurs finaux à son utilisation et à sa valeur. Avant de commencer, vérifiez que vous avez configuré les bonnes phases de l’[infrastructure de base](deploy-workloads.md#foundation-infrastructure-prerequisites) de telle sorte que vos sites SharePoint disposent des fonctionnalités de sécurité utiles. 

Pour déployer OneDrive pour Microsoft 365 Entreprise, consultez la rubrique relative au [guide OneDrive pour les entreprises](https://docs.microsoft.com/onedrive/plan-onedrive-enterprise).

## <a name="phase-1-envision"></a>Phase 1 : Comprendre
Dans cette phase, vous rassemblerez les partenaires de l’organisation pour effectuer votre déploiement de SharePoint, ainsi que pour déterminer comment votre organisation utilisera SharePoint afin de traiter les besoins d’entreprise.

### <a name="step-1-gather-your-sharepoint-deployment-members"></a>Étape 1 : Recueillir les membres de votre déploiement SharePoint

Pour un déploiement réussi de SharePoint par-dessus l’[infrastructure de base de Microsoft 365 Entreprise](deploy-foundation-infrastructure.md), vous devez rassembler les bonnes personnes en vue d’obtenir leurs commentaires et leurs réactions. Les personnes clés incluent les décideurs d’entreprise, le service informatique (architectes et implémenteurs), et les défenseurs de vos utilisateurs finaux. 

Ces trois groupes veillent à ce que votre déploiement inclue des considérations qui répondent aux besoins professionnels, aux aspects techniques de sécurité et de migration des dossiers et documents, et à ce que le résultat soit adopté par vos utilisateurs types.

#### <a name="result"></a>Résultat

Liste des personnes qui représentent les perspectives professionnelles, techniques et celles des utilisateurs finaux de votre organisation.

### <a name="step-2-determine-and-prioritize-your-sharepoint-business-scenarios"></a>Étape 2 : Déterminer et définir les priorités des scénarios d’entreprise SharePoint

SharePoint peut être utilisé à des fins différentes, parmi lesquelles vous devez déterminer celles qui correspondent aux besoins de votre entreprise. Vous devez cibler SharePoint pour répondre aux besoins en stockage et partage de documents, en gestion de contenu et en collaboration de vos équipes, de votre service ou de l’ensemble de votre organisation. 

Affichez la liste des scénarios et des fonctionnalités disponibles dans [SharePoint](https://products.office.com/sharepoint/sharepoint-online-collaboration-software).

Voici des piliers commerciaux qui peuvent répondre aux besoins de votre organisation :

|||
|:-----|:-----|
| Partager et collaborer | Tirez parti des sites d’équipe, des sites de collaboration, et synchronisez-les. |
| Informer et impliquer | Informations bientôt disponibles. |
| Transformer | Utilise le flux pour créer un magasin ou un flux de travail. |
| Exploiter les connaissances collectives | Utilise la recherche pour apporter les résultats souhaités au sein de votre organisation. |
| Protéger | Garantit que votre organisation est sécurisée et conforme. |
| Développement/externe | Permet à votre organisation de développer des solutions et applications personnalisées avec SharePoint Framework. |
|||

Consultez la rubrique sur l’[administration de SharePoint](https://docs.microsoft.com/sharepoint/sharepoint-online) pour obtenir des informations sur la configuration de SharePoint en fonction de vos besoins.

Pour découvrir les avantages de SharePoint, étudiez la manière dont les individus, les équipes, les services ou l’ensemble de votre organisation interagissent actuellement, puis recherchez un scénario approprié qui propose des méthodes plus faciles pour stocker et partager des fichiers. Gardez à l’esprit que [Microsoft Teams](teams-workload.md) peut s’avérer un meilleur choix dans certains de vos scénarios.

#### <a name="sharepoint-site-for-highly-regulated-data"></a>Sites SharePoint pour les données hautement réglementées

Les données hautement réglementées sont soumises aux réglementations régionales représentent les données les plus précieuses de votre organisation comme les secrets commerciaux, les informations sur les ressources humaines ou financières et la stratégie de l’organisation. Vous pouvez configurer un site SharePoint pour un accès restreint, la classification des données, la protection contre la perte de données et le chiffrement pour ce type de données. Pour plus d’informations, consultez l’article [Les sites SharePoint et Microsoft Teams pour un scénario de données hautement réglementées](teams-sharepoint-online-sites-highly-regulated-data.md).

#### <a name="result"></a>Résultat
Une liste des scénarios SharePoint qui répondent aux besoins de votre organisation pour le stockage et le partage de documents, la gestion de contenu, la collaboration et la sécurité.

## <a name="phase-2-onboard"></a>Phase 2 : intégration

Dans cette phase, vous planifierez les aspects techniques d’un déploiement SharePoint et commencerez à effectuer le déploiement sur des groupes d’utilisateurs sélectionnés.

### <a name="prerequisites-identity-and-device-access-configuration"></a>Conditions préalables : configuration des identités et de l’accès aux appareils

Pour protéger l’accès aux sites SharePoint, vérifiez que vous avez configuré les [stratégies pour les identités et l’accès aux appareils](identity-access-policies.md) et les [stratégies d’accès à SharePoint recommandées](sharepoint-file-access-policies.md).

### <a name="step-1-complete-your-technical-planning"></a>Étape 1 : finaliser la planification technique

Avant de commencer la planification technique, déterminez si vous voulez utiliser FastTrack. Si votre organisation comporte plus de 50 sièges et participe à un [plan pris en charge](https://technet.microsoft.com/library/dn783224.aspx), vous pouvez profiter des avantages de FastTrack, disponibles sans coût additionnel pour vous guider dans la planification, la migration, le déploiement et l’adoption du service. Vous pouvez aussi effectuer ce travail vous-même à l’aide des assistants d’intégration FastTrack, qui sont disponibles depuis [FastTrack](https://docs.microsoft.com/fasttrack/m365-fasttrack-benefit-overview) lorsque vous vous connectez à votre compte Microsoft 365.

Si vous effectuez votre propre planification (ou conjointement avec FastTrack), vous devez déterminer si votre réseau et votre organisation sont prêts pour SharePoint. Il est particulièrement important que vous répondiez aux critères de sortie réseau dans votre infrastructure de base, avec une attention particulière accordée à la bande passante, au débit et aux retards du trafic afin d’optimiser les performances pour le trafic supplémentaire lié aux documents basés sur SharePoint.

Utilisez ces ressources pour préparer les aspects techniques d’un déploiement SharePoint : 

- [Guide de planification de SharePoint](https://docs.microsoft.com/sharepoint/planning-guide)
- [Migrer vers SharePoint](https://docs.microsoft.com/sharepointmigration/migrate-to-sharepoint-online) 

Pour mieux comprendre la sécurité dans SharePoint, consultez les ressources suivantes :

-   [SharePoint et OneDrive protègent vos données dans le cloud](https://docs.microsoft.com/sharepoint/safeguarding-your-data)
-   [Chiffrement de données dans OneDrive et SharePoint](https://docs.microsoft.com/microsoft-365/compliance/data-encryption-in-odb-and-spo)

#### <a name="result"></a>Résultat

Vous comprenez comment fonctionnent les sites SharePoint, ainsi que la sécurité et la migration des dossiers et des documents en local. De plus, vous êtes prêt à déployer SharePoint sur les groupes sélectionnés dans votre organisation.

### <a name="step-2-run-an-it-pilot"></a>Étape 2 : exécuter une session pilote

Dans la plupart des moyennes et grandes organisations, nous vous conseillons d’exécuter une session pilote avec vos parties prenantes de la phase 1, les adeptes précoces et les amateurs de technique. Pendant la session pilote :

- Choisissez un scénario d’entreprise pour SharePoint dans lequel les participants à votre session pilote peuvent s’exercer.
- Fournissez aux participants de la session pilote un ensemble d’exercices visant à tester le stockage et le partage de documents dans SharePoint, ainsi que la collaboration, la planification d’équipe et d’autres fonctionnalités.
- Déterminez votre stratégie de gestion des modifications et créez des documents pour favoriser l’adoption de SharePoint par les utilisateurs à l’échelle de l’organisation. Les documents relatifs à la gestion des modifications peuvent inclure du texte d'annonce par courrier électronique, des plans de formation interne, des affiches dans les couloirs et des présentations. Ces documents informent votre organisation au sujet de SharePoint et de ses avantages dans le but d'accroître la sensibilisation et de stimuler l'utilisation de SharePoint. Pour consulter quelques idées, reportez-vous à l’article sur la stratégie de gestion des modifications pour [Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/change-management-strategy). 
- Demandez à vos participants au programme pilote informatique de passer en revue les documents relatifs à la gestion des modifications en fonction de leur expérience. Ils peuvent fournir des conseils sur les pratiques recommandées et des conseils sur la manière de décrire au mieux les avantages de SharePoint et comment l’utiliser.

#### <a name="result"></a>Résultat

Votre session pilote SharePoint est terminée et les supports de gestion des modifications de départ ont été développés, révisés et améliorés.

### <a name="step-3-roll-out-to-a-business-group"></a>Étape 3 : déployer pour un groupe d’entreprise

Une fois votre session pilote terminée, déployez SharePoint pour un groupe d’entreprise ou un service de votre organisation. Ce processus de déploiement doit inclure les éléments suivants :

- Identification des scénarios d’entreprise clés pour SharePoint au sein du groupe d’entreprise.
- Annonces pour informer les utilisateurs des attentes et du calendrier relatifs à l’utilisation de SharePoint pour les équipes de service, de travail ou de projet.
- Migration de documents et de dossiers en local des membres de votre groupe d’entreprise vers SharePoint.
- Offrir une formation aux utilisateurs ou des liens vers des ressources qui présentent SharePoint et qui indiquent comment l’utiliser. Consultez la formation vidéo complète sur [SharePoint](https://support.office.com/article/sharepoint-online-video-training-cb8ef501-84db-4427-ac77-ec2009fb8e23).
- Mécanisme de commentaires, comme une équipe Microsoft Teams centrale composée de tous les membres du groupe d’entreprise, pour recueillir les commentaires et résoudre les problèmes des utilisateurs du groupe d’entreprise.
 
Pendant le déploiement, vous pouvez améliorer vos supports de gestion des modifications en vue du processus de déploiement à l’échelle de l’organisation.

#### <a name="result"></a>Résultat

Un groupe d’entreprise est opérationnel avec SharePoint, et les supports de gestion des modifications ont été testés et améliorés.

## <a name="phase-3-drive-value"></a>Phase 3 : créer de la valeur

Dans cette phase, vous terminerez le processus de déploiement de SharePoint et permettez ainsi à vos utilisateurs de prendre conscience de leurs avantages.

### <a name="step-1-roll-out-to-the-rest-of-your-organization"></a>Étape 1 : Effectuer le déploiement dans le reste de votre organisation

Le processus de déploiement dans le reste de votre organisation doit inclure les éléments suivants :

- Identification des scénarios d’entreprise clés pour SharePoint au sein de groupes d’entreprise distincts.
- Utilisation de vos supports de gestion des modifications améliorés pour les annonces afin d’informer votre organisation des attentes et du calendrier relatifs à l’utilisation.
- Migration des dossiers et des documents pour le reste de votre organisation vers SharePoint.
- Formation des utilisateurs ou liens vers des ressources qui présentent SharePoint et qui indiquent comment l’utiliser.
- Mécanisme de commentaires, comme une équipe centrale composée de tous les membres du groupe, pour recueillir les commentaires et traiter les problèmes des utilisateurs de l’organisation. Si votre organisation possède moins de 2 500 collaborateurs, utilisez un canal public dans Teams. Sinon, utilisez un groupe public dans Yammer.

#### <a name="result"></a>Résultat
Votre organisation est opérationnelle et votre stratégie de gestion des modifications est en place pour informer, former et permettre aux utilisateurs de commencer à utiliser SharePoint.

### <a name="step-2-measure-usage-manage-satisfaction-and-drive-adoption"></a>Étape 2 : mesurer l’utilisation, gérer la satisfaction et favoriser l’adoption

Après avoir effectué le déploiement pour toute votre organisation, vous devez continuer à utiliser votre stratégie de gestion des modifications pour :

- Demandez à votre équipe de direction de promouvoir SharePoint comme principal outil de stockage et de partage de documents.
- Encouragez les personnes à l’utiliser pour le stockage et le partage de documents entre les groupes d’entreprises, les départements et les équipes de travail et de projet.

Voici des suggestions d’activités :

- Consultez la page [Facteurs de succès pour Office 365](https://aka.ms/successfactors) pour en savoir plus sur les meilleures pratiques générales relatives à l’adoption du service cloud. 
- Consultez l’article [Rapports d’activité Office 365](https://docs.microsoft.com/office365/admin/activity-reports/activity-reports) pour comprendre l’utilisation des services Office 365 au sein de votre organisation. Si vous n’êtes pas administrateur général Office 365 pour votre organisation, demandez à la personne habilitée de vous accorder les autorisations d’accès en lecture aux rapports pour que vous puissiez accéder aux rapports d’activité.
- Surveillez vos commentaires (un canal public dans une équipe centrale Teams ou Yammer) pour résoudre les problèmes et traiter les commentaires des personnes qui ont des difficultés à utiliser SharePoint. Répondez aux questions et problèmes dans les meilleurs délais afin d'éviter les frustrations et de montrer du soutien dans le cadre du déploiement.
- Identifiez et entretenez les champions de chaque groupe d’entreprises et mettez en évidence leurs réalisations et leurs meilleures pratiques lors de l’utilisation de SharePoint. Faites part de leurs réussites à l'organisation pour montrer le succès et l'adoption du projet. L'appui des responsables techniques au sein d'un groupe d'entreprises peut exercer une forte influence sur la direction et les pairs.

#### <a name="result"></a>Résultat

Votre organisation a adopté SharePoint dans Microsoft 365 Entreprise pour prendre en charge la collaboration et le stockage relatifs aux documents.

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Pour observer de plus près Microsoft et découvrir comment nous avons déployé SharePoint, reportez-vous à l’article [SharePoint dans le cloud : découvrez comment Microsoft a exécuté sa propre migration](https://www.microsoft.com/fr-FR/itshowcase/sharepoint-to-the-cloud-learn-how-microsoft-ran-its-own-migration).

## <a name="next-steps"></a>Étapes suivantes

Consultez ces ressources pour assurer la maintenance permanente de SharePoint : 

- [Présentation des niveaux d’autorisation dans SharePoint](https://docs.microsoft.com/sharepoint/understanding-permission-levels)
- [Personnaliser les autorisations de site SharePoint](https://docs.microsoft.com/sharepoint/customize-sharepoint-site-permissions)
- [Activer ou désactiver le partage externe pour SharePoint](https://docs.microsoft.com/sharepoint/turn-external-sharing-on-or-off)
- [Configurer et gérer les demandes d’accès](https://support.office.com/article/Set-up-and-manage-access-requests-94B26E0B-2822-49D4-929A-8455698654B3)
