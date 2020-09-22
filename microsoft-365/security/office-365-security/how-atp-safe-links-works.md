---
title: Fonctionnement des liens fiables PACM
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: La fonctionnalité liens fiables permet de vérifier le temps de cliquer sur les liens hypertexte dans les documents Office et dans les messages électroniques. Lisez cet article pour découvrir le fonctionnement des liens fiables ATP.
ms.openlocfilehash: 09357b20173e2609587137764737c8aba044190e
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48201464"
---
# <a name="how-atp-safe-links-works"></a>Fonctionnement des liens fiables PACM

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT] 
> Pour que les liens sécurisés ATP Office 365 fonctionnent correctement, tous les services doivent être au même niveau de version.
         
## <a name="how-atp-safe-links-works"></a>Fonctionnement des liens fiables PACM

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]
 avec des URL dans le courrier électronique

À un niveau élevé, voici le fonctionnement de la protection [des liens fiables ATP](atp-safe-links.md) pour les URL dans les messages électroniques (hébergé dans Office 365, pas en local) :
  
1. Les utilisateurs reçoivent des messages électroniques, dont certains contiennent des URL.
    
2. Tous les messages passent par Exchange Online Protection, où les filtres IP (Internet Protocol) et des enveloppes, la protection contre les programmes malveillants basée sur la signature, le blocage du courrier indésirable et les filtres anti-programme malveillant sont appliqués. 
    
3. Le courrier électronique arrive dans les boîtes de réception des utilisateurs.
    
4. Un utilisateur se connecte à Office 365 et accède à sa boîte de réception.
    
5. L’utilisateur ouvre un message électronique et clique sur une URL dans le message électronique.
    
6. La fonctionnalité de liens fiables ATP vérifie immédiatement l’URL avant d’ouvrir le site Web. L’URL est identifiée comme étant bloquée, malveillante ou sécurisée.
        
   - Si l’URL est vers un site Web inclus dans la [liste des URL bloquées personnalisées](set-up-a-custom-blocked-urls-list-atp.md)de l’organisation, une [page d’avertissement](atp-safe-links-warning-pages.md) s’ouvre. 
    
   - Si l’URL est vers un site Web qui a été jugé malveillant, une [page d’avertissement](atp-safe-links-warning-pages.md) s’ouvre. 
    
   - Si l’URL est dirigée vers un fichier téléchargeable et que les [stratégies de liens fiables ATP](set-up-atp-safe-links-policies.md) de votre organisation sont configurées pour analyser ce contenu, le fichier téléchargeable est vérifié. 
    
   - Si l’URL est jugée fiable, le site Web s’ouvre.
    
## <a name="how-atp-safe-links-works"></a>Fonctionnement des liens fiables PACM

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]
 avec des URL dans des documents Office 

À un niveau élevé, voici le mode de protection [des liens fiables ATP](atp-safe-links.md) pour les URL dans les applications Microsoft 365 pour les applications Enterprise Premium (versions actuelles de Word, Excel et PowerPoint sur Windows, Mac ou dans un navigateur, les applications Office sur les appareils iOS ou Android, Visio sur Windows, OneNote dans un navigateur) :
  
1. Les utilisateurs ont installé Microsoft 365 apps pour Enterprise ou Business Premium sur leur ordinateur, smartphone ou tablette. (Ou, ils utilisent Office dans leur navigateur.)
    
2. Un utilisateur ouvre un Word, Excel, PowerPoint, OneNote (dans le navigateur) ou Visio (sur le bureau) et se connecte à Office 365 Enterprise à l’aide de son compte professionnel ou scolaire. Le document contient des URL.
    
3. Lorsque l’utilisateur clique sur une URL dans le document, le lien est vérifié par le service de liens fiables ATP.
    
   - Si l’URL est vers un site Web inclus dans la [liste des URL bloquées personnalisées](set-up-a-custom-blocked-urls-list-atp.md)de l’organisation, l’utilisateur est dirigé vers une [page d’avertissement](atp-safe-links-warning-pages.md).
    
   - Si l’URL est vers un site Web qui a été jugé malveillant, l’utilisateur est dirigé vers une [page d’avertissement](atp-safe-links-warning-pages.md).
    
   - Si l’URL mène à un fichier téléchargeable et que les [stratégies de liens fiables ATP](set-up-atp-safe-links-policies.md) sont configurées pour analyser ces téléchargements, le fichier téléchargeable est vérifié. 
    
   - Si l’URL est considérée comme fiable, l’utilisateur est dirigé vers le site Web.
      
   - Si la vérification de l’URL échoue, la protection des liens fiables n’est pas déclenchée. Sur les clients de bureau, l’utilisateur est averti avant de passer au site.
      
> [!NOTE]
> Cette opération peut prendre plusieurs secondes au début de chaque session pour vérifier que l’utilisateur a activé les liens approuvés pour Office. 
      
