---
title: Exécuter une version d’Sujets Microsoft Viva
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris; jaeccles
ms.date: ''
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.custom: ''
search.appverid: ''
localization_priority: Normal
description: Découvrez comment planifier et exécuter un programme pilote d’essai pour Sujets Microsoft Viva votre organisation.
ms.openlocfilehash: 783c84e0b7d14c51269672bc49902f02bdedd0e3
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59181132"
---
# <a name="run-a-trial-of-microsoft-viva-topics"></a>Exécuter une version d’Sujets Microsoft Viva

Cet article explique comment configurer et exécuter un programme pilote d’essai pour déployer Topics dans votre organisation. Cet article recommande également les meilleures pratiques pour la version d’essai.

## <a name="sign-up-for-a-trial"></a>S’inscrire à une version d’essai

Les essais sont disponibles publiquement à partir de l’une des sources suivantes. Ces essais d’essai offrent à 25 utilisateurs l’accès aux rubriques Topics pendant 30 jours.

- Page [Du produit Rubriques](https://www.microsoft.com/microsoft-viva/topics?activetab=pivot:overviewtab)

- Le [Centre d'administration Microsoft 365](https://admin.microsoft.com)
    1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com).
    2. Go to **Billing**  >  **Purchase Services**.
    3. Faites défiler la page vers le bas jusqu’à la section **Modules complémentaires**.
    4. Dans la vignette **Expériences des** **rubriques, sélectionnez Détails.**
    5. Sélectionnez **Obtenir un essai gratuit**.
    6. Suivez les étapes restantes de l’Assistant pour confirmer la version d’essai.

Vous devez être un administrateur Microsoft 365 général ou un administrateur de facturation pour activer une version d’essai.

> [!NOTE]
> Les essais publics ne peuvent être ajoutés qu’une seule fois pour Microsoft 365 client.

### <a name="who-should-be-involved-in-a-trial"></a>Qui doivent être impliquées dans une version d’essai

|Rôle|Activité|
|---|---|
|Microsoft 365 administrateur global ou administrateur de facturation|Activer la version d’essai et attribuer des licences|
|Microsoft 365 administrateur global ou administrateur SharePoint administrateur|Configurer des rubriques Et créer des centres de rubriques|
|Utilisateur commercial|Effectuer des rôles de gestionnaire de connaissances, de collaborateur de rubriques et de consommateur de rubriques|

### <a name="before-you-activate-a-trial"></a>Avant d’activer une version d’essai

La planification est essentielle pour une version d’essai efficace de Topics. La période d’essai est limitée et doit inclure la découverte et l’exploration de la qualité, de la gestion et des expériences des utilisateurs finux.

#### <a name="discovery"></a>Discovery

Il existe deux options de stratégie de haut niveau pour la configuration de la découverte de sujets au cours d’une version d’essai :

- Indexez l’ensemble ou la majeure partie SharePoint contenu en ligne.
  - L’indexation complète des locataires importants peut prendre jusqu’à deux semaines. Bien que les rubriques soient générées de manière incrémentielle tout au long de cette période, l’indexation complète peut consommer jusqu’à la moitié de la période d’essai.
  - Pour les clients avec un volume important de données, cette option peut produire un très grand nombre de rubriques, voire des dizaines de milliers.

- Identifiez un sous-ensemble de vos sites SharePoint à indexer.

Le choix de ces stratégies est un équilibre entre les deux facteurs suivants :

- Suffisamment de données pour générer des rubriques significatives. L’IA de Topics est mise au point pour fonctionner sur des jeux de données de grande taille, dans l’idéal ceux qui ont plus de 10 000 documents.
- Le fait de ne pas générer autant de rubriques pendant la période d’évaluation que leur évaluation pendant la période disponible est difficile.

Pour la plupart des organisations, la deuxième stratégie produit le meilleur résultat.

> [!NOTE]
> En raison du nombre de documents requis par l’IA, nous vous recommandons d’exécuter des essais de Rubriques Dans le cas d’un client de production. Il n’y a aucun impact sur les performances du client pendant cette période. Seuls les utilisateurs titulaires d’une licence d’essai peuvent accéder aux expériences des utilisateurs de Topics.

#### <a name="roles"></a>Rôles

Au cours de la version d’essai, trois rôles doivent être actifs, qui sont décrits dans le tableau suivant.

|Rôle|Activité|
|---|---|
|Gestionnaire des connaissances|Contrôler les étapes du cycle de vie des rubriques ; confirmer et supprimer des rubriques ; agir en tant que gestionnaire de communauté pour les collaborateurs de rubriques ;|
|Contributeur de rubrique|Experts techniques du contenu, qui peuvent :<br> Examiner les rubriques pour évaluer la qualité du contenu défini par l’IA<br>Organiser des rubriques découvertes avec du contenu supplémentaire<br>Créer des rubriques supplémentaires qui n’ont pas été découvertes par l’IA|
|Consommateur de rubriques|Utiliser des rubriques par le biais des points forts de la page et de la recherche<br>Fournir des commentaires sur la valeur des rubriques présentées|

#### <a name="expected-topics"></a>Rubriques attendues

Il peut être utile de documenter les rubriques que vous prévoyez d’être générées par l’IA, même si cela est basé uniquement sur des hypothèses. Cette tâche est plus facile à accomplir lorsque vous indexez un sous-ensemble défini de vos sites SharePoint pour lesquels les PME peuvent être identifiées facilement.

Le fait de disposer d’une liste documentée vous aidera à :

- Examinez la liste des rubriques générées par l’IA, qui peuvent être plus volumineuses que prévu.
- Connaissez les rubriques que vous devrez peut-être créer manuellement ou qui sont des priorités pour la curation.

Vous aurez toujours besoin d’une combinaison de rubriques définies par l’IA et de rubriques créées par l’être humain dans le cas d’un déploiement ou d’une version d’essai réussi de Topics.

## <a name="activate-a-trial"></a>Activer une version d’essai

Lorsque vous lancez une version d’essai, vous devez :

- Attribuez des licences aux utilisateurs concernés.
- Effectuez [une configuration](set-up-topic-experiences.md) supplémentaire de Rubriques.

Lorsque la version d’évaluation est activée, le processus de découverte de sujet commence.

## <a name="during-a-trial"></a>Pendant une version d’essai

La période d’évaluation doit être utilisée pour évaluer les composants suivants de Topics :

- Rubriques suggérées par l’IA et contenu de rubrique
- Expériences de l’utilisateur final, avec l’utilisation de cartes de sujet sur des pages SharePoint modernes et dans Recherche Microsoft

Tenez compte de ces facteurs :

- Pour que Topics offre la valeur maximale, le contenu des rubriques doit être une combinaison de contenu défini par l’IA et de contenu organisé par l’être humain.
- Toutes les expériences utilisateur sont « découpées en autorisations » (y compris l’affichage du gestionnaire de connaissances sur la page Gérer **les rubriques).** Les utilisateurs ne voient une rubrique que s’ils sont autorisés à afficher certaines des ressources qui ont été utilisées pour générer la rubrique. Cela signifie que différents utilisateurs peuvent voir un contenu différent sur la même page de rubrique.
- Les utilisateurs peuvent voir plusieurs rubriques qui ont le même nom dans la page **Gérer les rubriques.** Ces rubriques ne sont pas nécessairement des doublons, mais peuvent être dues à un seul terme utilisé dans plusieurs contextes dans les données, comme un nom de code de projet utilisé par deux projets distincts.

## <a name="after-a-trial"></a>Après une version d’essai

En fonction du résultat de la version d’essai, vous pouvez décider s’il faut passer à l’utilisation en production de Topics.

### <a name="proceed-to-production-use"></a>Passer à l’utilisation de la production

Pour garantir la continuité du service, vous devez acheter le nombre requis de licences et les attribuer aux utilisateurs. Les utilisateurs avec une version d’évaluation qui ne disposent pas d’une licence complète à la fin de la période d’essai ne pourront accéder à aucune expérience Rubriques Viva.

### <a name="dont-proceed-to-production-use"></a>Ne pas passer à l’utilisation en production

Si vous n’achetez pas de licences à la suite de la version d’essai :

- La découverte de rubrique s’arrête.
- Les utilisateurs ne voient plus les points forts ou les cartes des rubriques.
- Le centre de rubriques ne sera pas supprimé, mais les rubriques suggérées et les expériences de gestion des rubriques ne seront pas disponibles.
- Toutes les rubriques définies par l’IA seront perdues.
- Les rubriques qui ont été modifiées par un collaborateur de rubrique resteront dans la bibliothèque de pages du centre de rubriques. Seul le contenu fourni manuellement reste sur ces pages, pas sur tout contenu suggéré par l’IA.

## <a name="see-also"></a>Voir aussi

[Commencer à piloter l’adoption de Sujets Microsoft Viva](topics-adoption-getstarted.md)
