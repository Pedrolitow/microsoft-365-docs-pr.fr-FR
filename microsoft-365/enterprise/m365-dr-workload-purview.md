---
title: Data Residency pour Microsoft Purview
description: Data Residency pour Microsoft Purview
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.service: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: ''
ms.reviewer: dmwmsft
ms.custom:
- it-pro
ms.collection:
- M365-subscription-management
ms.openlocfilehash: c9eb616409de83bc08ca8140a41cd90ad10ba2dc
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805436"
---
# <a name="data-residency-for-microsoft-purview"></a>Data Residency pour Microsoft Purview

Les engagements de résidence des données pour l’ensemble de services Purview, comme décrit ci-dessous, sont disponibles avec le module complémentaire Advanced Data Residency.
Les conditions requises pour les engagements connexes pour les services décrits ci-dessous sont les suivantes :

1. _Le client_ a un pays d’inscription inclus dans _Région locale Geography_ ou _Expanded Local Region Geography_.
1. _Le locataire_ dispose d’un abonnement advanced Data Residency valide pour tous les utilisateurs du _locataire_.
1. Les données client du service Purview sont approvisionnées dans _Région locale Geography_ ou _Expanded Local Region Geography_.

## <a name="migration"></a>Migration

Les données client prenant en charge les services Purview sont étroitement alignées sur les services Exchange Online et SharePoint Online, et la majeure partie des données migrées, si nécessaire pour respecter les engagements de résidence des données pour les services Purview, sera gérée par ces services. Dans les cas où les données client prises en charge sont conservées dans un service Azure, par exemple, la migration de ces données est liée à la migration des données Exchange Online/SharePoint Online sous-jacentes.

## <a name="how-can-i-determine-customer-data-location"></a>Comment puis-je déterminer l’emplacement des données client ?

Nous sommes en train de mettre à jour l’emplacement réel des données dans _le Centre Administration client_.  Une fois cette modification terminée, vous pouvez voir l’emplacement réel des données, pour les données validées, en accédant à Administration->Paramètres->Paramètres de l’organisation->Profil de l’organisation->Emplacement des données.  Tant que cette modification n’est pas visible, vous pouvez afficher les informations d’emplacement des données Exchange Online afin de comprendre où vos données validées sont stockées pour ce service.

### <a name="purview-audit-standard"></a>Audit Purview (Standard)

#### <a name="summary"></a>Résumé

Documentation du service : [Solutions d’audit Microsoft Purview](/microsoft-365/compliance/auditing-solutions-overview)

Résumé des fonctionnalités : Microsoft Purview Audit (Standard) vous permet d’enregistrer et de rechercher vos données pour les activités d’audit et d’alimenter vos efforts d’investigation, d’informatique, de conformité et d’enquêtes juridiques.

#### <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

Engagement:

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#purview-audit-standard) pour connaître l’engagement spécifique des données client au repos pour l’audit Purview (Standard).

### <a name="purview-audit-premium"></a>Audit Purview (Premium)

#### <a name="summary"></a>Résumé

Documentation du service : [Solutions d’audit Microsoft Purview](/microsoft-365/compliance/auditing-solutions-overview)

Résumé des fonctionnalités : Microsoft Purview Audit (Premium) s’appuie sur les fonctionnalités de l’audit (Standard) en fournissant des stratégies de rétention des journaux d’audit, une conservation plus longue des enregistrements d’audit, une capacité d’identification des événements essentiels à grande valeur et un accès plus large à la bande passante à l’API d’activité de gestion Office 365.

#### <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

Engagement:

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#purview-audit-premium) pour connaître l’engagement spécifique des données client au repos pour Purview Audit (Premium).

### <a name="data-lifecycle-management---data-retention"></a>Gestion du cycle de vie des données - Conservation des données

#### <a name="summary"></a>Résumé

Adr s’applique aux services suivants dans la gestion du cycle de vie des données Purview, Conservation des données :

- Étiquettes de rétention manuelles
- Stratégies de rétention de base à l’échelle de l’organisation ou de l’emplacement
- Stratégies de rétention automatique basées sur des règles
- Rétention basée sur Machine Learning
- Stratégies de rétention des messages Teams

Documentation du service :  [En savoir plus sur les stratégies de rétention & étiquettes](/microsoft-365/compliance/retention)

Pour plus d’informations sur le fonctionnement des paramètres de rétention en fonction des différentes charges de travail, consultez les articles suivants :

- [Découvrir la rétention pour Exchange](/microsoft-365/compliance/retention-policies-exchange)
- [En savoir plus sur la rétention dans SharePoint et OneDrive](/microsoft-365/compliance/retention-policies-sharepoint)
- [En savoir plus sur la rétention dans Microsoft Teams](/microsoft-365/compliance/retention-policies-teams)

Résumé des fonctionnalités : vous permet de conserver ou de supprimer du contenu avec la gestion des stratégies pour les e-mails, les documents et Teams.

#### <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

Engagement:

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#data-lifecycle-management---data-retention) pour connaître l’engagement spécifique données client au repos pour la gestion du cycle de vie des données - Conservation des données.

### <a name="data-lifecycle-management---records-management"></a>Gestion du cycle de vie des données - Gestion des enregistrements

#### <a name="summary"></a>Résumé

Documentation du service : [en savoir plus sur Gestion des enregistrements Microsoft Purview](/microsoft-365/compliance/records-management)

Résumé des fonctionnalités : les organisations de tous types ont besoin d’une solution de gestion des enregistrements pour gérer les enregistrements réglementaires, juridiques et critiques pour l’entreprise dans leurs données d’entreprise. La gestion des enregistrements pour Microsoft Purview permet à une organisation de gérer ses obligations légales, offre la possibilité de démontrer la conformité aux réglementations et augmente l’efficacité avec la destruction régulière d’éléments qui ne sont plus tenus d’être conservés, qui n’ont plus de valeur ou qui ne sont plus nécessaires à des fins professionnelles.

#### <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

Engagement:

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#data-lifecycle-management---records-management) pour connaître l’engagement spécifique données client au repos pour la gestion du cycle de vie des données - Gestion des enregistrements.

### <a name="information-protection---sensitivity-labels"></a>Information Protection - Étiquettes de confidentialité

#### <a name="summary"></a>Résumé

Adr s’applique aux services suivants dans purview Information Protection, étiquettes de confidentialité :

- Étiquetage manuel, par défaut et obligatoire de confidentialité dans Office 365
- Étiquetage automatique de confidentialité dans les applications Office 365
- Étiquettes de confidentialité automatiques dans Exchange, SharePoint et OneDrive
- Étiquettes de confidentialité basées sur la classification avancée
- Étiquetage de confidentialité pour les conteneurs dans Office 365

Documentation du service :

- [En savoir plus sur les étiquettes de niveau de confidentialité](/microsoft-365/compliance/sensitivity-labels)
- [Prise en main de l’explorateur d’activités](/microsoft-365/compliance/data-classification-activity-explorer)

Résumé des fonctionnalités : les étiquettes de confidentialité de Protection des données Microsoft Purview vous permettent de classifier et de protéger les données de votre organisation, tout en vous assurant que la productivité des utilisateurs et leur capacité à collaborer ne sont pas entravées.

#### <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

Engagement:

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#information-protection---sensitivity-labels) pour connaître l’engagement spécifique aux données au repos des Information Protection - Étiquettes de confidentialité.

### <a name="information-protection---data-loss-prevention-dlp"></a>Information Protection - Protection contre la perte de données (DLP)

#### <a name="summary"></a>Résumé

La règle ADR s’applique aux services suivants dans Purview Information Protection, Protection contre la perte de données (DLP) :

- Office 365 protection contre la perte de données (DLP) pour les e-mails et les fichiers
- Conversation DLP pour Teams

Documentation du service : [En savoir plus sur la protection contre la perte de données](/microsoft-365/compliance/dlp-learn-about-dlp)

Résumé de la fonctionnalité :

Les organisations ont des informations sensibles sous leur contrôle, telles que des données financières, des données propriétaires, des numéros de carte de crédit, des dossiers médicaux ou des numéros de sécurité sociale. Pour protéger ces données sensibles et réduire les risques, ils ont besoin d’un moyen d’empêcher leurs utilisateurs de les partager de manière inappropriée avec des personnes qui ne devraient pas les avoir. Cette pratique est appelée protection contre la perte de données (DLP).

Dans Microsoft Purview, vous implémentez la protection contre la perte de données en définissant et en appliquant des stratégies DLP. Avec une stratégie DLP, vous pouvez identifier, surveiller et protéger automatiquement les éléments sensibles dans :

- Services Microsoft 365 tels que Teams, Exchange, SharePoint et OneDrive
- Applications Office telles que Word, Excel et PowerPoint
- points de terminaison Windows 10, Windows 11 et macOS (Catalina 10.15 et versions ultérieures)
- applications cloud non-Microsoft
- partages de fichiers locaux et SharePoint local.

DLP détecte les éléments sensibles à l’aide d’une analyse de contenu approfondie, et pas seulement par une simple analyse de texte. Le contenu est analysé pour rechercher les correspondances de données primaires aux mots clés, par l’évaluation des expressions régulières, par la validation de fonction interne et par les correspondances de données secondaires qui se trouvent à proximité de la correspondance de données primaires. En outre, DLP utilise également des algorithmes d’apprentissage automatique et d’autres méthodes pour détecter le contenu qui correspond à vos stratégies DLP.

#### <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

Engagement:

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#information-protection---data-loss-prevention-dlp) pour connaître l’engagement spécifique des données client au repos pour Information Protection - Protection contre la perte de données (DLP).

### <a name="information-protection---office-message-encryption"></a>Information Protection - Chiffrement des messages Office

#### <a name="summary"></a>Résumé

Adr s’applique aux services suivants dans Purview Information Protection, Chiffrement des messages Office :

- Chiffrement de messages Office de base
- Chiffrement avancé des messages Office

Documentation du service : [chiffrement des messages Office 365 - Microsoft Purview](/microsoft-365/compliance/ome)

Résumé de la fonctionnalité : avec Office 365 Chiffrement des messages, votre organisation peut envoyer et recevoir des messages électroniques chiffrés entre des personnes internes et externes à votre organisation. Chiffrement de messages Office 365 fonctionne avec Outlook.com, Yahoo !, Gmail et d’autres services de messagerie. Email chiffrement des messages permet de s’assurer que seuls les destinataires prévus peuvent afficher le contenu du message.

#### <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

Engagement:

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#information-protection---office-message-encryption) pour connaître l’engagement spécifique des données client au repos pour Information Protection - Chiffrement des messages Office.

### <a name="insider-risk-management---information-barriers"></a>Gestion des risques internes - Obstacles à l’information

#### <a name="summary"></a>Résumé

Documentation du service : [En savoir plus sur les obstacles à l’information](/microsoft-365/compliance/information-barriers)

Résumé des fonctionnalités : Microsoft Purview Information Barriers (IB) est une solution de conformité qui vous permet de restreindre la communication bidirectionnelle et la collaboration entre les groupes et les utilisateurs dans Microsoft Teams, SharePoint et OneDrive. Souvent utilisée dans des secteurs hautement réglementés, l’IB peut aider à éviter les conflits d’intérêts et à protéger les informations internes entre les utilisateurs et les secteurs organisationnels.

#### <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

Engagement:

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#insider-risk-management---information-barriers) pour connaître l’engagement spécifique des données client au repos pour la gestion des risques internes - Obstacles à l’information.
