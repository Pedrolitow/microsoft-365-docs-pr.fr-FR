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
ms.openlocfilehash: ca15f26cf8eb19990c3252acf66ba50d52567e44
ms.sourcegitcommit: f6840dfcfdbcadc53cda591fd6cf9ddcb749d303
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "44327122"
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

Différentes zones géographiques et organisationnelles peuvent avoir des exigences de conformité et de confidentialité qui sont très différentes des autres zones de votre organisation. Collaborez avec les parties prenantes dans ces domaines pour vous assurer qu’ils comprennent les contrôles de conformité et de confidentialité dans la gestion des risques initiés et comment ils doivent être utilisés dans différentes zones de votre organisation. Dans certains scénarios, les exigences en matière de conformité et de confidentialité peuvent nécessiter des stratégies qui désignent ou restreignent certaines parties prenantes des enquêtes et des incidents en fonction de l’incident pour un utilisateur ou des exigences réglementaires ou politiques relatives à la zone.

Si vous avez des exigences pour que des parties prenantes spécifiques soient impliquées dans des investigations de cas impliquant des employés dans certaines régions, rôles ou divisions, vous pouvez implémenter des [stratégies de gestion des risques Insider](insider-risk-management-policies.md) distinctes (même si identiques) ciblant les différentes régions et populations. Cela permettra aux parties prenantes appropriées de trier et de gérer plus facilement les cas qui s’appliquent à leurs rôles et régions. En outre, vous pouvez envisager de créer des processus et des stratégies pour les régions où les enquêteurs et les relecteurs parlent de la même langue que les utilisateurs afin de rationaliser le processus de remontée des alertes et des incidents de gestion des risques initiés.

## <a name="plan-for-the-review-and-investigation-workflow"></a>Planifier le flux de travail de révision et d’enquête

Sélectionnez les parties prenantes dédiées pour surveiller et passer en revue les alertes et les incidents à intervalles réguliers dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/). Assurez-vous de comprendre comment affecter des parties prenantes différentes aux différents groupes de rôles disponibles dans la gestion des risques initiés.

En fonction de la structure de votre équipe de gestion de la conformité, vous disposez des options permettant d’affecter des utilisateurs à des groupes de rôles spécifiques afin de gérer différents ensembles de fonctionnalités de gestion des risques initiés. Vous avez le choix entre ces options de groupe de rôles lors de la configuration de la gestion des risques initiés :

| **Groupe de rôles** | **Autorisations de rôle** |
| :---- | :---------------- |
| **Gestion des risques initiés** | Utilisez ce groupe de rôles pour gérer la gestion des risques Insider de votre organisation dans un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes et investigateurs désignés, vous pouvez configurer des autorisations de gestion des risques Insider dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de gestion des risques Insider. Cette configuration est la méthode la plus simple pour démarrer rapidement avec la gestion des risques initiés et pour les organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts.|
| **Administrateur de gestion des risques des Insiders** | Utilisez ce groupe de rôles pour configurer initialement la gestion des risques initiés et, par la suite, pour séparer les administrateurs des risques des Insiders en un groupe défini.  Les utilisateurs de ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de gestion des risques internes, des paramètres globaux et des affectations de groupes de rôles. |
| **Analystes de gestion des risques Insiders** | Utilisez ce groupe pour attribuer des autorisations à des utilisateurs qui agiront en tant qu’analystes de cas d’Insider. Les utilisateurs de ce groupe de rôles peuvent accéder aux modèles alertes, incidents et notifications de gestion des risques Insider. Ils ne peuvent pas accéder à l’Explorateur de contenu risque Insider. |
| **Investigateurs de gestion des risques Insiders** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agiront en tant qu’enquêteurs de données sur les risques des Insiders. Les utilisateurs de ce groupe de rôles peuvent accéder à toutes les alertes de gestion des risques Insider, les cas, les modèles de notifications et l’Explorateur de contenu dans tous les cas. |

## <a name="understand-requirements-and-dependencies"></a>Comprendre les exigences et les dépendances

En fonction de la façon dont vous envisagez d’implémenter des stratégies de gestion des risques inSided, vous devez disposer des abonnements aux licences Microsoft 365 et comprendre et planifier les conditions préalables de la solution.

Gestion des **licences :** La gestion des risques initiés est disponible dans le cadre de la large sélection des abonnements aux licences Microsoft 365. Pour plus d’informations, reportez-vous à l’article [Getting Started with Insider Risk Management](insider-risk-management-configure.md#before-you-begin) .

Si vous ne disposez pas d’un plan Microsoft 365 entreprise E5 existant et que vous souhaitez essayer de gérer les risques internes, vous pouvez [Ajouter microsoft 365](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou [vous inscrire pour obtenir une version d’évaluation](https://www.microsoft.com/microsoft-365/enterprise) de Microsoft 365 entreprise E5.

**Conditions requises pour le modèle de stratégie :** Selon le modèle de stratégie, vous devrez peut-être comprendre et planifier avant de configurer la gestion des risques initiés au sein de votre organisation :

- Lors de l’utilisation du modèle de **vol de données d’employé** en cours de suppression, vous devez configurer un connecteur rh Microsoft 365 pour importer régulièrement des informations de démission et de date d’arrêt pour les employés de votre organisation. Pour obtenir des conseils détaillés sur la configuration du connecteur RH Microsoft 365 pour votre organisation, voir la rubrique [importer des données avec le connecteur RH](import-hr-data.md) .
- Lorsque vous utilisez le modèle de **fuites de données** , vous devez configurer au moins une stratégie de protection contre la perte de données (DLP) pour définir des informations sensibles dans votre organisation et recevoir des alertes de risque pour les alertes de stratégie DLP de gravité élevée. Consultez la rubrique [créer, tester et régler une stratégie DLP](create-test-tune-dlp-policy.md) pour obtenir des instructions détaillées sur la configuration des stratégies DLP pour votre organisation.

## <a name="test-with-a-small-group-of-users-in-a-production-environment"></a>Tester avec un petit groupe d’utilisateurs dans un environnement de production

Avant d’activer la solution à grande échelle dans votre environnement de production, vous pouvez envisager de tester les stratégies avec un petit groupe d’utilisateurs de production tout en effectuant les vérifications juridiques, de confidentialité et de conformité nécessaires dans votre organisation. L’évaluation de la gestion des risques initiés dans un environnement de test exigerait que vous génériez des actions utilisateur simulées et d’autres signaux pour créer des alertes de triage et de cas de traitement. En règle générale, cela n’est pas pratique pour la plupart des organisations, c’est pourquoi il est généralement préférable de tester la gestion des risques initiés avec un petit groupe d’utilisateurs dans un environnement de production.

Conservez la fonctionnalité d’anonymisation dans paramètres de stratégie activée pour pseudonymiser les noms d’affichage des utilisateurs dans la console de gestion des risques Insiders pendant ce test afin de maintenir la confidentialité dans l’outil. Cela permet de protéger la confidentialité des utilisateurs qui ont des correspondances de stratégie et peuvent favoriser l’application de l’audit des alertes relatives aux risques internes pour les analyses de données et les analyses d’analyse.

Si vous ne voyez pas d’alertes immédiatement après avoir configuré une stratégie de gestion des risques Insiders, cela peut signifier que le seuil de risque minimal n’a pas encore été atteint. Un bon moyen de vérifier si la stratégie est déclenchée et de fonctionner comme prévu consiste à déterminer si l’utilisateur est dans l’étendue de la stratégie sur la page **utilisateurs** .

## <a name="resources-for-stakeholders"></a>Ressources pour les parties prenantes

Partagez la documentation de gestion des risques Insider avec les parties prenantes de votre organisation qui sont incluses dans votre flux de travail de gestion et de correction :

- [Créer et gérer les stratégies de risques internes](insider-risk-management-policies.md)
- [Identifier les alertes de risques internes](insider-risk-management-alerts.md)
- [Agir sur les cas de risques internes](insider-risk-management-cases.md)
- [Examiner les données de cas avec l’Explorateur de contenu des risques Insiders](insider-risk-management-content-explorer.md)
- [Créer des modèles d’avertissement sur les risques internes](insider-risk-management-notices.md)

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Vous êtes prêt à configurer la gestion des risques initiés pour votre organisation ? Consultez la rubrique [prise en main de la gestion des risques initiés](insider-risk-management-configure.md) pour configurer les conditions préalables, créer des stratégies et commencer à recevoir des alertes.
