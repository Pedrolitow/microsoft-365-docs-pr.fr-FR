---
title: Prise en charge de la conformité Microsoft 365 pour les notes de publication de caractères à double octets (préversion)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Notes de publication pour la prise en charge des jeux de caractères à double octets.
ms.openlocfilehash: 3731e32594461df29a9cc5ec3f21bf3eb17ee79c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60190676"
---
# <a name="support-for-double-byte-character-set-release-notes"></a>Prise en charge des notes de publication des jeux de caractères à double octets

 Microsoft 365 Information Protection prend désormais en charge les langues de jeu de caractères à double octets pour:

- Chinois (simplifié)
- Chinois (traditionnel)
- Korean
- Japanese

Cette prise en charge est disponible pour les types d’informations sensibles et les dictionnaires de mots-clés et sera reflétée dans la protection contre la perte de données (Exchange Online, Share Point Online, OneDrive Entreprise, et Teams), la conformité des communications, la détection automatique dans les applications Office et Microsoft Cloud App Security.

## <a name="known-issues"></a>Problèmes connus

- Lorsqu’un fichier texte joint à un e-mail est au format UTF-8 sans indicateur d’ordre des octets (BOM), l’e-mail n’est pas détecté par la stratégie de conformité des communications.

- Les stratégies de conformité des communications ne peuvent pas détecter de valeurs si une phrase est saisie pour la condition de stratégie : « Le message contient l’un de ces mots ». Si le texte spécifié dans la stratégie est écrit sous forme de mot, il peut être détecté. Cependant, s’il est écrit au milieu d’une phrase, il ne sera pas détecté.

- Les stratégies de conformité des communications qui spécifient des dictionnaires comme informations de type ne détectent pas les discussions privées et les discussions de canal Teams.

- Les conditions suivantes ne sont pas prises en charge pour la conformité des communications à ce stade (nous prévoyons de résoudre ces problèmes à l’avenir) : 
  - « Le message contient l’un de ces mots »
  - « Le message ne contient aucun de ces mots »
  - « La pièce jointe contient l’un de ces mots »
  - « La pièce jointe contient l’un de ces mots »

Nous vous recommandons plutôt de créer un type d’informations sensibles personnalisé, avec un dictionnaire de mots-clés, qui détectera les modèles dans les messages et les pièces jointes, et d’utiliser ce type d’informations sensibles personnalisé comme condition de stratégie de conformité des communications.


