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
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment connecter votre domaine à Microsoft 365.
ms.openlocfilehash: d54b3bbf00dd0cf37006924e2884f2861c345d3e
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2022
ms.locfileid: "62825589"
---
# <a name="connect-your-domain-to-microsoft-365-for-business"></a>Connecter votre domaine pour Microsoft 365 entreprise

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LFpy?autoplay=false]

Une fois que vous avez Microsoft 365 et déplacé vos données de courrier à partir de Google Workspace, vous pouvez connecter votre domaine à Microsoft 365. 

Tout d’abord, vous devez supprimer des enregistrements DNS existants de Google, puis nous pouvons ajouter de nouveaux enregistrements DNS à partir Microsoft 365.

## <a name="try-it"></a>Essayez !

1. Connectez-vous à votre console d’administration Google Workspace [admin.google.com](https://admin.google.com).
1. **Sélectionnez Domaines**, **Gérer les domaines**, **Afficher les détails**, **Gérer** le domaine, puis **DNS** dans le navigation gauche.
1. Faites défiler vers le bas **jusqu’aux enregistrements** synthétiques, ouvrez **Google Workspace**, **sélectionnez Supprimer**, puis **Supprimez à** nouveau.
1. Faites défiler vers le bas **jusqu’aux** enregistrements de ressource personnalisés et supprimez tous les enregistrements DNS existants qui apparaissent, y compris ceux que vous avez peut-être créés précédemment pour Microsoft 365.
1. Accédez au [Centre d’administration Microsoft 365](https://admin.microsoft.com).
1. Dans le navigation gauche, **choisissez Afficher** >  tous **les Paramètres** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.
1. Choisissez ensuite votre domaine par défaut.
1. **Sélectionnez Continuer l’installation**, puis, pour connecter votre domaine, sélectionnez **Continuer**.
1. Faites défiler vers le bas pour afficher les enregistrements DNS qui doivent être copiés dans Google.
1. **Ouvrez les enregistrements MX**, puis sous **Pointe vers l’adresse ou la valeur**, copiez l’enregistrement.
1. Revenir à Google et, dans la section **Enregistrements de** ressource personnalisés, ouvrez ladown du type d’enregistrement et sélectionnez **MX**.
1. Dans le **champ** Données, collez l’enregistrement que vous avez copié.
1. Puis sélectionnez **Ajouter**.
1. Répétez le processus pour les enregistrements CNAME et TXT et ajoutez les valeurs dans la page de gestion DNS Google.
1. Revenir à la Centre d'administration Microsoft 365 puis sélectionnez **Continuer**.

    La configuration de votre domaine est terminée.