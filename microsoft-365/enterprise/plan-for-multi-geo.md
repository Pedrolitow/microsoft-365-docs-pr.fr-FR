---
title: Plan pour Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Découvrez Microsoft 365 Multi-Geo, comment opèrent les fonctionnalités multigéographiques et les emplacements géographiques disponibles pour le stockage de données.
ms.openlocfilehash: bc742ebc77f5b28fe10f071e66d2e9753f8ced47
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68804923"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>Plan pour Microsoft 365 Multi-Geo

Ce guide est conçu pour les administrateurs de _locataires_ qui préparent leur _locataire_ Microsoft 365 pour qu’il soit étendu à d’autres zones géographiques, conformément aux besoins de l’entreprise pour répondre aux exigences de résidence des données.

Dans une configuration multigéographique, votre _client_ Microsoft 365 se compose d’un emplacement _géographique approvisionné principal_ et d’un ou plusieurs emplacements _géographiques satellites_ . Il s’agit d’un seul _locataire_ qui s’étend sur plusieurs emplacements _Geography_ .

Pour vous aider à comprendre les concepts de base de la configuration multigéographique, consultez les termes de la section Définitions de la [page Vue d’ensemble et définitions](m365-dr-overview.md).

L’activation Multi-Géo requiert quatre étapes principales :

1. Travailler avec votre équipe de compte pour ajouter le plan de services des _fonctionnalités multigéographiques dans Microsoft 365_.

2. Choisissez l’emplacement géographique _satellite_ souhaité et ajoutez-les à votre _locataire_.

3. Définissez l’emplacement de données préféré de vos utilisateurs sur l’emplacement _géographique satellite_ souhaité. Lorsqu’un nouvel OneDrive Entreprise site ou Exchange Online boîte aux lettres est approvisionné pour un utilisateur, il est approvisionné dans son PDL.

4. Migrez les sites OneDrive Entreprise existants de vos utilisateurs à partir de l’emplacement _géographique principal approvisionné_ vers leur emplacement de données _Geography satellite_, selon les besoins. (Exchange Online boîtes aux lettres sont migrées automatiquement lorsque vous définissez la pdl d’un utilisateur.)

Pour plus d’informations sur chacune de ces étapes, voir [Configurer Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md).

Consultez la [section Disponibilité](microsoft-365-multi-geo.md#microsoft-365-multi-geo-availability) de la page Vue d’ensemble multigéographique M365 pour les _zones géographiques_ qui peuvent être un emplacement _géographique satellite_ où vous pouvez héberger des sites OneDrive Entreprise et SharePoint Online, des boîtes aux lettres Exchange Online et Microsoft Teams. Lorsque vous planifiez l’utilisation de multigéographiques, dressez une liste des emplacements que vous souhaitez ajouter à votre _client_ Microsoft 365. Nous vous recommandons de commencer avec un ou deux emplacements satellites, puis d’étendre progressivement la configuration à d’autres emplacements géographiques si nécessaire.

## <a name="best-practices"></a>Meilleures pratiques

Nous vous recommandons de créer un utilisateur de test dans Microsoft 365 pour effectuer certains tests initiaux. Nous allons suivre certaines étapes de test et de vérification avec cet utilisateur avant de procéder à l’intégration des utilisateurs de production dans Microsoft 365 Multi-Geo.

Une fois que vous avez terminé le test avec l’utilisateur de test, sélectionnez un groupe pilote (éventuellement de votre service informatique) pour être le premier à utiliser OneDrive Entreprise et Exchange Online dans un nouvel emplacement géographique. Pour ce premier groupe, sélectionnez les utilisateurs qui n’ont pas encore de OneDrive Entreprise. Nous vous recommandons de limiter ce groupe initial à cinq personnes et de l’étoffer progressivement en suivant une approche de déploiement par lots.

Chaque utilisateur doit avoir un _emplacement de données préféré_ (PDL) défini afin que Microsoft 365 puisse déterminer dans quel emplacement _Geography_ provisionner son OneDrive. L’emplacement de données préféré de l’utilisateur doit correspondre à l’un des emplacements _géographiques satellites_ que vous avez choisis ou à votre _zone géographique approvisionnée principale_. Si le champ d’emplacement par défaut des données n’est pas obligatoire, nous vous recommandons de définir un emplacement par défaut des données pour tous les utilisateurs. Les charges de travail d’un utilisateur sans pdl seront approvisionnées dans la _zone géographique approvisionnée principale_.

Créez une liste de vos utilisateurs et incluez leur nom d’utilisateur principal (UPN) et le code d’emplacement de l’emplacement de données préféré approprié. Incluez votre utilisateur de test et votre groupe pilote initial. Vous aurez besoin de cette liste pour les procédures de configuration.

Si vos utilisateurs sont synchronisés à partir d’un système Active Directory local sur Azure Active Directory, vous devez définir l’emplacement par défaut des données en tant qu’attribut Active Directory et le synchroniser à l’aide d’Azure Active Directory Connect. Vous ne pouvez pas configurer directement l’emplacement par défaut des données pour des utilisateurs synchronisés à l’aide d’Azure AD PowerShell. Les étapes de configuration d’un emplacement par défaut des données et de synchronisation de celui-ci dans Active Directory sont décrites dans [Synchronisation Azure Active Directory Connect : Configurer un emplacement de données par défaut pour les ressources Microsoft 365](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

L’administration d’un _locataire_ multigéographique peut différer d’un _locataire_ non multigéographique, car la plupart des paramètres et services SharePoint Online et OneDrive Entreprise sont compatibles avec la géogéo. Nous vous recommandons de passer [en revue Administration d’un environnement multigéographique](administering-a-multi-geo-environment.md) avant de poursuivre votre configuration.

Pour plus d’informations sur l’expérience de vos utilisateurs finaux [dans un environnement multigéographique, consultez Expérience utilisateur dans un environnement](multi-geo-user-experience.md) multigéographique.

Pour commencer à configurer Microsoft 365 Multi-Geo, voir [Configurer Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md).

Une fois que vous avez terminé la configuration, n’oubliez pas de [migrer les bibliothèques OneDrive de vos utilisateurs](move-onedrive-between-geo-locations.md) pour permettre à ceux-ci de travailler à partir de leur emplacement par défaut des données.

## <a name="related-topics"></a>Voir aussi

[Configuration eDiscovery dans Microsoft 365 Multi-Geo](./multi-geo-ediscovery-configuration.md)
