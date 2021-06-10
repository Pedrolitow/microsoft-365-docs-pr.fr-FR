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
ms.openlocfilehash: f5a0db755f919cb47c4cd284857ddf4e27d16996
ms.sourcegitcommit: 3b9fab82d63aea41d5f544938868c5d2cbf52d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2021
ms.locfileid: "52782884"
---
# <a name="antivirus-solution-compatibility-with-microsoft-defender-for-endpoint"></a>Compatibilité des solutions antivirus avec Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-defendercompat-abovefoldlink)

L’agent Microsoft Defender pour endpoint dépend Antivirus Microsoft Defender certaines fonctionnalités telles que l’analyse de fichiers.

>[!IMPORTANT]
>Defender pour le point de terminaison ne respecte pas les paramètres Antivirus Microsoft Defender Exclusions. 

Vous devez configurer les mises à jour d’intelligence de sécurité sur les appareils Defender for Endpoint, Antivirus Microsoft Defender est le logiciel anti-programme malveillant actif ou non. Pour plus d’informations, [voir Gérer Antivirus Microsoft Defender mises à jour et appliquer les lignes de base.](manage-updates-baselines-microsoft-defender-antivirus.md)

Si un appareil intégré est protégé par un client tiers anti-programme malveillant, Antivirus Microsoft Defender sur ce point de terminaison passe en mode passif.

Antivirus Microsoft Defender continue de recevoir des mises à jour, et le processus *mspeng.exe* est répertorié comme un service en cours d’exécution, mais il n’effectue pas d’analyses et ne remplace pas le client anti-programme malveillant tiers en cours d’exécution.

L’interface Antivirus Microsoft Defender sera désactivée et les utilisateurs de l’appareil ne pourront pas utiliser Antivirus Microsoft Defender pour effectuer des analyses à la demande ou configurer la plupart des options.

Pour plus d’informations, [consultez la rubrique Antivirus Microsoft Defender et defender pour la compatibilité des points de terminaison.](microsoft-defender-antivirus-compatibility.md)
