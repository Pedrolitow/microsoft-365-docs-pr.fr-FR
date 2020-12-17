---
title: Ajouter un domaine
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
description: Découvrez comment ajouter un autre domaine à votre abonnement.
ms.openlocfilehash: 16f6c4e416ede560d69014e320eb32c4453fd3f5
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49702169"
---
# <a name="add-another-domain"></a>Ajouter un autre domaine

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

Il se peut que votre société ait besoin de plusieurs noms de domaine à des fins différentes. Par exemple, vous pouvez ajouter une orthographe différente du nom de votre société car les clients l’utilisent déjà et leurs communications n’ont pas pu vous joindre.

## <a name="try-it"></a>Essayez !

1. Dans le centre d’administration Microsoft 365, sélectionnez **configuration**.
1. Sous **obtenir votre configuration de domaine personnalisé**, sélectionnez **Afficher**.
1. Cliquez sur **gérer**, puis sur **Ajouter un domaine**.
1. Entrez le nouveau nom de domaine que vous souhaitez ajouter, puis cliquez sur **suivant**.
1. Connectez-vous à votre bureau d’enregistrement de domaines, dans ce cas GoDaddy, puis cliquez sur **suivant**.
1. Si vous y êtes invité, connectez-vous à votre bureau d’enregistrement, puis choisissez **autoriser**.
1. Choisissez **Ajouter les enregistrements DNS pour moi**, puis cliquez sur **suivant**.
1. Choisissez les services pour votre nouveau domaine et désactivez les cases à cocher des services qui seront gérés par un autre domaine. Par exemple, si vous souhaitez simplement utiliser le nouveau domaine pour le courrier électronique, choisissez **Exchange**, puis désactivez les cases à cocher de la gestion des appareils **Skype entreprise** et de la **gestion des appareils mobiles pour Office 365**.
1. Sélectionnez **suivant**, **autoriser**, **suivant**, puis **Terminer**. Votre nouveau domaine a été ajouté.

Pour recevoir des courriers électroniques dans votre nouveau domaine, vous devez ajouter un nouvel alias de messagerie pour chaque utilisateur :

1. Sélectionnez **utilisateurs**, **utilisateurs actifs**, puis sélectionnez l’utilisateur auquel le nouvel alias sera affecté.
1. Choisissez **gérer les alias de messagerie**, puis **Ajoutez un alias**.
1. Entrez le nom d’utilisateur, puis choisissez le nouveau domaine dans la liste déroulante.
1. Sélectionnez **enregistrer les modifications**, puis fermez la fenêtre.
1. Répétez ces étapes pour chaque utilisateur qui doit recevoir des courriers électroniques sur le nouveau domaine.