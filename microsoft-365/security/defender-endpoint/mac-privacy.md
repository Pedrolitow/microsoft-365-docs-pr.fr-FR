---
title: Confidentialité des Microsoft Defender pour point de terminaison sur Mac
description: Contrôles de confidentialité, comment configurer les paramètres de stratégie qui ont un impact sur la confidentialité et les informations sur les données de diagnostic collectées dans Microsoft Defender pour point de terminaison sur Mac.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, confidentialité, diagnostic, catalina, big sur, monterey, ventura, mde pour mac
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
ms.openlocfilehash: 527051a2bbbc902895b1fb99d5eb5f64fea01411
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68768586"
---
# <a name="privacy-for-microsoft-defender-for-endpoint-on-macos"></a>Confidentialité des Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft s’engage à vous fournir les informations et les contrôles dont vous avez besoin pour faire des choix sur la façon dont vos données sont collectées et utilisées lorsque vous utilisez Microsoft Defender pour point de terminaison sur macOS.

Cette rubrique décrit les contrôles de confidentialité disponibles dans le produit, comment gérer ces contrôles avec des paramètres de stratégie et plus d’informations sur les événements de données collectés.

## <a name="overview-of-privacy-controls-in-microsoft-defender-for-endpoint-on-macos"></a>Vue d’ensemble des contrôles de confidentialité dans Microsoft Defender pour point de terminaison sur macOS

Cette section décrit les contrôles de confidentialité pour les différents types de données collectées par Microsoft Defender pour point de terminaison sur macOS.

### <a name="diagnostic-data"></a>Données de diagnostic

Les données de diagnostic sont utilisées pour maintenir Microsoft Defender pour point de terminaison sécurité et à jour, détecter, diagnostiquer et résoudre les problèmes, et apporter des améliorations au produit.

Certaines données de diagnostic sont obligatoires, d’autres sont facultatives. Nous vous offrons la possibilité de configurer l’envoi des données de diagnostic requises ou facultatives via des contrôles de confidentialité, comme les paramètres de stratégie des organisations.

Vous avez le choix entre deux niveaux de données de diagnostic pour Microsoft Defender pour point de terminaison logiciel client :

- **Obligatoire** : données minimales nécessaires pour maintenir Microsoft Defender pour point de terminaison sécurisé, à jour et fonctionner comme prévu sur l’appareil sur lequel il est installé.

- **Facultatif** : données supplémentaires qui aident Microsoft à apporter des améliorations au produit et fournissent des informations améliorées pour détecter, diagnostiquer et corriger les problèmes.

Par défaut, seules les données de diagnostic requises sont envoyées à Microsoft.

### <a name="cloud-delivered-protection-data"></a>Données de protection fournies par le cloud

La protection fournie par le cloud est utilisée pour fournir une protection accrue et plus rapide avec l’accès aux données de protection les plus récentes dans le cloud.

L’activation du service de protection fourni par le cloud est facultative, mais elle est fortement recommandée, car elle fournit une protection importante contre les programmes malveillants sur vos points de terminaison et sur votre réseau.

### <a name="sample-data"></a>Exemple de données

Les exemples de données sont utilisés pour améliorer les fonctionnalités de protection du produit, en envoyant des échantillons suspects à Microsoft afin qu’ils puissent être analysés. L’activation de l’envoi automatique d’exemples est facultative.

Lorsque cette fonctionnalité est activée et que l’exemple collecté est susceptible de contenir des informations personnelles, l’utilisateur est invité à donner son consentement.

## <a name="manage-privacy-controls-with-policy-settings"></a>Gérer les Contrôles de protection des données avec des paramètres de stratégie

Si vous êtes administrateur informatique, vous pouvez configurer ces contrôles au niveau de l’entreprise.

Les contrôles de confidentialité pour les différents types de données décrits dans la section précédente sont décrits en détail dans [Définir des préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md).

Comme avec les nouveaux paramètres de stratégie, vous devez les tester soigneusement dans un environnement limité et contrôlé pour vous assurer que les paramètres que vous configurez ont l’effet souhaité avant d’implémenter les paramètres de stratégie plus largement dans votre organisation.

## <a name="diagnostic-data-events"></a>Événements de données de diagnostic

Cette section décrit les données de diagnostic requises et les données de diagnostic facultatives, ainsi qu’une description des événements et des champs collectés.

### <a name="data-fields-that-are-common-for-all-events"></a>Champs de données communs à tous les événements

Voici quelques informations sur les événements qui sont communs à tous les événements, indépendamment de la catégorie ou du sous-type de données.

Les champs suivants sont considérés comme communs pour tous les événements :

|Champ|Description|
|---|---|
|platform|Classification générale de la plateforme sur laquelle l’application s’exécute. Permet à Microsoft d’identifier sur quelles plateformes un problème peut se produire afin qu’il puisse être correctement hiérarchisé.|
|machine_guid|Identificateur unique associé à l’appareil. Permet à Microsoft d’identifier si les problèmes affectent un ensemble sélectionné d’installations et le nombre d’utilisateurs concernés.|
|sense_guid|Identificateur unique associé à l’appareil. Permet à Microsoft d’identifier si les problèmes affectent un ensemble sélectionné d’installations et le nombre d’utilisateurs concernés.|
|org_id|Identificateur unique associé à l’entreprise à laquelle appartient l’appareil. Permet à Microsoft d’identifier si les problèmes affectent un ensemble sélectionné d’entreprises et le nombre d’entreprises concernées.|
|Hostname|Nom de l’appareil local (sans suffixe DNS). Permet à Microsoft d’identifier si les problèmes affectent un ensemble sélectionné d’installations et le nombre d’utilisateurs concernés.|
|product_guid|Identificateur unique du produit. Permet à Microsoft de différencier les problèmes affectant différentes saveurs du produit.|
|app_version|Version du Microsoft Defender pour point de terminaison sur l’application macOS. Permet à Microsoft d’identifier les versions du produit qui présentent un problème afin qu’il puisse être correctement hiérarchisé.|
|sig_version|Version de la base de données security intelligence. Permet à Microsoft d’identifier les versions du renseignement de sécurité qui présentent un problème afin qu’il puisse être correctement hiérarchisé.|
|supported_compressions|Liste des algorithmes de compression pris en charge par l’application, par exemple `['gzip']`. Permet à Microsoft de comprendre quels types de compressions peuvent être utilisés lorsqu’il communique avec l’application.|
|release_ring|Sonnerie à laquelle l’appareil est associé (par exemple Insider Fast, Insider Slow, Production). Permet à Microsoft d’identifier sur quel anneau de mise en production un problème peut se produire afin qu’il puisse être correctement hiérarchisé.|

### <a name="required-diagnostic-data"></a>Données de diagnostic requises

**Les données de diagnostic requises** sont les données minimales nécessaires pour maintenir Microsoft Defender pour point de terminaison sécurisé, à jour et fonctionner comme prévu sur l’appareil sur lequel elles sont installées.

Les données de diagnostic requises permettent d’identifier les problèmes liés aux Microsoft Defender pour point de terminaison qui peuvent être liés à une configuration d’appareil ou de logiciel. Par exemple, il peut aider à déterminer si une fonctionnalité Microsoft Defender pour point de terminaison se bloque plus fréquemment sur une version particulière du système d’exploitation, avec des fonctionnalités nouvellement introduites ou quand certaines fonctionnalités Microsoft Defender pour point de terminaison sont désactivées. Les données de diagnostic requises aident Microsoft à détecter, diagnostiquer et résoudre ces problèmes plus rapidement afin de réduire l’impact sur les utilisateurs ou les organisations.

#### <a name="software-setup-and-inventory-data-events"></a>Événements de données liés à l’inventaire et à la configuration des logiciels

**installation/désinstallation Microsoft Defender pour point de terminaison** :

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|correlation_id|Identificateur unique associé à l’installation.|
|version|Version du package.|
|Sévérité |Gravité du message (par exemple, Information).|
|code|Code qui décrit l’opération.|
|text|Informations supplémentaires associées à l’installation du produit.|

**Microsoft Defender pour point de terminaison configuration** :

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|antivirus_engine.enable_real_time_protection|Indique si la protection en temps réel est activée sur l’appareil ou non.|
|antivirus_engine.passive_mode|Indique si le mode passif est activé ou non sur l’appareil.|
|cloud_service.enabled|Indique si la protection fournie par le cloud est activée sur l’appareil ou non.|
|cloud_service.timeout|Délai d’expiration lorsque l’application communique avec le cloud Microsoft Defender pour point de terminaison.|
|cloud_service.heartbeat_interval|Intervalle entre les pulsations consécutives envoyées par le produit au cloud.|
|cloud_service.service_uri|URI utilisé pour communiquer avec le cloud.|
|cloud_service.diagnostic_level|Niveau de diagnostic de l’appareil (obligatoire, facultatif).|
|cloud_service.automatic_sample_submission|Indique si l’envoi automatique d’échantillons est activé ou non.|
|cloud_service.automatic_definition_update_enabled|Indique si la mise à jour automatique des définitions est activée ou non.|
|edr.early_preview|Indique si l’appareil doit exécuter les fonctionnalités EDR en préversion anticipée.|
|edr.group_id|Identificateur de groupe utilisé par le composant de détection et de réponse.|
|edr.tags|Balises définies par l’utilisateur.|
|fonctionnalités.\[ nom de la fonctionnalité facultative\]|Liste des fonctionnalités en préversion, indiquant si elles sont activées ou non.|

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
|v1_crash_count|Nombre de blocages du processus du moteur V1 toutes les heures sur l’ordinateur client|
|v2_crash_count|Nombre de blocages du processus du moteur V2 toutes les heures sur l’ordinateur client|
|EDR_crash_count|Nombre de blocages du processus EDR toutes les heures sur l’ordinateur client|

**Statistiques d’extension du noyau** :

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|version|Version de Microsoft Defender pour point de terminaison sur macOS.|
|instance_id|Identificateur unique généré au démarrage de l’extension du noyau.|
|trace_level|Niveau de trace de l’extension du noyau.|
|Sous-système|Sous-système sous-jacent utilisé pour la protection en temps réel.|
|ipc.connects|Nombre de demandes de connexion reçues par l’extension du noyau.|
|ipc.rejects|Nombre de demandes de connexion rejetées par l’extension du noyau.|
|ipc.connected|Indique s’il existe une connexion active à l’extension du noyau.|

#### <a name="support-data"></a>Données de support

**Journaux de diagnostic** :

Les journaux de diagnostic sont collectés uniquement avec le consentement de l’utilisateur dans le cadre de la fonctionnalité de soumission de commentaires. Les fichiers suivants sont collectés dans les journaux de support :

- Tous les fichiers sous */Library/Logs/Microsoft/mdatp/*
- Sous-ensemble de fichiers sous */Library/Application Support/Microsoft/Defender/* qui sont créés et utilisés par Microsoft Defender pour point de terminaison sur macOS
- Sous-ensemble de fichiers sous */Library/Managed Preferences* qui sont utilisés par Microsoft Defender pour point de terminaison sur macOS
- /Library/Logs/Microsoft/autoupdate.log
- $HOME/Library/Preferences/com.microsoft.autoupdate2.plist

### <a name="optional-diagnostic-data"></a>Données de diagnostic facultatives

**Les données de diagnostic facultatives** sont des données supplémentaires qui aident Microsoft à améliorer le produit et fournissent des informations améliorées pour détecter, diagnostiquer et résoudre les problèmes.

Si vous choisissez d’envoyer des données de diagnostic facultatives, les données de diagnostic requises sont également incluses.

Parmi les exemples de données de diagnostic facultatives, citons les données collectées par Microsoft sur la configuration du produit (par exemple le nombre d’exclusions définies sur l’appareil) et les performances du produit (mesures agrégées sur les performances des composants du produit).

#### <a name="software-setup-and-inventory-data-events-for-optional-diagnostic-data"></a>Événements de données de configuration logicielle et d’inventaire pour les données de diagnostic facultatives

**Microsoft Defender pour point de terminaison configuration** :

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|connection_retry_timeout|Délai d’expiration des nouvelles tentatives de connexion lors de la communication avec le cloud.|
|file_hash_cache_maximum|Taille du cache de produit.|
|crash_upload_daily_limit|Limite de journaux d’incident chargés quotidiennement.|
|antivirus_engine.exclusions[].is_directory|Indique si l’exclusion de l’analyse est un répertoire ou non.|
|antivirus_engine.exclusions[].path|Chemin qui a été exclu de l’analyse.|
|antivirus_engine.exclusions[].extension|Extension exclue de l’analyse.|
|antivirus_engine.exclusions[].name|Nom du fichier exclu de l’analyse.|
|antivirus_engine.scan_cache_maximum|Taille du cache de produit.|
|antivirus_engine.maximum_scan_threads|Nombre maximal de threads utilisés pour l’analyse.|
|antivirus_engine.threat_restoration_exclusion_time|Délai d’attente avant qu’un fichier restauré à partir de la quarantaine puisse être détecté à nouveau.|
|antivirus_engine.threat_type_settings|Configuration de la façon dont les différents types de menaces sont gérés par le produit.|
|filesystem_scanner.full_scan_directory|Répertoire d’analyse complète.|
|filesystem_scanner.quick_scan_directories|Liste des répertoires utilisés dans l’analyse rapide.|
|edr.latency_mode|Mode de latence utilisé par le composant de détection et de réponse.|
|edr.proxy_address|Adresse proxy utilisée par le composant de détection et de réponse.|

**Configuration de Microsoft Auto-Update** :

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|how_to_check|Détermine la façon dont les mises à jour de produit sont vérifiées (par exemple, automatique ou manuelle).|
|channel_name|Canal de mise à jour associé à l’appareil.|
|manifest_server|Serveur utilisé pour télécharger les mises à jour.|
|update_cache|Emplacement du cache utilisé pour stocker les mises à jour.|

### <a name="product-and-service-usage"></a>Utilisation des produits et services

#### <a name="diagnostic-log-upload-started-report"></a>Rapport de chargement du journal de diagnostic démarré

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

#### <a name="product-and-service-performance-data-events-for-product-and-service-usage"></a>Événements de données de performances de produit et de service pour l’utilisation des produits et services

**Sortie inattendue de l’application (plantage)** :

Sorties inattendues de l’application et état de celle-ci lorsque cela se produit.

**Statistiques d’extension du noyau** :

Les champs collectés sont les suivants :

|Champ|Description|
|---|---|
|pkt_ack_timeout|Les propriétés suivantes sont des valeurs numériques agrégées, représentant le nombre d’événements qui se sont produits depuis le démarrage de l’extension du noyau.|
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
