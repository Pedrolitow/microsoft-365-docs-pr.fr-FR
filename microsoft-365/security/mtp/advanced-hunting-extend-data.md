---
title: Étendre la couverture de la chasse avancée avec les paramètres corrects
description: Vérifier les paramètres d’audit sur les appareils Windows et d’autres paramètres pour vous aider à obtenir les données les plus complètes dans la recherche avancée
keywords: chasse avancée, incident, tableau croisé dynamique, entité, paramètres d’audit, gestion des comptes d’utilisateur, gestion des groupes de sécurité, recherche des menaces, recherche dans les menaces informatiques, recherche, requête, télémétrie, Microsoft 365, protection contre les menaces de Microsoft
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.openlocfilehash: 223ef56d7d0d61cd4ae8d90bce974d4086227286
ms.sourcegitcommit: de600339b08951d6dd3933288a8da2327a4b6ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48430379"
---
# <a name="extend-advanced-hunting-coverage-with-the-right-settings"></a>Étendre la couverture de la chasse avancée avec les paramètres corrects

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

La [chasse avancée](advanced-hunting-overview.md) repose sur les données provenant de différentes sources, notamment vos appareils, vos espaces de travail Office 365, Azure ad et Azure ATP. Pour obtenir les données les plus complètes possible, vérifiez que vous disposez des paramètres corrects dans les sources de données correspondantes.

## <a name="advanced-security-auditing-on-windows-devices"></a>Audit de sécurité avancé sur les appareils Windows
Activez ces paramètres d’audit avancés pour vous assurer que vous obtenez des données sur les activités de vos appareils, notamment la gestion des comptes locaux, la gestion des groupes de sécurité locaux et la création de services.

| Data | Description | Table de schéma | Procédure de configuration |
| --- | --- | --- | --- |
| Gestion des comptes | Événements capturés sous la forme de différentes `ActionType` valeurs indiquant la création, la suppression et d’autres activités liées au compte local | [DeviceEvents](advanced-hunting-deviceevents-table.md) | -Déployer une stratégie d’audit de sécurité avancée : [audit User Account Management](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-user-account-management)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Gestion des groupes de sécurité | Événements capturés sous la forme de différentes `ActionType` valeurs indiquant la création du groupe de sécurité local et d’autres activités de gestion des groupes locaux | [DeviceEvents](advanced-hunting-deviceevents-table.md) | -Déployer une stratégie d’audit de sécurité avancée : [gestion des groupes de sécurité d’audit](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-security-group-management)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Installation de service | Événements capturés avec la `ActionType` valeur `ServiceInstalled` , indiquant qu’un service a été créé | [DeviceEvents](advanced-hunting-deviceevents-table.md) | -Déployer une stratégie d’audit de sécurité avancée : [audit Security System extension](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-security-system-extension)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing) |

## <a name="azure-atp-sensor-on-the-domain-controller"></a>Capteur DAV Azure sur le contrôleur de domaine
Si vous exécutez Active Directory sur site, vous devez installer le capteur DAV Azure sur le contrôleur de domaine pour obtenir des données pour Azure ATP. Une fois installée et correctement configurée, ces données sont également intégrées dans Azure ATP et fournissent une image plus holistique des informations d’identité et des événements de votre réseau. Ces données améliorent également la capacité d’Azure ATP à générer des alertes pertinentes qui sont également couvertes par la chasse avancée. 

| Data | Description | Table de schéma | Procédure de configuration |
| --- | --- | --- | --- |
| Contrôleur de domaine | Données provenant d’Active Directory en local envoyées à Azure ATP, enrichiant les informations d’identité, telles que les détails du compte, l’activité d’ouverture de session et les requêtes Active Directory | Plusieurs tables, y compris [IdentityInfo](advanced-hunting-identityinfo-table.md), [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)et [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)  | - [Installer le capteur ATP Azure](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step4)<br>- [Activer les événements Windows pertinents](https://docs.microsoft.com/azure-advanced-threat-protection/configure-event-collection) |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
