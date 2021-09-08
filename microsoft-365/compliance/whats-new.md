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
localization_priority: Normal
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: Que ce soit l’ajout de nouvelles solutions au centre de conformité, la mise à jour des fonctionnalités existantes en fonction de vos commentaires ou le déploiement d’une documentation actualisée et mise à jour, Microsoft 365 vous permet de rester au-dessus du paysage de conformité en constante évolution. Découvrez ce que nous avons fait ce mois-ci.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: f05350819c040f2b230bc9be9f963b9bcf057452
ms.sourcegitcommit: 8db88004f4c015138b20c55095ada2c0c79e5910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2021
ms.locfileid: "58928691"
---
# <a name="whats-new-in-microsoft-365-compliance"></a>Nouveautés dans la conformité Microsoft 365

Que ce soit en ajoutant de nouvelles solutions au [Centre de conformité Microsoft 365,](microsoft-365-compliance-center.md)en mettant à jour les fonctionnalités existantes en fonction de vos commentaires ou en mettant en place une documentation actualisée et mise à jour, Microsoft 365 vous aide à rester informé du paysage de conformité en constante évolution. Consultez la ci-dessous pour voir les nouveautés de la conformité Microsoft 365 jour.

> [!NOTE]
> Certaines fonctionnalités de conformité sont déployées à des vitesses différentes pour nos clients. Si vous ne voyez pas encore de fonctionnalité, essayez de vous ajouter à [la version ciblée.](/office365/admin/manage/release-options-in-office-365)

> [!TIP]
> Vous êtes intéressé par ce qui se passe dans d’autres centres d’administration ? Consultez les articles suivants :
>
> - [Nouveautés du Centre d'administration Microsoft 365](/office365/admin/whats-new-in-preview)
> - [Nouveautés du Centre d’administration SharePoint de gestion](/sharepoint/what-s-new-in-admin-center)
> - [Nouveautés de Microsoft 365 Defender](../security/defender/whats-new.md)
>
> Consultez la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour en savoir plus sur les fonctionnalités Microsoft 365 qui ont été lancées, sont en cours de déploiement, sont en cours de développement, ont été annulées ou publiées précédemment.

## <a name="august-2021"></a>Août 2021

### <a name="app-governance"></a>Gouvernance des applications
- [Entrées étendues pour les informations sur les alertes.](app-governance-anomaly-detection-alerts.md#collection-alerts) De nouvelles entrées ont été ajoutées pour décrire des informations supplémentaires sur les alertes désormais disponibles dans la gouvernance des applications.

### <a name="communication-compliance"></a>Conformité des communications
- [La référence des fonctionnalités de](communication-compliance-feature-reference.md) conformité des communications a ajouté une nouvelle prise en charge de la fonctionnalité d’aperçu pour l’analyse des pièces jointes modernes dans Teams conversations et canaux privés.

### <a name="compliance--service-assurance"></a>Certification du service & conformité

- [L’assurance de](https://docs.microsoft.com/en-us/compliance/) service a été mise à jour avec des mises à jour de contenu trimestrielles pour les certifications et les déclarations d’applicabilité :
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

- [Référence de stratégie de protection contre la perte de données.](dlp-policy-reference.md) Ajout d’une nouvelle page de référence de stratégie pour vous aider à créer des stratégies.

### <a name="insider-risk-management"></a>Gestion des risques internes
- [Découvrez et configurez la détection du signal](insider-risk-management-browser-support.md)du navigateur de gestion des risques internes. Fonctionnalité d’aperçu pour la configuration de la détection du signal du navigateur pour les navigateurs Edge et Chrome.

### <a name="retention-and-records-management"></a>Gestion des enregistrements et de la rétention
- [Flowchart pour déterminer quand](retention-flowchart.md) un élément sera conservé ou supprimé définitivement pour compléter les concepts et les exemples des principes de rétention.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité
- Améliorations apportées aux stratégies d’étiquetage automatique qui incluent des nombres plus [élevés](apply-sensitivity-label-automatically.md#recent-enhancements-for-auto-labeling-policies) pris en charge pour les sites et stratégies, la prise en charge de tous les sites OneDrive et SharePoint et la possibilité de sélectionner les sites SharePoint disponibles au lieu d’avoir à entrer chaque site par URL et améliorations de simulation.
- L’étiquetage automatique dans Office applications en tant que paramètre d’étiquette de sensibilité prend désormais en charge la correspondance exacte des données [(EDM).](apply-sensitivity-label-automatically.md#custom-sensitive-information-types-with-exact-data-match)
- Les étiquettes par défaut sont désormais étendues [Power BI (en prévisualisation).](/power-bi/admin/service-security-sensitivity-label-default-label-policy)
- Les événements d’audit [](data-classification-activity-explorer-available-events.md) pour les Outlook sur le web qui s’surfacent dans l’Explorateur d’activités sont désormais entièrement déployés, ce qui signifie que l’activité des utilisateurs pour les étiquettes intégrées est désormais disponible pour toutes les applications Office sur toutes les plateformes.
- Les [](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) tableaux des fonctionnalités pris en charge ont une nouvelle note de bas de page pour Windows afin de clarifier que les versions minimales sont pour le canal actuel et un conseil pour comparer plus facilement les versions antérieures qui omettent les zéros non non pris en compte par rapport aux versions plus récentes.

## <a name="july-2021"></a>Juillet 2021

### <a name="advanced-ediscovery"></a>Advanced eDiscovery

- [Advanced eDiscovery flux](teams-workflow-in-advanced-ediscovery.md) de travail pour le contenu dans Microsoft Teams à l’aide de grands cas ajout d’un flux de travail de bout en bout de gestion du contenu Teams dans Advanced eDiscovery ; inclut des détails sur l’aperçu de la nouvelle fonctionnalité de transcription de conversation.
- Utilisez de grands cas dans [Advanced eDiscovery](advanced-ediscovery-large-cases.md) ajout d’un aperçu du nouveau format de cas de grande taille qui étend les limites de révision et de cas et prend en charge les transcriptions de conversation pour Teams et Yammer conversation.

### <a name="app-governance"></a>Gouvernance des applications

- Le [module de gouvernance des](app-governance-manage-app-governance.md) applications pour Microsoft Cloud App Security (MCAS) est passé en prévisualisation publique. La gouvernance des applications permet de surveiller les applications basées sur OAUth dans votre client M365 et génère des alertes d’activité qui peuvent représenter des programmes malveillants ou des niveaux d’autorisation inappropriés.

### <a name="compliance-offerings"></a>Offres pour la conformité

- [Les offres de conformité changent](/compliance/regulatory/offering-home) en se concentrant sur la couverture de service applicable et les mises à jour pour s’aligner plus étroitement avec les offres Azure pour les [réglementations](/azure/compliance) applicables.

### <a name="compliance--service-assurance"></a>Certification du service & conformité

- [Assurance de service](/compliance/) (mise à jour ; révision trimestrielle des mises à jour de contenu pour les certifications et déclarations d’applicabilité)
    - Vérifications d’arrière-plan dans le cloud
    - Transfert d'& employé
    - Gouvernance
    - Ressources humaines
    - Gestion des incidents
    - Filtrage avant l’embauche
    - Gestion des incidents de sécurité (SIM)
    - SIM : containment, éradication et récupération
    - SIM – Analyse des & détection
    - SIM : rapports post-incident
    - SIM – Préparation
    - Isolation du locataire

### <a name="data-classification"></a>Classification des données

- [En savoir plus sur la classification des données.](data-classification-overview.md) Mise à jour pour la version GA du classifieur de discrimination entra nements.

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- [Découvrez comment Microsoft 365 protection contre la](endpoint-dlp-learn-about.md) perte de données de point de terminaison a ajouté des conseils mis à jour sur l’activité de fichier Toujours auditer pour les appareils.
- [Mise en place du scanneur](dlp-on-premises-scanner-get-started.md) local de protection contre la perte de données mis à jour pour la version GA.
- [En savoir plus sur la Microsoft 365 protection contre](dlp-on-premises-scanner-learn.md) la perte de données sur site mise à jour pour la version GA.
- [Utilisez le Microsoft 365 protection contre](dlp-on-premises-scanner-use.md) la perte de données local mis à jour pour la version GA.
- [Utilisez des stratégies de protection contre](dlp-use-policies-non-microsoft-cloud-apps.md) la perte de données pour les applications cloud non-Microsoft mises à jour pour la version GA et l’intégration MIP-MCAS.

### <a name="insider-risk-management"></a>Gestion des risques internes

- [Examiner les activités de gestion des](insider-risk-management-activities.md) risques internes a ajouté des mises à jour de contenu pour les nouveaux rapports d’activité des utilisateurs et de nouvelles fonctionnalités d’aperçu de plusieurs alertes.
- [Prise en charge des paramètres](insider-risk-management-settings.md) de gestion des risques internes ajout de mises à jour de contenu pour les nouvelles fonctionnalités RBAC pour choisir les réviseurs pour la fonctionnalité d’aperçu des groupes d’utilisateurs prioritaires.

### <a name="privacy-management"></a>Gestion de la confidentialité

- La [gestion de la confidentialité Microsoft](privacy-management.md) est passée en prévisualisation publique. La gestion de la confidentialité permet à votre organisation de comprendre et de gérer les données personnelles dans votre environnement Microsoft 365, de corriger les risques potentiels en matière de confidentialité et de répondre aux demandes de droits de l’objet.

### <a name="retention-and-records-management"></a>Gestion des enregistrements et de la rétention
- En prévisualisation : les stratégies de [rétention pour Teams](create-retention-policies.md#retention-policy-for-teams-locations) prend désormais en charge les canaux privés en tant que nouveaux emplacements Teams lorsque vous créez ou modifiez une stratégie de rétention
- Les instructions [d’importation d’un plan de](file-plan-manager.md#import-retention-labels-into-your-file-plan) gestion de fichiers sont mises à jour pour inclure les enregistrements réglementaires et les dépendances sont désormais répertoriées pour chaque entrée.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

Les pages suivantes ont été ajoutées :

- [Référence de filtres de type d’informations sensibles personnalisé](sit-custom-sit-filters.md)
- [Modifier un type d’informations sensibles personnalisé à l’aide de PowerShell](sit-modify-a-custom-sensitive-information-type-in-powershell.md)
- [Supprimer un type d’informations sensibles personnalisé à l’aide de PowerShell](sit-remove-a-custom-sensitive-information-type-in-powershell.md)

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité
- Les classifieurs entraisables sont désormais généralement disponibles pour l’étiquetage automatique dans [Office apps](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps) for Windows and the web (Office Online)
- L’étiquetage obligatoire est désormais étendu aux [Power BI (en prévisualisation)](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy)
- Pour [la co-auteur]( sensitivity-labels-coauthoring.md)pour les fichiers chiffrés avec des étiquettes de confidentialité : déploiement de la prise en charge des stratégies DLP qui utilisent des étiquettes de confidentialité comme conditions et pièces jointes non chiffrées pour les e-mails
- Les événements d’audit Outlook sont désormais disponibles pour macOS, iOS et Android, et sont également Outlook sur le web

## <a name="june-2021"></a>Juin 2021

### <a name="customer-key"></a>Clé client

- [Chiffrement de service avec clé](customer-key-overview.md) client (les DEP de niveau client de clé client chiffrent désormais la configuration des étiquettes de Protection des données Microsoft.)

### <a name="data-connectors"></a>Connecteurs de données

- Nous avons publié 17 nouveaux connecteurs de données en partenariat avec [17a-4 LLC](archiving-third-party-data.md#17a-4-data-connectors) et un nouveau connecteur en partenariat avec [CellTrust](archiving-third-party-data.md#celltrust-data-connectors). Nous avons également publié des connecteurs de données supplémentaires en partenariat avec [Veritas](archiving-third-party-data.md#veritas-data-connectors) et [TeleMessage](archiving-third-party-data.md#telemessage-data-connectors). À ce jour, 65 connecteurs de données sont disponibles pour importer et archiver des données tierces vers des Microsoft 365.

### <a name="ediscovery"></a>eDiscovery

- [Interroger et filtrer le contenu](review-set-search.md) d’un jeu à réviser (nouvelle fonctionnalité de requête et de filtrage dans un nouveau format d’UX pour filtrer et rechercher du contenu dans un jeu à réviser)
- Baliser des documents dans un jeu à réviser dans [Advanced eDiscovery](tagging-documents.md) (nouvelle fonctionnalité de balise et expérience UX pour accélérer et faciliter le marquage des documents dans un jeu à réviser ; inclut une nouvelle fonctionnalité de marquage des documents à l’aide d’une requête et à l’aide de filtres pour rechercher ou exclure rapidement des éléments de jeu à réviser en fonction de la façon dont un élément est balisé)
- Configurer des limites de conformité pour les enquêtes [eDiscovery](set-up-compliance-boundaries.md) (Microsoft a supprimé l’obligation de contacter le support MS pour demander qu’un attribut de conformité soit synchronisé avec les comptes OneDrive ; désormais, un filtre d’autorisations de recherche de boîte aux lettres est utilisé pour appliquer les limites de conformité pour OneDrive)

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- L’Assistant Stratégie d’étiquette de confidentialité prend désormais en charge [Outlook options](sensitivity-labels-office-apps.md#outlook-specific-options-for-default-label-and-mandatory-labeling) spécifiques pour l’étiquette par défaut et l’étiquetage obligatoire en tant que configuration plus facile que les paramètres avancés (toujours pris en charge) de PowerShell.
- La prise [en charge des marquages dynamiques avec des variables](sensitivity-labels-office-apps.md#dynamic-markings-with-variables ) est désormais en cours de déploiement pour Word, Excel et PowerPoint sur le web
- Pour [les stratégies d’étiquetage](apply-sensitivity-label-automatically.md) Exchange, si l’étiquette est configurée pour le chiffrement, ce chiffrement n’est pas appliqué. En outre, pour Exchange d’étiquetage automatique, vous pouvez désormais configurer des exceptions et les nouvelles conditions suivantes : l’objet, l’adresse du destinataire ou l’adresse de l’expéditeur correspond aux modèles ; l’adresse du destinataire contient des mots ; le domaine de l’expéditeur est, le destinataire est membre de ; l’expéditeur est.
- Lorsque vous utilisez des étiquettes de niveau de sensibilité avec des équipes, des groupes et des sites, vous pouvez utiliser Set-SPOTenant avec le paramètre BlockSendLabelMismatchEmail pour empêcher le courrier électronique généré automatiquement lorsque l’événement d’audit a détecté une inaltérable sensibilité du **document.**  Pour plus d’informations, voir [Auditer les activités des étiquettes de sensibilité.](sensitivity-labels-teams-groups-sites.md#auditing-sensitivity-label-activities )
- Le paramètre [de contexte d’authentification](sensitivity-labels-teams-groups-sites.md#more-information-about-the-dependencies-for-the-authentication-context-option) est désormais entièrement déployé en prévisualisation pour les étiquettes de sensibilité. En outre, cette configuration est désormais prise en charge par Microsoft Teams.
- Les fichiers étiquetés et chiffrés par un nom principal de service (tel que Microsoft Cloud App Security), puis téléchargés sur SharePoint et OneDrive peuvent désormais être ouverts en Office sur le Web lorsque vous avez activé les étiquettes de niveau de sensibilité pour les fichiers Office dans [SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).
- La [co-création](sensitivity-labels-coauthoring.md) et l’auto-ave ne sont plus limités aux locataires de test et sont désormais pris en charge en production lorsque vous utilisez la version 2105 : 18 juin pour Windows et version 16.50+ pour macOS. Notez que cette fonctionnalité n’est toujours pas prise en charge par iOS et Android et reste en prévisualisation.

## <a name="may-2021"></a>Mai 2021

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- De nouveaux conseils [pour la planification de votre](dlp-overview-plan-for-dlp.md) stratégie de protection contre la perte de données.

### <a name="retention-and-records-management"></a>Gestion des enregistrements et de la rétention

- Si vous publiez une stratégie de rétention à partir d’un site SharePoint ou d’un compte OneDrive, vous n’avez plus besoin d’attendre la période de grâce de 30 jours avant de pouvoir supprimer le site ou le compte. Une demande populaire par les clients, cette modification est maintenant terminée pour tous les clients.
- En prévisualisation, révision de **la disposition** en plusieurs étapes : un administrateur peut désormais ajouter jusqu’à cinq étapes consécutives de révision de [la disposition](disposition.md) pour une étiquette de rétention, et les réviseurs peuvent ajouter d’autres utilisateurs à la phase de révision de leur disposition. Vous pouvez également personnaliser les rappels et les notifications par e-mail.

### <a name="sensitive-information-types"></a>Types d'informations sensibles

- Nouvelles informations ajoutées pour vous aider [à modifier un dictionnaire de mots clés](sit-modify-keyword-dictionary.md).

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- En prévisualisation,  un nouveau paramètre pour le contexte d’authentification est désormais disponible lorsque vous configurez une étiquette de niveau de sensibilité pour les [groupes et les sites.](sensitivity-labels-teams-groups-sites.md) Cette option fonctionne conjointement avec les stratégies d’accès conditionnel Azure AD pour appliquer des conditions plus strictes lorsque les utilisateurs accèdent aux sites SharePoint qui ont l’étiquette appliquée. Veillez à lire les [dépendances et limitations](sensitivity-labels-teams-groups-sites.md#more-information-about-the-dependencies-for-the-authentication-context-option) avant de configurer ce paramètre.
- [](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) Les stratégies d’étiquetage automatique qui sont configurées uniquement pour Exchange désormais la prise en charge des étiquettes de confidentialité qui appliquent le chiffrement avec Autoriser les utilisateurs à attribuer des **autorisations** pour les options Ne pas Encrypt-Only pas de données.
- [L’étiquetage obligatoire est](sensitivity-labels-office-apps.md#require-users-to-apply-a-label-to-their-email-and-documents) désormais généralement disponible pour toutes les applications Office, sur toutes les plateformes.

## <a name="april-2021"></a>Avril 2021

### <a name="advanced-ediscovery"></a>Advanced eDiscovery

- [Limites dans Advanced eDiscovery](/microsoft-365/compliance/limits-ediscovery20#export-limits---final-export-out-of-review-set). Les organisations peuvent désormais exporter jusqu’à 5 millions d’éléments ou 500 Mo, selon la taille la plus petite, dans une seule exportation d’éléments d’un groupe de révision.

### <a name="data-classification"></a>Classification des données

- [Activités d’étiquetage disponibles dans l’Explorateur d’activités](/microsoft-365/compliance/data-classification-activity-explorer-available-events)

### <a name="data-connectors"></a>Connecteurs de données

- [Configurer un connecteur pour archiver des données Cisco Jabber sur Oracle](/microsoft-365/compliance/archive-ciscojabberonoracle-data)
- [Configurer un connecteur pour archiver cisco Jabber sur les données PostgreSQL](/microsoft-365/compliance/archive-ciscojabberonpostgresql-data)

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- Nouvelle rubrique de référence sur les [conseils de stratégie de protection contre la perte de données.](/microsoft-365/compliance/dlp-policy-tips-reference)
- Nouvelle rubrique pour [en savoir plus sur la protection contre la perte de données.](/microsoft-365/compliance/dlp-learn-about-dlp)
- Nouvelle rubrique pour [la mise en place du tableau de bord d’alerte de protection contre la perte de données.](/microsoft-365/compliance/dlp-alerts-dashboard-get-started)

### <a name="retention-policies-and-retention-label-policies"></a>Stratégies de rétention et stratégies d’étiquette de rétention

- L’emplacement Microsoft 365 Groups prend désormais en charge l’application des paramètres de rétention uniquement aux boîtes aux lettres Microsoft 365 ou uniquement aux sites SharePoint connectés à l’aide de la cmdlet [Set-RetentionCompliancePolicy PowerShell](/powershell/module/exchange/set-retentioncompliancepolicy) avec le paramètre *Applications.*

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Outlook et mises à jour :

- [Différents paramètres pour l’étiquette par défaut](sensitivity-labels-office-apps.md#outlook-specific-options-for-default-label-and-mandatory-labeling) et l’étiquetage obligatoire sont désormais pris en charge pour l’étiquetage intégré. Auparavant, ces paramètres étaient pris en charge uniquement par le client d’étiquetage unifié AIP.
- [Encrypt-Only est](encryption-sensitivity-labels.md#let-users-assign-permissions) désormais pris en charge par macOS, iOS et Android.
- [L’étiquetage obligatoire](sensitivity-labels-office-apps.md#require-users-to-apply-a-label-to-their-email-and-documents) est en cours de déploiement sur les plateformes restantes.
- [Les marquages dynamiques avec toutes les variables](sensitivity-labels-office-apps.md#dynamic-markings-with-variables) sont pris en charge dans tous Outlook clients.

## <a name="march-2021"></a>Mars 2021

Voici quelques-unes des modifications apportées aux solutions Microsoft 365 conformité et au contenu pour le mois de mars.

### <a name="advanced-ediscovery"></a>Advanced eDiscovery

- **Advanced eDiscovery collections de collections prend** désormais en charge les nouveaux [outils de collections et flux de travail.](/microsoft-365/compliance/collections-overview) D’autres nouvelles rubriques incluent [la création d’un brouillon de collection,](/microsoft-365/compliance/create-draft-collection)la validation d’une collection provisoire dans un jeu à [réviser](/microsoft-365/compliance/commit-draft-collection)et les statistiques et les rapports [de collection.](/microsoft-365/compliance/collection-statistics-reports)
- **Exporter des documents** dans un jeu à réviser vers [un stockage Azure](/microsoft-365/compliance/download-export-jobs) client.
- **Module de codage prédictif pour Advanced eDiscovery**. Tout d’abord, regardez la nouvelle fonctionnalité de [codage](/microsoft-365/compliance/predictive-coding-overview) prédictif qui remplace le module Pertinence retiré.

### <a name="data-classification"></a>Classification des données

- **Explorateur de classification des données**. [Commencer avec l’Explorateur](/microsoft-365/compliance/data-classification-activity-explorer) de classification des données.

### <a name="data-connectors"></a>Connecteurs de données

- **Clés privées**. La prise en charge des clés privées a été ajoutée aux données [de message Bloomberg,](/microsoft-365/compliance/archive-bloomberg-message-data#set-up-a-connector-using-public-keys) aux données [ICE Chat](/microsoft-365/compliance/archive-icechat-data#set-up-a-connector-using-public-keys) et aux connecteurs de données [Instant Bloomberg.](/microsoft-365/compliance/archive-instant-bloomberg-data#set-up-a-connector-using-public-keys)

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- **Microsoft Teams prise en charge.** Prise en charge de la protection contre la perte de [données étendue Microsoft Teams](/microsoft-365/compliance/dlp-teams-default-policy).
- **Extension de conformité Microsoft**. Commencer avec [l’extension de conformité Microsoft](/microsoft-365/compliance/dlp-chrome-get-started).

### <a name="encryption"></a>Chiffrement

- **Clé client pour Microsoft 365**. [Vue d’ensemble de la](/microsoft-365/compliance/customer-key-tenant-level) clé client Microsoft 365 au niveau du client (prévisualisation publique).
- **Chiffrement à double clé**. En savoir plus [sur l’activation de la prise](/microsoft-365/compliance/double-key-encryption) en charge des documents étiquetés et protégés dans SharePoint et OneDrive Entreprise.

### <a name="insider-risk-management"></a>Gestion des risques internes

Les mises à jour suivantes des fonctionnalités de gestion des risques internes ont été publiées pour la prévisualisation publique en mars :

- Nouvelle fonctionnalité d’analyse permettant d’identifier les risques avant de créer des stratégies de risque internes
- Nouvelle prise en charge et gestion de la détection des séquences d’activités de risque
- Nouvelle prise en charge de la détection d’exfiltration cumulative
- Nouvelle prise en charge des recommandations et des rapports d’état des stratégies dans l’application
- Nouvelle fonctionnalité de journal d’audit et rapports
- Améliorations apportées à l’Assistant Création de stratégie
- Mises à jour de l’explorateur de contenu
- Nouveau processus/prise en charge de la gestion des utilisateurs (ajouter/supprimer des utilisateurs de stratégies)
- Nouvelle prise en charge de l’intégration AAD (prise en charge de la stratégie utilisateur de départ)
- Prise en charge de domaine mise à jour dans les stratégies (REGEX)
- Améliorations et améliorations apportées aux modèles de stratégie

Les rubriques suivantes ont été mises à jour ou ajoutées pour prendre en charge ces nouvelles fonctionnalités :

- [En savoir plus sur la gestion des risques internes Microsoft](/microsoft-365/compliance/insider-risk-management)
- [Planifier la gestion des risques Insider](/microsoft-365/compliance/insider-risk-management-plan)
- [Prise en charge des paramètres de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-settings)
- [Prise en main de la gestion des risques internes](/microsoft-365/compliance/insider-risk-management-configure)
- [Créer et gérer les stratégies de risques internes](/microsoft-365/compliance/insider-risk-management-policies)
- [Identifier les alertes de risques internes](/microsoft-365/compliance/insider-risk-management-alerts)
- [Agir sur les cas de risques internes](/microsoft-365/compliance/insider-risk-management-cases)
- [Passer en revue des activités avec le journal d’audit des risques Insider](/microsoft-365/compliance/insider-risk-management-audit-log)
- [Examiner les données à l’aide de l’explorateur de contenu des risques internes](/microsoft-365/compliance/insider-risk-management-content-explorer)
- [Gérer le flux de travail avec le Tableau de bord des utilisateurs](/microsoft-365/compliance/insider-risk-management-users)

### <a name="records-management"></a>Gestion des enregistrements

- **Améliorations apportées au plan de fichiers.** Une mise à [jour du plan](file-plan-manager.md) de fichiers supprime ou améliore les restrictions de longueur précédentes pour l’importation.
- **Supprimer des étiquettes de rétention pour les enregistrements.** Une version d’aperçu prend en charge la possibilité de [supprimer les étiquettes de](create-apply-retention-labels.md#deleting-retention-labels) rétention qui marquent les éléments comme des enregistrements.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

Le contenu a été ajouté ou mis à jour dans les rubriques suivantes :

- [Mise en place d’un type d’informations sensibles personnalisé](/microsoft-365/compliance/create-a-custom-sensitive-information-type)
- [En savoir plus sur les types d’informations confidentielles](/microsoft-365/compliance/sensitive-information-type-learn-about).
- [Créez des types d’informations sensibles personnalisés à l’aide d’une classification Exact Data Match.](/microsoft-365/compliance/create-custom-sensitive-information-types-with-exact-data-match-based-classification)
- [Créer des notifications pour les activités de correspondance de données exactes](/microsoft-365/compliance/sit-edm-notifications-activities)
- [Définitions d’entités de types d’informations sensibles](/microsoft-365/compliance/sensitive-information-type-entity-definitions)
- [Créer un type d’informations sensibles personnalisé à l’aide de PowerShell](/microsoft-365/compliance/create-a-custom-sensitive-information-type-in-scc-powershell)
- [Créer un dictionnaire de mots clés](/microsoft-365/compliance/create-a-keyword-dictionary)

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- **Prise en charge de DoD**. Prise en charge des locataires du gouvernement américain avec des environnements DoD.
- **Chiffrer uniquement pour Outlook**. Les options de chiffrement Outlook désormais inclure Encrypt-Only lorsque vous sélectionnez [Autoriser les utilisateurs à attribuer des autorisations.](encryption-sensitivity-labels.md#let-users-assign-permissions)
- **Application d’étiquettes intégrées dans Office applications.** Mise à [jour des instructions](sensitivity-labels-office-apps.md#office-built-in-labeling-client-and-the-azure-information-protection-client) sur l’application d’étiquettes intégrées dans Office applications lorsque le client d’étiquetage unifié Azure Information Protection est installé.
