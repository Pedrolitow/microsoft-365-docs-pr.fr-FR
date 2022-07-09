---
title: Modifications apportées aux certificats TLS Office
description: Comment préparer les modifications à venir apportées aux certificats TLS Office.
author: pshelton-skype
ms.author: pshelton
manager: toddbeckett
ms.topic: article
audience: Developer
ms.date: 3/7/2022
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.openlocfilehash: d5390c97c097bdbf52e496336e3a239d975a88aa
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2022
ms.locfileid: "66696225"
---
# <a name="office-tls-certificate-changes"></a>Modifications du certificat TLS Office

Microsoft 365 met à jour les services de messagerie, de réunions, de téléphonie, de voix et de vidéo pour utiliser des certificats TLS provenant d’un autre ensemble d’autorités de certification racines. Cette modification est en cours, car l’autorité de certification racine actuelle expirera en mai 2025.

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

En outre, Teams et les points de terminaison Skype Entreprise Online dans les instances cloud nationales du gouvernement des États-Unis de Microsoft 365 apporteront les mêmes modifications, affectant les points de terminaison tels que :
- *.gcc.teams.microsoft.com
- *.dod.teams.microsoft.us
- *.gov.teams.microsoft.us
- *.online.dod.skypeforbusiness.us
- *.online.gov.skypeforbusiness.us
- *.um-dod.office365.us
- *.um.office365.us

Cette modification n’affecte pas les certificats, domaines ou services utilisés dans les instances cloud nationales de Microsoft 365 en Chine ou en Allemagne.

Toutes les informations de certificat de cet article ont été précédemment [fournies dans les chaînes de chiffrement Microsoft 365](./encryption-office-365-certificate-chains.md) au plus tard en octobre 2020.

## <a name="when-will-this-change-happen"></a>Quand cette modification aura-t-elle lieu ?

Les services ont commencé à passer aux nouvelles autorités de certification racine en janvier 2022 et se poursuivent jusqu’en octobre 2022.

## <a name="what-is-changing"></a>Qu’est-ce qui change ?

Aujourd’hui, la plupart des certificats TLS utilisés par les services Microsoft 365 s’enchaînent jusqu’à l’autorité de certification racine suivante :

| Nom commun de l’autorité de certification | Empreinte numérique (SHA1) |
|--|--|
| [Baltimore CyberTrust Root](https://cacerts.digicert.com/BaltimoreCyberTrustRoot.crt) | d4de20d05e66fc53fe1a50882c78db2852cae474 |

avec l’une des autorités de certification intermédiaires suivantes :

| Nom commun de l’autorité de certification | Empreinte numérique (SHA1) |
|--|--|
| [Microsoft RSA TLS CA 01](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2001.crt) | 703d7a8f0ebf55aaa59f98eaf4a206004eb2516a |
| [Microsoft RSA TLS CA 02](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2002.crt) | b0c2d2d13cdd56cdaa6ab6e2c04440be4a429c75 |

Les nouveaux certificats TLS utilisés par les services Microsoft 365 vont maintenant s’enchaîner jusqu’à l’une des autorités de certification racine suivantes :

| Nom commun de l’autorité de certification | Empreinte numérique (SHA1) |
|--|--|
| [DigiCert Global Root G2](https://cacerts.digicert.com/DigiCertGlobalRootG2.crt) | df3c24f9bfd666761b268073fe06d1cc8d4f82a4 |
| [Autorité de certification racine Microsoft RSA 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crt) | 73a5e64a3bff8316ff0edccc618a906e4eae4d74 | 
| [Autorité de certification racine Microsoft ECC 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crt) | 999a64c37ff47d9fab95f14769891460eec4c3c5 |

avec l’une des autorités de certification intermédiaires suivantes :

| Nom commun de l’autorité de certification | Empreinte numérique (SHA1) |
|--|--|
| [Microsoft Azure TLS Émission CA 01](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2001%20-%20xsign.crt) | 2f2877c5d778c31e0f29c7e371df5471bd673173 |
| [Microsoft Azure TLS émettant l’autorité de certification 02](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2002%20-%20xsign.crt) | e7eea674ca718e3befd90858e09f8372ad0ae2aa |
| [Microsoft Azure TLS émettant l’autorité de certification 05](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2005%20-%20xsign.crt) | 6c3af02e7f269aa73afd0eff2a88a4a1f04ed1e5 |
| [Microsoft Azure TLS émettant l’autorité de certification 06](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2006%20-%20xsign.crt) | 30e01761ab97e59a06b41ef20af6f2de7ef4f7b0 |

Par exemple, il s’agit d’un certificat valide avec l’une des nouvelles chaînes de certificats :

![Chaîne de certificats TLS Teams](../media/teams-tls-certificate-chain.png)

## <a name="will-this-change-affect-me"></a>Ce changement va-t-il m’affecter ?

L’autorité de certification racine « DigiCert Global Root G2 » est largement approuvée par les systèmes d’exploitation, notamment Windows, macOS, Android et iOS, et par des navigateurs tels que Microsoft Edge, Chrome, Safari et Firefox. Nous nous attendons à ce que **la plupart des clients Microsoft 365 ne soient pas affectés**. 

Toutefois, **votre application peut être affectée si elle spécifie explicitement une liste d’autorités de certification acceptables**. Cette pratique est appelée « épinglage de certificat ». Les clients qui n’ont pas les nouvelles autorités de certification racine dans leur liste d’autorités de certification acceptables recevront des erreurs de validation de certificat, ce qui peut avoir un impact sur la disponibilité ou la fonction de votre application.

Voici quelques façons de détecter si votre application peut être impactée :

- Recherchez dans votre code source l’empreinte numérique, le nom commun ou d’autres propriétés de l’une des autorités de certification intermédiaires trouvées [ici](https://www.microsoft.com/pki/mscorp/cps/default.htm). S’il existe une correspondance, votre application sera affectée. Pour résoudre ce problème, mettez à jour le code source pour ajouter les propriétés des nouvelles autorités de certification. En guise de bonne pratique, assurez-vous que les autorités de certification peuvent être ajoutées ou modifiées à court préavis. Les réglementations du secteur exigent que les certificats d’autorité de certification soient remplacés dans un délai de sept jours dans certaines circonstances, de sorte que les applications qui implémentent l’épinglage de certificat doivent réagir rapidement à ces modifications.

- .NET expose les `System.Net.ServicePointManager.ServerCertificateValidationCallback` fonctions de rappel, `System.Net.HttpWebRequest.ServerCertificateValidationCallback` qui permettent aux développeurs d’utiliser une logique personnalisée pour déterminer si les certificats sont valides plutôt que de s’appuyer sur le magasin de certificats Windows standard. Un développeur peut ajouter une logique qui recherche un nom commun ou une empreinte numérique spécifique ou autorise uniquement une autorité de certification racine spécifique telle que « Baltimore CyberTrust Root ». Si votre application utilise ces fonctions de rappel, vous devez vous assurer qu’elle accepte à la fois l’ancienne et la nouvelle autorité de certification racine et intermédiaire.

- Les applications natives peuvent utiliser `WINHTTP_CALLBACK_STATUS_SENDING_REQUEST`, ce qui permet aux applications natives d’implémenter une logique de validation de certificat personnalisée. L’utilisation de cette notification est rare et nécessite une quantité importante de code personnalisé à implémenter. À l’instar de ce qui précède, assurez-vous que votre application accepte les autorités de certification racines et intermédiaires anciennes et nouvelles. 

- Si vous utilisez une application qui s’intègre à Microsoft Teams, Skype, Skype Entreprise Online ou aux API Microsoft Dynamics et que vous ne savez pas si elle utilise l’épinglage de certificat, contactez le fournisseur de l’application.

- Les différents systèmes d’exploitation et runtimes linguistiques qui communiquent avec les services Azure peuvent nécessiter d’autres étapes pour générer et valider correctement les nouvelles chaînes de certificats :
   - **Linux** : de nombreuses distributions vous obligent à ajouter des autorités de certification à `/etc/ssl/certs`. Pour obtenir des instructions spécifiques, reportez-vous à la documentation de la distribution.
   - **Java** : vérifiez que le magasin de clés Java contient les autorités de certification répertoriées ci-dessus.
   - **Windows s’exécutant dans des environnements déconnectés** : les systèmes qui s’exécutent dans des environnements déconnectés doivent avoir les nouvelles autorités de certification racine ajoutées à leur `Trusted Root Certification Authorities` magasin et les nouvelles autorités de certification intermédiaires ajoutées à leur `Intermediate Certification Authorities` magasin.
   - **Android** : consultez la documentation de votre appareil et de votre version d’Android.
   - **IoT ou appareils incorporés** : les appareils incorporés, tels que les zones haut de gamme tv, sont souvent fournis avec un ensemble limité de certificats d’autorité racine et n’ont pas de moyen simple de mettre à jour le magasin de certificats. Si vous écrivez du code pour ou gérez des déploiements d’appareils incorporés ou IoT personnalisés, assurez-vous que les appareils approuvent les nouvelles autorités de certification racine. Vous devrez peut-être contacter le fabricant de l’appareil.

- Si vous avez un environnement dans lequel les règles de pare-feu autorisent les appels sortants uniquement vers des points de terminaison spécifiques, autorisez les URL de liste de révocation de certificats (CRL) ou OCSP (Online Certificate Status Protocol) suivantes :
   - `http://crl3.digicert.com`
   - `http://crl4.digicert.com`
   - `http://ocsp.digicert.com`
   - `http://crl.microsoft.com`
   - `http://oneocsp.microsoft.com`
   - `http://ocsp.msocsp.com`
   - `http://www.microsoft.com/pkiops`

- Si cette modification vous affecte, il se peut que des messages d’erreur dépendent du type d’environnement dans lequel vous exécutez et du scénario dans lequel vous êtes affecté. Vérifiez les journaux des événements d’application Windows, les journaux des événements CAPI2 et les journaux d’application personnalisés pour les messages qui ressemblent à ceci :
   ```output
   An operation failed because the following certificate has validation errors:
   
   Subject Name: CN=teams.microsoft.com
   Issuer Name: CN=Microsoft Azure TLS Issuing CA 01, O=Microsoft Corporation, C=US
   
   Errors:
   
   The root of the certificate chain is not a trusted root authority.
   ```

## <a name="when-can-i-retire-the-old-ca-information"></a>Quand puis-je mettre hors service les anciennes informations d’autorité de certification ?

L’autorité de certification racine, l’autorité de certification intermédiaire et les certificats feuille actuels ne seront pas révoqués. Les noms communs d’autorité de certification existants et/ou les empreintes numériques seront requis au moins jusqu’en octobre 2023 en fonction de la durée de vie des certificats existants.

## <a name="known-issues"></a>Problèmes connus

Dans de très rares cas, les utilisateurs d’entreprise peuvent voir des erreurs de validation de certificat lorsque l’autorité de certification racine « DigiCert Global Root G2 » apparaît comme révoquée. Cela est dû à un bogue Windows connu dans les deux conditions suivantes :

- L’autorité de certification racine se trouve dans le [magasin de certificats CurrentUser\Root](/windows/win32/seccrypto/system-store-locations#cert_system_store_current_user) et il manque les propriétés et `NotBeforeEKU` les `NotBeforeFileTime`
- L’autorité de certification racine se trouve dans le [magasin de certificats LocalMachine\AuthRoot](/windows/win32/seccrypto/system-store-locations#cert_system_store_local_machine), mais possède les propriétés et `NotBeforeEKU` les propriétés `NotBeforeFileTime`
- L’autorité de certification racine n’est PAS dans le [magasin de certificats LocalMachine\Root](/windows/win32/seccrypto/system-store-locations#cert_system_store_local_machine)

Tous les certificats feuille émis à partir de cette autorité de certification racine après la `NotBeforeFileTime` révoquer. 

Les administrateurs peuvent identifier et résoudre le problème en inspectant le journal CAPI2 pour détecter cette erreur :

```text
Log Name:      Microsoft-Windows-CAPI2/Operational
Source:        Microsoft-Windows-CAPI2
Date:          6/23/2022 8:36:39 AM
Event ID:      11
Task Category: Build Chain
Level:         Error
[...]
        <ChainElement>
          <Certificate fileRef="DF3C24F9BFD666761B268073FE06D1CC8D4F82A4.cer" subjectName="DigiCert Global Root G2" />
          [...]
          <TrustStatus>
            <ErrorStatus value="4000024" CERT_TRUST_IS_REVOKED="true" CERT_TRUST_IS_UNTRUSTED_ROOT="true" CERT_TRUST_IS_EXPLICIT_DISTRUST="true" />
            <InfoStatus value="10C" CERT_TRUST_HAS_NAME_MATCH_ISSUER="true" CERT_TRUST_IS_SELF_SIGNED="true" CERT_TRUST_HAS_PREFERRED_ISSUER="true" />
          </TrustStatus>
          [...]
          <RevocationInfo freshnessTime="PT0S">
            <RevocationResult value="80092010">The certificate is revoked.</RevocationResult>
          </RevocationInfo>
        </ChainElement>
      </CertificateChain>
      <EventAuxInfo ProcessName="Teams.exe" />
      <Result value="80092010">The certificate is revoked.</Result>
```
Notez la présence de l’élément `CERT_TRUST_IS_EXPLICIT_DISTRUST="true"` . 

Vous pouvez vérifier que deux copies de l’autorité de certification racine avec des propriétés différentes `NotBeforeFileTime` sont présentes en exécutant les commandes suivantes `certutil` et en comparant la sortie :

```
certutil -store -v authroot DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
certutil -user -store -v root DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
```

Un utilisateur peut résoudre le problème en supprimant la copie de l’autorité de certification racine dans le `CurrentUser\Root` magasin de certificats en procédant comme ceci :
```
certutil -user -delstore root DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
```
ou 
```
reg delete HKCU\SOFTWARE\Microsoft\SystemCertificates\Root\Certificates\DF3C24F9BFD666761B268073FE06D1CC8D4F82A4 /f
```
La première approche crée une boîte de dialogue Windows qu’un utilisateur doit cliquer alors que la deuxième approche ne le fait pas. 