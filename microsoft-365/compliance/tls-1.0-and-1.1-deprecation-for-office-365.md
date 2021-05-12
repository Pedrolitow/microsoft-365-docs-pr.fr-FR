---
title: Désactivation de TLS 1.0 et 1.1 pour Microsoft 365
description: Décrit l’annulation et la désactivation de TLS 1.0 et 1.1 pour Microsoft 365.
author: workshay
manager: laurawi
localization_priority: Normal
search.appverid:
- MET150
audience: ITPro
ms.service: O365-seccomp
ms.topic: article
ms.author: fasqiu
ms.reviewer: krowley
appliesto:
- Microsoft 365 Apps for enterprise
- Office 365 Business
- Office 365 Personal
- Office Online Server
- Office Web Apps
ms.openlocfilehash: 870572a61c241d3d3c8ce6791cee77edba2a1956
ms.sourcegitcommit: 967f64dfa1a05f31179c8316b96bfb7758a5d990
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52332677"
---
# <a name="disabling-tls-10-and-11-for-microsoft-365"></a>Désactivation de TLS 1.0 et 1.1 pour Microsoft 365

> [!IMPORTANT]
> Nous avons temporairement interrompu la désactivation de TLS 1.0 et 1.1 pour les clients commerciaux en raison du COVID-19. À mesure que les chaînes d’approvisionnement ont été ajustées et que certains pays s’ouvrent, nous avons redémarré le déploiement de l’application de TLS 1.2 le 15 octobre 2020. Le déploiement se poursuit au cours des semaines et des mois suivants.

Depuis le 31 octobre 2018, les protocoles TLS 1.0 et 1.1 sont supprimés pour le service Microsoft 365. L’effet est minime pour les utilisateurs finaux. Cette modification a été annoncée pendant plus de deux ans, avec la première annonce publique en décembre 2017. Cet article est destiné uniquement à couvrir le client local Office 365 par rapport au service Office 365, mais peut également s’appliquer aux problèmes TLS locaux avec Office et Office Online Server/Office Web Apps.

Pour SharePoint et OneDrive, vous devez mettre à jour et configurer .NET pour prendre en charge TLS 1.2. Pour plus d’informations, [voir Comment activer TLS 1.2 sur les clients](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="office-365-and-tls-overview"></a>Vue d’ensemble d’Office 365 et de TLS

Le client Office s’appuie sur le service web Windows (WINHTTP) pour envoyer et recevoir du trafic sur les protocoles TLS. Le client Office peut utiliser TLS 1.2 si le service web de l’ordinateur local peut utiliser TLS 1.2. Tous les clients Office peuvent utiliser des protocoles TLS, car les protocoles TLS et SSL font partie du système d’exploitation et ne sont pas spécifiques au client Office.

### <a name="on-windows-8-and-later-versions"></a>Sur Windows 8 et versions ultérieures

Par défaut, les protocoles TLS 1.2 et 1.1 sont disponibles si aucun périphérique réseau n’est configuré pour rejeter le trafic TLS 1.2.

### <a name="on-windows-7"></a>Sur Windows 7

Les protocoles TLS 1.1 et 1.2 ne sont pas disponibles sans la mise à jour de la [KB 3140245.](https://support.microsoft.com/help/3140245) La mise à jour résout ce problème et ajoute la sous-clé de Registre suivante :

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
> N’utilisez pas les protocoles SSL 2.0 et 3.0, qui peuvent également être définies à l’aide de la clé **DefaultSecureProtocols.** SSL 2.0 et 3.0 sont considérés comme des protocoles obsolètes et non sécurisés. La meilleure pratique consiste à mettre fin à l’utilisation de SSL 2.0 et SSL 3.0, bien que la décision finale dépende de ce qui répond le mieux aux besoins de votre produit. Pour plus d’informations sur les vulnérabilités SSL 3.0, reportez-vous à la [KB 3009008](https://support.microsoft.com/help/3009008).

Vous pouvez utiliser la calculatrice Windows par défaut en mode programmeur pour configurer les mêmes valeurs de clé de Registre de référence. Pour plus d’informations, voir la mise à jour de la [KB 3140245 pour activer TLS 1.1 et TLS 1.2](https://support.microsoft.com/help/3140245)en tant que protocoles sécurisés par défaut dans WinHTTP dans Windows.

Que la mise à jour Windows 7 ([KB 3140245](https://support.microsoft.com/help/3140245)) soit installée ou non, la sous-clé de Registre DefaultSecureProtocols n’est pas présente et doit être ajoutée manuellement ou via un objet de stratégie de groupe (GPO). Autrement dit, sauf si vous devez personnaliser les protocoles sécurisés activés ou restreints, cette clé n’est pas requise. Vous avez uniquement besoin de la mise à jour de Windows 7 SP1 ([KB 3140245).](https://support.microsoft.com/help/3140245)

## <a name="update-and-configure-the-net-framework-to-support-tls-12"></a>Mettre à jour et configurer le .NET Framework pour prendre en charge TLS 1.2

Vous devez mettre à jour les applications qui appellent les API Microsoft 365 sur TLS 1.0 ou TLS 1.1 pour utiliser TLS 1.2. Par défaut, .NET 4.5 est TLS 1.1. Pour mettre à jour votre configuration .NET, voir [Comment activer TLS (Transport Layer Security) 1.2 sur les clients.](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client)

## <a name="more-information"></a>Plus d’informations

Pour plus d’informations, voir Préparation de l’utilisation obligatoire de [TLS 1.2 dans Office 365.](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365)

## <a name="references"></a>Références

Les ressources suivantes fournissent des conseils pour vous assurer que vos clients utilisent TLS 1.2 ou une version ultérieure et pour désactiver TLS 1.0 et 1.1 :

- Pour les clients Windows 7 qui se connectent à Office 365, assurez-vous que TLS 1.2 est le protocole sécurisé défini par défaut dans WinHTTP sous Windows. Pour plus d’informations, voir la KB 3140245 - Mise à jour pour activer [TLS 1.1 et TLS 1.2](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in)en tant que protocoles sécurisés par défaut dans WinHTTP dans Windows.
- Pour résoudre les problèmes d’utilisation faible de TLS en supprimant les dépendances TLS 1.0 et 1.1, consultez la prise en charge de [TLS 1.2](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/)chez Microsoft.
- [La nouvelle fonctionnalité IIS](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) facilite la recherche de clients sur [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) et [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334) qui se connectent au service en utilisant des protocoles de sécurité faibles.
- Obtenez plus d’informations sur la résolution du problème [TLS 1.0.](https://www.microsoft.com/download/details.aspx?id=55266)
- Pour plus d’informations sur notre approche de la sécurité, accédez au [Centre de gestion de la confidentialité d'Office 365](https://www.microsoft.com/trustcenter/cloudservices/office365).
- [Preparing for TLS 1.0/1.1 Deprecation - Office 365 Skype for Business](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247) (en anglais uniquement)
- [Exchange Server TLS guidance, part 1: Getting Ready for TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649) (en anglais uniquement)
- [Directives concernant le protocole TLS dans Exchange Server, Partie 2 : Enabling TLS 1.2 and Identifying Clients Not Using It](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761) (en anglais uniquement)
- [Directives concernant le protocole TLS dans Exchange Server, Partie 3 : Désactivation de TLS 1.0/1.1](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [Activation de la prise en charge de TLS 1.1 et TLS 1.2 dans Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)

