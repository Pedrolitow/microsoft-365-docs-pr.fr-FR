---
title: Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN
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
f1.keywords:
- NOCSH
description: Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN
ms.openlocfilehash: 0f16ed8f7f9721a79375f05f7b889bc8aab2d824
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330858"
---
# <a name="securing-teams-media-traffic-for-vpn-split-tunneling"></a>Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN

>[!NOTE]
>Cet article fait partie d’un ensemble d’articles qui traitent Microsoft 365'optimisation des utilisateurs distants.

>- Pour une vue d’ensemble de l’utilisation de la tunneling fractionnement VPN pour optimiser la connectivité Microsoft 365 pour les utilisateurs distants, voir Vue d’ensemble : [tunneling fractionnel VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Pour obtenir des instructions détaillées sur l’implémentation de la tunneling fractionnement VPN, voir [Implementing VPN split tunneling for Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Pour obtenir la liste détaillée des scénarios de tunneling fractionnement VPN, voir [Scénarios courants de tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Pour plus d’informations sur la configuration de Stream et d’événements en direct dans les environnements VPN, voir Considérations spéciales pour Stream et les [événements en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md).
>- Pour plus d’informations sur l’optimisation Microsoft 365 performances des clients internationaux pour les utilisateurs en Chine, voir Microsoft 365 [optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md).

Certains administrateurs Microsoft Teams peuvent avoir besoin d’informations détaillées sur le fonctionnement des flux d’appels dans Teams à l’aide d’un modèle de tunneling fractionnel et sur la façon dont les connexions sont sécurisées.

## <a name="configuration"></a>Configuration

Pour les appels et les réunions, tant que les sous-réseaux IP Optimiser pour les médias Teams sont correctement en place dans la table d’itinéraires, lorsque Teams appelle la fonction [GetBestRoute](/windows/win32/api/iphlpapi/nf-iphlpapi-getbestroute) pour déterminer l’interface locale qui correspond à l’itinéraire qu’il doit utiliser pour une destination particulière, l’interface locale est renvoyée pour les destinations Microsoft dans les blocs IP Microsoft répertoriés ci-dessus.

Certains logiciels clients VPN autorisent la manipulation des itinéraires sur la base de l’URL. Cependant, le trafic médiatique de Teams n'est pas associé à une URL, le contrôle du routage de ce trafic doit donc être effectué à l'aide de sous-réseaux IP.

Dans certains scénarios, souvent non liés à la configuration du client Teams, le trafic multimédia traverse également le tunnel VPN, même lorsque les itinéraires corrects sont en place. Si vous rencontrez ce scénario, l’utilisation d’une règle de pare-feu pour empêcher les Teams ou les ports IP d’utiliser le VPN devrait suffire.

>[!IMPORTANT]
>Pour vous assurer que le trafic multimédia Teams est acheminé via la méthode souhaitée dans tous les scénarios VPN, assurez-vous que les utilisateurs exécutent Microsoft Teams client version **1.3.00.13565** ou supérieure. Cette version inclut des améliorations dans la façon dont le client détecte les chemins d’accès réseau disponibles.

Le trafic de signalisation est effectué sur HTTPS et n’est pas aussi sensible à la latence que le trafic multimédia et  est marqué comme Autoriser dans les données URL/IP et peut donc être acheminé en toute sécurité via le client VPN si vous le souhaitez.

>[!NOTE]
>Microsoft Edge **96 et** supérieures prend également en charge la tunneling fractionnée VPN pour le trafic pair à pair. Cela signifie que les clients peuvent tirer parti de la tunneling fractionnement VPN pour Teams clients web sur Edge, par exemple. Les clients qui souhaitent la configurer pour les sites web qui s’exécutent sur Edge peuvent y parvenir en prenant l’étape supplémentaire d’activation de la stratégie [Edge WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) .

### <a name="security"></a>Sécurité

L’un des arguments courants pour éviter les tunnelages fractionnements est le fait qu’il est moins sécurisé de le faire, c’est-à-dire Tout trafic qui ne passe pas par le tunnel VPN ne bénéficiera d’aucun schéma de chiffrement appliqué au tunnel VPN et sera donc moins sécurisé.

L’argument de compteur principal permet de faire en sorte que le trafic multimédia soit déjà chiffré via _SRTP (Protocole de transport sécurisé en temps réel)_, un profil de protocole RTP (Protocole de transport en temps réel) qui assure la confidentialité, l’authentification et la protection contre les attaques contre le trafic RTP. SRTP lui-même utilise une clé de session générée de façon aléatoire, qui est échangée via le canal de signalement sécurisé TLS. Celui-ci sont décrites en détail dans [Ce guide de sécurité](/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online), mais la section principale est consacrée au chiffrement de médias.

Le trafic multimédia est chiffré à l’aide de SRTP, qui utilise une clé de session générée par un générateur de nombres aléatoires sécurisés et échangées à l’aide du canal TLS de signalisation. De plus, le flux de contenu entrant dans les deux directions entre le serveur de médiation et son saut interne suivant est également chiffré à l’aide de SRTP.

Skype Entreprise Online génère les noms d’utilisateur et les mots de passe pour sécuriser l’accès aux relais de contenu par le biais de _Traverser à l’aide de relais autour de NAT (TURN)_. Les relais de média échangent le nom d’utilisateur/mot de passe sur un canal SIP sécurisé par TLS. Il est important de noter que même si un tunnel VPN peut être utilisé pour connecter le client au réseau d’entreprise, le trafic doit toujours circuler sous sa forme SRTP lorsqu’il quitte le réseau d’entreprise pour atteindre le service.

Des informations sur la façon dont Teams atténue les problèmes de sécurité courants tels que les utilitaires de voix ou de traversée de session pour les attaques d’amplification _NAT (STUN)_ sont disponibles dans [5.1 Security Considerations for Implementers](/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c).

Vous pouvez également consulter des informations sur les contrôles de sécurité modernes dans les scénarios de travail à distance sur [Autres méthodes pour les professionnels de la sécurité et l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance uniques d’aujourd’hui (blog de l’équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

### <a name="testing"></a>Tests

Une fois la stratégie en place, vous devez vérifier qu’elle fonctionne comme prévu. Plusieurs méthodes s’offrent à vous pour tester que le chemin d’accès est correctement configuré pour utiliser la connexion Internet locale :

- Exécutez le [test Microsoft 365 de](https://aka.ms/netonboard) connectivité qui exécutera pour vous des tests de connectivité, y compris des itinéraires de suivi comme ci-dessus. Nous ajoutons également dans cet outil des tests VPN qui doivent également fournir des informations supplémentaires.

- Un simple **tracert vers un** point de terminaison dans l’étendue du tunnel partagé doit afficher le chemin d’accès pris, par exemple :

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  Vous devriez ensuite voir un chemin d’accès via le isp local à ce point de terminaison qui doit résoudre une adresse IP dans les plages Teams que nous avons configurées pour la tunnellation fractionner.

- Prenez une capture réseau à l’aide d’un outil tel que Wireshark. Filtrez sur le protocole UDP pendant un appel et le trafic s'acheminera vers une adresse IP dans la plage **Optimiser** Teams. Si le tunnel VPN est utilisé pour ce trafic, le trafic multimédia n’est pas visible dans le suivi.

## <a name="additional-support-logs"></a>Journaux de support supplémentaires

Si vous avez besoin de données supplémentaires pour résoudre les problèmes, ou si vous demandez l’aide du support technique Microsoft, vous pouvez obtenir les informations suivantes afin de vous permettre d’accélérer la recherche d’une solution. Le jeu d’outils **TSS Windows script** de dépannage universel basé sur CMD du support Microsoft peut vous aider à collecter les journaux pertinents de manière simple. L’outil et les instructions d’utilisation sont à l’aide <https://aka.ms/TssTools>de .

## <a name="related-articles"></a>Articles connexes

[Vue d’ensemble : tunnel vpn partagé pour Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implémentation de la tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Scénarios courants de tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Considérations spéciales pour les flux et les événements en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Microsoft 365 réseau et l’optimisation des performances](network-planning-and-performance.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Réseau mondial Microsoft](/azure/networking/microsoft-global-network)
