---
title: Gestion des risques initiés
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
ms.collection: m365-security-compliance
ms.openlocfilehash: cc0c698b5c27b41548b646d03d9f94a2f8671eea
ms.sourcegitcommit: 87cc278ea2ddcd536ecfaa3dfae9a5ddaa502cf9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "42179185"
---
# <a name="insider-risk-management-in-microsoft-365"></a>Gestion des risques internes dans Microsoft 365

La gestion des risques initiés est une solution dans Microsoft 365 qui permet de réduire les risques internes en vous permettant de détecter, d’examiner et de prendre des mesures pour les activités à risque au sein de votre organisation. Les stratégies personnalisées vous permettent de détecter et de prendre des mesures concernant les activités malveillantes et les risques involontaires dans votre organisation, y compris la signalisation progressive de Microsoft Advanced eDiscovery, le cas échéant. Les analystes de risques de votre organisation peuvent rapidement prendre les mesures appropriées pour s’assurer que les utilisateurs sont conformes aux normes de conformité de votre organisation.

Regardez la vidéo ci-dessous pour découvrir comment la gestion des risques des Insiders peut aider votre organisation à prévenir, détecter et concourir des risques tout en hiérarchisant les valeurs de votre organisation, la culture et l’expérience de l’employé :
<br>
<br>
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4j9CN]

## <a name="modern-risk-pain-points"></a>Points névralgiques des risques modernes

La gestion et la minimisation des risques au sein de votre organisation commencent par la compréhension des types de risques détectés dans l’espace de travail moderne. Certains risques sont pilotés par des événements et des facteurs externes et sont en dehors du contrôle direct. Les autres risques sont dictés par des événements internes et des activités de l’employé qui peuvent être éliminés et évités. Certains exemples sont des risques de comportements et d’actions illicites, inappropriés, non autorisés ou inéthiques par les employés et les responsables. Ces comportements incluent une large gamme de risques internes pour les employés :

- Fuites de données sensibles et de dépassements de données
- Violations de confidentialité
- Vol de propriété intellectuelle (IP)
- Lutte
- Commerce d’initié
- Violations de conformité réglementaire

Les employés du lieu de travail moderne ont accès à la création, la gestion et le partage de données sur un large éventail de plateformes et de services. Dans la plupart des cas, les organisations disposent de ressources et d’outils limités pour identifier et atténuer les risques à l’échelle de l’organisation, tout en respectant les normes de confidentialité des employés.

La gestion des risques initiés dans Microsoft 365 utilise l’ensemble complet des indicateurs de service et tiers pour vous aider à identifier rapidement, à trier et à agir sur l’activité des risques. À l’aide des journaux d’Office 365 et Microsoft Graph, la gestion des risques internes vous permet de définir des stratégies spécifiques pour identifier les indicateurs de risques. Ces stratégies vous permettent d’identifier les activités à risque et de prendre des mesures pour atténuer ces risques.

La gestion des risques initiés est axée sur les principes suivants :

- **Transparence**: équilibrer la confidentialité des employés et les risques de l’organisation avec l’architecture de confidentialité.
- **Configurable**: stratégies configurables basées sur les groupes de secteur industriel, géographique et d’entreprise.
- **Intégré**: flux de travail intégré dans les solutions de conformité Microsoft 365.
- **Exploitable**: fournit des informations sur la façon d’activer les notifications de l’employé, les enquêtes sur les données et les enquêtes des employés.

## <a name="workflow"></a>Flux de travail

La gestion des risques initiés vous permet d’identifier, d’analyser et de prendre des mesures pour résoudre les risques internes au sein de votre organisation. Avec des modèles de stratégie ciblés, une activité complète signalant le service Microsoft 365 et un flux de travail flexible, vous pouvez utiliser des informations exploitables pour identifier et résoudre rapidement le comportement risqué.

L’identification et la résolution des problèmes liés aux activités de gestion des risques internes et à la conformité avec la gestion des risques initiés dans Microsoft 365 utilisent le flux de travail suivant :

![Flux de travail de gestion des risques Insiders](../media/insider-risk-workflow.png)

### <a name="policies"></a>Stratégies

Les stratégies de gestion des risques initiés sont créées à l’aide de modèles prédéfinis et de conditions de stratégie qui définissent quels indicateurs de risques sont examinés dans les fonctionnalités de Microsoft 365. Ces conditions incluent le mode d’utilisation des indicateurs pour les alertes, les utilisateurs inclus dans la stratégie, les services classés par ordre de priorité et la période de surveillance.

Vous pouvez sélectionner l’un des [modèles de stratégie](insider-risk-management-policies.md#policy-templates) suivants pour commencer rapidement à utiliser la gestion des risques initiés :

- Défaition des vols de données des employés
- Fuites de données
- Langage choquant dans le courrier électronique

Pour plus d’informations, consultez la rubrique [stratégies de gestion des risques internes](insider-risk-management-policies.md).

![Tableau de bord des stratégies de gestion des risques internes](../media/insider-risk-policy-dashboard.png)

### <a name="alerts"></a>Alertes

Les alertes sont automatiquement générées par des indicateurs de risque qui correspondent aux conditions de la stratégie et sont affichés dans le **tableau de bord des alertes**. Ce tableau de bord permet d’afficher un aperçu rapide de toutes les alertes nécessitant une révision, d’ouvrir des alertes dans le temps et de statistiques d’alerte pour votre organisation. Toutes les alertes de stratégie sont affichées avec des informations associées pour vous aider à identifier rapidement l’état actuel des alertes existantes et de nouvelles alertes qui nécessitent une action :

- Statut
- Severity
- Heure de détection
- Cas
- État de l’incident

Pour plus d’informations, consultez la rubrique [alertes de gestion des risques internes](insider-risk-management-alerts.md).

![Tableau de bord d’alerte de gestion des risques Insiders](../media/insider-risk-alerts-dashboard.png)

### <a name="triage"></a>Tri

Les nouvelles activités qui nécessitent une enquête génèrent automatiquement des alertes auxquelles l’état de *révision des besoins* est affecté. Les relecteurs peuvent rapidement identifier ces alertes et faire défiler chacune d’elles pour évaluer et trier. 

Les alertes sont résolues en ouvrant une nouvelle demande de devis, en affectant l’alerte à un incident existant ou en le rejetant. À l’aide de filtres d’alerte, il est facile d’identifier rapidement les alertes en fonction de l’État, de la gravité ou du temps détecté. Dans le cadre du processus de triage, les relecteurs peuvent afficher les détails de l’alerte pour la correspondance de stratégie, afficher l’activité utilisateur associée à la correspondance, voir la gravité de l’alerte et vérifier les informations de profil utilisateur.

![Triage de la gestion des risques initiés](../media/insider-risk-triage.png)

### <a name="investigate"></a>Pench

Les cas sont créés pour les alertes qui nécessitent une révision et une vérification approfondies des détails et des circonstances entourant la correspondance de stratégie. Le **tableau de bord de cas** fournit une vue d’ensemble de tous les incidents actifs, des incidents ouverts au fil du temps et des statistiques de cas pour votre organisation. Les relecteurs peuvent rapidement filtrer les incidents par État, date d’ouverture et date de la dernière mise à jour du cas.

La sélection d’un cas dans le tableau de bord de cas ouvre le cas à des fins d’examen et de révision. Cette étape est le cœur du flux de travail de gestion des risques Insiders. Cette zone est là où les indicateurs d’activité des risques, les conditions de stratégie, les détails des alertes et les détails des employés sont synthétisés en un mode intégré pour les relecteurs. Les principaux outils d’enquête de cette zone sont les suivants :

- **Activité**de l’utilisateur : l’activité de l’utilisateur est automatiquement affichée dans un graphique interactif qui trace les activités de risque au cours du temps et du niveau de risque pour les activités actuelles ou passées. Les relecteurs peuvent rapidement filtrer et afficher l’historique des risques de l’employé et explorer des activités spécifiques pour obtenir plus d’informations.
- **Explorateur de contenu**: tous les fichiers de données et les messages électroniques associés aux activités de risque d’alerte sont automatiquement capturés et affichés dans l’Explorateur de contenu. Les relecteurs peuvent filtrer et afficher les fichiers et les messages par source de données, type de fichier, balises, conversation et bien d’autres attributs.
- **Notes de cas**: les réviseurs fournissent des notes pour un cas dans la section Notes de cas. Cette liste consolide toutes les notes dans une vue centrale et inclut les informations de réviseur et de date d’envoi.

Pour plus d’informations, consultez la rubrique [cas de gestion des risques internes](insider-risk-management-cases.md).

![Enquête sur la gestion des risques des Insiders](../media/insider-risk-investigate.png)

### <a name="action"></a>Action

Après enquête, les réviseurs peuvent rapidement prendre des mesures pour résoudre le cas ou collaborer avec les autres parties prenantes du risque au sein de votre organisation. Lorsque les employés enfreignent accidentellement ou par inadvertance les conditions de la stratégie, un simple avis de rappel peut être envoyé à l’employé à partir des modèles de notification que vous pouvez configurer pour votre organisation. Ces notifications peuvent servir de rappels simples ou diriger l’employé vers une formation ou des conseils de réactualisation afin de prévenir un futur comportement risqué. Pour plus d’informations, reportez-vous à la rubrique [modèles d’avis de gestion des risques internes](insider-risk-management-notices.md).

Dans les situations les plus graves, il se peut que vous deviez partager les informations de cas de gestion des risques Insider avec d’autres réviseurs de votre organisation. La gestion des risques initiés est étroitement intégrée aux autres fonctionnalités de conformité de Microsoft 365 pour vous aider à résoudre les risques de bout en bout. La transmission d’un cas pour l’enquête vous permet de transférer des données et de gérer le cas vers Advanced eDiscovery dans Microsoft 365. Advanced eDiscovery fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter du contenu réactif aux investigations internes et externes de votre organisation. Elle permet aux équipes juridiques de gérer l’ensemble du flux de travail de notification de suspension légale. Pour en savoir plus sur les cas avancés de découverte électronique, consultez la rubrique [Overview of Advanced eDiscovery in Microsoft 365](overview-ediscovery-20.md).

## <a name="scenarios"></a>Scénarios

La gestion des risques initiés peut vous aider à détecter, examiner et prendre des mesures pour atténuer les risques internes dans votre organisation dans plusieurs scénarios courants :

### <a name="data-theft-by-departing-employee"></a>Vol de données en décomposant un employé

Lorsque les employés quittent une organisation, volontairement ou à la suite d’une résiliation, il existe souvent des problèmes légitimes que les données d’entreprise, de client et d’employé sont menacées. Les employés peuvent inoffensifment supposer que les données du projet ne sont pas propriétaires ou qu’ils peuvent être tentés de prendre des données d’entreprise à des fins de profit personnel et de violation de la politique de l’entreprise et des normes juridiques. Les stratégies de gestion des risques Insiders qui utilisent le modèle de stratégie de [vol de données employé en cours](insider-risk-management-policies.md#policy-templates) de détection détectent automatiquement les activités généralement associées à ce type de vol. Grâce à cette stratégie, vous recevrez automatiquement des alertes pour les activités suspectes associées au vol des employés, afin que vous puissiez prendre les mesures d’investigation appropriées. La configuration d’un [connecteur RH Microsoft 365](import-hr-data.md) pour votre organisation est requise pour ce modèle de stratégie.

### <a name="intentional-or-unintentional-leak-of-sensitive-or-confidential-information"></a>Fuite intentionnelle ou involontaire d’informations sensibles ou confidentielles

Dans la plupart des cas, les employés essaient de traiter correctement les informations sensibles ou confidentielles. Toutefois, les employés occasionnels composent des erreurs et les informations sont partagées par inadvertance en dehors de votre organisation ou en violation de vos stratégies de protection des informations. Parfois, les employés peuvent divulguer ou partager intentionnellement des informations sensibles et confidentielles à des fins malveillantes et potentielles. Les stratégies de gestion des risques internes créées à l’aide du modèle de stratégie [fuites de données](insider-risk-management-policies.md#policy-templates) détectent automatiquement les activités généralement associées au partage d’informations sensibles ou confidentielles. La configuration d’au moins une [stratégie de protection contre la perte de données (DLP)](create-test-tune-dlp-policy.md) Microsoft 365 pour votre organisation est requise pour ce modèle de stratégie.

### <a name="actions-and-behaviors-that-violate-corporate-policies"></a>Actions et comportements qui enfreignent les stratégies d’entreprise

Les communications entre les employés et les employés sont souvent une source de violations accidentelle ou malveillante des stratégies d’entreprise. Ces violations peuvent inclure un langage offensant, des menaces et la cyber-intimidation entre les employés. Ce type d’activité contribue à un environnement de travail hostile et peut entraîner des actions judiciaires contre les employés et l’organisation plus grande. La gestion des risques internes utilise de nouveaux classifieurs Microsoft 365 intégrés et le [langage offensant dans le modèle de stratégie de messagerie](insider-risk-management-policies.md#policy-templates) . Ces classifieurs et modèles permettent de configurer rapidement une stratégie pour détecter automatiquement et vous alerter de ce type de comportement.

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Vous êtes prêt à configurer la gestion des risques initiés pour votre organisation ? Consultez la rubrique [prise en main de la gestion des risques initiés](insider-risk-management-configure.md) pour configurer les conditions préalables, créer des stratégies et commencer à recevoir des alertes.
