---
title: Microsoft Defender pour point de terminaison démonstration d’applications potentiellement indésirables (PUA)
description: Démonstration montrant comment la fonctionnalité de protection des applications potentiellement indésirables (PUA) peut identifier et bloquer le téléchargement et l’installation des APPLICATIONS sur les points de terminaison.
keywords: Microsoft Defender pour point de terminaison, applications potentiellement indésirables, (PUA), protection des applications nuisibles, démonstration
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
ms.openlocfilehash: b8212717d21f7509195ab5b276ccffc443b760c3
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68732688"
---
# <a name="potentially-unwanted-applications-pua-demonstration"></a>Démonstration d’applications potentiellement indésirables (PUA)

La fonctionnalité de protection des applications potentiellement indésirables (PUA) dans Microsoft Defender Antivirus peut identifier et bloquer le téléchargement et l’installation des APPLICATIONS sur les points de terminaison de votre réseau. Ces applications ne sont pas considérées comme des virus, des programmes malveillants ou d’autres types de menaces, mais peuvent effectuer des actions sur des points de terminaison qui affectent négativement leurs performances ou leur utilisation.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10, Windows 11

- Activez la protection puA. Pour plus d’informations, consultez [l’article Détecter et bloquer les applications potentiellement indésirables](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) .
- Vous pouvez également [télécharger et utiliser le script PowerShell](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings/) pour activer ce paramètre et d’autres.

## <a name="scenario"></a>Scénario

1. Atteindre [http://www.amtso.org/feature-settings-check-potentially-unwanted-applications/](http://www.amtso.org/feature-settings-check-potentially-unwanted-applications/)
2. Cliquez sur le lien « Télécharger le fichier 'test' de l’application potentiellement indésirable »
3. Après le téléchargement du fichier, il est automatiquement bloqué et ne peut pas s’exécuter.

## <a name="see-also"></a>Voir aussi

[Détecter et bloquer des applications potentiellement indésirables](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)

[Microsoft Defender pour point de terminaison - scénarios de démonstration](defender-endpoint-demonstrations.md)
