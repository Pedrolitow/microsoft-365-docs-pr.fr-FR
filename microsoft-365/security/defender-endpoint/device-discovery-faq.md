---
title: Questions fréquemment posées sur la découverte d’appareils
description: Trouvez des réponses aux questions fréquemment posées sur la découverte d’appareils
keywords: détection d’appareils, découverte, passif, proactif, réseau, visibilité, serveur, station de travail, intégration, appareils nonmanagés
ms.prod: m365-security
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
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: df0488f8ae9aad5ab00b39f85d638fae2dc0eabc
ms.sourcegitcommit: e09ced3e3628bf2ccb84d205d9699483cbb4b3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2021
ms.locfileid: "60882704"
---
# <a name="device-discovery-frequently-asked-questions"></a>Questions fréquemment posées sur la découverte d’appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

Trouvez des réponses aux questions fréquemment posées sur la découverte d’appareils.

## <a name="what-is-basic-discovery-mode"></a>Qu’est-ce que le mode de découverte de base ?
Ce mode permet à chaque appareil intégré à Microsoft Defender for Endpoint de collecter des données réseau et de découvrir les appareils voisins. Les points de terminaison intégrés collectent passivement des événements dans le réseau et extraient les informations de l’appareil. Aucun trafic réseau n’est initié. Les points de terminaison intégrés extraient simplement les données de chaque trafic réseau visible par un appareil intégré. Ces données sont utilisées pour lister les appareils non utilisés dans votre réseau.


## <a name="can-i-disable-basic-discovery"></a>Puis-je désactiver la découverte de base ?
Vous avez la possibilité de désactiver la découverte d’appareils via la page [Fonctionnalités avancées.](advanced-features.md) Toutefois, vous perdrez la visibilité sur les appareils non utilisés dans votre réseau. Notez que SenseNDR.exe seront toujours en cours d’exécution sur les appareils intégrés, même si la découverte est désactivée. 

## <a name="what-is-standard-discovery-mode"></a>Qu’est-ce que le mode de découverte standard ?
 Dans ce mode, les points de terminaison intégrés à Microsoft Defender pour point de terminaison peuvent sonder activement les appareils observés dans le réseau pour enrichir les données collectées (avec une quantité négligeable de trafic réseau). Seuls les appareils observés par le mode de découverte de base sont activement sondés en mode standard. Ce mode est vivement recommandé pour créer un inventaire fiable et cohérent des appareils. Si vous choisissez de désactiver ce mode et de sélectionner le mode de découverte de base, vous n’aurez probablement qu’une visibilité limitée des points de terminaison nonmanagés dans votre réseau.

 Le mode standard exploite également les protocoles de découverte courants qui utilisent des requêtes multidiffusion dans le réseau pour trouver encore plus d’appareils, en plus de ceux qui ont été ovédés à l’aide de la méthode passive.

## <a name="can-i-control-which-devices-perform-standard-discovery"></a>Puis-je contrôler quels appareils effectuent la découverte standard ?
 Vous pouvez personnaliser la liste des appareils utilisés pour effectuer la découverte standard. Vous pouvez activer la découverte standard sur tous les appareils intégrés qui également prendre en charge cette fonctionnalité (appareils actuellement Windows 10 uniquement) ou sélectionner un sous-ensemble ou des sous-ensembles de vos appareils en spécifiant leurs balises d’appareil. Dans ce cas, tous les autres appareils sont configurés pour exécuter la découverte de base uniquement. La configuration est disponible dans la page des paramètres de découverte d’appareils.

## <a name="can-i-exclude-unmanaged-devices-from-the-device-inventory-list"></a>Puis-je exclure des appareils non utilisés de la liste d’inventaire des appareils ?
Oui, vous pouvez appliquer des filtres pour exclure les appareils nonmanagés de la liste d’inventaire des appareils. Vous pouvez également utiliser la colonne d’état d’intégration sur les requêtes API pour filtrer les appareils nonmanagés. 


## <a name="which-onboarded-devices-can-perform-discovery"></a>Quels appareils intégrés peuvent effectuer la découverte ?
 Les appareils intégrés s’exécutant Windows 10 version 1809 ou ultérieure, ou Windows 11 peuvent effectuer la découverte. Les serveurs ne peuvent pas effectuer de découverte à ce stade.

## <a name="what-happens-if-my-onboarded-devices-is-connected-to-my-home-network-or-to-public-access-point"></a>Que se passe-t-il si mes appareils intégrés sont connectés à mon réseau à domicile ou au point d’accès public ?
 Le moteur de découverte fait la distinction entre les événements réseau reçus dans le réseau d’entreprise et en dehors du réseau d’entreprise. En corrélant les identificateurs réseau sur tous les clients du client, les événements sont différenciés entre ceux reçus à partir de réseaux privés et de réseaux d’entreprise. Par exemple, si la majorité des appareils de l’organisation signalent qu’ils sont connectés au même nom de réseau, avec la même passerelle par défaut et la même adresse de serveur DHCP, il est possible de supposer que ce réseau est probablement un réseau d’entreprise. Les périphériques de réseau privé ne sont pas répertoriés dans l’inventaire et ne sont pas activement sondés.

## <a name="what-protocols-are-you-capturing-and-analyzing"></a>Quels protocoles capturez-vous et analysez-vous ?
 Par défaut, tous les appareils intégrés s’exécutant sur Windows 10 version 1809 ou ultérieure, ou Windows 11 capturent et analysent les protocoles suivants : ARP, CDP, DHCP, DHCPv6, IP (en-têtes), LLDP, LLMNR, mDNS, MNDP, NBNS, SSDP, TCP (en-têtes SYN), UDP (en-têtes), WSD

## <a name="which-protocols-do-you-use-for-active-probing-in-standard-discovery"></a>Quels protocoles utilisez-vous pour l’analyse active dans la découverte standard ?
 Lorsqu’un appareil est configuré pour exécuter la découverte standard, les services exposés sont sondés à l’aide des protocoles suivants : ARP, FTP, HTTP, HTTPS, ICMP, LLMNR, NBNS, RDP, SIP, SMTP, SNMP, SSH, Telnet, UPNP, WSD, SMB, NBSS, IPP, PJL, RPC, mDNS, DHCP, PIC, CrestonCIP, IphoneSync, WinRM, VNC, SLP

## <a name="how-can-i-exclude-targets-from-being-probed-with-standard-discovery"></a>Comment puis-je exclure les cibles de l’analyse de la découverte standard ?
 S’il existe des appareils sur votre réseau qui ne doivent pas être activement analysés, vous pouvez également définir une liste d’exclusions pour empêcher leur analyse. La configuration est disponible dans la page des paramètres de découverte d’appareils. 

>[!NOTE]
> Les appareils peuvent toujours répondre aux tentatives de découverte multidiffusion sur le réseau. Ces appareils seront découverts, mais ne seront pas activement sondés. 

## <a name="can-i-exclude-devices-from-being-discovered"></a>Puis-je exclure les appareils de la découverte ?
 Comme la découverte d’appareils utilise des méthodes passives pour découvrir les appareils du réseau, tout appareil qui communique avec vos appareils intégrés dans le réseau d’entreprise peut être découvert et répertorié dans l’inventaire. Vous pouvez exclure les appareils de l’analyse active uniquement.

## <a name="how-frequent-is-the-active-probing"></a>Quelle est la fréquence de l’analyse active ?
 Les appareils sont activement sondés lorsque des modifications des caractéristiques de l’appareil sont observées pour s’assurer que les informations existantes sont à jour (en règle générale, les appareils ne sont interrogés qu’une seule fois par période de trois semaines).

## <a name="my-security-tool-raised-alert-on-unicastscannerps1-or-port-scanning-activity-initiated-by-it-what-should-i-do"></a>Mon outil de sécurité a déclenché une alerte UnicastScanner.ps1 l’activité d’analyse des ports initiée par elle, que dois-je faire ?
 Les scripts d’analyse actifs sont signés par Microsoft et sont sécurisés. Vous pouvez ajouter le chemin d’accès suivant à votre liste d’exclusions : `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps1`


## <a name="what-is-the-amount-of-traffic-being-generated-by-the-standard-discovery-active-probe"></a>Quelle est la quantité de trafic générée par la sonde active de découverte standard ?
 L’analyse active peut générer jusqu’à 50 000 go de trafic entre l’appareil intégré et l’appareil sondé, chaque tentative d’analyse

## <a name="why-is-there-a-discrepancy-between-can-be-onboarded-devices-in-the-device-inventory-and-the-number-of-devices-to-onboard-in-the-dashboard-tile"></a>Pourquoi existe-t-il une différence entre les appareils « peuvent être intégrés » dans l’inventaire des appareils et le nombre d’appareils à intégrer dans la vignette du tableau de bord ?
Vous remarquerez peut-être des différences entre le nombre d’appareils répertoriés sous « peut être intégré » dans l’inventaire des appareils, la recommandation de sécurité « intégration à Microsoft Defender pour point de terminaison » et le widget de tableau de bord « appareils à intégrer ».

 La recommandation de sécurité et le widget de tableau de bord sont pour les appareils stables dans le réseau ; à l’exclusion des appareils éphémères, des appareils invités et d’autres. L’idée est de recommander sur les appareils persistants, ce qui implique également le score de sécurité global de l’organisation.

## <a name="can-i-onboard-unmanaged-devices-that-were-found"></a>Puis-je intégrer des appareils non utilisés qui ont été trouvés ?
 Oui. Vous pouvez intégrer manuellement des appareils non utilisés. Les points de terminaison non pris en compte dans votre réseau introduisent des vulnérabilités et des risques pour votre réseau. Leur intégration au service peut accroître leur visibilité sur la sécurité. 

## <a name="ive-noticed-that-unmanaged-device-health-state-is-always-active-why-is-that"></a>J’ai remarqué que l’état d’état d’état de l’appareil non pris en compte est toujours « Actif », pourquoi ?
Temporairement, l’état d’état d’état de l’appareil non gestioné sera « Actif » pendant la période de rétention standard de l’inventaire des appareils, quel que soit leur état réel.


## <a name="does-standard-discovery-look-like-malicious-network-activity"></a>La découverte standard ressemble-t-elle à une activité réseau malveillante ?
Lorsque vous envisagez la découverte standard, vous vous demandez peut-être quelles sont les implications de l’analyse et si les outils de sécurité peuvent suspecter une telle activité comme malveillante. La sous-section suivante explique pourquoi, dans presque tous les cas, les organisations ne doivent pas avoir de préoccupations concernant l’activation de la découverte standard.  

### <a name="probing-is-distributed-across-all-windows-devices-on-the-network"></a>L’analyse est distribuée sur tous les Windows sur le réseau
Par opposition aux activités malveillantes, qui analysent généralement l’ensemble du réseau à partir d’un petit nombre d’appareils compromis, l’analyse de découverte standard de Microsoft Defender for Endpoint est lancée à partir de tous les appareils Windows intégrés rendant l’activité anormale et non anormale. L’analyse est gérée de manière centralisée à partir du cloud pour équilibrer la tentative d’analyse entre tous les appareils intégrés pris en charge dans le réseau.  

### <a name="active-probing-generates-negligible-amount-of-extra-traffic"></a>L’analyse active génère une quantité négligeable de trafic supplémentaire
En règle générale, les appareils non utilisés ne sont sondés qu’une seule fois par période de trois semaines et génèrent moins de 50 000 To de trafic. Les activités malveillantes incluent généralement des tentatives d’analyse répétitives élevées et, dans certains cas, une exfiltration de données qui génère une quantité importante de trafic réseau qui peut être identifiée comme une anomalie par les outils de surveillance du réseau. 

### <a name="your-windows-device-already-runs-active-discovery"></a>Votre appareil Windows exécute déjà la découverte active
Les fonctionnalités de découverte actives ont toujours été incorporées dans le système d’exploitation Windows pour rechercher des appareils, des points de terminaison et des imprimantes à proximité, pour faciliter les expériences « plug-and-play » et le partage de fichiers entre les points de terminaison du réseau. Des fonctionnalités similaires sont implémentées dans les appareils mobiles, l’équipement réseau et les applications d’inventaire pour n’en citer que quelques-uns.  

La découverte standard utilise les mêmes méthodes de découverte pour identifier les appareils et avoir une visibilité unifiée pour tous les appareils de votre réseau dans l’inventaire Microsoft 365 Defender périphériques. Par exemple, la découverte standard identifie les points de terminaison à proximité dans le réseau de la même manière que Windows les imprimantes disponibles dans le réseau. 

Les outils de sécurité et de surveillance du réseau sont en mesure d’effectuer de telles activités par les appareils sur le réseau. 

### <a name="only-unmanaged-devices-are-being-probed"></a>Seuls les appareils nonmanagés sont sondés
Les fonctionnalités de découverte d’appareils ont été conçues pour détecter et identifier uniquement les appareils non utilisés sur votre réseau. Cela signifie que les appareils précédemment découverts qui sont déjà intégrés à Microsoft Defender pour le point de terminaison ne seront pas sondés. 

### <a name="you-can-exclude-network-lures-from-active-probing"></a>Vous pouvez exclure les leurres réseau de l’analyse active
La découverte standard prend en charge l’exclusion des appareils ou des plages (sous-réseaux) de l’analyse active. Si des leurres réseau sont déployés, vous pouvez utiliser les paramètres de découverte de périphériques pour définir des exclusions basées sur des adresses IP ou des sous-réseaux (une plage d’adresses IP). La définition de ces exclusions garantit que ces appareils ne seront pas activement sondés et ne seront pas avertis. Ces appareils seront découverts à l’aide de méthodes passives uniquement (similaires au mode de découverte de base).
