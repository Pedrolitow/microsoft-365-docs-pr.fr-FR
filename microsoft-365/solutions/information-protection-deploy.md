---
title: Déployer la protection des informations pour les réglementations sur la confidentialité des données avec Microsoft 365
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/22/2020
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-overview
- zerotrust-solution
ms.custom: admindeeplinkCOMPLIANCE
description: Configurez la protection des informations dans Microsoft 365 pour les réglementations de confidentialité des données telles que le RGPD et le CCPA (California Consumer Privacy Act), notamment Microsoft Teams, SharePoint et le courrier électronique.
ms.openlocfilehash: dd066d3240be5fb3472491b0caa45ea29301af0f
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67731571"
---
# <a name="deploy-information-protection-for-data-privacy-regulations-with-microsoft-365"></a>Déployer la protection des informations pour les réglementations sur la confidentialité des données avec Microsoft 365

Votre organisation peut être soumise à des réglementations régionales de confidentialité des données qui vous obligent à protéger, gérer et fournir des droits et un contrôle sur les informations personnelles stockées dans votre infrastructure informatique, y compris localement et dans le cloud. Le meilleur exemple de réglementation de la confidentialité des données est le Règlement général sur la protection des données (RGPD) de l’Union européenne. Le non-respect des réglementations sur la confidentialité des données peut entraîner des amendes substantielles.

Les sessions de conversation dans Microsoft Teams, les e-mails dans Exchange et les fichiers dans SharePoint et OneDrive sont des exemples de types de données dans Microsoft 365. Cette solution fournit des conseils sur la façon d’évaluer les risques et de prendre les mesures appropriées pour protéger les données personnelles dans Microsoft 365. Cela inclut l’identification des informations personnelles afin que vous puissiez protéger, régir et répondre aux incidents de confidentialité des données.

![Qu’est-ce que la protection des informations pour les réglementations sur la confidentialité des données?](../media/information-protection-deploy/information-protection-data-privacy-regulations-overview.png#lightbox)

Des informations supplémentaires sont également fournies sur l’utilisation des contrôles d’identité, d’appareil et de protection contre les menaces Microsoft 365 pour vos besoins en matière de confidentialité des données.

Regardez cette vidéo de présentation du processus de déploiement.
<br>
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4NHCQ]

Ces fonctionnalités et fonctionnalités Microsoft 365 vous aident à répondre aux critères de protection des informations.

| Fonctionnalité | Description | Licence |
|:-------|:-----|:-------|
| Gestionnaire de conformité | Gérez les activités de conformité réglementaire, obtenez un score global de votre configuration de conformité actuelle et recherchez des recommandations pour l’amélioration. Il s’agit d’un outil d’évaluation des risques basé sur le flux de travail dans le portail de conformité Microsoft Purview. | Microsoft 365 E3 et E5 |
| Microsoft Defender pour Office 365 | Protégez vos applications et données Microsoft 365 (par exemple, messages électroniques, documents Office et outils de collaboration) contre les attaques. | Microsoft 365 E3 et E5 |
| Étiquettes de confidentialité | Classifiez et protégez les données de votre organisation sans entraver la productivité des utilisateurs et leur capacité à collaborer. Placez des étiquettes avec différents niveaux de protection sur les e-mails, les fichiers ou les sites. | Microsoft 365 E3 et E5 |
| Protection contre la perte de données (DLP) | Détecter, avertir et bloquer le partage risqué, par inadvertance ou inapproprié des données contenant des informations personnelles, en interne et en externe. | Microsoft 365 E3 et E5 |
| Étiquettes et stratégies de rétention des données | Implémentez des contrôles de gouvernance des informations. Il peut s’agir de déterminer la durée pendant laquelle les données (telles que les données personnelles relatives aux clients) doivent être conformes aux stratégies ou réglementations de données de votre organisation. | Microsoft 365 E3 et E5 |
| Chiffrement du courrier électronique | Protégez les données personnelles en envoyant et en recevant des messages électroniques chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. | Microsoft 365 E3 et E5 |
||||

## <a name="organization-of-the-guidance-in-this-solution"></a>Organisation des conseils dans cette solution

Pour vous aider à comprendre les outils Microsoft 365 disponibles pour vous aider à respecter une ou plusieurs réglementations liées à la confidentialité, ces conseils sont organisés en sections.

![Étapes d’implémentation de la protection des informations pour les réglementations de confidentialité des données.](../media/information-protection-deploy/information-protection-data-privacy-regulations-steps.png)

Chacune de ces sections correspond à un article distinct de cette solution.

> [!NOTE]
> Si vous êtes déjà familiarisé avec vos obligations en matière de confidentialité des données et que vous vous exécutez sur un plan existant, vous pouvez vous concentrer sur les conseils Prevent, Protect, Retain et Investigate.

> [!IMPORTANT]
> Si vous suivez ces instructions, vous ne serez pas nécessairement conforme aux réglementations en matière de confidentialité des données, en particulier compte tenu du nombre d’étapes requises en dehors du contexte des fonctionnalités. Il vous incombe d’assurer votre conformité et de consulter vos équipes juridiques et de conformité, ou de demander des conseils et des conseils à des tiers spécialisés dans la conformité.

## <a name="plan-assess-data-privacy-risks-and-identify-sensitive-items"></a>Plan : Évaluer les risques liés à la confidentialité des données et identifier les éléments sensibles

L’évaluation des réglementations de confidentialité des données et des risques auxquels votre organisation est soumise est une première étape essentielle avant de commencer à implémenter des améliorations, notamment la configuration des fonctionnalités dans Microsoft 365. Ce travail peut inclure une évaluation globale de la préparation ou l’identification de types d’informations sensibles particuliers soumis aux contrôles réglementaires auxquels votre organisation doit se conformer.

Pour plus d’informations, consultez [Évaluer les risques liés à la confidentialité des données et identifier les éléments sensibles](information-protection-deploy-assess.md).

## <a name="track-run-risk-assessments-and-check-your-compliance-score"></a>Suivi : Exécuter des évaluations des risques et vérifier votre score de conformité

Le Gestionnaire de conformité, disponible dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>, vous offre une capacité intégrée de suivre et de gérer les actions d’amélioration globales, ainsi que celles liées à plusieurs réglementations de confidentialité des données qui s’appliquent à vous.

Vous pouvez utiliser des modèles d’évaluation intégrés spécifiques à chaque règlement, où vous pouvez suivre les éléments d’action pour chaque modèle d’évaluation sélectionné, afficher des contrôles réglementaires spécifiques et les associer à des actions spécifiques.

Pour plus d’informations, consultez [Utiliser le Gestionnaire de conformité pour gérer les actions d’amélioration](information-protection-deploy-compliance.md).

## <a name="prevent-protect-personal-data"></a>Empêcher : protéger les données personnelles

Microsoft 365 fournit des fonctionnalités d’identité, d’appareil et de protection contre les menaces que vous pouvez utiliser pour vous aider à vous conformer à la conformité réglementaire en matière de confidentialité des données.

Pour plus d’informations, consultez [Utiliser la protection des identités, des appareils et des menaces pour la réglementation de la confidentialité des données](information-protection-deploy-identity-device-threat.md).

Cet article décrit brièvement ce que les réglementations sur la confidentialité des données appellent généralement dans ces domaines et fournit une liste des solutions Microsoft 365 associées, avec des liens vers plus d’informations pour vous aider à répondre à toutes les exigences d’implémentation.

## <a name="protect-information-subject-to-data-privacy-regulation"></a>Protéger les informations soumises à la réglementation sur la confidentialité des données

Les réglementations sur la confidentialité des données imposent un certain nombre de contrôles de protection des informations personnelles qui peuvent être utilisés dans votre environnement, y compris plus de 40 contrôles pour la protection des informations sur les quatre réglementations sur la confidentialité des données dans notre exemple de RGPD, la Loi sur la protection des consommateurs de Californie (CCPA), HIPAA-HITECH (Estados Unidos loi sur la confidentialité des soins de santé) et la Loi brésilienne sur la protection des données (LGPD).

Pour plus d’informations, consultez [Protéger les informations soumises à la réglementation sur la confidentialité des données dans votre organisation](information-protection-deploy-protect-information.md).

Cet article présente les principaux schémas de contrôle qui peuvent être utilisés pour répondre aux besoins de protection des informations pour la confidentialité des données dans votre organisation.

## <a name="retain-govern-information-subject-to-data-privacy-regulation"></a>Conserver : régir les informations soumises à la réglementation sur la confidentialité des données

Les réglementations sur la confidentialité des données appellent des contrôles de gouvernance des informations personnelles qui peuvent être utilisés dans votre environnement, y compris plus de 24 contrôles sur les quatre réglementations sur la confidentialité des données dans notre exemple de RGPD, CCPA, HIPAA-HITECH et LGPD.

Pour plus d’informations, consultez [Régir les informations soumises à la réglementation sur la confidentialité des données dans votre organisation](information-protection-deploy-govern.md).

Bien que les réglementations sur la confidentialité des données puissent être vagues en ce qui concerne la gouvernance&mdash;des informations, telles que la conservation, la suppression et l’archivage&mdash;volontaires, cet article présente les principaux schémas de contrôle que vous pouvez utiliser pour répondre aux besoins de gouvernance des informations pour la confidentialité des données dans votre organisation.

## <a name="investigate-monitor-investigate-and-respond-to-data-privacy-incidents"></a>Examiner : surveiller, examiner et répondre aux incidents de confidentialité des données

Des fonctionnalités Microsoft 365 sont disponibles pour vous aider à surveiller, examiner et répondre aux incidents de confidentialité des données au sein de votre organisation lorsque vous mettez en œuvre les fonctionnalités associées.

Il peut être important de disposer de processus, de procédures et d’autres documents pour l’utilisation de ces fonctionnalités pour démontrer la conformité aux organismes de réglementation.

Pour plus d’informations, consultez [Surveiller et répondre aux incidents de confidentialité des données dans votre organisation](information-protection-deploy-monitor-respond.md).

## <a name="training-for-administrators"></a>Formation pour les administrateurs

Ces modules de formation de Microsoft Learn peuvent vous aider à découvrir comment les fonctionnalités qui sont importantes pour la protection des informations.


#### <a name="information-protection"></a>Protection des informations

|Formation :|Protéger les informations d’entreprise avec Microsoft 365|
|:---|:---|
|![Icône d’entraînement de la protection des informations Teams.](../media/protect-enterprise-information-microsoft-365.svg)|Plus que jamais, la protection et la sécurisation des informations de votre organisation constituent un défi. Le chemin d’apprentissage pour protéger les informations d’entreprise avec Microsoft 365 explique comment protéger vos informations sensibles contre tout partage excessif accidentel ou utilisation incorrecte, comment découvrir et classifier des données, comment les protéger à l’aide d’étiquettes de confidentialité et comment surveiller et analyser vos informations sensibles pour les protéger contre la perte. Ce parcours d’apprentissage peut vous aider à préparer les certifications Microsoft 365 Certified: Security Administrator Associate et Microsoft 365 Certified: Enterprise Administration Expert.<br><br>1 heure - Parcours d’apprentissage - 5 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/m365-security-info-overview/introduction/)

#### <a name="identity-and-access"></a>Identité et accès

|Formation :|Protégez l’identité et l’accès avec Azure Active Directory Domain Services|
|:---|:---|
|![Icône d’entraînement d’identité et d’accès.](../media/protect-identity-and-access-with-microsoft-365.svg)|Le parcours d’apprentissage Identité et accès aborde les dernières technologies de gestion des identités et accès, ainsi que les outils de renforcement de l’authentification, et donne des conseils sur la protection des identités au sein de votre organisation. Les technologies de gestion des identités et accès de Microsoft vous permettent de sécuriser l’identité de votre organisation (locale ou dans le cloud) et permettent à vos utilisateurs de travailler en toute sécurité où qu’ils se trouvent. Cette rubrique d’apprentissage peut vous aider à vous préparer aux certifications Certification Microsoft 365 : Administrateur de sécurité associé et Certification Microsoft 365 : Administration entreprise expert.<br><br>2 h 52 min - Parcours d’apprentissage - 6 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/m365-identity-overview/introduction/)