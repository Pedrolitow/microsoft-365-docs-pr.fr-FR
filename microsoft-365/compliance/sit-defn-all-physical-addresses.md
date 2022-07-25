---
title: Définition d’entité Toutes les adresses physiques
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
description: Définition d’entité de type d’informations sensibles Toutes les adresses physiques.
ms.openlocfilehash: 3d8b40d6362c2a39525959467f524bc83c7cc3c8
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997029"
---
# <a name="all-physical-addresses"></a>Toutes les adresses physiques aux États-Unis

Toutes les adresses physiques sont une entité groupée SIT, qui détecte les modèles liés aux adresses physiques de tous les pays/régions pris en charge.

## <a name="format"></a>Format

Divers

## <a name="pattern"></a>Modèle

Divers

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="description"></a>Description

La correspondance des adresses de rue est conçue pour correspondre à des chaînes qu’un humain identifierait comme adresse de rue. Pour ce faire, il utilise plusieurs ressources principales :

- Dictionnaire d’établissements, de comtés et de régions.
- Dictionnaire de suffixes de rue, comme Road, Street ou Avenue.
- Modèles de codes postaux.
- Modèles de formats d’adresse.

Les ressources sont différentes pour chaque pays. Les ressources principales sont les modèles de formats d’adresse utilisés dans un pays donné. Différents formats sont choisis pour s’assurer que autant d’adresses que possible sont mises en correspondance. Ces formats permettent la flexibilité, par exemple, une adresse peut omettre le code postal ou omettre un nom de ville ou avoir une rue sans suffixe de rue. Dans tous les cas, ces correspondances sont utilisées pour augmenter la confiance de la correspondance.

Les modèles sont conçus pour correspondre à des adresses uniques individuelles, et non à des emplacements génériques. Ainsi, les chaînes telles que *Redmond, WA 98052* ou *Main Street, Albuquerque* ne seront pas mises en correspondance.

## <a name="contains"></a>Contains

Cette entité nommée groupée SIT contient les SIT individuels suivants :

- Adresses physiques australiennes
- Adresses physiques en Autriche
- Adresses physiques en Belgique
- Adresses physiques du Brésil
- Adresses physiques roumaines
- Adresses physiques du Canada
- Adresses physiques croates
- Adresses physiques chypriotes
- Adresses physiques de la République tchèque
- Adresses physiques danoises
- Adresses physiques estoniennes
- Adresses physiques finlandaises
- Adresses physiques françaises
- Adresses physiques allemandes
- Adresses physiques grecques
- Adresses physiques hongroises
- Adresses physiques islandaises
- Adresses physiques irlandaises
- Adresses physiques italiennes
- Adresses physiques lettones
- Adresses physiques du Liechtenstein
- Adresses physiques lituaniennes
- Adresses physiques luxembourgeoises
- Adresses physiques maltaises
- Adresses physiques néerlandaises
- Adresses physiques en Nouvelle-Zélande
- Adresses physiques norvégiennes
- Adresses physiques polonaises
- Adresses physiques portugaises
- Adresses physiques roumaines
- Adresses physiques slovaques
- Adresses physiques slovènes
- Adresses physiques espagnoles
- Adresses physiques suédoises
- Adresses physiques suisse
- Adresses physiques en Turquie
- Adresses physiques du Royaume-Uni
- États-Unis adresses physiques

## <a name="supported-languages"></a>Langues prises en charge

- Français
- Bulgare
- Chinois
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