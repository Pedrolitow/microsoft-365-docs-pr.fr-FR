---
title: Microsoft Defender pour point de terminaison sur la découverte de proxy statique Linux
ms.reviewer: ''
description: Décrit comment configurer Microsoft Defender pour point de terminaison sur Linux pour la découverte de proxy statique.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, installation, proxy
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
- m365-security-compliance
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 37fa8cf1acf8c557401a698710495d39882bf318
ms.sourcegitcommit: 2dedd0f594b817779e034afa6c4418def2382a22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2022
ms.locfileid: "67796828"
---
# <a name="configure-microsoft-defender-for-endpoint-on-linux-for-static-proxy-discovery"></a>Configurer Microsoft Defender pour point de terminaison sur Linux pour la découverte de proxy statique

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Microsoft Defender pour point de terminaison pouvez découvrir un serveur proxy à l’aide de la variable d’environnement`HTTPS_PROXY`. Ce paramètre doit être configuré à la **fois** au moment de l’installation et après l’installation du produit.

## <a name="installation-time-configuration"></a>Configuration de l’heure d’installation

Pendant l’installation, la `HTTPS_PROXY` variable d’environnement doit être passée au gestionnaire de package. Le gestionnaire de package peut lire cette variable de l’une des manières suivantes :

- La `HTTPS_PROXY` variable est définie avec `/etc/environment` la ligne suivante :

  ```bash
  HTTPS_PROXY="http://proxy.server:port/"
  ```

- La `HTTPS_PROXY` variable est définie dans la configuration globale du gestionnaire de package. Par exemple, dans Ubuntu 18.04, vous pouvez ajouter la ligne suivante à `/etc/apt/apt.conf.d/proxy.conf`:

  ```bash
  Acquire::https::Proxy "http://proxy.server:port/";
  ```

  > [!CAUTION]
  > Notez que les deux méthodes ci-dessus peuvent définir le proxy à utiliser pour d’autres applications sur votre système. Utilisez cette méthode avec précaution, ou uniquement si elle est destinée à être une configuration globale.

- La `HTTPS_PROXY` variable est ajoutée aux commandes d’installation ou de désinstallation. Par exemple, avec le gestionnaire de package APT, ajoutez la variable comme suit lors de l’installation de Microsoft Defender pour point de terminaison :

  ```bash
  HTTPS_PROXY="http://proxy.server:port/" apt install mdatp
  ```

  > [!NOTE]
  > N’ajoutez pas sudo entre la définition de variable d’environnement et apt, sinon la variable ne sera pas propagée.

La `HTTPS_PROXY` variable d’environnement peut être définie de la même façon lors de la désinstallation.

Notez que l’installation et la désinstallation ne échoueront pas nécessairement si un proxy est requis, mais pas configuré. Toutefois, les données de télémétrie ne seront pas envoyées et l’opération peut prendre beaucoup plus de temps en raison des délais d’expiration du réseau.

## <a name="post-installation-configuration"></a>Configuration après l’installation

Après l’installation, la `HTTPS_PROXY` variable d’environnement doit être définie dans le fichier de service Defender pour point de terminaison. Pour ce faire, exécutez `sudo systemctl edit --full mdatp.service`.
Vous pouvez ensuite propager la variable au service de deux manières :

- Supprimez les marques de commentaire de la ligne `#Environment="HTTPS_PROXY=http://address:port"` et spécifiez votre adresse proxy statique.

- Ajouter une ligne `EnvironmentFile=/path/to/env/file`. Ce chemin d’accès peut pointer vers `/etc/environment` ou un fichier personnalisé, qui doit ajouter la ligne suivante :

  ```bash
  HTTPS_PROXY="http://proxy.server:port/"
  ```

Après la `mdatp.service`modification, enregistrez le fichier et redémarrez le service afin que les modifications puissent être appliquées à l’aide des commandes suivantes :

```bash
sudo systemctl daemon-reload; sudo systemctl restart mdatp
```
> [!NOTE]
> Pour supprimer les ajouts que vous avez pu effectuer avant la désinstallation`mdatp`, supprimez le fichier personnalisé.`/etc/systemd/system`
