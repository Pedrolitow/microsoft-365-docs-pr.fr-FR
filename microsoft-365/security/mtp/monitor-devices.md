---
title: Rapports d'& de surveillance des appareils - Centre de sécurité
description: Décrit comment sécuriser, mettre à jour et repérer les menaces potentielles dans votre organisation
keywords: sécurité, programmes malveillants, Microsoft 365, M365, centre de sécurité, surveiller, signaler, appareils
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: ellevin
author: levinec
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
search.appverid: met150
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: b9580f904f9cc5043fa3e825007339ce66daaa72
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49930497"
---
# <a name="device-monitoring-and-reporting-in-the-microsoft-365-security-center"></a>Surveillance des appareils et rapports dans le Centre de sécurité Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


Maintenez vos appareils sécurisés, à jour et repérer les menaces potentielles dans le Centre de sécurité Microsoft 365.

## <a name="view-device-alerts"></a>Afficher les alertes de périphérique

Recevez des alertes à jour concernant l’activité de violation et d’autres menaces sur vos appareils à partir de Microsoft Defender for Endpoint (disponible avec une licence E5). Le Centre de sécurité Microsoft 365 surveille efficacement ces alertes à un niveau élevé à l’aide de votre flux de travail préféré.

### <a name="monitor-high-impact-alerts"></a>Surveiller les alertes à fort impact

Chaque alerte Microsoft Defender pour point de terminaison a une gravité correspondante (élevée, moyenne, faible ou informationnelle). Il indique l’impact potentiel sur votre réseau s’il est laissé sans surveillance.  

Utilisez la carte **de gravité des** alertes d’appareil pour vous concentrer spécifiquement sur les alertes plus graves et qui peuvent nécessiter une réponse immédiate. À partir de cette carte, vous pouvez afficher plus d’informations sur le portail centre de sécurité Microsoft Defender.

![Carte de gravité des alertes d’appareil](../../media/device-alerts-severity.png)

### <a name="understand-sources-of-alerts"></a>Comprendre les sources d’alertes

Microsoft Defender pour le point de terminaison exploite les données d’un large éventail de capteurs de sécurité et de sources d’intelligence pour générer des alertes. Par exemple, il peut utiliser les informations de détection de l’Antivirus Microsoft Defender et des logiciels anti-programme malveillant tiers. Il peut également utiliser votre propre intelligence contre les menaces personnalisée fournie par le biais de l’API de service web.

La carte **sources de détection des alertes** d’appareil affiche la distribution des alertes par source. Suivre l’activité liée à certaines sources, en particulier vos sources personnalisées. Vous pouvez également utiliser la carte pour vous concentrer sur les alertes provenant de capteurs qui ne sont pas configurés pour bloquer automatiquement les activités ou composants malveillants.

![Carte sources de détection des alertes d’appareil](../../media/device-alert-detection-sources.png)

À partir de cette carte, vous pouvez afficher plus d’informations sur le portail centre de sécurité Microsoft Defender.

### <a name="understand-the-types-of-threats-that-trigger-alerts"></a>Comprendre les types de menaces qui déclenchent des alertes

Microsoft Defender pour le point de terminaison trie chaque alerte dans une catégorie représentant une étape particulière de la chaîne d’attaque ou du type de composant de menace. Par exemple, une activité de menace détectée peut être classée comme « mouvement latéral » pour indiquer qu’il y a eu une tentative d’atteindre d’autres appareils sur le réseau. L’activité s’est probablement produite après que les attaquants ont pris une première place. Lorsqu’il est détecté, un composant de menace peut être considéré à grande étendue comme programme malveillant ou spécifiquement comme un type de menace spécifique. Les détails incluent les ransomware, le vol d’informations d’identification ou d’autres types de logiciels malveillants ou indésirables.

La **carte catégories de menaces d’appareil** affiche la distribution des alertes dans ces catégories. Utilisez ces informations pour identifier l’activité des menaces, telles que les tentatives de vol d’informations d’identification, qui ont généralement un impact plus élevé que les tentatives d’ingénierie sociale. Vous pouvez également surveiller les menaces potentiellement destructrices telles que les ransomware.

![Carte catégories de menaces d’appareil](../../media/device-threat-categories.png)

### <a name="monitor-active-alerts"></a>Surveiller les alertes actives

La **carte d’état d’alerte** d’appareil indique le nombre d’alertes qui n’ont pas été résolues et qui peuvent nécessiter une attention particulière. À partir de cette carte, vous pouvez afficher plus d’informations sur le portail centre de sécurité Microsoft Defender.

![Carte d’état d’alerte d’appareil](../../media/device-alert-status.png)

### <a name="monitor-classification-of-resolved-alerts"></a>Surveiller la classification des alertes résolues

Lors de la résolution d’une alerte Microsoft Defender pour point de terminaison, votre personnel de sécurité peut spécifier si une alerte a été vérifiée comme :

* Une alerte réelle qui identifie l’activité de violation réelle ou les composants de menace
* Une fausse alerte qui a détecté de manière incorrecte l’activité normale

La **carte de classification des alertes** d’appareil indique si vos alertes résolues ont été classées en tant qu’alertes vraies ou fausses. À partir de cette carte, vous pouvez afficher plus d’informations sur le portail centre de sécurité Microsoft Defender.

Remarque : dans certains cas, les informations de classification ne sont pas disponibles pour certaines alertes.

![Carte de classification des alertes d’appareil](../../media/device-alert-classification.png)

### <a name="monitor-determination-of-resolved-alerts"></a>Surveiller la détermination des alertes résolues

En plus de classer si une alerte est vraie ou false lors de la résolution, votre personnel de sécurité peut fournir une détermination. Une détermination indique le type d’activité normale ou malveillante qui a été trouvé lors de la validation de l’alerte.

La **carte de détermination de l’alerte** d’appareil indique la détermination fournie pour chaque alerte.

* **APT**: menace persistante avancée, indiquant que l’activité détectée ou le composant de menace fait partie d’une violation sophistiquée conçue pour prendre pied dans le réseau concerné  
* **Programmes malveillants**: fichier ou code malveillant
* **Personnel de sécurité :** activité normale effectuée par le personnel de sécurité
* **Test de sécurité**: activité ou composants conçus pour simuler des menaces réelles et qui doivent déclencher des capteurs de sécurité et générer des alertes
* **Logiciels indésirables**: applications et autres logiciels qui ne sont pas considérés comme malveillants, mais qui ne respectent pas la politique ou les normes d’utilisation acceptables
* **Autres**: toute autre détermination qui ne relève pas des types fournis

À partir de cette carte, vous pouvez afficher plus d’informations dans le Centre de sécurité Microsoft Defender.

![Carte de détermination des alertes d’appareil](../../media/device-alert-determination.png)

### <a name="understand-which-devices-are-at-risk"></a>Comprendre les appareils à risque

**La protection des** appareils indique le niveau de risque pour les appareils. Le niveau de risque est basé sur des facteurs tels que le type et la gravité des alertes sur l’appareil.

![Carte de protection de l’appareil](../../media/device-protection.png)

## <a name="monitor-and-report-status-of-intune-managed-devices"></a>Surveiller et signaler l’état des appareils gérés par Intune

Les rapports suivants contiennent des données provenant d’appareils inscrits dans Intune. Les données provenant d’appareils non inscrits ne sont pas incluses. Seuls les administrateurs globaux peuvent afficher ces cartes.

Les données d’appareil inscrites dans Intune incluent :

* Conformité des appareils
* Appareils avec programmes malveillants actifs
* Types de programmes malveillants sur les appareils
* Programmes malveillants sur les appareils
* Appareils avec détection de programmes malveillants
* Utilisateurs avec détection de programmes malveillants

### <a name="monitor-device-compliance"></a>Surveiller la conformité des appareils

**La conformité des** appareils indique le nombre d’appareils inscrits dans Intune conformes aux stratégies de configuration.

![Carte de conformité de l’appareil](../../media/device-compliance.png)

### <a name="discover-devices-with-malware-detections"></a>Détecter les appareils avec détection de programmes malveillants

**Les détections de programmes malveillants** de périphérique fournissent le nombre d’appareils inscrits à Intune avec des programmes malveillants qui n’ont pas été entièrement résolus. Un manque de résolution peut être dû à des actions en attente, un redémarrage, une analyse complète, des actions manuelles de l’utilisateur ou si l’action de correction n’a pas été correctement effectuée.

![Carte de détection des programmes malveillants d’appareil](../../media/device-malware-detections.png)

### <a name="understand-the-types-of-malware-detected"></a>Comprendre les types de programmes malveillants détectés

**Les types de programmes malveillants sur les appareils** indiquent différents types de programmes malveillants détectés sur les appareils inscrits dans Intune. Vous pouvez examiner chaque type dans le Centre de sécurité Microsoft 365.

![Types de programmes malveillants sur la carte d’appareil](../../media/types-of-malware-on-devices.png)

### <a name="understand-the-specific-malware-detected-on-your-devices"></a>Comprendre les programmes malveillants spécifiques détectés sur vos appareils

**Les programmes malveillants sur les** appareils fournissent une liste des programmes malveillants spécifiques détectés sur vos appareils.

![Carte programmes malveillants sur les appareils](../../media/malware-on-devices.png)

### <a name="understand-which-devices-have-the-most-malware"></a>Comprendre les appareils qui ont le plus de programmes malveillants

**Les appareils avec détection de programmes malveillants** indiquent les appareils qui ont le plus de détections de programmes malveillants. dans le Centre de sécurité Microsoft 365, vous pouvez déterminer si un programme malveillant est actif, qui utilise l’appareil et son état de gestion dans Intune.

![Appareils avec carte de détection de programmes malveillants](../../media/devices-with-malware-detections.png)

### <a name="understand-which-users-have-devices-with-the-most-malware"></a>Comprendre quels utilisateurs ont des appareils avec le plus de programmes malveillants

**Les utilisateurs qui ont détecté des programmes malveillants** montrent les utilisateurs ayant le plus de détections de programmes malveillants sur des appareils. Dans le Centre de sécurité Microsoft 365, vous pouvez voir le nombre d’appareils affectés à chaque utilisateur et plus d’informations sur chaque appareil et le type de programmes malveillants.

![Utilisateurs avec carte de détection de programmes malveillants](../../media/users-with-malware-detections.png)

## <a name="monitor-and-manage-attack-surface-reduction-rule-deployment-and-detections"></a>Surveiller et gérer le déploiement et les détections des règles de réduction de la surface d’attaque

Les règles de réduction de la surface d’attaque [(ASR)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction) permettent d’empêcher les actions et les applications généralement utilisées par des programmes malveillants malveillants pour infecter des appareils. Ces règles contrôlent quand et comment les fichiers exécutables peuvent être exécutés. Par exemple, vous pouvez empêcher JavaScript ou VBScript de lancer un exécutable téléchargé, bloquer des appels API Win32 à partir de macros Office, ou bloquer les processus exécutés à partir de lecteurs USB.

![Carte réduction de la surface d’attaque](../../media/attack-surface-reduction-rules.png)

La carte **Règles de réduction de la surface d’attaque** offre une vue d’ensemble du déploiement des règles sur vos appareils.

La barre supérieure de la carte affiche le nombre total d’appareils figurant dans les modes de déploiement suivants :

* **Mode blocage :** appareils avec au moins une règle configurée pour bloquer l’activité détectée
* **Mode audit :** appareils sans règles définies pour bloquer l’activité détectée, mais avec au moins une règle définie pour auditer l’activité détectée  
* **Désactivé :** appareils avec toutes les règles de la asr. désactivées

La partie inférieure de cette carte présente les paramètres par règle sur tous vos appareils. Chaque barre indique le nombre d’appareils qui sont définies pour bloquer, auditer la détection ou dont la règle est complètement désactivée.

### <a name="view-asr-detections"></a>Afficher les détections de la asr.

Pour afficher des informations détaillées sur les détections de règles de réduction de la surface d’attaque dans votre réseau, sélectionnez Afficher les **détections** sur la carte des règles de réduction de la **surface d’attaque.** **L’onglet Détections** de la page de rapport détaillé s’ouvre.

![Onglet Détections](../../media/detections-tab.png)

Le graphique en haut de la page présente les détections au fil du temps de détections d’empilement qui ont été bloquées ou auditées. Le tableau en bas répertorie les détections les plus récentes. Utilisez les informations suivantes sur le tableau pour comprendre la nature des détections :

* **Fichier détecté :** le fichier, généralement un script ou un document, dont le contenu a déclenché l’activité d’attaque suspecte
* **Règle**: nom décrivant les activités d’attaque que la règle est conçue pour capturer. En savoir plus sur les règles de asr existantes
* **Application source**: application qui a chargé ou exécuté du contenu déclenchant l’activité d’attaque suspecte. Il peut s’agit d’une application légitime, telle qu’un navigateur web, une application Office ou un outil système tel que PowerShell.
* **Publisher**: le fournisseur qui a publié l’application source

### <a name="review-device-asr-rule-settings"></a>Passer en revue les paramètres de règle asr de l’appareil

Dans la page Du rapport **règles de réduction** de la surface d’attaque, allez dans l’onglet **Configuration** pour passer en revue les paramètres de règle pour les appareils individuels. Sélectionnez un appareil pour obtenir des informations détaillées sur le fait que chaque règle soit en mode blocage, en mode audit ou complètement désactivée.

![Onglet Configuration](../../media/configuration-tab.png)

Microsoft Intune fournit des fonctionnalités de gestion pour vos règles de astér. Si vous souhaitez mettre à  jour  vos paramètres, sélectionnez Prise en charge sous Configurer les appareils dans l’onglet pour ouvrir la gestion des appareils sur Intune.

### <a name="exclude-files-from-asr-rules"></a>Exclure des fichiers des règles de la asr.

Le Centre de sécurité Microsoft 365 collecte les noms des fichiers que vous souhaitez exclure des détections par les règles de réduction de la surface d’attaque. [](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/enable-attack-surface-reduction#exclude-files-and-folders-from-asr-rules) En excluant des fichiers, vous pouvez réduire les détections de faux positifs et déployer en toute confiance les règles de réduction de la surface d’attaque en mode blocage.

Les exclusions sont gérées sur Microsoft Intune, mais le Centre de sécurité Microsoft 365 fournit un outil d’analyse pour vous aider à comprendre les fichiers. Pour commencer à collecter des fichiers pour l’exclusion, reportez-vous à l’onglet Ajouter des **exclusions** dans la page du rapport règles de réduction de la **surface d’attaque.**

>[!NOTE]  
>L’outil analyse les détections par toutes les règles de réduction de la surface d’attaque, mais seules certaines règles peuvent prendre en charge [les exclusions.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-asr)

![Onglet Ajouter des exclusions](../../media/add-exclusions-tab.png)

Le tableau répertorie tous les noms de fichiers détectés par vos règles de réduction de la surface d’attaque. Vous pouvez sélectionner des fichiers pour examiner l’impact de leur exclusion :

* Nombre de détections moins nombreuses
* Nombre d’appareils moins signalant les détections

Pour obtenir une liste des fichiers sélectionnés avec leurs chemins d’accès complets pour l’exclusion, **sélectionnez Obtenir les chemins d’accès d’exclusion.**

Les journaux de la règle ASR bloquent le vol d’informations d’identification à partir du sous-système de l’autorité de sécurité locale **Windows (lsass.exe)** capturent l’application source **lsass.exe**. Il s’agit d’un fichier système normal, mais capturé en tant que fichier détecté. Par conséquent, la liste des chemins d’exclusion générés inclut ce fichier. Pour exclure le fichier qui a déclenché cette règle au lieu de **lsass.exe,** utilisez le chemin d’accès à l’application source au lieu du fichier détecté.

Pour localiser l’application source, exécutez la requête de recherche avancée suivante pour cette règle spécifique (identifiée par l’ID de règle 9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2) : [](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting)

```kusto
DeviceEvents
| where Timestamp > ago(7d)
| where ActionType startswith "Asr"
| where AdditionalFields contains "9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2"
| project InitiatingProcessFolderPath, InitiatingProcessFileName
```

#### <a name="check-files-for-exclusion"></a>Vérifier les fichiers pour l’exclusion

Avant d’exclure un fichier de la RSA, nous vous recommandons d’inspecter le fichier pour déterminer s’il n’est pas malveillant.

Pour consulter un fichier, utilisez la [page d’informations](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/investigate-files) sur le fichier dans le Centre de sécurité Microsoft Defender. La page fournit des informations sur la prévalence et le taux de détection antivirus VirusTotal. Vous pouvez également utiliser la page pour envoyer le fichier pour analyse approfondie.

Pour localiser un fichier détecté dans le Centre de sécurité Microsoft Defender, recherchez toutes les détections de la asr à l’aide de la requête de repérage avancé suivante :

```kusto
MiscEvents
| where EventTime > ago(7d)
| where ActionType startswith "Asr"
| project FolderPath, FileName, SHA1, InitiatingProcessFolderPath, InitiatingProcessFileName, InitiatingProcessSHA1
```

Utilisez **sha1 ou** **InitiatingProcessSHA1** dans les résultats pour rechercher le fichier à l’aide de la barre de recherche universelle dans le Centre de sécurité Microsoft Defender.
