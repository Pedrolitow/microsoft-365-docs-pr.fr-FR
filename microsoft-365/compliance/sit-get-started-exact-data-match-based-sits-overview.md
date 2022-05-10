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
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Démarrage la création de types d’informations sensibles basés sur des correspondances de données exactes.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 592a4c7342af9ffe5c18d0d25b99b12cd1b3e212
ms.sourcegitcommit: f723ebbc56db8013598a88b0d7f13214d9d3eb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2022
ms.locfileid: "65294666"
---
# <a name="get-started-with-exact-data-match-based-sensitive-information-types"></a>Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

La création et la mise à disposition d’un type d’informations sensibles basé sur EDM (EDM) sont un processus en plusieurs phases. Ils peuvent être utilisés dans les stratégies de protection contre la perte de données Microsoft Purview, eDiscovery et certaines tâches de gouvernance du contenu Cet article décrit le flux de travail et les liens vers les procédures pour chacune des phases

## <a name="before-you-begin"></a>Avant de commencer

Familiarisez-vous avec les concepts et la terminologie de ces articles :

- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

## <a name="supported-regions"></a>Régions prises en charge

La correspondance exacte des données est disponible dans les régions suivantes :

- Asie-Pacifique
- Australie
- Brésil
- Canada
- Europe
- France
- Allemagne
- Inde
- Japon
- Corée
- Norvège
- Afrique du Sud
- Suisse
- Émirats arabes unis
- Royaume-Uni
- États-Unis
- DoD des États-Unis
- Cloud de la communauté du secteur public des États-Unis
- US GCCH

Vous pouvez déterminer la région dans laquelle votre locataire héberge les données au repos en suivant les procédures décrites dans [l’emplacement où vos données client Microsoft 365 sont stockées](../enterprise/o365-data-locations.md) et en faisant référence aux emplacements des centres de données dans le même article.

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Pour effectuer les tâches décrites dans cet article, vous devez être un administrateur général, un administrateur de conformité ou un administrateur Exchange Online. Pour en avoir plus sur les autorisations DLP, consultez la section[Autorisations](data-loss-prevention-policies.md#permissions).

Consultez la [description du service de protection contre la perte de données](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business) pour obtenir des informations complètes sur les licences

## <a name="portal-links-for-your-subscription"></a>Liens vers les portails de votre abonnement

|Portail|World Wide/GCC|GCC-High|DOD|
|---|---|---|---|
|Office SCC|compliance.microsoft.com|scc.office365.us|scc.protection.apps.mil|
|Portail Microsoft 365 Defender|security.microsoft.com|security.microsoft.us|security.apps.mil|
|Portail de conformité Microsoft Purview|compliance.microsoft.com|compliance.microsoft.us|compliance.apps.mil|

## <a name="the-work-flow-at-a-glance"></a>Flux de travail en un clin d’œil

![phases de flux de travail de correspondance de données exactes](..\media\swimlane_edm_process.png)


|Phase|De quoi ai-je besoin ?|
|---|---|
|[Phase 1 : Exporter des données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)|-Accès en lecture aux données sensibles|
|[Phase 2 : Créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)|- Accès à l’Assistant Type d’informations sensibles dans le Centre d'administration Microsoft 365 </br>- accès à [Centre d'administration Microsoft 365 via PowerShell sécurité & conformité](/powershell/exchange/connect-to-scc-powershell) |
|[Phase 3 : Hachage et chargement de la table source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|-Groupe de sécurité personnalisé et compte d’utilisateur </br>- **Hachage et chargement à partir d’un ordinateur** : accès administrateur local à un ordinateur disposant d’un accès Direct à Internet et pour héberger l’agent EDM Télécharger </br>- **Hachage et chargement à partir d’ordinateurs distincts** : accès administrateur local à un ordinateur disposant d’un accès Internet direct et hébergement de l’agent de Télécharger EDM pour le chargement et l’accès administrateur local à un ordinateur sécurisé pour héberger l’agent EDM Télécharger pour hachager la table source d’informations sensibles </br>- Accès en lecture au fichier de table source d’informations sensibles </br> le fichier de schéma |
|[Phase 4 : Créer des données exactes correspondant au type d’informations sensibles/au package de règle](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) |- Accès au portail de conformité Microsoft Purview |
|[Tester un type d’informations sensibles correspondant exactement aux données](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)| - Accès au portail de conformité Microsoft Purview

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Exporter les données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
