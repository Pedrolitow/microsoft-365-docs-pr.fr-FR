---
title: Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 Enterprise
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce guide de laboratoire de test pour ajouter des stratégies de conformité d’appareil Intune à votre environnement de test Microsoft 365 Enterprise.
ms.openlocfilehash: 5ef39310ff74e5d5a38e8a5dd8c7ca24a126af58
ms.sourcegitcommit: 584e2e9db8c541fe32624acdca5e12ee327fdb63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "44679025"
---
# <a name="device-compliance-policies-for-your-microsoft-365-enterprise-test-environment"></a>Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 Enterprise

*Ce Guide de Laboratoire Test peut uniquement être utilisé pour les environnements de test Microsoft 365 Entreprise*.

À l’aide des instructions fournies dans cet article, vous ajoutez une stratégie Intune Device Compliance pour les appareils Windows 10 et Microsoft 365 apps pour les entreprises à votre environnement de test Microsoft 365 Enterprise.

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Créer l’environnement de test Microsoft 365 Entreprise.

Si vous souhaitez simplement configurer des stratégies MAM de manière simple avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer des stratégies MAM dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des licences automatisées et l’appartenance aux groupes ne nécessitent pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester les licences automatiques et les appartenances aux groupes et de les tester dans un environnement qui représente une organisation typique. 
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>Phase 2 : créer une stratégie de conformité des appareils pour les appareils Windows 10

Au cours de cette phase, vous allez créer une stratégie de conformité des appareils pour les appareils Windows 10.
  
1. Accédez au portail Office 365 à l’adresse ( [https://portal.office.com](https://portal.office.com) ) et connectez-vous à votre abonnement de laboratoire de test office 365 avec votre compte d’administrateur général.
    
2. Dans un nouvel onglet de votre navigateur, ouvrez le portail Azure à l’adresse [https://portal.azure.com](https://portal.azure.com) .

3. Dans l’onglet portail Azure de votre navigateur, saisissez **Intune** dans la zone de recherche, puis cliquez sur **Intune**.
    
4. Si vous voyez un message « **vous n’avez pas activé la gestion des appareils activés** » dans le volet **Microsoft Intune** , cliquez sur celui-ci. Dans le volet **autorité de gestion des appareils mobiles** , cliquez sur **autorité MDM Intune**, puis sur **choisir**. Actualisez l’onglet de votre navigateur.
    
5. Dans le volet de navigation gauche, cliquez sur **Groupes**.
    
6. Dans le volet **groupes-tous les groupes** , cliquez sur **+ nouveau groupe**.
    
7. Dans le **volet groupe** , sélectionnez **Office 365** ou **sécurité** pour **type de groupe ?**, entrez **utilisateurs d’appareils Windows 10 gérés** dans **nom**, sélectionnez **attribué** dans **type d’appartenance**, puis cliquez sur **créer**. 
    
8. Cliquez sur **Microsoft Intune**. Dans le volet **Microsoft Intune** , dans la liste **tâches rapides** , cliquez sur **créer une stratégie de conformité**.
    
9. Dans le volet **profils de stratégie de conformité** , cliquez sur créer une **stratégie**.
    
10. Dans le volet **créer une stratégie** , dans **nom**, tapez **Windows 10**. Dans **plateforme**, sélectionnez **Windows 10 et versions ultérieures**, cliquez sur **OK** dans le volet **stratégie de conformité Windows 10** , puis cliquez sur **créer**. 
    
11. Cliquez sur **profils de stratégie de conformité**, puis sur le nom de la stratégie **Windows 10** .
    
12. Dans le volet **Windows 10** , cliquez sur **affectations**, puis sur **Sélectionner les groupes à inclure**.
    
13. Dans le volet **Sélectionner des groupes à inclure** , cliquez sur le groupe **utilisateurs d’appareils Windows 10 gérés** , puis cliquez sur **Sélectionner**.
    
14. Cliquez sur **Enregistrer**, sur **Microsoft Intune-vue d’ensemble**, puis sur **applications clientes** dans le volet de navigation de gauche.
    
15. Dans le volet **applications client** , cliquez sur **applications**, puis sur **Ajouter**. 

16. Dans le volet **Ajouter une application** , sélectionnez type d' **application**, puis sélectionnez **Windows 10** sous la **suite Office 365**.

17. Dans le volet **Ajouter une application** , sélectionnez **informations sur la suite d’applications**.
 
18. Dans le volet d’informations de la **suite d’applications** , tapez **Microsoft 365 apps pour entreprises** dans les descriptions **nom** et **suite**de la suite.
Cliquez sur OK.

19. Dans le volet **Ajouter une application** , sélectionnez configurer une suite d' **applications**, puis cliquez sur **OK**.

20. Dans le volet **Ajouter une application** , sélectionnez Paramètres de la suite d' **applications**.

21. Pour **canal de mise à jour**, sélectionnez **entreprise semi-annuelle**, puis cliquez sur **OK**.

22. Dans le volet **Ajouter une application** , cliquez sur **Ajouter**.

Vous disposez maintenant d’une stratégie de conformité de l’appareil pour tester les applications sélectionnées dans la stratégie de conformité des appareils **Windows 10** et pour les membres du groupe **utilisateurs d’appareils Windows 10 gérés** . Notez que si vous sélectionnez Office 365 comme type de groupe, des ressources supplémentaires seront créées. 
  
## <a name="next-step"></a>Étape suivante

Explorez les fonctionnalités supplémentaires de [gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Enterprise](m365-enterprise-test-lab-guides.md).
  
[Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 Enterprise](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
