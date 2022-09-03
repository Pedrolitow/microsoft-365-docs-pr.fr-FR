---
title: Restaurer des fichiers mis en quarantaine dans l’antivirus Microsoft Defender
description: Vous pouvez restaurer les fichiers et dossiers qui ont été mis en quarantaine par l’antivirus Microsoft Defender.
keywords: ''
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/19/2021
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 415c16677669277e75f88ec91d1ef18cefd00ee0
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67585573"
---
# <a name="restore-quarantined-files-in-microsoft-defender-antivirus"></a>Restaurer des fichiers mis en quarantaine dans l’antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Si l’Antivirus Microsoft Defender est configuré pour détecter et corriger les menaces sur votre appareil, l’Antivirus Microsoft Defender met en quarantaine les fichiers suspects. Si vous êtes certain qu’un fichier mis en quarantaine n’est pas une menace, vous pouvez le restaurer.

1. Ouvrez **Sécurité Windows**.
2. Sélectionnez **Virus & protection contre les menaces** , puis cliquez sur **Historique de protection**.
3. Dans la liste de tous les éléments récents, **filtrez les éléments mis en quarantaine**.
4. Sélectionnez un élément que vous souhaitez conserver et effectuez une action, telle que la restauration.

> [!TIP]
> La restauration d’un fichier à partir de la mise en quarantaine peut également être effectuée à l’aide de l’invite de commandes. Consultez [Restaurer un fichier à partir d’une mise en quarantaine](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts#restore-file-from-quarantine). 

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-articles"></a>Articles connexes

- [Configurer la correction pour les analyses](configure-remediation-microsoft-defender-antivirus.md)
- [Examiner les résultats de l’analyse](review-scan-results-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions en fonction du nom de fichier, de l’extension et de l’emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider les exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer les exclusions de l’Antivirus Microsoft Defender sur Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)