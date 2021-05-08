---
title: Questions fréquemment posées sur la découverte d’appareils
description: Trouvez des réponses aux questions fréquemment posées sur la découverte d’appareils
keywords: détection d’appareils, découverte, passif, proactif, réseau, visibilité, serveur, station de travail, intégration, appareils nonmanagés
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1c61e69b5c8d414ab229fa8bf64eb657a6e40304
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52245959"
---
# <a name="device-discovery-frequently-asked-questions"></a>Questions fréquemment posées sur la découverte d’appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

Trouvez des réponses aux questions fréquemment posées sur la découverte d’appareils.

## <a name="what-is-basic-discovery-mode"></a>Qu’est-ce que le mode de découverte de base ?
Ce mode permet à chaque appareil intégré à Microsoft Defender for Endpoint de collecter des données réseau et de découvrir les appareils voisins. Les points de terminaison intégrés collectent passivement des événements dans le réseau et extraient les informations de l’appareil. Aucun trafic réseau n’est initié. Les points de terminaison intégrés extraient simplement les données de chaque trafic réseau visible par un appareil intégré. Ces données sont utilisées pour lister les appareils non utilisés dans votre réseau.

## <a name="can-i-disable-basic-discovery"></a>Puis-je désactiver la découverte de base ?
Vous avez la possibilité de désactiver la découverte d’appareils via la page [Fonctionnalités avancées.](advanced-features.md) Toutefois, vous perdrez la visibilité sur les appareils non utilisés dans votre réseau. 

## <a name="what-is-standard-discovery-mode"></a>Qu’est-ce que le mode de découverte standard ?
 Dans ce mode, les points de terminaison intégrés à Microsoft Defender pour le point de terminaison peuvent sonder activement les appareils observés dans le réseau pour enrichir les données collectées (avec une quantité négligeable de trafic réseau). Ce mode est vivement recommandé pour créer un inventaire fiable et cohérent des appareils. Si vous choisissez de désactiver ce mode et de sélectionner le mode de découverte de base, vous n’aurez probablement qu’une visibilité limitée des points de terminaison nonmanagés dans votre réseau.

## <a name="can-i-control-which-devices-perform-standard-discovery"></a>Puis-je contrôler quels appareils effectuent la découverte standard ?
 Vous pouvez personnaliser la liste des appareils utilisés pour effectuer la découverte standard. Vous pouvez activer la découverte standard sur tous les appareils intégrés qui également prendre en charge cette fonctionnalité (appareils actuellement Windows 10 uniquement) ou sélectionner un sous-ensemble ou sous-ensemble de vos appareils en spécifiant leurs balises d’appareil. Dans ce cas, tous les autres appareils sont configurés pour exécuter la découverte de base uniquement. La configuration est disponible dans la page des paramètres de découverte d’appareils.

## <a name="can-i-exclude-unmanaged-devices-from-the-device-inventory-list"></a>Puis-je exclure des appareils non utilisés de la liste d’inventaire des appareils ?
Oui, vous pouvez appliquer des filtres pour exclure les appareils nonmanagés de la liste d’inventaire des appareils. Vous pouvez également utiliser la colonne d’état d’intégration sur les requêtes API pour filtrer les appareils nonmanagés. 


## <a name="which-onboarded-devices-can-perform-discovery"></a>Quels appareils intégrés peuvent effectuer la découverte ?
 Les appareils intégrés s’exécutant Windows 10 version 1809 ou ultérieure peuvent effectuer la découverte.

## <a name="what-happens-if-my-onboarded-devices-is-connected-to-my-home-network-or-to-public-access-point"></a>Que se passe-t-il si mes appareils intégrés sont connectés à mon réseau à domicile ou au point d’accès public ?
 Le moteur de découverte fait la distinction entre les événements réseau reçus dans le réseau d’entreprise et en dehors du réseau d’entreprise. En corrélant les identificateurs réseau sur tous les clients du client, les événements sont différenciés entre ceux reçus à partir de réseaux privés et de réseaux d’entreprise. Par exemple, si la majorité des périphériques du réseau indiquent qu’ils sont connectés au même nom de réseau, avec la même passerelle par défaut et la même adresse de serveur DHCP, il est possible de supposer que ce réseau est probablement un réseau d’entreprise. Les périphériques de réseau privé ne sont pas répertoriés dans l’inventaire et ne sont pas activement sondés.

## <a name="what-protocols-are-you-capturing-and-analyzing"></a>Quels protocoles capturez-vous et analysez-vous ?
 Par défaut, tous les appareils intégrés s’exécutant sur Windows 10 version 1809 ou ultérieure capturent et analysent les protocoles suivants : ARP, CDP, DHCP, DHCPv6, IP (en-têtes), LLDP, LLMNR, mDNS, MNDP, NBNS, SSDP, TCP (en-têtes), UDP (en-têtes), WSD

## <a name="which-protocols-do-you-use-for-active-probing-in-standard-discovery"></a>Quels protocoles utilisez-vous pour l’analyse active dans la découverte standard ?
 Lorsqu’un appareil est configuré pour exécuter la découverte standard, les services exposés sont sondés à l’aide des protocoles suivants : ARP, FTP, HTTP, ICMP, LLMNR, NBNS, RDP, SIP, SMTP, SNMP, SSH, Telnet, UPNP, WSD, SMB, NBSS, IPP, PJL

## <a name="how-can-i-exclude-targets-from-being-probed-with-standard-discovery"></a>Comment puis-je exclure les cibles de l’analyse de la découverte standard ?
 S’il existe des appareils sur votre réseau qui ne doivent pas être activement analysés, vous pouvez également définir une liste d’exclusions pour empêcher leur analyse. La configuration est disponible dans la page des paramètres de découverte d’appareils.

## <a name="can-i-exclude-devices-from-being-discovered"></a>Puis-je exclure les appareils de la découverte ?
 Comme la découverte d’appareils utilise des méthodes passives pour découvrir les appareils du réseau, tout appareil qui communique avec vos appareils intégrés dans le réseau d’entreprise peut être découvert et répertorié dans l’inventaire. Vous pouvez exclure les appareils de l’analyse active uniquement.

## <a name="how-frequent-is-the-active-probing"></a>Quelle est la fréquence de l’analyse active ?
 Les appareils sont activement sondés lorsque des modifications des caractéristiques de l’appareil sont observées (toutes les 1 à 3 semaines) pour s’assurer que les informations existantes sont à jour.

## <a name="my-security-tool-raised-alert-on-unicastscannerps1-or-port-scanning-activity-initiated-by-it-what-should-i-do"></a>Mon outil de sécurité a déclenché une alerte UnicastScanner.ps1 l’activité d’analyse des ports initiée par elle, que dois-je faire ?
 Les scripts d’analyse actifs sont signés par Microsoft et sont sécurisés. Vous pouvez ajouter le chemin d’accès suivant à votre liste d’exclusions : `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps`


## <a name="what-is-the-amount-of-traffic-being-generated-by-the-standard-discovery-active-probe"></a>Quelle est la quantité de trafic générée par la sonde active de découverte standard ?
 L’analyse active peut générer jusqu’à 5K de trafic entre l’appareil intégré et l’appareil sondé, chaque tentative d’analyse

## <a name="why-is-there-a-discrepancy-between-can-be-onboarded-devices-in-the-device-inventory-and-the-number-of-devices-to-onboard-in-the-dashboard-tile"></a>Pourquoi existe-t-il une différence entre les appareils « peuvent être intégrés » dans l’inventaire des appareils et le nombre d’appareils à intégrer dans la vignette du tableau de bord ?
Vous remarquerez peut-être des différences entre le nombre d’appareils répertoriés sous « Peut être intégré » dans l’inventaire des appareils, la recommandation de sécurité « intégration à Microsoft Defender pour point de terminaison » et le widget de tableau de bord « appareils à intégrer ».

 La recommandation de sécurité et le widget de tableau de bord sont pour les appareils stables dans le réseau ; à l’exclusion des appareils éphémères, des appareils invités et d’autres. L’idée est de recommander sur les appareils persistants, ce qui implique également le score de sécurité global de l’organisation.

## <a name="can-i-onboard-unmanaged-devices-that-were-found"></a>Puis-je intégrer des appareils non utilisés qui ont été trouvés ?
 Oui. Les points de terminaison non pris en compte dans votre réseau introduisent des vulnérabilités et des risques pour votre réseau. Leur intégration au service peut accroître leur visibilité sur la sécurité. 


