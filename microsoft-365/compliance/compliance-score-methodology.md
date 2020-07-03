---
title: Calcul du score de conformité Microsoft (aperçu)
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
description: Comprendre comment le score de conformité Microsoft calcule un score personnalisé en fonction des actions entreprises pour traiter les risques et améliorer la position de votre conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 69b631dc355ff497d0f6042e0cce6aff3d70e557
ms.sourcegitcommit: 51a9f34796535309b8ca8b52da92da0a3621327b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "45024674"
---
# <a name="compliance-score-preview-calculation"></a>Calcul du score de conformité (aperçu)

> [!IMPORTANT]
> Les recommandations du Gestionnaire de conformité ne doivent pas être interprétées comme une garantie de conformité. Il vous revient d’évaluer et de valider l’efficacité des contrôles client selon votre environnement réglementaire. Ces services sont actuellement en version préliminaire et soumis aux conditions des [services en ligne](https://go.microsoft.com/fwlink/?linkid=2108910). Consultez également [les conseils Microsoft 365 sur les licences pour la sécurité et la conformité](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="how-compliance-score-works"></a>Fonctionnement du score de conformité

Le tableau de bord de score de conformité affiche un score qui mesure votre progression dans la réalisation d’actions d’amélioration dans les contrôles. Chaque action a un impact différent sur votre score, en fonction des risques potentiels impliqués. Votre score peut vous aider à déterminer l’action à mettre en évidence afin d’améliorer votre position de conformité globale.

Les valeurs de score de conformité affichées pour le contrôle sont appliquées *dans leur intégralité* à votre score total en fonction de la réussite ou de l’échec. Le contrôle est implémenté et réussit le test d’évaluation suivant, ou non. 

Les points sont ajoutés à votre score de conformité lorsque le contrôle a :

- Le statut de l' **implémentation** est égal à **implémenté** ou **autre implémentation**, et
- Le **résultat des tests** est égal à **passé**.

Un score de contrôle est la somme des points gagnés en prenant des mesures d’amélioration. La somme de vos scores de contrôle est le score d’évaluation. **La somme de vos scores d’évaluation est votre score de conformité global.**

## <a name="initial-score-based-on-microsoft-365-data-protection-baseline"></a>Score initial basé sur la base de données de protection des données Microsoft 365
  
Le score de conformité vous donne un score initial basé sur la base de données de protection des données Microsoft 365. Cette configuration de référence est un ensemble de contrôles qui inclut des normes et des réglementations clés pour la protection des données et la gouvernance générale des données. Cette ligne de base présente principalement des éléments d’Institut CSF (Institut national de normes et technologie Cybersecurity Framework) et ISO (Organisation internationale de normalisation), ainsi que de FedRAMP (Federal Risk and Authorization Management Program) et RGPD (règlement général sur la protection des données de l’Union européenne).

L’évaluation de la base de données de protection des données (fournie par défaut à toutes les organisations) est utilisée pour calculer votre score initial avant de configurer d’autres évaluations. Lors de votre première visite, le score de conformité collecte déjà des signaux à partir de vos solutions Microsoft 365. Vous verrez en un clin d’œil comment votre organisation est en fonction des normes et des réglementations clés en matière de protection des données, et découvrez les actions d’amélioration suggérées à entreprendre.

Étant donné que chaque organisation a des besoins spécifiques, le score de conformité repose sur la configuration et la gestion de vos propres évaluations afin de réduire et réduire le risque le plus complet possible.

## <a name="how-compliance-score-continuously-assesses-controls"></a>Évaluation continue des contrôles par le score de conformité

Le score de conformité analyse automatiquement votre environnement Microsoft 365 et détecte vos paramètres système, en continu et en mettant automatiquement à jour votre état de contrôle technique. Le score de sécurité est le moteur sous-jacent qui effectue la surveillance.

Votre état de contrôle est mis à jour sur votre tableau de bord de score de conformité toutes les 24 heures. Une fois que vous avez recommandé d’implémenter un contrôle, vous verrez le statut de contrôle mis à jour le jour suivant.

Par exemple, si vous activez l’authentification multifacteur (MFA) dans le portail Azure AD, le score de conformité détecte le paramètre et indique que, dans les détails de la solution Access de contrôle. À l’inverse, si vous n’avez pas activé l’authentification multifacteur, les indicateurs de score de conformité qui vous sont recommandés.

Lors de la préversion publique, l’évaluation continue est disponible pour une partie des contrôles, mais pas pour tous.

#### <a name="learn-more"></a>Si vous souhaitez en savoir plus
Découvrez [le score sécurisé et son fonctionnement](../security/mtp/microsoft-secure-score-new.md).
  
## <a name="action-types-and-points"></a>Types et points d’action

Le score de conformité effectue le suivi de deux types d’actions : les actions que vous gérez et les actions gérées par Microsoft. Les deux types d’actions ont des points qui comptent sur votre score global lorsque vous avez terminé :

1. **Vos points** contribuent à votre score de conformité en fonction des contrôles gérés par votre organisation.
2. Les **points gérés Microsoft** contribuent à votre score de conformité en fonction des actions gérées par Microsoft en tant que fournisseur de services Cloud.

Les actions se voient attribuer une valeur de score selon qu’elles sont obligatoires ou discrétionnaires, et si elles sont préventives, détectives ou correctives.

### <a name="mandatory-and-discretionary-actions"></a>Actions obligatoires et discrétionnaires

 - Les **actions obligatoires** ne peuvent pas être contournées, intentionnellement ou accidentellement. Par exemple, une stratégie de mot de passe gérée de manière centralisée définit les exigences de longueur, de complexité et d’expiration des mots de passe. Les utilisateurs doivent respecter ces exigences pour accéder au système.
  
 - Les **actions discrétionnaires** reposent sur les utilisateurs pour comprendre la stratégie et agir en conséquence. Par exemple, une stratégie imposant aux utilisateurs de verrouiller leur ordinateur lorsqu’ils le quittent est une action discrétionnaire car elle s’appuie sur l’utilisateur.
  
### <a name="preventative-detective-and-corrective-actions"></a>Actions préventives, de détection et de correction
  
 - Les **actions préventives** répondent à des risques spécifiques. Par exemple, la protection des informations sur REST à l’aide du chiffrement est une action préventive contre les attaques et les violations. La séparation des tâches est une action préventive permettant de gérer le conflit d’intérêts et de prévenir les fraudes.
  
 - Les **actions de détective** surveillent activement les systèmes pour identifier les problèmes ou les comportements irréguliers qui représentent un risque, ou qui peuvent être utilisés pour détecter des intrusions ou des violations. Les exemples incluent l’audit de l’accès système et les actions d’administration privilégiées. Conformité réglementaire les audits sont un type d’action de détective utilisé pour trouver des problèmes de processus.
  
- Les **actions correctives** tentent de limiter les effets néfastes d’un incident de sécurité à un minimum, de prendre des mesures correctives pour réduire l’effet immédiat, et de renverser les dommages dans la mesure du possible. La réponse aux incidents de confidentialité est une mesure corrective permettant de limiter les dommages et de restaurer les systèmes à un état opérationnel après une violation.
  
Chaque action a une valeur affectée dans le score de conformité en fonction du risque qu’elle représente :

|**Type**|**Score attribué**|
|:-----|:-----|
| Préventif obligatoire | vingt |
| Discrétionnaire préventif | 9  |
| Détective obligatoire | 3  |
| Discrétion de détective | 1  |
| Correction obligatoire | 3  |
| Correction discrétionnaire corrective | 1  |
  
![Valeurs de point de contrôle de score de conformité](../media/compliance-score-controls-scoring.png "Valeurs de point de contrôle de score de conformité")