---
title: Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN
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
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN
ms.openlocfilehash: eb06696b35df6ddb923c6b1e9ae97abf01dccabe
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67701145"
---
# <a name="securing-teams-media-traffic-for-vpn-split-tunneling"></a>Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN

>[!NOTE]
>Cet article fait partie d’un ensemble d’articles qui traitent de l’optimisation de Microsoft 365 pour les utilisateurs distants.

>- Pour obtenir une vue d’ensemble de l’utilisation du tunneling fractionné VPN pour optimiser la connectivité Microsoft 365 pour les utilisateurs distants, consultez [Vue d’ensemble : tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Pour obtenir des conseils détaillés sur l’implémentation du tunneling fractionné VPN, consultez [Implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Pour obtenir la liste détaillée des scénarios de tunneling fractionné [VPN, consultez les scénarios de tunneling fractionné VPN courants pour Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Pour plus d’informations sur la configuration des événements stream et en direct dans les environnements VPN, consultez [considérations spéciales sur les événements stream et en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md).
>- Pour plus d’informations sur l’optimisation des performances des locataires Microsoft 365 dans le monde entier pour les utilisateurs en Chine, consultez [l’optimisation des performances de Microsoft 365 pour les utilisateurs chinois](microsoft-365-networking-china.md).

Certains administrateurs Microsoft Teams peuvent avoir besoin d’informations détaillées sur le fonctionnement des flux d’appels dans Teams à l’aide d’un modèle de tunneling fractionné et sur la façon dont les connexions sont sécurisées.

## <a name="configuration"></a>Configuration

Pour les appels et les réunions, tant que les sous-réseaux Ip d’optimisation requis pour les médias Teams sont correctement en place dans la table de routage, lorsque Teams appelle la fonction [GetBestRoute](/windows/win32/api/iphlpapi/nf-iphlpapi-getbestroute) pour déterminer quelle interface locale correspond à l’itinéraire qu’il doit utiliser pour une destination particulière, l’interface locale est retournée pour les destinations Microsoft dans les blocs IP Microsoft répertoriés ci-dessus.

Certains logiciels clients VPN autorisent la manipulation des itinéraires sur la base de l’URL. Cependant, le trafic médiatique de Teams n'est pas associé à une URL, le contrôle du routage de ce trafic doit donc être effectué à l'aide de sous-réseaux IP.

Dans certains scénarios, souvent non liés à la configuration du client Teams, le trafic multimédia traverse également le tunnel VPN, même lorsque les itinéraires corrects sont en place. Si vous rencontrez ce scénario, l’utilisation d’une règle de pare-feu pour empêcher les sous-réseaux ou ports IP Teams d’utiliser le VPN doit suffire.

>[!IMPORTANT]
>Pour vous assurer que le trafic multimédia Teams est acheminé via la méthode souhaitée dans tous les scénarios VPN, vérifiez que les utilisateurs exécutent la version **1.3.00.13565** ou ultérieure du client Microsoft Teams. Cette version inclut des améliorations dans la façon dont le client détecte les chemins d’accès réseau disponibles.

Le trafic de signalisation est effectué sur HTTPS et n’est pas aussi sensible à la latence que le trafic multimédia et est marqué comme **Autorisé** dans les données URL/IP et peut donc être routée en toute sécurité via le client VPN si vous le souhaitez.

>[!NOTE]
>Microsoft Edge **96 et versions ultérieures** prend également en charge le tunneling fractionné VPN pour le trafic d’égal à égal. Cela signifie que les clients peuvent tirer parti du tunneling fractionné VPN pour les clients web Teams sur Edge, par exemple. Les clients qui souhaitent la configurer pour les sites web s’exécutant sur Edge peuvent y parvenir en effectuant l’étape supplémentaire de désactivation de la stratégie Edge [WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) .

### <a name="security"></a>Sécurité

Un argument courant pour éviter les tunnels fractionnés est qu’il est moins sécurisé de le faire, c’est-à-dire Tout trafic qui ne passe pas par le tunnel VPN ne bénéficiera d’aucun schéma de chiffrement appliqué au tunnel VPN et est donc moins sécurisé.

L’argument de compteur principal permet de faire en sorte que le trafic multimédia soit déjà chiffré via _SRTP (Protocole de transport sécurisé en temps réel)_, un profil de protocole RTP (Protocole de transport en temps réel) qui assure la confidentialité, l’authentification et la protection contre les attaques contre le trafic RTP. SRTP lui-même utilise une clé de session générée de façon aléatoire, qui est échangée via le canal de signalement sécurisé TLS. Celui-ci sont décrites en détail dans [Ce guide de sécurité](/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online), mais la section principale est consacrée au chiffrement de médias.

Le trafic multimédia est chiffré à l’aide de SRTP, qui utilise une clé de session générée par un générateur de nombres aléatoires sécurisés et échangées à l’aide du canal TLS de signalisation. De plus, le flux de contenu entrant dans les deux directions entre le serveur de médiation et son saut interne suivant est également chiffré à l’aide de SRTP.

Skype Entreprise Online génère les noms d’utilisateur et les mots de passe pour sécuriser l’accès aux relais de contenu par le biais de _Traverser à l’aide de relais autour de NAT (TURN)_. Les relais de média échangent le nom d’utilisateur/mot de passe sur un canal SIP sécurisé par TLS. Il est important de noter que même si un tunnel VPN peut être utilisé pour connecter le client au réseau d’entreprise, le trafic doit toujours circuler sous sa forme SRTP lorsqu’il quitte le réseau d’entreprise pour atteindre le service.

Vous trouverez des informations sur la façon dont Teams atténue les problèmes de sécurité courants tels que les utilitaires vocaux ou les utilitaires de traversée de session pour les attaques d’amplification _NAT (STUN)_ dans [la version 5.1 Considérations sur la sécurité des implémenteurs](/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c).

Vous pouvez également consulter des informations sur les contrôles de sécurité modernes dans les scénarios de travail à distance sur [Autres méthodes pour les professionnels de la sécurité et l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance uniques d’aujourd’hui (blog de l’équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

### <a name="testing"></a>Tests

Une fois la stratégie en place, vous devez confirmer qu’elle fonctionne comme prévu. Plusieurs méthodes s’offrent à vous pour tester que le chemin d’accès est correctement configuré pour utiliser la connexion Internet locale :

- Exécutez le [test de connectivité Microsoft 365](https://aka.ms/netonboard) qui exécutera des tests de connectivité pour vous, y compris les itinéraires de trace comme ci-dessus. Nous ajoutons également des tests VPN à ces outils qui doivent également fournir des insights supplémentaires.

- Un **suivi** simple d’un point de terminaison dans l’étendue du tunnel fractionné doit afficher le chemin d’accès pris, par exemple :

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  Vous devez ensuite voir un chemin d’accès via le fournisseur de services Internet local vers ce point de terminaison qui doit être résolu en adresse IP dans les plages Teams que nous avons configurées pour le tunneling fractionné.

- Prenez une capture réseau à l’aide d’un outil tel que Wireshark. Filtrez sur le protocole UDP pendant un appel et le trafic s'acheminera vers une adresse IP dans la plage **Optimiser** Teams. Si le tunnel VPN est utilisé pour ce trafic, le trafic multimédia n’est pas visible dans la trace.

## <a name="additional-support-logs"></a>Journaux de support supplémentaires

Si vous avez besoin de données supplémentaires pour résoudre les problèmes, ou si vous demandez l’aide du support technique Microsoft, vous pouvez obtenir les informations suivantes afin de vous permettre d’accélérer la recherche d’une solution. L’ensemble d’outils de script de résolution des **problèmes universels basé sur TSS Windows CMD** du support Microsoft peut vous aider à collecter les journaux pertinents de manière simple. L’outil et les instructions sur l’utilisation se trouvent à l’adresse <https://aka.ms/TssTools>.

## <a name="related-articles"></a>Articles connexes

[Vue d’ensemble : tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Scénarios courants de tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Considérations spéciales sur les événements stream et en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md)

[Optimisation des performances de Microsoft 365 pour les utilisateurs chinois](microsoft-365-networking-china.md)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Optimisation des performances et du réseau Microsoft 365](network-planning-and-performance.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Réseau mondial Microsoft](/azure/networking/microsoft-global-network)
