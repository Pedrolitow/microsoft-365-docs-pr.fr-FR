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
description: De nombreux types d’informations sensibles sont prêts à être utilisés dans vos stratégies DLP. Cet article répertorie tous ces types d’informations sensibles et montre ce qu’une stratégie DLP recherche lorsqu’elle détecte chaque type.
ms.openlocfilehash: 2d81410b86ca9a90b12dbaa850e36d8803af0d79
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622422"
---
# <a name="sensitive-information-type-entity-definitions"></a>Définitions d’entités des types d’informations sensibles

Cet article répertorie toutes les définitions d’entité de type d’informations sensibles. Chaque définition montre ce qu’une stratégie DLP recherche pour détecter chaque type. Pour en savoir plus sur les types d’informations sensibles, consultez [Types d’informations sensibles](sensitive-information-type-learn-about.md)

> [!NOTE]
> Mappage du niveau de confiance (élevé/moyen/faible) avec le numéro de précision (valeur numérique de 1 à 100)
>
> - Confiance faible : 65 ou moins
> - Confiance moyenne : 75
> - Confiance élevée : 85

## <a name="aba-routing-number"></a>Numéro de routage ABA

### <a name="format"></a>Format

neuf chiffres qui peuvent être dans un modèle mis en forme ou non mis en forme

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

Une stratégie a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_aba_routing trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ABA_Routing est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_aba_routing"></a>Keyword_aba_routing

- numéro aba
- Aba #
- Aba
- abarouting #
- abaroutingnumber
- americanbankassociationrouting #
- americanbankassociationroutingnumber
- bankrouting #
- bankroutingnumber
- Routage #
- routage non
- numéro de routage
- numéro de routage
- Routage #
- RTN

## <a name="all-full-names"></a>Tous les noms complets

Tous les noms complets sont une entité nommée groupée. Il détecte les noms complets des personnes de tous les pays/régions pris en charge, notamment l’Australie, la Chine, le Japon, les États-Unis et les pays de l’UE. Utilisez ce SIT pour détecter toutes les correspondances possibles de noms complets.

### <a name="format"></a>Format

Divers.

### <a name="pattern"></a>Modèle

Divers.

### <a name="checksum"></a>Somme de contrôle

Non.

### <a name="description"></a>Description

Cette entité nommée SIT correspond à des noms personnels qu’un humain identifierait en tant que nom avec une confiance élevée. Par exemple, si une chaîne est trouvée composée d’un nom donné et est suivie d’un nom de famille, une correspondance est effectuée avec une confiance élevée. Il utilise trois ressources principales :

- Dictionnaire de noms donnés.
- Dictionnaire de noms de famille.
- Modèles de la façon dont les noms sont formés.

Les trois ressources sont différentes pour chaque pays.  Les chaînes *Olivia Wilson* déclencherait une correspondance. Les noms donnés/de famille courants bénéficient d’une plus grande confiance que les noms plus rares. Toutefois, le modèle autorise également les correspondances partielles. Si un nom donné du dictionnaire est trouvé et qu’il est suivi d’un nom de famille qui n’est pas dans le dictionnaire, une correspondance partielle est déclenchée. Par exemple, *Tomas Richard* déclencherait un match partiel. La confiance des correspondances partielles est moindre.

En outre, les modèles qu’un humain considérerait comme indicatifs de noms sont également mis en correspondance avec la confiance appropriée. Comme *O. Wilson*, *O.P. Wilson*, *Dr. O. P. Wilson*, *Wilson, O.P.* ou *T. Richard, Jr.* serait des correspondances.

### <a name="supported-languages"></a>Langues prises en charge

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

## <a name="all-medical-terms-and-conditions"></a>Toutes les conditions générales médicales

Tous les termes et conditions médicales sont une entité nommée groupée qui détecte les conditions médicales et les conditions médicales. Il détecte uniquement les termes anglais. Utilisez ce SIT pour détecter toutes les correspondances possibles de conditions médicales.

### <a name="format"></a>Format

Dictionary

### <a name="pattern"></a>Modèle

Dictionary

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="description"></a>Description

Cette entité nommée groupée correspond au texte qui mentionne les conditions médicales présentes dans les dictionnaires organisés. Il existe un dictionnaire organisé par langue prise en charge. Les dictionnaires proviennent de nombreuses ressources médicales internationales. Les dictionnaires incluent autant de conditions médicales que possible sans risquer un grand nombre de faux positifs. Chaque entrée contient les différentes formes dans lesquelles une condition unique est couramment écrite pour garantir la couverture, par exemple :

- *TB*
- *Tuberculose*
- *phthisis pulmonalis*

### <a name="contains"></a>Contains

Cette entité nommée groupée SIT contient ces SIT individuels.

- Termes de l’analyse de sang
- Types de médicaments
- Maladies
- Noms de médicaments génériques
- Déficiences répertoriées dans l’évaluation des incapacités aux États-Unis sous sécurité sociale
- Termes du test lab
- Modes de vie liés aux conditions médicales
- Spécialités médicales
- Interventions chirurgicales
- Noms des médicaments de marque

## <a name="all-physical-addresses"></a>Toutes les adresses physiques

Toutes les adresses physiques sont une entité groupée SIT, qui détecte les modèles liés aux adresses physiques de tous les pays/régions pris en charge.

### <a name="format"></a>Format

Divers

### <a name="pattern"></a>Modèle

Divers

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="description"></a>Description

La correspondance des adresses de rue est conçue pour correspondre à des chaînes qu’un humain identifierait comme adresse de rue. Pour ce faire, il utilise plusieurs ressources principales :

- Dictionnaire d’établissements, de comtés et de régions.
- Dictionnaire de suffixes de rue, comme Road, Street ou Avenue.
- Modèles de codes postaux.
- Modèles de formats d’adresse.

Les ressources sont différentes pour chaque pays. Les ressources principales sont les modèles de formats d’adresse utilisés dans un pays donné. Différents formats sont choisis pour s’assurer que autant d’adresses que possible sont mises en correspondance. Ces formats permettent la flexibilité, par exemple, une adresse peut omettre le code postal ou omettre un nom de ville ou avoir une rue sans suffixe de rue. Dans tous les cas, ces correspondances sont utilisées pour augmenter la confiance de la correspondance.

Les modèles sont conçus pour correspondre à des adresses uniques individuelles, et non à des emplacements génériques. Ainsi, les chaînes telles que *Redmond, WA 98052* ou *Main Street, Albuquerque* ne seront pas mises en correspondance.

### <a name="contains"></a>Contains

Cette entité nommée groupée SIT contient les SIT individuels suivants :

- Adresses physiques de l’Australie
- Adresses physiques en Autriche
- Adresses physiques belges
- Adresses physiques du Brésil
- Adresses physiques bulgares
- Adresses physiques du Canada
- Adresses physiques croates
- Adresses physiques de Chypre
- Adresses physiques de la République tchèque
- Adresses physiques du Danemark
- Adresses physiques estoniennes
- Adresses physiques finlandaises
- Adresses physiques en France
- Adresses physiques allemandes
- Adresses physiques en Grèce
- Adresses physiques en Hongrie
- Adresses physiques islandaises
- Adresses physiques d’Irlande
- Adresses physiques en Italie
- Adresses physiques lettones
- Adresses physiques du Liechtenstein
- Adresses physiques lituaniennes
- Adresses physiques luxembourgeoises
- Adresses physiques de Malte
- Adresses physiques des Pays-Bas
- Adresses physiques néo-zélandaises
- Adresses physiques en Norvège
- Adresses physiques en Pologne
- Adresses physiques du Portugal
- Adresses physiques roumaines
- Adresses physiques en Slovaquie
- Adresses physiques slovènes
- Adresses physiques en Espagne
- Adresses physiques en Suède
- Adresses physiques en Suisse
- Adresses physiques de la Turquie
- Adresses physiques du Royaume-Uni
- États-Unis adresses physiques

### <a name="supported-languages"></a>Langues prises en charge

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

## <a name="argentina-national-identity-dni-number"></a>Numéro d’identité nationale argentine (DNI)

### <a name="format"></a>Format

Huit chiffres avec ou sans périodes

### <a name="pattern"></a>Modèle

Huit chiffres :

- deux chiffres
- une période facultative
- trois chiffres
- une période facultative
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Argentina National Identity number
- cedula
- cédula
- Dni
- documento nacional de identidad
- documento número
- documento numero
- registro nacional de las personas
- Rnp

## <a name="argentina-unique-tax-identification-key-cuitcuil"></a>Clé d’identification fiscale unique argentine (CUIT/CUIL)

### <a name="format"></a>Format

11 chiffres avec tiret

### <a name="pattern"></a>Modèle

11 chiffres avec un tiret :

- deux chiffres dans 20, 23, 24, 27, 30, 33 ou 34
- un trait d’union (-)
- huit chiffres
- un trait d’union (-)
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_Argentina_Unique_Tax_Key` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_Argentina_Unique_Tax_Key` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_Argentina_Unique_Tax_Key` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_argentina_unique_tax_key"></a>Keyword_Argentina_Unique_Tax_Key

- Clave Unica de Identificacion Tributaria
- CUIT
- code unique d’identification du travail
- Clave Única de Identificación Tributaria
- code unique d’identification du travail
- CUIL
- Clé d’identification fiscale unique
- Clé unique d’identification du travail
- Clé unique de l’identification du travail
- Code d’identification de travail unique
- Code unique d’identification du travail
- Clé d’identification de travail unique
- Clé unique d’identification du travail
- Code unique d’identification fiscale
- Clé unique d’identification fiscale
- Code d’identification du travail unique
- Code unique d’identification du travail
- Clé d’identification du travail unique
- Clé unique de l’identification du travail
- ID d’impôt
- taxID #
- taxId
- taxidnumber
- numéro d’impôt
- tax no
- Taxe #
- Taxe #
- ID du contribuable
- numéro de contribuable
- contribuable non
- Contribuable #
- Contribuable #
- identité fiscale
- identification fiscale
- Número de Identificación Fiscal
- número de contribuyente

## <a name="australia-bank-account-number"></a>Numéro de compte bancaire en Australie

### <a name="format"></a>Format

6 à 10 chiffres avec ou sans numéro de succursale bancaire

### <a name="pattern"></a>Modèle

Le numéro de compte est compris entre 6 et 10 chiffres.

Numéro de succursale bancaire en Australie :

- trois chiffres
- un trait d’union
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Regex_australia_bank_account_number recherche du contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_australia_bank_account_number est trouvé.
- L’expression régulière Regex_australia_bank_account_number_bsb trouve un contenu qui correspond au modèle.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Regex_australia_bank_account_number recherche du contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

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
- Aiea

## <a name="australia-business-number"></a>Numéro d’entreprise en Australie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

11 chiffres avec délimiteurs facultatifs

### <a name="pattern"></a>Modèle

11 chiffres avec délimiteurs facultatifs :

- deux chiffres
- un trait d’union ou un espace facultatif
- trois chiffres
- un trait d’union ou un espace facultatif
- trois chiffres
- un trait d’union ou un espace facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_australian_business_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_australian_business_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_australian_business_number recherche le contenu qui correspond au modèle.

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
### <a name="keywords"></a>Mots-clés

#### <a name="keyword_australia_business_number"></a>Keyword_australia_business_number

- australie business no
- numéro d’entreprise
- Abn #
- Businessid #
- ID d’entreprise
- Abn
- businessno #

## <a name="australia-company-number"></a>Numéro d’entreprise en Australie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

neuf chiffres avec délimiteurs

### <a name="pattern"></a>Modèle

neuf chiffres avec délimiteurs :

- trois chiffres
- un espace
- trois chiffres
- un espace
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_Australian_Company_Number recherche le contenu qui correspond au modèle.
- Un mot clé de Keyword_Australian_Company_Number est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_Australian_Company_Number recherche le contenu qui correspond au modèle.

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
### <a name="keywords"></a>Mots-clés

#### <a name="keyword_australia_company_number"></a>Keyword_australia_company_number

- Anc
- australia company no
- australia company no #
- numéro d’entreprise australie
- australian company no
- australian company no #
- numéro d’entreprise australien

## <a name="australia-drivers-license-number"></a>Numéro de permis de conduire en Australie

### <a name="format"></a>Format

neuf lettres et chiffres

### <a name="pattern"></a>Modèle

neuf lettres et chiffres :

- deux chiffres ou lettres (non sensibles à la casse)
- deux chiffres
- cinq chiffres ou lettres (non sensibles à la casse)

OR

- une à deux lettres facultatives (non sensibles à la casse)
- quatre à neuf chiffres

OR

- neuf chiffres ou lettres (non sensibles à la casse)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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

- Aaa
- DriverLicense
- DriverLicenses
- Permis de conduire
- Permis de conduire
- DriversLicense
- DriversLicenses
- Permis de conduire
- Permis de conduire
- Driver’License
- Licences de pilote
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
- Driver’License #
- Licences de pilote #
- #Permis de conduire
- #Permis de conduire
- Driver’sLicense #
- Driver’sLicenses #
- #Permis de conduire
- #Permis de conduire

## <a name="australia-medical-account-number"></a>Numéro de compte médical en Australie

### <a name="format"></a>Format

10 à 11 chiffres

### <a name="pattern"></a>Modèle

10 à 11 chiffres :

- Le premier chiffre est compris entre 2 et 6
- Le neuvième chiffre est un chiffre de contrôle
- Le dixième chiffre est le chiffre d’émission
- 11e chiffre (facultatif) est le nombre individuel

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_australia_medical_account_number"></a>Keyword_Australia_Medical_Account_Number

- informations sur le compte bancaire
- remboursements d’assurance maladie
- compte de prêts immobiliers
- paiements bancaires
- direction de l’information
- prêt sur carte de crédit
- département des services sociaux
- service local
- Medicare

## <a name="australia-passport-number"></a>Numéro de passeport en Australie

### <a name="format"></a>Format

huit ou neuf caractères alphanumériques

### <a name="pattern"></a>Modèle

- une lettre (N, E, D, F, A, C, U, X) suivie de sept chiffres ou
- Deux lettres (PA, PB, PC, PD, PE, PF, PU, PW, PX, PZ) suivies de sept chiffres.

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_australia_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_australia_passport_number` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_australia_passport_number` régulière recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
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

## <a name="australia-physical-addresses"></a>Adresses physiques de l’Australie

Entité nommée non groupée, détecte les modèles liés à l’adresse physique de l’Australie. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance
medium

## <a name="australia-tax-file-number"></a>Numéro de fichier fiscal en Australie

### <a name="format"></a>Format

huit à neuf chiffres

### <a name="pattern"></a>Modèle

Huit à neuf chiffres sont généralement présentés avec des espaces comme suit :

- trois chiffres
- un espace facultatif
- trois chiffres
- un espace facultatif
- deux à trois chiffres où le dernier chiffre est un chiffre à cocher

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_australia_tax_file_number"></a>Keyword_australia_tax_file_number

- numéro d’entreprise australien
- taux d’imposition marginale
- prélèvement d’assurance maladie
- numéro de portefeuille
- service des vétérans
- retenue à la source
- déclaration d’impôts individuels
- numéro de dossier fiscal
- Tfn

## <a name="austria-drivers-license-number"></a>Numéro de permis de conduire en Autriche

### <a name="format"></a>Format

huit chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_austria_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_austria_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_austria_eu_drivers_license_number"></a>Keywords_austria_eu_driver s_license_number

- fuhrerschein
- führerschein
- Führerscheine
- Führerscheinnummer
- Führerscheinnummern

## <a name="austria-identity-card"></a>Carte d’identité en Autriche

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Combinaison de 24 caractères de lettres, de chiffres et de caractères spéciaux

### <a name="pattern"></a>Modèle

24 caractères :

- 22 lettres (non sensibles à la casse), chiffres, barres obliques, barres obliques ou signes plus

- deux lettres (non sensibles à la casse), chiffres, barres obliques inverses, barres obliques, signes plus ou signes égaux

### <a name="checksum"></a>Somme de contrôle

Non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_austria_eu_national_id_card` régulière recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_austria_eu_national_id_card` trouvé.

```xml
      <!-- Austria Identity Card -->
      <Entity id="5ec06c3b-007e-4820-8343-7ff73b889735" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_national_id_card" />
          <Match idRef="Keywords_austria_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_austria_eu_national_id_card"></a>Keywords_austria_eu_national_id_card

- numéro d’identité
- id national
- personalausweis republik österreich

## <a name="austria-passport-number"></a>Numéro de passeport en Autriche

### <a name="format"></a>Format

Une lettre suivie d’un espace facultatif et de sept chiffres

### <a name="pattern"></a>Modèle

Combinaison d’une lettre, de sept chiffres et d’un espace :

- une lettre (non sensible à la casse)
- un espace (facultatif)
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_austria_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_austria_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_austria_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_austria_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
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

- date du problème
- date d’expiration

## <a name="austria-physical-addresses"></a>Adresses physiques en Autriche

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique en provenance d’Autriche. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="austria-social-security-number"></a>Numéro de sécurité sociale en Autriche

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_austria_eu_ssn_or_equivalent` recherche le contenu qui correspond au modèle.
- un mot clé à partir de `Keywords_austria_eu_ssn_or_equivalent` est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_austria_eu_ssn_or_equivalent` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_austria_eu_ssn_or_equivalent"></a>Keywords_austria_eu_ssn_or_equivalent

- ssn autrichien
- nombre ehic
- ehic no
- code d’assurance
- insurancecode #
- numéro d’assurance
- assurance no
- krankenkassennummer
- Krankenversicherung
- socialsecurityno
- socialsecurityno #
- sécurité sociale non
- numéro de sécurité sociale
- code de sécurité sociale
- sozialversicherungsnummer
- sozialversicherungsnummer #
- soziale sicherheit kein
- sozialesicherheitkein #
- Ssn #
- Ssn
- versicherungscode
- versicherungsnummer
- zdravstveno zavarovanje

## <a name="austria-tax-identification-number"></a>Numéro d’identification fiscale en Autriche

### <a name="format"></a>Format

neuf chiffres avec trait d’union facultatif et barre oblique

### <a name="pattern"></a>Modèle

neuf chiffres avec trait d’union facultatif et barre oblique :

- deux chiffres
- un trait d’union (facultatif)
- trois chiffres
- une barre oblique (facultatif)
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_austria_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_austria_eu_tax_file_number` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_austria_eu_tax_file_number` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_austria_eu_tax_file_number"></a>Keywords_austria_eu_tax_file_number

- Österreich
- st.nr.
- steuernummer
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #
- numéro d’impôt

## <a name="austria-value-added-tax"></a>Taxe sur la valeur ajoutée en Autriche

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Modèle alphanumérique à 11 caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique à 11 caractères :

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_Austria_Value_Added_Tax recherche le contenu qui correspond au modèle.
- Un mot clé de Keyword_Austria_Value_Added_Tax est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_Austria_Value_Added_Tax recherche le contenu qui correspond au modèle.

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
### <a name="keywords"></a>Mots-clés

#### <a name="keyword_austria_value_added_tax"></a>Keyword_austria_value_added_tax

- numéro de tva
- Tva #
- numéro de tva autrichien
- vat no.
- vatno #
- numéro de taxe sur la valeur ajoutée
- tva autrichienne
- mwst
- umsatzsteuernummer
- mwstnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- numéro d’identification de tva
- atu number
- uid number

## <a name="azure-documentdb-auth-key"></a>Clé d’authentification Azure DocumentDB

### <a name="format"></a>Format

Chaîne « DocumentDb » suivie des caractères et des chaînes décrits dans le modèle ci-dessous.

### <a name="pattern"></a>Modèle

- Chaîne « DocumentDb »
- Toute combinaison comprise entre 3 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- Symbole supérieur (>), signe égal (=), guillemet (« ) ou apostrophe (')
- Toute combinaison de 86 lettres minuscules ou majuscules, chiffres, barre oblique (/) ou signe plus (+)
- Deux signes égaux (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière CEP_Regex_AzureDocumentDBAuthKey recherche du contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve pas de contenu correspondant au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>Chaîne de connexion de base de données Azure IAAS et chaîne de connexion Azure SQL

### <a name="format"></a>Format

Chaîne « Serveur », « serveur » ou « source de données », suivie des caractères et des chaînes décrits dans le modèle ci-dessous, y compris la chaîne « cloudapp.azure ».<!--no-hyperlink-->com » ou « cloudapp.azure.<!--no-hyperlink-->net » ou « database.windows.<!--no-hyperlink-->net » et la chaîne « Password » ou « password » ou « pwd ».

### <a name="pattern"></a>Modèle

- la chaîne « Server », « server » ou « data source »
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison d’entre 1 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- Chaîne « cloudapp.azure.<!--no-hyperlink-->com », « cloudapp.azure.<!--no-hyperlink-->net », ou « database.windows.<!--no-hyperlink-->net »
- toute combinaison d’entre 1 et 300 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- la chaîne « Password », « password » ou « pwd »
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- un ou plusieurs caractères qui ne sont pas un point-virgule (;), guillemets (« ) ou apostrophe (')
- un point-virgule (;), guillemet (« ), ou apostrophe (')

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière CEP_Regex_AzureConnectionString recherche du contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve pas de contenu correspondant au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-iot-connection-string"></a>Chaîne de connexion Azure IoT

### <a name="format"></a>Format

Chaîne « HostName » suivie des caractères et des chaînes décrits dans le modèle ci-dessous, y compris les chaînes « azure-devices ».<!--no-hyperlink-->net » et « SharedAccessKey ».

### <a name="pattern"></a>Modèle

- chaîne « HostName »
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison d’entre 1 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- chaîne « azure-devices.<!--no-hyperlink-->net »
- toute combinaison d’entre 1 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- chaîne « SharedAccessKey »
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison de 43 lettres minuscules ou majuscules, chiffres, barre oblique (/) ou signe plus (+)
- un signe égal (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière CEP_Regex_AzureIoTConnectionString recherche du contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve pas de contenu correspondant au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-publish-setting-password"></a>Mot de passe du paramètre de publication Azure

### <a name="format"></a>Format

Chaîne « userpwd= » suivie d’une chaîne alphanumérique.

### <a name="pattern"></a>Modèle

- la chaîne " userpwd= »
- toute combinaison de 60 lettres minuscules ou chiffres
- un guillemet (« )

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière CEP_Regex_AzurePublishSettingPasswords recherche du contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve pas de contenu correspondant au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-redis-cache-connection-string"></a>Chaîne de connexion au cache Redis Azure

### <a name="format"></a>Format

Chaîne « redis.cache.windows.<!--no-hyperlink-->net » suivi des caractères et des chaînes décrits dans le modèle ci-dessous, y compris la chaîne « password » ou « pwd ».

### <a name="pattern"></a>Modèle

- chaîne « redis.cache.windows.<!--no-hyperlink-->net »
- toute combinaison d’entre 1 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- la chaîne « password » ou « pwd »
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison de 43 caractères qui sont des lettres minuscules ou majuscules, des chiffres, une barre oblique (/) ou un signe plus (+)
- un signe égal (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière CEP_Regex_AzureRedisCacheConnectionString recherche le contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve pas de contenu correspondant au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-sas"></a>Azure SAS

### <a name="format"></a>Format

Chaîne « sig » suivie des caractères et des chaînes décrits dans le modèle ci-dessous.

### <a name="pattern"></a>Modèle

- la chaîne « sig »
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison comprise entre 43 et 53 caractères qui sont des lettres minuscules ou majuscules, des chiffres ou le signe de pourcentage (%)
- chaîne « %3d »
- tout caractère qui n’est pas une lettre minuscule ou majuscule, un chiffre ou un signe de pourcentage (%)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière CEP_Regex_AzureSAS recherche du contenu qui correspond au modèle.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```

## <a name="azure-service-bus-connection-string"></a>Chaîne de connexion Azure Service Bus

### <a name="format"></a>Format

Chaîne « EndPoint » suivie des caractères et des chaînes décrits dans le modèle ci-dessous, y compris les chaînes « servicebus.windows.<!--no-hyperlink-->net » et « SharedAccesKey ».

### <a name="pattern"></a>Modèle

- chaîne « Point de terminaison »
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison d’entre 1 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- chaîne « servicebus.windows .<!--no-hyperlink-->net »
- toute combinaison d’entre 1 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- chaîne « SharedAccessKey »
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison de 43 caractères qui sont des lettres minuscules ou majuscules, des chiffres, une barre oblique (/) ou un signe plus (+)
- un signe égal (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière CEP_Regex_AzureServiceBusConnectionString recherche du contenu qui correspond au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve pas de contenu correspondant au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-storage-account-key"></a>Clé de compte de stockage Azure

### <a name="format"></a>Format

Chaîne « DefaultEndpointsProtocol » suivie des caractères et des chaînes décrits dans le modèle ci-dessous, y compris la chaîne « AccountKey ».

### <a name="pattern"></a>Modèle

- chaîne « DefaultEndpointsProtocol »
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison d’entre 1 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- chaîne « AccountKey »
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison de 86 caractères qui sont des lettres minuscules ou majuscules, des chiffres, une barre oblique (/) ou un signe plus (+)
- deux signes égaux (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière CEP_Regex_AzureStorageAccountKey recherche du contenu qui correspond au modèle.
- L’expression régulière CEP_AzureEmulatorStorageAccountFilter ne trouve pas de contenu correspondant au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve pas de contenu correspondant au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="cep_azure_emulator_storage_account_filter"></a>CEP_azure_emulator_storage_account_filter

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Techniquement, ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.)

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-storage-account-key-generic"></a>Clé de compte de stockage Azure (générique)

### <a name="format"></a>Format

Toute combinaison de 86 lettres minuscules ou majuscules, chiffres, barre oblique (/) ou signe plus (+), précédée ou suivie des caractères indiqués dans le modèle ci-dessous.

### <a name="pattern"></a>Modèle

- zéro à l’un des symboles supérieurs (>), apostrophe ('), signe égal (=), guillemet (« ) ou signe numérique (#)
- toute combinaison de 86 caractères qui sont des lettres minuscules ou majuscules, des chiffres, la barre oblique (/) ou le signe plus (+)
- deux signes égaux (=)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière CEP_Regex_AzureStorageAccountKeyGeneric recherche du contenu qui correspond au modèle.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```

## <a name="belgium-drivers-license-number"></a>Numéro de permis de conduire en Belgique

### <a name="format"></a>Format

10 chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

10 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_belgium_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_belgium_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_belgium_eu_drivers_license_number"></a>Keywords_belgium_eu_driver s_license_number

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

## <a name="belgium-national-number"></a>Numéro national belge

### <a name="format"></a>Format

11 chiffres plus délimiteurs facultatifs

### <a name="pattern"></a>Modèle

11 chiffres plus des délimiteurs :

- six chiffres et deux périodes facultatives au format YY. MM.DD pour la date de naissance
- Délimiteur facultatif à partir d’un point, d’un tiret, d’un espace
- trois chiffres séquentiels (impairs pour les mâles, même pour les femelles)
- Délimiteur facultatif à partir d’un point, d’un tiret, d’un espace
- deux chiffres de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_belgium_national_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_belgium_national_number est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_belgium_national_number"></a>Keyword_belgium_national_number

- belasting aantal
- Bnn #
- Bnn
- carte d’identité
- identifiant national
- identifiantnational #
- identificatie
- Identification
- identifikation
- identifikationsnummer
- identifizierung
- identité
- identiteit
- identiteitskaart
- Identité
- inscription
- numéro national
- registre national
- nationalnumber #
- nationalnumber
- Nif #
- Nif
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
- Enregistrement
- registrationsnumme
- registrierung
- numéro de sécurité sociale
- Ssn #
- Ssn
- steuernummer
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="belgium-passport-number"></a>Numéro de passeport en Belgique

### <a name="format"></a>Format

deux lettres suivies de six chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

deux lettres et suivies de six chiffres

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

 Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_belgium_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_belgium_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date2` régulière recherche la date au format MM YY DD ou un mot clé à partir ou `Keywords_eu_passport_date` `Keywords_belgium_eu_passport_number` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_belgium_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_belgium_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
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
- Carte Passeport
- Passeport livre
- Pass-Nr
- Passnummer
- reisepass kein

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="belgium-physical-addresses"></a>Adresses physiques belges

Cette entité nommée non groupée détecte les modèles liés aux adresses physiques en provenance de Belgique. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="belgium-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée en Belgique

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Modèle alphanumérique à 12 caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique à 12 caractères :

- une lettre B ou b
- une lettre E ou e
- un chiffre 0
- un chiffre de 1 à 9
- un point ou un trait d’union ou un espace facultatif
- quatre chiffres
- un point ou un trait d’union ou un espace facultatif
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_belgium_value_added_tax_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_belgium_value_added_tax_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_belgium_value_added_tax_number recherche le contenu qui correspond au modèle.

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
### <a name="keywords"></a>Mots-clés

#### <a name="keyword_belgium_value_added_tax_number"></a>Keyword_belgium_value_added_tax_number

- nº tva
- numéro de tva
- vat no
- numéro t.v.a
- umsatzsteuer-identifikationsnummer
- umsatzsteuernummer
- Au fait
- Au fait #
- Tva #

## <a name="blood-test-terms"></a>Termes de l’analyse de sang

Cette entité nommée non groupée détecte les termes liés aux tests sanguins, tels que *hCG*. Il prend uniquement en charge les termes anglais. Il est également inclus dans les [conditions générales médicales](#all-medical-terms-and-conditions) regroupées sous le nom d’entité SIT.

### <a name="confidence-level"></a>Niveau de confiance

Élevé

## <a name="brand-medication-names"></a>Noms des médicaments de marque

Cette entité nommée non groupée détecte les noms des médicaments de marque, tels que *le Tylenol*. Il prend uniquement en charge les termes anglais. Il est également inclus dans les [conditions générales médicales](#all-medical-terms-and-conditions) regroupées sous le nom d’entité SIT.

### <a name="confidence-level"></a>Niveau de confiance

Élevé

## <a name="brazil-cpf-number"></a>Numéro CPF du Brésil

### <a name="format"></a>Format

11 chiffres qui incluent un chiffre de contrôle et peuvent ou non être mis en forme 

### <a name="pattern"></a>Modèle

Formaté:

- trois chiffres
- un point
- trois chiffres
- un point
- trois chiffres
- un trait d’union
- deux chiffres qui sont des chiffres de vérification

Mémoire:

- 11 chiffres où les deux derniers sont des chiffres de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_brazil_cpf trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_brazil_cpf est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_brazil_cpf"></a>Keyword_brazil_cpf

- CPF
- Identification
- Inscription
- Revenus
- Cadastro de Pessoas Físicas
- Imposto
- Identificação
- Inscrição
- Receita

## <a name="brazil-legal-entity-number-cnpj"></a>Numéro d’entité juridique du Brésil (CNPJ)

### <a name="format"></a>Format

14 chiffres qui incluent un numéro d’enregistrement, un numéro de succursale et des chiffres de contrôle, avec des délimiteurs en plus

### <a name="pattern"></a>Modèle

14 chiffres plus des délimiteurs :

- deux chiffres
- un point
- trois chiffres
- un point
- trois chiffres (ces huit premiers chiffres sont le numéro d’inscription)
- une barre oblique
- Numéro de branche à quatre chiffres
- un trait d’union
- deux chiffres qui sont des chiffres de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_brazil_cnpj trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_brazil_cnpj est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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
- Société
- CNPJ
- Cadastro Nacional da Pessoa Jurídica
- Cadastro Geral de Contribuintes
- CGC
- Pessoa jurídica
- Pessoas jurídicas
- Situação cadastral
- Inscrição
- Empresa

## <a name="brazil-national-identification-card-rg"></a>Carte d’identification nationale du Brésil (RG)

### <a name="format"></a>Format

Registro Geral (ancien format) : Neuf chiffres

Registro de Identidade (RIC) (nouveau format) : 11 chiffres

### <a name="pattern"></a>Modèle

Registro Geral (ancien format) :

- deux chiffres
- un point
- trois chiffres
- un point
- trois chiffres
- un trait d’union
- un chiffre qui est un chiffre à cocher

Registro de Identidade (RIC) (nouveau format) :

- 10 chiffres
- un trait d’union
- un chiffre qui est un chiffre à cocher

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

- Cédula de identidade
- Carte d’identité
- id national
- Número de registro
- Registro de Identidade
- Registro Geral
- RG (ce mot clé respecte la casse)
- RIC (ce mot clé respecte la casse)

## <a name="brazil-physical-addresses"></a>Adresses physiques du Brésil

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique du Brésil. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="bulgaria-drivers-license-number"></a>Numéro de permis de conduire en Bulgarie

### <a name="format"></a>Format

neuf chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_bulgaria_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_bulgaria_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_bulgaria_eu_drivers_license_number"></a>Keywords_bulgaria_eu_driver s_license_number

- свидетелство за управление на мпс
- свидетелство за управление на моторно превозно средство
- сумпс
- шофьорска книжка
- шофьорски книжки

## <a name="bulgaria-passport-number"></a>Numéro de passeport en Bulgarie

### <a name="format"></a>Format

neuf chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_bulgaria_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_bulgaria_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_bulgaria_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_bulgaria_eu_passport_number` est trouvé.

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
### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
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

- date du problème
- date d’expiration

## <a name="bulgaria-physical-addresses"></a>Adresses physiques bulgares

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique en provenance de Bulgarie. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="bulgaria-uniform-civil-number"></a>Numéro civil uniforme en Bulgarie
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

10 chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

10 chiffres sans espaces et délimiteurs

- six chiffres qui correspondent à la date de naissance (AAAAMMD)
- deux chiffres qui correspondent à l’ordre de naissance
- un chiffre qui correspond au sexe : un chiffre pair pour un homme et un chiffre impair pour la femme
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_bulgaria_eu_national_id_card` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_bulgaria_eu_national_id_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_bulgaria_eu_national_id_card` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_bulgaria_eu_national_id_card"></a>Keywords_bulgaria_eu_national_id_card

- Bnn #
- Bnn
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
- personnel non
- numéro personnel
- personalidnumber #
- numéro de sécurité sociale
- Ssn #
- Ssn
- ID civil uniforme
- non civil uniforme
- numéro civil uniforme
- uniformcivilno #
- uniformcivilno
- uniformcivilnumber #
- uniformcivilnumber
- numéro de citoyenneté unique
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

## <a name="canada-bank-account-number"></a>Numéro de compte bancaire au Canada

### <a name="format"></a>Format

7 ou 12 chiffres

### <a name="pattern"></a>Modèle

Un numéro de compte bancaire du Canada est de 7 ou 12 chiffres.

Un numéro de transit de compte bancaire du Canada est indiqué au format suivant :

- cinq chiffres
- un trait d’union
- trois chiffres OU
- un zéro « 0 »
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Regex_canada_bank_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_canada_bank_account_number est trouvé.
- L’expression régulière Regex_canada_bank_account_transit_number trouve un contenu qui correspond au modèle.

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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

## <a name="canada-drivers-license-number"></a>Numéro de permis de conduire au Canada

### <a name="format"></a>Format

Varie selon la province

### <a name="pattern"></a>Modèle

Différents modèles couvrant :

- Alberta
- Colombie-britannique
- Manitoba
- Nouveau-Brunswick
- Terre-Neuve-et-Labrador
- Nouvelle-Écosse
- Ontario
- Île-du-Prince-Édouard
- Québec
- Saskatchewan

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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
- Driver’License
- Licences de pilote
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
- Identification
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
- Driver’License #
- Licences de pilote #
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
- Id #
- Id #
- #carte carte d’identification
- #cartes carte d’identification
- idcard #
- #carte d’identification
- #cartes d’identification
- Identification #

## <a name="canada-health-service-number"></a>Numéro du service de santé du Canada

### <a name="format"></a>Format

 10 chiffres

### <a name="pattern"></a>Modèle

10 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_canada_health_service_number"></a>Keyword_canada_health_service_number

- numéro d’assurance-maladie
- informations sur le patient
- services de santé
- services spécialisés
- accident automobile
- hôpital pour malades
- Psychiatre
- indemnisation des salariés
- Handicap

## <a name="canada-passport-number"></a>Numéro de passeport du Canada

### <a name="format"></a>Format

deux lettres majuscules suivies de six chiffres

### <a name="pattern"></a>Modèle

deux lettres majuscules suivies de six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Regex_canada_passport_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keyword_canada_passport_number ou de Keyword_passport est trouvé.

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

### <a name="keywords"></a>Mots-clés

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
- Passeport #
- PassportID
- Passportno
- passportnumber
- パスポート
- パスポート番号
- パのポートのNum
- パスポート＃
- Numéro de passeport
- Passeport n°
- Passeport numéro
- # Passeport
- Passeport #
- PasseportNon
- Passeportn °

## <a name="canada-personal-health-identification-number-phin"></a>Numéro d’identification de la santé personnelle du Canada (PHIN)

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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
- Québec
- Territoires du Nord-Ouest
- Ontario
- Colombie-britannique
- Alberta
- Saskatchewan
- Manitoba
- Yukon
- Terre-Neuve-et-Labrador
- Nouveau-Brunswick
- Nouvelle-Écosse
- Île-du-Prince-Édouard
- Canada

## <a name="canada-physical-addresses"></a>Adresses physiques du Canada

Cette entité nommée non regroupée détecte les modèles liés à l’adresse physique du Canada. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="canada-social-insurance-number"></a>Numéro d’assurance sociale du Canada

### <a name="format"></a>Format

neuf chiffres avec des traits d’union ou des espaces facultatifs

### <a name="pattern"></a>Modèle

Formaté:

- trois chiffres
- un trait d’union ou un espace
- trois chiffres
- un trait d’union ou un espace
- trois chiffres

Non mis en forme : neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_canadian_sin trouve un contenu qui correspond au modèle.
- Au moins deux des modèles suivants :
    - Un mot clé figurant dans la liste Keyword_sin est trouvé.
    - Un mot clé figurant dans la liste Keyword_sin_collaborative est trouvé.
    - La fonction Func_eu_date trouve une date au format correct.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_sin"></a>Keyword_sin

- assoc
- assurance sociale
- numéro d’assurance sociale
- Péchés
- Ssn
- ssns
- sécurité sociale
- numéro d’assurance sociale
- numéro d’identification nationale
- id national
- Péché #
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

## <a name="chile-identity-card-number"></a>Numéro de carte d’identité chilienne

### <a name="format"></a>Format

sept à huit chiffres plus délimiteurs un chiffre ou une lettre de vérification

### <a name="pattern"></a>Modèle

sept à huit chiffres plus délimiteurs :

- un à deux chiffres
- une période facultative
- trois chiffres
- une période facultative
- trois chiffres
- un tiret
- un chiffre ou une lettre (non sensible à la casse) qui est un chiffre à cocher

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_chile_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_chile_id_card est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_chile_id_card"></a>Keyword_chile_id_card

- cédula de identidad
- identificación
- numéro d’identification nationale
- numéro d’identification nationale
- id national
- número de identificación nacional
- rol único nacional
- rol único tributario
- COURIR
- ORNIÈRE
- tarjeta de identificación
- Rol Unico Nacional
- Rol Unico Tributario
- COURIR #
- ORNIÈRE #
- nationaluniqueroleID #
- nacional identidad
- número identificación
- identidad número
- numero identificacion
- identidad nombreuses
- Identité chilienne non.
- Numéro d’identité chilien
- Identité chilienne #
- Registre fiscal unique
- Unique Tributary Role
- Rôle fiscal unique
- Numéro de tribut unique
- Numéro national unique
- Rôle national unique
- Rôle unique national
- Identité chilienne non.
- Numéro d’identité chilien
- Identité chilienne #
- R.U.T
- R.U.N

## <a name="china-resident-identity-card-prc-number"></a>Numéro de carte d’identité de résident en Chine

### <a name="format"></a>Format

18 chiffres

### <a name="pattern"></a>Modèle

18 chiffres :

- six chiffres qui sont un code d’adresse
- huit chiffres sous la forme YYYYMMDD, qui sont la date de naissance
- trois chiffres qui sont un code de commande
- un chiffre qui est un chiffre à cocher

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_china_resident_id trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_china_resident_id est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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

14 à 19 chiffres qui peuvent être mis en forme ou non mis en forme (ddddddddddddddd) et qui doivent réussir le test Luhn.

### <a name="pattern"></a>Modèle

Détecte les cartes de toutes les grandes marques du monde entier, y compris Visa, MasterCard, Discover Card, JCB, American Express, cartes cadeaux, cartes de dîner, Rupay et China UnionPay.

### <a name="checksum"></a>Somme de contrôle

Oui, la vérification Luhn

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_credit_card trouve un contenu qui correspond au modèle.
- L’une des conditions suivantes est vraie :
  - Un mot clé figurant dans la liste Keyword_cc_verification est trouvé.
  - Un mot clé figurant dans la liste Keyword_cc_name est trouvé.
  - La fonction Func_expiration_date trouve une date au format correct.
- La somme de contrôle est correcte.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_cc_verification"></a>Keyword_cc_verification

- vérification de la carte
- numéro d’identification de la carte
- cvn
- nic
- Cvc2
- Cvv2
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
- Cod. Sicurezza
- cod sicurezza
- n autorizzazione
- Código
- Codigo
- Cod. Seg
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- cód. Segurança
- Cod. seguranca
- Cod. Segurança
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
- Valor
- vencimento
- Transaction
- numéro de transaction
- numéro de référence
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

#### <a name="keyword_cc_name"></a>Keyword_cc_name

- Amex
- american express
- americanexpress
- americano espresso
- Visa
- Mastercard
- master card
- Mc
- Mastercard
- master cards
- diner’s Club
- diners club
- Dinersclub
- Découvrir
- discover card
- discovercard
- discover cards
- JCB
- BrandSmart
- japanese card bureau
- carte blanche
- carteblanche
- carte de crédit
- Cc #
- cc#:

- date d’expiration
- date d’exp
- date d’expiration
- date d’expiration
- date d’exp
- date expiration
- carte bancaire
- Bankcard
- numéro de carte
- num de carte
- cardnumber
- cardnumbers
- numéros de carte
- Creditcard
- cartes de crédit
- cartes de crédit
- ccn
- titulaire de la carte
- Détenteur
- titulaires de la carte
- Titulaires
- carte de vérification
- coche
- cartes de vérification
- cartes de contrôle
- carte de débit
- debitcard
- cartes de débit
- cartes de débit
- carte de retrait
- atmcard
- cartes de retrait
- cartes d’atmcard
- Enroute
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
- carte no
- numéro de carte
- carte bancaire
- carte de crédit
- carte de credit
- numéro de carte
- numero de carte
- nº de la carte
- nº de carte
- kreditkarte
- Karte
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
- Â¡n. Carta
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
- non. de tarjeta
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
- nº. do cartão
- no do cartão
- no do cartao
- non. do cartão
- non. do cartao
- rupay
- salaire des syndicats
- unionpay
- diner’s
- Diners
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
- 中国银联
- 银联

## <a name="croatia-drivers-license-number"></a>Numéro de permis de conduire en Croatie

### <a name="format"></a>Format

huit chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_croatia_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_croatia_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
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

## <a name="croatia-identity-card-number"></a>Numéro de carte d’identité en Croatie

Cette entité est incluse dans le type d’informations sensibles numéro d’identification nationale de l’UE. Il est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_croatia_id_card"></a>Keyword_croatia_id_card

- majstorski broj građana
- numéro de citoyen maître
- nacionalni identifikacijski broj
- numéro d’identification nationale
- Oib #
- Oib
- osobna iskaznica
- iD osobni
- osobni identifikacijski broj
- numéro d’identification personnelle
- porezni broj
- porezni identifikacijski broj
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="croatia-passport-number"></a>Numéro de passeport en Croatie

### <a name="format"></a>Format

neuf chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_croatia_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_croatia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_croatia_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_croatia_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_croatia_eu_passport_number"></a>Keywords_croatia_eu_passport_number

- broj putovnice
- Br. Putovnice
- br putovnice

## <a name="croatia-personal-identification-oib-number"></a>Numéro d’identification personnelle croate (OIB)

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres :

- 10 chiffres
- chiffre final est un chiffre à cocher

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_croatia_oib_number trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_croatia_eu_tax_file_number est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_croatia_oib_number"></a>Keyword_croatia_oib_number

- majstorski broj građana
- numéro de citoyen maître
- nacionalni identifikacijski broj
- numéro d’identification nationale
- Oib #
- Oib
- osobna iskaznica
- iD osobni
- osobni identifikacijski broj
- numéro d’identification personnelle
- porezni broj
- porezni identifikacijski broj
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="croatia-physical-addresses"></a>Adresses physiques croates

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique en provenance de Croatie. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="cyprus-drivers-license-number"></a>Numéro de permis de conduire chypriote

### <a name="format"></a>Format

12 chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

12 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_cyprus_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_cyprus_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_cyprus_eu_drivers_license_number"></a>Keywords_cyprus_eu_driver s_license_number

- άδεια οδήγησης
- αριθμό άδειας οδήγησης
- άδειες οδήγησης

## <a name="cyprus-identity-card"></a>Carte d’identité de Chypre

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

10 chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

10 chiffres

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_cyprus_eu_national_id_card` régulière recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_cyprus_eu_national_id_card` trouvé.

```xml
      <!-- Cyprus Identity Card -->
      <Entity id="3ba8afe5-7a6c-4929-8247-0001b6878438" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_national_id_card" />
          <Match idRef="Keywords_cyprus_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_cyprus_eu_national_id_card"></a>Keywords_cyprus_eu_national_id_card

- Numéro de carte d’ID
- numéro de carte d’identité
- kimlik karti
- numéro d’identification nationale
- numéro d’ID personnel
- ταυτοτητασ

## <a name="cyprus-passport-number"></a>Numéro de passeport à Chypre

### <a name="format"></a>Format

une lettre suivie de 6 à 8 chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

une lettre suivie de six à huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_cyprus_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_cyprus_eu_passport_number` est trouvé.
- L’expression `Regex_cyprus_eu_passport_date` régulière recherche la date au format DD/MM/AAAA ou un mot clé `Keywords_cyprus_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_cyprus_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_cyprus_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passeport #
- Passeport #
- passportid
- Passeports
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
- pasaport numarası
- Pasaport no.
- Αρ. Διαβατηρίου

#### <a name="keywords_cyprus_eu_passport_date"></a>Keywords_cyprus_eu_passport_date

- expire le
- émis le

## <a name="cyprus-physical-addresses"></a>Adresses physiques de Chypre

Cette entité nommée non regroupée détecte les modèles liés à l’adresse physique de Chypre. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="cyprus-tax-identification-number"></a>Numéro d’identification fiscale de Chypre

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

huit chiffres et une lettre dans le modèle spécifié

### <a name="pattern"></a>Modèle

huit chiffres et une lettre :

- un « 0 » ou « 9 »
- sept chiffres
- une lettre (non sensible à la casse)

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_cyprus_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_cyprus_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_cyprus_eu_tax_file_number` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_cyprus_eu_tax_file_number"></a>Keywords_cyprus_eu_tax_file_number

- id fiscal
- code d’identification fiscale
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- tic #
- tic
- iD d’tin
- tin no
- Étain #
- vergi kimlik kodu
- vergi kimlik numarası
- αριθμός φορολογικού μητρώου
- κωδικός φορολογικού μητρώου
- φορολογική ταυτότητα
- φορολογικού κωδικού

## <a name="czech-drivers-license-number"></a>Numéro de permis de conduire tchèque

### <a name="format"></a>Format

deux lettres suivies de six chiffres

### <a name="pattern"></a>Modèle

huit lettres et chiffres :

- lettre 'E' (non sensible à la casse)
- une lettre
- un espace (facultatif)
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_czech_republic_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_czech_republic_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_czech_republic_eu_drivers_license_number"></a>Keywords_czech_republic_eu_driver s_license_number

- řidičský prúkaz
- řidičské průkazy
- číslo řidičského průkazu
- čísla řidičských průkazů

## <a name="czech-passport-number"></a>Numéro de passeport tchèque

### <a name="format"></a>Format

huit chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

huit chiffres sans espaces ni délimiteurs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_czech_republic_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_czech_republic_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_czech_republic_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_czech_republic_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_czech_republic_eu_passport_number"></a>Keywords_czech_republic_eu_passport_number

- cestovní pas
- číslo pasu
- cestovní pasu
- passeport no
- čísla pasu

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="czech-personal-identity-number"></a>Numéro d’identité personnelle tchèque

### <a name="format"></a>Format

neuf chiffres avec barre oblique facultative (ancien format)

10 chiffres avec barre oblique facultative (nouveau format)

### <a name="pattern"></a>Modèle

neuf chiffres (ancien format) :

- six chiffres qui représentent la date de naissance
- une barre oblique facultative
- trois chiffres

10 chiffres (nouveau format) :

- six chiffres qui représentent la date de naissance
- une barre oblique facultative
- quatre chiffres où le dernier chiffre est un chiffre à cocher

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_czech_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_czech_id_card est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_czech_id_card_new_format recherche le contenu qui correspond au modèle.
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
### <a name="keywords"></a>Mots-clés

#### <a name="keyword_czech_id_card"></a>Keyword_czech_id_card

- nombre de naissances
- ID de république tchèque
- czechidno #
- daňové číslo
- identifikační číslo
- identity no
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
- numéro d’identification personnelle
- numéro personnel
- Pid #
- pid
- pojištění číslo
- rč
- rodne cislo
- rodné číslo
- Ssn
- Ssn #
- numéro de sécurité sociale
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #
- numéro d’identification unique

## <a name="czech-republic-physical-addresses"></a>Adresses physiques de la République tchèque

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique de la République tchèque. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="denmark-drivers-license-number"></a>Numéro de permis de conduire au Danemark

### <a name="format"></a>Format

huit chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_denmark_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_denmark_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_denmark_eu_drivers_license_number"></a>Keywords_denmark_eu_driver s_license_number

- kørekort
- kørekortnummer

## <a name="denmark-passport-number"></a>Numéro de passeport du Danemark

### <a name="format"></a>Format

neuf chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_denmark_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_denmark_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date2` régulière recherche la date au format JJ MM YY ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_denmark_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_denmark_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passeport #
- Passeport #
- passportid
- Passeports
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

- date du problème
- date d’expiration

## <a name="denmark-personal-identification-number"></a>Numéro d’identification personnelle du Danemark

### <a name="format"></a>Format

10 chiffres contenant un trait d’union

### <a name="pattern"></a>Modèle

10 chiffres :

- six chiffres au format DDMMYY, qui sont la date de naissance
- un espace ou un trait d’union facultatif
- quatre chiffres où le chiffre final est un chiffre à cocher

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Func_denmark_eu_tax_file_number recherche du contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_denmark_id est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Func_denmark_eu_tax_file_number recherche du contenu qui correspond au modèle.
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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_denmark_id"></a>Keyword_denmark_id

- centrale personregister
- civilt registreringssystem
- Cpr
- Cpr #
- gesundheitskarte nummer
- gesundheitsversicherungkarte nummer
- carte d’intégrité
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
- reisekrankenversicherungskartenummer
- rejsesygesikringskort
- Ssn
- Ssn #
- skat id
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
- code fiscal
- carte d’assurance maladie de voyage
- uniqueidentityno #
- numéro d’impôt
- numéro d’enregistrement fiscal
- id fiscal
- numéro d’identification fiscale
- taxid #
- taxnumber #
- tax no
- taxno #
- taxnumber
- identification fiscale non
- Étain #
- taxidno #
- taxidnumber #
- tax no #
- iD d’tin
- tin no
- cpr.nr
- cpnr
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

## <a name="denmark-physical-addresses"></a>Adresses physiques du Danemark

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique du Danemark. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="diseases"></a>Maladies

Cette entité nommée non groupée détecte le texte qui correspond aux noms de maladies, tels que *le diabète*. Il prend uniquement en charge les termes anglais. Il est également inclus dans les [conditions générales médicales](#all-medical-terms-and-conditions) regroupées sous le nom d’entité SIT.

### <a name="confidence-level"></a>Niveau de confiance

Élevé

## <a name="drug-enforcement-agency-dea-number"></a>Numéro de la Drug Enforcement Agency (DEA)

### <a name="format"></a>Format

deux lettres suivies de sept chiffres

### <a name="pattern"></a>Modèle

Le modèle doit inclure tous les éléments suivants :

- une lettre (non sensible à la casse) de cet ensemble de lettres possibles : A/B/F/G/M/P/R, qui est un code inscrit
- une lettre (non sensible à la casse), qui est la première lettre du nom ou du chiffre de l’inscrit « 9 »
- sept chiffres, dont le dernier est le chiffre à cocher

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_dea_number trouve un contenu qui correspond au modèle.
- Un mot clé à partir de `Keyword_dea_number` est trouvé
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_dea_number"></a>Keyword_dea_number

- Dea
- Dea #
- administration de l’application des drogues
- agence de lutte contre les drogues

## <a name="estonia-drivers-license-number"></a>Numéro de permis de conduire estonien

### <a name="format"></a>Format

deux lettres suivies de six chiffres

### <a name="pattern"></a>Modèle

deux lettres et six chiffres :

- les lettres « ET » (non sensibles à la casse)
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_estonia_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_estonia_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_estonia_eu_drivers_license_number"></a>Keywords_estonia_eu_driver s_license_number

- permis de conduire
- juhilubade numbrid
- juhiloa number
- juhiluba

## <a name="estonia-passport-number"></a>Numéro de passeport estonien

### <a name="format"></a>Format

une lettre suivie de sept chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

une lettre suivie de sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_estonia_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_estonia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_estonia_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_estonia_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

eesti kodaniku pass passi number passinumbrid document number no dokumendi nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="estonia-personal-identification-code"></a>Code d’identification personnelle de l’Estonie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

11 chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

11 chiffres :

- un chiffre qui correspond au sexe et au siècle de naissance (nombre impair masculin, même nombre féminin ; 1-2 : 19e siècle ; 3-4 : 20e siècle ; 5-6 : 21e siècle)
- six chiffres qui correspondent à la date de naissance (AAAAMMD)
- trois chiffres qui correspondent à un numéro de série séparant les personnes nées à la même date
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_estonia_eu_national_id_card` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_estonia_eu_national_id_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_estonia_eu_national_id_card` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_estonia_eu_national_id_card"></a>Keywords_estonia_eu_national_id_card

- id-kaart
- Ik
- isikukood #
- isikukood
- maksu id
- maksukohustuslase identifitseerimisnumber
- maksunumber
- numéro d’identification nationale
- numéro national
- code personnel
- numéro d’ID personnel
- code d’identification personnelle
- numéro d’identification personnelle
- personalidnumber #
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="estonia-physical-addresses"></a>Adresses physiques estoniennes

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique de l’Estonie. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="eu-debit-card-number"></a>Numéro de carte de crédit de l'UE

### <a name="format"></a>Format

16 chiffres

### <a name="pattern"></a>Modèle

Modèle complexe et robuste

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_eu_debit_card"></a>Keyword_eu_debit_card

- numéro de compte
- numéro de carte
- n° carte
- numéro de sécurité
- Cc #

#### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- num de compte
- num de compte
- n° compte
- american express
- americanexpress
- americano espresso
- Amex
- carte de retrait
- cartes de retrait
- atm kaart
- atmcard
- cartes d’atmcard
- atmkaart
- atmkaarten
- Bancontact
- carte bancaire
- bankkaart
- titulaire de la carte
- titulaires de la carte
- num de carte
- numéro de carte
- numéros de carte
- type de carte
- cardano numerico
- Détenteur
- Titulaires
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
- coche
- cartes de contrôle
- chequekaart
- Cirrus
- cirrus-edc-maestro
- controlekaart
- controlekaarten
- carte de crédit
- cartes de crédit
- Creditcard
- cartes de crédit
- debetkaart
- debetkaarten
- carte de débit
- cartes de débit
- debitcard
- cartes de débit
- debito automatico
- diners club
- Dinersclub
- Découvrir
- discover card
- discover cards
- discovercard
- discovercards
- débito automático
- Edc
- eigentümername
- carte de crédit européenne
- hoofdkaart
- hoofdkaarten
- in viaggio
- japanese card bureau
- japanse kaartdienst
- Jcb
- Kaart
- kaart num
- kaartaantal
- kaartaantallen
- kaarthouder
- kaarthouders
- Karte
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
- Maestro
- master card
- master cards
- Mastercard
- Mastercard
- Mc
- mister cash
- n carta
- Carta
- no de tarjeta
- no do cartao
- no do cartão
- non. de tarjeta
- non. do cartao
- non. do cartão
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
- Solo
- supporti di scheda
- supporto di scheda
- Interrupteur
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
- Scheda
- v pay
- v-pay
- Visa
- visa plus
- visa electron
- Visto
- Visum
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
- Cod. Seg
- Cod. seguranca
- Cod. Segurança
- Cod. Sicurezza
- codice di sicurezza
- codice di verifica
- Codigo
- codigo de seguranca
- codigo de segurança
- crittogramma
- Cryptogramme
- cryptogramme
- cv2
- cvc
- Cvc2
- cvn
- Cvv
- Cvv2
- cód seguranca
- cód segurança
- cód. seguranca
- cód. Segurança
- Código
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
- non. dell’edizione
- non. di sicurezza
- numéro de sécurité
- numero de verificacao
- numero dell’edizione
- numero di identificazione della
- Scheda
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
- Espira
- Espira
- date d’exp
- exp datum
- expiration
- Expirer
- Expire
- Expiration
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
- Valor
- venc
- vencimento
- vencimiento
- verloopt
- vervaldag
- vervaldatum
- vto
- válido hasta

## <a name="eu-drivers-license-number"></a>Numéro de permis de conduire de l’UE

Ces entités se trouvent dans le numéro de permis de conduire de l’UE et sont des types d’informations sensibles.

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
- [Luxembourg](#luxemburg-drivers-license-number)
- [Malte](#malta-drivers-license-number)
- [Pays-Bas](#netherlands-drivers-license-number)
- [Pologne](#poland-drivers-license-number)
- [Portugal](#portugal-drivers-license-number)
- [Roumanie](#romania-drivers-license-number)
- [République de Slovaquie](#slovakia-drivers-license-number)
- [Slovénie](#slovenia-drivers-license-number)
- [Espagne](#spain-drivers-license-number)
- [Suède](#sweden-drivers-license-number)
- [ROYAUME-UNI.](#uk-drivers-license-number)

## <a name="eu-national-identification-number"></a>Numéro d’identification nationale de l’UE

Ces entités se trouvent dans le numéro d’identification national de l’UE et sont des types d’informations sensibles.

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
- [Luxembourg](#luxemburg-national-identification-number-natural-persons)
- [Malte](#malta-identity-card-number)
- [Pays-Bas](#netherlands-citizens-service-bsn-number)
- [Pologne](#poland-national-id-pesel)
- [Portugal](#portugal-citizen-card-number)
- [Roumanie](#romania-personal-numeric-code-cnp)
- [République de Slovaquie](#slovakia-personal-number)
- [Slovénie](#slovenia-unique-master-citizen-number)
- [Espagne](#spain-dni)
- [ROYAUME-UNI.](#uk-national-insurance-number-nino)

## <a name="eu-passport-number"></a>Numéro de passeport de l’UE

Ces entités se trouvent dans le numéro de passeport de l’UE et sont des types d’informations sensibles. Ces entités se trouvent dans l’offre groupée de numéros de passeport de l’UE.

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
- [Luxembourg](#luxemburg-passport-number)
- [Malte](#malta-passport-number)
- [Pays-Bas](#netherlands-passport-number)
- [Pologne](#poland-passport-number)
- [Portugal](#portugal-passport-number)
- [Roumanie](#romania-passport-number)
- [République de Slovaquie](#slovakia-passport-number)
- [Slovénie](#slovenia-passport-number)
- [Espagne](#spain-passport-number)
- [Suède](#sweden-passport-number)
- [Numéro de passeport des États-Unis/Du Royaume-Uni](#usuk-passport-number)

## <a name="eu-social-security-number-or-equivalent-identification"></a>Numéro de sécurité sociale de l’UE ou identification équivalente

Ces entités se trouvent dans le numéro de sécurité sociale de l’UE ou une identification équivalente et sont des types d’informations sensibles.

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

Ces entités se trouvent dans le type d’informations sensibles du numéro d’identification fiscale de l’UE.

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
- [Luxembourg](#luxemburg-national-identification-number-non-natural-persons)
- [Malte](#malta-tax-identification-number)
- [Pays-Bas](#netherlands-tax-identification-number)
- [Pologne](#poland-tax-identification-number)
- [Portugal](#portugal-tax-identification-number)
- [Roumanie](#romania-personal-numeric-code-cnp)
- [République de Slovaquie](#slovakia-personal-number)
- [Slovénie](#slovenia-tax-identification-number)
- [Espagne](#spain-tax-identification-number)
- [Suède](#sweden-tax-identification-number)
- [ROYAUME-UNI.](#uk-unique-taxpayer-reference-number)

## <a name="finland-drivers-license-number"></a>Numéro de permis de conduire en Finlande

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

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_finland_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_finland_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_finland_eu_drivers_license_number"></a>Keywords_finland_eu_driver s_license_number

- ajokortti
- permis de conduire
- ajokortin nombreux
- kuljettaja lic.
- körkort
- körkortnummer
- förare lic.
- ajokortit
- ajokortin numerot

## <a name="finland-european-health-insurance-number"></a>Numéro d’assurance maladie européen en Finlande

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Nombre à 20 chiffres

### <a name="pattern"></a>Modèle

Nombre à 20 chiffres :

- 10 chiffres - 8024680246
- un espace ou un trait d’union facultatif
- 10 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- Le Regex_Finland_European_Health_Insurance_Number regex recherche le contenu qui correspond au modèle.
- Un mot clé de Keyword_Finland_European_Health_Insurance_Number est trouvé.

```xml
      <!-- Finland European Health Insurance Number -->
      <Entity id="60f75aed-81bf-4625-89b0-0846b9248ee7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Finland_European_Health_Insurance_Number"/>
          <Match idRef="Keyword_Finland_European_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Mots-clés

#### <a name="keyword_finland_european_health_insurance_number"></a>Keyword_finland_european_health_insurance_number

- Ceam #
- Ceam
- finlandehicnumber #
- finska sjukförsäkringskort
- carte d’intégrité
- carte d’assurance maladie
- numéro d’assurance maladie
- hälsokort
- sairaanhoitokortin
- sairausvakuutuskortti
- sairausvakuutusnumero
- sjukförsäkring nummer
- sjukförsäkringskort
- suomen sairausvakuutuskortti
- terveyskortti

## <a name="finland-national-id"></a>ID national de la Finlande

### <a name="format"></a>Format

six chiffres plus un caractère indiquant un siècle plus trois chiffres plus un chiffre à cocher

### <a name="pattern"></a>Modèle

Le modèle doit inclure tous les éléments suivants :

- six chiffres au format DDMMYY, qui sont une date de naissance
- marqueur de siècle ('-', '+' ou 'a')
- Numéro d’identification personnelle à trois chiffres
- un chiffre ou une lettre (non sensible à la casse) qui est un chiffre à cocher

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- la fonction Func_finnish_national_id recherche du contenu qui correspond au modèle
- un mot clé de Keyword_finnish_national_id est trouvé
- la somme de contrôle réussit

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- la fonction Func_finnish_national_id recherche du contenu qui correspond au modèle
- la somme de contrôle réussit

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

### <a name="keywords"></a>Mots-clés

- ainutlaatuinen henkilökohtainen tunnus
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
- ID personnel
- code d’identité personnelle
- personalidnumber #
- personbeteckning
- personnummer
- numéro de sécurité sociale
- sosiaaliturvatunnus
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #
- tunnistenumero
- tunnus numero
- tunnusluku
- tunnusnumero
- verokortti
- veronumero
- verotunniste
- verotunnus

## <a name="finland-passport-number"></a>Numéro de passeport en Finlande

Cette entité est disponible dans le type d’informations sensibles Numéro de passeport de l’UE et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format
combinaison de neuf lettres et chiffres

### <a name="pattern"></a>Modèle

combinaison de neuf lettres et chiffres :

- deux lettres (non sensibles à la casse)
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_finland_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keyword_finland_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_finland_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keyword_finland_passport_number` est trouvé.

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
### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keyword_finland_passport_number"></a>Keyword_finland_passport_number

- suomalainen passi
- passin numero
- passin nombreux. #
- passin numero #
- passin nombreux.
- Passi #
- passi number

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="finland-physical-addresses"></a>Adresses physiques finlandaises

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique de la Finlande. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="france-drivers-license-number"></a>Numéro de permis de conduire en France

Cette entité est disponible dans le type d’informations sensibles numéro de permis de conduire de l’UE et est disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

12 chiffres

### <a name="pattern"></a>Modèle

12 chiffres avec validation pour écarter les modèles similaires, comme les numéros de téléphone français

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- la fonction Func_français_drivers_license recherche du contenu qui correspond au modèle.
- Un mot clé keyword_français_drivers_license est trouvé.

```xml
    <!-- France Driver's License Number -->
    <Entity id="18e55a36-a01b-4b0f-943d-dc10282a1824" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_drivers_license" />
        <Match idRef="Keyword_french_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_french_drivers_license"></a>Keyword_français_drivers_license

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
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

## <a name="france-health-insurance-number"></a>Numéro d’assurance maladie en France

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Nombre à 21 chiffres

### <a name="pattern"></a>Modèle

Nombre à 21 chiffres :

- 10 chiffres
- un espace facultatif
- 10 chiffres
- un espace facultatif
- un chiffre

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- le regex Regex_France_Health_Insurance_Number recherche le contenu qui correspond au modèle.
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
### <a name="keywords"></a>Mots-clés

#### <a name="keyword_france_health_insurance_number"></a>Keyword_France_health_insurance_number

- carte d’assurance
- carte vitale
- carte d’assuré social

## <a name="france-national-id-card-cni"></a>Carte d’identité nationale de France (CNI)

### <a name="format"></a>Format

12 chiffres

### <a name="pattern"></a>Modèle

12 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_france_eu_national_id_card"></a>Keywords_france_eu_national_id_card

- numéro de carte
- carte nationale d’identité
- carte nationale d’idenite no
- Cni #
- Cni
- compte bancaire
- numéro d’identification nationale
- identité nationale
- nationalidno #
- numéro d’assurance maladie
- numéro de carte vitale

## <a name="france-passport-number"></a>Numéro de passeport en France

Cette entité est disponible dans le type d’informations sensibles Numéro de passeport de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

neuf chiffres et lettres

### <a name="pattern"></a>Modèle

neuf chiffres et lettres :

- deux chiffres
- deux lettres (non sensibles à la casse)
- cinq chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_fr_passport` recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_france_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date3` régulière recherche la date au format DD MM AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_fr_passport` recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_france_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
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
- carte passeport
- numéro passeport
- passeport n°
- n° du passeport
- n° passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="france-physical-addresses"></a>Adresses physiques en France

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique de la France. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="france-social-security-number-insee"></a>Numéro de sécurité sociale en France (INSEE)

### <a name="format"></a>Format

15 chiffres

### <a name="pattern"></a>Modèle

Doit correspondre à l’un des deux modèles suivants :

- 13 chiffres suivis d’un espace suivi de deux chiffres

  ou

- 15 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_french_insee` recherche le contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_fr_insee est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_français_insee ou Func_fr_insee recherche du contenu qui correspond au modèle.
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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_fr_insee"></a>Keyword_fr_insee

- code sécu
- d’identité nationale
- Insee
- fssn #
- le numéro d’identification nationale
- le code de la sécurité sociale
- id national
- numéro d’identification nationale
- n° d’identité
- non. d’identité
- numéro d’assurance
- numéro d’identité
- numéro d’identité
- numéro de sécu
- numéro de sécurité sociale
- n° d’identité
- non. d’identite
- Ssn
- Ssn #
- sécurité sociale
- securité sociale
- securite sociale
- socialsecuritynumber
- numéro de sécurité sociale
- code de sécurité sociale
- numéro d’assurance sociale

## <a name="france-tax-identification-number"></a>Numéro d’identification fiscale en France

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_france_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_france_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_france_eu_tax_file_number` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_france_eu_tax_file_number"></a>Keywords_france_eu_tax_file_number

- numéro d’identification fiscale
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="france-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée en France

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Modèle alphanumérique de 13 caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique de 13 caractères :

- deux lettres - FR (ne respectant pas la casse)
- un espace ou un trait d’union facultatif
- deux lettres ou chiffres
- un espace, un point, un trait d’union ou une virgule facultatif
- trois chiffres
- un espace, un point, un trait d’union ou une virgule facultatif
- trois chiffres
- un espace, un point, un trait d’union ou une virgule facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_france_value_added_tax_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_france_value_added_tax_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_france_value_added_tax_number recherche le contenu qui correspond au modèle.

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
### <a name="keywords"></a>Mots-clés

#### <a name="keyword_france_value_added_tax_number"></a>Keyword_France_value_added_tax_number

- numéro de tva
- vat no
- Tva #
- taxe sur la valeur ajoutée
- siren identification no numéro d’identification taxe sur valeur ajoutée
- taxe valeur ajoutée
- taxe sur la valeur ajoutée
- n° tva
- numéro de tva
- numéro d’identification siren

## <a name="generic-medication-names"></a>Noms de médicaments génériques

Cette entité nommée non regroupée détecte les noms des médicaments génériques, tels que *l’acétaminophène*. Il prend uniquement en charge les termes anglais. Il est également inclus dans les [conditions générales médicales](#all-medical-terms-and-conditions) regroupées sous le nom d’entité SIT.

### <a name="confidence-level"></a>Niveau de confiance

Élevé

## <a name="germany-drivers-license-number"></a>Numéro de permis de conduire en Allemagne

Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles numéro de permis de conduire de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

combinaison de 11 chiffres et lettres

### <a name="pattern"></a>Modèle

11 chiffres et lettres (non sensibles à la casse) :

- un chiffre ou une lettre
- deux chiffres
- six chiffres ou lettres
- un chiffre
- un chiffre ou une lettre

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dlno

## <a name="germany-identity-card-number"></a>Numéro de carte d’identité en Allemagne

### <a name="format"></a>Format

depuis le 1er novembre 2010 : 9 à 11 lettres et chiffres

du 1er avril 1987 au 31 octobre 2010 : 10 chiffres

### <a name="pattern"></a>Modèle

depuis le 1er novembre 2010 : modèle alphanumérique de 9 à 11 caractères
- one L, M, N, P, R, T, V, W, X, Y (ne respectant pas la casse)
- huit chiffres ou lettres en C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y et Z (ne respectant pas la casse)
- chiffre de vérification facultatif
- D/D facultatif

du 1er avril 1987 au 31 octobre 2010 :

- 10 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_german_id_card_with_check` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_germany_id_card` trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_germany_id_card` régulière recherche du contenu qui correspond au modèle (9 caractères sans chiffre à cocher émis avant 2010 ou 10 chiffres avec le modèle posy 2010).
- Un mot clé figurant dans la liste Keyword_germany_id_card est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_german_id_card_with_check` recherche le contenu qui correspond au modèle.
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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- ausweis
- gpid
- Identification
- identifikation
- identifizierungsnummer
- Carte d’identité
- numéro d’identité
- id-nummer
- ID personnel
- personalausweis
- persönliche id nummer
- persönliche identifikationsnummer
- persönliche-id-nummer

## <a name="germany-passport-number"></a>Numéro de passeport en Allemagne

### <a name="format"></a>Format

9 à 11 caractères

### <a name="pattern"></a>Modèle

- une lettre en C, F, G, H, J, K (ne respectant pas la casse)
- huit chiffres ou lettres en C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y et Z (ne respectant pas la casse)
- chiffre de vérification facultatif
- D/D facultatif

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_german_passport_checksum` recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keyword_german_passport` `Keywords_eu_passport_number_common` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_german_passport` recherche le contenu qui correspond au modèle de neuf caractères (sans chiffre de vérification et d/D facultatif).
- Un mot clé à partir ou `Keyword_german_passport` `Keywords_eu_passport_number_common` est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_german_passport_checksum` recherche le contenu qui correspond au modèle.
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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_german_passport"></a>Keyword_german_passport

- reisepasse
- reisepassnummer
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe
- passeport non.
- passeport no

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

## <a name="germany-physical-addresses"></a>Adresses physiques allemandes

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique en provenance d’Allemagne. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="germany-tax-identification-number"></a>Numéro d’identification fiscale en Allemagne

### <a name="format"></a>Format

11 chiffres sans espaces et délimiteurs

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_germany_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_germany_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_germany_eu_tax_file_number` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_germany_eu_tax_file_number"></a>Keywords_germany_eu_tax_file_number

- identifikationsnummer
- steuer id
- steueridentifikationsnummer
- steuernummer
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #
- Zinn #
- Zinn
- zinnnummer

## <a name="germany-value-added-tax-number"></a>Numéro d’impôt sur la valeur ajoutée en Allemagne

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Modèle alphanumérique à 11 caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique à 11 caractères :

- une lettre D ou d
- une lettre E ou e
- un espace facultatif
- trois chiffres
- un espace facultatif ou une virgule
- trois chiffres
- un espace facultatif ou une virgule
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_germany_value_added_tax_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_germany_value_added_tax_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_germany_value_added_tax_number recherche le contenu qui correspond au modèle.

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
### <a name="keywords"></a>Mots-clés

#### <a name="keyword_germany_value_added_tax_number"></a>Keyword_germany_value_added_tax_number

- numéro de tva
- vat no
- Tva #
- vat# mehrwertsteuer
- mwst
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer

## <a name="greece-drivers-license-number"></a>Numéro de permis de conduire en Grèce

Cette entité est incluse dans le type d’informations sensibles numéro de permis de conduire de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

neuf chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_greece_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_greece_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_greece_eu_drivers_license_number"></a>Keywords_greece_eu_driver s_license_number

- δεια οδήγησης
- Adeia odigisis
- Άδεια οδήγησης
- Δίπλωμα οδήγησης

## <a name="greece-national-id-card"></a>Carte d’identité nationale grecque

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Regex_greece_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_greece_id_card est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- ID grec
- greek national id
- carte d’ID personnelle grecque
- ID de police grec
- Carte d’identité
- Tautotita
- ταυτότητα
- ταυτότητας

## <a name="greece-passport-number"></a>Numéro de passeport en Grèce

### <a name="format"></a>Format

Deux lettres suivies de sept chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

Deux lettres suivies de sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_greece_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_greece_eu_passport_number` est trouvé.
- L’expression `Regex_greece_eu_passport_date` régulière trouve la date au format DD MMM YY (exemple - 28 août 19) ou à partir de `Keywords_greece_eu_passport_date` laquelle un mot clé est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_greece_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_greece_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
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

## <a name="greece-physical-addresses"></a>Adresses physiques en Grèce

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique de la Grèce. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="greece-social-security-number-amka"></a>Numéro de sécurité sociale en Grèce (AMKA)

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

11 chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

- Six chiffres comme date de naissance YYMMDD
- Quatre chiffres
- un chiffre à cocher

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_greece_eu_ssn` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_greece_eu_ssn_or_equivalent` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_greece_eu_ssn` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_greece_eu_ssn_or_equivalent"></a>Keywords_greece_eu_ssn_or_equivalent

- Ssn
- Ssn #
- sécurité sociale non
- socialsecurityno #
- numéro de sécurité sociale
- Amka
- a.m.k.a.
- Αριθμού Μητρώου Κοινωνικής Ασφάλισης

## <a name="greece-tax-identification-number"></a>Numéro d’identification fiscale en Grèce

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Neuf chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

Neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_greece_eu_tax_file_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_greece_eu_tax_file_number` trouvé.

```xml
      <!-- Greek Tax Identification Number -->
      <Entity id="15a54a5a-53d4-4080-ad43-a2a4fe1d3bf7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_tax_file_number" />
          <Match idRef="Keywords_greece_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_greece_eu_tax_file_number"></a>Keywords_greece_eu_tax_file_number

- Afm #
- Afm
- aφμ|aφμ αός
- aφμ
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- registre fiscal non
- numéro de registre fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- taxregistryno #
- iD d’tin
- tin no
- Étain #
- αριθμός φορολογικού μητρώου
- τον αριθμό φορολογικού μητρώου
- φορολογικού μητρώου νο

## <a name="hong-kong-identity-card-hkid-number"></a>Numéro de carte d’identité de Hong Kong (HKID)

### <a name="format"></a>Format

Combinaison de 8 ou 9 lettres et chiffres plus éventuellement des parenthèses autour du dernier caractère

### <a name="pattern"></a>Modèle

Combinaison de 8 ou 9 lettres :

- 1-2 lettres (non sensibles à la casse)
- Six chiffres
- espace facultatif
- un caractère de vérification (n’importe quel chiffre ou la lettre A) qui est éventuellement entre parenthèses

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_hong_kong_id_card trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_hong_kong_id_card est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_hong_kong_id_card"></a>Keyword_hong_kong_id_card

- hkid
- carte d’identité hong kong
- HKIDC
- carte d’identité
- Carte d’identité
- hk identity card
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

## <a name="hungary-drivers-license-number"></a>Numéro de permis de conduire en Hongrie

### <a name="format"></a>Format

Deux lettres suivies de six chiffres

### <a name="pattern"></a>Modèle

Deux lettres et six chiffres :

- Deux lettres (non sensibles à la casse)
- Six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_hungary_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_hungary_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_hungary_eu_drivers_license_number"></a>Keywords_hungary_eu_driver s_license_number

- vezetoi engedely
- vezetői engedély
- vezetői engedélyek

## <a name="hungary-passport-number"></a>Numéro de passeport en Hongrie

### <a name="format"></a>Format

Deux lettres suivies de six ou sept chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

Deux lettres suivies de six ou sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_hungary_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_hungary_eu_passport_number` est trouvé.
- L’expression `Regex_hungary_eu_passport_date` régulière trouve la date au format DD MMM/MMM YY (exemple - 01 MÁR/MAR 12) ou un mot clé est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_hungary_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_hungary_eu_passport_number` est trouvé.

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
### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
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

- date du problème
- date d’expiration

## <a name="hungary-personal-identification-number"></a>Numéro d’identification personnelle en Hongrie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres :

- Un chiffre qui correspond au sexe, 1 pour les hommes, 2 pour les femmes. D’autres chiffres sont également possibles pour les citoyens nés avant 1900 ou les citoyens ayant la double citoyenneté.
- Six chiffres correspondant à la date de naissance (AAAAMMD)
- Trois chiffres qui correspondent à un numéro de série
- Un chiffre à cocher

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_hungary_eu_national_id_card` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_hungary_eu_national_id_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_hungary_eu_national_id_card` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_hungary_eu_national_id_card"></a>Keywords_hungary_eu_national_id_card

- numéro d’ID
- numéro d’identification
- sz ig
- Sz. Ig.
- sz.ig.
- személyazonosító igazolvány
- személyi igazolvány

## <a name="hungary-physical-addresses"></a>Adresses physiques en Hongrie

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique en provenance de Hongrie. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="hungary-social-security-number-taj"></a>Numéro de sécurité sociale en Hongrie (TAJ)

### <a name="format"></a>Format

Neuf chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

Neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_hungary_eu_ssn_or_equivalent` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_hungary_eu_ssn_or_equivalent` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_hungary_eu_ssn_or_equivalent` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_hungary_eu_ssn_or_equivalent"></a>Keywords_hungary_eu_ssn_or_equivalent

- numéro de sécurité sociale hongrois
- numéro de sécurité sociale
- socialsecuritynumber #
- hssn #
- socialsecuritynno
- hssn
- Taj
- Taj #
- Ssn
- Ssn #
- sécurité sociale non
- áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám
- magyar áfa szám

## <a name="hungary-tax-identification-number"></a>Numéro d’identification fiscale en Hongrie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

10 chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

10 chiffres :

- Un chiffre qui doit être « 8 »
- Huit chiffres
- Un chiffre à cocher

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_hungary_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_hungary_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_hungary_eu_tax_file_number` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_hungary_eu_tax_file_number"></a>Keywords_hungary_eu_tax_file_number

- adóazonosító szám
- adóhatóság szám
- adószám
- fer blanc hongrois
- hungatiantin #
- l’autorité fiscale n’a pas
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #
- numéro de tva

## <a name="hungary-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée en Hongrie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_hungarian_value_added_tax_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_hungarian_value_added_tax_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_hungarian_value_added_tax_number recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_hungary_value_added_tax_number"></a>Keyword_Hungary_value_added_tax_number

- Tva
- numéro de taxe sur la valeur ajoutée
- Tva #
- vatno #
- hungarianvatno #
- tax no.
- taxe sur la valeur ajoutée áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám

## <a name="iceland-physical-addresses"></a>Adresses physiques islandaises

Cette entité nommée non regroupée détecte les modèles liés à l’adresse physique de l’Islande. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyenne

## <a name="impairments-listed-in-the-us-disability-evaluation-under-social-security"></a>Déficiences répertoriées dans l’évaluation des incapacités aux États-Unis sous sécurité sociale

Cette entité nommée non regroupée détecte les noms des déficiences répertoriées dans l’évaluation des incapacités aux États-Unis sous sécurité sociale, comme la *dystrophie musculaire*. Il prend uniquement en charge les termes anglais. Il est également inclus dans les [conditions générales médicales](#all-medical-terms-and-conditions) regroupées sous le nom d’entité SIT.

### <a name="confidence-level"></a>Niveau de confiance

Élevé

## <a name="india-drivers-license-number"></a>Numéro de permis de conduire en Inde

### <a name="format"></a>Format

Modèle alphanumérique à 15 caractères

### <a name="pattern"></a>Modèle

15 lettres ou chiffres :

- deux lettres indiquant le code d’état
- espace ou tiret facultatif
- deux chiffres indiquant le code de ville
- espace ou tiret facultatif
- quatre chiffres indiquant l’année d’émission
- espace ou tiret facultatif
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_india_driving_license` régulière recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_eu_driver's_license_number_common` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_india_driving_license` régulière recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number_common"></a>Keywords_eu_driver s_license_number_common

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

## <a name="india-gst-number"></a>Numéro de TPS en Inde

### <a name="format"></a>Format

Modèle alphanumérique à 15 caractères

### <a name="pattern"></a>Modèle

15 lettres ou chiffres :

- deux chiffres représentant le code d’état valide
- un espace ou un tiret facultatif
- dix caractères représentant le numéro de compte permanent (PAN)
- une lettre ou un chiffre
- un espace ou un tiret facultatif
- une lettre 'z' ou 'Z'
- un espace ou un tiret facultatif
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_india_gst_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_india_gst_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_india_gst_number` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_india_gst_number"></a>Keyword_india_gst_number

- Tps
- gstin
- taxe sur les biens et services
- biens et taxe de service

## <a name="india-permanent-account-number-pan"></a>Numéro de compte permanent de l’Inde (PAN)

### <a name="format"></a>Format

10 lettres ou chiffres

### <a name="pattern"></a>Modèle

10 lettres ou chiffres :

- Trois lettres (non sensibles à la casse)
- Lettre en C, P, H, F, A, T, B, L, J, G (non sensible à la casse)
- Une lettre
- Quatre chiffres
- Lettre qui est un chiffre à cocher alphabétique

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Regex_india_permanent_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_india_permanent_account_number est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- Permanent Account Number
- PAN

## <a name="india-unique-identification-aadhaar-number"></a>Numéro d’identification unique de l’Inde (Aadhaar)

### <a name="format"></a>Format

12 chiffres contenant éventuellement des espaces ou des tirets

### <a name="pattern"></a>Modèle

12 chiffres :

- Chiffre qui n’est pas 0 ou 1
- Trois chiffres
- Éventuellement un tiret ou un espace 
- Quatre chiffres
- Éventuellement un tiret ou un espace 
- Chiffre final, qui est le chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_india_aadhaar trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_india_aadhar est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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
### <a name="keywords"></a>Mots-clés

#### <a name="keyword_india_aadhar"></a>Keyword_india_aadhar
- aadhaar
- aadhar
- aadhar #
- uid
- आधार
- uidai

## <a name="india-voter-id-card"></a>Carte d’identité de l’électeur indien

### <a name="format"></a>Format

Modèle alphanumérique de 10 caractères

### <a name="pattern"></a>Modèle

10 lettres ou chiffres :

- trois lettres
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_india_voter_id_card` régulière recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_india_voter_id_card` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_india_voter_id_card` régulière recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_india_voter_id_card"></a>Keyword_india_voter_id_card

- Électeur
- voterid
- votercard
- voteridcard
- carte d’identité de photo électorale
- ÉPIQUE
- ECI
- élection commmision

## <a name="indonesia-identity-card-ktp-number"></a>Numéro de carte d’identité de l’Indonésie (KTP)

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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
- Ae
- Al
- À
- az
- Ba
- be
- bg
- Bh
- Ch
- Cr
- cy
- Cz
- de
- Dk
- faire
- Ee
- es
- fi
- fo
- fr
- Go
- ge
- Gi
- gl
- Gr
- hr
- hu
- Ie
- il
- is
- it
- Kw
- Kz
- lb
- Li
- lt
- lu
- lv
- Mc
- md
- me
- mk
- mr
- mt
- Mu
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
- Sm
- Amt
- tr
- Vg

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_iban trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots-clés

Aucun

## <a name="international-classification-of-diseases-icd-10-cm"></a>Classification internationale des maladies (ICD-10-CM)

### <a name="format"></a>Format

Dictionary

### <a name="pattern"></a>Modèle

Mot clé

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- Un mot clé de Dictionary_icd_10_updated est trouvé.
- Un mot clé de Dictionary_icd_10_codes est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

Tout terme du dictionnaire de mots clés Dictionary_icd_10_updated, qui est basé sur la [classification internationale des maladies, dixième révision, modification clinique (ICD-10-CM).](https://icd10cmtool.cdc.gov/) Ce type recherche uniquement le terme, pas les codes d’assurance.

Tout terme du dictionnaire de mots clés Dictionary_icd_10_codes, qui est basé sur la [classification internationale des maladies, dixième révision, modification clinique (ICD-10-CM).](https://icd10cmtool.cdc.gov/) Ce type recherche uniquement les codes d’assurance, pas la description.

## <a name="international-classification-of-diseases-icd-9-cm"></a>Classification internationale des maladies (ICD-9-CM)

### <a name="format"></a>Format

Dictionary

### <a name="pattern"></a>Modèle

Mot clé

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- Un mot clé de Dictionary_icd_9_updated est trouvé.
- Un mot clé de Dictionary_icd_9_codes est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

Tout terme du dictionnaire de mots clés Dictionary_icd_9_updated, qui est basé sur la [classification internationale des maladies, neuvième révision, modification clinique (ICD-9-CM).](https://go.microsoft.com/fwlink/?linkid=852605) Ce type recherche uniquement le terme, pas les codes d’assurance.

Tout terme du dictionnaire de mots clés Dictionary_icd_9_codes, qui est basé sur la [classification internationale des maladies, neuvième révision, modification clinique (ICD-9-CM).](https://go.microsoft.com/fwlink/?linkid=852605) Ce type recherche uniquement les codes d’assurance, pas la description.

## <a name="ip-address"></a>Adresse IP

### <a name="format"></a>Format

#### <a name="ipv4"></a>IPv4 :
Modèle complexe qui prend en compte les versions mises en forme (périodes) et non mises en forme (sans périodes) des adresses IPv4

#### <a name="ipv6"></a>IPv6 :
Modèle complexe qui prend en compte les nombres IPv6 mis en forme (y compris les deux-points)

### <a name="pattern"></a>Modèle

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Pour IPv6, une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Regex_ipv6_address trouve un contenu qui correspond au modèle.
- Aucun mot clé figurant dans la liste Keyword_ipaddress n’est trouvé.

Pour IPv4, une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Regex_ipv4_address trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ipaddress est trouvé.

Pour IPv6, une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (ce mot clé respecte la casse)
- ip address
- adresses IP
- protocole internet
- IP-כתובת ה

## <a name="ip-address-v4"></a>Adresse IP v4

### <a name="format"></a>Format

Modèle complexe qui prend en compte les versions mises en forme (périodes) et non mises en forme (sans périodes) des adresses IPv4

### <a name="pattern"></a>Modèle

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_ipv4_address` régulière recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_ipaddress` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_ipv4_address` régulière recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (respect de la casse)
- ip address
- adresses IP
- protocole internet
- IP-כתובת ה

## <a name="ip-address-v6"></a>Adresse IP v6

### <a name="format"></a>Format

Modèle complexe qui prend en compte les nombres IPv6 mis en forme (y compris les deux-points)

### <a name="pattern"></a>Modèle

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_ipv6_address` régulière recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_ipaddress` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_ipv6_address` régulière recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (respect de la casse)
- ip address
- adresses IP
- protocole internet
- IP-כתובת ה

## <a name="ireland-drivers-license-number"></a>Numéro de permis de conduire en Irlande

### <a name="format"></a>Format

Six chiffres suivis de quatre lettres

### <a name="pattern"></a>Modèle

Six chiffres et quatre lettres :

- Six chiffres
- Quatre lettres (non sensibles à la casse)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_ireland_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_ireland_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_ireland_eu_drivers_license_number"></a>Keywords_ireland_eu_driver s_license_number

- ceadúnas tiomána
- ceadúnais tiomána

## <a name="ireland-passport-number"></a>Numéro de passeport en Irlande

### <a name="format"></a>Format

Deux lettres ou chiffres suivis de sept chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

Deux lettres ou chiffres suivis de sept chiffres :

- Deux chiffres ou lettres (non sensibles à la casse)
- Sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_ireland_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_ireland_eu_passport_number` est trouvé.
- L’expression `Regex_ireland_eu_passport_date` régulière recherche la date au format DD MMM/MMM YYYY (exemple - 01 BEA/MAY 1988) ou un mot clé est `Keywords_eu_passport_date` trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_ireland_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_ireland_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_ireland_eu_passport_number"></a>Keywords_ireland_eu_passport_number

- passeport numero
- uimhreacha pasanna
- uimhir pas
- uimhir phas
- uimhreacha pas
- uimhir cárta
- uimhir chárta

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="ireland-personal-public-service-pps-number"></a>Numéro de service public personnel (PPS) en Irlande

### <a name="format"></a>Format

Ancien format (jusqu’au 31 décembre 2012) :

- sept chiffres suivis de 1 à 2 lettres

Nouveau format (1er janvier 2013 et après) :

- sept chiffres suivis de deux lettres

### <a name="pattern"></a>Modèle

Ancien format (jusqu’au 31 décembre 2012) :

- sept chiffres
- une à deux lettres (sans respect de la casse)

Nouveau format (1er janvier 2013 et après) :

- sept chiffres
- une lettre (non sensible à la casse) qui est un chiffre à cocher alphabétique
- Lettre facultative dans la plage A-I ou « W »

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_ireland_pps trouve un contenu qui correspond au modèle.
- Un mot clé de Keywords_ireland_eu_national_id_card est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_ireland_eu_national_id_card"></a>Keywords_ireland_eu_national_id_card

- service d’identité du client
- numéro d’identification
- numéro d’ID personnel
- numéro de service public personnel
- service personnel non
- phearsanta seirbhíse poiblí
- pps no
- pps number
- pps num
- pps service no
- ppsn
- ppsno #
- ppsno
- Psp
- service public non
- publicserviceno #
- publicserviceno
- chiffre d’affaires et d’assurance sociale
- rsi no
- nombre rsi
- rsin
- client seirbhís aitheantais
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phearsanta
- uimhir phearsanta seirbhíse poiblí
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="ireland-physical-addresses"></a>Adresses physiques d’Irlande

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique de l’Irlande. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="israel-bank-account-number"></a>Numéro de compte bancaire en Israël

### <a name="format"></a>Format

13 chiffres

### <a name="pattern"></a>Modèle

Formaté:

- deux chiffres
- un tiret
- trois chiffres
- un tiret
- huit chiffres

Mémoire:

- 	13 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_israel_bank_account_number"></a>Keyword_israel_bank_account_number

- Bank Account Number
- Bank Account
- Numéro de compte
- מספר חשבון בנק

## <a name="israel-national-identification-number"></a>Numéro d’identification nationale d’Israël

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_israel_national_id"></a>Keyword_Israel_National_ID

- מספר זהות
- מספר זיה וי
- מספר זיהוי ישר אלי
- זהותישר אלית
- هو ية اسرائيل ية عدد
- هوية إسرائ يلية
- رقم الهوية
- عدد هوية فريدة من نوعها
- idnumber #
- numéro d’ID
- identity no
- identitynumber #
- numéro d’identité
- israeliidentitynumber
- ID personnel
- ID unique

## <a name="italy-drivers-license-number"></a>Numéro de permis de conduire en Italie

Cette entité de type est incluse dans le type d’informations sensibles numéro de permis de conduire de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

combinaison de 10 lettres et chiffres

### <a name="pattern"></a>Modèle

une combinaison de 10 lettres et chiffres :

- une lettre (non sensible à la casse)
- la lettre « A » ou « V » (non sensible à la casse)
- sept chiffres
- une lettre (non sensible à la casse)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_italy_drivers_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keyword_italy_drivers_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
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

## <a name="italy-fiscal-code"></a>Code fiscal de l’Italie
Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

combinaison de 16 caractères de lettres et de chiffres dans le modèle spécifié

### <a name="pattern"></a>Modèle

Combinaison de 16 caractères de lettres et de chiffres :

- trois lettres qui correspondent aux trois premières consonnes dans le nom de famille
- trois lettres qui correspondent aux première, troisième et quatrième consonnes dans le prénom
- deux chiffres qui correspondent aux derniers chiffres de l’année de naissance
- une lettre qui correspond à la lettre pour le mois de naissance : les lettres sont utilisées par ordre alphabétique, mais seules les lettres A à E, H, L, M, P, R à T sont utilisées (donc, Janvier est A et Octobre est R)
- deux chiffres qui correspondent au jour du mois de naissance afin de différencier les sexes, 40 sont ajoutés au jour de naissance pour les femmes
- quatre chiffres qui correspondent à l’indicatif régional spécifique à la municipalité où la personne est née (les codes nationaux sont utilisés pour les pays étrangers)
- un chiffre de parité

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_italy_eu_national_id_card` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_italy_eu_national_id_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_italy_eu_national_id_card` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_italy_eu_national_id_card"></a>Keywords_italy_eu_national_id_card

- codice fiscal
- codice fiscale
- codice id personale
- codice personale
- code fiscal
- numero certificato personale
- numero di identificazione fiscale
- numero id personale
- nombreuses informations personnelles
- numéro de certificat personnel
- code personnel
- code d’ID personnel
- numéro d’ID personnel
- personalcodeno #
- code fiscal
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- numéro d’identité fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="italy-passport-number"></a>Numéro de passeport en Italie

### <a name="format"></a>Format

deux lettres ou chiffres suivis de sept chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

deux lettres ou chiffres suivis de sept chiffres :

- deux chiffres ou lettres (non sensibles à la casse)
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_italy_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_italy_eu_passport_number` est trouvé.
- L’expression `Regex_italy_eu_passport_date` régulière recherche la date au format DD MMM/MMM YYYY (exemple - 01 GEN/JAN 1988) ou un mot clé à partir de `Keywords_eu_passport_date` laquelle est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_italy_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_italy_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_italy_eu_passport_number"></a>Keywords_italy_eu_passport_number

- italiana passaporto
- passaporto italiana
- passaporto nombreux
- numéro passeport
- numero di passaporto
- numeri del passaporto
- passeport italien

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="italy-physical-addresses"></a>Adresses physiques en Italie

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique en provenance d’Italie. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="italy-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée en Italie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Modèle alphanumérique de 13 caractères avec délimiteurs facultatifs

### <a name="pattern"></a>Modèle

Modèle alphanumérique de 13 caractères avec délimiteurs facultatifs :

- I ou i
- T ou t
- espace facultatif, point, trait d’union ou virgule
- 11 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_italy_value_added_tax_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_italy_value_added_tax_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_italy_value_added_tax_number recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_italy_value_added_tax_number"></a>Keyword_italy_value_added_tax_number

- numéro de tva
- vat no
- Tva #
- Iva
- Iva #

## <a name="japan-bank-account-number"></a>Numéro de compte bancaire au Japon

### <a name="format"></a>Format

sept ou huit chiffres

### <a name="pattern"></a>Modèle

numéro de compte bancaire :

- sept ou huit chiffres
- code de branche de compte bancaire :

- quatre chiffres
- un espace ou un tiret (facultatif)
- trois chiffres

Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_jp_bank_account trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_bank_account est trouvé.
- L’une des affirmations suivantes est vraie :

- La fonction Func_jp_bank_account_branch_code trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_bank_branch_code est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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

## <a name="japan-drivers-license-number"></a>Numéro de permis de conduire au Japon

### <a name="format"></a>Format

12 chiffres

### <a name="pattern"></a>Modèle

12 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_jp_drivers_license_number"></a>Keyword_jp_drivers_license_number

- driverlicense
- driverslicense
- driver’slicense
- driverslicenses
- driver’slicenses
- driverlicenses
- Dl #
- Dls #
- Lic #
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

## <a name="japan-my-number---corporate"></a>Japan My Number - Entreprise

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Numéro à 13 chiffres

### <a name="pattern"></a>Modèle

Numéro à 13 chiffres :

- un chiffre de un à neuf
- 12 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_japanese_my_number_corporate recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_japanese_my_number_corporate est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_japanese_my_number_corporate recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

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

## <a name="japan-my-number---personal"></a>Japon Mon numéro - Personnel

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Numéro à 12 chiffres

### <a name="pattern"></a>Modèle

Numéro à 12 chiffres :

- quatre chiffres
- un espace, un point ou un trait d’union facultatif
- quatre chiffres
- un espace, un point ou un trait d’union facultatif
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_japanese_my_number_personal recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_japanese_my_number_personal est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_japanese_my_number_personal recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

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

## <a name="japan-passport-number"></a>Numéro de passeport au Japon

### <a name="format"></a>Format

deux lettres suivies de sept chiffres

### <a name="pattern"></a>Modèle

deux lettres (non sensibles à la casse) suivies de sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_jp_passport"></a>Keyword_jp_passport

- Passeport
- Numéro de passeport
- Passeport Non.
- # Passeport
- パスポート
- パスポート番号
- パスポートナンバー
- パスポート＃
- パスポート #
- パスポートNo.
- 旅券番号
- 旅券番号＃
- 旅券番号♯
- 旅券ナンバー

## <a name="japan-residence-card-number"></a>Numéro de carte de séjour au Japon

### <a name="format"></a>Format

12 lettres et chiffres

### <a name="pattern"></a>Modèle

12 lettres et chiffres :

- deux lettres (non sensibles à la casse)
- huit chiffres
- deux lettres (non sensibles à la casse)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Regex_jp_residence_card_number recherche du contenu qui correspond au modèle.
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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_jp_residence_card_number"></a>Keyword_jp_residence_card_number

- Numéro de carte de séjour
- Carte de séjour no
- Carte de séjour #
- 在留カード番号
- 在留カード
- 在留番号

## <a name="japan-resident-registration-number"></a>Numéro d’inscription des résidents du Japon

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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

## <a name="japan-social-insurance-number-sin"></a>Numéro d’assurance sociale au Japon (SIN)

### <a name="format"></a>Format

7 à 12 chiffres

### <a name="pattern"></a>Modèle

7 à 12 chiffres :

- quatre chiffres
- un trait d’union (facultatif)
- six chiffres OR
- 7 à 12 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_jp_sin trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_jp_sin est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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

## <a name="lab-test-terms"></a>Termes du test lab

Cette entité nommée non regroupée détecte les termes liés aux tests en laboratoire, tels que *l’insuline C-peptide*. Il prend uniquement en charge les termes anglais. Il est également inclus dans les [conditions générales médicales](#all-medical-terms-and-conditions) regroupées sous le nom d’entité SIT.

### <a name="confidence-level"></a>Niveau de confiance

Élevé

## <a name="latvia-drivers-license-number"></a>Numéro de permis de conduire letton

### <a name="format"></a>Format

trois lettres suivies de six chiffres

### <a name="pattern"></a>Modèle

trois lettres et six chiffres :

- trois lettres (non sensibles à la casse)
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_latvia_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_latvia_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
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

## <a name="latvia-passport-number"></a>Numéro de passeport letton

### <a name="format"></a>Format

deux lettres ou chiffres suivis de sept chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

deux lettres ou chiffres suivis de sept chiffres :

- deux chiffres ou lettres (non sensibles à la casse)
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_latvia_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_latvia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_latvia_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_latvia_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passeport #
- Passeport #
- passportid
- Passeports
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

- date du problème
- date d’expiration

## <a name="latvia-personal-code"></a>Code personnel letton

### <a name="format"></a>Format

11 chiffres et un trait d’union facultatif

### <a name="pattern"></a>Modèle

Ancien format

11 chiffres et un trait d’union :

- six chiffres qui correspondent à la date de naissance (DDMMYY)
- un trait d’union
- un chiffre qui correspond au siècle de naissance (« 0 » pour le 19ème siècle, « 1 » pour le 20ème siècle et « 2 » pour le 21ème siècle)
- quatre chiffres, générés de manière aléatoire

Nouveau format

11 chiffres

- Deux chiffres « 32 »
- Neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_latvia_eu_national_id_card` ou l’expression `Regex_latvia_eu_national_id_card_new_format` régulière recherche du contenu qui correspond au modèle.
- Un mot clé est `Keywords_latvia_eu_national_id_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_latvia_eu_national_id_card` ou l’expression `Regex_latvia_eu_national_id_card_new_format` régulière recherche du contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_latvia_eu_national_id_card"></a>Keywords_latvia_eu_national_id_card

- numéro d’administration
- alvas nē
- nombre de naissances
- numéro de citoyen
- numéro civil
- numéro de recensement électronique
- numéro électronique
- code fiscal
- numéro d’utilisateur de soins de santé
- Id #
- id-code
- numéro d’identification
- identifikācijas numurs
- id-number
- nombre individuel
- latvija alva
- nacionālais id
- id national
- numéro d’identification national
- numéro d’identité nationale
- numéro d’assurance nationale
- numéro de registre national
- nodokļa numurs
- nodokļu id
- nodokļu identifikācija numurs
- numéro de certificat personnel
- code personnel
- code d’ID personnel
- numéro d’ID personnel
- code d’identification personnelle
- identificateur personnel
- numéro d’identité personnelle
- numéro personnel
- code numérique personnel
- personalcodeno #
- personas kods
- code d’identification de la population
- numéro de service public
- numéro d’enregistrement
- numéro de chiffre d’affaires
- numéro d’assurance sociale
- numéro de sécurité sociale
- code fiscal d’état
- numéro de dossier fiscal
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #
- numéro de l’électeur

## <a name="latvia-physical-addresses"></a>Adresses physiques lettones

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique en provenance de Lettonie. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="liechtenstein-physical-addresses"></a>Adresses physiques du Liechtenstein

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique du Liechtenstein. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyenne

## <a name="lifestyles-that-relate-to-medical-conditions"></a>Modes de vie liés aux conditions médicales

Cette entité nommée non regroupée détecte les termes liés aux modes de vie qui peuvent entraîner une condition médicale, comme *le tabagisme*. Il prend uniquement en charge les termes anglais. Il est également inclus dans les [conditions générales médicales](#all-medical-terms-and-conditions) regroupées sous le nom d’entité SIT.

### <a name="confidence-level"></a>Niveau de confiance

Élevé

## <a name="lithuania-drivers-license-number"></a>Numéro de permis de conduire en Lituanie

### <a name="format"></a>Format

huit chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_lithuania_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_lithuania_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_lithuania_eu_drivers_license_number"></a>Keywords_lithuania_eu_driver s_license_number

- vairuotojo pažymėjimas
- vairuotojo pažymėjimo numeris
- vairuotojo pažymėjimo numeriai

## <a name="lithuania-personal-code"></a>Code personnel lituanien

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

11 chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

11 chiffres sans espaces et délimiteurs :

- un chiffre (1-6) qui correspond au sexe et au siècle de naissance de la personne
- six chiffres qui correspondent à la date de naissance (AAAAMMD)
- trois chiffres qui correspondent au numéro de série de la date de naissance
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_lithuania_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_lithuania_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_lithuania_eu_tax_file_number` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_lithuania_eu_national_id_card"></a>Keywords_lithuania_eu_national_id_card

- asmeninis skaitmeninis kodas
- asmens kodas
- numéro de service citoyen
- mokesčių id
- mokesčių identifikavimas numeris
- mokesčių identifikavimo numeris
- mokesčių numeris
- numéro d’identification nationale
- code personnel
- code numérique personnel
- piliečio paslaugos numeris
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #
- unikalus identifikavimo kodas
- unikalus identifikavimo numeris
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #

## <a name="lithuania-physical-addresses"></a>Adresses physiques lituaniennes

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique en provenance de Lituanie. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="lithuania-passport-number"></a>Numéro de passeport en Lituanie

### <a name="format"></a>Format

huit chiffres ou lettres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

huit chiffres ou lettres (non sensibles à la casse)

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_lithuania_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_lithuania_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date3` régulière recherche la date au format DD MM AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_lithuania_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_lithuania_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
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

- date du problème
- date d’expiration

## <a name="luxemburg-drivers-license-number"></a>Numéro de permis de conduire du Luxemburg

### <a name="format"></a>Format

six chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_luxemburg_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_luxemburg_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_luxemburg_eu_drivers_license_number"></a>Keywords_luxemburg_eu_driver s_license_number

- fahrerlaubnis
- Führerschäin

## <a name="luxemburg-national-identification-number-natural-persons"></a>Numéro d’identification national du Luxembourg (personnes physiques)

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

13 chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

13 chiffres :

- 11 chiffres
- deux chiffres de vérification

### <a name="checksum"></a>Somme de contrôle

oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_luxemburg_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_luxemburg_eu_national_id_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_luxemburg_eu_tax_file_number` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

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
- ID personnel
- identification personnelle
- identité personnelle
- personalidno #
- personalidnumber #
- persönliche identifikationsnummer
- ID unique
- identité unique
- uniqueidkey #

## <a name="luxemburg-national-identification-number-non-natural-persons"></a>Numéro d’identification national du Luxembourg (personnes non naturelles)

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
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_luxemburg_eu_tax_file_number_non_natural` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_luxemburg_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_luxemburg_eu_tax_file_number_non_natural` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_luxemburg_eu_tax_file_number"></a>Keywords_luxemburg_eu_tax_file_number

- carte de sécurité sociale
- non resserr
- resserr #
- identifiant d’impôt
- luxembourg tax identifikatiounsnummer
- numéro d’resser
- numéro d’identification fiscal luxembourgeois
- numéro d’identification fiscale
- sécurité sociale
- sozialunterstützung
- sozialversécherung
- sozialversicherungsausweis
- steier id
- steier identifikatiounsnummer
- steier nummer
- steuer id
- steueridentifikationsnummer
- steuernummer
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #
- Zinn #
- Zinn
- zinnzahl

## <a name="luxemburg-passport-number"></a>Numéro de passeport du Luxembourg

### <a name="format"></a>Format

huit chiffres ou lettres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

huit chiffres ou lettres (non sensibles à la casse)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_luxemburg_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_luxemburg_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date3` régulière recherche la date au format DD MM AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_luxemburg_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_luxemburg_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_luxemburg_eu_passport_number"></a>Keywords_luxemburg_eu_passport_number
- ausweisnummer
- luxembourg pass
- luxembourg passeport
- luxembourg passport
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

- date du problème
- date d’expiration

## <a name="luxemburg-physical-addresses"></a>Adresses physiques du Luxembourg

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique à partir de Luxemburg. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="malaysia-identification-card-number"></a>Numéro de carte d’identification en Malaisie

### <a name="format"></a>Format

12 chiffres contenant éventuellement des traits d’union

### <a name="pattern"></a>Modèle

12 chiffres :

- six chiffres au format YYMMDD, qui sont la date de naissance
- un tiret (facultatif)
- code de lieu de naissance à deux lettres
- un tiret (facultatif)
- trois chiffres aléatoires
- code de genre à un chiffre

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_malaysia_id_card_number"></a>Keyword_malaysia_id_card_number

- carte d’application numérique
- i/c
- i/c no
- Ic
- ic no
- carte d’identité
- carte d’identification
- Carte d’identité
- k/p
- k/p no
- kad akuan diri
- kad aplikasi digital
- kad pengenalan malaysia
- Kp
- kp no
- mykad
- mykas
- mykid
- mypr
- mytentera
- carte d’identité malaysia
- carte d’identité malaisienne
- nric
- carte d’identification personnelle

## <a name="malta-drivers-license-number"></a>Numéro de permis de conduire maltais

### <a name="format"></a>Format

Combinaison de deux caractères et de six chiffres dans le modèle spécifié

### <a name="pattern"></a>Modèle

combinaison de deux caractères et de six chiffres :

- deux caractères (chiffres ou lettres, non sensibles à la casse)
- un espace (facultatif)
- trois chiffres
- un espace (facultatif)
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_malta_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_malta_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_malta_eu_drivers_license_number"></a>Keywords_malta_eu_driver s_license_number

- liċenzja tas-sewqan
- liċenzji tas-sewwieq

## <a name="malta-identity-card-number"></a>Numéro de carte d’identité de Malte

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

sept chiffres suivis d’une lettre

### <a name="pattern"></a>Modèle

sept chiffres suivis d’une lettre :

- sept chiffres
- une lettre dans « M, G, A, P, L, H, B, Z » (ne respectant pas la casse)

### <a name="checksum"></a>Somme de contrôle

Non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_malta_eu_national_id_card` régulière recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_malta_eu_national_id_card` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_malta_eu_national_id_card` régulière recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_malta_eu_national_id_card"></a>Keywords_malta_eu_national_id_card

- numéro de service citoyen
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

## <a name="malta-passport-number"></a>Numéro de passeport maltais

### <a name="format"></a>Format

sept chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_malta_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_malta_eu_passport_number` est trouvé.
- Un mot clé à partir de `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_malta_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_malta_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_malta_eu_passport_number"></a>Keywords_malta_eu_passport_number

- numru tal-passaport
- numri tal-passaport
- Nru tal-passaport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="malta-physical-addresses"></a>Adresses physiques de Malte

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique de Malte. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="malta-tax-identification-number"></a>Numéro d’identification fiscale de Malte

### <a name="format"></a>Format

Pour les ressortissants maltais :

- sept chiffres et une lettre dans le modèle spécifié

Ressortissants non maltais et entités maltaises :

- neuf chiffres

### <a name="pattern"></a>Modèle

Ressortissants maltais : sept chiffres et une lettre

- sept chiffres
- une lettre (non sensible à la casse)

Ressortissants non maltais et entités maltaises : neuf chiffres

- neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_malta_eu_tax_file_number`  régulière ou `Regex_malta_eu_tax_file_number_non_maltese_national` recherche du contenu qui correspond au modèle.
- Un mot clé est `Keywords_malta_eu_tax_file_number` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_malta_eu_tax_file_number` régulière ou `Regex_malta_eu_tax_file_number_non_maltese_national` recherche du contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_malta_eu_tax_file_number"></a>Keywords_malta_eu_tax_file_number

- numéro de service citoyen
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
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #

## <a name="medical-specialities"></a>Spécialités médicales

Cette entité nommée non groupée détecte les termes liés aux spécialités médicales, telles que *la dermatologie*.  Il prend uniquement en charge les termes anglais. Il est également inclus dans les [conditions générales médicales](#all-medical-terms-and-conditions) regroupées sous le nom d’entité SIT.

### <a name="confidence-level"></a>Niveau de confiance

Élevé

## <a name="medicare-beneficiary-identifier-mbi-card"></a>Carte d’identificateur du bénéficiaire de l’assurance-maladie (MBI)

### <a name="format"></a>Format

Modèle alphanumérique à 11 caractères

### <a name="pattern"></a>Modèle

- un chiffre compris entre 1 et 9
- une lettre à l’exclusion de S, L, O, I, B, Z
- un chiffre ou une lettre à l’exclusion de S, L, O, I, B, Z
- un chiffre
- un trait d’union facultatif
- une lettre à l’exclusion de S, L, O, I, B, Z
- un chiffre ou une lettre à l’exclusion de S, L, O, I, B, Z
- un chiffre
- un trait d’union facultatif
- deux lettres à l’exclusion de S, L, O, I, B, Z
- deux chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_mbi_card` régulière recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_mbi_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_mbi_card` régulière recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_mbi_card"></a>Keyword_mbi_card

- Mbi
- Mbi #
- bénéficiaire de l’assurance-maladie #
- Identificateur du bénéficiaire de l’assurance-maladie
- bénéficiaire de l’assurance-maladie non
- numéro de bénéficiaire de l’assurance-maladie
- bénéficiaire de l’assurance-maladie #

## <a name="mexico-unique-population-registry-code-curp"></a>Code du Registre de la population unique du Mexique (CURP)

### <a name="format"></a>Format

Modèle alphanumérique à 18 caractères

### <a name="pattern"></a>Modèle

- quatre lettres (ne respectant pas la casse)
- six chiffres indiquant une date valide
- une lettre - H/h ou M/m
- deux lettres indiquant un code d’état mexicain valide
- trois lettres
- une lettre ou un chiffre
- un chiffre

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_mexico_population_registry_code` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_mexico_population_registry_code` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_mexico_population_registry_code` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_mexico_population_registry_code"></a>Keyword_mexico_population_registry_code

- Clave Única de Registro de Población
- Clave Unica de Registro de Poblacion
- Code unique du Registre de la population
- code de remplissage unique
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
- claveunica
- clavepersonalIdentidad

## <a name="netherlands-citizens-service-bsn-number"></a>Numéro de service du citoyen néerlandais (BSN)

### <a name="format"></a>Format

huit ou neuf chiffres contenant des espaces facultatifs

### <a name="pattern"></a>Modèle

huit-neuf chiffres :

- trois chiffres
- un espace (facultatif)
- trois chiffres
- un espace (facultatif)
- deux-trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_netherlands_eu_national_id_card"></a>Keywords_netherlands_eu_national_id_card

- Bsn #
- Bsn
- burgerservicenummer
- numéro de service citoyen
- numéro de personne
- numéro personnel
- code numérique personnel
- numéro lié à la personne
- persoonlijk nummer
- persoonlijke numerieke code
- persoonsgebonden
- persoonsnummer
- sociaal-fiscaal nummer
- numéro social-fiscal
- Sofi
- sofinummer
- uniek identificatienummer
- uniek identiteitsnummer
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #

## <a name="netherlands-drivers-license-number"></a>Numéro de permis de conduire aux Pays-Bas

### <a name="format"></a>Format

10 chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

10 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_netherlands_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_netherlands_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_netherlands_eu_drivers_license_number"></a>Keywords_netherlands_eu_driver s_license_number

- permis de conduire
- rijbewijs
- rijbewijsnummer
- rijbewijzen
- rijbewijs nummer
- rijbewijsnummers

## <a name="netherlands-passport-number"></a>Numéro de passeport des Pays-Bas

### <a name="format"></a>Format

neuf lettres ou chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

neuf lettres ou chiffres

### <a name="checksum"></a>Somme de contrôle

non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_netherlands_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_netherlands_eu_passport_number` est trouvé.
- L’expression `Regex_netherlands_eu_passport_date` régulière trouve la date au format DD MMM/MMM AAAA (exemple - 26 MAA/MAR 2012)

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_netherlands_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_netherlands_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_netherlands_eu_passport_number"></a>Keywords_netherlands_eu_passport_number

- paspoort nummer
- paspoortnummers
- paspoortnummer
- paspoort nr

## <a name="netherlands-physical-addresses"></a>Adresses physiques des Pays-Bas

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique des Pays-Bas. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="netherlands-tax-identification-number"></a>Numéro d’identification fiscale aux Pays-Bas

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

neuf chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_netherlands_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_netherlands_eu_tax_file_number` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_netherlands_eu_tax_file_number` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_netherlands_eu_tax_file_number"></a>Keywords_netherlands_eu_tax_file_number

- btw nummer
- hollânske identification fiscale
- hulandes impuesto id number
- hulandes impuesto identification
- identificatienummer belasting
- identificatienummer van belasting
- numéro d’identification impuesto
- impuesto number
- nederlands belasting id nummer
- nederlands belasting identificatie
- nederlands belasting identificatienummer
- nederlands belastingnummer
- nederlandse belasting identificatie
- identification fiscale aux Pays-Bas
- l’identification fiscale de netherland
- boîte pays-bas
- netherland’s tin
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax identification tal
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- tax tal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="netherlands-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée aux Pays-Bas

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Modèle alphanumérique à 14 caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique à 14 caractères :

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_netherlands_value_added_tax_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_netherlands_value_added_tax_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_netherlands_value_added_tax_number recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_netherlands_value_added_tax_number"></a>Keyword_netherlands_value_added_tax_number

- numéro de tva
- vat no
- Tva #
- wearde tafoege tax getal
- btw nûmer
- btw-nummer

## <a name="new-zealand-bank-account-number"></a>Numéro de compte bancaire en Nouvelle-Zélande

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Modèle à 14 chiffres à 16 chiffres avec délimiteur facultatif

### <a name="pattern"></a>Modèle

Modèle à 14 chiffres à 16 chiffres avec délimiteur facultatif :

- deux chiffres
- un trait d’union ou un espace facultatif
- trois à quatre chiffres
- un trait d’union ou un espace facultatif
- sept chiffres
- un trait d’union ou un espace facultatif
- deux à trois chiffres
- un trait d’union ou un espace d’options

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_new_zealand_bank_account_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_new_zealand_bank_account_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_new_zealand_bank_account_number recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_new_zealand_bank_account_number"></a>Keyword_new_zealand_bank_account_number

- numéro de compte
- compte bancaire
- bank_acct_id
- bank_acct_branch
- bank_acct_nbr

## <a name="new-zealand-drivers-license-number"></a>Numéro de permis de conduire en Nouvelle-Zélande

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

modèle alphanumérique à huit caractères

### <a name="pattern"></a>Modèle

modèle alphanumérique à huit caractères

- deux lettres
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_newzealand_driver_license_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_newzealand_driver_license_number est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_newzealand_driver_license_number recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

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
- driver' lic
- driver' lics
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicence
- driver’slicences
- driver’s lic
- driver’s lics
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
- driver' lic #
- driver' lics #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicence #
- driver’slicences #
- driver’s lic #
- driver’s lics #
- permis de conduire #
- permis de conduire #
- permis de conduite international
- permis de conduite internationaux
- nz automobile association
- Association automobile néo-zélandaise

## <a name="new-zealand-inland-revenue-number"></a>Chiffre d’affaires intérieur de la Nouvelle-Zélande

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

huit ou neuf chiffres avec délimiteurs facultatifs

### <a name="pattern"></a>Modèle

huit ou neuf chiffres avec délimiteurs facultatifs

- deux ou trois chiffres
- un espace ou un trait d’union facultatif
- trois chiffres
- un espace ou un trait d’union facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_new_zealand_inland_revenue_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_new_zealand_inland_revenue_number est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_new_zealand_inland_revenue_number recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_new_zealand_inland_revenue_number"></a>Keyword_new_zealand_inland_revenue_number

- ird no.
- ird no #
- nz ird
- nouvelle zélande ird
- ird number
- chiffre d’affaires intérieur

## <a name="new-zealand-ministry-of-health-number"></a>Numéro de ministère de la Santé de Nouvelle-Zélande

### <a name="format"></a>Format

trois lettres et quatre chiffres

### <a name="pattern"></a>Modèle

- trois lettres (non sensibles à la casse) à l’exception de « I » et « O »
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_new_zealand_ministry_of_health_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_nz_terms est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_nz_terms"></a>Keyword_nz_terms

- NHI
- Nouvelle-Zélande
- National Health Index
- NHI #
- National Health Index #

## <a name="new-zealand-physical-addresses"></a>Adresses physiques néo-zélandaises

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique de la Nouvelle-Zélande. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="new-zealand-social-welfare-number"></a>Numéro de l’aide sociale en Nouvelle-Zélande

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_newzealand_social_welfare_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_newzealand_social_welfare_number est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_newzealand_social_welfare_number recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_new_zealand_social_welfare_number"></a>Keyword_new_zealand_social_welfare_number

- Sociale #
- Sociale #
- bien-être social Non.
- numéro de bien-être social
- swn #

## <a name="norway-identification-number"></a>Numéro d’identification de la Norvège

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres :

- six chiffres au format DDMMYY, qui sont la date de naissance
- Nombre individuel à trois chiffres
- deux chiffres de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_norway_id_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_norway_id_number est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_norway_id_number"></a>Keyword_norway_id_number

- Personal identification number
- Norwegian ID Number
- ID Number
- Identification
- Personneur
- Fødselsnummer

## <a name="norway-physical-addresses"></a>Adresses physiques en Norvège

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique à partir de la Norvège. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="philippines-unified-multi-purpose-identification-number"></a>Numéro d’identification multi-usage unifié aux Philippines

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

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_philippines_id"></a>Keyword_philippines_id

- Unified Multi-Purpose ID
- UMID
- Identity Card
- Pinag-isang Multi-Layunin ID

## <a name="poland-drivers-license-number"></a>Numéro de permis de conduire en Pologne

### <a name="format"></a>Format

14 chiffres contenant deux barres obliques

### <a name="pattern"></a>Modèle

14 chiffres et deux barres obliques :

- cinq chiffres
- une barre oblique
- deux chiffres
- une barre oblique
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_poland_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_poland_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_poland_eu_drivers_license_number"></a>Keywords_poland_eu_driver s_license_number

- prawo jazdy
- prawa jazdy

## <a name="poland-identity-card"></a>Carte d’identité polonaise

### <a name="format"></a>Format

trois lettres et six chiffres

### <a name="pattern"></a>Modèle

trois lettres (non sensibles à la casse) suivies de six chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_poland_national_id_passport_number"></a>Keyword_poland_national_id_passport_number

- Dowód osobisty
- Numer dowodu osobistego
- Nazwa i numer dowodu osobistego
- Nazwa i nr dowodu osobistego
- Nazwa je nr dowodu tożsamości
- Dowód Tożsamości
- Dow. Os.

## <a name="poland-national-id-pesel"></a>ID national polonais (PESEL)

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

- six chiffres représentant la date de naissance au format YYMMDD
- quatre chiffres
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_pesel_identification_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_pesel_identification_number est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_pesel_identification_number"></a>Keyword_pesel_identification_number

- dowód osobisty
- dowódosobisty
- niepowtarzalny numer
- niepowtarzalnynumer
- nr.-pesel
- nr-pesel
- numer identyfikacyjny
- pesel
- tożsamości narodowej

## <a name="poland-passport-number"></a>Numéro de passeport en Pologne

Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles numéro de passeport de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

deux lettres et sept chiffres

### <a name="pattern"></a>Modèle

Deux lettres (non sensibles à la casse) suivies de sept chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_polish_passport_number_v2` recherche le contenu qui correspond au modèle.
- La somme de contrôle est correcte.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keyword_polish_national_passport_number` est trouvé.
- Un mot clé est `Keywords_eu_passport_date` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_polish_passport_number_v2` recherche le contenu qui correspond au modèle.
- La somme de contrôle est correcte.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keyword_polish_national_passport_number` est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_polish_passport_number_v2` recherche le contenu qui correspond au modèle.
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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
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
- Nr. paszportu
- nr paszportów
- n° passeport
- passeport n°

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="poland-physical-addresses"></a>Adresses physiques en Pologne

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique de la Pologne. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="poland-regon-number"></a>Numéro REGON de Pologne

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

9 chiffres ou 14 chiffres

### <a name="pattern"></a>Modèle

neuf chiffres ou 14 chiffres :

- neuf chiffres ou
- neuf chiffres
- Tiret
- cinq chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_polish_regon_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_polish_regon_number est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_polish_regon_number recherche le contenu qui correspond au modèle.

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
### <a name="keywords"></a>Mots-clés

#### <a name="keywords_poland_regon_number"></a>Keywords_poland_regon_number

- regon id
- nombre statistique
- ID statistique
- statistiques non
- regon number
- regonid #
- regonno #
- ID d’entreprise
- companyid #
- companyidno #
- numer statystyczny
- numeru regon
- numerstatystyczny #
- numeruregon #

## <a name="poland-tax-identification-number"></a>Numéro d’identification fiscale en Pologne

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

11 chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

11 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_poland_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_poland_eu_tax_file_number` trouvé.

```xml
      <!-- Poland Tax Identification Number -->
      <Entity id="1ff28b4d-40f2-49e9-b677-9606a88e2bca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_poland_eu_tax_file_number" />
          <Match idRef="Keywords_poland_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_poland_eu_tax_file_number"></a>Keywords_poland_eu_tax_file_number

- nip #
- nip
- numer identyfikacji podatkowej
- numeridentyfikacjipodatkowej #
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #
- vat id #
- vat id
- vat no
- numéro de tva
- vatid #
- vatid
- vatno #

## <a name="portugal-citizen-card-number"></a>Numéro de carte de citoyen du Portugal

### <a name="format"></a>Format

huit chiffres

### <a name="pattern"></a>Modèle

huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_portugal_citizen_card"></a>Keyword_portugal_citizen_card

- bilhete de identidade
- cartão de cidadão
- carte de citoyen
- numéro de document
- documento de identificação
- numéro d’ID
- identification no
- numéro d’identification
- identity card no
- numéro de carte d’identité
- carte d’identité nationale
- Nic
- número bi de portugal
- número de identificação civil
- número de identificação fiscal
- número do documento
- portugal bi number

## <a name="portugal-drivers-license-number"></a>Numéro de permis de conduire au Portugal

### <a name="format"></a>Format

deux modèles : deux lettres suivies de 5 à 8 chiffres avec des caractères spéciaux

### <a name="pattern"></a>Modèle

Modèle 1 : Deux lettres suivies de 5/6 avec des caractères spéciaux :

- Deux lettres (non sensibles à la casse)
- Un trait d’union 
- Cinq ou six chiffres
- Un espace
- Un chiffre

Modèle 2 : Une lettre suivie de 6/8 chiffres avec des caractères spéciaux :

- Une lettre (non sensible à la casse)
- Un trait d’union 
- Six ou huit chiffres
- Un espace
- Un chiffre

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_portugal_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_portugal_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_portugal_eu_drivers_license_number"></a>Keywords_portugal_eu_driver s_license_number

- carteira de motorista
- carteira motorista
- carteira de habilitação
- carteira habilitação
- número de licença
- número licença
- permissão de condução
- permissão condução
- Licença condução Portugal
- carta de condução

## <a name="portugal-passport-number"></a>Numéro de passeport du Portugal

### <a name="format"></a>Format

une lettre suivie de six chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

une lettre suivie de six chiffres :

- une lettre (non sensible à la casse)
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_portugal_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_portugal_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_portugal_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_portugal_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_portugal_eu_passport_number"></a>Keywords_portugal_eu_passport_number

- número do passaporte
- passeport portugais
- passeport portugais
- portugais passaporte
- passaporte nº
- passeport nº
- números de passaporte
- passeports portugais
- número passaporte
- números passaporte

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="portugal-physical-addresses"></a>Adresses physiques du Portugal

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique du Portugal. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="portugal-tax-identification-number"></a>Numéro d’identification fiscale du Portugal

### <a name="format"></a>Format

neuf chiffres avec des espaces facultatifs

### <a name="pattern"></a>Modèle

- trois chiffres
- un espace facultatif
- trois chiffres
- un espace facultatif
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_portugal_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_portugal_eu_tax_file_number` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_portugal_eu_tax_file_number` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_portugal_eu_tax_file_number"></a>Keywords_portugal_eu_tax_file_number

- Cpf #
- Cpf
- Nif #
- Nif
- número de identificação fisca
- nombreuses
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="romania-drivers-license-number"></a>Numéro de permis de conduire en Roumanie

### <a name="format"></a>Format

un caractère suivi de huit chiffres

### <a name="pattern"></a>Modèle

un caractère suivi de huit chiffres :

- une lettre (non sensible à la casse) ou un chiffre
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_romania_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_romania_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_romania_eu_drivers_license_number"></a>Keywords_romania_eu_driver s_license_number

- permis de conducere
- permisului de conducere
- permisului conducere
- permisele de conducere
- permisele conducere
- permis conducere

## <a name="romania-passport-number"></a>Numéro de passeport en Roumanie

### <a name="format"></a>Format

huit ou neuf chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

huit ou neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_romania_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_romania_eu_passport_number` est trouvé.
- L’expression `Regex_romania_eu_passport_date` régulière recherche la date au format DD MMM/MMM YY (exemple - 01 FEB/FEB 10) ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_romania_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_romania_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_romania_eu_passport_number"></a>Keywords_romania_eu_passport_number

numărul pașaportului numarul pasaportului numerele pașaportului Pașaport nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="romania-personal-numeric-code-cnp"></a>Code numérique personnel (CNP) en Roumanie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

13 chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

- un chiffre de 1 à 9
- six chiffres représentant la date de naissance (AAAAMMD)
- deux chiffres, qui peuvent être 01-52 ou 99
- quatre chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_romania_eu_national_id_card` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_romania_eu_national_id_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_romania_eu_national_id_card` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_romania_eu_national_id_card"></a>Keywords_romania_eu_national_id_card

- cnp #
- cnp
- cod identificare personnel
- cod numeric personal
- cod unic identificare
- codnumericpersonal #
- codul fiscal nr.
- identificarea fiscală nr #
- id-ul taxei
- numéro d’assurance
- insurancenumber #
- ID national #
- id national
- numéro d’identification nationale
- număr identificare personnel
- număr identitate
- număr personal unic
- număridentitate #
- număridentitate
- numărpersonalunic #
- numărpersonalunic
- număru de identificare fiscală
- numărul de identificare fiscală
- code numérique personnel
- épingler #
- épingler
- fichier fiscal no
- numéro de dossier fiscal
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #
- uniqueidentityno

## <a name="romania-physical-addresses"></a>Adresses physiques roumaines

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique en provenance de Roumanie. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="russia-passport-number-domestic"></a>Numéro de passeport russe national

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Nombre à 10 chiffres

### <a name="pattern"></a>Modèle

Nombre à 10 chiffres :

- deux chiffres
- un espace ou un trait d’union facultatif
- deux chiffres
- un espace facultatif
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- Le Regex_Russian_Passport_Number_Domestic regex recherche le contenu qui correspond au modèle.
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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_russia_passport_number_domestic"></a>Keyword_russia_passport_number_domestic

- numéro de passeport
- passport no
- Passeport #
- iD passport
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

## <a name="russia-passport-number-international"></a>Numéro de passeport international de la Russie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

numéro à neuf chiffres

### <a name="pattern"></a>Modèle

Nombre à neuf chiffres :

- deux chiffres
- un espace ou un trait d’union facultatif
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- Le Regex_Russian_Passport_Number_International regex recherche le contenu qui correspond au modèle.
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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_russia_passport_number_international"></a>Keywords_russia_passport_number_international

- numéro de passeport
- passport no
- Passeport #
- iD passport
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

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_saudi_arabia_national_id"></a>Keyword_saudi_arabia_national_id

- Carte d’identification
- numéro de carte d’identité
- Numéro d’identification
- الوطنية الهوية بطاقة رقم

## <a name="singapore-national-registration-identity-card-nric-number"></a>Numéro de carte d’identité d’inscription nationale (NRIC) de Singapour

### <a name="format"></a>Format

neuf lettres et chiffres

### <a name="pattern"></a>Modèle

- neuf lettres et chiffres :

- la lettre « F », « G », « M », « S » ou « T » (non sensible à la casse)
- sept chiffres
- un chiffre à cocher alphabétique

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Regex_singapore_nric trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_singapore_nric est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_singapore_nric"></a>Keyword_singapore_nric

- National Registration Identity Card
- Identity Card Number
- NRIC
- IC
- Foreign Identification Number
- FIN
- 身份证
- 身份證

## <a name="slovakia-drivers-license-number"></a>Numéro de permis de conduire en Slovaquie

### <a name="format"></a>Format

un caractère suivi de sept chiffres

### <a name="pattern"></a>Modèle

un caractère suivi de sept chiffres

- une lettre (non sensible à la casse) ou un chiffre
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_slovakia_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_slovakia_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_slovakia_eu_drivers_license_number"></a>Keywords_slovakia_eu_driver s_license_number

- vodičský preukaz
- vodičské preukazy
- vodičského preukazu
- vodičských preukazov

## <a name="slovakia-passport-number"></a>Numéro de passeport en Slovaquie

### <a name="format"></a>Format

modèle alphanumérique de huit ou neuf caractères

### <a name="pattern"></a>Modèle

une lettre (non sensible à la casse) suivie de sept chiffres ou deux lettres (non sensibles à la casse) suivies de six ou sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_slovakia_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_slovakia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_slovakia_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_slovakia_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
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

- date du problème
- date d’expiration

## <a name="slovakia-personal-number"></a>Numéro personnel en Slovaquie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_slovakia_eu_national_id_card` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_slovakia_eu_national_id_card` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_slovakia_eu_national_id_card` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_slovakia_eu_national_id_card"></a>Keywords_slovakia_eu_national_id_card

- azonosító szám
- nombre de naissances
- číslo národnej identifikačnej karty
- číslo občianského preukazu
- daňové číslo
- numéro d’ID
- identification no
- numéro d’identification
- identifikačná karta č
- identifikačné číslo
- identity card no
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
- Ssn #
- Ssn
- személyi igazolvány szám
- személyi igazolvány száma
- személyigazolvány szám
- fichier fiscal no
- numéro de dossier fiscal
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="slovakia-physical-addresses"></a>Adresses physiques en Slovaquie

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique en provenance de Slovaquie. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="slovenia-drivers-license-number"></a>Numéro de permis de conduire en Slovénie

### <a name="format"></a>Format

neuf chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_slovenia_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_slovenia_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_slovenia_eu_drivers_license_number"></a>Keywords_slovenia_eu_driver s_license_number

- vozniško dovoljenje
- vozniška številka licence
- vozniških dovoljenj
- številka vozniškega dovoljenja
- številke vozniških dovoljenj

## <a name="slovenia-passport-number"></a>Numéro de passeport en Slovénie

### <a name="format"></a>Format

deux lettres suivies de sept chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

deux lettres suivies de sept chiffres :

- la lettre « P »
- une lettre majuscule
- sept chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_slovenia_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_slovenia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_slovenia_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_slovenia_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
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

- date du problème
- date d’expiration

## <a name="slovenia-physical-addresses"></a>Adresses physiques slovènes

Cette entité nommée non regroupée détecte les modèles liés à l’adresse physique de la Slovénie. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="slovenia-tax-identification-number"></a>Numéro d’identification fiscale en Slovénie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

huit chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

- un chiffre de 1 à 9
- six chiffres
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_slovenia_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_slovenia_eu_tax_file_number` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_slovenia_eu_tax_file_number` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_slovenia_eu_tax_file_number"></a>Keywords_slovenia_eu_tax_file_number

- davčna številka
- identifikacijska številka davka
- številka davčne datoteke
- fichier fiscal no
- numéro de dossier fiscal
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="slovenia-unique-master-citizen-number"></a>Slovénie Unique Master Citizen Number

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

13 chiffres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

13 chiffres dans le modèle spécifié :

- sept chiffres qui correspondent à la date de naissance (DDMMLLL) où « LLL » correspond aux trois derniers chiffres de l’année de naissance
- deux chiffres qui correspondent à la zone de naissance « 50 »
- trois chiffres qui correspondent à une combinaison de sexe et de numéro de série pour les personnes nées le même jour. 000-499 pour les hommes et 500-999 pour les femmes.
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_slovenia_eu_national_id_card` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_slovenia_eu_national_id_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_slovenia_eu_national_id_card` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_slovenia_eu_national_id_card"></a>Keywords_slovenia_eu_national_id_card

- edinstvena številka glavnega državljana
- emšo
- enotna maticna številka obcana
- carte d’identité
- numéro d’identification
- identifikacijska številka
- Carte d’identité
- id de la nacionalna
- list nacionalni potni
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

## <a name="south-africa-identification-number"></a>Numéro d’identification de l’Afrique du Sud

### <a name="format"></a>Format

13 chiffres pouvant contenir des espaces

### <a name="pattern"></a>Modèle

13 chiffres :

- six chiffres au format YYMMDD, qui sont la date de naissance
- quatre chiffres
- un indicateur de citoyenneté à un chiffre
- le chiffre « 8 » ou « 9 »
- un chiffre, qui est un chiffre de somme de contrôle

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_south_africa_identification_number"></a>Keyword_south_africa_identification_number

- Identity card
- ID
- Identification

## <a name="south-korea-resident-registration-number"></a>Numéro d’inscription des résidents sud-coréens

### <a name="format"></a>Format

13 chiffres contenant un trait d’union

### <a name="pattern"></a>Modèle

13 chiffres :

- six chiffres au format YYMMDD, qui sont la date de naissance
- un trait d’union
- un chiffre déterminé par le siècle et le sexe
- Code de région de naissance à quatre chiffres
- un chiffre utilisé pour différencier les personnes pour lesquelles les nombres précédents sont identiques
- un chiffre à cocher.

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_south_korea_resident_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_south_korea_resident_number est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- National ID card
- Citizen’s Registration Number
- Jumin deungnok beonho
- RRN
- 주민등록번호

## <a name="spain-dni"></a>Espagne DNI

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

huit chiffres suivis d’un caractère

### <a name="pattern"></a>Modèle

sept chiffres suivis d’un caractère

- huit chiffres
- Espace ou trait d’union facultatif
- une lettre de vérification (non sensible à la casse)

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- `Func_spain_eu_DL_and_NI_number_citizen` Fonction ou `Func_spain_eu_DL_and_NI_number_foreigner` recherche du contenu qui correspond au modèle.
- Un mot clé est `Keywords_spain_eu_national_id_card"` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- `Func_spain_eu_DL_and_NI_number_citizen` Fonction ou `Func_spain_eu_DL_and_NI_number_foreigner` recherche du contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_spain_eu_national_id_card"></a>Keywords_spain_eu_national_id_card

- carné de identidad
- Dni #
- Dni
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
- numéro d’identification personnelle
- identité personnelle non
- numéro d’identité unique
- Uniqueid #

## <a name="spain-drivers-license-number"></a>Numéro de permis de conduire en Espagne

### <a name="format"></a>Format

huit chiffres suivis d’un caractère

### <a name="pattern"></a>Modèle

huit chiffres suivis d’un caractère :

- huit chiffres
- un chiffre ou une lettre (non sensible à la casse)

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- `Func_spain_eu_DL_and_NI_number_citizen` Fonction ou `Func_spain_eu_DL_and_NI_number_foreigner` recherche du contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_spain_eu_driver's_license_number` est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- `Func_spain_eu_DL_and_NI_number_citizen` Fonction ou `Func_spain_eu_DL_and_NI_number_foreigner` recherche du contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_spain_eu_drivers_license_number"></a>Keywords_spain_eu_driver s_license_number

- permiso de conducción
- permiso conducción
- licencia de conducir
- licencia conducir
- permiso conducir
- permiso de conducir
- permisos de conducir
- permisos conducir
- carnet favorable
- carnet de conducir
- licencia de manejo
- licencia manejo

## <a name="spain-passport-number"></a>Numéro de passeport en Espagne

### <a name="format"></a>Format

une combinaison de huit ou neuf caractères de lettres et de nombres sans espaces ni délimiteurs

### <a name="pattern"></a>Modèle

une combinaison de lettres et de chiffres de huit ou neuf caractères :

- deux chiffres ou lettres
- un chiffre ou une lettre (facultatif)
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non applicable

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_spain_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_spain_eu_passport_number` est trouvé.
- L’expression `Regex_spain_eu_passport_date` régulière recherche la date au format DD-MM-AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_spain_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_spain_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
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
- pasaporte non.
- pasaporte n°
- passeport espagne

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="spain-physical-addresses"></a>Adresses physiques en Espagne

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique en provenance d’Espagne. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="spain-social-security-number-ssn"></a>Numéro de sécurité sociale en Espagne (SSN)

### <a name="format"></a>Format

11 à 12 chiffres

### <a name="pattern"></a>Modèle

11 à 12 chiffres :

- deux chiffres
- une barre oblique (facultatif)
- sept à huit chiffres
- une barre oblique (facultatif)
- deux chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_spanish_social_security_number trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.
- - Un mot clé est `Keywords_spain_eu_ssn_or_equivalent` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- Ssn
- Ssn #
- socialsecurityno
- sécurité sociale non
- numéro de sécurité sociale
- número de la seguridad social

## <a name="spain-tax-identification-number"></a>Numéro d’identification fiscale en Espagne

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

sept ou huit chiffres et une ou deux lettres dans le modèle spécifié

### <a name="pattern"></a>Modèle

Personnes physiques espagnoles avec une carte d’identité nationale d’Espagne :

- huit chiffres
- une lettre majuscule (respect de la casse)

Espagnols non résidents sans carte d’identité nationale d’Espagne

- une lettre majuscule « L » (respect de la casse)
- sept chiffres
- une lettre majuscule (respect de la casse)

Résidents espagnols âgés de moins de 14 ans sans carte d’identité nationale d’Espagne :

- une lettre majuscule « K » (respect de la casse)
- sept chiffres
- une lettre majuscule (respect de la casse)

Étrangers avec le numéro d’identification d’un étranger

- une lettre majuscule qui est « X », « Y » ou « Z » (respectant la casse)
- sept chiffres
- une lettre majuscule (respect de la casse)

Étrangers sans numéro d’identification d’étranger

- une lettre majuscule qui est « M » (respect de la casse)
- sept chiffres
- une lettre majuscule (respect de la casse)

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- `Func_spain_eu_tax_file_number` Fonction ou `Func_spain_eu_DL_and_NI_number_citizen` recherche du contenu qui correspond au modèle.
- Un mot clé est `Keywords_spain_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- `Func_spain_eu_tax_file_number` Fonction ou `Func_spain_eu_DL_and_NI_number_citizen` recherche du contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_spain_eu_tax_file_number"></a>Keywords_spain_eu_tax_file_number

- Caf
- cifid #
- cifnúmero #
- número de contribuyente
- número de identificación fiscal
- número de impuesto corporativo
- spanishcifid #
- spanishcifid
- spanishcifno #
- spanishcifno
- fichier fiscal no
- numéro de dossier fiscal
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="sql-server-connection-string"></a>chaîne de connexion SQL Server

### <a name="format"></a>Format

Chaîne « ID d’utilisateur », « ID utilisateur », « uid » ou « UserId », suivie des caractères et des chaînes décrits dans le modèle ci-dessous.

### <a name="pattern"></a>Modèle

- la chaîne « ID utilisateur », « ID utilisateur », « uid » ou « UserId »
- toute combinaison d’entre 1 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- chaîne « Password » ou « pwd » où « pwd » n’est pas précédé d’une lettre minuscule
- un signe égal (=)
- tout caractère qui n’est pas un signe dollar ($), un symbole de pourcentage (%), supérieur au symbole (>), au symbole (@), au guillemet (« ), au point-virgule (;), accolade gauche([) ou crochet gauche ({)
- toute combinaison de 7 à 128 caractères qui ne sont pas un point-virgule (;), barre oblique (/) ou guillemet (« )
- point-virgule (;) ou guillemet (« )

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière CEP_Regex_SQLServerConnectionString recherche du contenu qui correspond au modèle.
- Un mot clé de CEP_GlobalFilter est introuvable.
- L’expression régulière CEP_PasswordPlaceHolder ne trouve pas de contenu correspondant au modèle.
- L’expression régulière CEP_CommonExampleKeywords ne trouve pas de contenu correspondant au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="cep_globalfilter"></a>CEP_GlobalFilter

- certains mots de passe
- somepassword
- secretPassword
- Échantillon

#### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

Ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.

- Mot de passe ou pwd suivi de 0-2 espaces, d’un signe égal (=), de 0 à 2 espaces et d’un astérisque (*) -OR-
- Mot de passe ou pwd suivi de :
    - Un signe égal (=)
    - Symbole inférieur à (<)
    - Toute combinaison de 1 à 200 caractères qui sont des lettres majuscules ou minuscules, des chiffres, un astérisque (*), un trait d’union (-), un trait d’union (_), un trait de soulignement (_) ou un caractère d’espace blanc
    - Supérieur au symbole (>)

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

Ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="surgical-procedures"></a>Interventions chirurgicales

Cette entité nommée non regroupée détecte les termes liés aux procédures chirurgicales, telles que *l’appendectomie*.  Il prend uniquement en charge les termes anglais. Il est également inclus dans les [conditions générales médicales](#all-medical-terms-and-conditions) regroupées sous le nom d’entité SIT.

### <a name="confidence-level"></a>Niveau de confiance

Élevé

## <a name="sweden-drivers-license-number"></a>Numéro de permis de conduire en Suède

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

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_sweden_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_sweden_eu_driver's_license_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

#### <a name="keywords_sweden_eu_drivers_license_number"></a>Keywords_sweden_eu_driver s_license_number

- ajokortti
- permis de conducere
- ajokortin nombreux
- kuljettajat lic.
- drivere lic.
- körkort
- numărul permisului de conducere
- שאָפער דערלויבעניש נומער
- förare lic.
- דריווערס דערלויבעניש
- körkortsnummer

## <a name="sweden-national-id"></a>ID national de la Suède

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_swedish_national_identifier` recherche le contenu qui correspond au modèle.
- Un mot clé à partir de `Keywords_swedish_national_identifier` est trouvé
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_swedish_national_identifier` recherche le contenu qui correspond au modèle.
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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_swedish_national_identifier"></a>Keywords_swedish_national_identifier

- id no
- numéro d’ID
- Id #
- identification no
- numéro d’identification
- identifikationsnumret #
- identifikationsnumret
- identitetshandling
- document d’identité
- identity no
- numéro d’identité
- id-nummer
- ID personnel
- personnummer #
- personnummer
- skatteidentifikationsnummer

## <a name="sweden-passport-number"></a>Numéro de passeport en Suède

### <a name="format"></a>Format

huit chiffres

### <a name="pattern"></a>Modèle

huit chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- l’expression régulière Regex_sweden_passport_number recherche le contenu qui correspond au modèle.
- un mot clé à partir ou `Keywords_eu_passport_number` `Keyword_sweden_passport` est trouvé.
- l’expression `Regex_sweden_eu_passport_date` régulière trouve une date au format DD MMM/MMM YY (01 JAN/JAN 12) ou un mot clé `Keywords_eu_passport_date` est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- l’expression régulière Regex_sweden_passport_number recherche le contenu qui correspond au modèle.
- un mot clé à partir ou `Keywords_eu_passport_number` `Keyword_sweden_passport` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- carte d’inscription alien
- Frais de traitement g3
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
- visa schengen
- visas schengen
- entrée unique
- passe sverige
- exigences en matière de visa
- traitement des visas
- type de visa

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration

## <a name="sweden-physical-addresses"></a>Adresses physiques en Suède

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique de la Suède. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="sweden-tax-identification-number"></a>Numéro d’identification fiscale en Suède

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

10 chiffres et un symbole dans le modèle spécifié

### <a name="pattern"></a>Modèle

10 chiffres et un symbole :

- six chiffres qui correspondent à la date de naissance (AAAAMMD)
- signe plus ou signe moins
- trois chiffres qui rendent le numéro d’identification unique où :
  - pour les nombres émis avant 1990, les septième et huitième chiffres identifient le comté de naissance ou les personnes nées à l’étranger
  - le chiffre à la neuvième position indique le sexe par impair pour les hommes ou même pour les femmes
- un chiffre de vérification

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_sweden_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_sweden_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_sweden_eu_tax_file_number` recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_sweden_eu_tax_file_number"></a>Keywords_sweden_eu_tax_file_number

- numéro d’ID personnel
- personnummer
- skatt id nummer
- skatt identifikation
- skattebetalarens identifikationsnummer
- sverige tin
- fichier fiscal
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="swift-code"></a>Code SWIFT

### <a name="format"></a>Format

quatre lettres suivies de 5 à 31 lettres ou chiffres

### <a name="pattern"></a>Modèle

quatre lettres suivies de 5 à 31 lettres ou chiffres :

- Code bancaire à quatre lettres (non sensible à la casse)
- un espace facultatif
- 4 à 28 lettres ou chiffres (numéro de compte bancaire de base (BBAN))
- un espace facultatif
- une à trois lettres ou chiffres (reste du BBAN)

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_swift"></a>Keyword_swift

- organisation internationale de normalisation 9362
- ISO 9362
- iso9362
- Swift #
- swiftcode
- swiftnumber
- swiftroutingnumber
- code swift
- # numéro swift
- numéro d’acheminement swift
- numéro BIC
- code BIC
- # bic
- Bic #
- code d’identification bancaire
- Organisation internationale de normalisation 9362
- rapide #
- code SWIFT
- le numéro de swift
- swift numéro d’acheminement
- le numéro BIC
- \# BIC
- code identificateur de banque
- SWIFTコード
- SWIFT番号
- BIC番号
- BICコード
- SWIFT コード
- SWIFT 番号
- BIC 番号
- BIC コード
- 金融機関識別コード
- 金融機関コード
- 銀行コード

## <a name="switzerland-physical-addresses"></a>Adresses physiques en Suisse

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique de la Suisse. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="switzerland-ssn-ahv-number"></a>Numéro DEV SSN suisse

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Numéro à 13 chiffres

### <a name="pattern"></a>Modèle

Numéro à 13 chiffres :

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_swiss_social_security_number_ahv recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_swiss_social_security_number_ahv est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_swiss_social_security_number_ahv recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_swiss_ssn_ahv_number"></a>Keyword_swiss_ssn_AHV_number

- Avs
- Ssn
- pid
- numéro d’assurance
- personalidno #
- numéro de sécurité sociale
- numéro d’ID personnel
- identification personnelle non.
- insuranceno #
- uniqueidno #
- identification unique non.
- avs number
- identité personnelle pas versicherungsnummer
- identifikationsnummer
- einzigartige identität nicht
- sozialversicherungsnummer
- identification personnelle id
- numéro de sécurité sociale

## <a name="taiwan-national-identification-number"></a>Numéro d’identification nationale de Taïwan

### <a name="format"></a>Format

une lettre (en anglais) suivie de neuf chiffres

### <a name="pattern"></a>Modèle

une lettre (en anglais) suivie de neuf chiffres :

- une lettre (en anglais, non sensible à la casse)
- le chiffre « 1 » ou « 2 »
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_taiwanese_national_id trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_taiwanese_national_id est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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

- numéro de passeport biométrique : neuf chiffres
- Numéro de passeport non biométrique : neuf chiffres

### <a name="pattern"></a>Modèle
numéro de passeport biométrique :

- le caractère « 3 »
- huit chiffres

numéro de passeport non biométrique :

- neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_taiwan_passport"></a>Keyword_taiwan_passport

- ROC passport number
- Passport number
- Passport no
- Passport Num
- Passport #
- 护照
- 中華民國護照
- Zhōnghuá Mínguó hùzhào

## <a name="taiwan-resident-certificate-arctarc-number"></a>Numéro de certificat de résident taïwanais (ARC/TARC)

### <a name="format"></a>Format

10 lettres et chiffres

### <a name="pattern"></a>Modèle

10 lettres et chiffres :

- deux lettres (non sensibles à la casse)
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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

## <a name="thai-population-identification-code"></a>Code d’identification de la population thaïlandaise

### <a name="format"></a>Format

13 chiffres

### <a name="pattern"></a>Modèle

13 chiffres :

- premier chiffre n’est pas zéro ou neuf
- 12 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_Thai_Citizen_Id recherche le contenu qui correspond au modèle.
- Un mot clé de Keyword_Thai_Citizen_Id est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_Thai_Citizen_Id recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_thai_citizen_id"></a>Keyword_thai_citizen_Id

- ID Number
- Numéro d’identification
- บัตรประชาชน
- รหัสบัตรประชาชน
- บัตรประชาชน
- รหัสบัตรประชาชน

## <a name="turkey-national-identification-number"></a>Numéro d’identification nationale de la Turquie

### <a name="format"></a>Format

11 chiffres

### <a name="pattern"></a>Modèle

11 chiffres

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_Turkish_National_Id recherche le contenu qui correspond au modèle.
- Un mot clé de Keyword_Turkish_National_Id est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_Turkish_National_Id recherche le contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_turkish_national_id"></a>Keyword_turkish_national_id

- TC Kimlik No
- TC Kimlik numarası
- Vatandaşlık numarası
- Vatandaşlık no

## <a name="turkey-physical-addresses"></a>Adresses physiques de la Turquie

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique de la Turquie. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="types-of-medication"></a>Types de médicaments

Cette entité nommée non regroupée détecte les noms des médicaments, tels que *l’insuline*.  Il prend uniquement en charge les termes anglais. Il est également inclus dans les [conditions générales médicales](#all-medical-terms-and-conditions) regroupées sous le nom d’entité SIT.

### <a name="confidence-level"></a>Niveau de confiance

Élevé

## <a name="uk-drivers-license-number"></a>ROYAUME-UNI. numéro de permis de conduire

### <a name="format"></a>Format

Combinaison de 18 lettres et chiffres au format spécifié

### <a name="pattern"></a>Modèle

18 lettres et chiffres

- Cinq lettres (sans respect de la casse) ou le chiffre « 9 » à la place d’une lettre.
- Un chiffre.
- Cinq chiffres au format de date MMDDY pour la date de naissance. Le septième caractère est incrémenté de 50 si le conducteur est une femme; par exemple, 51 à 62 au lieu de 01 à 12.
- Deux lettres (sans respect de la casse) ou le chiffre « 9 » à la place d’une lettre.
- Cinq chiffres.

### <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_uk_drivers_license` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_eu_driver's_license_number` trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_uk_drivers_license` recherche le contenu qui correspond au modèle.
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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

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
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
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
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
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
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
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
- driver’s lic #
- driver’s lics #
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
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

## <a name="uk-electoral-roll-number"></a>ROYAUME-UNI. numéro de liste électorale

### <a name="format"></a>Format

deux lettres suivies de 1 à 4 chiffres

### <a name="pattern"></a>Modèle

deux lettres (non sensibles à la casse) suivies de 1 à 4 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_uk_electoral"></a>Keyword_uk_electoral

- nomination au conseil
- formulaire de nomination
- registre électoral
- liste électorale

## <a name="uk-national-health-service-number"></a>ROYAUME-UNI. numéro de service de santé national

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- service national de santé
- Nhs
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
- D.D.N
- Date of Birth
- Birth Date

## <a name="uk-national-insurance-number-nino"></a>ROYAUME-UNI. numéro d’assurance nationale (NINO)

Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles numéro d’identification nationale de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

### <a name="format"></a>Format

sept caractères ou neuf caractères séparés par des espaces ou des tirets

### <a name="pattern"></a>Modèle

deux modèles possibles :

- deux lettres (les objets NINO valides utilisent uniquement certains caractères de ce préfixe, ce que ce modèle valide ; non sensibles à la casse)
- six chiffres
- 'A', 'B', 'C' ou 'D' (comme le préfixe, seuls certains caractères sont autorisés dans le suffixe ; non sensibles à la casse)

OR

- deux lettres
- un espace ou un tiret
- deux chiffres
- un espace ou un tiret
- deux chiffres
- un espace ou un tiret
- deux chiffres
- un espace ou un tiret
- 'A', 'B', 'C' ou 'D'

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_uk_nino trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_uk_nino est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_uk_nino"></a>Keyword_uk_nino

- numéro d’assurance nationale
- cotisations sociales
- loi sur la protection
- Assurance
- numéro de sécurité sociale
- demande d’assurance
- demande de soins médicaux
- assurance sociale
- soins médicaux
- sécurité sociale
- grande-bretagne
- Numéro d’interface de commande
- Ni Non.
- NI #
- NI #
- Assurance #
- insurancenumber
- nationalinsurance #
- nationalinsurancenumber

## <a name="uk-physical-addresses"></a>ROYAUME-UNI. adresses physiques

Cette entité nommée non regroupée détecte les modèles liés à l’adresse physique à partir du Royaume-Uni. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="uk-unique-taxpayer-reference-number"></a>ROYAUME-UNI. Numéro de référence unique du contribuable

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

10 chiffres sans espaces et délimiteurs

### <a name="pattern"></a>Modèle

10 chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_uk_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_uk_eu_tax_file_number` trouvé.

```xml
      <!-- U.K. Unique Taxpayer Reference Number -->
      <Entity id="ad4a8116-0db8-439a-b545-6d967642f0ec" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_uk_eu_tax_file_number" />
          <Match idRef="Keywords_uk_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_uk_eu_tax_file_number"></a>Keywords_uk_eu_tax_file_number

- numéro d’impôt
- fichier fiscal
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #

## <a name="us-bank-account-number"></a>Numéro de compte bancaire américain

### <a name="format"></a>Format

6 à 17 chiffres

### <a name="pattern"></a>Modèle

6 à 17 chiffres consécutifs

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

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

dépend de l’état , par exemple, New York :

- neuf chiffres mis en forme comme ddd ddd ddd ddd correspondent.
- neuf chiffres comme dddddddddd ne correspondent pas.

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_new_york_drivers_license_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_[state_name]_drivers_license_name est trouvé.
- Un mot clé figurant dans la liste Keyword_us_drivers_license est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_us_drivers_license_abbreviations"></a>Keyword_us_drivers_license_abbreviations

- DL
- DLS
- CDL
- CDLS
- ID
- Id
- DL #
- DLS #
- CDL #
- CDLS #
- ID #
- Id #
- Numéro d’identification
- Numéros d’identification
- LIC
- LIC #
- DLN

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
- Driver’License
- Licences de pilote
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
- Driver’License #
- Licences de pilote #
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

- abréviation d’état (par exemple, « NY »)
- nom de l’état (par exemple, « New York »)

## <a name="us-individual-taxpayer-identification-number-itin"></a>Numéro d’identification des contribuables américains individuels (ITIN)

### <a name="format"></a>Format

neuf chiffres qui commencent par un « 9 » et contiennent « 7 » ou « 8 » comme quatrième chiffre, éventuellement mis en forme avec des espaces ou des tirets

### <a name="pattern"></a>Modèle

Formaté:

- le chiffre « 9 »
- deux chiffres
- un espace ou un tiret
- un « 7 » ou « 8 »
- un chiffre
- un espace ou un tiret
- quatre chiffres

Mémoire:

- le chiffre « 9 »
- deux chiffres
- un « 7 » ou « 8 »
- cinq chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_formatted_itin trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_itin est trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_unformatted_itin trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_itin est trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_formatted_itin ou Func_unformatted_itin recherche du contenu qui correspond au modèle.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_itin"></a>Keyword_itin

- Contribuable
- id fiscal
- identification fiscale
- itin
- i.t.i.n.
- Ssn
- Étain
- sécurité sociale
- contribuable
- itins
- taxid
- contribuable individuel

## <a name="us-physical-addresses"></a>Adresses physiques américaines

Cette entité nommée non groupée détecte les modèles liés à l’adresse physique des États-Unis. Il est également inclus dans l’entité SIT toutes [les adresses physiques](#all-physical-addresses) regroupées.

### <a name="confidence-level"></a>Niveau de confiance

Moyen

## <a name="us-social-security-number-ssn"></a>Numéro de sécurité sociale (SSN) des États-Unis

### <a name="format"></a>Format

neuf chiffres, qui peuvent être dans un modèle mis en forme ou non mis en forme

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_ssn` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_ssn` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_unformatted_ssn recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_ssn` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- `Func_randomized_formatted_ssn` Fonction ou `Func_randomized_unformatted_ssn` recherche du contenu qui correspond au modèle.
- Un mot clé est `Keyword_ssn` trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_ssn"></a>Keyword_ssn

- Numéro SSA
- numéro de sécurité sociale
- sécurité sociale #
- sécurité sociale #
- sécurité sociale non
- # sécurité sociale
- Sécu sociale
- SSN
- SSNS
- SSN #
- SS #
- SSID

## <a name="usuk-passport-number"></a>États-Unis/Royaume-Uni numéro de passeport

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

- une lettre ou un chiffre
- huit chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_usa_uk_passport trouve un contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_uk_eu_passport_number` est trouvé.
- Un mot clé à partir de `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_usa_uk_passport trouve un contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_uk_eu_passport_number` est trouvé.

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

### <a name="keywords"></a>Mots-clés

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

#### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- passeport britannique
- uk passport

## <a name="ukraine-passport-domestic"></a>Passeport d’Ukraine intérieur

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

neuf chiffres

### <a name="pattern"></a>Modèle

neuf chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- Le Regex_Ukraine_Passport_Domestic regex recherche le contenu qui correspond au modèle.
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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_ukraine_passport_domestic"></a>Keyword_ukraine_passport_domestic

- passeport ukraine
- numéro de passeport
- passport no
- паспорт України
- номер паспорта
- персональний

## <a name="ukraine-passport-international"></a>Passeport international de l’Ukraine

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Modèle alphanumérique à huit caractères

### <a name="pattern"></a>Modèle

Modèle alphanumérique à huit caractères :

- deux lettres ou chiffres
- six chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- Le Regex_Ukraine_Passport_International regex recherche le contenu qui correspond au modèle.
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

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_ukraine_passport_international"></a>Keyword_ukraine_passport_international

- passeport ukraine
- numéro de passeport
- passport no
- паспорт України
- номер паспорта
