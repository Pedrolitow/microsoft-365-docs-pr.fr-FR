---
title: Réponse COVID-19 et prise en charge de contoso pour le travail à distance et sur site
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre comment Contoso Corporation a répondu au COVID-19 Pandemic et a conçu son infrastructure d’installation et de mise à jour logicielle pour un travail à distance ou sur site.
ms.openlocfilehash: 8e25b399d7acd2cb3486283623d29315eac9491e
ms.sourcegitcommit: bdf65d48b20f0f428162c39ee997accfa84f4e5d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "49371762"
---
# <a name="contosos-covid-19-response-and-support-for-remote-and-onsite-work"></a>Réponse COVID-19 et prise en charge de contoso pour le travail à distance et sur site

Contoso a toujours pris en charge ses collaborateurs distants, qui ont accédé aux ressources locales via un serveur VPN central dans le siège social de Paris. Contoso a émis tous les collaborateurs distants d’un ordinateur portable géré. Les travailleurs sur site disposaient d’un mélange d’ordinateurs de bureau et d’ordinateurs portables.

## <a name="contosos-response-to-covid-19"></a>Réponse de contoso à COVID-19

Avec le début du COVID-19 Pandemic, tous les employés, mais les employés essentiels étaient des travailleurs distants. Contoso a répondu en incitant son personnel à travailler depuis son domicile et à mener ses activités principales via l’accès à distance aux ressources locales et en ligne à l’aide des services Cloud de Microsoft 365.

Contoso disposait de serveurs VPN d’accès à distance au siège social de Paris pour prendre en charge les 25% de ses employés distants, mais il a été rapidement déplacé vers le haut de sa capacité d’accès à distance afin de prendre en charge 90% de ses effectifs. Contoso a déployé des serveurs VPN d’accès à distance dans chaque bureau de satellites afin que les travailleurs distants utilisent un point d’entrée de fermeture régional pour l’accès à l’intranet contoso.

Contoso a également mis à jour la configuration des clients VPN installés sur des ordinateurs portables, des tablettes et des téléphones intelligents pour le tunneling fractionné afin que le trafic pour l’ensemble d’utilisateurs de points de terminaison Office 365 a contourné la connexion VPN et qu’il a été envoyé directement sur Internet. Pour plus d’informations, consultez la rubrique [optimize Office 365 Connectivity for Remote Users using VPN Split tunneling](../enterprise/microsoft-365-vpn-split-tunnel.md).

Voici la configuration obtenue avec les périphériques VPN installés dans le siège de Paris et chacun des bureaux satellites. 

![Infrastructure VPN de contoso](../media/contoso-remote-onsite-work/contoso-vpn-infrastructure.png)

Un collaborateur distant avec le client VPN installé utilise le DNS pour trouver le bureau le plus proche de la région et se connecte au périphérique VPN qui y est installé. Avec le tunneling fractionné, le trafic vers Microsoft 365 optimiser les points de terminaison est envoyé directement à l’emplacement réseau Microsoft 365 le plus proche de la région. Tout autre trafic est envoyé via la connexion VPN au périphérique VPN.

## <a name="contosos-support-for-remote-and-onsite-work"></a>Prise en charge de contoso pour le travail à distance et sur site

Une fois que les modifications initiales ont été apportées pour prendre en charge principalement les employés distants pendant les verrouillages régionaux, Contoso a apporté des modifications d’infrastructure pour prendre en charge le travail à distance et sur site dans lequel un travailleur pourrait être :

- Toujours à distance.
- Toujours en local.
- Une combinaison de à distance et en local.

Les fonctionnalités d’identité, de sécurité et de conformité de Microsoft 365 sont conçues pour une approbation zéro et pour fonctionner indépendamment de l’emplacement de l’utilisateur et de son appareil. Pour plus d’informations, consultez la rubrique [Zero Trust](https://www.microsoft.com/security/business/zero-trust).

Toutefois, la gestion des nouvelles installations et des mises à jour logicielles dépend de l’emplacement de l’appareil, car le logiciel à installer peut provenir d’une source locale ou Internet. Les architectes informatiques de contoso ont conçu leurs nouvelles installations et mises à jour de l’infrastructure en fonction de l’emplacement de l’appareil, plutôt que du travail.

Ils ont désigné deux types d’appareils : local dédié et itinérance.

### <a name="dedicated-on-premises"></a>Local dédié

Un appareil local dédié est un ordinateur de bureau ou serveur qui ne quitte jamais l’intranet contoso et sur lequel un client VPN n’est pas installé. Ces appareils sur site continuent à utiliser le gestionnaire de configuration de point de terminaison Microsoft et ses points de distribution pour les installations et les mises à jour de Windows 10, les applications Microsoft 365 pour les entreprises et le navigateur Edge.

### <a name="roaming"></a>Itinérance

Un périphérique d’itinérance peut quitter l’intranet contoso et inclut des ordinateurs portables émis à de nombreux employés Office, ainsi qu’à tous les employés distants et autres appareils appartenant à une organisation, tels que des téléphones intelligents et des tablettes, sur lesquels le client VPN contoso est installé. 

Étant donné que ces appareils peuvent être connectés à Internet à tout moment, ils utilisent Intune ou d’autres services en nuage pour les installations et les mises à jour de Windows 10, Microsoft 365 apps pour les entreprises et Edge. Elles n’utilisent pas les points de distribution du gestionnaire de configuration local existants.

Cela signifie que certaines des installations et des mises à jour de l’appareil d’itinérance seront réalisées sur Internet alors qu’elles sont en local et connectées à l’intranet. Toutefois, les architectes informatiques de contoso ont décidé que la simplicité de configuration était plus importante que l’optimisation de la bande passante de l’intranet sur Internet, en particulier lorsque la plupart des travailleurs distants sont rarement connectés à l’intranet.

Voici l’infrastructure obtenue.

![L’infrastructure de contoso installe et met à jour l’infrastructure](../media/contoso-remote-onsite-work/contoso-updates-infrastructure.png)

Le comportement de l’installation et de la mise à jour est déterminé par le fait que les comptes d’ordinateur des appareils sont membres de l’un des groupes suivants :

- OnPremDevices

  Le client gestionnaire de configuration sur l’appareil utilise des points de distribution pour les installations et les mises à jour.

- RoamingDevices

  Intune et d’autres paramètres sur l’appareil spécifiez l’utilisation du réseau Microsoft 365 pour les installations et les mises à jour.

## <a name="new-onboarding-process"></a>Nouveau processus d’intégration

Pour un nouvel appareil local dédié publié sur un nouveau travailleur ou un nouveau serveur dans un centre de donnée, lorsque le travailleur se connecte, le client gestionnaire de configuration basé sur l’appartenance de l’appareil au groupe OnPremDevices télécharge et installe les dernières mises à jour pour Windows 10, les applications Microsoft 365 pour Enterprise et Edge à partir de points de distribution sur site du gestionnaire de configuration. Une fois terminé, l’appareil local dédié est prêt à être utilisé et utilise ces points de distribution pour les mises à jour continues.

Pour un nouveau périphérique distant émis vers un nouveau travailleur, lorsque le travailleur se connecte, l’appareil, en fonction de son appartenance au groupe RoamingDevices, contacte le service Cloud Intune et d’autres services, et télécharge et installe les dernières mises à jour pour Windows 10, les applications Microsoft 365 pour les entreprises et Edge. Une fois terminé, l’appareil distant est prêt à être utilisé et utilise le client VPN installé pour accéder aux ressources locales et au réseau Microsoft 365 pour les mises à jour continues.

## <a name="next-step"></a>Étape suivante

[Autorisez les travailleurs distants](empower-people-to-work-remotely.md) au sein de votre organisation.
