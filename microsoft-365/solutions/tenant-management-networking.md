---
title: Étape 2. Mise en réseau optimale pour votre Microsoft 365 pour les locataires d’entreprise
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Optimisez l’accès réseau à vos locataires Microsoft 365.
ms.openlocfilehash: 526330cb7f0cdf19ac3633988f60df259bde4206
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67731219"
---
# <a name="step-2-optimal-networking-for-your-microsoft-365-for-enterprise-tenants"></a>Étape 2. Mise en réseau optimale pour votre Microsoft 365 pour les locataires d’entreprise

Microsoft 365 entreprise inclut des applications de productivité cloud telles que Teams et Exchange Online, ainsi que des Microsoft Intune, ainsi que de nombreux services d’identité et de sécurité de Microsoft Azure. Tous ces services basés sur le cloud s’appuient sur la sécurité, les performances et la fiabilité des connexions à partir d’appareils clients sur votre réseau local ou sur n’importe quel emplacement sur Internet. 

Pour optimiser l’accès réseau pour votre locataire, vous devez :

- Optimisez le chemin d’accès entre vos utilisateurs locaux et l’emplacement le plus proche du réseau global Microsoft.
- Optimisez l’accès au Réseau mondial Microsoft pour vos utilisateurs distants qui utilisent une solution VPN d’accès à distance.
- Utilisez Network Insights pour concevoir le périmètre réseau de vos bureaux.
- Optimisez l’accès à des ressources spécifiques hébergées sur des sites SharePoint avec le CDN Office 365.
- Configurez les périphériques proxy et réseau pour contourner le traitement du trafic approuvé Microsoft 365 avec la liste des points de terminaison et automatiser la mise à jour de la liste à mesure que des modifications sont apportées.

## <a name="enterprise-on-premises-workers"></a>Travailleurs locaux d’entreprise

Pour les réseaux d’entreprise, vous devez optimiser l’expérience utilisateur final en activant l’accès réseau le plus performant entre les clients et les points de terminaison Microsoft 365 les plus proches. La qualité de l’expérience utilisateur final est directement liée aux performances et à la réactivité de l’application que l’utilisateur utilise. Par exemple, Microsoft Teams s’appuie sur une faible latence pour que les appels téléphoniques des utilisateurs, les conférences et les collaborations sur écran partagé soient sans problème.

L’objectif principal de la conception du réseau doit être de réduire la latence en réduisant le temps d’aller-retour (RTT) des appareils clients au Réseau mondial Microsoft, le réseau principal du réseau public de Microsoft qui interconnecte tous les centres de données de Microsoft avec une faible latence, des points d’entrée d’application cloud à haute disponibilité, appelés portes d’entrée, répartis dans le monde entier.

Voici un exemple de réseau d’entreprise traditionnel.

![Un réseau d’entreprise traditionnel avec un accès central à Internet.](../media/tenant-management-overview/tenant-management-networking-traditional.png)

Dans cette illustration, les succursales se connectent à un bureau central par le biais d’appareils de réseau étendu (WAN) et d’un réseau principal WAN. L’accès à Internet se fait par le biais d’un appareil de sécurité ou proxy à la périphérie réseau du bureau central et d’un fournisseur de services Internet (ISP). Sur Internet, microsoft Global Network dispose d’une série de portes d’entrée dans les régions du monde entier. Les organisations peuvent également utiliser des emplacements intermédiaires pour le traitement des paquets et la sécurité supplémentaire pour le trafic. Le locataire Microsoft 365 d’une organisation se trouve dans le réseau global Microsoft.

Les problèmes liés à cette configuration pour les services cloud Microsoft 365 sont les suivants :

- Pour les utilisateurs des succursales, le trafic est envoyé aux portes d’entrée non locales, ce qui augmente la latence.
- L’envoi de trafic vers des emplacements intermédiaires crée des épingles réseau qui effectuent le traitement des paquets en double sur le trafic approuvé, ce qui augmente la latence.
- Les périphériques réseau effectuent un traitement inutile et en double des paquets sur le trafic approuvé, ce qui augmente la latence.

L’optimisation des performances réseau de Microsoft 365 n’a pas besoin d’être compliquée. Vous pouvez obtenir les meilleures performances possibles en suivant quelques principes clés :

- Identifiez le trafic réseau Microsoft 365, qui est un trafic approuvé destiné aux services cloud Microsoft.
- Autorisez la sortie de branche locale du trafic réseau Microsoft 365 vers Internet à partir de chaque emplacement où les utilisateurs se connectent à Microsoft 365.
- Évitez les épingles réseau.
- Autorisez le trafic Microsoft 365 à contourner les proxys et les appareils d’inspection des paquets.

Si vous implémentez ces principes, vous obtenez un réseau d’entreprise optimisé pour Microsoft 365.

![Un réseau d’entreprise optimisé pour Microsoft 365.](../media/tenant-management-overview/tenant-management-networking-optimized.png)

Dans cette illustration, les succursales disposent de leur propre connexion Internet via un appareil SDWAN (software-defined WAN device), qui envoie le trafic Microsoft 365 approuvé vers la porte d’entrée la plus proche de la région. Au bureau central, le trafic Microsoft 365 approuvé contourne l’appareil de sécurité ou proxy et les appareils intermédiaires ne sont plus utilisés.

Voici comment la configuration optimisée résout les problèmes de latence d’un réseau d’entreprise traditionnel :

- Le trafic Microsoft 365 approuvé ignore le réseau principal du réseau étendu et est envoyé aux portes d’entrée locales pour tous les bureaux, ce qui réduit la latence.
- Les épingles réseau qui effectuent le traitement des paquets en double sont ignorées pour le trafic approuvé Microsoft 365, ce qui réduit la latence.
- Les périphériques réseau qui effectuent un traitement inutile et en double des paquets sont ignorés pour le trafic approuvé Microsoft 365, ce qui réduit la latence.

Pour plus d’informations, consultez la [vue d’ensemble de la connectivité réseau Microsoft 365](../enterprise/microsoft-365-networking-overview.md).

## <a name="remote-workers"></a>Travailleurs à distance

Si vos employés à distance utilisent un client VPN traditionnel pour obtenir l’accès à distance au réseau de votre organisation, vérifiez que le client VPN a une prise en charge de la segmentation de tunnel. Sans cette segmentation, l’ensemble de votre trafic de travail à distance est envoyé sur la connexion VPN, où il doit être transféré vers les appareils Microsoft Edge de votre organisation, être traité, puis envoyé sur Internet. Voici un exemple.

![Trafic réseau provenant de clients VPN sans tunneling.](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png)

Dans cette illustration, le trafic Microsoft 365 doit prendre un itinéraire indirect par le biais de votre organisation, qui peut être transféré vers une porte d’entrée microsoft Global Network loin de l’emplacement physique du client VPN. Ce chemin d’accès indirect ajoute de la latence au trafic réseau et réduit les performances globales. 

La segmentation de tunnel vous permet de configurer votre client VPN pour empêcher l’envoi de certains types de trafic sur la connexion VPN vers le réseau de l’organisation.

Pour optimiser l’accès aux ressources cloud de Microsoft 365, configurez vos clients VPN avec la segmentation de tunnel afin d’exclure le trafic vers la catégorie **Optimiser** des points de terminaison Microsoft 365 sur la connexion VPN. Pour plus d’informations, consultez [Office 365 catégories de points](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories) de terminaison et [les listes](../enterprise/microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) de points de terminaison de catégorie Optimize pour le tunneling fractionné.

Voici le flux de trafic résultant pour le tunneling fractionné, dans lequel la plupart du trafic vers les applications cloud Microsoft 365 contourne la connexion VPN.

![Trafic réseau provenant de clients VPN avec tunneling.](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png)

Dans cette illustration, le client VPN envoie et reçoit le trafic de service cloud Microsoft 365 essentiel directement via Internet et vers la porte d’entrée la plus proche dans microsoft global network.

Pour plus d’informations et de conseils, voir [Optimiser la connectivité d’Office 365 pour les utilisateurs à distance à l’aide de la segmentation de tunnel de VPN](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="using-network-insights-preview"></a>Utilisation de Network Insights (préversion)

Les insights réseau sont des métriques de performances collectées auprès de votre locataire Microsoft 365 qui vous aident à concevoir des périmètres réseau pour vos emplacements de bureau. Chaque insight fournit des détails en direct sur les caractéristiques de performances d’un problème spécifié pour chaque emplacement géographique où les utilisateurs locaux accèdent à votre locataire.

Il existe deux insights réseau au niveau du locataire qui peuvent être affichés pour le locataire :

- [Connexions échantillonnées Exchange affectées par des problèmes de connectivité](../enterprise/office-365-network-mac-perf-insights.md#exchange-sampled-connections-affected-by-connectivity-issues)
- [Connexions échantillonnées SharePoint affectées par des problèmes de connectivité](../enterprise/office-365-network-mac-perf-insights.md#sharepoint-sampled-connections-affected-by-connectivity-issues)

Voici les informations réseau spécifiques pour chaque emplacement de bureau :

- [Sortie réseau backhauled](../enterprise/office-365-network-mac-perf-insights.md#backhauled-network-egress)
- [Meilleures performances détectées pour les clients proches de chez vous](../enterprise/office-365-network-mac-perf-insights.md#better-performance-detected-for-customers-near-you)
- [Utilisation d’une porte d’entrée de service Exchange Online non optimale](../enterprise/office-365-network-mac-perf-insights.md#use-of-a-non-optimal-exchange-online-service-front-door)
- [Utilisation d’une porte d’entrée de service SharePoint Online non optimale](../enterprise/office-365-network-mac-perf-insights.md#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [Vitesse de téléchargement faible à partir de la porte d’entrée SharePoint](../enterprise/office-365-network-mac-perf-insights.md#low-download-speed-from-sharepoint-front-door)
- [Sortie réseau optimale de l’utilisateur chinois](../enterprise/office-365-network-mac-perf-insights.md#china-user-optimal-network-egress)

> [!IMPORTANT]
> Les insights réseau, les recommandations en matière de performances et les évaluations dans le Centre Administration Microsoft 365 sont actuellement en préversion. Il est uniquement disponible pour les locataires Microsoft 365 qui ont été inscrits dans le programme d’aperçu des fonctionnalités.

Pour plus d’informations, consultez [Microsoft 365 Network Insights](../enterprise/office-365-network-mac-perf-insights.md).

## <a name="sharepoint-performance-with-the-office-365-cdn"></a>Performances de SharePoint avec le CDN Office 365

Un réseau de distribution de contenu (CDN) basé sur le cloud vous permet de réduire les temps de chargement, d’économiser de la bande passante et d’accélérer la réactivité. Un CDN améliore les performances en mettant en cache des ressources statiques telles que des fichiers graphiques ou vidéo plus proches des navigateurs qui les demandent, ce qui permet d’accélérer les téléchargements et de réduire la latence. Vous pouvez utiliser le réseau de distribution de contenu (CDN) Office 365 intégré, inclus avec SharePoint dans Microsoft 365 E3 et E5, pour héberger des ressources statiques afin de fournir de meilleures performances pour vos pages SharePoint.

Le réseau de distribution de contenu Office 365 est composé de plusieurs réseaux de distribution de contenu qui vous permettent d’héberger des ressources statiques à différents emplacements (ou _origines_) et de les servir à partir de réseaux à haut débit mondiaux. Selon le type de contenu que vous souhaitez héberger dans le cdN Office 365, vous pouvez ajouter des origines **publiques**, des origines **privées** ou les deux.

Une fois déployé et configuré, le CDN Office 365 charge les ressources à partir d’origines publiques et privées et les rend disponibles pour un accès rapide aux utilisateurs situés sur Internet.

![Office 365 CDN déployé pour les utilisateurs.](../media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN déployé pour les utilisateurs")

Pour plus d’informations, consultez [Utiliser le CDN Office 365 avec SharePoint Online](../enterprise/use-microsoft-365-cdn-with-spo.md).

## <a name="automated-endpoint-listing"></a>Liste des points de terminaison automatisés

Pour que vos clients locaux, périphériques et services d’analyse de paquets basés sur le cloud ignorent le traitement du trafic Microsoft 365 approuvé, vous devez les configurer avec l’ensemble de points de terminaison (plages d’adresses IP et noms DNS) correspondant aux services Microsoft 365. Ces points de terminaison peuvent être configurés manuellement dans des pare-feu et d’autres périphériques de sécurité, des fichiers PAC pour les ordinateurs clients afin de contourner les proxys ou des appareils SD-WAN dans les filiales. Toutefois, les points de terminaison changent au fil du temps, ce qui nécessite une maintenance manuelle continue des listes de points de terminaison dans ces emplacements.

Pour automatiser la liste et la gestion des modifications pour les points de terminaison Microsoft 365 dans vos fichiers PAC clients et appareils réseau, utilisez le [service web rest basé sur l’adresse IP et l’URL Office 365](../enterprise/microsoft-365-ip-web-service.md). Ce service vous aide à mieux identifier et différencier le trafic réseau Microsoft 365, ce qui vous permet d’évaluer, de configurer et de rester à jour avec les dernières modifications.

Vous pouvez utiliser PowerShell, Python ou d’autres langages pour déterminer les modifications apportées aux points de terminaison au fil du temps et configurer vos fichiers PAC et périphériques réseau.

Le processus de base est le suivante :

1. Utilisez le service web d’adresse IP et d’URL Office 365 et le mécanisme de configuration de votre choix pour configurer vos fichiers PAC et appareils réseau avec l’ensemble actuel de points de terminaison Microsoft 365.
2. Exécutez une opération périodique quotidienne pour rechercher des modifications dans les points de terminaison ou utiliser une méthode de notification.
3. Lorsque des modifications sont détectées, régénérez et redistribuez le fichier PAC pour les ordinateurs clients et apportez les modifications à vos appareils réseau.

Pour plus d’informations, consultez [Office 365 service web d’adresse IP et d’URL](../enterprise/microsoft-365-ip-web-service.md).

## <a name="results-of-step-2"></a>Résultats de l’étape 2

Pour votre locataire Microsoft 365 avec une mise en réseau optimale, vous avez déterminé :

- Comment optimiser les performances réseau pour les utilisateurs locaux en ajoutant des connexions Internet à toutes les succursales et en éliminant les épingles réseau.
- Comment implémenter la liste automatisée des points de terminaison approuvés pour vos fichiers PAC basés sur le client et vos appareils et services réseau, y compris les mises à jour en cours (les plus adaptées aux réseaux d’entreprise).
- Comment prendre en charge l’accès des travailleurs distants aux ressources locales.
- Comment utiliser Network Insights
- Comment déployer le CDN Office 365.

Voici un exemple d’organisation d’entreprise et de son locataire avec une mise en réseau optimale.

![Exemple de locataire avec mise en réseau optimale.](../media/tenant-management-overview/tenant-management-tenant-build-step2.png)

[Voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/tenant-management-overview/tenant-management-tenant-build-step2.png)

Dans cette illustration, le locataire de cette organisation d’entreprise a :

- Accès Internet local pour chaque filiale avec un appareil SDWAN qui transfère le trafic Microsoft 365 approuvé vers une porte d’entrée locale.
- Pas d’épingles réseau.
- Appareils de sécurité du bureau central et périphériques proxy qui transfèrent le trafic approuvé Microsoft 365 vers une porte d’entrée locale.

## <a name="ongoing-maintenance-for-optimal-networking"></a>Maintenance continue pour une mise en réseau optimale

De façon continue, vous devrez peut-être :

- Mettez à jour vos périphériques et vos fichiers PAC déployés pour les modifications apportées aux points de terminaison ou vérifiez que votre processus automatisé fonctionne correctement.
- Gérez vos ressources dans le CDN Office 365.
- Mettez à jour la configuration du tunneling fractionné dans vos clients VPN pour les modifications apportées aux points de terminaison.

## <a name="next-step"></a>Étape suivante

[![Étape 3. Synchronisez vos identités et appliquez des connexions sécurisées.](../media/tenant-management-overview/tenant-management-step-grid-identity.png)](tenant-management-identity.md)

Continuez avec [l’identité](tenant-management-identity.md) pour synchroniser vos comptes et groupes locaux et appliquer des connexions utilisateur sécurisées.
