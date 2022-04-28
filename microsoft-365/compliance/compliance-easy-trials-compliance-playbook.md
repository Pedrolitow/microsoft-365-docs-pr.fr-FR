---
title: Guide opérationnel d'essai des solutions de conformité Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MOE150
- MET150
description: Guide opérationnel d'essai des solutions de conformité Microsoft Purview.
ms.openlocfilehash: 3ff103a2e6ebc260f5f00964ae09c6b6bbc1fd69
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098887"
---
# <a name="trial-playbook-microsoft-purview-solutions"></a>Guide opérationnel d'essai : solutions Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bienvenue dans le guide opérationnel d’essai des solutions de conformité Microsoft Purview. Ce guide opérationnel vous aidera à tirer le meilleur parti de votre essai gratuit de 90 jours en vous aidant à découvrir les fonctionnalités robustes et complètes des produits de conformité et de sécurité Microsoft Purview.

Essayer chaque solution vous aidera à prendre des décisions éclairées pour répondre aux besoins de conformité de votre organisation.

Fonctionnalités :

- [Audit (Premium)](#audit-premium)
- [Conformité des communications](#communication-compliance)
- [Gestionnaire de conformité](#compliance-manager)
- [Gestion du cycle de vie des données](#data-lifecycle-management)
- [Protection contre la perte de données Microsoft Purview](#data-loss-prevention)
- [eDiscovery](#ediscovery)
- [Protection des informations](#information-protection)
- [Gestion des risques internes](#insider-risk-management)
- [Gestion des enregistrements](#records-management)

Modules complémentaires en option :

- [Évaluations des primes du responsable de la conformité](#compliance-manager-premium-assessments)
- [Gestion des risques liés à la confidentialité Microsoft Priva et demandes de droits d'objet Microsoft Priva](#microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests)

## <a name="compliance-actions-with-microsoft-purview"></a>Actions de conformité avec Microsoft Purview

Commencez facilement et rapidement à essayer les solutions de conformité de Microsoft sans modifier les métadonnées de votre organisation. En fonction de vos priorités, vous pouvez commencer par n'importe lequel de ces domaines de solution pour voir une valeur immédiate. Vous trouverez ci-dessous les cinq principales préoccupations organisationnelles communiquées par nos clients et les solutions recommandées pour commencer.

:::image type="content" source="../media/compliance-trial/workflow.png" alt-text="Actions de conformité avec Microsoft 365":::

## <a name="audit-premium"></a>Audit (Premium)

**Mener des enquêtes**

Microsoft Purview Audit (Premium) aide les organisations à mener des enquêtes judiciaires et de conformité en augmentant la rétention des journaux d'audit requise pour mener une enquête, en fournissant un accès aux événements cruciaux qui aident à déterminer l'étendue de la compromission et en fournissant un accès plus rapide à l'API Activité de gestion Office 365.

### <a name="step-1-apply-the-e5-license-to-each-user-for-which-youd-like-to-generate-e5-events"></a>Étape 1 : [Appliquez la licence E5 à chaque utilisateur pour lequel vous souhaitez générer des événements E5](set-up-advanced-audit.md#step-1-set-up-audit-premium-for-users)

> [!TIP]
> Meilleures pratiques d'essai : Jour 1

Les fonctionnalités d’audit (Premium) telles que la possibilité d’enregistrer des événements importants tels que MailItemsAccessed et envoyer nécessitent une licence E5 appropriée attribuée aux utilisateurs. De plus, l’application/plan de service d’audit avancé doit être activé pour ces utilisateurs.

Configurer l'audit (Premium) pour les utilisateurs – pour vérifier que l'application d'audit avancé est attribuée aux utilisateurs, [effectuez les étapes suivantes pour chaque utilisateur](set-up-advanced-audit.md#step-1-set-up-audit-premium-for-users).

1. Activer les événements d'audit (Premium) – [activez l’audit SearchQueryInitiatedExchange et SearchQueryInitiatedSharePoint](set-up-advanced-audit.md#step-2-enable-audit-premium-events) pour chaque utilisateur dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
1. Configurez des stratégies de rétention d'audit – [créez des stratégies de rétention des journaux d'audit supplémentaires](set-up-advanced-audit.md#step-3-set-up-audit-retention-policies) pour répondre aux exigences des opérations de sécurité, de l'informatique et des équipes de conformité de votre organisation.
1. Rechercher des événements d'audit (Premium) – [rechercher des événements d'audit (Premium) cruciaux](set-up-advanced-audit.md#step-4-search-for-audit-premium-events) et d'autres activités lors de la conduite d'enquêtes judiciaires.

### <a name="step-2-create-new-audit-log-policies-to-specify-how-long-to-retain-audit-logs-in-your-org-for-activities-performed-by-users-and-define-priority-levels-for-your-policies"></a>Étape 2 : [Créez de nouvelles stratégies de journal d'audit pour spécifier la durée de conservation des journaux d'audit dans votre organisation pour les activités effectuées par les utilisateurs et définissez les niveaux de priorité pour vos stratégies](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy)

> [!TIP]
> Bonne pratique d'essai : créez dans les 30 premiers jours

Les stratégies de rétention du journal d’audit font partie des nouvelles fonctionnalités d’audit (Premium) de Microsoft 365. Une stratégie de rétention de journal d’audit vous permet de spécifier la durée de conservation des journaux d’audit dans votre organisation.

1. Avant de créer une stratégie de conservation des journaux d'audit – [éléments clés à connaître](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy) avant de créer votre stratégie.
1. [Créer une stratégie de rétention de journal d’audit](audit-log-retention-policies.md#create-an-audit-log-retention-policy)
1. [Gérer les stratégies de rétention des journaux d'audit dans le portail de conformité Microsoft Purview](audit-log-retention-policies.md#manage-audit-log-retention-policies-in-the-compliance-portal) – Les stratégies de rétention des journaux d'audit sont répertoriées dans l'onglet Stratégies de rétention d'audit (également appelé tableau de bord). Vous pouvez utiliser le tableau de bord pour afficher, modifier et supprimer les politiques de conservation des audits.
1. Créez et gérez des stratégies de rétention des journaux d'audit sur PowerShell : vous pouvez également utiliser le Centre de sécurité et de conformité PowerShell pour [créer et gérer des stratégies de rétention des journaux d'audit](audit-log-retention-policies.md#create-and-manage-audit-log-retention-policies-in-powershell). L’une des raisons de l’utilisation de PowerShell est la création d’une stratégie pour un type ou une activité d’enregistrement qui n’est pas disponible dans l’interface utilisateur.

## <a name="communication-compliance"></a>Conformité des communications

**Identifier et agir sur les violations de la politique du code de conduite**

La conformité de la communication Microsoft Purview vous aide à identifier intelligemment les violations de communication pour soutenir un environnement de travail conforme et sain en vous aidant à détecter les messages inappropriés, à enquêter sur d'éventuelles violations de stratégie et à prendre des mesures pour y remédier.

### <a name="step-1-enable-permissions-for-communication-compliance"></a>Étape 1 : [Activer les autorisations pour la conformité des communications](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance)

> [!TIP]
> Meilleures pratiques d'essai : Jour 1

[Attribuez tous les utilisateurs de conformité au groupe de rôles Conformité de la communication](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance).

### <a name="step-2-enable-the-audit-log"></a>Étape 2 : [Activer le journal d’audit](communication-compliance-configure.md#step-2-required-enable-the-audit-log)

> [!TIP]
> Meilleure pratique d'essai : configuration dans les 30 premiers jours

Pour utiliser cette fonctionnalité, activez l'audit afin que votre organisation puisse commencer à enregistrer l'activité des utilisateurs et des administrateurs dans votre organisation. Lorsque vous activez cette option, l'activité est enregistrée dans le journal d'audit et peut être consultée dans un rapport. Pour plus d’informations, consultez [Activer ou désactiver la recherche dans le journal d’audit](turn-audit-log-search-on-or-off.md).

### <a name="step-3-create-a-communication-compliance-policy"></a>Étape 3 : [Créer une politique de conformité des communications](communication-compliance-policies.md)

[Créer une politique de conformité de communication en utilisant les modèles existants](communication-compliance-policies.md) : 1- Contenu inapproprié ; 2- Informations sensibles ; 3- Conformité réglementaire ; 4- Conflit d'intérêts.

### <a name="step-4-investigate-and-remediate-alerts"></a>Étape 4 : [Enquêter et corriger les alertes](communication-compliance-investigate-remediate.md)

[Examiner et corriger](communication-compliance-investigate-remediate.md) les alertes de conformité de communication.

## <a name="compliance-manager"></a>Gestionnaire de conformité

**Gérez facilement la conformité de votre organisation**

Le Gestionnaire de conformité Microsoft Purview peut vous aider tout au long de votre parcours de conformité, de l’inventaire des risques de protection de vos données à la gestion des complexités de l’implémentation de contrôles, la mise à jour des réglementations et des certifications et la création de rapports aux auditeurs.

### <a name="step-1-get-to-know-compliance-manager"></a>Étape 1 : [Connaître le Gestionnaire de conformité](compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)

> [!TIP]
> Meilleures pratiques d'essai : Jour 1

Notre page de vue d’ensemble du Gestionnaire de conformité est la meilleure première étape pour une révision complète de ce qu’est le Gestionnaire de conformité et de son fonctionnement. Vous pouvez également accéder directement aux sections clés de notre documentation en utilisant les liens ci-dessous :

- [Comprendre votre score de conformité](compliance-manager.md#understanding-your-compliance-score)
- [Présentation des éléments clés : contrôles, évaluations, modèles et actions d'amélioration](compliance-manager.md#key-elements-controls-assessments-templates-improvement-actions)
- [Comprendre le tableau de bord du Gestionnaire de conformité](compliance-manager-setup.md#understand-the-compliance-manager-dashboard)
- [Filtrer l’affichage de votre tableau de bord](compliance-manager-setup.md#filtering-your-dashboard-view)
- [En savoir plus sur les actions d’amélioration](compliance-manager-setup.md#improvement-actions-page)
- [Comprendre les évaluations](compliance-manager.md#assessments)
- [Effectuez une analyse rapide de votre environnement à l'aide de Microsoft Compliance Configuration Manager](compliance-manager-mcca.md)

![Gestionnaire de conformité – tableau de bord.](../media/compliance-manager-dashboard.png "Tableau de bord du Gestionnaire de conformité")

### <a name="step-2-configure-compliance-manager-to-manage-your-compliance-activities"></a>Étape 2 : [Configurer le Gestionnaire de conformité pour gérer vos activités de conformité](compliance-manager-assessments.md)

> [!TIP]
> Meilleure pratique d'essai : inspecter dans les 30 premiers jours

Commencez à travailler avec des évaluations et à prendre des mesures d'amélioration pour mettre en œuvre des contrôles et améliorer votre score de conformité.

1. [Choisissez un modèle prédéfini pour créer et gérer votre première évaluation](compliance-manager-assessments.md).
1. [Comprendre comment utiliser des modèles pour les évaluations de bâtiments](compliance-manager-templates.md).
1. [Effectuer des travaux de mise en œuvre et de test sur les actions d'amélioration pour compléter les contrôles dans vos évaluations](compliance-manager-improvement-actions.md).
1. [Mieux comprendre l'impact des différentes actions sur votre score de conformité](compliance-score-calculation.md).

> [!NOTE]
> L'abonnement Microsoft 365 ou Office 365 E1/E3 inclut le modèle Microsoft Data Protection Baseline. Microsoft 365 ou Office 365 E5, la conformité E5 comprend des modèles pour :
>
> - Base de protection des données Microsoft
> - RGPD de l’Union européenne  
> - ISO/IEC 27001,
> - NIST 800-53
>
> Compliance Manager comprend plus de 300 modèles réglementaires ou premium qui peuvent être achetés en tant que module complémentaire. Consultez la liste ici. Avec tous les modèles premium (inclus avec votre abonnement ou achetés en tant que module complémentaire), vous recevrez la version universelle de ces modèles, vous permettant de gérer votre conformité avec n'importe quel produit ou service

### <a name="step-3-scaling-up-use-advanced-functionality-to-meet-your-custom-needs"></a>Étape 3 : [Mise à l'échelle : utilisez des fonctionnalités avancées pour répondre à vos besoins personnalisés](compliance-manager-templates-create.md)

Les évaluations personnalisées sont utiles pour :

- Gestion de la conformité pour les produits non Microsoft 365 tels que les applications et services tiers, les applications sur site et d'autres actifs
- Gestion de vos propres contrôles de conformité personnalisés ou spécifiques à votre entreprise

1. [Étendez un modèle de gestionnaire de conformité en ajoutant vos propres contrôles et actions d'amélioration](compliance-manager-templates-extend.md)
1. [Créez votre propre modèle personnalisé](compliance-manager-templates-create.md)
1. [Modifier un modèle existant pour ajouter ou supprimer des contrôles et des actions](compliance-manager-templates-modify.md)
1. [Mettre en place des tests automatisés des actions d'amélioration](compliance-manager-setup.md#set-up-automated-testing)
1. [Réaffecter les actions d'amélioration à un autre utilisateur](compliance-manager-setup.md#reassign-improvement-actions-to-another-user)

## <a name="data-lifecycle-management"></a>Gestion du cycle de vie des données

**Gouverner à grande échelle avec l’automatisation**

Améliorez votre capacité à vous adapter aux modifications apportées à votre organisation avec des étendues de stratégie qui sont automatiquement mises à jour. Automatisez l’étiquetage du contenu pour réduire les efforts manuels et améliorez la posture de conformité.

### <a name="step-1-dynamically-target-retention-policies-with-adaptive-policy-scopes"></a>Étape 1 : Ciblez dynamiquement les stratégies de rétention avec les étendues de stratégie adaptatives
> [!TIP]
> Meilleures pratiques d'essai : Jour 1

Les étendues de stratégie adaptatives vous permettent de cibler dynamiquement une stratégie sur certains utilisateurs, groupes ou sites en fonction de leurs attributs AD.  Les attributs des étendues peuvent être sélectionnés dans une liste ou personnalisés à l'aide d'un générateur de requêtes avancé.

Les politiques utilisant des champs d'application adaptatifs restent à jour au fur et à mesure que l'organisation change avec l'arrivée ou le départ de nouveaux employés. De plus, ils ne sont pas soumis aux limites précédentes de 100/1 000 emplacements inclus dans une police.

- Créez une portée de stratégie adaptative et utilisez-la avec une stratégie de rétention

### <a name="step-2-automate-labeling-to-apply-a-label-to-all-items-by-default"></a>Étape 2 : Automatiser l’étiquetage pour appliquer une étiquette à tous les éléments par défaut

> [!TIP]
> Meilleure pratique d'essai : configuration dans les 30 premiers jours

Les étiquettes par défaut vous permettent d’appliquer automatiquement une étiquette de rétention à tous les éléments d’une bibliothèque, d’un dossier ou d’un document spécifié dans SharePoint.

- Publier une étiquette et l’appliquer par défaut dans SharePoint

## <a name="data-loss-prevention"></a>Protection contre la perte de données

**Protéger les données sensibles**

Pour respecter les normes de l'entreprise et les réglementations du secteur, les organisations doivent protéger les informations sensibles et empêcher leur divulgation accidentelle. Configurez des stratégies de protection contre la perte de données Microsoft Purview pour identifier, surveiller et protéger automatiquement les informations sensibles dans Microsoft 365.

### <a name="step-1-protect-data-loss-on-teams-locations"></a>Étape 1 : [Protégez la perte de données sur les emplacements Teams](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)

> [!TIP]
> Meilleures pratiques d'essai : Jour 1

Si votre organisation dispose d'une protection contre la perte de données (DLP), vous pouvez définir des stratégies qui empêchent les personnes de partager des informations sensibles dans un canal ou une session de discussion Microsoft Teams.

1. En savoir plus sur [Licences DLP pour Microsoft Teams et étendue de la protection DLP](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)
1. [Ajouter Microsoft Teams comme emplacement aux stratégies DLP existantes](dlp-microsoft-teams.md#add-microsoft-teams-as-a-location-to-existing-dlp-policies)
1. [Configurer notre stratégie DLP par défaut pour Teams](mip-easy-trials.md) ou [Définir une nouvelle stratégie DLP pour Microsoft Teams](dlp-microsoft-teams.md#define-a-new-dlp-policy-for-microsoft-teams)

### <a name="step-2-protect-data-loss-on-device-locations"></a>Étape 2 : [Protégez la perte de données sur les emplacements des appareils](endpoint-dlp-getting-started.md)

> [!TIP]
> Meilleure pratique d'essai : configuration dans les 30 premiers jours

Microsoft Endpoint DLP vous permet de surveiller les appareils Windows 10 et de détecter les situations d’utilisation et de partage des éléments sensibles.

1. Préparez vos points de terminaison – assurez-vous que les appareils Windows 10 et macOS que vous prévoyez de déployer Endpoint DLP [répondre à ces exigences](endpoint-dlp-getting-started.md)
1. [Intégrer les appareils dans la gestion des appareils](endpoint-dlp-getting-started.md) – Vous devez activer la surveillance des appareils et intégrer vos points de terminaison avant de pouvoir surveiller et protéger les éléments sensibles sur un appareil. Ces deux actions sont effectuées dans le portail de conformité Microsoft Purview.
   - Scénario 1 – [Appareils d’intégration](endpoint-dlp-getting-started.md) qui n'ont pas encore été intégrés.
   - Scénario 2 – [Microsoft Defender pour point de terminaison est déjà déployé et il existe des rapports de points de terminaison dans](endpoint-dlp-getting-started.md). Tous ces points de terminaison s’affichent dans la liste des appareils gérés.
1. [Configurer notre politique DLP par défaut pour les appareils](mip-easy-trials.md#dlp-for-devices) ou [Définir une nouvelle stratégie DLP pour les appareils](endpoint-dlp-learn-about.md).
1. [Afficher les alertes Endpoint DLP](dlp-configure-view-alerts-policies.md) dans le tableau de bord de gestion des alertes DLP.
1. [Afficher les données Endpoint DLP](data-classification-activity-explorer.md) dans l'explorateur d'activités.

### <a name="step-3-expand-policies-in-scope-or-protection"></a>Étape 3 : [Étendre les politiques dans la portée ou la protection](dlp-learn-about-dlp.md#dlp-policy-configuration-overview)

Vous disposez d'une certaine flexibilité dans la façon dont vous configurez vos stratégies DLP. Vous pouvez commencer avec notre stratégie DLP par défaut pour les équipes et les appareils et étendre ces stratégies pour protéger des emplacements supplémentaires, des types d'informations sensibles ou des étiquettes. En outre, vous pouvez développer les actions de stratégie et personnaliser les alertes.

1. Ajouter des emplacements
1. Ajoutez des types d'informations sensibles ou des étiquettes à protéger
1. Ajouter des actions
   - Teams :
      - [Empêcher l'accès externe aux documents sensibles](dlp-microsoft-teams.md#prevent-external-access-to-sensitive-documents)
      - [Obtenez des conseils de stratégie pour aider à éduquer les utilisateurs et des instructions pour personnaliser les conseils de stratégie](dlp-microsoft-teams.md#policy-tips-help-educate-users)
   - Appareils : passer de l'audit uniquement au blocage
1. [Configurer et afficher les alertes pour les stratégies de prévention des pertes de données – Microsoft Purview | Microsoft Docs](dlp-configure-view-alerts-policies.md)

## <a name="ediscovery"></a>eDiscovery

**Découvrez-en plus avec un workflow de bout en bout**

Tirez parti d'un flux de travail de bout en bout pour préserver, collecter, analyser et exporter du contenu adapté aux enquêtes internes et externes de votre organisation. Les équipes juridiques peuvent également gérer l’ensemble du processus de notification de conservation légale en communiquant avec les dépositaires impliqués dans un cas.

### <a name="step-1-required-permissions"></a>Étape 1 (obligatoire) : [Autorisations](https://aka.ms/ediscoveryninja)

> [!TIP]
> Meilleures pratiques d'essai : Jour 1

Pour accéder à la découverte électronique (Premium) ou être ajouté en tant que membre d'un dossier de la découverte électronique (Premium), un utilisateur doit disposer des autorisations appropriées.

1. [Configurer la découverte électronique (Premium) – Attribuer des autorisations eDiscovery](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions)
1. [Ajouter ou supprimer des membres à partir d’un cas](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

### <a name="step-2-required-create-a-case"></a>Étape 2 (obligatoire) : créer un cas

> [!TIP]
> Bonne pratique d'essai : créez dans les 30 premiers jours

De plus en plus d'organisations utilisent la solution de la découverte électronique (Premium) dans Microsoft 365 pour les processus critiques de la découverte électronique. Cela comprend la réponse aux demandes réglementaires, aux enquêtes et aux litiges.

1. Gérer la découverte électronique (Premium) – [découvrir comment configurer la découverte électronique (Premium), gérer les cas à l'aide du Centre de sécurité et de conformité, gérer un flux de travail dans la découverte électronique (Premium) et analyser les résultats de la recherche de la découverte électronique (Premium)](/learn/modules/manage-advanced-ediscovery).
1. [Créer un cas eDiscovery à l’aide du nouveau format de cas d’Advance eDiscovery](advanced-ediscovery-new-case-format.md)
1. [Fermer ou supprimer un cas](close-or-delete-case.md) – Lorsque l'affaire judiciaire ou l'enquête est terminée, vous pouvez fermer ou supprimer.

### <a name="step-3-optional-settings"></a>Étape 3 (facultative) : Paramètres

Pour permettre aux membres de votre organisation de commencer à créer et à utiliser des cas, vous devez configurer des paramètres globaux qui s'appliquent à tous les cas de votre organisation. À l'heure actuelle, le seul paramètre global est la **détection du privilège avocat-client** (des paramètres plus globaux seront disponibles à l'avenir).

1. [Configurer la découverte électronique (Premium) – Paramètres globaux](get-started-with-advanced-ediscovery.md#step-3-configure-global-settings-for-ediscovery-premium)
1. [Configurer les paramètres de recherche et d’analyse](configure-search-and-analytics-settings-in-advanced-ediscovery.md)
1. [Gérer les tâches dans la découverte électronique (Premium)](managing-jobs-ediscovery20.md)

### <a name="step-4-optional-compliance-boundaries"></a>Étape 4 (facultative) : [limites de conformité](set-up-compliance-boundaries.md)

Les limites de conformité créent des limites logiques au sein d'une organisation qui contrôlent les emplacements de contenu utilisateur (tels que les boîtes aux lettres, les comptes OneDrive et les sites Microsoft Office SharePoint Online) que les gestionnaires de découverte électronique peuvent rechercher. Ils contrôlent également qui peut accéder aux cas d'eDiscovery utilisés pour gérer les enquêtes juridiques, les ressources humaines ou d'autres enquêtes au sein de votre organisation.

![Les limites de conformité consistent en des filtres d'autorisations de recherche qui contrôlent l'accès aux agences et aux groupes de rôles d'administrateur qui contrôlent l'accès aux cas de découverte électronique.](../media/M365_ComplianceBoundary_OrgChart_v2.png)

Définissez des limites de conformité pour les enquêtes eDiscovery :

1. [Identifier un attribut utilisateur pour définir vos agences](set-up-compliance-boundaries.md#step-1-identify-a-user-attribute-to-define-your-agencies)
1. [Créer un groupe de rôles pour chaque agence](set-up-compliance-boundaries.md#step-2-create-a-role-group-for-each-agency)
1. [Créer un filtre d'autorisations de recherche pour appliquer la limite de conformité](set-up-compliance-boundaries.md#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)
1. [Créer un dossier eDiscovery pour une enquête intra-agence](set-up-compliance-boundaries.md#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

### <a name="step-5-optional-learn-about-content-search-tool"></a>Étape 5 (facultative) : [En savoir plus sur l'outil de recherche de contenu](search-for-content.md)

Utilisez l'outil de recherche de contenu dans le portail de conformité Microsoft Purview pour rechercher rapidement des e-mails dans les boîtes aux lettres Exchange, des documents dans des sites SharePoint et des emplacements OneDrive, et des conversations de messagerie instantanée dans Skype Entreprise. Vous pouvez utiliser l'outil de recherche de contenu pour rechercher des e-mails, des documents et des conversations de messagerie instantanée dans des outils de collaboration tels que Microsoft Teams et Microsoft 365 Groups.

- [En savoir plus sur la recherche de la découverte électronique (Premium)](search-for-content.md#search-for-content)

## <a name="information-protection"></a>Protection des informations

**Découvrir, classez et protégez vos informations sensibles**

Implémentez Microsoft Purview Information Protection et les étiquettes de confidentialité pour vous aider à découvrir, classer et protéger votre contenu sensible où qu’il se trouve et ou qu’il se déplace.

### <a name="step-1-start-your-information-protection-trial"></a>Étape 1 : [Démarrer votre essai de protection des informations](mip-easy-trials.md)

> [!TIP]
> Meilleures pratiques d'essai : Jour 1

Les clients éligibles peuvent activer les étiquettes et les stratégies par défaut pour Microsoft Purview Information Protection. Lorsque vous activez la configuration par défaut dans la version d’évaluation, il faut environ 2 minutes pour configurer toutes les stratégies de votre client et jusqu’à 24 heures pour voir les résultats de ces stratégies par défaut.

En choisissant la configuration par défaut, en 1 clic, se configure automatiquement :

- Étiquettes de sensibilité et politique d'étiquette de sensibilité
- Étiquetage automatique côté client
- Étiquetage automatique côté service
- Stratégies de prévention des pertes de données (DLP) pour les équipes et les appareils

[Activer les étiquettes et stratégies par défaut.](mip-easy-trials.md#activate-the-default-labels-and-policies) Si nécessaire, vous pouvez modifier manuellement une fois la configuration terminée.

### <a name="step-2-automatically-apply-sensitivity-labels-to-documents"></a>Étape 2 : [Appliquer automatiquement des étiquettes de sensibilité aux documents](apply-sensitivity-label-automatically.md)

> [!TIP]
> Meilleure pratique d'essai : configuration dans les 30 premiers jours

Lorsque vous créez une étiquette de confidentialité, vous pouvez attribuer automatiquement cette étiquette au contenu lorsque celle-ci répond aux conditions que vous spécifiez.

1. [Créer et configurer des étiquettes de confidentialité](create-sensitivity-labels.md#create-and-configure-sensitivity-labels)
1. [Publier la politique d'étiquette de sensibilité à tous les utilisateurs](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
1. [Créer une politique d'étiquetage automatique](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
   - Choisissez les informations auxquelles vous souhaitez appliquer l'étiquette
   - Définir les emplacements pour appliquer l'étiquette
   - Sélectionnez l'étiquette à appliquer
   - [Exécutez une stratégie en mode de simulation](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)

![Nouvelle configuration de stratégies pour l’étiquetage automatique.](../media/auto-labeling-wizard.png)

### <a name="step-3-review-and-turn-on-auto-labeling-policy"></a>Étape 3 : [Examiner et activer la politique d'étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)

Désormais, sur la page **Protection des informations** > , étiquetage automatique, vous voyez votre politique d'**étiquetage automatique** dans la section **Simulation**.

Sélectionnez votre stratégie pour voir les détails de la configuration et de l'état. Une fois la simulation terminée, sélectionnez l'onglet Éléments à examiner pour voir quels e-mails ou documents correspondaient aux règles spécifiées.

Lorsque vous êtes prêt à exécuter la stratégie sans simulation, sélectionnez l’option **Activer la stratégie**.

## <a name="insider-risk-management"></a>Gestion des risques internes

**Détecter et corriger les risques d'initiés**

Tirez parti de l’intelligence artificielle pour vous aider à identifier, trier et corriger rapidement les risques internes. À l’aide des journaux d’Microsoft 365 et des services Azure, vous pouvez définir des stratégies qui surveillent les signaux de risque interne, puis prendre des mesures correctives telles que la promotion de l’éducation des utilisateurs ou l’ouverture d’une enquête.

### <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Étape 1 (obligatoire) : [Activer les autorisations pour la gestion des risques internes](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management)

> [!TIP]
> Meilleures pratiques d'essai : Jour 1

Il existe quatre groupes de rôles utilisés pour configurer les autorisations pour gérer les fonctionnalités de gestion des risques internes.

[Ajoutez des utilisateurs à un groupe de rôles de gestion des risques d'initiés.](insider-risk-management-configure.md#add-users-to-an-insider-risk-management-role-group)

Si vous ne pouvez pas voir les autorisations, veuillez contacter votre administrateur de locataire pour attribuer les bons rôles.

### <a name="step-2-start-with-user-quick-start-guide"></a>Étape 2 : [Démarrer avec le guide de démarrage rapide de l'utilisateur](insider-risk-management-configure.md#recommended-actions-preview)

Lancez-vous rapidement et tirez le meilleur parti des capacités de gestion des risques internes grâce aux actions recommandées. Incluses sur la page Présentation, les actions recommandées vous guident tout au long des étapes de configuration et de déploiement des stratégies et pour entreprendre des actions d'investigation pour les actions des utilisateurs qui génèrent des alertes à partir des correspondances de stratégies.

[Sélectionnez une recommandation dans la liste](insider-risk-management-configure.md#recommended-actions-preview) pour commencer à configurer la gestion des risques internes.

![Actions recommandées par la gestion des risques internes.](../media/insider-risk-recommended-actions.png)

Chaque action recommandée vous guide à travers les activités requises pour la recommandation, y compris les exigences, à quoi s'attendre et l'impact de la configuration de la fonctionnalité dans votre organisation.

### <a name="step-3-required-enable-the-microsoft-365-audit-log"></a>Étape 3 (obligatoire) : [Activer le journal d'audit Microsoft 365](insider-risk-management-configure.md#step-2-required-enable-the-microsoft-365-audit-log)

L'audit est activé par défaut pour les organisations Microsoft 365. Certaines organisations peuvent avoir désactivé l'audit pour des raisons spécifiques. Si l'audit est désactivé pour votre organisation, c'est peut-être parce qu'un autre administrateur l'a désactivé. Nous vous recommandons de confirmer que vous pouvez réactiver l'audit lorsque vous terminez cette étape.

Pour obtenir des instructions détaillées sur l'activation de l'audit, consultez [Activer ou désactiver la recherche dans le journal d'audit](turn-audit-log-search-on-or-off.md). Une fois l’audit activé, le message qui apparaît indique que le journal d’audit est en cours de préparation et que vous pourrez effectuer une recherche environ deux heures après la fin de la préparation. Vous n'avez à faire cette action qu'une seule fois. Pour plus d'informations sur l'utilisation du journal d'audit Microsoft 365, consultez [Rechercher dans le journal d'audit](search-the-audit-log-in-security-and-compliance.md).

### <a name="step-4-required-enable-and-view-insider-risk-analytics-insights"></a>Étape 4 (obligatoire) : [Activer et afficher les informations d'analyse des risques d'initiés](insider-risk-management-configure.md#step-3-optional-enable-and-view-insider-risk-analytics-insights)

L'analyse de la gestion des risques d'initiés vous permet d'effectuer une évaluation des risques d'initiés potentiels dans votre organisation sans configurer de politiques de risque d'initiés. Les résultats de l'analyse analytique peuvent prendre jusqu'à 48 heures avant que les informations ne soient disponibles sous forme de rapports pour examen. Pour en savoir plus sur les informations analytiques, consultez [Paramètres de gestion des risques d'initiés : Analytics (préversion)](insider-risk-management-settings.md) et regardez la [vidéo Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) pour vous aider à comprendre votre position de risque d'initiés et vous aider à prendre des mesures en mettant en place des politiques appropriées pour identifier les utilisateurs à risque.

Pour activer l'analyse des risques d'initiés, vous devez être membre de Insider Risk Management ou Insider Risk Management Admin. [Effectuez ces étapes pour activer l'analyse des risques d'initiés](insider-risk-management-configure.md).

## <a name="records-management"></a>Gestion des enregistrements

**Gérez les éléments à valeur élevée pour les exigences de conservation des enregistrements professionnelles, légales ou réglementaires :**

Utilisez les fonctionnalités de gestion des enregistrements Microsoft Purview pour automatiser le calendrier de conservation des enregistrements réglementaires, juridiques et critiques de l'entreprise. Tirez parti des fonctionnalités d’automatisation de la création à la collaboration, pour déclarer des enregistrements, conserver le contenu et les supprimer à la fin.

### <a name="step-1-mark-contents-as-records"></a>Étape 1 : Marquer le contenu en tant qu’enregistrements  

> [!TIP]
> Meilleures pratiques d'essai : Jour 1

Lorsque le contenu est déclaré un enregistrement, des restrictions sont imposées à l'élément en termes d'actions autorisées ou bloquées, des activités supplémentaires concernant les éléments sont enregistrées et vous disposez d'une preuve de disposition si les éléments sont supprimés à la fin de leur période de conservation.

- Créer une étiquette de rétention qui déclare le contenu en tant qu'enregistrement ou enregistrement réglementaire

### <a name="step-2-review-content-to-approve-before-its-permanently-deleted"></a>Étape 2 : Vérifier le contenu à approuver avant sa suppression définitive

> [!TIP]
> Meilleures pratiques d'essai : Jour 1

À la fin de la période de rétention, les utilisateurs que vous spécifiez (« reviseurs ») seront invités à examiner le contenu et à approuver l'action d'élimination permanente. Cela prend en charge si une action différente de la suppression est plus appropriée, comme l’affectation d’une période de rétention différente au contenu ou la suspension de la suppression pour un audit.

- Créer une étiquette de rétention qui utilise la révision de disposition

### <a name="step-3-apply-labels-automatically-to-content-that-matches-specific-conditions"></a>Étape 3 : Appliquer automatiquement des étiquettes au contenu qui correspond à des conditions spécifiques

> [!TIP]
> Meilleure pratique d'essai : configuration dans les 30 premiers jours

L'application automatique d'étiquettes évite aux utilisateurs d'avoir à effectuer manuellement les activités d'étiquetage. Vous pouvez appliquer automatiquement des étiquettes de rétention à du contenu lorsque celui-ci ne contient pas encore d’étiquette de rétention appliquée et des informations sensibles, des mots clés, des propriétés pouvant faire l’objet d’une recherche ou une correspondance pour des classifieurs pouvant être formés.

- Application automatique d’étiquettes de rétention au contenu incluant des types spécifiques d’informations sensibles
- Appliquer automatiquement des étiquettes de rétention au contenu à l'aide de classificateurs pouvant être entraînés
- Application automatique des étiquettes de rétention comprenant des mots clés ou des propriétés pouvant faire l’objet d’une recherche

## <a name="additional-trials-and-add-ons"></a>Essais et modules complémentaires supplémentaires

### <a name="compliance-manager-premium-assessments"></a>Évaluations des primes du responsable de la conformité

**Évaluer les risques et réagir efficacement**

Aidez votre organisation à évaluer les risques et à répondre efficacement aux exigences nationales, régionales et industrielles régissant la collecte et l'utilisation des données.

[Plus d'informations sur l'essai des évaluations premium de Compliance Manager](compliance-easy-trials-compliance-manager-assessments.md).

[Guide opérationnel d'essai : évaluations premium du Gestionnaire de conformité Microsoft Purview](compliance-easy-trials-compliance-manager-assessment-playbook.md)

### <a name="microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests"></a>Gestion des risques liés à la confidentialité Microsoft Priva et demandes de droits d'objet Microsoft Priva

**Identifier et prévenir les risques de confidentialité**

Identifiez et protégez de manière proactive les risques de confidentialité tels que la thésaurisation des données, les transferts de données et le partage excessif des données, et aidez votre organisation à automatiser et à gérer les demandes de sujets à grande échelle.

[En savoir plus sur Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management).

[Playbook d'essai : Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management-trial-playbook)

## <a name="additional-resources"></a>Ressources supplémentaires

**Qu'inclut-il ?** : pour une liste complète des solutions et fonctionnalités de conformité Microsoft Purview répertoriées par niveau de produit, consultez la [Matrice des fonctionnalités](https://go.microsoft.com/fwlink/?linkid=2139145).

**Bibliothèque de contenu technique de sécurité Microsoft** : explorez cette bibliothèque pour trouver des guides interactifs et d'autres contenus d'apprentissage correspondant à vos besoins. [Visitez la bibliothèque](/security).

**ressources de sécurité Microsoft**: du logiciel anti-programme malveillant à la confiance zéro, obtenez toutes les ressources pertinentes pour les besoins de sécurité de votre organisation. [Visitez ressources](/security/business/resources).
