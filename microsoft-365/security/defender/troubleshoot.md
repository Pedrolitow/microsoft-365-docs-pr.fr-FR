---
title: Résoudre les problèmes liés au service Microsoft 365 Defender
description: Trouver des solutions et des solutions de contournement aux problèmes connus de Microsoft 365 Defender
keywords: résoudre les problèmes Microsoft 365 Defender, résoudre les problèmes, Microsoft Defender pour Identity, problèmes, module complémentaire, page paramètres
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- tier3
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 1909756f77f48d96dc997726019f4d2eb518d22e
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68069510"
---
# <a name="troubleshoot-microsoft-365-defender-service-issues"></a>Résoudre les problèmes liés au service Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Cette section traite des problèmes qui peuvent survenir lorsque vous utilisez le service Microsoft 365 Defender.

## <a name="i-dont-see-microsoft-365-defender-content"></a>Je ne vois pas Microsoft 365 Defender contenu

Si vous ne voyez pas de fonctionnalités dans le volet de navigation, telles que les incidents, le centre d’actions ou la chasse dans votre portail, vous devez vérifier que votre locataire dispose des licences appropriées.

Si vous souhaitez en savoir plus, consultez la page[Conditions préalables](prerequisites.md).

## <a name="microsoft-defender-for-identity-alerts-are-not-showing-up-in-the-microsoft-365-defender-incidents"></a>Microsoft Defender pour Identity alertes ne s’affichent pas dans les incidents Microsoft 365 Defender

Si vous avez Microsoft Defender pour Identity déployé dans votre environnement, mais que vous ne voyez pas d’alertes Defender pour Identity dans le cadre d’incidents Microsoft 365 Defender, vous devez vous assurer que le Microsoft Defender for Cloud Apps  et l’intégration de Defender pour Identity est activée.

Pour plus d’informations, consultez [Microsoft Defender pour Identity intégration](/cloud-app-security/mdi-integration).

## <a name="where-is-the-settings-page-for-turning-on-the-service"></a>Où se trouve la page des paramètres pour l’activation du service ?

Pour activer Microsoft 365 Defender, **accédez aux paramètres** à partir du volet de navigation du portail Microsoft 365 Defender. Cet élément de navigation est visible uniquement si vous [disposez des autorisations et des licences requises](m365d-enable.md#check-license-eligibility-and-required-permissions).

## <a name="how-do-i-create-an-exception-for-my-fileurl"></a>Comment faire créer une exception pour mon fichier/URL ?

Un faux positif est un fichier ou une URL qui est détecté comme malveillant, mais qui n’est pas une menace. Vous pouvez créer des indicateurs et définir des exclusions pour débloquer et autoriser certains fichiers/URL. Voir [Adresse des faux positifs/négatifs dans Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/defender-endpoint-false-positives-negatives).
