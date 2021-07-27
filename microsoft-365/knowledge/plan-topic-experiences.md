---
title: Planifier les Sujets Microsoft Viva
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: nkokoye
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: MET150
localization_priority: Normal
description: Découvrez comment planifier la Sujets Microsoft Viva
ms.openlocfilehash: bd732edf9d206f6d62ed0cb3040b1d077b1948ca
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53542392"
---
# <a name="plan-for-microsoft-viva-topics"></a>Planifier les Sujets Microsoft Viva

Vous contrôlez la façon dont les sujets sont abordés dans votre organisation. Vos décisions de planification pour Rubriques garantissent que les rubriques de haute qualité sont présentées à vos utilisateurs et qu’ils ont les autorisations nécessaires pour consommer et contribuer aux connaissances.

Dans cet article, nous examinerons les décisions de planification ci-après :

- Les SharePoint sites que vous souhaitez analyser pour les rubriques
- Rubriques, le cas caser, que vous souhaitez exclure des expériences de rubrique
- Utilisateurs pour lesquels vous souhaitez rendre les rubriques visibles
- Utilisateurs que vous souhaitez autoriser à gérer les rubriques dans le centre de rubriques
- Utilisateurs que vous souhaitez autoriser à créer ou modifier des rubriques dans le centre de rubriques
- Quel nom voulez-vous donner à votre centre de rubriques ?

La sécurité et la confidentialité de vos données sont respectées, et les expériences de rubrique n’octroient pas aux utilisateurs un accès supplémentaire aux fichiers dont ils n’ont pas le droit. Nous vous recommandons également de lire Sujets Microsoft Viva [sécurité et confidentialité](topic-experiences-security-privacy.md) dans le cadre de votre processus de planification.

Pour en savoir plus sur la technologie d’IA derrière Topics, consultez La rubrique Sujets Microsoft Viva : du [big data au big knowledge.](https://www.microsoft.com/research/blog/alexandria-in-microsoft-viva-topics-from-big-data-to-big-knowledge)

Gardez à l’esprit que Topics Doit accéder aux sites et fichiers que vos utilisateurs utilisent tous les jours. Le déploiement de rubriques Dans un environnement de test ou de développement peut ne pas produire de résultats utiles.

## <a name="requirements"></a>Conditions requises

Vous devez être [abonné à Rubriques Et](https://www.microsoft.com/microsoft-viva/topics) être administrateur général ou administrateur SharePoint pour accéder à la Centre d’administration Microsoft 365 et configurer Rubriques.

Tous les utilisateurs qui vont utiliser rubriques nécessitent une licence **Expériences de** rubrique. L’attribution de licences est couverte par [la](set-up-topic-experiences.md)Sujets Microsoft Viva .

## <a name="topic-discovery"></a>Découverte de rubrique

Les paramètres de découverte des rubriques spécifient les sites SharePoint utilisés comme sources pour les rubriques. Cela inclut les sites classiques et modernes, ainsi que les sites associés à Microsoft Teams et Microsoft 365 groupes. OneDrive sites ne sont pas inclus.

Vous pouvez choisir d'inclure tous les sites SharePoint, une liste spécifique de sites ou aucun site. Nous vous recommandons de choisir tous les sites afin que les expériences de rubriques puisse découvrir un grand nombre de bonnes rubriques pour vos utilisateurs.

Lorsque vous définissez Rubriques, vous pouvez choisir l’une des options suivantes :

- **Tous les sites** : tous les sites SharePoint dans votre organisation. Cela inclut les sites actuels et futurs.
- **Tous, sauf les sites sélectionnés** : tous les sites à l’exception de ceux que vous spécifiez. Les sites créés à l’avenir seront inclus en tant que sources pour la découverte de rubriques. 
- **Uniquement les sites sélectionnés**: uniquement les sites que vous spécifiez. Les sites créés dans le futur ne seront pas inclus comme sources pour la découverte de rubriques.
- **Aucun site** : n’incluez aucun site SharePoint.

Si vous choisissez **Tous, à** l’exception des sites sélectionnés ou uniquement des **sites** sélectionnés, vous pouvez télécharger un fichier .csv avec une liste de sites. Ces options sont utiles si vous faites un projet pilote et que vous souhaitez inclure un nombre limité de sites à démarrer.

Vous pouvez copier le modèle .csv ci-dessous :

``` csv
Site name,URL
```

Nous vous déconseillons de choisir Aucun **site,** car cela empêche la création ou la mise à jour automatique des rubriques. Toutefois, vous pouvez choisir cette option si vous souhaitez configurer Rubriques, puis ajouter des sites ultérieurement.

Nous vous recommandons de créer un processus pour que les utilisateurs ou les gestionnaires de connaissances demandent que des sites individuels soient supprimés de la découverte de rubriques si nécessaire dans votre organisation.

### <a name="multi-geo"></a>Multi-Géo

Si votre organisation a déployé [Microsoft 365 Multi-Géo,](/microsoft-365/enterprise/microsoft-365-multi-geo)le centre de rubriques est mis en service dans l’emplacement central et seuls les sites SharePoint de l’emplacement central peuvent être utilisés comme sources pour les rubriques. (Si vous sélectionnez **Tous les sites,** Rubriques Topics utilisera tous les sites dans l’emplacement central.)

Tout le traitement et le stockage du contenu sont effectués à l’emplacement central.

## <a name="user-permissions"></a>Autorisations utilisateur

Les autorisations utilisateur que vous spécifiez déterminent les personnes de votre organisation qui interagissent avec les rubriques et ce qu’elles peuvent faire.

> [!Note] 
> Pour l’instant, Topics ne prend pas en charge la fourniture de licences ou d’autorisations utilisateur pour les utilisateurs invités (externes). 

*Gestion des rubriques*

Les gestionnaires de connaissances supervisent la qualité des informations, la façon dont elles sont structurées et d’autres meilleures pratiques au niveau de votre organisation. Ils peuvent confirmer et rejeter des rubriques.

Bien que vous pouvez spécifier des responsables de rubriques individuels, nous vous recommandons de créer un groupe de sécurité (ou d’utiliser un groupe existant) qui contient les personnes que vous souhaitez utiliser comme responsables de connaissances. Vous pouvez spécifier ce groupe de sécurité pendant le processus d’installation.

*Créer et modifier des rubriques.*

Les contributeurs de rubriques sont les champions et les experts techniques de votre organisation. Ils peuvent créer et modifier des rubriques. 

Nous vous recommandons d’autoriser tous les membres de votre organisation à créer et modifier des rubriques, car les expériences de rubrique fonctionnent mieux lorsque tous les utilisateurs peuvent partager des informations.

Si vous souhaitez limiter la création et la modification de rubriques à des personnes ou des groupes spécifiques, créez un groupe de sécurité pour eux et spécifiez-le pendant le processus d’installation.

Vous pouvez choisir de ne permettre à personne de contribuer à des rubriques, mais cela n’est pas recommandé. Les gestionnaires de connaissances pourront toujours modifier et créer des rubriques si vous choisissez cette option.

*Visionneuses de rubriques*

Les visiteurs peuvent voir des informations sur les pages de rubriques, dans les résultats de la recherche et lorsque des rubriques sont mises en surbrillez dans le contenu tel que SharePoint pages. Les utilisateurs peuvent uniquement voir les rubriques découvertes lorsqu’ils ont accès aux fichiers et aux pages dans qui la rubrique a été découverte.

Lors de la configuration des visionneuses de rubriques, vous pouvez choisir parmi :

- **Tous les membres de mon organisation**
- **Personnes ou groupes de sécurité sélectionnés uniquement**
- **Personne**

Nous vous **recommandons tout le monde** dans mon organisation, mais si vous faites un projet pilote, vous pouvez choisir uniquement des personnes ou des groupes de sécurité sélectionnés. Vous pouvez également choisir **Personne** si vous souhaitez configurer Des rubriques, mais ne pas autoriser les personnes à voir les rubriques pour le moment. (Les gestionnaires de connaissances auront toujours accès pour leur permettre d’afficher les rubriques et d’aider à prendre la décision de rendre les rubriques largement disponibles.)

## <a name="knowledge-rules"></a>Règles de connaissance

En tant qu’administrateur, vous pouvez exclure certaines rubriques des expériences de rubrique. Cela est utile si vous souhaitez empêcher les données sensibles d’apparaître dans les rubriques. Bien que les gestionnaires de connaissances peuvent exclure des rubriques dans le centre de rubriques, les rubriques exclues par l’administrateur ne sont même pas visibles pour les gestionnaires de connaissances. (Les gestionnaires de connaissances peuvent également supprimer des rubriques dans le centre de rubriques après la découverte.)

Si vous souhaitez exclure des rubriques au niveau de l’administrateur, vous devez les ajouter à un .csv et télécharger le fichier. Vous pouvez le faire lors de l’installation ou ultérieurement.

Le .csv doit contenir les paramètres suivants :

- **Nom** : tapez le nom de la rubrique à exclure. Il existe deux méthodes pour y parvenir :
- **MatchType-Exact/Partial**: tapez si le nom que vous avez entré était un type de correspondance *exact* *ou* partiel.
    - Correspondance exacte : vous pouvez inclure le nom exact ou l’acronyme (par exemple, *Contoso* ou *ATL*).
    - Correspondance partielle : vous pouvez exclure toutes les rubriques qui ont un mot spécifique.  Par exemple, *arc exclura* toutes les rubriques avec le mot *arc* dans celui-ci, telles que le cercle *d’arc,* *l’arc de Pierre ou* *l’arc de formation*. Notez qu’il n’exclura pas les rubriques dans lesquelles le texte est inclus dans le cadre d’un mot, comme *Architecture*.
- **Signifie (facultatif)**: (également appelé *expansion)* Si vous souhaitez exclure un acronyme, tapez les mots qu’il signifie.

    ![Exclure des rubriques dans le modèle CSV](../media/exclude-topics-csv.png) 

Vous pouvez copier le modèle csv ci-dessous :

``` csv
Name (required),Expansion,MatchType- Exact/Partial (required)
```

## <a name="administration"></a>Administration

Lorsque vous définissez Rubriques, dans le cadre du processus d’installation, un centre de rubriques est automatiquement créé. Réfléchissez à ce que vous souhaitez nommer le centre de rubriques et à ce que doit être l’URL. Vous pouvez définir le nom et l’URL dans le cadre du processus d’installation, et vous pouvez modifier le nom (mais pas l’URL) plus loin dans la Centre d’administration Microsoft 365. Vous ne pouvez avoir qu’un seul centre de rubriques.

## <a name="setup-checklist"></a>Liste de vérification du programme d’installation

Lorsque vous configurerez des expériences de rubrique, vous aurez besoin des éléments suivants à mesure que vous passerez par l’Assistant Installation :

> [!div class="checklist"]
> * La liste des sites à inclure ou à exclure si vous n’incluez pas tous les sites pour la découverte de rubriques
> * Le groupe de sécurité pour les spectateurs des rubriques s’il ne permet pas à tous les utilisateurs d’afficher les rubriques
> * Le groupe de sécurité pour les contributeurs de rubriques s’il ne permet pas à tous les utilisateurs de créer et de modifier des rubriques
> * Le groupe de sécurité pour les gestionnaires des connaissances pour les rubriques s’il ne permet pas à tous les utilisateurs de gérer les rubriques
> * Liste des rubriques sensibles à exclure de la découverte de rubriques
> * Nom de votre site centre de rubriques

## <a name="see-also"></a>Voir aussi

[Configurer les expériences de sujets](set-up-topic-experiences.md)

[Gérer la découverte de rubriques dans Microsoft 365](topic-experiences-discovery.md)

[Gérer la visibilité des rubriques dans Microsoft 365](topic-experiences-knowledge-rules.md)

[Gérer les autorisations de rubrique dans Microsoft 365](topic-experiences-user-permissions.md)

[Modifier le nom du centre de rubriques dans Microsoft 365](topic-experiences-administration.md)
