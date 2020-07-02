---
title: Programme d’installation du score de conformité Microsoft (aperçu)
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
description: Découvrez comment configurer et commencer à utiliser le score de conformité Microsoft, ce qui permet de simplifier et d’automatiser les évaluations des risques.
ms.openlocfilehash: f7a501d0ede0d7635e20581774ce51a599dde65b
ms.sourcegitcommit: 0650da0e54a2b484a3156b3aabe44397fbb38e00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "45016189"
---
# <a name="compliance-score-preview-setup"></a>Programme d’installation du score de conformité (aperçu)

**Dans cet article :** Découvrez comment **accéder** au score de conformité, définir **les rôles et les autorisations**et configurer les **mises à jour automatiques du score de sécurité**. Cet article décrit également les pages de score de conformité principales : **votre tableau de bord**, la page actions d’amélioration, la page solutions et la page évaluations.

## <a name="before-you-begin"></a>Avant de commencer

L’administrateur général de Microsoft 365 de votre organisation sera probablement le premier utilisateur à accéder au score de conformité. Nous vous recommandons de vous connecter à l’administrateur général et de définir les autorisations utilisateur comme indiqué ci-dessous lorsque vous visitez le score de conformité pour la première fois.

## <a name="sign-in"></a>Connexion

1. Accédez au [Centre de conformité microsoft 365](https://compliance.microsoft.com/) et **Connectez-vous** à l’aide de votre compte d’administrateur global Microsoft 365.
2. Sélectionnez **score de conformité** dans le volet de navigation de gauche. Vous devez ensuite voir votre [tableau de bord de score de conformité avec votre score](#understand-the-compliance-score-dashboard).

Le lien direct vers le score de conformité de l’accès est [https://compliance.microsoft.com/compliancescore](https://compliance.microsoft.com/compliancescore) .

## <a name="set-user-permissions-and-assign-roles"></a>Définir les autorisations utilisateur et affecter des rôles

Le score de conformité utilise un modèle d’autorisation de contrôle d’accès basé sur un rôle (RBAC). Seuls les utilisateurs auxquels un rôle est attribué peuvent accéder au score de conformité, et les actions autorisées par chaque utilisateur sont restreintes par type de rôle.

### <a name="where-to-set-permissions"></a>Où définir les autorisations

La personne qui détient le rôle d’administrateur global pour votre organisation peut définir des autorisations utilisateur dans [Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal) ou dans le [Gestionnaire de conformité](compliance-manager-overview.md#permissions). Une fois les rôles définis dans l’un de ces emplacements, les utilisateurs peuvent accéder au score de conformité ainsi qu’au gestionnaire de conformité.

### <a name="role-types"></a>Types de rôles

Le tableau ci-dessous montre comment chaque [rôle Azure ad](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles) correspond aux rôles du gestionnaire de conformité existants et aux fonctions autorisées par chaque rôle. Les utilisateurs doivent disposer au moins du rôle de lecteur global Azure AD pour accéder au score de conformité.


| L’utilisateur peut : | Rôle Azure AD | Rôle du gestionnaire de conformité | 
| :------------- | :-------------: | :------------: |
| **Lire mais ne pas modifier les données**| Lecteur global Azure AD  | Lecteur global Azure AD | 
| **Lire mais ne pas modifier les données**| Lecteur Sécurité | Lecteur du gestionnaire de conformité  | 
| **Modifier des données**| Administrateur de conformité | Collaborateur du gestionnaire de conformité | 
| **Modifier les résultats des tests**| Administrateur de conformité | Évaluateur du gestionnaire de conformité | 
| **Gérer les évaluations, et les données de modèle et de client**| Administrateur de conformité<br>Administrateur de conformité des données<br>Administrateur de sécurité | Administrateur du gestionnaire de conformité | 
| **Affecter des utilisateurs**| Administrateur général | Administrateur de portail | 

> [!NOTE]
> Lorsque vous passez du score de conformité au gestionnaire de conformité pour effectuer une tâche pendant la préversion publique, votre navigateur ouvre un nouvel onglet et une boîte de dialogue s’affiche. Dans la section supérieure avec l’en-tête «déjà un client des services Cloud Microsoft ? Connectez-vous à votre compte, «sélectionnez **connexion** pour accéder au gestionnaire de conformité. Vous n’avez pas besoin de saisir de nouveau vos informations d’identification.

## <a name="configure-automatic-secure-score-updates"></a>Configurer les mises à jour automatiques du score de sécurité

Par défaut, les mises à jour automatiques des [scores sécurisés](../security/mtp/microsoft-secure-score-new.md) sont activées pour tous les nouveaux clients. Toutes les actions surveillées par le score sécurisé mettent automatiquement à jour l’état de la même action dans le score de conformité.

Votre administrateur général peut gérer ce paramètre pour désactiver les mises à jour automatiques pour toutes les actions ou définir des mises à jour pour les actions individuellement.

Lors de la préversion publique, vous devez accéder au portail d’approbation de service Microsoft (où se trouve le gestionnaire de conformité) pour gérer les mises à jour du score sécurisé.

Pour gérer les mises à jour automatiques du score de sécurité, procédez comme suit :

1. Connectez-vous au [portail d’approbation de service](https://servicetrust.microsoft.com) avec votre compte d’administrateur général.

2. Dans la barre de menus supérieure du portail d’approbation de service, sous **autres**, sélectionnez **administrateur** , puis **paramètres**.

3. Sous l’onglet **score sécurisé** , sélectionnez le bouton correspondant pour **activer toutes les actions**, **désactiver pour toutes les actions**ou **définir par action.**

Si vous choisissez **définir par action,** suivez ces étapes supplémentaires pour activer les mises à jour du score de sécurité pour des actions individuelles :

4. Sélectionnez **Gestionnaire de conformité** dans le menu supérieur (ne sélectionnez pas « gestionnaire de conformité (classique) »).

5. Sélectionnez **gestion des clients** dans le coin supérieur droit de votre écran.

6. Dans le volet **actions client** , recherchez l’action souhaitée avec des points de suspension (**...**) dans la colonne **actions affectées** . Cliquez sur les ellipses et sélectionnez **modifier.**

7. Basculez le commutateur de basculement de **mise à jour continue de score de sécurité** **sur activé.**

8. Sélectionnez **Enregistrer.** Score de sécurité la surveillance continue est maintenant activée pour cette action.

**Remarque :** Seul l’administrateur général peut activer ou désactiver les mises à jour automatiques pour toutes les actions. L’administrateur du gestionnaire de conformité peut activer les mises à jour automatiques pour des actions individuelles, mais pas pour toutes les actions de manière globale.

#### <a name="learn-more"></a>Si vous souhaitez en savoir plus

[En savoir plus sur la gestion des mises à jour du score sécurisé](compliance-manager-release-notes.md#secure-score).

## <a name="understand-the-compliance-score-dashboard"></a>Comprendre le tableau de bord de score de conformité

Le tableau de bord de score de conformité est conçu pour vous offrir une vue instantanée de votre position actuelle en matière de conformité.

![Score de conformité-tableau de bord](../media/compliance-score-dashboard.png "Tableau de bord de score de conformité")

### <a name="overall-compliance-score"></a>Score de conformité global

Votre score de conformité est bien visible en haut. Elle indique un pourcentage basé sur des points réalisables pour effectuer les actions d’amélioration qui répondent aux normes et réglementations clés en matière de protection des données.

Lorsque vous accédez au score de conformité pour la première fois, votre score initial est basé sur la base de [données de protection des données Microsoft 365](compliance-score-methodology.md#initial-score-based-on-microsoft-365-data-protection-baseline)intégrée, un ensemble de contrôles qui inclut des normes et des réglementations industrielles communes. Le score de conformité analyse vos solutions Microsoft 365 existantes et vous fournit une évaluation initiale basée sur vos paramètres de confidentialité et de sécurité actuels. À mesure que vous ajoutez des évaluations pertinentes pour votre organisation, votre score devient plus significatif pour vous.

#### <a name="learn-more"></a>Si vous souhaitez en savoir plus
[Comprendre comment le score de conformité est calculé](compliance-score-methodology.md).

### <a name="key-improvement-actions"></a>Actions d’amélioration clés

Cette section répertorie les principales actions d’amélioration que vous pouvez effectuer dès à présent pour tirer le plus grand impact positif sur votre score de conformité global.

### <a name="solutions-that-affect-your-score"></a>Solutions ayant une incidence sur votre score

Cette section présente les solutions qui contiennent les actions les plus précieuses pour avoir un impact positif sur votre score, ainsi que le nombre d’actions d’amélioration en suspens dans chaque solution.

### <a name="compliance-score-breakdown"></a>Répartition du score de conformité

Cette section fournit une vue plus détaillée de votre score de deux manières différentes :

- **Catégories**: indique le pourcentage de votre score global dans les catégories de protection des données, telles que « protéger les informations » ou « gérer les appareils ».
- **Évaluations**: indique le pourcentage de votre progression dans la gestion des évaluations pour des normes, réglementations ou lois spécifiques en matière de protection des données, telles que RGPD ou NIST 800-53.

### <a name="filtering-your-dashboard-view"></a>Filtrage de l’affichage du tableau de bord

Vous pouvez filtrer votre vue de tableau de bord pour afficher uniquement les éléments liés à des réglementations, des normes, des solutions, un type d’action, des groupes d’évaluation ou des catégories de protection des données spécifiques. De cette manière, le filtrage de votre affichage filtre le score sur votre tableau de bord, indiquant le nombre de points que vous avez obtenus au total de points possibles en fonction de vos critères de filtre.

Pour appliquer des filtres :

1. Sélectionnez **filtre** dans le coin supérieur droit du tableau de bord.
2. Sélectionnez vos critères de filtre dans le volet flyout **filtres** , puis sélectionnez **appliquer**.

Une fois que vous avez appliqué un filtre, vous verrez votre score ajusté en temps réel. Le pourcentage du score de conformité et les informations de répartition, ainsi que les actions et les solutions d’amélioration, ne concernent désormais que les données couvertes par vos critères de filtre. Si vous vous déconnectez du score de conformité, l’affichage filtré reste lorsque vous vous reconnectez.

Pour supprimer des filtres :

- Sur le titre **filtres appliqués** au-dessus de votre score de conformité, sélectionnez le **X** en regard du filtre individuel que vous souhaitez supprimer ; des
- Sélectionnez **filtre** dans le coin supérieur droit de votre tableau de bord, puis sélectionnez **effacer les filtres**.

## <a name="improvement-actions-page"></a>Page actions d’amélioration

Les [actions d’amélioration](compliance-score-improvement-actions.md) centralisent vos activités de conformité et vous aident à vous aligner sur les normes et réglementations en matière de protection des données. Chaque action d’amélioration fournit des conseils détaillés sur la mise en œuvre et un lien permettant de vous lancer dans la solution appropriée. Des actions peuvent être attribuées à des utilisateurs de votre organisation pour effectuer le travail d’implémentation et de test. Vous pouvez également stocker la documentation, les notes et les mises à jour de l’état des enregistrements au cours de l’action d’amélioration.

### <a name="view-your-improvement-actions"></a>Afficher vos actions d’amélioration

Le tableau de bord de score de conformité affiche vos **actions d’amélioration clés**, c’est-à-dire celles dont les points les plus disponibles concernent les problèmes les plus importants.

Pour afficher toutes vos actions d’amélioration, sélectionnez l’onglet **actions d’amélioration** de votre tableau de bord. Sinon, sélectionnez **afficher toutes les actions d’amélioration** sous la liste des actions d’amélioration de clé sur votre tableau de bord.

Si vous avez une longue liste d’actions, il peut être utile de filtrer votre vue. Sélectionnez **filtre** dans le coin supérieur droit de la liste actions. Lorsque le volet flyout **filtres** apparaît, sélectionnez vos critères en fonction des réglementations, des normes, de la solution et du groupe. Vous pouvez également personnaliser votre affichage en sélectionnant **groupe** dans le coin supérieur droit. Dans le menu déroulant, sélectionnez pour afficher par groupe, solution, catégorie, type d’action ou état.

L’affichage par défaut de cette page n’affiche pas les actions d’amélioration dont l’état de test est **réussite**. Pour afficher les actions qui ont été testées, activez la case à cocher **passé** dans le volet flyout filtres. Uniquement les actions dont l’état de test est **passé** vers votre score.

La page actions d’amélioration affiche les points de données suivants pour chaque action d’amélioration :

- **Impact sur le score**: les points par lesquels votre score global augmentera lors de l’exécution de l’action
- **Réglementation**: la réglementation ou la norme relative à l’action
- **Groupe**: groupe auquel vous avez affecté l’action.
- **Solutions**: la solution à partir de laquelle vous pouvez effectuer l’action
- **Évaluations**: l’évaluation (qui organise les contrôles afin de respecter un certain objectif de conformité) dans lequel l’action réside.
- **Catégories**: catégorie de protection des données associée (par exemple, protection des informations, gestion des appareils, etc.)
- **État du test**:
    - **Aucun** – pas de mise à jour d’État enregistrée
    - **Non évalué** -le test n’a pas commencé
    - **Réussite** de l’implémentation réussie
    - Échec du test à **faible risque** pour les tests, risque faible
    - **Risque moyen échoué** -test ayant échoué, risque moyen
    - Échec de test à **haut risque ayant** échoué, à risque élevé
    - **Non inclus dans l’étendue** : l’action n’est pas dans l’étendue de l’évaluation et n’influe pas sur votre score
    - **À détecter** : pour le test manuel, indique qu’une action a été implémentée, mais qu’elle n’a pas été testée ; pour le test automatisé, indique qu’une action attend un résultat d’automatisation
    - **Impossible de détecter** : l’État automatisé ne peut pas être déterminé.
    - **Partiellement testé** : score automatique qui récompense les points partiels
- **Points atteints**: nombre de points obtenus du maximum possible

#### <a name="learn-more"></a>Si vous souhaitez en savoir plus
[Découvrez comment affecter et exécuter des actions d’amélioration](compliance-score-improvement-actions.md).

## <a name="solutions-page"></a>Page solutions

La page solutions indique le partage des points gagnés et potentiels, tel qu’il est organisé par la solution. L’affichage de vos points restants et des actions d’amélioration à partir de cette vue vous permet de comprendre les solutions qui nécessitent une attention plus immédiate.

Recherchez la page solutions en sélectionnant l’onglet **solutions** dans votre tableau de bord de score de conformité. Vous pouvez également sélectionner **afficher toutes les solutions** sous **solutions qui affectent votre score** dans la section supérieure droite de votre tableau de bord.

### <a name="filtering-your-solutions-view"></a>Filtrage de l’affichage des solutions

Pour filtrer votre vue de solutions :

1. Sélectionnez **filtre** dans le coin supérieur gauche de votre liste évaluations.
2. Dans le volet flyout **filtres** , activez la case à cocher en regard des critères de votre choix (normes et réglementations, solution, type d’action, groupe du gestionnaire de conformité, catégorie).
3. Sélectionnez le bouton **appliquer** . Le volet de filtre se ferme et vous verrez votre affichage filtré.

Vous pouvez également modifier votre vue pour afficher les évaluations par groupe, produit ou réglementation en sélectionnant le type de regroupement dans le menu déroulant **groupe** au-dessus de votre liste d’évaluations.

### <a name="taking-actions-from-the-solution-page"></a>Prendre des mesures à partir de la page de solution

La page solutions affiche les solutions de votre organisation qui sont connectées à des actions d’amélioration. Le tableau répertorie chaque contribution de chaque solution à votre score global, les points d’amélioration de score obtenus et possibles au sein de cette solution, ainsi que le nombre d’actions d’amélioration restantes regroupées dans cette solution qui peuvent augmenter votre score.

Il existe deux façons d’effectuer une action à partir de cet écran :

1. Sur la ligne de la solution souhaitée, sous la colonne **actions restantes** , sélectionnez le numéro du lien hypertexte. Vous verrez une vue filtrée de l’écran actions d’amélioration montrant les actions d’amélioration non testées pour cette solution.

2. Sur la ligne de la solution voulue, sous la colonne **ouvrir une solution** , sélectionnez **ouvrir**. Vous verrez la solution ou l’emplacement dans les centres de sécurité et de conformité Microsoft 365 et Office 365, où vous pouvez prendre l’action recommandée.

## <a name="assessments-page"></a>Page évaluations

La page évaluations répertorie toutes les [évaluations](compliance-score-assessments.md) que vous avez configurées pour votre organisation. Votre dénominateur de score de conformité est déterminé par toutes vos évaluations suivies. Plus vous ajoutez d’évaluations, plus les actions d’amélioration que vous voyez sur votre page actions d’amélioration et plus votre dénominateur de score est élevé.

Cette page résume les informations clés de chaque évaluation :

- **Évaluation**: nom de l’évaluation
- **État**:
    - **Complet** -tous les contrôles ont l’État « réussite », ou au moins un est passé et le reste est « hors de portée »
    - **Incomplet** : au moins un contrôle a l’État « failed » (échec).
    - **Aucun** : tous les contrôles n’ont pas été testés
    - **En cours** -les actions d’amélioration ont un autre statut, y compris « en cours », « crédit partiel » ou «non détecté
- **Progression**de l’évaluation : pourcentage du travail effectué vers l’achèvement, mesuré par le nombre de contrôles correctement testés
- **Vos actions d’amélioration**: nombre d’actions terminées pour satisfaire l’implémentation de vos contrôles
- **Actions Microsoft**: nombre d’actions terminées pour répondre à l’implémentation des contrôles Microsoft
- **Group**: nom du groupe auquel l’évaluation appartient
- **Produit**: service Microsoft 365 associé
- **Réglementation**: norme, politique ou loi réglementaire qui s’applique à l’évaluation

### <a name="filtering-your-assessments-view"></a>Filtrage de l’affichage des évaluations

Pour filtrer les évaluations, procédez comme suit :

1. Sélectionnez **filtre** dans le coin supérieur gauche de votre liste évaluations.
2. Dans le volet flyout **filtres** , vérifiez les critères de votre choix.
3. Sélectionnez le bouton appliquer. Le volet de filtre se ferme et vous verrez votre affichage filtré.

Vous pouvez également modifier votre vue pour afficher les évaluations par groupe, produit ou réglementation en sélectionnant le type de regroupement dans le menu déroulant **groupe** au-dessus de votre liste d’évaluations.

### <a name="default-assessment"></a>Évaluation par défaut

Par défaut, vous verrez l’évaluation de la [base de données de protection des données Microsoft 365](compliance-score-methodology.md#initial-score-based-on-microsoft-365-data-protection-baseline) sur la page évaluations. Le score de conformité offre également plusieurs [modèles](compliance-score-templates.md) prêts à l’emploi à partir desquels créer des évaluations.

## <a name="next-step"></a>Étape suivante
Personnalisez le score de conformité en [configurant des évaluations](compliance-score-assessments.md).