---
title: Planifier la gestion des risques Insider
description: Découvrez comment planifier l’utilisation des stratégies de gestion des risques Insiders dans votre organisation.
keywords: Microsoft 365, Insider Risk, gestion des risques, conformité
localization_priority: Normal
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: b2aa72dea55d4c75f6e73161e07cf0a9bb5ecf1c
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48846272"
---
# <a name="plan-for-insider-risk-management"></a>Planifier la gestion des risques Insider

Avant de commencer à [gérer les risques initiaux](insider-risk-management.md) au sein de votre organisation, il existe des activités de planification et des considérations importantes qui doivent être examinées par vos équipes de gestion de la conformité et de la technologie de l’information. La compréhension et la planification rigoureuses du déploiement dans les domaines suivants permettent de s’assurer que l’implémentation et l’utilisation des fonctionnalités de gestion des risques internes se déroulent en douceur et sont alignées sur les meilleures pratiques pour la solution.

## <a name="work-with-stakeholders-in-your-organization"></a>Utilisation des parties prenantes au sein de votre organisation

Identifiez les parties prenantes appropriées dans votre organisation afin de collaborer afin de prendre des mesures pour les alertes et les incidents de gestion des risques initiés. Certaines parties prenantes recommandées doivent envisager l’inclusion dans la planification initiale et le [flux de travail de gestion des risques initiés](insider-risk-management.md#workflow) de bout en bout sont des personnes des zones suivantes de votre organisation :

- Technologies de l’information
- Conformité
- Confidentialité
- Sécurité
- ressources humaines ;
- Informations juridiques

## <a name="determine-any-regional-compliance-requirements"></a>Déterminer les exigences de conformité régionales

Différentes zones géographiques et organisationnelles peuvent avoir des exigences de conformité et de confidentialité différentes des autres zones de votre organisation. Collaborez avec les parties prenantes dans ces domaines pour vous assurer qu’ils comprennent les contrôles de conformité et de confidentialité dans la gestion des risques initiés et comment ils doivent être utilisés dans différentes zones de votre organisation. Dans certains scénarios, les exigences en matière de conformité et de confidentialité peuvent nécessiter des stratégies qui désignent ou restreignent certaines parties prenantes des enquêtes et des incidents en fonction de l’incident pour un utilisateur ou des exigences réglementaires ou politiques relatives à la zone.

Si vous avez des exigences pour que des parties prenantes spécifiques soient impliquées dans des investigations de cas impliquant des utilisateurs dans certaines régions, rôles ou divisions, vous pouvez implémenter des [stratégies de gestion des risques Insider](insider-risk-management-policies.md) distinctes (même si identiques) ciblant les différentes régions et populations. Cette configuration permettra aux parties prenantes appropriées de trier et de gérer les cas pertinents pour leurs rôles et leurs régions. En outre, vous pouvez envisager de créer des processus et des stratégies pour les régions où les enquêteurs et les relecteurs parlent de la même langue que les utilisateurs afin de rationaliser le processus de remontée des alertes et des incidents de gestion des risques initiés.

## <a name="plan-for-the-review-and-investigation-workflow"></a>Planifier le flux de travail de révision et d’enquête

Sélectionnez les parties prenantes dédiées pour surveiller et passer en revue les alertes et les incidents à intervalles réguliers dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/). Assurez-vous de comprendre comment affecter des parties prenantes différentes aux différents groupes de rôles disponibles dans la gestion des risques initiés.

Selon la structure de votre équipe de gestion de la conformité, vous avez la choix d’affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de gestion des risques internes. Vous avez le choix entre ces options de groupe de rôles lors de la configuration de la gestion des risques initiés :

| **Groupe de rôles** | **Autorisations de rôle** |
| :---- | :---------------- |
| **Gestion des risques initiés** | Ce groupe de rôles permet de gérer la gestion des risques internes pour votre organisation au sein d’un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes et enquêteurs désignés, vous pouvez définir des autorisations de gestion des risques internes dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de gestion des risques internes. Cette configuration est la méthode la plus simple pour démarrer rapidement avec la gestion des risques initiés et pour les organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts.|
| **Administrateur de gestion des risques des Insiders** | Utilisez ce groupe de rôles pour configurer initialement la gestion des risques initiés et, par la suite, pour séparer les administrateurs des risques des Insiders en un groupe défini.  Les utilisateurs de ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de gestion des risques internes, des paramètres globaux et des affectations de groupe de rôles. |
| **Analystes de gestion des risques Insiders** | Utilisez ce groupe pour affecter des autorisations aux utilisateurs qui agiront comme des analystes de cas de risque internes. Les utilisateurs de ce groupe de rôles peuvent accéder aux modèles alertes, incidents et notifications de gestion des risques Insider. Ils ne peuvent pas accéder à l’Explorateur de contenu de risques internes. |
| **Investigateurs de gestion des risques Insiders** | Utilisez ce groupe pour affecter des autorisations aux utilisateurs qui agiront comme des enquêteurs de données de risque internes. Les utilisateurs de ce groupe de rôles peuvent accéder à toutes les alertes de gestion des risques Insider, les cas, les modèles de notifications et l’Explorateur de contenu dans tous les cas. |

## <a name="understand-requirements-and-dependencies"></a>Comprendre les exigences et les dépendances

En fonction de la façon dont vous envisagez d’implémenter des stratégies de gestion des risques inSided, vous devez disposer des abonnements aux licences Microsoft 365 et comprendre et planifier les conditions préalables de la solution.

Gestion des **licences :** La gestion des risques initiés est disponible dans le cadre de la large sélection des abonnements aux licences Microsoft 365. Pour plus d’informations, reportez-vous à l’article [Getting Started with Insider Risk Management](insider-risk-management-configure.md#before-you-begin) .

Si vous ne disposez pas d’un plan Microsoft 365 entreprise E5 existant et que vous souhaitez essayer de gérer les risques internes, vous pouvez [Ajouter microsoft 365](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou [vous inscrire pour obtenir une version d’évaluation](https://www.microsoft.com/microsoft-365/enterprise) de Microsoft 365 entreprise E5.

**Conditions requises pour le modèle de stratégie :** Selon le modèle de stratégie que vous choisissez, vous devez comprendre et planifier avant de configurer la gestion des risques initiés au sein de votre organisation :

- Lors de l’utilisation du modèle **utilisateurs de vol de données** , vous devez configurer un connecteur rh Microsoft 365 pour importer régulièrement les informations de démission et de date d’arrêt pour les utilisateurs de votre organisation. Pour obtenir des conseils détaillés sur la configuration du connecteur RH Microsoft 365 pour votre organisation, voir l’article [importer des données avec le connecteur RH](import-hr-data.md) .
- Lorsque vous utilisez des modèles de **fuites de données** , vous devez configurer au moins une stratégie de protection contre la perte de données (DLP) pour définir des informations sensibles dans votre organisation et recevoir des alertes de risque pour les alertes de stratégie DLP de gravité élevée. Consultez l’article [créer, tester et ajuster une stratégie DLP](create-test-tune-dlp-policy.md) pour obtenir des instructions détaillées sur la configuration des stratégies DLP pour votre organisation.
- Lorsque vous utilisez des modèles de **violation de stratégie de sécurité** , vous devez activer Microsoft Defender pour le point de terminaison de l’intégration de la gestion des risques initiaux dans le centre de sécurité de Defender pour importer les alertes de violation de sécurité. Reportez-vous à l’article [configure Advanced Features in Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-features) pour obtenir des conseils détaillés sur l’activation de l’intégration de Defender for Endpoint avec la gestion des risques initiés.
- Lorsque vous utilisez des modèles **utilisateur mécontents** , vous devez configurer un connecteur rh Microsoft 365 pour importer régulièrement des informations sur l’état des performances ou de la rétrogradation pour les utilisateurs de votre organisation. Pour obtenir des conseils détaillés sur la configuration du connecteur RH Microsoft 365 pour votre organisation, voir l’article [importer des données avec le connecteur RH](import-hr-data.md) .

## <a name="test-with-a-small-group-of-users-in-a-production-environment"></a>Tester avec un petit groupe d’utilisateurs dans un environnement de production

Avant d’activer la solution à grande échelle dans votre environnement de production, vous pouvez envisager de tester les stratégies avec un petit groupe d’utilisateurs de production tout en effectuant les vérifications juridiques, de confidentialité et de conformité nécessaires dans votre organisation. L’évaluation de la gestion des risques initiés dans un environnement de test exigerait que vous génériez des actions utilisateur simulées et d’autres signaux pour créer des alertes de triage et de cas de traitement. Cette approche n’est pas pratique pour la plupart des organisations, c’est pourquoi il est préférable de tester la gestion des risques initiés avec un petit groupe d’utilisateurs dans un environnement de production.

Conservez la fonctionnalité d’anonymisation des paramètres de stratégie activée pour rendre les noms d’affichage d’utilisateur anonymes dans la console de gestion des risques Insider pendant ce test afin de maintenir la confidentialité dans l’outil. Ce paramètre permet de protéger la confidentialité des utilisateurs qui ont des correspondances de stratégie et qui peuvent favoriser l’application de l’audit des alertes de risque d’initié pour les analyses de données et les analyses d’analyse.

Si vous ne voyez pas d’alertes immédiatement après avoir configuré une stratégie de gestion des risques Insiders, cela peut signifier que le seuil de risque minimal n’a pas encore été atteint. Un bon moyen de vérifier si la stratégie est déclenchée et de fonctionner comme prévu consiste à déterminer si l’utilisateur est dans l’étendue de la stratégie sur la page **utilisateurs** .

## <a name="resources-for-stakeholders"></a>Ressources pour les parties prenantes

Partagez la documentation de gestion des risques Insider avec les parties prenantes de votre organisation qui sont incluses dans votre flux de travail de gestion et de correction :

- [Créer et gérer les stratégies de risques internes](insider-risk-management-policies.md)
- [Identifier les alertes de risques internes](insider-risk-management-alerts.md)
- [Agir sur les cas de risques internes](insider-risk-management-cases.md)
- [Examiner les données de cas avec l’Explorateur de contenu des risques Insiders](insider-risk-management-content-explorer.md)
- [Créer des modèles d’avertissement sur les risques internes](insider-risk-management-notices.md)

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Vous êtes prêt à configurer la gestion des risques initiés pour votre organisation ? Consultez les articles suivants :

- [Prise en main des paramètres de gestion des risques initiés](insider-risk-management-settings.md) pour configurer les paramètres de stratégie globale.
- [Prise en main de la gestion des risques initiés](insider-risk-management-configure.md) pour configurer les conditions préalables, créer des stratégies et commencer à recevoir des alertes.
