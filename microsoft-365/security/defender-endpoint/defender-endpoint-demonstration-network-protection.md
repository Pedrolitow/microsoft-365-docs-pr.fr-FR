---
title: démonstrations de la protection réseau Microsoft Defender pour point de terminaison
description: Montre comment la protection réseau empêche les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux susceptibles d’héberger des escroqueries, des exploits et d’autres contenus malveillants sur Internet.
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
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 1d6693e625c1fd088d7275fc15dcbcde1a67c26c
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68638431"
---
# <a name="network-protection-demonstrations"></a>Démonstrations de la protection réseau

La protection réseau permet de réduire la surface d’attaque de vos appareils à partir d’événements basés sur Internet. Il empêche les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux susceptibles d’héberger des escroqueries, des exploits et d’autres contenus malveillants sur Internet.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10 1709 build 16273, Windows 11
- Antivirus Microsoft Defender

## <a name="powershell-command"></a>Commande PowerShell

```powershell
Set-MpPreference -EnableNetworkProtection Enabled
```

## <a name="rule-states"></a>États de règle

|État|Mode|Valeur numérique|
|---|---|---|
|AuditMode|= Mode Audit|2|
|Activé|= Mode bloc|1|
|Désactivé|= Désactivé|0|

## <a name="verify-configuration"></a>Vérifier la configuration

```powershell
Get-MpPreference
```

## <a name="scenario"></a>Scénario

1. Activez la protection réseau à l’aide de la commande PowerShell :

   ```powershell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

2. À l’aide du navigateur de votre choix (et non de Microsoft Edge*), accédez au [test du site web Protection réseau](https://smartscreentestratings2.net/). Microsoft Edge a mis en place d’autres mesures de sécurité pour protéger contre cette vulnérabilité (SmartScreen).

## <a name="expected-results"></a>Résultats attendus

La navigation vers le site web doit être bloquée et vous devriez voir une notification **de connexion bloquée** .

## <a name="clean-up"></a>Nettoyer

```powershell
Set-MpPreference -EnableNetworkProtection Disabled
```

## <a name="see-also"></a>Voir aussi

[Protection réseau](network-protection.md)

[Microsoft Defender pour point de terminaison - Scénarios de démonstration](defender-endpoint-demonstrations.md)
