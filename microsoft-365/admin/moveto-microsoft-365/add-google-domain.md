---
title: Ajouter votre domaine Google Workspace
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
description: Découvrez comment déplacer votre domaine de Google Workspace vers Microsoft 365 pour les entreprises.
ms.openlocfilehash: 35e699de5e1060ecfd58cad7ecd3a16724d686c4
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68204604"
---
# <a name="add-your-google-workspace-domain-to-microsoft-365"></a>Ajouter le domaine Google Workspace à Microsoft 365

Consultez [l’aide de Microsoft 365 petite entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

## <a name="watch-add-google-workspace-domain"></a>Regarder : Ajouter un domaine d’espace de travail Google

Regardez cette vidéo et d’autres encore sont disponibles sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198105).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LWKT?autoplay=false]

Ajoutez votre domaine Google Workspace à Microsoft 365 pour les entreprises afin que vous puissiez continuer à utiliser votre adresse e-mail professionnelle.

1. Accédez au [Centre d’administration Microsoft 365](https://admin.microsoft.com).
1. Dans le Centre d'administration Microsoft 365, dans le volet de navigation de gauche, sélectionnez **Afficher tous les** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**domaines de**</a> >  **paramètres**.
1. Choisissez **Ajouter un domaine**, entrez votre nom de domaine, puis **sélectionnez Utiliser ce domaine**. 
1. Choisissez, **ajoutez un enregistrement TXT aux enregistrements DNS des domaines**, sélectionnez **Continuer** et copiez la valeur TXT. 
1. Retour à la [console Google Administration](https://admin.google.com), choisissez **Domaines**, **Gérer les domaines**, **Afficher les détails**, **Gérer le domaine**, **DNS**, puis faites défiler jusqu’aux **enregistrements de ressources personnalisés**. 
1. Ouvrez la liste déroulante du type d’enregistrement, choisissez **TXT**, collez la valeur TXT que vous avez copiée, puis sélectionnez **Ajouter**. 

    La mise à jour prend généralement un fait en quelques minutes, mais peut prendre jusqu’à 48 heures. 
1. Revenez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centre d’administration</a>, **sélectionnez Vérifier**, puis **Fermez**. 
1. Pour définir votre domaine comme adresse e-mail principale pour vos utilisateurs, dans le volet de navigation de gauche, sélectionnez **Utilisateurs** > [**actifs**](https://go.microsoft.com/fwlink/p/?linkid=834822). 
1. Choisissez un utilisateur, sélectionnez **Gérer le nom d’utilisateur et l’e-mail**, **Modifier**, sélectionnez votre domaine dans la liste déroulante, puis sélectionnez **Terminé** et **Enregistrer les modifications**. 
1. Répétez ce processus pour chaque utilisateur. 

    Une fois que vous avez terminé, vous serez prêt à installer des applications Office et à migrer vos éléments de courrier électronique et de calendrier vers Microsoft 365. 