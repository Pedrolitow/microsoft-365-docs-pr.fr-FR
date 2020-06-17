---
title: Informations de référence technique sur le chiffrement
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
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
ms.assetid: 862cbe93-4268-4ef9-ba79-277545ecf221
description: Découvrez les différents certificats, technologies et suites de chiffrement TLS utilisés pour le chiffrement dans Office 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 298d73551b5eb3d7ad7121075b086ee4630562f4
ms.sourcegitcommit: 9ea67fd2e02af760d4fb62e3d09c93b446173f9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44739108"
---
# <a name="technical-reference-details-about-encryption"></a>Informations de référence technique sur le chiffrement

Consultez cet article pour en savoir plus sur les certificats, les technologies et les suites de chiffrement TLS utilisées pour le [chiffrement dans Office 365](encryption.md). Cet article fournit également des détails sur les désapprobations planifiées.
  
- Si vous souhaitez obtenir des informations générales, consultez la rubrique [chiffrement dans Office 365](encryption.md).
- Si vous recherchez des informations de configuration, reportez-vous à la rubrique [set up Encryption in Office 365 Enterprise](set-up-encryption.md).
- Pour plus d’informations sur les suites de chiffrement prises en charge par des versions spécifiques de Windows, voir [cipher Suites in TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/cipher-suites-in-schannel).

## <a name="microsoft-office-365-certificate-ownership-and-management"></a>Gestion et propriété de certificats Microsoft Office 365

Il est inutile d’acheter ou de mettre à jour les certificats pour Office 365 car Microsoft utilise ses propres certificats.
  
## <a name="current-encryption-standards-and-planned-deprecations"></a>Normes de chiffrement actuelles et désapprobations planifiées

Pour continuer à fournir le chiffrement le plus approprié pour Office 365, Microsoft vérifie régulièrement les standards de chiffrement pris en charge. Parfois, nous devons déprécier les anciennes normes lorsqu’elles deviennent obsolètes et donc moins sécurisées. Cette rubrique décrit les suites de chiffrement actuellement prises en charge, ainsi que d’autres normes, ainsi que des détails sur les désapprobations planifiées. 

## <a name="fips-compliance-for-office-365"></a>Conformité FIPS pour Office 365

Toutes les suites de chiffrement prises en charge par Office 365 utilisent des algorithmes acceptables sous FIPS 140-2. Office 365 hérite des validations FIPS de Windows (via Schannel). Pour plus d’informations sur Schannel, voir [cipher Suites in TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/cipher-suites-in-schannel).
  
## <a name="versions-of-tls-supported-by-office-365"></a>Versions de TLS prises en charge par Office 365

Les protocoles TLS (Transport Layer Security) et SSL (antérieur au protocole TLS) sont des protocoles de chiffrement qui sécurisent les communications sur un réseau à l’aide de certificats de sécurité pour chiffrer une connexion entre plusieurs ordinateurs. Office 365 prend en charge la version TLS 1,2 (TLS 1,2).

La version TLS 1,3 (TLS 1,3) n’est pas prise en charge actuellement.
  
## <a name="support-for-tls-10-and-11-deprecation-and-what-this-means-for-you"></a>Prise en charge des protocoles TLS 1,0 et 1,1 déconseillée et ce que cela signifie pour vous

Depuis le 31 octobre 2018, Office 365 ne prend plus en charge TLS 1,0 et 1,1. Dès lors, Microsoft ne résoudra pas les nouveaux problèmes détectés au niveau des clients, des appareils ou des services qui se connectent à Office 365 à l’aide de TLS 1.0 et 1.1.

Cela ne signifie pas que Office 365 bloquera les connexions TLS 1,0 et 1,1.

TLS 1,0 et TLS 1,1 étaient officiellement obsolètes à ces dates.

- Le 1er juin 2020 dans les environnements mondiaux et GCC.
- 15 janvier 2020 dans les environnements GCC High et DoD.

Vous devez vous assurer que toutes les combinaisons client-serveur et navigateur-serveur utilisent TLS 1,2 et des suites de chiffrement modernes pour maintenir une connexion sécurisée avec Office 365 et les services Microsoft 365. Il se peut que vous deviez procéder à la mise à jour de certaines combinaisons client-serveur et navigateur-serveur. Pour plus d’informations sur la façon dont cela vous affecte, consultez [la rubrique préparation de l’utilisation obligatoire de TLS 1,2 dans Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).
  
## <a name="deprecating-support-for-3des"></a>Dépréciation de la prise en charge 3DES

Depuis le 31 octobre 2018, Office 365 ne prend plus en charge l’utilisation de suites de chiffrement 3DES pour communiquer avec Office 365. Plus spécifiquement, Office 365 ne prend plus en charge la suite de chiffrement TLS_RSA_WITH_3DES_EDE_CBC_SHA. Depuis le 28 février 2019, cette suite de chiffrement a été désactivée dans Office 365. Les clients et les serveurs communiquant avec Office 365 après cette date doivent prendre en charge au moins l’un des chiffrements les plus sécurisés mentionnés dans cette rubrique (voir les [suites de chiffrement TLS prises en charge par Office 365](#tls-cipher-suites-supported-by-office-365)).
  
## <a name="deprecating-sha-1-certificate-support-in-office-365"></a>Arrêt de la prise en charge du certificat SHA-1 dans Office 365

Depuis juin 2016, Office 365 n’accepte plus de certificat SHA-1 pour les connexions entrantes ou sortantes. Si vous utilisez actuellement un certificat avec l’algorithme SHA-1 dans la chaîne de certificats, vous devrez mettre à jour la chaîne pour utiliser SHA-2 (Secure Hash Algorithm 2) ou un algorithme de hachage plus puissant.
  
## <a name="tls-cipher-suites-supported-by-office-365"></a>Suites de chiffrement TLS prises en charge par Office 365

Une suite de chiffrement est un ensemble d’algorithmes de chiffrement utilisés par le protocole TLS pour établir des connexions sécurisées. Les suites de chiffrement prises en charge par Office 365 sont répertoriées dans le tableau suivant par niveau décroissant. Lorsque Office 365 reçoit une demande de connexion, Office 365 tente d’abord de se connecter à l’aide de la suite de chiffrement de niveau supérieur. Ensuite, si l’opération échoue, Office 365 essaie la deuxième suite de chiffrement dans la liste, et ainsi de suite. Quand Office 365 envoie une demande de connexion à un autre serveur ou à un client, il incombe au client ou au serveur de réception de choisir la suite de chiffrement ou de déterminer s’il convient d’utiliser le protocole TLS.

> [!IMPORTANT]
> N’oubliez pas que les versions de TLS sont déconseillées et que les versions déconseillées ne *doivent pas être utilisées* lorsque des versions plus récentes sont disponibles. TLS 1,3 n’est actuellement pas pris en charge. Si vos services hérités ne requièrent pas TLS 1,0 ou 1,1, vous devez les désactiver.
  
|**Protocoles**|**Nom de suite de chiffrement**|**Algorithme/force d’échange de clés**|**Prise en charge du secret de transfert parfait**|**Algorithme/force d’authentification**|**Chiffrement/force**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|TLS 1.2  <br/> |TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384  <br/> |ECDH/192  <br/> |Oui  <br/> |RSA/112  <br/> |AES/256  <br/> |
|TLS 1.2  <br/> |TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256  <br/> |ECDH/128  <br/> |Oui  <br/> |RSA/112  <br/> |AES/128  <br/> |
|TLS 1.2  <br/> |TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384_P384  <br/> |ECDH/192  <br/> |Oui  <br/> |RSA/112  <br/> |AES/256  <br/> |
|TLS 1.2  <br/> |TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256_P256  <br/> |ECDH/128  <br/> |Oui  <br/> |RSA/112  <br/> |AES/128  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA_P384  <br/> |ECDH/192  <br/> |Oui  <br/> |RSA/112  <br/> |AES/256  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA_P256  <br/> |ECDH/128  <br/> |Oui  <br/> |RSA/112  <br/> |AES/128  <br/> |
|TLS 1.2  <br/> |TLS_RSA_WITH_AES_256_CBC_SHA256  <br/> |RSA/112  <br/> |Non  <br/> |RSA/112  <br/> |AES/256  <br/> |
|TLS 1.2  <br/> |TLS_RSA_WITH_AES_128_CBC_SHA256  <br/> |RSA/112  <br/> |Non  <br/> |RSA/112  <br/> |AES/128  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_RSA_WITH_AES_256_CBC_SHA  <br/> |RSA/112  <br/> |Non  <br/> |RSA/112  <br/> |AES/256  <br/> |
|TLS 1.0, 1.1, 1.2  <br/> |TLS_RSA_WITH_AES_128_CBC_SHA  <br/> |RSA/112  <br/> |Non  <br/> |RSA/112  <br/> |AES/128  <br/> |
   
## <a name="related-topics"></a>Voir aussi
[Suites de chiffrement TLS dans Windows 10 v1903](https://docs.microsoft.com/windows/win32/secauthn/tls-cipher-suites-in-windows-10-v1903)

[Chiffrement dans Office 365](encryption.md)
  
[Configurer le chiffrement dans Office 365 Entreprise](set-up-encryption.md)
  
[Implémentation Schannel de TLS 1,0 dans la mise à jour de l’état de sécurité Windows : 24 novembre 2015](https://support.microsoft.com/kb/3117336)
  
[Améliorations de chiffrement TLS/SSL (centre informatique Windows)](https://technet.microsoft.com/library/cc766285%28v=ws.10%29.aspx)
  
 [Préparation de TLS 1.2 dans Office 365 et Office 365 GCC](https://docs.microsoft.com/office365/troubleshoot/security/prepare-tls-1.2-in-office-365)

