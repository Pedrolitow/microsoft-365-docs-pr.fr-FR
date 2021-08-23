---
title: Résoudre les problèmes d’état du capteur à l’aide de Microsoft Defender pour Endpoint Client Analyzer
description: Dépanner l’état du capteur sur les appareils afin d’identifier un problème potentiel de configuration, d’environnement, de connectivité ou de télémétrie affectant les données ou fonctionnalités du capteur.
keywords: capteur, état du capteur, mal configuré, inactif, aucune donnée de capteur, données du capteur, communications altérées, communication
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 604a7d98b25d7b5b858db87c8b8f467ffb8edb83
ms.sourcegitcommit: 251551539b1532fdac7b7e3dd2733a75c62e8a54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58360106"
---
#  <a name="troubleshoot-sensor-health-using-microsoft-defender-for-endpoint-client-analyzer"></a>Résoudre les problèmes d’état du capteur à l’aide de Microsoft Defender pour Endpoint Client Analyzer

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)

Microsoft Defender for Endpoint Client Analyzer (MDECA) peut être utile lors du [](/microsoft-365/security/defender-endpoint/onboard-configure) diagnostic des problèmes d’état ou de fiabilité du capteur sur les appareils intégrés exécutant Windows, Linux ou macOS. Par exemple, vous pouvez exécuter l’analyseur sur un ordinateur qui semble défectueux en fonction de l’état d’état du capteur [affiché](/microsoft-365/security/defender-endpoint/fix-unhealthy-sensors) (Inactif, Aucune donnée de capteur ou Communications altérées) dans le portail de sécurité.

Outre les problèmes d’état du capteur évidents, MDECA peut collecter d’autres suivis, journaux et informations de diagnostic pour résoudre des problèmes complexes tels que :  
Compatibilité des applications (AppCompat), performances, connectivité réseau ou comportement inattendu lié à [endpoint Data Loss Prevention](/microsoft-365/compliance/endpoint-dlp-learn-about).

## <a name="privacy-notice"></a>Avis de confidentialité


-   L’outil Analyseur de client Microsoft Defender pour point de terminaison est régulièrement utilisé par les services de support technique Microsoft (CSS) pour collecter des informations qui vous aideront à résoudre les problèmes que vous rencontrez avec Microsoft Defender pour Endpoint.

-   Les données collectées peuvent contenir des informations d’identification personnelle (PII) et/ou des données sensibles, telles que (mais sans s’y limiter) des adresses IP, des noms de PC et des noms d’utilisateur.

-   Une fois la collecte de données terminée, l’outil enregistre les données localement sur l’ordinateur dans un sous-dossier et un fichier zip compressé.

-   Aucune donnée n’est envoyée automatiquement à Microsoft. Si vous utilisez l’outil pendant la collaboration sur un problème de support, vous pouvez être invité à envoyer les données compressées à Microsoft CSS à l’aide de l’Exchange de fichier sécurisé pour faciliter l’examen du problème.

Pour plus d’informations sur la Exchange fichiers sécurisés, voir Comment utiliser la Exchange fichiers sécurisés pour échanger des fichiers [avec le Support Microsoft](/troubleshoot/azure/general/secure-file-exchange-transfer-files)  

Pour plus d’informations sur notre déclaration de confidentialité, voir [déclaration de confidentialité Microsoft.](https://privacy.microsoft.com/privacystatement)

## <a name="requirements"></a>Configuration requise

-   Avant d’utiliser l’analyseur, nous vous recommandons de vous assurer que la configuration de votre proxy ou pare-feu autorise l’accès aux URL du service Microsoft Defender pour les points [de terminaison.](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

-   L’analyseur peut s’exécuter sur les éditions de [Windows,](minimum-requirements.md#supported-windows-versions) [Linux](microsoft-defender-endpoint-linux.md#system-requirements)ou [macOS](microsoft-defender-endpoint-mac.md#system-requirements) avant l’intégration à Microsoft Defender pour Endpoint.

-   Pour Windows appareils, si vous exécutez l’analyseur directement sur des ordinateurs spécifiques et non à distance via [Live Response,](/microsoft-365/security/defender-endpoint/troubleshoot-collect-support-log)SysInternals [PsExec.exe](/sysinternals/downloads/psexec) doit être autorisé (au moins temporairement) à s’exécuter.  
    L’analyseur appelle PsExec.exe'outil pour exécuter des vérifications de connectivité cloud en tant que système local et émuler le comportement du service SENSE.

    > [!NOTE]
    > Sur les appareils Windows, si vous utilisez des créations de processus de blocage de processus de réduction de la surface d’attaque (ASR) provenant de commandes [PSExec et WMI,](attack-surface-reduction-rules.md#block-process-creations-originating-from-psexec-and-wmi-commands)vous pouvez désactiver temporairement la règle ou configurer une exclusion à la règle [de](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) réduction de la surface d’attaque pour permettre à l’analyseur d’exécuter des vérifications de connectivité dans le cloud comme prévu.
