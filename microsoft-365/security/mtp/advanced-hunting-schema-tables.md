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
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: aa2fbeebed10bcb1f0c4078a161be99d16d3b97b
ms.sourcegitcommit: 5b8e9935fe7bfcb96b8f8356119ce23152bd16a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "41210319"
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
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Informations sur l’ordinateur, y compris les informations de système d’exploitation |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Propriétés réseau des ordinateurs, y compris les adaptateurs, les adresses IP et MAC, ainsi que les réseaux et domaines connectés |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Création de processus et événements associés |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** | Connexion réseau et événements connexes |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Création de fichier, modification et autres événements de système de fichiers |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Création et modification d'entrées de registre |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Connexions et autres événements d’authentification |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | Événements de chargement de DLL |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** | Plusieurs types d’événements, y compris les événements déclenchés par des contrôles de sécurité tels que l’Antivirus Windows Defender et la protection contre l’exploitation |
| **[DeviceFileCertificateInfoBeta](advanced-hunting-devicefilecertificateinfobeta-table.md)** | Informations de certificat des fichiers signés provenant d’événements de vérification de certificat sur les points de terminaison |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Événements d’e-mails Office 365, y compris les événements de remise et de blocage d’e-mail |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | Informations sur les fichiers joints aux e-mails Office 365 |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | Informations sur les URL des e-mails Office 365 |
| **[DeviceTvmSoftwareInventoryVulnerabilities](advanced-hunting-tvm-softwareinventory-table.md)** | Inventaire des logiciels sur les appareils, ainsi que les vulnérabilités connues dans ces produits logiciels |
| **[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-tvm-softwarevulnerability-table.md)** | Base de connaissances des vulnérabilités révélées publiquement, notamment si le code d’exploitation est disponible au public |
| **[DeviceTvmSecureConfigurationAssessment](advanced-hunting-tvm-configassessment-table.md)** | Menace et événements d’évaluation de la gestion des vulnérabilités, indiquant l’état de plusieurs configurations de sécurité sur les appareils |
| **[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-tvm-secureconfigkb-table.md)** | Base de connaissances de plusieurs configurations de sécurité utilisées par les menaces et la gestion des vulnérabilités pour évaluer les appareils ; inclut les mappages vers différentes normes et points de référence  |

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)