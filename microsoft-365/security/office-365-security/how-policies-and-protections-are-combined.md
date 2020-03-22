---
title: Ordre et priorité de la protection de la messagerie dans Office 365
keywords: sécurité, programmes malveillants, Microsoft 365, M365, centre de sécurité, ATP, Microsoft Defender ATP, Office 365 ATP, Azure ATP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
description: Décrit l’ordre des applications des protections Office 365 et la façon dont la valeur de priorité dans les stratégies de protection détermine quelle stratégie est appliquée.
ms.openlocfilehash: 9f2033b1ec066c1f8501ce019b8f8c7f3748fd15
ms.sourcegitcommit: fce0d5cad32ea60a08ff001b228223284710e2ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42895334"
---
# <a name="order-and-precedence-of-email-protection-in-office-365"></a>Ordre et priorité de la protection de la messagerie dans Office 365

En tant qu’utilisateur d’Office 365, votre courrier électronique entrant peut être marqué par plusieurs formes de protection. Par exemple, les stratégies de protection contre le hameçonnage intégrées, disponibles pour tous les clients Office 365, et les stratégies anti-hameçonnage plus robustes disponibles pour les clients Office 365 Advanced Threat Protection. Les messages passent également par des analyses de détection multiples pour les programmes malveillants, le courrier indésirable, le hameçonnage, etc. Une fois cette activité terminée, il peut y avoir une certaine confusion quant à l’application de la stratégie.

En règle générale, une stratégie appliquée à un message est identifiée dans l’en-tête **X-Forefront-antispam-Report** de la propriété **Cat (Category)** . Pour plus d’informations, consultez la rubrique [en-têtes de message anti-courrier indésirable](anti-spam-message-headers.md).

Il existe deux facteurs principaux qui déterminent la stratégie appliquée à un message :

- **Priorité du type de protection de messagerie**: cette commande n’est pas configurable et est décrite dans le tableau suivant :

  |||||
  |---|---|---|---|
  |**Priorité**|**Protection de la messagerie**|**Catégorie**|**Où gérer**|
  |0,1|Programme malveillant|CAT : MALW|[Configurer des stratégies anti-programmes malveillants dans Office 365](configure-anti-malware-policies.md)|
  |n°2|Hameçonnage|CAT : PHSH|[Configurer des stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md)|
  |3|Courrier fortement suspecté d’être indésirable|CAT : HSPM|[Configurer des stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md)|
  |4 |Usurpation|CAT : USURPATION|[Configuration de l’anti-hameçonnage d’Office 365 – Protection avancée contre les menaces et des stratégies anti-hameçonnage](set-up-anti-phishing-policies.md) <Br/><br/> [En savoir plus sur l’usurpation d’identité](learn-about-spoof-intelligence.md)|
  |5 |Courrier indésirable|CAT : SPM|[Configurer des stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md)|
  |6 |Courrier en nombre|CAT : BULK|[Configurer des stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md)|
  |7j/7<sup>\*</sup>|Emprunt d’identité de domaine|DIMP|[Configuration de l’anti-hameçonnage d’Office 365 – Protection avancée contre les menaces et des stratégies anti-hameçonnage](set-up-anti-phishing-policies.md)|
  |8bits<sup>\*</sup>|Emprunt d’identité d’utilisateur|UIMP|[Configuration de l’anti-hameçonnage d’Office 365 – Protection avancée contre les menaces et des stratégies anti-hameçonnage](set-up-anti-phishing-policies.md)|
  |

  <sup>\*</sup>Ces fonctionnalités sont disponibles uniquement dans la protection avancée contre les menaces.

- **Priorité de la stratégie**: pour chaque type de protection (blocage du courrier indésirable, anti-programme malveillant, anti-hameçonnage, etc.), il existe une stratégie par défaut qui s’applique à tous les utilisateurs, mais vous pouvez créer des stratégies personnalisées qui s’appliquent à des utilisateurs spécifiques. Chaque stratégie personnalisée a une valeur de priorité qui détermine l’ordre dans lequel les stratégies sont appliquées. La stratégie par défaut est toujours appliquée en dernier.

  Si un utilisateur est défini dans plusieurs stratégies personnalisées, seule la stratégie avec la priorité la plus élevée est appliquée. Les stratégies restantes ne sont pas évaluées pour l’utilisateur (y compris la stratégie par défaut).

Par exemple, considérez les stratégies anti-hameçonnage suivantes **qui s’appliquent aux mêmes utilisateurs**, et un message qui est identifié à la fois comme emprunt d’identité d’utilisateur et usurpation d’identité :

  |||||
  |---|---|---|---|
  |**Stratégie anti-courrier indésirable**|**Priorité**|**Emprunt d’identité d’utilisateur (ATP)**|**Protection contre l’usurpation d’identité (EOP)**|
  |Stratégie A|0,1|Activé|Désactivé|
  |Stratégie B|n°2|Désactivé|Activé|
  |

1. Le message est marqué et traité comme falsifié, car l’usurpation a une priorité plus élevée (4) que l’emprunt d’identité d’utilisateur (8).
2. La stratégie A est appliquée aux utilisateurs car elle a une priorité plus élevée que la priorité B.
3. En fonction des paramètres de la stratégie A, aucune action n’est effectuée sur le message, car l’anti-usurpation d’identité est désactivée dans la stratégie.
4. Le traitement de la stratégie de blocage du courrier indésirable s’arrête, de sorte que la stratégie B n’est jamais appliquée aux utilisateurs.

Étant donné qu’il existe un grand nombre d’utilisateurs dans de nombreuses stratégies personnalisées du même type, prenez en compte les instructions de conception suivantes pour les stratégies personnalisées :

- Attribuez une priorité plus élevée aux stratégies qui s’appliquent à un petit nombre d’utilisateurs, et une priorité moindre aux stratégies qui s’appliquent à un grand nombre d’utilisateurs. N’oubliez pas que la stratégie par défaut est toujours appliquée en dernier.
- Configurez vos stratégies de priorité supérieure pour qu’elles aient des paramètres plus ou moins spécialisés que les stratégies de faible priorité.
- Envisagez d’utiliser moins de stratégies personnalisées (utilisez uniquement des stratégies personnalisées pour les utilisateurs qui nécessitent des paramètres plus stricts ou plus spécialisés).
