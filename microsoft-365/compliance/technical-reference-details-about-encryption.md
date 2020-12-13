---
title: Détails techniques de référence sur le chiffrement
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 06/15/2020
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
ms.openlocfilehash: 244d7a6cef6d77322475245435dafb6c89ab5353
ms.sourcegitcommit: 47de4402174c263ae8d70c910ca068a7581d04ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "49663427"
---
# <a name="technical-reference-details-about-encryption"></a>Détails techniques de référence sur le chiffrement

Consultez cet article pour en savoir plus sur les certificats, les technologies et les suites de chiffrement TLS utilisées pour le [chiffrement dans Office 365](encryption.md). Cet article fournit également des détails sur les désapprobations planifiées.
  
- Si vous souhaitez obtenir des informations générales, consultez la rubrique [chiffrement dans Office 365](encryption.md).
- Si vous recherchez des informations de configuration, reportez-vous à la rubrique [set up Encryption in Office 365 Enterprise](set-up-encryption.md).
- Pour plus d’informations sur les suites de chiffrement prises en charge par des versions spécifiques de Windows, voir [cipher Suites in TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/cipher-suites-in-schannel).

## <a name="microsoft-office-365-certificate-ownership-and-management"></a>Gestion et propriété de certificats Microsoft Office 365

Vous n’avez pas besoin d’acheter ni de gérer les certificats pour Office 365. Au lieu de cela, Office 365 utilise ses propres certificats.
  
## <a name="current-encryption-standards-and-planned-deprecations"></a>Normes de chiffrement actuelles et désapprobations planifiées

Pour fournir un chiffrement de meilleure qualité, Office 365 examine régulièrement les normes de chiffrement prises en charge. Parfois, les anciennes normes sont déconseillées lorsqu’elles deviennent obsolètes et moins sûres. Cet article décrit les suites de chiffrement actuellement prises en charge, ainsi que d’autres normes et informations sur les désapprobations planifiées.

## <a name="fips-compliance-for-office-365"></a>Conformité FIPS pour Office 365

Toutes les suites de chiffrement prises en charge par Office 365 utilisent des algorithmes acceptables sous FIPS 140-2. Office 365 hérite des validations FIPS de Windows (via Schannel). Pour plus d’informations sur Schannel, voir [cipher Suites in TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/cipher-suites-in-schannel).
  
## <a name="versions-of-tls-supported-by-office-365"></a>Versions de TLS prises en charge par Office 365

TLS et SSL, qui sont fournis avant TLS, sont des protocoles de chiffrement qui sécurisent la communication sur un réseau à l’aide de certificats de sécurité pour chiffrer une connexion entre les ordinateurs. Office 365 prend en charge la version TLS 1,2 (TLS 1,2).

La version TLS 1,3 (TLS 1,3) n’est pas prise en charge actuellement.
  
## <a name="support-for-tls-10-and-11-deprecation"></a>Prise en charge des protocoles TLS 1,0 et 1,1

Office 365 a cessé de prendre en charge les protocoles TLS 1,0 et 1,1 le 31 octobre 2018. Les nouveaux problèmes détectés dans les clients, les appareils ou les services qui se connectent à Office 365 sur TLS 1,0 et 1,1 ne seront pas résolus. La désapprobation officielle des environnements GCC High et DoD a débuté le 15 janvier 2020. La dépréciation des protocoles TLS 1,0 et 1,1 pour les environnements internationaux et de GCC a débuté le 15 octobre 2020.

Pour maintenir une connexion sécurisée avec les services Office 365 et Microsoft 365, toutes les combinaisons client-serveur et navigateur-serveur utilisent TLS 1,2 et les suites de chiffrement modernes. Il se peut que vous deviez procéder à la mise à jour de certaines combinaisons client-serveur et navigateur-serveur. Pour plus d’informations sur l’impact de cette modification, consultez [la rubrique préparation de l’utilisation obligatoire de TLS 1,2 dans Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).
  
## <a name="deprecating-support-for-3des"></a>Dépréciation de la prise en charge 3DES

Depuis le 31 octobre 2018, Office 365 ne prend plus en charge l’utilisation de suites de chiffrement 3DES pour communiquer avec Office 365. Plus spécifiquement, Office 365 ne prend plus en charge la suite de chiffrement TLS_RSA_WITH_3DES_EDE_CBC_SHA. Depuis le 28 février 2019, cette suite de chiffrement a été désactivée dans Office 365. Les clients et les serveurs qui communiquent avec Office 365 doivent prendre en charge un ou plusieurs chiffrements pris en charge. Pour obtenir la liste des chiffrements pris en charge, voir [suites de chiffrement TLS prises en charge par Office 365](#tls-cipher-suites-supported-by-office-365).
  
## <a name="deprecating-sha-1-certificate-support-in-office-365"></a>Arrêt de la prise en charge du certificat SHA-1 dans Office 365

Depuis le 2016 juin, Office 365 n’accepte plus de certificat SHA-1 pour les connexions entrantes ou sortantes. Utilisez SHA-2 (Secure Hash Algorithm 2) ou un algorithme de hachage plus puissant dans la chaîne de certificats.
  
## <a name="tls-cipher-suites-supported-by-office-365"></a>Suites de chiffrement TLS prises en charge par Office 365

TLS utilise des *Suites* de chiffrement, des ensembles d’algorithmes de chiffrement, pour établir des connexions sécurisées. Office 365 prend en charge les suites de chiffrement indiquées dans le tableau suivant. Le tableau répertorie les suites de chiffrement par ordre de force, la suite de chiffrement la plus forte répertoriée en premier.

Office 365 répond à une demande de connexion en tentant d’abord de se connecter à l’aide de la suite de chiffrement la plus sécurisée. Si la connexion ne fonctionne pas, Office 365 essaie la deuxième suite de chiffrement la plus sécurisée dans la liste, et ainsi de suite. Le service se poursuit vers le bas de la liste jusqu’à ce que la connexion soit acceptée. De même, lorsque Office 365 demande une connexion, le service de réception détermine si TLS sera utilisé et la suite de chiffrement à utiliser.

> [!IMPORTANT]
> N’oubliez pas que les versions de TLS sont déconseillées et que les versions déconseillées ne *doivent pas être utilisées* lorsque des versions plus récentes sont disponibles. TLS 1,3 n’est actuellement pas pris en charge. Si vos services hérités ne requièrent pas TLS 1,0 ou 1,1, vous devez les désactiver.

| Suite de chiffrement | Algorithme/force d’échange de clés | Confidentialité de transmission parfaite | Chiffrement/force | Algorithme d’authentification |
|:-----|:-----|:-----|:-----|:-----|
|TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 <br/>     |ECDH/192 <br/>|Oui <br/>|AES/256 <br/>|RSA/112 <br/> |
|TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 <br/>     |ECDH/128 <br/>|Oui <br/>|AES/128 <br/>|RSA/112 <br/> |
|TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384 <br/>     |ECDH/192 <br/>|Oui <br/>|AES/256 <br/>|RSA/112 <br/> |
|TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256 <br/>     |ECDH/128 <br/>|Oui <br/>|AES/128 <br/>|RSA/112 <br/> |
|TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA <br/>        |ECDH/192 <br/>|Oui <br/>|AES/256 <br/>|RSA/112 <br/> |
|TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA <br/>        |ECDH/128 <br/>|Oui <br/>|AES/128 <br/>|RSA/112 <br/> |
|TLS_RSA_WITH_AES_256_GCM_SHA384 <br/>           |RSA/112 <br/> |Non <br/> |AES/256 <br/>|RSA/112 <br/> |
|TLS_RSA_WITH_AES_128_GCM_SHA256 <br/>           |RSA/112 <br/> |Non <br/> |AES/256 <br/>|RSA/112 <br/> |

Ces suites de chiffrement prenait en charge les protocoles TLS 1,0 et 1,1 jusqu’à leur date de désapprobation. Pour les environnements GCC High et DoD dont la date de dépréciation était le 15 janvier 2020, et pour les environnements internationaux et GCC date du 15 octobre 2020.

| Protocoles | Nom de suite de chiffrement | Algorithme/force d’échange de clés | Prise en charge du secret de transfert parfait | Algorithme/force d’authentification | Chiffrement/force |
|:-----|:-----|:-----|:-----|:-----|:-----|
|TLS 1.0, 1.1, 1.2  <br/> |TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA  <br/> |ECDH/192  <br/> |Oui  <br/> |RSA/112  <br/> |AES/256  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA  <br/> |ECDH/128  <br/> |Oui  <br/> |RSA/112  <br/> |AES/128  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_RSA_WITH_AES_256_CBC_SHA        <br/> |RSA/112  <br/>  |Non  <br/>  |RSA/112  <br/> |AES/256  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_RSA_WITH_AES_128_CBC_SHA        <br/> |RSA/112  <br/>  |Non  <br/>  |RSA/112  <br/> |AES/128  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_RSA_WITH_AES_256_CBC_SHA256     <br/> |RSA/112  <br/>  |Non   <br/> |RSA/112  <br/> |AES/256  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_RSA_WITH_AES_128_CBC_SHA256     <br/> |RSA/112  <br/>  |Non   <br/> |RSA/112  <br/> |AES/256  <br/> |

## <a name="related-articles"></a>Articles connexes

[Suites de chiffrement TLS dans Windows 10 v1903](https://docs.microsoft.com/windows/win32/secauthn/tls-cipher-suites-in-windows-10-v1903)

[Chiffrement dans Office 365](encryption.md)
  
[Configurer le chiffrement dans Office 365 Entreprise](set-up-encryption.md)
  
[Implémentation Schannel de TLS 1,0 dans la mise à jour de l’état de sécurité Windows : 24 novembre 2015](https://support.microsoft.com/kb/3117336)
  
[Améliorations de chiffrement TLS/SSL (centre informatique Windows)](https://technet.microsoft.com/library/cc766285%28v=ws.10%29.aspx)
  
[Préparation de TLS 1.2 dans Office 365 et Office 365 GCC](https://docs.microsoft.com/office365/troubleshoot/security/prepare-tls-1.2-in-office-365)
