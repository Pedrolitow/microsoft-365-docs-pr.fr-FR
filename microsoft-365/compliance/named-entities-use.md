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
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Utilisez ces procédures pour tirer parti d’entités nommées dans vos stratégies de protection contre la perte de données
ms.openlocfilehash: 9b3a8899ef4b64c682289e29df19648a00d4f048
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665159"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies-preview"></a>Utiliser des entités nommées dans vos politiques de prévention des pertes de données (aperçu)

> [!IMPORTANT]
> La fonctionnalité d’entités nommées est déployée et s’affiche dans votre locataire lorsqu’elle est disponible pour vous. Recherchez-les dans l’Explorateur de contenu et dans le flux de création de stratégie de protection contre la perte de données (DLP). 

Lisez [en savoir plus sur les entités nommées (préversion)](named-entities-learn.md) avant de commencer à les utiliser.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="skusubscriptions-licensing"></a>Licences SKU/abonnements

Vous devez disposer de l’un de ces abonnements

- Information Protection et gouvernance
- Microsoft 365 E5 Conformité
- Office 365 E5
- Microsoft 365 E5

Pour plus d’informations sur les licences, consultez [la description du service](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>Autorisations

Le compte que vous utilisez pour créer et modifier des stratégies de protection contre la perte de données (DLP) doit disposer des autorisations du rôle **Gestion de la conformité DLP** . Pour plus d’informations, consultez [Donner aux utilisateurs l’accès au Centre de conformité Office 365](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>Emplacements pris en charge

Vous pouvez utiliser des SIT d’entité nommées et des stratégies améliorées pour détecter et protéger les éléments sensibles à ces emplacements :

- Sites SharePoint
- Les comptes OneDrive
- conversation et messages de canal Teams
- Appareils (Windows 10 périphériques de point de terminaison)

Les SIT d’entité nommée et les stratégies améliorées ne sont pas pris en charge pour :


- Référentiels locaux
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>Créer et modifier des stratégies améliorées

Pour créer ou modifier une stratégie DLP, utilisez les procédures de [création, de test et d’optimisation d’une stratégie DLP](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>Charges de travail et services qui prennent en charge les entités nommées


- **Microsoft 3655 eDiscovery** prend en charge l’utilisation d’entités nommées dans les services Substrate.
- **Microsoft Defender for Cloud Apps** prend en charge l’utilisation d’entités nommées dans les stratégies Defender pour le cloud Apps.
- **Insider Risk Management** prend en charge l’utilisation d’entités nommées dans les services Substrate.
<!--- **Communication Compliance** doesn't support the use of named entities in Exchange transport rules and data-at-rest.
- **Microsoft Information Governance** (MIG) doesn't support the use of named entities in Exchange transport rules and data-at-rest.-->
 
### <a name="unified-dlp"></a>DLP unifiée

|Charge de travail/services  |Prise en charge de la préversion publique pour les entités nommées  |
|---------|---------|
|Office conseil de stratégie des clients Win32    |non pris en charge  |
|Office conseil de stratégie des clients WAC    |Pris en charge         |
|Conseil de stratégie OWA     |non pris en charge         |
|Outlook conseil de stratégie     |non pris en charge |
|Points de terminaison (appareils Windows 10)     |Pris en charge  |
|règles de transport Exchange     |non pris en charge |
|OneDrive Entreprise données au repos     |Pris en charge         |
|SharePoint les données au repos en ligne     |Pris en charge         |
|Teams données au repos     |Pris en charge         |
|Données au repos des messages électroniques     |non pris en charge         |
|Microsoft Defender for Cloud Apps     |Pris en charge         |

### <a name="autolabeling"></a>Étiquetage automatique

|Charge de travail/services |Prise en charge de la préversion publique pour les entités nommées  |
|---------|---------|
|Office clients Win32 hors connexion   |pris en charge, l’utilisateur doit sélectionner l’étiquette et appliquer manuellement |
|Clients Win32 en ligne Office en ligne|pris en charge avec l’ancien schéma de confiance |
|Outlook en ligne   |pris en charge avec l’ancien schéma de confiance  |
|Office client WAC     |Pris en charge |
|OWA     |Pris en charge |
|transport Exchange     |non pris en charge |
|OneDrive Entreprise données au repos     |Pris en charge |
|SharePoint les données au repos en ligne|Pris en charge|
|Scanneur Azure Information Protection (AIP)|non pris en charge|

## <a name="known-issues"></a>Problèmes connus

|Problème  |Impact  |
|---------|---------|
|Conseils de stratégie DLP (clients OWA, Outlook, Office Win32)     |   Les conseils de stratégie avec la condition d’entité entraînent « aucune correspondance »      |
| Prise en charge de la langue asiatique pour le nom de la personne (chinois, japonais, coréen)    | Entités nommées prises en charge pour le jeu de caractères basé sur le latin uniquement (autrement dit, kanji n’est pas pris en charge) pour le nom de la personne        |
|Référentiels locaux    | Non pris en charge en tant que charge de travail|

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="for-further-information"></a>Pour plus d’informations
<!-- - [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [Découvrez les entités nommées (préversion).](named-entities-learn.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
