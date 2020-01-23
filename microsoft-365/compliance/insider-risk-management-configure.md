---
title: Prise en main de la gestion des risques initiés (préversion)
description: Configurez la gestion des risques initiaux dans votre organisation.
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: Microsoft-365-enterprise
ms.topic: article
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 5d32e28d53fccbb16d935bbd9348ad7c12bac365
ms.sourcegitcommit: 3dca80f268006658a0b721aa4f6df1224c7964dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "41259842"
---
# <a name="get-started-with-insider-risk-management-preview"></a>Prise en main de la gestion des risques initiés (préversion)

Utilisez des stratégies de gestion des risques internes pour identifier les activités à risque et les outils de gestion qui permettent de prendre des mesures concernant les alertes de risque au sein de votre organisation. Pour plus d’informations sur la façon dont les stratégies de risque d’initié peuvent vous aider à gérer les risques au sein de votre organisation, consultez la rubrique [gestion des risques internes dans Microsoft 365](insider-risk-management.md).

>[!IMPORTANT]
>La solution de gestion des risques Microsoft 365 Insider offre une option de niveau client pour aider les clients à faciliter la gouvernance interne au niveau de l’utilisateur. Les administrateurs de niveau client peuvent configurer des autorisations pour permettre l’accès à cette solution pour les membres de votre organisation et configurer des connecteurs de données dans le centre de conformité Microsoft 365 pour importer des données pertinentes afin de prendre en charge l’identification de niveau utilisateur potentiellement activité à risque. Les clients reconnaissent les informations relatives au comportement, au caractère ou aux performances des utilisateurs individuels liés à l’emploi, peuvent être calculées par l’administrateur et mises à la disposition des autres membres de l’organisation.

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer à gérer les risques initiaux, vous devez confirmer votre abonnement Microsoft 365. Les utilisateurs inclus dans les stratégies de gestion des risques internes doivent disposer d’une licence de conformité Microsoft 365 E5 ou être inclus dans un abonnement Microsoft 365 E5.

Si vous ne disposez pas d’un plan Microsoft 365 entreprise E5 existant et que vous souhaitez essayer de gérer les risques internes, vous pouvez [Ajouter microsoft 365](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365) à votre abonnement Office 365 existant ou [vous inscrire pour obtenir une version d’évaluation](https://www.microsoft.com/microsoft-365/enterprise) de Microsoft 365 entreprise E5.

Procédez comme suit pour configurer et utiliser la gestion des risques initiés dans votre organisation Microsoft 365 :

## <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Étape 1 (obligatoire) : activer les autorisations pour la gestion des risques initiés

Il existe quatre rôles d’autorisation permettant de configurer et de gérer la gestion des risques initiés. Pour poursuivre ces étapes de configuration, vos administrateurs client doivent d’abord vous attribuer le rôle d' **administrateur de gestion des risques Insiders** .

| **Rôle** | **Autorisations de rôle** |
| ---- | ---------------- |
| **Administrateur de gestion des risques des Insiders** | Créer, lire, mettre à jour et supprimer des stratégies de gestion des risques internes <br> Créer, lire, mettre à jour et supprimer des autorisations et des rôles de gestion des risques initiés |
| **Analystes de gestion des risques Insiders** | Accès à toutes les alertes, incidents et notifications de gestion des risques Insider |
| **Investigateurs de gestion des risques Insiders** | Accès à toutes les alertes, incidents, avis et Explorateur de contenu Insider dans tous les cas |
| **Visionneuse de gestion des risques Insiders** | Accès en lecture seule à toutes les alertes, incidents, avis et Explorateur de contenu Insider dans tous les cas |

En fonction de la structure de votre équipe de gestion de la conformité, vous disposez de deux options d’autorisation pour configurer les rôles afin de gérer les fonctionnalités de gestion des risques internes. Choisissez l’une des options de gestion des rôles suivantes lors de la configuration de la gestion des risques initiés :

1. **Utiliser le groupe de rôles de gestion des risques initié par défaut**: utilisez ce groupe de rôles pour gérer la gestion des risques initiés de votre organisation en ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes et enquêteurs désignés dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de gestion des risques Insider. Il s’agit de la méthode la plus simple pour démarrer rapidement avec la gestion des risques initiés et pour les organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts.
2. **Créez des groupes différents pour les différents rôles de gestion**: pour les organisations qui ont besoin d’autorisations distinctes pour la configuration et la gestion des risques initiés, vous devez créer des groupes de rôles et attribuer des rôles et des utilisateurs appropriés aux nouveaux groupes. Par exemple, si vous souhaitez des autorisations différentes pour l’analyse et l’analyse de la gestion des risques initiaux, vous devrez créer un groupe pour les analystes et un groupe distinct pour les investigateurs. Pour chaque groupe, vous devez attribuer les rôles requis pour ces responsabilités, puis ajouter les utilisateurs qui doivent être affectés au groupe.

Si vous décidez de configurer différents groupes pour différents rôles, utilisez le tableau suivant pour affecter les rôles requis à chaque groupe de rôles :

| **Exemple de groupe** | **Rôles requis** |
| ---- | ---------------- |
| **Administrateurs** | Rôle d' *administrateur de gestion des risques Insiders* |
| **Analystes** | Rôle des *analystes de gestion des risques Insiders* <br> Rôle de *gestion des cas* |
| **Investigations** | Rôle des *enquêteurs sur la gestion des risques Insiders* <br> Rôle de *gestion des cas* |

### <a name="option-1-add-users-to-the-insider-risk-management-role-group"></a>Option 1 : ajouter des utilisateurs au groupe de rôles de gestion des risques Insider

Si vous souhaitez utiliser un groupe de rôles pour tous les utilisateurs qui configurent et gèrent la gestion des risques initiés, procédez comme suit pour ajouter des utilisateurs au groupe de rôles de **gestion des risques initié** par défaut :

1. Connectez- [https://protection.office.com/permissions](https://protection.office.com/permissions) vous à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de sécurité et conformité Microsoft Office 365, accédez à **autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez le groupe de rôles *gestion des risques Insiders* , puis sélectionnez **modifier le groupe de rôles**.

4. Sélectionnez **choisir les membres** dans le volet de navigation de gauche, puis sélectionnez **modifier**.

5. Sélectionnez **Ajouter** , puis activez la case à cocher de tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Sélectionnez **Ajouter**, puis sélectionnez **Terminer**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles. Sélectionnez **Fermer** pour effectuer les étapes.

### <a name="option-2-create-a-new-role-group"></a>Option 2 : créer un groupe de rôles

Si vous devez créer des groupes de rôles distincts pour les différents rôles de gestion, procédez comme suit pour créer chaque nouveau groupe :

1. Connectez- [https://protection.office.com/permissions](https://protection.office.com/permissions) vous à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de sécurité et conformité Microsoft Office 365, accédez à **autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez **Créer**.

4. Dans le champ **nom** , attribuez un nom convivial au nouveau groupe de rôles. Sélectionnez **Suivant**.

5. Sélectionnez **choisir les rôles** , puis **Ajouter**. Activez la case à cocher pour les rôles que vous devez attribuer. Par exemple, si ce groupe est destiné aux analystes des risques des Insiders, sélectionnez le rôle *analystes de gestion des risques Insiders* et le rôle *gestion des cas* , puis sélectionnez **Ajouter** et **Terminer**. Sélectionnez **Suivant**.

6. Sélectionnez **choisir les membres** , puis **Ajouter**. Activez la case à cocher de tous les utilisateurs et groupes pour lesquels vous souhaitez créer des stratégies et gérer les messages avec des correspondances de stratégie, puis sélectionnez **Ajouter** et **Terminer**. Sélectionnez **Suivant**.

7. Sélectionnez **créer un groupe de rôles** à terminer.

Pour plus d’informations sur les groupes de rôles et les autorisations, consultez [la rubrique autorisations dans le centre de conformité](../security/office-365-security/protect-against-threats.md).

## <a name="step-2-optional-configure-the-microsoft-365-human-resources-data-connector"></a>Étape 2 (facultatif) : configurer le connecteur de données de ressources humaines Microsoft 365

La gestion des risques internes prend en charge l’importation des données d’utilisateur et de journal importées des plateformes de gestion des risques et de ressources humaines tierces. Le connecteur de données RH de Microsoft 365 vous permet d’extraire des données de ressources humaines à partir de fichiers CSV, y compris les dates de fin d’emploi et de fin de l’utilisateur. Ces données aident à piloter les indicateurs d’alerte dans les stratégies de gestion des risques internes et constituent un élément important de la configuration de la couverture de gestion des risques complète dans votre organisation.

Consultez la rubrique [configurer un connecteur pour importer des données RH](import-hr-data.md) pour obtenir des instructions détaillées sur la configuration du connecteur rh Microsoft 365 pour votre organisation. Une fois que vous avez configuré le connecteur RH, revenez à ces étapes de configuration.

>[!IMPORTANT]
>Si vous envisagez de configurer une stratégie à l’aide du modèle de vol de données pour les *employés qui fait partie* du, vous devez configurer le connecteur RH de sorte qu’il utilise les fonctionnalités de détection de signal complètes du modèle de stratégie. Si vous configurez plusieurs connecteurs RH pour votre organisation, la gestion des risques internes extrait automatiquement les indicateurs de tous les connecteurs RH.

## <a name="step-3-optional-configure-data-loss-prevention-dlp-policies"></a>Étape 3 (facultative) : configurer les stratégies de protection contre la perte de données (DLP)

La gestion des risques internes prend en charge l’utilisation des stratégies DLP pour identifier l’exposition intentionnelle ou accidentelle d’informations sensibles aux parties indésirables. Lors de la configuration d’une stratégie de gestion des risques inSided avec le modèle *fuites de données* , vous devez affecter une stratégie DLP spécifique à la stratégie. Cette stratégie permet de piloter les indicateurs d’alerte pour les informations sensibles est une partie importante de la configuration de la couverture complète de la gestion des risques dans votre organisation.

Consultez la rubrique [créer, tester et régler une stratégie DLP](create-test-tune-dlp-policy.md) pour obtenir des instructions détaillées sur la configuration des stratégies DLP pour votre organisation. Une fois que vous avez configuré une stratégie DLP, revenez à ces étapes de configuration.

>[!IMPORTANT]
>Si vous envisagez de configurer une stratégie à l’aide du modèle *fuites de données* , vous devez configurer au moins une stratégie DLP pour utiliser les fonctionnalités de détection de signal complètes du modèle de stratégie. Si vous configurez plusieurs stratégies DLP pour votre organisation, vous devez attribuer une stratégie de gestion des risques inSided par stratégie DLP.

## <a name="step-4-required-create-an-insider-risk-management-policy"></a>Étape 4 (obligatoire) : créer une stratégie de gestion des risques Insider

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
8. Sur la page **choisir les indicateurs d’alerte** , vous verrez les indicateurs inclus dans le modèle que vous avez choisi pour cette stratégie. Si vous avez sélectionné le modèle *fuites de données* au début de l’Assistant, vous devez sélectionner une stratégie DLP dans la liste déroulante **stratégie DLP** .
9. Sur la page **Sélectionner la fenêtre d’analyse** , vous définirez les conditions de la fenêtre de [surveillance](insider-risk-management-policies.md#monitoring-windows) pour la stratégie. Configurez les fenêtres de surveillance comme il convient.
10. Sélectionnez **suivant** pour continuer.
11. Sur la page **révision** , passez en revue les paramètres que vous avez choisis pour la stratégie. Sélectionnez **modifier** pour modifier les valeurs de la stratégie ou sélectionnez **Envoyer** pour créer et activer la stratégie.

Une fois que vous avez terminé ces étapes pour créer votre première stratégie de gestion des risques Insiders, vous commencerez à recevoir des alertes des indicateurs d’activité après environ 24 heures. Configurez des stratégies supplémentaires selon vos besoins à l’aide des instructions de l’étape 4 de cette rubrique ou des procédures décrites dans [Create a New Insider Risk Policy](insider-risk-management-policies.md#create-a-new-policy).
