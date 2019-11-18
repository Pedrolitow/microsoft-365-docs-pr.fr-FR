---
title: Créer un classifieur de formation (aperçu)
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Utilisez des classifieurs adaptés lorsque l’un des classifieurs de zone prêt à l’emploi ne répond pas à vos besoins. Un classificateur Microsoft 365 est un outil que vous pouvez former afin de reconnaître différents types de contenu en leur donnant des exemples à consulter. Cette rubrique vous montre comment créer un classifieur personnalisé.
ms.openlocfilehash: 1d62b70d821593ff7d8d3889c0da0e0b5cc9809f
ms.sourcegitcommit: 9ee873c6a2f738a0c99921e036894b646742e706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2019
ms.locfileid: "38690417"
---
# <a name="creating-a-trainable-classifier-preview"></a>Création d’un classifieur de formation (aperçu)

Utilisez des classifieurs adaptés lorsque l’un des classifieurs de la zone ne répond pas à vos besoins. Un classificateur Microsoft 365 est un outil que vous pouvez former afin de reconnaître différents types de contenu en leur donnant des exemples à consulter. Formation le classificateur implique d’abord de donner aux échantillons prélevés par des personnes et correspondant à la catégorie positive. Ensuite, une fois qu’il les a traités, vous testez les prévisions en lui donnant un mélange d’échantillons positifs et négatifs.

Pour en savoir plus sur les différents types de classifieurs, voir [Getting Started with trainable Classifiers (Preview)](classifier-getting-started-with.md)

Cette chronologie reflète un exemple de déploiement.

![formation de classifieur-chronologie](media/trainable-classifier-deployment-timeline_border.png)

## <a name="seed-content"></a>Contenu de départ

Si vous souhaitez qu’un classifieur puisse identifier de manière indépendante et précise un élément comme étant dans une catégorie particulière de contenu, vous devez d’abord le présenter avec de nombreux exemples du type de contenu qui se trouve dans la catégorie. Cette alimentation d’échantillons vers le classificateur peut être qualifiée d' *amorçage*. Le contenu de départ est sélectionné par un humain et est jugé pour représenter la catégorie de contenu.

> [!TIP]
> Vous devez avoir au moins 50 échantillons positifs et un maximum de 500. Le classificateur pouvant être mis en place traitera jusqu’à 500 exemples de création les plus récents (par date et heure de création du fichier). Plus le nombre d’exemples que vous fournissez est précis, plus les prévisions seront précises.

## <a name="testing-content"></a>Test du contenu

Une fois que le classifieur peut traiter suffisamment d’échantillons positifs pour créer un modèle de prévision, vous devez tester les prévisions qu’il permet de déterminer si le classifieur peut faire la distinction entre les éléments qui correspondent à la catégorie et ceux qui ne le sont pas. Pour ce faire, vous devez l’alimenter un autre ensemble de contenu choisi par l’homme qui se compose d’exemples qui doivent être inclus dans la catégorie et les échantillons qui ne le seront pas. Une fois qu’il les traite, vous parcourez manuellement les résultats et vérifiez si chaque prévision est correcte, incorrecte ou si vous n’êtes pas sûr. Le classificateur de formation utilise ces commentaires pour améliorer son modèle de prévision.

> [!TIP]
> Pour obtenir de meilleurs résultats, comportez 10 000 éléments dans votre jeu d’échantillons de test avec une répartition égale des correspondances positives et négatives.

> [!TIP]
> L’option opt-in est requise pour la première fois pour les classifieurs de formation. Il faut douze jours pour que Microsoft 365 effectue une évaluation de base du contenu de votre organisation.

## <a name="how-to-create-a-trainable-classifier"></a>Procédure de création d’un classifieur de formation

1. Collect entre les éléments de contenu Seed 50-500. Il doit s’agir uniquement d’exemples qui représentent fortement le type de contenu que vous souhaitez que le classifieur peut identifier de manière positive comme appartenant à la catégorie de classification. Pour connaître les types de fichiers pris en charge, reportez-vous aux [extensions de nom de fichier et aux types de fichiers analysés par défaut dans SharePoint Server](https://docs.microsoft.com/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) .

> [!IMPORTANT]
> Les éléments de l’exemple Seed et test ne doivent pas être chiffrés et doivent être en anglais.

> [!IMPORTANT]
> Assurez-vous que les éléments de votre ensemble Seed sont des exemples **forts** de la catégorie. Le classificateur de formation génère initialement son modèle en fonction de ce que vous amorcez avec. Le classifieur part du principe que tous les échantillons de départ sont des positifs forts et n’ont aucun moyen de savoir si un échantillon est une correspondance faible ou négative avec la catégorie.

2. Placez le contenu Seed dans un dossier SharePoint Online dédié au maintien *du contenu de l’amorçage uniquement*. Notez l’URL du site, de la bibliothèque et du dossier.

> [!TIP]
> Si vous créez un nouveau site et dossier pour vos données de départ, autorisez au moins une heure pour cet emplacement à indexer avant de créer le classifieur qui utilisera ces données de départ.

3. Connectez-vous au centre de conformité Microsoft 365 avec l’administrateur de conformité ou l’accès au rôle d’administrateur de sécurité et ouvrez le **Centre de conformité Microsoft 365 ou la** classification des**données** du centre > de **sécurité Microsoft 365**

4. Sélectionnez l’onglet **classeurs de formation** .

5. Sélectionnez **Create Training classificateur**.

6. Renseignez les valeurs appropriées pour `Name`les `Description` champs de la catégorie d’éléments que vous souhaitez que le classifieur pouvant identifier.

7. Entrez l’URL du site, de la bibliothèque et du dossier SharePoint Online exactes pour le site de contenu Seed à partir de l’étape 2. Choisissez `Add`.

8. Passez en revue les paramètres `Create trainable classifier`, puis choisissez.

9. Dans les 24 heures, le classificateur peut traiter les données de départ et créer un modèle de prévision. L’état du classifieur est `In progress` en cours de traitement des données de l’amorçage. Lorsque le classificateur a terminé le traitement des données de départ, l’état `Need test items`devient.

10. Vous pouvez désormais afficher la page de détails en choisissant le classifieur.


![classificateur prêt à être testé](media/classifier-trainable-ready-to-test-detail.png)

11. Collectez au moins 200 éléments de contenu de test. Microsoft recommande 10 000 pour obtenir de meilleurs résultats. Il doit s’agir d’un mélange d’éléments qui sont des positifs forts, de fortes négatifs et d’autres moins évidents dans leur nature. Pour connaître les types de fichiers pris en charge, reportez-vous aux [extensions de nom de fichier et aux types de fichiers analysés par défaut dans SharePoint Server](https://docs.microsoft.com/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) .

> [!IMPORTANT]
> Les éléments de l’exemple ne doivent pas être chiffrés et doivent être en anglais.

12. Placez le contenu de test dans un dossier SharePoint Online dédié à la conservation *du contenu de test uniquement*. Notez le site SharePoint Online, l’URL de bibliothèque et de dossier.

> [!TIP]
> Si vous créez un nouveau site et dossier pour vos données de test, autorisez au moins une heure pour cet emplacement à indexer avant de créer le classifieur qui utilisera ces données de départ.

13. Choisissez `Add items to test`.

14. Entrez l’URL du site SharePoint Online, de la bibliothèque et du dossier exactes pour le site de contenu de test à partir de l’étape 12. Choisissez `Add`.

15. Terminez l’Assistant en `Done`sélectionnant. Votre classificateur peut prendre jusqu’à une heure pour traiter les fichiers de test.

16. Lorsque le classificateur de formation est fini de `Ready to review`traiter vos fichiers de test, l’État sur la page des détails prend la forme. Si vous devez augmenter la taille de l’échantillon de test `Add items to test` , choisissez et autorisez le classificateur en train de traiter les éléments supplémentaires.

![capture d’écran prêt à examiner](media/classifier-trainable-ready-to-review-detail.png)

17. Choisissez `Tested items to review` Tab pour passer en revue les éléments.

18. Microsoft 365 présente 30 éléments à la fois. Vérifiez-les et, `We predict this item is "Relevant". Do you agree?` dans la zone `Yes` , `No` choisissez `Not sure, skip to next item`ou ou. La précision du modèle est automatiquement mise à jour après 30 éléments.

![zone passer en revue les éléments](media/classifier-trainable-review-detail.png)

19. Passez *en revue au moins* 200 éléments.

20. Continuez à passer en revue jusqu’à ce que la précision atteigne `Publish the classifier` au moins `Ready to use`70% et que l’État est.

![précision et prêt à publier](media/classifier-trainable-review-ready-to-publish.png)

21. Publiez le classifieur.

22. Une fois publié, votre classifieur est disponible sous forme de condition dans la [stratégie d’attribution automatique d’étiquette de rétention basée sur une condition](labels.md#applying-a-retention-label-automatically-based-on-conditions) et [la conformité de communication](communication-compliance.md).

> [!CAUTION]
> Une fois qu’un classifieur est publié, il ne peut pas passer par une formation supplémentaire, nous vous recommandons donc de tester et de réviser autant d’éléments que possible afin de vous assurer que la précision est la plus élevée possible.

## <a name="see-also"></a>Voir aussi

- [Prise en main des classificateurs de formation (préversion)](classifier-getting-started-with.md)
- [Extensions de nom de fichier et types de fichier analysés par défaut dans SharePoint Server](https://docs.microsoft.com/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
