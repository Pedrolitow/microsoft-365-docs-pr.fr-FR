---
title: Étendre la couverture de chasse avancée avec les paramètres appropriés
description: Vérifiez les paramètres d’audit sur les appareils Windows et d’autres paramètres pour vous assurer d’obtenir les données les plus complètes dans la recherche avancée
keywords: repérage avancé, incident, tableau croisé dynamique, entité, paramètres d’audit, gestion des comptes d’utilisateur, gestion des groupes de sécurité, repérage des menaces, repérage de cybermenaces, recherche, requête, télémétrie, Microsoft 365, Microsoft 365 Defender
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
- tier2
ms.topic: conceptual
ms.openlocfilehash: 1c2e0ef6b07f746ba88e190807ef914a9948b8f8
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68625410"
---
# <a name="extend-advanced-hunting-coverage-with-the-right-settings"></a>Étendre la couverture de chasse avancée avec les paramètres appropriés

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

[La chasse avancée](advanced-hunting-overview.md) s’appuie sur des données provenant de différentes sources, notamment vos appareils, vos espaces de travail Office 365, Azure AD et Microsoft Defender pour Identity. Pour obtenir les données les plus complètes possibles, assurez-vous que vous disposez des paramètres corrects dans les sources de données correspondantes.

## <a name="advanced-security-auditing-on-windows-devices"></a>Audit de sécurité avancé sur les appareils Windows
Activez ces paramètres d’audit avancés pour vous assurer d’obtenir des données sur les activités sur vos appareils, notamment la gestion des comptes locaux, la gestion des groupes de sécurité locaux et la création de services.

| Data | Description | Table de schémas | Procédure de configuration |
| --- | --- | --- | --- |
| Gestion des comptes | Événements capturés sous forme de différentes `ActionType` valeurs indiquant la création, la suppression et d’autres activités liées au compte locaux | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Déployer une stratégie d’audit de sécurité avancée : [Auditer la gestion des comptes d’utilisateur](/windows/security/threat-protection/auditing/audit-user-account-management)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Gestion des groupes de sécurité | Événements capturés sous forme de différentes `ActionType` valeurs indiquant la création d’un groupe de sécurité local et d’autres activités de gestion de groupe locales | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Déployer une stratégie d’audit de sécurité avancée : [Auditer la gestion des groupes de sécurité](/windows/security/threat-protection/auditing/audit-security-group-management)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Installation du service | Événements capturés avec la `ActionType` valeur `ServiceInstalled`, indiquant qu’un service a été créé | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Déployer une stratégie d’audit de sécurité avancée : [Auditer l’extension du système de sécurité](/windows/security/threat-protection/auditing/audit-security-system-extension)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](/windows/security/threat-protection/auditing/advanced-security-auditing) |

## <a name="microsoft-defender-for-identity-sensor-on-the-domain-controller"></a>capteur Microsoft Defender pour Identity sur le contrôleur de domaine
Si vous exécutez Active Directory localement, vous devez installer le capteur Microsoft Defender pour Identity sur le contrôleur de domaine pour obtenir des données pour Microsoft Defender pour Identity. Une fois installées et correctement configurées, ces données alimentent également la chasse avancée par le biais de Microsoft Defender pour Identity et fournissent une image plus holistique des informations d’identité et des événements dans votre réseau. Ces données améliorent également la capacité des Microsoft Defender pour Identity à générer des alertes pertinentes qui sont également couvertes par la chasse avancée. 

| Data | Description | Table de schémas | Procédure de configuration |
| --- | --- | --- | --- |
| Contrôleur de domaine | Les données de Active Directory local envoyées à Microsoft Defender pour Identity, enrichissant les informations relatives à l’identité, telles que les détails du compte, l’activité d’ouverture de session et les requêtes Active Directory | Plusieurs tables, notamment [IdentityInfo](advanced-hunting-identityinfo-table.md), [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) et [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)  | - [Installer le capteur Microsoft Defender pour Identity](/azure-advanced-threat-protection/install-atp-step4)<br>- [Activer les événements Windows pertinents](/azure-advanced-threat-protection/configure-event-collection) |

>[!NOTE]
>Certaines tables de cet article peuvent ne pas être disponibles dans Microsoft Defender pour point de terminaison. [Activez Microsoft 365 Defender](m365d-enable.md) pour rechercher des menaces à l’aide de sources de données supplémentaires. Vous pouvez déplacer vos flux de travail de chasse avancés de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender en suivant les étapes de migration [des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)