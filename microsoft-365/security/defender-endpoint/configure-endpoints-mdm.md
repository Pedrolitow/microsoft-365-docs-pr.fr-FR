---
title: Intégrer des Windows à l’aide des outils de gestion des appareils mobiles
description: Utilisez les outils de gestion des appareils mobiles pour déployer le package de configuration sur les appareils afin qu’ils soient intégrés au service Defender for Endpoint.
keywords: intégrer des appareils à l’aide de mdm, gestion des appareils, intégration de Microsoft Defender pour les appareils Endpoint, mdm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a92b663eeddfcfb8ccf17bad204074764711685d
ms.sourcegitcommit: be095345257225394674698beb3feeb0696ec86d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2021
ms.locfileid: "60239875"
---
# <a name="onboard-windows-devices-using-mobile-device-management-tools"></a>Intégrer des Windows à l’aide des outils de gestion des appareils mobiles

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsmdm-abovefoldlink)

Vous pouvez utiliser des solutions de gestion des périphériques mobiles (MDM) pour configurer Windows 10 appareils mobiles. Defender for Endpoint prend en charge les appareils mobiles en fournissant des OMA-URIs pour créer des stratégies pour gérer les appareils.


Pour plus d’informations sur l’utilisation du programme CSP Defender for Endpoint, voir le fichier DDF [WindowsAdvancedThreatProtection](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) et [WindowsAdvancedThreatProtection.](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx)

## <a name="before-you-begin"></a>Avant de commencer

Si vous utilisez Microsoft Intune, l’appareil doit être inscrit À la gestion des périphériques. Dans le cas contraire, les paramètres ne seront pas appliqués correctement.

Pour plus d’informations sur l’activation de la gestion des périphériques Microsoft Intune, voir [Inscription d’appareil (Microsoft Intune).](/mem/intune/enrollment/device-enrollment)

## <a name="onboard-devices-using-microsoft-intune"></a>Intégrer des appareils à l’aide Microsoft Intune

Consultez le [fichier PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) [ou Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) pour voir les différents chemins d’accès dans le déploiement de Defender for Endpoint.

Suivez les instructions [d’Intune.](/intune/advanced-threat-protection)

Pour plus d’informations sur l’utilisation du programme CSP Defender for Endpoint, voir le fichier DDF [WindowsAdvancedThreatProtection](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) et [WindowsAdvancedThreatProtection.](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx)

> [!NOTE]
>
> - La **stratégie État d’état d’état des appareils** intégrés utilise des propriétés en lecture seule et ne peut pas être corrigé.
> - La configuration de la fréquence de rapports de données de diagnostic est disponible uniquement pour les appareils Windows 10 version 1703.


Consultez le [fichier PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) [ou Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) pour voir les différents chemins d’accès dans le déploiement de Microsoft Defender pour Endpoint.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Exécuter un test de détection pour vérifier l’intégration
Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, voir Exécuter un test de détection sur un appareil [Microsoft Defender pour point de terminaison nouvellement intégré.](run-detection-test.md)


## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Utiliser les outils de gestion des périphériques mobiles pour les appareils mobiles pour les hors-bord et les surveiller

Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages deboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et deboarding ne doivent pas être déployées sur le même appareil en même temps, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package deboarding à partir [Microsoft 365 Defender portail :](https://security.microsoft.com/)

   1. Dans le volet de navigation, sélectionnez **le Paramètres** de gestion des appareils \> **endpoints.** \>  \> 

   1. Sélectionnez Windows 10 ou Windows 11 comme système d’exploitation.

   1. Dans le **champ Méthode de déploiement,** sélectionnez Gestion des périphériques **mobiles /Microsoft Intune**.

   1. Cliquez **sur Télécharger le package,** puis enregistrez .zip fichier.

2. Extrayez le contenu du fichier .zip vers un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez avoir un fichier nommé *WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding*.

3. Utilisez la stratégie Microsoft Intune de configuration personnalisée pour déployer les paramètres OMA-URI pris en charge suivants.
   - OMA-URI : ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
   - Type de date : Chaîne
   - Valeur : [Copier et coller la valeur à partir du contenu du fichier WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding]

Pour plus d’informations Microsoft Intune paramètres de stratégie, voir Windows 10 [paramètres de](/mem/intune/configuration/custom-settings-windows-10)stratégie dans Microsoft Intune .

> [!NOTE]
> La **stratégie État d’état d’état des appareils** déboardés utilise des propriétés en lecture seule et ne peut pas être corrigé.

> [!IMPORTANT]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois.

## <a name="related-topics"></a>Rubriques connexes
- [Intégrer des Windows à l’aide de la stratégie de groupe](configure-endpoints-gp.md)
- [Intégrer Windows appareils à l’aide Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Intégrer Windows appareils à l’aide d’un script local](configure-endpoints-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)
- [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md)
- [Résoudre les problèmes d’intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)
