---
title: Résoudre les problèmes de connectivité cloud pour Microsoft Defender pour endpoint sur Linux
ms.reviewer: ''
description: Découvrez comment résoudre les problèmes de connectivité cloud pour Microsoft Defender pour Endpoint sur Linux
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, cloud, connectivité, communication
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
ms.openlocfilehash: 4f547e6701e0b22c2d55d0fa68a236f85b821a11
ms.sourcegitcommit: 43adb0d91af234c34e22d450a9c1d26aa745c2ca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2021
ms.locfileid: "60478912"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Résoudre les problèmes de connectivité cloud pour Microsoft Defender pour endpoint sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="run-the-connectivity-test"></a>Exécuter le test de connectivité

Pour tester si Defender pour Endpoint sur Linux peut communiquer avec le cloud avec les paramètres réseau actuels, exécutez un test de connectivité à partir de la ligne de commande :

```bash
mdatp connectivity test
```

sortie attendue :

```output
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

Si le test de connectivité échoue, vérifiez si [](microsoft-defender-endpoint-linux.md#network-connections) l’appareil dispose d’un accès à Internet et si l’un des points de terminaison requis par le produit est bloqué par un proxy ou un pare-feu.

Les échecs avec erreur d’erreur 35 ou 60 indiquent le rejet de l’épinglage du certificat. Vérifiez si la connexion est sous inspection SSL ou HTTPS. Si c’est le cas, ajoutez Microsoft Defender pour le point de terminaison à la liste d’accès.

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-transparent-proxy"></a>Étapes de résolution des problèmes pour les environnements sans proxy ou avec proxy transparent

Pour vérifier qu’une connexion n’est pas bloquée dans un environnement sans proxy ou avec un proxy transparent, exécutez la commande suivante dans le terminal :

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

La sortie de cette commande doit être similaire à celle-ci :

```Output
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```

## <a name="troubleshooting-steps-for-environments-with-static-proxy"></a>Étapes de résolution des problèmes pour les environnements avec proxy statique

> [!WARNING]
> Les pacs, WPAD et les proxies authentifiés ne sont pas pris en charge. Assurez-vous que seul un proxy statique ou transparent est utilisé.
>
> L’inspection et l’interception des proxies SSL ne sont pas non plus pris en charge pour des raisons de sécurité. Configurez une exception pour l’inspection SSL et votre serveur proxy afin de transmettre directement les données de Defender pour Endpoint sur Linux aux URL pertinentes sans interception. L’ajout de votre certificat d’interception au magasin global n’autorise pas l’interception.

Si un proxy statique est requis, ajoutez un paramètre de proxy à la commande ci-dessus, où correspond à l’adresse `proxy_address:port` proxy et au port :

```bash
curl -x http://proxy_address:port -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Veillez à utiliser les mêmes adresse et port proxy que celui configuré dans le `/lib/system/system/mdatp.service` fichier. Vérifiez la configuration de votre proxy en cas d’erreurs provenant des commandes ci-dessus.

Pour définir le proxy pour mdatp, utilisez la commande suivante :

```bash
mdatp config proxy set --value http://address:port 
```


En cas de réussite, tentez un autre test de connectivité à partir de la ligne de commande :

```bash
mdatp connectivity test
```

Si le problème persiste, contactez le support technique.

## <a name="resources"></a>Ressources

- Pour plus d’informations sur la configuration du produit afin qu’il utilise un proxy statique, voir [Configurer Microsoft Defender pour endpoint](linux-static-proxy-configuration.md)pour la découverte de proxy statique.
