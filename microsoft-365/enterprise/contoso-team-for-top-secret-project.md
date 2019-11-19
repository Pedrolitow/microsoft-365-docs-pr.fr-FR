---
title: Équipe pour un projet secret principal de Contoso Corporation
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
description: 'Résumé : Comment Contoso a utilisé une équipe pour les données hautement réglementées pour un projet à forte priorité afin de développer une nouvelle suite de produits et de services.'
ms.openlocfilehash: 23a967ea7ffdb3497d705a3ddda4d3c56e415b8e
ms.sourcegitcommit: 0ceb79a633f7004e82b80e69b6f7a7329ccec7ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2019
ms.locfileid: "38699890"
---
# <a name="team-for-a-top-secret-project-of-the-contoso-corporation"></a>Équipe pour un projet secret principal de Contoso Corporation

Après un cadre hors site, le PDG de Contoso a ordonné le développement d’une nouvelle suite de produits et de services qui pourrait doubler les bénéfices de contoso au cours des cinq prochaines années. Le projet de secret principal pour développer l’entreprise, l’ingénierie et le plan de marché a été nommé **Project 2x** et le personnel clé de l’entreprise ont été recrutés. 

Les chronologies de recherche et de développement étaient étroites, ce qui signifiait que la collaboration devait être efficace et fournir des réunions sécurisées, des conversations en cours et le stockage de fichiers.

Les livrables résultants pour Project 2X étaient des offres professionnelles, des spécifications de produits et d’ingénierie, ainsi que des documents et des plans de marketing sous forme de fichiers Word, Excel et PowerPoint. 

En raison de leur nature confidentielle, l’accès à ces fichiers était :

- Limité à Project 2X membres de l’équipe.
- Protégé par une stratégie de protection contre la perte de données (DLP) pour empêcher Project 2 membres de l’équipe de les partager en dehors de l’équipe.
- Chiffrés et protégés par des autorisations pour permettre l’accès uniquement aux membres de l’équipe Project 2X, même si les fichiers ont été distribués en dehors de contoso.

Le personnel informatique de Contoso a utilisé une [équipe pour les données hautement réglementées](secure-teams-highly-regulated-data-scenario.md) pour Project 2x et les étapes suivantes.

## <a name="step-1-created-a-private-team-and-locked-down-the-underlying-sharepoint-site"></a>Étape 1 : création d’une équipe privée et verrouillage du site SharePoint sous-jacent

Pour protéger l’accès au site SharePoint sous-jacent pour l’équipe, les administrateurs informatiques de contoso ont configuré les [stratégies d’accès SharePoint recommandées](sharepoint-file-access-policies.md).

Ensuite, un administrateur informatique de Contoso a créé une nouvelle équipe privée appelée Project 2X et a ajouté les comptes d’utilisateur de Project 2X personnel en tant que membres.

Ensuite, ils ont configuré des paramètres d’autorisation supplémentaires pour le site afin d’empêcher Project 2X de partager l’accès au site et d’empêcher d’autres personnes de demander l’accès au site.

Pour plus d’informations sur la configuration, consultez la rubrique [paramètres SharePoint d’une équipe hautement réglementée](https://docs.microsoft.com/microsoft-365/security/office-365-security/deploy-teams-three-tiers#highly-confidential-teams).

## <a name="step-2-configured-a-dlp-policy-and-the-underlying-site-for-a-retention-label"></a>Étape 2 : configuration d’une stratégie DLP et du site sous-jacent pour une étiquette de rétention 

Tout d’abord, contoso admins a appliqué l’étiquette de rétention Office 365 **hautement confidentiel** existante à la section **documents** du site SharePoint sous-jacent de l’équipe Project 2x.

Ensuite, ils ont créé une nouvelle stratégie DLP Office 365 nommée **Project 2x** qui :

- Utilise l’étiquette de rétention Office 365 hautement confidentiel.
- Bloque les utilisateurs lorsqu’ils tentent de partager un fichier dans l’équipe Project 2X en dehors de contoso.

Pour plus d’informations sur la configuration, consultez la rubrique [protéger les fichiers dans teams avec les étiquettes de rétention et DLP](https://docs.microsoft.com/microsoft-365/security/office-365-security/deploy-teams-retention-dlp).

## <a name="step-3-created-an-office-365-sensitivity-label-for-the-project-2x-team"></a>Étape 3 : création d’une étiquette de confidentialité Office 365 pour l’équipe Project 2X

Les administrateurs contoso ont créé une étiquette de confidentialité Office 365 nommée **Project 2x** qui :

- Nécessite le chiffrement.
- Autorise les autorisations de co-auteur pour le groupe 2 d’Office 365.

Voici la configuration obtenue de l’équipe Project 2X.

![La configuration obtenue de l’équipe Project 2X](./media/contoso-team-for-highly-confidential-assets/final-config.png)
 
Les fichiers de la section documents du projet sous-jacent 2 SharePoint ont été protégés par :

- Les autorisations de site, qui autorisent uniquement l’accès aux membres du groupe 2 d’Office 365.
- Étiquette de rétention hautement confidentielle, automatiquement affectée aux nouveaux fichiers.
- Stratégie DLP qui utilise l’étiquette de rétention hautement confidentielle et les paramètres qui empêchent le partage du fichier avec les utilisateurs externes.
- L’étiquette de sensibilité Project 2X, avec le chiffrement et les autorisations qui transitent avec le fichier s’il est déplacé ou copié à partir du site.

Voici un exemple de fichier stocké dans le site Project 2X sous-jacent avec l’étiquette de rétention hautement réglementée et l’étiquette de sensibilité du projet 2X attribuée.

![Exemple de fichier stocké dans le site du projet 2 sous-jacent](./media/contoso-team-for-highly-confidential-assets/final-config-example-file.png)
 
## <a name="step-4-trained-project-2x-team-members"></a>Étape 4 : projet formé 2X membres de l’équipe

Le personnel de sécurité de Contoso a formé le projet 2 membres d’équipe dans un cours obligatoire qui les a exécutés par les utilisateurs :

- Comment accéder au nouveau projet 2 équipe, utiliser des réunions et des conversations et collaborer sur des fichiers d’équipe.
- Comment créer des fichiers dans l’équipe et télécharger de nouveaux fichiers créés localement.
- Démonstration de la façon dont la stratégie DLP empêche les fichiers d’être partagés en externe.
- Comment étiqueter les fichiers avec l’étiquette de sensibilité Project 2X.
- Démonstration de la façon dont l’étiquette Project 2X protège un fichier même lorsqu’il quitte l’équipe.

Le résultat final était un environnement sécurisé dans lequel Project 2 membres de l’équipe ont collaboré dans un environnement sécurisé pour les conversations, les réunions et les fichiers.

Dans quelques exemples, Project 2X les membres de l’équipe ont téléchargé des fichiers protégés par l’étiquette Project 2X sur un lecteur local pour le travail hors connexion. Toutefois, une fois que vous êtes invité à entrer les informations d’identification lors de leur ouverture, elles ont fait l’erreur et les ont supprimées.

En raison de l’environnement de collaboration de teams et des fonctionnalités de sécurité de Microsoft 365, les détails du projet 2X étaient secrets pendant toute la durée du projet. Contoso a annoncé ses plans et est en train de déployer les nouveaux produits et services à l’esprit de ses clients et investisseurs, ainsi que les chagrin de ses concurrents.

## <a name="next-step"></a>Étape suivante

[Déployer](deploy-microsoft-365-enterprise.md) Microsoft 365 entreprise dans votre organisation.

## <a name="see-also"></a>Voir aussi

[Bibliothèque de productivité Microsoft 365](https://aka.ms/productivitylibrary)https://aka.ms/productivitylibrary)
