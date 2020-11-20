---
title: Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 pour les entreprises
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce guide de laboratoire de test pour ajouter des stratégies de conformité d’appareil Intune à votre environnement de test Microsoft 365 pour les entreprises.
ms.openlocfilehash: d42c9a603ca581941cb5a8f30b9ecd9d6f780759
ms.sourcegitcommit: 001e64f89f9c3cd6bbd4a25459f5bee3b966820c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "49367094"
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

Au cours de cette phase, vous allez créer une stratégie de conformité des appareils pour les appareils Windows 10. Cette phase utilise Microsoft Intune et le [Centre d’administration du gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) pour ajouter un groupe et créer une stratégie de conformité.

1. Accédez au [Centre d’administration microsoft 365](https://admin.microsoft.com), puis connectez-vous à votre abonnement de laboratoire de test Microsoft 365 avec votre compte d’administrateur général. Sélectionnez le centre d’administration du **Gestionnaire de point de terminaison** . Le [Centre d’administration du gestionnaire de point de terminaison](https://go.microsoft.com/fwlink/?linkid=2109431) s’ouvre.

    Si un message similaire à celui **que vous n’avez pas activé la gestion des appareils** , un message s’affiche, puis sélectionnez Intune comme autorité MDM. Pour connaître les étapes spécifiques, reportez-vous à [la rubrique Set the Mobile Device Management Authority](/mem/intune/fundamentals/mdm-authority-set).

    Le centre d’administration du gestionnaire de point de terminaison est axé sur la gestion des applications et des applications. Pour une visite guidée de ce centre d’administration, consultez la rubrique [Tutorial : Walkthrough Intune in Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager).

2. Dans **groupes**, ajoutez un nouveau groupe de sécurité ou un groupe de **sécurité** **Microsoft 365** nommé **utilisateurs d’appareils Windows 10 gérés**, avec un type d’appartenance **affecté** . Dans les étapes suivantes, vous allez affecter votre stratégie de conformité à ce groupe. 

    Pour connaître les étapes spécifiques, et pour plus d’informations sur **Microsoft 365** ou sur les groupes de **sécurité** , consultez la rubrique [Add Groups to organi Users and Devices](/mem/intune/fundamentals/groups-add).

3. Dans **appareils**, créez une stratégie de conformité Windows 10. Affectez cette stratégie au groupe d' **utilisateurs d’appareils Windows 10 géré** que vous avez créé.

    Dans votre stratégie, vous pouvez bloquer les mots de passe simples, exiger un pare-feu, exiger que le service anti-programme malveillant de Microsoft Defender soit en cours d’exécution, et plus encore. En règle générale, une stratégie de conformité inclut les paramètres de base ou le minimum absolu que chaque appareil doit avoir.

    Pour connaître les étapes spécifiques, et pour plus d’informations sur les paramètres de conformité disponibles que vous pouvez configurer, reportez-vous à la rubrique [utiliser des stratégies de conformité pour définir des règles pour les appareils que vous gérez](/mem/intune/protect/device-compliance-get-started).

Lorsque vous avez terminé, vous disposez d’une stratégie de conformité de l’appareil pour tester les membres dans le groupe **utilisateurs d’appareils Windows 10 gérés** .
  
## <a name="next-step"></a>Étape suivante

Explorez les fonctionnalités supplémentaires de [gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les guides de laboratoire de test d’entreprise](m365-enterprise-test-lab-guides.md).
  
[Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 pour les entreprises](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
