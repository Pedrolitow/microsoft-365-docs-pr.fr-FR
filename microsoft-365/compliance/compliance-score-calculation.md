---
title: Calcul du score de conformité
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment le Gestionnaire de conformité Microsoft Purview calcule un score personnalisé en fonction des actions prises pour résoudre les risques et améliorer votre posture de conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 177f3eb5a16da6541c2331d68f4d2a3b8cf215ac
ms.sourcegitcommit: 06b81b66f13774102bb34556479c1ff890011afb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67357397"
---
# <a name="compliance-score-calculation"></a>Calcul du score de conformité

**Dans cet article :** Découvrez comment le Gestionnaire de conformité calcule un score de conformité pour votre organisation. Cet article explique comment **interpréter votre score**, ce que comprend l’évaluation **de la base de référence de protection des données** , la **surveillance continue** et **comment différents types d’actions sont gérés et notés**.

> [!IMPORTANT]
> Les recommandations du Gestionnaire de conformité ne doivent pas être interprétées comme des garanties de conformité. C’est à vous d’évaluer et de valider l’efficacité des contrôles clients en fonction de votre environnement réglementaire. Ces services sont soumis aux conditions générales des conditions générales du [produit](https://go.microsoft.com/fwlink/?linkid=2108910). Consultez également les [conseils de gestion des licences Microsoft 365 pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="how-to-read-your-compliance-score"></a>Comment lire votre score de conformité

Le tableau de bord du Gestionnaire de conformité affiche votre score de conformité global. Ce score mesure votre progression dans l’exécution des actions d’amélioration recommandées dans les contrôles. Votre score peut vous aider à comprendre votre posture de conformité actuelle. Il peut également vous aider à hiérarchiser les actions en fonction de leur potentiel de réduction des risques.

Une valeur de score est affectée à ces niveaux :

1. **Action d’amélioration** : chaque action a un impact différent sur votre score en fonction du risque potentiel impliqué. Pour plus [d’informations, consultez les types d’actions et les points](#action-types-and-points) ci-dessous.

2. **Évaluation** : ce score est calculé à l’aide des scores d’action d’amélioration. Chaque action Microsoft et chaque action d’amélioration gérée par votre organisation sont comptées une seule fois, quelle que soit la fréquence à laquelle elle est référencée dans un contrôle.

Le score de conformité global est calculé à l’aide de scores d’action, où chaque action Microsoft est comptée une fois, chaque action technique que vous gérez est comptée une fois et chaque action non technique que vous gérez est comptée une fois par groupe. Cette logique est conçue pour fournir la comptabilité la plus précise de la façon dont les actions sont implémentées et testées dans votre organisation. Vous remarquerez peut-être que votre score de conformité global peut différer de la moyenne de vos scores d’évaluation. En savoir plus ci-dessous sur la [façon dont les actions sont notées](#action-types-and-points).

## <a name="initial-score-based-on-microsoft-365-data-protection-baseline"></a>Score initial basé sur la base de référence de la protection des données Microsoft 365
  
Le Gestionnaire de conformité vous donne un score initial basé sur la ligne de base de protection des données Microsoft 365. Cette base de référence est un ensemble de contrôles qui inclut des réglementations et des normes clés pour la protection des données et la gouvernance générale des données. Cette base de référence tire principalement des éléments du NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) et de l’ISO (Organisation internationale pour la normalisation), ainsi que du FedRAMP (Federal Risk and Authorization Management Program) et du RGPD (Règlement général sur la protection des données de l’Union européenne).

Votre score initial est calculé en fonction de l’évaluation par défaut de la base de référence de protection des données fournie à toutes les organisations. Lors de votre première visite, le Gestionnaire de conformité collecte déjà les signaux de vos solutions Microsoft 365. Vous verrez en un coup d’œil les performances de votre organisation par rapport aux principales normes et réglementations de protection des données, et vous verrez les suggestions de mesures d’amélioration à prendre.

Étant donné que chaque organisation a des besoins spécifiques, le Gestionnaire de conformité s’appuie sur vous pour configurer et gérer les évaluations afin de réduire et d’atténuer les risques de la manière la plus complète possible.

## <a name="how-compliance-manager-continuously-assesses-controls"></a>Comment le Gestionnaire de conformité évalue en permanence les contrôles

Le Gestionnaire de conformité identifie automatiquement les paramètres de votre environnement Microsoft 365 qui permettent de déterminer quand certaines configurations répondent aux exigences d’implémentation des actions d’amélioration. Le Gestionnaire de conformité détecte les signaux provenant d’autres solutions de conformité que vous avez peut-être déployées, notamment la gestion du cycle de vie des données, la protection des informations, la conformité des communications et la gestion des risques internes, et tire également parti de la surveillance du degré de sécurisation Microsoft pour les actions d’amélioration complémentaires.

L’état de votre action est mis à jour sur votre tableau de bord dans les 24 heures suivant la modification. Une fois que vous suivez une recommandation pour implémenter un contrôle, l’état du contrôle est généralement mis à jour le lendemain.

Par exemple, si vous activez l’authentification multifacteur (MFA) dans le portail Azure AD, le Gestionnaire de conformité détecte le paramètre et le reflète dans les détails de la solution d’accès au contrôle. À l’inverse, si vous n’avez pas activé l’authentification multifacteur, le Gestionnaire de conformité signale cette action comme une action recommandée à prendre.

En savoir plus sur [le degré de sécurisation et son fonctionnement](../security/defender/microsoft-secure-score.md).
  
## <a name="action-types-and-points"></a>Types et points d’action

Le Gestionnaire de conformité effectue le suivi de deux types d’actions :

1. **Vos actions d’amélioration** : gérées par votre organisation
2. **Actions Microsoft** : gérées par Microsoft

Les deux types d’actions ont des points qui comptent pour votre score global une fois terminé.

### <a name="technical-and-non-technical-actions"></a>Actions techniques et non techniques

Les actions sont regroupées selon qu’elles sont de nature technique ou non technique. L’impact de scoring de chaque action diffère selon le type.

- **Les actions techniques** sont implémentées en interagissant avec la technologie d’une solution (par exemple, en modifiant une configuration). Les points pour les actions techniques sont accordés une fois par action, quel que soit le nombre de groupes auxquels il appartient.

- **Les actions non techniques** sont gérées par votre organisation et implémentées d’une manière autre que l’utilisation de la technologie d’une solution. Il existe deux types d’actions non techniques : **la documentation** et **les opérations**. Les points de ces actions sont appliqués à votre score de conformité au niveau du groupe. Cela signifie que si une action existe dans plusieurs groupes, vous recevrez la valeur de point de l’action chaque fois que vous l’implémentez au sein d’un groupe.

**Exemple de notation des actions techniques et non techniques :**

Supposons que vous avez une action technique d’une valeur de 3 points qui existe dans 5 groupes, et que vous avez une action non technique d’une valeur de 3 points qui existe dans les 5 mêmes groupes.

Si vous implémentez correctement l’action technique, le nombre total de points que vous recevez est de 3. Cela est dû au fait que vous n’avez besoin d’implémenter l’action qu’une seule fois pour votre locataire. L’état d’implémentation et de test de l’action technique sera le même dans toutes les instances de cette action, dans chaque groupe auquel elle appartient.

Si vous avez correctement implémenté l’action non technique dans chacun des 5 groupes, le nombre total de points que vous recevez est de 15. Cela est dû au fait que vous devez implémenter l’action dans chaque groupe. L’état d’implémentation et de test de l’action non technique diffère d’un groupe à l’autre, car l’action est implémentée séparément au sein de chacun de ses groupes.

Cette logique de scoring est conçue pour fournir la comptabilité la plus précise de la façon dont les actions sont implémentées et testées dans votre organisation.

### <a name="how-score-values-are-determined"></a>Comment les valeurs de score sont déterminées

Les actions se voient attribuer une valeur de score selon qu’elles sont obligatoires ou discrétionnaires, et si elles sont préventives, détectives ou correctives.

### <a name="mandatory-and-discretionary-actions"></a>Actions obligatoires et discrétionnaires

- **Les actions obligatoires** ne peuvent pas être contournées, intentionnellement ou accidentellement. Un exemple d’action obligatoire est une stratégie de mot de passe gérée de manière centralisée qui définit les exigences relatives à la longueur, à la complexité et à l’expiration du mot de passe. Les utilisateurs doivent respecter ces exigences pour accéder au système.
  
- **Les actions discrétionnaires** s’appuient sur les utilisateurs pour comprendre et respecter une stratégie. Par exemple, une stratégie exigeant que les utilisateurs verrouillent leur ordinateur lorsqu’ils quittent l’ordinateur est une action discrétionnaire, car elle s’appuie sur l’utilisateur.
  
### <a name="preventative-detective-and-corrective-actions"></a>Actions préventives, de détection et correctives
  
-  Les **actions préventives** portent sur des risques spécifiques. Par exemple, la protection des informations au repos par chiffrement est une action préventive contre les attaques et les violations. La séparation des fonctions est une action préventive pour gérer les conflits d'intérêts et se prémunir contre la fraude.
  
- **Les actions de détection** surveillent activement les systèmes pour identifier les conditions irrégulières ou les comportements qui représentent des risques, ou qui peuvent être utilisés pour détecter les intrusions ou les violations. Les exemples incluent l’audit de l’accès système et les actions d’administration privilégiées. Les audits de conformité réglementaire sont un type d’action de détection utilisé pour rechercher les problèmes de processus.
  
- **Les mesures correctives** tentent de limiter au minimum les effets négatifs d’un incident de sécurité, de prendre des mesures correctives pour réduire l’effet immédiat et d’inverser les dommages si possible. Une réponse à un incident de confidentialité est une action corrective visant à limiter les dommages, puis à remettre les systèmes en état de fonctionnement après une violation.
  
Chaque action a une valeur affectée dans le Gestionnaire de conformité en fonction du risque qu’elle représente :

|**Type**|**Score attribué**|
|:-----|:-----|
| Obligatoire préventif | 27 |
| Discrétionnaire préventive | 9  |
| Détective obligatoire | 3 |
| Détective discrétionnaire | 1 |
| Corrective obligatoire | 3 |
| Correctif discrétionnaire | 1 |
  
![Valeurs de point d’action du Gestionnaire de conformité.](../media/compliance-score-action-scoring.png "Valeurs de point d’action du Gestionnaire de conformité")
