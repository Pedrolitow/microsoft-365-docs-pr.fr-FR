---
title: Table DeviceFileCertificateInfo dans le schéma de chasse avancé
description: En savoir plus sur les informations de signature de fichier dans la table DeviceFileCertificateInfo du schéma de repérage avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, signature numérique, certificat, signature de fichier, DeviceFileCertificateInfo
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
ms.openlocfilehash: 694d5dd15dbead030e392f3095c0cc578dc8f85f
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68640893"
---
# <a name="devicefilecertificateinfo"></a>DeviceFileCertificateInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

La `DeviceFileCertificateInfo` table du schéma [de chasse avancé](advanced-hunting-overview.md) contient des informations sur les certificats de signature de fichier. Ce tableau utilise les données obtenues à partir d’activités de vérification de certificat régulièrement effectuées sur des fichiers sur des points de terminaison.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `DeviceId` | `string` | Identificateur unique de la machine dans le service |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de la machine |
| `SHA1` | `string` | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `IsSigned` | `boolean` | Indique si le fichier est signé |
| `SignatureType` | `string` | Indique si les informations de signature ont été lues en tant que contenu incorporé dans le fichier lui-même ou lues à partir d’un fichier catalogue externe |
| `Signer` | `string` | Informations sur le signataire du fichier |
| `SignerHash` | `string` | Valeur de hachage unique identifiant le signataire |
| `Issuer` | `string` | Informations sur l’autorité de certification émettrice |
| `IssuerHash` | `string` | Valeur de hachage unique identifiant l’autorité de certification émettrice |
| `CertificateSerialNumber` | `string` | Identificateur du certificat propre à l’autorité de certification émettrice |
| `CrlDistributionPointUrls` | `string` |  Tableau JSON répertoriant les URL des partages réseau qui contiennent des certificats et des listes de révocation de certificats |
| `CertificateCreationTime` | `datetime` | Date et heure de création du certificat |
| `CertificateExpirationTime` | `datetime` | Date et heure d’expiration du certificat |
| `CertificateCountersignatureTime` | `datetime` | Date et heure à laquelle le certificat a été contre-signé |
| `IsTrusted` | `boolean` | Indique si le fichier est approuvé en fonction des résultats de la fonction WinVerifyTrust, qui recherche des informations de certificat racine inconnues, des signatures non valides, des certificats révoqués et d’autres attributs douteux. |
| `IsRootSignerMicrosoft` | `boolean` | Indique si le signataire du certificat racine est Microsoft et si le fichier est inclus dans le système d’exploitation Windows |
| `ReportId` | `long` | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp. | 

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
