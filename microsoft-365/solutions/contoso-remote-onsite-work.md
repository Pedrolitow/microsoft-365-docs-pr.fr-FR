---
title: Réponse contoso-19 et prise en charge du travail hybride
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre comment Contoso Corporation a répondu à la épidémie COVID-19 et conçu son infrastructure d’installation et de mise à jour logicielles pour le travail hybride.
ms.openlocfilehash: 06ce48969d35017da47be1e75ec3c374b9afb9a1
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58575443"
---
# <a name="contosos-covid-19-response-and-support-for-hybrid-work"></a>Réponse contoso-19 et prise en charge du travail hybride

Contoso avait toujours pris en charge ses employés à distance, qui accédaient aux ressources sur site via un serveur VPN central du siège social parisien. Contoso avait émis un ordinateur portable géré pour tous les travailleurs à distance. Les employés locaux avaient un mélange d’ordinateurs de bureau et d’ordinateurs portables.

## <a name="contosos-response-to-covid-19"></a>Réponse de Contoso à COVID-19

Avec l’apparition de la épidémie COVID-19, soudainement, tous les travailleurs essentiels, sauf les travailleurs à distance, étaient soudainement des travailleurs à distance. Contoso a répondu en déplaçant ses employés pour qu’ils travaillent de chez eux et mener leurs activités principales via l’accès à distance aux ressources locales et en ligne à l’aide de Microsoft 365 services cloud.

Contoso avait des serveurs VPN d’accès à distance dans le siège social parisien pour prendre en charge 25 % de ses employés déjà distants, mais a rapidement été déplacé pour faire monter en charge sa capacité d’accès à distance pour prendre en charge 90 % de ses employés. Contoso a déployé des serveurs VPN d’accès à distance dans chaque bureau satellite afin que les travailleurs à distance utilisent un point d’entrée de fermeture régionale pour accéder à l’intranet Contoso.

Contoso a également mis à jour la configuration des clients VPN installés sur des ordinateurs portables, des tablettes et des smartphones pour la tunnellation fractionnée afin que le trafic pour l’ensemble optimiser des points de terminaison Office 365 contourne la connexion VPN et a été envoyé directement sur Internet. Pour plus d’informations, voir Optimiser la Office 365 pour les utilisateurs distants à l’aide de [la tunneling fractionnement VPN.](../enterprise/microsoft-365-vpn-split-tunnel.md)

Voici la configuration qui en résulte avec les périphériques VPN installés au siège social parisien et dans chacun des succursales. 

![Infrastructure VPN de Contoso.](../media/contoso-remote-onsite-work/contoso-vpn-infrastructure.png)

Un travailleur à distance avec le client VPN installé utilise DNS pour rechercher le bureau le plus proche de la région et se connecte au périphérique VPN installé à cet emplacement. Avec la tunnellisation fractionnée, le trafic vers Microsoft 365 optimiser les points de terminaison est envoyé directement à l’emplacement Microsoft 365 réseau le plus proche. Tout autre trafic est envoyé sur la connexion VPN au périphérique VPN.

## <a name="contosos-support-for-hybrid-work"></a>Prise en charge de Contoso pour le travail hybride

Une fois que les modifications initiales ont été apportées pour prendre en charge la plupart des travailleurs à distance pendant les verrouillages régionaux, Contoso a apporté des modifications d’infrastructure pour prendre en charge le travail hybride dans lequel un travailleur pourrait être :

- Toujours distant.
- Toujours sur site.
- Combinaison de l’emplacement sur site et de la télécommande.

Microsoft 365 fonctionnalités d’identité, de sécurité et de conformité sont conçues pour la confiance zéro et fonctionnent quel que soit l’emplacement de l’utilisateur et de son appareil. Pour plus d’informations, voir [Confiance zéro](https://www.microsoft.com/security/business/zero-trust).

Toutefois, la gestion des nouvelles installations et des mises à jour logicielles dépend de l’emplacement de l’appareil, car le logiciel à installer peut être issu d’une source sur site ou Internet. Les architectes informatiques de Contoso ont conçu leur nouvelle infrastructure d’installation et de mise à jour en fonction de l’emplacement de l’appareil, plutôt que du travail.

Ils ont désigné deux types d’appareils : dédiés en local et itinérants.

### <a name="dedicated-on-premises"></a>Dédié en local

Un appareil local dédié est un ordinateur de bureau ou serveur qui ne quitte jamais l’intranet Contoso et n’a pas de client VPN installé. Ces appareils locaux continuent d’utiliser Microsoft Endpoint Configuration Manager et ses points de distribution pour les installations et les mises à jour de Windows 10, Applications Microsoft 365 pour les grandes entreprises et le navigateur Edge.

### <a name="roaming"></a>Itinérance

Un appareil itinérant peut quitter l’intranet contoso et inclut des ordinateurs portables émis par de nombreux employés du bureau et tous les travailleurs à distance et d’autres appareils dont l’organisation est propriétaire, tels que les smartphones et les tablettes, avec le client VPN Contoso installé. 

Étant donné que ces appareils peuvent être connectés à Internet à tout moment, ils utilisent Intune ou d’autres services informatiques pour installer et mettre à jour Windows 10, Applications Microsoft 365 pour les grandes entreprises et Edge. Ils n’utilisent pas les points de distribution Configuration Manager locaux existants.

Cela signifie que certaines des installations et mises à jour de l’appareil itinérant seront réalisées sur Internet pendant qu’ils sont locaux et connectés à l’intranet. Toutefois, les architectes de Contoso ont décidé que la simplicité de configuration était plus importante que l’optimisation de la bande passante intranet vers Internet, en particulier lorsque la plupart des travailleurs à distance sont rarement connectés à l’intranet.

Voici l’infrastructure qui en résulte.

![Infrastructure d’installation et de mise à jour de Contoso.](../media/contoso-remote-onsite-work/contoso-updates-infrastructure.png)

Le comportement d’installation et de mise à jour est déterminé en faisant des comptes d’ordinateur des appareils un membre de l’un de ces groupes :

- OnPremDevices

  Le client Configuration Manager sur l’appareil utilise des points de distribution pour les installations et les mises à jour.

- RoamingDevices

  Intune et d’autres paramètres sur l’appareil spécifient l’utilisation du réseau Microsoft 365 pour les installations et les mises à jour.

## <a name="new-onboarding-process"></a>Nouveau processus d’intégration

Pour un nouvel appareil local dédié émis à un nouvel employé ou à un nouveau serveur dans un centre de données, lorsque le travailleur se connecté, le client Configuration Manager basé sur l’appartenance de l’appareil au groupe OnPremDevices télécharge et installe les dernières mises à jour pour Windows 10, Applications Microsoft 365 pour les grandes entreprises et Edge à partir de points de distribution Configuration Manager locaux. Une fois terminé, l’appareil local dédié est prêt à être utilisé et utilise ces points de distribution pour les mises à jour en cours.

Pour un nouvel appareil distant émis à un nouvel employé, lorsque le travailleur se connecté, l’appareil, en fonction de son appartenance au groupe RoamingDevices, contacte le service cloud Intune et d’autres services, télécharge et installe les dernières mises à jour pour Windows 10, Applications Microsoft 365 pour les grandes entreprises et Edge. Une fois terminé, l’appareil distant est prêt à être utilisé et utilise le client VPN installé pour accéder aux ressources sur site et au réseau Microsoft 365 pour les mises à jour en cours.

## <a name="next-step"></a>Étape suivante

[Configurer votre infrastructure pour le travail hybride](empower-people-to-work-remotely.md) dans votre organisation.
