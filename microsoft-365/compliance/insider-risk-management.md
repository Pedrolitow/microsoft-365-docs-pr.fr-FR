---
title: En savoir plus sur la gestion des risques internes Microsoft
description: Découvrez comment réduire les risques dans votre organisation avec la gestion des risques internes dans Microsoft Purview.
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
- highpri
- tier1
- purview-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- highpri
ms.openlocfilehash: 65ec1b52582b1cbefb9a4b995118bb7f60d0081d
ms.sourcegitcommit: 21548843708d80bc861f03ffae41457252492bb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68793314"
---
# <a name="learn-about-insider-risk-management"></a>En savoir plus sur la gestion des risques internes Microsoft

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

La gestion des risques liés aux initiés Microsoft Purview est une solution de conformité qui contribue à minimiser les risques internes en vous permettant de détecter, d'enquêter et d'agir sur les activités malveillantes et involontaires au sein de votre organisation. Les stratégies relatives aux risques d'initiés vous permettent de définir les types de risques à identifier et à détecter dans votre organisation, y compris les mesures à prendre et l'escalade des cas vers Microsoft eDiscovery (Premium) si nécessaire. Les analystes de risques de votre organisation peuvent rapidement prendre les mesures appropriées pour s'assurer que les utilisateurs respectent les normes de conformité de votre organisation.

Pour plus d’informations et pour obtenir une vue d’ensemble du processus de planification pour traiter les activités potentiellement à risque au sein de votre organisation susceptibles d’entraîner un incident de sécurité, consultez [Démarrage d’un programme de gestion des risques internes](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf).

Regardez les vidéos ci-dessous pour découvrir comment la gestion des risques internes peut aider votre organisation à prévenir, détecter et contenir les risques tout en hiérarchisant les valeurs, la culture et l’expérience utilisateur de votre organisation :

**Solution de gestion des risques internes & développement** :
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4j9CN]
<br>

**Workflow de gestion des risques internes** :
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

Regardez la [vidéo Microsoft Mechanics](https://www.youtube.com/watch?v=Ynkfu8OF0wQ) sur la façon dont la gestion des risques internes et la conformité des communications fonctionnent ensemble pour réduire les risques liés aux données des utilisateurs de votre organisation.

> [!IMPORTANT]
> La gestion des risques internes est actuellement disponible dans les locataires hébergés dans des régions et des pays géographiques pris en charge par les dépendances de service Azure. Pour vérifier que la gestion des risques internes est prise en charge pour votre organisation, consultez [Disponibilité des dépendances Azure par pays/région](/troubleshoot/azure/general/dependency-availability-by-country).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="modern-risk-pain-points"></a>Points faibles du risque moderne

La gestion et la réduction des risques au sein de votre organisation commencent par la compréhension des types de risques présents sur le lieu de travail moderne. Certains risques sont pilotés par des événements et des facteurs externes qui échappent au contrôle direct. D’autres risques sont pilotés par les événements internes et les actions de l’utilisateur qui peuvent être réduits et évités. Voici quelques exemples de risques liés à des comportements et actions illégaux, inappropriés, non autorisés ou contraires à l’éthique par les utilisateurs de votre organisation. Ces comportements incluent un large éventail de risques internes des utilisateurs :

- Fuites de données sensibles et fuite de données
- Violations de confidentialité
- Vol de propriété intellectuelle (IP)
- Fraude
- Délit d’initié
- Violations de la conformité avec la réglementation

Les utilisateurs de l’espace de travail moderne ont accès à la création, à la gestion et au partage de données sur un large éventail de plateformes et de services. Dans la plupart des cas, les organisations disposent de ressources et d’outils limités pour identifier et atténuer les risques à l’échelle de l’organisation tout en respectant les normes de confidentialité des utilisateurs.

La gestion des risques internes utilise toute l’étendue des indicateurs de service et tiers pour vous aider à identifier, trier et agir rapidement sur les activités à risque. En utilisant les journaux de Microsoft 365 et de Microsoft Graph, la gestion des risques internes vous permet de définir des stratégies spécifiques pour identifier les indicateurs de risque. Ces stratégies vous permettent d’identifier les activités à risque et d’agir pour atténuer ces risques.

La gestion des risques internes est centrée sur les principes suivants :

- **Transparence** : équilibrez la confidentialité des utilisateurs par rapport au risque de l’organisation avec l’architecture de confidentialité par conception.
- **Configurable** : stratégies configurables en fonction du secteur d’activité, de la zone géographique et des groupes d’entreprises.
- **Intégré** : flux de travail intégré dans les solutions Microsoft Purview.
- **Actionnable** : fournit des insights pour activer les notifications des réviseurs, les investigations de données et les investigations utilisateur.

## <a name="identifying-potential-risks-with-analytics"></a>Identification des risques potentiels avec l’analytique

L’analyse des risques internes vous permet d’effectuer une évaluation des risques internes potentiels au sein de votre organisation sans aucune configuration de stratégie des risques internes. Cette évaluation peut permettre à votre organisation d’identifier des zones potentielles plus élevées de risque utilisateur et vous aider à déterminer le type et l’étendue des stratégies de gestion des risques internes que vous pouvez envisager de configurer. Cette évaluation peut également vous aider à déterminer les besoins en matière de licences supplémentaires ou d’optimisation future des stratégies de risque internes existantes.

Pour en savoir plus sur l’analytique des risques internes, consultez [Paramètres de gestion des risques internes : Analytique](insider-risk-management-settings.md#analytics).

## <a name="get-started-with-recommended-actions-preview"></a>Prise en main des actions recommandées (préversion)

Que vous configuriez la gestion des risques internes pour la première fois ou que vous ayez commencé à créer de nouvelles stratégies, les nouvelles [actions recommandées](insider-risk-management-configure.md#recommended-actions-preview) peuvent vous aider à tirer le meilleur parti des fonctionnalités de gestion des risques internes. Les actions recommandées incluent la configuration des autorisations, le choix d’indicateurs de stratégie, la création d’une stratégie, etc.

## <a name="workflow"></a>Flux de travail

Le workflow de gestion des risques internes vous permet d’identifier, d’examiner et de prendre des mesures pour traiter les risques internes dans votre organisation. Avec des modèles de stratégie ciblés, une signalisation d’activité complète dans le service Microsoft 365 et des outils de gestion des alertes et des cas, vous pouvez utiliser des insights actionnables pour identifier et agir rapidement sur les comportements à risque.

L’identification et la résolution des activités à risque internes et des problèmes de conformité avec la gestion des risques internes utilisent le workflow suivant :

![Workflow de gestion des risques internes.](../media/insider-risk-workflow.png)

### <a name="policies"></a>Politiques

[Les stratégies de gestion des risques internes](insider-risk-management-policies.md) sont créées à l’aide de modèles prédéfinis et de conditions de stratégie qui définissent les événements déclencheurs et les indicateurs de risque examinés dans votre organisation. Ces conditions incluent la façon dont les indicateurs de risque sont utilisés pour les alertes, les utilisateurs inclus dans la stratégie, les services hiérarchisés et la période de détection.

Vous pouvez choisir parmi les modèles de stratégie suivants pour commencer rapidement avec la gestion des risques internes :

- [Vol de données par des employés quittant votre organisation](insider-risk-management-policies.md#data-theft-by-departing-users)
- [Fuites de données](insider-risk-management-policies.md#data-leaks)
- [Fuites de données par des utilisateurs prioritaires (aperçu)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)
- [Fuites de données par des utilisateurs à risque (préversion)](insider-risk-management-policies.md#data-leaks-by-risky-users-preview)
- [Violations de stratégie de sécurité (préversion)](insider-risk-management-policies.md#security-policy-violations-preview)
- [Mauvaise utilisation des données des patients (préversion)](insider-risk-management-policies.md#patient-data-misuse-preview)
- [Violations de stratégie de sécurité par des utilisateurs sortants (préversion)](insider-risk-management-policies.md#security-policy-violations-by-departing-users-preview)
- [Violations de la stratégie de sécurité par des utilisateurs prioritaires (préversion)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Violations de stratégie de sécurité par les utilisateurs à risque (préversion)](insider-risk-management-policies.md#security-policy-violations-by-risky-users-preview)

![Tableau de bord de stratégie de gestion des risques internes.](../media/insider-risk-policy-dashboard.png)

### <a name="alerts"></a>Alertes

Les alertes sont générées automatiquement par des indicateurs de risque qui correspondent aux conditions de stratégie et sont affichées dans le [tableau de bord Alertes](insider-risk-management-activities.md#alert-dashboard). Ce tableau de bord autorise un affichage rapide de toutes les alertes nécessitant un examen, des alertes ouvertes au fil du temps et des statistiques des alertes pour votre organisation. Toutes les alertes de stratégie sont affichées avec les informations suivantes pour vous aider à identifier rapidement l’état des alertes existantes et des nouvelles alertes qui nécessitent une action :

- État
- Severity
- Heure détectée
- Cas
- État de l’incident

![Tableau de bord des alertes de gestion des risques internes.](../media/insider-risk-alerts-dashboard.png)

### <a name="triage"></a>Triage

Les nouvelles activités de l’utilisateur qui nécessitent une investigation génèrent automatiquement des alertes auxquelles un état *de révision a besoin* est attribué. Les réviseurs peuvent rapidement identifier et examiner, évaluer et trier ces alertes.

Les alertes sont résolues par l'ouverture d'un nouveau cas, l'affectation de l'alerte à un cas existant ou le rejet de l'alerte. À l’aide de filtres d’alerte, il est facile d’identifier rapidement les alertes par état, gravité ou heure de détection. Dans le cadre du processus de triage, les réviseurs peuvent afficher les détails des alertes pour les activités identifiées par la stratégie, afficher l’activité de l’utilisateur associée à la correspondance de stratégie, voir la gravité de l’alerte et passer en revue les informations de profil utilisateur.

![Triage de la gestion des risques internes.](../media/insider-risk-triage.png)

### <a name="investigate"></a>Examiner

Examinez rapidement toutes les activités à risque pour un utilisateur sélectionné avec les [rapports d’activité utilisateur (préversion)](insider-risk-management-activities.md#user-activity-reports) . Ces rapports permettent aux enquêteurs de votre organisation d’examiner les activités d’utilisateurs spécifiques pendant une période définie sans avoir à les affecter temporairement ou explicitement à une stratégie de gestion des risques internes. Après avoir examiné les activités d’un utilisateur, les enquêteurs peuvent ignorer les activités individuelles comme étant bénignes, partager ou envoyer par e-mail un lien vers le rapport avec d’autres enquêteurs, ou choisir d’affecter l’utilisateur temporairement ou explicitement à une stratégie de gestion des risques internes.

[Les cas](insider-risk-management-cases.md) sont créés pour les alertes qui nécessitent un examen approfondi des détails de l’activité et des circonstances relatives à la correspondance de stratégie. La **Tableau de bord des cas** fournit un affichage total de tous les cas actifs, des cas ouverts au fil du temps et des statistiques sur les cas pour votre organisation. Les réviseurs peuvent rapidement filtrer les cas par état, la date d’ouverture du cas et la date de la dernière mise à jour du cas.

La sélection d’un cas dans le tableau de bord des cas ouvre le cas pour examen et enquête. Cette étape est au cœur du workflow de gestion des risques internes. C’est dans ce domaine que les activités à risque, les conditions de stratégie, les détails des alertes et les détails de l’utilisateur sont synthétisés dans une vue intégrée pour les réviseurs. Les principaux outils d’investigation dans ce domaine sont les suivants :

- **Activité de l’utilisateur** : l’activité à risque de l’utilisateur s’affiche automatiquement dans un graphique interactif qui trace les activités au fil du temps et par niveau de risque pour les activités à risque actuelles ou passées. Les réviseurs peuvent rapidement filtrer et afficher l’ensemble de l’historique des risques pour l’utilisateur et explorer des activités spécifiques pour plus de détails.
- **Explorateur de** contenu : tous les fichiers de données et messages électroniques associés aux activités d’alerte sont automatiquement capturés et affichés dans l’Explorateur de contenu. Les réviseurs peuvent filtrer et afficher les fichiers et les messages par source de données, type de fichier, balises, conversation et bien d’autres attributs.
- **Notes sur les cas** : les réviseurs peuvent fournir des notes pour un cas dans la section Notes sur le cas. Cette liste regroupe toutes les notes dans une vue centrale et inclut les informations du réviseur et de la date d’envoi.

![Enquête sur la gestion des risques internes.](../media/insider-risk-investigate.png)

En outre, le nouveau [journal d’audit (préversion)](insider-risk-management-audit-log.md) vous permet de rester informé des actions effectuées sur les fonctionnalités de gestion des risques internes. Cette ressource permet un examen indépendant des actions effectuées par les utilisateurs affectés à un ou plusieurs groupes de rôles de gestion des risques internes.

### <a name="action"></a>Action

Une fois les cas examinés, les réviseurs peuvent agir rapidement pour résoudre le cas ou collaborer avec d’autres parties prenantes à risque de votre organisation. Si les utilisateurs violent accidentellement ou par inadvertance les conditions de la stratégie, une simple notification de rappel peut être envoyée à l’utilisateur à partir de modèles de notification que vous pouvez personnaliser pour votre organisation. Ces avis peuvent servir de rappels simples ou diriger l’utilisateur vers une formation de mise à jour ou des conseils pour éviter les comportements à risque futurs. Pour plus d’informations, voir [Modèles de notifications sur la gestion des risques internes](insider-risk-management-notices.md).

Dans des situations plus graves, vous devrez peut-être partager les informations de cas de gestion des risques internes avec d’autres réviseurs ou services de votre organisation. La gestion des risques internes est étroitement intégrée à d’autres solutions Microsoft Purview pour vous aider à résoudre les risques de bout en bout.

- **eDiscovery (Premium)** : l’escalade d’un cas pour investigation vous permet de transférer les données et la gestion du cas vers Microsoft Purview eDiscovery (Premium). eDiscovery (Premium) fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter du contenu qui répond aux investigations internes et externes de votre organisation. Il permet aux équipes juridiques de gérer l’ensemble du flux de travail de notification de conservation légale. Pour en savoir plus sur les cas eDiscovery (Premium), consultez [Vue d’ensemble de Microsoft Purview eDiscovery (Premium)](overview-ediscovery-20.md).
- **Intégration des API de gestion des Office 365 (préversion)** : la gestion des risques internes prend en charge l’exportation des informations d’alerte vers les services SIEM (Security Information and Event Management) via les API de gestion des Office 365. L’accès aux informations d’alerte dans la plateforme correspond le mieux aux processus de risque de votre organisation vous donne plus de flexibilité dans la façon d’agir sur les activités à risque. Pour en savoir plus sur l’exportation des informations d’alerte avec les API de gestion des Office 365, consultez [Exporter des alertes](insider-risk-management-settings.md#export-alerts).

> [!NOTE]
> Merci pour vos commentaires et votre support lors de la préversion du connecteur ServiceNow. Nous avons décidé de mettre fin à la préversion du connecteur ServiceNow et d’arrêter la prise en charge de la gestion des risques internes le 30 novembre 2020. Nous évaluons activement d’autres méthodes pour fournir aux clients l’intégration de ServiceNow dans la gestion des risques internes.

## <a name="scenarios"></a>Scénarios

La gestion des risques internes peut vous aider à détecter, examiner et prendre des mesures pour atténuer les risques internes dans votre organisation dans plusieurs scénarios courants :

### <a name="data-theft-by-departing-users"></a>Vol de données par des employés quittant votre organisation

Lorsque des utilisateurs quittent une organisation, soit volontairement, soit à la suite d’une résiliation, il existe souvent des préoccupations légitimes selon laquelle les données de l’entreprise, des clients et des utilisateurs sont menacées. Les utilisateurs peuvent supposer innocemment que les données du projet ne sont pas propriétaires, ou ils peuvent être tentés de prendre les données de l’entreprise à des fins personnelles et en violation de la politique et des normes juridiques de l’entreprise. Les stratégies de gestion des risques internes qui utilisent le modèle [de stratégie Vol de données en quittant les utilisateurs](insider-risk-management-policies.md#policy-templates) détectent automatiquement les activités généralement associées à ce type de vol. Avec cette stratégie, vous recevez automatiquement des alertes pour les activités suspectes associées au vol de données par les utilisateurs sortants afin que vous puissiez prendre les mesures d’investigation appropriées. La configuration d’un [connecteur Microsoft 365 RH](import-hr-data.md) pour votre organisation est requise pour ce modèle de stratégie.

### <a name="intentional-or-unintentional-leak-of-sensitive-or-confidential-information"></a>Fuite intentionnelle ou involontaire d’informations sensibles ou confidentielles

Dans la plupart des cas, les utilisateurs font de leur mieux pour gérer correctement les informations sensibles ou confidentielles. Mais parfois, les utilisateurs peuvent faire des erreurs et les informations sont partagées accidentellement en dehors de votre organisation ou en violation de vos stratégies de protection des informations. Dans d’autres circonstances, les utilisateurs peuvent intentionnellement divulguer ou partager des informations sensibles et confidentielles avec des intentions malveillantes et pour un gain personnel potentiel. Les stratégies de gestion des risques internes créées à l’aide des modèles de stratégie fuites de données suivants détectent automatiquement les activités généralement associées au partage d’informations sensibles ou confidentielles :

- [Fuites de données](insider-risk-management-policies.md#data-leaks)
- [Fuites de données par des utilisateurs prioritaires (aperçu)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)
- [Fuites de données par des utilisateurs à risque (préversion)](insider-risk-management-policies.md#data-leaks-by-risky-users-preview)

### <a name="intentional-or-unintentional-security-policy-violations-preview"></a>Violations intentionnelles ou involontaires de la stratégie de sécurité (préversion)

Les utilisateurs ont généralement un grand degré de contrôle lors de la gestion de leurs appareils dans l’espace de travail moderne. Ce contrôle peut inclure des autorisations pour installer ou désinstaller les applications nécessaires à l’exécution de leurs tâches ou la possibilité de désactiver temporairement les fonctionnalités de sécurité des appareils. Que cette activité à risque soit accidentelle, accidentelle ou malveillante, cette conduite peut présenter un risque pour votre organisation et il est important d’identifier et d’agir pour minimiser. Pour aider à identifier ces activités de sécurité à risque, les modèles de violation de stratégie de sécurité de gestion des risques internes suivants évaluent les indicateurs de risque de sécurité et utilisent des alertes Microsoft Defender pour point de terminaison pour fournir des insights sur les activités liées à la sécurité :

- [Violations de stratégie de sécurité (préversion)](insider-risk-management-policies.md#security-policy-violations-preview)
- [Violations de stratégie de sécurité par des utilisateurs sortants (préversion)](insider-risk-management-policies.md#security-policy-violations-by-departing-users-preview)
- [Violations de la stratégie de sécurité par des utilisateurs prioritaires (préversion)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Violations de stratégie de sécurité par les utilisateurs à risque (préversion)](insider-risk-management-policies.md#security-policy-violations-by-risky-users-preview)

### <a name="policies-for-users-based-on-position-access-level-or-risk-history-preview"></a>Stratégies pour les utilisateurs basées sur la position, le niveau d’accès ou l’historique des risques (préversion)

Les utilisateurs de votre organisation peuvent avoir différents niveaux de risque en fonction de leur position, de leur niveau d’accès aux informations sensibles ou de leur historique des risques. Cette structure peut inclure des membres de l’équipe de direction de votre organisation, des administrateurs informatiques disposant de privilèges d’accès réseau et de données étendus, ou des utilisateurs ayant des antécédents d’activités à risque. Dans ces circonstances, une inspection plus approfondie et un scoring de risque plus agressif sont importants pour aider à faire apparaître des alertes en vue d’une investigation et d’une action rapide. Pour aider à identifier les activités à risque pour ces types d’utilisateurs, vous pouvez créer des groupes d’utilisateurs prioritaires et créer des stratégies à partir des modèles de stratégie suivants :

- [Violations de la stratégie de sécurité par des utilisateurs prioritaires (préversion)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Fuites de données par des utilisateurs prioritaires (aperçu)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)

### <a name="healthcare-preview"></a>Soins de santé (préversion)

Pour les organisations du secteur de la santé, des études récentes ont révélé un taux très élevé de violations de données internes. La détection d’une mauvaise utilisation des données des patients et des informations relatives aux dossiers médicaux est un élément essentiel de la protection de la vie privée des patients et du respect des réglementations de conformité telles que la loi HIPAA (Health Insurance Portability and Accountability Act) et la loi HITECH (Health Information Technology for Economic and Clinical Health). L’utilisation abusive des données des patients peut aller de l’accès aux dossiers privilégiés des patients à l’accès aux dossiers de patients de la famille ou des voisins avec une intention malveillante. Pour identifier ces types d’activités à risque, les modèles de stratégie de gestion des risques internes suivants utilisent le connecteur Microsoft 365 RH et un connecteur de données spécifique aux soins de santé pour commencer à évaluer les indicateurs de risque liés aux comportements qui peuvent se produire dans vos systèmes d’enregistrement de santé électronique (DSE) :

- [Mauvaise utilisation des données des patients (préversion)](insider-risk-management-policies.md#patient-data-misuse-preview)

### <a name="actions-and-behaviors-by-risky-users-preview"></a>Actions et comportements des utilisateurs à risque (préversion)

Les événements stressants liés à l’emploi peuvent avoir un impact sur le comportement de l’utilisateur de plusieurs manières liées aux risques internes. Ces facteurs de stress peuvent être une évaluation médiocre des performances, une rétrogradation de poste ou l’utilisateur placé sur un plan d’évaluation des performances. Les facteurs de stress peuvent également entraîner un comportement potentiellement inapproprié, comme l’envoi par des utilisateurs d’un langage potentiellement menaçant, harcelant ou discriminatoire dans des e-mails et d’autres messages. Bien que la plupart des utilisateurs ne répondent pas de manière malveillante à ces événements, le stress de ces actions peut conduire certains utilisateurs à se comporter d’une manière qu’ils ne peuvent normalement pas envisager dans des circonstances normales. Pour aider à identifier ces types d’activités potentiellement risquées, les modèles de stratégie de gestion des risques internes suivants peuvent utiliser le connecteur RH et/ou l’intégration avec une stratégie de [conformité de communication dédiée](/microsoft-365/compliance/communication-compliance-policies#integration-with-insider-risk-management-preview) pour amener les utilisateurs dans l’étendue des stratégies de gestion des risques internes et commencer à évaluer les indicateurs de risque liés aux comportements qui peuvent se produire :

- [Fuites de données par des utilisateurs à risque (préversion)](insider-risk-management-policies.md#data-leaks-by-risky-users-preview)
- [Violations de stratégie de sécurité par les utilisateurs à risque (préversion)](insider-risk-management-policies.md#security-policy-violations-by-risky-users-preview)

### <a name="visual-context-for-potentially-risky-user-activities-with-forensic-evidence-preview"></a>Contexte visuel pour les activités potentiellement risquées des utilisateurs avec des preuves forensiques (préversion)

Le contexte visuel est essentiel pour les équipes de sécurité pendant les enquêtes judiciaires afin d’obtenir de meilleures informations sur les activités potentiellement risquées des utilisateurs susceptibles d’entraîner un incident de sécurité. Cela peut inclure la capture visuelle de ces activités pour aider à évaluer si elles sont effectivement risquées ou prises hors de contexte et non potentiellement risquées. Pour les activités jugées risquées, le fait de disposer de captures de preuves forensiques peut aider les enquêteurs et votre organisation à mieux les atténuer, les comprendre et y répondre. Pour faciliter ce scénario, [activez la capture de preuves forensiques](insider-risk-management-forensic-evidence.md) pour les appareils en ligne et hors connexion de votre organisation.

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

- Consultez [Planifier la gestion des risques internes](insider-risk-management-plan.md) pour savoir comment préparer l’activation des stratégies de gestion des risques internes dans votre organisation.
- Consultez [Prise en main des paramètres de gestion des risques internes](insider-risk-management-settings.md) pour configurer les paramètres globaux des stratégies de risque interne.
- Consultez [Prise en main de la gestion des risques internes](insider-risk-management-configure.md) pour configurer les prérequis, créer des stratégies et commencer à recevoir des alertes.
