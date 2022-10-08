---
title: Ordre et priorité de la protection par e-mail
keywords: sécurité, programmes malveillants, Microsoft 365, M365, security center, portail Microsoft 365 Defender, Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender pour Identity
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.collection:
- m365-security
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur l’ordre des applications des protections dans Exchange Online Protection (EOP) et comment la valeur de priorité dans les stratégies de protection détermine quelle stratégie est appliquée.
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: 5bb3f1a8b15c2d6407ba09ffd2fafaa1987c010f
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68082590"
---
# <a name="order-and-precedence-of-email-protection"></a>Ordre et priorité de la protection par e-mail

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, les e-mails entrants peuvent être marqués par plusieurs formes de protection. Par exemple, les stratégies anti-hameçonnage intégrées dans EOP qui sont disponibles pour tous les clients Microsoft 365 et les stratégies anti-hameçonnage plus robustes qui sont disponibles pour Microsoft Defender pour Office 365 clients. Les messages passent également par plusieurs analyses de détection pour détecter les programmes malveillants, le courrier indésirable, le hameçonnage, etc. Compte tenu de toute cette activité, il peut y avoir une certaine confusion quant à la stratégie appliquée.

En général, une stratégie appliquée à un message est identifiée dans **l’en-tête X-Forefront-Antispam-Report** dans la propriété **CAT (Category).** Pour plus d’informations, consultez [En-têtes de message anti-courrier indésirable dans Microsoft 365](anti-spam-message-headers.md).

Il existe deux facteurs majeurs qui déterminent quelle stratégie est appliquée à un message :

- **Ordre de traitement pour le type de protection par e-mail** : cette commande n’est pas configurable et est décrite dans le tableau suivant :

  |Commande|protection Email|Catégorie|Où gérer|
  |:---:|---|---|---|
  |1|Programme malveillant|CAT:MALW|[Configurer des stratégies anti-programme malveillant dans EOP](configure-anti-malware-policies.md)|
  |2|Hameçonnage|CAT:PHSH|[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
  |3|Courrier fortement suspecté d’être indésirable|CAT:HSPM|[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
  |4|Usurpation|CAT:SPOOF|[Informations sur l’intelligence d’usurpation d’identité dans EOP](learn-about-spoof-intelligence.md)|
  |5<sup>\*</sup>|Emprunt d’identité d’utilisateur (utilisateurs protégés)|UIMP|[Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md)|
  |6<sup>\*</sup>|Emprunt d’identité de domaine (domaines protégés)|DIMP|[Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md)|
  |7 |Courrier indésirable|CAT:SPM|[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
  |8 |Courrier en nombre|CAT:BULK|[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|

  <sup>\*</sup>Ces fonctionnalités sont disponibles uniquement dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.

- **Priorité de la stratégie** : pour chaque type de stratégie (anti-courrier indésirable, anti-programme malveillant, anti-hameçonnage, etc.), il existe une stratégie par défaut qui s’applique à tout le monde, mais vous pouvez créer des stratégies personnalisées qui s’appliquent à des utilisateurs spécifiques (destinataires). Chaque stratégie personnalisée a une valeur de priorité qui détermine l’ordre dans lequel les stratégies sont appliquées. La stratégie par défaut est toujours appliquée en dernier.

  > [!IMPORTANT]
  > Si un destinataire est défini dans plusieurs stratégies du même type (anti-courrier indésirable, anti-hameçonnage, etc.), seule la stratégie ayant la priorité la plus élevée est appliquée au destinataire. Les stratégies restantes de ce type ne sont pas évaluées pour le destinataire (y compris la stratégie par défaut).

Par exemple, considérez les **stratégies anti-hameçonnage suivantes** dans Microsoft Defender pour Office 365 **qui s’appliquent aux mêmes utilisateurs**, et un message identifié comme étant à la **fois l’emprunt d’identité et l’usurpation d’identité** :

|Nom de la stratégie|Priorité|Emprunt d’identité de l’utilisateur|Anti-usurpation d’identité|
|---|:---:|:---:|:---:|
|Stratégie A|1|Activé|Désactivé|
|Stratégie B|2|Désactivé|Activé|

1. Le message est identifié comme usurpation d’identité, car l’usurpation d’identité (4) est évaluée avant l’emprunt d’identité de l’utilisateur (5).
2. La stratégie A est appliquée en premier, car elle a une priorité plus élevée que la stratégie B.
3. En fonction des paramètres de la stratégie A, aucune action n’est effectuée sur le message, car l’usurpation d’identité est désactivée.
4. Le traitement des stratégies anti-hameçonnage s’arrête pour tous les destinataires inclus, de sorte que la stratégie B n’est jamais appliquée aux destinataires qui se trouvent également dans la stratégie A.

Étant donné que les mêmes utilisateurs peuvent être inclus intentionnellement ou involontairement dans plusieurs stratégies du même type, utilisez les instructions de conception suivantes pour les stratégies personnalisées :

- Attribuez une priorité plus élevée aux stratégies qui s’appliquent à un petit nombre d’utilisateurs et une priorité inférieure aux stratégies qui s’appliquent à un grand nombre d’utilisateurs. N’oubliez pas que la stratégie par défaut est toujours appliquée en dernier.
- Configurez vos stratégies de priorité supérieure pour avoir des paramètres plus stricts ou plus spécialisés que des stratégies de priorité inférieure.
- Envisagez d’utiliser moins de stratégies personnalisées (utilisez uniquement des stratégies personnalisées pour les utilisateurs qui nécessitent des paramètres plus stricts ou plus spécialisés).
