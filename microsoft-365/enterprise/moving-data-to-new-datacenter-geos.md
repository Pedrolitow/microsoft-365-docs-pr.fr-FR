---
title: Déplacement de données principales vers de nouvelles Microsoft 365 de centres de données
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
f1.keywords:
- NOCSH
description: Découvrez les nouvelles Office 365 de centres de données et comment utiliser l’option de résidence des données pour demander un déplacement de vos données principales vers une nouvelle géo.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ddf0caa30f80033a9cfdbbc4cd19f0811f92fcd5e4f28bb98d0e949f9f67412c
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53854710"
---
# <a name="moving-core-data-to-new-microsoft-365-datacenter-geos"></a>Déplacement de données principales vers de nouvelles Microsoft 365 de centres de données

Nous continuons à ouvrir de nouvelles géos de centres de données pour Microsoft 365 services. Ces nouvelles régions de centre de données permettent d'accroître la capacité et le nombre de ressources de calcul pour prendre en charge la demande continue des clients et l'augmentation de l'utilisation. En outre, les nouvelles régions de centre de données permettent d'héberger des données dans la région pour les données client essentielles. 

Les données client essentielles sont un terme qui fait référence à un sous-ensemble de données client, notamment : 
- Exchange Online de boîte aux lettres (corps du courrier électronique, entrées de calendrier et contenu des pièces jointes)
- SharePoint Contenu du site en ligne et fichiers stockés dans ce site
- Fichiers téléchargés vers OneDrive Entreprise
- Teams messages de conversation, y compris les messages privés, les messages de canal et les images utilisées dans les conversations
  
Les clients existants dont les données client essentielles sont stockées dans une région de centre de données existante ne sont pas concernés par le lancement de la nouvelle région de centre de données. Aucune fonction, fonctionnalité ou certification de conformité unique n'est fournie avec la nouvelle région de centre de données. En tant que client de l'une de ces deux régions, vous bénéficierez de la même qualité de service, ainsi que des mêmes performances et contrôles de sécurité qu'auparavant. Nous proposons aux clients existants répertoriés dans le tableau ci-dessous une option pour demander une migration anticipée des données client essentielles de leur organisation au repos vers leur nouvelle géodécenter de données.
  
|**Clients dont le pays d’inscription client est**|**Précédente région de centre de données**|**Nouvelle géo de centre de données**|**Région disponible depuis**|
|:-----|:-----|:-----|:-----|
|**Japon**| Asie/Pacifique | Japon | Décembre 2014 |
|**Australie, Nouvelle-Zélande, Fidji**| Asie/Pacifique | Australie | Mars 2015 |
|**Inde**| Asie/Pacifique | Inde | Octobre 2015 |
|**Canada**| États-Unis | Canada | Mai 2016 |
|**Royaume-Uni**| Union européenne | Royaume-Uni | Septembre 2016 |
|**Corée du Sud**| Asie/Pacifique | Corée du Sud | Avril 2017 |
|**France**| Union européenne | France | Mars 2018 |
|**Émirats arabes unis**| Union européenne | Émirats arabes unis | Juin 2019 |
|**Afrique du Sud**| Union européenne | Afrique du Sud | Juillet 2019 |
|**Suisse, Liechtenstein**| Union européenne | Suisse | Décembre 2019 |
|**Allemagne**| Union européenne | Allemagne | Décembre 2019 |
|**Norvège**| Union européenne | Norvège | Avril 2020 |
|**Brésil**| Amériques | Brésil | Novembre 2020 |

Depuis le 1er octobre 2020, 2020 clients avec un abonnement Office 365 Éducation inclus dans le client ne sont pas éligibles pour la migration.

La liste complète de l'ensemble des régions de centre de données, des centres de données et l'emplacement des données client au repos est disponible via les [cartes interactives de centre de données](https://office.com/datamaps). 
  
## <a name="data-residency-option"></a>Option de résidence des données

Nous fournissons une option de résidence des données aux clients Microsoft 365 éligibles qui sont couverts par les géos du centre de données répertoriés dans le tableau ci-dessus. Avec cette option, les clients éligibles ayant des exigences en matière de résidence des données peuvent demander la migration des données client essentielles de leur organisation au repos vers leur nouvelle géodécenter de données.  Microsoft proposera une échéance déterminée à tous les clients éligibles qui demandent la migration pendant la fenêtre d’inscription.  Pour plus [d’informations](request-your-data-move.md) sur la fenêtre d’inscription ouverte de votre site géographique de centres de données et les étapes à suivre pour vous inscrire au programme, voir la page Procédure de demande de déplacement de données.  Les déplacements de données peuvent prendre jusqu’à 24 mois après la fin de la période de demande.

Aucune fonction, fonctionnalité ou certification de conformité unique n'est fournie avec la nouvelle région de centre de données.
    
La complexité, la précision et l'échelle en fonction desquelles nous devons effectuer les déplacements de données dans un environnement automatisé et commandé de façon globale ne nous permettent pas d'indiquer la date de fin du déplacement pour votre client ou tout autre client unique. Les clients recevront une confirmation dans le centre de messages pour chaque service concerné une fois que le déplacement des données sera terminé. 
    
Les déplacements de données sont des opérations de service principales qui ont une incidence minime sur les utilisateurs finals. Les fonctionnalités pouvant être concernées sont répertoriées à la page [Pendant et après le déplacement de vos données](during-and-after-your-data-move.md). Nous respectons le [contrat de niveau de service Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkId=523897) concernant la disponibilité. Ainsi, les clients n'ont rien à préparer ou à surveiller pendant le déplacement. Si besoin, le client est averti de toute maintenance de service. 

Les déplacements de données vers la nouvelle géo de centres de données sont effectués sans frais supplémentaires pour le client.
    
## <a name="related-topics"></a>Sujets connexes 
 
[Procédure de demande d’un déplacement de données](request-your-data-move.md)
    
[FAQ général relatif au déplacement de données](data-move-faq.yml)
  
[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Services Azure par région](https://azure.microsoft.com/regions/)

[Teams expérience utilisateur dans Microsoft 365 client multigéogé](/microsoftteams/teams-experience-o365odb-spo-multi-geo)
