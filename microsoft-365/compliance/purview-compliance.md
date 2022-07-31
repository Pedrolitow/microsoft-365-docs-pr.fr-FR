---
title: Solutions en matière de conformité et de risques Microsoft Purview
description: Utilisez cet article pour en savoir plus sur les solutions de conformité et de risque Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, conformité, solutions
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: m365-security-compliance
ms.openlocfilehash: 96b1efdddcf8a0b2e1034c392c27f160137379de
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66992041"
---
# <a name="microsoft-purview-risk-and-compliance-solutions"></a>Solutions en matière de conformité et de risques Microsoft Purview

Les solutions de risque et de conformité [Microsoft Purview](/purview/purview) vous aident à gérer et à surveiller vos données, à protéger les informations, à réduire les risques de conformité et à répondre aux exigences réglementaires. Cet article vous aidera à en savoir plus sur les solutions de risque et de conformité Microsoft Purview et à commencer rapidement à déployer ces solutions pour répondre à des besoins spécifiques de conformité pour votre organisation.

## <a name="protect-sensitive-data-across-clouds-apps-and-devices"></a>Protéger les données sensibles sur les clouds, les applications et les appareils

Votre stratégie de protection des informations doit être pilotée par vos besoins métier, mais chaque organisation doit protéger une partie ou la totalité de ses données. Utilisez les fonctionnalités de [Protection des données Microsoft Purview](/microsoft-365/compliance/information-protection) (anciennement Protection des données Microsoft) pour vous aider à découvrir, classifier, protéger et régir des informations sensibles où qu’elles résident ou voyagent.

### <a name="know-your-data"></a>Ayez une bonne connaissance de vos données

Vous disposez d’informations résidant dans tous les services Microsoft 365 et en local. Identifier les éléments sensibles et obtenir une visibilité sur la façon dont ils sont utilisés est essentiel à votre pratique de protection des informations. Microsoft Purview inclut :

- [Types d’informations sensibles](/microsoft-365/compliance/sensitive-information-type-learn-about) pour identifier les éléments sensibles à l’aide d’expressions régulières intégrées ou personnalisées, ou d’une fonction.
- [Classifieurs pouvant être formés](/microsoft-365/compliance/classifier-learn-about) pour identifier les éléments sensibles à l’aide d’exemples de données qui vous intéressent plutôt que d’identifier les éléments de l’élément.
- [La classification des données](/microsoft-365/compliance/data-classification-overview) fournit une identification graphique des éléments de votre organisation qui ont une étiquette de confidentialité, une étiquette de rétention ou qui ont été classifiés et les actions que vos utilisateurs effectuent sur eux

### <a name="protect-your-data"></a>Protéger ses données

Il existe de nombreuses fonctionnalités que vous pouvez utiliser à partir de la solution Protection des données Microsoft Purview pour protéger vos données, où qu’elles soient stockées et accessibles. Toutefois, les étiquettes de confidentialité sont la fonctionnalité fondamentale qui fournit des actions de protection et interagisse avec d’autres solutions et fonctionnalités Purview.

Les étiquettes de confidentialité fournissent aux utilisateurs et aux administrateurs une visibilité sur la sensibilité des données qu’ils utilisent, et les étiquettes elles-mêmes peuvent appliquer des actions de protection qui incluent le chiffrement, les restrictions d’accès et les marquages visuels. Pour plus d’informations sur la plage de scénarios d’étiquetage pris en charge, consultez la section [Scénarios courants pour les étiquettes de confidentialité](/microsoft-365/compliance/get-started-with-sensitivity-labels#common-scenarios-for-sensitivity-labels) de la documentation de prise en main. Pour plus d’informations sur les étiquettes de confidentialité, consultez [En savoir plus sur les étiquettes de confidentialité](/microsoft-365/compliance/sensitivity-labels).

### <a name="prevent-data-loss"></a>Évitez les pertes de données

Le partage involontaire d’éléments sensibles peut nuire financièrement à votre organisation et entraîner une violation des lois et réglementations. [Protection contre la perte de données Microsoft Purview](/microsoft-365/compliance/dlp-learn-about-dlp) pouvez protéger votre organisation contre le partage involontaire ou accidentel d’informations sensibles à l’intérieur et à l’extérieur de votre organisation. Dans une stratégie de protection contre la perte de données, vous :

- Définissez les informations sensibles à surveiller, telles que les données financières, d’intégrité, médicales et de confidentialité.
- Où surveiller, comme les services Microsoft 365 ou les appareils Windows et macOS.
- Conditions qui doivent être mises en correspondance pour qu’une stratégie soit appliquée à un élément, comme les éléments contenant une carte de crédit, un permis de conduire ou des numéros de sécurité sociale.
- Actions à effectuer lorsqu’une correspondance est trouvée, comme l’audit, bloquez l’activité et bloquez l’activité avec remplacement.

### <a name="manage-your-data-lifecycle"></a>Gérer votre cycle de vie des données

[Gestion du cycle de vie des données Microsoft Purview](/microsoft-365/compliance/manage-data-governance#microsoft-purview-data-lifecycle-management) (anciennement Microsoft Information Governance) vous fournit des outils et des fonctionnalités pour conserver et supprimer du contenu dans Exchange, SharePoint, OneDrive, Groupes Microsoft 365, Teams et Yammer. La conservation et la suppression des e-mails, documents et messages sont souvent nécessaires pour la conformité et les exigences réglementaires. Toutefois, la suppression de contenu qui n’a plus de valeur métier réduit également votre surface d’attaque.

Pour plus d’informations, consultez [En savoir plus sur la gestion du cycle de vie des données](/microsoft-365/compliance/data-lifecycle-management).

### <a name="encrypt-your-data-and-control-your-encryption-keys"></a>Chiffrer vos données et contrôler vos clés de chiffrement

[Le chiffrement](/microsoft-365/compliance/encryption) est une partie importante de votre stratégie de protection des fichiers et d’informations. Le processus de chiffrement encode vos données (appelées texte en clair) en texte chiffré. Contrairement au texte en clair, le texte chiffré ne peut pas être utilisé par des personnes ou des ordinateurs, sauf si le texte chiffré est déchiffré. Le déchiffrement nécessite une clé de chiffrement dont disposent uniquement les utilisateurs autorisés. Le chiffrement permet de s’assurer que seuls les destinataires autorisés peuvent déchiffrer votre contenu.

[Microsoft Purview Double Key Encryption](/microsoft-365/compliance/double-key-encryption) permet de sécuriser vos données les plus sensibles soumises aux exigences de protection les plus strictes. [La clé client Microsoft Purview](/microsoft-365/compliance/customer-key-overview) vous aide à respecter les obligations réglementaires ou de conformité relatives au contrôle des clés racine. Vous autorisez explicitement les services Microsoft 365 à utiliser vos clés de chiffrement pour fournir des services cloud à valeur ajoutée, tels que eDiscovery, anti-programmes malveillants, anti-courrier indésirable, indexation de recherche, etc.

## <a name="identify-data-risks-and-manage-regulatory-compliance-requirements"></a>Identifier les risques liés aux données et gérer les exigences de conformité réglementaire

Les risques internes sont l’une des principales préoccupations des professionnels de la sécurité et de la conformité dans le milieu de travail moderne. Des études de l’industrie ont montré que les risques internes sont souvent associés à des événements ou activités utilisateur spécifiques. La protection de votre organisation contre ces risques peut être difficile à identifier et difficile à atténuer. Les risques internes comprennent des vulnérabilités dans différents domaines et peuvent entraîner des problèmes majeurs pour votre organisation, allant de la perte de propriété intellectuelle au harcèlement au travail, etc.

Microsoft Purview propose les solutions de conformité suivantes pour aider votre organisation à gérer les risques liés aux données et les exigences de conformité :

- [Gestion des risques internes](#detect-and-act-on-risk-activities-with-insider-risk-management)
- [Conformité des communications](#detect-and-act-on-inappropriate-and-sensitive-messages-with-communication-compliance)
- [Obstacles aux informations](#restrict-communication-and-collaboration-between-users-with-information-barriers)
- [Gestion des enregistrements](#manage-business-legal-or-regulatory-record-keeping-requirements-with-records-management)
- [Audit (Premium) et Audit (Standard)](#log-and-search-for-audited-activities-in-sharepoint-and-onedrive-with-audit-premium-or-audit-standard)
- [eDiscovery (Premium) et eDiscovery (Standard)](#identify-and-manage-data-for-legal-cases-with-ediscovery-premium-or-ediscovery-standard)

### <a name="detect-and-act-on-risk-activities-with-insider-risk-management"></a>Détecter et agir sur les activités à risque avec la gestion des risques internes

[Gestion des risques internes Microsoft Purview](/microsoft-365/compliance/insider-risk-management) utilise l’étendue complète du service et des indicateurs tiers pour vous aider à identifier, trier et agir rapidement sur l’activité des utilisateurs à risque dans votre organisation. En utilisant les journaux d’activité de Microsoft 365 et Microsoft Graph, la gestion des risques internes vous permet de définir des stratégies spécifiques pour identifier les indicateurs de risque. Après avoir identifié les activités à risque, vous pouvez prendre des mesures pour atténuer ces risques.

### <a name="detect-and-act-on-inappropriate-and-sensitive-messages-with-communication-compliance"></a>Détecter et agir sur les messages inappropriés et sensibles avec la conformité des communications

La protection des informations sensibles et la détection et l’action en cas d’incidents de harcèlement au travail sont un élément important du respect des politiques et des normes internes. [Conformité des communications Microsoft Purview permet de](/microsoft-365/compliance/communication-compliance-policies) réduire ces risques en vous aidant à détecter, capturer et prendre rapidement des mesures de correction pour les communications par e-mail et Microsoft Teams. Il s’agit notamment de communications inappropriées contenant des blasphèmes, des menaces, du harcèlement et des communications qui partagent des informations sensibles à l’intérieur et à l’extérieur de votre organisation.

### <a name="restrict-communication-and-collaboration-between-users-with-information-barriers"></a>Restreindre la communication et la collaboration entre les utilisateurs avec des obstacles à l’information

[Microsoft Purview Information Barriers (IB)](/microsoft-365/compliance/information-barriers) est une solution de conformité qui vous permet de restreindre la communication bidirectionnelle et la collaboration entre les groupes et les utilisateurs dans Microsoft Teams, SharePoint Online et OneDrive Entreprise. Souvent utilisé dans les secteurs hautement réglementés, IB peut aider à éviter les conflits d’intérêts et à protéger les informations internes entre les utilisateurs et les domaines organisationnels.

### <a name="manage-business-legal-or-regulatory-record-keeping-requirements-with-records-management"></a>Gérer les exigences commerciales, légales ou réglementaires en matière de conservation des enregistrements avec la gestion des enregistrements

[Gestion des enregistrements Microsoft Purview](/microsoft-365/compliance/manage-data-governance#microsoft-purview-records-management) permet à une organisation de gérer ses obligations légales, de démontrer la conformité aux réglementations et d’accroître l’efficacité avec la disposition régulière d’éléments qui ne sont plus obligatoires pour être conservés, qui n’ont plus de valeur ou qui ne sont plus nécessaires à des fins commerciales. Pour plus d’informations, consultez [En savoir plus sur la gestion des enregistrements](/microsoft-365/compliance/records-management).

### <a name="log-and-search-for-audited-activities-in-sharepoint-and-onedrive-with-audit-premium-or-audit-standard"></a>Journaliser et rechercher des activités auditées dans SharePoint et OneDrive avec Audit (Premium) ou Audit (Standard)

Les [solutions d’audit Microsoft Purview](/microsoft-365/compliance/auditing-solutions-overview) fournissent des solutions intégrées pour aider les organisations à répondre efficacement aux événements de sécurité, aux enquêtes judiciaires, aux enquêtes internes et aux obligations de conformité. Des milliers d’opérations utilisateur et administrateur effectuées dans des dizaines de services et solutions Microsoft 365 sont capturées, enregistrées et conservées dans le journal d’audit unifié de votre organisation. Les enregistrements d'audit de ces événements peuvent être utilisables dans une recherchepar les responsables de la sécurité, les administrateurs informatiques, les équipes chargées de la lutte contre le risque interne et les enquêteurs chargés de la conformité et de la législation au sein de votre organisation. Cette fonctionnalité permet de gagner en visibilité sur les activités effectuées au sein de votre organisation Microsoft 365.

Pour plus d’informations sur les solutions d’audit, consultez [Audit (Premium)](/microsoft-365/compliance/advanced-audit) et [Audit (Standard).](/microsoft-365/compliance/set-up-basic-audit)

### <a name="identify-and-manage-data-for-legal-cases-with-ediscovery-premium-or-ediscovery-standard"></a>Identifier et gérer les données pour les cas juridiques avec eDiscovery (Premium) ou eDiscovery (Standard)

La découverte électronique, ou eDiscovery, est le processus d’identification, de collecte et d’audit de l’information électronique pour des raisons juridiques, réglementaires ou commerciales. Vous pouvez utiliser [Microsoft Purview eDiscovery solutions](/microsoft-365/compliance/ediscovery) pour rechercher des données et du contenu dans les équipes Exchange Online, OneDrive Entreprise, SharePoint Online, Microsoft Teams, Groupes Microsoft 365 et Yammer. Vous pouvez rechercher des boîtes aux lettres et des sites dans la même recherche eDiscovery, puis exporter les résultats de la recherche à des fins d’analyse et de révision.

Pour plus d’informations sur les solutions eDiscovery, consultez [eDiscovery (Premium)](/microsoft-365/compliance/overview-ediscovery-20) et [eDiscovery (Standard).](/microsoft-365/compliance/get-started-core-ediscovery)

## <a name="get-started-with-regulatory-compliance"></a>Prise en main de la conformité réglementaire

Les organisations doivent se conformer à un réseau complexe et en constante évolution de politiques, de normes sectorielles et de réglementations régionales, et également faire face au coût croissant de la non-conformité potentielle. En fait, il y a des centaines de mises à jour par jour de milliers d’organismes de réglementation, ce qui rend difficile la mise à jour avec le paysage de conformité en constante évolution. Le Gestionnaire de conformité Microsoft Purview et une collection détaillée d’offres de conformité peuvent aider votre organisation à gérer ces exigences réglementaires.

### <a name="get-started-with-compliance-manager"></a>Prise en main du Gestionnaire de conformité

Le [Gestionnaire de conformité Microsoft Purview](/microsoft-365/compliance/compliance-manager) est une fonctionnalité du portail de conformité Microsoft Purview qui vous aide à gérer les exigences de conformité de votre organisation avec plus de facilité et de commodité. Le Gestionnaire de conformité peut vous aider tout au long de votre parcours de conformité, de l’inventaire des risques de protection de vos données à la gestion des complexités de l’implémentation de contrôles, la mise à jour des réglementations et des certifications et la création de rapports aux auditeurs.

### <a name="learn-about-microsoft-regulatory-compliance-offerings"></a>En savoir plus sur les offres de conformité réglementaire Microsoft

Microsoft propose un ensemble complet [d’offres de conformité](/compliance/regulatory/offering-home) pour aider votre organisation à se conformer aux exigences nationales, régionales, internationales et spécifiques au secteur qui régissent la collecte et l’utilisation des données.

## <a name="deploy-purview-compliance-solutions"></a>Déployer des solutions de conformité Purview

Les solutions spécifiques à un domaine rassemblent les conseils techniques dont vous avez besoin pour comprendre, planifier et implémenter des solutions de conformité intégrées pour une collaboration de données sécurisée et conforme :

- [Sécuriser les données avec une confiance zéro](/security/zero-trust/deploy/data)
- [Déployer une solution de protection des informations](/microsoft-365/compliance/information-protection-solution)
- [Déployer une solution de gouvernance des données](/microsoft-365/compliance/data-governance-solution)
- [Déployer la protection des informations pour la confidentialité des données](/microsoft-365/solutions/information-protection-deploy)
- [Explorer les illustrations de conformité & la protection des informations](/microsoft-365/solutions/productivity-illustrations)

## <a name="next-steps-for-organizations-new-to-risk-and-compliance-solutions"></a>Étapes suivantes pour les organisations qui découvrent les solutions de risque et de conformité

- [En savoir plus sur la version d’évaluation de la solution Microsoft Purview](/microsoft-365/compliance/compliance-easy-trials)
- [Tâches rapides pour bien démarrer avec la conformité dans Microsoft Purview](/microsoft-365/compliance/compliance-quick-tasks)
