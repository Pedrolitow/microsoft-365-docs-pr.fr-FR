---
title: Détecter et bloquer les applications potentiellement indésirables avec Microsoft Defender pour Endpoint sur Mac
description: Détecter et bloquer les applications potentiellement indésirables (PUA) à l’aide de Microsoft Defender sur le point de terminaison pour Mac.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, pua, pus
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: e21407ada85dbed1395f4be9cb943835d563ae8a
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53624079"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-macos"></a>Détecter et bloquer les applications potentiellement indésirables avec Microsoft Defender pour endpoint sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


La fonctionnalité de protection des applications potentiellement indésirables (PUA) dans Microsoft Defender for Endpoint sur macOS peut détecter et bloquer les fichiers PUA sur les points de terminaison de votre réseau.

Ces applications ne sont pas considérées comme des virus, des programmes malveillants ou d’autres types de menaces, mais peuvent effectuer des actions sur les points de terminaison qui affectent leurs performances ou leur utilisation. PuA peut également faire référence à des applications considérées comme de mauvaise réputation.

Ces applications peuvent augmenter le risque d’infection de votre réseau par des programmes malveillants, rendre l’identification des programmes malveillants plus difficile et entraîner une perte de ressources informatiques lors du nettoyage des applications.

## <a name="how-it-works"></a>Mode de fonctionnement

Microsoft Defender pour le point de terminaison sur macOS peut détecter et signaler des fichiers PUA. Lorsqu’ils sont configurés en mode de blocage, les fichiers PUA sont placés en quarantaine.

Lorsqu’une puA est détectée sur un point de terminaison, Microsoft Defender pour Endpoint sur macOS présente une notification à l’utilisateur, sauf si les notifications ont été désactivées. Le nom de la menace contient le mot « Application ».

## <a name="configure-pua-protection"></a>Configurer la protection PUA

La protection PUA dans Microsoft Defender pour endpoint sur macOS peut être configurée de l’une des manières suivantes :

- **Désactivé**: la protection PUA est désactivée.
- **Audit**: les fichiers PUA sont signalés dans les journaux du produit, mais pas dans Microsoft 365 Defender portail. Aucune notification n’est présentée à l’utilisateur et aucune action n’est prise par le produit.
- **Bloquer**: les fichiers PUA sont signalés dans les journaux du produit et dans Microsoft 365 Defender portail. Une notification est présentée à l’utilisateur et une action est prise par le produit.

>[!WARNING]
>Par défaut, la protection PUA est configurée en mode **Audit.**

Vous pouvez configurer la façon dont les fichiers PUA sont gérés à partir de la ligne de commande ou de la console de gestion.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>Utilisez l’outil de ligne de commande pour configurer la protection PUA :

Dans Terminal, exécutez la commande suivante pour configurer la protection PUA :

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>Utilisez la console de gestion pour configurer la protection PUA :

Dans votre entreprise, vous pouvez configurer la protection PUA à partir d’une console de gestion, telle que JAMF ou Intune, de la même façon que les autres paramètres de produit sont configurés. Pour plus d’informations, consultez la section [Paramètres](mac-preferences.md#threat-type-settings) du type de menace de la rubrique Définir les préférences de Microsoft Defender pour le point de terminaison [sur macOS.](mac-preferences.md)

## <a name="related-topics"></a>Voir aussi

- [Définir des préférences pour Microsoft Defender pour le point de terminaison sur macOS](mac-preferences.md)
