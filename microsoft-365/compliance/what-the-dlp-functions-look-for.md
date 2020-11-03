---
title: Les fonctions de protection contre la perte de données (DLP)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
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
description: Découvrez les fonctions de protection contre la perte de données (DLP).
ms.openlocfilehash: b77075b0b31ad5d6e6e2b7062c35e96649fa8365
ms.sourcegitcommit: e56894917d2aae05705c3b9447388d10e2156183
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48841445"
---
# <a name="what-the-dlp-functions-look-for"></a>Éléments recherchés par les fonctions DLP

Les stratégies de protection contre la perte de données (DLP) peuvent utiliser des types d’informations sensibles pour identifier des éléments sensibles. Le numéro de carte de crédit et le numéro de carte de débit UE sont des exemples de types d’informations sensibles. Les types d’informations sensibles recherchent des modèles spécifiques. Les types d’informations sensibles valident les données en leur format, leurs Checksum, et recherche des mots clés pertinents ou d’autres informations. Certaines de ces fonctionnalités sont effectuées par des fonctions internes. Par exemple, le type d’informations sensibles de numéro de carte de crédit utilise une fonction pour rechercher les dates qui sont mises en forme comme une date d’expiration. Cela permet de corroborer qu’un numéro est un numéro de carte de crédit.
  
Cet article explique ce que ces fonctions recherchent, pour vous aider à comprendre le fonctionnement des types d’informations sensibles prédéfinis. Pour plus d’informations, consultez la rubrique [informations sensibles type d’entité définitions](sensitive-information-type-entity-definitions.md)
  
## <a name="table-of-functions"></a>Tableau des fonctions

|nom de la fonction  |action de fonction  |est un validateur|
|---------|---------|---------|
|Func_Argentina_Unique_Tax_Key|détecte et valide la clé fiscale unique Argentine|Non|
|Func_aba_routing|détecte le numéro de routage ABA| oui|
|Func_alabama_drivers_license_number|détecte le numéro de permis de conduire du pilote Alabama|Non|
|Func_alaska_delaware_oregon_drivers_license_number|détecte l’Alaska, le Delaware, le numéro de permis de conduire de l’Oregon|Non|
|Func_alaska_drivers_license_number|détecte le numéro de permis de conduire Alaska|Non|
|Func_alberta_drivers_license_number|détecte le numéro de permis de conduire d’Alberta|Non|
|Func_Argentina_Unique_Tax_Key|détecte la clé fiscale unique Argentine|Non|
|Func_arizona_drivers_license_number|détecte le numéro de permis de conduire d’Arizona|Non|
|Func_arkansas_drivers_license_number|détecte le numéro de permis de conduire Arkansas|Non|
|Func_australian_business_number|détecte le numéro d’entreprise Australie|Non|
|Func_Australian_Company_Number|détecte le numéro de société Australie|Non|
|Func_australian_medical_account_number|détecte le numéro de compte médical Australie|Non|
|Func_australian_tax_file_number|Numéro de fichier de taxe Australie|oui|
|Func_austria_eu_ssn_or_equivalent|détecte le numéro de sécurité sociale autrichien|Non|
|Func_austria_eu_tax_file_number|détecte le numéro de fichier fiscal autrichien|Non|
|Func_Austria_Value_Added_Tax|détecte la taxe sur la valeur ajoutée autrichienne|Non|
|Func_belgium_national_number|détecte le numéro national belge|Non|
|Func_belgium_value_added_tax_number|détecte le numéro de TVA belge à la valeur ajoutée|Non|
|Func_brazil_cnpj|détecte le numéro d’entité juridique brésilienne (CNPJ)|oui|
|Func_brazil_cpf|détecte le Brésil CPF|oui|
|Func_brazil_rg|détecte le RG Brésil|Non|
|Func_british_columbia_drivers_license_number|détecte le numéro de permis de conduire de la British Columbia|Non|
|Func_bulgaria_eu_national_id_card|détecte le numéro civil uniforme de la Bulgarie|Non|
|Func_california_drivers_license_number|détecte le numéro de permis de conduire du pilote California|Non|
|Func_canadian_sin|détecte le NAS du Canada|oui|
|Func_chile_id_card|détecte la carte d’identité Chili|Non|
|Func_china_resident_id|détecte l’ID résident de la Chine|Non|
|Func_colorado_drivers_license_number|détecte le numéro de permis de conduire Colorado|Non|
|Func_connecticut_drivers_license_number|détecte le numéro de permis de conduire Connecticut|Non|
|Func_credit_card|détecte une carte de crédit|Oui|Non|
|Func_croatia_id_card|détecte la carte d’identité de Croatie|Non|
|Func_croatia_oib_number|détecte le numéro OIB de Croatie|Non|
|Func_cyprus_eu_tax_file_number|détecte le numéro de fichier de taxe de Chypre|Non|
|Func_czech_id_card|détecte la carte d’identité tchèque|Non|
|Func_czech_id_card_new_format|détecte la carte d’identité tchèque dans le nouveau format|Non|
|Func_dea_number|détecte le numéro de DEA|oui|
|Func_denmark_eu_tax_file_number|détecte le numéro d’identification personnel Danemark|Non|
|Func_district_of_columbia_drivers_license_number|détecte le numéro de permis de conduire du pilote Columbia|Non|
|Func_estonia_eu_national_id_card|détecte le code d’identification personnelle en Estonie|Non|
|Func_eu_debit_card|détecte une carte de débit UE|Non|
|Func_finnish_national_id|détecte l’ID national finnois|Non|
|Func_florida_drivers_license_number|détecte le numéro de permis de conduire du pilote de la Floride|Non|
|Func_florida_maryland_michigan_minnesota_drivers_license_number|détecte le numéro de permis de conduire de la Floride, du Maryland, du Michigan, du fabricant de Minnesota|Non|
|Func_formatted_itin|détecte le format américain ITIN|oui|
|Func_fr_insee|détecte la France INSEE|Non|
|Func_fr_passport|détecte la fonctionnalité Passport France|Non|
|Func_france_eu_tax_file_number|Numéro de fichier de taxe France détecté|Non|
|Func_france_value_added_tax_number|détecte le numéro de TVA de la valeur ajoutée France|Non|
|Func_french_drivers_license|détecte la licence du pilote français|Non|
|Func_french_insee|détecte le français INSEE|Non|
|Func_georgia_drivers_license_number|détecte le numéro de permis de conduire Georgia|Non|
|Func_german_drivers_license|détecte la licence du pilote d’Allemagne|Non|
|Func_german_passport|détecte le passeport en Allemagne|Non|
|Func_german_passport_data|détecte le passeport en Allemagne|Non|
|Func_germany_eu_tax_file_number|Numéro de fichier de taxe d’Allemagne détecté|Non|
|Func_germany_value_added_tax_number|détecte le numéro de taxe ajouté à la valeur d’Allemagne|Non|
|Func_greece_eu_ssn|détecte le NAS de Grèce (AMKA)|Non|
|Func_hawaii_drivers_license_number|détecte le numéro de permis de conduire Hawaii|Non|
|Func_hong_kong_id_card |détecte la carte d’identité de Hong Kong|Non|
|Func_hungarian_value_added_tax_number|détecte le numéro de taxe de la valeur ajoutée à la Hongrie|Non|
|Func_hungary_eu_national_id_card|détecte le numéro d’identification personnel de Hongrie|Non|
|Func_hungary_eu_ssn_or_equivalent|détecte le numéro de sécurité sociale de la Hongrie|Non|
|Func_hungary_eu_tax_file_number|détecte le numéro de fichier de taxe Hongrie|Non|
|Func_iban|détecte le IBAN|oui|
|Func_idaho_drivers_license_number|détecte le numéro de permis de conduire Idaho|Non|
|Func_illinois_drivers_license_number|détecte le numéro de permis de conduire de l’Illinois|Non|
|Func_india_aadhaar|détecte l’Inde aadhaar|oui|
|Func_indiana_drivers_license_number|détecte le numéro de permis de conduire d’Indiana|Non|
|Func_iowa_drivers_license_number|détecte le numéro de permis de conduire Iowa|Non|
|Func_ireland_pps|détecte l’Irlande PPS|Non|
|Func_israeli_national_id_number|détecte le numéro d’identification national d’Israël|Non|
|Func_italy_eu_national_id_card |détecte le code fiscal de l’Italie|Non|
|Func_italy_value_added_tax_number|détecte le numéro de taxe de la valeur ajoutée pour l’Italie|Non|
|Func_japanese_my_number_corporate|détecte le Japon mon numéro entreprise|oui|
|Func_japanese_my_number_personal|détecte mon numéro de Japon personnel|oui|
|Func_jp_bank_account|détecte le compte bancaire japonais|Non|
|Func_jp_bank_account_branch_code|détecte le code de succursale du compte bancaire japonais|Non|
|Func_jp_drivers_license_number|détecte le numéro de permis de conduire Japon|Non|
|Func_jp_passport|détecte le passeport japonais|Non|
|Func_jp_resident_registration_number|détecte le numéro d’enregistrement résident au Japon|Non|
|Func_jp_sin|détecte le NAS japonais|Non|
|Func_jp_sin_pre_1997|détecte le NAS Japan 1997|Non|
|Func_kansas_drivers_license_number|détecte le numéro de permis de conduire Kansas|Non|
|Func_kentucky_drivers_license_number|détecte le numéro de permis de conduire du pilote du Kentucky|Non|
|Func_kentucky_massachusetts_virginia_drivers_license_number|détecte le Kentucky, le Massachusetts, le numéro de permis de conduire de la Virginie|Non|
|Func_latvia_eu_national_id_card|détecte le code personnel en Lettonie|Non|
|Func_lithuania_eu_tax_file_number|détecte le code personnel de Lituanie|Non|
|Func_louisiana_drivers_license_number|détecte le numéro de permis de conduire Louisiane|Non|
|Func_luxemburg_eu_tax_file_number|détecte le numéro d’identification nationale du Luxembourg (personnes physiques)|Non|
|Func_luxemburg_eu_tax_file_number_non_natural|détecte le numéro d’identification nationale du Luxembourg (personnes non physiques)|Non|
|Func_maine_drivers_license_number|détecte le numéro de permis de conduire du chauffeur|Non|
|Func_manitoba_drivers_license_number|détecte le numéro de permis de conduire du pilote Manitoba|Non|
|Func_maryland_drivers_license_number|détecte le numéro de permis de conduire de la recherche de Maryland|Non|
|Func_massachusetts_drivers_license_number|détecte le numéro de permis de conduire du pilote du Massachusetts|Non|
|Func_mexico_population_registry_code|détecte le code de registre de la population du Mexique|Non|
|Func_michigan_minnesota_drivers_license_number|détecte le numéro de permis de conduire du permis de conduire|Non|
|Func_minnesota_drivers_license_number|détecte le numéro de permis de conduire du fabricant de Minnesota|Non|
|Func_mississippi_oklahoma_drivers_license_number|détecte Mississippi, numéro de permis de conduire Oklahoma|Non|
|Func_missouri_drivers_license_number|détecte le numéro de permis de conduire du pilote Missouri|Non|
|Func_montana_drivers_license_number|détecte le numéro de permis de conduire Montana|Non|
|Func_nebraska_drivers_license_number|détecte le numéro de permis de conduire Nebraska|Non|
|Func_netherlands_bsn|détecte les BSN Pays-Bas|Non|
|Func_netherlands_eu_tax_file_number|détecte le numéro de fichier fiscal néerlandais|Non|
|Func_netherlands_value_added_tax_number|détecte le numéro de taxe ajoutée aux Pays-Bas|Non|
|Func_nevada_drivers_license_number|détecte le numéro de permis de conduire Nevada|Non|
|Func_new_brunswick_drivers_license_number|détecte le numéro de permis de conduire du nouveau pilote Brunswick|Non|
|Func_new_hampshire_drivers_license_number|détecte le nouveau numéro de permis de conduire Hampshire|Non|
|Func_new_jersey_drivers_license_number |détecte le numéro de permis de conduire du nouveau pilote Jersey|Non|
|Func_new_mexico_drivers_license_number |détecte le nouveau numéro de permis de conduire du pilote mexicain|Non|
|Func_new_york_drivers_license_number   |détecte le numéro de permis de conduire de New York|Non|
|Func_new_zealand_bank_account_number   |détecte le numéro de compte bancaire de la Nouvelle-Zélande|Non|
|Func_new_zealand_inland_revenue_number |détecte le numéro de revenu Inland de la Nouvelle-Zélande|Non|
|Func_new_zealand_ministry_of_health_number|détecte le ministère de l’assurance Nouvelle-Zélande|Non|
|Func_newfoundland_labrador_drivers_license_number|détecte le numéro de permis de conduire de la société Terre-Neuve|Non|
|Func_newzealand_driver_license_number  |détecte le numéro de licence de pilote Nouvelle-Zélande|Non|
|Func_newzealand_social_welfare_number  |détecte le numéro de la protection sociale de Nouvelle-Zélande|Non|
|Func_north_carolina_drivers_license_number|détecte le numéro de permis de conduire du pilote nord de Caroline|Non|
|Func_north_dakota_drivers_license_number|détecte le numéro de permis de conduire Nord Dakota|Non|
|Func_norway_id_number  |détecte le numéro d’identification de la Norvège|Non|
|Func_nova_scotia_drivers_license_number|détecte le numéro de permis de conduire de la Nouvelle-Écosse|Non|
|Func_ohio_drivers_license_number   |détecte le numéro de permis de conduire d’Ohio|Non|
|Func_ontario_drivers_license_number    |détecte le numéro de permis de conduire du pilote Ontario|Non|
|Func_pennsylvania_drivers_license_number|détecte le numéro de permis de conduire de Pennsylvanie|Non|
|Func_pesel_identification_number   |détecte l’ID national de la Pologne (PESEL)|Non|
|Func_poland_eu_tax_file_number |détecte le numéro de fichier de taxe de Pologne|Non|
|Func_polish_national_id    |détecte la carte d’identité Pologne|Non|
|Func_polish_passport_number    |détecte le numéro de passeport polonais|Non|
|Func_polish_regon_number   |détecte le numéro REGON polonais|Non|
|Func_portugal_eu_tax_file_number|détecte le numéro d’identification fiscale de la taxe Portugal|Non|
|Func_prince_edward_island_drivers_license_number|détecte le numéro de permis du pilote du Prince Edward Island|Non|
|Func_quebec_drivers_license_number |détecte le numéro de permis de conduire Québec|Non|
|Func_randomized_formatted_ssn  |détecte le numéro de sécurité sociale formaté de manière aléatoire|oui|
|Func_randomized_unformatted_ssn|détecte le numéro de sécurité sociale non formaté de manière aléatoire|oui|
|Func_rhode_island_drivers_license_number|détecte le numéro de permis de conduire Rhode Island|Non|
|Func_romania_eu_national_id_card   |détecte le code numérique personnel en Roumanie (CNP)|Non|
|Func_saskatchewan_drivers_license_number|détecte le numéro de permis de conduire de la société|Non|
|Func_slovakia_eu_national_id_card  |détecte le numéro personnel de Slovaquie|Non|
|Func_slovenia_eu_national_id_card  |détecte le numéro de citoyen principal unique de Slovénie|Non|
|Func_slovenia_eu_tax_file_number   |détecte le numéro de fichier fiscal de Slovénie|Non|
|Func_south_africa_identification_number|détecte le numéro d’identification Afrique du Sud|oui|
|Func_south_carolina_drivers_license_number|détecte le numéro de permis de conduire du pilote sud de la Caroline|Non|
|Func_south_dakota_drivers_license_number|détecte le numéro de permis de conduire Sud Dakota|Non|
|Func_south_korea_resident_number   |détecte le numéro de résident de Corée du Sud|Non|
|Func_spain_eu_DL_and_NI_number_citizen |détecte les numéros d’Espagne DL et NI le citoyen|Non|
|Func_spain_eu_DL_and_NI_number_foreigner|détecte les listes de distribution et les étrangers aux numéros d’Espagne|Non|
|Func_spain_eu_driver’s_license_number  |détecte le numéro de permis de conduire de l’Espagne|Non|
|Func_spain_eu_tax_file_number  |Numéro de fichier de taxe Espagne|Non|
|Func_spanish_social_security_number|détecte le numéro de sécurité sociale espagnol|Non|
|Func_ssn   |Fonction permettant de détecter le numéro de sécurité sociale formaté non aléatoire|oui|
|Func_sweden_eu_tax_file_number|détecte le numéro de fichier de taxe Suède|Non|
|Func_swedish_national_identifier|détecte l’identificateur national suédois|oui|
|Func_swiss_social_security_number_ahv|détecte le numéro d’assurance sociale Suisse AVS|Non|
|Func_taiwanese_national_id |détecte l’ID national taïwanais|Non|
|Func_tennessee_drivers_license_number|détecte le numéro de permis de conduire Tennessee|Non|
|Func_texas_drivers_license_number  |détecte le numéro de permis de conduire du pilote Texas|Non|
|Func_Thai_Citizen_Id   |détecte l’ID de citoyen thaï|Non|
|Func_Turkish_National_Id|détecte l’ID national turc|oui|
|Func_uk_drivers_license|détecte la licence du pilote UK|Non|
|Func_uk_eu_tax_file_number|détecte le numéro de contribuable UK unique|Non|
|Func_uk_nhs_number |détecte le numéro UK (Royaume-Uni)|oui|
|Func_uk_nino   |détecte la NINO UK|Non|
|Func_unformatted_canadian_sin|détecte le NAS canadien non formaté|Non|
|Func_unformatted_itin  |détecte les ITIN US non mis en forme|oui|
|Func_unformatted_ssn   |détecte le numéro de sécurité sociale non aléatoire non aléatoire|oui|
|Func_usa_uk_passport   |détecte les passeports américains et britanniques|oui|
|Func_utah_drivers_license_number|détecte le numéro de permis de conduire du pilote Utah|Non|
|Func_vermont_drivers_license_number|détecte le numéro de permis de conduire Vermont|Non|
|Func_virginia_drivers_license_number|détecte le numéro de permis de conduire de Virginie|Non|
|Func_washington_drivers_license_number|détecte le numéro de permis de conduire Washington|Non|
|Func_west_virginia_drivers_license_number|détecte le numéro de permis de conduire West Virginie|Non|
|Func_wisconsin_drivers_license_number  |détecte le numéro de permis de conduire du pilote Wisconsin|Non|
|Func_wyoming_drivers_license_number    |détecte le numéro de permis de conduire Wyoming|Non|


## <a name="func_us_date"></a>Func_us_date

Func_us_date recherche des dates aux formats américains courants. Les formats courants sont « mois/jour/année », « mois-jour-année » et « mois de jour du mois ». Les noms ou abréviations de mois ne sont pas sensibles à la casse. 
  
Exemples :
  
- 2 décembre 2016
    
- 2 décembre 2016
    
- DEC 02 2016
    
- 12/2/2016
    
- 12/02/16
    
- Déc-2-2016
    
- 12-2-16
    
Noms de mois acceptés :
  
- Anglais
    
  - Janvier, février, mars, avril, mai, juin, juillet, août, septembre, octobre, novembre, décembre
    
  - Jan. fév. Mar. mai du 1er juillet aoû. septembre. Oct. nov. déc
    
## <a name="func_eu_date"></a>Func_eu_date

Fund_eu_dates recherche des dates en Union commune formats (et la plupart des emplacements en dehors des États-Unis), tels que « jour/mois/année », « jour-mois-année » et « année mois de jour ». Les noms ou abréviations de mois ne sont pas sensibles à la casse.
  
Exemples :
  
- 2 déc 2016
    
- 02 déc 2016
    
- 2 déc 16
    
- 2/12/2016
    
- 02/12/16
    
- 2-déc-2016
    
- 2-12-16
    
Noms de mois acceptés :
  
- Anglais
    
  - Janvier, février, mars, avril, mai, juin, juillet, août, septembre, octobre, novembre, décembre
    
  - Jan. fév. Mar. mai du 1er juillet aoû. septembre. Oct. nov. déc
    
- Néerlandais
    
  - januari, februari, maart, April, mei, juni, juli, augustus, September, ocktober, October, November, December
    
  - Jan fév maart avr Mei Jun Jul aoû Sep sept oct OKT nov déc
    
- Français
    
  - janvier, février, mars, avril, mai, juin juillet, août, septembre, octobre, novembre, décembre
    
  - janv. févr. mars avril Maï juin juil. août sept. OPO. novembre. déc.
    
- Allemand
    
  - jänuar, Februar, März, avril, mai, Juni Juli, août, septembre, oktober, novembre, Dezember
    
  - Jan./Jän. Fév. März avr. Maï Juni Juli aoû. sept. Okt. Nov. Dez.
    
- Italien
    
  - gennaio, febbraio, marzo, aprile, maggio, giugno, luglio, agosto, settembre, ottobre, novembre, dicembre
    
  - genn. febbr. détériore. avancé. magg. giugno luglio AG. sett. Verlag. novembre. DIC.
    
- Portugais
    
  - janeiro, fevereiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
    
  - Jan Fev Mar Abr mai Jun Jul a été défini sur le mois de novembre dez
    
- Espagnol
    
  - enero, febrero, marzo, abril, mayo, junio, julio, agosto, septiembre, octubre, noviembre, diciembre
    
  - enero fév. marzo abr. Mayo Jun. juil. agosto sept./Set. OPO. novembre. DIC.
    
## <a name="func_eu_date1-deprecated"></a>Func_eu_date1 (déconseillée)

> [!NOTE]
> Cette fonction est déconseillée, car elle prend en charge uniquement les noms de mois portugais, qui sont désormais inclus dans la  `Func_eu_date` fonction ci-dessus. 
  
Cette fonction recherche une date au format couramment utilisé en portugais. Le format de cette fonction est le même que  `Func_eu_date` , qui diffère uniquement dans la langue utilisée.
  
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
> Cette fonction est déconseillée, car elle prend en charge uniquement les noms de mois néerlandais, qui sont désormais inclus dans la  `Func_eu_date` fonction ci-dessus. 
  
Cette fonction recherche une date au format couramment utilisé en néerlandais. Le format de cette fonction est le même que  `Func_eu_date` , qui diffère uniquement dans la langue utilisée.
  
Exemples :
  
- 2 Mei 2016
    
- 02 Mei 2016
    
- 2 Mei 16
    
- 2/12/2016
    
- 02/12/16
    
- 2-Mei-2016
    
- 2-12-16
    
Noms de mois acceptés :
  
- Néerlandais
    
  - januari, februari, maart, April, mei, juni, juli, augustus, September, ocktober, October, November, December
    
  - Jan fév maart avr Mei Jun Jul aoû Sep sept parti OKT nov déc
    
## <a name="func_expiration_date"></a>Func_expiration_date

Func_expiration_date recherche des dates dans des formats couramment utilisés par les cartes de crédit et de débit. Cette fonction correspond aux dates au format « mois/année », « mois-année », « [nom du mois] année » et « [abréviation mois-année] ». Les noms ou abréviations de mois ne sont pas sensibles à la casse.
  
Exemples :
  
- MM/AA, par exemple, 01/11 ou 1/11
    
- MM/AAAA, par exemple, 01/2011 ou 1/2011
    
- MM-AA, par exemple, 01-22 ou 1-11
    
- MM-AAAA, par exemple, 01-2000 ou 1-2000
    
Les formats suivants prennent en charge AA ou AAAA :
  
- Mois-aaaa--par exemple, Jan-2010, janvier-2010 ou Jan-10 ou janvier-10
    
- Mois AAAA, par exemple, « janvier 2010 », « jan 2010 », « janvier 10 » ou « jan 10 »
    
- MoisAAAA, par exemple, « janvier2010 », « jan2010 », « janvier10 » ou « jan10 »
    
- Mois/aaaa--par exemple, « janvier/2010 » ou « Jan/2010 », « janvier/10 » ou « Jan/10 »
    
Noms de mois acceptés :
  
- Anglais
    
  - Janvier, février, mars, avril, mai, juin, juillet, août, septembre, octobre, novembre, décembre
    
  - Jan Fév Mar Avr mai juin septembre sept octobre déc
    
## <a name="func_us_address"></a>Func_us_address

Func_us_address recherche un nom d’État américain ou une abréviation postale suivie d’un code postal valide. Le code postal doit être l’un des codes postaux corrects qui sont associés au nom de l’état américain ou à son abréviation. Le nom de l’état américain et le code postal ne doivent pas être séparés par des signes de ponctuation ou des lettres.
  
Exemples :
  
- Washington 98052
    
- Washington 98052-9998
    
- WA 98052
    
- WA 98052-9998
