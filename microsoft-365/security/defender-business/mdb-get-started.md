---
title: Visitez le portail Microsoft 365 Defender
description: Votre centre de sécurité dans Defender Entreprise est le portail Microsoft 365 Defender. Découvrez comment naviguer dans le portail et voir les étapes suivantes.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.date: 08/15/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 20d1bf0cb045e3ee2efc70a6b0c68fec8b8436ca
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67598085"
---
# <a name="visit-the-microsoft-365-defender-portal"></a>Visitez le portail Microsoft 365 Defender

Le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) est votre magasin unique pour l’utilisation et la gestion des Microsoft Defender pour entreprises. Il inclut des légendes pour vous aider à démarrer, des cartes qui affichent des informations pertinentes et une barre de navigation pour vous permettre d’accéder facilement à diverses fonctionnalités et fonctionnalités.

:::image type="content" source="../../media/defender-business/mdb-portal-home.png" alt-text="Portail Microsoft 365 Defender":::

## <a name="the-navigation-bar"></a>Barre de navigation

Utilisez la barre de navigation sur le côté gauche de l’écran pour accéder à vos incidents, afficher les rapports et gérer vos stratégies de sécurité. Le tableau suivant décrit les éléments que vous verrez dans votre barre de navigation.

| Élément | Description |
|:---|:---|
| **Accueil** | Vous permet d’accéder à votre page d’accueil dans le portail Microsoft 365 Defender. La page d’accueil met en évidence toutes les menaces actives détectées, ainsi que des recommandations pour sécuriser les données et les appareils de votre entreprise. Les recommandations sont incluses dans Defender entreprise pour économiser du temps et des efforts de votre équipe de sécurité. Les recommandations sont basées sur les meilleures pratiques de l’industrie. Pour en savoir plus, consultez [recommandations de sécurité - Gestion des vulnérabilités Microsoft Defender](../defender-endpoint/tvm-security-recommendation.md). |
| **Incidents** | Vous permet d’accéder à votre liste d’incidents récents. Lorsque des alertes sont déclenchées, des incidents sont créés. Un incident peut inclure plusieurs alertes. Veillez à examiner régulièrement vos incidents. Pour plus d’informations, consultez [Afficher et gérer les incidents dans Defender entreprise](mdb-view-manage-incidents.md).|
| **Actions & soumissions** >  **Centre d’action** | Vous dirige vers votre liste d’actions de réponse, y compris les actions terminées et en attente.<br/>- Sélectionnez l’onglet **En attente** pour afficher les actions qui nécessitent une approbation pour continuer.<br/>- Sélectionnez l’onglet **Historique** pour voir les actions qui ont été effectuées. Certaines actions sont effectuées automatiquement ; d’autres sont prises manuellement ou terminées une fois qu’elles sont approuvées.<br/><br/>Pour plus d’informations, consultez [Examiner les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md). |
| **Actions & soumissions** >  **Soumissions** | Vous dirige vers le portail des soumissions unifiées, où vous pouvez envoyer des fichiers à Microsoft à des fins d’analyse. Pour plus d’informations, consultez [Envoyer des fichiers dans Microsoft Defender pour point de terminaison](../defender-endpoint/admin-submissions-mde.md) (le processus est similaire pour Defender entreprise). |
| **Analyses de menaces** | Vous permet d’obtenir une vue des menaces actuelles et fournit une vue d’ensemble de votre paysage de menaces. L’analytique des menaces inclut également des rapports et des informations provenant de chercheurs en sécurité Microsoft. Pour en savoir plus, consultez [Suivi et réponse aux menaces émergentes par le biais de l’analytique des menaces](../defender-endpoint/threat-analytics.md). |
| **Degré de sécurisation** | Fournit une représentation de la position de sécurité de votre entreprise et propose des suggestions pour l’améliorer. Pour plus d’informations, consultez [Le score de sécurité Microsoft pour les appareils](../defender-endpoint/tvm-microsoft-secure-score-devices.md). |
| **Hub d’apprentissage** | Fournit l’accès à la formation de sécurité et à d’autres ressources par le biais de parcours d’apprentissage inclus dans votre abonnement. Vous pouvez filtrer par produit, niveau de compétence, rôle, etc. Le hub d’apprentissage peut aider votre équipe de sécurité à se familiariser avec les fonctionnalités et fonctionnalités de sécurité dans Defender entreprise et d’autres offres Microsoft, telles que [Microsoft Defender pour point de terminaison](../defender-endpoint/microsoft-defender-endpoint.md) et [Microsoft Defender pour Office 365](../office-365-security/defender-for-office-365.md).  |
| **Essais** | Essayez des fonctionnalités de sécurité et de conformité supplémentaires en ajoutant un abonnement d’essai. Si vous ne voyez pas **d’essais** dans votre barre de navigation et que vous souhaitez ajouter une autre version d’évaluation, vous pouvez effectuer l’une des étapes suivantes : <br/>- Visitez la [page Solutions aux petites entreprises](https://www.microsoft.com/en-us/store/b/business?icid=CNavBusinessStore) et choisissez **Questions ? Contactez un expert** pour obtenir de l’aide sur l’ajout d’un abonnement d’essai. <br/>- Accédez à la [Centre d'administration Microsoft 365](https://admin.microsoft.com/?auth_upn=admin%40M365B614031.onmicrosoft.com&source=applauncher#/catalog) et choisissez Les **services d’achat** **de facturation** > . Si vous avez besoin d’aide, choisissez **Aide & support**.    |
| **Actifs** >  **Dispositifs** | Vous permet d’afficher les appareils, tels que les ordinateurs et les appareils mobiles inscrits dans [Microsoft Intune](/mem/intune/fundamentals/what-is-intune). |
| **Terminaison** >  **Gestion des vulnérabilités** | Vous permet d’accéder à vos fonctionnalités [de Gestion des vulnérabilités Microsoft Defender](../defender-vulnerability-management/defender-vulnerability-management.md). Fournit un tableau de bord, des recommandations, des activités de correction, un inventaire logiciel et une liste des faiblesses potentielles au sein de votre entreprise. |
| **Terminaison** >  **Tutoriels** | Fournit un accès aux procédures pas à pas et aux simulations pour vous aider à en savoir plus sur le fonctionnement de vos fonctionnalités de protection contre les menaces. Sélectionnez le lien **Lire la procédure pas à pas** avant de tenter d’obtenir le fichier de simulation pour chaque didacticiel. Certaines simulations nécessitent des applications Office, telles que Microsoft Word, pour lire la procédure pas à pas. |
| **Terminaison** >  **Gestion de la configuration** >  **Configuration de l’appareil** | Répertorie vos stratégies de sécurité par système d’exploitation et par type. Pour en savoir plus sur vos stratégies de sécurité, consultez [Afficher ou modifier des stratégies dans Defender entreprise](mdb-view-edit-policies.md). |
| **Terminaison** >  **Gestion de la configuration** >  **Rapports de gestion des appareils** | Répertorie les appareils qui sont intégrés à Defender entreprise, ainsi que leur version du système d’exploitation, leur état d’intégrité du capteur et la date de leur dernière mise à jour. |
| Email &**règles de & des stratégies de** **collaboration** >  | Si votre abonnement inclut Exchange Online Protection ou Microsoft Defender pour Office 365, cette section vous permet de gérer vos stratégies et paramètres de sécurité pour les services de messagerie et de collaboration. [En savoir plus sur Office 365 sécurité](../office-365-security/overview.md). *La version autonome de Defender entreprise n’inclut pas de stratégies de collaboration & par e-mail, mais Microsoft 365 Business Premium inclut Exchange Online Protection et Defender pour Office 365 Plan 1*. [Comparez les fonctionnalités de sécurité dans les plans de Microsoft 365 pour les petites et moyennes entreprises](compare-mdb-m365-plans.md).  |
| **Applications** >  cloud **Gouvernance des applications** | Si votre abonnement inclut [Microsoft Defender for Cloud Apps](/defender-cloud-apps/what-is-defender-for-cloud-apps), vous pouvez ajouter à la [gouvernance des applications](/defender-cloud-apps/app-governance-manage-app-governance), et cette section vous permet d’afficher et d’accéder à ces fonctionnalités. *Defender pour Entreprises et Microsoft 365 Business Premium n’incluent pas Defender pour Cloud Apps*. |
| **Rapports** | Répertorie les rapports de sécurité disponibles. Ces rapports vous permettent de voir vos tendances de sécurité, d’afficher des détails sur les détections de menaces et les alertes, et d’en savoir plus sur les appareils vulnérables de votre entreprise. |
| **État d'intégrité** | Vous permet d’afficher l’état d’intégrité de votre service et de planifier les modifications à venir. <br/>- Sélectionnez **État des services** pour afficher l’état d’intégrité des services Microsoft 365 inclus dans l’abonnement de votre entreprise.<br/>- Sélectionnez **Centre** de messages pour en savoir plus sur les modifications planifiées et ce à quoi vous devez vous attendre.  |
| **Autorisations** | Vous permet d’attribuer des autorisations aux personnes de votre entreprise qui gèrent votre sécurité et d’afficher les incidents et les rapports dans le portail Microsoft 365 Defender. Vous permet également de configurer et de gérer des groupes d’appareils pour intégrer les appareils de votre entreprise et d’attribuer des stratégies de protection contre les menaces.  |
| **Paramètres** | Vous permet de modifier les paramètres du portail Microsoft 365 Defender et de Defender entreprise. Par exemple, vous pouvez intégrer (ou déconnecter) les appareils de votre entreprise (également appelés points de terminaison). Vous pouvez également définir des règles, telles que des règles de suppression d’alerte, et configurer des indicateurs pour bloquer ou autoriser certains fichiers ou processus.  |
| **Autres ressources** | Accédez à d’autres portails, tels qu’Azure Active Directory. Toutefois, n’oubliez pas que le portail Microsoft 365 Defender doit répondre à vos besoins sans vous obliger à accéder à d’autres portails. |
| **Personnaliser votre volet de navigation** | Sélectionnez cette option pour masquer ou afficher les options dans votre barre de navigation. |

## <a name="next-steps"></a>Prochaines étapes

- [Utiliser l’Assistant Installation dans Defender entreprise](mdb-use-wizard.md)
- [Voir le processus d’installation et de configuration global](mdb-setup-configuration.md)