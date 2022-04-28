---
title: Prise en charge de la traduction d'adresses réseau (NAT) avec Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Cet article fournit des détails sur la façon d’estimer le nombre de clients que vous pouvez utiliser par adresse IP dans votre organisation à l’aide de NAT.
ms.openlocfilehash: 71c9d54ddf88d9b69c890609fea7ece8cac0de33
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097379"
---
# <a name="nat-support-with-office-365"></a>Prise en charge de la traduction d'adresses réseau (NAT) avec Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Auparavant, les conseils suggéraient que le nombre maximal de clients Exchange que vous devez utiliser par adresse IP pour vous connecter à Office 365 était d’environ 2 000 clients par port réseau.
  
## <a name="why-use-nat"></a>Pourquoi utiliser NAT ?

En utilisant NAT, des milliers de personnes sur un réseau d’entreprise peuvent « partager » quelques adresses IP routables publiquement.
  
La plupart des réseaux d’entreprise utilisent un espace d’adressage IP privé (RFC1918). L’espace d’adressage privé est alloué par l’IANA (Internet Assigned Numbers Authority) et destiné uniquement aux réseaux qui ne sont pas acheminés directement vers et depuis l’Internet global.
  
Pour fournir un accès Internet aux appareils sur un espace d’adressage IP privé, les organisations utilisent des technologies de passerelle telles que des pare-feu et des proxys qui fournissent des services de traduction d’adresses réseau (NAT) ou de traduction d’adresses de port (PAT). Ces passerelles font en sorte que le trafic provenant d’appareils internes vers Internet (y compris Office 365) semble provenir d’une ou plusieurs adresses IP routables publiquement. Chaque connexion sortante à partir d’un appareil interne se traduit par un port TCP source différent sur l’adresse IP publique. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Pourquoi avez-vous besoin d’avoir autant de connexions ouvertes à Office 365 en même temps ?

Outlook peut ouvrir huit connexions ou plus (dans les cas où il existe des compléments, des calendriers partagés, des boîtes aux lettres, etc.). Étant donné qu’un maximum de 64 000 ports est disponible sur un appareil NAT basé sur Windows, il peut y avoir un maximum de 8 000 utilisateurs derrière une adresse IP avant que les ports ne soient épuisés. Notez que si les clients utilisent des appareils non Windows basés sur le système d’exploitation pour NAT, le nombre total de ports disponibles dépend de l’appareil nat ou des logiciels utilisés. Dans ce scénario, le nombre maximal de ports peut être inférieur à 64 000. La disponibilité des ports est également affectée par d’autres facteurs tels que Windows la restriction de 4 000 ports pour sa propre utilisation, ce qui réduit le nombre total de ports disponibles à 60 000. Il peut y avoir d’autres applications, telles qu’Internet Explorer, qui peuvent se connecter en même temps, nécessitant des ports supplémentaires.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Calcul du nombre maximal d’appareils pris en charge derrière une seule adresse IP publique avec Office 365

Pour déterminer le nombre maximal d’appareils derrière une seule adresse IP publique, vous devez surveiller le trafic réseau pour déterminer la consommation maximale de ports par client. En outre, un facteur de pointe doit être utilisé pour l’utilisation du port (minimum 4). 
  
 **Utilisez la formule suivante pour calculer le nombre d’appareils pris en charge par adresse IP :**
  
Nombre maximal d’appareils pris en charge derrière une seule adresse IP publique = (64 000 - ports restreints)/(Consommation maximale de ports + facteur de pointe)
  
 **Par exemple, si les valeurs suivantes étaient vraies :**
  
- **Ports restreints :** 4 000 pour le système d’exploitation

- **Consommation maximale de ports :** 6 par appareil

- **Facteur de pointe :** 4

Ensuite, le nombre maximal d’appareils pris en charge derrière une seule adresse IP publique = (64 000 - 4 000)/(6 + 4) = 6 000
  
Avec la publication de Office 365 pack d’hébergement, inclus dans les mises à jour de septembre 2011 pour Microsoft Office Outlook 2007 ou de novembre 2011 pour Microsoft Outlook 2010, ou une mise à jour ultérieure, le nombre de connexions provenant de Outlook (les deux Office Outlook 2007 avec Service Pack 2 et Outlook 2010) à Exchange peuvent être aussi peu que 2. Vous devez prendre en compte les différents systèmes d’exploitation, les comportements des utilisateurs, et ainsi de suite pour déterminer le nombre minimal et maximal de ports dont votre réseau aura besoin au pic.
  
Si vous souhaitez prendre en charge davantage d’appareils derrière une seule adresse IP publique, suivez les étapes décrites pour évaluer le nombre maximal d’appareils pouvant être pris en charge :
  
Surveillez le trafic réseau pour déterminer la consommation maximale des ports par client. Vous devez collecter ces données :
  
- À partir de plusieurs emplacements
    
- À partir de plusieurs appareils
    
- À plusieurs reprises
    
Utilisez la formule précédente pour calculer le nombre maximal d’utilisateurs par adresse IP qui peuvent être pris en charge dans leur environnement.
  
Il existe différentes méthodes pour distribuer la charge du client entre d’autres adresses IP publiques. Les stratégies disponibles dépendent des fonctionnalités de la solution de passerelle d’entreprise. La solution la plus simple consiste à segmenter votre espace d’adressage utilisateur et à « affecter » statiquement un certain nombre d’adresses IP à chaque passerelle. Une autre alternative offerte par de nombreux appareils de passerelle est la possibilité d’utiliser un pool d’adresses IP. L’avantage du pool d’adresses est qu’il est beaucoup plus dynamique et moins susceptible de nécessiter un ajustement à mesure que votre base d’utilisateurs augmente.
  
## <a name="see-also"></a>Voir aussi

[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
