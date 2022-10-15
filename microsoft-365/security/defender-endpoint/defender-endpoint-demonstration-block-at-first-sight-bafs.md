---
title: démonstration Microsoft Defender pour point de terminaison Block at First Sight (BAFS)
description: Démonstration montrant comment Bloquer à la première consultation détecte et bloque de nouveaux programmes malveillants en quelques secondes.
keywords: Microsoft Defender pour point de terminaison, protection fournie par le cloud, détecter les programmes malveillants, bloquer les programmes malveillants, démonstration
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: evaluation
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: e3ccfa67a66d9326b945bde49a1ccfc0187879c2
ms.sourcegitcommit: 1f4c51d022d1cfb6c194bf0f0af9c2841c781d68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2022
ms.locfileid: "68573019"
---
# <a name="block-at-first-sight-bafs-demonstration"></a>Démonstration de bloquer à la première consultation (BAFS)

Bloquer à la première consultation est une fonctionnalité de Microsoft Defender protection antivirus fournie par le cloud qui fournit un moyen de détecter et de bloquer de nouveaux programmes malveillants en quelques secondes. Vous pouvez tester qu’il fonctionne comme prévu en téléchargeant un fichier de logiciels malveillants factice.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10 mise à jour anniversaire (1607) ou ultérieure
- La protection cloud est activée
- Vous pouvez [télécharger et utiliser le script PowerShell](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings/) pour activer ce paramètre et d’autres

  > [!NOTE]
  > Votre navigateur doit vous demander d’enregistrer ce fichier en quelques secondes.

### <a name="test-bafs"></a>Tester BAFS

1. Cliquez sur **Créer et télécharger un fichier** ci-dessous.
1. Vous devriez voir le navigateur analyser le fichier, suivi d’une notification de bloc antivirus.
1. [Créez & téléchargez un nouveau fichier !](https://demowdtestground.blob.core.windows.net/samples/ztp_xzXLX_s1H8MsxK2SRlsjmzaH62cOZEaqtstGsOw/wdtestfile.exe?sv=2015-07-08&sr=b&sig=7JNcGzAYWEinuWKNmjoC6tDmEjGZMQj8rAEF9HIzJdE%3D&se=2022-09-30T18%3A29%3A28Z&sp=r)

## <a name="see-also"></a>Voir aussi

[Bloquer à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md)

[Microsoft Defender pour point de terminaison - Scénarios de démonstration](defender-endpoint-demonstrations.md)
