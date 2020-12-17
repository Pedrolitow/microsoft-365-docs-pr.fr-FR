---
title: Gérer les stratégies d’appareil Windows 10 professionnel avec Microsoft 365 Business Premium
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
description: Découvrez comment gérer les stratégies d’appareils Windows 10 professionnel avec Microsoft 365 Business Premium.
ms.openlocfilehash: 9052859f03035a76bf69b7c8c23c75ae00353846
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49702384"
---
# <a name="manage-windows-10-pro-device-policies"></a>Gérer les stratégies d’appareil Windows 10 professionnel

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FYSL?autoplay=false]

Vous pouvez utiliser Microsoft 365 entreprise pour vous assurer que l’antivirus Windows Defender est activé sur les appareils Windows 10 et que les mises à jour Microsoft sont automatiquement téléchargées sur les appareils des utilisateurs.

## <a name="try-it"></a>Essayez !

1. Connectez-vous au Centre d’administration Microsoft 365.
1. Sous **stratégies**, choisissez Ajouter une stratégie.
1. Dans le **volet ajouter une stratégie** , entrez un nom sous nom de la **stratégie**, puis sélectionnez Configuration de l' **appareil Windows 10** sous **type de stratégie**.
1. Choisissez **sécuriser les appareils Windows 10** pour afficher les sous-paramètres.
1. Assurez-vous que la **protection des PC contre les virus et les autres menaces à l’aide de l’antivirus Windows Defender** et que **les appareils Windows 10 à jour** sont activés automatiquement.
1. Sous **qui va obtenir ces paramètres ?**, tous les utilisateurs sont sélectionnés par défaut, mais vous pouvez choisir **modifier** pour sélectionner les groupes de sécurité que vous avez créés.
1. Pour terminer la création de la stratégie, sélectionnez **Ajouter**.
1. Sur la page **Ajouter une stratégie** , cliquez sur **Fermer**.
1. Sur la page d’accueil du centre d’administration, vérifiez que votre nouvelle stratégie a été ajoutée en sélectionnant **stratégies** et en examinant votre stratégie sur la page **stratégies** .
1. Pour vérifier que la stratégie a pris effet, sur le périphérique Windows 10 d’un utilisateur, accédez à Windows Update, choisissez **Options avancées**, puis vérifiez que les paramètres sont grisés.

    Ensuite, cliquez sur **choisir comment les mises à jour sont livrées** et vérifiez que les paramètres sont grisés et que le message suivant s’affiche : **certains paramètres sont masqués ou gérés par votre organisation**.

