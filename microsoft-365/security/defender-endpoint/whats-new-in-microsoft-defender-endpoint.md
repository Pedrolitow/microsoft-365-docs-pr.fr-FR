---
title: Nouveautés dans Microsoft Defender pour point de terminaison
description: Découvrez les fonctionnalités généralement disponibles dans la dernière version de Pertahanan Microsoft untuk Titik Akhir et les fonctionnalités de sécurité dans Windows 10 et Windows Server.
keywords: nouveautés de Pertahanan Microsoft untuk Titik Akhir, ga, généralement disponibles, fonctionnalités, disponibles, nouvelles
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
ms.date: 09/12/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 852677c02060e3c355ab15708b1be0a720fc5ed2
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67736031"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint"></a>Nouveautés dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Les fonctionnalités suivantes sont disponibles en préversion ou en disponibilité générale dans la dernière version de Pertahanan Microsoft untuk Titik Akhir.

Pour plus d’informations sur les fonctionnalités en préversion, consultez [Fonctionnalités en préversion](preview.md).

> [!TIP]
> Flux RSS : recevez une notification lorsque cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux :
>
> ```https
> https://docs.microsoft.com/api/search/rss?search=%22features+are+generally+available+%28GA%29+in+the+latest+release+of+Microsoft+Defender+for+Endpoint%22&locale=en-us&facet=
> ```

Pour plus d’informations sur les nouveautés des autres produits de sécurité Microsoft Defender, consultez :

- [Nouveautés de Microsoft 365 Defender](../defender/whats-new.md)
- [Nouveautés de Microsoft Defender pour Office 365](../office-365-security/whats-new-in-defender-for-office-365.md)
- [Nouveautés de Microsoft Defender pour Identity](/defender-for-identity/whats-new)
- [Nouveautés de Microsoft Defender for Cloud Apps](/cloud-app-security/release-notes)

Pour plus d’informations sur Pertahanan Microsoft untuk Titik Akhir sur d’autres systèmes d’exploitation :

- [Nouveautés de Defender pour point de terminaison sur macOS](mac-whatsnew.md)
- [Nouveautés de Defender pour point de terminaison sur iOS](ios-whatsnew.md)
- [Nouveautés de Defender pour point de terminaison sur Linux](linux-whatsnew.md)

## <a name="september-2022"></a>Septembre 2022

- [Les rapports d’intégrité des appareils sont désormais en disponibilité générale](device-health-reports.md). <br/>Le rapport d’intégrité des appareils fournit des informations sur l’intégrité et la sécurité de vos points de terminaison. Le rapport inclut des informations de tendance indiquant l’état d’intégrité du capteur, l’état de l’antivirus, les plateformes de système d’exploitation, les versions Windows 10 et les versions de mise à jour de l’antivirus Microsoft Defender.

- [Le mode de résolution des problèmes](enable-troubleshooting-mode.md) est désormais disponible pour d’autres systèmes d’exploitation Windows, notamment Windows Server 2012 R2 et versions ultérieures. Pour plus d’informations sur les mises à jour requises, consultez l’article.

## <a name="august-2022"></a>Août 2022

- [État d’intégrité de l’appareil](investigate-machines.md#device-health-status)<br>La carte d’état d’intégrité de l’appareil affiche un rapport d’intégrité résumé pour l’appareil spécifique.
- [Rapports d’intégrité des appareils (préversion)](/microsoft-365/security/defender-endpoint/machine-reports)<br> Le rapport d’état des appareils fournit des informations générales sur les appareils de votre organisation. Le rapport inclut des informations de tendance indiquant l’état d’intégrité du capteur, l’état antivirus, les plateformes de système d’exploitation et les versions Windows 10.
- [La protection contre les falsifications sur macOS est désormais en disponibilité générale](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/tamper-protection-on-macos-is-now-generally-available/ba-p/3595422)<br> Cette fonctionnalité sera publiée avec le mode d’audit activé par défaut, et vous pouvez décider s’il faut appliquer (bloquer) ou désactiver la fonctionnalité. Plus tard cette année, nous proposerons un mécanisme de déploiement progressif qui basculera automatiquement les points de terminaison en mode de blocage. Notez que cela ne s’applique que si vous n’avez pas choisi d’activer (mode bloc) ou de désactiver la fonctionnalité.
- [La protection réseau et la protection web pour macOS et Linux sont désormais en préversion publique !](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/network-protection-and-web-protection-for-macos-and-linux-is-now/ba-p/3601576)<br>La protection réseau permet de réduire la surface d’attaque de vos appareils à partir d’événements basés sur Internet. Il empêche les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux susceptibles d’héberger des escroqueries, des exploits et d’autres contenus malveillants sur Internet. C’est la base sur laquelle repose notre protection web pour Pertahanan Microsoft untuk Titik Akhir. Ces fonctionnalités incluent la protection contre les menaces web, le filtrage de contenu web et les indicateurs personnalisés IP/URL. La protection web vous permet de sécuriser vos appareils contre les menaces web et permet de réglementer le contenu indésirable.
- [Intégration améliorée de Pertahanan Microsoft untuk Titik Akhir (MDE) pour Windows Server 2012 R2 et Windows Server 2016](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2207#improved-microsoft-defender-for-endpoint-mde-onboarding-for-windows-server-2012-r2-and-windows-server-2016)<br>Configuration Manager version 2207 prend désormais en charge le déploiement automatique de Pertahanan Microsoft untuk Titik Akhir modernes unifiées pour Windows Server 2012 R2 & 2016. Windows Server 2012 et les appareils 2016 ciblés par Pertahanan Microsoft untuk Titik Akhir stratégie d’intégration utiliseront l’agent unifié par rapport à la solution existante basée sur Microsoft Monitoring Agent, s’ils sont configurés via les paramètres client.


## <a name="july-2022"></a>Juillet 2022
- [Ajouter des appareils de contrôleur de domaine - Amélioration du laboratoire d’évaluation](evaluation-lab.md#add-a-domain-controller)<br>Désormais en disponibilité générale : ajoutez un contrôleur de domaine pour exécuter des scénarios complexes tels que le déplacement latéral et les attaques multiphases sur plusieurs appareils.
- [Annonce des améliorations apportées aux pages de fichiers dans Pertahanan Microsoft untuk Titik Akhir](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-file-page-enhancements-in-microsoft-defender-for/ba-p/3584004)<br>Avez-vous déjà examiné des fichiers dans Pertahanan Microsoft untuk Titik Akhir ? Nous la rendons maintenant encore plus facile grâce à notre annonce récente d’améliorations apportées à la page fichier et au panneau latéral. Les utilisateurs peuvent désormais simplifier les processus en ayant une expérience de navigation plus efficace qui héberge toutes ces informations au même endroit.
- [Présentation de la nouvelle expérience de suppression d’alerte](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/introducing-the-new-alert-suppression-experience/ba-p/3562719)<br>Nous sommes heureux de partager l’expérience de suppression d’alertes nouvelle et avancée qui est désormais en disponibilité générale. La nouvelle expérience offre une granularité et un contrôle plus étroits, ce qui permet aux utilisateurs d’ajuster Pertahanan Microsoft untuk Titik Akhir alertes.
- [Empêcher les appareils non managés compromis de se déplacer latéralement dans votre organisation avec « Contenir](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/prevent-compromised-unmanaged-devices-from-moving-laterally-in/ba-p/3482134)<br>À compter d’aujourd’hui, lorsqu’un appareil qui n’est pas inscrit dans Pertahanan Microsoft untuk Titik Akhir est suspecté d’être compromis, en tant qu’analyste SOC, vous serez en mesure de le « contenir ». Par conséquent, tout appareil inscrit dans Pertahanan Microsoft untuk Titik Akhir bloque désormais toute communication entrante/sortante avec l’appareil suspecté.
- [La prise en charge des appareils mobiles est désormais disponible pour les clients du gouvernement des États-Unis qui utilisent Defender pour point de terminaison](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/mobile-device-support-is-now-available-for-us-government/ba-p/3472590)<br>Pertahanan Microsoft untuk Titik Akhir pour les clients du gouvernement des États-Unis est intégré à l’environnement Azure US Government et utilise les mêmes technologies sous-jacentes que Defender dans Azure Commercial. Cette offre est disponible pour les clients GCC, GCC High et DoD et étend la disponibilité de notre plateforme de Windows, macOS et Linux, aux appareils Android et iOS.


## <a name="june-2022"></a>Juin 2022
- [Defender pour serveurs Plan 2 s’intègre désormais à la solution unifiée MDE](https://techcommunity.microsoft.com/t5/microsoft-defender-for-cloud/defender-for-servers-plan-2-now-integrates-with-mde-unified/ba-p/3527534)<br>Vous pouvez maintenant commencer à déployer la solution unifiée moderne pour Windows Server 2012 R2 et 2016 sur les serveurs couverts par Defender pour serveurs Plan 2 à l’aide d’un seul bouton.
- [Protection réseau mobile dans Pertahanan Microsoft untuk Titik Akhir sur Android & iOS désormais en préversion publique](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/mobile-network-protection-in-microsoft-defender-for-endpoint-on/ba-p/3559121)<br>Microsoft offre une fonctionnalité de protection réseau mobile dans Defender pour point de terminaison qui permet aux organisations d’identifier, d’évaluer et de corriger les faiblesses des points de terminaison à l’aide de renseignements fiables sur les menaces. Nous sommes ravis d’annoncer que les utilisateurs peuvent désormais bénéficier de cette nouvelle fonctionnalité sur les plateformes Android et iOS avec Pertahanan Microsoft untuk Titik Akhir.

## <a name="may-2022"></a>Mai 2022
- [Protection contre les falsifications pour macOS (préversion)](tamperprotection-macos.md)<br>La protection contre les falsifications permet d’empêcher la suppression non autorisée de Pertahanan Microsoft untuk Titik Akhir sur macOS.
- [Ajouter des appareils de contrôleur de domaine - Amélioration du laboratoire d’évaluation (préversion)](evaluation-lab.md#add-a-domain-controller)<br>Ajoutez un contrôleur de domaine pour exécuter des scénarios complexes tels que le déplacement latéral et les attaques multiphases sur plusieurs appareils.
- [Mode de résolution des problèmes pour Pertahanan Microsoft untuk Titik Akhir désormais en disponibilité générale](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/troubleshooting-mode-for-microsoft-defender-for-endpoint-now/ba-p/3347344)<br>Présentation du mode de résolution des problèmes, un moyen unique, innovant et sécurisé d’examiner et d’ajuster les configurations sur vos appareils. Ce mode permet à l’administrateur local sur l’appareil de remplacer les configurations de stratégie de sécurité de l’Antivirus Microsoft Defender sur l’appareil, y compris la protection contre les falsifications. 
- [Annonce de la préversion publique du profil personnel Defender pour point de terminaison pour Android Enterprise](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-the-public-preview-of-defender-for-endpoint-personal/ba-p/3370979)<br>Nous sommes heureux d’annoncer que les utilisateurs qui souhaitent inscrire leurs propres appareils dans le programme BYOD de leur lieu de travail peuvent désormais bénéficier de la protection fournie par Pertahanan Microsoft untuk Titik Akhir dans leur profil personnel.
- [La gestion des paramètres de sécurité dans Pertahanan Microsoft untuk Titik Akhir est désormais en disponibilité générale](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/security-settings-management-in-microsoft-defender-for-endpoint/ba-p/3356970)<br>À la fin de 2021, nous avons annoncé que Pertahanan Microsoft untuk Titik Akhir étendu ses fonctionnalités de gestion de la configuration. Cette version a autorisé les équipes de sécurité à configurer les appareils avec les paramètres de sécurité souhaités sans avoir à déployer et à implémenter d’autres outils ou infrastructure.  Grâce à Microsoft Endpoint Manager, les organisations ont pu gérer les stratégies antivirus (AV), de détection et de réponse de point de terminaison (EDR) et de pare-feu (FW) à partir d’une seule vue pour tous les appareils inscrits. Aujourd’hui, nous annonons que cette fonctionnalité est désormais en disponibilité générale pour le client Windows et le serveur Windows, ce qui prend en charge Windows 10, Windows 11 et Windows Server 2012 R2 ou version ultérieure.

## <a name="april-2022"></a>Avril 2022
- [Mise à jour de l’intégration et de la parité des fonctionnalités pour Windows Server 2012 R2 et Windows Server 2016)](configure-server-endpoints.md)<br/> Le nouveau package de solution unifié est désormais en disponibilité générale et facilite l’intégration des serveurs en supprimant les dépendances et les étapes d’installation. En outre, ce package de solution unifié est fourni avec de nombreuses nouvelles améliorations de fonctionnalités.
- [Intégration à Tunnel pour iOS](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/what-s-new-in-microsoft-endpoint-manager-2204-april-edition/ba-p/3297995). Pertahanan Microsoft untuk Titik Akhir sur iOS peut désormais s’intégrer à Microsoft Tunnel, une solution de passerelle VPN pour activer la sécurité et la connectivité dans une seule application. Cette fonctionnalité était auparavant disponible uniquement sur Android.
- [Protection anti-programme malveillant améliorée dans Pertahanan Microsoft untuk Titik Akhir Android](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/enhanced-antimalware-protection-in-microsoft-defender-for/ba-p/3290320)<br>Nous sommes heureux de partager les principales mises à jour des fonctionnalités de protection contre les programmes malveillants de Pertahanan Microsoft untuk Titik Akhir sur Android. Ces nouvelles fonctionnalités constituent un composant majeur de votre protection de nouvelle génération dans Pertahanan Microsoft untuk Titik Akhir. Cette protection regroupe le Machine Learning, l’analyse big data, la recherche approfondie sur les menaces et l’infrastructure cloud Microsoft pour protéger les appareils Android (ou les points de terminaison) de votre organisation.
- [Fonctionnalités améliorées du moteur anti-programme malveillant pour Linux et macOS](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/enhanced-antimalware-engine-capabilities-for-linux-and-macos/ba-p/3292003)<br>Nous annoncons une mise à niveau significative vers notre protection de nouvelle génération sur Linux et macOS avec un nouveau moteur amélioré. Le moteur de logiciel anti-programme malveillant antivirus Microsoft Defender est un composant clé de la protection de nouvelle génération. Cette protection apporte le Machine Learning, l’analyse big data, la recherche approfondie sur les menaces et l’infrastructure cloud Microsoft pour protéger les appareils (ou points de terminaison) de votre organisation. Les principaux avantages de cette mise à jour majeure sont les améliorations des performances et de la prévention, ainsi que l’ajout de la prise en charge des indicateurs de fichiers personnalisés sur macOS et Linux.
- [Nouvelle fonctionnalité de création de rapports pour le contrôle d’appareil et le pare-feu Windows Defender](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/new-reporting-functionality-for-device-control-and-windows/ba-p/3290601)<br>Nous sommes heureux d’annoncer les nouvelles fonctionnalités de création de rapports de points de terminaison dans le portail Microsoft 365 Defender. Ce travail rassemble de nouveaux rapports de point de terminaison pour vous permettre de voir ce qui se passe dans votre environnement en quelques clics. Nos rapports sont conçus pour fournir des informations sur le comportement et l’activité des appareils tout en vous permettant de tirer pleinement parti des expériences intégrées dans Microsoft 365 Defender portail, telles que la chronologie des appareils et la chasse avancée.
- [Les soumissions unifiées dans Microsoft 365 Defender désormais en disponibilité générale !](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/unified-submissions-in-microsoft-365-defender-now-generally/ba-p/3270770)<br>Votre équipe de sécurité dispose désormais d’un « guichet unique » pour l’envoi d’e-mails, d’URL, de pièces jointes et de fichiers dans une expérience de soumission facile à utiliser. Pour simplifier le processus de soumission, nous sommes heureux d’annoncer une nouvelle expérience de soumission unifiée dans le portail Microsoft 365 Defender (https://security.microsoft.com). Avec les soumissions unifiées, vous pouvez envoyer des fichiers à Microsoft 365 Defender pour révision à partir du portail. Nous ajoutons également la possibilité d’envoyer un fichier directement à partir d’une page d’alerte Pertahanan Microsoft untuk Titik Akhir.  
- [Annonce de la prise en charge et des fonctionnalités étendues pour les API Live Response](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-expanded-support-and-functionality-for-live-response/ba-p/3178432)<br>Nous sommes heureux de partager que nous continuons à développer la prise en charge des API existantes sur toutes nos plateformes prises en charge dans Pertahanan Microsoft untuk Titik Akhir, en plus d’annoncer de nouvelles qui aideront à simplifier et à augmenter l’automatisation et l’orchestration des réponses de l’organisation.

## <a name="february-2022"></a>Février 2022

- [Le module complémentaire Splunk pour Microsoft Security est désormais disponible](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/the-splunk-add-on-for-microsoft-security-is-now-available/ba-p/3171272)<br>Nous sommes heureux de partager que le module complémentaire Splunk pris en charge par Splunk pour Microsoft Security est désormais disponible. Ce module complémentaire s’appuie sur le module complémentaire Microsoft 365 Defender pour Splunk 1.3.0 et mappe les propriétés de l’API Alertes Pertahanan Microsoft untuk Titik Akhir ou les propriétés de l’API incidents Microsoft 365 Defender sur le modèle d’information commun (CIM) de Splunk.
- [Dépréciation de l’API SIEM héritée - Différée](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/deprecating-the-legacy-siem-api-postponed/ba-p/3139643)<br>Nous avons précédemment annoncé que l’API REST SIEM serait déconseillée le 1er/04/2022. Nous avons écouté les commentaires des clients et la dépréciation de l’API a été reportée pour l’instant, plus de détails sont attendus au troisième trimestre 2022. Nous sommes impatients de partager des détails passionnants sur les API Microsoft 365 Defender dans Microsoft Graph au troisième trimestre 2022.

## <a name="january-2022"></a>Janvier 2022

- [La gestion des vulnérabilités pour Android et iOS est désormais en disponibilité générale](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663)<br>Avec cette nouvelle couverture multiplateforme, Gestion des menaces et des vulnérabilités fonctionnalités prennent désormais en charge toutes les principales plateformes d’appareils au sein de l’organisation , couvrant les stations de travail, les serveurs et les appareils mobiles. 
- [Pertahanan Microsoft untuk Titik Akhir plan 1 désormais inclus dans les licences Microsoft 365 E3/A3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-for-endpoint-plan-1-now-included-in-m365-e3/ba-p/3060639)<br>À compter du 14 janvier, Pertahanan Microsoft untuk Titik Akhir Plan 1 (P1) sera automatiquement inclus dans les licences Microsoft 365 E3/A3.
- [Intégration sans contact de Pertahanan Microsoft untuk Titik Akhir sur iOS désormais en préversion publique](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/zero-touch-onboarding-of-microsoft-defender-for-endpoint-on-ios/ba-p/3038045)<br>Grâce à cette nouvelle fonctionnalité, les entreprises peuvent désormais déployer Pertahanan Microsoft untuk Titik Akhir sur des appareils iOS inscrits auprès de Microsoft Endpoint Manager automatiquement, sans avoir besoin d’utilisateurs finaux pour interagir avec l’application. Cela facilite les frictions de déploiement et réduit considérablement le temps nécessaire au déploiement de l’application sur tous les appareils à mesure que Pertahanan Microsoft untuk Titik Akhir s’active en mode silencieux sur les appareils ciblés et commence à protéger votre patrimoine iOS.

## <a name="december-2021"></a>Décembre 2021

- [Gestion des vulnérabilités Microsoft Defender peut aider à identifier les vulnérabilités Log4j dans les applications et les composants](https://www.microsoft.com/security/blog/2021/12/11/guidance-for-preventing-detecting-and-hunting-for-cve-2021-44228-log4j-2-exploitation/#TVM)<br>La gestion des menaces et des vulnérabilités identifie automatiquement et en toute transparence les appareils affectés par les vulnérabilités Log4j et les risques associés dans l’environnement, et réduit considérablement le temps d’atténuation. Microsoft continue d’itérer sur ces fonctionnalités en fonction des dernières informations du paysage des menaces.
- Découvrir les appareils IoT (préversion) : la [découverte](device-discovery.md) d’appareils peut désormais vous aider à trouver des appareils IoT non managés connectés à votre réseau d’entreprise. Cela vous donne une vue unifiée de votre inventaire IoT avec le reste de vos appareils informatiques (stations de travail, serveurs et appareils mobiles).
- [Intégration de Microsoft Defender pour IoT (préversion)](enable-microsoft-defender-for-iot-integration.md) : cette intégration améliore vos fonctionnalités de découverte d’appareils avec les fonctionnalités de surveillance sans agent fournies par Microsoft Defender pour IoT. Cela offre une visibilité accrue pour vous aider à localiser, identifier et sécuriser les appareils IoT dans votre réseau.

## <a name="november-2021"></a>Novembre 2021

- [Gestion de la configuration de la sécurité](security-config-management.md) <br/> Possibilité pour les appareils qui ne sont pas gérés par un Endpoint Manager Microsoft, Microsoft Intune ou Microsoft Endpoint Configuration Manager, de recevoir des configurations de sécurité pour Microsoft Defender directement à partir de Endpoint Manager.
- [Laboratoire d’évaluation : Prise en charge étendue du système d’exploitation & simulations Atomic Red Team](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/evaluation-lab-expanded-os-support-amp-atomic-red-team/ba-p/2993927)<br>Le laboratoire d’évaluation prend désormais en charge l’ajout d’appareils Windows 11, Windows Server 2016 et Linux. En outre, nous aimerions également annoncer un nouveau partenariat avec la bibliothèque de simulation open source de Red Canary, Atomic Red Team!
- [Annonce de la préversion publique de Pertahanan Microsoft untuk Titik Akhir Mobile - Protection contre les falsifications](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-the-public-preview-of-microsoft-defender-for-endpoint/ba-p/2971038)<br>Marquez un appareil non conforme après sept jours d’inactivité dans l’application mobile Pertahanan Microsoft untuk Titik Akhir.
- [Renforcer la protection de votre patrimoine Linux avec la surveillance du comportement, la couverture étendue des distributions et bien plus encore](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/boost-protection-of-your-linux-estate-with-behavior-monitoring/ba-p/2909320)<br>Nous sommes ravis de partager les dernières nouvelles sur Pertahanan Microsoft untuk Titik Akhir sur la protection de nouvelle génération Linux, la détection des points de terminaison et la réponse (EDR), Gestion des menaces et des vulnérabilités (TVM). La protection Microsoft pour votre patrimoine Linux reçoit une amélioration impressionnante dans l’ensemble de la suite de sécurité. Avec les Pertahanan Microsoft untuk Titik Akhir récentes sur l’intégration de Linux à Azure Security Center, les avantages de nos systèmes EDR et TVM Linux s’étendent désormais aux clients Azure Defender.

## <a name="october-2021"></a>Octobre 2021

- [Mise à jour de l’intégration et de la parité des fonctionnalités pour Windows Server 2012 R2 et Windows Server 2016 (préversion)](configure-server-endpoints.md)<br/> Le nouveau package de solution unifiée facilite l’intégration des serveurs en supprimant les dépendances et les étapes d’installation. En outre, ce package de solution unifié est fourni avec de nombreuses nouvelles améliorations de fonctionnalités.
- Windows 11 prise en charge ajoutée à Pertahanan Microsoft untuk Titik Akhir et Microsoft 365 Defender.

## <a name="september-2021"></a>Septembre 2021

- [Filtrage du contenu web](web-content-filtering.md) <br/>Dans le cadre des fonctionnalités de protection web de Pertahanan Microsoft untuk Titik Akhir, le filtrage de contenu web permet à l’équipe de sécurité de votre organisation de suivre et de réglementer l’accès aux sites web en fonction de leurs catégories de contenu. Les catégories incluent le contenu pour adultes, la bande passante élevée, la responsabilité légale, les loisirs et les catégories non catégorisées. Bien que de nombreux sites web qui appartiennent à une ou plusieurs de ces catégories ne soient pas malveillants, ils peuvent être problématiques en raison des réglementations de conformité, de l’utilisation de la bande passante ou d’autres problèmes. [Mer informasjon sur le filtrage de contenu web](web-content-filtering.md).

## <a name="august-2021"></a>Août 2021

- (Préversion) [Pertahanan Microsoft untuk Titik Akhir Plan 1](defender-endpoint-plan-1.md) <br/>Defender pour point de terminaison Plan 1 (préversion) est une solution de protection des points de terminaison qui inclut la protection de nouvelle génération, la réduction de la surface d’attaque, la gestion et la création de rapports centralisées, ainsi que des API. Defender pour point de terminaison Plan 1 (préversion) est une nouvelle offre pour les clients qui souhaitent essayer nos fonctionnalités de protection des points de terminaison, qui ont Microsoft 365 E3 et qui n’ont pas encore Microsoft 365 E5. 

   Pour en savoir plus, consultez [Pertahanan Microsoft untuk Titik Akhir Plan 1 (préversion).](defender-endpoint-plan-1.md) Les fonctionnalités [existantes de Defender pour point de terminaison](microsoft-defender-endpoint.md) seront appelées Defender pour point de terminaison Plan 2. 
- (Préversion) [Filtrage de contenu web](web-content-filtering.md)<br>  Le filtrage de contenu web fait partie des fonctionnalités de protection web dans Pertahanan Microsoft untuk Titik Akhir. Il permet à votre organisation de suivre et de réglementer l’accès aux sites web en fonction de leurs catégories de contenu. La plupart de ces sites web, bien qu’ils ne soient pas malveillants, peuvent être problématiques en raison des réglementations de conformité, de l’utilisation de la bande passante ou d’autres problèmes.

## <a name="july-2021"></a>Juillet 2021

- (Préversion) [Rapport d’intégrité et de conformité des appareils](device-health-reports.md) <br>  Le rapport d’intégrité et de conformité des appareils fournit des informations générales sur les appareils de votre organisation.

## <a name="june-2021"></a>Juin 2021

- [Évaluation des vulnérabilités des logiciels d’exportation Delta](get-assessment-methods-properties.md#31-methods) Api <br> Ajout aux [évaluations d’exportation des vulnérabilités et](get-assessment-methods-properties.md) à la collecte d’API de configurations sécurisées. <br> Contrairement à l’évaluation complète des vulnérabilités logicielles (réponse JSON) - qui est utilisée pour obtenir un instantané complet de l’évaluation des vulnérabilités logicielles de votre organisation par appareil - l’appel d’API d’exportation delta est utilisé pour extraire uniquement les modifications qui se sont produites entre une date sélectionnée et la date actuelle (l’appel d’API « delta »). Au lieu d’obtenir une exportation complète avec une grande quantité de données à chaque fois, vous obtenez uniquement des informations spécifiques sur les vulnérabilités nouvelles, corrigées et mises à jour. L’appel d’API d’exportation Delta peut également être utilisé pour calculer différents indicateurs de performance clés, tels que « le nombre de vulnérabilités qui ont été corrigées » ou « le nombre de nouvelles vulnérabilités ajoutées à une organisation ».
- [Exporter des évaluations des vulnérabilités et des configurations sécurisées](get-assessment-methods-properties.md) Api <br> Ajoute une collection d’API qui extraient les données de gestion des vulnérabilités Defender par appareil. Il existe différents appels d’API pour obtenir différents types de données : évaluation de la configuration sécurisée, évaluation de l’inventaire logiciel et évaluation des vulnérabilités logicielles. Chaque appel d’API contient les données requises pour les appareils de votre organisation.
- [Activité de correction](get-remediation-methods-properties.md) Api <br> Ajoute une collection d’API avec des réponses qui contiennent des activités de correction de Gestion des vulnérabilités Defender qui ont été créées dans votre locataire. Les types d’informations de réponse incluent une activité de correction par ID, toutes les activités de correction et les appareils exposés d’une activité de correction.
- [Découverte d’appareils](device-discovery.md) <br> Vous permet de trouver des appareils non gérés connectés à votre réseau d’entreprise sans avoir besoin d’appliances supplémentaires ou de modifications de processus fastidieuses. À l’aide d’appareils intégrés, vous pouvez trouver des appareils non gérés dans votre réseau et évaluer les vulnérabilités et les risques. Vous pouvez ensuite intégrer des appareils détectés pour réduire les risques associés à la présence de points de terminaison non managés dans votre réseau.

   > [!IMPORTANT]
   > La découverte standard sera le mode par défaut pour tous les clients à compter du 19 juillet 2021. Vous pouvez choisir de conserver le mode de base via la page des paramètres.

- [Les définitions de groupe d’appareils](/microsoft-365/security/defender-endpoint/machine-groups) peuvent désormais inclure plusieurs valeurs pour chaque condition. Vous pouvez définir plusieurs balises, noms d’appareils et domaines sur la définition d’un seul groupe d’appareils.
- [Prise en charge de la gestion des applications mobiles](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-new-capabilities-on-android-and-ios/ba-p/2442730) <br> Cette amélioration permet Pertahanan Microsoft untuk Titik Akhir protéger les données d’une organisation au sein d’une application managée quand Intune est utilisé pour gérer des applications mobiles. Pour plus d’informations sur la gestion des applications mobiles, consultez [cette documentation](/mem/intune/apps/mam-faq).
- [Intégration du VPN Microsoft Tunnel](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-new-capabilities-on-android-and-ios/ba-p/2442730) <br> Les fonctionnalités VPN de Microsoft Tunnel sont désormais intégrées à Pertahanan Microsoft untuk Titik Akhir application pour Android. Cette unification permet aux organisations d’offrir une expérience utilisateur final simplifiée avec une application de sécurité, offrant à la fois la défense contre les menaces mobiles et la possibilité d’accéder aux ressources locales à partir de leur appareil mobile, tandis que la sécurité et les équipes informatiques sont en mesure de maintenir les mêmes expériences d’administration qu’elles connaissent.
- [Détection jailbreak sur iOS](/microsoft-365/security/defender-endpoint/ios-configure-features#conditional-access-with-defender-for-endpoint-on-ios) <br> La fonctionnalité de détection de jailbreak dans Pertahanan Microsoft untuk Titik Akhir sur iOS est désormais en disponibilité générale. Cela ajoute à la protection contre le hameçonnage qui existe déjà.  Pour plus d’informations, consultez [la stratégie d’accès conditionnel d’installation basée sur les signaux de risque de l’appareil](/microsoft-365/security/defender-endpoint/ios-configure-features).


## <a name="march-2021"></a>Mars 2021
- [Gérer la protection contre les falsifications pour votre organisation à l’aide du portail Microsoft 365 Defender](manage-tamper-protection-microsoft-365-defender.md) <br> Vous pouvez gérer les paramètres de protection contre les falsifications sur Windows 10, Windows Server 2016, Windows Server 2019 et Windows Server 2022 à l’aide d’une méthode appelée *attachement de locataire*.


## <a name="january-2021"></a>Janvier 2021

- [Azure Virtual Desktop](https://azure.microsoft.com/services/virtual-desktop/) <br> Pertahanan Microsoft untuk Titik Akhir ajoute désormais la prise en charge d’Azure Virtual Desktop.
