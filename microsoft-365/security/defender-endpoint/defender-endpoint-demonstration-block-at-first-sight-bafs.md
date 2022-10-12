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
ms.openlocfilehash: a8fa480d4408a77630ba1dd2834a990869ebbb14
ms.sourcegitcommit: 4f8200453d347de677461f27eb5a3802ce5cc888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68543198"
---
<!--- v-jweston resumes authorship and ms.authorship appx April-May 2023 ---> 

# <a name="block-at-first-sight-bafs-demonstration"></a>Démonstration de bloquer à la première consultation (BAFS)

Bloquer à la première consultation est une fonctionnalité de Microsoft Defender protection antivirus fournie par le cloud qui fournit un moyen de détecter et de bloquer de nouveaux programmes malveillants en quelques secondes. Vous pouvez tester qu’il fonctionne comme prévu en téléchargeant un fichier de logiciels malveillants factice.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10 mise à jour anniversaire (1607) ou ultérieure
- Protection cloud activée
- Vous pouvez [télécharger et utiliser le script PowerShell](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings/) pour activer ce paramètre et d’autres
- Remarque : votre navigateur doit demander à enregistrer ce fichier en quelques secondes.

### <a name="test-bafs"></a>Tester BAFS

- Cliquez sur le bouton Créer et télécharger un fichier
- Vous devriez voir le navigateur analyser le fichier, suivi d’une notification de bloc antivirus.
- [Créez & téléchargez un nouveau fichier !](https://demowdtestground.blob.core.windows.net/samples/ztp_xzXLX_s1H8MsxK2SRlsjmzaH62cOZEaqtstGsOw/wdtestfile.exe?sv=2015-07-08&sr=b&sig=7JNcGzAYWEinuWKNmjoC6tDmEjGZMQj8rAEF9HIzJdE%3D&se=2022-09-30T18%3A29%3A28Z&sp=r)

## <a name="see-also"></a>Voir aussi

[Bloquer à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md)

[Microsoft Defender pour point de terminaison - Scénarios de démonstration](defender-endpoint-demonstrations.md)
