---
title: Comparer les paramètres de stratégie de conformité des appareils
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment comparer les paramètres de stratégie de conformité des appareils.
ms.openlocfilehash: 30645ef4d59fcdee0d994ae709ff9bb45fc21b09
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320366"
---
# <a name="compare-device-compliance-policy-settings"></a>Comparer les paramètres de stratégie de conformité des appareils

Microsoft 365 Lighthouse vous permet d’afficher les stratégies de conformité entre vos locataires dans un affichage unique. Vous pouvez stimuler la sécurité et la normalisation au sein de vos locataires en comparant les stratégies. Vous pouvez filtrer les affichages pour voir les paramètres qui ont été configurés (par opposition aux paramètres qui n’ont pas été configurés), les paramètres qui diffèrent dans leurs configurations ou les paramètres qui correspondent. Vous pouvez également rechercher des paramètres spécifiques pour voir comment ils se comparent entre les stratégies.

## <a name="before-you-begin"></a>Avant de commencer

Assurez-vous que les appareils ont une licence Microsoft Intune et qu’ils sont inscrits Microsoft Endpoint Manager (MEM).

## <a name="compare-policy-settings"></a>Comparer les paramètres de stratégie

1. Dans le volet de navigation gauche de l’écran, sélectionnez **Appareils**.

2. Cliquez sur l'onglet **Stratégies**.

3. Dans la liste **drop-down Filtres** , sélectionnez un système d’exploitation ou une plateforme.

   > [!NOTE]
   > Vous pouvez uniquement comparer des stratégies avec le même système d’exploitation ou la même plateforme.

4. Dans la liste filtrée, sélectionnez jusqu’à trois stratégies à comparer.

5. **Sélectionnez Comparer**.

Vous pouvez filtrer les résultats pour voir les **Paramètres qui diffèrent**, Paramètres **qui correspondent** ou **les paramètres configurés**.

## <a name="configure-a-policy-setting"></a>Configurer un paramètre de stratégie

1. Dans le volet de navigation gauche de l’écran, sélectionnez **Appareils**.

2. Cliquez sur l'onglet **Stratégies**.

3. Dans la liste, sélectionnez un nom de stratégie.

4. Dans le volet Détails de la stratégie, **sélectionnez Afficher cette stratégie dans Microsoft Endpoint Manager**.

5. Dans MEM, modifiez les paramètres de stratégie selon vos besoins.

## <a name="next-steps"></a>Étapes suivantes

Lorsque vous ajustez la stratégie, veillez à évaluer vos modifications par rapport à vos paramètres de référence actuels. Pour plus d’informations, voir [Vue d’ensemble de l’utilisation des lignes de base pour déployer des configurations client standard](m365-lighthouse-deploy-standard-tenant-configurations-overview.md).

## <a name="related-content"></a>Contenu associé

[Qu’est-ce que l’inscription des appareils dans Intune ?](/mem/intune/enrollment/device-enrollment) (article)  
[Utiliser des stratégies de conformité pour définir des règles pour les appareils que vous gérez avec Intune](/mem/intune/protect/device-compliance-get-started) (article)  
[Vue d’ensemble de l’utilisation des lignes de base pour déployer des configurations client standard](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (article)
