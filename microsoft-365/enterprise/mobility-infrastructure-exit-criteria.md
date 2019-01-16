---
title: Critères de sortie de l’infrastructure de gestion appareil mobile
description: Microsoft 365 entreprise inclut la gestion des appareils mobiles à l’aide de Microsoft Intune. Passez en revue les exigences et les conditions préalables, configurer Intune à l’aide de vos ressources Azure Active Directory, inscrivez iOS, Mac OS, Android et Windows appareils, déployer des applications, créer un profil de configuration, utilisez une stratégie de conformité et activer l’accès mobile conditionnelle gestion des périphériques avec Microsoft 365 pour entreprises.
keywords: Documentation Microsoft 365, Microsoft 365 pour entreprises, Microsoft 365, gestion des appareils mobiles, Intune
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/10/2018
ms.topic: article
audience: ITPro
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.assetid: fb4182e6-5e78-45d0-9641-d791c4519441
ms.custom: microsoft-intune
ms.openlocfilehash: b511052698f42a07df5fc25aeaad7fc7f00c2a6e
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867010"
---
# <a name="mobile-device-management-infrastructure-exit-criteria"></a>Critères de sortie de l’infrastructure de gestion appareil mobile

![](./media/deploy-foundation-infrastructure/mobiledevicemgmt_icon-small.png)

*Cela s’applique aux versions de Microsoft 365 entreprise E3 et E5*

Avant de passer à la phase suivante du processus de déploiement, assurez-vous que votre configuration remplit les conditions suivantes pour l’infrastructure de gestion des appareils mobiles.

- Intune est configuré, y compris la création des utilisateurs et des groupes Azure AD, pour appliquer les règles de votre organisation à vos appareils.
- Vous avez inscrit des appareils dans Intune pour qu’ils reçoivent les stratégies que vous créez.
- Les applications sont ajoutées aux appareils pour permettre à vos utilisateurs d’accéder aux services cloud Microsoft 365 de votre organisation, comme Exchange Online et SharePoint Online.
- Les fonctionnalités et les paramètres sont configurés et appliqués à vos appareils à l’aide des utilisateurs et des groupes Azure AD créés. Parmi ces fonctionnalités et paramètres peuvent figurer l’activation de l’antivirus et la limitation de certaines applications.
- Des stratégies de conformité sont implémentées pour exiger un pare-feu ou une longueur de mot de passe sur un appareil. Si des appareils ne sont pas conformes, l’accès conditionnel bloque l’accès aux données de votre organisation.

## <a name="next-phase"></a>Phase suivante

|||
|:-------|:-----|
|![](./media/deploy-foundation-infrastructure/infoprotection_icon-small.png)| La phase suivante du processus de déploiement de bout en bout Microsoft 365 entreprise est [la protection des informations](infoprotect-infrastructure.md). |
