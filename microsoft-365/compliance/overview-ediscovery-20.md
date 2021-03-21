---
title: Vue d’ensemble de la solution Advanced eDiscovery dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- m365-security-compliance
- m365solution-aed
- m365initiative-compliance
- m365solution-overview
search.appverid:
- MOE150
- MET150
description: Découvrez la solution Advanced eDiscovery dans Microsoft 365. Cet article fournit une vue d’ensemble d’Advanced eDiscovery dans Microsoft 365, un outil qui vous aide à gérer les enquêtes internes et externes. Il encadre également les raisons professionnelles de l’utilisation d’Advanced eDiscovery pour gérer vos enquêtes juridiques.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0f6ae536f84190f81248bbf68ff66f438727e068
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50927648"
---
# <a name="overview-of-microsoft-365-advanced-ediscovery"></a>Vue d’ensemble de Microsoft 365 Advanced eDiscovery

La solution Advanced eDiscovery dans Microsoft 365 s’appuie sur les fonctionnalités eDiscovery et d’analyse de Microsoft existantes. Advanced eDiscovery fournit un flux de travail de bout en bout pour conserver, collecter, analyser, examiner, analyser et exporter du contenu qui répond aux enquêtes internes et externes de votre organisation. Il permet également aux équipes juridiques de gérer l’ensemble du flux de travail de notification de conservation légale pour communiquer avec les dépositaires impliqués dans un cas.

## <a name="advanced-ediscovery-capabilities"></a>Fonctionnalités eDiscovery avancées

Advanced eDiscovery peut aider votre organisation à répondre à des questions juridiques ou à des enquêtes internes en découvrant les données où elle se trouve. Vous pouvez gérer en toute transparence les flux de travail eDiscovery en identifiant les personnes d’intérêt et leurs sources de données, en appliquant en toute transparence des conservations pour conserver les données, puis en gérant le processus de communication de conservation légale. En collectant des données à partir de la source, vous pouvez effectuer des recherches sur la plateforme Microsoft 365 en direct pour trouver rapidement ce dont vous avez besoin. Les fonctionnalités intelligentes d’apprentissage automatique telles que l’indexation approfondie, le thread de courrier électronique et la détection de quasi-doublons vous aident également à réduire les volumes importants de données dans un jeu de données pertinent.

Les sections suivantes décrivent comment ces fonctionnalités Advanced eDiscovery peuvent aider votre organisation.

![Fonctionnalités eDiscovery avancées](../media/advanced-ediscovery-capabilities.png)

### <a name="discover-and-collect-data-in-place"></a>Découvrir et collecter des données sur place

En général, les organisations qui s’appuient sur plusieurs solutions eDiscovery tierces nécessitent la copie de grands volumes de données de Microsoft 365 pour traiter et avoir à héberger des données en double. Cette nécessité augmente le temps nécessaire pour trouver des données pertinentes, ainsi que les risques, les coûts et la complexité de la gestion de plusieurs solutions.

Advanced eDiscovery dans Microsoft 365 vous permet de découvrir les données à la source et de rester dans vos limites de sécurité et de conformité Microsoft 365.  En collectant des données sur place à partir du système en direct, Advanced eDiscovery réduit la friction de revenir à la source et réduit le travail inutile d’avoir à trouver le contenu manquant, ce qui se produit souvent lorsque la journaling est en retard dans les solutions eDiscovery traditionnelles.

Les fonctionnalités de recherche et de collecte natives pour les données dans Teams, Yammer, SharePoint Online, OneDrive Entreprise et Exchange Online améliorent davantage la découverte des données. Par exemple, Advanced eDiscovery :

- Reconstruit les conversations Teams (au lieu de renvoyer des messages individuels à partir de conversations).

- Collecte le contenu basé sur le cloud partagé avec les utilisateurs à l’utilisation de liens ou de pièces jointes modernes dans les messages électroniques et les conversations Teams.

- Offre une prise en charge intégrée de centaines de types de fichiers non-Microsoft 365.

- Collecte des données à partir de sources tierces (comme Bloomberg, Facebook, Slack et Zoom Meetings) importées et archivées dans Microsoft 365 par des connecteurs de [données.](archiving-third-party-data.md)

### <a name="manage-ediscovery-workflow-in-one-platform"></a>Gérer le flux de travail eDiscovery dans une plateforme

Advanced eDiscovery peut vous aider à réduire le nombre de solutions eDiscovery dont vous avez besoin. Il fournit un flux de travail simplifié de bout en bout, qui se produit tous dans Microsoft 365. Advanced eDiscovery permet de réduire les points de friction entre l’identification et la collecte des sources potentielles d’informations pertinentes en m mappage automatique des sources de données uniques et partagées avec la personne d’intérêt (appelée *dépositaire),* et en fournissant des rapports et des analyses sur les données potentiellement pertinentes avant de les collecter pour analyse et révision.

En outre, les API Microsoft Graph peuvent vous aider à automatiser le flux de travail eDiscovery et à étendre Advanced eDiscovery pour les solutions personnalisées.

### <a name="cull-data-intelligently"></a>Annuler les données de manière intelligente

Les fonctionnalités intelligentes d’apprentissage automatique dans Advanced eDiscovery vous aident à réduire la quantité de données à réviser. Ces fonctionnalités intelligentes vous aident à réduire et à réduire les volumes de données importants vers un ensemble pertinent. Par exemple, une requête d’ensemble de révision intégrée permet de filtrer uniquement le contenu unique en identifiant les quasi-doublons. Cette fonctionnalité peut considérablement réduire la quantité de données à réviser.

D’autres fonctionnalités d’apprentissage automatique peuvent affiner et identifier les données pertinentes à l’aide de balises intelligentes et d’outils d’examen avec assistance technologique tels que les modules de pertinence.

## <a name="advanced-ediscovery-alignment-with-the-electronic-discovery-reference-model"></a>Alignement advanced eDiscovery avec le modèle de référence de découverte électronique

Le flux de travail intégré d’Advanced eDiscovery dans Microsoft 365 s’aligne sur le processus eDiscovery décrit par le modèle de référence de découverte électronique (EDRM).

![Modèle de référence de découverte électronique (EDRM)](../media/EDRMv1.png)

(Image source fournie par edrm.net. L’image source a été rendue disponible sous Creative Commons Attribution 3.0 Unported License.)

À un niveau élevé, voici comment Advanced eDiscovery prend en charge le flux de travail EDRM :

- **Identification.** Après avoir identifié les personnes potentielles concernées par une enquête, vous pouvez les ajouter en tant que dépositaires (également *appelés dépositaires* de données, car elles peuvent détenir des informations pertinentes pour l’enquête) à un cas Advanced eDiscovery. Une fois que les utilisateurs sont ajoutés en tant que dépositaires, il est facile de conserver, de collecter et de réviser les documents des dépositaires.

- **Conservation.** Pour conserver et protéger les données pertinentes pour un examen, Advanced eDiscovery vous permet de placer une conservation légale sur les sources de données associées aux dépositaires dans un cas. Vous pouvez également placer en attente les données non privatives. Advanced eDiscovery dispose également d’un flux de travail de communications intégré qui vous permet d’envoyer des notifications de conservation légale aux dépositaires et de suivre leurs accusés de réception.

- **Collection.** Une fois que vous avez identifié (et conservé) les sources de données pertinentes pour l’examen, vous pouvez utiliser l’outil de recherche intégré dans advanced eDiscovery pour rechercher et collecter des données en direct à partir des sources de données privatives (et des sources de données non privatives, le cas échéant) qui peuvent être pertinentes pour le cas.

- **Traitement.** Une fois que vous avez collecté toutes les données pertinentes pour le cas, l’étape suivante consiste à les traiter pour une analyse et un examen approfondis. Dans Advanced eDiscovery, les données sur place que vous avez identifiées lors de la phase de collecte sont copiées dans un emplacement de stockage Azure (appelé ensemble de *révision),* ce qui vous fournit une vue statique des données de cas. 

- **Révision.** Une fois que les données ont été ajoutées à un jeu à réviser, vous pouvez afficher des documents spécifiques et exécuter des requêtes supplémentaires pour réduire les données à ce qui est le plus pertinent pour le cas. Peut également annoter et marquer des documents spécifiques.

- **Analyse.** Advanced eDiscovery fournit un outil d’analyse intégré qui vous permet d’annuler davantage les données du jeu à réviser que vous déterminez ne sont pas pertinentes pour l’examen. En plus de réduire le volume de données pertinentes, Advance eDiscovery vous permet également d’économiser des coûts de révision juridique en vous permettant d’organiser le contenu afin de simplifier et d’améliorer l’efficacité du processus de révision.

- **Production** et **présentation.** Lorsque vous êtes prêt, vous pouvez exporter des documents à partir d’un groupe de révision pour révision légale. Vous pouvez exporter des documents dans leur format natif ou dans un format EDRM spécifié afin qu’ils soient importés dans des applications de révision tierces.

## <a name="subscriptions-and-licensing"></a>Abonnements et licences

La gestion des licences pour Advanced eDiscovery nécessite l’abonnement d’organisation et la licence par utilisateur appropriés.

- **Abonnement à l’organisation :** Pour accéder à Advanced eDiscovery dans le Centre de conformité Microsoft 365, votre organisation doit avoir l’une des fonctionnalités suivantes :

  - Abonnement Microsoft 365 E5 ou Office 365 E5
  
  - Abonnement Microsoft 365 E3 avec le module complémentaire E5 conformité

  - Abonnement Microsoft 365 E3 avec E5 eDiscovery et module d’audit

  Si vous n’avez pas de plan Microsoft 365 E5 et que vous souhaitez essayer Advanced eDiscovery, vous pouvez ajouter [Microsoft 365](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou vous inscrire à une version d’essai de Microsoft 365 E5. [](https://www.microsoft.com/microsoft-365/enterprise)

- **Licences par utilisateur :** Pour ajouter un utilisateur en tant que dépositaire dans un cas advance eDiscovery, cet utilisateur doit se voir attribuer l’une des licences suivantes, en fonction de l’abonnement de votre organisation :

  - Microsoft 365 : une licence Microsoft 365 E5, une licence de module de conformité E5 ou une licence de modules de découverte électronique et d’audit E5 doivent être attribuées aux utilisateurs.

  - Office 365 : une licence Office 365 E5 doit être attribuée aux utilisateurs.

   Pour plus d’informations sur l’attribution de licences, voir [Attribuer des licences aux utilisateurs.](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)

> [!NOTE]
> Les utilisateurs ont uniquement besoin d’une licence E5 (ou de la licence de module supplémentaire appropriée) pour être ajoutés en tant que dépositaires à un cas Advanced eDiscovery. Les administrateurs informatiques, les gestionnaires eDiscovery, les avocats, les techniciens juridiques ou les enquêteurs qui utilisent Advanced eDiscovery pour gérer les cas et examiner les données de cas n’ont pas besoin d’une licence E5 ou de modules add-on.

## <a name="get-started-with-advanced-ediscovery"></a>Prise en main Advanced eDiscovery

Il existe deux étapes rapides et simples pour commencer à utiliser Advanced eDiscovery.

![Flux de travail de mise en place avec Advanced eDiscovery](../media/get-started-AeD.png)

|Étapes  |Description  |
|:---------|:---------|
|[Configurer Advanced eDiscovery](get-started-with-advanced-ediscovery.md)| Après avoir vérifié les exigences d’abonnement et de licence, vous pouvez attribuer des autorisations et configurer les paramètres à l’échelle de l’organisation pour commencer à utiliser Advanced eDiscovery.|
|[Créer et gérer des cas](create-and-manage-advanced-ediscoveryv2-case.md) | Créez des cas pour gérer le flux de travail Advanced eDiscovery pour tous les types d’enquêtes juridiques et autres dans votre organisation.|
|||

## <a name="advanced-ediscovery-architecture"></a>Architecture eDiscovery avancée

Voici un diagramme d’architecture Advanced eDiscovery qui montre le flux de travail de bout en bout dans un environnement à une seule géo et dans un environnement multigé géographique, ainsi que le flux de données de bout en bout aligné sur la gestion des données [EDRM.](#advanced-ediscovery-alignment-with-the-electronic-discovery-reference-model)

[![Affiche de modèle : Architecture eDiscovery avancée dans Microsoft 365](../media/solutions-architecture-center/ediscovery-poster-thumb.png)](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Afficher en tant qu’image](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Télécharger en tant que fichier PDF](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.pdf)

[Télécharger en tant que fichier Visio](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.vsdx)
