---
title: Optimisation des performances Exchange Online
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Cet article contient des conseils généraux et des liens vers d’autres ressources qui vous indiquent comment améliorer les performances des Exchange Online.
ms.openlocfilehash: 0f1a55648b90cfc07a81928f3e30196f9d928bd5271073828500e58138a4007c
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53794653"
---
# <a name="tune-exchange-online-performance"></a>Optimisation des performances Exchange Online

Cet article contient des conseils généraux et des liens vers d’autres ressources qui vous indiquent comment améliorer les performances des Exchange Online, en particulier devant une migration. Cet article fait partie de la planification réseau et de l’optimisation des performances [pour Office 365](./network-planning-and-performance.md) projet.
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Éléments à prendre en compte afin d’améliorer Exchange Online performances

Pour améliorer la vitesse de migration et réduire les contraintes de bande passante de votre organisation pour Exchange Online, prenons en compte les considérations suivantes :
  
- **Réduisez la taille des boîtes aux lettres.** Une taille de boîte aux lettres plus petite améliore la vitesse de migration. 
    
- **Utilisez les fonctionnalités de déplacement de boîtes aux lettres avec un déploiement Exchange hybride.** Avec un Exchange hybride, le courrier hors connexion (sous la forme . Fichiers OST) ne nécessite pas de re-téléchargement lors de la migration vers Exchange Online. Cela réduit considérablement vos besoins en bande passante de téléchargement. 
    
- **Planifier des déplacements de boîtes aux lettres pendant les périodes de faible trafic Internet et de faible Exchange’utilisation.** Lors de la planification des déplacements, les demandes de migration sont envoyées au proxy de réplication de boîte aux lettres et peuvent ne pas avoir lieu immédiatement. 
    
- **Utilisez des fenêtres popouts légères pour Outlook sur le web.** Les fenêtres pop-out allégées fournissent des versions plus petites et moins intensives en mémoire de certains messages électroniques dans Microsoft Edge ou Internet Explorer en rendant certains composants sur le serveur. Pour plus d’informations, voir [Utiliser des fenêtres publicitaires légères pour réduire la mémoire utilisée lors de la lecture des messages électroniques.](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)


## <a name="general-advice"></a>Conseils généraux

- Assurez-vous que la recherche DNS pour outlook.office.com le centre de données MS à un emplacement d’entrée logique pour votre emplacement.

- Mise en cache de boîte aux lettres de recherche et choix des options appropriées (re. période de mise en cache, mise en cache de boîtes aux lettres partagées, et courrier électronique).

- Conservez vos Outlook de connexions VPN (à un bureau central) avant qu’elles ne passent par Internet.

- Assurez-vous que vos données de boîte aux lettres respectent les limites imposées aux montants des dossiers et des éléments.
    
Pour plus d’informations Exchange performances de migration, voir Office 365 [de migration et les meilleures pratiques.](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)
