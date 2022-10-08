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
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 3d55b5b97e6a54ed9583843644c07b28129f3beb
ms.sourcegitcommit: 0380a7cd5adb710b80a0ed6fcd349199f1571080
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2022
ms.locfileid: "68334821"
---
# <a name="network-protection-demonstrations"></a>Démonstrations de la protection réseau

La protection réseau permet de réduire la surface d’attaque de vos appareils à partir d’événements basés sur Internet. Il empêche les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux susceptibles d’héberger des escroqueries, des exploits et d’autres contenus malveillants sur Internet.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10 1709 build 16273
- Antivirus Microsoft Defender

## <a name="powershell-command"></a>Commande PowerShell

Set-MpPreference -EnableNetworkProtection activé

### <a name="states"></a>États
- Activé = Mode bloc (1)
- AuditMode = Mode Audit (2)
- Disabled = Off (0)

## <a name="verify-configuration"></a>Vérifier la configuration

Get-MpPreference

## <a name="scenario"></a>Scénario

1. Activer la protection réseau à l’aide de la commande PowerShell : Set-MpPreference -EnableNetworkProtection Activé
2. À l’aide du navigateur de votre choix (et non de Microsoft Edge*), accédez au [test du site web de protection réseau](https://smartscreentestratings2.net/) (Microsoft Edge dispose d’autres mesures de sécurité pour se protéger de cette vulnérabilité (SmartScreen)). 

## <a name="expected-results"></a>Résultats attendus

La navigation vers le site web doit être bloquée et une notification « Connexion bloquée » doit s’afficher.

## <a name="clean-up"></a>Nettoyer

Set-MpPreference -EnableNetworkProtection Désactivé

## <a name="see-also"></a>Voir aussi

[Protection réseau](network-protection.md)

[Microsoft Defender pour point de terminaison - Scénarios de démonstration](defender-endpoint-demonstrations.md)