---
title: Résoudre les erreurs des appareils AutoPilot
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: troubleshooting
f1_keywords:
- ZTDTroubleshootDeviceErrors
- O365E_ZTDTroubleshootDeviceErrors
- BCS365_ZTDTroubleshootDeviceErrors
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 1f468690-530c-47ea-918f-fede24607c53
description: Découvrez comment résoudre les erreurs de fichier de périphérique en pilote automatique.
ms.openlocfilehash: 9b8d8ab424dd3189ff5c228dab8f5c513ff5dafc
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867019"
---
# <a name="troubleshoot-autopilot-device-errors"></a>Résoudre les erreurs des appareils AutoPilot

## <a name="device-file-error-messages"></a>Messages d’erreur de fichier de périphérique

Info Voici certaines des erreurs que vous pouvez rencontrer lorsque vous travaillez avec des fichiers de périphérique en pilote automatique dans Microsoft 365 Business. 
  
|**Code d’erreur**|**Solution pour l’essayer**|
|:-----|:-----|
|Corps de la demande non valide  <br/> |Cette erreur doit se produire rarement, si vous voyez cette erreur, réessayez l’opération.  <br/> |
|Valeur de hachage du matériel pour un périphérique n’est pas correct.  <br/> |Si vous voyez cette erreur, cela signifie que la valeur fournie dans votre fichier CSV pour le hachage du matériel d’un périphérique n’est pas correcte. Tout d’abord, vérifiez que la valeur a été correctement tapée. Si vous pensez que la valeur est correcte, mais cette erreur qui se passe, demandez à votre fournisseur de matériel pour une assistance.  <br/> |
|Périphérique affecté à un autre client  <br/> |Si vous voyez cette erreur, cela signifie que la valeur fournie pour le numéro de série ou la clé de produit d’un ou plusieurs périphériques dans votre fichier CSV n’est pas correcte. Tout d’abord, vérifiez que la valeur a été correctement tapée. Si vous pensez que la valeur est correcte, mais cette erreur qui se passe, demandez à votre fournisseur de matériel pour une assistance.  <br/> |
|Le fichier CSV contient un numéro de série ou de la clé de produit  <br/> |Si vous rencontrez cette erreur, cela signifie que le périphérique que vous êtes lors de la tentative d’enregistrer est déjà enregistré par une autre organisation. Pour résoudre ce problème, demandez à votre fournisseur de matériel pour une assistance.  <br/> |
|Ce périphérique n’est pas pris en charge pour le programme d’installation à l’aide de pilote  <br/> | Cette erreur signifie que le périphérique ne répond pas aux besoins de déploiement pilote automatique. Périphériques doivent répondre aux exigences suivantes :  <br/>  Windows 10, version 1703 ou supérieure.  <br/>  Nouveaux appareils qui ne sont pas issus d'une expérience Windows prête à l'emploi.  <br/> |
|Périphérique non trouvé  <br/> |Cette erreur signifie qu’un ou plusieurs périphériques dans votre fichier CSV n’est pas inscrit à votre organisation. Pour résoudre ce problème, demandez à votre fournisseur de matériel pour une assistance.  <br/> |
   
