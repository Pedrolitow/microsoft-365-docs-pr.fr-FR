---
title: Vue d’ensemble de la mobilité et de la sécurité de base pour Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier3
- scotvorg
- highpri
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Gérez et sécurisez les appareils mobiles connectés à votre organisation Microsoft 365 en configurant et en utilisant Mobilité et sécurité de base.
ms.openlocfilehash: 1dac959ff15147bb16c250ce4af4c2c16342cefd
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68727606"
---
# <a name="overview-of-basic-mobility-and-security-for-microsoft-365"></a>Vue d’ensemble de la mobilité et de la sécurité de base pour Microsoft 365

Vous pouvez gérer et sécuriser les appareils mobiles lorsqu’ils sont connectés à votre organisation Microsoft 365 à l’aide de Mobilité et sécurité de base. Les appareils mobiles tels que les smartphones et les tablettes qui sont utilisés pour accéder à la messagerie professionnelle, au calendrier, aux contacts et aux documents jouent un rôle important pour s’assurer que les employés effectuent leur travail à tout moment et en tout lieu. Il est donc essentiel que vous aidiez à protéger les informations de votre organisation lorsque les utilisateurs utilisent des appareils. Vous pouvez utiliser Mobilité et sécurité de base pour définir des stratégies de sécurité des appareils et des règles d’accès, et pour réinitialiser les appareils mobiles s’ils sont perdus ou volés.

:::image type="content" source="../../media/basic-mobility-security/bms-3-setup.png" alt-text="Configuration de la mobilité et de la sécurité de base.":::

## <a name="what-types-of-devices-can-you-manage"></a>Quels types d’appareils pouvez-vous gérer ?

Vous pouvez utiliser Mobilité et sécurité de base pour gérer de nombreux types d’appareils mobiles comme Android, iPhone et iPad. Pour gérer les appareils mobiles utilisés par les membres de votre organisation, chaque personne doit disposer d’une licence Microsoft 365 applicable et son appareil doit être inscrit à Mobilité et sécurité de base.

Pour voir ce que la mobilité et la sécurité de base prennent en charge pour chaque type d’appareil, consultez [Fonctionnalités de mobilité et de sécurité de base](capabilities.md).

## <a name="setup-steps-for-basic-mobility-and-security"></a>Étapes de configuration de la mobilité et de la sécurité de base

Un administrateur général Microsoft 365 doit effectuer les étapes suivantes pour activer et configurer Mobilité et sécurité de base. Pour obtenir des instructions détaillées, suivez les instructions fournies dans [Configurer la mobilité et la sécurité de base](set-up.md). 

Voici un résumé des étapes :

**Étape 1 :** Activez mobilité et sécurité de base en suivant les étapes décrites dans [Configurer la mobilité et la sécurité de base](set-up.md).

**Étape 2 :** Configurez Mobilité et sécurité de base, par exemple en créant un certificat APNs pour gérer les appareils iOS et en ajoutant un enregistrement DNS (Domain Name System) pour votre domaine.

**Étape 3 :** Créez des stratégies d’appareil et appliquez-les à des groupes d’utilisateurs. Dans ce cas, vos utilisateurs reçoivent un message d’inscription sur leur appareil et, lorsqu’ils ont terminé l’inscription, leurs appareils sont limités par les stratégies que vous avez configurées pour eux. Pour plus d’informations, consultez [Inscrire votre appareil mobile à l’aide de Mobilité et sécurité de base](enroll-your-mobile-device.md). 

:::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Paramètres de stratégie sécurité et mobilité de base.":::

## <a name="device-management-tasks"></a>Tâches de gestion des appareils

Une fois que mobilité et sécurité de base sont configurés et que vos utilisateurs ont inscrit leurs appareils, vous pouvez gérer les appareils, bloquer l’accès ou réinitialiser un appareil, si nécessaire. Pour en savoir plus sur certaines tâches courantes de gestion des appareils, notamment sur l’emplacement où effectuer les tâches, consultez [Gérer les appareils inscrits dans mobile Gestion des appareils pour Microsoft 365](manage-enrolled-devices.md).

## <a name="other-ways-to-manage-devices-and-apps"></a>Autres façons de gérer les appareils et les applications

Si vous avez simplement besoin de gestion des applications mobiles (GAM), peut-être pour les personnes mettant à jour des projets de travail sur leurs propres appareils, Intune offre une autre option en plus de l’inscription et de la gestion des appareils. Un abonnement Intune vous permet de configurer des stratégies GAM à l’aide de la Portail Azure, même si les appareils des utilisateurs ne sont pas inscrits dans Intune. Pour plus d’informations, consultez [vue d’ensemble des stratégies Protection d'applications](/mem/intune/apps/app-protection-policy).

## <a name="related-content"></a>Contenu associé

[Configurer la mobilité et la sécurité de base](set-up.md) (article)\
[Inscrire votre appareil mobile à l’aide de Mobilité et sécurité de base](enroll-your-mobile-device.md) (article)\
[Gérer les appareils inscrits dans mobile Gestion des appareils pour Microsoft 365](manage-enrolled-devices.md) (article)\
