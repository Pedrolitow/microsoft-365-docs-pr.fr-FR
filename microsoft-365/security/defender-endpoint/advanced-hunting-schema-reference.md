---
title: Référence de schéma de recherche avancée
description: Découvrez les tableaux du schéma de recherche avancée pour comprendre les données sur qui vous pouvez exécuter des requêtes de recherche de menaces.
keywords: advanced hunting, threat hunting, cyber threat hunting, mdatp, microsoft defender atp, wdatp search, query, telemetry, schema reference, kusto, table, data
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 01/14/2020
ms.technology: mde
ms.openlocfilehash: 7516744b72bc86bbf8f776adde690d75f057efd5
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065113"
---
# <a name="understand-the-advanced-hunting-schema"></a>Comprendre le schéma de repérage avancé

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Le [schéma de recherche](advanced-hunting-overview.md) avancée est composé de plusieurs tables qui fournissent des informations sur les événements ou des informations sur les appareils et d’autres entités. Pour créer des requêtes qui couvrent efficacement sur plusieurs tableaux, vous devez comprendre les tableaux et les colonnes du schéma de repérage avancé.

## <a name="get-schema-information-in-the-security-center"></a>Obtenir des informations de schéma dans le centre de sécurité
Lors de la construction de requêtes, utilisez la référence de schéma intégrée pour obtenir rapidement les informations suivantes sur chaque table du schéma :

- **Description des tableaux**: type de données contenues dans la table et source de ces données.
- **Colonnes**— toutes les colonnes du tableau.
- **Types d’action**: valeurs possibles dans la `ActionType` colonne représentant les types d’événements pris en charge par le tableau. Cette information est fournie uniquement pour les tables qui contiennent des informations sur les événements.
- **Exemple de requête**: exemples de requêtes qui présentent la façon dont la table peut être utilisée.

### <a name="access-the-schema-reference"></a>Accéder à la référence de schéma
Pour accéder rapidement à la  référence de schéma, sélectionnez l’action de référence Afficher en regard du nom de la table dans la représentation de schéma. Vous pouvez également sélectionner une **référence de schéma** pour rechercher une table.

![Image montrant comment accéder à la référence de schéma dans le portail](images/ah-reference.png)

## <a name="learn-the-schema-tables"></a>Découvrir les tableaux de schéma

La référence suivante répertorie tous les tableaux du schéma de recherche avancée. Chaque nom de tableau renvoie à une page décrivant les noms des colonnes de ce tableau.

Les noms de table et de colonne sont également répertoriés dans le Centre de sécurité Microsoft Defender, dans la représentation de schéma sur l’écran de recherche avancée.

| Nom du tableau | Description |
|------------|-------------|
| **[DeviceAlertEvents](advanced-hunting-devicealertevents-table.md)** | Alertes sur le Centre de sécurité Microsoft Defender |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Informations sur l’appareil, y compris les informations sur le système d’exploitation |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Propriétés réseau des appareils, y compris les adaptateurs, les adresses IP et MAC, ainsi que les réseaux et domaines connectés |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Création de processus et événements associés |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** | Connexion réseau et événements connexes |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Création de fichier, modification et autres événements de système de fichiers |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Création et modification d'entrées de registre |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Connexions et autres événements d’authentification |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | Événements de chargement de DLL |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** | Plusieurs types d’événements, y compris les événements déclenchés par des contrôles de sécurité tels que l’Antivirus Microsoft Defender et Exploit Protection |
| **[DeviceFileCertificateInfo](advanced-hunting-devicefilecertificateinfo-table.md)** | Informations de certificat des fichiers signés obtenus à partir d’événements de vérification de certificat sur les points de terminaison |
| **[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)** | Inventaire des logiciels installés sur les appareils, y compris les informations de version et l’état de fin de prise en charge |
| **[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)** | Vulnérabilités logicielles trouvées sur les appareils et liste des mises à jour de sécurité disponibles qui s’adressent à chaque vulnérabilité |
| **[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)** | Base de connaissances des vulnérabilités révélées publiquement, notamment si le code d’exploitation est disponible au public |
| **[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)** | Menace et événements d’évaluation de la gestion des vulnérabilités, indiquant l’état de plusieurs configurations de sécurité sur les appareils |
| **[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)** | Base de connaissances de plusieurs configurations de sécurité utilisées par les menaces et la gestion des vulnérabilités pour évaluer les appareils ; inclut les mappages vers différentes normes et points de référence |


## <a name="related-topics"></a>Sujets associés
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](overview-custom-detections.md)
- [Modifications avancées apportées au schéma de données de recherche](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/advanced-hunting-data-schema-changes/ba-p/1043914)
