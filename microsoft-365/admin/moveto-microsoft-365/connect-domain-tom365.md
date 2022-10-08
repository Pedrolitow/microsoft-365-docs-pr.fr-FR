---
title: Connecter votre domaine à Microsoft 365
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- highpri
- M365-subscription-management
- Adm_O365
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment connecter votre domaine à Microsoft 365.
ms.openlocfilehash: 604a1edb14276c38b36ed81e63238bf93c0d7699
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68188524"
---
# <a name="connect-your-domain-to-microsoft-365-for-business"></a>Connecter votre domaine à Microsoft 365 pour les entreprises

Consultez [l’aide de Microsoft 365 petite entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

## <a name="watch-connect-your-domain-to-microsoft-365"></a>Espion : Connecter votre domaine à Microsoft 365

Regardez cette vidéo et d’autres encore sont disponibles sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198216).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LFpy?autoplay=false]

Une fois que vous avez configuré Microsoft 365 et déplacé vos données de messagerie à partir de Google Workspace, vous pouvez connecter votre domaine à Microsoft 365. 

Tout d’abord, vous devez supprimer des enregistrements DNS existants de Google, puis nous pouvons ajouter de nouveaux enregistrements DNS à partir de Microsoft 365.

1. Connectez-vous à la console d’administration de votre espace de travail Google à [admin.google.com](https://admin.google.com).
1. Sélectionnez **Domaines**, **Gérer les domaines**, **Afficher les détails**, **Gérer le domaine**, puis **DNS** dans le volet de navigation gauche.
1. Faites défiler jusqu’aux **enregistrements synthétiques**, **ouvrez l’espace de travail Google**, **sélectionnez Supprimer**, puis **supprimez** à nouveau.
1. Faites défiler jusqu’aux **enregistrements de ressources personnalisés** et supprimez tous les enregistrements DNS existants qui apparaissent, y compris ceux que vous avez créés précédemment pour Microsoft 365.
1. Accédez au [Centre d’administration Microsoft 365](https://admin.microsoft.com).
1. Dans le volet de navigation de gauche, sélectionnez **Afficher tous les** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**domaines de paramètres**</a> > .
1. Choisissez ensuite votre domaine par défaut.
1. Sélectionnez **Continuer l’installation**, puis, pour connecter votre domaine,  **choisissez Continuer**.
1. Faites défiler vers le bas pour afficher les enregistrements DNS qui doivent être copiés dans Google.
1. Ouvrez **les enregistrements MX** et, sous **Points pour l’adresse ou la valeur**, copiez l’enregistrement.
1. Revenez à Google et, dans la section **Enregistrements de ressources personnalisés** , ouvrez la liste déroulante type d’enregistrement et sélectionnez **MX**.
1. Dans le champ **Données** , collez l’enregistrement que vous avez copié.
1. Puis sélectionnez **Ajouter**.
1. Répétez le processus pour les enregistrements CNAME et TXT et ajoutez les valeurs dans la page de gestion Google DNS.
1. Revenez au Centre d'administration Microsoft 365 et **sélectionnez Continuer**.

    La configuration de votre domaine est terminée.