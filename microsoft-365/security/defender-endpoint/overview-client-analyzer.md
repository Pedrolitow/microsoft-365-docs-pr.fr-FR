---
title: Résoudre les problèmes d’intégrité des capteurs à l’aide de l’analyseur client Microsoft Defender pour point de terminaison
description: Résolvez les problèmes d’intégrité des capteurs sur les appareils pour identifier les problèmes potentiels de configuration, d’environnement, de connectivité ou de télémétrie affectant les données ou fonctionnalités du capteur.
keywords: capteur, intégrité du capteur, mal configuré, inactif, aucune donnée de capteur, données de capteur, communications altérées, communication
ms.service: microsoft-365-security
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
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: bae0ff46333b447e73e130901545fe1f87d50d91
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68227545"
---
# <a name="troubleshoot-sensor-health-using-microsoft-defender-for-endpoint-client-analyzer"></a>Résoudre les problèmes d’intégrité des capteurs à l’aide de l’analyseur client Microsoft Defender pour point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

L’analyseur client Microsoft Defender pour point de terminaison (MDECA) peut être utile lors du diagnostic des problèmes d’intégrité ou de fiabilité des capteurs sur [les appareils intégrés](/microsoft-365/security/defender-endpoint/onboard-configure) exécutant Windows, Linux ou macOS. Par exemple, vous pouvez exécuter l’analyseur sur un ordinateur qui semble défectueux en fonction de [l’état d’intégrité du capteur](/microsoft-365/security/defender-endpoint/fix-unhealthy-sensors) affiché (Inactif, Aucune donnée de capteur ou Communications altérées) dans le portail de sécurité.

Outre les problèmes évidents d’intégrité des capteurs, MDECA peut collecter d’autres traces, journaux et informations de diagnostic pour résoudre les problèmes de scénarios complexes tels que :

- Compatibilité des applications (AppCompat), performances, connectivité réseau ou
- Comportement inattendu lié à la [prévention de la perte de données de point de terminaison](/microsoft-365/compliance/endpoint-dlp-learn-about).

## <a name="privacy-notice"></a>Avis de confidentialité

- L’outil Microsoft Defender pour point de terminaison Client Analyzer est régulièrement utilisé par microsoft Customer Support Services (CSS) pour collecter des informations qui vous aideront à résoudre les problèmes que vous rencontrez peut-être avec Microsoft Defender pour point de terminaison.

- Les données collectées peuvent contenir des informations d’identification personnelle (PII) et/ou des données sensibles, telles que des adresses IP, des noms de PC et des noms d’utilisateur (sans s’y limiter).

- Une fois la collecte de données terminée, l’outil enregistre les données localement sur l’ordinateur dans un sous-dossier et un fichier zip compressé.

- Aucune donnée n’est automatiquement envoyée à Microsoft. Si vous utilisez l’outil pendant la collaboration sur un problème de support, vous pouvez être invité à envoyer les données compressées à Microsoft CSS à l’aide de Secure File Exchange pour faciliter l’examen du problème.

Pour plus d’informations sur l’échange de fichiers sécurisés, consultez [Comment utiliser Secure File Exchange pour échanger des fichiers avec Support Microsoft](/troubleshoot/azure/general/secure-file-exchange-transfer-files)

Pour plus d’informations sur notre déclaration de confidentialité, consultez [la déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="requirements"></a>Conditions requises

- Avant d’exécuter l’analyseur, nous vous recommandons de vous assurer que votre configuration de proxy ou de pare-feu autorise l’accès aux [URL de service Microsoft Defender pour point de terminaison](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- L’analyseur peut s’exécuter sur les éditions prises en charge de [Windows](minimum-requirements.md#supported-windows-versions), [Linux](microsoft-defender-endpoint-linux.md#system-requirements) ou [macOS](microsoft-defender-endpoint-mac.md#system-requirements) avant l’intégration à Microsoft Defender pour point de terminaison.

- Pour les appareils Windows, si vous exécutez l’analyseur directement sur des machines spécifiques et non à distance via [Live Response](/microsoft-365/security/defender-endpoint/troubleshoot-collect-support-log), SysInternals [PsExec.exe](/sysinternals/downloads/psexec) doit être autorisé (au moins temporairement) à s’exécuter. L’analyseur appelle PsExec.exe outil pour exécuter des vérifications de connectivité cloud en tant que système local et émuler le comportement du service SENSE.

    > [!NOTE]
    > Sur les appareils Windows, si vous utilisez des créations de processus de blocage de règle ASR (Attack Surface Reduction) [provenant des commandes PSExec et WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands), vous pouvez désactiver temporairement la règle ou [configurer une exclusion de la règle ASR](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) pour permettre à l’analyseur d’exécuter des vérifications de connectivité dans le cloud comme prévu.
