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
description: Découvrez comment étendre les solutions de conformité Microsoft 365 en utilisant des connecteurs de données tiers et des API Microsoft Graph.
ms.openlocfilehash: 8eeb83013ec412ed82973b37c4c10e2250f5eaf8
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285740"
---
# <a name="microsoft-365-compliance-extensibility"></a>Extensibilité de conformité Microsoft 365

Les solutions de conformité Microsoft 365 aident les organisations à évaluer intelligemment leurs risques de conformité, à régir et à protéger les données sensibles, et à répondre efficacement aux exigences réglementaires. La conformité de Microsoft 365 est riche en scénarios d’extensibilité et permet aux organisations d’adapter, d’étendre, d’accélérer et de prendre en charge leurs solutions de conformité.

Il existe deux blocs de construction clés pour l’extensibilité de la conformité :

- **Connecteurs de données**. Utilisez pour importer et archiver des données non Microsoft afin d’appliquer les fonctionnalités de protection et de gouvernance de Microsoft 365 aux données tierces.

- **API**. Permet un accès par programme aux fonctionnalités de conformité de Microsoft 365.

## <a name="data-connectors"></a>Connecteurs de données

Microsoft fournit des connecteurs de données tiers qui peuvent être configurés dans le centre de conformité Microsoft 365. Pour obtenir la liste des connecteurs de données fournis par Microsoft, reportez-vous à la table [connecteurs de données tiers](archiving-third-party-data.md#third-party-data-connectors) . Le tableau des connecteurs de données tiers résume également les solutions de conformité que vous pouvez appliquer aux données tierces après avoir importé et archivé les données dans Microsoft 365, et fournit des liens vers les instructions détaillées pour chaque connecteur.

Pour en savoir plus sur les connecteurs de données Microsoft 365, consultez la rubrique [archivage de données](archiving-third-party-data.md)tierces. Si un type de données tiers n’est pas pris en charge par les connecteurs de données disponibles dans le centre de conformité Microsoft 365, vous pouvez collaborer avec un partenaire qui peut vous fournir un connecteur personnalisé. Pour obtenir la liste des partenaires avec lesquels vous pouvez travailler et le processus pas à pas pour cette méthode, reportez-vous [à travailler avec un partenaire pour archiver des données](work-with-partner-to-archive-third-party-data.md)tierces.

### <a name="prerequisites-for-data-connectors"></a>Conditions préalables pour les connecteurs de données

De nombreux connecteurs de données disponibles dans le centre de conformité Microsoft 365 pour importer et archiver des données tierces exigent que vous prépariez et exécutiez des tâches de configuration dans la source de données tierce. Ces conditions préalables sont documentées en détail pour chaque connecteur de données tiers.

Pour les connecteurs de données dans le centre de conformité Microsoft 365 fourni par l’un des partenaires de Microsoft, votre organisation aura besoin d’une relation commerciale avec le partenaire pour pouvoir déployer un connecteur.

Vous trouverez les conditions requises en matière de licences pour les connecteurs de données tiers dans le document de [comparaison des licences de conformité de Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/downloads/microsoft-365-compliance-licensing-comparison.xlsx) .

## <a name="apis"></a>API

Les API de conformité Microsoft 365 sont disponibles dans le kit de développement logiciel (SDK) Microsoft information protection, l’API Microsoft Graph et l’API d’activité de gestion d’Office 365. Certaines API de conformité font partie d’un nouvel ensemble d’API de sécurité et de conformité qui permettent aux développeurs de clients Microsoft 365, aux fournisseurs de logiciels indépendants, aux intégrateurs de système et aux fournisseurs de services de sécurité gérés de créer des solutions de sécurité et de conformité à haute valeur.

Pour en savoir plus sur l’accès aux API Graph, consultez la rubrique [vue d’ensemble de Microsoft Graph](https://docs.microsoft.com/graph/overview).

### <a name="microsoft-information-protection-mip-sdk"></a>Kit de développement logiciel (SDK) Microsoft information protection (MIP)

Le kit de développement minimal SDK expose les services d’étiquetage et de protection des centres de sécurité et de conformité Microsoft 365 aux applications et services tiers. Les développeurs peuvent utiliser le kit de développement logiciel (SDK) pour créer une prise en charge native pour l’application d’étiquettes et la protection des fichiers. Les développeurs peuvent déterminer les actions à entreprendre lorsque des étiquettes spécifiques sont détectées, ainsi qu’une raison sur les informations chiffrées MIP.

Les cas d’utilisation d’un SDK MIP de haut niveau sont les suivants :

- Application métier qui applique des étiquettes de classification aux fichiers lors de l’exportation.

- Application de conception de CFAO qui fournit une prise en charge native de l’étiquetage MIP.

- Une solution de protection contre la perte de données ou de sécurité du Cloud Access qui peut chiffrer les données avec Azure information protection.

Pour en savoir plus sur le kit de développement logiciel (SDK) MIP, les conditions préalables, les scénarios supplémentaires et les exemples, voir [MIP SDK Overview](https://docs.microsoft.com/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>API Microsoft Graph pour les équipes DLP

Les fonctionnalités de [protection contre la perte de données (DLP)](dlp-microsoft-teams.md) sont largement utilisées dans Microsoft Teams, en particulier lorsque les organisations ont été déplacées vers le travail à distance. Au cours de cette année, nous avons [annoncé la](https://developer.microsoft.com/graph/blogs/announcing-change-notifications-for-microsoft-teams-messages/) préversion publique de l’API de notification de modification Microsoft Graph pour les messages dans Teams. Cette API permet aux développeurs de créer des applications capables d’écouter des messages Microsoft teams en temps quasi-réel, puis d’implémenter des scénarios DLP pour les clients et les partenaires. En outre, l’API patch Microsoft Graph vous permet d’appliquer des actions DLP à des messages Teams.

Ces deux API forment l’API Microsoft Graph pour teams DLP. Vous pouvez commencer en essayant l’exemple d' [application](https://github.com/microsoftgraph/csharp-webhook-with-resource-data). Pour plus d’informations sur les webhooks de messagerie Microsoft Teams, consultez la [documentation](https://docs.microsoft.com/graph/api/subscription-post-subscriptions).

Pour connaître les conditions requises en matière de licences pour teams DLP, consultez la rubrique [Microsoft 365 Licensing Guidance for security & Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-data-loss-prevention-for-teams).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>API Microsoft Graph pour eDiscovery (aperçu)

Grâce à la [découverte électronique avancée](overview-ediscovery-20.md), les organisations peuvent découvrir les données là où elles résident, et gérer plus de flux de travail eDiscovery de bout en bout avec des fonctionnalités intelligentes de formation et d’apprentissage automatique afin de réduire les données à l’ensemble concerné, tout en restant dans la limite de sécurité et de conformité de Microsoft 365.

Les API Graph pour Advanced eDiscovery peuvent être utilisées pour créer et gérer des incidents, examiner des jeux et examiner les requêtes Set de manière évolutive et reproductible. Cela permet aux clients et aux partenaires de créer des applications et des flux de travail pour automatiser les processus courants et répétitifs, tels que la création de cas et la gestion des dépositaires et des suspensions légales.

Le premier ensemble d’API Graph pour eDiscovery est disponible en préversion publique. Nous prévoyons d’ajouter d’autres fonctionnalités à la fin de l’année civile. Pour en savoir plus sur ces API et d’autres mises à jour pour Advanced eDiscovery, consultez ce [blog](https://aka.ms/Ignite2020AeDAA).

Pour connaître les exigences en matière de licences pour Advanced eDiscovery et l’API, voir la section « eDiscovery » dans les [conseils de licence Microsoft 365 pour la sécurité & conformité](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export-preview"></a>Exportation de l’API Microsoft Graph pour Teams (aperçu)

Enterprise Information Archiving (EIA) pour Microsoft teams est un scénario clé pour nos clients, car il leur permet de répondre aux exigences réglementaires. En plus de nos fonctionnalités intégrées pour l’archivage de contenu dans Microsoft Teams, les clients et partenaires peuvent désormais utiliser des API d’exportation teams pour résoudre les scénarios d’intégration et d’application personnalisés. Les API d’exportation des équipes prennent en charge l’exportation en bloc (jusqu’à 200 requêtes par seconde/par application/client) des messages et pièces jointes des messages de teams. Les messages supprimés sont également accessibles par l’API pendant une période de 30 jours maximum après leur suppression. Pour plus d’informations sur l’exportation d’API de teams et sur la façon de les utiliser dans vos applications, consultez [la rubrique exporter du contenu avec les API d’exportation de Microsoft teams](https://docs.microsoft.com/microsoftteams/export-teams-content).

Pour connaître les conditions requises en matière de licence pour l’utilisation des API d’exportation Teams, consultez la rubrique [Microsoft 365 Licensing Guidance for security & Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).
