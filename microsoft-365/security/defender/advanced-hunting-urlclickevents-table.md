---
title: Table UrlClickEvents dans le schéma de chasse avancé
description: Découvrez comment rechercher des campagnes de hameçonnage et des clics suspects à l’aide de la table UrlClickEvents dans le schéma de chasse avancé.
keywords: repérage avancé, chasse aux menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, UrlClickEvents, SafeLinks, hameçonnage, programmes malveillants, clics malveillants, outlook, équipes, e-mail, office365
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: bb7ee0397c79cc64c6f7396b6c3ca9450c8306f2
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2022
ms.locfileid: "66991681"
---
# <a name="urlclickevents"></a>UrlClickEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour Office 365


Le `UrlClickEvents` tableau du schéma de chasse avancé contient des informations sur les clics [liens fiables](../office-365-security/safe-links.md) à partir de messages électroniques, de Microsoft Teams et d’applications Office 365 dans les applications de bureau, mobiles et web prises en charge. 

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure auxquelles l’utilisateur a cliqué sur le lien |
| `Url` | `string` | URL complète sur laquelle l’utilisateur a cliqué |
| `ActionType` | `string` | Indique si le clic a été autorisé ou bloqué par des liens sécurisés ou bloqué en raison d’une stratégie de locataire, par exemple, à partir de la liste des blocs autorisés du locataire|
| `AccountUpn` | `string` | Nom d’utilisateur principal du compte qui a cliqué sur le lien|
| `Workload` | `string` | Application à partir de laquelle l’utilisateur a cliqué sur le lien, avec les valeurs Email, Office et Teams|
| `NetworkMessageId` | `string` | Identificateur unique de l’e-mail contenant le lien cliqué, généré par Microsoft 365|
| `IPAddress` | `string` | Adresse IP publique de l’appareil à partir duquel l’utilisateur a cliqué sur le lien|
| `ThreatTypes` | `string` | Verdict au moment du clic, qui indique si l’URL a provoqué des programmes malveillants, des hameçonnages ou d’autres menaces|
| `DetectionMethods` | `string` | Technologie de détection utilisée pour identifier la menace au moment du clic|
| `IsClickedThrough` | `bool` | Indique si l’utilisateur a pu cliquer sur l’URL d’origine ou s’il n’a pas été autorisé|
| `UrlChain` | `string` | Pour les scénarios impliquant des redirections, il inclut les URL présentes dans la chaîne de redirection|
| `ReportId` | `string` | Il s’agit de l’identificateur unique d’un événement click. Notez que pour les scénarios de clic, l’ID de rapport aurait la même valeur. Par conséquent, il doit être utilisé pour mettre en corrélation un événement de clic.|

Vous pouvez essayer cet exemple de requête qui utilise la `UrlClickEvents` table pour retourner une liste de liens où un utilisateur a été autorisé à continuer : 

```kusto
// Search for malicious links where user was allowed to proceed through
UrlClickEvents
| where ActionType == "ClickAllowed" or IsClickedThrough !="0"
| where ThreatTypes has "Phish"
| summarize by ReportId, IsClickedThrough, AccountUpn, NetworkMessageId, ThreatTypes, Timestamp
```

## <a name="related-topics"></a>Sujets associés

- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Liens sécurisés dans Microsoft Defender pour Office 365](../office-365-security/safe-links.md)
- [Prendre des mesures sur les résultats de la requête de chasse avancée](advanced-hunting-take-action.md)