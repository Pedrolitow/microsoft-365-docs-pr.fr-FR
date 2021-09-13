---
title: Repérer des appareils exposés
description: Découvrez comment Gestion des menaces et des vulnérabilités peuvent être utilisés pour aider les administrateurs de sécurité, les administrateurs informatiques et SecOps à collaborer.
keywords: Scénarios Microsoft Defender pour endpoint-tvm, Microsoft Defender pour le point de terminaison, tvm, scénarios tvm, réduire l’exposition aux vulnérabilités & menaces, réduire les menaces et vulnérabilités, améliorer la configuration de la sécurité, augmenter le Degré de sécurisation Microsoft pour les appareils, augmenter le niveau de sécurité Microsoft pour les appareils, augmenter la vulnérabilité & Degré de sécurité Microsoft pour les appareils, Degré de sécurisation Microsoft pour les appareils, score d’exposition, contrôles de sécurité
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: bec319f840728599f01680c32561bf3998d59381
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59164817"
---
# <a name="hunt-for-exposed-devices---threat-and-vulnerability-management"></a>Recherche des appareils exposés - Gestion des menaces et des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Menaces et gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="use-advanced-hunting-to-find-devices-with-vulnerabilities"></a>Utiliser le recherche avancée pour rechercher des appareils avec des vulnérabilités

Le repérage avancé est un outil de repérage de menaces basé sur des requêtes qui vous permet d’explorer jusqu’à 30 jours de données brutes. Vous pouvez inspecter de manière proactive les événements de votre réseau pour localiser les indicateurs et entités de menace. L’accès flexible aux données permet un recherche sans contraintes pour les menaces connues et potentielles. [En savoir plus sur le chasse avancée](advanced-hunting-overview.md)

### <a name="schema-tables"></a>Tableaux de schéma

- [DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md) : inventaire des logiciels installés sur les appareils, y compris les informations de version et l’état de fin de prise en charge.

- [DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md) : vulnérabilités logicielles trouvées sur les appareils et liste des mises à jour de sécurité disponibles qui s’adressent à chaque vulnérabilité.

- [DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md) : base de connaissances sur les vulnérabilités divulguées publiquement, notamment si le code d’exploitation est disponible publiquement.

- [DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md) : événements d’évaluation des menaces gestion des vulnérabilités, indiquant l’état de différentes configurations de sécurité sur les appareils.

- [DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) : base de connaissances sur les différentes configurations de sécurité utilisées par la gestion des menaces & des vulnérabilités pour évaluer les appareils ; inclut des mappages à différentes normes et critères

## <a name="check-which-devices-are-involved-in-high-severity-alerts"></a>Vérifier les appareils impliqués dans les alertes de gravité élevée

1. Go to **Hunting**  >  **Advanced hunting** from the left-hand navigation pane of the Microsoft 365 Defender portal.

2. Faites défiler vers le bas jusqu’aux schémas de recherche avancée TVM pour vous familiariser avec les noms des colonnes.

3. Entrez les requêtes suivantes :

```kusto
// Search for devices with High active alerts or Critical CVE public exploit
let DeviceWithHighAlerts = AlertInfo
| where Severity == "High"
| project Timestamp, AlertId, Title, ServiceSource, Severity
| join kind=inner (AlertEvidence | where EntityType == "Machine" | project AlertId, DeviceId, DeviceName) on AlertId
| summarize HighSevAlerts = dcount(AlertId) by DeviceId;
let DeviceWithCriticalCve = DeviceTvmSoftwareVulnerabilities
| join kind=inner(DeviceTvmSoftwareVulnerabilitiesKB) on CveId
| where IsExploitAvailable == 1 and CvssScore >= 7
| summarize NumOfVulnerabilities=dcount(CveId),
DeviceName=any(DeviceName) by DeviceId;
DeviceWithCriticalCve
| join kind=inner DeviceWithHighAlerts on DeviceId
| project DeviceId, DeviceName, NumOfVulnerabilities, HighSevAlerts
```

## <a name="related-topics"></a>Rubriques connexes

- [Vue d’ensemble gestion des vulnérabilités menaces et gestion des vulnérabilités menaces](next-gen-threat-and-vuln-mgt.md)
- [Recommandations de sécurité](tvm-security-recommendation.md)
- [API](next-gen-threat-and-vuln-mgt.md#apis)
- [Configurer l’accès aux données pour Gestion des menaces et des vulnérabilités rôles](user-roles.md#create-roles-and-assign-the-role-to-an-azure-active-directory-group)
- [Vue d’ensemble du repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Toutes les tables de recherche avancées](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference.md)
