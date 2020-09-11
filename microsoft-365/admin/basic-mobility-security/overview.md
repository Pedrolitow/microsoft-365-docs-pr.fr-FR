---
title: Vue d’ensemble de la sécurité et de la mobilité de base pour Microsoft 365
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
search.appverid:
- MET150
description: Utilisez la sécurité et la mobilité de base pour définir les stratégies de sécurité des appareils et les règles d’accès.
ms.openlocfilehash: 177b0769f3cad928d05a41cfe95d5d62ab2b4786
ms.sourcegitcommit: aeb94601a81db3ead8610c2f36cff30eb9fe10e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "47430153"
---
# <a name="overview-of-basic-mobility-and-security-for-microsoft-365"></a>Vue d’ensemble de la sécurité et de la mobilité de base pour Microsoft 365

Vous pouvez gérer et sécuriser les appareils mobiles lorsqu’ils sont connectés à votre organisation Microsoft 365 à l’aide de la sécurité et de la sécurité de base. Les appareils mobiles, tels que les smartphones et les tablettes, utilisés pour accéder à la messagerie, au calendrier, aux contacts et aux documents professionnels donnent aux employés la possibilité d’effectuer leur travail partout, à tout moment. Il est donc essentiel de protéger les informations de votre organisation lorsque des personnes utilisent des appareils. Vous pouvez utiliser la mobilité et la sécurité de base pour définir les stratégies de sécurité des appareils et les règles d’accès, et pour réinitialiser les appareils mobiles en cas de perte ou de vol.

:::image type="content" source="../../media/basic-mobility-security/bms-3-setup.png" alt-text="Configuration de base de la mobilité et de la sécurité":::

## <a name="what-types-of-devices-can-you-manage"></a>Quels types d’appareils pouvez-vous gérer ?

Vous pouvez utiliser la mobilité et la sécurité de base pour gérer de nombreux types d’appareils mobiles tels que Windows Phone, Android, iPhone et iPad. Pour gérer les appareils mobiles utilisés par les membres de votre organisation, chaque personne doit disposer d’une licence Microsoft 365 applicable et son appareil doit être inscrit dans la sécurité et la mobilité de base.

Pour connaître les supports de base et de sécurité pris en charge pour chaque type d’appareil, reportez-vous à la rubrique [fonctionnalités de base de mobilité et de sécurité](capabilities.md).

## <a name="setup-steps-for-basic-mobility-and-security"></a>Étapes de configuration pour la sécurité et la mobilité de base

Un administrateur général Microsoft 365 doit effectuer les étapes suivantes pour activer et configurer la sécurité et la mobilité de base. Pour obtenir la procédure détaillée, suivez les instructions de la procédure de configuration de la [mobilité et](set-up.md)de la sécurité de base. 

Voici un résumé des étapes :

**Étape 1 :** Pour activer la mobilité et la sécurité de base, procédez comme suit dans la [configuration de base Mobility and Security](set-up.md).

**Étape 2 :** Configurez la mobilité et la sécurité de base par, par exemple, en créant un certificat APNs pour gérer les appareils iOS et en ajoutant un enregistrement DNS (Domain Name System) pour votre domaine afin de prendre en charge les téléphones Windows.

**Étape 3 :** Créer des stratégies d’appareil et les appliquer à des groupes d’utilisateurs ; Lorsque vous effectuez cette opération, vos utilisateurs reçoivent un message d’inscription sur leur appareil, et lorsqu’ils ont terminé leur inscription, leurs appareils sont restreints par les stratégies que vous avez configurées pour eux. Pour plus d’informations, consultez [la rubrique inscrire votre appareil mobile à l’aide de la sécurité et de la sécurité de base](enroll-your-mobile-device.md). 

:::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Paramètres de stratégie de mobilité et de sécurité de base":::

## <a name="device-management-tasks"></a>Tâches de gestion des appareils

Une fois que vous avez configuré la mobilité et la sécurité de base et que vos utilisateurs ont inscrit leurs appareils, vous pouvez gérer les appareils, bloquer l’accès ou réinitialiser un appareil, le cas échéant. Pour en savoir plus sur certaines tâches courantes de gestion des appareils, notamment l’emplacement où effectuer les tâches, consultez la rubrique [Manage Devices in Mobile Device Management for Microsoft 365](manage-enrolled-devices.md).

## <a name="other-ways-to-manage-devices-and-apps"></a>Autres méthodes de gestion des appareils et des applications

Si vous avez simplement besoin de la gestion des applications mobiles (MAM), par exemple pour des personnes mettant à jour des projets de travail sur leurs propres appareils, Intune offre une autre option en plus de l’inscriptions et de la gestion des appareils. Un abonnement Intune vous permet de configurer des stratégies MAM à l’aide du portail Azure, même si les appareils de l’utilisateur ne sont pas inscrit dans Intune. Pour plus d’informations, consultez la rubrique [vue d’ensemble des stratégies de protection des applications](https://go.microsoft.com/fwlink/?LinkId=2132517).

## <a name="related-topics"></a>Voir aussi

[Configurer Mobility + Security](set-up.md)

[Inscrire votre appareil mobile à l’aide de la mobilité et de la sécurité de base](enroll-your-mobile-device.md)

[Gérer les appareils intégrés dans la gestion des appareils mobiles pour Microsoft 365](manage-enrolled-devices.md)

[Obtenir des détails sur les appareils gérés par la sécurité et la mobilité de base](get-details-about-managed-devices.md)