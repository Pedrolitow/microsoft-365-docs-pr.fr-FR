---
title: Découvrez comment atténuer la vulnérabilité Log4Shell dans Microsoft Defender pour point de terminaison - Gestion des menaces et des vulnérabilités
description: Découvrez comment atténuer la vulnérabilité Log4Shell dans Microsoft Defender pour point de terminaison
keywords: tvm, lo4j
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365-initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6e265490eb5afee275debcdd1eb073f11bb845e3
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416489"
---
# <a name="learn-how-to-manage-the-log4shell-vulnerability-in-microsoft-defender-for-endpoint"></a>Découvrez comment gérer la vulnérabilité Log4Shell dans Microsoft Defender pour point de terminaison

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [La gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

La vulnérabilité Log4Shell est une vulnérabilité d’exécution de code à distance (RCE) trouvée dans la bibliothèque de journalisation Apache Log4j 2. Étant donné qu’Apache Log4j 2 est couramment utilisé par de nombreuses applications logicielles et services en ligne, il représente une situation complexe et à haut risque pour les entreprises à travers le monde. Appelé « Log4Shell » ([CVE-2021-44228](https://cve.mitre.org/cgi-bin/cvename.cgi?name=2021-44228), [CVE-2021-45046](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-45046) ), il introduit un nouveau vecteur d’attaque que les attaquants peuvent exploiter pour extraire des données et déployer des ransomware dans une organisation.

> [!NOTE]
> Reportez-vous aux blogs [Conseils pour la prévention, la détection et la chasse à l’exploitation de la vulnérabilité Log4j 2 et](https://www.microsoft.com/security/blog/2021/12/11/guidance-for-preventing-detecting-and-hunting-for-cve-2021-44228-log4j-2-exploitation/) [au Centre de réponse à la sécurité Microsoft](https://msrc-blog.microsoft.com/2021/12/11/microsofts-response-to-cve-2021-44228-apache-log4j2/) pour obtenir des conseils et des informations techniques sur la vulnérabilité et les recommandations d’atténuation spécifiques aux produits pour protéger votre organisation.

## <a name="overview-of-discovery-monitoring-and-mitigation-capabilities"></a>Vue d’ensemble des fonctionnalités de découverte, de surveillance et d’atténuation

Menaces et gestion des vulnérabilités vous offrent les fonctionnalités suivantes pour vous aider à identifier, surveiller et atténuer l’exposition de votre organisation à la vulnérabilité Log4Shell :

- **Découverte** : la détection des appareils exposés, à la fois Microsoft Defender pour point de terminaison les appareils intégrés et les appareils qui ont été découverts mais qui ne sont pas encore intégrés, est basée sur des logiciels vulnérables et des fichiers vulnérables détectés sur le disque.
- **Sensibilisation aux menaces :** Vue consolidée pour évaluer l’exposition de votre organisation. Cette vue montre votre exposition au niveau de l’appareil et du logiciel, et donne accès à des détails sur des fichiers vulnérables tels que la dernière fois qu’il a été vu, la dernière fois qu’il a été exécuté et la dernière fois qu’il a été exécuté avec des ports ouverts. Vous pouvez utiliser ces informations pour hiérarchiser vos actions de correction. L’affichage des données relatives aux appareils exposés sur le tableau de bord peut prendre jusqu’à 24 heures.
- **Options d’atténuation :** Appliquez des options d’atténuation pour réduire votre risque d’exposition.
- **Repérage avancé :** Utilisez la chasse avancée pour retourner les détails des fichiers log4j vulnérables identifiés sur le disque.

> [!NOTE]
> Ces fonctionnalités sont prises en charge sur Windows 10 & Windows 11, Windows Server, Linux et macOS.
>
> La prise en charge sur Linux nécessite Microsoft Defender pour point de terminaison client Linux version 101.52.57 (30.121092.15257.0) ou version ultérieure.
>
> La prise en charge sur macOS nécessite Microsoft Defender pour point de terminaison macOS version client 20.121111.15416.0 ou ultérieure.
>
>Pour plus d’informations sur les versions prises en charge, consultez [Plateformes et fonctionnalités des systèmes d’exploitation pris en charge](tvm-supported-os.md).

## <a name="exposed-devices-discovery"></a>Découverte d’appareils exposés

Les fonctionnalités de Gestion des menaces et des vulnérabilités incorporées, ainsi que l’activation de la détection Log4j, dans le portail Microsoft 365 Defender, vous aideront à découvrir les appareils exposés à la vulnérabilité Log4Shell.

Les appareils intégrés sont évalués à l’aide de fonctionnalités de Gestion des menaces et des vulnérabilités incorporées existantes qui peuvent détecter des logiciels et des fichiers vulnérables.

Pour la détection sur les appareils découverts mais pas encore intégrés, la détection Log4j doit être activée. Cela lance les sondes de la même façon que la découverte d’appareils sonde activement votre réseau. Cela inclut la détection à partir de plusieurs points de terminaison intégrés (appareils Windows 10+ et Windows Server 2019+) et la détection uniquement au sein de sous-réseaux pour détecter les appareils vulnérables et exposés à distance à CVE-2021-44228.

Pour activer la détection Log4 :

1. Accédez à **Paramètres** >  **Device** **discoveryDiscovery** >  setup
2. Sélectionnez **Activer la détection Log4j2 (CVE-2021-44228)**
3. Sélectionnez **Enregistrer**.

:::image type="content" source="images/enable_log4j.png" alt-text="Paramètre permettant d’activer la détection log4j2" lightbox="images/enable_log4j.png":::

L’exécution de ces sondes déclenche le flux Log4j standard sans provoquer d’impact nocif sur l’appareil en cours de sonde ou sur l’appareil de détection. La détection elle-même est effectuée en envoyant plusieurs requêtes HTTP aux appareils découverts, en ciblant les ports d’application web courants (par exemple, 80 8000 8080 443 8443) et les URL. La requête contient des en-têtes HTTP avec une charge utile JNDI qui déclenche une requête DNS à partir de la machine sondée.

Par exemple, User-Agent : ${jndi:dns://192.168.1.3:5353/MDEDiscoveryUser-Agent} où 192.168.1.3 est l’adresse IP de la machine de détection.

> [!NOTE]
> L’activation de la détection Log4j2 signifie également que les appareils intégrés utilisent la détection automatique pour détecter les vulnérabilités locales.

## <a name="vulnerable-software-and-files-detection"></a>Détection de logiciels et de fichiers vulnérables

Menaces et gestion des vulnérabilités fournit des couches de détection pour vous aider à découvrir :

- **Logiciels vulnérables** : la découverte est basée sur des énumérations de plateforme commune (CPE) d’application installées qui sont connues pour être vulnérables à l’exécution du code distant Log4j.
- **Fichiers vulnérables :** Les fichiers en mémoire et les fichiers du système de fichiers sont évalués. Ces fichiers peuvent être des fichiers jar Log4j-core avec la version vulnérable connue ou un fichier Uber-JAR qui contient une classe de recherche jndi vulnérable ou un fichier log4j-core vulnérable. Plus précisément, il :

  - détermine si un fichier JAR contient un fichier Log4j vulnérable en examinant les fichiers JAR et en recherchant le fichier suivant : \\META-INFmavenorg.apache.logging.log4jlog4j-corepom.properties\\\\\\\\ . Si ce fichier existe, la version de Log4j est lue et extraite.
  - recherche le fichier JndiLookup.class à l’intérieur du fichier JAR en recherchant les chemins qui contiennent la chaîne « /log4j/core/lookup/JndiLookup.class » : si le fichier JndiLookup.class existe, Gestion des menaces et des vulnérabilités détermine si ce fichier JAR contient un fichier Log4j avec la version définie dans pom.properties.
  - recherche les fichiers JAR Log4j-core vulnérables incorporés dans un fichier JAR imbriqué en recherchant les chemins qui contiennent l’une de ces chaînes :
    - lib/log4j-core-
    - WEB-INF/lib/log4j-core-
    - App-INF/lib/log4j-core-

Ce tableau décrit les fonctionnalités de recherche prises en charge par les plateformes et les versions :

|Fonctionnalité|Type de fichier|Windows10+,<br>server2019+|Server 2012R2,<br>server2016|Server 2008R2|Linux + macOS|
|:---|:---|:---|:---|:---|:---|
|Rechercher en mémoire  | Log4j-core | Oui |Oui<sup>[1]| - | Oui |
| |Uber-JARs | Oui |Oui<sup>[1]| - | Oui |
| Rechercher tous les fichiers sur le disque  |Log4j-core | Oui |Oui<sup>[1]| Oui | - |
| | Uber-JARs|Oui |Oui<sup>[1]| - | -|

(1) Les fonctionnalités sont disponibles lorsque [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) est installé sur Windows Server 2012 R2 et 2016.

## <a name="learn-about-your-log4shell-exposure-and-mitigation-options"></a>En savoir plus sur vos options d’exposition et d’atténuation Log4Shell

### <a name="threat-and-vulnerability-management-dashboard"></a>Tableau de bord menaces et gestion des vulnérabilités

Utilisez le tableau de bord Gestion des menaces et des vulnérabilités pour voir votre exposition actuelle.

1. Dans le portail Microsoft 365 Defender, accédez à **Vulnerability** **managementDashboardThreat** >  >  **awareness:**
:::image type="content" source="images/awareness_dashboard.png" alt-text="The threat awareness widget on the gestion des vulnérabilités dashboard" lightbox="images/awareness_dashboard.png":::
2. Sélectionnez **Afficher les détails des vulnérabilités** pour afficher la vue consolidée de l’exposition de votre organisation.
:::image type="content" source="images/view_vulnerability_details.png" alt-text="Page détails de la vulnérabilité pour CVE-2021-44228 (Log4j)" lightbox="images/view_vulnerability_details.png":::
3. Choisissez l’onglet approprié pour voir votre exposition décomposée par :
    - Appareils exposés – intégration
    - Appareils exposés – non intégrés
    - Fichiers vulnérables
    - Logiciels vulnérables

### <a name="log4shell-vulnerability-mitigation"></a>Atténuation des vulnérabilités Log4Shell

La vulnérabilité log4Shell peut être atténuée en empêchant les recherches JNDI sur les versions 2.10 - 2.14.1 de Log4j avec les configurations par défaut. Pour créer cette action d’atténuation, à partir du **tableau de bord de sensibilisation aux menaces** :

1. Sélectionner **Afficher les détails des vulnérabilités**
2. Sélectionner **les options d’atténuation**

Vous pouvez choisir d’appliquer l’atténuation à tous les appareils exposés ou de sélectionner des appareils intégrés spécifiques. Pour terminer le processus et appliquer l’atténuation sur les appareils, sélectionnez **Créer une action d’atténuation**.

:::image type="content" source="images/mitigation_options.png" alt-text="Options d’atténuation pour CVE-2021-44228" lightbox="images/mitigation_options.png":::

### <a name="mitigation-status"></a>État d’atténuation

L’état d’atténuation indique si l’atténuation de la solution de contournement pour désactiver les recherches JDNI a été appliquée à l’appareil. Vous pouvez afficher l’état d’atténuation pour chaque appareil affecté dans les onglets Appareils exposés. Cela peut aider à hiérarchiser l’atténuation et/ou la mise à jour corrective des appareils en fonction de leur état d’atténuation.

:::image type="content" source="images/mitigation_status.png" alt-text="États d’atténuation possibles" lightbox="/mitigation_status.png":::

Le tableau ci-dessous répertorie les états d’atténuation potentiels :

| État d’atténuation | Description |
|:---|:---|
| Solution de contournement appliquée | _Windows_ : La variable d’environnement LOG4J_FORMAT_MSG_NO_LOOKUPS a été observée avant le dernier redémarrage de l’appareil. <br/><br/> _Linux + macOS_ : tous les processus en cours d’exécution ont LOG4J_FORMAT_MSG_NO_LOOKUPS=true dans ses variables d’environnement. |
| Solution de contournement en attente de redémarrage | La variable d’environnement LOG4J_FORMAT_MSG_NO_LOOKUPS est définie, mais aucun redémarrage suivant n’a été détecté. |
| Non appliqué | _Windows_ : La variable d’environnement LOG4J_FORMAT_MSG_NO_LOOKUPS n’a pas été observée. <br/><br/> _Linux + macOS_ : tous les processus en cours d’exécution n’ont pas LOG4J_FORMAT_MSG_NO_LOOKUPS=true dans ses variables d’environnement, et l’action d’atténuation n’a pas été appliquée sur l’appareil. |
| Partiellement atténué | _Linux + macOS_ : bien que l’action d’atténuation ait été appliquée sur l’appareil, tous les processus en cours d’exécution n’ont pas LOG4J_FORMAT_MSG_NO_LOOKUPS=true dans ses variables d’environnement. |
|Non applicable | Appareils qui ont des fichiers vulnérables qui ne figurent pas dans la plage de versions de l’atténuation. |
|Inconnu | L’état d’atténuation n’a pas pu être déterminé pour l’instant. |

> [!NOTE]
> La répercution de l’état d’atténuation mis à jour d’un appareil peut prendre quelques heures.

### <a name="revert-mitigations-applied-for-the-log4shell-vulnerability"></a>Rétablir les atténuations appliquées à la vulnérabilité Log4Shell

Dans les cas où l’atténuation doit être rétablie, procédez comme suit :

**_Pour Windows :_**

1. Ouvrir une fenêtre PowerShell avec élévation de privilèges
2. Exécutez la commande suivante :

 ```Powershell
   [Environment]::SetEnvironmentVariable("LOG4J\_FORMAT\_MSG\_NO\_LOOKUPS", $null,[EnvironmentVariableTarget]::Machine)
```

La modification prend effet après le redémarrage de l’appareil.

**_Pour Linux :_**

1. Ouvrez le fichier /etc/environment et supprimez la ligne LOG4JFORMATMSGNOLOOKUPS\_\_\_\_=true
2. Supprimer le fichier /etc/systemd/system.conf.d/log4jdisablejndilookups.conf\_\_\_
3. Supprimer le fichier /etc/systemd/user.conf.d/log4jdisablejndilookups.conf\_\_\_

La modification prend effet après le redémarrage de l’appareil.

**_Pour macOS :_**

Supprimez le setenv de fichier. LOG4JFORMATMSGNOLOOKUPS.plist\_\_\_\_ dans les dossiers suivants :

- */Library/LaunchDaemons/*
- */Library/LaunchAgents/*
- */Users/\[username\]/Library/LaunchAgents/ - pour tous les utilisateurs*

La modification prend effet après le redémarrage de l’appareil.

### <a name="apache-log4j-security-recommendations"></a>Recommandations en matière de sécurité Apache Log4j

Pour afficher les recommandations de sécurité actives liées à Apache log4j, sélectionnez l’onglet **Recommandations de sécurité** dans la page des détails des vulnérabilités. Dans cet exemple, si vous sélectionnez **Mettre à jour Apache Log4j** , vous verrez un autre menu volant contenant plus d’informations :

:::image type="content" source="images/update_apache_log4j.png" alt-text="Mettre à jour la recommandation de sécurité apache log4j" lightbox="images/update_apache_log4j.png":::

Sélectionnez **Demander la correction** pour créer une demande de correction.

## <a name="explore-the-vulnerability-in-the-microsoft-365-defender-portal"></a>Explorer la vulnérabilité dans le portail Microsoft 365 Defender

Une fois les appareils, fichiers et logiciels exposés trouvés, les informations pertinentes sont également transmises via les expériences suivantes dans le portail Microsoft 365 Defender :

### <a name="security-recommendations"></a>Recommandations en matière de sécurité

Recherchez **CVE-2021-44228** pour voir les recommandations de sécurité concernant la vulnérabilité Log4Shell :

:::image type="content" source="images/security_recommendations_log4j.png" alt-text="Vulnérabilité log4j sur la page recommandations de sécurité" lightbox="images/security_recommendations_log4j.png":::

### <a name="software-inventory"></a>Inventaire de logiciels

 Dans la page d’inventaire logiciel, recherchez **CVE-2021-44228** pour afficher des détails sur les installations et l’exposition des logiciels Log4j :

:::image type="content" source="images/software_inventory_log4j.png" alt-text="Vulnérabilité log4j sur la page d’inventaire logiciel" lightbox="images/software_inventory_log4j.png":::

### <a name="weaknesses"></a>Faiblesses

Dans la page Faiblesses, recherchez **CVE-2021-44228** pour afficher des informations sur la vulnérabilité Log4Shell :

:::image type="content" source="images/weaknesses_log4j.png" alt-text="Vulnérabilité log4j sur la page Faiblesses" lightbox="images/weaknesses_log4j.png":::

## <a name="use-advanced-hunting"></a>Utiliser la chasse avancée

Vous pouvez utiliser la requête de repérage avancée suivante pour identifier les vulnérabilités dans les logiciels installés sur les appareils :

 ```text
    DeviceTvmSoftwareVulnerabilities
    | where CveId in ("CVE-2021-44228", "CVE-2021-45046")
 ```

Vous pouvez utiliser la requête de repérage avancée suivante pour identifier les vulnérabilités dans les logiciels installés sur les appareils afin d’exposer les résultats au niveau du fichier à partir du disque :

 ```text
    DeviceTvmSoftwareEvidenceBeta
    | mv-expand DiskPaths
    | where DiskPaths contains "log4j"
    | project DeviceId, SoftwareName, SoftwareVendor, SoftwareVersion, DiskPaths
 ```

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble des menaces et des gestion des vulnérabilités](http://next-gen-threat-and-vuln-mgt.md)
- [Recommandations en matière de sécurité](tvm-security-recommendation.md)
