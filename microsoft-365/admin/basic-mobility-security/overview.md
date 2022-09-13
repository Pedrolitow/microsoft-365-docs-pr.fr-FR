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
ms.localizationpriority: medium
ms.collection:
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
description: Gérez et sécurisez les appareils mobiles connectés à votre organisation Microsoft 365 en configurant et en utilisant mobilité et sécurité de base.
ms.openlocfilehash: 0d36a12220e6e2c7aac1109309fb11b52ce5dd89
ms.sourcegitcommit: 37e137535c4f70702afe1a5eeaa899c75ee02cfd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2022
ms.locfileid: "67663386"
---
# <a name="overview-of-basic-mobility-and-security-for-microsoft-365"></a>Vue d’ensemble de la mobilité et de la sécurité de base pour Microsoft 365

Vous pouvez gérer et sécuriser les appareils mobiles lorsqu’ils sont connectés à votre organisation Microsoft 365 à l’aide de mobilité et de sécurité de base. Les appareils mobiles tels que les smartphones et les tablettes utilisés pour accéder à la messagerie professionnelle, au calendrier, aux contacts et aux documents jouent un rôle important dans la façon dont les employés effectuent leur travail à tout moment, où qu’ils se trouvent. Il est donc essentiel de protéger les informations de votre organisation lorsque les utilisateurs utilisent des appareils. Vous pouvez utiliser La mobilité et la sécurité de base pour définir des stratégies et des règles d’accès de sécurité des appareils et réinitialiser les appareils mobiles en cas de perte ou de vol.

:::image type="content" source="../../media/basic-mobility-security/bms-3-setup.png" alt-text="Configuration de base de la mobilité et de la sécurité.":::

## <a name="what-types-of-devices-can-you-manage"></a>Quels types d’appareils pouvez-vous gérer ?

Vous pouvez utiliser mobilité et sécurité de base pour gérer de nombreux types d’appareils mobiles comme Android, iPhone et iPad. Pour gérer les appareils mobiles utilisés par les membres de votre organisation, chaque personne doit disposer d’une licence Microsoft 365 applicable et son appareil doit être inscrit à Basic Mobility and Security.

Pour voir ce que la mobilité et la sécurité de base prennent en charge pour chaque type d’appareil, consultez [Fonctionnalités de mobilité et de sécurité de base](capabilities.md).

## <a name="setup-steps-for-basic-mobility-and-security"></a>Étapes de configuration de la mobilité et de la sécurité de base

Un administrateur général Microsoft 365 doit effectuer les étapes suivantes pour activer et configurer la mobilité et la sécurité de base. Pour des étapes détaillées, suivez les instructions de [configuration de la mobilité et de la sécurité de base](set-up.md). 

Voici un résumé des étapes :

**Étape 1 :** Activez mobilité et sécurité de base en suivant les étapes de configuration de [la mobilité et de la sécurité de base](set-up.md).

**Étape 2 :** Configurez la mobilité et la sécurité de base en créant, par exemple, un certificat APNs pour gérer les appareils iOS et en ajoutant un enregistrement DNS (Domain Name System) pour votre domaine.

**Étape 3 :** Créez des stratégies d’appareil et appliquez-les à des groupes d’utilisateurs. Lorsque vous effectuez cette opération, vos utilisateurs reçoivent un message d’inscription sur leur appareil et, une fois l’inscription terminée, leurs appareils sont limités par les stratégies que vous avez configurées pour eux. Pour plus d’informations, consultez [Inscrire votre appareil mobile à l’aide de mobilité et de sécurité de base](enroll-your-mobile-device.md). 

:::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Paramètres de stratégie de sécurité et de mobilité de base.":::

## <a name="device-management-tasks"></a>Tâches de gestion des appareils

Une fois que vous avez configuré La mobilité et la sécurité de base et que vos utilisateurs ont inscrit leurs appareils, vous pouvez gérer les appareils, bloquer l’accès ou réinitialiser un appareil, si nécessaire. Pour en savoir plus sur certaines tâches courantes de gestion des appareils, notamment l’endroit où effectuer les tâches, consultez [Gérer les appareils inscrits dans Mobile Gestion des appareils pour Microsoft 365](manage-enrolled-devices.md).

## <a name="other-ways-to-manage-devices-and-apps"></a>Autres façons de gérer les appareils et les applications

Si vous avez simplement besoin de gestion des applications mobiles (MAM), peut-être pour les personnes mettant à jour des projets de travail sur leurs propres appareils, Intune fournit une autre option que l’inscription et la gestion des appareils. Un abonnement Intune vous permet de configurer des stratégies GAM à l’aide de la Portail Azure, même si les appareils des personnes ne sont pas inscrits dans Intune. Pour plus d’informations, consultez [Protection d'applications vue d’ensemble des stratégies](/mem/intune/apps/app-protection-policy).

## <a name="related-content"></a>Contenu associé

[Configurer la mobilité et la sécurité de base](set-up.md) (article)\
[Inscrire votre appareil mobile à l’aide de la mobilité et de la sécurité de base](enroll-your-mobile-device.md) (article)\
[Gérer les appareils inscrits dans Mobile Gestion des appareils pour Microsoft 365](manage-enrolled-devices.md) (article)\
