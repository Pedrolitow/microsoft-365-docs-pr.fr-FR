---
title: 'Présentation : la segmentation de tunnel VPN avec Office 365'
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/22/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
- m365initiative-coredeploy
f1.keywords:
- NOCSH
description: Instructions d’utilisation de la segmentation de tunnel VPN avec Office 365 afin d’optimiser la connectivité d’Office 365 pour les utilisateurs distants.
ms.openlocfilehash: dc9e9fa6b730ac6a98879c692f349b2480d3dcf14320c7817d5d5b14eb6ac825
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53848906"
---
# <a name="optimize-office-365-connectivity-for-remote-users-using-vpn-split-tunneling"></a>Optimiser la connectivité d’Office 365 pour les utilisateurs à distance à l’aide de la segmentation de tunnel VPN
<!---
>[!NOTE]
>This topic is part of a set of topics that address Office 365 optimization for remote users.
>- For VPN split tunnel implementation guidance, see [Implementing VPN split tunneling for Office 365](microsoft-365-vpn-implement-split-tunnel.md).
>- For information about optimizing Office 365 worldwide tenant performance for users in China, see [Office 365 performance optimization for China users](microsoft-365-networking-china.md).
-->

Pour les clients qui connectent leurs appareils de travail à distance au réseau d’entreprise ou à l’infrastructure cloud sur VPN, Microsoft recommande que les scénarios de Office 365 clés **Microsoft Teams,** **SharePoint Online** et **Exchange Online** soient acheminés sur une configuration de tunnel partagé _VPN._ Cela devient particulièrement important comme stratégie de première ligne pour faciliter la productivité continue des employés lors d’événements de travail à domicile à grande échelle tels que la crise du COVID-19.

![Configuration de la segmentation de tunnel par VPN](../media/vpn-split-tunneling/vpn-model-2.png)

_Image 1 : Une solution de segmentation de tunnel VPN avec des exceptions Office 365 définies, envoyées directement au service. Tout autre trafic traverse le tunnel VPN, indépendamment de la destination._

L’essentiel de cette approche consiste à offrir une méthode simple, permettant aux entreprises de limiter les risques liés à la saturation de l’infrastructure VPN et d’améliorer considérablement les performances d’Office 365 le plus rapidement possible. La configuration des clients VPN pour permettre au trafic Office 365 le plus important et le plus intense de contourner le tunnel VPN offre les avantages suivants :

- Atténue immédiatement la cause principale de la majorité des problèmes de performances et de capacité réseau, signalés par les clients dans les architectures VPN d'entreprise, ayant un impact sur l'expérience utilisateur Office 365
  
  La solution recommandée cible spécifiquement les points de terminaison du service Office 365 classés dans la catégorie **Optimiser** dans l’article [URL et plages d'adresses IP Office 365](./urls-and-ip-address-ranges.md). Le trafic vers ces points de terminaison est hautement sensible à la latence et à la limitation de la bande passante, et son activation pour contourner le tunnel VPN peut considérablement améliorer l’expérience utilisateur final et réduire la charge du réseau d’entreprise. Les connexions Office 365 qui ne constituent pas la majorité de la bande passante ou de l'empreinte de l'expérience utilisateur peuvent continuer à être acheminées via le tunnel VPN avec le reste du trafic lié à Internet. Si vous souhaitez en savoir plus, consultez l’article [la stratégie de segmentation de tunnel VPN](#the-vpn-split-tunnel-strategy).

- Peuvent être configurés, testés et implémentés rapidement par les clients et sans configuration d’infrastructure ou d’application supplémentaire.

  En fonction de la plateforme VPN et de l’architecture réseau, l’implémentation peut prendre quelques heures. Si vous souhaitez en savoir plus, consultez l’article [Implémenter la segmentation de tunnel VPN](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling).

- Préserve la posture de sécurité des implémentations VPN client en ne modifiant pas la façon dont les autres connexions sont acheminées, notamment le trafic vers Internet

  La configuration recommandée respecte les principes de **moindre privilège** pour les exceptions de trafic VPN et permet aux clients d’implémenter une segmentation de tunnel VPN sans exposer les utilisateurs ou l’infrastructure à des risques de sécurité supplémentaires. Le trafic réseau acheminé directement vers les points de terminaison Office 365 est chiffré, validé pour l’intégrité par les piles d’applications clientes Office et s’étendue aux adresses IP dédiées aux services Office 365 qui sont renforcés au niveau de l’application et du réseau. Si vous souhaitez en savoir plus, consultez l’article [Des moyens alternatifs pour les professionnels de la sécurité et les services informatiques de réaliser des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d'aujourd'hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

- Est pris en charge nativement par la plupart des plateformes VPN d’entreprise

  Microsoft continue de collaborer avec des partenaires de production de solutions VPN commerciales pour aider les partenaires à développer des instructions et des modèles de configuration ciblés pour leurs solutions, conformément aux recommandations ci-dessus. Si vous souhaitez en savoir plus, consultez l’article [Guides d’utilisation pour les plateformes VPN courantes](microsoft-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms).

>[!TIP]
>Microsoft recommande de concentrer la configuration de la segmentation du tunnel VPN sur les plages d’adresses IP dédiées aux services Office 365. Bien que les configurations de segmentation de tunnel basées sur des FQDN ou AppID soient possibles sur certaines plates-formes clientes VPN, elles peuvent ne pas couvrir entièrement les scénarios clés d'Office 365 et peuvent entrer en conflit avec les règles de routage VPN basées sur IP. Pour cette raison, Microsoft vous déconseille d’utiliser les FQDN Office 365 pour configurer la segmentation de tunnel VPN. L’utilisation de la configuration des FQDN peut être utile dans d’autres cas connexes, tels que les personnalisations de fichier .pac ou pour implémenter la dérivation par proxy.

Si vous souhaitez obtenir des instructions complètes sur l’implémentation, consultez l’article [Implémentation de la segmentation de tunnel VPN pour Office 365](microsoft-365-vpn-implement-split-tunnel.md).

Pour un processus pas à pas de configuration de Microsoft 365 pour les travailleurs à distance, voir Configurer votre [infrastructure pour le travail à distance](..\solutions\empower-people-to-work-remotely.md)

## <a name="the-vpn-split-tunnel-strategy"></a>La stratégie de segmentation de tunnel VPN

Les réseaux d’entreprise traditionnels sont souvent conçus pour fonctionner de façon sécurisée dans un environnement préexistant dans lequel les données, les services et les applications les plus importants sont hébergés en local et sont directement connectés au réseau interne de l’entreprise, comme la plupart des utilisateurs. Ainsi, l'infrastructure réseau est construite autour de ces éléments et, en ce sens, les succursales sont connectées au siège social via des réseaux _MPLS (Multiprotocol Label Switching)_, et les utilisateurs distants doivent se connecter au réseau d'entreprise via un VPN pour accéder à la fois aux points de terminaison locaux et à Internet. Dans ce modèle, tout le trafic provenant d’utilisateurs distants traverse le réseau d’entreprise et est acheminé vers le service cloud via un point de sortie commun.

![Configuration VPN obligatoire](../media/vpn-split-tunneling/vpn-model-1.png)

_Image 2 : Une solution VPN commune pour les utilisateurs distants où tout le trafic est renvoyé vers le réseau d’entreprise, quelle que soit la destination_

À mesure que les organisations déplacent des données et des applications vers le cloud, ce modèle commence à devenir moins efficace, car il devient rapidement fastidieux, coûteux et incalgable, ce qui a un impact significatif sur les performances et l’efficacité du réseau des utilisateurs et limite la capacité de l’organisation à s’adapter à l’évolution des besoins. De nombreux clients Microsoft ont signalé qu’il y a quelques années, 80 % du trafic réseau était vers une destination interne, mais en 2020, plus de 80 % du trafic se connecte à une ressource cloud externe.

La crise du COVID-19 a aggravé ce problème et a exigé des solutions immédiates pour la grande majorité des organisations. De nombreux clients ont trouvé que le modèle de VPN obligatoire n’était pas suffisamment évolutif ou performant pour les scénarios de travail se faisant à 100% à distance, comme le nécessite cette crise. Des solutions rapides sont nécessaires pour que ces organisations continuent à fonctionner efficacement.

Pour le service Office 365, Microsoft a conçu les exigences de connectivité pour le service en ayant ce problème à l’esprit, où un ensemble de points de terminaison de service concentrés, étroitement contrôlés et relativement statiques peut être optimisé très simplement et rapidement afin de fournir des performances élevées pour les utilisateurs qui accèdent au service et de réduire la charge sur l’infrastructure VPN afin qu’elle puisse être utilisée par le trafic qui en a encore besoin.

Office 365 classe les points de terminaison requis pour Office 365 en trois catégories : **Optimiser**, **Autoriser** et **Par défaut**. **Optimiser** les points de terminaison est notre objectif ici et présente les caractéristiques suivantes :

- Les points de terminaison détenus et gérés par Microsoft sont-ils hébergés sur une infrastructure Microsoft
- Sont-ils dédiés aux principales charges de travail Office 365 comme Exchange Online, SharePoint Online, Skype Entreprise Online et Microsoft Teams
- Ont-ils des adresses IP fournies
- Faible taux de modifications et qui devraient rester de taille réduite (actuellement 20 sous-réseaux IP)
- Ils sont sensibles au volume et / ou à la latence
- Ils sont en mesure d'avoir les éléments de sécurité requis fournis dans le service plutôt qu'en ligne sur le réseau
- Représente environ 70 à 80% du volume de trafic vers le service Office 365

Cet ensemble de points de terminaison étroitement limité peut être séparé du tunnel VPN obligatoire et envoyé directement, et en toute sécurité, au service Office 365 via l'interface locale de l'utilisateur. C’est ce qu’on appelle **la segmentation du tunnel**.

Les éléments de sécurité tels que DLP, la protection antivirus, l’authentification et le contrôle d’accès peuvent tous être remis beaucoup plus efficacement sur ces points de terminaison à différentes couches du service. Comme nous redirigés également l’essentiel du volume de trafic de la solution VPN, cela libère la capacité VPN pour le trafic critique de l’entreprise qui s’en appuie toujours. Cela devrait également supprimer la nécessité, dans de nombreux cas, de passer par un programme de mise à niveau long et coûteux pour faire face à ce nouveau mode de fonctionnement.

![Détails Tunnel configuration VPN partagés](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

_Image 3 : Une solution de segmentation de tunnel VPN avec des exceptions Office 365 définies, envoyées directement au service. Tout autre trafic est renvoyé dans le réseau d'entreprise, quelle que soit la destination._

Du point de vue de la sécurité, Microsoft dispose d'une gamme de fonctionnalités de sécurité qui peuvent être utilisées pour fournir une sécurité similaire, voire améliorée, à celle fournie par l'inspection en ligne par des piles de sécurité locales. L’article de blog de l’équipe de sécurité Microsoft, [Des moyens alternatifs pour les professionnels de la sécurité et l'informatique de réaliser des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d'aujourd'hui](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) propose un résumé clair des fonctionnalités disponibles. Vous trouverez aussi des instructions plus détaillées dans cet article. Vous pouvez également en apprendre plus sur l’implémentation Microsoft de la segmentation de tunnel VPN en consultant l’article [Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

Dans de nombreux cas, cette implémentation peut être réalisée en quelques heures, ce qui permet de résoudre rapidement l'un des problèmes les plus urgents auxquels sont confrontées les organisations, qui passent rapidement au travail à distance de façon exclusive. Si vous souhaitez obtenir des instructions sur l’implémentation de la segmentation du tunnel VPN, consultez l’article [Implémentation de la segmentation de tunnel VPN pour Office 365](microsoft-365-vpn-implement-split-tunnel.md).

## <a name="related-topics"></a>Voir aussi

[Implémentation d'un tunnel VPN partagé pour Office 365](microsoft-365-vpn-implement-split-tunnel.md)

[Optimisation des performances de Microsoft Office 365 pour les utilisateurs résidant en Chine](microsoft-365-networking-china.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Principes de connectivité réseau Office 365](microsoft-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)

[Test de connectivité Microsoft 365](https://aka.ms/netonboard)