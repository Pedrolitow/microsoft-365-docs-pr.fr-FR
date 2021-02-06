---
title: Stratégies de gestion des risques internes
description: En savoir plus sur les stratégies de gestion des risques internes dans Microsoft 365
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
ms.openlocfilehash: 9f8424beb7e4a078d14bce755fc399ecd41764d9
ms.sourcegitcommit: eac5d9f759f290d3c51cafaf335a1a1c43ded927
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2021
ms.locfileid: "50126633"
---
# <a name="insider-risk-management-policies"></a>Stratégies de gestion des risques internes

Les stratégies de gestion des risques internes déterminent quels utilisateurs sont dans l’étendue et quels types d’indicateurs de risque sont configurés pour les alertes. Vous pouvez rapidement créer une stratégie qui s’applique à tous les utilisateurs de votre organisation ou définir des utilisateurs individuels ou des groupes à gérer dans une stratégie. Les stratégies de prise en charge des priorités de contenu pour concentrer les conditions de stratégie sur plusieurs Microsoft Teams, sites SharePoint, types de confidentialité des données et étiquettes de données spécifiques ou multiples. À l’aide de modèles, vous pouvez sélectionner des indicateurs de risque spécifiques et personnaliser les seuils d’événement pour les indicateurs de stratégie, en personnalisant efficacement les scores de risque, ainsi que le niveau et la fréquence des alertes. En outre, les détections de score de risque et d’anomalies permettent d’identifier l’activité des utilisateurs qui est plus importante ou plus inhabituelle. Les fenêtres de stratégies vous permettent de définir le délai d’application de la stratégie aux activités d’alerte et sont utilisées pour déterminer la durée de la stratégie une fois activée.

## <a name="policy-dashboard"></a>Tableau de bord de stratégie

Le **Tableau de bord de stratégie** vous permet de consulter rapidement les stratégies de votre organisation et l’état actuel des alertes associées à chaque stratégie.

- **Nom de la** stratégie : nom attribué à la stratégie dans l’Assistant Stratégie.
- **Alertes actives**: nombre d’alertes actives pour chaque stratégie.
- **Alertes confirmées**: nombre total d’alertes résultant de cas de la stratégie au cours des 365 derniers jours.
- **Actions prises sur les alertes**: nombre total d’alertes qui ont été confirmées ou rejetées au cours des 365 derniers jours.
- **Efficacité de** la stratégie : pourcentage déterminé par le nombre total d’alertes confirmées divisé par le nombre total d’actions entreprises sur les alertes (c’est-à-dire la somme des alertes confirmées ou rejetées au cours de l’année précédente).
- **Actif**: l’état du cas, *oui* ou *non*.

![Tableau de bord de la stratégie de gestion des risques internes](../media/insider-risk-policy-dashboard.png)

## <a name="policy-templates"></a>Modèles de stratégie

Les modèles de gestion des risques internes sont des conditions de stratégie prédéfinëes qui définissent les types d’indicateurs de risque et le modèle d’évaluation des risques utilisés par la stratégie. Chaque stratégie doit avoir un modèle affecté dans l’Assistant de création de stratégie avant la création de celle-ci. La gestion des risques internes prend en charge jusqu’à cinq stratégies pour chaque modèle de stratégie. Lorsque vous créez une stratégie de risque interne avec l’Assistant Stratégie, vous avez le choix entre l’un des modèles de stratégie suivants :

### <a name="data-theft-by-departing-users"></a>Vol de données par des utilisateurs qui quittent le site

Lorsque des utilisateurs quittent votre organisation, des indicateurs de risque spécifiques sont généralement associés au vol de données par les utilisateurs qui quittent l’organisation. Ce modèle de stratégie utilise des indicateurs pour l’évaluation des risques et met l’accent sur la détection et les alertes sur cette zone de risque. Le vol de données pour les utilisateurs qui quittent l’entreprise peut inclure le téléchargement de fichiers à partir de SharePoint Online, l’impression de fichiers et la copie de données dans des services de messagerie et de stockage cloud personnels près de leur lieu de travail et de leur date de fin. Ce modèle démarre l’évaluation des indicateurs de risque relatifs à ces activités et leur corrélation avec l’état d’emploi des utilisateurs.

>[!IMPORTANT]
>Lorsque vous utilisez ce modèle, vous devez configurer un connecteur Microsoft 365 HR pour importer régulièrement les informations de date de résiliation et de résiliation pour les utilisateurs de votre organisation. Consultez [l’article](import-hr-data.md) Importer des données avec le connecteur RH pour obtenir des instructions pas à pas pour configurer le connecteur RH Microsoft 365 pour votre organisation.

### <a name="general-data-leaks"></a>Fuites de données générales

La protection des données et la prévention des fuites de données sont un défi constant pour la plupart des organisations, en particulier avec la croissance rapide des nouvelles données créées par les utilisateurs, les appareils et les services. Les utilisateurs sont habilités à créer, stocker et partager des informations sur les services et les appareils, ce qui rend la gestion des fuites de données de plus en plus complexe et difficile. Les fuites de données peuvent inclure un partage accidentel d’informations en dehors de votre organisation ou un vol de données à des fins malveillantes. Conjointement avec une stratégie de protection contre la perte de données (DLP) affectée, ce modèle démarre l’évaluation en temps réel des détections de téléchargements de données SharePoint Online suspects, du partage de fichiers et de dossiers, de l’impression de fichiers et de la copie de données dans des services de messagerie et de stockage cloud personnels.

Lorsque vous utilisez un **modèle de fuites** de données, vous devez affecter une stratégie DLP pour déclencher des indicateurs dans la stratégie de risque interne pour les alertes de gravité élevée dans votre organisation. Chaque fois qu’une alerte de gravité élevée est générée par une règle de stratégie DLP est ajoutée au journal d’audit Office 365, les stratégies de risque internes créées avec ce modèle examinent automatiquement l’alerte DLP de gravité élevée. Si l’alerte contient un utilisateur dans l’étendue définie dans la stratégie de risque interne, l’alerte est traitée par la stratégie de risque interne comme une nouvelle alerte et est affectée à une gravité des risques internes et à un score de risque. Cette stratégie vous permet d’évaluer cette alerte en contexte avec d’autres activités incluses dans le cas.

#### <a name="data-leaks-policy-guidelines"></a>Recommandations en matière de stratégie de fuite de données

Lorsque vous créez ou modifiez des stratégies DLP à utiliser avec des stratégies de gestion des risques internes, prenons en compte les recommandations suivantes :

- Hiérarchisez les événements d’exfiltration de données et soyez sélectif lors de l’affectation des paramètres de rapports **d’incident** à *Élevé* lors de la configuration des règles dans vos stratégies DLP. Par exemple, l’envoi par courrier électronique de documents sensibles à un concurrent connu doit être *un* événement d’exfiltration de niveau d’alerte élevé. La sur-affectation  du niveau  élevé dans les paramètres des rapports d’incident dans d’autres règles de stratégie DLP peut augmenter le bruit dans le flux de travail d’alerte de gestion des risques internes et rendre plus difficile pour vos enquêteurs et analystes de données d’évaluer correctement ces alertes. Par exemple,  l’attribution de niveaux d’alerte élevés pour accéder aux activités par déni dans les stratégies DLP complique l’évaluation du comportement et des activités des utilisateurs réellement risqués.
- Assurez-vous que vous comprenez et configurez correctement les utilisateurs dans l’étendue dans les stratégies de gestion des risques internes et DLP. Seuls les utilisateurs définis en tant que stratégies de gestion des risques internes à l’aide du modèle fuites de données auront des **alertes** de stratégie DLP de gravité élevée traitées. En outre, seuls les utilisateurs définis comme étant dans l’étendue d’une règle pour une alerte DLP de gravité élevée seront examinés par la stratégie de gestion des risques internes pour examen. Il est important de ne pas configurer inconsciemment les utilisateurs dans l’étendue dans vos stratégies DLP et de risques internes de manière conflictuelle.

     Par exemple, si vos règles de stratégie DLP sont limitées aux utilisateurs de l’équipe commerciale et que la stratégie de risque interne créée à partir du modèle de fuites de données a défini tous les utilisateurs comme étant dans l’étendue, la stratégie de risque interne traitera uniquement les alertes DLP de gravité élevée pour les **utilisateurs** de l’équipe commerciale. La stratégie de risque interne ne reçoit aucune alerte DLP haute priorité que les utilisateurs doivent traiter et qui ne sont pas définies dans les règles DLP de cet exemple. À l’inverse, si votre stratégie de gestion des risques internes créée à partir de modèles de fuites de données s’étendue uniquement aux **utilisateurs** de l’équipe commerciale et que la stratégie DLP affectée est étendue à tous les utilisateurs, la stratégie de risque interne traitera uniquement les alertes DLP de gravité élevée pour les membres de l’équipe commerciale. La stratégie de gestion des risques internes ignorera les alertes DLP de gravité élevée pour tous les utilisateurs qui ne sont pas membres de l’équipe commerciale.

- Assurez-vous que le **paramètre** de règle rapports d’incident dans la  stratégie DLP utilisée pour ce modèle de gestion des risques internes est configuré pour les alertes de niveau de gravité élevé. Le  niveau de gravité élevé est le déclenchement des événements et les alertes de gestion des risques internes ne sont pas générées à partir des règles dans les stratégies DLP avec le champ Rapports **d’incidents** définie sur *Faible* ou *Moyen*.

    ![Paramètre d’alerte de stratégie DLP](../media/insider-risk-DLP-policy-high-severity.png)

     >[!NOTE]
     >Lorsque vous créez une stratégie DLP à l’aide des modèles intégrés, vous devez sélectionner l’option  Créer ou personnaliser des règles **DLP** avancées pour configurer le paramètre rapports **d’incident** pour le niveau de gravité élevé.

Une seule stratégie DLP peut être affectée à chaque stratégie de gestion des risques internes créée à partir du modèle de **fuites** de données. Envisagez de créer une stratégie DLP dédiée qui combine les différentes activités que vous souhaitez détecter et agir en tant que déclencheurs d’événements pour les stratégies de risques internes qui utilisent le modèle de **fuites de** données.

Consultez [l’article Créer, tester](create-test-tune-dlp-policy.md) et régler une stratégie DLP pour obtenir des instructions pas à pas pour configurer des stratégies DLP pour votre organisation.

### <a name="data-leaks-by-priority-users-preview"></a>Fuites de données par les utilisateurs prioritaires (aperçu)

La protection des données et la prévention des fuites de données pour les utilisateurs de votre organisation peuvent dépendre de leur position, du niveau d’accès aux informations sensibles ou de l’historique des risques. Les fuites de données peuvent inclure le partage accidentel d’informations hautement sensibles en dehors de votre organisation ou le vol de données à des fins malveillantes. Conjointement avec une stratégie de protection contre la perte de données (DLP) affectée, ce modèle démarre l’évaluation en temps réel des activités suspectes et augmente la probabilité d’alertes et d’alertes à risque interne avec des niveaux de gravité plus élevés. Les utilisateurs prioritaires sont définis dans les groupes [d’utilisateurs](insider-risk-management-settings.md#priority-user-groups-preview) prioritaires configurés dans la zone des paramètres de gestion des risques internes.

Comme avec le **modèle Fuites générales** de données, vous devez affecter une stratégie DLP pour déclencher des indicateurs dans la stratégie de risque interne pour les alertes de gravité élevée dans votre organisation. Suivez les instructions de stratégie de fuite de données ci-dessus lors de la création d’une stratégie à l’aide de ce modèle. En outre, vous devez affecter à la stratégie des groupes d’utilisateurs prioritaires créés dans les  >  **paramètres** de gestion des risques  >   internes.

### <a name="data-leaks-by-disgruntled-users-preview"></a>Fuites de données par des utilisateurs disgrunts (aperçu)

Lorsque les utilisateurs font face à des contraintes d’emploi, ils peuvent devenir indisciplinés, ce qui peut augmenter les risques internes. Ce modèle démarre l’score de l’activité de l’utilisateur lorsqu’un indicateur associé à disgruntlement est identifié. Les notifications d’amélioration des performances, les révisions de performances médiocres ou les modifications apportées à l’état du niveau de travail en sont des exemples. Les fuites de données pour les utilisateurs non régrunts peuvent inclure le téléchargement de fichiers à partir de SharePoint Online et la copie de données dans des services de messagerie et de stockage cloud personnels proches des événements de contrainte d’emploi.

Lorsque vous utilisez ce modèle, vous devez également configurer un connecteur RH Microsoft 365 pour importer régulièrement des notifications d’amélioration des performances, un état d’évaluation des performances médiocres ou des informations de modification du niveau de travail pour les utilisateurs de votre organisation. Consultez [l’article](import-hr-data.md) Importer des données avec le connecteur RH pour obtenir des instructions pas à pas pour configurer le connecteur RH Microsoft 365 pour votre organisation.

### <a name="general-security-policy-violations-preview"></a>Violations générales de la stratégie de sécurité (aperçu)

Dans de nombreuses organisations, les utilisateurs sont autorisés à installer des logiciels sur leurs appareils ou à modifier les paramètres de l’appareil pour faciliter leurs tâches. Par inadvertance ou avec une intention malveillante, les utilisateurs peuvent installer des programmes malveillants ou désactiver des fonctionnalités de sécurité importantes qui aident à protéger les informations sur leur appareil ou sur vos ressources réseau. Ce modèle de stratégie utilise les alertes de sécurité de Microsoft Defender pour le point de terminaison pour commencer à marquer ces activités et la détection de focus et les alertes à cette zone de risque. Utilisez ce modèle pour fournir des informations sur les violations de stratégie de sécurité dans les scénarios où les utilisateurs peuvent avoir un historique de violations de stratégie de sécurité qui peuvent être un indicateur de risque interne.

Microsoft Defender pour point de terminaison doit être configuré dans votre organisation et activer Defender pour le point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Defender pour importer les alertes de violation de sécurité. Pour plus d’informations sur la configuration de Defender pour Endpoint pour l’intégration de la gestion des risques internes, voir Configurer des fonctionnalités avancées [dans Defender pour Endpoint.](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center)

### <a name="security-policy-violations-by-departing-users-preview"></a>Violations de stratégie de sécurité par les utilisateurs qui quittent le site (aperçu)

Les utilisateurs sortants, qu’ils s’en vont dans des conditions positives ou négatives, peuvent être plus à risque pour les violations de stratégie de sécurité. Pour vous protéger contre les violations de sécurité accidentelles ou malveillantes pour les utilisateurs qui quittent l’entreprise, ce modèle de stratégie utilise les alertes Defender for Endpoint pour fournir des informations sur les activités liées à la sécurité. Ces activités incluent l’installation de programmes malveillants ou d’autres applications potentiellement dangereuses par l’utilisateur et la désactivation des fonctionnalités de sécurité sur leurs appareils. Les indicateurs de stratégie sont activés une fois que les utilisateurs ont une date de départ ou de fermeture importée à partir du connecteur Microsoft 365 HR en tant qu’événement déclencheur.

Lorsque vous utilisez ce modèle, vous devez configurer un connecteur Microsoft 365 HR pour importer régulièrement les informations de date de résiliation et de résiliation pour les utilisateurs de votre organisation. Consultez [l’article](import-hr-data.md) Importer des données avec le connecteur RH pour obtenir des instructions pas à pas pour configurer le connecteur RH Microsoft 365 pour votre organisation.

Microsoft Defender pour point de terminaison doit être configuré dans votre organisation et activer Defender pour le point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Defender pour importer les alertes de violation de sécurité. Pour plus d’informations sur la configuration de Defender pour Endpoint pour l’intégration de la gestion des risques internes, voir Configurer des fonctionnalités avancées [dans Defender pour Endpoint.](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center)

### <a name="security-policy-violations-by-priority-users-preview"></a>Violations de stratégie de sécurité par les utilisateurs prioritaires (aperçu)

La protection contre les violations de sécurité pour les utilisateurs de votre organisation peut dépendre de leur position, du niveau d’accès aux informations sensibles ou de l’historique des risques. Étant donné que les violations de sécurité par les utilisateurs prioritaires peuvent avoir un impact sur les zones critiques de votre organisation, ce modèle de stratégie commence à scorer sur ces indicateurs et utilise les alertes Microsoft Defender for Endpoint pour fournir des informations sur les activités liées à la sécurité pour ces utilisateurs. Il peut s’agir de la priorité des utilisateurs qui installent des programmes malveillants ou d’autres applications potentiellement dangereuses et désactivent les fonctionnalités de sécurité sur leurs appareils. Les utilisateurs prioritaires sont définis dans les groupes d’utilisateurs prioritaires configurés dans la zone des paramètres de gestion des risques internes.

Microsoft Defender pour point de terminaison doit être configuré dans votre organisation et activer Defender pour le point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Defender pour importer les alertes de violation de sécurité. Pour plus d’informations sur la configuration de Defender pour Endpoint pour l’intégration de la gestion des risques internes, voir Configurer des fonctionnalités avancées [dans Defender pour Endpoint.](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center) En outre, vous devez affecter à la stratégie des groupes d’utilisateurs prioritaires créés dans les  >  **paramètres** de gestion des risques  >   internes.

### <a name="security-policy-violations-by-disgruntled-users-preview"></a>Violations de stratégie de sécurité par les utilisateurs non résusés (aperçu)

Les utilisateurs qui sont exposés à des contraintes d’emploi peuvent être plus à risque de violations accidentelles ou malveillantes de la stratégie de sécurité. Ces stresseurs peuvent inclure l’utilisateur placé sur un plan d’amélioration des performances, l’état de l’évaluation des performances médiocres ou le fait d’être rétrogradé de sa position actuelle. Ce modèle de stratégie démarre l’évaluation des risques en fonction de ces indicateurs et activités associés à ces événements pour ces utilisateurs.

Lorsque vous utilisez ce modèle, vous devez également configurer un connecteur RH Microsoft 365 pour importer régulièrement des notifications d’amélioration des performances, un état d’évaluation des performances médiocres ou des informations de modification du niveau de travail pour les utilisateurs de votre organisation. Consultez [l’article](import-hr-data.md) Importer des données avec le connecteur RH pour obtenir des instructions pas à pas pour configurer le connecteur RH Microsoft 365 pour votre organisation.

Microsoft Defender pour point de terminaison doit également être configuré dans votre organisation et activer Defender pour le point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Defender pour importer les alertes de violation de la sécurité. Pour plus d’informations sur la configuration de Defender pour Endpoint pour l’intégration de la gestion des risques internes, voir Configurer des fonctionnalités avancées [dans Defender pour Endpoint.](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center)

### <a name="policy-template-prerequisites-and-triggering-events"></a>Conditions préalables du modèle de stratégie et déclenchement d’événements

Selon le modèle que vous choisissez pour une stratégie de gestion des risques internes, les événements de déclenchement et les conditions préalables à la stratégie varient. Le déclenchement d’événements est une condition préalable qui détermine si un utilisateur est actif pour une stratégie de gestion des risques internes. Si un utilisateur est ajouté à une stratégie de gestion des risques internes sans événement déclencheur, l’activité de l’utilisateur n’est pas évaluée par la stratégie, sauf s’il est ajouté manuellement dans le tableau de bord Utilisateurs. Les conditions préalables à la stratégie sont des éléments obligatoires afin que la stratégie reçoine les signaux ou les activités nécessaires pour évaluer les risques.

Le tableau suivant répertorie les événements déclencheurs et les conditions préalables pour les stratégies créées à partir de chaque modèle de stratégie de gestion des risques internes :

| **Modèle de stratégie** | **Déclenchement d’événements pour des stratégies** | **Configuration requise** |
| :------------------ | :--------------------------------- | :---------------- |
| Vol de données par des utilisateurs qui quittent le site | Indicateur de date de départ ou de résiliation à partir d’un connecteur RH | Connecteur Microsoft 365 HR configuré pour les indicateurs de date de résiliation et de fin de contrat |
| Fuites générales de données | Activité de stratégie de fuite de données qui crée une alerte de gravité élevée | Stratégie DLP configurée pour les alertes de gravité élevée |
| Fuites de données par utilisateurs prioritaires | Activité de stratégie de fuite de données qui crée une alerte de gravité élevée | Stratégie DLP configurée pour les alertes de gravité élevée <br><br> Groupes d’utilisateurs prioritaires configurés dans les paramètres de risque internes |
| Fuites de données par des utilisateurs non régrunts | Amélioration des performances, performances médiocres ou indicateurs de changement de niveau de travail à partir du connecteur RH | Connecteur Microsoft 365 HR configuré pour les indicateurs de désgruntlement |
| Violations générales de la stratégie de sécurité | Défense de contrôles de sécurité ou de logiciels indésirables détectés par Microsoft Defender pour le point de terminaison | Abonnement Microsoft Defender pour point de terminaison actif <br><br> Intégration de Microsoft Defender for Endpoint au Centre de conformité Microsoft 365 configuré |
| Violations de la stratégie de sécurité par les utilisateurs qui quittent le site | Indicateurs de date de départ ou de résiliation à partir du connecteur RH | Connecteur Microsoft 365 HR configuré pour les indicateurs de date de résiliation et de fin de contrat <br><br> Abonnement Microsoft Defender pour point de terminaison actif <br><br> Intégration de Microsoft Defender for Endpoint au Centre de conformité Microsoft 365 configuré |
| Violations de stratégie de sécurité par les utilisateurs prioritaires | Défense de contrôles de sécurité ou de logiciels indésirables détectés par Microsoft Defender pour le point de terminaison | Abonnement Microsoft Defender pour point de terminaison actif <br><br> Intégration de Microsoft Defender for Endpoint au Centre de conformité Microsoft 365 configuré <br><br> Groupes d’utilisateurs prioritaires configurés dans les paramètres de risque internes |
| Violations de stratégie de sécurité par des utilisateurs non résusés | Amélioration des performances, performances médiocres ou indicateurs de changement de niveau de travail à partir du connecteur RH | Connecteur Microsoft 365 HR configuré pour les indicateurs de désgruntlement <br><br> Abonnement Microsoft Defender pour point de terminaison actif <br><br> Intégration de Microsoft Defender for Endpoint au Centre de conformité Microsoft 365 configuré |

## <a name="prioritize-content-in-policies"></a>Hiérarchiser le contenu dans les stratégies

Les stratégies de gestion des risques internes prise en charge la spécification d’une priorité plus élevée pour le contenu en fonction de l’endroit où il est stocké ou de la façon dont il est classé. La spécification du contenu comme priorité augmente le score de risque pour toute activité associée, ce qui augmente à son tour le risque de génération d’une alerte de gravité élevée. Toutefois, certaines activités ne génèrent aucune alerte, sauf si le contenu associé contient des types d’informations sensibles intégrés ou personnalisés ou a été spécifié en tant que priorité dans la stratégie.

Par exemple, votre organisation dispose d’un site SharePoint dédié pour un projet hautement confidentiel. Les fuites de données pour les informations dans ce site SharePoint peuvent compromettre le projet et avoir un impact significatif sur son succès. En hiér donc sur ce site SharePoint dans une stratégie de fuites de données, les scores de risque pour les activités éligibles sont automatiquement augmentés. Cette hiér donc augmente la probabilité que ces activités génèrent une alerte de risque interne et augmente le niveau de gravité de l’alerte.

Lorsque vous créez une stratégie de gestion des risques internes dans l’Assistant Stratégie, vous pouvez choisir parmi les priorités suivantes :

- **Sites SharePoint**: toute activité associée à tous les types de fichiers dans les sites SharePoint définis se voit attribuer un score de risque plus élevé. 
- **Types d’informations sensibles**: toute activité associée au contenu qui contient des [types d’informations](sensitive-information-type-entity-definitions.md) sensibles se voit attribuer un score de risque plus élevé.
- **Étiquettes de sensibilité**: toute activité associée à du contenu avec des étiquettes [de sensibilité](sensitivity-labels.md) spécifiques est affectée d’un score de risque plus élevé.

## <a name="create-a-new-policy"></a>Créer une stratégie

Pour créer une stratégie de gestion des risques internes, vous allez utiliser l’Assistant Stratégie dans la **solution** de gestion des risques internes dans le Centre de conformité Microsoft 365.

Pour créer une stratégie, vous pouvez effectuer les étapes suivantes :

1. Dans le Centre de conformité [Microsoft 365,](https://compliance.microsoft.com)allez à **La** gestion des risques internes et sélectionnez **l’onglet Stratégies.**
2. Sélectionnez **Créer une stratégie** pour ouvrir l’Assistant Stratégie
3. Dans la page **Nouvelle stratégie de risque interne,** remplissez les champs suivants :
    - **Nom (obligatoire)**: entrez un nom convivial pour la stratégie.
    - **Description (facultative)**: entrez une description de la stratégie.
    - **Choisissez un modèle de stratégie (obligatoire)**: sélectionnez l’un des [modèles](insider-risk-management-policies.md#policy-templates) de stratégie pour définir les types d’indicateurs de risque surveillés par la stratégie.

    >[!IMPORTANT]
    >La plupart des modèles de stratégie ont des conditions préalables qui doivent être configurées pour que la stratégie génère des alertes pertinentes. Si vous n’avez pas configuré les conditions préalables applicables à la stratégie, voir Prise [en charge de la gestion des risques internes.](insider-risk-management-configure.md#step-3-configure-prerequisites-for-templates)

4. Sélectionnez **Suivant** pour continuer.
5. Dans la **page**  Utilisateurs, sélectionnez Ajouter un utilisateur ou un groupe ou Choisir des groupes d’utilisateurs prioritaires pour définir quels utilisateurs ou groupes d’utilisateurs prioritaires sont inclus dans la stratégie, en fonction du modèle de stratégie que vous avez sélectionné.  Activez **la case à cocher** Tous les utilisateurs et groupes à messagerie le cas échéant (si vous n’avez pas sélectionné de modèle basé sur l’utilisateur prioritaire). Sélectionnez **Suivant** pour continuer.
6. Dans la page Spécifier le contenu à hiérarchiser **(facultatif),** vous pouvez affecter les sources à hiérarchiser pour augmenter les scores de risque. Toutefois, certaines activités ne génèrent aucune alerte, sauf si le contenu associé contient des types d’informations sensibles intégrés ou personnalisés ou a été spécifié comme priorité sur cette page :
    - **Sites SharePoint**: sélectionnez Ajouter un **site SharePoint** et sélectionnez les organisations SharePoint que vous souhaitez hiérarchiser. Par exemple, *« group1@contoso.sharepoint.com/sites/group1*».
    - **Type d’informations sensibles**: sélectionnez Ajouter **un type d’informations sensibles** et sélectionnez les types de sensibilité que vous souhaitez hiérarchiser. Par exemple, *« Numéro de compte* bancaire américain » et « Numéro de carte de *crédit*».
    - **Étiquettes de sensibilité**: **sélectionnez Ajouter une** étiquette de sensibilité et sélectionnez les étiquettes que vous souhaitez hiérarchiser. Par exemple, *« Confidentiel »* et « *Secret*».
7. Sélectionnez **Suivant** pour continuer.
8. Dans **la** page Sélectionner des indicateurs de [](insider-risk-management-settings.md#indicators) stratégie, vous verrez les indicateurs que vous avez définis comme disponibles dans la page Indicateurs des **paramètres** de risque  >   internes. Si vous avez sélectionné un modèle de fuites de données au début de l’Assistant, vous devez sélectionner une stratégie DLP dans la liste de listes de listes des *stratégies* **DLP** pour activer les indicateurs de déclenchement de la stratégie. Sélectionnez les indicateurs que vous souhaitez appliquer à la stratégie. Si vous préférez ne pas utiliser les paramètres de seuil de stratégie par défaut pour ces indicateurs, désactivez les seuils par défaut recommandés par Microsoft et entrez les **valeurs** de seuil pour chaque indicateur sélectionné. Si vous avez sélectionné au moins un indicateur *Office* ou *Appareil,* sélectionnez les **marqueurs** de score de risque selon le cas. Les score de risque ne s’appliquent qu’aux indicateurs sélectionnés.

    >[!IMPORTANT]
    >Si les indicateurs de cette page ne peuvent pas être sélectionnés, vous devez sélectionner les indicateurs que vous souhaitez activer pour toutes les stratégies dans la page Indicateurs de stratégie des  >  **paramètres** de gestion des risques  >   internes.

9. Sélectionnez **Suivant** pour continuer.
10. Dans la page **Périodes** de la stratégie, vous verrez les conditions de la fenêtre [d’activation](insider-risk-management-settings.md#policy-timeframes) de la stratégie qui s’y trouverez dans la page Délais de stratégie des   >  **paramètres de** risque internes.
11. Sélectionnez **Suivant** pour continuer.
12. Dans **la** page Révision, examinez les paramètres que vous avez choisis pour la stratégie. Sélectionnez **Modifier** pour modifier l’une des valeurs de stratégie ou **sélectionnez Envoyer** pour créer et activer la stratégie.

## <a name="update-a-policy"></a>Mettre à jour une stratégie

Pour mettre à jour une stratégie de gestion des risques internes existante, vous utiliserez l’Assistant Stratégie dans la **solution** de gestion des risques internes dans le Centre de conformité Microsoft 365.

Pour gérer une stratégie existante, complétez les étapes suivantes :

1. Dans le Centre de conformité [Microsoft 365,](https://compliance.microsoft.com)allez à **La** gestion des risques internes et sélectionnez **l’onglet Stratégies.**
2. Dans le tableau de bord de stratégie, sélectionnez la stratégie à gérer.
3. Dans la page détails de la stratégie, **sélectionnez Modifier la stratégie**
4. Dans l’Assistant Stratégie, vous ne pouvez pas modifier les champs suivants :
    - **Nom**: nom convivial de la stratégie
    - **Choisir un modèle de** stratégie : modèle utilisé pour définir les types d’indicateurs de risque surveillés par la stratégie.
5. Entrez une nouvelle description pour la stratégie dans le champ **Description.** 
6. Sélectionnez **Suivant** pour continuer.
7. Dans la **page**  Utilisateurs, sélectionnez Ajouter un utilisateur ou un groupe ou Choisir des groupes d’utilisateurs prioritaires pour définir quels utilisateurs ou groupes d’utilisateurs prioritaires sont inclus dans la stratégie, en fonction du modèle de stratégie que vous avez sélectionné.  Activez **la case à cocher** Tous les utilisateurs et groupes à messagerie le cas échéant (si vous n’avez pas sélectionné de modèle basé sur l’utilisateur prioritaire). Sélectionnez **Suivant** pour continuer.
8. Dans la page Spécifier le contenu à hiérarchiser **(facultatif),** vous pouvez affecter les sources à hiérarchiser pour augmenter les scores de risque. Toutefois, certaines activités ne génèrent aucune alerte, sauf si le contenu associé contient des types d’informations sensibles intégrés ou personnalisés ou a été spécifié comme priorité sur cette page :
    - **Sites SharePoint**: sélectionnez Ajouter un **site SharePoint** et sélectionnez les organisations SharePoint que vous souhaitez hiérarchiser. Par exemple, *« group1@contoso.sharepoint.com/sites/group1*».
    - **Type d’informations sensibles**: sélectionnez Ajouter **un type d’informations sensibles** et sélectionnez les types de sensibilité que vous souhaitez hiérarchiser. Par exemple, *« Numéro de compte* bancaire américain » et « Numéro de carte de *crédit*».
    - **Étiquettes de sensibilité**: **sélectionnez Ajouter une** étiquette de sensibilité et sélectionnez les étiquettes que vous souhaitez hiérarchiser. Par exemple, *« Confidentiel »* et « *Secret*».
9. Sélectionnez **Suivant** pour continuer.
10. Dans **la** page Sélectionner des indicateurs de [](insider-risk-management-settings.md#indicators) stratégie, vous verrez les indicateurs que vous avez définis comme disponibles dans la page Indicateurs des **paramètres** de risque  >   internes. Si vous avez sélectionné un modèle de fuites de données au début de l’Assistant, vous devez sélectionner une stratégie DLP dans la liste de listes de listes des *stratégies* **DLP** pour activer les indicateurs de déclenchement de la stratégie. Sélectionnez les indicateurs que vous souhaitez appliquer à la stratégie. Si vous préférez ne pas utiliser les paramètres de seuil de stratégie par défaut pour ces indicateurs, désactivez les seuils par défaut recommandés par Microsoft et entrez les **valeurs** de seuil pour chaque indicateur sélectionné. Si vous avez sélectionné au moins un indicateur *Office* ou *Appareil,* sélectionnez le **score de risque** selon le cas. Les score de risque ne s’appliquent qu’aux indicateurs sélectionnés.

    >[!IMPORTANT]
    >Si les indicateurs de cette page ne peuvent pas être sélectionnés, vous devez sélectionner les indicateurs que vous souhaitez activer pour toutes les stratégies dans la page Indicateurs de stratégie des  >  **paramètres** de gestion des risques  >   internes.

11. Sélectionnez **Suivant** pour continuer.
12. Dans la page **Périodes** de la stratégie, vous verrez les conditions de la fenêtre [d’activation](insider-risk-management-settings.md#policy-timeframes) de la stratégie qui s’y trouverez dans la page Délais de stratégie des   >  **paramètres de** risque internes.
13. Sélectionnez **Suivant** pour continuer.
14. Dans **la** page Révision, examinez les paramètres que vous avez mis à jour pour la stratégie. Sélectionnez **Modifier** pour modifier l’une des valeurs de stratégie ou **sélectionnez Envoyer** pour mettre à jour et activer la stratégie.

## <a name="delete-a-policy"></a>Suppression d’une stratégie

>[!NOTE]
>La suppression d’une stratégie ne supprime pas les alertes actives ou archivées générées à partir de la stratégie.

Pour supprimer une stratégie de gestion des risques internes existante, complétez les étapes suivantes :

1. Dans le Centre de conformité [Microsoft 365,](https://compliance.microsoft.com)allez à **La** gestion des risques internes et sélectionnez **l’onglet Stratégies.**
2. Dans le tableau de bord de stratégie, sélectionnez la stratégie à supprimer.
3. Sélectionnez **Supprimer** dans la barre d’outils du tableau de bord.
4. Dans la **boîte de** dialogue Supprimer, sélectionnez **Oui** pour supprimer la stratégie ou sélectionnez **Annuler** pour fermer la boîte de dialogue.
