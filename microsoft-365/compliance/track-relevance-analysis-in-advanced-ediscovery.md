---
title: Suivre l’analyse de pertinence dans eDiscovery (Premium)
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
ms.assetid: 3ab1e2c3-28cf-4bf5-b0a8-c0222f32bdf5
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment afficher et interpréter l’état et les résultats de la formation pertinence pour les problèmes de cas dans eDiscovery (Premium).
ms.openlocfilehash: dce726553d5664714f9c479113ae00abd91aafff
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627346"
---
# <a name="track-relevance-analysis-in-ediscovery-premium"></a>Suivre l’analyse de pertinence dans eDiscovery (Premium)
  
Dans Microsoft Purview eDiscovery (Premium), l’onglet Suivi de la pertinence affiche la validité calculée de l’entraînement pertinence effectué sous l’onglet Balise et indique l’étape suivante à effectuer dans le processus d’apprentissage itératif dans Pertinence. 
  
## <a name="tracking-relevance-training-status"></a>Suivi de l’état de l’entraînement pertinence

1. Affichez les détails suivants dans La piste de pertinence pour les problèmes de cas, comme illustré dans l’exemple suivant d’une boîte de dialogue **Nom du problème** ci-dessous.

   - **Évaluation** : cet indicateur de progression indique dans quelle mesure la formation de pertinence effectuée à ce stade a atteint la cible d’évaluation en termes de marge d’erreur. La richesse des résultats de l’apprentissage de pertinence s’affiche également.

   - **Formation** : cet indicateur de progression codé en couleurs et cette info-bulle indiquent la stabilité des résultats de l’entraînement de pertinence et une échelle numérique indiquant le nombre d’exemples d’entraînement de pertinence marqués pour chaque problème. L’expert surveille la progression du processus d’entraînement de pertinence itérative. 
  
   - **Calcul par lots** : cet indicateur de progression fournit des informations sur l’achèvement du calcul Batch.
  
   - **Étape suivante** : affiche la recommandation pour l’étape suivante à effectuer. 
  
    Dans l’exemple, une évaluation réussie pour un problème s’affiche, indiquée par l’indicateur de progression de couleur terminé et la coche. Le balisage est en cours, mais le cas est toujours considéré comme instable (état de stabilité également indiqué dans une info-bulle). La recommandation de l’étape suivante est « Formation ». 
  
    ![Étape 1 de la formation du suivi de la pertinence.](../media/a00fe607-680a-48eb-9d61-4565319f7ab6.png)
  
    La vue développée affiche des informations et des options supplémentaires. La marge d’erreur actuelle affichée est la marge d’erreur du rappel dans l’état actuel de l’évaluation, compte tenu des fichiers d’évaluation existants (déjà étiquetés).
  
    > [!NOTE]
    >  L’étape d’évaluation peut être contournée en désactivant la case à cocher **Évaluation** par problème, puis pour « tous les problèmes ». Toutefois, il n’y aura donc aucune statistique pour ce problème. > la case à cocher **Évaluation** ne peut être effectuée qu’avant l’évaluation. Lorsque plusieurs problèmes existent dans un cas, l’évaluation est contournée uniquement si la case à cocher est désactivée pour chaque problème 
  
    Lorsque l’évaluation n’est pas terminée avec le premier exemple de fichiers, l’évaluation peut être l’étape suivante pour l’étiquetage d’autres fichiers.
  
    Dans Le **suivi** **de la pertinence**\>, l’indicateur de progression de l’apprentissage et la info-bulle indiquent le nombre estimé d’échantillons supplémentaires nécessaires pour atteindre la stabilité. Cette estimation fournit des instructions pour la formation supplémentaire nécessaire.
  
    ![Formation du suivi de la pertinence.](../media/98dbc3f5-5238-4d73-9f88-1aa4d77ea729.png)
  
2. Lorsque vous avez terminé le balisage et si vous devez continuer l’entraînement, cliquez sur **Formation**. Un autre exemple de jeu de fichiers est généré à partir du jeu de fichiers chargé pour une formation supplémentaire. Vous êtes ensuite retourné à l’onglet Étiquette pour étiqueter et entraîner d’autres fichiers.

### <a name="reaching-stable-training-levels"></a>Atteindre des niveaux d’entraînement stables

Une fois que les fichiers d’évaluation ont atteint un niveau stable d’entraînement, eDiscovery (Premium) est prêt pour le calcul Batch.
  
> [!NOTE]
> En règle générale, après trois exemples d’entraînement stables, l’étape suivante est « Calcul batch ». Il peut y avoir des exceptions, par exemple, lorsque des modifications ont été apportées à l’étiquetage des fichiers à partir d’exemples antérieurs ou lorsque des fichiers initiaux ont été ajoutés. 
  
### <a name="performing-batch-calculation"></a>Exécution du calcul Batch

Le calcul par lots est exécuté à l’étape suivante une fois l’entraînement terminé (lorsqu’un état d’apprentissage stable est affiché par la barre de progression, une coche et un état stable dans l’info-bulle.) Le calcul par lots applique les connaissances acquises pendant l’entraînement de pertinence à l’ensemble du remplissage des fichiers, pour évaluer la pertinence des fichiers et attribuer des scores de pertinence.
  
Lorsqu’il existe plusieurs problèmes, le calcul Batch est effectué par problème. Pendant le calcul Batch, la progression est surveillée lors du traitement de tous les fichiers. 
  
Ici, l’étape suivante recommandée est « None », ce qui indique qu’aucune formation itérative supplémentaire sur la pertinence n’est requise à ce stade. La phase suivante est l’onglet **Décider de la pertinence\>**. 
  
Si vous souhaitez importer de nouveaux fichiers après le calcul Batch, l’administrateur peut ajouter les fichiers importés à une nouvelle charge.
  
> [!NOTE]
> Si vous cliquez sur **Annuler** pendant le calcul Batch, le processus enregistre ce qui a déjà été exécuté. Si vous réexécutez le calcul Batch, le processus se poursuit à partir du dernier point exécuté. 
  
### <a name="assessing-tagging-consistency"></a>Évaluation de la cohérence de l’étiquetage

S’il existe des incohérences dans l’étiquetage des fichiers, cela peut affecter l’analyse. Le processus de cohérence de balisage eDiscovery (Premium) peut être utilisé lorsque les résultats ne sont pas optimaux ou que la cohérence est incertaine. Une liste de fichiers éventuellement étiquetés de manière incohérente est retournée et peut être examinée et retalée, si nécessaire.
  
> [!NOTE]
> Après sept cycles d’entraînement ou plus après l’évaluation, la cohérence de l’étiquetage peut être affichée dans Le **problème** \> de **suivi** \> **de pertinence** \> **Résultats détaillés** \> Progression de l’apprentissage **.** Cette révision est effectuée pour un problème à la fois.
  
1. Dans **La piste de pertinence\>**, développez la ligne d’un problème.
  
2. À droite de **l’étape suivante**, cliquez sur **Modifier**.
  
3. Sélectionnez **Les incohérences de balise** comme option **d’étape suivante** , après sept exemples d’apprentissage, puis cliquez sur **OK**.
  
4. Sélectionnez **Incohérences de balise**. L’onglet **Balise** s’ouvre et affiche une liste des incohérences à rétager si nécessaire.
  
5. Cliquez sur **Calculer** pour envoyer les modifications. L’étape suivante après l’étiquetage des incohérences est « Formation ». 
  
## <a name="viewing-and-using-relevance-results"></a>Affichage et utilisation des résultats de pertinence

Sous l’onglet **Suivi de la pertinence\>**, développez la ligne d’un problème et, en regard des **résultats détaillés**, cliquez sur **Afficher**. Les volets de résultats détaillés sont affichés, comme indiqué et décrit ci-dessous.
  
![Résultats détaillés de la formation sur la pertinence.](../media/495c04a9-ed1e-4355-8cab-c14270ca2bbb.png)
  
### <a name="tagging-summary"></a>Résumé de l’étiquetage

 Dans l’exemple ci-dessous, le **résumé du balisage** affiche les totaux de chacun des processus d’étiquetage des fichiers d’évaluation, d’apprentissage et de rattrapage.
  
![Récapitulatif du balisage du suivi de la pertinence.](../media/0ec906fc-bc84-4245-a964-fb3ca37891db.png)
  
### <a name="keywords"></a>Mots-clés

Un mot clé est une chaîne unique, un mot, une expression ou une séquence de mots dans un fichier identifié par eDiscovery (Premium) comme indicateur significatif de la pertinence d’un fichier. Les colonnes « Include » répertorient le mot clé et les pondérations dans les fichiers marqués comme pertinents, et les colonnes « Exclure » répertorient les mots clés et les pondérations dans les fichiers marqués comme non pertinents.
  
eDiscovery (Premium) attribue des valeurs de poids de mot clé négatives ou positives. Plus le poids est élevé, plus la probabilité qu’un fichier dans lequel le mot clé apparaît soit affectée à un score de pertinence plus élevé pendant le calcul Batch.
  
La liste eDiscovery (Premium) de mots clés peut être utilisée pour compléter une liste créée par un expert ou comme vérification indirecte de l’intégrité à tout moment dans le processus de révision des fichiers.
  
### <a name="training-progress"></a>Progression de la formation

Le volet **Progression** de l’apprentissage comprend un graphique de progression de l’apprentissage et un affichage d’indicateur de qualité, comme illustré dans l’exemple ci-dessous.
  
![Pertinence Suivre la progression de l’entraînement.](../media/8a5089f5-a162-4246-ae09-bc1921859860.png)
  
**Indicateur de qualité** de l’entraînement : affiche l’évaluation de la cohérence de balisage comme suit :
  
- **Bon** : les fichiers sont étiquetés de manière cohérente. (Feu vert affiché)
  
- **Moyen** : certains fichiers peuvent être étiquetés de manière incohérente. (Lumière jaune affichée)

- **Avertissement** : de nombreux fichiers peuvent être étiquetés de manière incohérente. (Lumière rouge affichée)

**Graphique de progression** de l’entraînement : indique le degré de stabilité de l’entraînement de pertinence après de nombreux cycles d’entraînement de pertinence par rapport à la valeur de mesure F. À mesure que nous nous déplaçons de gauche à droite dans le graphique, l’intervalle de confiance se rétrécit et est utilisé, avec la mesure F, par la pertinence eDiscovery (Premium) pour déterminer la stabilité lorsque les résultats de l’entraînement pertinence sont optimisés.
  
> [!NOTE]
> La pertinence utilise F2, une métrique de mesure F où Recall reçoit deux fois plus de poids que precision. Pour les cas avec une richesse élevée (plus de 25 %), la pertinence utilise F1 (ratio 1:1). Le ratio de mesure F peut être configuré dans les **paramètres avancés** de **configuration** \> de pertinence.
  
### <a name="batch-calculation-results"></a>Résultats du calcul par lot

Le volet des **résultats du calcul Batch** inclut le nombre de fichiers qui ont été notés pour pertinence, comme suit : 
  
- **Success**
  
- **Vide** : ne contient aucun texte, par exemple, uniquement des espaces/onglets
  
- **Échec** : En raison d’une taille excessive ou d’une lecture impossible
  
- **Ignoré :** En raison d’une taille excessive
  
- **Nébuleux** : contient du texte sans signification ou aucune fonctionnalité pertinente pour le problème
  
> [!NOTE]
> Empty, Failed, Ignored ou Nebulous recevra un score de pertinence de -1.
  
### <a name="training-statistics"></a>Statistiques de formation

Le volet **Statistiques** de formation affiche des statistiques et des graphiques basés sur les résultats de l’apprentissage de pertinence eDiscovery (Premium). 
  
![Statistiques de formation du suivi de la pertinence.](../media/9a07740e-20d3-49fb-b9b9-84265e0a1836.png)
  
Cette vue montre les éléments suivants :
  
- **Ratio révision-rappel** : comparaison des résultats en fonction des scores de pertinence dans une révision hypothétiquement linéaire. Le rappel est estimé en fonction de la taille du jeu de révision défini.
  
- **Paramètres** : statistiques calculées cumulatives relatives à l’ensemble de révisions par rapport à la population de fichiers pour l’ensemble du cas.
  
- **Révision** : pourcentage de fichiers à examiner en fonction de ce seuil.
  
- **Rappel** : Pourcentage de fichiers pertinents dans l’ensemble de révision. 
  
- **Distribution par score de pertinence** : les fichiers dans l’affichage gris foncé à gauche sont inférieurs au score de coupure. Un info-bulle affiche le score de pertinence et le pourcentage associé de fichiers dans le fichier de révision défini par rapport au nombre total de fichiers.
