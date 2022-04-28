---
title: Microsoft 365 optique de connectivité
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Cet article contient des informations sur Microsoft 365 l’optique de connectivité.
ms.openlocfilehash: cda5fa074aa04be5fbbaff9b98360a3a2f927fc2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090316"
---
# <a name="microsoft-365-connectivity-optics"></a>Microsoft 365 optique de connectivité

Ce document décrit certaines des optiques de connectivité que Microsoft collecte généralement à partir des appareils clients, et décrit certaines des façons dont Microsoft utilise ces données pour analyser et optimiser la prestation de services, et pour évaluer et garantir la meilleure expérience possible pour l’utilisateur final.

Les optiques de connectivité sont généralement collectées à partir d’applications Microsoft, qui peuvent être installées sur des appareils de l’utilisateur final ou accessibles à partir de navigateurs. Contrairement à la collecte de données facultative dans Microsoft 365 services, la plupart des optiques de connectivité décrites ici font partie intégrante de la garantie que Microsoft respecte notre engagement en matière de disponibilité et de performances envers les clients. Ces optiques permettent à Microsoft de détecter et de répondre rapidement aux problèmes dans le chemin de connectivité entre les utilisateurs finaux et les points de terminaison de service Microsoft. Certaines de ces optiques sont également utilisées pour activer des fonctionnalités telles que [la connectivité réseau dans le centre Administration Microsoft 365](office-365-network-mac-perf-overview.md).

## <a name="optics-collected-from-microsoft-365-applications"></a>Optiques collectées à partir d’applications Microsoft 365

Les optiques sont actuellement collectées à l’aide d’un échantillonnage peu fréquent sur tous les appareils. En règle générale, l’ensemble spécifique d’optiques et de destinations (points de terminaison de service) qui doivent être mesurés dans une itération particulière sont configurés par Microsoft en fonction des exigences de service et aléatoires à des fins d’échantillonnage.
À chaque intervalle de collecte optique, une ou plusieurs des mesures suivantes peuvent être collectées à l’aide de l’appareil de l’utilisateur final comme source de mesure et d’un point de terminaison de service Microsoft 365 comme destination de mesure :

| Mesure | Description |
| --- | --- |
| Latence | Temps nécessaire pour récupérer un petit fichier via HTTP |
| Débit | Temps nécessaire pour récupérer un fichier plus volumineux via HTTP, mesuré rarement pour éviter une consommation excessive de bande passante |
| Durée des allers-retours (RTT) | Ping ICMP |
| Traceroute | IcMP traceroute |

Chaque mesure est généralement associée à des informations supplémentaires, qui peuvent inclure les éléments suivants :

| Élément | Description |
| --- | --- |
| ID client | Identificateur unique du locataire Azure Active Directory du client associé à l’appareil de l’utilisateur final. |
| ID du moniteur | Identificateur de l’application générant la requête (par exemple, Outlook, OneDrive, etc.), fournie par l’application cliente qui effectue la mesure. |
| ID de la demande | Identificateur de la demande de mesure, spécifié dans la configuration de mesure fournie par Microsoft. |
| Adresse IP distante | Adresse IP source masquée associée à la demande du point de terminaison client au point de terminaison de service, fournie par le serveur qui a reçu la demande de mesure et calculée en fonction de l’adresse IP source du client visible par Microsoft. Les adresses IP sont masquées dans un sous-réseau /24 pour les adresses IPv4 ou un sous-réseau /48 pour les adresses IPv6 afin de garantir que Microsoft ne peut pas identifier des appareils ou des utilisateurs individuels. |
| Serveur frontal | Microsoft 365 identificateur frontal de service, fourni par le serveur qui a reçu la demande de mesure. |
| Point de terminaison | Microsoft 365 emplacement du point de terminaison de service, fourni par le serveur qui a reçu la demande de mesure. |
| Certificat émis par | Propriété « certificat émis par » du certificat SSL présenté lors de la connexion au point de terminaison de service, qui indique l’autorité de certification qui a émis le certificat au point de terminaison de service. |
| Empreinte numérique du certificat | Propriété « empreinte numérique de certificat » du certificat SSL présenté lors de la connexion au point de terminaison de service, qui est un identificateur unique accessible publiquement du certificat. |
| Latitude/longitude | Latitude et longitude abstraites de l’appareil de l’utilisateur final. Cette opération est uniquement collectée pour les locataires qui ont activé Windows Service d’emplacement sur les appareils des utilisateurs finaux et qui ont également [activé la collecte de ces informations dans le portail d’administration Microsoft 365](office-365-network-mac-perf-overview.md#1-enable-windows-location-services). |

## <a name="measurement-process"></a>Processus de mesure

Chaque appareil de l’utilisateur final effectue généralement une mesure planifiée (pour les applications installées) ou basée sur l’action de chargement des pages de navigateur (pour les applications web). Les activités de mesure sont effectuées en tant qu’opérations en arrière-plan et n’ont pas d’impact sur l’expérience de l’application pour les utilisateurs. Étant donné que les types et destinations de mesure qui seront utilisés pour une itération particulière de ce processus sont aléatoires, les clients peuvent remarquer des demandes adressées à des points de terminaison de service Microsoft dans leur région qui sont similaires aux demandes classiques effectuées par les appareils de l’utilisateur final pour une connectivité d’application normale. En outre, les clients peuvent remarquer des demandes adressées à des points de terminaison de service Microsoft qui se trouvent bien en dehors de leur région locale. Ces mesures sont souvent utilisées pour garantir un routage optimal des demandes des clients vers le meilleur point de terminaison de service, car les modifications apportées à l’infrastructure du client et du fournisseur de services Internet peuvent obliger Microsoft à modifier nos stratégies de routage des demandes de manière continue. Découvrez comment Microsoft achemine le trafic vers le meilleur point de terminaison de service et comment optimiser la connectivité aux services Microsoft 365 dans la [vue d’ensemble de la connectivité réseau Microsoft 365](microsoft-365-networking-overview.md).

## <a name="service-endpoints"></a>Points de terminaison de service

Les points de terminaison de service Microsoft utilisés comme destinations pour ces mesures sont contenus dans les [URL Office 365 publiées et les plages d’adresses IP](urls-and-ip-address-ranges.md). L’accès à des points de terminaison de service supplémentaires n’est pas nécessaire pour la collecte de ces optiques de connectivité.
