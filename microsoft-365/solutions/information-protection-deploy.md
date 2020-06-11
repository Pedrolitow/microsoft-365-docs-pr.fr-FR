---
title: Déployer la protection des informations pour les réglementations sur la confidentialité des données avec Microsoft 365
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- M365solutions
ms.custom: ''
description: Configurez l’infrastructure de sécurité et de service afin de protéger vos informations et de respecter les réglementations en matière de confidentialité des données.
ms.openlocfilehash: 35ccfb21accd969c2a2cbdddde9a4ec1c7eeed64
ms.sourcegitcommit: b03a7ad0a80f8b839f40b8d396ab3a049491a12f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "44695106"
---
# <a name="deploy-information-protection-for-data-privacy-regulations-with-microsoft-365"></a>Déployer la protection des informations pour les réglementations sur la confidentialité des données avec Microsoft 365

Cette solution fournit des instructions sur la planification et la protection des données personnelles stockées dans les services Microsoft 365 et susceptibles d’être soumises à des réglementations sur la confidentialité des données, telles que le règlement général sur la protection des données de l’Union européenne (RGPD). Cette solution est axée sur les fonctionnalités de conformité et de protection des informations Microsoft applicables, le score de conformité Microsoft et les outils d’évaluation pour vous aider à savoir vos données. 
 
Des informations supplémentaires sont également fournies sur l’utilisation des contrôles Microsoft Identity, Device et protection contre les menaces pour répondre à vos besoins en matière de confidentialité des données, ainsi qu’aux outils de détection et de réponse aux incidents de données. 

## <a name="organization-of-this-guidance-material"></a>Organisation de ce guide

Pour vous aider à comprendre les outils Microsoft 365 disponibles pour identifier, gérer, contrôler et surveiller les données personnelles soumises à une ou plusieurs réglementations liées à la confidentialité, ces instructions sont organisées en sections.
 
![Déployer la protection des informations pour la confidentialité des données](../media/information-protection-deploy/information-protection-deploy-grid.png)

Chacune de ces sections correspond à un article distinct de cette solution.

>[!Note]
>Si vous êtes déjà familiarisé avec vos obligations de confidentialité des données et que vous exécutez votre projet sur une offre existante, vous souhaiterez peut-être vous concentrer sur les instructions de prévention, de protection, de rétention et d’enquête.

>[!Important]
>Ce guide ne vous permettra pas de vous conformer à la réglementation relative à la confidentialité des données, notamment en tenant compte du nombre d’étapes requises en dehors du contexte des fonctionnalités. Vous êtes chargé de vous assurer de votre conformité et de consulter vos équipes juridiques et de conformité, ou de rechercher des conseils et des conseils de tiers spécialisés en matière de conformité.
>

## <a name="plan-assess-data-privacy-risks-and-identify-sensitive-items"></a>Plan : évaluer les risques de confidentialité des données et identifier les éléments sensibles 

L’évaluation des réglementations et des risques de confidentialité des données dont votre organisation est soumise est une première étape essentielle avant de commencer à implémenter les améliorations, notamment celles réalisables via la configuration Microsoft 365. Cela peut inclure une évaluation de la disponibilité globale ou l’identification d’un type d’informations sensibles particulier soumis aux contrôles réglementaires dont votre organisation a besoin pour se conformer, ainsi qu’à l’occurrence de celles-ci dans votre environnement Microsoft 365.

Pour plus d’informations, consultez la rubrique [évaluation des risques de confidentialité des données et identification des éléments sensibles](information-protection-deploy-assess.md).

## <a name="track-use-compliance-score-and-compliance-manager"></a>Track : utiliser le score de conformité et le gestionnaire de conformité 

Le score de conformité et le gestionnaire de conformité fournissent un ensemble intégré d’outils disponibles dans le centre d’administration de la conformité Microsoft 365 et le portail d’approbation des services. Ensemble, ces outils vous permettent de suivre et de gérer les actions d’amélioration en général, ainsi que celles liées à plusieurs réglementations de confidentialité auxquelles vous êtes soumis.

Les outils vous permettent également d’utiliser des modèles d’évaluation intégrés spécifiques à chaque règle, qui vous permettent de suivre les éléments d’action pour chaque modèle d’évaluation sélectionné, ainsi que d’afficher des contrôles de réglementation spécifiques et de les associer à des actions spécifiques.

Pour plus d’informations, consultez [la rubrique utiliser le score de conformité et le gestionnaire de conformité pour gérer les actions d’amélioration](information-protection-deploy-compliance.md).

## <a name="prevent-use-identity-device-and-threat-protection-for-data-privacy-regulation"></a>Empêcher : utiliser l’identité, l’appareil et la protection contre les menaces pour le règlement de confidentialité des données

Microsoft 365 fournit un certain nombre de fonctionnalités d’identité, de protection des appareils et de protection contre les menaces que vous pouvez utiliser pour vous conformer à la conformité réglementaire des données en matière de confidentialité des données. 

Pour plus d’informations, voir [use Identity, Device, and Threat Protection for Data Privacy Regulation](information-protection-deploy-identity-device-threat.md).

Cet article décrit brièvement ce que les réglementations en matière de confidentialité des données appellent généralement dans ces domaines et fournit une liste de solutions Microsoft 365 connexes, ainsi que des liens vers des informations supplémentaires pour vous aider à répondre aux exigences de mise en œuvre. 

## <a name="protect-information-subject-to-data-privacy-regulation"></a>Protéger les informations soumises au règlement de confidentialité des données

Les réglementations sur la confidentialité des données imposent un certain nombre de contrôles de protection des informations personnelles qui peuvent être employés dans votre environnement, dont plus de 40 protéger les contrôles des informations sur les quatre réglementations de confidentialité des données de notre exemple de RGPD, California Consumer Protection Act (CCPA), HIPAA-Hi (United Health Care Privacy Act) et le Brésil (Data Protection Act).

Pour plus d’informations, consultez [la rubrique protection des informations soumises au règlement de confidentialité des données dans votre organisation](information-protection-deploy-protect-information.md).

Cet article présente les principaux modèles de contrôle qui peuvent être utilisés pour répondre aux besoins en matière de protection des informations pour la confidentialité des données dans votre organisation.

## <a name="retain-govern-information-subject-to-data-privacy-regulation"></a>Conserver : régit les informations soumises au règlement de confidentialité des données

Les réglementations relatives à la confidentialité des données appellent des contrôles de la gouvernance des informations personnelles qui peuvent être employés dans votre environnement, dont plus de vingt-quatre contrôles parmi les quatre réglementations de confidentialité des données dans notre ensemble d’exemples de RGPD, CCPA, HIPAA-Hi et LGPD.

Pour plus d’informations, consultez la rubrique gestion des [informations relatives au règlement de confidentialité des données dans votre organisation](information-protection-deploy-govern.md).

Bien que les réglementations relatives à la confidentialité des données puissent être vagues en matière de gouvernance des informations &mdash; , telles que la rétention volontaire, la suppression et l’archivage &mdash; cet article présente les principaux modèles de contrôle que vous pouvez utiliser pour la confidentialité des données dans votre organisation.

## <a name="investigate-monitor-and-respond-subject-to-data-privacy-regulation"></a>Enquête : surveiller et répondre à l’objet du règlement sur la confidentialité des données

Les fonctionnalités de Microsoft 365 sont disponibles pour vous aider à surveiller, examiner et répondre aux incidents de confidentialité des données au sein de votre organisation lorsque vous avez opérationnel les fonctionnalités connexes. 

L’existence de processus, de procédures et d’autres documents pour chacun de ces éléments peut être importante pour prouver la conformité aux organismes de réglementation.

Pour plus d’informations, consultez [la rubrique surveiller et répondre aux incidents de confidentialité des données dans votre organisation](information-protection-deploy-monitor-respond.md).
