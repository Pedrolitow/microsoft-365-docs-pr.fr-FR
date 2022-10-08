---
title: Réponse contoso-19 et prise en charge du travail hybride
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Découvrez comment Contoso Corporation a répondu à la pandémie du COVID-19 et a conçu son infrastructure d’installation et de mise à jour logicielle pour le travail hybride.
ms.openlocfilehash: f59017c8da65317233d13b3fa2b5d0c0d234af68
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67987145"
---
# <a name="contosos-covid-19-response-and-support-for-hybrid-work"></a>Réponse contoso-19 et prise en charge du travail hybride

Contoso avait toujours pris en charge ses travailleurs à distance, qui accédaient aux ressources locales via un serveur VPN central au siège de Paris. Contoso avait émis à tous les travailleurs distants un ordinateur portable géré. Les travailleurs locaux avaient un mélange d’ordinateurs de bureau et d’ordinateurs portables.

## <a name="contosos-response-to-covid-19"></a>Réponse de Contoso à COVID-19

Avec le début de la pandémie du COVID-19, soudainement tous les travailleurs, sauf les travailleurs essentiels, étaient des travailleurs à distance. Contoso a répondu en déplaçant sa main-d’œuvre à travailler de chez elle et en effectuant ses principales activités par le biais d’un accès à distance aux ressources locales et en ligne à l’aide des services cloud Microsoft 365.

Contoso disposait de serveurs VPN d’accès à distance au siège de Paris pour prendre en charge les 25 % de sa main-d’œuvre déjà à distance, mais a rapidement décidé de mettre à l’échelle sa capacité d’accès à distance pour prendre en charge 90 % de son effectif. Contoso a déployé des serveurs VPN d’accès à distance dans chaque bureau satellite afin que les travailleurs distants utilisent un point d’entrée régional pour accéder à l’intranet Contoso.

Contoso a également mis à jour la configuration des clients VPN installés sur des ordinateurs portables, des tablettes et des téléphones intelligents pour le tunneling fractionné afin que le trafic pour l’ensemble Optimize de Office 365 points de terminaison contourne la connexion VPN et soit envoyé directement sur Internet. Pour plus d’informations, consultez [Optimiser la connectivité Office 365 pour les utilisateurs distants à l’aide du tunneling fractionné VPN](../enterprise/microsoft-365-vpn-split-tunnel.md).

Voici la configuration obtenue avec des périphériques VPN installés au siège de Paris et dans chacun des bureaux satellites. 

![Infrastructure VPN de Contoso.](../media/contoso-remote-onsite-work/contoso-vpn-infrastructure.png)

Un worker distant avec le client VPN installé utilise DNS pour rechercher le bureau le plus proche au plan régional et se connecte à l’appareil VPN qui y est installé. Avec le tunneling fractionné, le trafic vers les points de terminaison Microsoft 365 Optimize est envoyé directement à l’emplacement réseau Microsoft 365 le plus proche au niveau régional. Tout autre trafic est envoyé via la connexion VPN à l’appareil VPN.

## <a name="contosos-support-for-hybrid-work"></a>Prise en charge de Contoso pour le travail hybride

Une fois que les modifications initiales ont été apportées pour prendre en charge la plupart des travailleurs à distance pendant les verrouillages régionaux, Contoso a apporté des modifications d’infrastructure pour prendre en charge le travail hybride dans lequel un worker peut être :

- Toujours distant.
- Toujours sur place.
- Combinaison d’éléments sur site et distants.

Les fonctionnalités d’identité, de sécurité et de conformité de Microsoft 365 sont conçues pour Confiance nulle et fonctionner indépendamment de l’emplacement de l’utilisateur et de son appareil. Pour plus d’informations, consultez [Confiance nulle](https://www.microsoft.com/security/business/zero-trust).

Toutefois, la gestion des nouvelles installations et mises à jour des logiciels dépend de l’emplacement de l’appareil, car le logiciel à installer peut provenir d’une source locale ou Internet. Les architectes informatiques de Contoso ont conçu leurs nouvelles installations et mises à jour de l’infrastructure en fonction de l’emplacement de l’appareil, plutôt que du worker.

Ils ont désigné deux types d’appareils : dédiés en local et itinérants.

### <a name="dedicated-on-premises"></a>Dédié localement

Un appareil local dédié est un ordinateur de bureau ou de serveur qui ne quitte jamais l’intranet Contoso et n’a pas de client VPN installé. Ces appareils locaux continuent à utiliser Microsoft Endpoint Configuration Manager et ses points de distribution pour les installations et mises à jour de Windows 10, Applications Microsoft 365 pour les grandes entreprises et le navigateur Edge.

### <a name="roaming"></a>Itinérance

Un appareil itinérant peut quitter l’intranet contoso et inclut des ordinateurs portables émis pour de nombreux employés de bureau et tous les travailleurs à distance et d’autres appareils appartenant à l’organisation, tels que les téléphones intelligents et les tablettes, avec le client VPN Contoso installé. 

Étant donné que ces appareils peuvent être connectés à Internet à tout moment, ils utilisent Intune ou d’autres services cloud pour installer et mettre à jour Windows 10, Applications Microsoft 365 pour les grandes entreprises et Edge. Ils n’utilisent pas les points de distribution locaux Configuration Manager existants.

Cela signifie que certaines des installations et mises à jour de l’appareil itinérant seront effectuées sur Internet alors qu’elles sont locales et connectées à l’intranet. Mais les architectes informatiques de Contoso ont décidé que la simplicité de la configuration était plus importante que l’optimisation de la bande passante intranet vers Internet, en particulier lorsque la plupart des travailleurs distants sont rarement connectés à l’intranet.

Voici l’infrastructure qui en résulte.

![L’infrastructure d’installation et de mise à jour de Contoso.](../media/contoso-remote-onsite-work/contoso-updates-infrastructure.png)

Le comportement d’installation et de mise à jour est déterminé en faisant des comptes d’ordinateur des appareils un membre de l’un de ces groupes :

- OnPremDevices

  Le client Configuration Manager sur l’appareil utilise des points de distribution pour les installations et les mises à jour.

- RoamingDevices

  Intune et d’autres paramètres sur l’appareil spécifient l’utilisation du réseau Microsoft 365 pour les installations et les mises à jour.

## <a name="new-onboarding-process"></a>Nouveau processus d’intégration

Pour un nouvel appareil local dédié émis à un nouveau worker ou pour un nouveau serveur dans un centre de données, lorsque le worker se connecte, le client Configuration Manager basé sur l’appartenance de l’appareil au groupe OnPremDevices télécharge et installe les dernières mises à jour pour Windows 10, Applications Microsoft 365 pour les grandes entreprises et Edge à partir de points de distribution Configuration Manager locaux. Une fois terminé, l’appareil local dédié est prêt à être utilisé et utilise ces points de distribution pour les mises à jour en cours.

Pour un nouvel appareil distant émis à un nouveau worker, lorsque le worker se connecte, l’appareil, en fonction de son appartenance au groupe RoamingDevices, contacte le service cloud Intune et d’autres services et télécharge et installe les dernières mises à jour pour Windows 10, Applications Microsoft 365 pour les grandes entreprises et Edge. Une fois terminé, l’appareil distant est prêt à être utilisé et utilise le client VPN installé pour l’accès aux ressources locales et le réseau Microsoft 365 pour les mises à jour en cours.

## <a name="next-step"></a>Étape suivante

[Configurez votre infrastructure pour le travail hybride](empower-people-to-work-remotely.md) dans votre organisation.
