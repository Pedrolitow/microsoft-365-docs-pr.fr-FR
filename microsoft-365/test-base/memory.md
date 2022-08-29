---
title: Analyse de régression de la mémoire
description: Comment déduire la régression de la mémoire
search.appverid: MET150
author: mansipatel-usl
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: test-base
ms.localizationpriority: medium
ms.collection: TestBase-Microsoft 365
ms.custom: ''
ms.reviewer: tinachen
f1.keywords: NOCSH
ms.openlocfilehash: 421fce87bc57f794bdf875e9bc09889bb20b62fb
ms.sourcegitcommit: eb81b49205cbc66b021326b8e2c00a8336b4a2fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67316422"
---
# <a name="memory-regression-analysis"></a>Analyse de la régression de la mémoire

La base de tests vous aide à remarquer plus clairement les augmentations significatives de l’utilisation de la mémoire dans les machines virtuelles de test exécutant vos applications. Les métriques de performances, telles que l’utilisation de la mémoire, peuvent indiquer l’intégrité globale des applications et nous pensons que cet ajout aidera grandement à optimiser les performances de vos applications.

Lisez la suite pour plus d’informations ou regardez cette vidéo pour une présentation rapide des dernières améliorations. 

Pour plus d’informations sur la capacité de Test Base for Microsoft 365 à faciliter l’analyse de régression, consultez les résultats de régression basés sur la fiabilité des processus.

<b>En regardant de plus près les régressions de mémoire</b>

Le tableau de bord Base de test pour Microsoft 365 affiche la mémoire consommée par votre application sur une nouvelle mise à jour Windows préversion et la compare à la mémoire utilisée par la dernière mise à jour Windows publiée. 

Grâce aux améliorations apportées ce mois-ci, l’analyse de régression de la mémoire est désormais proposée dans vos processus favoris. Les applications peuvent contenir plusieurs processus et vous pouvez sélectionner manuellement vos processus favoris sous l’onglet Fiabilité. Notre service identifie ensuite les régressions de mémoire dans ces processus favoris tout en comparant les séries de tests dans différentes versions de mise à jour Windows. Si une régression est détectée, des détails sur la régression sont facilement disponibles.

Examinons maintenant cette fonctionnalité en détail et voyons comment vous pouvez résoudre les problèmes de régression de mémoire à l’aide de Windows Analyseur de performances.

Le signal d’échec provoqué par une régression de la mémoire s’affiche dans le tableau de bord Base de test pour Microsoft 365 dans la page résultats du test sous Utilisation de la mémoire :

![Résultats de l’utilisation de la mémoire.](Media/01_memory-utilization-results.png)


L’échec de l’application en raison d’une consommation de mémoire plus élevée s’affiche également sur ```Fail``` la page Résumé du test :

![Résultats récapitulatifs des tests.](Media/02_test-summary.png)

En fournissant les signaux d’échec à l’avance, notre objectif est de signaler clairement les problèmes potentiels qui peuvent perturber et impacter l’expérience de l’utilisateur final pour votre application. 

Vous pouvez ensuite télécharger les fichiers journaux et utiliser le Analyseur de performances Windows, ou votre kit de ressources préféré, pour approfondir vos recherches. Vous pouvez également collaborer avec l’équipe De base de test pour Microsoft 365 pour résoudre le problème et éviter les problèmes affectant les utilisateurs finaux.

Les signaux de mémoire sont capturés sous l’onglet Utilisation de la mémoire dans le service Base de test pour Microsoft 365 pour toutes les séries de tests. L’exemple ci-dessous montre une exécution de test récente avec l’application intégrée « Contrainte de mémoire du test de fumée » par rapport à la mise à jour de sécurité d’août 2020 en préversion. (Cette application a été écrite par notre équipe pour illustrer les régressions de mémoire.)

![Résultats de la régression de la mémoire.](Media/03_memory-regression%20comparison.png)

Dans cet exemple, le processus favori « USLTestMemoryStress.exe » a consommé une moyenne d’environ 100 Mo lors de la mise à jour d’août en préversion par rapport à la mise à jour publiée de juillet. Par conséquent, la base de test pour Microsoft 365 a identifié une régression. 

Les autres processus, présentés ici comme « USLTestMemoryStress_Aux1.exe » et « USLTestMemoryStress_Aux2.exe », appartiennent également à la même application, mais ont consommé approximativement la même quantité de mémoire pour les deux versions afin qu’elles « passent » et soient considérées comme saines.

La régression sur le processus principal a été déterminée comme étant « statistiquement significative », de sorte que le service a communiqué et mis en évidence cette différence pour l’utilisateur. Si la comparaison n’était pas statistiquement significative, elle ne serait pas mise en surbrillance. L’utilisation de la mémoire peut être bruyante. Nous utilisons donc des modèles statistiques pour distinguer, entre les builds et les versions, des différences significatives entre les différences sans conséquence. 

Une comparaison peut rarement être signalée lorsqu’il n’existe aucune différence réelle (faux positif), mais il s’agit d’un compromis nécessaire pour améliorer la probabilité d’identifier correctement les régressions (ou les vrais positifs).)

L’étape suivante consiste à comprendre ce qui a provoqué la régression de la mémoire. Vous pouvez télécharger les fichiers zip pour les deux exécutions à partir de l’option Télécharger les fichiers journaux, comme indiqué ci-dessous. 

Ces fichiers zip contiennent les résultats de votre série de tests, y compris les résultats du script, la mémoire et les données de performances de l’UC incluses dans le fichier ETL.

![Fichiers de test de régression de la mémoire.](Media/04_memory-regression-test-files.png)

Vous pouvez télécharger et décompresser les journaux des deux séries de tests, puis localiser le fichier ETL dans chaque dossier et les renommer en tant que target.etl (pour le test qui s’exécute sur la mise à jour de préversion) et baseline.etl (pour le test qui s’exécute lors de la dernière mise à jour publiée) pour simplifier l’exploration et la navigation.
 
## <a name="next-steps"></a>Prochaines étapes

Passez à l’article suivant pour commencer à comprendre l’analyse intelligente de la régression du processeur.
> [!div class="nextstepaction"]
> [Étape suivante](cpu.md)

<!---
Add button for next page
-->
