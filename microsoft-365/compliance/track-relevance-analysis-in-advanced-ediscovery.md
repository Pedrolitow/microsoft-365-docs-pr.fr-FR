---
title: Suivre l’analyse de pertinence dans Advanced eDiscovery
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
ms.assetid: 3ab1e2c3-28cf-4bf5-b0a8-c0222f32bdf5
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment afficher et interpréter l’état et les résultats de l’entraînement Pertinence pour les problèmes de Advanced eDiscovery.
ms.openlocfilehash: ac575ebf073afa8eb4ba13e63202f8b634c52f60
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58573198"
---
# <a name="track-relevance-analysis-in-advanced-ediscovery"></a>Suivre l’analyse de pertinence dans Advanced eDiscovery
  
Dans Advanced eDiscovery, l’onglet Suivi de pertinence affiche la validité calculée de l’entraînement Pertinence effectué dans l’onglet Balise et indique l’étape suivante à effectuer dans le processus de formation itérative en Pertinence. 
  
## <a name="tracking-relevance-training-status"></a>Suivi de l’état de l’entraînement Pertinence

1. Consultez les détails suivants dans suivi de pertinence pour les problèmes de cas, comme illustré dans l’exemple suivant d’une boîte de dialogue Nom **du** problème ci-dessous.

   - **Évaluation**: cet indicateur de progression indique dans quelle mesure l’entraînement Pertinence effectué à ce stade a atteint l’objectif d’évaluation en termes de marge d’erreur. La richesse des résultats de l’entraînement Pertinence s’affiche également.

   - **Formation**: cet indicateur de progression et cette info-conseil codés en couleur indiquent la stabilité des résultats de l’entraînement Pertinence et une échelle numérique indiquant le nombre d’exemples d’entraînement Pertinence marqués pour chaque problème. L’expert surveille la progression du processus itératif de formation Pertinence. 
  
   - **Calcul par lot**: cet indicateur de progression fournit des informations sur la fin du calcul par lots.
  
   - **Étape suivante**: affiche la recommandation pour l’étape suivante à effectuer. 
  
    Dans l’exemple, une évaluation réussie d’un problème est affichée, indiquée par l’indicateur de progression de couleur terminé et la coche. Le marquage est en cours, mais le cas est toujours considéré comme instable (état de stabilité également indiqué dans une info-conseil). La recommandation de l’étape suivante est « Formation ». 
  
    ![Formation Pertinence - Étape 1.](../media/a00fe607-680a-48eb-9d61-4565319f7ab6.png)
  
    La vue étendue affiche des informations et des options supplémentaires. La marge d’erreur actuelle affichée est la marge d’erreur du rappel dans l’état actuel de l’évaluation, étant donné les fichiers d’évaluation existants (déjà marqués).
  
    > [!NOTE]
    >  L’étape d’évaluation peut  être contourné en effanant la case à cocher Évaluation par problème, puis pour « tous les problèmes ». Toutefois, il n’y aura donc pas de statistiques pour ce problème. > la case à cocher **d’évaluation** ne peut être effectuée qu’avant l’évaluation. Lorsque plusieurs problèmes existent dans un cas, l’évaluation est contourné uniquement si la case à cocher est effacée pour chaque problème 
  
    Lorsque l’évaluation n’est pas terminée avec le premier exemple de fichiers, l’évaluation peut être l’étape suivante pour baliser d’autres fichiers.
  
    Dans **la piste de pertinence,** l’indicateur de progression de la formation et l’info-conseil indiquent le nombre estimé d’échantillons supplémentaires nécessaires pour atteindre la \> stabilité. Cette estimation fournit des instructions pour la formation supplémentaire nécessaire.
  
    ![Formation de suivi de pertinence.](../media/98dbc3f5-5238-4d73-9f88-1aa4d77ea729.png)
  
2. Lorsque vous avez terminé le marquage et si vous avez besoin de continuer la formation, cliquez sur **Formation.** Un autre exemple de jeu de fichiers est généré à partir du jeu de fichiers chargé pour une formation supplémentaire. Vous êtes ensuite renvoyé à l’onglet Balise pour baliser et former d’autres fichiers.

### <a name="reaching-stable-training-levels"></a>Atteindre des niveaux de formation stables

Une fois que les fichiers d’évaluation ont atteint un niveau stable de formation, Advanced eDiscovery est prêt pour le calcul par lots.
  
> [!NOTE]
> En règle générale, après trois exemples de formation stables, l’étape suivante est « Calcul par lots ». Il peut y avoir des exceptions, par exemple, lorsque des modifications ont été apportées au marquage des fichiers à partir d’exemples précédents ou lorsque des fichiers d’amorçage ont été ajoutés. 
  
### <a name="performing-batch-calculation"></a>Effectuer le calcul par lots

Le calcul par lot est exécuté comme l’étape suivante une fois la formation terminée (lorsqu’un état de formation stable est affiché par la barre de progression, une coche et un état stable dans l’info-conseil).) Le calcul par lots applique les connaissances acquises lors de l’entraînement Pertinence à l’ensemble de la population de fichiers, afin d’évaluer la pertinence des fichiers et d’affecter des scores de pertinence.
  
Lorsqu’il y a plusieurs problèmes, le calcul par lot est effectué par problème. Pendant le calcul par lots, la progression est surveillée lors du traitement de tous les fichiers. 
  
Ici, l’étape suivante recommandée est « Aucun », ce qui indique qu’aucune formation itérative supplémentaire sur la pertinence n’est requise à ce stade. La phase suivante est **l’onglet Déterminer \> la** pertinence. 
  
Si vous souhaitez importer de nouveaux fichiers après le calcul par lots, l’administrateur peut ajouter les fichiers importés à un nouveau chargement.
  
> [!NOTE]
> Si vous cliquez sur **Annuler** pendant le calcul par lots, le processus enregistre ce qui a déjà été exécuté. Si vous exécutez à nouveau le calcul par lots, le processus se poursuit à partir du dernier point exécuté. 
  
### <a name="assessing-tagging-consistency"></a>Évaluation de la cohérence du marquage

S’il existe des incohérences dans le marquage de fichiers, cela peut affecter l’analyse. Le Advanced eDiscovery de cohérence de marquage peut être utilisé lorsque les résultats ne sont pas optimaux ou lorsque la cohérence est en doute. Une liste des fichiers marqués incohérents possibles est renvoyée, et ils peuvent être révisés et retardés, si nécessaire.
  
> [!NOTE]
> Après sept séries d’entraînements ou plus après  l’évaluation, la cohérence du marquage peut être vue dans la progression de formation détaillée des résultats du suivi de \>  \>  \>  \> **pertinence.** Cette révision est effectuée pour un problème à la fois.
  
1. Dans **la piste de \> pertinence,** développez la ligne d’un problème.
  
2. À droite de **l’étape suivante,** cliquez sur **Modifier.**
  
3. Sélectionnez **incohérences de balise comme** option de **l’étape** suivante, après sept exemples de formation et cliquez sur **OK**.
  
4. Sélectionner **les incohérences de balise**. **L’onglet** Balise s’ouvre et affiche une liste des incohérences à retager si nécessaire.
  
5. Cliquez **sur Calculer** pour envoyer les modifications. L’étape suivante après le marquage des incohérences est « Formation ». 
  
## <a name="viewing-and-using-relevance-results"></a>Affichage et utilisation des résultats de pertinence

Dans **l’onglet Suivi \>** de pertinence, développez la ligne d’un problème, puis en regard des résultats détaillés, cliquez sur **Afficher.** Les volets de résultats détaillés sont affichés, comme indiqué et décrit ci-dessous.
  
![Résultats détaillés de l’entraînement de pertinence.](../media/495c04a9-ed1e-4355-8cab-c14270ca2bbb.png)
  
### <a name="tagging-summary"></a>Résumé du marquage

 Dans l’exemple ci-dessous, **le** résumé de marquage affiche les totaux de chacun des processus de marquage des fichiers d’évaluation, de formation et de rattrapage.
  
![Résumé du marquage du suivi de pertinence.](../media/0ec906fc-bc84-4245-a964-fb3ca37891db.png)
  
### <a name="keywords"></a>Mots clés

Un mot clé est une chaîne, un mot, une expression ou une séquence de mots uniques dans un fichier identifié par Advanced eDiscovery comme un indicateur significatif de la pertinence d’un fichier. Les colonnes « Inclure » répertorient les mots clés et les poids dans les fichiers marqués comme pertinents, et les colonnes « Exclure » répertorient les mots clés et les pondérations dans les fichiers marqués comme non pertinents.
  
Advanced eDiscovery attribue des valeurs négatives ou positives de poids de mot clé. Plus le poids est élevé, plus la probabilité qu’un fichier dans lequel le mot clé apparaît soit affecté d’un score de pertinence plus élevé lors du calcul par lot est élevée.
  
La Advanced eDiscovery de mots clés peut être utilisée pour compléter une liste conçue par un expert ou comme une vérification de l’insérezation indirecte à tout moment dans le processus de révision de fichier.
  
### <a name="training-progress"></a>Progression de la formation

Le **volet Progression de** l’entraînement inclut un graphique de progression de la formation et un indicateur de qualité, comme illustré dans l’exemple ci-dessous.
  
![Progression de l’entraînement de suivi de pertinence.](../media/8a5089f5-a162-4246-ae09-bc1921859860.png)
  
**Indicateur de qualité de formation**: affiche l’évaluation de la cohérence du marquage comme suit :
  
- **Bon**: les fichiers sont balisé de manière cohérente. (Lumière verte affichée)
  
- **Moyen**: certains fichiers peuvent être marqués de manière incohérente. (Lumière jaune affichée)

- **Avertissement**: de nombreux fichiers peuvent être marqués de manière incohérente. (Lumière rouge affichée)

**Graphique de progression de l’entraînement**: indique le degré de stabilité de l’entraînement Pertinence après de nombreux cycles d’entraînement Pertinence par rapport à la valeur de mesure F. Lorsque nous allons de gauche à droite sur le graphique, l’intervalle de confiance est réduit et utilisé, avec la mesure F, par Advanced eDiscovery Pertinence pour déterminer la stabilité lorsque les résultats de l’entraînement Pertinence sont optimisés.
  
> [!NOTE]
> La pertinence utilise F2, une mesure F dans laquelle le rappel reçoit deux fois plus de poids que la précision. Pour les cas avec une richesse élevée (plus de 25 %) la pertinence utilise F1 (rapport 1:1). Le rapport de mesure F peut être configuré dans les **paramètres** avancés d’installation \> **de pertinence.**
  
### <a name="batch-calculation-results"></a>Résultats de calcul par lot

Le **volet Résultats du calcul par** lot inclut le nombre de fichiers qui ont été marqués pour Pertinence, comme suit : 
  
- **Success**
  
- **Vide**: ne contient pas de texte, par exemple, uniquement les espaces/onglets
  
- **Échec :** en raison d’une taille excessive ou de l’échec de lecture
  
- **Ignoré :** en raison d’une taille excessive
  
- **Nebulous**: contient du texte sans signification ou aucune fonctionnalité pertinente au problème
  
> [!NOTE]
> Empty, Failed, Ignored ou Nebulous reçoit un score de pertinence de -1.
  
### <a name="training-statistics"></a>Statistiques de formation

Le **volet Statistiques** de formation affiche des statistiques et des graphiques basés sur les résultats de Advanced eDiscovery formation Pertinence. 
  
![Statistiques de formation de suivi de pertinence.](../media/9a07740e-20d3-49fb-b9b9-84265e0a1836.png)
  
Cet affichage présente les exemples suivants :
  
- **Taux de révision/rappel :** comparaison des résultats en fonction des scores de pertinence dans une révision hypothétiquement linéaire. Le rappel est estimé en raison de la taille du jeu à réviser.
  
- **Paramètres**: statistiques calculées cumulées relatives au jeu à réviser par rapport à la population de fichiers pour l’ensemble du cas.
  
- **Révision**: Pourcentage de fichiers à réviser en fonction de ce cutoff.
  
- **Rappel**: pourcentage de fichiers pertinents dans le jeu à réviser. 
  
- **Répartition par score de pertinence**: les fichiers dans l’affichage gris foncé à gauche sont inférieurs au score de seuil. Une info-conseil affiche le score de pertinence et le pourcentage connexe de fichiers dans le jeu de fichiers de révision par rapport au nombre total de fichiers.
