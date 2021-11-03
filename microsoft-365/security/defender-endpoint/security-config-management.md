---
title: Gérer les paramètres de configuration de Microsoft Defender for Endpoint sur les appareils Microsoft Endpoint Manager
description: Découvrez comment activer les paramètres de sécurité dans Microsoft Endpoint Manager via Microsoft Defender for Endpoint.
keywords: gestion des appareils, configurer Microsoft Defender pour les appareils de point de terminaison, Microsoft Endpoint Manager
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 08fae46ce14a74dacefd76fbc8e77511c40609e6
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60677067"
---
# <a name="manage-microsoft-defender-for-endpoint-configuration-settings-on-devices-with-microsoft-endpoint-manager"></a>Gérer les paramètres de configuration de Microsoft Defender for Endpoint sur les appareils Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Gérer Microsoft Defender pour le point de terminaison sur les appareils avec Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)


La gestion de la sécurité pour Microsoft Defender pour point de terminaison est une fonctionnalité qui permet aux appareils qui ne sont pas gérés par un Microsoft Endpoint Manager, Microsoft Intune ou Microsoft Endpoint Configuration Manager, de recevoir des configurations de sécurité pour Microsoft Defender. directement à partir Endpoint Manager.


Pour plus d’informations sur la gestion de la configuration de la sécurité, notamment sur les conditions préalables, les plateformes prise en charge et bien plus encore, voir Gérer [Microsoft Defender pour endpoint](/mem/intune/protect/mde-security-integration)sur les appareils avec Microsoft Endpoint Manager .



[!INCLUDE [Prerequisites](../../includes/security-config-mgt-prerequisites.md)]


Pour plus d’informations sur la gestion de la configuration de la sécurité, voir [Gérer Microsoft Defender pour le point](/mem/intune/protect/mde-security-integration)de terminaison sur les appareils Microsoft Endpoint Manager .

Si vous rencontrez des problèmes d’inscription, voir Résoudre les problèmes d’intégration de la gestion [de la configuration de la sécurité.](troubleshoot-security-config-mgt.md)

> [!NOTE]
> Cette fonctionnalité ne s’applique pas aux appareils déjà inscrits à Microsoft Endpoint Manager (Intune ou Configuration Manager). Les appareils inscrits dans Intune continueront de recevoir des stratégies via leur canal de gestion établi.

## <a name="identify-onboarded-devices"></a>Identifier les appareils intégrés

Utilisez les étapes suivantes pour vérifier que vos points de terminaison ont correctement terminé le processus de gestion de la sécurité de Microsoft Defender pour l’intégration des points de terminaison.

1.  Vérifiez que l’appareil apparaît dans la section Inventaire des appareils de [Microsoft 365 Defender](https://security.microsoft.com/).

2.  Dans le [portail Azure Active Directory,](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/MsGraphUsers)vérifiez que l’appareil a été correctement inscrit.

3.  Dans le [Microsoft Endpoint Manager d’administration,](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/mDMDevicesPreview)vérifiez que l’appareil a été correctement inscrit en le vérifiant dans la section Appareils **> tous les** appareils.


## <a name="offboard-devices"></a>Appareils hors-carte
Pour hors-boarder les appareils qui ont été intégrés via la Gestion de la sécurité pour Microsoft Defender pour le point de terminaison, consultez Les appareils Deboard à partir du [service Microsoft Defender pour point de terminaison.](offboard-machines.md)

>[!NOTE]
>La désintion [désintion désactive la protection](prevent-changes-to-security-settings-with-tamper-protection.md#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal) contre les falsifications si elle est activée.

## <a name="troubleshooting-security-management"></a>Résolution des problèmes de gestion de la sécurité 
Pour résoudre les problèmes de gestion de la sécurité pour Microsoft Defender pour l’inscription des points de terminaison, voir Résoudre les problèmes d’intégration liés à la gestion de la sécurité [pour Microsoft Defender pour le point de terminaison.](troubleshoot-security-config-mgt.md)

## <a name="related-topic"></a>Rubrique connexe
- [Résoudre les problèmes d’intégration liés à la gestion de la sécurité pour Microsoft Defender pour le point de terminaison](troubleshoot-security-config-mgt.md)
- [Gérer Microsoft Defender pour le point de terminaison sur les appareils avec Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-mde-security-configuration-management)
