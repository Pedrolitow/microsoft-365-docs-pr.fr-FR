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
ms.openlocfilehash: 6dca58070d21271ffc832bcd628679303736f99e
ms.sourcegitcommit: ebb1c3b4d94058a58344317beb9475c8a2eae9a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2021
ms.locfileid: "53108138"
---
# <a name="configure-microsoft-defender-for-endpoint-on-linux-for-static-proxy-discovery"></a>Configurer Microsoft Defender pour le point de terminaison sur Linux pour la découverte de proxy statique

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

Microsoft Defender pour le point de terminaison peut découvrir un serveur proxy à l’aide de ```HTTPS_PROXY``` la variable d’environnement. Ce paramètre doit être configuré **à** la fois au moment de l’installation et après l’installation du produit.

## <a name="installation-time-configuration"></a>Configuration de l’heure d’installation

Lors de l’installation, ```HTTPS_PROXY``` la variable d’environnement doit être transmise au gestionnaire de package. Le gestionnaire de package peut lire cette variable de l’une des manières suivantes :

- La ```HTTPS_PROXY``` variable est définie avec la ligne suivante ```/etc/environment``` :

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

Notez que l’installation et la désinstallation ne échouent pas nécessairement si un proxy est requis mais n’est pas configuré. Toutefois, la télémétrie n’est pas envoyée et l’opération peut prendre beaucoup plus de temps en raison de délai d’accès réseau.

## <a name="post-installation-configuration"></a>Configuration post-installation
  
Après l’installation, `HTTPS_PROXY` la variable d’environnement doit être définie dans le fichier de service Defender for Endpoint. Pour ce faire, ouvrez dans `/lib/systemd/system/mdatp.service` un éditeur de texte lors de l’exécution en tant qu’utilisateur racine. Vous pouvez ensuite propager la variable au service de deux manières :

    > [!NOTE]
    > On CentOS or RedHat Linux distributions the location of the Endpoint service file is `/usr/lib/systemd/system/mdatp.service`.

- Décompressez la ligne `#Environment="HTTPS_PROXY=http://address:port"` et spécifiez votre adresse proxy statique.

- Ajoutez une ligne `EnvironmentFile=/path/to/env/file` . Ce chemin d’accès peut pointer vers ou un fichier personnalisé, lequel doit `/etc/environment` ajouter la ligne suivante :
  
    ```bash
    HTTPS_PROXY="http://proxy.server:port/"
    ```

Après avoir modifié le `mdatp.service` fichier, enregistrez-le et fermez-le. Redémarrez le service afin que les modifications soient appliquées. Dans Ubuntu, cela implique deux commandes :  

```bash
systemctl daemon-reload; systemctl restart mdatp
```
