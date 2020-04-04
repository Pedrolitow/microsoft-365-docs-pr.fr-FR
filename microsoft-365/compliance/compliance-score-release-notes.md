---
title: Notes de publication du score de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Notes de publication et problèmes connus pour le score de conformité Microsoft (aperçu), une fonctionnalité du centre de conformité M365 qui permet de simplifier et d’automatiser les évaluations des risques.
ms.openlocfilehash: dd7c99d2f0a86826be7803dc36e390250a4fc37b
ms.sourcegitcommit: ff62dd99fa0d4e780da25dc622f93ddc8f7f95a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "43141549"
---
# <a name="microsoft-compliance-score-preview-release-notes"></a>Notes de publication du score de conformité Microsoft (aperçu)

La préversion publique du score de conformité Microsoft vous permet d’accéder en avant-première aux nouvelles fonctionnalités et mises à jour. Consultez régulièrement cette page pour découvrir les nouveautés.

Le score de conformité est une nouvelle fonctionnalité du [Centre de conformité Microsoft 365](microsoft-365-compliance-center.md) qui calcule un score basé sur les risques en mesurant la progression de l’exécution des actions recommandées qui permettent de réduire les risques de conformité.

## <a name="new-templates-for-assessments"></a>Nouveaux modèles d’évaluation

De nouveaux modèles préconfigurés pour les évaluations sont publiés en production pour le score de conformité (aperçu) dès qu’ils sont disponibles. Consultez la [liste complète des modèles ici](compliance-score.md#templates). Les modèles récemment ajoutés sont les suivants :

- Loi sur la protection générale des données du Brésil (LGPD)
- IRAP/Australian Government ISM (Preview)
- ISO 27701:2019
- SOC 1
- SOC 2

## <a name="improvements-in-managing-assessments"></a>Améliorations apportées à la gestion des évaluations

La dernière version du gestionnaire de conformité en avril 2020 inclut des mises à jour qui simplifient la création et la personnalisation des évaluations et les maintiennent mises à jour. Pour plus d’informations, consultez les [notes de publication du gestionnaire de conformité](compliance-manager-release-notes.md) .

## <a name="language-support"></a>Prise en charge linguistique

Le score de conformité est désormais disponible dans les langues suivantes, en plus de l’anglais : chinois (simplifié), chinois (traditionnel), français, allemand, italien, japonais, coréen, portugais (Brésil), russe et espagnol.

## <a name="common-actions-will-synch-status-across-groups"></a>Les actions courantes synchronisent l’état entre les groupes

Si votre organisation dispose de plusieurs groupes d’évaluations, le comportement des actions **techniques** (c’est-à-dire, des actions affectant l’ensemble de votre organisation) a changé. Toutes les actions dupliquées entre les groupes ont été regroupées en une seule action. Cette action unique contient toutes les notes et preuves téléchargées des versions en double. Avec cette modification, les actions techniques se comporteront désormais comme lorsqu’elles appartenaient au même groupe. Toutes les modifications apportées à l’action dans un groupe ou une évaluation apparaissent maintenant dans toutes les instances. L' **État de mise en œuvre**, la **Date de mise en œuvre**, l' **État du test**et la **Date** de test reflètent les mises à jour les plus récentes.

## <a name="compliance-score-relationship-to-compliance-manager"></a>Relation avec le score de conformité avec le gestionnaire de conformité

De nombreuses fonctions gérées dans le gestionnaire de conformité peuvent désormais être réalisées dans le score de conformité. Toutefois, certaines fonctions continuent de fonctionner dans le gestionnaire de conformité. Gardez les points suivants à l’esprit lorsque vous utilisez le score de conformité et le gestionnaire de conformité lors de la préversion publique :

- **Gestion des évaluations**: les utilisateurs peuvent consulter les évaluations et leurs informations d’État dans le score de conformité. Toutefois, les utilisateurs peuvent uniquement effectuer des tâches de gestion de l’évaluation dans le gestionnaire de conformité ([afficher les instructions](working-with-compliance-manager.md#assessments)). Voici des exemples de ces tâches :
    - Créer et copier des évaluations
    - Exporter des évaluations
    - Archives d’archivage
    - Afficher les évaluations archivées
 - **Création de modèles pour les évaluations**: 
   - Les utilisateurs doivent accéder au gestionnaire de conformité pour créer de nouveaux modèles et modifier des [modèles](working-with-compliance-manager.md#templates)existants. 
   - Lors de la création d’un modèle, vous devez inclure des dimensions pour le **produit** et la **certification** afin de garantir l’affichage du modèle dans le score de conformité.
 - **Définition des autorisations**: score de conformité les utilisateurs qui n’ont pas déjà des autorisations dans le gestionnaire de conformité ont besoin de leurs autorisations définies dans le centre de conformité Microsoft 365 ([en savoir plus](compliance-score-setup.md#set-user-permissions-and-assign-roles)).
- **Transfert de données**: les organisations avec des données dans le gestionnaire de conformité verront ces données dans le score de conformité, et la même est la même.
- **Connexion au gestionnaire de conformité à partir du score de conformité**: si un utilisateur est connecté à un score de conformité et sélectionne un lien pour accéder au gestionnaire de conformité, il n’a pas besoin de se reconnecter. Après avoir cliqué sur le lien, un nouvel onglet s’ouvre dans votre navigateur avec une boîte de dialogue. Dans la section supérieure avec l’en-tête «déjà un client des services Cloud Microsoft ? Connectez-vous à votre compte, «cliquez sur le bouton de **connexion** pour vous connecter automatiquement au gestionnaire de conformité.

## <a name="known-issues-in-compliance-score-preview"></a>Problèmes connus dans le score de conformité (aperçu)

Les sections suivantes couvrent les problèmes connus à résoudre dans les versions à venir du score de conformité.

### <a name="long-load-times-for-non-admin-users"></a>Temps de chargement long pour les utilisateurs non-administrateurs
Score de conformité les utilisateurs qui détiennent des rôles autres qu’un rôle d’administrateur peuvent avoir des temps de chargement longs lors de la tentative de connexion. L’actualisation de votre navigateur permet de résoudre ce problème. (En savoir plus sur les [rôles de score de conformité](compliance-score-setup.md#set-user-permissions-and-assign-roles).)

### <a name="supported-browsers"></a>Navigateurs pris en charge

- Les versions les plus récentes de Microsoft Edge, chrome et Safari sont prises en charge.
- Les données mises à jour ne s’affichent pas tant que votre navigateur n’est pas actualisé.
- Internet Explorer n’est pas pris en charge.
