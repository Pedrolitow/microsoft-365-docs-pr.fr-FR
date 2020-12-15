---
title: Planification des expériences de rubrique dans Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: nkokoye
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: MET150
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment planifier des expériences de rubrique dans Microsoft 365
ms.openlocfilehash: 153937cf6bc4a12f0a27866204b2286c343ddf55
ms.sourcegitcommit: 1a9f0f878c045e1ddd59088ca2a94397605a242a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "49668155"
---
# <a name="plan-topic-experiences-in-microsoft-365"></a>Planification des expériences de rubrique dans Microsoft 365

Vous contrôlez le mode d’expérience des rubriques dans votre organisation. Vos décisions de planification pour les expériences de rubrique permettent de s’assurer que des rubriques de qualité supérieure sont affichées pour vos utilisateurs et qu’ils disposent des autorisations appropriées pour utiliser et contribuer aux connaissances.

Dans cet article, nous allons examiner les décisions de planification suivantes :

- Les sites SharePoint que vous souhaitez analyser.
- Les rubriques, le cas échéant, que vous souhaitez exclure des expériences de rubrique
- Les utilisateurs auxquels vous souhaitez faire apparaître les rubriques.
- Les utilisateurs auxquels vous souhaitez accorder des autorisations pour gérer les rubriques dans le Centre des rubriques.
- Les utilisateurs auxquels vous souhaitez accorder des autorisations pour créer ou modifier des rubriques dans le Centre des rubriques.
- Le nom que vous souhaitez donner à votre centre de sujets.

La sécurité et la confidentialité de vos données sont respectées, et les expériences de rubrique n’accordent pas aux utilisateurs un accès supplémentaire aux fichiers auxquels ils ne disposent pas de droits. Nous vous recommandons également de lire la [rubrique relative à la sécurité et](topic-experiences-security-privacy.md) à la confidentialité dans le cadre de votre processus de planification.

## <a name="requirements"></a>Configuration requise

Vous devez être un administrateur général ou un administrateur SharePoint pour accéder au centre d’administration Microsoft 365 et configurer des expériences de rubrique.

Tous les utilisateurs qui vont utiliser des expériences de rubrique requièrent une **rubrique relative** aux licences. Pour affecter des licences, reportez-vous à la [rubrique relative à la configuration des expériences](set-up-topic-experiences.md).

## <a name="topic-discovery"></a>Découverte de rubrique

Les paramètres de découverte de rubrique spécifient les sites SharePoint qui sont utilisés comme sources pour les rubriques. Vous pouvez choisir d’inclure tous les sites SharePoint, une liste spécifique de sites ou aucun site. Nous vous recommandons de choisir tous les sites de sorte que les expériences de rubrique puissent découvrir un grand nombre de rubriques intéressantes pour vos utilisateurs.

Lorsque vous configurez des expériences de rubrique, vous pouvez choisir l’une des options suivantes :

- **Tous les sites**: tous les sites SharePoint de votre organisation. Cela inclut les sites actuels et futurs.
- **Tout, à l’exception des sites sélectionnés**: tous les sites à l’exception de ceux que vous spécifiez. Les sites créés à l’avenir seront inclus en tant que sources pour la découverte des rubriques. 
- **Sites sélectionnés uniquement**: uniquement les sites que vous spécifiez. Les sites créés à l’avenir ne seront pas inclus en tant que sources pour la découverte des rubriques.
- **Aucun site**: n’inclut aucun site SharePoint.

Si vous choisissez **tous, à l’exception des sites sélectionnés** ou des **sites sélectionnés uniquement**, vous pouvez télécharger un fichier. csv avec une liste de sites. Ces options sont utiles si vous effectuez un projet pilote et si vous souhaitez inclure un nombre limité de sites à démarrer.

Vous pouvez copier le modèle. csv ci-dessous :

``` csv
Site name,URL
```

Nous vous déconseillons de ne pas choisir de **sites** , car cela empêche la création ou la mise à jour automatique des rubriques. Toutefois, vous pouvez choisir cette option si vous souhaitez configurer des expériences de rubrique, puis ajouter des sites ultérieurement.

Nous vous recommandons de créer un processus pour les utilisateurs ou les responsables de la connaissance afin de demander la suppression des sites individuels de la découverte de rubrique, si nécessaire dans votre organisation.

## <a name="user-permissions"></a>Autorisations utilisateur

Les autorisations utilisateur que vous spécifiez déterminent les personnes de votre organisation qui interagissent avec des rubriques et ce qu’elles peuvent faire.

*Gérer les rubriques*

Les responsables des connaissances supervisent la qualité des informations, la façon dont ils sont structurés et d’autres meilleures pratiques au sein de votre organisation. Ils peuvent confirmer et rejeter des rubriques.

Bien que vous puissiez spécifier des gestionnaires de rubriques spécifiques, nous vous recommandons de créer un groupe de sécurité (ou d’utiliser un groupe existant) qui contient les personnes que vous voulez désigner comme responsables du savoir. Vous pouvez spécifier ce groupe de sécurité pendant le processus d’installation.

*Créer et modifier des rubriques*

Les contributeurs de rubrique sont les champions et les experts techniques de votre organisation. Ils peuvent créer et modifier des rubriques. 

Nous vous recommandons de permettre à tous les membres de votre organisation de créer et de modifier des rubriques, car les expériences de rubrique sont meilleures lorsque tous les utilisateurs peuvent partager des informations.

Si vous souhaitez limiter la création et la modification des rubriques à des personnes ou des groupes spécifiques, créez un groupe de sécurité pour ceux-ci et spécifiez-le pendant le processus d’installation.

Vous pouvez choisir de ne pas autoriser quiconque à contribuer aux rubriques, mais cela n’est pas recommandé. Les responsables de la connaissance seront toujours en mesure de modifier et de créer des rubriques.

*Visionneuses de rubrique*

Les visionneuses de rubrique peuvent afficher des informations sur les pages de rubrique, dans les résultats de recherche et lorsque des rubriques sont mises en surbrillance dans le contenu comme les pages SharePoint. Les utilisateurs peuvent uniquement voir les rubriques découvertes lorsqu’ils ont accès aux fichiers et aux pages sur lesquels la rubrique a été découverte.

Lorsque vous configurez des visionneuses de rubrique, vous pouvez choisir parmi les éléments suivants :

- **Tous les membres de mon organisation**
- **Uniquement les personnes ou les groupes de sécurité sélectionnés**
- **Personne**

Nous recommandons **tout le monde au sein de mon organisation**, mais si vous effectuez un test pilote, vous pouvez choisir uniquement des personnes ou des groupes de sécurité sélectionnés. Vous pouvez également choisir **personne** si vous souhaitez configurer des expériences de rubrique, mais ne pas autoriser les utilisateurs à voir les rubriques. (Les gestionnaires de connaissances auront toujours accès pour leur permettre d’afficher les rubriques et d’aider à la décision de rendre les expériences de rubrique largement disponibles.)

## <a name="knowledge-rules"></a>Règles de connaissances

En tant qu’administrateur, vous pouvez exclure certaines rubriques de la rubrique expériences. Cela est utile si vous souhaitez que les données sensibles ne s’affichent pas dans les rubriques. Alors que les gestionnaires de connaissances peuvent exclure des rubriques dans le Centre des rubriques, les rubriques exclues par l’administrateur ne sont même pas visibles par les gestionnaires de connaissances. (Les gestionnaires de connaissances peuvent également supprimer des rubriques dans le Centre des rubriques après la découverte.)

Si vous souhaitez exclure des rubriques au niveau de l’administrateur, vous devez les ajouter à un fichier. csv et charger le fichier. Vous pouvez effectuer cette opération pendant l’installation ou version ultérieure.

Le fichier. csv doit contenir les paramètres suivants :

- **Nom**: tapez le nom de la rubrique à exclure. Vous pouvez procéder de deux manières :
- **MatchType-exacte/partielle**: spécifiez si le nom que vous avez entré est un type de correspondance *exacte* ou *partielle* .
    - Correspondance exacte : vous pouvez inclure le nom exact ou un acronyme (par exemple, *contoso* ou *ATL*).
    - Correspondance partielle : vous pouvez exclure toutes les rubriques qui contiennent un mot spécifique.  Par exemple, *arc* exclut toutes les rubriques contenant le mot *arc* , comme un *cercle arc*, un *soudage* à l’arc de plasma ou un *arc de formation*. Notez qu’il n’exclura pas les rubriques dans lesquelles le texte est inclus dans un mot, tel que *architecture*.
- **Abréviation de (facultatif)**: (également appelée *expansion*) si vous souhaitez exclure un acronyme, tapez les mots que l’acronyme signifie.

    ![Exclure les rubriques du modèle CSV](../media/exclude-topics-csv.png) 

Vous pouvez copier le modèle CSV ci-dessous :

``` csv
Name (required),Expansion,MatchType- Exact/Partial (required)
```

## <a name="administration"></a>Administration

Lorsque vous configurez des expériences de rubrique, dans le cadre du processus de configuration, un centre de rubriques est créé automatiquement. Réfléchissez à ce que vous souhaitez nommer le centre de la rubrique et ce que vous voulez faire de l’URL. Vous pouvez définir le nom et l’URL dans le processus de configuration, et vous pouvez modifier le nom (mais pas l’URL) plus loin dans le centre d’administration 365 de Microsoft. Vous ne pouvez avoir qu’un seul centre de rubriques.

## <a name="setup-checklist"></a>Liste de vérification de configuration

Lorsque vous configurez des expériences de rubrique, vous aurez besoin des éléments suivants lors de l’installation de l’Assistant de configuration :

> [!div class="checklist"]
> * Liste des sites à inclure ou à exclure si tous les sites ne sont pas inclus pour la découverte de rubrique
> * Groupe de sécurité pour les visionneuses de rubrique si vous n’autorisez pas tous les utilisateurs à consulter les rubriques
> * Groupe de sécurité pour les contributeurs de rubrique si vous n’autorisez pas tous les utilisateurs à créer et modifier des rubriques
> * Groupe de sécurité pour les gestionnaires de connaissances si vous n’autorisez pas tous les utilisateurs à gérer les rubriques
> * Liste des rubriques sensibles à exclure de la découverte de rubriques
> * Un nom pour votre site Centre de rubriques

## <a name="see-also"></a>Voir aussi

[Configurer des expériences de rubrique](set-up-topic-experiences.md)

[Gestion de la découverte de rubrique dans Microsoft 365](topic-experiences-discovery.md)

[Gestion de la visibilité des rubriques dans Microsoft 365](topic-experiences-knowledge-rules.md)

[Gérer les autorisations de rubrique dans Microsoft 365](topic-experiences-user-permissions.md)

[Modifier le nom du centre de rubrique dans Microsoft 365](topic-experiences-administration.md)
