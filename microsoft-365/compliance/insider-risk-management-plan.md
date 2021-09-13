---
title: Planifier la gestion des risques Insider
description: Découvrez comment planifier l’utilisation des stratégies de gestion des risques internes dans votre organisation.
keywords: Microsoft 365, risques internes, gestion des risques, conformité
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
ms.openlocfilehash: 4c128b4396b21852ac0cdf24b9528ec8ae238caf
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59181282"
---
# <a name="plan-for-insider-risk-management"></a>Planifier la gestion des risques Insider

Avant de commencer à [gérer](insider-risk-management.md) les risques internes dans votre organisation, il existe d’importantes activités de planification et des considérations qui doivent être examinées par vos équipes de gestion des technologies de l’information et de la conformité. Une compréhension approfondie et la planification du déploiement dans les domaines suivants vous aideront à vous assurer que votre implémentation et votre utilisation des fonctionnalités de gestion des risques internes se déroulent sans problème et sont conformes aux meilleures pratiques pour la solution.

Regardez la vidéo ci-dessous pour découvrir comment le flux de travail de gestion des risques internes peut aider votre organisation à prévenir, détecter et contenir des risques tout en hiérbant les valeurs, la culture et l’expérience utilisateur de votre organisation :
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

## <a name="work-with-stakeholders-in-your-organization"></a>Travailler avec les parties prenantes de votre organisation

Identifiez les parties prenantes appropriées dans votre organisation pour collaborer pour prendre des mesures sur les alertes et les cas de gestion des risques internes. Certaines parties prenantes recommandées à envisager, y compris [](insider-risk-management.md#workflow) dans la planification initiale et le flux de travail de gestion des risques internes de bout en bout, sont les personnes des zones suivantes de votre organisation :

- Technologie de l’information
- Conformité
- Confidentialité
- Sécurité
- Ressources humaines
- Informations juridiques

## <a name="determine-any-regional-compliance-requirements"></a>Déterminer les exigences de conformité régionale

Différentes zones géographiques et organisationnelles peuvent avoir des exigences de conformité et de confidentialité différentes des autres zones de votre organisation. Travaillez en équipe avec les parties prenantes dans ces domaines pour vous assurer qu’elles comprennent les contrôles de conformité et de confidentialité dans la gestion des risques internes et comment elles doivent être utilisées dans différents domaines de votre organisation. Dans certains scénarios, les exigences de conformité et de confidentialité peuvent nécessiter des stratégies qui désignent ou limitent certaines parties prenantes à des enquêtes et des cas basés sur le cas d’un utilisateur ou des exigences réglementaires ou de stratégie pour la zone.

Si vous avez besoin que des parties prenantes spécifiques soient impliquées dans des enquêtes de cas qui [](insider-risk-management-policies.md) impliquent des utilisateurs de certaines régions, rôles ou divisions, vous pouvez implémenter des stratégies de gestion des risques internes distinctes (même identiques) ciblant les différentes régions et population. Cette configuration permettra aux parties prenantes de trier et de gérer plus facilement les cas pertinents pour leurs rôles et régions. En outre, vous pouvez envisager de créer des processus et des stratégies pour les régions où les enquêteurs et les réviseurs parlent la même langue que les utilisateurs pour simplifier le processus d’escalade pour les alertes et les cas de gestion des risques internes.

## <a name="plan-for-the-review-and-investigation-workflow"></a>Planifier le flux de travail de révision et d’examen

Sélectionnez des parties prenantes dédiées pour surveiller et examiner les alertes et les cas à une cadence régulière dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/). Assurez-vous de bien comprendre comment vous allez affecter différentes parties prenantes aux différents groupes de rôles disponibles dans la gestion des risques internes.

>[!IMPORTANT]
>Assurez-vous que vous avez toujours  au moins  un utilisateur dans les groupes de rôles Gestion des risques internes ou Administrateur de la gestion des risques internes (selon l’option que vous choisissez) afin que votre configuration de gestion des risques internes n’entre pas dans un scénario « administrateur zéro » si des utilisateurs spécifiques quittent votre organisation.

Selon la structure de votre équipe de gestion de la conformité, vous avez la choix d’affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de gestion des risques internes. Pour afficher l’onglet Autorisations dans le Centre de conformité Microsoft 365 et gérer les groupes  de rôles, vous devez être affecté au groupe de **rôles** Gestion de l’organisation ou avoir le rôle Gestion des *rôles.* Choisissez parmi ces options de groupe de rôles lors de la configuration de la gestion des risques internes :

| **Groupe de rôles** | **Autorisations de rôle** |
| :------------- | :------------------- |
| **Gestion des risques internes** | Ce groupe de rôles permet de gérer la gestion des risques internes pour votre organisation au sein d’un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et auditeurs désignés, vous pouvez configurer les autorisations de gestion des risques internes dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de gestion des risques internes et les autorisations associées. Cette configuration est le moyen le plus simple de se lancer rapidement dans la gestion des risques internes et convient parfaitement aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. Lorsque vous utilisez cette configuration, vous devez vous assurer qu’au moins un utilisateur est toujours affecté à ce groupe de rôles pour vous assurer que vos stratégies fonctionnent comme prévu et que l’utilisateur peut créer et modifier des **_stratégies,_** configurer les paramètres de la solution et passer en revue les avertissements d’état de la stratégie.|
| **Administrateur de la gestion des risques internes** | Utilisez ce groupe de rôles pour configurer initialement la gestion des risques internes, puis pour séparer les administrateurs des risques internes en un groupe défini. Les utilisateurs de ce groupe de rôles peuvent activer et afficher des analyses et créer, lire, mettre à jour et supprimer des stratégies de gestion des risques internes, des paramètres globaux et des attributions de groupe de rôles. Lorsque vous utilisez cette configuration, vous devez vous assurer qu’au moins un utilisateur est toujours affecté à ce groupe de rôles pour vous assurer que vos stratégies fonctionnent comme prévu et que l’utilisateur peut créer et modifier des **_stratégies,_** configurer les paramètres de la solution et passer en revue les avertissements d’état de la stratégie. |
| **Analystes de la gestion des risques internes.** | Utilisez ce groupe pour affecter des autorisations aux utilisateurs qui agiront comme des analystes de cas de risque internes. Les utilisateurs de ce groupe de rôles peuvent accéder à toutes les alertes, cas, analyses et modèles de notifications de gestion des risques internes et les afficher. Ils ne peuvent pas accéder à l’Explorateur de contenu à risque interne. |
| **Enquêteurs sur la gestion des risques internes.** | Utilisez ce groupe pour affecter des autorisations aux utilisateurs qui agiront comme des enquêteurs de données de risque internes. Les utilisateurs de ce groupe de rôles peuvent accéder à toutes les alertes de gestion des risques internes, cas, modèles d’avis et explorateur de contenu pour tous les cas. |
| **Auditeurs de gestion des risques internes** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui auditeront les activités de gestion des risques internes. Les utilisateurs de ce groupe de rôles peuvent accéder au journal d’audit des risques internes. |

## <a name="understand-requirements-and-dependencies"></a>Comprendre les exigences et les dépendances

Selon la façon dont vous prévoyez d’implémenter des stratégies de gestion des risques internes, vous devez avoir les abonnements aux licences Microsoft 365 appropriés et comprendre et planifier certaines conditions préalables de solution.

**Licences :** La gestion des risques internes est disponible dans le cadre d’un large éventail d’abonnements Microsoft 365 licences. Pour plus d’informations, consultez l’article Prise en charge de la gestion des [risques internes.](insider-risk-management-configure.md#subscriptions-and-licensing)

Si vous n’avez pas de plan Microsoft 365 Entreprise E5 et que vous souhaitez essayer la gestion des risques [](https://www.microsoft.com/microsoft-365/enterprise) internes, vous pouvez ajouter des [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou vous inscrire à une version d’évaluation de Microsoft 365 Entreprise E5.

**Conditions requises pour les modèles de stratégie :** Selon le modèle de stratégie que vous choisissez, il existe des exigences que vous devez comprendre et planifier avant de configurer la gestion des risques internes dans votre organisation :

- Lorsque vous  utilisez le modèle de vol de données par des utilisateurs qui quittent le modèle, vous devez configurer un connecteur RH Microsoft 365 pour importer régulièrement les informations de date de résiliation et de renvoi pour les utilisateurs de votre organisation. Consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) pour obtenir des conseils détaillés pour configurer le connecteur Microsoft 365 RH au sein de votre organisation.
- Lorsque vous utilisez des modèles de **fuites** de données, vous devez configurer au moins une stratégie de protection contre la perte de données (DLP) pour définir des informations sensibles dans votre organisation et recevoir des alertes de risques internes pour les alertes de stratégie DLP de gravité élevée. Pour obtenir des conseils détaillés sur la configuration de stratégies DLP pour votre organisation, consultez l’article [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md).
- Lorsque vous utilisez **des modèles** de violation de stratégie de sécurité, vous devez activer Microsoft Defender pour Endpoint pour l’intégration de la gestion des risques internes dans le Centre de sécurité Defender pour importer les alertes de violation de sécurité. Consultez [l’article](/windows/security/threat-protection/microsoft-defender-atp/advanced-features) Configurer les fonctionnalités avancées dans Microsoft Defender pour obtenir des instructions pas à pas pour activer Defender pour l’intégration de Point de terminaison avec la gestion des risques internes.
- Lorsque vous utilisez des modèles utilisateur **disgruntled,** vous devez configurer un connecteur RH Microsoft 365 pour importer régulièrement des informations sur les performances ou l’état de rétrogradation pour les utilisateurs de votre organisation. Consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) pour obtenir des conseils détaillés pour configurer le connecteur Microsoft 365 RH au sein de votre organisation.

## <a name="test-with-a-small-group-of-users-in-a-production-environment"></a>Tester avec un petit groupe d’utilisateurs dans un environnement de production

Avant d’activer la solution à grande échelle dans votre environnement de production, vous pouvez envisager de tester les stratégies avec un petit groupe d’utilisateurs de production tout en mener à bien la conformité, la confidentialité et les révisions juridiques nécessaires dans votre organisation. L’évaluation de la gestion des risques internes dans un environnement de test nécessite de générer des actions utilisateur simulées et d’autres signaux pour créer des alertes pour le tri et les cas de traitement. Cette approche n’est pas pratique pour la plupart des organisations. Il est donc préférable de tester la gestion des risques internes avec un petit groupe d’utilisateurs dans un environnement de production.

Maintenez la fonctionnalité d’anonymisation dans les paramètres de stratégie activée pour anonymiser les noms d’affichage des utilisateurs dans la console de gestion des risques internes pendant ce test afin de maintenir la confidentialité au sein de l’outil. Ce paramètre permet de protéger la confidentialité des utilisateurs qui ont des correspondances de stratégie et peut contribuer à promouvoir une certaine fiabilité dans les examens d’analyse et d’examen des données pour les alertes de risques internes.

Si vous ne voyez aucune alerte immédiatement après la configuration d’une stratégie de gestion des risques internes, cela peut signifier que le seuil de risque minimal n’a pas encore été atteint. Un bon moyen de vérifier si la stratégie est déclenchée et fonctionne comme prévu consiste à voir si l’utilisateur est dans l’étendue de la stratégie sur la page **Utilisateurs.**

## <a name="resources-for-stakeholders"></a>Ressources pour les parties prenantes

Partagez la documentation de gestion des risques internes avec les parties prenantes de votre organisation qui sont incluses dans votre flux de travail de gestion et de correction :

- [Créer et gérer les stratégies de risques internes](insider-risk-management-policies.md)
- [Identifier les activités de risques internes](insider-risk-management-activities.md)
- [Agir sur les cas de risques internes](insider-risk-management-cases.md)
- [Examiner les données de cas avec l’Explorateur de contenu à risque interne](insider-risk-management-content-explorer.md)
- [Créer des modèles d’avertissement sur les risques internes](insider-risk-management-notices.md)

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Vous êtes prêt à configurer la gestion des risques internes pour votre organisation ? Lisez les articles suivants :

- [Prise en charge des paramètres de gestion des](insider-risk-management-settings.md) risques internes pour configurer les paramètres de stratégie globale.
- [Prise en charge de la gestion des risques](insider-risk-management-configure.md) internes pour configurer les conditions préalables, créer des stratégies et commencer à recevoir des alertes.
