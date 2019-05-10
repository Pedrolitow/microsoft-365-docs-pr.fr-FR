---
title: Gérer les accès des utilisateurs aux documents Office sur appareils mobiles
ms.author: sirkkuw
author: sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: conceptual
f1_keywords:
- O365E_BCSSetup4OfficeMobile
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: aa31319c-9196-48c9-a90b-4057e0494c7a
description: Découvrez les stratégies de protection qui peuvent aider à sécuriser l’accès aux applications Office à partir d’appareils mobiles.
ms.openlocfilehash: b49ec33f4899a25f92ffd9d7a25d3e435016749e
ms.sourcegitcommit: db1dfb2df2c2f7beced3b57bc772d106c189e88a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "33660325"
---
# <a name="manage-how-users-access-office-documents-on-mobile-devices"></a>Gérer les accès des utilisateurs aux documents Office sur appareils mobiles

 [] Les paramètres de stratégie qui contrôlent la manière dont les utilisateurs accèdent aux fichiers Office à partir de leur appareil mobile sont **désactivés** par défaut. Nous vous recommandons d'accepter les valeurs par défaut lors de l'installation pour créer des stratégies d'application pour Windows 10, iOS et Android qui s'appliquent à tous les utilisateurs. Vous pouvez créer des stratégies supplémentaires une fois l'installation terminée. 
  
## <a name="settings-that-control-how-users-access-office-files-on-mobile-devices"></a>Paramètres qui contrôlent la façon dont les utilisateurs accèdent aux fichiers Office sur appareils mobiles

Les paramètres suivants sont disponibles pour gérer la manière dont les utilisateurs accèdent aux fichiers professionnels Office :
  
|||
|:-----|:-----|
|Setting  <br/> |Description  <br/> |
|Exiger un code confidentiel ou une empreinte pour accéder aux applications Office  <br/> |Si ce paramètre est **activé**, les utilisateurs doivent fournir une autre forme d'authentification, en plus de leur nom d'utilisateur et de leur mot de passe, pour pouvoir utiliser les applications Office sur leur appareil mobile.  <br/> |
|Réinitialiser le code confidentiel en cas d'échecs successifs de la connexion  <br/> |Afin d'empêcher un utilisateur non autorisé de deviner un code confidentiel de façon aléatoire, le code confidentiel est réinitialisé après le nombre d'entrées incorrectes que vous spécifiez.  <br/> |
|Demander aux utilisateurs de se reconnecter à l'issue d'une période d'inactivité des applications Office  <br/> |Ce paramètre détermine combien de temps un utilisateur peut être inactif avant d'être invité à se connecter à nouveau.  <br/> |
|Refuser l'accès aux fichiers de travail sur les appareils « jailbreakés » ou débridés  <br/> |Les utilisateurs intelligents peuvent avoir un appareil jailbreaké ou rooté. Cela signifie que l'utilisateur est en mesure de modifier le système d'exploitation, ce qui peut rendre l'appareil plus vulnérable aux logiciels malveillants. Ces appareils sont bloqués lorsque ce paramètre est **activé**.  <br/> |
|Ne pas autoriser les utilisateurs à copier le contenu des applications Office dans des applications personnelles  <br/> |Lorsque le paramètre est **activé**, l’utilisateur ne peut pas copier les informations d’un fichier de travail dans un fichier personnel. Si le paramètre est **désactivé**, l’utilisateur peut copier des informations à partir d’un fichier de travail vers une application personnelle ou un compte personnel.  <br/> |
   

