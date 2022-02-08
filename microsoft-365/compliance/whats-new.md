---
title: Nouveautés dans la conformité Microsoft 365
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
description: Que vous ajoutiez de nouvelles solutions au centre de conformité, mettiez à jour les fonctionnalités existantes en fonction de vos commentaires ou mettiez en place une documentation actualisée et mise à jour, Microsoft 365 vous permet de rester au-dessus du paysage de conformité en constante évolution. Découvrez ce que nous avons fait ce mois-ci.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: bfbae00812400b211abdda9d7310179cc65e2c15
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2022
ms.locfileid: "62444664"
---
# <a name="whats-new-in-microsoft-365-compliance"></a>Nouveautés dans la conformité Microsoft 365

Que vous ajoutiez de nouvelles solutions au [Centre de conformité Microsoft 365](microsoft-365-compliance-center.md), mettiez à jour les fonctionnalités existantes en fonction de vos commentaires ou mettiez en place une documentation actualisée et mise à jour, Microsoft 365 vous permet de rester informé du paysage de conformité en constante évolution. Consultez la ci-dessous pour voir les nouveautés de la conformité Microsoft 365 jour.

> [!NOTE]
> Certaines fonctionnalités de conformité sont déployées à différentes vitesses pour nos clients. Si vous ne voyez pas encore de fonctionnalité, essayez de vous ajouter à [la version ciblée](/office365/admin/manage/release-options-in-office-365).

> [!TIP]
> Vous êtes intéressé par ce qui se passe dans d’autres centres d’administration ? Consultez les articles suivants :
>
> - [Nouveautés du Centre d'administration Microsoft 365](/office365/admin/whats-new-in-preview)
> - [Nouveautés du Centre d’administration SharePoint de gestion](/sharepoint/what-s-new-in-admin-center)
> - [Nouveautés de Microsoft 365 Defender](../security/defender/whats-new.md)
>
> Visitez également la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour en savoir plus sur les fonctionnalités Microsoft 365 qui ont été lancées, sont en cours de déploiement, sont en cours de développement, ont été annulées ou publiées précédemment.

## <a name="january-2022"></a>Janvier 2022

### <a name="microsoft-information-governance"></a>Gouvernance des informations Microsoft

- La page gouvernance des informations [Microsoft en Microsoft 365](manage-information-governance.md) et la section de la documentation sont considérablement révisées et restructurées pour vous aider à trouver plus facilement des informations relatives aux solutions que vous configurez dans le Centre de conformité Microsoft 365 : connecteurs de données, gouvernance des informations et gestion des enregistrements. Dans le cadre de cette révision, la documentation fournit une distinction plus claire entre les scénarios de rétention pour la gouvernance des informations et la gestion des enregistrements.
- [En savoir plus sur la gouvernance des informations](information-governance.md) - nouveauté, pour prendre en charge la réorganisation.
- [Prendre en main la](get-started-with-information-governance.md) gouvernance des informations - nouveauté, pour remplacer « Commencer avec la rétention », cet article inclut les étapes de mise en place de toutes les fonctionnalités de gouvernance des informations, y compris la rétention.
- [Créez des étiquettes de rétention pour les exceptions à vos stratégies](create-retention-labels-information-governance.md) de rétention : nouveau scénario identifié pour l’utilisation d’étiquettes de rétention pour la gouvernance des informations plutôt que pour la gestion des enregistrements.
- [En savoir plus sur les boîtes aux lettres d’archivage](archive-mailboxes.md) : nouveauté, pour prendre en charge la réorganisation, contient des informations conceptuelles qui se trouvait auparavant dans activer les boîtes aux lettres d’archivage.

### <a name="microsoft-priva"></a>Microsoft Priva

- [La gestion de la confidentialité est désormais Microsoft Priva](/privacy/priva/priva-overview) : mise à jour pour renommer le produit et ses solutions, priva Privacy Risk Management et Priva Subject Rights Requests.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Prise en charge des nouveaux rôles et [groupes de rôles MIP](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels), désormais en prévisualisation.
- Nouvelles [fonctionnalités d’analyse](apply-sensitivity-label-automatically.md#monitoring-your-auto-labeling-policy) pour les stratégies d’étiquetage automatique.
- Désormais en cours de déploiement : étiquette par défaut pour les documents existants dans le canal actuel (prévisualisation) et texte de justification pour Office sur le Web.
- Annoncé pour le Canal Semi-Annual Enterprise juillet avec la version 2202+ : co-édition et audit pour Outlook.

## <a name="december-2021"></a>Décembre 2021

### <a name="compliance-and-service-assurance"></a>Conformité et assurance de service

- Notification de violation [Azure, Dynamics 365 et Windows](/compliance/regulatory/gdpr-breach-notification) dans le cadre du R GDPR : mise à jour pour clarifier que les clients n’ont pas besoin d’utiliser un service de salaire tel que Defender for Cloud pour recevoir des notifications de sécurité et de confidentialité

### <a name="ediscovery"></a>eDiscovery

- Advanced eDiscovery flux de travail pour le [contenu dans Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#reference-guide) - mis à jour avec un nouveau guide de référence rapide téléchargeable pour la gestion Teams contenu dans Advanced eDiscovery

### <a name="information-governance"></a>Gouvernance des informations

- [Activer les boîtes aux lettres d’archivage dans le](enable-archive-mailboxes.md#run-diagnostics-on-archive-mailboxes) centre de conformité : ajout d’une section sur le nouvel outil de diagnostic pour les boîtes aux lettres d’archivage
- [Utiliser le chargement réseau pour importer les fichiers PST](use-network-upload-to-import-pst-files.md#step-2-upload-your-pst-files-to-microsoft-365) de votre organisation dans Microsoft 365 : l’importation PST prend désormais en charge AzCopy v10
- [Restaurer une boîte aux lettres inactive](restore-an-inactive-mailbox.md) : procédure révisée pour restaurer une boîte aux lettres inactive en ajoutant d’abord LegacyExchangeDN de la boîte aux lettres inactive à la boîte aux lettres cible

### <a name="information-protection"></a>Protection des informations

- [Déployer une solution MIP](information-protection-solution.md) : nouvelles instructions pas à pas pour les clients qui recherchent une feuille de route normative pour déployer Protection des données Microsoft (MIP)

### <a name="retention-and-records-management"></a>Gestion des enregistrements et de la rétention

- Nouvelles recommandations sur [la durée d’application des stratégies de rétention](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- Nouveaux paramètres de client en cours de déploiement : paramètre de gestion des enregistrements qui empêche la modification des propriétés des éléments SharePoint étiquetés marqués comme étant un enregistrement et verrouillés, et d’autres paramètres pour empêcher les utilisateurs de déverrouiller les éléments marqués comme enregistrements

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- L’étiquetage obligatoire et une étiquette par défaut pour Power BI sont désormais généralement disponibles (GA)

## <a name="november-2021"></a>Novembre 2021

### <a name="compliance-manager"></a>Gestionnaire de conformité

Les nouvelles mises à jour de contenu peuvent être vues dans les [nouveautés du Gestionnaire](compliance-manager-whats-new.md) de conformité Microsoft.

### <a name="device-onboarding"></a>Intégration d’appareil

Les articles suivants ont été ajoutés pour l’intégration d’appareil :

- [Intégration des appareils macOS dans la vue d'ensemble de Microsoft 365 (aperçu)](device-onboarding-macos-overview.md)
- [intégrer et déclasser des appareils macOS dans des solutions de conformité Microsoft 365 à l’aide d’Intune (préversion)](device-onboarding-offboarding-macos-intune.md)
- [Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide d'Intune pour les clients de Microsoft Defender pour point de terminaison (aperçu)](device-onboarding-offboarding-macos-intune-mde.md)
- [intégrer et déclasser des appareils macOS dans des solutions de conformité Microsoft 365 à l’aide de JAMF Pro (préversion)](device-onboarding-offboarding-macos-jamfpro.md)
- [Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide de JAMF Pro pour les clients de Microsoft Defender pour point de terminaison (aperçu)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>eDiscovery

- [Utilisez le nouveau format de cas dans Advanced eDiscovery](advanced-ediscovery-new-case-format.md) nouveau format de cas a été publié à la disponibilité générale et renommé à partir du « grand format de cas »

### <a name="retention-and-records-management"></a>Gestion des enregistrements et de la rétention
- Déploiement : nouveaux paramètres de gestion des enregistrement qui contrôlent si les éléments étiquetés dans SharePoint et OneDrive peuvent être supprimés par les utilisateurs. Auparavant, les étiquettes de rétention configurées pour conserver le contenu et qui ne marquent pas les éléments comme enregistrements empêchaient les utilisateurs de supprimer le contenu étiqueté dans SharePoint lorsque cette action était autorisée dans OneDrive. Pour plus d’informations, voir [Comment fonctionne la rétention SharePoint et OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

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
- Le nom [d’étendue des étiquettes Azure Purview](/azure/purview/create-sensitivity-label) est désormais « Ressources de données schématisées ».

## <a name="october-2021"></a>Octobre 2021

### <a name="app-governance"></a>Gouvernance des applications

- [Le module de gouvernance des applications pour Defender pour les applications cloud a été publié à la disponibilité générale](/cloud-app-security/app-governance-manage-app-governance). La documentation sur la gouvernance des applications a été déplacée pour rejoindre la documentation de Defender for Cloud Apps.

### <a name="compliance--service-assurance"></a>Certification du service & conformité

- [Assurance de service](/compliance) : examiner trimestriellement les mises à jour de contenu pour les certifications et les déclarations d’applicabilité) Gestion des ressources du centre de données
  - Architecture et infrastructure des centres de données
  - Continuité d’activité du centre de données et récupération d’urgence
  - Protections environnementales du centre de données
  - Sécurité de l’accès physique au centre de données
  - Microsoft 365 de conformité SDL
  - Contrôle d’accès de l’ingénieur de service Microsoft 365
  - Guide d’évaluation des risques pour MS Cloud

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- [En savoir plus sur la protection contre la perte de](endpoint-dlp-learn-about.md) données a été mise à jour pour la prise en charge de macOS et la classification avancée ; mise à jour pour la création d’une stratégie DLP personnalisée pour auditer l’activité pour tous les types de fichiers pris en charge.
- [Prise en Microsoft 365 protection contre](endpoint-dlp-getting-started.md) la perte de données de point de terminaison a été mise à jour pour la prise en charge de macOS et la classification avancée.
- [L’utilisation de la protection contre la perte de](endpoint-dlp-using.md) données de point de terminaison a été mise à jour pour la prise en charge de macOS et la classification avancée.
- [La référence des conseils de stratégie de](dlp-policy-tips-reference.md) protection contre la perte de données a été mise à jour pour la prise en charge de macOS et la classification avancée.
- [L’intégration d’appareils macOS Microsoft 365 (prévisualisation)](device-onboarding-macos-overview.md) a été mise à jour pour la prise en charge de macOS et la classification avancée.
- Ajout des nouvelles pages suivantes pour l’intégration d’appareils :
  - [intégrer et déclasser des appareils macOS dans des solutions de conformité Microsoft 365 à l’aide d’Intune (préversion)](device-onboarding-offboarding-macos-intune.md)
  - [Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide d'Intune pour les clients de Microsoft Defender pour point de terminaison (aperçu)](device-onboarding-offboarding-macos-intune-mde.md)
  - [intégrer et déclasser des appareils macOS dans des solutions de conformité Microsoft 365 à l’aide de JAMF Pro (préversion)](device-onboarding-offboarding-macos-jamfpro.md)
  - [Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide de JAMF Pro pour les clients de Microsoft Defender pour point de terminaison (aperçu)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>eDiscovery

- Collecter des pièces [jointes](advanced-ediscovery-cloud-attachments.md) dans le cloud dans Advanced eDiscovery en plus de collecter la dernière version d’une pièce jointe cloud, vous pouvez collecter la version qui a été partagée dans un message électronique ou une conversation Teams ; la collecte de la version partagée est rendue possible par la nouvelle fonctionnalité d’application automatique d’une étiquette de rétention aux pièces jointes cloud.
- Configurer les versions historiques dans [Advanced eDiscovery](advanced-ediscovery-historical-versions.md) nouvelle fonctionnalité qui indexe toutes les versions des documents stockés sur un site SharePoint pour la recherche ; cela signifie que les versions de document qui contiennent du contenu qui correspondent à une requête de collection sont renvoyées dans les résultats de la recherche.

### <a name="encryption"></a>Chiffrement

- [Utiliser le chiffrement de bout](/microsoftteams/teams-end-to-end-encryption) en bout pour les appels Microsoft Teams (prévisualisation publique) Nouveau contenu pour la prévisualisation publique.

### <a name="information-governance"></a>Gouvernance des informations

- Configurer un connecteur pour importer [des données d’audit EHR par Le](import-epic-data.md) nouveau connecteur vous permet d’importer des données à partir du système électronique d’enregistrements de santé électronique DeCén afin de prendre en charge de nouveaux scénarios généraux d’utilisation abusive des données des patients pour la gestion des risques internes.
- Configurer un connecteur pour importer des données [d’audit EHR](import-healthcare-data.md) de santé. Ce nouveau connecteur vous permet d’importer des données à partir d’un système électronique d’enregistrements de santé pour prendre en charge de nouveaux scénarios généraux d’utilisation abusive des données des patients pour la gestion des risques internes.

### <a name="retention-and-records-management"></a>Gestion des enregistrements et de la rétention
- [Les étendues de stratégie adaptative sont publiées](retention.md#adaptive-or-static-policy-scopes-for-retention) en prévisualisation pour les stratégies de rétention et les stratégies d’étiquette de rétention.
- Vous pouvez désormais [appliquer automatiquement une étiquette de rétention basée sur une étiquette de niveau de sensibilité](apply-retention-labels-automatically.md#identify-files-and-emails-that-have-a-sensitivity-label).
- Le plan de fichiers a un nouveau [processus d’importation](file-plan-manager.md#import-retention-labels-into-your-file-plan).
- [Paramètres communs pour les stratégies](retention-settings.md) de rétention et les stratégies d’étiquette de rétention : nouvel article pour obtenir des informations détaillées sur la configuration des étendues adaptatives et d’autres paramètres dans les stratégies de rétention et les stratégies d’étiquette de rétention.

### <a name="sensitive-information-types"></a>Types d'informations sensibles

- [Découvrez le nouveau contenu des entités nommées (prévisualisation)](named-entities-learn.md) pour les entités nommées.
- [Utilisez des entités nommées dans vos stratégies de](named-entities-use.md) protection contre la perte de données (prévisualisation) nouveau contenu sur l’utilisation d’entités nommées.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- [Les étiquettes par défaut et les stratégies par](mip-easy-trials.md) défaut sont en place pour les clients éligibles.

## <a name="september-2021"></a>Septembre 2021

### <a name="app-governance"></a>Gouvernance des applications

- [Les informations de mise en place simplifiée de](app-governance-get-started.md) la gouvernance des applications ont un flux de travail modifié et ajouté de nouveaux liens vers l’inscription à la prévisualisation publique
- [Nouvelle définition des alertes de détection](app-governance-anomaly-detection-alerts.md#app-made-high-volume-of-importance-mail-read-and-created-inbox-rule) ajoutée (mise à jour ; ajout d’une nouvelle définition pour les alertes de collecte)

### <a name="auditing"></a>Audit

- [Activer ou désactiver l’audit](turn-audit-log-search-on-or-off.md) ajout d’une nouvelle section sur la façon dont les modifications apportées à l’état d’audit dans une organisation sont elles-mêmes auditées ; Cela signifie que les enregistrements d’audit sont enregistrés lorsque l’audit est allumé ou désactivé ; vous pouvez rechercher ces enregistrements d’audit dans Exchange journal d’audit de l’administrateur

### <a name="communication-compliance"></a>Conformité des communications

- [Conseils sur la conformité des communications avec les solutions SIEM](communication-compliance-siem.md) pour l’intégration de la conformité des communications avec les solutions SIEM)

### <a name="compliance-offerings"></a>Offres pour la conformité

- [MTCS (Multi-Tier Cloud Security)](/compliance/regulatory/offering-mtcs-singapore) Mises à jour standard pour Singapour pour la couverture Dynamics 365
- [Secteur des cartes de paiement (PCI)](/compliance/regulatory/offering-pci-dss) Mises à jour DSS (Data Security Standard) pour la couverture SharePoint Online
- [Guide des nouveaux logiciels clients de la section 508 pour](/compliance/regulatory/offering-section-508-vpats) les États-Unis
- [Recommandations en matière d’accessibilité du contenu Web](/compliance/regulatory/offering-wcag-2-1) : nouvelles instructions sur les logiciels clients

### <a name="compliance--service-assurance"></a>Certification du service & conformité

- [Révision trimestrielle de l’assurance](/compliance/) de service des mises à jour de contenu pour les certifications et les déclarations d’applicabilité
  - Destruction d’appareils porteurs de données
  - Attaques DDOS

### <a name="data-connectors"></a>Connecteurs de données

- [Archivage de données](archiving-third-party-data.md#data-connectors-in-the-us-government-cloud) tierces dans Microsoft 365 connecteurs de données à partir de CellTrust et 17a-4 LLC désormais disponible dans les Cloud de la communauté du secteur public organisations dans le cloud pour le gouvernement des États-Unis
- [La mise en place d’un connecteur pour archiver les données YouTube](archive-youtube-data.md) fournit de nouvelles instructions pour cette fonctionnalité en prévisualisation publique.

### <a name="ediscovery"></a>eDiscovery

- Utilisez l’éditeur [KQL](ediscovery-kql-editor.md) pour générer la prévisualisation publique des requêtes de recherche d’une nouvelle façon de créer des requêtes de recherche dans la recherche de contenu, la découverte électronique principale et les Advanced eDiscovery ; l’éditeur KQL fournit la saisie automatique pour les propriétés et conditions utilisables dans une recherche prise en charge et affiche des listes de valeurs pris en charge pour les propriétés et conditions standard ; l’éditeur KQL fournit également la détection d’erreurs et des suggestions pour corriger les erreurs potentielles dans les requêtes de recherche.

### <a name="information-barriers"></a>Obstacles aux informations

- [Mise en place de la nouvelle fonctionnalité de prévisualisation des obstacles](information-barriers-policies.md#step-6-information-barriers-modes) à l’information
- [Obstacles à l’information Microsoft Teams](/microsoftteams/information-barriers-in-teams) nouvelle fonctionnalité de prévisualisation pour les modes d’obstacles à l’information
- [Obstacles à l’information OneDrive](/onedrive/information-barriers) nouvelle fonctionnalité de prévisualisation pour les modes d’obstacles à l’information
- [Obstacles à l’information SharePoint online nouvelle](/sharepoint/information-barriers) fonctionnalité de prévisualisation pour les modes d’obstacles à l’information

### <a name="insider-risk-management"></a>Gestion des risques internes

- [Prise en charge de la nouvelle fonctionnalité de prévisualisation de la gestion](insider-risk-management-configure.md#recommended-actions-preview) des risques internes pour la prise en charge des actions recommandées
- [Examiner les activités de risques internes nouvelle](insider-risk-management-activities.md#get-help-managing-your-insider-risk-alert-queue) section « Obtenir de l’aide pour gérer votre file d’attente d’alertes de risque interne »
- [Prise en charge des paramètres de gestion des risques internes](insider-risk-management-settings.md#admin-notifications) nouvelle fonctionnalité de prévisualisation des paramètres de notifications d’administrateur

### <a name="retention-and-records-management"></a>Gestion des enregistrements et de la rétention
- [La révision de disposition à plusieurs étapes](disposition.md) est désormais généralement disponible (GA), avec de nouveaux [événements d’audit](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities). La révision de disposition à plusieurs étapes vous permet de spécifier jusqu’à cinq étapes consécutives de révision de la disposition d’une étiquette de rétention, et les réviseurs peuvent ajouter d’autres utilisateurs à la phase de révision de leur disposition. Vous pouvez également personnaliser les rappels et les notifications par e-mail.
- Les canaux privés [pour Teams stratégies de](create-retention-policies.md#retention-policy-for-teams-locations) rétention sont désormais généralement disponibles.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité
- La [co-édition et l’auto-ave](sensitivity-labels-coauthoring.md) sont désormais généralement disponibles pour Windows (version minimale de 2107 à partir du canal actuel ou du canal Enterprise mensuel) et macOS (version minimale de 16,51).
- Déploiement pour les Office qui utilisent des étiquettes intégrées : le paramètre d’étiquette par défaut prend désormais en charge les documents existants ainsi que les nouveaux documents. Ce changement de comportement assure la parité avec le client d’étiquetage unifié Azure Information Protection. Pour plus d’informations sur le déploiement par application et les versions minimales, consultez le [tableau des fonctionnalités](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) pour Word, Excel et PowerPoint.
- Les étiquettes de conteneur prisent désormais [en charge les paramètres de lien de partage par défaut à l’aide des paramètres avancés PowerShell](sensitivity-labels-teams-groups-sites.md#configure-settings-for-the-default-sharing-link-for-a-site-by-using-powershell-advanced-settings).
- Les tableaux de [fonctionnalités](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) qui listent les versions minimales prise en charge pour l’étiquetage intégré ont désormais des versions pour le canal actuel, le canal Enterprise mensuel et le canal Semi-Annual Enterprise.

## <a name="august-2021"></a>Août 2021

### <a name="app-governance"></a>Gouvernance des applications
- [Entrées étendues pour les informations sur les alertes](app-governance-anomaly-detection-alerts.md#collection-alerts). De nouvelles entrées ont été ajoutées pour décrire des informations supplémentaires sur les alertes désormais disponibles dans la gouvernance des applications.

### <a name="communication-compliance"></a>Conformité des communications
- [Les canaux de conformité des communications](communication-compliance-channels.md) ont ajouté une nouvelle prise en charge de la fonctionnalité d’aperçu pour l’analyse des pièces jointes modernes Teams conversations et canaux privés.

### <a name="compliance--service-assurance"></a>Certification du service & conformité

- [L’assurance de](/compliance/) service a été mise à jour avec des mises à jour de contenu trimestrielles pour les certifications et les déclarations d’applicabilité :
  - Architecture
  - Journalisation d'audit
  - Chiffrement et gestion des clés
  - Gestion des identités et des accès
  - Microsoft 365'accès aux données
  - Sécurité réseau
  - Confidentialité
  - Résilience et continuité
  - Gestion des risques
  - Développement et opérations de sécurité
  - Surveillance de la sécurité
  - Gestion de fournisseurs
  - Gestion des vulnérabilités

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- [Référence de stratégie de protection contre la perte de données](dlp-policy-reference.md). Ajout d’une nouvelle page de référence de stratégie pour vous aider à créer des stratégies.

### <a name="insider-risk-management"></a>Gestion des risques internes
- [Découvrez et configurez la détection du signal](insider-risk-management-browser-support.md) du navigateur de gestion des risques internes. Fonctionnalité d’aperçu pour la configuration de la détection du signal du navigateur pour les navigateurs Edge et Chrome.

### <a name="retention-and-records-management"></a>Gestion des enregistrements et de la rétention
- [Flowchart pour déterminer quand](retention-flowchart.md) un élément sera conservé ou définitivement supprimé pour compléter les concepts et les exemples des principes de rétention.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité
- Améliorations apportées aux stratégies d’étiquetage automatique qui incluent des [nombres plus élevés](apply-sensitivity-label-automatically.md) pris en charge pour les sites et stratégies, la prise en charge de tous les sites OneDrive et SharePoint et la possibilité de sélectionner les sites SharePoint disponibles au lieu d’avoir à entrer chaque site par URL et améliorations de simulation.
- L’étiquetage automatique dans Office applications en tant que paramètre d’étiquette de sensibilité prend désormais en charge la correspondance exacte des données [(EDM).](apply-sensitivity-label-automatically.md#custom-sensitive-information-types-with-exact-data-match)
- Les étiquettes par défaut sont désormais étendues [Power BI (en prévisualisation).](/power-bi/admin/service-security-sensitivity-label-default-label-policy)
- Les événements d’audit pour les Outlook sur le web [](data-classification-activity-explorer-available-events.md) qui s’surfacent dans l’Explorateur d’activités sont désormais entièrement déployés, ce qui signifie que l’activité des utilisateurs pour les étiquettes intégrées est désormais disponible pour toutes les applications Office sur toutes les plateformes.
- Les [](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) tableaux des fonctionnalités pris en charge ont une nouvelle note de bas de page pour Windows pour clarifier que les versions minimales sont pour le canal actuel et un conseil pour comparer plus facilement les versions antérieures qui omettent les zéros non obligatoires par rapport aux versions plus récentes.
