---
title: Microsoft Defender pour point de terminaison sur la découverte de proxy statique Linux
ms.reviewer: ''
description: Décrit comment configurer Microsoft Defender pour endpoint sur Linux, pour la découverte de proxy statique.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, installation, proxy
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 59a9ae07b6d8073bd46a36a803abda3b419cc4cb33e3739250474a2217fbbf8a
ms.sourcegitcommit: 4f074a8598a430344a2361728a64b8b8c0e1d215
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2021
ms.locfileid: "54523368"
---
# <a name="configure-microsoft-defender-for-endpoint-on-linux-for-static-proxy-discovery"></a>Configurer Microsoft Defender pour le point de terminaison sur Linux pour la découverte de proxy statique

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Microsoft Defender pour point de terminaison peut découvrir un serveur proxy à l’aide de `HTTPS_PROXY` la variable d’environnement. Ce paramètre doit être configuré **à** la fois au moment de l’installation et après l’installation du produit.

## <a name="installation-time-configuration"></a>Configuration de l’heure d’installation

Lors de l’installation, `HTTPS_PROXY` la variable d’environnement doit être transmise au gestionnaire de package. Le gestionnaire de package peut lire cette variable de l’une des manières suivantes :

- La `HTTPS_PROXY` variable est définie avec la ligne suivante `/etc/environment` :

  ```bash
  HTTPS_PROXY="http://proxy.server:port/"
  ```

- La `HTTPS_PROXY` variable est définie dans la configuration globale du gestionnaire de packages. Par exemple, dans Ubuntu 18.04, vous pouvez ajouter la ligne suivante à `/etc/apt/apt.conf.d/proxy.conf` :

  ```bash
  Acquire::https::Proxy "http://proxy.server:port/";
  ```

  > [!CAUTION]
  > Notez que deux méthodes ci-dessus peuvent définir le proxy à utiliser pour d’autres applications sur votre système. Utilisez cette méthode avec précaution, ou uniquement s’il s’agit d’une configuration globale.

- La variable est précédée des commandes `HTTPS_PROXY` d’installation ou de désinstallation. Par exemple, avec le gestionnaire de package APT, prédépender la variable comme suit lors de l’installation de Microsoft Defender pour Endpoint :

  ```bash
  HTTPS_PROXY="http://proxy.server:port/" apt install mdatp
  ```

  > [!NOTE]
  > N’ajoutez pas de sudo entre la définition de variable d’environnement et apt, sinon la variable ne sera pas propagée.

La `HTTPS_PROXY` variable d’environnement peut être définie de la même manière lors de la désinstallation.

Notez que l’installation et la désinstallation ne échouent pas nécessairement si un proxy est requis mais non configuré. Toutefois, la télémétrie n’est pas envoyée et l’opération peut prendre beaucoup plus de temps en raison de délai d’accès réseau.

## <a name="post-installation-configuration"></a>Configuration post-installation

Après l’installation, `HTTPS_PROXY` la variable d’environnement doit être définie dans le fichier de service Defender for Endpoint. Pour ce faire, exécutez `sudo systemctl edit --full mdatp.service` .
Vous pouvez ensuite propager la variable au service de deux manières :

- Décompressez la ligne `#Environment="HTTPS_PROXY=http://address:port"` et spécifiez votre adresse proxy statique.

- Ajoutez une ligne `EnvironmentFile=/path/to/env/file` . Ce chemin d’accès peut pointer vers ou un fichier personnalisé, lequel doit `/etc/environment` ajouter la ligne suivante :

  ```bash
  HTTPS_PROXY="http://proxy.server:port/"
  ```

Après avoir modifié , enregistrez le fichier et redémarrez le service afin que les modifications soient appliquées à `mdatp.service` l’aide des commandes suivantes :

```bash
sudo systemctl daemon-reload; sudo systemctl restart mdatp
```
