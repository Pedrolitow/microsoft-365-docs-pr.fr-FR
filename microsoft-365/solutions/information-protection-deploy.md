---
title: Déployer la protection des informations pour les réglementations en matière de confidentialité des données avec Microsoft 365
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/22/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-overview
ms.custom: ''
description: Configurez l’infrastructure de sécurité et de service pour protéger vos informations et respecter les réglementations en matière de confidentialité des données.
ms.openlocfilehash: 9af0a113d9b0eb2cbca07fdf457cd8bb7db3e094
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48842295"
---
# <a name="deploy-information-protection-for-data-privacy-regulations-with-microsoft-365"></a>Déployer la protection des informations pour les réglementations en matière de confidentialité des données avec Microsoft 365

Votre organisation peut être soumise à des réglementations régionales en matière de confidentialité des données qui vous obligent à protéger, gérer et fournir des droits et un contrôle sur les informations personnelles stockées dans votre infrastructure informatique, y compris localement et dans le cloud. Le meilleur exemple de règlement sur la confidentialité des données est le Règlement général sur la protection des données (R GDPR) de l’Union européenne. Le non-respect des réglementations en matière de confidentialité des données peut entraîner des amendes importantes.

Les sessions de conversation dans Microsoft Teams, les e-mails dans Exchange et les fichiers dans SharePoint et OneDrive sont des exemples de types de données dans Microsoft 365. Cette solution fournit des conseils sur l’évaluation des risques et l’identification des informations, la protection, la gouvernance et la réponse aux incidents de confidentialité des données pour les données personnelles stockées dans les services Microsoft 365 soumis aux réglementations en matière de confidentialité des données.

![Qu’est-ce que la protection des informations pour les réglementations en matière de confidentialité des données ?](../media/information-protection-deploy/information-protection-data-privacy-regulations-overview.png)

Des informations supplémentaires sont également fournies sur l’utilisation des contrôles d’identité, d’appareil et de protection contre les menaces Microsoft 365 pour vos besoins en matière de confidentialité des données. 

Pour répondre aux critères de protection des informations en conformité avec les réglementations en matière de confidentialité des données, utilisez ces fonctionnalités et fonctionnalités Microsoft 365.

| Fonctionnalité | Description | Licence |
|:-------|:-----|:-------|
| Gestionnaire de conformité | Gérez les activités de conformité réglementaire, obtenez un score global de votre configuration de conformité actuelle et trouvez des recommandations pour améliorer cet outil d’évaluation des risques basé sur les flux de travail dans le Centre de conformité Microsoft 365. | Microsoft 365 E3 et E5 |
| Microsoft Defender pour Office 365 | Protégez vos applications et données Microsoft 365 (par exemple, messages électroniques, documents Office et outils de collaboration) contre les attaques. | Microsoft 365 E3 et E5 | 
| Étiquettes de confidentialité | Classifiez et protégez les données de votre organisation sans entraver la productivité des utilisateurs ni leur capacité à collaborer en plaçant des étiquettes avec différents niveaux de protection sur les messages électroniques, les fichiers et les sites. | Microsoft 365 E3 et E5 |
| Protection contre la perte de données (DLP) | Détectez, signalez et bloquez le partage risqué, accidentel ou inapproprié, tel que le partage de données contenant des informations personnelles, à la fois en interne et en externe. | Microsoft 365 E3 et E5 | 
| Étiquettes et stratégies de rétention des données | Mettez en place des contrôles de gouvernance des informations, tels que la durée de conservation des données ainsi que des exigences sur le stockage de données personnelles sur les clients, pour vous conformer aux stratégies de votre organisation ou aux réglementations relatives aux données. | Microsoft 365 E3 et E5 |
| Chiffrement du courrier électronique | Envoyez et recevez entre des personnes à l’intérieur et à l’extérieur de votre organisation des messages électroniques chiffrés qui contiennent des données réglementées, telles que des données personnelles relatives aux clients. | Microsoft 365 E3 et E5 |
||||

## <a name="organization-of-the-guidance-in-this-solution"></a>Organisation des conseils dans cette solution

Pour vous aider à comprendre les outils Microsoft 365 disponibles pour identifier, gérer, contrôler et surveiller les données personnelles soumises à une ou plusieurs réglementations en matière de confidentialité, ces instructions sont organisées en sections.
 
![Étapes de mise en œuvre de la protection des informations pour les réglementations en matière de confidentialité des données](../media/information-protection-deploy/information-protection-data-privacy-regulations-steps.png)

Chacune de ces sections correspond à un article distinct de cette solution.

>[!Note]
>Si vous êtes déjà familiarisé avec vos obligations en matière de confidentialité des données et que vous vous exécutez par rapport à un plan existant, vous souhaitez peut-être vous concentrer sur les recommandations relatives à la prévention, à la protection, à la rétention et à l’examen.

>[!Important]
>Le fait de suivre ces instructions ne vous permettra pas nécessairement de vous conformer à une réglementation en matière de confidentialité des données, en particulier en raison du nombre d’étapes requises en dehors du contexte des fonctionnalités. Vous êtes chargé de garantir votre conformité et de consulter vos équipes juridiques et de conformité, ou de rechercher des conseils et des conseils auprès de tiers spécialisés dans la conformité.
>

## <a name="plan-assess-data-privacy-risks-and-identify-sensitive-items"></a>Plan : évaluer les risques de confidentialité des données et identifier les éléments sensibles

L’évaluation des réglementations et des risques liés à la confidentialité des données auxquels votre organisation est soumise est une première étape essentielle à prendre avant de commencer à implémenter des améliorations, y compris celles réalisables par le biais de la configuration de Microsoft 365. Cela peut inclure une évaluation globale de la préparation ou l’identification de types d’informations sensibles particuliers soumis à des contrôles réglementaires que votre organisation doit respecter, ainsi que leur occurrence dans votre environnement Microsoft 365.

Pour plus d’informations, voir [Évaluer les risques de confidentialité des données et identifier les éléments sensibles.](information-protection-deploy-assess.md)

## <a name="track-run-risk-assessments-and-check-your-compliance-score"></a>Suivi : exécuter des évaluations des risques et vérifier votre score de conformité

Le Gestionnaire de conformité, disponible dans le Centre de conformité Microsoft 365, vous offre la possibilité intégrée de suivre et de gérer les actions d’amélioration globales, ainsi que celles liées à plusieurs réglementations en matière de confidentialité des données qui vous sont applicables.

Tirez parti des modèles d’évaluation intégrés spécifiques à chaque réglementation, où vous pouvez suivre les éléments d’action pour chaque modèle d’évaluation sélectionné, ainsi que visualiser des contrôles réglementaires spécifiques et les mettre en relation avec des actions spécifiques.

Pour plus d’informations, voir [Utiliser le Gestionnaire de conformité pour gérer les actions d’amélioration.](information-protection-deploy-compliance.md)

## <a name="prevent-protect-personal-data"></a>Empêcher : protéger les données personnelles

Microsoft 365 fournit un certain nombre de fonctionnalités de protection contre les menaces, les appareils et les identités que vous pouvez utiliser pour vous conformer à la réglementation en matière de confidentialité des données. 

Pour plus d’informations, voir [Utiliser l’identité, l’appareil](information-protection-deploy-identity-device-threat.md)et la protection contre les menaces pour la réglementation sur la confidentialité des données.

Cet article décrit brièvement ce que les réglementations en matière de confidentialité des données appellent généralement dans ces domaines et fournit une liste des solutions Microsoft 365 associées, avec des liens vers des informations supplémentaires pour vous aider à répondre aux exigences d’implémentation. 

## <a name="protect-information-subject-to-data-privacy-regulation"></a>Protéger les informations soumises à la réglementation sur la confidentialité des données

Les réglementations en matière de confidentialité des données dictent un certain nombre de contrôles de protection des informations personnelles qui peuvent être utilisés dans votre environnement, y compris plus de trente contrôles de protection des informations parmi les quatre réglementations de confidentialité des données dans notre exemple de RGPD, le CCPA (California Consumer Protection Act), HIPAA-HITECH (Loi américaine sur la confidentialité des soins de santé) et le LGPD (Brazil Data Protection Act).

Pour plus d’informations, voir Protéger les informations soumises à la réglementation sur la confidentialité des données [dans votre organisation.](information-protection-deploy-protect-information.md)

Cet article présente les principaux schémas de contrôle qui peuvent être utilisés pour répondre aux besoins de protection des informations en matière de confidentialité des données dans votre organisation.

## <a name="retain-govern-information-subject-to-data-privacy-regulation"></a>Rétention : régir les informations soumises à la réglementation sur la confidentialité des données

Les réglementations en matière de confidentialité des données appellent des contrôles de gouvernance des informations personnelles qui peuvent être utilisés dans votre environnement, y compris plus de vingt-quatre contrôles parmi les quatre réglementations en matière de confidentialité des données dans notre exemple d’ensemble de RGPD, CCPA, HIPAA-HITECH et LGPD.

Pour plus d’informations, voir [Govern information subject to data privacy regulation in your organization.](information-protection-deploy-govern.md)

Bien que les réglementations en matière de confidentialité des données soient floues en matière de gouvernance des informations, telles que la rétention, la suppression et l’archivage délibérés, cet article présente les principaux schémas de contrôle que vous pouvez utiliser pour répondre aux besoins de gouvernance des informations pour la confidentialité des données dans votre &mdash; &mdash; organisation.

## <a name="investigate-monitor-investigate-and-respond-to-data-privacy-incidents"></a>Examiner : surveiller, examiner et répondre aux incidents de confidentialité des données

Des fonctionnalités de Microsoft 365 sont disponibles pour vous aider à surveiller, examiner et répondre aux incidents de confidentialité des données au niveau de votre organisation au cours de l’opérationnalisation des fonctionnalités associées. 

Il peut être important d’avoir des processus, des procédures et d’autres documents pour chacun d’eux pour démontrer la conformité aux organismes de réglementation.

Pour plus d’informations, voir [Surveiller et répondre aux incidents](information-protection-deploy-monitor-respond.md)de confidentialité des données dans votre organisation.
