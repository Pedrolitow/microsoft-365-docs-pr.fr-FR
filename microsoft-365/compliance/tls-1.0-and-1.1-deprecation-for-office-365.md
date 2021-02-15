---
title: Dépréciation TLS 1.0 et 1.1 pour Office 365
description: Décrit l’annulation de TLS 1.0 et 1.1 pour Office 365.
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
> Nous avons temporairement interrompu l’application de TLS 1.0 et 1.1 pour les clients commerciaux en raison du COVID-19, mais à mesure que les chaînes d’approvisionnement se sont ajustées et que certains pays s’ouvrent, nous réinitialiserons l’application du TLS pour commencer le 15 octobre 2020 et le déploiement se poursuit au cours des semaines et des mois suivants. 

Depuis le 31 octobre 2018, les protocoles TLS 1.0 et 1.1 sont supprimés pour le service Office 365. L’effet pour les utilisateurs finaux est censé être minime. Cette modification a été annoncée pendant plus de deux ans, avec la première annonce publique en décembre 2017. Cet article est destiné uniquement à couvrir le client local Office 365 par rapport au service Office 365, mais peut également s’appliquer aux problèmes TLS locaux avec Office et Office Online Server/Office Web Apps.

## <a name="office-and-tls-overview"></a>Vue d’ensemble d’Office et de TLS

Le client Office s’appuie sur le service web Windows (WINHTTP) pour envoyer et recevoir du trafic sur les protocoles TLS. Le client Office peut utiliser TLS 1.2 si le service web de l’ordinateur local peut utiliser TLS 1.2. Tous les clients Office peuvent utiliser des protocoles TLS, car les protocoles TLS et SSL font partie du système d’exploitation et ne sont pas spécifiques au client Office.

### <a name="on-windows-8-and-later-versions"></a>Sur Windows 8 et versions ultérieures

Par défaut, les protocoles TLS 1.2 et 1.1 sont disponibles si aucun périphérique réseau n’est configuré pour rejeter le trafic TLS 1.2.

### <a name="on-windows-7"></a>Sur Windows 7

Les protocoles TLS 1.1 et 1.2 ne sont pas disponibles sans la mise à jour [KB 3140245.](https://support.microsoft.com/help/3140245) La mise à jour résout ce problème et ajoute la sous-clé de Registre suivante :

```console
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp
```

> [!NOTE]
> Les utilisateurs de Windows 7 qui n’ont pas cette mise à jour sont affectés depuis le 31 octobre 2018. [La KB 3140245](https://support.microsoft.com/help/3140245) présente des détails sur la modification des paramètres WINHTTP pour activer les protocoles TLS.

#### <a name="more-information"></a>Plus d’informations

La valeur de la clé de Registre **DefaultSecureProtocols** que l’article de la base de données décrit détermine les protocoles réseau qui peuvent être utilisés :

|Valeur DefaultSecureProtocols|Protocole activé|
|-|-|
|0x00000008|Activer SSL 2.0 par défaut|
|0x00000020|Activer SSL 3.0 par défaut|
|0x00000080|Activer TLS 1.0 par défaut|
|0x00000200|Activer TLS 1.1 par défaut|
|0x00000800|Activer TLS 1.2 par défaut|

## <a name="office-clients-and-tls-registry-keys"></a>Clients Office et clés de Registre TLS

Vous pouvez consulter la KB 4057306 Préparation de l’utilisation obligatoire de [TLS 1.2 dans Office 365](https://support.microsoft.com/help/4057306). Il s’agit d’un article général pour les administrateurs informatiques et d’une documentation officielle sur la modification de TLS 1.2.

Le tableau suivant indique les valeurs de clé de Registre appropriées dans les clients Office 365 après le 31 octobre 2018.

|Protocoles activés pour le service Office 365 après le 31 octobre 2018|Valeur hexadécimale|
|-|-|
|TLS 1.0 + 1.1 + 1.2|0x00000A80|
|TLS 1.1 + 1.2|0x00000A00|
|TLS 1.0 + 1.2|0x00000880|
|TLS 1.2|0x00000800|

> [!IMPORTANT]
> Nous vous déconseillons d’utiliser les protocoles SSL 2.0 et 3.0, qui peuvent également être définies à l’aide de la clé **DefaultSecureProtocols.** SSL 2.0 et 3.0 sont considérés comme des protocoles dépréciés. La meilleure pratique consiste à mettre fin à l’utilisation de SSL 2.0 et SSL 3.0, bien que la décision finale dépende de ce qui répond le mieux aux besoins de votre produit. Pour plus d’informations sur les vulnérabilités SSL 3.0, reportez-vous à la [KB 3009008](https://support.microsoft.com/help/3009008).

Vous pouvez utiliser la calculatrice Windows par défaut en mode programmeur pour configurer les mêmes valeurs de clé de Registre de référence. Pour plus d’informations, voir la mise à jour de la [KB 3140245 pour activer TLS 1.1 et TLS 1.2](https://support.microsoft.com/help/3140245)en tant que protocoles sécurisés par défaut dans WinHTTP dans Windows.

Que la mise à jour Windows 7 ([KB 3140245](https://support.microsoft.com/help/3140245)) soit installée ou non, la sous-clé de Registre DefaultSecureProtocols n’est pas présente et doit être ajoutée manuellement ou via un objet de stratégie de groupe (GPO). Autrement dit, sauf si vous devez personnaliser les protocoles sécurisés activés ou restreints, cette clé n’est pas requise. Vous avez uniquement besoin de la mise à jour de Windows 7 SP1 ([KB 3140245).](https://support.microsoft.com/help/3140245)
