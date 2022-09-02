---
title: Azure ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/5/2019
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
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
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Découvrez comment utiliser Azure ExpressRoute avec Office 365 et planifier le projet d’implémentation réseau si vous déployez avec lui.
ms.openlocfilehash: ecaab47f3b7f5e5dcd203f6b8d2cdfb15143e182
ms.sourcegitcommit: 62368e5a48e569c8e475b07d194d7d8ff7d167ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67560700"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute pour Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Découvrez comment Azure ExpressRoute est utilisé avec Office 365 et comment planifier le projet d’implémentation réseau qui sera nécessaire si vous déployez Azure ExpressRoute pour une utilisation avec Office 365. Les services d’infrastructure et de plateforme s’exécutant dans Azure bénéficient souvent de l’analyse de l’architecture réseau et des considérations relatives aux performances. Dans ce cas, nous recommandons ExpressRoute pour Azure. Les offres de logiciels en tant que service telles que Office 365 et Dynamics 365 ont été conçues pour être accessibles de manière sécurisée et fiable via Internet. Vous pouvez en savoir plus sur les performances et la sécurité d’Internet, ainsi que sur le moment où vous pouvez envisager Azure ExpressRoute pour Office 365 dans l’article [Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md).

> [!NOTE]
> Microsoft Defender pour point de terminaison ne fournit pas d’intégration à Azure ExpressRoute. Bien que cela n’empêche pas les clients de définir des règles ExpressRoute qui permettent la connectivité d’un réseau privé à Microsoft Defender pour point de terminaison services cloud, il incombe au client de gérer les règles à mesure que le service ou l’infrastructure cloud évolue.

> [!NOTE]
> Nous ne recommandons pas ExpressRoute pour Microsoft 365, car il ne fournit pas le meilleur modèle de connectivité pour le service dans la plupart des cas. Par conséquent, l’autorisation Microsoft est nécessaire pour utiliser ce modèle de connectivité pour Microsoft 365. Nous passons en revue chaque demande du client et n’autorisons ExpressRoute pour Microsoft 365 que dans les rares scénarios où cela est nécessaire. Lisez le [guide ExpressRoute pour Microsoft 365 pour](https://aka.ms/erguide) plus d’informations et après une révision complète du document avec vos équipes de productivité, de réseau et de sécurité, collaborez avec votre équipe de compte Microsoft pour soumettre une exception si nécessaire. Les abonnements non autorisés qui tentent de créer des filtres de routage pour Office 365 recevront un [message d’erreur](https://support.microsoft.com/kb/3181709).

## <a name="planning-azure-expressroute-for-office-365"></a>Planification d’Azure ExpressRoute pour Office 365

En plus de la connectivité Internet, vous pouvez choisir d’acheminer un sous-ensemble de leur trafic réseau Office 365 via une connexion directe qui offre une prévisibilité et un contrat SLA de durée de fonctionnement de 99,95 % pour les composants réseau Microsoft. Azure ExpressRoute vous fournit cette connexion réseau dédiée à Office 365 et à d’autres services cloud Microsoft.

Que vous ayez ou non un wan MPLS existant, ExpressRoute peut être ajouté à votre architecture réseau de l’une des trois manières suivantes : par le biais d’un fournisseur de colocalisation Exchange cloud pris en charge, d’un fournisseur de connexions point à point Ethernet ou d’un fournisseur de connexions MPLS. Découvrez les [fournisseurs disponibles dans votre région](/azure/expressroute/expressroute-locations). La connexion ExpressRoute directe permet la connectivité aux applications décrites dans [Quels services Office 365 sont inclus ?](azure-expressroute.md#BKMK_WhatDoIGet) ci-dessous. Le trafic réseau pour toutes les autres applications et services continuera de traverser Internet.

Prenons le diagramme réseau de haut niveau suivant, qui montre un client Office 365 qui se connecte aux centres de données de Microsoft via Internet pour accéder à toutes les applications Microsoft telles que Office 365, Windows Update et TechNet. Les clients utilisent un chemin d’accès réseau similaire, qu’ils se connectent à partir d’un réseau local ou d’une connexion Internet indépendante.

![Office 365 connectivité réseau.](../media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Regardez maintenant le diagramme mis à jour, qui illustre un client Office 365 qui utilise à la fois Internet et ExpressRoute pour se connecter à Office 365. Notez que certaines connexions telles que le DNS public et les nœuds de réseau de distribution de contenu nécessitent toujours la connexion Internet publique. Notez également que les utilisateurs du client qui ne se trouvent pas dans leur bâtiment connecté ExpressRoute se connectent via Internet.

![Office 365 connectivité avec ExpressRoute.](../media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Vous voulez toujours plus d’informations ? Découvrez comment [gérer votre trafic réseau avec Azure ExpressRoute pour Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) et comment [configurer Azure ExpressRoute pour Office 365](/azure/expressroute/expressroute-faqs). Nous avons également enregistré une série de 10 parties [d’Azure ExpressRoute pour Office 365 Training](https://channel9.msdn.com/series/aer) sur Channel 9 afin d’expliquer plus en détail les concepts.

## <a name="what-office-365-services-are-included"></a>Quels services Office 365 sont inclus ?
<a name="BKMK_WhatDoIGet"> </a>

Le tableau suivant répertorie les services Office 365 pris en charge via ExpressRoute. Consultez [l’article Office 365 points de terminaison](./urls-and-ip-address-ranges.md) pour comprendre quelles demandes réseau pour ces applications nécessitent une connectivité Internet.

| Applications incluses |
|:-----|
|Exchange Online <sup>1</sup> <br/> Exchange Online Protection <sup>1</sup> <br/> Delve<sup>1</sup> <br/> |
|Skype Entreprise Online<sup>1</sup> <br/> Microsoft Teams <sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive Entreprise <sup>1</sup> <br/> Project Online <sup>1</sup> <br/> |
|Portail et partagé<sup>1</sup> <br/> Azure Active Directory (Azure AD) <sup>1</sup> <br/> Azure AD Connect<sup>1</sup> <br/> Office<sup>1</sup> <br/> |

<sup>1</sup> Chacune de ces applications a des exigences de connectivité Internet non prises en charge via ExpressRoute. Pour plus d’informations, consultez [l’article sur les points de terminaison Office 365](./urls-and-ip-address-ranges.md).

Les services qui ne sont pas inclus avec ExpressRoute pour Office 365 sont Applications Microsoft 365 pour les grandes entreprises téléchargements clients, la connexion au fournisseur d’identité local et le service Office 365 (géré par 21 Vianet) en Chine.

## <a name="implementing-expressroute-for-office-365"></a>Implémentation d’ExpressRoute pour Office 365

L’implémentation d’ExpressRoute nécessite la participation des propriétaires de réseau et d’application et nécessite une planification minutieuse pour déterminer la nouvelle [architecture de routage réseau](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), les exigences de bande passante, où la sécurité sera implémentée, la haute disponibilité, et ainsi de suite. Pour implémenter ExpressRoute, vous devez :

1. Comprenez pleinement le besoin satisfait par ExpressRoute dans votre planification de la connectivité Office 365. Découvrez quelles applications utiliseront Internet ou ExpressRoute et planifiez entièrement vos besoins en matière de capacité réseau, de sécurité et de haute disponibilité dans le contexte de l’utilisation d’Internet et d’ExpressRoute pour Office 365 trafic.

2. Déterminez les emplacements de sortie et de peering pour le trafic Internet et ExpressRoute<sup>1</sup>.

3. Déterminez la capacité requise sur les connexions Internet et ExpressRoute.

4. Disposer d’un plan pour l’implémentation de la sécurité et d’autres contrôles de périmètre standard<sup>1</sup>.

5. Disposez d’un compte Microsoft Azure valide pour vous abonner à ExpressRoute.

6. Sélectionnez un modèle de connectivité et un [fournisseur approuvé](/azure/expressroute/expressroute-locations). Gardez à l’esprit que les clients peuvent sélectionner plusieurs modèles de connectivité ou partenaires et que le partenaire n’a pas besoin d’être le même que votre fournisseur réseau existant.

7. Valider le déploiement avant de diriger le trafic vers ExpressRoute.

8. [Implémentez éventuellement QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) et évaluez l’expansion régionale.

<sup>1</sup> Considérations importantes sur les performances. Les décisions prises ici peuvent avoir un impact considérable sur la latence, ce qui est essentiel pour les applications telles que Skype Entreprise.

Pour obtenir des références supplémentaires, utilisez notre [guide de routage](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) en plus de la [documentation ExpressRoute](/azure/expressroute/expressroute-introduction).

Pour acheter ExpressRoute pour Office 365, vous devez travailler avec un ou plusieurs [fournisseurs approuvés](/azure/expressroute/expressroute-locations) pour approvisionner les circuits de nombre et de taille souhaités avec un abonnement ExpressRoute Premium. Il n’existe aucune licence supplémentaire à acheter auprès de Office 365.

Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/expressrouteoffice365]()

Vous êtes prêt à vous inscrire à [ExpressRoute pour Office 365](https://aka.ms/ert) ?

## <a name="related-topics"></a>Rubriques connexes

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)

[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)

[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)

[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)

[Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)

[Utilisation de communautés BGP dans ExpressRoute pour Office 365 scénarios](bgp-communities-in-expressroute.md)

[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)

[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)
