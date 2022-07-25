---
title: Définition de toutes les entités de noms complets
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’informations sensibles de tous les noms complets.
ms.openlocfilehash: 727448848dbc3a4ea46b83ec404b4c9151ea192e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997210"
---
# <a name="all-full-names"></a>Tous les noms complets

Tous les noms complets sont une entité nommée groupée. Il détecte les noms complets des personnes de tous les pays/régions pris en charge, notamment l’Australie, la Chine, le Japon, les États-Unis et les pays de l’UE. Utilisez ce SIT pour détecter toutes les correspondances possibles de noms complets.

## <a name="format"></a>Format

Divers.

## <a name="pattern"></a>Modèle

Divers.

## <a name="checksum"></a>Somme de contrôle

Non.

## <a name="description"></a>Description

Cette entité nommée SIT correspond à des noms personnels qu’un humain identifierait en tant que nom avec une confiance élevée. Par exemple, si une chaîne est trouvée composée d’un nom donné et est suivie d’un nom de famille, une correspondance est effectuée avec une confiance élevée. Il utilise trois ressources principales :

- Dictionnaire de noms donnés.
- Dictionnaire de noms de famille.
- Modèles de la façon dont les noms sont formés.

Les trois ressources sont différentes pour chaque pays.  Les chaînes *Olivia Wilson* déclencherait une correspondance. Les noms donnés/de famille courants bénéficient d’une plus grande confiance que les noms plus rares. Toutefois, le modèle autorise également les correspondances partielles. Si un nom donné du dictionnaire est trouvé et qu’il est suivi d’un nom de famille qui n’est pas dans le dictionnaire, une correspondance partielle est déclenchée. Par exemple, *Tomas Richard* déclencherait un match partiel. La confiance des correspondances partielles est moindre.

En outre, les modèles qu’un humain considérerait comme indicatifs de noms sont également mis en correspondance avec la confiance appropriée. Comme *O. Wilson*, *O.P. Wilson*, *Dr. O. P. Wilson*, *Wilson, O.P.* ou *T. Richard, Jr.* serait des correspondances.

## <a name="supported-languages"></a>Langues prises en charge

- Français
- Bulgare
- Croate
- Tchèque
- Danois
- Estonien
- Finnois
- Français
- Allemand
- Hongrois
- Islandais
- Irlandais
- Italien
- Japonais
- Letton
- Lituanien
- Maltais
- Néerlandais
- Norvégien
- Polonais
- Portugais
- Roumain
- Slovaque
- Slovène
- Espagnol
- Suédois
- Turc