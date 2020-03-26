---
title: Chaînes de chiffrement Office 365-DOD et GCC High
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/24/2020
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- Strat_O365_IP
description: Affichez la liste complète des certificats racines et autorités de certification DOD et GCC dans Office 365.
ms.openlocfilehash: 615a62b2ae2a954580ebf82f4c1b70748c991a71
ms.sourcegitcommit: 6adfcf042e64b21f09f2b8e072e8eba6d3479e31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "42951902"
---
# <a name="office-365-encryption-chains---dod-and-gcc-high"></a>Chaînes de chiffrement Office 365-DOD et GCC High

Office 365 tire parti d’un certain nombre de fournisseurs de certificats. Ce qui suit décrit la liste complète des certificats racines Office 365 connus que les **clients DOD et GCC High** peuvent rencontrer lors de l’accès à Office 365. Pour plus d’informations sur les certificats que vous devrez peut-être installer dans votre propre infrastructure, voir [planifier les certificats SSL tiers pour Office 365](https://docs.microsoft.com/office365/enterprise/plan-for-third-party-ssl-certificates).

Les informations de certificat suivantes s’appliquent à **tous les clients DOD et GCC High**.

>[!NOTE]
>Pour plus d’informations sur les certificats qui s’appliquent aux **clients internationaux**, consultez la rubrique [chaînes de chiffrement Office 365](encryption-office-365-certificate-chains.md).

| **Type de certificat** | **Téléchargement de la fichier. p7b** | **Points de terminaison CRL** | **Points de terminaison OCSP** |
| --- | --- | --- | --- | --- |
| Certificats racines et intermédiaires de confiance publique | [Package de certificat ITAR Office 365 (P7B)](https://download.microsoft.com/download/b/3/a/b3ae08a2-516c-46a9-8723-6256e4fd6383/O365_Chain_Certs_ITAR20200304.p7b) | crl.entrust.net<br>crl3.digicert.com<br>crl4.digicert.com | ocsp.digicert.com<br>ocsp.entrust.net |

Développez les sections racine et intermédiaire pour afficher des détails supplémentaires sur les fournisseurs de certificats.

## <a name="office-365-certificate-details"></a>**Détails du certificat Office 365**

### <a name="baltimore-cybertrust-root"></a>**Baltimore CyberTrust Root**

| **Subject** | CN = racine Baltimore CyberTrust<br>OU = CyberTrust<br>O = Baltimore<br>C = IE |
| --- | --- |
| **Numéro de série** | 02:00:00 : B9 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | 12 18:46:00 2000 mai UTC |
| **Validité non postérieure à** | 12 23:59:00 2025 mai UTC |
| **Identificateur de la clé de l’objet** | E5:9D : 59:30:82:47:58 : CC : AC : fa : 08:54:36:86:7B : 3a : B5:04:4D : F0 |
| **Empreinte numérique (SHA-1)** | D4DE20D05E66FC53FE1A50882C78DB2852CAE474 |
| **Empreinte numérique (SHA-256)** | 16AF57A9F676B0AB126095AA5EBADEF22AB31119D644AC95CD4B93DBF3F26AEB |
| **Code confidentiel (SHA-256)** | Y9mvm0exBk1JoQ57f9Vm28jKo5lFm/woKcVxrYxu80o = |

### <a name="digicert-cloud-services-ca-1"></a>**CA services Cloud DigiCert-1**

| **Subject** | CN = DigiCert cloud services CA-1<br>O = DigiCert Inc<br>C = US |
| --- | --- |
| **Issuer** | CN = DigiCert racine globale de l’autorité de certification<br>OU = www. DigiCert. com<br>O = DigiCert Inc<br>C = US |
| **Numéro de série** | 01:9E : C1 : C6 : BD : 3F : 9:7B : B2:0C : 33:38 : E5:51 : D8:77 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Août 04 12:00:00 2015 UTC |
| **Validité non postérieure à** | Août 04 12:00:00 2030 UTC |
| **Identificateur de la clé de l’objet** | DD : 51 : D0 : a2:31:73 : A9:73 : AE : 8F : B4:01:7e : 5D : 8c : 57 : CB : 9F : F0 : F7 |
| **Identificateur de la clé de l’autorité** | KeyId : 03 : de : 50:35:56 : D1:4 quater : BB : 66 : F0 : a3 : E2:1b : 1b : C3:97 : B2:3D : D1:55 |
| **Empreinte numérique (SHA-1)** | 81B68D6CD2F221F8F534E677523BB236BBA1DC56 |
| **Empreinte numérique (SHA-256)** | 2F6889961A7CA7067E8BA103C2CF9B9A924F8CA293F11178E23A1978D2F133D3 |
| **Code confidentiel (SHA-256)** | UgpUVparimk8QCjtWQaUQ7EGrtrykc/L8N66EhFY3VE = |
| **URL de liste de révocation** | http://crl4.digicert.com/DigiCertGlobalRootCA.crl<br>http://crl3.digicert.com/DigiCertGlobalRootCA.crl |
| **URL OCSP** | http://ocsp.digicert.com |

### <a name="digicert-global-root-ca"></a>**Autorité de certification racine globale DigiCert**

| **Subject** | CN = DigiCert racine globale de l’autorité de certification<br>OU = www. DigiCert. com<br>O = DigiCert Inc<br>C = US |
| --- | --- |
| **Numéro de série** | 08:3B : E0:56:90:42:46 : B1 : A1:75:6A : C9:59:91 : C7:4A |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | Nov 10 00:00:00 2006 UTC |
| **Validité non postérieure à** | Nov 10 00:00:00 2031 UTC |
| **Identificateur de la clé de l’objet** | 03 : de : 50:35:56 : D1:4 quater : BB : 66 : F0 : a3 : E2:1b : 1b : C3:97 : B2:3D : D1:55 |
| **Identificateur de la clé de l’autorité** | KeyId : 03 : de : 50:35:56 : D1:4 quater : BB : 66 : F0 : a3 : E2:1b : 1b : C3:97 : B2:3D : D1:55 |
| **Empreinte numérique (SHA-1)** | A8985D3A65E5E5C4B2D7D66D40C6DD2FB19C5436 |
| **Empreinte numérique (SHA-256)** | 4348A0E9444C78CB265E058D5E8944B4D84F9662BD26DB257F8934A443C70161 |
| **Code confidentiel (SHA-256)** | r/mIkG3eEpVdm + u/Ko/cwxzOMo1bk4TyHIlByibiA5E = |

### <a name="digicert-high-assurance-ev-root-ca"></a>**Autorité de certification racine EV de l’assurance haute DigiCert**

| **Subject** | CN = autorité de certification racine EV de l’assurance haute DigiCert<br>OU = www. DigiCert. com<br>O = DigiCert Inc<br>C = US |
| --- | --- |
| **Numéro de série** | 02 : AC : 5C : 26:6A : 0B : 40:9B : 8F : 0B : 79 : F2 : AE : 46:25:77 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | Nov 10 00:00:00 2006 UTC |
| **Validité non postérieure à** | Nov 10 00:00:00 2031 UTC |
| **Identificateur de la clé de l’objet** | B1:3e : C3:69:03 : F8 : BF : 47:01 : D4:98:26:1a : 08:02 : EF : 63:64:2b : C3 |
| **Identificateur de la clé de l’autorité** | KeyId : B1:3e : C3:69:03 : F8 : BF : 47:01 : D4:98:26:1a : 08:02 : EF : 63:64:2b : C3 |
| **Empreinte numérique (SHA-1)** | 5FB7EE0633E259DBAD0C4C9AE6D38F1A61C7DC25 |
| **Empreinte numérique (SHA-256)** | 7431E5F4C3C1CE4690774F0B61E05440883BA9A01ED00BA6ABD7806ED3B118CF |
| **Code confidentiel (SHA-256)** | WoiWRyIOVNa9ihaBciRSC7XHjliYS9VwUGOIud4PB18 = |

### <a name="digicert-sha2-extended-validation-server-ca"></a>**DigiCert SHA2 étendue de l’autorité de certification du serveur de validation étendue**

| **Subject** | CN = DigiCert SHA2 étendue de l’autorité de certification du serveur de validation étendue<br>OU = www. DigiCert. com<br>O = DigiCert Inc<br>C = US |
| --- | --- |
| **Numéro de série** | 0C : 79 : A9:44 : B0:8C : 11:95:20:92:61:5F : E2:6B : 1J : 83 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Octobre 22 00:00:00 2013 UTC |
| **Validité non postérieure à** | Octobre 22 00:00:00 2028 UTC |
| **Identificateur de la clé de l’objet** | 3D : D3:50 : A5 : D6 : A0 : AD : EE : F3:4A : 60:0A : 65 : D3:21 : D4 : F8 : F8 : D6:0F |
| **Identificateur de la clé de l’autorité** | keyID : B1:3e : C3:69:03 : F8 : BF : 47:01 : D4:98:26:1a : 08:02 : EF : 63:64:2b : C3 |
| **Empreinte numérique (SHA-1)** | 7E2F3A4F8FE8FA8A5730AECA029696637E986F3F |
| **Empreinte numérique (SHA-256)** | 403E062A2653059113285BAF80A0D4AE422C848C9F78FAD01FC94BC5B87FEF1A |

### <a name="entrust-root-certification-authority"></a>**Autorité de certification racine Entrust**

| **Subject** | CN = autorité de certification racine Entrust<br>OU = "(c) 2006 Entrust, Inc."<br>OU = www. Entrust. net/CPS est incorporée par référence<br>OU = voir www.entrust.net/legal-terms<br>O =&quot;Entrust, Inc.&quot;<br>C = US |
| --- | --- |
| **Numéro de série** | 45:6B : 50:54 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | Nov 27 12:23:42 2006 UTC |
| **Validité non postérieure à** | Nov 27 12:53:42 2026 UTC |
| **Identificateur de la clé de l’objet** | 68:90 : E4:67 : A4 : A6:53:80 : C7:86:66 : A4 : F1 : F7:4B : 43 : FB : 84 : BD : 6D |
| **Identificateur de la clé de l’autorité** | keyID : 68:90 : E4:67 : A4 : A6:53:80 : C7:86:66 : A4 : F1 : F7:4b : 43 : FB : 84 : BD : 6D |
| **Empreinte numérique (SHA-1)** | B31EB1B740E36C8402DADC37D44DF5D4674952F9 |
| **Empreinte numérique (SHA-256)** | 73C176434F1BC6D5ADF45B0E76E727287C8DE57616C1E6E6141A2B2CBC7D8E4C |

### <a name="entrust-root-certification-authority---g2"></a>**Autorité de certification racine Entrust-G2**

| **Subject** | CN = autorité de certification racine Entrust-G2<br>OU =&quot;(c) 2009 Entrust, Inc.-pour une utilisation autorisée uniquement&quot;<br>OU = voir www.entrust.net/legal-terms<br>O =&quot;Entrust, Inc.&quot;<br>C = US |
| --- | --- |
| **Numéro de série** | 4A : 53:8C : 28 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | 07 17:25:54 2009 juillet (UTC) |
| **Validité non postérieure à** | Dec 07 17:55:54 2030 UTC |
| **Identificateur de la clé de l’objet** | 6A : 72:26:7A : D0:1e : EF : 7D : E7:3b : 69:51 : D4:6C : 8D : 9F : 90:12:66 : ab |
| **Empreinte numérique (SHA-1)** | 8CF427FD790C3AD166068DE81E57EFBB932272D4 |
| **Empreinte numérique (SHA-256)** | 43DF5774B03E7FEF5FE40D931A7BEDF1BB2E6B42738C4E6D3841103D3AA7F339 |
| **Code confidentiel (SHA-256)** | du6FkDdMcVQ3u8prumAo6t3i3G27uMP2EOhR8R0at/U = |

### <a name="entrustnet-certification-authority-2048"></a>**Entrust.net Certification Authority (2048)**

| **Subject** | CN = Entrust. net Certification Authority (2048)<br>OU = (c) 1999 Entrust.net limité<br>OU = www. Entrust. net/CPS\_2048 Incorp. par Réf. (Limitez s Liab.)<br>O = Entrust. net |
| --- | --- |
| **Numéro de série** | 38:63 : DE : F8 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | Dec 24 17:50:51 1999 UTC |
| **Validité non postérieure à** | 24 14:15:12 2029 juillet (UTC) |
| **Identificateur de la clé de l’objet** | 55 : E4:81 : D1:11:80 : be : D8:89 : B9:08 : a3:31 : F9 : a1:24:09:16 : B9:70 |
| **Empreinte numérique (SHA-1)** | 503006091D97D4F5AE39F7CBE7927D7D652D3431 |
| **Empreinte numérique (SHA-256)** | 6DC47172E01CBCB0BF62580D895FE2B8AC9AD4F873801E0C10B9C837D21EB177 |
| **Code confidentiel (SHA-256)** | HqPF5D7WbC2imDpCpKebHpBnhs6fG1hiFBmgBGOofTg = |

### <a name="entrust-certification-authority---l1c"></a>**Autorité de certification Entrust-L1C**

| **Subject** | CN = autorité de certification Entrust-L1C<br>OU =&quot;(c) 2009 Entrust, Inc.&quot;<br>OU = www. Entrust. net/RPA est incorporée par référence<br>O =&quot;Entrust, Inc.&quot;<br>C = US |
| --- | --- |
| **Issuer** | CN = Entrust. net Certification Authority (2048)<br>OU = (c) 1999 Entrust.net limité<br>OU = www. Entrust. net/CPS\_2048 Incorp. par Réf. (limite Liab.)<br>O = Entrust. net |
| **Numéro de série** | 4C : 0E : 8C : 39 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | Nov 11 15:40:40 2011 UTC |
| **Validité non postérieure à** | Nov 11 02:51:17 2021 UTC |
| **Identificateur de la clé de l’objet** | 1e : F1 : AB : 89:06 : F8:49:0F : 01:33:77 : EE : 14:7A : EE : 19:7C : 93:28:4D |
| **Identificateur de la clé de l’autorité** | KeyId : 55 : E4:81 : D1:11:80 : be : D8:89 : B9:08 : a3:31 : F9 : a1:24:09:16 : B9:70 |
| **Empreinte numérique (SHA-1)** | C53E73073F93CE7895DE7484126BC303DAB9E657 |
| **Empreinte numérique (SHA-256)** | 0EE4DAF71A85D842D23F4910FD4C909B7271861931F1D5FEAC868225F52700E2 |
| **Code confidentiel (SHA-256)** | VFv5NemtodoRftw8KsvFb8AoCWwOJL6bOJS + Ui0bQ94 = |
| **URL de liste de révocation** | http://crl.entrust.net/2048ca.crl |
| **URL OCSP** | http://ocsp.entrust.net |

### <a name="entrust-certification-authority---l1e"></a>**Autorité de certification Entrust-L1E**

| **Subject** | CN = autorité de certification Entrust-L1E<br>OU =&quot;(c) 2009 Entrust, Inc.&quot;<br>OU = www. Entrust. net/RPA est incorporée par référence<br>O =&quot;Entrust, Inc.&quot;<br>C = US |
| --- | --- |
| **Issuer** | CN = Entrust. net Certification Authority (2048)<br>OU = (c) 1999 Entrust.net limité<br>OU = www. Entrust. net/CPS\_2048 Incorp. par Réf. (limite Liab.)<br>O = Entrust. net |
| **Numéro de série** | 4C : 0E : C9:18 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | Nov 11 15:40:40 2011 UTC |
| **Validité non postérieure à** | Nov 11 02:51:17 2021 UTC |
| **Identificateur de la clé de l’objet** | 5B : 41:8A : B2 : C4:43 : C1 : BD : BF : C8:54:41:55:9D : E0:96 : AD : FF : B9 : A1 |
| **Identificateur de la clé de l’autorité** | KeyId : 68:90 : E4:67 : A4 : A6:53:80 : C7:86:66 : A4 : F1 : F7:4b : 43 : FB : 84 : BD : 6D |
| **Empreinte numérique (SHA-1)** | 8A000CC056F7D17349F045BEB0319A3B91C9F979 |
| **Empreinte numérique (SHA-256)** | 3C7A634E5778A0F731972B702DAE24B2CF2060219F607E69878B164C61A06C41 |
| **URL de liste de révocation** | http://crl.entrust.net/rootca1.crl |
| **URL OCSP** | http://ocsp.entrust.net |

### <a name="entrust-certification-authority---l1k"></a>**Autorité de certification Entrust-L1K**

| **Subject** | CN = autorité de certification Entrust-L1K<br>OU =&quot;(c) 2012 Entrust, Inc.-pour une utilisation autorisée uniquement&quot;<br>OU = voir www.entrust.net/legal-terms<br>O =&quot;Entrust, Inc.&quot;<br>C = US |
| --- | --- |
| **Issuer** | CN = autorité de certification racine Entrust-G2<br>OU =&quot;(c) 2009 Entrust, Inc.-pour une utilisation autorisée uniquement&quot;<br>OU = voir www.entrust.net/legal-terms<br>O =&quot;Entrust, Inc.&quot;<br>C = US |
| **Numéro de série** | 0E : E9:4C : C3:00:00:00:00:00:51 : D3:77:85 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Octobre 05 19:13:56 2015 UTC |
| **Validité non postérieure à** | DEC 05 19:43:56 2030 UTC |
| **Identificateur de la clé de l’objet** | 82 : a2:70:74 : DD : BC : 53:3F : cf : 7B : D4 : F7 : CD : 7F : A7:60 : C6:0A : 4C : BF |
| **Identificateur de la clé de l’autorité** | KeyId : 6A : 72:26:7A : D0:1e : EF : 7D : E7:3b : 69:51 : D4:6C : 8D : 9F : 90:12:66 : ab |
| **Empreinte numérique (SHA-1)** | F21C12F46CDB6B2E16F09F9419CDFF328437B2D7 |
| **Empreinte numérique (SHA-256)** | 13EFB39A2F6654E8C67BD04F4C6D4C90CD6CAB5091BCEDC73787F6B77D3D3FE7 |
| **Code confidentiel (SHA-256)** | 980Ionqp3wkYtN9SZVgMzuWQzJta1nfxNPwTem1X0uc = |
| **URL de liste de révocation** | http://crl.entrust.net/g2ca.crl |
| **URL OCSP** | http://ocsp.entrust.net |

### <a name="entrust-certification-authority---l1m"></a>**Autorité de certification Entrust-L1M**

| **Subject** | CN = Entrust autorité de certification-L1M, OU&quot;= (c) 2014 Entrust, Inc.-pour usage autorisé uniquement&quot;<br>OU = voir www.entrust.net/legal-terms<br>O =&quot;Entrust, Inc.&quot;<br>C = US |
| --- | --- |
| **Issuer** | CN = autorité de certification racine Entrust-G2<br>OU =&quot;(c) 2009 Entrust, Inc.-pour une utilisation autorisée uniquement&quot;<br>OU = voir www.entrust.net/legal-terms<br>O =&quot;Entrust, Inc.&quot;<br>C = US |
| **Numéro de série** | 61 : A1 : E7 : D2:00:00:00:00:51 : D3:66 : A6 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Dec 15 07:25:03 2014 UTC |
| **Validité non postérieure à** | Octobre 15 08:55:03 2030 UTC |
| **Identificateur de la clé de l’objet** | C3 : F7 : D0 : B5:2A : 30 : AD : AF : 0D : 91:21:70:39:54 : DD : BC : 89:70 : C7:3A |
| **Identificateur de la clé de l’autorité** | KeyId : 6A : 72:26:7A : D0:1e : EF : 7D : E7:3b : 69:51 : D4:6C : 8D : 9F : 90:12:66 : ab |
| **Empreinte numérique (SHA-1)** | CC136695639065FAB47074D28C55314C66077E90 |
| **Empreinte numérique (SHA-256)** | 75C5B3F01FD1F51A2C447AB7C785D72E69FA9C472C08571E7EADF3B8EABAE70C |
| **URL de liste de révocation** | http://crl.entrust.net/g2ca.crl |
| **URL OCSP** | http://ocsp.entrust.net |

### <a name="microsoft-it-tls-ca-1"></a>**Autorité de certification Microsoft IT TLS 1**

| **Subject** | CN = autorité de certification Microsoft IT TLS 1<br>OU = Microsoft IT<br>O = Microsoft Corporation<br>L = Redmond<br>S = Washington<br>C = US |
| --- | --- |
| **Issuer** | CN = racine Baltimore CyberTrust<br>OU = CyberTrust<br>O = Baltimore<br>C = IE |
| **Numéro de série** | 08 : B8:7 A : 50:1B : BE : 9C : DA : 2D : 16:4D : 3E : 39:51 : BF : 55 |
| **Longueur de la clé publique** | RSA 4096 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | 20 12:51:28 2016 mai UTC |
| **Validité non postérieure à** | 20 12:51:28 2024 mai UTC |
| **Identificateur de la clé de l’objet** | 58:88:9F : D6 : DC : 9C : 48:22 : B7:14:3e : FF : 84:88 : E8 : E6:85 : FF : fa : 7D |
| **Identificateur de la clé de l’autorité** | KeyId : E5:9D : 59:30:82:47:58 : CC : AC : fa : 08:54:36:86:7B : 3a : B5:04:4D : F0 |
| **Empreinte numérique (SHA-1)** | 417E225037FBFAA4F95761D5AE729E1AEA7E3A42 |
| **Empreinte numérique (SHA-256)** | 4FF404F02E2CD00188F15D1C00F4B6D1E38B5A395CF85314EAEBA855B6A64B75 |
| **Code confidentiel (SHA-256)** | xjXxgkOYlag7jCtR5DreZm9b61iaIhd + J3 + b2LiybIw = |
| **URL de liste de révocation** | http://crl3.digicert.com/Omniroot2025.crl |
| **URL OCSP** | http://ocsp.digicert.com |

### <a name="microsoft-it-tls-ca-2"></a>**Autorité de certification Microsoft IT TLS 2**

| **Subject** | CN = autorité de certification Microsoft IT TLS 2<br>OU = Microsoft IT<br>O = Microsoft Corporation<br>L = Redmond<br>S = Washington<br>C = US |
| --- | --- |
| **Issuer** | CN = racine Baltimore CyberTrust<br>OU = CyberTrust<br>O = Baltimore<br>C = IE |
| **Numéro de série** | 0F : 2C : 10 : C9:5B : (06) : C0:93:7F : B8 : D4:49 : F8:3E : DE 85:69 |
| **Longueur de la clé publique** | RSA 4096 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | 20 12:51:57 2016 mai UTC |
| **Validité non postérieure à** | 20 12:51:57 2024 mai UTC |
| **Identificateur de la clé de l’objet** | 91:9 e : 3b : 44:6C : 3D : 57:9C : 42:77:2a : 34 : D7:4F : D1 : CC : 4a : 97:2C : da |
| **Identificateur de la clé de l’autorité** | KeyId : E5:9D : 59:30:82:47:58 : CC : AC : fa : 08:54:36:86:7B : 3a : B5:04:4D : F0 |
| **Empreinte numérique (SHA-1)** | 54D9D20239080C32316ED9FF980A48988F4ADF2D |
| **Empreinte numérique (SHA-256)** | 4E107C981B42ACBE41C01067E16D44DB64814D4193E572317EA04B87C79C475F |
| **Code confidentiel (SHA-256)** | wBdPad95AU7OgLRs0FU/E6ILO1MSCM84kJ9y0H + TT7s = |
| **URL de liste de révocation** | http://crl3.digicert.com/Omniroot2025.crl |
| **URL OCSP** | http://ocsp.digicert.com |

### <a name="microsoft-it-tls-ca-4"></a>**Autorité de certification Microsoft IT TLS 4**

| **Subject** | CN = autorité de certification Microsoft IT TLS 4<br>OU = Microsoft IT<br>O = Microsoft Corporation<br>L = Redmond<br>S = Washington<br>C = US |
| --- | --- |
| **Issuer** | CN = racine Baltimore CyberTrust<br>OU = CyberTrust<br>O = Baltimore<br>C = IE |
| **Numéro de série** | 0B : 6A : B3 : B0:3E : B1 : A9 : F6 : C4:60:92:6A : A8 : CD : FE : B3 |
| **Longueur de la clé publique** | RSA 4096 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | 20 12:52:38 2016 mai UTC |
| **Validité non postérieure à** | 20 12:52:38 2024 mai UTC |
| **Identificateur de la clé de l’objet** | 7A : 7B : 8c : C1 : cf : E7 : ca : 1C : D4:6B : fa : FB : E1:33 : C3:0F : 1a : a2:9D |
| **Identificateur de la clé de l’autorité** | KeyId : E5:9D : 59:30:82:47:58 : CC : AC : fa : 08:54:36:86:7B : 3a : B5:04:4D : F0 |
| **Empreinte numérique (SHA-1)** | 8A38755D0996823FE8FA3116A277CE446EAC4E99 |
| **Empreinte numérique (SHA-256)** | 5FFAC43E0DDC5B4AF2B696F6BC4DB7E91DF314BB8FE0D0713A0B1A7AD2A68FAC |
| **Code confidentiel (SHA-256)** | wUY9EOTJmS7Aj4fDVCu/KeE + + mV7FgIcbn4WhMz1I2k = |
| **URL de liste de révocation** | http://crl3.digicert.com/Omniroot2025.crl |
| **URL OCSP** | http://ocsp.digicert.com |

### <a name="microsoft-it-tls-ca-5"></a>**Autorité de certification Microsoft IT TLS 5**

| **Subject** | CN = autorité de certification Microsoft IT TLS 5<br>OU = Microsoft IT<br>O = Microsoft Corporation<br>L = Redmond<br>S = Washington<br>C = US |
| --- | --- |
| **Issuer** | CN = racine Baltimore CyberTrust<br>OU = CyberTrust<br>O = Baltimore<br>C = IE |
| **Numéro de série** | 08:88 : CD : 52:5F : 19:24:44:4D : 14 : A5:82:91 : DE : B9:52 |
| **Longueur de la clé publique** | RSA 4096 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | 20 12:53:03 2016 mai UTC |
| **Validité non postérieure à** | 20 12:53:03 2024 mai UTC |
| **Identificateur de la clé de l’objet** | 08 : Fe : 25:9F : 74 : AE : 87:04 : C2 : BC : BB : 8e : A8:38:5F : 33 : C6 : D1:6C : 65 |
| **Identificateur de la clé de l’autorité** | KeyId : E5:9D : 59:30:82:47:58 : CC : AC : fa : 08:54:36:86:7B : 3a : B5:04:4D : F0 |
| **Empreinte numérique (SHA-1)** | AD898AC73DF333EB60AC1F5FC6C4B2219DDB79B7 |
| **Empreinte numérique (SHA-256)** | F0EE5914ED94C7252D058B4E39808AEE6FA8F62CF0974FB7D6D2A9DF16E3A87F |
| **Code confidentiel (SHA-256)** | RCbqB + W8nwjznTeP4O6VjqcwdxIgI79eBpnBKRr32gc = |
| **URL de liste de révocation** | http://crl3.digicert.com/Omniroot2025.crl |
| **URL OCSP** | http://ocsp.digicert.com |
