---
title: Prise en main de la gestion des risques internes
description: Configurez la gestion des risques internes dans votre organisation.
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
ms.localizationpriority: medium
ms.service: O365-seccomp
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
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: ca858aaf10c453a3fa333288fd5e44c62d20cb08
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783906"
---
# <a name="get-started-with-insider-risk-management"></a>Prise en main de la gestion des risques internes

Utilisez des stratégies de gestion des risques internes pour identifier les activités à risque et les outils de gestion pour agir sur les alertes de risque dans votre organisation. Effectuez les étapes suivantes pour configurer les prérequis et configurer une stratégie de gestion des risques internes.

> [!IMPORTANT]
> La Microsoft 365 solution de gestion des risques internes fournit une option de niveau client pour aider les clients à faciliter la gouvernance interne au niveau de l’utilisateur. Les administrateurs au niveau du locataire peuvent configurer des autorisations pour fournir l’accès à cette solution aux membres de votre organisation et configurer des connecteurs de données dans le Centre de conformité Microsoft 365 pour importer les données pertinentes afin de prendre en charge l’identification au niveau utilisateur de l’activité potentiellement risquée. Les clients reconnaissent les insights liés au comportement, au caractère ou aux performances de l’utilisateur individuel en rapport avec l’emploi peuvent être calculés par l’administrateur et mis à la disposition d’autres membres de l’organisation. En outre, les clients reconnaissent qu’ils doivent mener leur propre enquête complète sur le comportement, le caractère ou les performances de l’utilisateur individuel en rapport avec l’emploi, et pas seulement s’appuyer sur les insights du service de gestion des risques internes. Les clients sont uniquement responsables de l’utilisation du Microsoft 365 service de gestion des risques internes et de toute fonctionnalité ou service associé conformément à toutes les lois applicables, y compris les lois relatives à l’identification des utilisateurs individuels et à toutes les actions de correction.

Pour plus d’informations sur la façon dont les stratégies de risque interne peuvent vous aider à gérer les risques au sein de votre organisation, consultez [la gestion des risques internes dans Microsoft 365](insider-risk-management.md).

## <a name="subscriptions-and-licensing"></a>Abonnements et licences

Avant de commencer à gérer les risques internes, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) et tous les modules complémentaires. Pour accéder à la gestion des risques internes et l’utiliser, votre organisation doit disposer de l’un des abonnements ou modules complémentaires suivants :

- abonnement Microsoft 365 E5/A5/F5/G5 (version payante ou d’évaluation)
- Microsoft 365 E3/A3/F3/G3 + le module complémentaire conformité Microsoft 365 E5/A5/F5/G5
- Microsoft 365 E3/A3/F3/G3 + le module complémentaire de gestion des risques internes Microsoft 365 E5/A5/F5/G5
- Abonnement Office 365 E3 + Enterprise Mobility and Security E3 + le module complémentaire Microsoft 365 E5 Conformité

L’une des licences ci-dessus doit être attribuée aux utilisateurs inclus dans les stratégies de gestion des risques internes.

> [!IMPORTANT]
> La gestion des risques internes est actuellement disponible dans les locataires hébergés dans des régions géographiques et des pays pris en charge par les dépendances du service Azure. Pour vérifier que la gestion des risques internes est prise en charge pour votre organisation, consultez [la disponibilité des dépendances Azure par pays/région](/troubleshoot/azure/general/dependency-availability-by-country).

Si vous n’avez pas de plan Microsoft 365 Entreprise E5 et que vous souhaitez essayer la gestion des risques internes, vous pouvez [ajouter Microsoft 365](/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou [vous inscrire à une version d’évaluation](https://www.microsoft.com/microsoft-365/enterprise) de Microsoft 365 Entreprise E5.

## <a name="recommended-actions-preview"></a>Actions recommandées (préversion)

Les actions recommandées peuvent aider votre organisation à se familiariser rapidement avec la gestion des risques internes. Incluses dans la page **Vue d’ensemble** , les actions recommandées vous guident tout au long des étapes de configuration et de déploiement des stratégies.

![Actions recommandées par la gestion des risques internes.](../media/insider-risk-recommended-actions.png)

Les recommandations suivantes sont disponibles pour vous aider à prendre en main ou à optimiser votre configuration de gestion des risques internes :

- **Activer l’audit** : lorsqu’elle est activée, l’activité utilisateur et administrateur dans votre organisation est enregistrée dans le journal d’audit Microsoft 365. Les stratégies de risque interne et les analyses analytiques utilisent ce journal pour détecter les activités à risque.
- **Obtenir des autorisations pour la gestion des risques utilisateur** : le niveau d’accès dont vous disposez aux fonctionnalités de gestion des risques internes dépend du groupe de rôles qui vous a été attribué. Pour accéder aux actions recommandées et les configurer, les utilisateurs doivent être affectés aux groupes de rôles *Insider Risk Management* ou *Insider Risk Management Admins* .
- **Choisissez des indicateurs de stratégie : les indicateurs** sont essentiellement les activités utilisateur que vous souhaitez détecter et examiner. Vous pouvez choisir des indicateurs pour suivre l’activité dans plusieurs Microsoft 365 emplacements et services.
- **Recherchez les risques potentiels internes** : exécutez une analyse analytique pour découvrir les risques internes potentiels qui se produisent dans votre organisation. Après avoir évalué les résultats, passez en revue les stratégies recommandées à configurer.
- **Attribuer des autorisations à d’autres** personnes : si d’autres membres de l’équipe seront responsables de la gestion des fonctionnalités à risque interne, vous devez les affecter aux groupes de rôles appropriés.
- **Créez votre première stratégie** : pour recevoir des alertes sur les activités potentiellement risquées, vous devez configurer des stratégies basées sur des modèles prédéfinis qui définissent les activités utilisateur que vous souhaitez détecter et examiner.

Chaque action recommandée incluse dans cette expérience a quatre attributs :

- **Action** : nom et description de l’action recommandée.
- **État** : état de l’action recommandée. Les valeurs *ne sont pas démarrées*, *en cours*, *enregistrées ultérieurement* ou *terminées*.
- **Obligatoire ou facultatif** : indique si l’action recommandée est requise ou facultative pour que les fonctionnalités de gestion des risques internes fonctionnent comme prévu.
- **Durée estimée :** durée estimée pour effectuer l’action recommandée en minutes.

Sélectionnez une recommandation dans la liste pour commencer à configurer la gestion des risques internes. Chaque action recommandée vous guide à travers les activités requises pour la recommandation, y compris les exigences, à quoi s'attendre et l'impact de la configuration de la fonctionnalité dans votre organisation.   Chaque action recommandée est automatiquement marquée comme terminée une fois configurée, ou vous devez sélectionner manuellement l’action comme terminée une fois configurée.

## <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Étape 1 (obligatoire) : Activer les autorisations pour la gestion des risques internes

> [!IMPORTANT]
> Après avoir configuré vos groupes de rôles, l’application des autorisations de groupe de rôles aux utilisateurs affectés au sein de votre organisation peut prendre jusqu’à 30 minutes.

Six groupes de rôles sont utilisés pour configurer les fonctionnalités de gestion des risques internes. Pour rendre **la gestion des risques Insider** disponible en tant qu’option de menu dans Centre de conformité Microsoft 365 et pour poursuivre ces étapes de configuration, vous devez être affecté à l’un des rôles ou groupes de rôles suivants :

- Azure Active Directory rôle [*d’administrateur général*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory rôle [*d’administrateur de conformité*](/azure/active-directory/roles/permissions-reference#compliance-administrator)
- groupe de rôles Centre de conformité Microsoft 365 [*Gestion de l’organisation*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- Centre de conformité Microsoft 365 groupe de [*rôles Administrateur de conformité*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- *Groupe de rôles Gestion des risques internes*
- *Groupe de rôles Administrateur de la gestion des risques internes*

Selon la façon dont vous souhaitez gérer les stratégies et alertes de gestion des risques internes, vous devez affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de gestion des risques internes. Vous avez la possibilité d’affecter des utilisateurs ayant des responsabilités de conformité différentes à des groupes de rôles spécifiques pour gérer différents domaines de fonctionnalités de gestion des risques internes. Vous pouvez également décider d’affecter tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et observateurs désignés au groupe de rôles Insider Risk Management. Utilisez un seul groupe de rôles ou plusieurs groupes de rôles pour répondre au mieux à vos exigences de gestion de la conformité.

Vous choisirez parmi ces options de groupe de rôles et actions de solution lorsque vous travaillez avec la gestion des risques internes :

|Actions|Gestion des risques internes|Administrateur de la gestion des risques internes|Analystes de la gestion des risque internes.|Enquêteurs de la gestion des risque internes.|Auditeurs de gestion des risques internes|
|---|---|---|---|---|---|
|Configurer des stratégies et des paramètres|Oui|Oui|Non|Non|Non|
|Access Analytics Insights|Oui|Oui|Oui|Non|Non|
|Accéder & examiner les alertes|Oui|Non|Oui|Oui|Non|
|Accès & examiner les cas|Oui|Non|Oui|Oui|Non|
|Accéder & afficher l’Explorateur de contenu|Oui|Non|Non|Oui|Non|
|Configurer des modèles d’avis|Oui|Non|Oui|Oui|Non|
|Afficher & exporter les journaux d’audit|Oui|Non|Non|Non|Oui|

> [!IMPORTANT]
> Assurez-vous d’avoir toujours au moins un utilisateur dans les groupes de rôles *Insider Risk Management* ou *Insider Risk Management Admin* (en fonction de l’option que vous choisissez) afin que votre configuration de gestion des risques internes n’accède pas à un scénario « zéro administrateur » si des utilisateurs spécifiques quittent votre organisation.

Les membres des rôles suivants peuvent affecter des utilisateurs à des groupes de rôles de gestion des risques internes et disposer des mêmes autorisations de solution que le groupe de rôles *Administrateur de la gestion des risques internes* :

- *administrateur général* Azure Active Directory
- *administrateur de conformité* Azure Active Directory
- *gestion de l’organisation* Centre de conformité Microsoft 365
- *administrateur de conformité* Centre de conformité Microsoft 365

> [!NOTE]
> Ces groupes de rôles ne sont actuellement pas pris en charge sur Privileged Identity Management (PIM). Pour en savoir plus sur PIM, consultez [Attribuer des rôles Azure AD dans Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-how-to-add-role-to-user).

### <a name="add-users-to-an-insider-risk-management-role-group"></a>Ajouter des utilisateurs à un groupe de rôles de gestion des risques internes

Effectuez les étapes suivantes pour ajouter des utilisateurs à un groupe de rôles de gestion des risques internes :

1. Connectez-vous [Centre de conformité Microsoft 365](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le Centre de conformité de sécurité &amp; , accédez à **Autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez le groupe de rôles de gestion des risques internes auquel vous souhaitez ajouter des utilisateurs, puis sélectionnez **Modifier le groupe de rôles**.

4. **Sélectionnez Choisir des membres** dans le volet de navigation gauche, puis sélectionnez **Modifier**.

5. Sélectionnez **Ajouter** , puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Sélectionnez **Ajouter**, puis **Terminé**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles. Sélectionnez **Fermer** pour effectuer les étapes.

## <a name="step-2-required-enable-the-microsoft-365-audit-log"></a>Étape 2 (obligatoire) : activer le journal d’audit Microsoft 365

La gestion des risques internes utilise Microsoft 365 journaux d’audit pour les insights utilisateur et les activités identifiés dans les stratégies et les insights analytiques. Les journaux d’audit Microsoft 365 sont un résumé de toutes les activités au sein de votre organisation et les stratégies de gestion des risques internes peuvent utiliser ces activités pour générer des insights de stratégie.

L'audit est activé par défaut pour les organisations Microsoft 365. Certaines organisations peuvent avoir désactivé l'audit pour des raisons spécifiques. Si l'audit est désactivé pour votre organisation, c'est peut-être parce qu'un autre administrateur l'a désactivé. Nous vous recommandons de confirmer que vous pouvez réactiver l'audit lorsque vous terminez cette étape.

Pour obtenir des instructions détaillées sur l'activation de l'audit, consultez [Activer ou désactiver la recherche dans le journal d'audit](turn-audit-log-search-on-or-off.md). Une fois l’audit activé, le message qui apparaît indique que le journal d’audit est en cours de préparation et que vous pourrez effectuer une recherche environ deux heures après la fin de la préparation. Vous n'avez à faire cette action qu'une seule fois. Pour plus d'informations sur l'utilisation du journal d'audit Microsoft 365, consultez [Rechercher dans le journal d'audit](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-enable-and-view-insider-risk-analytics-insights"></a>Étape 3 (facultatif) : activer et afficher les insights d’analyse des risques internes

L'analyse de la gestion des risques d'initiés vous permet d'effectuer une évaluation des risques d'initiés potentiels dans votre organisation sans configurer de politiques de risque d'initiés. Cette évaluation peut permettre à votre organisation d’identifier des zones potentielles plus élevées de risque utilisateur et vous aider à déterminer le type et l’étendue des stratégies de gestion des risques internes que vous pouvez envisager de configurer. Cette évaluation peut également vous aider à déterminer les besoins en matière de licences supplémentaires ou d’optimisation future des stratégies existantes. Les résultats de l'analyse analytique peuvent prendre jusqu'à 48 heures avant que les informations ne soient disponibles sous forme de rapports pour examen. Pour en savoir plus sur les insights analytiques, consultez [les paramètres de gestion des risques internes : Analytique](insider-risk-management-settings.md#analytics) et consultez la [vidéo Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) pour comprendre comment l’analytique peut aider à accélérer l’identification des risques internes potentiels et vous aider à prendre rapidement des mesures.

Pour activer l’analytique des risques internes, vous devez être membre du groupe de rôles *Insider Risk Management*, *Insider Risk Management Admin* ou Microsoft 365 *Global Admin*.

Effectuez les étapes suivantes pour activer l’analytique des risques internes :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **la gestion des risques internes**.
2. Sélectionnez **Exécuter l’analyse** dans l’onglet **Analyse des risques internes dans votre carte d’organisation** sous l’onglet **Vue d’ensemble** de la gestion des risques internes. Cette action active l’analyse analytique pour votre organisation. Vous pouvez également activer l’analyse dans votre organisation en accédant aux **paramètres** >  de risque **InsiderAnalytics** et en activant **Analyser l’activité utilisateur de votre locataire pour identifier les risques internes potentiels**.
3. Dans le volet **d’informations Analytics** , sélectionnez **Exécuter l’analyse pour démarrer l’analyse de votre organisation**. Les résultats de l'analyse analytique peuvent prendre jusqu'à 48 heures avant que les informations ne soient disponibles sous forme de rapports pour examen.

Après avoir examiné les insights analytiques, choisissez les stratégies de risque interne et configurez les conditions préalables associées qui répondent le mieux à la stratégie d’atténuation des risques internes de votre organisation.

## <a name="step-4-recommended-configure-prerequisites-for-policies"></a>Étape 4 (recommandé) : Configurer les prérequis pour les stratégies

La plupart des stratégies de gestion des risques internes ont des prérequis qui doivent être configurés pour que les indicateurs de stratégie génèrent des alertes d’activité pertinentes. Configurez les prérequis appropriés en fonction des stratégies que vous envisagez de configurer pour votre organisation.

### <a name="configure-microsoft-365-hr-connector"></a>Configurer Microsoft 365 connecteur RH

La gestion des risques internes prend en charge l’importation de données utilisateur et de journal importées à partir de plateformes tierces de gestion des risques et de ressources humaines. Le connecteur de données Microsoft 365 ressources humaines (RH) vous permet d’extraire des données de ressources humaines à partir de fichiers CSV, notamment les dates de fin d’emploi des utilisateurs, les dernières dates d’emploi, les notifications de plan d’amélioration des performances, les actions d’évaluation des performances et l’état des modifications au niveau du travail. Celles-ci permettent d’attirer l’attention sur les indicateurs d’alertes dans les stratégies de gestion des risques internes et il s’agit d’un élément essentiel de la configuration de la couverture de la gestion des risques. Si vous configurez plusieurs connecteurs RH pour votre organisation, la gestion des risques internes extrait automatiquement les indicateurs de tous les connecteurs RH.

Le connecteur RH Microsoft 365 est requis lors de l’utilisation des modèles de stratégie suivants :

- Fuites de données provoquées par un utilisateur mécontent
- Vol de données utilisateur sortant
- Utilisation incorrecte générale des données des patients
- Violations de stratégie de sécurité par des utilisateurs quittant l’entreprise
- Violations de stratégie de sécurité par des utilisateurs mécontents

Consultez l’article [Configurer un connecteur pour importer des données RH](import-hr-data.md) pour obtenir des instructions détaillées sur la configuration du connecteur RH Microsoft 365 pour votre organisation. Une fois que vous avez configuré le connecteur RH, revenez à ces étapes de configuration.

### <a name="configure--a-healthcare-specific-data-connector"></a>Configurer un connecteur de données spécifique aux soins de santé

La gestion des risques internes prend en charge l’importation de données utilisateur et de journal importées à partir de tiers sur des systèmes d’enregistrement médical électronique (EMR) existants. Les connecteurs de données Microsoft Healthcare et Epic vous permettent d’extraire des données d’activité de votre système EMR avec des fichiers CSV, notamment un accès incorrect aux enregistrements des patients, des activités de volume suspectes et des activités de modification et d’exportation. Celles-ci permettent d’attirer l’attention sur les indicateurs d’alertes dans les stratégies de gestion des risques internes et il s’agit d’un élément essentiel de la configuration de la couverture de la gestion des risques.

Si vous configurez plusieurs connecteurs Healthcare ou Epic pour votre organisation, la gestion des risques internes prend automatiquement en charge les signaux d’événements et d’activités de tous les connecteurs Healthcare et Epic.
Le connecteur Microsoft 365 Healthcare ou Epic est requis lors de l’utilisation des modèles de stratégie suivants :

- Utilisation incorrecte générale des données des patients

Consultez l’article [Configurer un connecteur pour importer des données de santé](import-healthcare-data.md) ou [configurer un connecteur pour importer des données d’ehr Epic](import-epic-data.md) pour obtenir des instructions détaillées sur la configuration d’un connecteur spécifique aux soins de santé pour votre organisation. Une fois que vous avez configuré un connecteur, revenez à ces étapes de configuration.

### <a name="configure-data-loss-prevention-dlp-policies"></a>Configurer des stratégies de protection contre la perte de données (DLP)

La gestion des risques internes prend en charge l’utilisation de stratégies DLP pour aider à identifier l’exposition intentionnelle ou accidentelle d’informations sensibles aux parties indésirables pour les alertes DLP de niveau de gravité élevé. Lors de la configuration d’une stratégie de gestion des risques internes avec l’un des modèles de **fuites de données** , vous avez la possibilité d’affecter une stratégie DLP spécifique à la stratégie pour ces types d’alertes.

Les stratégies DLP permettent d’identifier les utilisateurs pour activer le scoring des risques dans la gestion des risques internes pour les alertes DLP à gravité élevée pour les informations sensibles et constituent une partie importante de la configuration de la couverture complète de la gestion des risques dans votre organisation. Pour plus d’informations sur la gestion des risques internes et les considérations relatives à l’intégration et à la planification des stratégies DLP, consultez stratégies [de gestion des risques internes](insider-risk-management-policies.md#general-data-leaks).

> [!IMPORTANT]
>Vérifiez que vous avez terminé les opérations suivantes :
>
> - Vous comprenez et configurez correctement les utilisateurs dans l’étendue dans les stratégies de gestion des risques internes et DLP pour produire la couverture de stratégie attendue.
> - Vérifiez que le paramètre **Rapports d’incidents** dans la stratégie DLP pour la gestion des risques internes utilisé avec ces modèles est configuré pour les alertes de niveau de gravité *élevé* . Les alertes de gestion des risques internes ne seront pas générées à partir des stratégies DLP avec le champ **Rapports d’incidents** défini sur *Faible* ou *Moyen*.

Une stratégie DLP est facultative lors de l’utilisation des modèles de stratégie suivants :

- Fuites de données générales
- Fuites de données par des utilisateurs prioritaires

Consultez l’article [Créer, tester et paramétrer une stratégie DLP](create-test-tune-dlp-policy.md) pour obtenir des instructions pas à pas pour configurer des stratégies DLP pour votre organisation. Une fois que vous avez configuré une stratégie DLP, revenez à ces étapes de configuration.

### <a name="configure-priority-user-groups"></a>Configurer des groupes d’utilisateurs prioritaires

La gestion des risques internes inclut la prise en charge de l’affectation de groupes d’utilisateurs prioritaires à des stratégies pour aider à identifier des activités à risque uniques pour l’utilisateur ayant des positions critiques, des niveaux élevés de données et d’accès réseau, ou un historique passé du comportement à risque. La création d’un groupe d’utilisateurs prioritaire et l’affectation d’utilisateurs au groupe permettent d’étendre les stratégies aux circonstances uniques présentées par ces utilisateurs.

Un groupe d’utilisateurs prioritaire est requis lors de l’utilisation des modèles de stratégie suivants :

- Violations de la stratégie de sécurité par des utilisateurs prioritaires
- Fuites de données par des utilisateurs prioritaires

Consultez l’article [Sur la prise en main des paramètres de gestion des risques internes](insider-risk-management-settings.md#priority-user-groups-preview) pour obtenir des instructions pas à pas pour créer un groupe d’utilisateurs prioritaire. Une fois que vous avez configuré un groupe d’utilisateurs prioritaire, revenez à ces étapes de configuration.

### <a name="configure-physical-badging-connector-optional"></a>Configurer le connecteur de badging physique (facultatif)

La gestion des risques internes prend en charge l’importation de données utilisateur et de journal à partir de plateformes de contrôle physique et d’accès. Le connecteur de badging physique vous permet d’extraire des données d’accès à partir de fichiers JSON, notamment les ID utilisateur, les ID de point d’accès, l’heure et les dates d’accès, ainsi que l’état d’accès. Celles-ci permettent d’attirer l’attention sur les indicateurs d’alertes dans les stratégies de gestion des risques internes et il s’agit d’un élément essentiel de la configuration de la couverture de la gestion des risques. Si vous configurez plusieurs connecteurs de badging physique pour votre organisation, la gestion des risques internes extrait automatiquement les indicateurs de tous les connecteurs de badging physique. Les informations du connecteur de badging physique complètent d’autres signaux de risque interne lors de l’utilisation de tous les modèles de stratégie de risque interne.

> [!IMPORTANT]
> Pour que les stratégies de gestion des risques internes utilisent et corrélent les données de signal liées aux utilisateurs sortants et arrêtés avec les données d’événement de vos plateformes de contrôle physique et d’accès, vous devez également configurer le connecteur rh Microsoft 365. Si vous activez le connecteur de badging physique sans activer le connecteur rh Microsoft 365, les stratégies de gestion des risques internes traitent uniquement les événements d’accès physique non autorisé pour les utilisateurs de votre organisation.

Consultez l’article [Configurer un connecteur pour importer des données de badging physiques](import-physical-badging-data.md) pour obtenir des instructions pas à pas pour configurer le connecteur de badging physique pour votre organisation. Une fois que vous avez configuré le connecteur, revenez à ces étapes de configuration.

### <a name="configure-microsoft-defender-for-endpoint-optional"></a>Configurer Microsoft Defender pour point de terminaison (facultatif)

[Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) est une plateforme de sécurité de point de terminaison d’entreprise conçue pour aider les réseaux d’entreprise à prévenir, détecter, examiner et répondre aux menaces avancées. Pour avoir une meilleure visibilité des violations de sécurité dans votre organisation, vous pouvez importer et filtrer les alertes Defender pour point de terminaison pour les activités utilisées dans les stratégies créées à partir de modèles de stratégie de violation de sécurité de gestion des risques internes.

Si vous créez des stratégies de violation de la sécurité, vous devez avoir Microsoft Defender pour point de terminaison configurés dans votre organisation et activer Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Defender pour importer des alertes de violation de sécurité. Pour plus d’informations sur les exigences, consultez les [conditions minimales requises pour Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements) article.

Consultez l’article [Configurer les fonctionnalités avancées dans l’article Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center) pour obtenir des conseils pas à pas sur la configuration de Defender pour point de terminaison pour l’intégration de la gestion des risques internes. Une fois que vous avez configuré le Microsoft Defender pour point de terminaison, revenez à ces étapes de configuration.

## <a name="step-5-required-configure-insider-risk-settings"></a>Étape 5 (obligatoire) : Configurer les paramètres de risque interne

[Les paramètres de risque interne s’appliquent](insider-risk-management-settings.md) à toutes les stratégies de gestion des risques internes, quel que soit le modèle que vous avez choisi lors de la création d’une stratégie. Les paramètres sont configurés à l’aide des **Paramètres de risque internes** contrôle situés en haut de tous les onglets de gestion des risques internes. Ces paramètres contrôlent la confidentialité, les indicateurs, la surveillance de fenêtres et les détections intelligentes.

Avant de configurer une stratégie, définissez les paramètres de risque interne suivants :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **la gestion des risques internes** et sélectionnez **les paramètres de risque Insider** dans le coin supérieur droit de n’importe quelle page.
2. Dans la page **Confidentialité** , sélectionnez un paramètre de confidentialité pour afficher les noms d’utilisateur des alertes de stratégie.
3. Dans la page **Indicateurs** , sélectionnez les indicateurs d’alerte que vous souhaitez appliquer à toutes les stratégies de risque interne.

    > [!IMPORTANT]
    > Pour recevoir des alertes pour l’activité risquée définie dans vos stratégies, vous devez sélectionner un ou plusieurs indicateurs. Si les indicateurs ne sont pas configurés dans Paramètres, les indicateurs ne seront pas sélectionnables dans les stratégies de risque interne.

4. Dans la page **Périodes** de stratégie, sélectionnez les [périodes](insider-risk-management-settings.md#policy-timeframes) de stratégie à mettre en vigueur pour un utilisateur lorsqu’il déclenche une correspondance pour une stratégie de risque interne.
5. Dans la page **Détections intelligentes** , configurez les paramètres suivants pour les stratégies de risque interne :
    - [Exclusions de type de fichier](insider-risk-management-settings.md#file-type-exclusions)
    - [Nombre minimal d’événements quotidiens pour améliorer le score pour une activité inhabituelle](insider-risk-management-settings.md#minimum-number-of-daily-events-to-boost-score-for-unusual-activity)
    - [Niveau de volume d’alerte](insider-risk-management-settings.md#alert-volume)
    - [état de l’alerte Microsoft Defender pour point de terminaison](insider-risk-management-settings.md#microsoft-defender-for-endpoint-preview)
    - [Paramètres de domaine](insider-risk-management-settings.md#domains)
6. Dans la page **Exporter les alertes**, activez l’exportation des informations d’alerte de risque interne à l’aide des API de gestion Office 365 si nécessaire.
7. Dans la page **Groupes d’utilisateurs Priorité** , créez un groupe d’utilisateurs prioritaire et ajoutez des utilisateurs s’ils ne sont pas créés à **l’étape 3**.
8. Dans la page **Power Automate flux**, configurez un flux à partir de modèles de flux à risque interne ou créez un flux. Consultez l’article [Sur la prise en main des paramètres de gestion des risques internes](insider-risk-management-settings.md#power-automate-flows-preview) pour obtenir des conseils pas à pas.
9. Dans la **page Ressources prioritaires**, configurez les ressources de priorité pour utiliser les données de votre plateforme de contrôle physique et d’accès importées par le connecteur de badging physique. Consultez l’article [Sur la prise en main des paramètres de gestion des risques internes](insider-risk-management-settings.md#priority-physical-assets-preview) pour obtenir des conseils pas à pas.
10. Dans la page **Microsoft Teams**, activez Microsoft Teams intégration à la gestion des risques internes pour créer automatiquement une équipe pour la collaboration des cas ou des utilisateurs. Consultez l’article [Sur la prise en main des paramètres de gestion des risques internes](insider-risk-management-settings.md#microsoft-teams-preview) pour obtenir des conseils pas à pas.
11. Sélectionnez **Enregistrer** pour activer ces paramètres pour vos stratégies de risque interne.

## <a name="step-6-required-create-an-insider-risk-management-policy"></a>Étape 6 (obligatoire) : Créer une stratégie de gestion des risques internes

Les stratégies de gestion des risques internes incluent les utilisateurs attribués et définissent quels types d’indicateurs de risque sont configurés pour les alertes. Pour que les activités puissent déclencher des alertes, une stratégie doit être configurée. Utilisez l’Assistant Stratégie pour créer de nouvelles stratégies de gestion des risques internes.

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **Gestion des risques internes**, puis sélectionnez l’onglet **Stratégies**.
2. Sélectionnez **Créer une stratégie** pour ouvrir l’Assistant stratégie.
3. Sur la page **Modèle de stratégie**, choisissez une catégorie de stratégie, puis sélectionnez le modèle pour la nouvelle stratégie. Ces modèles sont constitués d'indicateurs et de conditions définissant les activités à risque que vous voulez détecter et examiner. Examinez les conditions préalables du modèle, les événements déclencheurs et les activités détectées pour confirmer que ce modèle de stratégie correspond à vos besoins.

    > [!IMPORTANT]
    > Certains modèles de stratégie ont des conditions préalables devant être configurées pour que la stratégie génère des alertes pertinentes. Si vous n’avez pas configuré les conditions préalables applicables de la stratégie, consultez **Étape 4** ci-dessus.

4. Sélectionnez **Suivant** pour continuer.
5. Dans la page **Nom et description**, complétez les champs suivants :
    - **Nom (obligatoire)** : entrez un nom convivial pour la stratégie. Ce nom ne peut pas être modifié après la création de la stratégie.
    - **Description (facultatif)** : entrez une description pour la stratégie.

6. Sélectionnez **Suivant** pour continuer.
7. Sur la page **Utilisateurs et groupes**, sélectionnez **Inclure tous les utilisateurs et groupes** ou **Inclure des utilisateurs et groupes spécifiques** pour définir les utilisateurs ou groupes inclus dans la stratégie ou, si vous avez choisir un modèle basé sur les utilisateurs prioritaires, sélectionnez **Ajouter ou modifier des groupes d’utilisateurs prioritaires**. La sélection de **Inclure tous les utilisateurs et groupes** permettra de rechercher les événements déclencheurs pour tous les utilisateurs et groupes dans votre organisation pour commencer à établir des scores de risque pour la stratégie. La sélection de **Inclure des utilisateurs et groupes spécifiques** vous permettra de définir les utilisateurs et groupes à affecter à la stratégie. Les comptes d’utilisateur invité ne sont pas pris en charge.
8. Sélectionnez **Suivant** pour continuer.
9. Sur la page **Contenu à prioriser**, vous pouvez attribuer (le cas échéant) les sources à hiérarchiser, ce qui augmente les possibilités de générer une alerte de gravité élevée pour ces sources. Sélectionnez l'une des options suivantes :

    - **Je veux indiquer des sites SharePoint, étiquettes de confidentialité et/ou des types d’information sensible comme contenu prioritaire**. La sélection de cette option active les pages détaillées dans l’Assistant pour configurer ces canaux.
    - **Je ne souhaite pas indiquer de contenu prioritaire pour le moment (vous pourrez le faire après la création de la stratégie)**. La sélection de cette option permettra d’ignorer les pages détaillées du canal dans l’Assistant.

10. Sélectionnez **Suivant** pour continuer.

11. Si vous avez sélectionné **je souhaite spécifier SharePoint sites, étiquettes de confidentialité et/ou types d’informations sensibles comme contenu prioritaire** à l’étape précédente, vous verrez les pages de détails pour *les sites SharePoint*, les *types d’informations sensibles* et *les étiquettes de confidentialité*. Utilisez ces pages détaillées pour définir les sites SharePoint, les types d’information sensible et les étiquettes de confidentialité à hiérarchiser dans la stratégie.

    - **Sites SharePoint** : sélectionnez **Ajouter un site SharePoint**, puis sélectionnez les sites SharePoint auxquels vous avez accès et que vous souhaitez classer. Par exemple, *« groupe1@contoso.sharepoint.com/sites/group1 »*.
    - **Type d’information sensible** : sélectionnez **Ajouter un type d’information confidentielle**, puis les types de confidentialité que vous souhaitez classer. Par exemple, *« Numéro de compte bancaire américain »* et *« Numéro de carte de crédit »*.
    - **Étiquette de confidentialité** : sélectionnez **Ajouter une étiquette de confidentialité**, puis les étiquettes que vous souhaitez classer. Par exemple, *« Confidentiel »* et *« Secret »*.

    > [!NOTE]
    > Les utilisateurs qui configurent la stratégie et qui sélectionnent des sites de point de partage prioritaires peuvent sélectionner SharePoint sites auxquels ils ont l’autorisation d’accéder. Si SharePoint sites ne sont pas disponibles pour la sélection dans la stratégie par l’utilisateur actuel, un autre utilisateur disposant des autorisations requises peut sélectionner les sites de la stratégie ultérieurement ou l’utilisateur actuel doit avoir accès aux sites requis.

12. Sélectionnez **Suivant** pour continuer.
13. Si vous avez sélectionné les *fuites de données générales ou les fuites* de *données par des modèles d’utilisateurs prioritaires* , vous verrez des options sur les **déclencheurs** de cette page de stratégie pour les événements de déclenchement personnalisé et les indicateurs de stratégie. Vous avez le choix de sélectionner une stratégie ou des indicateurs DLP pour déclencher des événements qui amènent les utilisateurs affectés à la stratégie dans l’étendue pour le scoring d’activité. Si vous sélectionnez **l’option d’événement de déclenchement de stratégie de protection contre la perte de données (DLP),** vous devez sélectionner une stratégie DLP dans la liste déroulante de la stratégie DLP pour activer les indicateurs de déclenchement de la stratégie DLP pour cette stratégie de gestion des risques internes. Si vous sélectionnez **l’utilisateur exécute une option d’événement de déclenchement d’activité d’exfiltration** , vous devez sélectionner un ou plusieurs des indicateurs répertoriés pour l’événement de déclenchement de stratégie.

    > [!IMPORTANT]
    > Si vous ne parvenez pas à sélectionner un indicateur répertorié, c’est qu’il n’est pas activé pour votre organisation. Pour les rendre disponibles pour la sélection et l’affectation à la stratégie, activez les indicateurs dans **la gestion des** >  risques **internes Paramètres** >  **Les indicateurs de stratégie**.

    Si vous avez sélectionné d’autres modèles de stratégie, les événements de déclenchement personnalisés ne sont pas pris en charge. Les événements de déclenchement de stratégie intégrés s’appliquent et vous passez à l’étape 23 sans définir d’attributs de stratégie.

14. Sélectionnez **Suivant** pour continuer.
15. Si vous avez sélectionné les *fuites de données générales ou les fuites* de *données par des modèles d’utilisateurs prioritaires* et que vous avez sélectionné l’utilisateur **effectue une activité d’exfiltration et les indicateurs associés**, vous pouvez choisir des seuils personnalisés ou par défaut pour l’indicateur déclenchant les événements que vous avez sélectionnés. Choisissez les **seuils d’utilisation par défaut (recommandés)** ou **utilisez des seuils personnalisés pour les événements déclencheurs**.
16. Sélectionnez **Suivant** pour continuer.
17. Si vous avez sélectionné **Utiliser des seuils personnalisés pour les événements de déclenchement**, pour chaque indicateur d’événement de déclenchement que vous avez sélectionné à l’étape 13, choisissez le niveau approprié pour générer le niveau souhaité d’alertes d’activité.
18. Sélectionnez **Suivant** pour continuer.
19. Dans la page **Indicateurs** de stratégie, vous verrez [les indicateurs](insider-risk-management-settings.md#indicators) que vous avez définis comme étant disponibles dans la page **Paramètres** >  **du** risque Insider. Sélectionnez les indicateurs que vous souhaitez appliquer à la stratégie.

    > [!IMPORTANT]
    > Si les indicateurs sur cette page ne peuvent pas être sélectionnés, vous sélectionner les indicateurs que vous souhaitez activer pour toutes les stratégies. Vous pouvez utiliser le bouton **Activer les indicateurs** dans l’Assistant ou sélectionner des indicateurs sur la page **Gestion des risques internes** > **Paramètres** > **Indicateurs de stratégie**.

    Si vous avez sélectionné au moins un indicateur *Office* ou *Appareil*, choisissez les **Boosters de score de risque** selon le cas. Les boosters de score de risque sont uniquement applicables pour les indicateurs sélectionnés.
    Si vous avez sélectionné un modèle de stratégie *Vol de données* ou *Fuites de données*, choisissez au moins une des méthodes **Détection de séquence** et une méthode **Détection d’exfiltration cumulée** à appliquer à la stratégie.

20. Sélectionnez **Suivant** pour continuer.
21. Dans la page **Décider d’utiliser des seuils d’indicateurs par défaut ou personnalisés** , choisissez des seuils personnalisés ou par défaut pour les indicateurs de stratégie que vous avez sélectionnés. Choisissez les **seuils d’utilisation par défaut pour tous les indicateurs** ou **spécifiez des seuils personnalisés** pour les indicateurs de stratégie sélectionnés. Si vous avez sélectionné Spécifier des seuils personnalisés, choisissez le niveau approprié pour générer le niveau d’alertes d’activité souhaité pour chaque indicateur de stratégie.
22. Sélectionnez **Suivant** pour continuer.
23. Sur la page **Évaluation**, examinez les paramètres choisis pour la stratégie et toute suggestion ou tout avertissement pour vos sélections. Sélectionnez **Modifier** pour changer toute valeur de stratégie ou **Soumettre** pour créer et activer la stratégie.

## <a name="next-steps"></a>Prochaines étapes

Une fois que vous avez effectué ces étapes pour créer votre première stratégie de gestion des risques internes, vous commencerez à recevoir des alertes à partir d’indicateurs d’activité après environ 24 heures. Configurez des stratégies supplémentaires en fonction des besoins à l’aide des conseils de l’étape 4 de cet article ou des étapes de [la création d’une stratégie de risque interne](insider-risk-management-policies.md#create-a-new-policy).

Pour en savoir plus sur l’examen des alertes à risque interne et du **tableau de bord Alertes**, consultez [les activités de gestion des risques internes](insider-risk-management-activities.md#alert-dashboard).
