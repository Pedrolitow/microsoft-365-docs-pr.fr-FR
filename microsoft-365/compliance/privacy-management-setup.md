---
title: Prise en charge de la gestion de la confidentialité Microsoft (prévisualisation)
f1.keywords:
- CSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- M365-privacy-management
search.appverid:
- MOE150
- MET150
description: Découvrez comment configurer la gestion de la confidentialité pour votre organisation, définir des rôles et des autorisations et configurer des paramètres importants.
ms.openlocfilehash: 1472b20b32315480f5b7b237ca91a465de293747
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58247533"
---
# <a name="get-started-with-privacy-management-preview"></a>Prise en charge de la gestion de la confidentialité (aperçu)

Dans cet article : découvrez  comment configurer l’accès à  la gestion de la confidentialité pour votre organisation, comment commencer à évaluer vos données et comment gérer les **paramètres importants.**

## <a name="who-can-access-privacy-management"></a>Qui pouvez accéder à la gestion de la confidentialité

La prévisualisation publique de la gestion de la confidentialité est disponible dans le Centre de conformité Microsoft 365 et est disponible pour les organisations ayant des licences E1, E3 et E5 entreprise dans Office 365 et Microsoft 365. Lorsque la gestion de la confidentialité passe à la disponibilité générale, les organisations qui ont utilisé la prévisualisation publique doivent obtenir une nouvelle licence.

Pour obtenir des instructions détaillées sur les licences, consultez [instructions relatives aux licences Microsoft 365 pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

> [!Note]
> La prévisualisation publique de la gestion de la confidentialité ne sera pas disponible pour les clients modérés, Cloud de la communauté du secteur public élevés ou du département de la Défense (DoD) du gouvernement américain Community (Cloud de la communauté du secteur public).

## <a name="set-up-privacy-management"></a>Configurer la gestion de la confidentialité

Pour commencer à gérer la confidentialité, obtenez d’abord votre licence d’essai et connectez-vous. Vous pouvez ensuite attribuer des autorisations à vos utilisateurs et examiner les paramètres.

### <a name="get-trial-license"></a>Obtenir une licence d’essai

Pour commencer la prévisualisation publique, votre administrateur général peut obtenir la licence d’essai de gestion de la confidentialité gratuite à partir du [Centre d’administration.](https://aka.ms/purchasem365privacy) Sélectionnez « Démarrer la version d’essai » pour commencer. Votre licence dure un mois et vous pouvez la renouveler sans frais selon vos besoins lors de la prévisualisation publique.

Après avoir obtenu votre abonnement, autorisez son activation pendant 30 minutes. Revenir ensuite à la gestion de la confidentialité pour commencer. Vous serez invité à confirmer que vous acceptez les termes et le processus d’évaluation des données personnelles[(en savoir plus).](privacy-management.md#how-we-evaluate-your-data) Vous pouvez consulter les liens fournis dans son intégralité avant de poursuivre. Une fois que vous êtes d’accord, la gestion de la confidentialité peut prendre jusqu’à 24 heures pour fournir des informations sur les données de votre organisation.

Si vous ne devez pas détenir le rôle requis pour obtenir l’abonnement ou consentir aux conditions d’utilisation de la gestion de la confidentialité, vous serez invité à contacter votre administrateur global pour obtenir de l’aide.

### <a name="set-user-permissions-and-assign-roles"></a>Définir des autorisations utilisateur et attribuer des rôles

La gestion de la confidentialité utilise un modèle d’autorisation de contrôle d’accès basé sur un rôle (RBAC). Seuls les utilisateurs affectés à un rôle peuvent accéder à la gestion de la confidentialité, et les actions autorisées par chaque utilisateur sont limitées par type de rôle.

Il est recommandé que l’administrateur global se connecte et définisse les autorisations des utilisateurs dans le Centre de conformité lors de l’utilisation de la gestion de la confidentialité pour la première fois. Pour un démarrage rapide, le groupe de rôles Gestion de la confidentialité dispose des autorisations pour accéder à toutes les fonctionnalités de gestion de la confidentialité. Ce groupe peut être adapté aux organisations où la même personne peut effectuer toutes les tâches au sein de la solution de gestion de la confidentialité. D’autres rôles de confidentialité vous permettent de prendre un contrôle plus granulaire et d’affecter des utilisateurs à des fonctions ou fonctionnalités sélectionnées.

Pour en savoir plus sur les groupes de rôles et sur la façon d’accorder l’accès, voir Définir des [autorisations utilisateur et attribuer des rôles.](privacy-management-permissions.md)

### <a name="manage-settings"></a>Gérer les paramètres

La Paramètres page est accessible via la roulette d’engrenage dans le coin supérieur droit des pages principales de la gestion de la confidentialité. Il permet aux administrateurs de gestion de la confidentialité de configurer les propriétés essentielles dans la gestion de la confidentialité.

Vous pouvez passer en revue la configuration par défaut et effectuer les ajustements souhaités avant de commencer. Pour en savoir plus sur vos options, voir [Gérer les paramètres de gestion de la confidentialité.](privacy-management-settings.md)

## <a name="get-initial-data-insights"></a>Obtenir des informations sur les données initiales

Une fois que vous êtes passé à la gestion de la confidentialité, vous arrivez à la page **Vue d’ensemble.** Cette page fournit des informations sur les données personnelles stockées dans votre environnement Microsoft 365 afin de vous aider à identifier rapidement les problèmes, à identifier les indicateurs de risque et à prendre des mesures pour résoudre les problèmes. Votre vue d’ensemble doit être remplie avec les informations initiales dans les 24 premières heures de l’inscription. À mesure que vous continuez d’utiliser la gestion de la confidentialité, la page de vue d’ensemble s’actualise pour continuer à fournir des informations actuelles.

Pour obtenir des informations supplémentaires sur vos données au fil du temps, votre **page** de profil de données fournit davantage de visualisations et d’analyses et vous offre une vue d’ensemble des données de votre organisation par emplacement géographique et par service Microsoft 365.

Pour en savoir plus sur ces pages, voir [Rechercher et visualiser vos données.](privacy-management-data-profile.md)

## <a name="get-started-with-default-policies"></a>Mise en place des stratégies par défaut 

La gestion de la confidentialité vous aidera à lancer votre processus d’évaluation des données en créant trois stratégies avec des paramètres par défaut, à l’aide des modèles de réduction des données, de surexposation des données et de transferts de données. Ces stratégies sont en cours d’application par défaut, mais ne déclenchent pas automatiquement les messages de notification ou les invites de correction. Après votre configuration initiale, vous pouvez continuer à créer et personnaliser vos propres stratégies. Pour plus d’informations, voir [Créer et gérer des stratégies.](privacy-management-policies.md)
