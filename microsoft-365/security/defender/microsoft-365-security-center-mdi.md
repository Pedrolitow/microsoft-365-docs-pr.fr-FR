---
title: Microsoft Defender pour Identity dans Microsoft 365 Defender
description: En savoir plus sur les modifications apportées à la Microsoft Defender pour Identity à Microsoft 365 Defender
keywords: Bien démarrer avec Microsoft 365 Defender, Microsoft Defender pour Identity, NDI
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dacurwin
author: dcurwin
manager: dansimp
ms.date: 07/06/2022
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- m365-security
- tier2
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: dff0aca75740441d60f148d35eb27873e5ccaea0
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68075467"
---
# <a name="microsoft-defender-for-identity-in-microsoft-365-defender"></a>Microsoft Defender pour Identity dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender pour l’identité](/defender-for-identity/)

Microsoft Defender pour Identity fait désormais partie de Microsoft 365 Defender. Le portail Microsoft 365 Defender permet aux administrateurs de sécurité d’effectuer leurs tâches de sécurité à un emplacement unique. Cela simplifie les flux de travail et ajoute les fonctionnalités des autres services Microsoft 365 Defender. Microsoft 365 Defender sera le point d’accueil de la surveillance et de la gestion de la sécurité sur vos identités, données, appareils, applications et infrastructure Microsoft.

Microsoft Defender pour Identity apporte des informations axées sur l’identité dans les incidents et les alertes présentés par Microsoft 365 Defender. Ces informations sont essentielles pour fournir un contexte et mettre en corrélation des alertes à partir des autres produits dans Microsoft 365 Defender.

## <a name="quick-reference"></a>Référence rapide

Le tableau ci-dessous répertorie les modifications apportées à la navigation entre Microsoft Defender pour Identity et Microsoft 365 Defender.

| **Defender pour** Identité  | **Microsoft 365 Defender**                                   |
| -------------------------- | ------------------------------------------------------------ |
| Chronologie                   | file d’attente alertes/incidents Microsoft 365 Defender                |
| Rapports                    | Reste dans le [portail Defender pour Identity classique](/defender-for-identity/classic-workspace-portal). <br> Les rapports personnalisés peuvent être créés dans le portail Microsoft 365 Defender à l’aide de [la chasse avancée](#advanced-hunting-new).               |
| Page utilisateur                  | page utilisateur Microsoft 365 Defender                             |
| Page Appareil                | Microsoft 365 Defender page Appareil                           |
| Page De groupe                 | volet latéral des groupes Microsoft 365 Defender                      |
| Page d’alerte                 | page d’alerte Microsoft 365 Defender                            |
| Rechercher                     | recherche Microsoft 365 Defender                                |
| Centre d’intégrité              | Paramètres -> Identités -> Capteurs                            |
| Activités d’entité          | Recherche avancée de menaces                                             |
| Paramètres                   | Paramètres - identités >                                       |
| Utilisateurs et comptes         | Ressources -> identités                                         |
| Posture de sécurité des identités  | [Évaluations de la posture de sécurité de Microsoft Defender pour Identity](/defender-for-identity/security-assessment) |
| Intégration d’un nouvel espace de travail | Paramètres -> identités (automatiquement)                       |

## <a name="whats-changed"></a>Fonctionnalités modifiées

### <a name="defender-for-identity-settings"></a>Paramètres Defender pour Identity

Pour accéder aux paramètres de configuration Microsoft Defender pour Identity, dans [Microsoft 365 Defender](https://security.microsoft.com), accédez aux **paramètres**, puis aux **identités**.

### <a name="defender-for-identity-security-posture"></a>Posture de sécurité de Defender pour Identity

Toutes les évaluations de la gestion de la posture de sécurité des identités qui étaient auparavant accessibles dans Defender pour Cloud Apps sont désormais disponibles dans microsoft Secure Score, qui se trouve <https://security.microsoft.com/securescore> dans le [portail Microsoft 365 Defender](https://security.microsoft.com). Pour plus [d’informations, consultez les évaluations de la posture de sécurité de Microsoft Defender pour Identity](/defender-for-identity/security-assessment).

### <a name="global-search"></a>Recherche globale

La recherche globale dans Microsoft 365 Defender (à l’aide de la barre de recherche en haut de la page) permet aux équipes de sécurité de rechercher toute entité surveillée par Microsoft 365 Defender, qu’il s’agit de l’identité, du point de terminaison, des données Office 365, etc. Les résultats peuvent être interagis directement à partir de la liste déroulante de recherche, ou les équipes de sécurité peuvent choisir de sélectionner **Tous les utilisateurs** ou **tous les appareils**  pour voir toutes les entités associées à ce terme de recherche.

### <a name="onboarding-and-administration"></a>Intégration et administration

Le processus d’intégration est désormais automatique pour les nouveaux clients, sans avoir à configurer manuellement un espace de travail. En outre, toutes les fonctionnalités d’administration sont disponibles dans le menu **Identités** des paramètres de Microsoft 365 Defender.

### <a name="alerting-and-incident-correlation"></a>Corrélation des alertes et des incidents

Les alertes Defender pour Identity sont désormais incluses dans la file d’attente d’alertes de Microsoft 365 Defender, ce qui les rend disponibles pour la fonctionnalité de corrélation des incidents automatiques. Cela garantit que toutes les alertes sont disponibles au même endroit et que l’étendue d’une violation peut être déterminée plus rapidement qu’auparavant. Pour plus d’informations, consultez [les alertes de sécurité Defender pour Identity dans Microsoft 365 Defender](/defender-for-identity/manage-security-alerts).

### <a name="advanced-hunting-new"></a>Repérage avancé (nouveau)

Vous pouvez désormais rechercher de manière proactive les menaces et les activités malveillantes à l’aide de requêtes de chasse avancées. Ces requêtes puissantes peuvent être utilisées pour rechercher et examiner les indicateurs et entités de menaces pour les menaces connues et potentielles.

Des règles de détection personnalisées peuvent être créées à partir de requêtes de repérage avancées pour vous aider à surveiller de manière proactive les événements qui peuvent indiquer une activité de violation et des appareils mal configurés. Pour plus d’informations, consultez [La chasse proactive contre les menaces avec la chasse avancée dans Microsoft 365 Defender](advanced-hunting-overview.md).

### <a name="alert-exclusions-updated"></a>Exclusions d’alerte (mise à jour)

L’interface d’alerte est plus conviviale, y compris l’ajout d’une fonction de recherche utile. En outre, il inclut désormais des exclusions globales. Cela signifie que n’importe quelle entité peut être exclue de toutes les alertes générées par Defender pour Identity, ce qui aide à tous les scénarios de test que vous pouvez avoir. Pour plus d’informations, consultez [Configurer les exclusions de détection defender pour l’identité dans Microsoft 365 Defender](/defender-for-identity/exclusions).

### <a name="entity-profiles"></a>Profils d’entité

Les données Defender pour Identity sont désormais incluses dans les profils d’entité Utilisateur et Appareil Microsoft 365.

### <a name="remediation-actions-new"></a>Actions de correction (nouveau)

Les actions de correction defender pour l’identité, telles que la désactivation des comptes ou la nécessité de réinitialiser le mot de passe, peuvent désormais être effectuées à partir de la page utilisateur Microsoft 365 Defender. Pour plus d’informations, consultez [Actions de correction dans Microsoft Defender pour Identity](/defender-for-identity/remediation-actions).

### <a name="lateral-movement-paths"></a>Chemins de mouvement latéral

En plus de l’onglet **Chemins de mouvement latéral** de la page utilisateur, les chemins de mouvement latéral peuvent également être découverts via la fonctionnalité **de chasse avancée** et l’évaluation de la sécurité des chemins de mouvement latéral. Pour plus d’informations, consultez [Microsoft Defender pour Identity chemins de mouvement latéral (LPM).](/defender-for-identity/understand-lateral-movement-paths)

## <a name="related-videos"></a>Vidéos connexes

- [Nouveautés pour Microsoft Defender pour Identity](https://www.microsoft.com/videoplayer/embed/RE4HcEU)

## <a name="related-information"></a>Informations connexes

- [Microsoft 365 Defender](microsoft-365-defender.md)
