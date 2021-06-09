---
title: Microsoft 365 conformité des données
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment étendre les solutions Microsoft 365 conformité à l’aide de connecteurs de données tiers et d’API Microsoft Graph.
ms.openlocfilehash: 1fed5ac72c7dbfa4b1be370ec03678e1beecdcd2
ms.sourcegitcommit: 07e536f1a6e335f114da55048844e4a866fe731b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52651055"
---
# <a name="microsoft-365-compliance-extensibility"></a>Microsoft 365 conformité des données

Microsoft 365 solutions de conformité permettent aux organisations d’évaluer intelligemment leurs risques de conformité, de régir et de protéger les données sensibles et de répondre efficacement aux exigences réglementaires. Microsoft 365 conformité est riche en scénarios d’extensibilité et permet aux organisations d’adapter, d’étendre, d’intégrer, d’accélérer et de prendre en charge leurs solutions de conformité.

Il existe deux blocs de construction clés pour l’extensibilité de la conformité :

- **Connecteurs de données**. Permet d’importer et d’archiver des données non Microsoft afin que vous Microsoft 365 fonctionnalités de protection et de gouvernance aux données tierces.

- **API**. Permet d’accéder par programme aux fonctionnalités Microsoft 365 conformité.

## <a name="data-connectors"></a>Connecteurs de données

Microsoft fournit des connecteurs de données tiers qui peuvent être configurés dans le centre Microsoft 365 conformité. Pour obtenir la liste des connecteurs de données fournis par Microsoft, consultez la table [des connecteurs de données tiers.](archiving-third-party-data.md#third-party-data-connectors) Le tableau des connecteurs de données tiers récapitule également les solutions de conformité que vous pouvez appliquer aux données tierces après avoir importé et archivé des données dans Microsoft 365, ainsi que des liens vers les instructions pas à pas pour chaque connecteur.

Pour en savoir plus sur Microsoft 365 connecteurs de données, consultez [l’archivage de données tierces.](archiving-third-party-data.md) Si un type de données tiers n’est pas pris en charge par les connecteurs de données disponibles dans le Centre de conformité Microsoft 365, vous pouvez travailler avec un partenaire qui peut vous fournir un connecteur personnalisé. Pour obtenir la liste des partenaires avec qui vous pouvez travailler et le processus pas à pas pour cette méthode, voir Travailler avec un partenaire pour archiver des données [tierces.](work-with-partner-to-archive-third-party-data.md)

### <a name="prerequisites-for-data-connectors"></a>Conditions préalables pour les connecteurs de données

La plupart des connecteurs de données disponibles dans le centre de conformité Microsoft 365 pour importer et archiver des données tierces nécessitent que vous prépariez et effectuez des tâches de configuration dans la source de données tierce. Ces conditions préalables sont documentées en détail pour chaque connecteur de données tiers.

Pour les connecteurs de données dans le centre de conformité Microsoft 365 fourni par l’un des partenaires de Microsoft, votre organisation aura besoin d’une relation professionnelle avec le partenaire avant de pouvoir déployer un connecteur.

Vous trouverez les exigences en matière de licences pour les connecteurs de données tiers dans le document de comparaison des licences [Microsoft 365 conformité.](/office365/servicedescriptions/downloads/microsoft-365-compliance-licensing-comparison.xlsx)

## <a name="apis"></a>API

Microsoft 365 api de conformité sont disponibles dans le SDK Microsoft Information Protection, l’API Microsoft Graph et l’API activité Office 365 gestion des données. Certaines API de conformité font partie d’un nouvel ensemble d’API de sécurité et de conformité qui permettent aux développeurs pour les clients Microsoft 365, les éditeurs de logiciels indépendants, les intégrateurs de système et les fournisseurs de services de sécurité gérés de créer des solutions de sécurité et de conformité à valeur élevée.

Pour en savoir plus sur l’accès Graph API, voir [Vue d’ensemble](/graph/overview)de Microsoft Graph .

### <a name="microsoft-information-protection-mip-sdk"></a>Microsoft Information Protection (MIP) SDK

Le SDK MIP expose les services d’étiquetage et de protection des centres de sécurité et de conformité Microsoft 365 aux applications et services tiers. Les développeurs peuvent utiliser le SDK pour créer une prise en charge native pour l’application d’étiquettes et de protection aux fichiers. Les développeurs peuvent déterminer les actions à prendre lorsque des étiquettes spécifiques sont détectées et la raison sur les informations chiffrées par MIP.

Les cas d’utilisation du SDK MIP de haut niveau sont les suivants :

- Application métier qui applique des étiquettes de classification aux fichiers à l’exportation.

- Application de conception CAD/CAM qui fournit une prise en charge native de l’étiquetage MIP.

- Un courtier de sécurité d’accès au cloud ou une solution de protection contre la perte de données qui peut chiffrer des données avec Azure Information Protection.

Pour en savoir plus sur le SDK MIP, les conditions préalables, les scénarios supplémentaires et les exemples, voir vue d’ensemble du [SDK MIP.](/information-protection/develop/overview)

### <a name="microsoft-graph-api-for-teams-dlp"></a>API Graph Microsoft pour Teams DLP

Les fonctionnalités de protection contre la perte de données [(DLP)](dlp-microsoft-teams.md) sont largement utilisées dans Microsoft Teams en particulier lorsque les organisations ont été décalées vers le travail à distance. Plus tôt cette année, nous avons annoncé la prévisualisation [publique](https://developer.microsoft.com/graph/blogs/announcing-change-notifications-for-microsoft-teams-messages/) de l’API de notification de modification Graph Microsoft pour les messages Teams. Cette API permet aux développeurs de créer des applications qui peuvent écouter Microsoft Teams messages en temps quasi réel, puis d’implémenter des scénarios DLP pour les clients et les partenaires. En outre, Microsoft Graph API patch vous permet d’appliquer des actions DLP à Teams messages.

Ces deux API forment l’API microsoft Graph pour Teams DLP. Vous pouvez commencer en essayant [l’exemple d’application.](https://github.com/microsoftgraph/csharp-webhook-with-resource-data) Pour plus d’informations sur Microsoft Teams webhooks de messagerie, consultez la [documentation.](/graph/api/subscription-post-subscriptions)

Pour les conditions de licence requises pour Teams DLP, voir Microsoft 365 recommandations en matière de licences pour la sécurité [& conformité.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-data-loss-prevention-for-teams)

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>API microsoft Graph pour eDiscovery (prévisualisation)

Avec [Advanced eDiscovery,](overview-ediscovery-20.md)les organisations peuvent découvrir les données là où elles se trouve et gérer davantage de flux de travail eDiscovery de bout en bout avec des fonctionnalités intelligentes d’apprentissage automatique et d’analyse pour réduire les données à l’ensemble approprié, tout en respectant les limites de sécurité et de conformité Microsoft 365.

Graph Les API pour Advanced eDiscovery peuvent être utilisées pour créer et gérer des cas, des ensembles de révision et des requêtes de jeu à réviser de manière évolutive et extensible. Cela permet aux clients et aux partenaires de créer des applications et des flux de travail pour automatiser les processus courants et répétitifs tels que la création de cas et la gestion des dépositaires et des conservations légales.

Le premier ensemble d’API Graph pour eDiscovery sont disponibles en prévisualisation publique. Nous prévoyons d’ajouter des fonctionnalités d’ici la fin de l’année civile. Pour en savoir plus sur ces API et d’autres mises à jour pour Advanced eDiscovery, consultez ce [blog.](https://aka.ms/Ignite2020AeDAA)

Pour les conditions de licence requises pour Advanced eDiscovery et l’API, consultez la section « eDiscovery » dans les conseils de licence Microsoft 365 pour la conformité & [sécurité.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery)

### <a name="microsoft-graph-api-for-teams-export-preview"></a>API microsoft Graph pour l Teams exporter (prévisualisation)

Enterprise L’archivage des informations (EIA) pour Microsoft Teams est un scénario clé pour nos clients, car il leur permet de résoudre les exigences réglementaires. Outre nos fonctionnalités intégrées d’archivage de contenu dans Microsoft Teams, les clients et les partenaires peuvent désormais utiliser les API d’exportation Teams pour résoudre les scénarios d’application et d’intégration personnalisés. Le Teams’API Export permet l’exportation en bloc (jusqu’à 200 demandes par seconde/par application/par client) de messages Teams et de pièces jointes de message. Les messages supprimés sont également accessibles par l’API pendant 30 jours après leur suppression. Pour plus d’informations sur ces Teams exporter des API et sur la façon de les utiliser dans vos applications, voir Exporter du contenu avec Microsoft Teams [exporter des API.](/microsoftteams/export-teams-content)

Pour les conditions de licence requises pour l’utilisation des API d’exportation Teams, voir Microsoft 365 recommandations en matière de licences pour la sécurité [& conformité.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

### <a name="microsoft-graph-connector-apis-preview"></a>API Microsoft Graph Connector (prévisualisation)

Avec [les connecteurs Graph Microsoft,](/microsoftsearch/connectors-overview)les organisations peuvent indexer des données tierces afin qu’elles apparaissent dans les résultats de recherche Microsoft. Cette fonctionnalité élargit les types de sources de contenu disponibles dans vos applications de productivité Microsoft 365 et dans l’écosystème Microsoft plus vaste. Les données tierces peuvent être hébergées en local ou dans des clouds publics ou privés. À partir Advanced eDiscovery, nous activons la prévisualisation pour développeurs de la valeur de conformité intégrée de Microsoft 365 applications connectées. Cela permet la conformité des applications intégrées à l’écosystème Microsoft 365 pour permettre aux utilisateurs d’obtenir des expériences de conformité transparentes. Pour en savoir plus sur l’intégration des API Microsoft Graph Connector dans l’affichage de vos applications, voir Créer, mettre à jour et supprimer des [connexions](/graph/search-index-manage-connections)dans microsoft Graph .

