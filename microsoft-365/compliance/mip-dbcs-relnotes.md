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
ms.openlocfilehash: 2de0e67c78ac558f4bdc2648790e49fad86e3178
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595051"
---
# <a name="support-for-double-byte-character-set-release-notes"></a>Prise en charge des notes de publication des jeux de caractères à double octets

 Microsoft 365 Information Protection prend désormais en charge les langues de jeu de caractères à double octets pour:

- Chinois (simplifié)
- Chinois (traditionnel)
- Korean
- Japanese

Cette prise en charge est disponible pour les types d’informations sensibles et les dictionnaires de mots-clés et sera reflétée dans la protection contre la perte de données (Exchange Online, Share Point Online, OneDrive Entreprise et Teams), la conformité des communications, l’étiquetage automatique dans les applications Office et Microsoft Defender for Cloud Apps.

## <a name="known-issues"></a>Problèmes détectés

- Lorsqu’un fichier texte joint à un e-mail est au format UTF-8 sans indicateur d’ordre des octets (BOM), l’e-mail n’est pas détecté par la stratégie de Conformité des communications.

- Les stratégies de Conformité des communications ne peuvent pas détecter de valeurs si une phrase est saisie pour la condition de stratégie : « Le message contient l’un de ces mots ». Si le texte spécifié dans la stratégie est écrit sous forme de mot, il peut être détecté. Cependant, s’il est écrit au milieu d’une phrase, il ne sera pas détecté.

- Les stratégies de Conformité des communications qui spécifient des dictionnaires comme informations de type ne détectent pas les discussions privées et les discussions de canal Teams.

- Les conditions suivantes ne sont pas prises en charge pour la Conformité des communications à ce stade (nous prévoyons de résoudre ces problèmes à l’avenir) : 
  - « Le message contient l’un de ces mots »
  - « Le message ne contient aucun de ces mots »
  - « La pièce jointe contient l’un de ces mots »
  - « La pièce jointe contient l’un de ces mots »

- Les stratégies de protection contre la perte de données sont appliquées sur les appareils macOS (préversion) exécutant la version Catalina 10.15 ou ultérieure, à l’exception des conditions mentionnées ci-dessous pour les langues d’Asie orientale, y compris le japonais.
  - Les numéros à pleine chasse ne sont pas détectés, par exemple à l’aide d’un modèle intégré tel qu’un numéro de compte bancaire japonais
  - Les nombres sans séparateur ne sont pas détectés
  - Les mots clés séparés par un espace demi-chasse ne sont pas détectés pour un type d’informations sensibles. Par exemple : le mot japonais est défini sur le type d’informations sensibles et le dictionnaire n’est pas détecté s’il se trouve dans une phrase
  - Les mots contenant à la fois l’anglais et le japonais (東京2020) ne sont pas détectés

Nous vous recommandons plutôt de créer un type d’informations sensibles personnalisé, avec un dictionnaire de mots-clés, qui détectera les modèles dans les messages et les pièces jointes, et d’utiliser ce type d’informations sensibles personnalisé comme condition de stratégie de conformité des communications.
