---
title: Vue d’ensemble de la solution avancée eDiscovery dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-aed
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Cet article fournit une vue d’ensemble de Advanced eDiscovery dans Microsoft 365, un outil destiné aux investigations internes et externes.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6225411bcd3051c19e22fcb205cc7dee92f99f82
ms.sourcegitcommit: ce46d1bd67091d4ed0e2b776dfed55e2d88cdbf4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "49131027"
---
# <a name="overview-of-the-advanced-ediscovery-solution-in-microsoft-365"></a>Vue d’ensemble de la solution avancée eDiscovery dans Microsoft 365

La solution eDiscovery avancée de Microsoft 365 repose sur les fonctionnalités d’analyse et de découverte électronique existantes dans Office 365. Cette nouvelle solution, appelée *Advanced eDiscovery*, fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter du contenu réactif aux investigations internes et externes de votre organisation. Il permet également aux équipes juridiques de gérer l’ensemble du flux de travail de notification de suspension légale pour communiquer avec les dépositaires impliqués dans un cas. 

> [!NOTE]
> Advanced eDiscovery nécessite un abonnement Office 365 ou Microsoft 365 E5 Enterprise. Pour plus d’informations sur la gestion des licences eDiscovery avancée, consultez [la rubrique Microsoft 365 Licensing Guidance for security & Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#advanced-ediscovery).

## <a name="alignment-with-edrm"></a>Alignement avec EDRM

Le flux de travail intégré de Advanced eDiscovery s’aligne sur le processus eDiscovery décrit par le modèle de référence de découverte électronique (EDRM). 

![Modèle de référence de découverte électronique (EDRM)](../media/EDRMv1.png)

(Image source courtoisie de edrm.net. L’image source a été mise à disposition sous la licence non à l’attribution 3,0 Creative.

À un niveau élevé, voici comment Advanced eDiscovery prend en charge le flux de travail EDRM :

- **Identificateur.** Une fois que vous avez identifié les personnes intéressantes pour une enquête, vous pouvez les ajouter en tant que dépositaires (également appelés « *dépositaires de données*», car ils peuvent posséder des informations pertinentes pour l’enquête) dans un cas avancé de découverte électronique. Après avoir identifié les dépositaires et les avoir ajoutés à un cas, vous pouvez facilement conserver, collecter, examiner et analyser les données privatives de Troie associées.

- **Leur.** Pour conserver et protéger les données correspondant à une enquête, la fonctionnalité eDiscovery avancée vous permet de placer une suspension légale sur les sources de données associées aux dépositaires dans un cas. Vous pouvez également placer des données non privatives de stock (généralement des ressources de groupe partagé telles que des sites SharePoint ou des canaux teams partagés). Advanced eDiscovery comprend également un flux de travail de communication intégré qui vous permet d’envoyer des notifications de conservation légale aux dépositaires et d’effectuer le suivi de leurs remerciements.

- **Collection.** Une fois que vous avez identifié (et éventuellement préservé) les sources de données pertinentes pour l’enquête, vous pouvez utiliser l’outil de recherche intégré dans Advanced eDiscovery pour rechercher et collecter des données en direct à partir de sources de données privatives (et, le cas échéant, de sources de données non privatives de temps) susceptibles de s’appliquer.

- **Formation.** Une fois que vous avez collecté toutes les données pertinentes pour le cas, l’étape suivante consiste à le traiter pour révision et analyse. Dans Advanced eDiscovery, les données sur place que vous avez identifiées dans la phase de collecte sont copiées vers un emplacement de stockage Azure (appelé *ensemble de révision*), qui fournit une vue statique des données de cas.

- **Veuillez.** Une fois que les données ont été ajoutées à un jeu de révisions, vous pouvez afficher des documents spécifiques et exécuter des requêtes supplémentaires au sein de l’ensemble de révision pour réduire les données aux documents les plus pertinents. Vous pouvez également annoter et baliser des documents spécifiques.

- **Analys.** Advanced eDiscovery fournit un ensemble puissant d’outils d’analyse intégrés qui vous permettent de mettre en suspens intelligemment les données non pertinentes du jeu de révision, ce qui vous permet de réduire efficacement le volume des données pertinentes pour la production.

- **Production** et **présentation.** Lorsque vous êtes prêt, vous pouvez exporter des documents à partir d’un jeu de révision pour vérification légale. Vous pouvez exporter des documents dans leur format spécifié par EDRM afin qu’ils puissent être importés dans des applications de révision tierces.

## <a name="advanced-ediscovery-architecture"></a>Architecture eDiscovery avancée

Voici un diagramme d’architecture eDiscovery avancé qui montre le flux de travail de bout en bout dans un environnement géographique unique et un environnement multi-géo. Le flux de données de bout en bout est aligné sur le EDRM.

[![Affiche de modèle : architecture eDiscovery avancée dans Microsoft 365](../media/solutions-architecture-center/ediscovery-poster-thumb.png)](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Afficher sous forme d’image](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Télécharger en tant que fichier PDF](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.pdf)

[Télécharger en tant que fichier Visio](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.vsdx)

Pour plus d’informations sur le flux de travail de bout en bout dans Advanced eDiscovery, reportez-vous à cette [vidéo de mécanique Microsoft](https://go.microsoft.com/fwlink/?linkid=2066133).

Les sections qui suivent décrivent chaque étape du flux de travail intégré dans Advanced eDiscovery. La capture d’écran suivante présente l’onglet **vue d’ensemble** d’un cas nommé *2020.11.03-contoso v. fabrikam*.

![Onglets dans le flux de travail eDiscovery avancé intégré](../media/AeD-Case-Screenshot1.png)

## <a name="managing-custodians-and-non-custodial-data-sources"></a>Gestion des dépositaires et des sources de données non privatives de cœur

Utilisez l’onglet **sources de données** pour ajouter et gérer les personnes que vous avez identifiées comme des personnes intéressantes dans le cas et d’autres sources de données qui ne peuvent pas être associées à un dépositaire. Lorsque vous ajoutez des dépositaires ou des sources de données non privatives de temps, vous pouvez effectuer rapidement des actions telles que le placement d’une conservation légale sur des dépositaires et des sources de données non-privatives, la communication avec des dépositaires et la recherche de dépositaires et de sources de données non privatives pour collecter du contenu pertinent pour le cas. Au fur et à mesure de la progression, il est facile d’ajouter de nouveaux dépositaires ou des sources de données non privatives ou de les diffuser à partir du cas. Pour plus d’informations, consultez la rubrique [utiliser des dépositaires dans Advanced eDiscovery](managing-custodians.md).

## <a name="managing-legal-hold-notifications"></a>Gestion des notifications de conservation légale

Utilisez l’onglet **communications** pour gérer le processus de communication avec les dépositaires dans le cas. Une notice légale indique aux dépositaires de conserver tout contenu pertinent pour le cas. Les équipes juridiques doivent suivre les notifications reçues, lues et reconnues par les dépositaires. Le flux de travail de communication dans Advanced eDiscovery vous permet de créer et d’envoyer des notifications initiales, des rappels, des notifications de publication et des escalades si les dépositaires ne reconnaissent pas une notification de blocage. Pour plus d’informations, consultez la rubrique [utilisation des communications dans Advanced eDiscovery](managing-custodian-communications.md).

## <a name="managing-content-preservation"></a>Gestion de la conservation du contenu

Lorsque vous ajoutez un dépositaire à un cas, vous pouvez placer un blocage sur des données privatives. Utilisez l’onglet **blocage** pour gérer le blocage créé lorsque vous ajoutez des dépositaires et gérez les autres conservations légales associées au cas ; par exemple, vous pouvez identifier et placer une conservation sur des sources de données non privatives de cœur. Vous pouvez également modifier n’importe quelle conservation dans le cas et en faire une conservation basée sur une requête pour conserver uniquement le contenu qui correspond à la requête. Par exemple, vous pouvez ajouter une plage de dates à la suspension afin que seul le contenu créé dans une date spécifique soit dans l’intervalle préservé. Vous pouvez également obtenir des statistiques sur le contenu en attente, supprimer la conservation une fois qu’elle n’est plus pertinente pour le cas ou la supprimer. Pour plus d’informations, consultez la rubrique Manage holds [in Advanced eDiscovery](managing-holds.md).

## <a name="indexing-custodian-data"></a>Indexation des données des dépositaires

Lorsque vous ajoutez un dépositaire et les sources de données privatives de Troie correspondantes à un cas, tout élément partiellement indexé d’une source de données de dépositaire est réindexé par un processus appelé *indexation avancée*. Cela permet à un contenu privative de formes, comme des images, des types de fichiers non pris en charge et d’autres contenus potentiellement non indexés, d’être entièrement consultable lorsque vous exécutez des recherches pour collecter des données pour le cas. Utilisez l’onglet **traitement** pour surveiller l’état des erreurs d’indexation et de traitement avancées à l’aide d’un processus appelé correction des *Erreurs*. Pour plus d’informations, voir [corriger les erreurs de traitement dans Advanced eDiscovery](processing-data-for-case.md).

## <a name="collecting-case-data"></a>Collecte des données d’un cas

L’onglet **recherches** permet de créer des recherches pour effectuer des recherches dans les sources de données privatives de Troie et non-privatives de place pour le contenu pertinent pour le cas. Vous pouvez créer et exécuter des recherches basées sur des requêtes (à l’aide de mots clés et de conditions) pour identifier un ensemble de messages électroniques et de documents pertinents pour le cas et que vous souhaitez examiner et analyser dans les étapes suivantes dans le flux de travail de découverte électronique. Vous pouvez créer une ou plusieurs recherches associées au cas. Vous pouvez également utiliser l’outil de recherche pour afficher un aperçu des exemples de documents et afficher des statistiques de recherche pour vous aider à affiner et à améliorer les résultats de la recherche. Une fois que vous avez effectué une recherche et collecté toutes les données pertinentes pour le cas, vous pouvez ajouter les résultats de la recherche à un jeu de révision pour une révision, une analyse et une élimination ultérieures. Pour plus d’informations, reportez-vous à [la rubrique collecte de données pour un cas dans Advanced eDiscovery](collecting-data-for-ediscovery.md).

## <a name="reviewing-and-analyzing-case-data"></a>Révision et analyse des données de cas

Utilisez l’onglet **réviser les ensembles** pour examiner et analyser le contenu que vous avez collecté dans le système réel et ajouté à un jeu de révision. Un *ensemble de révision* est une collection statique de ces données (en d’autres termes, une copie hors connexion) de données privatives (et, le cas échéant, de données non privatives) que vous avez collectées au cours de la phase précédente du flux de travail de découverte électronique. Lorsque vous ajoutez des résultats de recherche à un jeu de réviseurs, un processus est déclenché pour extraire des fichiers des conteneurs, extraire des métadonnées et extraire du texte. Une fois le processus terminé, le système génère un nouvel index de toutes les données collectées auprès des dépositaires et les ajoute à l’ensemble de révision. Une fois que les données sont ajoutées à l’ensemble de vérification, vous pouvez exécuter davantage de requêtes pour affiner les données de cas, afficher les données au format texte ou au format de fichier natif, et annoter, biffer et baliser les documents dans l’ensemble de révision. Vous pouvez également effectuer des analyses avancées, telles que l’identification de la duplication de documents, le Threading de messagerie électronique et les thèmes. Une fois que vous avez consulté les données uniquement sur ce qui est pertinent pour le cas, vous pouvez télécharger les documents directement ou les exporter, ainsi que les métadonnées de fichier, les annotations et les balises. Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Afficher les documents d’un jeu à réviser](view-documents-in-review-set.md)

- [Interroger les données d’un jeu à réviser](review-set-search.md)

- [Étiqueter les documents d’un jeu à réviser](tagging-documents.md)

- [Analyser les données d’un ensemble de révision](analyzing-data-in-review-set.md)

## <a name="exporting-data-for-review-and-presentation"></a>Exportation de données à des fins de révision et de présentation

Une fois que vous avez exporté les données à partir d’un jeu de révision, utilisez l’onglet **exportations** pour gérer une tâche d’exportation et télécharger des données à partir d’un jeu de révision. Lorsque vous exportez un jeu de révision, les données sont téléchargées vers un emplacement de stockage Azure fourni par Microsoft (ou un emplacement de stockage Azure géré par votre organisation). Une fois qu’il est téléchargé vers Azure, il est ensuite disponible pour téléchargement sur un ordinateur local. Vous pouvez obtenir la clé d’accès au stockage nécessaire pour télécharger les données exportées dans l’onglet **exportations** . Pour plus d’informations, consultez la rubrique [Export case Data in Advanced eDiscovery](exporting-data-ediscover20.md).

## <a name="managing-jobs"></a>Gestion des travaux

Utilisez l’onglet **travaux** pour surveiller les processus de longue durée pour les tâches liées à la casse que vous avez lancées. Exemples de travaux : ceux liés à la réindexation, à la recherche et à l’exportation des données de cas. Par exemple, si vous créez une recherche dans l’onglet **recherches** qui inclut de nombreuses sources de données, l’état de ce processus de recherche s’affiche sous l’onglet **travaux** . Pour plus d’informations, consultez la rubrique [gestion des travaux dans Advanced eDiscovery](managing-jobs-ediscovery20.md).

## <a name="configuring-case-settings"></a>Configuration des paramètres de cas

Utilisez l’onglet **paramètres** pour configurer les paramètres à l’échelle de l’incident. Cela inclut l’ajout de membres à un cas, la fermeture ou la suppression d’un cas et la configuration des paramètres de recherche et d’analyse.
