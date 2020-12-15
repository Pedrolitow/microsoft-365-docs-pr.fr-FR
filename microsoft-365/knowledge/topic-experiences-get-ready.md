---
title: Préparez votre environnement pour les expériences de rubrique (aperçu)
description: Préparez votre environnement de sorte que vous puissiez fournir autant de contenu que possible pour vos utilisateurs avec des expériences de rubrique (aperçu).
ms.author: samanro
author: samanro
manager: pamgreen
ms.date: 7/20/2020
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.custom: Adopt
search.appverid: ''
localization_priority: Normal
ROBOTS: NOINDEX
ms.openlocfilehash: 19112b222be328eb75b7eea807bea94e524fd56d
ms.sourcegitcommit: 29eb89b8ba0628fbef350e8995d2c38369a4ffa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "49683439"
---
# <a name="get-your-environment-ready-for-topic-experiences-preview"></a>Préparez votre environnement pour les expériences de rubrique (aperçu)

> [!Note]
> Le contenu de cet article est destiné à Project cortex privé preview. [En savoir plus sur le Projet cortex](https://aka.ms/projectcortex).

Pour tirer le plus grand nombre d’expériences de rubrique, vous souhaitez disposer de autant de contenu que possible pour la découverte de rubrique, afin de disposer d’un ensemble complet de rubriques pour vos utilisateurs. Quel est le contenu qui doit être utilisé pour la découverte de rubrique ? Comment optimiser le contenu indexé, tout en restant au contrôle ? Plus le contenu est dans l’étendue, plus l’intelligence artificielle peut générer des informations. Cet article vous guide à travers les étapes de planification afin de vous assurer que vous incluez le contenu approprié, et que vous disposez des personnes et des ressources appropriées pour que vos utilisateurs puissent s’en servir.

Pour planifier les expériences de rubrique (aperçu), vous devez :

![Migrer, connecter, moderniser, sécuriser et identifier les étapes de l’intégration à la gestion des connaissances](../media/knowledge-management/km-adoption-onboarding-checklist.png)

1. [Migrer du contenu vers SharePoint](#1-migrate-content-to-microsoft-365)
    - La rubrique Mining inclut uniquement le contenu sur les sites SharePoint.
      - Dans la mesure du possible, migrez du contenu précieux vers SharePoint Online à partir de sources externes.
      - Hiérarchiser les sources de contenu avec un fort potentiel pour des connaissances tacites.
      - Insistez sur les avantages de la gestion des connaissances pour encourager les utilisateurs à déplacer du contenu de OneDrive vers les sites SharePoint.

2. [Connecter des informations à Microsoft Graph](#2-connect-information-to-microsoft-graph)
    - À l’avenir, du contenu externe peut être placé dans le graphique de connaissances et bientôt disponible.
    - Pour les contenus qui ne peuvent pas être déplacés, envisagez d’utiliser des connecteurs Graph pour améliorer la recherche et vous préparer à une inclusion future.

3. [Moderniser des pages SharePoint](#3-modernize-sharepoint-pages)
    - Les fiches de rubrique ne peuvent être représentées que sur des pages modernes.
    - Identifiez les pages classiques de profil élevé qui sont des candidats de modernisation.

4. [Sécurisation du contenu de manière appropriée](#4-secure-content-appropriately)
    - Les ressources de rubrique sont découpées en sécurité en fonction des autorisations d’un utilisateur.
    - Identifiez le contenu susceptible d’avoir des autorisations incorrectes ou restrictives :
      - Encourager les propriétaires de site à utiliser les rapports de partage pour vérifier les autorisations
      - Les administrateurs doivent-ils auditer le contenu largement partagé à l’aide de la recherche
      - Encourager les propriétaires de contenu à partager du contenu qui n’est pas sensible et qui peut bénéficier d’un plus grand bénéfice pour l’organisation.
    - Passez en revue la configuration de Microsoft Graph sur les utilisateurs et le contenu :
      - La rubrique Mining honore la configuration, à l’exclusion du contenu de la recherche ou de Delve. Vérifiez si ces configurations sont toujours pertinentes.

5. [Identifier les gestionnaires de connaissances et les rubriques](#5-identify-knowledge-managers-and-topics)
    - Utiliser les taxonomies existantes pour créer manuellement des rubriques.
    - Identifier les experts techniques pour les sujets prévisibles ou amorcés.
    - Identifier les sites qui couvrent un grand nombre de données importantes pouvant être utilisées pour piloter le Mining.
    - Engager des responsables de connaissances et des communautés de pratiques.

## <a name="1-migrate-content-to-microsoft-365"></a>1. migrer le contenu vers Microsoft 365

Il existe plusieurs outils et services pour vous aider dans votre migration : vous pouvez obtenir une vue d’ensemble et des informations sur la migration à [migrer votre contenu vers Microsoft 365](https://docs.microsoft.com/sharepointmigration/migrate-to-sharepoint-online). Les outils de migration sont les suivants :

- [Gestionnaire de migration](https://docs.microsoft.com/sharepointmigration/mm-get-started)
- [Outil de migration SharePoint (SPMT)](https://docs.microsoft.com/sharepointmigration/introducing-the-sharepoint-migration-tool)
- [Microsoft 365 FastTrack](https://www.microsoft.com/fasttrack/microsoft-365)
- [Services et outils de migration de partenaires](https://www.microsoft.com/solution-providers)

Tirer le meilleur parti de votre migration :

- Migrer vers un site moderne, qui inclut Microsoft Teams. Bien que l’indexation puisse avoir lieu sur n’importe quel site SharePoint (classique ou moderne), l’affichage des rubriques pour les utilisateurs par le biais de mises en surbrillance et de cartes se produit uniquement sur les pages modernes.
- Gérer les noms d’utilisateur : la plupart des outils de migration vous permettent de mapper les identités des utilisateurs au sein de la migration, de sorte que les propriétés telles que créées ou modifiées par soient conservées après la migration. Ceci est important pour les sujets, car l’auteur de fichiers est utilisé pour identifier les experts ajoutés à une page de rubrique ou une carte. 
- Description des noms de compte de service : dans certains cas, il n’est pas possible de gérer les noms d’utilisateur. Par exemple, si vous migrez du contenu qui a été créé par une personne qui n’est plus un employé de l’organisation. Dans ce cas, la plupart des outils de migration déplacent un fichier comme s’il était créé par un compte administrateur ou un compte de service. Si cela se produit fréquemment, le compte de service peut ensuite être répertorié sur des rubriques en tant qu’expert. C’est ici que le nom de ce compte devient très important. Si vous la démarquez, la présence de ces comptes non humains sera compréhensible par vos utilisateurs.

## <a name="2-connect-information-to-microsoft-graph"></a>2. connexion d’informations à Microsoft Graph

Si vous ne parvenez pas à migrer du contenu, connectez-le avec Microsoft Graph :

- Envisagez d’implémenter des [connecteurs de contenu de graphique](https://docs.microsoft.com/microsoftsearch/connectors-overview). À l’aide de connecteurs, le contenu externe peut être indexé dans Microsoft Graph, où les utilisateurs peuvent le découvrir par le biais de Microsoft Search.
- Les développements à venir apportent des données externes à des expériences de sujet.

## <a name="3-modernize-sharepoint-pages"></a>3. moderniser les pages SharePoint

Étant donné que les cartes et les surbrillances de rubrique ne peuvent apparaître que sur des pages modernes, mettez à jour les pages que vous souhaitez inclure dans les expériences de la version classique à la version moderne. Reportez-vous à [la rubrique modernisation de sites SharePoint classiques](https://docs.microsoft.com/sharepoint/dev/transform/modernize-classic-sites). Vous pouvez utiliser le [scanneur de modernisation de SharePoint](https://docs.microsoft.com/sharepoint/dev/transform/modernize-scanner) pour préparer vos sites classiques à la modernisation.

Si vous avez un grand nombre de sites classiques, donnez la priorité aux pages de profil élevée pour les convertir en version moderne.

## <a name="4-secure-content-appropriately"></a>4. sécurisation du contenu de façon appropriée

Lorsque les utilisateurs interagissent avec une carte de rubrique ou une page de rubrique, ils peuvent voir des ressources différentes. Cela est dû au fait que les utilisateurs ont accès à différents fichiers associés à la rubrique. Si vos autorisations sous-jacentes sont trop strictes, les aspects Serendipitous de la découverte des informations par le biais des rubriques peuvent être réduits. En revanche, si elles sont trop larges, une rubrique pourrait exposer le contenu à un utilisateur que vous ne l’envisagez pas de voir.
La gestion des autorisations est essentielle ici. Et la gestion des autorisations est basée sur un partenariat continu entre les administrateurs et les propriétaires de contenu. Bien qu’il puisse s’agir d’une activité continue, vous pouvez suivre certaines étapes pratiques lors de la préparation des rubriques :

- Encourager les propriétaires de sites à examiner le partage et les autorisations ;

  Les propriétaires de sites SharePoint peuvent consulter un rapport de partage pour leur site qui affiche des détails complets de toutes les autorisations et les liens de partage configurés sur le site, consultez la rubrique [partage de rapports](https://docs.microsoft.com/sharepoint/sharing-reports). Cette liste répertorie les utilisateurs internes et externes (invités).

  Les propriétaires de site peuvent également voir qui dispose d’autorisations sur le site en accédant aux pages **autorisations de site** et **paramètres d’autorisations avancées** .

  1. Sur votre site, choisissez   >  **autorisations de site** de paramètres. Vérifiez les personnes qui sont indiquées sous propriétaires de site, membres du site et visiteurs du site. Recherchez les utilisateurs invités.
  2. Sur la page **autorisations** , choisissez **paramètres d’autorisations avancés**. Vous pouvez vérifier les autorisations uniques et Voir qui a un accès limité à tous les éléments du site.

- Auditez les groupes et les équipes Microsoft 365 pour vous assurer qu’ils sont correctement définis comme des équipes ou des groupes publics ou privés. Les nouveaux groupes teams et Microsoft 365 sont définis sur Private par défaut, mais lors de la publication initiale étaient publiques par défaut. Si vous étiez précédemment adopté de ces technologies, vous souhaiterez peut-être passer en revue. En outre, la fonction d’une équipe évolue souvent pendant son cycle de vie et le paramètre doit être mis à jour pour refléter l’utilisation actuelle de l’équipe.
- Passez en revue l’utilisation de « tout le monde », « tout le monde sauf les utilisateurs externes » ou des groupes de sécurité étendus. Le contenu peut être partagé de manière incorrecte avec ces valeurs. Pour passer en revue l’utilisation de ces groupes, vous pouvez :
  - Créer un compte qui n’a pas d’appartenance à un groupe
  - Utilisez la recherche avec ce compte pour découvrir le contenu qui est largement partagé.
  - Si le contenu inapproprié est visible par le biais de la recherche, vous pouvez utiliser les propriétaires de site pour corriger la configuration des autorisations.

En plus des autorisations, vous pouvez également contrôler l’étendue de ce qui est découvert dans les rubriques. Vous pouvez toujours contrôler ce qui est indexé.

Les administrateurs peuvent configurer l’indexation dans le centre d’administration 365 de Microsoft. Lorsque vous configurez la [gestion des connaissances](set-up-topic-experiences.md), vous pouvez :

- Autorisez la découverte sur tous les sites SharePoint ou spécifiez les sites à inclure ou exclure comme sources de rubrique.
- Lorsque vous avez des termes sensibles, vous pouvez également exclure les rubriques par nom. Par exemple, si vous avez le nom d’un projet sensible, où vous ne souhaitez pas qu’une mise en surbrillance ou une carte s’affiche, indépendamment des autorisations de l’utilisateur, vous pouvez exclure ce nom de projet.

Au niveau du contenu, vous pouvez également contrôler ce qui est détectable. Toute configuration que vous avez effectuée pour exclure le contenu de la recherche sera également utilisée par la découverte de contenu. Par conséquent, par exemple, si vous avez exclu une bibliothèque de documents spécifique de l’affichage dans les résultats de la recherche, cette bibliothèque de documents ne sera pas utilisée pour la découverte de rubrique.

## <a name="5-identify-knowledge-managers-and-topics"></a>5. identifier les gestionnaires de connaissances et les rubriques

La gestion des rubriques implique trois rôles clés, notamment deux nouveaux rôles Azure Active Directory (AAD) : administrateur de connaissances et gestionnaire de connaissances :

- L’administrateur des connaissances (KA) est un rôle technique, généralement dans celui-ci. Ce rôle permet de configurer les expériences des rubriques dans le centre d’administration M365, ainsi que la configuration de la découverte et de la visibilité des rubriques.
- Le gestionnaire de connaissances (KM) fonctionne avec les sujets eux-mêmes et supervise leur qualité et leur qualité.
- Les contributeurs de rubrique (TCs) ne sont pas basés sur un rôle AAD, mais sur les autorisations dans le centre d’administration. Ils sont des experts en matière de sujets qui permettent de répartir le contenu des rubriques, d’ajouter des ressources et des personnes.

En fonction de votre organisation, vous pouvez avoir peu ou plusieurs personnes qui agissent sur ces rôles. Pour certaines organisations, il peut s’agir de personnes identiques.

| Administrateur de connaissances | Gestionnaire de connaissances | Collaborateur de rubrique |
|:-------|:-------|:-------|:-------|
| Rôle AAD | Rôle AAD | SME |
| A accès au centre d’administration | A accès au centre d’administration | Aucun accès au centre d’administration |
| Configure des expériences de rubrique | Propriétaire de la gestion et de la qualité des rubriques | Contribue à des sujets en fonction de leur expertise. |
| Garantit que les normes de sécurité et de conformité sont appliquées et comprennent le contrat de licence.| Effectue des tâches de gestion telles que la création, la modification, la suppression et le rejet des rubriques. Prend en charge les contributeurs de rubrique avec leurs tâches. | Organise les informations et le contenu sur les pages de rubrique, notamment les personnes et les ressources qui sont épinglées à cette rubrique. |

Les mises en surbrillance et les cartes apparaissent aux utilisateurs dans le contexte de leur travail, par exemple lorsqu’ils explorent les pages modernes dans SharePoint. Vous contrôlez l’expérience de l’utilisateur final pour les rubriques.

- Qui peut voir les rubriques ? La visibilité des rubriques est configurée dans le centre d’administration Microsoft 365. Choisissez les groupes à autoriser à consulter les rubriques :
  - Tous les membres de mon organisation. « Tout le monde » n’inclut pas les invités, il s’agit de tous les utilisateurs internes de votre répertoire.
  - Uniquement les personnes ou les groupes de sécurité sélectionnés (cette option est intéressante lorsque vous effectuez encore le déploiement d’expériences de rubrique, vous pouvez donc tester avec un sous-ensemble d’utilisateurs). Si vous souhaitez que les invités puissent consulter les rubriques, vous devez utiliser l’option « personnes ou groupes de sécurité sélectionnés » et leur accorder une licence.
  - Personne.

    Une licence doit être appliquée à tous les utilisateurs, même invités, pour afficher l’expérience utilisateur. N’oubliez pas que les autorisations contrôlent toujours ce qui est visible.

- Quelles rubriques sont visibles ? Vous pouvez choisir l’une des actions suivantes :
  - Affichez toutes les rubriques candidates.
  - Afficher uniquement les rubriques confirmées.

À présent que nous disposons des responsables, des experts et des utilisateurs, nous pouvons parler des sujets eux-mêmes.

- Il est recommandé d’amorcer des rubriques dans votre liste de rubriques. La qualité et la quantité des rubriques sont basées sur votre contenu : elle sera uniquement créée sous forme de rubrique si elle est incluse dans le contenu de l’étendue. S’il y a suffisamment d’informations et de preuves pour le sujet, il sera créé par l’AI. L’amorçage des rubriques est l’endroit où le responsable du savoir et les experts du sujet peuvent vous aider. La combinaison des connaissances humaines et de l’AI est le meilleur itinéraire pour les sujets de qualité. Par conséquent, si des rubriques vous sont recommandées, vous pouvez les créer manuellement dans le Centre des rubriques. Cette opération donnera à l’AI un signal fort de la pertinence de cette rubrique et identifiera les ressources et les personnes à associer à ce sujet.
- Utiliser les taxonomies existantes pour vous aider dans la planification de votre rubrique, soit à partir de SharePoint, soit ailleurs. Les taxonomies existantes incluent souvent les termes de l’organisation, les produits, les domaines d’objet, etc. Les sources des rubriques peuvent également provenir de listes de projets, de signets de recherche existants, etc.
