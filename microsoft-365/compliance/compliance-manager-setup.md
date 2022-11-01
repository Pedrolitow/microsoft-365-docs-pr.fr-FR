---
title: Prise en main du Gestionnaire de conformité Microsoft Purview
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- purview-compliance
- m365solution-compliancemanager
- m365initiative-compliance
- highpri
- tier1
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Définissez les autorisations et les rôles utilisateur du Gestionnaire de conformité Microsoft Purview et configurez le test automatisé des actions. Gérez l’historique utilisateur et filtrez l’affichage de votre tableau de bord.
ms.openlocfilehash: 22c23c64148f9a95b26b90e1b9097218413158ec
ms.sourcegitcommit: b439d097e55bba35d9328447d993bbcac7a178a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68802260"
---
# <a name="get-started-with-compliance-manager"></a>Prise en main du Gestionnaire de conformité

**Dans cet article :** Cet article vous aide à configurer le Gestionnaire de conformité. Découvrez comment **accéder** au Gestionnaire de conformité, **définir des rôles et des autorisations** et configurer le **test automatique des actions d’amélioration**. Parcourez **votre tableau de bord du Gestionnaire de conformité** et comprenez les pages principales : la page des actions d’amélioration, la page des solutions, la page des évaluations et la page des modèles d’évaluation.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="who-can-access-compliance-manager"></a>Qui peut accéder au Gestionnaire de conformité

Le Gestionnaire de conformité est disponible pour les organisations disposant de licences Office 365 et Microsoft 365, ainsi que pour les clients modérés du cloud de la communauté du secteur public (GCC), GCC High et du ministère de la Défense (DoD). Les fonctionnalités de gestion et de disponibilité de l’évaluation dépendent de votre contrat de licence.  [Afficher les détails de la description du service](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="before-you-begin"></a>Avant de commencer

L’administrateur général Microsoft 365 de votre organisation sera probablement le premier utilisateur à accéder au Gestionnaire de conformité. Nous vous recommandons de vous connecter à l’administrateur général et de définir les autorisations utilisateur comme indiqué ci-dessous lors de la première visite du Gestionnaire de conformité.

## <a name="sign-in"></a>Connexion

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a> et **connectez-vous** avec votre compte d’administrateur général Microsoft 365.
2. Sélectionnez **Gestionnaire de conformité** dans le volet de navigation gauche. Vous arriverez à votre [tableau de bord du Gestionnaire de conformité](#understand-the-compliance-manager-dashboard).

Le lien direct pour accéder au Gestionnaire de conformité est [https://compliance.microsoft.com/compliancemanager](https://compliance.microsoft.com/compliancemanager).

## <a name="set-user-permissions-and-assign-roles"></a>Définir des autorisations utilisateur et attribuer des rôles

Le Gestionnaire de conformité utilise un modèle d’autorisation de contrôle d’accès en fonction du rôle (RBAC). Seuls les utilisateurs auxquels un rôle est attribué peuvent accéder au Gestionnaire de conformité, et les actions autorisées par chaque utilisateur sont limitées par [type de rôle](#role-types).

### <a name="where-to-set-permissions"></a>Où définir les autorisations

La personne détenant le rôle d’administrateur général de votre organisation peut définir des autorisations utilisateur pour le Gestionnaire de conformité. Les autorisations peuvent être définies dans le portail de conformité Microsoft Purview ainsi que dans Azure Active Directory (Azure AD).

> [!NOTE]
> Les clients des environnements US Government Community (GCC) High et Department of Defense (DoD) peuvent uniquement définir des autorisations et des rôles utilisateur pour le Gestionnaire de conformité dans Azure AD. Consultez les instructions azure AD et les définitions de type de rôle ci-dessous.

Pour définir des autorisations et attribuer des rôles dans le portail de conformité Microsoft Purview, suivez les étapes ci-dessous :

1. Accédez au portail de conformité Microsoft Purview, puis sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Autorisations**</a>.

2. Dans la liste déroulante du portail de conformité, sélectionnez **Rôles**.

3. Recherchez le groupe de rôles auquel vous souhaitez ajouter un ou plusieurs utilisateurs, puis cochez la case à gauche du nom du groupe. (Consultez la [liste des rôles et fonctions associées ci-dessous](#role-types). Les noms des groupes de rôles imitent le nom du rôle.)

4. Dans le volet volant de ce groupe, sélectionnez **Modifier** sous l’en-tête **Membres** .

5. Sélectionnez **Choisir les membres**. Une autre fenêtre de menu volant s’affiche.

6. Sélectionnez **+ Ajouter** pour choisir un ou plusieurs utilisateurs à ajouter au groupe.

7. Cochez la case en regard des noms que vous souhaitez ajouter, puis sélectionnez le bouton **Ajouter** en bas.

8. Lorsque vous avez terminé d’affecter des utilisateurs, sélectionnez **Terminé**, puis **Enregistrer**, puis **Fermer**.

#### <a name="more-about-azure-ad"></a>En savoir plus sur Azure AD

Pour attribuer des rôles et définir des autorisations dans Azure AD, consultez [Attribuer des rôles d’administrateur et de non-administrateur aux utilisateurs avec Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

Les utilisateurs disposant d’identités Azure AD qui n’ont pas d’abonnements Office 365 ou Microsoft 365 ne pourront pas accéder au Gestionnaire de conformité dans le portail de conformité Microsoft Purview. Pour obtenir de l’aide pour accéder au Gestionnaire de conformité, contactez [cmresearch@microsoft.com](mailto:cmresearch@microsoft.com).

### <a name="role-types"></a>Types de rôles

Le tableau ci-dessous présente les fonctions autorisées par chaque rôle dans le Gestionnaire de conformité. Le tableau montre également comment chaque [rôle Azure AD](/azure/active-directory/roles/permissions-reference) est mappé aux rôles du Gestionnaire de conformité. Les utilisateurs auront besoin au moins du rôle lecteur du Gestionnaire de conformité ou du rôle de lecteur global Azure AD pour accéder au Gestionnaire de conformité.

| L’utilisateur peut : | Rôle gestionnaire de conformité | Rôle de Azure AD | 
| :------------- | :-------------: | :------------: |
| **Lire les données mais ne peut pas les modifier**| Gestionnaire de conformité - Lecteur  | Lecteur global Azure AD, Lecteur sécurité |
| **Modifier les données**| Contribution du Gestionnaire de conformité | Administrateur de conformité |
| **Modifier les résultats des tests**| Gestionnaire de conformité - Analyste | Administrateur de conformité |
| **Gérer les évaluations, les modèles et les données de locataire ; affecter des actions d’amélioration**| Administration du Gestionnaire de conformité | Administrateur de conformité, Administrateur des données de conformité, Administrateur de la sécurité  |

## <a name="start-a-premium-assessments-trial"></a>Démarrer une version d’évaluation premium

La version d’évaluation premium du Gestionnaire de conformité est un excellent moyen de configurer rapidement les évaluations les plus pertinentes pour votre organisation. Notre bibliothèque de plus de 300 modèles correspond aux réglementations gouvernementales et aux normes du secteur dans le monde entier.
En savoir plus sur la [version d’évaluation premium](compliance-easy-trials-compliance-manager-assessments.md).

Vous pouvez démarrer votre version d’évaluation directement à partir du Gestionnaire de conformité et configurer les évaluations recommandées en procédant comme suit :

1. Dans la page **Vue d’ensemble** du Gestionnaire de conformité, sélectionnez **Démarrer la version d’évaluation**. Vous allez entrer un Assistant d’activation d’essai qui posera des questions pour nous aider à recommander des évaluations pour votre organisation.

2. Dans la page **Activer la version d’évaluation** , sélectionnez **Suivant** pour commencer votre essai gratuit d’évaluations Premium de 90 jours et continuer à créer des évaluations.

3. Sélectionnez un ou plusieurs secteurs d’activité qui identifient votre organisation, puis sélectionnez **Suivant**.

4. Sélectionnez une ou plusieurs régions pour l’emplacement de votre organisation, puis sélectionnez **Suivant**.

5. Dans l’écran **Choisir les évaluations** , sélectionnez la flèche déroulante en regard de **Modèles recommandés** pour afficher la liste des évaluations qui s’appliquent à votre organisation. Cochez les cases en regard des modèles que vous souhaitez utiliser pour créer des évaluations, puis sélectionnez **Suivant**.

6. Passez en revue vos sélections finales et sélectionnez **Ajouter des évaluations recommandées** pour créer vos nouvelles évaluations.

Pour en savoir plus sur la prise en main des évaluations, consultez la [section Évaluations](#assessments-page) ci-dessous.

## <a name="settings-for-automated-testing-and-user-history"></a>Paramètres pour les tests automatisés et l’historique utilisateur

Les paramètres du Gestionnaire de conformité dans le portail de conformité Microsoft Purview vous permettent d’activer et de désactiver le test automatique des actions d’amélioration. Les paramètres vous permettent également de gérer les données des utilisateurs associés aux actions d’amélioration, notamment la possibilité de réaffecter des actions d’amélioration à un autre utilisateur.  Seules les personnes disposant d’un rôle Administrateur général ou Administrateur du Gestionnaire de conformité peuvent accéder aux paramètres du Gestionnaire de conformité.

> [!NOTE]
> La fonctionnalité de test automatisé n’est pas disponible pour les clients dans les environnements GCC High et DoD, car le degré de sécurisation n’est pas disponible dans ces environnements. Les clients GCC High et DoD devront implémenter et tester manuellement leurs actions d’amélioration.

### <a name="set-up-automated-testing"></a>Configurer des tests automatisés

Le Gestionnaire de conformité détecte les signaux d’autres solutions Microsoft Purview auxquelles votre organisation peut s’abonner, notamment la gestion du cycle de vie des données, la protection des informations, les Protection contre la perte de données Microsoft Purview, la conformité des communications et la gestion des risques internes. Le Gestionnaire de conformité détecte également les signaux provenant d’actions d’amélioration complémentaires qui sont surveillées par [microsoft Secure Score](../security/defender/microsoft-secure-score.md).

À l’aide de ces signaux, le Gestionnaire de conformité peut tester automatiquement certaines actions d’amélioration pour vous, ce qui vous permet d’optimiser l’efficacité de vos activités de conformité. Lorsqu’une action d’amélioration est correctement testée et implémentée, vous recevez le montant total de points, qui est [crédité sur votre score de conformité global](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).

**Le test automatique est activé par défaut pour les organisations qui débutent avec le Gestionnaire de conformité.** Lorsque vous déployez Microsoft 365 ou Office 365 pour la première fois, la collecte complète des données et leur prise en compte dans votre score de conformité prend environ sept jours. Lorsque le test automatisé est activé, la date de test de l’action n’est pas mise à jour, mais son état de test est mis à jour. Lorsque de nouvelles évaluations sont créées, les scores incluent automatiquement les scores de contrôle Microsoft et l’intégration du degré de sécurisation. Consultez [Gérer les paramètres de test automatisé](#manage-automated-testing-settings) ci-dessous pour modifier ou désactiver ce paramètre.

#### <a name="how-to-tell-which-actions-are-tested-automatically"></a>Comment savoir quelles actions sont testées automatiquement

Dans la page **Actions d’amélioration** , recherchez la colonne **Source de test** . Si la valeur est répertoriée comme **Automatique**, l’action est automatiquement testée par le Gestionnaire de conformité.  Si la valeur est **Manuel**, l’action est testée par votre organisation. Si la valeur est **Parent**, l’action hérite de l’état de test d’une autre action à laquelle elle est liée. Obtenez des détails sur la [source de test de l’action d’amélioration](compliance-manager-improvement-actions.md#update-testing-source).

#### <a name="which-actions-cant-be-tested-automatically"></a>Quelles actions ne peuvent pas être testées automatiquement

Les actions d’amélioration dans les modèles non limités à Microsoft 365 ne sont actuellement pas éligibles pour les tests automatiques. Par exemple, les modèles universels ou un modèle pour Microsoft Azure ou Microsoft Dynamics n’auront pas d’actions pouvant être testées automatiquement. En savoir plus sur les [modèles d’évaluation](compliance-manager-templates.md).

#### <a name="manage-automated-testing-settings"></a>Gérer les paramètres de test automatisé

L’administrateur général de votre organisation peut modifier les paramètres des tests automatisés à tout moment. Vous pouvez désactiver les tests automatisés pour les actions d’amélioration courantes ou les activer pour des actions individuelles. Suivez les instructions ci-dessous pour modifier vos paramètres de test automatisé.

1. Sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Paramètres**</a> dans le portail de conformité Microsoft Purview.

2. Dans la page des paramètres, sélectionnez **Gestionnaire de conformité**.

3. Sélectionnez **Source de test** dans le volet de navigation gauche.

4. Sélectionnez le bouton applicable pour activer le test automatique pour toutes les actions d’amélioration, le désactiver pour toutes les actions ou l’activer par action individuelle.

5. Si vous sélectionnez **Activer par action d’amélioration**, une liste affiche toutes les actions d’amélioration disponibles parmi lesquelles choisir.  Cochez la case en regard de toute action que vous souhaitez tester automatiquement.

6. Sélectionnez **Enregistrer** pour enregistrer vos paramètres. Vous recevrez un message de confirmation en haut de votre écran indiquant que votre sélection a été enregistrée. Si vous recevez un avis d’échec, réessayez.

> [!NOTE]
> Seul l’administrateur général peut activer ou désactiver les mises à jour automatiques pour toutes les actions. L’administrateur du Gestionnaire de conformité peut activer les mises à jour automatiques pour les actions individuelles, mais pas pour toutes les actions globalement.

### <a name="manage-user-history"></a>Gérer l’historique utilisateur

Les paramètres **Gérer l’historique utilisateur** vous aident à identifier rapidement les utilisateurs qui ont travaillé avec des actions d’amélioration dans le Gestionnaire de conformité. Les données utilisateur identifiables associées aux actions d’amélioration incluent l’état des actions d’amélioration et des documents qu’ils ont chargés. La compréhension et la récupération de ce type de données peuvent être nécessaires pour les besoins de conformité de votre organisation.

Les paramètres de l’historique utilisateur vous permettent également de réaffecter toutes les actions d’amélioration d’un utilisateur à un autre.

**Pour rechercher les paramètres de l’historique utilisateur :**

1. Sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Paramètres**</a> dans le portail de conformité Microsoft Purview.

2. Dans la page des paramètres, sélectionnez **Gestionnaire de conformité**.

3. Sélectionnez **Gérer l’historique utilisateur** dans le volet de navigation gauche.

La page **Gérer l’historique utilisateur** affiche une liste de tous les utilisateurs par adresse e-mail qui sont affectés à une action d’amélioration. Utilisez le bouton **Rechercher** pour trouver rapidement un utilisateur spécifique en tapant son adresse e-mail.

À droite de l’adresse e-mail de chaque utilisateur, le menu déroulant **Sélectionner** fournit des options pour exporter un rapport, réaffecter des actions d’amélioration ou supprimer l’historique. Pour plus d’informations sur chaque option, consultez chaque section ci-dessous.

#### <a name="export-a-report-of-user-history-data"></a>Exporter un rapport de données d’historique utilisateur

Vous pouvez exporter un fichier Excel contenant une liste d’actions d’amélioration actuellement attribuées à un utilisateur.  Le rapport répertorie également tous les fichiers de preuve chargés par cet utilisateur. Ces informations peuvent vous aider à réaffecter des actions d’amélioration ouvertes.

Le rapport reflète l’état de l’action d’amélioration à sa date de création. Il ne s’agit pas d’un rapport historique de toutes les modifications précédentes apportées à son état ou à son affectation (découvrez comment [exporter un rapport à partir de la page des actions d’amélioration](compliance-manager-improvement-actions.md#export-a-report)).

**Suivez les étapes ci-dessous pour exporter un rapport par utilisateur :**

1. Sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Paramètres**</a> dans le portail de conformité Microsoft Purview.

2. Dans la page des paramètres, sélectionnez **Gestionnaire de conformité**.

3. Sélectionnez **Gérer l’historique utilisateur** dans le volet de navigation à gauche.

4. Recherchez l’utilisateur prévu en recherchant les adresses e-mail de la liste, ou en sélectionnant **Rechercher** et en entrant l’adresse e-mail de l’utilisateur.

5. Dans le menu déroulant **Sélectionner** , choisissez **Exporter le rapport**.

6. Une fois le fichier Excel de votre rapport généré, vous pouvez l’ouvrir et l’enregistrer sur votre ordinateur local.

#### <a name="reassign-improvement-actions-to-another-user"></a>Réaffecter les actions d'amélioration à un autre utilisateur

Vous pouvez réaffecter des actions d’amélioration d’un utilisateur à un autre. Lorsque vous réaffectez une action, l’historique de chargement du document ne change pas, mais le nom de l’utilisateur qui a initialement chargé la documentation n’apparaît plus dans l’action d’amélioration.

**Suivez les étapes ci-dessous pour réaffecter des actions d’amélioration à un autre utilisateur :**

1. Sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Paramètres**</a> dans le portail de conformité Microsoft Purview.

2. Dans la page des paramètres, sélectionnez **Gestionnaire de conformité**.

3. Sélectionnez **Gérer l’historique utilisateur** dans le volet de navigation à gauche.

4. Recherchez un utilisateur en effectuant une recherche dans la liste d’adresses e-mail, ou en sélectionnant **Rechercher** et en entrant l’adresse e-mail de cet utilisateur.

5. Dans le menu déroulant **Sélectionner** , choisissez **Réaffecter les actions d’amélioration**. Le volet volant **Réaffecter les actions d’amélioration** s’affiche.

6. Dans le champ **Rechercher des utilisateurs** , entrez le nom ou l’adresse e-mail de l’utilisateur *auquel* vous souhaitez affecter les actions d’amélioration.

7. Lorsque vous voyez le nom de l’utilisateur prévu sous **Actions d’amélioration qui seront affectées,** sélectionnez l’utilisateur, puis **sélectionnez Affecter des actions**.

8. Une fois la réaffectation terminée, un message de confirmation s’affiche dans le volet volant confirmant que toutes les actions d’amélioration de l’utilisateur précédent ont été réaffectées au nouvel utilisateur. Si vous recevez un avis d’échec de réaffectation, fermez la fenêtre et réessayez. Pour fermer le volet volant, sélectionnez **Terminé**.

Le nouveau destinataire reçoit un e-mail indiquant qu’il a été affecté à une action d’amélioration. L’e-mail contient un lien direct vers la page de détails de l’action d’amélioration.

 > [!NOTE]
> Si vous réaffectez une action qui a une mise à jour en attente, le lien direct vers l’action dans l’e-mail de réaffectation s’arrête si la mise à jour est acceptée après la réaffectation. Vous pouvez résoudre ce problème en ré assignant l’action à l’utilisateur une fois la mise à jour acceptée. En savoir plus sur les [mises à jour des actions d’amélioration](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

#### <a name="delete-user-history"></a>Supprimer l’historique utilisateur

La suppression de l’historique d’un utilisateur le supprimera en tant que propriétaire des actions d’amélioration et supprimera son nom de tous les autres champs dans le Gestionnaire de conformité. Lorsque vous supprimez l’historique d’un utilisateur, les actions d’amélioration dont il était propriétaire n’affichent pas la valeur **Affectée à** tant qu’un nouvel utilisateur n’est pas affecté. Tous les documents chargés vers l’action d’amélioration affichent **l’utilisateur supprimé** à la place du nom de l’utilisateur supprimé. La suppression de l’historique utilisateur est permanente.

Pour supprimer l’historique d’un utilisateur, suivez les étapes ci-dessous :

1. Sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Paramètres**</a> dans le portail de conformité Microsoft Purview.

2. Dans la page des paramètres, sélectionnez **Gestionnaire de conformité**.

3. Sélectionnez **Gérer l’historique utilisateur** dans le volet de navigation à gauche.

4. Recherchez un utilisateur en effectuant une recherche dans la liste d’adresses e-mail, ou en sélectionnant **Rechercher** et en entrant l’adresse e-mail de cet utilisateur.

5. Dans le menu déroulant **Sélectionner** , choisissez **Supprimer l’historique**.

6. Une fenêtre s’affiche pour vous demander de confirmer la suppression définitive de l’historique de l’utilisateur. Pour poursuivre la suppression, sélectionnez **Supprimer l’historique**. Pour quitter sans supprimer l’historique, sélectionnez **Annuler**.

7. Vous revenez à la page **Gérer l’historique utilisateur** avec un message de confirmation en haut indiquant que l’historique de l’utilisateur a été supprimé.

## <a name="understand-the-compliance-manager-dashboard"></a>Comprendre le tableau de bord du Gestionnaire de conformité

Le tableau de bord du Gestionnaire de conformité est conçu pour vous fournir une vue d’ensemble de votre posture de conformité actuelle.

:::image type="content" alt-text="Gestionnaire de conformité – tableau de bord." source="../media/compliance-manager-dashboard.png" lightbox="../media/compliance-manager-dashboard.png":::

### <a name="overall-compliance-score"></a>Score de conformité global

Votre score de conformité figure en tête de liste. Il affiche un pourcentage basé sur les points réalisables pour effectuer des actions d’amélioration qui répondent aux normes et réglementations clés en matière de protection des données. Les points des [actions Microsoft](compliance-manager-assessments.md#microsoft-actions-tab), qui sont gérées par Microsoft, comptent également dans votre score de conformité.

Lorsque vous accédez au Gestionnaire de conformité pour la première fois, votre score initial est basé sur la [base de référence de protection des données Microsoft 365](compliance-manager-assessments.md#data-protection-baseline-default-assessment). Cette évaluation de base, qui est disponible pour toutes les organisations, est un ensemble de contrôles qui incluent des réglementations et des normes courantes du secteur. Le Gestionnaire de conformité vérifie vos solutions Microsoft 365 existantes et vous donne une évaluation initiale basée sur vos paramètres de confidentialité et de sécurité actuels. À mesure que vous ajoutez des évaluations pertinentes pour votre organisation, votre score devient plus significatif pour vous.

**En savoir plus :** [Comprendre comment votre score de conformité est calculé](compliance-score-calculation.md).

### <a name="key-improvement-actions"></a>Principales actions d’amélioration

Cette section répertorie les principales actions d’amélioration que vous pouvez entreprendre dès maintenant pour avoir le plus grand impact positif sur votre score de conformité global. Sélectionnez **Afficher toutes les actions d’amélioration** pour accéder à la page de vos actions d’amélioration.

### <a name="solutions-that-affect-your-score"></a>Solutions qui affectent votre score

Cette section met en évidence les solutions contenant des actions d’amélioration qui peuvent avoir un impact positif sur votre score, ainsi que le nombre d’actions d’amélioration en suspens dans ces solutions. Sélectionnez **Afficher toutes les solutions** pour accéder à la page de vos solutions.

### <a name="compliance-score-breakdown"></a>Répartition du score de conformité

Cette section vous donne une vue plus détaillée de votre score de deux manières différentes :

- **Catégories** : affiche le pourcentage de votre score global dans les catégories de protection des données, telles que « protéger les informations » ou « gérer les appareils ».
- **Évaluations** : indique le pourcentage de vos progrès dans la gestion des évaluations pour des normes, réglementations ou lois particulières en matière de conformité et de protection des données, telles que le RGPD ou le NIST 800-53.

### <a name="filtering-your-dashboard-view"></a>Filtrage de la vue de votre tableau de bord

Vous pouvez filtrer votre affichage de tableau de bord pour afficher uniquement les éléments liés à des réglementations et normes particulières, des solutions, un type d’action, des groupes d’évaluation ou des catégories de protection des données. Le filtrage de votre vue de cette façon filtre également le score sur votre tableau de bord, indiquant le nombre de points que vous avez obtenus sur le total des points possibles en fonction de vos critères de filtre.

Pour appliquer des filtres :

1. Sélectionnez **Filtrer** en haut à droite du tableau de bord.
2. Sélectionnez vos critères de filtre dans le volet **volant Filtres** , puis sélectionnez **Appliquer**.

Après avoir appliqué un filtre, votre score est ajusté en temps réel. Le pourcentage de score de conformité et les informations de répartition, ainsi que les actions et solutions d’amélioration, concernent désormais uniquement les données couvertes par vos critères de filtre. Si vous vous déconnectez du Gestionnaire de conformité, votre affichage filtré reste lorsque vous vous reconnectez.

Pour supprimer des filtres :

- Dans l’en-tête **Filtres appliqués** au-dessus de votre score de conformité, sélectionnez le **X** en regard du filtre individuel que vous souhaitez supprimer. Ou
- Sélectionnez **Filtrer** en haut à droite de votre tableau de bord, puis dans le volet **volant Filtres** , sélectionnez **Effacer les filtres**.

## <a name="improvement-actions-page"></a>Page Actions d’amélioration

[Les actions d’amélioration](compliance-manager-improvement-actions.md) sont des actions gérées par votre organisation. L’utilisation d’actions d’amélioration permet de centraliser vos activités de conformité et de vous aligner sur les réglementations et normes de protection des données. Chaque action d’amélioration fournit des conseils d’implémentation détaillés et un lien pour vous lancer dans la solution appropriée. Des actions d’amélioration peuvent être affectées aux utilisateurs de votre organisation pour effectuer un travail d’implémentation et de test. Vous pouvez également stocker de la documentation, des notes et enregistrer des mises à jour d’état dans l’action d’amélioration.

### <a name="view-your-improvement-actions"></a>Afficher vos actions d’amélioration

Le tableau de bord du Gestionnaire de conformité affiche vos principales actions d’amélioration. Pour afficher toutes vos actions d’amélioration, sélectionnez l’onglet **Actions d’amélioration** dans votre tableau de bord, ce qui vous permet d’accéder à la page de vos actions d’amélioration. Vous pouvez également sélectionner **Afficher toutes les actions d’amélioration** sous la liste des actions d’amélioration clés de votre tableau de bord pour accéder à la page des actions d’amélioration.

La page Actions d’amélioration affiche toutes les actions d’amélioration gérées par votre organisation. Les actions gérées par Microsoft peuvent être consultées dans chaque évaluation (en savoir plus sur [les actions Microsoft](compliance-manager-assessments.md#microsoft-actions-tab)).

Si vous avez une longue liste d’actions sur votre page d’actions d’amélioration, il peut être utile de filtrer votre affichage. Sélectionnez **Filtrer** en haut à droite de la liste des actions. Lorsque le volet **volant Filtres** s’affiche, sélectionnez vos critères parmi les options disponibles. Vous pouvez également personnaliser votre affichage en sélectionnant **Grouper** dans le coin supérieur droit. Dans le menu déroulant, sélectionnez pour afficher par groupe, solution, catégorie, type d’action ou état.

L’affichage par défaut de cette page n’affiche pas les actions d’amélioration avec l’état de test **Réussi**. Pour afficher les actions qui ont réussi le test, cochez la case **Réussite** dans le volet volant Filtres. Seules les actions avec l’état de test **Réussite** comptent dans votre score. Certaines actions peuvent afficher une **étiquette de mise à jour en attente.** En savoir plus sur les [mises à jour des actions d’amélioration](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

La page actions d’amélioration affiche les points de données suivants pour chaque action d’amélioration :

- **Products** : produit en cours d’évaluation.
- **Points atteints** : nombre de points obtenus sur le total disponible en effectuant l’action
- **Règlements** : les réglementations ou normes relatives à l’action
- **Groupe** : groupe auquel vous avez affecté l’action
- **Solutions** : la solution dans laquelle vous pouvez vous rendre pour effectuer l’action
- **Évaluations** : les évaluations qui contiennent l’action
- **Catégories** : catégorie de protection des données associée (par exemple, protéger les informations, gérer les appareils, etc.)
- **État du test** :
  - **Aucun :** aucune mise à jour d’état enregistrée
  - **Non évalué** : le test n’a pas démarré
  - **Réussite** : l’implémentation a été testée avec succès
  - **Échec à faible risque** - Échec du test, risque faible
  - **Échec à risque moyen** : échec du test, risque moyen
  - **Échec à risque élevé** - Échec du test, risque élevé
  - **Hors de l’étendue** : l’action n’est pas dans l’étendue de l’évaluation et n’a pas d’impact sur votre score
  - **À détecter** : pour un test manuel, indique qu’une action a été implémentée, mais pas testée ; pour le test automatisé, indique qu’une action attend le résultat de l’automatisation
  - **Impossible de détecter** : l’état automatisé ne peut pas être déterminé
  - **Partiellement testé :** scoring automatisé qui attribue des points partiels
- **Type d’action** : indique si l’action d’amélioration est technique, ce qui signifie qu’elle peut être implémentée dans une solution ou un produit, ou non technique, qui serait implémentée en dehors d’une solution technique
- **Affecté à** : la personne à laquelle cette action a été affectée, le cas échéant
- **Source de test** : indique si la source de test de l’action est manuelle, automatique ou héritée d’un parent

**En savoir plus :** [Découvrez comment affecter et effectuer des tâches sur des actions d’amélioration](compliance-manager-improvement-actions.md).

## <a name="solutions-page"></a>Page Solutions

La page solutions affiche le partage des points gagnés et potentiels organisés par solution. L’affichage des points restants et des actions d’amélioration à partir de cette vue vous aide à comprendre quelles solutions nécessitent une attention plus immédiate.

Recherchez la page solutions en sélectionnant l’onglet **Solutions** dans votre tableau de bord du Gestionnaire de conformité. Vous pouvez également sélectionner **Afficher toutes les solutions** sous **Solutions qui affectent votre score** dans la section supérieure droite de votre tableau de bord.

### <a name="filtering-your-solutions-view"></a>Filtrage de la vue de vos solutions

Pour filtrer votre vue des solutions :

1. Sélectionnez **Filtrer** en haut à gauche de votre liste d’évaluations.
2. Dans le volet **volant Filtres** , cochez les critères souhaités (réglementations, solutions, types d’actions, groupes, catégories).
3. Sélectionnez le bouton **Appliquer** . Le volet de filtre se ferme et votre affichage filtré s’affiche.

Vous pouvez également modifier votre affichage pour afficher les évaluations par groupe, produit ou réglementation en sélectionnant le type de regroupement dans le menu déroulant **Groupe** au-dessus de votre liste d’évaluations.

### <a name="taking-action-from-the-solution-page"></a>Action à partir de la page de la solution

La page solutions affiche les solutions de votre organisation qui sont connectées aux actions d’amélioration. Le tableau répertorie la contribution de chaque solution à votre score global, les points obtenus et possibles au sein de cette solution, ainsi que le nombre restant d’actions d’amélioration regroupées dans cette solution qui peuvent augmenter votre score.

Il existe deux façons d’effectuer une action à partir de cet écran :

1. Sur la ligne de la solution prévue, sous la colonne **Actions restantes** , sélectionnez le numéro hypertexte. Vous verrez une vue filtrée de l’écran actions d’amélioration montrant les actions d’amélioration non testées pour cette solution.

2. Sur la ligne de votre solution prévue, sous la colonne **Ouvrir la solution** , sélectionnez **Ouvrir**. Vous arriverez à l’emplacement de la solution dans le portail de conformité Microsoft Purview, le portail Microsoft 365 Defender ou son centre d’administration, où vous pouvez effectuer l’action recommandée.

## <a name="assessments-page"></a>Page Évaluations

La page évaluations répertorie toutes les [évaluations](compliance-manager-assessments.md) que vous avez configurées pour votre organisation. Votre dénominateur de score de conformité est déterminé par toutes vos évaluations suivies. À mesure que vous ajoutez d’autres évaluations, vous verrez d’autres actions d’amélioration répertoriées sur la page de vos actions d’amélioration, et votre dénominateur de score de conformité augmente.

Le compteur **de modèles activés** en haut de la page indique le nombre de modèles d’évaluation actifs actuellement utilisés sur le nombre total de modèles disponibles pour votre organisation. Pour plus d’informations, consultez [Disponibilité et gestion des licences](compliance-manager-templates.md#template-availability-and-licensing) des modèles.

La page évaluations récapitule les informations clés sur chaque évaluation :

- **Évaluation** : nom de l’évaluation
- **Statut** :
  - **Terminé** : tous les contrôles ont l’état « Passé », ou au moins un est passé et les autres sont « hors de portée »
  - **Incomplet** : au moins un contrôle a l’état « Échec »
  - **Aucun** : tous les contrôles n’ont pas été testés
  - **En cours** : les actions d’amélioration ont tout autre état, y compris « en cours », « crédit partiel » ou « non détecté »
- **Progression de l’évaluation** : pourcentage du travail effectué en vue de l’achèvement, mesuré par le nombre de contrôles testés avec succès
- **Vos actions d’amélioration** : nombre d’actions terminées pour satisfaire l’implémentation de vos contrôles
- **Actions Microsoft** : nombre d’actions terminées pour satisfaire l’implémentation des contrôles Microsoft
- **Groupe** : nom du groupe auquel appartient l’évaluation
- **Produit** : produit associé, tel que Microsoft 365 ou un autre produit défini pour l’évaluation
- **Réglementation** : la norme réglementaire, la politique ou la loi qui s’applique à l’évaluation

### <a name="filtering-your-assessments-view"></a>Filtrage de la vue des évaluations

Pour filtrer votre affichage des évaluations :

1. Sélectionnez **Filtrer** en haut à gauche de votre liste d’évaluations.
2. Dans le volet **volant Filtres** , vérifiez les critères souhaités.
3. Sélectionnez le bouton **Appliquer** . Le volet de filtre se ferme et votre vue filtrée s’affiche.

Vous pouvez également modifier votre affichage pour afficher les évaluations par groupe, produit ou réglementation en sélectionnant le type de regroupement dans le menu déroulant **Groupe** au-dessus de votre liste d’évaluations.

### <a name="default-assessment"></a>Évaluation par défaut

Par défaut, vous verrez l’évaluation [de la base de référence de la protection des données](compliance-manager-assessments.md#data-protection-baseline-default-assessment) sur la page des évaluations. Le Gestionnaire de conformité fournit également plusieurs [modèles prédéfinis](compliance-manager-templates-list.md) pour générer des évaluations.

## <a name="assessment-templates-page"></a>Page modèles d’évaluation

Un modèle est un cadre permettant de créer une évaluation dans le Gestionnaire de conformité. La page des modèles d’évaluation affiche une liste de modèles et des informations clés. La liste inclut les modèles fournis par le Gestionnaire de conformité, ainsi que tous les modèles que votre organisation a modifiés ou créés. Vous pouvez appliquer des filtres pour rechercher un modèle en fonction de la certification, de l’étendue du produit, du pays, du secteur et de la personne qui l’a créé.

Le compteur **de modèles activés** en haut de la page indique le nombre de modèles d’évaluation actifs actuellement utilisés sur le nombre total de modèles disponibles pour votre organisation. Pour plus d’informations, consultez [Disponibilité et gestion des licences](compliance-manager-templates.md#template-availability-and-licensing) des modèles.

Sélectionnez un modèle à partir de sa ligne pour afficher sa page de détails, qui contient une description du modèle et des informations supplémentaires sur la certification, l’étendue et les détails des contrôles. À partir de cette page, vous pouvez sélectionner les boutons appropriés pour créer une évaluation, exporter les données du modèle vers Excel ou modifier le modèle.

**En savoir plus :** [Découvrez comment utiliser des modèles d’évaluation](compliance-manager-templates.md).

## <a name="next-step"></a>Étape suivante

Personnalisez le Gestionnaire de conformité [en configurant des évaluations](compliance-manager-assessments.md).
