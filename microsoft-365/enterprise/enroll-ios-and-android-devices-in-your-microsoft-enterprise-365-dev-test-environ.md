---
title: Inscrire des appareils iOS/iPadOS et Android dans votre environnement de test Microsoft 365 pour entreprise
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
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Utilisez ce guide de laboratoire de test pour inscrire des appareils dans votre environnement de test Microsoft 365 et les gérer à distance.
ms.openlocfilehash: d4516ac4901cbebed494571527ea5b018299223d
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68186720"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 pour entreprise

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Cet article explique comment inscrire et tester des fonctionnalités de base de gestion des appareils mobiles pour les appareils iOS/iPadOS et Android dans votre environnement de test Microsoft 365 pour entreprise.

L’inscription d’appareils iOS/iPadOS et Android dans votre environnement de test implique trois phases :
- [Phase 1 : Créer votre environnement de test Microsoft 365 pour entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Inscrire vos appareils iOS/iPadOS et Android](#phase-2-enroll-your-ios-and-android-devices)
- [Phase 3 : Gérer vos appareils iOS/iPadOS et Android à distance](#phase-3-manage-your-ios-and-android-devices-remotely)

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile des guides de laboratoire de test Microsoft 365 pour entreprise, accédez à [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 pour entreprise

Si vous souhaitez inscrire des appareils iOS/iPadOS et Android de manière légère avec la configuration minimale requise, suivez les instructions de [la configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez inscrire des appareils iOS/iPadOS et Android dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des licences automatisées et de l’appartenance aux groupes ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt services de domaine Active Directory (AD DS). Il est fourni ici en tant qu’option pour vous permettre de tester la gestion automatisée des licences et l’appartenance aux groupes, et vous pouvez l’expérimenter dans un environnement qui représente une organisation classique.

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Phase 2 : Inscrire vos appareils iOS et Android

Si vous envisagez une solution de gestion des appareils mobiles (GPM) pour gérer vos appareils, vous pouvez utiliser Microsoft Intune. Lorsque vous travaillez avec n’importe quel fournisseur GPM, y compris Intune, les appareils sont « inscrits ». Une fois inscrits, ils reçoivent les fonctionnalités et les paramètres que vous configurez. 

Dans Intune, il existe plusieurs façons d’inscrire vos appareils iOS/iPadOS et Android. Vous pouvez choisir l’option d’inscription qui convient le mieux à votre organisation. Pour plus d’informations et de conseils, consultez les articles suivants :

- [Guide de déploiement : inscrire des appareils iOS et iPadOS dans Microsoft Intune.](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados)
- [Guide de déploiement : inscrire des appareils Android dans Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android)

Si vous êtes prêt à utiliser Intune pour la gestion des appareils et que vous souhaitez obtenir des conseils, les informations suivantes peuvent vous aider :

- [Vue d’ensemble de la gestion des appareils](/mem/intune/fundamentals/what-is-device-management)
- [Tutoriel : Procédure pas à pas Intune dans Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager)
- [Guide de déploiement : configurer ou passer à Microsoft Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Phase 3 : Gérer vos appareils iOS et Android à distance

Microsoft Intune fournit la fonctionnalité de verrouillage à distance et de réinitialisation du code secret. Si quelqu’un perd son appareil, vous pouvez le verrouiller à distance. Si quelqu’un oublie son code secret, vous pouvez le réinitialiser à distance.

- Pour verrouiller à distance un appareil iOS/iPadOS ou Android, consultez Verrouillage à distance [des appareils avec Intune](/mem/intune/remote-actions/device-remote-lock).
- Pour réinitialiser à distance le code secret, consultez [Réinitialiser ou supprimer un code secret d’appareil dans Intune](/mem/intune/remote-actions/device-passcode-reset).

Pour des tâches supplémentaires que vous pouvez exécuter à distance, consultez [les actions d’appareil disponibles](/mem/intune/remote-actions/device-management#available-device-actions).
    
## <a name="next-step"></a>Étape suivante

Explorez d’autres fonctionnalités et fonctionnalités de [gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)
  
[Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 pour entreprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)
