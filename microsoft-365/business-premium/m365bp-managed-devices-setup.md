---
title: Configurer les appareils gérés
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection:
- M365-Campaigns
- m365solution-smb
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
description: Comment configurer des appareils gérés
ms.openlocfilehash: a4298bcdc284f1957a1afa73cbc7ae8e3f15e7d1
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2022
ms.locfileid: "66895006"
---
# <a name="set-up-managed-devices"></a>Configurer les appareils gérés

Un appareil « géré » est un appareil sous contrôle et surveillé par l’organisation. Il est donc régulièrement mis à jour et sécurisé. Le fait de disposer d’appareils sous contrôle géré est un objectif essentiel. Pour contrôler ces appareils, ils sont inscrivez-les dans un gestionnaire d’appareils avec Microsoft Intune et Azure Active Directory Premium, qui sont tous deux inclus dans Microsoft Business Premium.

1. Configurez les stratégies de protection des appareils et des données dans l’[Assistant Installation](../business/set-up.md).

2. Connectez l’ordinateur à [Azure Active Directory](../business/set-up-windows-devices.md) avec son nom d’utilisateur et son mot de passe Microsoft 365. 

## <a name="enroll-devices-in-intune"></a>Inscrire des appareils dans Intune

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Sélectionnez **Appareils** > **Inscrire des appareils**. 

   :::image type="content" source="media/m365bp-endpoint-manager-enroll-devices.png" alt-text="Utilisez Microsoft Endpoint Manager pour inscrire des appareils."::: 

3. Suivez les instructions d’inscription d’appareils spécifiques ci-dessous.

### <a name="for-windows-enrollment"></a>Pour l’inscription Windows :

1. Sélectionnez **Windows** >  **Inscription Windows**. 

2. Dans les méthodes d’inscription répertoriées, sélectionnez **Inscription automatique**.

### <a name="for-ios-enrollment"></a>Pour l’inscription iOS :

1. Sélectionnez **iOS** > **Inscription iOS**.

2. Dans la liste des stratégies, sélectionnez une stratégie pour afficher ses détails.

3. Sélectionnez **Propriétés** pour gérer la stratégie.

4. Sélectionnez **Paramètres** >  **Sécurité du système** et configurez les détails de sécurité dans Intune.

5. Examinez les profils de configuration. 

6. Créez un profil et envoyez-le aux appareils de votre organisation, si nécessaire.

### <a name="for-android-enrollment"></a>Pour l’inscription Android :

1. Sélectionnez **Android** > **Inscription Android**.

2. Choisissez **Google Play géré** et accordez à Microsoft l’autorisation d’envoyer des informations à Google.

## <a name="next-objective"></a>Objectif suivant

Suivez les instructions suivantes pour [intégrer des appareils vers les fonctionnalités de Defender for Business](m365bp-onboard-devices-mdb.md).

