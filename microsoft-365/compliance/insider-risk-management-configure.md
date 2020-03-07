---
title: Prise en main de la gestion des risques initiés
description: Configurez la gestion des risques initiaux dans votre organisation.
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: Microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 4b8bd0f8d540434410d9ebc2365789a669f455e1
ms.sourcegitcommit: b567e946b57697186267cdfe303dfe3463cfd6ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "42552038"
---
# <a name="get-started-with-insider-risk-management"></a>Prise en main de la gestion des risques initiés

Utilisez des stratégies de gestion des risques internes pour identifier les activités à risque et les outils de gestion qui permettent de prendre des mesures concernant les alertes de risque au sein de votre organisation. Procédez comme suit pour configurer les conditions préalables et configurer une stratégie de gestion des risques inSided.

>[!IMPORTANT]
>La solution de gestion des risques Microsoft 365 Insider offre une option de niveau client pour aider les clients à faciliter la gouvernance interne au niveau de l’utilisateur. Les administrateurs de niveau client peuvent configurer des autorisations pour permettre l’accès à cette solution pour les membres de votre organisation et configurer des connecteurs de données dans le centre de conformité Microsoft 365 pour importer des données pertinentes afin de prendre en charge l’identification de niveau utilisateur potentiellement activité à risque. Les clients reconnaissent les informations relatives au comportement, au caractère ou aux performances des utilisateurs individuels liés à l’emploi, peuvent être calculées par l’administrateur et mises à la disposition des autres membres de l’organisation.

Pour plus d’informations sur la façon dont les stratégies de risque d’initié peuvent vous aider à gérer les risques au sein de votre organisation, consultez la rubrique [gestion des risques internes dans Microsoft 365](insider-risk-management.md).

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer à gérer les risques initiaux, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans). Pour accéder à la gestion des risques initiés et l’utiliser, votre organisation doit disposer de l’un des abonnements suivants :

- Abonnement Microsoft 365 E5 (payant ou version d’évaluation)
- Abonnement Microsoft 365 entreprise E3 avec le [complément de conformité Microsoft E5](https://signup.microsoft.com/signup/?offerid=57806d24-4357-4eff-b0a3-4054ebdf2abe&DL=INFORMATION_PROTECTION_COMPLIANCE&ali=1)

Les utilisateurs inclus dans les stratégies de gestion des risques internes doivent disposer d’une licence de conformité Microsoft 365 E5 ou être inclus dans un abonnement Microsoft 365 E5.

Si vous ne disposez pas d’un plan Microsoft 365 entreprise E5 existant et que vous souhaitez essayer de gérer les risques internes, vous pouvez [Ajouter microsoft 365](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365) à votre abonnement Office 365 existant ou [vous inscrire pour obtenir une version d’évaluation](https://www.microsoft.com/microsoft-365/enterprise) de Microsoft 365 entreprise E5.

## <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Étape 1 (obligatoire) : activer les autorisations pour la gestion des risques initiés

Il existe quatre groupes de rôles utilisés pour configurer les autorisations permettant de gérer les fonctionnalités de gestion des risques inSided. Pour poursuivre ces étapes de configuration, vos administrateurs client doivent d’abord vous attribuer le groupe de rôles d’administrateur de gestion des **risques Insiders** ou d' **Insider Management** . Pour accéder et gérer les fonctionnalités de gestion des risques internes après la configuration initiale, les utilisateurs doivent être membres d’au moins un groupe de rôles de gestion des risques Insiders.

En fonction de la structure de votre équipe de gestion de la conformité, vous disposez des options permettant d’affecter des utilisateurs à des groupes de rôles spécifiques afin de gérer différents ensembles de fonctionnalités de gestion des risques initiés. Vous avez le choix entre ces options de groupe de rôles lors de la configuration de la gestion des risques initiés :

| **Groupe de rôles** | **Autorisations de rôle** |
| :---- | :---------------- |
| **Gestion des risques initiés** | Utilisez ce groupe de rôles pour gérer la gestion des risques Insider de votre organisation dans un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes et investigateurs désignés, vous pouvez configurer des autorisations de gestion des risques Insider dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de gestion des risques Insider. Il s’agit de la méthode la plus simple pour démarrer rapidement avec la gestion des risques initiés et pour les organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts.|
| **Administrateur de gestion des risques des Insiders** | Utilisez ce groupe de rôles pour configurer initialement la gestion des risques initiés et, par la suite, pour séparer les administrateurs des risques des Insiders en un groupe défini.  Les utilisateurs de ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de gestion des risques internes, des paramètres globaux et des affectations de groupes de rôles. |
| **Analystes de gestion des risques Insiders** | Utilisez ce groupe pour attribuer des autorisations à des utilisateurs qui agiront en tant qu’analystes de cas d’Insider. Les utilisateurs de ce groupe de rôles peuvent accéder aux modèles alertes, incidents et notifications de gestion des risques Insider. Ils ne peuvent pas accéder à l’Explorateur de contenu risque Insider. |
| **Investigateurs de gestion des risques Insiders** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agiront en tant qu’enquêteurs de données sur les risques des Insiders. Les utilisateurs de ce groupe de rôles peuvent accéder à toutes les alertes de gestion des risques Insider, les cas, les modèles de notifications et l’Explorateur de contenu dans tous les cas. |

### <a name="add-users-to-an-insider-risk-management-role-group"></a>Ajouter des utilisateurs à un groupe de rôles de gestion des risques Insider

Procédez comme suit pour ajouter des utilisateurs à un groupe de rôles de gestion des risques Insider :

1. Connectez- [https://protection.office.com/permissions](https://protection.office.com/permissions) vous à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de sécurité et conformité Microsoft Office 365, accédez à **autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez le groupe de rôles Gestion des risques Insiders auquel vous souhaitez ajouter des utilisateurs, puis sélectionnez **modifier le groupe de rôles**.

4. Sélectionnez **choisir les membres** dans le volet de navigation de gauche, puis sélectionnez **modifier**.

5. Sélectionnez **Ajouter** , puis activez la case à cocher de tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Sélectionnez **Ajouter**, puis sélectionnez **Terminer**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles. Sélectionnez **Fermer** pour effectuer les étapes.

## <a name="step-2-required-enable-the-office-365-audit-log"></a>Étape 2 (obligatoire) : activer le journal d’audit Office 365

La gestion des risques internes utilise les journaux d’audit pour les activités et les informations utilisateur configurées dans les stratégies. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie de gestion des risques inSided ou à chaque fois qu’une stratégie est modifiée.

Pour obtenir des instructions détaillées sur l’activation de l’audit, voir [activer ou désactiver la recherche dans le journal d’audit Office 365](turn-audit-log-search-on-or-off.md). Une fois que vous avez activé l’audit, un message s’affiche indiquant que le journal d’audit est en cours de préparation et que vous pouvez exécuter une recherche dans quelques heures après la fin de la préparation. Vous n’avez besoin d’effectuer cette action qu’une seule fois. Pour plus d’informations sur l’utilisation du journal d’audit, consultez [la rubrique Search the audit log](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-configure-prerequisites-for-templates"></a>Étape 3 (facultative) : configuration des éléments prérequis pour les modèles

Certains modèles de gestion des risques initiaux doivent être configurés pour que les indicateurs de stratégie génèrent des alertes d’activité pertinentes. Configurez les conditions préalables appropriées en fonction des stratégies que vous prévoyez de configurer pour votre organisation.

### <a name="configure-microsoft-365-hr-connector"></a>Configurer le connecteur RH de Microsoft 365

La gestion des risques internes prend en charge l’importation des données d’utilisateur et de journal importées des plateformes de gestion des risques et de ressources humaines tierces. Le connecteur de données RH de Microsoft 365 vous permet d’extraire des données de ressources humaines à partir de fichiers CSV, y compris les dates de fin d’emploi et de fin de l’utilisateur. Ces données aident à piloter les indicateurs d’alerte dans les stratégies de gestion des risques internes et constituent un élément important de la configuration de la couverture complète de la gestion des risques dans votre organisation.

Consultez la rubrique [configurer un connecteur pour importer des données RH](import-hr-data.md) pour obtenir des instructions détaillées sur la configuration du connecteur rh Microsoft 365 pour votre organisation. Une fois que vous avez configuré le connecteur RH, revenez à ces étapes de configuration.

>[!IMPORTANT]
>Si vous configurez une stratégie à l’aide du modèle de *vol de données des employés qui fait partie* du, vous devez configurer le connecteur RH pour qu’il utilise les fonctionnalités de détection de signal complètes du modèle de stratégie. Si vous configurez plusieurs connecteurs RH pour votre organisation, la gestion des risques internes extrait automatiquement les indicateurs de tous les connecteurs RH.

### <a name="configure-data-loss-prevention-dlp-policies"></a>Configurer les stratégies de protection contre la perte de données (DLP)

La gestion des risques internes prend en charge l’utilisation des stratégies DLP pour identifier l’exposition intentionnelle ou accidentelle d’informations sensibles aux parties indésirables. Lors de la configuration d’une stratégie de gestion des risques inSided avec le modèle *fuites de données* , vous devez affecter une stratégie DLP spécifique à la stratégie. Cette stratégie permet de piloter les indicateurs d’alerte pour les informations sensibles est une partie importante de la configuration de la couverture complète de la gestion des risques dans votre organisation.

Consultez la rubrique [créer, tester et régler une stratégie DLP](create-test-tune-dlp-policy.md) pour obtenir des instructions détaillées sur la configuration des stratégies DLP pour votre organisation. Une fois que vous avez configuré une stratégie DLP, revenez à ces étapes de configuration.

>[!IMPORTANT]
>Si vous configurez une stratégie à l’aide du modèle *fuites de données* , vous devez configurer au moins une stratégie DLP pour utiliser les fonctionnalités de détection de signal complètes du modèle de stratégie. Si vous configurez plusieurs stratégies DLP pour votre organisation, vous devez attribuer une stratégie de gestion des risques inSided par stratégie DLP.

## <a name="step-4-required-configure-insider-risk-settings"></a>Étape 4 (obligatoire) : configure Insider Risk Settings

Les [paramètres des risques internes](insider-risk-management-policies.md#policy-settings) s’appliquent à toutes les stratégies de gestion des risques internes, quel que soit le modèle que vous avez choisi lors de la création d’une stratégie. Les paramètres sont configurés à l’aide du contrôle des **paramètres des risques Insiders** situé en haut de tous les onglets de gestion des risques Insiders. Ces paramètres contrôlent la confidentialité, les indicateurs, les fenêtres de surveillance et les détections intelligentes.

Avant de configurer une stratégie, définissez les paramètres de risque Insider suivants :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez **paramètres des risques Insiders** dans le coin supérieur droit de n’importe quelle page.
2. Sur la page **confidentialité** , sélectionnez un paramètre de confidentialité pour l’affichage des noms d’utilisateur pour les alertes de stratégie.
3. Sur la page **indicateurs** , sélectionnez les indicateurs d’alerte à appliquer à toutes les stratégies de risque pour les initiés.

    >[!IMPORTANT]
    >Pour recevoir des alertes relatives aux activités à risque définies dans vos stratégies, vous devez sélectionner un ou plusieurs indicateurs.

4. Dans la page périodes de la **stratégie** , sélectionnez les [périodes de stratégie](insider-risk-management-policies.md#policy-timeframes) à appliquer à un utilisateur lorsqu’il déclenche une correspondance pour une stratégie de risque initié par les utilisateurs.
5. Sur la page **détections intelligentes** , configurez les [détections d’anomalies et de langues choquantes](insider-risk-management-policies.md#intelligent-detections) pour les stratégies de risque pour les initiés.
6. Sélectionnez **Enregistrer** pour activer ces paramètres pour vos stratégies de risque Insider.

## <a name="step-5-required-create-an-insider-risk-management-policy"></a>Étape 5 (obligatoire) : créer une stratégie de gestion des risques Insider

Les stratégies de gestion des risques internes incluent les utilisateurs affectés et les types d’indicateurs de risque configurés pour les alertes. Avant que les activités puissent déclencher des alertes, une stratégie doit être configurée.

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **stratégies** .
2. Sélectionnez **créer une stratégie** pour ouvrir l’Assistant stratégie.
3. Sur la page **nouvelle stratégie de risque Insider** , renseignez les champs suivants :
    - **Nom (obligatoire)**: entrez un nom convivial pour la stratégie.
    - **Description (facultatif)**: entrez une description pour la stratégie.
    - **Choisir un modèle de stratégie (obligatoire)**: sélectionnez un des [modèles de stratégie](insider-risk-management-policies.md#policy-templates) pour définir les types d’indicateurs de risque sont surveillés par la stratégie.

    >[!IMPORTANT]
    >Si vous sélectionnez le modèle *fuites de données* , vous devez configurer au moins une stratégie DLP que vous allez attribuer ultérieurement dans l’Assistant. Si vous sélectionnez le modèle de *vol de données par employé* , vous devez configurer le connecteur RH pour qu’il utilise les fonctionnalités de détection de signal complètes du modèle de stratégie.

4. Sélectionnez **suivant** pour continuer.
5. Dans la page **utilisateurs** , sélectionnez **Ajouter un utilisateur ou un groupe** pour définir les utilisateurs inclus dans la stratégie ou cochez la case **tous les utilisateurs et les groupes à extension messagerie** . Sélectionnez **suivant** pour continuer.
6. Sur la page **spécifier le contenu à classer par priorité (facultatif)** , vous pouvez affecter les sources à classer par ordre de priorité pour les activités utilisateur à risque :
    - **Sites SharePoint**: sélectionnez **Ajouter un site SharePoint** et sélectionnez les organisations SharePoint dont vous souhaitez définir la priorité. Par exemple, *« Group1@contoso.sharepoint.com/sites/group1 »*.
    - **Type d’informations sensibles**: sélectionnez **Ajouter un type d’informations sensibles** et sélectionnez les types de critère de diffusion dont vous souhaitez définir la priorité. Par exemple, *« numéro de compte bancaire américain »* et *« numéro de carte de crédit »*.
    - **Étiquettes de sensibilité**: sélectionnez **Ajouter une étiquette de confidentialité** et sélectionnez les étiquettes dont vous souhaitez définir la priorité. Par exemple, *« confidentiel »* et *« secret »*.
7. Sélectionnez **suivant** pour continuer.
8. Sur la **page indicateurs d’alerte** , vous verrez les indicateurs que vous avez définis sur la page**indicateurs** de paramètres > de **risque inSided**. Si vous avez sélectionné le modèle *fuites de données* au début de l’Assistant, vous devez sélectionner une stratégie DLP dans la liste déroulante **stratégie DLP** .
9. Sur la page **Sélectionner la fenêtre d’analyse** , vous verrez les conditions de la fenêtre de [surveillance](insider-risk-management-policies.md#policy-timeframes) pour la stratégie qui s’affichent dans la page**périodes de stratégie** des paramètres > des **risques Insider**. Si vous avez sélectionné le modèle de stratégie de *vol de données par employé* , vous pouvez activer la case à cocher valider l’activité après *arrêt* pour détecter toute activité postérieure à la date d’expiration importée du connecteur RH de Microsoft 365.
10. Sélectionnez **suivant** pour continuer.
11. Sur la page **révision** , passez en revue les paramètres que vous avez choisis pour la stratégie. Sélectionnez **modifier** pour modifier les valeurs de la stratégie ou sélectionnez **Envoyer** pour créer et activer la stratégie.

Une fois que vous avez terminé ces étapes pour créer votre première stratégie de gestion des risques Insiders, vous commencerez à recevoir des alertes des indicateurs d’activité après environ 24 heures. Configurez des stratégies supplémentaires selon vos besoins à l’aide des instructions de l’étape 4 de cette rubrique ou des procédures décrites dans [Create a New Insider Risk Policy](insider-risk-management-policies.md#create-a-new-policy).
