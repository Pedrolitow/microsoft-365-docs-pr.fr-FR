---
title: Dépréciation TLS 1.0 et 1.1 pour Office 365
description: Décrit les protocoles TLS 1,0 et 1,1 obsolètes pour Office 365.
author: workshay
manager: laurawi
localization_priority: Normal
search.appverid:
- MET150
audience: ITPro
ms.service: O365-seccomp
ms.topic: article
ms.author: shmehta
ms.reviewer: krowley
appliesto:
- Microsoft 365 Apps for enterprise
- Office 365 Business
- Office 365 Personal
- Office Online Server
- Office Web Apps
ms.openlocfilehash: 622d783011defcf9c84061087b7d05f2a117172e
ms.sourcegitcommit: 3bf4f1c0d3a8515cca651b2a520217195f89457f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "49777055"
---
# <a name="tls-10-and-11-deprecation-for-office-365"></a>Dépréciation TLS 1.0 et 1.1 pour Office 365
> [!IMPORTANT]
> Nous avons interrompu temporairement l’application de la désapprobation de TLS 1,0 et 1,1 pour les clients commerciaux en raison du COVID-19, mais, étant donné que les chaînes d’approvisionnement ont été modifiées et que certains pays sont ouverts, nous redéfinissons l’application TLS pour qu’elle commence le 15 octobre, 2020, et le lancement se poursuivra au cours des semaines et mois suivants. 

À partir du 31 octobre 2018, les protocoles TLS (Transport Layer Security) 1,0 et 1,1 sont déconseillés pour le service Office 365. L’effet pour les utilisateurs finaux est supposé minimal. Cette modification a été publique depuis plus de deux ans, avec la première annonce publique effectuée en décembre 2017. Cet article est destiné uniquement à traiter le client local Office 365 en relation avec le service Office 365, mais peut également s’appliquer aux problèmes TLS sur site avec Office et Office Online Server/Office Web Apps.

## <a name="office-and-tls-overview"></a>Vue d’ensemble d’Office et de TLS

Le client Office s’appuie sur le service Web Windows (WINHTTP) pour envoyer et recevoir le trafic sur les protocoles TLS. Le client Office peut utiliser TLS 1,2 si le service Web de l’ordinateur local peut utiliser TLS 1,2. Tous les clients Office peuvent utiliser les protocoles TLS, car les protocoles TLS et SSL font partie du système d’exploitation et ne sont pas spécifiques du client Office.

### <a name="on-windows-8-and-later-versions"></a>Sur Windows 8 et versions ultérieures

Par défaut, les protocoles TLS 1,2 et 1,1 sont disponibles si aucun périphérique réseau n’est configuré pour rejeter le trafic TLS 1,2.

### <a name="on-windows-7"></a>Sur Windows 7

Les protocoles TLS 1,1 et 1,2 ne sont pas disponibles sans la mise à jour [KB 3140245](https://support.microsoft.com/help/3140245) . La mise à jour corrige ce problème et ajoute la sous-clé de Registre suivante :

```console
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp
```

> [!NOTE]
> Les utilisateurs de Windows 7 qui n’ont pas cette mise à jour sont affectés le 31 octobre 2018. [KB 3140245](https://support.microsoft.com/help/3140245) explique comment modifier les paramètres WinHTTP pour activer les protocoles TLS.

#### <a name="more-information"></a>Informations supplémentaires

La valeur de la clé de Registre **DefaultSecureProtocols** décrite dans l’article de la base de connaissances détermine les protocoles réseau qui peuvent être utilisés :

|Valeur DefaultSecureProtocols|Protocole activé|
|-|-|
|0x00000008|Activer SSL 2.0 par défaut|
|0x00000020|Activer SSL 3.0 par défaut|
|0x00000080|Activer TLS 1.0 par défaut|
|0x00000200|Activer TLS 1.1 par défaut|
|0x00000800|Activer TLS 1.2 par défaut|

## <a name="office-clients-and-tls-registry-keys"></a>Clients Office et clés de Registre TLS

Vous pouvez vous reporter à [la 4057306 de la préparation à l’utilisation obligatoire de TLS 1,2 dans Office 365](https://support.microsoft.com/help/4057306). Il s’agit d’un article général pour les administrateurs informatiques, et de la documentation officielle sur la modification TLS 1,2.

Le tableau suivant indique les valeurs de clés de Registre appropriées dans les clients Office 365 après le 31 octobre 2018.

|Protocoles activés pour le service Office 365 après le 31 octobre 2018|Valeur hexadécimale|
|-|-|
|TLS 1,0 + 1,1 + 1,2|0x00000A80|
|TLS 1,1 + 1,2|0x00000A00|
|TLS 1,0 + 1,2|0x00000880|
|TLS 1.2|0x00000800|

> [!IMPORTANT]
> Il n’est pas recommandé d’utiliser les protocoles SSL 2,0 et 3,0, qui peuvent également être définis à l’aide de la clé **DefaultSecureProtocols** . Les protocoles SSL 2,0 et 3,0 sont considérés comme des protocoles déconseillés. La meilleure pratique consiste à mettre fin à l’utilisation des protocoles SSL 2,0 et SSL 3,0, bien que la décision de le faire dépende de ce qui est le mieux adapté à vos besoins. Pour plus d’informations sur les vulnérabilités SSL 3,0, reportez-vous à [KB 3009008](https://support.microsoft.com/help/3009008).

Vous pouvez utiliser la calculatrice Windows par défaut en mode programmeur pour configurer les mêmes valeurs de clés de registre de référence. Pour plus d’informations, reportez-vous à [la mise à jour KB 3140245 pour activer tls 1,1 et tls 1,2 comme protocoles de sécurité par défaut dans WinHTTP dans Windows](https://support.microsoft.com/help/3140245).

Quelle que soit la mise à jour de Windows 7 ([KB 3140245](https://support.microsoft.com/help/3140245)) installée ou non, la sous-clé de Registre DefaultSecureProtocols n’est pas présente et doit être ajoutée manuellement ou par le biais d’un objet de stratégie de groupe (GPO). Autrement dit, sauf si vous devez personnaliser les protocoles sécurisés qui sont activés ou restreints, cette clé n’est pas requise. Vous n’avez besoin que de la mise à jour de Windows 7 SP1 ([KB 3140245](https://support.microsoft.com/help/3140245)).
