---
title: Analyser les données d’un jeu à réviser dans Advanced eDiscovery
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
description: Découvrez les outils disponibles pour organiser les ensembles de documents lors de l’analyse Advanced eDiscovery cas.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 332c467ed6d178d6d8252cdd337a9b23384d88790729e3923eb0cafae981cd82
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53843106"
---
# <a name="analyze-data-in-a-review-set-in-advanced-ediscovery"></a>Analyser les données d’un jeu à réviser dans Advanced eDiscovery

Lorsque le nombre de documents collectés est élevé, il peut être difficile de les examiner tous. Advanced eDiscovery fournit un certain nombre d’outils pour analyser les documents afin de réduire le volume de documents à examiner sans perte d’informations et pour vous aider à organiser les documents de manière cohérente. Pour en savoir plus sur ces fonctionnalités, voir :

- [Détecter des quasi-duplicatas](near-duplicate-detection-in-advanced-ediscovery.md)

- [Threading de messagerie](email-threading-in-advanced-ediscovery.md)

- [Thèmes](themes-in-advanced-ediscovery.md)

Pour analyser les données d’un jeu à réviser :

1. Configurez les paramètres d’analyse pour votre cas. Pour plus d’informations, voir Configurer les paramètres de recherche [et d’analyse.](configure-search-and-analytics-settings-in-advanced-ediscovery.md)

2. Ouvrez le jeu à réviser que vous souhaitez analyser.

3. Cliquez sur **Gérer le jeu à réviser.**

4. Cliquez **sur Exécuter l’analyse pour le jeu à réviser.**

Vous pouvez vérifier la progression de l’analyse sous **l’onglet Travaux** du cas.

 Une fois l’analyse terminée, vous pouvez afficher le rapport d’analyse, exécuter des requêtes dans votre jeu à réviser sur les sorties de l’analyse (voir Requête dans votre jeu à [réviser)](review-set-search.md)et voir les documents associés d’un document donné (voir Données de révision dans le jeu à [réviser).](reviewing-data-in-review-set.md)

## <a name="analytics-report"></a>Rapport d’analyse

Pour afficher un rapport d’analyse pour un jeu à réviser :

1. Ouvrez le jeu à réviser.

2. Cliquez sur **Gérer le jeu à réviser.**

3. Cliquez **sur Afficher le rapport.**

Le rapport possède sept composants issus de l’analyse :

- **Population cible :** Nombre de messages électroniques, pièces jointes et documents libres trouvés dans le jeu à réviser.

- **Documents (à l’exclusion des pièces jointes) :** Nombre de documents libres qui sont des tableaux croisés dynamiques, des doublons proches uniques d’un tableau croisé dynamique ou un doublon exact d’un autre document.

- **E-mails :** Nombre de messages électroniques inclus, copies incluses, moinss inclus ou aucun des messages ci-dessus.

- **Pièces jointes :** Nombre de pièces jointes qui sont uniques ou dupliquées d’une autre pièce jointe dans le jeu à réviser.

- **Nombre de fichiers par type :** Nombre de fichiers, identifié par l’extension de fichier.

- **Documents par source :** Résumé du contenu par sa source de données d’origine.

- **Documents agrégés par processus :** Résumé du contenu par processus d’ensemble de révision. 
