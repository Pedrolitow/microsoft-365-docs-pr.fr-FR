---
title: Compatibilité des solutions antivirus avec Defender pour le point de terminaison
description: Découvrez comment Windows Defender fonctionne avec Microsoft Defender pour Endpoint et comment il fonctionne lorsqu’un client anti-programme malveillant tiers est utilisé.
keywords: compatibilité de windows defender, defender, Microsoft Defender pour le point de terminaison, defender pour le point de terminaison, antivirus, mde
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.date: 05/06/2021
ms.technology: mde
ms.openlocfilehash: 84c523b721596d9c467f01cf6b8a0685b2091669
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52274879"
---
# <a name="antivirus-solution-compatibility-with-microsoft-defender-for-endpoint"></a>Compatibilité des solutions antivirus avec Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-defendercompat-abovefoldlink)

L’agent Microsoft Defender pour points de terminaison dépend de l’Antivirus Microsoft Defender pour certaines fonctionnalités telles que l’analyse de fichiers.

>[!IMPORTANT]
>Defender pour le point de terminaison ne respecte pas les paramètres d’exclusions de l’Antivirus Microsoft Defender. 

Vous devez configurer les mises à jour d’intelligence de sécurité sur les appareils Defender for Endpoint, que l’Antivirus Microsoft Defender soit ou non le logiciel anti-programme malveillant actif. Pour plus d’informations, voir Gérer les mises à [jour de l’Antivirus Microsoft Defender et appliquer les lignes de base.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus.md)

Si un appareil intégré est protégé par un client tiers anti-programme malveillant, l’Antivirus Microsoft Defender sur ce point de terminaison passe en mode passif.

L’Antivirus Microsoft Defender continue de recevoir des mises à jour et le processus *mspeng.exe* est répertorié comme un service en cours d’exécution, mais il n’effectue pas d’analyses et ne remplace pas le client anti-programme malveillant tiers en cours d’exécution.

L’interface antivirus Microsoft Defender sera désactivée et les utilisateurs de l’appareil ne pourront pas utiliser l’Antivirus Microsoft Defender pour effectuer des analyses à la demande ou configurer la plupart des options.

Pour plus d’informations, voir la rubrique sur la compatibilité de l’Antivirus Microsoft Defender et de Defender pour les [points de terminaison.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility)
