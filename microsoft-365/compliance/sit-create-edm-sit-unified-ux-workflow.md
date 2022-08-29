---
title: Créer une nouvelle expérience de flux de travail de type de données exactes correspondant à des informations sensibles
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
description: Commencez à créer des types d’informations sensibles basés sur des correspondances de données exactes à l’aide de la nouvelle expérience.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 47fa9bd604f5a905ce46dad2ef0b2177c86cfdec
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67360588"
---
# <a name="create-exact-data-match-sensitive-information-type-workflow-new-experience"></a>Créer une nouvelle expérience de flux de travail de type de données exactes correspondant à des informations sensibles

La création et la mise à disposition d’un type d’informations sensibles basé sur EDM (EDM) sont un processus en plusieurs phases. Ils peuvent être utilisés dans les stratégies de protection contre la perte de données Microsoft Purview, eDiscovery et certaines tâches de gouvernance du contenu Cet article décrit le flux de travail et les liens vers les procédures pour chacune des phases

## <a name="applies-to"></a>S’applique à

- Nouvelle expérience

Si vous souhaitez créer un sit EDM à l’aide de l’expérience classique, [créez l’expérience classique EDM SIT](sit-create-edm-sit-classic-ux-workflow.md).

## <a name="before-you-begin"></a>Avant de commencer

Veillez à passer en revue :

- [En savoir plus sur les SIT basés sur EDM](sit-learn-about-exact-data-match-based-sits.md)
- [Prise en main de la vue d’ensemble des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md)

## <a name="the-work-flow-at-a-glance"></a>Flux de travail en un clin d’œil


|Phase|De quoi ai-je besoin ?|
|---|---|
|[Phase 1 : Exporter des données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)|-Accès en lecture aux données sensibles|
|[Phase 2 : Créer l’exemple de fichier](sit-create-edm-sit-unified-ux-sample-file.md)|- Connaître les en-têtes de colonne et le format des données que vous recherchez dans chaque colonne.
|[Phase 3 : Créer le sit EDM](sit-create-edm-sit-unified-ux-schema-rule-package.md)|- Accès à la correspondance exacte des données de **classification** > **des données** du portail  > **de conformité Microsoft Purview** |
|[Phase 4 : Hachage et chargement de la table source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md)|-Groupe de sécurité personnalisé et compte d’utilisateur </br>- **Hachage et chargement à partir d’un ordinateur** : accès administrateur local à un ordinateur disposant d’un accès Internet direct et pour héberger l’agent de chargement EDM </br>- **Hachage et chargement à partir d’ordinateurs distincts** : accès administrateur local à un ordinateur disposant d’un accès Internet direct et hébergement de l’agent de chargement EDM pour le chargement et l’accès administrateur local à un ordinateur sécurisé pour héberger l’agent de chargement EDM pour hacher la table source d’informations sensibles </br>- Accès en lecture au fichier de table source d’informations sensibles|
|[Phase 5 : Tester un type d’informations sensibles correspondant exactement aux données](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)| - Accès au portail de conformité Microsoft Purview

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)


## <a name="next-step"></a>Étape suivante

- **Pour une nouvelle expérience** : [Exporter des données sources pour un type d’informations sensibles basé sur des correspondances de données exactes](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
