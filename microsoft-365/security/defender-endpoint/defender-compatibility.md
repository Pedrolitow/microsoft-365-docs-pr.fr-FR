---
title: Compatibilité des solutions antivirus avec Defender pour point de terminaison
description: Découvrez comment Windows Defender fonctionne avec Microsoft Defender pour point de terminaison. Découvrez également le fonctionnement de Defender pour point de terminaison lorsqu’un client anti-programme malveillant tiers est utilisé.
keywords: compatibilité windows defender, defender, Microsoft Defender pour point de terminaison, defender pour point de terminaison, antivirus, mde
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.date: 05/06/2021
ms.subservice: mde
ms.openlocfilehash: 2fcab2ab95623b8d2a7d551b697765bc317d2e42
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67679798"
---
# <a name="antivirus-solution-compatibility-with-microsoft-defender-for-endpoint"></a>Compatibilité des solutions antivirus avec Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-defendercompat-abovefoldlink)

L’agent Microsoft Defender pour point de terminaison dépend de l’Antivirus Microsoft Defender pour certaines fonctionnalités telles que l’analyse de fichiers.

> [!IMPORTANT]
> Defender pour point de terminaison n’adhère pas aux paramètres d’exclusions de l’antivirus Microsoft Defender.

Vous devez configurer les mises à jour du renseignement de sécurité sur les appareils Defender pour point de terminaison, que l’antivirus Microsoft Defender soit ou non le logiciel anti-programme malveillant actif. Pour plus d’informations, consultez [Gérer les mises à jour de l’Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).

Si un appareil intégré est protégé par un client anti-programme malveillant tiers, l’Antivirus Microsoft Defender sur ce point de terminaison passe en mode passif.

L’Antivirus Microsoft Defender continuera de recevoir des mises à jour, et le processus *demspeng.exe* sera répertorié en tant qu’exécution d’un service. Toutefois, il n’effectue pas d’analyses et ne remplace pas le client anti-programme malveillant tiers en cours d’exécution.

L’interface antivirus Microsoft Defender sera désactivée. Les utilisateurs sur l’appareil ne pourront pas utiliser l’Antivirus Microsoft Defender pour effectuer des analyses à la demande ou configurer la plupart des options.

Pour plus d’informations, consultez la [rubrique sur la compatibilité de l’antivirus Microsoft Defender et de Defender pour point de terminaison](microsoft-defender-antivirus-compatibility.md).
