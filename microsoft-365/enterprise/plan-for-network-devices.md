---
title: Planifier les périphériques réseau qui se connectent aux services Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Résumé : Décrit les considérations pour la capacité du réseau, les accélérateurs wan et les périphériques d’équilibrage de charge utilisés pour se connecter à Office 365.'
ms.openlocfilehash: e1209c13eb24d11a2cc9692957bc4ee5f6310f41
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50927499"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Planifier les périphériques réseau qui se connectent aux services Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*
  
Certains matériels réseau peuvent avoir des limites sur le nombre de sessions simultanées qui sont pris en charge. Pour les organisations qui ont plus de 2 000 utilisateurs, il est recommandé qu’elles surveillent leurs périphériques réseau pour s’assurer qu’elles sont en mesure de gérer le trafic de service Office 365 supplémentaire. Le logiciel de surveillance SNMP (Simple Network Management Protocol) peut vous aider à le faire.

Cet article fait partie de la planification [réseau et de l’optimisation](./network-planning-and-performance.md)des performances pour Office 365 .

Les paramètres de proxy Internet sortant local affectent également la connectivité aux services Office 365 pour vos applications clientes. Vous devez également configurer vos périphériques proxy réseau pour autoriser les connexions pour les URL et applications des services cloud De Microsoft. Chaque organisation est différente. Pour vous faire une idée de la façon dont Microsoft gère ce processus et de la quantité de bande passante que nous approvisionnement, lisez [l’étude de cas.](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)
  
Les articles d Skype Entreprise d’aide suivants ont plus d’informations sur Skype Entreprise paramètres de mise à jour :
  
- [Résolution des Skype Entreprise de la signature en ligne pour les administrateurs](/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [Vous ne pouvez pas vous connecter Skype Entreprise ou certaines fonctionnalités ne fonctionnent pas, car un pare-feu local bloque la connexion.](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Bien que la plupart de ces paramètres Skype Entreprise spécifiques, les instructions générales sur la configuration du réseau sont utiles pour tous Office 365 services.
  
## <a name="determining-network-capacity"></a>Détermination de la capacité du réseau

Chaque périphérique réseau existant sur une connexion a sa limite de capacité. Ces appareils incluent les cartes réseau client et serveur, les routeurs, les commutateurs et les concentrateurs qui les interconnectent. Une capacité réseau adéquate signifie qu’aucun d’entre eux n’est saturé. La surveillance de l’activité réseau est essentielle pour garantir que les charges réelles sur tous les appareils réseau sont inférieures à leur capacité maximale. La capacité du réseau affecte les performances des périphériques proxy.
  
Dans la plupart des cas, la bande passante de connexion Internet définit la limite du trafic. Les performances faibles pendant les heures de pointe du trafic sont probablement dues à une utilisation excessive du lien Internet. Cette situation s’applique également à un scénario de succursale, où les ordinateurs serveurs proxy de succursale sont connectés au périphérique proxy au siège social de la succursale sur une liaison de réseau large (WAN) lente.
  
Pour tester la capacité du réseau, surveillez l’activité réseau sur l’interface réseau proxy. S’il s’agit de plus de 75 % de la bande passante maximale d’une interface réseau, envisagez d’augmenter la bande passante de l’infrastructure réseau qui est insuffisante. Vous pouvez également utiliser des fonctionnalités avancées, telles que la compression HTTP.
  
## <a name="wan-accelerators"></a>Accélérateurs de réseau étendu

Si votre organisation utilise des appliances proxy d’accélération de réseau wan (WAN), vous pouvez rencontrer des problèmes lorsque vous accédez aux services Office 365 réseau. Vous devrez peut-être optimiser votre ou vos périphériques réseau pour vous assurer que vos utilisateurs ont une expérience cohérente lors de l’accès Office 365. Par exemple, les services Office 365 chiffrent certains Office 365 contenu et l’en-tête TCP. Il se peut que votre appareil ne soit pas en mesure de gérer ce type de trafic.
  
Lisez notre déclaration de support sur l’utilisation du contrôleur [d’optimisation wan ou des périphériques de trafic/inspection avec Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Dispositifs d’équilibrage de charge matériels et logiciels

Votre organisation doit utiliser un programme d’équilibrage de la charge matérielle (HLB) ou une solution d’équilibrage de la charge réseau (NLB) pour distribuer les demandes à vos serveurs AD FS (Active Directory Federation Services) et/ou à vos serveurs hybrides Exchange. Les appareils d’équilibrage de charge contrôlent le trafic réseau vers les serveurs locaux. Ces serveurs sont essentiels pour garantir la disponibilité de l' sign-on unique et Exchange déploiement hybride.
  
Nous fournissons une solution DLB logicielle intégrée à Windows Server. Office 365 prend en charge cette solution pour mettre en œuvre l’équilibrage de charge.
  
## <a name="firewalls-and-proxies"></a>Pare-feu et proxies

Pour plus d’informations sur la configuration des pare-feux et des proxies pour la connexion à Office 365, voir Gestion des points de terminaison [de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) [,](assessing-network-connectivity.md)Évaluation de la connectivité réseau Office 365 et FAQ sur les points de terminaison [Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) pour en savoir plus sur les appareils et la sélection de circuits.
  
## <a name="see-also"></a>Voir aussi

[Guides d’installation pour Office 365 services](setup-guides-for-microsoft-365.md)

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)