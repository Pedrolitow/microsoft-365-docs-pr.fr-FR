---
title: Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Utilisez ce guide de laboratoire de test pour inscrire des appareils dans votre environnement de test Microsoft 365 et les gérer à distance.
ms.openlocfilehash: e653b3e6cafb6ee2eb492709a2d060c7b92a6904
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32281246"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-test-environment"></a>Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 Enterprise

En suivant les instructions fournies dans cet article, vous serez en mesure d'inscrire et de tester des fonctionnalités de gestion des appareils mobiles de base pour les appareils iOS et Android dans votre environnement de test Microsoft 365 Enterprise.

![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1: créer votre environnement de test Microsoft 365 Enterprise

Si vous souhaitez simplement inscrire des appareils iOS et Android de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez inscrire des appareils iOS et Android dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des licences automatisées et l'appartenance aux groupes ne nécessitent pas l'environnement de test d'entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d'annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu'option pour vous permettre de tester les licences automatiques et les appartenances aux groupes et de les tester dans un environnement qui représente une organisation typique. 
>  

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Phase 2: inscrire vos appareils iOS et Android

Tout d'abord, suivez les instructions de la procédure d' [installation et connectez-vous à l'application portail d'entreprise](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) pour personnaliser l'application portail d'entreprise Microsoft Intune pour votre environnement de test.

Ensuite, suivez les instructions de la procédure [configurer l'accès aux ressources de votre entreprise](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) pour inscrire un appareil iOS.

Ensuite, suivez les instructions de la procédure [inscrire votre appareil Android dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) pour inscrire un appareil Android.

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Phase 3: gérer les appareils iOS et Android à distance

Microsoft Intune fournit des fonctionnalités de verrouillage à distance et de réinitialisation du code secret. Si une personne perd son appareil, vous pouvez le verrouiller à distance. Si une personne oublie son mot de passe, vous pouvez le réinitialiser à distance.
  
Pour verrouiller un appareil iOS ou Android à distance:

1. Connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) l'aide des informations d'identification de votre compte d'administrateur général.
2. Cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.
3. Cliquez sur **périphériques _GT_ tous les appareils**.
4. Dans la liste des périphériques, cliquez sur un appareil iOS ou Android, puis sur l'action de **verrouillage à distance** .

    
Pour réinitialiser le code secret à distance, procédez comme suit :

1. Si nécessaire, connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) l'aide des informations d'identification de votre compte d'administrateur général.
2. Cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.
3. Cliquez sur **périphériques _GT_ tous les appareils**.
4. Dans la liste des appareils gérés, cliquez sur un appareil iOS ou Android, puis choisissez **... Plus encore**. Ensuite, sélectionnez l'action de **suppression** de l'appareil à distance.

Pour une expérience supplémentaire, consultez la rubrique [available Device actions](https://docs.microsoft.com/intune/device-management#available-device-actions).

    
## <a name="next-step"></a>Étape suivante

Explorez les fonctionnalités supplémentaires de [gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)
  
[Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 Enterprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
