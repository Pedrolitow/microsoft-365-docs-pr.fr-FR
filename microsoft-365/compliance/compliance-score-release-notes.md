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
ms.openlocfilehash: 6678ec03d2cd87a97244acaa55a15483d78dd632
ms.sourcegitcommit: 3ddcf08e8deec087df1fe524147313f1cb12a26d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "45022191"
---
# <a name="microsoft-compliance-score-preview-release-notes"></a>Notes de publication du score de conformité Microsoft (aperçu)

**Dans cet article :** Cette **page présente les nouveautés de** la préversion publique du score de [conformité Microsoft](compliance-score.md), qui vous permet d’accéder en avant-première aux nouvelles fonctionnalités.

## <a name="assessment-creation-and-management-functionality"></a>Fonctionnalités de création et de gestion de l’évaluation

La version de juin 2020 ajoute des fonctionnalités permettant aux utilisateurs de créer, supprimer et gérer leurs évaluations directement dans le score de conformité. Auparavant, toutes les gestions d’évaluation résidaient dans le gestionnaire de conformité. Lorsque vous créez ou modifiez une évaluation dans le score de conformité, les mises à jour sont représentées dans le gestionnaire de conformité. De même, toutes les tâches d’évaluation effectuées dans le gestionnaire de conformité doivent apparaître dans le score de conformité. Découvrez comment [gérer les évaluations dans le score de conformité](compliance-score-assessments.md). Notez que la création et la modification du modèle sont toujours gérées dans le gestionnaire de conformité.

## <a name="new-templates-for-assessments"></a>Nouveaux modèles d’évaluation

Les nouveaux modèles prêts à l’emploi pour les évaluations sont publiés dans le score de conformité dès qu’elles sont disponibles. Consultez la [liste complète des modèles ici](compliance-score-templates.md). Récemment ajouté :

- Résolution de la sécurité des informations de Dubaï (DGISR)

## <a name="compliance-score-relationship-to-compliance-manager"></a>Relation avec le score de conformité avec le gestionnaire de conformité

De nombreuses fonctions gérées dans le gestionnaire de conformité peuvent désormais être réalisées dans le score de conformité. Toutefois, certaines fonctions continuent de fonctionner dans le gestionnaire de conformité. Gardez les points suivants à l’esprit lorsque vous utilisez le score de conformité et le gestionnaire de conformité lors de la préversion publique :

 - **Création de modèles pour les évaluations**: 
   - Les utilisateurs doivent accéder au gestionnaire de conformité pour [créer de nouveaux modèles et modifier des modèles existants](working-with-compliance-manager.md#templates).
   - Les nouveaux modèles doivent inclure des dimensions pour le **produit** et la **certification**.
 - **Définition des autorisations**: score de conformité les utilisateurs qui n’ont pas déjà des autorisations dans le gestionnaire de conformité ont besoin de leurs autorisations définies dans le centre de conformité Microsoft 365 ([en savoir plus](compliance-score-setup.md#set-user-permissions-and-assign-roles)).
- **Transfert de données**: les organisations dont les données se trouvent dans le gestionnaire de conformité voient ces données dans le score de conformité, et la même est la même.
- **Connexion au gestionnaire de conformité à partir du score de conformité**: si un utilisateur est connecté à un score de conformité et sélectionne un lien pour accéder au gestionnaire de conformité, il n’a pas besoin de se reconnecter. Après avoir cliqué sur le lien, un nouvel onglet s’ouvre dans votre navigateur avec une boîte de dialogue. Dans la section supérieure avec l’en-tête «déjà un client des services Cloud Microsoft ? Connectez-vous à votre compte, «cliquez sur le bouton de **connexion** pour vous connecter automatiquement au gestionnaire de conformité.

## <a name="known-issues-in-compliance-score-preview"></a>Problèmes connus dans le score de conformité (aperçu)

Les sections suivantes couvrent les problèmes connus à résoudre dans les versions à venir du score de conformité.

### <a name="long-load-times-for-non-admin-users"></a>Temps de chargement long pour les utilisateurs non-administrateurs
Score de conformité les utilisateurs qui détiennent des rôles autres qu’un rôle d’administrateur peuvent avoir des temps de chargement longs lors de la tentative de connexion. L’actualisation de votre navigateur permet de résoudre ce problème. En savoir plus sur les [rôles de score de conformité](compliance-score-setup.md#set-user-permissions-and-assign-roles).

### <a name="supported-browsers"></a>Navigateurs pris en charge

- Les versions les plus récentes de Microsoft Edge, chrome et Safari sont prises en charge.
- Les données mises à jour ne s’affichent pas tant que votre navigateur n’est pas actualisé.
- Internet Explorer n’est pas pris en charge.
