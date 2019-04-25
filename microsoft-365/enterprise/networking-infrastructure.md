---
title: 'Phase 1 : Infrastructure réseau pour Microsoft 365 Entreprise'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/31/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Les étapes de déploiement de l’infrastructure réseau pour Microsoft 365 Entreprise.
ms.openlocfilehash: 9b8c23d543eca97147801d70e42de7105266c52d
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32291181"
---
# <a name="phase-1-networking-infrastructure-for-microsoft-365-enterprise"></a>Phase 1 : Infrastructure réseau pour Microsoft 365 Entreprise

![](./media/deploy-foundation-infrastructure/networking_icon.png)

Microsoft 365 Entreprise inclut Office 365 et Microsoft Intune dans le cadre de la gestion d’entreprise + Security (EMS). Ces deux services cloud s’appuient sur la sécurité, les performances et la fiabilité des connexions à partir d’appareils clients via Internet ou des circuits dédiés. Pour héberger ces services et les rendre accessibles aux clients dans le monde entier, Microsoft a conçu une infrastructure réseau qui met en évidence les performances et l’intégration. 

Dans cette phase, vous découvrez les considérations clés pour la création d’une connexion performante aux services cloud de Microsoft 365 Entreprise. Pour une vue d’ensemble, consultez la rubrique relative aux [principes de la mise en réseau d’Office 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Getting-the-best-connectivity-and-performance-in-Office-365/ba-p/124694).

>[!Note]
>Si vous avez déjà déployé une infrastructure réseau, consultez les [critères de sortie](networking-exit-criteria.md) de cette phase pour vous assurer que vous répondez aux conditions requises et facultatives pour Microsoft 365 Entreprise.

## <a name="plan-and-deploy-your-microsoft-365-enterprise-networking-infrastructure"></a>Planifier et déployer votre infrastructure réseau de Microsoft 365 Entreprise 

Procédez comme suit pour déployer votre infrastructure réseau pour la configuration requise et les fonctionnalités de Microsoft 365 Entreprise.

|||
|:-------|:-----|
|![](./media/stepnumbers/Step1.png)|[Préparer le réseau de votre organisation pour Microsoft 365](networking-provide-bandwidth-cloud-services.md)|
|![](./media/stepnumbers/Step2.png)|[Configurer les connexions Internet locales pour chaque bureau](networking-dns-resolution-same-location.md)|
|![](./media/stepnumbers/Step3.png)|[Éviter les épingles de réseau](networking-avoid-network-hairpins.md)|
|![](./media/stepnumbers/Step4.png)|[Configurer le trafic de contournement](networking-configure-proxies-firewalls.md)|
|![](./media/stepnumbers/Step5.png)|[Optimisez les performances du service Office 365 et du client](networking-optimize-tcp-performance.md)|


Lorsque vous avez terminé ces étapes, accédez aux [critères de sortie](networking-exit-criteria.md) de cette phase pour vous assurer que vous répondez aux conditions requises et facultatives pour Microsoft 365 Entreprise.

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Jetez un œil aux coulisses de Microsoft et découvrez comment l’entreprise a mis en place et a amélioré le réseau Microsoft pour les services cloud Office 365 en lisant l’article relatif à l’[optimisation des performances réseau pour Microsoft Office 365](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).

## <a name="how-contoso-did-microsoft-365-enterprise"></a>Comment Contoso est-elle passée à Microsoft 365 Entreprise ?

Découvrez comment Contoso Corporation, une entreprise multinationale fictive mais représentative, [a optimisé son réseau](contoso-networking.md) pour les services cloud Microsoft 365.

![](./media/contoso-overview/contoso-icon.png)

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step1.png)|[Préparer le réseau de votre organisation pour Microsoft 365](networking-provide-bandwidth-cloud-services.md)|

