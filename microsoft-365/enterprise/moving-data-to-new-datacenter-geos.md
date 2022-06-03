---
title: Déplacement de données de base vers de nouvelles zones géographiques de centre de données Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/02/2022
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
f1.keywords:
- NOCSH
description: Découvrez les nouvelles zones géographiques de centre de données Office 365 et comment utiliser l’option de résidence des données pour demander un déplacement de vos données principales vers une nouvelle zone géographique.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c70d59edba9cd35710b315adc8f93d6139fd2595
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873575"
---
# <a name="moving-core-data-to-new-microsoft-365-datacenter-geos"></a>Déplacement de données de base vers de nouvelles zones géographiques de centre de données Microsoft 365

Nous continuons à ouvrir de nouvelles zones géographiques de centre de données pour Microsoft 365 services. Ces nouvelles régions de centre de données permettent d'accroître la capacité et le nombre de ressources de calcul pour prendre en charge la demande continue des clients et l'augmentation de l'utilisation. En outre, les nouvelles régions de centre de données permettent d'héberger des données dans la région pour les données client essentielles.

Les données client principales sont un terme qui fait référence à un sous-ensemble de données client, notamment :

- Exchange Online contenu de boîte aux lettres (corps de l’e-mail, entrées de calendrier et contenu des pièces jointes)
- SharePoint contenu du site en ligne et les fichiers stockés dans ce site
- Fichiers chargés dans OneDrive Entreprise
- Teams les messages de conversation, y compris les messages privés, les messages de canal et les images utilisés dans les conversations
  
Les clients existants dont les données client essentielles sont stockées dans une région de centre de données existante ne sont pas concernés par le lancement de la nouvelle région de centre de données. Aucune fonction, fonctionnalité ou certification de conformité unique n'est fournie avec la nouvelle région de centre de données. En tant que client de l'une de ces deux régions, vous bénéficierez de la même qualité de service, ainsi que des mêmes performances et contrôles de sécurité qu'auparavant. Nous offrons aux clients existants répertoriés dans le tableau ci-dessous une option permettant de demander une migration anticipée des données client principales de leur organisation au repos vers leur nouvelle zone géographique de centre de données.
  
| Clients avec le pays d’inscription de locataire dans | Précédente région de centre de données | Nouvelle région de centre de données | Région disponible depuis |
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
|**Suède**| Union européenne | Suède | Novembre 2021 |

À compter du 1er octobre 2020, les clients disposant d’un abonnement Office 365 Éducation inclus dans le locataire ne sont pas éligibles à la migration.

La liste complète de l'ensemble des régions de centre de données, des centres de données et l'emplacement des données client au repos est disponible via les [cartes interactives de centre de données](https://office.com/datamaps).
  
## <a name="data-residency-option"></a>Option de résidence des données

Nous fournissons une option de résidence des données aux clients éligibles Microsoft 365 qui sont couverts par les zones géographiques du centre de données répertoriées dans le tableau ci-dessus. Avec cette option, les clients éligibles ayant des exigences de résidence des données peuvent demander la migration des données client principales de leur organisation au repos vers leur nouvelle zone géographique de centre de données.  Microsoft proposera une échéance validée à tous les clients éligibles qui demandent la migration pendant la fenêtre d’inscription.  Consultez la page [Comment demander votre déplacement de données](request-your-data-move.md) pour plus d’informations sur la fenêtre d’inscription ouverte pour la zone géographique de votre centre de données et les étapes à suivre pour vous inscrire au programme.  Les déplacements de données peuvent prendre jusqu'à 24 mois à compter de la fin de la période de demande.

Aucune fonction, fonctionnalité ou certification de conformité unique n'est fournie avec la nouvelle région de centre de données.

La complexité, la précision et l'échelle en fonction desquelles nous devons effectuer les déplacements de données dans un environnement automatisé et commandé de façon globale ne nous permettent pas d'indiquer la date de fin du déplacement pour votre client ou tout autre client unique. Les clients recevront une confirmation dans le centre de messages pour chaque service concerné une fois que le déplacement des données sera terminé.

Les déplacements de données sont des opérations de service principales qui ont une incidence minime sur les utilisateurs finals. Les fonctionnalités pouvant être concernées sont répertoriées à la page [Pendant et après le déplacement de vos données](during-and-after-your-data-move.md). Nous respectons le [contrat de niveau de service Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkId=523897) concernant la disponibilité. Ainsi, les clients n'ont rien à préparer ou à surveiller pendant le déplacement. Si besoin, le client est averti de toute maintenance de service.

Les déplacements de données vers la nouvelle zone géographique du centre de données sont effectués sans coût supplémentaire pour le client.

## <a name="related-topics"></a>Rubriques connexes

[Procédure de demande d’un déplacement de données](request-your-data-move.md)

[FAQ général relatif au déplacement de données](data-move-faq.md)
  
[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Services Azure par région](https://azure.microsoft.com/regions/)

[Teams expérience dans une location Microsoft 365 multigéographique](/microsoftteams/teams-experience-o365odb-spo-multi-geo)
