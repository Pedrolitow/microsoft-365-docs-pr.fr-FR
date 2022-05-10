---
title: Nouveautés de Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: Qu’il s’agisse d’ajouter de nouvelles solutions au Centre de conformité, de mettre à jour les fonctionnalités existantes en fonction de vos commentaires ou de déployer une documentation actualisée et mise à jour, Microsoft 365 vous aide à rester au-dessus du paysage de conformité en constante évolution. Découvrez ce que nous avons fait ce mois-ci.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 3bfa6ce581b0bd4846ebe27b95cf27d1228b10b2
ms.sourcegitcommit: f723ebbc56db8013598a88b0d7f13214d9d3eb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2022
ms.locfileid: "65294608"
---
# <a name="whats-new-in-microsoft-purview"></a>Nouveautés de Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Qu’il s’agisse d’ajouter de nouvelles solutions au [portail de conformité Microsoft Purview](microsoft-365-compliance-center.md), de mettre à jour les fonctionnalités existantes en fonction de vos commentaires ou de déployer une documentation actualisée et mise à jour, Microsoft 365 vous aide à rester au-dessus du paysage de conformité en constante évolution. Jetez un coup d’œil ci-dessous pour découvrir les nouveautés de Microsoft Purview aujourd’hui.

> [!NOTE]
> Certaines fonctionnalités de conformité sont déployées à différentes vitesses pour nos clients. Si vous ne voyez pas encore de fonctionnalité, essayez de vous ajouter à [une version ciblée](/office365/admin/manage/release-options-in-office-365).

> [!TIP]
> Vous vous intéressez à ce qui se passe dans d’autres centres d’administration ? Consultez les articles suivants :
>
> - [Nouveautés du Centre d'administration Microsoft 365](/office365/admin/whats-new-in-preview)
> - [Nouveautés du Centre d’administration SharePoint](/sharepoint/what-s-new-in-admin-center)
> - [Nouveautés de Microsoft 365 Defender](../security/defender/whats-new.md)
>
> Et visitez la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour en savoir plus sur Microsoft 365 fonctionnalités qui ont été lancées, qui ont été déployées, qui sont en cours de développement, qui ont été annulées ou qui ont été publiées précédemment.

## <a name="april-2022"></a>Avril 2022

### <a name="communication-compliance"></a>Conformité des communications

- [Créez et gérez des stratégies de conformité des communications](communication-compliance-policies.md) mises à jour avec des conseils ajoutés pour la nouvelle fonctionnalité de stratégie de message signalée par l’utilisateur pour l’intégration Microsoft Teams.
- [Démarrage avec la conformité des communications](communication-compliance-configure.md) - mise à jour pour ajouter des clarifications pour l’abonnement F5 et les licences.

### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Liste des modèles du Gestionnaire](compliance-manager-templates-list.md) de conformité : ajout de 6 nouveaux modèles et liens de navigation sur la page pour accéder plus facilement aux catégories de modèles.
- [Vue d’ensemble du Gestionnaire de conformité](compliance-manager.md) - Vidéo de présentation du produit mise à jour.

### <a name="compliance-offerings--service-assurance"></a>Offres de conformité & assurance du service

- [Offres de conformité](/compliance/regulatory/offering-home) : mises à jour de la couverture du service et des rapports d’audit pour les offres VPATS, SOC, ISO et FedRAMP.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- [Régir vos données avec Microsoft Purview](manage-data-governance.md) : les connecteurs de données sont supprimés de cette page et la solution de gestion des enregistrements est présentée comme un produit homologue.
- [Paramètres courants pour les stratégies de rétention et les étiquettes de rétention](retention-settings.md) : reflète les nouvelles références de navigation et d’interface utilisateur pour l’Assistant Étiquette de rétention nouvellement conçu.
- [Déclarez des enregistrements à l’aide d’étiquettes de rétention](declare-records.md) et [utilisez le contrôle de version des enregistrements pour mettre à jour les enregistrements stockés dans SharePoint ou OneDrive](record-versioning.md) : nouvelles informations sur le nouveau paramètre d’étiquette « Déverrouiller cet enregistrement par défaut » en cours de déploiement en préversion.
- [Utilisez le plan de fichiers pour créer et gérer des étiquettes de rétention](file-plan-manager.md#information-about-the-label-properties-for-import)  . La section d’importation divulgue désormais les paramètres d’étiquette qui ne sont pas actuellement pris en charge pour l’importation (révision de la disposition en plusieurs étapes et déverrouillage de cet enregistrement par défaut).

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- Articles mis à jour pour l’intégration d’appareils macOS en disponibilité générale :
  - [En savoir plus sur le point de terminaison DLP](endpoint-dlp-learn-about.md)
  - [Configurer les paramètres de protection contre la perte de données de point de terminaison](dlp-configure-endpoint-settings.md)
  - [Planifier la protection contre la perte de données (DLP)](dlp-overview-plan-for-dlp.md)
  - [Informations de référence sur la stratégie de protection contre la perte de données](dlp-policy-reference.md)
  - [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md)
- [Conditions de stratégie DLP, exceptions et actions](dlp-conditions-and-exceptions.md) : ajout de conseils pour l’action Modifier l’objet.
- [Informations de référence sur la stratégie de protection contre la perte](dlp-policy-reference.md) de données - Prédicats SPO/ODB en disponibilité générale ; mise à jour avec de nouvelles instructions sur le traitement des règles sur les points de terminaison.

### <a name="device-onboarding"></a>Intégration d’appareils

- Articles mis à jour pour l’intégration d’appareils macOS en disponibilité générale :
  - [Intégrer des appareils macOS à Microsoft 365 vue d’ensemble](device-onboarding-macos-overview.md)
  - [Intégrer et désactiver les appareils macOS dans les solutions de conformité à l’aide d’Intune pour les clients Microsoft Defender pour points de terminaison](device-onboarding-offboarding-macos-intune-mde.md)
  - [Intégrer et déconnecter des appareils macOS dans les solutions Microsoft Purview à l’aide d’Intune](device-onboarding-offboarding-macos-intune.md)
  - [Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide de JAMF Pro pour les clients de Microsoft Defender pour point de terminaison](device-onboarding-offboarding-macos-jamfpro-mde.md)
  - [Intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de JAMF Pro](device-onboarding-offboarding-macos-jamfpro.md)

### <a name="information-barriers"></a>Obstacles aux informations

- [Utiliser les obstacles à l’information avec SharePoint](/sharepoint/information-barriers) : conseils ajoutés pour la prise en charge des nouveaux canaux privés dans SharePoint.
- [Gérer les stratégies d’obstacles à l’information](information-barriers-edit-segments-policies.md) : conseils ajoutés pour supprimer ensemble des segments et des stratégies/segments.

### <a name="microsoft-priva"></a>Microsoft Priva

- [Politiques de gestion des risques liés à la confidentialité](/privacy/priva/risk-management) : nouvelles pages, mises à jour importantes et restructuration du contenu des stratégies; détails ci-dessous :
  - [Stratégies de gestion des risques liés à la confidentialité](/privacy/priva/risk-management-policies) : ajout de détails importants sur la configuration et la gestion des stratégies qui s’appliquent à toutes les stratégies; ajout de liens vers de nouvelles pages pour chacun des trois types de stratégie.
  - [Stratégies de surexposition des données](/privacy/priva/risk-management-policy-data-overexposure) : expose les besoins et les utilisations de la stratégie ; explique les paramètres par défaut pour la création out-of-box et des instructions détaillées pour la personnalisation des paramètres.
  - [Stratégies de transfert de données](/privacy/priva/risk-management-policy-data-transfer) : met en évidence la nouvelle condition de la stratégie pour détecter les transferts en dehors de l’organisation ; expose les besoins et les utilisations de la stratégie ; explique les paramètres par défaut pour la création out-of-box et des instructions détaillées pour la personnalisation des paramètres.
  - [Stratégies de réduction des données](/privacy/priva/risk-management-policy-data-minimization) : articule les besoins et les utilisations de la stratégie ; explique les paramètres par défaut pour la création out-of-box et des instructions détaillées pour la personnalisation des paramètres.
  - [Examiner et corriger les alertes](/privacy/priva/risk-management-alerts) : ajout de détails de clarification et modifications de mise en forme pour améliorer la lisibilité.
  - [Notifications utilisateur](/privacy/priva/risk-management-notifications) : ajout d’informations sur la fonctionnalité d’aperçu et de personnalisation du contenu des notifications par e-mail.
- [Créer une demande de droits d’objet](/privacy/priva/subject-rights-requests-create) : ajout d’une section sur la prise en main de votre première demande avec les paramètres par défaut pour explorer les fonctionnalités.
- [Passez en revue les données d’une demande de droits d’objet](/privacy/priva/subject-rights-requests-data-review) : ajout de détails expliquant les éléments prioritaires à examiner et comment les trouver, et la nécessité de configurer la correspondance des données pour obtenir ces informations.
- [Rechercher et visualiser des données personnelles](/privacy/priva/priva-data-profile) : il est précisé que les utilisateurs doivent configurer la correspondance des données afin de recevoir des insights pour « Éléments ayant le plus de contenu de sujet de données » sous « Insights clés ».
- [Correspondance des données pour les demandes de droits d’objet](/privacy/priva/subject-rights-requests-data-match) : clarification de la progression de l’étape dans ce processus et ajout de la deuxième étape de création de types d’informations sensibles.

### <a name="sensitive-information-types"></a>Types d'informations sensibles

- [Utilisez des entités nommées dans les stratégies DLP](named-entities-use.md) - ga d’entités nommées.
- [En savoir plus sur les entités nommées](named-entities-learn.md) - ga d’entités nommées.
- [Définitions d’entités de types d’informations sensibles](sensitive-information-type-entity-definitions.md) : ga d’entités nommées et mises à jour de modèle.
- [En savoir plus sur les types d’informations sensibles](sensitive-information-type-learn-about.md) ( ga) d’entités nommées.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- [Utilisez des étiquettes de confidentialité pour protéger le contenu dans les Microsoft Teams, les groupes Microsoft 365 et les sites SharePoint](sensitivity-labels-teams-groups-sites.md#configure-site-sharing-permissions-by-using-powershell-advanced-settings) : nouvelle configuration désormais disponible en préversion pour les autorisations de partage de site à l’aide de paramètres avancés PowerShell.
- [Restreindre l’accès au contenu à l’aide d’étiquettes de confidentialité pour appliquer le chiffrement](encryption-sensitivity-labels.md) : ajout du problème connu de spécification d’un groupe contenant des contacts de messagerie, avec un lien vers la base de connaissances publiée pour plus d’informations et des solutions de contournement.
- [Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) : suppression du problème connu lié à la suppression OneDrive sites affichés de manière incorrecte dans les résultats de la simulation pour les stratégies d’étiquetage automatique)
- [Activez la co-création pour les fichiers chiffrés avec des étiquettes de confidentialité](sensitivity-labels-coauthoring.md) . Suite aux commentaires des clients, supprimez la légende dans la section Prérequis que cette fonctionnalité n’est pas encore prise en charge par le canal Semi-Annual Enterprise, puis ajoutez Semi-Annual Enterprise Channel (préversion) avec la version minimale 2202.
- [Gérer les étiquettes de confidentialité dans Office applications](sensitivity-labels-office-apps.md) : les détails de prise en charge de l’application d’une étiquette par défaut aux documents existants sont mis à jour pour corriger que sur Windows, cette version est toujours déployée dans le canal bêta et est maintenant entièrement déployée pour le web.

### <a name="changes-to-product-names"></a>Modifications apportées aux noms des produits

Pour relever les défis du milieu de travail décentralisé et riche en données d’aujourd’hui, nous introduisons [Microsoft Purview](https://aka.ms/microsoftpurview), un ensemble complet de solutions qui vous aide à comprendre, régir et protéger l’ensemble de votre patrimoine de données. Cette nouvelle famille de marques combine les fonctionnalités de l’ancienne carte de données Microsoft Purview et le portefeuille de conformité Microsoft 365 sur lequel les clients s’appuient déjà, fournissant une gouvernance unifiée des données et une gestion des risques pour votre organisation.

| **Ancien nom** | **Nouveau nom** | **Description** |
|:----------------|:-------------|:----------------|
| audit avancé Microsoft 365 <br><br> audit de base Microsoft 365 | Audit de Microsoft Purview (Premium) <br><br> Audit Microsoft Purview (Standard)| Les solutions d’audit fournissent une solution intégrée pour aider les organisations à répondre efficacement aux événements de sécurité, aux enquêtes judiciaires, aux enquêtes internes et aux obligations de conformité. Pour plus d’informations, consultez [Microsoft Purview Advanced Audit (Premium)](advanced-audit.md) et [Microsoft Purview Advanced Audit (Standard).](set-up-basic-audit.md) |
| conformité des communications Microsoft 365 | Conformité des communications Microsoft Purview | La conformité des communications permet de réduire les risques en vous aidant à détecter, capturer et prendre rapidement des mesures correctives pour les canaux de communication d’entreprise et les violations de stratégie. Pour en savoir plus, consultez [Microsoft Purview Communication Compliance](communication-compliance-solution-overview.md). |
| Gestionnaire de conformité Microsoft | Gestionnaire de conformité Microsoft Purview | Le Gestionnaire de conformité peut vous aider tout au long de votre parcours de conformité, de l’inventaire des risques de protection de vos données à la gestion des complexités de l’implémentation de contrôles, la mise à jour des réglementations et des certifications et la création de rapports aux auditeurs. Pour plus d’informations, consultez [le Gestionnaire de conformité Microsoft Purview](compliance-manager.md). |
| clé client Microsoft 365 | Clé client Microsoft Purview | La clé client offre une protection supplémentaire contre l’affichage des données par des systèmes ou du personnel non autorisés, et complète le chiffrement de disque BitLocker dans les centres de données Microsoft. Pour plus d’informations, consultez [la clé client Microsoft Purview](customer-key-overview.md). |
| Customer Lockbox dans Office 365 | Microsoft Purview Customer Lockbox | Customer Lockbox garantit que Microsoft ne peut pas accéder à votre contenu pour effectuer des opérations de service sans votre approbation explicite. Customer Lockbox vous permet d’entrer dans le processus de flux de travail d’approbation utilisé par Microsoft pour vous assurer que seules les demandes autorisées autorisent l’accès à votre contenu. Pour plus d’informations, consultez [Microsoft Purview Customer Lockbox](customer-lockbox-requests.md). |
| Protection contre la perte de données | Protection contre la perte de données Microsoft Purview | DLP permet de protéger les données sensibles et de réduire les risques en empêchant les utilisateurs de partager ces données de manière inappropriée avec des personnes qui ne devraient pas les avoir. Pour plus d’informations, consultez [Microsoft Purview Data Loss Prevention](dlp-learn-about-dlp.md). |
| Chiffrement à double clé pour Microsoft 365 | Chiffrement à double clé Microsoft Purview | Double Key Encryption (DKE) utilise deux clés ensemble pour accéder au contenu protégé. Microsoft stocke une clé dans Microsoft Azure, et vous conservez l’autre clé. Pour en savoir plus, consultez [Le chiffrement à double clé Microsoft Purview](double-key-encryption.md) |
| Microsoft 365 obstacles à l’information | Cloisonnement de l’information Microsoft Purview | Les obstacles à l’information sont une solution qui limite la communication et la collaboration entre certaines personnes au sein de votre organisation afin de protéger les informations internes. Pour en savoir plus, consultez [Microsoft Purview Information Barriers](information-barriers-solution-overview.md). |
| Microsoft Information Protection | Protection de l'information Microsoft Purview | La protection des informations vous aide à découvrir, classifier et protéger des informations sensibles où qu’elles résident ou voyagent. Pour en savoir plus, consultez [Microsoft Purview Information Protection](information-protection.md). |
| Gouvernance des informations Microsoft | Gestion du cycle de vie des données Microsoft Purview | La gestion du cycle de vie des données vous fournit des outils et des fonctionnalités pour conserver le contenu dont vous avez besoin pour conserver et supprimer le contenu que vous n’avez pas. Pour plus d’informations, consultez [Gestion du cycle de vie des données Microsoft Purview](data-lifecycle-management.md). |
| Microsoft 365 : gestion des risques internes | Microsoft Purview : gestion des risques internes | La gestion des risques internes utilise l’ensemble des indicateurs de service et tiers pour vous aider à identifier, trier et agir rapidement sur l’activité des utilisateurs à risque. Pour en savoir plus, consultez [Microsoft Purview Insider Risk Management](insider-risk-management.md). |
| Chiffrement de messages Office 365 | Chiffrement des messages Microsoft Purview | Avec Le chiffrement des messages, votre organisation peut envoyer et recevoir des messages électroniques chiffrés entre des personnes internes et externes à votre organisation. Pour plus d’informations, consultez [Chiffrement des messages Microsoft Purview](ome.md). |
| Privileged Access Management dans Microsoft 365 | Privileged Access Management Microsoft Purview | Privileged Access Management permet de protéger votre organisation contre les violations et de respecter les meilleures pratiques de conformité en limitant l’accès permanent aux données sensibles ou l’accès aux paramètres de configuration critiques. Pour plus d’informations, consultez [Microsoft Purview Privileged Access Management](privileged-access-management-solution-overview.md). |
| Connecteurs de données Microsoft | Connecteurs de données Microsoft Purview | Microsoft 365 permet aux administrateurs d’utiliser des connecteurs de données pour importer et archiver des données non-Microsoft tierces à partir de plateformes de médias sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration de documents dans des boîtes aux lettres de votre organisation Microsoft 365. Pour plus d’informations, consultez [les connecteurs de données Microsoft Purview](compliance-extensibility.md). |
| Microsoft 365 advanced eDiscovery <br><br> Microsoft 365 Core eDiscovery | Microsoft Purview eDiscovery (Premium) <br><br> Microsoft Purview eDiscovery (Standard) | La découverte électronique, ou eDiscovery, est le processus d'identification et de livraison d'informations électroniques qui peuvent être utilisées comme preuves dans des affaires juridiques. Pour en savoir plus, consultez [Microsoft Purview eDiscovery (Premium)](overview-ediscovery-20.md) et [Microsoft Purview eDiscovery (Standard).](get-started-core-ediscovery.md) |
| Centre de conformité Microsoft 365 | Portail de conformité Microsoft Purview | Portail d’administration pour accéder aux solutions et au catalogue de solutions dans la suite Microsoft 365 E5 Conformité. Pour en savoir plus, consultez le [portail de conformité Microsoft Purview](microsoft-365-compliance-center.md). |

## <a name="march-2022"></a>Mars 2022

### <a name="communication-compliance"></a>Conformité des communications

- [Examiner et corriger les alertes de conformité des communications : instructions supprimées](communication-compliance-investigate-remediate.md) pour la vue d’annotation déconseillée.

### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Utilisation des actions d’amélioration](compliance-manager-improvement-actions.md), [Démarrage avec le Gestionnaire de conformité](compliance-manager-setup.md) : ajout d’informations sur d’autres actions d’amélioration qui peuvent être automatiquement surveillées et testées (« évaluation continue de la conformité ») ; cela inclut de nouvelles capacités pour parenter l’état de test d’une action à celui d’une autre action.

### <a name="data-classification"></a>Classification des données

- [Prise en main avec l’Explorateur de contenu](data-classification-content-explorer.md) - Teams instructions ajoutées, la section relative aux licences pointait vers les descriptions de service.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- [Les stratégies de rétention pour Yammer](create-retention-policies.md#retention-policy-for-yammer-locations) sont désormais en disponibilité générale (GA).
- Prise en charge des canaux partagés, actuellement en préversion. Lorsque vous configurez une stratégie de rétention pour l’emplacement du message de canal Teams, tous les canaux partagés héritent des paramètres de rétention de leur équipe parente.
- [Limites par locataire pour la disposition du contenu](retention-limits.md#maximum-number-of-items-for-disposition).

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- [Protection contre la perte de données et Microsoft Teams](dlp-microsoft-teams.md) : préversion publique du contenu Share Teams Channels.
- [Démarrage avec l’extension de conformité Microsoft](dlp-chrome-get-started.md) - préversion publique des groupes d’applications restreints, supprimez les instructions de clé de Registre, configuration désormais activée par défaut.
- [Configurez les paramètres de protection contre la perte de données](dlp-configure-endpoint-settings.md) de point de terminaison : nouveau pour la préversion publique des groupes d’applications restreints.
- [Informations de référence sur la stratégie de protection contre la perte de données](dlp-policy-reference.md) : mises à jour pour la préversion publique des groupes d’applications restreints.
- [Démarrage avec protection contre la perte de données pour les Power BI](dlp-powerbi-get-started.md) : nouveauté de la préversion publique.

### <a name="insider-risk-management"></a>Gestion des risques internes

- [Démarrage avec la gestion des risques internes](insider-risk-management-configure.md) : ajout de nouvelles tâches pour l’aide sur les actions recommandées.
- [Démarrage avec les paramètres de gestion des risques internes](insider-risk-management-settings.md) : nouvelles mises à jour pour les fonctionnalités de notification et d’alertes par e-mail, nouvelles mises à jour pour les notifications analytiques.

### <a name="microsoft-information-protection"></a>Microsoft Information Protection

- [Prise en charge des notes de publication du jeu de caractères sur deux octets](mip-dbcs-relnotes.md) - ajout de conseils pour macOS.

### <a name="microsoft-priva"></a>Microsoft Priva

- [Configurer les paramètres Priva](/privacy/priva/priva-settings) : mise à jour des informations de clarification sur les périodes de rétention des données pour les demandes de droits des personnes concernées ; ajout de détails sur la gestion et l’application de balises de révision des données pour les demandes de droits d’objet.
- [Créer une demande de droits d’objet](/privacy/priva/subject-rights-requests-create) : ajout de détails sur l’affinement des recherches et le choix des conditions et des attributs ; ajout d’informations sur les nouvelles fonctionnalités qui permettent aux utilisateurs de sélectionner toutes les versions de SharePoint éléments dans leur recherche (par rapport au paramètre par défaut, qui retourne uniquement la version actuelle des éléments SharePoint).
- [Passer en revue les données d’une demande de droits d’objet](/privacy/priva/subject-rights-requests-data-review) : ajout de détails à l’étape 3 pour l’examen des éléments au cours de l’étape de révision des données, y compris le marquage des fichiers en tant qu’inclusion/exclusion, l’annotation des fichiers pour appliquer des actions, l’application de balises et la saisie de notes.
- [Générer des rapports et répondre à une demande de droits d’objet](/privacy/priva/subject-rights-requests-reports) : ajout de détails sur la façon de comprendre les rapports ; clarifié quand un package d’exportation est généré et comment utiliser son contenu ; ajout d’informations sur les journaux d’audit, les rapports de fichiers étiquetés et les périodes de rétention pour les données et les rapports SRR.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- [Étiquettes de confidentialité pour Teams](sensitivity-labels-teams-groups-sites.md) :
  - Prise en charge des canaux partagés, actuellement en préversion. Si une équipe a des canaux partagés, elle hérite automatiquement des paramètres d’étiquette de confidentialité de son équipe parente, et cette étiquette ne peut pas être supprimée ou remplacée par une autre étiquette.
  - Prise en charge des modèles, précédemment répertoriés comme [non pris en charge avec les API Teams Graph et les applets de commande PowerShell]( /microsoftteams/sensitivity-labels#limitations).  
- Pour l’audit de Word, Excel et PowerPoint sur le web, le texte de justification est maintenant entièrement déployé.
- L’application d’une étiquette par défaut aux documents existants pour Word, Excel et PowerPoint sur le web est maintenant entièrement déployée.

## <a name="february-2022"></a>Février 2022

### <a name="ediscovery"></a>eDiscovery

- [Gérer les modèles de communication de consignation dans eDiscovery (Premium)](advanced-ediscovery-communications-library.md) : les gestionnaires eDiscovery peuvent désormais créer des modèles de communication de consignation qui peuvent être utilisés dans n’importe quel cas eDiscovery (Premium) dans l’organisation.
- [Gérer les agents émetteurs dans eDiscovery (Premium)](advanced-ediscovery-issuing-officers.md) : les gestionnaires eDiscovery peuvent ajouter une liste d’agents émetteurs qui peuvent être affectés aux communications des consignatateurs dans n’importe quel cas eDiscovery (Premium) dans l’organisation.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- [Les étendues adaptatives pour les](retention.md#adaptive-or-static-policy-scopes-for-retention) stratégies de rétention et les stratégies d’étiquette de rétention sont désormais en disponibilité générale (GA). Les instructions de [configuration d’une étendue adaptative](retention-settings.md#to-configure-an-adaptive-scope) incluent désormais plus d’informations pour SharePoint étendues de site : Référence de billet de blog pour l’utilisation de propriétés de site personnalisées et utilisation de la propriété site SiteTemplate pour inclure ou exclure des types de sites spécifiques avec le générateur de requêtes avancé.
- [La recherche de stratégie](retention.md#policy-lookup) dans la solution de gestion du cycle de vie des données est désormais généralement disponible (disponibilité générale).
- PowerShell alternative au paramètre de gestion des enregistrements qui permet aux utilisateurs de supprimer des éléments étiquetés dans SharePoint et OneDrive à l’aide de AllowFilesWithKeepLabelToBeDeletedSPO et AllowFilesWithKeepLabelToBeDeletedODB à partir de [Get-PnPTenant](/powershell/module/sharepoint-pnp/get-pnptenant) et [Set-PnPTenant]( /powershell/module/sharepoint-pnp/set-pnptenant).

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Nouvelles instructions [Pourquoi choisir l’étiquetage intégré sur le complément AIP pour les applications Office](sensitivity-labels-aip.md) si vous utilisez le client d’étiquetage unifié Azure Information Protection (AIP) pour Windows ordinateurs. Cette page contient des informations sur la nouvelle préversion privée pour Office applications.
- Nouveaux paramètres pour les stratégies [d’étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) :
  - Paramètres supplémentaires pour l’e-mail afin de prendre en charge l’application systématique d’une étiquette de confidentialité correspondante et d’appliquer le chiffrement aux e-mails reçus de l’extérieur de l’organisation.
  - Les exclusions pour des instances spécifiques (utilisateurs, groupes, sites) sont prises en charge à l’aide de la nouvelle option **Exclus** lorsque la sélection par défaut de **Tout** est spécifiée pour **Inclus**.
- Maintenant en préversion : les appareils mobiles (iOS et Android) prennent en charge [la co-édition](sensitivity-labels-coauthoring.md) lorsque vous avez des versions minimales et que vous optez pour cette préversion.
- La prise en charge de la définition du type de lien de partage par défaut est étendue aux documents individuels dans SharePoint et OneDrive. Pour plus d’informations, consultez le nouvel article [Utiliser des étiquettes de confidentialité pour configurer le type de lien de partage par défaut pour les sites et les documents dans SharePoint et OneDrive]( sensitivity-labels-default-sharing-link.md).
- Teams centre d’administration prend désormais en charge les étiquettes de conteneur (étiquettes de confidentialité avec l’étendue des groupes & sites).

## <a name="january-2022"></a>Janvier 2022

### <a name="microsoft-purview-data-lifecycle-management"></a>Gestion du cycle de vie des données Microsoft Purview

- La documentation relative à ce qui était auparavant Microsoft Information Governance a été considérablement révisée et restructurée pour vous aider à trouver plus facilement des informations relatives aux solutions que vous configurez dans le portail de conformité Microsoft Purview : Connecteurs de données, Gestion du cycle de vie des données et Gestion des enregistrements. Dans le cadre de cette révision, la documentation fournit une distinction plus claire entre les scénarios de rétention pour la gestion du cycle de vie des données et la gestion des enregistrements.
- [Apprenez-en davantage sur la gestion du cycle de vie des données](data-lifecycle-management.md) , nouveauté pour prendre en charge la restructuration.
- [Démarrage avec la gestion du cycle de vie des données](get-started-with-data-lifecycle-management.md) - nouveau, pour remplacer « Démarrage par rétention », cet article inclut les étapes de prise en main de toutes les fonctionnalités de gestion du cycle de vie des données, notamment la rétention.
- [Créez des étiquettes de rétention pour les exceptions à vos stratégies de rétention](create-retention-labels-data-lifecycle-management.md) . Nouveau scénario identifié pour l’utilisation d’étiquettes de rétention pour la gestion du cycle de vie des données plutôt que pour la gestion des enregistrements.
- [En savoir plus sur les boîtes aux lettres d’archivage](archive-mailboxes.md) - nouvelles, pour prendre en charge la restructuration, contient des informations conceptuelles qui se trouvaient précédemment dans l’article « Activer les boîtes aux lettres d’archivage ».

### <a name="microsoft-priva"></a>Microsoft Priva

- [La gestion de la confidentialité est désormais Microsoft Priva](/privacy/priva/priva-overview) - mise à jour pour renommer le produit et ses solutions, Priva Privacy Risk Management et Priva Subject Rights Requests.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Prise en charge des nouveaux [groupes de rôles et rôles](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels), désormais en préversion.
- Nouvelles [fonctionnalités de surveillance pour les](apply-sensitivity-label-automatically.md#monitoring-your-auto-labeling-policy) stratégies d’étiquetage automatique.
- Déploiement à présent : étiquette par défaut pour les documents existants et texte de justification pour Office sur le Web.
- Annoncé pour le canal de Semi-Annual Enterprise juillet avec la version 2202+: Co-création et audit pour Outlook.

## <a name="december-2021"></a>Décembre 2021

### <a name="compliance-and-service-assurance"></a>Conformité et assurance du service

- [Notification de violation d’Azure, Dynamics 365 et Windows dans le cadre du RGPD](/compliance/regulatory/gdpr-breach-notification) - mise à jour pour préciser que les clients n’ont pas besoin d’utiliser un service payant tel que Defender pour le cloud pour recevoir des notifications de sécurité et de confidentialité

### <a name="ediscovery"></a>eDiscovery

- [Flux de travail eDiscovery (Premium) pour le contenu dans Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#reference-guide) - mis à jour avec un nouveau guide de référence rapide téléchargeable pour la gestion Teams contenu dans eDiscovery (Premium)

### <a name="data-lifecycle-management"></a>Gestion du cycle de vie des données

- [Activer les boîtes aux lettres d’archivage dans le centre de conformité](enable-archive-mailboxes.md#run-diagnostics-on-archive-mailboxes) - Ajout d’une section sur le nouvel outil de diagnostic pour les boîtes aux lettres d’archivage
- [Utiliser le chargement réseau pour importer les fichiers PST de votre organisation vers Microsoft 365](use-network-upload-to-import-pst-files.md#step-2-upload-your-pst-files-to-microsoft-365) - L’importation PST prend désormais en charge AzCopy v10
- [Restaurer une boîte aux lettres inactive](restore-an-inactive-mailbox.md) - procédure révisée pour restaurer une boîte aux lettres inactive en ajoutant d’abord LegacyExchangeDN de boîte aux lettres inactive à la boîte aux lettres cible

### <a name="information-protection"></a>Protection des informations

- [Déployer une solution de protection des informations avec Microsoft Purview](information-protection-solution.md) - Nouvelles instructions pas à pas pour les clients qui recherchent une feuille de route normative pour déployer Microsoft Purview Information Protection

### <a name="retention-and-records-management"></a>Conservation et gestion des enregistrements

- Nouvelles instructions sur le [temps nécessaire à l’application des stratégies de rétention](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- Nouveaux paramètres de locataire déployés : paramètre de gestion des enregistrements qui empêche la modification des propriétés pour les éléments étiquetés SharePoint marqués comme un enregistrement et verrouillés, et autre paramètre pour empêcher les utilisateurs de déverrouiller les éléments marqués comme enregistrement

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- L’étiquetage obligatoire et une étiquette par défaut pour Power BI sont désormais en disponibilité générale (GA)

## <a name="november-2021"></a>Novembre 2021

### <a name="compliance-manager"></a>Gestionnaire de conformité

Les nouvelles mises à jour de contenu peuvent être affichées dans [les nouveautés du Gestionnaire de conformité Microsoft Purview](compliance-manager-whats-new.md).

### <a name="device-onboarding"></a>Intégration d’appareils

Les articles suivants ont été ajoutés pour l’intégration des appareils :

- [Intégration des appareils macOS dans la vue d'ensemble de Microsoft 365 (aperçu)](device-onboarding-macos-overview.md)
- [Intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de Intune (préversion)](device-onboarding-offboarding-macos-intune.md)
- [Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide d'Intune pour les clients de Microsoft Defender pour point de terminaison (aperçu)](device-onboarding-offboarding-macos-intune-mde.md)
- [Intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de JAMF Pro (préversion)](device-onboarding-offboarding-macos-jamfpro.md)
- [Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide de JAMF Pro pour les clients de Microsoft Defender pour point de terminaison (aperçu)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>eDiscovery

- [Utiliser le nouveau format de cas dans eDiscovery (Premium)](advanced-ediscovery-new-case-format.md) nouveau format de cas a été publié en disponibilité générale et renommé à partir du « grand format de cas »

### <a name="retention-and-records-management"></a>Conservation et gestion des enregistrements
- Déploiement : Nouveaux paramètres de gestion des enregistrements qui contrôlent si les éléments étiquetés dans SharePoint et OneDrive peuvent être supprimés par les utilisateurs. Auparavant, les étiquettes de rétention configurées pour conserver le contenu et qui ne marquent pas les éléments en tant qu’enregistrements ont empêché les utilisateurs de supprimer du contenu étiqueté dans SharePoint lorsque cette action était autorisée dans OneDrive. Pour plus d’informations, consultez [le fonctionnement de la rétention pour SharePoint et OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

### <a name="sensitive-information-types"></a>Types d'informations sensibles

Ajout des nouveaux articles suivants :

- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md)
- [Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md)
- [Exporter les données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md)
- [Créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-create-schema.md)
- [Hacher et charger la table de source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md)
- [Créer des données exactes correspondant au type d’informations sensibles/au package de règles](sit-get-started-exact-data-match-create-rule-package.md)
- [Tester un type d’informations sensibles correspondant exactement aux données](sit-get-started-exact-data-match-test.md)
- [Gérer votre schéma de correspondance exacte des données](sit-use-exact-data-manage-schema.md)
- [Actualiser votre fichier de table source d’informations sensibles](sit-use-exact-data-refresh-data.md)

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité
- Le nom d’étendue des étiquettes de mappage de [données Microsoft Purview](/azure/purview/create-sensitivity-label) est désormais « Ressources de données schématisées ».
