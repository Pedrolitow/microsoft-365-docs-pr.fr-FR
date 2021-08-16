---
title: Configurer la protection anti-hameçonnage
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
description: Découvrez comment configurer la protection anti-hameçonnage.
ms.openlocfilehash: 71acaf070ea121db93947423e9824ae93d90b53c3ccbd3cc47e57df23a92a40f
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53887514"
---
# <a name="set-up-anti-phishing"></a>Configurer les stratégies d’anti-hameçonnage et d’anti-hameçonnage

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvt9r?autoplay=false]

Le hameçonnage est une attaque malveillante dans laquelle un e-mail semble avoir été envoyé à partir d’une source familière, mais il tente de collecter vos informations personnelles. Par défaut, Microsoft 365 inclut une certaine protection anti-hameçonnage, mais vous pouvez augmenter cette protection en affinant les paramètres. Examinons ce qui se fait.

## <a name="try-it"></a>Essayez !

1. Dans le centre d’administration, [https://admin.microsoft.com](https://admin.microsoft.com) sélectionnez **Sécurité,** **Gestion** des **menaces, Stratégie,** puis **Anti-hameçonnage ATP**.
1. Sélectionnez **Stratégie par défaut** pour l’affiner.
1. Dans la section **Emprunt d’identité,** sélectionnez **Modifier.**
1. Go to **Add domains to protect** and select the toggle to automatically include the domains you own.
1. Go to **Actions**, open the drop-down **If email is sent by an impersonated user**, and choose the action you want.

    Ouvrez la liste drop-down **Si le courrier électronique** est envoyé par un domaine dont l’identité a été usurpée et choisissez l’action de votre choix.
1. Sélectionnez **Activer les conseils de sécurité pour l’emprunt d’identité.** Choisissez si des conseils doivent être fournis aux utilisateurs lorsque le système détecte des utilisateurs usurpés d’identité, des domaines ou des caractères inhabituels. Sélectionnez **Enregistrer**.
1. Sélectionnez **l’intelligence de** boîte aux lettres et vérifiez qu’elle est allumée. Cela permet à votre courrier électronique d’être plus efficace en apprendant les modèles d’utilisation.
1. Choose **Add trusted senders and domains**. Ici, vous pouvez ajouter des adresses e-mail ou des domaines qui ne doivent pas être classés comme emprunt d’identité.
1. Sélectionnez **Passer en revue vos paramètres,** assurez-vous que tout est correct, **sélectionnez Enregistrer,** puis **Fermer.**

    Votre organisation dispose désormais d’une meilleure protection contre les menaces de hameçonnage.