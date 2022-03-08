---
title: Commencer à utiliser le portail Microsoft 365 Defender web
description: Découvrez comment commencer à utiliser le portail Microsoft 365 Defender web. Découvrez comment naviguer dans le portail et afficher votre état de sécurité actuel et vos recommandations
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 267e293cf2a1d7b7755a58cddc7fb04af138e4ae
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329374"
---
# <a name="get-started-using-the-microsoft-365-defender-portal"></a>Commencer à utiliser le portail Microsoft 365 Defender web

> [!IMPORTANT]
> Microsoft Defender for Business est en déploiement Microsoft 365 Business Premium clients, à partir du 1er mars 2022. Defender for Business as a standalone subscription is in preview, and will roll out gradually to customers and IT Partners who [sign-up here](https://aka.ms/mdb-preview) to request it. La [prévisualisation inclut un ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Une fois que vous vous êtes inscrit à Microsoft Defender pour les entreprises, vous voudrez vous familiariser avec le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Le présent article contient les sections suivantes :

- [Navigation dans le portail Microsoft 365 Defender web](#navigate-the-microsoft-365-defender-portal)

- [Learning modules sur les incidents et les actions de réponse](#complete-a-learning-module-about-incidents-and-response-actions) 

- [Étapes suivantes](#next-steps)

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="navigate-the-microsoft-365-defender-portal"></a>Naviguer dans le Microsoft 365 Defender web

Le Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) est votre magasin unique pour l’utilisation et la gestion de Microsoft Defender pour les entreprises. Il inclut une bannière de bienvenue et des callouts pour vous aider à commencer, des cartes qui surfacent des informations pertinentes et une barre de navigation pour vous permettre d’accéder facilement aux différentes fonctionnalités et fonctionnalités.
 
Prenez le temps de vous familiariser avec votre portail Microsoft 365 Defender web.

:::image type="content" source="../../media/defender-business/mdb-portal-home.png" alt-text="Portail Microsoft 365 Defender":::

### <a name="use-the-navigation-bar"></a>Utiliser la barre de navigation

Utilisez la barre de navigation sur le côté gauche de l’écran pour accéder à vos incidents, afficher les rapports et gérer vos stratégies de sécurité. Le tableau suivant décrit les éléments que vous verrez dans votre barre de navigation.

| Élément | Description |
|:---|:---|
| **Accueil** | Vous prend à votre page d’accueil dans Microsoft 365 Defender. La page d’accueil inclut des cartes qui mettent en évidence les menaces actives détectées, ainsi que des recommandations pour sécuriser les données et les appareils de votre organisation. <br/><br/>Recommandations sont inclus dans Defender for Business peut économiser du temps et des efforts pour votre équipe de sécurité. Recommandations sont basées sur les meilleures pratiques du secteur. Pour en savoir plus sur les recommandations, voir [Recommandations en](../defender-endpoint/tvm-security-recommendation.md) matière de sécurité - Gestion des menaces et des vulnérabilités. |
| **Incidents** | Vous permet d’avoir accès à votre liste des incidents récents. Lorsque des alertes sont déclenchées, des incidents sont créés. Un incident peut inclure plusieurs alertes. Veillez à passer régulièrement en revue vos incidents. <br/><br/>Pour en savoir plus sur les incidents, voir [Afficher et gérer les incidents dans Microsoft Defender pour Les entreprises](mdb-view-manage-incidents.md).|
| **Centre de notifications** | Vous place dans votre liste d’actions de réponse, y compris les actions terminées ou en attente. <br/>- Sélectionnez **l’onglet** Historique pour voir les actions qui ont été entreprises. Certaines actions sont prises automatiquement ; d’autres sont prises manuellement ou se terminent après leur approbation. <br/>- Sélectionnez **l’onglet En** attente pour afficher les actions qui nécessitent une approbation pour continuer. <br/><br/>Pour en savoir plus sur le centre de traitement des actions, consultez [La révision des actions de correction dans le centre de actions](mdb-review-remediation-actions.md). |
| **Analyses de menaces** | Vous donne un aperçu des menaces actuelles et vous offre une vue d’un coup d’œil de votre paysage des menaces. L’analyse des menaces inclut également des rapports et des informations de chercheurs en matière de sécurité Microsoft. <br/><br/>Pour en savoir plus sur l’analyse des menaces, voir [Suivre et répondre aux menaces émergentes par le biais de l’analyse des menaces](../defender-endpoint/threat-analytics.md). |
| **Degré de sécurisation** | Fournit une représentation de la position de sécurité de votre organisation et propose des suggestions pour l’améliorer.<br/><br/>Pour en savoir plus sur le score de sécurisation, voir [Le Score de sécurisation Microsoft pour les appareils](../defender-endpoint/tvm-microsoft-secure-score-devices.md). |
| **Learning hub** | Permet d’accéder à des formations sur la sécurité et à d’autres ressources par le biais de parcours d’apprentissage inclus dans votre abonnement. Vous pouvez filtrer par produit, niveau de compétence, rôle, etc. Le hub Learning peut aider votre équipe de sécurité à se développer sur les fonctionnalités de sécurité & fonctionnalités dans Defender pour Entreprise et d’autres offres Microsoft, telles que [Microsoft Defender pour Point](../defender-endpoint/microsoft-defender-endpoint.md) de terminaison et [Microsoft Defender pour Office 365](../office-365-security/defender-for-office-365.md).  |
| **Points de terminaison** >  **Recherche** | Vous permet de rechercher un ou plusieurs appareils qui ont été intégrés à Microsoft Defender pour Entreprises. |
| **Points de terminaison** >  **Inventaire des appareils** | Vous permet de rechercher un ou plusieurs appareils qui ont été intégrés à Microsoft Defender pour Entreprises. |
| **Points de terminaison** >  **Gestion des vulnérabilités** | Fournit un tableau de bord, des recommandations, des activités de correction, un inventaire logiciel et une liste des faiblesses potentielles au sein de votre organisation. |
| **Points de terminaison** >  **Didacticiels** | Permet d’accéder à des walkthroughs et des simulations pour vous aider à en savoir plus sur le fonctionnement de vos fonctionnalités de protection contre les menaces. <br/><br/>Sélectionnez **le lien Lire la walkthrough** avant d’essayer d’obtenir le fichier de simulation pour chaque didacticiel. Certaines simulations nécessitent Office applications, telles que Microsoft Word, pour lire la walkthrough. |
| **Points de terminaison** >  **Configuration de l’appareil** | Répertorie vos stratégies de sécurité par système d’exploitation et par type. <br/><br/>Pour en savoir plus sur vos stratégies de sécurité, voir Afficher ou modifier des stratégies [dans Microsoft Defender entreprise](mdb-view-edit-policies.md). |
| **Rapports** | Répertorie vos rapports de sécurité disponibles. Ces rapports vous permettent d’afficher vos tendances de sécurité, d’afficher des détails sur les détections de menaces et les alertes, et d’en savoir plus sur les appareils vulnérables de votre organisation. |
| **État d'intégrité** | Vous permet d’afficher l’état d’état de votre service et de planifier les modifications à venir. <br/>- Sélectionnez **l’état du** service pour afficher l’état d’Microsoft 365 services inclus dans l’abonnement de votre organisation. <br/>- **Sélectionnez centre de messages** pour en savoir plus sur les modifications planifiées et à quoi s’attendre.  |
| **Autorisations & rôles** | Vous permet d’attribuer des autorisations aux personnes de votre organisation qui gèreront votre sécurité et afficheront les incidents et les rapports dans le portail Microsoft 365 Defender. Vous permet également de configurer et de gérer des groupes d’appareils pour intégrer les appareils de votre organisation et d’affecter vos stratégies de protection contre les menaces.  |
| **Settings** | Permet de modifier les paramètres du portail Microsoft 365 Defender microsoft Defender pour entreprises. Par exemple, vous pouvez intégrer (ou hors-carte) et les appareils de votre organisation (également appelés points de terminaison). Vous pouvez également définir des règles, telles que des règles de suppression des alertes, et configurer des indicateurs pour bloquer ou autoriser certains fichiers ou processus.  |
| **Autres ressources** | Accédez à d’autres portails, tels que Azure Active Directory. N’oubliez pas que le Microsoft 365 Defender web doit répondre à vos besoins sans que vous n’exigeiez que vous accédiez à d’autres portails. |

## <a name="complete-a-learning-module-about-incidents-and-response-actions"></a>Compléter un module d’apprentissage sur les incidents et les actions de réponse

Consultez le module d’apprentissage, Détecter et répondre aux problèmes [de sécurité](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/), pour obtenir une vue d’ensemble des incidents et des actions de réponse. Vous découvrirez la file d’attente des incidents, les alertes et les actions de réponse que vous pouvez prendre. Ce cours vous aidera à commencer à travailler avec les incidents dans Defender for Business.

> [!NOTE]
> Bien que le module d’apprentissage (Détecter et répondre aux problèmes de sécurité) soit en fait pour Microsoft Defender pour Endpoint, les concepts de base et le flux global sont [similaires](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/) à ce que vous verrez dans Defender pour Entreprise.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez une vue d’ensemble de Defender for Business, essayez une ou plusieurs des tâches suivantes :

- [Essayer des didacticiels et des simulations dans Microsoft Defender entreprise](mdb-tutorials.md)

- [Gérer les appareils dans Microsoft Defender pour les entreprises](mdb-manage-devices.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)

- [Afficher ou modifier des stratégies dans Microsoft Defender entreprise](mdb-view-edit-policies.md)