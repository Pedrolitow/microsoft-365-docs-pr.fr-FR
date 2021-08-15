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
description: Découvrez comment déplacer votre domaine de Google Workspace vers Microsoft 365 entreprise.
ms.openlocfilehash: 77d1284d842c862eb8044db0fc461618e48300756ca462fa3ac957a4eea82e84
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53861574"
---
# <a name="add-your-google-workspace-domain-to-microsoft-365"></a>Ajoutez votre domaine Google Workspace à Microsoft 365

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LWKT?autoplay=false]

Ajoutez votre domaine Google Workspace à Microsoft 365 entreprise afin de continuer à utiliser votre adresse de messagerie professionnelle.

## <a name="try-it"></a>Essayez !

1. Go to the [Centre d’administration Microsoft 365](https://admin.microsoft.com).
1. Dans le Administration Microsoft 365, dans le navigation de gauche, sélectionnez Afficher **tout, Paramètres** puis **Domaines**.
1. Choisissez **Ajouter un domaine,** entrez votre nom de domaine, puis **sélectionnez Utiliser ce domaine.** 
1. Choose, **Add a TXT record to the domains DNS records,** select **Continue**, and copy the TXT value. 
1. Revenir à la [console d’administration Google,](https://admin.google.com)choisissez **Domaines,** Gérer les domaines, Afficher les **détails,** Gérer le domaine, **DNS,** puis faites défiler vers le bas jusqu’aux enregistrements de ressources **personnalisés.**   
1. Ouvrez la drop-down du type d’enregistrement, choisissez **TXT**, collez la valeur TXT que vous avez copiée, puis sélectionnez **Ajouter**. 

    La mise à jour prend généralement quelques minutes, mais peut prendre jusqu’à 48 heures. 
1. Revenir au centre Administration Microsoft 365, **sélectionnez Vérifier,** puis **Fermez.** 
1. Pour définir votre domaine comme courrier électronique principal pour vos utilisateurs, dans le navigation de gauche, sélectionnez **Utilisateurs**  >  **actifs.** 
1. Choisissez un utilisateur, sélectionnez Gérer le nom **d’utilisateur** et le courrier électronique, **Modifier,** sélectionner votre domaine dans la liste modifiable, puis sélectionnez Terminé **et** Enregistrer **les modifications.** 
1. Répétez ce processus pour chaque utilisateur. 

    Lorsque vous avez terminé, vous serez prêt à installer Office applications et à migrer vos éléments de courrier et de calendrier vers Microsoft 365. 