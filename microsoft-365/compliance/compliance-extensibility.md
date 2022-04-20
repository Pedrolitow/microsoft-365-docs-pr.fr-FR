---
title: Extensibilité Microsoft Purview
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
description: Découvrez comment étendre les solutions Microsoft Purview à l’aide de connecteurs de données tiers et d’API Microsoft Graph.
ms.openlocfilehash: e61cd2dfa8121a0925cc89fd5373569d9697936a
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64942752"
---
# <a name="microsoft-purview-and-microsoft-priva-extensibility"></a>Extensibilité de Microsoft Purview et Microsoft Priva

Les solutions Microsoft Purview aident les organisations à évaluer intelligemment leurs risques de conformité, à régir et à protéger les données sensibles, et à répondre efficacement aux exigences réglementaires. Microsoft Purview est riche en scénarios d’extensibilité et permet aux organisations d’adapter, d’étendre, d’intégrer, d’accélérer et de prendre en charge leurs solutions de conformité.

Il existe deux blocs de construction clés pour l’extensibilité de conformité :

- **Connecteurs de données**. Permet d’importer et d’archiver des données non-Microsoft afin de pouvoir appliquer Microsoft 365 fonctionnalités de protection et de gouvernance à des données tierces.

- **API**. Active l’accès par programmation aux fonctionnalités de Microsoft Purview.

## <a name="data-connectors"></a>Connecteurs de données

Microsoft fournit des connecteurs de données tiers qui peuvent être configurés dans le portail de conformité Microsoft Purview. Pour obtenir la liste des connecteurs de données fournis par Microsoft, consultez la table [des connecteurs de données tiers](archiving-third-party-data.md#third-party-data-connectors) . La table des connecteurs de données tiers récapitule également les solutions de conformité que vous pouvez appliquer aux données tierces après avoir importé et archivé des données dans Microsoft 365, ainsi que des liens vers les instructions pas à pas pour chaque connecteur.

Pour en savoir plus sur Microsoft 365 connecteurs de données, consultez [Archivage des données tierces](archiving-third-party-data.md). Si un type de données tiers n’est pas pris en charge par les connecteurs de données disponibles dans le portail de conformité, vous pouvez travailler avec un partenaire qui peut vous fournir un connecteur personnalisé. Pour obtenir la liste des partenaires avec qui vous pouvez travailler et le processus pas à pas pour cette méthode, consultez [Travailler avec un partenaire pour archiver des données tierces](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>Prérequis pour les connecteurs de données

La plupart des connecteurs de données disponibles dans le portail de conformité pour importer et archiver des données tierces nécessitent que vous prépariez et effectuez des tâches de configuration dans la source de données tierce. Ces conditions préalables sont documentées en détail pour chaque connecteur de données tiers.

Pour les connecteurs de données dans le portail de conformité fournis par l’un des partenaires de Microsoft, votre organisation a besoin d’une relation commerciale avec le partenaire avant de pouvoir déployer un connecteur.

Pour obtenir des conseils et des exigences pour les connecteurs de données tiers, consultez la section « Connecteurs de données » dans [Microsoft 365 conseils sur la sécurité & la conformité - Descriptions de service | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>API

Les API Microsoft Purview et Microsoft Priva sont disponibles dans le Kit de développement logiciel (SDK) Protection des données Microsoft, Microsoft API Graph et l’API d’activité de gestion Office 365. Certaines API de conformité font partie d’un nouvel ensemble d’API de sécurité et de conformité qui permettent aux développeurs de Microsoft 365 clients, éditeurs de logiciels indépendants, intégrateurs système et fournisseurs de services de sécurité gérés de créer des solutions de sécurité et de conformité à valeur élevée.

Pour en savoir plus sur l’accès aux API Graph, consultez [Vue d’ensemble de Microsoft Graph](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>API Microsoft Graph pour les demandes de droits d’objet

Conformément à certaines réglementations en matière de confidentialité dans le monde entier, les particuliers peuvent faire des demandes pour examiner ou gérer les données personnelles sur elles-mêmes collectées par les entreprises. Ces demandes sont appelées *demandes de droits d’objet* dans la solution Microsoft Priva Subject Rights Requests. Les demandes de droits d’objet sont également appelées *demandes de personnes concernées* (DSR) ou *demandes d’accès aux personnes concernées* (DSAR). Les API Microsoft Graph pour les demandes de droits d’objet permettent aux développeurs d’intégrer Microsoft 365 demandes de droits relatifs aux sujets à l’écosystème de confidentialité plus large. Cette extensibilité basée sur l’API permet aux organisations de répondre de manière unifiée aux demandes de droits d’objet sur l’ensemble de leur patrimoine de données couvrant les environnements Microsoft et non-Microsoft. Cette fonctionnalité facilite également l’automatisation à grande échelle et aide les organisations à respecter plus efficacement les réglementations du secteur sans s’appuyer sur des processus manuels.

Pour plus d’informations, consultez [les API Microsoft Graph pour la demande de droits d’objet](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview).

### <a name="microsoft-information-protection-mip-sdk"></a>SDK Protection des données Microsoft (MIP)

Le Kit de développement logiciel (SDK) MIP expose les services d’étiquetage et de protection des centres de sécurité et de conformité Microsoft 365 à des applications et services tiers. Les développeurs peuvent utiliser le Kit de développement logiciel (SDK) pour créer une prise en charge native pour l’application d’étiquettes et de protection aux fichiers. Les développeurs peuvent déterminer les actions à entreprendre quand des étiquettes spécifiques sont détectées et raisonner les informations chiffrées par MIP.

Les cas d’utilisation du Kit de développement logiciel (SDK) MIP de haut niveau sont les suivants :

- Application métier qui applique des étiquettes de classification aux fichiers à l’exportation.

- Application de conception CAO/CAM qui fournit une prise en charge native des étiquettes de confidentialité.

- Un service broker de sécurité d’accès cloud ou une solution de protection contre la perte de données qui peut chiffrer des données avec Azure Information Protection.

Pour en savoir plus sur le Kit de développement logiciel (SDK) MIP, les prérequis, les scénarios supplémentaires et les exemples, consultez [vue d’ensemble du SDK MIP](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>Microsoft API Graph pour Teams DLP

Les fonctionnalités [de protection contre la perte de données (DLP)](dlp-microsoft-teams.md) sont largement utilisées dans Microsoft Teams en particulier lorsque les organisations se sont déplacées vers le travail à distance. Récemment, nous avons [annoncé la disponibilité générale](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/) de l’API Microsoft Graph Change Notification pour les messages dans Teams. Cette API permet aux développeurs de créer des applications qui peuvent écouter Microsoft Teams messages en quasi-temps réel, puis d’implémenter des scénarios DLP pour les clients et les partenaires. En outre, l’API Correctif Microsoft Graph vous permet d’appliquer des actions DLP à Teams messages.

Ces deux API forment le API Graph Microsoft pour Teams DLP. Vous pouvez commencer en essayant [l’exemple d’application](https://github.com/microsoftgraph/aspnetcore-webhooks-sample). Pour plus d’informations sur Microsoft Teams webhooks de messagerie, consultez la [documentation](/graph/api/subscription-post-subscriptions).

Pour connaître les exigences en matière de licences pour Teams DLP, consultez [Microsoft 365 conseils sur les licences pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>Microsoft API Graph pour eDiscovery (préversion)

Avec [eDiscovery (Premium),](overview-ediscovery-20.md) les organisations peuvent découvrir les données où elles se trouvent et gérer d’autres flux de travail eDiscovery de bout en bout avec des fonctionnalités intelligentes d’apprentissage automatique et d’analytique pour réduire les données à l’ensemble approprié, le tout pendant que les données restent dans la limite de sécurité et de conformité Microsoft 365.

Graph API pour eDiscovery (Premium) peuvent être utilisées pour créer et gérer des cas, examiner des ensembles et examiner des requêtes de jeu de manière évolutive et reproductible. Cela permet aux clients et aux partenaires de créer des applications et des flux de travail pour automatiser des processus courants et répétitifs, tels que la création de cas et la gestion des conservations légales et des conservations légales.

Le premier ensemble d’API Graph pour eDiscovery est disponible en préversion publique. Nous prévoyons d’ajouter d’autres fonctionnalités d’ici la fin de l’année civile. Pour en savoir plus sur ces API et d’autres mises à jour pour eDiscovery (Premium), consultez ce [blog](https://aka.ms/Ignite2020AeDAA).

Pour connaître les exigences en matière de licences pour eDiscovery (Premium) et l’API, consultez la section « eDiscovery » dans les [instructions de licence Microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export"></a>Microsoft API Graph for Teams Export

Enterprise’archivage des informations (EIA) pour Microsoft Teams est un scénario clé pour nos clients, car il leur permet de répondre aux exigences réglementaires. Outre nos fonctionnalités intégrées d’archivage de contenu dans Microsoft Teams, les clients et les partenaires peuvent désormais utiliser Teams Exporter des API pour résoudre des scénarios d’application et d’intégration personnalisés. Les API d’exportation Teams prennent en charge l’exportation en bloc (jusqu’à 200 demandes par seconde/par application/par locataire) de Teams messages et pièces jointes de message. Les messages supprimés sont également accessibles par l’API jusqu’à 30 jours après leur suppression. Pour plus d’informations sur ces API Teams Exporter et comment les utiliser dans vos applications, consultez [Exporter du contenu avec les API d’exportation Microsoft Teams](/microsoftteams/export-teams-content).

Pour connaître les exigences en matière de licences pour l’utilisation des API d’exportation Teams, consultez [Microsoft 365 conseils de gestion des licences pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>API microsoft Graph Connecteur (préversion)

Avec [les connecteurs Microsoft Graph](/microsoftsearch/connectors-overview), les organisations peuvent indexer des données tierces afin qu’elles apparaissent dans Recherche Microsoft résultats. Cette fonctionnalité élargit les types de sources de contenu disponibles dans vos applications de productivité Microsoft 365 et dans l’écosystème Microsoft plus vaste. Les données tierces peuvent être hébergées localement ou dans des clouds publics ou privés. À compter d’eDiscovery (Premium), nous allons activer la préversion par les développeurs de la valeur de conformité intégrée de Microsoft 365 applications connectées. Cela permet la conformité pour les applications qui s’intègrent à l’écosystème Microsoft 365 afin de permettre aux utilisateurs d’avoir des expériences de conformité transparentes. Pour en savoir plus sur la façon d’incorporer des API Microsoft Graph Connecteur dans l’affichage de vos applications, consultez [Créer, mettre à jour et supprimer des connexions dans microsoft Graph](/graph/connecting-external-content-connectors-api-overview).
