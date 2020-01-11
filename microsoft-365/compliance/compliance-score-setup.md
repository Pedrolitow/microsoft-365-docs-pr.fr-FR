---
title: Programme d’installation du score de conformité Microsoft
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
description: Découvrez comment vous connecter, configurer des autorisations et comprendre votre tableau de bord pour le score de conformité Microsoft, ce qui vous permet de simplifier et d’automatiser les évaluations des risques.
ms.openlocfilehash: 79e93a102107433ed2b493a56381bc60ca544157
ms.sourcegitcommit: 40e83b22b74db8e37d65e0988d4c11de3aa541b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "41021910"
---
# <a name="microsoft-compliance-score-preview-setup"></a>Programme d’installation du score de conformité Microsoft (aperçu)

## <a name="before-you-begin"></a>Avant de commencer

L’administrateur général de Microsoft 365 de votre organisation sera probablement le premier utilisateur à accéder au score de conformité. Nous vous recommandons de vous connecter à l’administrateur général et de définir les autorisations utilisateur comme indiqué ci-dessous lorsque vous visitez le score de conformité pour la première fois.

## <a name="sign-in"></a>Se connecter

1. Accédez au [Centre de conformité microsoft 365](https://compliance.microsoft.com/) et **Connectez-vous** à l’aide de votre compte d’administrateur global Microsoft 365.
2. Sélectionnez **score de conformité** dans le volet de navigation de gauche. Vous devez ensuite voir votre [tableau de bord de score de conformité avec votre score](#understand-the-compliance-score-dashboard).

## <a name="set-user-permissions-and-assign-roles"></a>Définir les autorisations utilisateur et affecter des rôles

Le score de conformité utilise un modèle d’autorisation de contrôle d’accès basé sur un rôle (RBAC). Seuls les utilisateurs auxquels un rôle est attribué peuvent accéder au score de conformité, et les actions autorisées par chaque utilisateur sont restreintes par type de rôle.

### <a name="where-to-set-permissions"></a>Où définir les autorisations

L’administrateur général de votre organisation peut définir des autorisations utilisateur dans le centre de conformité Microsoft 365 ou dans Azure Active Directory (Azure AD). Une fois les rôles définis dans l’un de ces emplacements, les utilisateurs peuvent accéder au score de conformité (ainsi qu’au gestionnaire de conformité).

Notez que les rôles du gestionnaire de conformité existants **ne sont pas** transférés vers le score de conformité.  Cela signifie que si vous avez déjà affecté un rôle dans le gestionnaire de conformité, ce rôle ne vous accordera pas l’accès au score de conformité. Votre administrateur global devra définir des autorisations et un rôle pour vous dans le centre de conformité Microsoft 365 ou Azure AD pour pouvoir accéder au score de conformité.

### <a name="role-types"></a>Types de rôles

Le tableau ci-dessous montre comment chaque rôle du centre de conformité Microsoft 365 est mappé aux rôles du gestionnaire de conformité existants, ainsi qu’aux fonctions autorisées par chaque rôle.


| L’utilisateur peut : | Rôle du centre de conformité Microsoft 365 | Rôle du gestionnaire de conformité | 
| :------------- | :-------------: | :------------: |
| **Lire mais ne pas modifier les données**| Lecteur global Azure AD  | Lecteur global Azure AD | 
| **Lire mais ne pas modifier les données**| Lecteur Sécurité | Lecteur du gestionnaire de conformité  | 
| **Modifier des données**| Administrateur de conformité | Collaborateur du gestionnaire de conformité | 
| **Modifier les résultats des tests**| Administrateur de conformité | Évaluateur du gestionnaire de conformité | 
| **Gérer les évaluations, et les données de modèle et de client**| Administrateur de conformité<br>Administrateur de conformité des données<br>Administrateur de sécurité | Administrateur du gestionnaire de conformité | 
| **Affecter des utilisateurs**| Administrateur général | Administrateur de portail | 

> [!NOTE]
> Lorsque vous passez du score de conformité au gestionnaire de conformité pour effectuer une tâche (par exemple, pour gérer les évaluations), votre navigateur ouvre un nouvel onglet et une boîte de dialogue s’affiche. Dans la section supérieure avec l’en-tête «déjà un client des services Cloud Microsoft ? Connectez-vous à votre compte, «sélectionnez **connexion** pour accéder au gestionnaire de conformité ; vous n’avez pas besoin d’entrer de nouveau vos informations d’identification.

### <a name="how-to-set-permissions-and-roles-in-the-microsoft-365-compliance-center"></a>Procédure de définition des autorisations et des rôles dans le centre de conformité Microsoft 365

Pour définir des autorisations dans le centre de conformité Microsoft 365 :

1. Accédez au [Centre de conformité Microsoft 365](https://compliance.microsoft.com) et connectez-vous avec votre compte d’administrateur général.
2. Sélectionnez **autorisations** dans le volet de navigation de gauche. À partir de là, vous pouvez afficher les rôles et attribuer des autorisations.

## <a name="understand-the-compliance-score-dashboard"></a>Comprendre le tableau de bord de score de conformité

Le tableau de bord de score de conformité est conçu pour vous offrir une vue instantanée de votre position actuelle en matière de conformité.

![Score de conformité-tableau de bord](media/compliance-score-dashboard.png "Tableau de bord de score de conformité")

### <a name="overall-compliance-score"></a>Score de conformité global

Votre score de conformité, présenté en évidence en haut, indique un pourcentage basé sur les points qui sont parfaits pour terminer les actions d’amélioration en fonction des normes et des réglementations clés en matière de protection des données.

Lorsque vous accédez au score de conformité pour la première fois, votre score initial est basé sur la base de données de protection des données Microsoft 365 intégrée, un ensemble de contrôles qui inclut des normes et des réglementations industrielles communes. Étant donné que le score de conformité analyse votre système de solutions Microsoft 365 existantes, il fournit une évaluation initiale de votre position de conformité en fonction des paramètres de confidentialité et de sécurité actuellement activés par votre organisation.

À mesure que vous ajoutez des évaluations pertinentes pour votre organisation, votre score devient encore plus significatif. En savoir plus sur le [calcul de votre score](compliance-score-methodology.md).

### <a name="key-improvement-actions"></a>Actions d’amélioration clés

Cette section répertorie les principales actions d’amélioration que vous pouvez effectuer dès à présent pour tirer le plus grand impact positif sur votre score de conformité global. Il répertorie les actions qui ne sont pas terminées ou qui ont échoué avec l’évaluation avec des risques élevés.

### <a name="solutions-that-affect-your-score"></a>Solutions ayant une incidence sur votre score

Cette section présente les solutions qui contiennent des actions les plus susceptibles d’avoir un impact positif sur votre score, ainsi que le nombre d’actions d’amélioration en suspens dans chaque solution.

### <a name="compliance-score-breakdown"></a>Répartition du score de conformité

Cette section fournit une vue plus détaillée de votre score de deux manières différentes :

- **Catégories**: indique le pourcentage de votre score global dans les catégories de protection des données, telles que « protéger les informations » ou « gérer les appareils ».
- **Évaluations**: indique le pourcentage de votre progression dans la gestion des évaluations pour des normes, réglementations ou lois spécifiques en matière de protection des données, telles que RGPD ou NIST 800-53.

### <a name="filtering-your-dashboard-view"></a>Filtrage de l’affichage du tableau de bord

Vous pouvez filtrer votre vue de tableau de bord pour n’afficher que les éléments liés à des réglementations, des normes, des solutions, un type d’action, [des groupes d’évaluations que vous configurez ou des](working-with-compliance-manager.md#groups)catégories de protection des données. De cette manière, le filtrage de votre affichage filtre le score sur votre tableau de bord, indiquant le nombre de points que vous avez obtenus au total de points possibles en fonction de vos critères de filtre.

Pour appliquer des filtres :

1. Sélectionnez **filtre** dans le coin supérieur droit du tableau de bord.
2. Sélectionnez vos critères de filtre dans le volet **filtres** de menu volant, puis sélectionnez **appliquer**.

Une fois qu’un filtre est appliqué, votre score est ajusté en temps réel. Le pourcentage du score de conformité et les informations de répartition, ainsi que les actions et les solutions d’amélioration, ne concernent désormais que les données couvertes par vos critères de filtre. Si vous vous déconnectez du score de conformité, l’affichage filtré reste lorsque vous vous reconnectez.

Pour supprimer des filtres :

- Sur le titre **filtres appliqués** au-dessus de votre score de conformité, sélectionnez le **X** en regard du filtre individuel que vous souhaitez supprimer ; des
- Sélectionnez **filtre** dans le coin supérieur droit de votre tableau de bord, puis sélectionnez **effacer les filtres**.

## <a name="next-step"></a>Étape suivante

Consultez la rubrique [utilisation du score de conformité](working-with-compliance-score.md) pour comprendre le flux de travail sur la façon d’effectuer des actions pour améliorer votre score.