---
title: 'Vue d’ensemble : tunneling fractionné VPN pour Microsoft 365'
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
- Strat_O365_Enterprise
- remotework
- m365initiative-coredeploy
f1.keywords:
- NOCSH
description: Vue d’ensemble du tunneling fractionné VPN avec Microsoft 365 pour optimiser la connectivité pour les utilisateurs distants.
ms.openlocfilehash: ab719109756da721ac46a1ecba069a02ce85fb68
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68200976"
---
# <a name="overview-vpn-split-tunneling-for-microsoft-365"></a>Vue d’ensemble : tunneling fractionné VPN pour Microsoft 365

>[!NOTE]
>Cet article fait partie d’un ensemble d’articles qui traitent de l’optimisation de Microsoft 365 pour les utilisateurs distants.

>- Pour obtenir des conseils détaillés sur l’implémentation du tunneling fractionné VPN, consultez [Implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Pour obtenir la liste détaillée des scénarios de tunneling fractionné [VPN, consultez les scénarios de tunneling fractionné VPN courants pour Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Pour obtenir des conseils sur la sécurisation du trafic multimédia Teams dans les environnements de tunneling fractionné VPN, consultez [Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN](microsoft-365-vpn-securing-teams.md).
>- Pour plus d’informations sur la configuration des événements stream et en direct dans les environnements VPN, consultez [considérations spéciales sur les événements stream et en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md).
>- Pour plus d’informations sur l’optimisation des performances des locataires Microsoft 365 dans le monde entier pour les utilisateurs en Chine, consultez [l’optimisation des performances de Microsoft 365 pour les utilisateurs chinois](microsoft-365-networking-china.md).

Les entreprises utilisent traditionnellement des VPN pour prendre en charge des expériences distantes sécurisées pour leurs utilisateurs. Bien que les charges de travail de base restaient locales, un VPN du client distant routée via un centre de données sur le réseau d’entreprise était la principale méthode permettant aux utilisateurs distants d’accéder aux ressources d’entreprise. Pour protéger ces connexions, les entreprises construisent des couches de solutions de sécurité réseau sur les chemins VPN. Cette sécurité a été conçue pour protéger l’infrastructure interne et protéger la navigation mobile des sites web externes en réacheminement le trafic vers le VPN, puis via le périmètre Internet local. Les VPN, les périmètres réseau et l’infrastructure de sécurité associée ont souvent été spécialement conçus et mis à l’échelle pour un volume défini de trafic, généralement avec la plupart de la connectivité initiée à partir du réseau d’entreprise, et la plupart d’entre eux restant dans les limites du réseau interne.

Pendant un certain temps, les modèles VPN où toutes les connexions à partir de l’appareil utilisateur distant sont routés vers le réseau local (appelées _tunnel imposé_) étaient très durables tant que l’échelle simultanée des utilisateurs distants était modeste et que les volumes de trafic qui traversent le réseau privé (VPN) étaient faibles.  Certains clients ont continué à utiliser le tunneling par force VPN comme statu quo, même après que leurs applications sont passées de l’intérieur du périmètre de l’entreprise aux clouds SaaS publics.

L’utilisation de VPN tunnelés forcés pour la connexion à des applications cloud distribuées et sensibles aux performances n’est pas optimale, mais les effets négatifs ont été acceptés par certaines entreprises afin de maintenir le statu quo de sécurité. Un exemple de diagramme de ce scénario est illustré ci-dessous :

![Configuration du VPN de tunnel forcé.](../media/vpn-split-tunneling/enterprise-network-traditional.png)

_Figure 1 : Solution VPN de tunnel forcé classique._

Ce problème se développe depuis de nombreuses années, de nombreux clients signalant un changement significatif des modèles de trafic réseau. Le trafic qui restait local se connecte désormais aux points de terminaison cloud externes. De nombreux clients Microsoft signalent qu’auparavant, environ 80 % de leur trafic réseau était vers une source interne (représentée par la ligne en pointillés du diagramme ci-dessus). En 2020, ce nombre est passé à environ 20 % ou moins, car les charges de travail majeures ont été déplacées vers le cloud. Ces tendances ne sont pas rares dans d’autres entreprises. Au fil du temps, à mesure que le parcours cloud progresse, le modèle ci-dessus devient de plus en plus lourd et insoutenable, empêchant une organisation d’être agile lorsqu’elle passe à un monde cloud.

La crise mondiale du COVID-19 a fait remonter ce problème pour exiger une correction immédiate. La nécessité d'assurer la sécurité des employés a généré des demandes sans précédent en matière de technologies de l'information pour prendre en charge la productivité du travail à domicile à une échelle massive. Microsoft 365 est bien positionné pour aider les clients à répondre à cette demande, mais la concurrence élevée des utilisateurs travaillant à domicile génère un grand volume de trafic Microsoft 365 qui, s’il est acheminé via un VPN de tunnel forcé et des périmètres réseau locaux, provoque une saturation rapide et exécute l’infrastructure VPN hors de capacité. Dans cette nouvelle réalité, l’utilisation du VPN pour accéder à Microsoft 365 n’est plus seulement un obstacle aux performances, mais un mur dur qui affecte non seulement Microsoft 365, mais aussi les opérations métier critiques qui doivent encore compter sur le VPN pour fonctionner.

Microsoft travaille en étroite collaboration avec les clients et le secteur dans son ensemble pour fournir des solutions efficaces et modernes à ces problèmes à partir de nos propres services, et pour s’aligner sur les meilleures pratiques du secteur. [Les principes de connectivité](./microsoft-365-network-connectivity-principles.md) du service Microsoft 365 ont été conçus pour fonctionner efficacement pour les utilisateurs distants tout en permettant à une organisation de maintenir la sécurité et le contrôle de leur connectivité. Ces solutions peuvent également être implémentées rapidement avec un travail limité tout en obtenant un effet positif significatif sur les problèmes décrits ci-dessus.

Pour les clients qui connectent leurs appareils de travail à distance au réseau d’entreprise ou à l’infrastructure cloud via VPN, Microsoft recommande que les principaux scénarios Microsoft 365 **Microsoft Teams**, **SharePoint Online** et **Exchange Online** soient routées via une configuration de _tunnel fractionné VPN_. Cela devient particulièrement important, car la stratégie de première ligne visant à faciliter la productivité continue des employés lors d’événements professionnels à grande échelle comme la crise du COVID-19.

![Configuration du VPN de tunnel fractionné.](../media/vpn-split-tunneling/vpn-model-2.png)

_Figure 2 : Solution de tunnel fractionné VPN avec des exceptions Microsoft 365 définies envoyées directement au service. Tous les autres trafics parcourent le tunnel VPN, quelle que soit la destination._

L’essence de cette approche consiste à fournir aux entreprises une méthode simple pour atténuer le risque de saturation de l’infrastructure VPN et améliorer considérablement les performances de Microsoft 365 dans les délais les plus courts possible. La configuration des clients VPN pour permettre au trafic Microsoft 365 le plus critique et le plus volumineux de contourner le tunnel VPN présente les avantages suivants :

- Atténue immédiatement la cause racine de la majorité des problèmes de performances et de capacité réseau signalés par le client dans les architectures VPN d’entreprise ayant un impact sur l’expérience utilisateur de Microsoft 365
  
  La solution recommandée cible spécifiquement les points de terminaison de service Microsoft 365 classés comme **optimisés** dans la rubrique [URL et plages d’adresses IP Microsoft 365](./urls-and-ip-address-ranges.md). Le trafic vers ces points de terminaison est très sensible à la latence et à la limitation de bande passante, et l’activation du contournement du tunnel VPN peut améliorer considérablement l’expérience de l’utilisateur final et réduire la charge réseau de l’entreprise. Les connexions Microsoft 365 qui ne constituent pas la majorité de la bande passante ou de l’empreinte utilisateur peuvent continuer à être routées via le tunnel VPN avec le reste du trafic internet. Si vous souhaitez en savoir plus, consultez l’article [la stratégie de segmentation de tunnel VPN](#the-vpn-split-tunnel-strategy).

- Peut être configuré, testé et implémenté rapidement par les clients et sans infrastructure supplémentaire ni exigences d’application

  En fonction de la plateforme VPN et de l’architecture réseau, l’implémentation peut prendre quelques heures. Si vous souhaitez en savoir plus, consultez l’article [Implémenter la segmentation de tunnel VPN](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling).

- Préserve la posture de sécurité des implémentations VPN client en ne modifiant pas la façon dont les autres connexions sont acheminées, notamment le trafic vers Internet

  La configuration recommandée respecte les principes de **moindre privilège** pour les exceptions de trafic VPN et permet aux clients d’implémenter une segmentation de tunnel VPN sans exposer les utilisateurs ou l’infrastructure à des risques de sécurité supplémentaires. Le trafic réseau acheminé directement vers les points de terminaison Microsoft 365 est chiffré, validé pour l’intégrité par les piles d’applications clientes Office et étendu aux adresses IP dédiées aux services Microsoft 365 renforcés au niveau de l’application et du réseau. Si vous souhaitez en savoir plus, consultez l’article [Des moyens alternatifs pour les professionnels de la sécurité et les services informatiques de réaliser des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d'aujourd'hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

- Est pris en charge nativement par la plupart des plateformes VPN d’entreprise

  Microsoft continue de collaborer avec des partenaires de production de solutions VPN commerciales pour aider les partenaires à développer des instructions et des modèles de configuration ciblés pour leurs solutions, conformément aux recommandations ci-dessus. Si vous souhaitez en savoir plus, consultez l’article [Guides d’utilisation pour les plateformes VPN courantes](microsoft-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms).

>[!TIP]
>Microsoft recommande de concentrer la configuration VPN de tunnel fractionné sur les plages d’adresses IP dédiées documentées pour les services Microsoft 365. Les configurations de tunnel fractionné basées sur un nom de domaine complet ou AppID, bien que possibles sur certaines plateformes clientes VPN, peuvent ne pas couvrir entièrement les principaux scénarios Microsoft 365 et peuvent entrer en conflit avec les règles de routage VPN basées sur IP. Pour cette raison, Microsoft ne recommande pas d’utiliser des noms de domaine complets Microsoft 365 pour configurer le VPN de tunnel fractionné. L’utilisation de la configuration des FQDN peut être utile dans d’autres cas connexes, tels que les personnalisations de fichier .pac ou pour implémenter la dérivation par proxy.

Pour obtenir des conseils d’implémentation complets, consultez [Implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

Pour un processus pas à pas de configuration de Microsoft 365 pour les travailleurs à distance, consultez [Configurer votre infrastructure pour le travail à distance](..\solutions\empower-people-to-work-remotely.md)

## <a name="the-vpn-split-tunnel-strategy"></a>La stratégie de segmentation de tunnel VPN

Les réseaux d’entreprise traditionnels sont souvent conçus pour fonctionner de façon sécurisée dans un environnement préexistant dans lequel les données, les services et les applications les plus importants sont hébergés en local et sont directement connectés au réseau interne de l’entreprise, comme la plupart des utilisateurs. Ainsi, l'infrastructure réseau est construite autour de ces éléments et, en ce sens, les succursales sont connectées au siège social via des réseaux _MPLS (Multiprotocol Label Switching)_, et les utilisateurs distants doivent se connecter au réseau d'entreprise via un VPN pour accéder à la fois aux points de terminaison locaux et à Internet. Dans ce modèle, tout le trafic provenant d’utilisateurs distants traverse le réseau d’entreprise et est acheminé vers le service cloud via un point de sortie commun.

![Configuration VPN forcée.](../media/vpn-split-tunneling/vpn-model-1.png)

_Image 2 : Une solution VPN commune pour les utilisateurs distants où tout le trafic est renvoyé vers le réseau d’entreprise, quelle que soit la destination_

À mesure que les organisations déplacent des données et des applications vers le cloud, ce modèle a commencé à devenir moins efficace, car il devient rapidement lourd, coûteux et indisponible, ce qui affecte considérablement les performances et l’efficacité du réseau des utilisateurs et limite la capacité de l’organisation à s’adapter aux besoins changeants. De nombreux clients Microsoft ont signalé qu’il y a quelques années, 80 % du trafic réseau était vers une destination interne, mais qu’en 2020, plus de 80 % du trafic se connectait à une ressource cloud externe.

La crise du COVID-19 a aggravé ce problème et a exigé des solutions immédiates pour la grande majorité des organisations. De nombreux clients ont trouvé que le modèle de VPN obligatoire n’était pas suffisamment évolutif ou performant pour les scénarios de travail se faisant à 100% à distance, comme le nécessite cette crise. Des solutions rapides sont nécessaires pour que ces organisations continuent à fonctionner efficacement.

Pour le service Microsoft 365, Microsoft a conçu les exigences de connectivité pour le service avec ce problème carrément à l’esprit, où un ensemble ciblé, étroitement contrôlé et relativement statique de points de terminaison de service peut être optimisé très simplement et rapidement afin de fournir des performances élevées pour les utilisateurs qui accèdent au service, et de réduire la charge sur l’infrastructure VPN afin qu’il puisse être utilisé par le trafic qui en a encore besoin.

Microsoft 365 classe les points de terminaison requis pour Microsoft 365 en trois catégories : **Optimiser**, **Autoriser** et **Par défaut**. **Optimiser** les points de terminaison est notre objectif ici et présente les caractéristiques suivantes :

- Les points de terminaison détenus et gérés par Microsoft sont-ils hébergés sur une infrastructure Microsoft
- Sont dédiés aux charges de travail Microsoft 365 principales telles que Exchange Online, SharePoint Online, Skype Entreprise Online et Microsoft Teams
- Ont-ils des adresses IP fournies
- Faible taux de modifications et qui devraient rester de taille réduite (actuellement 20 sous-réseaux IP)
- Ils sont sensibles au volume et / ou à la latence
- Ils sont en mesure d'avoir les éléments de sécurité requis fournis dans le service plutôt qu'en ligne sur le réseau
- Représentent environ 70 à 80 % du volume de trafic vers le service Microsoft 365

Cet ensemble de points de terminaison étroitement délimités peut être séparé du tunnel VPN forcé et envoyé en toute sécurité et directement au service Microsoft 365 via l’interface locale de l’utilisateur. C’est ce qu’on appelle **la segmentation du tunnel**.

Les éléments de sécurité tels que la protection DLP, la protection AV, l’authentification et le contrôle d’accès peuvent tous être fournis beaucoup plus efficacement sur ces points de terminaison à différentes couches au sein du service. Comme nous détourons également la majeure partie du volume de trafic de la solution VPN, cela libère la capacité VPN pour le trafic critique pour l’entreprise qui s’appuie toujours sur celle-ci. Cela devrait également supprimer la nécessité, dans de nombreux cas, de passer par un programme de mise à niveau long et coûteux pour faire face à ce nouveau mode de fonctionnement.

![Détails de configuration du VPN de tunnel fractionné.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

_Figure 3 : Solution de tunnel fractionné VPN avec des exceptions Microsoft 365 définies envoyées directement au service. Tous les autres trafics sont de nouveau forcés dans le réseau d’entreprise, quelle que soit la destination._

Du point de vue de la sécurité, Microsoft dispose d'une gamme de fonctionnalités de sécurité qui peuvent être utilisées pour fournir une sécurité similaire, voire améliorée, à celle fournie par l'inspection en ligne par des piles de sécurité locales. L’article de blog de l’équipe de sécurité Microsoft, [Des moyens alternatifs pour les professionnels de la sécurité et l'informatique de réaliser des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d'aujourd'hui](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) propose un résumé clair des fonctionnalités disponibles. Vous trouverez aussi des instructions plus détaillées dans cet article. Vous pouvez également en apprendre plus sur l’implémentation Microsoft de la segmentation de tunnel VPN en consultant l’article [Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

Dans de nombreux cas, cette implémentation peut être réalisée en quelques heures, ce qui permet de résoudre rapidement l'un des problèmes les plus urgents auxquels sont confrontées les organisations, qui passent rapidement au travail à distance de façon exclusive. Pour obtenir des conseils d’implémentation de tunnel fractionné [VPN, consultez Implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

## <a name="faq"></a>Questions fréquentes (FAQ)

L’équipe de sécurité Microsoft a publié [d’autres méthodes pour les professionnels de la sécurité et l’informatique afin d’obtenir des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d’aujourd’hui](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/), un billet de blog qui décrit les principales façons pour les professionnels de la sécurité et l’informatique d’obtenir des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d’aujourd’hui. De plus, vous trouverez ci-dessous quelques-unes des questions et réponses les plus fréquemment posées à ce sujet.

### <a name="how-do-i-stop-users-accessing-other-tenants-i-do-not-trust-where-they-could-exfiltrate-data"></a>Comment empêcher les utilisateurs d'accéder à d'autres locataires en qui je n'ai pas confiance et où ils pourraient exfiltrer des données ?

La réponse est une [fonctionnalité de appelée restrictions de locataire](/azure/active-directory/manage-apps/tenant-restrictions). Le trafic d’authentification n’étant pas sensible au volume élevé ni à la latence, il peut être envoyé via la solution VPN au proxy local où la fonctionnalité est appliquée. Une liste verte de locataires approuvés est conservée ici et si le client tente d’obtenir un jeton à un locataire qui n’est pas approuvé, le proxy refuse simplement la demande. Si le locataire est digne de confiance, un jeton est accessible si l'utilisateur a les informations d'identification et les droits appropriés.

Ainsi, même si un utilisateur peut établir une connexion TCP/UDP aux points de terminaison optimisés marqués ci-dessus, sans jeton valide pour accéder au locataire en question, il ne peut tout simplement pas se connecter et accéder/déplacer des données.

### <a name="does-this-model-allow-access-to-consumer-services-such-as-personal-onedrive-accounts"></a>Ce modèle autorise-t-il l’accès aux services grand public tels que les comptes OneDrive personnels ?

Non, ce n’est pas le cas, les points de terminaison Microsoft 365 ne sont pas les mêmes que les services consommateurs (Onedrive.live.com par exemple) de sorte que le tunnel fractionné n’autorise pas un utilisateur à accéder directement aux services consommateurs. Le trafic vers les points de terminaison consommateurs continuera à utiliser le tunnel VPN et les stratégies existantes continueront à s’appliquer.

### <a name="how-do-i-apply-dlp-and-protect-my-sensitive-data-when-the-traffic-no-longer-flows-through-my-on-premises-solution"></a>Comment appliquer le DLP et protéger mes données sensibles lorsque le trafic ne passe plus par ma solution locale ?

Pour vous aider à empêcher la divulgation accidentelle d’informations sensibles, Microsoft 365 dispose d’un ensemble complet [d’outils intégrés](../compliance/information-protection.md). Vous pouvez utiliser les [fonctionnalités DLP](../compliance/dlp-learn-about-dlp.md) intégrées de Teams et de SharePoint pour détecter des informations sensibles stockées ou partagées de manière inappropriée. Si une partie de votre stratégie de travail à distance implique une stratégie BYOD (bring-your-own-device), vous pouvez utiliser [l’accès conditionnel basé sur l’application](/azure/active-directory/conditional-access/app-based-conditional-access) pour empêcher le téléchargement de données sensibles sur les appareils personnels des utilisateurs

### <a name="how-do-i-evaluate-and-maintain-control-of-the-users-authentication-when-they-are-connecting-directly"></a>Comment évaluer et maintenir le contrôle de l’authentification de l’utilisateur lorsqu’il se connecte directement ?

En plus de la fonctionnalité restrictions de locataire signalée au T1, les [stratégies d’accès conditionnel](/azure/active-directory/conditional-access/overview) peuvent être appliquées pour évaluer de façon dynamique le risque d’une demande d’authentification et réagir de façon appropriée. Microsoft recommande que le [modèle Confiance nulle](https://www.microsoft.com/security/zero-trust?rtc=1) soit implémenté au fil du temps et que nous puissions utiliser des stratégies d’accès conditionnel Azure AD pour maintenir le contrôle dans un monde mobile et cloud. Les stratégies d'accès conditionnel peuvent être utilisées pour décider en temps réel si une demande d'authentification est acceptée ou non, en fonction de nombreux facteurs tels que :

- Appareil, l’appareil est-il connu/approuvé/lié au domaine ?
- IP : la demande d’authentification provient-elle d’une adresse IP d’entreprise connue ? Ou d’un pays dans lequel nous ne sommes pas dignes de confiance ?
- Application : l’utilisateur est-il autorisé à utiliser cette application ?

Nous pouvons ensuite déclencher une stratégie telle que approuver, déclencher l’authentification multifacteur ou bloquer l’authentification en fonction de ces stratégies.

### <a name="how-do-i-protect-against-viruses-and-malware"></a>Comment puis-je me protéger contre les virus et les programmes malveillants ?

Là encore, Microsoft 365 fournit une protection pour les points de terminaison marqués Optimiser dans différentes couches du service lui-même, [décrits dans ce document](/office365/Enterprise/office-365-malware-and-ransomware-protection). Comme indiqué, il est beaucoup plus efficace de fournir ces éléments de sécurité dans le service lui-même plutôt que d’essayer de le faire conformément aux appareils qui peuvent ne pas comprendre pleinement les protocoles/le trafic. Par défaut, SharePoint Online [analyse automatiquement les chargements de fichiers](../security/office-365-security/virus-detection-in-spo.md) à la recherche de programmes malveillants connus

Pour les points de terminaison Exchange répertoriés ci-dessus, [Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) et [Microsoft Defender pour Microsoft 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) font un excellent travail pour assurer la sécurité du trafic vers le service.

### <a name="can-i-send-more-than-just-the-optimize-traffic-direct"></a>Puis-je envoyer plus que le message direct Optimiser le trafic ?

Une priorité doit être accordée au points de terminaison marqués **Optimiser**, car ceux-ci vous permettront de bénéficier d’un niveau de travail optimal. Toutefois, si vous le souhaitez, les points de terminaison marqués d’autorisation sont requis pour que le service fonctionne et des adresses IP sont fournies pour les points de terminaison qui peuvent être utilisés si nécessaire.

Il existe également différents fournisseurs qui offrent des solutions de proxy/sécurité basées sur le cloud appelées _passerelles web sécurisées_ qui fournissent une application de sécurité, de contrôle et de stratégie d’entreprise centralisée pour la navigation web générale. Ces solutions peuvent fonctionner correctement dans un monde cloud, si elles sont hautement disponibles, performantes et approvisionnées à proximité de vos utilisateurs en autorisant un accès Internet sécurisé à partir d’un emplacement cloud proche de l’utilisateur. Cela supprime la nécessité d’une épingle à cheveux via le réseau VPN/d’entreprise pour le trafic de navigation général, tout en autorisant le contrôle de sécurité central.

Toutefois, même si ces solutions sont en place, Microsoft recommande toujours vivement d’envoyer directement au service le trafic Optimisé marqué microsoft 365.

Pour obtenir des conseils sur l’autorisation de l’accès direct à un Réseau virtuel Azure, consultez [Travail à distance à l’aide d’Azure passerelle VPN point à site](/azure/vpn-gateway/work-remotely-support).

### <a name="why-is-port-80-required-is-traffic-sent-in-the-clear"></a>Pourquoi le port 80 est-il obligatoire ? Le trafic est-il envoyé en clair ?

Le port 80 est uniquement utilisé pour les opérations telles que la redirection vers une session de port 443, les données client ne sont pas envoyées ou sont accessibles via le port 80. [Le chiffrement](../compliance/encryption.md) décrit le chiffrement des données en transit et au repos pour Microsoft 365, et les [types de trafic](/microsoftteams/microsoft-teams-online-call-flows#types-of-traffic) décrivent la façon dont nous utilisons SRTP pour protéger le trafic multimédia Teams.

### <a name="does-this-advice-apply-to-users-in-china-using-a-worldwide-instance-of-microsoft-365"></a>Ces conseils s’appliquent-ils aux utilisateurs en Chine utilisant une instance mondiale de Microsoft 365 ?

**Pas de**, ce n’est pas le cas. La seule mise en garde aux conseils ci-dessus concerne les utilisateurs de la RPC qui se connectent à une instance mondiale de Microsoft 365. En raison de l'encombrement fréquent des réseaux transfrontaliers dans la région, les performances de la sortie directe d'Internet peuvent être variables. La plupart des clients dans la région utilisent un réseau privé virtuel (VPN) pour transférer le trafic vers le réseau d’entreprise et utiliser leur circuit MPLS autorisé ou similaires à des sortir du pays via un chemin optimisé. Cela est décrit plus en détail dans l’article [Sur l’optimisation des performances de Microsoft 365 pour les utilisateurs chinois](microsoft-365-networking-china.md).

### <a name="does-split-tunnel-configuration-work-for-teams-running-in-a-browser"></a>La configuration du tunnel fractionné fonctionne-t-elle pour Teams s’exécutant dans un navigateur ?

Oui, avec des mises en garde. La plupart des fonctionnalités Teams sont prises en charge dans les navigateurs répertoriés dans [Obtenir des clients pour Microsoft Teams](/microsoftteams/get-clients#web-client).

En outre, Microsoft Edge **96 et versions ultérieures** prennent en charge le tunneling fractionné VPN pour le trafic pair à pair en activant la stratégie Edge [WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) . À ce stade, d’autres navigateurs peuvent ne pas prendre en charge le tunneling fractionné VPN pour le trafic P2P.

## <a name="related-articles"></a>Articles connexes

[Implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Scénarios courants de tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN](microsoft-365-vpn-securing-teams.md)

[Considérations spéciales sur les événements stream et en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md)

[Optimisation des performances de Microsoft 365 pour les utilisateurs chinois](microsoft-365-networking-china.md)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Optimisation des performances et du réseau Microsoft 365](network-planning-and-performance.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Réseau mondial Microsoft](/azure/networking/microsoft-global-network)
