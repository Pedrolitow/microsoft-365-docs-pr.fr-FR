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
ms.openlocfilehash: 82faff2599cd61fa1a4deb3129e1e6780d3f529c
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48842475"
---
# <a name="extend-advanced-hunting-coverage-with-the-right-settings"></a>Étendre la couverture de la chasse avancée avec les paramètres corrects

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La recherche [avancée](advanced-hunting-overview.md) repose sur les données provenant de différentes sources, notamment vos appareils, vos espaces de travail Office 365, Azure ad et Microsoft Defender pour l’identité. Pour obtenir les données les plus complètes possible, vérifiez que vous disposez des paramètres corrects dans les sources de données correspondantes.

## <a name="advanced-security-auditing-on-windows-devices"></a>Audit de sécurité avancé sur les appareils Windows
Activez ces paramètres d’audit avancés pour vous assurer que vous obtenez des données sur les activités de vos appareils, notamment la gestion des comptes locaux, la gestion des groupes de sécurité locaux et la création de services.

| Data | Description | Table de schéma | Procédure de configuration |
| --- | --- | --- | --- |
| Gestion des comptes | Événements capturés sous la forme de différentes `ActionType` valeurs indiquant la création, la suppression et d’autres activités liées au compte local | [DeviceEvents](advanced-hunting-deviceevents-table.md) | -Déployer une stratégie d’audit de sécurité avancée : [audit User Account Management](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-user-account-management)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Gestion des groupes de sécurité | Événements capturés sous la forme de différentes `ActionType` valeurs indiquant la création du groupe de sécurité local et d’autres activités de gestion des groupes locaux | [DeviceEvents](advanced-hunting-deviceevents-table.md) | -Déployer une stratégie d’audit de sécurité avancée : [gestion des groupes de sécurité d’audit](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-security-group-management)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Installation de service | Événements capturés avec la `ActionType` valeur `ServiceInstalled` , indiquant qu’un service a été créé | [DeviceEvents](advanced-hunting-deviceevents-table.md) | -Déployer une stratégie d’audit de sécurité avancée : [audit Security System extension](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-security-system-extension)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing) |

## <a name="microsoft-defender-for-identity-sensor-on-the-domain-controller"></a>Microsoft Defender pour le capteur d’identité sur le contrôleur de domaine
Si vous utilisez Active Directory en local, vous devez installer le capteur de Microsoft Defender pour l’identité sur le contrôleur de domaine pour obtenir des données pour l’identité de Microsoft Defender. Lorsqu’elles sont installées et correctement configurées, ces données alimentent également la chasse avancée par le biais de Microsoft Defender pour l’identité et fournissent une image plus holistique des informations d’identité et des événements dans votre réseau. Ces données améliorent également la capacité de Microsoft Defender pour l’identité à générer des alertes pertinentes qui sont également couvertes par la chasse avancée. 

| Data | Description | Table de schéma | Procédure de configuration |
| --- | --- | --- | --- |
| Contrôleur de domaine | Données provenant d’Active Directory en local envoyées à Microsoft Defender pour obtenir des informations d’identité, enrichiant les informations d’identité, telles que les détails du compte, l’activité d’ouverture de session et les requêtes Active Directory | Plusieurs tables, y compris [IdentityInfo](advanced-hunting-identityinfo-table.md), [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)et [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)  | - [Installer Microsoft Defender pour le capteur d’identité](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step4)<br>- [Activer les événements Windows pertinents](https://docs.microsoft.com/azure-advanced-threat-protection/configure-event-collection) |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
