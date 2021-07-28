---
title: Isolation matérielle (Windows 10)
ms.reviewer: ''
description: Découvrez comment l’isolation matérielle dans Windows 10 permet de lutter contre les programmes malveillants.
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.author: macapara
ms.date: 09/07/2018
ms.technology: mde
ms.openlocfilehash: 68a21e832ca81054411a6e3720921edaa6c9301e
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53622807"
---
# <a name="hardware-based-isolation-in-windows-10"></a>Isolation basée sur le matériel dans Windows 10

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


L’isolation matérielle permet de protéger l’intégrité du système Windows 10 et est intégrée à Microsoft Defender pour endpoint. 

| Fonctionnalité | Description |
|------------|-------------|
| [Windows Defender Application Guard](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview.md) | Application Guard protège votre appareil contre les attaques avancées tout en vous conservant productif. À l’aide d’une approche d’isolation matérielle unique, l’objectif est d’isoler les sites web non confiance et les documents PDF à l’intérieur d’un conteneur léger séparé du système d’exploitation via l’hyperviseur Windows natif. Si un site non sécurisé ou un document PDF s’avère malveillant, il reste contenu dans le conteneur sécurisé d’Application Guard, en maintenant le PC de bureau protégé et l’attaquant à l’écart de vos données d’entreprise. |
| [Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows.md) | System Guard protège et maintient l’intégrité du système au démarrage et après son exécution, et valide l’intégrité du système à l’aide de l’attestation.  |

