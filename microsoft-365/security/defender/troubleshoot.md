---
title: Résoudre les Microsoft 365 de service Defender
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
ms.openlocfilehash: 81da6c6ef46798ac656e7d5f0f374bf2c722583d
ms.sourcegitcommit: 3b9fab82d63aea41d5f544938868c5d2cbf52d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2021
ms.locfileid: "52782740"
---
# <a name="troubleshoot-microsoft-365-defender-service-issues"></a>Résoudre les Microsoft 365 de service Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Cette section traite des problèmes qui peuvent survenir lorsque vous utilisez le service Microsoft 365 Defender.

## <a name="i-dont-see-microsoft-365-defender-content"></a>Je ne vois pas le Microsoft 365 Defender

Si vous ne voyez pas de fonctionnalités dans le volet de navigation, telles que les incidents, le centre de gestion des actions ou le hunting dans votre portail, vous devez vérifier que votre client dispose des licences appropriées.

Si vous souhaitez en savoir plus, consultez la page[Conditions préalables](prerequisites.md).

## <a name="microsoft-defender-for-identity-alerts-are-not-showing-up-in-the-microsoft-365-defender-incidents"></a>Les alertes Microsoft Defender pour l’identité ne s’affichent pas dans les incidents Microsoft 365 Defender

Si Vous avez déployé Microsoft Defender pour l’identité dans votre environnement, mais que vous ne voyez pas les alertes Defender pour l’identité dans le cadre des incidents Microsoft 365 Defender, vous devez vous assurer que l’intégration de Microsoft Cloud App Security et defender pour l’identité est activée.

Pour plus d’informations, [voir Microsoft Defender pour l’intégration de l’identité.](/cloud-app-security/mdi-integration)

## <a name="where-is-the-settings-page-for-turning-on-the-service"></a>Où se trouve la page des paramètres pour l’ment du service ?

Pour activer Microsoft 365 Defender, accédez **Paramètres** à partir du volet de navigation dans le centre Microsoft 365 de sécurité. Cet élément de navigation n’est visible que si vous avez les autorisations et [licences requises.](m365d-enable.md#check-license-eligibility-and-required-permissions)

## <a name="how-do-i-create-an-exception-for-my-fileurl"></a>Comment créer une exception pour mon fichier/URL ?

Un faux positif est un fichier ou une URL détecté comme malveillant, mais qui n’est pas une menace. Vous pouvez créer des indicateurs et définir des exclusions pour débloquer et autoriser certains fichiers/URL. Voir [Adresse faux positifs/négatifs dans Defender pour le point de terminaison.](/microsoft-365/security/defender-endpoint/defender-endpoint-false-positives-negatives)


