---
title: Utiliser des entités nommées dans vos politiques de prévention des pertes de données (aperçu)
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
description: Utilisez ces procédures pour tirer parti des entités nommées dans vos stratégies de protection contre la perte de données
ms.openlocfilehash: eec82365e6fb4af4b6ca23896addd491637ec022
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61110810"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies-preview"></a>Utiliser des entités nommées dans vos politiques de prévention des pertes de données (aperçu)

> [!IMPORTANT]
> La fonctionnalité entités nommées est en cours de déploiement et apparaît dans votre client lorsqu’elle est disponible pour vous. Recherchez-les dans l’Explorateur de contenu et dans le flux de authoring de stratégie de protection contre la perte de données (DLP). 

Lisez la [lecture en savoir plus sur les entités nommées (prévisualisation)](named-entities-learn.md) avant de commencer à les utiliser.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="skusubscriptions-licensing"></a>Licences SKU/abonnements

Vous devez avoir l’un de ces abonnements

- Protection et gouvernance des informations
- Microsoft 365 E5 Conformité
- Office 365 E5
- Microsoft 365 E5

Pour plus d’informations sur les licences, voir [la description du service.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer)

### <a name="permissions"></a>Autorisations

Le compte que vous utilisez pour créer et modifier des stratégies de protection contre la perte de données (DLP) doit avoir les autorisations du rôle Gestion de la conformité **DLP.** Pour plus d’informations, voir [Give users access to the Office 365 Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>Emplacements pris en charge

Vous pouvez utiliser des sits d’entité nommée et des stratégies améliorées pour détecter et protéger les éléments sensibles à ces emplacements :

- Sites SharePoint
- Les comptes OneDrive
- conversation et messages de canal Teams

Les sits d’entité nommée et les stratégies améliorées ne sont pas pris en charge pour :

- Appareils (Windows 10 de point de terminaison)
- Référentiels locaux

## <a name="create-and-edit-enhanced-policies"></a>Créer et modifier des stratégies améliorées

Pour créer ou modifier une stratégie DLP, utilisez les procédures dans Créer, tester et [régler une stratégie DLP.](create-test-tune-dlp-policy.md)

## <a name="workloads-and-services-that-support-named-entities"></a>Charges de travail et services qui la prise en charge des entités nommées


- **Microsoft 3655 eDiscovery** prend en charge l’utilisation d’entités nommées dans les services substrat.
- **Microsoft Defender pour les applications cloud prend** en charge l’utilisation d’entités nommées dans les stratégies de Defender for Cloud Apps.
- **La gestion des risques internes prend** en charge l’utilisation d’entités nommées dans les services substrat.
- **La conformité des** communications ne prend pas en charge l’utilisation d’entités nommées Exchange règles de transport et de données au repos.
- **Microsoft Information Governance** (MIG) ne prend pas en charge l’utilisation d’entités nommées dans Exchange règles de transport et de données au repos.
 
### <a name="unified-dlp"></a>DLP unifiée

|Charge de travail/services  |Prise en charge de la prévisualisation publique pour les entités nommées  |
|---------|---------|
|Office conseil de stratégie des clients Win32    |non pris en charge  |
|Office conseil de stratégie des clients WAC    |Pris en charge         |
|OWA conseil de stratégie     |non pris en charge         |
|Outlook conseil de stratégie     |non pris en charge |
|Points de terminaison (Windows 10 périphériques)     |non pris en charge  |
|Exchange transport     |non pris en charge |
|OneDrive Entreprise données au repos     |Pris en charge         |
|SharePoint données au repos en ligne     |Pris en charge         |
|Teams données au repos     |Pris en charge         |
|Données au repos des messages électroniques     |non pris en charge         |
|Microsoft Defender for Cloud Apps     |Pris en charge         |

### <a name="autolabeling"></a>Autolabeling

|Charge de travail/services |Prise en charge de la prévisualisation publique pour les entités nommées  |
|---------|---------|
|Office clients Win32 hors connexion   |pris en charge, l’utilisateur doit sélectionner une étiquette et appliquer manuellement |
|Online Office clients Win32 en ligne|pris en charge avec l’ancien schéma de confiance |
|Outlook en ligne   |pris en charge avec l’ancien schéma de confiance  |
|Office client WAC     |Pris en charge |
|OWA     |Pris en charge |
|Exchange transport     |non pris en charge |
|OneDrive Entreprise données au repos     |Pris en charge |
|SharePoint données au repos en ligne|Pris en charge|
|Scanneur Azure Information Protection (AIP)|non pris en charge|

## <a name="known-issues"></a>Problèmes connus

|Problème  |Impact  |
|---------|---------|
|Conseils de stratégie DLP (OWA, Outlook, Office clients Win32)     |   Les conseils de stratégie avec condition d’entité entraînent l’absence de correspondance      |
| Prise en charge des langues asiatiques pour le nom de la personne (chinois, japonais, coréen)    | Entités nommées uniquement prise en charge pour le jeu de caractères en caractères latins (autrement dit, kanji non pris en charge) pour le nom de la personne        |
|Charge de travail des appareils (point de terminaison)     | Non pris en charge en tant que charge de travail : la stratégie de authoring avec des entités nommées n’est pas autorisée        |
|Référentiels locaux    | Non pris en charge en tant que charge de travail|

## <a name="for-further-information"></a>Pour plus d’informations
<!-- - [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [En savoir plus sur les entités nommées (prévisualisation).](named-entities-learn.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
