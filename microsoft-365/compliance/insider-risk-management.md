---
title: Gestion des risques internes
description: Découvrez comment limiter les risques au sein de votre organisation avec la gestion des risques initiés dans Microsoft 365.
keywords: Microsoft 365, Insider Risk, gestion des risques, conformité
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
ms.openlocfilehash: c9b19066b57d40ad33ac8d50ee1bee1f4a828030
ms.sourcegitcommit: 45c0afcf958069c5c1b31f9b6c762d8dd806e1e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "48774047"
---
# <a name="insider-risk-management-in-microsoft-365"></a>Gestion des risques internes dans Microsoft 365

La gestion des risques initiés est une solution de conformité dans Microsoft 365 qui permet de réduire les risques internes en vous permettant de détecter, d’examiner et d’agir sur les activités malveillantes et involontaires dans votre organisation. Les stratégies de risque d’initié vous permettent de définir les types de risques à identifier et à détecter dans votre organisation, notamment en agissant sur les incidents et en transférant les incidents à Microsoft Advanced eDiscovery si nécessaire. Les analystes de risques de votre organisation peuvent rapidement prendre les mesures appropriées pour s’assurer que les utilisateurs sont conformes aux normes de conformité de votre organisation.

Regardez la vidéo ci-dessous pour découvrir comment la gestion des risques internes peut aider votre organisation à prévenir, détecter et concourir les risques tout en hiérarchisant les valeurs, la culture et l’expérience utilisateur de votre organisation :
<br>
<br>
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4j9CN]

## <a name="modern-risk-pain-points"></a>Points névralgiques des risques modernes

La gestion et la réduction des risques au sein de votre organisation commencent par la compréhension des types de risques présents sur le lieu de travail moderne. Certains risques sont pilotés par des événements externes et des facteurs qui se trouvent en dehors du contrôle direct. Les autres risques sont dictés par les événements internes et les activités de l’utilisateur qui peuvent être minimisés et évités. Certains exemples sont des risques de comportements illégaux, inappropriés, non autorisés ou non éthiques, et les actions effectuées par les utilisateurs de votre organisation. Ces comportements incluent une large gamme de risques internes pour les utilisateurs :

- Fuites de données sensibles et de dépassements de données
- Violations de confidentialité
- Vol de propriété intellectuelle (IP)
- Fraude
- Délit d’initié
- Violations de la conformité avec la réglementation

Les utilisateurs du lieu de travail moderne ont accès à la création, la gestion et le partage de données sur un large éventail de plateformes et de services. Dans la plupart des cas, les organisations disposent de ressources et d’outils limités pour identifier et atténuer les risques à l’échelle de l’organisation, tout en respectant les normes de confidentialité de l’utilisateur.

La gestion des risques initiés par les utilisateurs utilise l’ensemble complet des indicateurs de service et de tiers pour vous aider à identifier rapidement, à trier et à agir sur l’activité des risques. À l’aide des journaux Microsoft 365 et Microsoft Graph, la gestion des risques internes vous permet de définir des stratégies spécifiques pour identifier les indicateurs de risques. Ces stratégies vous permettent d’identifier les activités à risque et d’agir pour atténuer ces risques.

La gestion des risques initiés est axée sur les principes suivants :

- **Transparence** : équilibrer la confidentialité des utilisateurs et l’Organisation des risques avec l’architecture de confidentialité.
- **Configurable** : stratégies configurables basées sur les groupes de secteur industriel, géographique et d’entreprise.
- **Intégré** : flux de travail intégré dans les solutions de conformité Microsoft 365.
- **Exploitable** : fournit des informations pour activer les notifications utilisateur, les enquêtes de données et les investigations utilisateur.

## <a name="workflow"></a>Flux de travail

Le flux de travail de gestion des risques Insiders vous permet d’identifier, d’analyser et de prendre des mesures pour résoudre les risques internes au sein de votre organisation. Les modèles de stratégie ciblés, la signalisation d’activité complète via le service Microsoft 365, ainsi que les outils de gestion des alertes et des cas, vous pouvez utiliser des informations exploitables pour identifier et agir rapidement sur le comportement à risque.

L'identification et la résolution des activités à risque internes et des problèmes de conformité avec la gestion des risques internes dans Microsoft 365 utilise le flux de travail suivant :

![Flux de travail de gestion des risques internes](../media/insider-risk-workflow.png)

### <a name="policies"></a>Stratégies

Les [stratégies de gestion des risques initiés](insider-risk-management-policies.md) sont créées à l’aide de modèles prédéfinis et de conditions de stratégie qui définissent ce que les événements déclencheurs et les indicateurs de risque sont examinés dans votre organisation. Ces conditions incluent le mode d’utilisation des indicateurs de risque pour les alertes, les utilisateurs inclus dans la stratégie, les services classés par ordre de priorité et la période de surveillance.

Vous pouvez sélectionner l’un des modèles de stratégie suivants pour commencer rapidement à utiliser la gestion des risques initiés :

- [Vol de données en faisant part des utilisateurs](insider-risk-management-policies.md#data-theft-by-departing-users)
- [Fuites de données générales](insider-risk-management-policies.md#general-data-leaks)
- [Fuites de données par les utilisateurs prioritaires (aperçu)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)
- [Fuites de données par les utilisateurs mécontents (aperçu)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)
- [Violations de stratégie de sécurité générale (préversion)](insider-risk-management-policies.md#general-security-policy-violations-preview)
- [Violations de stratégie de sécurité en faisant ressorter les utilisateurs (aperçu)](insider-risk-management-policies.md#security-policy-violations-by-departing-users-preview)
- [Violations de stratégie de sécurité par utilisateurs prioritaires (aperçu)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Violations de stratégie de sécurité par des utilisateurs mécontents (aperçu)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)
- [Langage offensant dans les messages électroniques](insider-risk-management-policies.md#offensive-language-in-email)

![Tableau de bord des stratégies de gestion des risques internes](../media/insider-risk-policy-dashboard.png)

### <a name="alerts"></a>Alertes

Les alertes sont automatiquement générées par des indicateurs de risque qui correspondent aux conditions de la stratégie et sont affichés dans le [tableau de bord des alertes](insider-risk-management-alerts.md). Ce tableau de bord permet d’afficher un aperçu rapide de toutes les alertes nécessitant une révision, d’ouvrir des alertes dans le temps et de statistiques d’alerte pour votre organisation. Toutes les alertes de stratégie s’affichent avec les informations suivantes pour vous aider à identifier rapidement l’état des alertes existantes et de nouvelles alertes qui nécessitent une action :

- Statut
- Severity
- Heure de détection
- Cas
- État de l’incident

![Tableau de bord d’alerte de gestion des risques Insiders](../media/insider-risk-alerts-dashboard.png)

### <a name="triage"></a>Tri

Les nouvelles activités des utilisateurs qui ont besoin d’une enquête génèrent automatiquement des alertes auxquelles l’état de *révision des besoins* est affecté. Les relecteurs peuvent rapidement identifier et vérifier, évaluer et trier ces alertes.

Les alertes sont résolues par l'ouverture d'un nouveau cas, l'affectation de l'alerte à un cas existant ou le rejet de l'alerte. À l’aide de filtres d’alerte, il est facile d’identifier rapidement les alertes en fonction de l’État, de la gravité ou du temps détecté. Dans le cadre du processus de triage, les relecteurs peuvent afficher les détails de l’alerte pour les activités identifiées par la stratégie, afficher l’activité de l’utilisateur associée à la correspondance de stratégie, voir la gravité de l’alerte et vérifier les informations de profil utilisateur.

![Triage de la gestion des risques initiés](../media/insider-risk-triage.png)

### <a name="investigate"></a>Examiner

Des [cas](insider-risk-management-cases.md) sont créés pour les alertes qui nécessitent une révision et une analyse approfondies des détails de l’activité et des circonstances entourant la correspondance de stratégie. Le **tableau de bord de cas** fournit une vue d’ensemble de tous les incidents actifs, des incidents ouverts au fil du temps et des statistiques de cas pour votre organisation. Les relecteurs peuvent rapidement filtrer les incidents par État, date d’ouverture et date de la dernière mise à jour du cas.

La sélection d’un cas dans le tableau de bord de cas ouvre le cas à des fins d’examen et de révision. Cette étape est le cœur du flux de travail de gestion des risques Insiders. Ce domaine est l’endroit où les activités de risque, les conditions de la stratégie, les détails des alertes et les détails de l’utilisateur sont synthétisés dans un mode intégré pour les relecteurs. Les principaux outils d’enquête de cette zone sont les suivants :

- **Activité** de l’utilisateur : l’activité de l’utilisateur est automatiquement affichée dans un graphique interactif qui représente les activités dans le temps et selon le niveau de risque pour les activités actuelles ou passées. Les relecteurs peuvent rapidement filtrer et afficher l’historique des risques de l’utilisateur et effectuer des recherches dans des activités spécifiques pour obtenir plus d’informations.
- **Explorateur de contenu** : tous les fichiers de données et les messages électroniques associés aux activités d’alerte sont automatiquement capturés et affichés dans l’Explorateur de contenu. Les relecteurs peuvent filtrer et afficher les fichiers et les messages par source de données, type de fichier, balises, conversation et bien d’autres attributs.
- **Notes de cas** : les relecteurs peuvent fournir des notes pour un cas dans la section Notes de cas. Cette liste consolide toutes les notes dans une vue centrale et inclut les informations de réviseur et de date d’envoi.

![Enquête sur la gestion des risques des Insiders](../media/insider-risk-investigate.png)

### <a name="action"></a>Action

Après enquête, les réviseurs peuvent rapidement agir pour résoudre le cas ou collaborer avec les autres parties prenantes du risque au sein de votre organisation. Si des utilisateurs enfreignent accidentellement ou par inadvertance des conditions de stratégie, un simple avertissement de rappel peut être envoyé à l’utilisateur à partir de modèles de notification que vous pouvez personnaliser pour votre organisation. Ces notifications peuvent servir de rappels simples ou inviter l’utilisateur à effectuer une formation ou des conseils de réactualisation afin de prévenir un futur comportement risqué. Pour plus d’informations, reportez-vous à la rubrique [modèles d’avis de gestion des risques internes](insider-risk-management-notices.md).

Dans les situations les plus graves, vous devrez peut-être partager les informations de cas de gestion des risques Insider avec d’autres réviseurs ou services dans votre organisation. La gestion des risques initiés est étroitement intégrée aux autres solutions de conformité Microsoft 365 pour vous aider à résoudre les risques de bout en bout.

- **Advanced eDiscovery** : le remontage d’un cas pour l’enquête vous permet de transférer des données et de gérer le cas vers Advanced EDiscovery dans Microsoft 365. Advanced eDiscovery fournit un flux de travail intégral pour préserver, collecter, examiner, analyser et exporter du contenu adapté aux examens internes et externes de votre organisation. Il permet aux équipes juridiques de gérer l’ensemble du flux de travail de notification de conservation légale. Pour en savoir plus sur les cas Advanced eDiscovery, consultez [Présentation de Advanced eDiscovery dans Microsoft 365](overview-ediscovery-20.md).
- **ServiceNow (aperçu)** : ServiceNow est une plateforme de Cloud Computing populaire qui aide les organisations à gérer les flux de travail numériques pour les opérations d’entreprise. La gestion des risques initiés prend en charge le partage des alertes de cas avec votre service ServiceNow et vous permet de créer des demandes d’incident et de modification liées à des cas particuliers de risque d’initié. Pour en savoir plus sur le partage des informations d’alerte avec ServiceNow, voir [partager un cas avec ServiceNow](insider-risk-management-cases.md#share-the-case).
- **Office 365 Management API Integration (Preview)** : la gestion des risques internes prend en charge l’exportation des informations d’alerte vers les services d’informations de sécurité et de gestion des événements via les API de gestion d’Office 365. L’accès aux informations d’alerte dans la plateforme le mieux adapté aux processus de risque de votre organisation vous offre plus de flexibilité dans la procédure à suivre pour agir sur les activités à risque. Pour en savoir plus sur l’exportation des informations d’alerte avec les API de gestion d’Office 365, consultez la rubrique [Export Alerts](insider-risk-management-settings.md#export-alerts-preview).

>[!NOTE]
>La version d’évaluation de ServiceNow se terminera le 1er novembre 30 2020 et ne sera pas poursuivie. Nous vous remercions de vos commentaires et de votre soutien pendant que nous déterminons les étapes suivantes.

## <a name="scenarios"></a>Scénarios

La gestion des risques initiés peut vous aider à détecter, examiner et prendre des mesures pour atténuer les risques internes dans votre organisation dans plusieurs scénarios courants :

### <a name="data-theft-by-departing-users"></a>Vol de données en faisant part des utilisateurs

Lorsque les utilisateurs quittent une organisation, volontairement ou à la suite d’une résiliation, il existe souvent des problèmes légitimes que les données de l’entreprise, du client et de l’utilisateur sont menacées. Les utilisateurs peuvent inoffensifment supposer que les données de projet ne sont pas propriétaires ou peuvent être tentées de prendre des données d’entreprise à des fins de profit personnel et de violation de la politique de l’entreprise et des normes juridiques. Les stratégies de gestion des risques internes qui utilisent le modèle de stratégie des [utilisateurs](insider-risk-management-policies.md#policy-templates) qui se dépêchent détectent automatiquement les activités généralement associées à ce type de vol. Grâce à cette stratégie, vous recevrez automatiquement des alertes pour les activités suspectes associées au vol de données en déposant des utilisateurs, afin de prendre les mesures d’investigation appropriées. La configuration d’un [connecteur RH Microsoft 365](import-hr-data.md) pour votre organisation est requise pour ce modèle de stratégie.

### <a name="intentional-or-unintentional-leak-of-sensitive-or-confidential-information"></a>Fuite intentionnelle ou involontaire d’informations sensibles ou confidentielles

Dans la plupart des cas, les utilisateurs essaient de traiter correctement les informations sensibles ou confidentielles. Toutefois, les utilisateurs peuvent parfois faire des erreurs et des informations qui sont partagées par inadvertance à l’extérieur de votre organisation ou en violation de vos stratégies de protection des informations. Dans d’autres circonstances, les utilisateurs peuvent intentionnellement divulguer ou partager des informations sensibles et confidentielles à des fins malveillantes et potentielles. Les stratégies de gestion des risques internes créées à l’aide des informations de fuite de données suivantes détectent automatiquement les activités généralement associées au partage d’informations sensibles ou confidentielles :

- [Fuites de données générales](insider-risk-management-policies.md#general-data-leaks)
- [Fuites de données par les utilisateurs prioritaires (aperçu)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)
- [Fuites de données par les utilisateurs mécontents (aperçu)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)

### <a name="offensive-behavior-that-violates-corporate-policies"></a>Comportement offensant qui enfreint les stratégies d’entreprise

Les communications entre utilisateurs sont souvent une source de violations accidentelle ou malveillante des stratégies d’entreprise. Ces violations peuvent inclure un langage offensant, des menaces et un harcèlement entre les utilisateurs. Ce type d’activité contribue à un environnement de travail hostile et peut entraîner des actions judiciaires contre les utilisateurs et l’organisation plus importante. La gestion des risques des Insiders utilise de nouveaux classifieurs Microsoft 365 intégrés et le [langage offensant dans](insider-risk-management-policies.md#offensive-language-in-email) le modèle de stratégie de messagerie pour réduire ces risques. Ce modèle de stratégie vous permet de configurer et d’activer rapidement une stratégie pour détecter automatiquement et vous avertir de ce type de comportement dans votre organisation.

## <a name="intentional-or-unintentional-security-policy-violations-preview"></a>Violations de stratégie de sécurité intentionnelles ou involontaires (préversion)

Les utilisateurs ont généralement un grand degré de contrôle lors de la gestion de leurs appareils dans l’espace de travail moderne. Cela peut inclure des autorisations pour installer ou désinstaller des applications nécessaires dans les performances de leurs tâches ou pour désactiver temporairement les fonctionnalités de sécurité des appareils. Que cette activité soit involontaire, accidentelle ou malveillante, elle peut présenter un risque pour votre organisation et est importante pour identifier et agir pour minimiser les risques. Pour vous aider à identifier ces activités à risque, les modèles de violation de la stratégie de sécurité de gestion des risques Insider suivants dénotent les indicateurs de risque de sécurité et utilisent les alertes ATP (protection avancée contre les menaces) de Microsoft pour fournir des informations sur les activités liées à la sécurité :

- [Violations de stratégie de sécurité générale (préversion)](insider-risk-management-policies.md#general-security-policy-violations-preview)
- [Violations de stratégie de sécurité en faisant ressorter les utilisateurs (aperçu)](insider-risk-management-policies.md#security-policy-violations-by-departing-users-preview)
- [Violations de stratégie de sécurité par utilisateurs prioritaires (aperçu)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Violations de stratégie de sécurité par des utilisateurs mécontents (aperçu)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

## <a name="policies-for-users-based-on-position-access-level-or-risk-history-preview"></a>Stratégies pour les utilisateurs en fonction de leur position, de leur niveau d’accès ou de leur historique des risques (aperçu)

Les utilisateurs de votre organisation peuvent avoir différents niveaux de risque en fonction de leur position, de leur niveau d’accès aux informations sensibles ou de l’historique des risques. Cela peut inclure les membres de l’équipe responsable de la direction de votre organisation, les administrateurs informatiques disposant de nombreux privilèges de données et d’accès réseau, ou les utilisateurs ayant un historique des activités à risque. Dans ces circonstances, un examen plus approfondi et une évaluation plus agressive des risques sont importants pour aider les alertes de surface pour l’enquête et l’action rapide. Pour identifier les activités à risque pour ces types d’utilisateurs, vous pouvez créer des groupes d’utilisateurs prioritaires et créer des stratégies à partir des modèles de stratégie suivants :

- [Violations de stratégie de sécurité par utilisateurs prioritaires (aperçu)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Fuites de données par les utilisateurs prioritaires (aperçu)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)

## <a name="actions-and-behaviors-by-disgruntled-users-preview"></a>Actions et comportements par les utilisateurs mécontents (aperçu)

Les événements de contraintes d’emploi peuvent avoir un impact sur le comportement de l’utilisateur de plusieurs façons liées aux risques d’Insider. Il peut s’agir d’un examen des performances médiocres, d’une rétrogradation de position ou de l’utilisateur en place sur un plan d’analyse des performances. Bien que la plupart des utilisateurs ne répondent pas à ces événements à des fins malveillantes, la contrainte de ces actions peut empêcher certains utilisateurs de prendre des mesures qu’ils ne peuvent normalement prendre en compte pendant les circonstances normales. Pour vous aider à identifier ces types d’activités à risque, les modèles de stratégie de gestion des risques Insider suivants utilisent le connecteur RH de Microsoft 365 et commencent à dénoter les indicateurs de risques liés aux comportements susceptibles de se produire à proximité de l’emploi événements stressor :

- [Fuites de données par les utilisateurs mécontents (aperçu)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)
- [Violations de stratégie de sécurité par des utilisateurs mécontents (aperçu)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

- Pour plus d’informations sur les stratégies de gestion des risques Insider dans votre organisation, reportez-vous à la rubrique [plan for Insider Management Management](insider-risk-management-plan.md) .
- Voir [Get Started with insidest Management Settings](insider-risk-management-settings.md) to configure Global Settings for Insider Risk Policies.
- Consultez la rubrique [prise en main de la gestion des risques initiés](insider-risk-management-configure.md) pour configurer les conditions préalables, créer des stratégies et commencer à recevoir des alertes.
