---
title: Tables de données dans le schéma de chasse Microsoft 365 Defender avancé
description: Découvrez les tableaux du schéma de repérage avancé pour comprendre les données sur lesquelles vous pouvez exécuter des requêtes de repérage de menace
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, données
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.openlocfilehash: 2fb0ebc9b3bc095a7cf0eb76fe4440283e175b7f
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68639574"
---
# <a name="understand-the-advanced-hunting-schema"></a>Comprendre le schéma de repérage avancé

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le schéma de [chasse avancé](advanced-hunting-overview.md) est constitué de plusieurs tables qui fournissent des informations sur les événements ou des informations sur les appareils, les alertes, les identités et d’autres types d’entités. Pour générer efficacement des requêtes qui s’étendent sur plusieurs tables, vous devez comprendre les tables et les colonnes du schéma de repérage avancé.

<a name="get-schema-information-in-the-security-center"></a>

## <a name="get-schema-information"></a>Obtenir des informations sur le schéma

Lors de la construction de requêtes, utilisez la référence de schéma intégrée pour obtenir rapidement les informations suivantes sur chaque table du schéma :

- **Description des tables** : type de données contenues dans la table et source de ces données.
- **Colonnes** : toutes les colonnes de la table.
- **Types d’actions** : valeurs possibles dans la `ActionType` colonne représentant les types d’événements pris en charge par la table. Ces informations sont fournies uniquement pour les tables qui contiennent des informations sur les événements.
- **Exemple de requête** : exemples de requêtes qui présentent la façon dont la table peut être utilisée.

### <a name="access-the-schema-reference"></a>Accéder à la référence de schéma
Pour accéder rapidement à la référence de schéma, sélectionnez l’action **Afficher la référence** en regard du nom de la table dans la représentation de schéma. Vous pouvez également sélectionner **la référence de schéma** pour rechercher une table.

:::image type="content" source="../../media/understand-schema-1.png" alt-text="Page référence du schéma sur la page Repérage avancé dans le portail Microsoft 365 Defender" lightbox="../../media/understand-schema-1.png":::

## <a name="learn-the-schema-tables"></a>Découvrir les tables de schéma
La référence suivante répertorie les tableaux du schéma. Chaque nom de tableau renvoie à une page décrivant les noms des colonnes de ce tableau. Les noms de tables et de colonnes sont également répertoriés dans Defender pour cloud dans le cadre de la représentation de schéma sur l’écran de chasse avancé.

| Nom du tableau | Description |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | Fichiers, adresses IP, URL, utilisateurs ou appareils associés aux alertes |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | Alertes provenant de Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender for Cloud Apps et Microsoft Defender pour Identity, y compris les informations de gravité et la catégorisation des menaces  |
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)** | Événements impliquant des comptes et des objets dans Office 365 et d’autres applications et services cloud |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** | Plusieurs types d’événements, y compris les événements déclenchés par des contrôles de sécurité tels que Microsoft Defender Antivirus et la protection contre les attaques |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** | Informations de certificat des fichiers signés obtenus à partir d’événements de vérification de certificat sur les points de terminaison |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Création de fichier, modification et autres événements de système de fichiers |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | Événements de chargement de DLL |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Informations sur l’ordinateur, y compris les informations de système d’exploitation |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Connexions et autres événements d’authentification |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** | Connexion réseau et événements connexes |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Propriétés réseau des ordinateurs, y compris les adaptateurs, les adresses IP et MAC, ainsi que les réseaux et domaines connectés |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Création de processus et événements associés |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Création et modification d'entrées de registre |
| **[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)** | Gestion des vulnérabilités Microsoft Defender les événements d’évaluation, indiquant l’état des différentes configurations de sécurité sur les appareils |
| **[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)** | Base de connaissances de différentes configurations de sécurité utilisées par Gestion des vulnérabilités Microsoft Defender pour évaluer les appareils ; inclut des mappages à différents standards et benchmarks  |
| **[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)** | Inventaire des logiciels installés sur les appareils, y compris les informations de version et l’état de fin de prise en charge |
| **[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)** | Vulnérabilités logicielles trouvées sur les appareils et liste des mises à jour de sécurité disponibles qui s’adressent à chaque vulnérabilité |
| **[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)** | Base de connaissances des vulnérabilités révélées publiquement, notamment si le code d’exploitation est disponible au public |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | Informations sur les fichiers joints aux e-mails |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Événements d’e-mails Microsoft 365, y compris les événements de remise et de blocage d’e-mail |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | Événements de sécurité qui se produisent après la remise, une fois que Microsoft 365 a remis les e-mails à la boîte aux lettres du destinataire |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | Informations sur les URL des e-mails |
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)** | Événements impliquant un contrôleur de domaine local exécutant Active Directory (AD). Ce tableau couvre un ensemble d’événements liés à l’identité, ainsi que des événements système sur le contrôleur de domaine. |
| **[IdentityInfo](advanced-hunting-identityinfo-table.md)** | Informations de compte provenant de différentes sources, notamment Azure Active Directory |
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)** | Événements d’authentification sur Active Directory et les services en ligne Microsoft |
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)** | Requêtes pour les objets Active Directory, tels que les utilisateurs, les groupes, les appareils et les domaines |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
