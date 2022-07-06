---
title: Tester l’analyse de pertinence dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 1b092f7c-ea55-44f5-b419-63f3458fd7e0
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment utiliser l’onglet Test après le calcul Batch dans eDiscovery (Premium) pour tester, comparer et valider la qualité globale du traitement.
ms.openlocfilehash: 5c1fabf677dd305fb91d77e94af0e18304280d45
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637040"
---
# <a name="test-relevance-analysis-in-ediscovery-premium"></a>Tester l’analyse de pertinence dans eDiscovery (Premium)
  
L’onglet Test de Microsoft Purview eDiscovery (Premium) vous permet de tester, comparer et valider la qualité globale du traitement. Ces tests sont effectués après le calcul Batch. En étiquetant les fichiers de la collection, un expert rend le jugement final sur la pertinence de chaque fichier étiqueté pour l’affaire.
  
Dans les scénarios à un ou plusieurs problèmes, les tests sont généralement effectués par problème. Les résultats peuvent être affichés après chaque test, et les résultats des tests peuvent être retravaillés avec des exemples de fichiers de test spécifiés.
  
## <a name="testing-the-rest"></a>Test du reste

Le test « Tester le reste » est utilisé pour valider les décisions d’élimination, par exemple, pour passer en revue uniquement les fichiers au-dessus d’un score de seuil de pertinence spécifique en fonction des résultats finaux de la découverte électronique (Premium). L’expert examine un exemple de fichiers sous un score de seuil sélectionné pour évaluer le nombre de fichiers pertinents au sein de cet ensemble.
  
Ce test fournit des statistiques et une comparaison entre l’ensemble de révisions et la population Test the Rest. Les résultats de l’ensemble d’examens sont ceux calculés par pertinence pendant l’entraînement. Les résultats incluent des calculs basés sur des paramètres et des paramètres d’entrée, tels que :
  
- Testez les exemples de statistiques du nombre de fichiers dans un exemple et identifiez les fichiers pertinents.

- Comparaison tabulaire des paramètres Population de l’ensemble de révision et du reste, par exemple, le nombre de fichiers, le nombre estimé de fichiers pertinents, la richesse estimée et le coût moyen de recherche d’un autre fichier pertinent. Les paramètres de coût peuvent être définis par l’administrateur.

Pour exécuter le test « Tester le reste » :

1. Ouvrez l’onglet **Test de pertinence\>**.

2. Sous l’onglet **Test** , cliquez sur **Nouveau test**. La boîte de **dialogue Créer un test** s’affiche, comme illustré dans l’exemple suivant.

    ![Pertinence Testez les résultats rest.](../media/46e6898a-f929-4fd0-88d9-6f91d04b6ce2.png)
  
3. Dans **Le nom du test** et **la description**, tapez le nom et la description.

4. Dans la liste **des types de tests** , sélectionnez **Tester le reste**

5. Dans la liste **Problème/Catégorie** , sélectionnez le nom du problème.

6. Dans la liste **de chargement** , sélectionnez la charge. 

7. En **lecture %**, acceptez la valeur par défaut ou sélectionnez une valeur pour le score de pertinence de coupure. 

8. Dans **Définir la taille**, ou accepter la valeur par défaut. Les icônes de restauration restaurent les valeurs par défaut.

9. Cliquez sur **Démarrer le balisage**. Un exemple de test est généré.

10. Passez en revue et étiquetez chacun des fichiers sous l’onglet **Balise de pertinence \>** et, une fois terminé, cliquez sur **Calculer**.

11. Sous l’onglet Test, vous pouvez cliquer sur **Afficher les résultats** pour afficher les résultats du test. Un exemple est illustré dans la capture d’écran suivante.

    ![Testez les autres résultats.](../media/b95744a9-047d-4c29-992d-04fa7e58e58a.png)
  
Dans la capture d’écran précédente, la section **Exemples de paramètres** de la table contient des détails sur le nombre de fichiers dans l’exemple balisé par l’expert et le nombre de fichiers pertinents trouvés dans cet exemple.
  
La section **Paramètres** de remplissage de la table contient les résultats des tests, y compris le remplissage de l’ensemble de révisions de fichiers dont le score est inférieur au seuil sélectionné et la population « Le reste » des fichiers dont le score est supérieur au seuil sélectionné. Pour chaque population, les résultats suivants s’affichent :
  
- Inclut des fichiers avec le pourcentage de lecture - Seuil indiqué

- Nombre total de fichiers

- Nombre estimé de fichiers pertinents

- La richesse estimée

- Coût moyen de révision de la recherche d’un autre fichier pertinent

## <a name="testing-the-slice"></a>Test de la tranche

Le test « Tester la tranche » effectue des tests similaires au test « Tester le reste », mais à un segment du jeu de fichiers tel que spécifié par Relevance Read %.

Pour exécuter le test « Tester la tranche » :
  
1. Ouvrez l’onglet **Test de pertinence\>**.

2. Sous l’onglet **Test** , cliquez sur **Nouveau test**. La boîte de **dialogue Créer un test** s’affiche.

3. Dans **Le nom** et **la description** du test, tapez les informations.

4. Dans la liste **des types de tests** , sélectionnez **Tester la tranche**.

5. Dans la liste **Des problèmes** , sélectionnez le nom du problème.

6. Dans la liste **de chargement** , sélectionnez la charge.

7. Dans **Read % between**, acceptez les valeurs de plage basse et élevée par défaut ou sélectionnez des valeurs pour les scores de pertinence de seuil.

8. Dans **Définir la taille**, sélectionnez une valeur ou acceptez la valeur par défaut.

    Les icônes de restauration restaurent la valeur par défaut.

9. Cliquez sur **Démarrer le balisage**. Un exemple de test est généré.

10. Passez en revue et étiquetez chacun des fichiers sous l’onglet **Balise de pertinence \>** et, une fois terminé, cliquez sur **Calculer**.

11. Sous l’onglet Test, vous pouvez cliquer sur **Afficher les résultats** pour afficher les résultats du test.
