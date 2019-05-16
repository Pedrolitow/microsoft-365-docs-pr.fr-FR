---
title: Site SharePoint Online pour les biens numériques hautement confidentiels de Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/15/2019
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: Ent_Architecture
description: 'Résumé: Comment Contoso a mis en œuvre un site SharePoint Online pour les données hautement réglementées afin de faciliter la collaboration entre ses équipes de recherche.'
ms.openlocfilehash: 99599829658e5dc46c8adebfe59f5c6d09b165de
ms.sourcegitcommit: 66bb5af851947078872a4d31d3246e69f7dd42bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34072778"
---
# <a name="sharepoint-online-site-for-highly-confidential-digital-assets-of-the-contoso-corporation"></a>Site SharePoint Online pour les biens numériques hautement confidentiels de Contoso Corporation

 **Résumé:** Comment Contoso a mis en œuvre un site SharePoint Online pour les données hautement réglementées afin de faciliter la collaboration entre ses équipes de recherche.
  
Les biens les plus précieux de Contoso sont sa propriété intellectuelle sous la forme de secrets commerciaux, tels que des techniques de fabrication propriétaires et des spécifications de conception pour les produits en cours de développement. Ces biens sont au format numérique, stockés à l’origine en tant que fichiers sur un site SharePoint Server 2016. Lorsque Contoso a déployé Microsoft 365 Enterprise, il souhaitait faire passer ses biens numériques locaux dans le nuage pour faciliter l’accès et la collaboration ouverte entre les équipes de recherche à Paris, Moscou, New York, Pékin et Bangalore. 
  
Toutefois, en raison de leur nature sensible, l’accès à ces fichiers doit être:

- Limité à l’ensemble des personnes autorisées à les afficher ou à les modifier, avec des autorisations en cours pour le site administré uniquement par les administrateurs SharePoint. 
- Protégé par la protection contre la perte de données (DLP) pour empêcher les utilisateurs de les répartir hors du site.
- Chiffrés et protégés à l’aide des listes de contrôle d’accès pour empêcher les utilisateurs non autorisés d’accéder à leur contenu, même s’ils sont distribués en dehors du site.

Les administrateurs de la sécurité et de SharePoint du service informatique de contoso ont décidé d’utiliser un [site SharePoint Online pour les données hautement réglementées](teams-sharepoint-online-sites-highly-regulated-data.md).
  
Contoso a utilisé ces étapes pour créer et sécuriser un site d’équipe SharePoint Online pour ses équipes de recherche.

## <a name="step-1-reviewed-and-verified-the-members-of-research-team-groups"></a>Étape 1: révision et vérification des membres des groupes d’équipes de recherche

Les administrateurs informatiques de contoso ont effectué un examen de l’ensemble des groupes de sécurité pour leurs équipes de recherche. Ils ont supprimé les personnes qui n’étaient pas chercheur ou n’ont pas besoin d’accéder aux ressources de recherche. 

Ils ont également créé ces nouveaux groupes de sécurité et les ont créés:

- **Research-administrateurs**  Ensemble des administrateurs SharePoint qui disposent d’un contrôle total sur le site, y compris la possibilité de modifier les autorisations.
- **Research-members**  Ensemble de groupes de sécurité pour les équipes de recherche dans le monde entier.
- **Research-visualiseurs**  Ensemble des utilisateurs de gestion, tels que les cadres de l’organisation de recherche, qui ne peuvent afficher que les biens sur le site.

## <a name="step-2-created-an-isolated-sharepoint-online-team-site"></a>Étape 2: création d’un site d’équipe SharePoint Online isolé 

Les administrateurs SharePoint de contoso ont d’abord créé un nouveau site d’équipe nommé **Research**. Ils sont ensuite configurés:

- Niveau d’autorisation contrôle total permettant d’utiliser le groupe SharePoint propriétaires de recherche, dont le groupe de sécurité **administrateurs de recherche** est membre.
- Le niveau d’autorisation Modifier pour utiliser le groupe SharePoint membres de la recherche, dont le groupe de sécurité **membres de recherche** est membre
- Le niveau d’autorisation lecture pour utiliser le groupe SharePoint des visiteurs de la recherche, qui a le groupe de sécurité **des visionneuses de recherche** en tant que membre

Voici les niveaux d’autorisation SharePoint qui en résultent, les groupes SharePoint et leurs membres.

![](./media/contoso-sharepoint-online-site-for-highly-confidential-assets/spo-permissions.png)

Ensuite, ils ont configuré des restrictions supplémentaires pour le site.

Pour plus d’informations sur la configuration, consultez la rubrique [deploy an Isolated SharePoint Online Team site](https://docs.microsoft.com/office365/enterprise/deploy-an-isolated-sharepoint-online-team-site).

## <a name="step-3-configured-the-site-for-a-restrictive-dlp-policy"></a>Étape 3: configuration du site pour une stratégie DLP restrictive

Tout d’abord, les administrateurs de contoso ont appliqué l’étiquette de rétention Office 365 **hautement confidentiel** au site de **recherche** .

Ensuite, ils ont créé une nouvelle stratégie DLP Office 365 nommée **Research** qui:

- Utilise l’étiquette de rétention Office 365 **hautement confidentiel** . 
- Est appliqué au site de **recherche** .
- Bloque les utilisateurs lorsqu’ils tentent de partager une ressource numérique sur le site de **recherche** en dehors de contoso.

Pour plus d’informations sur la configuration, consultez la rubrique [protéger des fichiers SharePoint Online avec des étiquettes de rétention et DLP](https://docs.microsoft.com/office365/enterprise/protect-sharepoint-online-files-with-office-365-labels-and-dlp).

## <a name="step-4-created-an-azure-information-protection-sub-label-for-the-site"></a>Étape 4: création d’une sous-étiquette Azure information protection pour le site

Les administrateurs contoso ont créé une nouvelle sous-étiquette Azure information protection nommée **Research** de l’étiquette **hautement confidentiel** par défaut dans une stratégie délimitée:

- Nécessite le chiffrement.
- Permet un accès total par les membres du groupe de sécurité des membres de la **recherche** .
- Autorise l’accès en lecture par les membres du groupe de sécurité **Research-visualisers** .

Ensuite, ils ont déployé le client Azure information protection sur les appareils des membres de l’équipe de recherche.

Pour plus d’informations sur la configuration, consultez la rubrique [protéger les fichiers SharePoint Online avec Azure information protection](https://docs.microsoft.com/office365/enterprise/protect-sharepoint-online-files-with-azure-information-protection). 

Voici la configuration obtenue du site de **recherche** pour les ressources hautement confidentielles.

![](./media/contoso-sharepoint-online-site-for-highly-confidential-assets/final-config.png)

Les fichiers dans les dossiers du site de **recherche** sont protégés par:

- Sous-étiquette **Research** Azure information protection, qui applique le chiffrement et permssions à chaque fichier qui voyage avec le fichier lorsqu’il est déplacé ou copié à partir du site de **recherche** .
- La stratégie DLP de **recherche** , qui utilise l’étiquette de rétention **hautement sensible** et les paramètres qui empêchent le partage du fichier avec des utilisateurs externes.
- Ensemble des autorisations de site, qui autorisent uniquement l’accès aux membres des groupes de sécurité et de l’administration des **membres** de la recherche et des visionneuses de **recherche** par les membres du groupe de sécurité **Research-admins** .

## <a name="step-5-migrated-the-on-premises-sharepoint-research-data"></a>Étape 5: migration des données de recherche SharePoint locales

Les administrateurs de contoso ont déplacé tous les fichiers de recherche sur site du site SharePoint Server 2016 local vers des dossiers dans le nouveau site SharePoint Online de **recherche** .

## <a name="step-6-trained-their-users"></a>Étape 6: apprentissage de leurs utilisateurs 

Le personnel de sécurité de Contoso a formé les équipes de recherche dans un cours obligatoire qui les a exécutées par les utilisateurs:

- Comment accéder au nouveau site SharePoint Online de **recherche** et à ses fichiers existants.
- Création de nouveaux fichiers sur le site et chargement de nouveaux fichiers stockés localement.
- Démonstration de la façon dont la stratégie DLP empêche les fichiers d’être partagés en externe.
- Comment utiliser le client Azure information protection pour étiqueter les fichiers de recherche avec la sous-étiquette **Research** .
- Démonstration de la façon dont la sous-étiquette de **recherche** protège un fichier même lorsqu’il est divulgué à partir du site.

Le résultat final est un environnement sécurisé dans lequel les chercheurs peuvent collaborer au sein de l’organisation dans un environnement sécurisé. 

Si un document de recherche avec la sous-étiquette **Research** est divulgué à partir du site de **recherche** , il est chiffré et accessible uniquement aux membres des groupes de sécurité **Research-members** et **Research-visualisables** avec des informations d’identification valides.

## <a name="next-step"></a>Étape suivante

[Déployer](deploy-microsoft-365-enterprise.md) Microsoft 365 entreprise dans votre organisation.

