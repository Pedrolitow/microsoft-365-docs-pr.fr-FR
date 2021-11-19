---
title: Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Commencer à créer des types d’informations sensibles basés sur des correspondances de données exactes.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 469cc7262ff1eef92d9a03e04070dc353e12b445
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61110498"
---
# <a name="get-started-with-exact-data-match-based-sensitive-information-types"></a>Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes

La création et la mise à disposition d’un type d’informations sensibles basé sur une correspondance exacte de données (EDM) est un processus en plusieurs phases. Ils peuvent être utilisés dans les stratégies de protection contre la perte de données, eDiscovery et certaines tâches de gouvernance de contenu Cet article décrit le flux de travail et des liens vers les procédures pour chacune des phases

## <a name="before-you-begin"></a>Avant de commencer

Familiarisez-vous avec les concepts et la terminologie des articles suivants :

- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Pour effectuer les tâches décrites dans cet article, vous devez être un administrateur général, un administrateur de conformité ou un administrateur Exchange Online. Pour en avoir plus sur les autorisations DLP, consultez la section[Autorisations](data-loss-prevention-policies.md#permissions).

Voir la [description du service de protection contre la perte de données](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business) pour obtenir des informations complètes sur les licences

## <a name="portal-links-for-your-subscription"></a>Liens vers les portails de votre abonnement

|Portail|World Wide/GCC|GCC-High|DOD|
|---|---|---|---|
|Office SCC|compliance.microsoft.com|scc.office365.us|scc.protection.apps.mil|
|Portail Microsoft 365 Defender|security.microsoft.com|security.microsoft.us|security.apps.mil|
|Centre de conformité Microsoft 365|compliance.microsoft.com|compliance.microsoft.us|compliance.apps.mil|

## <a name="the-work-flow-at-a-glance"></a>Flux de travail en un clin d’œil

![phases de flux de travail de correspondance exacte des données](..\media\swimlane_edm_process.png)


|Phase|De quoi ai-je besoin ?|
|---|---|
|[Phase 1 : Exportation des données sources pour le type d’informations sensibles de correspondance exacte](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)|-Accès en lecture aux données sensibles|
|[Phase 2 : Création du schéma pour les types d’informations sensibles basés sur la correspondance exacte des données](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)|- Accès à l’Assistant Type d’informations sensibles dans le Centre d'administration Microsoft 365 </br>- accès à Centre d'administration Microsoft 365 [via Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) |
|[Phase 3 : hachage et chargement de la table des sources d’informations sensibles pour les types d’informations sensibles de correspondance exacte des données](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|-Groupe de sécurité personnalisé et compte d’utilisateur </br>- **Hachage et chargement à partir d’un** ordinateur : accès administrateur local à un ordinateur avec un accès Internet direct et pour héberger l’agent Télécharger EDM </br>- Hachage et chargement à partir d’ordinateurs distincts : accès administrateur local à un ordinateur avec accès Internet direct et héberger l’agent EDM Télécharger pour le chargement et l’accès administrateur local à un ordinateur sécurisé pour héberger l’agent EDM Télécharger afin de hachage de la table des sources d’informations sensibles </br>- Accès en lecture au fichier de table des sources d’informations sensibles </br> fichier de schéma |
|[Phase 4 : Créer un package de règles/type d’informations sensibles de correspondance exacte de données](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) |- Accès au Centre Microsoft 365 conformité de l’application |
|[Tester un type d’informations sensibles correspondant exactement aux données](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)| - Accès au Centre Microsoft 365 conformité de l’application

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Exporter les données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
