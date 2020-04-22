---
title: Site SharePoint pour les biens numériques hautement confidentiels de Contoso Corporation
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/18/2019
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: Ent_Architecture
description: 'Résumé : Comment Contoso a mis en œuvre un site SharePoint pour les données hautement réglementées afin de faciliter la collaboration entre ses équipes de recherche.'
ms.openlocfilehash: 0a4bc2f685cf015611da62ebbed000218f37f31e
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43634251"
---
# <a name="sharepoint-site-for-highly-confidential-digital-assets-of-the-contoso-corporation"></a>Site SharePoint pour les biens numériques hautement confidentiels de Contoso Corporation

Les biens les plus précieux de Contoso sont sa propriété intellectuelle sous la forme de secrets commerciaux, tels que des techniques de fabrication propriétaires et des spécifications de conception pour les produits en cours de développement. Ces biens étaient sous forme numérique, stockés à l’origine en tant que fichiers sur un site SharePoint Server 2016. Lorsque Contoso a déployé Microsoft 365 Enterprise, il souhaitait faire passer ses biens numériques locaux dans le nuage pour faciliter l’accès et la collaboration ouverte entre les équipes de recherche à Paris, Moscou, New York, Pékin et Bangalore. 
  
Toutefois, en raison de leur nature sensible, l’accès à ces fichiers doit être :

- Limité à l’ensemble des personnes qui sont autorisées à y accéder. 
- Protégé par une stratégie de protection contre la perte de données (DLP) pour empêcher les utilisateurs de les répartir hors du site.
- Chiffrés et protégés par des autorisations pour empêcher les utilisateurs non autorisés d’accéder à leur contenu, même s’ils sont distribués en dehors du site.

La sécurité et les administrateurs SharePoint du service informatique de contoso ont décidé d’utiliser un [site SharePoint pour les données hautement réglementées](teams-sharepoint-online-sites-highly-regulated-data.md).
  
Contoso a utilisé ces étapes pour créer et sécuriser un site d’équipe SharePoint pour ses équipes de recherche.

## <a name="step-1-created-a-private-sharepoint-team-site"></a>Étape 1 : création d’un site d’équipe SharePoint privé

Pour protéger l’accès au site SharePoint, contoso IT a configuré les [stratégies d’accès SharePoint recommandées](sharepoint-file-access-policies.md).

Ensuite, les administrateurs informatiques de contoso ont compilé une liste des comptes d’utilisateurs pour les chercheurs de Paris, Moscou, New York, Pékin et Bangalore. 

Ensuite, un administrateur informatique de Contoso a créé un nouveau site d’équipe privé nommé **Research** et ajouté tous les comptes d’utilisateurs pour ses chercheurs.

Ils ont ensuite configuré des paramètres d’autorisation supplémentaires pour le site afin d’empêcher les chercheurs de partager l’accès au site et d’empêcher les non-chercheurs de demander l’accès au site.

## <a name="step-2-configured-the-site-for-a-restrictive-dlp-policy"></a>Étape 2 : configuration du site pour une stratégie DLP restrictive

Tout d’abord, les administrateurs de contoso ont appliqué l’étiquette de rétention **hautement confidentielle** existante au dossier documents du site de **recherche** .

Ensuite, ils ont créé une nouvelle stratégie DLP nommée **Research** qui :

- Utilise l’étiquette de rétention **hautement confidentielle** . 
- Bloque les utilisateurs lorsqu’ils tentent de partager une ressource numérique sur le site de **recherche** en dehors de contoso.

Pour plus d’informations sur la configuration, consultez la rubrique [protéger les fichiers SharePoint avec les étiquettes de rétention et DLP](https://docs.microsoft.com/office365/enterprise/protect-sharepoint-online-files-with-office-365-labels-and-dlp).

## <a name="step-3-created-a-sensitivity-sublabel-for-the-site"></a>Étape 3 : création d’une sous-étiquette de sensibilité pour le site

Les administrateurs contoso ont créé une nouvelle sous-étiquette de sensibilité nommée « **Team teams** » de l’étiquette **hautement confidentiel** qui :

- Nécessite le chiffrement.
- Autorise les autorisations de co-auteur pour le groupe Microsoft 365 **Research**
- S’applique au groupe Microsoft 365 **Research**

Voici la configuration obtenue du site d’équipe de **recherche** pour les ressources hautement confidentielles.

![La configuration obtenue du site d’équipe de recherche pour les ressources hautement confidentielles](../media/contoso-sharepoint-online-site-for-highly-confidential-assets/final-config.png)

Les fichiers dans les dossiers du site de **recherche** sont protégés par :

- Les autorisations de site, qui autorisent uniquement l’accès aux membres du groupe Microsoft 365 **Research** .
- La stratégie DLP de **recherche** , qui utilise l’étiquette de rétention **hautement confidentielle** et les paramètres qui empêchent le partage du fichier avec des utilisateurs externes.
- Sous-étiquette de sensibilité des **équipes de recherche** , avec le chiffrement et les autorisations qui voyagent avec le fichier s’il est déplacé ou copié à partir du site de **recherche** .

Voici un exemple de fichier stocké sur le site de **recherche** avec la sous-étiquette de sensibilité **teams de recherche** affectée.

![La configuration obtenue du site d’équipe de recherche pour les ressources hautement confidentielles](../media/contoso-sharepoint-online-site-for-highly-confidential-assets/final-config-example-file.png)


## <a name="step-4-migrated-the-on-premises-sharepoint-research-data"></a>Étape 4 : migration des données de recherche SharePoint locales

Les administrateurs de contoso ont déplacé tous les fichiers de recherche sur site du site SharePoint Server 2016 local vers des dossiers dans le nouveau site SharePoint de **recherche** .

## <a name="step-5-trained-their-researchers"></a>Étape 5 : formation de leurs chercheurs

Le personnel de sécurité de Contoso a formé les membres du groupe Microsoft 365 **Research** dans un cours obligatoire qui les a exécutées par les éléments suivants :

- Comment accéder au nouveau site de **recherche** et à ses fichiers existants.
- Création de nouveaux fichiers sur le site et chargement de nouveaux fichiers stockés localement.
- Démonstration de la façon dont la stratégie DLP de **recherche** empêche les fichiers d’être partagés en externe.
- Comment étiqueter les fichiers avec la sous-étiquette de sensibilité des **équipes de recherche** .
- Démonstration de la façon dont la sous-étiquette **Research teams** protège un fichier même lorsqu’il est divulgué à partir du site.

Le résultat final est un environnement sécurisé dans lequel les chercheurs peuvent collaborer entre Contoso dans un environnement sécurisé sur des fichiers contenant des informations de recherche. 

Si un document de recherche avec la sous-étiquette **Research teams** quitte le site de **recherche** , il est chiffré et accessible uniquement aux membres du groupe Microsoft 365 **Research** avec des informations d’identification de compte d’utilisateur valides.

## <a name="next-step"></a>Étape suivante

[Déployer](deploy-microsoft-365-enterprise.md) Microsoft 365 entreprise dans votre organisation.

## <a name="see-also"></a>Voir également

[Bibliothèque de productivité Microsoft 365](https://aka.ms/productivitylibrary)https://aka.ms/productivitylibrary)
