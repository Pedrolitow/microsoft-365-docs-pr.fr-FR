---
title: Configurer Antivirus Microsoft Defender avec WMI
description: Découvrez comment configurer et gérer les Antivirus Microsoft Defender à l’aide de scripts WMI pour récupérer, modifier et mettre à jour les paramètres dans Microsoft Defender pour le point de terminaison.
keywords: wmi, scripts, instrumentation de gestion Windows, configuration
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: d16030609cbb3949c93127d5ba5805747667850c
ms.sourcegitcommit: 6968594dc8cf8b30a4c958df6d65dfd0cd2cfae1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2021
ms.locfileid: "59491312"
---
# <a name="use-windows-management-instrumentation-wmi-to-configure-and-manage-microsoft-defender-antivirus"></a>Utiliser Windows Management Instrumentation (WMI) pour configurer et gérer les Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Windows Management Instrumentation (WMI) est une interface de script qui vous permet de récupérer, modifier et mettre à jour les paramètres.

Pour en savoir plus sur WMI, consultez la bibliothèque [Microsoft Developer Network System Administration.](/windows/win32/wmisdk/wmi-start-page)

Antivirus Microsoft Defender possède un certain nombre de classes WMI spécifiques qui peuvent être utilisées pour effectuer la plupart des mêmes fonctions que la stratégie de groupe et d’autres outils de gestion. De nombreuses classes sont analogues aux [cmdlets Defender PowerShell.](use-powershell-cmdlets-microsoft-defender-antivirus.md)

La bibliothèque de référence du fournisseur [MSDN Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) répertorie les classes WMI disponibles pour Antivirus Microsoft Defender et inclut des exemples de scripts.

Les modifications apportées avec WMI affecteront les paramètres locaux sur le point de terminaison où les modifications sont déployées ou apportées. Cela signifie que les déploiements de stratégie avec stratégie de groupe, Microsoft Endpoint Configuration Manager ou Microsoft Intune peuvent modifier les modifications apportées avec WMI. 

Vous pouvez configurer les paramètres qui peuvent être remplacer localement avec les [remplacements de stratégie locale.](configure-local-policy-overrides-microsoft-defender-antivirus.md)

## <a name="related-topics"></a>Sujets associés

- [Rubriques de référence pour les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)