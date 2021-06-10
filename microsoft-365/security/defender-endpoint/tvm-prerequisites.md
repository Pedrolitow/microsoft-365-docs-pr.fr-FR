---
title: 'Conditions préalables & autorisations : Gestion des menaces et des vulnérabilités'
description: Avant de commencer à utiliser Gestion des menaces et des vulnérabilités, assurez-vous que vous avez les configurations et autorisations pertinentes.
keywords: conditions préalables & gestion des vulnérabilités sur les autorisations de Gestion des menaces et des vulnérabilités, conditions préalables pour les autorisations d’Gestion des menaces et des vulnérabilités, conditions préalables pour les autorisations TVM de Microsoft Defender pour les points de terminaison, gestion des vulnérabilités
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
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c0544665ea4e9b1ceafa645a2dcc96a224b0c242
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52843949"
---
# <a name="prerequisites--permissions---threat-and-vulnerability-management"></a>Conditions préalables & autorisations : Gestion des menaces et des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Menaces et gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

Assurez-vous que vos appareils :

- Sont intégrés à Microsoft Defender pour le point de terminaison
- Exécuter les [systèmes d’exploitation et les plateformes pris en charge](tvm-supported-os.md)
- Installez et déployez les mises à jour obligatoires suivantes dans votre réseau pour augmenter les taux de détection de l’évaluation des vulnérabilités :

> Version | Numéro et lien de la mise à jour de sécurité de la KB
> :---|:---
> Windows 10 Version 1709 | [KB4493441 et](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441) [KB 4516071](https://support.microsoft.com/help/4516071/windows-10-update-kb4516071)
> Windows 10 Version 1803 | [KB4493464](https://support.microsoft.com/help/4493464) et [KB 4516045](https://support.microsoft.com/help/4516045/windows-10-update-kb4516045)
> Windows 10 Version 1809 | [KB 4516077](https://support.microsoft.com/help/4516077/windows-10-update-kb4516077)
> Windows 10 Version 1903 | [KB 4512941](https://support.microsoft.com/help/4512941/windows-10-update-kb4512941)

- Sont intégrés à [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) et [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) pour vous aider à résoudre les menaces trouvées par les Gestion des menaces et des vulnérabilités. Si vous utilisez Configuration Manager, mettez à jour votre console vers la dernière version.
    - **Remarque**: si la connexion Intune est activée, vous pouvez créer une tâche de sécurité Intune lors de la création d’une demande de correction. Cette option n’apparaît pas si la connexion n’est pas définie.
- Avoir au moins une recommandation de sécurité qui peut être vue dans la page de l’appareil
- Sont marqués ou marqués comme co-gérés

## <a name="relevant-permission-options"></a>Options d’autorisation pertinentes

1. Connectez-vous Centre de sécurité Microsoft Defender compte avec un rôle d’administrateur de sécurité ou d’administrateur général attribué.
2. Dans le volet de navigation, sélectionnez **Paramètres > rôles.**

Pour plus d’informations, voir [Créer et gérer des rôles pour le contrôle d’accès basé sur les rôles](user-roles.md)

### <a name="view-data"></a>Afficher les données

- **Opérations de sécurité** : afficher toutes les données des opérations de sécurité dans le portail
- **Menaces et gestion des vulnérabilités** : afficher Gestion des menaces et des vulnérabilités données de sécurité dans le portail

### <a name="active-remediation-actions"></a>Actions de correction actives

- **Opérations de sécurité** : prendre des mesures de réponse, approuver ou ignorer les actions de correction en attente, gérer les listes autorisées/bloquées pour l’automatisation et les indicateurs
- **Menaces et gestion des vulnérabilités - Gestion des exceptions** : créer des exceptions et gérer les exceptions actives
- **Threat and gestion des vulnérabilités - Remediation handling** - Submit new remediation requests, create tickets, and manage existing remediation activities

Pour plus d’informations, voir [les options d’autorisation RBAC](user-roles.md#permission-options)

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble gestion des vulnérabilités menaces et gestion des vulnérabilités menaces](next-gen-threat-and-vuln-mgt.md)
- [Plateformes et systèmes d’exploitation pris en charge](tvm-supported-os.md)
- [Affecter une valeur aux appareils](tvm-assign-device-value.md)
- [Tableau de bord des menaces gestion des vulnérabilités de sécurité](tvm-dashboard-insights.md)

