---
title: Configurer les appareils gérés
f1.keywords:
- NOCSH
ms.author: v-kcirillo
author: cirilk
manager: scotv
ms.date: 03/18/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
description: Comment configurer des appareils gérés
ms.openlocfilehash: 91d5a8cacb967499b20e069f5005f133c1736625
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101640"
---
# <a name="set-up-managed-devices"></a>Configurer les appareils gérés

Un appareil « géré » est un appareil sous contrôle et surveillé par l’organisation. Il est donc régulièrement mis à jour et sécurisé. Le fait de disposer d’appareils sous contrôle géré est un objectif essentiel. Pour contrôler ces appareils, ils sont inscrits dans un gestionnaire d’appareils avec Intune et Azure Active Directory Premium, qui sont tous deux inclus dans Microsoft Business Premium. 

Un PC Windows 10 est considéré comme géré une fois que les utilisateurs ont effectué les deux étapes suivantes :

1. Configurez les stratégies de protection des appareils et des données dans l’[Assistant Installation](../business/set-up.md).

2. Connectez l’ordinateur à [Azure Active Directory](../business/set-up-windows-devices.md) avec son nom d’utilisateur et son mot de passe Microsoft 365. 

## <a name="enroll-devices-in-microsoft-endpoint-manager"></a>Inscrire des appareils dans Microsoft Endpoint Manager

Vous pouvez désormais inscrire des appareils dans Endpoint Manager, accéder à https://endpoint.microsoft.com et sélectionner **Appareils** > **Inscrire des appareils**. 

:::image type="content" source="media/m365bp-endpoint-manager-enroll-devices.png" alt-text="Utilisez Microsoft Endpoint Manager pour inscrire des appareils."::: 

Suivez les instructions d’inscription d’appareils spécifiques ci-dessous.

### <a name="for-windows-enrollment"></a>Pour l’inscription Windows :

1. Sélectionnez **Windows** >  **Inscription Windows**. 
1. Dans les méthodes d’inscription répertoriées, sélectionnez **Inscription automatique**.

### <a name="for-ios-enrollment"></a>Pour l’inscription iOS :

1. Sélectionnez **iOS** > **Inscription iOS**.
1. Dans la liste des stratégies, sélectionnez une stratégie pour afficher ses détails.
1. Sélectionnez **Propriétés** pour gérer la stratégie.
1. Sélectionnez **Paramètres** >  **Sécurité du système** et configurez les détails de sécurité dans Intune.
1. Examinez les profils de configuration. 
1. Créez un profil et envoyez-le aux appareils de votre organisation, si nécessaire.

### <a name="for-android-enrollment"></a>Pour l’inscription Android :

1. Sélectionnez **Android** > **Inscription Android**.
1. Choisissez **Google Play géré** et accordez à Microsoft l’autorisation d’envoyer des informations à Google.

## <a name="next-objective"></a>Objectif suivant

Utilisez les conseils suivants pour [intégrer les appareils](m365bp-onboard-devices-mdb.md).
