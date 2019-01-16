---
title: À propos des paramètres du profil AutoPilot
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: overview
f1_keywords:
- ZTDProfileSettings
- O365E_ZTDProfileSettings
- BCS365_ZTDProfileSettings
ms.service: o365-administration
localization_priority: Normal
ms.collection: Adm_O365
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 99bfbf81-e719-4630-9b0f-c187edfa1f8a
description: Profils de pilote vous aider à contrôler la façon dont Windows est installé sur les périphériques de l’utilisateur. Les profils contiennent par défaut et les paramètres facultatifs comme ignorer l’installation du Cortana.
ms.openlocfilehash: 5440286f1363780c87ab60514584c4addfeea0b2
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26866865"
---
# <a name="about-autopilot-profile-settings"></a>À propos des paramètres du profil AutoPilot

## <a name="autopilot-profile-settings"></a>Paramètres de profil pilote

Vous pouvez contrôler la façon dont Windows est installé sur les périphériques de l’utilisateur en utilisant les profils de pilote. Les profils contiennent les paramètres suivants.
  
 **Pilote fonctionnalités par défaut (requis) qui sont définies automatiquement :**
  
|**Paramètre**|**Description**|
|:-----|:-----|
|Ignorer l’enregistrement OEM, OneDrive et Cortana  <br/> |Ignore l’installation des applications consommateur, telles que Cortana et OneDrive personnel. L’utilisateur de l’appareil peut installer ultérieurement tant qu’il est un administrateur local sur l’appareil. L’inscription du fabricant d’origine est ignorée car le périphérique sera géré par Microsoft 365 Business.  <br/> |
|Connecter l’expérience avec la marque de votre société  <br/> |Si votre société possède une [personnalisation d’ajouter votre société pour Office 365 page de connexion](https://support.office.com/article/a1229cdb-ce19-4da5-90c7-2b9b146aef0a), l’utilisateur d’appareil obtenez cette expérience lors de la connexion.  <br/> |
|Mobile Device Manager l’inscription automatique avec des comptes DAS configurés.  <br/> |Identité de l’utilisateur est gérée par Azure Active directory et les utilisateurs seront vous connecter à Windows et Office 365 avec leurs informations d’identification Microsoft 365 Business.  <br/> |
   
 **Paramètres facultatifs :**
  
|**Paramètre**|**Description**|
|:-----|:-----|
|Ignorer les paramètres de confidentialité (désactivé par défaut)  <br/> |Si cette option est définie sur **activé**, l’utilisateur d’appareil verrez pas le contrat de licence pour le périphérique et Windows lorsqu’il se connecte tout d’abord en.  <br/> |
|Ne pas autoriser l’utilisateur de devenir l’administrateur local  <br/> |Si cette option est définie sur **activé**, l’utilisateur du périphérique ne sera pas en mesure d’installer des applications personnelles, telles que Cortana.  <br/> |
   
