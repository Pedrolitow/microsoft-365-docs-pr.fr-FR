---
title: Microsoft Defender pour point de terminaison Linux
ms.reviewer: ''
description: Décrit comment installer et utiliser Microsoft Defender pour endpoint sur Linux.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, installation, déployer, désinstallation, préinstallation, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a0c013b6b99ad9b8da6a3cedeb93df036de4e257
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2022
ms.locfileid: "62464068"
---
# <a name="microsoft-defender-for-endpoint-on-linux"></a>Microsoft Defender pour point de terminaison Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique décrit comment installer, configurer, mettre à jour et utiliser Microsoft Defender pour Endpoint sur Linux.

> [!CAUTION]
> L’exécution d’autres produits de protection de point de terminaison tiers avec Microsoft Defender pour Endpoint sur Linux est susceptible de provoquer des problèmes de performances et des effets secondaires imprévisibles. Si la protection des points de terminaison non-Microsoft est une exigence absolue dans votre environnement, vous pouvez toujours tirer parti en toute sécurité de defender pour point de terminaison sur la fonctionnalité Linux PEPT après avoir configuré la fonctionnalité antivirus pour qu’elle s’exécute en [mode](linux-preferences.md#enforcement-level-for-antivirus-engine) passif.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-linux"></a>Comment installer Microsoft Defender pour endpoint sur Linux

### <a name="prerequisites"></a>Conditions préalables

- Accès au portail Microsoft 365 Defender web
- Distribution Linux à l’aide [du gestionnaire système](https://systemd.io/)
- Expérience de niveau débutant dans les scripts Linux et BASH
- Privilèges d’administration sur l’appareil (en cas de déploiement manuel)

> [!NOTE]
> Microsoft Defender pour point de terminaison sur l’agent Linux est indépendant de [l’agent OMS](/azure/azure-monitor/agents/agents-overview#log-analytics-agent). Microsoft Defender pour le point de terminaison s’appuie sur son propre pipeline de télémétrie indépendant.


### <a name="installation-instructions"></a>Instructions d’installation

Vous pouvez utiliser plusieurs méthodes et outils de déploiement pour installer et configurer Microsoft Defender pour Endpoint sur Linux.

En règle générale, vous devez suivre les étapes suivantes :

- Assurez-vous que vous avez un abonnement Microsoft Defender pour point de terminaison.
- Déployez Microsoft Defender pour Endpoint sur Linux à l’aide de l’une des méthodes de déploiement suivantes :
  - L’outil en ligne de commande :
    - [Déploiement manuel](linux-install-manually.md)
  - Outils de gestion tiers :
    - [Déployer à l’aide de l’outil de gestion de la configuration de l’ordinateur](linux-install-with-puppet.md)
    - [Déployer à l’aide de l’outil de gestion de la configuration Ansible](linux-install-with-ansible.md)
    - [Déployer à l’aide de l’outil de gestion de la configuration Chef](linux-deploy-defender-for-endpoint-with-chef.md)

Si vous avez des échecs d’installation, reportez-vous à Résolution des problèmes [d’installation dans Microsoft Defender pour Point de terminaison sur Linux](linux-support-install.md).

> [!NOTE]
> Il n’est pas pris en charge d’installer Microsoft Defender pour le point de terminaison à un autre emplacement que le chemin d’installation par défaut. 

### <a name="system-requirements"></a>Configuration requise

- Distributions de serveurs Linux et versions x64 (AMD64/EM64T) prise en charge :

  - Red Hat Enterprise Linux 6.7 ou supérieur
  - Red Hat Enterprise Linux 7.2 ou supérieur
  - Red Hat Enterprise Linux 8.x
  - CentOS 6.7 ou supérieur 
  - CentOS 7.2 ou supérieur
  - Ubuntu 16.04 LTS ou une LTS supérieure
  - Debian 9 ou supérieur
  - SUSE Linux Enterprise Server 12 ou supérieur
  - Oracle Linux 7.2 ou supérieur
  - Amazon Linux 2
  - Fedora 33 ou supérieure

    > [!NOTE]
    > Les distributions et les versions qui ne sont pas explicitement répertoriées ne sont pas pris en charge (même s’ils sont dérivés des distributions officiellement pris en charge).

- Liste des versions de noyau prise en charge
  - Red Hat Enterprise Linux 6 et CentOS 6 :
    - Pour 6,7 : 2.6.32-573.*
    - Pour 6,8 : 2.6.32-642.*
    - Pour 6,9 : 2.6.32-696.*
    - Pour 6,10 : 2.6.32.754.2.1.el6.x86_64 2.6.32-754.41.2 :
    
       - 2.6.32-754.10.1.el6.x86_64
       - 2.6.32-754.11.1.el6.x86_64
       - 2.6.32-754.12.1.el6.x86_64
       - 2.6.32-754.14.2.el6.x86_64
       - 2.6.32-754.15.3.el6.x86_64
       - 2.6.32-754.17.1.el6.x86_64
       - 2.6.32-754.18.2.el6.x86_64
       - 2.6.32-754.2.1.el6.x86_64
       - 2.6.32-754.22.1.el6.x86_64
       - 2.6.32-754.23.1.el6.x86_64
       - 2.6.32-754.24.2.el6.x86_64
       - 2.6.32-754.24.3.el6.x86_64
       - 2.6.32-754.25.1.el6.x86_64
       - 2.6.32-754.27.1.el6.x86_64
       - 2.6.32-754.28.1.el6.x86_64
       - 2.6.32-754.29.1.el6.x86_64
       - 2.6.32-754.29.2.el6.x86_64
       - 2.6.32-754.3.5.el6.x86_64
       - 2.6.32-754.30.2.el6.x86_64
       - 2.6.32-754.33.1.el6.x86_64
       - 2.6.32-754.35.1.el6.x86_64
       - 2.6.32-754.39.1.el6.x86_64
       - 2.6.32-754.41.2.el6.x86_64
       - 2.6.32-754.6.3.el6.x86_64
       - 2.6.32-754.9.1.el6.x86_64


    > [!NOTE]
    > Après la publication d’une nouvelle version de package, la prise en charge des deux versions précédentes est réduite au support technique uniquement. Les versions antérieures à celles répertoriées dans cette section sont fournies uniquement pour la prise en charge de la mise à niveau technique.

  - Pour le reste des distributions prise en charge, la version minimale du noyau requise est 3.10.0-327

- Mécanisme du fournisseur d’événements
  - Red Hat Enterprise Linux 6 et CentOS 6 : `Talpa` solution basée sur un module noyau
  - Pour le reste des distributions pris en charge : `Fanotify`
    - L’option `fanotify` noyau doit être activée

      > [!CAUTION]
      > L’exécution de Defender pour Endpoint sur Linux côte `fanotify`à côte avec d’autres solutions de sécurité basées sur n’est pas prise en charge. Cela peut entraîner des résultats imprévisibles, y compris l’arrêt du système d’exploitation.

- Espace disque : 1 Go

- /opt/microsoft/mdatp/sbin/wdavdaemon requiert une autorisation exécutable. Pour plus d’informations, voir « S’assurer que le daemon dispose de l’autorisation exécutable » dans Résolution des problèmes [d’installation de Microsoft Defender pour Endpoint sur Linux](/microsoft-365/security/defender-endpoint/linux-support-install).

- Cœurs : 2 minimum, 4 préférés

- Mémoire : 1 Go minimum, 4 par préférence

    > [!NOTE]
    > Assurez-vous que vous avez de l’espace disque libre dans /var.

- La solution fournit actuellement une protection en temps réel pour les types de système de fichiers suivants :

  - `btrfs`
  - `ecryptfs`
  - `ext2`
  - `ext3`
  - `ext4`
  - `fuse`
  - `fuseblk`
  - `jfs`
  - `nfs`
  - `overlay`
  - `ramfs`
  - `reiserfs`
  - `tmpfs`
  - `udf`
  - `vfat`
  - `xfs`

Après avoir activé le service, vous devrez peut-être configurer votre réseau ou votre pare-feu pour autoriser les connexions sortantes entre celui-ci et vos points de terminaison.

- L’infrastructure d’audit (`auditd`) doit être activée.

  > [!NOTE]
  > Les événements système capturés par les règles ajoutées `/etc/audit/rules.d/` `audit.log`à s’ajoutent à (s) et peuvent affecter l’audit de l’hôte et la collecte en amont. Les événements ajoutés par Microsoft Defender pour Endpoint sur Linux sont marqués avec une `mdatp` clé.

### <a name="configuring-exclusions"></a>Configuration des exclusions

Lorsque vous ajoutez des exclusions Antivirus Microsoft Defender, vous devez tenir compte des [erreurs d’exclusion courantes Antivirus Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus)

### <a name="network-connections"></a>Connexions réseau

La feuille de calcul téléchargeable suivante répertorie les services et les URL associées à qui votre réseau doit pouvoir se connecter. Vous devez vous assurer qu’il n’existe aucune règle de pare-feu ou de filtrage réseau qui refuserait l’accès à ces URL. Si c’est le cas, vous devrez peut-être *créer une* règle d’autoriser spécifiquement pour eux.

<br>

****


|Liste de feuilles de calcul de domaines| Description|
|---|---|
|Liste d’URL Microsoft Defender pour les points de terminaison pour les clients commerciaux | Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation pour les clients commerciaux. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Liste d’URL Microsoft Defender pour les points de terminaison pour les clients Gov/Cloud de la communauté du secteur public/DoD| Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation pour les clients Gov/Cloud de la communauté du secteur public/DoD. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)
|


> [!NOTE]
> Pour obtenir une liste d’URL plus spécifique, voir [Configurer les paramètres de proxy et de connectivité Internet](/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server).

Defender pour le point de terminaison peut découvrir un serveur proxy à l’aide des méthodes de découverte suivantes :

- Proxy transparent
- Configuration manuelle du proxy statique

Si un proxy ou un pare-feu bloque le trafic anonyme, assurez-vous que le trafic anonyme est autorisé dans les URL répertoriées précédemment. Pour les proxies transparents, aucune configuration supplémentaire n’est nécessaire pour Defender for Endpoint. Pour le proxy statique, suivez les étapes de [la configuration manuelle du proxy statique](linux-static-proxy-configuration.md).

> [!WARNING]
> Les pacs, WPAD et les proxies authentifiés ne sont pas pris en charge. Assurez-vous que seul un proxy statique ou transparent est utilisé.
>
> L’inspection et l’interception des proxies SSL ne sont pas non plus pris en charge pour des raisons de sécurité. Configurez une exception pour l’inspection SSL et votre serveur proxy afin de transmettre directement les données de Defender pour Endpoint sur Linux aux URL pertinentes sans interception. L’ajout de votre certificat d’interception au magasin global n’autorise pas l’interception.

Pour les étapes de résolution des problèmes, voir Résoudre les problèmes de connectivité [cloud pour Microsoft Defender pour Endpoint sur Linux](linux-support-connectivity.md).

## <a name="how-to-update-microsoft-defender-for-endpoint-on-linux"></a>Comment mettre à jour Microsoft Defender pour endpoint sur Linux

Microsoft publie régulièrement des mises à jour logicielles pour améliorer les performances, la sécurité et fournir de nouvelles fonctionnalités. Pour mettre à jour Microsoft Defender pour endpoint sur Linux, reportez-vous à Déployer les mises à jour [de Microsoft Defender pour Endpoint sur Linux](linux-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-linux"></a>Comment configurer Microsoft Defender pour point de terminaison sur Linux

Des instructions sur la configuration du produit dans les environnements d’entreprise sont disponibles dans Définir les préférences [de Microsoft Defender pour Endpoint sur Linux](linux-preferences.md).

## <a name="common-applications-to-microsoft-defender-for-endpoint-can-impact"></a>Les applications courantes à Microsoft Defender pour le point de terminaison peuvent avoir un impact

Des charges de travail d’I/S élevées de certaines applications peuvent être problématiques en matière de performances lors de l’installation de Microsoft Defender for Endpoint. Il s’agit notamment des applications pour les scénarios de développement tels que Jenkins et Jira, et des charges de travail de base de données telles que OracleDB et Postgres. Si vous rencontrez une dégradation des performances, envisagez de définir des exclusions pour les applications fiables, en gardant les [erreurs d’exclusion courantes Antivirus Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus) à l’esprit. Pour obtenir des conseils supplémentaires, consultez la documentation de conseil concernant les exclusions antivirus provenant d’applications tierces.

## <a name="resources"></a>Ressources

- Pour plus d’informations sur la journalisation, la désinstallation ou d’autres rubriques, voir [Resources](linux-resources.md).
