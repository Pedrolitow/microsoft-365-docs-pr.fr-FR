---
title: Résoudre les problèmes de connectivité cloud pour Microsoft Defender pour point de terminaison sur macOS
description: Cette rubrique explique comment résoudre les problèmes de connectivité cloud pour Microsoft Defender pour point de terminaison sur macOS
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, deploy, uninstallation, intune, jamf, macos, catalina, mojave, high sierra
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 592ef3bc4c51685393e95c717b5cb605a139b49d
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67684340"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Résoudre les problèmes de connectivité cloud pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plateforme** macOS

Cette rubrique explique comment résoudre les problèmes de connectivité cloud pour Microsoft Defender pour point de terminaison sur macOS.

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

Si le test de connectivité échoue, vérifiez si l’appareil a accès à Internet et si [l’un des points de terminaison requis par le produit](microsoft-defender-endpoint-mac.md#network-connections) est bloqué par un proxy ou un pare-feu.

Les échecs avec l’erreur curl 35 ou 60 indiquent le rejet de l’épinglage de certificat, ce qui indique un problème potentiel avec l’inspection SSL ou HTTPS. Consultez les instructions ci-dessous concernant la configuration de l’inspection SSL.

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-proxy-autoconfig-pac-or-with-web-proxy-autodiscovery-protocol-wpad"></a>Étapes de résolution des problèmes pour les environnements sans proxy, avec la configuration automatique du proxy (PAC) ou avec le protocole WPAD (Web Proxy Autodiscovery Protocol)
Utilisez la procédure suivante pour vérifier qu’une connexion n’est pas bloquée dans un environnement sans proxy ou avec la configuration automatique du proxy (PAC) ou avec le protocole WPAD (Web Proxy Autodiscovery Protocol).

Si un proxy ou un pare-feu bloque le trafic anonyme, assurez-vous que le trafic anonyme est autorisé dans les URL précédemment répertoriées.

> [!WARNING]
> Les proxys authentifiés ne sont pas pris en charge. Vérifiez que seuls pac, WPAD ou proxy statique sont utilisés. Les proxys d’inspection et d’interception SSL ne sont pas non plus pris en charge pour des raisons de sécurité. Configurez une exception pour l’inspection SSL et votre serveur proxy pour passer directement les données de Microsoft Defender pour point de terminaison sur macOS aux URL pertinentes sans interception. L’ajout de votre certificat d’interception au magasin global n’autorise pas l’interception.
Pour tester qu’une connexion n’est pas bloquée : dans un navigateur tel que Microsoft Edge pour Mac ou Safari ouvert https://x.cp.wd.microsoft.com/api/report et https://cdn.x.cp.wd.microsoft.com/ping.

Si vous le souhaitez, dans Terminal, exécutez la commande suivante :

```Bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping' 
```

La sortie de cette commande doit être similaire à :
```bash
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```
