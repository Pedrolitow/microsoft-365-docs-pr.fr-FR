---
title: Résoudre les erreurs des appareils AutoPilot
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 1f468690-530c-47ea-918f-fede24607c53
description: Découvrez comment résoudre les erreurs que vous pouvez voir lors de l’utilisation de fichiers d’appareil AutoPilot dans Microsoft 365 Business Premium.
ms.openlocfilehash: 0c0742e5bf17c85cedfb421cabfd87c0e2184ba5
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43635041"
---
# <a name="troubleshoot-autopilot-device-errors"></a>Résoudre les erreurs des appareils AutoPilot

## <a name="device-file-error-messages"></a>Messages d’erreur de fichier d’appareil

Voici des informations sur certaines des erreurs que vous pouvez voir lors de l’utilisation de fichiers d’appareil AutoPilot dans Microsoft 365 Business Premium. 
  
|**Code d’erreur**|**Correctif à essayer**|
|:-----|:-----|
|Corps de la requête non valide  <br/> |Cette erreur devrait se produire rarement, si vous voyez cette erreur, renouvelez l’opération.  <br/> |
|La valeur de hachage de matériel pour un périphérique est incorrecte.  <br/> |Si cette erreur apparaît, cela signifie que la valeur que vous avez fournie dans votre fichier CSV pour le hachage matériel d’un périphérique est incorrecte. Tout d’abord, vérifiez que la valeur a été tapée correctement. Si vous pensez que la valeur est correcte, mais que cette erreur persiste, demandez de l’aide à votre fournisseur de matériel.  <br/> |
|Appareil affecté à un autre client  <br/> |Si cette erreur apparaît, cela signifie que la valeur que vous avez fournie dans votre fichier CSV pour le numéro de série ou la clé de produit d’un ou plusieurs périphériques est incorrecte. Tout d’abord, vérifiez que la valeur a été tapée correctement. Si vous pensez que la valeur est correcte, mais que cette erreur persiste, demandez de l’aide à votre fournisseur de matériel.  <br/> |
|Le fichier CSV contient un numéro de série ou une clé de produit non valide  <br/> |Si cette erreur apparaît, cela signifie que l’appareil que vous essayez d’enregistrer est déjà enregistré par une autre organisation. Pour corriger cette erreur, demandez de l’aide à votre fournisseur de matériel.  <br/> |
|Ce périphérique n’est pas pris en charge pour l’installation à l’aide de AutoPilot  <br/> | Cette erreur signifie que l’appareil ne répond pas à la configuration requise pour le déploiement de AutoPilot. Les appareils doivent respecter ces exigences :  <br/>  Windows 10, version 1703 ou supérieure.  <br/>  Nouveaux appareils qui n’ont pas été via Windows out-of-Box.  <br/> |
|Appareil introuvable  <br/> |Cette erreur signifie qu’un ou plusieurs périphériques de votre fichier CSV ne sont pas enregistrés dans votre organisation. Pour résoudre ce problème, demandez de l’aide à votre fournisseur de matériel.  <br/> |
