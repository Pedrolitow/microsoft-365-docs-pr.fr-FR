---
title: Prise en charge de la traduction d'adresses réseau (NAT) avec Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: Cet article fournit des détails sur la façon d’obtenir une valeur approximative du nombre de clients que vous pouvez utiliser par adresse IP dans votre organisation à l’aide de nat.
ms.openlocfilehash: f48874853c3acb80927933761862b14379b6d4bd
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46689612"
---
# <a name="nat-support-with-office-365"></a>Prise en charge de la traduction d'adresses réseau (NAT) avec Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Auparavant, les conseils suggéraient que le nombre maximal de clients Exchange que vous devez utiliser par adresse IP pour vous connecter à Office 365 était d’environ 2 000 clients par port réseau.
  
## <a name="why-use-nat"></a>Pourquoi utiliser NAT ?

À l’aide de nat, des milliers de personnes sur un réseau d’entreprise peuvent « partager » quelques adresses IP routables publiquement.
  
La plupart des réseaux d’entreprise utilisent un espace d’adressare IP privé (RFC1918). L’espace d’adressag privé est alloué par l’IANA (Internet Assigned Numbers Authority) et destiné uniquement aux réseaux qui ne sont pas acheminés directement vers et depuis Internet.
  
Pour fournir un accès Internet aux appareils sur un espace d’adressa visite IP privé, les organisations utilisent des technologies de passerelle telles que les pare-feux et les proxies qui fournissent des services de traduction d’adresses réseau (NAT) ou de traduction d’adresses de port (PAT). Ces passerelles font en sorte que le trafic provenant d’appareils internes vers Internet (y compris Office 365) semble être provenant d’une ou plusieurs adresses IP routables publiquement. Chaque connexion sortante d’un appareil interne se traduit par un port TCP source différent sur l’adresse IP publique. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Pourquoi devez-vous avoir autant de connexions ouvertes à Office 365 en même temps ?

Outlook peut ouvrir huit connexions ou plus (dans les situations où il existe des modules de 2013, des calendriers partagés, des boîtes aux lettres, etc.). Étant donné qu’un maximum de 64 000 ports sont disponibles sur un périphérique NAT basé sur Windows, il peut y avoir 8 000 utilisateurs au maximum derrière une adresse IP avant que les ports ne soient épuisés. Notez que si les clients utilisent des appareils non basés sur le système d’exploitation Windows pour nat, le nombre total de ports disponibles dépend de l’appareil ou du logiciel NAT utilisé. Dans ce scénario, le nombre maximal de ports peut être inférieur à 64 000. La disponibilité des ports est également affectée par d’autres facteurs tels que Windows limitant 4 000 ports pour son propre usage, ce qui réduit le nombre total de ports disponibles à 60 000. Il peut y avoir d’autres applications, telles qu’Internet Explorer, qui peuvent se connecter en même temps, nécessitant des ports supplémentaires.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Calcul du nombre maximal d’appareils pris en charge derrière une adresse IP publique unique avec Office 365

Pour déterminer le nombre maximal d’appareils derrière une seule adresse IP publique, vous devez surveiller le trafic réseau afin de déterminer la consommation maximale des ports par client. En outre, un facteur de pointe doit être utilisé pour l’utilisation du port (minimum 4). 
  
 **Utilisez la formule suivante pour calculer le nombre d’appareils pris en charge par adresse IP :**
  
Nombre maximal d’appareils pris en charge derrière une seule adresse IP publique = (64 000 - ports restreints)/(Consommation maximale des ports + facteur de pointe)
  
 **Par exemple, si les valeurs suivantes sont vraies :**
  
- **Ports restreints :** 4 000 pour le système d’exploitation

- **Consommation maximale des ports :** 6 par appareil

- **Facteur de pointe :** 4

Ensuite, le nombre maximal d’appareils pris en charge derrière une seule adresse IP publique = (64 000 - 4 000)/(6 + 4) = 6 000
  
Avec la publication du pack d’hébergement Office 365, inclus dans les mises à jour de septembre 2011 pour Microsoft Office Outlook 2007 ou novembre 2011 pour Microsoft Outlook 2010, ou d’une mise à jour ultérieure, le nombre de connexions de Outlook (Office Outlook 2007 avec Service Pack 2 et Outlook 2010) à Exchange peut être aussi petit que 2. Vous devez prendre en compte les différents systèmes d’exploitation, les comportements des utilisateurs, etc. pour déterminer le nombre minimal et maximal de ports dont votre réseau aura besoin au maximum.
  
Si vous souhaitez prendre en charge davantage d’appareils derrière une seule adresse IP publique, suivez les étapes décrites pour évaluer le nombre maximal d’appareils qui peuvent être pris en charge :
  
Surveillez le trafic réseau pour déterminer la consommation maximale des ports par client. Vous devez collecter les données ci-après :
  
- À partir de plusieurs emplacements
    
- À partir de plusieurs appareils
    
- À plusieurs reprises
    
Utilisez la formule précédente pour calculer le nombre maximal d’utilisateurs par adresse IP qui peuvent être pris en charge dans leur environnement.
  
Il existe différentes méthodes pour répartir la charge du client entre des adresses IP publiques supplémentaires. Les stratégies disponibles dépendent des fonctionnalités de la solution de passerelle d’entreprise. La solution la plus simple consiste à segmenter l’espace d’adressa ment de l’utilisateur et à « attribuer » de manière statique un certain nombre d’adresses IP à chaque passerelle. De nombreux périphériques de passerelle offrent également la possibilité d’utiliser un pool d’adresses IP. L’avantage du pool d’adresses est qu’il est beaucoup plus dynamique et moins susceptible de nécessiter un ajustement à mesure que votre base d’utilisateurs augmente.
  
## <a name="see-also"></a>Voir aussi

[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
