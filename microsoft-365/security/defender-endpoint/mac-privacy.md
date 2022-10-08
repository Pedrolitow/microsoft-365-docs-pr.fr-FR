---
title: Confidentialité des Microsoft Defender pour point de terminaison sur Mac
description: Contrôles de confidentialité, configuration des paramètres de stratégie qui ont un impact sur la confidentialité et les informations sur les données de diagnostic collectées dans Microsoft Defender pour point de terminaison sur Mac.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, confidentialité, diagnostic
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
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 96a44fd7bd80d0d348928860be9d97a6d0cc68a6
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68229435"
---
# <a name="privacy-for-microsoft-defender-for-endpoint-on-macos"></a>Confidentialité des Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft s’engage à vous fournir les informations et les contrôles dont vous avez besoin pour faire des choix sur la façon dont vos données sont collectées et utilisées lorsque vous utilisez Microsoft Defender pour point de terminaison sur macOS.

Cette rubrique décrit les contrôles de confidentialité disponibles dans le produit, comment gérer ces contrôles avec des paramètres de stratégie et plus de détails sur les événements de données collectés.

## <a name="overview-of-privacy-controls-in-microsoft-defender-for-endpoint-on-macos"></a>Vue d’ensemble des contrôles de confidentialité dans Microsoft Defender pour point de terminaison sur macOS

Cette section décrit les contrôles de confidentialité pour les différents types de données collectées par Microsoft Defender pour point de terminaison sur macOS.

### <a name="diagnostic-data"></a>Données de diagnostic

Les données de diagnostic sont utilisées pour maintenir Microsoft Defender pour point de terminaison sécurisées et à jour, détecter, diagnostiquer et résoudre les problèmes, ainsi que pour apporter des améliorations aux produits.

Certaines données de diagnostic sont obligatoires, d’autres sont facultatives. Nous vous offrons la possibilité de configurer l’envoi des données de diagnostic requises ou facultatives via des contrôles de confidentialité, comme les paramètres de stratégie des organisations.

Il existe deux niveaux de données de diagnostic pour Microsoft Defender pour point de terminaison logiciel client parmi lesquels vous pouvez choisir :

- **Obligatoire** : données minimales nécessaires pour maintenir Microsoft Defender pour point de terminaison sécurisé, à jour et performants comme prévu sur l’appareil sur lequel il est installé.

- **Facultatif** : données supplémentaires qui aident Microsoft à apporter des améliorations aux produits et fournit des informations améliorées pour vous aider à détecter, diagnostiquer et corriger les problèmes.

Par défaut, seules les données de diagnostic requises sont envoyées à Microsoft.

### <a name="cloud-delivered-protection-data"></a>Données de protection fournies par le cloud

La protection fournie par le cloud est utilisée pour fournir une protection accrue et plus rapide avec l’accès aux données de protection les plus récentes dans le cloud.

L’activation du service de protection fournie par le cloud est facultative, mais elle est fortement recommandée, car elle offre une protection importante contre les programmes malveillants sur vos points de terminaison et sur votre réseau.

### <a name="sample-data"></a>Exemple de données

Les exemples de données sont utilisés pour améliorer les fonctionnalités de protection du produit, en envoyant des exemples suspects Microsoft afin qu’ils puissent être analysés. L’activation de la soumission automatique d’exemples est facultative.

Lorsque cette fonctionnalité est activée et que l’exemple collecté est susceptible de contenir des informations personnelles, l’utilisateur est invité à donner son consentement.

## <a name="manage-privacy-controls-with-policy-settings"></a>Gérer les Contrôles de protection des données avec des paramètres de stratégie

Si vous êtes administrateur informatique, vous souhaiterez peut-être configurer ces contrôles au niveau de l’entreprise.

Les contrôles de confidentialité pour les différents types de données décrits dans la section précédente sont décrits en détail dans [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md).

Comme pour tous les nouveaux paramètres de stratégie, vous devez les tester soigneusement dans un environnement limité et contrôlé pour vous assurer que les paramètres que vous configurez ont l’effet souhaité avant d’implémenter les paramètres de stratégie plus largement dans votre organisation.

## <a name="diagnostic-data-events"></a>Événements de données de diagnostic

Cette section décrit les données de diagnostic requises et les données de diagnostic facultatives, ainsi qu’une description des événements et des champs collectés.

### <a name="data-fields-that-are-common-for-all-events"></a>Champs de données communs à tous les événements

Voici quelques informations sur les événements qui sont communs à tous les événements, indépendamment de la catégorie ou du sous-type de données.

Les champs suivants sont considérés comme courants pour tous les événements :

|Champ|Description|
|---|---|
|platform|Classification générale de la plateforme sur laquelle l’application s’exécute. Permet à Microsoft d’identifier sur quelles plateformes un problème peut se produire afin qu’il puisse être correctement hiérarchisé.|
|machine_guid|Identificateur unique associé à l’appareil. Permet à Microsoft d’identifier si les problèmes affectent un ensemble sélectionné d’installations et le nombre d’utilisateurs concernés.|
|sense_guid|Identificateur unique associé à l’appareil. Permet à Microsoft d’identifier si les problèmes affectent un ensemble sélectionné d’installations et le nombre d’utilisateurs concernés.|
|org_id|Identificateur unique associé à l’entreprise à laquelle appartient l’appareil. Permet à Microsoft d’identifier si les problèmes affectent un ensemble sélectionné d’entreprises et le nombre d’entreprises concernées.|
|Hostname|Nom de l’appareil local (sans suffixe DNS). Permet à Microsoft d’identifier si les problèmes affectent un ensemble sélectionné d’installations et le nombre d’utilisateurs concernés.|
|product_guid|Identificateur unique du produit. Permet à Microsoft de différencier les problèmes qui ont un impact sur les différentes versions du produit.|
|app_version|Version du Microsoft Defender pour point de terminaison sur l’application macOS. Permet à Microsoft d’identifier les versions du produit présentant un problème afin qu’il puisse être correctement hiérarchisé.|
|sig_version|Version de la base de données security intelligence. Permet à Microsoft d’identifier les versions du renseignement de sécurité présentant un problème afin qu’il puisse être correctement hiérarchisé.|
|supported_compressions|Liste des algorithmes de compression pris en charge par l’application, par exemple `['gzip']`. Permet à Microsoft de comprendre quels types de compressions peuvent être utilisés lorsqu’il communique avec l’application.|
|release_ring|Anneau auquel l’appareil est associé (par exemple Insider Fast, Insider Slow, Production). Permet à Microsoft d’identifier sur quel anneau de mise en production un problème peut se produire afin qu’il puisse être correctement hiérarchisé.|

### <a name="required-diagnostic-data"></a>Données de diagnostic requises

**Les données de diagnostic requises** sont les données minimales nécessaires pour garantir Microsoft Defender pour point de terminaison sécurité, la mise à jour et les performances attendues sur l’appareil sur lequel elle est installée.

Les données de diagnostic requises permettent d’identifier les problèmes liés aux Microsoft Defender pour point de terminaison qui peuvent être liés à une configuration d’appareil ou de logiciel. Par exemple, il peut aider à déterminer si une fonctionnalité Microsoft Defender pour point de terminaison se bloque plus fréquemment sur une version particulière du système d’exploitation, avec des fonctionnalités nouvellement introduites, ou quand certaines fonctionnalités Microsoft Defender pour point de terminaison sont désactivées. Les données de diagnostic requises aident Microsoft à détecter, diagnostiquer et résoudre ces problèmes plus rapidement afin de réduire l’impact sur les utilisateurs ou les organisations.

#### <a name="software-setup-and-inventory-data-events"></a>Événements de données liés à l’inventaire et à la configuration des logiciels

**Microsoft Defender pour point de terminaison installation/désinstallation** :

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|correlation_id|Identificateur unique associé à l’installation.|
|version|Version du package.|
|Sévérité |Gravité du message (par exemple Informational).|
|code|Code qui décrit l’opération.|
|text|Informations supplémentaires associées à l’installation du produit.|

**configuration Microsoft Defender pour point de terminaison** :

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|antivirus_engine.enable_real_time_protection|Indique si la protection en temps réel est activée ou non sur l’appareil.|
|antivirus_engine.passive_mode|Indique si le mode passif est activé ou non sur l’appareil.|
|cloud_service.enabled|Indique si la protection fournie par le cloud est activée ou non sur l’appareil.|
|cloud_service.timeout|Délai d’expiration lorsque l’application communique avec le cloud Microsoft Defender pour point de terminaison.|
|cloud_service.heartbeat_interval|Intervalle entre les pulsations consécutives envoyées par le produit au cloud.|
|cloud_service.service_uri|URI utilisé pour communiquer avec le cloud.|
|cloud_service.diagnostic_level|Niveau de diagnostic de l’appareil (obligatoire, facultatif).|
|cloud_service.automatic_sample_submission|Indique si l’envoi automatique d’exemples est activé ou non.|
|cloud_service.automatic_definition_update_enabled|Indique si la mise à jour automatique des définitions est activée ou non.|
|edr.early_preview|Indique si l’appareil doit exécuter les fonctionnalités EDR en préversion anticipée.|
|edr.group_id|Identificateur de groupe utilisé par le composant de détection et de réponse.|
|edr.tags|Balises définies par l’utilisateur.|
|fonctionnalités.\[ nom de fonctionnalité facultatif\]|Liste des fonctionnalités en préversion, ainsi que leur activation ou non.|

#### <a name="product-and-service-usage-data-events"></a>Événements de données liés à l'utilisation des produits et services

**Rapport de mise à jour du renseignement de sécurité** :

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|from_version|Version d’origine du renseignement de sécurité.|
|to_version|Nouvelle version du renseignement de sécurité.|
|status|État de la mise à jour indiquant la réussite ou l’échec.|
|using_proxy|Indique si la mise à jour a été effectuée via un proxy.|
|error|Code d’erreur si la mise à jour a échoué.|
|reason (Raison)|Message d’erreur si la mise à jour a été déposée.|

#### <a name="product-and-service-performance-data-events-for-required-diagnostic-data"></a>Événements de données de performances de produit et de service pour les données de diagnostic requises

**Sortie inattendue de l’application (plantage)** :

Collecte les informations système et l’état d’une application lorsqu’une application se ferme de manière inattendue.

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|v1_crash_count|Nombre de fois où le processus du moteur V1 s’est écrasé toutes les heures sur la machine cliente|
|v2_crash_count|Nombre de fois où le processus du moteur V2 s’est écrasé toutes les heures sur la machine cliente|
|EDR_crash_count|Nombre de fois que le processus EDR s’est écrasé toutes les heures sur la machine cliente|

**Statistiques d’extension de noyau :**

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|version|Version de Microsoft Defender pour point de terminaison sur macOS.|
|instance_id|Identificateur unique généré au démarrage de l’extension de noyau.|
|trace_level|Niveau de trace de l’extension de noyau.|
|Sous-système|Sous-système sous-jacent utilisé pour la protection en temps réel.|
|ipc.connects|Nombre de demandes de connexion reçues par l’extension de noyau.|
|ipc.rejects|Nombre de demandes de connexion rejetées par l’extension de noyau.|
|ipc.connected|Indique s’il existe une connexion active à l’extension du noyau.|

#### <a name="support-data"></a>Données de support

**Journaux de diagnostic :**

Les journaux de diagnostic sont collectés uniquement avec le consentement de l’utilisateur dans le cadre de la fonctionnalité de soumission de commentaires. Les fichiers suivants sont collectés dans le cadre des journaux de support :

- Tous les fichiers sous */Library/Logs/Microsoft/mdatp/*
- Sous-ensemble de fichiers sous */Library/Application Support/Microsoft/Defender/* créés et utilisés par Microsoft Defender pour point de terminaison sur macOS
- Sous-ensemble de fichiers sous */Library/Managed Preferences utilisés* par Microsoft Defender pour point de terminaison sur macOS
- /Library/Logs/Microsoft/autoupdate.log
- $HOME/Library/Preferences/com.microsoft.autoupdate2.plist

### <a name="optional-diagnostic-data"></a>Données de diagnostic facultatives

**Les données de diagnostic facultatives** sont des données supplémentaires qui aident Microsoft à apporter des améliorations aux produits et fournit des informations améliorées pour vous aider à détecter, diagnostiquer et résoudre les problèmes.

Si vous choisissez d’envoyer des données de diagnostic facultatives, les données de diagnostic requises sont également incluses.

Parmi les exemples de données de diagnostic facultatives, citons les données collectées par Microsoft sur la configuration du produit (par exemple, le nombre d’exclusions définies sur l’appareil) et les performances du produit (mesures agrégées sur les performances des composants du produit).

#### <a name="software-setup-and-inventory-data-events-for-optional-diagnostic-data"></a>Événements de données d’inventaire et d’installation de logiciels pour les données de diagnostic facultatives

**configuration Microsoft Defender pour point de terminaison** :

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|connection_retry_timeout|Délai d’expiration de la nouvelle tentative de connexion lors de la communication avec le cloud.|
|file_hash_cache_maximum|Taille du cache de produit.|
|crash_upload_daily_limit|Limite des journaux d’activité d’incident chargés quotidiennement.|
|antivirus_engine.exclusions[].is_directory|Indique si l’exclusion de l’analyse est un répertoire ou non.|
|antivirus_engine.exclusions[].path|Chemin d’accès exclu de l’analyse.|
|antivirus_engine.exclusions[].extension|Extension exclue de l’analyse.|
|antivirus_engine.exclusions[].name|Nom du fichier exclu de l’analyse.|
|antivirus_engine.scan_cache_maximum|Taille du cache de produit.|
|antivirus_engine.maximum_scan_threads|Nombre maximal de threads utilisés pour l’analyse.|
|antivirus_engine.threat_restoration_exclusion_time|Délai d’expiration avant qu’un fichier restauré à partir de la mise en quarantaine puisse être détecté à nouveau.|
|antivirus_engine.threat_type_settings|Configuration de la façon dont les différents types de menaces sont gérés par le produit.|
|filesystem_scanner.full_scan_directory|Répertoire d’analyse complet.|
|filesystem_scanner.quick_scan_directories|Liste des répertoires utilisés dans l’analyse rapide.|
|edr.latency_mode|Mode de latence utilisé par le composant de détection et de réponse.|
|edr.proxy_address|Adresse proxy utilisée par le composant de détection et de réponse.|

**Configuration de la mise à jour automatique Microsoft** :

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|how_to_check|Détermine la façon dont les mises à jour du produit sont vérifiées (par exemple, automatiques ou manuelles).|
|channel_name|Mettre à jour le canal associé à l’appareil.|
|manifest_server|Serveur utilisé pour télécharger les mises à jour.|
|update_cache|Emplacement du cache utilisé pour stocker les mises à jour.|

### <a name="product-and-service-usage"></a>Utilisation des produits et services

#### <a name="diagnostic-log-upload-started-report"></a>Rapport de démarrage du chargement du journal de diagnostic

Les champs suivants sont affichés :

|Champ|Description|
|---|---|
|sha256|Identificateur SHA256 du journal de support.|
|size|Taille du journal de support.|
|original_path|Chemin d’accès au journal de support (toujours sous */Library/Application Support/Microsoft/Defender/wdavdiag/*).|
|format|Format du journal de support.|
|Métadonnées|Informations sur le contenu du journal de support.|

#### <a name="diagnostic-log-upload-completed-report"></a>Rapport terminé sur le chargement du journal de diagnostic

Les champs suivants sont affichés :

|Champ|Description|
|---|---|
|request_id|ID de corrélation pour la demande de chargement du journal de support.|
|sha256|Identificateur SHA256 du journal de support.|
|blob_sas_uri|URI utilisé par l’application pour charger le journal de support.|

#### <a name="product-and-service-performance-data-events-for-product-and-service-usage"></a>Événements de données de performances de produit et de service pour l’utilisation des produits et des services

**Sortie inattendue de l’application (plantage)** :

Sorties inattendues de l’application et état de celle-ci lorsque cela se produit.

**Statistiques d’extension de noyau :**

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|pkt_ack_timeout|Les propriétés suivantes sont des valeurs numériques agrégées, représentant le nombre d’événements qui se sont produits depuis le démarrage de l’extension de noyau.|
|pkt_ack_conn_timeout||
|ipc.ack_pkts||
|ipc.nack_pkts||
|ipc.send.ack_no_conn||
|ipc.send.nack_no_conn||
|ipc.send.ack_no_qsq||
|ipc.send.nack_no_qsq||
|ipc.ack.no_space||
|ipc.ack.timeout||
|ipc.ack.ackd_fast||
|ipc.ack.ackd||
|ipc.recv.bad_pkt_len||
|ipc.recv.bad_reply_len||
|ipc.recv.no_waiter||
|ipc.recv.copy_failed||
|ipc.kauth.vnode.mask||
|ipc.kauth.vnode.read||
|ipc.kauth.vnode.write||
|ipc.kauth.vnode.exec||
|ipc.kauth.vnode.del||
|ipc.kauth.vnode.read_attr||
|ipc.kauth.vnode.write_attr||
|ipc.kauth.vnode.read_ex_attr||
|ipc.kauth.vnode.write_ex_attr||
|ipc.kauth.vnode.read_sec||
|ipc.kauth.vnode.write_sec||
|ipc.kauth.vnode.take_own||
|ipc.kauth.vnode.link||
|ipc.kauth.vnode.create||
|ipc.kauth.vnode.move||
|ipc.kauth.vnode.mount||
|ipc.kauth.vnode.denied||
|ipc.kauth.vnode.ackd_before_deadline||
|ipc.kauth.vnode.missed_deadline||
|ipc.kauth.file_op.mask||
|ipc.kauth_file_op.open||
|ipc.kauth.file_op.close||
|ipc.kauth.file_op.close_modified||
|ipc.kauth.file_op.move||
|ipc.kauth.file_op.link||
|ipc.kauth.file_op.exec||
|ipc.kauth.file_op.remove||
|ipc.kauth.file_op.unmount||
|ipc.kauth.file_op.fork||
|ipc.kauth.file_op.create||

## <a name="resources"></a>Ressources

- [Confidentialité chez Microsoft](https://privacy.microsoft.com/)
