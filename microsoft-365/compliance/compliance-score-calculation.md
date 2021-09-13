---
title: Calcul du score de conformité
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Comprendre comment le Gestionnaire de conformité Microsoft calcule un score personnalisé en fonction des actions prises pour résoudre les risques et améliorer votre posture de conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 26ef0f73a8da9403c2d1fd8248f828d6faf7f6e3
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59176084"
---
# <a name="compliance-score-calculation"></a>Calcul du score de conformité

**Dans cet article :** Découvrez comment le Gestionnaire de conformité calcule un score de conformité pour votre organisation. Cet article explique comment interpréter votre **score,** ce que l’évaluation de référence de la **protection** des données inclut, une surveillance continue et comment différents types d’actions sont gérés et **marqués.**

> [!IMPORTANT]
> Les recommandations du Gestionnaire de conformité ne doivent pas être interprétées comme des garanties de conformité. C’est à vous d’évaluer et de valider l’efficacité des contrôles client par rapport à votre environnement réglementaire. Ces services sont soumis aux conditions générales des [conditions générales des services en ligne.](https://go.microsoft.com/fwlink/?linkid=2108910) Voir aussi Microsoft 365 [licences pour la sécurité et la conformité.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

## <a name="how-to-read-your-compliance-score"></a>Comment lire votre score de conformité

Le tableau de bord du Gestionnaire de conformité affiche votre score de conformité global. Ce score mesure votre progression dans l’exécution des actions d’amélioration recommandées au sein des contrôles. Votre score peut vous aider à comprendre votre posture de conformité actuelle. Il peut également vous aider à hiérarchiser les actions en fonction de leur potentiel pour réduire les risques.

Une valeur de score est affectée à trois niveaux :

1. **Score d’action d’amélioration**: chaque action a un impact différent sur votre score en fonction du risque potentiel impliqué

2. **Score de contrôle**: ce score est la somme des points gagnés en effectuant des actions d’amélioration au sein du contrôle. Cette somme est appliquée entièrement à votre score de conformité global lorsque le contrôle répond aux deux conditions suivantes :
    - **L’état d’implémentation** **est égal à Implémenté** ou **Autre implémentation** et
    - **Le résultat du** test est égal **à Réussi**.

3. **Score d’évaluation**: ce score est la somme de vos scores de contrôle. Elle est calculée à l’aide de scores d’action. Chaque action Microsoft et chaque action d’amélioration gérée par votre organisation sont comptabilisées une seule fois, quelle que soit la fréquence de référencement dans un contrôle.

Le score de conformité global est calculé à l’aide de scores d’action, où chaque action Microsoft est comptée une fois, chaque action technique que vous gérez est comptée une seule fois et chaque action non technique que vous gérez est comptée une fois par groupe. Cette logique est conçue pour fournir la comptabilité la plus précise de la façon dont les actions sont implémentées et testées dans votre organisation. Vous remarquerez peut-être que votre score de conformité global peut différer de la moyenne de vos scores d’évaluation. En savoir plus [ci-dessous sur le score des actions.](#action-types-and-points)

## <a name="initial-score-based-on-microsoft-365-data-protection-baseline"></a>Score initial basé sur la ligne de base Microsoft 365 protection des données
  
Le Gestionnaire de conformité vous donne un score initial basé sur la ligne de base Microsoft 365 protection des données. Cette ligne de base est un ensemble de contrôles qui inclut des réglementations et des normes clés pour la protection des données et la gouvernance générale des données. Cette ligne de base dessine principalement des éléments du NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) et de l’ISO (International Organization for Standardization), ainsi que du FedRAMP (Federal Risk and Authorization Management Program) et du R GDPR (Règlement général sur la protection des données de l’Union européenne).

Votre score initial est calculé en fonction de l’évaluation de base de la protection des données par défaut fournie à toutes les organisations. Lors de votre première visite, le Gestionnaire de conformité collecte déjà des signaux à partir de Microsoft 365 solutions. Vous verrez d’un coup d’œil les résultats de votre organisation par rapport aux principales normes et réglementations en matière de protection des données, ainsi que les suggestions d’actions d’amélioration à prendre.

Étant donné que chaque organisation a des besoins spécifiques, le Gestionnaire de conformité s’appuie sur vous pour configurer et gérer les évaluations afin de réduire et d’atténuer les risques de manière aussi complète que possible.

## <a name="how-compliance-manager-continuously-assesses-controls"></a>Évaluation continue des contrôles par le Gestionnaire de conformité

Le Gestionnaire de conformité analyse automatiquement votre environnement Microsoft 365 et détecte vos paramètres système, en mettant à jour en continu et automatiquement l’état de votre action technique. Le score de sécurité Microsoft est le moteur sous-jacent qui effectue l’analyse.

L’état de votre action est mis à jour sur votre tableau de bord toutes les 24 heures. Une fois que vous avez suivi une recommandation pour implémenter un contrôle, l’état du contrôle est généralement mis à jour le jour suivant.

Par exemple, si vous allumez l’authentification multifacteur (MFA) dans le portail Azure AD, le Gestionnaire de conformité détecte le paramètre et le reflète dans les détails de la solution d’accès aux contrôles. À l’inverse, si vous n’avez pas activer l’ation MFA, le Gestionnaire de conformité l’indicateurs comme une action recommandée à prendre.

En savoir plus sur [le score de sécurité et son fonctionnement.](../security/defender/microsoft-secure-score.md)
  
## <a name="action-types-and-points"></a>Types et points d’action

Le Gestionnaire de conformité suit deux types d’actions :

1. **Vos actions d’amélioration**: actions que votre organisation gère.
2. **Actions Microsoft**: actions que Microsoft gère.

Les deux types d’actions ont des points qui comptent pour votre score global une fois terminé.

### <a name="technical-and-non-technical-actions"></a>Actions techniques et non techniques

Les actions sont regroupées selon qu’elles sont de nature technique ou non technique. L’impact sur le score de chaque action diffère selon le type.

- **Les actions** techniques sont implémentées en interagissant avec la technologie d’une solution (par exemple, en modifiant une configuration). Les points pour les actions techniques sont accordés une fois par action, quel que soit le nombre de groupes à qui il appartient.

- **Les actions non techniques** sont gérées par votre organisation et implémentées d’une manière autre que l’utilisation de la technologie d’une solution. Il existe deux types d’actions non techniques : **la documentation** et **l’opération.** Les points de ces actions sont appliqués à votre score de conformité au niveau du groupe. Cela signifie que si une action existe dans plusieurs groupes, vous recevrez la valeur de point de l’action chaque fois que vous l’implémentez au sein d’un groupe.

**Exemple de score des actions techniques et non techniques :**

Supposons que vous avez une action technique de 3 points qui existe dans 5 groupes et que vous avez une action non technique de 3 points qui existe dans les 5 mêmes groupes.

Si vous avez correctement implémenté l’action technique, le nombre total de points que vous recevez est de 3. Cela est dû au fait que vous n’avez besoin d’implémenter l’action qu’une seule fois pour votre client. L’état d’implémentation et de test de l’action technique sera identique dans toutes les instances de cette action, dans chaque groupe à qui elle appartient.

Si vous avez correctement implémenté l’action non technique dans chacun des 5 groupes, le nombre total de points que vous recevez est de 15. Cela est dû au fait que vous devez implémenter l’action dans chaque groupe. L’état d’implémentation et de test de l’action non technique varie selon les groupes, car l’action est implémentée séparément au sein de chacun de ses groupes.

Cette logique de notation est conçue pour fournir la comptabilité la plus précise de la façon dont les actions sont implémentées et testées dans votre organisation.

### <a name="how-score-values-are-determined"></a>Comment les valeurs de score sont déterminées
 
Une valeur de score est attribuée aux actions selon qu’elles sont obligatoires ou discrétionnaires, et qu’elles soient préventives, préventives ou correctives.

### <a name="mandatory-and-discretionary-actions"></a>Actions obligatoires et discrétionnaires

 - **Les actions obligatoires** ne peuvent pas être contourn es, intentionnellement ou accidentellement. Un exemple d’action obligatoire est une stratégie de mot de passe gérée de manière centralisée qui définit des exigences en matière de longueur, de complexité et d’expiration du mot de passe. Les utilisateurs doivent respecter ces exigences pour accéder au système.
  
 - **Les actions discrétionnaires** s’appuient sur les utilisateurs pour comprendre et adhérer à une stratégie. Par exemple, une stratégie qui oblige les utilisateurs à verrouiller leur ordinateur lorsqu’ils la quittent est une action discrétionnaire, car elle s’appuie sur l’utilisateur.
  
### <a name="preventative-detective-and-corrective-actions"></a>Actions préventives, de prévention et correctives
  
 - Les **actions préventives** gèrent des risques spécifiques. Par exemple, la protection des informations au repos à l’aide du chiffrement est une action préventive contre les attaques et les violations. La répartition des tâches est également une action préventive qui permet de gérer les conflits d’intérêts, puis de lutter contre la fraude.
  
 - **Les actions de détection** surveillent activement les systèmes pour identifier les conditions ou comportements insérez des conditions ou des comportements qui représentent un risque, ou qui peuvent être utilisés pour détecter les intrusions ou les violations. Les exemples incluent l’audit de l’accès au système et les actions administratives privilégiées. Les audits de conformité réglementaire sont un type d’action de recherche utilisé pour rechercher les problèmes de processus.
  
- **Les actions correctives** tentent de limiter au minimum les effets négatifs d’un incident de sécurité, de prendre des mesures correctives pour réduire l’effet immédiat et d’annuler les dommages si possible. Une réponse à un incident de confidentialité est une action corrective visant à limiter les dommages, puis à remettre les systèmes en état de fonctionnement après une violation.
  
Chaque action a une valeur attribuée dans le Gestionnaire de conformité en fonction du risque qu’elle représente :

|**Type**|**Score attribué**|
|:-----|:-----|
| Obligatoire préventive | 27 |
| Discrétionnaire préventive | 9  |
| Inspecteur obligatoire | 3 |
| Discrétionnaire de l’inspecteur | 1 |
| Corrective obligatoire | 3 |
| Correction discrétionnaire | 1 |
  
![Valeurs de point d’action du Gestionnaire de conformité.](../media/compliance-score-action-scoring.png "Valeurs de point d’action du Gestionnaire de conformité")