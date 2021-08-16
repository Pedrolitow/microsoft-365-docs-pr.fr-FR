---
title: Inscrire des appareils iOS/iPadOS et Android dans votre environnement de test Microsoft 365 entreprise
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/19/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Utilisez ce Guide de laboratoire de test pour inscrire des appareils dans Microsoft 365 environnement de test et les gérer à distance.
ms.openlocfilehash: ee7933a5e111b33ac7d3b17c0de2ef14483f9714
ms.sourcegitcommit: e269371de759a1a747c9f292775463aa11415f25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58356743"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 entreprise

*Ce Guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Cet article explique comment inscrire et tester les fonctionnalités de gestion des appareils mobiles de base pour les appareils iOS/iPadOS et Android dans votre environnement de test Microsoft 365 entreprise.

L’inscription d’appareils iOS/iPadOS et Android dans votre environnement de test implique trois phases :
- [Phase 1 : Créer votre environnement de test Microsoft 365 entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Inscrire vos appareils iOS/iPadOS et Android](#phase-2-enroll-your-ios-and-android-devices)
- [Phase 3 : Gérer vos appareils iOS/iPadOS et Android à distance](#phase-3-manage-your-ios-and-android-devices-remotely)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile Microsoft 365 guide de laboratoire de test pour entreprise, Microsoft 365 pour la pile de guides de laboratoire de [test d’entreprise.](../downloads/Microsoft365EnterpriseTLGStack.pdf)

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 entreprise

Si vous souhaitez inscrire les appareils iOS/iPadOS et Android de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère.](lightweight-base-configuration-microsoft-365-enterprise.md)
  
Si vous souhaitez inscrire des appareils iOS/iPadOS et Android dans une entreprise simulée, suivez les instructions de [l’authentification directe.](pass-through-auth-m365-ent-test-environment.md)
  
> [!NOTE]
> Le test de la gestion automatisée des licences et de l’appartenance à un groupe ne nécessite pas l’environnement de test d’entreprise simulée, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt AD DS (Active Directory Domain Services). Il est fourni ici en tant qu’option pour que vous pouvez tester les licences automatisées et l’appartenance à un groupe, et vous pouvez l’expérimenter dans un environnement qui représente une organisation classique.

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Phase 2 : Inscrire vos appareils iOS et Android

Si vous envisagez d’utiliser une solution de gestion des périphériques mobiles (MDM) pour gérer vos appareils, vous pouvez utiliser Microsoft Intune. Lorsque vous travaillez avec un fournisseur de gestion des périphériques mobiles, y compris Intune, les appareils sont « inscrits ». Une fois inscrits, ils reçoivent les fonctionnalités et paramètres que vous configurez. 

Dans Intune, il existe plusieurs façons d’inscrire vos appareils iOS/iPadOS et Android. Vous pouvez choisir l’option d’inscription qui fonctionne le mieux pour votre organisation. Pour plus d’informations et de conseils, consultez les articles suivants :

- [Guide de déploiement : Inscrire des appareils iOS et iPadOS dans Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados)
- [Guide de déploiement : Inscrire des appareils Android dans Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android)

Si vous êtes prêt à utiliser Intune pour la gestion des appareils et que vous souhaitez obtenir des conseils, les informations suivantes peuvent vous aider :

- [Vue d’ensemble de la gestion des appareils](/mem/intune/fundamentals/what-is-device-management)
- [Didacticiel : Walkthrough Intune in Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager)
- [Guide de déploiement : installation ou déplacement vers Microsoft Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Phase 3 : Gérer vos appareils iOS et Android à distance

Microsoft Intune fonctionnalité de verrouillage à distance et de réinitialisation du code secret. Si quelqu’un perd son appareil, vous pouvez verrouiller l’appareil à distance. Si quelqu’un oublie son code secret, vous pouvez le réinitialiser à distance.

- Pour verrouiller à distance un appareil iOS/iPadOS ou Android, voir Verrouiller à distance les appareils [avec Intune.](/mem/intune/remote-actions/device-remote-lock)
- Pour réinitialiser à distance le code secret, voir Réinitialiser ou supprimer un code [secret d’appareil dans Intune.](/mem/intune/remote-actions/device-passcode-reset)

Pour les autres tâches que vous pouvez exécuter à distance, consultez [les actions de périphérique disponibles.](/mem/intune/remote-actions/device-management#available-device-actions)
    
## <a name="next-step"></a>Étape suivante

Explorez [d’autres fonctionnalités de gestion des](m365-enterprise-test-lab-guides.md#mobile-device-management) appareils mobiles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)
  
[Stratégies de conformité des appareils pour votre environnement Microsoft 365 de test d’entreprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)
