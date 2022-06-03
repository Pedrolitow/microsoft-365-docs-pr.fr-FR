---
title: Prise en charge D’ipv6 dans les services Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/02/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Résumé : Décrit le support IPv6 dans Microsoft 365 composants et dans Microsoft 365 offres gouvernementales.'
ms.openlocfilehash: 2619567e8dac6f4b87cba0108bcf105011c4a87c
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872739"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>Prise en charge D’ipv6 dans les services Microsoft 365

Avec l’adoption et la prise en charge croissantes d’IPv6 sur les réseaux d’entreprise, les fournisseurs de services et les appareils, de nombreux clients se demandent si leurs utilisateurs peuvent continuer à accéder à Microsoft 365 services à partir de clients IPv6 et de réseaux IPv6. Microsoft 365 services peuvent être utilisés avec succès à partir d’appareils IPv6 double pile et IPv6 uniquement. En fait, nous avons un nombre croissant de clients, des consommateurs aux grandes entreprises, qui s’orientent vers une plus grande adoption d’IPv6. Pour la plupart des clients, IPv4 ne disparaît pas complètement de leur paysage numérique. Nous ne prévoyons donc pas d’exiger IPv6 ou de dé-hiérarchiser IPv4 dans les fonctionnalités ou services Microsoft 365.

L’une de nos principales priorités avec Microsoft 365 est de garantir une expérience transparente des clients et des utilisateurs sur Internet à partir de n’importe quel emplacement, à partir de n’importe quel appareil. Cela inclut l’accès aux Microsoft 365 à partir d’appareils clients qui utilisent IPv6 dans la configuration à double pile, ainsi que la transition vers des déploiements clients IPv6 uniquement. Dans la plupart des cas, lorsque vous suivez un modèle Internet standard de connexion à Microsoft 365 comme décrit dans [Microsoft 365 principes de connectivité réseau](microsoft-365-network-connectivity-principles.md), [Microsoft 365 URL et plages d’adresses IP](urls-and-ip-address-ranges.md), et [Microsoft 365 meilleures pratiques de planification réseau](network-and-migration-planning.md#best-practices-for-network-planning-and-improving-migration-performance-for-office-365) , les transitions IPv6 ne perturberont pas votre expérience utilisateur.

De nombreux services Microsoft 365 offrent déjà une prise en charge IPv6 native aujourd’hui et sont accessibles directement à partir de clients IPv6 double pile et IPv6 uniquement. Microsoft 365 autorise également l’accès via des technologies de traduction IPv6 conventionnelles à IPv4 (telles que les proxys de base 64 ou DNS64/NAT64) couramment utilisées par les clients et les fournisseurs de solutions réseau pour se connecter aux ressources Internet IPv4.

Comme avec n’importe quel service SaaS et Internet dans son ensemble, l’étendue des interfaces, fonctionnalités et API Microsoft 365 activées en mode natif IPv6 s’étend en permanence et sans action directe du client ni contrôle. Si vous exécutez des services IPv6 ou IPv6 uniquement sur vos réseaux qui ont besoin d’accéder à Microsoft 365 et à Internet, il est recommandé d’inclure des mécanismes de transition dynamiques IPv6/IPv4 tels que DNS64/NAT64 pour garantir la connectivité IPv6 de bout en bout aux Microsoft 365 sans aucune reconfiguration de réseau supplémentaire.

La plupart des services Microsoft 365 ont été ou seront activés avec des fonctionnalités IPv6 complètement transparentes pour les utilisateurs finaux et les administrateurs informatiques. Certains scénarios Microsoft 365 (tels que les e-mails entrants anonymes) ont des exigences et des considérations spéciales à utiliser conjointement avec IPv6. Pour plus d’informations sur les exigences et considérations spécifiques à un scénario IPv6, contactez votre équipe de compte Microsoft ou le support Microsoft.

Voici un bref lien que vous pouvez utiliser pour revenir : [https://aka.ms/o365ip6](https://aka.ms/o365ip6)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la connectivité réseau Microsoft 365](microsoft-365-networking-overview.md)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

[Service web URL et adresses IP Office 365](microsoft-365-ip-web-service.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Planification réseau et optimisation des performances pour Microsoft 365](network-planning-and-performance.md)

[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)

[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)

[Réseaux de distribution de contenu](content-delivery-networks.md)

[Test de connectivité Microsoft 365](https://aka.ms/netonboard)

[Comment Microsoft construit son réseau mondial rapide et fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Blog sur la mise en réseau Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
