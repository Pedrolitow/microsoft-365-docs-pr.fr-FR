---
title: Prise en main du gestionnaire de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Définissez les autorisations et les rôles utilisateur du gestionnaire de conformité Microsoft, et configurez le test automatisé des actions. Gérer l’historique des utilisateurs et filtrer votre vue de tableau de bord.
ms.openlocfilehash: 043a52e2817e770671c2ef8876049f6bbe0285ee
ms.sourcegitcommit: 9d8d071659e662c266b101377e24549963e43fef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "48368137"
---
# <a name="get-started-with-compliance-manager"></a>Prise en main du Gestionnaire de conformité

**Dans cet article :** Cet article vous aide à configurer le gestionnaire de conformité. Découvrez comment **accéder** au gestionnaire de conformité, **définir des rôles et des autorisations**, et configurer le **test automatique des actions d’amélioration**. Parcourez **votre tableau de bord du gestionnaire de conformité** et comprenez les pages principales : la page actions d’amélioration, la page solutions, la page évaluations et la page modèles d’évaluation.

## <a name="who-can-access-compliance-manager"></a>Qui peut accéder au gestionnaire de conformité

Le gestionnaire de conformité est disponible pour les organisations disposant de licences Office 365 et Microsoft 365. Les fonctionnalités de gestion et de disponibilité de l’évaluation dépendent de votre contrat de licence.  [Afficher les détails de description de service](https://go.microsoft.com/fwlink/?linkid=2132371).

## <a name="before-you-begin"></a>Avant de commencer

L’administrateur général de Microsoft 365 de votre organisation sera probablement le premier utilisateur à accéder au gestionnaire de conformité. Nous vous recommandons de vous connecter à l’administrateur général et de définir les autorisations utilisateur comme indiqué ci-dessous lorsque vous visitez le gestionnaire de conformité pour la première fois.

## <a name="sign-in"></a>Se connecter

1. Accédez au [Centre de conformité microsoft 365](https://compliance.microsoft.com/) et **Connectez-vous** à l’aide de votre compte d’administrateur général Microsoft 365.
2. Sélectionnez **Gestionnaire de conformité** dans le volet de navigation de gauche. Vous arrivez à votre [tableau de bord gestionnaire de conformité](#understand-the-compliance-manger-dashboard).

Le lien direct vers le gestionnaire de conformité Access est [https://compliance.microsoft.com/compliancemanager](https://compliance.microsoft.com/compliancemanager) .

## <a name="set-user-permissions-and-assign-roles"></a>Définir les autorisations utilisateur et affecter des rôles

Le gestionnaire de conformité utilise un modèle d’autorisation de contrôle d’accès basé sur un rôle (RBAC). Seuls les utilisateurs auxquels un rôle est attribué peuvent accéder au gestionnaire de conformité, et les actions autorisées par chaque utilisateur sont restreintes par [type de rôle](#role-types).

### <a name="where-to-set-permissions"></a>Où définir les autorisations

La personne qui détient le rôle d’administrateur global pour votre organisation peut définir des autorisations utilisateur dans le centre de conformité Microsoft 365, ainsi que dans Azure Active Directory (Azure AD).

Pour définir des autorisations et attribuer des rôles à partir du centre de conformité Microsoft 365, suivez les étapes ci-dessous :

1. Sélectionnez **autorisations** sur le volet de navigation de gauche depuis n’importe quel endroit du [Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

2. Dans la partie supérieure, sélectionnez le lien **« pour afficher et gérer les rôles dans Office 365, cliquez ici. »** Un nouvel onglet s’ouvre dans le centre de conformité Office 365 Security & ([Découvrez pourquoi vous êtes redirigé](microsoft-365-compliance-center.md#frequently-asked-questions)).

3. Recherchez le groupe de rôles auquel vous souhaitez ajouter un ou plusieurs utilisateurs, puis activez la case à cocher à gauche du nom du groupe. (Reportez-vous à la [liste des rôles et des fonctions associées ci-dessous](#role-types). Les noms des groupes de rôles imitent le nom du rôle.)

4. Dans le volet flyout de ce groupe, sélectionnez **modifier** sous l’en-tête **membres** .

5. Sélectionnez **choisir les membres**. Une autre fenêtre de menu volant s’affiche.

6. Sélectionnez **+ Ajouter** pour choisir un ou plusieurs utilisateurs à ajouter au groupe.

7. Activez la case à cocher en regard des noms que vous souhaitez ajouter, puis cliquez sur le bouton **Ajouter** en bas.

8. Lorsque vous avez fini d’affecter des utilisateurs, sélectionnez **Terminer**, puis **Enregistrer**, puis **Fermer**.

##### <a name="more-about-the-office-365-secruity--compliance-center"></a>En savoir plus sur le centre de conformité Office 365 Secruity &

Pour plus d’informations sur [les autorisations, consultez la rubrique Office 365 Security & Compliance Center](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

Si vous n’avez pas accès au centre de sécurité et de conformité Office 365, ou si vous avez besoin d’accéder à la version classique du gestionnaire de conformité dans le portail d’approbation de service Microsoft, les paramètres d’administration dans le portail d’approbation de service offrent une autre façon d’attribuer des rôles ([afficher les instructions](meet-data-protection-and-regulatory-reqs-using-microsoft-cloud.md#assigning-compliance-manager-roles-to-users)). N’oubliez pas que ces rôles sont plus limités dans leur fonctionnalité.

##### <a name="more-about-azure-ad"></a>En savoir plus sur Azure AD

Pour attribuer des rôles et définir des autorisations dans Azure AD, reportez-vous à [affecter des rôles administrateur et non administrateur aux utilisateurs d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

Les utilisateurs disposant d’identités Azure AD qui n’ont pas d’abonnements Office 365 ou Microsoft 365 ne pourront pas accéder au gestionnaire de conformité dans le centre de conformité Microsoft 365. Pour demander de l’aide pour accéder au gestionnaire de conformité, contactez [cmresearch@microsoft.com](mailto:cmresearch@microsoft.com).

### <a name="role-types"></a>Types de rôles

Le tableau ci-dessous présente les fonctions autorisées par chaque rôle dans le gestionnaire de conformité. Le tableau indique également comment chaque [rôle Azure ad](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles) est mappé aux rôles du gestionnaire de conformité. Pour accéder au gestionnaire de conformité, les utilisateurs doivent disposer au moins du rôle de lecteur du gestionnaire de conformité ou du rôle de lecteur Azure AD global.


| L’utilisateur peut : | Rôle du gestionnaire de conformité | Rôle Azure AD | 
| :------------- | :-------------: | :------------: |
| **Lire mais ne pas modifier les données**| Lecteur du Gestionnaire de conformité  | Lecteur Azure AD global, lecteur de sécurité | 
| **Modifier des données**| Contribution du gestionnaire de conformité | Administrateur de conformité | 
| **Modifier les résultats des tests**| Évaluation du gestionnaire de conformité | Administrateur de conformité | 
| **Gérer les évaluations, et les données de modèle et de client**| Administration du gestionnaire de conformité | Administrateur de conformité, administrateur de données de conformité, administrateur de sécurité  | 
| **Affecter des utilisateurs**| Administrateur général | Administrateur général | 

## <a name="settings-for-automated-testing-and-user-history"></a>Paramètres pour les tests automatisés et l’historique des utilisateurs

Les paramètres du gestionnaire de conformité dans le centre de conformité Microsoft 365 vous permettent d’activer et de désactiver le test automatique des actions d’amélioration. Les paramètres vous permettent également de gérer les données des utilisateurs associés aux actions d’amélioration, notamment la possibilité de réaffecter les actions d’amélioration à un autre utilisateur.  Seules les personnes disposant d’un rôle d’administrateur général ou de gestionnaire de conformité peuvent accéder aux paramètres du gestionnaire de conformité.

### <a name="set-up-automated-testing"></a>Configurer les tests automatisés

Certaines actions d’amélioration dans le gestionnaire de conformité sont également surveillées par le [score de sécurité Microsoft](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-secure-score). Vous pouvez configurer des tests automatisés d’actions qui sont surveillées conjointement, ce qui signifie que lorsqu’une action est testée et mise à jour dans le score sécurisé, ces résultats sont synchronisés avec les mêmes actions dans le gestionnaire de conformité et sont pris en compte dans le score de conformité.

Le test automatique est activé par défaut pour les organisations qui débutent avec le gestionnaire de conformité. Lorsque vous déployez pour la première fois Microsoft 365 ou Office 365, il faut environ sept jours pour que l’évaluation complète des données et les intégrer dans votre score de conformité.  Lorsque le test automatisé est activé, la date de test de l’action n’est pas mise à jour, mais son état de test est mis à jour. Lors de la création d’évaluations, les scores incluent automatiquement les scores de contrôle de Microsoft et l’intégration de la note de sécurité.

L’administrateur général de votre organisation peut modifier les paramètres de test automatisé à tout moment. Vous pouvez désactiver le test automatisé pour les actions d’amélioration courantes ou l’activer pour des actions individuelles. Suivez les instructions ci-dessous pour modifier vos paramètres de test automatisé.

#### <a name="to-manage-your-automated-testing-settings"></a>Pour gérer vos paramètres de test automatisés :

1. Sélectionnez **paramètres** dans le volet de navigation de gauche depuis n’importe quel endroit du [Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

2. Sur la page Paramètres, sélectionnez **Gestionnaire de conformité**.

3. Sélectionnez **test automatisé** dans le volet de navigation de gauche.

4. Sélectionnez le bouton applicable pour activer le test automatique pour toutes les actions d’amélioration, désactivez-le pour toutes les actions ou activez-le par une action individuelle.

5. Si vous sélectionnez **activer**pour une action d’amélioration, une liste affiche toutes les actions d’amélioration disponibles.  Activez la case à cocher en regard des actions que vous souhaitez tester automatiquement.

6. Sélectionnez **Enregistrer** pour enregistrer vos paramètres. Vous recevrez un message de confirmation en haut de l’écran indiquant que votre sélection a été enregistrée. Si vous recevez une notification d’échec, réessayez.

**Remarque :** Seul l’administrateur général peut activer ou désactiver les mises à jour automatiques pour toutes les actions. L’administrateur du gestionnaire de conformité peut activer les mises à jour automatiques pour des actions individuelles, mais pas pour toutes les actions de manière globale.

### <a name="manage-user-history"></a>Gérer l’historique des utilisateurs

Les paramètres **gérer l’historique des utilisateurs** vous aident à identifier rapidement les utilisateurs ayant travaillé avec des actions d’amélioration dans le gestionnaire de conformité. Les données utilisateur identifiables associées aux actions d’amélioration incluent toutes les opérations de mise en œuvre et de test effectuées, les documents qu’ils ont téléchargés et toutes les notes qu’ils ont entrées. La compréhension et la récupération de ce type de données peuvent être nécessaires pour les besoins de conformité propres à votre organisation.

Les paramètres de l’historique des utilisateurs vous permettent également de réaffecter toutes les actions d’amélioration d’un utilisateur à l’autre.

**Pour rechercher les paramètres d’historique de l’utilisateur :**

1. Sélectionnez Paramètres dans le volet de navigation de gauche depuis n’importe quel endroit du [Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

2. Sur la page Paramètres, sélectionnez **Gestionnaire de conformité**.

3. Sélectionnez **gérer l’historique** de l’utilisateur dans le volet de navigation de gauche.

La page **gérer l’historique des utilisateurs** affiche la liste de tous les utilisateurs par adresse de messagerie qui sont affectés à une action d’amélioration. Utilisez le bouton **Rechercher** pour trouver rapidement un utilisateur spécifique en tapant son adresse de messagerie.

À droite de l’adresse de messagerie de chaque utilisateur, le menu déroulant **Sélectionner** fournit des options pour exporter un rapport, réaffecter les actions d’amélioration ou supprimer l’historique. Pour plus d’informations sur chaque option, voir chaque section ci-dessous.

#### <a name="export-a-report-of-user-history-data"></a>Exporter un rapport des données d’historique de l’utilisateur

Vous pouvez exporter un fichier Excel contenant une liste d’actions d’amélioration actuellement attribuées à un utilisateur.  Le rapport répertorie également tous les fichiers de preuve téléchargés par cet utilisateur. Ces informations peuvent vous aider à réaffecter les actions d’amélioration ouvertes.

Le rapport reflète l’état de l’action d’amélioration à la date de sa création. Il ne s’agit pas d’un rapport historique de toutes les modifications précédentes apportées à son statut ou à son affectation (Découvrez comment [exporter un rapport à partir de votre page actions d’amélioration](compliance-manager-improvement-actions.md#export-a-report)).

**Suivez les étapes ci-dessous pour exporter un rapport par utilisateur :**

1. Sélectionnez **paramètres** dans le volet de navigation de gauche depuis n’importe quel endroit du [Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

2. Sur la page Paramètres, sélectionnez **Gestionnaire de conformité**.

3. Sélectionnez **gérer l’historique** de l’utilisateur à partir du volet de navigation à gauche.

4. Recherchez votre utilisateur ciblé en recherchant dans la liste des adresses de messagerie ou en sélectionnant **recherche** et en entrant l’adresse de messagerie de l’utilisateur.

5. Dans le menu déroulant **Sélectionner** , choisissez **Exporter le rapport**.

6. Une fois que le fichier Excel de votre rapport est généré, vous pouvez l’ouvrir et l’enregistrer sur votre ordinateur local.

#### <a name="reassign-improvement-actions-to-another-user"></a>Réaffecter les actions d’amélioration à un autre utilisateur

Vous pouvez réaffecter les actions d’amélioration d’un utilisateur à l’autre. Lorsque vous réaffectez une action, l’historique de téléchargement du document n’est pas modifié, mais le nom de l’utilisateur qui a chargé à l’origine la documentation n’apparaît plus dans l’action d’amélioration.

**Suivez les étapes ci-dessous pour réaffecter les actions d’amélioration à un autre utilisateur :**

1. Sélectionnez **paramètres** dans le volet de navigation de gauche depuis n’importe quel endroit du [Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

2. Sur la page Paramètres, sélectionnez **Gestionnaire de conformité**.

3. Sélectionnez **gérer l’historique** de l’utilisateur à partir du volet de navigation à gauche.

4. Recherchez un utilisateur en recherchant dans la liste des adresses de messagerie ou en sélectionnant **Rechercher** et en entrant l’adresse de messagerie de cet utilisateur.

5. Dans le menu déroulant **Sélectionner** , choisissez **réaffecter les actions d’amélioration**. Le volet de **réassignation des actions d’amélioration** s’affiche.

6. Dans le champ **Rechercher des utilisateurs** , entrez le nom ou l’adresse de messagerie de l’utilisateur auquel vous souhaitez affecter les actions *d'* amélioration.

7. Lorsque vous voyez le nom de votre utilisateur prévu dans **lequel les actions d’amélioration seront affectées**, sélectionnez l’utilisateur, puis sélectionnez **affecter des actions**.

8. Une fois la réaffectation terminée, un message de confirmation s’affiche dans le volet flyout, confirmant que toutes les actions d’amélioration de l’utilisateur précédent ont été réattribuées au nouvel utilisateur. Si vous recevez un avis d’échec de la réaffectation, fermez la fenêtre et réessayez. Pour fermer le volet flyout, sélectionnez **Terminer**.

Le nouvel utilisateur reçoit un e-mail auquel il a été affecté une action d’amélioration. Le message électronique contient un lien direct vers la page de détails de l’action d’amélioration.
 
 > [!NOTE]
> Si vous réaffectez une action dont la mise à jour est en attente, le lien direct vers l’action dans le message de réaffectation s’arrêtera si la mise à jour est acceptée après la réaffectation. Vous pouvez résoudre ce problème en réaffectant l’action à l’utilisateur une fois la mise à jour acceptée. En savoir plus sur les [mises à jour des actions d’amélioration](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

#### <a name="delete-user-history"></a>Supprimer l’historique de l’utilisateur

La suppression de l’historique d’un utilisateur les supprime en tant que propriétaire des actions d’amélioration et supprime son nom de tous les autres champs dans le gestionnaire de conformité. Lorsque vous supprimez l’historique d’un utilisateur, les actions d’amélioration dont il est propriétaire n’affichent pas une valeur **attribuée** tant qu’un nouvel utilisateur n’a pas été affecté. Tous les documents téléchargés dans l’action d’amélioration affichent l' **utilisateur supprimé** à la place du nom de l’utilisateur supprimé. La suppression de l’historique de l’utilisateur est définitive.

Pour supprimer l’historique d’un utilisateur, suivez les étapes ci-dessous :

1. Sélectionnez **paramètres** dans le volet de navigation de gauche depuis n’importe quel endroit du [Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

2. Sur la page Paramètres, sélectionnez **Gestionnaire de conformité**.

3. Sélectionnez **gérer l’historique** de l’utilisateur à partir du volet de navigation à gauche.

4. Recherchez un utilisateur en recherchant dans la liste des adresses de messagerie ou en sélectionnant **Rechercher** et en entrant l’adresse de messagerie de cet utilisateur.

5. Dans le menu déroulant **Sélectionner** , sélectionnez **Supprimer l’historique**.

6. Une fenêtre s’affiche pour vous demander de confirmer la suppression définitive de l’historique de l’utilisateur. Pour poursuivre la suppression, sélectionnez **Supprimer l’historique**. Pour quitter sans supprimer l’historique, sélectionnez **Annuler**.

7. Vous revenez à la page **gérer l’historique des utilisateurs** avec un message de confirmation dans la partie supérieure de l’historique de l’utilisateur qui a été supprimé.

## <a name="understand-the-compliance-manger-dashboard"></a>Comprendre le tableau de bord du gestionnaire de conformité

Le tableau de bord du gestionnaire de conformité est conçu pour vous offrir une vue instantanée de votre position actuelle en matière de conformité.

![Gestionnaire de conformité-tableau de bord](../media/compliance-manager-dashboard.png "Tableau de bord du gestionnaire de conformité")

### <a name="overall-compliance-score"></a>Score de conformité global

Votre score de conformité est bien visible en haut. Elle indique un pourcentage basé sur des points réalisables pour effectuer les actions d’amélioration qui répondent aux normes et réglementations clés en matière de protection des données. Les points à partir des [actions Microsoft](compliance-manager-assessments.md#microsoft-actions-tab), qui sont gérées par mon Microsoft, sont également pris en compte dans votre score de conformité.

Lorsque vous accédez au gestionnaire de conformité pour la première fois, votre score initial est basé sur la [base de données de protection des données Microsoft 365](compliance-manager-assessments.md#data-protection-baseline-default-assessment). Cette évaluation de la configuration de référence, qui est disponible pour toutes les organisations, est un ensemble de contrôles qui inclut des normes et des réglementations sectorielles communes. Le gestionnaire de conformité analyse vos solutions Microsoft 365 existantes et vous fournit une évaluation initiale basée sur vos paramètres de confidentialité et de sécurité actuels. À mesure que vous ajoutez des évaluations pertinentes pour votre organisation, votre score devient plus significatif pour vous.

**Pour plus d’informations, voir** [Comment le score de conformité est calculé](compliance-score-calculation.md).

### <a name="key-improvement-actions"></a>Actions d’amélioration clés

Cette section répertorie les principales actions d’amélioration que vous pouvez effectuer dès à présent pour tirer le plus grand impact positif sur votre score de conformité global. Sélectionnez **afficher toutes les actions d’amélioration** pour accéder à votre page actions d’amélioration.

### <a name="solutions-that-affect-your-score"></a>Solutions ayant une incidence sur votre score

Cette section présente les solutions qui contiennent des actions d’amélioration pouvant avoir un impact positif sur votre score, ainsi que le nombre d’actions d’amélioration en suspens dans ces solutions. Sélectionnez **afficher toutes les solutions** pour accéder à la page de vos solutions.

### <a name="compliance-score-breakdown"></a>Répartition du score de conformité

Cette section fournit une vue plus détaillée de votre score de deux manières différentes :

- **Catégories**: indique le pourcentage de votre score global dans les catégories de protection des données, telles que « protéger les informations » ou « gérer les appareils ».
- **Évaluations**: indique le pourcentage de votre progression dans la gestion des évaluations pour des normes, réglementations ou lois spécifiques en matière de protection des données, telles que RGPD ou NIST 800-53.

### <a name="filtering-your-dashboard-view"></a>Filtrage de l’affichage du tableau de bord

Vous pouvez filtrer votre vue de tableau de bord pour afficher uniquement les éléments liés à des réglementations, des normes, des solutions, un type d’action, des groupes d’évaluation ou des catégories de protection des données spécifiques. De cette manière, le filtrage de votre affichage filtre le score sur votre tableau de bord, indiquant le nombre de points que vous avez obtenus au total de points possibles en fonction de vos critères de filtre.

Pour appliquer des filtres :

1. Sélectionnez **filtre** dans le coin supérieur droit du tableau de bord.
2. Sélectionnez vos critères de filtre dans le volet flyout **filtres** , puis sélectionnez **appliquer**.

Une fois que vous avez appliqué un filtre, vous verrez votre score ajusté en temps réel. Le pourcentage du score de conformité et les informations de répartition, ainsi que les actions et les solutions d’amélioration, ne concernent désormais que les données couvertes par vos critères de filtre. Si vous vous déconnectez du gestionnaire de conformité, votre affichage filtré reste lorsque vous vous reconnectez.

Pour supprimer des filtres :

- Sur le titre **filtres appliqués** au-dessus de votre score de conformité, sélectionnez le **X** en regard du filtre individuel que vous souhaitez supprimer ; des
- Sélectionnez **filtre** dans le coin supérieur droit de votre tableau de bord, puis, dans le volet flyout **filtres** , sélectionnez **effacer les filtres**.

## <a name="improvement-actions-page"></a>Page actions d’amélioration

Les [actions d’amélioration](compliance-manager-improvement-actions.md) sont des actions gérées par votre organisation. L’utilisation des actions d’amélioration permet de centraliser vos activités de conformité et de s’aligner sur les normes et réglementations en matière de protection des données. Chaque action d’amélioration fournit des conseils détaillés sur la mise en œuvre et un lien permettant de vous lancer dans la solution appropriée. Des actions d’amélioration peuvent être affectées aux utilisateurs de votre organisation pour effectuer le travail d’implémentation et de test. Vous pouvez également stocker la documentation, les notes et les mises à jour de l’état des enregistrements au cours de l’action d’amélioration.

### <a name="view-your-improvement-actions"></a>Afficher vos actions d’amélioration

Le tableau de bord du gestionnaire de conformité affiche vos **actions d’amélioration clés.** Pour afficher toutes vos actions d’amélioration, sélectionnez l’onglet actions d’amélioration de votre tableau de bord, qui vous permet d’accéder à votre page actions d’amélioration. Vous pouvez également sélectionner Afficher toutes les actions d’amélioration sous la liste des actions d’amélioration de clé de votre tableau de bord pour accéder à votre page actions d’amélioration.

La page actions d’amélioration affiche toutes les actions d’amélioration qui sont gérées par votre organisation. Les actions gérées par Microsoft peuvent être affichées au sein de chaque évaluation (en savoir plus sur les [actions Microsoft](compliance-manager-assessments.md#microsoft-actions-tab)).

Si vous avez une longue liste d’actions sur votre page actions d’amélioration, il peut s’avérer utile de filtrer votre vue. Sélectionnez **filtre** dans le coin supérieur droit de la liste actions. Lorsque le volet flyout **filtres** apparaît, sélectionnez vos critères en fonction des réglementations, des normes, de la solution et du groupe. Vous pouvez également personnaliser votre affichage en sélectionnant **groupe** dans le coin supérieur droit. Dans le menu déroulant, sélectionnez pour afficher par groupe, solution, catégorie, type d’action ou état.

L’affichage par défaut de cette page n’affiche pas les actions d’amélioration dont l’état de test est **réussite**. Pour afficher les actions qui ont été testées, activez la case à cocher **passé** dans le volet flyout filtres. Uniquement les actions dont l’état de test est **passé** vers votre score. Certaines actions peuvent afficher une **étiquette de mise à jour en attente.** En savoir plus sur les [mises à jour des actions d’amélioration](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

La page actions d’amélioration affiche les points de données suivants pour chaque action d’amélioration :

- **Points atteints**: nombre de points obtenus en dehors du total disponible en effectuant l’action
- **Réglementations**: réglementations ou normes relatives à l’action
- **Groupe**: groupe auquel vous avez affecté l’action.
- **Solutions**: la solution à partir de laquelle vous pouvez effectuer l’action
- **Évaluations**: évaluations qui contiennent l’action
- **Catégories**: catégorie de protection des données associée (par exemple, protection des informations, gestion des appareils, etc.)
- **État du test**:
    - **Aucun** – pas de mise à jour d’État enregistrée
    - **Non évalué** -le test n’a pas commencé
    - **Réussite** de l’implémentation réussie
    - Échec du test à **faible risque** pour les tests, risque faible
    - **Risque moyen échoué** -test ayant échoué, risque moyen
    - Échec de test à **haut risque ayant** échoué, à risque élevé
    - **Hors de portée** – l’action n’est pas dans l’étendue de l’évaluation et n’influe pas sur votre score
    - **À détecter** : pour le test manuel, indique qu’une action a été implémentée, mais qu’elle n’a pas été testée ; pour le test automatisé, indique qu’une action attend un résultat d’automatisation
    - **Impossible de détecter** : l’État automatisé ne peut pas être déterminé.
    - **Partiellement testé** : score automatique qui récompense les points partiels

Pour **plus d’informations** [, consultez la rubrique How to Assign and perform work on improvation actions](compliance-manager-improvement-actions.md).

## <a name="solutions-page"></a>Page solutions

La page solutions indique le partage des points gagnés et potentiels, tel qu’il est organisé par la solution. L’affichage de vos points restants et des actions d’amélioration à partir de cette vue vous permet de comprendre les solutions qui nécessitent une attention plus immédiate.

Recherchez la page solutions en sélectionnant l’onglet **solutions** dans votre tableau de bord gestionnaire de conformité. Vous pouvez également sélectionner **afficher toutes les solutions** sous **solutions qui affectent votre score** dans la section supérieure droite de votre tableau de bord.

### <a name="filtering-your-solutions-view"></a>Filtrage de l’affichage des solutions

Pour filtrer votre vue de solutions :

1. Sélectionnez **filtre** dans le coin supérieur gauche de votre liste évaluations.
2. Dans le volet flyout **filtres** , activez la case à cocher en regard des critères de votre choix (normes et réglementations, solution, type d’action, groupe du gestionnaire de conformité, catégorie).
3. Sélectionnez le bouton **appliquer** . Le volet de filtre se ferme et vous verrez votre affichage filtré.

Vous pouvez également modifier votre vue pour afficher les évaluations par groupe, produit ou réglementation en sélectionnant le type de regroupement dans le menu déroulant **groupe** au-dessus de votre liste d’évaluations.

### <a name="taking-action-from-the-solution-page"></a>Prendre des mesures à partir de la page de solution

La page solutions affiche les solutions de votre organisation qui sont connectées à des actions d’amélioration. Le tableau indique la contribution de chaque solution à votre score global, les points obtenus et possibles au sein de cette solution, ainsi que le nombre d’actions d’amélioration restantes regroupées dans cette solution qui peuvent augmenter votre score.

Il existe deux façons d’effectuer une action à partir de cet écran :

1. Sur la ligne de la solution souhaitée, sous la colonne **actions restantes** , sélectionnez le numéro du lien hypertexte. Vous verrez une vue filtrée de l’écran actions d’amélioration montrant les actions d’amélioration non testées pour cette solution.

2. Sur la ligne de la solution voulue, sous la colonne **ouvrir une solution** , sélectionnez **ouvrir**. Vous verrez la solution ou l’emplacement dans les centres de sécurité et de conformité Microsoft 365 et Office 365, où vous pouvez prendre l’action recommandée.

## <a name="assessments-page"></a>Page évaluations

La page évaluations répertorie toutes les [évaluations](compliance-manager-assessments.md) que vous avez configurées pour votre organisation. Votre dénominateur de score de conformité est déterminé par toutes vos évaluations suivies. À mesure que vous ajoutez des évaluations supplémentaires, vous voyez plus d’actions d’amélioration indiquées sur votre page actions d’amélioration, et votre dénominateur de score de conformité augmente.

La page évaluations résume les informations clés de chaque évaluation :

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
3. Sélectionnez le bouton **appliquer** . Le volet de filtre se ferme et vous verrez votre affichage filtré.

Vous pouvez également modifier votre vue pour afficher les évaluations par groupe, produit ou réglementation en sélectionnant le type de regroupement dans le menu déroulant **groupe** au-dessus de votre liste d’évaluations.

### <a name="default-assessment"></a>Évaluation par défaut

Par défaut, vous verrez l’évaluation de la [base de données de protection des données](compliance-manager-assessments.md#data-protection-baseline-default-assessment) sur la page évaluations. Le gestionnaire de conformité fournit également plusieurs [modèles](compliance-manager-templates-list.md) prédéfinis pour la création d’évaluations.

## <a name="assessment-templates-page"></a>Page modèles d’évaluation

Un modèle est une infrastructure pour la création d’une évaluation dans le gestionnaire de conformité. La page modèles d’évaluation affiche la liste des modèles et des détails clés. La liste inclut des modèles fournis par le gestionnaire de conformité, ainsi que tous les modèles que votre organisation a modifiés ou créés. Vous pouvez appliquer des filtres pour rechercher un modèle en fonction de la certification, de l’étendue du produit, du pays, de l’industrie et de son auteur.

Sélectionnez un modèle à partir de sa ligne pour afficher sa page détails, qui contient une description du modèle et des informations supplémentaires sur la certification, l’étendue et les contrôles. À partir de cette page, vous pouvez sélectionner les boutons appropriés pour créer une évaluation, exporter les données du modèle vers Excel ou modifier le modèle.

**En savoir plus :** Découvrez [comment utiliser les modèles d’évaluation](compliance-manager-templates.md).

## <a name="next-step"></a>Étape suivante
Personnalisez le gestionnaire de conformité en [configurant des évaluations](compliance-manager-assessments.md).