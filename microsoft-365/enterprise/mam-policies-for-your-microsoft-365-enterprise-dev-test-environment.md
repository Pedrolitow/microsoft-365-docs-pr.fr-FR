---
title: Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 pour entreprise
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/19/2020
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce guide de laboratoire de test pour ajouter Intune stratégies de conformité des appareils à votre environnement de test Microsoft 365 pour entreprise.
ms.openlocfilehash: 6d75721bd8b4fa6e707111ffd383c20770da0cda
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68178776"
---
# <a name="device-compliance-policies-for-your-microsoft-365-for-enterprise-test-environment"></a>Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 pour entreprise

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Cet article explique comment ajouter une stratégie de conformité d’appareil Intune pour Windows 10 appareils et Applications Microsoft 365 pour les grandes entreprises à votre environnement de test Microsoft 365 pour entreprise.

L’ajout d’une stratégie de conformité d’appareil Intune implique deux phases :
- [Phase 1 : Créer votre environnement de test Microsoft 365 pour entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Créer une stratégie de conformité des appareils pour les appareils Windows 10](#phase-2-create-a-device-compliance-policy-for-windows-10-devices)

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile des guides de laboratoire de test Microsoft 365 pour entreprise, accédez à [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 pour entreprise

Si vous souhaitez configurer des stratégies GAM de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer des stratégies GAM dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des licences automatisées et de l’appartenance aux groupes ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt services de domaine Active Directory (AD DS). Il est fourni ici en tant qu’option afin que vous puissiez tester la gestion automatisée des licences et l’appartenance à un groupe et l’expérimenter dans un environnement qui représente une organisation classique.
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>Phase 2 : Créer une stratégie de conformité des appareils pour les appareils Windows 10

Dans cette phase, vous créez une stratégie de conformité des appareils pour Windows 10 appareils. Cette phase utilise Microsoft Intune et le Centre d’administration [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) pour ajouter un groupe et créer une stratégie de conformité.

1. Accédez à la [Centre d'administration Microsoft 365](https://admin.microsoft.com), connectez-vous à votre abonnement de laboratoire de test Microsoft 365 avec votre compte d’administrateur général, puis sélectionnez le <a href="https://go.microsoft.com/fwlink/?linkid=2109431" target="_blank">centre d’administration Endpoint Manager</a>.

    Si un message similaire à **Vous n’avez pas encore activé la gestion des appareils** s’affiche, sélectionnez Intune en tant qu’autorité MDM. Pour connaître les étapes spécifiques, consultez [Définir l’autorité de gestion des appareils mobiles](/mem/intune/fundamentals/mdm-authority-set).

    Le centre d’administration Endpoint Manager se concentre sur la gestion des appareils et les applications. Pour une visite guidée de ce centre d’administration, consultez [didacticiel : Intune de procédure pas à pas dans Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager).

2. Dans **Les groupes**, ajoutez un nouveau groupe **Microsoft 365** ou **Sécurité** nommé **Utilisateurs de l’appareil Managed Windows 10**, avec un type d’appartenance **attribué**. Dans les étapes suivantes, vous allez affecter votre stratégie de conformité à ce groupe. 

    Pour connaître les étapes spécifiques et pour plus d’informations sur **Microsoft 365** ou les groupes **de sécurité** , consultez [Ajouter des groupes pour organiser les utilisateurs et les appareils](/mem/intune/fundamentals/groups-add).

3. Dans **Appareils**, créez une stratégie de conformité Windows 10. Affectez cette stratégie au groupe **d’utilisateurs de l’appareil Managed Windows 10** que vous avez créé.

    Dans votre stratégie, vous pouvez bloquer des mots de passe simples, exiger un pare-feu, exiger l’exécution du service Antimalware Microsoft Defender, etc. Une stratégie de conformité inclut généralement les paramètres de base, ou le strict minimum que chaque appareil doit avoir.

    Pour connaître les étapes spécifiques et pour plus d’informations sur les paramètres de conformité disponibles que vous pouvez configurer, consultez [Utiliser des stratégies de conformité pour définir des règles pour les appareils que vous gérez](/mem/intune/protect/device-compliance-get-started).

Lorsque vous avez terminé, vous disposez d’une stratégie de conformité des appareils pour tester les membres dans le groupe **Utilisateurs d’appareils Windows 10 managés**.
  
## <a name="next-step"></a>Étape suivante

Explorez d’autres fonctionnalités et fonctionnalités de [gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 pour entreprise](m365-enterprise-test-lab-guides.md).
  
[Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 pour entreprise](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
