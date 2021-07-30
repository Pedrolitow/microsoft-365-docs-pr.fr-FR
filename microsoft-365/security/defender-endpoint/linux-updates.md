---
title: Déployer des mises à jour pour Microsoft Defender pour point de terminaison sur Linux
ms.reviewer: ''
description: Décrit comment déployer des mises à jour pour Microsoft Defender pour Endpoint sur Linux dans les environnements d’entreprise.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, mises à jour, déployer
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
ms.openlocfilehash: 7de99494a373a2e741e7dff2da4b59d94115cc33
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53650498"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-linux"></a>Déployer des mises à jour pour Microsoft Defender pour point de terminaison sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Microsoft publie régulièrement des mises à jour logicielles pour améliorer les performances, la sécurité et fournir de nouvelles fonctionnalités.

> [!WARNING]
> Chaque version de Defender pour Endpoint sur Linux a une date d’expiration, après laquelle elle ne continuera plus à protéger votre appareil. Vous devez mettre à jour le produit avant cette date. Pour vérifier la date d’expiration, exécutez la commande suivante :
> ```bash
> mdatp health --field product_expiration
> ```


Les fonctionnalités de Microsoft Defender pour point de terminaison généralement disponibles sont équivalentes, quel que soit le canal de mise à jour utilisé pour un déploiement (Bêta (Insider), Preview (externe), Actuel (Production)).


Pour mettre à jour Defender pour Endpoint sur Linux manuellement, exécutez l’une des commandes suivantes :

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
