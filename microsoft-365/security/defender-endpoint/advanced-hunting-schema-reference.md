---
title: Référence de schéma de recherche avancée
description: Découvrez les tableaux du schéma de recherche avancée pour comprendre les données sur qui vous pouvez exécuter des requêtes de recherche de menaces.
keywords: advanced hunting, threat hunting, cyber threat hunting, mdatp, microsoft defender atp, microsoft defender for endpoint, wdatp search, query, telemetry, schema reference, kusto, table, data
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 01/14/2020
ms.technology: mde
ms.openlocfilehash: b13e3974e71ca5cb24598720b2fe273df7fe82b34e13e24bd2ed53e926c519ba
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53829905"
---
# <a name="understand-the-advanced-hunting-schema-in-microsoft-defender-for-endpoint"></a>Comprendre le schéma de recherche avancé dans Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Le [schéma de recherche](advanced-hunting-overview.md) avancé est composé de plusieurs tables qui fournissent des informations sur les événements ou sur les appareils et d’autres entités. Pour créer des requêtes qui couvrent efficacement sur plusieurs tableaux, vous devez comprendre les tableaux et les colonnes du schéma de repérage avancé.

## <a name="get-schema-information-in-the-security-center"></a>Obtenir des informations de schéma dans le centre de sécurité

Lors de la construction de requêtes, utilisez la référence de schéma intégrée pour obtenir rapidement les informations suivantes sur chaque table du schéma :

- **Description des tableaux**: type de données contenues dans la table et source de ces données.
- **Colonnes**: toutes les colonnes du tableau.
- **Types d’action**: valeurs possibles dans la `ActionType` colonne représentant les types d’événements pris en charge par le tableau. Cette information est fournie uniquement pour les tables qui contiennent des informations sur les événements.
- **Exemple de requête**: exemples de requêtes qui présentent la façon dont la table peut être utilisée.

### <a name="access-the-schema-reference"></a>Accéder à la référence de schéma

Pour accéder rapidement à la  référence de schéma, sélectionnez l’action de référence Afficher en regard du nom de la table dans la représentation de schéma. Vous pouvez également sélectionner une **référence de schéma** pour rechercher une table.

![Image montrant comment accéder à la référence de schéma dans le portail](images/ah-reference.png)

## <a name="learn-the-schema-tables"></a>Découvrir les tableaux de schéma

La référence suivante répertorie tous les tableaux du schéma de recherche avancée. Chaque nom de tableau renvoie à une page décrivant les noms des colonnes de ce tableau.

Les noms de table et de colonne sont également répertoriés dans le Centre de sécurité Microsoft Defender, dans la représentation de schéma sur l’écran de recherche avancée.

<br>

****

|Nom du tableau|Description|
|---|---|
|**[DeviceAlertEvents](advanced-hunting-devicealertevents-table.md)**|Alertes sur Centre de sécurité Microsoft Defender|
|**[DeviceInfo](advanced-hunting-deviceinfo-table.md)**|Informations sur l’appareil, y compris les informations sur le système d’exploitation|
|**[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)**|Propriétés réseau des appareils, y compris les adaptateurs, les adresses IP et MAC, ainsi que les réseaux et domaines connectés|
|**[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)**|Création de processus et événements associés|
|**[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)**|Connexion réseau et événements connexes|
|**[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)**|Création de fichier, modification et autres événements de système de fichiers|
|**[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)**|Création et modification d'entrées de registre|
|**[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)**|Connexions et autres événements d’authentification|
|**[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)**|Événements de chargement de DLL|
|**[DeviceEvents](advanced-hunting-deviceevents-table.md)**|Plusieurs types d’événements, y compris les événements déclenchés par des contrôles de sécurité tels que Antivirus Microsoft Defender et Exploit Protection|
|**[DeviceFileCertificateInfo](advanced-hunting-devicefilecertificateinfo-table.md)**|Informations de certificat des fichiers signés obtenus à partir d’événements de vérification de certificat sur les points de terminaison|
|**[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)**|Inventaire des logiciels installés sur les appareils, y compris les informations de version et l’état de fin de prise en charge|
|**[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)**|Vulnérabilités logicielles trouvées sur les appareils et liste des mises à jour de sécurité disponibles qui s’adressent à chaque vulnérabilité|
|**[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)**|Base de connaissances des vulnérabilités révélées publiquement, notamment si le code d’exploitation est disponible au public|
|**[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)**|Menace et événements d’évaluation de la gestion des vulnérabilités, indiquant l’état de plusieurs configurations de sécurité sur les appareils|
|**[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)**|Base de connaissances de plusieurs configurations de sécurité utilisées par les menaces et la gestion des vulnérabilités pour évaluer les appareils ; inclut les mappages vers différentes normes et points de référence|
|

> [!TIP]
> Utilisez la recherche avancée [dans Microsoft 365 Defender](/microsoft-365/security/defender/advanced-hunting-overview) pour la recherche de menaces à l’aide des données de Defender pour endpoint, Microsoft Defender pour Office 365, Microsoft Cloud App Security et Microsoft Defender pour l’identité. [Activer Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable).

En savoir plus sur la façon de déplacer vos flux de travail de recherche avancée de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender dans Migrer des requêtes de recherche avancée à partir de [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde).

## <a name="related-topics"></a>Sujets connexes

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](overview-custom-detections.md)
- [Modifications avancées apportées au schéma de données de recherche](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/advanced-hunting-data-schema-changes/ba-p/1043914)
