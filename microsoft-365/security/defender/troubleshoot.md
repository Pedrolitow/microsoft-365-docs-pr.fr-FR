---
title: Résoudre les problèmes de service Microsoft 365 Defender
description: Trouver des solutions et des solutions de contournement pour les problèmes connus de Microsoft 365 Defender
keywords: résoudre les problèmes de protection Microsoft contre les menaces, dépannage, Azure ATP, problèmes, module supplémentaire, page de paramètres
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
ms.openlocfilehash: a2cd27bf7bf8b1c4931b9d768f3a6b5e5f2a0d93
ms.sourcegitcommit: e0a96e08b7dc29e074065e69a2a86fc3cf0dad01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2021
ms.locfileid: "51592035"
---
# <a name="troubleshoot-microsoft-365-defender-service-issues"></a>Résoudre les problèmes de service Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Cette section traite des problèmes qui peuvent survenir lorsque vous utilisez le service Microsoft 365 Defender.

## <a name="i-dont-see-microsoft-365-defender-content"></a>Je ne vois pas le contenu De Microsoft 365 Defender

Si vous ne voyez pas de fonctionnalités dans le volet de navigation, telles que les incidents, le centre de action ou le hunting dans votre portail, vous devez vérifier que votre client dispose des licences appropriées.

Si vous souhaitez en savoir plus, consultez la page[Conditions préalables](prerequisites.md).

## <a name="microsoft-defender-for-identity-alerts-are-not-showing-up-in-the-microsoft-365-defender-incidents"></a>Les alertes Microsoft Defender pour l’identité ne s’affichent pas dans les incidents Microsoft 365 Defender

Si Vous avez déployé Microsoft Defender pour l’identité dans votre environnement, mais que vous ne voyez pas les alertes Defender pour l’identité dans le cadre des incidents microsoft 365 Defender, vous devez vous assurer que l’intégration de Microsoft Cloud App Security et Defender for Identity est activée.

Pour plus d’informations, [voir Microsoft Defender pour l’intégration de l’identité.](/cloud-app-security/mdi-integration)

## <a name="where-is-the-settings-page-for-turning-on-the-service"></a>Où se trouve la page de paramètres pour l’ment du service ?

Pour activer Microsoft 365 Defender, accédez aux **Paramètres** à partir du volet de navigation du Centre de sécurité Microsoft 365. Cet élément de navigation n’est visible que si vous avez les [autorisations et licences requises.](m365d-enable.md#check-license-eligibility-and-required-permissions)

## <a name="how-do-i-create-an-exception-for-my-fileurl"></a>Comment créer une exception pour mon fichier/URL ?

Un faux positif est un fichier ou une URL détecté comme malveillant, mais qui n’est pas une menace. Vous pouvez créer des indicateurs et définir des exclusions pour débloquer et autoriser certains fichiers/URL. Voir [Adresse faux positifs/négatifs dans Defender pour le point de terminaison.](/microsoft-365/security/defender-endpoint/defender-endpoint-false-positives-negatives)

