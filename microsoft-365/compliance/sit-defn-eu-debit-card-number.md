---
title: Définition de l’entité du numéro de carte de débit de l’UE
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
description: Définition d’entité de type d’entité de type d’information sensible du numéro de carte de débit de l’UE.
ms.openlocfilehash: 53e7ea3475786032d2871092e3c7e6c39697958c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997750"
---
# <a name="eu-debit-card-number"></a>Numéro de carte de crédit de l'UE

## <a name="format"></a>Format

16 chiffres

## <a name="pattern"></a>Modèle

Modèle complexe et robuste

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_eu_debit_card` trouve un contenu qui correspond au modèle.
- Au moins une des affirmations suivantes est vraie :
    - Un mot clé figurant dans la liste `Keyword_eu_debit_card` est trouvé.
    - Un mot clé figurant dans la liste `Keyword_card_terms_dict` est trouvé.
    - Un mot clé figurant dans la liste `Keyword_card_security_terms_dict` est trouvé.
    - Un mot clé figurant dans la liste `Keyword_card_expiration_terms_dict` est trouvé.
    - La fonction `Func_expiration_date` trouve une date au format correct.
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

## <a name="keywords"></a>Mots-clés

### <a name="keyword_eu_debit_card"></a>Keyword_eu_debit_card

- numéro de compte
- numéro de carte
- n° carte
- numéro de sécurité
- # CC

### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

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
- cartes de retrait
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
- titulaires de la carte
- numéro de carte
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
- cartes de vérification
- chequekaart
- cirrus
- cirrus-edc-maestro
- controlekaart
- controlekaarten
- carte de crédit
- cartes de crédit
- creditcard
- cartes de crédit
- debetkaart
- debetkaarten
- carte de débit
- cartes de débit
- debitcard
- debitcards
- debito automatico
- diners club
- dinersclub
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
- maestro
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
- N° de tarjeta
- N° do cartao
- N° do cartão
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
- switch
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
- v-pay
- visa
- visa plus
- visa electron
- visto
- visum
- vpay

### <a name="keyword_card_security_terms_dict"></a>Keyword_card_security_terms_dict

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
- cryptogramme
- cryptogramme
- cv2
- cvc
- cvc2
- nvc
- cvv
- cvv2
- cód seguranca
- cód segurança
- cód seguranca
- cód segurança
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
- N° dell’edizione
- N° di sicurezza
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

### <a name="keyword_card_expiration_terms_dict"></a>Keyword_card_expiration_terms_dict

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
- expire
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
- valor
- venc
- vencimento
- vencimiento
- verloopt
- vervaldag
- vervaldatum
- vto
- válido hasta