---
title: Prise en main des classificateurs de formation (préversion)
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
description: Un classificateur Microsoft 365 est un outil que vous pouvez former afin de reconnaître différents types de contenu en leur donnant des exemples à consulter. Cet article vous explique comment créer et former un classifieur personnalisé et comment le former pour améliorer la précision.
ms.openlocfilehash: fd6bc68a8bc373d9d02e23b73971b28ce8761cd9
ms.sourcegitcommit: fdb5f9d865037c0ae23aae34a5c0f06b625b2f69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "48132335"
---
# <a name="get-started-with-trainable-classifiers-preview"></a>Prise en main des classificateurs de formation (préversion)

Un classificateur Microsoft 365 pouvant être formé est un outil que vous pouvez former afin de reconnaître différents types de contenu en leur donnant des exemples à consulter. Une fois l’apprentissage effectué, vous pouvez l’utiliser pour identifier un élément pour l’application des étiquettes de sensibilité d’Office, des stratégies de conformité des communications et des stratégies d’étiquette de rétention.

La création d’un classificateur de formation personnalisée implique d’abord de donner aux échantillons prélevés par des personnes et correspondant à la catégorie. Ensuite, une fois qu’il les a traités, vous testez la capacité des classifieurs à les prédire en leur donnant un mélange d’échantillons positifs et négatifs. Cet article vous explique comment créer et former un classificateur personnalisé et comment améliorer les performances des classifieurs de formation personnalisée et des classifieurs préformés pendant leur durée de formation.

Pour en savoir plus sur les différents types de classifieurs, voir [en savoir plus sur les classifieurs de formation (aperçu)](classifier-learn-about.md).

## <a name="prerequisites"></a>Conditions préalables

### <a name="licensing-requirements"></a>Critères de licence

Les classifieurs sont une fonctionnalité de conformité de Microsoft 365 E5 ou E5. Vous devez disposer de l’un de ces abonnements pour pouvoir les utiliser.

### <a name="permissions"></a>Autorisations

Pour accéder aux classifieurs dans l’interface utilisateur : 

- l’administrateur global doit s’abonner au client pour créer des classifieurs personnalisés
- le rôle d’administrateur de conformité ou l’administrateur des données de conformité est requis pour former un classifieur

Vous aurez besoin de comptes dotés des autorisations suivantes pour utiliser les classifieurs dans les scénarios suivants :

- Scénario de stratégie d’étiquette de rétention : rôles de gestion des enregistrements et de rétention 
- Scénario de stratégie d’étiquette de confidentialité : administrateur de sécurité, administrateur de conformité, administrateur de données de conformité
- Scénario de stratégie de conformité des communications : administrateur de gestion des risques Insiders, administrateur de vérification de la surveillance 

> [!IMPORTANT]
> Par défaut, seul l’utilisateur qui crée un classifieur personnalisé peut former et examiner les prévisions effectuées par ce classifieur. Si vous souhaitez que d’autres personnes puissent former et passer en revue les prévisions de classifieur, consultez la rubrique [accorder à d’autres personnes les droits de formation et de révision](#give-others-train-and-review-rights).

## <a name="prepare-for-a-custom-trainable-classifier"></a>Préparer un classificateur de formation personnalisée 

Il est utile de comprendre ce qui est impliqué dans la création d’un classificateur de formation personnalisée avant de vous plonger dans. 

### <a name="timeline"></a>Chronologie

Cette chronologie reflète un exemple de déploiement de classifieur de formation.

![formation de classifieur-chronologie](../media/trainable-classifier-deployment-timeline_border.png)

> [!TIP]
> L’option opt-in est requise pour la première fois pour les classifieurs de formation. Il faut douze jours pour que Microsoft 365 effectue une évaluation de base du contenu de votre organisation. Contactez votre administrateur général pour lancer le processus d’abonnement.

### <a name="overall-workflow"></a>Flux de travail global

Pour en savoir plus sur le flux de travail général de création de classifieurs de formation personnalisée, voir [Flow Process for Creating Customer trainable Classifiers](classifier-learn-about.md#process-flow-for-creating-custom-classifiers)

### <a name="seed-content"></a>Contenu de départ

Si vous souhaitez qu’un classifieur puisse identifier de manière indépendante et précise un élément comme étant dans une catégorie particulière de contenu, vous devez d’abord le présenter avec de nombreux exemples du type de contenu qui se trouve dans la catégorie. Cette alimentation d’échantillons vers le classificateur peut être qualifiée d' *amorçage*. Le contenu de départ est sélectionné par un humain et est jugé pour représenter la catégorie de contenu.

> [!TIP]
> Vous devez avoir au moins 50 échantillons positifs et un maximum de 500. Le classificateur pouvant être mis en place traitera jusqu’à 500 exemples de création les plus récents (par date et heure de création du fichier). Plus le nombre d’exemples que vous fournissez est précis, plus les prévisions seront précises.

### <a name="testing-content"></a>Test du contenu

Une fois que le classifieur peut traiter suffisamment d’échantillons positifs pour créer un modèle de prévision, vous devez tester les prévisions qu’il permet de déterminer si le classifieur peut faire la distinction entre les éléments qui correspondent à la catégorie et ceux qui ne l’ont pas. Pour ce faire, vous devez l’alimenter un autre ensemble de contenu choisi par l’homme qui se compose d’exemples qui doivent être inclus dans la catégorie et les échantillons qui ne le seront pas. Une fois qu’il les traite, vous parcourez manuellement les résultats et vérifiez si chaque prévision est correcte, incorrecte ou si vous n’êtes pas sûr. Le classificateur de formation utilise ces commentaires pour améliorer son modèle de prévision.

> [!TIP]
> Pour obtenir de meilleurs résultats, vous devez avoir au moins 200 éléments dans votre jeu d’échantillons de test avec une répartition égale des correspondances positives et négatives.

## <a name="how-to-create-a-trainable-classifier"></a>Procédure de création d’un classifieur de formation

1. Collect entre les éléments de contenu Seed 50-500. Il doit s’agir uniquement d’exemples qui représentent fortement le type de contenu que vous souhaitez que le classifieur peut identifier de manière positive comme appartenant à la catégorie de classification. Pour connaître les types de fichiers pris en charge, reportez-vous aux [extensions de nom de fichier et aux types de fichiers analysés par défaut dans SharePoint Server](https://docs.microsoft.com/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) .

> [!IMPORTANT]
> Les éléments de l’exemple Seed et test ne doivent pas être chiffrés et doivent être en anglais.

> [!IMPORTANT]
> Assurez-vous que les éléments de votre ensemble Seed sont des exemples **forts** de la catégorie. Le classificateur de formation génère initialement son modèle en fonction de ce que vous amorcez avec. Le classifieur part du principe que tous les échantillons de départ sont des positifs forts et n’ont aucun moyen de savoir si un échantillon est une correspondance faible ou négative avec la catégorie.

2. Placez le contenu Seed dans un dossier SharePoint Online dédié au maintien *du contenu de l’amorçage uniquement*. Notez l’URL du site, de la bibliothèque et du dossier.

> [!TIP]
> Si vous créez un nouveau site et dossier pour vos données de départ, autorisez au moins une heure pour cet emplacement à indexer avant de créer le classifieur qui utilisera ces données de départ.

3. Connectez-vous au centre de conformité Microsoft 365 avec l’administrateur de conformité ou l’accès au rôle d’administrateur de sécurité et ouvrez le **Centre de conformité Microsoft 365 ou la** classification des données du centre de **sécurité Microsoft 365**  >  **Data classification**

4. Sélectionnez l’onglet **classeurs de formation** .

5. Sélectionnez **Create Training classificateur**.

6. Renseignez les valeurs appropriées pour les `Name` `Description` champs de la catégorie d’éléments que vous souhaitez que le classifieur pouvant identifier.

7. Sélectionnez l’URL du site, de la bibliothèque et du dossier SharePoint Online pour le site de contenu Seed à partir de l’étape 2. Choisissez `Add` .

8. Passez en revue les paramètres, puis choisissez `Create trainable classifier` .

9. Dans les 24 heures, le classificateur peut traiter les données de départ et créer un modèle de prévision. L’état du classifieur est `In progress` en cours de traitement des données de l’amorçage. Lorsque le classificateur a terminé le traitement des données de départ, l’État devient `Need test items` .

10. Vous pouvez désormais afficher la page de détails en choisissant le classifieur.


![classificateur prêt à être testé](../media/classifier-trainable-ready-to-test-detail.png)

11. Collectez au moins 200 éléments de contenu de test (10 000 max) pour obtenir de meilleurs résultats. Il doit s’agir d’un mélange d’éléments qui sont des positifs forts, de fortes négatifs et d’autres moins évidents dans leur nature. Pour connaître les types de fichiers pris en charge, reportez-vous aux [extensions de nom de fichier et aux types de fichiers analysés par défaut dans SharePoint Server](https://docs.microsoft.com/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) .

> [!IMPORTANT]
> Les éléments de l’exemple ne doivent pas être chiffrés et doivent être en anglais.

12. Placez le contenu de test dans un dossier SharePoint Online dédié à la conservation *du contenu de test uniquement*. Notez le site SharePoint Online, la bibliothèque et l’URL du dossier.

> [!TIP]
> Si vous créez un nouveau site et dossier pour vos données de test, autorisez au moins une heure pour cet emplacement à indexer avant de créer le classifieur qui utilisera ces données de départ.

13. Choisissez `Add items to test` .

14. Sélectionnez l’URL du site, de la bibliothèque et du dossier SharePoint Online pour le site de contenu de test à partir de l’étape 12. Choisissez `Add` .

15. Terminez l’Assistant en sélectionnant `Done` . Votre classificateur peut prendre jusqu’à une heure pour traiter les fichiers de test.

16. Lorsque le classificateur de formation est fini de traiter vos fichiers de test, l’État sur la page des détails prend la forme `Ready to review` . Si vous devez augmenter la taille de l’échantillon de test, choisissez `Add items to test` et autorisez le classificateur en train de traiter les éléments supplémentaires.

![capture d’écran prêt à examiner](../media/classifier-trainable-ready-to-review-detail.png)

17. Choisissez `Tested items to review` Tab pour passer en revue les éléments.

18. Microsoft 365 présente 30 éléments à la fois. Vérifiez-les et, dans la `We predict this item is "Relevant". Do you agree?` zone, choisissez `Yes` ou `No` ou `Not sure, skip to next item` . La précision du modèle est automatiquement mise à jour après 30 éléments.

![zone passer en revue les éléments](../media/classifier-trainable-review-detail.png)

19. Passez *en revue au moins* 200 éléments. Une fois le score de précision stabilisé, l’option **publier** devient disponible et l’état du classifieur indique `Ready to use` .

![score de précision et prêt à publier](../media/classifier-trainable-review-ready-to-publish.png)

20. Publiez le classifieur.

21. Une fois publié, votre classifieur sera disponible sous forme de condition dans [Office auto-étiquetage avec les étiquettes de confidentialité](apply-sensitivity-label-automatically.md), [appliquant automatiquement la stratégie d’étiquette de rétention en fonction d’une condition](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) et de [la conformité de la communication](communication-compliance.md).

## <a name="give-others-train-and-review-rights"></a>Donner aux autres les droits de formation et de révision

Utilisez cette procédure pour donner aux autres autorisations pour former, examiner et ajuster votre classificateur personnalisé.  
 
1. En tant que créateur du classifieur, un administrateur général ou un administrateur eDiscovery se connecte au centre de conformité à l’aide de PowerShell à l’aide des procédures décrites dans [Connect to Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell?view=exchange-ps&preserve-view=true).
2. Ensuite, exécutez la commande suivante :
```powershell
Add-ComplianceCaseMember -Case "<classifier name>" -Member "<user or role group>"
```
Par exemple : `Add-ComplianceCaseMember -Case "Financial Contract Classifier" -Member johnevans@contoso.com`

Vous pouvez exécuter cette commande plusieurs fois pour ajouter plusieurs utilisateurs. Notez que vous pouvez uniquement ajouter des groupes de rôles Exchange Online Protection (EOP) et non des groupes de rôles Azure.
