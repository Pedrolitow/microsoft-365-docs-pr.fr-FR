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
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Utilisez les outils de gestion des appareils mobiles pour déployer le package de configuration sur les appareils afin qu’ils soient intégrés au service.
ms.openlocfilehash: 7c5efde45558f41da4331c33937526f36b777abf
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2021
ms.locfileid: "60754314"
---
# <a name="onboard-windows-10-devices-using-mobile-device-management-tools"></a>Intégrer les appareils Windows 10 à l’aide des outils de gestion des appareils mobiles

**S’applique à :**

- [Microsoft 365 Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)

Vous pouvez utiliser des solutions de gestion des périphériques mobiles (MDM) pour configurer des appareils. Microsoft 365 La protection contre la perte de données de point de terminaison prend en charge les appareils mobiles en fournissant OMA-URIs pour créer des stratégies pour gérer les appareils.


## <a name="before-you-begin"></a>Avant de commencer
Si vous utilisez Microsoft Intune, l’appareil doit être inscrit À la gestion des appareils. Dans le cas contraire, les paramètres ne seront pas appliqués correctement. 

Pour plus d’informations sur l’activation de la gestion des périphériques Microsoft Intune, voir [Inscription d’appareil (Microsoft Intune).](/mem/intune/enrollment/device-enrollment)

## <a name="onboard-devices-using-microsoft-intune"></a>Intégrer des appareils à l’aide Microsoft Intune

Suivez les instructions [d’Intune.](/intune/advanced-threat-protection)

> [!NOTE]
> - La **stratégie État d’état d’état des appareils** intégrés utilise des propriétés en lecture seule et ne peut pas être corrigé.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Utiliser les outils de gestion des périphériques mobiles pour les appareils mobiles pour les hors-bord et les surveiller

Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages deboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et deboarding ne doivent pas être déployées sur le même appareil en même temps, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package deboarding à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centre de conformité Microsoft 365</a>.

2. Dans le volet de navigation, sélectionnez **Paramètres**  >  **l’intégration**  >  **de l’appareil.**

3. Dans le **champ Méthode de déploiement,** sélectionnez **Gestion des périphériques mobiles /Microsoft Intune**.

4. Cliquez **sur Télécharger le package,** puis enregistrez .zip fichier.

5. Extrayez le contenu du fichier .zip vers un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez avoir un fichier nommé *DeviceCompliance_valid_until_YYYY-MM-DD.offboarding*.

6. Utilisez la stratégie Microsoft Intune de configuration personnalisée pour déployer les paramètres OMA-URI pris en charge suivants.

    ```text
    OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
    Date type: String
    Value: [Copy and paste the value from the content of the DeviceCompliance_valid_until_YYYY-MM-DD.offboarding file]
    ```

Pour plus d’informations Microsoft Intune paramètres de stratégie, voir [Windows 10 paramètres de](/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)stratégie dans Microsoft Intune .

> [!NOTE]
> La **stratégie État d’état d’état des** appareils déboardés utilise des propriétés en lecture seule et ne peut pas être corrigé.

> [!IMPORTANT]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois.

## <a name="related-topics"></a>Voir aussi
- [Intégrer des Windows 10 à l’aide de la stratégie de groupe](dlp-configure-endpoints-gp.md)
- [Intégrer Windows 10 appareils à l’aide Microsoft Endpoint Configuration Manager](dlp-configure-endpoints-sccm.md)
- [Intégrer les appareils Windows 10 utilisant un script local](dlp-configure-endpoints-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](dlp-configure-endpoints-vdi.md)
- [Résoudre les problèmes d’intégration de la Protection avancée contre les menaces Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)