---
title: 'Étape 7 : Configurer la gestion des accès privilégiés pour Office 365'
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
description: Familiarisez-vous avec la gestion des accès privilégiés pour Office 365 et apprenez à la configurer.
ms.openlocfilehash: da047d21094854f15fdb39fc46fd046a1c4605ed
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41600961"
---
# <a name="step-7-configure-privileged-access-management-for-office-365"></a>Étape 7 : Configurer la gestion des accès privilégiés pour Office 365

*Cette étape est facultative et s’applique uniquement à la version E5 et à la version Conformité avancée de Microsoft 365 Entreprise*

![Phase 6 : Protection des informations](./media/deploy-foundation-infrastructure/infoprotection_icon-small.png)

Vous activez la gestion des accès privilégiés en configurant des stratégies qui indiquent l’accès juste-à-temps pour les activités basées sur des tâches dans votre client Office 365. Elle peut vous aider à protéger votre organisation contre les violations qui pourraient survenir par le biais de comptes d’administrateur privilégiés existants qui donnent un accès permanent à des données sensibles ou à des paramètres de configuration critiques. Par exemple, vous pouvez configurer une stratégie de gestion des accès privilégiés qui requiert une approbation explicite pour pouvoir accéder aux paramètres de boîte aux lettres de votre organisation dans votre client Office 365 et les modifier.

Pour cette étape, vous allez activer la gestion des accès privilégiés dans votre client Office 365 et configurer les stratégies d’accès privilégiés qui permettent de renforcer la sécurité des accès basés sur les tâches à vos paramètres de configuration et à vos données Office 365 pour votre organisation. Il existe trois étapes simples pour commencer à utiliser les accès privilégiés dans votre organisation Office 365 :
- Création d’un groupe d’approbateurs
- Activation des accès privilégiés
- Création de stratégies d’approbation

Une fois configurée, la gestion des accès privilégiés permettra à votre organisation de fonctionner sans aucun privilège permanent et de fournir une sécurité renforcée contre les lacunes d’un accès administratif permanent comme celui-ci. L’accès privilégié requiert des approbations pour exécuter toute tâche pour laquelle une stratégie d’approbation associée a été définie. Les utilisateurs ayant besoin d’exécuter des tâches incluses dans la stratégie d’approbation doivent demander l’approbation de l’accès et l’obtenir afin de disposer des autorisations nécessaires pour exécuter les tâches définies dans la stratégie.

Pour activer la gestion des accès privilégiés d’Office 365, consultez la rubrique relative à la [configuration de la gestion des accès privilégiés dans Office 365](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-configuration).

Pour plus d’informations, reportez-vous à la rubrique relative à la [gestion des accès privilégiés dans Office 365](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-overview).


|||
|:-------|:-----|
|![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)|  Pour tester cette configuration dans un environnement de laboratoire de test, consultez le [Guide de laboratoire de test Gestion des accès privilégiés](privileged-access-microsoft-365-enterprise-dev-test-environment.md). |
|||

Comme point de contrôle intermédiaire, consultez les [critères de sortie](infoprotect-exit-criteria.md#crit-infoprotect-step7) correspondant à cette étape.

## <a name="next-step"></a>Étape suivante

[Critères de sortie de l’infrastructure de protection des informations](infoprotect-exit-criteria.md)
