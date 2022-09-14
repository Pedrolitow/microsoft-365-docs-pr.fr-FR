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
ms.localizationpriority: medium
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
ms.openlocfilehash: 6b5df1f9e983ab2e8add09b50c2dfbd30dc1243e
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67679304"
---
# <a name="technical-reference-details-about-encryption"></a>Détails techniques de référence sur le chiffrement

Reportez-vous à cet article pour en savoir plus sur les certificats, les technologies et les suites de chiffrement TLS utilisés pour [le chiffrement dans Office 365](encryption.md). Cet article fournit également des détails sur les dépréciations planifiées.
  
- Si vous recherchez des informations de vue d’ensemble, consultez [Chiffrement dans Office 365](encryption.md).
- Si vous recherchez des informations d’installation, consultez [Configurer le chiffrement dans Office 365 Entreprise](set-up-encryption.md).
- Pour plus d’informations sur les suites de chiffrement prises en charge par des versions spécifiques de Windows, consultez [Suites de chiffrement dans TLS/SSL (Schannel SSP).](/windows/desktop/SecAuthN/cipher-suites-in-schannel)

## <a name="microsoft-office-365-certificate-ownership-and-management"></a>Gestion et propriété de certificats Microsoft Office 365

Vous n’avez pas besoin d’acheter ou de gérer des certificats pour Office 365. Au lieu de cela, Office 365 utilise ses propres certificats.
  
## <a name="current-encryption-standards-and-planned-deprecations"></a>Normes de chiffrement actuelles et dépréciations planifiées

Pour fournir un chiffrement optimal, Office 365 examine régulièrement les normes de chiffrement prises en charge. Parfois, les anciennes normes sont dépréciées à mesure qu’elles deviennent obsolètes et moins sécurisées. Cet article décrit les suites de chiffrement actuellement prises en charge et d’autres normes et détails sur les dépréciations planifiées.

## <a name="fips-compliance-for-office-365"></a>Conformité FIPS pour Office 365

Toutes les suites de chiffrement prises en charge par Office 365 utilisent des algorithmes acceptables sous FIPS 140-2. Office 365 hérite des validations FIPS de Windows (via Schannel). Pour plus d’informations sur Schannel, consultez [Suites de chiffrement dans TLS/SSL (Schannel SSP).](/windows/desktop/SecAuthN/cipher-suites-in-schannel)
  
## <a name="versions-of-tls-supported-by-office-365"></a>Versions de TLS prises en charge par Office 365

Les protocoles TLS et SSL antérieurs à TLS sont des protocoles de chiffrement qui sécurisent la communication sur un réseau à l’aide de certificats de sécurité pour chiffrer une connexion entre les ordinateurs. Office 365 prend en charge TLS version 1.2 (TLS 1.2).

TLS version 1.3 (TLS 1.3) est pris en charge par certains services.

> [!IMPORTANT]
> N’oubliez pas que les versions TLS sont déconseillées et que les versions déconseillées *ne doivent pas être utilisées* là où des versions plus récentes sont disponibles. Si vos services hérités ne nécessitent pas TLS 1.0 ou 1.1, vous devez les désactiver.
  
## <a name="support-for-tls-10-and-11-deprecation"></a>Prise en charge de la dépréciation de TLS 1.0 et 1.1

Office 365 pris en charge TLS 1.0 et 1.1 le 31 octobre 2018. Nous avons terminé la désactivation de TLS 1.0 et 1.1 dans les environnements GCC High et DoD. Nous avons commencé à désactiver TLS 1.0 et 1.1 pour les environnements du monde entier et du GCC à compter du 15 octobre 2020 et nous continuerons à le déployer au cours des prochaines semaines et mois.

Pour maintenir une connexion sécurisée aux services Office 365 et Microsoft 365, toutes les combinaisons client-serveur et navigateur-serveur utilisent TLS 1.2 et les suites de chiffrement modernes. Il se peut que vous deviez procéder à la mise à jour de certaines combinaisons client-serveur et navigateur-serveur. Pour plus d’informations sur l’impact de ce changement sur vous, consultez [Préparation à l’utilisation obligatoire de TLS 1.2 dans Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).
  
## <a name="deprecating-support-for-3des"></a>Dépréciation de la prise en charge de 3DES

Depuis le 31 octobre 2018, Office 365 ne prend plus en charge l’utilisation de suites de chiffrement 3DES pour la communication vers Office 365. Plus précisément, Office 365 ne prend plus en charge la suite de chiffrement TLS_RSA_WITH_3DES_EDE_CBC_SHA. Depuis le 28 février 2019, cette suite de chiffrement est désactivée dans Office 365. Les clients et serveurs qui communiquent avec Office 365 doivent prises en charge un ou plusieurs des chiffrements pris en charge. Pour obtenir la liste des chiffrements pris en charge, consultez les [suites de chiffrement TLS prises en charge par Office 365](#tls-cipher-suites-supported-by-office-365).
  
## <a name="deprecating-sha-1-certificate-support-in-office-365"></a>Arrêt de la prise en charge du certificat SHA-1 dans Office 365

Depuis juin 2016, Office 365 n’accepte plus de certificat SHA-1 pour les connexions sortantes ou entrantes. Utilisez SHA-2 (Secure Hash Algorithm 2) ou un algorithme de hachage plus fort dans la chaîne de certificats.
  
## <a name="tls-cipher-suites-supported-by-office-365"></a>Suites de chiffrement TLS prises en charge par Office 365

TLS utilise des *suites de chiffrement*, des collections d’algorithmes de chiffrement, pour établir des connexions sécurisées. Office 365 prend en charge les suites de chiffrement répertoriées dans le tableau suivant. Le tableau répertorie les suites de chiffrement par ordre de force, avec la suite de chiffrement la plus forte répertoriée en premier.

Office 365 répond à une demande de connexion en essayant d’abord de se connecter à l’aide de la suite de chiffrement la plus sécurisée. Si la connexion ne fonctionne pas, Office 365 tente la deuxième suite de chiffrement la plus sécurisée de la liste, et ainsi de suite. Le service continue dans la liste jusqu’à ce que la connexion soit acceptée. De même, quand Office 365 demande une connexion, le service de réception choisit si TLS sera utilisé et quelle suite de chiffrement utiliser.

| Nom de suite de chiffrement | Algorithme/force d’échange de clés | Transférer le secret | Chiffrement/force | Algorithme/force d’authentification |
|:-----|:-----|:-----|:-----|:-----|
| TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384  <br/> | ECDH/192  <br/> | Oui  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256  <br/> | ECDH/128  <br/> | Oui  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384  <br/> | ECDH/192  <br/> | Oui  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256  <br/> | ECDH/128  <br/> | Oui  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA     <br/> | ECDH/192  <br/> | Oui  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA     <br/> | ECDH/128  <br/> | Oui  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_RSA_WITH_AES_256_GCM_SHA384        <br/> | RSA/112   <br/> | Non   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_RSA_WITH_AES_128_GCM_SHA256        <br/> | RSA/112   <br/> | Non   <br/> | AES/256  <br/> | RSA/112  <br/> |

Les suites de chiffrement suivantes ont pris en charge les protocoles TLS 1.0 et 1.1 jusqu’à leur date de dépréciation. Pour les environnements GCC High et DoD dont la date de dépréciation était le 15 janvier 2020. Pour les environnements du monde entier et du GCC, cette date était le 15 octobre 2020.

| Protocoles | Nom de suite de chiffrement | Algorithme/force d’échange de clés | Transférer le secret | Chiffrement/force | Algorithme/force d’authentification | 
|:-----|:-----|:-----|:-----|:-----|:-----|
| TLS 1.0, 1.1, 1.2  <br/> | TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA  <br/> | ECDH/192  <br/> | Oui  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA  <br/> | ECDH/128  <br/> | Oui  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_256_CBC_SHA        <br/> | RSA/112   <br/> | Non   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_128_CBC_SHA        <br/> | RSA/112   <br/> | Non   <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_256_CBC_SHA256     <br/> | RSA/112   <br/> | Non   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_128_CBC_SHA256     <br/> | RSA/112   <br/> | Non   <br/> | AES/256  <br/> | RSA/112  <br/> |

Certains produits Office 365 (notamment Microsoft Teams) utilisent [Azure Front Door](/azure/frontdoor/front-door-overview) pour arrêter les connexions TLS et acheminer efficacement le trafic réseau. Au moins une des [suites de chiffrement prises en charge par Azure Front Door sur TLS 1.2](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-) doit être activée pour se connecter à ces produits. Pour Windows 10 et versions ultérieures, nous vous recommandons d’activer une ou les deux suites de chiffrement ECDHE pour une meilleure sécurité. Windows 7, 8 et 8.1 ne sont pas compatibles avec les suites de chiffrement ECDHE d’Azure Front Door et les suites de chiffrement DHE ont été fournies pour assurer la compatibilité avec ces systèmes d’exploitation.

## <a name="related-articles"></a>Articles connexes

[Suites de chiffrement TLS dans Windows 10 v1903](/windows/win32/secauthn/tls-cipher-suites-in-windows-10-v1903)

[Chiffrement dans Office 365](encryption.md)
  
[Configurer le chiffrement dans Office 365 Entreprise](set-up-encryption.md)
  
[Implémentation Schannel de TLS 1.0 dans la mise à jour de l’état de sécurité Windows : 24 novembre 2015](https://support.microsoft.com/kb/3117336)
  
[Améliorations du chiffrement TLS/SSL (Windows IT Center)](/previous-versions/windows/it-pro/windows-vista/cc766285(v=ws.10))
  
[Préparation de TLS 1.2 dans Office 365 et Office 365 Cloud de la communauté du secteur public](/office365/troubleshoot/security/prepare-tls-1.2-in-office-365)

[Quelles sont les suites de chiffrement actuelles prises en charge par Azure Front Door ?](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-)
