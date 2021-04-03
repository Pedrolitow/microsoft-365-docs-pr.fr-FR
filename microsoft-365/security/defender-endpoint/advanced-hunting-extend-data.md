---
title: Étendre la couverture de recherche avancée avec les bons paramètres
description: Vérifier les paramètres d’audit sur les appareils Windows et d’autres paramètres pour vous assurer que vous obtenez les données les plus complètes dans le cadre d’un recherche avancée
keywords: advanced hunting, incident, pivot, entity, audit settings, user account management, security group management, threat hunting, cyber threat hunting, search, query, telemetry, mdatp, Microsoft Defender ATP, Microsoft Defender for Endpoint, Windows Defender, Windows Defender ATP, Windows Defender Advanced Threat Protection
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
ms.date: 10/10/2020
ms.technology: mde
ms.openlocfilehash: ea2524cb214d3cf7c784162a472722727cf0d57c
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51500614"
---
# <a name="extend-advanced-hunting-coverage-with-the-right-settings"></a>Étendre la couverture de recherche avancée avec les bons paramètres

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[La recherche avancée](advanced-hunting-overview.md) repose sur des données provenant de l’ensemble de votre organisation. Pour obtenir les données les plus complètes possibles, assurez-vous que vous avez les paramètres corrects dans les sources de données correspondantes.

## <a name="advanced-security-auditing-on-windows-devices"></a>Audit de sécurité avancée sur les appareils Windows

Activer ces paramètres d’audit avancés pour vous assurer que vous obtenez des données sur les activités sur vos appareils, notamment la gestion des comptes local, la gestion des groupes de sécurité locaux et la création de services.

Data | Description | Table schema | Procédure de configuration
-|-|-|-
Gestion des comptes | Événements capturés en tant que différentes valeurs indiquant la création, la suppression et d’autres activités liées `ActionType` au compte local | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Déployer une stratégie d’audit de sécurité avancée : [auditer la gestion des comptes d’utilisateurs](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-user-account-management)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing)
Gestion des groupes de sécurité | Événements capturés en tant que différentes valeurs indiquant la création d’un groupe de `ActionType` sécurité local et d’autres activités de gestion des groupes locaux | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Déployer une stratégie d’audit de sécurité avancée : [auditer la gestion des groupes de sécurité](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-security-group-management)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing)
Installation du service | Événements capturés `ActionType` avec la valeur , indiquant `ServiceInstalled` qu’un service a été créé | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Déployer une stratégie d’audit de sécurité avancée : [auditer l’extension du système de sécurité](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-security-system-extension)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing)

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](overview-custom-detections.md)
