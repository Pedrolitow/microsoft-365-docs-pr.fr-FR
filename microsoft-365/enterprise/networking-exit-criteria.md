---
title: 'Phase 1 : Critères de sortie de l’infrastructure réseau'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/05/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Assurez-vous que votre configuration répond aux critères de Microsoft 365 Entreprise pour l’infrastructure réseau.
ms.openlocfilehash: 9d818a97e79465d639c52f96901bd1cbaa31144a
ms.sourcegitcommit: 91ff1d4339f0f043c2b43997d87d84677c79e279
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "36982775"
---
# <a name="phase-1-networking-infrastructure-exit-criteria"></a>Phase 1 : Critères de sortie de l’infrastructure réseau

![](./media/deploy-foundation-infrastructure/networking_icon-small.png)

Vérifiez que votre infrastructure réseau répond aux critères requis suivants et que vous avez pris en considération les critères facultatifs.

<a name="crit-networking-step1"></a>
## <a name="required-your-network-is-ready-for-microsoft-365-enterprise"></a>Obligatoire : votre réseau est prêt pour Microsoft 365 Entreprise

- Vos bureaux disposent d’une bande passante Internet adéquate pour le trafic Microsoft 365, y compris pour l’installation et les mises à jour d’Office 365, de Microsoft Intune et de Windows 10 Entreprise
- Votre réseau global est conforme à l’[architecture de référence Office 365](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#BKMK_P2)
- Les modifications de votre réseau ont été testées et répondent aux exigences en matière de latence du trafic 

Si nécessaire, l’[Étape 1](networking-provide-bandwidth-cloud-services.md) peut vous aider à répondre à cette exigence.

<a name="crit-networking-step2"></a>
## <a name="required-your-local-offices-have-local-internet-connections-and-name-resolution"></a>Obligatoire : vos bureaux locaux ont une résolution de noms et des connexions Internet locales

Vous avez configuré chaque bureau local avec un accès Internet via un fournisseur de services Internet local dont des serveurs DNS utilisent une adresse IP publique locale qui identifie leur emplacement sur Internet. Ainsi, les meilleures performances possibles pour les utilisateurs qui accèdent à Office 365 et Intune sont garanties.

Si vous n’utilisez pas de fournisseur de services Internet local pour chaque filiale, les performances peuvent en pâtir car le trafic réseau doit parcourir la structure fondamentale d’une organisation ou des requêtes de données sont prises en charge par des serveurs frontaux à distance.

### <a name="how-to-test"></a>Comment effectuer les tests
Utilisez un outil ou site web sur un appareil dans ce bureau pour déterminer l’adresse IP publique utilisée par le serveur proxy. Par exemple, utilisez la page web [What Is My IP Address](https://www.whatismypublicip.com/). Cette adresse IP publique attribuée par votre fournisseur de services Internet doit être géographiquement locale. Elle ne doit pas être issue d’une plage d’adresses IP publiques pour un bureau local ou d’un fournisseur de sécurité réseau basé sur le cloud.

Si nécessaire, l’[Étape 2](networking-dns-resolution-same-location.md) peut vous aider à répondre à cette exigence.

<a name="crit-networking-step3"></a>
## <a name="optional-unneeded-network-hairpins-are-removed"></a>Facultatif : les épingles de réseau inutiles sont supprimées

Vous avez examiné vos épingles de réseau et avez identifié leur impact sur les performances pour tous vos bureaux. Vous avez supprimé les épingles de réseau lorsque cela était possible ou avez travaillé avec votre fournisseur de réseau ou de sécurité tiers pour implémenter une homologation Microsoft 365 optimale pour leur réseau.

Si nécessaire, l’[Étape 3](networking-avoid-network-hairpins.md) peut vous aider avec cette option.


<a name="crit-networking-step4"></a>
## <a name="optional-you-have-configured-traffic-bypass-on-your-internet-browsers-and-edge-devices"></a>Facultatif : vous avez configuré le trafic de contournement sur vos navigateurs Internet et équipements de périmètre

Vous avez déployé les derniers fichiers PAC sur vos navigateurs Internet locaux afin que le trafic vers des noms de domaine DNS Microsoft 365 contournent les serveurs proxy.

Vous avez configuré vos équipements de périmètre réseau (les pare-feu, SSL Break and Inspect et autres appareils d’inspection de paquets) de façon à ce qu’ils utilisent le trafic de contournement ou qu’ils traitent le trafic au minimum pour les catégories Optimiser et Autoriser des points de terminaison Microsoft 365.


### <a name="how-to-test"></a>Procédure de test

Utilisez les outils de journalisation sur vos appareils de périmètre réseau pour vous assurer que le trafic vers les destinations Microsoft 365 n’est pas en cours d’inspection, de déchiffrement ou altéré d’une autre façon.

Si nécessaire, l’[Étape 4](networking-configure-proxies-firewalls.md) peut vous aider avec cette option.


<a name="crit-networking-step5"></a>
## <a name="optional-your-clients-and-office-365-applications-are-configured-for-optimal-performance"></a>Facultatif : vos applications Office 365 et clients sont configurés pour des performances optimales

Vous avez optimisé les paramètres TCP sur vos appareils client et pour les services Exchange Online, Skype Entreprise Online, SharePoint Online et Project Online.

Si nécessaire, l’[Étape 5](networking-optimize-tcp-performance.md) peut vous aider avec cette option.

## <a name="results-and-next-steps"></a>Résultats et étapes suivantes

Les utilisateurs de votre intranet sont désormais prêts à utiliser les services de cloud computing de Microsoft 365 via un chemin de mise en réseau efficace vers et sur Internet.

|||
|:-------|:-----|
|![](./media/deploy-foundation-infrastructure/identity_icon-small.png)| Si vous suivez les phases de déploiement de bout en bout de Microsoft 365 Entreprise, la prochaine phase est l’[identité](identity-infrastructure.md). |
