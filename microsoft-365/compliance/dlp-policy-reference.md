---
title: Informations de référence sur la stratégie de protection contre la perte de données
f1.keywords: CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 03/02/2022
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- M365-security-compliance
- SPO_Content
recommendations: false
description: Informations de référence sur le composant de stratégie DLP et la configuration
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: 12c416af0a6f715ce56c193830ddb0db0ad9eba1
ms.sourcegitcommit: 651610ca73bfd1d008d97311b59782790df664fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67615229"
---
# <a name="data-loss-prevention-policy-reference"></a>Informations de référence sur la stratégie de protection contre la perte de données

les stratégies Protection contre la perte de données Microsoft Purview (DLP) ont de nombreux composants à configurer. Pour créer une stratégie efficace, vous devez comprendre quel est l’objectif de chaque composant et comment sa configuration modifie le comportement de la stratégie. Cet article fournit une anatomie détaillée d’une stratégie DLP.

## <a name="policy-templates"></a>Modèles de stratégie 

Les modèles de stratégie DLP sont pré triés en quatre catégories :

- Qui peuvent détecter et protéger les types d’informations **financières** .
- Celles qui peuvent détecter et protéger les types d’informations **médicales et médicales** .
- Qui peuvent détecter et protéger les types d’informations de **confidentialité** .
- Modèle **personnalisé** que vous pouvez utiliser pour créer votre propre stratégie si l’un des autres ne répond pas aux besoins de votre organisation.

Ce tableau répertorie tous les modèles de stratégie et les types d’informations sensibles (SIT) qu’ils couvrent. 

mise à jour : 23/06/2021

|Catégorie|Modèle | S' asseoir |
|---------|---------|---------|
|Financier| Données financières en Australie| - [Code SWIFT](sit-defn-swift-code.md) </br> -  [Numéro de fichier fiscal en Australie](sit-defn-australia-tax-file-number.md) </br> - [Numéro de compte bancaire en Australie](sit-defn-australia-bank-account-number.md) </br> - [Numéro de carte de crédit](sit-defn-credit-card-number.md)|
|Financier| Données financières du Canada |- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Numéro de compte bancaire au Canada](sit-defn-canada-bank-account-number.md)|
|Financier| Données financières de la France |- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Numéro de carte de débit de l’UE](sit-defn-eu-debit-card-number.md)|
|Financier| Données financières en Allemagne |- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Numéro de carte de débit de l’UE](sit-defn-eu-debit-card-number.md)|
|Financier| Données financières en Israël |- [Numéro de compte bancaire en Israël](sit-defn-israel-bank-account-number.md) </br> - [Code SWIFT](sit-defn-swift-code.md) </br> - [Numéro de carte de crédit](sit-defn-credit-card-number.md)|
|Financier| Données financières au Japon |- [Numéro de compte bancaire au Japon](sit-defn-japan-bank-account-number.md)</br> - [Numéro de carte de crédit](sit-defn-credit-card-number.md)|
|Financier| PCI Data Security Standard (PCI DSS)|- [Numéro de carte de crédit](sit-defn-credit-card-number.md)|
|Financier| Loi anti-cybercriminalité en Arabie saoudite|- [Code SWIFT](sit-defn-swift-code.md) </br> - [Numéro de compte bancaire international (IBAN)](sit-defn-international-banking-account-number.md)|
|Financier| Données financières en Arabie Saoudite |- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Code SWIFT](sit-defn-swift-code.md) </br> - [Numéro de compte bancaire international (IBAN)](sit-defn-international-banking-account-number.md)|
|Financier| Données financières du Royaume-Uni|- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Numéro de carte de débit de l’UE](sit-defn-eu-debit-card-number.md) </br> - [Code SWIFT](sit-defn-swift-code.md)|
|Financier| Données financières américaines|- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Numéro de compte bancaire américain](sit-defn-us-bank-account-number.md)</br> - [Numéro de routage ABA](sit-defn-aba-routing.md)|
|Financier| U.S. Federal Trade Commission (FTC) Consumer Rules|- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Numéro de compte bancaire américain](sit-defn-us-bank-account-number.md)</br> - [Numéro de routage ABA](sit-defn-aba-routing.md)|
|Financier| U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced|- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Numéro de compte bancaire américain](sit-defn-us-bank-account-number.md)</br> - [Numéro d’identification du contribuable (ITIN) des États-Unis](sit-defn-us-individual-taxpayer-identification-number.md)  </br> - [Numéro de sécurité sociale (SSN) des États-Unis](sit-defn-us-social-security-number.md)</br> - [Numéro de passeport des États-Unis/Du Royaume-Uni](sit-defn-us-uk-passport-number.md) </br> -[Numéro de permis de conduire américain](sit-defn-us-drivers-license-number.md)</br> - [Tous les noms complets](sit-defn-all-full-names.md)</br> - [Adresses physiques américaines](sit-defn-us-physical-addresses.md)|
|Financier| U.S. Gramm-Leach-Bliley Act (GLBA)|- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Numéro de compte bancaire américain](sit-defn-us-bank-account-number.md)</br> - [Numéro d’identification du contribuable (ITIN) des États-Unis](sit-defn-us-individual-taxpayer-identification-number.md)  </br> - [Numéro de sécurité sociale (SSN) des États-Unis](sit-defn-us-social-security-number.md)|
|Santé et médical| Australia Health Records Act (HRIP Act) Enhanced |- [Numéro de fichier fiscal en Australie](sit-defn-australia-tax-file-number.md)</br> - [Numéro de compte médical en Australie](sit-defn-australia-medical-account-number.md)</br> - [Tous les noms complets](sit-defn-all-full-names.md) </br> - [Toutes les conditions générales médicales](sit-defn-all-medical-terms-conditions.md) </br> - [Adresses physiques de l’Australie](sit-defn-australia-physical-addresses.md)|
|Santé et médical| Australia Health Records Act (HRIP Act)|- [Numéro de fichier fiscal en Australie](sit-defn-australia-tax-file-number.md) </br> - [Numéro de compte médical en Australie](sit-defn-australia-medical-account-number.md)|
|Santé et médical| Canada Health Information Act (HIA) |- [Numéro de passeport du Canada](sit-defn-canada-passport-number.md) </br> - [Numéro d’assurance sociale du Canada](sit-defn-canada-social-insurance-number.md) </br> - [Numéro du service de santé du Canada](sit-defn-canada-health-service-number.md) </br> - [Numéro d’identification de la santé personnelle du Canada](sit-defn-canada-personal-health-identification-number.md)|
|Santé et médical| Canada Personal Health Information Act (PHIA) Manitoba|- [Numéro d’assurance sociale du Canada](sit-defn-canada-social-insurance-number.md) </br> - [Numéro du service de santé du Canada](sit-defn-canada-health-service-number.md) </br> - [Numéro d’identification de la santé personnelle du Canada](sit-defn-canada-personal-health-identification-number.md)|
|Santé et médical| Canada Personal Health Act (PHIPA) Ontario |- [Numéro de passeport du Canada](sit-defn-canada-passport-number.md) </br> - [Numéro d’assurance sociale du Canada](sit-defn-canada-social-insurance-number.md) </br> - [Numéro du service de santé du Canada](sit-defn-canada-health-service-number.md) </br> - [Numéro d’identification de la santé personnelle du Canada](sit-defn-canada-personal-health-identification-number.md)|
|Santé et médical| Royaume-Uni Access to Medical Reports Act|- [Numéro de service de santé national du Royaume-Uni](sit-defn-uk-national-health-service-number.md) </br> - [Numéro d’assurance nationale du Royaume-Uni (NINO)](sit-defn-uk-national-insurance-number.md)|
|Santé et médical| Loi américaine sur l’assurance maladie (HIPAA) améliorée|</br> - [Classification internationale des maladies (ICD-9-CM)](sit-defn-international-classification-of-diseases-icd-9-cm.md) </br> - [Classification internationale des maladies (ICD-10-CM)](sit-defn-international-classification-of-diseases-icd-10-cm.md) </br> - [Tous les noms complets](sit-defn-all-full-names.md) </br> - [Toutes les conditions générales médicales](sit-defn-all-medical-terms-conditions.md) </br> - [Adresses physiques américaines](sit-defn-us-physical-addresses.md)|
|Santé et médical| U.S. Health Insurance Act (HIPAA)| - [Classification internationale des maladies (ICD-9-CM)](sit-defn-international-classification-of-diseases-icd-9-cm.md) </br> - [Classification internationale des maladies (ICD-10-CM)](sit-defn-international-classification-of-diseases-icd-10-cm.md)|
|Confidentialité| Australie Privacy Act Enhanced|- [Numéro de permis de conduire en Australie](sit-defn-australia-drivers-license-number.md) </br> - [Numéro de passeport en Australie](sit-defn-australia-passport-number.md) </br> - [Tous les noms complets](sit-defn-all-full-names.md) </br> - [Toutes les conditions générales médicales](sit-defn-all-medical-terms-conditions.md) </br> - [Adresses physiques de l’Australie](sit-defn-australia-physical-addresses.md)|
|Confidentialité| Australia Privacy Act|- [Numéro de permis de conduire en Australie](sit-defn-australia-drivers-license-number.md)</br> - [Numéro de passeport en Australie](sit-defn-australia-passport-number.md)|
|Confidentialité| Australia Personally Identifiable Information (PII) Data|- [Numéro de fichier fiscal en Australie](sit-defn-australia-tax-file-number.md) </br> - [Numéro de permis de conduire en Australie](sit-defn-australia-drivers-license-number.md)|
|Confidentialité| Canada Personally Identifiable Information (PII) Data|- [Numéro de permis de conduire au Canada](sit-defn-canada-drivers-license-number.md) </br> - [Numéro de compte bancaire au Canada](sit-defn-canada-bank-account-number.md) </br> - [Numéro de passeport du Canada](sit-defn-canada-passport-number.md) </br> - [Numéro d’assurance sociale du Canada](sit-defn-canada-social-insurance-number.md) </br> - [Numéro du service de santé du Canada](sit-defn-canada-health-service-number.md) </br> - [Numéro d’identification de la santé personnelle du Canada](sit-defn-canada-personal-health-identification-number.md)|
|Confidentialité| Canada Personal Information Protection Act (PIPA)|- [Numéro de passeport du Canada](sit-defn-canada-passport-number.md) </br> - [Numéro d’assurance sociale du Canada](sit-defn-canada-social-insurance-number.md) </br> - [Numéro du service de santé du Canada](sit-defn-canada-health-service-number.md) </br> - [Numéro d’identification de la santé personnelle du Canada](sit-defn-canada-personal-health-identification-number.md)|
|Confidentialité| Canada Personal Information Protection and Electronic Documents Act (PIPEDA)|- [Numéro de permis de conduire au Canada](sit-defn-canada-drivers-license-number.md) </br> - [Numéro de compte bancaire au Canada](sit-defn-canada-bank-account-number.md) </br> - [Numéro de passeport du Canada](sit-defn-canada-passport-number.md) </br> - [Numéro d’assurance sociale du Canada](sit-defn-canada-social-insurance-number.md) </br> - [Numéro du service de santé du Canada](sit-defn-canada-health-service-number.md) </br> - [Numéro d’identification de la santé personnelle du Canada](sit-defn-canada-personal-health-identification-number.md)|
|Confidentialité| Loi informatique et liberté en France|- [Carte d’identité nationale de France (CNI)](sit-defn-france-national-id-card.md)</br> - [Numéro de sécurité sociale en France (INSEE)](sit-defn-france-social-security-number.md)|
|Confidentialité| France Personally Identifiable Information (PII) Data|- [Numéro de sécurité sociale en France (INSEE)](sit-defn-france-social-security-number.md) </br> - [Numéro de permis de conduire en France](sit-defn-france-drivers-license-number.md) </br> - [Numéro de passeport en France](sit-defn-france-passport-number.md) </br> - [Carte d’identité nationale de France (CNI)](sit-defn-france-national-id-card.md)|
|Confidentialité| Règlement général sur la protection des données (RGPD) amélioré|- [Adresses physiques en Autriche](sit-defn-austria-physical-addresses.md) </br> - [Adresses physiques belges](sit-defn-belgium-physical-addresses.md) </br> - [Adresses physiques bulgares](sit-defn-bulgaria-physical-addresses.md) </br> - [Adresses physiques croates](sit-defn-croatia-physical-addresses.md) </br> - [Adresses physiques de Chypre](sit-defn-cyprus-physical-addresses.md) </br> - [Adresses physiques de la République tchèque](sit-defn-czech-republic-physical-addresses.md)</br> - [Adresses physiques du Danemark](sit-defn-denmark-physical-addresses.md)</br> - [Adresses physiques estoniennes](sit-defn-estonia-physical-addresses.md)</br> - [Adresses physiques en Finlande](sit-defn-finland-physical-addresses.md)</br> - [Adresses physiques de la France](sit-defn-france-physical-addresses.md)</br> - [Adresses physiques allemandes](sit-defn-germany-physical-addresses.md)</br> - [Adresses physiques de la Grèce](sit-defn-greece-physical-addresses.md)</br> - [Adresses physiques en Hongrie](sit-defn-hungary-physical-addresses.md)</br> - [Adresses physiques de l’Irlande](sit-defn-ireland-physical-addresses.md)</br> - [Adresses physiques en Italie](sit-defn-italy-physical-addresses.md)</br> - [Adresses physiques lettones](sit-defn-latvia-physical-addresses.md)</br> - [Adresses physiques lituaniennes](sit-defn-lithuania-physical-addresses.md)</br> - [Adresses physiques luxembourgeoises](sit-defn-luxemburg-physical-addresses.md)</br> - [Adresses physiques de Malte](sit-defn-malta-physical-addresses.md)</br> - [Adresses physiques des Pays-Bas](sit-defn-netherlands-physical-addresses.md)</br> - [Adresses physiques en Pologne](sit-defn-poland-physical-addresses.md)</br> - [Adresses physiques portugaises](sit-defn-portugal-physical-addresses.md)</br> - [Adresses physiques en Roumanie](sit-defn-romania-physical-addresses.md)</br> - [Adresses physiques en Slovaquie](sit-defn-slovakia-physical-addresses.md)</br> - [Adresses physiques slovènes](sit-defn-slovenia-physical-addresses.md)</br> - [Adresses physiques en Espagne](sit-defn-spain-physical-addresses.md)</br> - [Adresses physiques en Suède](sit-defn-sweden-physical-addresses.md)</br> - [Numéro de sécurité sociale en Autriche](sit-defn-austria-social-security-number.md) </br> - [Numéro de sécurité sociale en France (INSEE)](sit-defn-france-social-security-number.md)</br> - [Numéro de sécurité sociale en Grèce (AMKA)](sit-defn-greece-social-security-number.md)</br> - [Numéro de sécurité sociale hongrois (TAJ)](sit-defn-hungary-social-security-number.md)</br> - [Numéro de sécurité sociale en Espagne (SSN)](sit-defn-spain-social-security-number.md)</br> - [Carte d’identité d’Autriche](sit-defn-austria-identity-card.md) </br> - [Carte d’identité de Chypre](sit-defn-cyprus-identity-card.md) </br> - [Numéro de carte d’identité d’Allemagne](sit-defn-germany-identity-card-number.md)</br> - [Numéro de carte d’identité de Malte](sit-defn-malta-identity-card-number.md)</br> - [Carte d’identité nationale de France (CNI)](sit-defn-france-national-id-card.md)</br> - [Carte nationale d’ID de Grèce](sit-defn-greece-national-id-card.md)</br> - [ID national de la Finlande](sit-defn-finland-national-id.md)</br> - [Poland National ID (PESEL)](sit-defn-poland-national-id.md)</br> - [ID national de la Suède](sit-defn-sweden-national-id.md)</br> - [Numéro d’identification personnelle croate (OIB)](sit-defn-croatia-personal-identification-number.md) </br> - [Numéro d’identité personnelle tchèque](sit-defn-czech-personal-identity-number.md)</br> - [Numéro d’identification personnelle du Danemark](sit-defn-denmark-personal-identification-number.md)</br> - [Code d’identification personnelle de l’Estonie](sit-defn-estonia-personal-identification-code.md)</br> - [Numéro d’identification personnelle en Hongrie](sit-defn-hungary-personal-identification-number.md)</br> - [Luxemburg National Identification Number natural persons](sit-defn-luxemburg-national-identification-number-natural-persons.md)</br> - [Numéro d’identification national du Luxembourg (personnes non naturelles)](sit-defn-luxemburg-national-identification-number-non-natural-persons.md)</br> - [Code fiscal de l’Italie](sit-defn-italy-fiscal-code.md)</br> - [Code personnel letton](sit-defn-latvia-personal-code.md)</br> - [Code personnel lituanien](sit-defn-lithuania-personal-code.md)</br> - [Code numérique personnel roumain (CNP)](sit-defn-romania-personal-numeric-code.md)</br> - [Numéro du BSN (Netherlands Citizen’s Service)](sit-defn-netherlands-citizens-service-number.md)</br> - [Numéro de service public personnel (PPS) en Irlande](sit-defn-ireland-personal-public-service-number.md)</br> - [Numéro civil uniforme en Bulgarie](sit-defn-bulgaria-uniform-civil-number.md) </br> - [Numéro national de belgique](sit-defn-belgium-national-number.md) </br> - [Espagne DNI](sit-defn-spain-dni.md)</br> - [Slovénie Unique Master Citizen Number](sit-defn-slovenia-unique-master-citizen-number.md)</br> - [Numéro personnel en Slovaquie](sit-defn-slovakia-personal-number.md)</br> - [Numéro de carte de citoyen du Portugal](sit-defn-portugal-citizen-card-number.md)</br> - [Numéro d’ID fiscal de Malte](sit-defn-malta-tax-identification-number.md)</br> - [Numéro d’identification fiscale en Autriche](sit-defn-austria-tax-identification-number.md) </br> - [Numéro d’identification fiscale de Chypre](sit-defn-cyprus-tax-identification-number.md) </br> -[Numéro d’identification fiscale en France (numéro SPI.)](sit-defn-france-tax-identification-number.md)</br> - [Numéro d’identification fiscale en Allemagne](sit-defn-germany-tax-identification-number.md)</br> - [Numéro d’identification fiscale grecque](sit-defn-greece-tax-identification-number.md)</br> - [Numéro d’identification fiscale en Hongrie](sit-defn-hungary-tax-identification-number.md)</br> - [Numéro d’identification fiscale aux Pays-Bas](sit-defn-netherlands-tax-identification-number.md)</br> - [Numéro d’identification fiscale en Pologne](sit-defn-poland-tax-identification-number.md)</br> - [Numéro d’identification fiscale du Portugal](sit-defn-portugal-tax-identification-number.md)</br> - [Numéro d’identification fiscale en Slovénie](sit-defn-slovenia-tax-identification-number.md)</br> - [Numéro d’identification fiscale en Espagne](sit-defn-spain-tax-identification-number.md)</br> - [Numéro d’identification fiscale en Suède](sit-defn-sweden-tax-identification-number.md)</br> - [Permis de conduire en Autriche](sit-defn-austria-drivers-license-number.md) </br> - [Numéro de permis de conduire en Belgique](sit-defn-belgium-drivers-license-number.md) </br> - [Numéro de permis de conduire en Bulgarie](sit-defn-bulgaria-drivers-license-number.md) </br> - [Numéro de permis de conduire en Croatie](sit-defn-croatia-drivers-license-number.md) </br> - [Numéro de permis de conduire de Chypre](sit-defn-cyprus-drivers-license-number.md) </br> - [Numéro de permis de conduire tchèque](sit-defn-czech-drivers-license-number.md) </br> - [Numéro de permis de conduire au Danemark](sit-defn-denmark-drivers-license-number.md)</br> - [Numéro de permis de conduire estonien](sit-defn-estonia-drivers-license-number.md)</br> - [Numéro de permis de conduire en Finlande](sit-defn-finland-drivers-license-number.md)</br> - [Numéro de permis de conduire en France](sit-defn-france-drivers-license-number.md)</br> - [Numéro de permis de conduire allemand](sit-defn-germany-drivers-license-number.md)</br> - [Numéro de permis de conduire en Grèce](sit-defn-greece-drivers-license-number.md) </br> - [Numéro de permis de conduire en Hongrie](sit-defn-hungary-drivers-license-number.md)</br> - [Numéro de permis de conduire en Irlande](sit-defn-ireland-drivers-license-number.md)</br> - [Numéro de permis de conduire en Italie](sit-defn-italy-drivers-license-number.md)</br> - [Numéro de permis de conduire letton](sit-defn-latvia-drivers-license-number.md)</br> - [Numéro de permis de conduire en Lituanie](sit-defn-lithuania-drivers-license-number.md)</br> - [Numéro de permis de conduire du Luxemburg](sit-defn-luxemburg-drivers-license-number.md)</br> - [Numéro de permis de conduire de Malte](sit-defn-malta-drivers-license-number.md)</br> - [Numéro de permis de conduire aux Pays-Bas](sit-defn-netherlands-drivers-license-number.md)</br> - [Numéro de permis de conduire en Pologne](sit-defn-poland-drivers-license-number.md)</br> - [Numéro de permis de conduire au Portugal](sit-defn-portugal-drivers-license-number.md)</br> - [Numéro de permis de conduire en Roumanie](sit-defn-romania-drivers-license-number.md)</br> - [Numéro de permis de conduire en Slovaquie](sit-defn-slovakia-drivers-license-number.md)</br> - [Numéro de permis de conduire en Slovénie](sit-defn-slovenia-drivers-license-number.md)</br> - [Numéro de permis de conduire en Espagne](sit-defn-spain-drivers-license-number.md)</br> - [Numéro de permis de conduire en Suède](sit-defn-sweden-drivers-license-number.md)</br> - [Numéro de passeport en Autriche](sit-defn-austria-passport-number.md) </br> - [Numéro de passeport en Belgique](sit-defn-belgium-passport-number.md) </br> - [Numéro de passeport en Bulgarie](sit-defn-bulgaria-passport-number.md) </br> - [Numéro de passeport en Croatie](sit-defn-croatia-passport-number.md) </br> - [Numéro de passeport de Chypre](sit-defn-cyprus-passport-number.md) </br> - [Numéro de passeport de la République tchèque](sit-defn-czech-passport-number.md) </br> - [Numéro de passeport du Danemark](sit-defn-denmark-passport-number.md)</br> - [Numéro de passeport estonien](sit-defn-estonia-passport-number.md)</br> - [Numéro de passeport en Finlande](sit-defn-finland-passport-number.md)</br> - [Numéro de passeport en France](sit-defn-france-passport-number.md)</br> - [Numéro de passeport allemand](sit-defn-germany-passport-number.md)</br> - [Numéro de passeport en Grèce](sit-defn-greece-passport-number.md)</br> - [Numéro de passeport en Hongrie](sit-defn-hungary-passport-number.md)</br> - [Numéro de passeport en Irlande](sit-defn-ireland-passport-number.md)</br> - [Numéro de passeport en Italie](sit-defn-italy-passport-number.md)</br> - [Numéro de passeport letton](sit-defn-latvia-passport-number.md)</br> - [Numéro de passeport en Lituanie](sit-defn-lithuania-passport-number.md)</br> - [Numéro de passeport de Luxemburg](sit-defn-luxemburg-passport-number.md)</br> - [Numéro de passeport maltais](sit-defn-malta-passport-number.md)</br> - [Numéro de passeport des Pays-Bas](sit-defn-netherlands-passport-number.md)</br> - [Passeport pologne](sit-defn-poland-passport-number.md)</br> - [Numéro de passeport du Portugal](sit-defn-portugal-passport-number.md)</br> - [Numéro de passeport en Roumanie](sit-defn-romania-passport-number.md)</br> - [Numéro de passeport en Slovaquie](sit-defn-slovakia-passport-number.md)</br> - [Numéro de passeport en Slovénie](sit-defn-slovenia-passport-number.md)</br> - [Numéro de passeport en Espagne](sit-defn-spain-passport-number.md)</br> - [Numéro de passeport en Suède](sit-defn-sweden-passport-number.md)</br> - [Numéro de carte de débit de l’UE](sit-defn-eu-debit-card-number.md)</br> - [Tous les noms complets](sit-defn-all-full-names.md)|
|Confidentialité| Règlement général sur la protection des données (RGPD)|- [Numéro de carte de débit de l’UE](sit-defn-eu-debit-card-number.md) </br> - [Numéro de permis de conduire de l’UE](sit-defn-eu-drivers-license-number.md) </br> - [Numéro d’identification nationale de l’UE](sit-defn-eu-national-identification-number.md)</br> - [Numéro de passeport de l’UE](sit-defn-eu-passport-number.md) </br> - [Numéro de sécurité sociale de l’UE ou identification équivalente](sit-defn-eu-social-security-number-equivalent-identification.md)</br> - [Numéro d’identification fiscale de l’UE](sit-defn-eu-tax-identification-number.md)|
|Confidentialité| Germany Personally Identifiable Information (PII) Data|- [Numéro de permis de conduire en Allemagne](sit-defn-germany-drivers-license-number.md) </br> - [Numéro de passeport en Allemagne](sit-defn-germany-passport-number.md)| 
|Confidentialité| Israel Personally Identifiable Information (PII) Data|- [Numéro d’identification nationale d’Israël](sit-defn-israel-national-identification-number.md)| 
|Confidentialité| Israel Protection of Privacy|- [Numéro d’identification nationale d’Israël](sit-defn-israel-national-identification-number.md)</br> - [Numéro de compte bancaire en Israël](sit-defn-israel-bank-account-number.md)|
|Confidentialité| Amélioration des données d’informations d’identification personnelle (PII) au Japon|- [Numéro d’assurance sociale du Japon (SIN)](sit-defn-japan-social-insurance-number.md)</br> - [Japon Mon numéro - Personnel](sit-defn-japan-my-number-personal.md)</br> - [Numéro de passeport au Japon](sit-defn-japan-passport-number.md)</br> - [Numéro de permis de conduire au Japon](sit-defn-japan-drivers-license-number.md)</br> - [Tous les noms complets](sit-defn-all-full-names.md)</br> - [Adresses physiques du Japon](sit-defn-all-physical-addresses.md)|
|Confidentialité| Japan Personally Identifiable Information (PII) Data|- [Numéro d’inscription des résidents du Japon](sit-defn-japan-resident-registration-number.md) </br> - [Numéro d’assurance sociale du Japon (SIN)](sit-defn-japan-social-insurance-number.md)|
|Confidentialité| Amélioration de la protection des informations personnelles au Japon|- [Numéro d’assurance sociale du Japon (SIN)](sit-defn-japan-social-insurance-number.md) </br> - [Japon Mon numéro - Personnel](sit-defn-japan-my-number-personal.md)</br> - [Numéro de passeport au Japon](sit-defn-japan-passport-number.md) </br> - [Numéro de permis de conduire au Japon](sit-defn-japan-drivers-license-number.md)</br> - [Tous les noms complets](sit-defn-all-full-names.md)</br> - [Adresses physiques du Japon](sit-defn-all-physical-addresses.md)|
|Confidentialité| Japan Protection of Personal Information|- [Numéro d’inscription des résidents du Japon](sit-defn-japan-resident-registration-number.md)</br> - [Numéro d’assurance sociale du Japon (SIN)](sit-defn-japan-social-insurance-number.md)|
|Confidentialité| Données d’identification personnelle (PII) de l’Arabie saoudite|- [ID national de l’Arabie saoudite](sit-defn-saudi-arabia-national-id.md)|
|Confidentialité| Royaume-Uni Data Protection Act|- [Numéro d’assurance nationale du Royaume-Uni (NINO)](sit-defn-uk-national-insurance-number.md) </br> - [Numéro de passeport des États-Unis/Du Royaume-Uni](sit-defn-us-uk-passport-number.md) </br> - [Code SWIFT](sit-defn-swift-code.md)|
|Confidentialité| Royaume-Uni Privacy and Electronic Communications Regulations|- [Code SWIFT](sit-defn-swift-code.md)|
|Confidentialité| Royaume-Uni Personally Identifiable Information (PII) Data|- [Numéro d’assurance nationale du Royaume-Uni (NINO)](sit-defn-uk-national-insurance-number.md) </br> - [Numéro de passeport des États-Unis/Du Royaume-Uni](sit-defn-us-uk-passport-number.md)|
|Confidentialité| Royaume-Uni Personal Information Online Code of Practice (PIOCP)|- [Numéro d’assurance nationale du Royaume-Uni (NINO)](sit-defn-uk-national-insurance-number.md) </br> - [Numéro de service de santé national du Royaume-Uni](sit-defn-uk-national-health-service-number.md) </br> - [Code SWIFT](sit-defn-swift-code.md)|
|Confidentialité| U.S Patriot Act amélioré|- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Numéro de compte bancaire américain](sit-defn-us-bank-account-number.md)</br> - [Numéro d’identification du contribuable (ITIN) des États-Unis](sit-defn-us-individual-taxpayer-identification-number.md)  </br> - [Numéro de sécurité sociale (SSN) des États-Unis](sit-defn-us-social-security-number.md)</br> - [Tous les noms complets](sit-defn-all-full-names.md)</br> - [Adresses physiques américaines](sit-defn-us-physical-addresses.md)|
|Confidentialité| U.S. Patriot Act|- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Numéro de compte bancaire américain](sit-defn-us-bank-account-number.md)</br> - [Numéro d’identification du contribuable (ITIN) des États-Unis](sit-defn-us-individual-taxpayer-identification-number.md)  </br> - [Numéro de sécurité sociale (SSN) des États-Unis](sit-defn-us-social-security-number.md)|
|Confidentialité| Données d’identification personnelle (PII) améliorées aux États-Unis|- [Numéro d’identification du contribuable (ITIN) des États-Unis](sit-defn-us-individual-taxpayer-identification-number.md)  </br> - [Numéro de sécurité sociale (SSN) des États-Unis](sit-defn-us-social-security-number.md)</br> - [Numéro de passeport des États-Unis/Du Royaume-Uni](sit-defn-us-uk-passport-number.md)</br> - [Tous les noms complets](sit-defn-all-full-names.md)</br> - [Adresses physiques américaines](sit-defn-us-physical-addresses.md)|
|Confidentialité| U.S. Personally Identifiable Information (PII) Data|- [Numéro d’identification du contribuable (ITIN) des États-Unis](sit-defn-us-individual-taxpayer-identification-number.md)  </br> - [Numéro de sécurité sociale (SSN) des États-Unis](sit-defn-us-social-security-number.md)</br> - [Numéro de passeport des États-Unis/Du Royaume-Uni](sit-defn-us-uk-passport-number.md)|
|Confidentialité| Les lois sur les notifications de violation de l’État des États-Unis ont été améliorées|- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Numéro de compte bancaire américain](sit-defn-us-bank-account-number.md)</br> -[Numéro de permis de conduire américain](sit-defn-us-drivers-license-number.md) </br> - [Numéro de sécurité sociale (SSN) des États-Unis](sit-defn-us-social-security-number.md)</br> - [Tous les noms complets](sit-defn-all-full-names.md) </br> - [Numéro de passeport des États-Unis/Du Royaume-Uni](sit-defn-us-uk-passport-number.md)</br> - [Toutes les conditions générales médicales](sit-defn-all-medical-terms-conditions.md)|
|Confidentialité| U.S. State Breach Notification Laws|- [Numéro de carte de crédit](sit-defn-credit-card-number.md) </br> - [Numéro de compte bancaire américain](sit-defn-us-bank-account-number.md)</br> -[Numéro de permis de conduire américain](sit-defn-us-drivers-license-number.md) </br> - [Numéro de sécurité sociale (SSN) des États-Unis](sit-defn-us-social-security-number.md)|
|Confidentialité| U.S. State Social Security Number Confidentiality Laws|- [Numéro de sécurité sociale (SSN) des États-Unis](sit-defn-us-social-security-number.md)|

## <a name="locations"></a>Emplacements

Une stratégie DLP peut rechercher et protéger des éléments qui contiennent des informations sensibles sur plusieurs emplacements.

|Emplacement  |Inclure/exclure l’étendue  |État des données  |Prérequis supplémentaires |
|---------|---------|---------|---------|
|E-mail Exchange en ligne |groupe de distribution | données en mouvement| Non |
|Sites en ligne SharePoint   |sites       | données au repos </br> données utilisées | Non|
|Les comptes OneDrive Entreprise| compte ou groupe de distribution |données au repos </br> données utilisées|Non|
|conversation et messages de canal Teams     | compte ou groupe de distribution |données en mouvement </br> données utilisées |  Non       |
|Microsoft Defender for Cloud Apps   | instance d’application cloud       |données au repos         | - [Utiliser des stratégies de protection contre la perte de données pour les applications cloud non Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)        |
|Appareils  |utilisateurs ou groupe         |données au repos </br>  données utilisées </br>  données en mouvement         |- [En savoir plus sur la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md) </br>- [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md) </br>- [Configurer les paramètres de proxy d’appareil et de connexion Internet pour Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection) |
|Référentiels locaux (partages de fichiers et SharePoint)    |Référentiel         | données au repos         | - [En savoir plus sur le scanneur local de protection contre la perte de données](dlp-on-premises-scanner-learn.md) </br> - [Prise en main du scanneur local de protection contre la perte de données](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)         |
|Power BI| Espaces | données utilisées | Non|

Si vous décidez d’inclure des groupes de distribution particuliers dans Exchange, la stratégie DLP est uniquement étendue aux membres de ceux-ci. De manière identique, l’exclusion d’un groupe de distribution exclut tous ses membres de l’évaluation de la stratégie. Vous pouvez choisir de limiter une stratégie aux membres des listes de distribution, aux groupes de distribution dynamiques et aux groupes de sécurité. Une stratégie DLP ne peut pas contenir plus de 50 inclusions et exclusions de ce genre.

Si vous optez pour l’inclusion ou l’exclusion de sites SharePoint ou de comptes OneDrive spécifiques, notez qu’une stratégie DLP ne peut pas contenir plus de 100 inclusions et exclusions. Vous pouvez néanmoins contourner cette limite en appliquant une stratégie mise en place à l’échelle de l’organisation ou une stratégie qui s’applique aux emplacements entiers.

Si vous choisissez d’inclure ou d’exclure des comptes ou groupes OneDrive spécifiques, une stratégie DLP peut contenir au plus 100 comptes d’utilisateurs ou 50 groupes pour l’inclusion ou l’exclusion.

### <a name="location-support-for-how-content-can-be-defined"></a>Prise en charge de l’emplacement pour la façon dont le contenu peut être défini

Les stratégies DLP détectent les éléments sensibles en les mettant en correspondance avec un type d’informations sensibles (SIT), une étiquette de confidentialité ou une étiquette de rétention. Chaque emplacement prend en charge différentes méthodes de définition de contenu sensible. Lorsque vous combinez des emplacements dans une stratégie, la façon dont le contenu peut être défini peut changer par la façon dont il peut être défini par un emplacement unique. 

> [!IMPORTANT]
> Lorsque vous sélectionnez plusieurs emplacements pour une stratégie, une valeur « non » pour une catégorie de définition de contenu est prioritaire sur la valeur « oui ». Par exemple, lorsque vous sélectionnez des sites SharePoint uniquement, la stratégie prend en charge la détection d’éléments sensibles par un ou plusieurs sit, par étiquette de confidentialité ou par étiquette de rétention. Toutefois, lorsque vous sélectionnez des sites SharePoint ***et*** des emplacements de messages de conversation et de canal Teams, la stratégie prend uniquement en charge la détection des éléments sensibles par SIT.

|Emplacement| Le contenu peut être défini par SIT| Le contenu peut être défini sur une étiquette de confidentialité| Le contenu peut être défini par une étiquette de rétention|
|---------|---------|---------|---------|
|E-mail Exchange en ligne|Oui| Oui| Non|
|Sites en ligne SharePoint| Oui| Oui| Oui|
|Les comptes OneDrive Entreprise| Oui| Oui| Oui|
|Messages de conversation et de canal Teams | Oui| Non| Non|
|Appareils |Oui | Oui|  Non|
|Microsoft Defender for Cloud Apps | Oui| Oui| Oui|
|Référentiels locaux| Oui| Oui| Non|
|Power BI|Oui | Oui| Non|

> [!NOTE]
> DLP prend en charge (en préversion) l’utilisation de classifieurs pouvant être formés comme condition pour détecter les documents sensibles. Le contenu peut être défini par des classifieurs pouvant être formés dans des Exchange Online, des sites SharePoint Online, des comptes OneDrive Entreprise, des canaux de conversation et des appareils Teams. Pour plus d’informations, consultez [Classifieurs pouvant être formés](classifier-learn-about.md).

> [!NOTE]
> DLP prend en charge la détection des étiquettes de confidentialité sur les e-mails et les pièces jointes. Pour plus d’informations, consultez [Utiliser les étiquettes de confidentialité comme conditions dans les stratégies DLP](dlp-sensitivity-label-as-condition.md#use-sensitivity-labels-as-conditions-in-dlp-policies).

## <a name="rules"></a>Rules

<!--This section introduces the classifications of content that, when detected, can be protected. Link out to [Learn about sensitive information types]() and [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) as well as labels (cross referenced by supporting workload). It will touch on the purpose of multiple conditions, confidence levels (link out to [more on confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels)) and confidence levels video. How to use the confidence level to change the behavior of a policy in conjunction with the instance count.  eg. if you want your policy to trigger when it encounters situation DEF, set your conditions like HIJ.-->
<!--
- What is a rule in the context of a Policy?
- when and why should I have more than one rule?
- The purpose of rule groups
- How do I tune the behavior of a Policy through the tuning of rules
- what's in a rule-->

Les règles sont la logique métier des stratégies DLP. Elles se composent des éléments suivantes :

- [**Conditions**](#conditions) qui, lorsqu’elle est mise en correspondance, déclenchent la stratégie
- [**Exceptions**](#exceptions) aux conditions
- [**Actions**](#actions) à effectuer lorsque la stratégie est déclenchée
- [**Notifications utilisateur**](#user-notifications-and-policy-tips) pour informer vos utilisateurs lorsqu’ils font quelque chose qui déclenche une stratégie et les aider à les informer sur la façon dont votre organisation souhaite que les informations sensibles soient traitées
- [**Les remplacements d’utilisateurs**](#user-overrides) lorsqu’ils sont configurés par un administrateur permettent aux utilisateurs de substituer de manière sélective une action de blocage
- [**Rapports d’incidents**](#incident-reports) qui informent les administrateurs et d’autres parties prenantes clés lorsqu’une correspondance de règle se produit
- [**Options supplémentaires**](#additional-options) qui définissent la priorité pour l’évaluation des règles et peuvent arrêter le traitement des règles et des stratégies.

 Une stratégie contient une ou plusieurs règles. Les règles sont exécutées de façon séquentielle, en commençant par la règle de priorité la plus élevée dans chaque stratégie.

### <a name="the-priority-by-which-rules-are-processed"></a>La priorité de traitement des règles

#### <a name="hosted-service-workloads"></a>Charges de travail de service hébergées

Pour les charges de travail de service hébergées, telles que Exchange Online, SharePoint Online et OneDrive Entreprise, chaque règle reçoit une priorité dans l’ordre dans lequel elle est créée. Cela signifie que la règle créée en premier a la première priorité, la règle créée en deuxième a la deuxième priorité, et ainsi de suite.
  
![Règles dans l’ordre de priorité](../media/dlp-rules-in-priority-order.png)

Lorsque des règles sont appliquées au contenu, elles sont traitées dans l’ordre de priorité. Si le contenu correspond à plusieurs règles, la première règle évaluée avec l’action la *plus* restrictive est appliquée. Par exemple, si le contenu correspond à toutes les règles suivantes, la *règle 3* est appliquée, car il s’agit de la règle la plus prioritaire et la plus restrictive :
  
- Règle 1 : informe seulement les utilisateurs
- Règle 2 : informe les utilisateurs, limite l’accès et permet le remplacement de l’utilisateur
- *Règle 3 : informe les utilisateurs, restreint l’accès et n’autorise pas les remplacements d’utilisateurs*
- Règle 4 : restreint l’accès

Les règles 1, 2 et 4 seraient évaluées, mais pas appliquées. Dans cet exemple, les correspondances pour toutes les règles sont enregistrées dans les journaux d’audit et affichées dans les rapports DLP, même si seule la règle la plus restrictive est appliquée.

Vous pouvez utiliser une règle pour répondre à une exigence de protection particulière, puis utiliser une stratégie DLP pour regrouper des spécifications requises communes en matière de protection, par exemple l’ensemble des règles requises pour se conformer à une réglementation spécifique.
  
Par exemple, vous pouvez avoir une stratégie DLP qui vous aide à détecter la présence d’informations visées par la loi américaine sur l’assurance maladie (Health Insurance Portability Accountability Act, ou HIPAA). Cette stratégie DLP peut contribuer à protéger les données HIPAA (quoi) sur tous les sites SharePoint Online et tous les sites OneDrive Entreprise (où) en recherchant les documents contenant ces informations sensibles partagées avec des personnes extérieures à votre organisation (conditions), et en bloquant l’accès au document et en envoyant une notification (actions). Ces conditions sont stockées en tant que règles individuelles et regroupées sous la forme d’une stratégie DLP pour simplifier la gestion et la création de rapports.
  
![Diagramme montrant que la stratégie DLP contient les règles et les emplacements](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png)

#### <a name="for-endpoints"></a>Pour les points de terminaison

La priorité des règles sur les points de terminaison est également affectée en fonction de l’ordre dans lequel elle est créée. Cela signifie que la règle créée en premier a la première priorité, la règle créée en deuxième a la deuxième priorité, et ainsi de suite. 

Lorsqu’un fichier sur un point de terminaison correspond à plusieurs stratégies DLP, la première règle activée avec l’application la plus restrictive [sur les activités de point](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on) de terminaison est celle qui est appliquée sur le contenu. Par exemple, si le contenu correspond à toutes les règles suivantes, la règle 2 est prioritaire sur les autres règles, car elle est la plus restrictive.

- Règle 1 : audite uniquement toutes les activités
- *Règle 2 : bloque toutes les activités*
- Règle 3 : bloque toute activité avec l’option permettant à l’utilisateur final de remplacer

Dans l’exemple ci-dessous, la règle 1 est prioritaire sur les autres règles correspondantes, car elle est la plus restrictive.

- *Règle 1 : bloque l’activité et n’autorise pas le remplacement par l’utilisateur*
- Règle 2 : bloque l’activité et autorise les remplacements d’utilisateurs
- Règle 3 : audite uniquement toutes les activités
- Règle 4 : aucune application

Toutes les autres règles sont évaluées, mais leurs actions ne sont pas appliquées. Les journaux d’audit affichent la règle la plus restrictive appliquée au fichier. S’il existe plusieurs règles qui correspondent et qu’elles sont tout aussi restrictives, la stratégie et la priorité de règle régissent la règle qui serait appliquée sur le fichier.

### <a name="conditions"></a>Conditions

Les conditions sont inclusives et vous définissez ce que vous souhaitez que la règle recherche et le contexte dans lequel ces éléments sont utilisés. Ils indiquent à la règle &#8212; lorsque vous trouvez un élément qui ressemble à *ceci* et qui est utilisé comme *cela* &#8212; il s’agit d’une correspondance et les autres actions de la stratégie doivent être effectuées sur celui-ci. Vous pouvez utiliser les conditions pour affecter différentes actions à différents niveaux de risque. Par exemple, un contenu sensible partagé en interne peut être moins risqué et nécessiter moins d’actions qu’un contenu sensible partagé avec des personnes extérieures à l’organisation.

> [!NOTE]
> Les utilisateurs qui ont des comptes non invités dans le client Active Directory ou Azure Active Directory d’une organisation hôte sont considérés comme des personnes internes à l’organisation. 

#### <a name="content-contains"></a>Le contenu contient

 Tous les emplacements prennent en charge la condition **contenu contient** . Vous pouvez sélectionner plusieurs instances de chaque type de contenu et affiner les conditions en utilisant l’un **de ces** opérateurs (OR logique) ou **tous ces** opérateurs (AND logiques) :

- [types d’informations sensibles](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [étiquettes de confidentialité](sensitivity-labels.md)
- [étiquettes de rétention](retention.md#using-a-retention-label-as-a-condition-in-a-dlp-policy)
- [Classifieurs pouvant être formés](classifier-learn-about.md) (en préversion) 

selon [l’emplacement auquel](#location-support-for-how-content-can-be-defined) vous choisissez d’appliquer la stratégie.

La règle recherche uniquement la présence d’étiquettes de **confidentialité** et **d’étiquettes de rétention** que vous sélectionnez.

Les SIT ont un [**niveau de confiance**](https://www.microsoft.com/videoplayer/embed/RE4Hx60) prédéfini que vous pouvez modifier si nécessaire. Pour plus d’informations, consultez [Plus sur les niveaux de confiance](sensitive-information-type-learn-about.md#more-on-confidence-levels).

> [!IMPORTANT]
> Les SIT ont deux façons différentes de définir les paramètres de nombre d’instances uniques max. Pour plus d’informations, consultez [Valeurs prises en charge par le nombre d’instances pour SIT](sit-limits.md#instance-count-supported-values-for-sit).

#### <a name="condition-context"></a>Contexte de condition

Les options de contexte disponibles changent en fonction de l’emplacement que vous choisissez. Si vous sélectionnez plusieurs emplacements, seules les conditions communes aux emplacements sont disponibles.

##### <a name="conditions-exchange-supports"></a>Conditions prises en charge par Exchange

- Le contenu contient
- Le contenu est partagé à partir de Microsoft 365
- Le contenu est reçu de
- L’adresse IP de l’expéditeur est
- L’expéditeur a remplacé l’info-bulle de stratégie
- L’expéditeur est
- Le domaine de l’expéditeur est
- L’adresse de l’expéditeur contient des mots
- L’adresse de l’expéditeur contient des modèles
- L’attribut AD de l’expéditeur contient des mots ou des expressions
- L’attribut AD de l’expéditeur correspond aux modèles
- L’expéditeur est membre de
- Le contenu de la pièce jointe n’a pas pu être analysé
- L’analyse du contenu de la pièce jointe n’a pas été terminée
- La pièce jointe est protégée par mot de passe
- L’extension de fichier est
- Le destinataire est membre de
- Le domaine du destinataire est
- Le destinataire est
- L'adresse du destinataire contient les mots
- L’adresse du destinataire correspond aux modèles
- L’attribut AD du destinataire contient des mots ou des expressions
- L’attribut AD du destinataire correspond aux modèles
- Le nom du document contient des mots ou des expressions
- Le nom du document correspond aux modèles
- La propriété du document est
- La taille du document est égale ou supérieure à
- Le contenu du document contient des mots ou des expressions
- Le contenu du document correspond aux modèles
- L’objet contient des mots ou des expressions
- L’objet correspond aux modèles
- Objet ou corps contient des mots ou des expressions
- L’objet ou le corps correspond aux modèles
- Le jeu de caractères de contenu contient des mots
- L’en-tête contient des mots ou des expressions
- L’en-tête correspond aux modèles
- La taille du message est égale ou supérieure à
- Le type de message est
- L’importance du message est

##### <a name="conditions-sharepoint-supports"></a>Conditions prises en charge par SharePoint
 
- Le contenu contient
- Le contenu est partagé à partir de Microsoft 365
- Document créé par
- Document créé par un membre de
- Le nom du document contient des mots ou des expressions
- Le nom du document correspond aux modèles
- Taille du document dépassée
- La propriété du document est
- L’extension de fichier est

##### <a name="conditions-onedrive-accounts-supports"></a>Conditions prises en charge par les comptes OneDrive

- Le contenu contient
- Le contenu est partagé à partir de Microsoft 365
- Document créé par
- Document créé par un membre de
- Le nom du document contient des mots ou des expressions
- Le nom du document correspond aux modèles
- Taille du document dépassée
- La propriété du document est
- L’extension de fichier est

##### <a name="conditions-teams-chat-and-channel-messages-supports"></a>Conditions prises en charge par les messages de conversation et de canal Teams

- Le contenu contient
- Le contenu est partagé à partir de Microsoft 365
- L’expéditeur est 
- Le domaine de l’expéditeur est 
- Le domaine du destinataire est 
- Le destinataire est 

##### <a name="conditions-devices-supports"></a>Conditions prises en charge par les appareils

- Le contenu contient
- (préversion) Le document ou la pièce jointe est protégé par mot de passe/le fichier est chiffré. (.pdf, les fichiers Office sont entièrement pris en charge. Seuls les fichiers chiffrés pgp sont pris en charge)
- (préversion) L’étiquette de confidentialité n’est pas appliquée au contenu.
- (préversion) L’utilisateur a accédé à un site web sensible à partir de Edge. Pour plus d’informations, consultez [Scénario 6 Surveiller ou restreindre les activités des utilisateurs sur les domaines de service sensibles (préversion).](endpoint-dlp-using.md#scenario-6-monitor-or-restrict-user-activities-on-sensitive-service-domains)  
- L’extension de fichier est
- Le type de fichier est
- Consultez les activités de point de terminaison sur [laquelle vous pouvez surveiller et prendre des mesures](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on)

##### <a name="conditions-microsoft-defender-for-cloud-apps-supports"></a>Conditions prises en charge par Microsoft Defender for Cloud Apps

- Le contenu contient
- Le contenu est partagé à partir de Microsoft 365

##### <a name="conditions-on-premises-repositories-supports"></a>Les référentiels locaux de conditions prennent en charge

- Le contenu contient
- L’extension de fichier est
- La propriété du document est

##### <a name="conditions-powerbi-supports"></a>Conditions prises en charge par PowerBI

- Le contenu contient

#### <a name="condition-groups"></a>Groupes de conditions

Parfois, vous avez besoin d’une règle pour identifier une seule chose, comme tout le contenu qui contient un numéro de sécurité sociale des États-Unis, qui est défini par un sit unique. Toutefois, dans de nombreux scénarios, où les types d’éléments que vous essayez d’identifier sont plus complexes et, par conséquent, plus difficiles à définir, il est nécessaire de disposer d’une plus grande flexibilité dans la définition des conditions.

Par exemple, pour identifier le contenu soumis à la réglementation des États-Unis sur le Health Insurance Act (HIPAA), vous devez rechercher :
  
- Le contenu qui contient certains types d’informations sensibles, par exemple un numéro de sécurité sociale ou le numéro émis par l’agence du médicament (DEA).
    
    AND
    
- Le contenu plus difficile à identifier, comme les communications relatives aux soins du patient ou la description des services médicaux fournis. L’identification de ce contenu nécessite des mots clés correspondants à partir de listes de mots clés volumineux, telles que la Classification internationale des maladies (ICD-9-CM ou ICD-10-CM).
    
Vous pouvez identifier ce type de données en regroupant des conditions et en utilisant des opérateurs logiques (AND, OR) entre les groupes.
    
Pour la **Loi américaine sur l’assurance maladie (HIPPA),** les conditions sont regroupées comme suit :

![Conditions de stratégie HIPPA](../media/dlp-rules-condition-groups-booleans.png)

Le premier groupe contient les SIT qui identifient et individuels, et le deuxième groupe contient les SIT qui identifient le diagnostic médical.

### <a name="exceptions"></a>Exceptions

Dans les règles, les exceptions définissent des conditions utilisées pour exclure un élément de la stratégie. Logiquement, conditions exclusives qui sont évaluées après les conditions inclusives et le contexte. Ils indiquent à la règle &#8212; lorsque vous trouvez un élément qui ressemble à *ceci* et qui est utilisé comme *suit* : il s’agit d’une correspondance et les autres actions de la stratégie doivent être effectuées ***dessus, sauf si***... &#8212; 

Par exemple, en respectant la stratégie HIPPA, nous pourrions modifier la règle pour exclure tout élément qui contient un numéro de permis de conduire belge, comme suit :

![Stratégie HIPPA avec exclusions](../media/dlp-rule-exceptions.png)

Les conditions d’exception prises en charge par l’emplacement sont identiques à toutes les conditions d’inclusion, la seule différence étant l’attente de « Sauf si » pour chaque condition prise en charge. Si une règle contient uniquement des exceptions, elle s’applique à tous les e-mails ou fichiers qui ne répondent pas aux critères d’exclusion.

Tout comme tous les emplacements prennent en charge la condition inclusive :

- Le contenu contient

l’exception serait la suivante :

- **Sauf si** le contenu contient 

### <a name="actions"></a>Actions 

Tout élément qui le fait via les filtres inclus ***conditions** _ et _*_exceptions exclusives_*_ aura toutes les _*_actions_*_ définies dans la règle qui lui est appliquée. Vous devrez configurer les options requises pour prendre en charge l’action. Par exemple, si vous sélectionnez Exchange avec l’action _ *Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365**, vous devez choisir parmi les options suivantes :

- Empêcher les utilisateurs d’accéder au contenu SharePoint, OneDrive et Teams partagé
    - Bloquez tout le monde. Seuls le propriétaire du contenu, le dernier modificateur et l’administrateur de site continueront d’avoir accès
    - Bloquez uniquement les personnes extérieures à votre organisation. Les utilisateurs au sein de votre organisation continueront d’avoir accès.
- Chiffrer les courriers (applicable uniquement au contenu dans Exchange)

Les actions disponibles dans une règle dépendent des emplacements sélectionnés. Si vous sélectionnez un seul emplacement pour la stratégie à appliquer, les actions disponibles sont répertoriées ci-dessous.

> [!IMPORTANT]
> Pour SharePoint Online et OneDrive Entreprise les documents d’emplacements seront bloqués de manière proactive juste après la détection d’informations sensibles, que le document soit partagé ou non, pour tous les utilisateurs externes, tandis que les utilisateurs internes continueront d’avoir accès au document.

#### <a name="exchange-location-actions"></a>Actions d’emplacement Exchange

- Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365
- Définir des en-têtes
- Supprimer l’en-tête
- Rediriger le message vers des utilisateurs spécifiques
- Transférer le message pour approbation au responsable de l’expéditeur
- Transférer le message pour approbation à des approbateurs spécifiques
- Ajouter un destinataire à la zone À
- Ajouter un destinataire à la zone Cc
- Ajouter un destinataire à la zone CCI
- Ajouter le gestionnaire de l’expéditeur en tant que destinataire
- Suppression du chiffrement des messages O365 et de la protection des droits
- Prepend Email Subject
- Modifier Email objet
- Ajouter une clause d’exclusion de responsabilité HTML

#### <a name="sharepoint-sites-location-actions"></a>Actions d’emplacement des sites SharePoint

- Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365

#### <a name="onedrive-account-location-actions"></a>Actions d’emplacement de compte OneDrive

- Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365

#### <a name="teams-chat-and-channel-messages-actions"></a>Actions de conversation teams et de messages de canal

- Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365

#### <a name="devices-actions"></a>Actions des appareils

<!-- - Restrict access or encrypt the content in Microsoft 365 locations-->
- Auditez ou limitez les activités lorsque les utilisateurs accèdent à des sites web sensibles dans le navigateur Microsoft Edge sur les appareils Windows. Pour plus d’informations, consultez le [scénario 6 Surveiller ou restreindre les activités des utilisateurs sur des domaines de service sensibles](endpoint-dlp-using.md#scenario-6-monitor-or-restrict-user-activities-on-sensitive-service-domains) .
- Auditer ou restreindre les activités sur les appareils Windows

Pour l’utiliser `Audit or restrict activities on Windows devices`, vous devez configurer des options dans **les paramètres DLP** et dans la stratégie dans laquelle vous souhaitez les utiliser. Pour plus d’informations, consultez [applications restreintes et groupes d’applications](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) .

L’emplacement des appareils fournit de nombreuses sous-activités (conditions) et actions. Pour plus d’informations, consultez [les activités de point de terminaison sur laquelle vous pouvez surveiller et prendre des mesures](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on).

Lorsque vous sélectionnez **Auditer ou restreindre les activités sur les appareils Windows**, vous pouvez restreindre les activités utilisateur par domaine de service ou navigateur, et définir l’étendue des actions effectuées par DLP :

- Toutes les applications
- Par une liste d’applications restreintes que vous définissez
- Groupe d’applications restreint (préversion) que vous définissez.

##### <a name="service-domain-and-browser-activities"></a>Activités de domaine de service et de navigateur

Lorsque vous configurez les **domaines de service cloud Allow/Block** et la liste **des navigateurs non autorisés** (voir [Navigateur et restrictions de domaine pour les données sensibles](dlp-configure-endpoint-settings.md#browser-and-domain-restrictions-to-sensitive-data)) et qu’un utilisateur tente de charger un fichier protégé dans un domaine de service cloud ou d’y accéder à partir d’un navigateur non autorisé, vous pouvez configurer l’action de stratégie sur `Audit only`, `Block with override`ou `Block` l’activité.

##### <a name="file-activities-for-all-apps"></a>Activités de fichiers pour toutes les applications

Avec l’option **Activités de fichier pour toutes les applications** , vous sélectionnez **Ne pas restreindre les activités de fichier** ou **Appliquer des restrictions à des activités spécifiques**. Lorsque vous sélectionnez d’appliquer des restrictions à des activités spécifiques, les actions que vous sélectionnez ici sont appliquées lorsqu’un utilisateur a accédé à un élément protégé DLP. Vous pouvez indiquer à DLP , `Audit only``Block with override``Block` (les actions) sur ces activités utilisateur :

- **Copier dans le Presse-papiers**
- **Copier sur un lecteur amovible USB** 
- **Copier vers un partage réseau**
- **Print**
- **Copier ou déplacer à l’aide d’une application Bluetooth non autorisée**
- **Services de bureau à distance**


##### <a name="restricted-app-activities"></a>Activités d'application restreintes  

Précédemment appelé applications non autorisées, vous définissez une liste d’applications dans les paramètres DLP du point de terminaison sur lesquels vous souhaitez appliquer des restrictions. Lorsqu’un utilisateur tente d’accéder à un fichier protégé DLP à l’aide d’une application figurant dans la liste, vous pouvez `Audit only`soit , `Block with override`soit `Block` l’activité. Les actions DLP **définies dans les activités d’application restreintes sont remplacées** si l’application est membre d’un groupe d’applications restreint. Ensuite, les actions définies dans le groupe d’applications restreintes sont appliquées.

##### <a name="file-activities-for-apps-in-restricted-app-groups-preview"></a>Activités de fichiers pour les applications dans des groupes d’applications restreintes (préversion)

Vous définissez vos groupes d’applications restreints dans les paramètres DLP du point de terminaison et ajoutez des groupes d’applications restreints à vos stratégies. Lorsque vous ajoutez un groupe d’applications restreint à une stratégie, vous devez sélectionner l’une des options suivantes :

- Ne restreignez pas l'activité des fichiers
- Appliquer des restrictions à toutes les activités
- Appliquer des restrictions à une activité spécifique

Quand vous sélectionnez l’une des options *Appliquer les restrictions* et qu’un utilisateur tente d’accéder à un fichier protégé par DLP à l’aide d’une application qui se trouve dans le groupe d’applications restreintes, vous pouvez `Audit only`, `Block with override`ou `Block` par activité. Les actions DLP que vous définissez ici remplacent les actions **définies dans les activités d’application restreintes** et **les activités de fichier pour toutes les applications** de l’application.

Pour plus d’informations, consultez [applications restreintes et groupes d’applications](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) . 

#### <a name="microsoft-defender-for-cloud-apps-actions"></a>actions Microsoft Defender for Cloud Apps

- Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365
- Restreindre les applications tierces

#### <a name="on-premises-repositories-actions"></a>Actions de référentiels locaux

- Restreindre l’accès ou supprimer des fichiers locaux

#### <a name="powerbi-actions"></a>Actions PowerBI

- Informer les utilisateurs à l’aide de courriers électroniques et de conseils de stratégie
- Envoyer des alertes à l’administrateur

#### <a name="actions-available-when-you-combine-locations"></a>Actions disponibles lorsque vous combinez des emplacements

Si vous sélectionnez Exchange et tout autre emplacement unique pour la stratégie à appliquer, le

- Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365

et

- toutes les actions pour l’emplacement non Exchange

actions seront disponibles.

Si vous sélectionnez au moins deux emplacements non Exchange pour la stratégie à appliquer, le

- Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365

AND

- toutes les actions pour les emplacements non Exchange 

actions seront disponibles.

Par exemple, si vous sélectionnez Exchange et Appareils comme emplacements, ces actions sont disponibles :

- Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365
- Auditer ou restreindre les activités sur les appareils Windows

Si vous sélectionnez Appareils et Microsoft Defender for Cloud Apps, ces actions sont disponibles :

- Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365
- Auditer ou restreindre les activités sur les appareils Windows
- Restreindre les applications tierces

L’effet ou non d’une action dépend de la façon dont vous configurez le mode de la stratégie. Vous pouvez choisir d’exécuter la stratégie en mode test avec ou sans afficher l’info-bulle de stratégie en sélectionnant la **première option Tester** . Vous choisissez d’exécuter la stratégie dès qu’une heure après sa création en sélectionnant l’option **Activer immédiatement** , ou vous pouvez choisir de l’enregistrer et d’y revenir plus tard en sélectionnant **l’option Conserver** . 


<!-- This section needs to explain that the actions available depend on the locations selected AND that the observed behavior of a policy is produced through an interaction of the configured actions AND the configured status (off, test, apply) of a policy. It will detail the purpose of each of the available actions and the location/desired outcome interaction and provide examples eg. how to use the Restrict Third Party apps in the context of a policy that is applied to endpoints so that users can't use a upload content to a third party site or the interaction of on-premises scanner with restrict access or remove on-premises files.  Also what happens when I select multiple locations? provide abundant examples for most common scenarios-->


### <a name="user-notifications-and-policy-tips"></a>Notifications utilisateur et conseils de stratégie

<!--This section introduces the business need for user notifications, what they are, their benefit, how to use them, how to customize them, and links out to 

- https://docs.microsoft.com/en-us/microsoft-365/compliance/use-notifications-and-policy-tips?view=o365-worldwide
- https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-policy-tips-reference?view=o365-worldwide

for where they are used/expected behavior-->

<!--You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.-->

Lorsqu’un utilisateur tente une action sur un élément sensible dans un contexte qui répond aux conditions et exceptions d’une règle, vous pouvez l’informer à ce sujet via des e-mails de notification utilisateur et dans des fenêtres contextuelles de conseil de stratégie. Ces notifications sont utiles, car elles sensibilisent davantage les utilisateurs aux stratégies DLP de votre organisation.

Par exemple, du contenu tel qu’un classeur Excel sur un site OneDrive Entreprise qui contient des informations d’identification personnelle (PII) et qui est partagé avec un invité.

![La barre des messages affiche le conseil de stratégie dans Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

> [!IMPORTANT]
> - Les e-mails de notification sont envoyés sans protection.
> - Email notifications sont prises en charge uniquement pour les services Microsoft 365.

#### <a name="email-notifications-support-by-selected-location"></a>prise en charge des notifications Email par emplacement sélectionné

|Emplacement sélectionné  |notifications Email prises en charge  |
|---------|---------|
|Appareils     |- Non pris en charge         |
|Exchange + Appareils     |- Pris en charge pour Exchange </br>- Non pris en charge pour les appareils  |
|Exchange    |- Pris en charge        |
|SharePoint + Appareils  |- Pris en charge pour SharePoint </br>- Non pris en charge pour les appareils         |
|SharePoint    |- Pris en charge |
|Exchange + SharePoint    |- Pris en charge pour Exchange </br>- Pris en charge pour SharePoint  |
|Appareils + SharePoint + Exchange    |- Non pris en charge pour les appareils </br>- Pris en charge pour SharePoint </br> Pris en charge pour Exchange |
|Teams    |- Non pris en charge |
|OneDrive Entreprise   |- Pris en charge         |
|OneDrive Entreprise + Appareils     |- Pris en charge pour OneDrive Entreprise </br>- Non pris en charge pour les appareils         |
|Power-BI|- Non pris en charge|
|Microsoft Defender for Cloud Apps|- Non pris en charge|
|Référentiels locaux|- Non pris en charge|

Vous pouvez également donner aux utilisateurs la possibilité de [remplacer la stratégie](#user-overrides), afin qu’ils ne soient pas bloqués s’ils ont un besoin commercial valide ou si la stratégie détecte un faux positif.

Les options de configuration des notifications utilisateur et des conseils de stratégie varient en fonction des emplacements de surveillance que vous avez sélectionnés. Si vous avez sélectionné :

- Exchange
- SharePoint
- OneDrive
- Conversation et canal Teams
- Defender for Cloud Apps





Vous pouvez activer/désactiver les notifications utilisateur pour différentes applications Microsoft. Consultez [les informations de référence sur les conseils de stratégie de protection contre la perte de données](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)

- Vous pouvez activer/désactiver les notifications avec un conseil de stratégie.
    - notifications par e-mail à l’utilisateur qui a envoyé, partagé ou modifié pour la dernière fois le contenu OU
    - avertir des personnes spécifiques

et personnalisez le texte de l’e-mail, l’objet et le texte de l’info-bulle de stratégie.

![Options de configuration de notification utilisateur et de conseil de stratégie disponibles pour Exchange, SharePoint, OneDrive, Teams Chat and Channel et Defender for Cloud Apps](../media/dlp-user-notification-non-devices.png)

Si vous avez sélectionné Appareils uniquement, vous obtenez toutes les mêmes options disponibles pour Exchange, SharePoint, OneDrive, Teams Chat and Channel et Defender for Cloud Apps, ainsi que la possibilité de personnaliser le titre et le contenu de la notification qui s’affiche sur l’appareil Windows 10.

![Options de configuration de notification utilisateur et de conseil de stratégie disponibles pour les appareils](../media/dlp-user-notification-devices.png)  

Vous pouvez personnaliser le titre et le corps du texte à l’aide de ces paramètres. Le texte du corps prend en charge les éléments suivants :

|Nom commun  |Paramètre  |Exemple
|---------|---------|---------|
|nom du fichier     |%%FileName%% | Doc 1 de Contoso |
|nom du processus     |%%ProcessName%% | Word |
|nom de la stratégie     |%%PolicyName%%| Contoso hautement confidentiel |
|action | %%AppliedActions%% | collage du contenu du document du Presse-papiers à une autre application |

**%%AppliedActions%%** remplace ces valeurs dans le corps du message :


|nom commun de l’action |valeur remplacée par le paramètre %%AppliedActions%% |
|---------|---------|
|copier vers un stockage amovible    |*écriture dans un stockage amovible*         |
|copier sur un partage réseau     |*écriture dans un partage réseau*         |
|Imprimer     |*Impression*         |
|coller à partir du Presse-papiers  |*collage à partir du Presse-papiers*         |
|copier via bluetooth   |*transfert via Bluetooth*         |
|ouvrir avec une application non autorisée     |*ouverture avec cette application*         |
|copier sur un bureau à distance (RDP)     |*transfert vers le bureau à distance*         |
|chargement vers un site web non autorisé     |*chargement sur ce site*         |
|accès à l’élément via un navigateur non autorisé     |*ouverture avec ce navigateur*         |

Utilisation de ce texte personnalisé

*%%AppliedActions%% Le nom de fichier %%FileName%% via %%ProcessName%% n’est pas autorisé par votre organisation. Cliquez sur « Autoriser » si vous souhaitez contourner la stratégie %%PolicyName%%* 

produit ce texte dans la notification personnalisée :

*Collage à partir du nom de fichier du Presse-papiers : contoso doc 1 via WINWORD.EXE n’est pas autorisé par votre organisation. Cliquez sur le bouton « Autoriser » si vous souhaitez contourner la stratégie Contoso hautement confidentielle*
 

> [!NOTE]
> Les notifications utilisateur et les conseils de stratégie ne sont pas disponibles pour l’emplacement local

> [!NOTE]
> Uniquement le conseil de stratégie de la priorité la plus élevée, la règle la plus restrictive est affichée. Par exemple, un conseil de stratégie à partir d’une règle qui bloque l’accès au contenu est affiché sur un conseil de stratégie à partir d’une règle qui envoie simplement une notification. Cela évite que les personnes voient une cascade de conseils de stratégie.

Pour en savoir plus sur la configuration et l’utilisation des notifications utilisateur et des conseils de stratégie, notamment sur la personnalisation de la notification et du texte de l’info-bulle, consultez 
- [Envoyer des notifications par e-mail et afficher des conseils de stratégie pour les stratégies DLP](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies).
  
<!--The email can notify the person who sent, shared, or last modified the content and, for site content, the primary site collection administrator and document owner. In addition, you can add or remove whomever you choose from the email notification.
  
In addition to sending an email notification, a user notification displays a policy tip:
  
- In Outlook and Outlook on the web.
    
- For the document on a SharePoint Online or OneDrive for Business site.
    
- In Excel, PowerPoint, and Word, when the document is stored on a site included in a DLP policy.
    
The email notification and policy tip explain why content conflicts with a DLP policy. If you choose, the email notification and policy tip can allow users to override a rule by reporting a false positive or providing a business justification. This can help you educate users about your DLP policies and enforce them without preventing people from doing their work. Information about overrides and false positives is also logged for reporting (see below about the DLP reports) and included in the incident reports (next section), so that the compliance officer can regularly review this information.
  
Here's what a policy tip looks like in a OneDrive for Business account.
  
![Policy tip for a document in a OneDrive account](../media/f9834d35-94f0-4511-8555-0fe69855ce6d.png)

 To learn more about user notifications and policy tips in DLP policies, see [Use notifications and policy tips](use-notifications-and-policy-tips.md).

> [!NOTE]
> The default behavior of a DLP policy, when there is no alert configured, is not to alert or trigger. This applies only to default information types. For custom information types, the system will alert even if there is no action defined in the policy.
-->

#### <a name="blocking-and-notifications-in-sharepoint-online-and-onedrive-for-business"></a>Blocage et notifications dans SharePoint Online et OneDrive Entreprise

Ce tableau présente le comportement de blocage et de notification DLP pour les stratégies qui sont étendues à SharePoint Online et OneDrive Entreprise.

|Conditions  |Configuration des actions |Configuration de la notification utilisateur|Configuration des rapports d’incidents |Comportement de blocage et de notification|
|---------|---------|---------|---------|---------|
|- **Le contenu est partagé à partir de Microsoft 365** </br>- **avec des personnes extérieures à mon organisation**     |Aucune action n’est configurée         |- **Notifications utilisateur définies** **sur Activé** </br>- **Avertir les utilisateurs dans Office 365 service avec un conseil de stratégie** est sélectionné </br>- **Notifier l’utilisateur qui a envoyé, partagé ou modifié le contenu pour la dernière fois** est sélectionné         |- **Envoyer une alerte aux administrateurs lorsqu’une correspondance de règle est** définie **sur Activé** </br>- **Envoyer une alerte chaque fois qu’une activité correspond à la règle** définie **sur Activé** </br>- **Utiliser les rapports d’incidents par e-mail pour vous avertir lorsqu’une correspondance de stratégie est** définie **sur Activé**         |- Les notifications sont envoyées uniquement lorsqu’un fichier est partagé avec un utilisateur externe et qu’un utilisateur externe accède au fichier.  |
|- **Le contenu est partagé à partir de Microsoft 365** </br>- **uniquement avec des personnes au sein de mon organisation**        | Aucune action n’est configurée         |-  **Notifications utilisateur définies** **sur Activé**   </br>- **Avertir les utilisateurs dans Office 365 service avec un conseil de stratégie** est sélectionné  </br>- **Notifier l’utilisateur qui a envoyé, partagé ou modifié le contenu pour la dernière fois** est sélectionné    |  - **Envoyer une alerte aux administrateurs lorsqu’une correspondance de règle est** définie **sur Activé** </br>- **Envoyer une alerte chaque fois qu’une activité correspond à la règle** est sélectionnée </br>- **Utiliser les rapports d’incidents par e-mail pour vous avertir lorsqu’une correspondance de stratégie est** définie **sur Activé**       |- Les notifications sont envoyées lorsqu’un fichier est chargé |
|- **Le contenu est partagé à partir de Microsoft 365** </br>- **avec des personnes extérieures à mon organisation**    | - **Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365** est sélectionné </br>- **Empêcher les utilisateurs de recevoir des e-mails ou d’accéder aux fichiers SharePoint, OneDrive et Teams partagés** est sélectionné </br>- **Bloquer uniquement les personnes extérieures à votre organisation** est sélectionné          |- **Notifications utilisateur définies** **sur Activé** </br>- **Avertir les utilisateurs dans Office 365 service avec un conseil de stratégie** est sélectionné </br>- **Notifier l’utilisateur qui a envoyé, partagé ou modifié le contenu pour la dernière fois** est sélectionné  |  - **Envoyer une alerte aux administrateurs lorsqu’une correspondance de règle est** définie **sur Activé** </br>- **Envoyer une alerte chaque fois qu’une activité correspond à la règle** est sélectionnée </br>- **Utiliser les rapports d’incidents par e-mail pour vous avertir lorsqu’une correspondance de stratégie est** définie **sur Activé**             | - L’accès à un fichier sensible est bloqué dès qu’il est chargé </br>- Notifications envoyées lorsque du contenu est partagé à partir de Microsoft 365 avec des personnes extérieures à mon organisation         |
|- **Le contenu est partagé à partir de Microsoft 365** </br>- **avec des personnes extérieures à mon organisation** |  - **Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365** est sélectionné </br>- **Empêcher les utilisateurs de recevoir des e-mails ou d’accéder aux fichiers SharePoint, OneDrive et Teams partagés** est sélectionné </br>- **Bloquer tout le monde** est sélectionné        | - **Notifications utilisateur définies** **sur Activé** </br>- **Avertir les utilisateurs dans Office 365 service avec un conseil de stratégie** est sélectionné </br>- **Notifier l’utilisateur qui a envoyé, partagé ou modifié le contenu pour la dernière fois** est sélectionné         | - **Envoyer une alerte aux administrateurs lorsqu’une correspondance de règle est** définie **sur Activé** </br>- **Envoyer une alerte chaque fois qu’une activité correspond à la règle** est sélectionnée </br>- **Utiliser les rapports d’incidents par e-mail pour vous avertir lorsqu’une correspondance de stratégie est** définie **sur Activé**        |Les notifications sont envoyées lorsqu’un fichier est partagé avec un utilisateur externe et qu’un utilisateur externe accède à ce fichier.         |
|- **Le contenu est partagé à partir de Microsoft 365** </br>- **avec des personnes extérieures à mon organisation**     |- **Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365** est sélectionné </br>- **Bloquer uniquement les personnes qui ont reçu l’accès au contenu via l’option « Toute personne ayant le lien »** est sélectionnée.         |  - **Notifications utilisateur définies** **sur Activé** </br>- **Notifier les utilisateurs dans Office 365 service avec un conseil de stratégie** est sélectionné.  </br>- **Notifier l’utilisateur qui a envoyé, partagé ou modifié le contenu pour la dernière fois** est sélectionné     |- **Envoyer une alerte aux administrateurs lorsqu’une correspondance de règle est** définie **sur Activé**   </br>- **Envoyer une alerte chaque fois qu’une activité correspond à la règle** est sélectionnée </br>- **Utiliser les rapports d’incidents par e-mail pour vous avertir lorsqu’une correspondance de stratégie est** définie **sur Activé**       |Les notifications sont envoyées dès qu’un fichier est chargé         |


### <a name="user-overrides"></a>Remplacements par l’utilisateur

L’objectif des **remplacements d’utilisateurs** est de donner aux utilisateurs un moyen de contourner, avec justification, les actions de blocage de stratégie DLP sur les éléments sensibles dans Exchange, SharePoint, OneDrive ou Teams afin qu’ils puissent continuer leur travail. Les remplacements d’utilisateurs sont activés uniquement lorsque la notification aux **utilisateurs dans les services Office 365 avec un conseil de stratégie** est activée. Par conséquent, les remplacements utilisateur vont de pair avec les notifications et les conseils de stratégie. 

![Options de remplacement d’utilisateur pour une stratégie DLP](../media/dlp-user-overrides.png)

> [!NOTE]
> Les remplacements d’utilisateurs ne sont pas disponibles pour l’emplacement des référentiels locaux.

En règle générale, les remplacements d’utilisateurs sont utiles lorsque votre organisation déploie une stratégie pour la première fois. Les commentaires que vous obtenez à partir de toute justification de remplacement et l’identification de faux positifs vous aident à paramétrer la stratégie. 

<!-- This section covers what they are and how to best use them in conjunction with Test/Turn it on right away and link out to where to find the business justification for the override (DLP reports?  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide)  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide#view-the-justification-submitted-by-a-user-for-an-override-->

- Si les conseils de stratégie de la règle la plus restrictive autorisent les utilisateurs à remplacer la règle, toute autre règle également mise en correspondance avec le contenu est aussi remplacée.
 
<!--![User notifications and user overrides sections of DLP rule editor](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)-->
 
Pour en savoir plus sur les remplacements d’utilisateurs, consultez :

- [Afficher la justification soumise par un utilisateur pour une substitution](view-the-dlp-reports.md#view-the-justification-submitted-by-a-user-for-an-override)

### <a name="incident-reports"></a>Rapports d’incident

<!--DLP interacts with other M365 information protection services, like IR. Link this to a process outline for triaging/managing/resolving DLP incidents


https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide
https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-configure-view-alerts-policies?view=o365-worldwide-->

Lorsqu’une règle est satisfaite, vous pouvez envoyer un rapport d’incident contenant les détails de l’événement à votre responsable de la mise en conformité (ou une autre personne de votre choix). Le rapport contient des informations sur l’élément qui a été mis en correspondance, le contenu réel correspondant à la règle et le nom de la personne qui a modifié le contenu pour la dernière fois. Pour les messages électroniques, le rapport inclut également sous forme de pièce jointe le message d’origine qui correspond à une stratégie DLP.

DLP alimente les informations d’incident à d’autres services de protection des informations Microsoft Purview, tels que [la gestion des risques internes](insider-risk-management.md). Pour obtenir des informations sur les incidents à la gestion des risques internes, vous devez définir le niveau de gravité **des rapports d’incident** sur **Élevé**.

<!--![Page for configuring incident reports](../media/31c6da0e-981c-415e-91bf-d94ca391a893.png)-->

Les alertes peuvent être envoyées chaque fois qu’une activité correspond à une règle, ce qui peut être bruyant, ou elles peuvent être agrégées en moins d’alertes en fonction du nombre de correspondances ou du volume d’éléments sur une période définie.

![envoyer une alerte chaque fois qu’une règle correspond ou s’agréger au fil du temps en moins de rapports](../media/dlp-incident-reports-aggregation.png)

DLP analyse les e-mails différemment de sharePoint Online ou d’éléments OneDrive Entreprise. Dans SharePoint Online et OneDrive Entreprise, DLP analyse les éléments existants, ainsi que les nouveaux et génère un rapport d’incident chaque fois qu’une correspondance est trouvée. Dans Exchange Online, DLP analyse uniquement les nouveaux messages électroniques et génère un rapport en cas de correspondance de stratégie. DLP ***ne peut pas*** analyser ou mettre en correspondance les éléments de messagerie existants qui sont stockés dans une boîte aux lettres ou une archive.

### <a name="additional-options"></a>Options supplémentaires

Si vous avez plusieurs règles dans une stratégie, vous pouvez utiliser les **options Supplémentaires** pour contrôler le traitement ultérieur des règles s’il existe une correspondance avec la règle que vous modifiez et définir la priorité pour l’évaluation de la règle.

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Planifier la protection contre la perte de données (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md#create-a-dlp-policy-from-a-template)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
