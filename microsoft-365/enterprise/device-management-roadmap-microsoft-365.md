---
title: Gestion des appareils mobiles pour Microsoft 365
keywords: Microsoft 365, Microsoft 365 pour les entreprises, documentation Microsoft 365, gestion des appareils mobiles, Intune
author: kelleyvice-msft
ms.author: kvice
manager: scotv
ms.date: 08/10/2020
ms.topic: conceptual
f1.keywords:
- NOCSH
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.assetid: fb4182e6-5e78-45d0-9641-d791c4519441
audience: ITPro
ms.custom: microsoft-intune
description: Feuille de route pour configurer la gestion des appareils pour Microsoft 365.
ms.openlocfilehash: eeed1a69fc1724f3feb75f4bc096cad3a3c25cf0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095309"
---
# <a name="device-management-roadmap-for-microsoft-365"></a>Gestion des appareils mobiles pour Microsoft 365

Microsoft 365 pour l’entreprise inclut des fonctionnalités permettant de gérer les appareils et leurs applications au sein de votre organisation. La gestion des appareils mobiles vous permet de sécuriser et de protéger les ressources de votre organisation.

Il existe deux options pour la gestion des appareils :

- [Microsoft Intune](#microsoft-intune)
- [Mobility + Security de Base](#basic-mobility-and-security)

## <a name="microsoft-intune"></a>Microsoft Intune

Vous pouvez utiliser Microsoft Intune pour gérer l’accès à votre organisation à l’aide de la gestion des appareils mobiles ou de la gestion des applications mobiles. La gestion des appareils mobiles se fait lorsque les utilisateurs « inscrivent » leurs appareils dans Intune. Une fois qu’un appareil est inscrit, il s’agit d’un appareil géré ; par conséquent, il peut recevoir les stratégies, les règles et les paramètres de votre organisation. Par exemple, vous pouvez installer des applications spécifiques, créer une stratégie de mot de passe, installer une connexion VPN, etc.

Les utilisateurs avec leurs propres appareils personnels peuvent ne pas vouloir inscrire leurs appareils ou être gérés par Intune et les stratégies de votre organisation. Toutefois, vous devez toujours protéger les ressources et les données de votre organisation. Dans ce scénario, vous pouvez protéger vos applications à l’aide de la gestion des applications mobiles. Par exemple, vous pouvez utiliser une stratégie de gestion des applications mobiles qui exige qu’un utilisateur entre un code confidentiel lors de l’accès à SharePoint Online sur l’appareil.

Vous allez également déterminer comment gérer les appareils personnels et les appareils appartenant à l’organisation. Vous souhaiterez peut-être traiter les appareils différemment, en fonction de leurs utilisations.

## <a name="basic-mobility-and-security"></a>Mobility + Security de Base

Il est intégré à Microsoft 365 et vous permet de sécuriser et de gérer les appareils mobiles de vos utilisateurs, tels que les iPhone, les iPad, les Android et les téléphones Windows. Vous pouvez créer et gérer des stratégies de sécurité des appareils, réinitialiser un appareil à distance et afficher des rapports détaillés sur les appareils.

## <a name="choose-between-the-two-options"></a>Choisir entre les deux options

Pour vous aider à mieux évaluer l’option de gestion des appareils qui vous convient le mieux, consultez [Choisir entre Sécurité de la mobilité de base et Intune](/office365/securitycompliance/choose-between-mdm-and-intune).

En fonction de votre évaluation, commencez à gérer vos appareils avec :

- [Intune](/microsoft-365/solutions/manage-devices-with-intune-overview)
- [Mobility + Security de Base](https://support.microsoft.com/office/set-up-basic-mobility-and-security-dd892318-bc44-4eb1-af00-9db5430be3cd)
 
## <a name="identity-and-device-access-recommendations"></a>Recommandations en matière d’identité et d’accès aux appareils

Microsoft fournit un ensemble de recommandations sur l’[accès aux appareils et à l’identité](../security/office-365-security/microsoft-365-policies-configurations.md) pour garantir un personnel conforme et productif. Pour l’accès aux appareils, utilisez les recommandations et les paramètres de ces articles :

- [Conditions préalables](../security/office-365-security/identity-access-prerequisites.md)
- [Stratégies communes pour les identités et l’accès aux appareils](../security/office-365-security/identity-access-policies.md)

## <a name="how-contoso-did-device-management-for-microsoft-365"></a>Comment Contoso a-t-il effectué la gestion des appareils pour Microsoft 365

Pour plus d’informations sur la façon dont une entreprise multinationale fictive mais représentative a déployé son infrastructure de gestion des appareils mobiles avec Microsoft 365 services cloud, consultez [La gestion des appareils mobiles pour Contoso](contoso-mdm.md).