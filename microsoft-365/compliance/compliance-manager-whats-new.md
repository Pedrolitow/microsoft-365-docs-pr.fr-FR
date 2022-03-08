---
title: Nouveautés du Gestionnaire de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez les nouveautés du gestionnaire de conformité et les nouveautés à venir. Découvrez les évaluations mises à jour, les nouveaux modèles d’évaluation, les nouvelles actions, etc.
ms.openlocfilehash: 48aed2e173231e3945bcdd3de73052de9f970a5b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317652"
---
# <a name="whats-new-in-microsoft-compliance-manager"></a>Nouveautés du Gestionnaire de conformité Microsoft

**Dans cet article :** Découvrez les mises à jour récentes dans le Gestionnaire de conformité.

## <a name="february-2022"></a>Février 2022

### <a name="continuous-compliance-assessment-of-improvement-actions"></a>Évaluation continue de la conformité des actions d’amélioration

Nous ajoutons des tests automatisés et la génération de preuves pour plus de 35 actions d’amélioration dans le Gestionnaire de conformité qui n’étaient pas précédemment couvertes par le Niveau de sécurité. Grâce à l’évaluation continue de la conformité, vous pouvez recevoir des mises à jour sur les actions d’amélioration que vous avez effectuées si elles sont pertinentes pour vos évaluations de conformité et si vous êtes autorisé à accéder aux solutions appropriées. L’évaluation continue de la conformité donne également aux utilisateurs une visibilité sur la logique de notation de vos actions d’amélioration et fournit des informations et des preuves sur la raison pour laquelle vous avez reçu un certain score. Cette fonctionnalité fonctionne parallèlement aux intégrations existantes avec Microsoft 365 Secure Score, et toutes les actions automatisées que vous avez précédemment configurées continueront de fonctionner telle quelle. En savoir plus sur [les paramètres de test automatisés](compliance-manager-setup.md#set-up-automated-testing).
### <a name="alerts-and-alert-policies"></a>Alertes et stratégies d’alerte

Les utilisateurs peuvent désormais définir des alertes pour les modifications apportées au Gestionnaire de conformité qu’une organisation souhaite suivre. À l’aide d’un Assistant d’installation facile, vous pouvez créer des stratégies d’alerte pour créer des notifications lorsque les types d’événements suivants se produisent : une modification du score d’action d’amélioration, une modification d’affectation d’action d’amélioration, un changement d’état de test ou d’implémentation dans une action d’amélioration et un téléchargement ou suppression de fichiers dans l’onglet Documents d’une action d’amélioration. Pour en savoir plus, consultez les [alertes et les stratégies d’alerte du Gestionnaire de conformité](compliance-manager-alert-policies.md).

### <a name="try-recommended-assessment-templates-for-your-organization"></a>Essayer les modèles d’évaluation recommandés pour votre organisation

Votre organisation peut désormais obtenir des recommandations du Gestionnaire de conformité sur les évaluations les plus pertinentes pour vous, avec un processus de configuration rapide pour être opérationnel. Pour en savoir plus sur les recommandations et sur la façon d’essayer des modèles d’évaluation premium avant d’acheter une licence, voir Démarrer une évaluation [premium](compliance-manager-setup.md#start-a-premium-assessments-trial).

## <a name="november-2021"></a>Novembre 2021

### <a name="zero-trust-integration-for-the-data-protection-baseline-template"></a>Intégration de confiance zéro pour le modèle de référence de la protection des données

La confiance zéro est une approche proactive et intégrée de la sécurité sur toutes les couches du patrimoine numérique qui vérifie explicitement et en permanence chaque transaction, déclare le moindre privilège et s’appuie sur l’intelligence, la détection avancée et la réponse en temps réel aux menaces. Le modèle de base de la protection des données du Gestionnaire de conformité, inclus pour tous les utilisateurs, intègre désormais 57 nouveaux contrôles et 36 nouvelles actions pour la confiance zéro alignées sur les familles de contrôles suivantes :

- Application de confiance zéro
- Conseils de développement d’application De confiance zéro
- Point de terminaison d’une confiance zéro
- Données de confiance zéro
- Identité de confiance zéro
- Infrastructure de confiance zéro
- Réseau de confiance zéro
- Visibilité, automatisation et orchestration de confiance zéro

### <a name="new-preview-templates"></a>Nouveaux modèles d’aperçu

Les modèles d’évaluation suivants sont désormais disponibles en prévisualisation :

- ISO 27001:2013 pour Azure (prévisualisation)
- ISO 27001:2013 pour Dynamics 365 (aperçu)
- Modéré FedRAMP pour Dynamics 365 (prévisualisation)
- Modéré FedRAMP pour Azure (prévisualisation)
- FedRAMP Élevé pour Azure (prévisualisation)
- FedRAMP high for Dynamics 365 (Preview)
- SOC 2 pour Azure (prévisualisation)
- SOC 2 pour Dynamics 365 (prévisualisation)
- ISO 27018:2019 pour Azure (prévisualisation)
- ISO 27018:2019 pour Dynamics 365 (prévisualisation)

## <a name="october-2021"></a>Octobre 2021

### <a name="new-assessment-templates"></a>Nouveaux modèles d’évaluation

Nous avons publié de nouveaux modèles d’évaluation, notamment :

- Loi sur la protection des données personnelles (CPA)
- Loi sur la protection des données du consommateur (CDPA)
- Égypte - Loi sur la protection des données
- Australie - ASD Essential 8 Niveau de maturité 1
- Australie - ASD Essential 8 Niveau de maturité 2
- Australie - ASD Essential 8 - Niveau de maturité 3

### <a name="integration-with-microsoft-priva"></a>Intégration à Microsoft Priva

Le Gestionnaire de conformité peut désormais travailler de pair avec Microsoft Priva, une solution qui peut vous aider à protéger les données personnelles que votre organisation stocke dans Microsoft 365. Priva propose des outils pour vous aider à visualiser et à comprendre vos données, implémenter des stratégies pour gérer les scénarios de risque clés et gérer les demandes de droits de l’objet. Lorsque vous prenez des mesures en Priva pour protéger les données personnelles que vous stockez, cela peut contribuer à vos évaluations de confidentialité dans le Gestionnaire de conformité et peut vous aider à améliorer votre score de conformité. Pour voir comment Priva et d’autres solutions contribuent à votre score et en savoir plus sur les opportunités potentielles pour d’autres améliorations, consultez l’onglet **Solutions** dans le Gestionnaire de conformité. Vous trouverez également plus d’informations sur Priva à [l’aide de la description de Microsoft Priva](/privacy/priva).

## <a name="july-2021"></a>Juillet 2021

Nous avons ajouté la possibilité de créer des évaluations pour les produits autres que Microsoft 365, en fonction des nouvelles versions universelles de nos modèles. Pour en savoir plus, commencez [par utiliser les modèles d’évaluation](compliance-manager-templates.md).

## <a name="may-2021"></a>Mai 2021

### <a name="new-assessment-templates"></a>Nouveaux modèles d’évaluation

Nous avons publié 75 nouveaux modèles d’évaluation, notamment :
- Australia Privacy Act
- CIS Microsoft 365 Foundation Levels 1 et 2
- Allemagne : exigences de surveillance pour les services it dans les institutions financières (CASER)
- Sarbanes-Oxley Act
- Afrique du Sud - Promotion de la loi sur l’accès à l’information

Consultez la liste complète des [modèles d’évaluation](compliance-manager-templates-list.md).

## <a name="april-2021"></a>Avril 2021

### <a name="support-for-us-government-dod-customers"></a>Prise en charge des clients DoD du gouvernement américain

Le Gestionnaire de conformité est désormais disponible pour les clients doD du gouvernement américain, en plus des clients modérés et Cloud de la communauté du secteur public du gouvernement américain Community (Cloud de la communauté du secteur public).

## <a name="march-2021"></a>mars 2021

### <a name="active-and-inactive-templates"></a>Modèles actifs et inactifs

Chaque page d’évaluation et page de modèle d’évaluation possède un compteur de modèles activé. Ce compteur indique le nombre de modèles éligibles que vous utilisez conformément à votre contrat de licence. Afficher la [disponibilité et la gestion des licences des](compliance-manager-templates.md#template-availability-and-licensing) modèles pour en savoir plus.
