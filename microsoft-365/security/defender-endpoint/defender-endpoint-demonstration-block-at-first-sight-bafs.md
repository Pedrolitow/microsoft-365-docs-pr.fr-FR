---
title: démonstration Microsoft Defender pour point de terminaison Block at First Sight (BAFS)
description: Démonstration qui montre comment Bloquer à la première consultation détecte et bloque les nouveaux programmes malveillants en quelques secondes.
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
- demo
ms.topic: article
ms.subservice: mde
ms.date: 10/21/2022
ms.openlocfilehash: d8d2b130381228ec2f7c57c0c8ae351841fbd277
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68730203"
---
# <a name="block-at-first-sight-bafs-demonstration"></a>Démonstration Bloquer à la première consultation (BAFS)

Bloquer à la première consultation est une fonctionnalité de Microsoft Defender protection fournie par le cloud antivirus qui permet de détecter et de bloquer les nouveaux programmes malveillants en quelques secondes. Vous pouvez tester qu’il fonctionne comme prévu en téléchargeant un fichier de logiciel malveillant factice.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- mise à jour anniversaire Windows 10 (1607) ou ultérieure
- La protection cloud est activée
- Vous pouvez [télécharger et utiliser le script PowerShell](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings/) pour activer ce paramètre et d’autres

  > [!NOTE]
  > Vous devriez voir votre navigateur demander d’enregistrer ce fichier dans quelques secondes.

### <a name="test-bafs"></a>Tester BAFS

1. Cliquez sur **Créer et téléchargez un fichier** ci-dessous.
1. Vous devez voir le navigateur analyser le fichier, suivi d’une notification de blocage antivirus.
1. [Créez & téléchargez un fichier !](https://demowdtestground.blob.core.windows.net/samples/ztp_xzXLX_s1H8MsxK2SRlsjmzaH62cOZEaqtstGsOw/wdtestfile.exe?sv=2015-07-08&sr=b&sig=7JNcGzAYWEinuWKNmjoC6tDmEjGZMQj8rAEF9HIzJdE%3D&se=2022-09-30T18%3A29%3A28Z&sp=r)

## <a name="see-also"></a>Voir aussi

[Bloquer à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md)

[Microsoft Defender pour point de terminaison - scénarios de démonstration](defender-endpoint-demonstrations.md)
