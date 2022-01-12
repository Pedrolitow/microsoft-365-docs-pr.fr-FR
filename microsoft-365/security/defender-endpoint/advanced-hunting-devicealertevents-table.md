---
title: Table DeviceAlertEvents dans le schéma de recherche avancé
description: En savoir plus sur les événements de génération d’alertes dans la table DeviceAlertEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, mdatp, microsoft defender atp, microsoft defender for endpoint, wdatp search, query, telemetry, schema reference, kusto, table, column, data type, description, DeviceAlertEvents, alert, severity, category
ms.prod: m365-security
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
ms.date: 01/22/2020
ms.technology: mde
ms.openlocfilehash: 32dbff60a37c31cdbfd492eb5d746a10d9b7a185
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61934380"
---
# <a name="devicealertevents"></a>DeviceAlertEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

Le `DeviceAlertEvents` tableau du schéma de [recherche](advanced-hunting-overview.md) avancée contient des informations sur les alertes Microsoft 365 Defender. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tableaux du schéma de chasse avancé, voir la référence de schéma [de chasse avancée.](advanced-hunting-schema-reference.md)

|Nom de colonne|Type de données|Description|
|---|---|---|
|`AlertId`|string|Identificateur unique de l’alerte|
|`Timestamp`|DateHeure|Date et heure d’enregistrement de l’événement|
|`DeviceId`|chaîne|Identificateur unique de l’appareil dans le service|
|`DeviceName`|chaîne|Nom de domaine complet (FQDN) de l’appareil|
|`Severity`|string|Indique l’impact potentiel (élevé, moyen ou faible) de l’indicateur de menace ou de la violation identifié(e) par l’alerte|
|`Category`|string|Type d’indicateur de menace ou d’activité de violation identifié par l’alerte|
|`Title`|string|Titre de l'alerte|
|`FileName`|string|Nom du fichier auquel l’action enregistrée a été appliquée|
|`SHA1`|string|SHA-1 du fichier auquel l’action enregistrée a été appliquée|
|`RemoteUrl`|string|URL ou nom de domaine complet (FQDN) à laquelle/auquel la connexion était en cours|
|`RemoteIP`|string|Adresse IP à laquelle la connexion était en cours|
|`AttackTechniques`|chaîne|MITRE ATT&techniques CK associées à l’activité ayant déclenché l’alerte|
|`ReportId`|long|Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée avec les `DeviceName` colonnes et les `Timestamp`|
|`Table`|string|Table qui contient les détails de l’événement|

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
