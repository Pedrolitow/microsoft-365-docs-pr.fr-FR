---
title: Prise en main de la gestion des risques internes
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
ms.openlocfilehash: c53bfa58e36b2723d5227c38805482dcb629d864
ms.sourcegitcommit: a08103bc120bdec7cfeaf67c1be4e221241e69ad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "45199688"
---
# <a name="get-started-with-insider-risk-management"></a>Prise en main de la gestion des risques internes

Utilisez des stratégies de gestion des risques internes pour identifier les activités à risque et les outils de gestion qui agissent sur les alertes de risque au sein de votre organisation. Procédez comme suit pour configurer les conditions préalables et configurer une stratégie de gestion des risques inSided.

>[!IMPORTANT]
>La solution de gestion des risques Microsoft 365 Insider offre une option de niveau client pour aider les clients à faciliter la gouvernance interne au niveau de l’utilisateur. Les administrateurs de niveau client peuvent configurer des autorisations pour permettre l’accès à cette solution pour les membres de votre organisation et configurer des connecteurs de données dans le centre de conformité Microsoft 365 afin d’importer des données pertinentes afin de prendre en charge l’identification des activités potentiellement dangereuses. Les clients reconnaissent les informations relatives au comportement, au caractère ou aux performances des utilisateurs individuels liés à l’emploi, peuvent être calculées par l’administrateur et mises à la disposition des autres membres de l’organisation.

Pour plus d’informations sur la façon dont les stratégies de risque d’initié peuvent vous aider à gérer les risques au sein de votre organisation, consultez la rubrique [gestion des risques internes dans Microsoft 365](insider-risk-management.md).

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer à gérer les risques initiaux, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) et tous les modules complémentaires. Pour accéder à la gestion des risques initiés et l’utiliser, votre organisation doit disposer de l’un des abonnements ou des modules complémentaires suivants :

- Abonnement Microsoft 365 E5 (payant ou version d’évaluation)
- Microsoft 365 E3 subscription + le complément de conformité Microsoft 365 E5
- Microsoft 365 E3 subscription + le complément de gestion des risques de Microsoft 365 E5 Insider
- Abonnement Microsoft 365 a5 (payant ou version d’évaluation)
- Abonnement Microsoft 365 a3 + complément Microsoft 365 a5 Compliance
- Abonnement Microsoft 365 a3 + complément de gestion des risques Microsoft 365 a5 Insider

Les utilisateurs inclus dans les stratégies de gestion des risques internes doivent disposer de l’une des licences ci-dessus.

Si vous ne disposez pas d’un plan Microsoft 365 entreprise E5 existant et que vous souhaitez essayer de gérer les risques internes, vous pouvez [Ajouter microsoft 365](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou [vous inscrire pour obtenir une version d’évaluation](https://www.microsoft.com/microsoft-365/enterprise) de Microsoft 365 entreprise E5.

## <a name="step-1-enable-permissions-for-insider-risk-management"></a>Étape 1 : activer les autorisations pour la gestion des risques initiés

Il existe quatre groupes de rôles utilisés pour configurer les autorisations permettant de gérer les fonctionnalités de gestion des risques inSided. Pour poursuivre ces étapes de configuration, vos administrateurs client doivent d’abord vous attribuer le groupe de rôles d’administrateur de gestion des **risques Insiders** ou d' **Insider Management** . Pour accéder et gérer les fonctionnalités de gestion des risques internes après la configuration initiale, les utilisateurs doivent être membres d’au moins un groupe de rôles de gestion des risques Insiders.

Selon la structure de votre équipe de gestion de la conformité, vous avez la choix d’affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de gestion des risques internes. Vous avez le choix entre ces options de groupe de rôles lors de la configuration de la gestion des risques initiés :

| **Groupe de rôles** | **Autorisations de rôle** |
| :---- | :---------------- |
| **Gestion des risques initiés** | Ce groupe de rôles permet de gérer la gestion des risques internes pour votre organisation au sein d’un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes et enquêteurs désignés, vous pouvez définir des autorisations de gestion des risques internes dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de gestion des risques internes. Cette configuration est la méthode la plus simple pour démarrer rapidement avec la gestion des risques initiés et pour les organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts.|
| **Administrateur de gestion des risques des Insiders** | Utilisez ce groupe de rôles pour configurer initialement la gestion des risques initiés et, par la suite, pour séparer les administrateurs des risques des Insiders en un groupe défini.  Les utilisateurs de ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de gestion des risques internes, des paramètres globaux et des affectations de groupe de rôles. |
| **Analystes de gestion des risques Insiders** | Utilisez ce groupe pour affecter des autorisations aux utilisateurs qui agiront comme des analystes de cas de risque internes. Les utilisateurs de ce groupe de rôles peuvent accéder aux modèles alertes, incidents et notifications de gestion des risques Insider. Ils ne peuvent pas accéder à l’Explorateur de contenu de risques internes. |
| **Investigateurs de gestion des risques Insiders** | Utilisez ce groupe pour affecter des autorisations aux utilisateurs qui agiront comme des enquêteurs de données de risque internes. Les utilisateurs de ce groupe de rôles peuvent accéder à toutes les alertes de gestion des risques Insider, les cas, les modèles de notifications et l’Explorateur de contenu dans tous les cas. |

### <a name="add-users-to-an-insider-risk-management-role-group"></a>Ajouter des utilisateurs à un groupe de rôles de gestion des risques Insider

Procédez comme suit pour ajouter des utilisateurs à un groupe de rôles de gestion des risques Insider :

1. Connectez-vous [https://protection.office.com/permissions](https://protection.office.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de sécurité &amp; conformité, accédez à **autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez le groupe de rôles Gestion des risques Insiders auquel vous souhaitez ajouter des utilisateurs, puis sélectionnez **modifier le groupe de rôles**.

4. Sélectionnez **choisir les membres** dans le volet de navigation de gauche, puis sélectionnez **modifier**.

5. Sélectionnez **Ajouter** , puis activez la case à cocher de tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Sélectionnez **Ajouter**, puis **Terminé**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles. Sélectionnez **Fermer** pour effectuer les étapes.

## <a name="step-2-enable-the-audit-log"></a>Étape 2 : activer le journal d’audit

La gestion des risques internes utilise les journaux d’audit pour les informations des utilisateurs et les activités configurées dans les stratégies. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie de gestion des risques inSided ou à chaque fois qu’une stratégie est modifiée.

Pour obtenir des instructions détaillées sur l’activation de l’audit, consultez la rubrique [activer ou désactiver la recherche dans le journal d’audit](turn-audit-log-search-on-or-off.md). Une fois l’audit activé, le message qui apparaît indique que le journal d’audit est en cours de préparation et que vous pourrez effectuer une recherche environ deux heures après la fin de la préparation. Vous n’avez besoin d’effectuer cette action qu’une seule fois. Pour plus d’informations sur l’utilisation du journal d’audit, consultez [la rubrique Search the audit log](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-configure-prerequisites-for-templates"></a>Étape 3 : configuration des conditions préalables pour les modèles

La plupart des modèles de gestion des risques Insiders comportent des éléments prérequis qui doivent être configurés pour que les indicateurs de stratégie génèrent des alertes d’activité pertinentes. Configurez les conditions préalables appropriées en fonction des stratégies que vous prévoyez de configurer pour votre organisation.

Si vous configurez une stratégie à l’aide du *langage offensant dans le modèle de stratégie de messagerie* , vous pouvez ignorer cette étape et passer directement à l' **étape 4**.

### <a name="configure-microsoft-365-hr-connector"></a>Configurer le connecteur RH de Microsoft 365

La gestion des risques internes prend en charge l’importation des données d’utilisateur et de journal importées des plateformes de gestion des risques et de ressources humaines tierces. Le connecteur de données RH de Microsoft 365 vous permet d’extraire des données de ressources humaines à partir de fichiers CSV, notamment les dates de fin d’utilisateur, les dates de dernière emploi, les notifications de plan d’amélioration des performances, les actions d’analyse des performances et l’état de modification du niveau des tâches. Celles-ci permettent d’attirer l’attention sur les indicateurs d’alertes dans les stratégies de gestion des risques internes et il s’agit d’un élément essentiel de la configuration de la couverture de la gestion des risques. Si vous configurez plusieurs connecteurs RH pour votre organisation, la gestion des risques internes extrait automatiquement les indicateurs de tous les connecteurs RH.
Le connecteur RH de Microsoft 365 est requis lors de l’utilisation des modèles de stratégie suivants :

- Défaition des vols de données utilisateur
- Violations de stratégie de sécurité en faisant départion des utilisateurs
- Violations de stratégie de sécurité par des utilisateurs mécontents
- Fuites de données par les utilisateurs mécontents

Consultez l’article [configurer un connecteur pour importer les données RH](import-hr-data.md) pour obtenir des instructions détaillées sur la configuration du connecteur rh Microsoft 365 pour votre organisation. Une fois que vous avez configuré le connecteur RH, revenez à ces étapes de configuration.

### <a name="configure-data-loss-prevention-dlp-policies"></a>Configurer les stratégies de protection contre la perte de données (DLP)

La gestion des risques initiés prend en charge l’utilisation des stratégies DLP pour identifier l’exposition intentionnelle ou accidentelle d’informations sensibles aux parties indésirables pour les alertes DLP à niveau de gravité élevé. Lors de la configuration d’une stratégie de gestion des risques inSided avec l’un des modèles de **fuite de données** , vous devez affecter une stratégie DLP spécifique à la stratégie.

Les stratégies DLP aident à identifier les utilisateurs à activer le score de risque en matière de gestion des risques initiés pour les alertes DLP de haute gravité pour les informations sensibles et constituent un élément important de la configuration de la couverture de la gestion des risques dans votre organisation. Pour plus d’informations sur la gestion des risques internes et les considérations relatives à l’intégration et à la planification des stratégies DLP, consultez la rubrique [stratégies de gestion des risques internes](insider-risk-management-policies.md#general-data-leaks).

>[!IMPORTANT]
>Assurez-vous que vous avez effectué les opérations suivantes :
>
>- Vous comprenez et configurez correctement les utilisateurs dans l’étendue dans les stratégies de gestion des risques DLP et Insider pour produire la couverture de stratégie que vous attendez.
>- Assurez-vous que le paramètre **rapports d’incident** de la stratégie DLP pour la gestion des risques des Insiders utilisés avec ces modèles est configuré pour des alertes de niveau de gravité *élevé* . Les alertes de gestion des risques internes ne seront pas générées à partir des stratégies DLP avec le champ **rapports d’incident** défini sur *faible* ou *moyen*.

Une stratégie DLP est requise lors de l’utilisation des modèles de stratégie suivants :

- Fuites de données générales
- Fuites de données par les utilisateurs prioritaires

Consultez l’article [créer, tester et ajuster une stratégie DLP](create-test-tune-dlp-policy.md) pour obtenir des instructions détaillées sur la configuration des stratégies DLP pour votre organisation. Une fois que vous avez configuré une stratégie DLP, revenez à ces étapes de configuration.

### <a name="configure-priority-user-groups"></a>Configurer les groupes d’utilisateurs prioritaires

La gestion des risques initiés comprend la prise en charge de l’affectation de groupes d’utilisateurs prioritaires aux stratégies afin d’aider à identifier les activités à risque unique pour les utilisateurs ayant des positions critiques, les niveaux élevés de données et l’accès au réseau, ou un historique des risques passés. La création d’un groupe d’utilisateurs prioritaire et l’affectation d’utilisateurs au groupe aident les stratégies d’étendue aux circonstances uniques présentées par ces utilisateurs.

Un groupe d’utilisateurs prioritaire est requis lors de l’utilisation des modèles de stratégie suivants :

- Violations de stratégie de sécurité par utilisateurs prioritaires 
- Fuites de données par les utilisateurs prioritaires

Pour obtenir des instructions détaillées sur la création d’un groupe d’utilisateurs prioritaire, voir l’article [Getting Started with insidest Management Settings](insider-risk-management-settings.md#priority-user-groups-preview) . Une fois que vous avez configuré un groupe d’utilisateurs de priorité, revenez à ces étapes de configuration.

## <a name="step-4-configure-insider-risk-settings"></a>Étape 4 : configurez les paramètres des risques internes

Les [paramètres des risques internes](insider-risk-management-settings.md) s’appliquent à toutes les stratégies de gestion des risques internes, quel que soit le modèle que vous avez choisi lors de la création d’une stratégie. Les paramètres sont configurés à l’aide des **Paramètres de risque internes** contrôle situés en haut de tous les onglets de gestion des risques internes. Ces paramètres contrôlent la confidentialité, les indicateurs, la surveillance de fenêtres et les détections intelligentes.

Avant de configurer une stratégie, définissez les paramètres de risque Insider suivants :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez **paramètres des risques Insiders** dans le coin supérieur droit de n’importe quelle page.
2. Sur la page **confidentialité** , sélectionnez un paramètre de confidentialité pour l’affichage des noms d’utilisateur pour les alertes de stratégie.
3. Sur la page **indicateurs** , sélectionnez les indicateurs d’alerte à appliquer à toutes les stratégies de risque pour les initiés.

    >[!IMPORTANT]
    >Pour recevoir des alertes relatives aux activités à risque définies dans vos stratégies, vous devez sélectionner un ou plusieurs indicateurs.

4. Dans la page périodes de la **stratégie** , sélectionnez les [périodes de stratégie](insider-risk-management-settings.md#policy-timeframes) à appliquer à un utilisateur lorsqu’il déclenche une correspondance pour une stratégie de risque initié par les utilisateurs.
5. Sur la page **détections intelligentes** , configurez les paramètres suivants pour les stratégies de risque pour les initiés :
    - [Détections d’anomalies](insider-risk-management-settings.md#anomaly-detections)
    - [Détections de langage choquant](insider-risk-management-settings.md#offensive-language-detections)
    - [Niveau du volume d’alerte](insider-risk-management-settings.md#alert-volume)
    - [État de l’alerte de protection avancée contre les menaces Microsoft 365 Defender](insider-risk-management-settings.md#microsoft-defender-advanced-threat-protection-preview)
    - [Paramètres de domaine](insider-risk-management-settings.md#domains-preview)
6. Sur la page **Exporter les alertes** , activez l’exportation des informations d’alerte sur les risques internes à l’aide des API de gestion d’Office 365 si nécessaire.
7. Dans la page **Priority User Groups** , créez un groupe d’utilisateurs de priorité et ajoutez des utilisateurs s’ils ne sont pas créés à l' **étape 3**.
8. Sélectionnez **Enregistrer** pour activer ces paramètres pour vos stratégies de risque Insider.

## <a name="step-5-create-an-insider-risk-management-policy"></a>Étape 5 : créer une stratégie de gestion des risques Insider

Les stratégies de gestion des risques internes incluent les utilisateurs attribués et définissent quels types d’indicateurs de risque sont configurés pour les alertes. Pour que les activités puissent déclencher des alertes, une stratégie doit être configurée.

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **stratégies** .
2. Sélectionnez **créer une stratégie** pour ouvrir l’Assistant stratégie.
3. Sur la page **nouvelle stratégie de risque Insider** , renseignez les champs suivants :
    - **Nom (obligatoire)**: entrez un nom convivial pour la stratégie.
    - **Description (facultatif)**: entrez une description pour la stratégie.
    - **Choisir un modèle de stratégie (obligatoire)**: sélectionnez un des [modèles de stratégie](insider-risk-management-policies.md#policy-templates) pour définir les types d’indicateurs de risque sont surveillés par la stratégie.

    >[!IMPORTANT]
    >La plupart des modèles de stratégie comportent des éléments prérequis qui doivent être configurés pour que la stratégie génère des alertes appropriées. Si vous n’avez pas configuré les prérequis de stratégie applicables, reportez-vous à l' **étape 3** ci-dessus.

4. Sélectionnez **suivant** pour continuer.
5. Dans la page **utilisateurs** , sélectionnez **Ajouter un utilisateur ou un groupe** ou **Choisissez Priority Group Groups** pour définir les utilisateurs ou groupes d’utilisateurs de priorité inclus dans la stratégie, en fonction du modèle de stratégie que vous avez sélectionné. Activez la case à cocher **tous les utilisateurs et les groupes à extension messagerie** , le cas échéant (si vous n’avez pas sélectionné de modèle de priorité basé sur l’utilisateur). Sélectionnez **suivant** pour continuer.
6. Sur la page **spécifier le contenu à classer par priorité (facultatif)** , vous pouvez attribuer les sources à hiérarchiser pour augmenter le score des risques. Toutefois, certaines activités ne génèrent pas d’alerte en tout lieu, sauf si le contenu associé contient des types d’informations sensibles intégrés ou personnalisés ou s’il a été spécifié comme priorité sur cette page :
    - **Sites SharePoint**: sélectionnez **Ajouter un site SharePoint** et sélectionnez les organisations SharePoint dont vous souhaitez définir la priorité. Par exemple, *« Group1@contoso.sharepoint.com/sites/group1 »*.
    - **Type d’informations sensibles**: sélectionnez **Ajouter un type d’informations sensibles** et sélectionnez les types de critère de diffusion dont vous souhaitez définir la priorité. Par exemple, *« numéro de compte bancaire américain »* et *« numéro de carte de crédit »*.
    - **Étiquettes de sensibilité**: sélectionnez **Ajouter une étiquette de confidentialité** et sélectionnez les étiquettes dont vous souhaitez définir la priorité. Par exemple, *« confidentiel »* et *« secret »*.
7. Sélectionnez **suivant** pour continuer.
8. Sur la page **Sélectionner les indicateurs de stratégie** , vous verrez les [indicateurs](insider-risk-management-settings.md#indicators) que vous avez définis comme étant disponibles sur la page indicateurs des paramètres de **risque Insider**  >  **Indicators** . Si vous avez sélectionné un modèle de *fuites de données* au début de l’Assistant, vous devez sélectionner une stratégie DLP dans la liste déroulante **stratégie DLP** pour activer le déclenchement des indicateurs pour la stratégie. Sélectionnez les indicateurs que vous souhaitez appliquer à la stratégie. Si vous préférez ne pas utiliser les paramètres de seuil de stratégie par défaut pour ces indicateurs, désactivez l’option **utiliser les seuils par défaut recommandés par Microsoft** et entrez les valeurs de seuil pour chaque indicateur sélectionné. Si vous avez sélectionné au moins un indicateur de *Bureau* ou d' *appareil* , sélectionnez les **suramplificateurs de score de risque** , le cas échéant. Les amplificateurs de score de risque ne s’appliquent qu’aux indicateurs sélectionnés.

    >[!IMPORTANT]
    >Si les indicateurs de cette page ne peuvent pas être sélectionnés, vous devrez sélectionner les indicateurs que vous souhaitez activer pour toutes les stratégies sur la page indicateurs de stratégie des paramètres de **gestion des risques inSided**  >  **Settings**  >  **Policy indicators** .

9. Sélectionnez **suivant** pour continuer.
10. Dans la page périodes de la **stratégie** , les conditions de la [fenêtre d’activation](insider-risk-management-settings.md#policy-timeframes) s’affichent pour la stratégie dans la page périodes de la stratégie des paramètres des **risques Insider**  >  **Policy timeframes** .
11. Sélectionnez **suivant** pour continuer.
12. Sur la page **révision** , passez en revue les paramètres que vous avez choisis pour la stratégie. Sélectionnez **modifier** pour modifier les valeurs de la stratégie ou sélectionnez **Envoyer** pour créer et activer la stratégie.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez terminé ces étapes pour créer votre première stratégie de gestion des risques Insiders, vous commencerez à recevoir des alertes des indicateurs d’activité après environ 24 heures. Configurez des stratégies supplémentaires selon vos besoins à l’aide des instructions de l’étape 4 de cet article ou des procédures décrites dans [Create a New Insider Risk Policy](insider-risk-management-policies.md#create-a-new-policy).

Pour en savoir plus sur l’analyse des alertes des risques internes et le **tableau de bord des alertes**, consultez la rubrique alertes de gestion des [risques internes](insider-risk-management-alerts.md).