---
title: 'Vue d’ensemble : tunnel vpn partagé pour Microsoft 365'
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
- m365initiative-coredeploy
f1.keywords:
- NOCSH
description: Vue d’ensemble de la tunneling fractionnement VPN avec Microsoft 365 optimiser la connectivité pour les utilisateurs distants.
ms.openlocfilehash: 67ce8a38b536dab12af679ba860aac6d974db60e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329070"
---
# <a name="overview-vpn-split-tunneling-for-microsoft-365"></a>Vue d’ensemble : tunnel vpn partagé pour Microsoft 365

>[!NOTE]
>Cet article fait partie d’un ensemble d’articles qui traitent Microsoft 365'optimisation des utilisateurs distants.

>- Pour obtenir des instructions détaillées sur l’implémentation de la tunneling fractionnement VPN, voir [Implementing VPN split tunneling for Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Pour obtenir la liste détaillée des scénarios de tunneling fractionnement VPN, voir [Scénarios courants de tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Pour obtenir des instructions sur la sécurisation Teams trafic multimédia dans les environnements de tunnel partagé VPN, voir Sécurisation du trafic Teams multimédia [pour la tunnelisation fractionnée VPN](microsoft-365-vpn-securing-teams.md).
>- Pour plus d’informations sur la configuration de Stream et d’événements en direct dans les environnements VPN, voir Considérations spéciales pour Stream et les [événements en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md).
>- Pour plus d’informations sur l’optimisation Microsoft 365 performances des clients internationaux pour les utilisateurs en Chine, voir Microsoft 365 [optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md).

Les entreprises utilisent traditionnellement des VPN pour prendre en charge des expériences distantes sécurisées pour leurs utilisateurs. Bien que les charges de travail principales restent en local, un VPN du client distant acheminé via un centre de données sur le réseau d’entreprise était la méthode principale pour les utilisateurs distants pour accéder aux ressources d’entreprise. Pour protéger ces connexions, les entreprises construisent des couches de solutions de sécurité réseau sur les chemins VPN. Cette sécurité a été conçue pour protéger l’infrastructure interne et pour protéger la navigation mobile des sites web externes en réroutant le trafic vers le VPN, puis via le périmètre Internet local. Les VPN, les périmètres réseau et l’infrastructure de sécurité associée ont souvent été conçus et mis à l’échelle pour un volume défini de trafic, généralement avec la plupart de la connectivité initiée à partir du réseau d’entreprise et la plupart d’entre elles restant dans les limites du réseau interne.

Pendant un certain temps, les modèles VPN où toutes les connexions à partir de l’appareil utilisateur distant sont routés vers le réseau local (appelées _tunnel imposé_) étaient très durables tant que l’échelle simultanée des utilisateurs distants était modeste et que les volumes de trafic qui traversent le réseau privé (VPN) étaient faibles.  Certains clients ont continué à utiliser le tunneling de force VPN comme état de quo même après que leurs applications ont été déplacées de l’intérieur du périmètre d’entreprise vers les clouds SaaS publics.

L’utilisation de VPN tunnelés forcés pour la connexion à des applications cloud distribuées et sensibles aux performances est sous-optimale, mais les effets négatifs ont été acceptés par certaines entreprises afin de maintenir le quo de sécurité. Un exemple de diagramme de ce scénario est illustré ci-dessous :

![Configuration vpn Tunnel contrainte.](../media/vpn-split-tunneling/enterprise-network-traditional.png)

_Figure 1 : Une solution VPN Tunnel contrainte traditionnelle._

This problem has been growing for many years, with many customers reporting a significant shift of network traffic patterns. Le trafic qui était utilisé pour rester sur site se connecte désormais aux points de terminaison cloud externes. De nombreux clients Microsoft signalent qu’auparavant, environ 80 % du trafic réseau était vers une source interne (représentée par la ligne pointillée dans le diagramme ci-dessus). En 2020, ce nombre a diminué jusqu’à environ 20 % ou moins, car les charges de travail majeures ont été décalées vers le cloud. Ces tendances ne sont pas rares avec d’autres entreprises. Au fil du temps, au fur et à mesure de l’évolution du cloud, le modèle ci-dessus devient de plus en plus fastidieux et fastidieux, empêchant ainsi une organisation d’être agile au fur et à mesure qu’elle passe à un monde avant tout cloud.

La crise mondiale du COVID-19 a fait resserre ce problème pour exiger une correction immédiate. La nécessité d'assurer la sécurité des employés a généré des demandes sans précédent en matière de technologies de l'information pour prendre en charge la productivité du travail à domicile à une échelle massive. Microsoft 365 est bien placé pour aider les clients à répondre à cette demande, mais la forte concurrence des utilisateurs travaillant à partir de leur domicile génère un volume élevé de trafic Microsoft 365 qui, s’il est acheminé via un tunnel forcé VPN et des périmètres réseau locaux, entraîne une saturation rapide et exécute l’infrastructure VPN hors capacité. Dans cette nouvelle réalité, l’utilisation du VPN pour accéder à Microsoft 365 n’est plus seulement un obstacle aux performances, mais un mur dur qui non seulement a un impact sur les Microsoft 365 mais également sur les opérations d’entreprise critiques qui doivent encore s’appuyer sur le VPN pour fonctionner.

Microsoft a travaillé en étroite collaboration avec les clients et le secteur plus large pour fournir des solutions efficaces et modernes à ces problèmes à partir de nos propres services et pour s’aligner sur les meilleures pratiques du secteur. Les principes de connectivité du service Microsoft 365 ont été conçus pour fonctionner efficacement pour les [utilisateurs distants](./microsoft-365-network-connectivity-principles.md) tout en permettant à une organisation de maintenir la sécurité et de contrôler sa connectivité. Ces solutions peuvent également être implémentées rapidement avec un travail limité tout en ayant un impact positif significatif sur les problèmes décrits ci-dessus.

Pour les clients qui connectent leurs appareils de travail à distance au réseau d’entreprise ou à l’infrastructure cloud sur VPN, Microsoft recommande que les scénarios de Microsoft 365 clés **Microsoft Teams**, **SharePoint Online** et **Exchange Online** soient acheminés sur une configuration de _tunnel partagé VPN_. Cela devient particulièrement important en tant que stratégie de première ligne pour faciliter la productivité continue des employés lors d’événements de travail à domicile à grande échelle tels que la crise du COVID-19.

![Fractionner Tunnel configuration VPN.](../media/vpn-split-tunneling/vpn-model-2.png)

_Figure 2 : Solution de tunnel partagé VPN avec des exceptions Microsoft 365 envoyées directement au service. Tout autre trafic traverse le tunnel VPN quelle que soit la destination._

L’essentiel de cette approche est de fournir aux entreprises une méthode simple pour atténuer les risques de saturation de l’infrastructure VPN et améliorer considérablement les performances de Microsoft 365 dans la période la plus courte possible. La configuration des clients VPN pour autoriser le trafic de trafic à volume élevé le plus Microsoft 365 critique à contourner le tunnel VPN offre les avantages suivants :

- Atténue immédiatement la cause première d’une majorité de problèmes de performances et de capacité réseau signalés par les clients dans les architectures VPN d’entreprise qui ont un impact sur Microsoft 365 expérience utilisateur
  
  La solution recommandée cible spécifiquement les points Microsoft 365 service classés comme Optimiser dans la rubrique Microsoft 365  [URL et plages d’adresses IP](./urls-and-ip-address-ranges.md). Le trafic vers ces points de terminaison est hautement sensible à la latence et à la limitation de bande passante, et son activation pour contourner le tunnel VPN peut considérablement améliorer l’expérience utilisateur final et réduire la charge réseau d’entreprise. Microsoft 365 connexions qui ne constituent pas la majorité de la bande passante ou de l’encombrement de l’expérience utilisateur peuvent continuer à être acheminées via le tunnel VPN avec le reste du trafic internet. Si vous souhaitez en savoir plus, consultez l’article [la stratégie de segmentation de tunnel VPN](#the-vpn-split-tunnel-strategy).

- Peut être configuré, testé et implémenté rapidement par les clients et sans configuration d’infrastructure ou d’application supplémentaire.

  En fonction de la plateforme VPN et de l’architecture réseau, l’implémentation peut prendre quelques heures. Si vous souhaitez en savoir plus, consultez l’article [Implémenter la segmentation de tunnel VPN](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling).

- Préserve la posture de sécurité des implémentations VPN client en ne modifiant pas la façon dont les autres connexions sont acheminées, notamment le trafic vers Internet

  La configuration recommandée respecte les principes de **moindre privilège** pour les exceptions de trafic VPN et permet aux clients d’implémenter une segmentation de tunnel VPN sans exposer les utilisateurs ou l’infrastructure à des risques de sécurité supplémentaires. Le trafic réseau acheminé directement vers les points de terminaison Microsoft 365 est chiffré, validé pour l’intégrité par les piles d’applications clientes Office et s’étendue aux adresses IP dédiées aux services Microsoft 365 qui sont renforcés au niveau de l’application et du réseau. Si vous souhaitez en savoir plus, consultez l’article [Des moyens alternatifs pour les professionnels de la sécurité et les services informatiques de réaliser des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d'aujourd'hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

- Est pris en charge nativement par la plupart des plateformes VPN d’entreprise

  Microsoft continue de collaborer avec des partenaires de production de solutions VPN commerciales pour aider les partenaires à développer des instructions et des modèles de configuration ciblés pour leurs solutions, conformément aux recommandations ci-dessus. Si vous souhaitez en savoir plus, consultez l’article [Guides d’utilisation pour les plateformes VPN courantes](microsoft-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms).

>[!TIP]
>Microsoft recommande de concentrer la configuration VPN de tunnel partagé sur des plages d’adresses IP dédiées documentées pour Microsoft 365 services. Les configurations de tunnel partagé basées sur le FQDN ou AppID, bien que cela soit possible sur certaines plateformes clientes VPN, peuvent ne pas couvrir entièrement les scénarios de Microsoft 365 clés et peuvent être en conflit avec les règles de routage VPN basées sur IP. Pour cette raison, Microsoft ne recommande pas d’utiliser Microsoft 365 FQDN pour configurer un VPN de tunnel partagé. L’utilisation de la configuration des FQDN peut être utile dans d’autres cas connexes, tels que les personnalisations de fichier .pac ou pour implémenter la dérivation par proxy.

Pour obtenir des instructions d’implémentation complètes, voir [Implémentation de la tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

Pour un processus pas à pas de configuration de Microsoft 365 pour les travailleurs à distance, voir Configurer votre [infrastructure pour le travail à distance](..\solutions\empower-people-to-work-remotely.md)

## <a name="the-vpn-split-tunnel-strategy"></a>La stratégie de segmentation de tunnel VPN

Les réseaux d’entreprise traditionnels sont souvent conçus pour fonctionner de façon sécurisée dans un environnement préexistant dans lequel les données, les services et les applications les plus importants sont hébergés en local et sont directement connectés au réseau interne de l’entreprise, comme la plupart des utilisateurs. Ainsi, l'infrastructure réseau est construite autour de ces éléments et, en ce sens, les succursales sont connectées au siège social via des réseaux _MPLS (Multiprotocol Label Switching)_, et les utilisateurs distants doivent se connecter au réseau d'entreprise via un VPN pour accéder à la fois aux points de terminaison locaux et à Internet. Dans ce modèle, tout le trafic provenant d’utilisateurs distants traverse le réseau d’entreprise et est acheminé vers le service cloud via un point de sortie commun.

![Configuration VPN forcée.](../media/vpn-split-tunneling/vpn-model-1.png)

_Image 2 : Une solution VPN commune pour les utilisateurs distants où tout le trafic est renvoyé vers le réseau d’entreprise, quelle que soit la destination_

À mesure que les organisations déplacent des données et des applications vers le cloud, ce modèle commence à devenir moins efficace, car il devient rapidement fastidieux, coûteux et incalgable, ce qui a un impact significatif sur les performances et l’efficacité du réseau des utilisateurs et limite la capacité de l’organisation à s’adapter à l’évolution des besoins. De nombreux clients Microsoft ont signalé qu’il y a quelques années, 80 % du trafic réseau était vers une destination interne, mais en 2020, plus 80 % du trafic se connecte à une ressource cloud externe.

La crise du COVID-19 a aggravé ce problème et a exigé des solutions immédiates pour la grande majorité des organisations. De nombreux clients ont trouvé que le modèle de VPN obligatoire n’était pas suffisamment évolutif ou performant pour les scénarios de travail se faisant à 100% à distance, comme le nécessite cette crise. Des solutions rapides sont nécessaires pour que ces organisations continuent à fonctionner efficacement.

Pour le service Microsoft 365, Microsoft a conçu les exigences de connectivité pour le service en ayant ce problème à l’esprit, où un ensemble de points de terminaison de service concentrés, étroitement contrôlés et relativement statiques peut être optimisé très simplement et rapidement afin de fournir des performances élevées pour les utilisateurs qui accèdent au service et de réduire la charge sur l’infrastructure VPN afin qu’il puisse être utilisé par le trafic qui en a encore besoin.

Microsoft 365 classe les points de terminaison requis pour Microsoft 365 en trois catégories : **Optimiser****, Autoriser** et **Par défaut**. **Optimiser** les points de terminaison est notre objectif ici et présente les caractéristiques suivantes :

- Les points de terminaison détenus et gérés par Microsoft sont-ils hébergés sur une infrastructure Microsoft
- Sont dédiés aux charges Microsoft 365 de travail principales telles que Exchange Online, SharePoint Online, Skype Entreprise Online et Microsoft Teams
- Ont-ils des adresses IP fournies
- Faible taux de modifications et qui devraient rester de taille réduite (actuellement 20 sous-réseaux IP)
- Ils sont sensibles au volume et / ou à la latence
- Ils sont en mesure d'avoir les éléments de sécurité requis fournis dans le service plutôt qu'en ligne sur le réseau
- Représente environ 70 à 80 % du volume du trafic vers Microsoft 365 service

Cet ensemble étroitement restreint de points de terminaison peut être séparé du tunnel VPN forcé et envoyé en toute sécurité et directement au service Microsoft 365 via l’interface locale de l’utilisateur. C’est ce qu’on appelle **la segmentation du tunnel**.

Les éléments de sécurité tels que DLP, la protection antivirus, l’authentification et le contrôle d’accès peuvent tous être remis beaucoup plus efficacement sur ces points de terminaison à différentes couches du service. Comme nous redirigés également l’essentiel du volume du trafic de la solution VPN, cela libère la capacité VPN pour le trafic critique de l’entreprise qui s’en appuie toujours. Cela devrait également supprimer la nécessité, dans de nombreux cas, de passer par un programme de mise à niveau long et coûteux pour faire face à ce nouveau mode de fonctionnement.

![Fractionner Tunnel de configuration VPN.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

_Figure 3 : Solution de tunnel partagé VPN avec des exceptions Microsoft 365 envoyées directement au service. Tous les autres trafics sont de nouveau forcés dans le réseau d’entreprise, quelle que soit la destination._

Du point de vue de la sécurité, Microsoft dispose d'une gamme de fonctionnalités de sécurité qui peuvent être utilisées pour fournir une sécurité similaire, voire améliorée, à celle fournie par l'inspection en ligne par des piles de sécurité locales. L’article de blog de l’équipe de sécurité Microsoft, [Des moyens alternatifs pour les professionnels de la sécurité et l'informatique de réaliser des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d'aujourd'hui](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) propose un résumé clair des fonctionnalités disponibles. Vous trouverez aussi des instructions plus détaillées dans cet article. Vous pouvez également en apprendre plus sur l’implémentation Microsoft de la segmentation de tunnel VPN en consultant l’article [Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

Dans de nombreux cas, cette implémentation peut être réalisée en quelques heures, ce qui permet de résoudre rapidement l'un des problèmes les plus urgents auxquels sont confrontées les organisations, qui passent rapidement au travail à distance de façon exclusive. Pour obtenir des instructions d’implémentation de tunnel vpn fractioné, voir [Implémentation de la tunnelisation fractionner VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

## <a name="faq"></a>FAQ

L’équipe de sécurité Microsoft a publié d’autres méthodes pour les professionnels de la sécurité et les services [informatiques afin d’obtenir des contrôles](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) de sécurité modernes dans les scénarios de travail à distance uniques d’aujourd’hui, un billet de blog qui décrit les principales façons pour les professionnels de la sécurité et les services informatiques d’obtenir des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d’aujourd’hui. De plus, vous trouverez ci-dessous quelques-unes des questions et réponses les plus fréquemment posées à ce sujet.

### <a name="how-do-i-stop-users-accessing-other-tenants-i-do-not-trust-where-they-could-exfiltrate-data"></a>Comment empêcher les utilisateurs d'accéder à d'autres locataires en qui je n'ai pas confiance et où ils pourraient exfiltrer des données ?

La réponse est une [fonctionnalité de appelée restrictions de locataire](/azure/active-directory/manage-apps/tenant-restrictions). Le trafic d’authentification n’est pas un volume élevé, ni particulièrement sensible à la latence. Par ailleurs, il peut être envoyé via la solution VPN au proxy local où la fonctionnalité est appliquée. Une liste d’autorisation des clients de confiance est conservée ici et si le client tente d’obtenir un jeton à un client qui n’est pas approuvé, le proxy refuse simplement la demande. Si le locataire est digne de confiance, un jeton est accessible si l'utilisateur a les informations d'identification et les droits appropriés.

Ainsi, même si un utilisateur peut établir une connexion TCP/UDP aux points de terminaison marqués Optimiser ci-dessus, sans jeton valide pour accéder au client en question, il ne peut simplement pas se connecter et accéder/déplacer des données.

### <a name="does-this-model-allow-access-to-consumer-services-such-as-personal-onedrive-accounts"></a>Ce modèle autorise-t-il l’accès aux services grand public tels que les comptes OneDrive personnels ?

Non, ce n’est pas le cas, les points de terminaison Microsoft 365 ne sont pas les mêmes que les services grand public (Onedrive.live.com par exemple), de sorte que le tunnel fractioné ne permet pas à un utilisateur d’accéder directement aux services grand public. Le trafic vers les points de terminaison consommateurs continuera à utiliser le tunnel VPN et les stratégies existantes continueront à s’appliquer.

### <a name="how-do-i-apply-dlp-and-protect-my-sensitive-data-when-the-traffic-no-longer-flows-through-my-on-premises-solution"></a>Comment appliquer le DLP et protéger mes données sensibles lorsque le trafic ne passe plus par ma solution locale ?

Pour éviter la divulgation accidentelle d’informations sensibles, Microsoft 365 dispose d’un ensemble riche [d’outils intégrés](../compliance/information-protection.md). Vous pouvez utiliser les [fonctionnalités DLP](../compliance/dlp-learn-about-dlp.md) intégrées de Teams et de SharePoint pour détecter des informations sensibles stockées ou partagées de manière inappropriée. Si une partie de votre stratégie de travail à distance implique une stratégie BYOD (Bring-your-own-device), vous pouvez utiliser [](/azure/active-directory/conditional-access/app-based-conditional-access) l’accès conditionnel basé sur l’application pour empêcher le téléchargement de données sensibles sur les appareils personnels des utilisateurs

### <a name="how-do-i-evaluate-and-maintain-control-of-the-users-authentication-when-they-are-connecting-directly"></a>Comment évaluer et maintenir le contrôle de l’authentification de l’utilisateur lorsqu’il se connecte directement ?

En plus de la fonctionnalité restrictions de locataire signalée au T1, les [stratégies d’accès conditionnel](/azure/active-directory/conditional-access/overview) peuvent être appliquées pour évaluer de façon dynamique le risque d’une demande d’authentification et réagir de façon appropriée. Microsoft recommande que le [](https://www.microsoft.com/security/zero-trust?rtc=1) modèle confiance zéro soit implémenté au fil du temps et nous pouvons utiliser des stratégies d’accès conditionnel Azure AD pour maintenir le contrôle dans un monde mobile et cloud. Les stratégies d'accès conditionnel peuvent être utilisées pour décider en temps réel si une demande d'authentification est acceptée ou non, en fonction de nombreux facteurs tels que :

- Appareil, l’appareil est-il connu/approuvé/lié au domaine ?
- IP : la demande d’authentification provient-elle d’une adresse IP d’entreprise connue ? Ou d’un pays dans lequel nous ne sommes pas dignes de confiance ?
- Application : l’utilisateur est-il autorisé à utiliser cette application ?

Nous pouvons ensuite déclencher une stratégie telle que approuver, déclencher l’authentification multifacteur ou bloquer l’authentification en fonction de ces stratégies.

### <a name="how-do-i-protect-against-viruses-and-malware"></a>Comment puis-je me protéger contre les virus et les programmes malveillants ?

Là encore, Microsoft 365 protection des points de terminaison marqués Optimiser dans différentes couches du service lui-même, [décrites dans ce document](/office365/Enterprise/office-365-malware-and-ransomware-protection). Comme indiqué, il est beaucoup plus efficace de fournir ces éléments de sécurité dans le service lui-même plutôt que d’essayer de le faire en ligne avec des appareils qui ne comprennent peut-être pas complètement les protocoles/trafic. Par défaut, SharePoint Online analyse automatiquement les [téléchargements](../security/office-365-security/virus-detection-in-spo.md) de fichiers pour les programmes malveillants connus

Pour les Exchange de terminaison répertoriés ci-dessus, [Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) et [Microsoft Defender pour Microsoft 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) font un excellent travail de sécurité du trafic vers le service.

### <a name="can-i-send-more-than-just-the-optimize-traffic-direct"></a>Puis-je envoyer plus que le message direct Optimiser le trafic ?

Une priorité doit être accordée au points de terminaison marqués **Optimiser**, car ceux-ci vous permettront de bénéficier d’un niveau de travail optimal. Toutefois, si vous le souhaitez, les points de terminaison autoriser marqués sont requis pour que le service fonctionne et que des adresses IP soient fournies pour les points de terminaison qui peuvent être utilisés si nécessaire.

Plusieurs fournisseurs proposent également des solutions de proxy/sécurité basées sur le cloud, _appelées passerelles web sécurisées_ , qui fournissent une application centrale de sécurité, de contrôle et de stratégie d’entreprise pour la navigation web générale. Ces solutions peuvent fonctionner bien dans un monde cloud, si hautement disponible, performant et mis en service à proximité de vos utilisateurs en permettant à un accès Internet sécurisé d’être remis à partir d’un emplacement basé sur le cloud à proximité de l’utilisateur. Cela supprime la nécessité d’une épingle via le réseau VPN/d’entreprise pour le trafic de navigation général, tout en permettant le contrôle central de sécurité.

Même avec ces solutions en place toutefois, Microsoft recommande toujours vivement d’optimiser les Microsoft 365 trafic est envoyé directement au service.

Pour obtenir des instructions sur l’accès direct à un réseau virtuel Azure, voir Travail à distance à l’aide de la passerelle [VPN Azure point à site](/azure/vpn-gateway/work-remotely-support).

### <a name="why-is-port-80-required-is-traffic-sent-in-the-clear"></a>Pourquoi le port 80 est-il obligatoire ? Le trafic est-il envoyé en clair ?

Le port 80 est uniquement utilisé pour les opérations telles que la redirection vers une session de port 443, les données client ne sont pas envoyées ou sont accessibles via le port 80. [Le](../compliance/encryption.md) chiffrement décrit le chiffrement pour les données en transit et au repos pour Microsoft 365, et [Les types](/microsoftteams/microsoft-teams-online-call-flows#types-of-traffic) de trafic indiquent comment nous utilisons SRTP pour protéger Teams trafic multimédia.

### <a name="does-this-advice-apply-to-users-in-china-using-a-worldwide-instance-of-microsoft-365"></a>Ce conseil s’applique-t-il aux utilisateurs en Chine à l’aide d’une instance Microsoft 365 ?

**Pas de**, ce n’est pas le cas. La seule mise en garde aux conseils ci-dessus est que les utilisateurs de la RPC se connectent à une instance mondiale de Microsoft 365. En raison de l'encombrement fréquent des réseaux transfrontaliers dans la région, les performances de la sortie directe d'Internet peuvent être variables. La plupart des clients dans la région utilisent un réseau privé virtuel (VPN) pour transférer le trafic vers le réseau d’entreprise et utiliser leur circuit MPLS autorisé ou similaires à des sortir du pays via un chemin optimisé. Cela est décrit plus en détail dans l’article [Microsoft 365 optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md).

### <a name="does-split-tunnel-configuration-work-for-teams-running-in-a-browser"></a>La configuration en tunnel partagé fonctionne-t-elle Teams’exécution dans un navigateur ?

Oui, avec des avertissements. La Teams est prise en charge dans les navigateurs répertoriés dans [Obtenir des clients pour Microsoft Teams](/microsoftteams/get-clients#web-client).

En outre, Microsoft Edge **96** et supérieures prend en charge la tunneling fractionné VPN pour le trafic pair à pair en activant la stratégie [Edge WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled). Pour l’instant, d’autres navigateurs peuvent ne pas prendre en charge la tunneling fractionnée VPN pour le trafic pair à pair.

## <a name="related-articles"></a>Articles connexes

[Implémentation de la tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Scénarios courants de tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN](microsoft-365-vpn-securing-teams.md)

[Considérations spéciales pour les flux et les événements en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Microsoft 365 réseau et l’optimisation des performances](network-planning-and-performance.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Réseau mondial Microsoft](/azure/networking/microsoft-global-network)
