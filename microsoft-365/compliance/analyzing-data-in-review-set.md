---
title: Analyser les données d’un ensemble de vérification dans Advanced eDiscovery
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez les outils disponibles pour organiser des ensembles de documents lors de l’analyse d’un cas avancé eDiscovery.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 7c63e7eca2e032bfa11c4d4e6f961bb7a7700a4e
ms.sourcegitcommit: 98b889e674ad1d5fa37d4b6c5fc3eda60a1d67f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "49751369"
---
# <a name="analyze-data-in-a-review-set-in-advanced-ediscovery"></a>Analyser les données d’un ensemble de vérification dans Advanced eDiscovery

Lorsque le nombre de documents collectés est important, il peut s’avérer difficile de les examiner tous. Advanced eDiscovery fournit un certain nombre d’outils pour analyser les documents afin de réduire le volume des documents à examiner sans perte de données et pour vous aider à organiser les documents de manière cohérente. Pour en savoir plus sur ces fonctionnalités, consultez les éléments suivants :

- [Détecter des quasi-duplicatas](near-duplicate-detection-in-advanced-ediscovery.md)

- [Threading de messagerie](email-threading-in-advanced-ediscovery.md)

- [Thèmes](themes-in-advanced-ediscovery.md)

Pour analyser les données d’un ensemble de révision :

1. Configurez les paramètres d’analyse pour votre cas. Pour plus d’informations, consultez la rubrique [configurer les paramètres de recherche et d’analyse](configure-search-and-analytics-settings-in-advanced-ediscovery.md).

2. Ouvrez l’ensemble de révision à analyser.

3. Cliquez sur **gérer le jeu de révision**.

4. Cliquez sur **exécuter l’analyse pour l’ensemble de révision**.

Vous pouvez vérifier la progression de l’analyse sous l’onglet **tâches** du cas.

 Une fois l’analyse terminée, vous pouvez afficher le rapport d’analyse, exécuter des requêtes dans votre ensemble de révision sur les sorties de l’analyse (voir la rubrique relative à la [recherche dans l’ensemble de révision](review-set-search.md)) et consulter les documents connexes d’un document donné (voir [Review Data in Review Set](reviewing-data-in-review-set.md)).

## <a name="analytics-report"></a>Rapport d’analyse

Pour afficher un rapport d’analyse pour un jeu de révisions :

1. Ouvrez l’ensemble de révision.

2. Cliquez sur **gérer le jeu de révision**.

3. Cliquez sur **afficher le rapport**.

Le rapport comprend sept composants de l’analyse :

- **Population cible :** Le nombre de messages électroniques, de pièces jointes et de documents en vrac trouvés dans l’ensemble de révision.

- **Documents (à l’exception des pièces jointes) :** Nombre de documents en vrac, qui sont des tableaux croisés dynamiques, qui sont des doublons d’un tableau croisé dynamique ou un doublon exact d’un autre document.

- **E-mails :** Nombre de messages électroniques inclus, de copies inclusives, inclusifs ou aucun des.

- **Pièces jointes :** Nombre de pièces jointes qui sont uniques ou des doublons d’une autre pièce jointe dans l’ensemble de révision.

- **Nombre de fichiers par type :** Nombre de fichiers identifiés par extension de fichier.

- **Documents par source :** Résumé du contenu par sa source de données d’origine.

- **Documents agrégés par processus :** Résumé du contenu en revue les processus de jeu. 
