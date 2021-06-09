---
title: Stratégies de conformité des appareils pour votre environnement Microsoft 365 de test d’entreprise
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
description: Utilisez ce guide de laboratoire de test pour ajouter des stratégies de conformité d’appareil Intune à votre Microsoft 365 environnement de test d’entreprise.
ms.openlocfilehash: d42c9a603ca581941cb5a8f30b9ecd9d6f780759
ms.sourcegitcommit: 001e64f89f9c3cd6bbd4a25459f5bee3b966820c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "49367094"
---
# <a name="device-compliance-policies-for-your-microsoft-365-for-enterprise-test-environment"></a>Stratégies de conformité des appareils pour votre environnement Microsoft 365 de test d’entreprise

*Ce Guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Cet article explique comment ajouter une stratégie de conformité des appareils Intune pour les appareils Windows 10 et les Applications Microsoft 365 pour les grandes entreprises à votre environnement de test Microsoft 365 entreprise.

L’ajout d’une stratégie de conformité d’appareil Intune implique deux phases :
- [Phase 1 : Créer votre environnement de test Microsoft 365 entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Création d’une stratégie de conformité des appareils Windows 10 appareils](#phase-2-create-a-device-compliance-policy-for-windows-10-devices)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile Microsoft 365 guide de laboratoire de test pour entreprise, Microsoft 365 pour la pile de guides de laboratoire de [test d’entreprise.](../downloads/Microsoft365EnterpriseTLGStack.pdf)

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 entreprise

Si vous souhaitez configurer des stratégies DE GESTION uniquement de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère.](lightweight-base-configuration-microsoft-365-enterprise.md)
  
Si vous souhaitez configurer des stratégies MAM dans une entreprise simulée, suivez les instructions de [l’authentification directe.](pass-through-auth-m365-ent-test-environment.md)
  
> [!NOTE]
> Le test de la gestion automatisée des licences et de l’appartenance à un groupe ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt AD DS (Active Directory Domain Services). Il est fourni ici en tant qu’option afin que vous pouvez tester la gestion automatisée des licences et l’appartenance à un groupe et l’expérimenter dans un environnement qui représente une organisation classique.
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>Phase 2 : Création d’une stratégie de conformité des appareils Windows 10 appareils

Dans cette phase, vous allez créer une stratégie de conformité des appareils Windows 10 appareils. Cette phase utilise Microsoft Intune et le [centre d Microsoft Endpoint Manager’administration](https://go.microsoft.com/fwlink/?linkid=2109431) pour ajouter un groupe et créer une stratégie de conformité.

1. Go to the [Microsoft 365 admin center,](https://admin.microsoft.com)and sign in to your Microsoft 365 test lab subscription with your global administrator account. Sélectionnez le **Endpoint Manager’administration** centrale. Le [centre Endpoint Manager’administration](https://go.microsoft.com/fwlink/?linkid=2109431) s’ouvre.

    Si un message similaire à **Vous n’avez** pas encore activé la gestion des appareils s’affiche, sélectionnez Intune comme autorité de gestion des périphériques. Pour les étapes spécifiques, voir [Définir l’autorité de gestion des appareils mobiles.](/mem/intune/fundamentals/mdm-authority-set)

    Le Centre Endpoint Manager’administration de l’entreprise se concentre sur la gestion des appareils et des applications. Pour une visite guidée de ce centre d’administration, voir [Didacticiel : Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager)pas à pas dans Microsoft Endpoint Manager .

2. Dans **groupes,** ajoutez un  nouveau groupe **Microsoft 365** ou de sécurité nommé **Utilisateurs** Windows 10'appareil géré, avec un type **d’appartenance** affecté. Dans les étapes suivantes, vous allez affecter votre stratégie de conformité à ce groupe. 

    Pour les étapes spécifiques et pour  plus d’informations **sur Microsoft 365** ou les groupes de sécurité, voir Ajouter des groupes pour organiser les utilisateurs et [les appareils.](/mem/intune/fundamentals/groups-add)

3. Dans **Les appareils,** créez une stratégie Windows 10 conformité. Affectez cette stratégie au **groupe d’utilisateurs Windows 10 d’appareil géré** que vous avez créé.

    Dans votre stratégie, vous pouvez bloquer des mots de passe simples, exiger un pare-feu, exiger l’exécution du service anti-programme malveillant De Microsoft Defender, etc. Une stratégie de conformité inclut généralement les paramètres de base, ou un minimum minimal, pour chaque appareil.

    Pour les étapes spécifiques et pour plus d’informations sur les paramètres de conformité disponibles que vous pouvez configurer, voir Utiliser des stratégies de conformité pour définir des règles pour les appareils [que vous gérez.](/mem/intune/protect/device-compliance-get-started)

Lorsque vous avez terminé, vous avez une stratégie de conformité des appareils pour tester les membres du groupe d’utilisateurs Windows 10 **géré.**
  
## <a name="next-step"></a>Étape suivante

Explorez [d’autres fonctionnalités de gestion](m365-enterprise-test-lab-guides.md#mobile-device-management) des appareils mobiles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 guides de laboratoire de test pour entreprise.](m365-enterprise-test-lab-guides.md)
  
[Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 entreprise](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
