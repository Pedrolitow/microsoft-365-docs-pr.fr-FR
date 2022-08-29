---
title: Créer une expérience classique de type de flux de travail de type informations sensibles pour créer des données exactes
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
description: Commencez à créer des types d’informations sensibles basés sur des correspondances de données exactes à l’aide du workflow d’expérience utilisateur classique.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0d01d90c83c8bdd919de275ea2f173082737de94
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67360605"
---
# <a name="create-exact-data-match-sensitive-information-type-workflow-classic-experience"></a>Créer une expérience classique de type de flux de travail de type informations sensibles pour créer des données exactes

La création et la mise à disposition d’un type d’informations sensibles basé sur EDM (EDM) sont un processus en plusieurs phases. Elles peuvent être utilisées dans les stratégies de protection contre la perte de données Microsoft Purview, l’étiquetage automatique, la découverte électronique et certaines tâches de gouvernance du contenu.  Cet article décrit le flux de travail et les liens vers les procédures pour chaque phase à l’aide de l’expérience classique.

## <a name="applies-to"></a>S’applique à

- Expérience classique

Si vous souhaitez créer un sit EDM à l’aide de la nouvelle expérience, consultez [Créer un flux de travail d’expérience SIT EDM ](sit-create-edm-sit-unified-ux-workflow.md).

## <a name="before-you-begin"></a>Avant de commencer

Veillez à passer en revue :

- [En savoir plus sur les SIT basés sur EDM](sit-learn-about-exact-data-match-based-sits.md)
- [Prise en main de la vue d’ensemble des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md)

## <a name="the-work-flow-at-a-glance"></a>Flux de travail en un clin d’œil

![phases de flux de travail de correspondance de données exactes](..\media\swimlane_edm_process.png)


|Phase|De quoi ai-je besoin ?|
|---|---|
|[Phase 1 : Exporter des données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)|-Accès en lecture aux données sensibles|
|[Phase 2 : Créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)|- Accès à l’Assistant Type d’informations sensibles dans le portail de conformité </br>- accès à la [Centre d'administration Microsoft 365 par le biais de Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) |
|[Phase 3 : Hachage et chargement de la table source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|-Groupe de sécurité personnalisé et compte d’utilisateur </br>- **Hachage et chargement à partir d’un ordinateur** : accès administrateur local à un ordinateur disposant d’un accès Internet direct et pour héberger l’agent de chargement EDM </br>- **Hachage et chargement à partir d’ordinateurs distincts** : accès administrateur local à un ordinateur disposant d’un accès Internet direct et hébergement de l’agent de chargement EDM pour le chargement et l’accès administrateur local à un ordinateur sécurisé pour héberger l’agent de chargement EDM pour hacher la table source d’informations sensibles </br>- Accès en lecture au fichier de table source d’informations sensibles </br> le fichier de schéma |
|[Phase 4 : Créer des données exactes correspondant au type d’informations sensibles/au package de règle](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) |- Accès au portail de conformité Microsoft Purview |
|[Tester un type d’informations sensibles correspondant exactement aux données](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)| - Accès au portail de conformité Microsoft Purview

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Exporter les données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
