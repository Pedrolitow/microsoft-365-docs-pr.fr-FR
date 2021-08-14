---
title: Ordre et priorité de la protection de la messagerie
keywords: sécurité, programmes malveillants, Microsoft 365, M365, centre de sécurité, portail Microsoft 365 Defender, Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender pour l’identité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur l’ordre d’application des protections dans Exchange Online Protection (EOP) et comment la valeur de priorité dans les stratégies de protection détermine quelle stratégie est appliquée.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 522af9171b9188bd817708ce7de5eb90cd0df7c8412c60ab5d79a128b75d6ff4
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "56801501"
---
# <a name="order-and-precedence-of-email-protection"></a>Ordre et priorité de la protection de la messagerie

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres en Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, les messages entrants peuvent être signalés par plusieurs formes de protection. Par exemple, les stratégies anti-hameçonnage intégrées dans EOP qui sont disponibles pour tous les clients Microsoft 365 et les stratégies anti-hameçonnage les plus robustes disponibles pour Microsoft Defender pour Office 365 clients. Les messages passent également par plusieurs analyses de détection des programmes malveillants, du courrier indésirable, du hameçonnage, etc. Étant donné toute cette activité, il peut y avoir une certaine confusion quant à la stratégie appliquée.

En règle générale, une stratégie appliquée à un message est identifiée dans **l’en-tête X-Forefront-Antispam-Report** de la propriété **CAT (Category).** Pour plus d’informations, consultez [les en-têtes de message anti-courrier indésirable.](anti-spam-message-headers.md)

Deux facteurs majeurs déterminent la stratégie appliquée à un message :

- **La priorité du type de protection de** la messagerie électronique : cette commande n’est pas configurable et est décrite dans le tableau suivant :

  <br>

  ****

  |Priorité|Protection de la messagerie|Catégorie|Où gérer|
  |---|---|---|---|
  |1 |Programme malveillant|CAT:MALW|[Configurer des stratégies anti-programme malveillant dans EOP](configure-anti-malware-policies.md)|
  |2 |Hameçonnage|CAT:PHSH|[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
  |3 |Courrier fortement suspecté d’être indésirable|CAT:HSPM|[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
  |4 |Usurpation|CAT:SPOOF|[Informations sur l’usurpation d’intelligence dans EOP](learn-about-spoof-intelligence.md)|
  |5<sup>\*</sup>|Emprunt d’identité d’utilisateur (utilisateurs protégés)|UIMP|[Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md)|
  |6<sup>\*</sup>|Emprunt d’identité de domaine (domaines protégés)|DIMP|[Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md)|
  |7 |Courrier indésirable|CAT:SPM|[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
  |8 |En nombre|CAT:BULK|[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
  |

  <sup>\*</sup>Ces fonctionnalités sont disponibles uniquement dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.

- Priorité de la stratégie : pour chaque type de stratégie (anti-courrier indésirable, anti-programme malveillant, anti-hameçonnage, etc.), il existe une stratégie par défaut qui s’applique à tout le monde, mais vous pouvez créer des stratégies personnalisées qui s’appliquent à des utilisateurs spécifiques. Chaque stratégie personnalisée a une valeur de priorité qui détermine l’ordre d’application des stratégies. La stratégie par défaut est toujours appliquée en dernier.

  > [!IMPORTANT]
  > Si un utilisateur est défini dans plusieurs stratégies du même type, seule la stratégie ayant la priorité la plus élevée lui est appliquée. Les stratégies restantes de ce type ne sont pas évaluées pour l’utilisateur (y compris la stratégie par défaut).

Par exemple, prenons les stratégies anti-hameçonnage suivantes dans Microsoft Defender pour les Office 365 qui s’appliquent aux mêmes utilisateurs **et** un message identifié comme usurpant l’identité et l’usurpation d’identité d’utilisateur :

<br>

****

|Nom de la stratégie|Priorité|Emprunt d’identité de l’utilisateur|Détection d’usurpation d’identité|
|---|---|---|---|
|Stratégie A|1 |Activé|Désactivé|
|Stratégie B|2 |Désactivé|Activé|
|

1. Le message est marqué et traité comme une usurpation d’identité, car l’usurpation d’identité a une priorité plus élevée (4) que l’emprunt d’identité de l’utilisateur (5).
2. La stratégie A est appliquée aux utilisateurs, car elle a une priorité plus élevée que la stratégie B.
3. En fonction des paramètres de la stratégie A, aucune action n’est entreprise sur le message, car la stratégie de anti-usurpation est désactivée.
4. Le traitement des stratégies s’arrête, de sorte que la stratégie B n’est jamais appliquée aux utilisateurs.

Étant donné qu’il est possible que les mêmes utilisateurs soient inclus intentionnellement ou involontairement dans plusieurs stratégies personnalisées du même type, utilisez les instructions de conception suivantes pour les stratégies personnalisées :

- Attribuez une priorité plus élevée aux stratégies qui s’appliquent à un petit nombre d’utilisateurs et une priorité inférieure aux stratégies qui s’appliquent à un grand nombre d’utilisateurs. N’oubliez pas que la stratégie par défaut est toujours appliquée en dernier.
- Configurez vos stratégies de priorité supérieure pour avoir des paramètres plus stricts ou plus spécialisés que les stratégies de priorité inférieure.
- Envisagez d’utiliser moins de stratégies personnalisées (utilisez uniquement des stratégies personnalisées pour les utilisateurs qui nécessitent des paramètres plus stricts ou plus spécialisés).
