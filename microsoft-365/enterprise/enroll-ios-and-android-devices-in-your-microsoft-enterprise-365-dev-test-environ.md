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
ms.openlocfilehash: 3736934dbb62e84aad6a91fcd1d65b4a47ef8637
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487695"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 pour les entreprises

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Cet article explique comment inscrire et tester les fonctionnalités de base de gestion des appareils mobiles pour les appareils iOS et Android dans votre environnement de test Microsoft 365 pour les entreprises.

L’enregistrement des appareils iOS et Android dans votre environnement de test implique trois phases :
- [Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : inscrire vos appareils iOS et Android](#phase-2-enroll-your-ios-and-android-devices)
- [Phase 3 : gérer les appareils iOS et Android à distance](#phase-3-manage-your-ios-and-android-devices-remotely)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Pour obtenir un plan de tous les Articles de la pile de guide de laboratoire de test Microsoft 365 pour Enterprise, accédez à [Microsoft 365 pour la pile de guide de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises

Si vous souhaitez inscrire des appareils iOS et Android de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez inscrire des appareils iOS et Android dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des licences automatisées et l’appartenance aux groupes ne nécessitent pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester les licences automatiques et l’appartenance aux groupes, et vous pouvez l’expérimenter dans un environnement qui représente une organisation typique.

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Phase 2 : inscrire vos appareils iOS et Android

Tout d’abord, suivez les instructions de la procédure d' [installation et connectez-vous à l’application portail d’entreprise](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) pour personnaliser l’application portail d’entreprise Microsoft Intune pour votre environnement de test.

Ensuite, suivez les instructions de la procédure [configurer l’accès aux ressources de votre entreprise](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) pour inscrire un appareil iOS.

Ensuite, suivez les instructions de la procédure [inscrire votre appareil Android dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) pour inscrire un appareil Android.

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Phase 3 : gérer les appareils iOS et Android à distance

Microsoft Intune fournit des fonctionnalités de verrouillage à distance et de réinitialisation du code secret. Si une personne perd son appareil, vous pouvez verrouiller l’appareil à distance. Si une personne oublie son mot de passe, vous pouvez la réinitialiser à distance.
  
Pour verrouiller un appareil iOS ou Android à distance :

1. Connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) l’aide des informations d’identification de votre compte d’administrateur général.
2. Dans le portail Azure, entrez **Intune** dans la zone de recherche, puis sélectionnez **Intune**.
3. Cliquez sur **périphériques > tous les appareils**.
4. Dans la liste des périphériques, sélectionnez un appareil iOS ou Android, puis sélectionnez l’action de **verrouillage à distance** .
    
Pour réinitialiser le code secret à distance :

1. Si nécessaire, connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) l’aide des informations d’identification de votre compte d’administrateur général.
2. Dans le portail Azure, entrez **Intune** dans la zone de recherche, puis sélectionnez **Intune**.
3. Sélectionnez **périphériques**  >  **tous les appareils**.
4. Dans la liste des appareils que vous gérez, sélectionnez un appareil iOS ou Android, sélectionnez **... Plus encore**, puis sélectionnez l’action de **suppression** de l’appareil à distance.

Pour une expérience supplémentaire, consultez la rubrique [available Device actions](https://docs.microsoft.com/intune/device-management#available-device-actions).
    
## <a name="next-step"></a>Étape suivante

Explorez les fonctionnalités supplémentaires de [gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)
  
[Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 pour les entreprises](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)
