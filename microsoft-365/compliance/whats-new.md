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
ms.openlocfilehash: dada5e5fe82f12e02365d9babe4d91c10acdd6195a8371b9fe9b6bd4713d4fe8
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53807551"
---
# <a name="whats-new-in-microsoft-365-compliance"></a>Nouveautés dans la conformité Microsoft 365

Que ce soit en ajoutant de nouvelles solutions au [Centre de conformité Microsoft 365,](microsoft-365-compliance-center.md)en mettant à jour les fonctionnalités existantes en fonction de vos commentaires ou en mettant en place une documentation actualisée et mise à jour, Microsoft 365 vous aide à rester informé du paysage de conformité en constante évolution. Consultez la ci-dessous pour voir les nouveautés de la conformité Microsoft 365 jour.

> [!NOTE]
> Certaines fonctionnalités de conformité sont déployées à des vitesses différentes pour nos clients. Si vous ne voyez pas encore de fonctionnalité, essayez de vous ajouter à [la version ciblée.](/office365/admin/manage/release-options-in-office-365)

> [!TIP]
> Vous êtes intéressé par ce qui se passe dans d’autres centres d’administration ? Consultez les articles suivants :
>
> - [Nouveautés du Centre d’administration Microsoft 365](/office365/admin/whats-new-in-preview)
> - [Nouveautés du Centre d’administration SharePoint de gestion](/sharepoint/what-s-new-in-admin-center)
> - [Nouveautés de Microsoft 365 Defender](../security/defender/whats-new.md)
>
> Consultez la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour en savoir plus sur les fonctionnalités Microsoft 365 qui ont été lancées, sont en cours de déploiement, sont en cours de développement, ont été annulées ou publiées précédemment.

## <a name="june-2021"></a>Juin 2021

### <a name="customer-key"></a>Clé client

- [Chiffrement de service avec clé](customer-key-overview.md) client (les DEP de niveau client de clé client chiffrent désormais la configuration des étiquettes de Protection des données Microsoft.)

### <a name="data-connectors"></a>Connecteurs de données

- Nous avons publié 17 nouveaux connecteurs de données en partenariat avec [17a-4 LLC](archiving-third-party-data.md#17a-4-data-connectors) et un nouveau connecteur en partenariat avec [CellTrust](archiving-third-party-data.md#celltrust-data-connectors). Nous avons également publié des connecteurs de données supplémentaires en partenariat avec [Veritas](archiving-third-party-data.md#veritas-data-connectors) et [TeleMessage](archiving-third-party-data.md#telemessage-data-connectors). À ce jour, 65 connecteurs de données sont disponibles pour importer et archiver des données tierces vers des Microsoft 365.

### <a name="ediscovery"></a>eDiscovery

- [Interroger et filtrer le contenu](review-set-search.md) d’un jeu à réviser (nouvelle fonctionnalité de requête et de filtrage dans un nouveau format d’UX pour filtrer et rechercher du contenu dans un jeu à réviser)
- Baliser des documents dans un jeu à réviser dans [Advanced eDiscovery](tagging-documents.md) (nouvelle fonctionnalité de balise et expérience UX pour accélérer et faciliter le marquage des documents dans un jeu à réviser ; inclut une nouvelle fonctionnalité de marquage des documents à l’aide d’une requête et de filtres pour rechercher ou exclure rapidement les éléments de jeu à réviser en fonction de la façon dont un élément est balisé)
- Configurer des limites de conformité pour les enquêtes [eDiscovery](set-up-compliance-boundaries.md) (Microsoft a supprimé l’obligation de contacter le support MS pour demander qu’un attribut de conformité soit synchronisé avec les comptes OneDrive ; désormais, un filtre d’autorisations de recherche de boîte aux lettres est utilisé pour appliquer les limites de conformité pour OneDrive)

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- L’Assistant Stratégie d’étiquette de confidentialité prend désormais en charge [Outlook options](sensitivity-labels-office-apps.md#outlook-specific-options-for-default-label-and-mandatory-labeling) spécifiques pour l’étiquette par défaut et l’étiquetage obligatoire en tant que configuration plus facile que les paramètres avancés (toujours pris en charge) de PowerShell.
- La prise [en charge des marquages dynamiques avec des variables](sensitivity-labels-office-apps.md#dynamic-markings-with-variables ) est désormais en cours de déploiement pour Word, Excel et PowerPoint sur le web
- Pour [les stratégies d’étiquetage](apply-sensitivity-label-automatically.md) Exchange, si l’étiquette est configurée pour le chiffrement, ce chiffrement n’est pas appliqué. En outre, pour Exchange d’étiquetage automatique, vous pouvez désormais configurer des exceptions et les nouvelles conditions suivantes : l’objet, l’adresse du destinataire ou l’adresse de l’expéditeur correspond aux modèles ; l’adresse du destinataire contient des mots ; le domaine de l’expéditeur est, le destinataire est membre de ; l’expéditeur est.
- Lorsque vous utilisez des étiquettes de niveau de sensibilité avec des équipes, des groupes et des sites, vous pouvez utiliser Set-SPOTenant avec le paramètre BlockSendLabelMismatchEmail pour empêcher le courrier électronique généré automatiquement lorsque l’événement d’audit a détecté une inaltérable sensibilité du **document.**  Pour plus d’informations, voir [Auditer les activités des étiquettes de sensibilité.](sensitivity-labels-teams-groups-sites.md#auditing-sensitivity-label-activities )
- Le paramètre [de contexte d’authentification](sensitivity-labels-teams-groups-sites.md#more-information-about-the-dependencies-for-the-authentication-context-option) est désormais entièrement déployé en prévisualisation pour les étiquettes de sensibilité. En outre, cette configuration est désormais prise en charge par Microsoft Teams.
- Les fichiers étiquetés et chiffrés par un nom principal de service (tel que Microsoft Cloud App Security), puis téléchargés sur SharePoint et OneDrive peuvent désormais être ouverts en Office sur le Web lorsque vous avez activé les étiquettes de niveau de sensibilité pour les fichiers Office dans [SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).
- La [co-création](sensitivity-labels-coauthoring.md) et l’auto-ave ne sont plus limités aux locataires de test et sont désormais pris en charge en production lorsque vous utilisez la version 2105 : 18 juin pour Windows et version 16.50+ pour macOS. Notez que cette fonctionnalité n’est toujours pas prise en charge par iOS et Android et reste en prévisualisation.

## <a name="may-2021"></a>Mai 2021

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- De nouveaux conseils [pour la planification de votre](dlp-overview-plan-for-dlp.md) stratégie de protection contre la perte de données.

### <a name="retention-and-records-management"></a>Gestion des enregistrements et de la rétention

- Si vous publiez une stratégie de rétention à partir d’un site SharePoint ou d’un compte OneDrive, vous n’avez plus besoin d’attendre la période de grâce de 30 jours avant de pouvoir supprimer le site ou le compte. Une demande populaire par les clients, cette modification est maintenant terminée pour tous les clients.
- En prévisualisation, révision de **la disposition** en plusieurs étapes : un administrateur peut désormais ajouter jusqu’à cinq étapes consécutives de révision de [la disposition](disposition.md) pour une étiquette de rétention, et les réviseurs peuvent ajouter d’autres utilisateurs à leur étape de révision de disposition. Vous pouvez également personnaliser les rappels et les notifications par e-mail.

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

## <a name="february-2021"></a>Février 2021

Voici quelques-unes des modifications apportées aux solutions Microsoft 365 conformité et au contenu pour le mois de février.

### <a name="auditing"></a>Audit

- **Gérer les stratégies de rétention du journal d’audit.** En savoir plus sur le nouveau tableau de bord des [stratégies de rétention d’audit.](/microsoft-365/compliance/audit-log-retention-policies#manage-audit-log-retention-policies-1)
- **Recherchez dans le journal d’audit.** [Utilisez le script PowerShell pour effectuer une recherche dans le journal d’audit.](/microsoft-365/compliance/audit-log-search-script)

### <a name="data-classification-content-explorer"></a>Explorateur de contenu de classification des données

Le contenu a été ajouté ou mis à jour dans les rubriques suivantes :

- [Prise en main de l’explorateur de contenu](/microsoft-365/compliance/data-classification-content-explorer)
- [Notes de publication pour la classification des données](/microsoft-365/compliance/data-classification-pub-preview-relnotes)

### <a name="data-loss-prevention"></a>Protection contre la perte de données

Le contenu a été ajouté ou mis à jour dans les rubriques suivantes :

- [En savoir plus sur le point de terminaison DLP](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Envoi des notifications et affichage des conseils de stratégie pour les stratégies DLP](/microsoft-365/compliance/use-notifications-and-policy-tips)
- [En savoir plus sur le scanner local de prévention des pertes de données Microsoft 365](/microsoft-365/compliance/dlp-on-premises-scanner-learn)
- [Prise en main du scanneur local de protection contre la perte de données(préversion)](/microsoft-365/compliance/dlp-on-premises-scanner-get-started)
- [Créer une stratégie DLP pour protéger les documents avec l’ICF ou d’autres propriétés](/microsoft-365/compliance/protect-documents-that-have-fci-or-other-properties)
- [Utilisation de la prévention des pertes de données sur les points de terminaison](/microsoft-365/compliance/endpoint-dlp-using)
- [Prise en main de la protection contre la perte de données de point de terminaison](/microsoft-365/compliance/endpoint-dlp-getting-started)

### <a name="ediscovery"></a>eDiscovery

Le contenu a été ajouté ou mis à jour dans les rubriques suivantes :

- [Déchiffrement dans les outils Microsoft 365 eDiscovery](/microsoft-365/compliance/ediscovery-decryption)
- [Requêtes par mots clés et conditions de recherche](/microsoft-365/compliance/keyword-queries-and-search-conditions#limitations-for-searching-sensitive-data-types)
- [Retrait du module de pertinence dans Advanced eDiscovery](/microsoft-365/compliance/relevance-module-retirement)
- [Utiliser un script pour ajouter des utilisateurs à une attente dans un cas core eDiscovery](/microsoft-365/compliance/use-a-script-to-add-users-to-a-hold-in-ediscovery)

### <a name="encryption"></a>Chiffrement

Le contenu a été ajouté ou mis à jour dans les rubriques suivantes :

#### <a name="azure-rights-management-service-rms"></a>Azure Rights Management Service (RMS)

- [Fonctionnalités de chiffrement gérées par le client](/microsoft-365/compliance/office-365-customer-managed-encryption-features)
- [Exchange Online de messagerie avec AD RMS](/microsoft-365/compliance/information-rights-management-in-exchange-online). La prise en charge de ce service a été dépréciée. Vous ne pouvez plus utiliser AD RMS dans un environnement Exchange hybride. Migrez plutôt vers Azure RMS.

#### <a name="customer-key"></a>Clé client

- [Clé client pour Microsoft 365 au niveau du client](/microsoft-365/compliance/customer-key-tenant-level)
- [Vue d’ensemble de la sécurité et de la conformité](/microsoftteams/security-compliance-overview)

#### <a name="information-rights-management-irm"></a>Gestion des droits relatifs à l'information (IRM)

- [Appliquer la Gestion des droits à l’information (IRM) à une liste ou une bibliothèque](/microsoft-365/compliance/configure-irm-to-use-an-on-premises-ad-rms-server). Ces clouds nationaux ne sont pas en charge :
  - Microsoft Cloud for US Government
  - Microsoft Cloud Germany
  - Azure et Microsoft 365 gérés par 21Vianet en Chine)
- [Configurez IRM pour utiliser un serveur AD RMS local.](/microsoft-365/compliance/configure-irm-to-use-an-on-premises-ad-rms-server) La prise en charge de ce service dans un environnement Exchange hybride est devenu désacdexé.

### <a name="sensitive-information-types"></a>Types d'informations sensibles

Le contenu a été ajouté ou mis à jour dans les rubriques suivantes :

- [En savoir plus sur les types d’informations confidentielles](/microsoft-365/compliance/sensitive-information-type-learn-about).
- [Créer un type d’informations sensibles personnalisé à l’aide de PowerShell](/microsoft-365/compliance/create-a-custom-sensitive-information-type-in-scc-powershell)
- [Créer des types d’informations sensibles personnalisés avec une classification exacte basée sur la correspondance de données](/microsoft-365/compliance/create-custom-sensitive-information-types-with-exact-data-match-based-classification)
- [Définitions d’entités des types d’informations sensibles](/microsoft-365/compliance/sensitive-information-type-entity-definitions)

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Le contenu a été ajouté ou mis à jour dans les rubriques suivantes :

- **SharePoint partage externe.** Pour [les étiquettes de conteneur,](sensitivity-labels-teams-groups-sites.md) l’option de partage externe à partir SharePoint sites est désormais publiée comme généralement disponible. En outre, le Centre d’administration Microsoft 365 et le Planificateur peuvent désormais appliquer ces étiquettes de niveau de sensibilité. 
- **Co-authoring and AutoSave**. La prise en charge de la co-création et de [l’auto-ave](sensitivity-labels-coauthoring.md) pour les fichiers chiffrés est publiée en prévisualisation pour les tests dans les clients hors production.

## <a name="january-2021"></a>Janvier 2021

### <a name="support-for-card-content-in-teams"></a>Prise en charge du contenu de carte dans Teams

Les solutions de conformité Microsoft 365 suivantes [](/microsoftteams/platform/task-modules-and-cards/what-are-cards) permettent désormais de détecter le contenu de carte généré par le biais d’applications Teams messages électroniques :

- **Core et Advanced eDiscovery**. Le contenu de la carte peut désormais [être mis en attente](create-ediscovery-holds.md#preserve-card-content) ou inclus dans les [recherches](/microsoftteams/ediscovery-investigation#search-for-card-content) (s’applique également à la recherche de contenu).
- **Audit**. L’activité de carte est [désormais enregistrée dans le journal d’audit.](/microsoftteams/audit-log-events#teams-activities)
- **Stratégies de rétention**. Peut désormais utiliser des stratégies de rétention [pour conserver et supprimer le contenu de la carte.](retention-policies-teams.md#whats-included-for-retention-and-deletion)

### <a name="information-governance-and-records-management"></a>Gouvernance des informations et gestion des enregistrements

[Nouvelle évaluation de l’utilisation](retention-regulatory-requirements.md#new-zealand-public-records-act) de la gouvernance des informations et de la gestion des enregistrements pour répondre aux obligations de conformité de la Loi sur les enregistrements publics en Nouvelle-Zélande.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Les étiquettes de sensibilité sont désormais pris en charge pour les locataires du gouvernement américain (Cloud de la communauté du secteur public et Cloud de la communauté du secteur public-H).
- Nouvelle [prise en charge de l’étiquetage](sensitivity-labels-office-apps.md) automatique pour macOS.
