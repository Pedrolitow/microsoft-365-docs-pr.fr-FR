---
title: Planifier la gestion des risques Insider
description: Découvrez comment planifier l’utilisation des stratégies de gestion des risques internes dans votre organisation.
keywords: Microsoft 365, risques internes, gestion des risques, conformité
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 3a1a2fcebdc097b1402d866a2af59d3caac633d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315594"
---
# <a name="plan-for-insider-risk-management"></a>Planifier la gestion des risques Insider

Avant de commencer à [](insider-risk-management.md) gérer les risques internes dans votre organisation, il existe d’importantes activités de planification et des considérations qui doivent être examinées par vos équipes de gestion des technologies de l’information et de la conformité. Une compréhension approfondie et la planification du déploiement dans les domaines suivants vous aideront à vous assurer que votre implémentation et votre utilisation des fonctionnalités de gestion des risques internes se déroulent sans problème et sont conformes aux meilleures pratiques pour la solution.

Regardez la vidéo ci-dessous pour découvrir comment le flux de travail de gestion des risques internes peut aider votre organisation à prévenir, détecter et contenir des risques tout en hiérbant les valeurs, la culture et l’expérience utilisateur de votre organisation :
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

## <a name="work-with-stakeholders-in-your-organization"></a>Travailler avec les parties prenantes de votre organisation

Identifiez les parties prenantes appropriées dans votre organisation pour collaborer pour prendre des mesures sur les alertes et les cas de gestion des risques internes. Certaines parties prenantes recommandées à envisager, y compris dans la planification initiale et le flux [](insider-risk-management.md#workflow) de travail de gestion des risques internes de bout en bout, sont les personnes des zones suivantes de votre organisation :

- Technologie de l’information
- Conformité
- Confidentialité
- Sécurité
- Ressources humaines
- Informations juridiques

## <a name="determine-any-regional-compliance-requirements"></a>Déterminer les exigences de conformité régionale

Différentes zones géographiques et organisationnelles peuvent avoir des exigences de conformité et de confidentialité différentes des autres zones de votre organisation. Travaillez en équipe avec les parties prenantes dans ces domaines pour vous assurer qu’elles comprennent les contrôles de conformité et de confidentialité dans la gestion des risques internes et comment elles doivent être utilisées dans différents domaines de votre organisation. Dans certains scénarios, les exigences de conformité et de confidentialité peuvent nécessiter des stratégies qui désignent ou limitent certaines parties prenantes à des enquêtes et des cas basés sur le cas d’un utilisateur, d’exigences réglementaires ou de stratégies pour la zone.

Si vous avez besoin que des parties prenantes spécifiques soient impliquées dans des enquêtes de cas qui impliquent des utilisateurs de certaines régions, rôles ou divisions, vous pouvez implémenter des stratégies distinctes (même identiques [) de](insider-risk-management-policies.md) gestion des risques internes ciblant les différentes régions et régions. Cette configuration permettra aux parties prenantes de trier et de gérer plus facilement les cas pertinents pour leurs rôles et régions. En outre, vous pouvez envisager de créer des processus et des stratégies pour les régions où les enquêteurs et les réviseurs parlent la même langue que les utilisateurs pour simplifier le processus d’escalade pour les alertes et les cas de gestion des risques internes.

## <a name="plan-for-the-review-and-investigation-workflow"></a>Planifier le flux de travail de révision et d’examen

Selon la façon dont vous souhaitez gérer les stratégies et les alertes de gestion des risques internes, vous devez affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de gestion des risques internes. Vous avez la possibilité d’affecter des utilisateurs ayant différentes responsabilités de conformité à des groupes de rôles spécifiques pour gérer différents domaines de fonctionnalités de gestion des risques internes. Vous pouvez également décider d’affecter tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et visionneuses désignés au groupe de rôles Gestion des risques internes. Utilisez un ou plusieurs groupes de rôles pour mieux vous adapter à vos exigences de gestion de la conformité.

Vous aurez le choix entre ces options de groupe de rôles et les actions de solution lorsque vous travaillerez avec la gestion des risques internes :

|**Actions**|**Gestion des risques internes**|**Administrateur de la gestion des risques internes**|**Analystes de la gestion des risques internes.**|**Enquêteurs sur la gestion des risques internes.**|**Auditeurs de gestion des risques internes**|
|:----------|:--------------------------|:--------------------------------|:-----------------------------------|:----------------------------------------|:-----------------------------------|
| Configurer les stratégies et les paramètres | Oui | Oui | Non | Non | Non |
| Informations d’analyse d’accès | Oui | Oui | Oui | Non | Non |
| Accéder aux & examiner les alertes | Oui | Non | Oui | Oui | Non |
| Accéder aux & cas | Oui | Non | Oui | Oui | Non |
| Accéder & afficher l’Explorateur de contenu | Oui | Non | Non | Oui | Non |
| Configurer des modèles d’avis | Oui | Non | Oui | Oui | Non |
| Afficher les journaux d& exporter | Oui | Non | Non | Non | Oui |

>[!IMPORTANT]
>Assurez-vous que vous avez toujours au moins un utilisateur  dans les groupes de  rôles Gestion des risques internes ou Administrateur de la gestion des risques internes (selon l’option que vous choisissez) afin que votre configuration de gestion des risques internes n’entre pas dans un scénario « administrateur zéro » si des utilisateurs spécifiques quittent votre organisation.

Les membres des rôles suivants peuvent affecter des utilisateurs à des groupes de rôles de gestion des risques internes et  avoir les mêmes autorisations de solution incluses avec le groupe de rôles Administrateur de la gestion des risques internes :

- Administrateur général Azure Active *Directory*
- Administrateur de conformité Azure Active *Directory*
- Centre de conformité Microsoft 365 *Gestion de l’organisation*
- Administrateur de conformité *du Centre de* conformité Microsoft 365

## <a name="understand-requirements-and-dependencies"></a>Comprendre les exigences et les dépendances

Selon la façon dont vous prévoyez d’implémenter des stratégies de gestion des risques internes, vous devez avoir les abonnements aux licences Microsoft 365 appropriés et comprendre et planifier certaines conditions préalables de solution.

**Licences :** La gestion des risques internes est disponible dans le cadre d’un large éventail d’abonnements aux licences Microsoft 365. Pour plus d’informations, consultez l’article Prise [en charge de la gestion des risques internes](insider-risk-management-configure.md#subscriptions-and-licensing) .

> [!IMPORTANT]
> La gestion des risques internes est actuellement disponible dans les clients hébergés dans des régions géographiques et des pays pris en charge par les dépendances de service Azure. Pour vérifier que la gestion des risques internes est prise en charge pour votre organisation, consultez disponibilité des dépendances [Azure par pays/région](/troubleshoot/azure/general/dependency-availability-by-country).

Si vous n’avez pas d’offre Microsoft 365 Entreprise E5 existante et que vous souhaitez essayer la gestion des risques internes, vous pouvez ajouter [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant [](https://www.microsoft.com/microsoft-365/enterprise) ou vous inscrire à une version d’évaluation de Microsoft 365 Entreprise E5.

**Conditions requises pour les modèles de stratégie :** Selon le modèle de stratégie que vous choisissez, il existe des exigences que vous devez comprendre et planifier avant de configurer la gestion des risques internes dans votre organisation :

- Lorsque vous utilisez  le modèle de vol de données par des utilisateurs qui quittent le modèle, vous devez configurer un connecteur Microsoft 365 HR pour importer régulièrement les informations de date de résiliation et de résiliation pour les utilisateurs de votre organisation. Consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) pour obtenir des conseils détaillés pour configurer le connecteur Microsoft 365 RH au sein de votre organisation.
- Lorsque vous utilisez des **modèles de fuites** de données, vous devez configurer au moins une stratégie de protection contre la perte de données (DLP) pour définir des informations sensibles dans votre organisation et recevoir des alertes de risques internes pour les alertes de stratégie DLP de gravité élevée. Pour obtenir des conseils détaillés sur la configuration de stratégies DLP pour votre organisation, consultez l’article [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md).
- Lorsque vous utilisez **des modèles de violation** de stratégie de sécurité, vous devez activer Microsoft Defender pour endpoint pour l’intégration de la gestion des risques internes dans le Centre de sécurité Defender pour importer les alertes de violation de sécurité. Pour obtenir des instructions pas à pas pour activer l’intégration de Defender pour Endpoint à la gestion des risques internes, voir Configurer des fonctionnalités avancées [dans Microsoft Defender pour Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features).
- Lorsque vous utilisez **des modèles utilisateur disgruntled** , vous devez configurer un connecteur Microsoft 365 HR pour importer régulièrement des informations sur les performances ou l’état de rétrogradation pour les utilisateurs de votre organisation. Consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) pour obtenir des conseils détaillés pour configurer le connecteur Microsoft 365 RH au sein de votre organisation.

## <a name="test-with-a-small-group-of-users-in-a-production-environment"></a>Tester avec un petit groupe d’utilisateurs dans un environnement de production

Avant d’activer la solution à grande échelle dans votre environnement de production, vous pouvez envisager de tester les stratégies avec un petit groupe d’utilisateurs de production tout en mener à bien la conformité, la confidentialité et les révisions juridiques nécessaires dans votre organisation. L’évaluation de la gestion des risques internes dans un environnement de test nécessite de générer des actions utilisateur simulées et d’autres signaux pour créer des alertes pour le tri et les cas de traitement. Cette approche n’est pas pratique pour la plupart des organisations. Il est donc préférable de tester la gestion des risques internes avec un petit groupe d’utilisateurs dans un environnement de production.

Conservez la fonctionnalité d’anonymisation dans les paramètres de stratégie activée pour anonymiser les noms d’affichage des utilisateurs dans la console de gestion des risques internes pendant ce test afin de maintenir la confidentialité au sein de l’outil. Ce paramètre permet de protéger la confidentialité des utilisateurs qui ont des correspondances de stratégie et peut contribuer à promouvoir une certaine fiabilité dans les examens d’analyse et d’examen des données pour les alertes de risques internes.

Si vous ne voyez aucune alerte immédiatement après la configuration d’une stratégie de gestion des risques internes, cela peut signifier que le seuil de risque minimal n’a pas encore été atteint. Un bon moyen de vérifier si la stratégie est déclenchée et fonctionne comme prévu consiste à voir si l’utilisateur est dans l’étendue de la stratégie sur la page **Utilisateurs** .

## <a name="resources-for-stakeholders"></a>Ressources pour les parties prenantes

Partagez la documentation de gestion des risques internes avec les parties prenantes de votre organisation qui sont incluses dans votre flux de travail de gestion et de correction :

- [Créer et gérer les stratégies de risques internes](insider-risk-management-policies.md)
- [Identifier les activités de risques internes](insider-risk-management-activities.md)
- [Agir sur les cas de risques internes](insider-risk-management-cases.md)
- [Examiner les données de cas avec l’Explorateur de contenu à risque interne](insider-risk-management-content-explorer.md)
- [Créer des modèles d’avertissement sur les risques internes](insider-risk-management-notices.md)

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Vous êtes prêt à configurer la gestion des risques internes pour votre organisation ? Lisez les articles suivants :

- [Prise en charge des paramètres de gestion des risques internes](insider-risk-management-settings.md) pour configurer les paramètres de stratégie globale.
- [Prise en charge de la gestion des](insider-risk-management-configure.md) risques internes pour configurer les conditions préalables, créer des stratégies et commencer à recevoir des alertes.
