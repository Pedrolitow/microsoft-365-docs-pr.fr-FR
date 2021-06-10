---
title: Ce que les fonctions de protection contre la perte de données (DLP) recherchent
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
recommendations: false
description: Découvrez ce que les fonctions de protection contre la perte de données (DLP) recherchent.
ms.openlocfilehash: 47eda79470fd131939c493ac4f66af6efea01dd6
ms.sourcegitcommit: 1206319a5d3fed8d52a2581b8beafc34ab064b1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2021
ms.locfileid: "52086511"
---
# <a name="what-the-dlp-functions-look-for"></a>Éléments recherchés par les fonctions DLP

Les stratégies de protection contre la perte de données (DLP) peuvent utiliser des types d’informations sensibles pour identifier les éléments sensibles. Le numéro de carte de crédit et le numéro de carte de crédit de l’UE sont des exemples de types d’informations sensibles. Les types d’informations sensibles recherchent des modèles spécifiques. Les types d’informations sensibles valident les données en regardant leur format, leurs sommes de contrôle et recherchent des mots clés pertinents ou d’autres informations. Certaines de ces fonctionnalités sont effectuées par des fonctions internes. Par exemple, le type d’informations sensibles Numéro de carte de crédit utilise une fonction pour rechercher les dates qui sont formatées comme une date d’expiration. Cela permet de confirmer qu’un numéro est un numéro de carte de crédit.
  
Cet article explique ce que ces fonctions recherchent, pour vous aider à comprendre le fonctionnement des types d’informations sensibles prédéfincis. Pour plus d’informations, voir [Définitions d’entités de type d’informations sensibles](sensitive-information-type-entity-definitions.md)
  
## <a name="table-of-functions"></a>Table des fonctions

|nom de la fonction  |action de fonction  |est un validateur|
|---------|---------|---------|
|Func_Argentina_Unique_Tax_Key|détecte et valide la clé fiscale unique argentine|non|
|Func_aba_routing|détecte le numéro de routage ABA| oui|
|Func_alabama_drivers_license_number|détecte le numéro de permis de conduire de l’État d’Alabama|non|
|Func_alaska_delaware_oregon_drivers_license_number|détecte le numéro de permis de conduire De Oregon, Oregon|non|
|Func_alaska_drivers_license_number|détecte le numéro de permis de conduire De Alaska|non|
|Func_alberta_drivers_license_number|détecte le numéro de permis de conduire De l’Alberta|non|
|Func_Argentina_Unique_Tax_Key|détecte la clé fiscale unique argentine|non|
|Func_arizona_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_arkansas_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_australian_business_number|détecte le numéro d’entreprise Australie|non|
|Func_Australian_Company_Number|détecte le numéro de société australie|non|
|Func_australian_medical_account_number|détecte le numéro de compte médical australie|non|
|Func_australian_tax_file_number|détecte le numéro de fichier fiscal australie|oui|
|Func_austria_eu_ssn_or_equivalent|détecte le numéro de sécurité sociale d’Autriche|non|
|Func_austria_eu_tax_file_number|détecte le numéro de fichier fiscal autrichen|non|
|Func_Austria_Value_Added_Tax|détecte la taxe sur la valeur ajoutée en Autriche|non|
|Func_belgium_national_number|détecte le numéro national belgique|non|
|Func_belgium_value_added_tax_number|détecte le numéro de taxe sur la valeur ajoutée en Belgique|non|
|Func_brazil_cnpj|détecte le numéro d’entité juridique brésil (CNPJ)|oui|
|Func_brazil_cpf|détecte le brésil CPF|oui|
|Func_brazil_rg|détecte la R.A.S. du Brésil|non|
|Func_british_columbia_drivers_license_number|détecte le numéro de permis de conduire britannique|non|
|Func_bulgaria_eu_national_id_card|détecte le numéro civile uniforme bulgarien|non|
|Func_california_drivers_license_number|détecte le numéro de permis de conduire californien|non|
|Func_canadian_sin|détecte le sin canada|oui|
|Func_chile_id_card|détecte la carte d’ID chili|non|
|Func_china_resident_id|détecte l’ID résident en Chine|non|
|Func_colorado_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_connecticut_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_credit_card|détecte la carte de crédit|Oui|Non|
|Func_croatia_id_card|détecte la carte d’ID de Croatie|non|
|Func_croatia_oib_number|détecte le numéro de l’OIB en Croatie|non|
|Func_cyprus_eu_tax_file_number|détecte le numéro de fichier fiscal de Chypre|non|
|Func_czech_id_card|détecte la carte d’identité tchèque|non|
|Func_czech_id_card_new_format|détecte la carte d’identité tchèque dans un nouveau format|non|
|Func_dea_number|détecte le numéro DEA|oui|
|Func_denmark_eu_tax_file_number|détecte le numéro d’identification personnel du Danemark|non|
|Func_district_of_columbia_drivers_license_number|détecte le numéro de permis de conduire du district de Colombie|non|
|Func_estonia_eu_national_id_card|détecte le code d’identification personnel estonien|non|
|Func_eu_debit_card|détecte la carte de débit de l’UE|non|
|Func_finnish_national_id|détecte l’ID national finnois|non|
|Func_florida_drivers_license_number|détecte le numéro de permis de conduire De Sons|non|
|Func_florida_maryland_michigan_minnesota_drivers_license_number|détecte le numéro de permis de conduire de l’un des pilotes de l’état de l’État du États-Unis, de l’État du États-Unis et du États-Unis|non|
|Func_formatted_itin|détecte l’ITIN américain formaté|oui|
|Func_fr_insee|détecte la France INSEE|non|
|Func_fr_passport|détecte un passeport français|non|
|Func_france_eu_tax_file_number|détecte le numéro de fichier fiscal français|non|
|Func_france_value_added_tax_number|détecte le numéro de taxe sur la valeur ajoutée en France|non|
|Func_french_drivers_license|détecte le permis de conduire français|non|
|Func_french_insee|détecte le français INSEE|non|
|Func_georgia_drivers_license_number|détecte le numéro de permis de conduire géorgien|non|
|Func_german_drivers_license|détecte le permis de conduire allemand|non|
|Func_german_passport|détecte un passeport allemand|non|
|Func_german_passport_data|détecte un passeport allemand|non|
|Func_germany_eu_tax_file_number|détecte le numéro de fichier fiscal allemand|non|
|Func_germany_value_added_tax_number|détecte le numéro de taxe sur la valeur ajoutée en Allemagne|non|
|Func_greece_eu_ssn|détecte le sin grec (AMKA)|non|
|Func_hawaii_drivers_license_number|détecte le numéro de permis de conduire De Hawaii|non|
|Func_hong_kong_id_card |détecte la carte d’ID de Hong Kong|non|
|Func_hungarian_value_added_tax_number|détecte le numéro de taxe sur la valeur ajoutée en Hongrie|non|
|Func_hungary_eu_national_id_card|détecte le numéro d’identification personnel en Hongrie|non|
|Func_hungary_eu_ssn_or_equivalent|détecte le numéro de sécurité sociale en Hongrie|non|
|Func_hungary_eu_tax_file_number|détecte le numéro de fichier fiscal hongrie|non|
|Func_iban|détecte IBAN|oui|
|Func_idaho_drivers_license_number|détecte le numéro de permis de conduire DeNter|non|
|Func_illinois_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_india_aadhaar|détecte l’Inde aadhaar|oui|
|Func_indiana_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_iowa_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_ireland_pps|détecte les PPS d’Irlande|non|
|Func_israeli_national_id_number|détecte le numéro d’ID national israël|non|
|Func_italy_eu_national_id_card |détecte le code fiscal italien|non|
|Func_italy_value_added_tax_number|détecte le numéro de taxe sur la valeur ajoutée en Italie|non|
|Func_japanese_my_number_corporate|détecte le Japon mon numéro d’entreprise|oui|
|Func_japanese_my_number_personal|détecte le Japon mon numéro personnel|oui|
|Func_jp_bank_account|détecte un compte bancaire japonais|non|
|Func_jp_bank_account_branch_code|détecte le code de succursale d’un compte bancaire japonais|non|
|Func_jp_drivers_license_number|détecte le numéro de permis de conduire Japon|non|
|Func_jp_passport|détecte un passeport japonais|non|
|Func_jp_resident_registration_number|détecte le numéro d’inscription d’un résident japonais|non|
|Func_jp_sin|détecte le sin du Japon|non|
|Func_jp_sin_pre_1997|détecte le sin du Japon avant 1997|non|
|Func_kansas_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_kentucky_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_kentucky_massachusetts_virginia_drivers_license_number|détecte le numéro de permis de conduire DeNty, Massachusetts, États-Unis|non|
|Func_latvia_eu_national_id_card|détecte le code personnel letton|non|
|Func_lithuania_eu_tax_file_number|détecte le code personnel lituanien|non|
|Func_louisiana_drivers_license_number|détecte le numéro de permis de conduire de LaTns|non|
|Func_luxemburg_eu_tax_file_number|détecte le numéro d’identification national (personnes physiques)|non|
|Func_luxemburg_eu_tax_file_number_non_natural|détecte le numéro d’identification national (personnes non physiques)|non|
|Func_maine_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_manitoba_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_maryland_drivers_license_number|détecte le numéro de permis de conduire De Sons|non|
|Func_massachusetts_drivers_license_number|détecte le numéro de permis de conduire du Massachusetts|non|
|Func_mexico_population_registry_code|détecte le code du Registre de la population du Mexique|non|
|Func_michigan_minnesota_drivers_license_number|détecte le numéro de permis de conduire Du Monde|non|
|Func_minnesota_drivers_license_number|détecte le numéro de permis de conduire du États-Unis|non|
|Func_mississippi_oklahoma_drivers_license_number|détecte le numéro de permis de conduire Desoe|non|
|Func_missouri_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_montana_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_nebraska_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_netherlands_bsn|détecte le BSN (Pays-Bas)|non|
|Func_netherlands_eu_tax_file_number|détecte le numéro de fichier fiscal des Pays-Bas|non|
|Func_netherlands_value_added_tax_number|détecte le numéro de taxe sur la valeur ajoutée aux Pays-Bas|non|
|Func_nevada_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_new_brunswick_drivers_license_number|détecte le numéro de permis de conduire new-|non|
|Func_new_hampshire_drivers_license_number|détecte le numéro de permis de conduire new-|non|
|Func_new_jersey_drivers_license_number |détecte le numéro de permis de conduire du New Jersey|non|
|Func_new_mexico_drivers_license_number |détecte le numéro de permis de conduire du Nouveau Mexique|non|
|Func_new_york_drivers_license_number   |détecte le numéro de permis de conduire de New York|non|
|Func_new_zealand_bank_account_number   |détecte le numéro de compte bancaire nouvelle-zélande|non|
|Func_new_zealand_inland_revenue_number |détecte le numéro de revenu intérieur de la Nouvelle-Zélande|non|
|Func_new_zealand_ministry_of_health_number|détecte le numéro de santé du ministère de la Nouvelle-Zélande|non|
|Func_newfoundland_labrador_drivers_license_number|détecte le numéro de permis de conduire de l’Île-du-Nord|non|
|Func_newzealand_driver_license_number  |détecte le numéro de permis de conduire pour la Nouvelle-Zélande|non|
|Func_newzealand_social_welfare_number  |détecte le numéro de sécurité sociale de la Nouvelle-Zélande|non|
|Func_north_carolina_drivers_license_number|détecte le numéro de permis de conduire North Driver’s|non|
|Func_north_dakota_drivers_license_number|détecte le numéro de permis de conduire North Driver’s|non|
|Func_norway_id_number  |détecte le numéro d’ID norvégien|non|
|Func_nova_scotia_drivers_license_number|détecte le numéro de permis de conduire de l’entreprise|non|
|Func_ohio_drivers_license_number   |détecte le numéro de permis de conduire de Sons|non|
|Func_ontario_drivers_license_number    |détecte le numéro de permis de conduire de Sons|non|
|Func_pennsylvania_drivers_license_number|détecte le numéro de permis de conduire de #A0|non|
|Func_pesel_identification_number   |détecte l’ID national polonais (PESEL)|non|
|Func_poland_eu_tax_file_number |détecte le numéro de fichier fiscal polonais|non|
|Func_polish_national_id    |détecte la carte d’identité pologne|non|
|Func_polish_passport_number    |détecte le numéro de passeport polonais|non|
|Func_polish_regon_number   |détecte le numéro POLONAIS REGON|non|
|Func_portugal_eu_tax_file_number|détecte le numéro d’identification fiscale portugais|non|
|Func_prince_edward_island_drivers_license_number|détecte le numéro de permis de conduire de l’île de Îles-du-Îles|non|
|Func_quebec_drivers_license_number |détecte le numéro de permis de conduire de l’Permis de conduire|non|
|Func_randomized_formatted_ssn  |détecte le SSN américain au format aléatoire|oui|
|Func_randomized_unformatted_ssn|détecte le SSN américain non formaté aléatoire|oui|
|Func_rhode_island_drivers_license_number|détecte le numéro de permis de conduire de l’île DeSyr|non|
|Func_romania_eu_national_id_card   |détecte le code numérique personnel roumain (CNP)|non|
|Func_saskatchewan_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_slovakia_eu_national_id_card  |détecte le numéro personnel slovaque|non|
|Func_slovenia_eu_national_id_card  |détecte le numéro de citoyen maître unique de Slovénie|non|
|Func_slovenia_eu_tax_file_number   |détecte le numéro de fichier fiscal slovénien|non|
|Func_south_africa_identification_number|détecte le numéro d’identification de l’Afrique du Sud|oui|
|Func_south_carolina_drivers_license_number|détecte le numéro de permis de conduire Sud-Îles|non|
|Func_south_dakota_drivers_license_number|détecte le numéro de permis de conduire Sud-Îles|non|
|Func_south_korea_resident_number   |détecte le numéro de résident sud-coréen|non|
|Func_spain_eu_DL_and_NI_number_citizen |détecte les chiffres DL et NI espagnols|non|
|Func_spain_eu_DL_and_NI_number_foreigner|détecte les chiffres DL et NI d’Espagne|non|
|Func_spain_eu_driver’s_license_number  |détecte le numéro de permis de conduire espagnol|non|
|Func_spain_eu_tax_file_number  |détecte le numéro de fichier fiscal espagnol|non|
|Func_spanish_social_security_number|détecte le numéro de sécurité sociale espagnol|non|
|Func_ssn   |Fonction pour détecter le SSN américain au format non aléatoire|oui|
|Func_sweden_eu_tax_file_number|détecte le numéro de fichier fiscal suédois|non|
|Func_swedish_national_identifier|détecte l’identificateur national suédois|oui|
|Func_swiss_social_security_number_ahv|détecte le numéro de sécurité sociale suisse AHV|non|
|Func_taiwanese_national_id |détecte l’ID national taïwanais|non|
|Func_tennessee_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_texas_drivers_license_number  |détecte le numéro de permis de conduire texas|non|
|Func_Thai_Citizen_Id   |détecte l’ID de citoyen thaï|non|
|Func_Turkish_National_Id|détecte l’ID national turc|oui|
|Func_uk_drivers_license|détecte le permis de conduire au Royaume-Uni|non|
|Func_uk_eu_tax_file_number|détecte le numéro de contribuable unique du Royaume-Uni|non|
|Func_uk_nhs_number |détecte le numéro NHS au Royaume-Uni|oui|
|Func_uk_nino   |détecte le NINO (Royaume-Uni)|non|
|Func_unformatted_canadian_sin|détecte un SIN canadien non formaté|non|
|Func_unformatted_itin  |détecte les itins américains non formatés|oui|
|Func_unformatted_ssn   |détecte le SSN américain non aléatoire non aléatoire|oui|
|Func_usa_uk_passport   |détecte les passeports des États-Unis et du Royaume-Uni|oui|
|Func_utah_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_vermont_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_virginia_drivers_license_number|détecte le numéro de permis de conduire de Sons|non|
|Func_washington_drivers_license_number|détecte le numéro de permis de conduire washington|non|
|Func_west_virginia_drivers_license_number|détecte le numéro de permis de conduire de West Driver|non|
|Func_wisconsin_drivers_license_number  |détecte le numéro de permis de conduire de Sons|non|
|Func_wyoming_drivers_license_number    |détecte le numéro de permis de conduire de Sons|non|


## <a name="func_us_date"></a>Func_us_date

Func_us_date recherche les dates dans les formats américains courants. Les formats courants sont « mois/jour/année », « mois-jour-année » et « mois jour année ». Les noms ou abréviations des mois ne sont pas sensibles à la cas. 
  
Exemples :
  
- 2 décembre 2016
    
- 2 décembre 2016
    
- dec 02 2016
    
- 12/2/2016
    
- 12/02/16
    
- Dec-2-2016
    
- 12-2-16
    
Noms de mois acceptés :
  
- Français
    
  - Janvier, Février, Mars, Avril, peut, Juin, Juillet, Août, Septembre, Octobre, Novembre, Décembre
    
  - Jan. Feb. Mar. Apr. May June July Aug. Sept. Oct. Nov. Dec.
    
## <a name="func_eu_date"></a>Func_eu_date

Fund_eu_dates recherche les dates dans les États-Unis courants. formats (et la plupart des lieux en dehors des États-Unis), tels que « jour/mois/année », « jour-mois-année » et « jour mois année ». Les noms ou abréviations des mois ne sont pas sensibles à la cas.
  
Exemples :
  
- 2 décembre 2016
    
- 02 décembre 2016
    
- 2 décembre 16
    
- 2/12/2016
    
- 02/12/16
    
- 2-dec-2016
    
- 2-12-16
    
Noms de mois acceptés :
  
- Français
    
  - Janvier, Février, Mars, Avril, peut, Juin, Juillet, Août, Septembre, Octobre, Novembre, Décembre
    
  - Jan. Feb. Mar. Apr. May June July Aug. Sept. Oct. Nov. Dec.
    
- Néerlandais
    
  - januari, februari, maart, April, mei, juni, juli, augustus, September, ocktober, October, November, December
    
  - jan feb maart apr mei jun jul aug sep sept oct okt nov dec
    
- Français
    
  - janvier, février, mars, avril, mai, juin juillet, août, septembre, octobre, novembre, décembre
    
  - janv. févr. mars avril mai juin jril. août sept. oct. nov. déc.
    
- Allemand
    
  - jänuar, februar, märz, April, mai, juni juli, August, September, oktober, November, dezember
    
  - Jan./Jän. Feb. März Apr. Mai Juni Juli Aug. Sept. Okt. Nov. Dez.
    
- Italien
    
  - gennaio, febbraio, marzo, aprile, maggio, giugno, luglio, agosto, settembre,brebre, novembre, dicembre
    
  - genn. febbr. mar. apr. magg. giugno luglio ag. sett. ott. nov. dic.
    
- Portugais
    
  - janeiro, fevereiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
    
  - jan fev mar abr mai jun jul ago set out nov dez
    
- Espagnol
    
  - enero, febrero, marzo, abril, mayo, junio, général, agosto, septiembre, octubre, noviembre, diciembre
    
  - enero feb. marzo abr. mayo jun. jul. agosto sept./set. oct. nov. dic.
    
## <a name="func_eu_date1-deprecated"></a>Func_eu_date1 (déconseillée)

> [!NOTE]
> Cette fonction est dépréciée car elle prend en charge uniquement les noms de mois portugais, qui sont désormais inclus dans la  `Func_eu_date` fonction ci-dessus. 
  
Cette fonction recherche une date au format couramment utilisé en portugais. Le format de cette fonction est identique à  `Func_eu_date` , différent uniquement dans le langage utilisé.
  
Exemples :
  
- 2 dez 2016
    
- 02 dez 2016
    
- 2 Dez 16
    
- 2/12/2016
    
- 02/12/16
    
- 2-Dez-2016
    
- 2-12-16
    
Noms de mois acceptés :
  
- Portugais
    
  - janeiro, fevereiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
    
  - jan fev mar abr mai jun jul ago set out nov dez
    
## <a name="func_eu_date2-deprecated"></a>Func_eu_date2 (déconseillée)

> [!NOTE]
> Cette fonction est dépréciée car elle prend en charge uniquement les noms de mois néerlandais, qui sont désormais inclus dans la  `Func_eu_date` fonction ci-dessus. 
  
Cette fonction recherche une date au format couramment utilisé en néerlandais. Le format de cette fonction est identique à  `Func_eu_date` , différent uniquement dans le langage utilisé.
  
Exemples :
  
- 2 Mei 2016
    
- 02 mei 2016
    
- 2 Mei 16
    
- 2/12/2016
    
- 02/12/16
    
- 2-Mei-2016
    
- 2-12-16
    
Noms de mois acceptés :
  
- Néerlandais
    
  - januari, februari, maart, April, mei, juni, juli, augustus, September, ocktober, October, November, December
    
  - jan feb maart apr mei jun jul aug sep sept out okt nov dec
    
## <a name="func_expiration_date"></a>Func_expiration_date

Func_expiration_date recherche les dates qui sont dans des formats couramment utilisés par les cartes de crédit et de débit. Cette fonction correspond aux dates au format « mois/année », « mois-année », « [nom du mois] année » et « [abréviation du mois] année ». Les noms ou abréviations des mois ne sont pas sensibles à la cas.
  
Exemples :
  
- MM/AA, par exemple, 01/11 ou 1/11
    
- MM/AAAA, par exemple, 01/2011 ou 1/2011
    
- MM-AA, par exemple, 01-22 ou 1-11
    
- MM-AAAA, par exemple, 01-2000 ou 1-2000
    
Les formats suivants prennent en charge AA ou AAAA :
  
- Mois-AAAY - par exemple Jan-2010 ou janvier-2010 ou jan-10 ou janvier-10
    
- Mois AAAA, par exemple, « janvier 2010 », « jan 2010 », « janvier 10 » ou « jan 10 »
    
- MoisAAAA, par exemple, « janvier2010 », « jan2010 », « janvier10 » ou « jan10 »
    
- Mois/AAAAY : par exemple, « janvier/2010 » ou « jan/2010 » ou « janvier/10 » ou « jan/10 »
    
Noms de mois acceptés :
  
- Français
    
  - Janvier, Février, Mars, Avril, peut, Juin, Juillet, Août, Septembre, Octobre, Novembre, Décembre
    
  - Jan Feb Mar Apr May June July Aug Sept Oct Nov Dec
    
## <a name="func_us_address"></a>Func_us_address

Func_us_address recherche un nom d’état américain ou une abréviation postale suivie d’un code postal valide. Le code postal doit être l’un des codes postaux corrects qui sont associés au nom de l’état américain ou à son abréviation. Le nom de l’état américain et le code postal ne doivent pas être séparés par des signes de ponctuation ou des lettres.
  
Exemples :
  
- Washington 98052
    
- Washington 98052-9998
    
- WA 98052
    
- WA 98052-9998
