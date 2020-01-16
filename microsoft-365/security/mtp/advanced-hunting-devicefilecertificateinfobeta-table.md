---
title: Table DeviceFileCertificateInfoBeta dans le schéma de chasse avancé
description: En savoir plus sur les informations de signature de fichiers dans le tableau DeviceFileCertificateInfoBeta du schéma de chasse avancé
keywords: chasse aux menaces, recherche de menace, recherche sur les menaces de la cybercriminalité, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, signature numérique, certificat, signature de fichiers, DeviceFileCertificateInfoBeta
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
ms.openlocfilehash: d51fc812ffb82d9af1f706e513498da7611a1a6b
ms.sourcegitcommit: 5b8e9935fe7bfcb96b8f8356119ce23152bd16a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "41210466"
---
# <a name="devicefilecertificateinfobeta"></a>DeviceFileCertificateInfoBeta

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le `DeviceFileCertificateInfoBeta` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les certificats de signature de fichier. Ce tableau utilise les données obtenues à partir des activités de vérification de certificat effectuées régulièrement sur des fichiers sur des points de terminaison.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement
| `DeviceId` | chaîne | Identificateur unique de la machine dans le service
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée
| `IsSigned` | booléen | Indique si le fichier est signé
| `SignatureType` | string | Indique si les informations de signature ont été lues dans le fichier ou lues à partir d’un fichier de catalogue externe.
| `Signer` | string | Informations sur le signataire du fichier
| `SignerHash` | string | Valeur de hachage unique identifiant le signataire
| `Issuer` | string | Informations sur l’autorité de certification émettrice
| `IssuerHash` | string | Valeur de hachage unique permettant l’identification de l’autorité de certification émettrice
| `CrlDistributionPointUrls` | string |  URL du partage réseau qui contient les certificats et la liste de révocation de certificats (CRL)
| `CertificateCreationTime` | DateHeure | Date et heure de création du certificat
| `CertificateExpirationTime` | DateHeure | Date et heure auxquelles le certificat est configuré pour expirer
| `CertificateCountersignatureTime` | DateHeure | Date et heure auxquelles le certificat a été contresigné
| `IsTrusted` | booléen | Indique si le fichier est approuvé en fonction des résultats de la fonction WinVerifyTrust, qui vérifie les informations de certificat racine inconnues, les signatures non valides, les certificats révoqués et d’autres attributs douteux.
| `IsRootSignerMicrosoft` | booléen | Indique si le signataire du certificat racine est Microsoft
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et timestamp.

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)