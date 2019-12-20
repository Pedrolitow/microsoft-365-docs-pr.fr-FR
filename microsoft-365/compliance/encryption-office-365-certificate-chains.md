---
title: Chaînes de chiffrement Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/19/2019
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
description: Affichez la liste complète des certificats racines et des autorités de certification dans Office 365.
ms.openlocfilehash: 8cbb36afc5cb28e2eeea7aa87957cedade2e5f30
ms.sourcegitcommit: 0ad0092d9c5cb2d69fc70c990a9b7cc03140611b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "40807700"
---
# <a name="office-365-encryption-chains"></a>Chaînes de chiffrement Office 365

Office 365 tire parti d’un certain nombre de fournisseurs de certificats. La liste complète des certificats racines Office 365 connus que les clients peuvent rencontrer lors de l’accès à Office 365 est décrite ci-dessous. Pour plus d’informations sur les certificats que vous devrez peut-être installer dans votre propre infrastructure, voir [planifier les certificats SSL tiers pour Office 365](https://docs.microsoft.com/office365/enterprise/plan-for-third-party-ssl-certificates). Les informations de certificat suivantes s’appliquent à toutes les instances mondiales et nationales de Cloud d’Office 365.

**Clients ITAR (défense & GCC High) :** veuillez contacter votre responsable TAM ou votre SDM pour le package.

| **Type de certificat** | **Téléchargement de la fichier. p7b** | **Points de terminaison CRL** | **Points de terminaison OCSP** | **Points de terminaison AIA** |
| --- | --- | --- | --- | --- |
| Certificats racines de confiance publique | [Fichier groupé de certificat racine Office 365 (P7B)](https://download.microsoft.com/download/A/5/A/A5AE01F3-D19B-4A11-9407-801263CEF72C/O365_Root_Certs_20170321.p7b) | crl.globalsign.net<br>www.d-trust.net | N/A | N/A |
| Certificats intermédiaires de confiance publique | [Fichier groupé de certificat intermédiaire Office 365 (P7B)](https://download.microsoft.com/download/4/D/5/4D5339A4-0A4A-46AB-AE52-B179DEDA4BEC/O365_Intermediate_Certs_20170321.p7b) | cdp1.public-trust.com<br>crl.cnnic.cn<br>crl.entrust.net<br>crl.globalsign.com<br>crl.globalsign.net<br>crl.identrust.com<br>crl.thawte.com<br>crl3.digicert.com<br>crl4.digicert.com<br>s1.symcb.com<br>www.d-trust.net | isrg.trustid.ocsp.identrust.com<br>ocsp.digicert.com<br>ocsp.entrust.net<br>ocsp.globalsign.com<br>ocsp.omniroot.com<br>ocsp.startssl.com<br>ocsp.thawte.com<br>ocsp2.globalsign.com<br>ocspcnnicroot.cnnic.cn<br>root-c3-ca2-2009.ocsp.d-trust.net<br>root-c3-ca2-ev-2009.ocsp.d-trust.net<br>s2.symcb.com | aia.startssl.com<br>apps.identrust.com<br>cacert.omniroot.com<br>www.cnnic.cn |

Développez les sections racine et intermédiaire pour afficher des détails supplémentaires sur les fournisseurs de certificats.

## <a name="office-365-root-certificate-details"></a>**Détails du certificat racine Office 365**

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

### <a name="cnnic-root"></a>**RACINE CNNIC**

| **Subject** | CN = RACINE CNNIC<br>O = CNNIC<br>C = CN |
| --- | --- |
| **Numéro de série** | 49:33:00:01 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | Avr 16 07:09:14 2007 UTC |
| **Validité non postérieure à** | Avr 16 07:09:14 2027 UTC |
| **Identificateur de la clé de l’objet** | 65 : F2:31 : AD :-2a : F7 : F7 : DD : 52:96:0A : C7:02 : C1:0E : EF : A6 : D5:3b : 11 |
| **Identificateur de la clé de l’autorité** | KeyId : 65 : F2:31 : AD :-2a : F7 : F7 : DD : 52:96:0A : C7:02 : C1:0E : EF : A6 : D5:3b : 11 |
| **Empreinte numérique (SHA-1)** | 8BAF4C9B1DF02A92F7DA128EB91BACF498604B6F |
| **Empreinte numérique (SHA-256)** | E28393773DA845A679F2080CC7FB44A3B7A1C3792CB7EB7729FDCB6A8D99AEA7 |
| **Code confidentiel (SHA-256)** | H0IkzshPyZztiB/2/P0 + IfjFGcVHqmpd094kcwLOUNE = |

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

### <a name="d-trust-root-class-3-ca-2-2009"></a>**D-TRUST racine de la classe 3 CA 2 2009**

| **Subject** | CN = D-TRUST racine de la classe 3 CA 2 2009<br>O = D-Trust GmbH<br>C = DE |
| --- | --- |
| **Numéro de série** | 09:83 : F3 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Nov 05 08:35:58 2009 UTC |
| **Validité non postérieure à** | Nov 05 08:35:58 2029 UTC |
| **Identificateur de la clé de l’objet** | FD : da : 14 : C4:9F : 30 : de : 21 : BD : 1e : 42:39 : FC : AB : 63:23:49 : E0 : F1:84 |
| **Empreinte numérique (SHA-1)** | 58E8ABB0361533FB80F79B1B6D29D3FF8D5F00F0 |
| **Empreinte numérique (SHA-256)** | 49E7A442ACF0EA6287050054B52564B650E4F49E42E348D6AA38E039E957B1C1 |
| **Code confidentiel (SHA-256)** | 7KDxgUAs56hlKzG00DbfJH46MLf0GlDZHsT5CwBrQ6E = |
| **URL de liste de révocation** | ldap://directory.d-trust.net/CN=D-TRUST%20Root%20Class%203%20CA%202%202009,O=D-Trust%20GmbH,C=DE?certificaterevocationlist<br>http://www.d-trust.net/crl/d-trust\_root\_class\_3\_ca\_2\_2009.crl |

### <a name="d-trust-root-class-3-ca-2-ev-2009"></a>**D-TRUST racine de la classe 3 CA 2 EV 2009**

| **Subject** | CN = D-TRUST racine de la classe 3 CA 2 EV 2009<br>O = D-Trust GmbH<br>C = DE |
| --- | --- |
| **Numéro de série** | 09:83 : F4 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Nov 05 08:50:46 2009 UTC |
| **Validité non postérieure à** | Nov 05 08:50:46 2029 UTC |
| **Identificateur de la clé de l’objet** | D3:94:8A : 4C : 62:13:2a : 19:2e : CC : AF : 72:8A : 7D : 36 : D7:9A : 1C : DC : 67 |
| **Empreinte numérique (SHA-1)** | 96C91B0B95B4109842FAD0D82279FE60FAB91683 |
| **Empreinte numérique (SHA-256)** | EEC5496B988CE98625B934092EEC2908BED0B0F316C2D4730C84EAF1F3D34881 |
| **Code confidentiel (SHA-256)** | /zQvtsTIvTCkcG9zSJU58Z5uSMwF9GJUZU9mENvFQOk = |
| **URL de liste de révocation** | ldap://directory.d-trust.net/CN=D-TRUST%20Root%20Class%203%20CA%202%20EV%202009,O=D-Trust%20GmbH,C=DE?certificaterevocationlist<br>http://www.d-trust.net/crl/d-trust\_root\_class\_3\_ca\_2\_ev\_2009.crl |

### <a name="dst-root-ca-x3"></a>**Autorité de certification racine x3 DST**

| **Subject** | CN = autorité de certification racine x3<br>O = approbation de signature numérique Co. |
| --- | --- |
| **Numéro de série** | 44 : AF : B0:80 : D6 : A3:27 : BA : 89:30:39:86:2E : F8:40:6B |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | Sep 30 21:12:19 2000 UTC |
| **Validité non postérieure à** | Sep 30 14:01:15 2021 UTC |
| **Identificateur de la clé de l’objet** | C4 : A7 : B1 : A4:7B : 2C : 71 : fa : DB : E1:4b : 90:75 : FF : C4:15:60:85:89:10 |
| **Empreinte numérique (SHA-1)** | DAC9024F54D8F6DF94935FB1732638CA6AD77C13 |
| **Empreinte numérique (SHA-256)** | 0687260331A72403D909F105E69BCF0D32E1BD2493FFC6D9206D11BCD6770739 |
| **Code confidentiel (SHA-256)** | Vjs8r4z + 80wjNcr1YKepWQboSIRi63WsWXhIMN + eWys = |

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

### <a name="globalsign"></a>**GlobalSign**

| **Subject** | CN = GlobalSign<br>O = GlobalSign<br>OU = GlobalSign racine CA-R2 |
| --- | --- |
| **Numéro de série** | 04:00:00:00:00:01:0F : 86:26 : E6:0D |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | Dec 15 08:00:00 2006 UTC |
| **Validité non postérieure à** | Dec 15 08:00:00 2021 UTC |
| **Identificateur de la clé de l’objet** | 9B : E2:07:57:67:1C : 1e : C0:6A : 06 : de : 59 : B4:9A : 2D : DF : DC : 19:86:2e |
| **Identificateur de la clé de l’autorité** | KeyId : 9B : E2:07:57:67:1C : 1e : C0:6A : 06 : de : 59 : B4:9A : 2D : DF : DC : 19:86:2e |
| **Empreinte numérique (SHA-1)** | 75E0ABB6138512271C04F85FDDDE38E4B7242EFE |
| **Empreinte numérique (SHA-256)** | CA42DD41745FD0B81EB902362CF9D8BF719DA1BD1B1EFC946F5B4C99F42C1B9E |
| **Code confidentiel (SHA-256)** | iie1VXtL7HzAMF +/PVPR9xzT80kQxdZeJ + zduCB3uj0 = |
| **URL de liste de révocation** | http://crl.globalsign.net/root-r2.crl |

### <a name="globalsign-root-ca"></a>**GlobalSign Root CA**

| **Subject** | CN = autorité de certification racine GlobalSign<br>OU = AC racine<br>O = GlobalSign NV-sa<br>C = BE |
| --- | --- |
| **Numéro de série** | 04:00:00:00:00:01:15:4B : 5A : C3:94 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | Sep 01 12:00:00 1998 UTC |
| **Validité non postérieure à** | Janvier 28 12:00:00 2028 UTC |
| **Identificateur de la clé de l’objet** | 60:7B : 66:1a : 45:0d : 97 : ca : 89:50:2F : 7D : 04 : CD : 34 : A8 : FF : FC : FD : 4b |
| **Empreinte numérique (SHA-1)** | B1BC968BD4F49D622AA89A81F2150152A41D829C |
| **Empreinte numérique (SHA-256)** | EBD41040E4BB3EC742C9E381D31EF2A41A48B6685C96E7CEF3C1DF6CD4331C99 |
| **Code confidentiel (SHA-256)** | K87oWBWM9UZfyddvDfoxL + 8lpNyoUB2ptGtn0fv6G2Q = |

### <a name="thawte-primary-root-ca---g3"></a>**AUTORITÉ racine principale Thawte-G3**

| **Subject** | CN = autorité racine principale Thawte-G3<br>OU =&quot;(c) 2008 Thawte, Inc.-pour utilisation autorisée uniquement&quot;<br>OU = Division des services de certification<br>O =&quot;Thawte, Inc.&quot;<br>C = US |
| --- | --- |
| **Numéro de série** | 60:01:97 : B7:46 : A7 (EA) : EA : B4 : B4:9A : D6:4B : 2F : + 90 : FB |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Avr 02 00:00:00 2008 UTC |
| **Validité non postérieure à** | DEC 01 23:59:59 2037 UTC |
| **Identificateur de la clé de l’objet** | ad : 6C : AA : 94:60:9C : Ed : E4 : FF : fa : 3e : 0A : 74:2b : 63:03 : F7 : B6:59 : BF |
| **Empreinte numérique (SHA-1)** | F18B538D1BE903B6A6F056435B171589CAF36BF2 |
| **Empreinte numérique (SHA-256)** | 4B03F45807AD70F21BFC2CAE71C9FDE4604C064CF5FFB686BAE5DBAAD7FDD34C |
| **Code confidentiel (SHA-256)** | GQbGEk27Q4V40A4GbVBUxsN/D6YCjAVUXgmU7drshik = |

### <a name="verisign-class-3-public-primary-certification-authority---g5"></a>**Autorité de certification principale publique VeriSign Class 3-G5**

| **Subject** | CN = VeriSign Class 3 Public Primary Certification Authority-G5<br>OU =&quot;(c) 2006 VeriSign, Inc.-pour utilisation autorisée uniquement&quot;<br>OU = VeriSign Trust Network<br>O =&quot;VeriSign, Inc.&quot;<br>C = US |
| --- | --- |
| **Numéro de série** | 18 : DA : D1:9 E : 26:7D : E8 : BB : 4A : 21:58 : CD : CC : 6B : 3B : 4A |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | Nov 08 00:00:00 2006 UTC |
| **Validité non postérieure à** | 16 23:59:59 2036 juillet (UTC) |
| **Identificateur de la clé de l’objet** | 7F : D3:65 : A7 : C2 : DD : EC : BB : F0:30:09 : F3:43:39 : fa : 02 : AF : 33:31:33 |
| **Empreinte numérique (SHA-1)** | 4EB6D578499B1CCF5F581EAD56BE3D9B6744A5E5 |
| **Empreinte numérique (SHA-256)** | 9ACFAB7E43C8D880D06B262A94DEEEE4B4659989C3D0CAF19BAF6405E41AB7DF |
| **Code confidentiel (SHA-256)** | JbQbUG5JMJUoI6brnx0x3vZF6jilxsapbXGVfjhN8Fg = |

## <a name="office-365-intermediate-certificate-details"></a>**Détails sur le certificat intermédiaire Office 365**

### <a name="cnnic-sha256-ssl"></a>**CNNIC SHA256 SSL**

| **Subject** | CN = CNNIC SHA256 SSL <br>O = CNNIC SHA256 SSL <br>C = CN |
| --- | --- |
| **Issuer** | CN = RACINE CNNIC <br>O = CNNIC <br>C = CN |
| **Numéro de série** | 49:33:00:7C |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Dec 18 12:32:18 2014 UTC |
| **Validité non postérieure à** | Dec 18 12:32:18 2024 UTC |
| **Identificateur de la clé de l’objet** | B7 : D1:59:8B : 8c : 0d : 06:28:47:23:00:3a : 36:04 : A5 : EE : 38:76:53:3c |
| **Identificateur de la clé de l’autorité** | KeyId : 65 : F2:31 : AD :-2a : F7 : F7 : DD : 52:96:0A : C7:02 : C1:0E : EF : A6 : D5:3b : 11 |
| **Empreinte numérique (SHA-1)** | FC844648FC708433921BE88B18C48787A3E2813E |
| **Empreinte numérique (SHA-256)** | FA8B9F99DBB94E7B772AA9190846E777047C15C7A3BF4A1AF9C0CA984A689511 |
| **Code confidentiel (SHA-256)** | dKZRcLDh7hBNZTmTIHOGJ6C2Om/ITjUCPkOnLTnrZXk = |
| **URL AIA** | http://www.cnnic.cn/download/cert/CNNICROOT.cer |
| **URL de liste de révocation** | ldap:///CN=crl1,%20OU=crl,%20O=CNNIC,%20C=CN?certificateRevocationList;binary,authorityRevocationList;binary,deltaRevocationList;binary<br>http://crl.cnnic.cn/download/rootsha2crl/CRL1.crl |
| **URL OCSP** | <http://ocspcnnicroot.cnnic.cn> |

### <a name="d-trust-ssl-class-3-ca-1-2009"></a>**D-TRUST SSL Class 3 CA 1 2009**

| **Subject** | CN = D-TRUST SSL Class 3 CA 1 2009<br>O = D-Trust GmbH<br>C = DE |
| --- | --- |
| **Issuer** | CN = D-TRUST racine de la classe 3 CA 2 2009<br>O = D-Trust GmbH<br>C = DE |
| **Autre nom de l’objet** | Name=info@d-trust.net RFC822<br>URL =http://www.d-trust.net |
| **Numéro de série** | 09:90:63 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Nov 12 12:46:55 2009 UTC |
| **Validité non postérieure à** | Nov 05 08:35:58 2029 UTC |
| **Identificateur de la clé de l’objet** | 50:19:32:94:9A : C4 : B5:04:4D : 56 : D0 : C0 : C0:83:94:83:21 : D5:35:55 : B0 : B1:7A |
| **Identificateur de la clé de l’autorité** | KeyId : FD : da : 14 : C4:9F : 30 : de : 21 : BD : 1e : 42:39 : FC : AB : 63:23:49 : E0 : F1:84 |
| **Empreinte numérique (SHA-1)** | 2FC5DE6528CDBE50A14C382FC1DE524FAABF95FC |
| **Empreinte numérique (SHA-256)** | 6AC159B4C2BC8E729F3B84642EF1286BCC80D775FE278C740ADA468D59439025 |
| **Code confidentiel (SHA-256)** | 9w0QP9HzLXkfs + 4zENaUFq2XKcQON1oyksoJ + Gg2AZE = |
| **URL de liste de révocation** | ldap://directory.d-trust.net/CN=D-TRUST%20Root%20Class%203%20CA%202%202009,O=D-Trust%20GmbH,C=DE?certificaterevocationlist<br>http://www.d-trust.net/crl/d-trust\_root\_class\_3\_ca\_2\_2009.crl |
| **URL OCSP** | http://root-c3-ca2-2009.ocsp.d-trust.net |

### <a name="d-trust-ssl-class-3-ca-1-ev-2009"></a>**D-TRUST SSL Class 3 CA 1 EV 2009**

| **Subject** | CN = D-TRUST SSL Class 3 CA 1 EV 2009<br>O = D-Trust GmbH<br>C = DE |
| --- | --- |
| **Issuer** | CN = D-TRUST racine de la classe 3 CA 2 EV 2009<br>O = D-Trust GmbH<br>C = DE |
| **Autre nom de l’objet** | Name=info@d-trust.net RFC822<br>URL =http://www.d-trust.net |
| **Numéro de série** | 09:90:64 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Nov 12 12:52:43 2009 UTC |
| **Validité non postérieure à** | Nov 05 08:50:46 2029 UTC |
| **Identificateur de la clé de l’objet** | AC : Ed : A5:9d de l’alimentation : 7 a : a2 : B6:43 : F1:18:8A : 25:6A : 6 6C : B1 : CC : A8 : F2:5A : D4 |
| **Identificateur de la clé de l’autorité** | KeyId : D3:94:8A : 4C : 62:13:2 a : 19:2e : CC : AF : 72:8A : 7D : 36 : D7:9A : 1C : DC : 67 |
| **Empreinte numérique (SHA-1)** | 1069423D308D0FC54575059638560FC7556E32B3 |
| **Empreinte numérique (SHA-256)** | B0935DC04B4E60C0C42DEF7EC57A1B1D8F958D17988E71CC80A8CF5E635BA5B4 |
| **Code confidentiel (SHA-256)** | lv5BNZ5aWd27ooolULDolFTwIaaWjHvG4yyH3rss4X8 = |
| **URL de liste de révocation** | ldap://directory.d-trust.net/CN=D-TRUST%20Root%20Class%203%20CA%202%20EV%202009,O=D-Trust%20GmbH,C=DE?certificaterevocationlist<br>http://www.d-trust.net/crl/d-trust\_root\_class\_3\_ca\_2\_ev\_2009.crl |
| **URL OCSP** | http://root-c3-ca2-ev-2009.ocsp.d-trust.net |

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

### <a name="digicert-sha2-high-assurance-server-ca"></a>**DigiCert SHA2 de l’autorité de certification de serveur haute qualité**

| **Subject** | CN = DigiCert SHA2 High assurance Server CA<br>OU = www. DigiCert. com<br>O = DigiCert Inc<br>C = US |
| --- | --- |
| **Issuer** | CN = autorité de certification racine EV de l’assurance haute DigiCert<br>OU = www. DigiCert. com<br>O = DigiCert Inc<br>C = US |
| **Numéro de série** | 04 : E1 : E7 : A4 : DC : 5C : F2:/N : 6D : C0:2 TER : 42 : B8 : N : 15:9F |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Octobre 22 12:00:00 2013 UTC |
| **Validité non postérieure à** | Octobre 22 12:00:00 2028 UTC |
| **Identificateur de la clé de l’objet** | 51:68 : FF : 90 : AF : 02:07:75:3c : CC : D9:65:64:62 : a2:12 : B8:59:72:3b |
| **Identificateur de la clé de l’autorité** | KeyId : B1:3e : C3:69:03 : F8 : BF : 47:01 : D4:98:26:1a : 08:02 : EF : 63:64:2b : C3 |
| **Empreinte numérique (SHA-1)** | A031C46782E6E6C662C2C87C76DA9AA62CCABD8E |
| **Empreinte numérique (SHA-256)** | 19400BE5B7A31FB733917700789D2F0A2471C0C9D506C0E504C06C16D7CB17C0 |
| **Code confidentiel (SHA-256)** | k2v657xBsOVe1PQRwOsHsw3bsGT2VzIqz5K + 59sNQws = |
| **URL de liste de révocation** | http://crl4.digicert.com/DigiCertHighAssuranceEVRootCA.crl |
| **URL OCSP** | http://ocsp.digicert.com |

### <a name="digicert-sha2-secure-server-ca"></a>**DigiCert SHA2 serveur de l’autorité de certification sécurisée**

| **Subject** | CN = DigiCert SHA2 serveur sécurisé de l’autorité de certification<br>O = DigiCert Inc<br>C = US |
| --- | --- |
| **Issuer** | CN = DigiCert racine globale de l’autorité de certification<br>OU = www. DigiCert. com<br>O = DigiCert Inc<br>C = US |
| **Numéro de série** | 01 : FD : A3 : EB : 6E : CA : 75 : C8:88:43:8B : 72:4B : CF : BC : 91 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Mars 08 12:00:00 2013 UTC |
| **Validité non postérieure à** | Mars 08 12:00:00 2023 UTC |
| **Identificateur de la clé de l’objet** | 0F : 80:61:1C : 82:31:61 : D5:2F : 28 : E7:8D : 46:38 : B4:2C : E1 : C6 : D9 : E2 |
| **Identificateur de la clé de l’autorité** | KeyId : 03 : de : 50:35:56 : D1:4 quater : BB : 66 : F0 : a3 : E2:1b : 1b : C3:97 : B2:3D : D1:55 |
| **Empreinte numérique (SHA-1)** | 1FB86B1168EC743154062E8C9CC5B171A4B7CCB4 |
| **Empreinte numérique (SHA-256)** | 154C433C491929C5EF686E838E323664A00E6A0D822CCC958FB4DAB03E49A08F |
| **Code confidentiel (SHA-256)** | 5kJvNEMw0KjrCAu7eXY5HZdvyCS13BbA0VJG1RSP91w = |
| **URL de liste de révocation** | http://crl3.digicert.com/DigiCertGlobalRootCA.crl<br>http://crl4.digicert.com/DigiCertGlobalRootCA.crl |
| **URL OCSP** | http://ocsp.digicert.com |

### <a name="entrust-certification-authority---l1c"></a>**Autorité de certification Entrust-L1C**

| **Subject** | CN = autorité de certification Entrust-L1C<br>OU =&quot;(c) 2009 Entrust, Inc.&quot;<br>OU = www. Entrust. net/RPA est incorporée par référence<br>O =&quot;Entrust, Inc.&quot;<br>C = US |
| --- | --- |
| **Issuer** | CN = Entrust. net Certification Authority (2048)<br>OU = (c) 1999 Entrust.net limité<br>OU = www. Entrust. net/CPS\_2048 Incorp. par Réf. (limite Liab.)<br>O = Entrust. net |
| **Numéro de série** | 4C : 0E : 8C : 39 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha1RSA |
| **Validité non antérieure** | Nov 11 15:40:40 2011 UTC |
| **Validité non postérieure à** | Nov 12 02:51:17 2021 UTC |
| **Identificateur de la clé de l’objet** | 1e : F1 : AB : 89:06 : F8:49:0F : 01:33:77 : EE : 14:7A : EE : 19:7C : 93:28:4D |
| **Identificateur de la clé de l’autorité** | KeyId : 55 : E4:81 : D1:11:80 : be : D8:89 : B9:08 : a3:31 : F9 : a1:24:09:16 : B9:70 |
| **Empreinte numérique (SHA-1)** | C53E73073F93CE7895DE7484126BC303DAB9E657 |
| **Empreinte numérique (SHA-256)** | 0EE4DAF71A85D842D23F4910FD4C909B7271861931F1D5FEAC868225F52700E2 |
| **Code confidentiel (SHA-256)** | VFv5NemtodoRftw8KsvFb8AoCWwOJL6bOJS + Ui0bQ94 = |
| **URL de liste de révocation** | http://crl.entrust.net/2048ca.crl |
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

### <a name="globalsign"></a>**GlobalSign**

| **Subject** | CN = GlobalSign<br>O = GlobalSign<br>OU = GlobalSign racine CA-R3 |
| --- | --- |
| **Issuer** | CN = autorité de certification racine GlobalSign<br>OU = racine CAO = GlobalSign NV-sa<br>C = BE |
| **Numéro de série** | 04:00:00:00:00:01:25:07:1J : F9 : AF |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Nov 18 10:00:00 2009 UTC |
| **Validité non postérieure à** | Mars 18 10:00:00 2019 UTC |
| **Identificateur de la clé de l’objet** | 8F : F0:4b : 7F : A8:2e : 45:24 : AE : 4D : 50 : fa : 63:9A : 8B : de : E2 : DD : 1b : BC |
| **Identificateur de la clé de l’autorité** | KeyId : 60:7B : 66:1a : 45:0d : 97 : ca : 89:50:2F : 7D : 04 : CD : 34 : A8 : FF : FC : FD : 4b |
| **Empreinte numérique (SHA-1)** | 4765557AF418C68A641199146A7E556AA8242996 |
| **Empreinte numérique (SHA-256)** | FDFC6560B09C237F468B8130EB90996FF85FA13FA266239B8D5863798D6AB898 |
| **Code confidentiel (SHA-256)** | cGuxAXyFXFkWm61cF4HPWX8S0srS9j0aSqN0k4AP + 4A = |
| **URL de liste de révocation** | http://crl.globalsign.net/root.crl |
| **URL OCSP** | http://ocsp.globalsign.com/ExtendedSSLSHA256CACross |

### <a name="globalsign-extended-validation-ca---sha256---g2"></a>**AUTORITÉ de validation étendue GlobalSign-SHA256-G2**

| **Subject** | CN = GlobalSign de validation étendue CA-SHA256-G2<br>O = GlobalSign NV-sa<br>C = BE |
| --- | --- |
| **Issuer** | CN = GlobalSign<br>O = GlobalSign<br>OU = GlobalSign racine CA-R2 |
| **Numéro de série** | 04:00:00:00:00:01:44:4E : F0:4A : 55 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Février 20 10:00:00 2014 UTC |
| **Validité non postérieure à** | Dec 15 08:00:00 2021 UTC |
| **Identificateur de la clé de l’objet** | da : 40:77:43:65:1C : F8 : Fe : A7 : E3 : F4:64:82:3e : 4D : 43:13:22:31:02 |
| **Identificateur de la clé de l’autorité** | KeyId : 9B : E2:07:57:67:1C : 1e : C0:6A : 06 : de : 59 : B4:9A : 2D : DF : DC : 19:86:2e |
| **Empreinte numérique (SHA-1)** | 65BE102BE26928650E0EF54DC8F4F15AF5F98E8B |
| **Empreinte numérique (SHA-256)** | 24F91C0705A0A5338641B365FB0D9D9709B56297CFF1857E73C02C1636D486AA |
| **Code confidentiel (SHA-256)** | LvRiGEjRqfzurezaWuj8Wie2gyHMrW5Q06LspMnox7A = |
| **URL de liste de révocation** | http://crl.globalsign.net/root-r2.crl |
| **URL OCSP** | http://ocsp.globalsign.com/rootr2 |

### <a name="globalsign-extended-validation-ca---sha256---g3"></a>**GlobalSign de validation étendue de l’autorité de certification-SHA256-G3**

| **Subject** | CN = GlobalSign de validation étendue CA-SHA256-G3<br>O = GlobalSign NV-sa<br>C = BE |
| --- | --- |
| **Issuer** | CN = GlobalSign<br>O = GlobalSign<br>OU = GlobalSign racine CA-R3 |
| **Numéro de série** | 48 : A4:02 : DD : 27:92:0D :: A2:08:34:9D : D1:99:7B |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Sep 21 00:00:00 2016 UTC |
| **Validité non postérieure à** | Sep 21 00:00:00 2026 UTC |
| **Identificateur de la clé de l’objet** | DD : B3 : E7:6D : A8:2e : E8 : C5:4e : 6e : cf : 74 : E6:75:3c : 94:15 : ce : E8:1J |
| **Identificateur de la clé de l’autorité** | KeyId : 8F : F0:4b : 7F : A8:2e : 45:24 : AE : 4D : 50 : fa : 63:9A : 8B : de : E2 : DD : 1b : BC |
| **Empreinte numérique (SHA-1)** | 6023192FE7B59D2789130A9FE4094F9B5570D4A2 |
| **Empreinte numérique (SHA-256)** | AED5DD9A5339685DFB029F6D89A14335A96512C3CACC52B2994AF8B6B37FA4D2 |
| **Code confidentiel (SHA-256)** | 86fLIetopQLDNxFZ0uMI66Xpl1pFgLlHHn9v6kT0i4I = |
| **URL de liste de révocation** | http://crl.globalsign.com/root-r3.crl |
| **URL OCSP** | http://ocsp2.globalsign.com/rootr3 |

### <a name="globalsign-organization-validation-ca---sha256---g2"></a>**Validation de l’organisation GlobalSign CA-SHA256-G2**

| **Subject** | CN = GlobalSign de validation de l’organisation CA-SHA256-G2<br>O = GlobalSign NV-sa<br>C = BE |
| --- | --- |
| **Issuer** | CN = GlobalSign<br>O = GlobalSign<br>OU = GlobalSign racine CA-R3 |
| **Numéro de série** | 04:00:00:00:00:01:31:89 : C6:44 : C9 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Août 02 10:00:00 2011 UTC |
| **Validité non postérieure à** | Août 02 10:00:00 2022 UTC |
| **Identificateur de la clé de l’objet** | 96 : de : 61 : F1 : BD : 1C : 16:29:53:1C : C0 : CC : 7D : 3b : 83:00:40 : E6:1a : 7c |
| **Identificateur de la clé de l’autorité** | KeyId : 8F : F0:4b : 7F : A8:2e : 45:24 : AE : 4D : 50 : fa : 63:9A : 8B : de : E2 : DD : 1b : BC |
| **Empreinte numérique (SHA-1)** | EF90B2B86F4756EBE7D36FF3015D63523A0076E9 |
| **Empreinte numérique (SHA-256)** | 0B339212D7CFF17A2C59E35669B58E77350133750A78DA9404770EDD470DEF76 |
| **Code confidentiel (SHA-256)** | IQBnNBEiFuhj + 8x6X8XLgh01V9Ic5/V3IRQLNFFc7v4 = |
| **URL de liste de révocation** | http://crl.globalsign.net/root-r3.crl |
| **URL OCSP** | http://ocsp2.globalsign.com/rootr3 |

### <a name="globalsign-organization-validation-ca---sha256---g2"></a>**Validation de l’organisation GlobalSign CA-SHA256-G2**

| **Subject** | CN = GlobalSign de validation de l’organisation CA-SHA256-G2<br>O = GlobalSign NV-sa<br>C = BE |
| --- | --- |
| **Issuer** | CN = autorité de certification racine GlobalSign<br>OU = AC racine<br>O = GlobalSign NV-sa<br>C = BE |
| **Numéro de série** | 04:00:00:00:00:01:44:4E : F0:42:47 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Février 20 10:00:00 2014 UTC |
| **Validité non postérieure à** | Février 20 10:00:00 2024 UTC |
| **Identificateur de la clé de l’objet** | 96 : de : 61 : F1 : BD : 1C : 16:29:53:1C : C0 : CC : 7D : 3b : 83:00:40 : E6:1a : 7c |
| **Identificateur de la clé de l’autorité** | KeyId : 60:7B : 66:1a : 45:0d : 97 : ca : 89:50:2F : 7D : 04 : CD : 34 : A8 : FF : FC : FD : 4b |
| **Empreinte numérique (SHA-1)** | 902EF2DEEB3C5B13EA4C3D5193629309E231AE55 |
| **Empreinte numérique (SHA-256)** | 74EF335E5E18788307FB9D89CB704BEC112ABD23487DBFF41C4DED5070F241D9 |
| **Code confidentiel (SHA-256)** | IQBnNBEiFuhj + 8x6X8XLgh01V9Ic5/V3IRQLNFFc7v4 = |
| **URL de liste de révocation** | http://crl.globalsign.net/root.crl |
| **URL OCSP** | http://ocsp.globalsign.com/rootr1 |

### <a name="globalsign-organization-validation-ca---sha256---g2"></a>**Validation de l’organisation GlobalSign CA-SHA256-G2**

| **Subject** | CN = GlobalSign de validation de l’organisation CA-SHA256-G2<br>O = GlobalSign NV-sa<br>C = BE |
| --- | --- |
| **Issuer** | CN = autorité de certification racine GlobalSign<br>OU = AC racine<br>O = GlobalSign NV-sa<br>C = BE |
| **Numéro de série** | 04:00:00:00:00:01:44:4E : F0:42:47 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Février 20 10:00:00 2014 UTC |
| **Validité non postérieure à** | Février 20 10:00:00 2024 UTC |
| **Identificateur de la clé de l’objet** | 96 : de : 61 : F1 : BD : 1C : 16:29:53:1C : C0 : CC : 7D : 3b : 83:00:40 : E6:1a : 7c |
| **Identificateur de la clé de l’autorité** | KeyId : 60:7B : 66:1a : 45:0d : 97 : ca : 89:50:2F : 7D : 04 : CD : 34 : A8 : FF : FC : FD : 4b |
| **Empreinte numérique (SHA-1)** | 902EF2DEEB3C5B13EA4C3D5193629309E231AE55 |
| **Empreinte numérique (SHA-256)** | 74EF335E5E18788307FB9D89CB704BEC112ABD23487DBFF41C4DED5070F241D9 |
| **Code confidentiel (SHA-256)** | IQBnNBEiFuhj + 8x6X8XLgh01V9Ic5/V3IRQLNFFc7v4 = |
| **URL de liste de révocation** | http://crl.globalsign.net/root.crl |
| **URL OCSP** | http://ocsp.globalsign.com/rootr1 |

### <a name="lets-encrypt-authority-x3"></a>**Chiffrer l’autorité x3**

| **Subject** | CN = déchiffrer l’autorité x3<br>O = chiffrer<br>C = US |
| --- | --- |
| **Issuer** | CN = autorité de certification racine x3<br>O = approbation de signature numérique Co. |
| **Numéro de série** | 0A : 01:41:42:00:00:01:53:85:73:6A : 0B : 0 : EC : A7:08 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Mars 17 16:40:46 2016 UTC |
| **Validité non postérieure à** | Mars 17 16:40:46 2021 UTC |
| **Identificateur de la clé de l’objet** | A8:4a : 6A : 63:04:7D : DD : BA : E6 : D1:39 : B7 : A6:45:65 : EF : F3 : A8 : EC : a1 |
| **Identificateur de la clé de l’autorité** | KeyId : C4 : A7 : B1 : A4:7B : 2C : 71 : fa : DB : E1:4b : 90:75 : FF : C4:15:60:85:89:10 |
| **Empreinte numérique (SHA-1)** | E6A3B45B062D509B3382282D196EFE97D5956CCB |
| **Empreinte numérique (SHA-256)** | 25847D668EB4F04FDD40B12B6B0740C567DA7D024308EB6C2C96FE41D9DE218D |
| **Code confidentiel (SHA-256)** | YLh1dUR9y6Kja30RrAn7JKnbQG/uEtLMkBgFF2Fuihg = |
| **URL AIA** | http://apps.identrust.com/roots/dstrootcax3.p7c |
| **URL de liste de révocation** | http://crl.identrust.com/DSTROOTCAX3CRL.crl |
| **URL OCSP** | http://isrg.trustid.ocsp.identrust.com |

### <a name="microsoft-it-ssl-sha2"></a>**SHA2 SSL de Microsoft IT**

| **Subject** | CN = Microsoft IT SSL SHA2<br>OU = Microsoft IT<br>O = Microsoft Corporation<br>L = Redmond<br>S = Washington<br>C = US |
| --- | --- |
| **Issuer** | CN = racine Baltimore CyberTrust<br>OU = CyberTrust<br>O = Baltimore<br>C = IE |
| **Numéro de série** | 07:27:9A : A9 |
| **Longueur de la clé publique** | RSA 4096 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | DEC 19 20:07:32 2013 UTC |
| **Validité non postérieure à** | DEC 19 20:06:55 2017 UTC |
| **Identificateur de la clé de l’objet** | 51 : AF : 24:26:9C : F4:68:22:57:80:26:2b : 3b : 46:62:15:7B : 1e : CC : a5 |
| **Identificateur de la clé de l’autorité** | KeyId : E5:9D : 59:30:82:47:58 : CC : AC : fa : 08:54:36:86:7B : 3a : B5:04:4D : F0 |
| **Empreinte numérique (SHA-1)** | 948E1652586240D453287AB69CAEB8F2F4F02117 |
| **Empreinte numérique (SHA-256)** | 34BD941A06ED10E2FAC8459F79E4748C1EA08F142C6DE5E557884D0D3CE249FA |
| **Code confidentiel (SHA-256)** | CzdPous1hY3sIkO55pUH7vklXyIHVZAl/UnprSQvpEI = |
| **URL de liste de révocation** | http://cdp1.public-trust.com/CRL/Omniroot2025.crl |

### <a name="microsoft-it-ssl-sha2"></a>**SHA2 SSL de Microsoft IT**

| **Subject** | CN = Microsoft IT SSL SHA2<br>OU = Microsoft IT<br>O = Microsoft Corporation<br>L = Redmond<br>S = Washington<br>C = US |
| --- | --- |
| **Issuer** | CN = racine Baltimore CyberTrust<br>OU = CyberTrust<br>O = Baltimore<br>C = IE |
| **Numéro de série** | 07:27 : AA : 47 |
| **Longueur de la clé publique** | RSA 4096 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | 07 17:04:09 2014 mai UTC |
| **Validité non postérieure à** | 07 17:03:30 2018 mai UTC |
| **Identificateur de la clé de l’objet** | 51 : AF : 24:26:9C : F4:68:22:57:80:26:2b : 3b : 46:62:15:7B : 1e : CC : a5 |
| **Identificateur de la clé de l’autorité** | KeyId : E5:9D : 59:30:82:47:58 : CC : AC : fa : 08:54:36:86:7B : 3a : B5:04:4D : F0 |
| **Empreinte numérique (SHA-1)** | 97EFF3028677894BDD4F9AC53F789BEE5DF4AD86 |
| **Empreinte numérique (SHA-256)** | 2399983E99703EBD01CEA466C10799810C4BA62A8D61B88170A334DCD61BB20F |
| **Code confidentiel (SHA-256)** | CzdPous1hY3sIkO55pUH7vklXyIHVZAl/UnprSQvpEI = |
| **URL de liste de révocation** | http://cdp1.public-trust.com/CRL/Omniroot2025.crl |
| **URL OCSP** | http://ocsp.omniroot.com/baltimoreroot |

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

### <a name="symantec-class-3-ev-ssl-ca---g3"></a>**Symantec classe 3 EV SSL CA-G3**

| **Subject** | CN = Symantec classe 3 EV SSL CA-G3<br>OU = Symantec Trust Network<br>O = Symantec Corporation<br>C = US |
| --- | --- |
| **Issuer** | CN = VeriSign Class 3 Public Primary Certification Authority-G5<br>OU =&quot;(c) 2006 VeriSign, Inc.-pour utilisation autorisée uniquement&quot;<br>OU = VeriSign Trust Network<br>O =&quot;VeriSign, Inc.&quot;<br>C = US |
| **Autre nom de l’objet** | Adresse du répertoire : CN = SymantecPKI-1-533 |
| **Numéro de série** | 7E : E1:4A : 6F : 6F : EF : F2 : D3:7F : 3F : AD : 65:4D : 3A : DA : B4 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Octobre 31 00:00:00 2013 UTC |
| **Validité non postérieure à** | Octobre 30 23:59:59 2023 UTC |
| **Identificateur de la clé de l’objet** | 01:59 : AB : E7 : DD : 3a : 0b : 59 : A6:64:63 : D6 : cf : 20:07:57 : D5:91 : E7:6A |
| **Identificateur de la clé de l’autorité** | KeyId : 7F : D3:65 : A7 : C2 : DD : EC : BB : F0:30:09 : F3:43:39 : fa : 02 : AF : 33:31:33 |
| **Empreinte numérique (SHA-1)** | E3FC0AD84F2F5A83ED6F86F567F8B14B40DCBF12 |
| **Empreinte numérique (SHA-256)** | 9E6BC5F9ECC52460E8EDC02C644D1BE1CB9F2316F41DAF3B616A0B2058294B31 |
| **Code confidentiel (SHA-256)** | gMxWOrX4PMQesK9qFNbYBxjBfjUvlkn/vN1n + L9lE5E = |
| **URL de liste de révocation** | http://s1.symcb.com/pca3-g5.crl |
| **URL OCSP** | http://s2.symcb.com |

### <a name="symantec-class-3-secure-server-ca---g4"></a>**Symantec Class 3 Secure Server CA-G4**

| **Subject** | CN = Symantec Class 3 Secure Server CA-G4<br>OU = Symantec Trust Network<br>O = Symantec Corporation<br>C = US |
| --- | --- |
| **Issuer** | CN = VeriSign Class 3 Public Primary Certification Authority-G5<br>OU =&quot;(c) 2006 VeriSign, Inc.-pour utilisation autorisée uniquement&quot;<br>OU = VeriSign Trust Network<br>O =&quot;VeriSign, Inc.&quot;<br>C = US |
| **Autre nom de l’objet** | Adresse du répertoire : CN = SymantecPKI-1-534 |
| **Numéro de série** | 51:3F : B9:74:38:70 : B7:34:40:41:8D : 30:93:06:99 : FF |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Octobre 31 00:00:00 2013 UTC |
| **Validité non postérieure à** | Octobre 30 23:59:59 2023 UTC |
| **Identificateur de la clé de l’objet** | 5F : 60 : cf : 61:90:55 : DF : 84:43:14:8A : 60:2a : a2 : F5:7A : F4:43:18 : EF |
| **Identificateur de la clé de l’autorité** | KeyId : 7F : D3:65 : A7 : C2 : DD : EC : BB : F0:30:09 : F3:43:39 : fa : 02 : AF : 33:31:33 |
| **Empreinte numérique (SHA-1)** | FF67367C5CD4DE4AE18BCCE1D70FDABD7C866135 |
| **Empreinte numérique (SHA-256)** | EAE72EB454BF6C3977EBD289E970B2F5282949190093D0D26F98D0F0D6A9CF17 |
| **Code confidentiel (SHA-256)** | 9n0izTnSRF + W4W4JTq51avSXkWhQB8duS2bxVLfzXsY = |
| **URL de liste de révocation** | http://s1.symcb.com/pca3-g5.crl |
| **URL OCSP** | http://s2.symcb.com |

### <a name="thawte-sha256-ssl-ca"></a>**autorité de certification Thawte SHA256 SSL**

| **Subject** | CN = Thawte SHA256 SSL CA<br>O =&quot;Thawte, Inc.&quot;<br>C = US |
| --- | --- |
| **Issuer** | CN = autorité racine principale Thawte-G3<br>OU =&quot;(c) 2008 Thawte, Inc.-pour utilisation autorisée uniquement&quot;<br>OU = Division des services de certification<br>O =&quot;Thawte, Inc.&quot;<br>C = US |
| **Autre nom de l’objet** | Adresse du répertoire : CN = VeriSignMPKI-2-415 |
| **Numéro de série** | 36:34:9E : 18 : C9:9 : 26:69 : B6:56:2E : 6C : E5 : AD : 71:32 |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | 23 00:00:00 2013 mai UTC |
| **Validité non postérieure à** | 22 23:59:59 2023 mai UTC |
| **Identificateur de la clé de l’objet** | 2b : 9A : 35 : AE : 01:18:38:30 : E1:70:7A : 05 : E0:11:76 : a3 : ce : BD : 90:14 |
| **Identificateur de la clé de l’autorité** | KeyId : AD : 6C : AA : 94:60:9C : Ed : E4 : FF : fa : 3e : 0A : 74:2b : 63:03 : F7 : B6:59 : BF |
| **Empreinte numérique (SHA-1)** | 67D147D5DAB7F28D663CA5B7A9568F087427B9F7 |
| **Empreinte numérique (SHA-256)** | 3F3AF9C9CC2C7599EF8F6DD7CA516CFC1797D7D12002254F3BFD0D4D0FE9DE86 |
| **Code confidentiel (SHA-256)** | /36ymPAVaJl3QDyB1lUkVf9GqJNug0R8JJPDN6348p8 = |
| **URL de liste de révocation** | http://crl.thawte.com/ThawtePCA-G3.crl |
| **URL OCSP** | http://ocsp.thawte.com |

### <a name="verizon-akamai-sureserver-ca-g14-sha2"></a>**Verizon Akamai SureServer CA G14-SHA2**

| **Subject** | CN = Verizon Akamai SureServer CA G14-SHA2<br>OU = Cybertrust<br>O = solutions de Verizon Enterprise<br>L = Amsterdam<br>C = NL |
| --- | --- |
| **Issuer** | CN = racine Baltimore CyberTrust<br>OU = CyberTrust<br>O = Baltimore<br>C = IE |
| **Numéro de série** | 07:27 : A4:6B |
| **Longueur de la clé publique** | RSA 2048 bits (e 65537) |
| **Algorithme de signature** | sha256RSA |
| **Validité non antérieure** | Avr 02 14:36:10 2014 UTC |
| **Validité non postérieure à** | Avr 02 14:35:52 2021 UTC |
| **Identificateur de la clé de l’objet** | F8 : BD : fa : AF : 73:77 : C6 : C7:1b : F9:4b : 4D : 11 : A7 : D1:33 : AF : AF : 72:11 |
| **Identificateur de la clé de l’autorité** | KeyId : E5:9D : 59:30:82:47:58 : CC : AC : fa : 08:54:36:86:7B : 3a : B5:04:4D : F0 |
| **Empreinte numérique (SHA-1)** | 6AD2B04E2196E48BF685752890E811CD2ED60606 |
| **Empreinte numérique (SHA-256)** | 7373D219B42547E41BCB752BCBCBE93F592FF6F99C340CE57B73D38C3EC0BA98 |
| **Code confidentiel (SHA-256)** | 8XFPrRr4VxmEIYKUu35QtR3oGbduX1AlrBzaBUHgp7c = |
| **URL AIA** | https://cacert.omniroot.com/baltimoreroot.crt<br>https://cacert.omniroot.com/baltimoreroot.der |
| **URL de liste de révocation** | http://cdp1.public-trust.com/CRL/Omniroot2025.crl |
| **URL OCSP** | http://ocsp.omniroot.com/baltimoreroot |

## <a name="additional-certificate-paths"></a>**Chemins d’accès de certificat supplémentaires**

La liste suivante inclut les certificats hérités qui ne sont pas inclus ci-dessus et qui seront fusionnés avec la liste ci-dessus au fil du temps.

evsecure-aia.verisign.com<br>
sa.symcb.com<br>
sd.symcb.com<br>
\*. omniroot.com<br>
\*. verisign.com<br>
\*. symcb.com<br>
\*. symcd.com<br>
\*. verisign.net<br>
\*. geotrust.com<br>
\*. entrust.net<br>
\*. public-trust.com<br>
EVIntl-ocsp.verisign.com<br>
EVSecure-ocsp.verisign.com<br>
isrg.trustid.ocsp.identrust.com<br>
ocsp.digicert.com<br>
ocsp.entrust.net<br>
ocsp.globalsign.com/ExtendedSSLSHA256CACross<br>
ocsp.globalsign.com/rootr1<br>
ocsp.globalsign.com/rootr2<br>
ocsp2.globalsign.com/rootr3<br>
ocsp.int-x3.letsencrypt.org/<br>
ocsp.msocsp.com<br>
ocsp.omniroot.com/baltimoreroot<br>
ocsp2.globalsign.com/gsextendvalsha2g3r3<br>
ocsp2.globalsign.com/gsorganizationvalsha2g2<br>
ocsp2.globalsign.com/gsorganizationvalsha2g3<br>
ocsp2.globalsign.com/rootr3<br>
ocspx.digicert.com<br>
s2.symcb.com<br>
sr.symcd.com<br>
su.symcd.com<br>
vassg142.ocsp.omniroot.com<br>
cdp1.public-trust.com/CRL/Omniroot2025.crl<br>
crl.entrust.net/2048ca.crl<br>
crl.entrust.net/g2ca.crl<br>
crl.entrust.net/level1k.crl<br>
crl.entrust.net/rootca1.crl<br>
crl.globalsign.com/gs/gsextendvalsha2g3r3.crl<br>
crl.globalsign.com/gs/gsorganizationvalsha2g2.crl<br>
crl.globalsign.com/gsorganizationvalsha2g3.crl<br>
crl.globalsign.com/root.crl<br>
crl.globalsign.net/root-r2.crl<br>
crl.globalsign.com/root-r3.crl<br>
crl.globalsign.net/root.crl<br>
crl.identrust.com/DSTROOTCAX3CRL.crl<br>
crl.microsoft.com/pki/mscorp/crl/msitwww1.crl<br>
crl.microsoft.com/pki/mscorp/crl/msitwww2.crl<br>
crl3.digicert.com/DigiCertCloudServicesCA-1-g1.crl<br>
crl3.digicert.com/DigiCertGlobalRootCA.crl<br>
crl3.digicert.com/sha2-ev-server-g1.crl<br>
crl3.digicert.com/sha2-ha-server-g5.crl<br>
crl3.digicert.com/ssca-sha2-g5.crl<br>
crl4.digicert.com/DigiCertCloudServicesCA-1-g1.crl<br>
crl4.digicert.com/DigiCertGlobalRootCA.crl<br>
crl4.digicert.com/DigiCertHighAssuranceEVRootCA.crl<br>
crl4.digicert.com/sha2-ev-server-g1.crl<br>
crl4.digicert.com/sha2-ha-server-g5.crl<br>
crl4.digicert.com/ssca-sha2-g5.crl<br>
EVIntl-crl.verisign.com/EVIntl2006.crl<br>
EVSecure-crl.verisign.com/pca3-g5.crl<br>
mscrl.microsoft.com/pki/mscorp/crl/msitwww1.crl<br>
mscrl.microsoft.com/pki/mscorp/crl/msitwww2.crl<br>
s1.symcb.com/pca3-g5.crl<br>
sr.symcb.com/sr.crl<br>
su.symcb.com/su.crl<br>
vassg142.crl.omniroot.com/vassg142.crl<br>
aia.entrust.net/l1k-chain256.cer<br>
apps.identrust.com/roots/dstrootcax3.p7c<br>
<https://cacert.a.omniroot.com/vassg142.crt><br>
<https://cacert.a.omniroot.com/vassg142.der><br>
<https://cacert.omniroot.com/baltimoreroot.crt><br>
<https://cacert.omniroot.com/baltimoreroot.der><br>
cacerts.digicert.com/DigiCertCloudServicesCA-1.crt<br>
cacerts.digicert.com/DigiCertSHA2ExtendedValidationServerCA.crt<br>
cacerts.digicert.com/DigiCertSHA2HighAssuranceServerCA.crt<br>
cacerts.digicert.com/DigiCertSHA2SecureServerCA.crt<br>
cert.int-x3.letsencrypt.org/<br>
EVIntl-aia.verisign.com/EVIntl2006.cer<br>
secure.globalsign.com/cacert/gsextendvalsha2g2r2.crt<br>
secure.globalsign.com/cacert/gsextendvalsha2g3r3.crt<br>
secure.globalsign.com/cacert/gsorganizationvalsha2g2r1.crt<br>
secure.globalsign.com/cacert/gsorganizationvalsha2g3.crt<br>
sr.symcb.com/sr.crt<br>
su.symcb.com/su.crt<br>
<https://www.digicert.com/CACerts/DigiCertGlobalRootCA.crt><br>
<https://www.digicert.com/CACerts/DigiCertHighAssuranceEVRootCA.crt><br>
<https://www.microsoft.com/pki/mscorp/msitwww1.crt><br>
<https://www.microsoft.com/pki/mscorp/msitwww2.crt><br>
