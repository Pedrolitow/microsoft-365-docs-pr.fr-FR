---
title: Forum aux questions sur la découverte d’appareils
description: Trouver des réponses aux questions fréquentes (FAQ) sur la découverte d’appareils
keywords: détection d’appareil, détection, passif, proactif, réseau, visibilité, serveur, station de travail, appareils intégrés, appareils non gérés
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 6a238f3c6c4161326e02681a5336699fee6da586
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68167206"
---
# <a name="device-discovery-frequently-asked-questions"></a>Forum aux questions sur la découverte d’appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- - [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

Trouvez des réponses aux questions fréquentes (FAQ) sur la découverte d’appareils.

## <a name="what-is-basic-discovery-mode"></a>Qu’est-ce que le mode de découverte de base ?

Ce mode permet à chaque Microsoft Defender pour point de terminaison appareil intégré de collecter des données réseau et de découvrir les appareils voisins. Les points de terminaison intégrés collectent passivement les événements dans le réseau et en extraient les informations de l’appareil. Aucun trafic réseau n’est lancé. Les points de terminaison intégrés extraient simplement les données de chaque trafic réseau qui est vu par un appareil intégré. Ces données sont utilisées pour répertorier les appareils non gérés dans votre réseau.

## <a name="can-i-disable-basic-discovery"></a>Puis-je désactiver la découverte de base ?

Vous avez la possibilité de désactiver la découverte d’appareils via la page [Fonctionnalités avancées](advanced-features.md) . Toutefois, vous perdrez de la visibilité sur les appareils non gérés de votre réseau. Notez que SenseNDR.exe sera toujours en cours d’exécution sur les appareils intégrés, quelle que soit la découverte désactivée. 

## <a name="what-is-standard-discovery-mode"></a>Qu’est-ce que le mode de découverte Standard ?

Dans ce mode, les points de terminaison intégrés à Microsoft Defender pour point de terminaison peuvent activement sonder les appareils observés dans le réseau pour enrichir les données collectées (avec une quantité négligeable de trafic réseau). Seuls les appareils qui ont été observés par le mode de découverte de base seront activement sondés en mode standard. Ce mode est fortement recommandé pour la création d’un inventaire fiable et cohérent des appareils. Si vous choisissez de désactiver ce mode et de sélectionner le mode de découverte de base, vous ne bénéficiez probablement que d’une visibilité limitée des points de terminaison non managés dans votre réseau.

 Le mode Standard tire également parti des protocoles de découverte courants qui utilisent des requêtes de multidiffusion dans le réseau pour rechercher encore plus d’appareils, en plus de celles observées à l’aide de la méthode passive.

## <a name="can-i-control-which-devices-perform-standard-discovery"></a>Puis-je contrôler les appareils qui effectuent la découverte standard ?

Vous pouvez personnaliser la liste des appareils utilisés pour effectuer la découverte standard. Vous pouvez activer la découverte standard sur tous les appareils intégrés qui prennent également en charge cette fonctionnalité (actuellement Windows 10 ou version ultérieure et les appareils Windows Server 2019 ou ultérieurs uniquement) ou sélectionner un sous-ensemble ou un sous-ensemble de vos appareils en spécifiant leurs balises d’appareil. Dans ce cas, tous les autres appareils sont configurés pour exécuter la découverte de base uniquement. La configuration est disponible dans la page des paramètres de découverte des appareils.

## <a name="can-i-exclude-unmanaged-devices-from-the-device-inventory-list"></a>Puis-je exclure des appareils non gérés de la liste d’inventaire des appareils ?

Oui, vous pouvez appliquer des filtres pour exclure les appareils non gérés de la liste d’inventaire des appareils. Vous pouvez également utiliser la colonne d’état d’intégration sur les requêtes d’API pour filtrer les appareils non gérés.

## <a name="which-onboarded-devices-can-perform-discovery"></a>Quels appareils intégrés peuvent effectuer la découverte ?

Les appareils intégrés exécutés sur Windows 10 version 1809 ou ultérieure, Windows 11, Windows Server 2019 ou Windows Server 2022 peuvent effectuer la découverte.

## <a name="what-happens-if-my-onboarded-devices-is-connected-to-my-home-network-or-to-public-access-point"></a>Que se passe-t-il si mes appareils intégrés sont connectés à mon réseau domestique ou à un point d’accès public ?

Le moteur de découverte fait la distinction entre les événements réseau reçus dans le réseau d’entreprise et en dehors du réseau d’entreprise. En mettant en corrélation les identificateurs réseau entre tous les clients du locataire, les événements sont différenciés entre ceux qui ont été reçus de réseaux privés et de réseaux d’entreprise. Par exemple, si la majorité des appareils de l’organisation indiquent qu’ils sont connectés au même nom de réseau, avec la même passerelle par défaut et la même adresse de serveur DHCP, il peut être supposé que ce réseau est probablement un réseau d’entreprise. Les appareils de réseau privé ne seront pas répertoriés dans l’inventaire et ne seront pas activement analysés.

## <a name="what-protocols-are-you-capturing-and-analyzing"></a>Quels protocoles capturez-vous et analysez-vous ?

Par défaut, tous les appareils intégrés s’exécutant sur Windows 10 version 1809 ou ultérieure, Windows 11, Windows Server 2019 ou Windows Server 2022 capturent et analysent les protocoles suivants : ARP, CDP, DHCP, DHCPv6, IP (en-têtes), LLDP, LLMNR, mDNS, MNDP, NBNS, SSDP, TCP (en-têtes SYN), UDP (en-têtes), WSD

## <a name="which-protocols-do-you-use-for-active-probing-in-standard-discovery"></a>Quels protocoles utilisez-vous pour la détection active dans la découverte Standard ?
Lorsqu’un appareil est configuré pour exécuter la découverte standard, les services exposés sont analysés à l’aide des protocoles suivants : ARP, FTP, HTTP, HTTPS, ICMP, LLMNR, NBNS, RDP, SIP, SMTP, SNMP, SSH, Telnet, UPNP, WSD, SMB, NBSS, IPP, PJL, RPC, mDNS, DHCP, AFP, CrestonCIP, IphoneSync, WinRM, VNC, SLP, LDAP


## <a name="how-can-i-exclude-targets-from-being-probed-with-standard-discovery"></a>Comment puis-je exclure des cibles d’être sondés avec la découverte Standard ?

S’il existe des appareils sur votre réseau qui ne doivent pas être analysés activement, vous pouvez également définir une liste d’exclusions pour les empêcher d’être analysés. La configuration est disponible dans la page des paramètres de découverte des appareils.

> [!NOTE]
> Les appareils peuvent toujours répondre aux tentatives de découverte de multidiffusion dans le réseau. Ces appareils seront découverts, mais ne seront pas analysés activement. 

## <a name="can-i-exclude-devices-from-being-discovered"></a>Puis-je exclure les appareils de la découverte ?

Comme la découverte d’appareils utilise des méthodes passives pour découvrir les appareils dans le réseau, tout appareil qui communique avec vos appareils intégrés dans le réseau d’entreprise peut être découvert et répertorié dans l’inventaire. Vous pouvez exclure les appareils de la détection active uniquement.

## <a name="how-frequent-is-the-active-probing"></a>Quelle est la fréquence de la détection active ?

Les appareils sont activement interrogés lorsque des modifications des caractéristiques de l’appareil sont observées pour s’assurer que les informations existantes sont à jour (généralement, les appareils n’ont pas été sondés plus d’une fois sur une période de trois semaines)

## <a name="my-security-tool-raised-alert-on-unicastscannerps1--psscript_guidps1-or-port-scanning-activity-initiated-by-it-what-should-i-do"></a>Mon outil de sécurité a déclenché une alerte sur UnicastScanner.ps1/PSScript_{GUID}.ps1 ou l’activité d’analyse de port lancée par celui-ci, que dois-je faire ?

Les scripts de détection actifs sont signés par Microsoft et sont sécurisés. Vous pouvez ajouter le chemin suivant à votre liste d’exclusions : `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps1`

## <a name="what-is-the-amount-of-traffic-being-generated-by-the-standard-discovery-active-probe"></a>Quelle est la quantité de trafic générée par la sonde active de découverte Standard ?

La détection active peut générer jusqu’à 50 Ko de trafic entre l’appareil intégré et l’appareil sondé, chaque tentative de détection

## <a name="why-is-there-a-discrepancy-between-can-be-onboarded-devices-in-the-device-inventory-and-the-number-of-devices-to-onboard-in-the-dashboard-tile"></a>Pourquoi existe-t-il une différence entre les appareils « peuvent être intégrés » dans l’inventaire des appareils et le nombre d'« appareils à intégrer » dans la vignette du tableau de bord ?

Vous remarquerez peut-être des différences entre le nombre d’appareils répertoriés sous « peut être intégré » dans l’inventaire des appareils, la recommandation de sécurité « intégrer à Microsoft Defender pour point de terminaison » et le widget de tableau de bord « Appareils à intégrer ».

 La recommandation de sécurité et le widget de tableau de bord s’adressent aux appareils qui sont stables dans le réseau ; à l’exclusion des appareils éphémères, des appareils invités et autres. L’idée est de recommander sur les appareils persistants, ce qui implique également le score de sécurité global de l’organisation.

## <a name="can-i-onboard-unmanaged-devices-that-were-found"></a>Puis-je intégrer des appareils non managés qui ont été trouvés ?

Oui. Vous pouvez intégrer manuellement des appareils non gérés. Les points de terminaison non managés de votre réseau introduisent des vulnérabilités et des risques pour votre réseau. Leur intégration au service peut augmenter la visibilité de la sécurité sur ces derniers.

## <a name="ive-noticed-that-unmanaged-device-health-state-is-always-active-why-is-that"></a>J’ai remarqué que l’état d’intégrité de l’appareil non managé est toujours « Actif », pourquoi est-ce ?

Temporairement, l’état d’intégrité des appareils non managés sera « Actif » pendant la période de rétention standard de l’inventaire des appareils, quel que soit leur état réel.

## <a name="does-standard-discovery-look-like-malicious-network-activity"></a>La découverte standard ressemble-t-elle à une activité réseau malveillante ?

Lorsque vous envisagez la découverte standard, vous vous demandez peut-être les implications de la détection et, plus précisément, si les outils de sécurité peuvent soupçonner une telle activité comme malveillante. La sous-section suivante explique pourquoi, dans presque tous les cas, les organisations ne doivent pas se soucier de l’activation de la découverte standard.  

### <a name="probing-is-distributed-across-all-windows-devices-on-the-network"></a>La détection est distribuée sur tous les appareils Windows sur le réseau

Contrairement aux activités malveillantes, qui analysent généralement l’ensemble du réseau à partir d’un petit nombre d’appareils compromis, Microsoft Defender pour point de terminaison’analyse de découverte standard est lancée à partir de tous les appareils Windows intégrés, ce qui rend l’activité bénigne et non anormale. La détection est gérée de manière centralisée à partir du cloud pour équilibrer la tentative de détection entre tous les appareils intégrés pris en charge dans le réseau.  

### <a name="active-probing-generates-negligible-amount-of-extra-traffic"></a>La détection active génère une quantité négligeable de trafic supplémentaire

En règle générale, les appareils non managés sont analysés au plus une fois sur une période de trois semaines et génèrent moins de 50 Ko de trafic. L’activité malveillante inclut généralement des tentatives de détection répétitives élevées et, dans certains cas, l’exfiltration de données qui génère une quantité importante de trafic réseau qui peut être identifiée comme anomalie par les outils de surveillance réseau.

### <a name="your-windows-device-already-runs-active-discovery"></a>Votre appareil Windows exécute déjà une découverte active

Les fonctionnalités de découverte active ont toujours été incorporées dans le système d’exploitation Windows, pour rechercher des appareils, des points de terminaison et des imprimantes à proximité, pour faciliter les expériences de « plug-and-play » et le partage de fichiers entre les points de terminaison du réseau. Des fonctionnalités similaires sont implémentées dans les appareils mobiles, l’équipement réseau et les applications d’inventaire pour n’en nommer que quelques-unes.  

La découverte standard utilise les mêmes méthodes de découverte pour identifier les appareils et pour avoir une visibilité unifiée pour tous les appareils de votre réseau dans l’inventaire des appareils Microsoft 365 Defender. Par exemple , la découverte standard identifie les points de terminaison à proximité dans le réseau de la même façon que Windows répertorie les imprimantes disponibles dans le réseau. 

Les outils de sécurité et de surveillance du réseau sont indifférents à ces activités effectuées par les appareils sur le réseau. 

### <a name="only-unmanaged-devices-are-being-probed"></a>Seuls les appareils non managés sont analysés

Les fonctionnalités de découverte des appareils ont été créées pour détecter et identifier uniquement les appareils non gérés sur votre réseau. Cela signifie que les appareils précédemment découverts qui sont déjà intégrés à Microsoft Defender pour point de terminaison ne seront pas sondés.

### <a name="you-can-exclude-network-lures-from-active-probing"></a>Vous pouvez exclure les leurres réseau de la détection active

La découverte standard prend en charge l’exclusion des appareils ou des plages (sous-réseaux) de la détection active. Si des leurres réseau sont déployés, vous pouvez utiliser les paramètres de découverte d’appareils pour définir des exclusions basées sur des adresses IP ou des sous-réseaux (une plage d’adresses IP). La définition de ces exclusions garantit que ces appareils ne seront pas sondés activement et qu’ils ne seront pas alertés. Ces appareils seront découverts à l’aide de méthodes passives uniquement (similaires au mode de découverte de base).
