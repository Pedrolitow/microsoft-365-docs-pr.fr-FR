---
title: Démarrage à l’aide du portail Microsoft 365 Defender
description: Découvrez comment commencer à utiliser le portail Microsoft 365 Defender. Découvrez comment naviguer dans le portail et afficher l’état et les recommandations de sécurité actuels
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: c5a940676eab6ae3a07c526ecb1bd910ed8751fe
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667139"
---
# <a name="get-started-using-the-microsoft-365-defender-portal"></a>Démarrage à l’aide du portail Microsoft 365 Defender

> [!IMPORTANT]
> Microsoft Defender pour les PME est déployée pour [Microsoft 365 Business Premium](../../business-premium/index.md) clients, à compter du 1er mars 2022. Defender entreprise en tant qu’abonnement autonome est en préversion et sera déployé progressivement pour les clients et les partenaires informatiques qui [s’inscrivent ici](https://aka.ms/mdb-preview) pour le demander. La préversion inclut un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios), et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations contenues dans cet article concernent des produits/services prédéfinis qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expresse ou implicite, pour les informations fournies ici. 

Une fois que vous êtes inscrit à Microsoft Defender pour les PME, vous devez vous familiariser avec le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Le présent article contient les sections suivantes :

- [Guide pratique pour naviguer dans le portail Microsoft 365 Defender](#navigate-the-microsoft-365-defender-portal)

- [Learning modules sur les incidents et les actions de réponse](#complete-a-learning-module-about-incidents-and-response-actions) 

- [Étapes suivantes](#next-steps)

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">court sondage sur Microsoft Defender pour les PME</a>. Vos commentaires sont les bienvenus.
>

## <a name="navigate-the-microsoft-365-defender-portal"></a>Naviguer dans le portail Microsoft 365 Defender

Le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) est votre magasin unique pour l’utilisation et la gestion des Microsoft Defender pour les PME. Il comprend une bannière d’accueil et des légendes pour vous aider à commencer, des cartes qui affichent des informations pertinentes et une barre de navigation pour vous permettre d’accéder facilement aux différentes fonctionnalités.
 
Prenez un moment pour vous familiariser avec votre portail Microsoft 365 Defender.

:::image type="content" source="../../media/defender-business/mdb-portal-home.png" alt-text="Portail Microsoft 365 Defender":::

### <a name="use-the-navigation-bar"></a>Utiliser la barre de navigation

Utilisez la barre de navigation sur le côté gauche de l’écran pour accéder à vos incidents, afficher les rapports et gérer vos stratégies de sécurité. Le tableau suivant décrit les éléments que vous verrez dans votre barre de navigation.

| Item | Description |
|:---|:---|
| **Accueil** | Vous permet d’accéder à votre page d’accueil dans Microsoft 365 Defender. La page d’accueil inclut des cartes qui mettent en évidence les menaces actives détectées, ainsi que des recommandations pour sécuriser les données et les appareils de votre entreprise. <br/><br/>Recommandations sont inclus dans Defender entreprise, cela peut faire gagner du temps et des efforts à votre équipe de sécurité. Recommandations sont basées sur les meilleures pratiques de l’industrie. Pour en savoir plus sur les recommandations, consultez [Recommandations de sécurité - Gestion des menaces et des vulnérabilités](../defender-endpoint/tvm-security-recommendation.md). |
| **Incidents** | Vous permet d’accéder à votre liste d’incidents récents. Lorsque des alertes sont déclenchées, des incidents sont créés. Un incident peut inclure plusieurs alertes. Veillez à examiner régulièrement vos incidents. <br/><br/>Pour en savoir plus sur les incidents, consultez [Afficher et gérer les incidents dans Microsoft Defender pour les PME](mdb-view-manage-incidents.md).|
| **Centre de notifications** | Vous dirige vers votre liste d’actions de réponse, y compris les actions terminées ou en attente. <br/>- Sélectionnez l’onglet **Historique** pour voir les actions qui ont été effectuées. Certaines actions sont effectuées automatiquement ; d’autres sont prises manuellement ou terminées une fois qu’elles sont approuvées. <br/>- Sélectionnez l’onglet **En attente** pour afficher les actions qui nécessitent une approbation pour continuer. <br/><br/>Pour en savoir plus sur le Centre d’actions, consultez [Examiner les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md). |
| **Analyses de menaces** | Vous permet d’afficher les menaces actuelles et vous offre une vue d’ensemble de votre paysage de menaces. L’analytique des menaces inclut également des rapports et des informations provenant de chercheurs en sécurité Microsoft. <br/><br/>Pour en savoir plus sur l’analyse des menaces, consultez [Suivi et réponse aux menaces émergentes par le biais de l’analytique des menaces](../defender-endpoint/threat-analytics.md). |
| **Degré de sécurisation** | Fournit une représentation de la position de sécurité de votre entreprise et propose des suggestions pour l’améliorer.<br/><br/>Pour en savoir plus sur le degré de sécurisation, consultez [Score de sécurité Microsoft pour les appareils](../defender-endpoint/tvm-microsoft-secure-score-devices.md). |
| **hub Learning** | Fournit l’accès à la formation de sécurité et à d’autres ressources par le biais de parcours d’apprentissage inclus dans votre abonnement. Vous pouvez filtrer par produit, niveau de compétence, rôle, etc. Le hub Learning peut aider votre équipe de sécurité à s’intensifier sur les fonctionnalités de sécurité & fonctionnalités dans Defender entreprise et d’autres offres Microsoft, telles que [Microsoft Defender pour point de terminaison](../defender-endpoint/microsoft-defender-endpoint.md) et [Microsoft Defender pour Office 365](../office-365-security/defender-for-office-365.md).  |
| **Terminaison** >  **Rechercher** | Vous permet de rechercher un ou plusieurs appareils qui ont été intégrés à Microsoft Defender pour les PME. |
| **Terminaison** >  **Inventaire des appareils** | Vous permet de rechercher un ou plusieurs appareils qui ont été intégrés à Microsoft Defender pour les PME. |
| **Terminaison** >  **Gestion des vulnérabilités** | Fournit un tableau de bord, des recommandations, des activités de correction, un inventaire logiciel et une liste des faiblesses potentielles au sein de votre entreprise. |
| **Terminaison** >  **Tutoriels** | Fournit un accès aux procédures pas à pas et aux simulations pour vous aider à en savoir plus sur le fonctionnement de vos fonctionnalités de protection contre les menaces. <br/><br/>Sélectionnez le lien **Lire la procédure pas à pas** avant de tenter d’obtenir le fichier de simulation pour chaque didacticiel. Certaines simulations nécessitent Office applications, telles que Microsoft Word, pour lire la procédure pas à pas. |
| **Terminaison** >  **Configuration de l’appareil** | Répertorie vos stratégies de sécurité par système d’exploitation et par type. <br/><br/>Pour en savoir plus sur vos stratégies de sécurité, consultez [Afficher ou modifier des stratégies dans Microsoft Defender pour les PME](mdb-view-edit-policies.md). |
| **Rapports** | Répertorie vos rapports de sécurité disponibles. Ces rapports vous permettent de voir vos tendances de sécurité, d’afficher des détails sur les détections de menaces et les alertes, et d’en savoir plus sur les appareils vulnérables de votre entreprise. |
| **État d'intégrité** | Vous permet d’afficher l’état d’intégrité de votre service et de planifier les modifications à venir. <br/>- Sélectionnez **État des services** pour afficher l’état d’intégrité des services Microsoft 365 inclus dans l’abonnement de votre entreprise. <br/>- Sélectionnez **Centre** de messages pour en savoir plus sur les modifications planifiées et ce à quoi vous devez vous attendre.  |
| **Autorisations & rôles** | Vous permet d’attribuer des autorisations aux personnes de votre entreprise qui gèreront votre sécurité et afficheront les incidents et les rapports dans le portail Microsoft 365 Defender. Vous permet également de configurer et de gérer des groupes d’appareils pour intégrer les appareils de votre entreprise et d’affecter vos stratégies de protection contre les menaces.  |
| **Settings** | Vous permet de modifier les paramètres du portail Microsoft 365 Defender et des Microsoft Defender pour les PME. Par exemple, vous pouvez intégrer (ou déconnecter) les appareils de votre entreprise (également appelés points de terminaison). Vous pouvez également définir des règles, telles que des règles de suppression d’alerte, et configurer des indicateurs pour bloquer ou autoriser certains fichiers ou processus.  |
| **Autres ressources** | Accédez à d’autres portails, tels que Azure Active Directory. N’oubliez pas que le portail Microsoft 365 Defender doit répondre à vos besoins sans vous obliger à accéder à d’autres portails. |

## <a name="complete-a-learning-module-about-incidents-and-response-actions"></a>Terminer un module d’apprentissage sur les incidents et les actions de réponse

Consultez le module d’apprentissage, [Détecter et répondre aux problèmes de sécurité](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/) pour obtenir une vue d’ensemble des incidents et des actions de réponse. Vous allez découvrir la file d’attente d’incidents, les alertes et les actions de réponse que vous pouvez effectuer. Ce cours vous aidera à commencer à utiliser les incidents dans Defender entreprise.

> [!NOTE]
> Bien que le module d’apprentissage ([détecter et répondre aux problèmes de sécurité](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/)) soit en fait destiné à Microsoft Defender pour point de terminaison, les concepts de base et le flux global sont similaires à ce que vous verrez dans Defender entreprise.

## <a name="next-steps"></a>Prochaines étapes

Maintenant que vous disposez d’une vue d’ensemble de Defender entreprise, essayez une ou plusieurs des tâches suivantes :

- [Essayer des didacticiels et des simulations dans Microsoft Defender pour les PME](mdb-tutorials.md)

- [Gérer les appareils dans Microsoft Defender pour les PME](mdb-manage-devices.md)

- [Afficher et gérer les incidents dans Microsoft Defender pour les PME](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender pour les PME](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)

- [Afficher ou modifier des stratégies dans Microsoft Defender pour les PME](mdb-view-edit-policies.md)