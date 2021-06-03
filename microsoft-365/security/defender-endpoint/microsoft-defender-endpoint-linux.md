---
title: Microsoft Defender pour point de terminaison Linux
ms.reviewer: ''
description: Décrit comment installer et utiliser Microsoft Defender pour endpoint sur Linux.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, installation, déployer, désinstallation, préinstallation, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 2242d195f4a4ea4b8f0c345d82fa0ad1f947bfa2
ms.sourcegitcommit: e8f5d88f0fe54620308d3bec05263568f9da2931
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2021
ms.locfileid: "52730761"
---
# <a name="microsoft-defender-for-endpoint-on-linux"></a>Microsoft Defender pour point de terminaison Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique décrit comment installer, configurer, mettre à jour et utiliser Microsoft Defender pour Endpoint sur Linux.

> [!CAUTION]
> L’exécution d’autres produits de protection de point de terminaison tiers avec Microsoft Defender pour Endpoint sur Linux est susceptible de provoquer des problèmes de performances et des effets secondaires imprévisibles. Si la protection des points de terminaison non-Microsoft est une exigence absolue dans votre environnement, vous pouvez toujours tirer parti en toute sécurité de defender pour point de terminaison sur la fonctionnalité linux PEPT après avoir configuré la fonctionnalité antivirus pour qu’elle s’exécute en [mode](linux-preferences.md#enable--disable-passive-mode)passif.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-linux"></a>Comment installer Microsoft Defender pour endpoint sur Linux

### <a name="prerequisites"></a>Conditions préalables

- Accès au portail Centre de sécurité Microsoft Defender web
- Distribution Linux à l’aide [du gestionnaire système](https://systemd.io/)
- Expérience de niveau débutant dans les scripts Linux et BASH
- Privilèges d’administration sur l’appareil (en cas de déploiement manuel)

> [!NOTE]
>  Microsoft Defender pour point de terminaison sur l’agent Linux est indépendant de [l’agent OMS.](/azure/azure-monitor/agents/agents-overview#log-analytics-agent) Microsoft Defender pour le point de terminaison s’appuie sur son propre pipeline de télémétrie indépendant.
> 
> Microsoft Defender pour point de terminaison sur Linux n’est pas encore intégré au Centre de sécurité Azure.



### <a name="installation-instructions"></a>Instructions d’installation

Vous pouvez utiliser plusieurs méthodes et outils de déploiement pour installer et configurer Microsoft Defender pour Endpoint sur Linux.

En règle générale, vous devez suivre les étapes suivantes :

- Assurez-vous que vous avez un abonnement Microsoft Defender pour points de terminaison et que vous avez accès au portail [Microsoft Defender pour points de terminaison.](microsoft-defender-security-center.md)
- Déployez Microsoft Defender pour Endpoint sur Linux à l’aide de l’une des méthodes de déploiement suivantes :
  - L’outil en ligne de commande :
    - [Déploiement manuel](linux-install-manually.md)
  - Outils de gestion tiers :
    - [Déployer à l’aide de l’outil de gestion de la configuration de l’ordinateur](linux-install-with-puppet.md)
    - [Déployer à l’aide de l’outil de gestion de la configuration Ansible](linux-install-with-ansible.md)

Si vous avez des échecs d’installation, reportez-vous à Résolution des problèmes d’installation dans [Microsoft Defender pour Point de terminaison sur Linux.](linux-support-install.md)



### <a name="system-requirements"></a>Configuration requise

- Distributions de serveurs Linux et versions x64 (AMD64/EM64T) prise en charge :

  - Red Hat Enterprise Linux 7.2 ou supérieur
  - CentOS 7.2 ou supérieur
  - Ubuntu 16.04 LTS ou une LTS supérieure
  - Debian 9 ou supérieur
  - SUSE Linux Enterprise Server 12 ou supérieur
  - Oracle Linux 7.2 ou supérieur

    > [!NOTE]
    > Les distributions et les versions qui ne sont pas explicitement répertoriées ne sont pas pris en charge (même s’ils sont dérivés des distributions officiellement pris en charge).


- Version minimale du noyau 3.10.0-327

- `fanotify`L’option noyau doit être activée

  > [!CAUTION]
  > L’exécution de Defender pour Endpoint sur Linux côte à côte avec d’autres solutions de sécurité basées sur `fanotify` n’est pas prise en charge. Cela peut entraîner des résultats imprévisibles, y compris l’arrêt du système d’exploitation.

- Espace disque : 1 Go

- /opt/microsoft/mdatp/sbin/wdavdaemon requiert une autorisation exécutable. Pour plus d’informations, voir « S’assurer que le daemon dispose de l’autorisation exécutable » dans Résoudre les problèmes d’installation de [Microsoft Defender pour Endpoint sur Linux.](/microsoft-365/security/defender-endpoint/linux-support-install)

- Mémoire : 1 Go

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

- L’infrastructure `auditd` d’audit ( ) doit être activée.
  > [!NOTE]
  > Les événements système capturés par les règles ajoutées à s’ajoutent à (s) et peuvent affecter l’audit de l’hôte `/etc/audit/rules.d/` et la collecte en `audit.log` amont. Les événements ajoutés par Microsoft Defender pour Endpoint sur Linux sont marqués avec une `mdatp` clé.

### <a name="network-connections"></a>Connexions réseau

La feuille de calcul téléchargeable suivante répertorie les services et les URL associées à qui votre réseau doit pouvoir se connecter. Vous devez vous assurer qu’il n’existe aucune règle de pare-feu ou de filtrage réseau qui refuserait l’accès à ces URL. Si c’est le cas, vous devrez peut-être *créer* une règle d’autoriser spécifiquement pour eux.

| Liste de feuilles de calcul de domaines | Description |
|:-----|:-----|
|![Image miniature de la feuille de calcul DES URL de Microsoft Defender pour les points de terminaison](images/mdatp-urls.png)<br/>  | Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation. <br><br>[Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)

> [!NOTE]
> Pour obtenir une liste d’URL plus spécifique, voir [Configurer les paramètres de proxy et de connectivité Internet.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server)

Defender pour le point de terminaison peut découvrir un serveur proxy à l’aide des méthodes de découverte suivantes :
- Proxy transparent
- Configuration manuelle du proxy statique

Si un proxy ou un pare-feu bloque le trafic anonyme, assurez-vous que le trafic anonyme est autorisé dans les URL répertoriées précédemment. Pour les proxies transparents, aucune configuration supplémentaire n’est nécessaire pour Defender for Endpoint. Pour le proxy statique, suivez les étapes de [la configuration manuelle du proxy statique.](linux-static-proxy-configuration.md)

> [!WARNING]
> Les pacs, WPAD et les proxies authentifiés ne sont pas pris en charge. Assurez-vous que seul un proxy statique ou transparent est utilisé.
>
> L’inspection et l’interception des proxies SSL ne sont pas non plus pris en charge pour des raisons de sécurité. Configurez une exception pour l’inspection SSL et votre serveur proxy afin de transmettre directement les données de Defender pour Endpoint sur Linux aux URL pertinentes sans interception. L’ajout de votre certificat d’interception au magasin global n’autorise pas l’interception.

Pour les étapes de résolution des problèmes, voir Résoudre les problèmes de connectivité cloud pour [Microsoft Defender pour Endpoint sur Linux.](linux-support-connectivity.md)

## <a name="how-to-update-microsoft-defender-for-endpoint-on-linux"></a>Comment mettre à jour Microsoft Defender pour endpoint sur Linux

Microsoft publie régulièrement des mises à jour logicielles pour améliorer les performances, la sécurité et fournir de nouvelles fonctionnalités. Pour mettre à jour Microsoft Defender pour endpoint sur Linux, reportez-vous à Déployer les mises à jour [de Microsoft Defender pour Endpoint sur Linux.](linux-updates.md)

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-linux"></a>Comment configurer Microsoft Defender pour endpoint sur Linux

Des instructions sur la configuration du produit dans les environnements d’entreprise sont disponibles dans Définir les préférences [de Microsoft Defender pour Endpoint sur Linux.](linux-preferences.md)

## <a name="resources"></a>Ressources

- Pour plus d’informations sur la journalisation, la désinstallation ou d’autres rubriques, voir [Resources](linux-resources.md).
