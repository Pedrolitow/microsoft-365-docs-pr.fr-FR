---
title: Comment reformer un classificateur en explorateur de contenu
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment fournir des commentaires à un classifieur pouvant être formé dans l’Explorateur de contenu.
ms.openlocfilehash: bde570b8bbb104d7f89523eb12bd8b9ac9210ad7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637436"
---
# <a name="how-to-retrain-a-classifier-in-content-explorer"></a>Comment reformer un classificateur en explorateur de contenu

Un classifieur pouvant être entraîné Microsoft 365 est un outil que vous pouvez entraîner pour reconnaître différents types de contenu en lui donnant des exemples à examiner. Une fois formé, vous pouvez l’utiliser pour identifier les éléments pour l’application d’étiquettes de confidentialité Office, de stratégies de conformité des communications et de stratégies d’étiquette de rétention.

Cet article explique comment améliorer les performances des classifieurs entraînés personnalisés en leur fournissant des commentaires supplémentaires.

Pour en savoir plus sur les différents types de classifieurs, consultez [En savoir plus sur les classifieurs pouvant être formés](classifier-learn-about.md).

Regardez cette vidéo pour obtenir un résumé rapide du processus de réglage et de réentraînement. Vous devrez toujours lire cet article complet pour obtenir les détails.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGMs]

> [!NOTE]
> Les classifieurs préentraînés ne peuvent pas être réentraînés.

## <a name="permissions"></a>Autorisations

Pour accéder aux classifieurs dans le portail de conformité Microsoft Purview :

- le rôle d’administrateur de conformité ou l’administrateur des données de conformité est requis pour entraîner un classifieur

Vous aurez besoin de comptes disposant des autorisations suivantes pour utiliser des classifieurs dans les scénarios suivants :

- Scénario de stratégie d’étiquette de rétention : rôles gestion des enregistrements et gestion de la rétention 

## <a name="overall-workflow"></a>Flux de travail global

> [!IMPORTANT]
> Vous fournissez des commentaires dans l’Explorateur de contenu pour appliquer automatiquement des stratégies d’étiquette de rétention aux éléments Exchange et utilisez le classifieur comme condition. **Si vous n’avez pas de stratégie de rétention qui applique automatiquement une étiquette de rétention aux éléments Exchange et utilise un classifieur comme condition, arrêtez-vous ici.**

Lorsque vous utilisez vos classifieurs, vous souhaiterez peut-être augmenter la précision des classifications qu’ils créent. Pour ce faire, vous évaluez la qualité des classifications effectuées pour les éléments qu’il a identifiés comme étant une correspondance ou non une correspondance. Une fois que vous avez fait 30 évaluations pour un classifieur, il prend ces commentaires et se réentraîne automatiquement.

Pour en savoir plus sur le flux de travail global de réentraînement d’un classifieur, consultez [Flux de processus pour réentraîner un classifieur](classifier-learn-about.md#retraining-classifiers).

> [!NOTE]
> Un classifieur doit déjà être publié et utilisé avant de pouvoir être réentraîné.

## <a name="how-to-retrain-a-classifier-in-content-explorer"></a>Comment reformer un classificateur en explorateur de contenu

1. Connectez-vous à portail de conformité Microsoft Purview avec l’accès au rôle d’administrateur de conformité ou d’administrateur de sécurité et ouvrez **portail de conformité Microsoft Purview** >  **Data classification** > **De l’Explorateur de contenu**. 
2. Sous la liste **Filtrer sur les étiquettes, les types d’informations ou les catégories** , développez **les classifieurs Trainable**.

> [!IMPORTANT]
> L’affichage des éléments agrégés sous l’en-tête des classifieurs pouvant être formés peut prendre jusqu’à huit jours.

3. Choisissez le classifieur pouvant être formé que vous avez utilisé pour appliquer automatiquement la stratégie d’étiquette de rétention. Il s’agit du classifieur pouvant être formé sur lequel vous donnerez vos commentaires.

> [!NOTE]
> Si un élément a une entrée dans la colonne **Étiquette de rétention** , cela signifie que l’élément a été classé en tant que `match`.  Si un élément n’a pas d’entrée dans la colonne **d’étiquette de rétention** , cela signifie qu’il a été classé en tant que `close match`. Vous pouvez améliorer la précision du classifieur le plus en fournissant des commentaires sur `close match` les éléments. 

4. Choisissez un élément et ouvrez-le.
 
 > [!TIP]
> Vous pouvez fournir des commentaires sur plusieurs éléments simultanément en les choisissant tous, puis en choisissant **Améliorer la classification** dans la barre de commandes.

5. Choisissez **Fournir des commentaires**.
6. Dans le volet **Commentaires détaillés** , si l’élément est un vrai positif, choisissez **Match**.  Si l’élément est un faux positif, c’est-à-dire qu’il a été inclus de manière incorrecte dans la catégorie, choisissez **Non une correspondance**.
7. S’il existe un autre classifieur qui serait plus approprié pour l’élément, vous pouvez le choisir dans la liste **Suggérer d’autres classifieurs pouvant être formés** . Cela déclenche l’autre classifieur pour évaluer l’élément.
8. Choisissez **Envoyer des commentaires** pour envoyer votre évaluation des `match`classifications `not a match` et suggérer d’autres classifieurs pouvant être formés. Une fois que vous avez fourni 30 instances de commentaires à un classifieur, il est automatiquement réentraîné. Le réentraînement peut prendre de une à quatre heures. Les classifieurs ne peuvent être réentraînés que deux fois par jour.

> [!IMPORTANT]
> Ces informations sont renvoyées au classifieur de votre locataire, **mais pas à Microsoft**.

9. Ouvrez **les classifieurs Trainable**.
10. Le classifieur qui a été utilisé dans votre stratégie de conformité des communications apparaît sous **l’en-tête Réentraîner** .

![classifieur dans l’état de réentraînement.](../media/classifier-retraining.png)

11. Une fois le réentraînement terminé, choisissez le classifieur pour ouvrir la vue d’ensemble du réentraînement.

![Vue d’ensemble des résultats du réentraînement du classifieur.](../media/classifier-retraining-overview.png)

12. Passez en revue l’action recommandée et les comparaisons de prédiction des versions réentraînées et publiées du classifieur.
13. Si vous êtes satisfait des résultats du réentraînement, choisissez **Republier**.
14. Si vous n’êtes pas satisfait des résultats du réentraînement, vous pouvez choisir de fournir des commentaires supplémentaires au classifieur dans l’interface de l’Explorateur de contenu et de démarrer un autre cycle de réentraînement ou de ne rien faire, auquel cas la version actuellement publiée du classifieur continuera d’être utilisée. 

## <a name="details-on-republishing-recommendations"></a>Détails sur la republication des recommandations

Voici quelques informations sur la façon dont nous formulerons la recommandation de publier à nouveau un classifieur réentraîné ou de suggérer un réentraînement. Cela nécessite une compréhension un peu plus approfondie du fonctionnement des classifieurs pouvant être formés.

Après un réentraînement, nous évaluons les performances du classifieur à la fois sur les éléments avec commentaires, ainsi que sur tous les éléments utilisés à l’origine pour entraîner le classifieur. 

- Pour les modèles intégrés, les éléments utilisés pour entraîner le classifieur sont les éléments utilisés par Microsoft pour générer le modèle.
- Pour les modèles personnalisés, les éléments utilisés dans l’entraînement d’origine du classifieur proviennent des sites que vous avez ajoutés à des fins de test et de révision.

Nous comparons les nombres de performances sur les deux ensembles d’éléments pour le classifieur réentraîné et publié pour fournir une recommandation sur l’amélioration de la republiation. 

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les classifieurs avec capacité d’apprentissage](classifier-learn-about.md)
- [Extensions de nom de fichier et types de fichier analysés par défaut dans SharePoint Server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
