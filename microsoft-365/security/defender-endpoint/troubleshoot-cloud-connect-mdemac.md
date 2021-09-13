---
title: Résoudre les problèmes de connectivité cloud pour Microsoft Defender pour endpoint sur macOS
description: Cette rubrique décrit comment résoudre les problèmes de connectivité cloud pour Microsoft Defender pour endpoint sur macOS
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, déployer, désinstallation, intune, jamf, macos,pératin, mojave, high sierra
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-lsaldanha
author: lovina-saldanha
localization_priority: normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 291cd3016dcb4e1a321f39b4d2731ce2068b6544
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59203856"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Résoudre les problèmes de connectivité cloud pour Microsoft Defender pour endpoint sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plateforme** macOS

Cette rubrique décrit comment résoudre les problèmes de connectivité cloud pour Microsoft Defender pour Endpoint sur macOS.

## <a name="run-the-connectivity-test"></a>Exécuter le test de connectivité
Pour tester si Defender pour point de terminaison sur Mac peut communiquer avec le cloud avec les paramètres réseau actuels, exécutez un test de connectivité à partir de la ligne de commande :

```Bash
mdatp connectivity test
```

sortie attendue :
```Bash
Testing connection with https://cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://eu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://wu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://x.cp.wd.microsoft.com/api/report ... [OK]
Testing connection with https://winatp-gw-cus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-eus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-weu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-neu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-ukw.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-uks.microsoft.com/test ... [OK]
Testing connection with https://eu-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://us-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://uk-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://v20.events.data.microsoft.com/ping ... [OK]
```

Si le test de connectivité échoue, vérifiez si [](microsoft-defender-endpoint-mac.md#network-connections) l’appareil dispose d’un accès à Internet et si l’un des points de terminaison requis par le produit est bloqué par un proxy ou un pare-feu.

Les échecs avec erreur d’erreur 35 ou 60 indiquent le rejet de l’épinglage de certificat, ce qui indique un problème potentiel avec l’inspection SSL ou HTTPS. Consultez les instructions ci-dessous concernant la configuration de l’inspection SSL.

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-proxy-autoconfig-pac-or-with-web-proxy-autodiscovery-protocol-wpad"></a>Étapes de résolution des problèmes pour les environnements sans proxy ou avec la mise en conférence automatique du proxy (PAC) ou avec le protocole WPAD (Web Proxy Autodiscovery Protocol)
Utilisez la procédure suivante pour vérifier qu’une connexion n’est pas bloquée dans un environnement sans proxy ou avec la mise en service automatique du proxy (PAC) ou avec le protocole WPAD (Web Proxy Autodiscovery Protocol).

Si un proxy ou un pare-feu bloque le trafic anonyme, assurez-vous que le trafic anonyme est autorisé dans les URL répertoriées précédemment.

> [!WARNING]
> Les proxies authentifiés ne sont pas pris en charge. Assurez-vous que seuls pac, WPAD ou un proxy statique est utilisé. L’inspection et l’interception des proxies SSL ne sont pas non plus pris en charge pour des raisons de sécurité. Configurez une exception pour l’inspection SSL et votre serveur proxy afin de transmettre directement les données de Microsoft Defender for Endpoint sur macOS aux URL pertinentes sans interception. L’ajout de votre certificat d’interception au magasin global n’autorise pas l’interception.
Pour tester qu’une connexion n’est pas bloquée : dans un navigateur tel que Microsoft Edge pour Mac ou Safari, ouvrez https://x.cp.wd.microsoft.com/api/report et https://cdn.x.cp.wd.microsoft.com/ping .

Éventuellement, dans Terminal, exécutez la commande suivante :

```Bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping' 
```

La sortie de cette commande doit être similaire à celle-ci :
```bash
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```
