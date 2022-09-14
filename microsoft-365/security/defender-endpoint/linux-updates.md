---
title: Déployer des mises à jour pour Microsoft Defender pour point de terminaison sur Linux
ms.reviewer: ''
description: Décrit comment déployer des mises à jour pour Microsoft Defender pour point de terminaison sur Linux dans des environnements d’entreprise.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, mises à jour, déployer
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
ms.openlocfilehash: ad5bb0d0c1d49a23dc296f5e01c5a31988473d5f
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67686366"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-linux"></a>Déployer des mises à jour pour Microsoft Defender pour point de terminaison sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Microsoft publie régulièrement des mises à jour logicielles pour améliorer les performances, la sécurité et fournir de nouvelles fonctionnalités.

> [!WARNING]
> Chaque version de Defender pour point de terminaison sur Linux a une date d’expiration, après laquelle elle ne continuera plus à protéger votre appareil. Vous devez mettre à jour le produit avant cette date. Pour vérifier la date d’expiration, exécutez la commande suivante :
> ```bash
> mdatp health --field product_expiration
> ```


Les fonctionnalités Microsoft Defender pour point de terminaison généralement disponibles sont équivalentes, quel que soit le canal de mise à jour utilisé pour un déploiement (Bêta (Insider), Preview (Externe), Current (Production)).


Pour mettre à jour Defender pour point de terminaison sur Linux manuellement, exécutez l’une des commandes suivantes :

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

> [!IMPORTANT]
> Lors de l’intégration de Microsoft Defender pour point de terminaison et defender pour le cloud, l’agent mdatp reçoit automatiquement les mises à jour par défaut.
