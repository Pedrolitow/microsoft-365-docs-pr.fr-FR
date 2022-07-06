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
description: Utilisez les outils de Gestion des appareils mobile pour déployer le package de configuration sur les appareils afin qu’ils soient intégrés au service.
ms.openlocfilehash: d5c03c80c9a38d34ab27f888084604372874a64a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624198"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-mobile-device-management-tools"></a>Intégrer les appareils Windows 10 et Windows 11 à l’aide des outils de gestion des périphériques mobiles

**S’applique à :**

- [Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md)

Vous pouvez utiliser des solutions de gestion des appareils mobiles (GPM) pour configurer des appareils. La protection des informations Microsoft 365 prend en charge les GPM en fournissant des OMA-URIs pour créer des stratégies pour gérer les appareils.


## <a name="before-you-begin"></a>Avant de commencer
Si vous utilisez Microsoft Intune, l’appareil MDM doit être inscrit. Sinon, les paramètres ne seront pas appliqués correctement. 

Pour plus d’informations sur l’activation de GPM avec Microsoft Intune, consultez [Inscription de l’appareil (Microsoft Intune).](/mem/intune/enrollment/device-enrollment)

## <a name="onboard-devices-using-microsoft-intune"></a>Intégrer des appareils à l’aide de Microsoft Intune

Suivez les instructions de [Intune](/mem/intune/protect/advanced-threat-protection-configure).
 
> [!NOTE]
> - La stratégie **État d’intégrité des appareils intégrés** utilise des propriétés en lecture seule et ne peut pas être corrigée.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Désinstégez et surveillez les appareils à l’aide des outils de Gestion des appareils mobile

Pour des raisons de sécurité, le package utilisé pour désintégrez les appareils expirera 30 jours après la date de téléchargement. Les packages de désintégrage expirés envoyés à un appareil seront rejetés. Lors du téléchargement d’un package de désintégrage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et de désintégrage ne doivent pas être déployées simultanément sur le même appareil, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package de désintégrage à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>.

2. Dans le volet de navigation, sélectionnez **Paramètres** > **De l’intégration de l’appareil** > **hors-bord**.

3. Dans le champ **Méthode de déploiement**, sélectionnez **Mobile Gestion des appareils/Microsoft Intune**.

4. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.

5. Extrayez le contenu du fichier .zip dans un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez disposer d’un fichier nommé *DeviceCompliance_valid_until_YYYY-MM-DD.offboarding*.

6. Utilisez la stratégie de configuration personnalisée Microsoft Intune pour déployer les paramètres OMA-URI pris en charge suivants.

    ```text
    OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
    Date type: String
    Value: [Copy and paste the value from the content of the DeviceCompliance_valid_until_YYYY-MM-DD.offboarding file]
    ```
> [!NOTE]
> Si Microsoft Defender pour point de terminaison est déjà configuré, vous pouvez **activer l’intégration des appareils** et l’étape 6 n’est plus nécessaire.

> [!NOTE]
> La **stratégie État d’intégrité des appareils hors-carte** utilise des propriétés en lecture seule et ne peut pas être corrigée.

> [!IMPORTANT]
> La désintégération entraîne l’arrêt de l’envoi de données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois maximum.

## <a name="related-topics"></a>Rubriques connexes
- [Intégrer des appareils Windows 10 à l’aide de stratégie de groupe](device-onboarding-gp.md)
- [Intégrer des appareils Windows 10 à l’aide de Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Intégrer les appareils Windows 10 utilisant un script local](device-onboarding-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](device-onboarding-vdi.md)
- [Résoudre les problèmes d’intégration de Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
