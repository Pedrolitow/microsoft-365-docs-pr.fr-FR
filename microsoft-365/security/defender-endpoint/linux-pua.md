---
title: Détecter et bloquer les applications potentiellement indésirables avec Microsoft Defender pour point de terminaison sur Linux
description: Détecter et bloquer les applications potentiellement indésirables (PUA) à l’aide de Microsoft Defender pour point de terminaison sur Linux.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, pua, pus
ms.prod: m365-security
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
ms.technology: mde
ms.openlocfilehash: 004a9d7af09e8a2abb656c29db558d797173edcd
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663599"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-linux"></a>Détecter et bloquer les applications potentiellement indésirables avec Microsoft Defender pour point de terminaison sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

La fonctionnalité de protection des applications potentiellement indésirables dans Defender pour point de terminaison sur Linux peut détecter et bloquer les fichiers PUA sur les points de terminaison de votre réseau.

Ces applications ne sont pas considérées comme des virus, des programmes malveillants ou d’autres types de menaces, mais peuvent effectuer des actions sur des points de terminaison qui affectent leurs performances ou leur utilisation. PuA peut également faire référence à des applications qui sont considérées comme ayant une mauvaise réputation.

Ces applications peuvent augmenter le risque que votre réseau soit infecté par des programmes malveillants, que les infections de programmes malveillants soient plus difficiles à identifier et qu’elles gaspillent les ressources informatiques pour nettoyer les applications.

## <a name="how-it-works"></a>Mode de fonctionnement

Defender pour point de terminaison sur Linux peut détecter et signaler des fichiers PUA. Lorsqu’ils sont configurés en mode de blocage, les fichiers PUA sont déplacés vers la mise en quarantaine.

Lorsqu’un PUA est détecté sur un point de terminaison, Defender pour point de terminaison sur Linux conserve un enregistrement de l’infection dans l’historique des menaces. L’historique peut être visualisé à partir du portail Microsoft 365 Defender ou via l’outil `mdatp` en ligne de commande. Le nom de la menace contient le mot « Application ».

## <a name="configure-pua-protection"></a>Configurer la protection PUA

La protection PUA dans Defender pour point de terminaison sur Linux peut être configurée de l’une des manières suivantes :

- **Désactivé** : la protection PUA est désactivée.
- **Audit** : les fichiers PUA sont signalés dans les journaux des produits, mais pas dans Microsoft 365 Defender. Aucun enregistrement de l’infection n’est stocké dans l’historique des menaces et aucune action n’est effectuée par le produit.
- **Bloc** : les fichiers PUA sont signalés dans les journaux des produits et dans Microsoft 365 Defender. Un enregistrement de l’infection est stocké dans l’historique des menaces et des mesures sont prises par le produit.

> [!WARNING]
> Par défaut, la protection PUA est configurée en mode **Audit** .

Vous pouvez configurer la façon dont les fichiers PUA sont gérés à partir de la ligne de commande ou de la console de gestion.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>Utilisez l’outil en ligne de commande pour configurer la protection PUA :

Dans Terminal, exécutez la commande suivante pour configurer la protection PUA :

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>Utilisez la console de gestion pour configurer la protection PUA :

Dans votre entreprise, vous pouvez configurer la protection PUA à partir d’une console de gestion, telle que Puppet ou Ansible, de la même façon que d’autres paramètres de produit. Pour plus d’informations, consultez la section [Paramètres du type de menace](linux-preferences.md#threat-type-settings) de l’article [Définir les préférences pour Defender pour point de terminaison sur Linux](linux-preferences.md) .

## <a name="related-articles"></a>Articles connexes

- [Définir les préférences pour Defender pour point de terminaison sur Linux](linux-preferences.md)
