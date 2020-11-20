---
title: Inscrire des appareils iOS/iPad et Android dans votre environnement de test Microsoft 365 pour les entreprises
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
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Utilisez ce guide de laboratoire de test pour inscrire des appareils dans votre environnement de test Microsoft 365 et les gérer à distance.
ms.openlocfilehash: 06f83d1ed61bcc530b6aa974d7730f1aadc0ecbd
ms.sourcegitcommit: 001e64f89f9c3cd6bbd4a25459f5bee3b966820c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "49367082"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>Inscrire des appareils iOS et Android dans votre environnement de test Microsoft 365 pour les entreprises

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Cet article explique comment inscrire et tester des fonctionnalités de gestion des appareils mobiles de base pour les appareils iOS/iPad et Android dans votre environnement de test Microsoft 365 pour les entreprises.

L’enregistrement d’appareils iOS/iPad et Android dans votre environnement de test implique trois phases :
- [Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : inscrire vos appareils iOS/iPad et Android](#phase-2-enroll-your-ios-and-android-devices)
- [Phase 3 : gérer les appareils iOS/iPad et Android à distance](#phase-3-manage-your-ios-and-android-devices-remotely)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Pour obtenir un plan de tous les Articles de la pile de guide de laboratoire de test Microsoft 365 pour Enterprise, accédez à [Microsoft 365 pour la pile de guide de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises

Si vous souhaitez inscrire des appareils iOS/iPad et Android de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez inscrire des appareils iOS/iPad et Android dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des licences automatisées et l’appartenance aux groupes ne nécessitent pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester les licences automatiques et l’appartenance aux groupes, et vous pouvez l’expérimenter dans un environnement qui représente une organisation typique.

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Phase 2 : inscrire vos appareils iOS et Android

Si vous envisagez une solution de gestion des appareils mobiles (MDM) pour gérer vos appareils, vous pouvez utiliser Microsoft Intune. Lors de l’utilisation d’un fournisseur MDM, y compris Intune, les appareils sont « à l’État ». Lorsqu’ils sont déployés, ils reçoivent les fonctionnalités et les paramètres que vous configurez. 

Dans Intune, il existe plusieurs façons d’inscrire vos appareils iOS/iPad et Android. Vous pouvez choisir l’option d’enregistrement qui convient le mieux à votre organisation. Pour plus d’informations et d’instructions, consultez les articles suivants :

- [Guide de déploiement : inscrire des appareils iOS et iPados dans Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados)
- [Guide de déploiement : inscrire des appareils Android dans Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android)

Si vous êtes prêt à utiliser Intune pour la gestion des appareils et que vous souhaitez obtenir des conseils, les informations suivantes peuvent vous aider :

- [Vue d’ensemble de la gestion des appareils](/mem/intune/fundamentals/what-is-device-management)
- [Didacticiel : procédure pas à pas Intune dans le gestionnaire de points de terminaison Microsoft](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager)
- [Guide de déploiement : installation ou déplacement vers Microsoft Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Phase 3 : gérer les appareils iOS et Android à distance

Microsoft Intune fournit la fonctionnalité de réinitialisation à distance et par code secret. Si une personne perd son appareil, vous pouvez verrouiller l’appareil à distance. Si une personne oublie son mot de passe, vous pouvez la réinitialiser à distance.

- Pour verrouiller à distance un appareil iOS ou Android, reportez-vous à [Remote Lock devices with Intune](/mem/intune/remote-actions/device-remote-lock).
- Pour réinitialiser le code secret à distance, consultez la rubrique [réinitialiser ou supprimer un code secret de périphérique dans Intune](/mem/intune/remote-actions/device-passcode-reset).

Pour les tâches supplémentaires que vous pouvez exécuter à distance, consultez la rubrique [available Device actions](/mem/intune/remote-actions/device-management#available-device-actions).
    
## <a name="next-step"></a>Étape suivante

Explorez les fonctionnalités supplémentaires de [gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)
  
[Stratégies de conformité des appareils pour votre environnement de test Microsoft 365 pour les entreprises](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)
