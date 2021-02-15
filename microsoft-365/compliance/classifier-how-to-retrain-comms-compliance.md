---
title: Comment reformer un classifieur en conformité de communications
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment fournir des commentaires à un classifieur entra nevable dans la conformité des communications.
ms.openlocfilehash: cdb8787715c3e022dfa0aa17cd83cc405aeef955
ms.sourcegitcommit: 54d1a2f363b2d5b63aae258c3cec0573a08f2866
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "49752648"
---
# <a name="how-to-retrain-a-classifier-in-communications-compliance"></a>Comment reformer un classifieur en conformité de communications

Un classifieur entraidable Microsoft 365 est un outil que vous pouvez former pour reconnaître différents types de contenu en lui donnant des exemples à examiner. Une fois formé, vous pouvez l’utiliser pour identifier l’élément pour l’application des étiquettes de confidentialité Office, des stratégies de conformité des communications et des stratégies d’étiquette de rétention.

Cet article vous montre comment améliorer les performances des classifieurs entraçables personnalisés et de certains classifieurs pré-formés en leur fournissant des commentaires supplémentaires.

Pour en savoir plus sur les différents types de classifieurs, voir En savoir plus sur les [classifieurs entraisables.](classifier-learn-about.md)

## <a name="permissions"></a>Autorisations

Pour accéder aux classifieurs dans le Centre de conformité Microsoft 365 :

- le rôle d’administrateur de conformité ou l’administrateur des données de conformité est requis pour former un classificateur

Vous aurez besoin de comptes avec ces autorisations pour utiliser des classifieurs dans les scénarios suivants :

- Scénario de stratégie de conformité des communications : administrateur de la gestion des risques internes, administrateur de vérification de surveillance 

## <a name="overall-workflow"></a>Flux de travail global

> [!IMPORTANT]
> Vous fournissez des commentaires dans la solution de conformité qui utilise le classifieur comme condition. **Si vous n’avez pas de stratégie de conformité des communications qui utilise un classificateur comme condition, arrêtez-vous ici.**

Lorsque vous utilisez vos classifieurs, vous souhaitez peut-être augmenter la précision des classifications qu’ils sont en train d’effectuer. Pour ce faire, vous devez évaluer la qualité des classifications des éléments qu’il a identifiés comme étant une correspondance ou non. Une fois que vous avez fait 30 évaluations pour un classificateur, il prend ce retour d’expérience et se réévalue automatiquement.

Pour en savoir plus sur le flux de travail global de la nouvelle formation d’un classifieur, voir Flux de processus pour former à nouveau [un classificateur.](classifier-learn-about.md#retraining-classifiers)

> [!NOTE]
> Un classifieur doit déjà être publié et en cours d’utilisation avant de pouvoir être à nouveau formé.

## <a name="how-to-retrain-a-classifier-in-communication-compliance-policies"></a>Comment former à nouveau un classificateur dans les stratégies de conformité des communications

1. Ouvrez la stratégie de conformité des communications qui utilise un classifieur comme condition et choisissez l’un des éléments identifiés dans la **liste En** attente.
2. Choisissez les points de non-accès et **améliorez la classification.**
3. Dans le **volet commentaires détaillés,** si l’élément est un vrai positif, choisissez, **Match**.  Si l’élément est un faux positif, c’est-à-dire qu’il a été inclus de manière incorrecte dans la catégorie, **sélectionnez Ne pas correspondre.**
4. S’il existe un autre classificateur qui serait plus approprié pour l’élément, vous pouvez le choisir dans la liste Suggérer d’autres **classifieurs entra nessifiables.** Cela déclenchera l’évaluation de l’élément par l’autre classificateur.

> [!TIP]
> Vous pouvez fournir des commentaires sur plusieurs éléments simultanément en les sélectionnant tous, puis en choisissant Fournir des commentaires détaillés **dans** la barre de commandes.

5. Sélectionnez **Envoyer des commentaires** pour envoyer votre évaluation des `match` classifications et suggérer `not a match` d’autres classifieurs entraintables. Lorsque vous avez fourni 30 instances de commentaires à un classifieur, il se formera automatiquement. La formation peut prendre entre 1 et 4 heures. Les classifieurs ne peuvent être formés que deux fois par jour.

> [!IMPORTANT]
> Ces informations sont ensuite données au classifieur de votre client, elles ne sont **pas revenir à Microsoft.**

6.  Ouvrez la page **Classification des** données dans le Centre de conformité Microsoft **365.**
7. Ouvrez **les classifieurs Entraisables.**
8. Le classificateur qui a été utilisé dans votre stratégie de conformité des communications s’affiche sous **l’en-tête Nouvelle** formation.

![classifieur dans l’état de la formation](../media/classifier-retraining.png)

9. Une fois la nouvelle formation terminée, choisissez le classificateur pour ouvrir la vue d’ensemble de la nouvelle formation.

![Vue d’ensemble des résultats de la formation du classificateur](../media/classifier-retraining-overview.png)

10. Examinez l’action recommandée et les comparaisons de prédictions des versions réétrainées et actuellement publiées du classifieur.
11. If you satisfied with the results of the retraining, choose **Re-publish**.
12. Si vous n’êtes pas satisfait des résultats de la nouvelle formation, vous pouvez choisir de fournir des commentaires supplémentaires au classifieur dans l’interface de conformité des communications et de démarrer un autre cycle de formation ou de ne rien faire, auquel cas la version actuellement publiée du classificateur continuera d’être utilisée. 

## <a name="details-on-republishing-recommendations"></a>Détails sur la republier des recommandations

Voici quelques informations sur la façon dont nous vous suggérons de publier à nouveau un classifieur retrained ou de suggérer une nouvelle formation. Cela nécessite une compréhension plus approfondie du fonctionnement des classifieurs entraisables.

Après une nouvelle formation, nous évaluons les performances du classificateur à la fois sur les éléments avec des commentaires, ainsi que sur tous les éléments utilisés à l’origine pour former le classificateur. 

- Pour les modèles intégrés, les éléments utilisés pour former le classifieur sont les éléments utilisés par Microsoft pour créer le modèle.
- Pour les modèles personnalisés, les éléments utilisés dans la formation d’origine du classifieur sont issus des sites que vous avez ajoutés pour le test et la révision.

Nous comparons les chiffres de performances sur les deux ensembles d’éléments pour le classifieur réécrit et publié afin de fournir une recommandation sur l’amélioration de la publication. 

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les classifieurs avec capacité d’apprentissage](classifier-learn-about.md)
- [Extensions de nom de fichier et types de fichier analysés par défaut dans SharePoint Server](https://docs.microsoft.com/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
