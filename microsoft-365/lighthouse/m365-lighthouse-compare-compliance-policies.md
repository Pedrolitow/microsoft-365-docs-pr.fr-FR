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
ms.openlocfilehash: 05f67cda1e99aff0b43109c5f55f78efaf30049c
ms.sourcegitcommit: f3c912780bbcf5a5b47de192202adb3afbd5952b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2022
ms.locfileid: "62219020"
---
# <a name="compare-device-compliance-policy-settings"></a>Comparer les paramètres de stratégie de conformité des appareils

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences.](m365-lighthouse-requirements.md) Si votre organisation n’a pas Microsoft 365 Lighthouse, [consultez s’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse vous permet d’afficher les stratégies de conformité entre vos locataires dans un affichage unique. Vous pouvez stimuler la sécurité et la normalisation au sein de vos locataires en comparant les stratégies. Vous pouvez filtrer les affichages pour voir les paramètres qui ont été configurés (par opposition aux paramètres qui n’ont pas été configurés), les paramètres qui diffèrent dans leurs configurations ou uniquement les paramètres qui correspondent. Vous pouvez également rechercher des paramètres spécifiques qui vous intéressent et voir comment cela se compare entre les stratégies.

## <a name="before-you-begin"></a>Avant de commencer

- Les appareils doivent avoir une licence Intune et être inscrits Microsoft Endpoint Manager (MEM).

## <a name="compare-policy-settings"></a>Comparer les paramètres de stratégie

1. Dans le volet de navigation gauche de l’écran, sélectionnez **Appareils.**

2. Cliquez sur l'onglet **Stratégies**.

3. Dans la liste **de** listes listes de filtres, sélectionnez un système d’exploitation/une plateforme.

   > [!NOTE]
   > Vous pouvez uniquement comparer des stratégies avec le même système d’exploitation/plateforme.

4. Dans la liste filtrée, sélectionnez jusqu’à trois stratégies à comparer.

5. Sélectionnez **Comparer.**

Vous pouvez filtrer les résultats pour voir les **Paramètres qui diffèrent,** Paramètres qui **correspondent** ou **paramètres configurés.**

## <a name="configure-a-policy-setting"></a>Configurer un paramètre de stratégie

1. Dans le volet de navigation gauche de l’écran, sélectionnez **Appareils.**

2. Cliquez sur l'onglet **Stratégies**.

3. Dans la liste, sélectionnez un nom de stratégie.

4. Dans le volet Détails de la stratégie, **sélectionnez Afficher** cette stratégie dans Microsoft Endpoint Manager .

5. Dans MEM, modifiez les paramètres de stratégie selon vos besoins.

## <a name="next-steps"></a>Prochaines étapes

Lorsque vous ajustez la stratégie, veillez à évaluer vos modifications par rapport à vos paramètres de référence actuels. Pour plus d’informations, voir [Vue d’ensemble de l’utilisation des lignes de base pour déployer des configurations client standard.](m365-lighthouse-deploy-standard-tenant-configurations-overview.md)

## <a name="related-content"></a>Contenu connexe

[Qu’est-ce que l’inscription des appareils dans Intune ?](/mem/intune/enrollment/device-enrollment) (article)  
[Utiliser des stratégies de conformité pour définir des règles pour les appareils que vous gérez avec Intune](/mem/intune/protect/device-compliance-get-started) (article)  
[Vue d’ensemble de l’utilisation des lignes de base pour déployer des configurations client standard](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (article)
