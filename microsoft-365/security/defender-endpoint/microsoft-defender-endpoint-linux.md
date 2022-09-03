---
title: Microsoft Defender pour point de terminaison Linux
ms.reviewer: ''
description: Décrit comment installer et utiliser Microsoft Defender pour point de terminaison sur Linux.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, installation, deploy, uninstallation, puppet, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
ms.service: microsoft-365-security
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 32debe4990d7f6832e0c9a58e453cbf6ace0118b
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67580835"
---
# <a name="microsoft-defender-for-endpoint-on-linux"></a>Microsoft Defender pour point de terminaison Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique explique comment installer, configurer, mettre à jour et utiliser Microsoft Defender pour point de terminaison sur Linux.

> [!CAUTION]
> L’exécution d’autres produits de protection de point de terminaison tiers avec Microsoft Defender pour point de terminaison sur Linux est susceptible d’entraîner des problèmes de performances et des effets secondaires imprévisibles. Si la protection des points de terminaison non Microsoft est une exigence absolue dans votre environnement, vous pouvez toujours tirer parti en toute sécurité de la fonctionnalité Defender pour point de terminaison sur Linux EDR après avoir configuré la fonctionnalité antivirus pour qu’elle s’exécute en [mode passif](linux-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="how-to-install-microsoft-defender-for-endpoint-on-linux"></a>Comment installer Microsoft Defender pour point de terminaison sur Linux

Microsoft Defender pour point de terminaison pour Linux inclut des fonctionnalités anti-programme malveillant et de détection et de réponse de point de terminaison (EDR). 


### <a name="prerequisites"></a>Prerequisites

- Accès au portail Microsoft 365 Defender
- Distribution Linux à l’aide du gestionnaire système [systemd](https://systemd.io/)

  >[!NOTE]
  >La distribution Linux à l’aide du gestionnaire de système, à l’exception de RHEL/CentOS 6.x, prend en charge SystemV et Upstart.

- Expérience de niveau débutant dans les scripts Linux et BASH
- Privilèges d’administration sur l’appareil (en cas de déploiement manuel)

> [!NOTE]
> Microsoft Defender pour point de terminaison sur l’agent Linux est indépendant de [l’agent OMS](/azure/azure-monitor/agents/agents-overview#log-analytics-agent). Microsoft Defender pour point de terminaison s’appuie sur son propre pipeline de télémétrie indépendant.


### <a name="installation-instructions"></a>Instructions d’installation

Vous pouvez utiliser plusieurs méthodes et outils de déploiement pour installer et configurer Microsoft Defender pour point de terminaison sur Linux.

En général, vous devez effectuer les étapes suivantes :

- Vérifiez que vous disposez d’un abonnement Microsoft Defender pour point de terminaison.
- Déployez Microsoft Defender pour point de terminaison sur Linux à l’aide de l’une des méthodes de déploiement suivantes :
  - Outil en ligne de commande :
    - [Déploiement manuel](linux-install-manually.md)
  - Outils de gestion tiers :
    - [Déployer à l’aide de l’outil de gestion de configuration Puppet](linux-install-with-puppet.md)
    - [Déployer à l’aide de l’outil de gestion de configuration Ansible](linux-install-with-ansible.md)
    - [Déployer à l’aide de l’outil de gestion de configuration Chef](linux-deploy-defender-for-endpoint-with-chef.md)

Si vous rencontrez des échecs d’installation, [reportez-vous à la résolution des problèmes d’installation dans Microsoft Defender pour point de terminaison sur Linux](linux-support-install.md).

> [!NOTE]
> Il n’est pas pris en charge d’installer Microsoft Defender pour point de terminaison à un autre emplacement que le chemin d’installation par défaut. 

> [!NOTE]
> Microsoft Defender pour point de terminaison sur Linux crée un utilisateur « mdatp » avec un UID et un GID aléatoires. Si vous souhaitez contrôler l’UID et le GID, créez un utilisateur « mdatp » avant l’installation à l’aide de l’option shell « /usr/sbin/nologin ».
> Par exemple : `mdatp:x:UID:GID::/home/mdatp:/usr/sbin/nologin`.

### <a name="system-requirements"></a>Configuration requise

> [!NOTE]
> La prise en charge de Red Hat Enterprise Linux et CentOS 6.7+ à 6.10+ est en préversion.

- Distributions de serveurs Linux prises en charge et versions x64 (AMD64/EM64T) et x86_64 :

  - Red Hat Enterprise Linux 6.7 ou version ultérieure (préversion)
  - Red Hat Enterprise Linux 7.2 ou version ultérieure
  - Red Hat Enterprise Linux 8.x
  - Red Hat Enterprise Linux 9.x
  - CentOS 6.7 ou version ultérieure (préversion)
  - CentOS 7.2 ou version ultérieure
  - Ubuntu 16.04 LTS ou LTS supérieur
  - Debian 9 ou version ultérieure
  - SUSE Linux Enterprise Server 12 ou version ultérieure
  - Oracle Linux 7.2 ou version ultérieure
  - Oracle Linux 8.x
  - Amazon Linux 2
  - Fedora 33 ou version ultérieure

    > [!NOTE]
    > Les distributions et les versions qui ne sont pas explicitement répertoriées ne sont pas prises en charge (même si elles sont dérivées des distributions officiellement prises en charge).




- Liste des versions de noyau prises en charge
  > [!NOTE]
  > Microsoft Defender pour point de terminaison sur RHEL/CentOS - 6.7 à 6.10 est une solution basée sur le noyau. Vous devez vérifier que le noyau est pris en charge avant de procéder à la mise à jour vers la version plus récente du noyau. Consultez la liste ci-dessous pour obtenir la liste des noyaux pris en charge.
  > Microsoft Defender pour point de terminaison implémentation de toutes les autres distributions et versions prises en charge est indépendante des versions du noyau. Avec une exigence minimale pour que la version du noyau soit activée ou supérieure à 3.10.0-327.

  - L’option `fanotify` de noyau doit être activée
  - Red Hat Enterprise Linux 6 et CentOS 6 :
    - Pour 6.7 : 2.6.32-573.*
    - Pour 6.8 : 2.6.32-642.*
    - Pour 6.9 : 2.6.32-696.* (sauf 2.6.32-696.el6.x86_64)
    - Pour 6.10 : 2.6.32.754.2.1.el6.x86_64 à 2.6.32-754.47.1 :
    
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
       - 2.6.32-754.43.1.el6.x86_64
       - 2.6.32-754.47.1.el6.x86_64
       - 2.6.32-754.6.3.el6.x86_64
       - 2.6.32-754.9.1.el6.x86_64

 > [!NOTE]
 > Une fois qu’une nouvelle version de package est publiée, la prise en charge des deux versions précédentes est réduite au support technique uniquement. Les versions antérieures à celles répertoriées dans cette section sont fournies uniquement pour la prise en charge de la mise à niveau technique.


  > [!CAUTION]
  > L’exécution de Defender pour point de terminaison sur Linux côte à côte avec d’autres `fanotify`solutions de sécurité basées n’est pas prise en charge. Il peut entraîner des résultats imprévisibles, y compris suspendre le système d’exploitation.

- Espace disque : 1 Go

- /opt/microsoft/mdatp/sbin/wdavdaemon nécessite une autorisation exécutable. Pour plus d’informations, consultez « Vérifier que le démon dispose d’une autorisation exécutable » dans [Résoudre les problèmes d’installation pour Microsoft Defender pour point de terminaison sur Linux](/microsoft-365/security/defender-endpoint/linux-support-install).

- Cœurs : 2 minimum, 4 préférés

- Mémoire : 1 Go minimum, 4 préférés

    > [!NOTE]
    > Vérifiez que vous disposez d’un espace disque libre dans /var.

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

Une fois que vous avez activé le service, vous devrez peut-être configurer votre réseau ou votre pare-feu pour autoriser les connexions sortantes entre celui-ci et vos points de terminaison.

- L’infrastructure d’audit (`auditd`) doit être activée.

  > [!NOTE]
  > Les événements système capturés par les règles ajoutées s’ajoutent `/etc/audit/rules.d/` à `audit.log`(s) et peuvent affecter l’audit de l’hôte et la collecte en amont. Les événements ajoutés par Microsoft Defender pour point de terminaison sur Linux sont marqués avec `mdatp` une clé.

### <a name="configuring-exclusions"></a>Configuration des exclusions

Lors de l’ajout d’exclusions à l’antivirus Microsoft Defender, vous devez tenir compte des [erreurs courantes d’exclusion pour l’antivirus Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus)

### <a name="network-connections"></a>Connexions réseau

La feuille de calcul téléchargeable suivante répertorie les services et leurs URL associées auxquelles votre réseau doit pouvoir se connecter. Vous devez vous assurer qu’il n’existe aucune règle de pare-feu ou de filtrage réseau qui refuserait l’accès à ces URL. Si c’est le cas, vous devrez peut-être créer une règle *d’autorisation* spécifique pour eux.

<br>

****

|Feuille de calcul de la liste des domaines| Description|
|---|---|
|liste d’URL Microsoft Defender pour point de terminaison pour les clients commerciaux| Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation des clients commerciaux. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender pour point de terminaison liste d’URL pour Gov/GCC/DoD | Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation pour les clients Gov/GCC/DoD. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

> [!NOTE]
> Pour obtenir une liste d’URL plus spécifique, consultez [Configurer les paramètres de connectivité proxy et Internet](/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server).

Defender pour point de terminaison peut découvrir un serveur proxy à l’aide des méthodes de découverte suivantes :

- Proxy transparent
- Configuration manuelle du proxy statique

Si un proxy ou un pare-feu bloque le trafic anonyme, assurez-vous que le trafic anonyme est autorisé dans les URL précédemment répertoriées. Pour les proxys transparents, aucune configuration supplémentaire n’est nécessaire pour Defender pour point de terminaison. Pour le proxy statique, suivez les étapes de [la configuration manuelle du proxy statique](linux-static-proxy-configuration.md).

> [!WARNING]
> Les proxys PAC, WPAD et authentifiés ne sont pas pris en charge. Vérifiez que seul un proxy statique ou transparent est utilisé.
>
> Les proxys d’inspection et d’interception SSL ne sont pas non plus pris en charge pour des raisons de sécurité. Configurez une exception pour l’inspection SSL et votre serveur proxy pour passer directement les données de Defender pour point de terminaison sur Linux aux URL pertinentes sans interception. L’ajout de votre certificat d’interception au magasin global n’autorise pas l’interception.

Pour connaître les étapes de résolution des problèmes, consultez [Résoudre les problèmes de connectivité cloud pour Microsoft Defender pour point de terminaison sur Linux](linux-support-connectivity.md).

## <a name="how-to-update-microsoft-defender-for-endpoint-on-linux"></a>Comment mettre à jour Microsoft Defender pour point de terminaison sur Linux

Microsoft publie régulièrement des mises à jour logicielles pour améliorer les performances, la sécurité et fournir de nouvelles fonctionnalités. Pour mettre à jour Microsoft Defender pour point de terminaison sur Linux, reportez-vous à [Déployer des mises à jour pour Microsoft Defender pour point de terminaison sur Linux](linux-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-linux"></a>Comment configurer Microsoft Defender pour point de terminaison sur Linux

Des conseils sur la configuration du produit dans les environnements d’entreprise sont [disponibles dans Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md).

## <a name="common-applications-to-microsoft-defender-for-endpoint-can-impact"></a>Les applications courantes à Microsoft Defender pour point de terminaison peuvent avoir un impact

Les charges de travail d’E/S élevées de certaines applications peuvent rencontrer des problèmes de performances lors de l’installation de Microsoft Defender pour point de terminaison. Il s’agit notamment d’applications pour des scénarios de développeur comme Jenkins et Jira, et de charges de travail de base de données comme OracleDB et Postgres. Si vous rencontrez une dégradation des performances, envisagez de définir des exclusions pour les applications approuvées, en gardant à l’esprit [les erreurs d’exclusion courantes pour l’antivirus Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus) . Pour obtenir des conseils supplémentaires, consultez la documentation relative aux exclusions antivirus des applications tierces.

## <a name="resources"></a>Ressources

- Pour plus d’informations sur la journalisation, la désinstallation ou d’autres rubriques, consultez [Ressources](linux-resources.md).
  
## <a name="related-articles"></a>Articles connexes
  
- [Protégez vos points de terminaison avec la solution EDR intégrée de Defender pour Cloud : Microsoft Defender pour point de terminaison](/azure/defender-for-cloud/integration-defender-for-endpoint)
- [Connecter vos machines non Azure à Microsoft Defender pour cloud](/azure/defender-for-cloud/quickstart-onboard-machines)
- [Activer la protection réseau pour Linux](network-protection-linux.md)
