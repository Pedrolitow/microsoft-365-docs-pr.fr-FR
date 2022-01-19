---
title: Exporter les méthodes et propriétés d’évaluation par appareil
description: Fournit des informations sur les API qui tirent les données Gestion des menaces et des vulnérabilités données. Il existe différents appels d’API pour obtenir différents types de données. En règle générale, chaque appel d’API contient les données requises pour les appareils de votre organisation.
keywords: api, api, évaluation d’exportation, évaluation par appareil, évaluation par ordinateur, rapport d’évaluation des vulnérabilités, évaluation des vulnérabilités d’appareils, rapport de vulnérabilité d’appareil, évaluation de la configuration sécurisée, rapport de configuration sécurisée, évaluation des vulnérabilités logicielles, rapport de vulnérabilité logicielle, rapport de vulnérabilité par ordinateur,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: c10f454919afc725b37537aa354fed05b95cb571
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2022
ms.locfileid: "62074473"
---
# <a name="export-assessment-methods-and-properties-per-device"></a>Exporter les méthodes et propriétés d’évaluation par appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="api-description"></a>Description de l’API

Fournit des méthodes et des détails de propriété sur les API qui Gestion des menaces et des vulnérabilités données par appareil. Il existe différents appels d’API pour obtenir différents types de données. En règle générale, chaque appel d’API contient les données requises pour les appareils de votre organisation.

> [!NOTE]
> Sauf indication contraire, toutes les méthodes **** d’évaluation d’exportation répertoriées sont l’exportation complète et par appareil **_(également_** appelé **_par appareil)._**

Vous pouvez utiliser les API d’évaluation d’exportation pour récupérer (exporter) différents types d’informations :

- [1. Exporter l’évaluation des configurations sécurisées](#1-export-secure-configurations-assessment)
- [2. Exportation de l’évaluation de l’inventaire logiciel](#2-export-software-inventory-assessment)
- [3. Exportation de l’évaluation des vulnérabilités logicielles](#3-export-software-vulnerabilities-assessment)

Les API qui correspondent aux types d’informations d’exportation sont décrites dans les sections 1, 2 et 3.

Chaque méthode a des appels d’API différents pour obtenir différents types de données. Étant donné que la quantité de données peut être importante, il existe deux façons de les récupérer :

- **Réponse JSON**  L’API tire toutes les données de votre organisation en tant que réponses JSON. Cette méthode est la meilleure pour _les petites organisations avec moins de 100 Ko d’appareils._ La réponse est paginée, afin que vous pouvez utiliser le champ odata.nextLink de la réponse \@ pour récupérer les résultats suivants.

- **via des fichiers** Cette solution d’API permet d’tirer plus rapidement et de manière plus fiable des données plus volumineuses. Il est donc recommandé pour les grandes organisations, avec plus de 100 Ko d’appareils. Cette API tire toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir de stockage Azure. Cette API vous permet de télécharger toutes vos données à partir stockage Azure comme suit :
  - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.
  - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traiter les données comme vous le souhaitez.

Les données collectées à l’aide de «_réponse JSON_ ou _via_ des fichiers » sont la capture instantanée actuelle de l’état actuel. Il ne contient pas de données historiques. Pour collecter des données historiques, les clients doivent les enregistrer dans leurs propres stockages de données.

## <a name="1-export-secure-configurations-assessment"></a>1. Exporter l’évaluation des configurations sécurisées

Renvoie toutes les configurations et leur état, par appareil.

### <a name="11-methods"></a>1.1 Méthodes

Méthode|Type de données|Description
:---|:---|:---
Exporter l’évaluation de la configuration **sécurisée (réponse JSON)**|Sécurisation de la configuration par collection d’appareils. Voir : [1.2 Properties (réponse JSON)](#12-properties-json-response)|Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, ConfigurationId. L’API tire toutes les données de votre organisation en tant que réponses JSON. Cette méthode est la meilleure pour les petites organisations avec moins de 100 Ko d’appareils. La réponse est paginée, afin que vous pouvez utiliser le champ @odata.nextLink de la réponse pour récupérer les résultats suivants.
Exporter l’évaluation de la configuration **sécurisée (via des fichiers)**|Sécurisation de la configuration par collection d’appareils. Voir : [1.3 Properties (via files)](#13-properties-via-files)|Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, ConfigurationId. Cette solution d’API permet d’tirer plus rapidement et de manière plus fiable des données plus volumineuses. Il est donc recommandé pour les grandes organisations, avec plus de 100 Ko d’appareils. Cette API tire toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir de stockage Azure. Cette API vous permet de télécharger toutes vos données à partir stockage Azure comme suit : <ol><li>Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.</li><li>Téléchargez tous les fichiers à l’aide des URL de téléchargement et traiter les données comme vous le souhaitez.</li></ol>

### <a name="12-properties-json-response"></a>1.2 Propriétés (réponse JSON)

Propriété (ID)|Type de données|Description
:---|:---|:---
configurationCategory|Chaîne|Catégorie ou regroupement auquel appartient la configuration : application, système d’exploitation, réseau, comptes, contrôles de sécurité.
configurationId|Chaîne|Identificateur unique pour une configuration spécifique.
configurationImpact|Chaîne|Impact de la configuration sur le score de configuration global (1-10).
configurationName|Chaîne|Nom complet de la configuration.
configurationSubcategory|Chaîne|Sous-catégorie ou sous-groupement auquel appartient la configuration. Dans de nombreux cas, des fonctionnalités ou fonctionnalités spécifiques.
deviceId|String|Identificateur unique de l’appareil dans le service.
deviceName|String|Nom de domaine complet (FQDN) de l’appareil.
isApplicable|Bool|Indique si la configuration ou la stratégie est applicable.
isCompliant|Bool|Indique si la configuration ou la stratégie est correctement configurée.
isExpectedUserImpact|Bool|Indique si l’utilisateur est affecté si la configuration est appliquée.
osPlatform|Chaîne|Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Systèmes d’exploitation spécifiques avec des variantes au sein de la même famille, tels que Windows 10 et Windows 11. Pour plus d’informations, voir systèmes d’exploitation et plateformes pris en charge par TVM.
osVersion|String|Version spécifique du système d’exploitation en cours d’exécution sur l’appareil.
rbacGroupName|Chaîne|Groupe de contrôle d’accès basé sur un rôle (RBAC). Si l’appareil n’est affecté à aucun groupe RBAC, la valeur sera « Unassigned ». Si l’organisation ne contient aucun groupe RBAC, la valeur est « None ».
rbacGroupId|Chaîne|ID de groupe RBAC (Contrôle d’accès basé sur un rôle).
recommendationReference|Chaîne|Référence à l’ID de recommandation lié au logiciel.
timestamp|Chaîne|Dernière fois que la configuration a été vue sur l’appareil.

### <a name="13-properties-via-files"></a>1.3 Propriétés (via des fichiers)

Propriété (ID)|Type de données|Description
:---|:---|:---
Exporter des fichiers|chaîne de \[ tableau\]|Liste des URL de téléchargement pour les fichiers qui contiennent la capture instantanée actuelle de l’organisation.
GeneratedTime|Chaîne|Heure de la générer.

## <a name="2-export-software-inventory-assessment"></a>2. Exportation de l’évaluation de l’inventaire logiciel

Renvoie tous les logiciels installés et leurs détails sur chaque appareil.

### <a name="21-methods"></a>2.1 Méthodes

|Méthode|Type de données|Description|
|:---|:---|:---|
|Exporter l’évaluation de l’inventaire logiciel **(réponse JSON)**|Inventaire logiciel par collection d’appareils. Voir : [Propriétés 2.2 (réponse JSON)](#22-properties-json-response)|Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. L’API tire toutes les données de votre organisation en tant que réponses JSON. Cette méthode est la meilleure pour les petites organisations avec moins de 100 Ko d’appareils. La réponse est paginée, afin que vous pouvez utiliser le champ @odata.nextLink de la réponse pour récupérer les résultats suivants. |
| Exporter l’évaluation de l’inventaire **logiciel (via des fichiers)**|Inventaire logiciel par fichiers d’appareil. Voir : [2.3 Properties (via files)](#23-properties-via-files)|Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. Cette solution d’API permet d’tirer plus rapidement et de manière plus fiable des données plus volumineuses. Il est donc recommandé pour les grandes organisations, avec plus de 100 Ko d’appareils. Cette API tire toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir de stockage Azure. Cette API vous permet de télécharger des données à partir stockage Azure comme suit : <ol><li>Appeler l’API pour obtenir la liste des URL de téléchargement avec les données de votre organisation</li><li>Téléchargez les fichiers à l’aide des URL de téléchargement et traiter les données comme vous le souhaitez.</li></ol> |

### <a name="22-properties-json-response"></a>2.2 Propriétés (réponse JSON)

Propriété (ID)|Type de données|Description
:---|:---|:---
DeviceId|Chaîne|Identificateur unique de l’appareil dans le service.
DeviceName|Chaîne|Nom de domaine complet (FQDN) de l’appareil.
DiskPaths|Array[string]|Preuve disque que le produit est installé sur l’appareil.
EndOfSupportDate|Chaîne|Date à laquelle la prise en charge de ce logiciel a ou va se terminer.
EndOfSupportStatus|Chaîne|État de fin du support. Peut contenir les valeurs possibles : None, EOS Version, Future EOS Version, EOS Software, Upcoming EOS Software.
NumberOfWeaknesses|Int|Nombre de faiblesses sur ce logiciel sur cet appareil.
OSPlatform|Chaîne|Plateforme du système d’exploitation en cours d’exécution sur l’appareil ; systèmes d’exploitation spécifiques avec des variantes au sein de la même famille, telles que Windows 10 et Windows 11. Pour plus d’informations, voir les systèmes d’exploitation et les plateformes pris en charge par tvm.
RbacGroupName|Chaîne|Groupe de contrôle d’accès basé sur un rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur sera « Unassigned ». Si l’organisation ne contient aucun groupe RBAC, la valeur est « None ».
rbacGroupId|Chaîne|ID de groupe RBAC (Contrôle d’accès basé sur un rôle).
RegistryPaths|Array[string]|Preuve dans le Registre que le produit est installé sur l’appareil.
SoftwareFirstSeenTimestamp|Chaîne|La première fois que ce logiciel a été vu sur l’appareil.
SoftwareName|Chaîne|Nom du produit logiciel.
SoftwareVendor|Chaîne|Nom du fournisseur de logiciels.
SoftwareVersion|Chaîne|Numéro de version du produit logiciel.

### <a name="23-properties-via-files"></a>2.3 Propriétés (via des fichiers)

Propriété (ID)|Type de données|Description
:---|:---|:---
Exporter des fichiers|chaîne de \[ tableau\]|Liste des URL de téléchargement pour les fichiers qui contiennent la capture instantanée actuelle de l’organisation.
GeneratedTime|Chaîne|Heure de la générer.

## <a name="3-export-software-vulnerabilities-assessment"></a>3. Exportation de l’évaluation des vulnérabilités logicielles

Renvoie toutes les vulnérabilités connues sur un appareil et leurs détails, pour tous les appareils.

### <a name="31-methods"></a>3.1 Méthodes

Méthode|Type de données|Description
:---|:---|:---
Exporter l’évaluation des vulnérabilités **logicielles (réponse JSON)**|Collection d’examens : [3.2 Propriétés (réponse JSON)](#32-properties-json-response)|Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. L’API tire toutes les données de votre organisation en tant que réponses JSON. Cette méthode est la meilleure pour les petites organisations avec moins de 100 Ko d’appareils. La réponse est paginée, afin que vous pouvez utiliser le champ @odata.nextLink de la réponse pour récupérer les résultats suivants.
Exporter l’évaluation des vulnérabilités **logicielles (via des fichiers)**|Entité Investigation Voir : [Propriétés 3.3 (via des fichiers)](#33-properties-via-files)|Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. Cette solution d’API permet d’tirer plus rapidement et de manière plus fiable des données plus volumineuses. Il est donc recommandé pour les grandes organisations, avec plus de 100 Ko d’appareils. Cette API tire toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir de stockage Azure. Cette API vous permet de télécharger toutes vos données à partir stockage Azure comme suit : <ol><li>Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.</li><li>Téléchargez tous les fichiers à l’aide des URL de téléchargement et traiter les données comme vous le souhaitez.</li></ol>
**Évaluation des vulnérabilités** logicielles d’exportation delta **(réponse JSON)**|Collection d’examens Voir : [Exportation delta de propriétés 3.4 (réponse JSON)](#34-properties-delta-export-json-response)|Renvoie un tableau avec une entrée pour chaque combinaison unique de : DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId et EventTimestamp. <p> L’API tire les données de votre organisation en tant que réponses JSON. La réponse est paginée, afin que vous pouvez utiliser le champ @odata.nextLink de la réponse pour récupérer les résultats suivants. L’évaluation complète des vulnérabilités logicielles (réponse JSON) permet d’obtenir un instantané complet de l’évaluation des vulnérabilités logicielles de votre organisation par appareil. Toutefois, l’appel de l’API d’exportation delta est utilisé pour récupérer uniquement les modifications qui se sont produites entre une date sélectionnée et la date actuelle (l’appel d’API « delta »). Au lieu d’obtenir une exportation complète avec une grande quantité de données à chaque fois, vous obtenez uniquement des informations spécifiques sur les vulnérabilités nouvelles, fixes et mises à jour. L’appel d’API d’exportation delta peut également être utilisé pour calculer différents KPI, tels que « combien de vulnérabilités ont été corrigées ? » ou « combien de nouvelles vulnérabilités ont été ajoutées à mon organisation ? » <p> Étant donné que l’appel de l’API d’exportation Delta pour les vulnérabilités logicielles renvoie des données uniquement pour une plage de dates ciblée, il n’est pas considéré comme _une exportation complète._

### <a name="32-properties-json-response"></a>3.2 Propriétés (réponse JSON)

Propriété (ID)|Type de données|Description
:---|:---|:---
CveId|Chaîne|Identificateur unique affecté à la vulnérabilité de sécurité sous le système CVE (Common Vulnerabilities and Exposures).
CvssScore|Chaîne|Score CVSS de la CVE.
DeviceId|Chaîne|Identificateur unique de l’appareil dans le service.
DeviceName|Chaîne|Nom de domaine complet (FQDN) de l’appareil.
DiskPaths|Chaîne de \[ tableau\]|Preuve disque que le produit est installé sur l’appareil.
ExploitabilityLevel|Chaîne|Le niveau d’exploitabilité de cette vulnérabilité (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|Chaîne|Première fois que la CVE de ce produit a été vue sur l’appareil.
ID|Chaîne|Identificateur unique de l’enregistrement.
LastSeenTimestamp|Chaîne|Dernière fois que la CVE a été vue sur l’appareil.
OSPlatform|Chaîne|Plateforme du système d’exploitation en cours d’exécution sur l’appareil ; systèmes d’exploitation spécifiques avec des variantes au sein de la même famille, telles que Windows 10 et Windows 11. Pour plus d’informations, voir les systèmes d’exploitation et les plateformes pris en charge par tvm.
RbacGroupName|Chaîne|Groupe de contrôle d’accès basé sur un rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur sera « Unassigned ». Si l’organisation ne contient aucun groupe RBAC, la valeur est « None ».
rbacGroupId|Chaîne|ID de groupe RBAC (Contrôle d’accès basé sur un rôle).
RecommendationReference|Chaîne|Référence à l’ID de recommandation associé à ce logiciel.
RecommendedSecurityUpdate|Chaîne|Nom ou description de la mise à jour de sécurité fournie par le fournisseur de logiciels pour résoudre la vulnérabilité.
RecommendedSecurityUpdateId|Chaîne|Identificateur des mises à jour de sécurité applicables ou de l’identificateur pour les articles de base de connaissances ou d’aide correspondants.
Chaîne de tableau des chemins \[ d’accès du Registre\]|Preuve dans le Registre que le produit est installé sur l’appareil.
SoftwareName|Chaîne|Nom du produit logiciel.
SoftwareVendor|Chaîne|Nom du fournisseur de logiciels.
SoftwareVersion|Chaîne|Numéro de version du produit logiciel.
VulnerabilitySeverityLevel|Chaîne|Niveau de gravité affecté à la vulnérabilité de sécurité en fonction du score CVSS et des facteurs dynamiques influencés par le paysage des menaces.

### <a name="33-properties-via-files"></a>3.3 Propriétés (via des fichiers)

Propriété (ID)|Type de données|Description
:---|:---|:---
Exporter des fichiers|chaîne de \[ tableau\]|Liste des URL de téléchargement pour les fichiers qui contiennent la capture instantanée actuelle de l’organisation.
GeneratedTime|Chaîne|Heure de la générer.

### <a name="34-properties-delta-export-json-response"></a>3.4 Propriétés (réponse JSON d’exportation delta)

Propriété (ID)|Type de données|Description
:---|:---|:---
CveId |Chaîne|Identificateur unique affecté à la vulnérabilité de sécurité sous le système CVE (Common Vulnerabilities and Exposures).
CvssScore|Chaîne|Score CVSS de la CVE.
DeviceId|Chaîne|Identificateur unique de l’appareil dans le service.
DeviceName|Chaîne|Nom de domaine complet (FQDN) de l’appareil.
DiskPaths|Array[string]|Preuve disque que le produit est installé sur l’appareil.
EventTimestamp|Chaîne|Heure de la découverte de l’événement delta.
ExploitabilityLevel|Chaîne|Niveau d’exploitabilité de la vulnérabilité (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|Chaîne|Première fois que la CVE du produit a été vue sur l’appareil.
ID|Chaîne|Identificateur unique de l’enregistrement.  
LastSeenTimestamp|Chaîne|Dernière fois que la CVE a été vue sur l’appareil.
OSPlatform|Chaîne|Plateforme du système d’exploitation en cours d’exécution sur l’appareil ; systèmes d’exploitation spécifiques avec des variantes au sein de la même famille, telles que Windows 10 et Windows 11. Pour plus d’informations, voir les systèmes d’exploitation et les plateformes pris en charge par tvm.
RbacGroupName|Chaîne|Groupe de contrôle d’accès basé sur un rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur sera « Unassigned ». Si l’organisation ne contient aucun groupe RBAC, la valeur est « None ».
RecommendationReference|Chaîne|Référence à l’ID de recommandation associé à ce logiciel.
RecommendedSecurityUpdate |Chaîne|Nom ou description de la mise à jour de sécurité fournie par le fournisseur de logiciels pour résoudre la vulnérabilité.
RecommendedSecurityUpdateId |Chaîne|Identificateur des mises à jour de sécurité applicables ou identificateur pour les articles de base de connaissances ou d’aide correspondants
RegistryPaths |Array[string]|Preuve dans le Registre que le produit est installé sur l’appareil.
SoftwareName|Chaîne|Nom du produit logiciel.
SoftwareVendor|Chaîne|Nom du fournisseur de logiciels.
SoftwareVersion|Chaîne|Numéro de version du produit logiciel.
État|Chaîne|**Nouveauté** (pour une nouvelle vulnérabilité introduite sur un appareil). **Correction** (pour une vulnérabilité qui n’existe plus sur l’appareil, ce qui signifie qu’elle a été corrigée). **Mise à** jour (pour une vulnérabilité sur un appareil qui a changé. Les modifications possibles sont les suivants : score CVSS, niveau d’exploitabilité, niveau de gravité, DiskPaths, RegistryPaths, RecommendedSecurityUpdate).
VulnerabilitySeverityLevel|Chaîne|Niveau de gravité affecté à la vulnérabilité de sécurité en fonction du score CVSS et des facteurs dynamiques influencés par le paysage des menaces.

## <a name="see-also"></a>Voir aussi

- [Exporter l’évaluation de la configuration sécurisée par appareil](get-assessment-secure-config.md)
- [Exporter l’évaluation de l’inventaire logiciel par appareil](get-assessment-software-inventory.md)
- [Exporter l’évaluation des vulnérabilités logicielles par appareil](get-assessment-software-vulnerabilities.md)

Autres associés

- [Menaces basées sur les risques & gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Vulnérabilités de votre organisation](tvm-weaknesses.md)
