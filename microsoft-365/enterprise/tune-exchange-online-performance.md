---
title: Optimisation des performances Exchange Online
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
description: Cet article contient des conseils généraux et des liens vers d’autres ressources qui vous indiquent comment améliorer les performances d’Exchange Online.
ms.openlocfilehash: 495b662aa6ef247a5751febbf2d50e1c1f21a44e
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46690057"
---
# <a name="tune-exchange-online-performance"></a>Optimisation des performances Exchange Online

Cet article contient des conseils généraux et des liens vers d’autres ressources qui vous indiquent comment améliorer les performances d’Exchange Online, en particulier avant une migration. Cet article fait partie de la planification réseau et de l’optimisation des performances pour le projet [Office 365.](https://aka.ms/tune)
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Éléments à prendre en compte pour améliorer les performances d’Exchange Online

Pour améliorer la vitesse de migration et réduire les contraintes de bande passante de votre organisation pour Exchange Online, prenons en compte les considérations suivantes :
  
- **Réduisez la taille des boîtes aux lettres.** Une taille de boîte aux lettres plus petite améliore la vitesse de migration. 
    
- **Utilisez les fonctionnalités de déplacement de boîtes aux lettres avec un déploiement hybride Exchange.** Avec un déploiement hybride Exchange, la messagerie hors connexion (sous la forme . Fichiers OST) ne nécessite pas de re-téléchargement lors de la migration vers Exchange Online. Cela réduit considérablement vos besoins en bande passante de téléchargement. 
    
- **Planifier les déplacements de boîtes aux lettres pendant les périodes de faible trafic Internet et d’utilisation d’Exchange sur site faible.** Lors de la planification des déplacements, les demandes de migration sont envoyées au proxy de réplication de boîte aux lettres et peuvent ne pas avoir lieu immédiatement. 
    
- **Utilisez des fenêtres pop-out allégées pour Outlook sur le web.** Les fenêtres pop-out allégées fournissent des versions plus petites et moins intensives en mémoire de certains messages électroniques dans Microsoft Edge ou Internet Explorer en rendant certains composants sur le serveur. Pour plus d’informations, voir [Utiliser des fenêtres publicitaires légères](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)pour réduire la mémoire utilisée lors de la lecture des messages électroniques.


## <a name="general-advice"></a>Conseils généraux

- Assurez-vous que la recherche DNS pour outlook.office.com le centre de données MS à un emplacement d’entrée logique pour votre emplacement.

- Mise en cache de boîte aux lettres de recherche et choix des options appropriées (re. période de mise en cache, mise en cache de boîtes aux lettres partagées, et courrier électronique).

- Veillez à ce que vos données Outlook ne passent pas de connexions VPN (à un bureau central) avant qu’elles ne passent par Internet.

- Assurez-vous que vos données de boîte aux lettres respectent les limites imposées aux montants des dossiers et des éléments.
    
Pour plus d’informations sur les performances de migration Exchange, consultez les meilleures pratiques et performances de [migration d’Office 365.](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)
  

