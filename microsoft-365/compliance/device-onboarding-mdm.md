---
title: Intégrer les appareils Windows 10 et Windows 11 à l’aide des outils de gestion des périphériques mobiles
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Utilisez les outils Gestion des appareils mobile pour déployer le package de configuration sur les appareils afin qu’ils soient intégrés au service.
ms.openlocfilehash: 9b329ccf86a2364c13ac72bd4348711d72c17ff5
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634490"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-mobile-device-management-tools"></a>Intégrer les appareils Windows 10 et Windows 11 à l’aide des outils de gestion des périphériques mobiles

**S’applique à :**

- [Protection contre la perte de données de point de terminaison (DLP) pour Microsoft 365](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

Vous pouvez utiliser des solutions de gestion des périphériques mobiles (MDM) pour configurer des appareils. Microsoft 365 protection des informations prend en charge les appareils mobiles en fournissant OMA-URIs pour créer des stratégies pour gérer les appareils.


## <a name="before-you-begin"></a>Avant de commencer
Si vous utilisez Microsoft Intune, vous devez avoir inscrit l’appareil MDM. Dans le cas contraire, les paramètres ne seront pas appliqués correctement. 

Pour plus d’informations sur l’activation de la gestion des périphériques Microsoft Intune, voir Inscription d’appareil [(Microsoft Intune).](/mem/intune/enrollment/device-enrollment)

## <a name="onboard-devices-using-microsoft-intune"></a>Intégrer des appareils à l’aide Microsoft Intune

Suivez les instructions de [la Intune](/mem/intune/protect/advanced-threat-protection-configure).
 
> [!NOTE]
> - La **stratégie État d’état d’état des appareils** intégrés utilise des propriétés en lecture seule et ne peut pas être corrigé.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Utiliser les outils d’analyse et de Gestion des appareils mobiles

Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages de offboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et deboarding ne doivent pas être déployées sur le même appareil en même temps, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package deboarding à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centre de conformité Microsoft 365</a>.

2. Dans le volet de navigation, sélectionnez **Paramètres** >  **Device onboardingOffboarding** > .

3. Dans le **champ Méthode de** déploiement, sélectionnez **Mobile Gestion des appareils /Microsoft Intune**.

4. Cliquez **sur Télécharger le package**, puis enregistrez .zip fichier.

5. Extrayez le contenu du fichier .zip vers un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez avoir un fichier nommé *DeviceCompliance_valid_until_YYYY-MM-DD.offboarding*.

6. Utilisez la Microsoft Intune de configuration personnalisée pour déployer les paramètres OMA-URI pris en charge suivants.

    ```text
    OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
    Date type: String
    Value: [Copy and paste the value from the content of the DeviceCompliance_valid_until_YYYY-MM-DD.offboarding file]
    ```
> [!NOTE]
> Si Microsoft Defender pour point de terminaison est déjà configuré, vous pouvez activer l’intégration de l’appareil et l’étape 6 n’est plus nécessaire.

> [!NOTE]
> La **stratégie État d’état d’état des** appareils déboardés utilise des propriétés en lecture seule et ne peut pas être corrigé.

> [!IMPORTANT]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois.

## <a name="related-topics"></a>Voir aussi
- [Intégrer Windows 10 appareils à l’aide stratégie de groupe](device-onboarding-gp.md)
- [Intégrer Windows 10 appareils à l’aide Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Intégrer les appareils Windows 10 utilisant un script local](device-onboarding-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](device-onboarding-vdi.md)
- [Résoudre les problèmes d’intégration de la Protection avancée contre les menaces Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
