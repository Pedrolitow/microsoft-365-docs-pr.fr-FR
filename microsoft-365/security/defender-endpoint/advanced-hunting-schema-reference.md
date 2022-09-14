---
title: Informations de référence sur les schémas de chasse avancés
description: Découvrez les tables du schéma de chasse avancé pour comprendre les données sur laquelle vous pouvez exécuter des requêtes de repérage de menaces.
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, mdatp, microsoft defender atp, microsoft defender pour point de terminaison, recherche wdatp, requête, télémétrie, référence de schéma, kusto, table, données
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 01/14/2020
ms.subservice: mde
ms.openlocfilehash: d53f0cb437a79e4a6841293833dd0f76c014154d
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67679732"
---
# <a name="understand-the-advanced-hunting-schema-in-microsoft-defender-for-endpoint"></a>Comprendre le schéma de chasse avancé dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Le schéma [de chasse avancé](advanced-hunting-overview.md) est constitué de plusieurs tables qui fournissent des informations d’événement ou des informations sur les appareils et d’autres entités. Pour générer efficacement des requêtes qui s’étendent sur plusieurs tables, vous devez comprendre les tables et les colonnes du schéma de repérage avancé.

## <a name="get-schema-information-in-the-defender-for-cloud"></a>Obtenir des informations de schéma dans Defender pour le cloud

Lors de la construction de requêtes, utilisez la référence de schéma intégrée pour obtenir rapidement les informations suivantes sur chaque table du schéma :

- **Description des tables** : type de données contenues dans la table et source de ces données.
- **Colonnes** : toutes les colonnes de la table.
- **Types d’actions** : valeurs possibles dans la `ActionType` colonne représentant les types d’événements pris en charge par la table. Ces valeurs sont fournies uniquement pour les tables qui contiennent des informations sur les événements.
- **Exemple de requête** : exemples de requêtes qui présentent la façon dont la table peut être utilisée.

### <a name="access-the-schema-reference"></a>Accéder à la référence de schéma

Pour accéder rapidement à la référence de schéma, sélectionnez l’action **Afficher la référence** en regard du nom de la table dans la représentation de schéma. Vous pouvez également sélectionner **la référence de schéma** pour rechercher une table.

:::image type="content" source="images/ah-reference.png" alt-text="Page Repérage avancé" lightbox="images/ah-reference.png":::

## <a name="learn-the-schema-tables"></a>Découvrir les tables de schéma

La référence suivante répertorie toutes les tables du schéma de chasse avancé. Chaque nom de tableau renvoie à une page décrivant les noms des colonnes de ce tableau.

Les noms de tables et de colonnes sont également répertoriés dans le portail Microsoft 365 Defender, dans la représentation de schéma sur l’écran de chasse avancé.

<br>

****

|Nom du tableau|Description|
|---|---|
|**[DeviceAlertEvents](advanced-hunting-devicealertevents-table.md)**|Alertes sur Microsoft 365 Defender |
|**[DeviceInfo](advanced-hunting-deviceinfo-table.md)**|Informations sur l’appareil, y compris les informations du système d’exploitation|
|**[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)**|Propriétés réseau des appareils, notamment les cartes, les adresses IP et MAC, ainsi que les réseaux et domaines connectés|
|**[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)**|Création de processus et événements associés|
|**[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)**|Connexion réseau et événements connexes|
|**[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)**|Création de fichier, modification et autres événements de système de fichiers|
|**[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)**|Création et modification d'entrées de registre|
|**[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)**|Connexions et autres événements d’authentification|
|**[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)**|Événements de chargement de DLL|
|**[DeviceEvents](advanced-hunting-deviceevents-table.md)**|Plusieurs types d’événements, y compris les événements déclenchés par des contrôles de sécurité tels que l’antivirus Microsoft Defender et la protection contre les attaques|
|**[DeviceFileCertificateInfo](advanced-hunting-devicefilecertificateinfo-table.md)**|Informations de certificat des fichiers signés obtenus à partir d’événements de vérification de certificat sur les points de terminaison|
|**[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)**|Inventaire des logiciels installés sur les appareils, y compris les informations de version et l’état de fin de prise en charge|
|**[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)**|Vulnérabilités logicielles trouvées sur les appareils et liste des mises à jour de sécurité disponibles qui s’adressent à chaque vulnérabilité|
|**[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)**|Base de connaissances des vulnérabilités révélées publiquement, notamment si le code d’exploitation est disponible au public|
|**[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)**|Gestion des vulnérabilités Microsoft Defender les événements d’évaluation, indiquant l’état des différentes configurations de sécurité sur les appareils|
|**[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)**|Base de connaissances de différentes configurations de sécurité utilisées par Defender Vulnerability Management pour évaluer les appareils ; inclut des mappages à différents standards et points de référence|
|

> [!TIP]
> Utilisez [la chasse avancée à Microsoft 365 Defender](/microsoft-365/security/defender/advanced-hunting-overview) pour rechercher des menaces à l’aide des données de Defender pour point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender for Cloud Apps et Microsoft Defender pour Identity. [Activez Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable).

En savoir plus sur le déplacement de vos flux de travail de chasse avancés de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender dans [Migrer des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde).

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](overview-custom-detections.md)
- [Modifications avancées du schéma de données de chasse](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/advanced-hunting-data-schema-changes/ba-p/1043914)
