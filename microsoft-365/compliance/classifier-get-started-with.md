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
localization_priority: None
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Un classificateur Microsoft 365 est un outil que vous pouvez former pour reconnaître différents types de contenu en lui donnant des exemples à examiner. Cet article vous montre comment créer et former un classifieur personnalisé et comment les former à nouveau pour améliorer la précision.
ms.openlocfilehash: 90e47ec94528bbadeb98dc9eb590929e25ae6ff1
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50918178"
---
# <a name="get-started-with-trainable-classifiers"></a>Prise en main des classifieurs avec capacité d’apprentissage

Un classifieur Entraéable Microsoft 365 est un outil que vous pouvez former pour reconnaître différents types de contenu en lui donnant des exemples à examiner. Une fois formé, vous pouvez l’utiliser pour identifier l’élément pour l’application des étiquettes de confidentialité Office, des stratégies de conformité des communications et des stratégies d’étiquette de rétention.

La création d’un classifieur entraisable personnalisé implique d’abord de lui donner des exemples qui sont choisis par l’homme et qui correspondent à la catégorie. Ensuite, après les avoir traitées, vous testez la capacité des classifieurs à prévoir en lui donnant un mélange d’échantillons positifs et négatifs. Cet article vous montre comment créer et former un classifieur personnalisé et comment améliorer les performances des classifieurs entraînables personnalisés et des classifieurs pré-formés tout au long de leur durée de vie via une nouvelle formation.

Pour en savoir plus sur les différents types de classifieurs, voir En savoir plus sur les [classifieurs entraisables.](classifier-learn-about.md)

Regardez cette vidéo pour obtenir un résumé rapide de la création d’un classifieur entraisable. Vous devrez tout de même lire cet article complet pour obtenir les détails.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGL7]


## <a name="prerequisites"></a>Conditions requises

### <a name="licensing-requirements"></a>Critères de licence

Les classifieurs sont une fonctionnalité de conformité Microsoft 365 E5 ou E5. Vous devez avoir l’un de ces abonnements pour pouvoir les utiliser.

### <a name="permissions"></a>Autorisations

Pour accéder aux classifieurs dans l’interface utilisateur : 

- L’administrateur global doit choisir le client pour créer des classifieurs personnalisés.
- Le rôle Administrateur de conformité est requis pour former un classifieur.

Vous aurez besoin de comptes avec ces autorisations pour utiliser des classifieurs dans les scénarios suivants :

- Scénario de stratégie d’étiquette de rétention : rôles gestion des enregistrement et gestion de la rétention 
- Scénario de stratégie d’étiquette de confidentialité : administrateur de sécurité, administrateur de conformité, administrateur de données de conformité
- Scénario de stratégie de conformité des communications : administrateur de la gestion des risques internes, administrateur de vérification de surveillance 

> [!IMPORTANT]
> Par défaut, seul l’utilisateur qui crée un classifieur personnalisé peut entraîner et passer en revue les prédictions faites par ce classificateur.

## <a name="prepare-for-a-custom-trainable-classifier"></a>Préparer un classifieur entraisable personnalisé 

Il est utile de comprendre ce qui est impliqué dans la création d’un classifieur entraisable personnalisé avant de vous plonger. 

### <a name="timeline"></a>Chronologie

Cette chronologie reflète un exemple de déploiement de classifieurs entraisables.

![trainable-classifier-timeline](../media/trainable-classifier-deployment-timeline_border.png)

> [!TIP]
> L’option d’opt-in est requise la première fois pour les classifieurs entraisables. Il faut douze jours pour que Microsoft 365 termine une évaluation de référence du contenu de votre organisation. Contactez votre administrateur général pour lancer le processus d’opt-in.

### <a name="overall-workflow"></a>Flux de travail global

Pour en savoir plus sur le flux de travail global de création de classifieurs entra nessables personnalisés, voir Flux de processus pour la création de [classifieurs entra mentables par le client.](classifier-learn-about.md#process-flow-for-creating-custom-classifiers)

### <a name="seed-content"></a>Contenu d’amorçage

Lorsque vous souhaitez qu’un classifieur entraisable identifie de manière indépendante et précise un élément comme étant dans une catégorie particulière de contenu, vous devez d’abord le présenter avec de nombreux exemples du type de contenu de la catégorie. Cet amorçage d’échantillons au classifieur entraçable est appelé *amorçage.* Le contenu de amorçage est sélectionné par un humain et est jugé pour représenter la catégorie de contenu.

> [!TIP]
> Vous devez avoir au moins 50 échantillons positifs et jusqu’à 500. Le classificateur entraçable traitera jusqu’aux 500 exemples créés les plus récents (par date/horodateur de création de fichier). Plus vous fournissez d’exemples, plus les prédictions du classifieur seront précises.

### <a name="testing-content"></a>Test du contenu

Une fois que le classifieur entraisable a traitée suffisamment d’échantillons positifs pour créer un modèle de prédiction, vous devez tester les prédictions qu’il effectue pour voir si le classifieur peut correctement faire la distinction entre les éléments qui correspondent à la catégorie et les éléments qui ne le sont pas. Pour ce faire, vous sélectionnez un autre ensemble de contenu sélectionné par l’être humain, avec un plus grand nombre d’échantillons qui doivent être placés dans la catégorie et des exemples qui ne le seront pas. Vous devez tester avec des données différentes des données initiales initiales que vous avez fournies. Une fois qu’il les traite, vous allez manuellement à travers les résultats et vérifiez si chaque prédiction est correcte, incorrecte ou vous n’êtes pas sûr. Le classifieur entraisable utilise ce retour d’expérience pour améliorer son modèle de prédiction.

> [!TIP]
> Pour obtenir de meilleurs résultats, vous devez avoir au moins 200 éléments dans votre exemple de test avec une distribution équitable de correspondances positives et négatives.

## <a name="how-to-create-a-trainable-classifier"></a>Comment créer un classifieur entraisable

1. Collectez entre 50 et 500 éléments de contenu d’amorçage. Il doit s’agit uniquement d’exemples qui représentent fortement le type de contenu que le classifieur entraçable doit identifier comme étant dans la catégorie de classification. Reportez-vous [aux extensions de](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) nom de fichier et aux types de fichiers analyse par défaut dans SharePoint Server pour les types de fichiers pris en charge.

   > [!IMPORTANT]
   > Les exemples d’amorçage et de test ne doivent pas être chiffrés et doivent être en anglais.

   > [!IMPORTANT]
   > Assurez-vous que les éléments de votre jeu de valeurs sont **des exemples** forts de la catégorie. Le classifieur entraçable crée initialement son modèle en fonction de ce avec quoi vous l’amorçez. Le classificateur suppose que tous les échantillons de amorçage sont des positifs forts et n’a aucun moyen de savoir si un échantillon est une correspondance faible ou négative avec la catégorie.

2. Placez le contenu de l’amorçage dans un dossier SharePoint Online dédié à la mise en place du *contenu d’amorçage uniquement.* Notez l’URL du site, de la bibliothèque et du dossier.

   > [!TIP]
   > Si vous créez un site et un dossier pour vos données d’amorçage, autorisez l’indexation d’au moins une heure de cet emplacement avant de créer le classifieur entraisable qui utilisera ces données d’amorçage.

3. Connectez-vous au Centre de conformité Microsoft 365 avec l’accès au rôle d’administrateur de conformité ou d’administrateur de sécurité et ouvrez le Centre de conformité **Microsoft 365** ou la classification des données du Centre de sécurité **Microsoft 365.**  >  

4. Sélectionnez **l’onglet Classifieurs avec formation.**

5. Choose **Create trainable classifier**.

6. Remplissez les valeurs appropriées pour les champs de la catégorie d’éléments que ce `Name` `Description` classifieur entraçable doit identifier.

7. Choisissez l’URL du site, de la bibliothèque et du dossier SharePoint Online pour le site de contenu d’amorçage à l’étape 2. Choose `Add` .

8. Examinez les paramètres et choisissez `Create trainable classifier` .

9. Dans un délai de 24 heures, le classifieur entraçable traitera les données d’amorçage et créera un modèle de prédiction. L’état du classifieur `In progress` est pendant qu’il traite les données d’amorçage. Lorsque le classificateur a terminé le traitement des données de amorçage, l’état change en `Need test items` .

10. Vous pouvez désormais afficher la page de détails en choisissant le classificateur.

    > [!div class="mx-imgBorder"]
    > ![Classifieur entraisable prêt pour le test](../media/classifier-trainable-ready-to-test-detail.png)

11. Collectez au moins 200 éléments de contenu de test (10 000 max) pour obtenir de meilleurs résultats. Il doit s’agit d’un mélange d’éléments qui sont de forts positifs, de négatifs forts et d’autres qui sont un peu moins évidents dans leur nature. Reportez-vous [aux extensions de](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) nom de fichier et aux types de fichiers analyse par défaut dans SharePoint Server pour les types de fichiers pris en charge.

    > [!IMPORTANT]
    > Les exemples d’éléments ne doivent pas être chiffrés et doivent être en anglais.

12. Placez le contenu de test dans un dossier SharePoint Online dédié à la mise en place du *contenu de test uniquement.* Notez l’URL du site, de la bibliothèque et du dossier SharePoint Online.

    > [!TIP]
    > Si vous créez un site et un dossier pour vos données de test, autorisez l’indexation d’au moins une heure de cet emplacement avant de créer le classifieur entraisable qui utilisera ces données d’amorçage.

13. Choose `Add items to test` .

14. Choisissez l’URL du site, de la bibliothèque et du dossier SharePoint Online pour le site de contenu de test à l’étape 12. Choose `Add` .

15. Terminez l’Assistant en choisissant `Done` . Le traitement des fichiers de test peut prendre jusqu’à une heure.

16. Lorsque le classifieur entra vous permet de traiter vos fichiers de test, l’état sur la page de détails passe à `Ready to review` . Si vous devez augmenter la taille de l’échantillon de test, choisissez et autorisez le `Add items to test` classifieur entraçable à traiter les éléments supplémentaires.

    > [!div class="mx-imgBorder"]
    > ![Capture d’écran prête à être revue](../media/classifier-trainable-ready-to-review-detail.png)

17. Choisissez `Tested items to review` l’onglet pour passer en revue les éléments.

18. Microsoft 365 présente 30 éléments à la fois. Examinez-les et dans la `We predict this item is "Relevant". Do you agree?` zone choisissez soit ou `Yes` `No` `Not sure, skip to next item` . La précision du modèle est automatiquement mise à jour après 30 éléments.

    > [!div class="mx-imgBorder"]
    > ![zone d’avis sur les éléments](../media/classifier-trainable-review-detail.png)

19. Passer *en revue au moins* 200 éléments. Une fois que le score de précision s’est stabilisé, l’option **de** publication devient disponible et l’état du classificateur le dit `Ready to use` .

    > [!div class="mx-imgBorder"]
    > ![score de précision et prêt à être publié](../media/classifier-trainable-review-ready-to-publish.png)

20. Publiez le classifieur.

21. Une fois publié, votre classificateur sera disponible en tant que condition dans l’étiquetage automatique [d’Office](apply-sensitivity-label-automatically.md)avec des étiquettes de confidentialité , appliquer automatiquement la stratégie d’étiquette de rétention basée sur une [condition](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) et dans la conformité des [communications](communication-compliance.md).