---
title: Définition d’entité de numéro de carte de crédit
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
- tier3
- purview-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de carte de crédit.
ms.openlocfilehash: d86612e539055bb33806c7ec8bdf893755ce4877
ms.sourcegitcommit: fa570d90b00ed1bb40e1ca27b11c66a84c4204e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68476042"
---
# <a name="credit-card-number"></a>Numéro de carte de crédit

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

14 à 19 chiffres qui peuvent être mis en forme ou non mis en forme (ddddddddddddddd) et qui doivent réussir le test Luhn.

## <a name="pattern"></a>Modèle

Détecte les cartes de toutes les grandes marques, y compris Visa, MasterCard, Discover Card, JCB, American Express, cartes cadeaux, cartes de restaurant, Rupay et China UnionPay.

## <a name="checksum"></a>Somme de contrôle

Oui, la vérification Luhn

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_credit_card` trouve un contenu qui correspond au modèle.
- L’une des conditions suivantes est vraie :
  - Un mot clé figurant dans la liste `Keyword_cc_verification` est trouvé.
  - Un mot clé figurant dans la liste `Keyword_cc_name` est trouvé.
  - La fonction `Func_expiration_date` trouve une date au format correct.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_credit_card` trouve un contenu qui correspond au modèle.
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

## <a name="keywords"></a>Mots-clés

### <a name="keyword_cc_verification"></a>Keyword_cc_verification

- vérification de la carte
- numéro d’identification de la carte
- nvc
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
- cód segurança
- cod. seguranca
- cod. segurança
- cód seguranca
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
- Transaction
- numéro de transaction
- numéro de référence
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

### <a name="keyword_cc_name"></a>Keyword_cc_name

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
- dinersclub
- discover
- discover card
- discovercard
- discover cards
- Jcb
- BrandSmart
- japanese card bureau
- carte blanche
- carteblanche
- carte de crédit
- # CC
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
- numéro de carte
- cardnumbers
- numéros de carte
- creditcard
- cartes de crédit
- cartes de crédit
- ccn
- titulaire de la carte
- cardholder
- titulaires de la carte
- titulaires de la carte
- carte de vérification
- checkcard
- cartes de vérification
- cartes de vérification
- carte de débit
- debitcard
- cartes de débit
- debitcards
- carte de retrait
- atmcard
- cartes de retrait
- cartes de retrait
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
- Â¡n. carta
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
- N° de tarjeta
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
- N° do cartão
- N° do cartao
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
