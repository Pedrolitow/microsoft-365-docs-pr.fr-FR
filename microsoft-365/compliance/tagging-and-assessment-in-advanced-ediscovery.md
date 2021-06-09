---
title: Marquage et évaluation dans Advanced eDiscovery
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
ms.assetid: b5c82de7-ed2f-4cc6-becd-db403faf4d18
ROBOTS: NOINDEX, NOFOLLOW
description: Examinez les étapes à suivre pour effectuer une formation sur l’évaluation, y compris le marquage des fichiers et l’examen des résultats de l’Advanced eDiscovery.
ms.openlocfilehash: 15bc8254ea1589d9afa17a74eaf3bfbcdfd4bba0
ms.sourcegitcommit: 5ba0015c1554048f817fdfdc85359eee1368da64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "49769189"
---
# <a name="tagging-and-assessment-in-the-relevance-module-in-advanced-ediscovery"></a>Marquage et évaluation dans le module de pertinence dans Advanced eDiscovery
  
Cette section décrit la procédure d’évaluation dans le module Pertinence dans Advanced eDiscovery.
  
## <a name="performing-assessment-training-and-analysis"></a>Formation et analyse de l’évaluation

1. Dans **l’onglet Suivi de \> pertinence,** cliquez **sur Évaluation** pour démarrer l’évaluation des cas.

    Par exemple, dans le cadre de cette procédure, un exemple  d’ensemble d’évaluation de 500 fichiers est créé et l’onglet Balise s’affiche, qui contient le panneau marquage, le contenu du fichier affiché et d’autres options de marquage. 

    ![Onglet Balise de pertinence pour l’évaluation](../media/c8acf891-b1cd-4344-816c-eabb8cbbe742.png)
  
2. Passez en revue chaque fichier de l’exemple, déterminez la pertinence du fichier pour chaque problème de cas et  marquez le fichier à l’aide des boutons Pertinence (R), Non pertinent (NR) et Ignorer dans le volet Marquage. 

    > [!NOTE]
    >  L’évaluation nécessite 500 fichiers balisé. Si les fichiers sont « ignorés », vous recevrez d’autres fichiers à baliser. 
  
3. Après avoir balisé tous les fichiers de l’exemple, cliquez sur **Calculer.**

    La marge d’erreur et la richesse  actuelles de l’évaluation sont calculées et affichées dans l’onglet Suivi de pertinence, avec des détails développés par problème, comme illustré ci-dessous. Plus d’informations sur cette boîte de dialogue sont décrites dans la section Révision des résultats [de l’évaluation.](#reviewing-assessment-results)

    ![Suivi de pertinence - Évaluation](../media/da911ba5-8678-40d6-9ad5-fd0b058355c1.png)
  
    > [!TIP]
    > Par défaut, nous vous recommandons de passer à l’étape suivante par défaut une fois l’indicateur de progression de l’évaluation du problème terminé, indiquant que l’exemple d’évaluation a été examiné et que des fichiers pertinents suffisants ont été balisé. > Dans le cas contraire, si  vous souhaitez afficher les résultats de l’onglet Suivi et contrôler la marge d’erreur et l’étape suivante, cliquez sur Modifier en regard de l’étape **suivante,** sélectionnez Continuer l’évaluation, puis cliquez sur **OK.**  
  
4. Cliquez **sur Modifier** à  droite de la case à cocher Évaluation pour afficher et spécifier les paramètres d’évaluation par problème. Une **boîte de dialogue de** niveau d’évaluation pour chaque problème s’affiche, comme illustré dans l’exemple suivant : 

    ![Problème de cas de niveau d’évaluation](../media/b7113fef-d125-4617-ae1b-c9eb0bf79aec.png)
  
    Les paramètres suivants du problème sont calculés et affichés dans la boîte de dialogue **Niveau d’évaluation** : 

    **Marge d’erreur cible pour** les estimations de rappel : en fonction de cette valeur, le nombre estimé de fichiers supplémentaires à réviser est calculé. La marge utilisée pour le rappel est supérieure à 75 % et avec un niveau de confiance de 95 %.

    **Fichiers d’évaluation supplémentaires** requis : indique combien de fichiers supplémentaires sont nécessaires si les exigences de la marge d’erreur actuelle n’ont pas été satisfaites. 

5. Pour ajuster la marge d’erreur actuelle et voir l’effet de différentes marges d’erreur (par problème) :

6. Dans la **liste Sélectionner un problème,** sélectionnez un problème. 

7. Dans **marge d’erreur cible pour les estimations de rappel,** entrez une nouvelle valeur.

8. Cliquez **sur Mettre à jour** les valeurs pour voir l’impact des ajustements. 

9. Cliquez **sur Avancé** dans la boîte de dialogue **Niveau** d’évaluation pour voir les paramètres et détails supplémentaires suivants : 

    ![Vue avancée de problème de cas de niveau d’évaluation](../media/577d7e0e-95df-48c2-9dec-bdeab5e801d8.png)
  
    - **Richesse estimée :** richesse estimée en fonction des résultats d’évaluation actuels

    - **Pour le rappel supposé :** par défaut, la marge d’erreur cible s’applique au rappel supérieur à 75 %. Cliquez **sur Modifier** si vous souhaitez modifier ce paramètre et contrôler la marge d’erreur sur une plage différente de valeurs de rappel. 

    - **Niveau de confiance**: par défaut, la marge d’erreur recommandée pour la confiance est de 95 %. Cliquez **sur Modifier** si vous souhaitez modifier ce paramètre.

    - **Marge d’erreur** de richesse attendue : étant donné les valeurs mises à jour, il s’agit de la marge d’erreur attendue de la richesse, une fois tous les fichiers d’évaluation supplémentaires examinés.

    - **Fichiers d’évaluation supplémentaires** requis : étant donné les valeurs mises à jour, le nombre de fichiers d’évaluation supplémentaires qui doivent être examinés pour atteindre la cible.

    - **Nombre total de fichiers d’évaluation requis**: étant donné les valeurs mises à jour, le nombre total de fichiers d’évaluation requis pour la révision.

    - **Nombre attendu de fichiers pertinents** dans l’évaluation : étant donné les valeurs mises à jour, le nombre attendu de fichiers pertinents dans l’ensemble de l’évaluation une fois tous les fichiers d’évaluation supplémentaires examinés.

10. Cliquez **sur Recalculer les valeurs,** si les paramètres sont modifiés. Lorsque vous avez terminé, s’il existe un problème,  cliquez sur **OK** pour enregistrer les modifications (ou suivant lorsqu’il existe plusieurs problèmes à réviser ou modifier, puis **à terminer).** 

    Lorsqu’il existe plusieurs problèmes, une fois tous les  problèmes examinés ou ajustés, un niveau d’évaluation : boîte de dialogue récapitulatif s’affiche, comme illustré dans l’exemple suivant. 

    ![Résumé de niveau d’évaluation](../media/4997b46d-10a5-4abc-b3b2-7b75a370eb9e.png)
  
    Une fois l’évaluation terminée, passer à l’étape suivante de l’entraînement Pertinence.

## <a name="reviewing-assessment-results"></a>Examen des résultats de l’évaluation

Une fois qu’un exemple d’évaluation est balisé, les résultats de l’évaluation sont calculés et affichés dans l’onglet Suivi de pertinence.
  
Les résultats suivants sont affichés dans l’affichage Piste étendue :
  
- Marge d’erreur actuelle d’évaluation pour les estimations de rappel

- Richesse estimée

- Fichiers d’évaluation supplémentaires requis (pour révision)

La marge d’erreur actuelle de l’évaluation est la marge d’erreur recommandée par Advanced eDiscovery. Le nombre affiché pour les « fichiers d’évaluation supplémentaires requis » correspond à cette recommandation.
  
L’indicateur de progression de l’évaluation indique le niveau d’achèvement de l’évaluation, compte tenu de la marge d’erreur actuelle. Lorsque l’évaluation est en cours, l’utilisateur marque un autre exemple d’évaluation.
  
Lorsque l’indicateur de progression de l’évaluation indique que l’évaluation est terminée, cela signifie que l’examen de l’exemple d’évaluation a été terminé et que des fichiers pertinents suffisants ont été marqués. 
  
L’affichage suivi développé montre l’étape suivante recommandée, les statistiques d’évaluation et l’accès aux résultats détaillés.
  
Lorsque la richesse est très faible, le nombre de fichiers d’évaluation supplémentaires nécessaires pour atteindre un nombre minimal de fichiers pertinents afin de produire des statistiques utiles est très élevé. Advanced eDiscovery vous recommanderez ensuite de passer à la formation. L’indicateur de progression de l’évaluation sera ombbré et aucune statistiques ne sera disponible.
  
En l’absence de stabilisation basée sur les statistiques, des résultats seront obtenus avec un niveau de précision et de confiance inférieurs. Toutefois, ces résultats peuvent être utilisés pour rechercher des fichiers pertinents lorsque vous n’avez pas besoin de connaître le pourcentage de fichiers pertinents trouvés. De même, cet état peut être utilisé pour entraîner des problèmes de faible richesse, où les scores de pertinence peuvent accélérer l’accès aux fichiers pertinents pour un problème spécifique.
  
> [!TIP]
> Dans **l’onglet Suivi de \> pertinence,** affichage des problèmes développé, les options d’affichage suivantes sont disponibles : 
> 
> L’étape suivante recommandée,  telle que l’étape suivante : le balisage peut être contourné (par problème) en cliquant sur le bouton Modifier à droite, puis en sélectionnant une autre étape à l’étape **suivante.**  Lorsque l’indicateur de progression de l’évaluation n’est pas terminé, l’évaluation est la prochaine option recommandée, pour baliser d’autres fichiers d’évaluation et améliorer la précision des statistiques. 
> 
> Vous pouvez modifier la marge d’erreur et évaluer son impact en cliquant sur Modifier **et** dans la boîte de dialogue Niveau d’évaluation, en modifiant la marge d’erreur cible pour les estimations de rappel et en cliquant sur Mettre à jour les **valeurs.** En outre, dans cette boîte de dialogue, vous pouvez afficher les options avancées en cliquant sur **Avancé.** 
> 
> Vous pouvez afficher des statistiques supplémentaires sur le niveau d’évaluation et leur impact en cliquant sur **Afficher.** Dans la boîte de dialogue De résultats détaillés affichée, des statistiques sont disponibles par problème, lorsqu’il y a au moins 500 fichiers d’évaluation balisé et qu’au moins 18 fichiers sont marqués comme pertinents pour le problème. 
