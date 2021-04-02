---
title: Tables de données dans le schéma de recherche avancée Microsoft 365 Defender
description: Découvrez les tableaux du schéma de repérage avancé pour comprendre les données sur lesquelles vous pouvez exécuter des requêtes de repérage de menace
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, data
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 48e72bf2384361315c1ed94e83f3e61f667da714
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51499708"
---
# <a name="understand-the-advanced-hunting-schema"></a>Comprendre le schéma de repérage avancé

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le [schéma de recherche](advanced-hunting-overview.md) avancée est composé de plusieurs tables qui fournissent des informations sur les événements ou sur les appareils, les alertes, les identités et d’autres types d’entités. Pour créer des requêtes qui couvrent efficacement sur plusieurs tableaux, vous devez comprendre les tableaux et les colonnes du schéma de repérage avancé.

## <a name="get-schema-information-in-the-security-center"></a>Obtenir des informations de schéma dans le centre de sécurité
Lors de la construction de requêtes, utilisez la référence de schéma intégrée pour obtenir rapidement les informations suivantes sur chaque table du schéma :

- **Description des tableaux**: type de données contenues dans la table et source de ces données.
- **Colonnes**— toutes les colonnes du tableau.
- **Types d’action**: valeurs possibles dans la `ActionType` colonne représentant les types d’événements pris en charge par le tableau. Ces informations sont fournies uniquement pour les tables qui contiennent des informations sur les événements.
- **Exemple de requête**: exemples de requêtes qui présentent la façon dont la table peut être utilisée.

### <a name="access-the-schema-reference"></a>Accéder à la référence de schéma
Pour accéder rapidement à la  référence de schéma, sélectionnez l’action de référence Afficher en regard du nom de la table dans la représentation de schéma. Vous pouvez également sélectionner une **référence de schéma** pour rechercher une table.   

![Image montrant comment accéder à la référence de schéma dans le portail ](../../media/mtp-ah/ah-reference.png) 

## <a name="learn-the-schema-tables"></a>Découvrir les tableaux de schéma
La référence suivante répertorie les tableaux du schéma. Chaque nom de tableau renvoie à une page décrivant les noms des colonnes de ce tableau. Les noms de table et de colonne sont également répertoriés dans le centre de sécurité dans le cadre de la représentation de schéma sur l’écran de recherche avancée.

| Nom du tableau | Description |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | Fichiers, adresses IP, URL, utilisateurs ou appareils associés à des alertes |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | Alertes de Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365, Microsoft Cloud App Security et Microsoft Defender pour l’identité, y compris les informations de gravité et la catégorisation des menaces  |
| **[AppFileEvents](advanced-hunting-appfileevents-table.md)** | Activités liées aux fichiers dans les applications et services cloud |
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)** | Événements impliquant des comptes et des objets dans Office 365 et d’autres applications et services cloud |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** | Plusieurs types d’événements, y compris les événements déclenchés par des contrôles de sécurité tels que l’Antivirus Windows Defender et la protection contre l’exploitation |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** | Informations de certificat des fichiers signés obtenus à partir d’événements de vérification de certificat sur les points de terminaison |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Création de fichier, modification et autres événements de système de fichiers |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | Événements de chargement de DLL |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Informations sur l’ordinateur, y compris les informations de système d’exploitation |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Connectez-vous et autres événements d’authentification sur les appareils |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** | Connexion réseau et événements connexes |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Propriétés réseau des appareils, y compris les cartes physiques, les adresses IP et MAC, ainsi que les réseaux et domaines connectés |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Création de processus et événements associés |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Création et modification d'entrées de registre |
| **[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)** | Menace et événements d’évaluation de la gestion des vulnérabilités, indiquant l’état de plusieurs configurations de sécurité sur les appareils |
| **[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)** | Base de connaissances de plusieurs configurations de sécurité utilisées par les menaces et la gestion des vulnérabilités pour évaluer les appareils ; inclut les mappages vers différentes normes et points de référence  |
| **[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)** | Inventaire des logiciels installés sur les appareils, y compris les informations de version et l’état de fin de prise en charge |
| **[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)** | Vulnérabilités logicielles trouvées sur les appareils et liste des mises à jour de sécurité disponibles qui s’adressent à chaque vulnérabilité |
| **[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)** | Base de connaissances des vulnérabilités révélées publiquement, notamment si le code d’exploitation est disponible au public |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | Informations sur les fichiers joints aux e-mails |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Événements de messagerie Microsoft 365, y compris les événements de remise et de blocage du courrier électronique |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | Événements de sécurité qui se produisent après la remise, une fois que Microsoft 365 a remis les messages électroniques à la boîte aux lettres du destinataire |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | Informations sur les URL des e-mails |
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)** | Événements impliquant un contrôleur de domaine local exécutant Active Directory (AD). Ce tableau couvre une plage d’événements liés à l’identité et d’événements système sur le contrôleur de domaine. |
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
