---
title: Utiliser des entités nommées dans les stratégies DLP
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
ms.openlocfilehash: 108b21e7c5a6708a01a712dcd44788f489df0e73
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971580"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies"></a>Utiliser des entités nommées dans vos stratégies de protection contre la perte de données

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Lisez [en savoir plus sur les entités nommées](named-entities-learn.md) avant de commencer à les utiliser.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="skusubscriptions-licensing"></a>Licences SKU/abonnements

Pour plus d’informations sur les licences, consultez [la description du service](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>Autorisations

Le compte que vous utilisez pour créer et modifier des stratégies de protection contre la perte de données (DLP) doit disposer des autorisations du rôle **Gestion de la conformité DLP** . Pour plus d’informations, consultez [Donner aux utilisateurs l’accès au Centre de conformité Office 365](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>Emplacements pris en charge

Vous pouvez utiliser des SIT d’entité nommées et des stratégies améliorées pour détecter et protéger les éléments sensibles à ces emplacements :

- Sites SharePoint
- Les comptes OneDrive
- conversation et messages de canal Teams
- Appareils (Windows 10 et 11 appareils de point de terminaison)
- Les boîtes aux lettres Exchange

Les SIT d’entité nommée et les stratégies améliorées ne sont pas pris en charge pour :

- Référentiels locaux
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>Créer et modifier des stratégies améliorées

Pour créer ou modifier une stratégie DLP, utilisez les procédures de [création, de test et d’optimisation d’une stratégie DLP](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>Charges de travail et services qui prennent en charge les entités nommées

- **Microsoft 365 eDiscovery prend en** charge l’utilisation d’entités nommées dans les services Substrate.
- **Microsoft Defender for Cloud Apps** prend en charge l’utilisation d’entités nommées dans les stratégies Defender pour le cloud Apps dans le portail des applications Defender pour le cloud.
- **Insider Risk Management** prend en charge l’utilisation d’entités nommées dans les services Substrate.
- **Gestion des enregistrements** prend en charge l’utilisation d’entités nommées.
- **Exact Data Match Sensitive Information Types** prend en charge l’utilisation d’entités nommées.
<!--- **Communication Compliance** doesn't support the use of named entities in Exchange transport rules and data-at-rest.
- **Microsoft Information Governance** (MIG) doesn't support the use of named entities in Exchange transport rules and data-at-rest.-->
 
### <a name="unified-dlp"></a>DLP unifiée

|Charge de travail/services  |Prise en charge des entités nommées  |
|---------|---------|
|Office conseil de stratégie des clients Win32    |Non pris en charge  |
|Office conseil de stratégie des clients WAC    |Pris en charge         |
|Conseil de stratégie OWA     |Non pris en charge         |
|Outlook conseil de stratégie     |Non pris en charge |
|Points de terminaison (Windows 10 et 11 appareils)     |Pris en charge  |
|règles de transport Exchange     |Pris en charge |
|OneDrive Entreprise données au repos     |Pris en charge         |
|SharePoint les données au repos en ligne     |Pris en charge         |
|Teams données au repos     |Pris en charge         |
|Données au repos des messages électroniques     |Prise en charge pour les locataires avec le plan de service de confidentialité         |
|Microsoft Defender for Cloud Apps     |Pris en charge         |

### <a name="autolabeling"></a>Étiquetage automatique

|Charge de travail/services |Prise en charge des entités nommées  |
|---------|---------|
|Office clients Win32 hors connexion   |Pris en charge, l’utilisateur doit sélectionner l’étiquette et appliquer manuellement |
|Clients Win32 en ligne Office en ligne|Pris en charge avec l’ancien schéma de confiance |
|Outlook en ligne   |Pris en charge avec l’ancien schéma de confiance  |
|Office client WAC     |Pris en charge |
|OWA     |Pris en charge |
|transport Exchange     |Pris en charge |
|OneDrive Entreprise données au repos     |Pris en charge |
|SharePoint les données au repos en ligne|Pris en charge|
|Scanneur Azure Information Protection (AIP)|non pris en charge|

## <a name="known-issues"></a>Problèmes détectés

|Problème  |Impact  |
|---------|---------|
|Conseils de stratégie DLP (clients OWA, Outlook, Office Win32)     |   Les conseils de stratégie avec la condition d’entité entraînent « aucune correspondance »      |
| Prise en charge de la langue asiatique pour le nom de la personne (chinois, japonais, coréen)    | Entités nommées prises en charge pour le jeu de caractères basé sur le latin uniquement (autrement dit, kanji n’est pas pris en charge) pour le nom de la personne        |
|Référentiels locaux    | Non pris en charge en tant que charge de travail|
|Power BI (préversion) | Non pris en charge

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="best-practices-for-using-named-entity-sits"></a>Meilleures pratiques pour l’utilisation de SIT d’entité nommée

Voici quelques pratiques que vous pouvez utiliser lorsque vous créez ou modifiez une stratégie qui utilise une entité nommée SIT.

- Utilisez des nombres d’instances faibles (trois à cinq) lorsque vous recherchez des données qui se trouvent dans une feuille de calcul et que le mot clé requis par le SIT pour ces données se trouve uniquement dans l’en-tête de colonne. Par exemple, supposons que vous recherchez des numéros de sécurité sociale des États-Unis et que le mot clé `Social Security Number` se trouve uniquement dans l’en-tête de colonne. Étant donné que les valeurs (la preuve corroborante) se trouve dans les cellules ci-dessous, il est probable que seules les premières instances soient suffisamment proches du mot clé pour être détectées.  

- Si vous utilisez une entité nommée SIT, comme Tous les noms complets, pour vous aider à trouver des numéros de sécurité sociale des États-Unis, utilisez des nombres d’instances plus importants, tels que 10 ou 50. Ensuite, lorsque les noms de personnes et les SSN sont détectés ensemble, vous êtes plus susceptible d’obtenir de vrais positifs.

- Vous pouvez utiliser [des simulations d’étiquetage automatique](apply-sensitivity-label-automatically.md#learn-about-simulation-mode) pour tester la précision des SIT d’entité nommée. Exécutez une simulation à l’aide d’une entité nommée SIT pour voir quels éléments correspondent à la stratégie. Avec ces informations, vous pouvez affiner la précision en ajustant le nombre d’instances et les niveaux de confiance dans vos stratégies personnalisées ou les conditions de modèle améliorées. Vous pouvez itérer des simulations jusqu’à ce que la précision soit à l’endroit souhaité, avant de déployer une stratégie DLP ou d’étiquetage automatique contenant des entités nommées en production. Voici une vue d’ensemble du flux :

1. Identifiez le SIT ou la combinaison de SIT que vous souhaitez tester en mode simulation, personnalisé ou cloné et modifié.
1. Identifiez ou créez une étiquette de confidentialité à appliquer lorsque la stratégie d’étiquetage automatique trouve une correspondance dans Exchange, des sites SharePoint ou des comptes OneDrive.
1. Créer une stratégie d’étiquetage automatique de confidentialité qui utilise le SIT de l’étape 1 et avec les mêmes conditions et exceptions que celle qui sera utilisée dans votre stratégie DLP
1. Exécuter la simulation de stratégie
1. Afficher les résultats
1. Paramétrez le SIT ou la stratégie, ainsi que le nombre d’instances et les niveaux de confiance pour réduire les faux positifs.
1. Répétez l’opération jusqu’à obtenir les résultats de précision souhaités.


## <a name="for-further-information"></a>Pour plus d’informations
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Découvrez les entités nommées](named-entities-learn.md).
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
