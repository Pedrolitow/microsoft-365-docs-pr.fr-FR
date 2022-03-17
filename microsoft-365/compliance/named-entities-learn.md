---
title: Découvrez les entités nommées (aperçu).
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
description: Découvrez comment les entités nommées vous aident à détecter les éléments sensibles contenant des noms de personnes, des adresses physiques et des termes médicaux via des stratégies de protection contre la perte de données
ms.openlocfilehash: 79f375fecf09a6f7ffe4c1a97b8d6864fbfb3e13
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63524864"
---
# <a name="learn-about-named-entities-preview"></a>Découvrez les entités nommées (aperçu).

> [!IMPORTANT]
> La fonctionnalité entités nommées est en cours de déploiement et apparaît dans votre client lorsqu’elle est disponible pour vous. Recherchez-les dans l’Explorateur de contenu et dans le flux de authoring de stratégie de protection contre la perte de données (DLP). 

*Les entités nommées* sont [des types d’informations sensibles](sensitive-information-type-learn-about.md) (SIT). Ce sont des classifieurs complexes basés sur des modèles et des dictionnaires que vous pouvez utiliser pour détecter des noms de personnes, des adresses physiques et des conditions médicales. Vous pouvez les voir dans le Centre de conformité > **classification des > types d’informations sensibles**. Voici une liste partielle des endroits où vous pouvez utiliser les sits :

- [Stratégies de protection contre la perte de données (DLP)](dlp-learn-about-dlp.md) 
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Gestion des risques internes](insider-risk-management-solution-overview.md)
- [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)

DLP fait un usage spécial des entités *nommées dans les modèles de stratégie améliorés*, qui sont des stratégies DLP pré-configurées que vous pouvez personnaliser pour les besoins de votre organisation. Vous pouvez également créer [vos propres stratégies DLP](create-test-tune-dlp-policy.md) à partir d’un modèle [vide](create-a-dlp-policy-from-a-template.md) et utiliser une entité nommée SIT comme condition.

<!-- There are many other SITs that detect strings like social security, credit card, or bank account numbers to identify sensitive items. For more information, see [Sensitive information types entity definitions](sensitive-information-type-entity-definitions.md).-->



## <a name="examples-of-named-entity-sits"></a>Exemples de sits d’entité nommée

Les sits d’entité nommée ont deux *noms :* regroupés et *dissociés*

Les sits d’entité nommée regroupées détectent toutes les correspondances possibles. Utilisez-les comme critères généraux dans vos stratégies DLP pour détecter les éléments sensibles.

Les sits d’entité nommée dissociées ont un focus plus étroit, comme un seul pays. Utilisez-les lorsque vous avez besoin d’une stratégie DLP avec une portée de détection plus étroite.
 
Voici quelques exemples de SIT d’entité nommée. Vous pouvez les trouver tous les 52 dans le Centre de conformité > classification des > **types d’informations sensibles**.

|Entité nommée |Description  |Bundled/Unbundled  |
|---------|---------|---------|
|Tous les noms complets    |détectera toutes les correspondances possibles de noms complets         |   bundled      |
|Toutes les adresses physiques    |détectera toutes les correspondances possibles d’adresses physiques     | bundled |
|Toutes les conditions médicales    |détectera toutes les correspondances possibles de conditions médicales |bundled |
|Adresses physiques en Australie |  Détecte les modèles liés aux adresses physiques d’Australie. |unbundled |
|Conditions de test du test de test pour le test de     |Détecte les termes liés aux tests de tests sur le sang, tels que « hCG ». Termes anglais uniquement.      |unbundled |
|Noms de marque     |Détecte les noms de marque de famille, tels que « Tylenol ». Termes anglais uniquement.         |unbundled |

## <a name="examples-of-enhanced-dlp-policies"></a>Exemples de stratégies DLP améliorées

Voici quelques exemples de stratégies DLP améliorées qui utilisent des sits d’entité nommée. Vous pouvez les trouver tous les 10 dans le Centre de conformité > protection contre la **perte de > créer une stratégie**. Les modèles améliorés peuvent être utilisés dans DLP et l’étiquetage automatique.

|Catégorie de stratégie  |Modèle  |Description  |
|---------|---------|---------|
|Financier|U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced         |Permet de détecter la présence d'informations protégées par la loi Gramm-Leach-Bliley Act (GLBA), notamment des informations comme des numéros de sécurité sociale ou des numéros de carte de crédit. Ce modèle amélioré étend l’original en détectant également les noms complets des personnes( États-Unis/Royaume-Uni). numéro de passeport, numéro de permis de conduire américain et adresses physiques américaines.         |
| Santé et médical   |Australia Health Records Act (HRIP Act) Enhanced         |Permet de détecter la présence d'informations généralement couvertes par la loi australienne sur la protection des renseignements personnels et des informations sur la santé, comme un numéro de dossier médical ou un numéro TFN (numéro de dossier fiscal). Ce modèle amélioré étend l’original en détectant également les noms complets des personnes, les conditions médicales et les adresses physiques de l’Australie.         |
|Confidentialité   |Règlement général sur la protection des données (R GDPR) amélioré         | Permet de détecter la présence d’informations personnelles pour des individus au sein de l’Union européenne (UE) afin de répondre aux obligations de confidentialité du R GDPR. Ce modèle amélioré détecte les noms complets et les adresses physiques des personnes pour les pays de l’UE.        |


## <a name="next-steps"></a>Prochaines étapes

- [Utiliser des entités nommées dans vos politiques de prévention des pertes de données (aperçu)](named-entities-use.md)


## <a name="for-further-information"></a>Pour plus d’informations
<!--- [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [En savoir plus sur les types d’informations sensibles](sensitive-information-type-learn-about.md)
- [Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md)
- [Créer un type d’informations sensibles personnalisé dans PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Stratégies de protection contre la perte de données (DLP)](data-loss-prevention-policies.md) 
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Étiquettes de rétention](retention.md)
- [Conformité des communications](communication-compliance.md)
- [Stratégies d’adage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md) 
