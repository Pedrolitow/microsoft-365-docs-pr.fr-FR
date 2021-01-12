---
title: Ajouter votre domaine Google Workspace
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
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
description: Découvrez comment déplacer votre domaine de Google Workspace vers Microsoft 365 pour les entreprises.
ms.openlocfilehash: 1abc05867147d2b52e26804918e8247053b5e1d5
ms.sourcegitcommit: 9833f95ab6ab95aea20d68a277246dca2223f93d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2021
ms.locfileid: "49794676"
---
# <a name="add-your-google-workspace-domain-to-microsoft-365"></a>Ajouter votre domaine Google Workspace à Microsoft 365

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LWKT?autoplay=false]

Ajoutez votre domaine Google Workspace à Microsoft 365 pour les entreprises afin de continuer à utiliser votre adresse de messagerie professionnelle.

## <a name="try-it"></a>Essayez !

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com).
1. In the Microsoft 365 Admin Center, in the left nav, select **Show all**, **Settings** and then **Domains**.
1. Choisissez **Ajouter un domaine,** entrez votre nom de domaine, puis **sélectionnez Utiliser ce domaine.** 
1. Choose, **Add a TXT record to the domains DNS records,** select **Continue**, and copy the TXT value. 
1. Revenir à la [console d’administration Google,](https://admin.google.com)choisissez **Domaines,** Gérer les domaines, Afficher les **détails,** Gérer le domaine, **DNS,** puis faites défiler vers le bas jusqu’aux enregistrements de ressources **personnalisés.**   
1. Ouvrez la drop-down du type d’enregistrement, choisissez **TXT**, collez la valeur TXT que vous avez copiée, puis sélectionnez **Ajouter**. 

    La mise à jour prend généralement quelques minutes, mais peut prendre jusqu’à 48 heures. 
1. Revenir au Centre d’administration Microsoft 365, **sélectionnez Vérifier,** puis **Fermez.** 
1. Pour définir votre domaine comme courrier électronique principal pour vos utilisateurs, dans le navigation de gauche, sélectionnez **Utilisateurs**  >  **actifs.** 
1. Choisissez un utilisateur, sélectionnez Gérer le nom **d’utilisateur** et le courrier électronique, **Modifier,** sélectionner votre domaine dans la liste modifiable, puis sélectionner Terminé **et** enregistrer **les modifications.** 
1. Répétez ce processus pour chaque utilisateur. 

    Lorsque vous avez terminé, vous êtes prêt à installer les applications Office et à migrer vos éléments de courrier et de calendrier vers Microsoft 365. 