---
title: Tableaux de données dans le schéma de repérage avancé de la Protection Microsoft contre les menaces
description: Découvrez les tableaux du schéma de repérage avancé pour comprendre les données sur lesquelles vous pouvez exécuter des requêtes de repérage de menace
keywords: chasse aux menaces, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, données
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: f22a046dc5289405aaf59086ed535016cc46bae9
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48197666"
---
# <a name="understand-the-advanced-hunting-schema"></a>Comprendre le schéma de repérage avancé

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le schéma de [chasse avancé](advanced-hunting-overview.md) est composé de plusieurs tables qui fournissent des informations sur les événements ou des informations sur les appareils, les alertes, les identités et d’autres types d’entité. Pour créer des requêtes qui couvrent efficacement sur plusieurs tableaux, vous devez comprendre les tableaux et les colonnes du schéma de repérage avancé.

## <a name="get-schema-information-in-the-security-center"></a>Obtenir des informations de schéma dans le centre de sécurité
Lors de la création de requêtes, utilisez la référence de schéma intégrée pour obtenir rapidement les informations suivantes sur chaque table du schéma :

- **Description des tableaux** : type de données contenues dans la table et la source de ces données.
- **Columns** : toutes les colonnes du tableau.
- **Types d’actions** : valeurs possibles dans la `ActionType` colonne représentant les types d’événement pris en charge par le tableau. Cela est uniquement fourni pour les tables qui contiennent des informations d’événement.
- Exemple de **requête** — exemples de requêtes qui démontrent comment la table peut être utilisée.

### <a name="access-the-schema-reference"></a>Accéder à la référence de schéma
Pour accéder rapidement à la référence de schéma, sélectionnez l’action **afficher la référence** en regard du nom de la table dans la représentation du schéma. Vous pouvez également sélectionner **référence de schéma** pour rechercher un tableau.   

![Image illustrant l’accès à la référence de schéma dans le portail ](../../media/mtp-ah/ah-reference.png) 

## <a name="learn-the-schema-tables"></a>Découvrir les tables de schéma
La référence suivante répertorie les tableaux du schéma. Chaque nom de tableau renvoie à une page décrivant les noms des colonnes de ce tableau. Les noms des tables et des colonnes apparaissent également dans le centre de sécurité dans cadre de la représentation du schéma sur l’écran de repérage avancé.

| Nom du tableau | Description |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | Fichiers, adresses IP, URL, utilisateurs ou périphériques associés à des alertes |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | Alertes de Microsoft Defender ATP, Office 365 ATP, sécurité de l’application Cloud Microsoft et Azure ATP, y compris les informations de gravité et la catégorisation des menaces  |
| **[AppFileEvents](advanced-hunting-appfileevents-table.md)** | Activités liées aux fichiers dans les applications et les services Cloud |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** | Plusieurs types d’événements, y compris les événements déclenchés par des contrôles de sécurité tels que l’Antivirus Windows Defender et la protection contre l’exploitation |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** | Informations de certificat des fichiers signés provenant d’événements de vérification de certificat sur les points de terminaison |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Création de fichier, modification et autres événements de système de fichiers |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | Événements de chargement de DLL |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Informations sur l’ordinateur, y compris les informations de système d’exploitation |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Connexions et autres événements d’authentification sur les appareils |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** | Connexion réseau et événements connexes |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Propriétés réseau des ordinateurs, y compris les adaptateurs, les adresses IP et MAC, ainsi que les réseaux et domaines connectés |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Création de processus et événements associés |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Création et modification d'entrées de registre |
| **[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)** | Menace et événements d’évaluation de la gestion des vulnérabilités, indiquant l’état de plusieurs configurations de sécurité sur les appareils |
| **[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)** | Base de connaissances de plusieurs configurations de sécurité utilisées par les menaces et la gestion des vulnérabilités pour évaluer les appareils ; inclut les mappages vers différentes normes et points de référence  |
| **[DeviceTvmSoftwareInventoryVulnerabilities](advanced-hunting-devicetvmsoftwareinventoryvulnerabilities-table.md)** | Inventaire des logiciels sur les appareils, ainsi que les vulnérabilités connues dans ces produits logiciels |
| **[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)** | Base de connaissances des vulnérabilités révélées publiquement, notamment si le code d’exploitation est disponible au public |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | Informations sur les fichiers joints aux courriers électroniques |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Événements de messagerie Microsoft 365, y compris les événements de remise et de blocage du courrier électronique |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | Événements de sécurité qui se produisent après la livraison, après que Microsoft 365 a remis les courriers électroniques à la boîte aux lettres du destinataire |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | Informations sur les URL des courriers électroniques |
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)** | Événements impliquant un contrôleur de domaine sur site exécutant Active Directory (AD). Ce tableau couvre un éventail d’événements liés à l’identité, ainsi que des événements système sur le contrôleur de domaine. |
| **[IdentityInfo](advanced-hunting-identityinfo-table.md)** | Informations de compte provenant de différentes sources, notamment Azure Active Directory |
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)** | Événements d’authentification sur Active Directory et Microsoft Online Services |
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)** | Activités de requête exécutées sur des objets Active Directory, tels que des utilisateurs, des groupes, des appareils et des domaines |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les emails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
