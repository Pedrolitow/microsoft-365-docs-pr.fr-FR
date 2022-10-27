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
- Tier2
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
ms.openlocfilehash: 7b724a4802659a85eb1c5315f6c74f0f0bf946ff
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68726593"
---
# <a name="connect-your-domain-to-microsoft-365-for-business"></a>Connecter votre domaine à Microsoft 365 pour les entreprises

Consultez [l’aide de Microsoft 365 petite entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

## <a name="watch-connect-your-domain-to-microsoft-365"></a>Regarder : Connecter votre domaine à Microsoft 365

Regardez cette vidéo et d’autres encore sont disponibles sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198216).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LFpy?autoplay=false]

Une fois que vous avez configuré Microsoft 365 et déplacé vos données de courrier à partir de Google Workspace, vous pouvez connecter votre domaine à Microsoft 365. 

Tout d’abord, vous devez supprimer les enregistrements DNS existants de Google, puis nous pouvons ajouter de nouveaux enregistrements DNS à partir de Microsoft 365.

1. Connectez-vous à la console d’administration de votre espace de travail Google à [l’adresse admin.google.com](https://admin.google.com).
1. Sélectionnez **Domaines**, **Gérer les domaines**, **Afficher les détails**, **Gérer le domaine**, puis **DNS** dans la navigation de gauche.
1. Faites défiler jusqu’à **Enregistrements synthétiques**, ouvrez **Google Workspace**, sélectionnez **Supprimer**, puis **Supprimer** à nouveau.
1. Faites défiler vers le bas **jusqu’à Enregistrements de ressources personnalisés** et supprimez tous les enregistrements DNS existants qui s’affichent, y compris ceux que vous avez peut-être créés précédemment pour Microsoft 365.
1. Accédez au [Centre d’administration Microsoft 365](https://admin.microsoft.com).
1. Dans la navigation de gauche, choisissez **Afficher tous les** > **domaines paramètres** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>
1. Choisissez ensuite votre domaine par défaut.
1. Sélectionnez **Continuer l’installation**, puis, pour connecter votre domaine, choisissez  **Continuer**.
1. Faites défiler vers le bas pour afficher les enregistrements DNS qui doivent être copiés dans Google.
1. Ouvrez **Enregistrements MX**, puis sous **Points vers l’adresse ou la valeur**, copiez l’enregistrement.
1. Revenez à Google et, dans la section **Enregistrements de ressources personnalisés** , ouvrez la liste déroulante type d’enregistrement et sélectionnez **MX**.
1. Dans le champ **Données** , collez l’enregistrement que vous avez copié.
1. Puis sélectionnez **Ajouter**.
1. Répétez le processus pour les enregistrements CNAME et TXT et ajoutez les valeurs dans la page de gestion GOOGLE DNS.
1. Revenez à la Centre d'administration Microsoft 365 et sélectionnez **Continuer**.

    La configuration de votre domaine est terminée.