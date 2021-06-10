---
title: Détails techniques de référence sur le chiffrement
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
- Strat_O365_IP
search.appverid:
- MET150
- MOE150
ms.assetid: 862cbe93-4268-4ef9-ba79-277545ecf221
description: Découvrez les différents certificats, technologies et suites de chiffrement TLS (Transport Layer Security) utilisés pour le chiffrement dans Office 365 et Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e7e50ea399cd694f512e0538de3f7e67c63ee0e3
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50919350"
---
# <a name="technical-reference-details-about-encryption"></a>Détails techniques de référence sur le chiffrement

Reportez-vous à cet article pour en savoir plus sur les certificats, les technologies et les suites de chiffrement TLS utilisés pour le chiffrement [dans Office 365](encryption.md). Cet article fournit également des détails sur les annulations planifiées.
  
- Si vous recherchez des informations générales, voir [Chiffrement dans Office 365](encryption.md).
- Si vous recherchez des informations d’installation, voir Configurer le chiffrement [dans Office 365 Entreprise](set-up-encryption.md).
- Pour plus d’informations sur les suites de chiffrement pris en charge par des versions spécifiques de Windows, voir [Cipher Suites dans TLS/SSL (SSP Schannel).](/windows/desktop/SecAuthN/cipher-suites-in-schannel)

## <a name="microsoft-office-365-certificate-ownership-and-management"></a>Gestion et propriété de certificats Microsoft Office 365

Vous n’avez pas besoin d’acheter ou de gérer des certificats pour Office 365. Au lieu de cela, Office 365 utilise ses propres certificats.
  
## <a name="current-encryption-standards-and-planned-deprecations"></a>Normes de chiffrement actuelles et dépréciations planifiées

Pour fournir un chiffrement de qualité supérieure, Office 365 examine régulièrement les normes de chiffrement pris en charge. Parfois, les anciennes normes sont dépréciées à mesure qu’elles deviennent plus anciennes et moins sécurisées. Cet article décrit les suites de chiffrement actuellement pris en charge, ainsi que d’autres normes et détails sur les déprédations planifiées.

## <a name="fips-compliance-for-office-365"></a>Conformité FIPS pour les Office 365

Toutes les suites de chiffrement Office 365 utilisent des algorithmes acceptables sous FIPS 140-2. Office 365 hérite des validations FIPS de Windows (via Schannel). Pour plus d’informations sur Schannel, voir [Cipher Suites dans TLS/SSL (SSP Schannel).](/windows/desktop/SecAuthN/cipher-suites-in-schannel)
  
## <a name="versions-of-tls-supported-by-office-365"></a>Versions de TLS prises en charge par Office 365

Les protocoles TLS et SSL qui étaient avant le protocole TLS sont des protocoles de chiffrement qui sécurisationnt les communications via un réseau à l’aide de certificats de sécurité pour chiffrer une connexion entre les ordinateurs. Office 365 prend en charge TLS version 1.2 (TLS 1.2).

TLS version 1.3 (TLS 1.3) n’est actuellement pas pris en charge.
  
## <a name="support-for-tls-10-and-11-deprecation"></a>Prise en charge de l’annulation de TLS 1.0 et 1.1

Office 365 prise en charge de TLS 1.0 et 1.1 le 31 octobre 2018. Nous avons terminé la désactivation de TLS 1.0 et 1.1 dans les environnements Cloud de la communauté du secteur public et DoD. Nous avons commencé à désactiver TLS 1.0 et 1.1 pour les environnements internationaux et Cloud de la communauté du secteur public à partir du 15 octobre 2020 et nous continuerons le déploiement au cours des prochaines semaines et mois.

Pour maintenir une connexion sécurisée aux services Office 365 et Microsoft 365, toutes les combinaisons client-serveur et navigateur-serveur utilisent TLS 1.2 et les suites de chiffrement modernes. Il se peut que vous deviez procéder à la mise à jour de certaines combinaisons client-serveur et navigateur-serveur. Pour plus d’informations sur l’impact de cette modification sur vous, voir Préparation de l’utilisation obligatoire de [TLS 1.2 dans Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).
  
## <a name="deprecating-support-for-3des"></a>Désaccatation de la prise en charge de 3DES

Depuis le 31 octobre 2018, Office 365 ne prend plus en charge l’utilisation des suites de chiffrement 3DES pour la communication Office 365. Plus spécifiquement, Office 365 ne prend plus en charge la suite TLS_RSA_WITH_3DES_EDE_CBC_SHA chiffrement. Depuis le 28 février 2019, cette suite de chiffrement est désactivée dans Office 365. Les clients et serveurs qui communiquent Office 365 doivent prendre en charge un ou plusieurs chiffrements pris en charge. Pour obtenir la liste des chiffrements pris en charge, voir les suites de chiffrement [TLS](#tls-cipher-suites-supported-by-office-365)pris en charge par Office 365 .
  
## <a name="deprecating-sha-1-certificate-support-in-office-365"></a>Arrêt de la prise en charge du certificat SHA-1 dans Office 365

Depuis juin 2016, Office 365 n’accepte plus de certificat SHA-1 pour les connexions sortantes ou entrantes. Utilisez SHA-2 (Secure Hash Algorithm 2) ou un algorithme de hachage plus puissant dans la chaîne de certificats.
  
## <a name="tls-cipher-suites-supported-by-office-365"></a>Suites de chiffrement TLS pris en charge par Office 365

TLS utilise *des suites de chiffrement,* des collections d’algorithmes de chiffrement, pour établir des connexions sécurisées. Office 365 prend en charge les suites de chiffrement répertoriées dans le tableau suivant. Le tableau répertorie les suites de chiffrement par ordre de force, avec la suite de chiffrement la plus forte répertoriée en premier.

Office 365 répond à une demande de connexion en essayant d’abord de se connecter à l’aide de la suite de chiffrement la plus sécurisée. Si la connexion ne fonctionne pas, Office 365 la deuxième suite de chiffrement la plus sécurisée de la liste, et ainsi de suite. Le service continue dans la liste jusqu’à ce que la connexion soit acceptée. De même, lorsque Office 365 demande une connexion, le service de réception choisit si TLS sera utilisé et quelle suite de chiffrement utiliser.

> [!IMPORTANT]
> N’oubliez pas que les versions TLS sont  dépréciées et qu’elles ne doivent pas être utilisées lorsque des versions plus récentes sont disponibles. TLS 1.3 n’est actuellement pas pris en charge. Si vos services hérités ne nécessitent pas TLS 1.0 ou 1.1, vous devez les désactiver.

| Suite de chiffrement | Algorithme/force d’échange de clés | Forward Secrecy | Chiffrement/puissance | Algorithme d’authentification |
|:-----|:-----|:-----|:-----|:-----|
|TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 <br/>     |ECDH/192 <br/>|Oui <br/>|AES/256 <br/>|RSA/112 <br/> |
|TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 <br/>     |ECDH/128 <br/>|Oui <br/>|AES/128 <br/>|RSA/112 <br/> |
|TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384 <br/>     |ECDH/192 <br/>|Oui <br/>|AES/256 <br/>|RSA/112 <br/> |
|TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256 <br/>     |ECDH/128 <br/>|Oui <br/>|AES/128 <br/>|RSA/112 <br/> |
|TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA <br/>        |ECDH/192 <br/>|Oui <br/>|AES/256 <br/>|RSA/112 <br/> |
|TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA <br/>        |ECDH/128 <br/>|Oui <br/>|AES/128 <br/>|RSA/112 <br/> |
|TLS_RSA_WITH_AES_256_GCM_SHA384 <br/>           |RSA/112 <br/> |Non <br/> |AES/256 <br/>|RSA/112 <br/> |
|TLS_RSA_WITH_AES_128_GCM_SHA256 <br/>           |RSA/112 <br/> |Non <br/> |AES/256 <br/>|RSA/112 <br/> |

Ces suites de chiffrement ont pris en charge les protocoles TLS 1.0 et 1.1 jusqu’à leur date d’annulation. Pour Cloud de la communauté du secteur public les environnements Haut et DoD dont la date de désinsion était le 15 janvier 2020 et pour les environnements internationaux et Cloud de la communauté du secteur public qui datent du 15 octobre 2020.

| Protocoles | Nom de suite de chiffrement | Algorithme d’échange de clés/Force | Prise en charge du secret avant | Algorithme d’authentification/Force | Chiffrement/Force |
|:-----|:-----|:-----|:-----|:-----|:-----|
|TLS 1.0, 1.1, 1.2  <br/> |TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA  <br/> |ECDH/192  <br/> |Oui  <br/> |RSA/112  <br/> |AES/256  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA  <br/> |ECDH/128  <br/> |Oui  <br/> |RSA/112  <br/> |AES/128  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_RSA_WITH_AES_256_CBC_SHA        <br/> |RSA/112  <br/>  |Non  <br/>  |RSA/112  <br/> |AES/256  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_RSA_WITH_AES_128_CBC_SHA        <br/> |RSA/112  <br/>  |Non  <br/>  |RSA/112  <br/> |AES/128  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_RSA_WITH_AES_256_CBC_SHA256     <br/> |RSA/112  <br/>  |Non   <br/> |RSA/112  <br/> |AES/256  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_RSA_WITH_AES_128_CBC_SHA256     <br/> |RSA/112  <br/>  |Non   <br/> |RSA/112  <br/> |AES/256  <br/> |

## <a name="related-articles"></a>Articles connexes

[Suites de chiffrement TLS Windows 10 v1903](/windows/win32/secauthn/tls-cipher-suites-in-windows-10-v1903)

[Chiffrement dans Office 365](encryption.md)
  
[Configurer le chiffrement dans Office 365 Entreprise](set-up-encryption.md)
  
[Implémentation de Schannel de TLS 1.0 dans Windows mise à jour de l’état de sécurité : 24 novembre 2015](https://support.microsoft.com/kb/3117336)
  
[Améliorations du chiffrement TLS/SSL (Windows IT Center)](/previous-versions/windows/it-pro/windows-vista/cc766285(v=ws.10))
  
[Préparation de TLS 1.2 dans Office 365 et Office 365 Cloud de la communauté du secteur public](/office365/troubleshoot/security/prepare-tls-1.2-in-office-365)