---
title: Gérer les paramètres de configuration de Microsoft Defender pour point de terminaison sur les appareils avec Microsoft Endpoint Manager
description: Découvrez comment activer les paramètres de sécurité dans Microsoft Endpoint Manager via Microsoft Defender pour point de terminaison.
keywords: gestion des appareils, configurer Microsoft Defender pour point de terminaison appareils, Microsoft Endpoint Manager
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 4d6c6200434ce4121be495c743b75c686fb54557
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68225589"
---
# <a name="manage-microsoft-defender-for-endpoint-configuration-settings-on-devices-with-microsoft-endpoint-manager"></a>Gérer les paramètres de configuration de Microsoft Defender pour point de terminaison sur les appareils avec Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Gérer Microsoft Defender pour point de terminaison sur les appareils avec Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)


La gestion de la sécurité pour Microsoft Defender pour point de terminaison est une fonctionnalité permettant aux appareils qui ne sont pas gérés par un Endpoint Manager Microsoft de recevoir des configurations de sécurité pour Microsoft Defender directement à partir de Endpoint Manager.


Pour plus d’informations sur la gestion de la configuration de la sécurité, notamment les prérequis, les plateformes prises en charge et bien plus encore, consultez [Gérer les Microsoft Defender pour point de terminaison sur les appareils avec Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Regardez cette vidéo pour découvrir comment utiliser Microsoft Endpoint Manager pour gérer la configuration de la sécurité pour Microsoft Defender pour point de terminaison.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4qLVq]

[!INCLUDE [Prerequisites](../../includes/security-config-mgt-prerequisites.md)]

>[!NOTE]
>Cette fonctionnalité est déployée progressivement. 

Pour plus d’informations sur la gestion de la configuration de la sécurité, consultez [Gérer les Microsoft Defender pour point de terminaison sur les appareils avec Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Si vous rencontrez des problèmes d’inscription, consultez [Résoudre les problèmes d’intégration de Security Configuration Management](troubleshoot-security-config-mgt.md).

> [!NOTE]
> Cette fonctionnalité ne s’applique pas aux appareils qui sont déjà inscrits auprès de Microsoft Endpoint Manager (Intune ou Configuration Manager). Les appareils inscrits dans Intune continueront de recevoir des stratégies via leur canal de gestion établi.

## <a name="identify-onboarded-devices"></a>Identifier les appareils intégrés

Suivez les étapes suivantes pour vérifier que vos points de terminaison ont terminé le processus de gestion de la sécurité pour Microsoft Defender pour point de terminaison processus d’intégration.

1.  Vérifiez que l’appareil apparaît dans la section Inventaire des [appareils de Microsoft 365 Defender](https://security.microsoft.com/).

2.  Dans le [portail Azure Active Directory](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/Devices/menuId/), vérifiez que l’appareil a été correctement inscrit.

3.  Dans le [Centre de Endpoint Manager Administration Microsoft](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/mDMDevicesPreview), vérifiez que l’appareil a bien été inscrit en le recherchant dans la section **Appareils > Tous les appareils**.


## <a name="offboard-devices"></a>Appareils hors-carte
Pour déconnecter les appareils qui ont été intégrés via Security Management pour Microsoft Defender pour point de terminaison, consultez [Les appareils hors-carte du service Microsoft Defender pour point de terminaison](offboard-machines.md).

>[!NOTE]
>Le désintégrage [désactive la protection contre les falsifications](manage-tamper-protection-microsoft-365-defender.md) si elle est activée.

## <a name="troubleshooting-security-management"></a>Résolution des problèmes de gestion de la sécurité 
Pour résoudre les problèmes de gestion de la sécurité pour Microsoft Defender pour point de terminaison problèmes d’inscription, consultez [Résolution des problèmes d’intégration liés à la gestion de la sécurité pour Microsoft Defender pour point de terminaison](troubleshoot-security-config-mgt.md).

## <a name="related-topic"></a>Rubrique connexe
- [Résoudre les problèmes d’intégration liés à la gestion de la sécurité pour Microsoft Defender pour point de terminaison](troubleshoot-security-config-mgt.md)
- [Gérer Microsoft Defender pour point de terminaison sur les appareils avec Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-mde-security-configuration-management)
