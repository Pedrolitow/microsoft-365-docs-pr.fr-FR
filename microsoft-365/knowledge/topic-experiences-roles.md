---
title: Rôles dans Sujets Microsoft Viva
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: cjtan
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-topics
ms.localizationpriority: medium
description: Découvrez les rôles d’utilisateur dans Rubriques.
ms.openlocfilehash: bf245cfc41fa3ad08af74dd2f2efbb8c0ddfef37
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60205796"
---
# <a name="roles-in-microsoft-viva-topics"></a>Rôles dans Sujets Microsoft Viva

Lorsque vous utilisez Topics dans votre environnement Microsoft 365, vos utilisateurs peuvent avoir les rôles suivants :

- Spectateurs des rubriques
- Contributeur de rubrique
- Gestionnaire des connaissances
- Administrateur d’informations

## <a name="topic-viewer"></a>Spectateurs des rubriques

Les visiteurs des rubriques sont les utilisateurs de votre organisation qui peuvent afficher les rubriques mises en surbrillez sur leur site moderne SharePoint, Recherche Microsoft via SharePoint et Office.com et le centre de rubriques. Ils peuvent afficher plus de détails sur une rubrique sur la page de rubrique. 

Pour que les points forts de la rubrique et leurs pages de rubriques soient visibles par un visionneur de rubriques, l'utilisateur doit :

- [Une licence Topics doit être attribuée par](./set-up-topic-experiences.md#assign-licenses) l’administrateur Microsoft 365 dossier.
- Être autorisé à avoir une visibilité sur des rubriques. Cette tâche est effectuée par l’administrateur du savoir dans la page des paramètres Rubriques Dans la Centre d'administration Microsoft 365.

## <a name="topic-contributors"></a>Contributeurs de rubrique

Les contributeurs de rubriques sont des utilisateurs de votre organisation qui ont non seulement des autorisations de visionneuse de rubrique, mais qui peuvent également modifier une rubrique existante ou créer une rubrique. Ils jouent un rôle important dans la « organisation » manuelle des informations d’une page de rubrique (ia ou fournies manuellement) pour garantir sa qualité.

Les utilisateurs qui ont des  autorisations de collaborateur de rubrique voient un bouton Modifier affiché sur les pages Rubrique, ce qui leur permet d’effectuer des mises à jour et de publier une rubrique.

Un contributeur peut également créer et publier une nouvelle rubrique via son centre thématique.

Pour créer et modifier une rubrique, l’utilisateur doit :

- [Une licence Topics doit être attribuée par](./set-up-topic-experiences.md#assign-licenses) l’administrateur Microsoft 365 dossier.
- [Des autorisations doivent être attribuées pour créer et modifier des rubriques.](./topic-experiences-user-permissions.md) Cette tâche est effectuée par l’administrateur du savoir dans la page des paramètres Rubriques Dans la Centre d'administration Microsoft 365.

## <a name="knowledge-managers"></a>Responsables d’informations

Les responsables d’informations sont des utilisateurs qui gèrent des rubriques dans votre organisation.  La gestion des rubriques est effectuée via la page Gérer **les rubriques** dans le centre de rubriques et elle est visible uniquement par les gestionnaires de connaissances.

Dans la page **Gérer les rubriques,** les gestionnaires de connaissances peuvent effectuer les tâches suivantes :

- Afficher les rubriques suggérées par l’IA.
- Examinez les rubriques pour vérifier qu’elles sont valides.
- Supprimez les rubriques que vous ne souhaitez pas voir pour vos utilisateurs.

En outre, un responsable d’informations peut modifier des rubriques existantes ou en créer.

Pour gérer les rubriques, l’utilisateur doit :

- [Une licence Topics doit être attribuée par](./set-up-topic-experiences.md#assign-licenses) l’administrateur Microsoft 365 dossier.
- [Des autorisations doivent être attribuées pour gérer les rubriques.](./topic-experiences-user-permissions.md) Cette tâche est effectuée par l’administrateur du savoir dans la page des paramètres Rubriques Dans la Centre d'administration Microsoft 365.

Les utilisateurs qui ont une bonne connaissance globale de votre entreprise peuvent être de bons candidats pour le rôle de gestionnaire de connaissances. Ces personnes peuvent non seulement avoir la connaissance de savoir si les rubriques sont valides ou non, mais peuvent également connaître les personnes au sein de l’entreprise qui sont liées à ces rubriques.

## <a name="knowledge-admins"></a>Administrateurs d’informations

Les administrateurs du savoir sont des administrateurs qui configurent et configurent Des rubriques Dans votre environnement Microsoft 365 de connaissances. Ils gèrent également les paramètres De La Rubriques Une fois la configuration terminée. Le rôle d’administrateur du savoir nécessite que vous soyez un administrateur Microsoft 365 ou un administrateur SharePoint, car la configuration et la gestion sont réalisées dans le Centre d'administration Microsoft 365.
Lors de l’installation, les administrateurs du savoir peuvent configurer Topics pour :

- Sélectionnez les sites SharePoint à analyser pour les rubriques.
- Sélectionnez les utilisateurs titulaires d’une licence qui peuvent afficher des rubriques (visionneuses de rubriques).
- Sélectionnez les rubriques à exclure de l’identification.
- Sélectionnez les utilisateurs titulaires d’une licence qui peuvent créer et modifier des rubriques (contributeurs de rubriques).
- Sélectionnez les utilisateurs titulaires d’une licence qui peuvent gérer des rubriques (Responsables d’informations).
- Nommez le centre de rubriques.

Les responsables d’informations doivent pouvoir se coordonner avec toutes les parties prenantes de Rubriques Viva dans leur organisation pour savoir comment le configurer. Par exemple, si un nouveau projet contient des informations sensibles, le gestionnaire de connaissances doit être informé afin qu’il puisse s’assurer que le site SharePoint n’est pas analyser pour les rubriques ou que des noms de sujets spécifiques doivent être exclus.
