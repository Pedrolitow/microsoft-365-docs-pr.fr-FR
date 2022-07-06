---
title: Prise en main des classifieurs avec capacité d’apprentissage
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
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkDEFENDER
search.appverid:
- MOE150
- MET150
description: Un classifieur Microsoft 365 est un outil que vous pouvez entraîner pour reconnaître différents types de contenu en lui donnant des exemples à examiner. Cet article vous montre comment créer et entraîner un classifieur personnalisé et comment le réentraîner pour augmenter la précision.
ms.openlocfilehash: ff23f24145cee1b694f96e933919dddf779dfd9a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631378"
---
# <a name="get-started-with-trainable-classifiers"></a>Prise en main des classifieurs avec capacité d’apprentissage

Un classifieur pouvant être entraîné Microsoft 365 est un outil que vous pouvez entraîner pour reconnaître différents types de contenu en lui donnant des exemples à examiner. Une fois formé, vous pouvez l’utiliser pour identifier l’élément pour l’application des étiquettes de confidentialité Office, des stratégies de conformité des communications et des stratégies d’étiquette de rétention.

La création d’un classifieur entraîné personnalisé implique d’abord de lui donner des échantillons qui sont sélectionnés par l’homme et correspondent positivement à la catégorie. Ensuite, après avoir traité ces éléments, vous testez la capacité des classifieurs à prédire en lui donnant un mélange d’échantillons positifs et négatifs. Cet article vous montre comment créer et entraîner un classifieur personnalisé et comment améliorer les performances des classifieurs et classifieurs préentraînés personnalisés tout au long de leur durée de vie grâce au réentraînement.

Pour en savoir plus sur les différents types de classifieurs, consultez [En savoir plus sur les classifieurs pouvant être formés](classifier-learn-about.md).

Regardez cette vidéo pour obtenir un résumé rapide de la création d’un classifieur pouvant être formé. Vous devrez toujours lire cet article complet pour obtenir les détails.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGL7]


## <a name="prerequisites"></a>Configuration requise

### <a name="licensing-requirements"></a>Conditions d'octroi de licence

Les classifieurs sont une fonctionnalité de conformité Microsoft 365 E5 ou E5. Vous devez disposer de l’un de ces abonnements pour pouvoir les utiliser.

### <a name="permissions"></a>Autorisations

Pour accéder aux classifieurs dans l’interface utilisateur : 

- l’administrateur général doit choisir le locataire pour créer des classifieurs personnalisés.
- Le rôle Administrateur de conformité est requis pour entraîner un classifieur.

Vous aurez besoin de comptes disposant des autorisations suivantes pour utiliser des classifieurs dans les scénarios suivants :

- Scénario de stratégie d’étiquette de rétention : rôles gestion des enregistrements et gestion de la rétention 
- Scénario de stratégie d’étiquette de confidentialité : Administrateur de sécurité, Administrateur de conformité, Administrateur des données de conformité
- Scénario de stratégie de conformité des communications : Administration de gestion des risques internes, administrateur de révision de surveillance 

> [!IMPORTANT]
> Par défaut, seul l’utilisateur qui crée un classifieur personnalisé peut entraîner et passer en revue les prédictions effectuées par ce classifieur.

## <a name="prepare-for-a-custom-trainable-classifier"></a>Préparer un classifieur entraîné personnalisé 

Il est utile de comprendre ce qui est impliqué dans la création d’un classifieur entraîné personnalisé avant de vous plonger. 

### <a name="timeline"></a>Chronologie

Cette chronologie reflète un exemple de déploiement de classifieurs pouvant être formés.

![trainable-classifier-timeline.](../media/trainable-classifier-deployment-timeline_border.png)

> [!TIP]
> L’adhésion est requise pour la première fois pour les classifieurs pouvant être formés. Il faut douze jours pour que Microsoft 365 effectue une évaluation de base du contenu de votre organisation. Contactez votre administrateur général pour lancer le processus d’adhésion.

### <a name="overall-workflow"></a>Flux de travail global

Pour en savoir plus sur le flux de travail global de la création de classifieurs pouvant être entraînés personnalisés, consultez [Flux de processus pour la création de classifieurs pouvant être entraînés personnalisés](classifier-learn-about.md#process-flow-for-creating-custom-classifiers).

### <a name="seed-content"></a>Contenu d’amorçage

Quand vous souhaitez qu’un classifieur pouvant être formé identifie de manière indépendante et précise un élément comme étant dans une catégorie particulière de contenu, vous devez d’abord le présenter avec de nombreux exemples du type de contenu qui se trouvent dans la catégorie. Cette alimentation d’échantillons au classifieur pouvant être formé est appelée *amorçage*. Le contenu seed est sélectionné par un humain et est jugé pour représenter la catégorie de contenu.

> [!TIP]
> Vous devez avoir au moins 50 échantillons positifs et jusqu’à 500. Le classifieur pouvant être formé traite jusqu’aux 500 exemples créés les plus récents (par horodatage/date/heure créé par fichier). Plus vous fournissez d’exemples, plus les prédictions effectuées par le classifieur sont précises.

### <a name="testing-content"></a>Test du contenu

Une fois que le classifieur pouvant être formé a traité suffisamment d’échantillons positifs pour générer un modèle de prédiction, vous devez tester les prédictions qu’il effectue pour voir si le classifieur peut faire correctement la distinction entre les éléments qui correspondent à la catégorie et les éléments qui ne le font pas. Pour ce faire, vous sélectionnez un autre ensemble, espérons-le plus volumineux, de contenu choisi par l’homme qui se compose d’échantillons qui doivent être classés dans la catégorie et d’échantillons qui ne le seront pas. Vous devez tester avec des données différentes des données initiales initiales que vous avez fournies. Une fois qu’il les traite, vous passez manuellement en revue les résultats et vérifiez si chaque prédiction est correcte, incorrecte ou que vous n’êtes pas sûr. Le classifieur pouvant être formé utilise ces commentaires pour améliorer son modèle de prédiction.

> [!TIP]
> Pour obtenir de meilleurs résultats, avez au moins 200 éléments dans votre jeu d’exemples de test avec une distribution uniforme de correspondances positives et négatives.

## <a name="how-to-create-a-trainable-classifier"></a>Comment créer un classifieur pouvant être formé

1. Collectez entre 50 et 500 éléments de contenu de départ. Il ne doit s’agir que d’exemples qui représentent fortement le type de contenu que vous souhaitez que le classifieur formable identifie positivement comme faisant partie de la catégorie de classification. Consultez les [extensions de nom de fichier analysées par défaut et les types de fichiers analysés dans SharePoint Server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) pour les types de fichiers pris en charge.

   > [!IMPORTANT]
   > Assurez-vous que les éléments de votre ensemble de semences sont des exemples **forts** de la catégorie. Le classifieur pouvant être formé génère initialement son modèle en fonction de ce que vous l’amorçez. Le classifieur suppose que tous les échantillons de semences sont des positifs forts et n’a aucun moyen de savoir si un échantillon est une correspondance faible ou négative avec la catégorie.

2. Placez le contenu d’amorçage dans un dossier SharePoint Online dédié à *la conservation du contenu de départ uniquement*. Notez le site, la bibliothèque et l’URL du dossier.

   > [!TIP]
   > Si vous créez un site et un dossier pour vos données initiales, autorisez au moins une heure l’indexation de cet emplacement avant de créer le classifieur pouvant être formé qui utilisera ces données initiales.

3. Connectez-vous à portail de conformité Microsoft Purview avec l’accès au rôle d’administrateur de conformité ou d’administrateur de la sécurité et ouvrez <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a> ou <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender données du portail</a> > **classification**.

4. Choisissez l’onglet **Classifieurs pouvant être formés** .

5. Choisissez **Créer un classifieur pouvant être formé**.

6. Renseignez les valeurs appropriées pour les champs et `Description` les `Name` champs de la catégorie d’éléments que vous souhaitez que ce classifieur formable identifie.

7. Sélectionnez le site SharePoint Online, la bibliothèque et l’URL du dossier pour le site de contenu de départ à l’étape 2. Choisissez `Add`.

8. Passez en revue les paramètres et choisissez `Create trainable classifier`.

9. Dans les 24 heures, le classifieur pouvant être formé traite les données initiales et génère un modèle de prédiction. L’état du classifieur est `In progress` alors qu’il traite les données initiales. Lorsque le classifieur a terminé le traitement des données initiales, l’état passe à `Need test items`.

10. Vous pouvez maintenant afficher la page de détails en choisissant le classifieur.

    > [!div class="mx-imgBorder"]
    > ![classifieur pouvant être entraîné prêt pour le test.](../media/classifier-trainable-ready-to-test-detail.png)

11. Collectez au moins 200 éléments de contenu de test (10 000 maximum) pour obtenir de meilleurs résultats. Il doit s’agir d’un mélange d’éléments qui sont des positifs forts, des négatifs forts et certains qui sont un peu moins évidents dans leur nature. Consultez les [extensions de nom de fichier analysées par défaut et les types de fichiers analysés dans SharePoint Server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) pour les types de fichiers pris en charge.

12. Placez le contenu du test dans un dossier SharePoint Online dédié à la conservation *du contenu de test uniquement*. Notez le site, la bibliothèque et l’URL du dossier SharePoint Online.

    > [!TIP]
    > Si vous créez un site et un dossier pour vos données de test, autorisez au moins une heure l’indexation de cet emplacement avant de créer le classifieur pouvant être formé qui utilisera ces données initiales.

13. Choisissez `Add items to test`.

14. Sélectionnez le site SharePoint Online, la bibliothèque et l’URL du dossier pour le site de contenu de test à l’étape 12. Choisissez `Add`.

15. Terminez l’Assistant en `Done`choisissant . Le traitement des fichiers de test prend jusqu’à une heure pour votre classifieur pouvant être formé.

16. Lorsque le classifieur pouvant être formé a terminé le traitement de vos fichiers de test, l’état de la page de détails passe à `Ready to review`. Si vous devez augmenter la taille de l’échantillon de test, choisissez et autorisez `Add items to test` le classifieur pouvant être formé à traiter les éléments supplémentaires.

    > [!div class="mx-imgBorder"]
    > ![capture d’écran prête à être examinée.](../media/classifier-trainable-ready-to-review-detail.png)

17. Choisissez `Tested items to review` l’onglet pour passer en revue les éléments.

18. Microsoft 365 présente 30 éléments à la fois. Passez-les en revue et dans la `We predict this item is "Relevant". Do you agree?` zone choisir ou `No` `Yes` `Not sure, skip to next item`. La précision du modèle est automatiquement mise à jour après chaque 30 éléments.

    > [!div class="mx-imgBorder"]
    > ![zone d’éléments de révision.](../media/classifier-trainable-review-detail.png)

19. Passez *en revue au moins* 200 éléments. Une fois le score de précision stabilisé, l’option **de publication** devient disponible et l’état du classifieur indique `Ready to use`.

    > [!div class="mx-imgBorder"]
    > ![score de précision et prêt à être publié.](../media/classifier-trainable-review-ready-to-publish.png)

20. Publiez le classifieur.

21. Une fois votre classifieur publié, il sera disponible en tant que condition dans [l’étiquetage automatique Office avec des étiquettes de confidentialité](apply-sensitivity-label-automatically.md), puis [appliquez automatiquement la stratégie d’étiquette de rétention en fonction d’une condition](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) et de la [conformité des communications](communication-compliance.md).
