---
title: Résoudre les problèmes Microsoft 365 Defender service
description: Trouver des solutions et des solutions de contournement pour les problèmes Microsoft 365 Defender connus
keywords: résoudre Microsoft 365 Defender, résoudre les problèmes, Microsoft Defender pour l’identité, problèmes, module add-on, page de paramètres
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: c4bbc9cd47d3ceb8110a6a2f0e3136a364458abc
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59180905"
---
# <a name="troubleshoot-microsoft-365-defender-service-issues"></a>Résoudre les problèmes Microsoft 365 Defender service

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Cette section traite des problèmes qui peuvent survenir lorsque vous utilisez le service Microsoft 365 Defender service.

## <a name="i-dont-see-microsoft-365-defender-content"></a>Je ne vois pas Microsoft 365 Defender contenu

Si vous ne voyez pas de fonctionnalités dans le volet de navigation, telles que les incidents, le centre de gestion des actions ou le hunting dans votre portail, vous devez vérifier que votre client dispose des licences appropriées.

Si vous souhaitez en savoir plus, consultez la page[Conditions préalables](prerequisites.md).

## <a name="microsoft-defender-for-identity-alerts-are-not-showing-up-in-the-microsoft-365-defender-incidents"></a>Les alertes Microsoft Defender pour l’identité ne s’affichent pas dans Microsoft 365 Defender incidents

Si Vous avez déployé Microsoft Defender pour l’identité dans votre environnement, mais que vous ne voyez pas les alertes Defender for Identity dans le cadre des incidents Microsoft 365 Defender, vous devez vous assurer que l’intégration de Microsoft Cloud App Security et defender pour l’identité est activée.

Pour plus d’informations, [voir Microsoft Defender pour l’intégration de l’identité.](/cloud-app-security/mdi-integration)

## <a name="where-is-the-settings-page-for-turning-on-the-service"></a>Où se trouve la page des paramètres pour l’ment du service ?

Pour activer la Microsoft 365 Defender, accédez **Paramètres** à partir du volet de navigation du portail Microsoft 365 Defender web. Cet élément de navigation n’est visible que si vous avez les autorisations et [licences requises.](m365d-enable.md#check-license-eligibility-and-required-permissions)

## <a name="how-do-i-create-an-exception-for-my-fileurl"></a>Comment créer une exception pour mon fichier/URL ?

Un faux positif est un fichier ou une URL détecté comme malveillant, mais qui n’est pas une menace. Vous pouvez créer des indicateurs et définir des exclusions pour débloquer et autoriser certains fichiers/URL. Voir [Adresse faux positifs/négatifs dans Defender pour le point de terminaison.](/microsoft-365/security/defender-endpoint/defender-endpoint-false-positives-negatives)
