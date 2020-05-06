---
title: Étape 2. Fournir l’accès à distance aux applications et services locaux
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: laurawi
ms.date: 05/01/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Priority
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
ms.custom:
- M365solutions
description: Assurez-vous que vos employés à distance peuvent accéder aux ressources locales tout en optimisant l’accès aux services cloud de Microsoft 365.
ms.openlocfilehash: fb91451b52c55f2cad1e0efefe19a044ce1cc37b
ms.sourcegitcommit: 101084f9c81616342d78493232d8f13f5ffa4ddf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "44002647"
---
# <a name="step-2-provide-remote-access-to-on-premises-apps-and-services"></a>Étape 2. Fournir l’accès à distance aux applications et services locaux

Si votre organisation utilise une solution VPN d’accès à distance, généralement avec les serveurs VPN sur la périphérie de votre réseau et les clients VPN installés sur les appareils de vos utilisateurs, vos utilisateurs peuvent utiliser les connexions VPN d’accès à distance pour accéder aux applications et serveurs locaux. Mais vous devrez peut-être optimiser le trafic vers les services cloud de Microsoft 365.

Si vos utilisateurs n’utilisent pas de solution VPN, vous pouvez utiliser le proxy d’application Azure Active Directory (Azure AD) et le VPN Azure Point-to-Site (P2S) pour fournir un accès, si toutes vos applications sont basées sur le web.

Il existe trois configurations principales :

1. Vous utilisez déjà une solution VPN d’accès à distance.
2. Vous n’utilisez pas une solution VPN d’accès à distance, vous avez une identité hybride, et vous avez besoin d’un accès à distance uniquement pour les applications web locales.
3. Vous n’utilisez pas de solution VPN d’accès à distance et vous avez besoin d’accéder à des applications locales, dont certaines ne sont pas basées sur le web.

Avec les connexions d’accès à distance, vous pouvez également utiliser le [Bureau à distance](https://support.microsoft.com/help/4028379/windows-10-how-to-use-remote-desktop) pour connecter vos utilisateurs à un PC local. Par exemple, un employé distant peut utiliser le Bureau à distance pour se connecter au PC de son bureau à partir de son appareil Windows, iOS ou Android. Lorsqu’il est connecté à distance, il peut l’utiliser comme s’il était assis face à son PC.

## <a name="optimize-performance-for-remote-access-vpn-clients-to-microsoft-365-cloud-services"></a>Optimiser les performances des clients VPN d’accès à distance aux services cloud de Microsoft 365

Si vos employés à distance utilisent un client VPN traditionnel pour obtenir l’accès à distance au réseau de votre organisation, vérifiez que le client VPN a une prise en charge de la segmentation de tunnel.

Sans cette segmentation, l’ensemble de votre trafic de travail à distance est envoyé sur la connexion VPN, où il doit être transféré vers les appareils Microsoft Edge de votre organisation, être traité, puis envoyé sur Internet.

![Trafic réseau provenant de clients VPN sans segmentation de tunnel](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png)

Le trafic Microsoft 365 doit emprunter une route indirecte au sein de votre organisation, qui peut être transférée vers un point d’entrée réseau Microsoft éloigné loin de l’emplacement physique du client VPN. Ce chemin d’accès indirect ajoute de la latence au trafic réseau et réduit les performances globales. 

La segmentation de tunnel vous permet de configurer votre client VPN pour empêcher l’envoi de certains types de trafic sur la connexion VPN vers le réseau de l’organisation.

Pour optimiser l’accès aux ressources cloud de Microsoft 365, configurez vos clients VPN avec la segmentation de tunnel afin d’exclure le trafic vers la catégorie **Optimiser** des points de terminaison Microsoft 365 sur la connexion VPN. Pour plus d’informations, consultez [Catégories de points de terminaison Office 365](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#new-office-365-endpoint-categories). Consultez la liste des points de terminaison de catégorie Optimiser [ici](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges).

![Trafic réseau provenant de clients VPN avec segmentation de tunnel](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png)

Cela permet au client VPN d’envoyer et de recevoir du trafic de service cloud Microsoft 365 crucial directement via Internet et vers le point d’entrée le plus proche dans le réseau Microsoft.

Pour plus d’informations et de conseils, voir [Optimiser la connectivité d’Office 365 pour les utilisateurs à distance à l’aide de la segmentation de tunnel de VPN](https://docs.microsoft.com/office365/enterprise/office-365-vpn-split-tunnel).

## <a name="deploy-remote-access-when-all-your-apps-are-web-apps-and-you-have-hybrid-identity"></a>Déployer l’accès à distance lorsque toutes vos applications sont des applications web et que vous avez une identité hybride

Si vos employés distants n’utilisent pas de client VPN classique et que vos comptes d’utilisateurs et groupes locaux sont synchronisés avec Azure AD, vous pouvez utiliser le proxy d’application Azure AD pour fournir un accès à distance sécurisé pour les applications web hébergées sur les serveurs intranet. Les applications web incluent les sites SharePoint, les serveurs Outlook Web Access ou toute autre application métier basée sur le web. 

Voici les composants du proxy d’application Azure AD.

![Composants du proxy d’application Azure AD](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-application-proxy.png)

Si vous souhaitez en savoir plus, consultez la page [Présentation du proxy d’application Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

## <a name="deploy-remote-access-when-not-all-your-apps-are-web-apps"></a>Déployer l’accès à distance lorsque l’ensemble de vos applications ne sont pas des applications web

Si vos employés distants n’utilisent pas de client VPN classique et que l’une de vos applications n’est pas basée sur le web, vous pouvez utiliser un réseau privé virtuel (P2S) Azure.

Une connexion VPN P2S crée une connexion sécurisée entre un appareil de travail distant et le réseau de votre organisation via un réseau virtuel Azure. 

![Composants d’Azure P2S VPN](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-p2s-vpn.png)

Si vous souhaitez en savoir plus, consultez la page [Présentation de P2S VPN](https://docs.microsoft.com/azure/vpn-gateway/point-to-site-about).

## <a name="deploy-windows-virtual-desktop-to-provide-remote-access-for-remote-workers-using-personal-devices"></a>Déployer l’application de Windows Virtual Desktop pour fournir l’accès distant aux travailleurs à distance en utilisant des appareils personnels 

Pour prendre en charge les travailleurs distants qui peuvent uniquement utiliser leurs appareils personnels et non gérés, utilisez l’application de Windows Virtual Desktop dans Azure pour créer et attribuer des bureaux virtuels à vos utilisateurs pour qu’ils les utilisent à partir de leur domicile.

Les PC virtualisés peuvent agir comme des PC connectés au réseau de votre organisation.

Si vous souhaitez en savoir plus, consultez la page [Présentation de Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/overview).

## <a name="admin-technical-resources-for-remote-access"></a>Ressources techniques dédiées aux administrateurs pour l’accès à distance

- [Comment optimiser rapidement le trafic Office 365 pour les membres du personnel à distance et réduire la charge sur votre infrastructure](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571)
- [Optimiser la connectivité d’Office 365 pour les utilisateurs à distance à l’aide de la segmentation de tunnel VPN](https://docs.microsoft.com/office365/enterprise/office-365-vpn-split-tunnel)

## <a name="results-of-step-2"></a>Résultats de l’étape 2

Après le déploiement d’une solution d’accès à distance pour vos employés à distance :

| Configuration de l’accès à distance | Résultats |
|:-------|:-----|
| Une solution VPN d’accès à distance est en place | Vous avez configuré votre client VPN d’accès distant pour la segmentation de tunnel et pour la catégorie Optimiser des points de terminaison Microsoft 365. |
| Aucune solution VPN d’accès à distance et vous avez besoin d’un accès à distance uniquement pour les applications web locales | Vous avez configuré l’application proxy Azure. |
| Aucune solution VPN d’accès à distance et vous avez besoin d’accéder à des applications locales, dont certaines ne sont pas basées sur le web | Vous avez configuré Azure P2S VPN. |
| Les employés à distance utilisent leurs appareils personnels chez eux | Vous avez configuré Windows Virtual Desktop. |
|||

## <a name="next-step"></a>Étape suivante

Poursuivez avec l’[Étape 3](empower-people-to-work-remotely-manage-endpoints.md) pour gérer vos appareils, PC et autres points de terminaison.
