---
title: Déployer les mises à jour de Microsoft Defender ATP pour Linux
ms.reviewer: ''
description: Décrit comment déployer des mises à jour pour Microsoft Defender ATP pour Linux dans les environnements d'entreprise.
keywords: microsoft, defender, atp, linux, mises à jour, déployer
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
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 2e4ea4942446317aef90288da9fb181935503fa9
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51687465"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-linux"></a>Déployer les mises à jour de Microsoft Defender pour Endpoint sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l'expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

Microsoft publie régulièrement des mises à jour logicielles pour améliorer les performances, la sécurité et fournir de nouvelles fonctionnalités.

> [!WARNING]
> Chaque version de Defender pour Endpoint pour Linux a une date d'expiration, après laquelle elle ne continuera plus à protéger votre appareil. Vous devez mettre à jour le produit avant cette date. Pour vérifier la date d'expiration, exécutez la commande suivante :
> ```bash
> mdatp health --field product_expiration
> ```

Pour mettre à jour Defender pour Endpoint pour Linux manuellement, exécutez l'une des commandes suivantes :

## <a name="rhel-and-variants-centos-and-oracle-linux"></a>RHEL et variantes (CentOS et Oracle Linux)

```bash
sudo yum update mdatp
```

## <a name="sles-and-variants"></a>SLES et variantes

```bash
sudo zypper update mdatp
```

## <a name="ubuntu-and-debian-systems"></a>Systèmes Ubuntu et Debian

```bash
sudo apt-get install --only-upgrade mdatp
```
