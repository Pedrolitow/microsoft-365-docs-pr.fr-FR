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
description: ''
ms.openlocfilehash: 0f9cb386ce57d6581ade5caa05e029511100d9b3
ms.sourcegitcommit: e741930c41abcde61add22d4b773dbf171ed72ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "42556782"
---
# <a name="analyze-data-in-a-review-set-in-advanced-ediscovery"></a>Analyser les données d’un ensemble de vérification dans Advanced eDiscovery

Lorsque le nombre de documents collectés est important, il peut s’avérer difficile de les examiner tous. Advanced eDiscovery fournit un certain nombre d’outils pour analyser les documents afin de réduire le volume des documents à examiner sans perte de données et pour vous aider à organiser les documents de manière cohérente. Pour en savoir plus sur ces fonctionnalités, consultez les éléments suivants :

- [Détecter des quasi-duplicatas](near-duplicates.md)

- [Threading de messagerie](email-threading.md)

- [Thèmes](themes.md)

Pour analyser les données d’un ensemble de révision :

1. Configurez les paramètres d’analyse pour votre cas. Pour plus d’informations, consultez la rubrique [configurer les paramètres de recherche et d’analyse](configure-search-analytics-settings.md).

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
