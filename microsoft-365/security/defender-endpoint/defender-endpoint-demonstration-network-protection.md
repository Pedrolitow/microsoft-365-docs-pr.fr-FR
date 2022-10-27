---
title: Microsoft Defender pour point de terminaison Démonstrations de protection réseau
description: Montre comment la protection du réseau empêche les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux susceptibles d’héberger des escroqueries par hameçonnage, des attaques et d’autres contenus malveillants sur Internet.
keywords: protection réseau, protection contre les escroqueries par hameçonnage, protection contre les attaques, protection contre les contenus malveillants, démonstration
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
ms.openlocfilehash: 41a1a023fbfdc71ceec060dda84349ff6776175d
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68732754"
---
# <a name="network-protection-demonstrations"></a>Démonstrations de protection réseau

La protection réseau permet de réduire la surface d’attaque de vos appareils à partir d’événements Basés sur Internet. Il empêche les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux susceptibles d’héberger des escroqueries par hameçonnage, des attaques et d’autres contenus malveillants sur Internet.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10 1709 build 16273, Windows 11
- Antivirus Microsoft Defender

## <a name="powershell-command"></a>Commande PowerShell

```powershell
Set-MpPreference -EnableNetworkProtection Enabled
```

## <a name="rule-states"></a>États de règle

|État | Mode| Valeur numérique |
|:---|:---|:---|
| Désactivé | = Désactivé | 0 |
| Activé | = Mode bloc | 1 |
| Audit | = Mode d’audit | 2 |

## <a name="verify-configuration"></a>Vérifier la configuration

```powershell
Get-MpPreference
```

## <a name="scenario"></a>Scénario

1. Activez la protection réseau à l’aide de la commande powershell :

   ```powershell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

2. À l’aide du navigateur de votre choix (et non Microsoft Edge*), accédez au [test du site web Protection réseau](https://smartscreentestratings2.net/). Microsoft Edge a mis en place d’autres mesures de sécurité pour se protéger contre cette vulnérabilité (SmartScreen).

## <a name="expected-results"></a>Résultats attendus

La navigation vers le site web doit être bloquée et une notification **Connexion bloquée** doit s’afficher.

## <a name="clean-up"></a>Nettoyer

```powershell
Set-MpPreference -EnableNetworkProtection Disabled
```

## <a name="see-also"></a>Voir aussi

[Protection réseau](network-protection.md)

[Microsoft Defender pour point de terminaison - scénarios de démonstration](defender-endpoint-demonstrations.md)
