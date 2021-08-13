---
title: Résoudre les erreurs des appareils AutoPilot
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
f1_keywords:
- ZTDTroubleshootDeviceErrors
- O365E_ZTDTroubleshootDeviceErrors
- BCS365_ZTDTroubleshootDeviceErrors
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 1f468690-530c-47ea-918f-fede24607c53
description: Découvrez comment résoudre les erreurs que vous pouvez voir lorsque vous travaillez avec des fichiers d’appareil AutoPilot dans Microsoft 365 Business Premium.
ms.openlocfilehash: b74c57acbaa5682f6db97e7d8a090e6e28a40dcc3246f00cacc7984cb52cc758
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53809177"
---
# <a name="troubleshoot-autopilot-device-errors"></a>Résoudre les erreurs des appareils AutoPilot

## <a name="device-file-error-messages"></a>Messages d’erreur de fichier d’appareil

Voici des informations sur certaines des erreurs que vous pouvez voir lors de l’utilisation de fichiers d’appareil AutoPilot dans Microsoft 365 Business Premium. 
  
|**Code d’erreur**|**Corriger pour essayer**|
|:-----|:-----|
|Corps de la demande non valide  <br/> |Cette erreur devrait se produire rarement, si vous voyez cette erreur, tentez à nouveau l’opération.  <br/> |
|La valeur de hachage matériel d’un appareil n’est pas correcte.  <br/> |Si vous voyez cette erreur, cela signifie que la valeur que vous avez fournie dans votre fichier CSV pour le hachage matériel d’un appareil n’est pas correcte. Tout d’abord, vérifiez que la valeur a été tapée correctement. Si vous pensez que la valeur est correcte, mais que cette erreur se produit toujours, demandez de l’aide à votre fournisseur de matériel.  <br/> |
|Appareil affecté à un autre client  <br/> |Si vous voyez cette erreur, cela signifie que la valeur que vous avez fournie dans votre fichier CSV pour le numéro de série ou la clé de produit d’un ou plusieurs appareils n’est pas correcte. Tout d’abord, vérifiez que la valeur a été tapée correctement. Si vous pensez que la valeur est correcte, mais que cette erreur se produit toujours, demandez de l’aide à votre fournisseur de matériel.  <br/> |
|Le fichier CSV contient un numéro de série ou une clé de produit non valide  <br/> |Si vous voyez cette erreur, cela signifie que l’appareil que vous essayez d’inscrire est déjà inscrit par une autre organisation. Pour corriger cette erreur, demandez de l’aide à votre fournisseur de matériel.  <br/> |
|Cet appareil n’est pas pris en charge pour l’installation à l’aide d’AutoPilot  <br/> | Cette erreur signifie que l’appareil ne répond pas aux exigences de déploiement AutoPilot. Les appareils doivent respecter ces exigences :  <br/>  Windows 10, version 1703 ou supérieure.  <br/>  Les nouveaux appareils qui n’ont pas fait l’Windows l’expérience out-of-box.  <br/> |
|Appareil in trouvé  <br/> |Cette erreur signifie qu’un ou plusieurs appareils de votre fichier CSV ne sont pas enregistrés dans votre organisation. Pour résoudre ce problème, demandez de l’aide à votre fournisseur de matériel.  <br/> |
