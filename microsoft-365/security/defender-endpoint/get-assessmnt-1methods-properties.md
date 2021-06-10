---
title: Exporter les méthodes et propriétés d’évaluation par appareil
description: Fournit des informations sur les API qui tirent les données Gestion des menaces et des vulnérabilités données. Il existe différents appels d’API pour obtenir différents types de données. En règle générale, chaque appel d’API contient les données requises pour les appareils de votre organisation. Étant donné que la quantité de données peut être importante, il existe deux façons de les récupérer.
keywords: api, api, évaluation d’exportation, évaluation par appareil, évaluation par ordinateur, rapport d’évaluation des vulnérabilités, évaluation de la vulnérabilité de l’appareil, rapport de vulnérabilité de périphérique, évaluation de la configuration sécurisée, rapport de configuration sécurisée, évaluation des vulnérabilités logicielles, rapport de vulnérabilité logicielle, rapport de vulnérabilité par ordinateur,
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: e820875a3350761824c3e4e67311e55507a9cb6f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2021
ms.locfileid: "52778351"
---
# <a name="export-assessment-methods-and-properties-per-device"></a>Exporter les méthodes et propriétés d’évaluation par appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="api-description"></a>Description de l’API

Fournit des méthodes et des détails de propriété sur les API qui Gestion des menaces et des vulnérabilités données par appareil. Il existe différents appels d’API pour obtenir différents types de données. En règle générale, chaque appel d’API contient les données requises pour les appareils de votre organisation.

> [!Note]
>
> Sauf indication contraire, toutes les méthodes **** d’évaluation d’exportation répertoriées sont l’exportation complète et par appareil **_(également_** appelé **_par appareil)._**

Il existe trois méthodes API que vous pouvez utiliser pour récupérer (exporter) différents types d’informations :

1. Exporter l’évaluation des configurations sécurisées

2. Exporter une évaluation d’inventaire de logiciel

3. Exporter une évaluation de vulnérabilités de logiciel

Pour chaque méthode, il existe différents appels d’API pour obtenir différents types de données. Étant donné que la quantité de données peut être importante, il existe deux façons de les récupérer :

- **OData**  L’API pulls all data in your organization as Json responses, following the OData protocol. Cette méthode est la meilleure pour _les petites organisations avec moins de 100 Ko d’appareils._ La réponse est paginée, afin que vous pouvez utiliser le champ odata.nextLink de la réponse \@ pour récupérer les résultats suivants.

- **via des fichiers** Cette solution d’API permet d’tirer plus rapidement et de manière plus fiable des données plus volumineuses. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 Ko d’appareils. Cette API tire toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir de stockage Azure. Cette API vous permet de télécharger toutes vos données à partir stockage Azure comme suit :

  - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.

  - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traiter les données comme vous le souhaitez.

Les données collectées (à l’aide _d’OData_ ou _via_ des fichiers) sont l’instantané actuel de l’état actuel et ne contiennent pas de données historiques. Pour collecter des données historiques, les clients doivent les enregistrer dans leurs propres stockages de données.

## <a name="1-export-secure-configurations-assessment"></a>1. Exporter l’évaluation des configurations sécurisées

Renvoie toutes les configurations et leur état, par appareil.

### <a name="11-methods"></a>1.1 Méthodes

Méthode | Type de données | Description
:---|:---|:---
Exporter l’évaluation de la configuration **sécurisée (OData)** | Sécurisation de la configuration par collection d’appareils. Voir : [1.2 Properties (OData)](#12-properties-odata) | Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, ConfigurationId. L’API pulls all data in your organization as Json responses, following the OData protocol. Cette méthode est la meilleure pour les petites organisations avec moins de 100 Ko d’appareils. La réponse est paginée, afin que vous pouvez utiliser le champ @odata.nextLink de la réponse pour récupérer les résultats suivants.
Exporter l’évaluation de la configuration **sécurisée (via des fichiers)** | Sécurisation de la configuration par collection d’appareils. Voir : [1.2 Properties (OData)](#12-properties-odata) | Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, ConfigurationId. Cette solution d’API permet d’tirer plus rapidement et de manière plus fiable des données plus volumineuses. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 Ko d’appareils. Cette API tire toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir de stockage Azure. Cette API vous permet de télécharger toutes vos données à partir stockage Azure comme suit : 1.  Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation. 2.  Téléchargez tous les fichiers à l’aide des URL de téléchargement et traiter les données comme vous le souhaitez.

### <a name="12-properties-odata"></a>1.2 Propriétés (OData)

Propriété (ID) | Type de données | Description
:---|:---|:---
ConfigurationCategory | string | Catégorie ou regroupement auquel appartient la configuration : application, système d’exploitation, réseau, comptes, contrôles de sécurité
ConfigurationId | string | Identificateur unique pour une configuration spécifique
ConfigurationImpact | string | Impact nominal de la configuration sur la note de configuration globale (1-10)
ConfigurationName | string | Nom d’affichage de la configuration
ConfigurationSubcategory | string | Sous-catégorie ou sous-groupement auquel appartient la configuration. Dans de nombreux cas, cela décrit des capacités ou des fonctionnalités spécifiques.
DeviceId | string | Identificateur unique de l’appareil dans le service.
DeviceName | string | Nom de domaine complet (FQDN) de l’appareil.
IsApplicable | bool | Indique si la configuration ou la stratégie est applicable
IsCompliant | bool | Indique si la configuration ou la stratégie est correctement configurée.
IsExpectedUserImpact | bool | Indique s’il y aura un impact sur l’utilisateur si la configuration est appliquée
OSPlatform | string | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. Pour plus d’informations, voir les systèmes d’exploitation et les plateformes pris en charge par tvm.
RbacGroupName | string | Groupe de contrôle d’accès basé sur un rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur sera « Unassigned ». Si l’organisation ne contient aucun groupe RBAC, la valeur sera « None ».
RecommendationReference | string | Référence à l’ID de recommandation associé à ce logiciel.
Timestamp | string | Dernière fois que la configuration a été vue sur l’appareil

### <a name="13-properties-via-files"></a>1.3 Propriétés (via des fichiers)

Propriété (ID) | Type de données | Description
:---|:---|:---
Exporter des fichiers | chaîne de \[ tableau\] | Liste des URL de téléchargement pour les fichiers qui contiennent la capture instantanée actuelle de l’organisation.
GeneratedTime | string | Heure de la générer.

## <a name="2-export-software-inventory-assessment"></a>2. Exportation de l’évaluation de l’inventaire logiciel

Renvoie tous les logiciels installés et leurs détails sur chaque appareil.

### <a name="21-methods"></a>2.1 Méthodes

Méthode | Type de données | Description
:---|:---|:---
Exporter l’évaluation de l’inventaire **logiciel (OData)** | Inventaire logiciel par collection d’appareils. Voir : [2.2 Properties (OData)](#22-properties-odata) | Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. L’API pulls all data in your organization as Json responses, following the OData protocol. Cette méthode est la meilleure pour les petites organisations avec moins de 100 Ko d’appareils. La réponse est paginée, afin que vous pouvez utiliser le champ @odata.nextLink de la réponse pour récupérer les résultats suivants.
Exporter l’évaluation de l’inventaire **logiciel (via des fichiers)** | Inventaire logiciel par fichiers d’appareil. Voir : [2.3 Properties (via files)](#23-properties-via-files) | Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. Cette solution d’API permet d’tirer plus rapidement et de manière plus fiable des données plus volumineuses. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 Ko d’appareils. Cette API tire toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir de stockage Azure. Cette API vous permet de télécharger toutes vos données à partir stockage Azure comme suit : 1.  Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation. 2.  Téléchargez tous les fichiers à l’aide des URL de téléchargement et traiter les données comme vous le souhaitez.

### <a name="22-properties-odata"></a>2.2 Propriétés (OData)

Propriété (ID) | Type de données | Description
:---|:---|:---
DeviceId | string | Identificateur unique de l’appareil dans le service.
DeviceName | string | Nom de domaine complet (FQDN) de l’appareil.
DiskPaths | Array[string]  | Preuve disque que le produit est installé sur l’appareil.
EndOfSupportDate | string | Date à laquelle la prise en charge de ce logiciel a ou va se terminer.
EndOfSupportStatus | string | État de fin du support. Peut contenir les valeurs possibles : None, EOS Version, Future EOS Version, EOS Software, Upcoming EOS Software.
ID | string | Identificateur unique de l’enregistrement.
NumberOfWeaknesses | entier|Nombre de faiblesses sur ce logiciel sur cet appareil
OSPlatform | string | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. Pour plus d’informations, voir les systèmes d’exploitation et les plateformes pris en charge par tvm.
RbacGroupName | string | Groupe de contrôle d’accès basé sur un rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur sera « Unassigned ». Si l’organisation ne contient aucun groupe RBAC, la valeur sera « None ».
RegistryPaths | Array[string] | Preuve dans le Registre que le produit est installé sur l’appareil.
SoftwareFirstSeenTimestamp | string | La première fois que ce logiciel a été vu sur l’appareil.
SoftwareName | string | Nom du produit logiciel.
SoftwareVendor | string | Nom du fournisseur de logiciels.
SoftwareVersion | string | Numéro de version du produit logiciel.

### <a name="23-properties-via-files"></a>2.3 Propriétés (via des fichiers)

Propriété (ID) | Type de données | Description
:---|:---|:---
Exporter des fichiers | chaîne de \[ tableau\] | Liste des URL de téléchargement pour les fichiers qui contiennent la capture instantanée actuelle de l’organisation.
GeneratedTime | string | Heure de la générer.

## <a name="3-export-software-vulnerabilities-assessment"></a>3. Exportation de l’évaluation des vulnérabilités logicielles

Renvoie toutes les vulnérabilités connues sur un appareil et leurs détails, pour tous les appareils.

### <a name="31-methods"></a>3.1 Méthodes

Méthode | Type de données | Description
:---|:---|:---
Exporter l’évaluation des vulnérabilités **logicielles (OData)** | Collection Investigation : [3.2 Propriétés (OData)](#32-properties-odata) | Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. L’API pulls all data in your organization as Json responses, following the OData protocol. Cette méthode est la meilleure pour les petites organisations avec moins de 100 Ko d’appareils. La réponse est paginée, afin que vous pouvez utiliser le champ @odata.nextLink de la réponse pour récupérer les résultats suivants.
Exporter l’évaluation des vulnérabilités **logicielles (via des fichiers)** | Entité Investigation Voir : [Propriétés 3.3 (via des fichiers)](#33-properties-via-files) | Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. Cette solution d’API permet d’tirer plus rapidement et de manière plus fiable des données plus volumineuses. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 Ko d’appareils. Cette API tire toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir de stockage Azure. Cette API vous permet de télécharger toutes vos données à partir stockage Azure comme suit : 1.  Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation. 2.  Téléchargez tous les fichiers à l’aide des URL de téléchargement et traiter les données comme vous le souhaitez.

### <a name="32-properties-odata"></a>3.2 Propriétés (OData)

Propriété (ID) | Type de données | Description
:---|:---|:---
CveId | string | Identificateur unique affecté à la vulnérabilité de sécurité sous le système CVE (Common Vulnerabilities and Exposures).
CvssScore | string | Score CVSS de la CVE.
DeviceId | string | Identificateur unique de l’appareil dans le service.
DeviceName | string | Nom de domaine complet (FQDN) de l’appareil.
DiskPaths | Chaîne de \[ tableau\] | Preuve disque que le produit est installé sur l’appareil.
ExploitabilityLevel | string | Le niveau d’exploitabilité de cette vulnérabilité (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp | string | Première fois que la CVE de ce produit a été vue sur l’appareil.
ID | string | Identificateur unique de l’enregistrement.
LastSeenTimestamp | string | Dernière fois que la CVE a été vue sur l’appareil.
OSPlatform | string | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. Pour plus d’informations, voir les systèmes d’exploitation et les plateformes pris en charge par tvm.
RbacGroupName | string | Groupe de contrôle d’accès basé sur un rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur sera « Unassigned ». Si l’organisation ne contient aucun groupe RBAC, la valeur sera « None ».
RecommendationReference | string | Référence à l’ID de recommandation associé à ce logiciel.
RecommendedSecurityUpdate | string | Nom ou description de la mise à jour de sécurité fournie par le fournisseur de logiciels pour résoudre la vulnérabilité.
RecommendedSecurityUpdateId | string | Identificateur des mises à jour de sécurité applicables ou identificateur pour les articles de base de connaissances ou de conseils correspondants
Chaîne de tableau des chemins \[ d’accès du Registre\] | Preuve dans le Registre que le produit est installé sur l’appareil.
SoftwareName | string | Nom du produit logiciel.
SoftwareVendor | string | Nom du fournisseur de logiciels.
SoftwareVersion | string | Numéro de version du produit logiciel.
VulnerabilitySeverityLevel | string | Niveau de gravité affecté à la vulnérabilité de sécurité en fonction du score CVSS et des facteurs dynamiques influencés par le paysage des menaces.

### <a name="33-properties-via-files"></a>3.3 Propriétés (via des fichiers)

Propriété (ID) | Type de données | Description
:---|:---|:---
Exporter des fichiers | chaîne de \[ tableau\]  | Liste des URL de téléchargement pour les fichiers qui contiennent la capture instantanée actuelle de l’organisation.
GeneratedTime | string | Heure de la générer.

## <a name="see-also"></a>Voir aussi

- [Exporter l’évaluation de la configuration sécurisée par appareil](get-assessmnt-secure-cfg.md)

- [Exporter l’évaluation de l’inventaire logiciel par appareil](get-assessmnt-software-inventory.md)

- [Exporter l’évaluation des vulnérabilités logicielles par appareil](get-assessmnt-software-vulnerabilities.md)

Autres associés

- [Menaces basées sur les risques & gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)

- [Vulnérabilités dans votre organisation](tvm-weaknesses.md)
