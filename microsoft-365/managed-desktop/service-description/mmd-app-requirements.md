---
title: Configuration requise de bureau Microsoft
description: ''
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: 71952a8b073f002890cc95883e717aeb04c0cd68
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866823"
---
# <a name="microsoft-managed-desktop-app-requirements"></a>Configuration requise de bureau Microsoft

<!--This topic is the target for aka.ms/app-req. This is aka link is used from EA agreeement for MMD. do not delete.-->

<!--Application addendum -->
 
Line-of-business applications que vous souhaitez déployer sur les périphériques de bureau Microsoft doivent respecter les spécifications indiquées dans cette rubrique. 

## <a name="application-condition"></a>Condition d’application

Il est important que les applications ne pas avoir un impact sur l’environnement de bureau Microsoft. Voici la configuration requise qu’une application dans l’ordre pour déployer Microsoft. Pour une application donnée ou le pilote, Microsoft renoncer à toutes les exigences fournies dans le présent document. Microsoft peut décider de supprimer une application ou un pilote qui affecte les performances et la fiabilité des périphériques de bureau Microsoft.

## <a name="deployable-using-microsoft-technologies"></a>Peut être déployé à l’aide des technologies Microsoft

Ordinateur de bureau Microsoft utilise Intune, Microsoft Store et Microsoft Store for Business pour déployer des applications. Par conséquent, les applications doivent être empaquetées sous forme peuvent être déployés par la version en cours de ces services.

## <a name="prohibited-app-classes"></a>Classes d’application interdite

Certains types d’applications ne sont pas autorisés sur les périphériques de bureau Microsoft :
- logiciel d’audit, de sécurité ou antivirus 3ème partie
- Versions de Microsoft Office avant d’Office 365 Pro Plus
- Applications qui installent ou regroupent les autres logiciels tiers 3

## <a name="restricted-app-behaviors"></a>Comportements d’application restreinte

Certains comportements d’application peuvent être être préjudiciable que l’expérience utilisateur ou représenter un risque de sécurité pour les périphériques de bureau Microsoft. Les applications ne doivent pas comporter les comportements ou les caractéristiques suivantes : 
- Installer les services d’arrière-plan ou de lancer le processus de longue durée en arrière-plan
- Ajouter le chemin d’accès de démarrage de Windows
- Appeler proposait Windows ou API Office ou prendre de dépendances sur les structures de données internes Windows ou Office
- Agir comme un magasin d’applications ou gestionnaire d’extension intégrés
- Élever les privilèges de l’utilisateur final
- Failles de sécurité connus
- Signé à l’aide d’un certificat qui ne reportés sur une racine de confiance
- Chiffrer ou restreindre l’accès aux données de l’utilisateur final
- Modifier le code du système d’exploitation en cours d’exécution

## <a name="driver-deployment"></a>Déploiement pilote

Sauf si un pilote est disponible dans Windows Update ou est signé séparément par Windows matériel qualité (WHQL), Microsoft doit approuver un pilote avant que Microsoft déploierez le pilote aux périphériques de bureau Microsoft.