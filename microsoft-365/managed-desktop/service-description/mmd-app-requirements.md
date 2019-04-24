---
title: Configuration requise pour les applications de bureau géré Microsoft
description: ''
keywords: Microsoft maNaged Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 01/08/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: de6cc7d77e023a9d41961e5fbcce060f1bb659ae
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32278334"
---
# <a name="microsoft-managed-desktop-app-requirements"></a>Configuration requise pour les applications de bureau géré Microsoft

<!--This topic is the target for aka.ms/app-req. This is aka link is used from EA agreeement for MMD. do not delete.-->

<!--Application addendum -->
 
Les applications métier que vous souhaitez déployer sur des appareils de bureau gérés Microsoft doivent répondre aux exigences de cette rubrique. 

## <a name="application-condition"></a>Condition de l'application

Il est important que les applications n'aient pas d'impact négatif sur l'environnement de bureau géré Microsoft. Les conditions suivantes doivent être satisfaites pour que Microsoft puisse le déployer. Pour une application ou un pilote donné, Microsoft peut renoncer aux exigences fournies dans le présent document. Microsoft peut décider de supprimer une application ou un pilote qui a un impact négatif sur les performances et la fiabilité des appareils de bureau gérés par Microsoft.

## <a name="deployable-using-microsoft-technologies"></a>Déployable à l'aide des technologies Microsoft

Microsoft maNaged Desktop utilise Intune, Microsoft Store et Microsoft Store pour les entreprises pour déployer des applications. Par conséquent, les applications doivent être empaquetées de manière à pouvoir être déployées par la version actuelle de ces services.

## <a name="prohibited-app-classes"></a>Classes d'application interDites

Certains types d'application ne sont pas autorisés sur les appareils de bureau géré Microsoft:
- logiciels antivirus, de sécurité ou d'audit tiers
- navigateurs Web tiers
- Versions de Microsoft Office antérieures à Office 365 Pro plus
- Applications qui installent ou regroupent d'autres logiciels tiers

## <a name="restricted-app-behaviors"></a>Comportements d'application restreinte

Certains comportements d'application peuvent être préjudiciables à l'expérience utilisateur ou présenter un risque de sécurité aux appareils de bureau gérés par Microsoft. Les applications ne doivent pas présenter les comportements ou caractéristiques suivants: 

Expérience utilisateur:
- Installer des services d'arrière-plan ou générer des processus d'arrière-plan de longue durée d'exécution
- S'ajouter au chemin de démarrage de Windows

Sécurité :
- Appeler des API Windows ou Office ou prendre des dépendances sur des structures de données Windows ou Office internes
- Agir en tant que magasin d'applications ou disposer d'un gestionnaire d'extensions intégré
- Élever les privilèges de l'utilisateur final
- Ont des failles de sécurité connues
- Signé à l'aide d'un certificat qui ne se cumule pas vers une racine approuvée
- Chiffrer ou restreindre l'accès aux données de l'utilisateur final
- Modifier le code du système d'exploitation au moment de l'exécution

## <a name="driver-deployment"></a>Déploiement de pilotes

À moins qu'un pilote ne soit disponible dans Windows Update ou qu'il soit signé séparément par le laboratoire de la qualité du matériel Windows (WHQL), Microsoft doit approuver un pilote pour que Microsoft déploie le pilote sur les appareils de bureau gérés par Microsoft.
