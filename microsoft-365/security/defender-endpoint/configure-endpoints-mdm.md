---
title: Intégrer des appareils Windows à Defender pour point de terminaison à l’aide de Intune
description: Utilisez Microsoft Intune pour déployer le package de configuration sur les appareils afin qu’ils soient intégrés au service Defender pour point de terminaison.
keywords: intégrer des appareils à l’aide de mdm, gestion des appareils, intégrer des appareils Microsoft Defender pour point de terminaison, mdm
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 8406e14f3573b449905b2ccb71a1685c8bd4fb10
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67701453"
---
# <a name="onboard-windows-devices-to-defender-for-endpoint-using-intune"></a>Intégrer des appareils Windows à Defender pour point de terminaison à l’aide de Intune 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsmdm-abovefoldlink)

Vous pouvez utiliser des solutions de gestion des appareils mobiles (GPM) pour configurer Windows 10 appareils. Defender pour point de terminaison prend en charge les GPM en fournissant des OMA-URIs pour créer des stratégies pour gérer les appareils.

Pour plus d’informations sur l’utilisation de Defender pour endpoint CSP, consultez le fichier DDF [WindowsAdvancedThreatProtection](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) et [WindowsAdvancedThreatProtection](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

## <a name="before-you-begin"></a>Avant de commencer

Les appareils doivent être inscrits avec Intune comme solution mobile Gestion des appareils (GPM).

Pour plus d’informations sur l’activation de GPM avec Microsoft Intune, consultez [Inscription de l’appareil (Microsoft Intune).](/mem/intune/enrollment/device-enrollment)

## <a name="onboard-devices-using-microsoft-intune"></a>Intégrer des appareils à l’aide de Microsoft Intune

Consultez le [fichier PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) ou [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) pour voir les différents chemins d’accès dans le déploiement de Defender pour point de terminaison.

Suivez les instructions de [Intune](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).


Pour plus d’informations sur l’utilisation de Defender pour endpoint CSP, consultez le fichier DDF [WindowsAdvancedThreatProtection](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) et [WindowsAdvancedThreatProtection](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

> [!NOTE]
>
> - La stratégie **État d’intégrité des appareils intégrés** utilise des propriétés en lecture seule et ne peut pas être corrigée.
> - La configuration de la fréquence de création de rapports de données de diagnostic est disponible uniquement pour les appareils sur Windows 10, version 1703.
> - L’intégration à Defender pour point de terminaison intégrera l’appareil à [la protection contre la perte de données (DLP),](../../compliance/endpoint-dlp-learn-about.md) qui fait également partie de la conformité à Microsoft 365.


## <a name="run-a-detection-test-to-verify-onboarding"></a>Exécuter un test de détection pour vérifier l’intégration
Après l’intégration de l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, consultez [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md).


## <a name="offboard-devices-using-mobile-device-management-tools"></a>Désintégrage des appareils à l’aide des outils de Gestion des appareils mobile

Pour des raisons de sécurité, le package utilisé pour désintégrez les appareils expirera 30 jours après la date de téléchargement. Les packages de désintégrage expirés envoyés à un appareil seront rejetés. Lors du téléchargement d’un package de désintégrage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et de désintégrage ne doivent pas être déployées simultanément sur le même appareil, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package de désintégrage à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> :

   1. Dans le volet de navigation, sélectionnez **Paramètres** \> **Points de terminaison** \> De la **désintégration** **de la gestion** \> des appareils.

   1. Sélectionnez Windows 10 ou Windows 11 comme système d’exploitation.

   1. Dans le champ **Méthode de déploiement**, sélectionnez **Mobile Gestion des appareils/Microsoft Intune**.

   1. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.

2. Extrayez le contenu du fichier .zip dans un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez disposer d’un fichier nommé *WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding*.

3. Utilisez la stratégie de configuration personnalisée Microsoft Intune pour déployer les paramètres OMA-URI pris en charge suivants.
   - OMA-URI : ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
   - Type de date : Chaîne
   - Valeur : [Copiez et collez la valeur à partir du contenu du fichier WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding]

Pour plus d’informations sur Microsoft Intune paramètres de stratégie, consultez [Windows 10 paramètres de stratégie dans Microsoft Intune](/mem/intune/configuration/custom-settings-windows-10).

> [!NOTE]
> La **stratégie État d’intégrité des appareils hors-carte** utilise des propriétés en lecture seule et ne peut pas être corrigée.

> [!IMPORTANT]
> La désintégération entraîne l’arrêt de l’envoi de données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois maximum.

## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows à l’aide d’une stratégie de groupe](configure-endpoints-gp.md)
- [Intégrer des appareils Windows à l’aide de Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Intégrer les appareils Windows utilisant un script local](configure-endpoints-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)
- [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md)
- [Résoudre les problèmes d’intégration Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md)
