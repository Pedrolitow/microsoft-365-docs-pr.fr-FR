---
title: Configuration de la protection anti-hameçonnage
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
description: Découvrez comment configurer la protection anti-hameçonnage.
ms.openlocfilehash: f3a1399c8a6a51c7b14af7ffea8fbaea39cd1541
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49702234"
---
# <a name="set-up-anti-phishing"></a>Configurer le hameçonnage

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvt9r?autoplay=false]

Le hameçonnage est une attaque malveillante dans laquelle un message électronique semble avoir été envoyé à partir d’une source familière, mais il tente de collecter vos informations personnelles. Par défaut, Microsoft 365 inclut une protection anti-hameçonnage, mais vous pouvez augmenter cette protection en affinant les paramètres. Jetons un œil.

## <a name="try-it"></a>Essayez !

1. Dans le centre d’administration [https://admin.microsoft.com](https://admin.microsoft.com) , sélectionnez **sécurité**, **gestion des menaces**, **stratégie**, puis **protection contre le hameçonnage (ATP**).
1. Sélectionnez **stratégie par défaut** pour l’affiner.
1. Dans la section **emprunt d’identité** , sélectionnez **modifier**.
1. Accédez à **Ajouter des domaines à protéger** , puis sélectionnez le bouton bascule pour inclure automatiquement les domaines que vous possédez.
1. Accédez à **actions**, ouvrez la liste déroulante **si le courrier électronique est envoyé par un utilisateur emprunté**, puis choisissez l’action souhaitée.

    Ouvrez la liste déroulante **si le courrier électronique est envoyé par un domaine emprunté** et choisissez l’action souhaitée.
1. Sélectionnez **activer les conseils de sécurité pour l’emprunt d’identité**. Déterminez si des conseils doivent être fournis aux utilisateurs lorsque le système détecte des utilisateurs, des domaines ou des caractères inhabituels. Sélectionnez **Enregistrer**.
1. Sélectionnez **intelligence des boîtes aux lettres** et vérifiez qu’elle est activée. Cela permet d’améliorer l’efficacité de votre courrier électronique en apprenant des modèles d’utilisation.
1. Choisissez **Ajouter des expéditeurs et des domaines approuvés**. Ici, vous pouvez ajouter des adresses de messagerie ou des domaines qui ne doivent pas être classés comme emprunt d’identité.
1. Choisissez **vérifier vos paramètres**, vérifiez que tout est correct, sélectionnez **Enregistrer**, puis **Fermer**.

    Votre organisation offre désormais une meilleure protection contre les menaces de hameçonnage.