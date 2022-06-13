---
title: Comparer les paramètres de stratégie de conformité des appareils dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
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
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment comparer les paramètres de stratégie de conformité des appareils.
ms.openlocfilehash: 5b82067f7d06ddd599a0e8da73825e536cf2d3fd
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66008416"
---
# <a name="compare-device-compliance-policy-settings-in-microsoft-365-lighthouse"></a>Comparer les paramètres de stratégie de conformité des appareils dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse vous permet d’afficher les stratégies de conformité entre vos locataires en une seule vue. Vous pouvez favoriser la sécurité et la standardisation entre vos locataires en comparant les stratégies. Vous pouvez filtrer les vues pour afficher les paramètres qui ont été configurés (par rapport aux paramètres qui n’ont pas été configurés), les paramètres qui diffèrent dans leurs configurations ou les paramètres qui correspondent. Vous pouvez également rechercher des paramètres spécifiques pour voir comment ils se comparent entre les stratégies.

## <a name="before-you-begin"></a>Avant de commencer

Assurez-vous que les appareils disposent d’une licence Microsoft Intune et sont inscrits dans Microsoft Endpoint Manager (MEM).

## <a name="compare-policy-settings"></a>Comparer les paramètres de stratégie

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Appareils**.

2. Cliquez sur l'onglet **Stratégies**.

3. Dans la liste déroulante **Filtres** , sélectionnez un système d’exploitation ou une plateforme.

   > [!NOTE]
   > Vous pouvez uniquement comparer des stratégies avec le même système d’exploitation ou la même plateforme.

4. Dans la liste filtrée, sélectionnez jusqu’à trois stratégies que vous souhaitez comparer.

5. Sélectionnez **Comparer**.

Vous pouvez filtrer les résultats pour voir **Paramètres qui diffèrent**, **Paramètres qui correspondent** ou **paramètres configurés**.

## <a name="configure-a-policy-setting"></a>Configurer un paramètre de stratégie

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Appareils**.

2. Cliquez sur l'onglet **Stratégies**.

3. Dans la liste, sélectionnez un nom de stratégie.

4. Dans le volet Détails de la stratégie, sélectionnez **Afficher cette stratégie dans Microsoft Endpoint Manager**.

5. Dans MEM, modifiez les paramètres de stratégie en fonction des besoins.

## <a name="next-steps"></a>Étapes suivantes

Lorsque vous apportez des ajustements de stratégie, veillez à évaluer vos modifications par rapport à vos paramètres de base de référence actuels. Pour plus d’informations, consultez [Vue d’ensemble de l’utilisation des bases de référence pour déployer des configurations de locataire standard](m365-lighthouse-deploy-standard-tenant-configurations-overview.md).

## <a name="related-content"></a>Contenu connexe

[Qu’est-ce que l’inscription des appareils dans Intune ?](/mem/intune/enrollment/device-enrollment) (article)  
[Utiliser des stratégies de conformité pour définir des règles pour les appareils que vous gérez avec Intune](/mem/intune/protect/device-compliance-get-started) (article)  
[Vue d’ensemble de l’utilisation de bases de référence Microsoft 365 Lighthouse pour déployer des configurations de locataire standard](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (article)
