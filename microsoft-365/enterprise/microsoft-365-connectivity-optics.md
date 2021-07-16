---
title: Microsoft 365 Connectivity Optics
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
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
description: Cet article contient des informations sur Microsoft 365 Connectivity Optics.
ms.openlocfilehash: 952990a63d4ad064b2027c6f2364e8082342fa34
ms.sourcegitcommit: 2abc6bf9939b14a427647e88f319dbb70de49ca6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2021
ms.locfileid: "53455976"
---
# <a name="microsoft-365-connectivity-optics"></a>Microsoft 365 Connectivity Optics

Ce document décrit certaines des optiques de connectivité généralement collectées par Microsoft à partir d’appareils clients, et décrit certaines des façons dont Microsoft utilise ces données pour analyser et optimiser la distribution du service et pour évaluer et garantir la meilleure expérience possible pour l’utilisateur final.

Les optiques de connectivité sont généralement collectées à partir d’applications Microsoft, qui peuvent être installées sur des appareils d’utilisateur final ou accessibles à partir de navigateurs. Contrairement à la collecte de données facultative au sein des services Microsoft 365, la plupart des optiques de connectivité décrites ici font partie intégrante de la garantie que Microsoft répond à notre engagement en matière de disponibilité et de performances auprès des clients. Ces optiques permettent à Microsoft de détecter et de répondre rapidement aux problèmes de connectivité entre les utilisateurs finaux et les points de terminaison du service Microsoft. Certaines de ces optiques sont également utilisées pour activer des fonctionnalités telles que la connectivité réseau dans [le centre Administration Microsoft 365.](office-365-network-mac-perf-overview.md)

## <a name="optics-collected-from-microsoft-365-applications"></a>Optiques collectées à partir d Microsoft 365 applications

Les optiques sont actuellement collectées à l’aide d’échantillonnages peu fréquents sur tous les appareils. En règle générale, l’ensemble spécifique d’optiques et de destinations (points de terminaison de service) à mesurer dans une itération particulière est configuré par Microsoft en fonction des exigences de service et aléatoire à des fins d’échantillonnage.
À chaque intervalle de collecte d’optiques, une ou plusieurs des mesures suivantes peuvent être collectées à l’aide de l’appareil de l’utilisateur final comme source de mesure et d’un point de terminaison de service Microsoft 365 comme destination de mesure :

| Mesure | Description |
| --- | --- |
| Latence | Temps pris pour récupérer un petit fichier via HTTP |
| Débit | Temps nécessaire pour récupérer un fichier plus volumineux via HTTP, mesuré rarement pour éviter une consommation excessive de bande passante |
| Durée de l’aller-retour (RTT) | Ping ICMP |
| Traceroute | Traceroute ICMP |

Chaque mesure est généralement associée à des informations supplémentaires, qui peuvent inclure les éléments suivants :

| Élément | Description |
| --- | --- |
| ID client | Identificateur unique du client Azure Active Directory client associé à l’appareil de l’utilisateur final. |
| ID du moniteur | Identificateur de l’application générant la demande (par exemple, Outlook, OneDrive, etc.), fourni par l’application cliente qui effectue la mesure. |
| ID de demande | Identificateur de la demande de mesure, spécifié dans la configuration de mesure fournie par Microsoft. |
| ADRESSE IP distante | ADRESSE IP source masquée associée à la demande du client au point de terminaison de service, fournie par le serveur qui a reçu la demande de mesure et calculée en fonction de l’adresse IP source du client visible par Microsoft. Les adresses IP sont masquées dans un sous-réseau /24 pour les adresses IPv4 ou un sous-réseau /48 pour les adresses IPv6 pour s’assurer que Microsoft ne peut pas identifier des appareils ou des utilisateurs individuels. |
| Serveur frontal | Microsoft 365'identificateur frontal du service, fourni par le serveur qui a reçu la demande de mesure. |
| Point de terminaison | Microsoft 365 point de terminaison du service, fourni par le serveur qui a reçu la demande de mesure. |
| Certificat émis par | La propriété « certificat émis par » du certificat SSL présenté lors de la connexion au point de terminaison du service, qui indique l’autorité de certification qui a émis le certificat au point de terminaison du service. |
| Empreinte numérique de certificat | Propriété « empreinte de certificat » du certificat SSL présenté lors de la connexion au point de terminaison du service, qui est un identificateur unique accessible publiquement du certificat. |
| Latitude/Longitude | Latitude abstraite et longitude de l’appareil de l’utilisateur final. Il est collecté uniquement pour les clients qui ont activé Windows Location Service sur les appareils des utilisateurs finaux et qui ont également activé la collecte de ces informations dans le portail d’administration [Microsoft 365](office-365-network-mac-perf-overview.md#1-enable-windows-location-services). |

## <a name="measurement-process"></a>Processus de mesure

Chaque appareil de l’utilisateur final effectue généralement une mesure sur une base programmée (pour les applications installées) ou sur la base de l’action de chargement des pages du navigateur (pour les applications web). Les activités de mesure sont effectuées en tant qu’opérations en arrière-plan et n’ont pas d’impact sur l’expérience de l’application pour les utilisateurs. Comme les types de mesure et les destinations qui seront utilisés pour une itération particulière de ce processus sont aléatoires, les clients peuvent remarquer des demandes aux points de terminaison de service Microsoft dans leur région qui sont similaires aux demandes classiques effectuées par les appareils des utilisateurs finaux pour une connectivité d’application normale. En outre, les clients peuvent remarquer des demandes aux points de terminaison de service Microsoft qui se trouveraient bien en dehors de leur région locale. Ces mesures sont souvent utilisées pour assurer un routage optimal des demandes des clients vers le meilleur point de terminaison de service, car les modifications apportées au client et à l’infrastructure des fournisseurs de services Web peuvent obliger Microsoft à modifier régulièrement nos stratégies de routage des demandes. En savoir plus sur la façon dont Microsoft a route le trafic vers le meilleur point de terminaison de service et comment optimiser la connectivité aux services Microsoft 365 dans la vue d’ensemble Microsoft 365 connectivité [réseau.](microsoft-365-networking-overview.md)

## <a name="service-endpoints"></a>Points de terminaison de service

Les points de terminaison du service Microsoft utilisés comme destinations pour ces mesures sont contenus dans les URL et les plages d’adresses IP Office 365 [publiées.](urls-and-ip-address-ranges.md) L’accès à des points de terminaison de service supplémentaires n’est pas nécessaire pour la collecte de ces optiques de connectivité.
