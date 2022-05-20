---
title: En savoir plus sur la gestion des risques internes Microsoft
description: Découvrez comment réduire les risques au sein de votre organisation avec la gestion des risques internes dans Microsoft Purview.
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
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.openlocfilehash: 86a56ec16f81eaa6b61a452829e65251b673cb78
ms.sourcegitcommit: b5529afa84f7dde0a89b1e08aeaf6a3a15cd7679
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65599252"
---
# <a name="learn-about-insider-risk-management"></a>En savoir plus sur la gestion des risques internes Microsoft

> [!TIP]
> *Saviez-vous que vous pouvez essayer les versions Premium des neuf solutions Microsoft Purview gratuitement ?* Utilisez la version d’évaluation des solutions Purview de 90 jours pour découvrir comment des fonctionnalités Purview robustes peuvent aider votre organisation à répondre à ses besoins de conformité. Microsoft 365 E3 et Office 365 E3 clients peuvent être démarrés maintenant sur le [Hub d’essais du portail de conformité Microsoft Purview](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). Découvrez plus d’informations sur [les personnes qui peuvent s’inscrire et les conditions d’évaluation](compliance-easy-trials.md).

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Gestion des risques internes Microsoft Purview est une solution de conformité qui permet de réduire les risques internes en vous permettant de détecter, d’examiner et d’agir sur des activités malveillantes et accidentelles dans votre organisation. Les stratégies de risque internes vous permettent de définir les types de risques à identifier et à détecter dans votre organisation, y compris agir sur les cas et faire remonter les cas à Microsoft eDiscovery (Premium) si nécessaire. Les analystes des risques de votre organisation peuvent rapidement prendre les mesures appropriées pour s’assurer que les utilisateurs sont conformes aux normes de conformité de votre organisation.

Pour plus d’informations et une vue d’ensemble du processus de planification pour traiter les activités à risque au sein de votre organisation, consultez [Démarrage d’un programme de gestion des risques internes](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf).

Regardez les vidéos ci-dessous pour découvrir comment la gestion des risques internes peut aider votre organisation à prévenir, détecter et contenir des risques tout en hiérarchisant les valeurs, la culture et l’expérience utilisateur de votre organisation :
<br>
<br>

**Solution de gestion des risques internes & développement** :
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4j9CN]
<br>

**Flux de travail de gestion des risques internes** :
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

> [!IMPORTANT]
> La gestion des risques internes est actuellement disponible dans les locataires hébergés dans des régions géographiques et des pays pris en charge par les dépendances du service Azure. Pour vérifier que la gestion des risques internes est prise en charge pour votre organisation, consultez [la disponibilité des dépendances Azure par pays/région](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="modern-risk-pain-points"></a>Points de douleur à risque modernes

La gestion et la réduction des risques au sein de votre organisation commencent par la compréhension des types de risques présents sur le lieu de travail moderne. Certains risques sont pilotés par des événements externes et des facteurs qui ne sont pas directement contrôlés. D’autres risques sont pilotés par des événements internes et des activités utilisateur qui peuvent être réduites et évitées. Certains exemples sont des risques liés à des comportements et actions illégaux, inappropriés, non autorisés ou contraires à l’éthique de la part des utilisateurs de votre organisation. Ces comportements incluent un large éventail de risques internes de la part des utilisateurs :

- Fuites de données sensibles et fuite de données
- Violations de confidentialité
- Vol de propriété intellectuelle (IP)
- Fraude
- Délit d’initié
- Violations de la conformité avec la réglementation

Les utilisateurs de l’espace de travail moderne ont accès à la création, à la gestion et au partage de données sur un large éventail de plateformes et de services. Dans la plupart des cas, les organisations disposent de ressources et d’outils limités pour identifier et atténuer les risques à l’échelle de l’organisation tout en respectant les normes de confidentialité des utilisateurs.

La gestion des risques internes utilise l’étendue complète du service et des indicateurs tiers pour vous aider à identifier, trier et agir rapidement sur l’activité à risque. En utilisant les journaux d’activité de Microsoft 365 et microsoft Graph, la gestion des risques internes vous permet de définir des stratégies spécifiques pour identifier les indicateurs de risque. Ces stratégies vous permettent d’identifier les activités à risque et d’agir pour atténuer ces risques.

La gestion des risques internes est centrée sur les principes suivants :

- **Transparence** : équilibrez la confidentialité des utilisateurs et les risques de l’organisation avec l’architecture de confidentialité par conception.
- **Configurable** : stratégies configurables basées sur des groupes sectoriels, géographiques et d’entreprise.
- **Intégré** : flux de travail intégré dans Microsoft Purview solutions.
- **Actionnable** : fournit des insights pour activer les notifications de réviseur, les investigations de données et les investigations utilisateur.

## <a name="identifying-potential-risks-with-analytics"></a>Identification des risques potentiels avec l’analytique

L’analyse des risques internes vous permet d’effectuer une évaluation des risques internes potentiels au sein de votre organisation sans aucune configuration de stratégie des risques internes. Cette évaluation peut permettre à votre organisation d’identifier des zones potentielles plus élevées de risque utilisateur et vous aider à déterminer le type et l’étendue des stratégies de gestion des risques internes que vous pouvez envisager de configurer. Cette évaluation peut également vous aider à déterminer les besoins en matière de licences supplémentaires ou d’optimisation future des stratégies de risque interne existantes.

Pour en savoir plus sur l’analytique des risques [internes, consultez les paramètres de gestion des risques internes : Analytique](insider-risk-management-settings.md#analytics).

## <a name="get-started-with-recommended-actions-preview"></a>Démarrage avec les actions recommandées (préversion)

Que vous configuriez la gestion des risques internes pour la première fois ou que vous commenciez à créer de nouvelles stratégies, la nouvelle expérience [d’actions recommandées](insider-risk-management-configure.md#recommended-actions-preview) peut vous aider à tirer le meilleur parti des fonctionnalités de gestion des risques internes. Les actions recommandées incluent la configuration des autorisations, le choix d’indicateurs de stratégie, la création d’une stratégie, etc.

## <a name="workflow"></a>Flux de travail

Le flux de travail de gestion des risques internes vous aide à identifier, examiner et prendre des mesures pour résoudre les risques internes dans votre organisation. Avec des modèles de stratégie axés, une signalisation d’activité complète dans le service Microsoft 365 et des outils de gestion des alertes et des cas, vous pouvez utiliser des insights actionnables pour identifier et agir rapidement sur les comportements à risque.

L’identification et la résolution des activités à risque internes et des problèmes de conformité avec la gestion des risques internes utilisent le flux de travail suivant :

![Flux de travail de gestion des risques internes.](../media/insider-risk-workflow.png)

### <a name="policies"></a>Stratégies

[Les stratégies de gestion des risques internes](insider-risk-management-policies.md) sont créées à l’aide de modèles et de conditions de stratégie prédéfinis qui définissent les événements déclencheurs et les indicateurs de risque examinés dans votre organisation. Ces conditions incluent la façon dont les indicateurs de risque sont utilisés pour les alertes, les utilisateurs inclus dans la stratégie, les services prioritaires et la période de surveillance.

Vous pouvez choisir parmi les modèles de stratégie suivants pour prendre rapidement en main la gestion des risques internes :

- [Vol de données par des employés quittant votre organisation](insider-risk-management-policies.md#data-theft-by-departing-users)
- [Fuites de données générales](insider-risk-management-policies.md#general-data-leaks)
- [Fuites de données par des utilisateurs prioritaires (aperçu)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)
- [Fuites de données par des utilisateurs mécontents (préversion)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)
- [Violations générales de la stratégie de sécurité (préversion)](insider-risk-management-policies.md#general-security-policy-violations-preview)
- [Utilisation incorrecte générale des données des patients (préversion)](insider-risk-management-policies.md#general-patient-data-misuse-preview)
- [Violations de stratégie de sécurité par des utilisateurs sortants (préversion)](insider-risk-management-policies.md#security-policy-violations-by-departing-users-preview)
- [Violations de la stratégie de sécurité par des utilisateurs prioritaires (préversion)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Violations de stratégie de sécurité par un utilisateur mécontent (préversion)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

![Tableau de bord de la stratégie de gestion des risques internes.](../media/insider-risk-policy-dashboard.png)

### <a name="alerts"></a>Alertes

Les alertes sont générées automatiquement par des indicateurs de risque qui correspondent aux conditions de stratégie et sont [affichées dans le tableau de bord Alertes](insider-risk-management-activities.md#alert-dashboard). Ce tableau de bord autorise un affichage rapide de toutes les alertes nécessitant un examen, des alertes ouvertes au fil du temps et des statistiques des alertes pour votre organisation. Toutes les alertes de stratégie sont affichées avec les informations suivantes pour vous aider à identifier rapidement l’état des alertes existantes et des nouvelles alertes qui nécessitent une action :

- État
- Severity
- Heure détectée
- Cas
- État du cas

![Tableau de bord des alertes de gestion des risques internes.](../media/insider-risk-alerts-dashboard.png)

### <a name="triage"></a>Triage

Les nouvelles activités utilisateur qui doivent faire l’objet d’une investigation génèrent automatiquement des alertes qui se voient attribuer un état *de révision des besoins* . Les réviseurs peuvent rapidement identifier et examiner, évaluer et trier ces alertes.

Les alertes sont résolues par l'ouverture d'un nouveau cas, l'affectation de l'alerte à un cas existant ou le rejet de l'alerte. À l’aide de filtres d’alerte, il est facile d’identifier rapidement les alertes par état, gravité ou heure détectée. Dans le cadre du processus de triage, les réviseurs peuvent afficher les détails de l’alerte pour les activités identifiées par la stratégie, afficher l’activité utilisateur associée à la correspondance de stratégie, voir la gravité de l’alerte et examiner les informations de profil utilisateur.

![Triage de la gestion des risques internes.](../media/insider-risk-triage.png)

### <a name="investigate"></a>Examiner

Examinez rapidement toutes les activités d’un utilisateur sélectionné avec [des rapports d’activité utilisateur (préversion).](insider-risk-management-activities.md#user-activity-reports-preview) Ces rapports permettent aux enquêteurs de votre organisation d’examiner les activités de certains utilisateurs pendant une période définie sans avoir à les affecter temporairement ou explicitement à une stratégie de gestion des risques internes. Après avoir examiné les activités d’un utilisateur, les enquêteurs peuvent ignorer les activités individuelles comme étant bénignes, partager ou envoyer par e-mail un lien vers le rapport avec d’autres enquêteurs, ou choisir d’affecter temporairement ou explicitement l’utilisateur à une stratégie de gestion des risques internes.

[Les cas](insider-risk-management-cases.md) sont créés pour les alertes qui nécessitent un examen et une investigation plus approfondis des détails et des circonstances de l’activité autour de la correspondance de stratégie. La **Tableau de bord des cas** fournit un affichage total de tous les cas actifs, des cas ouverts au fil du temps et des statistiques sur les cas pour votre organisation. Les réviseurs peuvent filtrer rapidement les cas par état, la date à laquelle le cas a été ouvert et la date de la dernière mise à jour du cas.

La sélection d’un cas dans le tableau de bord des cas ouvre le cas pour examen et enquête. Cette étape est au cœur du flux de travail de gestion des risques internes. C’est dans cette zone que les activités à risque, les conditions de stratégie, les détails des alertes et les détails de l’utilisateur sont synthétisés dans une vue intégrée pour les réviseurs. Les principaux outils d’investigation dans ce domaine sont les suivants :

- **Activité de l’utilisateur** : l’activité de l’utilisateur s’affiche automatiquement dans un graphique interactif qui trace les activités au fil du temps et par niveau de risque pour les activités à risque actuelles ou passées. Les réviseurs peuvent rapidement filtrer et afficher l’ensemble de l’historique des risques pour l’utilisateur et explorer des activités spécifiques pour plus d’informations.
- **Explorateur de** contenu : tous les fichiers de données et messages électroniques associés aux activités d’alerte sont automatiquement capturés et affichés dans l’Explorateur de contenu. Les réviseurs peuvent filtrer et afficher des fichiers et des messages par source de données, type de fichier, balises, conversation et bien d’autres attributs.
- **Notes de cas** : les réviseurs peuvent fournir des notes pour un cas dans la section Notes de cas. Cette liste consolide toutes les notes dans un affichage central et inclut les informations de réviseur et de date envoyées.

![Enquête sur la gestion des risques internes.](../media/insider-risk-investigate.png)

En outre, le nouveau [journal d’audit (préversion)](insider-risk-management-audit-log.md) vous permet de rester informé des actions qui ont été effectuées sur les fonctionnalités de gestion des risques internes. Cette ressource permet un examen indépendant des actions effectuées par les utilisateurs affectés à un ou plusieurs groupes de rôles de gestion des risques internes.

### <a name="action"></a>Action

Une fois les cas examinés, les réviseurs peuvent agir rapidement pour résoudre le cas ou collaborer avec d’autres parties prenantes à risque de votre organisation. Si les utilisateurs violent accidentellement ou par inadvertance les conditions de stratégie, un simple avis de rappel peut être envoyé à l’utilisateur à partir de modèles d’avis que vous pouvez personnaliser pour votre organisation. Ces avis peuvent servir de rappels simples ou peuvent diriger l’utilisateur vers une formation ou des conseils d’actualisation afin d’éviter tout comportement à risque futur. Pour plus d’informations, voir [Modèles de notifications sur la gestion des risques internes](insider-risk-management-notices.md).

Dans les situations les plus graves, vous devrez peut-être partager les informations sur les cas de gestion des risques internes avec d’autres réviseurs ou services de votre organisation. La gestion des risques internes est étroitement intégrée à d’autres solutions Microsoft Purview pour vous aider à résoudre les risques de bout en bout.

- **eDiscovery (Premium)** : l’escalade d’un cas d’enquête vous permet de transférer les données et la gestion du cas vers Microsoft Purview eDiscovery (Premium). eDiscovery (Premium) fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter du contenu qui répond aux investigations internes et externes de votre organisation. Il permet aux équipes juridiques de gérer l’ensemble du flux de travail de notification de conservation légale. Pour en savoir plus sur les cas eDiscovery (Premium), consultez [Vue d’ensemble de Microsoft Purview eDiscovery (Premium).](overview-ediscovery-20.md)
- **intégration des API de gestion Office 365 (préversion)** : la gestion des risques internes prend en charge l’exportation des informations d’alerte vers les services SIEM (Security Information and Event Management) via les API de gestion Office 365. Avoir accès aux informations d’alerte dans la plateforme le mieux adapté aux processus de risque de votre organisation vous donne plus de flexibilité dans la façon d’agir sur les activités à risque. Pour en savoir plus sur l’exportation des informations d’alerte avec Office 365 API de gestion, consultez [Exporter des alertes](insider-risk-management-settings.md#export-alerts).

> [!NOTE]
> Merci pour vos commentaires et votre support pendant la préversion du connecteur ServiceNow. Nous avons décidé de mettre fin à la préversion du connecteur ServiceNow et de ne plus prendre en charge la gestion des risques internes le 30 novembre 2020. Nous évaluons activement d’autres méthodes pour fournir aux clients l’intégration de ServiceNow dans la gestion des risques internes.

## <a name="scenarios"></a>Scénarios

La gestion des risques internes peut vous aider à détecter, examiner et prendre des mesures pour atténuer les risques internes dans votre organisation dans plusieurs scénarios courants :

### <a name="data-theft-by-departing-users"></a>Vol de données par des employés quittant votre organisation

Lorsque les utilisateurs quittent une organisation, volontairement ou à la suite d’un arrêt, il existe souvent des préoccupations légitimes quant au risque que les données de l’entreprise, du client et de l’utilisateur soient exposées. Les utilisateurs peuvent innocemment supposer que les données de projet ne sont pas propriétaires, ou ils peuvent être tentés de prendre des données d’entreprise pour un gain personnel et en violation des normes légales et de la politique de l’entreprise. Les stratégies de gestion des risques internes qui utilisent le [vol de données en quittant le modèle de stratégie des utilisateurs détectent](insider-risk-management-policies.md#policy-templates) automatiquement les activités généralement associées à ce type de vol. Avec cette stratégie, vous recevrez automatiquement des alertes pour les activités suspectes associées au vol de données en quittant les utilisateurs afin de pouvoir prendre les mesures d’enquête appropriées. La configuration d’un [connecteur RH Microsoft 365](import-hr-data.md) pour votre organisation est requise pour ce modèle de stratégie.

### <a name="intentional-or-unintentional-leak-of-sensitive-or-confidential-information"></a>Fuite intentionnelle ou involontaire d’informations sensibles ou confidentielles

Dans la plupart des cas, les utilisateurs font de leur mieux pour gérer correctement les informations sensibles ou confidentielles. Mais parfois, les utilisateurs peuvent faire des erreurs et les informations sont accidentellement partagées en dehors de votre organisation ou en violation de vos stratégies de protection des informations. Dans d’autres circonstances, les utilisateurs peuvent intentionnellement fuiter ou partager des informations sensibles et confidentielles avec une intention malveillante et pour un gain personnel potentiel. Les stratégies de gestion des risques internes créées à l’aide des modèles de stratégie de fuite de données suivants détectent automatiquement les activités généralement associées au partage d’informations sensibles ou confidentielles :

- [Fuites de données générales](insider-risk-management-policies.md#general-data-leaks)
- [Fuites de données par des utilisateurs prioritaires (aperçu)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)
- [Fuites de données par des utilisateurs mécontents (préversion)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)

## <a name="intentional-or-unintentional-security-policy-violations-preview"></a>Violations intentionnelles ou involontaires de la stratégie de sécurité (préversion)

Les utilisateurs ont généralement un grand degré de contrôle lors de la gestion de leurs appareils dans l’espace de travail moderne. Ce contrôle peut inclure des autorisations d’installation ou de désinstallation des applications nécessaires à l’exécution de leurs tâches ou la possibilité de désactiver temporairement les fonctionnalités de sécurité des appareils. Que cette activité soit accidentelle, accidentelle ou malveillante, cette conduite peut présenter un risque pour votre organisation et il est important d’identifier et d’agir pour réduire le risque. Pour vous aider à identifier ces activités de sécurité risquées, les modèles de violation de stratégie de sécurité de gestion des risques internes suivants évaluent les indicateurs de risque de sécurité et utilisent Microsoft Defender pour point de terminaison alertes pour fournir des insights sur les activités liées à la sécurité :

- [Violations générales de la stratégie de sécurité (préversion)](insider-risk-management-policies.md#general-security-policy-violations-preview)
- [Violations de stratégie de sécurité par des utilisateurs sortants (préversion)](insider-risk-management-policies.md#security-policy-violations-by-departing-users-preview)
- [Violations de la stratégie de sécurité par des utilisateurs prioritaires (préversion)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Violations de stratégie de sécurité par un utilisateur mécontent (préversion)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

## <a name="policies-for-users-based-on-position-access-level-or-risk-history-preview"></a>Stratégies pour les utilisateurs en fonction de la position, du niveau d’accès ou de l’historique des risques (préversion)

Les utilisateurs de votre organisation peuvent présenter différents niveaux de risque en fonction de leur position, du niveau d’accès aux informations sensibles ou de l’historique des risques. Cette structure peut inclure des membres de l’équipe de direction de votre organisation, des administrateurs informatiques disposant de privilèges d’accès réseau et de données étendus, ou des utilisateurs ayant des antécédents d’activités à risque. Dans ces circonstances, une inspection plus étroite et un scoring plus agressif des risques sont importants pour permettre d’afficher des alertes en vue d’une investigation et d’une action rapide. Pour identifier les activités à risque pour ces types d’utilisateurs, vous pouvez créer des groupes d’utilisateurs prioritaires et créer des stratégies à partir des modèles de stratégie suivants :

- [Violations de la stratégie de sécurité par des utilisateurs prioritaires (préversion)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Fuites de données par des utilisateurs prioritaires (aperçu)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)

## <a name="healthcare-preview"></a>Santé (préversion)

Pour les organisations du secteur de la santé, des études récentes ont révélé un taux très élevé de violations de données internes. La détection de l’utilisation abusive des données des patients et des informations sur les dossiers médicaux est un élément essentiel de la protection de la vie privée des patients et de la conformité aux réglementations de conformité telles que la Loi HIPAA (Health Insurance Portability and Accountability Act) et la Loi HITECH (Health Information Technology for Economic and Clinical Health). L’utilisation abusive des données des patients peut aller de l’accès aux dossiers de patients privilégiés à l’accès aux dossiers des patients de la famille ou des voisins ayant une intention malveillante. Pour vous aider à identifier ces types d’activités à risque, les modèles de stratégie de gestion des risques internes suivants utilisent le connecteur de ressources humaines Microsoft 365 et un connecteur de données spécifique aux soins de santé pour commencer à noter les indicateurs de risque liés aux comportements qui peuvent se produire dans vos systèmes d’enregistrement de santé électronique (DSE) :

- [Utilisation incorrecte générale des données des patients (préversion)](insider-risk-management-policies.md#general-patient-data-misuse-preview)

## <a name="actions-and-behaviors-by-disgruntled-users-preview"></a>Actions et comportements des utilisateurs mécontents (préversion)

Les événements stressants liés à l’emploi peuvent avoir un impact sur le comportement des utilisateurs de plusieurs manières liées aux risques internes. Ces facteurs de stress peuvent être une révision des performances médiocre, une rétrogradation de position ou le placement de l’utilisateur sur un plan d’évaluation des performances. Bien que la plupart des utilisateurs ne répondent pas de manière malveillante à ces événements, le stress de ces actions peut amener certains utilisateurs à prendre des actions qu’ils peuvent normalement ne pas prendre en compte dans des circonstances normales. Pour vous aider à identifier ces types d’activités à risque, les modèles de stratégie de gestion des risques internes suivants utilisent le connecteur rh Microsoft 365 et commencent à noter les indicateurs de risque liés aux comportements qui peuvent se produire à proximité des événements du stress professionnel :

- [Fuites de données par des utilisateurs mécontents (préversion)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)
- [Violations de stratégie de sécurité par un utilisateur mécontent (préversion)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

- Consultez [Plan for insider risk management](insider-risk-management-plan.md) for how to prepare to enable insider risk management policies in your organization.
- Consultez [Démarrage avec les paramètres de gestion des risques internes](insider-risk-management-settings.md) pour configurer les paramètres globaux des stratégies de risque interne.
- Consultez [Démarrage avec la gestion des risques internes](insider-risk-management-configure.md) pour configurer les prérequis, créer des stratégies et commencer à recevoir des alertes.
