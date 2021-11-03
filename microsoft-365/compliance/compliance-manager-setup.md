---
title: Mise en place du Gestionnaire de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Définissez les rôles et les autorisations utilisateur du Gestionnaire de conformité Microsoft et configurez des tests automatisés des actions. Gérer l’historique des utilisateurs et filtrer l’affichage de votre tableau de bord.
ms.openlocfilehash: ec44ec38a76cf0371804df25b698d77ba7b5aa22
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60668399"
---
# <a name="get-started-with-compliance-manager"></a>Prise en main du Gestionnaire de conformité

**Dans cet article :** Cet article vous aide à configurer le Gestionnaire de conformité. Découvrez comment accéder **au Gestionnaire de** conformité, définir des rôles et des **autorisations** et configurer le **test automatique des actions d’amélioration.** Parcourir votre tableau **de bord du Gestionnaire** de conformité et comprendre les pages principales : la page d’actions d’amélioration, la page des solutions, la page d’évaluations et la page des modèles d’évaluation.

## <a name="who-can-access-compliance-manager"></a>Qui pouvez accéder au Gestionnaire de conformité

Le Gestionnaire de conformité est disponible pour les organisations titulaires de licences Office 365 et Microsoft 365, et pour les clients modérés, Cloud de la communauté du secteur public élevés et du département de la Défense (DoD) des États-Unis Cloud de la communauté du secteur public (Cloud de la communauté du secteur public). La disponibilité de l’évaluation et les fonctionnalités de gestion dépendent de votre contrat de licence.  [Afficher les détails de description du service.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

## <a name="before-you-begin"></a>Avant de commencer

L Microsoft 365 général de votre organisation sera probablement le premier utilisateur à accéder au Gestionnaire de conformité. Nous recommandons à l’administrateur général de se connecter et de définir les autorisations utilisateur comme indiqué ci-dessous lors de la première visite du Gestionnaire de conformité.

## <a name="sign-in"></a>Connexion

1. Go to the [Centre de conformité Microsoft 365](https://compliance.microsoft.com/) and **sign in** with your Microsoft 365 global administrator account.
2. Sélectionnez **gestionnaire de conformité** dans le volet de navigation de gauche. Vous arrivez à votre tableau de [bord du Gestionnaire de conformité.](#understand-the-compliance-manager-dashboard)

Le lien direct vers le Gestionnaire de conformité est [https://compliance.microsoft.com/compliancemanager](https://compliance.microsoft.com/compliancemanager) .

## <a name="set-user-permissions-and-assign-roles"></a>Définir des autorisations utilisateur et attribuer des rôles

Le Gestionnaire de conformité utilise un modèle d’autorisation de contrôle d’accès basé sur un rôle (RBAC). Seuls les utilisateurs affectés à un rôle peuvent accéder au Gestionnaire de conformité et les actions autorisées par chaque utilisateur sont limitées par [type de rôle.](#role-types)

### <a name="where-to-set-permissions"></a>Où définir des autorisations

La personne détenant le rôle d’administrateur général de votre organisation peut définir des autorisations utilisateur pour le Gestionnaire de conformité. Les autorisations peuvent être définies dans le Centre de conformité Microsoft 365 ainsi que dans Azure Active Directory (Azure AD).

> [!NOTE]
> Les clients des environnements Community (Cloud de la communauté du secteur public) pour le gouvernement américain et le Département de la Défense (DoD) peuvent uniquement définir des autorisations utilisateur et des rôles pour le Gestionnaire de conformité dans Azure AD. Voir ci-dessous pour obtenir Azure AD instructions et les définitions de type de rôle.

Pour définir des autorisations et attribuer des rôles dans le Centre de conformité Microsoft 365, suivez les étapes ci-dessous :

1. Go to the [Centre de conformité Microsoft 365](https://compliance.microsoft.com/compliancemanager) and select **Permissions** on the left navigation.

2. Sous la **dropdown du Centre de** conformité, sélectionnez **Rôles.**

3. Recherchez le groupe de rôles auquel vous souhaitez ajouter un ou plusieurs utilisateurs, puis cochez la case à gauche du nom du groupe. (Consultez la [liste des rôles et des fonctions associées ci-dessous.](#role-types) Les noms des groupes de rôles imitent le nom du rôle.)

4. Dans le volet volant de ce groupe, sélectionnez **Modifier** sous **l’en-tête Membres.**

5. Sélectionnez **Choisir les membres.** Une autre fenêtre volante s’affiche.

6. Sélectionnez **+ Ajouter** pour choisir un ou plusieurs utilisateurs à ajouter au groupe.

7. Cochez la case en regard des noms que vous souhaitez ajouter, puis sélectionnez le bouton **Ajouter** en bas.

8. Lorsque vous avez terminé d’affecter des utilisateurs, sélectionnez **Terminé,** puis **Sélectionnez Enregistrer,** puis **Fermer**.

#### <a name="more-about-azure-ad"></a>En savoir plus sur Azure AD

Pour attribuer des rôles et définir des autorisations dans Azure AD, voir Attribuer des rôles d’administrateur et [non administrateur](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal)aux utilisateurs Azure Active Directory .

Les utilisateurs Azure AD identités qui n’ont pas d’abonnement Office 365 ou Microsoft 365 ne pourront pas accéder au Gestionnaire de conformité dans le Centre de conformité Microsoft 365. Pour obtenir de l’aide pour accéder au Gestionnaire de conformité, contactez [cmresearch@microsoft.com](mailto:cmresearch@microsoft.com).

### <a name="role-types"></a>Types de rôles

Le tableau ci-dessous présente les fonctions autorisées par chaque rôle dans le Gestionnaire de conformité. Le tableau montre également comment chaque rôle [Azure AD est](/azure/active-directory/roles/permissions-reference) mapré avec les rôles du Gestionnaire de conformité. Les utilisateurs auront besoin au moins du rôle de lecteur gestionnaire de conformité, ou Azure AD rôle de lecteur global, pour accéder au Gestionnaire de conformité.


| L’utilisateur peut : | Rôle du Gestionnaire de conformité | Azure AD rôle | 
| :------------- | :-------------: | :------------: |
| **Lire les données mais ne peut pas les modifier**| Gestionnaire de conformité - Lecteur  | Azure AD Lecteur global, lecteur Sécurité | 
| **Modifier les données**| Contribution du Gestionnaire de conformité | Administrateur de conformité | 
| **Modifier les résultats des tests**| Gestionnaire de conformité - Analyste | Administrateur de conformité | 
| **Gérer les évaluations, ainsi que les données de modèle et de client**| Administration du Gestionnaire de conformité | Administrateur de conformité, administrateur de données de conformité, administrateur de sécurité  | 
| **Affecter des utilisateurs**| Administrateur général | Administrateur général | 

## <a name="settings-for-automated-testing-and-user-history"></a>Paramètres pour les tests automatisés et l’historique des utilisateurs

Les paramètres du Gestionnaire de conformité du Centre de conformité Microsoft 365 vous permettent d’activer et de désactiver le test automatique des actions d’amélioration. Les paramètres vous permettent également de gérer les données des utilisateurs associés aux actions d’amélioration, y compris la possibilité de réaffecter des actions d’amélioration à un autre utilisateur.  Seules les personnes ayant un rôle d’administrateur général ou d’administrateur du Gestionnaire de conformité peuvent accéder aux paramètres du Gestionnaire de conformité.

> [!NOTE]
> La fonctionnalité de test automatisé n’est pas disponible pour les clients Cloud de la communauté du secteur public environnements Élevé et DoD, car le niveau de sécurité n’est pas disponible dans ces environnements. Cloud de la communauté du secteur public Les clients Haut et DoD doivent implémenter et tester manuellement leurs actions d’amélioration.

### <a name="set-up-automated-testing"></a>Configurer des tests automatisés

Certaines actions d’amélioration dans le Gestionnaire de conformité sont également surveillées par [le Score de sécurité Microsoft.](../security/defender/microsoft-secure-score.md) Vous pouvez configurer des tests automatisés des actions qui sont surveillées conjointement, ce qui signifie que lorsqu’une action est testée et mise à jour dans le Score de sécurité, ces résultats sont synchronisés avec les mêmes actions dans le Gestionnaire de conformité et comptent dans votre score de conformité.

Les tests automatiques sont désactivés par défaut pour les organisations qui ont été nouvelles dans le Gestionnaire de conformité. Lorsque vous déployez Microsoft 365 ou Office 365, le score de sécurité met environ sept jours à collecter entièrement les données et à les factorisation dans votre score de conformité.  Lorsque le test automatisé est allumé, la date de test de l’action n’est pas mise à jour, mais son état de test est mis à jour. Lorsque de nouvelles évaluations sont créées, les scores incluent automatiquement les scores de contrôle Microsoft et l’intégration du score de sécurité.

L’administrateur général de votre organisation peut modifier les paramètres des tests automatisés à tout moment. Vous pouvez désactiver le test automatisé pour les actions d’amélioration courantes ou l’activer pour des actions individuelles. Suivez les instructions ci-dessous pour modifier vos paramètres de test automatisés.

#### <a name="to-manage-your-automated-testing-settings"></a>Pour gérer vos paramètres de test automatisés :

1. Sélectionnez **Paramètres** sur le navigation de gauche à partir de n’importe où dans [le Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

2. Dans la page paramètres, sélectionnez **Gestionnaire de conformité.**

3. Sélectionnez **Tests automatisés** dans le navigation de gauche.

4. Sélectionnez le bouton applicable pour activer le test automatique pour toutes les actions d’amélioration, le désactiver pour toutes les actions ou l’activer par action individuelle.

5. Si vous **sélectionnez Activer par action** d’amélioration, une liste affiche toutes les actions d’amélioration disponibles à choisir.  Cochez la case en regard de toute action que vous souhaitez tester automatiquement.

6. Sélectionnez **Enregistrer** pour enregistrer vos paramètres. Vous recevrez un message de confirmation en haut de l’écran pour confirmer que votre sélection a été enregistrée. Si vous recevez un avis d’échec, recommencez.

**Remarque :** Seul l’administrateur général peut activer ou désactiver les mises à jour automatiques pour toutes les actions. L’administrateur du Gestionnaire de conformité peut activer les mises à jour automatiques pour des actions individuelles, mais pas pour toutes les actions globalement.

### <a name="manage-user-history"></a>Gérer l’historique des utilisateurs

Les **paramètres Gérer l’historique** des utilisateurs vous aident à identifier rapidement les utilisateurs qui ont travaillé avec des actions d’amélioration dans le Gestionnaire de conformité. Les données utilisateur identifiables associées aux actions d’amélioration incluent tout travail d’implémentation et de test effectué, les documents qu’ils ont téléchargés et les notes qu’ils ont entrées. La compréhension et la récupération de ce type de données peuvent être nécessaires pour les besoins de conformité de votre organisation.

Les paramètres de l’historique utilisateur vous permettent également de réaffecter toutes les actions d’amélioration d’un utilisateur à un autre.

**Pour rechercher les paramètres de l’historique utilisateur :**

1. Sélectionnez Paramètres sur le navigation de gauche à partir de n’importe où dans [le Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

2. Dans la page paramètres, sélectionnez **Gestionnaire de conformité.**

3. Sélectionnez **Gérer l’historique des utilisateurs** à partir du navigation de gauche.

La page **Gérer l’historique des** utilisateurs affiche la liste de tous les utilisateurs par adresse de messagerie qui sont affectés à une action d’amélioration. Utilisez le **bouton Rechercher** pour rechercher rapidement un utilisateur spécifique en tapant son adresse de messagerie.

À droite de l’adresse e-mail de chaque utilisateur, le menu déroulant Sélectionner fournit des options pour exporter un rapport, réaffecter des actions d’amélioration ou supprimer l’historique.  Pour plus d’informations sur chaque option, voir chaque section ci-dessous.

#### <a name="export-a-report-of-user-history-data"></a>Exporter un rapport de données d’historique utilisateur

Vous pouvez exporter un fichier Excel contenant une liste d’actions d’amélioration actuellement affectées à un utilisateur.  Le rapport répertorie également les fichiers de preuves téléchargés par cet utilisateur. Ces informations peuvent vous aider à réaffecter les actions d’amélioration de l’ouverture.

Le rapport reflète l’état de l’action d’amélioration à sa date de création. Il ne s’agit pas d’un rapport historique de toutes les modifications précédentes apportées à son état ou à son affectation (découvrez comment exporter un rapport à partir de votre [page d’actions d’amélioration).](compliance-manager-improvement-actions.md#export-a-report)

**Suivez les étapes ci-dessous pour exporter un rapport par utilisateur :**

1. Sélectionnez **Paramètres** sur le navigation de gauche à partir de n’importe où dans [le Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

2. Dans la page paramètres, sélectionnez **Gestionnaire de conformité.**

3. Sélectionnez **Gérer l’historique des** utilisateurs à partir de la navigation à gauche.

4. Recherchez l’utilisateur prévu en recherchant les adresses de messagerie de la liste ou en sélectionnant **Rechercher** et en entrant l’adresse e-mail de l’utilisateur.

5. Dans **le** menu déroulant Sélectionner, choisissez **Exporter le rapport.**

6. Une fois Excel fichier de votre rapport est généré, vous pouvez l’ouvrir et l’enregistrer sur votre ordinateur local.

#### <a name="reassign-improvement-actions-to-another-user"></a>Réaffecter des actions d’amélioration à un autre utilisateur

Vous pouvez réaffecter des actions d’amélioration d’un utilisateur à un autre. Lorsque vous réaffectez une action, l’historique de téléchargement de documents ne change pas, mais le nom de l’utilisateur qui a téléchargé la documentation à l’origine n’apparaît plus dans l’action d’amélioration.

**Suivez les étapes ci-dessous pour réaffecter des actions d’amélioration à un autre utilisateur :**

1. Sélectionnez **Paramètres** sur le navigation de gauche à partir de n’importe où dans [le Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

2. Dans la page paramètres, sélectionnez **Gestionnaire de conformité.**

3. Sélectionnez **Gérer l’historique des** utilisateurs à partir de la navigation à gauche.

4. Recherchez un utilisateur en recherchant les adresses de messagerie de la liste ou en sélectionnant **Rechercher** et en entrant l’adresse e-mail de cet utilisateur.

5. Dans le menu **déroulant Sélectionner,** sélectionnez **Réaffecter les actions d’amélioration.** Le **volet volant Réaffectation des actions** d’amélioration s’affiche.

6. Dans le **champ Utilisateurs de** la recherche, entrez le nom ou l’adresse e-mail de l’utilisateur à qui vous souhaitez attribuer les actions *d’amélioration.*

7. Lorsque vous voyez le nom de l’utilisateur prévu sous **Les actions** d’amélioration seront affectés à , sélectionnez l’utilisateur, puis **sélectionnez Affecter des actions**.

8. Une fois la réaffectation terminée, vous verrez un message de confirmation dans le volet volant confirmant que toutes les actions d’amélioration de l’utilisateur précédent ont été réaffectés au nouvel utilisateur. Si vous recevez un avis d’échec de réaffectation, fermez la fenêtre et réessayez. Pour fermer le volet volant, sélectionnez **Terminé.**

La nouvelle personne affectée reçoit un e-mail qui lui a été affecté à une action d’amélioration. Le courrier électronique contient un lien direct vers la page de détails de l’action d’amélioration.

 > [!NOTE]
> Si vous réaffectez une action qui a une mise à jour en attente, le lien direct vers l’action dans l’e-mail de réaffectation s' pause si la mise à jour est acceptée après la réaffectation. Vous pouvez résoudre ce problème en ré assignant l’action à l’utilisateur une fois la mise à jour acceptée. En savoir plus sur les [mises à jour des actions d’amélioration.](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions)

#### <a name="delete-user-history"></a>Supprimer l’historique des utilisateurs

La suppression de l’historique d’un utilisateur les supprime en tant que propriétaire des actions d’amélioration et supprime son nom de tous les autres champs du Gestionnaire de conformité. Lorsque vous supprimez l’historique d’un utilisateur, les  actions d’amélioration dont il était propriétaire n’affichent pas de valeur Affectée à tant qu’un nouvel utilisateur n’est pas affecté. Tous les documents téléchargés vers  l’action d’amélioration indiquent l’utilisateur supprimé à la place du nom de l’utilisateur supprimé. La suppression de l’historique des utilisateurs est permanente.

Pour supprimer l’historique d’un utilisateur, suivez les étapes ci-dessous :

1. Sélectionnez **Paramètres** sur le navigation de gauche à partir de n’importe où dans [le Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

2. Dans la page paramètres, sélectionnez **Gestionnaire de conformité.**

3. Sélectionnez **Gérer l’historique des** utilisateurs à partir de la navigation à gauche.

4. Recherchez un utilisateur en recherchant les adresses de messagerie de la liste ou en sélectionnant **Rechercher** et en entrant l’adresse e-mail de cet utilisateur.

5. Dans le menu **déroulant Sélectionner,** choisissez **Supprimer l’historique.**

6. Une fenêtre s’affiche vous demandant de confirmer la suppression définitive de l’historique de l’utilisateur. Pour continuer la suppression, sélectionnez **Supprimer l’historique.** Pour quitter sans supprimer l’historique, sélectionnez **Annuler**.

7. Vous revenirz à la **page** Gérer l’historique des utilisateurs avec un message de confirmation en haut de la page que l’historique de l’utilisateur a été supprimé.

## <a name="understand-the-compliance-manager-dashboard"></a>Comprendre le tableau de bord du Gestionnaire de conformité

Le tableau de bord du Gestionnaire de conformité est conçu pour vous fournir une vue d’un coup d’œil de votre posture de conformité actuelle.

:::image type="content" alt-text="Gestionnaire de conformité : tableau de bord." source="../media/compliance-manager-dashboard.png" lightbox="../media/compliance-manager-dashboard.png":::

### <a name="overall-compliance-score"></a>Score de conformité global

Votre score de conformité est mis en évidence en haut. Il présente un pourcentage basé sur des points réalisables pour effectuer des actions d’amélioration qui s’adressent aux principales normes et réglementations en matière de protection des données. Les points des [actions Microsoft,](compliance-manager-assessments.md#microsoft-actions-tab)qui sont gérés par Microsoft, comptent également dans votre score de conformité.

Lorsque vous arrivez au Gestionnaire de conformité pour la première fois, votre score initial est basé sur la ligne de base Microsoft 365 [protection des données.](compliance-manager-assessments.md#data-protection-baseline-default-assessment) Cette évaluation de référence, disponible pour toutes les organisations, est un ensemble de contrôles qui inclut des normes et réglementations courantes du secteur. Le Gestionnaire de conformité analyse vos solutions Microsoft 365 existantes et vous fournit une évaluation initiale basée sur vos paramètres de confidentialité et de sécurité actuels. Lorsque vous ajoutez des évaluations pertinentes pour votre organisation, votre score devient plus significatif pour vous.

**En savoir plus : comprendre** comment votre score de conformité est [calculé.](compliance-score-calculation.md)

### <a name="key-improvement-actions"></a>Principales actions d’amélioration

Cette section répertorie les principales actions d’amélioration que vous pouvez effectuer dès maintenant pour avoir le plus grand impact positif sur votre score de conformité global. Sélectionnez **Afficher toutes les actions d’amélioration** pour aller à votre page d’actions d’amélioration.

### <a name="solutions-that-affect-your-score"></a>Solutions qui affectent votre score

Cette section présente les solutions contenant des actions d’amélioration qui peuvent avoir un impact positif sur votre score, ainsi que le nombre d’actions d’amélioration en suspens dans ces solutions. Sélectionnez **Afficher toutes les solutions** pour consulter la page de vos solutions.

### <a name="compliance-score-breakdown"></a>Répartition du score de conformité

Cette section vous donne une vue plus détaillée de votre score de deux manières différentes :

- **Catégories :** affiche le pourcentage de votre score global au sein des catégories de protection des données, telles que « protéger les informations » ou « gérer les appareils ».
- **Évaluations**: indique le pourcentage de vos progrès dans la gestion des évaluations pour des normes, réglementations ou lois particulières en matière de conformité et de protection des données, telles que le R GDPR ou le NIST 800-53.

### <a name="filtering-your-dashboard-view"></a>Filtrage de l’affichage de votre tableau de bord

Vous pouvez filtrer l’affichage de votre tableau de bord pour afficher uniquement les éléments liés à des réglementations et des normes particulières, des solutions, un type d’action, des groupes d’évaluation ou des catégories de protection des données. Le filtrage de votre affichage de cette façon permet également de filtrer le score de votre tableau de bord, en indiquant le nombre de points que vous avez obtenus sur le nombre total de points possibles en fonction de vos critères de filtre.

Pour appliquer des filtres :

1. Sélectionnez **Filtre** en haut à droite du tableau de bord.
2. Sélectionnez vos critères de filtre dans le volet volant **Filtres,** puis sélectionnez **Appliquer.**

Une fois que vous avez appliqué un filtre, votre score est ajusté en temps réel. Le pourcentage du score de conformité et les informations de répartition, ainsi que les actions et solutions d’amélioration, concernent désormais uniquement les données couvertes par vos critères de filtre. Si vous vous connectez au Gestionnaire de conformité, votre affichage filtré reste lorsque vous vous connectez à nouveau.

Pour supprimer des filtres :

- Dans **l’en-tête Filtres** appliqués au-dessus de votre score de conformité, sélectionnez **le X** en dessous du filtre individuel que vous souhaitez supprimer . ou
- Sélectionnez **Filtre** en haut à droite de  votre tableau de bord, puis, dans le volet volant Filtres, sélectionnez **Effacer les filtres.**

## <a name="improvement-actions-page"></a>Page Actions d’amélioration

[Les actions d’amélioration](compliance-manager-improvement-actions.md) sont des actions gérées par votre organisation. L’application d’actions d’amélioration permet de centraliser vos activités de conformité et de s’aligner sur les normes et réglementations en matière de protection des données. Chaque action d’amélioration fournit des instructions d’implémentation détaillées et un lien pour vous lancer dans la solution appropriée. Des actions d’amélioration peuvent être affectées aux utilisateurs de votre organisation pour effectuer des tâches d’implémentation et de test. Vous pouvez également stocker de la documentation, des notes et enregistrer des mises à jour d’état dans l’action d’amélioration.

### <a name="view-your-improvement-actions"></a>Afficher vos actions d’amélioration

Le tableau de bord du Gestionnaire de conformité présente vos **principales actions d’amélioration.** Pour afficher toutes vos actions d’amélioration, sélectionnez l’onglet Actions d’amélioration de votre tableau de bord, qui vous permet d’afficher votre page d’actions d’amélioration. Vous pouvez également sélectionner Afficher toutes les actions d’amélioration sous la liste des actions d’amélioration clés de votre tableau de bord pour obtenir votre page d’actions d’amélioration.

La page Actions d’amélioration affiche toutes les actions d’amélioration qui sont gérées par votre organisation. Les actions gérées par Microsoft peuvent être vues dans chaque évaluation (en savoir plus sur les [actions De Microsoft).](compliance-manager-assessments.md#microsoft-actions-tab)

Si vous avez une longue liste d’actions sur votre page d’actions d’amélioration, il peut être utile de filtrer votre affichage. Sélectionnez **Filtre** dans le coin supérieur droit de la liste d’actions. Lorsque le **volet volant Filtres** s’affiche, sélectionnez vos critères en fonction des réglementations et normes, de la solution et du groupe. Vous pouvez également personnaliser votre affichage en sélectionnant **Groupe** dans le coin supérieur droit. Dans le menu déroulant, sélectionnez l’affichage par groupe, solution, catégorie, type d’action ou état.

L’affichage par défaut de cette page n’affiche pas les actions d’amélioration avec l’état de test **Réussi**. Pour afficher les actions qui ont réussi les tests, cochez la case **Réussi** dans le volet volant Filtres. Seules les actions dont l’état de test est **Réussi** comptent pour votre score. Certaines actions peuvent afficher une étiquette de mise à jour **en attente.** En savoir plus sur les [mises à jour des actions d’amélioration.](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions)

La page Actions d’amélioration affiche les points de données suivants pour chaque action d’amélioration :

- **Points obtenus**: nombre de points obtenus sur le total disponible en effectuant l’action
- **Réglementations**: réglementations ou normes relatives à l’action
- **Groupe**: groupe auquel vous avez affecté l’action
- **Solutions**: solution dans laquelle vous pouvez effectuer l’action
- **Évaluations**: évaluations qui contiennent l’action
- **Catégories :** la catégorie de protection des données associée (par exemple, protéger les informations, gérer les appareils, etc.)
- **État du test**:
    - **Aucun :** aucune mise à jour d’état enregistrée
    - **Non évalué -** le test n’a pas démarré
    - **Réussite :** implémentation testée avec succès
    - **Échec du risque faible :** échec du test, faible risque
    - **Échec du risque moyen :** échec du test, risque moyen
    - **Échec d’un risque élevé** : échec du test, risque élevé
    - **Hors de portée :** l’action n’est pas dans l’étendue de l’évaluation et n’a pas d’impact sur votre score
    - **À détecter : pour** un test manuel, indique qu’une action a été implémentée, mais qu’elle n’a pas été testée ; pour un test automatisé, indique qu’une action attend un résultat d’automatisation
    - **Non détecté : l’état** automatisé ne peut pas être déterminé
    - **Partiellement testé : score** automatisé qui accorde des points partiels

**En savoir plus : découvrez** comment affecter et effectuer des tâches sur les actions [d’amélioration.](compliance-manager-improvement-actions.md)

## <a name="solutions-page"></a>Page Solutions

La page des solutions affiche le partage des points gagnés et potentiels, tel qu’organisé par solution. L’affichage des points restants et des actions d’amélioration à partir de cet affichage vous permet de comprendre les solutions qui doivent être plus immédiatement prises en compte.

Recherchez la page solutions en sélectionnant **l’onglet Solutions** dans votre tableau de bord du Gestionnaire de conformité. Vous pouvez également sélectionner **Afficher toutes les solutions** sous Solutions qui affectent votre **score** dans la section supérieure droite de votre tableau de bord.

### <a name="filtering-your-solutions-view"></a>Filtrage de l’affichage de vos solutions

Pour filtrer votre vue des solutions :

1. Sélectionnez **Filtre** dans le coin supérieur gauche de votre liste d’évaluations.
2. Dans le volet volant **Filtres,** placez une vérification en regard des critères souhaités (normes et réglementations, solution, type d’action, groupe Gestionnaire de conformité, catégorie).
3. Sélectionnez le **bouton** Appliquer. Le volet filtre se ferme et votre affichage filtré s’affiche.

Vous pouvez également modifier votre affichage pour afficher les évaluations par groupe, produit  ou réglementation en sélectionnant le type de regroupement dans le menu déroulant Groupe au-dessus de votre liste d’évaluations.

### <a name="taking-action-from-the-solution-page"></a>Action à partir de la page solution

La page solutions affiche les solutions de votre organisation qui sont connectées à des actions d’amélioration. Le tableau répertorie la contribution de chaque solution à votre score global, les points obtenus et possibles au sein de cette solution, ainsi que le nombre restant d’actions d’amélioration regroupées dans cette solution qui peuvent augmenter votre score.

Il existe deux façons d’agir à partir de cet écran :

1. Sur la ligne de votre solution prévue, sous la colonne **Actions** restantes, sélectionnez le numéro de lien hypertexte. Vous verrez une vue filtrée de l’écran actions d’amélioration affichant les actions d’amélioration non testées pour cette solution.

2. Sur la ligne de votre solution prévue, sous la colonne **Ouvrir la solution,** sélectionnez **Ouvrir**. Vous verrez la solution ou l’emplacement dans les centres de sécurité et de conformité Microsoft 365 et Office 365 où vous pouvez prendre l’action recommandée.

## <a name="assessments-page"></a>Page Évaluations

La page évaluations répertorie toutes les [évaluations](compliance-manager-assessments.md) que vous avez définies pour votre organisation. Votre dénominateur de score de conformité est déterminé par toutes vos évaluations. À mesure que vous ajoutez d’autres évaluations, vous verrez d’autres actions d’amélioration répertoriées sur votre page d’actions d’amélioration et le dénominateur de votre score de conformité augmente.

Le compteur de **modèles activés** en haut de la page indique le nombre de modèles d’évaluation actifs actuellement utilisés par rapport au nombre total de modèles disponibles pour votre organisation. Pour plus [d’informations, voir](compliance-manager-templates.md#template-availability-and-licensing) Disponibilité des modèles et licences.

La page Évaluations récapitule les informations clés sur chaque évaluation :

- **Évaluation :** nom de l’évaluation
- **État**:
  - **Complète** : tous les contrôles ont l’état « transmis » ou au moins un est passé et les autres sont « hors de portée »
  - **Incomplet** : au moins un contrôle a l’état « échec »
  - **Aucun** : tous les contrôles n’ont pas été testés
  - **En cours** : les actions d’amélioration ont tout autre état, y compris « en cours », « crédit partiel » ou « non détecté »
- **Progression de l’évaluation**: pourcentage du travail effectué vers l’achèvement, tel que mesuré par le nombre de contrôles testés
- **Vos actions d’amélioration**: nombre d’actions terminées pour satisfaire l’implémentation de vos contrôles
- **Actions Microsoft**: nombre d’actions terminées pour satisfaire l’implémentation des contrôles Microsoft
- **Groupe**: nom du groupe à qui appartient l’évaluation
- **Produit**: produit associé, tel que Microsoft 365 ou un autre produit défini pour l’évaluation
- **Réglementation**: norme, stratégie ou loi réglementaire qui s’applique à l’évaluation

### <a name="filtering-your-assessments-view"></a>Filtrage de l’affichage de vos évaluations

Pour filtrer votre vue des évaluations :

1. Sélectionnez **Filtre** dans le coin supérieur gauche de votre liste d’évaluations.
2. Dans le volet volant **Filtres,** vérifiez les critères souhaités.
3. Sélectionnez le **bouton** Appliquer. Le volet de filtre se ferme et votre affichage filtré s’affiche.

Vous pouvez également modifier votre affichage pour afficher les évaluations par groupe, produit  ou réglementation en sélectionnant le type de regroupement dans le menu déroulant Groupe au-dessus de votre liste d’évaluations.

### <a name="default-assessment"></a>Évaluation par défaut

Par défaut, vous verrez l’évaluation de base de [la protection](compliance-manager-assessments.md#data-protection-baseline-default-assessment) des données sur la page des évaluations. Le Gestionnaire de conformité fournit également plusieurs [modèles](compliance-manager-templates-list.md) pré-créés pour la création d’évaluations.

## <a name="assessment-templates-page"></a>Page des modèles d’évaluation

Un modèle est un cadre permettant de créer une évaluation dans le Gestionnaire de conformité. La page des modèles d’évaluation affiche une liste de modèles et des informations clés. La liste inclut les modèles fournis par le Gestionnaire de conformité, ainsi que tous les modèles que votre organisation a modifiés ou créés. Vous pouvez appliquer des filtres pour rechercher un modèle basé sur la certification, l’étendue du produit, le pays, l’industrie et qui l’a créé.

Le compteur de **modèles activés** en haut de la page indique le nombre de modèles d’évaluation actifs actuellement utilisés par rapport au nombre total de modèles disponibles pour votre organisation. Pour plus [d’informations, voir](compliance-manager-templates.md#template-availability-and-licensing) Disponibilité des modèles et licences.

Sélectionnez un modèle dans sa ligne pour faire monter sa page de détails, qui contient une description du modèle et des informations supplémentaires sur la certification, l’étendue et les détails des contrôles. À partir de cette page, vous pouvez sélectionner les boutons appropriés pour créer une évaluation, exporter les données du modèle vers Excel ou modifier le modèle.

**En savoir plus :** [Découvrez comment utiliser des modèles d’évaluation.](compliance-manager-templates.md)

## <a name="next-step"></a>Étape suivante

Personnalisez le Gestionnaire de conformité [en mettant en place des évaluations.](compliance-manager-assessments.md)
