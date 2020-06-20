---
title: Éléments recherchés par les fonctions DLP
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/18/2016
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez les fonctions de protection contre la perte de données (DLP), pour vous aider à comprendre le fonctionnement des types d’informations sensibles prédéfinis.
ms.openlocfilehash: 838277b2e30696cd00cfc30df49c1d5a29149d92
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44819274"
---
# <a name="what-the-dlp-functions-look-for"></a>Éléments recherchés par les fonctions DLP

Data loss prevention (DLP) includes sensitive information types, such as Credit Card Number and EU Debit Card Number, which are ready for you to use in your DLP policies. These sensitive information types look for a specific pattern and corroborate it by ensuring proper formatting, enforcing checksums, and looking for relevant keywords or other information. Some of this functionality is performed by internal functions. For example, the Credit Card Number sensitive information type uses a function to look for dates formatted like an expiration date, to help corroborate that a number is a credit card number.
  
Cette rubrique explique ce que ces fonctions recherchent, pour vous aider à comprendre le fonctionnement des types d’informations sensibles prédéfinis. Pour plus d’informations, consultez la rubrique [informations sensibles type d’entité définitions](sensitive-information-type-entity-definitions.md)
  
## <a name="func_us_date"></a>Func_us_date

Cette fonction recherche une date au format couramment utilisé aux États-Unis. Cela inclut les formats « mois/jour/année », « mois-jour-année » et « mois de jour du mois ». Les noms ou les abréviations des mois ne respectent pas la casse. 
  
Exemples :
  
- 2 décembre 2016
    
- 2 décembre 2016
    
- DEC 02 2016
    
- 12/2/2016
    
- 12/02/16
    
- Déc-2-2016
    
- 12-2-16
    
Noms de mois acceptés :
  
- English
    
  - Janvier, février, mars, avril, mai, juin, juillet, août, septembre, octobre, novembre, décembre
    
  - Jan. fév. Mar. mai du 1er juillet aoû. septembre. Oct. nov. déc
    
## <a name="func_eu_date"></a>Func_eu_date

This function looks for a date in the format commonly used in the E.U. (and most places outside the U.S.). This includes the formats "day/month/year", "day-month-year", and "day month year". The names or abbreviations of months are not case sensitive.
  
Exemples :
  
- 2 déc 2016
    
- 02 déc 2016
    
- 2 déc 16
    
- 2/12/2016
    
- 02/12/16
    
- 2-déc-2016
    
- 2-12-16
    
Noms de mois acceptés :
  
- English
    
  - Janvier, février, mars, avril, mai, juin, juillet, août, septembre, octobre, novembre, décembre
    
  - Jan. fév. Mar. mai du 1er juillet aoû. septembre. Oct. nov. déc
    
- Dutch
    
  - januari, februari, maart, April, mei, juni, juli, augustus, September, ocktober, October, November, December
    
  - Jan fév maart avr Mei Jun Jul aoû Sep sept oct OKT nov déc
    
- French
    
  - janvier, février, mars, avril, mai, juin juillet, août, septembre, octobre, novembre, décembre
    
  - janv. févr. mars avril Maï juin juil. août sept. OPO. novembre. déc.
    
- German
    
  - jänuar, Februar, März, avril, mai, Juni Juli, août, septembre, oktober, novembre, Dezember
    
  - Jan./Jän. Fév. März avr. Maï Juni Juli aoû. sept. Okt. Nov. Dez.
    
- Italian
    
  - gennaio, febbraio, marzo, aprile, maggio, giugno, luglio, agosto, settembre, ottobre, novembre, dicembre
    
  - genn. febbr. détériore. avancé. magg. giugno luglio AG. sett. Verlag. novembre. DIC.
    
- Portugais
    
  - janeiro, fevereiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
    
  - Jan Fev Mar Abr mai Jun Jul a été défini sur le mois de novembre dez
    
- Spanish
    
  - enero, febrero, marzo, abril, mayo, junio, julio, agosto, septiembre, octubre, noviembre, diciembre
    
  - enero fév. marzo abr. Mayo Jun. juil. agosto sept./Set. OPO. novembre. DIC.
    
## <a name="func_eu_date1-deprecated"></a>Func_eu_date1 (déconseillée)

> [!NOTE]
> Cette fonction est déconseillée, car elle prend en charge uniquement les noms de mois portugais, qui sont désormais inclus dans la `Func_eu_date` fonction ci-dessus. 
  
Cette fonction recherche une date au format couramment utilisé en portugais. Le format de cette fonction est le même que `Func_eu_date` , qui diffère uniquement dans la langue utilisée.
  
Exemples :
  
- 2 dez 2016
    
- 02 dez 2016
    
- 2 dez 16
    
- 2/12/2016
    
- 02/12/16
    
- 2-dez-2016
    
- 2-12-16
    
Noms de mois acceptés :
  
- Portugais
    
  - janeiro, fevereiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
    
  - Jan Fev Mar Abr mai Jun Jul a été défini sur le mois de novembre dez
    
## <a name="func_eu_date2-deprecated"></a>Func_eu_date2 (déconseillée)

> [!NOTE]
> Cette fonction est déconseillée, car elle prend en charge uniquement les noms de mois néerlandais, qui sont désormais inclus dans la `Func_eu_date` fonction ci-dessus. 
  
Cette fonction recherche une date au format couramment utilisé en néerlandais. Le format de cette fonction est le même que `Func_eu_date` , qui diffère uniquement dans la langue utilisée.
  
Exemples :
  
- 2 Mei 2016
    
- 02 Mei 2016
    
- 2 Mei 16
    
- 2/12/2016
    
- 02/12/16
    
- 2-Mei-2016
    
- 2-12-16
    
Noms de mois acceptés :
  
- Dutch
    
  - januari, februari, maart, April, mei, juni, juli, augustus, September, ocktober, October, November, December
    
  - Jan fév maart avr Mei Jun Jul aoû Sep sept oct OKT nov déc
    
## <a name="func_expiration_date"></a>Func_expiration_date

Cette fonction recherche une date dans les formats couramment utilisés par les cartes de crédit et de débit, qui excluent les jours au profit des mois. Cette fonction correspond aux dates au format « mois/année », « mois-année », « [nom du mois] année » et « [abréviation mois-année] ». Les noms ou les abréviations des mois ne respectent pas la casse.
  
Exemples :
  
- MM/AA, par exemple, 01/11 ou 1/11
    
- MM/AAAA, par exemple, 01/2011 ou 1/2011
    
- MM-AA, par exemple, 01-22 ou 1-11
    
- MM-AAAA, par exemple, 01-2000 ou 1-2000
    
Les formats suivants prennent en charge AA ou AAAA :
  
- Mois-AAAA, par exemple, jan-2010, janvier-2010, jan-10 ou janvier-10
    
- Mois AAAA, par exemple, « janvier 2010 », « jan 2010 », « janvier 10 » ou « jan 10 »
    
- MoisAAAA, par exemple, « janvier2010 », « jan2010 », « janvier10 » ou « jan10 »
    
- Mois/aaaa--par exemple, « janvier/2010 » ou « Jan/2010 », « janvier/10 » ou « Jan/10 »
    
Noms de mois acceptés :
  
- English
    
  - Janvier, février, mars, avril, mai, juin, juillet, août, septembre, octobre, novembre, décembre
    
  - Jan Fév Mar Avr mai juin septembre sept octobre déc
    
## <a name="func_us_address"></a>Func_us_address

This function looks for a U.S. state name or postal abbreviation followed by a valid zip code, just as they are used in postal addresses. The zip code must be one of the correct zip codes associated with the U.S. state name or abbreviation. The U.S. state name and zip code cannot be separated by punctuation or letters.
  
Exemples :
  
- Washington 98052
    
- Washington 98052-9998
    
- WA 98052
    
- WA 98052-9998
    

