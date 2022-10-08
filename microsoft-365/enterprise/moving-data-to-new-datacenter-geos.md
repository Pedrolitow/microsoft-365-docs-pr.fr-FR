---
title: Déplacement de données de base vers de nouvelles zones géographiques de centre de données Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/23/2022
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
f1.keywords:
- NOCSH
description: Découvrez les nouvelles zones géographiques de centre de données Office 365 et comment utiliser l’option de résidence des données pour demander un déplacement de vos données principales vers une nouvelle zone géographique.
ms.custom: seo-marvel-apr2020
ms.collection: scotvorg
ms.openlocfilehash: 084753e838f02eccd228603cbb6540c1b01d85bc
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68172420"
---
# <a name="moving-core-data-to-new-microsoft-365-datacenter-geos"></a>Déplacement de données de base vers de nouvelles zones géographiques de centre de données Microsoft 365

Nous continuons à ouvrir de nouvelles zones géographiques de centre de données pour les services Microsoft 365. Ces nouvelles régions de centre de données permettent d'accroître la capacité et le nombre de ressources de calcul pour prendre en charge la demande continue des clients et l'augmentation de l'utilisation. En outre, les nouvelles régions de centre de données permettent d'héberger des données dans la région pour les données client essentielles.

Les données client principales sont un terme qui fait référence à un sous-ensemble de données client, notamment :

- Exchange Online contenu de boîte aux lettres (corps de l’e-mail, entrées de calendrier et contenu des pièces jointes)
- Contenu du site SharePoint Online et fichiers stockés dans ce site
- Fichiers chargés dans OneDrive Entreprise
- Messages de conversation Teams, y compris les messages privés, les messages de canal et les images utilisés dans les conversations
  
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
|**Qatar**| Union européenne | Qatar | Août 2022 |

À compter du 1er octobre 2020, les clients disposant d’un abonnement Office 365 Éducation inclus dans le locataire ne sont pas éligibles à la migration.

La liste complète de l'ensemble des régions de centre de données, des centres de données et l'emplacement des données client au repos est disponible via les [cartes interactives de centre de données](https://office.com/datamaps).
  
## <a name="data-residency-option"></a>Option de résidence des données

Nous fournissons une option de résidence des données aux clients Microsoft 365 éligibles qui sont couverts par les zones géographiques du centre de données répertoriées dans le tableau ci-dessus. Avec cette option, les clients éligibles ayant des exigences de résidence des données peuvent demander la migration des données client principales de leur organisation au repos vers leur nouvelle zone géographique de centre de données.  Microsoft proposera une échéance validée à tous les clients éligibles qui demandent la migration pendant la fenêtre d’inscription.  Consultez la page [Comment demander votre déplacement de données](request-your-data-move.md) pour plus d’informations sur la fenêtre d’inscription ouverte pour la zone géographique de votre centre de données et les étapes à suivre pour vous inscrire au programme.  Les déplacements de données peuvent prendre jusqu'à 24 mois à compter de la fin de la période de demande.

Aucune fonction, fonctionnalité ou certification de conformité unique n'est fournie avec la nouvelle région de centre de données.

The complexity, precision and scale at which we need to perform data moves within a globally operated and automated environment prohibit us from sharing when a data move is expected to complete for your tenant or any other single tenant. Customers will receive one confirmation in Message Center per participating service when its data move has completed.

Data moves are a back-end service operation with minimal impact to end-users. Features that can be impacted are listed on the [During and after your data move](during-and-after-your-data-move.md) page. We adhere to the [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for availability so there is nothing that customers need to prepare for or to monitor during the move. Notification of any service maintenance is done if needed.

Les déplacements de données vers la nouvelle zone géographique du centre de données sont effectués sans coût supplémentaire pour le client.

Pendant le processus de migration, Microsoft copie temporairement vos données de carnet d’adresses dans des ressources globales Microsoft où elles sont chiffrées et utilisées uniquement pour prendre en charge les opérations de continuité d’activité et de récupération d’urgence (BCDR). Une fois que Microsoft a terminé le déplacement des données de boîte aux lettres, Microsoft supprime ces données temporaires des ressources globales. Microsoft continue d’investir régulièrement dans des ressources mondiales et régionales. Au cours de l’année civile 2023, Microsoft prévoit d’utiliser des ressources régionales à des fins bcdr pendant le processus de migration.

## <a name="related-topics"></a>Voir aussi

[Procédure de demande d’un déplacement de données](request-your-data-move.md)

[FAQ général relatif au déplacement de données](data-move-faq.md)
  
[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Services Azure par région](https://azure.microsoft.com/regions/)

[Expérience Teams dans une location multigéographique Microsoft 365](/microsoftteams/teams-experience-o365odb-spo-multi-geo)
