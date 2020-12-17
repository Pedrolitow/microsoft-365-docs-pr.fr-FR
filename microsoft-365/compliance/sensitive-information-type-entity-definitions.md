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
localization_priority: Normal
ms.collection:
- M365-security-compliance
hideEdit: true
feedback_system: None
description: La protection contre la perte de données (DLP) dans le centre de sécurité &amp; conformité inclut 80 types d’informations sensibles que vous pouvez utiliser dans vos stratégies DLP. Cette rubrique répertorie tous ces types d'informations sensibles et indique ce qu'une stratégie DLP recherche pour chaque type.
ms.openlocfilehash: cb45d613da95c977f56b82e64ad3332434e08cd8
ms.sourcegitcommit: 884ac262443c50362d0c3ded961d36d6b15d8b73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49698507"
---
# <a name="sensitive-information-type-entity-definitions"></a>Définitions d’entités des types d’informations sensibles

La protection contre la perte de données (DLP) dans le centre de conformité comprend de nombreux types d’informations sensibles que vous pouvez utiliser dans vos stratégies DLP. Cette rubrique répertorie tous ces types d'informations sensibles et indique ce qu'une stratégie DLP recherche pour chaque type. Un type d'informations sensibles est défini par un modèle qui peut être identifié par une fonction ou une expression régulière. En outre, des preuves corroborantes comme les mots clés et les sommes de contrôle peuvent être utilisées pour identifier un type d'informations sensibles. La proximité et le niveau de confiance sont également utilisés dans le processus d'évaluation.

Les types d’informations sensibles nécessitent l’un de ces abonnements :
- Microsoft 365 E3
- Microsoft 365 E5

## <a name="aba-routing-number"></a>Numéro d’acheminement ABA

### <a name="format"></a>Format

neuf chiffres pouvant être mis en forme ou non mis en forme

### <a name="pattern"></a>Modèle

Avec
- quatre chiffres commençant par 0, 1, 2, 3, 6, 7 ou 8
- un trait d’Union
- quatre chiffres
- un trait d’Union
- un chiffre

Non mis en forme : neuf chiffres consécutifs commençant par 0, 1, 2, 3, 6, 7 ou 8 

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_aba_routing trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ABA_Routing est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
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
- ABA #
- ABA
- abarouting #
- abaroutingnumber
- americanbankassociationrouting #
- americanbankassociationroutingnumber
- bankrouting #
- bankroutingnumber
- positionnement #
- n ° de routage
- Numéro d’acheminement
- numéro de routage
- positionnement #
- RTN


## <a name="argentina-national-identity-dni-number"></a>Numéro d’identité nationale (DNI) Argentine

### <a name="format"></a>Format

Huit chiffres avec ou sans points

### <a name="pattern"></a>Modèle

Huit chiffres :
- deux chiffres
- un point facultatif
- trois chiffres
- un point facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- cédula 
- DNI 
- Documento Nacional de identidad 
- Documento número 
- Numéro de Documento 
- Registro Nacional de las personnes 
- rnp 
   
## <a name="australia-bank-account-number"></a>Numéro de compte bancaire australien

### <a name="format"></a>Format

six à dix chiffres avec ou sans numéro de succursale d’état bancaire

### <a name="pattern"></a>Modèle

Le numéro de compte est compris entre six et dix chiffres.

Numéro de succursale bancaire en Australie :
- trois chiffres 
- un trait d’Union 
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_australia_bank_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_australia_bank_account_number est trouvé.
- L’expression régulière Regex_australia_bank_account_number_bsb trouve un contenu qui correspond au modèle.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- auront

## <a name="australia-business-number"></a>Numéro d’entreprise Australie
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft


### <a name="format"></a>Format

11 chiffres avec des délimiteurs facultatifs

### <a name="pattern"></a>Modèle

11 chiffres avec des délimiteurs facultatifs :

- deux chiffres
- un trait d’Union ou un espace conditionnel
- trois chiffres
- un trait d’Union ou un espace conditionnel
- trois chiffres
- un trait d’Union ou un espace conditionnel
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_australian_business_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_australian_business_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_australian_business_number trouve le contenu qui correspond au modèle.

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

- n ° d’entreprise Australie
- numéro professionnel
- ABN #
- businessid #
- ID d’entreprise
- ABN
- businessno #

## <a name="australia-company-number"></a>Numéro de société Australie
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

neuf chiffres avec des délimiteurs

### <a name="pattern"></a>Modèle

neuf chiffres avec des délimiteurs :

- trois chiffres
- un espace
- trois chiffres
- un espace
- trois chiffres


### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_Australian_Company_Number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keyword_Australian_Company_Number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- La fonction Func_Australian_Company_Number trouve le contenu qui correspond au modèle.

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

- suffit
- n ° de société Australie
- n ° de société Australie #
- Numéro de société Australie
- Numéro de société australien
- Numéro de société australien #
- Numéro de société australien

## <a name="australia-drivers-license-number"></a>Numéro de permis de conduire Australie

### <a name="format"></a>Format

neuf lettres et chiffres

### <a name="pattern"></a>Modèle

neuf lettres et chiffres : 

- deux chiffres ou lettres (ne respectant pas la casse) 
- deux chiffres 
- cinq chiffres ou lettres (ne respectant pas la casse)

OR

- une à deux lettres facultatives (ne respectant pas la casse) 
- quatre à neuf chiffres

OR

- neuf chiffres ou lettres (ne respectant pas la casse)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- Driver'Lic
- Driver'Lics
- Driver'Licence
- Driver'Licences
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Driver'sLic
- Driver'sLics
- Driver'sLicence
- Driver'sLicences
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
- Driver'Lic #
- Driver'Lics #
- Driver'Licence #
- Driver'Licences #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- Driver'sLic #
- Driver'sLics #
- Driver'sLicence #
- Driver'sLicences #
- #Permisconduire
- #Permisconduire
- #Permis de conduire
- #Permis de conduire 

#### <a name="keyword_australia_drivers_license_number_exclusions"></a>Keyword_australia_drivers_license_number_exclusions

- AAA
- DriverLicense
- DriverLicenses
- Permis de conduire
- Permis de conduire
- DriversLicense
- DriversLicenses
- Permis de conduire
- Permis de conduire
- Driver'License
- Driver'Licenses
- Permis de conduire
- Permis de conduire
- Driver'sLicense
- Driver'sLicenses
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
- Driver'License #
- Driver'Licenses #
- #Permis de conduire
- #Permis de conduire
- Driver'sLicense #
- Driver'sLicenses #
- #Permis de conduire
- #Permis de conduire
   
## <a name="australia-medical-account-number"></a>Numéro de compte médical Australie

### <a name="format"></a>Format

10 à 11 chiffres

### <a name="pattern"></a>Modèle

10 à 11 chiffres :
- le premier chiffre se trouve dans la plage 2-6
- neuvième chiffre est un chiffre de contrôle
- le dixième chiffre est le chiffre de l’émission
- le onzième chiffre (facultatif) est le numéro individuel

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
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
- médicaux

   
## <a name="australia-passport-number"></a>Numéro de passeport Australie

### <a name="format"></a>Format

Une lettre suivie de sept chiffres

### <a name="pattern"></a>Modèle

Une lettre (ne respectant pas la casse) suivie de sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_australia_passport_number trouve un contenu qui correspond au modèle.
- Un mot clé depuis Keyword_passport ou Keyword_australia_passport_number est trouvé.

```xml
<!-- Australia Passport Number -->
<Entity id="29869db6-602d-4853-ab93-3484f905df50" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_passport_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_passport" />
          <Match idRef="Keyword_australia_passport_number" />
        </Any>
   </Pattern>
</Entity>   
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_passport"></a>Keyword_passport

- Numéro de passeport
- N° de passeport
- # Passeport
- Tel #
- PassportID
- N ° passeport
- passportnumber
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃ 
- Numéro de passeport
- Passeport n°
- Passeport numéro
- # Passeport
- Passeport #
- PasseportNon
- Passeportn °

#### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

- tel
- informations sur le passeport
- immigration et citoyenneté
- Australie
- service de l’immigration
- adresse de résidence
- service de l’immigration et de la citoyenneté
- délivrance
- Carte nationale d’identité
- numéro de passeport
- document de voyage
- autorité émettrice
   
## <a name="australia-tax-file-number"></a>Numéro de fichier fiscal Australie

### <a name="format"></a>Format

huit à neuf chiffres

### <a name="pattern"></a>Modèle

huit à neuf chiffres généralement présentés par des espaces, comme suit :
- trois chiffres 
- un espace facultatif 
- trois chiffres 
- un espace facultatif 
- deux à trois chiffres où le dernier chiffre est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
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

## <a name="austria-drivers-license-number"></a>Numéro de permis de conduire autrichien

### <a name="format"></a>Format

huit chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

huit chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- L’expression régulière  `Regex_austria_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_austria_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_austria_eu_drivers_license_number"></a>Keywords_austria_eu_driver’s_license_number

- Fuhrerschein
- Führerschein
- Führerscheine
- Führerscheinnummer
- Führerscheinnummern

## <a name="austria-identity-card"></a>Carte d’identité Autriche
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

Combinaison de 24 caractères de lettres, de chiffres et de caractères spéciaux
  
### <a name="pattern"></a>Modèle

24 caractères :
  
-  22 lettres (ne respectent pas la casse), chiffres, barres obliques inverses, barres obliques ou signes plus 
    
- deux lettres (ne respectent pas la casse), des chiffres, des barres obliques inverses, des barres obliques, des signes plus ou des signes égal
    
### <a name="checksum"></a>Somme de contrôle

Non applicable
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- L’expression régulière  `Regex_austria_eu_national_id_card` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_austria_eu_national_id_card` est trouvé. 
   
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

- Numéro d’identité
- id national
- personalausweis republik österreich

## <a name="austria-passport-number"></a>Numéro de passeport autrichien
Cette entité de type d’informations sensibles est uniquement disponible dans le type sensitiveinformation de numéro de passeport UE.

### <a name="format"></a>Format

Une lettre suivie d’un espace facultatif et de sept chiffres
  
### <a name="pattern"></a>Modèle

Une combinaison d’une lettre, de sept chiffres et d’un espace :
  
- une lettre (ne respecte pas la casse)
- un espace (facultatif)
- sept chiffres
    
### <a name="checksum"></a>Somme de contrôle

non applicable
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_austria_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_austria_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_austria_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
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

## <a name="austria-social-security-number-or-equivalent-identification"></a>Numéro de sécurité sociale autrichien ou identification équivalente
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’information de numéro de sécurité sociale ou d’ID équivalent.

### <a name="format"></a>Format

10 chiffres au format spécifié
  
### <a name="pattern"></a>Modèle

10 chiffres :
  
- trois chiffres correspondant à un numéro de série 
- un chiffre de contrôle
- six chiffres correspondant à la date de naissance (JJMMAA)
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction’Func_austria_eu_
- _or_equivalent’trouve le contenu qui correspond au modèle. 
- un mot clé from  `Keywords_austria_eu_ssn_or_equivalent` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_austria_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
    
```xml
 <!-- EU SSN or Equivalent Number -->
<Entity id="d24e32a4-c0bb-4ba8-899d-6303b95742d9" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_austria_eu_ssn_or_equivalent" />
        </Pattern>
<Pattern confidenceLevel="75">
            <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_austria_eu_ssn_or_equivalent"></a>Keywords_austria_eu_ssn_or_equivalent

- Numéro de sécurité sociale
- numéro de sécurité sociale
- code de sécurité sociale
- Numéro d’assurance
- Numéro de sécurité sociale autrichien
- SSN #
- SSN
- code d’assurance
- code d’assurance #
- socialsecurityno #
- sozialversicherungsnummer
- soziale sicherheit kein
- versicherungsnummer

## <a name="austria-tax-identification-number"></a>Numéro d’identification fiscale autrichienne

### <a name="format"></a>Format

neuf chiffres avec un trait d’union conditionnel et une barre oblique
  
### <a name="pattern"></a>Modèle

neuf chiffres avec un trait d’Union et une barre oblique facultatifs :
  
- deux chiffres
- un trait d’Union (facultatif)
- trois chiffres
- une barre oblique (facultatif)
- quatre chiffres
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_austria_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_austria_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- La fonction  `Func_austria_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
    
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
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #
- Numéro de taxe
 
## <a name="austria-value-added-tax"></a>Taxe sur la valeur ajoutée autrichienne
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

modèle alphanumérique de 11 caractères

### <a name="pattern"></a>Modèle

modèle alphanumérique de 11 caractères :

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

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_Austria_Value_Added_Tax trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keyword_Austria_Value_Added_Tax est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_Austria_Value_Added_Tax trouve le contenu qui correspond au modèle.

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

- Numéro de TVA
- compt #
- Numéro de TVA autrichien
- n ° TVA
- vatno #
- Numéro de taxe sur la valeur ajoutée
- TVA autrichienne
- mwst
- umsatzsteuernummer
- mwstnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- Numéro d’identification de TVA
- numéro ATU
- Numéro d’UID


## <a name="azure-documentdb-auth-key"></a>Clé d’authentification Azure DocumentDB

### <a name="format"></a>Format

La chaîne « DocumentDb » suivie des caractères et des chaînes présentés dans le modèle ci-dessous.

### <a name="pattern"></a>Modèle

- La chaîne « DocumentDb »
- N’importe quelle combinaison entre 3-200 majuscules ou minuscules, des chiffres, des symboles, des caractères spéciaux ou des espaces
- Symbole supérieur à (>), signe égal (=), guillemet (") ou apostrophe (')
- Toute combinaison de 86 lettres majuscules ou minuscules, des chiffres, une barre oblique (/) ou un signe plus (+)
- Deux signes égal (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureDocumentDBAuthKey trouve le contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve **pas** le contenu qui correspond au modèle.

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

(Notez que techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- société
- Northwind
- immédiatement
- onebox
- hôte
- bouclage
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->NET

## <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>Chaîne de connexion à la base de données IAAS Azure et chaîne de connexion Azure SQL

### <a name="format"></a>Format

La chaîne « Server », « Server » ou « Data source » suivie des caractères et des chaînes décrits dans le modèle ci-dessous, y compris la chaîne «cloudapp. Azure.<!--no-hyperlink-->com» ou «cloudapp. Azure.<!--no-hyperlink-->NET "ou" Database. Windows.<!--no-hyperlink-->NET ", et la chaîne" password "ou" password "ou" PWD ".

### <a name="pattern"></a>Modèle

- chaîne « serveur », « serveur » ou « source de données »
- zéro à deux espaces
- signe égal (=)
- zéro à deux espaces
- n’importe quelle combinaison entre 1-200 majuscules ou minuscules, des chiffres, des symboles, des caractères spéciaux ou des espaces
- La chaîne «cloudapp. Azure.<!--no-hyperlink-->com "," cloudapp. Azure.<!--no-hyperlink-->NET "ou" Database. Windows.<!--no-hyperlink-->NET
- n’importe quelle combinaison entre 1-300 majuscules ou minuscules, des chiffres, des symboles, des caractères spéciaux ou des espaces
- la chaîne "password", "password" ou "PWD"
- zéro à deux espaces
- signe égal (=)
- zéro à deux espaces
- un ou plusieurs caractères qui ne sont pas des points-virgules (;), guillemets (") ou apostrophe (')
- un point-virgule (;), guillemet (") ou apostrophe (')

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureConnectionString trouve le contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve **pas** le contenu qui correspond au modèle.

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

(Notez que techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- société
- Northwind
- immédiatement
- onebox
- hôte
- bouclage
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->NET

## <a name="azure-iot-connection-string"></a>Chaîne de connexion Azure IoT

### <a name="format"></a>Format

La chaîne « nomhôte » suivie des caractères et des chaînes décrits dans le modèle ci-dessous, y compris les chaînes «Azure-appareils.<!--no-hyperlink-->NET "et" SharedAccessKey ".

### <a name="pattern"></a>Modèle

- la chaîne « nomhôte »
- zéro à deux espaces
- signe égal (=)
- zéro à deux espaces
- n’importe quelle combinaison entre 1-200 majuscules ou minuscules, des chiffres, des symboles, des caractères spéciaux ou des espaces
- la chaîne «Azure-appareils.<!--no-hyperlink-->NET
- n’importe quelle combinaison entre 1-200 majuscules ou minuscules, des chiffres, des symboles, des caractères spéciaux ou des espaces
- la chaîne « SharedAccessKey »
- zéro à deux espaces
- signe égal (=)
- zéro à deux espaces
- toute combinaison de 43 lettres majuscules ou minuscules, des chiffres, une barre oblique (/) ou un signe plus (+)
- signe égal (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureIoTConnectionString trouve le contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve **pas** le contenu qui correspond au modèle.

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

(Notez que techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- société
- Northwind
- immédiatement
- onebox
- hôte
- bouclage
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->NET

## <a name="azure-publish-setting-password"></a>Mot de passe de paramètre de publication Azure

### <a name="format"></a>Format

La chaîne « userpwd = » suivie d’une chaîne alphanumérique.

### <a name="pattern"></a>Modèle

- la chaîne « userpwd = »
- n’importe quelle combinaison de 60 lettres minuscules ou chiffres
- guillemet (")

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzurePublishSettingPasswords trouve le contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve **pas** le contenu qui correspond au modèle.


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

(Notez que techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- société
- Northwind
- immédiatement
- onebox
- hôte
- bouclage
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->NET

## <a name="azure-redis-cache-connection-string"></a>Chaîne de connexion au cache des inversions Azure

### <a name="format"></a>Format

La chaîne «ReDim. cache. Windows.<!--no-hyperlink-->NET "suivi des caractères et des chaînes décrits dans le modèle ci-dessous, y compris la chaîne" password "ou" PWD ".

### <a name="pattern"></a>Modèle

- la chaîne «ReDim. cache. Windows.<!--no-hyperlink-->NET
- n’importe quelle combinaison entre 1-200 majuscules ou minuscules, des chiffres, des symboles, des caractères spéciaux ou des espaces
- la chaîne « password » ou « pwd »
- zéro à deux espaces
- signe égal (=)
- zéro à deux espaces
- toute combinaison de 43 caractères majuscules ou minuscules, des chiffres, une barre oblique (/) ou un signe plus (+)
- signe égal (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureRedisCacheConnectionString trouve le contenu qui correspond au modèle..
- L’expression régulière CEP_CommonExampleKeywords ne trouve **pas** le contenu qui correspond au modèle.

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

(Notez que techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- société
- Northwind
- immédiatement
- onebox
- hôte
- bouclage
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->NET

## <a name="azure-sas"></a>SAS Azure

### <a name="format"></a>Format

La chaîne « SIG » suivie des caractères et des chaînes présentés dans le modèle ci-dessous.

### <a name="pattern"></a>Modèle

- la chaîne « SIG »
- zéro à deux espaces
- signe égal (=)
- zéro à deux espaces
- toute combinaison comprise entre 43-53 caractères majuscules ou minuscules, des chiffres ou le signe pourcentage (%)
- la chaîne « % 3D »
- tout caractère qui n’est pas une lettre majuscule, un chiffre ou un signe de pourcentage (%)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureSAS trouve le contenu qui correspond au modèle.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```

## <a name="azure-service-bus-connection-string"></a>Chaîne de connexion au bus des services Azure

### <a name="format"></a>Format

La chaîne « point de terminaison » suivie des caractères et des chaînes décrits dans le modèle ci-dessous, y compris les chaînes «ServiceBus. Windows.<!--no-hyperlink-->NET "et" SharedAccesKey ".

### <a name="pattern"></a>Modèle

- chaîne « point de terminaison »
- zéro à deux espaces
- signe égal (=)
- zéro à deux espaces
- n’importe quelle combinaison entre 1-200 majuscules ou minuscules, des chiffres, des symboles, des caractères spéciaux ou des espaces
- la chaîne «ServiceBus. Windows.<!--no-hyperlink-->NET
- n’importe quelle combinaison entre 1-200 majuscules ou minuscules, des chiffres, des symboles, des caractères spéciaux ou des espaces
- la chaîne « SharedAccessKey »
- zéro à deux espaces
- signe égal (=)
- zéro à deux espaces
- toute combinaison de 43 caractères majuscules ou minuscules, des chiffres, une barre oblique (/) ou un signe plus (+)
- signe égal (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureServiceBusConnectionString trouve le contenu qui correspond au modèle..
- L’expression régulière CEP_CommonExampleKeywords ne trouve **pas** le contenu qui correspond au modèle.

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

(Notez que techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- société
- Northwind
- immédiatement
- onebox
- hôte
- bouclage
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->NET

## <a name="azure-storage-account-key"></a>Clé de compte de stockage Azure

### <a name="format"></a>Format

La chaîne « DefaultEndpointsProtocol » suivie des caractères et des chaînes décrits dans le modèle ci-dessous, y compris la chaîne « AccountKey ».

### <a name="pattern"></a>Modèle

- la chaîne « DefaultEndpointsProtocol »
- zéro à deux espaces
- signe égal (=)
- zéro à deux espaces
- n’importe quelle combinaison entre 1-200 majuscules ou minuscules, des chiffres, des symboles, des caractères spéciaux ou des espaces
- la chaîne « AccountKey »
- zéro à deux espaces
- signe égal (=)
- zéro à deux espaces
- toute combinaison de 86 caractères majuscules ou minuscules, des chiffres, une barre oblique (/) ou un signe plus (+)
- deux signes égal (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureStorageAccountKey trouve le contenu qui correspond au modèle.
- L’expression régulière CEP_AzureEmulatorStorageAccountFilter ne trouve **pas** le contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve **pas** le contenu qui correspond au modèle.

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

(Notez que techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw = =

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Notez que techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- société
- Northwind
- immédiatement
- onebox
- hôte
- bouclage
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->NET

## <a name="azure-storage-account-key-generic"></a>Clé de compte de stockage Azure (Générique)

### <a name="format"></a>Format

Toute combinaison de 86 lettres majuscules ou minuscules, des chiffres, la barre oblique (/) ou le signe plus (+), précédée ou suivie des caractères décrits dans le modèle ci-dessous.

### <a name="pattern"></a>Modèle

- zéro à l’un des symboles supérieur à (>), apostrophe ('), signe égal (=), guillemet (") ou numérique (#)
- toute combinaison de 86 caractères majuscules ou minuscules, des chiffres, la barre oblique (/) ou le signe plus (+)
- deux signes égal (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_AzureStorageAccountKeyGeneric trouve le contenu qui correspond au modèle.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```
## <a name="belgium-drivers-license-number"></a>Numéro de permis de conduire belge

### <a name="format"></a>Format

dix chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

dix chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_belgium_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis `Keywords_eu_driver's_license_number` ou `Keywords_belgium_eu_driver's_license_number` est trouvé.
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD

#### <a name="keywords_belgium_eu_drivers_license_number"></a>Keywords_belgium_eu_driver’s_license_number

- rijbewijs
- rijbewijsnummer
- Führerschein
- führerscheinnummer
- füehrerscheinnummer
- Fuhrerschein
- fuehrerschein
- fuhrerscheinnummer
- fuehrerscheinnummer
- permis de conduire
- numéro permis conduire


## <a name="belgium-national-number"></a>Numéro national belge

### <a name="format"></a>Format

11 chiffres plus des délimiteurs facultatifs

### <a name="pattern"></a>Modèle

11 chiffres plus des délimiteurs :
- six chiffres et deux points facultatifs au format YY. MM.DD pour la date de naissance 
- Délimiteur facultatif : point, tiret, espace 
- trois chiffres séquentiels (impairs pour les hommes, pairs pour les femelles) 
- Délimiteur facultatif : point, tiret, espace 
- deux chiffres de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_belgium_national_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_belgium_national_number est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
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

- aantal
- bnn #
- bnn
- carte d’identité
- identifiant national
- identifiantnational #
- identificatie
- identificateur
- identifikation
- identifikationsnummer
- identifizierung
- identité
- identiteit
- identiteitskaart
- identification
- inscriptions
- numéro national
- Registre national
- nationalnumber #
- nationalnumber
- nPour #
- nPour
- numéro d’assuré
- Numéro de registre national
- numéro de sécurité
- numéro d’identification
- numéro d’immatriculation
- numéro national
- numéronational #
- Numéro d’identification personnel
- personalausweis
- personalidnumber #
- registratie
- son
- registrationsnumme
- registrierung
- numéro de sécurité sociale
- SSN #
- SSN
- steuernummer
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #

## <a name="belgium-passport-number"></a>Numéro de passeport belge
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

deux lettres suivies de six chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

deux lettres et suivies de six chiffres
  
### <a name="checksum"></a>Somme de contrôle

non applicable
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_belgium_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_belgium_eu_passport_number` est trouvé.

```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_belgium_eu_passport_number"></a>Keywords_belgium_eu_passport_number

- numéro passeport
- paspoort Nr
- paspoort-Nr
- paspoortnummer
- paspoortnummers
- Carte passeport
- Livre de passeport
- Pass-Nr
- Passnummer
- reisepass kein

## <a name="belgium-social-security-number-or-equivalent-identification"></a>Numéro de sécurité sociale belge ou identification équivalente
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’information de numéro de sécurité sociale ou d’ID équivalent.

### <a name="format"></a>Format

11 chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

11 chiffres
  
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
  
- La fonction  `Func_belgium_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_belgium_eu_ssn_or_equivalent` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_belgium_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
    
```xml
 <!-- EU SSN or Equivalent Number -->
<Entity id="d24e32a4-c0bb-4ba8-899d-6303b95742d9" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_belgium_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_belgium_eu_ssn_or_equivalent" />
        </Pattern> 
       <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_eu_ssn_or_equivalent" />
        </Pattern>      
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_belgium_eu_ssn_or_equivalent"></a>Keywords_belgium_eu_ssn_or_equivalent

- numéro national belge
- numéro national
- numéro de sécurité sociale
- nationalnumber #
- SSN #
- SSN
- nationalnumber
- bnn #
- bnn
- Numéro d’identification personnel
- personalidnumber #
- numéro national
- numéro de sécurité
- numéro d’assuré
- identifiant national
- identifiantnational #
- numéronational #


## <a name="belgium-value-added-tax-number"></a>Valeur belge-valeur ajoutée de la taxe
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

modèle alphanumérique de 12 caractères

### <a name="pattern"></a>Modèle

modèle alphanumérique de 12 caractères :

- une lettre B ou b
- lettre E ou e
- un chiffre 0
- un chiffre compris entre 1 et 9
- un point ou un tiret ou un espace facultatif
- quatre chiffres
- un point ou un tiret ou un espace facultatif
- quatre chiffres


### <a name="checksum"></a>Somme de contrôle

Oui


### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_belgium_value_added_tax_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_belgium_value_added_tax_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_belgium_value_added_tax_number trouve le contenu qui correspond au modèle.

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

- n º TVA
- Numéro de TVA
- n ° TVA
- numéro t. v. a
- umsatzsteuer-identifikationsnummer
- umsatzsteuernummer
- btw
- btw #
- compt #


## <a name="brazil-cpf-number"></a>Numéro CPF Brésil

### <a name="format"></a>Format

11 chiffres qui incluent un chiffre de contrôle et peuvent ou non être mis en forme 

### <a name="pattern"></a>Modèle

Avec
- trois chiffres
- un point
- trois chiffres
- un point
- trois chiffres
- un trait d’Union
- deux chiffres qui sont des chiffres de contrôle

Non
- 11 chiffres où les deux derniers sont des chiffres de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_brazil_cpf trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_brazil_cpf est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- Identificateur
- Registration
- Parts
- Cadastro de Pessoas Físicas 
- Imposto 
- Identificação 
- Inscrição 
- Receita 

   
## <a name="brazil-legal-entity-number-cnpj"></a>Numéro d’entité juridique Brésil (CNPJ)

### <a name="format"></a>Format

14 chiffres qui incluent un numéro d’enregistrement, un numéro de succursale et des chiffres de contrôle, avec des délimiteurs en plus

### <a name="pattern"></a>Modèle

14 chiffres plus des délimiteurs :

- deux chiffres 
- un point 
- trois chiffres 
- un point 
- trois chiffres (ces huit premiers chiffres correspondent au numéro d’enregistrement) 
- une barre oblique 
- Numéro de succursale à quatre chiffres 
- un trait d’Union 
- deux chiffres qui sont des chiffres de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_brazil_cnpj trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_brazil_cnpj est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

   
## <a name="brazil-national-identification-card-rg"></a>Carte d’identification nationale (RG) du Brésil

### <a name="format"></a>Format

Registro Geral (ancien format) : neuf chiffres

Registro de identidade (RIC) (nouveau format) : 11 chiffres

### <a name="pattern"></a>Modèle

Registro Geral (ancien format) :
- deux chiffres 
- un point 
- trois chiffres 
- un point 
- trois chiffres 
- un trait d’Union 
- un chiffre qui est un chiffre de contrôle

Registro de identidade (RIC) (nouveau format) :
- dix chiffres 
- un trait d’Union 
- un chiffre qui est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_brazil_rg trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_brazil_rg est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_brazil_rg trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Brazil National ID Card (RG) -->
<Entity id="486de900-db70-41b3-a886-abdf25af119c" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_rg"/>
     <Match idRef="Keyword_brazil_rg"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_rg"/>
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
- RG (ce mot clé respecte la casse) 
- RIC (ce mot clé respecte la casse) 


## <a name="bulgaria-drivers-license-number"></a>Numéro de permis de conduire de la Bulgarie

### <a name="format"></a>Format

neuf chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

neuf chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_bulgaria_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_bulgaria_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_bulgaria_eu_drivers_license_number"></a>Keywords_bulgaria_eu_driver’s_license_number

- свидетелство за управление на мпс
- свидетелство за управление на моторно превозно средство
- сумпс
- шофьорска книжка
- шофьорски книжки

## <a name="bulgaria-uniform-civil-number"></a>Numéro civil uniforme de la Bulgarie
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

dix chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

dix chiffres sans espaces ni délimiteurs
  
- six chiffres correspondant à la date de naissance (AAMMJJ) 
- deux chiffres correspondant à l’ordre de naissance
- un chiffre correspondant au sexe : un chiffre pair pour le mâle et un chiffre impair pour femelle.
- un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_bulgaria_eu_national_id_card` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_bulgaria_eu_national_id_card` est trouvé. 

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_bulgaria_eu_national_id_card` trouve le contenu qui correspond au modèle. 
    
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
- bucn #
- bucn
- edinen grazhdanski nomer
- egn #
- egn
- numéro d’identification
- id national
- numéro national
- nationalnumber #
- nationalnumber
- ID personnel
- n ° personnel
- numéro personnel
- personalidnumber #
- numéro de sécurité sociale
- SSN #
- SSN
- ID civil uniforme
- non civil uniforme
- numéro civil uniforme
- uniformcivilno #
- uniformcivilno
- uniformcivilnumber #
- uniformcivilnumber
- Numéro de citoyenneté unique
- егн #
- егн
- единен граждански номер
- идентификационен номер
- личен номер
- лична идентификация
- лично не
- национален номер
- номер на гражданството
- ID униформ
- униформ граждански ID
- униформ граждански не
- униформ граждански номер
- униформгражданскиid #
- униформгражданскине. #


## <a name="bulgaria-passport-number"></a>Numéro de passeport pour la Bulgarie
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

neuf chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

neuf chiffres 
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_bulgaria_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_bulgaria_eu_passport_number` ou `Keywords_eu_passport_number_common` est trouvé. 

```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_bulgaria_eu_passport_number"></a>Keywords_bulgaria_eu_passport_number

- номер на паспорта
- номер на паспорт
- паспорт non

## <a name="canada-bank-account-number"></a>Numéro de compte bancaire canadien

### <a name="format"></a>Format

sept ou douze chiffres

### <a name="pattern"></a>Modèle

Un numéro de compte bancaire au Canada est composé de sept ou douze chiffres.

Un numéro de transit de compte bancaire du Canada est indiqué au format suivant :
- cinq chiffres 
- un trait d’Union 
- trois chiffres ou
- zéro « 0 » 
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_canada_bank_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_canada_bank_account_number est trouvé.
- L’expression régulière Regex_canada_bank_account_transit_number trouve un contenu qui correspond au modèle.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
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

   
## <a name="canada-drivers-license-number"></a>Numéro de permis de conduire Canada

### <a name="format"></a>Format

Varie selon la province

### <a name="pattern"></a>Modèle

Plusieurs modèles pour les différentes provinces : Alberta, Colombie-Britannique, Manitoba, Nouveau-Brunswick, Terre-Neuve-et-Labrador, Nouvelle-Écosse, Ontario, Île-du-Prince-Édouard, Québec et Saskatchewan

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

#### <a name="keyword_province_name_drivers_license_name"></a>Keyword_ [province_name] _drivers_license_name

- L’abréviation de la province, par exemple AB
- Le nom de la province, par exemple Alberta

#### <a name="keyword_canada_drivers_license"></a>Keyword_canada_drivers_license

- LD
- DISTRIBUTION
- CÈDE
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
- Driver'Lic
- Driver'Lics
- Driver'License
- Driver'Licenses
- Driver'Licence
- Driver'Licences
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Driver'sLic
- Driver'sLics
- Driver'sLicense
- Driver'sLicenses
- Driver'sLicence
- Driver'sLicences
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
- carte d’identification
- numéro d’identification
- numéros d’identification
- # identification
- # identification
- carte d’identification
- cartes d’identification
- identificateur 
- LD #
- DISTRIBUTION # 
- CÈDE # 
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
- Driver'Lic # 
- Driver'Lics # 
- Driver'License # 
- Driver'Licenses # 
- Driver'Licence # 
- Driver'Licences # 
- #Permis conduire 
- #Permis conduire 
- #Permis de conduire 
- #Permis de conduire 
- #Permis de conduire 
- #Permis de conduire 
- Driver'sLic # 
- Driver'sLics # 
- Driver'sLicense # 
- Driver'sLicenses # 
- Driver'sLicence # 
- Driver'sLicences # 
- #Permisconduire 
- #Permisconduire 
- #Permis de conduire 
- #Permis de conduire 
- #Permis de conduire 
- #Permis de conduire 
- Permis de conduire # 
- Réf # 
- codes # 
- #carte carte d’identification 
- #cartes carte d’identification 
- carte d’identification # 
- #carte d’identification 
- #cartes d’identification 
- identificateur # 

   
## <a name="canada-health-service-number"></a>Numéro de service d’intégrité Canada

### <a name="format"></a>Format

dix chiffres

### <a name="pattern"></a>Modèle

dix chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- psychiatrist
- indemnisation des salariés
- incapacité

      
## <a name="canada-passport-number"></a>Numéro de Passeport Canada

### <a name="format"></a>Format

deux lettres majuscules suivies de six chiffres

### <a name="pattern"></a>Modèle

deux lettres majuscules suivies de six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_canada_passport_number trouve un contenu qui correspond au modèle.
- Un mot clé depuis Keyword_canada_passport_number ou Keyword_passport est trouvé.

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
- Tel #
- PassportID
- N ° passeport
- passportnumber
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃
- Numéro de passeport
- Passeport n°
- Passeport numéro
- # Passeport
- Passeport #
- PasseportNon
- Passeportn °

   
## <a name="canada-personal-health-identification-number-phin"></a>Numéro d’identification médicale personnelle (PHIN) Canada

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_canada_phin trouve un contenu qui correspond au modèle.
- Au moins deux mots clés provenant d’Keyword_canada_phin ou de Keyword_canada_provinces sont trouvés.

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

- Nunavut
- Régime
- Territoires du Nord-Ouest
- Brand
- Colombie-britannique
- Alberta
- En-dessus
- Manitoba
- Yukon
- Terre-Neuve-et-Labrador
- Nouveau-Brunswick
- Nouvelle-Écosse
- Île-du-Prince-Édouard
- Canada

   
## <a name="canada-social-insurance-number"></a>Numéro d’assurance sociale Canada

### <a name="format"></a>Format

neuf chiffres avec des traits d’Union ou des espaces facultatifs

### <a name="pattern"></a>Modèle

Avec
- trois chiffres 
- un trait d’Union ou un espace 
- trois chiffres 
- un trait d’Union ou un espace 
- trois chiffres

Non mis en forme : neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_canadian_sin trouve un contenu qui correspond au modèle.
- Au moins deux des éléments suivants, quelle que soit la combinaison :
    - Un mot clé figurant dans la liste Keyword_sin est trouvé.
    - Un mot clé figurant dans la liste Keyword_sin_collaborative est trouvé.
    - La fonction Func_eu_date trouve une date au format correct.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- péchés 
- SSN 
- numéros 
- sécurité sociale 
- numéro d’assurance sociale 
- numéro d’identification nationale 
- id national 
- sine # 
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

sept à huit chiffres plus des délimiteurs un chiffre ou une lettre

### <a name="pattern"></a>Modèle

sept à huit chiffres plus des délimiteurs :
- un à deux chiffres 
- un point facultatif 
- trois chiffres 
- un point facultatif 
- trois chiffres 
- un tiret 
- un chiffre ou une lettre (ne respectant pas la casse), qui est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_chile_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_chile_id_card est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

- Cédula de identidad
- identificación
- numéro d’identification nationale
- numéro d’identification nationale
- id national
- Número de Identificación Nacional
- ROL Único Nacional
- rol único tributario
- GÉNÉRER
- ROUTINE
- Tarjeta de Identificación
- ROL Unico Nacional
- Rol Unico Tributario
- GÉNÉRER #
- ROUTINE #
- nationaluniqueroleID #
- Nacional identidad
- número identificación
- identidad número
- numéroto Identificacion
- identidad numérique
- N ° d’identité chilien
- Numéro d’identité chilien
- Identité chilien #
- Registre fiscal unique
- Rôle de lafonction unique
- Rôle de taxation unique
- Numéro d’identification unique unique
- Numéro national unique
- Rôle national unique
- Rôle national unique
- N ° d’identité du Chili
- Numéro d’identité Chili
- Identité Chili #

   
## <a name="china-resident-identity-card-prc-number"></a>Numéro de carte d’identité de résident chinoise (PRC)

### <a name="format"></a>Format

18 chiffres

### <a name="pattern"></a>Modèle

18 chiffres :
- six chiffres qui sont un code d’adresse 
- huit chiffres au format AAAAMMJJ, qui correspondent à la date de naissance 
- trois chiffres correspondant à un code de commande 
- un chiffre qui est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_china_resident_id trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_china_resident_id est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- FIGURANT 
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

14 à 16 chiffres qui peuvent être mis en forme ou non (dddddddddddddddd) et qui doivent réussir le test Luhn.

### <a name="pattern"></a>Modèle

Modèle très complexe et puissant qui détecte les cartes de visite de toutes les principales marques du monde, notamment Visa, MasterCard, Discover Card, JCB, American Express, etc.

### <a name="checksum"></a>Somme de contrôle

Oui, la somme de contrôle de Luhn

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_credit_card trouve un contenu qui correspond au modèle.
- L’une des affirmations suivantes est vraie :
    - Un mot clé figurant dans la liste Keyword_cc_verification est trouvé.
    - Un mot clé figurant dans la liste Keyword_cc_name est trouvé.
    - La fonction Func_expiration_date trouve une date au format correct.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
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
- cryptogramme
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
- contre. sicurezza
- cod sicurezza
- n autorizzazione
- código
- codigo
- contre. SEG
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- cód. segurança
- contre. seguranca
- contre. segurança
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
- valorisation
- vencimento
- transaction
- Numéro de transaction
- Numéro de référence
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

#### <a name="keyword_cc_name"></a>Keyword_cc_name

- American
- american express
- americanexpress
- americano espresso
- Délivrance
- MasterCard
- master card
- McDonald
- MasterCard
- master cards
- diner’s Club
- diners club
- dinersclub
- connaissance
- discover card
- discovercard
- discover cards
- JCB
- BrandSmart
- japanese card bureau
- carte blanche
- carteblanche
- carte de crédit
- CC #
- n ° de CC :
- date d’expiration
- date d’exp
- date d’expiration
- date d’expiration
- date d’exp
- date expiration
- carte bancaire
- bankcard
- numéro de carte
- num de carte
- carte
- carte
- numéros de carte
- CreditCard
- cartes de crédit
- crédit
- CCN
- titulaire de la carte
- titulaires
- titulaires de la carte
- titulaires
- carte de vérification
- carte
- cartes de vérification
- cartes
- carte de débit
- débit
- cartes de débit
- débit
- carte de retrait
- retrait
- cartes de retrait
- retrait
- envoier
- en route
- type de carte
- Cardmember ACCT
- compte cardmember
- Cardno
- Carte d’entreprise
- Cartes d’entreprise
- Type de carte
- Numéro de compte de carte
- compte de membre de carte
- Cardmember ACCT.
- n° carte
- n ° carte
- numéro de carte
- carte bancaire
- carte de crédit
- carte de credit
- numéro de carte
- numero de carte
- nº de la carte
- nº de carte
- kreditkarte
- karte
- karteninhaber
- karteninhabers
- kreditkarteninhaber
- kreditkarteninstitut
- kreditkartentyp
- eigentümername
- kartennr
- kartennummer
- kreditkartennummer
- kreditkarten-nummer
- Carta di credito
- Carta credito
- No. Carta
- n carta
- Nr. Carta
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
- Nbre. de tarjeta
- no de tarjeta
- numero de tarjeta
- número de tarjeta
- tarjeta no
- tarjetahabiente
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
- n º. do cartão
- no do cartão
- no do cartao
- Nbre. do cartão
- Nbre. do cartao
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
- Visaカード
- Visa カード
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


## <a name="croatia-drivers-license-number"></a>Numéro de permis de conduire de la Croatie

### <a name="format"></a>Format

huit chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

huit chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- L’expression régulière  `Regex_croatia_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis `Keywords_eu_driver's_license_number` ou `Keywords_croatia_eu_driver's_license_number` est trouvé. 

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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_croatia_eu_drivers_license_number"></a>Keywords_croatia_eu_driver’s_license_number

- vozačka dozvola
- vozačke dozvole


## <a name="croatia-identity-card-number"></a>Numéro de carte d’identité Croatie
Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles du numéro d’identification national de l’UE et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- Numéro de citoyen principal
- nacionalni identifikacijski broj
- numéro d’identification nationale
- OIB #
- OIB
- osobna iskaznica
- ID osobni
- osobni identifikacijski broj
- Numéro d’identification personnel
- porezni broj
- porezni identifikacijski broj
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #


## <a name="croatia-passport-number"></a>Numéro de passeport croate
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

neuf chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

neuf chiffres 
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_croatia_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_croatia_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_croatia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_croatia_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_croatia_eu_passport_number"></a>Keywords_croatia_eu_passport_number

- broj putovnice
- BR. Putovnice
- BR putovnice
   
## <a name="croatia-personal-identification-oib-number"></a>Numéro d’identification personnelle de la Croatie (OIB)

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres :
- dix chiffres 
- le chiffre final est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_croatia_oib_number trouve un contenu qui correspond au modèle.
- Un mot clé depuis Keywords_croatia_eu_tax_file_number est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- Numéro de citoyen principal
- nacionalni identifikacijski broj
- numéro d’identification nationale
- OIB #
- OIB
- osobna iskaznica
- ID osobni
- osobni identifikacijski broj
- Numéro d’identification personnel
- porezni broj
- porezni identifikacijski broj
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #

## <a name="croatia-social-security-number-or-equivalent-identification"></a>Numéro de sécurité sociale ou identification équivalent de la Croatie
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’information de numéro de sécurité sociale ou d’ID équivalent.

### <a name="format"></a>Format

11 chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

11 chiffres :
  
- dix chiffres
- un chiffre de contrôle
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
  
- La fonction  `Func_croatia_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_croatia_eu_ssn_or_equivalent` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- La fonction  `Func_croatia_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
    
```xml
 <!-- EU SSN or Equivalent Number -->
<Entity id="d24e32a4-c0bb-4ba8-899d-6303b95742d9" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_croatia_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_croatia_eu_ssn_or_equivalent" />
        </Pattern> 
       <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_croatia_eu_ssn_or_equivalent" />
        </Pattern>      
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_croatia_eu_ssn_or_equivalent"></a>Keywords_croatia_eu_ssn_or_equivalent

- Numéro d’identification personnel
- Numéro de citoyen principal
- numéro d’identification nationale
- numéro de sécurité sociale
- nationalnumber #
- SSN #
- SSN
- nationalnumber
- bnn #
- bnn
- Numéro d’identification personnel
- personalidnumber #
- OIB
- osobni identifikacijski broj

   
## <a name="cyprus-drivers-license-number"></a>Numéro de permis de conduire Chypre

### <a name="format"></a>Format

12 chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

12 chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_cyprus_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_cyprus_eu_driver's_license_number` est trouvé.

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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD

#### <a name="keywords_cyprus_eu_drivers_license_number"></a>Keywords_cyprus_eu_driver’s_license_number

- άδεια οδήγησης
- αριθμό άδειας οδήγησης
- άδειες οδήγησης


## <a name="cyprus-identity-card"></a>Carte d’identité Chypre
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

dix chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

dix chiffres 
  
### <a name="checksum"></a>Somme de contrôle

non applicable
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_cyprus_eu_national_id_card` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_cyprus_eu_national_id_card` est trouvé. 
    
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

- Numéro de carte d’identité
- Numéro de carte d’identité
- kimlik karti
- numéro d’identification nationale
- Numéro d’identification personnel
- ταυτοτητασ


## <a name="cyprus-passport-number"></a>Numéro de passeport de Chypre
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

une lettre suivie de 6-8 chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

une lettre suivie de six à huit chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_cyprus_eu_passport_number` trouve le contenu qui correspond au modèle.
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_cyprus_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_cyprus_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
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
- pasaport numarası
- N ° Pasaport
- Αρ. Διαβατηρίου

## <a name="cyprus-tax-identification-number"></a>Numéro d’identification fiscale de Chypre
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

huit chiffres et une lettre dans le modèle spécifié
  
### <a name="pattern"></a>Modèle

huit chiffres et une lettre :
  
- « 0 » ou « 9 »
- sept chiffres
- une lettre (ne respecte pas la casse)
    
### <a name="checksum"></a>Somme de contrôle

non applicable
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_cyprus_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_cyprus_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_cyprus_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
    
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
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- graduation #
- graduation
- ID d’étain
- n ° d’étain
- Etain #
- kimlik Kodu
- kimlik numarası
- αριθμός φορολογικού μητρώου
- κωδικός φορολογικού μητρώου
- φορολογική ταυτότητα
- φορολογικού κωδικού


## <a name="czech-drivers-license-number"></a>Numéro de permis de conduire tchèque

### <a name="format"></a>Format

deux lettres suivies de six chiffres
  
### <a name="pattern"></a>Modèle

huit lettres et chiffres :
  
- lettre « E » (ne respecte pas la casse)
- une lettre
- un espace (facultatif)
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_czech_republic_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_czech_republic_eu_driver's_license_number` est trouvé. 

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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD

#### <a name="keywords_czech_republic_eu_drivers_license_number"></a>Keywords_czech_republic_eu_driver’s_license_number

- řidičský prúkaz
- řidičské průkazy
- číslo řidičského průkazu
- čísla řidičských průkazů


## <a name="czech-passport-number"></a>Numéro de passeport tchèque
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

huit chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

huit chiffres sans espaces ni délimiteurs
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_czech_republic_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_czech_republic_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_czech_republic_eu_passport_number"></a>Keywords_czech_republic_eu_passport_number

- CESTOVNÍ pas
- číslo pasu
- cestovní pasu
- passeport non
- čísla pasu


## <a name="czech-personal-identity-number"></a>Numéro d’identité personnelle tchèque

### <a name="format"></a>Format

neuf chiffres avec une barre oblique inverse facultative (ancien format) dix chiffres avec une barre oblique facultative (nouveau format)

### <a name="pattern"></a>Modèle

neuf chiffres (ancien format) :
- six chiffres qui représentent la date de naissance
- une barre oblique facultative
- trois chiffres

dix chiffres (nouveau format) :
- six chiffres qui représentent la date de naissance
- une barre oblique facultative 
- quatre chiffres où le dernier chiffre est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :

- La fonction Func_czech_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_czech_id_card est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :

- La fonction Func_czech_id_card_new_format trouve le contenu qui correspond au modèle.
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

- Numéro de naissance
- ID de République tchèque
- czechidno #
- daňové číslo
- identifikační číslo
- n ° d’identité
- Numéro d’identité
- identityno #
- identityno
- Numéro d’assurance
- numéro d’identification nationale
- nationalnumber #
- numéro national
- osobní číslo
- personalidnumber #
- Numéro d’identification personnel
- Numéro d’identification personnel
- numéro personnel
- électro #
- pid
- pojištění číslo
- rč
- rodne cislo
- rodné číslo
- SSN
- SSN #
- numéro de sécurité sociale
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #
- Numéro d’identification unique


## <a name="czech-social-security-number-or-equivalent-identification"></a>Numéro de sécurité sociale tchèque ou identification équivalente

Cette entité de type d’informations sensibles est uniquement disponible dans le type d’information de numéro de sécurité sociale ou d’ID équivalent.

### <a name="format"></a>Format

10 chiffres et une barre oblique inverse dans le modèle spécifié
  
### <a name="pattern"></a>Modèle

dix chiffres et une barre oblique inverse :
  
- six chiffres correspondant à la date de naissance (AAMMJJ) : 
- une barre oblique inverse
- trois chiffres correspondant à un numéro de série qui sépare les personnes nés à la même date
- un chiffre de contrôle
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_czech_republic_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_czech_republic_eu_ssn_or_equivalent` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_czech_republic_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 

```xml
 <!-- EU SSN or Equivalent Number -->
<Entity id="d24e32a4-c0bb-4ba8-899d-6303b95742d9" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_czech_republic_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_czech_republic_eu_ssn_or_equivalent" />
        </Pattern> 
       <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_czech_republic_eu_ssn_or_equivalent" />
        </Pattern>      
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_czech_republic_eu_ssn_or_equivalent"></a>Keywords_czech_republic_eu_ssn_or_equivalent

- Numéro de naissance
- numéro d’identification nationale
- Numéro d’identification personnel
- numéro de sécurité sociale
- nationalnumber #
- SSN #
- SSN
- numéro national
- Numéro d’identification personnel
- personalidnumber #
- rč
- rodné číslo
- rodne cislo


## <a name="denmark-drivers-license-number"></a>Numéro de permis de conduire Danemark

### <a name="format"></a>Format

huit chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

huit chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_denmark_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_denmark_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD

#### <a name="keywords_denmark_eu_drivers_license_number"></a>Keywords_denmark_eu_driver’s_license_number

- kørekort
- kørekortnummer


## <a name="denmark-passport-number"></a>Numéro de passeport Danemark
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

neuf chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

neuf chiffres 
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_denmark_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_denmark_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_denmark_eu_passport_number"></a>Keywords_denmark_eu_passport_number

- pasnummer
- Passeport n °
- pasnumre


## <a name="denmark-personal-identification-number"></a>Numéro d’identification personnel Danemark

### <a name="format"></a>Format

dix chiffres contenant un trait d’Union

### <a name="pattern"></a>Modèle

dix chiffres :
- six chiffres au format JJMMAA qui correspondent à la date de naissance 
- un trait d’Union 
- quatre chiffres où le dernier chiffre est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière Func_denmark_eu_tax_file_number trouve le contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_denmark_id est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- L’expression régulière Func_denmark_eu_tax_file_number trouve le contenu qui correspond au modèle.
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
- registreringssystem civil
- cardio
- cardio #
- gesundheitskarte nummer
- gesundheitsversicherungkarte nummer
- carte d’intégrité
- Numéro de carte d’assurance maladie
- Numéro d’assurance-maladie
- numéro d’identification
- identifikationsnummer
- identifikationsnummer #
- Numéro d’identité
- krankenkassennummer
- nationalid #
- nationalnumber #
- numéro national
- personalidnumber #
- personalidentityno #
- Numéro d’identification personnel
- personnummer
- personnummer #
- reisekrankenversicherungskartenummer
- rejsesygesikringskort
- SSN
- SSN #
- ID Skat
- skat kode
- skat nummer
- skattenummer
- numéro de sécurité sociale
- sundhedsforsikringskort
- sundhedsforsikringsnummer
- sundhedskort
- sundhedskortnummer
- sygesikring
- sygesikringkortnummer
- Code de taxe
- carte d’assurance-santé voyages
- uniqueidentityno #
- Numéro de taxe
- Numéro d’enregistrement taxe
- id fiscal
- Numéro d’identification de taxe
- taxi #
- taxnumber #
- n ° taxe
- taxno #
- taxnumber
- n ° d’identification fiscale
- Etain #
- taxidno #
- taxidnumber #
- n ° taxe #
- ID d’étain
- n ° d’étain
- cpr.nr
- cprnr
- cprnummer
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


## <a name="denmark-social-security-number-or-equivalent-identification"></a>Numéro de sécurité sociale ou identification équivalente Danemark
Cette entité de type d’informations sensibles n’est disponible que pour le type d’informations sensibles de l’UE ou ID équivalent.

### <a name="format"></a>Format

10 chiffres et un trait d’Union dans le modèle spécifié
  
### <a name="pattern"></a>Modèle

dix chiffres et un trait d’Union :
  
- six chiffres correspondant à la date de naissance (JJMMAA) 
- un trait d’Union
- quatre chiffres correspondant à un numéro de séquence

### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_denmark_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_denmark_eu_ssn_or_equivalent` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_denmark_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
    
```xml
 <!-- EU SSN or Equivalent Number -->
<Entity id="d24e32a4-c0bb-4ba8-899d-6303b95742d9" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_denmark_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_denmark_eu_ssn_or_equivalent" />
        </Pattern> 
       <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_denmark_eu_ssn_or_equivalent" />
        </Pattern>      
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_denmark_eu_ssn_or_equivalent"></a>Keywords_denmark_eu_ssn_or_equivalent

- Numéro d’identification personnel
- numéro d’identification nationale
- numéro de sécurité sociale
- nationalnumber #
- SSN #
- SSN
- numéro national
- Numéro d’identification personnel
- personalidnumber #
- CPR-nummer
- personnummer


## <a name="drug-enforcement-agency-dea-number"></a>Numéro de la Loi sur la mise en œuvre du médicament (DEA)

### <a name="format"></a>Format

deux lettres suivies de sept chiffres

### <a name="pattern"></a>Modèle

Le modèle doit inclure tous les éléments suivants :
- une lettre (ne respecte pas la casse) à partir de cet ensemble de lettres possibles : abcdefghjklmnprstux, qui est un code de l’abonné 
- une lettre (ne respecte pas la casse), qui est la première lettre du nom de famille ou du chiffre « 9 » de l’inscrit
- sept chiffres, dont le dernier est le chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_dea_number trouve un contenu qui correspond au modèle.
- Un mot clé from `Keyword_dea_number` est trouvé
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

- DEA
- DEA #
- administration de l’application de médicament
- organisme d’application pharmaceutique


## <a name="estonia-drivers-license-number"></a>Numéro de permis de conduire Estonie

### <a name="format"></a>Format

deux lettres suivies de six chiffres
  
### <a name="pattern"></a>Modèle

deux lettres et six chiffres :
  
- les lettres "ET" (ne respectent pas la casse) 
- six chiffres
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_estonia_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_estonia_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD

#### <a name="keywords_estonia_eu_drivers_license_number"></a>Keywords_estonia_eu_driver’s_license_number

--autorisation de conduire
- juhilubade numbrid
- numéro juhiloa
- juhiluba


## <a name="estonia-personal-identification-code"></a>Code d’identification personnel (Estonie)
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

11 chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

11 chiffres :
  
- un chiffre correspondant au sexe et au siècle de naissance (nombre impair mâle, numéro pair femelle ; 1-2:19 siècle ; 3-4:20ème siècle ; 5-6:21ème siècle)
- six chiffres correspondant à la date de naissance (AAMMJJ)
- trois chiffres correspondant à un numéro de série séparant les personnes nés à la même date
- un chiffre de contrôle
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_estonia_eu_national_id_card` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_estonia_eu_national_id_card` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_estonia_eu_national_id_card` trouve le contenu qui correspond au modèle. 
    
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

- ID-kaart
- inverse
- isikukood #
- isikukood
- ID maksu
- maksukohustuslase identifitseerimisnumber
- maksunumber
- numéro d’identification nationale
- numéro national
- code personnel
- Numéro d’identification personnel
- code d’identification personnel
- Numéro d’identification personnel
- personalidnumber #
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #


## <a name="estonia-passport-number"></a>Numéro de passeport Estonie
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

une lettre suivie de sept chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

une lettre suivie de sept chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_estonia_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_estonia_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

Eesti kodaniku numéro de passe Passei passinumbrid document numéro de document n ° dokumendi Nr

## <a name="eu-debit-card-number"></a>Numéro de carte de crédit de l'UE

### <a name="format"></a>Format

16 chiffres

### <a name="pattern"></a>Modèle

Modèle très complexe et puissant

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
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
- CC # 

#### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- num de compte 
- num de compte 
- n° compte 
- american express 
- americanexpress 
- americano espresso 
- American 
- carte de retrait 
- cartes de retrait 
- atm kaart 
- retrait 
- retrait 
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
- titulaires 
- titulaires 
- carte 
- carte 
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
- CCN 
- carte de vérification 
- cartes de vérification 
- carte
- cartes 
- chequekaart 
- Cirrus 
- Cirrus-EDC-Maestro 
- controlekaart 
- controlekaarten 
- carte de crédit 
- cartes de crédit 
- CreditCard 
- crédit 
- debetkaart 
- debetkaarten 
- carte de débit 
- cartes de débit 
- débit 
- débit 
- debito automatico 
- diners club 
- dinersclub 
- connaissance 
- discover card 
- discover cards 
- discovercard 
- discovercards 
- débito automático
- EDC 
- eigentümername 
- carte de crédit européenne 
- hoofdkaart 
- hoofdkaarten 
- in viaggio 
- japanese card bureau 
- japanse kaartdienst 
- JCB 
- kaart 
- kaart num 
- kaartaantal 
- kaartaantallen 
- kaarthouder 
- kaarthouders 
- karte  
- karteninhaber 
- karteninhabers
- kartennr 
- kartennummer 
- kreditkarte 
- kreditkarten-nummer 
- kreditkarteninhaber 
- kreditkarteninstitut 
- kreditkartennummer 
- kreditkartentyp 
- sonne 
- master card 
- master cards 
- MasterCard 
- MasterCard 
- McDonald 
- mister cash 
- n carta 
- Carta 
- no de tarjeta 
- no do cartao 
- no do cartão 
- Nbre. de tarjeta 
- Nbre. do cartao 
- Nbre. do cartão 
- nr carta 
- Nr. Carta 
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
- n º. do cartão 
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
- tracteur 
- supporti di scheda 
- supporto di scheda 
- accéder 
- tarjeta atm 
- tarjeta credito 
- tarjeta de atm 
- tarjeta de credito 
- tarjeta de debito 
- tarjeta debito 
- tarjeta no
- tarjetahabiente 
- tipo della scheda 
- ufficio giapponese della 
- scheda 
- v pay 
- v-Pay 
- délivrance 
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
- contre. SEG 
- contre. seguranca 
- contre. segurança 
- contre. sicurezza 
- codice di sicurezza 
- codice di verifica 
- codigo 
- codigo de seguranca 
- codigo de segurança 
- crittogramma 
- cryptogram 
- cryptogramme 
- cv2 
- lâche 
- cvc2 
- cryptogramme 
- cvv 
- cvv2 
- cód seguranca 
- cód segurança 
- cód. seguranca 
- cód. segurança 
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
- Nbre. dell'edizione 
- Nbre. di sicurezza 
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
- veiligheidsaantal 
- veiligheidscode 
- veiligheidsnummer 
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
- pire 
- expiration 
- expire 
- expiration 
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
- valorisation 
- venc 
- vencimento 
- vencimiento 
- verloopt 
- vervaldag 
- vervaldatum 
- vto 
- válido hasta 


## <a name="eu-drivers-license-number"></a>Numéro de permis de conduire de l’UE

Il s’agit des entités du type d’informations sensibles du pilote de l’UE.

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
- [Relatif](#luxemburg-drivers-license-number)
- [Malte](#malta-drivers-license-number)
- [Pays-Bas](#netherlands-drivers-license-number)
- [Pologne](#poland-drivers-license-number) 
- [Portugal](#portugal-drivers-license-number)
- [Roumanie](#romania-drivers-license-number)
- [République de Slovaquie](#slovakia-drivers-license-number)
- [Slovénie](#slovenia-drivers-license-number)
- [Espagne](#spain-drivers-license-number)
- [Suède](#sweden-drivers-license-number)
- [impérial](#uk-drivers-license-number)


## <a name="eu-national-identification-number"></a>Numéro d’identification nationale de l’UE

Il s’agit des entités du type d’informations sensibles du numéro d’identification national UE.

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
- [Relatif](#luxemburg-national-identification-number-natural-persons)
- [Malte](#malta-identity-card-number)
- [Pays-Bas](#netherlands-citizens-service-bsn-number)
- [Pologne](#poland-national-id-pesel)
- [Portugal](#portugal-citizen-card-number)
- [Roumanie](#romania-personal-numeric-code-cnp)
- [République de Slovaquie](#slovakia-personal-number)
- [Slovénie](#slovenia-unique-master-citizen-number)
- [Espagne](#spain-dni)
- [impérial](#uk-national-insurance-number-nino)                                        


## <a name="eu-passport-number"></a>Numéro de passeport UE 

Il s’agit des entités dans le numéro de passeport UE typeThese sont les entités du groupe de numéros de passeport UE.

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
- [Relatif](#luxemburg-passport-number)
- [Malte](#malta-passport-number)
- [Pays-Bas](#netherlands-passport-number)
- [Pologne](#poland-passport-number)
- [Portugal](#portugal-passport-number)
- [Roumanie](#romania-passport-number)
- [République de Slovaquie](#slovakia-passport-number)
- [Slovénie](#slovenia-passport-number)
- [Espagne](#spain-passport-number)
- [Suède](#sweden-passport-number)
- [impérial](#us--uk-passport-number)


## <a name="eu-social-security-number-or-equivalent-identification"></a>Numéro de sécurité sociale de l’UE ou identification équivalente

Il s’agit des entités qui sont dans le type d’information de numéro de sécurité sociale ou d’identification équivalent.

- [Autriche](#austria-social-security-number-or-equivalent-identification)
- [Belgique](#belgium-social-security-number-or-equivalent-identification)
- [Croatie](#croatia-social-security-number-or-equivalent-identification)
- [Tchèque](#czech-social-security-number-or-equivalent-identification)
- [Danemark](#denmark-social-security-number-or-equivalent-identification)
- [Finlande](#finland-social-security-number-or-equivalent-identification)
- [France](#france-social-security-number-insee-or-equivalent-identification)
- [Allemagne](#germany-identity-card-number)
- [Grèce](#greece-national-id-card)
- [Hongrie](#hungary-social-security-number-or-equivalent-identification)
- [Portugal](#portugal-citizen-card-number)
- [Espagne](#spain-social-security-number-ssn)
- [Suède](#sweden-social-security-number-or-equivalent-identification)


## <a name="eu-tax-identification-number"></a>Numéro d’identification fiscale de l’UE

Ces entités sont dans le type d’informations sensibles du numéro d’identification fiscale de l’UE.

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
- [Relatif](#luxemburg-national-identification-number-non-natural-persons)
- [Malte](#malta-tax-identification-number)
- [Pays-Bas](#netherlands-tax-identification-number)
- [Pologne](#poland-tax-identification-number)
- [Portugal](#portugal-tax-identification-number)
- [Roumanie](#romania-personal-numeric-code-cnp)
- [République de Slovaquie](#slovakia-personal-number)
- [Slovénie](#slovenia-tax-identification-number)
- [Espagne](#spain-tax-identification-number)
- [Suède](#sweden-tax-identification-number)
- [impérial](#uk-unique-taxpayer-reference-number)


## <a name="finland-drivers-license-number"></a>Numéro de permis de conduire Finlande

### <a name="format"></a>Format

dix chiffres et lettres contenant un trait d’Union
  
### <a name="pattern"></a>Modèle

dix chiffres et lettres contenant un trait d’Union :
  
- six chiffres 
- un trait d’Union
- trois chiffres 
- un chiffre ou une lettre
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_finland_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_finland_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_finland_eu_drivers_license_number"></a>Keywords_finland_eu_driver’s_license_number

- ajokortti
- permis de conduire
- ajokortin numérique
- kuljettaja lic.
- körkort
- körkortnummer
- förare lic.
- ajokortit
- ajokortin numerot


## <a name="finland-european-health-insurance-number"></a>Numéro d’assurance maladie européenne pour la Finlande
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

numéro à 20 chiffres

### <a name="pattern"></a>Modèle

nombre à 20 chiffres :

- dix chiffres-8024680246
- un espace ou un tiret facultatif
- dix chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression Regex Regex_Finland_European_Health_Insurance_Number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keyword_Finland_European_Health_Insurance_Number est trouvé.

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
- carte d’intégrité
- carte d’assurance-maladie
- Numéro d’assurance-maladie
- hälsokort
- sairaanhoitokortin
- sairausvakuutuskortti
- sairausvakuutusnumero
- sjukförsäkring nummer
- sjukförsäkringskort
- suomen sairausvakuutuskortti
- terveyskortti


## <a name="finland-national-id"></a>ID national de Finlande

### <a name="format"></a>Format

six chiffres plus un caractère indiquant un siècle plus trois chiffres plus un chiffre de contrôle

### <a name="pattern"></a>Modèle

Le modèle doit inclure tous les éléments suivants :
- six chiffres au format de format JJMMAA qui correspondent à une date de naissance 
- marqueur siècle (« - », « + » ou « a ») 
- Numéro d’identification personnel à trois chiffres 
- un chiffre ou une lettre (ne respectant pas la casse), qui est un chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- la fonction Func_finnish_national_id trouve le contenu qui correspond au modèle
- un mot clé depuis Keyword_finnish_national_id est trouvé.
- le checksum passe

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- la fonction Func_finnish_national_id trouve le contenu qui correspond au modèle
- le checksum passe

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

- ainutlaatuinen henkilökohtainen tunnus
- henkilökohtainen tunnus
- henkilötunnus
- henkilötunnusnumero #
- henkilötunnusnumero
- hetu
- n ° ID
- Numéro d’identification
- numéro d’identification
- identiteetti numérique
- Numéro d’identité
- idnumber
- kansallinen henkilötunnus
- kansallisen henkilökortin
- carte d’identité nationale
- Numéro d’identification nationale
- ID personnel
- code d’identité personnelle
- personalidnumber #
- personbeteckning
- personnummer
- numéro de sécurité sociale
- sosiaaliturvatunnus
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #
- tunnistenumero
- tunnus numérique
- tunnusluku
- tunnusnumero
- verokortti
- veronumero
- verotunniste
- verotunnus


## <a name="finland-passport-number"></a>Numéro de passeport de Finlande
Cette entité de type d’informations sensibles est disponible dans le type d’informations sensibles du numéro de passeport de l’UE et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format
combinaison de neuf lettres et chiffres

### <a name="pattern"></a>Modèle
combinaison de neuf lettres et chiffres :
- deux lettres (ne respectant pas la casse) 
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_finland_passport_number trouve un contenu qui correspond au modèle.
- Un mot clé depuis Keywords_eu_passport_number_common ou Keyword_finland_passport_number est trouvé.

```xml
<!-- Finland Passport Number -->
<Entity id="d1685ac3-1d3a-40f8-8198-32ef5669c7a5" recommendedConfidence="75" patternsProximity="300">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_finland_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keyword_finland_passport_number" />
          </Any>
        </Pattern>
</Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keyword_finland_passport_number"></a>Keyword_finland_passport_number

- Suomalainen passes
- nombre de passerelles
- Numéro de transfert. #
- nombre de passerelles #
- Numéro de transfert.
- transfert #
- Numéro de transfert


## <a name="finland-social-security-number-or-equivalent-identification"></a>Numéro de sécurité sociale Finlande ou identification équivalente
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’information de numéro de sécurité sociale ou d’ID équivalent.

### <a name="format"></a>Format

Combinaison de 11 caractères au format spécifié
  
### <a name="pattern"></a>Modèle

combinaison de 11 caractères au format spécifié :
  
- six chiffres 
- une instance de l’un des éléments suivants :
  - symbole plus
  - symbole moins
  - la lettre « A » (ne respecte pas la casse)
- trois chiffres
- une lettre ou un chiffre
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_finland_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_finland_eu_ssn_or_equivalent` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_finland_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
    
```xml
 <!-- EU SSN or Equivalent Number -->
<Entity id="d24e32a4-c0bb-4ba8-899d-6303b95742d9" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_finland_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_finland_eu_ssn_or_equivalent" />
        </Pattern> 
       <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_finland_eu_ssn_or_equivalent" />
        </Pattern>      
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_finland_eu_ssn_or_equivalent"></a>Keywords_finland_eu_ssn_or_equivalent

- numéro d’identification
- ID personnel
- Numéro d’identité
- Numéro d’identification national finnois
- personalidnumber #
- numéro d’identification nationale
- Numéro d’identification
- Numéro d’identification nationale
- Numéro d’identification national
- n ° ID
- tunnistenumero
- henkilötunnus
- yksilöllinen henkilökohtainen tunnistenumero
- ainutlaatuinen henkilökohtainen tunnus
- identiteetti numérique
- suomen kansallinen henkilötunnus
- henkilötunnusnumero #
- kansallisen tunnistenumero
- tunnusnumero
- Kansallinen tunnus numérique
- hetu


## <a name="france-drivers-license-number"></a>Numéro de permis de conduire France

### <a name="format"></a>Format

12 chiffres

### <a name="pattern"></a>Modèle

12 chiffres avec validation pour écarter les modèles similaires, comme les numéros de téléphone français

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- la fonction Func_french_drivers_license trouve le contenu qui correspond au modèle.
- un mot clé depuis Keyword_french_drivers_license est trouvé.

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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD
- permis de conduire
- numéro de permis
- numéro de permis
- numéros de permis
- numéros de permis
- numéros de licence


## <a name="france-health-insurance-number"></a>Numéro d’assurance maladie France
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

nombre à 21 chiffres

### <a name="pattern"></a>Modèle

nombre à 21 chiffres :

- dix chiffres
- un espace facultatif
- dix chiffres
- un espace facultatif
- un chiffre


### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- l’expression Regex Regex_France_Health_Insurance_Number trouve le contenu qui correspond au modèle.
- un mot clé depuis Keyword_France_Health_Insurance_Number est trouvé.

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


## <a name="france-national-id-card-cni"></a>Carte d’identité nationale (CNI) France

### <a name="format"></a>Format

12 chiffres

### <a name="pattern"></a>Modèle

12 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_france_cni trouve un contenu qui correspond au modèle.
- Un mot clé depuis Keywords_france_eu_national_id_card est trouvé.

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
- carte d’identité nationale
- carte nationale d’idenite non
- CNI #
- CNI
- compte bancaire
- numéro d’identification nationale
- identité nationale
- nationalidno #
- Numéro d’assurance maladie
- Numéro de carte vitale

   
## <a name="france-passport-number"></a>Numéro de passeport français
Cette entité de type d’informations sensibles est disponible dans le type d’informations sensibles du numéro de passeport de l’UE et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

neuf chiffres et lettres

### <a name="pattern"></a>Modèle

neuf chiffres et lettres :
- deux chiffres 
- deux lettres (ne respectant pas la casse) 
- cinq chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_fr_passport trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_passport est trouvé.

```xml
<!-- France Passport Number -->
<Entity id="3008b884-8c8c-4cd8-a289-99f34fc7ff5d" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_fr_passport" />
        <Match idRef="Keyword_passport" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_passport"></a>Keyword_passport

- Numéro de passeport
- N° de passeport
- # Passeport
- Tel #
- PassportID
- N ° passeport
- passportnumber
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃ 
- Numéro de passeport
- Passeport n°
- Passeport numéro
- # Passeport
- Passeport #
- PasseportNon
- Passeportn °

      
## <a name="france-social-security-number-insee-or-equivalent-identification"></a>Numéro de sécurité sociale (INSEE) français ou identification équivalente
Cette entité de type d’informations sensibles est incluse dans le numéro de sécurité sociale de l’UE et un type d’informations sensibles ID équivalent et est disponible en tant qu’entité de type d’informations sensibles autonome.

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

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 95 % si, dans une proximité de 300 caractères :
- La fonction Func_french_insee ou Func_fr_insee trouve le contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_fr_insee est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_french_insee ou Func_fr_insee trouve le contenu qui correspond au modèle.
- Aucun mot clé figurant dans la liste Keyword_fr_insee n’est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- France INSEE -->
<Entity id="71f62b97-efe0-4aa1-aa49-e14de253619d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="95">
        <IdMatch idRef="Func_french_insee" />
        <Match idRef="Func_fr_insee" />
        <Any minMatches="1">
          <Match idRef="Keyword_fr_insee" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_french_insee" />
        <Match idRef="Func_fr_insee" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_fr_insee" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_fr_insee"></a>Keyword_fr_insee

- INSEE
- securité sociale
- securite sociale
- id national
- numéro d’identification nationale
- numéro d’identité
- n° d’identité
- Nbre. d’identité
- numéro d’identité
- n° d’identité
- Nbre. d’identite
- numéro de sécurité sociale
- code de sécurité sociale
- numéro d’assurance sociale
- le numéro d’identification nationale
- d’identité nationale
- numéro de sécurité sociale
- le code de la sécurité sociale
- numéro d’assurance sociale
- numéro de sécu
- code sécu 

## <a name="france-tax-identification-number"></a>Numéro d’identification fiscale France

### <a name="format"></a>Format

13 chiffres
  
### <a name="pattern"></a>Modèle

13 chiffres
  
- Un chiffre qui doit être 0, 1, 2 ou 3
- 1 chiffre
- Un espace (facultatif) 
- 2 chiffres 
- Un espace (facultatif) 
- 3 chiffres 
- Un espace (facultatif) 
- 3 chiffres 
- Un espace (facultatif) 
- 3 chiffres de vérification 

  
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_france_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_france_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_france_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
    
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

- Numéro d’identification fiscale
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #


## <a name="france-value-added-tax-number"></a>Numéro de TVA de la valeur ajoutée France
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

modèle alphanumérique de 13 caractères

### <a name="pattern"></a>Modèle

modèle alphanumérique de 13 caractères :

- deux lettres-FR (ne respectant pas la casse)
- un espace ou un tiret facultatif
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

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_france_value_added_tax_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_france_value_added_tax_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_france_value_added_tax_number trouve le contenu qui correspond au modèle.

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

- Numéro de TVA
- n ° TVA
- compt #
- taxe sur la valeur ajoutée
- ID Siren n ° numéro d’identification taxe sur valeur ajoutée
- taxe valeur ajoutée
- taxe sur la valeur ajoutée
- n ° TVA
- Numéro de TVA
- Numéro d’identification Siren


## <a name="germany-drivers-license-number"></a>Numéro de permis de conduire Allemagne

### <a name="format"></a>Format

combinaison de 11 chiffres et lettres

### <a name="pattern"></a>Modèle

11 chiffres et lettres (ne respectent pas la casse) :
- un chiffre ou une lettre 
- deux chiffres 
- six chiffres ou lettres 
- un chiffre 
- un chiffre ou une lettre

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- Führerschein
- Fuhrerschein
- fuehrerschein
- führerscheinnummer
- fuhrerscheinnummer
- fuehrerscheinnummer
- Führerschein 
- Fuhrerschein 
- fuehrerschein 
- führerscheinnummernr
- fuhrerscheinnummernr
- fuehrerscheinnummernr
- führerscheinnummerklasse
- fuhrerscheinnummerklasse
- fuehrerscheinnummerklasse
- Nr-Führerschein
- Nr-Fuhrerschein
- Nr-fuehrerschein
- non-Führerschein
- non-Fuhrerschein
- non-fuehrerschein
- n-Führerschein
- n-Fuhrerschein
- n-fuehrerschein
- permis de conduire
- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- dlno


## <a name="germany-identity-card-number"></a>Numéro de carte d’identité Allemagne

### <a name="format"></a>Format

depuis le 1er novembre 2010 : neuf lettres et chiffres

du 1er avril 1987 au 31 octobre 2010:10 chiffres

### <a name="pattern"></a>Modèle

depuis le 1er novembre 2010 :
- une lettre (ne respecte pas la casse) 
- huit chiffres

du 1er avril 1987 au 31 octobre 2010 :
- dix chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_germany_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_germany_id_card est trouvé.

```xml
<!-- Germany Identity Card Number -->
<Entity id="e577372f-c42e-47a0-9d85-bebed1c237d4" recommendedConfidence="65" patternsProximity="300">
  <Pattern confidenceLevel="65">
     <IdMatch idRef="Regex_germany_id_card"/>
     <Match idRef="Keyword_germany_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- ausweis
- gpid
- identificateur
- identifikation
- identifizierungsnummer
- Carte d’identité
- Numéro d’identité
- ID-Nummer
- ID personnel
- personalausweis
- persönliche ID Nummer
- persönliche identifikationsnummer
- persönliche-ID-Nummer


## <a name="germany-passport-number"></a>Numéro de passeport allemand
Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles du numéro de passeport de l’UE et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

10 chiffres ou lettres

### <a name="pattern"></a>Modèle

Le modèle doit inclure tous les éléments suivants :
- le premier caractère est un chiffre ou une lettre de cet ensemble (C, F, G, H, J, K) 
- trois chiffres 
- cinq chiffres ou lettres de cet ensemble (C,-H, J-N, P, R, T, V-Z) 
- un chiffre

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_german_passport trouve un contenu qui correspond au modèle.
- Un mot clé from `Keyword_german_passport` est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_german_passport_data trouve un contenu qui correspond au modèle.
- Un mot clé from `Keyword_german_passport` est trouvé.
- La somme de contrôle est correcte.

```xml
    <!-- German Passport Number -->
    <Entity id="2e3da144-d42b-47ed-b123-fbf78604e52c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_german_passport" />
        <Match idRef="Keyword_german_passport" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_passport_data" />
        <Match idRef="Keyword_german_passport" />
      </Pattern>
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
- n ° passeport
- passeport non

## <a name="germany-tax-identification-number"></a>Numéro d’identification fiscale de l’Allemagne

### <a name="format"></a>Format

11 chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

11 chiffres :
  
- Deux chiffres 
- Un espace facultatif
- Trois chiffres 
- Un espace facultatif
- Trois chiffres 
- Un espace facultatif
- Deux chiffres
- un chiffre de contrôle
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_germany_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_germany_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_germany_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
    
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
- ID Steuer
- steueridentifikationsnummer
- steuernummer
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #
- zinn #
- zinn
- zinnnummer


## <a name="germany-value-added-tax-number"></a>Numéro de TVA de la valeur ajoutée Germany
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

modèle alphanumérique de 11 caractères

### <a name="pattern"></a>Modèle

modèle alphanumérique de 11 caractères :

- lettre D ou d
- lettre E ou e
- un espace facultatif
- trois chiffres
- espace ou virgule facultatif
- trois chiffres
- espace ou virgule facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_germany_value_added_tax_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_germany_value_added_tax_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_germany_value_added_tax_number trouve le contenu qui correspond au modèle.

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

- Numéro de TVA
- n ° TVA
- compt #
- n ° de TVA Mehrwertsteuer
- mwst
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer


## <a name="greece-drivers-license-number"></a>Numéro de permis de conduire Grèce

### <a name="format"></a>Format

neuf chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

neuf chiffres 
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_greece_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_greece_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_greece_eu_drivers_license_number"></a>Keywords_greece_eu_driver’s_license_number

- δεια οδήγησης
- Adeia odigisis
- Άδεια οδήγησης
- Δίπλωμα οδήγησης


## <a name="greece-national-id-card"></a>Carte d’identité nationale Grèce

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

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_greece_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_greece_id_card est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
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

- ID grec
- ID national grec
- carte d’identité personnelle grecque
- ID de police grec
- Carte d’identité
- tautotita
- ταυτότητα
- ταυτότητας


## <a name="greece-passport-number"></a>Numéro de passeport Grèce

Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

Deux lettres suivies de sept chiffres, sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

Deux lettres suivies de sept chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- L’expression régulière  `Regex_greece_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_greece_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_greece_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_greece_eu_passport_number"></a>Keywords_greece_eu_passport_number

- αριθμός διαβατηρίου
- αριθμούς διαβατηρίου
- αριθμός διαβατηριο

## <a name="greece-tax-identification-number"></a>Numéro d’identification de taxe Grèce
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

Neuf chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

Neuf chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non applicable
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- L’expression régulière  `Regex_greece_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_greece_eu_tax_file_number` est trouvé. 
    
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

- financement #
- financement
- aφμ | aφμ Αριθμός
- aφμ
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- n ° Registre taxe
- Numéro de registre des taxes
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- taxregistryno #
- ID d’étain
- n ° d’étain
- Etain #
- αριθμός φορολογικού μητρώου
- τον αριθμό φορολογικού μητρώου
- φορολογικού μητρώου νο


## <a name="hong-kong-identity-card-hkid-number"></a>Numéro de carte d’identité (HKID) Hong Kong

### <a name="format"></a>Format

Combinaison de 8 ou 9 lettres et chiffres plus éventuellement des parenthèses autour du dernier caractère

### <a name="pattern"></a>Modèle

Combinaison de 8 ou 9 lettres :
- 1 ou 2 lettres (ne respectant pas la casse)  
- Six chiffres 
- Le dernier caractère (un chiffre ou la lettre A), qui est le chiffre de contrôle et est éventuellement entre parenthèses.

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_hong_kong_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_hong_kong_id_card est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
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
- carte d’identité de Hong Kong
- HKIDC
- carte d’identité
- Carte d’identité
- carte d’identité HK
- ID Hong Kong
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

Deux lettres et six chiffres :
  
- Deux lettres (ne respectent pas la casse) 
- Six chiffres
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- L’expression régulière  `Regex_hungary_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_hungary_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_hungary_eu_drivers_license_number"></a>Keywords_hungary_eu_driver’s_license_number

- vezetoi engedely
- vezetői engedély
- vezetői engedélyek


## <a name="hungary-personal-identification-number"></a>Numéro d’identification personnel Hongrie
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

11 chiffres
  
### <a name="pattern"></a>Modèle

11 chiffres :
  
- Un chiffre correspondant au sexe (1-mâle, 2 femelles), d’autres numéros sont également possibles pour les citoyens nés avant 1900 ou les citoyens ayant une double citoyenneté. 
- Six chiffres correspondant à la date de naissance (AAMMJJ)
- Trois chiffres correspondant à un numéro de série
- Un chiffre de contrôle
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
  
- La fonction  `Func_hungary_eu_national_id_card` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_hungary_eu_national_id_card` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- La fonction  `Func_hungary_eu_national_id_card` trouve le contenu qui correspond au modèle. 
    
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

- Numéro d’identification
- numéro d’identification
- SZ GI
- t. vitrage.
- sz. GI.
- személyazonosító igazolvány
- személyi igazolvány


## <a name="hungary-passport-number"></a>Numéro de passeport Hongrie

Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

Deux lettres suivies de six ou sept chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

Deux lettres suivies de six ou sept chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- L’expression régulière  `Regex_hungary_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_hungary_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_hungary_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_hungary_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```
### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_hungary_eu_passport_number"></a>Keywords_hungary_eu_passport_number

- útlevél száma
- Útlevelek száma
- útlevél szám

## <a name="hungary-social-security-number-or-equivalent-identification"></a>Numéro de sécurité sociale ou identification équivalente Hongrie

Cette entité de type d’informations sensibles est uniquement disponible dans le type d’information de numéro de sécurité sociale ou d’ID équivalent.

### <a name="format"></a>Format

Neuf chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

Neuf chiffres
  
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
  
- La fonction  `Func_hungary_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_hungary_eu_ssn_or_equivalent` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- La fonction  `Func_hungary_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
    
```xml
 <!-- EU SSN or Equivalent Number -->
<Entity id="d24e32a4-c0bb-4ba8-899d-6303b95742d9" patternsProximity="300" recommendedConfidence="75">
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

- Numéro de sécurité sociale hongrois
- numéro de sécurité sociale
- socialsecuritynumber #
- hssn #
- socialsecuritynno
- hssn
- taj
- taj #
- SSN
- SSN #
- Numéro de sécurité sociale
- áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám
- magyar áfa szám


## <a name="hungary-tax-identification-number"></a>Numéro d’identification de taxe Hongrie
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

Dix chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

Dix chiffres :
  
- Un chiffre qui doit être « 8 » 
- Huit chiffres
- Un chiffre de contrôle
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
  
- La fonction  `Func_hungary_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_hungary_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- La fonction  `Func_hungary_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
    
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
- étain hongrois
- hungatiantin #
- Numéro de l’autorité fiscale
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #
- Numéro de TVA


## <a name="hungary-value-added-tax-number"></a>Numéro de taxe de la valeur ajoutée à la Hongrie
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

modèle alphanumérique de 10 caractères

### <a name="pattern"></a>Modèle

modèle alphanumérique à 10 caractères :

- 2 lettres-HU ou HU
- espace facultatif
- 8 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :

- La fonction Func_hungarian_value_added_tax_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_hungarian_value_added_tax_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :

- La fonction Func_hungarian_value_added_tax_number trouve le contenu qui correspond au modèle.

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

- compt
- Numéro de taxe sur la valeur ajoutée
- compt #
- vatno #
- hungarianvatno #
- n ° taxe
- ÁFA de taxe sur la valeur ajoutée
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám


## <a name="india-permanent-account-number-pan"></a>Numéro de compte permanent Inde (PAN)

### <a name="format"></a>Format

10 lettres ou chiffres

### <a name="pattern"></a>Modèle

10 lettres ou chiffres :
- Trois lettres (ne respectant pas la casse) 
- Lettre en C, P, H, F, A, T, B, L, J, G (ne respectant pas la casse)
- Une lettre
- Quatre chiffres 
- Une lettre (ne respecte pas la casse)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_india_permanent_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_india_permanent_account_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
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
- PANEUROPÉENNES 
   
## <a name="india-unique-identification-aadhaar-number"></a>Numéro d’identification unique (Aadhaar) Inde

### <a name="format"></a>Format

12 chiffres contenant éventuellement des espaces ou des tirets

### <a name="pattern"></a>Modèle

12 chiffres :
- Un chiffre qui est différent de 0 ou 1
- Trois chiffres 
- Éventuellement un tiret ou un espace  
- Quatre chiffres 
- Éventuellement un tiret ou un espace  
- Le chiffre final, qui est le chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_india_aadhaar trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_india_aadhar est trouvé.
- La somme de contrôle est correcte.
- 
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :

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
   
## <a name="indonesia-identity-card-ktp-number"></a>Numéro de carte d’identité (KTP) Indonésie

### <a name="format"></a>Format

16 chiffres contenant éventuellement des points

### <a name="pattern"></a>Modèle

16 chiffres :
- Code à deux chiffres désignant la province  
- Un point (facultatif)  
- Code à deux chiffres désignant une régence ou une ville  
- Code à deux chiffres désignant un sous-district  
- Un point (facultatif)  
- Six chiffres au format JJMMAA qui correspondent à la date de naissance  
- Un point (facultatif)  
- Quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :

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

ad, ae, al, at, az, ba, be, bg, bh, ch, cr, cy, cz, de, dk, do, ee, es, fi, fo, fr, gb, ge, gi, gl, gr, hr, hu, ie, il, is, it, kw, kz, lb, li, lt, lu, lv, mc, md, me, mk, mr, mt, mu, nl, no, pl, pt, ro, rs, sa, se, si, sk, sm, tn, tr, vg

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :

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

   
## <a name="international-classification-of-diseases-icd-10-cm"></a>Classification internationale des maladies (ICD-10-CM)

### <a name="format"></a>Format

Dictionary

### <a name="pattern"></a>Modèle

Mot clé

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- Un mot clé depuis Dictionary_icd_10_updated est trouvé.
- Un mot clé depuis Dictionary_icd_10_codes est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- Un mot clé depuis Dictionary_icd_10_ mis à jour est trouvé.

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

Tout terme du dictionnaire de mots clés Dictionary_icd_10_updated, qui est basé sur la [Classification internationale des maladies, dixième révision, modification clinique (ICD-10-cm)](https://go.microsoft.com/fwlink/?linkid=852604). Ce type recherche uniquement le terme, pas les codes d’assurance.

Tout terme du dictionnaire de mots clés Dictionary_icd_10_codes, qui est basé sur la [Classification internationale des maladies, dixième révision, modification clinique (ICD-10-cm)](https://go.microsoft.com/fwlink/?linkid=852604). Ce type recherche uniquement les codes d’assurance, pas la description.

## <a name="international-classification-of-diseases-icd-9-cm"></a>Classification internationale des maladies (ICD-9-CM)

### <a name="format"></a>Format

Dictionary

### <a name="pattern"></a>Modèle

Mot clé

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- Un mot clé depuis Dictionary_icd_9_updated est trouvé.
- Un mot clé depuis Dictionary_icd_9_codes est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- Un mot clé depuis Dictionary_icd_9_updated est trouvé.

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

Tout terme du dictionnaire de mots clés Dictionary_icd_9_updated, qui est basé sur la [Classification internationale des maladies, neuvième révision, modification clinique (ICD-9-cm)](https://go.microsoft.com/fwlink/?linkid=852605). Ce type recherche uniquement le terme, pas les codes d’assurance.

Tout terme du dictionnaire de mots clés Dictionary_icd_9_codes, qui est basé sur la [Classification internationale des maladies, neuvième révision, modification clinique (ICD-9-cm)](https://go.microsoft.com/fwlink/?linkid=852605). Ce type recherche uniquement les codes d’assurance, pas la description.

## <a name="ip-address"></a>Adresse IP

### <a name="format"></a>Format

#### <a name="ipv4"></a>IPv6
Modèle complexe qui tient compte des versions mises en forme (points) et non mises en forme (sans points) des adresses IPv4

#### <a name="ipv6"></a>IPv4/IPv6
 Modèle complexe qui tient compte des numéros IPv6 mis en forme (qui incluent les signes deux-points)

### <a name="pattern"></a>Modèle

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Pour IPv6, le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_ipv6_address trouve un contenu qui correspond au modèle.
- Aucun mot clé figurant dans la liste Keyword_ipaddress n’est trouvé.

Pour IPv4, le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 95 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_ipv4_address trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ipaddress est trouvé.

Pour IPv6, le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 95 % si, dans une proximité de 300 caractères :
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

- IP (ce mot clé respecte la casse)
- ip address 
- adresses IP
- protocole internet
- IP-כתובת ה 

## <a name="ireland-drivers-license-number"></a>Numéro de permis de conduire Ireland

### <a name="format"></a>Format

Six chiffres suivis de quatre lettres
  
### <a name="pattern"></a>Modèle

Six chiffres et quatre lettres :
  
- Six chiffres
- Quatre lettres (ne respectent pas la casse)
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- L’expression régulière  `Regex_ireland_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_ireland_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_ireland_eu_drivers_license_number"></a>Keywords_ireland_eu_driver’s_license_number

- ceadúnas tiomána
- ceadúnais tiomána

## <a name="ireland-passport-number"></a>Numéro de passeport Irlande

Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

Deux lettres ou chiffres suivis de sept chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

Deux lettres ou chiffres suivis de sept chiffres :
  
- Deux chiffres ou lettres (ne respectent pas la casse)
- Sept chiffres
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
  
- L’expression régulière  `Regex_ireland_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_ireland_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_ireland_eu_passport_number"></a>Keywords_ireland_eu_passport_number

- passeport numérique
- uimhreacha pasanna
- uimhir pas
- uimhir
- uimhreacha pas
- uimhir cárta
- uimhir chárta

## <a name="ireland-personal-public-service-pps-number"></a>Numéro PPS (Personal public service) pour l’Irlande

### <a name="format"></a>Format

Ancien format (jusqu’au 31 décembre 2012) :
- sept chiffres suivis de 1-2 lettres 

Nouveau format (1er janvier 2013 et après) :
- sept chiffres suivis de deux lettres

### <a name="pattern"></a>Modèle

Ancien format (jusqu’au 31 décembre 2012) :
- sept chiffres 
- une à deux lettres (ne respectant pas la casse) 

Nouveau format (1er janvier 2013 et après) :
- sept chiffres 
- une lettre (ne respectant pas la casse), qui est un chiffre de contrôle alphabétique 
- Une lettre facultative dans la plage A-I, ou « W »

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_ireland_pps trouve un contenu qui correspond au modèle.
- Un mot clé depuis Keywords_ireland_eu_national_id_card est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
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
- Numéro d’identification personnel
- Numéro de service public
- Numéro de service personnel
- phearsanta seirbhíse poiblí
- n ° PPS
- numéro PPS
- numéro PPS
- n ° de Service PPS
- ppsn
- ppsno #
- ppsno
- toxine
- Numéro de service public
- publicserviceno #
- publicserviceno
- Numéro de produit et d’assurance sociale
- RSI non
- numéro RSI
- rsin
- client aitheantais seirbhís
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phearsanta
- uimhir phearsanta seirbhíse poiblí
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #


## <a name="israel-bank-account-number"></a>Numéro de compte bancaire Israël

### <a name="format"></a>Format

13 chiffres

### <a name="pattern"></a>Modèle

Avec
- deux chiffres 
- un tiret 
- trois chiffres 
- un tiret 
- huit chiffres

Non
- 	13 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
   
## <a name="israel-national-identification-number"></a>Numéro d’identification nationale Israël

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
-   Numéro d’identification
-   n ° d’identité        
-   identitynumber #
-   Numéro d’identité
-   israeliidentitynumber       
-   ID personnel
-   ID unique  

   
## <a name="italy-drivers-license-number"></a>Numéro de permis de conduire Italie

### <a name="format"></a>Format

une combinaison de 10 lettres et chiffres

### <a name="pattern"></a>Modèle

une combinaison de 10 lettres et chiffres :
- une lettre (ne respecte pas la casse) 
- la lettre « A » ou « V » (ne respecte pas la casse) 
- sept chiffres
- une lettre (ne respecte pas la casse)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_italy_drivers_license_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_italy_drivers_license_number est trouvé.

```xml
<!-- Italy Driver's license Number -->
<Entity id="97d6244f-9157-41bd-8e0c-9d669a5c4d71" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_italy_drivers_license_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_italy_drivers_license_number" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_italy_drivers_license_number"></a>Keyword_italy_drivers_license_number

- nombre di brevet di
- patente di guida 
- Guida brevet
- breveti di Guida
- breveti Guida

## <a name="italy-fiscal-code"></a>Code fiscal Italie
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

combinaison de 16 caractères de lettres et de chiffres dans le modèle spécifié.
  
### <a name="pattern"></a>Modèle

Combinaison de lettres et de chiffres de 16 caractères :
- trois lettres qui correspondent aux trois premières consonnes du nom de la famille
- trois lettres qui correspondent à la première, troisième et quatrième consonnes du prénom
- deux chiffres correspondant aux derniers chiffres de l’année de naissance
- une lettre correspondant à la lettre du mois de naissance : les lettres sont utilisées dans l’ordre alphabétique, mais seules les lettres de A à E, H, L, M, P, R à T sont utilisées (par conséquent, le mois de janvier est A et le mois d’octobre est R).
- deux chiffres correspondant au jour du mois de naissance — afin de différencier les hommes, 40 est ajouté au jour de naissance pour les femmes
- quatre chiffres correspondant à l’indicatif régional propre à la municipalité où la personne est né (des codes pays sont utilisés pour les pays étrangers)
- un chiffre de parité
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_italy_eu_national_id_card` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_italy_eu_national_id_card` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_italy_eu_national_id_card` trouve le contenu qui correspond au modèle. 
    
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
- Codice fiscale
- codice ID personnel
- codice Personal
- code fiscal
- numération Certificate-personnel
- numération di IDENTIFICAZIONE fiscale
- ID de numérotation personnelle
- numération personnelle
- Numéro de certificat personnel
- code personnel
- code d’identification personnel
- Numéro d’identification personnel
- personalcodeno #
- Code de taxe
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- Numéro d’identité fiscale
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #


## <a name="italy-passport-number"></a>Numéro de passeport Italie
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

deux lettres ou chiffres suivis de sept chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

deux lettres ou chiffres suivis de sept chiffres :
  
- deux chiffres ou lettres (ne respectant pas la casse)
- sept chiffres
    
### <a name="checksum"></a>Somme de contrôle

non applicable
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_italy_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_italy_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_italy_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_italy_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_italy_eu_passport_number"></a>Keywords_italy_eu_passport_number

- italiana passaporto
- passaporto italiana
- passaporto numérique
- numéro passeport
- numération di passaporto
- chiffresi del passaporto
- passeport italien

## <a name="italy-value-added-tax-number"></a>Numéro de TVA Italie valeur ajoutée
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

modèle alphanumérique de 13 caractères avec délimiteurs facultatifs

### <a name="pattern"></a>Modèle

modèle alphanumérique de 13 caractères avec délimiteurs facultatifs :

- I ou i
- T ou t
- espace, point, tiret ou virgule facultatif
- 11 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_italy_value_added_tax_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_italy_value_added_tax_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_italy_value_added_tax_number trouve le contenu qui correspond au modèle.

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

- Numéro de TVA
- n ° TVA
- compt #
- bis
- bis #


## <a name="japan-bank-account-number"></a>Numéro de compte bancaire japonais

### <a name="format"></a>Format

sept ou huit chiffres

### <a name="pattern"></a>Modèle

Numéro de compte bancaire :
- sept ou huit chiffres
- Code de succursale du compte bancaire :
- quatre chiffres 
- un espace ou un tiret (facultatif) 
- trois chiffres

Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_jp_bank_account trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_bank_account est trouvé.
- L’une des affirmations suivantes est vraie :
- La fonction Func_jp_bank_account_branch_code trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_bank_branch_code est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- driver'slicense
- driverslicenses
- driver'slicenses
- driverlicenses
- LD #
- distribution #
- Profil #
- conduire #
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


## <a name="japan-my-number---corporate"></a>Mon numéro japonais-entreprise
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

numéro à 13 chiffres

### <a name="pattern"></a>Modèle

numéro à 13 chiffres :

- un chiffre entre un et neuf
- 12 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_japanese_my_number_corporate trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_japanese_my_number_corporate est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_japanese_my_number_corporate trouve le contenu qui correspond au modèle.

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

- Numéro d’entreprise
- マイナンバー
- 共通番号
- マイナンバーカード
- マイナンバーカード番号
- 個人番号カード
- 個人識別番号
- 個人識別ナンバー
- 法人番号
- 指定通知書


## <a name="japan-my-number---personal"></a>Mon numéro-personnel
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

numéro à 12 chiffres

### <a name="pattern"></a>Modèle

numéro à 12 chiffres :

- quatre chiffres
- espace, point ou tiret facultatif
- quatre chiffres
- espace, point ou tiret facultatif
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_japanese_my_number_personal trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_japanese_my_number_personal est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- La fonction Func_japanese_my_number_personal trouve le contenu qui correspond au modèle.

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

   
## <a name="japan-passport-number"></a>Numéro de passeport japonais

### <a name="format"></a>Format

deux lettres suivies de sept chiffres

### <a name="pattern"></a>Modèle

deux lettres (ne respectant pas la casse) suivies de sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

- Tel
- Numéro de passeport
- Numéro de passeport
- # Passeport
- パスポート
- パスポート番号
- パスポートナンバー
- パスポート＃
- パスポート #
- パスポートNo.
- 旅券番号
- 旅券番号＃
- ♯ 旅券番号
- 旅券ナンバー


## <a name="japan-residence-card-number"></a>Numéro de carte de séjour Japon

### <a name="format"></a>Format

12 lettres et chiffres

### <a name="pattern"></a>Modèle

12 lettres et chiffres :
- deux lettres (ne respectant pas la casse)
- huit chiffres 
- deux lettres (ne respectant pas la casse)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_jp_residence_card_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keyword_jp_residence_card_number est trouvé.

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

- Numéro de carte de séjour
- N ° carte de séjour
- Carte de séjour #
- 在留カード番号
- 在留カード
- 在留番号

## <a name="japan-resident-registration-number"></a>Numéro d’enregistrement de résident Japon

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

   
## <a name="japan-social-insurance-number-sin"></a>Numéro d’assurance sociale japonaise (SIN)

### <a name="format"></a>Format

7 à 12 chiffres

### <a name="pattern"></a>Modèle

7 à 12 chiffres :
- quatre chiffres 
- un trait d’Union (facultatif) 
- six chiffres ou
- 7 à 12 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_jp_sin trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_sin est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- 社会保険No.
- 社会保険
- 介護保険
- 介護保険被保険者番号
- 健康保険被保険者整理番号
- 雇用保険被保険者整理番号
- 厚生年金
- 厚生年金被保険者整理番号


## <a name="latvia-drivers-license-number"></a>Numéro de permis de conduire de la Lettonie

### <a name="format"></a>Format

trois lettres suivies de six chiffres
  
### <a name="pattern"></a>Modèle

trois lettres et six chiffres :
  
- trois lettres (ne respectent pas la casse) 
- six chiffres
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_latvia_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_latvia_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_latvia_eu_drivers_license_number"></a>Keywords_latvia_eu_driver’s_license_number

- autovadītāja apliecība
- autovadītāja apliecības
- vadītāja apliecība

## <a name="latvia-personal-code"></a>Code personnel en Lettonie

### <a name="format"></a>Format

11 chiffres et trait d’union conditionnel
  
### <a name="pattern"></a>Modèle

Ancien format

11 chiffres et un trait d’Union :
  
- six chiffres correspondant à la date de naissance (JJMMAA) 
- un trait d’Union
- un chiffre correspondant au siècle de naissance (« 0 » pour le 19 siècle, « 1 » pour le vingtième siècle et « 2 » pour le 21ème siècle).
- quatre chiffres, généré de manière aléatoire

Nouveau format

11 chiffres

- Deux chiffres "32"
- Neuf chiffres
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_latvia_eu_national_id_card` ou l’expression régulière `Regex_latvia_eu_national_id_card_new_format` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_latvia_eu_national_id_card` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_latvia_eu_national_id_card` ou l’expression régulière `Regex_latvia_eu_national_id_card_new_format` trouve le contenu qui correspond au modèle. 
    
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

- Numéro d’administration
- alvas nē
- Numéro de naissance
- Numéro de citoyen
- numéro civil
- Numéro de recensement électronique
- numéro électronique
- code fiscal
- Numéro d’utilisateur pour la santé
- Réf #
- ID-code
- numéro d’identification
- identifikācijas numurs
- ID-Number
- Numéro individuel
- latvija alva
- ID nacionālais
- id national
- Numéro d’identification nationale
- Numéro d’identité nationale
- numéro d’assurance nationale
- Numéro de registre national
- nodokļa numurs
- ID nodokļu
- nodokļu identifikācija numurs
- Numéro de certificat personnel
- code personnel
- code d’identification personnel
- Numéro d’identification personnel
- code d’identification personnel
- identificateur personnel
- Numéro d’identité personnelle
- numéro personnel
- code numérique personnel
- personalcodeno #
- Personas kods
- code d’identification de la population
- Numéro de service public
- numéro d’enregistrement
- Numéro de produit
- numéro d’assurance sociale
- numéro de sécurité sociale
- Code de taxe provinciale
- numéro de dossier fiscal
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #
- Numéro de l’électeur

## <a name="latvia-passport-number"></a>Numéro de passeport Lettonie
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

deux lettres ou chiffres suivis de sept chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

deux lettres ou chiffres suivis de sept chiffres :
  
- deux chiffres ou lettres (ne respectant pas la casse)
- sept chiffres
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_latvia_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_latvia_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_latvia_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_latvia_eu_passport_number"></a>Keywords_latvia_eu_passport_number

- pase numurs
- pase numur
- pases numuri
- Pases Nr
- passeport non
- n ° du passeport

## <a name="lithuania-drivers-license-number"></a>Numéro de permis de conduire de la Lituanie

### <a name="format"></a>Format

huit chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

huit chiffres 
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_lithuania_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_lithuania_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_lithuania_eu_drivers_license_number"></a>Keywords_lithuania_eu_driver’s_license_number

- vairuotojo pažymėjimas
- vairuotojo pažymėjimo
- vairuotojo pažymėjimo numeriai

## <a name="lithuania-personal-code"></a>Code personnel de Lituanie
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

11 chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

11 chiffres sans espaces ni délimiteurs :
  
- un chiffre (1-6) correspondant au sexe et au siècle de la personne
- six chiffres correspondant à la date de naissance (AAMMJJ) 
- trois chiffres correspondant au numéro de série de la date de naissance
- un chiffre de contrôle
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_lithuania_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_lithuania_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_lithuania_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
    
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
- Numéro de service du citoyen
- ID mokesčių
- mokesčių identifikavimas
- mokesčių identifikavimo
- mokesčių chiffres
- numéro d’identification nationale
- code personnel
- code numérique personnel
- piliečio paslaugos
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #
- unikalus identifikavimo kodas
- unikalus identifikavimo
- Numéro d’identification unique
- Numéro d’identité unique
- uniqueidentityno #

## <a name="lithuania-passport-number"></a>Numéro de passeport Lituanie
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

huit chiffres ou lettres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

huit chiffres ou lettres (ne respectant pas la casse)
  
### <a name="checksum"></a>Somme de contrôle

non applicable
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_lithuania_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_lithuania_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_lithuania_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_lithuania_eu_passport_number"></a>Keywords_lithuania_eu_passport_number

- Paso chiffres
- paso numeriai
- Paso Nr

## <a name="luxemburg-drivers-license-number"></a>Numéro de permis de conduire du Luxembourg

### <a name="format"></a>Format

six chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

six chiffres 
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_luxemburg_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_luxemburg_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_luxemburg_eu_drivers_license_number"></a>Keywords_luxemburg_eu_driver’s_license_number

- fahrerlaubnis
- Führerschäin

## <a name="luxemburg-national-identification-number-natural-persons"></a>Numéro d’identification nationale du Luxembourg (personnes physiques)
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

13 chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

13 chiffres :
  
- 11 chiffres 
- deux chiffres de contrôle
    
### <a name="checksum"></a>Somme de contrôle

oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_luxemburg_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_luxemburg_eu_national_id_card` est trouvé. 

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_luxemburg_eu_tax_file_number` trouve le contenu qui correspond au modèle. 


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

- ID eindeutige
- ID eindeutige-Nummer
- eindeutigeid #
- ID personnelle
- idpersonnelle #
- idpersonnelle
- code individuel
- ID individuel
- identification individuelle
- identité individuelle
- Numéro d’identification personnel
- ID personnel
- identification personnelle
- identité personnelle
- personalidno #
- personalidnumber #
- persönliche identifikationsnummer
- ID unique
- identité unique
- uniqueidkey #

## <a name="luxemburg-passport-number"></a>Numéro de passeport Luxembourg
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

huit chiffres ou lettres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

huit chiffres ou lettres (ne respectant pas la casse)
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_nation_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_nation_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_nation_eu_passport_number" />
          <Match idRef="Keywords_nation_eu_passport_number" />
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_nation_eu_passport_number"></a>Keywords_nation_eu_passport_number

- numéro de passeport
- Numéro de passeport letton
- Numéro de passeport
- passnummer

## <a name="luxemburg-national-identification-number-non-natural-persons"></a>Numéro d’identification nationale du Luxembourg (personnes non physiques)

### <a name="format"></a>Format

11 chiffres
  
### <a name="pattern"></a>Modèle

11 chiffres
  
- deux chiffres
- un espace facultatif 
- trois chiffres 
- un espace facultatif
- trois chiffres 
- un espace facultatif
- deux chiffres
- un chiffre de contrôle
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_luxemburg_eu_tax_file_number_non_natural` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_luxemburg_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_luxemburg_eu_tax_file_number_non_natural` trouve le contenu qui correspond au modèle. 
    
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
- étain non
- étain #
- identificateur d’impôt
- identifikatiounsnummer taxe luxembourgeoise
- numéro d’étain
- Numéro d’identification fiscal luxembourgeois
- Numéro d’identification fiscale
- sécurité sociale
- sozialunterstützung
- sozialversécherung
- sozialversicherungsausweis
- ID Steier
- steier identifikatiounsnummer
- steier nummer
- ID Steuer
- steueridentifikationsnummer
- steuernummer
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #
- zinn #
- zinn
- zinnzahl


## <a name="malaysia-identification-card-number"></a>Numéro de carte d’identification de Malaisie

### <a name="format"></a>Format

12 chiffres contenant éventuellement des traits d’union

### <a name="pattern"></a>Modèle

12 chiffres :
- six chiffres au format AAMMJJ correspondant à la date de naissance 
- un tiret (facultatif) 
- Code de lieu de naissance à deux lettres 
- un tiret (facultatif) 
- trois chiffres aléatoires 
- Code de sexe à un chiffre

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
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
- n ° i/c non
- combustion
- n ° IC
- carte d’identité
- Carte d’identification
- Carte d’identité
- k/p
- n ° k/p
- kad akuan diri
- Kad aplikasi numérique
- Kad Pengenalan Malaisie
- kgf
- KP non
- mykad
- mykas
- mykid
- mypr
- mytentera
- carte d’identité Malaisie
- carte d’identité malais
- NRIC
- carte d’identification personnelle

## <a name="malta-drivers-license-number"></a>Numéro de permis de conduire Malte

### <a name="format"></a>Format

Combinaison de deux caractères et six chiffres dans le modèle spécifié
  
### <a name="pattern"></a>Modèle

combinaison de deux caractères et six chiffres :
  
- deux caractères (chiffres ou lettres, ne respectant pas la casse)
- un espace (facultatif)
- trois chiffres
- un espace (facultatif)
- trois chiffres
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_malta_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_malta_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_malta_eu_drivers_license_number"></a>Keywords_malta_eu_driver’s_license_number

- Liċenzja-sewqan
- liċenzji-sewwieq


## <a name="malta-identity-card-number"></a>Numéro de carte d’identité Malte
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

sept chiffres suivis d’une lettre
  
### <a name="pattern"></a>Modèle

sept chiffres suivis d’une lettre :
  
- sept chiffres 
- une lettre dans « M, G, A, P, L, H, B, Z » (ne respecte pas la casse)
    
### <a name="checksum"></a>Somme de contrôle

Non applicable
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_malta_eu_national_id_card` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_malta_eu_national_id_card` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_malta_eu_national_id_card` trouve le contenu qui correspond au modèle. 
    
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

- Numéro de service du citoyen
- ID tat-Taxxa
- identifika numru tal-biljett
- Kodiċi numerali
- numru ta’IDENTIFIKAZZJONI personnaliser
- numru ta’IDENTIFIKAZZJONI tat-Taxxa
- numru ta’IDENTIFIKAZZJONI uniku
- numru ta’identità uniku
- numru-Servizz taċ-ċittadin
- numru tat-Taxxa
- code numérique personnel
- Numéro d’identification unique
- Numéro d’identité unique
- uniqueidentityno #


## <a name="malta-passport-number"></a>Numéro de passeport de Malte
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

sept chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

sept chiffres 
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_malta_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_malta_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_malta_eu_passport_number"></a>Keywords_malta_eu_passport_number

- numru tal-passaport
- numri tal-passaport
- NRU Tal-Passaport

## <a name="malta-tax-identification-number"></a>Numéro d’identification fiscale Malte

### <a name="format"></a>Format

Pour les ressortissants maltais :
- sept chiffres et une lettre dans le modèle spécifié
  
Ressortissants non maltaises et entités maltaises :
- neuf chiffres
  
### <a name="pattern"></a>Modèle

Ressortissants maltaises : sept chiffres et une lettre
  
- sept chiffres 
- une lettre (ne respecte pas la casse)
    
Ressortissants non maltaises et entités maltaises : neuf chiffres
  
- neuf chiffres 
    
### <a name="checksum"></a>Somme de contrôle

Non applicable
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_malta_eu_tax_file_number`  ou `Regex_malta_eu_tax_file_number_non_maltese_national` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_malta_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_malta_eu_tax_file_number` ou `Regex_malta_eu_tax_file_number_non_maltese_national` trouve le contenu qui correspond au modèle. 
    
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

- Numéro de service du citoyen
- ID tat-Taxxa
- identifika numru tal-biljett
- Kodiċi numerali
- numru ta’IDENTIFIKAZZJONI personnaliser
- numru ta’IDENTIFIKAZZJONI tat-Taxxa
- numru ta’IDENTIFIKAZZJONI uniku
- numru ta’identità uniku
- numru-Servizz taċ-ċittadin
- numru tat-Taxxa
- code numérique personnel
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #
- Numéro d’identification unique
- Numéro d’identité unique
- uniqueidentityno #

## <a name="netherlands-citizens-service-bsn-number"></a>Numéro de service du citoyen néerlandais (BSN)

### <a name="format"></a>Format

huit à neuf chiffres contenant des espaces facultatifs

### <a name="pattern"></a>Modèle

huit chiffres :
- trois chiffres 
- un espace (facultatif) 
- trois chiffres 
- un espace (facultatif) 
- deux à trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
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
  
- BSN #
- BSN
- burgerservicenummer
- Numéro de service du citoyen
- Numéro de personne
- numéro personnel
- code numérique personnel
- numéro lié à la personne
- persoonlijk nummer
- persoonlijke Numerieke de code
- persoonsgebonden
- persoonsnummer
- sociaal-fiscaal nummer
- social-Numéro fiscal
- sofi
- sofinummer
- uniek identificatienummer
- uniek identiteitsnummer
- Numéro d’identification unique
- Numéro d’identité unique
- uniqueidentityno #

## <a name="netherlands-drivers-license-number"></a>Numéro de permis de conduire néerlandais

### <a name="format"></a>Format

dix chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

dix chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_netherlands_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_netherlands_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_netherlands_eu_drivers_license_number"></a>Keywords_netherlands_eu_driver’s_license_number

- permis de conduire
- rijbewijs
- rijbewijsnummer
- rijbewijzen
- rijbewijs nummer
- rijbewijsnummers


## <a name="netherlands-passport-number"></a>Numéro de passeport néerlandais
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

neuf lettres ou chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

neuf lettres ou chiffres
  
### <a name="checksum"></a>Somme de contrôle

non applicable
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_netherlands_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_netherlands_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_netherlands_eu_passport_number" />
          <Match idRef="Keywords_netherlands_eu_passport_number" />
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_netherlands_eu_passport_number"></a>Keywords_netherlands_eu_passport_number

- Numéro de passeport néerlandais
- numéro de passeport
- Numéro de passeport néerlandais
- nederlanden paspoort nummer
- paspoort
- nederlanden paspoortnummer
- paspoortnummer

## <a name="netherlands-tax-identification-number"></a>Numéro d’identification fiscale néerlandaise
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

neuf chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

neuf chiffres 
  
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_netherlands_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_netherlands_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- La fonction  `Func_netherlands_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
    
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
- identification fiscale hollânske
- Numéro d’identification Hulandes Impuesto
- Hulandes Impuesto identification
- identificatienummer qui a été modifié
- identificatienummer van à l’avant-dernière
- Numéro d’identification Impuesto
- numéro Impuesto
- néerlandais qui a pour ID Nummer
- néerlandais qui a identificatie
- néerlandais qui a identificatienummer
- Néerlandais belastingnummer
- Nederlandse qui a identificatie
- identification fiscale néerlandaise
- identification fiscale de Netherland
- étain (Pays-Bas)
- Netherland d’étain
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- Tal d’identification fiscale
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxe Tal
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #


## <a name="netherlands-value-added-tax-number"></a>Numéro de taxe ajoutée pour les pays-bas
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

modèle alphanumérique de 14 caractères

### <a name="pattern"></a>Modèle

modèle alphanumérique de 14 caractères :

- N ou n
- L ou l
- espace, point ou tiret facultatif
- neuf chiffres
- espace, point ou tiret facultatif
- B ou b
- deux chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_netherlands_value_added_tax_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_netherlands_value_added_tax_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_netherlands_value_added_tax_number trouve le contenu qui correspond au modèle.

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

- Numéro de TVA
- n ° TVA
- compt #
- wearde tafoege Tax getal
- btw nûmer
- btw-nummer


## <a name="new-zealand-bank-account-number"></a>Numéro de compte bancaire Nouvelle-Zélande
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

modèle de 14 à 16 chiffres avec un délimiteur facultatif

### <a name="pattern"></a>Modèle

modèle de 14 à 16 chiffres avec un délimiteur facultatif :

- deux chiffres
- un trait d’Union ou un espace conditionnel
- 3 à 4 chiffres
- un trait d’Union ou un espace conditionnel
- sept chiffres
- un trait d’Union ou un espace conditionnel
- deux à trois chiffres
- un tiret ou un espace d’options

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_new_zealand_bank_account_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_new_zealand_bank_account_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_new_zealand_bank_account_number trouve le contenu qui correspond au modèle.

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


## <a name="new-zealand-drivers-license-number"></a>Numéro de permis de conduire de la Nouvelle-Zélande
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

modèle alphanumérique à huit caractères

### <a name="pattern"></a>Modèle

modèle alphanumérique à huit caractères

- deux lettres 
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_newzealand_driver_license_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_newzealand_driver_license_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- La fonction Func_newzealand_driver_license_number trouve le contenu qui correspond au modèle.

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
- Gestionnaire de la LIC
- permis de conduire
- permis de conduire
- driverslic
- driverslicence
- driverslicences
- pilotes Lic
- pilotes conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- permis de conduire
- driverlic #
- driverlics #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduite international
- permis de conduite internationaux
- Association automobile NZ
- Association automobile Nouvelle-Zélande


## <a name="new-zealand-inland-revenue-number"></a>Numéro de revenu intérieur Nouvelle-Zélande
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

huit ou neuf chiffres avec des délimiteurs facultatifs

### <a name="pattern"></a>Modèle

huit ou neuf chiffres avec des délimiteurs facultatifs

- deux ou trois chiffres
- un espace ou un tiret facultatif
- trois chiffres
- un espace ou un tiret facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_new_zealand_inland_revenue_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_new_zealand_inland_revenue_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_new_zealand_inland_revenue_number trouve le contenu qui correspond au modèle.

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

- n ° IRD
- IRD non #
- NZ IRD
- Nouvelle-Zélande IRD
- numéro IRD
- Numéro de revenu intérieur


## <a name="new-zealand-ministry-of-health-number"></a>Ministère de l’assurance Nouvelle-Zélande

### <a name="format"></a>Format

trois lettres, un espace (facultatif) et quatre chiffres

### <a name="pattern"></a>Modèle

- trois lettres (ne respectant pas la casse), sauf « I » et « O »
- un espace (facultatif) 
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_new_zealand_ministry_of_health_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_nz_terms est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- Intégrité
- destinations
- Numéro d’index d’intégrité nationale
- numéro NHI
- n ° NHI
- NHI #
- N ° d’index sanitaire national
- ID d’index d’intégrité nationale
- Index d’intégrité nationale #

## <a name="new-zealand-social-wlefare-number"></a>Numéro de wlefare sociale Nouvelle-Zélande
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres

- trois chiffres
- un trait d’union conditionnel
- trois chiffres
- un trait d’union conditionnel
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_newzealand_social_welfare_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_newzealand_social_welfare_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- La fonction Func_newzealand_social_welfare_number trouve le contenu qui correspond au modèle.

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

- Social Welfare #
- Social Welfare #
- n ° de bien-être social
- numéro Social Welfare
- swn #

   
## <a name="norway-identification-number"></a>Numéro d’identification de la Norvège

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres :
- six chiffres au format JJMMAA qui correspondent à la date de naissance 
- Numéro individuel à trois chiffres 
- deux chiffres de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_norway_id_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_norway_id_number est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- Identificateur
- Personnummer
- Fødselsnummer

   
## <a name="philippines-unified-multi-purpose-identification-number"></a>Numéro d’identification unifiée à usage unique pour les Philippines

### <a name="format"></a>Format

12 chiffres séparés par des traits d’union

### <a name="pattern"></a>Modèle

12 chiffres :
- quatre chiffres 
- un trait d’Union 
- sept chiffres 
- un trait d’Union 
- un chiffre

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

14 chiffres contenant 2 barres obliques
  
### <a name="pattern"></a>Modèle

14 chiffres et 2 barres obliques :
  
- cinq chiffres 
- une barre oblique
- deux chiffres
- une barre oblique
- sept chiffres
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_poland_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_poland_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_poland_eu_drivers_license_number"></a>Keywords_poland_eu_driver’s_license_number

- prawo jazdy
- prawa jazdy

## <a name="poland-identity-card"></a>Carte d’identité Pologne

### <a name="format"></a>Format

trois lettres et six chiffres

### <a name="pattern"></a>Modèle

trois lettres (ne respectant pas la casse) suivies de six chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- Chiffre dowodu osobistego
- Nazwa i dowodu osobistego
- Nazwa i Nr dowodu osobistego
- Nazwa je nr dowodu tożsamości
- Dowód Tożsamości
- Dow. OS.

   
## <a name="poland-national-id-pesel"></a>ID national Pologne (PESEL)

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

- 6 chiffres représentant la date de naissance au format AAMMJJ
- 4 chiffres
- 1 chiffre de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_pesel_identification_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_pesel_identification_number est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

- dowód osobisty
- dowódosobisty
- niepowtarzalny
- niepowtarzalnynumer
- Nr.-PESEL
- Nr-PESEL
- numéro identyfikacyjny
- PESEL
- tożsamości narodowej

   
## <a name="poland-passport-number"></a>Numéro de passeport polonais
Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles du numéro de passeport de l’UE et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

deux lettres et sept chiffres

### <a name="pattern"></a>Modèle

Deux lettres (ne respectant pas la casse) suivies de sept chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_polish_passport_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_polish_national_id_passport_number est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- Poland Passport Number -->
<Entity id="03937FB5-D2B6-4487-B61F-0F8BFF7C3517" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_passport_number" />
          <Match idRef="Keyword_polish_national_id_passport_number" />
      </Pattern>
</Entity>
</Version>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_poland_national_id_passport_number"></a>Keyword_poland_national_id_passport_number

- Numéro paszportu
- Nr. Paszportu
- Paszport

## <a name="poland-regon-number"></a>Numéro REGON Pologne
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

nombre à neuf chiffres ou à 14 chiffres

### <a name="pattern"></a>Modèle

nombre à neuf chiffres ou 14 chiffres :

- neuf chiffres ou 
- neuf chiffres
- signe
- cinq chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_polish_regon_number trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_polish_regon_number est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- La fonction Func_polish_regon_number trouve le contenu qui correspond au modèle.

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

- ID REGON
- numéro statistique
- code statistique
- non statistique
- numéro REGON
- regonid #
- regonno #
- ID de la société
- CompanyID #
- companyidno #
- numéro Statystyczny
- numération REGON
- numerstatystyczny #
- numeruregon #


## <a name="poland-tax-identification-number"></a>Numéro d’identification de taxe polonais
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

11 chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

11 chiffres
  
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_poland_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_poland_eu_tax_file_number` est trouvé. 
    
  
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

- pince #
- pince
- chiffre identyfikacji podatkowej
- numeridentyfikacjipodatkowej #
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #
- Numéro de TVA #
- Numéro de TVA
- n ° TVA
- Numéro de TVA
- vatid #
- vatid
- vatno #
   

## <a name="portugal-citizen-card-number"></a>Numéro de carte de citoyen Portugal

### <a name="format"></a>Format

huit chiffres

### <a name="pattern"></a>Modèle

huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
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
- cartão de Cidadão
- carte de citoyen
- Numéro de document
- Documento de identificação
- Numéro d’identification
- Numéro d’identification
- numéro d’identification
- n ° carte d’identité
- Numéro de carte d’identité
- carte d’identité nationale
- HBAiSCSI
- número bi de Portugal
- Número de identificação civil
- Número de identificação fiscal
- número do Documento
- Numéro de bi Portugal


## <a name="portugal-drivers-license-number"></a>Numéro de permis de conduire du fabricant Portugal

### <a name="format"></a>Format

deux motifs : deux lettres suivies de 5-8 chiffres avec des caractères spéciaux
  
### <a name="pattern"></a>Modèle

Modèle 1 : deux lettres suivies de 5/6 avec des caractères spéciaux :
- Deux lettres (ne respectent pas la casse)
- Un trait d’union 
- Cinq ou six chiffres
- Un espace
- Un chiffre

Modèle 2 : une lettre suivie de 6/8 chiffres avec des caractères spéciaux :
- Une lettre (ne respecte pas la casse)
- Un trait d’union 
- Six ou huit chiffres
- Un espace
- Un chiffre

    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_portugal_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_portugal_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_portugal_eu_drivers_license_number"></a>Keywords_portugal_eu_driver’s_license_number

- Carteira de motorista
- carteira motorista
- Carteira de habilitação
- carteira habilitação
- Número de Licença
- número licença
- permissão de condução
- permissão condução
- Licença CONDUÇÃO Portugal
- Carta de condução

## <a name="portugal-passport-number"></a>Numéro de passeport Portugal
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

une lettre suivie de six chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

une lettre suivie de six chiffres :
  
- une lettre (ne respecte pas la casse)
- six chiffres
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_portugal_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_portugal_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_portugal_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_portugal_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_portugal_eu_passport_number"></a>Keywords_portugal_eu_passport_number

- número do Passaporte
- passeport Portugais
- passeport Portugais
- Passaporte Portugais
- Passaporte n º
- passeport n º
- números de Passaporte
- passeports Portugais
- número passaporte
- números passaporte

## <a name="portugal-tax-identification-number"></a>Numéro d’identification fiscale du Portugal

### <a name="format"></a>Format

neuf chiffres avec des espaces facultatifs
  
### <a name="pattern"></a>Modèle

- 3 chiffres
- un espace facultatif
- 3 chiffres
- un espace facultatif
- 3 chiffres
  
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_portugal_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_portugal_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- La fonction  `Func_portugal_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
    
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

- CPF #
- CPF
- nPour #
- nPour
- Número de identificação fisca
- chiffres fiscaux
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #


## <a name="romania-drivers-license-number"></a>Numéro de permis de conduire roumain

### <a name="format"></a>Format

un caractère suivi de huit chiffres
  
### <a name="pattern"></a>Modèle

un caractère suivi de huit chiffres :
- une lettre (ne respecte pas la casse) ou un chiffre 
- huit chiffres
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_romania_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_romania_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_romania_eu_drivers_license_number"></a>Keywords_romania_eu_driver’s_license_number

- permis de conducere
- permisului de conducere
- permisului conducere
- permisele de conducere
- permisele conducere
- permis conducere

## <a name="romania-personal-numeric-code-cnp"></a>Code numérique de la Roumanie (CNP)
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

13 chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

- 1 chiffre de 1-9
- 6 chiffres représentant la date de naissance (AAMMJJ)
- 2 chiffres qui peuvent être 01-52 ou 99
- 4 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_romania_eu_national_id_card` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_romania_eu_national_id_card` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_romania_eu_national_id_card` trouve le contenu qui correspond au modèle. 
    
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
- COD IDENTIFICARE personnel
- COD numérique personnel
- COD UNIC IDENTIFICARE
- codnumericpersonal #
- codul fiscale Nr.
- identificarea fiscală Nr #
- ID-UL taxei
- Numéro d’assurance
- insurancenumber #
- ID national #
- id national
- numéro d’identification nationale
- număr IDENTIFICARE personnel
- număr identitate
- UNIC personnel număr
- număridentitate #
- număridentitate
- numărpersonalunic #
- numărpersonalunic
- număru de IDENTIFICARE fiscală
- numărul de IDENTIFICARE fiscală
- code numérique personnel
- ancre #
- ancre
- n ° fichier taxe
- numéro de dossier fiscal
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #
- Numéro d’identification unique
- Numéro d’identité unique
- uniqueidentityno #
- uniqueidentityno

## <a name="romania-passport-number"></a>Numéro de passeport roumain
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

huit ou neuf chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

huit ou neuf chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_romania_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_romania_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_romania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_romania_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_romania_eu_passport_number"></a>Keywords_romania_eu_passport_number

numărul pașaportului numarul pasaportului numerele pașaportului Pașaport Nr

## <a name="russia-passport-number-domestic"></a>Numéro de passeport russe-Suisse
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

nombre à dix chiffres

### <a name="pattern"></a>Modèle

nombre à dix chiffres :

- deux chiffres
- un espace ou un tiret facultatif
- deux chiffres
- un espace facultatif
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression Regex Regex_Russian_Passport_Number_Domestic trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keyword_Russian_Passport_Number est trouvé.

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
- Numéro de passeport
- tel #
- ID de passeport
- n ° passeport #
- passportnumber #
- паспорт нет
- ID паспорт
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #


## <a name="russia-passport-number-international"></a>Numéro de passeport russe international
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

numéro à neuf chiffres

### <a name="pattern"></a>Modèle

numéro à neuf chiffres :

- deux chiffres
- un espace ou un tiret facultatif
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression Regex Regex_Russian_Passport_Number_International trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keyword_Russian_Passport_Number est trouvé.

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
- Numéro de passeport
- tel #
- ID de passeport
- n ° passeport #
- passportnumber #
- паспорт нет
- ID паспорт
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #


## <a name="saudi-arabia-national-id"></a>ID national Arabie saoudite

### <a name="format"></a>Format

dix chiffres

### <a name="pattern"></a>Modèle

dix chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

   
## <a name="singapore-national-registration-identity-card-nric-number"></a>Numéro de carte d’identité d’enregistrement national (NRIC) Singapour

### <a name="format"></a>Format

neuf lettres et chiffres

### <a name="pattern"></a>Modèle

- neuf lettres et chiffres :
- la lettre « F », « G », « S » ou « T » (ne respecte pas la casse) 
- sept chiffres 
- un chiffre de contrôle alphabétique

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière Regex_singapore_nric trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_singapore_nric est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- COMBUSTION 
- Foreign Identification Number 
- ECHERCHER 
- 身份证 
- 身份證 

## <a name="slovakia-drivers-license-number"></a>Numéro de permis de conduire Slovaquie

### <a name="format"></a>Format

un caractère suivi de sept chiffres
  
### <a name="pattern"></a>Modèle

un caractère suivi de sept chiffres
  
- une lettre (ne respecte pas la casse) ou un chiffre
- sept chiffres 
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_slovakia_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_slovakia_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_slovakia_eu_drivers_license_number"></a>Keywords_slovakia_eu_driver’s_license_number

- vodičský preukaz
- vodičské preukazy
- vodičského preukazu
- vodičských preukazov

## <a name="slovakia-personal-number"></a>Numéro personnel de Slovaquie
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

neuf ou dix chiffres contenant une barre oblique inverse facultative
  
### <a name="pattern"></a>Modèle

- 6 chiffres représentant la date de naissance
- barre oblique (/) facultative
- 3 chiffres
- 1 chiffre de contrôle facultatif
  
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_slovakia_eu_national_id_card` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_slovakia_eu_national_id_card` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- La fonction  `Func_slovakia_eu_national_id_card` trouve le contenu qui correspond au modèle. 
    
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
- Numéro de naissance
- číslo národnej identifikačnej karty
- číslo občianského preukazu
- daňové číslo
- Numéro d’identification
- Numéro d’identification
- numéro d’identification
- identifikačná karta č
- identifikačné číslo
- n ° carte d’identité
- Numéro de carte d’identité
- národná identifikačná značka č
- numéro national
- nationalnumber #
- nemzeti személyazonosító igazolvány
- personalidnumber #
- rč
- rodne cislo
- rodné číslo
- numéro de sécurité sociale
- SSN #
- SSN
- személyi igazolvány szám
- személyi igazolvány száma
- személyigazolvány szám
- n ° fichier taxe
- numéro de dossier fiscal
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #

## <a name="slovakia-passport-number"></a>Numéro de passeport slovaque
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

un chiffre ou une lettre suivi de sept chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

un chiffre ou une lettre (ne respectant pas la casse) suivi de sept chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_slovakia_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_slovakia_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_slovakia_eu_passport_number"></a>Keywords_slovakia_eu_passport_number

- číslo pasu
- čísla pasov
- pas de č.
- Passeport n °
- n ° passeport

## <a name="slovenia-drivers-license-number"></a>Numéro de permis de conduire Slovénie

### <a name="format"></a>Format

neuf chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

neuf chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_slovenia_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_slovenia_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_slovenia_eu_drivers_license_number"></a>Keywords_slovenia_eu_driver’s_license_number

- vozniško dovoljenje
- licence vozniška številka
- vozniških dovoljenj
- številka vozniškega dovoljenja
- številke vozniških dovoljenj

## <a name="slovenia-unique-master-citizen-number"></a>Numéro de citoyen principal unique Slovénie
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

13 chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

13 chiffres dans le modèle spécifié :
  
- sept chiffres correspondant à la date de naissance (DDMMLLL) où « LLL » correspond aux trois derniers chiffres de l’année de naissance 
- deux chiffres correspondant à la zone de naissance « 50 »
- trois chiffres correspondant à une combinaison de sexe et de numéro de série pour les personnes nées le même jour (000-499 pour les mâles et les 500-999 pour les femelles)
- un chiffre de contrôle
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_slovenia_eu_national_id_card` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_slovenia_eu_national_id_card` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_slovenia_eu_national_id_card` trouve le contenu qui correspond au modèle. 
    
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
- ID Nacionalna
- Nacionalni potni liste
- id national
- osebna izkaznica
- osebni koda
- osebni ne
- osebni številka
- code personnel
- numéro personnel
- code numérique personnel
- številka državljana
- Numéro de citoyen unique
- Numéro d’identification unique
- Numéro d’identité unique
- Numéro de citoyen principal unique
- Numéro d’enregistrement unique
- uniqueidentityno #
- uniqueidentityno #

## <a name="slovenia-passport-number"></a>Numéro de passeport Slovénie
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

deux lettres suivies de sept chiffres, sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

deux lettres suivies de sept chiffres :
  
- la lettre « P »
- une lettre majuscule
- sept chiffres
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_slovenia_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_slovenia_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_slovenia_eu_passport_number"></a>Keywords_slovenia_eu_passport_number

- številka potnega lista
- potek veljavnosti
- liste potni #
- Référence rojstva
- liste potni
- številke potnih listov

## <a name="slovenia-tax-identification-number"></a>Numéro d’identification fiscale de la Slovénie
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

huit chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

- un chiffre de 1-9
- six chiffres
- un chiffre de contrôle
  
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_slovenia_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_slovenia_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- La fonction  `Func_slovenia_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
    
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
- n ° fichier taxe
- numéro de dossier fiscal
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #


## <a name="south-africa-identification-number"></a>Numéro d’identification Afrique du Sud

### <a name="format"></a>Format

13 chiffres pouvant contenir des espaces

### <a name="pattern"></a>Modèle

13 chiffres :
- six chiffres au format AAMMJJ correspondant à la date de naissance 
- quatre chiffres 
- indicateur de citoyenneté à un seul chiffre 
- le chiffre « 8 » ou « 9 » 
- un chiffre qui est un chiffre de la somme de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
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
- Identificateur 
   
## <a name="south-korea-resident-registration-number"></a>Numéro d’enregistrement résident Corée du Sud

### <a name="format"></a>Format

13 chiffres contenant un trait d’union

### <a name="pattern"></a>Modèle

13 chiffres :
- six chiffres au format AAMMJJ correspondant à la date de naissance 
- un trait d’Union 
- un chiffre déterminé par le siècle et le sexe 
- Code de région de naissance à quatre chiffres 
- un chiffre utilisé pour différencier les personnes dont les numéros précédents sont identiques 
- un chiffre de contrôle.

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_south_korea_resident_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_south_korea_resident_number est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

## <a name="spain-drivers-license-number"></a>Numéro de permis de conduire Espagne

### <a name="format"></a>Format

huit chiffres suivis d’un caractère
  
### <a name="pattern"></a>Modèle

huit chiffres suivis d’un caractère :
  
- huit chiffres 
- un chiffre ou une lettre (ne respectant pas la casse)
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_spain_eu_DL_and_NI_number_citizen` ou `Func_spain_eu_DL_and_NI_number_foreigner` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_spain_eu_driver's_license_number` est trouvé. 

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_spain_eu_DL_and_NI_number_citizen` ou `Func_spain_eu_DL_and_NI_number_foreigner` trouve le contenu qui correspond au modèle. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_spain_eu_drivers_license_number"></a>Keywords_spain_eu_driver’s_license_number

- permiso de Conducción
- permiso conducción
- licencia de conducir
- licencia conducir
- permiso conducir
- permiso de conducir
- permisos de conducir
- permisos conducir
- carnet conducir
- carnet de conducir
- licencia de manejo
- licencia manejo

## <a name="spain-dni"></a>Espagne DNI
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

huit chiffres suivis d’un caractère
  
### <a name="pattern"></a>Modèle

sept chiffres suivis d’un caractère
  
- huit chiffres
- Un espace ou un tiret facultatif
- une lettre de vérification (ne respecte pas la casse)
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_spain_eu_DL_and_NI_number_citizen` ou `Func_spain_eu_DL_and_NI_number_foreigner` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_spain_eu_national_id_card"` est trouvé. 

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_spain_eu_DL_and_NI_number_citizen` ou `Func_spain_eu_DL_and_NI_number_foreigner` trouve le contenu qui correspond au modèle. 

    
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

- Carné de identidad
- DNI #
- DNI
- dninúmero #
- Documento Nacional de identidad
- identidad único
- identidadúnico #
- Numéro d’assurance
- numéro d’identification nationale
- identité nationale
- nationalid #
- nationalidno #
- nie #
- nie
- nienúmero #
- Número de Identificación
- número Nacional identidad
- Numéro d’identification personnel
- n ° d’identité personnelle
- Numéro d’identité unique
- quei #

## <a name="spain-passport-number"></a>Numéro de passeport Espagne
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’informations sensibles du numéro de passeport de l’UE.

### <a name="format"></a>Format

combinaison de huit ou neuf caractères de lettres et de chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

combinaison de huit ou neuf caractères de lettres et de chiffres :
  
- deux chiffres ou lettres 
- un chiffre ou une lettre (facultatif)
- six chiffres
    
### <a name="checksum"></a>Somme de contrôle

Non applicable
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_spain_eu_passport_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_passport_number_common` ou `Keywords_spain_eu_passport_number` est trouvé. 
    
```xml
 <!-- EU Passport Number -->
<Entity id="21883626-6245-4f3d-9b61-5cbb43e625ee" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_spain_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number_common" />
            <Match idRef="Keywords_spain_eu_passport_number" />
          </Any>
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- tel #
- tel #
- passportid
- passeports
- n ° passeport
- Numéro de passeport
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- libreta pasaporte
- número pasaporte
- españa pasaporte
- números de pasaporte
- Número de pasaporte
- números pasaporte
- pasaporte non
- Passeport n °
- n ° passeport
- n ° pasaporte
- pasaporte n °
- Passport Espagne


## <a name="spain-social-security-number-ssn"></a>Numéro de sécurité sociale (SSN) Espagne
Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles du numéro de sécurité sociale de l’UE ou d’un ID équivalent et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

11 à 12 chiffres

### <a name="pattern"></a>Modèle

11-12 chiffres :
- deux chiffres 
- une barre oblique (facultatif) 
- sept à huit chiffres 
- une barre oblique (facultatif) 
- deux chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_spanish_social_security_number trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Spain SSN -->
<Entity id="5df987c0-8eae-4bce-ace7-b316347f3070" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_spanish_social_security_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

Aucune

## <a name="spain-tax-identification-number"></a>Numéro d’identification fiscale Espagne
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

sept ou huit chiffres et une ou deux lettres dans le modèle spécifié
  
### <a name="pattern"></a>Modèle

Personnes physiques espagnoles avec une carte d’identité nationale d’Espagne :
  
- huit chiffres 
- une lettre majuscule (respecte la casse) 
    
Spaniards non résident sans carte d’identité nationale d’Espagne
  
- une lettre majuscule « L » (respecte la casse)
- sept chiffres
- une lettre majuscule (respecte la casse) 
    
Spaniards résident de moins de 14 ans sans carte d’identité nationale (Espagne) :
  
- une lettre majuscule « K » (respecte la casse)
- sept chiffres 
- une lettre majuscule (respecte la casse)
    
Foreigners avec le numéro d’identification d’un étranger
  
- une lettre majuscule qui est « X », « Y » ou « Z » (respecte la casse) 
- sept chiffres
- une lettre majuscule (respecte la casse) 
    
Foreigners sans numéro d’identification étranger
  
- une lettre majuscule qui est « M » (respecte la casse) 
- sept chiffres
- une lettre majuscule (respecte la casse) 
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_spain_eu_tax_file_number` ou `Func_spain_eu_DL_and_NI_number_citizen` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_spain_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_spain_eu_tax_file_number` ou `Func_spain_eu_DL_and_NI_number_citizen` trouve le contenu qui correspond au modèle. 
    
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

- importation
- cifid #
- cifnúmero #
- Número de contribuyente
- Número de Identificación fiscal
- Número de Impuesto Corporativo
- spanishcifid #
- spanishcifid
- spanishcifno #
- spanishcifno
- n ° fichier taxe
- numéro de dossier fiscal
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #


## <a name="sql-server-connection-string"></a>Chaîne de connexion SQL Server

### <a name="format"></a>Format

La chaîne « User ID », « User ID », « UID » ou « UserId » suivi des caractères et des chaînes décrits dans le modèle ci-dessous.

### <a name="pattern"></a>Modèle

- la chaîne « User ID », « User ID », « UID » ou « UserId »
- n’importe quelle combinaison entre 1-200 majuscules ou minuscules, des chiffres, des symboles, des caractères spéciaux ou des espaces
- la chaîne "password" ou "PWD" où "PWD" n’est pas précédé d’une lettre minuscule
- signe égal (=)
- tout caractère qui n’est pas un signe dollar ($), un symbole de pourcentage (%), un symbole supérieur à (>), un symbole (@), un guillemet ("), un point-virgule (;), une accolade ouvrante ([) ou un crochet gauche ({)
- n’importe quelle combinaison de 7-128 caractères qui ne sont pas des points-virgules (;), barre oblique (/) ou guillemets (")
- un point-virgule (;) ou guillemets (")

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- L’expression régulière CEP_Regex_SQLServerConnectionString trouve le contenu qui correspond au modèle.
- Un mot clé depuis CEP_GlobalFilter **est introuvable** .
- L’expression régulière CEP_PasswordPlaceHolder ne trouve **pas** le contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve **pas** le contenu qui correspond au modèle.

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
- échantillonnage

#### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

(Notez que techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- Mot de passe ou mot de passe suivi par 0-2 espaces, un signe égal (=), 0-2 espaces et un astérisque (*)--ou--
- Mot de passe ou mot de passe suivi par :
    - Signe égal (=)
    - Symbole inférieur à (<)
    - Toute combinaison de 1-200 caractères qui sont des lettres majuscules ou minuscules, des chiffres, un astérisque (*), un tiret (-), un trait de soulignement (_) ou un espace blanc
    - Symbole supérieur à (>)

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

(Notez que techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- contoso
- société
- Northwind
- immédiatement
- onebox
- hôte
- bouclage
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->NET

## <a name="sweden-drivers-license-number"></a>Numéro de permis de conduire Suède

### <a name="format"></a>Format

dix chiffres contenant un trait d’Union
  
### <a name="pattern"></a>Modèle

dix chiffres contenant un trait d’Union :
  
- six chiffres 
- un trait d’Union
- quatre chiffres
    
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression régulière  `Regex_sweden_eu_driver's_license_number` trouve le contenu qui correspond au modèle. 
- Un mot clé depuis  `Keywords_eu_driver's_license_number` ou `Keywords_sweden_eu_driver's_license_number` est trouvé. 
    
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
- Gestionnaire de la LIC
- pilote conduire
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
- pilotes Lic
- pilotes conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver'lic
- driver'lics
- driver'license
- driver'licenses
- driver'licence
- driver'licences
- Driver’Lic
- pilote’conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver'slic
- driver'slics
- driver'slicense
- driver'slicenses
- driver'slicence
- driver'slicences
- Gestionnaire de la LIC
- conduire du pilote
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- LD #
- distribution #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- Gestionnaire de la LIC #
- pilote conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- pilotes Lic #
- pilotes conduire #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver'lic #
- driver'lics #
- driver'license #
- driver'licenses #
- driver'licence #
- driver'licences #
- Driver’Lic #
- pilote’conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver'slic #
- driver'slics #
- driver'slicense #
- driver'slicenses #
- driver'slicence #
- driver'slicences #
- Gestionnaire de la LIC #
- conduire du pilote #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire 
- permis de conduire
- dlno #
- permis Lic
- permis conduire
- licence permis
- licences permis
- licence permis
- licences permis
- pilote conduire
- pilotes conduire
- conduire du pilote
- Lic de la commande
- conduite conduire
- licences de conduite
- permis de conduire
- permis de conduire
- permis de conduire
- n ° de DL
- dlno
- Numéro de la LD


#### <a name="keywords_sweden_eu_drivers_license_number"></a>Keywords_sweden_eu_driver’s_license_number

- ajokortti
- permis de conducere
- ajokortin numérique
- kuljettajat lic.
- Driver. lic.
- körkort
- numărul permisului de conducere
-  שאָפער דערלויבעניש נומער
- förare lic.
-  דריווערס דערלויבעניש
- körkortsnummer

## <a name="sweden-national-id"></a>ID national de Suède

### <a name="format"></a>Format

10 ou 12 chiffres et un délimiteur facultatif

### <a name="pattern"></a>Modèle

10 ou 12 chiffres et un délimiteur facultatif :
- deux chiffres (facultatif) 
- Six chiffres au format de date AAMMJJ 
- délimiteur « - » ou « + » (facultatif)
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction `Func_swedish_national_identifier` trouve le contenu qui correspond au modèle.
- Un mot clé from `Keywords_swedish_national_identifier` est trouvé
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction `Func_swedish_national_identifier` trouve le contenu qui correspond au modèle.
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

- n ° ID
- Numéro d’identification
- Réf #
- Numéro d’identification
- numéro d’identification
- identifikationsnumret #
- identifikationsnumret
- identitetshandling
- document d’identité
- n ° d’identité
- Numéro d’identité
- ID-Nummer
- ID personnel
- personnummer #
- personnummer
- skatteidentifikationsnummer
   
## <a name="sweden-passport-number"></a>Numéro de passeport Suède
Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles du numéro de passeport de l’UE et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

huit chiffres

### <a name="pattern"></a>Modèle

huit chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- l’expression régulière Regex_sweden_passport_number trouve le contenu qui correspond au modèle.
- l’une des conditions suivantes est vraie :
    - un mot clé depuis Keyword_passport est trouvé.
    - un mot clé depuis Keyword_sweden_passport est trouvé.

```xml
<!-- Sweden Passport Number -->
<Entity id="ba4e7456-55a9-4d89-9140-c33673553526" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_sweden_passport_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_passport" />
          <Match idRef="Keyword_sweden_passport" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés
   
#### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- exigences en matière de visa 
- Carte d’enregistrement d’une personne étrangère 
- Visas Schengen 
- Visa Schengen 
- Traitement du visa 
- Type de visa 
- Entrée unique 
- Entrée multiple 
- Frais de traitement G3 

#### <a name="keyword_passport"></a>Keyword_passport

- Numéro de passeport 
- N° de passeport 
- # Passeport 
- Tel # 
- PassportID 
- N ° passeport 
- passportnumber 
- パスポート 
- パスポート番号 
- パスポートのNum 
- パスポート＃ 
- Numéro de passeport 
- Passeport n° 
- Passeport numéro 
- # Passeport 
- Passeport # 
- PasseportNon 
- Passeportn ° 

## <a name="sweden-social-security-number-or-equivalent-identification"></a>Numéro de sécurité sociale de la Suède ou identification équivalente
Cette entité de type d’informations sensibles est uniquement disponible dans le type d’information de numéro de sécurité sociale ou d’ID équivalent.

### <a name="format"></a>Format

12 chiffres sans espaces ni délimiteurs
  
### <a name="pattern"></a>Modèle

12 chiffres :
  
- huit chiffres correspondant à la date de naissance (AAAAMMJJ) 
- trois chiffres correspondant à un numéro de série où : 
  - le dernier chiffre du numéro de série indique sexe par l’affectation d’un nombre impair pour le mâle et d’un nombre pair pour femelle.
  - jusqu’à 1990, l’affectation du numéro de série correspond au comté où le porteur du numéro est né ou (en naissance avant 1947) où il a été vivant, en fonction des enregistrements fiscaux, le 1er janvier 1947, avec un code spécial (généralement 9 comme le 7 chiffres) pour immigrants 
- un chiffre de contrôle
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_sweden_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_sweden_eu_ssn_or_equivalent` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_sweden_eu_ssn_or_equivalent` trouve le contenu qui correspond au modèle. 
    
```xml
 <!-- EU SSN or Equivalent Number -->
<Entity id="d24e32a4-c0bb-4ba8-899d-6303b95742d9" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_sweden_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_sweden_eu_ssn_or_equivalent" />
        </Pattern> 
       <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_sweden_eu_ssn_or_equivalent" />
        </Pattern>      
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keywords_sweden_eu_ssn_or_equivalent"></a>Keywords_sweden_eu_ssn_or_equivalent

- Numéro d’identification personnel
- numéro d’identification
- Numéro d’identification personnel
- n ° d’identité
- Numéro d’identification
- Numéro d’identification personnel
- ID personnummer
- ID personligt-Nummer
- ID unikt-Nummer
- personnummer
- identifikationsnumret
- personnummer #
- identifikationsnumret #

## <a name="sweden-tax-identification-number"></a>Numéro d’identification de taxe Suède
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

dix chiffres et un symbole dans le modèle spécifié
  
### <a name="pattern"></a>Modèle

dix chiffres et un symbole :
  
- six chiffres correspondant à la date de naissance (AAMMJJ) 
- un signe plus ou un signe moins
- trois chiffres qui permettent de définir le numéro d’identification unique : 
  - pour les numéros émis avant le 1990, le septième et le huitième chiffre identifient le comté de naissance ou les personnes nées à l’étranger.
  - le chiffre de la neuvième position indique le sexe soit impair, soit pair pour femme.
- un chiffre de contrôle
    
### <a name="checksum"></a>Somme de contrôle

Oui
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction  `Func_sweden_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_sweden_eu_tax_file_number` est trouvé. 
    
Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_sweden_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
    
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

- Numéro d’identification personnel
- personnummer
- skatt ID Nummer
- skatt identifikation
- skattebetalarens identifikationsnummer
- Sverige étain
- fichier taxe
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro de taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #


## <a name="swift-code"></a>Code SWIFT

### <a name="format"></a>Format

quatre lettres suivies de 5-31 lettres ou chiffres

### <a name="pattern"></a>Modèle

quatre lettres suivies de 5-31 lettres ou chiffres :
- Code de la Banque à quatre lettres (ne respectant pas la casse) 
- un espace facultatif 
- 4 à 28 lettres ou chiffres (numéro de compte bancaire de base (BBAN)) 
- un espace facultatif 
- une à trois lettres ou chiffres (reste de la BBAN)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- rapide #
- swiftcode
- swiftnumber
- swiftroutingnumber
- code swift
- # numéro swift
- numéro d’acheminement swift
- numéro BIC
- code BIC
- # bic
- BIC #
- code d’identification bancaire
- Organisation internationale de normalisation 9362
- rapide #
- code SWIFT
- le numéro de swift
- swift numéro d’acheminement
- le numéro BIC
- # <a name="bic"></a>BIC
- code identificateur de banque
- SWIFTコード
- SWIFT番号
- BIC番号
- BICコード
- コード SWIFT
- 番号 SWIFT
- BIC 番号
- BIC コード
- 金融機関識別コード
- 金融機関コード
- 銀行コード

## <a name="switzerland-ssn-ahv-number"></a>Suisse numéro AVS AVS
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

numéro à 13 chiffres

### <a name="pattern"></a>Modèle

numéro à 13 chiffres :

- trois chiffres-756
- point facultatif
- quatre chiffres
- point facultatif
- quatre chiffres
- point facultatif
- deux chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_swiss_social_security_number_ahv trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keywords_swiss_social_security_number_ahv est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_swiss_social_security_number_ahv trouve le contenu qui correspond au modèle.

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

- obligation
- SSN
- pid
- Numéro d’assurance
- personalidno #
- numéro de sécurité sociale
- Numéro d’identification personnel
- n ° d’identification personnelle
- insuranceno #
- uniqueidno #
- n ° d’identification unique
- numéro AVS
- identité personnelle aucune versicherungsnummer
- identifikationsnummer
- einzigartige identität nicht
- sozialversicherungsnummer
- ID personnelle d’identification
- numéro de sécurité sociale

   
## <a name="taiwan-national-identification-number"></a>Numéro d’identification national taïwanais

### <a name="format"></a>Format

une lettre suivie de neuf chiffres

### <a name="pattern"></a>Modèle

une lettre suivie de neuf chiffres :
- une lettre (en anglais, ne respectant pas la casse) 
- le chiffre « 1 » ou « 2 » 
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_taiwanese_national_id trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_taiwanese_national_id est trouvé.
- La somme de contrôle est correcte.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
   
## <a name="taiwan-passport-number"></a>Numéro de passeport taïwanais

### <a name="format"></a>Format

- Numéro de passeport biométrique : neuf chiffres
- Numéro de passeport non biométrique : neuf chiffres

### <a name="pattern"></a>Modèle
Numéro de passeport biométrique :
- le caractère « 3 » 
- huit chiffres

Numéro de passeport non biométrique :
- neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
   
## <a name="taiwan-resident-certificate-arctarc-number"></a>Numéro de certificat résident taïwanais (ARC/TARC)

### <a name="format"></a>Format

10 lettres et chiffres

### <a name="pattern"></a>Modèle

10 lettres et chiffres :
- deux lettres (ne respectant pas la casse) 
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

## <a name="thai-population-identification-code"></a>Code d’identification du remplissage thaï

### <a name="format"></a>Format

13 chiffres

### <a name="pattern"></a>Modèle

13 chiffres :
- le premier chiffre est différent de zéro ou neuf 
- 12 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_Thai_Citizen_Id trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keyword_Thai_Citizen_Id est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_Thai_Citizen_Id trouve le contenu qui correspond au modèle.

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

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_Turkish_National_Id trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keyword_Turkish_National_Id est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_Turkish_National_Id trouve le contenu qui correspond au modèle.

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

- TC Kimlik non
- TC Kimlik numarası
- Vatandaşlık numarası
- Vatandaşlık non

## <a name="uk-drivers-license-number"></a>impérial Numéro de permis de conduire
Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles du pilote de l’UE et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

Combinaison de 18 lettres et chiffres au format spécifié

### <a name="pattern"></a>Modèle

18 lettres et chiffres
- cinq lettres (ne respectant pas la casse) ou le chiffre « 9 » à la place d’une lettre 
- un chiffre 
- cinq chiffres au format de date MMDDY pour la date de naissance (7 caractères sont incrémentés de 50 si le pilote est femelle, c’est-à-dire 51 vers 62 au lieu de 01 à 12)
- deux lettres (ne respectant pas la casse) ou le chiffre « 9 » à la place d’une lettre 
- cinq chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_uk_drivers_license trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_uk_drivers_license est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- U.K. Driver's License Number -->
<Entity id="f93de4be-d94c-40df-a8be-461738047551" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_uk_drivers_license" />
        <Match idRef="Keyword_uk_drivers_license" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_uk_drivers_license"></a>Keyword_uk_drivers_license

- DVLA 
- véhicule utilitaire léger 
- quadbikes 
- automobiles 
- 125cc 
- annexes 
- tricycles 
- Side 
- permis de conduire plastifié 
- apprentis conducteurs 
- titulaire du permis 
- titulaires du permis 
- permis de conduire 
- permis de conduire 
- voiture à double commande 
   
## <a name="uk-electoral-roll-number"></a>impérial Numéro de la déroulation électorale

### <a name="format"></a>Format

deux lettres suivies de 1-4 chiffres

### <a name="pattern"></a>Modèle

deux lettres (ne respectant pas la casse) suivies de numéros 1-4

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

   
## <a name="uk-national-health-service-number"></a>impérial Numéro de service de santé national

### <a name="format"></a>Format

10 à 17 chiffres séparés par des espaces

### <a name="pattern"></a>Modèle

10 à 17 chiffres :
- trois ou dix chiffres 
- un espace 
- trois chiffres 
- un espace 
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
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
- NHS 
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
- D. O. B 
- Date of Birth 
- Birth Date 
   
## <a name="uk-national-insurance-number-nino"></a>impérial Numéro d’assurance nationale (NINO)
Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles du numéro identificaiton national UE et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

sept caractères ou neuf caractères séparés par des espaces ou des tirets

### <a name="pattern"></a>Modèle

deux modèles possibles :

- deux lettres (valides NINOs Utilisez uniquement certains caractères dans ce préfixe, que ce modèle valide ; ne respecte pas la casse)
- six chiffres
- « A », « B », « C » ou « d » (comme le préfixe, seuls certains caractères sont autorisés dans le suffixe ; ne respectent pas la casse)

OR

- deux lettres
- un espace ou un tiret
- deux chiffres
- un espace ou un tiret
- deux chiffres
- un espace ou un tiret
- deux chiffres
- un espace ou un tiret
- « A », « B », « C » ou « d »

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_uk_nino trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_uk_nino est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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
- cotisations
- numéro de sécurité sociale
- demande d’assurance
- demande de soins médicaux
- assurance sociale
- soins médicaux
- sécurité sociale
- grande-bretagne
- Nombre NI
- NI n °.
- ALLIAGE #
- ALLIAGE #
- cotisations #
- insurancenumber
- nationalinsurance #
- nationalinsurancenumber

    
## <a name="uk-unique-taxpayer-reference-number"></a>impérial Numéro de référence unique du contribuable
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

10 chiffres sans espaces ni délimiteurs
 
  
### <a name="pattern"></a>Modèle

10 chiffres
  
### <a name="checksum"></a>Somme de contrôle

Non
  
### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction  `Func_uk_eu_tax_file_number` trouve le contenu qui correspond au modèle. 
- Un mot clé from  `Keywords_uk_eu_tax_file_number` est trouvé. 
    
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

- Numéro de taxe
- fichier taxe
- id fiscal
- n ° d’identification fiscale
- Numéro d’identification de taxe
- n ° taxe #
- n ° taxe
- Numéro d’enregistrement taxe
- taxi #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- ID d’étain
- n ° d’étain
- Etain #

## <a name="us-bank-account-number"></a>Numéro de compte bancaire américain

### <a name="format"></a>Format

6-17 chiffres

### <a name="pattern"></a>Modèle

6-17 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
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

dépend de l’État (par exemple, New York) :
- neuf chiffres au format DDD DDD DDD correspondront.
- neuf chiffres comme ddddddddd ne correspondent pas.

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_new_york_drivers_license_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_[state_name]_drivers_license_name est trouvé.
- Un mot clé figurant dans la liste Keyword_us_drivers_license est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
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

- LD 
- DISTRIBUTION 
- CÈDE 
- CDLS 
- ID 
- Codes 
- LD # 
- DISTRIBUTION # 
- CÈDE # 
- CDLS # 
- Réf #
- Codes # 
- Numéro d’identification 
- Numéros d’identification 
- Profil 
- Profil # 

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
- Driver'Lic 
- Driver'Lics 
- Driver'License 
- Driver'Licenses 
- Permis conduire 
- Permis conduire 
- Permis de conduire 
- Permis de conduire
- Driver'sLic 
- Driver'sLics 
- Driver'sLicense 
- Driver'sLicenses 
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
- Driver'Lic # 
- Driver'Lics # 
- Driver'License # 
- Driver'Licenses # 
- #Permis conduire 
- #Permis conduire 
- #Permis de conduire 
- #Permis de conduire 
- Driver'sLic # 
- Driver'sLics # 
- Driver'sLicense # 
- Driver'sLicenses # 
- #Permisconduire 
- #Permisconduire 
- #Permis de conduire 
- #Permis de conduire 
- # carte d’identité 
- # cartes d’identité 
- #carte d’identification 
- #cartes d’identification 


#### <a name="keyword_state_name_drivers_license_name"></a>Keyword_ [state_name] _drivers_license_name

- abréviation de l’État (par exemple, « NY ») 
- nom de l’État (par exemple, « New York »)

## <a name="us-individual-taxpayer-identification-number-itin"></a>Numéro d’identification du contribuable américain (ITIN)

### <a name="format"></a>Format

neuf chiffres commençant par le « 9 » et contenant un « 7 » ou un « 8 » en tant que quatrième chiffre, éventuellement mis en forme avec des espaces ou des tirets

### <a name="pattern"></a>Modèle

avec
- le chiffre « 9 » 
- deux chiffres 
- un espace ou un tiret 
- « 7 » ou « 8 » 
- un chiffre 
- un espace ou un tiret 
- quatre chiffres

non
- le chiffre « 9 » 
- deux chiffres 
- « 7 » ou « 8 » 
- cinq chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_formatted_itin trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_itin est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_unformatted_itin trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_itin est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- La fonction Func_formatted_itin ou Func_unformatted_itin trouve le contenu qui correspond au modèle.

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

- redevable 
- id fiscal 
- identification fiscale 
- itin 
- i.t.i.n.
- SSN 
- Etain 
- sécurité sociale 
- contribuable 
- itins 
- taxi 
- contribuable individuel 


## <a name="us-social-security-number-ssn"></a>Numéro de sécurité sociale américain (SSN)

### <a name="format"></a>Format

neuf chiffres, qui peuvent être mis en forme ou non mis en forme

> [!NOTE]
> La mise en forme d’un numéro de sécurité sociale émis avant le milieu de l’année 2011 est fixe et certaines parties du numéro doivent se situer dans certaines plages pour qu’il soit valide (mais il n’y a pas de somme de contrôle).

### <a name="pattern"></a>Modèle

quatre fonctions recherchent numéros dans quatre modèles différents :
- Func_ssn recherche des numéros de sécurité sociale avec une mise en forme fixe d’avant l’année 2011, mis en forme avec des tirets ou des espaces (ddd-dd-dddd OU ddd dd dddd)
- Func_unformatted_ssn recherche des numéros de sécurité sociale avec une mise en forme fixe d’avant l’année 2011, avec neuf chiffres consécutifs non mis en forme (ddddddddd)
- Func_randomized_formatted_ssn recherche des numéros de sécurité sociale d’après l’année 2011, mis en forme avec des tirets ou des espaces  (ddd-dd-dddd OU ddd dd dddd)
- Func_randomized_unformatted_ssn recherche des numéros de sécurité sociale d’après l’année 2011, avec neuf chiffres consécutifs non mis en forme (ddddddddd)

### <a name="checksum"></a>Somme de contrôle

Non


### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 85 % si, dans une proximité de 300 caractères :
- La fonction Func_ssn trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ssn est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_unformatted_ssn trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ssn est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 65 % si, dans une proximité de 300 caractères :
- La fonction Func_randomized_formatted_ssn trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ssn est trouvé.

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 55 % si, dans une proximité de 300 caractères :
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
- Numéro de sécurité sociale
- # sécurité sociale
- Sécu sociale
- SSN
- NUMÉROS
- SSN #
- SOCIALE #
- Identifiant SSID
   
## <a name="us--uk-passport-number"></a>ANGLAIS (ÉTATS-UNIS) numéro de passeport
Le Royaume-Uni Numéro de passeport le type d’informations sensibles l’entité est disponible dans le type d’informations sensibles du numéro de passeport de l’euro et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- La fonction Func_usa_uk_passport trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_passport est trouvé.

```xml
<Entity id="178ec42a-18b4-47cc-85c7-d62c92fd67f8" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_usa_uk_passport" />
        <Match idRef="Keyword_passport" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots clés

#### <a name="keyword_passport"></a>Keyword_passport

- Numéro de passeport 
- N° de passeport 
- # Passeport 
- Tel # 
- PassportID 
- N ° passeport 
- passportnumber 
- パスポート 
- パスポート番号 
- パスポートのNum 
- パスポート＃ 
- Numéro de passeport 
- Passeport n° 
- Passeport numéro 
- # Passeport 
- Passeport # 
- PasseportNon 
- Passeportn ° 

## <a name="ukraine-passport-domestic"></a>Pays de l’Ukraine passeport national
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression Regex Regex_Ukraine_Passport_Domestic trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keyword_Ukraine_Passport_Domestic est trouvé.

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

- passeport de l’Ukraine
- numéro de passeport
- Numéro de passeport
- паспорт України
- номер паспорта
- персональний


## <a name="ukraine-passport-international"></a>International de l’Ukraine Passport
Ce type d’informations sensibles est disponible uniquement dans les cas suivants :
- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gouvernance des informations
- gestion des enregistrements
- Sécurité des applications Cloud Microsoft

### <a name="format"></a>Format

modèle alphanumérique à huit caractères

### <a name="pattern"></a>Modèle

modèle alphanumérique à huit caractères :
- deux lettres ou chiffres
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Le pourcentage de confiance d’une stratégie DLP ayant détecté ce type d’informations sensibles est de 75 % si, dans une proximité de 300 caractères :
- L’expression Regex Regex_Ukraine_Passport_International trouve le contenu qui correspond au modèle.
- Un mot clé depuis Keyword_Ukraine_Passport_International est trouvé.

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

- passeport de l’Ukraine
- numéro de passeport
- Numéro de passeport
- паспорт України
- номер паспорта
