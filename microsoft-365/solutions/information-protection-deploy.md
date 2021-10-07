---
title: Déployer la protection des informations pour les réglementations en matière de confidentialité des Microsoft 365
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/22/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-overview
ms.custom: ''
description: Configurez la protection des informations dans Microsoft 365 pour les réglementations en matière de confidentialité des données telles que le R GDPR et le CCPA (California Consumer Privacy Act), y compris Microsoft Teams, SharePoint et la messagerie électronique.
ms.openlocfilehash: 49d5848c6b81dcd6a81377cc3ff83cb242354690
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60213372"
---
# <a name="deploy-information-protection-for-data-privacy-regulations-with-microsoft-365"></a>Déployer la protection des informations pour les réglementations en matière de confidentialité des Microsoft 365

Votre organisation peut être soumise à des réglementations régionales en matière de confidentialité des données qui vous obligent à protéger, gérer et fournir des droits et un contrôle sur les informations personnelles stockées dans votre infrastructure informatique, y compris localement et dans le cloud. Le meilleur exemple de règlement sur la confidentialité des données est le Règlement général sur la protection des données (R GDPR) de l’Union européenne. Le non-respect des réglementations en matière de confidentialité des données peut entraîner des amendes importantes.

Les sessions de conversation en Microsoft Teams, les e-mails dans les Exchange et les fichiers dans SharePoint et OneDrive sont des exemples de types de données dans Microsoft 365. Cette solution fournit des conseils sur la façon d’évaluer les risques et de prendre les mesures appropriées pour protéger les données personnelles Microsoft 365. Cela inclut l’identification des informations personnelles afin que vous pouvez protéger, régir et répondre aux incidents de confidentialité des données.

![Qu’est-ce que la protection des informations pour les réglementations en matière de confidentialité des données ?](../media/information-protection-deploy/information-protection-data-privacy-regulations-overview.png#lightbox)

Des informations supplémentaires sont également fournies sur l’utilisation Microsoft 365 contrôles d’identité, d’appareil et de protection contre les menaces pour vos besoins en matière de confidentialité des données.

Regardez cette vidéo de présentation du processus de déploiement.
<br>
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4NHCQ]

Ces Microsoft 365 et fonctionnalités vous aident à répondre aux critères de protection des informations.

| Fonctionnalité | Description | Licence |
|:-------|:-----|:-------|
| Gestionnaire de conformité | Gérez les activités de conformité réglementaire, obtenez un score global de votre configuration de conformité actuelle et trouvez des recommandations pour l’amélioration. Il s’agit d’un outil d’évaluation des risques basé sur un flux de travail dans le Centre de conformité Microsoft 365. | Microsoft 365 E3 et E5 |
| Microsoft Defender pour Office 365 | Protégez vos applications et données Microsoft 365 (par exemple, messages électroniques, documents Office et outils de collaboration) contre les attaques. | Microsoft 365 E3 et E5 |
| Étiquettes de confidentialité | Classifiez et protégez les données de votre organisation sans entraver la productivité des utilisateurs et leur capacité à collaborer. Placez des étiquettes avec différents niveaux de protection sur le courrier électronique, les fichiers ou les sites. | Microsoft 365 E3 et E5 |
| Protection contre la perte de données (DLP) | Détecter, avertir et bloquer le partage risqué, involontaire ou inapproprié de données contenant des informations personnelles, à la fois en interne et en externe. | Microsoft 365 E3 et E5 |
| Étiquettes et stratégies de rétention des données | Implémenter des contrôles de gouvernance des informations. Il peut s’agir de déterminer la durée de la gestion des données (telles que les données personnelles liées aux clients) pour se conformer aux stratégies ou réglementations de votre organisation en matière de données. | Microsoft 365 E3 et E5 |
| Chiffrement du courrier électronique | Protégez les données personnelles en envoyant et en recevant des messages électroniques chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. | Microsoft 365 E3 et E5 |
||||

## <a name="organization-of-the-guidance-in-this-solution"></a>Organisation des conseils dans cette solution

Pour vous aider à comprendre les outils Microsoft 365 disponibles pour vous aider à respecter une ou plusieurs réglementations en matière de confidentialité, ces instructions sont organisées en sections.

![Étapes de mise en œuvre de la protection des informations pour les réglementations en matière de confidentialité des données.](../media/information-protection-deploy/information-protection-data-privacy-regulations-steps.png)

Chacune de ces sections correspond à un article distinct de cette solution.

> [!NOTE]
> Si vous êtes déjà familiarisé avec vos obligations en matière de confidentialité des données et que vous vous exécutez par rapport à un plan existant, vous souhaitez peut-être vous concentrer sur les recommandations relatives à la prévention, à la protection, à la rétention et à l’examen.

> [!IMPORTANT]
> Le fait de suivre ces instructions ne vous permettra pas nécessairement de vous conformer à une réglementation en matière de confidentialité des données, en particulier en raison du nombre d’étapes requises en dehors du contexte des fonctionnalités. Vous êtes chargé de garantir votre conformité et de consulter vos équipes juridiques et de conformité, ou de rechercher des conseils et des conseils auprès de tiers spécialisés dans la conformité.

## <a name="plan-assess-data-privacy-risks-and-identify-sensitive-items"></a>Plan : évaluer les risques de confidentialité des données et identifier les éléments sensibles

L’évaluation des réglementations et des risques en matière de confidentialité des données auxquels votre organisation est soumise est une première étape essentielle à prendre avant de commencer à implémenter des améliorations, y compris la configuration des fonctionnalités dans Microsoft 365. Ce travail peut inclure une évaluation globale de la préparation ou l’identification de types d’informations sensibles particuliers soumis à des contrôles réglementaires que votre organisation doit respecter.

Pour plus d’informations, voir [Évaluer les risques de confidentialité des données et identifier les éléments sensibles.](information-protection-deploy-assess.md)

## <a name="track-run-risk-assessments-and-check-your-compliance-score"></a>Suivi : exécuter des évaluations des risques et vérifier votre score de conformité

Le Gestionnaire de conformité, disponible dans le Centre de conformité Microsoft 365, vous offre la possibilité intégrée de suivre et de gérer les actions d’amélioration globales, ainsi que celles liées à plusieurs réglementations en matière de confidentialité des données qui vous sont applicables.

Vous pouvez utiliser des modèles d’évaluation intégrés spécifiques à chaque réglementation, où vous pouvez suivre les éléments d’action pour chaque modèle d’évaluation sélectionné, afficher des contrôles réglementaires spécifiques et les mettre en relation avec des actions spécifiques.

Pour plus d’informations, voir [Utiliser le Gestionnaire de conformité pour gérer les actions d’amélioration.](information-protection-deploy-compliance.md)

## <a name="prevent-protect-personal-data"></a>Empêcher : protéger les données personnelles

Microsoft 365 offre des fonctionnalités de protection contre les menaces, les appareils et les identités que vous pouvez utiliser pour vous conformer à la réglementation en matière de confidentialité des données.

Pour plus d’informations, voir [Utiliser l’identité, l’appareil](information-protection-deploy-identity-device-threat.md)et la protection contre les menaces pour la réglementation sur la confidentialité des données.

Cet article décrit brièvement ce que les réglementations en matière de confidentialité des données appellent généralement dans ces domaines et fournit une liste des solutions Microsoft 365 associées, avec des liens vers plus d’informations pour vous aider à répondre aux exigences d’implémentation.

## <a name="protect-information-subject-to-data-privacy-regulation"></a>Protéger les informations soumises à la réglementation sur la confidentialité des données

Les réglementations en matière de confidentialité des données dictent un certain nombre de contrôles de protection des informations personnelles qui peuvent être utilisés dans votre environnement, notamment plus de 40 contrôles pour la protection des informations dans le cadre des quatre réglementations de confidentialité des données dans notre exemple d’ensemble de RGPD, CCPA (California Consumer Protection Act), HIPAA-HITECH (Loi américaine sur la protection des données) et LGPD (Brazil Data Protection Act).

Pour plus d’informations, voir Protéger les informations soumises à la réglementation sur la confidentialité [des données dans votre organisation.](information-protection-deploy-protect-information.md)

Cet article présente les principaux schémas de contrôle qui peuvent être utilisés pour répondre aux besoins de protection des informations en matière de confidentialité des données dans votre organisation.

## <a name="retain-govern-information-subject-to-data-privacy-regulation"></a>Rétention : régir les informations soumises à la réglementation sur la confidentialité des données

Les réglementations en matière de confidentialité des données appellent des contrôles de gouvernance des informations personnelles qui peuvent être utilisés dans votre environnement, y compris plus de 24 contrôles parmi les quatre réglementations en matière de confidentialité des données dans notre exemple d’ensemble de RGPD, CCPA, HIPAA-HITECH et LGPD.

Pour plus d’informations, voir [Govern information subject to data privacy regulation in your organization.](information-protection-deploy-govern.md)

Bien que les réglementations en matière de confidentialité des données soient floues en matière de gouvernance des informations, telles que la rétention, la suppression et l’archivage délibérés, cet article présente les principaux schémas de contrôle que vous pouvez utiliser pour répondre aux besoins de gouvernance des informations pour la confidentialité des données dans votre &mdash; &mdash; organisation.

## <a name="investigate-monitor-investigate-and-respond-to-data-privacy-incidents"></a>Examiner : surveiller, examiner et répondre aux incidents de confidentialité des données

Des fonctionnalités Microsoft 365 disponibles pour vous aider à surveiller, examiner et répondre aux incidents de confidentialité des données au niveau de votre organisation au cours de l’opérationnalisation des fonctionnalités associées.

La mise en place de processus, de procédures et d’autres documents pour l’utilisation de ces fonctionnalités peut être important pour démontrer la conformité aux organismes de réglementation.

Pour plus d’informations, voir [Surveiller et répondre aux incidents](information-protection-deploy-monitor-respond.md)de confidentialité des données dans votre organisation.

## <a name="training-for-administrators"></a>Formation pour les administrateurs

Ces modules de formation de Microsoft Learn peuvent vous aider à découvrir les fonctionnalités importantes pour la protection des informations.


#### <a name="information-protection"></a>Protection des informations

|Formation :|Protéger les informations d’entreprise avec Microsoft 365|
|:---|:---|
|![Teams de formation sur la protection des informations.](../media/protect-enterprise-information-microsoft-365.svg)|Plus que jamais, la protection et la sécurisation des informations de votre organisation constituent un défi. Le chemin d’apprentissage pour protéger les informations d’entreprise avec Microsoft 365 explique comment protéger vos informations sensibles contre tout partage excessif accidentel ou utilisation incorrecte, comment découvrir et classifier des données, comment les protéger à l’aide d’étiquettes de confidentialité et comment surveiller et analyser vos informations sensibles pour les protéger contre la perte. Ce parcours d’apprentissage peut vous aider à vous préparer à la certification Microsoft 365 certification : associé administrateur de sécurité et Microsoft 365 certifié : Enterprise certifications expertes en administration.<br><br>1 h - chemin d Learning - 5 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/m365-security-info-overview/introduction/)

#### <a name="identity-and-access"></a>Identité et accès

|Formation :|Protégez l’identité et l’accès avec Azure Active Directory Domain Services|
|:---|:---|
|![Icône De formation identité et accès.](../media/protect-identity-and-access-with-microsoft-365.svg)|Le parcours d’apprentissage Identité et accès aborde les dernières technologies de gestion des identités et accès, ainsi que les outils de renforcement de l’authentification, et donne des conseils sur la protection des identités au sein de votre organisation. Les technologies de gestion des identités et accès de Microsoft vous permettent de sécuriser l’identité de votre organisation (locale ou dans le cloud) et permettent à vos utilisateurs de travailler en toute sécurité où qu’ils se trouvent. Cette rubrique d’apprentissage peut vous aider à vous préparer aux certifications Certification Microsoft 365 : Administrateur de sécurité associé et Certification Microsoft 365 : Administration entreprise expert.<br><br>2 h 52 min - Learning chemin d’accès - 6 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/m365-identity-overview/introduction/)