---
title: Périphériques Windows 10 intégrés à l’aide des outils de gestion des appareils mobiles
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Utilisez les outils de gestion des appareils mobiles pour déployer le package de configuration sur les appareils de sorte qu’ils soient intégrés au service.
ms.openlocfilehash: 1480c918589a1f00e00ceb1233e9a62887ccff32
ms.sourcegitcommit: 6647055154002c7d3b8f7ce25ad53c9636bc8066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "48769434"
---
# <a name="onboard-windows-10-devices-using-mobile-device-management-tools"></a>Périphériques Windows 10 intégrés à l’aide des outils de gestion des appareils mobiles

**S’applique à :**

- [Microsoft 365 protection contre la perte de données (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)

Vous pouvez utiliser les solutions MDM (Mobile Device Management) pour configurer des appareils. Microsoft 365 Endpoint Data Loss Prevention prend en charge MDMs en fournissant OMA-URIs pour créer des stratégies de gestion des appareils.


## <a name="before-you-begin"></a>Avant de commencer
Si vous utilisez Microsoft Intune, vous devez avoir déployé Device MDM. Dans le cas contraire, les paramètres ne seront pas appliqués. 

Pour plus d’informations sur l’activation de MDM avec Microsoft Intune, reportez-vous à la rubrique [inscrire des appareils (Microsoft Intune)](https://docs.microsoft.com/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Périphériques intégrés à l’aide de Microsoft Intune

Suivez les instructions de [Intune](https://docs.microsoft.com/intune/advanced-threat-protection).

> [!NOTE]
> - L' **État d’intégrité de la stratégie des appareils intégrés** utilise des propriétés en lecture seule et ne peut pas être résolu.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Débarquement et surveillance des périphériques à l’aide des outils de gestion des appareils mobiles

Pour des raisons de sécurité, le package utilisé pour les appareils débarquement expire 30 jours après la date de téléchargement. Les packages par débarquement expirés envoyés à un appareil seront rejetés. Lors du téléchargement d’un package par débarquement, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et de par débarquement ne doivent pas être déployées sur le même appareil simultanément, sinon cette opération entraîne des collisions imprévisibles.

1. Obtenir le package par débarquement à partir du [Centre de conformité Microsoft](https://compliance.microsoft.com/).

2. Dans le volet de navigation, sélectionnez **paramètres** d'  >  **intégration d’appareil**  >  **par débarquement** .

3. Dans le champ **méthode de déploiement** , sélectionnez gestion des **appareils mobiles/Microsoft Intune** .
    
4. Cliquez sur **Télécharger le package** , puis enregistrez le fichier. zip.

5. Extrayez le contenu du fichier. zip vers un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez avoir un fichier nommé *DeviceCompliance_valid_until_YYYY-mm-dd. par débarquement* .

6. Utilisez la stratégie de configuration personnalisée Microsoft Intune pour déployer les paramètres OMA-URI pris en charge suivants.

      OMA-URI :./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding      
      Type de date : chaîne      
      Valeur : [copiez et collez la valeur à partir du contenu du fichier DeviceCompliance_valid_until_YYYY-MM-DD. par débarquement]

Pour plus d’informations sur les paramètres de stratégie Microsoft Intune, voir [paramètres de stratégie Windows 10 dans Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).

> [!NOTE]
> L' **État d’intégrité de la stratégie périphériques offboarded** utilise des propriétés en lecture seule et ne peut pas être résolue.

> [!IMPORTANT]
> Par débarquement entraîne l’arrêt de l’envoi des données de capteur au portail, mais les données de l’appareil, y compris la référence à toutes les alertes qu’il a subi, seront conservées pendant 6 mois maximum.

## <a name="related-topics"></a>Voir aussi
- [Périphériques Windows 10 embarqués à l’aide de la stratégie de groupe](dlp-configure-endpoints-gp.md)
- [Appareils intégrés Windows 10 à l’aide du gestionnaire de configuration de point de terminaison Microsoft](dlp-configure-endpoints-sccm.md)
- [Périphériques Windows 10 embarqués à l’aide d’un script local](dlp-configure-endpoints-script.md)
- [Périphériques VDI (Virtual Desktop Infrastructure) non persistants](dlp-configure-endpoints-vdi.md)
- [Résoudre les problèmes d’intégration de la protection avancée contre les menaces Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
