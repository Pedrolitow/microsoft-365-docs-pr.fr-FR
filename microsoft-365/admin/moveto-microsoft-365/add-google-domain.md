---
title: Ajouter votre domaine Google Workspace
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
description: Découvrez comment déplacer votre domaine de Google Workspace vers Microsoft 365 entreprise.
ms.openlocfilehash: b41fdf304d0f0b9680f87f40a4564573593d6e75
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2022
ms.locfileid: "62825596"
---
# <a name="add-your-google-workspace-domain-to-microsoft-365"></a>Ajoutez votre domaine Google Workspace à Microsoft 365

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LWKT?autoplay=false]

Ajoutez votre domaine Google Workspace à Microsoft 365 entreprise afin de continuer à utiliser votre adresse de messagerie professionnelle.

## <a name="try-it"></a>Essayez !

1. Accédez au [Centre d’administration Microsoft 365](https://admin.microsoft.com).
1. Dans la Centre d'administration Microsoft 365, dans le navigation gauche, sélectionnez **Afficher** >  **Paramètres** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domaines**</a>.
1. **Sélectionnez Ajouter un domaine**, entrez votre nom de domaine, puis **sélectionnez Utiliser ce domaine**. 
1. Choose, **Add a TXT record to the domains DNS records**, select **Continue**, and copy the TXT value. 
1. Revenir à la [console](https://admin.google.com) d’administration Google, sélectionnez **Domaines, Gérer** les domaines, Afficher les **détails****, Gérer** le domaine, **DNS**, puis faites défiler vers le bas jusqu’aux **enregistrements de ressources personnalisés**.  
1. Ouvrez la drop-down du type d’enregistrement, choisissez **TXT**, collez la valeur TXT que vous avez copiée, puis sélectionnez **Ajouter**. 

    La mise à jour prend généralement quelques minutes, mais peut prendre jusqu’à 48 heures. 
1. Revenir au Centre <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">d’administration</a>, **sélectionnez Vérifier**, puis **Fermez**. 
1. Pour définir votre domaine comme courrier électronique principal pour vos utilisateurs, dans le navigation de gauche, sélectionnez **Utilisateurs** >  [**UsersActive**](https://go.microsoft.com/fwlink/p/?linkid=834822). 
1. Choisissez un utilisateur, sélectionnez Gérer le nom **d’utilisateur** et le courrier électronique, **Modifier**, sélectionner votre domaine dans la liste modifiable, puis sélectionner **Terminé et** **enregistrer les modifications**. 
1. Répétez ce processus pour chaque utilisateur. 

    Lorsque vous avez terminé, vous serez prêt à installer Office applications et à migrer vos éléments de courrier électronique et de calendrier vers Microsoft 365. 