---
title: Prise en main de la gestion des risques internes
description: Configurez la gestion des risques internes dans votre organisation.
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.openlocfilehash: 108f086af014c4f634e321f2e84e112db2032f17
ms.sourcegitcommit: a62ac3c01ba700a51b78a647e2301f27ac437c5a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50233306"
---
# <a name="get-started-with-insider-risk-management"></a>Prise en main de la gestion des risques internes

Utilisez les stratégies de gestion des risques internes pour identifier les activités à risque et les outils de gestion pour agir sur les alertes de risque dans votre organisation. Pour configurer les conditions préalables et une stratégie de gestion des risques internes, complétez les étapes suivantes.

>[!IMPORTANT]
>La solution de gestion des risques internes Microsoft 365 fournit une option au niveau du client pour aider les clients à faciliter la gouvernance interne au niveau de l’utilisateur. Les administrateurs au niveau du client peuvent configurer des autorisations pour fournir l’accès à cette solution aux membres de votre organisation et configurer des connecteurs de données dans le Centre de conformité Microsoft 365 pour importer les données pertinentes afin de prendre en charge l’identification au niveau de l’utilisateur de l’activité potentiellement risquée. Les clients reconnaissent que les informations liées au comportement, au caractère ou aux performances matériellement liés à l’emploi de l’utilisateur individuel peuvent être calculées par l’administrateur et rendues accessibles à d’autres membres de l’organisation. En outre, les clients reconnaissent qu’ils doivent mener leur propre examen complet lié au comportement, au caractère ou aux performances de l’utilisateur individuel matériellement liés à l’emploi, et non seulement s’appuyer sur les informations du service de gestion des risques internes. Les clients sont uniquement responsables de l’utilisation du service de gestion des risques internes de Microsoft 365, ainsi que de toute fonctionnalité ou service associé conformément à toutes les lois applicables, y compris les lois relatives à l’identification d’un utilisateur individuel et aux mesures correctives.

Pour plus d’informations sur la façon dont les stratégies de risque internes peuvent vous aider à gérer les risques au niveau de votre organisation, consultez La gestion des risques internes [dans Microsoft 365.](insider-risk-management.md)

## <a name="subscriptions-and-licensing"></a>Abonnements et licences

Avant de commencer à gérer les risques internes, vous devez confirmer votre abonnement [Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) et les modules. Pour accéder à la gestion des risques internes et l’utiliser, votre organisation doit avoir l’un des abonnements ou modules suivants :

- Abonnement Microsoft 365 E5 (version payante ou d’essai)
- Abonnement Microsoft 365 E3 + module de conformité Microsoft 365 E5
- Abonnement Microsoft 365 E3 + module de gestion des risques internes Microsoft 365 E5
- Abonnement Microsoft 365 A5 (version payante ou d’essai)
- Abonnement Microsoft 365 A3 + module de conformité Microsoft 365 A5
- Abonnement Microsoft 365 A3 + module de gestion des risques internes Microsoft 365 A5
- Abonnement Microsoft 365 G5 (version payante ou d’essai)
- Abonnement Microsoft 365 G3 + module de conformité Microsoft 365 G5
- Abonnement Microsoft 365 G3 + module de gestion des risques internes Microsoft 365 G5
- Abonnement Office 365 E3 + Enterprise Mobility and Security E3 + module de conformité Microsoft 365 E5

L’une des licences ci-dessus doit être attribuée aux utilisateurs inclus dans les stratégies de gestion des risques internes.

Si vous n’avez pas d’offre Microsoft 365 Entreprise E5 existante et que vous souhaitez essayer la [](https://www.microsoft.com/microsoft-365/enterprise) gestion des risques internes, vous pouvez ajouter [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou vous inscrire à une version d’évaluation de Microsoft 365 Entreprise E5.

## <a name="step-1-enable-permissions-for-insider-risk-management"></a>Étape 1 : Activer les autorisations pour la gestion des risques internes

>[!Important]
>Après avoir configuré vos groupes de rôles, l’application des autorisations de groupe de rôles aux utilisateurs affectés au sein de votre organisation peut prendre jusqu’à 30 minutes.

Quatre groupes de rôles sont utilisés pour configurer des autorisations pour gérer les fonctionnalités de gestion des risques internes. Pour poursuivre ces étapes de configuration, vos administrateurs client doivent d’abord vous affecter au groupe de rôles Gestion des risques internes ou Administrateur de la gestion **des** risques internes.  Pour accéder aux fonctionnalités de gestion des risques internes et les gérer après la configuration initiale, les utilisateurs doivent être membres d’au moins un groupe de rôles de gestion des risques internes.

Selon la structure de votre équipe de gestion de la conformité, vous avez la choix d’affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de gestion des risques internes. Choisissez parmi ces options de groupe de rôles lors de la configuration de la gestion des risques internes :

| **Groupe de rôles** | **Autorisations de rôle** |
| :---- | :---------------- |
| **Gestion des risques internes** | Ce groupe de rôles permet de gérer la gestion des risques internes pour votre organisation au sein d’un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes et enquêteurs désignés, vous pouvez définir des autorisations de gestion des risques internes dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de gestion des risques internes. Cette configuration est le moyen le plus simple de se lancer rapidement dans la gestion des risques internes et convient parfaitement aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts.|
| **Administrateur de la gestion des risques internes** | Utilisez ce groupe de rôles pour configurer initialement la gestion des risques internes, puis pour séparer les administrateurs de risques internes dans un groupe défini.  Les utilisateurs de ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de gestion des risques internes, des paramètres globaux et des affectations de groupe de rôles. |
| **Analystes de la gestion des risques internes.** | Utilisez ce groupe pour affecter des autorisations aux utilisateurs qui agiront comme des analystes de cas de risque internes. Les utilisateurs de ce groupe de rôles peuvent accéder à tous les modèles d’alertes, de cas et de notifications de gestion des risques internes. Ils ne peuvent pas accéder à l’Explorateur de contenu de risques internes. |
| **Enquêteurs sur la gestion des risques internes.** | Utilisez ce groupe pour affecter des autorisations aux utilisateurs qui agiront comme des enquêteurs de données de risque internes. Les utilisateurs de ce groupe de rôles peuvent accéder à toutes les alertes de gestion des risques internes, cas, modèles de notifications et l’Explorateur de contenu. |

> [!NOTE]
> Ces groupes de rôles ne sont actuellement pas pris en charge sur Privileged Identity Management (PIM). Pour en savoir plus sur PIM, voir [Attribuer des rôles Azure AD dans Privileged Identity Management.](/azure/active-directory/privileged-identity-management/pim-how-to-add-role-to-user)

### <a name="add-users-to-an-insider-risk-management-role-group"></a>Ajouter des utilisateurs à un groupe de rôles de gestion des risques internes

Pour ajouter des utilisateurs à un groupe de rôles de gestion des risques internes, complétez les étapes suivantes :

1. Connectez-vous [https://protection.office.com/permissions](https://protection.office.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le Centre &amp; de conformité de sécurité, allez à **Autorisations.** Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez le groupe de rôles de gestion des risques internes à ajouter aux utilisateurs, puis **sélectionnez Modifier le groupe de rôles.**

4. Sélectionnez **Choisir des membres** dans le volet de navigation de gauche, puis sélectionnez **Modifier.**

5. Sélectionnez **Ajouter,** puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Sélectionnez **Ajouter**, puis **Terminé**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles. Sélectionnez **Fermer** pour effectuer les étapes.

## <a name="step-2-enable-the-audit-log"></a>Étape 2 : Activer le journal d’audit

La gestion des risques internes utilise les journaux d’audit pour les informations des utilisateurs et les activités configurées dans les stratégies. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie de gestion des risques internes ou chaque fois qu’une stratégie est modifiée.

Pour obtenir des instructions détaillées sur l’activer, voir Activer ou désactiver la recherche dans le journal [d’audit.](turn-audit-log-search-on-or-off.md) Une fois l’audit activé, le message qui apparaît indique que le journal d’audit est en cours de préparation et que vous pourrez effectuer une recherche environ deux heures après la fin de la préparation. Vous ne devez faire cette action qu’une seule fois. Pour plus d’informations sur l’utilisation du journal d’audit, voir [Rechercher dans le journal d’audit.](search-the-audit-log-in-security-and-compliance.md)

## <a name="step-3-configure-prerequisites-for-templates"></a>Étape 3 : Configurer les conditions préalables pour les modèles

La plupart des modèles de gestion des risques internes ont des conditions préalables qui doivent être configurées pour que les indicateurs de stratégie génèrent des alertes d’activité pertinentes. Configurez les conditions préalables appropriées en fonction des stratégies que vous prévoyez de configurer pour votre organisation.

### <a name="configure-microsoft-365-hr-connector"></a>Configurer le connecteur RH Microsoft 365

La gestion des risques internes prend en charge l’importation de données utilisateur et de journal importées à partir de plateformes tierces de gestion des risques et de ressources humaines. Le connecteur de données des ressources humaines (RH) Microsoft 365 vous permet d’archiver des données de ressources humaines à partir de fichiers CSV, y compris les dates de résiliation des utilisateurs, les dates de dernière embauche, les notifications du plan d’amélioration des performances, les actions d’évaluation des performances et l’état de modification du niveau de travail. Celles-ci permettent d’attirer l’attention sur les indicateurs d’alertes dans les stratégies de gestion des risques internes et il s’agit d’un élément essentiel de la configuration de la couverture de la gestion des risques. Si vous configurez plusieurs connecteurs RH pour votre organisation, la gestion des risques internes tirera automatiquement les indicateurs de tous les connecteurs RH.

Le connecteur Microsoft 365 HR est requis lors de l’utilisation des modèles de stratégie suivants :

- Vol de données utilisateur en partant
- Violations de la stratégie de sécurité par les utilisateurs qui quittent le site
- Violations de stratégie de sécurité par les utilisateurs non résusés
- Fuites de données par des utilisateurs non régrunts

Consultez [l’article](import-hr-data.md) Configurer un connecteur pour importer des données RH pour obtenir des instructions pas à pas pour configurer le connecteur RH Microsoft 365 pour votre organisation. Une fois que vous avez configuré le connecteur RH, revenir à ces étapes de configuration.

### <a name="configure-data-loss-prevention-dlp-policies"></a>Configurer des stratégies de protection contre la perte de données (DLP)

La gestion des risques internes prend en charge l’utilisation de stratégies DLP pour vous aider à identifier l’exposition intentionnelle ou accidentelle d’informations sensibles à des parties indésirables pour les alertes DLP de niveau de gravité élevé. Lorsque vous configurez une stratégie de gestion des risques internes avec l’un des modèles de **fuites** de données, vous devez affecter une stratégie DLP spécifique à la stratégie.

Les stratégies DLP aident à identifier les utilisateurs à activer le score de risque dans la gestion des risques internes pour les alertes DLP de gravité élevée pour les informations sensibles et sont un élément important de la configuration de la couverture de gestion des risques complète dans votre organisation. Pour plus d’informations sur la gestion des risques internes et les considérations sur l’intégration et la planification des stratégies DLP, voir [Stratégies de gestion des risques internes.](insider-risk-management-policies.md#general-data-leaks)

>[!IMPORTANT]
>Assurez-vous que vous avez terminé les travaux suivants :
>
>- Vous comprenez et configurez correctement les utilisateurs dans l’étendue dans les stratégies de gestion des risques internes et DLP pour produire la couverture de stratégie que vous attendez.
>- Assurez-vous que le paramètre Rapports d’incident dans la stratégie DLP  pour la gestion des risques internes utilisé avec ces modèles est configuré pour les alertes de niveau de gravité élevé.  Les alertes de gestion des risques internes ne seront pas générées à partir des stratégies DLP avec le champ Rapports **d’incidents** définie sur *Faible* ou *Moyen*.

Une stratégie DLP est requise lors de l’utilisation des modèles de stratégie suivants :

- Fuites de données générales
- Fuites de données par utilisateurs prioritaires

Consultez [l’article Créer, tester](create-test-tune-dlp-policy.md) et régler une stratégie DLP pour obtenir des instructions pas à pas pour configurer des stratégies DLP pour votre organisation. Une fois que vous avez configuré une stratégie DLP, revenir à ces étapes de configuration.

### <a name="configure-priority-user-groups"></a>Configurer des groupes d’utilisateurs prioritaires

La gestion des risques internes inclut la prise en charge de l’attribution de groupes d’utilisateurs prioritaires à des stratégies pour faciliter l’identité des activités à risque uniques pour les utilisateurs ayant des positions critiques, des niveaux élevés de données et d’accès au réseau, ou un historique passé de comportement à risque. La création d’un groupe d’utilisateurs prioritaire et l’affectation d’utilisateurs au groupe aident les stratégies d’étendue aux circonstances uniques présentées par ces utilisateurs.

Un groupe d’utilisateurs prioritaire est requis lors de l’utilisation des modèles de stratégie suivants :

- Violations de stratégie de sécurité par les utilisateurs prioritaires
- Fuites de données par utilisateurs prioritaires

Consultez [l’article](insider-risk-management-settings.md#priority-user-groups-preview) Prise en charge des paramètres de gestion des risques internes pour obtenir des instructions pas à pas pour créer un groupe d’utilisateurs prioritaire. Une fois que vous avez configuré un groupe d’utilisateurs prioritaire, revenir à ces étapes de configuration.

### <a name="configure-physical-badging-connector-optional"></a>Configurer le connecteur de badging physique (facultatif)

La gestion des risques internes prend en charge l’importation de données utilisateur et de journal importées à partir de plateformes de contrôle physique et d’accès. Le connecteur de badging physique vous permet d’obtenir des données d’accès à partir de fichiers JSON, y compris les ID d’utilisateur, les ID de point d’accès, les heures et les dates d’accès et l’état d’accès. Celles-ci permettent d’attirer l’attention sur les indicateurs d’alertes dans les stratégies de gestion des risques internes et il s’agit d’un élément essentiel de la configuration de la couverture de la gestion des risques. Si vous configurez plusieurs connecteurs de mauvaise gestion physique pour votre organisation, la gestion des risques internes tire automatiquement les indicateurs de tous les connecteurs de mauvaise gestion physiques. Les informations du connecteur de gestion des risques physiques complètent d’autres signaux de risque internes lors de l’utilisation de tous les modèles de stratégie de risque internes.

>[!IMPORTANT]
>Pour que les stratégies de gestion des risques internes utilisent et corrélent les données de signal liées aux utilisateurs qui quittent et se terminent par des données d’événement à partir de vos plateformes de contrôle physique et d’accès, vous devez également configurer le connecteur RH Microsoft 365. Si vous activez le connecteur de badging physique sans activer le connecteur RH Microsoft 365, les stratégies de gestion des risques internes ne traitera que les événements d’accès physique non autorisé pour les utilisateurs de votre organisation.

Consultez [l’article](import-physical-badging-data.md) Configurer un connecteur pour importer des données de badging physique pour obtenir des instructions pas à pas pour configurer le connecteur de badging physique pour votre organisation. Une fois que vous avez configuré le connecteur, revenir à ces étapes de configuration.

## <a name="step-4-configure-insider-risk-settings"></a>Étape 4 : Configurer les paramètres des risques internes

[Les paramètres de risque internes s’appliquent](insider-risk-management-settings.md) à toutes les stratégies de gestion des risques internes, quel que soit le modèle que vous avez choisi lors de la création d’une stratégie. Les paramètres sont configurés à l’aide des **Paramètres de risque internes** contrôle situés en haut de tous les onglets de gestion des risques internes. Ces paramètres contrôlent la confidentialité, les indicateurs, la surveillance de fenêtres et les détections intelligentes.

Avant de configurer une stratégie, définissez les paramètres de risque internes suivants :

1. Dans le Centre de conformité Microsoft  [365,](https://compliance.microsoft.com)sélectionnez Gestion des risques internes et sélectionnez **Paramètres** des risques internes dans le coin supérieur droit de n’importe quelle page.
2. Dans la page **Confidentialité,** sélectionnez un paramètre de confidentialité pour afficher les noms d’utilisateur des alertes de stratégie.
3. Dans la page Indicateurs, sélectionnez les indicateurs d’alerte que vous souhaitez appliquer à toutes les **stratégies** de risque internes.

    >[!IMPORTANT]
    >Pour recevoir des alertes pour les activités risquées définies dans vos stratégies, vous devez sélectionner un ou plusieurs indicateurs.

4. Dans la page Délais de [](insider-risk-management-settings.md#policy-timeframes) **stratégie,** sélectionnez les délais de stratégie à mettre en vigueur pour un utilisateur lorsqu’il déclenche une correspondance pour une stratégie de risque interne.
5. Dans la page **Détections intelligentes,** configurez les paramètres suivants pour les stratégies de risque internes :
    - [Détections d’anomalies](insider-risk-management-settings.md#anomaly-detections)
    - [Niveau de volume d’alerte](insider-risk-management-settings.md#alert-volume)
    - [État d’alerte de Microsoft Defender pour point de terminaison](insider-risk-management-settings.md#microsoft-defender-for-endpoint-preview)
    - [Paramètres de domaine](insider-risk-management-settings.md#domains-preview)
6. Dans la page **Exporter les alertes,** activez l’exportation des informations d’alerte de risque interne à l’aide des API de gestion d’Office 365 si nécessaire.
7. Dans la page **Groupes d’utilisateurs** prioritaires, créez un groupe d’utilisateurs prioritaire et ajoutez des utilisateurs si ce n’est pas le cas à l’étape **3.**
8. Dans la page **Flux Power Automate,** configurez un flux à partir de modèles de flux de risques internes ou créez un flux. Consultez [l’article Prise en](insider-risk-management-settings.md#power-automate-flows-preview) charge des paramètres de gestion des risques internes pour obtenir des instructions pas à pas.
9. Dans la **page Ressources** de priorité, configurez les ressources de priorité pour utiliser les données de votre plateforme de contrôle physique et d’accès importées par le connecteur de badging physique. Consultez [l’article Prise en](insider-risk-management-settings.md#priority-physical-assets-preview) charge des paramètres de gestion des risques internes pour obtenir des instructions pas à pas.
10. Dans la page **Microsoft Teams,** activez l’intégration de Microsoft Teams à la gestion des risques internes pour créer automatiquement une équipe pour la collaboration de cas ou d’utilisateurs. Consultez [l’article Prise en](insider-risk-management-settings.md#microsoft-teams-preview) charge des paramètres de gestion des risques internes pour obtenir des instructions pas à pas.
11. Sélectionnez **Enregistrer** pour activer ces paramètres pour vos stratégies de risque internes.

## <a name="step-5-create-an-insider-risk-management-policy"></a>Étape 5 : Créer une stratégie de gestion des risques internes

Les stratégies de gestion des risques internes incluent les utilisateurs attribués et définissent quels types d’indicateurs de risque sont configurés pour les alertes. Pour que les activités puissent déclencher des alertes, une stratégie doit être configurée.

1. Dans le Centre de conformité [Microsoft 365,](https://compliance.microsoft.com)allez à **La** gestion des risques internes et sélectionnez **l’onglet Stratégies.**
2. Sélectionnez **Créer une stratégie** pour ouvrir l’Assistant Stratégie.
3. Dans la page **Nouvelle stratégie de risque interne,** remplissez les champs suivants :
    - **Nom (obligatoire)**: entrez un nom convivial pour la stratégie.
    - **Description (facultative)**: entrez une description de la stratégie.
    - **Choisissez un modèle de stratégie (obligatoire)**: sélectionnez l’un des [modèles](insider-risk-management-policies.md#policy-templates) de stratégie pour définir les types d’indicateurs de risque surveillés par la stratégie.

    >[!IMPORTANT]
    >La plupart des modèles de stratégie ont des conditions préalables qui doivent être configurées pour que la stratégie génère des alertes pertinentes. Si vous n’avez pas configuré les conditions préalables applicables à la stratégie, consultez **l’étape 3** ci-dessus.

4. Sélectionnez **Suivant** pour continuer.
5. Dans la **page**  Utilisateurs, sélectionnez Ajouter un utilisateur ou un groupe ou Choisir des groupes d’utilisateurs prioritaires pour définir quels utilisateurs ou groupes d’utilisateurs prioritaires sont inclus dans la stratégie, en fonction du modèle de stratégie que vous avez sélectionné.  Activez **la case à cocher** Tous les utilisateurs et groupes à messagerie le cas échéant (si vous n’avez pas sélectionné de modèle basé sur l’utilisateur prioritaire). Sélectionnez **Suivant** pour continuer.
6. Dans la page Spécifier le contenu à hiérarchiser **(facultatif),** vous pouvez affecter les sources à hiérarchiser pour augmenter les scores de risque. Toutefois, certaines activités ne génèrent aucune alerte, sauf si le contenu associé contient des types d’informations sensibles intégrés ou personnalisés ou a été spécifié comme priorité sur cette page :
    - **Sites SharePoint**: sélectionnez Ajouter un **site SharePoint** et sélectionnez les organisations SharePoint que vous souhaitez hiérarchiser. Par exemple, *« group1@contoso.sharepoint.com/sites/group1*».
    - **Type d’informations sensibles**: sélectionnez Ajouter **un type d’informations sensibles** et sélectionnez les types de sensibilité que vous souhaitez hiérarchiser. Par exemple, *« Numéro de compte* bancaire américain » et « Numéro de carte de *crédit*».
    - **Étiquettes de sensibilité**: **sélectionnez Ajouter** une étiquette de sensibilité et sélectionnez les étiquettes que vous souhaitez hiérarchiser. Par exemple, *« Confidentiel »* et « *Secret*».
7. Sélectionnez **Suivant** pour continuer.
8. Dans **la** page Sélectionner des indicateurs de [](insider-risk-management-settings.md#indicators) stratégie, vous verrez les indicateurs que vous avez définis comme disponibles dans la page Indicateurs des **paramètres** de risque  >   internes. Si vous avez sélectionné un modèle de fuites de données au début de l’Assistant, vous devez sélectionner une stratégie DLP dans la liste de listes de listes des *stratégies* **DLP** pour activer les indicateurs de déclenchement de la stratégie. Sélectionnez les indicateurs que vous souhaitez appliquer à la stratégie. Si vous préférez ne pas utiliser les paramètres de seuil de stratégie par défaut pour ces indicateurs, désactivez les seuils par défaut recommandés par Microsoft et entrez les **valeurs** de seuil pour chaque indicateur sélectionné. Si vous avez sélectionné au moins un indicateur *Office* ou *Appareil,* sélectionnez le **score de risque** selon le cas. Les score de risque ne s’appliquent qu’aux indicateurs sélectionnés.

    >[!IMPORTANT]
    >Si les indicateurs de cette page ne peuvent pas être sélectionnés, vous devez sélectionner les indicateurs que vous souhaitez activer pour toutes les stratégies dans la page Indicateurs de stratégie des  >  **paramètres** de gestion des risques  >   internes.

9. Sélectionnez **Suivant** pour continuer.
10. Dans la page **Périodes** de la stratégie, vous verrez les conditions de la fenêtre [d’activation](insider-risk-management-settings.md#policy-timeframes) de la stratégie qui s’y trouverez dans la page Délais de stratégie des   >  **paramètres de** risque internes.
11. Sélectionnez **Suivant** pour continuer.
12. Dans **la** page Révision, examinez les paramètres que vous avez choisis pour la stratégie. Sélectionnez **Modifier** pour modifier l’une des valeurs de stratégie ou **sélectionnez Envoyer** pour créer et activer la stratégie.

## <a name="next-steps"></a>Étapes suivantes

Après avoir effectué ces étapes pour créer votre première stratégie de gestion des risques internes, vous commencerez à recevoir des alertes des indicateurs d’activité après environ 24 heures. Configurez des stratégies supplémentaires selon vos besoins à l’aide des instructions de l’étape 4 de cet article ou des étapes de création d’une stratégie de [risque interne.](insider-risk-management-policies.md#create-a-new-policy)

Pour en savoir plus sur l’examen des alertes de risques internes et du tableau de bord **Alertes,** consultez les alertes de gestion [des risques internes.](insider-risk-management-alerts.md)
