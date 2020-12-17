---
title: Sécuriser les applications Office sur iOS
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment sécuriser les applications Office sur iOS avec Microsoft 365 Business Premium.
ms.openlocfilehash: 1703faa7cd7731f0779bacc3d2fa3ad3e4556910
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49702058"
---
# <a name="secure-office-apps-on-ios"></a>Sécuriser les applications Office sur iOS

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FLvZ?autoplay=false]

Vous pouvez configurer une stratégie d’accès utilisateur qui exige que les utilisateurs mobiles entrent un code confidentiel ou une empreinte digitale pour se connecter, et chiffre également les fichiers de travail stockés sur leurs appareils.

## <a name="try-it"></a>Essayez !

1. Connectez-vous au Centre d’administration Microsoft 365.
1. Sous **stratégies**, choisissez **Ajouter une stratégie**.
1. Dans le volet **Ajouter une stratégie** , entrez un nom sous nom de la **stratégie**, puis choisissez le type de stratégie souhaité sous type de **stratégie**.
1. Activer la **gestion de la façon dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles**, puis assurez-vous que les trois paramètres suivants sont activés :
    - **Exiger un code confidentiel ou une empreinte pour accéder aux applications Office**
    - **Protéger les fichiers de travail en cas de perte ou de vol des appareils**
    - **Chiffrer les fichiers de travail**

1. Sous **les fichiers de ces applications seront protégés**, sélectionnez les applications Office que vous souhaitez protéger sur les appareils mobiles.
1. Sous **qui va obtenir ces paramètres ?**, tous les utilisateurs sont sélectionnés par défaut, mais vous pouvez choisir **modifier** pour sélectionner les groupes de sécurité que vous avez créés.
1. Pour terminer la création de la stratégie, sélectionnez **Ajouter**.
1. Sur la page **Ajouter une stratégie** , cliquez sur **Fermer**.
1. Sur la page d’accueil du centre d’administration, vérifiez que votre nouvelle stratégie a été ajoutée en sélectionnant **stratégies** et en examinant votre stratégie sur la page **stratégies** .