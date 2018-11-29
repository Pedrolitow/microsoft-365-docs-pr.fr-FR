---
title: Inscription d’appareils iOS et Android dans votre environnement de test Microsoft 365 Entreprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Utilisez ce Guide de laboratoire de Test pour inscrire des périphériques dans votre environnement de test Microsoft 365 et les gérer à distance.
ms.openlocfilehash: 98696104ee8453adb7449980cf439eeb152aeea9
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866976"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-test-environment"></a>Inscription d’appareils iOS et Android dans votre environnement de test Microsoft 365 Entreprise

En suivant les instructions fournies dans cet article, vous serez en mesure de s’inscrire et tester les fonctionnalités de gestion de base des périphériques mobiles pour les périphériques iOS ou Android dans votre environnement de test Microsoft 365 pour entreprises.

![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Création de votre environnement de test Microsoft 365 pour entreprises

Si vous souhaitez simplement inscrire les périphériques iOS ou Android de manière léger avec la configuration minimale requise, suivez les instructions de [configuration de base léger](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez inscrire les périphériques iOS ou Android dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test automatisé de gestion des licences et l’appartenance au groupe ne nécessite pas de l’environnement de test simulé entreprise, qui comprend un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est fourni ici en tant qu’option afin que vous puissiez licences automatisé et l’appartenance au groupe de test et tester dans un environnement qui représente une organisation classique. 
>  

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Phase 2 : Inscrire vos périphériques iOS ou Android

Tout d’abord, suivez les instructions fournies dans [installer et se connecter à l’application de portail d’entreprise](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) pour personnaliser l’application de portail d’entreprise Microsoft Intune pour votre environnement de test.

Ensuite, suivez les instructions de [configurer l’accès aux ressources de votre société](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) à inscrire un périphérique iOS.

Ensuite, suivez les instructions dans [l’inscription de votre appareil Android dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) pour inscrire un appareil Android.

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Phase 3 : Gérer vos périphériques iOS ou Android à distance

Intune Microsoft fournit à distance verrouillage et code secret réinitialisation de fonctionnalités. Si une personne perd leur appareil, vous pouvez verrouiller le périphérique à distance. Si une personne oublie son code confidentiel, vous pouvez le réinitialiser à distance.
  
Pour verrouiller une iOS ou un appareil Android à distance :

1. Connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) avec les informations d’identification de votre compte d’administrateur global.
2. Cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.
3. Cliquez sur **périphériques > tous les périphériques**.
4. Dans la liste des périphériques, cliquez sur un appareil Android ou sur iOS, puis cliquez sur l’action **Verrouiller à distance** .

    
Pour réinitialiser le code secret à distance, procédez comme suit :

1. Si nécessaire, connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) avec les informations d’identification de votre compte d’administrateur global.
2. Cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.
3. Cliquez sur **périphériques > tous les périphériques**.
4. Dans la liste des périphériques gérer, cliquez sur un appareil Android ou sur iOS et choisissez **... Plus**. Puis sélectionnez l’action **Supprimer le code secret** périphérique à distance.

Pour une expérimentation supplémentaire, voir [actions de périphérique disponible](https://docs.microsoft.com/intune/device-management#available-device-actions).

    
## <a name="next-step"></a>Étape suivante

Explorez des fonctionnalités de [Gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)
  
[Stratégies GAM pour votre environnement de test Microsoft 365 Entreprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
