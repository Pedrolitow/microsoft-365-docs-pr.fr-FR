---
title: Ordre et priorité de la protection de la messagerie
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
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur l’ordre des applications des protections dans Exchange Online Protection (EOP) et la façon dont la valeur de priorité dans les stratégies de protection détermine quelle stratégie est appliquée.
ms.openlocfilehash: 7775f0a37751289e7f0116575e2f6b2733683b6b
ms.sourcegitcommit: 6a1a8aa024fd685d04da97bfcbc8eadacc488534
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46653676"
---
# <a name="order-and-precedence-of-email-protection"></a>Ordre et priorité de la protection de la messagerie

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online, le courrier électronique entrant peut être marqué par plusieurs formes de protection. Par exemple, les stratégies de protection contre le hameçonnage intégrées, disponibles pour tous les clients Microsoft 365, et les stratégies anti-hameçonnage plus robustes disponibles pour les clients Office 365 Advanced Threat Protection (Office 365 ATP). Les messages passent également par des analyses de détection multiples pour les programmes malveillants, le courrier indésirable, le hameçonnage, etc. Une fois cette activité terminée, il peut y avoir une certaine confusion quant à l’application de la stratégie.

En règle générale, une stratégie appliquée à un message est identifiée dans l’en-tête **X-Forefront-antispam-Report** de la propriété **Cat (Category)** . Pour plus d’informations, consultez la rubrique [en-têtes de message anti-courrier indésirable](anti-spam-message-headers.md).

Il existe deux facteurs principaux qui déterminent la stratégie appliquée à un message :

- **Priorité du type de protection de messagerie**: cette commande n’est pas configurable et est décrite dans le tableau suivant :

  ****

  |Priorité|Protection de la messagerie|Catégorie|Où gérer|
  |---|---|---|---|
  |0,1|Programme malveillant|CAT : MALW|[Configurer des stratégies anti-programmes malveillants dans EOP](configure-anti-malware-policies.md)|
  |n°2|Hameçonnage|CAT : PHSH|[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
  |3|Courrier fortement suspecté d’être indésirable|CAT : HSPM|[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
  |4 |Usurpation|CAT : USURPATION|[Configurer l’intelligence des usurpations d’identité dans EOP](learn-about-spoof-intelligence.md)|
  |5 |Courrier indésirable|CAT : SPM|[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
  |6 |Courrier en nombre|CAT : BULK|[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
  |7j/7<sup>\*</sup>|Emprunt d’identité de domaine (utilisateurs protégés)|DIMP|[Configurer des stratégies anti-hameçonnage ATP](configure-atp-anti-phishing-policies.md)|
  |8bits<sup>\*</sup>|Emprunt d’identité d’utilisateur (domaines protégés)|UIMP|[Configurer des stratégies anti-hameçonnage ATP](configure-atp-anti-phishing-policies.md)|
  |

  <sup>\*</sup>Ces fonctionnalités sont disponibles uniquement dans les stratégies anti-hameçonnage ATP.

- **Priorité de la stratégie**: pour chaque type de protection (blocage du courrier indésirable, anti-programme malveillant, anti-hameçonnage, etc.), il existe une stratégie par défaut qui s’applique à tous les utilisateurs, mais vous pouvez créer des stratégies personnalisées qui s’appliquent à des utilisateurs spécifiques. Chaque stratégie personnalisée a une valeur de priorité qui détermine l’ordre dans lequel les stratégies sont appliquées. La stratégie par défaut est toujours appliquée en dernier.

  Si un utilisateur est défini dans plusieurs stratégies du même type, seule la stratégie avec la priorité la plus élevée est appliquée. Les stratégies restantes de ce type ne sont pas évaluées pour l’utilisateur (y compris la stratégie par défaut).

Par exemple, considérez les stratégies anti-hameçonnage ATP suivantes **qui s’appliquent aux mêmes utilisateurs**, et un message qui est identifié à la fois comme emprunt d’identité d’utilisateur et usurpation d’identité :

  ****

  |Stratégie anti-hameçonnage ATP|Priorité|Emprunt d’identité de l’utilisateur|Détection d’usurpation d’identité|
  |---|---|---|---|
  |Stratégie A|0,1|Activé|Désactivé|
  |Stratégie B|n°2|Désactivé|Activé|
  |

1. Le message est marqué et traité comme falsifié, car l’usurpation a une priorité plus élevée (4) que l’emprunt d’identité d’utilisateur (8).
2. La stratégie A est appliquée aux utilisateurs car elle a une priorité plus élevée que la stratégie B.
3. En fonction des paramètres de la stratégie A, aucune action n’est effectuée sur le message, car l’anti-usurpation d’identité est désactivée dans la stratégie.
4. Le traitement de la stratégie s’arrête, de sorte que la stratégie B n’est jamais appliquée aux utilisateurs.

Étant donné que les mêmes utilisateurs peuvent être inclus intentionnellement ou involontairement dans plusieurs stratégies personnalisées du même type, utilisez les instructions de conception suivantes pour les stratégies personnalisées :

- Attribuez une priorité plus élevée aux stratégies qui s’appliquent à un petit nombre d’utilisateurs, et une priorité moindre aux stratégies qui s’appliquent à un grand nombre d’utilisateurs. N’oubliez pas que la stratégie par défaut est toujours appliquée en dernier.
- Configurez vos stratégies de priorité supérieure pour qu’elles aient des paramètres plus ou moins spécialisés que les stratégies de faible priorité.
- Envisagez d’utiliser moins de stratégies personnalisées (utilisez uniquement des stratégies personnalisées pour les utilisateurs qui requièrent des paramètres plus ou plus spécialisés).
