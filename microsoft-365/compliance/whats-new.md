---
title: Nouveautés des solutions de conformité et de risque Microsoft Purview
description: Qu’il s’agisse d’ajouter de nouvelles solutions au Centre de conformité, de mettre à jour les fonctionnalités existantes en fonction de vos commentaires ou de déployer une documentation actualisée et mise à jour, Microsoft Purview vous aide à rester au fait du paysage de conformité en constante évolution. Découvrez ce que nous avons fait ce mois-ci.
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
ms.openlocfilehash: 0d84b220496fd0a8f371e57492bb9f4cdd009be8
ms.sourcegitcommit: 21548843708d80bc861f03ffae41457252492bb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68793739"
---
# <a name="whats-new-in-microsoft-purview-risk-and-compliance-solutions"></a>Nouveautés des solutions de conformité et de risque Microsoft Purview

Qu’il s’agisse d’ajouter de nouvelles solutions au [portail de conformité Microsoft Purview](microsoft-365-compliance-center.md), de mettre à jour les fonctionnalités existantes en fonction de vos commentaires ou de déployer une documentation actualisée et mise à jour, Microsoft 365 vous aide à rester au fait du paysage de conformité en constante évolution. Jetez un coup d’œil ci-dessous pour découvrir les nouveautés de Microsoft Purview aujourd’hui.

> [!NOTE]
> Certaines fonctionnalités de conformité sont déployées à des vitesses différentes pour nos clients. Si vous ne voyez pas encore de fonctionnalité, essayez de vous ajouter à [la version ciblée](/office365/admin/manage/release-options-in-office-365).

> [!TIP]
> Vous êtes intéressé par ce qui se passe dans d’autres centres d’administration ? Consultez les articles suivants :
>
> - [Nouveautés de la Centre d'administration Microsoft 365](/office365/admin/whats-new-in-preview)
> - [Nouveautés du Centre d’administration SharePoint](/sharepoint/what-s-new-in-admin-center)
> - [Nouveautés de Microsoft 365 Defender](../security/defender/whats-new.md)
>
> Et visitez la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour en savoir plus sur les fonctionnalités Microsoft 365 qui ont été lancées, qui sont en cours de déploiement, qui sont en cours de développement, qui ont été annulées ou qui ont été publiées précédemment.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="october-2022"></a>Octobre 2022

### <a name="communication-compliance"></a>Conformité des communications

- **En préversion** : Nouvelle intégration de la conformité des communications [à la gestion des risques internes](/microsoft-365/compliance/communication-compliance#integration-with-insider-risk-management-preview). La conformité des communications peut désormais fournir des signaux de risque détectés dans les messages aux stratégies de gestion des risques internes. Les utilisateurs à risque détectés dans les messages par la stratégie de conformité des communications agissent comme un événement déclencheur pour amener les utilisateurs dans l’étendue des stratégies de gestion des risques internes.

### <a name="insider-risk-management"></a>Gestion des risques internes

- **En préversion** : La gestion des risques internes introduit des [preuves d’investigation](/microsoft-365/compliance/insider-risk-management-forensic-evidence), qui permet de capturer des activités visuelles personnalisables sur plusieurs appareils pour aider votre organisation à mieux atténuer, comprendre et répondre aux risques potentiels liés aux données, comme l’exfiltration de données sensibles non autorisées.
- **En préversion** : Intégration de la gestion des risques internes [à la conformité des communications](/microsoft-365/compliance/communication-compliance#integration-with-insider-risk-management-preview) lors de l’utilisation *des modèles de stratégie Fuites de données par les utilisateurs à risque* ou Violations de *stratégie de sécurité par les utilisateurs à risque* . La conformité des communications peut désormais fournir des signaux de risque détectés dans les messages aux stratégies de gestion des risques internes.
- **En préversion** : la nouvelle [personnalisation des alertes inline](/microsoft-365/compliance/insider-risk-management-settings#inline-alert-customization-preview) permet aux analystes et aux enquêteurs de modifier rapidement les stratégies lors de l’examen des alertes.
- Nouvelles [mises à jour de scoring de contenu de priorité](/microsoft-365/compliance/insider-risk-management-policies#prioritize-content-in-policies) qui vous permettent de choisir d’attribuer des scores de risque à toutes les activités détectées par une stratégie ou uniquement aux activités qui incluent du contenu prioritaire.
- Les équipes de sécurité sont désormais en mesure de [personnaliser un déclencheur de sécurité](/microsoft-365/compliance/insider-risk-management-policies#policy-templates) dans la stratégie « fuites de données » pour qu’il s’affiche lorsqu’un utilisateur effectue une séquence, ce qui leur permet de répondre aux actions de l’utilisateur qui peuvent être considérées comme plus risquées.
- Les nouvelles mises à jour permettent désormais aux équipes de sécurité de créer des [stratégies avec des séquences](/microsoft-365/compliance/insider-risk-management-policies#sequence-detection-preview) sans aucune autre sélection d’indicateur de stratégie sous-jacente requise.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- **Disponibilité générale (GA)** : [réétiquetage à la fin de la période de rétention](retention-settings.md#relabeling-at-the-end-of-the-retention-period).
- **Disponibilité générale (GA)** : [démarrage d’un enregistrement déverrouillé](declare-records.md#configuring-retention-labels-to-declare-records).
- **Disponibilité générale (GA)** : les utilisateurs peuvent désormais appliquer des étiquettes de rétention publiées aux fichiers [directement dans Teams](create-apply-retention-labels.md#applying-retention-labels-using-microsoft-365-groups).
- Nouvelles instructions de prise en charge de la rétention : les stratégies de rétention pour Teams prennent en charge la fonctionnalité [de conversation avec moi-même](https://support.microsoft.com/office/start-a-chat-in-teams-0c71b32b-c050-4930-a887-5afbe742b3d8?storagetype=live#bkmk_chatwithself) , [les clips vidéo](https://support.microsoft.com/office/record-a-video-clip-in-teams-0c57dae5-2974-4214-9c46-7a2136386f1c) et les enregistrements de données d’appel, qui sont des messages générés par le système qui contiennent des [métadonnées pour les réunions et les appels](/MicrosoftTeams/ediscovery-investigation#teams-metadata). Les stratégies de rétention pour yammer prennent en charge les [billets de scénario](https://support.microsoft.com/office/overview-of-storyline-for-yammer-and-viva-engage-530e4e66-9f1c-4be1-b371-08ea40dc4b69).
- Amélioration de l’expérience dans le produit si les stratégies de rétention comportent des erreurs : vous verrez maintenant une description détaillée de l’erreur dans le volet d’informations, avec des actions intégrées au produit à effectuer pour résoudre le problème. Par exemple, supprimez les emplacements non valides et resynchronisez la stratégie.

### <a name="microsoft-priva"></a>Microsoft Priva

- **En préversion** : Les stratégies de [transfert de données](/privacy/priva/risk-management-policy-data-transfer) dans La gestion des risques de confidentialité offrent désormais des conditions de limites flexibles supplémentaires : détection des transferts en fonction des attributs Azure Active Directory des utilisateurs, des transferts entre utilisateurs dans différents groupes Microsoft 365 et des transferts entre sites SharePoint.

### <a name="on-premises-scanner"></a>Scanneur local
- **En préversion** : le scanneur local Azure Information Protection (AIP) est renommé **Protection des données Microsoft Purview scanneur** et la [configuration est déplacée vers le portail de conformité Microsoft Purview](/information-protection/deploy-aip-scanner-configure-install).

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité
- Appel à l’action : [Conseils de migration](sensitivity-labels-aip.md) pour vous aider à passer du complément AIP pour les applications Office, avec un [playbook de migration](https://microsoft.github.io/ComplianceCxE/playbooks/AIP2MIPPlaybook) de notre équipe CxE (Customer Experience Engineering)
- **Disponibilité générale (GA)** : contextes d’authentification pour les groupes d’étiquettes [et les paramètres de site](sensitivity-labels-teams-groups-sites.md#how-to-configure-groups-and-site-settings) qui fonctionnent avec les stratégies d’accès conditionnel Azure AD pour appliquer des conditions d’accès plus strictes à un site.
- **Disponibilité générale (GA)** : [autorisations de partage de site à l’aide de PowerShell](sensitivity-labels-teams-groups-sites.md#configure-site-sharing-permissions-by-using-powershell-advanced-settings).
- **Déploiement** : [l’interdiction de la copie dans le Presse-papiers est respectée pour les fichiers étiquetés et chiffrés dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md#limitations), avec quelques exceptions pour les scénarios de réétiquetage.
- **En préversion** : le complément AIP pour les applications Office est [désactivé par défaut](sensitivity-labels-aip.md#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps) et nécessite un nouveau paramètre pour remplacer cette valeur par défaut.
- Prise en charge : [types de fichiers pris en charge pour SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md#supported-file-types), après activation des étiquettes de confidentialité pour ces services.
- Nouveau [prérequis pour la co-création](sensitivity-labels-coauthoring.md#prerequisites) et le client et le scanneur d’étiquetage unifié Azure Information Protection : l’utilisation du chiffrement double clé dans le même locataire que la fonctionnalité de co-édition n’est pas prise en charge.

## <a name="september-2022"></a>Septembre 2022

### <a name="communication-compliance"></a>Conformité des communications

- [Prise en main de la conformité des communications](/microsoft-365/compliance/communication-compliance-configure) : nouvelles mises à jour pour les actions recommandées et l’intégration accélérée. Les actions recommandées peuvent aider votre organisation à prendre rapidement en main la conformité des communications.
- [Examiner et corriger les alertes de conformité des communications](/microsoft-365/compliance/communication-compliance-investigate-remediate) : nouvelle mise à jour pour la prise en charge de la mise en surbrillance des mots clés pour l’affichage en texte brut. La mise en surbrillance des mots clés, actuellement disponible pour la langue anglaise uniquement, peut vous aider à vous diriger vers la zone d’intérêt des messages longs et des pièces jointes.
- [Utiliser des rapports et des audits de conformité des communications](/microsoft-365/compliance/communication-compliance-reports-audits) : clarifications sur les autorisations nécessaires pour afficher et gérer les rapports de conformité des communications. Pour afficher et gérer les rapports, les utilisateurs doivent être affectés au groupe de rôles *Observateurs de conformité des communications* .
 
### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Liste des modèles du Gestionnaire de conformité](/microsoft-365/compliance/compliance-manager-templates-list) : nouveau modèle ajouté pour le programme IRAP (Australian Information Security Registered Assessor Program) avec ISM Version 3.5 - Officiel).

### <a name="data-classification"></a>Classification des données

- [Augmenter la précision du classifieur (préversion)](data-classification-increase-accuracy.md) : cet article vous montre comment vérifier si les éléments mis en correspondance par un classifieur sont vrais positifs (une correspondance) ou faux positifs (non une correspondance) et fournir un commentaire Correspondance ou Non une correspondance. Vous pouvez utiliser ces commentaires pour paramétrer vos classifieurs afin d’augmenter la précision. Vous pouvez également envoyer des versions expurgées du document et les commentaires Match, Not a Match à Microsoft si vous souhaitez aider à améliorer la précision des classifieurs que Microsoft fournit.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- En préversion : Les étiquettes de rétention prennent désormais en charge l’exécution d’un flux Power Automate à la fin de la période de rétention pour prendre en charge les actions personnalisées et l’intégration à d’autres solutions. Pour plus d’informations, consultez [Personnaliser ce qui se passe à la fin de la période de rétention](retention-label-flow.md).
- Pour les éléments de gestion des enregistrements faisant l’objet d’une révision de destruction, lorsque vous sélectionnez cet élément dans la zone Disposition du portail de conformité, une nouvelle colonne Progression affiche l’état de l’élément. Cet état peut être « Approuvé pour la suppression, « En attente de suppression de SharePoint/OneDrive » ou « En attente de suppression d’Exchange » ou « Supprimé définitivement ». Lorsqu’un élément est approuvé pour suppression définitive dans le cadre du processus de révision de destruction, cette suppression peut prendre jusqu’à 15 jours et cette nouvelle colonne vous aide à suivre sa progression.
- La configuration permettant [d’activer une boîte aux lettres pour l’archivage](enable-archive-mailboxes.md) est déplacée vers le nouveau centre d’administration Exchange (EAC) et les instructions ont été mises à jour en conséquence.
- Actuellement, les classifieurs pouvant être entraînés pour les étiquettes de rétention d’application automatique ne sont pas pris en charge avec les étendues adaptatives. Pour contourner ce problème, utilisez des étendues statiques pour cette combinaison de configuration.
- Les instructions de [personnalisation d’une stratégie d’archivage et de suppression pour les boîtes aux lettres](set-up-an-archive-and-deletion-policy-for-mailboxes.md) sont mises à jour pour inclure uniquement les balises de rétention qui ont un résultat qui ne peut pas être obtenu avec la rétention Microsoft 365.

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- [Concevoir une conception de règles complexes de stratégie de protection contre la perte de données (préversion)](dlp-policy-design.md#complex-rule-design-preview) : le générateur de règles DLP prend en charge la logique booléenne (AND, OR, NOT) et les groupes imbriqués. Ajout d’une nouvelle vidéo et d’un nouveau contenu qui vous guide tout au long de cette nouvelle fonctionnalité.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité
- La [prise en charge de PDF](sensitivity-labels-office-apps.md#pdf-support) dans Word, Excel et PowerPoint est désormais disponible pour le canal Windows actuel et le canal Entreprise mensuel.
- L’étiquette par défaut des documents existants est désormais entièrement déployée sur Mac et Windows dans le canal actuel et le canal Entreprise mensuel, ce qui assure la parité avec le complément AIP.
- En préversion : nouvelle [barre de confidentialité](sensitivity-labels-office-apps.md#sensitivity-bar) et prise en charge des [couleurs d’étiquette](sensitivity-labels-office-apps.md#label-colors) dans les applications Office, offrant une parité avec le complément AIP avec des fonctionnalités supplémentaires.
- En préversion : [prise en charge de S/MIME](sensitivity-labels-office-apps.md#configure-a-label-to-apply-smime-protection-in-outlook) pour Windows, fournissant la parité avec le complément AIP. La prise en charge de Mac et mobile est désormais entièrement déployée.
- En préversion : classifieurs pouvant être formés pour les stratégies d’étiquetage automatique (toutes les charges de travail).

### <a name="trainable-classifiers"></a>Classifieurs avec capacité d’apprentissage

- [Définitions de classifieurs pouvant être entraînés](classifier-tc-definitions.md)  : plus de 20 nouveaux classifieurs ont été ajoutés, de sorte que les définitions de tous les classifieurs pouvant être entraînés ont été réparties dans ce nouvel article.

## <a name="august-2022"></a>Août 2022

### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Mettre à jour les actions d’amélioration et intégrer les données de conformité dans le Gestionnaire de conformité](compliance-manager-update-actions.md) : nouvelle fonctionnalité permettant de mettre à jour plusieurs actions d’amélioration à la fois, ce qui permet également aux organisations d’intégrer le travail de conformité effectué dans d’autres systèmes dans le Gestionnaire de conformité à des fins de suivi.
- [Utilisation d’actions d’amélioration dans le Gestionnaire de conformité](compliance-manager-improvement-actions.md) : les utilisateurs peuvent désormais inclure un lien/URL dans le cadre de la preuve de l’implémentation de l’action d’amélioration ou du travail de test.

### <a name="compliance-offerings--service-assurance"></a>Offres de conformité & assurance du service

- [Gestion des modifications Microsoft 365](/compliance/assurance/assurance-microsoft-365-change-management) : nouvelle rubrique d’assurance qui couvre les modifications de code et non-code apportées aux services Microsoft.
- **Japon CS Gold Mark sujet d’offre** - retiré, certification non renouvelée.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- La configuration [Exchange (héritée)](data-lifecycle-management.md#exchange-legacy-features) passe du Centre d’administration Exchange classique (EAC) au portail de conformité Microsoft Purview, sous Gestion du **cycle de vie des données**. Les fonctionnalités de gestion du cycle de vie des données existantes se trouvent sous un nouveau sous-nœud, **Microsoft 365**.
- Pour les pièces jointes cloud (actuellement en cours de déploiement en préversion), conservation automatique et temporaire des fichiers supprimés dans la bibliothèque de conservation de préservation afin de vous protéger contre la suppression du fichier d’origine par les utilisateurs avant que la copie ne puisse être créée et étiquetée. Pour plus d’informations, consultez [Fonctionnement de la rétention avec les pièces jointes cloud](retention-policies-sharepoint.md#how-retention-works-with-cloud-attachments).

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md) - Liens mis à jour pour des noms d’articles plus accessibles
- [En savoir plus sur la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md) - liens mis à jour pour des noms d’articles plus accessibles ; mise à jour des conseils sur les types de fichiers pris en charge ; mise à jour de l’aide sur la copie vers une autre application
- [Alertes de protection contre la perte de données de partage](dlp-share-alerts.md) (préversion) - nouveau
- [Configurer les paramètres DLP du point de terminaison](dlp-configure-endpoint-settings.md) - Disponibilité générale des domaines de service sensibles
- [Informations de référence sur la stratégie de protection contre la perte de données](dlp-policy-reference.md) - Disponibilité générale des domaines de service sensibles
- [Utilisation de la protection contre la perte de données de point de terminaison](endpoint-dlp-using.md) - Disponibilité générale des domaines de service sensibles

### <a name="insider-risk-management"></a>Gestion des risques internes

- [Créer et gérer des stratégies de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-policies#general-risky-browser-usage-preview) : nouveau modèle de stratégie d’utilisation générale du navigateur à risque pour la préversion publique. Cette stratégie peut aider à détecter et à activer le scoring des risques pour la navigation web qui peut être en violation de la stratégie d’utilisation acceptable de votre organisation, par exemple visiter des sites qui posent une menace (par exemple des sites de hameçonnage) ou contiennent du contenu pour adultes.
- [Créer et gérer des stratégies de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-policies#quick-policies-from-recommended-actions-preview) : nouveaux modèles de stratégies rapides pour la préversion publique. Vous pouvez utiliser une stratégie rapide pour accélérer la configuration d’une *stratégie Général fuites de données* ou *vol de données en quittant les utilisateurs*.
- [Prise en main des paramètres de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-settings#intelligent-detections) : prise en charge des nouvelles exclusions et classifieurs dans les paramètres de détection intelligente.

### <a name="microsoft-priva"></a>Microsoft Priva

- [guide de l’utilisateur de Microsoft Priva version d’évaluation](/privacy/priva/priva-trial-playbook) : conseils actualisés et simplifiés pour s’aligner sur les mises à jour récentes de la documentation

### <a name="sensitive-information-types"></a>Types d'informations sensibles

- [Créer une expérience classique de flux de travail de type d’informations sensibles correspondant exactement](sit-create-edm-sit-classic-ux-workflow.md) - nouveau
- [Créer l’exemple de fichier SIT EDM pour la nouvelle expérience](sit-create-edm-sit-unified-ux-sample-file.md) - nouveau
- [Créer EDM SIT à l’aide de la nouvelle expérience](sit-create-edm-sit-unified-ux-schema-rule-package.md) - nouveau
- [Créer une nouvelle expérience de flux de travail de type d’informations sensibles correspondant exactement](sit-create-edm-sit-unified-ux-workflow.md) à la correspondance des données - nouveau
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

- Disponibilité générale (GA) et n’ont plus besoin d’y adhérer : les appareils mobiles (iOS et Android, avec des versions minimales) prennent en charge [la co-création de fichiers chiffrés avec des étiquettes de confidentialité](sensitivity-labels-coauthoring.md).
- DISPONIBILITÉ GÉNÉRALE avec Current Channel 2208+ pour Word, Excel, PowerPoint sur Windows : [prise en charge de PDF](sensitivity-labels-office-apps.md#pdf-support). La prise en charge d’Outlook pour bloquer l’impression au format PDF si nécessaire est déployée sur le canal bêta.
- Déploiement en disponibilité générale avec le canal actuel 2208+ pour Windows et 16.63+ pour macOS : étiquette par défaut pour les documents existants.
- En préversion : classifieurs pouvant être formés pour les [stratégies d’étiquetage automatique](apply-sensitivity-label-automatically.md).
- Conseils sur la [configuration d’Azure AD pour le contenu chiffré](encryption-azure-ad-configuration.md), qui inclut des informations sur les paramètres d’accès interlocataire des identités externes, les stratégies d’accès conditionnel et les comptes invités.

## <a name="july-2022"></a>Juillet 2022

### <a name="compliance-manager"></a>Gestionnaire de conformité

- Liste des [modèles du Gestionnaire de conformité](compliance-manager-templates-list.md) : ajout d’un nouveau modèle Premium dans la catégorie Asia-Pacific pays pour « Hong Kong - Code of Banking Practice and Payment Card ».

### <a name="compliance-offerings--service-assurance"></a>Offres de conformité & assurance du service

- Résilience des [données SharePoint et OneDrive dans Microsoft 365](/compliance/assurance/assurance-sharepoint-onedrive-data-resiliency) - Section Modifications apportées à la résilience du stockage d’objets blob.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- [Section de licence combinée](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management--microsoft-purview-records-management) avec des détails supplémentaires pour les scénarios.
- La conservation des versions de documents SharePoint n’utilise plus de fichiers distincts dans la bibliothèque de conservation de préservation. Pour plus d’informations, consultez la documentation mise à jour, [Fonctionnement de la rétention avec les versions de document](retention-policies-sharepoint.md#how-retention-works-with-document-versions).
- Conseils sur la [validation des enregistrements que vous avez migrés vers SharePoint ou OneDrive](records-management.md#validating-migrated-records).
- Mise à jour du rapport d’évaluation de Cohasset pour [SEC 17a-4(f), FINRA 4511(c) et CFTC 1.31(c)-(d)](retention-regulatory-requirements.md#sec-17a-4f-finra-4511c-and-cftc-131c-d).
- Suppression des clauses d’exclusion de responsabilité en préversion pour les stratégies de rétention pour les canaux partagés Teams maintenant que cette fonctionnalité est déployée en disponibilité générale.

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- Informations de référence sur la [stratégie DLP](dlp-policy-reference.md#blocking-and-notifications-in-sharepoint-online-and-onedrive-for-business) : ajout d’une nouvelle section sur le blocage et les notifications dans SharePoint Online et OneDrive Entreprise en réponse aux escalades de clients. Mise à jour pour prendre en charge la préversion publique des domaines de services sensibles. Mise à jour de la prise en charge de Power BI. Mise à jour de la prise en charge des classifieurs pouvant être entraînés.
- [Configurer les paramètres DLP du point de terminaison](dlp-configure-endpoint-settings.md#sensitive-service-domains) : ajout d’un nouveau contenu à la prise en charge de la préversion publique des domaines de service sensibles en préversion publique. Mise à jour du comportement de correspondance d’URL.
- [Utilisation de DLP de point de terminaison](endpoint-dlp-using.md#scenario-6-monitor-or-restrict-user-activities-on-sensitive-service-domains) : nouveau contenu de scénario pour prendre en charge la préversion publique des domaines de services sensibles. Informations d’abonnement mises à jour.

### <a name="ediscovery"></a>eDiscovery

- [Requêtes par mot clé et conditions de recherche pour eDiscovery](keyword-queries-and-search-conditions.md) : suppression des informations remplacées.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

- [Définitions d’entité de type d’informations sensibles](sensitive-information-type-entity-definitions.md) : nous avons ajouté 41 nouvelles définitions d’entité SIT pour prendre en charge les 41 nouveaux SIT d’analyse des informations d’identification. Le contenu des définitions d’entités SIT a été entièrement retravaillé à partir d’un seul article monolithique en articles individuels plus facilement référencés et supportables. Il y a maintenant 303 articles au total, y compris les 42 nouveaux SIT d’analyse des informations d’identification.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- En préversion : [étiquette de confidentialité par défaut pour une bibliothèque de documents SharePoint](sensitivity-labels-sharepoint-default-label.md).
- En préversion : [Autorisations personnalisées à l’échelle de l’organisation](encryption-sensitivity-labels.md#support-for-organization-wide-custom-permissions) pour Windows lorsqu’une étiquette de confidentialité est configurée pour permettre aux utilisateurs d’attribuer des autorisations. Pour plus d’informations, consultez  [Prise en charge des autorisations personnalisées à l’échelle de l’organisation](encryption-sensitivity-labels.md#support-for-organization-wide-custom-permissions).
- Déploiement sur Canal actuel (préversion) pour Windows : étiquette par défaut pour les documents existants.
- Désormais disponible avec le canal entreprise Semi-Annual : [co-création pour les fichiers chiffrés avec des étiquettes de confidentialité](sensitivity-labels-coauthoring.md).
- Le [nom d’étendue d’étiquette](sensitivity-labels.md#label-scopes) « Fichiers & e-mails » que vous voyez lors de la configuration d’une étiquette de confidentialité est désormais « Items ».

## <a name="june-2022"></a>Juin 2022

### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Alertes et stratégies d’alerte du Gestionnaire de conformité Microsoft Purview](compliance-manager-alert-policies.md) : ajout de trois rôles AAD qui disposent des autorisations nécessaires pour créer ou modifier des stratégies d’alerte.
- [Analyseur de configuration pour Microsoft Purview](compliance-manager-mcca.md) : nouveau nom et liens de référence mis à jour pour cet outil de prise en main du Gestionnaire de conformité anciennement nommé « Microsoft Compliance Configuration Analyzer ».

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- Nombreuses mises à jour de page pour les captures d’écran de la marque Microsoft Purview.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- En préversion : [Microsoft API Graph pour la gestion des enregistrements](compliance-extensibility.md#microsoft-graph-api-for-records-management-preview)

### <a name="microsoft-priva"></a>Microsoft Priva

- [Demandes de droits des sujets](/privacy/priva/subject-rights-requests) : mises à jour importantes et restructuration du contenu SRR pour mieux aider les utilisateurs à chaque étape de progression; détails ci-dessous.
  - [En savoir plus sur Demandes de droits des personnes concernées Priva](/privacy/priva/subject-rights-requests) : une articulation plus claire de la propriété de valeur client et une description générale du processus SRR.
  - [Comprendre le flux de travail et les pages de détails](/privacy/priva/subject-rights-requests-workflow) : décrit les étapes de traitement d’une demande, indique la progression manuelle par rapport à la progression automatique et la liaison à un contenu détaillé ; une section explique comment interpréter et utiliser la page de détails d’une requête, y compris le nouvel onglet « Historique ».
  - [Créer une demande et définir des paramètres de recherche](/privacy/priva/subject-rights-requests-create) : nouveau cadrage avec des sous-titres expliquant qu’il existe désormais deux façons de créer une requête : via une méthode personnalisée à l’aide d’un processus guidé, et via la nouvelle fonctionnalité d’utilisation d’un modèle, dont les paramètres de recherche visent à récupérer le contenu le plus pertinent pour la situation.
  - [Estimation et récupération des données](/privacy/priva/subject-rights-requests-data-retrieval) : explique pourquoi certaines demandes s’interrompent à l’étape d’estimation des données et comment ajuster la recherche en conséquence ; explique également comment définir une requête pour qu’elle soit d’abord suspendue avant de passer automatiquement à la récupération des données.
  - [Passer en revue les données d’une demande de droits de l’objet](/privacy/priva/subject-rights-requests-data-review) : les nouvelles fonctionnalités d’importation de fichier permettent aux utilisateurs d’importer des fichiers provenant d’emplacements non Microsoft 365, ou de fichiers qui n’ont pas été sélectionnés par la recherche, dans l’onglet Données collectées.
  - [Générer des rapports et fermer des demandes](/privacy/priva/subject-rights-requests-reports) : clarifie le moment où les packages de données finaux sont générés et les types de fichiers qu’ils incluent.
  - [Intégrer et étendre via Microsoft API Graph et Power Automate](/privacy/priva/subject-rights-requests-automate) : vous avez modifié le titre de cette page Power Automate précédente et développé le contenu de la page pour inclure API Graph contenu et les liens de référence qui se trouvaient précédemment sur une autre page.

### <a name="sensitive-information-types"></a>Types d'informations sensibles

- [Découvrez les types d’informations sensibles basés sur les correspondances de données exactes](sit-learn-about-exact-data-match-based-sits.md) - section ajoutée sur les services pris en charge par EDM.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- En préversion : [prise en charge pdf pour les applications Office](sensitivity-labels-office-apps.md#pdf-support), qui inclut la conversion de documents au format PDF, en héritant l’étiquette avec tous les marquages visuels et le chiffrement. L’impression au format PDF n’est pas prise en charge, et cette option devient indisponible pour les utilisateurs si leur stratégie d’étiquette est configurée pour l’étiquetage obligatoire.
- En préversion : la boîte de dialogue que les utilisateurs voient quand leur stratégie d’étiquette est configurée pour exiger une justification pour supprimer ou rétrograder une étiquette est mise à jour pour avertir les utilisateurs que leur réponse typée ne doit pas inclure de données sensibles. La capture d’écran de la section [Ce que les stratégies d’étiquettes peuvent faire](sensitivity-labels.md#what-label-policies-can-do) montre cette boîte de dialogue mise à jour qui sera utilisée dans les canaux de déploiement Office pour une utilisation en production.
- En préversion : [La prise en charge d’Outlook pour appliquer la protection S/MIME](sensitivity-labels-office-apps.md#configure-a-label-to-apply-smime-protection-in-outlook) commence tout juste à être déployée sur les plateformes clientes.
- Pour [les stratégies d’étiquetage automatique](apply-sensitivity-label-automatically.md#creating-an-auto-labeling-policy), nouveau paramètre qui peut activer automatiquement la stratégie s’il n’est pas modifié dans un certain nombre de jours.

### <a name="trainable-classifiers"></a>Classifieurs entraînables

- [En savoir plus sur les classifieurs pouvant être entraînés : classifieur](classifier-learn-about.md) pouvant être formé pour adultes, racy et gory.

## <a name="may-2022"></a>Mai 2022

### <a name="communication-compliance"></a>Conformité des communications

- [Rapports et audits de conformité des communications](communication-compliance-reports-audits.md) : limites de taille de fichier mises à jour pour les rapports exportés.
- [Stratégies de conformité des communications](communication-compliance-policies.md) : processus de désactivation/activation des messages signalés par l’utilisateur et clarification du traitement pour Teams et Exchange.

### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Alertes et stratégies d’alerte](compliance-manager-alert-policies.md) : nouvelle section expliquant la stratégie de changement de score par défaut pour toutes les organisations.
- [Utilisation d’actions d’amélioration](compliance-manager-improvement-actions.md) : clarification des états d’état pour l’état d’implémentation et l’état de test, en faisant une distinction pour ce dernier entre les actions testées automatiquement et les actions testées manuellement.
- [Liste des modèles](compliance-manager-templates-list.md) : deux nouveaux modèles ont été ajoutés dans la région Europe, Moyen-Orient et Afrique (EMEA) : Qatar National Information Assurance (NIA) et Loi sur la confidentialité des données des Émirats arabes unis.

### <a name="compliance-offerings--service-assurance"></a>Offres de conformité & assurance du service

- [Microsoft Security Development Lifecycle](/compliance/assurance/assurance-microsoft-security-development-lifecycle) : nouvelle rubrique d’assurance SDL pour les services Microsoft.

### <a name="data-lifecycle-management-and-records-management"></a>Gestion du cycle de vie des données et gestion des enregistrements

- En cours de déploiement en préversion : nouvelle [option de réétiquetage à la fin de la période de rétention](retention-settings.md#relabeling-at-the-end-of-the-retention-period).
- Nouveau guide de déploiement : [Déployer une solution de gouvernance des données avec Microsoft Purview](data-governance-solution.md)
- Correction dans la documentation pour confirmer que les boîtes aux lettres de ressources sont prises en charge pour la rétention et la suppression Exchange pour les étendues statiques et les étendues adaptatives. Pour les étendues statiques, les boîtes aux lettres de ressources sont incluses par défaut dans une stratégie à l’échelle de l’organisation (tous par défaut).
- Nouvelle documentation pour les utilisateurs finaux : [Gérer le stockage des e-mails avec des boîtes aux lettres d’archivage en ligne](https://support.services.microsoft.com/office/manage-email-storage-with-online-archive-mailboxes-1cae7d17-7813-4fe8-8ca2-9a5494e9a721)

### <a name="data-loss-prevention"></a>Protection contre la perte de données

- [Envoyer des notifications par e-mail et des conseils de stratégie pour les stratégies DLP](use-notifications-and-policy-tips.md) : ajout de nouvelles informations sur ce qui déclenche une notification et qui peut les recevoir.

### <a name="information-barriers"></a>Obstacles aux informations

- [Découvrez les obstacles à l’information](information-barriers.md), [Bien démarrer avec les obstacles à l’information](information-barriers-policies.md) : structure refactorisée des rubriques et clarification supplémentaire pour Exchange Online prise en charge et limitations, mise à jour pour inclure la prise en charge de la nouvelle expérience de l’interface utilisateur ib.

### <a name="insider-risk-management"></a>Gestion des risques internes

- [Prise en main des paramètres de gestion des risques internes](insider-risk-management-settings.md) : ajout de conseils pour les nouveaux indicateurs Defender pour le cloud App, nouvelle anomalie comme événement déclencheur dans les seuils personnalisés, nouvelle prise en charge de la stratégie de hiérarchisation des extensions de fichier et des étiquettes de confidentialité.
- [Cas de gestion des risques internes](insider-risk-management-cases.md) : clarification de l’escalade vers les conseils de cas eDiscovery.

### <a name="microsoft-priva"></a>Microsoft Priva

- [En savoir plus sur l’essai gratuit priva](/privacy/priva/priva-trial) - lien mis à jour vers les nouvelles conditions générales de l’essai universel de Microsoft 365 et des mises à jour mineures pour clarifier les rôles et l’éligibilité.
- [Prise en main de Priva](/privacy/priva/priva-setup) : ajout de la section indiquant les limitations de la disponibilité de Priva.

### <a name="sensitive-information-types"></a>Types d'informations sensibles

- [En savoir plus sur les types d’informations sensibles basés sur la correspondance exacte des données](sit-learn-about-exact-data-match-based-sits.md) : à partir d’une escalade de client, ajout des régions dans lesquelles EDM est pris en charge et des procédures pour rechercher la région de votre locataire.
- [Créer un package de règles SIT EDM](sit-get-started-exact-data-match-create-rule-package.md) : ajout de « Utilisation de types de données spécifiques » à partir de l’article sur le schéma.
- [Créer un schéma pour EDM SIT](sit-get-started-exact-data-match-create-schema.md) : suppression de « l’utilisation de types de données spécifiques ».
- [Utiliser des entités nommées dans vos stratégies DLP](named-entities-use.md) : instruction de prise en charge ajoutée pour Microsoft Defender for Cloud Apps.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Nouvelle option à la fin du processus de création ou de modification des étiquettes, pour convertir automatiquement [les paramètres d’étiquetage automatique en stratégie d’étiquetage automatique](apply-sensitivity-label-automatically.md#convert-your-label-settings-into-an-auto-labeling-policy).
- Les stratégies d’étiquetage automatique pour SharePoint et OneDrive peuvent désormais appliquer des étiquettes avec chiffrement lorsque le compte qui a modifié le fichier pour la dernière fois n’existe plus dans Azure AD.
- Les étiquettes de conteneur sont prises en charge pour les réseaux de distribution de contenu (CDN) Office 365.
- Clarifications pour [la suppression et la suppression d’étiquettes](create-sensitivity-labels.md#removing-and-deleting-labels).
- Nouveaux [scénarios courants](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels) :
  - Étiqueter les colonnes de base de données SQL en utilisant les mêmes étiquettes de confidentialité que celles utilisées pour les fichiers et les e-mails afin que l’organisation dispose d’une solution d’étiquetage unifiée qui continue de protéger les données structurées lorsqu’elles sont exportées
  - Appliquer une étiquette de confidentialité à un fichier après avoir reçu une alerte indiquant que le contenu contenant des données personnelles est partagé et nécessite une protection

### <a name="changes-to-product-names"></a>Modifications apportées aux noms de produits

Pour relever les défis de l’espace de travail décentralisé et riche en données d’aujourd’hui, nous introduisons [Microsoft Purview](https://aka.ms/microsoftpurview), un ensemble complet de solutions qui vous permet de comprendre, de gouverner et de protéger l’ensemble de votre patrimoine de données. Cette nouvelle famille de marques combine les fonctionnalités de l’ancienne Mappage de données Microsoft Purview et le portefeuille de conformité Microsoft 365 sur lequel les clients s’appuient déjà, fournissant une gouvernance unifiée des données et une gestion des risques pour votre organisation.

| **Ancien nom** | **Nouveau nom** | **Description** |
|:----------------|:-------------|:----------------|
| Microsoft 365 Advanced Audit <br><br> Microsoft 365 Basic Audit | Audit de Microsoft Purview (Premium) <br><br> Microsoft Purview Audit (Standard)| Les solutions d’audit fournissent une solution intégrée pour aider les organisations à répondre efficacement aux événements de sécurité, aux enquêtes judiciaires, aux enquêtes internes et aux obligations de conformité. Pour plus d’informations, consultez [Microsoft Purview Advanced Audit (Premium)](advanced-audit.md) et [Microsoft Purview Advanced Audit (Standard).](set-up-basic-audit.md) |
| Conformité des communications Microsoft 365 | Conformité des communications Microsoft Purview | La conformité des communications permet de réduire les risques en vous aidant à détecter, capturer et prendre rapidement des mesures correctives pour les canaux de communication d’entreprise et les violations de stratégie. Pour en savoir plus, consultez [Conformité des communications Microsoft Purview](communication-compliance-solution-overview.md). |
| Gestionnaire de conformité Microsoft | Gestionnaire de conformité Microsoft Purview | Le Gestionnaire de conformité peut vous aider tout au long de votre parcours de conformité, de l’inventaire des risques de protection de vos données à la gestion des complexités de l’implémentation de contrôles, la mise à jour des réglementations et des certifications et la création de rapports aux auditeurs. Pour plus d’informations, consultez [Gestionnaire de conformité Microsoft Purview](compliance-manager.md). |
| Clé client Microsoft 365 | Clé client Microsoft Purview | La clé client offre une protection supplémentaire contre l’affichage des données par des systèmes ou du personnel non autorisés, et complète le chiffrement de disque BitLocker dans les centres de données Microsoft. Pour plus d’informations, consultez [Clé client Microsoft Purview](customer-key-overview.md). |
| Customer Lockbox dans Office 365 | Microsoft Purview Customer Lockbox | Customer Lockbox garantit que Microsoft ne peut pas accéder à votre contenu pour effectuer des opérations de service sans votre approbation explicite. Customer Lockbox vous permet d’accéder au processus de flux de travail d’approbation que Microsoft utilise pour garantir que seules les demandes autorisées autorisent l’accès à votre contenu. Pour plus d’informations, consultez [Microsoft Purview Customer Lockbox](customer-lockbox-requests.md). |
| Protection contre la perte de données | Protection contre la perte de données Microsoft Purview | DLP permet de protéger les données sensibles et de réduire les risques en empêchant les utilisateurs de partager ces données de manière inappropriée avec des personnes qui ne devraient pas les avoir. Pour en savoir plus, consultez [Protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md). |
| Chiffrement à double clé pour Microsoft 365 | Chiffrement à double clé Microsoft Purview | Le chiffrement à double clé (DKE) utilise deux clés ensemble pour accéder au contenu protégé. Microsoft stocke une clé dans Microsoft Azure, et vous détenez l’autre clé. Pour plus d’informations, consultez [Chiffrement à double clé Microsoft Purview](double-key-encryption.md) |
| Obstacles à l’information Microsoft 365 | Cloisonnement de l’information Microsoft Purview | Les obstacles à l’information sont une solution qui limite la communication et la collaboration entre certaines personnes au sein de votre organisation pour protéger les informations internes. Pour plus d’informations, consultez [Microsoft Purview Information Barriers](information-barriers-solution-overview.md). |
| Microsoft Information Protection | Protection de l'information Microsoft Purview | La protection des informations vous aide à découvrir, classifier et protéger les informations sensibles où qu’elles se trouvent ou voyagent. Pour en savoir plus, consultez [Protection des données Microsoft Purview](information-protection.md). |
| Gouvernance des informations Microsoft | Gestion du cycle de vie des données Microsoft Purview | La gestion du cycle de vie des données vous fournit des outils et des fonctionnalités pour conserver le contenu dont vous avez besoin et supprimer le contenu que vous n’avez pas. Pour plus d’informations, consultez [Gestion du cycle de vie des données Microsoft Purview](data-lifecycle-management.md). |
| Microsoft 365 : gestion des risques internes | Microsoft Purview : gestion des risques internes | La gestion des risques internes utilise l’ensemble des indicateurs de service et tiers pour vous aider à identifier, trier et agir rapidement sur l’activité des utilisateurs à risque. Pour plus d’informations, consultez [Gestion des risques internes Microsoft Purview](insider-risk-management.md). |
| Chiffrement de messages Office 365 | Chiffrement des messages Microsoft Purview | Avec le chiffrement des messages, votre organisation peut envoyer et recevoir des messages électroniques chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. Pour en savoir plus, consultez [Chiffrement de messages Microsoft Purview](ome.md). |
| Gestion des accès privilégiés dans Microsoft 365 | Privileged Access Management Microsoft Purview | Privileged Access Management permet de protéger votre organisation contre les violations et de respecter les bonnes pratiques de conformité en limitant l’accès permanent aux données sensibles ou à l’accès aux paramètres de configuration critiques. Pour plus d’informations, consultez [Gestion des accès privilégiés Microsoft Purview](privileged-access-management-solution-overview.md). |
| Connecteurs de données Microsoft | Connecteurs de données Microsoft Purview | Microsoft 365 permet aux administrateurs d’utiliser des connecteurs de données pour importer et archiver des données tierces non-Microsoft à partir de plateformes de réseaux sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration de documents dans des boîtes aux lettres de votre organisation Microsoft 365. Pour plus d’informations, consultez [Connecteurs de données Microsoft Purview](compliance-extensibility.md). |
| Microsoft 365 advanced eDiscovery <br><br> Microsoft 365 Core eDiscovery | Microsoft Purview eDiscovery (Premium) <br><br> Microsoft Purview eDiscovery (Standard) | La découverte électronique, ou eDiscovery, est le processus d'identification et de livraison d'informations électroniques qui peuvent être utilisées comme preuves dans des affaires juridiques. Pour plus d’informations, consultez [Microsoft Purview eDiscovery (Premium)](overview-ediscovery-20.md) et [Microsoft Purview eDiscovery (Standard).](get-started-core-ediscovery.md) |
| Centre de conformité Microsoft 365 | Portail de conformité Microsoft Purview | Administration portail pour accéder aux solutions et au catalogue de solutions dans la suite Microsoft 365 E5 Conformité. Pour plus d’informations, consultez [portail de conformité Microsoft Purview](microsoft-365-compliance-center.md). |
