---
title: Vue d’ensemble de la mobilité et de la sécurité de base pour Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Utilisez Basic Mobility and Security pour définir des stratégies de sécurité des appareils et des règles d’accès.
ms.openlocfilehash: 6ae42b9d7515e027e826fe7735a63b23ffd0eff04cb37995d28c60c9dddfada1
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53826845"
---
# <a name="overview-of-basic-mobility-and-security-for-microsoft-365"></a>Vue d’ensemble de la mobilité et de la sécurité de base pour Microsoft 365

Vous pouvez gérer et sécuriser les appareils mobiles lorsqu’ils sont connectés à votre organisation Microsoft 365 à l’aide de Basic Mobility and Security. Les appareils mobiles, tels que les smartphones et les tablettes, utilisés pour accéder à la messagerie, au calendrier, aux contacts et aux documents professionnels donnent aux employés la possibilité d’effectuer leur travail partout, à tout moment. Il est donc essentiel de protéger les informations de votre organisation lorsque des personnes utilisent des appareils. Vous pouvez utiliser la mobilité et la sécurité de base pour définir des stratégies de sécurité des appareils et des règles d’accès, et pour effacer les appareils mobiles en cas de perte ou de vol.

:::image type="content" source="../../media/basic-mobility-security/bms-3-setup.png" alt-text="Configuration de base de la mobilité et de la sécurité":::

## <a name="what-types-of-devices-can-you-manage"></a>Quels types d’appareils pouvez-vous gérer ?

Vous pouvez utiliser la mobilité et la sécurité de base pour gérer de nombreux types d’appareils mobiles tels que Windows Phone, Android, iPhone et iPad. Pour gérer les appareils mobiles utilisés par les membres de votre organisation, chaque personne doit avoir une licence Microsoft 365 applicable et son appareil doit être inscrit à Basic Mobility and Security.

Pour voir ce que Basic Mobility and Security prend en charge pour chaque type d’appareil, voir [Fonctionnalités de basic Mobility and Security](capabilities.md).

## <a name="setup-steps-for-basic-mobility-and-security"></a>Étapes de configuration de Basic Mobility and Security

Un administrateur Microsoft 365 global doit effectuer les étapes suivantes pour activer et configurer Basic Mobility and Security. Pour obtenir la procédure détaillée, suivez les instructions de [la procédure Set up Basic Mobility and Security](set-up.md). 

Voici un résumé des étapes :

**Étape 1 :** Activez Basic Mobility and Security en suivant les étapes de la procédure  [Set up Basic Mobility and Security](set-up.md).

**Étape 2 :** Configurer La mobilité et la sécurité de base en créant, par exemple, un certificat APNs pour gérer les appareils iOS et en ajoutant un enregistrement DNS (Domain Name System) pour votre domaine afin de prendre en charge Windows téléphones.

**Étape 3 :** Créez des stratégies d’appareil et appliquez-les à des groupes d’utilisateurs. Lorsque vous faites cela, vos utilisateurs obtiennent un message d’inscription sur leur appareil et une fois l’inscription terminée, leurs appareils sont limités par les stratégies que vous avez définies pour eux. Pour plus d’informations, voir [Inscrire votre appareil mobile à l’aide de Basic Mobility and Security](enroll-your-mobile-device.md). 

:::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Paramètres de stratégie de sécurité et de mobilité de base":::

## <a name="device-management-tasks"></a>Tâches de gestion des appareils

Une fois que vous avez installé basic Mobility and Security et que vos utilisateurs ont inscrit leurs appareils, vous pouvez gérer les appareils, bloquer l’accès ou effacer un appareil, si nécessaire. Pour en savoir plus sur certaines tâches courantes de gestion des [appareils,](manage-enrolled-devices.md)notamment sur l’endroit où effectuer les tâches, voir Gérer les appareils inscrits dans Gestion des appareils mobiles pour Microsoft 365 .

## <a name="other-ways-to-manage-devices-and-apps"></a>Autres façons de gérer les appareils et les applications

Si vous avez simplement besoin de la gestion des applications mobiles (MAM), par exemple pour les personnes mettant à jour des projets de travail sur leurs propres appareils, Intune propose une autre option en plus de l’inscription et de la gestion des appareils. Un abonnement Intune vous permet de configurer des stratégies MAM à l’aide du portail Azure, même si les appareils des personnes ne sont pas inscrits dans Intune. Pour plus d’informations, voir [vue d’ensemble des stratégies de protection des applications.](/mem/intune/apps/app-protection-policy)

## <a name="related-content"></a>Contenu connexe

[Configurer la mobilité et la sécurité de](set-up.md) base (article)\
[Inscrire votre appareil mobile à l’aide de Basic Mobility and Security](enroll-your-mobile-device.md) (article)\
[Gérer les appareils inscrits à Gestion des](manage-enrolled-devices.md) appareils mobiles pour Microsoft 365 (article)\
[Obtenir des détails sur les appareils gérés par Basic Mobility and Security](get-details-about-managed-devices.md) (article)