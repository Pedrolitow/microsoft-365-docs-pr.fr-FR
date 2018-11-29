---
title: 'Étape 3 : Éviter les épingles de réseau'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/31/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Découvrez le fonctionnement des épingles de réseau et supprimez-les pour obtenir de meilleures performances.
ms.openlocfilehash: 7277b8f5c07bc156599f946e032c3345da3316e9
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867478"
---
# <a name="step-3-avoid-network-hairpins"></a>Étape 3 : Éviter les épingles de réseau

*Cette étape est requise et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/networking_icon-small.png)

Une [épingle de réseau](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#BKMK_P3) se produit lorsque le trafic vers une destination est d’abord dirigé vers un autre emplacement intermédiaire, comme une pile de sécurité locale, un courtier d’accès au cloud ou une passerelle web basée sur le cloud. Une épingle de réseau peut également se produire à cause d’un routage médiocre sur Internet dû à des fournisseurs de services réseau. Une épingle ajoute une latence et peut potentiellement rediriger le trafic vers un emplacement distant géographiquement.

Pour optimiser les performances pour le trafic vers les services basés sur le cloud de Microsoft 365, vérifiez si l’ISP qui fournit la connexion Internet locale a une relation d’homologation directe avec le réseau global de Microsoft à proximité immédiate de cet emplacement. Ces connexions n’ont pas d’épingles.

Si vous utilisez les services de sécurité ou de réseau basés sur le cloud pour votre trafic Microsoft 365, assurez-vous que l’effet des épingles est évalué et que leur impact sur les performances est compris. Examinez les éléments suivants :

- le nombre et les emplacements des fournisseurs de services par lesquels le trafic est transféré par rapport à vos succursales et points d’homologation du réseau global de Microsoft ; 
- la qualité de la relation d’homologation du réseau du fournisseur de services avec votre ISP et Microsoft ; 
- l’impact sur les performances de la transmission dans l’infrastructure du fournisseur de services.

Dès que possible, configurez vos routeurs périphériques pour envoyer le trafic Microsoft 365 approuvé directement, au lieu d’utiliser la transmission par proxy ou le tunneling via un cloud tiers ou un fournisseur de sécurité réseau basé sur le cloud qui traite votre trafic Internet. 

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](networking-exit-criteria.md#crit-networking-step3) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step4.png)|[Configurer le trafic de contournement](networking-configure-proxies-firewalls.md)|
