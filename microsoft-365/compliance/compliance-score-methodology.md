---
title: Calcul du score de conformité
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
ms.openlocfilehash: 9fbc2b2beca3a667b09c1a4ba790651a364d1bf0
ms.sourcegitcommit: e872676ec98036a50d3a0cb5071109ea5f5a7ae5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "41515575"
---
# <a name="microsoft-compliance-score-preview-calculation"></a>Calcul du score de conformité Microsoft (aperçu)

> [!IMPORTANT]
> Le score de conformité n’exprime pas une mesure absolue de la conformité de l’organisation avec une norme ou réglementation particulière. Elle exprime la mesure dans laquelle vous avez adopté des contrôles qui peuvent réduire les risques pour les données personnelles et la confidentialité individuelle. Les recommandations du score de conformité et du gestionnaire de conformité ne doivent pas être interprétées comme garantie de conformité. Ce service est actuellement en version préliminaire et est soumis aux conditions des [services en ligne](https://go.microsoft.com/fwlink/?linkid=2108910).

## <a name="overview"></a>Vue d’ensemble

Le tableau de bord de score de conformité affiche un score qui mesure votre progression dans la réalisation d’actions d’amélioration dans les contrôles. Vos points s’accumulent lorsque vous effectuez des actions.

Votre score est calculé en fonction de l’exécution des actions gérées par Microsoft et des actions gérées par le client. Chaque action a un impact différent sur votre score, en fonction des risques potentiels impliqués, de sorte que le score puisse aider à déterminer l’action à mettre en évidence afin d’améliorer votre position de conformité globale.

Les valeurs de score de conformité affichées pour le contrôle sont appliquées *dans leur intégralité* à votre score total en fonction de la réussite ou de l’échec. Le contrôle est implémenté et réussit le test d’évaluation suivant ou non. Les points affectés sont ajoutés au score de conformité lorsque le contrôle a :

- Le statut de l' **implémentation** est égal à **implémenté** ou **autre implémentation** et,
- Le **résultat des tests** est égal à **passé**.

La somme des points gagnés en prenant en charge les actions d’amélioration est le score de contrôle. La somme de vos scores de contrôle est le score d’évaluation. La somme de vos scores d’évaluation est le score de conformité global

## <a name="initial-score-based-on-microsoft-365-data-protection-baseline"></a>Score initial basé sur la base de données de protection des données Microsoft 365
  
Le score de conformité vous donne un score standard basé sur la base de données de protection des données Microsoft 365, qui est un ensemble de contrôles qui inclut les réglementations et normes clés relatives à la protection des données et à la gouvernance générale des données. Cette ligne de base présente principalement des éléments d’Institut CSF (Institut national de normes et de technologie Cybersecurity Framework) et de l’ISO (Organisation internationale de normalisation), ainsi que de FedRAMP (Federal Risk and Authorization Management Programme) et RGPD (règlement général sur la protection des données de l’Union européenne).

## <a name="how-compliance-score-continuously-assesses-controls"></a>Évaluation continue des contrôles par le score de conformité

Le score de conformité analyse automatiquement votre environnement Microsoft 365 et détecte vos paramètres système, en continu et en mettant automatiquement à jour votre état de contrôle technique. Le score de conformité utilise le score de sécurité pour le moteur sous-jacent qui effectue la surveillance. [En savoir plus sur le score de sécurité et son fonctionnement](../security/mtp/microsoft-secure-score.md).

Votre état de contrôle est mis à jour sur votre tableau de bord de score de conformité toutes les 24 heures. Une fois que vous avez recommandé d’implémenter un contrôle, vous verrez le statut de contrôle mis à jour le jour suivant.

Par exemple, si vous activez l’authentification multifacteur (MFA) dans le portail Azure AD, le score de conformité détecte le paramètre et indique que, dans les détails de la solution Access de contrôle. À l’inverse, si vous n’avez pas activé l’authentification multifacteur, les indicateurs de score de conformité qui vous sont recommandés.

Lors de la préversion publique, l’évaluation continue est disponible pour une partie des contrôles, mais pas pour tous.
  
## <a name="control-types-and-points"></a>Types et points de contrôle

Le score de conformité effectue le suivi de deux types de contrôles, gérés par Microsoft et gérés par le client, dont chacun dispose de points qui contribuent à votre score global :

1. Les **points gérés** par le client contribuent à votre score de conformité en fonction des contrôles gérés par votre organisation.
2. Les **points gérés par Microsoft** contribuent à votre score de conformité en fonction des contrôles gérés par Microsoft en tant que fournisseur de services Cloud.

Les contrôles se voient attribuer une valeur de score selon qu’ils sont obligatoires ou discrétionnaires, et s’ils sont préventifs, détectives ou correcteurs, comme décrit ci-dessous.

### <a name="mandatory-and-discretionary-controls"></a>Contrôles obligatoires et discrétionnaires

 - Les **contrôles obligatoires** sont des actions qui ne peuvent pas être contournées intentionnellement ou accidentellement. Par exemple, une stratégie de mot de passe gérée de manière centralisée définit les exigences de longueur, de complexité et d’expiration des mots de passe. Les utilisateurs doivent se conformer à ces exigences pour accéder au système.
  
 - Les **contrôles discrétionnaires** reposent sur les utilisateurs pour comprendre la stratégie et agir en conséquence. Par exemple, une stratégie imposant aux utilisateurs de verrouiller leur ordinateur lorsqu’ils le quittent est un contrôle discrétionnaire, car il s’appuie sur l’utilisateur.
  
### <a name="preventative-detective-and-corrective-controls"></a>Contrôles de préventif, de détective et de correction
  
 - Les **contrôles préventives** traitent des risques spécifiques. Par exemple, la protection des informations sur REST à l’aide du chiffrement est un contrôle préventif contre les attaques et les violations. La séparation des tâches est un contrôle préventive permettant de gérer le conflit d’intérêt et de prévenir les fraudes.
  
 - Les **contrôles de détective** surveillent activement les systèmes pour identifier les problèmes ou les comportements irréguliers qui représentent un risque ou qui peuvent être utilisés pour détecter des intrusions ou déterminer si une violation se produit. Audit de l’accès au système et actions d’administration privilégiées l’audit est des types de contrôles de surveillance du détective. Conformité réglementaire les audits sont un type de contrôle de détective utilisé pour détecter les problèmes de processus.
  
- Les **contrôles de correction** essaient de limiter les effets néfastes d’un incident de sécurité au minimum, de prendre des mesures correctives pour réduire l’effet immédiat et d’inverser les dommages dans la mesure du possible. La réponse aux incidents de confidentialité est un contrôle correct pour limiter les dommages et restaurer les systèmes à un état opérationnel après une violation.
  
Chaque contrôle a une valeur affectée dans le score de conformité en fonction du risque qu’il représente :

|**Type**|**Score attribué**|
|:-----|:-----|
| Préventif obligatoire | vingt |
| Discrétionnaire préventif | 9  |
| Détective obligatoire | 3 |
| Discrétion de détective | 0,1 |
| Correction obligatoire | 3 |
| Correction discrétionnaire corrective | 0,1 |
  