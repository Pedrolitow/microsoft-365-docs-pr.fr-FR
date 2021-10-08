---
title: Définitions d’entités des types d’informations sensibles
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
description: 200 types d’informations sensibles sont prêts à être utilisés dans vos stratégies DLP. Cet article répertorie tous ces types d’informations sensibles et indique ce qu’une stratégie DLP recherche lorsqu’elle détecte chaque type.
ms.openlocfilehash: 9d018833f6dd6d63ff32e8a3d77209177d7709f6
ms.sourcegitcommit: 166bf635c0905ae12c04b1865cb17aadef81e82a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2021
ms.locfileid: "60245680"
---
# <a name="sensitive-information-type-entity-definitions"></a>Définitions d’entités des types d’informations sensibles

Cet article répertorie toutes les définitions d’entité de type d’informations sensibles. Chaque définition indique ce qu’une stratégie DLP recherche pour détecter chaque type. Pour en savoir plus sur les types d’informations sensibles, voir [Types d’informations sensibles](sensitive-information-type-learn-about.md)

## <a name="aba-routing-number"></a>Numéro de routage ABA

### <a name="format"></a>Format

neuf chiffres qui peuvent être dans un modèle formaté ou sans mise en forme

### <a name="pattern"></a>Modèle

- deux chiffres dans les plages 00-12, 21-32, 61-72 ou 80
- deux chiffres
- un trait d’union facultatif
- quatre chiffres
- un trait d’union facultatif
- un chiffre


### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_aba_routing trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ABA_Routing est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_aba_routing trouve un contenu qui correspond au modèle.

```xml
    <!-- ABA Routing Number -->
    <Entity id="cb353f78-2b72-4c3c-8827-92ebe4f69fdf" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_aba_routing" />
        <Match idRef="Keyword_ABA_Routing" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_aba_routing" />
      </Pattern>
    </Entity>
```


### <a name="keywords"></a>Mots clés

#### <a name="keyword_aba_routing"></a>Keyword_aba_routing

- numéro aba
- aba #
- aba
- abarouting #
- abaroutingnumber
- americanbankassociationrouting #
- americanbankassociationroutingnumber
- bankrouting #
- bankroutingnumber
- routage #
- routage non
- numéro de routage
- numéro de routage
- routage #
- RTN


## <a name="argentina-national-identity-dni-number"></a>Numéro d’identité nationale (DNI) argentine

### <a name="format"></a>Format

Huit chiffres avec ou sans points

### <a name="pattern"></a>Modèle

Huit chiffres :
- deux chiffres
- période facultative
- trois chiffres
- période facultative
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_argentina_national_id trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_argentina_national_id est trouvé.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Argentina National Identity number
- cedula
- butula
- dni
- documento nacional de identidad
- documento número
- documento numero
- registro nacional de las personas
- rnp

## <a name="argentina-unique-tax-identification-key-cuitcuil"></a>Clé d’identification fiscale unique (PROGRAMME DNS) Argentine

### <a name="format"></a>Format

11 chiffres avec tiret

### <a name="pattern"></a>Modèle

11 chiffres avec un tiret :
- deux chiffres dans les 20, 23, 24, 27, 30, 33 ou 34
- un trait d’union (-)
- huit chiffres
- un trait d’union (-)
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_Argentina_Unique_Tax_Key` trouve un contenu qui correspond au modèle.
- Un mot clé est `Keyword_Argentina_Unique_Tax_Key` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_Argentina_Unique_Tax_Key` trouve un contenu qui correspond au modèle.

```xml
    <!-- Argentina Unique Tax Identification Key (CUIT/CUIL) -->
      <Entity id="98da3da1-9199-4571-b7c4-b6522980b507" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
          <Match idRef="Keyword_Argentina_Unique_Tax_Key" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_argentina_unique_tax_key"></a>Keyword_Argentina_Unique_Tax_Key

- Clave Unica de Identificacion Casia
- LASER
- code unique d’identification d’identification 
- Clave Única de Identificación Tributaria
- code d’identification unique
- C FCD
- Clé d’identification fiscale unique
- Clé d’identification Unique Identification
- Clé unique d’identification d’identification
- Code d’identification de travail unique
- Code d’identification de travail unique
- Clé d’identification de travail unique
- Clé unique d’identification de travail
- Code unique d’identification fiscale
- Clé unique d’identification fiscale
- Code d’identification de travail unique
- Code d’identification de travail unique
- Clé d’identification de travail unique
- Clé unique d’identification du travail
- ID de taxe
- taxID #
- taxId
- Erdnumber
- numéro de taxe
- pas de taxe
- taxe #
- taxe #
- ID du contribuable
- numéro du contribuable
- pas de taxe
- contribuable #
- contribuable #
- identité fiscale
- identification fiscale
- Número de Identificación Fiscal
- número de quyente


## <a name="australia-bank-account-number"></a>Numéro de compte bancaire australie

### <a name="format"></a>Format

six à 10 chiffres avec ou sans numéro de succursale bancaire

### <a name="pattern"></a>Modèle

Le numéro de compte est de 6 à 10 chiffres.

Numéro de succursale bancaire en Australie :
- trois chiffres
- un trait d’union
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_australia_bank_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_australia_bank_account_number est trouvé.
- L’expression régulière Regex_australia_bank_account_number_bsb trouve un contenu qui correspond au modèle.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_australia_bank_account_number trouve un contenu qui correspond au modèle.

- Un mot clé figurant dans la liste Keyword_australia_bank_account_number est trouvé.

```xml
<!-- Australia Bank Account Number -->
<Entity id="74a54de9-2a30-4aa0-a8aa-3d9327fc07c7" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
        <Match idRef="Regex_australia_bank_account_number_bsb" />
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
  </Pattern>
 </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_australia_bank_account_number"></a>Keyword_australia_bank_account_number

- code swift banque
- banque correspondante
- devise de base
- compte aux États-Unis
- adresse du titulaire
- adresse de la banque
- informations du compte
- transferts de fonds
- frais bancaires
- informations sur la banque
- informations bancaires
- noms complets
- iaea

## <a name="australia-business-number"></a>Numéro d’entreprise Australie
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft


### <a name="format"></a>Format

11 chiffres avec des délimiteur facultatifs

### <a name="pattern"></a>Modèle

11 chiffres avec des délimiteur facultatifs :

- deux chiffres
- trait d’union ou espace facultatif
- trois chiffres
- trait d’union ou espace facultatif
- trois chiffres
- trait d’union ou espace facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_australian_business_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_australian_business_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_australian_business_number trouve un contenu qui correspond au modèle.

```xml
      <!-- Australia Business Number -->
      <Entity id="76e83b3b-01ee-4530-aced-e667a6609f49" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_australian_business_number" />
          <Match idRef="Keywords_australian_business_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_australian_business_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keyword_australia_business_number"></a>Keyword_australia_business_number

- australie business no
- numéro d’entreprise
- abn #
- businessid #
- business id
- abn
- businessno #

## <a name="australia-company-number"></a>Numéro de société australien
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

neuf chiffres avec des délimiteur

### <a name="pattern"></a>Modèle

neuf chiffres avec des délimiteur :

- trois chiffres
- un espace
- trois chiffres
- un espace
- trois chiffres


### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_Australian_Company_Number trouve un contenu qui correspond au modèle.
- Un mot clé de Keyword_Australian_Company_Number est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_Australian_Company_Number trouve un contenu qui correspond au modèle.

```xml
      <!-- Australia Company Number -->
      <Entity id="b1fba4f7-7b3e-4bb9-8f9a-9366df604dbb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Australian_Company_Number" />
          <Match idRef="Keyword_Australian_Company_Number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_Australian_Company_Number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keyword_australia_company_number"></a>Keyword_australia_company_number

- can
- australia company no
- australia company no #
- numéro de société australie
- société australien non
- société australien non #
- numéro de société australien

## <a name="australia-drivers-license-number"></a>Numéro de permis de conduire australien

### <a name="format"></a>Format

neuf lettres et chiffres

### <a name="pattern"></a>Modèle

neuf lettres et chiffres :

- deux chiffres ou lettres (ne sont pas sensibles à la majuscule) ;
- deux chiffres
- cinq chiffres ou lettres (ne sont pas sensibles à la majuscule)

OR

- une à deux lettres facultatives (ne sensibles pas à la majuscule)
- quatre à neuf chiffres

OR

- neuf chiffres ou lettres (ne sensibles pas à la majuscule)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_australia_drivers_license_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_australia_drivers_license_number est trouvé.
- Aucun mot clé figurant dans la liste Keyword_australia_drivers_license_number_exclusions n’est trouvé.

```xml
<!-- Australia Drivers License Number -->
<Entity id="1cbbc8f5-9216-4392-9eb5-5ac2298d1356" patternsProximity="300" recommendedConfidence="75">
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_drivers_license_number" />
        <Match idRef="Keyword_australia_drivers_license_number" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_australia_drivers_license_number_exclusions" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_australia_drivers_license_number"></a>Keyword_australia_drivers_license_number

- permis de conduite internationaux
- australian automobile association
- permis de conduite international
- DriverLicence
- DriverLicences
- Permis conduire
- Permis de conduire
- Permis de conduire
- DriversLic
- DriversLicence
- DriversLicences
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Driver’Lic
- Driver’Lics
- Permis de conduire
- Permis de conduire
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Driver’sLic
- Driver’sLics
- Driver’sLicence
- Driver’sLicences
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- DriverLic #
- DriverLics #
- DriverLicence #
- DriverLicences #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- DriversLic #
- DriversLics #
- DriversLicence #
- DriversLicences #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- Driver’Lic #
- Driver’Lics #
- Permis de conduire #
- Permis de conduire #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- Driver’sLic #
- Driver’sLics #
- Driver’sLicence #
- Driver’sLicences #
- #Permisconduire
- #Permisconduire
- #Permis de conduire
- #Permis de conduire

#### <a name="keyword_australia_drivers_license_number_exclusions"></a>Keyword_australia_drivers_license_number_exclusions

- aaa
- DriverLicense
- DriverLicenses
- Permis de conduire
- Permis de conduire
- DriversLicense
- DriversLicenses
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Driver’sLicense
- Driver’sLicenses
- Permis de conduire
- Driver’s Licenses
- DriverLicense #
- DriverLicenses #
- #Permis de conduire
- #Permis de conduire
- DriversLicense #
- DriversLicenses #
- #Permis de conduire
- #Permis de conduire
- Permis de conduire #
- Permis de conduire #
- #Permis de conduire
- #Permis de conduire
- Driver’sLicense #
- Driver’sLicenses #
- #Permis de conduire
- #Permis de conduire

## <a name="australia-medical-account-number"></a>Numéro de compte médical australie

### <a name="format"></a>Format

10 à 11 chiffres

### <a name="pattern"></a>Modèle

10 à 11 chiffres :
- Le premier chiffre est compris entre 2 et 6
- Le neuvième chiffre est un chiffre de contrôle
- Le dixième chiffre est le chiffre d’émission
- Le onzième chiffre (facultatif) est le numéro individuel

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_australian_medical_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_Australia_Medical_Account_Number est trouvé.
- La somme de contrôle est correcte.


```xml
  <!-- Australia Medical Account Number -->
<Entity id="104a99a0-3d3b-4542-a40d-ab0b9e1efe63" recommendedConfidence="85" patternsProximity="300">
    <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_australian_medical_account_number"/>
     <Match idRef="Keyword_Australia_Medical_Account_Number"/>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_australia_medical_account_number"></a>Keyword_Australia_Medical_Account_Number

- informations sur le compte bancaire
- remboursements d’assurance maladie
- compte de prêts immobiliers
- paiements bancaires
- direction de l’information
- prêt sur carte de crédit
- département des services sociaux
- service local
- sous-programme


## <a name="australia-passport-number"></a>Numéro de passeport australien

### <a name="format"></a>Format

huit ou neuf caractères alphanumériques

### <a name="pattern"></a>Modèle

- une lettre (N, E, D, F, A, C, U, X) suivie de sept chiffres ou
- Deux lettres (PA, PB, PC, PD, PE, PF, PU, PW, PX, PZ) suivies de sept chiffres.

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_australia_passport_number` régulière trouve un contenu qui correspond au modèle.
- Un mot clé est `Keyword_australia_passport_number` trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_australia_passport_number` régulière trouve un contenu qui correspond au modèle.

```xml
    <!-- Australia Passport Number -->
    <Entity id="29869db6-602d-4853-ab93-3484f905df50" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_passport_number" />
        <Match idRef="Keyword_australia_passport_number" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_australia_passport_number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport
- informations sur le passeport
- immigration et citoyenneté
- Australie
- service de l’immigration
- Carte nationale d’identité
- document de voyage
- autorité émettrice


## <a name="australia-tax-file-number"></a>Numéro de fichier fiscal australien

### <a name="format"></a>Format

huit à neuf chiffres

### <a name="pattern"></a>Modèle

De huit à neuf chiffres sont généralement présentés avec des espaces comme suit :
- trois chiffres
- espace facultatif
- trois chiffres
- espace facultatif
- deux à trois chiffres où le dernier chiffre est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_australian_tax_file_number trouve un contenu qui correspond au modèle.
- Aucun mot clé figurant dans la liste Keyword_Australia_Tax_File_Number ou Keyword_number_exclusions n’est trouvé.
- La somme de contrôle est correcte.

```xml
   <!-- Australia Tax File Number -->
    <Entity id="e29bc95f-ff70-4a37-aa01-04d17360a4c5" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_australian_tax_file_number" />
        <Match idRef="Keyword_Australia_Tax_File_Number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_australia_tax_file_number"></a>Keyword_australia_tax_file_number

- numéro d’entreprise australien
- taux d’imposition marginale
- prélèvement d’assurance maladie
- numéro de portefeuille
- service des vétérans
- retenue à la source
- déclaration d’impôts individuels
- numéro de dossier fiscal
- tfn

## <a name="austria-drivers-license-number"></a>Numéro de permis de conduire autrichen

### <a name="format"></a>Format

huit chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression  `Regex_austria_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_austria_eu_driver's_license_number` est trouvé.

```xml
      <!-- Austria Driver's License Number -->
      <Entity id="682f18ce-44eb-482b-8198-2bcb96a0761e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_austria_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_austria_eu_drivers_license_number"></a>Keywords_austria_eu_driver’s_license_number

- fuhrerschein
- führerschein
- Führerscheine
- Führerscheinnummer
- Führerscheinnummern

## <a name="austria-identity-card"></a>Carte d’identité Autriche
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Combinaison de 24 caractères de lettres, chiffres et caractères spéciaux

### <a name="pattern"></a>Modèle

24 caractères :

-  22 lettres (ne sensibles pas à la majuscule), chiffres, barres obliques inverses, barres obliques ou signes plus

- deux lettres (ne sont pas sensibles à la majuscule), des chiffres, des barres obliques inverses, des barres obliques, des signes plus ou des signes égaux

### <a name="checksum"></a>Somme de contrôle

Non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression  `Regex_austria_eu_national_id_card` régulière trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_austria_eu_national_id_card` trouvé.

```xml
      <!-- Austria Identity Card -->
      <Entity id="5ec06c3b-007e-4820-8343-7ff73b889735" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_national_id_card" />
          <Match idRef="Keywords_austria_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_austria_eu_national_id_card"></a>Keywords_austria_eu_national_id_card

- numéro d’identité
- id national
- personalausliks republik österreich

## <a name="austria-passport-number"></a>Numéro de passeport autrichen

### <a name="format"></a>Format

Une lettre suivie d’un espace facultatif et de sept chiffres

### <a name="pattern"></a>Modèle

Combinaison d’une lettre, de sept chiffres et d’un espace :

- une lettre (ne doit pas être sensible à la cas)
- un espace (facultatif)
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_austria_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_austria_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière trouve la date au format DD.MM.YYYY ou dans laquelle un mot clé est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_austria_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_austria_eu_passport_number` est trouvé.

```xml
      <!-- Austria Passport Number -->
      <Entity id="1c96ae4e-303b-447d-86c7-77113ac266bf" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_austria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_austria_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_austria_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_austria_eu_passport_number"></a>Keywords_austria_eu_passport_number

- reisepassnummer
- reisepasse
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration

## <a name="austria-social-security-number"></a>Numéro de sécurité sociale autrichen

### <a name="format"></a>Format

10 chiffres au format spécifié

### <a name="pattern"></a>Modèle

10 chiffres :

- trois chiffres qui correspondent à un numéro de série
- un chiffre de vérification
- six chiffres qui correspondent à la date de naissance (DDMMYY)

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_austria_eu_ssn_or_equivalent` trouve un contenu qui correspond au modèle.
- un mot clé  `Keywords_austria_eu_ssn_or_equivalent` est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_austria_eu_ssn_or_equivalent` trouve un contenu qui correspond au modèle.

```xml
      <!-- Austria Social Security Number -->
      <Entity id="6896a906-86c9-4d19-a2da-6e43ccd19b7b" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_austria_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_austria_eu_telephone_number" />
            <Match idRef="Keywords_austria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_austria_eu_ssn_or_equivalent"></a>Keywords_austria_eu_ssn_or_equivalent

- ssn de l’équipe de police
- nombre ehic
- ehic no
- code d’assurance
- insurancecode #
- numéro d’assurance
- n’assurance
- krankenkassennummer
- krankenversiche sous
- socialsecurityno
- socialsecurityno #
- non de sécurité sociale
- numéro de sécurité sociale
- code de sécurité sociale
- sozialversicheyousnummer
- sozialversicheyousnummer #
- soziale sicherheit kein
- sozialesicherheitkein #
- ssn #
- ssn
- versicheicheichescode
- versicheicheichesnummer
- zdravstveno zavarovanje

## <a name="austria-tax-identification-number"></a>Numéro d’identification fiscale autrichen

### <a name="format"></a>Format

neuf chiffres avec trait d’union facultatif et barre oblique

### <a name="pattern"></a>Modèle

neuf chiffres avec trait d’union facultatif et barre oblique :

- deux chiffres
- un trait d’union (facultatif) ;
- trois chiffres
- barre oblique (facultative)
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_austria_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_austria_eu_tax_file_number` trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_austria_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Austria Tax Identification Number -->
      <Entity id="4fd58d22-af28-4451-b18a-6f722430a56d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_tax_file_number" />
          <Match idRef="Keywords_austria_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_austria_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_austria_eu_tax_file_number"></a>Keywords_austria_eu_tax_file_number

- österreich
- st.nr.
- steuernummer
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #
- numéro de taxe

## <a name="austria-value-added-tax"></a>Taxe sur la valeur ajoutée en Autriche
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Modèle alphanumérique de 11 caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique de 11 caractères :

- A ou a
- T ou t
- Espace facultatif
- U ou u
- espace facultatif
- deux ou trois chiffres
- espace facultatif
- quatre chiffres
- espace facultatif
- un ou deux chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_Austria_Value_Added_Tax trouve un contenu qui correspond au modèle.
- Un mot clé de Keyword_Austria_Value_Added_Tax est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_Austria_Value_Added_Tax trouve un contenu qui correspond au modèle.

```xml
      <!-- Austria Value Added Tax -->
      <Entity id="b6a3eda2-c56c-4b69-a5f7-dca34db00f48" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
          <Match idRef="Keyword_Austria_Value_Added_Tax" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keyword_austria_value_added_tax"></a>Keyword_austria_value_added_tax

- numéro de tva
- vat #
- numéro de tva de tva
- vat no.
- vatno #
- numéro de taxe sur la valeur ajoutée
- tva de tva de tva
- mwst
- umsatzsteuernummer
- mwstnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- numéro d’identification de tva
- nombre atu
- numéro uid


## <a name="azure-documentdb-auth-key"></a>Clé d’th azure DocumentDB

### <a name="format"></a>Format

Chaîne « DocumentDb » suivie des caractères et des chaînes indiqués dans le modèle ci-dessous.

### <a name="pattern"></a>Modèle

- Chaîne « DocumentDb »
- Toute combinaison de 3 à 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- Supérieur au symbole (>), signe égal (=), guillemets (« ) ou apostrophe (')
- Toute combinaison de 86 lettres minuscules ou majuscules, chiffres, barre oblique (/) ou signe plus (+)
- Deux signes égaux (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureDocumentDBAuthKey trouve un contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords trouve pas de contenu qui correspond au modèle.

```xml
<!-- Azure Document DB Auth Key -->
<Entity id="0f587d92-eb28-44a9-bd1c-90f2892b47aa" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureDocumentDBAuthKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
          </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- fabrikam
- northwind
- sandbox
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net

## <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>Chaîne de connexion de base de données IAAS Azure et chaîne de connexion SQL azure

### <a name="format"></a>Format

Chaîne « Serveur », « serveur » ou « source de données » suivie des caractères et des chaînes indiqués dans le modèle ci-dessous, y compris la chaîne « cloudapp.azure ».<!--no-hyperlink-->com » ou « cloudapp.azure.<!--no-hyperlink-->net » ou « database.windows .<!--no-hyperlink-->et la chaîne « Password », « password » ou « pwd ».

### <a name="pattern"></a>Modèle

- chaîne « Serveur », « serveur » ou « source de données »
- de zéro à deux caractères d’espace blanc
- signe égal (=)
- de zéro à deux caractères d’espace blanc
- toute combinaison de 1 à 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- La chaîne « cloudapp.azure.<!--no-hyperlink-->com », « cloudapp.azure.<!--no-hyperlink-->« database.windows ».<!--no-hyperlink-->net »
- toute combinaison de 1 à 300 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- la chaîne « Password », « password » ou « pwd »
- de zéro à deux caractères d’espace blanc
- signe égal (=)
- de zéro à deux caractères d’espace blanc
- un ou plusieurs caractères qui ne sont pas des points-virgules (;), guillemets (« ), ou apostrophe (')
- point-virgule (;), guillemets (« ), ou apostrophe (')

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureConnectionString trouve un contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords trouve pas de contenu qui correspond au modèle.

```xml
<!--Azure IAAS Database Connection String and Azure SQL Connection String-->
<Entity id="ce1a126d-186f-4700-8c0c-486157b953fd" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- fabrikam
- northwind
- sandbox
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net

## <a name="azure-iot-connection-string"></a>Azure IoT de connexion

### <a name="format"></a>Format

Chaîne « HostName » suivie des caractères et des chaînes décrits dans le modèle ci-dessous, y compris les chaînes « azure-devices ».<!--no-hyperlink-->net » et « SharedAccessKey ».

### <a name="pattern"></a>Modèle

- la chaîne « HostName »
- de zéro à deux caractères d’espace blanc
- signe égal (=)
- de zéro à deux caractères d’espace blanc
- toute combinaison de 1 à 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- la chaîne « azure-devices.<!--no-hyperlink-->net »
- toute combinaison de 1 à 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- la chaîne « SharedAccessKey »
- de zéro à deux caractères d’espace blanc
- signe égal (=)
- de zéro à deux caractères d’espace blanc
- toute combinaison de 43 lettres minuscules ou majuscules, chiffres, barre oblique (/) ou signe plus (+)
- signe égal (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureIoTConnectionString trouve un contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords trouve pas de contenu qui correspond au modèle.

```xml
<!--Azure IoT Connection String-->
<Entity id="0b34bec3-d5d6-4974-b7b0-dcdb5c90c29d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureIoTConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- fabrikam
- northwind
- sandbox
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net

## <a name="azure-publish-setting-password"></a>Mot de passe de paramètre de publication Azure

### <a name="format"></a>Format

Chaîne « userpwd= » suivie d’une chaîne alphanumérique.

### <a name="pattern"></a>Modèle

- la chaîne « userpwd= »
- toute combinaison de 60 lettres minuscules ou chiffres
- guillemets (« )

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzurePublishSettingPasswords trouve un contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords trouve pas de contenu qui correspond au modèle.


```xml
<!--Azure Publish Setting Password-->
<Entity id="75f4cc8a-a68e-49e5-89ce-fa8f03d286a5" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
       <IdMatch idRef="CEP_Regex_AzurePublishSettingPasswords" />
       <Any minMatches="0" maxMatches="0">
           <Match idRef="CEP_CommonExampleKeywords" />
       </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- fabrikam
- northwind
- sandbox
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net

## <a name="azure-redis-cache-connection-string"></a>Chaîne de connexion au cache Azure Redis

### <a name="format"></a>Format

La chaîne « redis.cache.windows.<!--no-hyperlink-->« net » suivi des caractères et des chaînes décrits dans le modèle ci-dessous, y compris la chaîne « password » ou « pwd ».

### <a name="pattern"></a>Modèle

- la chaîne « redis.cache.windows.<!--no-hyperlink-->net »
- toute combinaison de 1 à 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- la chaîne « password » ou « pwd »
- de zéro à deux caractères d’espace blanc
- signe égal (=)
- de zéro à deux caractères d’espace blanc
- toute combinaison de 43 caractères qui sont des lettres minuscules ou majuscules, des chiffres, une barre oblique (/) ou un signe plus (+)
- signe égal (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureRedisCacheConnectionString trouve un contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords trouve pas de contenu qui correspond au modèle.

```xml
<!--Azure Redis Cache Connection String-->
<Entity id="095a7e6c-efd8-46d5-af7b-5298d53a49fc" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureRedisCacheConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- fabrikam
- northwind
- sandbox
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net

## <a name="azure-sas"></a>Azure SAS

### <a name="format"></a>Format

Chaîne « sig » suivie des caractères et des chaînes décrits dans le modèle ci-dessous.

### <a name="pattern"></a>Modèle

- la chaîne « sig »
- de zéro à deux caractères d’espace blanc
- signe égal (=)
- de zéro à deux caractères d’espace blanc
- toute combinaison de 43 à 53 caractères qui sont des lettres minuscules ou majuscules, des chiffres ou le signe pourcentage (%)
- la chaîne « %3d »
- tout caractère qui n’est pas une lettre minuscule ou minuscule, un chiffre ou un signe pourcentage (%)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureSAS trouve un contenu qui correspond au modèle.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```

## <a name="azure-service-bus-connection-string"></a>Chaîne de connexion azure service bus

### <a name="format"></a>Format

Chaîne « EndPoint » suivie des caractères et des chaînes indiqués dans le modèle ci-dessous, y compris les chaînes « servicebus.windows ».<!--no-hyperlink-->net » et « SharedAccesKey ».

### <a name="pattern"></a>Modèle

- la chaîne « EndPoint »
- de zéro à deux caractères d’espace blanc
- signe égal (=)
- de zéro à deux caractères d’espace blanc
- toute combinaison de 1 à 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- la chaîne « servicebus.windows.<!--no-hyperlink-->net »
- toute combinaison de 1 à 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- la chaîne « SharedAccessKey »
- de zéro à deux caractères d’espace blanc
- signe égal (=)
- de zéro à deux caractères d’espace blanc
- toute combinaison de 43 caractères qui sont des lettres minuscules ou majuscules, des chiffres, une barre oblique (/) ou un signe plus (+)
- signe égal (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureServiceBusConnectionString trouve un contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords trouve pas de contenu qui correspond au modèle.

```xml
<!--Azure Service Bus Connection String-->
<Entity id="b9a6578f-a83f-4fcd-bf44-2130bae49a6f" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureServiceBusConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- fabrikam
- northwind
- sandbox
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net

## <a name="azure-storage-account-key"></a>Clé de compte de stockage Azure

### <a name="format"></a>Format

Chaîne « DefaultEndpointsProtocol » suivie des caractères et des chaînes indiqués dans le modèle ci-dessous, y compris la chaîne « AccountKey ».

### <a name="pattern"></a>Modèle

- la chaîne « DefaultEndpointsProtocol »
- de zéro à deux caractères d’espace blanc
- signe égal (=)
- de zéro à deux caractères d’espace blanc
- toute combinaison de 1 à 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- la chaîne « AccountKey »
- de zéro à deux caractères d’espace blanc
- signe égal (=)
- de zéro à deux caractères d’espace blanc
- toute combinaison de 86 caractères qui sont des lettres minuscules ou majuscules, des chiffres, une barre oblique (/) ou un signe plus (+)
- deux signes égaux (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureStorageAccountKey trouve un contenu qui correspond au modèle.
- L’expression régulière CEP_AzureEmulatorStorageAccountFilter trouve pas de contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords trouve pas de contenu qui correspond au modèle.

```xml
<!--Azure Storage Account Key-->
<Entity id="c7bc98e8-551a-4c35-a92d-d2c8cda714a7" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_AzureEmulatorStorageAccountFilter" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="cep_azure_emulator_storage_account_filter"></a>CEP_azure_emulator_storage_account_filter

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- Eby8vdM02xNOotteFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- fabrikam
- northwind
- sandbox
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net

## <a name="azure-storage-account-key-generic"></a>stockage Azure de compte d’utilisateur (générique)

### <a name="format"></a>Format

Toute combinaison de 86 lettres minuscules ou majuscules, chiffres, barre oblique (/) ou signe plus (+), précédé ou suivi des caractères indiqués dans le modèle ci-dessous.

### <a name="pattern"></a>Modèle

- zéro à l’un des symboles supérieurs (>), apostrophe ('), signe égal (=), guillemets (« ), ou di diétique (#)
- toute combinaison de 86 caractères qui sont des lettres minuscules ou majuscules, des chiffres, la barre oblique (/) ou le signe plus (+)
- deux signes égaux (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureStorageAccountKeyGeneric trouve un contenu qui correspond au modèle.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```
## <a name="belgium-drivers-license-number"></a>Numéro de permis de conduire belgique

### <a name="format"></a>Format

10 chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

10 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_belgium_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir `Keywords_eu_driver's_license_number` de ou `Keywords_belgium_eu_driver's_license_number` est trouvé.

```xml
      <!-- Belgium Driver's License Number -->
      <Entity id="d89fd329-9324-433c-b687-2c37bd5166f3" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_belgium_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_belgium_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés


#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_belgium_eu_drivers_license_number"></a>Keywords_belgium_eu_driver’s_license_number

- rijbewijs
- rijbewijsnummer
- führerschein
- führerscheinnummer
- füehrerscheinnummer
- fuhrerschein
- fuehrerschein
- fuhrerscheinnummer
- fuehrerscheinnummer
- permis de conduire
- numéro permis conduire


## <a name="belgium-national-number"></a>Numéro national belgique

### <a name="format"></a>Format

11 chiffres plus des délimiteur facultatifs

### <a name="pattern"></a>Modèle

11 chiffres plus des délimiteurs :
- six chiffres et deux points facultatifs au format AA. MM.DD pour la date de naissance
- Délimiteur facultatif de point, tiret, espace
- trois chiffres séquentiels (impair pour les hommes, même pour les femme)
- Délimiteur facultatif de point, tiret, espace
- deux chiffres de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_belgium_national_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_belgium_national_number est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_belgium_national_number trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Belgium National Number -->
       <Entity id="fb969c9e-0fd1-4b18-8091-a2123c5e6a54" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_national_number" />
          <Match idRef="Keyword_belgium_national_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_belgium_national_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_belgium_national_number"></a>Keyword_belgium_national_number

- belasting aantal
- bnn #
- bnn
- carte d’identité
- identifiant national
- identifiantnational #
- identificatie
- identification
- identifikation
- identifikationsnummer
- identifizierung
- identité
- identiteit
- identiteitskaart
- identity
- inscription
- numéro national
- registre national
- nationalnumber #
- nationalnumber
- nif #
- nif
- numéro d’assuré
- numéro de registre national
- numéro de sécurité
- numéro d’identification
- numéro d’immatriculation
- numéro national
- numéronational #
- numéro d’ID personnel
- personalausweis
- personalidnumber #
- registratie
- registration
- registrationsnumme
- registrierung
- numéro de sécurité sociale
- ssn #
- ssn
- steuernummer
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #

## <a name="belgium-passport-number"></a>Numéro de passeport belgique

### <a name="format"></a>Format

deux lettres suivies de six chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

deux lettres suivies de six chiffres

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

 Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_belgium_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_belgium_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date2` régulière trouve la date au format JA J.-C. J.-C. ou un mot clé de ou est `Keywords_eu_passport_date` `Keywords_belgium_eu_passport_number` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_belgium_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_belgium_eu_passport_number` est trouvé.

```xml
      <!-- Belgium Passport Number -->
      <Entity id="d7b1315b-21ca-4774-a32a-596010ff78fd" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date2" />
            <Match idRef="Keywords_eu_passport_date" />
            <Match idRef="Keywords_belgium_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_belgium_eu_passport_number"></a>Keywords_belgium_eu_passport_number

- numéro passeport
- paspoort nr
- paspoort-nr
- paspoortnummer
- paspoortnummers
- Passeport carte
- Passeport livre
- Pass-Nr
- Passnummer
- reisepass kein

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date d’émission
- date d’expiration

## <a name="belgium-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée en Belgique
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Modèle alphanumérique de 12 caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique de 12 caractères :

- une lettre B ou b
- une lettre E ou e
- un chiffre 0
- un chiffre de 1 à 9
- point ou tiret ou espace facultatif
- quatre chiffres
- point ou tiret ou espace facultatif
- quatre chiffres


### <a name="checksum"></a>Somme de contrôle

Oui


### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_belgium_value_added_tax_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_belgium_value_added_tax_number est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_belgium_value_added_tax_number trouve un contenu qui correspond au modèle.

```xml
      <!-- Belgium Value Added Tax Number -->
      <Entity id="85b5b3c3-f2de-4ae8-ac46-fd3cb38bf9ed" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_belgium_value_added_tax_number" />
          <Match idRef="Keywords_belgium_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_value_added_tax_number" />
        </Pattern>
      </Entity>
    </Version>
```
### <a name="keywords"></a>Mots clés

#### <a name="keyword_belgium_value_added_tax_number"></a>Keyword_belgium_value_added_tax_number

- nº tva
- numéro de tva
- vat no
- numéro t.v.a
- umsatzsteuer-identifikationsnummer
- umsatzsteuernummer
- btw
- btw #
- vat #


## <a name="brazil-cpf-number"></a>Numéro CPF Brésil

### <a name="format"></a>Format

11 chiffres qui incluent un chiffre de contrôle et peuvent ou non être mis en forme 

### <a name="pattern"></a>Modèle

Mise en forme :
- trois chiffres
- un point
- trois chiffres
- un point
- trois chiffres
- un trait d’union
- deux chiffres qui sont des chiffres de vérification

Non formaté :
- 11 chiffres où les deux derniers sont des chiffres de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_brazil_cpf trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_brazil_cpf est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_brazil_cpf trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Brazil CPF Number -->
<Entity id="78e09124-f2c3-4656-b32a-c1a132cd2711" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cpf"/>
     <Match idRef="Keyword_brazil_cpf"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cpf"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_brazil_cpf"></a>Keyword_brazil_cpf

- CPF
- Identification
- Inscription
- Chiffre d’affaires
- Cadastro de Pessoas Físicas
- Impossibilitéto
- Identificação
- Inscrição
- Receita


## <a name="brazil-legal-entity-number-cnpj"></a>Numéro d’entité juridique brésil (CNPJ)

### <a name="format"></a>Format

14 chiffres qui incluent un numéro d’enregistrement, un numéro de succursale et des chiffres de contrôle, avec des délimiteurs en plus

### <a name="pattern"></a>Modèle

14 chiffres plus des délimiteurs :

- deux chiffres
- un point
- trois chiffres
- un point
- trois chiffres (ces huit premiers chiffres sont le numéro d’inscription)
- barre oblique
- Numéro de succursale à quatre chiffres
- un trait d’union
- deux chiffres qui sont des chiffres de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_brazil_cnpj trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_brazil_cnpj est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_brazil_cnpj trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Brazil Legal Entity Number (CNPJ) -->
<Entity id="9b58b5cd-5e90-4df6-b34f-1ebcc88ceae4" recommendedConfidence="85" patternsProximity="300">
   <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cnpj"/>
     <Match idRef="Keyword_brazil_cnpj"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cnpj"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_brazil_cnpj"></a>Keyword_brazil_cnpj

- CNPJ
- CNPJ/MF
- CNPJ-MF
- National Registry of Legal Entities
- Taxpayers Registry
- Legal entity
- Legal entities
- Registration Status
- Professionnel
- Company
- CNPJ
- Cadastro Nacional da Pessoa Jurídica
- Cadastro Geral de Contribuintes
- CGC
- Pessoa jurídica
- Pessoas jurídicas
- Situação cadastral
- Inscrição
- Empresa


## <a name="brazil-national-identification-card-rg"></a>Carte d’identification nationale (RG) brésil

### <a name="format"></a>Format

Registro Geral (ancien format) : neuf chiffres

Registro de Identidade (RIC) (nouveau format) : 11 chiffres

### <a name="pattern"></a>Modèle

Registro Geral (ancien format) :
- deux chiffres
- un point
- trois chiffres
- un point
- trois chiffres
- un trait d’union
- un chiffre qui est un chiffre de vérification

Registro de Identidade (RIC) (nouveau format) :
- 10 chiffres
- un trait d’union
- un chiffre qui est un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_brazil_rg trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_brazil_rg est trouvé.
- La somme de contrôle est correcte.


```xml
      <!-- Brazil National ID Card (RG) -->
      <Entity id="486de900-db70-41b3-a886-abdf25af119c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_brazil_rg" />
          <Match idRef="Keyword_brazil_rg" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

- Cédula de identidade
- Carte d’identité
- id national
- Número de registro
- Registro de Identidade
- Registro Geral
- RG (ce mot clé est sensible à la cas)
- RIC (ce mot clé est sensible à la cas)


## <a name="bulgaria-drivers-license-number"></a>Numéro de permis de conduire bulgare

### <a name="format"></a>Format

neuf chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_bulgaria_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_bulgaria_eu_driver's_license_number` est trouvé.

```xml
      <!-- Bulgaria Driver's License Number -->
      <Entity id="66d39258-94c2-43b2-804b-aa312258e54b" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_bulgaria_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_bulgaria_eu_drivers_license_number"></a>Keywords_bulgaria_eu_driver’s_license_number

- свидетелство за управление на мпс
- свидетелство за управление на моторно превозно средство
- сумпс
- шофьорска книжка
- шофьорски книжки

## <a name="bulgaria-uniform-civil-number"></a>Numéro civile uniforme bulgare
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

10 chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

10 chiffres sans espaces et délimiteur

- six chiffres qui correspondent à la date de naissance (AAMMMMDD)
- deux chiffres qui correspondent à l’ordre de naissance
- un chiffre qui correspond au sexe : un chiffre pair pour l’homme et un chiffre impair pour la femme
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_bulgaria_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_bulgaria_eu_national_id_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_bulgaria_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Bulgaria Uniform Civil Number -->
      <Entity id="100d58b1-0a35-4fb1-aa89-e4a86fb53fcc" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Match idRef="Keywords_bulgaria_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_bulgaria_eu_telephone_number" />
            <Match idRef="Keywords_bulgaria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_bulgaria_eu_national_id_card"></a>Keywords_bulgaria_eu_national_id_card

- bnn #
- bnn
- l’équipe de l’équipe #
- l’équipe de l’équipe
- edinen edinen edinenhdanski nomer
- egn #
- egn
- numéro d’identification
- id national
- numéro national
- nationalnumber #
- nationalnumber
- id personnel
- non personnel
- numéro personnel
- personalidnumber #
- numéro de sécurité sociale
- ssn #
- ssn
- id civile uniforme
- non civile uniforme
- numéro civile uniforme
- uniformcivilno #
- uniformcivilno
- uniformcivilnumber #
- uniformcivilnumber
- numéro unique de la nationalité
- егн #
- егн
- единен граждански номер
- идентификационен номер
- личен номер
- лична идентификация
- лично не
- национален номер
- номер на гражданството
- униформ id
- униформ граждански id
- униформ граждански не
- униформ граждански номер
- униформгражданскиid #
- униформгражданскине. #


## <a name="bulgaria-passport-number"></a>Numéro de passeport bulgare

### <a name="format"></a>Format

neuf chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_bulgaria_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_bulgaria_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière trouve la date au format DD.MM.YYYY ou dans laquelle un mot clé est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_bulgaria_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_bulgaria_eu_passport_number` est trouvé.

```xml
      <!-- Bulgaria Passport Number -->
      <Entity id="f7172b82-c588-4216-845e-4e54e397f29a" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_bulgaria_eu_passport_number"></a>Keywords_bulgaria_eu_passport_number

- номер на паспорта
- номер на паспорт
- паспорт No

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration

## <a name="canada-bank-account-number"></a>Numéro de compte bancaire canada

### <a name="format"></a>Format

7 ou 12 chiffres

### <a name="pattern"></a>Modèle

Un numéro de compte bancaire canadien est de 7 ou 12 chiffres.

Un numéro de transit de compte bancaire du Canada est indiqué au format suivant :
- cinq chiffres
- un trait d’union
- trois chiffres OU
- zéro « 0 »
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_canada_bank_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_canada_bank_account_number est trouvé.
- L’expression régulière Regex_canada_bank_account_transit_number trouve un contenu qui correspond au modèle.

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_canada_bank_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_canada_bank_account_number est trouvé.

```xml
<!-- Canada Bank Account Number -->
<Entity id="552e814c-cb50-4d94-bbaa-bb1d1ffb34de" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
        <Match idRef="Regex_canada_bank_account_transit_number" />
   </Pattern>
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_canada_bank_account_number"></a>Keyword_canada_bank_account_number

- obligations d’épargne du Canada
- agence du revenu du Canada
- institution financière du Canada
- formulaire de dépôt direct
- citoyen canadien
- représentant légal
- notaire
- commissaire à l’assermentation
- prestation pour la garde d’enfants
- prestation universelle pour la garde d’enfants
- prestation fiscale canadienne pour enfants
- prestation fiscale pour le revenu gagné
- taxe de vente harmonisée
- numéro d’assurance sociale
- remboursement d’impôt
- prestation fiscale pour enfants
- paiements aux territoires
- numéro d’institution
- demande de dépôt
- informations bancaires
- dépôt direct


## <a name="canada-drivers-license-number"></a>Numéro de permis de conduire canada

### <a name="format"></a>Format

Varie selon la province

### <a name="pattern"></a>Modèle

Différents modèles couvrent :
- Alberta
- Colombie-britannique
- Centre d’ment
- Nouveau-Brunswick
- France/Îles
- Nouvelle-Écosse
- Monde
- Île-du-Prince-Édouard
- Centre d’ment
- Centre d’ment

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_[province_name]_drivers_license_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_[province_name]_drivers_license_name est trouvé.
- Un mot clé figurant dans la liste Keyword_canada_drivers_license est trouvé.

```xml
<!-- Canada Driver's License Number -->
    <Entity id="37186abb-8e48-4800-ad3c-e3d1610b3db0" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_alberta_drivers_license_number" />
        <Match idRef="Keyword_alberta_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_british_columbia_drivers_license_number" />
        <Match idRef="Keyword_british_columbia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_manitoba_drivers_license_number" />
        <Match idRef="Keyword_manitoba_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_brunswick_drivers_license_number" />
        <Match idRef="Keyword_new_brunswick_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_newfoundland_labrador_drivers_license_number" />
        <Match idRef="Keyword_newfoundland_labrador_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_nova_scotia_drivers_license_number" />
        <Match idRef="Keyword_nova_scotia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_ontario_drivers_license_number" />
        <Match idRef="Keyword_ontario_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_prince_edward_island_drivers_license_number" />
        <Match idRef="Keyword_prince_edward_island_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_quebec_drivers_license_number" />
        <Match idRef="Keyword_quebec_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_saskatchewan_drivers_license_number" />
        <Match idRef="Keyword_saskatchewan_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_province_name_drivers_license_name"></a>Keyword_[province_name]_drivers_license_name

- L’abréviation de la province, par exemple AB
- Le nom de la province, par exemple Alberta

#### <a name="keyword_canada_drivers_license"></a>Keyword_canada_drivers_license

- DL
- DLS
- CDL
- CDLS
- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- DriverLicence
- DriverLicences
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- DriversLic
- DriversLics
- DriversLicence
- DriversLicences
- DriversLicense
- DriversLicenses
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Driver’Lic
- Driver’Lics
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Driver’sLic
- Driver’sLics
- Driver’sLicense
- Driver’sLicenses
- Driver’sLicence
- Driver’sLicences
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- id
- Ids
- numéro carte d’identification
- numéros carte d’identification
- # carte d’identification
- # carte d’identification
- carte d’identification
- cartes d’identification
- idcard
- numéro d’identification
- numéros d’identification
- # identification
- # identification
- carte d’identification
- cartes d’identification
- identification
- DL #
- DLS #
- CDL #
- CDLS #
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- DriverLicence #
- DriverLicences #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- DriversLic #
- DriversLics #
- DriversLicense #
- DriversLicenses #
- DriversLicence #
- DriversLicences #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- Driver’Lic #
- Driver’Lics #
- Permis de conduire #
- Permis de conduire #
- Permis de conduire #
- Permis de conduire #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- Driver’sLic #
- Driver’sLics #
- Driver’sLicense #
- Driver’sLicenses #
- Driver’sLicence #
- Driver’sLicences #
- #Permisconduire
- #Permisconduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- Permis de conduire #
- id #
- ids #
- #carte carte d’identification
- #cartes carte d’identification
- idcard #
- #carte d’identification
- #cartes d’identification
- identification #


## <a name="canada-health-service-number"></a>Numéro de service de santé canada

### <a name="format"></a>Format

 10 chiffres

### <a name="pattern"></a>Modèle

10 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_canada_health_service_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_canada_health_service_number est trouvé.

```xml
<!-- Canada Health Service Number -->
<Entity id="59c0bf39-7fab-482c-af25-00faa4384c94" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_health_service_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_health_service_number" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_canada_health_service_number"></a>Keyword_canada_health_service_number

- numéro d’assurance-maladie
- informations sur le patient
- services de santé
- services spécialisés
- accident automobile
- hôpital pour malades
- sous-traitant
- indemnisation des salariés
- disability


## <a name="canada-passport-number"></a>Numéro de passeport canada

### <a name="format"></a>Format

deux lettres majuscules suivies de six chiffres

### <a name="pattern"></a>Modèle

deux lettres majuscules suivies de six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_canada_passport_number trouve un contenu qui correspond au modèle.
- Un mot clé provenant Keyword_canada_passport_number ou Keyword_passport est trouvé.

```xml
<!-- Canada Passport Number -->
<Entity id="14d0db8b-498a-43ed-9fca-f6097ae687eb" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_passport_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_passport_number" />
          <Match idRef="Keyword_passport" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_canada_passport_number"></a>Keyword_canada_passport_number

- citoyenneté canadienne
- passeport canadien
- demande de passeport
- photos pour passeport
- traducteur agréé
- citoyens canadiens
- temps de traitement
- demande de renouvellement

#### <a name="keyword_passport"></a>Keyword_passport

- Numéro de passeport
- N° de passeport
- # Passeport
- Passport #
- PassportID
- Passportno
- passportnumber
- パスポート
- パスポート番号
- « ポ »
- パスポート＃
- Numéro de passeport
- Passeport n°
- Passeport numéro
- # Passeport
- Passeport #
- PasseportNon
- Passeportn °


## <a name="canada-personal-health-identification-number-phin"></a>Numéro d’identification de santé personnel (PHIN) canada

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_canada_phin trouve un contenu qui correspond au modèle.
- Au moins deux mots clés de Keyword_canada_phin ou Keyword_canada_provinces sont trouvés.

```xml
<!-- Canada PHIN -->
<Entity id="722e12ac-c89a-4ec8-a1b7-fea3469f89db" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_phin" />
        <Any minMatches="2">
          <Match idRef="Keyword_canada_phin" />
          <Match idRef="Keyword_canada_provinces" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_canada_phin"></a>Keyword_canada_phin

- numéro d’assurance sociale
- loi sur les renseignements médicaux
- renseignements relatifs à l’impôt sur le revenu
- santé Manitoba
- enregistrement aux services de santé
- achats de médicaments sur ordonnance
- admissibilité aux prestations
- santé personnelle
- procuration
- numéro d’enregistrement
- numéro d’assurance-maladie
- recommandation par le médecin
- professionnel de bien-être
- orientation d’un patient
- santé et bien-être

#### <a name="keyword_canada_provinces"></a>Keyword_canada_provinces

- Tyz
- Centre d’ment
- Territoires du Nord-Ouest
- Monde
- Colombie-britannique
- Alberta
- Centre d’ment
- Centre d’ment
- Tzé
- Terre-Neuve-et-Labrador
- Nouveau-Brunswick
- Nouvelle-Écosse
- Île-du-Prince-Édouard
- Canada


## <a name="canada-social-insurance-number"></a>Numéro d’assurance sociale canada

### <a name="format"></a>Format

neuf chiffres avec des traits d’union ou des espaces facultatifs

### <a name="pattern"></a>Modèle

Mise en forme :
- trois chiffres
- trait d’union ou espace
- trois chiffres
- trait d’union ou espace
- trois chiffres

Non formaté : neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_canadian_sin trouve un contenu qui correspond au modèle.
- Au moins deux des modèles suivants :
    - Un mot clé figurant dans la liste Keyword_sin est trouvé.
    - Un mot clé figurant dans la liste Keyword_sin_collaborative est trouvé.
    - La fonction Func_eu_date trouve une date au format correct.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_unformatted_canadian_sin trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_sin est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- Canada Social Insurance Number -->
<Entity id="a2f29c85-ecb8-4514-a610-364790c0773e" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_canadian_sin" />
        <Any minMatches="2">
          <Match idRef="Keyword_sin" />
          <Match idRef="Keyword_sin_collaborative" />
          <Match idRef="Func_eu_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_canadian_sin" />
        <Match idRef="Keyword_sin" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_sin"></a>Keyword_sin

- assoc
- assurance sociale
- numéro d’assurance sociale
- l’équipe de l
- ssn
- ssns
- sécurité sociale
- numéro d’assurance sociale
- numéro d’identification nationale
- id national
- sin #
- ass soc
- ass sociale

#### <a name="keyword_sin_collaborative"></a>Keyword_sin_collaborative

- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- DOB
- Birthdate
- Birthday
- Date of Birth


## <a name="chile-identity-card-number"></a>Numéro de carte d’identité Chili

### <a name="format"></a>Format

sept à huit chiffres plus des délimiteur d’un chiffre ou d’une lettre à cocher

### <a name="pattern"></a>Modèle

sept à huit chiffres plus des délimiteurs :
- un à deux chiffres
- une période facultative
- trois chiffres
- une période facultative
- trois chiffres
- un tiret
- un chiffre ou une lettre (ne sensible à la cas) qui est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_chile_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_chile_id_card est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_chile_id_card trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Chile Identity Card Number -->
<Entity id="4e979794-49a0-407e-a0b9-2c536937b925" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_chile_id_card"/>
     <Match idRef="Keyword_chile_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_chile_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_chile_id_card"></a>Keyword_chile_id_card

- butula de identidad
- identificación
- numéro d’identification nationale
- numéro d’identification nationale
- id national
- número de identificación nacional
- rol único nacional
- rol únicoio
- RUN
- LASER
- tarjeta de identificación
- Rol Unico Nacional
- Rol Unico Vaio
- RUN #
- LASER #
- nationaluniqueroleID #
- nacional identidad
- número identificación
- identidad número
- numero identificacion
- identidad numero
- Identité d’identité d’identité non.
- Numéro d’identité de l’identité de l'
- Identité d’identité d’identité d #
- Registre fiscal unique
- Rôle unique unique
- Rôle fiscal unique
- Numéro unique d’anniversaire
- Numéro national unique
- Rôle national unique
- Rôle national unique
- Chili identity no.
- Numéro d’identité Chili
- Identité chili #
- R.U.T
- R.U.N


## <a name="china-resident-identity-card-prc-number"></a>Numéro de carte d’identité résidente en Chine (RPC)

### <a name="format"></a>Format

18 chiffres

### <a name="pattern"></a>Modèle

18 chiffres :
- six chiffres qui sont un code d’adresse
- huit chiffres sous la forme YYYYMMDD, qui sont la date de naissance
- trois chiffres qui sont un code de commande
- un chiffre qui est un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_china_resident_id trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_china_resident_id est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_china_resident_id trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- China Resident Identity Card (PRC) Number -->
<Entity id="c92daa86-2d16-4871-901f-816b3f554fc1" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_china_resident_id"/>
     <Match idRef="Keyword_china_resident_id"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_china_resident_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

### <a name="keyword_china_resident_id"></a>Keyword_china_resident_id

- Resident Identity Card
- RPC
- National Identification Card
- 身份证
- 居民 身份证
- 居民身份证
- 鉴定
- 身分證
- 居民 身份證
- 鑑定


## <a name="credit-card-number"></a>Numéro de carte de crédit

### <a name="format"></a>Format

14 à 19 chiffres qui peuvent être mis en forme ou non mis en forme (ddddddd) et qui doivent réussir le test Luhn.

### <a name="pattern"></a>Modèle

Détecte les cartes de toutes les principales marques dans le monde, notamment Visa, MasterCard, Discover Card, JCB, American Express, cartes-anniversaire, cartes-mémoire, Rupay et China UnionPay.

### <a name="checksum"></a>Somme de contrôle

Oui, la vérification Luhn

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_credit_card trouve un contenu qui correspond au modèle.
- L’une des affirmations suivantes est vraie :
    - Un mot clé figurant dans la liste Keyword_cc_verification est trouvé.
    - Un mot clé figurant dans la liste Keyword_cc_name est trouvé.
    - La fonction Func_expiration_date trouve une date au format correct.
- La somme de contrôle est correcte.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_credit_card trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Credit Card Number -->
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_credit_card" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_cc_verification"></a>Keyword_cc_verification

- vérification de la carte
- numéro d’identification de la carte
- cvn
- nic
- cvc2
- cvv2
- pin block
- code de sécurité
- numéro de sécurité
- n° de sécurité
- numéro d’émission
- n° d’émission
- cryptogramme
- numéro de sécurité
- numéro de sécurité
- kreditkartenprüfnummer
- kreditkartenprufnummer
- prüfziffer
- prufziffer
- sicherheits Kode
- sicherheitscode
- sicherheitsnummer
- verfalldatum
- codice di verifica
- cod. sicurezza
- cod sicurezza
- n autorizzazione
- código
- codigo
- cod. seg
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- 
cód. Segurança
- cod. seguranca

- cod. segurança

- cód. seguranca
- cód segurança
- cod seguranca
- cod segurança
- cód seguranca
- número de verificação
- numero de verificacao
- ablauf
- gültig bis
- gültigkeitsdatum
- gultig bis
- gultigkeitsdatum
- scadenza
- data scad
- fecha de expiracion
- fecha de venc
- vencimiento
- válido hasta
- valido hasta
- vto
- data de expiração
- data de expiracao
- data em que expira
- validade
- valor
- vencimento
- transaction
- numéro de transaction
- numéro de référence
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

#### <a name="keyword_cc_name"></a>Keyword_cc_name

- amex
- american express
- americanexpress
- americano espresso
- Visa
- mastercard
- master card
- mc
- mastercards
- master cards
- diner’s Club
- diners club
- 2013
- discover
- discover card
- discovercard
- discover cards
- JCB
- BrandSmart
- japanese card bureau
- carte blanche
- carteblanche
- carte de crédit
- cc #
- cc#:
- date d’expiration
- date d’exp
- date d’expiration
- date d’expiration
- date d’exp
- date expiration
- carte bancaire
- carte bancaire
- numéro de carte
- num de carte
- cardnumber
- cardnumbers
- numéros de carte
- carte de crédit
- cartes de crédit
- cartes de crédit
- ccn
- titulaire de la carte
- cardholder
- titulaires de la carte
- cardholders
- carte de vérification
- checkcard
- cartes de vérification
- checkcards
- carte de débit
- debitcard
- cartes de débit
- debitcards
- carte de retrait
- atmcard
- cartes de retrait
- atmcards
- enroute
- en route
- type de carte
- Cardmember Acct
- compte cardmember
- Cardno
- Carte d’entreprise
- Cartes d’entreprise
- Type de carte
- numéro de compte de carte
- compte de membre de carte
- Cardmember Acct.
- n° carte
- carte non
- numéro de carte
- carte bancaire
- carte de crédit
- carte de credit
- numéro de carte
- numero de carte
- nº de la carte
- nº de carte
- kreditkarte
- 2013
- kartenber
- kartenbers
- kreditkartenhalber
- kreditkartendit
- kreditkartentyp
- eigentümername
- kartennr
- kartennummer
- kreditkartennummer
- kreditkarten-nummer
- Carta di credito
- Carta credito
- n. carta
- n carta
- nr. carta
- nr carta
- numero carta
- numero della carta
- numero di carta
- tarjeta credito
- tarjeta de credito
- tarjeta crédito
- tarjeta de crédito
- tarjeta de atm
- tarjeta atm
- tarjeta debito
- tarjeta de debito
- tarjeta débito
- tarjeta de débito
- nº de tarjeta
- non. de tarjeta
- no de tarjeta
- numero de tarjeta
- número de tarjeta
- tarjeta no
- tarjeta jetente
- cartão de crédito
- cartão de credito
- cartao de crédito
- cartao de credito
- cartão de débito
- cartao de débito
- cartão de debito
- cartao de debito
- débito automático
- debito automatico
- número do cartão
- numero do cartão
- número do cartao
- numero do cartao
- número de cartão
- numero de cartão
- número de cartao
- numero de cartao
- nº do cartão
- nº do cartao
- nº. do cartão
- no do cartão
- no do cartao
- non. do cartão
- no. do cartao

- rupay
- union pay
- unionpay
- l’équipe de l’équipe
- toys
- クレジットカード番号
- クレジットカードナンバー
- クレジットカード＃
- クレジットカード
- クレジット
- クレカ
- カード番号
- カードナンバー
- カード＃
- アメックス
- アメリカンエクスプレス
- アメリカン エクスプレス
- Visayーs
- Visa
- マスターカード
- マスター カード
- マスター
- ダイナースクラブ
- ダイナース クラブ
- ダイナース
- 有効期限
- 期限
- キャッシュカード
- キャッシュ カード
- カード名義人
- カードの名義人
- カードの名義
- デビット カード
- デビットカード
- 中国银联
- 银联



## <a name="croatia-drivers-license-number"></a>Numéro de permis de conduire croate

### <a name="format"></a>Format

huit chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression  `Regex_croatia_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir `Keywords_eu_driver's_license_number` de ou `Keywords_croatia_eu_driver's_license_number` est trouvé.

```xml
      <!-- Croatia Driver's License Number -->
      <Entity id="005b3ef1-47dd-4e68-bb02-c6db484d00f2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_croatia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_croatia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_croatia_eu_drivers_license_number"></a>Keywords_croatia_eu_driver’s_license_number

- vozačka dozvola
- vozačke dozvole


## <a name="croatia-identity-card-number"></a>Numéro de carte d’identité Croate
Cette entité est incluse dans le type d’informations sensibles Numéro d’identification national de l’UE. Il est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_croatia_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_croatia_id_card est trouvé.

```xml
<!--Croatia Identity Card Number-->
<Entity id="ff12f884-c20a-4189-b185-34c8e7258d47" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_croatia_id_card"/>
     <Match idRef="Keyword_croatia_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_croatia_id_card"></a>Keyword_croatia_id_card

- majstorski broj građana
- numéro de citoyen master
- nacionalni identifikacijski broj
- numéro d’identification nationale
- oib #
- oib
- osobna iskaznica
- osobni id
- osobni identifikacijski broj
- numéro d’identification personnel
- porezni broj
- porezni identifikacijski broj
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #


## <a name="croatia-passport-number"></a>Numéro de passeport croate

### <a name="format"></a>Format

neuf chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_croatia_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_croatia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière trouve la date au format DD.MM.YYYY ou un mot clé à partir de laquelle est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_croatia_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_croatia_eu_passport_number` est trouvé.

```xml
      <!-- Croatia Passport Number -->
      <Entity id="7d7a729d-32d8-4204-8d01-d5e6a6c25581" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_croatia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_croatia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_croatia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_croatia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_croatia_eu_passport_number"></a>Keywords_croatia_eu_passport_number

- broj putovnice
- br. Putovnice
- br putovnice

## <a name="croatia-personal-identification-oib-number"></a>Numéro d’identification personnelle (OIB) croate

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres :
- 10 chiffres
- le chiffre final est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_croatia_oib_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_croatia_eu_tax_file_number est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_croatia_oib_number trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
      <!-- Croatia Personal Identification (OIB) Number -->
      <Entity id="31983b6d-db95-4eb2-a630-b44bd091968d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_croatia_oib_number" />
          <Match idRef="Keywords_croatia_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_croatia_oib_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_croatia_oib_number"></a>Keyword_croatia_oib_number

- majstorski broj građana
- numéro de citoyen master
- nacionalni identifikacijski broj
- numéro d’identification nationale
- oib #
- oib
- osobna iskaznica
- osobni id
- osobni identifikacijski broj
- numéro d’identification personnel
- porezni broj
- porezni identifikacijski broj
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #

## <a name="cyprus-drivers-license-number"></a>Numéro de permis de conduire à Chypre

### <a name="format"></a>Format

12 chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

12 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_cyprus_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_cyprus_eu_driver's_license_number` est trouvé.

```xml
      <!-- Cyprus Driver's License Number -->
      <Entity id="356fa104-f9ac-4aff-a0e4-2e6e65ea06c4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_cyprus_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- permis de conduire
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_cyprus_eu_drivers_license_number"></a>Keywords_cyprus_eu_driver’s_license_number

- άδεια οδήγησης
- αριθμό άδειας οδήγησης
- άδειες οδήγησης


## <a name="cyprus-identity-card"></a>Carte d’identité Chypre
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

10 chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

10 chiffres

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_cyprus_eu_national_id_card` régulière trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_cyprus_eu_national_id_card` trouvé.

```xml
      <!-- Cyprus Identity Card -->
      <Entity id="3ba8afe5-7a6c-4929-8247-0001b6878438" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_national_id_card" />
          <Match idRef="Keywords_cyprus_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_cyprus_eu_national_id_card"></a>Keywords_cyprus_eu_national_id_card

- numéro de carte d’identité
- numéro de carte d’identité
- kimliksi
- numéro d’identification nationale
- numéro d’ID personnel
- ταυτοτητασ


## <a name="cyprus-passport-number"></a>Numéro de passeport à Chypre

### <a name="format"></a>Format

une lettre suivie de 6 à 8 chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

une lettre suivie de six à huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_cyprus_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_cyprus_eu_passport_number` est trouvé.
- L’expression `Regex_cyprus_eu_passport_date` régulière trouve la date au format JD/MM/AAA OU un mot clé à partir de laquelle est `Keywords_cyprus_eu_passport_date` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_cyprus_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_cyprus_eu_passport_number` est trouvé.

```xml
      <!-- Cyprus Passport Number -->
      <Entity id="9193e2e8-7f8c-43c1-a274-ac40d651936f" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_cyprus_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_cyprus_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_cyprus_eu_passport_date" />
            <Match idRef="Keywords_cyprus_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_cyprus_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_cyprus_eu_passport_number"></a>Keywords_cyprus_eu_passport_number

- αριθμό διαβατηρίου
- pasaportu
- Αριθμός Διαβατηρίου
- κυπριακό διαβατήριο
- διαβατήριο #
- διαβατήριο
- αριθμός διαβατηρίου
- Pasaport Kimliği
- pasaport nucéesı
- Pasaport no.
- Αρ. Διαβατηρίου

#### <a name="keywords_cyprus_eu_passport_date"></a>Keywords_cyprus_eu_passport_date

- expire le
- émis le


## <a name="cyprus-tax-identification-number"></a>Numéro d’identification fiscale à Chypre
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

huit chiffres et une lettre dans le modèle spécifié

### <a name="pattern"></a>Modèle

huit chiffres et une lettre :

- un « 0 » ou « 9 »
- sept chiffres
- une lettre (ne doit pas être sensible à la cas)

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_cyprus_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_cyprus_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_cyprus_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Cyprus Tax Identification Number -->
      <Entity id="40e64bd9-55f3-4a09-9bd6-1db18dced9dd" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_cyprus_eu_tax_file_number" />
          <Match idRef="Keywords_cyprus_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_cyprus_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_cyprus_eu_tax_file_number"></a>Keywords_cyprus_eu_tax_file_number

- id fiscal
- code d’identification fiscale
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tic #
- tic
- tin id
- tin no
- tin #
- velik kimlik kodu
- veı kimlik nuýsı
- αριθμός φορολογικού μητρώου
- κωδικός φορολογικού μητρώου
- φορολογική ταυτότητα
- φορολογικού κωδικού


## <a name="czech-drivers-license-number"></a>Numéro de permis de conduire tchèque

### <a name="format"></a>Format

deux lettres suivies de six chiffres

### <a name="pattern"></a>Modèle

huit lettres et chiffres :

- lettre 'E' (ne pas sensible à la cas)
- une lettre
- un espace (facultatif)
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_czech_republic_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_czech_republic_eu_driver's_license_number` est trouvé.

```xml
      <Entity id="86b40d3b-d8ea-4c36-aab0-ef9416a6769c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_czech_republic_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_czech_republic_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_czech_republic_eu_drivers_license_number"></a>Keywords_czech_republic_eu_driver’s_license_number

- řidičský prúkaz
- řidičské průkazy
- číslo řidičského průkazu
- čísla řidičských průkazů


## <a name="czech-passport-number"></a>Numéro de passeport tchèque

### <a name="format"></a>Format

huit chiffres sans espaces ni délimiteur

### <a name="pattern"></a>Modèle

huit chiffres sans espaces ni délimiteur

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_czech_republic_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_czech_republic_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière trouve la date au format DD.MM.YYYY ou un mot clé à partir de laquelle est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_czech_republic_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_czech_republic_eu_passport_number` est trouvé.

```xml
      <!-- Czech Republic Passport Number -->
      <Entity id="7bcd8ce8-5e92-4bbe-bc92-fa669f0369fa" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_czech_republic_eu_passport_number"></a>Keywords_czech_republic_eu_passport_number

- cesnkní pas
- číslo pasu
- cesnkní pasu
- passeport no
- čísla pasu

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration


## <a name="czech-personal-identity-number"></a>Numéro d’identité personnel tchèque

### <a name="format"></a>Format

neuf chiffres avec barre oblique facultative (ancien format) 10 chiffres avec barre oblique facultative (nouveau format)

### <a name="pattern"></a>Modèle

neuf chiffres (ancien format) :
- six chiffres qui représentent la date de naissance
- barre oblique facultative
- trois chiffres

10 chiffres (nouveau format) :
- six chiffres qui représentent la date de naissance
- barre oblique facultative
- quatre chiffres où le dernier chiffre est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_czech_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_czech_id_card est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_czech_id_card_new_format trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Czech Personal Identity Number -->
      <!-- Czech Personal Identity Number -->
      <Entity id="60c0725a-4eb6-455b-9dda-05d8a7396497" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_czech_id_card" />
          <Match idRef="Keyword_czech_id_card" />
        </Pattern>
        <Version minEngineVersion="15.20.3000.000">
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Func_czech_id_card_new_format" />
          </Pattern>
        </Version>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keyword_czech_id_card"></a>Keyword_czech_id_card

- numéro de naissance
- id de république tchèque
- czechidno #
- daňové číslo
- identifikační číslo
- identité non
- numéro d’identité
- identityno #
- identityno
- numéro d’assurance
- numéro d’identification nationale
- nationalnumber #
- numéro national
- osobní číslo
- personalidnumber #
- numéro d’ID personnel
- numéro d’identification personnel
- numéro personnel
- pid #
- pid
- pojištění číslo
- rč
- rodne cislo
- rodné číslo
- ssn
- ssn #
- numéro de sécurité sociale
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #
- numéro d’identification unique


## <a name="denmark-drivers-license-number"></a>Numéro de permis de conduire danois

### <a name="format"></a>Format

huit chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_denmark_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_denmark_eu_driver's_license_number` est trouvé.

```xml
      <!-- Denmark Driver's License Number -->
      <Entity id="98a95812-6203-451a-a220-d39870ebef0e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_denmark_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_denmark_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_denmark_eu_drivers_license_number"></a>Keywords_denmark_eu_driver’s_license_number

- kørekort
- kørekortnummer


## <a name="denmark-passport-number"></a>Numéro de passeport danois

### <a name="format"></a>Format

neuf chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_denmark_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_denmark_eu_passport_number` est trouvé.
- L’expression régulière trouve la date au format MM AA ou un mot clé `Regex_eu_passport_date2` à partir de laquelle est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_denmark_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_denmark_eu_passport_number` est trouvé.

```xml
      <!-- Denmark Passport Number -->
      <Entity id="25e8c47e-e6fe-4884-a211-74898f8c0196" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date2" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_denmark_eu_passport_number"></a>Keywords_denmark_eu_passport_number

- pasnummer
- Passeport n°
- pasnumre

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date d’émission
- date d’expiration


## <a name="denmark-personal-identification-number"></a>Numéro d’identification personnel danemark

### <a name="format"></a>Format

10 chiffres contenant un trait d’union

### <a name="pattern"></a>Modèle

10 chiffres :
- six chiffres au format DDMMYY, qui sont la date de naissance
- espace ou trait d’union facultatif
- quatre chiffres où le dernier chiffre est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Func_denmark_eu_tax_file_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_denmark_id est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Func_denmark_eu_tax_file_number trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Denmark Personal Identification Number -->
    <!-- Denmark Personal Identification Number -->
      <Entity id="6c4f2fef-56e1-4c00-8093-88d7a01cf460" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
          <Match idRef="Keyword_denmark_id" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_denmark_id"></a>Keyword_denmark_id

- centrale personregister
- civilet registreringssystem
- sous-président
- sous-groupe #
- gesundheitskarte nummer
- gesundheitsversicherakkarte nummer
- carte d’état d’état
- numéro de carte d’assurance maladie
- numéro d’assurance maladie
- numéro d’identification
- identifikationsnummer
- identifikationsnummer #
- numéro d’identité
- krankenkassennummer
- nationalid #
- nationalnumber #
- numéro national
- personalidnumber #
- personalidentityno #
- numéro d’ID personnel
- personnummer
- personnummer #
- reisekrankenversichenenskartenummer
- rejsesygesikringskort
- ssn
- ssn #
- id de l’id de l’équipe
- kode de kode
- nummer
- spamtenummer
- numéro de sécurité sociale
- sundhedsforsikringskort
- sundhedsforsikringsnummer
- sundhedskort
- sundhedskortnummer
- sygesikring
- sygesikringkortnummer
- code fiscal
- carte d’assurance maladie de voyage
- uniqueidentityno #
- numéro de taxe
- numéro d’enregistrement des taxes
- id fiscal
- numéro d’identification fiscale
- tld #
- numéro de taxe #
- pas de taxe
- taxno #
- numéro de taxe
- pas d’identification fiscale
- tin #
- todno #
- Erdnumber #
- pas de taxe #
- tin id
- tin no
- cpr.nr
- gianr
- butnummer
- personnr
- personregister
- sygesikringsbevis
- sygesikringsbevisnr
- sygesikringsbevisnummer
- sygesikringskort
- sygesikringskortnr
- sygesikringskortnummer
- sygesikringsnr
- sygesikringsnummer


## <a name="drug-enforcement-agency-dea-number"></a>Numéro de la Drug Enforcement Agency (DEA)

### <a name="format"></a>Format

deux lettres suivies de sept chiffres

### <a name="pattern"></a>Modèle

Le modèle doit inclure tous les éléments suivants :
- une lettre (ne sensible à la majuscule) de cet ensemble de lettres possibles : abcdefghjklmnprstux, qui est un code de registre
- une lettre (ne sensible à la cas), qui est la première lettre du nom de famille ou du chiffre « 9 » du registre
- sept chiffres, dont le dernier est le chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_dea_number trouve un contenu qui correspond au modèle.
- Un mot clé est `Keyword_dea_number` trouvé
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_dea_number trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
    <!-- DEA Number -->
    <Entity id="9a5445ad-406e-43eb-8bd7-cac17ab6d0e4" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_dea_number" />
      </Pattern>
      <Version minEngineVersion="15.20.1207.000" maxEngineVersion="15.20.3134.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
        </Pattern>
      </Version>
      <Version minEngineVersion="15.20.3135.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
          <Match idRef="Keyword_dea_number" />
        </Pattern>
      </Version>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_dea_number"></a>Keyword_dea_number

- dea
- dea #
- administration de l’application de la loi sur les anti
- agence d’application de la loi sur les anti-


## <a name="estonia-drivers-license-number"></a>Numéro de permis de conduire estonien

### <a name="format"></a>Format

deux lettres suivies de six chiffres

### <a name="pattern"></a>Modèle

deux lettres et six chiffres :

- les lettres « ET » (ne sont pas sensibles à la cas)
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_estonia_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_estonia_eu_driver's_license_number` est trouvé.

```xml
      <!-- Estonia Driver's License Number -->
      <Entity id="51da8171-da70-4cc1-9d65-055a59ca4f83" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_estonia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- permis de conduire
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_estonia_eu_drivers_license_number"></a>Keywords_estonia_eu_driver’s_license_number

-- permis de conduire
- juhilubade numbrid
- numéro juhiloa
- juhiluba


## <a name="estonia-personal-identification-code"></a>Code d’identification personnelle estonien
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

11 chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

11 chiffres :

- un chiffre qui correspond à des sexes et des années de naissance (nombre impair d’hommes, même nombre de femme ; 1-2 : 19e s. ; 3-4 : 20e s. ; 5-6 : 21e s.)
- six chiffres qui correspondent à la date de naissance (AAMMMMDD)
- trois chiffres qui correspondent à un numéro de série séparant des personnes qui sont né à la même date
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_estonia_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_estonia_eu_national_id_card` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_estonia_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Estonia Personal Identification Code -->
      <Entity id="bfb26de6-dad5-4d48-ab72-4789cdd0654c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Match idRef="Keywords_estonia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_estonia_eu_telephone_number" />
            <Match idRef="Keywords_estonia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_estonia_eu_national_id_card"></a>Keywords_estonia_eu_national_id_card

- id-kaart
- ik
- isikukood #
- isikukood
- maksu id
- maksukohustuslase identifitseerimisnumber
- maksunumber
- numéro d’identification nationale
- numéro national
- code personnel
- numéro d’ID personnel
- code d’identification personnel
- numéro d’identification personnel
- personalidnumber #
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #


## <a name="estonia-passport-number"></a>Numéro de passeport estonien

### <a name="format"></a>Format

une lettre suivie de sept chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

une lettre suivie de sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_estonia_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_estonia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière trouve la date au format DD.MM.YYYY ou un mot clé à partir de laquelle est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_estonia_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_estonia_eu_passport_number` est trouvé.

```xml
      <!-- Estonia Passport Number -->
      <Entity id="61f7073a-509e-425b-a754-bc01bb5d5b8c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

eesti kodaniku pass passi number passinumbrid document number document no dokumendi nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration


## <a name="eu-debit-card-number"></a>Numéro de carte de crédit de l'UE

### <a name="format"></a>Format

16 chiffres

### <a name="pattern"></a>Modèle

Modèle complexe et robuste

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_eu_debit_card trouve un contenu qui correspond au modèle.
- Au moins une des affirmations suivantes est vraie :
    - Un mot clé figurant dans la liste Keyword_eu_debit_card est trouvé.
    - Un mot clé figurant dans la liste Keyword_card_terms_dict est trouvé.
    - Un mot clé figurant dans la liste Keyword_card_security_terms_dict est trouvé.
    - Un mot clé figurant dans la liste Keyword_card_expiration_terms_dict est trouvé.
    - La fonction Func_expiration_date trouve une date au format correct.
- La somme de contrôle est correcte.

```xml
    <!-- EU Debit Card Number -->
    <Entity id="0e9b3178-9678-47dd-a509-37222ca96b42" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_eu_debit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_eu_debit_card" />
          <Match idRef="Keyword_card_terms_dict" />
          <Match idRef="Keyword_card_security_terms_dict" />
          <Match idRef="Keyword_card_expiration_terms_dict" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_eu_debit_card"></a>Keyword_eu_debit_card

- numéro de compte
- numéro de carte
- n° carte
- numéro de sécurité
- cc #

#### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- num de compte
- num de compte
- n° compte
- american express
- americanexpress
- americano espresso
- amex
- carte de retrait
- cartes de retrait
- atm kaart
- atmcard
- atmcards
- atmkaart
- atmkaarten
- bancontact
- carte bancaire
- bankkaart
- titulaire de la carte
- titulaires de la carte
- num de carte
- numéro de carte
- numéros de carte
- type de carte
- cardano numerico
- cardholder
- cardholders
- cardnumber
- cardnumbers
- carta bianca
- Carta credito
- Carta di credito
- cartao de credito
- cartao de crédito
- cartao de debito
- cartao de débito
- carte bancaire
- carte blanche
- carte bleue
- carte de credit
- carte de crédit
- carte di credito
- carteblanche
- cartão de credito
- cartão de crédito
- cartão de debito
- cartão de débito
- cb
- ccn
- carte de vérification
- cartes de vérification
- checkcard
- checkcards
- narkaart
- cirrus
- cirrus-edc-git
- controlekaart
- controlekaarten
- carte de crédit
- cartes de crédit
- carte de crédit
- cartes de crédit
- debetkaart
- debetkaarten
- carte de débit
- cartes de débit
- debitcard
- debitcards
- debito automatico
- diners club
- 2013
- discover
- discover card
- discover cards
- discovercard
- discovercards
- débito automático
- edc
- eigentümername
- carte de crédit européenne
- hoofdkaart
- hoofdkaarten
- in viaggio
- japanese card bureau
- japanse kaartdienst
- jcb
- kaart
- kaart num
- kaartaantal
- kaartaantallen
- kalououder
- kalououders
- 2013
- kartenber
- kartenbers
- kartennr
- kartennummer
- kreditkarte
- kreditkarten-nummer
- kreditkartenhalber
- kreditkartendit
- kreditkartennummer
- kreditkartentyp
- sous-titre
- master card
- master cards
- mastercard
- mastercards
- mc
- mister cash
- n carta
- carta
- no de tarjeta
- no do cartao
- no do cartão
- no. de tarjeta

- no. do cartao

- no. do cartão

- nr carta
- nr. carta

- numeri di scheda
- numero carta
- numero de cartao
- numero de carte
- numero de cartão
- numero de tarjeta
- numero della carta
- numero di carta
- numero di scheda
- numero do cartao
- numero do cartão
- numéro de carte
- nº carta
- nº de carte
- nº de la carte
- nº de tarjeta
- nº do cartao
- nº do cartão
- nº. do cartão

- número de cartao
- número de cartão
- número de tarjeta
- número do cartao
- scheda dell’assegno
- scheda dell’atmosfera
- scheda dell’atmosfera
- scheda della banca
- scheda di controllo
- scheda di debito
- scheda matrice
- schede dell’atmosfera
- schede di controllo
- schede di debito
- schede matrici
- scoprono la scheda
- scoprono le schede
- solo
- supporti di scheda
- supporto di scheda
- commutateur
- tarjeta atm
- tarjeta credito
- tarjeta de atm
- tarjeta de credito
- tarjeta de debito
- tarjeta debito
- tarjeta no
- tarjeta jetente
- tipo della scheda
- ufficio giapponese della
- scheda
- v pay
- v-pay
- visa
- visa plus
- visa electron
- visto
- visum
- vpay

#### <a name="keyword_card_security_terms_dict"></a>Keyword_card_security_terms_dict

- numéro d’identification de la carte
- vérification de la carte
- cardi la verifica
- nic
- cod seg
- cod seguranca
- cod segurança
- cod sicurezza
- cod. seg

- cod. seguranca

- cod. segurança

- cod. sicurezza

- codice di sicurezza
- codice di verifica
- codigo
- codigo de seguranca
- codigo de segurança
- crittogramma
- cryptogram
- cryptogramme
- cv2
- cvc
- cvc2
- cvn
- cvv
- cvv2
- cód seguranca
- cód segurança
- cód. seguranca

- cód. Segurança

- código
- código de seguranca
- código de segurança
- de kaart controle
- geeft nr suit
- n° d’émission
- numéro d’émission
- kaartidentificatienummer
- kreditkartenprufnummer
- kreditkartenprüfnummer
- kwestieaantal
- no. dell’edizione

- no. di sicurezza

- numéro de sécurité
- numero de verificacao
- numero dell’edizione
- numero di identificazione della
- scheda
- numero di sicurezza
- numero van veiligheid
- numéro de sécurité
- nº autorizzazione
- número de verificação
- perno il blocco
- pin block
- prufziffer
- prüfziffer
- code de sécurité
- n° de sécurité
- numéro de sécurité
- sicherheits kode
- sicherheitscode
- sicherheitsnummer
- speldblok
- veiligheid nr
- igheidsaantal
- igheidscode
- igheidsnummer
- verfalldatum

#### <a name="keyword_card_expiration_terms_dict"></a>Keyword_card_expiration_terms_dict

- ablauf
- data de expiracao
- data de expiração
- data del exp
- data di exp
- data di scadenza
- data em que expira
- data scad
- data scadenza
- date de validité
- datum afloop
- datum van exp
- de afloop
- espira
- espira
- date d’exp
- exp datum
- expiration
- expirer
- expire
- expiry
- fecha de expiracion
- fecha de venc
- gultig bis
- gultigkeitsdatum
- gültig bis
- gültigkeitsdatum
- la scadenza
- scadenza
- valable
- validade
- valido hasta
- valor
- venc
- vencimento
- vencimiento
- verloopt
- vervaldag
- vervaldatum
- vto
- válido hasta


## <a name="eu-drivers-license-number"></a>Numéro de permis de conduire de l’UE

Ces entités sont dans le numéro de permis de conduire de l’UE et sont des types d’informations sensibles.

- [Autriche](#austria-drivers-license-number)
- [Belgique](#belgium-drivers-license-number)
- [Bulgarie](#bulgaria-drivers-license-number)
- [Croatie](#croatia-drivers-license-number)
- [Chypre](#cyprus-drivers-license-number)
- [Tchèque](#czech-drivers-license-number)
- [Danemark](#denmark-drivers-license-number)
- [Estonie](#estonia-drivers-license-number)
- [Finlande](#finland-drivers-license-number)
- [France](#france-drivers-license-number)
- [Allemagne](#germany-drivers-license-number)
- [Grèce](#greece-drivers-license-number)
- [Hongrie](#hungary-drivers-license-number)
- [Irlande](#ireland-drivers-license-number)
- [Italie](#italy-drivers-license-number)
- [Lettonie](#latvia-drivers-license-number)
- [Lituanie](#lithuania-drivers-license-number)
- [Qu’est-ce que c’est ?](#luxemburg-drivers-license-number)
- [Malte](#malta-drivers-license-number)
- [Pays-Bas](#netherlands-drivers-license-number)
- [Pologne](#poland-drivers-license-number)
- [Portugal](#portugal-drivers-license-number)
- [Roumanie](#romania-drivers-license-number)
- [République de Slovaquie](#slovakia-drivers-license-number)
- [Slovénie](#slovenia-drivers-license-number)
- [Espagne](#spain-drivers-license-number)
- [Suède](#sweden-drivers-license-number)
- [Royaume-Uni](#uk-drivers-license-number)


## <a name="eu-national-identification-number"></a>Numéro d’identification national de l’UE

Ces entités sont dans le numéro d’identification national de l’UE et sont des types d’informations sensibles.

- [Autriche](#austria-identity-card)
- [Belgique](#belgium-national-number)
- [Bulgarie](#bulgaria-uniform-civil-number)
- [Croatie](#croatia-identity-card-number)
- [Chypre](#cyprus-identity-card)
- [Tchèque](#czech-personal-identity-number)
- [Danemark](#denmark-personal-identification-number)
- [Estonie](#estonia-personal-identification-code)
- [Finlande](#finland-national-id)
- [France](#france-national-id-card-cni)
- [Allemagne](#germany-identity-card-number)
- [Grèce](#greece-national-id-card)
- [Hongrie](#hungary-personal-identification-number)
- [Irlande](#ireland-personal-public-service-pps-number)
- [Italie](#italy-fiscal-code)
- [Lettonie](#latvia-personal-code)
- [Lituanie](#lithuania-personal-code)
- [Qu’est-ce que c’est ?](#luxemburg-national-identification-number-natural-persons)
- [Malte](#malta-identity-card-number)
- [Pays-Bas](#netherlands-citizens-service-bsn-number)
- [Pologne](#poland-national-id-pesel)
- [Portugal](#portugal-citizen-card-number)
- [Roumanie](#romania-personal-numeric-code-cnp)
- [République de Slovaquie](#slovakia-personal-number)
- [Slovénie](#slovenia-unique-master-citizen-number)
- [Espagne](#spain-dni)
- [Royaume-Uni](#uk-national-insurance-number-nino)


## <a name="eu-passport-number"></a>Numéro de passeport de l’UE

Ces entités sont dans le numéro de passeport de l’UE et sont des types d’informations sensibles. Ces entités sont dans l’ensemble des numéro de passeport de l’UE.

- [Autriche](#austria-passport-number)
- [Belgique](#belgium-passport-number)
- [Bulgarie](#bulgaria-passport-number)
- [Croatie](#croatia-passport-number)
- [Chypre](#cyprus-passport-number)
- [Tchèque](#czech-passport-number)
- [Danemark](#denmark-passport-number)
- [Estonie](#estonia-passport-number)
- [Finlande](#finland-passport-number)
- [France](#france-passport-number)
- [Allemagne](#germany-passport-number)
- [Grèce](#greece-passport-number)
- [Hongrie](#hungary-passport-number)
- [Irlande](#ireland-passport-number)
- [Italie](#italy-passport-number)
- [Lettonie](#latvia-passport-number)
- [Lituanie](#lithuania-passport-number)
- [Qu’est-ce que c’est ?](#luxemburg-passport-number)
- [Malte](#malta-passport-number)
- [Pays-Bas](#netherlands-passport-number)
- [Pologne](#poland-passport-number)
- [Portugal](#portugal-passport-number)
- [Roumanie](#romania-passport-number)
- [République de Slovaquie](#slovakia-passport-number)
- [Slovénie](#slovenia-passport-number)
- [Espagne](#spain-passport-number)
- [Suède](#sweden-passport-number)
- [Royaume-Uni](#us--uk-passport-number)


## <a name="eu-social-security-number-or-equivalent-identification"></a>Numéro de sécurité sociale de l’UE ou identification équivalente

Ces entités qui sont dans le numéro de sécurité sociale de l’UE ou une identification équivalente et qui sont des types d’informations sensibles.

- [Autriche](#austria-social-security-number)
- [Belgique](#belgium-national-number)
- [Croatie](#croatia-personal-identification-oib-number)
- [Tchèque](#czech-personal-identity-number)
- [Danemark](#denmark-personal-identification-number)
- [Finlande](#finland-national-id)
- [France](#france-social-security-number-insee)
- [Allemagne](#germany-identity-card-number)
- [Grèce](#greece-national-id-card)
- [Hongrie](#hungary-social-security-number-taj)
- [Portugal](#portugal-citizen-card-number)
- [Espagne](#spain-social-security-number-ssn)
- [Suède](#sweden-national-id)


## <a name="eu-tax-identification-number"></a>Numéro d’identification fiscale de l’UE

Ces entités sont du type d’informations sensibles numéro d’identification fiscale de l’UE.

- [Autriche](#austria-tax-identification-number)
- [Belgique](#belgium-national-number)
- [Bulgarie](#bulgaria-uniform-civil-number)
- [Croatie](#croatia-identity-card-number)
- [Chypre](#cyprus-tax-identification-number)
- [Tchèque](#czech-personal-identity-number)
- [Danemark](#denmark-personal-identification-number)
- [Estonie](#estonia-personal-identification-code)
- [Finlande](#finland-national-id)
- [France](#france-tax-identification-number)
- [Allemagne](#germany-tax-identification-number)
- [Grèce](#greece-tax-identification-number)
- [Hongrie](#hungary-tax-identification-number)
- [Irlande](#ireland-personal-public-service-pps-number)
- [Italie](#italy-fiscal-code)
- [Lettonie](#latvia-personal-code)
- [Lituanie](#lithuania-personal-code)
- [Qu’est-ce que c’est ?](#luxemburg-national-identification-number-non-natural-persons)
- [Malte](#malta-tax-identification-number)
- [Pays-Bas](#netherlands-tax-identification-number)
- [Pologne](#poland-tax-identification-number)
- [Portugal](#portugal-tax-identification-number)
- [Roumanie](#romania-personal-numeric-code-cnp)
- [République de Slovaquie](#slovakia-personal-number)
- [Slovénie](#slovenia-tax-identification-number)
- [Espagne](#spain-tax-identification-number)
- [Suède](#sweden-tax-identification-number)
- [Royaume-Uni](#uk-unique-taxpayer-reference-number)


## <a name="finland-drivers-license-number"></a>Numéro de permis de conduire finlande

### <a name="format"></a>Format

10 chiffres contenant un trait d’union

### <a name="pattern"></a>Modèle

10 chiffres contenant un trait d’union :

- six chiffres
- un trait d’union
- trois chiffres
- un chiffre ou une lettre

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_finland_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_finland_eu_driver's_license_number` est trouvé.

```xml
      <!-- Finland Driver's License Number -->
      <Entity id="bb3b27a3-79bd-4ac4-81a7-f9fca3c7d1a7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_finland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_finland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_finland_eu_drivers_license_number"></a>Keywords_finland_eu_driver’s_license_number

- ajokortti
- permis de conduire
- numero ajokortin
- kuljettaja lic.
- körkort
- körkortnummer
- förare lic.
- ajokortit
- numerot ajokortin


## <a name="finland-european-health-insurance-number"></a>Numéro d’assurance santé européen (Finlande)
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Numéro à 20 chiffres

### <a name="pattern"></a>Modèle

Nombre à 20 chiffres :

- 10 chiffres - 8024680246
- espace ou trait d’union facultatif
- 10 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’Regex_Finland_European_Health_Insurance_Number recherche le contenu qui correspond au modèle.
- Un mot clé de la Keyword_Finland_European_Health_Insurance_Number est trouvé.

```xml
      <!-- Finland European Health Insurance Number -->
      <Entity id="60f75aed-81bf-4625-89b0-0846b9248ee7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Finland_European_Health_Insurance_Number"/>
          <Match idRef="Keyword_Finland_European_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keyword_finland_european_health_insurance_number"></a>Keyword_finland_european_health_insurance_number

- ehic #
- ehic
- finlandehicnumber #
- finska sjukförsäkringskort
- carte d’état d’état
- carte d’assurance maladie
- numéro d’assurance maladie
- hälsokort
- sairaanhoitkomrtin
- sairausvakuutuskortti
- sairausvakuutusnumero
- sjukförsäkring nummer
- sjukförsäkringskort
- suomen sairausvakuutuskortti
- terilliskortti


## <a name="finland-national-id"></a>ID national (Finlande)

### <a name="format"></a>Format

six chiffres plus un caractère indiquant un xème plus trois chiffres plus un chiffre de contrôle

### <a name="pattern"></a>Modèle

Le modèle doit inclure tous les éléments suivants :
- six chiffres au format DDMMYY, qui sont une date de naissance
- marqueur de century ('-', '+' ou 'a')
- numéro d’identification personnel à trois chiffres
- un chiffre ou une lettre (ne sensible à la cas) qui est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- la fonction Func_finnish_national_id trouve un contenu qui correspond au modèle
- un mot clé de Keyword_finnish_national_id trouvé
- la passe de la passe de la passe de contrôle

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- la fonction Func_finnish_national_id trouve un contenu qui correspond au modèle
- la passe de la passe de la passe de contrôle

```xml
      <!-- Finnish National ID-->
      <Entity id="338FD995-4CB5-4F87-AD35-79BD1DD926C1" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_finnish_national_id" />
          <Match idRef="Keyword_finnish_national_id" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_finnish_national_id" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

- repairutlaatuinen henkilökohtainen tunnus
- henkilökohtainen tunnus
- henkilötunnus
- henkilötunnusnumero #
- henkilötunnusnumero
- hetu
- id no
- numéro d’ID
- numéro d’identification
- identiteetti numero
- numéro d’identité
- idnumber
- kansallinen henkilötunnus
- kansallisen henkilökortin
- carte d’identité nationale
- national id no.
- id personnel
- code d’identité personnelle
- personalidnumber #
- personbeteckning
- personnummer
- numéro de sécurité sociale
- sosiaaliturvatunnus
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #
- tunnumero
- tunnus numero
- tunnusloku
- tunnusnumero
- verkomrtti
- veronumero
- verotuntuntun
- verotunnus


## <a name="finland-passport-number"></a>Numéro de passeport finlande

Cette entité est disponible dans le type d’informations sensibles Numéro de passeport de l’UE et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format
combinaison de neuf lettres et chiffres

### <a name="pattern"></a>Modèle
combinaison de neuf lettres et chiffres :
- deux lettres (ne sont pas sensibles à la majuscule)
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_finland_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir `Keywords_eu_passport_number` de ou `Keyword_finland_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière trouve la date au format DD.MM.YYYY ou dans laquelle un mot clé est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_finland_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir `Keywords_eu_passport_number` de ou `Keyword_finland_passport_number` est trouvé.

```xml
      <!-- Finland Passport Number -->
      <Entity id="d1685ac3-1d3a-40f8-8198-32ef5669c7a5" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_finland_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_finland_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_finland_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_finland_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keyword_finland_passport_number"></a>Keyword_finland_passport_number

- suomaomaomaen passi
- passin numero
- passin numero. #
- passin numero #
- passin numero.
- passi #
- numéro passi

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration

## <a name="france-drivers-license-number"></a>Numéro de permis de conduire français

Cette entité est disponible dans le type d’informations sensibles Numéro de permis de conduire de l’UE et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

12 chiffres

### <a name="pattern"></a>Modèle

12 chiffres avec validation pour écarter les modèles similaires, comme les numéros de téléphone français

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- la fonction Func_french_drivers_license trouve un contenu qui correspond au modèle.
- un mot clé de Keyword_french_drivers_license est trouvé.

```xml
    <!-- France Driver's License Number -->
    <Entity id="18e55a36-a01b-4b0f-943d-dc10282a1824" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_drivers_license" />
        <Match idRef="Keyword_french_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_french_drivers_license"></a>Keyword_french_drivers_license

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- permis de conduire
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl
- permis de conduire
- numéro de permis
- numéro de permis
- numéros de permis
- numéros de permis
- numéros de licence


## <a name="france-health-insurance-number"></a>Numéro d’assurance maladie français
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Numéro à 21 chiffres

### <a name="pattern"></a>Modèle

Nombre à 21 chiffres :

- 10 chiffres
- espace facultatif
- 10 chiffres
- espace facultatif
- un chiffre


### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- l’Regex_France_Health_Insurance_Number regex trouve un contenu qui correspond au modèle.
- un mot clé de Keyword_France_Health_Insurance_Number est trouvé.

```xml
      <!-- France Health Insurance Number -->
      <Entity id="9bc2069e-76df-4ff9-ac02-2f519469e236" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_France_Health_Insurance_Number"/>
          <Match idRef="Keyword_France_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keyword_france_health_insurance_number"></a>Keyword_France_health_insurance_number

- carte d’assurance
- carte vitale
- carte d’assuré social


## <a name="france-national-id-card-cni"></a>Carte d’identité nationale (CNI) france

### <a name="format"></a>Format

12 chiffres

### <a name="pattern"></a>Modèle

12 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_france_cni trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_france_eu_national_id_card est trouvé.

```xml
    <!-- France CNI -->
    <Entity id="f741ac74-1bc0-4665-b69b-f0c7f927c0c4" patternsProximity="300" recommendedConfidence="65">
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_france_cni" />
        <Match idRef="Keywords_france_eu_national_id_card" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_france_eu_national_id_card"></a>Keywords_france_eu_national_id_card

- numéro de carte
- carte nationale d’identité
- carte nationale d’idenite no
- cni #
- cni
- compte bancaire
- numéro d’identification nationale
- identité nationale
- nationalidno #
- numéro d’assurance maladie
- numéro de carte vitale


## <a name="france-passport-number"></a>Numéro de passeport français
Cette entité est disponible dans le type d’informations sensibles Numéro de passeport de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

neuf chiffres et lettres

### <a name="pattern"></a>Modèle

neuf chiffres et lettres :
- deux chiffres
- deux lettres (ne sont pas sensibles à la majuscule)
- cinq chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_fr_passport` trouve un contenu qui correspond au modèle.
- Mot clé à partir `Keywords_eu_passport_number` de ou `Keywords_france_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date3` régulière trouve la date au format MM AAA OU un mot clé à partir de laquelle est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_fr_passport` trouve un contenu qui correspond au modèle.
- Mot clé à partir `Keywords_eu_passport_number` de ou `Keywords_france_eu_passport_number` est trouvé.


```xml
    <!-- France Passport Number -->
    <Entity id="3008b884-8c8c-4cd8-a289-99f34fc7ff5d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_fr_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_france_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_fr_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_france_eu_passport_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_france_eu_passport_number"></a>Keywords_france_eu_passport_number

- numéro de passeport
- passeport n °
- passeport non
- passeport #
- passeport #
- passeportnon
- passeportn °
- passeport français
- passeport livre
- passeport carte
- numéro passeport
- passeport n°
- n° du passeport
- n° passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration


## <a name="france-social-security-number-insee"></a>Numéro de sécurité sociale français (INSEE)

### <a name="format"></a>Format

15 chiffres

### <a name="pattern"></a>Modèle

Doit correspondre à l’un des deux modèles suivants :
- 13 chiffres suivis d’un espace suivi de deux chiffres<br/>
ou
- 15 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_french_insee` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_fr_insee est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_french_insee ou Func_fr_insee trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
    <!-- France INSEE -->
    <Entity id="71f62b97-efe0-4aa1-aa49-e14de253619d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_insee" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_fr_insee" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_french_insee" />
        <Match idRef="Keyword_fr_insee" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_fr_insee"></a>Keyword_fr_insee

- code sécu
- d’identité nationale
- insee
- fssn #
- le numéro d’identification nationale
- le code de la sécurité sociale
- id national
- numéro d’identification nationale
- n° d’identité
- 
n° d’identité
- numéro d’assurance
- numéro d’identité
- numéro d’identité
- numéro de sécu
- numéro de sécurité sociale
- n° d’identité
- 
n° d’identité
- ssn
- ssn #
- sécurité sociale
- securité sociale
- securite sociale
- socialsecuritynumber
- numéro de sécurité sociale
- code de sécurité sociale
- numéro d’assurance sociale


## <a name="france-tax-identification-number"></a>Numéro d’identification fiscale français

### <a name="format"></a>Format

13 chiffres

### <a name="pattern"></a>Modèle

13 chiffres

- Un chiffre qui doit être 0, 1, 2 ou 3
- Un chiffre
- Un espace (facultatif) 
- Deux chiffres
- Un espace (facultatif) 
- Trois chiffres
- Un espace (facultatif) 
- Trois chiffres
- Un espace (facultatif) 
- Trois chiffres de vérification


### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_france_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_france_eu_tax_file_number` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_france_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- France Tax Identification Number (numéro SPI.) -->
      <Entity id="ed59e77e-171d-442c-9ec1-88e2ebcb5b0a" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_france_eu_tax_file_number" />
          <Match idRef="Keywords_france_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_france_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_france_eu_telephone_number" />
            <Match idRef="Keywords_france_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_france_eu_tax_file_number"></a>Keywords_france_eu_tax_file_number

- numéro d’identification fiscale
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #


## <a name="france-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée pour la France
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Modèle alphanumérique de 13 caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique de 13 caractères :

- deux lettres - FR (ne sensible à la cas)
- espace ou trait d’union facultatif
- deux lettres ou chiffres
- espace, point, tiret ou virgule facultatif
- trois chiffres
- espace, point, tiret ou virgule facultatif
- trois chiffres
- espace, point, tiret ou virgule facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_france_value_added_tax_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_france_value_added_tax_number est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_france_value_added_tax_number trouve un contenu qui correspond au modèle.

```xml
      <!-- France Value Added Tax Number -->
      <Entity id="949121e6-ad9f-4379-8731-710342baea78" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_france_value_added_tax_number" />
          <Match idRef="Keywords_france_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_france_value_added_tax_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keyword_france_value_added_tax_number"></a>Keyword_France_value_added_tax_number

- numéro de tva
- vat no
- vat #
- taxe sur la valeur ajoutée
- siren identification no numéro d’identification taxe sur valeur ajoutée
- valeur de taxe ajoutée
- taxe sur la valeur ajoutée
- n° tva
- numéro de tva
- numéro d’identification siren


## <a name="germany-drivers-license-number"></a>Numéro de permis de conduire allemand

Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles Numéro de permis de conduire de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

combinaison de 11 chiffres et lettres

### <a name="pattern"></a>Modèle

11 chiffres et lettres (ne sensibles pas à la majuscule) :
- un chiffre ou une lettre
- deux chiffres
- six chiffres ou lettres
- un chiffre
- un chiffre ou une lettre

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_german_drivers_license trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_german_drivers_license_number est trouvé.
- La somme de contrôle est correcte.

```xml
    <!-- German Driver's License Number -->
    <Entity id="91da9335-1edb-45b7-a95f-5fe41a16c63c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_drivers_license" />
        <Match idRef="Keyword_german_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_german_drivers_license_number"></a>Keyword_german_drivers_license_number

- ausstellungsdatum
- ausstellungsort
- ausstellende behöde
- ausstellende behorde
- ausstellende behoerde
- führerschein
- fuhrerschein
- fuehrerschein
- führerscheinnummer
- fuhrerscheinnummer
- fuehrerscheinnummer
- führerschein- 
- fuhrerschein- 
- fuehrerschein- 
- führerscheinnummernr
- fuhrerscheinnummernr
- fuehrerscheinnummernr
- führerscheinnummerklasse
- fuhrerscheinnummerklasse
- fuehrerscheinnummerklasse
- nr-führerschein
- nr-fuhrerschein
- nr-fuehrerschein
- no-führerschein
- no-fuhrerschein
- no-fuehrerschein
- n-führerschein
- n-fuhrerschein
- n-fuehrerschein
- permis de conduire
- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dlno


## <a name="germany-identity-card-number"></a>Numéro de carte d’identité Allemagne

### <a name="format"></a>Format

depuis le 1er novembre 2010 : neuf à dix lettres et chiffres

du 1er avril 1987 au 31 octobre 2010 : 10 chiffres

### <a name="pattern"></a>Modèle

depuis le 1er novembre 2010 : modèle alphanumérique de 9 à 11 caractères
- one L, M, N, P, R, T, V, W, X, Y (ne sensible à la cas)
- huit chiffres ou lettres en C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y et Z (sans la case)
- chiffre de vérification facultatif
- D/D facultatif

du 1er avril 1987 au 31 octobre 2010 :
- 10 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_german_id_card_with_check` trouve un contenu qui correspond au modèle.
- Un mot clé est `Keyword_germany_id_card` trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière trouve un contenu qui correspond au modèle (9 caractères sans chiffre de vérification émis avant `Regex_germany_id_card` 2010 ou 10 chiffres modèle publié posy 2010).
- Un mot clé figurant dans la liste Keyword_germany_id_card est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_german_id_card_with_check` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.


```xml
      <!-- Germany Identity Card Number -->
      <Entity id="e577372f-c42e-47a0-9d85-bebed1c237d4" patternsProximity="300" recommendedConfidence="75"> 
        <Pattern confidenceLevel="75">
         <IdMatch idRef="Regex_germany_id_card" /> 
         <Match idRef="Keyword_germany_id_card" /> 
        </Pattern>
        <Version minEngineVersion="15.20.4545.000"> 
          <Pattern confidenceLevel="85">
           <IdMatch idRef="Func_german_id_card_with_check" />
            <Match idRef="Keyword_germany_id_card" /> 
          </Pattern> 
          <Pattern confidenceLevel="65">
           <IdMatch idRef="Func_german_id_card_with_check" /> 
          </Pattern> 
        </Version>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- ausweis
- gpid
- identification
- identifikation
- identifizierungsnummer
- Carte d’identité
- numéro d’identité
- id-nummer
- id personnel
- personalausweis
- persönliche id nummer
- persönliche identifikationsnummer
- persönliche-id-nummer


## <a name="germany-passport-number"></a>Numéro de passeport allemand

### <a name="format"></a>Format

9 à 11 caractères

### <a name="pattern"></a>Modèle

- une lettre en C, F, G, H, J, K (sans la case)
- huit chiffres ou lettres en C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y et Z (sans la case)
- chiffre de vérification facultatif
- D/D facultatif

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_german_passport_checksum` trouve un contenu qui correspond au modèle.
- Mot clé à partir `Keyword_german_passport` de ou `Keywords_eu_passport_number_common` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction trouve un contenu qui correspond au modèle de neuf caractères (sans chiffre de vérification `Func_german_passport` et d/D facultatif).
- Mot clé à partir `Keyword_german_passport` de ou `Keywords_eu_passport_number_common` est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_german_passport_checksum` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
    <!-- German Passport Number -->
    <Entity id="2e3da144-d42b-47ed-b123-fbf78604e52c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_passport" />
        <Any minMatches="1">
          <Match idRef="Keyword_german_passport" />
          <Match idRef="Keywords_eu_passport_number_common" />
        </Any>
      </Pattern>
      <Version minEngineVersion="15.20.4570.0">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_german_passport_checksum" />
          <Any minMatches="1">
            <Match idRef="Keyword_german_passport" />
            <Match idRef="Keywords_eu_passport_number_common" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_german_passport_checksum" />
        </Pattern>
      </Version>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_german_passport"></a>Keyword_german_passport

- reisepasse
- reisepassnummer
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe
- passeport no.
- passeport no

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport


## <a name="germany-tax-identification-number"></a>Numéro d’identification fiscale allemand

### <a name="format"></a>Format

11 chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

11 chiffres

- Deux chiffres
- Un espace facultatif
- Trois chiffres
- Un espace facultatif
- Trois chiffres
- Un espace facultatif
- Deux chiffres
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_germany_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_germany_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_germany_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Germany Tax Identification Number -->
      <Entity id="43316a89-9880-40cf-b980-04bc7eefcec5" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_eu_tax_file_number" />
          <Match idRef="Keywords_germany_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_germany_eu_tax_file_number"></a>Keywords_germany_eu_tax_file_number

- identifikationsnummer
- steuer id
- steueridentifikationsnummer
- steuernummer
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #
- l’équipe de l’équipe #
- l’équipe de l’équipe
- butnnummer


## <a name="germany-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée en Allemagne
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Modèle alphanumérique de 11 caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique de 11 caractères :

- une lettre D ou d
- une lettre E ou e
- espace facultatif
- trois chiffres
- espace ou virgule facultatif
- trois chiffres
- espace ou virgule facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_germany_value_added_tax_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_germany_value_added_tax_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_germany_value_added_tax_number trouve un contenu qui correspond au modèle.

```xml
      <!-- Germany Value Added Tax Number -->
      <Entity id="db177eb2-8811-4842-bffc-128c14aa219f" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
          <Match idRef="Keywords_germany_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keyword_germany_value_added_tax_number"></a>Keyword_germany_value_added_tax_number

- numéro de tva
- vat no
- vat #
- vat# mehrwertsteuer
- mwst
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer


## <a name="greece-drivers-license-number"></a>Numéro de permis de conduire grec

Cette entité est incluse dans le type d’informations sensibles Numéro de permis de conduire de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

neuf chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_greece_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_greece_eu_driver's_license_number` est trouvé.

```xml
      <!-- Greece Driver's License Number -->
      <Entity id="7a2200b5-aacf-4e3c-ab36-136d3e68b7da" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_greece_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_greece_eu_drivers_license_number"></a>Keywords_greece_eu_driver’s_license_number

- δεια οδήγησης
- Adeia odigisis
- Άδεια οδήγησης
- Δίπλωμα οδήγησης


## <a name="greece-national-id-card"></a>Carte d’identité nationale grèce

### <a name="format"></a>Format

Combinaison de 7 ou 8 lettres et chiffres, plus un tiret

### <a name="pattern"></a>Modèle

Sept lettres et chiffres (ancien format) :
- Une lettre (de l’alphabet grec) 
- Un tiret
- Six chiffres

Huit lettres et chiffres (nouveau format) :
- Deux lettres dont le caractère majuscule figure à la fois dans l’alphabet grec et l’alphabet latin (ABEZHIKMNOPTYX) 
- Un tiret
- Six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_greece_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_greece_id_card est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_greece_id_card trouve un contenu qui correspond au modèle.

```xml
      <!-- Greece National ID Card -->
      <Entity id="82568215-1da1-46d3-874a-d2294d81b5ac" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_id_card" />
          <Match idRef="Keyword_greece_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_greece_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- id grec
- ID national grec
- carte d’identité personnelle grec
- ID de police grec
- Carte d’identité
- tautotita
- ταυτότητα
- ταυτότητας


## <a name="greece-passport-number"></a>Numéro de passeport grec

### <a name="format"></a>Format

Deux lettres suivies de sept chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

Deux lettres suivies de sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_greece_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_greece_eu_passport_number` est trouvé.
- L’expression régulière trouve la date au `Regex_greece_eu_passport_date` format DD MMM AA (exemple - 28 août 19) ou un mot clé à partir `Keywords_greece_eu_passport_date` de laquelle est trouvé

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_greece_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_greece_eu_passport_number` est trouvé.

```xml
      <!-- Greece Passport Number -->
      <Entity id="7e65eb47-cdf9-4f52-8f90-2a27d5ee67e3" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_greece_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_greece_eu_passport_date" />
            <Match idRef="Keywords_greece_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_greece_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_greece_eu_passport_number"></a>Keywords_greece_eu_passport_number

- αριθμός διαβατηρίου
- αριθμούς διαβατηρίου
- αριθμός διαβατηριο


## <a name="greece-social-security-number-amka"></a>Numéro de sécurité sociale grec (AMKA)
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

11 chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

- Six chiffres comme date de naissance AAMMMMDD
- Quatre chiffres
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_greece_eu_ssn` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_greece_eu_ssn_or_equivalent` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_greece_eu_ssn` trouve un contenu qui correspond au modèle.

```xml
      <!-- Greece Social Security Number (AMKA) -->
      <Entity id="e39b03f4-50ea-41ae-af7a-a4b9539596ad" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_greece_eu_ssn" />
          <Match idRef="Keywords_greece_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_greece_eu_ssn" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_greece_eu_ssn_or_equivalent"></a>Keywords_greece_eu_ssn_or_equivalent

- ssn
- ssn #
- non de sécurité sociale
- socialsecurityno #
- numéro de sécurité sociale
- amka
- a.m.k.a.
- Αριθμού Μητρώου Κοινωνικής Ασφάλισης


## <a name="greece-tax-identification-number"></a>Numéro d’identification fiscale grec
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Neuf chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

Neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression  `Regex_greece_eu_tax_file_number` régulière trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_greece_eu_tax_file_number` trouvé.

```xml
      <!-- Greek Tax Identification Number -->
      <Entity id="15a54a5a-53d4-4080-ad43-a2a4fe1d3bf7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_tax_file_number" />
          <Match idRef="Keywords_greece_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_greece_eu_tax_file_number"></a>Keywords_greece_eu_tax_file_number

- afm #
- afm
- aφμ|aφμ αριΘμός
- aφμ
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- non au Registre fiscal
- numéro de Registre fiscal
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- taxregistryno #
- tin id
- tin no
- tin #
- αριθμός φορολογικού μητρώου
- τον αριθμό φορολογικού μητρώου
- φορολογικού μητρώου νο


## <a name="hong-kong-identity-card-hkid-number"></a>Numéro de carte d’identité Hong Kong (HKID)

### <a name="format"></a>Format

Combinaison de 8 ou 9 lettres et chiffres plus éventuellement des parenthèses autour du dernier caractère

### <a name="pattern"></a>Modèle

Combinaison de 8 ou 9 lettres :
- 1 à 2 lettres (ne sensibles pas à la majuscule)
- Six chiffres
- Le dernier caractère (un chiffre ou la lettre A), qui est le chiffre de contrôle et est éventuellement entre parenthèses.

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_hong_kong_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_hong_kong_id_card est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_hong_kong_id_card trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Hong Kong Identity Card (HKID) number -->
<Entity id="e63c28a7-ad29-4c17-a41a-3d2a0b70fd9c" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_hong_kong_id_card"/>
     <Match idRef="Keyword_hong_kong_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="65">
     <IdMatch idRef="Func_hong_kong_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_hong_kong_id_card"></a>Keyword_hong_kong_id_card

- hkid
- carte d’identité hong kong
- HKIDC
- carte d’identité
- Carte d’identité
- carte d’identité hk
- hong kong id
- 香港身份證
- 香港永久性居民身份證
- 身份證
- 身份証
- 身分證
- 身分証
- 香港身份証
- 香港身分證
- 香港身分証
- 香港身份證
- 香港居民身份證
- 香港居民身份証
- 香港居民身分證
- 香港居民身分証
- 香港永久性居民身份証
- 香港永久性居民身分證
- 香港永久性居民身分証
- 香港永久性居民身份證
- 香港非永久性居民身份證
- 香港非永久性居民身份証
- 香港非永久性居民身分證
- 香港非永久性居民身分証
- 香港特別行政區永久性居民身份證
- 香港特別行政區永久性居民身份証
- 香港特別行政區永久性居民身分證
- 香港特別行政區永久性居民身分証
- 香港特別行政區非永久性居民身份證
- 香港特別行政區非永久性居民身份証
- 香港特別行政區非永久性居民身分證
- 香港特別行政區非永久性居民身分証


## <a name="hungary-drivers-license-number"></a>Numéro de permis de conduire hongrois

### <a name="format"></a>Format

Deux lettres suivies de six chiffres

### <a name="pattern"></a>Modèle

Deux lettres et six chiffres :

- Deux lettres (ne sont pas sensibles à la majuscule)
- Six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression  `Regex_hungary_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_hungary_eu_driver's_license_number` est trouvé.

```xml
      <Entity id="9d31c46b-6e6b-444c-aeb1-6dd7e604bb24" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_hungary_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_hungary_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_hungary_eu_drivers_license_number"></a>Keywords_hungary_eu_driver’s_license_number

- vezetoi engedely
- vezetői engedély
- vezetői engedélyek


## <a name="hungary-personal-identification-number"></a>Numéro d’identification personnel hongrie
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres :

- Un chiffre qui correspond au sexe, 1 pour l’homme, 2 pour la femme. D’autres nombres sont également possibles pour les citoyens d’avant 1900 ou les citoyens ayant la double nationalité.
- Six chiffres qui correspondent à la date de naissance (AAMMMMDD)
- Trois chiffres qui correspondent à un numéro de série
- Un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction  `Func_hungary_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_hungary_eu_national_id_card` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction  `Func_hungary_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Hungary Personal Identification Number -->
      <Entity id="7b5cc218-7046-47d9-80c9-f325b50896ca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_national_id_card" />
          <Match idRef="Keywords_hungary_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_hungary_eu_telephone_number" />
            <Match idRef="Keywords_hungary_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_hungary_eu_national_id_card"></a>Keywords_hungary_eu_national_id_card

- numéro d’ID
- numéro d’identification
- sz ig
- sz. ig.
- sz.ig.
- személyazonosító igazolvány
- személyi igazolvány


## <a name="hungary-passport-number"></a>Numéro de passeport hongrois

### <a name="format"></a>Format

Deux lettres suivies de six ou sept chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

Deux lettres suivies de six ou sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_hungary_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_hungary_eu_passport_number` est trouvé.
- L’expression régulière trouve la date au `Regex_hungary_eu_passport_date` format DD MMM/MMM AA (exemple - 01 MÁR/MAR 12) ou un mot clé trouvé `Keywords_eu_passport_date`

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_hungary_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_hungary_eu_passport_number` est trouvé.

```xml
      <!-- Hungary Passport Number -->
      <Entity id="5b483910-9aa7-4c99-9917-f4001464bda7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_hungary_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_hungary_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_hungary_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_hungary_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_hungary_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_hungary_eu_passport_number"></a>Keywords_hungary_eu_passport_number

- útlevél száma
- Útlevelek száma
- útlevél szám

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date d’émission
- date d’expiration


## <a name="hungary-social-security-number-taj"></a>Numéro de sécurité sociale hongrois (TAJ)

### <a name="format"></a>Format

Neuf chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

Neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction  `Func_hungary_eu_ssn_or_equivalent` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_hungary_eu_ssn_or_equivalent` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction  `Func_hungary_eu_ssn_or_equivalent` trouve un contenu qui correspond au modèle.

```xml
      <!-- Hungarian Social Security Number (TAJ) -->
      <Entity id="0de78315-9537-47f5-95ab-b3e77eba3993" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_hungary_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_ssn_or_equivalent" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_hungary_eu_ssn_or_equivalent"></a>Keywords_hungary_eu_ssn_or_equivalent

- numéro de sécurité sociale hongrois
- numéro de sécurité sociale
- socialsecuritynumber #
- hssn #
- socialsecuritynno
- hssn
- taj
- taj #
- ssn
- ssn #
- non de sécurité sociale
- áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám
- magyar áfa szám


## <a name="hungary-tax-identification-number"></a>Numéro d’identification fiscale hongrie
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

10 chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

10 chiffres :

- Un chiffre qui doit être « 8 »
- Huit chiffres
- Un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction  `Func_hungary_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_hungary_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction  `Func_hungary_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Hungary Tax Identification Number -->
      <Entity id="ede42eb4-59d9-49eb-9603-d7853fbda91d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_tax_file_number" />
          <Match idRef="Keywords_hungary_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_hungary_eu_telephone_number" />
            <Match idRef="Keywords_hungary_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_hungary_eu_tax_file_number"></a>Keywords_hungary_eu_tax_file_number

- adóazonosító szám
- adóhatóság szám
- adószám
- tin hongrois
- hungatiantin #
- pas d’autorité fiscale
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #
- numéro de tva


## <a name="hungary-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée de hongrie
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Modèle alphanumérique de 10 caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique de 10 caractères :

- deux lettres - HU ou hu
- espace facultatif
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_hungarian_value_added_tax_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_hungarian_value_added_tax_number est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_hungarian_value_added_tax_number trouve un contenu qui correspond au modèle.

```xml
      <!-- Hungarian Value Added Tax Number -->
      <Entity id="976349a0-683b-477a-90f8-ff0a220d5592" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
          <Match idRef="Keywords_hungarian_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_hungary_value_added_tax_number"></a>Keyword_Hungary_value_added_tax_number

- vat
- numéro de taxe sur la valeur ajoutée
- vat #
- vatno #
- hungarianvatno #
- non fiscal.
- taxe sur la valeur ajoutée áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám


## <a name="india-drivers-license-number"></a>Numéro de permis de conduire Inde

### <a name="format"></a>Format

Modèle alphanumérique de 15 caractères

### <a name="pattern"></a>Modèle

15 lettres ou chiffres :
- deux lettres indiquant le code d’état
- espace ou tiret facultatif
- deux chiffres indiquant le code de la ville
- espace ou tiret facultatif
- quatre chiffres indiquant l’année du problème
- espace ou tiret facultatif
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_india_driving_license` régulière trouve un contenu qui correspond au modèle.
- Un mot clé est `Keywords_eu_driver's_license_number_common` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_india_driving_license` régulière trouve un contenu qui correspond au modèle.


```xml
      <!-- India Driver's License Number -->
        <Entity id="680788a3-53b6-455a-b891-c38cd76dc917" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_india_driving_license" />
            <Match idRef="Keywords_eu_driver's_license_number_common" />
          </Pattern>
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Regex_india_driving_license" />
            </Pattern>
        </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number_common"></a>Keywords_eu_driver’s_license_number_common

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- permis de conduire
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl



## <a name="india-gst-number"></a>Numéro de taxe sur l’inde

### <a name="format"></a>Format

Modèle alphanumérique de 15 caractères

### <a name="pattern"></a>Modèle

15 lettres ou chiffres :
- deux chiffres représentant un code d’état valide
- espace ou tiret facultatif
- dix caractères représentant le numéro de compte permanent (PAN) 
- une lettre ou un chiffre
- espace ou tiret facultatif
- une lettre « z » ou « Z »
- espace ou tiret facultatif
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_india_gst_number` trouve un contenu qui correspond au modèle.
- Un mot clé est `Keyword_india_gst_number` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_india_gst_number` trouve un contenu qui correspond au modèle.


```xml
    <!-- India GST number  -->
      <Entity id="9f5a721c-2fd2-446a-a27e-0c02fbe4630c" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_india_gst_number" />
          <Match idRef="Keyword_india_gst_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_india_gst_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_india_gst_number"></a>Keyword_india_gst_number

- gst
- gstin
- taxe sur les biens et services
- taxe sur les biens et services


## <a name="india-permanent-account-number-pan"></a>Numéro de compte permanent Inde (PAN)

### <a name="format"></a>Format

10 lettres ou chiffres

### <a name="pattern"></a>Modèle

10 lettres ou chiffres :
- Trois lettres (ne sont pas sensibles à la majuscule)
- Lettre en C, P, H, F, A, T, B, L, J, G (ne sensible à la cas)
- Une lettre
- Quatre chiffres
- Une lettre qui est un chiffre de vérification alphabétique

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_india_permanent_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_india_permanent_account_number est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_india_permanent_account_number trouve un contenu qui correspond au modèle.


```xml
      <!-- India Permanent Account Number -->
      <Entity id="2602bfee-9bb0-47a5-a7a6-2bf3053e2804" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_india_permanent_account_number" />
          <Match idRef="Keyword_india_permanent_account_number" />
        </Pattern>
        <Version minEngineVersion="15.20.3520.000">
          <Pattern confidenceLevel="65">
            <IdMatch idRef="Regex_india_permanent_account_number" />
          </Pattern>
        </Version>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- Permanent Account Number
- PAN

## <a name="india-unique-identification-aadhaar-number"></a>Numéro d’identification unique inde (Aadhaar)

### <a name="format"></a>Format

12 chiffres contenant éventuellement des espaces ou des tirets

### <a name="pattern"></a>Modèle

12 chiffres :
- Un chiffre qui n’est pas 0 ou 1
- Trois chiffres
- Éventuellement un tiret ou un espace 
- Quatre chiffres
- Éventuellement un tiret ou un espace 
- Chiffre final, qui est le chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_india_aadhaar trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_india_aadhar est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_india_aadhaar trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- India Unique Identification (Aadhaar) number -->
<Entity id="1ca46b29-76f5-4f46-9383-cfa15e91048f" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_india_aadhaar"/>
     <Match idRef="Keyword_india_aadhar"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_india_aadhaar"/>
  </Pattern>
</Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keyword_india_aadhar"></a>Keyword_india_aadhar
- aadhaar
- aadhar
- aadhar #
- uid
- आधार
- uidai


## <a name="india-voter-id-card"></a>Carte d’ID de votant inde

### <a name="format"></a>Format

Modèle alphanumérique de 10 caractères

### <a name="pattern"></a>Modèle

10 lettres ou chiffres :
- trois lettres
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_india_voter_id_card` régulière trouve un contenu qui correspond au modèle.
- Un mot clé est `Keyword_india_voter_id_card` trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_india_voter_id_card` régulière trouve un contenu qui correspond au modèle.


```xml
      <!-- India Voter Id Card  -->
        <Entity id="646d643f-5228-4408-acc8-f2e81a6df897" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
           <Pattern confidenceLevel="75">
             <IdMatch idRef="Regex_india_voter_id_card" />
             <Match idRef="Keyword_india_voter_id_card" />
            </Pattern>
           <Pattern confidenceLevel="65">
              <IdMatch idRef="Regex_india_voter_id_card" />
            </Pattern>
        </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_india_voter_id_card"></a>Keyword_india_voter_id_card

- voter
- voterid
- votercard
- voteridcard
- carte d’identité de photo électorale
- LASER
- ECI
- commmision de l’équipe de certification


## <a name="indonesia-identity-card-ktp-number"></a>Numéro de carte d’identité (KTP) indonésie

### <a name="format"></a>Format

16 chiffres contenant éventuellement des points

### <a name="pattern"></a>Modèle

16 chiffres :
- Code à deux chiffres désignant la province 
- Un point (facultatif) 
- Code à deux chiffres désignant une régence ou une ville 
- Code à deux chiffres désignant un sous-district 
- Un point (facultatif) 
- Six chiffres au format DDMMYY, qui sont la date de naissance
- Un point (facultatif) 
- Quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière Regex_indonesia_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_indonesia_id_card est trouvé.

```xml
<!-- Indonesia Identity Card (KTP) Number -->
<Entity id="da68fdb0-f383-4981-8c86-82689d3b7d55" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_indonesia_id_card"/>
     <Match idRef="Keyword_indonesia_id_card"/>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_indonesia_id_card"></a>Keyword_indonesia_id_card

- KTP
- Kartu Tanda Penduduk
- Nomor Induk Kependudukan

## <a name="international-banking-account-number-iban"></a>Numéro de compte bancaire international (IBAN)

### <a name="format"></a>Format

Code pays (à deux lettres) plus chiffres de contrôle (à deux chiffres) plus numéro BBAN (jusqu’à 30 chiffres)

### <a name="pattern"></a>Modèle

Le modèle doit inclure tous les éléments suivants :

- Code pays à deux lettres
- Deux chiffres de contrôle (suivis d’un espace facultatif) 
- 1 à 7 groupes de quatre lettres ou chiffres (séparés par des espaces facultatifs)
- 1 à 3 lettres ou chiffres

Le format pour chaque pays est légèrement différent. Le type d’informations sensibles IBAN recouvre ces 60 pays :

- ad
- ae
- al
- at
- az
- ba
- be
- bg
- bh
- ch
- cr
- cy
- cz
- de
- dk
- à faire
- ee
- es
- fi
- fo
- fr
- gb
- ge
- gi
- gl
- gr
- hr
- hu
- ie
- il
- is
- it
- kw
- kz
- lb
- li
- lt
- lu
- lv
- mc
- md
- me
- mk
- mr
- mt
- mu
- nl
- Non
- pl
- pt
- ro
- rs
- sa
- se
- si
- sk
- sm
- tn
- tr
- vg

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_iban trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

Aucune


## <a name="international-classification-of-diseases-icd-10-cm"></a>Classification internationale des maladie (ICD-10-CM)

### <a name="format"></a>Format

Dictionary

### <a name="pattern"></a>Modèle

Mot clé

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- Un mot clé de la Dictionary_icd_10_updated est trouvé.
- Un mot clé de Dictionary_icd_10_codes est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- Un mot clé de Dictionary_icd_10_ mis à jour est trouvé.

```xml
      <!-- ICD-10 CM -->
      <Entity id="3356946c-6bb7-449b-b253-6ffa419c0ce7" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_10_updated" />
          <Match idRef="Dictionary_icd_10_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_10_updated" />
        </Pattern>

```

### <a name="keywords"></a>Mots clés

Tout terme issu du dictionnaire Dictionary_icd_10_updated de mots clés, basé sur la classification internationale des maladie, la dixième révision, la modification de la santé [(ICD-10-CM)](https://go.microsoft.com/fwlink/?linkid=852604). Ce type recherche uniquement le terme, et non les codes d’assurance.

Tout terme issu du dictionnaire Dictionary_icd_10_codes de mots clés, basé sur la classification internationale des maladie, la dixième révision, la modification de la santé [(ICD-10-CM)](https://go.microsoft.com/fwlink/?linkid=852604). Ce type recherche uniquement les codes d’assurance, et non la description.

## <a name="international-classification-of-diseases-icd-9-cm"></a>Classification internationale des maladie (ICD-9-CM)

### <a name="format"></a>Format

Dictionary

### <a name="pattern"></a>Modèle

Mot clé

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- Un mot clé de Dictionary_icd_9_updated est trouvé.
- Un mot clé de Dictionary_icd_9_codes est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- Un mot clé de Dictionary_icd_9_updated est trouvé.

```xml
    <Entity id="fa3f9c74-ee07-4c52-b5f2-085d6b2c0ec4" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_9_updated" />
          <Match idRef="Dictionary_icd_9_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_9_updated" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

Tout terme du dictionnaire de mots clés Dictionary_icd_9_updated, qui est basé sur la classification internationale des maladie, la neuvième révision, la modification génétique [(ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). Ce type recherche uniquement le terme, et non les codes d’assurance.

Tout terme du dictionnaire de mots clés Dictionary_icd_9_codes, qui est basé sur la classification internationale des maladie, la neuvième révision, la modification génétique [(ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). Ce type recherche uniquement les codes d’assurance, et non la description.

## <a name="ip-address"></a>Adresse IP

### <a name="format"></a>Format

#### <a name="ipv4"></a>IPv4 :
Modèle complexe qui prend en compte les versions formatées (périodes) et non formatées (sans point) des adresses IPv4

#### <a name="ipv6"></a>IPv6 :
Modèle complexe qui compte pour les nombres IPv6 formatés (qui incluent les deux-points)

### <a name="pattern"></a>Modèle

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Pour IPv6, une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_ipv6_address trouve un contenu qui correspond au modèle.
- Aucun mot clé figurant dans la liste Keyword_ipaddress n’est trouvé.

Pour IPv4, une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_ipv4_address trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ipaddress est trouvé.

Pour IPv6, une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_ipv6_address trouve un contenu qui correspond au modèle.
- Aucun mot clé figurant dans la liste Keyword_ipaddress n’est trouvé.

```xml
    <!-- IP Address --> 
    <Entity id="1daa4ad5-e2dd-4ca4-a788-54722c09efb2" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv4_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (ce mot clé est sensible à la cas)
- ip address
- adresses IP
- protocole internet
- IP-כתובת ה


## <a name="ip-address-v4"></a>Adresse IP v4

### <a name="format"></a>Format

Modèle complexe qui prend en compte les versions formatées (périodes) et non formatées (sans point) des adresses IPv4

### <a name="pattern"></a>Modèle


### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_ipv4_address` régulière trouve un contenu qui correspond au modèle.
- Un mot clé est `Keyword_ipaddress` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_ipv4_address` régulière trouve un contenu qui correspond au modèle.


```xml
      <!-- IP Address v4--> 
      <Entity id="a7dd5e5f-e7f9-4626-a2c6-86a8cb6830d2" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ipv4_address" />
          <Match idRef="Keyword_ipaddress" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ipv4_address" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (sensible à la cas)
- ip address
- adresses IP
- protocole internet
- IP-כתובת ה


## <a name="ip-address-v6"></a>Adresse IP v6

### <a name="format"></a>Format

Modèle complexe qui compte pour les nombres IPv6 formatés (qui incluent les deux-points)

### <a name="pattern"></a>Modèle


### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_ipv6_address` régulière trouve un contenu qui correspond au modèle.
- Un mot clé est `Keyword_ipaddress` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_ipv6_address` régulière trouve un contenu qui correspond au modèle.


```xml
      <!-- IP Address v6-->
      <Entity id="3f691089-7413-4926-ab3b-3c5ea8a1c17e" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ipv6_address" />
          <Match idRef="Keyword_ipaddress" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ipv6_address" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (sensible à la cas)
- ip address
- adresses IP
- protocole internet
- IP-כתובת ה


## <a name="ireland-drivers-license-number"></a>Numéro de permis de conduire irlande

### <a name="format"></a>Format

Six chiffres suivis de quatre lettres

### <a name="pattern"></a>Modèle

Six chiffres et quatre lettres :

- Six chiffres
- Quatre lettres (ne sont pas sensibles à la majuscule)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression  `Regex_ireland_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_ireland_eu_driver's_license_number` est trouvé.

```xml
      <!-- Ireland Driver's License Number -->
      <Entity id="e01bccd9-eb4d-414f-ace1-e9b6a4c4a2ca" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ireland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_ireland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_ireland_eu_drivers_license_number"></a>Keywords_ireland_eu_driver’s_license_number

- ceadúnas tiomána
- ceadúnée tiomána

## <a name="ireland-passport-number"></a>Numéro de passeport irlande

### <a name="format"></a>Format

Deux lettres ou chiffres suivis de sept chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

Deux lettres ou chiffres suivis de sept chiffres :

- Deux chiffres ou lettres (ne sont pas sensibles à la majuscule)
- Sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_ireland_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_ireland_eu_passport_number` est trouvé.
- L’expression régulière trouve la date au `Regex_ireland_eu_passport_date` format DD MMM/MMM AAA (exemple - 01 BEA/MAI 1988) ou un mot clé est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_ireland_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_ireland_eu_passport_number` est trouvé.

```xml
      <!-- Ireland Passport Number -->
      <Entity id="a2130f27-9ee2-4103-84f9-a6b1ee7d0cbf" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_ireland_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_ireland_eu_passport_number"></a>Keywords_ireland_eu_passport_number

- passeport numero
- uimhreacha pascad
- uimhir pas
- uimhir phas
- uimhreacha pas
- uimhir cáemba
- uimhir cháemba

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date d’émission
- date d’expiration


## <a name="ireland-personal-public-service-pps-number"></a>Numéro de service public personnel (PPS) irlande

### <a name="format"></a>Format

Ancien format (jusqu’au 31 décembre 2012) :
- sept chiffres suivis de 1 à 2 lettres

Nouveau format (1er janvier 2013 et après) :
- sept chiffres suivis de deux lettres

### <a name="pattern"></a>Modèle

Ancien format (jusqu’au 31 décembre 2012) :
- sept chiffres
- une à deux lettres (ne pas prendre en compte la majuscule)

Nouveau format (1er janvier 2013 et après) :
- sept chiffres
- une lettre (ne sensible à la cas) qui est un chiffre de vérification alphabétique
- Lettre facultative de la plage A-I ou « W »

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_ireland_pps trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_ireland_eu_national_id_card est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_ireland_pps trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
      <!-- Ireland Personal Public Service (PPS) Number -->
      <Entity id="1cdb674d-c19a-4fcf-9f4b-7f56cc87345a" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_ireland_pps" />
          <Match idRef="Keywords_ireland_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_ireland_pps" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_ireland_eu_national_id_card"></a>Keywords_ireland_eu_national_id_card

- service d’identité client
- numéro d’identification
- numéro d’ID personnel
- numéro de service public personnel
- service personnel non
- phearsanta seirbhíse poiblí
- pps no
- nombre pps
- pps num
- pps service no
- ppsn
- ppsno #
- ppsno
- psp
- non de service public
- publicserviceno #
- publicserviceno
- numéro de revenu et d’assurance sociale
- rsi no
- rsi number
- rsin
- client seirbhís aitheantais
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phearsanta
- uimhir phearsanta seirbhíse poiblí
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #


## <a name="israel-bank-account-number"></a>Numéro de compte bancaire Israël

### <a name="format"></a>Format

13 chiffres

### <a name="pattern"></a>Modèle

Mise en forme :
- deux chiffres
- un tiret
- trois chiffres
- un tiret
- huit chiffres

Non formaté :
- 	13 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_israel_bank_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_israel_bank_account_number est trouvé.

```xml
<!-- Israel Bank Account Number -->
<Entity id="7d08b2ff-a0b9-437f-957c-aeddbf9b2b25" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_israel_bank_account_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_israel_bank_account_number" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_israel_bank_account_number"></a>Keyword_israel_bank_account_number

- Bank Account Number
- Bank Account
- Numéro de compte
- מספר חשבון בנק

## <a name="israel-national-identification-number"></a>Numéro d’identification national Israël

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_israeli_national_id_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_Israel_National_ID est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- Israel National ID Number -->
<Entity id="e05881f5-1db1-418c-89aa-a3ac5c5277ee" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_israeli_national_id_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_Israel_National_ID" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_israel_national_id"></a>Keyword_Israel_National_ID

-   מספר זהות
-   מספר זיה וי
-   מספר זיהוי ישר אלי      
-   זהותישר אלית
-   هو ية اسرائيل ية عدد
-   هوية إسرائ يلية
-   رقم الهوية
-   عدد هوية فريدة من نوعها
-   idnumber #
-   numéro d’ID
-   identité non        
-   identitynumber #
-   numéro d’identité
-   identitynumber       
-   id personnel
-   id unique  


## <a name="italy-drivers-license-number"></a>Numéro de permis de conduire Italien

Cette entité de type est incluse dans le type d’informations sensibles Numéro de permis de conduire de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

combinaison de 10 lettres et chiffres

### <a name="pattern"></a>Modèle

Combinaison de 10 lettres et chiffres :
- une lettre (ne doit pas être sensible à la cas)
- la lettre « A » ou « V » (ne doit pas être sensible à la cas)
- sept chiffres
- une lettre (ne doit pas être sensible à la cas)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression `Regex_italy_drivers_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir `Keywords_eu_driver's_license_number` de ou `Keyword_italy_drivers_license_number` est trouvé.

```xml
    <!-- Italy Driver's license Number -->
    <Entity id="97d6244f-9157-41bd-8e0c-9d669a5c4d71" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_italy_drivers_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keyword_italy_drivers_license_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keyword_italy_drivers_license_number"></a>Keyword_italy_drivers_license_number

- numero di patente
- patente di guida
- patente guida
- patenti di guida
- patenti guida


## <a name="italy-fiscal-code"></a>Code fiscal italien
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

combinaison de 16 caractères de lettres et de chiffres dans le modèle spécifié

### <a name="pattern"></a>Modèle

Combinaison de 16 caractères de lettres et de chiffres :
- trois lettres qui correspondent aux trois premières consonnes dans le nom de famille
- trois lettres qui correspondent à la première, la troisième et la quatrième consonne du prénom
- deux chiffres qui correspondent aux derniers chiffres de l’année de naissance
- une lettre qui correspond à la lettre du mois de naissance : les lettres sont utilisées dans l’ordre alphabétique, mais seules les lettres A à E, H, L, M, P, R à T sont utilisées (donc, Janvier est A et Octobre est R)
- deux chiffres qui correspondent au jour du mois de naissance afin de différencier les sexes, 40 sont ajoutés au jour de naissance des enfants
- quatre chiffres qui correspondent à l’indicatif de zone spécifique à l’endroit où la personne est né (les codes nationaux sont utilisés pour les pays étrangers)
- un chiffre de parité

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_italy_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_italy_eu_national_id_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_italy_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Italy Fiscal Code -->
      <Entity id="4cd79172-8da9-4ff5-9188-98b1e7e2eca6" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
          <Match idRef="Keywords_italy_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_italy_eu_national_id_card"></a>Keywords_italy_eu_national_id_card

- codice fiscal
- codice fiscale
- codice id personale
- codice personale
- code fiscal
- numero certificato personale
- numero di identificazione fiscale
- numero id personale
- numero personale
- numéro de certificat personnel
- code personnel
- code d’ID personnel
- numéro d’ID personnel
- personalcodeno #
- code fiscal
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- numéro d’identité fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #


## <a name="italy-passport-number"></a>Numéro de passeport Italien

### <a name="format"></a>Format

deux lettres ou chiffres suivis de sept chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

deux lettres ou chiffres suivis de sept chiffres :

- deux chiffres ou lettres (ne sont pas sensibles à la majuscule) ;
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_italy_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_italy_eu_passport_number` est trouvé.
- L’expression régulière trouve la date au `Regex_italy_eu_passport_date` format DD MMM/MMM AAAY (exemple - 01 GEN/JAN 1988) ou un mot clé trouvé `Keywords_eu_passport_date`

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_italy_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_italy_eu_passport_number` est trouvé.

```xml
      <!-- Italy Passport Number -->
      <Entity id="39811019-4750-445f-b26d-4c0e6c431544" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_italy_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_italy_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_italy_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_italy_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_italy_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_italy_eu_passport_number"></a>Keywords_italy_eu_passport_number

- italianantporto
- journal de l’italien
- numeroporto
- numéro passeport
- numero di numporto
- numeri deldéporto
- passeport italien

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration


## <a name="italy-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée italie
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Modèle alphanumérique de 13 caractères avec délimiteur facultatif

### <a name="pattern"></a>Modèle

Modèle alphanumérique de 13 caractères avec des délimiteur facultatifs :

- I ou i
- T ou t
- espace facultatif, point, trait d’union ou virgule
- 11 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_italy_value_added_tax_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_italy_value_added_tax_number est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_italy_value_added_tax_number trouve un contenu qui correspond au modèle.

```xml
      <!-- Italy Value Added Tax -->
      <Entity id="26a8cc07-2283-4a2a-ab1d-4ab643c4c67f" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_italy_value_added_tax_number" />
          <Match idRef="Keywords_italy_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_italy_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_italy_value_added_tax_number"></a>Keyword_italy_value_added_tax_number

- numéro de tva
- vat no
- vat #
- iva
- iva #


## <a name="japan-bank-account-number"></a>Numéro de compte bancaire Japon

### <a name="format"></a>Format

sept ou huit chiffres

### <a name="pattern"></a>Modèle

Numéro de compte bancaire :
- sept ou huit chiffres
- Code de succursale de compte bancaire :
- quatre chiffres
- un espace ou un tiret (facultatif) ;
- trois chiffres

Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_jp_bank_account trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_bank_account est trouvé.
- L’une des affirmations suivantes est vraie :
- La fonction Func_jp_bank_account_branch_code trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_bank_branch_code est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_jp_bank_account trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_bank_account est trouvé.

```xml
<!-- Japan Bank Account Number -->
<Entity id="d354f95b-96ee-4b80-80bc-4377312b55bc" patternsProximity="300" recommendedConfidence="75">
  <Version minEngineVersion="15.01.0131.000">
    <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_jp_bank_account" />
          <Match idRef="Keyword_jp_bank_account" />
          <Any minMatches="1">
            <Match idRef="Func_jp_bank_account_branch_code" />
            <Match idRef="Keyword_jp_bank_branch_code" />
          </Any>
      </Pattern>
  </Version>
     <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_bank_account" />
        <Match idRef="Keyword_jp_bank_account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_jp_bank_account"></a>Keyword_jp_bank_account

- Numéro de compte courant
- Compte courant
- # compte courant
- Numéro compte courant
- # compte courant
- N° de compte courant
- N° de compte courant
- Numéro de compte bancaire
- Compte bancaire
- # Compte bancaire
- Numéro de compte bancaire
- # Compte bancaire
- N° de compte bancaire
- N° de compte bancaire
- Numéro de compte d’épargne
- Compte d’épargne
- N° de compte d’épargne
- Numéro de compte d’épargne
- # compte d’épargne
- N° de compte d’épargne
- N° de compte d’épargne
- Numéro de compte de débit
- Compte de débit
- # Compte de débit
- Numéro de compte de débit
- # Compte de débit
- N° de compte de débit
- N° de compte de débit
- 口座番号
- 銀行口座
- 銀行口座番号
- 総合口座
- 普通預金口座
- 普通口座
- 当座預金口座
- 当座口座
- 預金口座
- 振替口座
- 銀行
- バンク

#### <a name="keyword_jp_bank_branch_code"></a>Keyword_jp_bank_branch_code

- 支店番号
- 支店コード
- 店番号

## <a name="japan-drivers-license-number"></a>Numéro de permis de conduire Japon

### <a name="format"></a>Format

12 chiffres

### <a name="pattern"></a>Modèle

12 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_jp_drivers_license_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_drivers_license_number est trouvé.

```xml
<!-- Japan Driver's License Number -->
<Entity id="c6011143-d087-451c-8313-7f6d4aed2270" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_drivers_license_number" />
        <Match idRef ="Keyword_jp_drivers_license_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_jp_drivers_license_number"></a>Keyword_jp_drivers_license_number

- driverlicense
- driverslicense
- driver’slicense
- driverslicenses
- driver’slicenses
- driverlicenses
- dl #
- dls #
- lic #
- lics #
- 運転免許証
- 運転免許
- 免許証
- 免許
- 運転免許証番号
- 運転免許番号
- 免許証番号
- 免許番号
- 運転免許証ナンバー
- 運転免許ナンバー
- 免許証ナンバー
- 運転免許証no
- 運転免許no
- 免許証no
- 免許no
- 運転経歴証明書番号
- 運転経歴証明書
- 運転免許証No.
- 運転免許No.
- 免許証No.
- 免許No.
- 運転免許証 #
- 運転免許 #
- 免許証 #
- 免許 #


## <a name="japan-my-number---corporate"></a>Japan My Number - Corporate
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Nombre à 13 chiffres

### <a name="pattern"></a>Modèle

Nombre à 13 chiffres :

- un chiffre d’un à neuf
- 12 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_japanese_my_number_corporate trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_japanese_my_number_corporate est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_japanese_my_number_corporate trouve un contenu qui correspond au modèle.

```xml
      <!-- Japanese My Number – Corporate -->
      <Entity id="9e0eaf79-ff20-4ffb-b3e4-e7368d5db6ff" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_japanese_my_number_corporate" />
          <Match idRef="Keywords_japanese_my_number_corporate" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_japanese_my_number_corporate" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_japan_my_number_corporate"></a>Keyword_japan_my_number_corporate

- numéro d’entreprise
- マイナンバー
- 共通番号
- マイナンバーカード
- マイナンバーカード番号
- 個人番号カード
- 個人識別番号
- 個人識別ナンバー
- 法人番号
- 指定通知書


## <a name="japan-my-number---personal"></a>Japan My Number - Personal
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Nombre à 12 chiffres

### <a name="pattern"></a>Modèle

Nombre à 12 chiffres :

- quatre chiffres
- espace, point ou trait d’union facultatif
- quatre chiffres
- espace, point ou trait d’union facultatif
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_japanese_my_number_personal trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_japanese_my_number_personal est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_japanese_my_number_personal trouve un contenu qui correspond au modèle.

```xml
      <!-- Japanese My Number – Personal -->
      <Entity id="98da8e66-7299-4ebd-9f82-c871ab37d3ef" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_japanese_my_number_personal" />
          <Match idRef="Keywords_japanese_my_number_personal" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_japanese_my_number_personal" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_japan_my_number_personal"></a>Keyword_japan_my_number_personal

- mon numéro
- マイナンバー
- 個人番号
- 共通番号
- マイナンバーカード
- マイナンバーカード番号
- 個人番号カード
- 個人識別番号
- 個人識別ナンバー
- 通知カード


## <a name="japan-passport-number"></a>Numéro de passeport Japon

### <a name="format"></a>Format

deux lettres suivies de sept chiffres

### <a name="pattern"></a>Modèle

deux lettres (ne faisant pas l’affaire) suivies de sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_jp_passport trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_passport est trouvé.

```xml
<!-- Japan Passport Number -->
<Entity id="75177310-1a09-4613-bf6d-833aae3743f8" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_passport" />
        <Match idRef="Keyword_jp_passport" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_jp_passport"></a>Keyword_jp_passport

- Passport
- Numéro de passeport
- Numéro de passeport
- # Passeport
- パスポート
- パスポート番号
- パスポートナンバー
- パスポート＃
- パスポート #
- « ポ »
- 旅券番号
- 旅券番号＃
- 旅券番号♯
- 旅券ナンバー


## <a name="japan-residence-card-number"></a>Numéro de carte de résidence Japon

### <a name="format"></a>Format

12 lettres et chiffres

### <a name="pattern"></a>Modèle

12 lettres et chiffres :
- deux lettres (ne sont pas sensibles à la majuscule)
- huit chiffres
- deux lettres (ne sont pas sensibles à la majuscule)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_jp_residence_card_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keyword_jp_residence_card_number est trouvé.

```xml
<!--Japan Residence Card Number-->
-<Entity id="ac36fef2-a289-4e2c-bb48-b02366e89fc0" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_jp_residence_card_number"/>
      <Match idRef="Keyword_jp_residence_card_number"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_jp_residence_card_number"></a>Keyword_jp_residence_card_number

- Numéro de carte de résidence
- Carte de résidence non
- Carte de résidence #
- 在留カード番号
- 在留カード
- 在留番号

## <a name="japan-resident-registration-number"></a>Numéro d’enregistrement du résident japonais

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_jp_resident_registration_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_resident_registration_number est trouvé.

```xml
<!-- Japan Resident Registration Number -->
<Entity id="01c1209b-6389-4faf-a5f8-3f7e13899652" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_resident_registration_number" />
        <Match idRef ="Keyword_jp_resident_registration_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_jp_resident_registration_number"></a>Keyword_jp_resident_registration_number

- Numéro d’enregistrement du résident
- Numéro de base d’enregistrement des résidents
- N° d’enregistrement du résident
- N° d’enregistrement du résident
- N° de base d’enregistrement des résidents
- N° d’enregistrement du résident de base
- 外国人登録証明書番号
- 証明書番号
- 登録番号
- 外国人登録証


## <a name="japan-social-insurance-number-sin"></a>Numéro d’assurance sociale Japon (SIN)

### <a name="format"></a>Format

7 à 12 chiffres

### <a name="pattern"></a>Modèle

7 à 12 chiffres :
- quatre chiffres
- un trait d’union (facultatif) ;
- SIX chiffres OU
- 7 à 12 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_jp_sin trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_sin est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_jp_sin_pre_1997 trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_sin est trouvé.

```xml
<!-- Japan Social Insurance Number -->
<Entity id="c840e719-0896-45bb-84fd-1ed5c95e45ff" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_jp_sin" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_sin_pre_1997" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_jp_sin"></a>Keyword_jp_sin

- N° d’assurance sociale
- Numéro d’assurance sociale
- Numéro d’assurance sociale
- 健康保険被保険者番号
- 健保番号
- 基礎年金番号
- 雇用保険被保険者番号
- 雇用保険番号
- 保険証番号
- 社会保険番号
- 保険No.
- 社会保険
- 介護保険
- 介護保険被保険者番号
- 健康保険被保険者整理番号
- 雇用保険被保険者整理番号
- 厚生年金
- 厚生年金被保険者整理番号


## <a name="latvia-drivers-license-number"></a>Numéro de permis de conduire letton

### <a name="format"></a>Format

trois lettres suivies de six chiffres

### <a name="pattern"></a>Modèle

trois lettres et six chiffres :

- trois lettres (ne sont pas sensibles à la majuscule)
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_latvia_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_latvia_eu_driver's_license_number` est trouvé.

```xml
      <!-- Latvia Driver's License Number -->
      <Entity id="ec996de0-30f2-46b1-b192-4d2ff8805fa7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_latvia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_latvia_eu_drivers_license_number"></a>Keywords_latvia_eu_driver’s_license_number

- autovadītāja apliecība
- autovadītāja apliecības
- vadītāja apliecība

## <a name="latvia-personal-code"></a>Code personnel letton

### <a name="format"></a>Format

11 chiffres et un trait d’union facultatif

### <a name="pattern"></a>Modèle

Ancien format

11 chiffres et un trait d’union :

- six chiffres qui correspondent à la date de naissance (DDMMYY)
- un trait d’union
- un chiffre qui correspond au xxe anniversaire de naissance ( « 0 » pour le 19e siecle, « 1 » pour le XXe et « 2 » pour le 21e s.)
- quatre chiffres, générés de manière aléatoire

Nouveau format

11 chiffres

- Deux chiffres « 32 »
- Neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_latvia_eu_national_id_card` ou l’regex `Regex_latvia_eu_national_id_card_new_format` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_latvia_eu_national_id_card` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_latvia_eu_national_id_card` ou l’regex `Regex_latvia_eu_national_id_card_new_format` trouve un contenu qui correspond au modèle.

```xml
      <!-- Latvia Personal Code -->
      <Entity id="03fcf763-27c2-49ed-9422-2641c6c895c9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_latvia_eu_national_id_card"></a>Keywords_latvia_eu_national_id_card

- numéro d’administration
- alvs nē
- numéro de naissance
- numéro de citoyen
- numéro civile
- numéro de recensement électronique
- numéro électronique
- code fiscal
- numéro d’utilisateur de la santé
- id #
- id-code
- numéro d’identification
- identifikācijas numurs
- id-number
- numéro individuel
- latvija alva
- identificationālais
- id national
- numéro d’identification national
- numéro d’identité national
- numéro d’assurance nationale
- numéro d’enregistrement national
- nodokļa numériques
- nodokļu ID
- nodokļu identifikācija numurs
- numéro de certificat personnel
- code personnel
- code d’ID personnel
- numéro d’ID personnel
- code d’identification personnel
- identificateur personnel
- numéro d’identité personnel
- numéro personnel
- code numérique personnel
- personalcodeno #
- personas kods
- code d’identification de population
- numéro de service public
- numéro d’enregistrement
- numéro de revenu
- numéro d’assurance sociale
- numéro de sécurité sociale
- code fiscal de l’état
- numéro de dossier fiscal
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #
- numéro de votant

## <a name="latvia-passport-number"></a>Numéro de passeport letton

### <a name="format"></a>Format

deux lettres ou chiffres suivis de sept chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

deux lettres ou chiffres suivis de sept chiffres :

- deux chiffres ou lettres (ne sont pas sensibles à la majuscule) ;
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_latvia_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_latvia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière trouve la date au format DD.MM.YYYY ou un mot clé à partir de laquelle est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_latvia_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_latvia_eu_passport_number` est trouvé.

```xml
      <!-- Latvia Passport Number -->
      <Entity id="23ae25ec-cc28-421b-b77a-3054eadf1ede" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_latvia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_latvia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_latvia_eu_passport_number"></a>Keywords_latvia_eu_passport_number

- pase numurs
- pase numur
- pases numuri
- pases nr
- passeport no
- n° du Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration


## <a name="lithuania-drivers-license-number"></a>Numéro de permis de conduire lituanien

### <a name="format"></a>Format

huit chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_lithuania_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_lithuania_eu_driver's_license_number` est trouvé.

```xml
      <!-- Lithuania Driver's License Number -->
      <Entity id="86f7628b-e0f4-4dc3-9fbc-e4300e4c7d78" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_lithuania_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_lithuania_eu_drivers_license_number"></a>Keywords_lithuania_eu_driver’s_license_number

- vairuotojo pažymėjimas
- vairuotojo pažymėjimo numeris
- vairuotojo pažymėjimo numeriai

## <a name="lithuania-personal-code"></a>Code personnel lituanien
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

11 chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

11 chiffres sans espaces et délimiteur :

- un chiffre (1-6) qui correspond au sexe et au century de naissance de la personne
- six chiffres qui correspondent à la date de naissance (AAMMMMDD)
- trois chiffres qui correspondent au numéro de série de la date de naissance
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_lithuania_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_lithuania_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_lithuania_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Lithuania Personal Code -->
      <Entity id="cd6d3786-8ec3-4524-a2cf-1e0095379171" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_lithuania_eu_tax_file_number" />
          <Match idRef="Keywords_lithuania_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_lithuania_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_lithuania_eu_telephone_number" />
            <Match idRef="Keywords_lithuania_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_lithuania_eu_national_id_card"></a>Keywords_lithuania_eu_national_id_card

- asmeninis skaitmeninis kodas
- asmens kodas
- numéro de service des citoyens
- id mcupsčių
- mcupsčių identifikavimas numeris
- mcupsčių identifikavimo numeris
- mcupsčių numeris
- numéro d’identification nationale
- code personnel
- code numérique personnel
- piliečio paslaugos numeris
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #
- unikalus identifikavimo kodas
- unikalus identifikavimo numeris
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #

## <a name="lithuania-passport-number"></a>Numéro de passeport lituanien

### <a name="format"></a>Format

huit chiffres ou lettres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

huit chiffres ou lettres (ne sensibles pas à la majuscule)

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_lithuania_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_lithuania_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date3` régulière trouve la date au format MM AAA OU un mot clé à partir de laquelle est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_lithuania_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_lithuania_eu_passport_number` est trouvé.

```xml
      <!-- Lithuania Passport Number -->
      <Entity id="1b79900f-047b-4c3f-846f-7d73b5534bce" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_lithuania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_lithuania_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_lithuania_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_lithuania_eu_passport_number"></a>Keywords_lithuania_eu_passport_number

- paso numeris
- paso numeriai
- paso nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date d’émission
- date d’expiration


## <a name="luxemburg-drivers-license-number"></a>Numéro de permis de conduire De Qu’est-ce que vous avez ?

### <a name="format"></a>Format

six chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_luxemburg_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_luxemburg_eu_driver's_license_number` est trouvé.

```xml
      <!-- Luxemburg Driver's License Number -->
      <Entity id="89daf717-1544-4860-9a2e-fc9166dd8852" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_luxemburg_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_luxemburg_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_luxemburg_eu_drivers_license_number"></a>Keywords_luxemburg_eu_driver’s_license_number

- fahrerlaubnis
- Führerschäin

## <a name="luxemburg-national-identification-number-natural-persons"></a>Numéro d’identification national (personnes physiques)
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

13 chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

13 chiffres :

- 11 chiffres
- deux chiffres de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_luxemburg_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_luxemburg_eu_national_id_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_luxemburg_eu_tax_file_number` trouve un contenu qui correspond au modèle.


```xml
      <!-- Luxemburg National Identification Number (Natural persons) -->
      <Entity id="aaf661ed-29ec-426d-8bf9-880cad298ebb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Match idRef="Keywords_luxemburg_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_luxemburg_eu_national_id_card"></a>Keywords_luxemburg_eu_national_id_card

- eindeutige id
- eindeutige id-nummer
- eindeutigeid #
- id personnelle
- idpersonnelle #
- idpersonnelle
- code individuel
- ID individuel
- identification individuelle
- identité individuelle
- numéro d’identification personnel
- id personnel
- identification personnelle
- identité personnelle
- personalidno #
- personalidnumber #
- persönliche identifikationsnummer
- id unique
- identité unique
- uniqueidkey #

## <a name="luxemburg-passport-number"></a>Numéro de passeport Dem passport

### <a name="format"></a>Format

huit chiffres ou lettres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

huit chiffres ou lettres (ne sensibles pas à la majuscule)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_luxemburg_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_luxemburg_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date3` régulière trouve la date au format MM AAA OU un mot clé à partir de laquelle est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_luxemburg_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_luxemburg_eu_passport_number` est trouvé.

```xml
      <!-- Luxemburg Passport Number -->
      <Entity id="81d5c027-bed9-4421-91a0-3b2e55b3eb85" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_luxemburg_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_luxemburg_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_luxemburg_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_luxemburg_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_luxemburg_eu_passport_number"></a>Keywords_luxemburg_eu_passport_number
- ausweisnummer
- pass luxembourg
- passeport luxembourg
- passport luxembourg
- no de passeport
- no-reisepass
- nr-reisepass
- numéro de passeport
- pass net
- pass nr
- passnummer
- passeport nombre
- reisepässe
- reisepass-nr
- reisepassnummer

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date d’émission
- date d’expiration


## <a name="luxemburg-national-identification-number-non-natural-persons"></a>Numéro d’identification national (personnes non physiques)

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres

- deux chiffres
- espace facultatif
- trois chiffres
- espace facultatif
- trois chiffres
- espace facultatif
- deux chiffres
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_luxemburg_eu_tax_file_number_non_natural` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_luxemburg_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_luxemburg_eu_tax_file_number_non_natural` trouve un contenu qui correspond au modèle.

```xml
      <!-- Luxemburg National Identification Number (Non-natural persons) -->
      <Entity id="84bffa3a-d805-4788-a613-b1e4df3804cf" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Match idRef="Keywords_luxemburg_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_luxemburg_eu_tax_file_number"></a>Keywords_luxemburg_eu_tax_file_number

- carte de sécurité sociale
- 2013 non
- 2013 #
- identifiant d’impôt
- luxembourg tax identifikatiounsnummer
- numéro d’dossier
- numéro d’identification fiscal dernier
- numéro d’identification fiscale
- sécurité sociale
- sozialunterstützung
- sozialversécherung
- sozialversicheèsausweis
- steier id
- steier identifikatiounsnummer
- steier nummer
- steuer id
- steueridentifikationsnummer
- steuernummer
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #
- l’équipe de l’équipe #
- l’équipe de l’équipe
- zinnzahl


## <a name="malaysia-identification-card-number"></a>Numéro de carte d’identification malaisien

### <a name="format"></a>Format

12 chiffres contenant éventuellement des traits d’union

### <a name="pattern"></a>Modèle

12 chiffres :
- six chiffres au format AAMMMMD, qui sont la date de naissance
- un tiret (facultatif)
- code de lieu de naissance à deux lettres
- un tiret (facultatif)
- trois chiffres aléatoires
- code de sexe à un chiffre

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_malaysia_id_card_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_malaysia_id_card_number est trouvé.

```xml
<!-- Malaysia ID Card Number -->
</Entity>
      <Entity id="7f0e921c-9677-435b-aba2-bb8f1013c749" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_malaysia_id_card_number" />
            <Match idRef="Keyword_malaysia_id_card_number" />
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_malaysia_id_card_number"></a>Keyword_malaysia_id_card_number

- carte d’application numérique
- i/c
- i/c no
- ic
- ic no
- carte d’identité
- carte d’identification
- Carte d’identité
- k/p
- k/p no
- kad akuan diri
- kad aplikasi digital
- kad pengenalan malaisie
- kp
- kp no
- mykad
- mykas
- mykid
- mypr
- mytentera
- carte d’identité Malaisie
- carte d’identité Dente
- nric
- carte d’identification personnelle

## <a name="malta-drivers-license-number"></a>Numéro de permis de conduire de Malte

### <a name="format"></a>Format

Combinaison de deux caractères et six chiffres dans le modèle spécifié

### <a name="pattern"></a>Modèle

combinaison de deux caractères et six chiffres :

- deux caractères (chiffres ou lettres, ne sensibles pas à la majuscule)
- un espace (facultatif)
- trois chiffres
- un espace (facultatif)
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_malta_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_malta_eu_driver's_license_number` est trouvé.

```xml
      <!-- Malta Driver's License Number -->
      <Entity id="a3bdaa4a-8371-4735-8fa5-56ee0fb4afc4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_malta_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_malta_eu_drivers_license_number"></a>Keywords_malta_eu_driver’s_license_number

- liċenzja tas-sewqan
- liċenzji tas-sewwieq


## <a name="malta-identity-card-number"></a>Numéro de carte d’identité de Malte
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

sept chiffres suivis d’une lettre

### <a name="pattern"></a>Modèle

sept chiffres suivis d’une lettre :

- sept chiffres
- une lettre dans « M, G, A, P, L, H, B, Z » (ne sensible à la cas)

### <a name="checksum"></a>Somme de contrôle

Non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_malta_eu_national_id_card` régulière trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_malta_eu_national_id_card` trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_malta_eu_national_id_card` régulière trouve un contenu qui correspond au modèle.

```xml
      <!-- Malta Identity Card Number -->
      <Entity id="854b36b3-a388-4ac8-a4ec-677c2b5e4356" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_national_id_card" />
          <Match idRef="Keywords_malta_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_malta_eu_national_id_card"></a>Keywords_malta_eu_national_id_card

- numéro de service des citoyens
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- code numérique personnel
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #


## <a name="malta-passport-number"></a>Numéro de passeport de Malte

### <a name="format"></a>Format

sept chiffres sans espaces ni délimiteur

### <a name="pattern"></a>Modèle

sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_malta_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_malta_eu_passport_number` est trouvé.
- Un mot clé est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_malta_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_malta_eu_passport_number` est trouvé.

```xml
      <!-- Malta Passport Number -->
      <Entity id="b2b21198-48f9-4d13-b2a5-03969bff0fb8" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
          <Match idRef="Keywords_eu_passport_date" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_malta_eu_passport_number"></a>Keywords_malta_eu_passport_number

- numru tal-talport
- numri tal-talport
- Nru tal-talport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration


## <a name="malta-tax-identification-number"></a>Numéro d’identification fiscale de Malte

### <a name="format"></a>Format

Pour les national(s) d’unité nationale(s) :
- sept chiffres et une lettre dans le modèle spécifié

Nationaux non-nationaux et entités américaines :
- neuf chiffres

### <a name="pattern"></a>Modèle

Nationals malaux : sept chiffres et une lettre

- sept chiffres
- une lettre (ne doit pas être sensible à la cas)

Personnes étrangères et entités locales : neuf chiffres

- neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’regex  `Regex_malta_eu_tax_file_number`  ou trouve le contenu qui correspond au `Regex_malta_eu_tax_file_number_non_maltese_national` modèle.
- Un mot clé est  `Keywords_malta_eu_tax_file_number` trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’regex  `Regex_malta_eu_tax_file_number` ou trouve le contenu qui correspond au `Regex_malta_eu_tax_file_number_non_maltese_national` modèle.

```xml
      <!-- Malta Tax ID Number -->
      <Entity id="ec830c63-65f4-45d0-9d8c-910dc8334b20" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_malta_eu_tax_file_number"></a>Keywords_malta_eu_tax_file_number

- numéro de service des citoyens
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- code numérique personnel
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #


## <a name="medicare-beneficiary-identifier-mbi-card"></a>Carte d’identificateur de bénéficiaire de programme (MBI)

### <a name="format"></a>Format

Modèle alphanumérique de 11 caractères

### <a name="pattern"></a>Modèle

- un chiffre entre 1 et 9
- une lettre à l’exclusion de S, L, O, I, B, Z
- un chiffre ou une lettre à l’exclusion de S, L, O, I, B, Z
- un chiffre
- trait d’union facultatif
- une lettre à l’exclusion de S, L, O, I, B, Z
- un chiffre ou une lettre à l’exclusion de S, L, O, I, B, Z
- un chiffre
- trait d’union facultatif
- deux lettres à l’exclusion de S, L, O, I, B, Z
- deux chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_mbi_card` régulière trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keyword_mbi_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_mbi_card` régulière trouve un contenu qui correspond au modèle.

```xml
    <!-- Medicare Beneficiary Identifier (MBI) card -->
      <Entity id="f753a286-f5cc-47e6-a592-4be25fd02591" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_mbi_card" />
          <Match idRef="Keyword_mbi_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_mbi_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_mbi_card"></a>Keyword_mbi_card

- mbi
- mbi #
- bénéficiaire de l’assurance maladie #
- identificateur du bénéficiaire de l’assurance maladie
- no de bénéficiaire de l’assurance maladie
- numéro de bénéficiaire de l’assurance maladie
- bénéficiaire de l’assurance maladie #


## <a name="mexico-unique-population-registry-code-curp"></a>Code curp (Unique Population Registry Code) du Mexique

### <a name="format"></a>Format

Modèle alphanumérique de 18 caractères

### <a name="pattern"></a>Modèle

- quatre lettres (ne sensibles à la majuscule)
- six chiffres indiquant une date valide
- une lettre - H/h ou M/m
- deux lettres indiquant un code d’état américain valide
- trois lettres
- une lettre ou un chiffre
- un chiffre

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_mexico_population_registry_code` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keyword_mexico_population_registry_code` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_mexico_population_registry_code` trouve un contenu qui correspond au modèle.

```xml
    <!-- Mexico Unique Population Registry Code (CURP) -->
      <Entity id="e905ad4d-5a74-406d-bf36-b1efca798af4" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_mexico_population_registry_code" />
          <Match idRef="Keyword_mexico_population_registry_code" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_mexico_population_registry_code" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_mexico_population_registry_code"></a>Keyword_mexico_population_registry_code

- Clave Única de Registro de Población
- Clave Unica de Registro de Poblacion
- Code de Registre de population unique 
- code de population unique
- CURP
- ID personnel
- Unique ID
- personalid
- personalidnumber
- uniqueidkey
- uniqueidnumber
- clave única
- clave unica
- clave personal Identidad
- personal Identidad Clave
- ClaveÚnica
- queunica
- clavepersonalIdentidad


## <a name="netherlands-citizens-service-bsn-number"></a>Numéro de service des citoyens (BSN) des Pays-Bas

### <a name="format"></a>Format

huit ou neuf chiffres contenant des espaces facultatifs

### <a name="pattern"></a>Modèle

huit à neuf chiffres :
- trois chiffres
- un espace (facultatif)
- trois chiffres
- un espace (facultatif)
- deux-trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_netherlands_bsn trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_netherlands_bsn est trouvé.
- La somme de contrôle est correcte.

```xml
      <!-- Netherlands Citizen's Service (BSN) Number -->
      <Entity id="c5f54253-ef7e-44f6-a578-440ed67e946d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_bsn" />
          <Match idRef="Keywords_netherlands_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_netherlands_eu_national_id_card"></a>Keywords_netherlands_eu_national_id_card

- bsn #
- bsn
- butservicenummer
- numéro de service des citoyens
- numéro de personne
- numéro personnel
- code numérique personnel
- numéro lié à la personne
- persoonlijk nummer
- code persoonlijke numerieke
- persoonsgeègeen
- persoonsnummer
- sociaal-fiscaal nummer
- numéro social-fiscal
- sofi
- sofinummer
- uniek identificatienummer
- uniek identiteitsnummer
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #

## <a name="netherlands-drivers-license-number"></a>Numéro de permis de conduire néerlandais

### <a name="format"></a>Format

10 chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

10 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_netherlands_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_netherlands_eu_driver's_license_number` est trouvé.

```xml
      <!-- Netherlands Driver's License Number -->
      <Entity id="6247fbea-ab80-4be5-8233-308b7c031401" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_netherlands_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_netherlands_eu_driver's_license_number" />
            </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_netherlands_eu_drivers_license_number"></a>Keywords_netherlands_eu_driver’s_license_number

- permis de conduire
- rijbewijs
- rijbewijsnummer
- rijbewijzen
- rijbewijs nummer
- rijbewijsnummers


## <a name="netherlands-passport-number"></a>Numéro de passeport néerlandais

### <a name="format"></a>Format

neuf lettres ou chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

neuf lettres ou chiffres

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_netherlands_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_netherlands_eu_passport_number` est trouvé.
- L’expression régulière trouve la date au `Regex_netherlands_eu_passport_date` format DD MMM/MMM AAAY (exemple - 26 MAA/MAR 2012)

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_netherlands_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_netherlands_eu_passport_number` est trouvé.

```xml
      <!-- Netherlands Passport Number -->
      <Entity id="61786727-bafd-45f6-94d9-888d815e228e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_netherlands_eu_passport_number" />
          <Match idRef="Regex_netherlands_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_netherlands_eu_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_netherlands_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_netherlands_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_netherlands_eu_passport_number"></a>Keywords_netherlands_eu_passport_number

- nummer paspoort
- paspoortnummers
- paspoortnummer
- paspoort nr

## <a name="netherlands-tax-identification-number"></a>Numéro d’identification fiscale pays-Bas
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

neuf chiffres sans espaces ni délimiteur

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_netherlands_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_netherlands_eu_tax_file_number` trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_netherlands_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Netherlands Tax Identification Number -->
      <Entity id="01f42a64-eba7-4892-a67b-398237e4ade2" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_eu_tax_file_number" />
          <Match idRef="Keywords_netherlands_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_netherlands_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_netherlands_eu_tax_file_number"></a>Keywords_netherlands_eu_tax_file_number

- btw nummer
- identification fiscale de l’entreprise
- hulandes impuesto id number
- hulandes impuesto identification
- identificatienummer belasting
- identificatienummer van belasting
- impuesto identification number
- impuesto number
- nederlands belasting id nummer
- nederlands belasting identificatie
- nederlands belasting identificatienummer
- nederlands belastingnummer
- nederlandse belasting identificatie
- identification fiscale pays-Bas
- identification fiscale de l’Île-du-Nord
- tin (pays-bas)
- l’tin (blanc) de la netherland
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- identification fiscale tal
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tax tal
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #


## <a name="netherlands-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée des Pays-Bas
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Modèle alphanumérique de 14 caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique de 14 caractères :

- N ou n
- L ou l
- espace facultatif, point ou trait d’union
- neuf chiffres
- espace facultatif, point ou trait d’union
- B ou b
- deux chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_netherlands_value_added_tax_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_netherlands_value_added_tax_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_netherlands_value_added_tax_number trouve un contenu qui correspond au modèle.

```xml
      <!-- Netherlands Value Added Tax Number -->
      <Entity id="4f320d9b-4972-41ae-b337-88d499bb1ade" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_value_added_tax_number" />
          <Match idRef="Keywords_netherlands_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_netherlands_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_netherlands_value_added_tax_number"></a>Keyword_netherlands_value_added_tax_number

- numéro de tva
- vat no
- vat #
- welg tafoege tax getal
- btw nûmer
- btw-nummer


## <a name="new-zealand-bank-account-number"></a>Numéro de compte bancaire nouvelle-Zélande
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Modèle de 14 à 16 chiffres avec délimiteur facultatif

### <a name="pattern"></a>Modèle

Modèle de 14 à 16 chiffres avec délimiteur facultatif :

- deux chiffres
- trait d’union ou espace facultatif
- trois à quatre chiffres
- trait d’union ou espace facultatif
- sept chiffres
- trait d’union ou espace facultatif
- deux à trois chiffres
- trait d’union ou espace des options

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_new_zealand_bank_account_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_new_zealand_bank_account_number est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_new_zealand_bank_account_number trouve un contenu qui correspond au modèle.

```xml
      <!-- New Zealand Bank Account Number -->
      <Entity id="1a97fc2b-dd2f-48f1-bc4e-2ddf25813956" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
          <Match idRef="Keywords_new_zFealand_bank_account_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_new_zealand_bank_account_number"></a>Keyword_new_zealand_bank_account_number

- numéro de compte
- compte bancaire
- bank_acct_id
- bank_acct_branch
- bank_acct_nbr


## <a name="new-zealand-drivers-license-number"></a>Numéro de permis de conduire nouvelle-Zélande
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

modèle alphanumérique à huit caractères

### <a name="pattern"></a>Modèle

modèle alphanumérique à huit caractères

- deux lettres
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_newzealand_driver_license_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_newzealand_driver_license_number est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_newzealand_driver_license_number trouve un contenu qui correspond au modèle.

```xml
      <!-- New Zealand Driver License Number -->
      <Entity id="1924b377-d287-49c9-a737-cfe7a8a2615a" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
          <Match idRef="Keywords_newzealand_driver_license_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_new_zealand_drivers_license_number"></a>Keyword_new_zealand_drivers_license_number

- driverlicence
- driverlicences
- driver lic
- permis de conduire
- permis de conduire
- driverslic
- driverslicence
- driverslicences
- drivers lic
- drivers lics
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- driverlic #
- driverlics #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicence #
- driver’slicences #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduite international
- permis de conduite internationaux
- nz automobile association
- association automobile nouvelle-Zélande


## <a name="new-zealand-inland-revenue-number"></a>Numéro de revenu pour la Nouvelle-Zélande
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

huit ou neuf chiffres avec des délimiteur facultatifs

### <a name="pattern"></a>Modèle

huit ou neuf chiffres avec des délimiteur facultatifs

- deux ou trois chiffres
- espace ou trait d’union facultatif
- trois chiffres
- espace ou trait d’union facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_new_zealand_inland_revenue_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_new_zealand_inland_revenue_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_new_zealand_inland_revenue_number trouve un contenu qui correspond au modèle.

```xml
      <!-- New Zealand Inland Revenue Number -->
      <Entity id="dd0fe2bc-7bcf-455f-bac1-83b1e3eb25fd" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
          <Match idRef="Keywords_new_zealand_inland_revenue_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_new_zealand_inland_revenue_number"></a>Keyword_new_zealand_inland_revenue_number

- ird no.
- ird no #
- nz ird
- nouvelle-Zélande ird
- numéro ird
- numéro de revenu intérieur


## <a name="new-zealand-ministry-of-health-number"></a>Numéro de santé du ministère de la Nouvelle-Zélande

### <a name="format"></a>Format

trois lettres et quatre chiffres

### <a name="pattern"></a>Modèle

- trois lettres (ne sont pas sensibles à la majuscule) à l’exception de « I » et « O »
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_new_zealand_ministry_of_health_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_nz_terms est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_new_zealand_ministry_of_health_number trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
    <!-- New Zealand Health Number -->
    <Entity id="2b71c1c8-d14e-4430-82dc-fd1ed6bf05c7" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
          <Match idRef="Keyword_nz_terms" />
      </Pattern>
      <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
       </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_nz_terms"></a>Keyword_nz_terms

- NHI
- Nouvelle-Zélande
- Index national de santé
- NHI #
- Index national de santé #

## <a name="new-zealand-social-welfare-number"></a>Numéro de réseau social nouvelle-zélande

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres

- trois chiffres
- un trait d’union facultatif
- trois chiffres
- un trait d’union facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_newzealand_social_welfare_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_newzealand_social_welfare_number est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_newzealand_social_welfare_number trouve un contenu qui correspond au modèle.

```xml
      <!-- Newzealand Social Welfare Number -->
      <Entity id="20f3c48d-4ac1-4cd2-86bd-34ecc1826e9d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_social_welfare_number" />
          <Match idRef="Keywords_newzealand_social_welfare_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_social_welfare_number" />
        </Pattern>
      </Entity>
    </Version>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_new_zealand_social_welfare_number"></a>Keyword_new_zealand_social_welfare_number

- social social #
- social social #
- social social no.
- numéro social
- swn #


## <a name="norway-identification-number"></a>Numéro d’identification norvégien

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres :
- six chiffres au format DDMMYY, qui sont la date de naissance
- numéro individuel à trois chiffres
- deux chiffres de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_norway_id_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_norway_id_number est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_norway_id_numbe trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Norway Identification Number -->
<Entity id="d4c8a798-e9f2-4bd3-9652-500d24080fc3" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_norway_id_number"/>
     <Match idRef="Keyword_norway_id_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_norway_id_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_norway_id_number"></a>Keyword_norway_id_number

- Personal identification number
- Norwegian ID Number
- ID Number
- Identification
- Personnummer
- Fødselsnummer


## <a name="philippines-unified-multi-purpose-identification-number"></a>Numéro d’identification multi-usage unifié philippines

### <a name="format"></a>Format

12 chiffres séparés par des traits d’union

### <a name="pattern"></a>Modèle

12 chiffres :
- quatre chiffres
- un trait d’union
- sept chiffres
- un trait d’union
- un chiffre

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_philippines_unified_id trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_philippines_id est trouvé.

```xml
<!-- Philippines Unified Multi-Purpose ID number -->
<Entity id="019b39dd-8c25-4765-91a3-d9c6baf3c3b3" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_philippines_unified_id"/>
     <Match idRef="Keyword_philippines_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_philippines_id"></a>Keyword_philippines_id

- Unified Multi-Purpose ID
- UMID
- Identity Card
- Pinag-isang Multi-Layunin ID

## <a name="poland-drivers-license-number"></a>Numéro de permis de conduire polonais

### <a name="format"></a>Format

14 chiffres contenant deux barres obliques

### <a name="pattern"></a>Modèle

14 chiffres et deux barres obliques :

- cinq chiffres
- barre oblique
- deux chiffres
- barre oblique
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_poland_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_poland_eu_driver's_license_number` est trouvé.

```xml
      <!-- Poland Driver's License Number -->
      <Entity id="24d51f99-ee9e-4060-a077-cae58cab1ee4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_poland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_poland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- permis de conduire
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_poland_eu_drivers_license_number"></a>Keywords_poland_eu_driver’s_license_number

- prawo jazdy
- prawa jazdy

## <a name="poland-identity-card"></a>Carte d’identité pologne

### <a name="format"></a>Format

trois lettres et six chiffres

### <a name="pattern"></a>Modèle

trois lettres (ne faisant pas l’affaire) suivies de six chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_polish_national_id trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_polish_national_id_passport_number est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- Poland Identity Card-->
<Entity id="25E64989-ED5D-40CA-A939-6C14183BB7BF" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_national_id" />
          <Match idRef="Keyword_polish_national_id_passport_number" />
      </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_poland_national_id_passport_number"></a>Keyword_poland_national_id_passport_number

- Dowód osobisty
- Numer dowodu osobistego
- Nazwa i numer dowodu osobistego
- Nazwa i nr dowodu osobistego
- Nazwa je nr dowodu tożsamości
- Dowód Tożsamości
- dow. os.



## <a name="poland-national-id-pesel"></a>ID national polonais (PESEL)

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

- six chiffres représentant la date de naissance au format AAMMMMDD
- quatre chiffres
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_pesel_identification_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_pesel_identification_number est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_pesel_identification_number trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
      <!-- Poland National ID (PESEL) -->
      <Entity id="E3AAF206-4297-412F-9E06-BA8487E22456" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_pesel_identification_number" />
          <Match idRef="Keyword_pesel_identification_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_pesel_identification_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_pesel_identification_number"></a>Keyword_pesel_identification_number

- dowód osobisty
- dowódosobisty
- numer niepowtarzalny
- niepowtarzalnynumer
- nr.-pesel
- nr-pesel
- numer identyfikacyjny
- pesel
- tożsamościodowej


## <a name="poland-passport-number"></a>Numéro de passeport polonais
Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles Numéro de passeport de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

deux lettres et sept chiffres

### <a name="pattern"></a>Modèle

Deux lettres (ne faisant pas l’affaire) suivies de sept chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_polish_passport_number_v2` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.
- Mot clé à partir `Keywords_eu_passport_number` de ou `Keyword_polish_national_passport_number` est trouvé.
- Un mot clé est `Keywords_eu_passport_date` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_polish_passport_number_v2` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.
- Mot clé à partir `Keywords_eu_passport_number` de ou `Keyword_polish_national_passport_number` est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_polish_passport_number_v2` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
      <!-- Poland Passport Number -->
      <Entity id="03937FB5-D2B6-4487-B61F-0F8BFF7C3517" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_passport_number_v2" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keyword_polish_national_passport_number"></a>Keyword_polish_national_passport_number

- numer paszportu
- numery paszportów
- numery paszportowe
- nr paszportu
- nr. paszportu
- nr paszportów
- n° passeport
- passeport n°

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date d’émission
- date d’expiration


## <a name="poland-regon-number"></a>Numéro reGON polonais
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Nombre à 9 chiffres ou 14 chiffres

### <a name="pattern"></a>Modèle

neuf chiffres ou un nombre à 14 chiffres :

- neuf chiffres ou
- neuf chiffres
- trait d’union
- cinq chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_polish_regon_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_polish_regon_number est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_polish_regon_number trouve un contenu qui correspond au modèle.

```xml
      <!-- Polish REGON Number  -->
      <Entity id="fc87b421-f437-4f8b-b739-29a735ead0d9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_regon_number" />
          <Match idRef="Keywords_polish_regon_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_regon_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keywords_poland_regon_number"></a>Keywords_poland_regon_number

- id de régon
- numéro statistique
- id statistique
- non statistique
- numéro de régon
- regonid #
- regonno #
- ID d’entreprise
- companyid #
- companyidno #
- numer statystyczny
- numeru regon
- numerstatystyczny #
- numeruregon #


## <a name="poland-tax-identification-number"></a>Numéro d’identification fiscale polonais
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

11 chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

11 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_poland_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_poland_eu_tax_file_number` trouvé.


```xml
      <!-- Poland Tax Identification Number -->
      <Entity id="1ff28b4d-40f2-49e9-b677-9606a88e2bca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_poland_eu_tax_file_number" />
          <Match idRef="Keywords_poland_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_poland_eu_tax_file_number"></a>Keywords_poland_eu_tax_file_number

- nip #
- nip
- numer identyfikacji podatkowej
- numeridentyfikacjipodatkowej #
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #
- vat id #
- vat id
- vat no
- numéro de tva
- vatid #
- vatid
- vatno #


## <a name="portugal-citizen-card-number"></a>Numéro de carte de citoyen portugais

### <a name="format"></a>Format

huit chiffres

### <a name="pattern"></a>Modèle

huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_portugal_citizen_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_portugal_citizen_card est trouvé.

```xml
<!-- Portugal Citizen Card Number -->
<Entity id="91a7ece2-add4-4986-9a15-c84544d81ecd" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_portugal_citizen_card"/>
     <Match idRef="Keyword_portugal_citizen_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_portugal_citizen_card"></a>Keyword_portugal_citizen_card

- bilhete de identidade
- cartão de cidadão
- carte de citoyen
- numéro de document
- documento de identificação
- numéro d’ID
- identification non
- numéro d’identification
- carte d’identité non
- numéro de carte d’identité
- carte d’identité nationale
- nic
- número bi de portugal
- número de identificação civile
- número de identificação fiscal
- número do documento
- numéro bi portugal


## <a name="portugal-drivers-license-number"></a>Numéro de permis de conduire Portugal

### <a name="format"></a>Format

deux modèles : deux lettres suivies de 5 à 8 chiffres avec des caractères spéciaux

### <a name="pattern"></a>Modèle

Modèle 1 : deux lettres suivies de 5/6 avec des caractères spéciaux :
- Deux lettres (ne sont pas sensibles à la majuscule)
- Un trait d’union 
- Cinq ou six chiffres
- Un espace
- Un chiffre

Modèle 2 : une lettre suivie de 6/8 chiffres avec des caractères spéciaux :
- Une lettre (ne doit pas être sensible à la cas)
- Un trait d’union 
- Six ou huit chiffres
- Un espace
- Un chiffre


### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_portugal_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_portugal_eu_driver's_license_number` est trouvé.

```xml
      <!-- Portugal Driver's License Number -->
      <Entity id="977f1e5a-2c33-4bcc-b516-95bb275cff23" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_portugal_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_portugal_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_portugal_eu_drivers_license_number"></a>Keywords_portugal_eu_driver’s_license_number

- carteira de qua
- carteira 2016
- carteira de habilitação
- carteira habilitação
- número de licença
- número licença
- permissão de condução
- permissão condução
- Licença condução Portugal
- carta de condução

## <a name="portugal-passport-number"></a>Numéro de passeport portugais

### <a name="format"></a>Format

une lettre suivie de six chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

une lettre suivie de six chiffres :

- une lettre (ne doit pas être sensible à la cas)
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_portugal_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_portugal_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière trouve la date au format DD.MM.YYYY ou un mot clé à partir de laquelle est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_portugal_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_portugal_eu_passport_number` est trouvé.

```xml
      <!-- Portugal Passport Number -->
      <Entity id="080a52fd-a7bc-431e-b54d-51f08f59db11" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_portugal_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_portugal_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_portugal_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_portugal_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_portugal_eu_passport_number"></a>Keywords_portugal_eu_passport_number

- número doentporte
- passport portugais
- passeport portugais
- portugueseeporte
- neporte nº
- passeport nº
- números depostporte
- passeports portugais
- númeroposte
- númerosposte

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date d’émission
- date d’expiration


## <a name="portugal-tax-identification-number"></a>Numéro d’identification fiscale portugais

### <a name="format"></a>Format

neuf chiffres avec espaces facultatifs

### <a name="pattern"></a>Modèle

- trois chiffres
- espace facultatif
- trois chiffres
- espace facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_portugal_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_portugal_eu_tax_file_number` trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_portugal_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Portugal Tax Identification Number -->
      <Entity id="65372402-3131-4f1e-9983-4439841d1f15" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_portugal_eu_tax_file_number" />
          <Match idRef="Keywords_portugal_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_portugal_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_portugal_eu_tax_file_number"></a>Keywords_portugal_eu_tax_file_number

- cpf #
- cpf
- nif #
- nif
- número de identificação fisca
- numero fiscal
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #


## <a name="romania-drivers-license-number"></a>Numéro de permis de conduire roumain

### <a name="format"></a>Format

un caractère suivi de huit chiffres

### <a name="pattern"></a>Modèle

un caractère suivi de huit chiffres :
- une lettre (ne sensible pas à la cas) ou un chiffre
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_romania_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_romania_eu_driver's_license_number` est trouvé.

```xml
      <!-- Romania Driver's License Number -->
      <Entity id="b5511ace-2fd8-4ae4-b6fc-c7c6e4689e3c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_romania_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_romania_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- permis de conduire
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_romania_eu_drivers_license_number"></a>Keywords_romania_eu_driver’s_license_number

- permis de déréere
- permisului de quere
- permisului permetere
- permisele de quere
- permisele permetere
- permiseere

## <a name="romania-personal-numeric-code-cnp"></a>Code numérique personnel roumain (CNP)
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

13 chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

- un chiffre de 1 à 9
- six chiffres représentant la date de naissance (AAMMMMDD)
- deux chiffres, qui peuvent être 01-52 ou 99
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_romania_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_romania_eu_national_id_card` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_romania_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Romania Personal Numerical Code (CNP) -->
      <Entity id="eb5fa399-fe28-4c67-8188-d63a616ed89c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_romania_eu_national_id_card" />
          <Match idRef="Keywords_romania_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_romania_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_romania_eu_national_id_card"></a>Keywords_romania_eu_national_id_card

- cnp #
- cnp
- cod identificare personal
- cod numérique personnel
- cod unic identificare
- codnumericpersonal #
- codul fiscal nr.
- identificarea fiscală nr #
- id-ul taxei
- numéro d’assurance
- insurancenumber #
- national id #
- id national
- numéro d’identification nationale
- număr identificare personal
- număr identitate
- număr personal unic
- număridentitate #
- număridentitate
- numărpersonalunic #
- numărpersonalunic
- număru de identificare fiscală
- numărul de identificare fiscală
- code numérique personnel
- pin #
- pin
- fichier fiscal non
- numéro de dossier fiscal
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #
- uniqueidentityno

## <a name="romania-passport-number"></a>Numéro de passeport roumain

### <a name="format"></a>Format

huit ou neuf chiffres sans espace et délimiteur

### <a name="pattern"></a>Modèle

huit ou neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_romania_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_romania_eu_passport_number` est trouvé.
- L’expression régulière trouve la date au `Regex_romania_eu_passport_date` format DD MMM/MMM AA (Exemple - 01 février/10 février) ou un mot clé trouvé `Keywords_eu_passport_date`

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_romania_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_romania_eu_passport_number` est trouvé.

```xml
      <!-- Romania Passport Number -->
      <Entity id="5d31b90c-7fe2-4a76-a14b-767b8fd19d6c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_romania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_romania_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_romania_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_romania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_romania_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_romania_eu_passport_number"></a>Keywords_romania_eu_passport_number

numărul pașaportului numarul pasaportului numerele pașaportului Pașaport nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration


## <a name="russia-passport-number-domestic"></a>Numéro de passeport russe national
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Nombre à 10 chiffres

### <a name="pattern"></a>Modèle

Nombre à 10 chiffres :

- deux chiffres
- espace ou trait d’union facultatif
- deux chiffres
- espace facultatif
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’Regex_Russian_Passport_Number_Domestic regex trouve un contenu qui correspond au modèle.
- Un mot clé de Keyword_Russian_Passport_Number est trouvé.

```xml
      <!-- Russian Passport Number Domestic -->
      <Entity id="76ec2f5d-cedb-48e1-8070-1998794af445" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_Domestic" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_russia_passport_number_domestic"></a>Keyword_russia_passport_number_domestic

- numéro de passeport
- passport no
- passport #
- id passport
- passportno #
- passportnumber #
- паспорт нет
- паспорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #


## <a name="russia-passport-number-international"></a>Numéro de passeport russe international
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

numéro à neuf chiffres

### <a name="pattern"></a>Modèle

nombre à neuf chiffres :

- deux chiffres
- espace ou trait d’union facultatif
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’Regex_Russian_Passport_Number_International recherche le contenu qui correspond au modèle.
- Un mot clé de Keyword_Russian_Passport_Number est trouvé.

```xml
      <!-- Russian Passport Number International -->
      <Entity id="ac5f4878-75e4-4b82-af2d-02e13ea9f411" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_International" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_russia_passport_number_international"></a>Keywords_russia_passport_number_international

- numéro de passeport
- passport no
- passport #
- id passport
- passportno #
- passportnumber #
- паспорт нет
- паспорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #


## <a name="saudi-arabia-national-id"></a>ID national Arabie saoudite

### <a name="format"></a>Format

10 chiffres

### <a name="pattern"></a>Modèle

10 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_saudi_arabia_national_id trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_saudi_arabia_national_id est trouvé.

```xml
<!-- Saudi Arabia National ID -->
<Entity id="8c5a0ba8-404a-41a3-8871-746aa21ee6c0" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_saudi_arabia_national_id" />
        <Any minMatches="1">
          <Match idRef="Keyword_saudi_arabia_national_id" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_saudi_arabia_national_id"></a>Keyword_saudi_arabia_national_id

- Carte d’identification
- numéro de carte d’identité
- Numéro d’identification
- الوطنية الهوية بطاقة رقم


## <a name="singapore-national-registration-identity-card-nric-number"></a>Numéro de carte d’identité d’inscription nationale (NRIC) Singapour

### <a name="format"></a>Format

neuf lettres et chiffres

### <a name="pattern"></a>Modèle

- neuf lettres et chiffres :
- la lettre « F », « G », « S » ou « T » (ne sensible pas à la cas)
- sept chiffres
- un chiffre de vérification alphabétique

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_singapore_nric trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_singapore_nric est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_singapore_nric trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Singapore National Registration Identity Card (NRIC) Number -->
<Entity id="cead390a-dd83-4856-9751-fb6dc98c34da" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_singapore_nric"/>
     <Match idRef="Keyword_singapore_nric"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_singapore_nric"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_singapore_nric"></a>Keyword_singapore_nric

- National Registration Identity Card
- Identity Card Number
- NRIC
- IC
- Foreign Identification Number
- FIN
- 身份证
- 身份證

## <a name="slovakia-drivers-license-number"></a>Numéro de permis de conduire slovaque

### <a name="format"></a>Format

un caractère suivi de sept chiffres

### <a name="pattern"></a>Modèle

un caractère suivi de sept chiffres

- une lettre (ne sensible à la cas) ou un chiffre
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_slovakia_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_slovakia_eu_driver's_license_number` est trouvé.

```xml
      <!-- Slovakia Driver's License Number -->
      <Entity id="14240c22-b6de-4ce5-a90b-137f74252513" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovakia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_slovakia_eu_drivers_license_number"></a>Keywords_slovakia_eu_driver’s_license_number

- vodičský preukaz
- vodičské preukazy
- vodičského preukazu
- vodičských preukazov

## <a name="slovakia-personal-number"></a>Numéro personnel slovaque
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

neuf ou 10 chiffres contenant une barre oblique inverse facultative

### <a name="pattern"></a>Modèle

- six chiffres représentant la date de naissance
- barre oblique facultative (/)
- trois chiffres
- un chiffre de vérification facultatif

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_slovakia_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_slovakia_eu_national_id_card` trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_slovakia_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Slovakia Personal Number -->
      <Entity id="951c26b7-3b35-4f73-924b-15dd599cb9ab" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
          <Match idRef="Keywords_slovakia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
        </Pattern>
      </Entity>
    </Version>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_slovakia_eu_national_id_card"></a>Keywords_slovakia_eu_national_id_card

- azonosító szám
- numéro de naissance
- číslo národnej identifikačnej 2013
- číslo občianského preukazu
- daňové číslo
- numéro d’ID
- identification non
- numéro d’identification
- identifikačnáča č
- identifikačné číslo
- carte d’identité non
- numéro de carte d’identité
- národná identifikačná značka č
- numéro national
- nationalnumber #
- nemzeti személyazonosító igazolvány
- personalidnumber #
- rč
- rodne cislo
- rodné číslo
- numéro de sécurité sociale
- ssn #
- ssn
- személyi igazolvány szám
- személyi igazolvány száma
- személyigazolvány szám
- fichier fiscal non
- numéro de dossier fiscal
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #

## <a name="slovakia-passport-number"></a>Numéro de passeport slovaque

### <a name="format"></a>Format

un chiffre ou une lettre suivi de sept chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

un chiffre ou une lettre (ne sensible à la cas) suivi de sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_slovakia_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_slovakia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière trouve la date au format DD.MM.YYYY ou dans laquelle un mot clé est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_slovakia_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_slovakia_eu_passport_number` est trouvé.

```xml
      <!-- Slovakia Passport Number -->
      <Entity id="238e1f08-d80e-4793-af33-9b57918335b7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_slovakia_eu_passport_number"></a>Keywords_slovakia_eu_passport_number

- číslo pasu
- čísla pasov
- pas č.
- Passeport n°
- n° Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration


## <a name="slovenia-drivers-license-number"></a>Numéro de permis de conduire slovène

### <a name="format"></a>Format

neuf chiffres sans espaces et délimiteur

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_slovenia_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_slovenia_eu_driver's_license_number` est trouvé.

```xml
      <!-- Slovenia Driver's License Number -->
      <Entity id="d5bc089a-f2ee-433d-a6b1-5c253051d6f2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovenia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_slovenia_eu_drivers_license_number"></a>Keywords_slovenia_eu_driver’s_license_number

- vozniško dovoljenje
- licence vozniška številka
- vozniških dovoljenj
- številka vozniškega dovoljenja
- številke vozniških dovoljenj

## <a name="slovenia-unique-master-citizen-number"></a>Numéro de citoyen maître unique de Slovénie
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

13 chiffres sans espaces ni délimiteur

### <a name="pattern"></a>Modèle

13 chiffres dans le modèle spécifié :

- sept chiffres qui correspondent à la date de naissance (DDMMLLL) où « LLL » correspond aux trois derniers chiffres de l’année de naissance
- deux chiffres qui correspondent à la zone de naissance « 50 »
- trois chiffres qui correspondent à une combinaison de sexe et de numéro de série pour les personnes qui sont né le même jour. 000-499 pour les hommes et 500-999 pour les hommes.
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_slovenia_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_slovenia_eu_national_id_card` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_slovenia_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Slovenia Unique Master Citizen Number -->
      <Entity id="68948b27-803d-41e4-adf1-13e05eb541bb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
          <Match idRef="Keywords_slovenia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_slovenia_eu_national_id_card"></a>Keywords_slovenia_eu_national_id_card

- edinstvena številka glavnega državljana
- emšo
- enotna maticna številka obcana
- carte d’identité
- numéro d’identification
- identifikacijska številka
- Carte d’identité
- nacionalna id
- liste nacionalni potni
- id national
- osebna izkaznica
- osebni koda
- osebni ne
- osebni številka
- code personnel
- numéro personnel
- code numérique personnel
- številka državljana
- numéro de citoyen unique
- numéro d’ID unique
- numéro d’identité unique
- numéro de citoyen maître unique
- numéro d’inscription unique
- uniqueidentityno #
- uniqueidentityno #

## <a name="slovenia-passport-number"></a>Numéro de passeport slovène

### <a name="format"></a>Format

deux lettres suivies de sept chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

deux lettres suivies de sept chiffres :

- la lettre « P »
- une lettre en lettres minuscules
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_slovenia_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_slovenia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière trouve la date au format DD.MM.YYYY ou un mot clé à partir de laquelle est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_slovenia_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_slovenia_eu_passport_number` est trouvé.

```xml
      <!-- Slovenia Passport Number -->
      <Entity id="235b7976-7bbe-4df5-bb40-08678e749d1a" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_slovenia_eu_passport_number"></a>Keywords_slovenia_eu_passport_number

- številka potnega lista
- potek veljavnosti
- liste potni #
- datum rojstva
- liste potni
- številke potnih listov

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration


## <a name="slovenia-tax-identification-number"></a>Numéro d’identification fiscale slovène
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

huit chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

- un chiffre de 1 à 9
- six chiffres
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_slovenia_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_slovenia_eu_tax_file_number` trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_slovenia_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Slovenia Tax Identification Number -->
      <Entity id="e47b071e-c352-4d70-8241-8c215ad65505" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_tax_file_number" />
          <Match idRef="Keywords_slovenia_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovenia_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_slovenia_eu_tax_file_number"></a>Keywords_slovenia_eu_tax_file_number

- davčna številka
- identifikacijska številka davka
- številka davčne datoteke
- fichier fiscal non
- numéro de dossier fiscal
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #


## <a name="south-africa-identification-number"></a>Numéro d’identification Afrique du Sud

### <a name="format"></a>Format

13 chiffres pouvant contenir des espaces

### <a name="pattern"></a>Modèle

13 chiffres :
- six chiffres au format AAMMMMD, qui sont la date de naissance
- quatre chiffres
- un indicateur de nationalité à un chiffre
- le chiffre « 8 » ou « 9 »
- un chiffre, qui est un chiffre de la checksum

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_south_africa_identification_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_south_africa_identification_number est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- South Africa Identification Number -->
<Entity id="e2adf7cb-8ea6-4048-a2ed-d89eb65f2780" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_africa_identification_number"/>
     <Match idRef="Keyword_south_africa_identification_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_south_africa_identification_number"></a>Keyword_south_africa_identification_number

- Identity card
- ID
- Identification

## <a name="south-korea-resident-registration-number"></a>Numéro d’enregistrement d’un résident en Corée du Sud

### <a name="format"></a>Format

13 chiffres contenant un trait d’union

### <a name="pattern"></a>Modèle

13 chiffres :
- six chiffres au format AAMMMMD, qui sont la date de naissance
- un trait d’union
- un chiffre déterminé par le xème et le sexe
- Code de région de naissance à quatre chiffres
- un chiffre utilisé pour différencier les personnes pour lesquelles les chiffres précédents sont identiques
- un chiffre de vérification.

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_south_korea_resident_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_south_korea_resident_number est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_south_korea_resident_number trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- South Korea Resident Registration Number -->
<Entity id="5b802e18-ba80-44c4-bc83-bf2ad36ae36a" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_korea_resident_number"/>
     <Match idRef="Keyword_south_korea_resident_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_south_korea_resident_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- National ID card
- Citizen’s Registration Number
- Jumin deungnok beonho
- RRN
- 주민등록번호

## <a name="spain-drivers-license-number"></a>Numéro de permis de conduire espagnol

### <a name="format"></a>Format

huit chiffres suivis d’un caractère

### <a name="pattern"></a>Modèle

huit chiffres suivis d’un caractère :

- huit chiffres
- un chiffre ou une lettre (ne pas sensible à la cas)

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_spain_eu_DL_and_NI_number_citizen` ou trouve un contenu qui correspond au `Func_spain_eu_DL_and_NI_number_foreigner` modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_spain_eu_driver's_license_number` est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_spain_eu_DL_and_NI_number_citizen` ou trouve un contenu qui correspond au `Func_spain_eu_DL_and_NI_number_foreigner` modèle.

```xml
      <!-- Spain Driver's License Number -->
      <Entity id="d5a82922-b501-4f40-8868-341321146aa2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_spain_eu_driver's_license_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_spain_eu_driver's_license_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_spain_eu_drivers_license_number"></a>Keywords_spain_eu_driver’s_license_number

- permiso de casción
- permiso casción
- licencia de qualique
- licencia caser
- permiso caser
- permiso de qualifir
- permisos de qualif
- permisos caser
- carnet d’carnets
- carnet de délirir
- licencia de manejo
- licencia manejo

## <a name="spain-dni"></a>DNI (Espagne)
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

huit chiffres suivis d’un caractère

### <a name="pattern"></a>Modèle

sept chiffres suivis d’un caractère

- huit chiffres
- Espace ou trait d’union facultatif
- une lettre à cocher (ne pas sensible à la cas)

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_spain_eu_DL_and_NI_number_citizen` ou trouve un contenu qui correspond au `Func_spain_eu_DL_and_NI_number_foreigner` modèle.
- Un mot clé est  `Keywords_spain_eu_national_id_card"` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_spain_eu_DL_and_NI_number_citizen` ou trouve un contenu qui correspond au `Func_spain_eu_DL_and_NI_number_foreigner` modèle.


```xml
      <!-- Spain DNI -->
      <Entity id="8e6251b9-47b4-40e8-a42b-0f80876be192" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_spain_eu_national_id_card"></a>Keywords_spain_eu_national_id_card

- carné de identidad
- dni #
- dni
- dninúmero #
- documento nacional de identidad
- identidad único
- identidadúnico #
- numéro d’assurance
- numéro d’identification nationale
- identité nationale
- nationalid #
- nationalidno #
- nie #
- nie
- nienúmero #
- número de identificación
- número nacional identidad
- numéro d’identification personnel
- identité personnelle non
- numéro d’identité unique
- uniqueid #

## <a name="spain-passport-number"></a>Numéro de passeport espagnol

### <a name="format"></a>Format

combinaison de huit ou neuf caractères de lettres et de chiffres sans espace ni délimiteur

### <a name="pattern"></a>Modèle

combinaison de huit ou neuf caractères de lettres et de chiffres :

- deux chiffres ou lettres
- un chiffre ou une lettre (facultatif)
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_spain_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_spain_eu_passport_number` est trouvé.
- L’expression `Regex_spain_eu_passport_date` régulière trouve la date au format JD-MM-AAA OU un mot clé à partir de laquelle est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_spain_eu_passport_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_passport_number` de ou `Keywords_spain_eu_passport_number` est trouvé.

```xml
      <!-- Spain Passport Number -->
      <Entity id="d17a57de-9fa5-4e9f-85d3-85c26d89686e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_spain_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_spain_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_spain_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_spain_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_spain_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- libreta pasaporte
- número pasaporte
- españa pasaporte
- números de pasaporte
- número de pasaporte
- números pasaporte
- pasaporte no
- Passeport n°
- n° Passeport
- pasaporte no.
- pasaporte n°
- passport espagne

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration


## <a name="spain-social-security-number-ssn"></a>Numéro de sécurité sociale (SSN) espagnol


### <a name="format"></a>Format

11 à 12 chiffres

### <a name="pattern"></a>Modèle

11 à 12 chiffres :
- deux chiffres
- barre oblique (facultative)
- sept à huit chiffres
- barre oblique (facultative)
- deux chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_spanish_social_security_number trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.
- - Un mot clé est  `Keywords_spain_eu_ssn_or_equivalent` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_spanish_social_security_number trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
    <!-- Spain SSN -->
    <Entity id="5df987c0-8eae-4bce-ace7-b316347f3070" patternsProximity="300" recommendedConfidence="85" relaxProximity="true" >
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spanish_social_security_number" />
          <Match idRef="Keywords_spain_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spanish_social_security_number" />
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- ssn
- ssn #
- socialsecurityno
- non de sécurité sociale
- numéro de sécurité sociale
- número de la seguridad social

## <a name="spain-tax-identification-number"></a>Numéro d’identification fiscale espagnol
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

sept ou huit chiffres et une ou deux lettres dans le modèle spécifié

### <a name="pattern"></a>Modèle

Personnes physiques espagnoles avec une carte d’identité nationale Espagne :

- huit chiffres
- une lettre en lettres minuscules (sensible à la minuscule)

Personnes non résidentes sans carte d’identité nationale Espagne

- une lettre minuscule « L » (sensible à la minuscule)
- sept chiffres
- une lettre en lettres minuscules (sensible à la minuscule)

Résidents résidants de moins de 14 ans sans carte d’identité nationale Espagne :

- une lettre minuscule « K » (sensible à la cas)
- sept chiffres
- une lettre en lettres minuscules (sensible à la minuscule)

Personnes avec un numéro d’identification de pièce d’identité

- une lettre en lettres minuscules qui est « X », « Y » ou « Z » (sensible à la cas)
- sept chiffres
- une lettre en lettres minuscules (sensible à la minuscule)

Personnes sans numéro d’identification

- une lettre en lettres minuscules qui est « M » (sensible à la minuscule)
- sept chiffres
- une lettre en lettres minuscules (sensible à la minuscule)

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_spain_eu_tax_file_number` ou trouve un contenu qui correspond au `Func_spain_eu_DL_and_NI_number_citizen` modèle.
- Un mot clé est  `Keywords_spain_eu_tax_file_number` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_spain_eu_tax_file_number` ou trouve un contenu qui correspond au `Func_spain_eu_DL_and_NI_number_citizen` modèle.

```xml
      <!-- Spain Tax Identification Number -->
      <Entity id="10f0d113-b0e1-47dc-872a-a4f45b9376a3" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_spain_eu_tax_file_number"></a>Keywords_spain_eu_tax_file_number

- cif
- cifid #
- cifnúmero #
- número de quyente
- número de identificación fiscal
- número de impuesto corporativo
- spanishcifid #
- spanishcifid
- spanishcifno #
- spanishcifno
- fichier fiscal non
- numéro de dossier fiscal
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #


## <a name="sql-server-connection-string"></a>SQL Server de connexion

### <a name="format"></a>Format

Chaîne « User Id », « User ID », « uid » ou « UserId » suivie des caractères et des chaînes décrits dans le modèle ci-dessous.

### <a name="pattern"></a>Modèle

- la chaîne « User Id », « User ID », « uid » ou « UserId »
- toute combinaison de 1 à 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- chaîne « Password » ou « pwd » où « pwd » n’est pas précédé d’une lettre minuscule
- signe égal (=)
- tout caractère qui n’est pas un signe dollar ($), un symbole de pourcentage (%) supérieur au symbole (>), au symbole (@), des guillemets (« ), un point-virgule (;), accolade gauche([) ou un crochet gauche ({)
- toute combinaison de 7 à 128 caractères qui ne sont pas des points-virgules (;), barre oblique (/) ou guillemets (« )
- point-virgule (;) ou guillemets (« )

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_SQLServerConnectionString trouve un contenu qui correspond au modèle.
- Un mot clé de CEP_GlobalFilter est in trouvé.
- L’expression régulière CEP_PasswordPlaceHolder trouve pas de contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords trouve pas de contenu qui correspond au modèle.

```sql
<!---SQL Server Connection String>
<Entity id="e76b6205-d3cb-46f2-bd63-c90153f2f97d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_SQLServerConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_GlobalFilter" />
            <Match idRef="CEP_PasswordPlaceHolder" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="cep_globalfilter"></a>CEP_GlobalFilter

- some-password
- somepassword
- secretPassword
- exemple

#### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

Ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.

- Mot de passe ou pwd suivi de 0 à 2 espaces, d’un signe égal (=), de 0 à 2 espaces et d’un astérisque (*) -OR-
- Mot de passe ou pwd suivi de :
    - Signe Égal (=)
    - Symbole inférieur à (<)
    - Toute combinaison de 1 à 200 caractères contenant des lettres majuscules ou minuscules, des chiffres, un astérisque (*), un tiret (-), un trait de soulignement (_) ou un espace blanc
    - Symbole supérieur à (>)

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

Ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.

- contoso
- fabrikam
- northwind
- sandbox
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net

## <a name="sweden-drivers-license-number"></a>Numéro de permis de conduire suédois

### <a name="format"></a>Format

10 chiffres contenant un trait d’union

### <a name="pattern"></a>Modèle

10 chiffres contenant un trait d’union :

- six chiffres
- un trait d’union
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression  `Regex_sweden_eu_driver's_license_number` régulière trouve un contenu qui correspond au modèle.
- Mot clé à partir  `Keywords_eu_driver's_license_number` de ou `Keywords_sweden_eu_driver's_license_number` est trouvé.

```xml
      <!-- Sweden Driver's License Number -->
      <Entity id="70088720-90dd-47f5-805e-5525f3567391" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_sweden_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


#### <a name="keywords_sweden_eu_drivers_license_number"></a>Keywords_sweden_eu_driver’s_license_number

- ajokortti
- permis de déréere
- ajokortin numero
- kuljettajat lic.
- drivere lic.
- körkort
- numărul permisului de quere
-  שאָפער דערלויבעניש נומער
- förare lic.
-  דריווערס דערלויבעניש
- körkortsnummer

## <a name="sweden-national-id"></a>ID national suédois

### <a name="format"></a>Format

10 ou 12 chiffres et éventuellement un délimiteur

### <a name="pattern"></a>Modèle

10 ou 12 chiffres et un délimiteur facultatif :
- deux chiffres (facultatif)
- Six chiffres au format de date AAMMJJ
- délimiteur de « - » ou « + » (facultatif)
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_swedish_national_identifier` trouve un contenu qui correspond au modèle.
- Un mot clé est `Keywords_swedish_national_identifier` trouvé
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_swedish_national_identifier` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.


```xml
    <!-- Sweden National ID -->
    <Entity id="f69aaf40-79be-4fac-8f05-fd1910d272c8" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_swedish_national_identifier" />
        <Match idRef="Keywords_swedish_national_identifier" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_swedish_national_identifier" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_swedish_national_identifier"></a>Keywords_swedish_national_identifier

- id no
- numéro d’ID
- id #
- identification non
- numéro d’identification
- identifikationsnumret #
- identifikationsnumret
- Gestion des identitets
- document d’identité
- identité non
- numéro d’identité
- id-nummer
- id personnel
- personnummer #
- personnummer
- cubeteidentifikationsnummer

## <a name="sweden-passport-number"></a>Numéro de passeport suédois

### <a name="format"></a>Format

huit chiffres

### <a name="pattern"></a>Modèle

huit chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- l’expression régulière Regex_sweden_passport_number trouve un contenu qui correspond au modèle.
- mot clé à `Keywords_eu_passport_number` partir de ou est `Keyword_sweden_passport` trouvé.
- l’expression régulière trouve une date au `Regex_sweden_eu_passport_date` format DD MMM/MMM AA (01 JAN/JAN 12) ou un mot clé est `Keywords_eu_passport_date` trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- l’expression régulière Regex_sweden_passport_number trouve un contenu qui correspond au modèle.
- mot clé à `Keywords_eu_passport_number` partir de ou est `Keyword_sweden_passport` trouvé.


```xml
    <!-- Sweden Passport Number -->
    <Entity id="ba4e7456-55a9-4d89-9140-c33673553526" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_sweden_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- carte d’inscription de l’inscription de l'
- frais de traitement g3
- entrée multiple
- Numéro de passeport
- passeport n °
- passeport non
- passeport #
- passeport #
- passeportnon
- passeportn °
- passnummer
- pass nr
- visa
- visas visas
- entrée unique
- sverige pass
- exigences en matière de visa
- traitement des visas
- type de visa

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date de problème
- date d’expiration


## <a name="sweden-tax-identification-number"></a>Numéro d’identification fiscale suédois
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

10 chiffres et un symbole dans le modèle spécifié

### <a name="pattern"></a>Modèle

10 chiffres et un symbole :

- six chiffres qui correspondent à la date de naissance (AAMMMMDD)
- signe plus ou signe moins
- trois chiffres qui rendent le numéro d’identification unique où :
  - pour les nombres émis avant 1990, le septième et le huitième chiffres identifient le département de naissance ou les personnes étrangères
  - le chiffre à la neuvième position indique le sexe par impair pour l’homme ou même pour la femme
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_sweden_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_sweden_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_sweden_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Sweden Tax Identification Number -->
      <Entity id="139acba0-a5bc-4fbb-876d-f7a493ae8a40" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_sweden_eu_tax_file_number" />
          <Match idRef="Keywords_sweden_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_sweden_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_sweden_eu_telephone_number" />
            <Match idRef="Keywords_sweden_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_sweden_eu_tax_file_number"></a>Keywords_sweden_eu_tax_file_number

- numéro d’ID personnel
- personnummer
- atomt id nummer
- identifikation
- bettebetaquets identifikationsnummer
- sverige tin
- fichier fiscal
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #


## <a name="swift-code"></a>Code SWIFT

### <a name="format"></a>Format

quatre lettres suivies de 5 à 31 lettres ou chiffres

### <a name="pattern"></a>Modèle

quatre lettres suivies de 5 à 31 lettres ou chiffres :
- code bancaire à quatre lettres (ne pas sensible à la cas)
- espace facultatif
- 4 à 28 lettres ou chiffres (numéro de compte bancaire de base (BBAN))
- espace facultatif
- une à trois lettres ou chiffres (reste du BBAN)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_swift trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_swift est trouvé.

```xml
<Entity id="cb2ab58c-9cb8-4c81-baf8-a4e106791df4" patternsProximity="300" recommendedConfidence="75">
<Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_swift" />
        <Match idRef="Keyword_swift" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_swift"></a>Keyword_swift

- organisation internationale de normalisation 9362
- ISO 9362
- iso9362
- swift #
- swiftcode
- swiftnumber
- swiftroutingnumber
- code swift
- # numéro swift
- numéro d’acheminement swift
- numéro BIC
- code BIC
- # bic
- bic #
- code d’identification bancaire
- Organisation internationale de normalisation 9362
- rapide #
- code SWIFT
- le numéro de swift
- swift numéro d’acheminement
- le numéro BIC
- # <a name="bic"></a>BIC
- code identificateur de banque
- SWIFT
- SWIFT番
- BIC番
- BIC
- SWIFT
- SWIFT 番
- Bic 番
- BIC
- 金融機関識別コード
- 金融機関コード
- 銀行コード

## <a name="switzerland-ssn-ahv-number"></a>Numéro SSN AHV suisse
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Nombre à 13 chiffres

### <a name="pattern"></a>Modèle

Nombre à 13 chiffres :

- trois chiffres - 756
- un point facultatif
- quatre chiffres
- un point facultatif
- quatre chiffres
- un point facultatif
- deux chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_swiss_social_security_number_ahv trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_swiss_social_security_number_ahv est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_swiss_social_security_number_ahv trouve un contenu qui correspond au modèle.

```xml
      <!-- Swiss SSN AHV Number -->
      <Entity id="277cfa4b-6eaa-4a1b-9492-099dec849971" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_swiss_social_security_number_ahv" />
          <Match idRef="Keywords_swiss_social_security_number_ahv" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_swiss_social_security_number_ahv" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_swiss_ssn_ahv_number"></a>Keyword_swiss_ssn_AHV_number

- ahv
- ssn
- pid
- numéro d’assurance
- personalidno #
- numéro de sécurité sociale
- numéro d’ID personnel
- n pas d’identification personnelle.
- insuranceno #
- uniqueidno #
- n d’identification unique.
- numéro avs
- identité personnelle no versicheicheichesnummer
- identifikationsnummer
- einzigartige identität nicht
- sozialversicheyousnummer
- identification personnelle id
- numéro de sécurité sociale


## <a name="taiwan-national-identification-number"></a>Numéro d’identification national Taïwan

### <a name="format"></a>Format

une lettre (en anglais) suivie de neuf chiffres

### <a name="pattern"></a>Modèle

une lettre (en anglais) suivie de neuf chiffres :
- une lettre (en anglais, ne doit pas être sensible à la cas)
- le chiffre « 1 » ou « 2 »
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée dans la détection de ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_taiwanese_national_id trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_taiwanese_national_id est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_taiwanese_national_id trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Taiwanese National ID -->
<Entity id="4C7BFC34-8DD1-421D-8FB7-6C6182C2AF03" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_taiwanese_national_id" />
          <Match idRef="Keyword_taiwanese_national_id" />
      </Pattern>
       <Pattern confidenceLevel="75">
         <IdMatch idRef="Func_taiwanese_national_id" />
       </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_taiwan_national_id"></a>Keyword_taiwan_national_id

- 身份證字號
- 身份證
- 身份證號碼
- 身份證號
- 身分證字號
- 身分證
- 身分證號碼
- 身份證號
- 身分證統一編號
- 國民身分證統一編號
- 簽名
- 蓋章
- 簽名或蓋章
- 簽章

## <a name="taiwan-passport-number"></a>Numéro de passeport Taïwan

### <a name="format"></a>Format

- numéro de passeport biométrique : neuf chiffres
- Numéro de passeport non biométrique : neuf chiffres

### <a name="pattern"></a>Modèle
numéro de passeport biométrique :
- caractère « 3 »
- huit chiffres

Numéro de passeport non biométrique :
- neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_taiwan_passport trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_taiwan_passport est trouvé.

```xml
<!-- Taiwan Passport Number -->
<Entity id="e7251cb4-4c2c-41df-963e-924eb3dae04a" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_passport"/>
     <Match idRef="Keyword_taiwan_passport"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_taiwan_passport"></a>Keyword_taiwan_passport

- ROC passport number
- Passport number
- Passport no
- Passport Num
- Passport #
- 护照
- 中華民國護照
- Zhōnghuá Mínguó hùzhào

## <a name="taiwan-resident-certificate-arctarc-number"></a>Numéro de certificat taïwanais (ARC/TARC)

### <a name="format"></a>Format

10 lettres et chiffres

### <a name="pattern"></a>Modèle

10 lettres et chiffres :
- deux lettres (ne sont pas sensibles à la majuscule)
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_taiwan_resident_certificate trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_taiwan_resident_certificate est trouvé.

```xml
<!-- Taiwan Resident Certificate (ARC/TARC) -->
<Entity id="48269fec-05ea-46ea-b326-f5623a58c6e9" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_resident_certificate"/>
     <Match idRef="Keyword_taiwan_resident_certificate"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_taiwan_resident_certificate"></a>Keyword_taiwan_resident_certificate

- Resident Certificate
- Resident Cert
- Resident Cert.
- Identification card
- Alien Resident Certificate
- ARC
- Taiwan Area Resident Certificate
- TARC
- 居留證
- 外僑居留證
- 台灣地區居留證

## <a name="thai-population-identification-code"></a>Code d’identification de population thaï

### <a name="format"></a>Format

13 chiffres

### <a name="pattern"></a>Modèle

13 chiffres :
- le premier chiffre n’est pas zéro ou neuf
- 12 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_Thai_Citizen_Id trouve un contenu qui correspond au modèle.
- Un mot clé de Keyword_Thai_Citizen_Id est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_Thai_Citizen_Id trouve un contenu qui correspond au modèle.

```xml
<!-- Thai Citizen ID -->
-<Entity id="44ca9e86-ead7-4c5d-884a-e2eaa401515e" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
      <Match idRef="Keyword_Thai_Citizen_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_thai_citizen_id"></a>Keyword_thai_citizen_Id

- ID Number
- Numéro d’identification
- บัตรประชาชน
- รหัสบัตรประชาชน
- บัตรประชาชน
- รหัสบัตรประชาชน

## <a name="turkish-national-identification-number"></a>Numéro d’identification national turc

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_Turkish_National_Id trouve un contenu qui correspond au modèle.
- Un mot clé de Keyword_Turkish_National_Id est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_Turkish_National_Id trouve un contenu qui correspond au modèle.

```xml
<!-- Turkish National Identity -->
-<Entity id="fb621f20-3876-4cfc-acec-8c8e73ca32c7" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Turkish_National_Id"/>
      <Match idRef="Keyword_Turkish_National_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Turkish_National_Id"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_turkish_national_id"></a>Keyword_turkish_national_id

- TC Kimlik No
- TC Kimlik nuýsı
- Vattcşlık nuşsı
- Vatşlık no

## <a name="uk-drivers-license-number"></a>Royaume-Uni numéro de permis de conduire

### <a name="format"></a>Format

Combinaison de 18 lettres et chiffres au format spécifié

### <a name="pattern"></a>Modèle

18 lettres et chiffres
- Cinq lettres (ne sensibles à la majuscule) ou le chiffre « 9 » à la place d’une lettre.
- Un chiffre.
- Cinq chiffres au format de date MMDDY pour la date de naissance. Le septième caractère est incrémenté de 50 si le pilote est une femme ; pour examen, 51 à 62 au lieu de 01 à 12.
- Deux lettres (ne sensibles à la majuscule) ou le chiffre « 9 » à la place d’une lettre.
- Cinq chiffres.

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_uk_drivers_license` trouve un contenu qui correspond au modèle.
- Un mot clé est `Keywords_eu_driver's_license_number` trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction `Func_uk_drivers_license` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
    <!-- U.K. Driver's License Number -->
    <Entity id="f93de4be-d94c-40df-a8be-461738047551" patternsProximity="300" recommendedConfidence="75" relaxProximity="true" >
      <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_uk_drivers_license" />
          <Match idRef="Keywords_eu_driver's_license_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_uk_drivers_license" />
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver’s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- lic du pilote
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- lic du pilote
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- lic du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- permis de conduire
- permis de conduire
- permis de conduire
- conduite lic
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl


## <a name="uk-electoral-roll-number"></a>Royaume-Uni numéro de liste électorale

### <a name="format"></a>Format

deux lettres suivies de 1 à 4 chiffres

### <a name="pattern"></a>Modèle

deux lettres (ne faisant pas l’affaire) suivies de 1 à 4 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_uk_electoral trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_uk_electoral est trouvé.

```xml
<!-- U.K. Electoral Number -->
<Entity id="a3eea206-dc0c-4f06-9e22-aa1be3059963" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_uk_electoral" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_electoral" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_uk_electoral"></a>Keyword_uk_electoral

- nomination au conseil
- formulaire de nomination
- registre électoral
- liste électorale


## <a name="uk-national-health-service-number"></a>Royaume-Uni numéro de service de santé national

### <a name="format"></a>Format

10 à 17 chiffres séparés par des espaces

### <a name="pattern"></a>Modèle

10 à 17 chiffres :
- 3 ou 10 chiffres
- un espace
- trois chiffres
- un espace
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_uk_nhs_number trouve un contenu qui correspond au modèle.
- L’une des affirmations suivantes est vraie :
    - Un mot clé figurant dans la liste Keyword_uk_nhs_number est trouvé.
    - Un mot clé figurant dans la liste Keyword_uk_nhs_number1 est trouvé.
    - Un mot clé figurant dans la liste Keyword_uk_nhs_number_dob est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- U.K. NHS Number -->
<Entity id="3192014e-2a16-44e9-aa69-4b20375c9a78" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nhs_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_nhs_number" />
          <Match idRef="Keyword_uk_nhs_number1" />
          <Match idRef="Keyword_uk_nhs_number_dob" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- service national de santé
- nhs
- administration des services de santé
- administration de la santé

#### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- id du patient
- identification du patient
- n° patient
- numéro de patient

#### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- GP
- DOB
- D.O.B
- Date of Birth
- Birth Date

## <a name="uk-national-insurance-number-nino"></a>Royaume-Uni numéro d’assurance national (NINO)
Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles Numéro d’identification national de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

sept caractères ou neuf caractères séparés par des espaces ou des tirets

### <a name="pattern"></a>Modèle

deux modèles possibles :

- deux lettres (les NINOs valides utilisent uniquement certains caractères dans ce préfixe, que ce modèle valide ; ne sont pas sensibles à la cas)
- six chiffres
- « A » (A), « B », « C » ou « D » (comme le préfixe, seuls certains caractères sont autorisés dans le suffixe ; ne sont pas sensibles à la cas)

OR

- deux lettres
- un espace ou un tiret
- deux chiffres
- un espace ou un tiret
- deux chiffres
- un espace ou un tiret
- deux chiffres
- un espace ou un tiret
- « A » (A), « B » (B), « C » (C) ou « D »

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_uk_nino trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_uk_nino est trouvé.

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_uk_nino trouve un contenu qui correspond au modèle.

```xml
    <!-- U.K. NINO -->
    <Entity id="16c07343-c26f-49d2-a987-3daf717e94cc" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nino" />
        <Match idRef="Keyword_uk_nino" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_uk_nino" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_uk_nino"></a>Keyword_uk_nino

- numéro d’assurance nationale
- cotisations sociales
- loi sur la protection
- insurance
- numéro de sécurité sociale
- demande d’assurance
- demande de soins médicaux
- assurance sociale
- soins médicaux
- sécurité sociale
- grande-bretagne
- Numéro NI
- NON.
- NI #
- NI #
- insurance #
- insurancenumber
- nationalinsurance #
- nationalinsurancenumber


## <a name="uk-unique-taxpayer-reference-number"></a>Royaume-Uni Numéro de référence du contribuable unique
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

10 chiffres sans espaces et délimiteur


### <a name="pattern"></a>Modèle

10 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction  `Func_uk_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé est  `Keywords_uk_eu_tax_file_number` trouvé.

```xml
      <!-- U.K. Unique Taxpayer Reference Number -->
      <Entity id="ad4a8116-0db8-439a-b545-6d967642f0ec" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_uk_eu_tax_file_number" />
          <Match idRef="Keywords_uk_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_uk_eu_tax_file_number"></a>Keywords_uk_eu_tax_file_number

- numéro de taxe
- fichier fiscal
- id fiscal
- pas d’identification fiscale
- numéro d’identification fiscale
- pas de taxe #
- pas de taxe
- numéro d’enregistrement des taxes
- tld #
- todno #
- Erdnumber #
- taxno #
- numéro de taxe #
- numéro de taxe
- tin id
- tin no
- tin #

## <a name="us-bank-account-number"></a>Numéro de compte bancaire américain

### <a name="format"></a>Format

6 à 17 chiffres

### <a name="pattern"></a>Modèle

6 à 17 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’expression régulière Regex_usa_bank_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_usa_Bank_Account est trouvé.

```xml
<!-- U.S. Bank Account Number -->
<Entity id="a2ce32a8-f935-4bb6-8e96-2a5157672e2c" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_usa_bank_account_number" />
        <Match idRef="Keyword_usa_Bank_Account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_usa_bank_account"></a>Keyword_usa_Bank_Account

- Numéro de compte courant
- Compte courant
- # compte courant
- Numéro compte courant
- # compte courant
- N° de compte courant
- N° de compte courant
- Numéro de compte bancaire
- # Compte bancaire
- Numéro de compte bancaire
- # Compte bancaire
- N° de compte bancaire
- N° de compte bancaire
- Numéro de compte d’épargne
- Compte d’épargne.
- N° de compte d’épargne
- Numéro de compte d’épargne
- # compte d’épargne
- N° de compte d’épargne
- N° de compte d’épargne
- Numéro de compte de débit
- Compte de débit
- # Compte de débit
- Numéro de compte de débit
- # Compte de débit
- N° de compte de débit
- N° de compte de débit

## <a name="us-drivers-license-number"></a>Numéro de permis de conduire américain

### <a name="format"></a>Format

Dépend de l’État

### <a name="pattern"></a>Modèle

dépend de l’état ( par exemple, New York :
- neuf chiffres formatés comme ddd ddd ddd correspondront.
- neuf chiffres comme dddddddddd ne correspondent pas.

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_new_york_drivers_license_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_[state_name]_drivers_license_name est trouvé.
- Un mot clé figurant dans la liste Keyword_us_drivers_license est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_new_york_drivers_license_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_[state_name]_drivers_license_name est trouvé.
- Un mot clé figurant dans la liste Keyword_us_drivers_license_abbreviations est trouvé.
- Aucun mot clé figurant dans la liste Keyword_us_drivers_license n’est trouvé.

```xml
<Entity id="dfeb356f-61cd-459e-bf0f-7c6d28b458c6 patternsProximity="300">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license" />
    </Pattern>
    <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license_abbreviations" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_us_drivers_license" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_us_drivers_license_abbreviations"></a>Keyword_us_drivers_license_abbreviations

- DL
- DLS
- CDL
- CDLS
- ID
- ID
- DL #
- DLS #
- CDL #
- CDLS #
- ID #
- ID #
- Numéro d’identification
- Numéros d’identification
- LIC
- LIC #

#### <a name="keyword_us_drivers_license"></a>Keyword_us_drivers_license

- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- DriversLic
- DriversLics
- DriversLicense
- DriversLicenses
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Driver’Lic
- Driver’Lics
- Permis de conduire
- Permis de conduire
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Driver’sLic
- Driver’sLics
- Driver’sLicense
- Driver’sLicenses
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Driver’s Licenses
- numéro d’identification
- numéros d’identification
- # identification
- carte d’identité
- cartes d’identité
- carte d’identification
- cartes d’identification
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- DriversLic #
- DriversLics #
- DriversLicense #
- DriversLicenses #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- Driver’Lic #
- Driver’Lics #
- Permis de conduire #
- Permis de conduire #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- Driver’sLic #
- Driver’sLics #
- Driver’sLicense #
- Driver’sLicenses #
- #Permisconduire
- #Permisconduire
- #Permis de conduire
- #Permis de conduire
- # carte d’identité
- # cartes d’identité
- #carte d’identification
- #cartes d’identification


#### <a name="keyword_state_name_drivers_license_name"></a>Keyword_[state_name]_drivers_license_name

- abréviation de l’état (par exemple, « NY »)
- nom de l’état (par exemple, « New York »)

## <a name="us-individual-taxpayer-identification-number-itin"></a>Numéro d’identification du contribuable individuel américain (ITIN)

### <a name="format"></a>Format

neuf chiffres qui commencent par un « 9 » et contiennent un « 7 » ou « 8 » comme quatrième chiffre, éventuellement formatés avec des espaces ou des tirets

### <a name="pattern"></a>Modèle

formaté :
- le chiffre « 9 »
- deux chiffres
- un espace ou un tiret
- un « 7 » ou « 8 »
- un chiffre
- un espace ou un tiret
- quatre chiffres

non formaté :
- le chiffre « 9 »
- deux chiffres
- un « 7 » ou « 8 »
- cinq chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_formatted_itin trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_itin est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_unformatted_itin trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_itin est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_formatted_itin ou Func_unformatted_itin trouve un contenu qui correspond au modèle.

```xml
    <!-- U.S. Individual Taxpayer Identification Number (ITIN) -->
    <Entity id="e55e2a32-f92d-4985-a35d-a0b269eb687b" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_formatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_formatted_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_unformatted_itin" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_itin"></a>Keyword_itin

- contribuable
- id fiscal
- identification fiscale
- itin
- i.t.i.n.
- ssn
- tin
- sécurité sociale
- contribuable
- itins
- tld
- contribuable individuel


## <a name="us-social-security-number-ssn"></a>Numéro de sécurité sociale (SSN) des États-Unis

### <a name="format"></a>Format

neuf chiffres, qui peuvent être dans un modèle formaté ou sans mise en forme

> [!NOTE]
> La mise en forme d’un numéro de sécurité sociale émis avant le milieu de l’année 2011 est fixe et certaines parties du numéro doivent se situer dans certaines plages pour qu’il soit valide (mais il n’y a pas de somme de contrôle).

### <a name="pattern"></a>Modèle

quatre fonctions recherchent des SSN dans quatre modèles différents :
- Func_ssn recherche des numéros de sécurité sociale avec une mise en forme fixe d’avant l’année 2011, mis en forme avec des tirets ou des espaces (ddd-dd-dddd OU ddd dd dddd)
- Func_unformatted_ssn recherche des numéros de sécurité sociale avec une mise en forme fixe d’avant l’année 2011, avec neuf chiffres consécutifs non mis en forme (ddddddddd)
- Func_randomized_formatted_ssn recherche des numéros de sécurité sociale d’après l’année 2011, mis en forme avec des tirets ou des espaces  (ddd-dd-dddd OU ddd dd dddd)
- Func_randomized_unformatted_ssn recherche des numéros de sécurité sociale d’après l’année 2011, avec neuf chiffres consécutifs non mis en forme (ddddddddd)

### <a name="checksum"></a>Somme de contrôle

Non


### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_ssn trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ssn est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_unformatted_ssn trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ssn est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_randomized_formatted_ssn trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ssn est trouvé.

Une stratégie DLP a peu de confiance qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_randomized_unformatted_ssn trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ssn est trouvé.


```xml
<!-- U.S. Social Security Number (SSN) -->
  <Entity id="a44669fe-0d48-453d-a9b1-2cc83f2cba77" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_randomized_formatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="55">
        <IdMatch idRef="Func_randomized_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
  </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_ssn"></a>Keyword_ssn

- Numéro SSA
- numéro de sécurité sociale
- sécurité sociale #
- sécurité sociale #
- non de sécurité sociale
- # sécurité sociale
- Sécu sociale
- SSN
- SSNS
- SSN #
- SS #
- SSID

## <a name="us--uk-passport-number"></a>États-Unis/Royaume-Uni numéro de passeport

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

- une lettre ou un chiffre
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_usa_uk_passport trouve un contenu qui correspond au modèle.
- Mot clé à partir `Keywords_eu_passport_number` de ou `Keywords_uk_eu_passport_number` est trouvé.
- Un mot clé est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- La fonction Func_usa_uk_passport trouve un contenu qui correspond au modèle.
- Mot clé à partir `Keywords_eu_passport_number` de ou `Keywords_uk_eu_passport_number` est trouvé.

```xml
    <!-- U.S. / U.K. Passport Number -->
    <Entity id="178ec42a-18b4-47cc-85c7-d62c92fd67f8" patternsProximity="300" recommendedConfidence="75">
       <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- passport #
- passport #
- passportid
- passports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- passport britannique
- uk passport


## <a name="ukraine-passport-domestic"></a>Passeport ukrainien national
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’Regex_Ukraine_Passport_Domestic recherche le contenu qui correspond au modèle.
- Un mot clé de Keyword_Ukraine_Passport_Domestic est trouvé.

```xml
      <!-- Ukraine Passport Domestic -->
      <Entity id="1817a540-221f-4459-9202-3bd78b81d803" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_Ukraine_Passport_Domestic"/>
          <Match idRef="Keyword_Ukraine_Passport_Domestic"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_ukraine_passport_domestic"></a>Keyword_ukraine_passport_domestic

- passport ukraine
- numéro de passeport
- passport no
- паспорт України
- номер паспорта
- персональний


## <a name="ukraine-passport-international"></a>Passeport ukrainien international
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications cloud Microsoft

### <a name="format"></a>Format

Modèle alphanumérique à huit caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique à huit caractères :
- deux lettres ou chiffres
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a un niveau de confiance moyen qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
- L’Regex_Ukraine_Passport_International regex trouve un contenu qui correspond au modèle.
- Un mot clé de Keyword_Ukraine_Passport_International est trouvé.

```xml
      <!-- Ukraine Passport International -->
      <Entity id="cfbe032d-22e0-4f28-ab68-d66e9641f1e2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Ukraine_Passport_International"/>
          <Match idRef="Keyword_Ukraine_Passport_International"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_ukraine_passport_international"></a>Keyword_ukraine_passport_international

- passport ukraine
- numéro de passeport
- passport no
- паспорт України
- номер паспорта
