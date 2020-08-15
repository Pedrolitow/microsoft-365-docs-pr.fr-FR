---
title: Feuille de route de gestion des appareils pour Microsoft 365
keywords: Microsoft 365, Microsoft 365 pour Enterprise, documentation Microsoft 365, gestion des appareils mobiles, Intune
author: JoeDavies-MSFT
ms.author: josephd
manager: laurawi
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
description: La feuille de route pour configurer la gestion des appareils pour Microsoft 365.
ms.openlocfilehash: 1c5a06c75ede11697e2ecf17c47eb035e78dcd27
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46689848"
---
# <a name="device-management-roadmap-for-microsoft-365"></a>Feuille de route de gestion des appareils pour Microsoft 365


Microsoft 365 for Enterprise inclut des fonctionnalités qui permettent de gérer les appareils et leurs applications au sein de votre organisation. La gestion des appareils mobiles vous permet de sécuriser et de protéger les ressources de votre organisation.

Il existe deux options pour la gestion des appareils.

## <a name="microsoft-intune"></a>Microsoft Intune

Intune vous offre des options pour gérer l’accès à votre organisation à l’aide de la gestion des appareils mobiles (MDM) ou de la gestion des applications mobiles (MAM). MDM est lorsque les utilisateurs « inscrivent » leurs appareils dans Intune. Une fois l’enregistrement effectué, il s’agit d’appareils gérés et peut recevoir toutes les stratégies, les règles et les paramètres utilisés par votre organisation. Par exemple, vous pouvez installer des applications spécifiques, créer une stratégie de mot de passe, installer une connexion VPN, et bien plus encore.

Les utilisateurs disposant de leurs propres appareils personnels peuvent ne pas vouloir inscrire leurs appareils ou être gérés par Intune et vos stratégies. Toutefois, vous devez toujours protéger les ressources et les données de votre organisation. Dans ce scénario, vous pouvez protéger vos applications à l’aide de MAM. Par exemple, vous pouvez utiliser une stratégie MAM qui exige qu’un utilisateur entre un code confidentiel lors de l’accès à SharePoint sur l’appareil.

Vous allez également déterminer la manière dont vous allez gérer les appareils personnels ou appartenant à l’organisation. Vous souhaiterez peut-être traiter les appareils différemment en fonction de leur utilisation. 

Démarrez [ici](https://docs.microsoft.com/mem/intune/fundamentals/planning-guide).

## <a name="basic-mobility-and-security"></a>Mobilité et sécurité de base
 
Il est intégré à Microsoft 365 et vous aide à sécuriser et gérer les appareils mobiles de vos utilisateurs, tels que les iPhone, les iPad, les Android et les téléphones Windows. Vous pouvez créer et gérer des stratégies de sécurité des appareils, réinitialiser un appareil à distance et afficher des rapports détaillés sur les appareils. 

Démarrez [ici](https://support.microsoft.com/office/set-up-basic-mobility-and-security-dd892318-bc44-4eb1-af00-9db5430be3cd).
 
## <a name="identity-and-device-access-recommendations"></a>Recommandations en matière d’identité et d’accès aux appareils

Microsoft fournit un ensemble de recommandations sur l’[accès aux appareils et à l’identité](microsoft-365-policies-configurations.md) pour garantir un personnel conforme et productif. Pour l’accès aux appareils, utilisez les recommandations et les paramètres présentés dans les articles suivants, ainsi que les étapes de cette phase :

- [Conditions préalables](identity-access-prerequisites.md)
- [Stratégies communes pour les identités et l’accès aux appareils](identity-access-policies.md)

## <a name="how-microsoft-does-device-management-for-microsoft-365"></a>Comment Microsoft effectue la gestion des appareils pour Microsoft 365

Découvrez comment les experts informatiques de Microsoft [gèrent les appareils avec EMS](https://www.microsoft.com/itshowcase/deploying-and-managing-microsoft-365#primaryR8).

## <a name="how-contoso-did-device-management-for-microsoft-365"></a>Comment Contoso a fait la gestion des appareils pour Microsoft 365

Découvrez comment Contoso Corporation, une entreprise multinationale fictive mais représentative, a [déployé son infrastructure de gestion des appareils mobiles](contoso-mdm.md) avec les services Cloud de Microsoft 365.

![Société Contoso](../media/contoso-overview/contoso-icon.png)
