---
title: Tableaux de données dans le schéma de repérage avancé de la Protection Microsoft contre les menaces
description: Découvrez les tableaux du schéma de repérage avancé pour comprendre les données sur lesquelles vous pouvez exécuter des requêtes de repérage de menace
keywords: repérage avancé, repérage de menace, repérage de cybermenace, recherche, requête, télémétrie, référence de schéma, kusto, tableau, données
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
ms.openlocfilehash: 1803445dfd9b46fce23b0dcc9585ea543f1b0347
ms.sourcegitcommit: 0c9c28a87201c7470716216d99175356fb3d1a47
ms.translationtype: MT + HT Review
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2019
ms.locfileid: "39910999"
---
# <a name="understand-the-advanced-hunting-schema"></a>Comprendre le schéma de repérage avancé

**S’applique à :**
- Protection Microsoft contre les menaces

[!include[Prerelease information](prerelease.md)]

Le schéma [repérage avancé](advanced-hunting-overview.md) est constitué de plusieurs tableaux qui fournissent des informations sur les événements ou des informations sur les ordinateurs et entités. Pour créer des requêtes qui couvrent efficacement sur plusieurs tableaux, vous devez comprendre les tableaux et les colonnes du schéma de repérage avancé.

## <a name="schema-tables"></a>Tableaux de schéma

La référence suivante répertorie les tableaux du schéma. Chaque nom de tableau renvoie à une page décrivant les noms des colonnes de ce tableau. Les noms des tables et des colonnes apparaissent également dans le centre de sécurité dans cadre de la représentation du schéma sur l’écran de repérage avancé.

| Nom du tableau | Description |
|------------|-------------|
| **[MachineInfo](advanced-hunting-machineinfo-table.md)** | Informations sur l’ordinateur, y compris les informations de système d’exploitation |
| **[MachineNetworkInfo](advanced-hunting-machinenetworkinfo-table.md)** | Propriétés réseau des ordinateurs, y compris les adaptateurs, les adresses IP et MAC, ainsi que les réseaux et domaines connectés |
| **[ProcessCreationEvents](advanced-hunting-processcreationevents-table.md)** | Création de processus et événements associés |
| **[NetworkCommunicationEvents](advanced-hunting-networkcommunicationevents-table.md)** | Connexion réseau et événements connexes |
| **[FileCreationEvents](advanced-hunting-filecreationevents-table.md)** | Création de fichier, modification et autres événements de système de fichiers |
| **[RegistryEvents](advanced-hunting-registryevents-table.md)** | Création et modification d'entrées de registre |
| **[LogonEvents](advanced-hunting-logonevents-table.md)** | Connexions et autres événements d’authentification |
| **[ImageLoadEvents](advanced-hunting-imageloadevents-table.md)** | Événements de chargement de DLL |
| **[MiscEvents](advanced-hunting-miscevents-table.md)** | Plusieurs types d’événements, y compris les événements déclenchés par des contrôles de sécurité tels que l’Antivirus Windows Defender et la protection contre l’exploitation |
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
