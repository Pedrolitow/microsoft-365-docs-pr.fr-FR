---
title: Repérer des appareils exposés
description: Découvrez comment la gestion des menaces et des vulnérabilités peut être utilisée pour aider les administrateurs de sécurité, les administrateurs informatiques et SecOps à collaborer.
keywords: scénarios mdatp-tvm, mdatp, tvm, tvm scenarios, réduire l’exposition aux vulnérabilités de & de menace, réduire les menaces et vulnérabilités, améliorer la configuration de la sécurité, augmenter le Degré de sécurisation Microsoft pour les appareils, augmenter le niveau de sécurité microsoft & vulnérabilité Microsoft Secure Score pour les appareils, Degré de sécurisation Microsoft pour les appareils, score d’exposition, contrôles de sécurité
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
ms.openlocfilehash: b8e3a80e73d9847837ae0a1542e7d16ee8ae0f29
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51500090"
---
# <a name="hunt-for-exposed-devices---threat-and-vulnerability-management"></a>Recherche des appareils exposés : gestion des menaces et des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="use-advanced-hunting-to-find-devices-with-vulnerabilities"></a>Utiliser le recherche avancée pour rechercher des appareils avec des vulnérabilités

Le repérage avancé est un outil de repérage de menaces basé sur des requêtes qui vous permet d’explorer jusqu’à 30 jours de données brutes. Vous pouvez inspecter de manière proactive les événements de votre réseau pour localiser les indicateurs et entités de menace. L’accès flexible aux données permet un recherche sans contraintes pour les menaces connues et potentielles. [En savoir plus sur le chasse avancée](advanced-hunting-overview.md)

### <a name="schema-tables"></a>Tableaux de schéma

- [DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md) : inventaire des logiciels installés sur les appareils, y compris les informations de version et l’état de fin de prise en charge.

- [DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md) : vulnérabilités logicielles trouvées sur les appareils et liste des mises à jour de sécurité disponibles qui s’adressent à chaque vulnérabilité.

- [DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md) : base de connaissances sur les vulnérabilités divulguées publiquement, notamment si le code d’exploitation est disponible publiquement.

- [DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md) : événements d’évaluation de la gestion des menaces et des vulnérabilités, indiquant l’état de différentes configurations de sécurité sur les appareils.

- [DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) : base de connaissances sur les différentes configurations de sécurité utilisées par la gestion des menaces & des vulnérabilités pour évaluer les appareils ; inclut des mappages à différentes normes et critères

## <a name="check-which-devices-are-involved-in-high-severity-alerts"></a>Vérifier les appareils impliqués dans les alertes de gravité élevée

1. Go to **Advanced hunting** from the left-hand navigation pane of the Microsoft Defender Security Center.

2. Faites défiler vers le bas jusqu’aux schémas de recherche avancée TVM pour vous familiariser avec les noms des colonnes.

3. Entrez les requêtes suivantes :

```kusto
// Search for devices with High active alerts or Critical CVE public exploit
DeviceTvmSoftwareVulnerabilities
| join kind=inner(DeviceTvmSoftwareVulnerabilitiesKB) on CveId
| where IsExploitAvailable == 1 and CvssScore >= 7
| summarize NumOfVulnerabilities=dcount(CveId),
DeviceName=any(DeviceName) by DeviceId
| join kind =inner(DeviceAlertEvents) on DeviceId  
| summarize NumOfVulnerabilities=any(NumOfVulnerabilities),
DeviceName=any(DeviceName) by DeviceId, AlertId
| project DeviceName, NumOfVulnerabilities, AlertId  
| order by NumOfVulnerabilities desc
```

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de la gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Recommandations de sécurité](tvm-security-recommendation.md)
- [API](next-gen-threat-and-vuln-mgt.md#apis)
- [Configurer l’accès aux données pour les rôles de gestion des menaces et des vulnérabilités](user-roles.md#create-roles-and-assign-the-role-to-an-azure-active-directory-group)
- [Vue d’ensemble du repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Toutes les tables de recherche avancées](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference.md)