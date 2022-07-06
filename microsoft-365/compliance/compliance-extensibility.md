---
title: Extensibilité Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
ms.openlocfilehash: 8cda9ea3a5ef69af69ab802ca21aa8c4c0e716b9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621180"
---
# <a name="microsoft-purview-and-microsoft-priva-extensibility"></a>Extensibilité de Microsoft Purview et Microsoft Priva

Les solutions Microsoft Purview aident les organisations à évaluer intelligemment leurs risques de conformité, à régir et à protéger les données sensibles, et à répondre efficacement aux exigences réglementaires. Microsoft Purview est riche en scénarios d’extensibilité et permet aux organisations d’adapter, d’étendre, d’intégrer, d’accélérer et de prendre en charge leurs solutions de conformité.

Il existe deux blocs de construction clés pour l’extensibilité de conformité :

- **Connecteurs de données**. Permet d’importer et d’archiver des données non-Microsoft afin de pouvoir appliquer des fonctionnalités de protection et de gouvernance Microsoft 365 à des données tierces.

- **API**. Active l’accès par programmation aux fonctionnalités de Microsoft Purview.

## <a name="data-connectors"></a>Connecteurs de données

Microsoft fournit des connecteurs de données tiers qui peuvent être configurés dans le portail de conformité Microsoft Purview. Pour obtenir la liste des connecteurs de données fournis par Microsoft, consultez la table [des connecteurs de données tiers](archiving-third-party-data.md#third-party-data-connectors) . La table des connecteurs de données tiers récapitule également les solutions de conformité que vous pouvez appliquer aux données tierces après avoir importé et archivé des données dans Microsoft 365, ainsi que des liens vers les instructions pas à pas pour chaque connecteur.

Pour en savoir plus sur les connecteurs de données Microsoft 365, consultez [Archivage de données tierces](archiving-third-party-data.md). Si un type de données tiers n’est pas pris en charge par les connecteurs de données disponibles dans le portail de conformité, vous pouvez travailler avec un partenaire qui peut vous fournir un connecteur personnalisé. Pour obtenir la liste des partenaires avec qui vous pouvez travailler et le processus pas à pas pour cette méthode, consultez [Travailler avec un partenaire pour archiver des données tierces](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>Prérequis pour les connecteurs de données

La plupart des connecteurs de données disponibles dans le portail de conformité pour importer et archiver des données tierces nécessitent que vous prépariez et effectuez des tâches de configuration dans la source de données tierce. Ces conditions préalables sont documentées en détail pour chaque connecteur de données tiers.

Pour les connecteurs de données dans le portail de conformité fournis par l’un des partenaires de Microsoft, votre organisation a besoin d’une relation commerciale avec le partenaire avant de pouvoir déployer un connecteur.

Pour obtenir des conseils et des exigences pour les connecteurs de données tiers, consultez la section « Connecteurs de données » de [Microsoft 365 pour la sécurité & conformité - Descriptions de service | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>API

Les API Microsoft Purview et Microsoft Priva sont disponibles dans le Kit de développement logiciel (SDK) Protection des données Microsoft, Microsoft API Graph et l’API d’activité de gestion Office 365. Certaines API de conformité font partie d’un nouvel ensemble d’API de sécurité et de conformité qui permettent aux développeurs pour les clients Microsoft 365, aux éditeurs de logiciels indépendants, aux intégrateurs système et aux fournisseurs de services de sécurité managés de créer des solutions de sécurité et de conformité à valeur élevée.

Pour en savoir plus sur l’accès aux API Graph, consultez [Vue d’ensemble de Microsoft Graph](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>API Microsoft Graph pour les demandes de droits d’objet

Conformément à certaines réglementations en matière de confidentialité dans le monde entier, les particuliers peuvent faire des demandes pour examiner ou gérer les données personnelles sur elles-mêmes collectées par les entreprises. Ces demandes sont appelées *demandes de droits d’objet* dans la solution Demandes de droits des personnes concernées Microsoft Priva. Les demandes de droits d’objet sont également appelées *demandes de personnes concernées* (DSR) ou *demandes d’accès aux personnes concernées* (DSAR). Les API Microsoft Graph pour les demandes de droits d’objet permettent aux développeurs d’intégrer les demandes de droits d’objet liées à Microsoft 365 à l’écosystème de confidentialité plus large. Cette extensibilité basée sur l’API permet aux organisations de répondre de manière unifiée aux demandes de droits d’objet sur l’ensemble de leur patrimoine de données couvrant les environnements Microsoft et non-Microsoft. Cette fonctionnalité facilite également l’automatisation à grande échelle et aide les organisations à respecter plus efficacement les réglementations du secteur sans s’appuyer sur des processus manuels.

Pour plus d’informations, consultez [les API Microsoft Graph pour la demande de droits d’objet](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview).

### <a name="microsoft-information-protection-mip-sdk"></a>SDK Protection des données Microsoft (MIP)

Le Kit de développement logiciel (SDK) MIP expose les services d’étiquetage et de protection des centres de sécurité et de conformité Microsoft 365 à des applications et services tiers. Les développeurs peuvent utiliser le Kit de développement logiciel (SDK) pour créer une prise en charge native pour l’application d’étiquettes et de protection aux fichiers. Les développeurs peuvent déterminer les actions à entreprendre quand des étiquettes spécifiques sont détectées et raisonner les informations chiffrées par MIP.

Les cas d’utilisation du Kit de développement logiciel (SDK) MIP de haut niveau sont les suivants :

- Application métier qui applique des étiquettes de classification aux fichiers à l’exportation.

- Application de conception CAO/CAM qui fournit une prise en charge native des étiquettes de confidentialité.

- Un service broker de sécurité d’accès cloud ou une solution de protection contre la perte de données qui peut chiffrer des données avec Azure Information Protection.

Pour en savoir plus sur le Kit de développement logiciel (SDK) MIP, les prérequis, les scénarios supplémentaires et les exemples, consultez [vue d’ensemble du SDK MIP](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>Microsoft API Graph for Teams DLP

Les fonctionnalités [de protection contre la perte de données (DLP)](dlp-microsoft-teams.md) sont largement utilisées dans Microsoft Teams, en particulier lorsque les organisations sont passées au travail à distance. Nous avons [récemment annoncé la disponibilité générale](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/) de l’API de notification des modifications Microsoft Graph pour les messages dans Teams. Cette API permet aux développeurs de créer des applications qui peuvent écouter les messages Microsoft Teams en quasi-temps réel, puis d’implémenter des scénarios DLP pour les clients et les partenaires. En outre, l’API correctif Microsoft Graph vous permet d’appliquer des actions DLP aux messages Teams.

Ces deux API forment le API Graph Microsoft pour teams DLP. Vous pouvez commencer en essayant [l’exemple d’application](https://github.com/microsoftgraph/aspnetcore-webhooks-sample). Pour plus d’informations sur les webhooks de messagerie Microsoft Teams, consultez la [documentation](/graph/api/subscription-post-subscriptions).

Pour connaître les exigences en matière de licences pour Teams DLP, consultez [l’aide relative aux licences Microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>Microsoft API Graph pour eDiscovery (préversion)

Avec [eDiscovery (Premium),](overview-ediscovery-20.md) les organisations peuvent découvrir les données où elles se trouvent et gérer d’autres flux de travail eDiscovery de bout en bout avec des fonctionnalités intelligentes d’apprentissage automatique et d’analytique pour réduire les données à l’ensemble approprié, le tout pendant que les données restent dans la limite de sécurité et de conformité de Microsoft 365.

Les API Graph pour eDiscovery (Premium) peuvent être utilisées pour créer et gérer des cas, examiner des ensembles et examiner des requêtes d’ensemble de manière évolutive et reproductible. Cela permet aux clients et aux partenaires de créer des applications et des flux de travail pour automatiser des processus courants et répétitifs, tels que la création de cas et la gestion des conservations légales et des conservations légales.

Le premier ensemble d’API Graph pour eDiscovery est disponible en préversion publique. Nous prévoyons d’ajouter d’autres fonctionnalités d’ici la fin de l’année civile. Pour en savoir plus sur ces API et d’autres mises à jour pour eDiscovery (Premium), consultez ce [blog](https://aka.ms/Ignite2020AeDAA).

Pour connaître les exigences en matière de licences pour eDiscovery (Premium) et l’API, consultez la section « eDiscovery » de [l’aide sur les licences Microsoft 365 pour la sécurité & conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export"></a>Microsoft API Graph for Teams Export

L’archivage des informations d’entreprise (EIA) pour Microsoft Teams est un scénario clé pour nos clients, car il leur permet de répondre aux exigences réglementaires. Outre nos fonctionnalités intégrées d’archivage de contenu dans Microsoft Teams, les clients et les partenaires peuvent désormais utiliser les API d’exportation Teams pour résoudre des scénarios d’application et d’intégration personnalisés. Les API d’exportation Teams prennent en charge l’exportation en bloc (jusqu’à 200 demandes par seconde/par application/par locataire) des messages et pièces jointes de messages Teams. Les messages supprimés sont également accessibles par l’API jusqu’à 30 jours après leur suppression. Pour plus d’informations sur ces API d’exportation Teams et sur leur utilisation dans vos applications, consultez [Exporter du contenu avec les API Microsoft Teams Export](/microsoftteams/export-teams-content).

Pour connaître les exigences en matière de licences pour l’utilisation des API d’exportation Teams, consultez les [conseils de licences Microsoft 365 pour la sécurité & conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>API du connecteur Microsoft Graph (préversion)

Avec [les connecteurs Microsoft Graph](/microsoftsearch/connectors-overview), les organisations peuvent indexer des données tierces afin qu’elles apparaissent dans les résultats de recherche Microsoft. Cette fonctionnalité élargit les types de sources de contenu disponibles dans vos applications de productivité Microsoft 365 et dans l’écosystème Microsoft plus vaste. Les données tierces peuvent être hébergées localement ou dans des clouds publics ou privés. À compter d’eDiscovery (Premium), nous allons activer la préversion par les développeurs de la valeur de conformité intégrée des applications connectées à Microsoft 365. Cela permet la conformité des applications qui s’intègrent à l’écosystème Microsoft 365 pour permettre aux utilisateurs d’avoir des expériences de conformité transparentes. Pour en savoir plus sur l’intégration des API connecteur Microsoft Graph dans l’affichage de vos applications, consultez [Créer, mettre à jour et supprimer des connexions dans Microsoft Graph](/graph/connecting-external-content-connectors-api-overview).

### <a name="microsoft-graph-api-for-records-management-preview"></a>Microsoft API Graph pour la gestion des enregistrements (préversion)

Les organisations de tous types ont besoin d’une solution de gestion des enregistrements pour gérer les enregistrements critiques dans leurs données. [Gestion des enregistrements Microsoft Purview](records-management.md) permet à une organisation de gérer ses obligations légales, de démontrer la conformité aux réglementations et d’accroître l’efficacité avec la disposition régulière d’éléments qui ne sont plus nécessaires.

La solution de gestion des enregistrements est utilisée par les organisations dans de grands volumes pour utiliser ses différentes fonctionnalités de protection, d’étiquetage, de conservation ou de suppression de leurs données. Les API Microsoft Graph pour la gestion des enregistrements permettent aux organisations de gérer les étiquettes de rétention et leurs actions associées plus efficacement, d’automatiser les tâches répétitives et d’équiper les clients de flexibilité dans les options.

À présent déployée, la première version des API Graph pour la gestion des enregistrements prend en charge la gestion des étiquettes de rétention et la rétention basée sur les événements. Exemples de scénarios :

- **Gestion des étiquettes de rétention**
    
    Les administrateurs et les développeurs de gestion des enregistrements doivent maintenir leurs systèmes de gestion des enregistrements avec des étiquettes qui sont régulièrement créées, mises à jour et supprimées.
    
    Les développeurs et les administrateurs de conformité utilisent les API Graph pour la gestion des enregistrements afin d’effectuer des opérations CRUD sur l’entité d’étiquette afin de maintenir leurs systèmes.

- **Déclenchement d’un événement pour une étiquette existante**
    
    Lorsqu’un employé quitte une organisation, les informations sont mises à jour dans le système de gestion des RH. À partir de la date de départ, les documents confidentiels doivent être conservés pendant sept ans. L’étiquette de rétention « Employee_departure » est déjà appliquée à ces documents.
    
    Les développeurs et les administrateurs de conformité utilisent les API Graph pour la gestion des enregistrements pour lire l’étiquette « Employee_departure » et rechercher le type d’événement associé « Event-employee_departure ».
    
    Ils utilisent ensuite les API Graph pour la gestion des enregistrements afin de créer un événement pour le type d’événement associé. La période de rétention des documents confidentiels commence après la création de cet événement.

Pour plus d’informations sur les API Graph pour la gestion des enregistrements, consultez [Utiliser l’API Gestion des enregistrements Microsoft Graph](/graph/api/resources/security-recordsmanagement-overview?view=graph-rest-beta&preserve-view=true).

Pour connaître les exigences en matière de licences pour utiliser ces API, consultez la section relative à la gestion des enregistrements de [l’aide sur la gestion des licences Microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).
