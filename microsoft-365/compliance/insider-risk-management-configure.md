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
ms.openlocfilehash: cdd368e7e78458067b9f363d41f7931ac5a2c0cd
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754204"
---
# <a name="get-started-with-insider-risk-management"></a>Prise en main de la gestion des risques internes

Utilisez les stratégies de gestion des risques internes pour identifier les activités à risque et les outils de gestion pour agir sur les alertes de risque dans votre organisation. Pour configurer les conditions préalables et une stratégie de gestion des risques internes, complétez les étapes suivantes.

> [!IMPORTANT]
> La solution Microsoft 365 de gestion des risques internes fournit une option au niveau du client pour aider les clients à faciliter la gouvernance interne au niveau de l’utilisateur. Les administrateurs au niveau du client peuvent configurer des autorisations pour fournir l’accès à cette solution aux membres de votre organisation et configurer des connecteurs de données dans le Centre de conformité Microsoft 365 pour importer les données pertinentes afin de prendre en charge l’identification au niveau de l’utilisateur de l’activité potentiellement risquée. Les clients reconnaissent que les informations liées au comportement, au caractère ou aux performances de l’utilisateur individuel liées à l’emploi peuvent être calculées par l’administrateur et rendues accessibles à d’autres membres de l’organisation. En outre, les clients reconnaissent qu’ils doivent mener leur propre enquête complète relative au comportement, au caractère ou aux performances de l’utilisateur individuel matériellement liés à l’emploi, et non seulement à s’appuyer sur les informations du service de gestion des risques internes. Les clients sont les seuls responsables de l’utilisation du service de gestion des risques internes Microsoft 365 et de toute fonctionnalité ou service associé conformément à toutes les lois applicables, y compris les lois relatives à l’identification des utilisateurs individuels et aux mesures correctives.

Pour plus d’informations sur la façon dont les stratégies de risque internes peuvent vous aider à gérer les risques au niveau de votre organisation, consultez La gestion des risques internes [dans Microsoft 365](insider-risk-management.md).

## <a name="subscriptions-and-licensing"></a>Abonnements et licences

Avant de commencer à gérer les risques internes, vous devez confirmer votre abonnement [Microsoft 365 et](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) les modules. Pour accéder à la gestion des risques internes et l’utiliser, votre organisation doit avoir l’un des abonnements ou modules suivants :

- Microsoft 365 E5/A5/G5 (version payante ou d’essai)
- Microsoft 365 E3/A3/G3 + le module Microsoft 365 E5 conformité Microsoft 365 E5/A5/G5
- Microsoft 365 E3/A3/G3 + le module Microsoft 365 E5/A5/G5 Gestion des risques internes
- Abonnement Office 365 E3 + Enterprise Mobility and Security E3 + le module complémentaire Microsoft 365 E5 Conformité

L’une des licences ci-dessus doit être attribuée aux utilisateurs inclus dans les stratégies de gestion des risques internes.

> [!IMPORTANT]
> La gestion des risques internes est actuellement disponible dans les clients hébergés dans des régions géographiques et des pays pris en charge par les dépendances de service Azure. Pour vérifier que la gestion des risques internes est prise en charge pour votre organisation, consultez disponibilité des dépendances [Azure par pays/région](/troubleshoot/azure/general/dependency-availability-by-country).

Si vous n’avez pas de plan Microsoft 365 Entreprise E5 et que vous souhaitez essayer la gestion des risques internes, vous pouvez ajouter des [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou vous inscrire à une [](https://www.microsoft.com/microsoft-365/enterprise) version d’évaluation de Microsoft 365 Entreprise E5.

## <a name="recommended-actions-preview"></a>Actions recommandées (aperçu)

Les actions recommandées peuvent aider votre organisation à gérer rapidement les risques internes. Incluses dans la page **Vue d’ensemble** , les actions recommandées vous guident tout au long des étapes de configuration et de déploiement des stratégies.

![Actions recommandées par la gestion des risques internes.](../media/insider-risk-recommended-actions.png)

Les recommandations suivantes sont disponibles pour vous aider à démarrer ou à optimiser votre configuration de gestion des risques internes :

- **Activer l’audit** : lorsqu’il est allumé, l’activité des utilisateurs et des administrateurs dans votre organisation est enregistrée dans Microsoft 365'audit. Les stratégies de risque internes et les analyses d’analyse utilisent ce journal pour détecter les activités à risque.
- **Obtenir des autorisations sur la** gestion des risques utilisateur : le niveau d’accès dont vous disposez aux fonctionnalités de gestion des risques internes dépend du groupe de rôles qui vous a été attribué. Pour accéder aux actions recommandées et les configurer, les utilisateurs doivent être  affectés aux groupes de rôles Gestion des risques internes ou *Administrateurs* de la gestion des risques internes.
- **Choisissez des indicateurs de stratégie** : les indicateurs sont essentiellement les activités des utilisateurs que vous souhaitez détecter et examiner. Vous pouvez choisir des indicateurs pour suivre l’activité dans plusieurs Microsoft 365 et services.
- **Recherchez les risques internes potentiels** : exécutez une analyse pour découvrir les risques internes potentiels qui se produisent dans votre organisation. Après avoir évalué les résultats, examinez les stratégies recommandées à configurer.
- **Attribuer des autorisations** à d’autres personnes : si d’autres membres de l’équipe sont chargés de gérer les fonctionnalités de risque internes, vous devez les attribuer aux groupes de rôles appropriés.
- Créez votre première stratégie : pour recevoir des alertes sur les activités potentiellement risquées, vous devez configurer des stratégies basées sur des modèles prédéfinie qui définissent les activités utilisateur que vous souhaitez détecter et examiner.

Chaque action recommandée incluse dans cette expérience possède quatre attributs :

- **Action** : nom et description de l’action recommandée.
- **État** : état de l’action recommandée. Les valeurs *ne sont pas démarrées*, *en cours*, *enregistrées pour ultérieurement* ou *terminées*.
- **Obligatoire ou facultatif :** si l’action recommandée est requise ou facultative pour que les fonctionnalités de gestion des risques internes fonctionnent comme prévu.
- **Durée d’évaluation :** durée estimée de l’action recommandée en minutes.

Sélectionnez une recommandation dans la liste pour commencer à configurer la gestion des risques internes. Chaque action recommandée vous guide à travers les activités requises pour la recommandation, y compris les exigences, à quoi s'attendre et l'impact de la configuration de la fonctionnalité dans votre organisation.   Chaque action recommandée est automatiquement marquée comme terminée lorsqu’elle est configurée ou vous devez sélectionner manuellement l’action comme étant terminée lorsqu’elle est configurée.

## <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Étape 1 (obligatoire) : Activer les autorisations pour la gestion des risques internes

> [!IMPORTANT]
> Après avoir configuré vos groupes de rôles, l’application des autorisations de groupe de rôles aux utilisateurs affectés au sein de votre organisation peut prendre jusqu’à 30 minutes.

Six groupes de rôles sont utilisés pour configurer les fonctionnalités de gestion des risques internes. Pour **rendre la** gestion des risques internes disponible en tant qu’option de menu dans Centre de conformité Microsoft 365 et pour poursuivre ces étapes de configuration, vous devez être affecté à l’un des rôles ou groupes de rôles suivants :

- Azure Active Directory [*administrateur général*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory [*administrateur de conformité de l’application*](/azure/active-directory/roles/permissions-reference#compliance-administrator)
- Centre de conformité Microsoft 365 [*groupe de rôles Gestion de l’organisation*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- Centre de conformité Microsoft 365 [*de rôle Administrateur de conformité*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) de l’application
- *Groupe de rôles Gestion des risques internes*
- *Groupe de rôles d’administrateur de gestion des* risques internes

Selon la façon dont vous souhaitez gérer les stratégies et les alertes de gestion des risques internes, vous devez affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de gestion des risques internes. Vous avez la possibilité d’affecter des utilisateurs ayant différentes responsabilités de conformité à des groupes de rôles spécifiques pour gérer différents domaines de fonctionnalités de gestion des risques internes. Vous pouvez également décider d’affecter tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et visionneuses désignés au groupe de rôles Gestion des risques internes. Utilisez un ou plusieurs groupes de rôles pour mieux vous adapter à vos exigences de gestion de la conformité.

Vous aurez le choix entre ces options de groupe de rôles et les actions de solution lorsque vous travaillerez avec la gestion des risques internes :

|**Actions**|**Gestion des risques internes**|**Administrateur de la gestion des risques internes**|**Analystes de la gestion des risques internes.**|**Enquêteurs sur la gestion des risques internes.**|**Auditeurs de gestion des risques internes**|
|:----------|:--------------------------|:--------------------------------|:-----------------------------------|:----------------------------------------|:-----------------------------------|
| Configurer les stratégies et les paramètres | Oui | Oui | Non | Non | Non |
| Informations d’analyse d’accès | Oui | Oui | Oui | Non | Non |
| Accéder aux & examiner les alertes | Oui | Non | Oui | Oui | Non |
| Accéder aux & cas | Oui | Non | Oui | Oui | Non |
| Accéder & afficher l’Explorateur de contenu | Oui | Non | Non | Oui | Non |
| Configurer des modèles d’avis | Oui | Non | Oui | Oui | Non |
| Afficher les journaux d& exporter | Oui | Non | Non | Non | Oui |

>[!IMPORTANT]
>Assurez-vous que vous avez toujours au moins un utilisateur  dans les groupes de  rôles Gestion des risques internes ou Administrateur de la gestion des risques internes (selon l’option que vous choisissez) afin que votre configuration de gestion des risques internes n’entre pas dans un scénario « administrateur zéro » si des utilisateurs spécifiques quittent votre organisation.

Les membres des rôles suivants peuvent affecter des utilisateurs à des groupes de rôles de gestion des risques internes et  avoir les mêmes autorisations de solution incluses avec le groupe de rôles Administrateur de la gestion des risques internes :

- Azure Active Directory *administrateur général*
- Azure Active Directory *de conformité de l’application*
- Centre de conformité Microsoft 365 *gestion de l’organisation*
- Centre de conformité Microsoft 365 *de conformité de l’application*

> [!NOTE]
> Ces groupes de rôles ne sont actuellement pas pris en charge sur Privileged Identity Management (PIM). Pour en savoir plus sur PIM, voir [Attribuer Azure AD rôles dans Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-how-to-add-role-to-user).

### <a name="add-users-to-an-insider-risk-management-role-group"></a>Ajouter des utilisateurs à un groupe de rôles de gestion des risques internes

Pour ajouter des utilisateurs à un groupe de rôles de gestion des risques internes, complétez les étapes suivantes :

1. [Connectez-vous Centre de conformité Microsoft 365](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.

2. Dans le Centre de &amp; conformité de sécurité, allez **à Autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez le groupe de rôles de gestion des risques internes à ajouter aux utilisateurs, puis **sélectionnez Modifier le groupe de rôles**.

4. **Sélectionnez Choisir les membres** dans le volet de navigation de gauche, puis sélectionnez **Modifier**.

5. **Sélectionnez Ajouter**, puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Sélectionnez **Ajouter**, puis **Terminé**.

7. **Sélectionnez Enregistrer** pour ajouter les utilisateurs au groupe de rôles. **Sélectionnez Fermer** pour effectuer les étapes.

## <a name="step-2-required-enable-the-microsoft-365-audit-log"></a>Étape 2 (obligatoire) : activer le journal d Microsoft 365'audit

La gestion des risques internes utilise Microsoft 365 journaux d’audit pour les informations et les activités utilisateur identifiées dans les stratégies et analyses. Les Microsoft 365 d’audit sont un résumé de toutes les activités au sein de votre organisation et les stratégies de gestion des risques internes peuvent utiliser ces activités pour générer des informations sur les stratégies.

L'audit est activé par défaut pour les organisations Microsoft 365. Certaines organisations peuvent avoir désactivé l'audit pour des raisons spécifiques. Si l'audit est désactivé pour votre organisation, c'est peut-être parce qu'un autre administrateur l'a désactivé. Nous vous recommandons de confirmer que vous pouvez réactiver l'audit lorsque vous terminez cette étape.

Pour obtenir des instructions détaillées sur l'activation de l'audit, consultez [Activer ou désactiver la recherche dans le journal d'audit](turn-audit-log-search-on-or-off.md). Une fois l’audit activé, le message qui apparaît indique que le journal d’audit est en cours de préparation et que vous pourrez effectuer une recherche environ deux heures après la fin de la préparation. Vous n'avez à faire cette action qu'une seule fois. Pour plus d'informations sur l'utilisation du journal d'audit Microsoft 365, consultez [Rechercher dans le journal d'audit](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-enable-and-view-insider-risk-analytics-insights"></a>Étape 3 (facultative) : activer et afficher les informations d’analyse des risques internes

L'analyse de la gestion des risques d'initiés vous permet d'effectuer une évaluation des risques d'initiés potentiels dans votre organisation sans configurer de politiques de risque d'initiés. Cette évaluation peut permettre à votre organisation d’identifier des zones potentielles plus élevées de risque utilisateur et vous aider à déterminer le type et l’étendue des stratégies de gestion des risques internes que vous pouvez envisager de configurer. Cette évaluation peut également vous aider à déterminer les besoins en matière de licences supplémentaires ou d’optimisation future des stratégies existantes. Les résultats de l'analyse analytique peuvent prendre jusqu'à 48 heures avant que les informations ne soient disponibles sous forme de rapports pour examen. Pour en savoir plus sur les analyses, voir [paramètres](insider-risk-management-settings.md#analytics) de gestion des risques internes : Analyse et vision de la vidéo [Analyse](https://www.youtube.com/watch?v=5c0P5MCXNXk) de la gestion des risques internes pour mieux comprendre comment l’analyse peut accélérer l’identification des risques internes potentiels et vous aider à prendre rapidement des mesures.

Pour activer l’analyse des risques internes, vous devez être membre du groupe de rôles d’administrateur de gestion des risques *internes,* d’administrateur de gestion des risques internes ou Microsoft 365 *d’administrateur* global.

Pour activer l’analyse des risques internes, vous suivrez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), allez à **La gestion des risques internes**.
2. **Sélectionnez Exécuter l’analyse** dans **l’analyse des risques** internes dans la carte de votre organisation, sous l’onglet Vue d’ensemble de la gestion **des** risques internes. Cette action permet d’analyser l’analyse de votre organisation. Vous pouvez également activer l’analyse dans votre organisation en naviguant vers les **paramètres** >  des risques **internesAnalytics** et en activant **l’analyse de l’activité** utilisateur de votre client pour identifier les risques internes potentiels.
3. Dans le **volet Détails de l’analyse** , **sélectionnez Exécuter l’analyse pour démarrer l’analyse pour votre organisation**. Les résultats de l'analyse analytique peuvent prendre jusqu'à 48 heures avant que les informations ne soient disponibles sous forme de rapports pour examen.

Après avoir passé en revue les analyses, choisissez les stratégies de risques internes et configurez les conditions préalables associées qui répondent le mieux à la stratégie de prévention des risques internes de votre organisation.

## <a name="step-4-recommended-configure-prerequisites-for-policies"></a>Étape 4 (recommandée) : configurer les conditions préalables pour les stratégies

La plupart des stratégies de gestion des risques internes ont des conditions préalables qui doivent être configurées pour que les indicateurs de stratégie génèrent des alertes d’activité pertinentes. Configurez les conditions préalables appropriées en fonction des stratégies que vous prévoyez de configurer pour votre organisation.

### <a name="configure-microsoft-365-hr-connector"></a>Configurer Microsoft 365 connecteur RH

La gestion des risques internes prend en charge l’importation de données utilisateur et de journal importées à partir de plateformes tierces de gestion des risques et de ressources humaines. Le connecteur de données Microsoft 365 Ressources humaines (RH) vous permet d’archiver des données de ressources humaines à partir de fichiers CSV, y compris les dates de résiliation des utilisateurs, les dates de dernière embauche, les notifications du plan d’amélioration des performances, les actions d’évaluation des performances et l’état des changements de niveau de travail. Celles-ci permettent d’attirer l’attention sur les indicateurs d’alertes dans les stratégies de gestion des risques internes et il s’agit d’un élément essentiel de la configuration de la couverture de la gestion des risques. Si vous configurez plusieurs connecteurs RH pour votre organisation, la gestion des risques internes tirera automatiquement les indicateurs de tous les connecteurs RH.

Le connecteur MICROSOFT 365 est requis lors de l’utilisation des modèles de stratégie suivants :

- Fuites de données provoquées par un utilisateur mécontent
- Vol de données utilisateur en partant
- Utilisation incorrecte des données générales des patients
- Violations de stratégie de sécurité par des utilisateurs quittant l’entreprise
- Violations de stratégie de sécurité par des utilisateurs mécontents

Consultez [l’article](import-hr-data.md) Configurer un connecteur pour importer des données RH pour obtenir des instructions pas à pas pour configurer le connecteur RH Microsoft 365 pour votre organisation. Une fois que vous avez configuré le connecteur RH, revenir à ces étapes de configuration.

### <a name="configure--a-healthcare-specific-data-connector"></a>Configurer un connecteur de données spécifique à la santé

La gestion des risques internes prend en charge l’importation de données utilisateur et de journaux importées à partir de tiers sur des systèmes de dossiers médicaux électroniques (EMR) existants. Les connecteurs de données Microsoft Health and Health and Health vous permettent d’obtenir des données d’activité à partir de votre système EMR avec des fichiers CSV, y compris un accès incorrect aux dossiers des patients, des activités de volume suspectes, ainsi que des activités de modification et d’exportation. Celles-ci permettent d’attirer l’attention sur les indicateurs d’alertes dans les stratégies de gestion des risques internes et il s’agit d’un élément essentiel de la configuration de la couverture de la gestion des risques.

Si vous configurez plusieurs connecteurs de santé ou de santé pour votre organisation, la gestion des risques internes prend automatiquement en charge les signaux d’événements et d’activités provenant de tous les connecteurs Santé et Santé.
Le connecteur Microsoft 365 Santé ou Connecteur de Santé ou Connecteur de Santé est requis lors de l’utilisation des modèles de stratégie suivants :

- Utilisation incorrecte des données générales des patients

Consultez [](import-healthcare-data.md) l’article Configurer un connecteur pour importer des données de santé ou Configurer un connecteur pour importer [des données EHR d’Ehr pour](import-epic-data.md) obtenir des instructions pas à pas pour configurer un connecteur spécifique à la santé pour votre organisation. Une fois que vous avez configuré un connecteur, revenir à ces étapes de configuration.

### <a name="configure-data-loss-prevention-dlp-policies"></a>Configurer des stratégies de protection contre la perte de données (DLP)

La gestion des risques internes prend en charge l’utilisation de stratégies DLP pour vous aider à identifier l’exposition intentionnelle ou accidentelle d’informations sensibles à des parties indésirables pour les alertes DLP de niveau de gravité élevé. Lorsque vous configurez une stratégie de gestion des risques internes avec l’un des **modèles de fuites** de données, vous avez la possibilité d’affecter une stratégie DLP spécifique à la stratégie pour ces types d’alertes.

Les stratégies DLP permettent d’identifier les utilisateurs pour activer le score de risque dans la gestion des risques internes pour les alertes DLP de gravité élevée pour les informations sensibles et sont un élément important de la configuration de la couverture de gestion des risques complète dans votre organisation. Pour plus d’informations sur la gestion des risques internes et les considérations sur l’intégration et la planification des stratégies DLP, voir [stratégies de gestion des risques internes](insider-risk-management-policies.md#general-data-leaks).

> [!IMPORTANT]
>Assurez-vous que vous avez terminé les travaux suivants :
>
>- Vous comprenez et configurez correctement les utilisateurs dans l’étendue dans les stratégies de gestion des risques internes et DLP pour produire la couverture de stratégie que vous attendez.
>- Assurez-vous que le paramètre **Rapports d’incident** dans la stratégie DLP pour la gestion des risques internes utilisé avec ces  modèles est configuré pour les alertes de niveau de gravité élevé. Les alertes de gestion des risques internes ne sont pas générées à partir des stratégies DLP avec le champ Rapports **d’incidents** définie sur *Faible* ou *Moyen*.

Une stratégie DLP est facultative lorsque vous utilisez les modèles de stratégie suivants :

- Fuites de données générales
- Fuites de données par des utilisateurs prioritaires

Consultez [l’article Créer, tester et régler une stratégie DLP](create-test-tune-dlp-policy.md) pour obtenir des instructions pas à pas pour configurer des stratégies DLP pour votre organisation. Une fois que vous avez configuré une stratégie DLP, revenir à ces étapes de configuration.

### <a name="configure-priority-user-groups"></a>Configurer des groupes d’utilisateurs prioritaires

La gestion des risques internes inclut la prise en charge de l’attribution de groupes d’utilisateurs prioritaires à des stratégies pour faciliter l’identité des activités à risque uniques pour les utilisateurs ayant des positions critiques, des niveaux élevés de données et d’accès au réseau, ou un historique passé de comportement à risque. La création d’un groupe d’utilisateurs prioritaire et l’affectation d’utilisateurs au groupe aident les stratégies d’étendue aux circonstances uniques présentées par ces utilisateurs.

Un groupe d’utilisateurs prioritaire est requis lors de l’utilisation des modèles de stratégie suivants :

- Violations de la stratégie de sécurité par des utilisateurs prioritaires
- Fuites de données par des utilisateurs prioritaires

Consultez [l’article Prise en charge des paramètres](insider-risk-management-settings.md#priority-user-groups-preview) de gestion des risques internes pour obtenir des instructions pas à pas pour créer un groupe d’utilisateurs prioritaire. Une fois que vous avez configuré un groupe d’utilisateurs prioritaires, revenir à ces étapes de configuration.

### <a name="configure-physical-badging-connector-optional"></a>Configurer le connecteur de badging physique (facultatif)

La gestion des risques internes prend en charge l’importation de données utilisateur et de journal à partir de plateformes de contrôle et d’accès physiques. Le connecteur de badging physique vous permet d’obtenir des données d’accès à partir de fichiers JSON, y compris les ID d’utilisateur, les ID de point d’accès, les heures et les dates d’accès et l’état d’accès. Celles-ci permettent d’attirer l’attention sur les indicateurs d’alertes dans les stratégies de gestion des risques internes et il s’agit d’un élément essentiel de la configuration de la couverture de la gestion des risques. Si vous configurez plusieurs connecteurs de mauvaise gestion physique pour votre organisation, la gestion des risques internes tire automatiquement les indicateurs de tous les connecteurs de mauvaise gestion physiques. Les informations du connecteur de badging physique complètent d’autres signaux de risque internes lors de l’utilisation de tous les modèles de stratégie de risque internes.

> [!IMPORTANT]
> Pour que les stratégies de gestion des risques internes utilisent et corrélent les données de signal liées aux utilisateurs qui quittent et se terminent par des données d’événement à partir de vos plateformes de contrôle physique et d’accès, vous devez également configurer le connecteur RH Microsoft 365. Si vous activez le connecteur de badging physique sans activer le connecteur RH Microsoft 365, les stratégies de gestion des risques internes ne traitera que les événements d’accès physique non autorisé pour les utilisateurs de votre organisation.

Pour obtenir [des](import-physical-badging-data.md) instructions pas à pas sur la configuration du connecteur de badging physique pour votre organisation, consultez l’article Configurer un connecteur pour importer des données de mauvaise gestion physiques. Une fois que vous avez configuré le connecteur, revenir à ces étapes de configuration.

### <a name="configure-microsoft-defender-for-endpoint-optional"></a>Configurer Microsoft Defender pour le point de terminaison (facultatif)

[Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) est une plateforme de sécurité de point de terminaison d’entreprise conçue pour aider les réseaux d’entreprise à prévenir, détecter, examiner et répondre aux menaces avancées. Pour avoir une meilleure visibilité des violations de sécurité dans votre organisation, vous pouvez importer et filtrer les alertes Defender for Endpoint pour les activités utilisées dans les stratégies créées à partir de modèles de stratégie de violation de sécurité de gestion des risques internes.

Si vous créez des stratégies de violation de la sécurité, Microsoft Defender pour point de terminaison doit être configuré dans votre organisation et activer Defender pour le point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Defender pour importer les alertes de violation de sécurité. Pour plus d’informations sur les conditions requises, consultez l’article Sur les conditions minimales [requises pour Microsoft Defender pour endpoint](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements) .

Consultez l’article Configurer les fonctionnalités avancées dans [Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center) pour obtenir des instructions pas à pas pour configurer Defender pour Endpoint pour l’intégration de la gestion des risques internes. Une fois que vous avez configuré Microsoft Defender pour le point de terminaison, revenir à ces étapes de configuration.

## <a name="step-5-required-configure-insider-risk-settings"></a>Étape 5 (obligatoire) : configurer les paramètres des risques internes

[Les paramètres de risque internes s’appliquent](insider-risk-management-settings.md) à toutes les stratégies de gestion des risques internes, quel que soit le modèle que vous avez choisi lors de la création d’une stratégie. Les paramètres sont configurés à l’aide des **Paramètres de risque internes** contrôle situés en haut de tous les onglets de gestion des risques internes. Ces paramètres contrôlent la confidentialité, les indicateurs, la surveillance de fenêtres et les détections intelligentes.

Avant de configurer une stratégie, définissez les paramètres de risque internes suivants :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez Gestion des risques  internes et sélectionnez **Paramètres** des risques internes dans le coin supérieur droit de n’importe quelle page.
2. Dans la page **Confidentialité** , sélectionnez un paramètre de confidentialité pour afficher les noms d’utilisateur des alertes de stratégie.
3. Dans la page Indicateurs, sélectionnez les indicateurs d’alerte que vous souhaitez appliquer à toutes les **stratégies** de risque internes.

    > [!IMPORTANT]
    > Pour recevoir des alertes pour les activités risquées définies dans vos stratégies, vous devez sélectionner un ou plusieurs indicateurs. Si les indicateurs ne sont pas configurés dans Paramètres, ils ne sont pas sélectionnables dans les stratégies de risque internes.

4. Dans la page **Délais de stratégie**, sélectionnez [](insider-risk-management-settings.md#policy-timeframes) les délais de stratégie à mettre en vigueur pour un utilisateur lorsqu’il déclenche une correspondance pour une stratégie de risque interne.
5. Dans la page **Détections intelligentes** , configurez les paramètres suivants pour les stratégies de risque interne :
    - [Exclusions de types de fichiers](insider-risk-management-settings.md#file-type-exclusions)
    - [Nombre minimal d’événements quotidiens pour améliorer le score d’activité inhabituelle](insider-risk-management-settings.md#minimum-number-of-daily-events-to-boost-score-for-unusual-activity)
    - [Niveau de volume d’alerte](insider-risk-management-settings.md#alert-volume)
    - [État d’alerte de Microsoft Defender pour point de terminaison](insider-risk-management-settings.md#microsoft-defender-for-endpoint-preview)
    - [Paramètres de domaine](insider-risk-management-settings.md#domains)
6. Dans la page **Exporter les alertes**, activez l’exportation des informations d’alerte de risque interne à l’aide des API de gestion Office 365 si nécessaire.
7. Dans la page **Groupes d’utilisateurs** prioritaires, créez un groupe d’utilisateurs prioritaire et ajoutez des utilisateurs s’ils ne sont pas créés à **l’étape 3**.
8. Dans la page **Power Automate flux**, configurez un flux à partir de modèles de flux de risques internes ou créez un flux. Consultez [l’article Prise en charge des paramètres de gestion](insider-risk-management-settings.md#power-automate-flows-preview) des risques internes pour obtenir des instructions pas à pas.
9. Dans la **page Ressources** de priorité, configurez les ressources de priorité pour utiliser les données de votre plateforme de contrôle physique et d’accès importées par le connecteur de badging physique. Consultez [l’article Prise en charge des paramètres de gestion](insider-risk-management-settings.md#priority-physical-assets-preview) des risques internes pour obtenir des instructions pas à pas.
10. Sur la page **Microsoft Teams**, activez l’intégration Microsoft Teams la gestion des risques internes pour créer automatiquement une équipe pour la collaboration des utilisateurs ou des cas. Consultez [l’article Prise en charge des paramètres de gestion](insider-risk-management-settings.md#microsoft-teams-preview) des risques internes pour obtenir des instructions pas à pas.
11. **Sélectionnez Enregistrer** pour activer ces paramètres pour vos stratégies de risque internes.

## <a name="step-6-required-create-an-insider-risk-management-policy"></a>Étape 6 (obligatoire) : créer une stratégie de gestion des risques internes

Les stratégies de gestion des risques internes incluent les utilisateurs attribués et définissent quels types d’indicateurs de risque sont configurés pour les alertes. Pour que les activités puissent déclencher des alertes, une stratégie doit être configurée. Utilisez l’Assistant Stratégie pour créer des stratégies de gestion des risques internes.

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

11. Si vous avez sélectionné je souhaite spécifier des **sites SharePoint,** des étiquettes de sensibilité et/ou des types d’informations sensibles comme contenu prioritaire à l’étape précédente, vous verrez les pages de détails pour les *sites SharePoint*, les *types* d’informations sensibles et les étiquettes de *sensibilité.* Utilisez ces pages détaillées pour définir les sites SharePoint, les types d’information sensible et les étiquettes de confidentialité à hiérarchiser dans la stratégie.

    - **Sites SharePoint** : sélectionnez **Ajouter un site SharePoint**, puis sélectionnez les sites SharePoint auxquels vous avez accès et que vous souhaitez classer. Par exemple, *« groupe1@contoso.sharepoint.com/sites/group1 »*.
    - **Type d’information sensible** : sélectionnez **Ajouter un type d’information confidentielle**, puis les types de confidentialité que vous souhaitez classer. Par exemple, *« Numéro de compte bancaire américain »* et *« Numéro de carte de crédit »*.
    - **Étiquette de confidentialité** : sélectionnez **Ajouter une étiquette de confidentialité**, puis les étiquettes que vous souhaitez classer. Par exemple, *« Confidentiel »* et *« Secret »*.

    >[!NOTE]
    >Les utilisateurs qui configurent la stratégie et sélectionnent des sites Share Point prioritaires peuvent sélectionner SharePoint sites à qui ils sont autorisés à accéder. Si SharePoint sites ne sont pas disponibles pour la sélection dans la stratégie par l’utilisateur actuel, un autre utilisateur avec les autorisations requises peut sélectionner les sites pour la stratégie ultérieurement ou l’utilisateur actuel doit avoir accès aux sites requis.

12. Sélectionnez **Suivant** pour continuer.
13. Si vous avez sélectionné les *fuites de données générales* ou les *fuites* de données par modèles d’utilisateurs prioritaires, des options s’offrent à vous dans la page Déclencheurs de cette stratégie pour les **événements** de déclenchement personnalisé et les indicateurs de stratégie. Vous avez la possibilité de sélectionner une stratégie ou des indicateurs DLP pour déclencher des événements qui amènent les utilisateurs affectés à la stratégie dans l’étendue du score d’activité. Si vous sélectionnez l’option Utilisateur correspond à une stratégie de protection contre la perte de données **(DLP)** déclenchant un événement, vous devez sélectionner une stratégie DLP dans la liste de listes de listes des stratégies DLP pour activer les indicateurs de déclenchement de la stratégie DLP pour cette stratégie de gestion des risques internes. Si vous sélectionnez l’option d’événement déclenchant une **activité d’exfiltration** , vous devez sélectionner un ou plusieurs des indicateurs répertoriés pour l’événement déclencheur de stratégie.
    >[!IMPORTANT]
    >Si vous ne parvenez pas à sélectionner un indicateur répertorié, c’est parce qu’il n’est pas activé pour votre organisation. Pour les rendre disponibles pour la sélection et l’affectation à la stratégie,  >  activez les indicateurs dans la gestion des risques internes **Paramètres** >  **Policy**.

    Si vous avez sélectionné d’autres modèles de stratégie, les événements de déclenchement personnalisés ne sont pas pris en charge. Les événements de déclenchement de stratégie intégrés s’appliquent et vous allez passer à l’étape 23 sans définir d’attributs de stratégie.

14. Sélectionnez **Suivant** pour continuer.
15. Si vous avez sélectionné les *fuites de données générales* ou les *fuites* de données par modèles utilisateur prioritaires et que vous avez sélectionné l’utilisateur effectue une **activité d’exfiltration** et les indicateurs associés, vous pouvez choisir des seuils personnalisés ou par défaut pour l’indicateur déclenchant des événements que vous avez sélectionnés. Choisissez les **seuils par défaut Utiliser (recommandé)** ou **Utiliser des seuils personnalisés pour les événements déclencheurs**.
16. Sélectionnez **Suivant** pour continuer.
17. Si vous avez sélectionné Utiliser des **seuils personnalisés pour les événements déclencheurs**, pour chaque indicateur d’événement déclencheur sélectionné à l’étape 13, choisissez le niveau approprié pour générer le niveau souhaité d’alertes d’activité.
18. Sélectionnez **Suivant** pour continuer.
19. Dans **la page** Indicateurs de stratégie, vous verrez les indicateurs que [](insider-risk-management-settings.md#indicators) vous avez définis comme disponibles dans la page **Paramètres** >  des risques **internes.** Sélectionnez les indicateurs que vous souhaitez appliquer à la stratégie.

    > [!IMPORTANT]
    > Si les indicateurs sur cette page ne peuvent pas être sélectionnés, vous sélectionner les indicateurs que vous souhaitez activer pour toutes les stratégies. Vous pouvez utiliser le bouton **Activer les indicateurs** dans l’Assistant ou sélectionner des indicateurs sur la page **Gestion des risques internes** > **Paramètres** > **Indicateurs de stratégie**.

    Si vous avez sélectionné au moins un indicateur *Office* ou *Appareil*, choisissez les **Boosters de score de risque** selon le cas. Les boosters de score de risque sont uniquement applicables pour les indicateurs sélectionnés.
    Si vous avez sélectionné un modèle de stratégie *Vol de données* ou *Fuites de données*, choisissez au moins une des méthodes **Détection de séquence** et une méthode **Détection d’exfiltration cumulée** à appliquer à la stratégie.

20. Sélectionnez **Suivant** pour continuer.
21. Dans la page **Décider s’il** faut utiliser les seuils d’indicateurs par défaut ou personnalisés, choisissez des seuils personnalisés ou par défaut pour les indicateurs de stratégie que vous avez sélectionnés. Choisissez les **seuils par défaut d’utilisation pour tous les indicateurs ou** spécifiez des **seuils personnalisés** pour les indicateurs de stratégie sélectionnés. Si vous avez sélectionné Spécifier des seuils personnalisés, choisissez le niveau approprié pour générer le niveau souhaité d’alertes d’activité pour chaque indicateur de stratégie.
22. Sélectionnez **Suivant** pour continuer.
23. Sur la page **Évaluation**, examinez les paramètres choisis pour la stratégie et toute suggestion ou tout avertissement pour vos sélections. Sélectionnez **Modifier** pour changer toute valeur de stratégie ou **Soumettre** pour créer et activer la stratégie.

## <a name="next-steps"></a>Prochaines étapes

Après avoir effectué ces étapes pour créer votre première stratégie de gestion des risques internes, vous commencerez à recevoir des alertes des indicateurs d’activité après environ 24 heures. Configurez des stratégies supplémentaires selon vos besoins à l’aide des instructions de l’étape 4 de cet article ou des étapes de création [d’une stratégie de risque interne](insider-risk-management-policies.md#create-a-new-policy).

Pour en savoir plus sur l’examen des alertes de risques internes et du tableau de bord **Alertes**, consultez les activités de gestion des risques [internes.](insider-risk-management-activities.md#alert-dashboard)
