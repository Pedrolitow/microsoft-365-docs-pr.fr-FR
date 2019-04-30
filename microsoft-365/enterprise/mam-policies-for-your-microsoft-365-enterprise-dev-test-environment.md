---
title: Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce guide de laboratoire de test pour ajouter des stratégies de conformité d'appareil Intune à votre environnement de test Microsoft 365 Enterprise.
ms.openlocfilehash: b8c2fbe437362f72effd5ba550817f847ccbbf74
ms.sourcegitcommit: e15cf5d0d8ff3dfdc457b469992d72ac802e6434
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "33467732"
---
# <a name="device-compliance-policies-for-your-microsoft-365-enterprise-test-environment"></a>Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 Enterprise

À l'aide des instructions fournies dans cet article, vous ajoutez une stratégie Intune Device Compliance à votre environnement de test Microsoft 365 Enterprise.

![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1: créer votre environnement de test Microsoft 365 Enterprise

Si vous souhaitez simplement configurer des stratégies MAM de manière simple avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer des stratégies MAM dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des licences automatisées et l'appartenance aux groupes ne nécessitent pas l'environnement de test d'entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d'annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu'option pour vous permettre de tester les licences automatiques et les appartenances aux groupes et de les tester dans un environnement qui représente une organisation typique. 
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>Phase 2: créer une stratégie de conformité des appareils pour les appareils Windows 10

Au cours de cette phase, vous allez créer une stratégie de conformité des appareils pour les appareils Windows 10.
  
1. Accédez au portail Office 365 à l'adresse[https://portal.office.com](https://portal.office.com)() et connectez-vous à votre abonnement de laboratoire de test Office 365 avec votre compte d'administrateur général.
    
2. Dans un nouvel onglet de votre navigateur, ouvrez le portail Azure à [https://portal.azure.com](https://portal.azure.com)l'adresse.

3. Sur l'onglet portail Azure de votre navigateur, dans le volet de navigation, cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.
    
4. Si vous voyez un message « **vous n'avez pas encore activé la gestion des appareils** sur le panneau **Microsoft Intune** , cliquez dessus. Dans le panneau **autorité de gestion des appareils mobiles** , cliquez sur **autorité MDM Intune**, puis sur **choisir**. Actualisez l'onglet de votre navigateur.
    
5. Dans le volet de navigation gauche, cliquez sur **Groupes**.
    
6. Dans le panneau **groupes-tous les groupes** , cliquez sur **+ nouveau groupe**.
    
7. Dans le **volet groupe** , sélectionnez **Office 365** ou **sécurité** pour **type de groupe?**, entrez **utilisateurs d'appareils Windows 10 gérés** dans **nom**, sélectionnez **attribué** dans **type d'appartenance**, puis cliquez sur **créer**. 
    
8. Fermez le volet **Groupe**.
    
11. Fermez le panneau **groupes-tous les groupes** .
    
12. Sur le panneau **Microsoft Intune** , dans la liste **tâches rapides** , cliquez sur **créer une stratégie de conformité**.
    
13. Dans le volet **Profils de stratégie de conformité**, cliquez sur **Créer une stratégie**.
    
14. Dans le panneau **créer une stratégie** , dans **nom**, tapez **Windows 10**. Dans **plateforme**, sélectionnez **Windows 10 et versions ultérieures**, cliquez sur **OK** dans le panneau de **stratégie de conformité Windows 10** , puis cliquez sur **créer**. Fermez la lame **Windows 10** .
    
15. Dans le panneau **profils de stratégie de conformité** , cliquez sur le nom de la stratégie **Windows 10** .
    
16. Dans le panneau **Windows 10** , cliquez sur **affectations**, puis sur Sélectionner les **groupes à inclure**.
    
17. Sur le panneau **Sélectionner les groupes à inclure** , cliquez sur le groupe **utilisateurs d'appareils Windows 10 gérés** , puis cliquez sur **Sélectionner**.
    
18. Cliquez sur **Enregistrer**, puis fermez le panneau affectations de **Windows 10** .
    
19. Fermez le volet **Profils de stratégie de conformité**.
    
20. Sur le panneau **Microsoft Intune** , cliquez sur **applications clientes** dans le volet de navigation de gauche.
    
21. Dans le panneau **applications clientes** , cliquez sur **applications**, puis sur **Ajouter**. 

22. Dans le panneau **Ajouter une application** , sélectionnez type d' **application**, puis sélectionnez **Windows 10** sous la **suite Office 365**.

23. Cliquez sur **configurer l'application suite**, puis cliquez sur **OK**.

24. Cliquez sur informations sur la **suite d'applications**, tapez **applications Office pour Windows 10** dans la **suite nom**, **applications Office pour Windows 10** dans la **Description**de la suite, puis cliquez sur **OK**.

25. Cliquez sur paramètres de la **suite d'applications**, sélectionnez **semi-annuel** dans **canal de mise à jour**, puis cliquez sur **OK**.

26. Dans le panneau **Ajouter une application** , cliquez sur **Ajouter**.

Vous disposez maintenant d'une stratégie de conformité de l'appareil pour tester les applications sélectionnées dans la stratégie de conformité des appareils **Windows 10** et pour les membres du groupe **utilisateurs d'appareils Windows 10 gérés** . Notez que si vous sélectionnez Office 365 comme type de groupe, des ressources supplémentaires seront créées. 
  
## <a name="next-step"></a>Étape suivante

Explorez les fonctionnalités supplémentaires de [gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Enterprise](m365-enterprise-test-lab-guides.md).
  
[Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 Enterprise](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
