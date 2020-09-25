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
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Comprendre comment le gestionnaire de conformité Microsoft calcule un score personnalisé en fonction des actions entreprises pour traiter les risques et améliorer la position de votre conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f1707e0117d0a61f572716f21d13a02821955401
ms.sourcegitcommit: 61d7284b412d0f7bbd8bbb2225c2e6324f86b717
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "48262267"
---
# <a name="compliance-score-calculation"></a>Calcul du score de conformité

**Dans cet article :** Découvrez comment le gestionnaire de conformité calcule un score de conformité pour votre organisation. Cet article explique comment **interpréter votre score**, ce qu’inclut l’évaluation de la **base de données de protection des données** , la **surveillance continue**et **la façon dont différents types d’actions sont gérés et évalués**.

> [!IMPORTANT]
> Les recommandations du gestionnaire de conformité ne doivent pas être interprétées comme garantie de conformité. Il vous revient d’évaluer et de valider l’efficacité des contrôles client selon votre environnement réglementaire. Ces services sont soumis aux conditions des [services en ligne](https://go.microsoft.com/fwlink/?linkid=2108910). Consultez également [les conseils Microsoft 365 sur les licences pour la sécurité et la conformité](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="how-to-read-your-compliance-score"></a>Comment lire le score de conformité

Le tableau de bord du gestionnaire de conformité affiche votre score de conformité global. Ce score mesure votre progression dans l’exécution des actions d’amélioration recommandées dans les contrôles. Votre score peut vous aider à comprendre votre position actuelle en matière de conformité. Elle peut également vous aider à hiérarchiser les actions en fonction de leur potentiel pour réduire les risques.

Une valeur de score est attribuée à trois niveaux :

1. **Résultat**de l’action d’amélioration : chaque action a un impact différent sur votre score en fonction du risque potentiel concerné

2. **Score de contrôle**: ce score est la somme des points gagnés en effectuant les actions d’amélioration dans le contrôle. Cette somme est appliquée dans son intégralité à votre score de conformité global lorsque le contrôle remplit les deux conditions suivantes :
    - Le statut de l' **implémentation** est égal à **implémenté** ou **autre implémentation**, et
    - Le **résultat des tests** est égal à **passé**.

3. **Score d’évaluation**: ce score est la somme de vos scores de contrôle. Elle est calculée à l’aide de scores d’action. Chaque action Microsoft et chaque action d’amélioration gérée par votre organisation sont comptabilisées une seule fois, quelle que soit la fréquence à laquelle elle est référencée dans un contrôle.

Le score de conformité global est calculé à l’aide de scores d’action, où chaque action Microsoft est comptabilisée une fois, chaque action technique que vous gérez est comptabilisée une fois et chaque action non technique que vous gérez est comptabilisée une fois par groupe. Cette logique est conçue pour fournir la comptabilisation la plus précise des actions mises en œuvre et testées dans votre organisation. Vous pouvez remarquer que cela peut entraîner une différence entre le score de conformité global et la moyenne de vos scores d’évaluation. Pour plus d’informations, reportez- [vous à la rubrique scores](#action-types-and-points).

## <a name="initial-score-based-on-microsoft-365-data-protection-baseline"></a>Score initial basé sur la base de données de protection des données Microsoft 365
  
Le gestionnaire de conformité fournit un score initial basé sur la base de données de protection des données Microsoft 365. Cette configuration de référence est un ensemble de contrôles qui inclut des normes et des réglementations clés pour la protection des données et la gouvernance générale des données. Cette ligne de base présente principalement des éléments d’Institut CSF (Institut national de normes et technologie Cybersecurity Framework) et ISO (Organisation internationale de normalisation), ainsi que de FedRAMP (Federal Risk and Authorization Management Program) et RGPD (règlement général sur la protection des données de l’Union européenne).

Votre score initial est calculé en fonction de l’évaluation de la base de données de protection des données par défaut fournie à toutes les organisations. Lors de votre première visite, le gestionnaire de conformité collecte déjà des signaux à partir de vos solutions Microsoft 365. Vous verrez en un clin d’œil comment votre organisation est en fonction des normes et des réglementations clés en matière de protection des données, et découvrez les actions d’amélioration suggérées à entreprendre.

Étant donné que chaque organisation a des besoins spécifiques, le gestionnaire de conformité s’appuie sur la configuration et la gestion des évaluations pour réduire et limiter les risques le plus complet possible.

## <a name="how-compliance-manager-continuously-assesses-controls"></a>Évaluation continue des contrôles par le gestionnaire de conformité

Le gestionnaire de conformité analyse automatiquement votre environnement Microsoft 365 et détecte vos paramètres système, en continu et en mettant automatiquement à jour votre statut d’action technique. Microsoft Secure score est le moteur sous-jacent qui effectue la surveillance.

L’état de votre action est mis à jour dans votre tableau de bord toutes les 24 heures. Une fois que vous avez recommandé d’implémenter un contrôle, vous verrez généralement l’état du contrôle mis à jour le jour suivant.

Par exemple, si vous activez l’authentification multifacteur (MFA) dans le portail Azure AD, le gestionnaire de conformité détecte le paramètre et le reflète dans les détails de la solution Access de contrôle. À l’inverse, si vous n’avez pas activé l’authentification multifacteur, les indicateurs du gestionnaire de conformité en tant qu’action recommandée.

En savoir plus sur [le score de sécurité et son fonctionnement](../security/mtp/microsoft-secure-score-new.md).
  
## <a name="action-types-and-points"></a>Types et points d’action

Le gestionnaire de conformité suit deux types d’actions :

1. **Vos actions d’amélioration**: actions gérées par votre organisation.
2. **Actions Microsoft**: actions gérées par Microsoft.

Les deux types d’actions ont des points qui comptent sur votre score global lorsque vous avez terminé.

### <a name="technical-and-non-technical-actions"></a>Actions techniques et non techniques

Les actions sont regroupées par nature technique ou non technique. L’impact du score de chaque action diffère selon le type.

- Les **actions techniques** sont mises en œuvre en interagissant avec la technologie d’une solution (par exemple, modification d’une configuration). Les points pour les actions techniques sont accordés une fois par action, quel que soit le nombre de groupes auxquels elle appartient.

- Les **actions non techniques** sont gérées par votre organisation et mises en œuvre de manière différente de l’utilisation de la technologie d’une solution. Il existe deux types d’actions non techniques : **documentation** et **opérationnel**. Les points de ces actions sont appliqués à votre score de conformité au niveau d’un groupe. En d’autres termes, si une action existe dans plusieurs groupes, vous recevrez la valeur du point de l’action chaque fois que vous l’implémenterez au sein d’un groupe.

**Exemple de la façon dont les actions techniques et non techniques sont évaluées :**

Imaginons que vous avez une action technique de 3 points qui existe dans 5 groupes, et que vous avez une action non technique de 3 points qui existe dans les cinq mêmes groupes.

Si vous implémentez correctement l’action technique, le nombre total de points que vous recevez est 3. Cela est dû au fait que vous n’avez besoin d’implémenter l’action qu’une seule fois pour votre client. L’état de mise en œuvre et de test de l’action technique s’affichera de la même façon dans toutes les instances de cette action, dans chaque groupe auquel elle appartient.

Si vous implémentez correctement l’action non technique dans chacun des 5 groupes, le nombre total de points que vous recevez est 15. Cela est dû au fait que vous devez implémenter l’action dans chaque groupe. L’état de mise en œuvre et de test pour l’action non technique varie d’un groupe à l’autre, car l’action est implémentée séparément dans chacun de ses groupes.

Cette logique de notation est conçue pour fournir la comptabilisation la plus précise des actions mises en œuvre et testées dans votre organisation.

### <a name="how-score-values-are-determined"></a>Comment les valeurs de score sont-elles déterminées
 
Les actions se voient attribuer une valeur de score selon qu’elles sont obligatoires ou discrétionnaires, et si elles sont préventives, détectives ou correctives.

### <a name="mandatory-and-discretionary-actions"></a>Actions obligatoires et discrétionnaires

 - Les **actions obligatoires** ne peuvent pas être contournées, intentionnellement ou accidentellement. Un exemple d’action obligatoire est une stratégie de mot de passe gérée de manière centralisée qui définit les besoins en termes de longueur, de complexité et d’expiration des mots de passe. Les utilisateurs doivent respecter ces exigences pour accéder au système.
  
 - Les **actions discrétionnaires** reposent sur les utilisateurs à comprendre et à adhérer à une stratégie. Par exemple, une stratégie imposant aux utilisateurs de verrouiller leur ordinateur lorsqu’ils le quittent est une action discrétionnaire car elle s’appuie sur l’utilisateur.
  
### <a name="preventative-detective-and-corrective-actions"></a>Actions préventives, de détection et de correction
  
 - Les **actions préventives** répondent à des risques spécifiques. Par exemple, la protection des informations sur REST à l’aide du chiffrement est une action préventive contre les attaques et les violations. La séparation des tâches est une action préventive permettant de gérer le conflit d’intérêts et de prévenir les fraudes.
  
 - Les **actions de détective** surveillent activement les systèmes pour identifier les problèmes ou les comportements irréguliers qui représentent un risque, ou qui peuvent être utilisés pour détecter des intrusions ou des violations. Les exemples incluent l’audit de l’accès système et les actions d’administration privilégiées. Conformité réglementaire les audits sont un type d’action de détective utilisé pour trouver des problèmes de processus.
  
- Les **actions correctives** tentent de limiter les effets néfastes d’un incident de sécurité à un minimum, de prendre des mesures correctives pour réduire l’effet immédiat, et de renverser les dommages dans la mesure du possible. La réponse aux incidents de confidentialité est une mesure corrective permettant de limiter les dommages et de restaurer les systèmes à un état opérationnel après une violation.
  
Chaque action a une valeur affectée dans le gestionnaire de conformité en fonction du risque qu’elle représente :

|**Type**|**Score attribué**|
|:-----|:-----|
| Préventif obligatoire | vingt |
| Discrétionnaire préventif | 9  |
| Détective obligatoire | 3 |
| Discrétion de détective | 0,1 |
| Correction obligatoire | 3 |
| Correction discrétionnaire corrective | 0,1 |
  
![Valeurs des points d’action du gestionnaire de conformité](../media/compliance-score-action-scoring.png "Valeurs des points d’action du gestionnaire de conformité")