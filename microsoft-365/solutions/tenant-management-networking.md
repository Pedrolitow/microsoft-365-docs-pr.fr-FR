---
title: Étape 2. Mise en réseau optimale pour votre Microsoft 365 pour les locataires d’entreprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Optimisez l’accès réseau à vos Microsoft 365 client.
ms.openlocfilehash: cf9591d2ec027c42f5ef9e7abac6dc9b06744a81
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53229178"
---
# <a name="step-2-optimal-networking-for-your-microsoft-365-for-enterprise-tenants"></a>Étape 2. Mise en réseau optimale pour votre Microsoft 365 pour les locataires d’entreprise

Microsoft 365 entreprise inclut des applications de productivité cloud telles que Teams et Exchange Online et Microsoft Intune, ainsi que de nombreux services d’identité et de sécurité Microsoft Azure. Tous ces services basés sur le cloud reposent sur la sécurité, les performances et la fiabilité des connexions à partir d’appareils clients sur votre réseau local ou sur n’importe quel emplacement sur Internet. 

Pour optimiser l’accès réseau pour votre client, vous devez :

- Optimisez le chemin d’accès entre vos utilisateurs locaux et l’emplacement le plus proche du réseau global Microsoft.
- Optimisez l’accès au réseau global Microsoft pour vos utilisateurs distants qui utilisent une solution VPN d’accès à distance.
- Utilisez network Informations pour concevoir le périmètre réseau de vos bureaux.
- Optimisez l’accès à des ressources spécifiques hébergées sur SharePoint sites avec le Office 365 CDN.
- Configurez les périphériques de périphérie réseau et proxy pour contourner le traitement du trafic Microsoft 365 approuvé avec la liste des points de terminaison et automatisez la mise à jour de la liste au fil des modifications.

## <a name="enterprise-on-premises-workers"></a>Enterprise des employés locaux

Pour les réseaux d’entreprise, vous devez optimiser l’expérience utilisateur final en activant l’accès réseau le plus performant entre les clients et les points de terminaison Microsoft 365 les plus proches. La qualité de l’expérience de l’utilisateur final est directement liée aux performances et à la réactivité de l’application que l’utilisateur utilise. Par exemple, Microsoft Teams sur une faible latence afin que les appels téléphoniques des utilisateurs, les conférences et les collaborations à l’écran partagé soient sans problème.

L’objectif principal dans la conception du réseau doit être de réduire la latence en réduisant le temps d’aller-retour (RTT) entre les appareils clients et le réseau mondial Microsoft, la dorsale principale du réseau public de Microsoft qui interconnecte tous les centres de données Microsoft avec une faible latence et des points d’entrée d’application cloud haute disponibilité, appelés « portes d’entrée » dans le monde entier.

Voici un exemple de réseau d’entreprise traditionnel.

![Un réseau d’entreprise traditionnel avec un accès centralisé à Internet](../media/tenant-management-overview/tenant-management-networking-traditional.png)

Dans cette illustration, les succursales se connectent à un bureau central par le biais de périphériques de réseau large (WAN) et d’une dorsale de base du réseau wan. L’accès à Internet s’fait par le biais d’un périphérique de sécurité ou de proxy au niveau du périmètre réseau du siège social et d’un fournisseur de services Internet (ISP). Sur Internet, microsoft Global Network dispose d’une série de portes d’entrée dans des régions du monde entier. Les organisations peuvent également utiliser des emplacements intermédiaires pour le traitement de paquets supplémentaire et la sécurité du trafic. Le client Microsoft 365 d’une organisation se trouve dans le réseau global Microsoft.

Les problèmes liés à cette configuration pour les services Microsoft 365 cloud sont les Microsoft 365 :

- Pour les utilisateurs des succursales, le trafic est envoyé aux portes frontales non locales, ce qui augmente la latence.
- L’envoi de trafic vers des emplacements intermédiaires crée des épingles de réseau qui effectuent un traitement de paquets en double sur le trafic approuvé, ce qui augmente la latence.
- Les périphériques de périphérie réseau effectuent un traitement de paquets inutile et en double sur le trafic approuvé, ce qui augmente la latence.

L’optimisation Microsoft 365 performances réseau n’a pas besoin d’être compliquée. Vous pouvez obtenir les meilleures performances possibles en suivant quelques principes clés :

- Identifiez Microsoft 365 réseau, c’est-à-dire le trafic approuvé destiné aux services cloud de Microsoft.
- Autoriser la sortie de la succursale locale Microsoft 365 trafic réseau vers Internet à partir de chaque emplacement où les utilisateurs se connectent Microsoft 365.
- Évitez les épingles de réseau.
- Autorisez Microsoft 365 trafic à contourner les proxies et les périphériques d’inspection des paquets.

Si vous implémentez ces principes, vous obtenez un réseau d’entreprise optimisé pour Microsoft 365.

![Un réseau d’entreprise optimisé pour Microsoft 365](../media/tenant-management-overview/tenant-management-networking-optimized.png)

Dans cette illustration, les succursales ont leur propre connexion Internet via un périphérique wan (SDWAN) défini par logiciel, qui envoie le trafic Microsoft 365 approuvé vers la porte d’entrée la plus proche au niveau régional. Au siège social, le trafic Microsoft 365 de confiance contourne le périphérique de sécurité ou de proxy et les périphériques intermédiaires ne sont plus utilisés.

Voici comment la configuration optimisée résout les problèmes de latence d’un réseau d’entreprise traditionnel :

- Le Microsoft 365 approuvé ignore la dorsale dorsale principal du réseau wan et est envoyé aux portes d’entrée locales pour tous les bureaux, ce qui réduit la latence.
- Les épingles de réseau qui effectuent un traitement de paquets en double sont ignorées Microsoft 365 trafic approuvé, ce qui réduit la latence.
- Les périphériques de périphérie réseau qui effectuent un traitement de paquets inutile et en double sont ignorés pour Microsoft 365 trafic approuvé, ce qui réduit la latence.

Pour plus d’informations, [voir Microsoft 365 vue d’ensemble de la connectivité réseau.](../enterprise/microsoft-365-networking-overview.md)

## <a name="remote-workers"></a>Travailleurs à distance

Si vos employés à distance utilisent un client VPN traditionnel pour obtenir l’accès à distance au réseau de votre organisation, vérifiez que le client VPN a une prise en charge de la segmentation de tunnel. Sans cette segmentation, l’ensemble de votre trafic de travail à distance est envoyé sur la connexion VPN, où il doit être transféré vers les appareils Microsoft Edge de votre organisation, être traité, puis envoyé sur Internet. Voici un exemple.

![Trafic réseau provenant de clients VPN sans segmentation de tunnel](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png)

Dans cette illustration, le trafic Microsoft 365 doit prendre un itinéraire indirect par le biais de votre organisation, qui peut être transmis à une porte principale du réseau global Microsoft loin de l’emplacement physique du client VPN. Ce chemin d’accès indirect ajoute de la latence au trafic réseau et réduit les performances globales. 

La segmentation de tunnel vous permet de configurer votre client VPN pour empêcher l’envoi de certains types de trafic sur la connexion VPN vers le réseau de l’organisation.

Pour optimiser l’accès aux ressources cloud de Microsoft 365, configurez vos clients VPN avec la segmentation de tunnel afin d’exclure le trafic vers la catégorie **Optimiser** des points de terminaison Microsoft 365 sur la connexion VPN. Pour plus d’informations, voir Office 365 [](../enterprise/microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) [catégories](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories) de points de terminaison et les listes des points de terminaison de catégorie Optimiser pour la tunnellation fractionner.

Voici le flux de trafic résultant pour le tunneling fractionné, dans lequel la plupart du trafic vers Microsoft 365 applications cloud contournent la connexion VPN.

![Trafic réseau provenant de clients VPN avec segmentation de tunnel](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png)

Dans cette illustration, le client VPN envoie et reçoit un trafic de service cloud Microsoft 365 essentiel directement via Internet et vers la porte d’accès la plus proche dans le réseau global Microsoft.

Pour plus d’informations et de conseils, voir [Optimiser la connectivité d’Office 365 pour les utilisateurs à distance à l’aide de la segmentation de tunnel de VPN](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="using-network-insights-preview"></a>Utilisation de la Informations réseau (prévisualisation)

Les informations réseau sont des mesures de performances collectées à partir de votre client Microsoft 365 qui vous aident à concevoir des périmètres réseau pour vos emplacements de bureau. Chaque insight fournit des détails en direct sur les caractéristiques de performances d’un problème spécifié pour chaque emplacement géographique où les utilisateurs locaux accèdent à votre client.

Il existe deux informations réseau au niveau du client qui peuvent être affichées pour le client :

- [Exchange exemples de connexions touchés par des problèmes de connectivité](../enterprise/office-365-network-mac-perf-insights.md#exchange-sampled-connections-impacted-by-connectivity-issues)
- [SharePoint exemples de connexions touchés par des problèmes de connectivité](../enterprise/office-365-network-mac-perf-insights.md#sharepoint-sampled-connections-impacted-by-connectivity-issues)

Voici les informations réseau spécifiques pour chaque emplacement de bureau :

- [Sortie réseau backhauled](../enterprise/office-365-network-mac-perf-insights.md#backhauled-network-egress)
- [Meilleures performances détectées pour les clients proches de chez vous](../enterprise/office-365-network-mac-perf-insights.md#better-performance-detected-for-customers-near-you)
- [Utilisation d’une porte d’Exchange Online service non optimale](../enterprise/office-365-network-mac-perf-insights.md#use-of-a-non-optimal-exchange-online-service-front-door)
- [Utilisation d’une porte d’entrée du service SharePoint Online non optimale](../enterprise/office-365-network-mac-perf-insights.md#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [Faible vitesse de téléchargement à partir SharePoint première ligne](../enterprise/office-365-network-mac-perf-insights.md#low-download-speed-from-sharepoint-front-door)
- [Sortie réseau optimale de l’utilisateur chinois](../enterprise/office-365-network-mac-perf-insights.md#china-user-optimal-network-egress)

> [!IMPORTANT]
> Les informations réseau, les recommandations en matière de performances et les évaluations dans le centre Administration Microsoft 365 sont actuellement en état d’aperçu. Il est uniquement disponible pour les Microsoft 365 qui ont été inscrits au programme d’aperçu des fonctionnalités.

Pour plus d’informations, [voir Microsoft 365 Network Informations](../enterprise/office-365-network-mac-perf-insights.md).

## <a name="sharepoint-performance-with-the-office-365-cdn"></a>SharePoint performances avec le Office 365 CDN

Un système informatique réseau de distribution de contenu (CDN) vous permet de réduire les temps de chargement, d’économiser de la bande passante et de accélérer la réactivité. Une CDN améliore les performances en achant des ressources statiques telles que des fichiers graphiques ou vidéo plus proches des navigateurs qui les demandent, ce qui permet d’accélérer les téléchargements et de réduire la latence. Vous pouvez utiliser le Office 365 réseau de distribution de contenu intégré (CDN), inclus avec SharePoint dans Microsoft 365 E3 et E5, pour héberger des ressources statiques afin de fournir de meilleures performances à vos pages SharePoint.

Le réseau de distribution de contenu Office 365 est composé de plusieurs réseaux de distribution de contenu qui vous permettent d’héberger des ressources statiques à différents emplacements (ou _origines_) et de les servir à partir de réseaux à haut débit mondiaux. Selon le type de contenu que vous souhaitez héberger  dans le Office 365 CDN, vous pouvez ajouter des origines publiques,  des origines privées ou les deux.

Lorsqu’elle est déployée et configurée, la Office 365 CDN charge les ressources à partir d’origines publiques et privées et les rend disponibles pour un accès rapide aux utilisateurs situés sur Internet.

![Office 365 CDN pour les utilisateurs](../media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN pour les utilisateurs")

Pour plus d’informations, [voir Utiliser la Office 365 CDN avec SharePoint Online.](../enterprise/use-microsoft-365-cdn-with-spo.md)

## <a name="automated-endpoint-listing"></a>Liste automatisée des points de terminaison

Pour que vos clients locaux, périphériques Edge et services d’analyse de paquets basés sur le cloud ignorent le traitement du trafic Microsoft 365 approuvé, vous devez les configurer avec l’ensemble de points de terminaison (plages d’adresses IP et noms DNS) correspondant aux services Microsoft 365. Ces points de terminaison peuvent être configurés manuellement dans les pare-feux et autres périphériques de sécurité Edge, les fichiers PAC pour les ordinateurs clients afin de contourner les proxies ou les périphériques SD-WAN des succursales. Toutefois, les points de terminaison changent au fil du temps, nécessitant une maintenance manuelle continue des listes de points de terminaison à ces emplacements.

Pour automatiser la gestion des listes et des changements pour les points de terminaison Microsoft 365 dans vos fichiers PAC clients et périphériques réseau, utilisez l’adresse IP Office 365 et le [service web REST d’URL.](../enterprise/microsoft-365-ip-web-service.md) Ce service vous permet d’identifier et de différencier Microsoft 365 trafic réseau, ce qui vous permet d’évaluer, de configurer et de rester à jour plus facilement avec les dernières modifications.

Vous pouvez utiliser PowerShell, Python ou d’autres langages pour déterminer les modifications apportées aux points de terminaison au fil du temps et configurer vos fichiers PAC et périphériques réseau edge.

Le processus de base est :

1. Utilisez le service web Office 365 d’URL et d’adresse IP et le mécanisme de configuration de votre choix pour configurer vos fichiers PAC et périphériques réseau avec l’ensemble actuel Microsoft 365 points de terminaison.
2. Exécutez une activité périodique quotidienne pour vérifier les modifications apportées aux points de terminaison ou utilisez une méthode de notification.
3. Lorsque des modifications sont détectées, régénérez et redistribuez le fichier PAC pour les ordinateurs clients et a apporter les modifications à vos périphériques réseau.

Pour plus d’informations, [voir Office 365'adresse IP et le service web d’URL.](../enterprise/microsoft-365-ip-web-service.md)

## <a name="results-of-step-2"></a>Résultats de l’étape 2

Pour votre client Microsoft 365 avec une mise en réseau optimale, vous avez déterminé :

- Comment optimiser les performances du réseau pour les utilisateurs locaux en ajoutant des connexions Internet à tous les succursales et en éliminant les épingles de réseau.
- Comment implémenter la liste des points de terminaison fiables automatisés pour vos fichiers PAC basés sur le client et vos périphériques et services réseau, y compris les mises à jour en cours (les plus adaptées aux réseaux d’entreprise).
- Comment prendre en charge l’accès des travailleurs à distance aux ressources sur site.
- Utilisation des réseaux Informations
- Comment déployer le Office 365 CDN.

Voici un exemple d’organisation d’entreprise et de son client avec une mise en réseau optimale.

![Exemple de client avec une mise en réseau optimale](../media/tenant-management-overview/tenant-management-tenant-build-step2.png)

[Voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/tenant-management-overview/tenant-management-tenant-build-step2.png)

Dans cette illustration, le client de cette organisation d’entreprise a :

- Accès Internet local pour chaque succursale avec un appareil SDWAN qui Microsoft 365 trafic vers une porte d’entrée locale.
- Aucune épingle de réseau.
- Les périphériques de sécurité et de proxy du siège social qui Microsoft 365 le trafic approuvé vers une porte d’entrée locale.

## <a name="ongoing-maintenance-for-optimal-networking"></a>Maintenance continue pour une mise en réseau optimale

Régulièrement, vous devrez peut-être :

- Mettez à jour vos périphériques Edge et les fichiers PAC déployés pour les modifications apportées aux points de terminaison ou vérifiez que votre processus automatisé fonctionne correctement.
- Gérez vos ressources dans le Office 365 CDN.
- Mettez à jour la configuration de tunneling fractionnel dans vos clients VPN pour les modifications apportées aux points de terminaison.

## <a name="next-step"></a>Étape suivante

[![Étape 3. Synchroniser vos identités et appliquer des sign-ins sécurisées](../media/tenant-management-overview/tenant-management-step-grid-identity.png)](tenant-management-identity.md)

Continuez [avec l’identité](tenant-management-identity.md) pour synchroniser vos comptes et groupes locaux et appliquer des connecteurs utilisateur sécurisés.
