---
title: Détecter et bloquer les applications potentiellement indésirables avec Microsoft Defender pour point de terminaison sur Mac
description: Détecter et bloquer les applications potentiellement indésirables (PUA) à l’aide de Microsoft Defender pour point de terminaison sur macOS.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, pua, pus
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 4ddce441f0a1948a774a24cb8ffcbb5d330cf910
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67519575"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-macos"></a>Détecter et bloquer les applications potentiellement indésirables avec Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

La fonctionnalité de protection des applications potentiellement indésirables (PUA) dans Microsoft Defender pour point de terminaison sur macOS peut détecter et bloquer les fichiers PUA sur les points de terminaison de votre réseau.

Ces applications ne sont pas considérées comme des virus, des programmes malveillants ou d’autres types de menaces, mais peuvent effectuer des actions sur des points de terminaison qui affectent leurs performances ou leur utilisation. PuA peut également faire référence à des applications qui sont considérées comme ayant une mauvaise réputation.

Ces applications peuvent augmenter le risque que votre réseau soit infecté par des programmes malveillants, que les infections de programmes malveillants soient plus difficiles à identifier et qu’elles gaspillent les ressources informatiques pour nettoyer les applications.

## <a name="how-it-works"></a>Mode de fonctionnement

Microsoft Defender pour point de terminaison sur macOS peuvent détecter et signaler des fichiers PUA. Lorsqu’ils sont configurés en mode de blocage, les fichiers PUA sont déplacés vers la mise en quarantaine.

Lorsqu’un puA est détecté sur un point de terminaison, Microsoft Defender pour point de terminaison sur macOS présente une notification à l’utilisateur, sauf si les notifications ont été désactivées. Le nom de la menace contient le mot « Application ».

## <a name="configure-pua-protection"></a>Configurer la protection PUA

La protection PUA dans Microsoft Defender pour point de terminaison sur macOS peut être configurée de l’une des manières suivantes :

- **Désactivé** : la protection PUA est désactivée.
- **Audit** : les fichiers PUA sont signalés dans les journaux des produits, mais pas dans Microsoft 365 Defender portail. Aucune notification n’est présentée à l’utilisateur et aucune action n’est effectuée par le produit.
- **Bloc** : les fichiers PUA sont signalés dans les journaux des produits et dans Microsoft 365 Defender portail. Une notification est présentée à l’utilisateur et une action est effectuée par le produit.

> [!WARNING]
> Par défaut, la protection PUA est configurée en mode **Audit** .

Vous pouvez configurer la façon dont les fichiers PUA sont gérés à partir de la ligne de commande ou de la console de gestion.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>Utilisez l’outil en ligne de commande pour configurer la protection PUA :

Dans Terminal, exécutez la commande suivante pour configurer la protection PUA :

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>Utilisez la console de gestion pour configurer la protection PUA :

Dans votre entreprise, vous pouvez configurer la protection PUA à partir d’une console de gestion, telle que JAMF ou Intune, de la même façon que d’autres paramètres de produit. Pour plus d’informations, consultez la section [Paramètres du type de menace](mac-preferences.md#threat-type-settings) de la rubrique [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md).

## <a name="related-topics"></a>Voir aussi

- [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
