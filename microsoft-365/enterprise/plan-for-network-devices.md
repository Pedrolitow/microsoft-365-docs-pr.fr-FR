---
title: Planifier les périphériques réseau qui se connectent aux services Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/29/2016
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Résumé : Décrit les considérations relatives à la capacité réseau, aux accélérateurs WAN et aux appareils d’équilibrage de charge utilisés pour se connecter à Office 365.'
ms.openlocfilehash: 3b79e73f292ecf1db38a90364db3d2e475723158
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622833"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Planifier les périphériques réseau qui se connectent aux services Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*
  
Certains matériels réseau peuvent avoir des limitations sur le nombre de sessions simultanées prises en charge. Pour les organisations comptant plus de 2 000 utilisateurs, nous recommandons qu’elles surveillent leurs appareils réseau pour s’assurer qu’elles sont capables de gérer le trafic de service Office 365 supplémentaire. Le logiciel de supervision SNMP (Simple Network Management Protocol) peut vous aider à effectuer cette opération.

Cet article fait partie de la [planification du réseau et de l’optimisation des performances pour Office 365](./network-planning-and-performance.md).

Les paramètres de proxy Internet sortants locaux affectent également la connectivité aux services Office 365 pour vos applications clientes. Vous devez également configurer vos périphériques proxy réseau pour autoriser les connexions pour les URL et applications des services cloud Microsoft. Chaque organisation est différente. Pour avoir une idée de la façon dont Microsoft gère ce processus et la quantité de bande passante que nous approvisionnons, [lisez l’étude de cas](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
Les articles d’aide Skype Entreprise suivants fournissent plus d’informations sur Skype Entreprise paramètres :
  
- [Résolution des erreurs de connexion Skype Entreprise Online pour les administrateurs](/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [Vous ne pouvez pas vous connecter à Skype Entreprise, ou certaines fonctionnalités ne fonctionnent pas, car un pare-feu local bloque la connexion](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Bien que la plupart de ces paramètres soient spécifiques à Skype Entreprise, les conseils généraux sur la configuration réseau sont utiles pour tous les services Office 365.
  
## <a name="determining-network-capacity"></a>Détermination de la capacité réseau

Chaque appareil réseau qui existe sur une connexion a sa limite de capacité. Ces appareils incluent les cartes réseau client et serveur, les routeurs, les commutateurs et les hubs qui les connectent. Une capacité réseau suffisante signifie qu’aucun d’entre eux n’est saturé. La surveillance de l’activité réseau est essentielle pour vous assurer que les charges réelles sur tous les appareils réseau sont inférieures à leur capacité maximale. La capacité réseau affecte les performances des périphériques proxy.
  
Dans la plupart des cas, la bande passante de connexion Internet définit la limite de la quantité de trafic. Les performances faibles pendant les heures de pointe du trafic sont probablement dues à une utilisation excessive de la liaison Internet. Cette situation s’applique également à un scénario de succursale, où les ordinateurs de serveur proxy de succursale sont connectés à l’appareil proxy au siège social de la branche via une liaison de réseau étendu lent (WAN).
  
Pour tester la capacité réseau, surveillez l’activité réseau sur l’interface réseau proxy. S’il s’agit de plus de 75 % de la bande passante maximale d’une interface réseau, envisagez d’augmenter la bande passante de l’infrastructure réseau qui est insuffisante. Vous pouvez également utiliser des fonctionnalités avancées, telles que la compression HTTP.
  
## <a name="wan-accelerators"></a>Accélérateurs de réseau étendu

Si votre organisation utilise des appliances proxy d’accélération de réseau étendu (WAN), vous pouvez rencontrer des problèmes lorsque vous accédez aux services Office 365. Vous devrez peut-être optimiser votre appareil réseau ou vos appareils pour vous assurer que vos utilisateurs bénéficient d’une expérience cohérente lors de l’accès à Office 365. Par exemple, Office 365 services chiffrent du contenu Office 365 et l’en-tête TCP. Votre appareil peut ne pas être en mesure de gérer ce type de trafic.
  
Lisez notre déclaration de support sur [l’utilisation du contrôleur d’optimisation WAN ou des appareils d’inspection/de trafic avec Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Dispositifs d’équilibrage de charge matériels et logiciels

Votre organisation doit utiliser un équilibreur de charge matériel (HLB) ou une solution d’équilibrage de charge réseau (NLB) pour distribuer les requêtes à vos serveurs Services ADFS (AD FS) et/ou à vos serveurs hybrides Exchange. Les appareils d’équilibrage de charge contrôlent le trafic réseau vers les serveurs locaux. Ces serveurs sont essentiels pour garantir la disponibilité de l’authentification unique et du déploiement hybride Exchange.
  
Nous fournissons une solution d’équilibrage de charge réseau basée sur un logiciel intégrée à Windows Server. Office 365 prend en charge cette solution pour mettre en œuvre l’équilibrage de charge.
  
## <a name="firewalls-and-proxies"></a>Pare-feu et proxys

Pour plus d’informations sur la configuration des pare-feu et des proxys pour se connecter à Office 365, consultez [La gestion des points](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) de terminaison Office 365, [l’évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md) et [Office 365 faq sur les points de terminaison](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) pour en savoir plus sur les appareils et la sélection du circuit.
  
## <a name="see-also"></a>Voir aussi

[Guides d’installation pour les services Office 365](setup-guides-for-microsoft-365.md)

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)