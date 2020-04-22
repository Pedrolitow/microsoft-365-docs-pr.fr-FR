---
title: 'Étape 7 : configurer la gestion des accès privilégiés'
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
ms.custom: ''
description: Comprenez et configurez la gestion des accès privilégiés.
ms.openlocfilehash: 4fed4daacc17a34563825bf0575880ce06ec6ebd
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43636987"
---
# <a name="step-7-configure-privileged-access-management"></a>Étape 7 : configurer la gestion des accès privilégiés

*Cette étape est facultative et s’applique uniquement à la version E5 et à la version Conformité avancée de Microsoft 365 Entreprise*

![Phase 6 : Protection des informations](../media/deploy-foundation-infrastructure/infoprotection_icon-small.png)

La gestion des accès privilégiés est activée en configurant des stratégies qui spécifient un accès juste-à-temps pour les activités basées sur les tâches de votre client. Il peut vous aider à protéger votre organisation contre les violations susceptibles d’utiliser des comptes administrateur avec privilèges existants avec un accès permanent aux données sensibles ou un accès aux paramètres de configuration critiques. Par exemple, vous pouvez configurer une stratégie de gestion des accès privilégiés qui requiert une approbation explicite pour accéder aux paramètres de la boîte aux lettres de l’organisation et les modifier dans votre client.

Dans cette étape, vous allez activer la gestion des accès privilégiés dans votre client et configurer des stratégies d’accès privilégié qui fournissent une sécurité supplémentaire pour l’accès basé sur les tâches aux paramètres de données et de configuration de votre organisation. Il existe trois étapes de base pour commencer à utiliser l’accès privilégié dans votre organisation :
- Création d’un groupe d’approbateurs
- Activation des accès privilégiés
- Création de stratégies d’approbation

Une fois configurée, la gestion des accès privilégiés permettra à votre organisation de fonctionner sans aucun privilège permanent et de fournir une sécurité renforcée contre les lacunes d’un accès administratif permanent comme celui-ci. L’accès privilégié requiert des approbations pour exécuter toute tâche pour laquelle une stratégie d’approbation associée a été définie. Les utilisateurs ayant besoin d’exécuter des tâches incluses dans la stratégie d’approbation doivent demander l’approbation de l’accès et l’obtenir afin de disposer des autorisations nécessaires pour exécuter les tâches définies dans la stratégie.

Pour activer la gestion des accès privilégiés, consultez la rubrique [configurer la gestion des accès privilégiés](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-configuration) .

Pour plus d’informations, consultez la rubrique [gestion des accès privilégiés](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-overview) .


|||
|:-------|:-----|
|![Guides de Laboratoire de Test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)|  Pour tester cette configuration dans un environnement de laboratoire de test, consultez le [Guide de laboratoire de test Gestion des accès privilégiés](privileged-access-microsoft-365-enterprise-dev-test-environment.md). |
|||

Comme point de contrôle intermédiaire, consultez les [critères de sortie](infoprotect-exit-criteria.md#crit-infoprotect-step7) correspondant à cette étape.

## <a name="next-step"></a>Étape suivante

[Critères de sortie de l’infrastructure de protection des informations](infoprotect-exit-criteria.md)
