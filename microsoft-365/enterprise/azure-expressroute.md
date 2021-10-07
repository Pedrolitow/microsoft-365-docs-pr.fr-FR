---
title: Azure ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: ITPro
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
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Découvrez comment utiliser Azure ExpressRoute avec Office 365 et planifier le projet d’implémentation réseau si vous déployez avec lui.
ms.openlocfilehash: 9a4f4be76751ec03610bd766f51ec91526ca18a4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60198540"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute pour Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Découvrez comment Azure ExpressRoute est utilisé avec Office 365 et comment planifier le projet d’implémentation réseau qui sera requis si vous déployez Azure ExpressRoute pour une utilisation avec Office 365. Les services d’infrastructure et de plateforme s’exécutant dans Azure bénéficieront souvent de la prise en compte de l’architecture réseau et des considérations de performances. Dans ce cas, nous vous recommandons ExpressRoute pour Azure. Les offres de logiciels en tant que service telles que Office 365 et Dynamics 365 ont été conçues pour être accessibles en toute sécurité et de manière fiable via Internet. Vous pouvez en savoir plus sur les performances et la sécurité d’Internet et sur les cas où vous pouvez envisager Azure ExpressRoute pour Office 365 dans l’article Évaluer Office 365 [connectivité réseau.](assessing-network-connectivity.md)

> [!NOTE]
> Microsoft Defender pour point de terminaison ne fournit pas d’intégration avec Azure ExpressRoute. Bien que cela n’empêche pas les clients de définir des règles ExpressRoute qui activent la connectivité à partir d’un réseau privé vers Microsoft Defender pour les services cloud de point de terminaison, il est de la part du client de maintenir les règles à mesure que le service ou l’infrastructure cloud évolue.

> [!NOTE]
> Nous ne recommandons pas ExpressRoute pour Microsoft 365 car il ne fournit pas le meilleur modèle de connectivité pour le service dans la plupart des cas. En tant que tel, l’autorisation Microsoft est requise pour utiliser ce modèle de connectivité pour Microsoft 365. Nous examinerons chaque demande client et autoriser ExpressRoute pour Microsoft 365 uniquement dans les rares cas où cela est nécessaire. Veuillez lire le [guide ExpressRoute pour Microsoft 365](https://aka.ms/erguide) pour plus d’informations et après une révision complète du document avec vos équipes de productivité, de réseau et de sécurité, travaillez avec votre équipe de compte Microsoft pour soumettre une exception si nécessaire. Les abonnements non autorisés qui tentent de créer des filtres d’itinéraire pour Office 365 recevront un [message d’erreur.](https://support.microsoft.com/kb/3181709)

## <a name="planning-azure-expressroute-for-office-365"></a>Planification d’Azure ExpressRoute pour Office 365

Outre la connectivité Internet, vous pouvez choisir d’router un sous-ensemble de son trafic réseau Office 365 via une connexion directe offrant une prévisibilité et un SLA de disponibilité de 99,95 % pour les composants réseau Microsoft. Azure ExpressRoute vous fournit cette connexion réseau dédiée à Office 365 et d’autres services cloud De Microsoft.

Qu’il existe ou non un wan MPLS, ExpressRoute peut être ajouté à votre architecture réseau de trois manières : via un fournisseur de co-emplacement Exchange cloud pris en charge, un fournisseur de connexion point à point Ethernet ou un fournisseur de connexion MPLS. Découvrez les [fournisseurs disponibles dans votre région.](/azure/expressroute/expressroute-locations) La connexion ExpressRoute directe permettra la connectivité aux applications décrites dans les Office 365 services sont [inclus ?](azure-expressroute.md#BKMK_WhatDoIGet) ci-dessous. Le trafic réseau pour toutes les autres applications et services continuera à traverser Internet.

Considérez le diagramme réseau de haut niveau suivant, qui montre un client Office 365 classique se connectant aux centres de données microsoft via Internet pour accéder à toutes les applications Microsoft telles que Office 365, Windows Update et TechNet. Les clients utilisent un chemin d’accès réseau similaire, qu’ils se connectent à partir d’un réseau local ou d’une connexion Internet indépendante.

![Office 365 connectivité réseau.](../media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Regardez maintenant le diagramme mis à jour qui représente un client Office 365 qui utilise Internet et ExpressRoute pour se connecter à Office 365. Notez que certaines connexions, telles que le DNS public et les réseau de distribution de contenu, nécessitent toujours la connexion Internet publique. Notez également que les utilisateurs du client qui ne se trouvent pas dans leur bâtiment connecté ExpressRoute se connectent via Internet.

![Office 365 avec ExpressRoute.](../media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Vous souhaitez encore plus d’informations ? Découvrez comment gérer votre trafic réseau avec [Azure ExpressRoute](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) pour Office 365 et comment configurer [Azure ExpressRoute pour Office 365](/azure/expressroute/expressroute-faqs). Nous avons également enregistré une série de formation Azure ExpressRoute pour [Azure ExpressRoute](https://channel9.msdn.com/series/aer) en 10 Office 365 sur Channel 9 pour expliquer plus en profondeur les concepts.

## <a name="what-office-365-services-are-included"></a>Quels Office 365 services sont inclus ?
<a name="BKMK_WhatDoIGet"> </a>

Le tableau suivant répertorie les Office 365 services pris en charge sur ExpressRoute. Consultez [l’article Office 365 points](./urls-and-ip-address-ranges.md) de terminaison pour comprendre les demandes réseau pour ces applications qui nécessitent une connectivité Internet.

| Applications incluses |
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> Delve<sup>1</sup> <br/> |
|Skype Entreprise Online<sup>1</sup> <br/> Microsoft Teams <sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive Entreprise<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|Portail et partagé<sup>1</sup> <br/> Azure Active Directory (Azure AD) <sup>1</sup> <br/> Azure AD Connecter<sup>1</sup> <br/> Office<sup>1</sup> <br/> |

<sup>1 Chacune</sup> de ces applications présente des exigences de connectivité Internet non prise en charge sur ExpressRoute, consultez [l’article](./urls-and-ip-address-ranges.md) Office 365 points de terminaison pour plus d’informations.

Les services qui ne sont pas inclus avec ExpressRoute pour Office 365 sont les téléchargements du client Applications Microsoft 365 pour les grandes entreprises, la signature du fournisseur d’identité local et le service Office 365 (géré par 21 Vianet) en Chine.

## <a name="implementing-expressroute-for-office-365"></a>Implémentation d’ExpressRoute pour Office 365

L’implémentation d’ExpressRoute nécessite l’implication des propriétaires de réseau et d’applications et nécessite une planification minutieuse pour déterminer la nouvelle architecture de [routage](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)réseau, les besoins en bande passante, l’endroit où la sécurité sera implémentée, la haute disponibilité, etc. Pour implémenter ExpressRoute, vous devez :

1. Comprenez parfaitement le besoin qu’ExpressRoute satisfait dans votre planification Office 365 connectivité. Comprenez les applications qui utiliseront Internet ou ExpressRoute et planifiez entièrement vos besoins en capacité réseau, sécurité et haute disponibilité dans le contexte de l’utilisation d’Internet et d’ExpressRoute pour le trafic Office 365 réseau.

2. Déterminez les emplacements de sortie et d’homologue pour le trafic Internet et ExpressRoute<sup>1.</sup>

3. Déterminez la capacité requise sur internet et les connexions ExpressRoute.

4. Mettre en place un plan pour implémenter la sécurité et d’autres contrôles de périmètre standard<sup>1</sup>.

5. Avoir un compte Microsoft Azure valide pour vous abonner à ExpressRoute.

6. Sélectionnez un modèle de connectivité et un [fournisseur approuvé.](/azure/expressroute/expressroute-locations) Gardez à l’esprit que les clients peuvent sélectionner plusieurs modèles de connectivité ou partenaires et que le partenaire n’a pas besoin d’être identique à votre fournisseur de réseau existant.

7. Valider le déploiement avant de diriger le trafic vers ExpressRoute.

8. Éventuellement [implémenter QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) et évaluer l’expansion régionale.

<sup>1 Considérations</sup> importantes sur les performances. Les décisions prises ici peuvent avoir un impact considérable sur la latence, ce qui est essentiel pour les applications telles que Skype Entreprise.

Pour plus de références, utilisez [notre guide de routage](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) en plus de la [documentation ExpressRoute.](/azure/expressroute/expressroute-introduction)

Pour acheter ExpressRoute pour Office 365, vous devez travailler avec [](/azure/expressroute/expressroute-locations) un ou plusieurs fournisseurs approuvés pour mettre en service les circuits de taille et de nombre souhaités avec un abonnement ExpressRoute Premium. Il n’existe aucune licence supplémentaire à acheter auprès de Office 365.

Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/expressrouteoffice365]()

Vous êtes prêt à vous inscrire à [ExpressRoute pour Office 365](https://aka.ms/ert)?

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
