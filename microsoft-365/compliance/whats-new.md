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
ms.openlocfilehash: 2c81a6b5706ff9310b1de6b7b75f807528dd75bb
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940467"
---
# <a name="whats-new-in-microsoft-purview"></a>Nouveautés de Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Qu’il s’agisse d’ajouter de nouvelles solutions au [portail de conformité Microsoft Purview](microsoft-365-compliance-center.md), de mettre à jour les fonctionnalités existantes en fonction de vos commentaires ou de déployer une documentation actualisée et mise à jour, Microsoft 365 vous aide à rester au-dessus du paysage de conformité en constante évolution. Jetez un coup d’œil ci-dessous pour découvrir les nouveautés de Microsoft Purview aujourd’hui.

> [!NOTE]
> Certaines fonctionnalités de conformité sont déployées à différentes vitesses pour nos clients. Si vous ne voyez pas encore de fonctionnalité, essayez de vous ajouter à [une version ciblée](/office365/admin/manage/release-options-in-office-365).

> [!TIP]
> Vous vous intéressez à ce qui se passe dans d’autres centres d’administration ? Consultez les articles suivants :
>
> - [Nouveautés du Centre d’administration Microsoft 365](/office365/admin/whats-new-in-preview)
> - [Nouveautés du Centre d’administration SharePoint](/sharepoint/what-s-new-in-admin-center)
> - [Nouveautés de Microsoft 365 Defender](../security/defender/whats-new.md)
>
> Et visitez la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour en savoir plus sur les fonctionnalités de Microsoft 365 qui ont été lancées, qui sont en cours de déploiement, qui sont en cours de développement, qui ont été annulées ou qui ont été publiées précédemment.

## <a name="may-2022"></a>Mai 2022

### <a name="communication-compliance"></a>Conformité des communications

- [Rapports et audits de conformité des communications](communication-compliance-reports-audits.md) : limites de taille de fichier mises à jour pour les rapports exportés.
- [Stratégies de conformité des communications : messages signalés](communication-compliance-policies.md) par l’utilisateur clarifiés désactivant/activant le processus et clarifié le traitement pour Teams et Exchange.

### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Alertes et stratégies d’alerte](compliance-manager-alert-policies.md) : nouvelle section expliquant la stratégie de changement de score par défaut pour toutes les organisations.
- [Utilisation des actions d’amélioration](compliance-manager-improvement-actions.md) : clarification des états d’état pour l’état d’implémentation et l’état de test, faisant la distinction entre les actions automatiquement testées et les actions testées manuellement.
- [Liste des modèles](compliance-manager-templates-list.md) : ajout de deux nouveaux modèles dans la région Europe, Moyen-Orient et Afrique (EMEA) : qatar national information assurance (NIA) et la loi sur la confidentialité des données des Émirats arabes unis.

### <a name="compliance-offerings--service-assurance"></a>Offres de conformité & assurance du service

- [Cycle de vie du développement de la sécurité Microsoft](/compliance/assurance/assurance-microsoft-security-development-lifecycle) : nouvelle rubrique d’assurance SDL pour les services Microsoft.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- Actuellement déployée en préversion : nouvelle [option de réétiqueter à la fin de la période de rétention](retention-settings.md#relabeling-at-the-end-of-the-retention-period).
- Nouveau guide de déploiement : [Déployer une solution de gouvernance des données avec Microsoft Purview](data-governance-solution.md)
- Correction dans la documentation pour confirmer que les boîtes aux lettres de ressources sont prises en charge pour la rétention et la suppression d’Exchange pour les étendues statiques et les étendues adaptatives. Pour les étendues statiques, les boîtes aux lettres de ressources sont incluses par défaut dans une stratégie à l’échelle de l’organisation (valeur par défaut All).
- Nouvelle documentation pour les utilisateurs finaux : [Gérer le stockage de courrier avec des boîtes aux lettres d’archivage en ligne](https://support.services.microsoft.com/office/manage-email-storage-with-online-archive-mailboxes-1cae7d17-7813-4fe8-8ca2-9a5494e9a721)

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- [Envoyer des notifications par e-mail et des conseils de stratégie pour les stratégies DLP](use-notifications-and-policy-tips.md) : ajout de nouvelles informations sur ce qui déclenche une notification et qui peut les recevoir.

### <a name="information-barriers"></a>Obstacles aux informations

- [En savoir plus sur les obstacles à l’information](information-barriers.md), [bien démarrer avec les obstacles à l’information](information-barriers-policies.md) - structure refactorisé des rubriques et ajout de clarification pour la prise en charge et les limitations Exchange Online, mis à jour pour inclure la prise en charge de la nouvelle expérience d’interface utilisateur de l’IB.

### <a name="insider-risk-management"></a>Gestion des risques internes

- [Prise en main des paramètres de gestion des risques internes](insider-risk-management-settings.md) : ajout de conseils pour les nouveaux indicateurs Defender pour Cloud App, nouvelle anomalie en tant qu’événement déclencheur dans les seuils personnalisés, nouvelle définition des priorités d’extension de fichier et prise en charge de la stratégie des étiquettes de confidentialité.
- [Cas de gestion des risques internes](insider-risk-management-cases.md) : clarification de l’escalade vers les conseils de cas eDiscovery.

### <a name="microsoft-priva"></a>Microsoft Priva

- [En savoir plus sur la version d’évaluation priva gratuite](/privacy/priva/priva-trial) : lien mis à jour vers les nouvelles conditions générales et conditions générales d’évaluation de Microsoft 365 universelles, ainsi que des mises à jour mineures pour clarifier les rôles et l’éligibilité.
- [Prise en main de Priva](/privacy/priva/priva-setup) - ajout d’une section indiquant les limitations de la disponibilité priva.

### <a name="sensitive-information-types"></a>Types d'informations sensibles

- [Découvrez les types d’informations sensibles basés sur des correspondances de données exactes](sit-learn-about-exact-data-match-based-sits.md) : à partir d’une escalade client, ajoutez les régions dans lesquelles EDM est pris en charge et les procédures permettant de trouver la région de votre locataire.
- [Créer un package de règles SIT EDM](sit-get-started-exact-data-match-create-rule-package.md) - ajout de l’option « Utilisation de types de données spécifiques » dans l’article de schéma.
- [Créer un schéma pour EDM SIT](sit-get-started-exact-data-match-create-schema.md) : suppression de « l’utilisation de types de données spécifiques ».
- [Utilisez des entités nommées dans vos stratégies DLP](named-entities-use.md) : ajout de l’instruction de support pour Microsoft Defender pour Cloud Apps.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Nouvelle option à la fin du processus de création ou de modification de l’étiquette, pour [convertir automatiquement les paramètres d’étiquetage automatique en stratégie d’étiquetage automatique](apply-sensitivity-label-automatically.md#convert-your-label-settings-into-an-auto-labeling-policy).
- Les stratégies d’étiquetage automatique pour SharePoint et OneDrive peuvent désormais appliquer des étiquettes avec chiffrement lorsque le compte qui a modifié le fichier pour la dernière fois n’existe plus dans Azure AD.
- Les étiquettes de conteneur sont prises en charge pour les réseaux de distribution de contenu (CDN) Office 365.
- Clarifications pour [la suppression et la suppression d’étiquettes](create-sensitivity-labels.md#removing-and-deleting-labels).
- Nouveaux [scénarios courants](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels) :
  - Étiqueter des colonnes de base de données SQL à l’aide des mêmes étiquettes de confidentialité que celles utilisées pour les fichiers et les e-mails afin que l’organisation dispose d’une solution d’étiquetage unifiée qui continue de protéger les données structurées lorsqu’elles sont exportées
  - Appliquer une étiquette de confidentialité à un fichier après avoir reçu une alerte indiquant que le contenu contenant des données personnelles est partagé et nécessite une protection

## <a name="april-2022"></a>Avril 2022

### <a name="communication-compliance"></a>Conformité des communications

- [Créer et gérer des stratégies de conformité des communications](communication-compliance-policies.md) - mise à jour avec des conseils ajoutés pour la nouvelle fonctionnalité de stratégie de message signalé par l’utilisateur pour l’intégration de Microsoft Teams.
- [Prise en main de la conformité des communications](communication-compliance-configure.md) - mise à jour pour ajouter des clarifications pour l’abonnement F5 et les licences.

### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Liste des modèles du Gestionnaire](compliance-manager-templates-list.md) de conformité : ajout de 6 nouveaux modèles et liens de navigation sur la page pour accéder plus facilement aux catégories de modèles.
- [Vue d’ensemble du Gestionnaire de conformité](compliance-manager.md) - Vidéo de présentation du produit mise à jour.

### <a name="compliance-offerings--service-assurance"></a>Offres de conformité & assurance du service

- [Offres de conformité](/compliance/regulatory/offering-home) : mises à jour de la couverture du service et des rapports d’audit pour les offres VPATS, SOC, ISO et FedRAMP.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- Avec la [modification du nom du produit](#changes-to-product-names), la **gouvernance des informations** est renommée **Gestion du cycle de vie des données** dans le portail de conformité.
- En cours de déploiement : nouvelle conception pour la configuration des paramètres d’étiquette de rétention.
- Actuellement en cours de déploiement : nouvelle option d’étiquette en préversion, « Déverrouiller cet enregistrement par défaut ». Pour plus d’informations, consultez [Configurer les étiquettes de rétention pour déclarer des enregistrements](declare-records.md#configuring-retention-labels-to-declare-records) et [utiliser le contrôle de version des enregistrements pour mettre à jour les enregistrements stockés dans SharePoint ou OneDrive](record-versioning.md).

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
  - [Vue d’ensemble de l’intégration des appareils macOS à Microsoft 365](device-onboarding-macos-overview.md)
  - [Intégrer et désactiver les appareils macOS dans les solutions de conformité à l’aide d’Intune pour les clients Microsoft Defender pour points de terminaison](device-onboarding-offboarding-macos-intune-mde.md)
  - [Intégrer et déconnecter des appareils macOS dans les solutions Microsoft Purview à l’aide d’Intune](device-onboarding-offboarding-macos-intune.md)
  - [Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide de JAMF Pro pour les clients de Microsoft Defender pour point de terminaison](device-onboarding-offboarding-macos-jamfpro-mde.md)
  - [Intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de JAMF Pro](device-onboarding-offboarding-macos-jamfpro.md)

### <a name="information-barriers"></a>Obstacles aux informations

- [Utiliser les obstacles à l’information avec SharePoint](/sharepoint/information-barriers) : conseils ajoutés pour la prise en charge du nouveau canal privé dans SharePoint.
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

- Scénario nouvellement pris en charge pour les sites SharePoint, désormais en préversion : [Configurer les autorisations de partage de site à l’aide de paramètres avancés PowerShell](sensitivity-labels-teams-groups-sites.md#configure-site-sharing-permissions-by-using-powershell-advanced-settings)
- [La co-création de fichiers chiffrés avec des étiquettes de confidentialité](sensitivity-labels-coauthoring.md) est désormais disponible pour les tests avec le canal Semi-Annual Enterprise Channel (préversion).
- Les comptes OneDrive supprimés sont désormais correctement affichés dans les résultats de simulation pour les stratégies d’étiquetage automatique.
- Problème connu si vous [attribuez des autorisations à des contacts de messagerie dans des groupes](/office365/troubleshoot/sensitivity-labels/mail-contacts-lose-access-encrypted-content) lorsque vous configurez une étiquette de confidentialité pour le chiffrement.

### <a name="changes-to-product-names"></a>Modifications apportées aux noms des produits

Pour relever les défis du milieu de travail décentralisé et riche en données d’aujourd’hui, nous introduisons [Microsoft Purview](https://aka.ms/microsoftpurview), un ensemble complet de solutions qui vous aide à comprendre, régir et protéger l’ensemble de votre patrimoine de données. Cette nouvelle famille de marques combine les fonctionnalités de l’ancienne carte de données Microsoft Purview et du portefeuille de conformité Microsoft 365 sur lequel les clients s’appuient déjà, fournissant une gouvernance unifiée des données et une gestion des risques pour votre organisation.

| **Ancien nom** | **Nouveau nom** | **Description** |
|:----------------|:-------------|:----------------|
| Audit avancé Microsoft 365 <br><br> Audit de base microsoft 365 | Audit de Microsoft Purview (Premium) <br><br> Audit Microsoft Purview (Standard)| Les solutions d’audit fournissent une solution intégrée pour aider les organisations à répondre efficacement aux événements de sécurité, aux enquêtes judiciaires, aux enquêtes internes et aux obligations de conformité. Pour plus d’informations, consultez [Microsoft Purview Advanced Audit (Premium)](advanced-audit.md) et [Microsoft Purview Advanced Audit (Standard).](set-up-basic-audit.md) |
| Conformité des communications Microsoft 365 | Conformité des communications Microsoft Purview | La conformité des communications permet de réduire les risques en vous aidant à détecter, capturer et prendre rapidement des mesures correctives pour les canaux de communication d’entreprise et les violations de stratégie. Pour en savoir plus, consultez [Microsoft Purview Communication Compliance](communication-compliance-solution-overview.md). |
| Gestionnaire de conformité Microsoft | Gestionnaire de conformité Microsoft Purview | Le Gestionnaire de conformité peut vous aider tout au long de votre parcours de conformité, de l’inventaire des risques de protection de vos données à la gestion des complexités de l’implémentation de contrôles, la mise à jour des réglementations et des certifications et la création de rapports aux auditeurs. Pour plus d’informations, consultez [le Gestionnaire de conformité Microsoft Purview](compliance-manager.md). |
| Clé client Microsoft 365 | Clé client Microsoft Purview | La clé client offre une protection supplémentaire contre l’affichage des données par des systèmes ou du personnel non autorisés, et complète le chiffrement de disque BitLocker dans les centres de données Microsoft. Pour plus d’informations, consultez [la clé client Microsoft Purview](customer-key-overview.md). |
| Customer Lockbox dans Office 365 | Microsoft Purview Customer Lockbox | Customer Lockbox garantit que Microsoft ne peut pas accéder à votre contenu pour effectuer des opérations de service sans votre approbation explicite. Customer Lockbox vous permet d’entrer dans le processus de flux de travail d’approbation utilisé par Microsoft pour vous assurer que seules les demandes autorisées autorisent l’accès à votre contenu. Pour plus d’informations, consultez [Microsoft Purview Customer Lockbox](customer-lockbox-requests.md). |
| Protection contre la perte de données | Protection contre la perte de données Microsoft Purview | DLP permet de protéger les données sensibles et de réduire les risques en empêchant les utilisateurs de partager ces données de manière inappropriée avec des personnes qui ne devraient pas les avoir. Pour plus d’informations, consultez [Microsoft Purview Data Loss Prevention](dlp-learn-about-dlp.md). |
| Chiffrement à double clé pour Microsoft 365 | Chiffrement à double clé Microsoft Purview | Double Key Encryption (DKE) utilise deux clés ensemble pour accéder au contenu protégé. Microsoft stocke une clé dans Microsoft Azure, et vous conservez l’autre clé. Pour en savoir plus, consultez [Le chiffrement à double clé Microsoft Purview](double-key-encryption.md) |
| Obstacles à l’information Microsoft 365 | Cloisonnement de l’information Microsoft Purview | Les obstacles à l’information sont une solution qui limite la communication et la collaboration entre certaines personnes au sein de votre organisation afin de protéger les informations internes. Pour en savoir plus, consultez [Microsoft Purview Information Barriers](information-barriers-solution-overview.md). |
| Microsoft Information Protection | Protection de l'information Microsoft Purview | La protection des informations vous aide à découvrir, classifier et protéger des informations sensibles où qu’elles résident ou voyagent. Pour plus d’informations, consultez [Microsoft Purview Information Protection](information-protection.md). |
| Gouvernance des informations Microsoft | Gestion du cycle de vie des données Microsoft Purview | La gestion du cycle de vie des données vous fournit des outils et des fonctionnalités pour conserver le contenu dont vous avez besoin pour conserver et supprimer le contenu que vous n’avez pas. Pour plus d’informations, consultez [Gestion du cycle de vie des données Microsoft Purview](data-lifecycle-management.md). |
| Microsoft 365 : gestion des risques internes | Microsoft Purview : gestion des risques internes | La gestion des risques internes utilise l’ensemble des indicateurs de service et tiers pour vous aider à identifier, trier et agir rapidement sur l’activité des utilisateurs à risque. Pour en savoir plus, consultez [Microsoft Purview Insider Risk Management](insider-risk-management.md). |
| Chiffrement de messages Office 365 | Chiffrement des messages Microsoft Purview | Avec Le chiffrement des messages, votre organisation peut envoyer et recevoir des messages électroniques chiffrés entre des personnes internes et externes à votre organisation. Pour plus d’informations, consultez [Chiffrement des messages Microsoft Purview](ome.md). |
| Privileged Access Management dans Microsoft 365 | Privileged Access Management Microsoft Purview | Privileged Access Management permet de protéger votre organisation contre les violations et de respecter les meilleures pratiques de conformité en limitant l’accès permanent aux données sensibles ou l’accès aux paramètres de configuration critiques. Pour plus d’informations, consultez [Microsoft Purview Privileged Access Management](privileged-access-management-solution-overview.md). |
| Connecteurs de données Microsoft | Connecteurs de données Microsoft Purview | Microsoft 365 permet aux administrateurs d’utiliser des connecteurs de données pour importer et archiver des données non-Microsoft tierces à partir de plateformes de médias sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration de documents dans des boîtes aux lettres de votre organisation Microsoft 365. Pour plus d’informations, consultez [les connecteurs de données Microsoft Purview](compliance-extensibility.md). |
| Microsoft 365 advanced eDiscovery <br><br> Microsoft 365 Core eDiscovery | Microsoft Purview eDiscovery (Premium) <br><br> Microsoft Purview eDiscovery (Standard) | La découverte électronique, ou eDiscovery, est le processus d'identification et de livraison d'informations électroniques qui peuvent être utilisées comme preuves dans des affaires juridiques. Pour plus d’informations, consultez [Microsoft Purview eDiscovery (Premium)](overview-ediscovery-20.md) et [Microsoft Purview eDiscovery (Standard).](get-started-core-ediscovery.md) |
| Centre de conformité Microsoft 365 | Portail de conformité Microsoft Purview | Portail d’administration pour accéder aux solutions et au catalogue de solutions dans la suite conformité Microsoft 365 E5. Pour en savoir plus, consultez le [portail de conformité Microsoft Purview](microsoft-365-compliance-center.md). |

## <a name="march-2022"></a>Mars 2022

### <a name="communication-compliance"></a>Conformité des communications

- [Examiner et corriger les alertes de conformité des communications : instructions supprimées](communication-compliance-investigate-remediate.md) pour la vue d’annotation déconseillée.

### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Utilisation des actions d’amélioration](compliance-manager-improvement-actions.md), [Prise en main du Gestionnaire de conformité](compliance-manager-setup.md) : ajout d’informations sur d’autres actions d’amélioration qui peuvent être automatiquement surveillées et testées (« évaluation continue de la conformité ») ; cela inclut de nouvelles capacités pour parenter l’état de test d’une action à celui d’une autre action.

### <a name="data-classification"></a>Classification des données

- [Prise en main de l’Explorateur de contenu](data-classification-content-explorer.md) - Conseils Teams ajoutés, section de licences pointant vers les descriptions de service.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- [Les stratégies de rétention pour Yammer](create-retention-policies.md#retention-policy-for-yammer-locations) sont désormais en disponibilité générale (GA).
- Prise en charge des canaux partagés, actuellement en préversion. Lorsque vous configurez une stratégie de rétention pour l’emplacement du message de canal Teams, tous les canaux partagés héritent des paramètres de rétention de leur équipe parente.
- [Limites par locataire pour la disposition du contenu](retention-limits.md#maximum-number-of-items-for-disposition).

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- [Protection contre la perte de données et Microsoft Teams](dlp-microsoft-teams.md) - Préversion publique du contenu Share Teams Channels.
- [Bien démarrer avec l’extension de conformité Microsoft](dlp-chrome-get-started.md) - préversion publique des groupes d’applications restreints, supprimer les instructions de clé de Registre, configuration désormais activée par défaut.
- [Configurez les paramètres de protection contre la perte de données](dlp-configure-endpoint-settings.md) de point de terminaison : nouveau pour la préversion publique des groupes d’applications restreints.
- [Informations de référence sur la stratégie de protection contre la perte de données](dlp-policy-reference.md) : mises à jour pour la préversion publique des groupes d’applications restreints.
- [Prise en main de la protection contre la perte de données pour Power BI](dlp-powerbi-get-started.md) : nouveauté de la préversion publique.
- 
### <a name="information-protection"></a>Protection des informations

- [Prise en charge des notes de publication du jeu de caractères sur deux octets](mip-dbcs-relnotes.md) - ajout de conseils pour macOS.
- 
### <a name="insider-risk-management"></a>Gestion des risques internes

- [Prise en main de la gestion des risques internes](insider-risk-management-configure.md) : ajout de nouvelles tâches pour les conseils sur les actions recommandées.
- [Bien démarrer avec les paramètres de gestion des risques internes](insider-risk-management-settings.md) : nouvelles mises à jour pour les fonctionnalités de notification et d’alertes par e-mail, nouvelles mises à jour pour les notifications analytiques.

### <a name="microsoft-priva"></a>Microsoft Priva

- [Configurer les paramètres Priva](/privacy/priva/priva-settings) : mise à jour des informations de clarification sur les périodes de rétention des données pour les demandes de droits des personnes concernées ; ajout de détails sur la gestion et l’application de balises de révision des données pour les demandes de droits d’objet.
- [Créer une demande de droits d’objet](/privacy/priva/subject-rights-requests-create) : ajout de détails sur l’affinement des recherches et le choix des conditions et des attributs ; ajout d’informations sur les nouvelles fonctionnalités qui permettent aux utilisateurs de sélectionner toutes les versions des éléments SharePoint dans leur recherche (par rapport au paramètre par défaut, qui retourne uniquement la version actuelle des éléments SharePoint).
- [Passer en revue les données d’une demande de droits d’objet](/privacy/priva/subject-rights-requests-data-review) : ajout de détails à l’étape 3 pour l’examen des éléments au cours de l’étape de révision des données, y compris le marquage des fichiers en tant qu’inclusion/exclusion, l’annotation des fichiers pour appliquer des actions, l’application de balises et la saisie de notes.
- [Générer des rapports et répondre à une demande de droits d’objet](/privacy/priva/subject-rights-requests-reports) : ajout de détails sur la façon de comprendre les rapports ; clarifié quand un package d’exportation est généré et comment utiliser son contenu ; ajout d’informations sur les journaux d’audit, les rapports de fichiers étiquetés et les périodes de rétention pour les données et les rapports SRR.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- [Étiquettes de confidentialité pour Teams](sensitivity-labels-teams-groups-sites.md) :
  - Prise en charge des canaux partagés, actuellement en préversion. Si une équipe a des canaux partagés, elle hérite automatiquement des paramètres d’étiquette de confidentialité de son équipe parente, et cette étiquette ne peut pas être supprimée ou remplacée par une autre étiquette.
  - Prise en charge des modèles, précédemment répertoriés comme [non pris en charge avec les API Graph Teams et les applets de commande PowerShell]( /microsoftteams/sensitivity-labels#limitations).  
- Pour l’audit de Word, Excel et PowerPoint sur le web, le texte de justification est maintenant entièrement déployé.
- L’application d’une étiquette par défaut aux documents existants pour Word, Excel et PowerPoint sur le web est maintenant entièrement déployée.

## <a name="february-2022"></a>Février 2022

### <a name="ediscovery"></a>eDiscovery

- [Gérer les modèles de communication des consignatateurs dans eDiscovery (Premium)](advanced-ediscovery-communications-library.md) : les gestionnaires eDiscovery peuvent désormais créer des modèles de communication de consignation qui peuvent être utilisés dans n’importe quel cas eDiscovery (Premium) dans l’organisation.
- [Gérer les agents émetteurs dans eDiscovery (Premium)](advanced-ediscovery-issuing-officers.md) : les gestionnaires eDiscovery peuvent ajouter une liste d’agents émetteurs qui peuvent être affectés aux communications des consignatateurs dans n’importe quel cas eDiscovery (Premium) dans l’organisation.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- [Les étendues adaptatives pour les](retention.md#adaptive-or-static-policy-scopes-for-retention) stratégies de rétention et les stratégies d’étiquette de rétention sont désormais en disponibilité générale (GA). Les instructions de [configuration d’une étendue adaptative](retention-settings.md#to-configure-an-adaptive-scope) incluent désormais plus d’informations sur les étendues de site SharePoint : Blog post reference for using custom site properties and how to use the site property SiteTemplate to include or exclude specific site types with the advanced query builder.
- [La recherche de stratégie](retention.md#policy-lookup) dans la solution de gestion du cycle de vie des données est désormais généralement disponible (disponibilité générale).
- PowerShell alternative au paramètre de gestion des enregistrements qui permet aux utilisateurs de supprimer des éléments étiquetés dans SharePoint et OneDrive à l’aide de AllowFilesWithKeepLabelToBeDeletedSPO et AllowFilesWithKeepLabelToBeDeletedODB à partir de [Get-PnPTenant](https://pnp.github.io/powershell/cmdlets/Get-PnPTenant.html) et [Set-PnPTenant](https://pnp.github.io/powershell/cmdlets/Set-PnPTenant.html).

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Nouvelles instructions [Pourquoi choisir l’étiquetage intégré sur le complément AIP pour les applications Office](sensitivity-labels-aip.md) si vous utilisez le client d’étiquetage unifié Azure Information Protection (AIP) pour les ordinateurs Windows. Cette page contient des informations sur la nouvelle préversion privée pour les applications Office.
- Nouveaux paramètres pour les stratégies [d’étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) :
  - Paramètres supplémentaires pour l’e-mail afin de prendre en charge l’application systématique d’une étiquette de confidentialité correspondante et d’appliquer le chiffrement aux e-mails reçus de l’extérieur de l’organisation.
  - Les exclusions pour des instances spécifiques (utilisateurs, groupes, sites) sont prises en charge à l’aide de la nouvelle option **Exclus** lorsque la sélection par défaut de **Tout** est spécifiée pour **Inclus**.
- Maintenant en préversion : les appareils mobiles (iOS et Android) prennent en charge [la co-édition](sensitivity-labels-coauthoring.md) lorsque vous avez des versions minimales et que vous optez pour cette préversion.
- La prise en charge de la définition du type de lien de partage par défaut est étendue aux documents individuels dans SharePoint et OneDrive. Pour plus d’informations, consultez le nouvel article [Utiliser des étiquettes de confidentialité pour configurer le type de lien de partage par défaut pour les sites et les documents dans SharePoint et OneDrive]( sensitivity-labels-default-sharing-link.md).
- Le Centre d’administration Teams prend désormais en charge les étiquettes de conteneur (étiquettes de confidentialité avec l’étendue des groupes & sites).

## <a name="january-2022"></a>Janvier 2022

### <a name="microsoft-purview-data-lifecycle-management"></a>Gestion du cycle de vie des données Microsoft Purview

- La documentation relative à ce qui était auparavant Microsoft Information Governance a été considérablement révisée et restructurée pour vous aider à trouver plus facilement des informations relatives aux solutions que vous configurez dans le portail de conformité Microsoft Purview : Connecteurs de données, Gestion du cycle de vie des données et Gestion des enregistrements. Dans le cadre de cette révision, la documentation fournit une distinction plus claire entre les scénarios de rétention pour la gestion du cycle de vie des données et la gestion des enregistrements.
- [Apprenez-en davantage sur la gestion du cycle de vie des données](data-lifecycle-management.md) , nouveauté pour prendre en charge la restructuration.
- [Prise en main de la gestion du cycle de vie des données](get-started-with-data-lifecycle-management.md) : nouvelle, pour remplacer « Prise en main de la rétention », cet article inclut les étapes de prise en main de toutes les fonctionnalités de gestion du cycle de vie des données, notamment la rétention.
- [Créez des étiquettes de rétention pour les exceptions à vos stratégies de rétention](create-retention-labels-data-lifecycle-management.md) . Nouveau scénario identifié pour l’utilisation d’étiquettes de rétention pour la gestion du cycle de vie des données plutôt que pour la gestion des enregistrements.
- [En savoir plus sur les boîtes aux lettres d’archivage](archive-mailboxes.md) - nouvelles, pour prendre en charge la restructuration, contient des informations conceptuelles qui se trouvaient précédemment dans l’article « Activer les boîtes aux lettres d’archivage ».

### <a name="microsoft-priva"></a>Microsoft Priva

- [La gestion de la confidentialité est désormais Microsoft Priva](/privacy/priva/priva-overview) - mise à jour pour renommer le produit et ses solutions, Priva Privacy Risk Management et Priva Subject Rights Requests.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Prise en charge des nouveaux [groupes de rôles et rôles](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels), désormais en préversion.
- Nouvelles [fonctionnalités de surveillance pour les](apply-sensitivity-label-automatically.md#monitoring-your-auto-labeling-policy) stratégies d’étiquetage automatique.
- Déploiement maintenant : étiquette par défaut pour les documents existants et texte de justification pour Office sur le web.
- Annoncé pour juillet Semi-Annual Enterprise Channel avec la version 2202+: Co-création et audit pour Outlook.

## <a name="december-2021"></a>Décembre 2021

### <a name="compliance-and-service-assurance"></a>Conformité et assurance du service

- [Notification de violation Azure, Dynamics 365 et Windows dans le cadre du RGPD](/compliance/regulatory/gdpr-breach-notification) : mise à jour pour préciser que les clients n’ont pas besoin d’utiliser un service payant tel que Defender pour le cloud pour recevoir des notifications de sécurité et de confidentialité

### <a name="ediscovery"></a>eDiscovery

- [Flux de travail eDiscovery (Premium) pour le contenu dans Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#reference-guide) - mis à jour avec un nouveau guide de référence rapide téléchargeable pour la gestion du contenu Teams dans eDiscovery (Premium)

### <a name="data-lifecycle-management"></a>Gestion du cycle de vie des données

- [Activer les boîtes aux lettres d’archivage dans le centre de conformité](enable-archive-mailboxes.md#run-diagnostics-on-archive-mailboxes) - Ajout d’une section sur le nouvel outil de diagnostic pour les boîtes aux lettres d’archivage
- [Utiliser le chargement réseau pour importer les fichiers PST de votre organisation dans Microsoft 365](use-network-upload-to-import-pst-files.md#step-2-upload-your-pst-files-to-microsoft-365) - L’importation PST prend désormais en charge AzCopy v10
- [Restaurer une boîte aux lettres inactive](restore-an-inactive-mailbox.md) - procédure révisée pour restaurer une boîte aux lettres inactive en ajoutant d’abord LegacyExchangeDN de boîte aux lettres inactive à la boîte aux lettres cible

### <a name="information-protection"></a>Protection des informations

- [Déployer une solution de protection des informations avec Microsoft Purview](information-protection-solution.md) - Nouveau guide pas à pas pour les clients qui recherchent une feuille de route normative pour déployer Microsoft Purview Information Protection

### <a name="retention-and-records-management"></a>Conservation et gestion des enregistrements

- Nouvelles instructions sur le [temps nécessaire à l’application des stratégies de rétention](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- Déploiement des nouveaux paramètres de locataire : paramètre de gestion des enregistrements qui empêche la modification des propriétés pour les éléments SharePoint étiquetés marqués comme un enregistrement et verrouillés, et autre paramètre pour empêcher les utilisateurs de déverrouiller les éléments marqués comme enregistrement

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- L’étiquetage obligatoire et une étiquette par défaut pour Power BI sont désormais en disponibilité générale (GA)
