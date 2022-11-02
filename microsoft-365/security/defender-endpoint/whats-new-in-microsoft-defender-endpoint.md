---
title: Nouveautés dans Microsoft Defender pour point de terminaison
description: Découvrez les fonctionnalités généralement disponibles dans la dernière version de Microsoft Defender pour point de terminaison et les fonctionnalités de sécurité dans Windows 10 et Windows Server.
keywords: nouveautés de Microsoft Defender pour point de terminaison, disponibilité générale, fonctionnalités, disponible, nouveau
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
ms.date: 11/01/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 656ed58f84657b76a8b923582fff7cf27a786c87
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68815570"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint"></a>Nouveautés dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Les fonctionnalités suivantes sont en préversion ou en disponibilité générale dans la dernière version de Microsoft Defender pour point de terminaison.

Pour plus d’informations sur les fonctionnalités en préversion, consultez [Fonctionnalités en préversion](preview.md).

> [!TIP]
> Flux RSS : recevez une notification lorsque cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux :
>
> ```https
> https://learn.microsoft.com/api/search/rss?search=%22features+are+generally+available+%28GA%29+in+the+latest+release+of+Microsoft+Defender+for+Endpoint%22&locale=en-us&facet=
> ```

Pour plus d’informations sur les nouveautés de Microsoft Defender pour point de terminaison sur Windows, consultez : [Nouveautés de Microsoft Defender pour point de terminaison sur Windows](windows-whatsnew.md)

Pour plus d’informations sur les nouveautés des autres produits de sécurité Microsoft Defender, consultez :

- [Nouveautés de Microsoft 365 Defender](../defender/whats-new.md)
- [Nouveautés de Microsoft Defender pour Office 365](../office-365-security/whats-new-in-defender-for-office-365.md)
- [Nouveautés de Microsoft Defender pour Identity](/defender-for-identity/whats-new)
- [Nouveautés de Microsoft Defender for Cloud Apps](/cloud-app-security/release-notes)

Pour plus d’informations sur Microsoft Defender pour point de terminaison sur des systèmes d’exploitation spécifiques :

- [Nouveautés de Defender pour point de terminaison sur Windows](windows-whatsnew.md)
- [Nouveautés de Defender pour point de terminaison sur macOS](mac-whatsnew.md)
- [Nouveautés de Defender pour point de terminaison sur iOS](ios-whatsnew.md)
- [Nouveautés de Defender pour point de terminaison sur Linux](linux-whatsnew.md)

## <a name="october-2022"></a>Octobre 2022

- [La détection et la correction de la protection réseau C2 sont désormais en disponibilité générale](network-protection.md#block-command-and-control-attacks). <br/>Les attaquants compromettent souvent les serveurs connectés à Internet existants pour devenir leurs serveurs de commande et de contrôle. Les attaquants peuvent utiliser les serveurs compromis pour masquer le trafic malveillant et déployer des bots malveillants utilisés pour infecter des points de terminaison. La détection et la correction de la protection réseau aideront à améliorer le temps nécessaire aux équipes d’opérations de sécurité (SecOps) pour identifier et répondre aux menaces réseau malveillantes qui cherchent à compromettre des points de terminaison.


## <a name="september-2022"></a>Septembre 2022

- [Le rapport sur les règles de réduction de la surface d’attaque (ASR) est désormais disponible dans le portail Microsoft 365 Defender](attack-surface-reduction-rules-report.md). <br/>Le rapport sur les règles de réduction de la surface d’attaque (ASR) est désormais disponible dans le portail Microsoft 365 Defender. Ce rapport ASR fournit des informations sur les règles de réduction de la surface d’attaque appliquées aux appareils de votre organisation et vous aide à détecter les menaces, à bloquer les menaces potentielles et à obtenir une visibilité sur l’ASR et la configuration des appareils.

- [La protection intégrée](built-in-protection.md) (préversion) est en cours de déploiement. La protection intégrée est un ensemble de paramètres par défaut, tels que la protection contre les falsifications activée, pour aider à protéger les appareils contre les rançongiciels et d’autres menaces.

- [Les rapports d’intégrité de l’appareil sont désormais en disponibilité générale](device-health-reports.md). <br/>Le rapport d’intégrité de l’appareil fournit des informations sur l’intégrité et la sécurité de vos points de terminaison. Le rapport inclut des informations de tendance montrant l’état d’intégrité du capteur, l’état de l’antivirus, les plateformes de système d’exploitation, les versions Windows 10 et Microsoft Defender versions de mise à jour de l’antivirus.

- [Les rapports d’intégrité des appareils sont désormais disponibles pour les clients du gouvernement des États-Unis à l’aide de Defender pour point de terminaison](device-health-reports.md). <br/>Les rapports d’intégrité des appareils sont désormais disponibles pour les clients GCC, GCC High et DoD.

- [Le mode résolution des problèmes](enable-troubleshooting-mode.md) est désormais disponible pour d’autres systèmes d’exploitation Windows, y compris Windows Server 2012 R2 et versions ultérieures. Consultez l’article pour plus d’informations sur les mises à jour requises.

## <a name="august-2022"></a>Août 2022

- [État d’intégrité de l’appareil](investigate-machines.md#device-health-status)<br>La carte État d’intégrité de l’appareil affiche un rapport d’intégrité résumé pour l’appareil spécifique.
- [Rapports d’intégrité des appareils (préversion)](/microsoft-365/security/defender-endpoint/machine-reports)<br> Le rapport d’état des appareils fournit des informations générales sur les appareils de votre organisation. Le rapport inclut des informations de tendance montrant l’état d’intégrité du capteur, l’état de l’antivirus, les plateformes de système d’exploitation et les versions Windows 10.
- [La protection contre les falsifications sur macOS est désormais en disponibilité générale](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/tamper-protection-on-macos-is-now-generally-available/ba-p/3595422)<br> Cette fonctionnalité sera publiée avec le mode d’audit activé par défaut, et vous pouvez décider d’appliquer (bloquer) ou de désactiver la fonctionnalité. Plus tard cette année, nous proposerons un mécanisme de déploiement progressif qui basculera automatiquement les points de terminaison en mode bloc; Notez que cela s’applique uniquement si vous n’avez pas choisi d’activer (mode bloquer) ou de désactiver la fonctionnalité.
- [La protection réseau et la protection web pour macOS et Linux sont désormais en préversion publique !](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/network-protection-and-web-protection-for-macos-and-linux-is-now/ba-p/3601576)<br>La protection réseau permet de réduire la surface d’attaque de vos appareils à partir d’événements Basés sur Internet. Il empêche les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux susceptibles d’héberger des escroqueries par hameçonnage, des attaques et d’autres contenus malveillants sur Internet. Il s’agit de la base sur laquelle repose notre protection web pour Microsoft Defender pour point de terminaison. Ces fonctionnalités incluent la protection contre les menaces web, le filtrage de contenu web et les indicateurs personnalisés IP/URL. La protection web vous permet de sécuriser vos appareils contre les menaces web et de réglementer le contenu indésirable.
- [Intégration améliorée Microsoft Defender pour point de terminaison (MDE) pour Windows Server 2012 R2 et Windows Server 2016](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2207#improved-microsoft-defender-for-endpoint-mde-onboarding-for-windows-server-2012-r2-and-windows-server-2016)<br>Configuration Manager version 2207 prend désormais en charge le déploiement automatique de Microsoft Defender pour point de terminaison modernes et unifiés pour Windows Server 2012 R2 & 2016. les appareils Windows Server 2012 et 2016 qui sont ciblés avec Microsoft Defender pour point de terminaison stratégie d’intégration utilisent l’agent unifié par rapport à la solution microsoft Monitoring Agent existante, s’ils sont configurés via les paramètres client.


## <a name="july-2022"></a>Juillet 2022
- [Ajouter des appareils de contrôleur de domaine - Amélioration du labo d’évaluation](evaluation-lab.md#add-a-domain-controller)<br>Désormais en disponibilité générale : ajoutez un contrôleur de domaine pour exécuter des scénarios complexes tels que le mouvement latéral et les attaques multiphases sur plusieurs appareils.
- [Annonce des améliorations apportées à la page Fichier dans Microsoft Defender pour point de terminaison](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-file-page-enhancements-in-microsoft-defender-for/ba-p/3584004)<br>Avez-vous déjà enquêté sur des fichiers dans Microsoft Defender pour point de terminaison ? Nous rendons désormais les choses encore plus faciles avec notre annonce récente d’améliorations apportées à la page Fichier et au panneau latéral. Les utilisateurs peuvent désormais simplifier les processus en offrant une expérience de navigation plus efficace qui héberge toutes ces informations au même endroit.
- [Présentation de la nouvelle expérience de suppression d’alerte](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/introducing-the-new-alert-suppression-experience/ba-p/3562719)<br>Nous sommes ravis de partager la nouvelle expérience de suppression d’alertes avancée qui est désormais en disponibilité générale. La nouvelle expérience offre une granularité et un contrôle plus stricts, ce qui permet aux utilisateurs de régler Microsoft Defender pour point de terminaison alertes.
- [Empêcher les appareils non gérés compromis de se déplacer latéralement dans votre organisation avec « Contenir »](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/prevent-compromised-unmanaged-devices-from-moving-laterally-in/ba-p/3482134)<br>À compter d’aujourd’hui, lorsqu’un appareil qui n’est pas inscrit dans Microsoft Defender pour point de terminaison est soupçonné d’être compromis, en tant qu’analyste SOC, vous serez en mesure de le « contenir ». Par conséquent, tout appareil inscrit dans Microsoft Defender pour point de terminaison bloque désormais toute communication entrante/sortante avec l’appareil suspect.
- [La prise en charge des appareils mobiles est désormais disponible pour les clients du gouvernement des États-Unis à l’aide de Defender pour point de terminaison](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/mobile-device-support-is-now-available-for-us-government/ba-p/3472590)<br>Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis est conçu dans l’environnement Azure US Government et utilise les mêmes technologies sous-jacentes que Defender dans Azure Commercial. Cette offre est disponible pour les clients GCC, GCC High et DoD et étend la disponibilité de notre plateforme de Windows, macOS et Linux aux appareils Android et iOS.


## <a name="june-2022"></a>Juin 2022
- [Defender pour serveurs Plan 2 s’intègre désormais à la solution unifiée MDE](https://techcommunity.microsoft.com/t5/microsoft-defender-for-cloud/defender-for-servers-plan-2-now-integrates-with-mde-unified/ba-p/3527534)<br>Vous pouvez maintenant commencer à déployer la solution moderne et unifiée pour Windows Server 2012 R2 et 2016 sur les serveurs couverts par Defender pour serveurs Plan 2 à l’aide d’un seul bouton.
- [Protection du réseau mobile dans Microsoft Defender pour point de terminaison sur Android & iOS désormais en préversion publique](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/mobile-network-protection-in-microsoft-defender-for-endpoint-on/ba-p/3559121)<br>Microsoft offre une fonctionnalité de protection de réseau mobile dans Defender pour point de terminaison qui permet aux organisations d’identifier, d’évaluer et de corriger les faiblesses des points de terminaison à l’aide de renseignements robustes sur les menaces. Nous sommes ravis d’annoncer que les utilisateurs peuvent désormais tirer parti de cette nouvelle fonctionnalité sur les plateformes Android et iOS avec Microsoft Defender pour point de terminaison.

## <a name="may-2022"></a>Mai 2022
- [Protection contre les falsifications pour macOS (préversion)](tamperprotection-macos.md)<br>La protection contre les falsifications permet d’empêcher la suppression non autorisée de Microsoft Defender pour point de terminaison sur macOS.
- [Ajouter des appareils de contrôleur de domaine - Amélioration du labo d’évaluation (préversion)](evaluation-lab.md#add-a-domain-controller)<br>Ajoutez un contrôleur de domaine pour exécuter des scénarios complexes tels que le mouvement latéral et les attaques multiphases sur plusieurs appareils.
- [Mode de résolution des problèmes pour Microsoft Defender pour point de terminaison désormais en disponibilité générale](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/troubleshooting-mode-for-microsoft-defender-for-endpoint-now/ba-p/3347344)<br>Présentation du mode de résolution des problèmes, un moyen unique, innovant et sécurisé d’examiner et d’ajuster les configurations sur vos appareils. Ce mode permet à l’administrateur local sur l’appareil de remplacer Microsoft Defender configurations de stratégie de sécurité antivirus sur l’appareil, y compris la protection contre les falsifications. 
- [Annonce de la préversion publique du profil personnel Defender pour point de terminaison pour Android Enterprise](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-the-public-preview-of-defender-for-endpoint-personal/ba-p/3370979)<br>Nous sommes heureux d’annoncer que les utilisateurs qui souhaitent inscrire leurs propres appareils dans le programme BYOD de leur lieu de travail peuvent désormais bénéficier de la protection fournie par Microsoft Defender pour point de terminaison dans leur profil personnel.
- [La gestion des paramètres de sécurité dans Microsoft Defender pour point de terminaison est désormais en disponibilité générale](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/security-settings-management-in-microsoft-defender-for-endpoint/ba-p/3356970)<br>Fin 2021, nous avons annoncé que Microsoft Defender pour point de terminaison étendait ses fonctionnalités de gestion de la configuration. Cette version a permis aux équipes de sécurité de configurer les appareils avec les paramètres de sécurité souhaités sans avoir à déployer et à implémenter d’autres outils ou infrastructures.  Grâce à Microsoft Endpoint Manager, les organisations ont pu gérer les stratégies antivirus (AV), EDR (Endpoint Detection and Response) et FW (Endpoint Detection and Response) à partir d’une vue unique pour tous les appareils inscrits. Aujourd’hui, nous annonçons que cette fonctionnalité est désormais en disponibilité générale pour le client Windows et le serveur Windows, prenant en charge Windows 10, Windows 11 et Windows Server 2012 R2 ou version ultérieure.

## <a name="april-2022"></a>Avril 2022
- [Mise à jour de l’intégration et de la parité des fonctionnalités pour Windows Server 2012 R2 et Windows Server 2016)](configure-server-endpoints.md)<br/> Le nouveau package de solution unifiée est désormais en disponibilité générale et facilite l’intégration des serveurs en supprimant les dépendances et les étapes d’installation. En outre, ce package de solution unifiée est fourni avec de nombreuses nouvelles améliorations de fonctionnalités.
- [Intégration à Tunnel pour iOS](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/what-s-new-in-microsoft-endpoint-manager-2204-april-edition/ba-p/3297995). Microsoft Defender pour point de terminaison sur iOS peuvent désormais s’intégrer à Microsoft Tunnel, une solution de passerelle VPN pour activer la sécurité et la connectivité dans une seule application. Cette fonctionnalité était auparavant disponible uniquement sur Android.
- [Protection renforcée contre les programmes malveillants dans Microsoft Defender pour point de terminaison Android](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/enhanced-antimalware-protection-in-microsoft-defender-for/ba-p/3290320)<br>Nous sommes ravis de partager les mises à jour majeures des fonctionnalités de protection contre les programmes malveillants de Microsoft Defender pour point de terminaison sur Android. Ces nouvelles fonctionnalités constituent un composant majeur de votre protection de nouvelle génération dans Microsoft Defender pour point de terminaison. Cette protection regroupe le Machine Learning, l’analyse du Big Data, la recherche approfondie des menaces et l’infrastructure cloud Microsoft pour protéger les appareils (ou points de terminaison) Android de votre organisation.
- [Fonctionnalités améliorées du moteur anti-programme malveillant pour Linux et macOS](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/enhanced-antimalware-engine-capabilities-for-linux-and-macos/ba-p/3292003)<br>Nous annonçons une mise à niveau significative de notre protection nouvelle génération sur Linux et macOS avec un nouveau moteur amélioré. Le moteur anti-programme malveillant Microsoft Defender Antivirus est un composant clé de la protection nouvelle génération. Cette protection apporte le Machine Learning, l’analyse du Big Data, la recherche approfondie des menaces et l’infrastructure cloud Microsoft pour protéger les appareils (ou points de terminaison) de votre organisation. Les principaux avantages de cette mise à jour majeure incluent les améliorations des performances et de la prévention, ainsi que l’ajout de la prise en charge des indicateurs de fichiers personnalisés sur macOS et Linux.
- [Nouvelle fonctionnalité de création de rapports pour le contrôle d’appareil et le pare-feu Windows Defender](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/new-reporting-functionality-for-device-control-and-windows/ba-p/3290601)<br>Nous sommes ravis d’annoncer les nouvelles fonctionnalités de création de rapports de point de terminaison dans le portail Microsoft 365 Defender. Ce travail réunit de nouveaux rapports de point de terminaison afin que vous puissiez voir ce qui se passe dans votre environnement en quelques clics. Nos rapports sont conçus pour fournir des informations sur le comportement et l’activité des appareils tout en vous permettant de tirer pleinement parti des expériences intégrées dans Microsoft 365 Defender portail, telles que la chronologie des appareils et la chasse avancée.
- [Les soumissions unifiées dans Microsoft 365 Defender désormais en disponibilité générale !](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/unified-submissions-in-microsoft-365-defender-now-generally/ba-p/3270770)<br>Votre équipe de sécurité dispose désormais d’un « guichet unique » pour l’envoi d’e-mails, d’URL, de pièces jointes et de fichiers dans une expérience de soumission simple à utiliser. Pour simplifier le processus de soumission, nous sommes ravis d’annoncer une nouvelle expérience de soumission unifiée dans le portail Microsoft 365 Defender (https://security.microsoft.com). Avec les soumissions unifiées, vous pouvez envoyer des fichiers à Microsoft 365 Defender pour révision à partir du portail. Nous ajoutons également la possibilité d’envoyer un fichier directement à partir d’une page d’alerte Microsoft Defender pour point de terminaison.  
- [Annonce d’une prise en charge et d’une fonctionnalité étendues pour les API Live Response](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-expanded-support-and-functionality-for-live-response/ba-p/3178432)<br>Nous sommes heureux de partager que nous continuons à étendre la prise en charge des API existantes sur toutes nos plateformes prises en charge dans Microsoft Defender pour point de terminaison, en plus d’en annoncer de nouvelles qui permettront de simplifier et d’améliorer l’automatisation et l’orchestration des réponses de l’organisation.

## <a name="february-2022"></a>Février 2022

- [Le module complémentaire Splunk pour Microsoft Security est désormais disponible](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/the-splunk-add-on-for-microsoft-security-is-now-available/ba-p/3171272)<br>Nous sommes heureux de vous dire que le module complémentaire Splunk pris en charge par Splunk pour la sécurité Microsoft est désormais disponible. Ce module complémentaire s’appuie sur le module complémentaire Microsoft 365 Defender pour Splunk 1.3.0 et mappe les propriétés de l’API Microsoft Defender pour point de terminaison Alerts ou les propriétés de l’API Microsoft 365 Defender Incidents sur le modèle CIM (Common Information Model) de Splunk.
- [Dépréciation de l’API SIEM héritée - Report](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/deprecating-the-legacy-siem-api-postponed/ba-p/3139643)<br>Nous avons précédemment annoncé que l’API REST SIEM serait déconseillée le 01/04/2022. Nous avons écouté les commentaires des clients et la dépréciation de l’API a été reportée pour l’instant, plus de détails attendus au 3e trimestre 2022. Nous sommes impatients de partager des détails passionnants sur les API Microsoft 365 Defender dans Microsoft Graph au 3e trimestre 2022.

## <a name="january-2022"></a>Janvier 2022

- [La gestion des vulnérabilités pour Android et iOS est désormais en disponibilité générale](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663)<br>Avec cette nouvelle couverture multiplateforme, les fonctionnalités Gestion des menaces et des vulnérabilités prennent désormais en charge toutes les principales plateformes d’appareils au sein de l’organisation, qui couvrent les stations de travail, les serveurs et les appareils mobiles. 
- [Microsoft Defender pour point de terminaison Plan 1 désormais inclus dans les licences Microsoft 365 E3/A3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-for-endpoint-plan-1-now-included-in-m365-e3/ba-p/3060639)<br>À compter du 14 janvier, Microsoft Defender pour point de terminaison Plan 1 (P1) sera automatiquement inclus dans les licences Microsoft 365 E3/A3.
- [Intégration sans contact de Microsoft Defender pour point de terminaison sur iOS désormais en préversion publique](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/zero-touch-onboarding-of-microsoft-defender-for-endpoint-on-ios/ba-p/3038045)<br>Avec cette nouvelle fonctionnalité, les entreprises peuvent désormais déployer des Microsoft Defender pour point de terminaison sur des appareils iOS inscrits automatiquement auprès de Microsoft Endpoint Manager, sans que les utilisateurs finaux n’aient besoin d’interagir avec l’application. Cela facilite les frictions de déploiement et réduit considérablement le temps nécessaire pour déployer l’application sur tous les appareils, car Microsoft Defender pour point de terminaison est activé en mode silencieux sur les appareils ciblés et commence à protéger votre patrimoine iOS.

## <a name="december-2021"></a>Décembre 2021

- [Gestion des vulnérabilités Microsoft Defender peuvent aider à identifier les vulnérabilités log4j dans les applications et les composants](https://www.microsoft.com/security/blog/2021/12/11/guidance-for-preventing-detecting-and-hunting-for-cve-2021-44228-log4j-2-exploitation/#TVM)<br>La gestion des menaces et des vulnérabilités identifie automatiquement et en toute transparence les appareils affectés par les vulnérabilités Log4j et le risque associé dans l’environnement, et réduit considérablement le délai d’atténuation. Microsoft continue d’itérer sur ces fonctionnalités en fonction des dernières informations du paysage des menaces.
- Découvrir des appareils IoT (préversion) : la [découverte](device-discovery.md) d’appareils peut désormais vous aider à trouver des appareils IoT non gérés connectés à votre réseau d’entreprise. Cela vous donne une vue unifiée de votre inventaire IoT avec le reste de vos appareils informatiques (stations de travail, serveurs et mobiles).
- [Microsoft Defender pour l’intégration IoT (préversion)](enable-microsoft-defender-for-iot-integration.md) : cette intégration améliore vos fonctionnalités de découverte d’appareils avec les fonctionnalités de surveillance sans agent fournies par Microsoft Defender pour IoT. Cela offre une visibilité accrue pour vous aider à localiser, identifier et sécuriser les appareils IoT dans votre réseau.

## <a name="november-2021"></a>Novembre 2021

- [Gestion de la configuration de la sécurité](security-config-management.md) <br/> Fonctionnalité permettant aux appareils qui ne sont pas gérés par Microsoft Endpoint Manager, Microsoft Intune ou Microsoft Endpoint Configuration Manager, de recevoir des configurations de sécurité pour Microsoft Defender directement à partir d’Endpoint Manager.
- [Labo d’évaluation : Prise en charge étendue du système d’exploitation & simulations Atomic Red Team](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/evaluation-lab-expanded-os-support-amp-atomic-red-team/ba-p/2993927)<br>Le laboratoire d’évaluation prend désormais en charge l’ajout d’appareils Windows 11, Windows Server 2016 et Linux. En outre, nous aimerions également annoncer un nouveau partenariat avec la bibliothèque de simulation open source de Red Canary, Atomic Red Team!
- [Annonce de la préversion publique de Microsoft Defender pour point de terminaison Mobile - Protection contre les falsifications](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-the-public-preview-of-microsoft-defender-for-endpoint/ba-p/2971038)<br>Marquer un appareil non conforme après sept jours d’inactivité dans l’application mobile Microsoft Defender pour point de terminaison.
- [Renforcer la protection de votre patrimoine Linux avec la surveillance du comportement, la couverture de distribution étendue et bien plus encore](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/boost-protection-of-your-linux-estate-with-behavior-monitoring/ba-p/2909320)<br>Nous sommes ravis de partager les dernières actualités sur Microsoft Defender pour point de terminaison sur Linux nouvelle génération protection, détection de point de terminaison et réponse (EDR), Gestion des menaces et des vulnérabilités (TVM). La protection Microsoft pour votre patrimoine Linux bénéficie d’un coup de pouce impressionnant dans tout le spectre de la suite de sécurité. Avec les Microsoft Defender pour point de terminaison récentes sur l’intégration de Linux à Azure Security Center, les avantages de notre EDR et TVM Linux s’étendent désormais aux clients Azure Defender.

## <a name="october-2021"></a>Octobre 2021

- [Mise à jour de l’intégration et de la parité des fonctionnalités pour Windows Server 2012 R2 et Windows Server 2016 (préversion)](configure-server-endpoints.md)<br/> Le nouveau package de solution unifiée facilite l’intégration des serveurs en supprimant les dépendances et les étapes d’installation. En outre, ce package de solution unifiée est fourni avec de nombreuses nouvelles améliorations de fonctionnalités.
- Windows 11 prise en charge ajoutée à Microsoft Defender pour point de terminaison et Microsoft 365 Defender.

## <a name="september-2021"></a>Septembre 2021

- [Filtrage du contenu web](web-content-filtering.md) <br/>Dans le cadre des fonctionnalités de protection web dans Microsoft Defender pour point de terminaison, le filtrage de contenu web permet à l’équipe de sécurité de votre organisation de suivre et de réglementer l’accès aux sites web en fonction de leurs catégories de contenu. Les catégories incluent le contenu pour adultes, la bande passante élevée, la responsabilité juridique, les loisirs et les non-catégories. Bien que de nombreux sites web qui appartiennent à une ou plusieurs de ces catégories ne soient pas malveillants, ils peuvent être problématiques en raison des réglementations de conformité, de l’utilisation de la bande passante ou d’autres problèmes. [En savoir plus sur le filtrage de contenu web](web-content-filtering.md).

## <a name="august-2021"></a>Août 2021

- (Préversion) [plan Microsoft Defender pour point de terminaison 1](defender-endpoint-plan-1.md) <br/>Defender pour point de terminaison Plan 1 (préversion) est une solution de protection de point de terminaison qui inclut la protection nouvelle génération, la réduction de la surface d’attaque, la gestion centralisée et la création de rapports, ainsi que les API. Defender pour point de terminaison Plan 1 (préversion) est une nouvelle offre destinée aux clients qui souhaitent essayer nos fonctionnalités de protection des points de terminaison, qui ont Microsoft 365 E3 et qui n’ont pas encore Microsoft 365 E5. 

   Pour en savoir plus, consultez [Microsoft Defender pour point de terminaison Plan 1 (préversion).](defender-endpoint-plan-1.md) Les fonctionnalités [existantes de Defender pour point de terminaison](microsoft-defender-endpoint.md) seront appelées Defender pour point de terminaison Plan 2. 
- (Préversion) [Filtrage de contenu web](web-content-filtering.md)<br>  Le filtrage de contenu web fait partie des fonctionnalités de protection web dans Microsoft Defender pour point de terminaison. Il permet à votre organisation de suivre et de réglementer l’accès aux sites web en fonction de leurs catégories de contenu. La plupart de ces sites web, bien qu’ils ne soient pas malveillants, peuvent être problématiques en raison des réglementations de conformité, de l’utilisation de la bande passante ou d’autres problèmes.

## <a name="july-2021"></a>Juillet 2021

- (Préversion) [Rapport de conformité et d’intégrité de l’appareil](device-health-reports.md) <br>  Le rapport d’intégrité et de conformité des appareils fournit des informations générales sur les appareils de votre organisation.

## <a name="june-2021"></a>Juin 2021

- [Évaluation des vulnérabilités logicielles d’exportation Delta](get-assessment-methods-properties.md#31-methods) Api <br> Ajout à la collection [d’API Exporter des évaluations des vulnérabilités et des configurations sécurisées](get-assessment-methods-properties.md) . <br> Contrairement à l’évaluation complète des vulnérabilités logicielles (réponse JSON), qui est utilisée pour obtenir un instantané complet de l’évaluation des vulnérabilités logicielles de votre organisation par appareil, l’appel d’API d’exportation delta est utilisé pour extraire uniquement les modifications qui se sont produites entre une date sélectionnée et la date actuelle (l’appel d’API « delta »). Au lieu d’obtenir une exportation complète avec une grande quantité de données à chaque fois, vous obtenez uniquement des informations spécifiques sur les vulnérabilités nouvelles, corrigées et mises à jour. L’appel d’API d’exportation Delta peut également être utilisé pour calculer différents indicateurs de performance clés, tels que « combien de vulnérabilités ont été corrigées » ou « combien de nouvelles vulnérabilités ont été ajoutées à une organisation ».
- [Exporter des évaluations des vulnérabilités et des configurations sécurisées](get-assessment-methods-properties.md) Api <br> Ajoute une collection d’API qui extrayent les données de Gestion des vulnérabilités Defender par appareil. Il existe différents appels d’API pour obtenir différents types de données : évaluation de la configuration sécurisée, évaluation de l’inventaire logiciel et évaluation des vulnérabilités logicielles. Chaque appel d’API contient les données requises pour les appareils de votre organisation.
- [Activité de correction](get-remediation-methods-properties.md) Api <br> Ajoute une collection d’API avec des réponses qui contiennent des activités de correction defender Vulnerability Management qui ont été créées dans votre locataire. Les types d’informations de réponse incluent une activité de correction par ID, toutes les activités de correction et les appareils exposés d’une activité de correction.
- [Découverte d’appareils](device-discovery.md) <br> Vous aide à trouver des appareils non gérés connectés à votre réseau d’entreprise sans avoir besoin d’appliances supplémentaires ou de modifications de processus fastidieuses. À l’aide d’appareils intégrés, vous pouvez trouver des appareils non gérés dans votre réseau et évaluer les vulnérabilités et les risques. Vous pouvez ensuite intégrer des appareils découverts pour réduire les risques associés à l’utilisation de points de terminaison non managés dans votre réseau.

   > [!IMPORTANT]
   > La découverte standard sera le mode par défaut pour tous les clients à partir du 19 juillet 2021. Vous pouvez choisir de conserver le mode de base via la page des paramètres.

- [Les définitions de groupe](/microsoft-365/security/defender-endpoint/machine-groups) d’appareils peuvent désormais inclure plusieurs valeurs pour chaque condition. Vous pouvez définir plusieurs étiquettes, noms d’appareils et domaines sur la définition d’un seul groupe d’appareils.
- [Prise en charge de la gestion des applications mobiles](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-new-capabilities-on-android-and-ios/ba-p/2442730) <br> Cette amélioration permet Microsoft Defender pour point de terminaison protéger les données d’une organisation au sein d’une application managée lorsque Intune est utilisé pour gérer des applications mobiles. Pour plus d’informations sur la gestion des applications mobiles, consultez [cette documentation](/mem/intune/apps/mam-faq).
- [Intégration du VPN Microsoft Tunnel](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-new-capabilities-on-android-and-ios/ba-p/2442730) <br> Les fonctionnalités VPN de Microsoft Tunnel sont désormais intégrées à Microsoft Defender pour point de terminaison’application pour Android. Cette unification permet aux organisations d’offrir une expérience utilisateur final simplifiée avec une seule application de sécurité, offrant à la fois la défense contre les menaces mobiles et la possibilité d’accéder aux ressources locales à partir de leur appareil mobile, tandis que les équipes de sécurité et informatiques sont en mesure de conserver les mêmes expériences d’administration qu’elles connaissent.
- [Détection de jailbreak sur iOS](/microsoft-365/security/defender-endpoint/ios-configure-features#conditional-access-with-defender-for-endpoint-on-ios) <br> La fonctionnalité de détection de jailbreak dans Microsoft Defender pour point de terminaison sur iOS est désormais en disponibilité générale. Cela s’ajoute à la protection contre l’hameçonnage qui existe déjà.  Pour plus d’informations, consultez [Configurer une stratégie d’accès conditionnel basée sur les signaux de risque de l’appareil](/microsoft-365/security/defender-endpoint/ios-configure-features).


## <a name="march-2021"></a>Mars 2021
- [Gérer la protection contre les falsifications pour votre organisation à l’aide Microsoft 365 Defender portail](manage-tamper-protection-microsoft-365-defender.md) <br> Vous pouvez gérer les paramètres de protection contre les falsifications sur Windows 10, Windows Server 2016, Windows Server 2019 et Windows Server 2022 à l’aide d’une méthode appelée *attachement de locataire*.


## <a name="january-2021"></a>Janvier 2021

- [Azure Virtual Desktop](https://azure.microsoft.com/services/virtual-desktop/) <br> Microsoft Defender pour point de terminaison prend désormais en charge Azure Virtual Desktop.
