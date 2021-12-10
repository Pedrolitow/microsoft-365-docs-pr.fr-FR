---
title: Compatibilité des solutions antivirus avec Defender pour le point de terminaison
description: Découvrez comment Windows Defender fonctionne avec Microsoft Defender pour Endpoint. Découvrez également le fonctionnement de Defender for Endpoint lorsqu’un client tiers anti-programme malveillant est utilisé.
keywords: compatibilité de windows defender, defender, Microsoft Defender pour le point de terminaison, defender pour le point de terminaison, antivirus, mde
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
ms.technology: mde
ms.openlocfilehash: a8384ed28e8c65871f61241dc522461390106be0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61164561"
---
# <a name="antivirus-solution-compatibility-with-microsoft-defender-for-endpoint"></a>Compatibilité des solutions antivirus avec Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-defendercompat-abovefoldlink)

L’agent Microsoft Defender for Endpoint dépend Antivirus Microsoft Defender certaines fonctionnalités telles que l’analyse de fichiers.

> [!IMPORTANT]
> Defender pour le point de terminaison ne respecte pas les paramètres Antivirus Microsoft Defender Exclusions.

Vous devez configurer les mises à jour de l’intelligence de la sécurité sur les appareils Defender for Endpoint, Antivirus Microsoft Defender est l’anti-programme malveillant actif ou non. Pour plus d’informations, [voir Gérer Antivirus Microsoft Defender mises à jour et appliquer les lignes de base.](manage-updates-baselines-microsoft-defender-antivirus.md)

Si un appareil intégré est protégé par un client tiers anti-programme malveillant, Antivirus Microsoft Defender sur ce point de terminaison passe en mode passif.

Antivirus Microsoft Defender continueront de recevoir des mises à jour et le processus *mspeng.exe* sera répertorié comme un service en cours d’exécution. Toutefois, il n’effectue pas d’analyses et ne remplace pas le client anti-programme malveillant tiers en cours d’exécution.

L Antivirus Microsoft Defender interface utilisateur sera désactivée. Les utilisateurs de l’appareil ne pourront pas utiliser Antivirus Microsoft Defender pour effectuer des analyses à la demande ou configurer la plupart des options.

Pour plus d’informations, [consultez la rubrique Antivirus Microsoft Defender et defender pour la compatibilité des points de terminaison.](microsoft-defender-antivirus-compatibility.md)
