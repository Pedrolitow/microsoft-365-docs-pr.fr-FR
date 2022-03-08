---
title: extensibilité Microsoft 365 conformité des données
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
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
ms.openlocfilehash: 0632de40141b86e6dfdebf3f5c3a97ca50219357
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330536"
---
# <a name="microsoft-365-compliance-and-microsoft-priva-extensibility"></a>Microsoft 365 conformité et extensibilité De Microsoft Priva

Microsoft 365 solutions de conformité permettent aux organisations d’évaluer intelligemment leurs risques de conformité, de régir et de protéger les données sensibles et de répondre efficacement aux exigences réglementaires. Microsoft 365 conformité est riche en scénarios d’extensibilité et permet aux organisations d’adapter, d’étendre, d’intégrer, d’accélérer et de prendre en charge leurs solutions de conformité.

Il existe deux blocs de construction clés pour l’extensibilité de la conformité :

- **Connecteurs de données**. Permet d’importer et d’archiver des données non Microsoft afin que vous Microsoft 365 fonctionnalités de protection et de gouvernance aux données tierces.

- **API**. Permet d’accéder par programme aux fonctionnalités Microsoft 365 conformité.

## <a name="data-connectors"></a>Connecteurs de données

Microsoft fournit des connecteurs de données tiers qui peuvent être configurés dans le Centre de conformité Microsoft 365. Pour obtenir la liste des connecteurs de données fournis par Microsoft, consultez la table [des connecteurs de données tiers](archiving-third-party-data.md#third-party-data-connectors) . Le tableau des connecteurs de données tiers récapitule également les solutions de conformité que vous pouvez appliquer aux données tierces après avoir importé et archivé des données dans Microsoft 365, ainsi que des liens vers les instructions pas à pas pour chaque connecteur.

Pour en savoir plus sur Microsoft 365 connecteurs de données, voir Données tierces [d’archivage](archiving-third-party-data.md). Si un type de données tiers n’est pas pris en charge par les connecteurs de données disponibles dans le Centre de conformité Microsoft 365, vous pouvez travailler avec un partenaire qui peut vous fournir un connecteur personnalisé. Pour obtenir la liste des partenaires avec qui vous pouvez travailler et le processus pas à pas pour cette méthode, voir Travailler avec un partenaire pour [archiver des données tierces](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>Conditions préalables pour les connecteurs de données

La plupart des connecteurs de données disponibles dans le Centre de conformité Microsoft 365 pour importer et archiver des données tierces nécessitent que vous prépariez et effectuez des tâches de configuration dans la source de données tierce. Ces conditions préalables sont documentées en détail pour chaque connecteur de données tiers.

Pour les connecteurs de données dans le Centre de conformité Microsoft 365 fourni par l’un des partenaires de Microsoft, votre organisation aura besoin d’une relation professionnelle avec le partenaire avant de pouvoir déployer un connecteur.

Pour obtenir des instructions et des exigences pour les connecteurs de données tiers, consultez la section « Connecteurs de données » dans Microsoft 365 recommandations pour la conformité des & de sécurité [- Descriptions de service | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>API

Microsoft 365 conformité et les API Microsoft Priva sont disponibles dans le SDK Protection des données Microsoft, l’API Microsoft Graph et l’API activité de gestion Office 365 microsoft. Certaines API de conformité font partie d’un nouvel ensemble d’API de sécurité et de conformité qui permettent aux développeurs pour les clients Microsoft 365, les éditeurs de logiciels indépendants, les intégrateurs de système et les fournisseurs de services de sécurité gérés de créer des solutions de sécurité et de conformité à valeur élevée.

Pour en savoir plus sur l’accès Graph API, voir [Vue d’ensemble de Microsoft Graph](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>API microsoft Graph pour les demandes de droits d’objet

Conformément à certaines réglementations en matière de confidentialité dans le monde entier, les individus peuvent effectuer des demandes de révision ou de gestion des données personnelles collectées par les entreprises. Ces demandes sont appelées demandes de droits d’objet *au sein de* la solution Demandes des droits d’objet de Microsoft Priva. Les demandes de droits d’objet sont également appelées demandes d’accès des personnes à l’aide de *données (* DSR) ou DSAR ( *Data Subject Subject Access Requests* ). Les API Graph Microsoft pour les demandes de droits d’objet permettent aux développeurs d’intégrer Microsoft 365 des demandes de droits d’objet liées à l’objet à l’écosystème de confidentialité plus large. Cette extensibilité basée sur l’API permet aux organisations de répondre aux demandes de droits de l’objet de manière unifiée sur l’ensemble de leur patrimoine de données couvrant les environnements Microsoft et non-Microsoft. Cette fonctionnalité facilite également l’automatisation à grande échelle et aide les organisations à respecter les réglementations du secteur plus efficacement sans retenter sur des processus manuels.

Pour en savoir plus, [consultez les API microsoft Graph pour obtenir des droits d’objet](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview).

### <a name="microsoft-information-protection-mip-sdk"></a>SDK Protection des données Microsoft (MIP)

Le SDK MIP expose les services d’étiquetage et de protection à partir de Microsoft 365 de sécurité et de conformité aux applications et services tiers. Les développeurs peuvent utiliser le SDK pour créer une prise en charge native pour l’application d’étiquettes et de protection aux fichiers. Les développeurs peuvent déterminer les actions à prendre lorsque des étiquettes spécifiques sont détectées et la raison sur les informations chiffrées par MIP.

Les cas d’utilisation du SDK MIP de haut niveau sont les suivants :

- Application métier qui applique des étiquettes de classification aux fichiers à l’exportation.

- Application de conception CAD/CAM qui fournit une prise en charge native de l’étiquetage MIP.

- Un courtier de sécurité d’accès au cloud ou une solution de protection contre la perte de données qui peut chiffrer des données avec Azure Information Protection.

Pour en savoir plus sur le SDK MIP, les conditions préalables, les scénarios supplémentaires et les exemples, voir Vue d’ensemble du [SDK MIP](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>API Graph Microsoft pour Teams DLP

[Les fonctionnalités de protection](dlp-microsoft-teams.md) contre la perte de données (DLP) sont largement utilisées dans Microsoft Teams en particulier lorsque les organisations ont été décalées vers le travail à distance. Récemment, [nous avons annoncé la disponibilité](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/) générale de l’API de notification de modification Graph Microsoft pour les messages Teams. Cette API permet aux développeurs de créer des applications qui peuvent écouter Microsoft Teams messages en temps quasi réel, puis d’implémenter des scénarios DLP pour les clients et les partenaires. En outre, Microsoft Graph API patch vous permet d’appliquer des actions DLP à Teams messages.

Ces deux API forment l’API microsoft Graph pour Teams DLP. Vous pouvez commencer en essayant [l’exemple d’application](https://github.com/microsoftgraph/aspnetcore-webhooks-sample). Pour plus d’informations sur Microsoft Teams webhooks de messagerie, consultez la [documentation](/graph/api/subscription-post-subscriptions).

Pour les exigences en matière de licences Teams DLP, voir Microsoft 365 [licences pour la sécurité et & conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>API Graph Microsoft pour eDiscovery (prévisualisation)

Avec [Advanced eDiscovery](overview-ediscovery-20.md), les organisations peuvent découvrir les données là où elles se trouve et gérer davantage de flux de travail eDiscovery de bout en bout avec des fonctionnalités intelligentes d’apprentissage automatique et d’analyse afin de réduire les données à l’ensemble approprié, tout en respectant les limites de sécurité et de conformité Microsoft 365.

Graph API de Advanced eDiscovery peuvent être utilisées pour créer et gérer des cas, des ensembles de révision et des requêtes de jeu à réviser de manière évolutive et extensible. Cela permet aux clients et aux partenaires de créer des applications et des flux de travail pour automatiser les processus courants et répétitifs tels que la création de cas et la gestion des dépositaires et des conservations légales.

Le premier ensemble d’API Graph pour eDiscovery sont disponibles en prévisualisation publique. Nous prévoyons d’ajouter des fonctionnalités d’ici la fin de l’année civile. Pour en savoir plus sur ces API et d’autres mises à jour pour Advanced eDiscovery, consultez ce [blog](https://aka.ms/Ignite2020AeDAA).

Pour les conditions de licence requises pour Advanced eDiscovery et l’API, consultez la section « eDiscovery » dans les conseils de licence Microsoft 365 pour la conformité & [sécurité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export"></a>API microsoft Graph pour l Teams exporter

Enterprise’archivage des informations (EIA) pour Microsoft Teams est un scénario clé pour nos clients, car il leur permet de résoudre les exigences réglementaires. Outre nos fonctionnalités intégrées d’archivage de contenu dans Microsoft Teams, les clients et les partenaires peuvent désormais utiliser les API d’exportation Teams pour résoudre les scénarios d’application et d’intégration personnalisés. Les API Teams exporter les api de prise en charge de l’exportation en bloc (jusqu’à 200 demandes par seconde/par application/par client) de Teams messages et de pièces jointes de message. Les messages supprimés sont également accessibles par l’API pendant 30 jours après leur suppression. Pour plus d’informations sur ces Teams des API d’exportation et sur leur utilisation dans vos applications, voir Exporter du contenu avec les [API d Microsoft Teams exporter](/microsoftteams/export-teams-content).

Pour les conditions de licence requises pour l’utilisation des API d Teams exportation d’Microsoft 365, voir les recommandations en matière de licences pour la sécurité [& conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>API Microsoft Graph Connector (prévisualisation)

Avec [les connecteurs Graph Microsoft](/microsoftsearch/connectors-overview), les organisations peuvent indexer des données tierces afin qu’elles apparaissent dans Recherche Microsoft résultats. Cette fonctionnalité élargit les types de sources de contenu disponibles dans vos applications de productivité Microsoft 365 et dans l’écosystème Microsoft plus vaste. Les données tierces peuvent être hébergées en local ou dans des clouds publics ou privés. À partir Advanced eDiscovery, nous activons la prévisualisation pour développeurs de la valeur de conformité intégrée de Microsoft 365 applications connectées. Cela permet la conformité des applications intégrées à l’écosystème Microsoft 365 pour permettre aux utilisateurs d’obtenir des expériences de conformité transparentes. Pour en savoir plus sur l’intégration des API Microsoft Graph Connector dans l’affichage de vos applications, voir Créer, mettre à jour et supprimer des [connexions](/graph/connecting-external-content-connectors-api-overview) dans le microsoft Graph.
