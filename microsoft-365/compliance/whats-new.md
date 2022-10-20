---
title: Nouveautés des solutions de conformité et de risque Microsoft Purview
description: Qu’il s’agisse d’ajouter de nouvelles solutions au centre de conformité, de mettre à jour les fonctionnalités existantes en fonction de vos commentaires ou de déployer une documentation actualisée et mise à jour, Microsoft Purview vous aide à rester au top du paysage de conformité en constante évolution. Découvrez ce que nous avons fait ce mois-ci.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
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
- purview-compliance
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 0e2c9d57aefed7c0cf77bcce14106b0b622e8735
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68634451"
---
# <a name="whats-new-in-microsoft-purview-risk-and-compliance-solutions"></a>Nouveautés des solutions de conformité et de risque Microsoft Purview

Qu’il s’agisse d’ajouter de nouvelles solutions au [portail de conformité Microsoft Purview](microsoft-365-compliance-center.md), de mettre à jour des fonctionnalités existantes en fonction de vos commentaires ou de déployer une documentation actualisée et mise à jour, Microsoft 365 vous aide à rester au-dessus du paysage de conformité en constante évolution. Jetez un coup d’œil ci-dessous pour découvrir les nouveautés de Microsoft Purview aujourd’hui.

> [!NOTE]
> Certaines fonctionnalités de conformité sont déployées à différentes vitesses pour nos clients. Si vous ne voyez pas encore de fonctionnalité, essayez de vous ajouter à [une version ciblée](/office365/admin/manage/release-options-in-office-365).

> [!TIP]
> Vous vous intéressez à ce qui se passe dans d’autres centres d’administration ? Consultez les articles suivants :
>
> - [Nouveautés du Centre d'administration Microsoft 365](/office365/admin/whats-new-in-preview)
> - [Nouveautés du Centre d’administration SharePoint](/sharepoint/what-s-new-in-admin-center)
> - [Nouveautés de Microsoft 365 Defender](../security/defender/whats-new.md)
>
> Et visitez la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour en savoir plus sur les fonctionnalités de Microsoft 365 qui ont été lancées, qui sont en cours de déploiement, qui sont en cours de développement, qui ont été annulées ou qui ont été publiées précédemment.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="october-2022"></a>Octobre 2022

### <a name="communication-compliance"></a>Conformité des communications

- **En préversion** : Nouvelle [intégration de la conformité des communications à la gestion des risques internes](/microsoft-365/compliance/communication-compliance#integration-with-insider-risk-management-preview). La conformité des communications peut désormais fournir des signaux disgruntlement détectés dans les messages aux stratégies de disgruntlement de la gestion des risques internes. Le disgruntlement détecté dans les messages par la stratégie de conformité des communications agit comme un événement déclencheur pour placer les utilisateurs dans l’étendue des stratégies de gestion des risques internes.

### <a name="insider-risk-management"></a>Gestion des risques internes

- **En préversion** : la gestion des risques internes introduit des [preuves légales](/microsoft-365/compliance/insider-risk-management-forensic-evidence), qui permettent la capture d’activités visuelles personnalisables sur les appareils pour aider votre organisation à mieux atténuer, comprendre et répondre aux risques potentiels de données tels que l’exfiltration de données non autorisées de données sensibles.
- **En préversion** : intégration de la gestion des risques [internes à la conformité des communications](/microsoft-365/compliance/communication-compliance#integration-with-insider-risk-management-preview) lors de l’utilisation *des fuites de données par des utilisateurs mécontents* ou *des violations de stratégie de sécurité par des modèles de stratégie d’utilisateurs mécontents* . La conformité des communications peut désormais fournir des signaux disgruntlement détectés dans les messages aux stratégies de disgruntlement de la gestion des risques internes.
- **En préversion** : Une nouvelle [personnalisation des alertes inline](/microsoft-365/compliance/insider-risk-management-settings#inline-alert-customization-preview) permet aux analystes et aux enquêteurs de modifier rapidement les stratégies lors de l’examen des alertes.
- Nouvelles [mises à jour de scoring de contenu de priorité](/microsoft-365/compliance/insider-risk-management-policies#prioritize-content-in-policies) qui vous permettent de choisir d’attribuer des scores de risque à toutes les activités détectées par une stratégie ou uniquement aux activités qui incluent du contenu prioritaire.
- Les équipes de sécurité sont désormais en mesure de [personnaliser un déclencheur de sécurité](/microsoft-365/compliance/insider-risk-management-policies#policy-templates) dans la stratégie de « fuites de données » pour qu’il apparaisse lorsqu’un utilisateur exécute une séquence, ce qui lui permet de répondre aux actions de l’utilisateur qui peuvent être considérées comme plus risquées.
- Les nouvelles mises à jour permettent désormais aux équipes de sécurité de créer des [stratégies avec des séquences](/microsoft-365/compliance/insider-risk-management-policies#sequence-detection-preview) sans autres sélections d’indicateurs de stratégie sous-jacents obligatoires.

## <a name="september-2022"></a>Septembre 2022

### <a name="communication-compliance"></a>Conformité des communications

- [Prise en main de la conformité des communications](/microsoft-365/compliance/communication-compliance-configure) : nouvelles mises à jour pour les actions recommandées et intégration accélérée. Les actions recommandées peuvent aider votre organisation à prendre rapidement en main la conformité des communications.
- [Examiner et corriger les alertes de conformité des communications](/microsoft-365/compliance/communication-compliance-investigate-remediate) : nouvelle mise à jour pour la prise en charge de la mise en surbrillance des mots clés pour la vue en texte brut. La mise en surbrillance des mots clés, actuellement disponible uniquement en anglais, peut vous aider à vous diriger vers la zone d’intérêt pour les longs messages et pièces jointes.
- [Utiliser les rapports et audits de conformité des communications](/microsoft-365/compliance/communication-compliance-reports-audits) : clarifications sur les autorisations nécessaires pour afficher et gérer les rapports de conformité des communications. Pour afficher et gérer des rapports, les utilisateurs doivent être affectés au groupe de *rôles Visionneuses de conformité des communications* .

### <a name="data-classification"></a>Classification des données

- [Augmenter la précision du classifieur (préversion)](data-classification-increase-accuracy.md) : cet article vous montre comment vérifier si les éléments mis en correspondance par un classifieur sont vrais positifs (correspondance) ou faux positifs (non une correspondance) et fournir une correspondance ou non un retour de correspondance. Vous pouvez utiliser ces commentaires pour ajuster vos classifieurs afin d’augmenter la précision. Vous pouvez également envoyer des versions expurgées du document et les commentaires Match, Not a Match à Microsoft si vous souhaitez améliorer la précision des classifieurs que Microsoft fournit.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- En préversion : les étiquettes de rétention prennent désormais en charge l’exécution d’un flux Power Automate à la fin de la période de rétention pour prendre en charge les actions personnalisées et l’intégration à d’autres solutions. Pour plus d’informations, consultez [Personnaliser ce qui se passe à la fin de la période de rétention](retention-label-flow.md).
- Pour les éléments de gestion des enregistrements en cours de révision de destruction, lorsque vous sélectionnez cet élément dans la zone Disposition du portail de conformité, une nouvelle colonne Progression affiche l’état de l’élément. Cet état peut être « Approuvé pour suppression, « Suppression en attente de SharePoint/OneDrive » ou « Suppression en attente d’Exchange » ou « Supprimé définitivement ». Lorsqu’un élément est approuvé pour suppression définitive dans le cadre du processus de révision de la suppression, cette suppression peut prendre jusqu’à 15 jours et cette nouvelle colonne vous aide à suivre sa progression.
- La configuration permettant [d’activer une boîte aux lettres pour l’archivage](enable-archive-mailboxes.md) est déplacée vers le nouveau Centre d’administration Exchange (EAC) et les instructions ont été mises à jour en conséquence.
- Actuellement, les classifieurs pouvant être formés pour appliquer automatiquement des étiquettes de rétention ne sont pas pris en charge avec des étendues adaptatives. Pour contourner ce problème, utilisez des étendues statiques pour cette combinaison de configuration.
- Les instructions de [personnalisation d’une stratégie d’archivage et de suppression pour les boîtes aux lettres](set-up-an-archive-and-deletion-policy-for-mailboxes.md) sont mises à jour pour inclure uniquement les balises de rétention qui ont un résultat qui ne peut pas être atteint avec la rétention De Microsoft 365.

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- [Concevoir une conception de règle complexe de stratégie de protection contre la perte de données (préversion)](dlp-policy-design.md#complex-rule-design-preview) : le générateur de règles DLP prend en charge la logique booléenne (AND, OR, NOT) et les groupes imbriqués. Nouvelle vidéo et contenu ajouté qui vous guident tout au long de cette nouvelle fonctionnalité.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité
- [La prise en charge PDF](sensitivity-labels-office-apps.md#pdf-support) dans Word, Excel et PowerPoint est désormais disponible pour Windows Current Channel et Monthly Enterprise Channel.
- L’étiquette par défaut des documents existants est désormais entièrement déployée sur Mac et Windows dans le canal actuel et le canal d’entreprise mensuel, ce qui assure la parité avec le complément AIP.
- En préversion : nouvelle [barre de confidentialité](sensitivity-labels-office-apps.md#sensitivity-bar) et prise en charge des [couleurs d’étiquette](sensitivity-labels-office-apps.md#label-colors) dans les applications Office, offrant une parité avec le complément AIP avec des fonctionnalités supplémentaires.
- En préversion : [prise en charge de S/MIME](sensitivity-labels-office-apps.md#configure-a-label-to-apply-smime-protection-in-outlook) pour Windows, fournissant la parité avec le complément AIP. La prise en charge de Mac et des appareils mobiles est maintenant entièrement déployée.
- En préversion : Classifieurs pouvant être formés pour les stratégies d’étiquetage automatique (toutes les charges de travail).

### <a name="trainable-classifiers"></a>Classifieurs avec capacité d’apprentissage

- [Définitions de classifieurs pouvant être formés](classifier-tc-definitions.md)  : plus de 20 nouveaux classifieurs ont été ajoutés, de sorte que les définitions de tous les classifieurs pouvant être formés ont été réparties dans ce nouvel article.

## <a name="august-2022"></a>Août 2022

### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Mettez à jour les actions d’amélioration et intégrez les données de conformité dans le Gestionnaire de conformité](compliance-manager-update-actions.md) : nouvelle fonctionnalité de mise à jour simultanée de plusieurs actions d’amélioration, qui permet également aux organisations d’effectuer le travail de conformité dans d’autres systèmes dans le Gestionnaire de conformité pour y effectuer le suivi.
- [Utilisation des actions d’amélioration dans le Gestionnaire de conformité](compliance-manager-improvement-actions.md) : les utilisateurs peuvent désormais inclure un lien/UNE URL dans le cadre de preuves pour l’implémentation ou le test des actions d’amélioration.

### <a name="compliance-offerings--service-assurance"></a>Offres de conformité & assurance du service

- [Gestion des modifications Microsoft 365](/compliance/assurance/assurance-microsoft-365-change-management) : nouvelle rubrique d’assurance qui couvre les modifications de code et de non-code apportées aux services Microsoft.
- **Japan CS Gold Mark offering topic** - retired, certification not renewed.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- La configuration [Exchange (héritée)](data-lifecycle-management.md#exchange-legacy-features) passe du Centre d’administration Exchange classique (EAC) au portail de conformité Microsoft Purview, sous gestion du **cycle de vie des données**. Les fonctionnalités de gestion du cycle de vie des données existantes se trouvent sous un nouveau sous-nœud, **Microsoft 365**.
- Pour les pièces jointes cloud (actuellement déployées en préversion), la rétention automatique et temporaire des fichiers supprimés dans la bibliothèque de conservation de la conservation permet de se protéger contre la suppression du fichier d’origine par les utilisateurs avant que la copie puisse être créée et étiquetée. Pour plus d’informations, consultez [le fonctionnement de la rétention avec les pièces jointes cloud](retention-policies-sharepoint.md#how-retention-works-with-cloud-attachments).

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- [Prise en main de la protection contre la perte de données](endpoint-dlp-getting-started.md) de point de terminaison - Liens mis à jour pour des noms d’articles plus accessibles
- [En savoir plus sur la protection contre la perte de données](endpoint-dlp-learn-about.md) de point de terminaison : liens mis à jour pour des noms d’articles plus accessibles ; conseils mis à jour sur les types de fichiers pris en charge ; mise à jour des instructions de copie vers d’autres applications
- [Partager des alertes de protection contre la perte de données](dlp-share-alerts.md) (préversion) - nouveau
- [Configurer les paramètres DLP du point de terminaison](dlp-configure-endpoint-settings.md) - Disponibilité générale des domaines de service sensibles
- [Informations de référence sur la stratégie de protection contre la perte de données](dlp-policy-reference.md) - Disponibilité générale des domaines de service sensibles
- [Utilisation de la protection contre la perte de données de point de terminaison](endpoint-dlp-using.md) - Disponibilité générale des domaines de service sensibles

### <a name="insider-risk-management"></a>Gestion des risques internes

- [Créer et gérer des stratégies de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-policies#general-risky-browser-usage-preview) : nouveau modèle général de stratégie d’utilisation des navigateurs à risque pour la préversion publique. Cette stratégie peut vous aider à détecter et à activer le scoring des risques pour la navigation web qui peut être en violation de la stratégie d’utilisation acceptable de votre organisation, comme la visite de sites qui représentent une menace (par exemple, des sites de hameçonnage) ou qui contiennent du contenu pour adultes.
- [Créer et gérer des stratégies de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-policies#quick-policies-from-recommended-actions-preview) - Nouveaux modèles de stratégies rapides pour la préversion publique. Vous pouvez utiliser une stratégie rapide pour accélérer la configuration d’une *fuite de données générale* ou *d’un vol de données en quittant la stratégie des utilisateurs*.
- [Prise en main des paramètres de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-settings#intelligent-detections) : les nouvelles exclusions et classifieurs prennent en charge les paramètres de détection intelligents.

### <a name="microsoft-priva"></a>Microsoft Priva

- [Microsoft Priva guide de l’utilisateur d’évaluation](/privacy/priva/priva-trial-playbook) - Conseils actualisés et simplifiés pour s’aligner sur les mises à jour récentes de la documentation

### <a name="sensitive-information-types"></a>Types d'informations sensibles

- [Créer des données exactes correspondant à une expérience classique de flux de travail de type informations sensibles](sit-create-edm-sit-classic-ux-workflow.md) - nouveau
- [Créer l’exemple de fichier SIT EDM pour la nouvelle expérience](sit-create-edm-sit-unified-ux-sample-file.md) - nouveau
- [Créer EDM SIT à l’aide de la nouvelle expérience](sit-create-edm-sit-unified-ux-schema-rule-package.md) - new
- [Créer une nouvelle expérience de flux de travail de type de données exactes correspondant à des informations sensibles](sit-create-edm-sit-unified-ux-workflow.md) - nouveau
- Ajout de conseils pour l’expérience de création sit EDM nouvelle et classique dans les rubriques suivantes :
  - [Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md)
  - [Créer des données exactes correspondant au type d’informations sensibles/au package de règles](sit-get-started-exact-data-match-create-rule-package.md)
  - [Créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-create-schema.md)
  - [Exporter les données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md)
  - [Hacher et charger la table de source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md)
  - [Tester un type d’informations sensibles correspondant exactement aux données](sit-get-started-exact-data-match-test.md)
  - [En savoir plus sur les types d’informations sensibles correspondant exactement aux données](sit-learn-about-exact-data-match-based-sits.md)
- [Limites des types d’informations sensibles](sit-limits.md) - nouveau

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Généralement disponible (GA) et n’avez plus besoin d’accepter : les appareils mobiles (iOS et Android, avec des versions minimales) prennent en charge [la co-création de fichiers chiffrés avec des étiquettes de confidentialité](sensitivity-labels-coauthoring.md).
- Disponibilité générale avec Canal actuel 2208+ pour Word, Excel, PowerPoint sur Windows : [prise en charge du pdf](sensitivity-labels-office-apps.md#pdf-support). La prise en charge d’Outlook pour bloquer l’impression au format PDF si nécessaire est déployée sur le canal bêta.
- Déploiement en disponibilité générale avec Current Channel 2208+ pour Windows et 16.63+ pour macOS : étiquette par défaut pour les documents existants.
- En préversion : Classifieurs pouvant être formés pour les [stratégies d’étiquetage automatique](apply-sensitivity-label-automatically.md).
- Conseils sur la [configuration d’Azure AD pour le contenu chiffré](encryption-azure-ad-configuration.md), qui inclut des informations sur les paramètres d’accès interlocataire des identités externes, les stratégies d’accès conditionnel et les comptes invités.

## <a name="july-2022"></a>Juillet 2022

### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Liste des modèles du Gestionnaire de conformité](compliance-manager-templates-list.md) : ajout d’un nouveau modèle Premium dans la catégorie Asia-Pacific pays pour « Hong Kong - Code of Banking Practice and Payment Card ».

### <a name="compliance-offerings--service-assurance"></a>Offres de conformité & assurance du service

- [Résilience des données SharePoint et OneDrive dans Microsoft 365](/compliance/assurance/assurance-sharepoint-onedrive-data-resiliency) : modifications apportées à la section de résilience du stockage d’objets blob.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- [Section des licences combinées](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management--microsoft-purview-records-management) avec des détails supplémentaires pour les scénarios.
- La conservation des versions de documents SharePoint n’utilise plus de fichiers distincts dans la bibliothèque de conservation. Pour plus d’informations, consultez la documentation mise à jour, [Comment la rétention fonctionne avec les versions de document](retention-policies-sharepoint.md#how-retention-works-with-document-versions).
- Guide pratique pour [valider les enregistrements que vous avez migrés vers SharePoint ou OneDrive](records-management.md#validating-migrated-records).
- Mise à jour du rapport d’évaluation de Cohasset pour [SEC 17a-4(f), FINRA 4511(c) et CFTC 1.31(c)-(d)](retention-regulatory-requirements.md#sec-17a-4f-finra-4511c-and-cftc-131c-d).
- Suppression des exclusions de responsabilité en préversion pour les stratégies de rétention pour les canaux partagés Teams maintenant que cette fonctionnalité est déployée en disponibilité générale.

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- [Informations de référence sur la stratégie DLP](dlp-policy-reference.md#blocking-and-notifications-in-sharepoint-online-and-onedrive-for-business) : ajout d’une nouvelle section sur le blocage et les notifications dans SharePoint Online, et OneDrive Entreprise en réponse aux escalades de clients. Mise à jour pour prendre en charge la préversion publique des domaines de services sensibles. Mise à jour de la prise en charge de Power BI. Mise à jour de la prise en charge des classifieurs pouvant être formés.
- [Configurer les paramètres DLP du point](dlp-configure-endpoint-settings.md#sensitive-service-domains) de terminaison : ajout d’un nouveau contenu à la prise en charge de la préversion publique des domaines de service sensibles en préversion publique. Comportement de correspondance d’URL mis à jour.
- Utilisation du point [de terminaison DLP](endpoint-dlp-using.md#scenario-6-monitor-or-restrict-user-activities-on-sensitive-service-domains) : nouveau contenu de scénario à la prise en charge de la préversion publique des domaines de services sensibles. Informations d’abonnement mises à jour.

### <a name="ediscovery"></a>eDiscovery

- [Requêtes de mots clés et conditions de recherche pour eDiscovery](keyword-queries-and-search-conditions.md) : suppression des informations remplacées.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

- [Définitions d’entités de type d’informations sensibles](sensitive-information-type-entity-definitions.md) : nous avons ajouté 41 nouvelles définitions d’entité SIT à la prise en charge des 41 nouvelles SIT d’analyse des informations d’identification. Le contenu des définitions d’entité SIT a été entièrement retravaillé à partir d’un seul article monolithique en articles individuels plus faciles à référencer et à prendre en charge. Il y a maintenant 303 articles au total, y compris les 42 nouveaux SIT d’analyse des informations d’identification.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- En préversion : [étiquette de confidentialité par défaut pour une bibliothèque de documents SharePoint](sensitivity-labels-sharepoint-default-label.md).
- En préversion : [Autorisations personnalisées à l’échelle de l’organisation](encryption-sensitivity-labels.md#support-for-organization-wide-custom-permissions) pour Windows lorsqu’une étiquette de confidentialité est configurée pour permettre aux utilisateurs d’attribuer des autorisations. Pour plus d’informations, consultez  [Prise en charge des autorisations personnalisées à l’échelle de l’organisation](encryption-sensitivity-labels.md#support-for-organization-wide-custom-permissions).
- Déploiement maintenant vers le canal actuel (préversion) pour Windows : étiquette par défaut pour les documents existants.
- Désormais disponible avec le canal d’entreprise Semi-Annual : [co-création pour les fichiers chiffrés avec des étiquettes de confidentialité](sensitivity-labels-coauthoring.md).
- Le [nom d’étendue de l’étiquette](sensitivity-labels.md#label-scopes) « Fichiers & e-mails » que vous voyez lors de la configuration d’une étiquette de confidentialité est désormais « Items ».

## <a name="june-2022"></a>Juin 2022

### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Alertes et stratégies d’alerte du Gestionnaire de conformité Microsoft Purview](compliance-manager-alert-policies.md) : ajout de trois rôles AAD disposant des autorisations nécessaires pour créer ou modifier des stratégies d’alerte.
- [Analyseur de configuration pour Microsoft Purview](compliance-manager-mcca.md) : nouveau nom et liens de référence mis à jour pour cet outil de prise en main du Gestionnaire de conformité anciennement nommé « Microsoft Compliance Configuration Analyzer ».

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- De nombreuses mises à jour de page pour les captures d’écran de marque Microsoft Purview.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- En préversion : [Microsoft API Graph pour la gestion des enregistrements](compliance-extensibility.md#microsoft-graph-api-for-records-management-preview)

### <a name="microsoft-priva"></a>Microsoft Priva

- [Demandes de droits d’objet](/privacy/priva/subject-rights-requests) : mises à jour importantes et restructuration du contenu SRR pour mieux aider les utilisateurs à chaque étape de progression; détails ci-dessous.
  - [Découvrez Demandes de droits des personnes concernées Priva](/privacy/priva/subject-rights-requests) : une articulation plus claire de la propriété de valeur client et du plan général du processus SRR.
  - [Comprendre les pages de flux de travail et de détails](/privacy/priva/subject-rights-requests-workflow) : décrit les étapes à suivre pour effectuer une demande, indiquer une progression manuelle ou automatique et établir une liaison avec du contenu détaillé; une section explique comment interpréter et utiliser la page de détails d’une demande, y compris le nouvel onglet « Historique ».
  - [Créez une demande et définissez des paramètres de recherche](/privacy/priva/subject-rights-requests-create) : un nouveau cadrage avec des sous-titres expliquant qu’il existe maintenant deux façons de créer une requête : par le biais d’une méthode personnalisée à l’aide d’un processus guidé et par le biais de la nouvelle fonctionnalité d’utilisation d’un modèle, dont les paramètres de recherche visent à récupérer le contenu le plus pertinent pour la situation.
  - [Estimation et récupération des données](/privacy/priva/subject-rights-requests-data-retrieval) : explique pourquoi certaines demandes s’interrompent à l’étape de l’estimation des données et comment ajuster la recherche en conséquence ; explique également comment définir une demande de pause avant de passer automatiquement à la récupération des données.
  - [Passez en revue les données d’une demande de droits d’objet](/privacy/priva/subject-rights-requests-data-review) : les nouvelles fonctionnalités de fichier d’importation permettent aux utilisateurs d’importer des fichiers à partir d’emplacements autres que Microsoft 365, ou des fichiers autrement non récupérés par la recherche, dans l’onglet Données collectées.
  - [Générer des rapports et fermer des demandes](/privacy/priva/subject-rights-requests-reports) : précise quand les packages de données finaux sont générés et quels types de fichiers ils incluent.
  - [Intégrer et étendre via Microsoft API Graph et Power Automate](/privacy/priva/subject-rights-requests-automate) - révision du titre de cette page Power Automate précédente et contenu de page développé pour inclure API Graph contenu et liens de référence qui vivaient précédemment sur une autre page.

### <a name="sensitive-information-types"></a>Types d'informations sensibles

- [En savoir plus sur les types d’informations sensibles basés sur des correspondances de données exactes](sit-learn-about-exact-data-match-based-sits.md) : ajout d’une section sur les services pris en charge par EDM.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- En préversion : [prise en charge PDF pour les applications Office](sensitivity-labels-office-apps.md#pdf-support), qui inclut la conversion de documents au format PDF, l’héritage de l’étiquette avec les marquages visuels et le chiffrement. L’impression au format PDF n’est pas prise en charge et cette option devient indisponible pour les utilisateurs si leur stratégie d’étiquette est configurée pour l’étiquetage obligatoire.
- En préversion : la boîte de dialogue que les utilisateurs voient quand leur stratégie d’étiquette est configurée pour exiger une justification pour supprimer ou rétrograder une étiquette est mise à jour pour avertir les utilisateurs que leur réponse typée ne doit pas inclure de données sensibles. La capture d’écran de la section [Quelles stratégies d’étiquette peuvent faire](sensitivity-labels.md#what-label-policies-can-do) montre cette boîte de dialogue mise à jour qui fera son chemin dans les canaux de déploiement Office pour une utilisation en production.
- En préversion : [La prise en charge d’Outlook pour appliquer la protection S/MIME](sensitivity-labels-office-apps.md#configure-a-label-to-apply-smime-protection-in-outlook) commence à peine à être déployée sur les plateformes clientes.
- Pour [les stratégies d’étiquetage automatique](apply-sensitivity-label-automatically.md#creating-an-auto-labeling-policy), un nouveau paramètre qui peut activer automatiquement la stratégie s’il n’est pas modifié dans un nombre défini de jours.

### <a name="trainable-classifiers"></a>Classifieurs entraînables

- [En savoir plus sur les classifieurs pouvant être formés](classifier-learn-about.md) : ajout du classifieur pouvant être entraîné pour les images Adult, Racy et Gory.

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

- [En savoir plus sur les obstacles à l’information](information-barriers.md), [bien démarrer avec les obstacles à l’information](information-barriers-policies.md) : structure refactorisé des rubriques et clarification supplémentaire pour Exchange Online le support et les limitations, mis à jour pour inclure la prise en charge de la nouvelle expérience d’interface utilisateur de l’IB.

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
- [Utilisez des entités nommées dans vos stratégies DLP](named-entities-use.md) : ajout de l’instruction de support pour Microsoft Defender for Cloud Apps.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Nouvelle option à la fin du processus de création ou de modification de l’étiquette, pour [convertir automatiquement les paramètres d’étiquetage automatique en stratégie d’étiquetage automatique](apply-sensitivity-label-automatically.md#convert-your-label-settings-into-an-auto-labeling-policy).
- Les stratégies d’étiquetage automatique pour SharePoint et OneDrive peuvent désormais appliquer des étiquettes avec chiffrement lorsque le compte qui a modifié le fichier pour la dernière fois n’existe plus dans Azure AD.
- Les étiquettes de conteneur sont prises en charge pour les réseaux de distribution de contenu (CDN) Office 365.
- Clarifications pour [la suppression et la suppression d’étiquettes](create-sensitivity-labels.md#removing-and-deleting-labels).
- Nouveaux [scénarios courants](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels) :
  - Étiqueter des colonnes de base de données SQL à l’aide des mêmes étiquettes de confidentialité que celles utilisées pour les fichiers et les e-mails afin que l’organisation dispose d’une solution d’étiquetage unifiée qui continue de protéger les données structurées lorsqu’elles sont exportées
  - Appliquer une étiquette de confidentialité à un fichier après avoir reçu une alerte indiquant que le contenu contenant des données personnelles est partagé et nécessite une protection

### <a name="changes-to-product-names"></a>Modifications apportées aux noms des produits

Pour relever les défis du milieu de travail décentralisé et riche en données d’aujourd’hui, nous introduisons [Microsoft Purview](https://aka.ms/microsoftpurview), un ensemble complet de solutions qui vous aide à comprendre, régir et protéger l’ensemble de votre patrimoine de données. Cette nouvelle famille de marques combine les fonctionnalités de l’ancien Mappage de données Microsoft Purview et du portefeuille de conformité Microsoft 365 sur lequel les clients s’appuient déjà, fournissant une gouvernance unifiée des données et une gestion des risques pour votre organisation.

| **Ancien nom** | **Nouveau nom** | **Description** |
|:----------------|:-------------|:----------------|
| Audit avancé Microsoft 365 <br><br> Audit de base microsoft 365 | Audit de Microsoft Purview (Premium) <br><br> Microsoft Purview Audit (Standard)| Les solutions d’audit fournissent une solution intégrée pour aider les organisations à répondre efficacement aux événements de sécurité, aux enquêtes judiciaires, aux enquêtes internes et aux obligations de conformité. Pour plus d’informations, consultez [Microsoft Purview Advanced Audit (Premium)](advanced-audit.md) et [Microsoft Purview Advanced Audit (Standard).](set-up-basic-audit.md) |
| Conformité des communications Microsoft 365 | Conformité des communications Microsoft Purview | La conformité des communications permet de réduire les risques en vous aidant à détecter, capturer et prendre rapidement des mesures correctives pour les canaux de communication d’entreprise et les violations de stratégie. Pour en savoir plus, consultez [Conformité des communications Microsoft Purview](communication-compliance-solution-overview.md). |
| Gestionnaire de conformité Microsoft | Gestionnaire de conformité Microsoft Purview | Le Gestionnaire de conformité peut vous aider tout au long de votre parcours de conformité, de l’inventaire des risques de protection de vos données à la gestion des complexités de l’implémentation de contrôles, la mise à jour des réglementations et des certifications et la création de rapports aux auditeurs. Pour plus d’informations, consultez [le Gestionnaire de conformité Microsoft Purview](compliance-manager.md). |
| Clé client Microsoft 365 | Clé client Microsoft Purview | La clé client offre une protection supplémentaire contre l’affichage des données par des systèmes ou du personnel non autorisés, et complète le chiffrement de disque BitLocker dans les centres de données Microsoft. Pour plus d’informations, consultez [la clé client Microsoft Purview](customer-key-overview.md). |
| Customer Lockbox dans Office 365 | Microsoft Purview Customer Lockbox | Customer Lockbox garantit que Microsoft ne peut pas accéder à votre contenu pour effectuer des opérations de service sans votre approbation explicite. Customer Lockbox vous permet d’entrer dans le processus de flux de travail d’approbation utilisé par Microsoft pour vous assurer que seules les demandes autorisées autorisent l’accès à votre contenu. Pour plus d’informations, consultez [Microsoft Purview Customer Lockbox](customer-lockbox-requests.md). |
| Protection contre la perte de données | Protection contre la perte de données Microsoft Purview | DLP permet de protéger les données sensibles et de réduire les risques en empêchant les utilisateurs de partager ces données de manière inappropriée avec des personnes qui ne devraient pas les avoir. Pour en savoir plus, consultez [Protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md). |
| Chiffrement à double clé pour Microsoft 365 | Chiffrement à double clé Microsoft Purview | Double Key Encryption (DKE) utilise deux clés ensemble pour accéder au contenu protégé. Microsoft stocke une clé dans Microsoft Azure, et vous détenez l’autre clé. Pour en savoir plus, consultez [Le chiffrement à double clé Microsoft Purview](double-key-encryption.md) |
| Obstacles à l’information Microsoft 365 | Cloisonnement de l’information Microsoft Purview | Les obstacles à l’information sont une solution qui limite la communication et la collaboration entre certaines personnes au sein de votre organisation afin de protéger les informations internes. Pour en savoir plus, consultez [Microsoft Purview Information Barriers](information-barriers-solution-overview.md). |
| Microsoft Information Protection | Protection de l'information Microsoft Purview | La protection des informations vous aide à découvrir, classifier et protéger des informations sensibles où qu’elles résident ou voyagent. Pour en savoir plus, consultez [Protection des données Microsoft Purview](information-protection.md). |
| Gouvernance des informations Microsoft | Gestion du cycle de vie des données Microsoft Purview | La gestion du cycle de vie des données vous fournit des outils et des fonctionnalités pour conserver le contenu dont vous avez besoin pour conserver et supprimer le contenu que vous n’avez pas. Pour en savoir plus, consultez [Gestion du cycle de vie des données Microsoft Purview](data-lifecycle-management.md). |
| Microsoft 365 : gestion des risques internes | Microsoft Purview : gestion des risques internes | La gestion des risques internes utilise l’ensemble des indicateurs de service et tiers pour vous aider à identifier, trier et agir rapidement sur l’activité des utilisateurs à risque. Pour en savoir plus, consultez [Gestion des risques internes Microsoft Purview](insider-risk-management.md). |
| Chiffrement de messages Office 365 | Chiffrement des messages Microsoft Purview | Avec Le chiffrement des messages, votre organisation peut envoyer et recevoir des messages électroniques chiffrés entre des personnes internes et externes à votre organisation. Pour en savoir plus, consultez [Chiffrement de messages Microsoft Purview](ome.md). |
| Privileged Access Management dans Microsoft 365 | Privileged Access Management Microsoft Purview | Privileged Access Management permet de protéger votre organisation contre les violations et de respecter les meilleures pratiques de conformité en limitant l’accès permanent aux données sensibles ou l’accès aux paramètres de configuration critiques. Pour plus d’informations, consultez [Microsoft Purview Privileged Access Management](privileged-access-management-solution-overview.md). |
| Connecteurs de données Microsoft | Connecteurs de données Microsoft Purview | Microsoft 365 permet aux administrateurs d’utiliser des connecteurs de données pour importer et archiver des données non-Microsoft tierces à partir de plateformes de médias sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration de documents dans des boîtes aux lettres de votre organisation Microsoft 365. Pour plus d’informations, consultez [les connecteurs de données Microsoft Purview](compliance-extensibility.md). |
| Microsoft 365 advanced eDiscovery <br><br> Microsoft 365 Core eDiscovery | Microsoft Purview eDiscovery (Premium) <br><br> Microsoft Purview eDiscovery (Standard) | La découverte électronique, ou eDiscovery, est le processus d'identification et de livraison d'informations électroniques qui peuvent être utilisées comme preuves dans des affaires juridiques. Pour plus d’informations, consultez [Microsoft Purview eDiscovery (Premium)](overview-ediscovery-20.md) et [Microsoft Purview eDiscovery (Standard).](get-started-core-ediscovery.md) |
| Centre de conformité Microsoft 365 | Portail de conformité Microsoft Purview | Administration portail pour accéder aux solutions et au catalogue de solutions dans la suite Microsoft 365 E5 Conformité. Pour en savoir plus, consultez [portail de conformité Microsoft Purview](microsoft-365-compliance-center.md). |
