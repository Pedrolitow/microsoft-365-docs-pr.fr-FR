---
title: Tester l’analyse de pertinence dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 1b092f7c-ea55-44f5-b419-63f3458fd7e0
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment utiliser l’onglet Test après le calcul par lots dans Advanced eDiscovery pour tester, comparer et valider la qualité globale du traitement.
ms.openlocfilehash: 3ac12c176f2e46ac0321976a7e0689fbd8893bba
ms.sourcegitcommit: 5ba0015c1554048f817fdfdc85359eee1368da64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "49769169"
---
# <a name="test-relevance-analysis-in-advanced-ediscovery"></a>Tester l’analyse de pertinence dans Advanced eDiscovery
  
L’onglet Test Advanced eDiscovery vous permet de tester, comparer et valider la qualité globale du traitement. Ces tests sont effectués après le calcul par lots. En balant les fichiers de la collection, un expert décide de façon finale si chaque fichier balisé est pertinent pour le cas.
  
Dans les scénarios à problème unique ou multiple, les tests sont généralement effectués par problème. Les résultats peuvent être consultables après chaque test, et les résultats des tests peuvent être retravaillés avec des exemples de fichiers de test spécifiés.
  
## <a name="testing-the-rest"></a>Test du reste

Le test « Tester le reste » est utilisé pour valider les décisions d’élimination, par exemple, pour passer en revue uniquement les fichiers au-dessus d’un score de pertinence spécifique en fonction des résultats Advanced eDiscovery finaux. L’expert examine un échantillon de fichiers sous un score de limite sélectionné pour évaluer le nombre de fichiers pertinents dans cet ensemble.
  
Ce test fournit des statistiques et une comparaison entre le jeu à réviser et la population Test du reste. Les résultats du jeu à réviser sont ceux calculés par Pertinence lors de l’entraînement. Les résultats incluent des calculs basés sur des paramètres et des paramètres d’entrée, tels que :
  
- Testez des exemples de statistiques sur le nombre de fichiers dans un exemple et identifiez les fichiers pertinents.

- Comparaison tabulaire des paramètres Population du jeu à réviser et du reste, par exemple, nombre de fichiers, nombre estimé de fichiers pertinents, richesse estimée et coût moyen de recherche d’un autre fichier pertinent. Les paramètres de coût peuvent être définies par l’administrateur.

Pour exécuter le test « Tester le reste » :

1. Ouvrez **l’onglet \> Test de** pertinence.

2. Dans **l’onglet Test,** cliquez **sur Nouveau test.** La **boîte de dialogue** Créer un test s’affiche, comme illustré dans l’exemple suivant.

    ![Résultats de pertinence du test Tester les éléments restants](../media/46e6898a-f929-4fd0-88d9-6f91d04b6ce2.png)
  
3. Dans **Nom du test** et **Description,** tapez le nom et la description.

4. Dans la liste **des types de test,** **sélectionnez Tester le reste**

5. Dans la **liste Problème/Catégorie,** sélectionnez le nom du problème.

6. Dans la **liste Charger,** sélectionnez le chargement. 

7. Dans **% de** lecture, acceptez la valeur par défaut ou sélectionnez une valeur pour le score de pertinence cutoff. 

8. Dans **Définir la taille** ou accepter la valeur par défaut. Les icônes de restauration restaurent les valeurs par défaut.

9. Cliquez **sur Démarrer le marquage.** Un exemple de test est généré.

10. Examinez et marquez chacun des fichiers dans l’onglet **Balise \>** de pertinence et, lorsque vous avez terminé, cliquez sur **Calculer**.

11. Dans l’onglet Test, vous pouvez cliquer sur **Afficher les résultats** pour afficher les résultats du test. Un exemple est illustré dans la capture d’écran suivante.

    ![Résultats du test Tester les éléments restants](../media/b95744a9-047d-4c29-992d-04fa7e58e58a.png)
  
Dans la capture d’écran précédente, la section Exemples de **paramètres** du tableau contient des détails sur le nombre de fichiers dans l’exemple balisé par l’expert et le nombre de fichiers pertinents trouvés dans cet exemple.
  
La section **Paramètres** de population du tableau contient les résultats des tests, y compris la population de fichiers du jeu à réviser avec un score inférieur au seuil sélectionné et la population de fichiers « Le reste » avec un score au-dessus du seuil sélectionné. Pour chaque population, les résultats suivants sont affichés :
  
- Inclut les fichiers avec % de lecture - Cutoff indiqué

- Nombre total de fichiers

- Le nombre estimé de fichiers pertinents

- Richesse estimée

- Coût moyen d’examen de la recherche d’un autre fichier pertinent

## <a name="testing-the-slice"></a>Test de la tranche

Le test « Tester la tranche » effectue des tests similaires au test « Tester le reste », mais à un segment du jeu de fichiers tel que spécifié par Pertinence lecture %.

Pour exécuter le test « Tester le slice » :
  
1. Ouvrez **l’onglet \> Test de** pertinence.

2. Dans **l’onglet Test,** cliquez **sur Nouveau test.** La **boîte de dialogue Créer** un test s’affiche.

3. Dans **Nom du test** et **Description,** tapez les informations.

4. Dans la **liste des types de test,** **sélectionnez Tester le slice.**

5. Dans la **liste Problèmes,** sélectionnez le nom du problème.

6. Dans la **liste Charger,** sélectionnez le chargement.

7. Dans **Lire le % entre**, acceptez les valeurs de plage basse et élevée par défaut ou sélectionnez des valeurs pour les scores de pertinence à couper.

8. Dans **Définir la taille,** sélectionnez une valeur ou acceptez la valeur par défaut.

    Les icônes de restauration restaurent la valeur par défaut.

9. Cliquez **sur Démarrer le marquage.** Un exemple de test est généré.

10. Examinez et marquez chacun des fichiers dans l’onglet **Balise \>** de pertinence et, lorsque vous avez terminé, cliquez sur **Calculer**.

11. Dans l’onglet Test, vous pouvez cliquer sur **Afficher les résultats** pour afficher les résultats du test.
