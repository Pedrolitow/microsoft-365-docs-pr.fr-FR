---
title: Résoudre les problèmes de licence pour Microsoft Defender pour point de terminaison sur Mac
description: Résoudre les problèmes de licence dans Microsoft Defender pour point de terminaison sur Mac.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, performance, catalina, big sur, monterey, ventura, mde pour mac
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
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 14812ed31800a65c6d0840d18840677ef74e558d
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68768124"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Résoudre les problèmes de licence pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison sur macOS](microsoft-defender-endpoint-mac.md)
 [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
[ Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Pendant que vous effectuez [des Microsoft Defender pour point de terminaison sur macOS](microsoft-defender-endpoint-mac.md) et des tests de [déploiement manuel](mac-install-manually.md) ou une preuve de concept (PoC), vous pouvez obtenir l’erreur suivante :

:::image type="content" source="images/no-license-found.png" alt-text="Erreur de licence" lightbox="images/no-license-found.png":::

**Message:** 

Aucune licence trouvée

Il semble que votre organisation ne dispose pas d’une licence pour Microsoft 365 Entreprise abonnement.

Contactez votre administrateur pour obtenir de l'aide.

**Cause :** 

Vous avez déployé et/ou installé le Microsoft Defender pour point de terminaison sur le package macOS (« Télécharger le package d’installation »), mais vous n’avez peut-être pas exécuté le script de configuration (« Télécharger le package d’intégration ») ou vous n’avez pas attribué de licence à l’utilisateur.

Vous pouvez également rencontrer cette erreur lorsque l’Microsoft Defender pour point de terminaison sur l’agent macOS n’est pas à jour. 


**Solution :**

Suivez les instructions MicrosoftDefenderATPOnboardingMacOs.py documentées ici : [Configuration du client](mac-install-manually.md#client-configuration)

Pour les scénarios où Microsoft Defender pour point de terminaison sur macOS n’est pas à jour, vous devez mettre à jour l’agent. 
