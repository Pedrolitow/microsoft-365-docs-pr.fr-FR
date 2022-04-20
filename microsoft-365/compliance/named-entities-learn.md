---
title: En savoir plus sur les entités nommées
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Découvrez comment les entités nommées vous aident à détecter des éléments sensibles contenant des noms de personnes, des adresses physiques et des termes médicaux via des stratégies de protection contre la perte de données
ms.openlocfilehash: 6c20932216953d64abe4515b529bba66b2561647
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973198"
---
# <a name="learn-about-named-entities"></a>En savoir plus sur les entités nommées

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

*Les entités nommées sont des* [types d’informations sensibles](sensitive-information-type-learn-about.md) (SIT). Ce sont des classifieurs complexes basés sur des dictionnaires et des modèles que vous pouvez utiliser pour détecter les noms de personnes, les adresses physiques et les conditions médicales. Vous pouvez les voir dans le **portail de conformité Microsoft Purview > classification des données > types d’informations sensibles**. Voici une liste partielle des emplacements où vous pouvez utiliser des SIT :


- [Stratégies de protection contre la perte de données Microsoft Purview (DLP)](dlp-learn-about-dlp.md) 
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Gestion des risques internes](insider-risk-management-solution-overview.md)
- [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [Microsoft Purview Information Protection](apply-sensitivity-label-automatically.md)
- [Gestion du cycle de vie des données](information-governance.md)
- [Gestion des enregistrements](records-management.md)
- [Microsoft Purview eDiscovery](ediscovery.md)
- [Microsoft Priva](/privacy/priva/priva-overview.md)
- [Les données exactes correspondent aux types d’informations sensibles](sit-learn-about-exact-data-match-based-sits.md)

DLP utilise spécialement des entités nommées dans les *modèles de stratégie améliorés*, qui sont des stratégies DLP préconfigurées que vous pouvez personnaliser en fonction des besoins de votre organisation. Vous pouvez également [créer vos propres stratégies DLP](create-test-tune-dlp-policy.md) à partir d’un [modèle vide](create-a-dlp-policy-from-a-template.md) et utiliser une entité nommée SIT comme condition.

<!-- There are many other SITs that detect strings like social security, credit card, or bank account numbers to identify sensitive items. For more information, see [Sensitive information types entity definitions](sensitive-information-type-entity-definitions.md).-->



## <a name="examples-of-named-entity-sits"></a>Exemples de SIT d’entité nommée

Les SIT d’entité nommées sont disponibles en deux versions, *regroupées* et *regroupées*

Les SIT d’entité nommée groupées détectent toutes les correspondances possibles. Utilisez-les comme critères généraux dans vos stratégies DLP pour détecter les éléments sensibles.

Les SIT d’entité nommée non regroupées ont un focus plus étroit, comme un seul pays. Utilisez-les lorsque vous avez besoin d’une stratégie DLP avec une étendue de détection plus étroite.
 
Voici quelques exemples de SIT d’entité nommée. Vous pouvez les trouver toutes dans les [définitions d’entité de type Informations sensibles](sensitive-information-type-entity-definitions.md).

|Entité nommée |Description  |Groupé/non groupé  |
|---------|---------|---------|
|Tous les noms complets    |détectera toutes les correspondances possibles de noms complets         |   Livré      |
|Toutes les adresses physiques    |détectera toutes les correspondances possibles d’adresses physiques     | Livré |
|Toutes les conditions générales médicales    |détectera toutes les correspondances possibles de conditions médicales |Livré |
|Adresses physiques de l’Australie |  Détecte les modèles liés aux adresses physiques de l’Australie. Inclus dans toutes les adresses physiques SIT. |Dégroupées |
|Termes de l’analyse de sang     |Détecte les termes liés aux tests sanguins, tels que « hCG ». Termes anglais uniquement. Inclus dans tous les termes et conditions médicales SIT      |Dégroupées |
|Noms des médicaments de marque     |Détecte les noms des médicaments de marque, tels que « Tylenol ». Termes anglais uniquement. Inclus dans tous les termes et conditions médicales.         |Dégroupées |

## <a name="examples-of-enhanced-dlp-policies"></a>Exemples de stratégies DLP améliorées

Voici quelques exemples de stratégies DLP améliorées qui utilisent des SIT d’entité nommée. Vous pouvez les trouver toutes les 10 dans le **portail de conformité Microsoft Purview > protection contre la perte de données > créer une stratégie**. Les modèles améliorés peuvent être utilisés dans la protection contre la perte de données et l’étiquetage automatique.

|Catégorie de stratégie  |Modèle  |Description  |
|---------|---------|---------|
|Financier|U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced         |Permet de détecter la présence d'informations protégées par la loi Gramm-Leach-Bliley Act (GLBA), notamment des informations comme des numéros de sécurité sociale ou des numéros de carte de crédit. Ce modèle amélioré étend l’original en détectant également les noms complets des personnes, États-Unis/Royaume-Uni. numéro de passeport, numéro de permis de conduire américain et adresses physiques américaines.         |
| Santé et médical   |Australia Health Records Act (HRIP Act) Enhanced         |Permet de détecter la présence d'informations généralement couvertes par la loi australienne sur la protection des renseignements personnels et des informations sur la santé, comme un numéro de dossier médical ou un numéro TFN (numéro de dossier fiscal). Ce modèle amélioré étend l’original en détectant également les noms complets des personnes, les conditions médicales et les adresses physiques de l’Australie.         |
|Confidentialité   |Règlement général sur la protection des données (RGPD) amélioré         | Permet de détecter la présence d’informations personnelles à l’intérieur de l’Union européenne (UE) pour aider à respecter les obligations de confidentialité du RGPD. Ce modèle amélioré détecte les noms complets des personnes et les adresses physiques des pays de l’UE.        |


## <a name="next-steps"></a>Prochaines étapes

- [Utiliser des entités nommées dans vos stratégies de protection contre la perte de données](named-entities-use.md)


## <a name="for-further-information"></a>Pour plus d’informations

- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [En savoir plus sur les types d’informations sensibles](sensitive-information-type-learn-about.md)
- [Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md)
- [Créer un type d’informations sensibles personnalisé dans PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Stratégies de protection contre la perte de données (DLP)](data-loss-prevention-policies.md) 
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Étiquettes de rétention](retention.md)
- [Conformité des communications](communication-compliance.md)
- [Stratégies d’étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md) 
