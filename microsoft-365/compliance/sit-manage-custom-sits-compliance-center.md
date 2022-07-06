---
title: Gérer les types d’informations sensibles personnalisés dans le Centre de conformité
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
description: Découvrez comment modifier et supprimer des types d’informations sensibles personnalisés dans le Centre de conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5e0b1b91fd19a5e0705ad95affe888a87847caf8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621958"
---
# <a name="manage-custom-sensitive-information-types-in-the-compliance-center"></a>Gérer les types d’informations sensibles personnalisés dans le Centre de conformité

Cet article vous guide tout au long des étapes de modification et de suppression d’un type d’informations sensibles personnalisé existant dans le Centre de conformité.

## <a name="modify-custom-sensitive-information-types-in-the-compliance-center"></a>Modifier des types d’informations sensibles personnalisés dans le centre de conformité

1. Dans le centre de conformité, accédez à **Classification de données** \> **Types d’informations sensibles**, puis sélectionnez le type d’informations sensibles dans la liste que vous voulez modifier, puis sélectionnez **Modifier**.

2. Vous pouvez ajouter d’autres motifs, avec des éléments principaux et de prise en charge uniques, des niveaux de confiance, la proximité des caractères et des [**vérifications supplémentaires**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks), ou modifier/supprimer les éléments existants.

## <a name="remove-custom-sensitive-information-types-in-the-compliance-center"></a>Supprimer des types d’informations sensibles personnalisés dans le centre de Conformité 

> [!NOTE]
> Vous pouvez uniquement supprimer des types d’informations sensibles personnalisés ; vous ne pouvez pas supprimer des types d’informations sensibles intégrés.

> [!IMPORTANT]
> Avant de supprimer un type d’informations sensibles personnalisé, vérifiez qu’aucune stratégie DLP ou règle de flux de courrier Exchange (également appelées règles de transport) ne référence toujours le type d’informations sensibles.

1. Dans le centre de conformité, accédez à **Classification des données** \> **Types d’informations sensibles** puis choisissez le type d’informations sensibles dans la liste que vous voulez supprimer.

2. Dans le lanceur qui s’ouvre, sélectionnez **Supprimer**.
