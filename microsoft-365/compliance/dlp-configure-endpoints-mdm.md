---
title: Intégrer les appareils Windows 10 à l’aide des outils de gestion des appareils mobiles
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
description: Utilisez les outils de gestion des appareils mobiles pour déployer le package de configuration sur les appareils afin qu’ils soient intégrés au service.
ms.openlocfilehash: 1480c918589a1f00e00ceb1233e9a62887ccff32
ms.sourcegitcommit: 6647055154002c7d3b8f7ce25ad53c9636bc8066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "48769434"
---
# <a name="onboard-windows-10-devices-using-mobile-device-management-tools"></a>Intégrer les appareils Windows 10 à l’aide des outils de gestion des appareils mobiles

**S’applique à :**

- [Protection contre la perte de données de point de terminaison Microsoft 365 (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)

Vous pouvez utiliser des solutions de gestion des périphériques mobiles (MDM) pour configurer des appareils. La protection contre la perte de données des points de terminaison Microsoft 365 prend en charge les appareils mobiles en fournissant OMA-URIs pour créer des stratégies pour gérer les appareils.


## <a name="before-you-begin"></a>Avant de commencer
Si vous utilisez Microsoft Intune, l’appareil doit être inscrit à la gestion des appareils. Dans le cas contraire, les paramètres ne seront pas appliqués correctement. 

Pour plus d’informations sur l’activation de la gestion des périphériques multi-appareils avec Microsoft Intune, voir Inscription des appareils [(Microsoft Intune).](https://docs.microsoft.com/mem/intune/enrollment/device-enrollment)

## <a name="onboard-devices-using-microsoft-intune"></a>Intégrer des appareils à l’aide de Microsoft Intune

Suivez les instructions [d’Intune.](https://docs.microsoft.com/intune/advanced-threat-protection)

> [!NOTE]
> - La **stratégie État d’état d’état des appareils** intégrés utilise des propriétés en lecture seule et ne peut pas être corrigé.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Utiliser les outils de gestion des périphériques mobiles pour les appareils mobiles pour les hors-bord et les surveiller

Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages deboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et deboarding ne doivent pas être déployées sur le même appareil en même temps, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package de mise hors programme à partir du [Centre de conformité Microsoft.](https://compliance.microsoft.com/)

2. Dans le volet de navigation, sélectionnez **Paramètres**  >  **Intégration de l’appareil**  >  **hors intégration.**

3. Dans le **champ Méthode de déploiement,** sélectionnez **Gestion des périphériques mobiles / Microsoft Intune**.
    
4. Cliquez **sur Télécharger le package,** puis enregistrez le fichier .zip.

5. Extrayez le contenu du fichier .zip vers un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez avoir un fichier nommé *DeviceCompliance_valid_until_YYYY-MM-DD.offboarding*.

6. Utilisez la stratégie de configuration personnalisée Microsoft Intune pour déployer les paramètres OMA-URI pris en charge suivants.

      OMA-URI : ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding      
      Type de date : Chaîne      
      Valeur : [Copier et coller la valeur à partir du contenu du fichier DeviceCompliance_valid_until_YYYY-MM-DD.offboarding]

Pour plus d’informations sur les paramètres de stratégie Microsoft Intune, voir les paramètres de stratégie [Windows 10 dans Microsoft Intune.](https://docs.microsoft.com/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)

> [!NOTE]
> La **stratégie État d’état d’état des appareils** déboardés utilise des propriétés en lecture seule et ne peut pas être corrigé.

> [!IMPORTANT]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois.

## <a name="related-topics"></a>Rubriques connexes
- [Intégrer des appareils Windows 10 à l’aide de la stratégie de groupe](dlp-configure-endpoints-gp.md)
- [Intégrer des appareils Windows 10 à l’aide de Microsoft Endpoint Configuration Manager](dlp-configure-endpoints-sccm.md)
- [Intégrer les appareils Windows 10 utilisant un script local](dlp-configure-endpoints-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.](dlp-configure-endpoints-vdi.md)
- [Résoudre les problèmes d’intégration de microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
