---
title: Équipe isolée pour un projet top secret de Contoso Corporation
f1.keywords:
- NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.date: 08/14/2020
audience: ITPro
ms.topic: overview
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- highpri
- M365-security-compliance
ms.custom: Ent_Architecture
description: 'Résumé : Comment Contoso a utilisé une équipe avec isolation de sécurité pour un projet top secret afin de développer une nouvelle suite de produits et de services.'
ms.openlocfilehash: 2afc993245e2ad1a67242855dd658a38de5e628a
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67730658"
---
# <a name="isolated-team-for-a-top-secret-project-of-the-contoso-corporation"></a>Équipe isolée pour un projet top secret de Contoso Corporation

Après un départ de cadres, le PDG de Contoso a commandé le développement d’une nouvelle suite de produits et de services qui pourrait doubler les bénéfices de Contoso dans les cinq prochaines années. Le projet top secret pour développer l’entreprise, l’ingénierie et le plan de marché a été nommé **Project 2X** et le personnel clé de l’entreprise a été recruté. 

Les délais de recherche et de développement étaient serrés, ce qui signifiait que la collaboration devait être efficace et assurer des réunions sécurisées, des conversations en cours et un stockage de fichiers.

Les livrables résultants pour Project 2X étaient des plans d’entreprise, des spécifications de produit et d’ingénierie, ainsi que des supports marketing et des planifications sous la forme de fichiers Word, Excel et PowerPoint. 

En raison de leur nature sensible, l’accès à ces fichiers était le suivant :

- Limité aux membres de l’équipe Project 2X et aux cadres supérieurs.
- Chiffré et protégé avec des autorisations permettant d’autoriser l’accès uniquement aux membres de l’équipe Project 2X et aux cadres supérieurs, même si les fichiers ont été distribués en dehors de leurs dossiers sécurisés.

Le personnel informatique de Contoso a utilisé une [équipe avec isolation de sécurité](secure-teams-security-isolation.md) pour Project 2X et ces étapes.

## <a name="step-1-created-a-private-team"></a>Étape 1 : Création d’une équipe privée

Tout d’abord, pour protéger l’accès au site SharePoint sous-jacent pour l’équipe, les administrateurs informatiques de Contoso ont configuré les [stratégies d’accès SharePoint recommandées](../security/office-365-security/sharepoint-file-access-policies.md).

Ensuite, un administrateur informatique de Contoso a créé une équipe privée nommée Project 2X et ajouté les comptes d’utilisateur du personnel de Project 2X en tant que membres. Ils ont également configuré l’équipe afin que seuls les propriétaires de l’équipe Project 2X puissent créer des canaux privés.

Pour plus d’informations sur la configuration, consultez [Créer une équipe privée](secure-teams-security-isolation.md#create-a-private-team).

## <a name="step-2-created-a-sensitivity-label-for-the-project-2x-team"></a>Étape 2 : Création d’une étiquette de confidentialité pour l’équipe Project 2X

Les administrateurs de Contoso ont créé une étiquette de confidentialité nommée **Project 2X** qui :

- Chiffrement activé.
- Autorisations Co-Author autorisées pour le groupe Project 2X Microsoft 365.
- Autorisations de visionneuse autorisées pour le groupe senior de direction.
- Accès bloqué aux appareils non gérés.

Les fichiers de la section **Documents** du site SharePoint Project 2X sous-jacent ont été protégés par :

- Les autorisations de site, qui autorisent uniquement les autorisations complètes pour les membres du groupe Project 2X Microsoft 365 et les autorisations de lecture pour le groupe Senior Leadership.
- Étiquette de confidentialité Project 2X, avec chiffrement et autorisations qui transitent avec le fichier s’il est déplacé ou copié à partir du site.

Pour plus d’informations sur la configuration, consultez [Créer une étiquette de confidentialité](secure-teams-security-isolation.md#create-a-sensitivity-label).

## <a name="step-3-configured-the-underlying-sharepoint-site"></a>Étape 3 : Configuration du site SharePoint sous-jacent

Tout d’abord, pour protéger l’accès au site SharePoint sous-jacent pour l’équipe, les administrateurs informatiques de Contoso ont configuré les [stratégies d’accès SharePoint recommandées](../security/office-365-security/sharepoint-file-access-policies.md).

Ensuite, ils ont configuré des paramètres d’autorisation supplémentaires pour le site :

- Pour empêcher les membres du groupe Project 2X de partager l’accès au site. Pour plus d’informations sur la configuration, consultez [les paramètres SharePoint pour une équipe avec isolation de sécurité](secure-teams-security-isolation.md#sharepoint-settings).
- Pour les autorisations de lecture pour le groupe de direction supérieure.

Ensuite, ils ont configuré des paramètres d’autorisation supplémentaires pour le site afin d’empêcher les membres du groupe Project 2X de partager l’accès au site. 

Lorsque des canaux privés pour Project 2X ont été créés, le propriétaire du groupe a désactivé le partage d’invités et défini le lien de partage par défaut sur la valeur **De personnes spécifiques** .

Voici la configuration résultante de l’équipe Project 2X avec isolation de sécurité.

![Configuration résultante de l’équipe Project 2X.](../media/contoso-team-for-top-secret-project.png)

 ## <a name="step-4-trained-project-2x-team-members"></a>Étape 4 : Membres formés de l’équipe Project 2X

Le personnel de sécurité de Contoso a formé les membres de l’équipe Project 2X dans un cours obligatoire qui les a suivis :

- Comment accéder à la nouvelle équipe Project 2X, utiliser des réunions et des conversations, et comment collaborer sur des fichiers d’équipe.
- Comment créer des fichiers dans l’équipe et charger de nouveaux fichiers créés localement.
- Comment étiqueter des fichiers avec l’étiquette de confidentialité Project 2X.
- Démonstration de la façon dont l’étiquette Project 2X protège un fichier même lorsqu’il quitte l’équipe.

Le résultat final a été un environnement sécurisé dans lequel les membres de l’équipe Project 2X ont collaboré dans un environnement sécurisé pour les conversations, les réunions et les fichiers.

Voici un exemple de fichier stocké dans le site Project 2X sous-jacent avec l’étiquette de confidentialité Project 2X affectée.

![Exemple de fichier stocké dans le site Project 2X sous-jacent.](../media/contoso-team-for-top-secret-project-example.png)

Dans quelques cas, les membres de l’équipe Project 2X ont téléchargé des fichiers protégés par l’étiquette Project 2X sur un lecteur local pour le travail hors connexion. 

Toutefois, après avoir été invité à entrer des informations d’identification lors de leur ouverture, ils ont réalisé leur erreur et les ont supprimés.

En raison de l’environnement de collaboration de Teams et des fonctionnalités de sécurité de Microsoft 365, les détails de Project 2X ont été conservés secrets pendant la durée du projet. Contoso a annoncé ses plans et est en train de déployer les nouveaux produits et services au grand plaisir de ses clients et investisseurs et au chagrin de ses concurrents.

## <a name="next-step"></a>Étape suivante

[Déployez une équipe avec isolation de la sécurité](secure-teams-security-isolation.md) dans votre organisation.

