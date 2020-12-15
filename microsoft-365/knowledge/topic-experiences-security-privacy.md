---
title: La rubrique présente la sécurité et la confidentialité
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: nkokoye, cjtan
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: MET150
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment planifier une rubrique relative à la sécurité et à la confidentialité dans Microsoft 365
ms.openlocfilehash: 7b88e5bbc8158ebd7dea65b2ecbf77085651b439
ms.sourcegitcommit: 1a9f0f878c045e1ddd59088ca2a94397605a242a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "49668165"
---
# <a name="topic-experiences-security-and-privacy"></a>La rubrique présente la sécurité et la confidentialité

Les expériences de rubrique utilisent les fonctionnalités de sécurité de contenu existantes dans Microsoft 365, ainsi que les contrôles de réseau de connaissances, pour contrôler ce que le contenu AI généré est présenté aux utilisateurs de votre organisation. Il s’agit de la combinaison des paramètres de sécurité de Microsoft 365 (autorisations sur les sites, les fichiers et les dossiers) et les paramètres d’administration qui déterminent ce qu’un utilisateur donné peuvent voir dans les rubriques.

La configuration du réseau de connaissances ne modifie pas les contrôles d’accès existants sur le contenu de votre organisation. Les utilisateurs ne peuvent voir que les utilisateurs auxquels ils ont déjà accès.

Cet article décrit la façon dont les expériences de rubrique fonctionnent du point de vue de la sécurité et les options dont les administrateurs de connaissances et les gestionnaires de connaissances ont besoin pour contrôler la visibilité des rubriques. Lisez cet article dans le cadre de votre [planification des expériences de rubrique](plan-topic-experiences.md).

Vous devez être familiarisé avec les [expériences de rubrique](knowledge-management-overview.md), le centre de [rubriques](topic-center-overview.md)et comment [utiliser les rubriques dans le centre de rubrique](work-with-topics.md) avant de lire cet article.

## <a name="what-users-can-see-in-topics"></a>Ce que les utilisateurs peuvent voir dans les rubriques

Pour voir les rubriques, un utilisateur doit :

- Disposer d’une licence pour une rubrique
- Être une [visionneuse de rubrique](topic-experiences-knowledge-rules.md#change-who-can-see-topics-in-your-organization), un [collaborateur ou un gestionnaire de connaissances](topic-experiences-user-permissions.md)

Ces deux éléments permettent aux utilisateurs d’afficher un accès au centre de rubriques et de les autoriser à consulter les points de vue et les cartes de sujet.

Rubriques les contributeurs disposent également d’autorisations de [création et de modification](topic-experiences-user-permissions.md#change-who-has permissions-to-update-topic-details) pour les rubriques, et les gestionnaires de connaissances peuvent confirmer ou supprimer des rubriques.

Lorsqu’une rubrique est détectée pour la première fois, les gestionnaires de connaissances peuvent l’afficher dans le centre de la rubrique. En fonction de l’intégralité et de la pertinence de la rubrique, les visionneuses de rubrique peuvent voir ou ne pas voir la rubrique présentée dans la rubrique cartes.

Les rubriques peuvent contenir des informations générées par les IA et des informations ajoutées ou modifiées par des collaborateurs ou des responsables du savoir.

- Les informations d’une rubrique qui a été ajoutée par AI sont visibles uniquement pour les personnes ayant accès au contenu source.
- Le texte qui a été ajouté ou modifié manuellement par un collaborateur de rubrique ou le gestionnaire de connaissances est visible par tous les utilisateurs qui peuvent voir la rubrique.

Les visionneuses de rubrique et les contributeurs peuvent afficher la liste des rubriques confirmées et publiées dans le centre de la rubrique, mais la rubrique détaille les détails qu’une personne peut voir dépend des autorisations dont elles disposent sur le matériel source et de la modification manuelle ou non de la rubrique.

Le tableau suivant décrit ce que les utilisateurs-consultants, contributeurs et gestionnaires de connaissances peuvent voir dans un sujet donné en fonction de leurs autorisations.

|Élément de rubrique|Ce que les utilisateurs peuvent voir|
|:---------|:------------------|
|Nom de la rubrique|Les utilisateurs peuvent voir le nom de toutes les rubriques dans le Centre des rubriques. Il se peut que certaines rubriques ne soient pas visibles si elles ont une faible pertinence pour l’utilisateur.|
|Description de la rubrique|Les descriptions générées par les IA sont visibles uniquement pour les utilisateurs qui disposent d’autorisations sur le contenu source. Les descriptions entrées ou modifiées manuellement sont visibles par tous les utilisateurs.|
|Personnes|Les personnes en attente sont visibles par tous les utilisateurs. Les personnes suggérées sont uniquement visibles par les utilisateurs disposant d’autorisations sur le contenu source.|
|Fichiers|Les fichiers ne sont visibles que pour les utilisateurs qui disposent d’autorisations sur le contenu source.|
|Pages|Les pages sont visibles uniquement pour les utilisateurs qui disposent d’autorisations sur le contenu source.|
|Sites|Les sites sont visibles uniquement pour les utilisateurs qui disposent d’autorisations sur le contenu source.|

## <a name="best-practices"></a>Meilleures pratiques

Les expériences de rubrique présentent des informations aux utilisateurs en fonction de leurs autorisations existantes sur le contenu. Microsoft 365 offre plusieurs façons de s’assurer que le contenu sensible est limité aux utilisateurs appropriés. Au-delà des autorisations de site ou d’équipe standard, vous pouvez utiliser des [étiquettes de confidentialité](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) ou la [protection contre la perte de données](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies) pour limiter l’accès au contenu et [aux révisions d’accès](https://docs.microsoft.com/azure/active-directory/governance/access-reviews-overview) pour vérifier régulièrement l’accès des utilisateurs aux informations sensibles.

Nous vous recommandons d’utiliser ces outils pour vous assurer que les autorisations de contenu sont correctement définies au sein de votre organisation. Les expériences de rubrique peuvent ensuite fournir des informations utiles et appropriées à vos utilisateurs.

S’il existe des rubriques que vous souhaitez exclure entièrement des expériences de rubrique, vous pouvez également :

- [Exclure les sites SharePoint sensibles de la découverte de rubrique](topic-experiences-discovery.md#select-sharepoint-topic-sources). Le contenu de ces sites n’apparaît pas dans la rubrique expériences.

- [Exclure les rubriques par nom](topic-experiences-discovery.md#exclude-topics-by-name). Les rubriques explicitement exclues n’apparaîtront pas dans la rubrique expériences.

- Demandez aux gestionnaires de connaissances de supprimer des rubriques dans le Centre des rubriques.

En outre, nous vous recommandons d’utiliser les meilleures pratiques suivantes :

- Recrutez des responsables de connaissances à partir de différentes zones de votre organisation. Le fait de disposer de gestionnaires de connaissances avec un large éventail d’expertise et d’accéder au contenu sous-jacent utilisé par les IA-peut vous aider à trouver les connaissances les plus utiles pour vos utilisateurs et à supprimer les informations sensibles s’il est trouvé.

- Configurer un flux de travail pour demander des modifications. Les responsables des connaissances ou les propriétaires d’équipe ou de site doivent disposer d’un processus qui leur permet de demander l’exclusion de sites ou de sites au démarrage de nouveaux projets au sein de votre organisation ou s’ils recherchent du contenu avec des paramètres d’autorisations inappropriés.

- Tenez compte de l’audience et de la sensibilité des informations lors de la création de descriptions de rubriques. Ces descriptions peuvent être visibles par les utilisateurs qui ne disposent pas d’autorisations sur le contenu source de la rubrique.

Bien que vous puissiez modifier les autorisations sur des pages de rubrique individuelles afin de limiter l’accès à un groupe spécifique d’utilisateurs, cette approche n’est pas recommandée en raison de l’effort administratif élevé requis.

## <a name="see-also"></a>Voir aussi

[Configurer Teams avec trois niveaux de protection](../solutions/configure-teams-three-tiers-protection.md)

[Planifier des expériences de rubrique](plan-topic-experiences.md)

[Configurer des expériences de rubrique](set-up-topic-experiences.md)
