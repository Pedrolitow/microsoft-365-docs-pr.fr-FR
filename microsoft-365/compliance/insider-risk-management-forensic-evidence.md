---
title: En savoir plus sur les preuves légales de gestion des risques internes (préversion)
description: Découvrez les preuves légales de gestion des risques internes dans Microsoft Purview. La preuve légale est un outil d’investigation permettant d’afficher l’activité de l’utilisateur capturé pour déterminer si les actions de l’utilisateur présentent un risque et peuvent entraîner un incident de sécurité.
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
ms.collection: m365-security-compliance
ms.openlocfilehash: 484da1e07de1a160149f2a1159b5610a3d22192f
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68638997"
---
# <a name="learn-about-insider-risk-management-forensic-evidence-preview"></a>En savoir plus sur les preuves légales de gestion des risques internes (préversion)

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou involontaires, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Créés avec la confidentialité par conception, les utilisateurs sont pseudonymes par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Le contexte visuel est essentiel pour les équipes de sécurité pendant les investigations judiciaires afin d’obtenir de meilleures informations sur les activités utilisateur potentiellement risquées liées à la sécurité. Avec des déclencheurs d’événements personnalisables et des contrôles intégrés de protection de la confidentialité des utilisateurs, les preuves légales permettent la capture d’activité visuelle personnalisable sur les appareils pour aider votre organisation à mieux atténuer, comprendre et répondre aux risques potentiels de données, tels que l’exfiltration de données non autorisées de données sensibles. Vous définissez les stratégies appropriées pour votre organisation, notamment les événements à risque qui sont la priorité la plus élevée pour la capture de preuves légales, les données les plus sensibles et si les utilisateurs sont avertis lorsque la capture légale est activée. La capture de preuves légales est désactivée par défaut et la création de stratégie nécessite une double autorisation.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="feature-capabilities"></a>Fonctionnalités

- **La capture visuelle** permet aux organisations de capturer des clips d’activités utilisateur liées à la sécurité clés, ce qui permet une visibilité plus sécurisée ou conforme et répond aux besoins de l’organisation.
- **Protection de la confidentialité des utilisateurs** par le biais de plusieurs niveaux d’approbation pour l’activation de la fonctionnalité de capture.
- Les **déclencheurs personnalisables et les options de capture** signifient que les équipes de sécurité peuvent configurer des preuves légales pour répondre à leurs besoins, qu’elles soient basées sur des incidents (par exemple, *capture 5 minutes avant et 10 minutes après qu’un utilisateur a téléchargé « SecretResearchPlans.docx* ») ou en fonction des besoins de capture continus.
- **Le ciblage de stratégie centré sur l’utilisateur** signifie que les équipes de sécurité et de conformité peuvent se concentrer sur l’activité par utilisateur, et non par appareil, pour obtenir de meilleurs insights contextuels.
- **Des contrôles d’accès en fonction du rôle (RBAC) forts** signifient que la possibilité de configurer et d’examiner des clips d’investigation est étroitement contrôlée et disponible uniquement pour les personnes de l’organisation disposant des autorisations appropriées.
- **Intégration approfondie avec les fonctionnalités actuelles de gestion des risques internes**, ce qui facilite l’intégration et des workflows plus familiers pour les administrateurs de gestion des risques internes et une approche à plateforme unique approuvée.

## <a name="capturing-options"></a>Options de capture

[Les événements déclencheurs, les indicateurs globaux et les indicateurs de stratégie](/microsoft-365/compliance/insider-risk-management-settings#indicators) jouent un rôle important dans toutes les stratégies de gestion des risques internes, y compris les stratégies de preuves légales. Les événements déclencheurs sont des actions utilisateur qui déterminent si les utilisateurs sont mis dans l’étendue pour évaluation dans les stratégies de gestion des risques internes. Les indicateurs de paramètres globaux sont utilisés pour déterminer les activités collectées par la gestion des risques internes. Les indicateurs de stratégie sont utilisés pour déterminer un score de risque pour un utilisateur dans l’étendue.

Selon la façon dont votre organisation décide de configurer la preuve légale, il existe deux options de capture :

- **Activités spécifiques** : cette option de stratégie capture l’activité uniquement lorsqu’un événement déclencheur a amené un utilisateur approuvé dans l’étendue de la stratégie de preuve légale et lorsque les conditions d’un indicateur de stratégie sont détectées pour l’utilisateur. Par exemple, un utilisateur approuvé pour la capture de preuves légales est inclus dans l’étendue de la stratégie de preuves légales et l’utilisateur copie les données vers des services de stockage cloud personnels ou des périphériques de stockage portables. La capture n’est limitée qu’à la période configurée lorsque l’utilisateur copie les données vers le service de stockage cloud personnel ou l’appareil de stockage portable. Les captures de cette option seront disponibles pour examen sous l’onglet **Preuves légales (préversion)** du tableau de bord **Alertes** .
- **Toutes les activités** : cette option de stratégie capture toutes les activités effectuées par les utilisateurs. Cela inclut le mouvement de la souris, les séquences de touches et toutes les activités définies par les indicateurs de risque interne. Par exemple, votre organisation a un besoin de capture d’activités pour un utilisateur approuvé qui est activement impliqué dans des activités potentiellement risquées qui peuvent entraîner un incident de sécurité. Il se peut que les indicateurs de stratégie n’aient pas atteint le seuil pour qu’une alerte soit générée par la stratégie et que l’activité potentiellement risquée ne soit pas documentée. L’aide de capture continue empêche l’activité potentiellement risquée d’être manquée ou de ne pas être détectée. Les captures de cette option seront disponibles pour examen sous l’onglet **Preuves légales (préversion)** du tableau de bord **Rapports d’activité utilisateur (préversion** ).

>[!IMPORTANT]
>Les clips de preuves légales sont supprimés 120 jours après leur capture ou à la fin de la période de préversion, la plus tôt possible. Vous pouvez télécharger ou transférer des clips de preuves légales avant qu’ils ne soient supprimés.

## <a name="workflow"></a>Flux de travail

Le flux de travail global pour la détection, l’examen et la correction des alertes qui contiennent la capture de clip suit les [mêmes étapes de base](/microsoft-365/compliance/insider-risk-management#workflow) que les autres stratégies de gestion des risques internes. Toutefois, il existe des différences notables pour les preuves légales lorsqu’elles sont configurées dans votre organisation :

- **Les utilisateurs soumis à la capture doivent disposer de demandes et d’approbations de capture explicites** : il s’agit d’un processus supplémentaire qui n’est pas inclus dans le cadre de la configuration d’autres stratégies de gestion des risques internes. Les utilisateurs affectés aux groupes de rôles Insider *Risk Management* ou *Insider Risk Management Admins* doivent envoyer une demande aux utilisateurs affectés au groupe de *rôles Approbateurs de gestion des risques internes* avant que n’importe quel utilisateur de votre organisation soit éligible aux options de capture clip. Par exemple, cette exigence permet de prendre en charge les scénarios organisationnels où vos administrateurs de gestion des risques internes doivent obtenir l’approbation explicite de votre personnel désigné des ressources juridiques ou humaines avant d’activer la capture pour n’importe quel utilisateur.
- **Les appareils doivent être intégrés et le client Microsoft Purview doit être installé** : avant que les preuves légales puissent collecter et stocker des clips capturés pour les utilisateurs éligibles, leurs appareils doivent être intégrés au portail de conformité Microsoft Purview. En outre, le client Microsoft Purview doit être installé sur chaque appareil. Ces prérequis permettent la prise en charge de la capture d’appareils en ligne et hors connexion.

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

- Consultez [Prise en main des preuves légales de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-forensic-evidence-configure) pour obtenir des instructions pas à pas pour configurer la capture de preuves légales dans votre organisation.
- Consultez [Prise en main de la gestion des risques internes](/microsoft-365/compliance/insider-risk-management-configure) pour configurer les prérequis, créer des stratégies et commencer à recevoir des alertes.
