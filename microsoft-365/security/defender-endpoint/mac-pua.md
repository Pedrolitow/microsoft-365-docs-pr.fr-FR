---
title: Détecter et bloquer les applications potentiellement indésirables avec Microsoft Defender pour point de terminaison sur Mac
description: Détectez et bloquez les applications potentiellement indésirables (PUA) à l’aide de Microsoft Defender pour point de terminaison sur macOS.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, pua, pus, catalina, big sur, monterey, ventura, mde pour mac
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
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 6469537490dfafff5aa3ea62874e4293fe810547
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68769026"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-macos"></a>Détecter et bloquer les applications potentiellement indésirables avec Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

La fonctionnalité de protection des applications potentiellement indésirables (PUA) dans Microsoft Defender pour point de terminaison sur macOS peut détecter et bloquer les fichiers PUA sur les points de terminaison de votre réseau.

Ces applications ne sont pas considérées comme des virus, des programmes malveillants ou d’autres types de menaces, mais peuvent effectuer des actions sur des points de terminaison qui affectent négativement leurs performances ou leur utilisation. PuA peut également faire référence à des applications qui sont considérées comme ayant une mauvaise réputation.

Ces applications peuvent augmenter le risque d’infection de votre réseau par des programmes malveillants, rendre les infections de programmes malveillants plus difficiles à identifier et gaspiller les ressources informatiques dans le nettoyage des applications.

## <a name="how-it-works"></a>Mode de fonctionnement

Microsoft Defender pour point de terminaison sur macOS peut détecter et signaler les fichiers PUA. Lorsqu’ils sont configurés en mode bloquant, les fichiers PUA sont déplacés vers la mise en quarantaine.

Lorsqu’un puA est détecté sur un point de terminaison, Microsoft Defender pour point de terminaison sur macOS présente une notification à l’utilisateur, sauf si les notifications ont été désactivées. Le nom de la menace contient le mot « Application ».

## <a name="configure-pua-protection"></a>Configurer la protection puA

La protection PUA dans Microsoft Defender pour point de terminaison sur macOS peut être configurée de l’une des manières suivantes :

- **Désactivé** : la protection puA est désactivée.
- **Audit** : les fichiers PUA sont signalés dans les journaux du produit, mais pas dans Microsoft 365 Defender portail. Aucune notification n’est présentée à l’utilisateur et aucune action n’est effectuée par le produit.
- **Bloquer** : les fichiers PUA sont signalés dans les journaux du produit et dans Microsoft 365 Defender portail. Une notification est présentée à l’utilisateur et une action est effectuée par le produit.

> [!WARNING]
> Par défaut, la protection PUA est configurée en mode **Audit** .

Vous pouvez configurer la façon dont les fichiers PUA sont gérés à partir de la ligne de commande ou de la console de gestion.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>Utilisez l’outil en ligne de commande pour configurer la protection puA :

Dans Terminal, exécutez la commande suivante pour configurer la protection puA :

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>Utilisez la console de gestion pour configurer la protection puA :

Dans votre entreprise, vous pouvez configurer la protection puA à partir d’une console de gestion, telle que JAMF ou Intune, de la même façon que d’autres paramètres de produit sont configurés. Pour plus d’informations, consultez la section [Paramètres du type](mac-preferences.md#threat-type-settings) de menace de la rubrique [Définir des préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md).

## <a name="related-topics"></a>Voir aussi

- [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
