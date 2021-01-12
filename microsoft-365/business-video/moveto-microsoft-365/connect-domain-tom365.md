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
ms.openlocfilehash: c7827b93b56560579b31bd2abb5a852467565103
ms.sourcegitcommit: 9833f95ab6ab95aea20d68a277246dca2223f93d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2021
ms.locfileid: "49794641"
---
# <a name="connect-your-domain-to-microsoft-365-for-business"></a>Connecter votre domaine à Microsoft 365 pour les entreprises

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LFpy?autoplay=false]

Une fois que vous avez installé Microsoft 365 et déplacé vos données de courrier à partir de Google Workspace, vous pouvez connecter votre domaine à Microsoft 365. 

Vous devez d’abord supprimer les enregistrements DNS existants de Google, puis nous pouvons ajouter de nouveaux enregistrements DNS à partir de Microsoft 365.

## <a name="try-it"></a>Essayez !

1. Connectez-vous à votre console d’administration Google Workspace [à l’admin.google.com](https://admin.google.com).
1. Select **Domains**, **Manage domains**, **View details**, **Manage domain**, then **DNS** in the left nav.
1. Faites défiler vers le bas **jusqu’aux enregistrements** synthétiques, **ouvrez Google Workspace,** **sélectionnez Supprimer,** puis **Supprimez à** nouveau.
1. Faites défiler vers le bas **jusqu’aux** enregistrements de ressources personnalisés et supprimez tous les enregistrements DNS existants qui apparaissent, y compris ceux que vous avez peut-être créés précédemment pour Microsoft 365.
1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com).
1. In the left nav, choose, **Show all**, **Settings**, **Domains**.
1. Choisissez ensuite votre domaine par défaut.
1. Sélectionnez **Continuer le programme** d’installation, puis, pour connecter votre domaine, choisissez **Continuer.**
1. Faites défiler vers le bas pour afficher les enregistrements DNS qui doivent être copiés dans Google.
1. Ouvrez **MX Records** et sous **Points vers l’adresse ou la valeur,** copiez l’enregistrement.
1. Revenir à Google, puis dans la section **Enregistrements de** ressource personnalisés, ouvrez ladown de type d’enregistrement et sélectionnez **MX**.
1. Dans le **champ** Données, collez l’enregistrement que vous avez copié.
1. Puis sélectionnez **Ajouter**.
1. Répétez le processus pour les enregistrements CNAME et TXT et ajoutez les valeurs dans la page de gestion DNS Google.
1. Revenir au Centre d’administration Microsoft 365 et sélectionnez **Continuer.**

    La configuration de votre domaine est terminée.