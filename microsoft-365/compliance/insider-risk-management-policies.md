---
title: Stratégies de gestion des risques internes
description: En savoir plus sur les stratégies de gestion des risques internes dans Microsoft 365
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
ms.openlocfilehash: a08d07f574c1cd5463772c803be0d4b3850144f4
ms.sourcegitcommit: a08103bc120bdec7cfeaf67c1be4e221241e69ad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "45199537"
---
# <a name="insider-risk-management-policies"></a>Stratégies de gestion des risques internes

Les stratégies de gestion des risques internes déterminent les utilisateurs à l’échelle et les types d’indicateurs de risque configurés pour les alertes. Vous pouvez rapidement créer une stratégie qui s’applique à tous les utilisateurs de votre organisation ou définir des utilisateurs ou des groupes individuels pour la gestion dans une stratégie. Les stratégies prennent en charge les priorités de contenu pour concentrer les conditions de stratégie sur plusieurs ou des équipes Microsoft Teams, des sites SharePoint, des types de sensibilité aux données et des étiquettes de données. À l’aide de modèles, vous pouvez sélectionner des indicateurs de risques spécifiques et personnaliser les seuils d’événement pour les indicateurs de stratégie, en personnalisant efficacement les scores de risque et le niveau et la fréquence des alertes. En outre, les amplificateurs de score de risque et les détections d’anomalies permettent d’identifier les activités de l’utilisateur plus importantes ou plus inhabituelles. Les fenêtres stratégies vous permettent de définir le délai d’application de la stratégie aux activités d’alerte et de déterminer la durée de la stratégie une fois activée.

## <a name="policy-dashboard"></a>Tableau de bord de stratégie

Le **Tableau de bord de stratégie** vous permet de consulter rapidement les stratégies de votre organisation et l’état actuel des alertes associées à chaque stratégie.

- **Nom**de la stratégie : nom attribué à la stratégie dans l’Assistant stratégie.
- **Alertes actives**: nombre d’alertes actives pour chaque stratégie.
- **Alertes confirmées**: le nombre total d’alertes résultantes dans les cas de la stratégie au cours des 365 derniers jours.
- **Actions effectuées sur les alertes**: nombre total d’alertes confirmées ou rejetées au cours des 365 derniers jours.
- **Efficacité**de la stratégie : pourcentage déterminé par les alertes totales confirmées divisé par les actions effectuées sur les alertes (c’est-à-dire la somme des alertes qui ont été confirmées ou refermées au cours de l’année précédente).
- **Actif**: état de l’incident, soit *Oui* , soit *non*.

![Tableau de bord des stratégies de gestion des risques internes](../media/insider-risk-policy-dashboard.png)

## <a name="policy-templates"></a>Modèles de stratégie

Les modèles de gestion des risques initiés sont des conditions de stratégie prédéfinies qui définissent les types d’indicateurs de risques et le modèle de notation des risques utilisés par la stratégie. Chaque stratégie doit avoir un modèle affecté dans l’Assistant de création de stratégie avant la création de celle-ci. La gestion des risques internes prend en charge jusqu’à cinq stratégies pour chaque modèle de stratégie. Lorsque vous créez une stratégie de risque d’initié à l’aide de l’Assistant stratégie, vous avez le choix entre l’un des modèles de stratégie suivants :

### <a name="data-theft-by-departing-users"></a>Vol de données en faisant part des utilisateurs

Lorsque les utilisateurs quittent votre organisation, il existe des indicateurs de risque spécifiques généralement associés au vol de données en quittant les utilisateurs. Ce modèle de stratégie utilise des indicateurs pour le score de risque, détecte une détection et signale les alertes à ce sujet. Vol de données pour les utilisateurs distants peuvent inclure le téléchargement de fichiers à partir de SharePoint Online, l’impression de fichiers et la copie de données dans des services de messagerie et de stockage cloud personnels à proximité de leurs dates de démission et de fin d’emploi. Ce modèle démarre l’évaluation des indicateurs de risque liés à ces activités et la façon dont ils correspondent à l’état de travail de l’utilisateur.

>[!IMPORTANT]
>Lorsque vous utilisez ce modèle, vous devez configurer un connecteur RH Microsoft 365 pour importer régulièrement les informations de démission et de cessation d’emploi pour les utilisateurs de votre organisation. Pour obtenir des conseils détaillés sur la configuration du connecteur RH Microsoft 365 pour votre organisation, voir l’article [importer des données avec le connecteur RH](import-hr-data.md) .

### <a name="general-data-leaks"></a>Fuites de données générales

La protection des données et la prévention des fuites de données sont des défis constants pour la plupart des organisations, en particulier en ce qui concerne la croissance rapide des nouvelles données créées par les utilisateurs, les appareils et les services. Les utilisateurs sont habilités à créer, stocker et partager des informations entre les services et les appareils qui rendent la gestion des fuites de données de plus en plus complexe et difficile. Les fuites de données peuvent inclure un partage accidentel d’informations en dehors de votre organisation ou du vol de données à des fins malveillantes. En association avec une stratégie de protection contre la perte de données (DLP) affectée, ce modèle commence à compter les détections en temps réel des téléchargements de données SharePoint Online suspects, le partage de fichiers et de dossiers, l’impression de fichiers et la copie de données dans les services de stockage et de messagerie Cloud personnels.

Lors de l’utilisation d’un modèle de **fuites de données** , vous devez affecter une stratégie DLP pour déclencher des indicateurs dans la stratégie des risques internes pour les alertes de gravité élevée au sein de votre organisation. Chaque fois qu’une alerte de gravité élevée est générée par une règle de stratégie DLP est ajoutée au Journal d’audit Office 365, les stratégies de risque internes créées à l’aide de ce modèle examinent automatiquement l’alerte DLP de gravité élevée. Si l’alerte contient un utilisateur dans l’étendue défini dans la stratégie d’Insider Risk, l’alerte est traitée par la stratégie des risques initiés en tant que nouvelle alerte et a affecté une sévérité et un score de risque aux risques initiés. Cette stratégie vous permet d’évaluer cette alerte dans le contexte avec d’autres activités incluses dans le cas.

#### <a name="data-leaks-policy-guidelines"></a>Instructions de stratégie de fuites de données

Lors de la création ou de la modification de stratégies DLP à utiliser avec des stratégies de gestion des risques initiées, tenez compte des instructions suivantes :

- Hiérarchiser les événements d’exfiltration des données et être sélectif lors de l’affectation des paramètres des **rapports d’incidents** à *haut* lors de la configuration des règles dans vos stratégies DLP. Par exemple, l’envoi de documents sensibles à un concurrent connu doit être un événement exfiltration de niveau d’alerte *élevé* . Le fait d’affecter le niveau *élevé* dans les paramètres des **rapports d’incident** dans d’autres règles de stratégie DLP peut augmenter le bruit dans le flux de travail d’alerte de gestion des risques inSided et compliquer la tâche des analystes et analystes de données pour évaluer correctement ces alertes. Par exemple, l’affectation de niveaux d’alerte *élevés* pour accéder aux activités de refus de service dans les stratégies DLP complique l’évaluation du comportement et des activités de l’utilisateur.
- Assurez-vous que vous comprenez et configurez correctement les utilisateurs dans le cadre des stratégies de gestion des risques DLP et Insider. Seuls les utilisateurs définis comme dans l’étendue pour les stratégies de gestion des risques internes utilisant le modèle **fuites de données** seront traités comme des alertes de stratégie DLP de gravité élevée. De plus, seuls les utilisateurs définis comme étant inclus dans une règle pour une alerte DLP de gravité élevée seront examinés par la stratégie de gestion des risques Insiders. Il est important de ne pas configurer les utilisateurs dans l’étendue à la fois dans vos stratégies de risque de DLP et d’initié de manière contradictoire.

     Par exemple, si vos règles de stratégie DLP ne concernent que les utilisateurs de l’équipe de vente et que la stratégie de risque d’initié créée à partir du modèle **fuites de données** a défini tous les utilisateurs comme étant dans l’étendue, la stratégie de risque d’initié ne traitera que les alertes DLP de gravité élevée pour les utilisateurs de l’équipe commerciale. La stratégie de risque initié ne reçoit pas d’alertes de haute priorité pour les utilisateurs à traiter qui ne sont pas définies dans les règles DLP de cet exemple. À l’inverse, si la stratégie de gestion des risques inSided créée à partir de **fuites de données** n’est étendue que pour les utilisateurs de l’équipe des ventes et que la stratégie DLP attribuée est étendue à tous les utilisateurs, la stratégie d’Insider risque de traiter uniquement les alertes DLP de gravité élevée pour les membres de l’équipe des ventes. La stratégie de gestion des risques Insider ignore les alertes de gravité élevée pour tous les utilisateurs qui ne se trouvent pas dans l’équipe des ventes.

- Assurez-vous que le paramètre de règle **rapports d’incident** de la stratégie DLP utilisée pour ce modèle de gestion des risques initiaux est configuré pour des alertes de niveau de gravité *élevé* . Le niveau de gravité *élevé* est que les alertes de déclenchement et les alertes de gestion des risques internes ne seront pas générées à partir des règles des stratégies DLP dont le champ **rapports d’incident** est défini sur *faible* ou *moyen*.

    ![Paramètre d’alerte de stratégie DLP](../media/insider-risk-DLP-policy-high-severity.png)

     >[!NOTE]
     >Lors de la création d’une stratégie DLP à l’aide des modèles prédéfinis, vous devez sélectionner l’option **créer ou personnaliser des règles DLP avancées** pour configurer le paramètre **rapports d’incident** pour le niveau de gravité *élevé* .

Chaque stratégie de gestion des risques inSided créée à partir du modèle **fuites de données** ne peut avoir qu’une seule stratégie DLP affectée. Envisagez de créer une stratégie DLP dédiée qui combine les différentes activités que vous souhaitez détecter et agir en tant qu’événements déclencheurs pour les stratégies de risque d’initié qui utilisent le modèle **fuites de données** .

Consultez la rubrique [créer, tester et régler une stratégie DLP](create-test-tune-dlp-policy.md) pour obtenir des instructions détaillées sur la configuration des stratégies DLP pour votre organisation.

### <a name="data-leaks-by-priority-users-preview"></a>Fuites de données par les utilisateurs prioritaires (aperçu)

La protection des données et la prévention des fuites de données pour les utilisateurs de votre organisation peuvent dépendre de leur position, de leur niveau d’accès aux informations sensibles ou de l’historique des risques. Les fuites de données peuvent inclure un surPartage accidentel d’informations hautement sensibles en dehors de votre organisation ou du vol de données à des fins malveillantes. En association avec une stratégie de protection contre la perte de données (DLP) affectée, ce modèle commence à compter les détections en temps réel d’activité suspecte et entraîne une augmentation de la probabilité d’alertes et d’alertes de risque d’initiés ayant des niveaux de gravité plus élevés. Les utilisateurs prioritaires sont définis dans les groupes d’utilisateurs prioritaires configurés dans la zone paramètres de gestion des risques inSided. AJOUTER UN LIEN

Comme avec le **modèle de fuite générale des données**, vous devez affecter une stratégie DLP pour déclencher des indicateurs dans la stratégie des risques internes pour les alertes de gravité élevée au sein de votre organisation. Suivez les instructions relatives aux fuites de données ci-dessus lors de la création d’une stratégie à l’aide de ce modèle. De plus, vous devrez affecter des groupes d’utilisateurs prioritaires créés dans les paramètres de **gestion des risques initiés**  >  **Settings**  >  aux**groupes d’utilisateurs prioritaires** sur la stratégie.

### <a name="data-leaks-by-disgruntled-users-preview"></a>Fuites de données par les utilisateurs mécontents (aperçu)

Lorsque les utilisateurs connaissent des contraintes d’emploi, ils peuvent devenir mécontents, ce qui peut augmenter les risques d’activité des risques initiés. Ce modèle commence à compter l’activité de l’utilisateur lorsqu’un indicateur associé à disgruntlement est identifié. Les exemples incluent des notifications d’amélioration des performances, des révisions de performances médiocres ou des modifications de l’état du niveau de travail. Les fuites de données pour les utilisateurs mécontents peuvent inclure le téléchargement de fichiers à partir de SharePoint Online et la copie de données dans des services de stockage et de messagerie Cloud personnels vers des événements stressor.

Lors de l’utilisation de ce modèle, vous devez également configurer un connecteur RH Microsoft 365 pour importer régulièrement des notifications d’amélioration des performances, un état de l’analyse des performances médiocres ou des informations sur la modification du niveau de travail pour les utilisateurs de votre organisation. Pour obtenir des conseils détaillés sur la configuration du connecteur RH Microsoft 365 pour votre organisation, voir l’article [importer des données avec le connecteur RH](import-hr-data.md) .

### <a name="general-security-policy-violations-preview"></a>Violations de stratégie de sécurité générale (préversion)

Dans de nombreuses organisations, les utilisateurs disposent d’autorisations pour installer des logiciels sur leurs appareils ou pour modifier les paramètres des appareils afin d’aider à leurs tâches. Par inadvertance ou à des fins malveillantes, les utilisateurs peuvent installer des programmes malveillants ou désactiver des fonctionnalités de sécurité importantes qui permettent de protéger les informations sur leur appareil ou sur les ressources réseau. Ce modèle de stratégie utilise des alertes de sécurité de Microsoft Defender-protection avancée contre les menaces (ATP) pour commencer à compter ces activités et activer la détection et les alertes dans ce domaine de risque. Utilisez ce modèle pour fournir des informations sur les violations de stratégie de sécurité dans les scénarios lorsque les utilisateurs peuvent avoir un historique des violations de stratégie de sécurité qui peuvent être un indicateur de risque d’initié.

Vous devez avoir Microsoft Defender ATP configuré dans votre organisation et activer l’intégration de la gestion des risques initiés de Microsoft Defender dans le centre de sécurité de Defender pour importer les alertes de violation de sécurité. Pour plus d’informations sur la configuration de Microsoft Defender ATP pour l’intégration de la gestion des risques initiaux, voir [configure Advanced Features in Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="security-policy-violations-by-departing-users-preview"></a>Violations de stratégie de sécurité en faisant ressorter les utilisateurs (aperçu)

Les utilisateurs à l’extérieur, qu’ils soient positifs ou négatifs, peuvent présenter des risques plus élevés pour les violations de la stratégie de sécurité. Pour vous protéger contre les violations de sécurité involontaires ou malveillantes pour les utilisateurs qui se déconnectent, ce modèle de stratégie utilise des alertes Microsoft Defender ATP pour fournir des informations sur les activités liées à la sécurité. Ces activités incluent l’utilisateur qui installe des programmes malveillants ou d’autres applications potentiellement dangereuses et désactive les fonctionnalités de sécurité sur leurs appareils. Les indicateurs de stratégie sont activés une fois que les utilisateurs ont une date de retrait ou d’arrêt importée du connecteur RH de Microsoft 365 en tant qu’événement déclencheur.

Lorsque vous utilisez ce modèle, vous devez configurer un connecteur RH Microsoft 365 pour importer régulièrement les informations de démission et de cessation d’emploi pour les utilisateurs de votre organisation. Pour obtenir des conseils détaillés sur la configuration du connecteur RH Microsoft 365 pour votre organisation, voir l’article [importer des données avec le connecteur RH](import-hr-data.md) .

Vous devez avoir Microsoft Defender ATP configuré dans votre organisation et activer l’intégration de la gestion des risques initiés de Microsoft Defender dans le centre de sécurité de Defender pour importer les alertes de violation de sécurité. Pour plus d’informations sur la configuration de Microsoft Defender ATP pour l’intégration de la gestion des risques initiaux, voir [configure Advanced Features in Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="security-policy-violations-by-priority-users-preview"></a>Violations de stratégie de sécurité par utilisateurs prioritaires (aperçu)

La protection contre les violations de sécurité pour les utilisateurs au sein de votre organisation peut dépendre de leur position, de leur niveau d’accès aux informations sensibles ou de l’historique des risques. Étant donné que les violations de sécurité par les utilisateurs prioritaires peuvent avoir un impact important sur les domaines critiques de votre organisation, ce modèle de stratégie commence le score sur ces indicateurs et utilise des alertes Microsoft Defender ATP pour fournir des informations sur les activités liées à la sécurité pour ces utilisateurs. Cela peut inclure la priorité des utilisateurs qui installent des programmes malveillants ou d’autres applications potentiellement dangereuses et qui désactivent les fonctionnalités de sécurité sur leurs appareils. Les utilisateurs prioritaires sont définis dans les groupes d’utilisateurs prioritaires configurés dans la zone paramètres de gestion des risques inSided.

Vous devez avoir Microsoft Defender ATP configuré dans votre organisation et activer l’intégration de la gestion des risques initiés de Microsoft Defender dans le centre de sécurité de Defender pour importer les alertes de violation de sécurité. Pour plus d’informations sur la configuration de Microsoft Defender ATP pour l’intégration de la gestion des risques initiaux, voir [configure Advanced Features in Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center). De plus, vous devrez affecter des groupes d’utilisateurs prioritaires créés dans les paramètres de **gestion des risques initiés**  >  **Settings**  >  aux**groupes d’utilisateurs prioritaires** sur la stratégie.

### <a name="security-policy-violations-by-disgruntled-users-preview"></a>Violations de stratégie de sécurité par des utilisateurs mécontents (aperçu)

Les utilisateurs qui connaissent des contraintes de travail peuvent être à un risque plus élevé pour les violations de stratégie de sécurité involontaire ou malveillante. Ces contraintes peuvent inclure l’utilisateur sur un plan d’amélioration des performances, un état de l’analyse des performances médiocres ou la rétrogradation de sa position actuelle. Ce modèle de stratégie commence le marquage des risques en fonction des indicateurs et des activités associés à ces événements pour ces utilisateurs.

Lors de l’utilisation de ce modèle, vous devez également configurer un connecteur RH Microsoft 365 pour importer régulièrement des notifications d’amélioration des performances, un état de l’analyse des performances médiocres ou des informations sur la modification du niveau de travail pour les utilisateurs de votre organisation. Pour obtenir des conseils détaillés sur la configuration du connecteur RH Microsoft 365 pour votre organisation, voir l’article [importer des données avec le connecteur RH](import-hr-data.md) .

Vous devrez également disposer de Microsoft Defender ATP configuré dans votre organisation et activer Microsoft Defender ATP pour l’intégration de la gestion des risques initiaux dans le centre de sécurité de Defender pour importer les alertes de violation de sécurité. Pour plus d’informations sur la configuration de Microsoft Defender ATP pour l’intégration de la gestion des risques initiaux, voir [configure Advanced Features in Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="offensive-language-in-email"></a>Langage offensant dans les messages électroniques

Détecter et prendre des mesures pour empêcher les comportements offensants et violent est un élément essentiel de la prévention des risques. Les classifieurs intégrés de Microsoft 365 analysent les messages électroniques envoyés à partir de boîtes aux lettres Exchange Online de votre organisation pour différents types de problèmes de conformité. Ces classifieurs utilisent une combinaison d’intelligence artificielle et de mots clés pour identifier la langue du courrier électronique susceptible de violer les stratégies anti-harcèlement. Utilisez ce modèle pour créer rapidement une stratégie qui utilise ces classifieurs pour détecter automatiquement le contenu des messages électroniques qui peut être considéré comme injurieux ou choquant. La gestion des risques internes utilise des classifieurs qui analysent les messages électroniques envoyés pour les termes et les sentiments de langue anglaise pour le langage offensant.

### <a name="policy-template-prerequisites-and-triggering-events"></a>Conditions préalables et événements de déclenchement des modèles de stratégie

Selon le modèle que vous choisissez pour une stratégie de gestion des risques Insider, les événements déclencheurs et les prérequis de stratégie varient. Les événements déclencheurs sont des conditions préalables qui déterminent si un utilisateur est actif pour une stratégie de gestion des risques Insiders. Si un utilisateur est ajouté à une stratégie de gestion des risques Insiders mais qu’il n’a pas d’événement déclencheur, l’activité de l’utilisateur n’est pas évaluée par la stratégie, sauf s’il est ajouté manuellement dans le tableau de bord utilisateurs. Les conditions préalables requises pour la stratégie sont les éléments nécessaires pour que la stratégie reçoive les signaux ou les activités nécessaires pour évaluer le risque.

Le tableau suivant répertorie les événements de déclenchement et les éléments prérequis pour les stratégies créées à partir de chaque modèle de stratégie de gestion des risques inSided :

| **Modèle de stratégie** | **Déclenchement des événements pour les stratégies** | **Conditions préalables** |
| :------------------ | :--------------------------------- | :---------------- |
| Vol de données en faisant part des utilisateurs | Indicateur de date de retrait ou d’arrêt du connecteur RH | Connecteur RH Microsoft 365 configuré pour les indicateurs de date de fin et de suppression |
| Fuites de données générales | Activité de stratégie de fuite de données qui crée une alerte de gravité élevée | Stratégie DLP configurée pour les alertes de gravité élevée |
| Fuites de données par les utilisateurs prioritaires | Activité de stratégie de fuite de données qui crée une alerte de gravité élevée | Stratégie DLP configurée pour les alertes de gravité élevée <br><br> Groupes d’utilisateurs prioritaires configurés dans les paramètres des risques initiés |
| Fuites de données par les utilisateurs mécontents | Amélioration des performances, performances médiocres ou indicateurs de modification au niveau du poste du connecteur RH | Connecteur RH Microsoft 365 configuré pour les indicateurs disgruntlement |
| Violations de stratégie de sécurité générale | Fraude défensive concernant les contrôles de sécurité ou les logiciels indésirables détectés par Microsoft Defender ATP | Abonnement actif à l’ATP Microsoft Defender <br><br> Intégration de Microsoft Defender ATP au centre de conformité Microsoft 365 configuré |
| Violations de stratégie de sécurité en faisant départion des utilisateurs | Démissions ou indicateurs de date de fin du connecteur RH | Connecteur RH Microsoft 365 configuré pour les indicateurs de date de fin et de suppression <br><br> Abonnement actif à l’ATP Microsoft Defender <br><br> Intégration de Microsoft Defender ATP au centre de conformité Microsoft 365 configuré |
| Violations de stratégie de sécurité par utilisateurs prioritaires | Fraude défensive concernant les contrôles de sécurité ou les logiciels indésirables détectés par Microsoft Defender ATP | Abonnement actif à l’ATP Microsoft Defender <br><br> Intégration de Microsoft Defender ATP au centre de conformité Microsoft 365 configuré <br><br> Groupes d’utilisateurs prioritaires configurés dans les paramètres des risques initiés |
| Violations de stratégie de sécurité par un utilisateur mécontent | Amélioration des performances, performances médiocres ou indicateurs de modification au niveau du poste du connecteur RH | Connecteur RH Microsoft 365 configuré pour les indicateurs disgruntlement <br><br> Abonnement actif à l’ATP Microsoft Defender <br><br> Intégration de Microsoft Defender ATP au centre de conformité Microsoft 365 configuré |
| Langage offensant dans les messages électroniques | Blasphèmes, menaces ou langage de harcèlement dans les messages électroniques | Abonnement Exchange Online actif |

## <a name="prioritize-content-in-policies"></a>Hiérarchisation du contenu dans les stratégies

Les stratégies de gestion des risques internes prennent en charge la spécification d’une priorité plus élevée pour le contenu en fonction de son emplacement de stockage et de son classement. La spécification du contenu en tant que priorité augmente le score de risque pour toute activité associée, ce qui augmente à son tour le risque de générer une alerte de gravité élevée. Toutefois, certaines activités ne génèrent pas d’alerte en tout lieu, sauf si le contenu associé contient des types d’informations sensibles intégrés ou personnalisés ou s’il a été spécifié en tant que priorité dans la stratégie.

Par exemple, votre organisation dispose d’un site SharePoint dédié pour un projet hautement confidentiel. Les fuites de données pour les informations de ce site SharePoint peuvent compromettre le projet et avoir un impact significatif sur sa réussite. En hiérarchisant ce site SharePoint dans une stratégie de fuites de données, les scores de risque pour les activités éligibles augmentent automatiquement. Cela augmente la probabilité que ces activités génèrent une alerte de risque d’initié et élève le niveau de gravité de l’alerte.

Lorsque vous créez une stratégie de gestion des risques inSided dans l’Assistant stratégie, vous pouvez choisir parmi les priorités suivantes :

- **Sites SharePoint**: toute activité associée à tous les types de fichiers dans les sites SharePoint définis reçoit un score de risque plus élevé. 
- **Types d’informations sensibles**: toute activité associée au contenu qui contient des [types d’informations sensibles](sensitive-information-type-entity-definitions.md) reçoit un score de risque plus élevé.
- **Étiquettes de sensibilité**: toute activité associée au contenu auquel des [étiquettes de sensibilité](sensitivity-labels.md) spécifiques sont appliquées reçoit un score de risque plus élevé.

## <a name="create-a-new-policy"></a>Créer une stratégie

Pour créer une stratégie de gestion des risques inSided, vous utiliserez l’Assistant stratégie dans la solution de **gestion des risques Insider** dans le centre de conformité Microsoft 365.

Pour créer une stratégie, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **stratégies** .
2. Sélectionnez **créer une stratégie** pour ouvrir l’Assistant stratégie.
3. Sur la page **nouvelle stratégie de risque Insider** , renseignez les champs suivants :
    - **Nom (obligatoire)**: entrez un nom convivial pour la stratégie.
    - **Description (facultatif)**: entrez une description pour la stratégie.
    - **Choisir un modèle de stratégie (obligatoire)**: sélectionnez un des [modèles de stratégie](insider-risk-management-policies.md#policy-templates) pour définir les types d’indicateurs de risque sont surveillés par la stratégie.

    >[!IMPORTANT]
    >La plupart des modèles de stratégie comportent des éléments prérequis qui doivent être configurés pour que la stratégie génère des alertes appropriées. Si vous n’avez pas configuré les conditions préalables requises pour la stratégie, consultez la rubrique [prise en main de la gestion des risques d’initié](insider-risk-management-configure.md#step-3-configure-prerequisites-for-templates).

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

## <a name="update-a-policy"></a>Mettre à jour une stratégie

Pour mettre à jour une stratégie de gestion des risques inSided existante, vous allez utiliser l’Assistant stratégie dans la solution de **gestion des risques inSided** dans le centre de conformité Microsoft 365.

Pour gérer une stratégie existante, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **stratégies** .
2. Dans le tableau de bord de stratégie, sélectionnez la stratégie que vous souhaitez gérer.
3. Sur la page Détails de stratégie, sélectionnez **modifier la stratégie** .
4. Dans l’Assistant stratégie, vous ne pouvez pas modifier les champs suivants :
    - **Name**: nom convivial de la stratégie
    - **Choisir le modèle de stratégie**: modèle utilisé pour définir les types d’indicateurs de risque surveillés par la stratégie.
5. Entrez une nouvelle description pour la stratégie dans le champ **Description** . 
6. Sélectionnez **suivant** pour continuer.
7. Dans la page **utilisateurs** , sélectionnez **Ajouter un utilisateur ou un groupe** ou **Choisissez Priority Group Groups** pour définir les utilisateurs ou groupes d’utilisateurs de priorité inclus dans la stratégie, en fonction du modèle de stratégie que vous avez sélectionné. Activez la case à cocher **tous les utilisateurs et les groupes à extension messagerie** , le cas échéant (si vous n’avez pas sélectionné de modèle de priorité basé sur l’utilisateur). Sélectionnez **suivant** pour continuer.
8. Sur la page **spécifier le contenu à classer par priorité (facultatif)** , vous pouvez attribuer les sources à hiérarchiser pour augmenter le score des risques. Toutefois, certaines activités ne génèrent pas d’alerte en tout lieu, sauf si le contenu associé contient des types d’informations sensibles intégrés ou personnalisés ou s’il a été spécifié comme priorité sur cette page :
    - **Sites SharePoint**: sélectionnez **Ajouter un site SharePoint** et sélectionnez les organisations SharePoint dont vous souhaitez définir la priorité. Par exemple, *« Group1@contoso.sharepoint.com/sites/group1 »*.
    - **Type d’informations sensibles**: sélectionnez **Ajouter un type d’informations sensibles** et sélectionnez les types de critère de diffusion dont vous souhaitez définir la priorité. Par exemple, *« numéro de compte bancaire américain »* et *« numéro de carte de crédit »*.
    - **Étiquettes de sensibilité**: sélectionnez **Ajouter une étiquette de confidentialité** et sélectionnez les étiquettes dont vous souhaitez définir la priorité. Par exemple, *« confidentiel »* et *« secret »*.
9. Sélectionnez **suivant** pour continuer.
10. Sur la page **Sélectionner les indicateurs de stratégie** , vous verrez les [indicateurs](insider-risk-management-settings.md#indicators) que vous avez définis comme étant disponibles sur la page indicateurs des paramètres de **risque Insider**  >  **Indicators** . Si vous avez sélectionné un modèle de *fuites de données* au début de l’Assistant, vous devez sélectionner une stratégie DLP dans la liste déroulante **stratégie DLP** pour activer le déclenchement des indicateurs pour la stratégie. Sélectionnez les indicateurs que vous souhaitez appliquer à la stratégie. Si vous préférez ne pas utiliser les paramètres de seuil de stratégie par défaut pour ces indicateurs, désactivez l’option **utiliser les seuils par défaut recommandés par Microsoft** et entrez les valeurs de seuil pour chaque indicateur sélectionné. Si vous avez sélectionné au moins un indicateur de *Bureau* ou d' *appareil* , sélectionnez les **suramplificateurs de score de risque** , le cas échéant. Les amplificateurs de score de risque ne s’appliquent qu’aux indicateurs sélectionnés.

    >[!IMPORTANT]
    >Si les indicateurs de cette page ne peuvent pas être sélectionnés, vous devrez sélectionner les indicateurs que vous souhaitez activer pour toutes les stratégies sur la page indicateurs de stratégie des paramètres de **gestion des risques inSided**  >  **Settings**  >  **Policy indicators** .

11. Sélectionnez **suivant** pour continuer.
12. Dans la page périodes de la **stratégie** , les conditions de la [fenêtre d’activation](insider-risk-management-settings.md#policy-timeframes) s’affichent pour la stratégie dans la page périodes de la stratégie des paramètres des **risques Insider**  >  **Policy timeframes** .
13. Sélectionnez **suivant** pour continuer.
14. Sur la page **révision** , passez en revue les paramètres que vous avez mis à jour pour la stratégie. Sélectionnez **modifier** pour modifier les valeurs de la stratégie ou sélectionnez **Envoyer** pour mettre à jour et activer la stratégie.

## <a name="delete-a-policy"></a>Suppression d’une stratégie

>[!NOTE]
>La suppression d’une stratégie ne supprime pas les alertes actives ou archivées générées à partir de la stratégie.

Pour supprimer une stratégie de gestion des risques initiés existante, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **stratégies** .
2. Dans le tableau de bord de stratégie, sélectionnez la stratégie que vous souhaitez supprimer.
3. Sélectionnez **supprimer** dans la barre d’outils Tableau de bord.
4. Dans la boîte de dialogue **supprimer** , sélectionnez **Oui** pour supprimer la stratégie, ou cliquez sur **Annuler** pour fermer la boîte de dialogue.
