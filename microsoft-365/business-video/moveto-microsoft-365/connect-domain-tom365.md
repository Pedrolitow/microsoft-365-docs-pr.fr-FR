---
title: Connecter votre domaine à Microsoft 365
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
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
description: Découvrez comment connecter votre domaine à Microsoft 365.
ms.openlocfilehash: b91b6fcc297449906e54a8f61f52b9d3c8b01ca6d009d43fa69a5873b81eb873
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53887862"
---
# <a name="connect-your-domain-to-microsoft-365-for-business"></a>Connecter votre domaine pour Microsoft 365 entreprise

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LFpy?autoplay=false]

Une fois que vous avez Microsoft 365 et déplacé vos données de courrier à partir de Google Workspace, vous pouvez connecter votre domaine à Microsoft 365. 

Tout d’abord, vous devez supprimer des enregistrements DNS existants de Google, puis nous pouvons ajouter de nouveaux enregistrements DNS à partir Microsoft 365.

## <a name="try-it"></a>Essayez !

1. Connectez-vous à votre console d’administration Google Workspace [admin.google.com](https://admin.google.com).
1. Select **Domains**, **Manage domains**, **View details**, **Manage domain**, then **DNS** in the left nav.
1. Faites défiler vers le bas **jusqu’aux enregistrements** synthétiques, **ouvrez Google Workspace,** **sélectionnez Supprimer,** puis **Supprimez à** nouveau.
1. Faites défiler vers le bas **jusqu’aux** enregistrements de ressource personnalisés et supprimez tous les enregistrements DNS existants qui apparaissent, y compris ceux que vous avez peut-être créés précédemment pour Microsoft 365.
1. Go to the [Centre d’administration Microsoft 365](https://admin.microsoft.com).
1. In the left nav, choose, **Show all**, **Paramètres**, **Domains**.
1. Choisissez ensuite votre domaine par défaut.
1. Sélectionnez **Continuer le programme** d’installation, puis, pour connecter votre domaine, choisissez **Continuer.**
1. Faites défiler vers le bas pour afficher les enregistrements DNS qui doivent être copiés dans Google.
1. Ouvrez **MX Records** et sous **Points vers l’adresse ou la valeur,** copiez l’enregistrement.
1. Revenir à Google, puis dans la section **Enregistrements de** ressource personnalisés, ouvrez ladown de type d’enregistrement et sélectionnez **MX**.
1. Dans le **champ** Données, collez l’enregistrement que vous avez copié.
1. Puis sélectionnez **Ajouter**.
1. Répétez le processus pour les enregistrements CNAME et TXT et ajoutez les valeurs dans la page de gestion DNS Google.
1. Revenir au centre Administration Microsoft 365 puis sélectionnez **Continuer.**

    La configuration de votre domaine est terminée.