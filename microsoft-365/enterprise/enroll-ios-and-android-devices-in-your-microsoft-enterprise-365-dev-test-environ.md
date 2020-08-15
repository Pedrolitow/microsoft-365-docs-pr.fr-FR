---
title: Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 pour les entreprises
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Utilisez ce guide de laboratoire de test pour inscrire des appareils dans votre environnement de test Microsoft 365 et les gérer à distance.
ms.openlocfilehash: b4a95b2c7e58239c0a8d0d3b5045e7337f43de6b
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46686009"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 pour les entreprises

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

En suivant les instructions fournies dans cet article, vous serez en mesure d’inscrire et de tester des fonctionnalités de gestion des appareils mobiles de base pour les appareils iOS et Android dans votre environnement de test Microsoft 365 pour les entreprises.

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Cliquez [ici](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan visuel de tous les articles de l’ensemble des guides de laboratoire de test de Microsoft 365 pour entreprise.

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises

Si vous souhaitez simplement inscrire des appareils iOS et Android de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez inscrire des appareils iOS et Android dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des licences automatisées et l’appartenance aux groupes ne nécessitent pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester les licences automatiques et les appartenances aux groupes et de les tester dans un environnement qui représente une organisation typique. 
>  

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Phase 2 : inscrire vos appareils iOS et Android

Tout d’abord, suivez les instructions de la procédure d' [installation et connectez-vous à l’application portail d’entreprise](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) pour personnaliser l’application portail d’entreprise Microsoft Intune pour votre environnement de test.

Ensuite, suivez les instructions de la procédure [configurer l’accès aux ressources de votre entreprise](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) pour inscrire un appareil iOS.

Ensuite, suivez les instructions de la procédure [inscrire votre appareil Android dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) pour inscrire un appareil Android.

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Phase 3 : gérer les appareils iOS et Android à distance

Microsoft Intune fournit des fonctionnalités de verrouillage à distance et de réinitialisation du code secret. Si une personne perd son appareil, vous pouvez le verrouiller à distance. Si une personne oublie son mot de passe, vous pouvez le réinitialiser à distance.
  
Pour verrouiller un appareil iOS ou Android à distance :

1. Connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) l’aide des informations d’identification de votre compte d’administrateur général.
2. Dans l’onglet portail Azure de votre navigateur, tapez **Intune** dans la zone de recherche, puis cliquez sur **Intune**.
3. Cliquez sur **périphériques > tous les appareils**.
4. Dans la liste des périphériques, cliquez sur un appareil iOS ou Android, puis sur l’action de **verrouillage à distance** .

    
Pour réinitialiser le code secret à distance, procédez comme suit :

1. Si nécessaire, connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) l’aide des informations d’identification de votre compte d’administrateur général.
2. Dans l’onglet portail Azure de votre navigateur, tapez **Intune** dans la zone de recherche, puis cliquez sur **Intune**.
3. Cliquez sur **périphériques > tous les appareils**.
4. Dans la liste des appareils gérés, cliquez sur un appareil iOS ou Android, puis choisissez **... Plus encore**. Ensuite, sélectionnez l’action de **suppression** de l’appareil à distance.

Pour une expérience supplémentaire, consultez la rubrique [available Device actions](https://docs.microsoft.com/intune/device-management#available-device-actions).

    
## <a name="next-step"></a>Étape suivante

Explorez les fonctionnalités supplémentaires de [gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)
  
[Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 pour les entreprises](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

