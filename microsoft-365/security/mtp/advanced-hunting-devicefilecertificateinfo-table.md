---
title: Table DeviceFileCertificateInfo dans le schéma de chasse avancé
description: En savoir plus sur les informations de signature de fichiers dans le tableau DeviceFileCertificateInfo du schéma de chasse avancé
keywords: chasse avancée, recherche de menace, recherche dans les menaces informatiques, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, signature numérique, certificat, signature de fichiers, DeviceFileCertificateInfo
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
ms.openlocfilehash: cba27b5b43141c8c90f9a8bc7f70c55aabc1979d
ms.sourcegitcommit: ab10c042e5e9c6a7b2afef930ab0d247a6aa275d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "44899314"
---
# <a name="devicefilecertificateinfo"></a>DeviceFileCertificateInfo

**S’applique à :**
- Protection Microsoft contre les menaces

Le `DeviceFileCertificateInfo` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les certificats de signature de fichier. Ce tableau utilise les données obtenues à partir des activités de vérification de certificat effectuées régulièrement sur des fichiers sur des points de terminaison.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | chaîne | Identificateur unique de la machine dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `IsSigned` | booléen | Indique si le fichier est signé |
| `SignatureType` | string | Indique si les informations de signature ont été lues dans le fichier ou lues à partir d’un fichier de catalogue externe. |
| `Signer` | string | Informations sur le signataire du fichier |
| `SignerHash` | string | Valeur de hachage unique identifiant le signataire |
| `Issuer` | string | Informations sur l’autorité de certification émettrice |
| `IssuerHash` | string | Valeur de hachage unique permettant l’identification de l’autorité de certification émettrice |
| `CertificateSerialNumber` | string | Identificateur du certificat propre à l’autorité de certification émettrice. |
| `CrlDistributionPointUrls` | string |  Tableau JSON répertoriant les URL des partages réseau qui contiennent des certificats et des listes de révocation de certificats (CRL) |
| `CertificateCreationTime` | DateHeure | Date et heure de création du certificat |
| `CertificateExpirationTime` | DateHeure | Date et heure auxquelles le certificat est configuré pour expirer |
| `CertificateCountersignatureTime` | DateHeure | Date et heure auxquelles le certificat a été contresigné |
| `IsTrusted` | booléen | Indique si le fichier est approuvé en fonction des résultats de la fonction WinVerifyTrust, qui vérifie les informations de certificat racine inconnues, les signatures non valides, les certificats révoqués et d’autres attributs douteux. |
| `IsRootSignerMicrosoft` | booléen | Indique si le signataire du certificat racine est Microsoft |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et timestamp. | 

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
