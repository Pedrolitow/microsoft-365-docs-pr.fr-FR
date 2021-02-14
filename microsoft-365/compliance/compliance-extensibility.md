---
title: Extensibilité de conformité Microsoft 365
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
description: Découvrez comment étendre les solutions de conformité Microsoft 365 à l’aide de connecteurs de données tiers et d’API Microsoft Graph.
ms.openlocfilehash: 8eeb83013ec412ed82973b37c4c10e2250f5eaf8
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285740"
---
# <a name="microsoft-365-compliance-extensibility"></a>Extensibilité de conformité Microsoft 365

Les solutions de conformité Microsoft 365 aident les organisations à évaluer intelligemment leurs risques de conformité, à gérer et protéger les données sensibles et à répondre efficacement aux exigences réglementaires. La conformité Microsoft 365 est riche en scénarios d’extensibilité et permet aux organisations d’adapter, d’étendre, d’intégrer, d’accélérer et de prendre en charge leurs solutions de conformité.

Il existe deux blocs de construction clés pour l’extensibilité de la conformité :

- **Connecteurs de données**. Permet d’importer et d’archiver des données non Microsoft afin de pouvoir appliquer des fonctionnalités de protection et de gouvernance Microsoft 365 à des données tierces.

- **API**. Permet d’accéder par programme aux fonctionnalités de conformité de Microsoft 365.

## <a name="data-connectors"></a>Connecteurs de données

Microsoft fournit des connecteurs de données tiers qui peuvent être configurés dans le Centre de conformité Microsoft 365. Pour obtenir la liste des connecteurs de données fournis par Microsoft, consultez la table [des connecteurs de données tiers.](archiving-third-party-data.md#third-party-data-connectors) Le tableau des connecteurs de données tiers récapitule également les solutions de conformité que vous pouvez appliquer aux données tierces après avoir importé et archivé des données dans Microsoft 365, ainsi que des liens vers les instructions pas à pas pour chaque connecteur.

Pour en savoir plus sur les connecteurs de données Microsoft 365, consultez [l’archivage des données tierces.](archiving-third-party-data.md) Si un type de données tiers n’est pas pris en charge par les connecteurs de données disponibles dans le Centre de conformité Microsoft 365, vous pouvez travailler avec un partenaire qui peut vous fournir un connecteur personnalisé. Pour obtenir la liste des partenaires avec qui vous pouvez travailler et le processus pas à pas pour cette méthode, voir Travailler avec un partenaire pour archiver des données [tierces.](work-with-partner-to-archive-third-party-data.md)

### <a name="prerequisites-for-data-connectors"></a>Conditions préalables pour les connecteurs de données

La plupart des connecteurs de données disponibles dans le Centre de conformité Microsoft 365 pour importer et archiver des données tierces nécessitent que vous prépariez et effectuez des tâches de configuration dans la source de données tierce. Ces conditions préalables sont documentées en détail pour chaque connecteur de données tiers.

Pour les connecteurs de données dans le Centre de conformité Microsoft 365 fourni par l’un des partenaires de Microsoft, votre organisation aura besoin d’une relation professionnelle avec le partenaire avant de pouvoir déployer un connecteur.

Vous trouverez les exigences en matière de licences pour les connecteurs de données tiers dans le document de comparaison des licences de conformité [Microsoft 365.](https://docs.microsoft.com/office365/servicedescriptions/downloads/microsoft-365-compliance-licensing-comparison.xlsx)

## <a name="apis"></a>API

Les API de conformité Microsoft 365 sont disponibles dans le SDK Microsoft Information Protection, l’API Microsoft Graph et l’API Activité de gestion Office 365. Certaines API de conformité font partie d’un nouvel ensemble d’API de sécurité et de conformité qui permettent aux développeurs pour les clients Microsoft 365, les éditeurs de logiciels indépendants, les intégrateurs de système et les fournisseurs de services de sécurité gérés de créer des solutions de sécurité et de conformité de grande valeur.

Pour en savoir plus sur l’accès aux API Graph, voir [Vue d’ensemble de Microsoft Graph.](https://docs.microsoft.com/graph/overview)

### <a name="microsoft-information-protection-mip-sdk"></a>Microsoft Information Protection (MIP) SDK

Le SDK MIP expose les services d’étiquetage et de protection des centres de sécurité et de conformité Microsoft 365 aux applications et services tiers. Les développeurs peuvent utiliser le SDK pour créer une prise en charge native pour l’application d’étiquettes et de protection aux fichiers. Les développeurs peuvent déterminer les actions à prendre lorsque des étiquettes spécifiques sont détectées et la raison sur les informations chiffrées par MIP.

Les cas d’utilisation du SDK MIP de haut niveau sont les suivants :

- Application métier qui applique des étiquettes de classification aux fichiers à l’exportation.

- Application de conception CAD/CAM qui fournit une prise en charge native de l’étiquetage MIP.

- Un courtier de sécurité d’accès au cloud ou une solution de protection contre la perte de données qui peut chiffrer des données avec Azure Information Protection.

Pour en savoir plus sur le SDK MIP, les conditions préalables, les scénarios supplémentaires et les exemples, voir vue d’ensemble du [SDK MIP.](https://docs.microsoft.com/information-protection/develop/overview)

### <a name="microsoft-graph-api-for-teams-dlp"></a>API Microsoft Graph pour teams DLP

Les fonctionnalités de protection contre la perte de données [(DLP)](dlp-microsoft-teams.md) sont largement utilisées dans Microsoft Teams, en particulier lorsque les organisations ont été décalées vers le travail à distance. Plus tôt cette année, nous avons annoncé la [prévisualisation publique](https://developer.microsoft.com/graph/blogs/announcing-change-notifications-for-microsoft-teams-messages/) de l’API de notification de modification de Microsoft Graph pour les messages dans Teams. Cette API permet aux développeurs de créer des applications qui peuvent écouter les messages De Microsoft Teams en temps quasi réel, puis d’implémenter des scénarios DLP pour les clients et les partenaires. En outre, l’API de correctif Microsoft Graph vous permet d’appliquer des actions DLP aux messages Teams.

Ces deux API forment l’API Microsoft Graph pour teams DLP. Vous pouvez commencer en essayant [l’exemple d’application.](https://github.com/microsoftgraph/csharp-webhook-with-resource-data) Pour plus d’informations sur les webhooks de messagerie Microsoft Teams, consultez la [documentation.](https://docs.microsoft.com/graph/api/subscription-post-subscriptions)

Pour les exigences de licence pour teams DLP, consultez les conseils de gestion des licences [Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-data-loss-prevention-for-teams)pour la sécurité et & conformité.

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>API Microsoft Graph pour eDiscovery (aperçu)

Grâce à [Advanced eDiscovery,](overview-ediscovery-20.md)les organisations peuvent découvrir les données là où elles se trouve et gérer davantage de flux de travail eDiscovery de bout en bout avec des fonctionnalités intelligentes d’apprentissage automatique et d’analyse pour réduire les données à l’ensemble approprié, tout en respectant les limites de sécurité et de conformité de Microsoft 365.

Les API Graph pour Advanced eDiscovery peuvent être utilisées pour créer et gérer des cas, des ensembles de révision et des requêtes de jeu à réviser de manière évolutive et extensible. Cela permet aux clients et aux partenaires de créer des applications et des flux de travail pour automatiser des processus courants et répétitifs tels que la création de cas et la gestion des dépositaires et des conservations légales.

Le premier ensemble d’API Graph pour eDiscovery est disponible en prévisualisation publique. Nous prévoyons d’ajouter des fonctionnalités d’ici la fin de l’année civile. Pour en savoir plus sur ces API et d’autres mises à jour pour Advanced eDiscovery, consultez ce [blog.](https://aka.ms/Ignite2020AeDAA)

Pour les exigences de licence pour Advanced eDiscovery et l’API, consultez la section « eDiscovery » dans les conseils de licence [Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery)pour la conformité & sécurité.

### <a name="microsoft-graph-api-for-teams-export-preview"></a>API Microsoft Graph pour l’exportation teams (prévisualisation)

L’archivage des informations d’entreprise (EIA) pour Microsoft Teams est un scénario clé pour nos clients, car il leur permet de résoudre les exigences réglementaires. En plus de nos fonctionnalités intégrées d’archivage de contenu dans Microsoft Teams, les clients et les partenaires peuvent désormais utiliser les API d’exportation Teams pour résoudre des scénarios d’application et d’intégration personnalisés. Les API d’exportation Teams prendre en charge l’exportation en bloc (jusqu’à 200 demandes par seconde/par application/par client) de messages teams et de pièces jointes de message. Les messages supprimés sont également accessibles par l’API pendant 30 jours après leur suppression. Pour plus d’informations sur ces API d’exportation Teams et sur leur utilisation dans vos applications, voir Exporter du contenu avec les API [d’exportation De Microsoft Teams.](https://docs.microsoft.com/microsoftteams/export-teams-content)

Pour les conditions de licence requises pour l’utilisation des API d’exportation Teams, consultez les conseils de licence [Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)pour la sécurité et & conformité.
