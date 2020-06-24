---
title: Détecter les problèmes liés au service de Protection Microsoft contre les menaces
description: Trouver des solutions et contourner les problèmes connus de la Protection Microsoft contre les menaces
keywords: résolution des problèmes liés à la protection contre les menaces Microsoft, résolution des problèmes, Azure ATP, problèmes, module complémentaire, page Paramètres
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
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
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: e19e5758f4d42799c96ecec51fd6295e3da19f9b
ms.sourcegitcommit: bd5a08785b5ec320b04b02f8776e28bce5fb448f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "44844917"
---
# <a name="troubleshoot-microsoft-threat-protection-service-issues"></a>Détecter les problèmes liés au service de Protection Microsoft contre les menaces

**S’applique à :**
- Protection Microsoft contre les menaces

Cette section traite des problèmes qui peuvent survenir lorsque vous utilisez le service Protection Microsoft contre les menaces.


## <a name="i-dont-see-microsoft-threat-protection-content"></a>Je ne vois pas le contenu de la protection contre les menaces Microsoft
Si vous ne voyez pas les fonctionnalités dans le volet de navigation, telles que les incidents, le centre de maintenance ou la chasse dans votre portail, vous devez vérifier que votre client dispose des licences appropriées. 

Si vous souhaitez en savoir plus, consultez[conditions préalables](prerequisites.md).

## <a name="azure-atp-alerts-are-not-showing-up-in-the-microsoft-threat-protection-incidents"></a>Les alertes Azure ATP n’apparaissent pas dans les incidents de la Protection Microsoft contre les menaces
Si Azure ATP est déployé dans votre environnement, mais que vous ne voyez pas d’alertes Azure ATP dans le cadre des incidents de Protection Microsoft contre les menaces, vous devez vous assurer que les applications Microsoft Cloud App Security et Azure ATP sont activées. 

Pour plus d’informations, consultez [Intégration Azure ATP](https://docs.microsoft.com/cloud-app-security/aatp-integration).

## <a name="where-is-the-settings-page-for-turning-the-service-on"></a>Où se trouve la page Paramètres pour activer le service ?
Pour activer Microsoft Threat Protection, accédez aux **paramètres** à partir du volet de navigation dans le centre de sécurité Microsoft 365. Cet élément de navigation n’est visible que si vous disposez des [autorisations et des licences prérequises](mtp-enable.md#check-license-eligibility-and-required-permissions).
 

