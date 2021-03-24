---
title: Confidentialité pour Microsoft Defender ATP pour Mac
description: Contrôles de confidentialité, comment configurer les paramètres de stratégie qui ont une incidence sur la confidentialité et les informations sur les données de diagnostic collectées dans Microsoft Defender ATP pour Mac.
keywords: microsoft, defender, atp, mac, confidentialité, diagnostic
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
ms.openlocfilehash: 0d8a5add74cad89a4635d112b29e6495199e0e1d
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064118"
---
# <a name="privacy-for-microsoft-defender-for-endpoint-for-mac"></a>Confidentialité pour Microsoft Defender pour point de terminaison pour Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 


Microsoft s’engage à vous fournir les informations et les contrôles dont vous avez besoin pour faire des choix sur la façon dont vos données sont collectées et utilisées lorsque vous utilisez Microsoft Defender pour Endpoint pour Mac.

Cette rubrique décrit les contrôles de confidentialité disponibles dans le produit, comment gérer ces contrôles avec des paramètres de stratégie et plus d’informations sur les événements de données collectés.

## <a name="overview-of-privacy-controls-in-microsoft-defender-for-endpoint-for-mac"></a>Vue d’ensemble des contrôles de confidentialité dans Microsoft Defender pour Endpoint pour Mac

Cette section décrit les contrôles de confidentialité pour les différents types de données collectées par Microsoft Defender pour Endpoint pour Mac.

### <a name="diagnostic-data"></a>Données de diagnostic

Les données de diagnostic sont utilisées pour sécuriser et mettre à jour Microsoft Defender for Endpoint, détecter, diagnostiquer et résoudre les problèmes, ainsi que pour améliorer les produits.

Certaines données de diagnostic sont obligatoires, d’autres sont facultatives. Nous vous offrons la possibilité de configurer l’envoi des données de diagnostic requises ou facultatives via des contrôles de confidentialité, comme les paramètres de stratégie des organisations.

Vous pouvez choisir parmi deux niveaux de données de diagnostic pour le logiciel client Microsoft Defender for Endpoint :

* **Obligatoire**: données minimales nécessaires pour assurer la sécurité, la mise à jour et les résultats de Microsoft Defender for Endpoint sur l’appareil sur laquelle il est installé.

* **Facultatif**: données supplémentaires qui aident Microsoft à améliorer les produits et fournissent des informations améliorées pour vous aider à détecter, diagnostiquer et résoudre les problèmes.

Par défaut, seules les données de diagnostic requises sont envoyées à Microsoft.

### <a name="cloud-delivered-protection-data"></a>Données de protection cloud

La protection fournie par le cloud est utilisée pour fournir une protection accrue et plus rapide avec l’accès aux dernières données de protection dans le cloud.

L’activation du service de protection cloud est facultative, mais elle est vivement recommandée, car elle offre une protection importante contre les programmes malveillants sur vos points de terminaison et sur votre réseau.

### <a name="sample-data"></a>Exemple de données

Des exemples de données sont utilisés pour améliorer les fonctionnalités de protection du produit, en envoyant des exemples suspects Microsoft afin qu’ils soient analysés. L’activation de l’envoi automatique d’échantillons est facultative.

Lorsque cette fonctionnalité est activée et que l’exemple collecté est susceptible de contenir des informations personnelles, l’utilisateur est invité à donner son consentement.

## <a name="manage-privacy-controls-with-policy-settings"></a>Gérer les Contrôles de protection des données avec des paramètres de stratégie

Si vous êtes un administrateur informatique, vous pouvez configurer ces contrôles au niveau de l’entreprise. 

Les contrôles de confidentialité pour les différents types de données décrits dans la section précédente sont décrits en détail dans Définir les préférences de [Microsoft Defender pour Endpoint pour Mac.](mac-preferences.md)

Comme avec les nouveaux paramètres de stratégie, vous devez les tester avec soin dans un environnement limité et contrôlé pour vous assurer que les paramètres que vous configurez ont l’effet souhaité avant d’implémenter les paramètres de stratégie plus largement dans votre organisation.

## <a name="diagnostic-data-events"></a>Événements de données de diagnostic

Cette section décrit ce qui est considéré comme des données de diagnostic requises et ce qui est considéré comme des données de diagnostic facultatives, ainsi qu’une description des événements et des champs collectés.

### <a name="data-fields-that-are-common-for-all-events"></a>Champs de données communs à tous les événements
Voici quelques informations sur les événements qui sont communs à tous les événements, indépendamment de la catégorie ou du sous-type de données. 

Les champs suivants sont considérés comme courants pour tous les événements :

| Champ                   | Description |
| ----------------------- | ----------- |
| platform                | Classification large de la plateforme sur laquelle l’application est en cours d’exécution. Permet à Microsoft d’identifier sur quelles plateformes un problème peut se produire afin qu’il puisse être correctement hiérarchisé. |
| machine_guid            | Identificateur unique associé à l’appareil. Permet à Microsoft d’identifier si des problèmes ont un impact sur un ensemble d’installation sélectionné et le nombre d’utilisateurs touchés. |
| sense_guid              | Identificateur unique associé à l’appareil. Permet à Microsoft d’identifier si des problèmes ont un impact sur un ensemble d’installation sélectionné et le nombre d’utilisateurs touchés. |
| org_id                  | Identificateur unique associé à l’entreprise à qui appartient l’appareil. Permet à Microsoft d’identifier si les problèmes ont un impact sur un ensemble d’entreprises sélectionné et le nombre d’entreprises qui en sont touchées. |
| hostname                | Nom de l’appareil local (sans suffixe DNS). Permet à Microsoft d’identifier si des problèmes ont un impact sur un ensemble d’installation sélectionné et le nombre d’utilisateurs touchés. |
| product_guid            | Identificateur unique du produit. Permet à Microsoft de différencier les problèmes qui ont un impact sur les différentes types de produit. |
| app_version             | Version de l’application Microsoft Defender pour Point de terminaison pour Mac. Permet à Microsoft d’identifier les versions du produit qui affichent un problème afin qu’il puisse être correctement hiérarchisé.|
| sig_version             | Version de la base de données d’informations de sécurité. Permet à Microsoft d’identifier les versions de l’intelligence de sécurité qui affichent un problème afin qu’il puisse être correctement hiérarchisé. |
| supported_compressions  | Liste des algorithmes de compression pris en charge par l’application, par `['gzip']` exemple. Permet à Microsoft de comprendre les types de compressions qui peuvent être utilisés lorsqu’il communique avec l’application. |
| release_ring            | Sonnerie à l’appareil (par exemple Insider Fast, Insider Slow, Production). Permet à Microsoft d’identifier l’anneau de publication sur lequel un problème peut se produire afin qu’il puisse être correctement hiérarchisé. |


### <a name="required-diagnostic-data"></a>Données de diagnostic requises

**Les données de diagnostic** requises sont les données minimales nécessaires pour assurer la sécurité, la mise à jour et la mise à jour de Microsoft Defender for Endpoint sur l’appareil sur laquelle il est installé.

Les données de diagnostic requises permettent d’identifier les problèmes avec Microsoft Defender pour point de terminaison qui peuvent être liés à une configuration d’appareil ou de logiciel. Par exemple, il peut aider à déterminer si une fonctionnalité De Microsoft Defender pour point de terminaison se crashe plus fréquemment sur une version de système d’exploitation particulière, avec les fonctionnalités nouvellement introduites ou lorsque certaines fonctionnalités de Microsoft Defender pour le point de terminaison sont désactivées. Les données de diagnostic requises aident Microsoft à détecter, diagnostiquer et résoudre ces problèmes plus rapidement afin de réduire l’impact sur les utilisateurs ou les organisations.

#### <a name="software-setup-and-inventory-data-events"></a>Événements de données liés à l’inventaire et à la configuration des logiciels

**Installation/désinstallation de Microsoft Defender for Endpoint**

Les champs suivants sont affichés :

| Champ            | Description |
| ---------------- | ----------- |
| correlation_id   | Identificateur unique associé à l’installation. |
| version          | Version du package. |
| Sévérité          | Gravité du message (par exemple, Informations). |
| code             | Code qui décrit l’opération. |
| text             | Informations supplémentaires associées à l’installation du produit. |

**Configuration de Microsoft Defender pour point de terminaison**

Les champs suivants sont affichés :

| Champ                                               | Description |
| --------------------------------------------------- | ----------- |
| antivirus_engine.enable_real_time_protection        | Si la protection en temps réel est activée sur l’appareil ou non. |
| antivirus_engine.passive_mode                       | Si le mode passif est activé sur l’appareil ou non. |
| cloud_service.enabled                               | Si la protection cloud est activée sur l’appareil ou non. |
| cloud_service.timeout                               | Délai d’arrêt lorsque l’application communique avec microsoft Defender pour le cloud de point de terminaison. |
| cloud_service.heartbeat_interval                    | Intervalle entre les pulsations consécutives envoyées par le produit au cloud. |
| cloud_service.service_uri                           | URI utilisé pour communiquer avec le cloud. |
| cloud_service.diagnostic_level                      | Niveau de diagnostic de l’appareil (obligatoire, facultatif). |
| cloud_service.automatic_sample_submission           | Si l’envoi automatique d’échantillons est allumé ou non. |
| edr.early_preview                                   | Si l’appareil doit exécuter les fonctionnalités d’aperçu préliminaire d’EDR. |
| edr.group_id                                        | Identificateur de groupe utilisé par le composant de détection et de réponse. |
| edr.tags                                            | Balises définies par l’utilisateur. |
| fonctionnalités. \[ nom de fonctionnalité facultatif\]                  | Liste des fonctionnalités d’aperçu, ainsi que si elles sont activées ou non. |

#### <a name="product-and-service-usage-data-events"></a>Événements de données liés à l'utilisation des produits et services

**Rapport de mise à jour de l’intelligence de la sécurité**

Les champs suivants sont affichés :

| Champ            | Description |
| ---------------- | ----------- |
| from_version     | Version d’origine de l’intelligence de sécurité. |
| to_version       | Nouvelle version de l’intelligence de la sécurité. |
| statut           | État de la mise à jour indiquant la réussite ou l’échec. |
| using_proxy      | Si la mise à jour a été effectuée sur un proxy. |
| error            | Code d’erreur en cas d’échec de la mise à jour. |
| reason (Raison)           | Message d’erreur si la mise à jour a été classée. |

#### <a name="product-and-service-performance-data-events"></a>Evénements des données de performance de produit et service

**Statistiques d’extension du noyau**

Les champs suivants sont affichés :

| Champ            | Description |
| ---------------- | ----------- |
| version          | Version de Microsoft Defender pour Point de terminaison pour Mac. |
| instance_id      | Identificateur unique généré au démarrage de l’extension du noyau. |
| trace_level      | Niveau de suivi de l’extension du noyau. |
| sous-système        | Sous-système sous-jacent utilisé pour la protection en temps réel. |
| ipc.connects     | Nombre de demandes de connexion reçues par l’extension du noyau. |
| ipc.rejects      | Nombre de demandes de connexion rejetées par l’extension du noyau. |
| ipc.connected    | S’il existe une connexion active à l’extension du noyau. |

#### <a name="support-data"></a>Données de prise en charge

**Journaux de diagnostic**

Les journaux de diagnostic sont collectés uniquement avec le consentement de l’utilisateur dans le cadre de la fonctionnalité de soumission de commentaires. Les fichiers suivants sont collectés dans le cadre des journaux de support :

- Tous les fichiers *sous /Library/Logs/Microsoft/mdatp/*
- Sous-ensemble de fichiers sous */Library/Application Support/Microsoft/Defender/* créés et utilisés par Microsoft Defender pour Endpoint pour Mac
- Sous-ensemble de fichiers sous */Library/Managed Preferences* utilisées par Microsoft Defender pour Endpoint pour Mac
- /Library/Logs/Microsoft/autoupdate.log
- $HOME/Library/Preferences/com.microsoft.autoupdate2.plist

### <a name="optional-diagnostic-data"></a>Données de diagnostic facultatives

**Les données de diagnostic facultatives** sont des données supplémentaires qui aident Microsoft à améliorer les produits et fournissent des informations améliorées pour vous aider à détecter, diagnostiquer et résoudre les problèmes.

Si vous choisissez d’envoyer des données de diagnostic facultatives, les données de diagnostic requises sont également incluses.

Les données de diagnostic facultatives collectées par Microsoft sur la configuration du produit (par exemple, le nombre d’exclusions définies sur l’appareil) et les performances du produit (mesures agrégées sur les performances des composants du produit) sont des exemples de données de diagnostic facultatives.

#### <a name="software-setup-and-inventory-data-events"></a>Événements de données liés à l’inventaire et à la configuration des logiciels

**Configuration de Microsoft Defender pour point de terminaison**

Les champs suivants sont affichés :

| Champ                                              | Description |
| -------------------------------------------------- | ----------- |
| connection_retry_timeout                           | Délai d’délai de nouvelle tentative de connexion lors de la communication avec le cloud. |
| file_hash_cache_maximum                            | Taille du cache du produit. |
| crash_upload_daily_limit                           | Limite des journaux d’incident téléchargés quotidiennement. |
| antivirus_engine.exclusions[].is_directory         | Si l’exclusion de l’analyse est un répertoire ou non. |
| antivirus_engine.exclusions[].path                 | Chemin d’accès exclu de l’analyse. |
| antivirus_engine.exclusions[].extension            | Extension exclue de l’analyse. |
| antivirus_engine.exclusions[].name                 | Nom du fichier exclu de l’analyse. |
| antivirus_engine.scan_cache_maximum                | Taille du cache du produit. |
| antivirus_engine.maximum_scan_threads              | Nombre maximal de threads utilisés pour l’analyse. |
| antivirus_engine.threat_restoration_exclusion_time | Délai d’délai avant qu’un fichier restauré à partir de la quarantaine puisse à nouveau être détecté. |
| filesystem_scanner.full_scan_directory             | Répertoire d’analyse complet. |
| filesystem_scanner.quick_scan_directories          | Liste des répertoires utilisés dans l’analyse rapide. |
| edr.latency_mode                                   | Mode latence utilisé par le composant de détection et de réponse. |
| edr.proxy_address                                  | Adresse proxy utilisée par le composant de détection et de réponse. |

**Configuration de la mise à jour automatique Microsoft**

Les champs suivants sont affichés :

| Champ                       | Description |
| --------------------------- | ----------- |
| how_to_check                | Détermine la façon dont les mises à jour des produits sont vérifiées (par exemple, automatiques ou manuelles). |
| channel_name                | Canal de mise à jour associé à l’appareil. |
| manifest_server             | Serveur utilisé pour télécharger les mises à jour. |
| update_cache                | Emplacement du cache utilisé pour stocker les mises à jour. |

### <a name="product-and-service-usage"></a>Utilisation des produits et services

#### <a name="diagnostic-log-upload-started-report"></a>Rapport de chargement démarré du journal de diagnostic

Les champs suivants sont affichés :

| Champ            | Description |
| ---------------- | ----------- |
| sha256           | Identificateur SHA256 du journal de support. |
| size             | Taille du journal de prise en charge. |
| original_path    | Chemin d’accès au journal de support (toujours sous */Library/Application Support/Microsoft/Defender/wdavdiag/*). |
| format           | Format du journal de prise en charge. |

#### <a name="diagnostic-log-upload-completed-report"></a>Rapport de chargement terminé du journal de diagnostic

Les champs suivants sont affichés :

| Champ            | Description |
| ---------------- | ----------- |
| request_id       | ID de corrélation pour la demande de chargement du journal de support. |
| sha256           | Identificateur SHA256 du journal de support. |
| blob_sas_uri     | URI utilisé par l’application pour télécharger le journal de support. |

#### <a name="product-and-service-performance-data-events"></a>Evénements des données de performance de produit et service

**Sortie inopinée de l’application (blocage)**

Sorties inattendues de l’application et état de celle-ci lorsque cela se produit.

**Statistiques d’extension du noyau**

Les champs suivants sont affichés :

| Champ                          | Description |
| ------------------------------ | ----------- |
| pkt_ack_timeout                | Les propriétés suivantes sont des valeurs numériques agrégées, représentant le nombre d’événements qui se sont produit depuis le démarrage de l’extension du noyau. |
| pkt_ack_conn_timeout             | |
| ipc.ack_pkts                     | |
| ipc.nack_pkts                    | |
| ipc.send.ack_no_conn             | |
| ipc.send.nack_no_conn            | |
| ipc.send.ack_no_qsq              | |
| ipc.send.nack_no_qsq             | |
| ipc.ack.no_space                 | |
| ipc.ack.timeout                  | |
| ipc.ack.ackd_fast                | |
| ipc.ack.ackd                     | |
| ipc.recv.bad_pkt_len             | |
| ipc.recv.bad_reply_len           | |
| ipc.recv.no_waiter               | |
| ipc.recv.copy_failed             | |
| ipc.kauth.vnode.mask             | |
| ipc.kauth.vnode.read             | |
| ipc.kauth.vnode.write            | |
| ipc.kauth.vnode.exec             | |
| ipc.kauth.vnode.del              | |
| ipc.kauth.vnode.read_attr        | |
| ipc.kauth.vnode.write_attr       | |
| ipc.kauth.vnode.read_ex_attr     | |
| ipc.kauth.vnode.write_ex_attr    | |
| ipc.kauth.vnode.read_sec         | |
| ipc.kauth.vnode.write_sec        | |
| ipc.kauth.vnode.take_own         | |
| ipc.kauth.vnode.link             | |
| ipc.kauth.vnode.create           | |
| ipc.kauth.vnode.move             | |
| ipc.kauth.vnode.mount            | |
| ipc.kauth.vnode.denied           | |
| ipc.kauth.vnode.ackd_before_deadline | |
| ipc.kauth.vnode.missed_deadline  | |
| ipc.kauth.file_op.mask           | |
| ipc.kauth_file_op.open           | |
| ipc.kauth.file_op.close          | |
| ipc.kauth.file_op.close_modified | |
| ipc.kauth.file_op.move           | |
| ipc.kauth.file_op.link           | |
| ipc.kauth.file_op.exec           | |
| ipc.kauth.file_op.remove         | |
| ipc.kauth.file_op.unmount        | |
| ipc.kauth.file_op.fork           | |
| ipc.kauth.file_op.create         | |

## <a name="resources"></a>Ressources

- [Confidentialité chez Microsoft](https://privacy.microsoft.com/)
