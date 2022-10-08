---
title: Microsoft Defender pour point de terminaison démonstration d’applications potentiellement indésirables (PUA)
description: Démonstration montrant comment la fonctionnalité de protection des applications potentiellement indésirables (PUA) peut identifier et bloquer le téléchargement et l’installation des applications potentiellement indésirables sur les points de terminaison.
keywords: Microsoft Defender pour point de terminaison, applications potentiellement indésirables, protection des applications dangereuses, démonstration
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: evaluation
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 4c5b0fe9af369db36829a4becc637e07cd40fdb9
ms.sourcegitcommit: 55672e44de74209f2e23b4bd9ca74a2ee7e88cd9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2022
ms.locfileid: "68319514"
---
# <a name="potentially-unwanted-applications-pua-demonstration"></a>Démonstration d’applications potentiellement indésirables (PUA)

La fonctionnalité de protection des applications potentiellement indésirables (PUA) dans Microsoft Defender Antivirus peut identifier et bloquer le téléchargement et l’installation des applications potentiellement indésirables sur les points de terminaison de votre réseau. Ces applications ne sont pas considérées comme des virus, des programmes malveillants ou d’autres types de menaces, mais peuvent effectuer des actions sur des points de terminaison qui affectent leurs performances ou leur utilisation.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10

- Activez la protection PUA. Pour plus d’informations, consultez l’article [Détecter et bloquer les applications potentiellement indésirables](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) .
- Vous pouvez également [télécharger et utiliser le script PowerShell](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings/) pour activer ce paramètre et d’autres.

## <a name="scenario"></a>Scénario

1. Atteindre [http://www.amtso.org/feature-settings-check-potentially-unwanted-applications/](http://www.amtso.org/feature-settings-check-potentially-unwanted-applications/)
2. Cliquez sur le lien « Télécharger le fichier « test » de l’application potentiellement indésirable
3. Après le téléchargement du fichier, il est automatiquement bloqué et empêché de s’exécuter.

## <a name="see-also"></a>Voir aussi

[Détecter et bloquer des applications potentiellement indésirables](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)

[Microsoft Defender pour point de terminaison - Scénarios de démonstration](defender-endpoint-demonstrations.md)
