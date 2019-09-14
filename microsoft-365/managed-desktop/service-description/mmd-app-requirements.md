---
title: Configuration requise pour les applications de bureau géré Microsoft
description: ''
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 5e0ca142e2ef84f198ee154c5b7c7f4f6621c37c
ms.sourcegitcommit: 91ff1d4339f0f043c2b43997d87d84677c79e279
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "36982455"
---
# <a name="microsoft-managed-desktop-app-requirements"></a>Configuration requise pour les applications de bureau géré Microsoft

<!--This topic is the target for aka.ms/app-req. This is aka link is used from EA agreeement for MMD. do not delete.-->

<!--Application addendum -->
 
Afin de garantir les performances, la fiabilité et la maintenance des périphériques de bureau géré Microsoft, les applications métier d’un client ne doivent pas sérieusement influer sur l’expérience de l’utilisateur final ou modifier l’attitude de la sécurité. Par conséquent, les applications métier que vous souhaitez déployer sur des appareils de bureau gérés Microsoft doivent répondre aux exigences de cette rubrique.

## <a name="application-condition"></a>Condition de l’application

Il est important que les applications n’aient pas d’impact négatif sur l’environnement de bureau géré Microsoft. Voici les conditions requises qu’une application doit respecter pour qu’une application soit déployée. Pour une application ou un pilote donné, Microsoft peut renoncer aux exigences fournies dans le présent document. Microsoft peut décider de supprimer une application ou un pilote qui a un impact négatif sur les performances et la fiabilité des appareils de bureau gérés par Microsoft.

## <a name="centrally-managed-apps"></a>Applications gérées de manière centralisée

Toutes les applications et tous les pilotes installés sur les appareils gérés par Microsoft doivent être déployés via Microsoft Intune, le Microsoft Store ou Microsoft Store pour les entreprises ; s’ils sont disponibles, les pilotes seront également déployés via le service Windows Update. 

## <a name="prohibited-app-classes"></a>Classes d’application interdites

Certains types d’application ne sont pas autorisés sur les appareils de bureau géré Microsoft :
- logiciels antivirus, de sécurité ou d’audit tiers
- Versions de Microsoft Office antérieures à Office 365 ProPlus
- Applications qui installent ou regroupent d’autres logiciels tiers

## <a name="restricted-app-behaviors"></a>Comportements d’application restreinte

Certains comportements d’application peuvent avoir un impact négatif sur l’expérience utilisateur ou présenter un risque de sécurité aux appareils de bureau gérés par Microsoft. Les applications présentant les comportements suivants ne sont pas autorisées à s’exécuter dans l’environnement de bureau géré Microsoft sans dérogation particulière de Microsoft.

Expérience utilisateur :
- Installer les services d’arrière-plan
- S’ajouter au chemin de démarrage de Windows
- Applications dépendant des pilotes
- navigateurs Web tiers

Sécurité :
- Élever les privilèges de l’utilisateur final
- Agir en tant que magasin d’applications ou disposer d’un gestionnaire d’extensions intégré
- Ont des failles de sécurité connues
- Chiffrer ou restreindre l’accès aux données de l’utilisateur final
- Non signé ou signé à l’aide d’un certificat qui ne se cumule pas vers une racine approuvée


## <a name="driver-deployment"></a>Déploiement de pilotes

Microsoft Managed Desktop prend en charge uniquement les pilotes de périphériques disponibles via Windows Update ou la boîte de réception installée avec l’appareil géré Microsoft. 

Si une application requiert un ou plusieurs pilotes pour l’exécuter, elle est considérée comme une application restreinte et nécessite le déploiement de l’exemption sur le bureau géré Microsoft. 

