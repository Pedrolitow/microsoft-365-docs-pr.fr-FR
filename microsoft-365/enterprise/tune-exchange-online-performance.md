---
title: Optimisation des performances Exchange Online
ms.author: krowley
author: tracyp
manager: scotv
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Cet article contient des conseils généraux et des liens vers d’autres ressources qui vous indiquent comment améliorer les performances de Exchange Online.
ms.openlocfilehash: dccd592c15f19229d968fd3585f1760e35ae617f
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68170198"
---
# <a name="tune-exchange-online-performance"></a>Optimisation des performances Exchange Online

Cet article contient des conseils généraux et des liens vers d’autres ressources qui vous indiquent comment améliorer les performances de Exchange Online, en particulier devant une migration. Cet article fait partie de la [planification réseau et de l’optimisation des performances pour Office 365](./network-planning-and-performance.md) projet.
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Éléments à prendre en compte pour améliorer Exchange Online performances

Pour améliorer la vitesse de migration et réduire les contraintes de bande passante de votre organisation pour Exchange Online, tenez compte des points suivants :
  
- **Réduisez les tailles de boîte aux lettres.** Une taille de boîte aux lettres plus petite améliore la vitesse de migration. 
    
- **Utilisez les fonctionnalités de déplacement de boîte aux lettres avec un déploiement hybride Exchange.** Avec un déploiement exchange hybride, courrier hors connexion (sous la forme de . Les fichiers OST) ne nécessitent pas de nouveau téléchargement lors de la migration vers Exchange Online. Cela réduit considérablement vos besoins en bande passante de téléchargement. 
    
- **Planifiez les déplacements de boîte aux lettres pendant les périodes de faible trafic Internet et de faible utilisation locale d’Exchange.** Lors de la planification des déplacements, les demandes de migration sont envoyées au proxy de réplication de boîte aux lettres et peuvent ne pas avoir lieu immédiatement. 
    
- **Utilisez des fenêtres contextuelles maigres pour Outlook sur le web.** Les fenêtres contextuelles maigres fournissent des versions plus petites et moins gourmandes en mémoire de certains messages électroniques dans Microsoft Edge ou Internet Explorer en affichant certains composants sur le serveur. Pour plus d’informations, consultez [Utiliser des fenêtres contextuelles maigres pour réduire la mémoire utilisée lors de la lecture des messages électroniques](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).


## <a name="general-advice"></a>Conseils généraux

- Assurez-vous que la recherche DNS pour outlook.office.com entre dans le centre de données MS à un emplacement d’entrée logique pour votre emplacement.

- Recherchez la mise en cache de boîte aux lettres et choisissez les options appropriées (re. période de mise en cache, mise en cache de boîtes aux lettres partagées, etc.).

- Empêchez vos données Outlook de transmettre des connexions VPN (à un bureau central) avant qu’elles ne passent par Internet.

- Assurez-vous que vos données de boîte aux lettres respectent les limitations relatives aux montants des dossiers et des éléments.
    
Pour plus d’informations sur les performances de migration Exchange, consultez [Office 365 performances de migration et les meilleures pratiques](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
