---
title: Critères de sortie de l'infrastructure de gestion des appareils mobiles
description: Microsoft 365 Enterprise inclut la gestion des appareils mobiles à l'aide de Microsoft Intune. Passez en revue les conditions requises et les conditions préalables, configurez Intune à l'aide de votre ressource Azure Active Directory, inscrivez iOS, macOS, Android et appareils Windows, déployer des applications, créer un profil, utiliser une stratégie de conformité et activer l'accès conditionnel pour les appareils mobiles gestion des appareils avec Microsoft 365 Enterprise.
keywords: Microsoft 365, Microsoft 365 entreprise, documentation Microsoft 365, gestion des appareils mobiles, Intune
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2019
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.assetid: fb4182e6-5e78-45d0-9641-d791c4519441
audience: ITPro
ms.custom: microsoft-intune
ms.openlocfilehash: 14f216fe352d9108fe69028731f4c94dfb9d19f7
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32291231"
---
# <a name="mobile-device-management-infrastructure-exit-criteria"></a>Critères de sortie de l'infrastructure de gestion des appareils mobiles

![](./media/deploy-foundation-infrastructure/mobiledevicemgmt_icon-small.png)

*Cela s'applique aux versions E3 et E5 de Microsoft 365 entreprise*

Assurez-vous que votre configuration remplit les conditions suivantes pour l'infrastructure de gestion des appareils mobiles.

- Intune est configuré, y compris la création des utilisateurs et des groupes Azure AD, pour appliquer les règles de votre organisation à vos appareils.
- Vous avez inscrit des appareils dans Intune pour qu’ils reçoivent les stratégies que vous créez.
- Les applications sont ajoutées aux appareils pour permettre à vos utilisateurs d’accéder aux services cloud Microsoft 365 de votre organisation, comme Exchange Online et SharePoint Online.
- Les fonctionnalités et les paramètres sont configurés et appliqués à vos appareils à l’aide des utilisateurs et des groupes Azure AD créés. Parmi ces fonctionnalités et paramètres peuvent figurer l’activation de l’antivirus et la limitation de certaines applications.
- Des stratégies de conformité sont implémentées pour exiger un pare-feu ou une longueur de mot de passe sur un appareil. Si des appareils ne sont pas conformes, l’accès conditionnel bloque l’accès aux données de votre organisation.



## <a name="results-and-next-steps"></a>Résultats et étapes suivantes

Vos appareils sont intégrés dans Intune et configurés avec les stratégies appropriées.

|||
|:-------|:-----|
|![](./media/deploy-foundation-infrastructure/infoprotection_icon-small.png)| Si vous suivez les phases du déploiement de bout en bout de Microsoft 365 entreprise, votre phase suivante est la protection des [informations](infoprotect-infrastructure.md). |
