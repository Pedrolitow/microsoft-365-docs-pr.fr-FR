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
ms.openlocfilehash: 032368e35cdfc991df4c01643e49cee538549f39
ms.sourcegitcommit: ab10c042e5e9c6a7b2afef930ab0d247a6aa275d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "44899362"
---
# <a name="understand-the-advanced-hunting-schema"></a>Comprendre le schéma de repérage avancé

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le schéma [repérage avancé](advanced-hunting-overview.md) est constitué de plusieurs tableaux qui fournissent des informations sur les événements ou des informations sur les ordinateurs et entités. Pour créer des requêtes qui couvrent efficacement sur plusieurs tableaux, vous devez comprendre les tableaux et les colonnes du schéma de repérage avancé.

## <a name="schema-tables"></a>Tableaux de schéma

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
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Connexions et autres événements d’authentification |
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
| **[IdentityInfo](advanced-hunting-identityinfo-table.md)** | Informations de compte provenant de différentes sources, notamment Azure Active Directory |
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)** | Événements d’authentification enregistrés par Active Directory et d’autres services Microsoft Online |
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)** | Activités de requête exécutées sur des objets Active Directory, tels que des utilisateurs, des groupes, des appareils et des domaines |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
