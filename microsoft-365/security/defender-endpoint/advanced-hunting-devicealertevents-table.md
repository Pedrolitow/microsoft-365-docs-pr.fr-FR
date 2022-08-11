---
title: Table DeviceAlertEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements de génération d’alerte dans la table DeviceAlertEvents du schéma de chasse avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, mdatp, microsoft defender atp, microsoft defender pour point de terminaison, recherche wdatp, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, DeviceAlertEvents, alerte, gravité, catégorie
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
ms.openlocfilehash: 1742c674cb982282d8edbe73e43e6ea59fedf8f6
ms.sourcegitcommit: 414682b9bf42dc19a89c893d3c515aee9765b6e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2022
ms.locfileid: "67281836"
---
# <a name="devicealertevents"></a>DeviceAlertEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!IMPORTANT]
> Les `AlertInfo` tables et `AlertEvidence` les tables remplacent la `DeviceAlertEvents` table dans le schéma Microsoft Defender pour point de terminaison. Pour plus d’informations, consultez [la table Map DeviceAlertEvents](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde).

Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

La `DeviceAlertEvents` table du schéma [de chasse avancé](advanced-hunting-overview.md) contient des informations sur les alertes dans Microsoft 365 Defender. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tables du schéma de chasse avancé, consultez [la référence du schéma de chasse avancé](advanced-hunting-schema-reference.md).

|Nom de colonne|Type de données|Description|
|---|---|---|
|`AlertId`|string|Identificateur unique de l’alerte|
|`Timestamp`|DateHeure|Date et heure d’enregistrement de l’événement|
|`DeviceId`|string|Identificateur unique de l’appareil dans le service|
|`DeviceName`|chaîne|Nom de domaine complet (FQDN) de l’appareil|
|`Severity`|string|Indique l’impact potentiel (élevé, moyen ou faible) de l’indicateur de menace ou de la violation identifié(e) par l’alerte|
|`Category`|string|Type d’indicateur de menace ou d’activité de violation identifié par l’alerte|
|`Title`|string|Titre de l'alerte|
|`FileName`|string|Nom du fichier auquel l’action enregistrée a été appliquée|
|`SHA1`|string|SHA-1 du fichier auquel l’action enregistrée a été appliquée|
|`RemoteUrl`|string|URL ou nom de domaine complet (FQDN) à laquelle/auquel la connexion était en cours|
|`RemoteIP`|string|Adresse IP à laquelle la connexion était en cours|
|`AttackTechniques`|string|MITRE ATT&techniques CK associées à l’activité qui a déclenché l’alerte|
|`ReportId`|long|Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée avec les `DeviceName` `Timestamp` colonnes|
|`Table`|string|Table qui contient les détails de l’événement|

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
