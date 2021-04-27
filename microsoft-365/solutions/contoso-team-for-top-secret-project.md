---
title: Équipe isolée pour un projet top secret de Contoso Corporation
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.date: 08/14/2020
audience: ITPro
ms.topic: overview
ms.prod: microsoft-365-enterprise
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: Ent_Architecture
description: 'Résumé : Comment Contoso a utilisé une équipe avec isolation de sécurité pour un projet top secret afin de développer une nouvelle suite de produits et services.'
ms.openlocfilehash: 751bf3972d148219a6cc341067c0bf34cd581447
ms.sourcegitcommit: e02cf5702af178ddd2968877a808874ecb49ed2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52029015"
---
# <a name="isolated-team-for-a-top-secret-project-of-the-contoso-corporation"></a>Équipe isolée pour un projet top secret de Contoso Corporation

Après un site hors site, le PDG de Contoso a commandé le développement d'une nouvelle suite de produits et services qui pourrait doubler les bénéfices de Contoso au cours des cinq prochaines années. Le projet top secret pour développer l'entreprise, l'ingénierie et l'offre de marché était nommé **Project 2X** et le personnel clé au sein de l'entreprise a été embauché. 

La chronologie de la recherche et du développement était étroite, ce qui signifie que la collaboration devait être efficace et fournir des réunions sécurisées, des conversations en cours et un stockage de fichiers.

Les livrables pour Project 2X étaient des plans d'entreprise, des spécifications de produit et d'ingénierie, ainsi que des supports et des planifications marketing sous la forme de fichiers Word, Excel et PowerPoint. 

En raison de leur nature sensible, l'accès à ces fichiers était :

- Limité aux membres de l'équipe Project 2X et à la direction.
- Chiffré et protégé par des autorisations permettant d'autoriser l'accès uniquement aux membres de l'équipe Project 2X et à la direction, même si les fichiers ont été distribués en dehors de leurs dossiers sécurisés.

Le personnel informatique de Contoso a utilisé une équipe avec isolation [de la sécurité](secure-teams-security-isolation.md) pour Project 2X et ces étapes.

## <a name="step-1-created-a-private-team"></a>Étape 1 : Création d'une équipe privée

Tout d'abord, pour protéger l'accès au site SharePoint sous-jacent pour l'équipe, les administrateurs informatiques de Contoso ont configuré les stratégies d'accès [SharePoint recommandées.](../security/office-365-security/sharepoint-file-access-policies.md)

Ensuite, un administrateur informatique de Contoso a créé une équipe privée nommée Project 2X et ajouté les comptes d'utilisateur du personnel Project 2X en tant que membres. Ils ont également configuré l'équipe de sorte que seuls les propriétaires d'équipe Project 2X peuvent créer des canaux privés.

Pour plus d'informations sur la configuration, voir [Créer une équipe privée.](secure-teams-security-isolation.md#create-a-private-team)

## <a name="step-2-created-a-sensitivity-label-for-the-project-2x-team"></a>Étape 2 : Création d'une étiquette de niveau de sensibilité pour l'équipe Project 2X

Les administrateurs Contoso ont créé une étiquette de sensibilité **nommée Project 2X** qui :

- Chiffrement activé.
- Autorisations Co-Author pour le groupe Microsoft 2X Project 365.
- Autorisations de visionneuse autorisées pour le groupe Senior Leadership.
- Accès bloqué aux appareils non utilisés.

Les fichiers de la section **Documents** du site SharePoint Project 2X sous-jacent étaient protégés par :

- Autorisations de site, qui autorisent uniquement les autorisations complètes pour les membres du groupe Project 2X Microsoft 365 et les autorisations de lecture pour le groupe Senior Leadership.
- Étiquette de sensibilité Project 2X, avec chiffrement et autorisations qui se déplacent avec le fichier s'il est déplacé ou copié à partir du site.

Pour plus d'informations sur la configuration, voir [Créer une étiquette de sensibilité.](secure-teams-security-isolation.md#create-a-sensitivity-label)

## <a name="step-3-configured-the-underlying-sharepoint-site"></a>Étape 3 : Configuration du site SharePoint sous-jacent

Tout d'abord, pour protéger l'accès au site SharePoint sous-jacent pour l'équipe, les administrateurs informatiques de Contoso ont configuré les stratégies d'accès [SharePoint recommandées.](../security/office-365-security/sharepoint-file-access-policies.md)

Ensuite, ils ont configuré des paramètres d'autorisation supplémentaires pour le site :

- Pour empêcher les membres du groupe Project 2X de partager l'accès au site. Pour plus d'informations sur la configuration, voir [paramètres SharePoint](secure-teams-security-isolation.md#sharepoint-settings)pour une équipe avec isolation de sécurité.
- Pour les autorisations de lecture pour le groupe Senior Leadership.

Ensuite, ils ont configuré des paramètres d'autorisation supplémentaires pour le site afin d'empêcher les membres du groupe Project 2X de partager l'accès au site. 

À mesure que des canaux privés pour Project 2X ont été créés, le propriétaire du groupe a désactivé le partage d'invités et définissez le lien de partage par défaut sur la valeur Personnes **spécifiques.**

Voici la configuration résultante de l'équipe Project 2X avec isolation de sécurité.

![Configuration résultante de l'équipe Project 2X](../media/contoso-team-for-top-secret-project.png)

 ## <a name="step-4-trained-project-2x-team-members"></a>Étape 4 : Membres d'équipe Project 2X formés

Le personnel de sécurité de Contoso a formé les membres de l'équipe Project 2X dans un cours obligatoire qui les a formés à :

- Comment accéder à la nouvelle équipe Project 2X, utiliser des réunions et des conversations, et comment collaborer sur des fichiers d'équipe.
- Comment créer des fichiers dans l'équipe et télécharger de nouveaux fichiers créés localement.
- Comment étiqueter des fichiers avec l'étiquette de sensibilité Project 2X.
- Démonstration de la façon dont l'étiquette Project 2X protège un fichier même lorsqu'il quitte l'équipe.

Le résultat final est un environnement sécurisé dans lequel les membres de l'équipe Project 2X ont travaillé dans un environnement sécurisé pour les conversations, les réunions et les fichiers.

Voici un exemple de fichier stocké dans le site Project 2X sous-jacent avec l'étiquette de sensibilité Project 2X attribuée.

![Exemple de fichier stocké dans le site Project 2X sous-jacent](../media/contoso-team-for-top-secret-project-example.png)

Dans deux cas, les membres de l'équipe Project 2X ont téléchargé des fichiers protégés par l'étiquette Project 2X sur un lecteur local pour le travail hors connexion. 

Toutefois, après avoir été invité à obtenir des informations d'identification lors de leur ouverture, ils ont réalisé leur erreur et les ont supprimés.

En raison de l'environnement de collaboration de Teams et des fonctionnalités de sécurité de Microsoft 365, les détails de Project 2X ont été conservés secrètes pendant toute la durée du projet. Contoso a annoncé ses plans et est en train de déployer les nouveaux produits et services pour le plus grand plaisir de ses clients et de ses investisseurs, ainsi que de ses concurrents.

## <a name="next-step"></a>Étape suivante

[Déployez une équipe avec isolation de la sécurité](secure-teams-security-isolation.md) dans votre organisation.

