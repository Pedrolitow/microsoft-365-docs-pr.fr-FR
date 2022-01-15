---
title: Office des certificats TLS
description: Comment préparer les modifications à venir apportées Office certificats TLS.
author: pshelton-skype
ms.author: pshelton
manager: elenip
ms.topic: article
audience: Developer
ms.date: 1/7/2021
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.openlocfilehash: 57183aff11671a86261789a1978e804317da69ca
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2022
ms.locfileid: "62055030"
---
# <a name="office-tls-certificate-changes"></a>Office des certificats TLS

Microsoft 365 met à jour les services de messagerie, de réunions, de téléphonie, de voix et de vidéo pour utiliser les certificats TLS d’un autre ensemble d’autorités de certification racines. Cette modification est en cours, car l’ac racine actuelle expirera en mai 2025.

Les produits concernés sont les suivants :
- Microsoft Teams
- Skype
- Skype Entreprise Online
- Microsoft Dynamics 365
- GroupMe
- Kaizala
- Azure Communication Services

Les points de terminaison affectés incluent (mais ne sont pas limités à) :
- *.teams.microsoft.com
- *.skype.com
- *.skypeforbusiness.com
- *.groupme.com
- *.communication.azure.com
- *.operatorconnect.microsoft.com

Cette modification n’affectera pas les certificats, les domaines ou les services utilisés dans les instances de cloud national des États-Unis, de la Chine ou de l’Allemagne Microsoft 365.

Toutes les informations de certificat de cet article ont été précédemment fournies dans [Microsoft 365 de](./encryption-office-365-certificate-chains.md) chiffrement au plus tard en octobre 2020.

## <a name="when-will-this-change-happen"></a>Quand cette modification aura-t-elle lieu ?

Services will begin transitioning to the new Root CAs beginning in Jan 2022, possibly continuing into the third quarter (July-Sept) 2022.

## <a name="what-is-changing"></a>Qu’est-ce qui change ?

Aujourd’hui, la plupart des certificats TLS utilisés par Microsoft 365 services sont chaînés jusqu’à l’AC racine suivante :

| Nom commun de l’ac | Thumbprint (SHA1) |
|--|--|
| [Baltimore CyberTrust Root](https://cacerts.digicert.com/BaltimoreCyberTrustRoot.crt) | d4de20d05e66fc53fe1a50882c78db2852cae474 |

avec l’une des CA intermédiaires suivantes :

| Nom commun de l’ac | Thumbprint (SHA1) |
|--|--|
| [Microsoft RSA TLS CA 01](http://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2001.crt) | 703d7a8f0ebf55aaa59f98eaf4a206004eb2516a |
| [Microsoft RSA TLS CA 02](http://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2002.crt) | b0c2d2d13cdd56cdaa6ab6e2c04440be4a429c75 |

Les nouveaux certificats TLS utilisés par Microsoft 365 services de contrôle d’accès sont désormais chaînés jusqu’à l’une des certifications racines suivantes :

| Nom commun de l’ac | Thumbprint (SHA1) |
|--|--|
| [DigiCert Global Root G2](https://cacerts.digicert.com/DigiCertGlobalRootG2.crt) | df3c24f9bfd666761b268073fe06d1cc8d4f82a4 |
| [Autorité de certification racine Microsoft RSA 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crt) | 73a5e64a3bff8316ff0edccc618a906e4eae4d74 | 
| [Autorité de certification racine Microsoft ECC 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crt) | 999a64c37ff47d9fab95f14769891460eec4c3c5 |

avec l’une des CA intermédiaires suivantes :

| Nom commun de l’ac | Thumbprint (SHA1) |
|--|--|
| [Microsoft Azure TLS émettrice CA 01](http://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2001%20-%20xsign.crt) | 2f2877c5d778c31e0f29c7e371df5471bd673173 |
| [Microsoft Azure TLS émettrice CA 02](http://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2002%20-%20xsign.crt) | e7eea674ca718e3befd90858e09f8372ad0ae2aa |
| [Microsoft Azure TLS émettrice CA 05](http://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2005%20-%20xsign.crt) | 6c3af02e7f269aa73afd0eff2a88a4a1f04ed1e5 |
| [Microsoft Azure TLS émettrice CA 06](http://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2006%20-%20xsign.crt) | 30e01761ab97e59a06b41ef20af6f2de7ef4f7b0 |

## <a name="will-this-change-affect-me"></a>Cette modification va-t-elle m’affecter ?

L’ac racine « DigiCert Global Root G2 » est largement fiable par les systèmes d’exploitation, notamment Windows, macOS, Android et iOS, et par des navigateurs tels que Microsoft Edge, Chrome, Safari et Firefox. Nous pensons que **la plupart Microsoft 365 clients ne seront pas touchés.** 

Toutefois, **votre application peut être impactée si elle spécifie** explicitement une liste d’ca acceptables . Cette pratique est appelée « épinglage de certificat ». Les clients qui n’ont pas les nouvelles CA racines dans leur liste d’applications de certification acceptables recevront des erreurs de validation de certificat, ce qui peut avoir un impact sur la disponibilité ou la fonction de votre application.

Voici quelques méthodes pour détecter si votre application peut être impactée :

- Recherchez dans votre code source l’empreinte numérique, le nom commun ou d’autres propriétés de l’une des CA intermédiaires trouvées [ici.](https://www.microsoft.com/pki/mscorp/cps/default.htm) S’il existe une correspondance, votre application sera impactée. Pour résoudre ce problème, mettez à jour le code source pour ajouter les propriétés des nouvelles CAs. En tant que meilleure pratique, assurez-vous que les CAs peuvent être ajoutées ou modifiées dans un court préavis. Les réglementations du secteur exigent que les certificats d’ac soient remplacés dans un délai de sept jours dans certaines circonstances, de sorte que les applications qui implémentent l’épinglage de certificat doivent réagir rapidement à ces modifications.

- .NET expose les fonctions de rappel, qui permettent aux développeurs d’utiliser une logique personnalisée pour déterminer si les certificats sont valides plutôt que de s’appuyer sur le magasin de `System.Net.ServicePointManager.ServerCertificateValidationCallback` `System.Net.HttpWebRequest.ServerCertificateValidationCallback` certificats Windows standard. Un développeur peut ajouter une logique qui recherche un nom commun ou une empreinte numérique spécifique ou n’autorise qu’une ca racine spécifique telle que « CyberTrust Root ». Si votre application utilise ces fonctions de rappel, vous devez vous assurer qu’elle accepte l’ancienne et la nouvelle cae racine et intermédiaire.

- Les applications natives peuvent utiliser , ce qui `WINHTTP_CALLBACK_STATUS_SENDING_REQUEST` permet aux applications natives d’implémenter une logique de validation de certificat personnalisée. L’utilisation de cette notification est rare et nécessite une quantité importante de code personnalisé à implémenter. Comme dans le cas ci-dessus, assurez-vous que votre application accepte l’ancienne et la nouvelle CA racine et intermédiaire. 

- Si vous utilisez une application qui s’intègre aux API Microsoft Teams, Skype, Skype Entreprise Online ou Microsoft Dynamics et que vous ne savez pas si elle utilise l’épinglage de certificat, vérifiez auprès du fournisseur de l’application.

- Différents systèmes d’exploitation et runtimes linguistiques qui communiquent avec les services Azure peuvent nécessiter d’autres étapes pour créer et valider correctement les nouvelles chaînes de certificats :
   - **Linux**: de nombreuses distributions nécessitent que vous ajoutiez des CAs `/etc/ssl/certs` à . Pour obtenir des instructions spécifiques, reportez-vous à la documentation de la distribution.
   - **Java**: assurez-vous que le magasin de clés Java contient les CA répertoriées ci-dessus.
   - Windows en cours d’exécution dans des **environnements déconnectés**: les systèmes qui s’exécutent dans des environnements déconnectés doivent être ajoutés à leur magasin par les nouvelles CA racines et les nouvelles sous-catégories intermédiaires ajoutées à leur `Trusted Root Certification Authorities` `Intermediate Certification Authorities` magasin.
   - **Android**: consultez la documentation relative à votre appareil et à votre version d’Android.
   - **Appareils IoT** ou incorporés : les appareils incorporés tels que les zones supérieure de l’écran de TV sont souvent intégrés avec un ensemble limité de certificats d’autorité racine et ne peuvent pas facilement mettre à jour le magasin de certificats. Si vous écrivez du code ou gérez des déploiements d’appareils IoT ou incorporés personnalisés, assurez-vous que les appareils font confiance aux nouvelles CA racines. Vous devrez peut-être contacter le fabricant de l’appareil.

- Si vous avez un environnement dans lequel les règles de pare-feu autorisent les appels sortants uniquement vers des points de terminaison spécifiques, autorisez les URL de liste de révocation de certificats (CRL) ou OCSP (Online Certificate Status Protocol) suivantes :
   - http://crl3.digicert.com
   - http://crl4.digicert.com
   - http://ocsp.digicert.com
   - http://crl.microsoft.com
   - http://oneocsp.microsoft.com
   - http://ocsp.msocsp.com
   - http://www.microsoft.com/pkiops

- Si vous êtes touché par cette modification, vous pouvez voir des messages d’erreur dépendant du type d’environnement que vous exécutez et du scénario dont vous êtes impacté. Vérifiez Windows journaux des événements de l’application, les journaux d’événements CAPI2 et les journaux d’applications personnalisés pour les messages qui ressemblent à :
   ```
   An operation failed because the following certificate has validation errors:
   
   Subject Name: CN=teams.microsoft.com
   Issuer Name: CN=Microsoft Azure TLS Issuing CA 01, O=Microsoft Corporation, C=US
   
   Errors:
   
   The root of the certificate chain is not a trusted root authority.
   ```

## <a name="when-can-i-retire-the-old-ca-information"></a>Quand puis-je retirer les anciennes informations de l’ac ?

Les certificats racines, intermédiaires et feuilles actuels ne seront pas révoqués. Les noms communs de l’ac et/ou les empreintes numériques existants seront requis jusqu’au moins février 2023 en fonction de la durée de vie des certificats existants.
