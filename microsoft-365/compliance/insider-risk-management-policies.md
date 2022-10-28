---
title: Stratégies de gestion des risques internes
description: En savoir plus sur les stratégies de gestion des risques internes dans Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, risque interne, gestion des risques, conformité
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
- tier1
- purview-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: f0651901050c91513949d992ab8c818c73e89c9e
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68768278"
---
# <a name="insider-risk-management-policies"></a>Stratégies de gestion des risques internes

> [!IMPORTANT]
> Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiellement malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Les stratégies de gestion des risques internes déterminent les utilisateurs visés et les types d’indicateurs de risque configurés pour les alertes. Vous pouvez rapidement créer une stratégie de sécurité qui s’applique à tous les utilisateurs de votre organisation ou définir des utilisateurs ou des groupes individuels pour la gestion dans une stratégie. Les stratégies prennent en charge les priorités de contenu pour centrer les conditions des stratégies sur des applications Microsoft Teams spécifiques ou multiples, des sites SharePoint, des types de confidentialité de données et des étiquettes de données. Avec l’utilisation de modèles, vous pouvez sélectionner des indicateurs de risque spécifiques et personnaliser les seuils d’un événement pour les indicateurs de stratégie, personnalisant concrètement les scores de risque, ainsi que la fréquence et le niveau des alertes. 

Vous pouvez également configurer des stratégies rapides de fuite de données et de vol de données en quittant les stratégies utilisateur qui définissent automatiquement des conditions de stratégie en fonction des résultats des dernières analyses. En outre, les rappels de score de risque et les détections d’anomalies aident à identifier les activités utilisateur potentiellement à risque qui sont d’une importance plus élevée ou inhabituelle. Les fenêtres de stratégie vous permettent de définir le délai d’exécution à appliquer à la stratégie pour les activités d’alerte et elles sont utilisées pour déterminer la durée de la stratégie une fois celle-ci activée.

Regardez la [vidéo Configuration des stratégies de gestion des risques](https://www.youtube.com/watch?v=kudK5ajZTUo) internes pour une vue d’ensemble de la façon dont les stratégies créées avec des modèles de stratégie intégrés peuvent vous aider à agir rapidement sur les risques potentiels.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="policy-dashboard"></a>Tableau de bord de stratégie

Le **tableau de bord Stratégie** vous permet de voir rapidement les stratégies de votre organisation, l’intégrité de la stratégie, d’ajouter manuellement des utilisateurs aux stratégies de sécurité et d’afficher l’état des alertes associées à chaque stratégie.

- **Nom de la** stratégie : nom affecté à la stratégie dans l’Assistant Stratégie.
- **État** : état d’intégrité de chaque stratégie. Affiche le nombre de recommandations et d’avertissements de la stratégie, ou un état *Intègre* pour les stratégies sans problème.  Vous pouvez sélectionner la stratégie pour afficher les détails de l’état d’intégrité des avertissements ou des recommandations.
- **Alertes actives** : nombre d’alertes actives pour chaque stratégie.
- **Alertes confirmées** : nombre total d’alertes qui ont entraîné des cas de la stratégie au cours des 365 derniers jours.
- **Actions effectuées sur les alertes** : nombre total d’alertes qui ont été confirmées ou ignorées au cours des 365 derniers jours.
- **Efficacité des alertes** de stratégie : pourcentage déterminé par le nombre total d’alertes confirmées divisées par le nombre total d’actions effectuées sur les alertes (qui correspond à la somme des alertes qui ont été confirmées ou ignorées au cours de l’année écoulée).

![Tableau de bord des stratégies de gestion des risques internes.](../media/insider-risk-policy-dashboard.png)

## <a name="policy-recommendations-from-analytics"></a>Recommandations de stratégie issues de l’analytique

L’analytique des risques internes vous donne une vue agrégée des activités anonymes des utilisateurs liées à la sécurité et à la conformité, ce qui vous permet d’évaluer les risques internes potentiels dans votre organisation sans configurer de stratégies de risque interne. Cette évaluation peut aider votre organisation à identifier les zones potentielles à risque plus élevé et à déterminer le type et l’étendue des stratégies de gestion des risques internes que vous pouvez envisager de configurer. Si vous décidez d’agir sur les résultats d’analyse pour les fuites de données générales ou le vol de données par des stratégies d’utilisateurs sortants, vous avez même la possibilité de configurer une stratégie rapide basée sur ces résultats.

Pour en savoir plus sur l’analytique des risques internes et les recommandations de stratégie, consultez [Paramètres de gestion des risques internes : Analytique](insider-risk-management-settings.md#analytics).

## <a name="quick-policies-from-recommended-actions-preview"></a>Stratégies rapides à partir des actions recommandées (préversion)

Pour de nombreuses organisations, la prise en main d’une stratégie initiale peut être un défi. Si vous débutez avec la gestion des risques internes et que vous utilisez les actions recommandées pour commencer, vous pouvez configurer une stratégie rapide pour accélérer les *fuites de données générales* ou le *vol de données en quittant les utilisateurs* . Les paramètres de stratégie rapides sont automatiquement renseignés en fonction des résultats de la dernière analyse analytique de votre organisation. Par exemple, si l’analyse détecte des activités potentielles de fuite de données, la stratégie rapide inclut les indicateurs utilisés pour détecter ces activités. 

Pour commencer, passez en revue les paramètres de stratégie rapides et configurez la stratégie avec une seule sélection. Si vous avez besoin de personnaliser une stratégie rapide, vous pouvez modifier les conditions pendant la configuration initiale ou après la création de la stratégie. En outre, vous pouvez rester informé des résultats de détection d’une stratégie rapide en configurant des notifications par e-mail chaque fois que vous avez un avertissement de stratégie ou chaque fois que la stratégie génère une alerte de gravité élevée.

## <a name="policy-templates"></a>Modèles de stratégie

Les modèles de gestion des risques internes sont des conditions de stratégie prédéfinies qui définissent les types d’indicateurs de risque et le modèle d’attribution de scores de risque utilisés par la stratégie. Chaque stratégie doit avoir un modèle affecté dans l’Assistant de création de stratégie avant la création de celle-ci. La gestion des risques internes prend en charge jusqu’à cinq stratégies pour chaque modèle de stratégie. Lorsque vous créez une stratégie de risque interne avec l’Assistant Stratégie, choisissez l’un des modèles de stratégie suivants :

### <a name="data-theft-by-departing-users"></a>Vol de données par des employés quittant votre organisation

Lorsque les utilisateurs quittent votre organisation, des indicateurs de risque spécifiques sont généralement associés au vol de données potentiel par les utilisateurs sortants. Cet modèle de stratégie utilise des indicateurs d’exfiltration pour l’attribution du scores de risque et se concentre sur la détection et les alertes dans cette zone à risque. Le vol de données par des employés quittant votre organisation peut inclure le téléchargement de fichiers à partir de SharePoint Online, l’impression de fichiers et la copie de données vers des services de stockage et de messagerie cloud personnels à l’approche de leur démission et de leur date de départ. En utilisant le connecteur Microsoft HR ou l’option permettant de rechercher automatiquement la suppression de compte d’utilisateur dans Azure Active Directory pour votre organisation, ce modèle commence à évaluer les indicateurs de risque liés à ces activités et à la façon dont ils sont corrélés avec l’état d’emploi de l’utilisateur.

> [!IMPORTANT]
> Lors de l’utilisation de ce modèle, vous pouvez configurer un connecteur Microsoft 365 RH pour importer périodiquement les informations sur la date de démission et la date de licenciement des utilisateurs dans votre organisation. Consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) pour obtenir des instructions détaillées sur la configuration du connecteur Microsoft 365 HR. Si vous choisissez de ne pas utiliser le connecteur RH, vous devez sélectionner l’option Compte d’utilisateur supprimé d’Azure Active Directory lors de la configuration des événements déclencheurs dans l’Assistant Stratégie.

### <a name="general-data-leaks"></a>Fuites de données générales

La protection des données et la prévention des fuites de données constituent un défi constant pour la plupart des organisations, en particulier avec la croissance rapide des nouvelles données créées par les utilisateurs, les appareils et les services. Les utilisateurs peuvent créer, stocker et partager des informations sur tous les services et appareils qui rendent la gestion des fuites de données de plus en plus complexe et difficile. Les fuites de données peuvent inclure le partage à outrance et accidentel d’informations en dehors de votre organisation ou le vol de données à des fins malveillantes. Avec une stratégie de Protection contre la perte de données Microsoft Purview (DLP) affectée, des événements déclencheurs intégrés ou personnalisables, ce modèle commence à évaluer les détections en temps réel des téléchargements de données SharePoint Online suspects, le partage de fichiers et de dossiers, l’impression de fichiers et la copie de données vers des services de messagerie cloud et de stockage personnels.

Lors de l’utilisation d’un modèle de *Fuites de données*, vous pouvez attribuer une stratégie DLP pour déclencher des indicateurs dans la stratégie de risque interne pour les alertes à gravité élevée au sein de votre organisation. Chaque fois qu’une alerte à gravité élevée générée par une règle de stratégie DLP est ajoutée au journal d’audit d’Office 365, les stratégies de risque interne créées à l’aide de ce modèle examinent automatiquement l’alerte DLP à gravité élevée. Si l’alerte contient un utilisateur dans l’étendue définie dans la stratégie de risque interne, l’alerte est traitée par la stratégie de risque interne en tant que nouvelle alerte et un score de risque et une gravité de risque interne lui sont attribués. Vous pouvez également choisir d’affecter des indicateurs sélectionnés comme déclencheurs d’événements pour une stratégie. Cette flexibilité et cette personnalisation permettent d’étendre la stratégie aux seules activités couvertes par les indicateurs. Cette stratégie vous permet d’évaluer cette alerte dans le contexte avec d’autres activités incluses dans le cas.

#### <a name="data-leaks-policy-guidelines"></a>Conseils sur la stratégie de fuite de données

Lorsque vous créez ou modifiez des stratégies de protection contre la perte de données à utiliser avec des stratégies de gestion des risques internes, tenez compte des instructions suivantes :

- Hiérarchisez les événements d’exfiltration de données et montrez-vous sélectif quand vous attribuez les paramètres des **Rapports d’incident** sur *Élevé* lors de la configuration de règles dans vos stratégies DLP. Par exemple, l’envoi de documents sensibles à un concurrent connu doit être un événement d’exfiltration de niveau d’alerte *Élevé*. L’attribution à outrance du niveau *Élevé* dans les paramètres de **Rapports d’incident** d’autres règles de stratégie DLP peut augmenter l’attention dans le flux de travail de l’alerte de gestion des risques internes et compliquer la tâche de vos enquêteurs et analystes en données pour évaluer correctement ces alertes. Par exemple, l’attribution de niveaux d’alerte *Élevé* pour accéder aux activités de refus dans les stratégies DLP peut rendre plus difficile l’évaluation des activités et du comportement utilisateur réellement risqués.
- Lorsque vous utilisez une stratégie DLP comme événement déclencheur, assurez-vous de comprendre et de configurer correctement les utilisateurs dans l’étendue dans les stratégies de gestion des risques internes et DLP. Seuls les utilisateurs définis comme étant dans l’étendue pour les stratégies de gestion des risques internes utilisant le modèle **Fuites de données** auront des alertes de stratégies DLP à gravité élevée traitées. En outre, seuls les utilisateurs définis comme dans l’étendue dans une règle pour une alerte DLP de gravité élevée seront analysés par la stratégie de gestion des risques internes pour être pris en compte. Il est important de ne pas configurer sans le savoir les utilisateurs dans l’étendue de vos stratégies de risque interne et DLP de manière conflictuelle.

     Par exemple, si vos règles de stratégie DLP sont limitées aux utilisateurs de l’équipe commerciale et que la stratégie de risque interne créée à partir du modèle **Fuites de données** a défini tous les utilisateurs comme étant inclus dans l’étendue, la stratégie de risque interne traite uniquement les alertes DLP de gravité élevée pour les utilisateurs de l’équipe commerciale. La stratégie de risque interne ne recevra aucune alerte DLP à gravité élevée pour les utilisateurs à traiter qui ne sont pas définis dans les règles DLP pour cet exemple. Inversement, si votre stratégie de gestion des risques internes créée à partir des modèles **Fuites de données** est définie sur les utilisateurs de l’équipe Ventes uniquement et que la stratégie DLP attribuée est définie sur tous les utilisateurs, la stratégie de risque interne ne traitera que les alertes DLP à gravité élevée pour les membres de l’équipe Ventes. La stratégie de gestion des risques internes ignorera les alertes DLP à gravité élevée pour tous les utilisateurs qui ne sont pas dans l’équipe Ventes.

- Vérifiez que le paramètre de règle des **Rapports d’incident** dans la stratégie DLP utilisée pour ce modèle de gestion des risques internes est paramétré pour les alertes à niveau de gravité *Élevé*. Le niveau de gravité *Élevé* est l’événement déclencheur et les alertes de gestion des risques internes ne sont pas générées à partir des règles dans les stratégies DLP ayant le champ **Rapports d’incident** défini sur *Faible* ou *Moyen*.

    ![Paramètre d’alerte de stratégie DLP.](../media/insider-risk-DLP-policy-high-severity.png)

     > [!NOTE]
     > Lorsque vous créez une stratégie DLP à l’aide de modèles intégrés, vous devez sélectionner l’option **Créer ou personnaliser des règles DLP avancées** pour configurer le paramètre **Rapports d’incident** pour le niveau de gravité *Élevé*.

Chaque stratégie de gestion des risques internes créée à partir du modèle **Fuites de données** ne peut avoir qu’une seule stratégie DLP affectée lors de l’utilisation de cette option d’événement de déclenchement. Envisagez de créer une stratégie DLP dédiée qui associe les différentes activités que vous souhaitez détecter et qui agissent en tant qu’événements déclencheurs pour les stratégies de risque interne qui utilisent le modèle **Fuites de données**.

Pour obtenir des conseils détaillés sur la configuration de stratégies DLP pour votre organisation, consultez l’article [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md).

### <a name="data-leaks-by-priority-users-preview"></a>Fuites de données par des utilisateurs prioritaires (aperçu)

Protéger et empêcher les fuites de données pour les utilisateurs de votre organisation peut dépendre de leur fonction, du niveau d’accès aux informations sensibles et de l’historique des risques. Les fuites de données peuvent inclure le partage accidentel et à outrance d’informations hautement sensibles en dehors de votre organisation ou le vol de données à des fins malveillantes. Avec une stratégie de protection contre la perte de données (DLP) affectée comme option de déclenchement d’événement, ce modèle commence à évaluer les détections en temps réel des activités suspectes et entraîne une probabilité accrue d’alertes à risque interne et d’alertes avec des niveaux de gravité plus élevés. Les utilisateurs prioritaires sont définis dans les [groupes d’utilisateurs prioritaires](insider-risk-management-settings.md#priority-user-groups-preview) configurés dans la zone des paramètres de la gestion des risques internes.

Comme avec le **modèle Fuites de données générales**, vous pouvez choisir une stratégie DLP pour déclencher des indicateurs dans la stratégie de risque interne pour les alertes de gravité élevée dans votre organisation. Suivez les instructions de stratégie de fuites de données pour les stratégies DLP lors de la création d’une stratégie avec l’option DLP lors de l’utilisation de ce modèle. Vous pouvez également choisir d’affecter des indicateurs sélectionnés comme déclencheurs d’événements pour une stratégie. Cette flexibilité et cette personnalisation permettent d’étendre la stratégie uniquement aux activités couvertes par les indicateurs. En outre, vous devez affecter des groupes d’utilisateurs prioritaires créés dans **Paramètres** >  **de gestion des** >  risques internes **Groupes d’utilisateurs prioritaires** à la stratégie.

### <a name="data-leaks-by-risky-users-preview"></a>Fuites de données par des utilisateurs à risque (préversion)

Lorsque les utilisateurs rencontrent des facteurs de stress de l’emploi, ils peuvent devenir des utilisateurs à risque, ce qui peut augmenter les risques d’activité à risque interne. Ce modèle démarre le scoring de l’activité utilisateur lorsqu’un indicateur associé à un utilisateur à risque est identifié. Il peut s’agir, par exemple, de notifications d’amélioration des performances, de révisions de performances médiocres, de modifications de l’état du niveau de travail ou d’e-mails et d’autres messages susceptibles de signaler des activités à risque. Les fuites de données pour les utilisateurs à risque peuvent inclure le téléchargement de fichiers à partir de SharePoint Online et la copie de données vers des services de stockage et de messagerie cloud personnels.

Lorsque vous utilisez ce modèle, vous devez configurer un connecteur RH, sélectionner l’option permettant [d’intégrer les signaux de risque de conformité des communications](/microsoft-365/compliance/communication-compliance-policies#policy-for-insider-risk-management-integration-preview) à partir des messages utilisateur, ou choisir les deux. Le connecteur RH permet d’importer régulièrement des notifications d’amélioration des performances, des états d’évaluation des performances médiocres ou des informations de modification de niveau de travail pour les utilisateurs de votre organisation. L’intégration des risques de conformité des communications importe des signaux pour les messages utilisateur qui peuvent contenir du contenu potentiellement menaçant, harcelant ou discriminatoire. Les alertes associées générées dans Communication Compliance n’ont pas besoin d’être triées, corrigées ou modifiées dans l’état pour être intégrées à la stratégie de gestion des risques internes.

Pour configurer un connecteur RH, consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) . Pour configurer l’intégration avec la conformité des communications, vous sélectionnez cette option dans l’Assistant lorsque vous configurez la stratégie.

### <a name="general-security-policy-violations-preview"></a>Violations générales de la stratégie de sécurité (préversion)

Dans de nombreuses organisations, les utilisateurs sont autorisés à installer des logiciels sur leur appareil ou à modifier les paramètres d’appareil pour faciliter leurs tâches. Que ce soit de manière involontaire ou avec une intention malveillante, les utilisateurs peuvent installer un programme malveillant ou désactiver des fonctionnalités importantes de sécurité permettant de protéger les informations sur leur appareil ou sur vos ressources réseau. Ce modèle de stratégie utilise les alertes de sécurité de Microsoft Defender pour point de terminaison pour commencer l’attribution de scores sur ces activités et concentrer la détection et les alertes sur cette zone à risque. Utilisez ce modèle pour fournir des informations concernant les violations de stratégie de sécurité pour les situations dans lesquelles des utilisateurs peuvent avoir un historique de violations liées à une stratégie de sécurité qui peut être un indicateur de risque interne.

Microsoft Defender pour point de terminaison doit être configuré dans votre organisation et vous devez activer Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Microsoft Defender pour importer les alertes de violation de la sécurité. Pour plus d’informations sur la configuration de Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes, consultez [Configurer des fonctionnalités avancées dans Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="general-patient-data-misuse-preview"></a>Mauvaise utilisation générale des données des patients (préversion)

La protection des données des dossiers médicaux et la prévention de l’utilisation abusive des données personnelles des patients constituent une préoccupation importante pour les organisations du secteur de la santé. Cette mauvaise utilisation peut inclure des fuites de données confidentielles à des personnes non autorisées, la modification frauduleuse des dossiers des patients ou le vol des dossiers médicaux des patients. La prévention de cette utilisation abusive des données des patients, que ce soit par manque de sensibilisation, négligence ou fraude par les utilisateurs, est également un élément clé pour répondre aux exigences réglementaires de la loi HIPAA (Health Insurance Portability and Accountability Act) et de la loi HITECH (Health Information Technology for Economic and Clinical Health). Ces deux lois établissent les exigences relatives à la protection de l’information médicale protégée par les patients (PHI).

Ce modèle de stratégie permet le scoring des risques pour les utilisateurs internes qui détectent les activités suspectes associées aux enregistrements hébergés sur des systèmes de dossiers médicaux électroniques (EMR) existants. La détection se concentre sur l’accès non autorisé, l’affichage, la modification et l’exportation des données des patients. Vous devez configurer un connecteur le [connecteur Microsoft Healthcare](import-healthcare-data.md) ou [le connecteur Epic](import-epic-data.md) pour prendre en charge la détection des activités d’accès, d’exfiltration ou d’obfuscation dans votre système EMR.

Lorsque vous utilisez ce modèle, vous devez également configurer un connecteur RH Microsoft pour importer régulièrement des données de profil d’organisation pour les utilisateurs de votre organisation. Consultez l’article [Configurer un connecteur pour importer des données RH](/microsoft-365/compliance/import-hr-data) pour obtenir des instructions détaillées sur la configuration du connecteur Microsoft 365 HR.

### <a name="general-risky-browser-usage-preview"></a>Utilisation générale du navigateur à risque (préversion)

L’identification de la visite des utilisateurs sur des sites web potentiellement inappropriés ou inacceptables sur les appareils et les réseaux de l’organisation est un élément important de la réduction des risques de sécurité, juridiques et réglementaires. Les utilisateurs qui visitent par inadvertance ou délibérément ces types de sites web peuvent exposer l’organisation à des actions en justice d’autres utilisateurs, enfreindre les exigences réglementaires, augmenter les risques de sécurité réseau ou compromettre les activités et opportunités commerciales actuelles et futures. Cette mauvaise utilisation est souvent définie dans la stratégie d’utilisation acceptable d’une organisation pour les appareils utilisateur et les ressources réseau de l’organisation, mais il est souvent difficile d’identifier et d’agir rapidement.

Pour vous protéger contre ces risques, cette stratégie peut vous aider à détecter et à activer le scoring des risques pour la navigation web qui peut être en violation de la stratégie d’utilisation acceptable de votre organisation, par exemple visiter des sites qui constituent une menace (par exemple des sites de hameçonnage) ou contiennent du contenu pour adultes. Plusieurs types de catégories sont disponibles pour la catégorisation automatique des activités de navigation web par les utilisateurs dans l’étendue.

Lorsque vous utilisez ce modèle de stratégie, vous aurez besoin de plusieurs prérequis. Pour plus d’informations, consultez [En savoir plus sur et configurer la détection des signaux du navigateur de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-browser-support).

### <a name="security-policy-violations-by-departing-users-preview"></a>Violations de stratégie de sécurité par des utilisateurs sortants (préversion)

Les utilisateurs sortants, qu’ils partent en bons ou en mauvais termes, peuvent constituer des risques plus élevés en matière de violations de stratégie de sécurité. Pour vous protéger contre des violations de sécurité malveillantes ou accidentelles de la part d’utilisateurs sortants, ce modèle de stratégie utilise les alertes de Microsoft Defender pour point de terminaison pour fournir des informations sur des activités liées à la sécurité. Ces activités incluent l’installation d’un programme malveillant ou d’autres applications potentiellement dangereuses par un utilisateur et la désactivation de fonctionnalités de sécurité sur son appareil. En utilisant le [connecteur Microsoft HR](import-hr-data.md) ou l’option permettant de rechercher automatiquement la suppression de compte d’utilisateur dans Azure Active Directory pour votre organisation, ce modèle commence à évaluer les indicateurs de risque liés à ces activités de sécurité et à la façon dont ils sont corrélés avec l’état d’emploi de l’utilisateur.

Vous devez avoir configuré Microsoft Defender pour point de terminaison dans votre organisation et activer Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans Defenfder Security Center pour importer les alertes de violation de sécurité. Pour plus d’informations sur la configuration de Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes, consultez [Configurer des fonctionnalités avancées dans Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="security-policy-violations-by-priority-users-preview"></a>Violations de la stratégie de sécurité par des utilisateurs prioritaires (préversion)

La protection contre des violations de sécurité pour les utilisateurs de votre organisation peut dépendre de leur fonction, du niveau d’accès aux informations sensibles et de l’historique des risques. Étant donné que les violations de sécurité par les utilisateurs prioritaires peuvent avoir un impact significatif sur les domaines critiques de votre organisation, ce modèle de stratégie commence à évaluer ces indicateurs et utilise des alertes Microsoft Defender pour point de terminaison pour fournir des insights sur les activités liées à la sécurité pour ces utilisateurs. Ces activités peuvent inclure l’installation d’un programme malveillant ou d’autres applications potentiellement dangereuses par des utilisateurs prioritaires et la désactivation de fonctionnalités de sécurité sur leur appareil. Les utilisateurs prioritaires sont définis dans les groupes d’utilisateurs prioritaires configurés dans la zone des paramètres de la gestion des risques internes.

Microsoft Defender pour point de terminaison doit être configuré dans votre organisation et vous devez activer Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Microsoft Defender pour importer les alertes de violation de la sécurité. Pour plus d’informations sur la configuration de Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes, consultez [Configurer des fonctionnalités avancées dans Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center). En outre, vous devez affecter des groupes d’utilisateurs prioritaires créés dans **Paramètres** >  **de gestion des** >  risques internes **Groupes d’utilisateurs prioritaires** à la stratégie.

### <a name="security-policy-violations-by-risky-users-preview"></a>Violations de stratégie de sécurité par les utilisateurs à risque (préversion)

Les utilisateurs qui font l’expérience de facteurs de stress professionnels peuvent constituer un risque plus élevé pour les violations de stratégie de sécurité malveillantes ou involontaires. Ces facteurs de stress peuvent entraîner des comportements qui entraînent la mise en place de l’utilisateur sur un plan d’amélioration des performances, un état d’évaluation des performances médiocre, une rétrogradation de sa position actuelle ou l’envoi par l’utilisateur d’e-mails et d’autres messages susceptibles de signaler un comportement à risque. Ce modèle de stratégie commence l’attribution de scores en fonction de ces indicateurs et des activités associées à ces événements pour ces utilisateurs.

Lorsque vous utilisez ce modèle, vous devez configurer un connecteur RH ou sélectionner l’option pour [intégrer les signaux de risque de conformité des communications](/microsoft-365/compliance/communication-compliance-policies#policy-for-insider-risk-management-integration-preview) provenant des messages utilisateur, ou les deux. Le connecteur RH permet d’importer régulièrement des notifications d’amélioration des performances, des états d’évaluation des performances médiocres ou des informations de modification de niveau de travail pour les utilisateurs de votre organisation. L’intégration des risques de conformité des communications importe des signaux pour les messages utilisateur qui peuvent contenir du contenu potentiellement menaçant, harcelant ou discriminatoire. Les alertes associées générées dans la conformité des communications n’ont pas besoin d’être triées, corrigées ou modifiées dans l’état pour être intégrées à la stratégie de gestion des risques internes. Pour configurer un connecteur RH, consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) . Pour configurer l’intégration à la conformité des communications, vous sélectionnez cette option dans l’Assistant lorsque vous configurez la stratégie.

Microsoft Defender pour point de terminaison doit également être configuré dans votre organisation et vous devez activer Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Microsoft Defender pour importer les alertes de violation de la sécurité. Pour plus d’informations sur la configuration de Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes, consultez [Configurer des fonctionnalités avancées dans Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="policy-template-prerequisites-and-triggering-events"></a>Conditions requises du modèle de stratégie et événements déclencheurs

En fonction du modèle choisi pour une stratégie de gestion des risques internes, les événements déclencheurs et les conditions requises de la stratégie varient. Les événements déclencheurs sont des conditions requises qui déterminent si un utilisateur est actif pour une stratégie de gestion des risques internes. Si un utilisateur est ajouté à une stratégie de gestion des risques internes mais n’a pas d’événement déclencheur, l’activité de l’utilisateur n’est pas évaluée par la stratégie, sauf s’il est ajouté manuellement dans le tableau de bord Utilisateurs. Les conditions requises de stratégie sont des éléments obligatoires pour que la stratégie reçoive les signaux ou les activités nécessaires pour évaluer les risques.

Le tableau suivant répertorie les événements déclencheurs et les conditions requises pour les stratégies créées à partir de chaque modèle de stratégie de gestion des risques internes :

| **Modèle de stratégie** | **Événements déclencheurs pour les stratégies** | **Conditions préalables** |
| :------------------ | :--------------------------------- | :---------------- |
| **Vol de données par des employés quittant votre organisation** | Indicateur de date de démission ou d’arrêt du connecteur RH ou de la suppression de compte Azure Active Directory | (facultatif) Connecteur Microsoft 365 RH configuré pour les indicateurs de date de démission ou de licenciement |
| **Fuites de données générales** | L’activité de stratégie de fuite de données qui crée une alerte de *Gravité élevée* ou des événements déclencheurs d’exfiltration intégrés | Stratégie DLP configurée pour *les alertes de gravité élevée* <br><br> OR <br><br> Indicateurs de déclenchement personnalisés |
| **Fuites de données par des utilisateurs prioritaires** | L’activité de stratégie de fuite de données qui crée une alerte de *Gravité élevée* ou des événements déclencheurs d’exfiltration intégrés | Stratégie DLP configurée pour *les alertes de gravité élevée* <br><br> OR <br><br> Indicateurs de déclenchement personnalisés <br><br> Groupes d’utilisateurs prioritaires configurés dans les paramètres de risque interne |
| **Fuites de données par des utilisateurs à risque** | - Indicateurs d’amélioration des performances, de performances médiocres ou de changement de niveau de travail à partir du connecteur RH. <br> - Messages contenant des propos potentiellement menaçants, harcelants ou discriminatoires | Connecteur Microsoft 365 HR configuré pour les indicateurs de risque <br><br> AND/OR <br><br> Intégration de la conformité des communications et stratégie d’utilisateur à risque dédiée |
| **Violations générales de la stratégie de sécurité** | Évasion de défense des contrôles de sécurité ou logiciels indésirables détectés par Microsoft Defender pour point de terminaison | Abonnement actif Microsoft Defender pour point de terminaison <br><br> intégration Microsoft Defender pour point de terminaison avec portail de conformité Microsoft Purview configurée |
| **Mauvaise utilisation des données générales sur les patients** | Évasion de défense des contrôles de sécurité à partir de systèmes EMR <br><br> Indicateurs de correspondance des adresses des utilisateurs et des patients des systèmes RH | Indicateurs d’accès aux soins de santé sélectionnés dans les paramètres de stratégie ou de risque interne <br><br> Connecteur Microsoft 365 HR configuré pour la correspondance d’adresse <br><br> Connecteur Microsoft Healthcare ou Epic configuré |
| **Utilisation générale du navigateur à risque** | Activité de navigation utilisateur liée à la sécurité qui correspond à au moins un *indicateur de navigation* sélectionné | Consultez la liste complète des prérequis dans [l’article détection des signaux du navigateur](/microsoft-365/compliance/insider-risk-management-browser-support) |
| **Violations de stratégie de sécurité par des utilisateurs quittant l’entreprise** | Indicateurs de date de démission ou de licenciement du connecteur RH ou suppression de compte Azure Active Directory | (facultatif) Connecteur Microsoft 365 RH configuré pour les indicateurs de date de démission ou de licenciement <br><br> Abonnement actif Microsoft Defender pour point de terminaison <br><br> intégration Microsoft Defender pour point de terminaison avec portail de conformité Microsoft Purview configurée |
| **Violations de la stratégie de sécurité par des utilisateurs prioritaires** | Évasion de défense des contrôles de sécurité ou logiciels indésirables détectés par Microsoft Defender pour point de terminaison | Abonnement actif Microsoft Defender pour point de terminaison <br><br> intégration Microsoft Defender pour point de terminaison avec portail de conformité Microsoft Purview configurée <br><br> Groupes d’utilisateurs prioritaires configurés dans les paramètres de risque interne |
| **Violations de stratégie de sécurité par les utilisateurs à risque** | - Indicateurs d’amélioration des performances, de performances médiocres ou de changement de niveau de travail à partir du connecteur RH. <br> - Messages contenant des propos potentiellement menaçants, harcelants ou discriminatoires | Connecteur Microsoft 365 HR configuré pour les indicateurs de risque <br><br> AND/OR <br><br> Intégration de la conformité des communications et stratégie d’utilisateur à risque dédiée <br><br> AND <br><br> Abonnement actif Microsoft Defender pour point de terminaison <br><br> intégration Microsoft Defender pour point de terminaison avec portail de conformité Microsoft Purview configurée |

## <a name="prioritize-content-in-policies"></a>Hiérarchiser le contenu dans les stratégies

Les stratégies de gestion des risques internes prennent en charge la spécification d’une priorité plus élevée pour le contenu en fonction de l’emplacement où il est stocké, du type de contenu ou de la façon dont il est classifié. Vous pouvez également choisir d’attribuer des scores de risque à toutes les activités détectées par une stratégie ou uniquement aux activités qui incluent du contenu prioritaire. La spécification du contenu comme prioritaire augmente le score de risque pour toute activité associée, ce qui à son tour augmente la possibilité de générer une alerte à gravité élevée. Certaines activités ne génèrent toutefois aucune alerte, sauf si le contenu associé contient des types d’information sensible personnalisés ou intégrés ou s’il a été spécifié comme prioritaire dans la stratégie.

Par exemple, votre organisation dispose d’un site SharePoint dédié pour un projet hautement confidentiel. Les fuites de données concernant les informations dans ce site SharePoint peuvent compromettre le projet et avoir un impact significatif sur sa réussite. En classant ce site SharePoint dans une stratégie de fuites de données, les scores de risque pour les activités éligibles sont automatiquement augmentés. Cette définition de priorités augmente les chances que ces activités génèrent une alerte de risque interne et hausse le niveau de gravité de l’alerte.

En outre, vous pouvez choisir de concentrer cette stratégie pour l’activité de site SharePoint qui inclut uniquement le contenu prioritaire pour ce projet. Les scores de risque sont attribués et les alertes sont générées uniquement lorsque les activités spécifiées incluent du contenu prioritaire. Les activités sans contenu prioritaire ne seront pas notées, mais vous pourrez toujours les examiner si une alerte est générée.

> [!NOTE]
> Si vous configurez une stratégie pour générer des alertes uniquement pour les activités qui incluent du contenu prioritaire, aucune modification n’est appliquée aux boosters de score de risque.

Lorsque vous créez une stratégie de gestion des risques internes dans l’Assistant stratégie, vous pouvez choisir parmi les priorités suivantes :

- **Sites SharePoint** : toute activité associée avec tous les types de fichiers dans les sites SharePoint définis se voit attribuer un score de risque plus élevé. Les utilisateurs qui configurent la stratégie et sélectionnent les sites SharePoint prioritaires peuvent sélectionner les sites SharePoint auxquels ils sont autorisés à accéder. Si les sites SharePoint ne sont pas disponibles pour la sélection dans la stratégie par l’utilisateur actuel, un autre utilisateur disposant des autorisations requises peut sélectionner les sites pour la stratégie ultérieurement, ou l’utilisateur actuel doit avoir accès aux sites requis.
- **Types d’information sensible** : toute activité associée au contenu qui contient des [types d’information sensible](sensitive-information-type-entity-definitions.md) se voit attribuer un score de risque plus élevé.
- **Étiquettes de confidentialité** : toute activité associée au contenu sur lequel des [étiquettes de confidentialité](sensitivity-labels.md) sont appliquées se voit attribuer un score de risque plus élevé.
- **Extensions de fichier** : toute activité associée au contenu qui a des extensions de fichier spécifiques. Les utilisateurs configurant une stratégie de vol/fuite de données qui sélectionne **extensions de fichier à hiérarchiser** dans l’Assistant Stratégie peuvent définir jusqu’à 50 extensions de fichier à hiérarchiser dans la stratégie. Les extensions entrées peuvent inclure ou omettre un « . » comme premier caractère de l’extension prioritaire.
- **Classifieurs pouvant être formés** : toute activité associée au contenu inclus dans un [classifieur pouvant être formé](/microsoft-365/compliance/classifier-learn-about). Les utilisateurs configurant une stratégie qui sélectionne classifieurs pouvant être formés dans l’Assistant Stratégie peuvent sélectionner jusqu’à 5 classifieurs pouvant être entraînés à appliquer à la stratégie. Ces classifieurs peuvent être des classifieurs existants qui identifient des modèles d’informations sensibles telles que la sécurité sociale, les numéros de carte de crédit ou de compte bancaire ou les classifieurs personnalisés créés dans votre organisation.

## <a name="sequence-detection-preview"></a>Détections de séquence (préversion)

Les activités de gestion des risques peuvent ne pas se produire en tant qu’événements isolés. Ces risques font fréquemment partie d’une séquence d’événements plus importante. Une séquence est un groupe de deux ou plusieurs activités potentiellement risquées effectuées l’une après l’autre qui peuvent suggérer un risque élevé. L’identification de ces activités utilisateur associées est une partie importante de l’évaluation du risque global. Lorsque la détection de séquence est sélectionnée pour les stratégies de vol de données ou de fuites de données, les insights des activités d’informations de séquence s’affichent sous l’onglet **Activité de l’utilisateur** dans un cas de gestion des risques internes. Les modèles de stratégie suivants prennent en charge la détection de séquence :

- Vol de données par des employés quittant votre organisation
- Fuites de données générales
- Fuites de données par des utilisateurs prioritaires
- Fuites de données par des utilisateurs à risque

Ces stratégies de gestion des risques internes peuvent utiliser des indicateurs spécifiques et l’ordre dans lequel elles se produisent pour détecter chaque étape dans une séquence de risque. Pour les stratégies créées à partir des *fuites de données générales* et des *fuites de données par les modèles utilisateur prioritaires* , vous pouvez également sélectionner les séquences qui déclenchent la stratégie. Les noms de fichiers sont utilisés lors du mappage des activités dans une séquence. Ces risques sont organisés en quatre types de détection de séquences principales :

- **Collection** : détecte les activités de téléchargement par les utilisateurs de stratégie dans l’étendue. Parmi les exemples d’activités de gestion des risques, citons le téléchargement de fichiers à partir de sites SharePoint ou le déplacement de fichiers dans un dossier compressé.
- **Exfiltration** : détecte les activités de partage ou d’extraction vers des sources internes et externes par les utilisateurs de stratégie dans l’étendue. Un exemple d’activité de gestion des risques inclut l’envoi d’e-mails avec des pièces jointes de votre organisation à des destinataires externes.
- **Obfuscation** : détecte le masquage des activités potentiellement risquées par les utilisateurs de stratégie dans l’étendue. Parmi les exemples d’activités de gestion des risques, citons le changement de nom des fichiers sur un appareil ou la suppression ou la rétrogradation des étiquettes de confidentialité sur les fichiers SharePoint.
- **Nettoyage** : détecte les activités de suppression par les utilisateurs de stratégie dans l’étendue. Un exemple d’activité de gestion des risques inclut la suppression de fichiers d’un appareil.

> [!NOTE]
> La détection de séquence utilise des indicateurs activés dans les paramètres globaux pour la gestion des risques internes. Si les indicateurs appropriés ne sont pas sélectionnés, vous pouvez activer ces indicateurs à l’étape de détection séquentielle de l’Assistant Stratégie.

Vous pouvez personnaliser les paramètres de seuil individuel pour chaque type de détection de séquence lorsqu’ils sont configurés dans la stratégie. Ces paramètres de seuil ajustent les alertes en fonction du volume de fichiers associés au type de séquence.

Si vous souhaitez en savoir plus sur la gestion de la détection de séquence dans l’affichage **Activité utilisateur**, consultez [Cas de gestion des risques internes : activité utilisateur](insider-risk-management-cases.md#user-activity).

## <a name="cumulative-exfiltration-detection-preview"></a>Détection d’exfiltration cumulée (préversion)

Avec la confidentialité activée par défaut, les indicateurs de risque interne permettent d’identifier des niveaux inhabituels d’activités à risque lorsqu’elles sont évaluées quotidiennement pour les utilisateurs qui sont dans l’étendue des stratégies de risque interne. La détection d’exfiltration cumulative utilise des modèles Machine Learning pour vous aider à identifier quand les activités d’exfiltration effectuées par un utilisateur sur une certaine période dépassent la quantité normale effectuée par les utilisateurs de votre organisation au cours des 30 derniers jours sur plusieurs types d’activités d’exfiltration. Par exemple, si un utilisateur a partagé plus de fichiers que la plupart des utilisateurs au cours du mois dernier, cette activité est détectée et classée comme une activité d’exfiltration cumulative.

Les enquêteurs et analystes de gestion des risques internes peuvent utiliser les informations de la détection d’exfiltration cumulée pour leur permettre d’identifier des activités d’exfiltration qui ne génèrent généralement aucune alerte , mais qui se situent au-dessus de ce qui est standard pour leur organisation. Des exemples peuvent correspondre à des utilisateurs sortants qui exfiltrent lentement des données sur un certain nombre de jours ou lorsque des utilisateurs partagent, à maintes reprises et plus que d’ordinaire pour votre organisation, des données sur plusieurs canaux.  Des scores de risque plus élevés sont attribués aux activités d’exfiltration cumulatives pour les sites SharePoint, les types d’informations sensibles et le contenu avec [des étiquettes de confidentialité configurées](/microsoft-365/compliance/sensitivity-labels#label-priority-order-matters) en tant que contenu prioritaire dans une stratégie ou pour une activité impliquant des étiquettes configurées en tant que priorité élevée dans Protection des données Microsoft Purview.

La détection d’exfiltration cumulée est activée par défaut lors de l’utilisation des modèles de stratégie suivants :

- Vol de données par des employés quittant votre organisation
- Fuites de données générales
- Fuites de données par des utilisateurs prioritaires
- Fuites de données par des utilisateurs à risque

> [!NOTE]
> La détection d’exfiltration cumulée utilise des indicateurs d’exfiltration activés dans les paramètres généraux pour la gestion des risques internes et les indicateurs d’exfiltration sélectionnés dans une stratégie. À ce titre, la détection d’exfiltration cumulée est uniquement évaluée pour les indicateurs d’exfiltration nécessaires sélectionnés. Les activités d’exfiltration [cumulatives pour les étiquettes de confidentialité configurées](sensitivity-labels.md) dans le contenu prioritaire génèrent des scores de risque plus élevés.

Quand une détection d’exfiltration cumulée est activée pour des stratégies de vol de données ou de fuite de données, les informations des activités d’exfiltration cumulée s’affichent dans l’onglet **Activité utilisateur** dans le cas de gestion des risques internes.

Si vous souhaitez en savoir plus sur la gestion de l’activité utilisateur, consultez [Cas de gestion des risques internes : activités utilisateur](insider-risk-management-cases.md#user-activity).

## <a name="policy-health"></a>Intégrité de la stratégie

L’état d’intégrité de la stratégie vous fournit des informations sur les problèmes potentiels avec vos stratégies de gestion des risques internes. La colonne **État** de l’onglet **Stratégies** peut vous alerter en cas de problèmes de stratégies susceptibles d’empêcher le signalement de l’activité des utilisateurs ou de la raison pour laquelle le nombre d’alertes d’activité est inhabituel. L’état de l’intégrité de la stratégie peut également confirmer que la stratégie est intègre et ne requiert aucune attention ni modification de la configuration.

If there are issues with a policy, the policy health status displays notification warnings and recommendations to help you take action to resolve policy issues. These notifications can help you resolve the following issues:

- **Stratégies avec une configuration incomplète**. Ces problèmes peuvent comprendre des groupes ou des utilisateurs manquants dans la stratégie ou d’autres étapes de configuration de la stratégie inachevées.
- **Stratégies avec des problèmes de configuration d’indicateur**. Les indicateurs sont des éléments importants de chaque stratégie. Si les indicateurs ne sont pas configurés, ou si trop peu d’indicateurs sont sélectionnés, la stratégie peut ne pas évaluer comme prévu les activités à risque.
- **Les déclencheurs de stratégie ne fonctionnent pas ou les exigences de déclencheur de stratégie ne sont pas correctement configurées**. La fonctionnalité de la stratégie peut dépendre d’autres services ou d’exigences de configuration pour détecter efficacement les événements déclencheurs permettant d’activer l’activité de score de risque aux utilisateurs dans la stratégie. Ces dépendances peuvent inclure des problèmes avec la configuration du connecteur, le partage d’alerte Microsoft Defender pour point de terminaison ou les paramètres de configuration de la stratégie de protection contre la perte de données.
- **Les limites de volume approchent ou dépassent les limites**. Les stratégies de gestion des risques internes utilisent les points de terminaison et les services Microsoft 365 pour agréger les signaux de l’activité à risque. En fonction du nombre d’utilisateurs dans vos stratégies, les limites de volume peuvent retarder l’identification et le signalement des activités à risque. Apprenez-en plus sur ces limites dans la section sur les limites du modèle de stratégie de cet article.

Pour afficher rapidement l’état d’intégrité d’une stratégie, accédez à l’onglet **Stratégie** et à la colonne **État** . Ici, vous verrez les options d’état d’intégrité de la stratégie suivantes pour chaque stratégie :

- *Sain* : aucun problème n’a été identifié avec la stratégie.
- *Recommandations* : Problème avec la stratégie qui peut empêcher la stratégie de fonctionner comme prévu.
- *Avertissements* : problème avec la stratégie qui peut l’empêcher d’identifier les activités potentiellement à risque.

Pour d’autres détails concernant les avertissements et les recommandations, sélectionnez une stratégie sur l’onglet **Stratégie** pour ouvrir la carte détaillée de la stratégie. Plus d’informations sur les recommandations et les avertissements, y compris des conseils sur la façon de résoudre ces problèmes, sont affichées dans la section **Notifications** de la carte de détails.

![Intégrité de la stratégie de gestion des risques internes.](../media/insider-risk-policy-health.png)

### <a name="notification-messages"></a>Les messages de notification

Utilisez le tableau suivant pour en savoir davantage sur les notifications d’avertissement et de recommandation, ainsi que les mesures à prendre pour résoudre des problèmes potentiels.

|**Messages de notification**|**Modèles de stratégie**|**Causes/Essayer cette action de correction**|
|:------------------------|:-------------------|:----------------------------------|
|**La stratégie n’affecte aucun score de risque à l’activité**| Tous les modèles de stratégie | Vous souhaiterez peut-être examiner l’étendue de votre stratégie et déclencher la configuration des événements afin que la stratégie puisse affecter des scores de risque aux activités <br><br> 1. Examinez les utilisateurs sélectionnés pour la stratégie. Si vous avez peu d’utilisateurs sélectionnés, vous voudrez peut-être sélectionner d’autres utilisateurs. <br> 2. Si vous utilisez un connecteur RH, vérifiez que votre connecteur RH envoie les correctes informations. <br> 3. Si vous utilisez une stratégie DLP comme événement déclencheur, vérifiez votre configuration de stratégie DLP pour vous assurer qu’elle est configurée pour être utilisée dans cette stratégie. <br> 4. For security violation policies, review the Microsoft Defender for Endpoint alert triage status selected in Insider risk settings > Intelligent detections. Confirm that the alert filter isn't too narrow.|
|**La stratégie n’a généré aucune alerte**| Tous les modèles de stratégie|Vous pouvez passer en revue la configuration de votre stratégie afin d’analyser l’activité de scoring la plus pertinente. <br><br> 1. Confirmez la sélection des indicateurs pour lesquels vous souhaitez établir un score. Plus vous aurez sélectionné des indicateurs, plus les activités se verront attribuer des scores de risque. <br> 2. Examinez la personnalisation du seuil pour la stratégie. Si les seuils sélectionnés ne s’alignent pas sur la tolérance au risque de votre organisation, ajustez les sélections afin que des alertes soient créées en fonction de vos seuils préférés. <br> 3. Examinez les utilisateurs et groupes sélectionnés pour la stratégie. Confirmez que vous avez sélectionné tous les groupes et utilisateurs applicables. <br> 4. Pour les stratégies de violation de la sécurité, confirmez que vous avez sélectionné l’état de triage de l’alerte pour laquelle vous souhaitez établir un score pour les alertes Microsoft Defender pour point de terminaison dans les Détections intelligentes des paramètres.|
|**Aucun utilisateur ou groupe n’est inclus dans cette stratégie**| Tous les modèles de stratégie | Les utilisateurs et groupes ne sont pas affectés à la stratégie. <br><br> Modifiez votre stratégie, puis sélectionnez les utilisateurs ou groupes pour la stratégie.|
|**Aucun indicateur n’a été sélectionné pour cette stratégie**| Tous les modèles de stratégie | Aucun indicateur n’a été sélectionné pour la stratégie <br><br> Modifiez votre stratégie, puis sélectionnez les indicateurs de stratégie appropriés pour la stratégie.|
|**Aucun groupe d’utilisateurs prioritaires n’est inclus dans cette stratégie**|-Fuites de données par des utilisateurs prioritaires <br> -Violations de la stratégie de sécurité par des utilisateurs prioritaires|Les groupes d’utilisateurs prioritaires ne sont pas affectés à la stratégie. <br><br> Configurez les groupes d’utilisateurs prioritaires dans les paramètres de la gestion des risques internes, puis affectez des groupes d’utilisateurs prioritaires à la stratégie.|
|**Aucun événement déclencheur n’a été sélectionné pour cette stratégie**| Tous les modèles de stratégie | Un événement déclencher n’est pas configuré pour la stratégie <br><br> Les scores de risque ne seront affectés aux activités utilisateur que lorsque vous modifierez la stratégie et sélectionnerez un événement déclencheur.|
|**Le connecteur HR n’est pas configuré ou ne fonctionne pas comme prévu**|-Vol de données par un employé quittant votre organisation <br> -Violations de stratégie de sécurité par un utilisateur quittant l’entreprise <br> - Fuites de données par des utilisateurs à risque <br> - Violations de la stratégie de sécurité par les utilisateurs à risque|Il y a un problème avec le connecteur RH. <br><br> 1. Si vous utilisez un connecteur RH, vérifiez que votre connecteur RH envoie les correctes informations <br><br> OU <br><br> 2. Sélectionnez l’événement déclencheur supprimé du compte Azure AD.|
|**Aucun appareil n’est intégré**|-Vol de données par des employés quittant votre organisation <br> -Fuites de données générales <br> - Fuites de données par des utilisateurs à risque <br> -Fuites de données par des utilisateurs prioritaires|Les indicateurs d’appareil sont sélectionnés, mais aucun appareil n’est intégré au portail de conformité <br><br> Vérifiez que les appareils sont intégrés et répondent à la configuration requise.|
|**Le connecteur RH n’a pas chargé de données récemment**|-Vol de données par un employé quittant votre organisation <br> -Violations de stratégie de sécurité par un utilisateur quittant l’entreprise <br> - Fuites de données par des utilisateurs à risque <br> - Violations de la stratégie de sécurité par les utilisateurs à risque|Le connecteur RH n’a pas importé de données depuis plus de 7 jours. <br><br> Vérifiez que votre connecteur RH est correctement configuré et qu’il envoie des données.|
|**Nous ne pouvons pas vérifier l’état de votre connecteur RH pour l’instant. Vérifiez à nouveau ultérieurement**|-Vol de données par un employé quittant votre organisation <br> -Violations de stratégie de sécurité par un utilisateur quittant l’entreprise <br> - Fuites de données par des utilisateurs à risque <br> - Violations de la stratégie de sécurité par les utilisateurs à risque|La solution de gestion des risques internes ne peut pas vérifier l’état de votre connecteur RH. <br><br> Vérifiez que votre connecteur RH est correctement configuré et qu’il envoie des données, ou revenez plus tard, puis vérifiez l’état de la stratégie.|
|**La stratégie DLP n’est pas sélectionnée comme événement déclencheur**|-Fuites de données générales <br> -Fuites de données par des utilisateurs prioritaires|Une stratégie DLP n’a pas été sélectionnée comme événement déclencheur ou la stratégie DLP sélectionnée a été supprimée. <br><br> Modifiez la stratégie, puis sélectionner une stratégie DLP active ou « L’utilisateur effectue une activité d’exfiltration » comme événement déclencheur dans la configuration de stratégie.|
|**La stratégie DLP utilisée dans cette stratégie est désactivée** |-Fuites de données générales <br> -Fuites de données par des utilisateurs prioritaires|La stratégie DLP utilisée dans cette stratégie est désactivée. <br><br> 1. Activez la stratégie DLP affectée à cette stratégie. <br><br> OU <br><br> 2. Modifiez cette stratégie, puis sélectionner une nouvelle stratégie DLP active ou « L’utilisateur effectue une activité d’exfiltration » comme événement déclencheur dans la configuration de stratégie.|
|**La stratégie DLP ne répond pas aux exigences**|-Fuites de données générales <br> -Fuites de données par des utilisateurs prioritaires|Les stratégies DLP utilisées comme événements déclencheurs doivent être configurées pour générer des alertes de gravité élevée. <br><br>  1. Modifiez votre stratégie DLP pour affecter des alertes applicables comme *Gravité élevée*. <br><br> OU <br><br> 2. Modifiez cette stratégie, puis sélectionnez *L’utilisateur effectue une activité d’exfiltration* comme événement déclencheur.|
|**Votre organisation n’a pas d’abonnement Microsoft Defender pour point de terminaison**|-Violations générales de la stratégie de sécurité <br> -Violations de stratégie de sécurité par des utilisateurs quittant l’entreprise <br> - Violations de la stratégie de sécurité par les utilisateurs à risque <br> -Violations de la stratégie de sécurité par des utilisateurs prioritaires|Aucun abonnement Microsoft Defender pour point de terminaison n’a été détecté pour votre organisation. <br><br> Tant qu’un abonnement Microsoft Defender pour point de terminaison n’a pas été ajouté, ces stratégies n’attribuent aucun score de risque à l’activité utilisateur.|
|**Microsoft Defender pour point de terminaison alertes ne sont pas partagées avec le portail de conformité**|-Violations générales de la stratégie de sécurité <br> -Violations de stratégie de sécurité par des utilisateurs quittant l’entreprise <br> - Violations de la stratégie de sécurité par les utilisateurs à risque <br> -Violations de la stratégie de sécurité par des utilisateurs prioritaires|Microsoft Defender pour point de terminaison alertes ne sont pas partagées avec le portail de conformité. <br><br> Configurez le partage des alertes de Microsoft Defender pour point de terminaison.|
|**Vous approchez de la limite maximale d’utilisateurs activement notés pour ce modèle de stratégie**|Tous les modèles de stratégie|Chaque modèle de stratégie a un nombre maximum d’utilisateurs dans l’étendue. Consultez les détails de la section limite du modèle. <br><br> Passez en revue les utilisateurs sous l’onglet Utilisateurs et supprimez tous les utilisateurs qui n’ont plus besoin d’être notés.|
|**Le déclenchement d’un événement se produit à plusieurs reprises pour plus de 15 % des utilisateurs de cette stratégie**|Tous les modèles de stratégie|Ajustez l’événement de déclenchement pour réduire la fréquence à laquelle les utilisateurs sont placés dans l’étendue de stratégie.|

## <a name="policy-template-limits"></a>Limites du modèle de stratégie

Les modèles de stratégie de gestion des risques internes utilisent des limites pour gérer le volume et le taux de traitement des activités de risque utilisateur dans l’étendue et la façon dont ce processus est intégré avec les services Microsoft 365 pris en charge. Chaque modèle de stratégie a un nombre maximal d’utilisateurs qui peuvent se voir attribuer activement des scores de risque pour la stratégie qu’il peut prendre en charge, traiter et signaler efficacement les activités potentiellement risquées. Les utilisateurs dans l’étendue sont des utilisateurs avec événements déclencheurs for la stratégie.

La limite de chaque stratégie est calculée en fonction du nombre total d’utilisateurs uniques recevant des scores de risque par type de modèle de stratégie. Si le nombre d’utilisateurs pour un type de modèle de stratégie est proche ou dépasse la limite utilisateur, les performances de la stratégie seront réduites. Pour afficher le nombre actuel d’utilisateurs pour une stratégie, naviguez vers l’onglet Stratégie et la colonne Utilisateurs dans l’étendue. Vous pouvez avoir jusqu’à cinq stratégies pour un modèle de stratégie. Ces limites maximales s’appliquent aux utilisateurs sur toutes les stratégies utilisant un modèle de stratégie donné.

Utilisez le tableau suivant pour déterminer le nombre maximum d’utilisateurs dans l’étendue pris en charge pour chaque modèle de stratégie :

|**Modèle de stratégie**|**Nombre maximum actuel d’utilisateurs dans l’étendue**|
|:------------------|:--------------------------------|
|Fuite de données générales|15 000|
|Fuite de données par des utilisateurs à risque|7 500|
|Fuite de données par des utilisateurs prioritaires|1 000|
|Vol de données par des employés quittant votre organisation|20 000|
|Violations générales de la stratégie de sécurité|1 000|
|Mauvaise utilisation des données générales sur les patients|5,000|
|Utilisation générale du navigateur à risque|7,000|
|Violation de la stratégie de sécurité par des utilisateurs prioritaires|1 000|
|Violations de stratégie de sécurité par des utilisateurs quittant l’entreprise|15 000|
|Violations de stratégie de sécurité par les utilisateurs à risque|7 500|
|Preuve d’investigation|5 utilisateurs pour la préversion|

## <a name="create-a-new-policy"></a>Créer une stratégie

Pour créer une stratégie de gestion des risques internes, vous utilisez généralement l’Assistant Stratégie dans la solution **de gestion des risques internes** dans le portail de conformité Microsoft Purview. Vous pouvez également créer des stratégies rapides pour les fuites de données générales et le vol de données en quittant les utilisateurs des analyses Analytics, le cas échéant.

Effectuez les étapes suivantes pour créer une stratégie à l’aide de l’Assistant Stratégie :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Stratégies**.
2. Sélectionnez **Créer une stratégie** pour ouvrir l’Assistant stratégie.
3. Sur la page **Modèle de stratégie**, choisissez une catégorie de stratégie, puis sélectionnez le modèle pour la nouvelle stratégie. Ces modèles sont constitués d'indicateurs et de conditions définissant les activités à risque que vous voulez détecter et examiner. Examinez les conditions préalables du modèle, les événements déclencheurs et les activités détectées pour confirmer que ce modèle de stratégie correspond à vos besoins.

    > [!IMPORTANT]
    > Certains modèles de stratégie ont des conditions préalables devant être configurées pour que la stratégie génère des alertes pertinentes. Si vous n’avez pas configuré les prérequis de la stratégie applicable, consultez **l’étape 4** de la rubrique [Prise en main de la gestion des risques internes](/microsoft-365/compliance/insider-risk-management-configure).

4. Sélectionnez **Suivant** pour continuer.
5. Dans la page **Nom et description**, complétez les champs suivants :
    - **Nom (obligatoire)** : entrez un nom convivial pour la stratégie. Ce nom ne peut pas être modifié après la création de la stratégie.
    - **Description (facultatif)** : entrez une description pour la stratégie.

6. Sélectionnez **Suivant** pour continuer.
7. Sur la page **Utilisateurs et groupes**, sélectionnez **Inclure tous les utilisateurs et groupes** ou **Inclure des utilisateurs et groupes spécifiques** pour définir les utilisateurs ou groupes inclus dans la stratégie ou, si vous avez choisir un modèle basé sur les utilisateurs prioritaires, sélectionnez **Ajouter ou modifier des groupes d’utilisateurs prioritaires**. La sélection de **Inclure tous les utilisateurs et groupes** permettra de rechercher les événements déclencheurs pour tous les utilisateurs et groupes dans votre organisation pour commencer à établir des scores de risque pour la stratégie. La sélection de **Inclure des utilisateurs et groupes spécifiques** vous permettra de définir les utilisateurs et groupes à affecter à la stratégie. Les comptes d’utilisateur invités ne sont pas pris en charge.
8. Sélectionnez **Suivant** pour continuer.
9. Sur la page **Contenu à prioriser**, vous pouvez attribuer (le cas échéant) les sources à hiérarchiser, ce qui augmente les possibilités de générer une alerte de gravité élevée pour ces sources. Sélectionnez l'une des options suivantes :

    - **Je souhaite hiérarchiser le contenu**. Cette option vous permet de hiérarchiser les *sites SharePoint*, *les étiquettes de confidentialité*, les *types d’informations sensibles* et les types de contenu *Extensions de fichier* . Si vous choisissez cette option, vous devez sélectionner au moins un type de contenu prioritaire.
    - **Je ne souhaite pas spécifier de contenu prioritaire pour l’instant**. La sélection de cette option ignore les pages de détails du contenu prioritaire dans l’Assistant.

10. Sélectionnez **Suivant** pour continuer.

11. Si vous avez sélectionné **Je veux hiérarchiser le contenu à** l’étape précédente, vous verrez les pages de détails pour les *sites SharePoint*, les *types d’informations sensibles*, *les étiquettes de confidentialité, les* *extensions de fichier* et le *scoring*. Utilisez ces pages de détails pour définir les sharePoint, les types d’informations sensibles, les étiquettes de confidentialité et les extensions de fichier à hiérarchiser dans la stratégie. La page *Détails du scoring* vous permet d’étendre la stratégie pour affecter uniquement des scores de risque au contenu prioritaire.

    - **Sites SharePoint** : sélectionnez **Ajouter un site SharePoint**, puis sélectionnez les sites SharePoint auxquels vous avez accès et que vous souhaitez classer. Par exemple, *« groupe1@contoso.sharepoint.com/sites/group1 »*.
    - **Type d’information sensible** : sélectionnez **Ajouter un type d’information confidentielle**, puis les types de confidentialité que vous souhaitez classer. Par exemple, *« Numéro de compte bancaire américain »* et *« Numéro de carte de crédit »*.
    - **Étiquette de confidentialité** : sélectionnez **Ajouter une étiquette de confidentialité**, puis les étiquettes que vous souhaitez classer. Par exemple, *« Confidentiel »* et *« Secret »*.
    - **Extensions de fichier** : ajoutez jusqu’à 50 extensions de fichier. Vous pouvez inclure ou omettre « . » avec l’extension de fichier. Par exemple, *.py* ou *py* hiérarchise les fichiers Python.
    - **Scoring** : déterminez s’il faut attribuer des scores de risque à toutes les activités détectées par cette stratégie ou uniquement aux activités qui incluent du contenu prioritaire. Choisissez **Obtenir des alertes pour toutes les activités** ou **Obtenir des alertes uniquement pour les activités qui incluent du contenu prioritaire**.

    > [!NOTE]
    > Les utilisateurs qui configurent la stratégie et déterminent les sites SharePoint prioritaires peuvent sélectionner les sites SharePoint auxquels ils sont autorisés à accéder. Si les sites SharePoint ne sont pas disponibles pour la sélection dans la stratégie par l’utilisateur actuel, un autre utilisateur disposant des autorisations requises peut sélectionner les sites pour la stratégie ultérieurement ou l’utilisateur actuel doit avoir accès aux sites requis.

12. Sélectionnez **Suivant** pour continuer.
13. Si vous avez sélectionné les *modèles Fuites de données générales ou Fuites* de *données par les utilisateurs prioritaires* , vous verrez des options dans la page **Déclencheurs de cette stratégie** pour les événements de déclenchement personnalisés et les indicateurs de stratégie. Vous avez le choix de sélectionner une stratégie ou des indicateurs DLP pour déclencher des événements qui amènent les utilisateurs affectés à la stratégie dans l’étendue pour le scoring d’activité. Si vous sélectionnez l’option d’événement déclencheur de stratégie De protection contre **la perte de données (DLP),** vous devez sélectionner une stratégie DLP dans la liste déroulante stratégie DLP pour activer les indicateurs de déclenchement de la stratégie DLP pour cette stratégie de gestion des risques internes. Si vous sélectionnez l’option **L’utilisateur effectue un événement déclencheur d’activité d’exfiltration** , vous devez sélectionner un ou plusieurs des indicateurs répertoriés pour l’événement de déclenchement de stratégie.
    >[!IMPORTANT]
    >Si vous ne parvenez pas à sélectionner un indicateur répertorié, c’est qu’il n’est pas activé pour votre organisation. Pour les rendre disponibles pour les sélectionner et les attribuer à la stratégie, activez les indicateurs dans La **gestion des** >  risques internes **Paramètres Indicateurs** > **de stratégie**.

    Si vous avez sélectionné d’autres modèles de stratégie, les événements de déclenchement personnalisés ne sont pas pris en charge. Les événements déclencheurs de stratégie intégrés s’appliquent et vous passez à l’étape 23 sans définir d’attributs de stratégie.

14. Si vous avez sélectionné *les modèles Fuites de données par les utilisateurs à risque* ou *Violations de stratégie de sécurité par les utilisateurs à risque* , vous verrez des options dans la page **Déclencheurs de cette stratégie pour** l’intégration aux événements de conformité de la communication et de connecteur de données RH. Vous avez le choix d’attribuer des scores de risque lorsque les utilisateurs envoient des messages qui contiennent un langage potentiellement menaçant, harcelant ou discriminatoire, ou d’amener les utilisateurs dans l’étendue de la stratégie après que des événements utilisateur à risque ont été signalés dans votre système RH. Si vous sélectionnez l’option **Déclencheurs à risque à partir de la conformité des communications (préversion),** vous pouvez accepter la stratégie de conformité des communications par défaut (créée automatiquement), choisir une étendue de stratégie créée précédemment pour ce déclencheur ou créer une autre stratégie délimitée. Si vous sélectionnez **événements de connecteur de données RH**, vous devez configurer un connecteur de données RH pour votre organisation.
15. Sélectionnez **Suivant** pour continuer.
16. Si vous avez sélectionné les *modèles Fuites de données générales* ou *Fuites de données par les utilisateurs prioritaires* et que vous avez sélectionné l’utilisateur **effectue une activité d’exfiltration et les indicateurs associés**, vous pouvez choisir des seuils personnalisés ou par défaut pour les événements déclencheurs d’indicateur que vous avez sélectionnés. Choisissez **l’option Utiliser les seuils par défaut (recommandé)** ou **Utiliser des seuils personnalisés pour les événements de déclenchement**.
17. Sélectionnez **Suivant** pour continuer.
18. Si vous avez sélectionné **Utiliser des seuils personnalisés pour les événements de déclenchement**, pour chaque indicateur d’événement de déclenchement que vous avez sélectionné à l’étape 13, choisissez le niveau approprié pour générer le niveau souhaité d’alertes d’activité.
19. Sélectionnez **Suivant** pour continuer.
20. Dans la page **Indicateurs de** stratégie, vous verrez les [indicateurs](insider-risk-management-settings.md#indicators) que vous avez définis comme disponibles dans la page **Paramètres de** >  risque internes **Indicateurs**. Sélectionnez les indicateurs que vous souhaitez appliquer à la stratégie.

    > [!IMPORTANT]
    > Si les indicateurs sur cette page ne peuvent pas être sélectionnés, vous sélectionner les indicateurs que vous souhaitez activer pour toutes les stratégies. Vous pouvez utiliser le bouton **Activer les indicateurs** dans l’Assistant ou sélectionner des indicateurs sur la page **Gestion des risques internes** > **Paramètres** > **Indicateurs de stratégie**.

    Si vous avez sélectionné au moins un indicateur *Office* ou *Appareil*, choisissez les **Boosters de score de risque** selon le cas. Les boosters de score de risque sont uniquement applicables pour les indicateurs sélectionnés.
    Si vous avez sélectionné un modèle de stratégie *Vol de données* ou *Fuites de données*, choisissez au moins une des méthodes **Détection de séquence** et une méthode **Détection d’exfiltration cumulée** à appliquer à la stratégie.
    Si vous avez sélectionné le modèle *de stratégie d’utilisation générale du navigateur à risque* , sélectionnez un ou plusieurs **des indicateurs de navigation**.

21. Sélectionnez **Suivant** pour continuer.
22. Dans la page **Déterminer s’il faut utiliser les seuils d’indicateur par défaut ou personnalisés** , choisissez des seuils personnalisés ou par défaut pour les indicateurs de stratégie que vous avez sélectionnés. Choisissez **l’option Utiliser les seuils par défaut pour tous les indicateurs** ou **Spécifier des seuils personnalisés** pour les indicateurs de stratégie sélectionnés. Si vous avez sélectionné Spécifier des seuils personnalisés, choisissez le niveau approprié pour générer le niveau souhaité d’alertes d’activité pour chaque indicateur de stratégie.
23. Sélectionnez **Suivant** pour continuer.
24. Sur la page **Évaluation**, examinez les paramètres choisis pour la stratégie et toute suggestion ou tout avertissement pour vos sélections. Sélectionnez **Modifier** pour changer toute valeur de stratégie ou **Soumettre** pour créer et activer la stratégie.

## <a name="update-a-policy"></a>Mettre à jour une stratégie

Pour mettre à jour une stratégie de gestion des risques internes existante, vous allez utiliser l’Assistant Stratégie dans la solution **de gestion des risques internes** dans le portail de conformité Microsoft Purview.

Finalisez les étapes suivantes pour gérer une stratégie existante :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Stratégies**.
2. Dans le tableau de bord des stratégies, sélectionnez la stratégie que vous souhaitez gérer.
3. Sur la page détaillée de la stratégie, sélectionnez **Modifier une stratégie**.
4. Dans l’Assistant Stratégie, vous ne pouvez pas modifier les éléments suivants :
    - **Modèle de stratégie** : modèle utilisé pour définir les types d’indicateurs de risque vérifiés par la stratégie.
    - **Nom** : nom convivial de la stratégie
5. Sur la page **Nom et description**, mettez à jour la description de la stratégie dans le champ **Description**.
6. Sélectionnez **Suivant** pour continuer.
7. Sur la page **Utilisateurs et groupes**, sélectionnez **Inclure tous les utilisateurs et groupes** ou **Inclure des utilisateurs et groupes spécifiques** pour définir les utilisateurs ou groupes inclus dans la stratégie ou, si vous avez choisir un modèle basé sur les utilisateurs prioritaires, sélectionnez **Ajouter ou modifier des groupes d’utilisateurs prioritaires**. Sélectionnez **Inclure tous les utilisateurs et groupes** pour rechercher le déclenchement d’événements liés à la sécurité et à la conformité pour tous les utilisateurs et groupes de votre organisation afin de commencer à attribuer des scores de risque pour la stratégie. La sélection de **Inclure des utilisateurs et groupes spécifiques** vous permettra de définir les utilisateurs et groupes à affecter à la stratégie. Les comptes d’utilisateur invités ne sont pas pris en charge.
8. Sélectionnez **Suivant** pour continuer.
9. Sur la page **Contenu à prioriser**, vous pouvez attribuer (le cas échéant) les sources à hiérarchiser, ce qui augmente les possibilités de générer une alerte de gravité élevée pour ces sources. Sélectionnez l'une des options suivantes :

    - **Je souhaite hiérarchiser le contenu**. Cette option vous permet de hiérarchiser les *sites SharePoint*, *les étiquettes de confidentialité*, les *types d’informations sensibles* et les types de contenu *Extensions de fichier* . Si vous choisissez cette option, vous devez sélectionner au moins un type de contenu prioritaire.
    - **Je ne souhaite pas spécifier de contenu prioritaire pour l’instant**. La sélection de cette option ignore les pages de détails du contenu prioritaire dans l’Assistant.

10. Sélectionnez **Suivant** pour continuer.

11. Si vous avez sélectionné **Je veux hiérarchiser le contenu à** l’étape précédente, vous verrez les pages de détails pour les *sites SharePoint*, les *types d’informations sensibles*, *les étiquettes de confidentialité, les* *extensions de fichier* et le *scoring*. Utilisez ces pages de détails pour définir les sharePoint, les types d’informations sensibles, les étiquettes de confidentialité et les extensions de fichier à hiérarchiser dans la stratégie. La page *Détails du scoring* vous permet d’étendre la stratégie pour affecter uniquement des scores de risque au contenu prioritaire.

    - **Sites SharePoint** : sélectionnez **Ajouter un site SharePoint**, puis sélectionnez les sites SharePoint auxquels vous avez accès et que vous souhaitez classer. Par exemple, *« groupe1@contoso.sharepoint.com/sites/group1 »*.
    - **Type d’information sensible** : sélectionnez **Ajouter un type d’information confidentielle**, puis les types de confidentialité que vous souhaitez classer. Par exemple, *« Numéro de compte bancaire américain »* et *« Numéro de carte de crédit »*.
    - **Étiquette de confidentialité** : sélectionnez **Ajouter une étiquette de confidentialité**, puis les étiquettes que vous souhaitez classer. Par exemple, *« Confidentiel »* et *« Secret »*.
    - **Extensions de fichier** : ajoutez jusqu’à 50 extensions de fichier. Vous pouvez inclure ou omettre « . » avec l’extension de fichier. Par exemple, *.py* ou *py* hiérarchise les fichiers Python.
    - **Scoring** : déterminez s’il faut attribuer des scores de risque à toutes les activités détectées par cette stratégie ou uniquement aux activités qui incluent du contenu prioritaire. Choisissez **Obtenir des alertes pour toutes les activités** ou **Obtenir des alertes uniquement pour les activités qui incluent du contenu prioritaire**.

    > [!NOTE]
    > Les utilisateurs qui configurent la stratégie et sélectionnent les sites SharePoint prioritaires peuvent sélectionner les sites SharePoint auxquels ils sont autorisés à accéder. Si les sites SharePoint ne sont pas disponibles pour la sélection dans la stratégie par l’utilisateur actuel, un autre utilisateur disposant des autorisations requises peut sélectionner les sites pour la stratégie ultérieurement ou l’utilisateur actuel doit avoir accès aux sites requis.

12. Sélectionnez **Suivant** pour continuer.
13. Si vous avez sélectionné les *modèles Fuites de données générales ou Fuites* de *données par les utilisateurs prioritaires* , vous verrez des options dans la page **Déclencheurs de cette stratégie** pour les événements de déclenchement personnalisés et les indicateurs de stratégie. Vous avez le choix de sélectionner une stratégie ou des indicateurs DLP pour déclencher des événements qui amènent les utilisateurs affectés à la stratégie dans l’étendue pour le scoring d’activité. Si vous sélectionnez l’option d’événement déclencheur de stratégie De protection contre **la perte de données (DLP),** vous devez sélectionner une stratégie DLP dans la liste déroulante stratégie DLP pour activer les indicateurs de déclenchement de la stratégie DLP pour cette stratégie de gestion des risques internes. Si vous sélectionnez l’option **L’utilisateur effectue un événement déclencheur d’activité d’exfiltration** , vous devez sélectionner un ou plusieurs des indicateurs répertoriés pour l’événement de déclenchement de stratégie.
    > [!IMPORTANT]
    > Si vous ne parvenez pas à sélectionner un indicateur répertorié, c’est qu’il n’est pas activé pour votre organisation. Pour les rendre disponibles pour les sélectionner et les attribuer à la stratégie, activez les indicateurs dans La **gestion des** >  risques internes **Paramètres Indicateurs** > **de stratégie**.

    Si vous avez sélectionné d’autres modèles de stratégie, les événements de déclenchement personnalisés ne sont pas pris en charge. Les événements déclencheurs de stratégie intégrés s’appliquent et vous passez à l’étape 23 sans définir d’attributs de stratégie.

14. Si vous avez sélectionné *les modèles Fuites de données par les utilisateurs à risque* ou *Violations de stratégie de sécurité par les utilisateurs à risque* , vous verrez des options dans la page **Déclencheurs de cette stratégie pour** [l’intégration aux événements de conformité de la communication](/microsoft-365/compliance/communication-compliance-policies#policy-for-insider-risk-management-integration-preview) et de connecteur de données RH. Vous avez le choix d’attribuer des scores de risque lorsque les utilisateurs envoient des messages qui contiennent un langage potentiellement menaçant, harcelant ou discriminatoire, ou d’amener les utilisateurs dans l’étendue de la stratégie après que des événements utilisateur à risque ont été signalés dans votre système RH. Si vous sélectionnez l’option **Déclencheurs à risque à partir de la conformité des communications (préversion),** vous pouvez accepter la stratégie de conformité des communications par défaut (créée automatiquement), choisir une étendue de stratégie créée précédemment pour ce déclencheur ou créer une autre stratégie délimitée. Si vous sélectionnez **événements de connecteur de données RH**, vous devez configurer un connecteur de données RH pour votre organisation.
15. Sélectionnez **Suivant** pour continuer.
16. Si vous avez sélectionné les *modèles Fuites de données générales* ou *Fuites de données par les utilisateurs prioritaires* et que vous avez sélectionné l’utilisateur **effectue une activité d’exfiltration et les indicateurs associés**, vous pouvez choisir des seuils personnalisés ou par défaut pour les événements déclencheurs d’indicateur que vous avez sélectionnés. Choisissez **l’option Utiliser les seuils par défaut (recommandé)** ou **Utiliser des seuils personnalisés pour les événements de déclenchement**.
17. Sélectionnez **Suivant** pour continuer.
18. Si vous avez sélectionné **Utiliser des seuils personnalisés pour les événements de déclenchement**, pour chaque indicateur d’événement de déclenchement que vous avez sélectionné à l’étape 13, choisissez le niveau approprié pour générer le niveau souhaité d’alertes d’activité.
19. Sélectionnez **Suivant** pour continuer.
20. Dans la page **Indicateurs de** stratégie, vous verrez les [indicateurs](insider-risk-management-settings.md#indicators) que vous avez définis comme disponibles dans la page **Paramètres de** >  risque internes **Indicateurs**. Sélectionnez les indicateurs que vous souhaitez appliquer à la stratégie.

    > [!IMPORTANT]
    > Si les indicateurs sur cette page ne peuvent pas être sélectionnés, vous sélectionner les indicateurs que vous souhaitez activer pour toutes les stratégies. Vous pouvez utiliser le bouton **Activer les indicateurs** dans l’Assistant ou sélectionner des indicateurs sur la page **Gestion des risques internes** > **Paramètres** > **Indicateurs de stratégie**.

    Si vous avez sélectionné au moins un indicateur *Office* ou *Appareil*, choisissez les **Boosters de score de risque** selon le cas. Les boosters de score de risque sont uniquement applicables pour les indicateurs sélectionnés.
    Si vous avez sélectionné un modèle de stratégie *Vol de données* ou *Fuites de données*, choisissez au moins une des méthodes **Détection de séquence** et une méthode **Détection d’exfiltration cumulée** à appliquer à la stratégie.

21. Sélectionnez **Suivant** pour continuer.
22. Dans la page **Déterminer s’il faut utiliser les seuils d’indicateur par défaut ou personnalisés** , choisissez des seuils personnalisés ou par défaut pour les indicateurs de stratégie que vous avez sélectionnés. Choisissez **l’option Utiliser les seuils par défaut pour tous les indicateurs** ou **Spécifier des seuils personnalisés** pour les indicateurs de stratégie sélectionnés. Si vous avez sélectionné Spécifier des seuils personnalisés, choisissez le niveau approprié pour générer le niveau souhaité d’alertes d’activité pour chaque indicateur de stratégie.
23. Sélectionnez **Suivant** pour continuer.
24. Sur la page **Évaluation**, examinez les paramètres choisis pour la stratégie et toute suggestion ou tout avertissement pour vos sélections. Sélectionnez **Modifier** pour changer toute valeur de stratégie ou **Soumettre** pour créer et activer la stratégie.

## <a name="copy-a-policy"></a>Copier une stratégie

Vous devrez peut-être créer une stratégie similaire à une stratégie existante qui ne nécessite que quelques modifications de configuration. Au lieu de créer une stratégie à partir de zéro, vous pouvez copier une stratégie existante, puis modifier les zones nécessitant une mise à jour dans la nouvelle stratégie.

Finalisez les étapes suivantes pour copier une stratégie existante :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Stratégies**.
2. Dans le tableau de bord des stratégies, sélectionnez la stratégie que vous souhaitez copier.
3. Sur la page détaillée de la stratégie, sélectionnez Copier.
4. Dans l’Assistant stratégie, nommez la nouvelle stratégie, puis mettez à jour sa configuration, le cas échéant.

## <a name="immediately-start-scoring-security-related-user-activity"></a>Démarrer immédiatement le scoring de l’activité utilisateur liée à la sécurité

Il peut y avoir des scénarios dans lesquels vous devez immédiatement commencer à attribuer des scores de risque à des utilisateurs en dehors des stratégies de gestion des risques extérieures au flux de travail d’événement déclencheur de gestion des risques internes. Utilisez **Démarrer l’activité d’attribution de score pour les utilisateurs** sur l’onglet **Stratégies** pour ajouter manuellement un utilisateur (ou des utilisateurs) à une ou plusieurs stratégies de risque interne, pendant une certaine période, dans le but de commencer immédiatement l’attribution de score de risque à son activité et pour contourner les conditions requises pour un utilisateur d’avoir un indicateur de déclenchement (tel qu’une correspondance de stratégie DLP). Vous pouvez également ajouter une raison pour l’ajout de l’utilisateur à la stratégie, laquelle s’affiche sur la chronologie d’activité des utilisateurs. Les utilisateurs manuellement ajoutés aux stratégies s’affichent dans le tableau de bord **Utilisateurs** et les alertes sont créées si l’activité respecte les seuils d’alerte de la stratégie. Vous pouvez ajouter jusqu’à 4 000 utilisateurs par stratégie lors de l’ajout d’utilisateurs pour un scoring immédiat.

Certains scénarios dans lesquels vous souhaitez commencer immédiatement à attribuer des scores aux activités utilisateur :

- Lorsque des utilisateurs sont identifiés avec des problèmes de risque et que vous souhaitez commencer immédiatement à attribuer des scores de risque à leur activité pour une ou plusieurs de vos stratégies.
- En cas d’incident qui peut vous obliger à commencer immédiatement à attribuer des scores de risque à l’activité des utilisateurs impliqués pour une ou plusieurs de vos stratégies.
- Lorsque vous n’avez pas encore configuré votre connecteur RH, mais que vous souhaitez commencer à attribuer des scores de risque aux activités des utilisateurs pour les événements RH en chargeant un fichier .csv pour les utilisateurs.

> [!NOTE]
> L’affichage des utilisateurs ajoutés manuellement dans le tableau de bord **Utilisateurs** peut prendre plusieurs heures. L’affichage des activités des 90 jours précédents de ces utilisateurs peut prendre jusqu’à 24 heures. Pour afficher des activités pour les utilisateurs manuellement ajoutés, naviguez vers l’onglet **Utilisateurs**, puis sélectionnez l’utilisateur sur le tableau de bord **Utilisateurs**, enfin ouvrez l’onglet **Activité utilisateur** sur le volet d’informations.

Pour commencer manuellement l’activité d’attribution de scores pour les utilisateur dans au moins une stratégie de gestion des risques internes, finalisez les étapes suivantes :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Stratégies**.
2. Dans le tableau de bord des stratégies, sélectionnez la ou les stratégies auxquelles vous souhaitez ajouter des utilisateurs.
3. Sélectionnez **Démarrer l’activité d’attribution de scores des utilisateurs**.
4. Dans le **champ Raison** du volet **Ajouter des utilisateurs à plusieurs stratégies**, ajoutez une raison pour l’ajout des utilisateurs.
5. Dans le champ **Cela doit durer pour (choisissez entre 5 et 30 jours),** définissez le nombre de jours pour noter l’activité de l’utilisateur pour la stratégie à laquelle il est ajouté
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

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Stratégies**.
2. Dans le tableau de bord des stratégies, sélectionnez la stratégie que vous souhaitez supprimer.
3. Sélectionnez **Supprimer** sur la barre d’outils du tableau de bord.
4. Dans la boîte de dialogue **Supprimer**, sélectionnez **Oui** pour supprimer la stratégie ou **Annuler** pour fermer la boîte de dialogue.
