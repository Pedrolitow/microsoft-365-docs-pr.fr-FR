---
title: Stratégies de gestion des risques internes
description: Découvrez les stratégies de gestion des risques internes dans Microsoft 365
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
ms.collection: m365-security-compliance
ms.openlocfilehash: 2f9a299faad33dbba09d9e32f3c860f9f7bd6311
ms.sourcegitcommit: 88c3b9758214936d283bad0321b826fb40a2e7e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2021
ms.locfileid: "60087808"
---
# <a name="insider-risk-management-policies"></a>Stratégies de gestion des risques internes

Les stratégies de gestion des risques internes déterminent les utilisateurs visés et les types d’indicateurs de risque configurés pour les alertes. Vous pouvez rapidement créer une stratégie qui s’applique à tous les utilisateurs au sein de votre organisation ou définir des groupes ou des utilisateurs individuels pour la gestion dans une stratégie. Les stratégies prennent en charge les priorités de contenu pour centrer les conditions des stratégies sur des applications Microsoft Teams spécifiques ou multiples, des sites SharePoint, des types de confidentialité de données et des étiquettes de données. Avec l’utilisation de modèles, vous pouvez sélectionner des indicateurs de risque spécifiques et personnaliser les seuils d’un événement pour les indicateurs de stratégie, personnalisant concrètement les scores de risque, ainsi que la fréquence et le niveau des alertes. En outre, les boosters de score de risque et les détections d’anomalies permettent d’identifier l’activité de l’utilisateur qui est de plus grande importance ou plus inhabituelle. Les fenêtres de stratégie vous permettent de définir le délai d’exécution à appliquer à la stratégie pour les activités d’alerte et elles sont utilisées pour déterminer la durée de la stratégie une fois celle-ci activée.

Consultez la [vidéo sur la Configuration des stratégies de gestion des risques internes](https://www.youtube.com/watch?v=kudK5ajZTUo) pour avoir une vue d’ensemble sur la façon dont les stratégies crées avec des modèles de stratégie intégrée peuvent vous aider à prendre des mesures sur des risques potentiels.

## <a name="policy-dashboard"></a>Tableau de bord de stratégie

Le **Tableau de bord de stratégie** vous permet de consulter rapidement les stratégies de votre organisation, d’ajouter manuellement des utilisateurs aux stratégies et de consulter l’état actuel des alertes associées à chaque stratégie.

- **Nom de la stratégie :** le nom attribué à la stratégie dans l’Assistant stratégie.
- **État** : l’état d’intégrité de chaque stratégie. Affiche le nombre de recommandations et d’avertissements de la stratégie, ou un état *Intègre* pour les stratégies sans problème.  Vous pouvez cliquer sur la stratégie pour afficher l’état d'intégrité détaillée de toute recommandation ou de tout avertissement.
- **Alertes actives** : le nombre d’alertes actives pour chaque stratégie.
- **Alertes confirmées** : le nombre total d’alertes ayant entraîné des cas à partir de la stratégie au cours des 365 derniers jours.
- **Actions effectuées sur les alertes** : le nombre total d’alertes confirmées ou ignorées au cours des 365 derniers jours.
- **Efficacité de la stratégie** : le pourcentage déterminé par le nombre total des alertes confirmées divisé par le nombre total de mesures prises à la suite des alertes (il s’agit du total des alertes qui ont été confirmées ou ignorées au cours de l’année précédente).

![Tableau de bord de la stratégie de gestion des risques internes.](../media/insider-risk-policy-dashboard.png)

## <a name="policy-recommendations-from-analytics-preview"></a>Recommandations de la stratégie à partir d’une analyse (préversion)

L’analyse des risques internes vous permet d’effectuer une évaluation des risques internes potentiels au sein de votre organisation sans aucune configuration de stratégie des risques internes. Cette évaluation peut permettre à votre organisation d’identifier des zones potentielles plus élevées de risque utilisateur et vous aider à déterminer le type et l’étendue des stratégies de gestion des risques internes que vous pouvez envisager de configurer.

Si vous souhaitez en savoir plus sur les recommandations de stratégie et l’analyse des risques internes, consultez [Paramètres de gestion des risques internes : analyse (préversion)](insider-risk-management-settings.md#analytics-preview).

## <a name="policy-templates"></a>Modèles de stratégie

Les modèles de gestion des risques internes sont des conditions de stratégie prédéfinies qui définissent les types d’indicateurs de risque et le modèle d’attribution de scores de risque utilisés par la stratégie. Chaque stratégie doit avoir un modèle affecté dans l’Assistant de création de stratégie avant la création de celle-ci. La gestion des risques internes prend en charge jusqu’à cinq stratégies pour chaque modèle de stratégie. Lorsque vous créez une stratégie de risque interne à l’aide de l’Assistant stratégie, vous choisissez l’un des modèles de stratégie suivants :

### <a name="data-theft-by-departing-users"></a>Vol de données par des employés quittant votre organisation

Lorsque des utilisateurs quittent votre organisation, il existe des indicateurs de risque spécifiques généralement associés au vol de données par des employés sortants. Cet modèle de stratégie utilise des indicateurs d’exfiltration pour l’attribution du scores de risque et se concentre sur la détection et les alertes dans cette zone à risque. Le vol de données par des employés quittant votre organisation peut inclure le téléchargement de fichiers à partir de SharePoint Online, l’impression de fichiers et la copie de données vers des services de stockage et de messagerie cloud personnels à l’approche de leur démission et de leur date de départ. En utilisant le connecteur Microsoft 365 RH ou l’option pour surveiller automatiquement la suppression de compte utilisateur dans Azure Active Directory pour votre organisation, ce modèle commence l’attribution de scores pour les indicateurs de risque liés à ces activités et la façon dont elles se mettent en corrélation avec le statut professionnel de l’utilisateur.

> [!IMPORTANT]
> Lors de l’utilisation de ce modèle, vous pouvez configurer un connecteur Microsoft 365 RH pour importer périodiquement les informations sur la date de démission et la date de licenciement des utilisateurs dans votre organisation. Consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) pour obtenir des conseils détaillés pour configurer le connecteur Microsoft 365 RH au sein de votre organisation. Si vous décidez de ne pas utiliser le connecteur RH, vous devez sélectionner le compte utilisateur supprimé à partir de l’option Azure AD lors de la configuration des événements déclencheurs dans l’Assistant stratégie.

### <a name="general-data-leaks"></a>Fuites de données générales

Protéger et empêcher les fuites de données constitue un défi permanent pour la plupart des organisations, en particulier avec l’augmentation rapide de nouvelles données créées par les utilisateurs, les appareils et les services. Les utilisateurs peuvent créer, stocker et partager des informations sur tous les services et appareils qui rendent la gestion des fuites de données de plus en plus complexe et difficile. Les fuites de données peuvent inclure le partage à outrance et accidentel d’informations en dehors de votre organisation ou le vol de données à des fins malveillantes. Avec une stratégie affectée de protection contre la perte de données (DLP) ou un événement déclencheur intégré, ce modèle commence les détections d’attribution de scores en temps réel des téléchargements de données suspectes SharePoint Online, le partage de dossiers et de fichiers, l’impression de fichiers et la copie de données vers des services de stockage et de messagerie cloud personnels.

Lors de l’utilisation d’un modèle de *Fuites de données*, vous pouvez attribuer une stratégie DLP pour déclencher des indicateurs dans la stratégie de risque interne pour les alertes à gravité élevée au sein de votre organisation. Chaque fois qu’une alerte à gravité élevée générée par une règle de stratégie DLP est ajoutée au journal d’audit d’Office 365, les stratégies de risque interne créées à l’aide de ce modèle examinent automatiquement l’alerte DLP à gravité élevée. Si l’alerte contient un utilisateur dans l’étendue définie dans la stratégie de risque interne, l’alerte est traitée par la stratégie de risque interne en tant que nouvelle alerte et un score de risque et une gravité de risque interne lui sont attribués. Cette stratégie vous permet d’évaluer cette alerte dans le contexte avec d’autres activités incluses dans le cas. Si vous ne choisissez aucune stratégie DLP, vous devez sélectionner l’événement déclencheur intégré.

#### <a name="data-leaks-policy-guidelines"></a>Conseils sur la stratégie de fuite de données

Lors de la création ou la modification de stratégies DLP pour les utiliser avec des stratégies de gestion des risques internes, tenez compte des conseils suivants :

- Hiérarchisez les événements d’exfiltration de données et montrez-vous sélectif quand vous attribuez les paramètres des **Rapports d’incident** sur *Élevé* lors de la configuration de règles dans vos stratégies DLP. Par exemple, l’envoi de documents sensibles à un concurrent connu doit être un événement d’exfiltration de niveau d’alerte *Élevé*. L’attribution à outrance du niveau *Élevé* dans les paramètres de **Rapports d’incident** d’autres règles de stratégie DLP peut augmenter l’attention dans le flux de travail de l’alerte de gestion des risques internes et compliquer la tâche de vos enquêteurs et analystes en données pour évaluer correctement ces alertes. Par exemple, l’attribution de niveaux d’alerte *Élevé* pour accéder aux activités de refus dans les stratégies DLP peut rendre plus difficile l’évaluation des activités et du comportement utilisateur réellement risqués.
- Assurez-vous de comprendre et de configurer correctement les utilisateurs dans l’étendue dans les stratégies de gestion des risques internes et DLP. Seuls les utilisateurs définis comme étant dans l’étendue pour les stratégies de gestion des risques internes utilisant le modèle **Fuites de données** auront des alertes de stratégies DLP à gravité élevée traitées. En outre, seuls les utilisateurs définis comme étant dans l’étendue dans une règle pour une alerte DLP à gravité élevée seront examinés par la stratégie de gestion des risques internes. Il est important de ne pas configurer involontairement de manière conflictuelle des utilisateurs dans l’étendue des stratégies de risque interne et DLP.

     Par exemple, si vos règles de stratégie DLP sont définies uniquement aux utilisateurs de l’équipe Ventes et que la stratégie de risque interne créée à partir du modèle **Fuites de données** a défini tous les utilisateurs comme étant dans l’étendue, la stratégie de risque interne ne traitera en réalité que les alertes DLP à gravité élevée pour les utilisateurs de l’équipe Ventes. La stratégie de risque interne ne recevra aucune alerte DLP à gravité élevée pour les utilisateurs à traiter qui ne sont pas définis dans les règles DLP pour cet exemple. Inversement, si votre stratégie de gestion des risques internes créée à partir des modèles **Fuites de données** est définie sur les utilisateurs de l’équipe Ventes uniquement et que la stratégie DLP attribuée est définie sur tous les utilisateurs, la stratégie de risque interne ne traitera que les alertes DLP à gravité élevée pour les membres de l’équipe Ventes. La stratégie de gestion des risques internes ignorera les alertes DLP à gravité élevée pour tous les utilisateurs qui ne sont pas dans l’équipe Ventes.

- Vérifiez que le paramètre de règle des **Rapports d’incident** dans la stratégie DLP utilisée pour ce modèle de gestion des risques internes est paramétré pour les alertes à niveau de gravité *Élevé*. Le niveau de gravité *Élevé* est l’événement déclencheur et les alertes de gestion des risques internes ne sont pas générées à partir des règles dans les stratégies DLP ayant le champ **Rapports d’incident** défini sur *Faible* ou *Moyen*.

    ![Paramètre d’alerte de stratégie DLP.](../media/insider-risk-DLP-policy-high-severity.png)

     > [!NOTE]
     > Lorsque vous créez une stratégie DLP à l’aide de modèles intégrés, vous devez sélectionner l’option **Créer ou personnaliser des règles DLP avancées** pour configurer le paramètre **Rapports d’incident** pour le niveau de gravité *Élevé*.

Les stratégies de gestion des risques internes créées à partir du modèle **Fuites de données** ne peuvent avoir qu’une seule stratégie DLP assignée. Envisagez de créer une stratégie DLP dédiée qui associe les différentes activités que vous souhaitez détecter et qui agissent en tant qu’événements déclencheurs pour les stratégies de risque interne qui utilisent le modèle **Fuites de données**.

Pour obtenir des conseils détaillés sur la configuration de stratégies DLP pour votre organisation, consultez l’article [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md).

### <a name="data-leaks-by-priority-users-preview"></a>Fuites de données par des utilisateurs prioritaires (aperçu)

Protéger et empêcher les fuites de données pour les utilisateurs de votre organisation peut dépendre de leur fonction, du niveau d’accès aux informations sensibles et de l’historique des risques. Les fuites de données peuvent inclure le partage accidentel et à outrance d’informations hautement sensibles en dehors de votre organisation ou le vol de données à des fins malveillantes. Grâce à une stratégie de protection contre la perte de données (DLP) assignée, ce modèle commence les détections d’attribution de scores en temps réel des activités suspectes et entraîne une probabilité accrue d’alertes de risque interne et d’alertes ayant des niveaux de gravité plus élevés. Les utilisateurs prioritaires sont définis dans les [groupes d’utilisateurs prioritaires](insider-risk-management-settings.md#priority-user-groups-preview) configurés dans la zone des paramètres de la gestion des risques internes.

Comme avec le **Modèle de fuites de données générales**, vous devez attribuer une stratégie DLP pour déclencher des indicateurs dans la stratégie de risque interne pour les alertes à gravité élevée au sein de votre organisation. Suivez les conseils de la Stratégie des fuites de données ci-dessus lorsque vous créez une stratégie à l’aide de ce modèle. De plus, vous devez affecter les groupes d’utilisateurs prioritaires créés dans la **Gestion des risques internes** > **Paramètres** > **Groupes d’utilisateurs prioritaires** à la stratégie.

### <a name="data-leaks-by-disgruntled-users-preview"></a>Fuites de données par des utilisateurs mécontents (préversion)

Quand des utilisateurs font l’expérience de facteurs de stress professionnels, ils peuvent devenir mécontents, qui ce augmente les possibilités d’activités de risque interne. Ce modèle commence l’attribution de scores sur l’activité utilisateur lorsqu’un indicateur associé au mécontentement est identifié. Des exemples incluent les notifications d’amélioration des performances, les évaluations médiocres des performances et les changements d’état du niveau des tâches. La fuite des données par des utilisateurs mécontents peut inclure le téléchargement de fichiers à partir de SharePoint Online et la copie de données vers des services de stockage et de messagerie cloud personnelle à l’approche d’événements professionnels stressants.

Lorsque vous utilisez ce modèle, vous pouvez également configurer un connecteur Microsoft 365 RH pour importer périodiquement des notifications d’amélioration des performances, des états d’évaluation médiocres des performances ou des informations sur les changements du niveau des tâches pour les utilisateurs de votre organisation. Consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) pour obtenir des conseils détaillés pour configurer le connecteur Microsoft 365 RH au sein de votre organisation.

### <a name="general-security-policy-violations-preview"></a>Violations générales de la stratégie de sécurité (préversion)

Dans de nombreuses organisations, les utilisateurs sont autorisés à installer des logiciels sur leur appareil ou à modifier les paramètres d’appareil pour faciliter leurs tâches. Que ce soit de manière involontaire ou avec une intention malveillante, les utilisateurs peuvent installer un programme malveillant ou désactiver des fonctionnalités importantes de sécurité permettant de protéger les informations sur leur appareil ou sur vos ressources réseau. Ce modèle de stratégie utilise les alertes de sécurité de Microsoft Defender pour point de terminaison pour commencer l’attribution de scores sur ces activités et concentrer la détection et les alertes sur cette zone à risque. Utilisez ce modèle pour fournir des informations concernant les violations de stratégie de sécurité pour les situations dans lesquelles des utilisateurs peuvent avoir un historique de violations liées à une stratégie de sécurité qui peut être un indicateur de risque interne.

Microsoft Defender pour point de terminaison doit être configuré dans votre organisation et vous devez activer Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Microsoft Defender pour importer les alertes de violation de la sécurité. Pour plus d’informations sur la configuration de Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes, consultez [Configurer des fonctionnalités avancées dans Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="security-policy-violations-by-departing-users-preview"></a>Violations de stratégie de sécurité par des utilisateurs sortants (préversion)

Les utilisateurs sortants, qu’ils partent en bons ou en mauvais termes, peuvent constituer des risques plus élevés en matière de violations de stratégie de sécurité. Pour vous protéger contre des violations de sécurité malveillantes ou accidentelles de la part d’utilisateurs sortants, ce modèle de stratégie utilise les alertes de Microsoft Defender pour point de terminaison pour fournir des informations sur des activités liées à la sécurité. Ces activités incluent l’installation d’un programme malveillant ou d’autres applications potentiellement dangereuses par un utilisateur et la désactivation de fonctionnalités de sécurité sur son appareil. En utilisant le connecteur [Microsoft 365 RH](import-hr-data.md) ou l’option pour surveiller automatiquement la suppression de compte utilisateur dans Azure Active Directory pour votre organisation, ce modèle commence l’attribution de scores pour les indicateurs de risque liés à ces activités de sécurité et la façon dont elles se mettent en corrélation avec le statut professionnel de l’utilisateur.

Microsoft Defender pour point de terminaison doit être configuré dans votre organisation et vous devez activer Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Microsoft Defender pour importer les alertes de violation de la sécurité. Pour plus d’informations sur la configuration de Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes, consultez [Configurer des fonctionnalités avancées dans Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="security-policy-violations-by-priority-users-preview"></a>Violations de la stratégie de sécurité par des utilisateurs prioritaires (préversion)

La protection contre des violations de sécurité pour les utilisateurs de votre organisation peut dépendre de leur fonction, du niveau d’accès aux informations sensibles et de l’historique des risques. En raison de l’impact significatif des violations de sécurité par des utilisateurs prioritaires sur les zones critiques de votre organisation, ce modèle de stratégie commence l’attribution de scores sur ces indicateurs et utilise les alertes de Microsoft Defender pour point de terminaison pour fournir des informations sur des activités liées à la sécurité pour ces utilisateurs. Ces activités peuvent inclure l’installation d’un programme malveillant ou d’autres applications potentiellement dangereuses par des utilisateurs prioritaires et la désactivation de fonctionnalités de sécurité sur leur appareil. Les utilisateurs prioritaires sont définis dans les groupes d’utilisateurs prioritaires configurés dans la zone des paramètres de la gestion des risques internes.

Microsoft Defender pour point de terminaison doit être configuré dans votre organisation et vous devez activer Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Microsoft Defender pour importer les alertes de violation de la sécurité. Pour plus d’informations sur la configuration de Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes, consultez [Configurer des fonctionnalités avancées dans Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center). De plus, vous devez affecter les groupes d’utilisateurs prioritaires créés dans la **Gestion des risques internes** > **Paramètres** > **Groupes d’utilisateurs prioritaires** à la stratégie.

### <a name="security-policy-violations-by-disgruntled-users-preview"></a>Violations de stratégie de sécurité par un utilisateur mécontent (préversion)

Les utilisateurs qui font l’expérience de facteurs de stress professionnels peuvent constituer un risque plus élevé pour les violations de stratégie de sécurité malveillantes ou involontaires. Ces facteurs de stress peuvent inclure le placement d’un utilisateur dans un plan d’amélioration des performances, un état d’évaluation médiocre des performances ou une rétrogradation de sa fonction actuelle. Ce modèle de stratégie commence l’attribution de scores en fonction de ces indicateurs et des activités associées à ces événements pour ces utilisateurs.

Lorsque vous utilisez ce modèle, vous pouvez également configurer un connecteur Microsoft 365 RH pour importer périodiquement des notifications d’amélioration des performances, des états d’évaluation médiocres des performances ou des informations sur les changements du niveau des tâches pour les utilisateurs de votre organisation. Consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) pour obtenir des conseils détaillés pour configurer le connecteur Microsoft 365 RH au sein de votre organisation.

Microsoft Defender pour point de terminaison doit également être configuré dans votre organisation et vous devez activer Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Microsoft Defender pour importer les alertes de violation de la sécurité. Pour plus d’informations sur la configuration de Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes, consultez [Configurer des fonctionnalités avancées dans Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="policy-template-prerequisites-and-triggering-events"></a>Conditions requises du modèle de stratégie et événements déclencheurs

En fonction du modèle choisi pour une stratégie de gestion des risques internes, les événements déclencheurs et les conditions requises de la stratégie varient. Les événements déclencheurs sont des conditions requises qui déterminent si un utilisateur est actif pour une stratégie de gestion des risques internes. Si un utilisateur est ajouté à une stratégie de gestion des risques internes, mais qu’il n’a aucun événement déclencheur, l’activité de l’utilisateur n’est pas évaluée par la stratégie, à moins qu’il ne soit manuellement ajouté au tableau de bord des utilisateurs. Les conditions requises de stratégie sont des éléments obligatoires pour que la stratégie reçoive les signaux ou les activités nécessaires pour évaluer les risques.

Le tableau suivant répertorie les événements déclencheurs et les conditions requises pour les stratégies créées à partir de chaque modèle de stratégie de gestion des risques internes :

| **Modèle de stratégie** | **Événements déclencheurs pour les stratégies** | **Conditions préalables** |
| :------------------ | :--------------------------------- | :---------------- |
| Vol de données par des employés quittant votre organisation | Indicateur de date de démission ou de licenciement du connecteur RH | (facultatif) Connecteur Microsoft 365 RH configuré pour les indicateurs de date de démission ou de licenciement ou l’intégration Azure Active Directory activée |
| Fuites de données générales | Activité de stratégie de fuite de données qui crée une alerte de gravité élevée | (facultatif) Stratégie DLP configurée pour les alertes de gravité élevée ou un événement déclencheur d’exfiltration des données intégré |
| Fuites de données par des utilisateurs prioritaires | L’activité de stratégie de fuite de données qui crée une alerte de *Gravité élevée* ou des événements déclencheurs d’exfiltration intégrés | (facultatif) Stratégie DLP configurée pour les alertes de gravité élevée <br><br> Groupes d’utilisateurs prioritaires configurés dans les paramètres de risque interne |
| Fuites de données provoquées par un utilisateur mécontent | Amélioration des performances, performances médiocres ou indicateurs de changement du niveau des tâches à partir du connecteur RH | Connecteur Microsoft 365 RH configuré pour les indicateurs de mécontentement |
| Violations générales de la stratégie de sécurité | Évasion défensive des contrôles de sécurité ou programme indésirable détecté par Microsoft Defender pour point de terminaison | Abonnement actif Microsoft Defender pour point de terminaison <br><br> Intégration de Microsoft Defender pour point de terminaison avec le Centre de conformité Microsoft 365 configuré |
| Violations de stratégie de sécurité par des utilisateurs quittant l’entreprise | Indicateurs de date de démission ou de licenciement du connecteur RH ou suppression de compte Azure Active Directory | (facultatif) Connecteur Microsoft 365 RH configuré pour les indicateurs de date de démission ou de licenciement <br><br> Abonnement actif Microsoft Defender pour point de terminaison <br><br> Intégration de Microsoft Defender pour point de terminaison avec le Centre de conformité Microsoft 365 configuré |
| Violations de la stratégie de sécurité par des utilisateurs prioritaires | Évasion défensive des contrôles de sécurité ou programme indésirable détecté par Microsoft Defender pour point de terminaison | Abonnement actif Microsoft Defender pour point de terminaison <br><br> Intégration de Microsoft Defender pour point de terminaison avec le Centre de conformité Microsoft 365 configuré <br><br> Groupes d’utilisateurs prioritaires configurés dans les paramètres de risque interne |
| Violations de stratégie de sécurité par un utilisateur mécontent | Amélioration des performances, performances médiocres ou indicateurs de changement du niveau des tâches à partir du connecteur RH | Connecteur Microsoft 365 RH configuré pour les indicateurs de mécontentement <br><br> Abonnement actif Microsoft Defender pour point de terminaison <br><br> Intégration de Microsoft Defender pour point de terminaison avec le Centre de conformité Microsoft 365 configuré |

## <a name="prioritize-content-in-policies"></a>Hiérarchiser le contenu dans les stratégies

Prise en charge des stratégies de gestion des risques internes spécifiant une priorité élevée pour le contenu en fonction de son emplacement de stockage et de sa classification. La spécification du contenu comme prioritaire augmente le score de risque pour toute activité associée, ce qui à son tour augmente la possibilité de générer une alerte à gravité élevée. Certaines activités ne génèrent toutefois aucune alerte, sauf si le contenu associé contient des types d’information sensible personnalisés ou intégrés ou s’il a été spécifié comme prioritaire dans la stratégie.

Par exemple, votre organisation dispose d’un site SharePoint dédié pour un projet hautement confidentiel. Les fuites de données concernant les informations dans ce site SharePoint peuvent compromettre le projet et avoir un impact significatif sur sa réussite. En classant ce site SharePoint dans une stratégie de fuites de données, les scores de risque pour les activités éligibles sont automatiquement augmentés. Cette définition de priorités augmente les chances que ces activités génèrent une alerte de risque interne et hausse le niveau de gravité de l’alerte.

Lorsque vous créez une stratégie de gestion des risques internes dans l’Assistant stratégie, vous pouvez choisir parmi les priorités suivantes :

- **Sites SharePoint** : toute activité associée avec tous les types de fichiers dans les sites SharePoint définis se voit attribuer un score de risque plus élevé. Les utilisateurs qui configurent la stratégie et sélectionnent des sites Share Point prioritaires peuvent sélectionner SharePoint sites à qui ils ont l’autorisation d’accéder. Si SharePoint sites ne sont pas disponibles pour la sélection dans la stratégie par l’utilisateur actuel, un autre utilisateur avec les autorisations requises peut sélectionner les sites pour la stratégie ultérieurement ou l’utilisateur actuel doit avoir accès aux sites requis.
- **Types d’information sensible** : toute activité associée au contenu qui contient des [types d’information sensible](sensitive-information-type-entity-definitions.md) se voit attribuer un score de risque plus élevé.
- **Étiquettes de confidentialité** : toute activité associée au contenu sur lequel des [étiquettes de confidentialité](sensitivity-labels.md) sont appliquées se voit attribuer un score de risque plus élevé.

## <a name="sequence-detection-preview"></a>Détections de séquence (préversion)

Des activités à risque peuvent ne pas se produire en tant qu’événements isolés. Ces risques font fréquemment partie d’une séquence d’événements plus importante. Une séquence est un groupe d’au moins deux activités utilisateur effectuées l’une après l’autre pouvant suggérer un risque élevé. L’identification de ces activités associées est un élément important de l’évaluation du risque global. Quand une détection de séquence est activée pour des stratégies de vol de données ou de fuites de données, les informations des activités sur les informations de la séquence s’affichent dans l’onglet **Activité utilisateur** dans le cas de gestion des risques internes. Les modèles de stratégie suivants prennent en charge la détection de séquence :

- Vol de données par des employés quittant votre organisation
- Fuites de données générales
- Fuites de données par des utilisateurs prioritaires
- Fuites de données provoquées par un utilisateur mécontent

Ces stratégies de gestion des risques internes peuvent utiliser des indicateurs spécifiques et l’ordre dans lequel elles se produisent pour détecter chaque étape dans une séquence de risque. Les noms de fichiers sont utilisés lors du mappage des activités dans une séquence. Ces risques sont organisés en quatre principales catégories d’activité :

- **Collection** : ces signaux de catégorie se concentrent sur les activités de téléchargement par des utilisateurs de stratégie dans l’étendue. Le téléchargement de fichiers de sites SharePoint est un exemple d’activité dans cette catégorie.
- **Exfiltration** : ces signaux de catégorie se concentrent sur le partage ou l’extraction d’activités vers des sources internes ou externes par des utilisateurs de stratégie dans l’étendue. L’envoi d’e-mails avec des pièces jointes de votre organisation vers des destinataires externes est un exemple d’activité dans cette catégorie.
- **Dissimulation** : ces signaux de catégorie se concentrent sur le masquage des activités à risque par des utilisateurs de stratégie dans l’étendue. Renommer des fichiers sur un appareil est un exemple d’activité dans cette catégorie.
- **Nettoyage** : ces signaux de catégorie se concentrent sur la suppression des activités par des utilisateurs de stratégie dans l’étendue. La suppression des fichiers d’un appareil est un exemple d’activité dans cette catégorie.

> [!NOTE]
> La détection de séquence utilise des indicateurs activés dans les paramètres généraux pour la gestion des risques internes et les indicateurs sélectionnés dans une stratégie. Si les indicateurs appropriés ne sont pas sélectionnés, la détection de séquence ne fonctionne pas.

Vous pouvez personnaliser les paramètres de seuil individuel pour chaque type de détection de séquence lorsqu’ils sont configurés dans la stratégie. Ces paramètres de seuil ajustent les alertes en fonction du volume de fichiers associés à la séquence.

Si vous souhaitez en savoir plus sur la gestion de la détection de séquence dans l’affichage **Activité utilisateur**, consultez [Cas de gestion des risques internes : activité utilisateur](insider-risk-management-cases.md#user-activity).

## <a name="cumulative-exfiltration-detection-preview"></a>Détection d’exfiltration cumulée (préversion)

Les indicateurs de risque interne permettent d’identifier des niveaux inhabituels de risque lorsqu’ils sont évalués quotidiennement pour des utilisateurs étant dans l’étendue des stratégie de risque interne. La détection d’exfiltration cumulée utilise des modèles d’apprentissage automatique pour vous aider à identifier des activités d’exfiltration utilisateur qui dépassent les moyennes de l’organisation lors de leur mesure au fil du temps et sur plusieurs types d’activité d’exfiltration. Les enquêteurs et analystes de gestion des risques internes peuvent utiliser les informations de la détection d’exfiltration cumulée pour leur permettre d’identifier des activités d’exfiltration qui ne génèrent généralement aucune alerte , mais qui se situent au-dessus de ce qui est standard pour leur organisation. Des exemples peuvent correspondre à des utilisateurs sortants qui exfiltrent lentement des données sur un certain nombre de jours ou lorsque des utilisateurs partagent, à maintes reprises et plus que d’ordinaire pour votre organisation, des données sur plusieurs canaux.

La détection d’exfiltration cumulée est activée par défaut lors de l’utilisation des modèles de stratégie suivants :

- Vol de données par des employés quittant votre organisation
- Fuites de données générales
- Fuites de données par des utilisateurs prioritaires
- Fuites de données provoquées par un utilisateur mécontent

> [!NOTE]
> La détection d’exfiltration cumulée utilise des indicateurs d’exfiltration activés dans les paramètres généraux pour la gestion des risques internes et les indicateurs d’exfiltration sélectionnés dans une stratégie. À ce titre, la détection d’exfiltration cumulée est uniquement évaluée pour les indicateurs d’exfiltration nécessaires sélectionnés. Les activités d’exfiltration cumulatives pour les étiquettes [de sensibilité](sensitivity-labels.md) configurées dans le contenu prioritaire génèrent des scores de risque plus élevés.

Quand une détection d’exfiltration cumulée est activée pour des stratégies de vol de données ou de fuite de données, les informations des activités d’exfiltration cumulée s’affichent dans l’onglet **Activité utilisateur** dans le cas de gestion des risques internes.

Si vous souhaitez en savoir plus sur la gestion de l’activité utilisateur, consultez [Cas de gestion des risques internes : activités utilisateur](insider-risk-management-cases.md#user-activity).

## <a name="policy-health"></a>État de la stratégie

L’état d’intégrité de la stratégie vous fournit des informations sur les problèmes potentiels avec vos stratégies de gestion des risques internes. La colonne État sur l’onglet Stratégie vous avertit sur les problèmes de stratégie qui peuvent empêcher l’activité utilisateur d’être signalée ou la raison pour laquelle le nombre d’alertes sur l’activité est inhabituel. L’état de l’intégrité de la stratégie peut également confirmer que la stratégie est intègre et ne requiert aucune attention ni modification de la configuration.

S’il existe des problèmes avec la stratégie, l’état d’intégrité de la stratégie affiche des notifications de recommandation et d’avertissement pour vous aider à prendre des mesures pour résoudre les problèmes de la stratégie. Ces notifications peuvent vous permettre de résoudre les problèmes suivants :

- Stratégies avec configuration incomplète. Ces problèmes peuvent comprendre des groupes ou des utilisateurs manquants dans la stratégie ou d’autres étapes de configuration de la stratégie inachevées.
- Stratégies avec des problèmes de configuration de l’indicateur. Les indicateurs sont des éléments importants de chaque stratégie. Si les indicateurs ne sont pas configurés, ou si trop peu d’indicateurs sont sélectionnés, la stratégie peut ne pas évaluer comme prévu les activités à risque.
- Les déclencheurs de stratégie ne fonctionnent pas ou la configuration requise de déclencheur de stratégie n’est pas correctement configurée. La fonctionnalité de la stratégie peut dépendre d’autres services ou d’exigences de configuration pour détecter efficacement les événements déclencheurs permettant d’activer l’activité de score de risque aux utilisateurs dans la stratégie. Ces dépendances peuvent inclure des problèmes avec la configuration du connecteur, le partage d’alerte Microsoft Defender pour point de terminaison ou les paramètres de configuration de la stratégie de protection contre la perte de données.
- Les limites de volume approchent ou dépassent les limites. Les stratégies de gestion des risques internes utilisent les points de terminaison et les services Microsoft 365 pour agréger les signaux de l’activité à risque. En fonction du nombre d’utilisateurs dans vos stratégies, les limites de volume peuvent retarder l’identification et le signalement des activités à risque. Apprenez-en plus sur ces limites dans la section sur les limites du modèle de stratégie de cet article.

Pour afficher rapidement l’état d’intégrité d’une stratégie, naviguez vers l’onglet Stratégie et la colonne État. Vous verrez à cet emplacement les options suivantes de l’état d’intégrité de la stratégie pour chacune d’entre elles :

- Intégrité : aucun problème n’a été identifié avec la stratégie.
- Recommandations : il existe des problèmes avec la stratégie qui l’empêchent de fonctionner comme prévu.
- Avertissements : il existe des problèmes avec la stratégie qui l’empêchent d’identifier des activités à risque.

Pour d’autres détails concernant les avertissements et les recommandations, sélectionnez une stratégie sur l’onglet **Stratégie** pour ouvrir la carte détaillée de la stratégie. Des informations supplémentaires sur les avertissements et les recommandations, notamment des conseils sur la façon de traiter ces problèmes, s’affichent dans la section Notification de la carte détaillées.

![L’état de la stratégie de gestion des risques internes.](../media/insider-risk-policy-health.png)

### <a name="notification-messages"></a>Les messages de notification

Utilisez le tableau suivant pour en savoir davantage sur les notifications d’avertissement et de recommandation, ainsi que les mesures à prendre pour résoudre des problèmes potentiels.

|**Messages de notification**|**Modèles de stratégie**|**Causes/Essayer cette action de correction**|
|:------------------------|:-------------------|:---------------------------|
| La stratégie n’affecte aucun score de risque à l’activité | Tous les modèles de stratégie | Vous voudrez peut-être examiner l’étendue de votre stratégie et la configuration de l’événement déclencheur pour que la stratégie puisse attribuer des scores de risque à une activité <br><br> 1. Examinez les utilisateurs sélectionnés pour la stratégie. Si vous avez peu d’utilisateurs sélectionnés, vous voudrez peut-être sélectionner d’autres utilisateurs. <br> 2. Si vous utilisez un connecteur RH, vérifiez que votre connecteur RH envoie les correctes informations. <br> 3. Si vous utilisez une stratégie DLP comme événement déclencheur, vérifiez la configuration de votre stratégie DLP pour vous assurer qu’elle est configurée pour être utilisée dans cette stratégie. <br> 4. Pour les stratégies de violation de la sécurité, examinez l’état du triage d’alerte Microsoft Defender pour point de terminaison sélectionné dans les paramètres de risque interne > détections intelligentes. Confirmez que le filtre d’alerte n’est pas trop limité. |
| La stratégie n’a généré aucune alerte | Tous les modèles de stratégie | Vous voudrez peut-être examiner la configuration de votre stratégie pour que vous analysiez l’attribution de scores de l’activité qui vous intéresse. <br><br> 1. Confirmez la sélection des indicateurs pour lesquels vous souhaitez établir un score. Plus vous aurez sélectionné des indicateurs, plus les activités se verront attribuer des scores de risque. <br> 2. Examinez la personnalisation de seuil pour la stratégie. Si le seuil sélectionné ne s’aligne pas avec la tolérance au risque de votre organisation, ajustez les sélections pour que les alertes soient créées en fonction de vos seuils favoris. <br> 3. Examinez les utilisateurs et groupes sélectionnés pour la stratégie. Confirmez que vous avez sélectionné tous les groupes et utilisateurs applicables. <br> 4. Pour les stratégies de violation de la sécurité, confirmez que vous avez sélectionné l’état de triage de l’alerte pour laquelle vous souhaitez établir un score pour les alertes Microsoft Defender pour point de terminaison dans les Détections intelligentes des paramètres.|
| Aucun utilisateur ou groupe n’est inclus dans cette stratégie | Tous les modèles de stratégie | Les utilisateurs et groupes ne sont pas affectés à la stratégie. <br><br> Modifiez votre stratégie, puis sélectionnez les utilisateurs ou groupes pour la stratégie. |
| Aucun indicateur n’a été sélectionné pour cette stratégie | Tous les modèles de stratégie | Aucun indicateur n’a été sélectionné pour la stratégie <br><br> Modifiez votre stratégie, puis sélectionnez les indicateurs de stratégie appropriés pour la stratégie. |
| Aucun groupe d’utilisateurs prioritaires n’est inclus dans cette stratégie | -Fuites de données par des utilisateurs prioritaires <br> -Violations de la stratégie de sécurité par des utilisateurs prioritaires | Les groupes d’utilisateurs prioritaires ne sont pas affectés à la stratégie. <br><br> Configurez les groupes d’utilisateurs prioritaires dans les paramètres de la gestion des risques internes, puis affectez des groupes d’utilisateurs prioritaires à la stratégie. |
| Aucun événement déclencheur n’a été sélectionné pour cette stratégie | Tous les modèles de stratégie | Un événement déclencher n’est pas configuré pour la stratégie <br><br> Les scores de risque ne seront affectés aux activités utilisateur que lorsque vous modifierez la stratégie et sélectionnerez un événement déclencheur. |
| Le connecteur HR n’est pas configuré ou ne fonctionne pas comme prévu | -Vol de données par un employé quittant votre organisation <br> -Violations de stratégie de sécurité par un utilisateur quittant l’entreprise <br> -Fuites de données provoquées par un utilisateur mécontent <br> -Violations de stratégie de sécurité par des utilisateurs mécontents | Il existe un problème avec le connecteur RH. <br><br> 1. Si vous utilisez un connecteur RH, vérifiez que votre connecteur RH envoie les correctes informations <br><br> OU <br><br> 2. Sélectionnez l’événement déclencheur supprimé du compte Azure AD. |
| Aucun appareil n’est intégré | -Vol de données par des employés quittant votre organisation <br> -Fuites de données générales <br> -Fuites de données provoquées par un utilisateur mécontent <br> -Fuites de données par des utilisateurs prioritaires | Les indicateurs d’appareil sont sélectionnés, mais aucun appareil n’est intégré à Microsoft 365 <br><br> Vérifiez que les appareils sont intégrés et répondent à la configuration requise. |
| Le connecteur RH n’a pas chargé de données récemment | -Vol de données par un employé quittant votre organisation <br> -Violations de stratégie de sécurité par un utilisateur quittant l’entreprise <br> -Fuites de données provoquées par un utilisateur mécontent <br> -Violations de stratégie de sécurité par des utilisateurs mécontents | Le connecteur RH n’a pas importé de données en plus de 7 jours. <br><br> Vérifiez que votre connecteur RH est correctement configuré et qu’il envoie des données. |
| Nous ne pouvons pas vérifier l’état de votre connecteur RH pour le moment. Veuillez revérifier plus tard | -Vol de données par un employé quittant votre organisation <br> -Violations de stratégie de sécurité par un utilisateur quittant l’entreprise <br> -Fuites de données provoquées par un utilisateur mécontent <br> -Violations de stratégie de sécurité par des utilisateurs mécontents | La solution de gestion des risques internes ne peut pas vérifier l’état de votre connecteur RH. <br><br> Vérifiez que votre connecteur RH est correctement configuré et qu’il envoie des données, ou revenez plus tard, puis vérifiez l’état de la stratégie.  |
| La stratégie DLP n’est pas sélectionnée comme événement déclencheur | -Fuites de données générales <br> -Fuites de données par des utilisateurs prioritaires | Une stratégie DLP n’as pas été sélectionnée comme événement déclencheur ou la stratégie DLP sélectionnée a été supprimée. <br><br> Modifiez la stratégie, puis sélectionner une stratégie DLP active ou « L’utilisateur effectue une activité d’exfiltration » comme événement déclencheur dans la configuration de stratégie. |
| La stratégie DLP utilisée dans cette stratégie est désactivée | -Fuites de données générales <br> -Fuites de données par des utilisateurs prioritaires | La stratégie DLP utilisée dans cette stratégie est désactivée. <br><br> 1. Activez la stratégie DLP affectée à cette stratégie. <br><br> OU <br><br> 2. Modifiez cette stratégie, puis sélectionner une nouvelle stratégie DLP active ou « L’utilisateur effectue une activité d’exfiltration » comme événement déclencheur dans la configuration de stratégie. |
| La stratégie DLP ne répond pas aux exigences | -Fuites de données générales <br> -Fuites de données par des utilisateurs prioritaires | Les stratégies DLP utilisées comme événements déclencheurs doivent être configurées pour générer des alertes de gravité élevée. <br><br>  1. Modifiez votre stratégie DLP pour affecter des alertes applicables comme *Gravité élevée*. <br><br> OU <br><br> 2. Modifiez cette stratégie, puis sélectionnez *L’utilisateur effectue une activité d’exfiltration* comme événement déclencheur. |
| Votre organisation n’a pas d’abonnement Microsoft Defender pour point de terminaison | -Violations générales de la stratégie de sécurité <br> -Violations de stratégie de sécurité par des utilisateurs quittant l’entreprise <br> -Violations de stratégie de sécurité par des utilisateurs mécontents <br> -Violations de la stratégie de sécurité par des utilisateurs prioritaires | Aucun abonnement Microsoft Defender pour point de terminaison n’a été détecté pour votre organisation. <br><br> Tant qu’un abonnement Microsoft Defender pour point de terminaison n’a pas été ajouté, ces stratégies n’attribuent aucun score de risque à l’activité utilisateur. |
| Les alertes Microsoft Defender pour point de terminaison ne sont pas partagées avec le Centre de conformité | -Violations générales de la stratégie de sécurité <br> -Violations de stratégie de sécurité par des utilisateurs quittant l’entreprise <br> -Violations de stratégie de sécurité par des utilisateurs mécontents <br> -Violations de la stratégie de sécurité par des utilisateurs prioritaires | Les alertes Microsoft Defender pour point de terminaison ne sont pas partagées avec le Centre de conformité. <br><br> Configurez le partage des alertes de Microsoft Defender pour point de terminaison. |
| Vous êtes proche de la limite maximum d’utilisateurs activement évalués pour ce modèle de stratégie. | Tous les modèles de stratégie | Chaque modèle de stratégie a un nombre maximum d’utilisateurs dans l’étendue. Consultez les détails de la section limite du modèle. <br><br> Examinez les utilisateurs dans l’onglet Utilisateurs, puis supprimez tout utilisateur ne nécessitant plus d’évaluation. |

## <a name="policy-template-limits"></a>Limites du modèle de stratégie

Les modèles de stratégie de gestion des risques internes utilisent des limites pour gérer le volume et le taux de traitement des activités de risque utilisateur dans l’étendue et la façon dont ce processus est intégré avec les services Microsoft 365 pris en charge. Chaque modèle de stratégie a un nombre maximum d’utilisateurs auquel des scores de risque peuvent être activement affectés pour la stratégie qu’il peut prend en charge et traiter efficacement, ainsi que signaler des activités à risque. Les utilisateurs dans l’étendue sont des utilisateurs avec événements déclencheurs for la stratégie.

La limite de chaque stratégie est calculée en fonction du nombre total d’utilisateurs uniques recevant des scores de risque par type de modèle de stratégie. Si le nombre d’utilisateurs pour un type de modèle de stratégie est proche ou dépasse la limite utilisateur, les performances de la stratégie seront réduites. Pour afficher le nombre actuel d’utilisateurs pour une stratégie, naviguez vers l’onglet Stratégie et la colonne Utilisateurs dans l’étendue. Vous pouvez avoir jusqu’à cinq stratégies pour un modèle de stratégie. Ces limites maximales s’appliquent aux utilisateurs sur toutes les stratégies utilisant un modèle de stratégie donné.

Utilisez le tableau suivant pour déterminer le nombre maximum d’utilisateurs dans l’étendue pris en charge pour chaque modèle de stratégie :

|**Modèle de stratégie**|**Nombre maximum actuel d’utilisateurs dans l’étendue**|
|:------------------|:--------------------------------|
| Fuite de données générales | 15 000 |
| Fuite de données provoquées par un utilisateur mécontent | 7 500 |
| Fuite de données par des utilisateurs prioritaires | 1 000 |
| Vol de données par des employés quittant votre organisation | 20 000 |
| Violations générales de la stratégie de sécurité | 1 000 |
| Violation de la stratégie de sécurité par des utilisateurs prioritaires | 1 000 |
| Violations de stratégie de sécurité par des utilisateurs quittant l’entreprise | 15 000 |
| Violations de stratégie de sécurité par des utilisateurs mécontents | 7 500 |

## <a name="create-a-new-policy"></a>Créer une stratégie

Pour créer une stratégie de gestion des risques internes, vous pouvez utiliser l’Assistant stratégie dans la solution de **Gestion des risques internes** dans le Centre de conformité Microsoft 365.

Achevez les étapes suivantes pour créer une stratégie :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **Gestion des risques internes**, puis sélectionnez l’onglet **Stratégies**.
2. Sélectionnez **Créer une stratégie** pour ouvrir l’Assistant stratégie.
3. Sur la page **Modèle de stratégie**, choisissez une catégorie de stratégie, puis sélectionnez le modèle pour la nouvelle stratégie. Ces modèles sont constitués d'indicateurs et de conditions définissant les activités à risque que vous voulez détecter et examiner. Examinez les conditions préalables du modèle, les événements déclencheurs et les activités détectées pour confirmer que ce modèle de stratégie correspond à vos besoins.

    > [!IMPORTANT]
    > Certains modèles de stratégie ont des conditions préalables devant être configurées pour que la stratégie génère des alertes pertinentes. Si vous n’avez pas configuré les conditions préalables applicables de la stratégie, consultez **Étape 4** ci-dessus.

4. Sélectionnez **Suivant** pour continuer.
5. Dans la page **Nom et description**, complétez les champs suivants :
    - **Nom (obligatoire)** : entrez un nom convivial pour la stratégie. Ce nom ne peut plus être modifié une fois la stratégie créée.
    - **Description (facultatif)** : entrez une description pour la stratégie.

6. Sélectionnez **Suivant** pour continuer.
7. Sur la page **Utilisateurs et groupes**, sélectionnez **Inclure tous les utilisateurs et groupes** ou **Inclure des utilisateurs et groupes spécifiques** pour définir les utilisateurs ou groupes inclus dans la stratégie ou, si vous avez choisir un modèle basé sur les utilisateurs prioritaires, sélectionnez **Ajouter ou modifier des groupes d’utilisateurs prioritaires**. La sélection de **Inclure tous les utilisateurs et groupes** permettra de rechercher les événements déclencheurs pour tous les utilisateurs et groupes dans votre organisation pour commencer à établir des scores de risque pour la stratégie. La sélection de **Inclure des utilisateurs et groupes spécifiques** vous permettra de définir les utilisateurs et groupes à affecter à la stratégie.
8. Sélectionnez **Suivant** pour continuer.
9. Sur la page **Contenu à prioriser**, vous pouvez attribuer (le cas échéant) les sources à hiérarchiser, ce qui augmente les possibilités de générer une alerte de gravité élevée pour ces sources. Sélectionnez l'une des options suivantes :

    - **Je veux indiquer des sites SharePoint, étiquettes de confidentialité et/ou des types d’information sensible comme contenu prioritaire**. La sélection de cette option active les pages détaillées dans l’Assistant pour configurer ces canaux.
    - **Je ne souhaite pas indiquer de contenu prioritaire pour le moment (vous pourrez le faire après la création de la stratégie)**. La sélection de cette option permettra d’ignorer les pages détaillées du canal dans l’Assistant.

10. Sélectionnez **Suivant** pour continuer.

11. Si vous avez sélectionné **Je veux spécifier les sites SharePoint, les étiquettes de confidentialité et/ou les types d’information sensible comme contenu prioritaire** à l’étape précédente, les pages détaillées s’affichent pour les *Sites SharePoint*, les *Types d’information sensible* et les *Étiquettes de confidentialité*. Utilisez ces pages détaillées pour définir les sites SharePoint, les types d’information sensible et les étiquettes de confidentialité à hiérarchiser dans la stratégie.

    - **Sites SharePoint** : sélectionnez **Ajouter un site SharePoint**, puis sélectionnez les sites SharePoint auxquels vous avez accès et que vous souhaitez classer. Par exemple, *« groupe1@contoso.sharepoint.com/sites/group1 »*.
    - **Type d’information sensible** : sélectionnez **Ajouter un type d’information confidentielle**, puis les types de confidentialité que vous souhaitez classer. Par exemple, *« Numéro de compte bancaire américain »* et *« Numéro de carte de crédit »*.
    - **Étiquette de confidentialité** : sélectionnez **Ajouter une étiquette de confidentialité**, puis les étiquettes que vous souhaitez classer. Par exemple, *« Confidentiel »* et *« Secret »*.

    >[!NOTE]
    >Les utilisateurs qui configurent la stratégie et sélectionnent des sites Share Point prioritaires peuvent sélectionner SharePoint sites à qui ils ont l’autorisation d’accéder. Si SharePoint sites ne sont pas disponibles pour la sélection dans la stratégie par l’utilisateur actuel, un autre utilisateur avec les autorisations requises peut sélectionner les sites pour la stratégie ultérieurement ou l’utilisateur actuel doit avoir accès aux sites requis.

12. Sélectionnez **Suivant** pour continuer.
13. Sur la page **Indicateurs et événements déclencheurs**, les [indicateurs](insider-risk-management-settings.md#indicators) définis s’affichent comme disponibles sur la page **Paramètres de risque interne** > **Indicateurs**. Si vous avez sélectionné le modèle *Fuites de données* au début de l’Assistant, vous devez sélectionner une stratégie DLP à partir de la liste déroulante **Stratégie DLP** pour activer les indicateurs déclencheurs pour la stratégie ou sélectionner l’événement déclencheur intégré.

    > [!IMPORTANT]
    > Si les indicateurs sur cette page ne peuvent pas être sélectionnés, vous sélectionner les indicateurs que vous souhaitez activer pour toutes les stratégies. Vous pouvez utiliser le bouton **Activer les indicateurs** dans l’Assistant ou sélectionner des indicateurs sur la page **Gestion des risques internes** > **Paramètres** > **Indicateurs de stratégie**.

    Sélectionnez les indicateurs que vous souhaitez appliquer à la stratégie. Si vous préférez ne pas utiliser les paramètres de seuil de stratégie par défaut pour ces indicateurs, désactivez **Utiliser les seuils par défaut recommandés par Microsoft**, puis entrez les valeurs de seuil pour chaque indicateur sélectionné.

    - Si vous avez sélectionné au moins un indicateur *Office* ou *Appareil*, choisissez les **Boosters de score de risque** selon le cas. Les boosters de score de risque sont uniquement applicables pour les indicateurs sélectionnés.
    - Si vous avez sélectionné un modèle de stratégie *Vol de données* ou *Fuites de données*, choisissez au moins une des méthodes **Détection de séquence** et une méthode **Détection d’exfiltration cumulée** à appliquer à la stratégie.

14. Sélectionnez **Suivant** pour continuer.
15. Sur la page **Seuils d’indicateur**, sélectionnez l’option pour utiliser les seuils d’indicateur par défaut ou pour spécifier des seuils personnalisés pour des indicateurs individuels. Pour chaque indicateur, choisissez le niveau approprié pour générer le niveau souhaité des alertes d’activité.
16. Sélectionnez **Suivant** pour continuer.
17. Sur la page **Évaluation**, examinez les paramètres choisis pour la stratégie et toute suggestion ou tout avertissement pour vos sélections. Sélectionnez **Modifier** pour changer toute valeur de stratégie ou **Soumettre** pour créer et activer la stratégie.

## <a name="update-a-policy"></a>Mettre à jour une stratégie

Pour mettre à jour une stratégie existante de gestion des risques internes, vous pouvez utiliser l’Assistant stratégie dans la solution de **Gestion des risques internes** dans le Centre de conformité Microsoft 365.

Finalisez les étapes suivantes pour gérer une stratégie existante :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **Gestion des risques internes**, puis sélectionnez l’onglet **Stratégies**.
2. Dans le tableau de bord des stratégies, sélectionnez la stratégie que vous souhaitez gérer.
3. Sur la page détaillée de la stratégie, sélectionnez **Modifier une stratégie**.
4. Dans l’Assistant stratégie, vous ne pouvez pas modifier ce qui suit :
    - **Modèle de stratégie** : le modèle utilisé pour définir le type des indicateurs de risque contrôlés par la stratégie.
    - **Nom** : nom convivial de la stratégie
5. Sur la page **Nom et description**, mettez à jour la description de la stratégie dans le champ **Description**.
6. Sélectionnez **Suivant** pour continuer.
7. Sur la page **Utilisateurs et groupes**, sélectionnez **Inclure tous les utilisateurs et groupes** ou **Inclure des utilisateurs et groupes spécifiques** pour définir les utilisateurs ou groupes inclus dans la stratégie ou, si vous avez choisir un modèle basé sur les utilisateurs prioritaires, sélectionnez **Ajouter ou modifier des groupes d’utilisateurs prioritaires**. La sélection de **Inclure tous les utilisateurs et groupes** permettra de rechercher les événements déclencheurs pour tous les utilisateurs et groupes dans votre organisation pour commencer à établir des scores de risque pour la stratégie. La sélection de **Inclure des utilisateurs et groupes spécifiques** vous permettra de définir les utilisateurs et groupes à affecter à la stratégie.
8. Sélectionnez **Suivant** pour continuer.
9. Sur la page **Contenu à prioriser**, vous pouvez attribuer (le cas échéant) les sources à hiérarchiser, ce qui augmente les possibilités de générer une alerte de gravité élevée pour ces sources. Sélectionnez l'une des options suivantes :

    - **Je veux indiquer des sites SharePoint, étiquettes de confidentialité et/ou des types d’information sensible comme contenu prioritaire**. La sélection de cette option active les pages détaillées dans l’Assistant pour configurer ces canaux.
    - **Je ne souhaite pas indiquer de contenu prioritaire pour le moment (vous pourrez le faire après la création de la stratégie)**. La sélection de cette option permettra d’ignorer les pages détaillées du canal dans l’Assistant.

10. Sélectionnez **Suivant** pour continuer.

11. Si vous avez sélectionné **Je veux spécifier les sites SharePoint, les étiquettes de confidentialité et/ou les types d’information sensible comme contenu prioritaire** à l’étape précédente, les pages détaillées s’affichent pour les *Sites SharePoint*, les *Types d’information sensible* et les *Étiquettes de confidentialité*. Utilisez ces pages détaillées pour définir les sites SharePoint, les types d’information sensible et les étiquettes de confidentialité à hiérarchiser dans la stratégie.

    - **Sites SharePoint** : sélectionnez **Ajouter un site SharePoint**, puis sélectionnez les sites SharePoint auxquels vous avez accès et que vous souhaitez classer. Par exemple, *« groupe1@contoso.sharepoint.com/sites/group1 »*.
    - **Type d’information sensible** : sélectionnez **Ajouter un type d’information confidentielle**, puis les types de confidentialité que vous souhaitez classer. Par exemple, *« Numéro de compte bancaire américain »* et *« Numéro de carte de crédit »*.
    - **Étiquette de confidentialité** : sélectionnez **Ajouter une étiquette de confidentialité**, puis les étiquettes que vous souhaitez classer. Par exemple, *« Confidentiel »* et *« Secret »*.

12. Sélectionnez **Suivant** pour continuer.
13. Sur la page **Indicateurs et événements déclencheurs**, les [indicateurs](insider-risk-management-settings.md#indicators) définis s’affichent comme disponibles sur la page **Paramètres de risque interne** > **Indicateurs**. Si vous avez sélectionné le modèle *Fuites de données* au début de l’Assistant, vous devez sélectionner une stratégie DLP à partir de la liste déroulante **Stratégie DLP** pour activer les indicateurs déclencheurs pour la stratégie ou sélectionner l’événement déclencheur intégré.

    > [!IMPORTANT]
    > Si les indicateurs sur cette page ne peuvent pas être sélectionnés, vous sélectionner les indicateurs que vous souhaitez activer pour toutes les stratégies. Vous pouvez utiliser le bouton **Activer les indicateurs** dans l’Assistant ou sélectionner des indicateurs sur la page **Gestion des risques internes** > **Paramètres** > **Indicateurs de stratégie**.

    Sélectionnez les indicateurs que vous souhaitez appliquer à la stratégie. Si vous préférez ne pas utiliser les paramètres de seuil de stratégie par défaut pour ces indicateurs, désactivez **Utiliser les seuils par défaut recommandés par Microsoft**, puis entrez les valeurs de seuil pour chaque indicateur sélectionné.

    - Si vous avez sélectionné au moins un indicateur *Office* ou *Appareil*, choisissez les **Boosters de score de risque** selon le cas. Les boosters de score de risque sont uniquement applicables pour les indicateurs sélectionnés.
    - Si vous avez sélectionné un modèle de stratégie *Vol de données* ou *Fuites de données*, choisissez au moins une des méthodes **Détection de séquence** et une méthode **Détection d’exfiltration cumulée** à appliquer à la stratégie.

14. Sélectionnez **Suivant** pour continuer.
15. Sur la page **Seuils d’indicateur**, sélectionnez l’option pour utiliser les seuils d’indicateur par défaut ou pour spécifier des seuils personnalisés pour des indicateurs individuels. Pour chaque indicateur, choisissez le niveau approprié pour générer le niveau souhaité des alertes d’activité.
16. Sélectionnez **Suivant** pour continuer.
17. Sur la page **Évaluation**, examinez les paramètres choisis pour la stratégie et toute suggestion ou tout avertissement pour vos sélections. Sélectionnez **Modifier** pour changer toute valeur de stratégie ou **Soumettre** pour créer et activer la stratégie.

## <a name="copy-a-policy"></a>Copier une stratégie

Vous devrez peut-être créer une stratégie similaire à une stratégie existante qui ne nécessite que quelques modifications de configuration. Au lieu de créer une stratégie à partir de zéro, vous pouvez copier une stratégie existante, puis modifier les zones nécessitant une mise à jour dans la nouvelle stratégie.

Finalisez les étapes suivantes pour copier une stratégie existante :

1. Dans le Centre de conformité Microsoft 365, accédez à la gestion des risques internes, puis sélectionnez l’onglet Stratégies.
2. Dans le tableau de bord des stratégies, sélectionnez la stratégie que vous souhaitez copier.
3. Sur la page détaillée de la stratégie, sélectionnez Copier.
4. Dans l’Assistant stratégie, nommez la nouvelle stratégie, puis mettez à jour sa configuration, le cas échéant.

## <a name="immediately-start-scoring-user-activity"></a>Commencez immédiatement à attribuer des scores à l’activité utilisateur

Il peut y avoir des scénarios dans lesquels vous devez immédiatement commencer à attribuer des scores de risque à des utilisateurs en dehors des stratégies de gestion des risques extérieures au flux de travail d’événement déclencheur de gestion des risques internes. Utilisez **Démarrer l’activité d’attribution de score pour les utilisateurs** sur l’onglet **Stratégies** pour ajouter manuellement un utilisateur (ou des utilisateurs) à une ou plusieurs stratégies de risque interne, pendant une certaine période, dans le but de commencer immédiatement l’attribution de score de risque à son activité et pour contourner les conditions requises pour un utilisateur d’avoir un indicateur de déclenchement (tel qu’une correspondance de stratégie DLP). Vous pouvez également ajouter une raison pour l’ajout de l’utilisateur à la stratégie, laquelle s’affiche sur la chronologie d’activité des utilisateurs. Les utilisateurs manuellement ajoutés aux stratégies s’affichent dans le tableau de bord **Utilisateurs** et les alertes sont créées si l’activité respecte les seuils d’alerte de la stratégie.

Certains scénarios dans lesquels vous souhaitez commencer immédiatement à attribuer des scores aux activités utilisateur :

- Lorsque des utilisateurs sont identifiés avec des problèmes de risque et vous souhaitez commencer immédiatement à attribuer des scores de risque à leur activité pour une ou plusieurs de vos stratégies
- Lorsqu’il existe un incident qui peut vous obliger à attribuer immédiatement des scores de risque à l’activité des utilisateurs concernés pour une ou plusieurs de vos stratégies
- Lorsque vous n’avez pas encore configuré votre connecteur RH, mais vous souhaitez commencer à attribuer des scores aux activités des utilisateurs pour les événements RH en chargeant un fichier. csv pour les utilisateurs

> [!NOTE]
> L’affichage des utilisateurs ajoutés manuellement dans le tableau de bord **Utilisateurs** peut prendre plusieurs heures. L’affichage des activités des 90 jours précédents de ces utilisateurs peut prendre jusqu’à 24 heures. Pour afficher des activités pour les utilisateurs manuellement ajoutés, naviguez vers l’onglet **Utilisateurs**, puis sélectionnez l’utilisateur sur le tableau de bord **Utilisateurs**, enfin ouvrez l’onglet **Activité utilisateur** sur le volet d’informations.

Pour commencer manuellement l’activité d’attribution de scores pour les utilisateur dans au moins une stratégie de gestion des risques internes, finalisez les étapes suivantes :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **Gestion des risques internes**, puis sélectionnez l’onglet **Stratégies**.
2. Dans le tableau de bord des stratégies, sélectionnez la ou les stratégies auxquelles vous souhaitez ajouter des utilisateurs.
3. Sélectionnez **Démarrer l’activité d’attribution de scores des utilisateurs**.
4. Dans le **champ Raison** du volet **Ajouter des utilisateurs à plusieurs stratégies**, ajoutez une raison pour l’ajout des utilisateurs.
5. Dans le champ **Cette opération doit durer (choisir entre 5 et 30 jours)**, définissez le nombre de jours pour attribuer un score à l’activité de l’utilisateur pour la stratégie à laquelle il est ajouté.
6. Pour rechercher votre Active Directory pour les utilisateurs, utilisez le champ **Rechercher un utilisateur à ajouter aux stratégies**. Tapez le nom de l’utilisateur que vous souhaitez ajouter aux stratégies. Sélectionnez le nom d’utilisateur, puis répétez pour affecter d’autres utilisateurs aux stratégies. La liste des utilisateurs sélectionnés s’affiche dans la section utilisateurs du volet Ajouter des utilisateurs à plusieurs stratégies.
7. Pour importer une liste d’utilisateurs à ajouter aux stratégies, sélectionnez **Importer** pour importer un fichier .csv (valeurs séparées par une virgule). Le fichier doit être dans le format ci-après et vous devez répertorier les noms de principal de l’utilisateur dans le fichier :

    ```csv
    user principal name
    user1@domain.com
    user2@domain.com
    ```

8. Sélectionnez Ajouter des utilisateurs aux stratégies pour accepter les modifications et ajouter des utilisateurs aux stratégies ou sélectionnez Annuler pour ignorer les modifications et fermer la boîte de dialogue.

## <a name="stop-scoring-users-in-a-policy"></a>Arrêter d’évaluer les utilisateurs dans une stratégie

Pour arrêter l’attribution de score aux utilisateurs dans une stratégie, voir l’article [Utilisateurs de la gestion des risques internes : Supprimer des utilisateurs de l’attribution dans l’étendue aux stratégies](insider-risk-management-users.md#remove-users-from-in-scope-assignment-to-policies).

## <a name="delete-a-policy"></a>Suppression d’une stratégie

> [!NOTE]
> La suppression d’une stratégie ne supprime pas les alertes actives ou archivées générées à partir de la stratégie.

Pour supprimer une stratégie de gestion des risques internes existante, finalisez les étapes suivantes :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **Gestion des risques internes**, puis sélectionnez l’onglet **Stratégies**.
2. Dans le tableau de bord des stratégies, sélectionnez la stratégie que vous souhaitez supprimer.
3. Sélectionnez **Supprimer** sur la barre d’outils du tableau de bord.
4. Dans la boîte de dialogue **Supprimer**, sélectionnez **Oui** pour supprimer la stratégie ou **Annuler** pour fermer la boîte de dialogue.
