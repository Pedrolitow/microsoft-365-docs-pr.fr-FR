---
title: Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 pour les entreprises
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
description: Utilisez ce guide de laboratoire de test pour ajouter des stratégies de conformité d’appareil Intune à votre environnement de test Microsoft 365 pour les entreprises.
ms.openlocfilehash: c1de822e5a97416bd0c672d88f2902d8986638c8
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487411"
---
# <a name="device-compliance-policies-for-your-microsoft-365-for-enterprise-test-environment"></a>Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 pour les entreprises

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Cet article explique comment ajouter une stratégie Intune de conformité des appareils pour les appareils Windows 10 et les applications Microsoft 365 pour les entreprises à votre environnement de test Microsoft 365 pour les entreprises.

L’ajout d’une stratégie Intune de conformité des appareils implique deux phases :
- [Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : créer une stratégie de conformité des appareils pour les appareils Windows 10](#phase-2-create-a-device-compliance-policy-for-windows-10-devices)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Pour obtenir un plan de tous les Articles de la pile de guide de laboratoire de test Microsoft 365 pour Enterprise, accédez à [Microsoft 365 pour la pile de guide de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises

Si vous souhaitez configurer des stratégies MAM de manière simple avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer des stratégies MAM dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des licences automatisées et l’appartenance aux groupes ne nécessitent pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester les licences automatiques et les appartenances aux groupes et de les tester dans un environnement qui représente une organisation typique.
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>Phase 2 : créer une stratégie de conformité des appareils pour les appareils Windows 10

Dans cette phase, créez une stratégie de conformité des appareils pour les appareils Windows 10.
  
1. Accédez au [Centre d’administration microsoft 365](https://admin.microsoft.com) et connectez-vous à votre abonnement de laboratoire de test Microsoft 365 avec votre compte d’administrateur général.
1. Dans un nouvel onglet de votre navigateur, ouvrez le portail Azure à l’adresse [https://portal.azure.com](https://portal.azure.com) .
1. Dans la zone de recherche du portail Azure, entrez **Intune**, puis sélectionnez **Intune**.
1. Si vous voyez un message « **vous n’avez pas activé la gestion des appareils activés** » dans le volet **Microsoft Intune** , sélectionnez-le. Dans le volet **autorité de gestion des appareils mobiles** , sélectionnez **autorité MDM Intune**, puis sélectionnez **choisir**.
1. Actualisez l’onglet de votre navigateur.
1. Dans le volet de navigation de gauche, sélectionnez **groupes**.
1. Dans le volet **groupes-tous les groupes** , sélectionnez **+ nouveau groupe**.
1. Dans le volet de **groupe** , sélectionnez **Microsoft 365** ou **sécurité** pour **type de groupe ?**, entrez **utilisateurs d’appareils Windows 10 gérés** dans **nom**, sélectionnez **attribué** dans **type d’appartenance**, puis sélectionnez **créer**.
1. Sélectionnez **Microsoft Intune**.
1. Dans le volet **Microsoft Intune** , dans la liste **tâches rapides** , sélectionnez **créer une stratégie de conformité**.
1. Dans le volet **profils de stratégie de conformité** , sélectionnez créer une **stratégie**.
1. Dans le volet **créer une stratégie** , dans **nom**, entrez **Windows 10**. Dans **plateforme**, sélectionnez **Windows 10 et versions ultérieures**, sélectionnez **OK** dans le volet **stratégie de conformité Windows 10** , puis sélectionnez **créer**.
1. Sélectionnez **profils de stratégie de conformité**, puis sélectionnez le nom de la stratégie **Windows 10** .
1. Dans le volet **Windows 10** , sélectionnez **affectations**, puis sélectionnez les **groupes à inclure**.
1. Dans le volet **Sélectionner des groupes à inclure** , sélectionnez le groupe **utilisateurs d’appareils Windows 10 gérés** , puis sélectionnez **Sélectionner**.
1. Sélectionnez **Enregistrer**, sélectionnez **Microsoft Intune-vue d’ensemble**, puis sélectionnez **applications client** dans le volet de navigation de gauche.
1. Dans le volet **applications client** , sélectionnez **applications**, puis **Ajouter**.
1. Dans le volet **Ajouter une application** , sélectionnez type d' **application**, puis sélectionnez **Windows 10** sous **Microsoft 365 suite**.
1. Dans le volet **Ajouter une application** , sélectionnez **informations sur la suite d’applications**.
1. Dans le volet d' **informations App suite** , entrez **Microsoft 365 apps pour entreprises** dans les descriptions nom et **suite**de la **suite** , puis sélectionnez **OK**.
1. Dans le volet **Ajouter une application** , sélectionnez configurer une suite d' **applications**, puis cliquez sur **OK**.
1. Dans le volet **Ajouter une application** , sélectionnez Paramètres de la suite d' **applications**.
1. Pour **canal de mise à jour**, sélectionnez **entreprise semi-annuelle**, puis sélectionnez **OK**.
1. Dans le volet **Ajouter une application** , sélectionnez **Ajouter**.

Vous disposez maintenant d’une stratégie de conformité de l’appareil pour tester les applications sélectionnées dans la stratégie de conformité des appareils **Windows 10** et pour les membres du groupe **utilisateurs d’appareils Windows 10 gérés** . Veuillez noter que la sélection de **Microsoft 365** comme type de groupe crée des ressources supplémentaires.
  
## <a name="next-step"></a>Étape suivante

Explorez les fonctionnalités supplémentaires de [gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les guides de laboratoire de test d’entreprise](m365-enterprise-test-lab-guides.md).
  
[Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 pour les entreprises](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
