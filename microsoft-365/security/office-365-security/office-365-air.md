---
title: Enquêter et répondre automatiquement aux menaces dans Office 365
keywords: AIR, autoIR, ATP, automatisation, analyse, réponse, correction, menaces, avancé, menace, protection
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: Prise en main des fonctionnalités d’analyse et de réponse automatisées dans Office 365 Advanced Threat Protection Plan 2.
ms.openlocfilehash: 9c17d7219e5dd15404b171fbd6707d00fd788f19
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41598761"
---
# <a name="automatically-investigate-and-respond-to-threats-in-office-365"></a>Enquêter et répondre automatiquement aux menaces dans Office 365

## <a name="overview"></a>Vue d’ensemble

En fonction de votre abonnement, [Office 365 protection avancée contre les menaces](office-365-atp.md) peut inclure des fonctionnalités d’analyse et de réponse automatisées (air) qui permettent d’économiser le temps et les efforts de l’équipe des opérations de sécurité pour traiter les alertes et les menaces.

- Pour commencer à utiliser les fonctionnalités d’analyse et de réponse automatisées dans Office 365, utilisez cet article. 
- Pour obtenir une vue d’ensemble du fonctionnement, voir [Automated Investigation and Response in Office 365](automated-investigation-response-office.md).

> [!TIP]
> Avez-vous Microsoft 365 E5 ou Microsoft 365 E3 conjointement avec identité et protection contre les menaces ? Envisagez [d’essayer l’automatisation des recherches et de la réponse (air) dans la protection contre les menaces Microsoft](../mtp/mtp-autoir.md).

Avec des fonctionnalités d’analyse et de réponse automatisées, lorsque certaines alertes sont déclenchées, un ou plusieurs règles de sécurité se déclenchent et le processus d’enquête automatisé commence. Pendant et après un processus d’enquête automatisé, votre équipe de sécurité peut effectuer les opérations suivantes :

- [Afficher les détails d’une enquête](#view-details-of-an-investigation)
- [Passer en revue et approuver les actions à la suite d’une enquête](#review-and-approve-actions) 
- [Afficher les détails d’une alerte liée à une enquête](#view-details-about-an-alert-related-to-an-investigation)

> [!IMPORTANT]
> Pour effectuer les tâches décrites dans cet article, vous devez disposer des autorisations appropriées. Consultez la rubrique [Required Permissions to use air Capabilities](automated-investigation-response-office.md#required-permissions-to-use-air-capabilities).

## <a name="view-details-of-an-investigation"></a>Afficher les détails d’une enquête

1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous. Cette opération vous permet d’accéder au centre de sécurité & conformité.

2. Effectuez l’une des opérations suivantes :

    - Accédez au **** > **tableau de bord**gestion des menaces. Cela vous amène au [tableau de bord de sécurité](security-dashboard.md). Vos widgets d’AIR s’affichent dans la partie supérieure du [tableau de bord de sécurité](security-dashboard.md). Sélectionnez un widget, par exemple, **Résumé des enquêtes**.

    - Accédez aux **** > **enquêtes**de gestion des menaces. 

    L’une ou l’autre de ces méthodes vous permet d’accéder à une liste d’investigations.

    ![Page d’enquête principale pour l’AIR](../media/air-maininvestigationpage.png) 

3. Dans la liste des enquêtes, sélectionnez un élément dans la colonne **ID** . Cette action ouvre la page des détails de l’enquête, en commençant par le graphique d’enquête dans l’affichage.

    ![Page graphique d’enquête sur l’AIR](../media/air-investigationgraphpage.png)

4. Utilisez les différents onglets pour en savoir plus sur l’enquête.

## <a name="review-and-approve-actions"></a>Vérifier et approuver des actions

Dans Office 365, les analyses automatiques entraînent généralement une ou plusieurs actions recommandées. Toutefois, aucune action n’est effectuée tant qu’elles n’ont pas été approuvées par votre équipe des opérations de sécurité. Utilisez la procédure suivante pour passer en revue et approuver les actions.

1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous. 

2. Accédez aux **** > **enquêtes**de gestion des menaces.

3. Dans la liste des enquêtes, sélectionnez un élément dans la colonne **ID** . 

3. Dans l’affichage Détails de l’enquête, sélectionnez l’onglet **actions** . Toutes les actions en attente d’approbation sont répertoriées ici.

4. Sélectionnez un élément dans la liste.

5. Sélectionnez **approuver** pour prendre l’action recommandée (ou **rejeter** pour fermer l’enquête sans entreprendre d’action).

## <a name="view-details-about-an-alert-related-to-an-investigation"></a>Afficher les détails d’une alerte liée à une enquête

Certains types d’alertes déclenchent une enquête automatisée dans Office 365. Pour en savoir plus, consultez la rubrique [alertes](automated-investigation-response-office.md#alerts). Utilisez la procédure suivante pour afficher les détails d’une alerte associée à une enquête automatisée.

1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous. Cette opération vous permet d’accéder au centre de sécurité & conformité.

2. Accédez aux **** > **enquêtes**de gestion des menaces.

3. Dans la liste des enquêtes, sélectionnez un élément dans la colonne **ID** . 

4. Les détails d’une enquête étant ouverts, sélectionnez l’onglet **alertes** . Les alertes qui ont déclenché l’enquête sont répertoriées ici.

5. Sélectionnez un élément dans la liste. Un menu volant s’ouvre, avec des détails sur l’alerte et des liens vers des informations et des actions supplémentaires.

6. Passez en revue les informations de la fenêtre mobile et, en fonction de l’alerte en particulier, effectuez une action, telle que **résoudre**, **supprimer**ou **avertir les utilisateurs**. 

    - La **résolution** équivaut à la fermeture d’une alerte
    
    - La **suppression** entraîne le déclenchement d’alertes par une stratégie pendant une période de temps spécifiée.
    
    - **Avertir les utilisateurs** de l’envoi d’un courrier électronique avec les adresses de messagerie des utilisateurs déjà entrées, et permet à l’équipe des opérations de sécurité de taper un message pour ces utilisateurs. (Ceci est similaire à l’envoi d’un message à des destinataires à l’aide de l' [Explorateur de menaces](threat-explorer.md).)  

## <a name="use-the-office-365-management-activity-api-for-custom-or-third-party-reporting-solutions"></a>Utiliser l’API activité de gestion d’Office 365 pour des solutions de création de rapports personnalisées ou tierces

Si votre organisation utilise une solution de création de rapports personnalisée ou tierce, vous pouvez afficher des informations sur les analyses automatisées dans cette solution à l’aide de l’API activité de gestion d’Office 365.

Pour ce faire, utilisez les ressources suivantes :

|Resource  |Description  |
|---------|---------|
|[Vue d’ensemble des API de gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview)     |L’API Activité de gestion Office 365 fournit des informations sur diverses actions et événements d’utilisateur, d’administrateur, de système et de stratégie à partir des journaux d’activité Office 365 et Azure Active Directory.         |
|[Prise en main des API de gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/get-started-with-office-365-management-apis)     |L’API de gestion d’Office 365 utilise Azure AD pour fournir des services d’authentification à votre application pour accéder aux données d’Office 365. Suivez les étapes décrites dans cet article pour le configurer.          |
|[Référence de l’API Activité de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference)     |Vous pouvez utiliser l’API activité de gestion d’Office 365 pour récupérer des informations sur les actions et événements d’utilisateur, d’administrateur, de système et de stratégie à partir des journaux d’activité Office 365 et Azure AD. Lisez cet article pour en savoir plus sur le fonctionnement de cette procédure.        |
|[Schéma de l’API Activité de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema)     |Pour en savoir plus sur des types de données spécifiques disponibles via l’API activité de gestion Office 365, consultez le schéma [commun](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) et le schéma d’enquête et de [réponse aux menaces Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema) .         |

## <a name="next-steps"></a>Étapes suivantes

- [Découvrez comment obtenir de l’AIR et voir les autorisations requises](automated-investigation-response-office.md#how-to-get-air)
- [En savoir plus sur les alertes](../../compliance/alert-policies.md)
- [Rechercher et identifier manuellement les messages électroniques malveillants remis dans Office 365](investigate-malicious-email-that-was-delivered.md)
- [En savoir plus sur AIR dans Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)
- [Consultez la feuille de route Microsoft 365 pour découvrir les éléments bientôt disponibles et à déployer](https://www.microsoft.com/microsoft-365/roadmap?filters=)