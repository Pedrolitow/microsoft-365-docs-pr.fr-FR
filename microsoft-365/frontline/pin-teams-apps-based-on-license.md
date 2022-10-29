---
title: Personnaliser les applications Teams pour vos employés de première ligne
author: LanaChin
ms.author: v-lanachin
ms.reviewer: aaglick
manager: samanro
ms.topic: how-to
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez l’expérience d’application personnalisée pour les employés de première ligne dans Microsoft Teams.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
- highpri
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 26f8039eb5160ea7555a53abe73c14e2cc3dfa1c
ms.sourcegitcommit: 0ad7edcfdcdd11d02fa8a14ffe4b36e120d92deb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2022
ms.locfileid: "68786318"
---
# <a name="tailor-teams-apps-for-your-frontline-workers"></a>Personnaliser les applications Teams pour vos employés de première ligne

## <a name="overview"></a>Vue d’ensemble

Teams épingle des applications basées sur une licence pour offrir à vos employés de première ligne une expérience tout à fait adaptée à leurs besoins dans Teams. 

Avec l’expérience d’application de première ligne personnalisée, vos employés de première ligne obtiennent les applications les plus pertinentes dans Teams sans aucune action nécessaire de la part de l’administrateur.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4VuCH]

## <a name="tailored-frontline-app-experience"></a>Expérience d’application de première ligne personnalisée

Les applications sont épinglées à la barre des applications. Il s’agit de la barre située sur le côté du client de bureau Teams et en bas des clients mobiles Teams (iOS et Android). Les applications suivantes sont épinglées pour les utilisateurs disposant d’une [licence F](https://www.microsoft.com/microsoft-365/enterprise/frontline#office-SKUChooser-0dbn8nt) :

- [Viva Connections](https://support.microsoft.com/office/your-intranet-is-now-in-microsoft-teams-8b4e7f76-f305-49a9-b6d2-09378476f95b) ([bientôt disponible](#coming-soon))
- [Activité](https://support.microsoft.com/office/explore-the-activity-feed-in-teams-91c635a1-644a-4c60-9c98-233db3e13a56)
- [Conversation](https://support.microsoft.com/office/get-started-with-chat-0b506ce2-eb6d-4fca-9668-e56980ba755e)
- [Teams](https://support.microsoft.com/office/teams-and-channels-in-microsoft-teams-c6d0e61d-a61e-44a6-a972-04f2a8fa4155)
- [Talkie-walkie](https://support.microsoft.com/office/get-started-with-teams-walkie-talkie-25bdc3d5-bbb2-41b7-89bf-650fae0c8e0c)
- [Tâches](https://support.microsoft.com/office/use-the-tasks-app-in-teams-e32639f3-2e07-4b62-9a8c-fd706c12c070)
- [Shifts](https://support.microsoft.com/office/what-is-shifts-f8efe6e4-ddb3-4d23-b81b-bb812296b821)
- [Approbations](https://support.microsoft.com/office/what-is-approvals-a9a01c95-e0bf-4d20-9ada-f7be3fc283d3)

**Teams Mobile**

:::image type="content" source="media/tailored-teams-apps-mobile.png" alt-text="Expérience d’application de première ligne personnalisée sur Teams mobile" lightbox="media/tailored-teams-apps-mobile.png"::: 

**Bureau Teams**

:::image type="content" source="media/tailored-teams-apps-desktop.png" alt-text="Expérience d’application de première ligne personnalisée sur le bureau Teams" lightbox="media/tailored-teams-apps-desktop.png"::: 

## <a name="admin-controls"></a>Contrôles d’administration

> [!NOTE]
> Le paramètre **d’épinglage utilisateur** doit être activé dans la [stratégie d’installation d’application](/microsoftteams/teams-app-setup-policies) globale (par défaut à l’échelle de l’organisation) pour que cette fonctionnalité prenne effet.

L’expérience d’application de première ligne personnalisée est contrôlée par le paramètre **Afficher les applications personnalisées** à l’échelle de l’organisation sur la page [Gérer les applications](/microsoftteams/manage-apps#manage-org-wide-app-settings) du Centre d’administration Teams. Si la fonctionnalité est activée, tous les utilisateurs de votre organisation qui disposent d’une licence F bénéficieront de l’expérience d’application personnalisée.

N’oubliez pas que toutes les [stratégies d’installation d’application](/microsoftteams/teams-app-setup-policies) personnalisées affectées aux utilisateurs sont prioritaires. Cela signifie que si une stratégie d’installation d’application personnalisée lui est déjà affectée, l’utilisateur obtient la configuration définie dans la stratégie d’installation d’application personnalisée. Pour en savoir plus sur le fonctionnement de la fonctionnalité avec les stratégies d’application Teams, notamment la stratégie d’installation d’application globale, consultez la section [Scénarios](#scenarios) plus loin dans cet article.

Cette fonctionnalité est activée par défaut. Toutefois, si vous ne souhaitez pas utiliser l’expérience d’application de première ligne personnalisée fournie par Microsoft, vous pouvez désactiver la fonctionnalité. Pour désactiver ou activer la fonctionnalité :

1. Dans le volet de navigation gauche du Centre d’administration Microsoft Teams, accédez à **Applications Teams** > **Gérer les applications**, puis sélectionnez **Paramètres d’application à l’échelle de l’organisation**.
2. Sous **Applications personnalisées**, **activez** ou **désactivez** l’option **Afficher les applications personnalisées**.

    :::image type="content" source="media/tailored-teams-apps-admin-center.png" alt-text="Capture d’écran du paramètre Afficher les applications personnalisées sur la page Gérer les applications du Centre d’administration Teams" lightbox="media/tailored-teams-apps-admin-center.png":::

## <a name="scenarios"></a>Scénarios

### <a name="how-does-the-tailored-frontline-app-experience-affect-my-global-app-setup-policy"></a>Comment l’expérience d’application de première ligne personnalisée affecte-t-elle ma stratégie d’installation d’application globale ?

Découvrez comment l’expérience d’application de première ligne personnalisée fonctionne avec la stratégie d’installation d’application globale. Les scénarios de ce tableau s’appliquent aux travailleurs de première ligne qui disposent d’une licence F et de la stratégie globale d’installation de l’application, avec **l’épinglage utilisateur** activé.

|Si... |Alors... |
|---------|---------|
|Un employé de première ligne a la stratégie d’installation d’application globale et la fonctionnalité est désactivée. |L’employé de première ligne obtient les applications définies dans la stratégie d’installation d’application globale.|
|Un employé de première ligne a la stratégie d’installation d’application globale et la fonctionnalité est activée.     | L’employé de première ligne obtient l’expérience d’application de première ligne personnalisée. Les applications définies dans la stratégie globale d’installation des applications sont épinglées sous les applications personnalisées.      |
|Vous mettez à jour la stratégie d’installation de l’application globale et la fonctionnalité est activée.     |L’employé de première ligne obtient l’expérience d’application de première ligne personnalisée et les applications définies dans la stratégie globale d’installation des applications sont épinglées sous les applications personnalisées.         |
|Un employé de première ligne a la stratégie d’installation d’application globale et **l’épinglage utilisateur** est désactivé. |L’employé de première ligne obtient les applications définies dans la stratégie d’installation d’application globale.|
|Un employé de première ligne a la stratégie d’installation d’application globale, et la stratégie d’installation d’application globale est modifiée pour inclure une application métier à la deuxième position dans la liste des applications. |L’application métier est épinglée sous les applications personnalisées. L’employé de première ligne peut modifier l’ordre de l’application si **l’épinglage de l’utilisateur** est activé.         |
|Un employé de première ligne a la stratégie d’installation globale et la stratégie d’installation d’application globale est modifiée pour inclure Shifts en première position.  |Les décalages sont épinglés à la sixième position, comme défini par l’expérience d’application de première ligne personnalisée. L’employé de première ligne peut modifier l’ordre de l’application si **l’épinglage de l’utilisateur** est activé.          |

### <a name="how-does-the-tailored-frontline-app-experience-work-with-other-teams-app-policies"></a>Comment l’expérience d’application de première ligne personnalisée fonctionne-t-elle avec d’autres stratégies d’application Teams ?

Découvrez comment l’expérience d’application de première ligne personnalisée fonctionne avec d’autres stratégies d’application Teams.

|Si...  |Alors... |
|---------|---------|
La fonctionnalité est désactivée.   | L’employé de première ligne obtient les applications définies dans la stratégie d’installation d’application globale ou la stratégie d’installation d’application personnalisée qui leur est affectée.          |
|Un employé de première ligne a une stratégie de configuration d’application personnalisée et la fonctionnalité est activée.    |L’employé de première ligne obtient les applications définies dans la stratégie d’installation d’application personnalisée.          |
|Une application dans l’expérience d’application de première ligne personnalisée est bloquée pour un utilisateur ou pour votre organisation.      |L’expérience d’application de première ligne personnalisée respecte la [stratégie d’autorisation de l’application](/microsoftteams/teams-app-permission-policies). Si une application est bloquée, l’employé de première ligne ne voit pas l’application bloquée.           |
|Une application dans l’expérience d’application de première ligne personnalisée est déjà définie dans une stratégie d’installation d’application et la fonctionnalité est activée. |L’application est épinglée en fonction de l’ordre défini par la liste des applications personnalisées.        |
|Un utilisateur dispose d’une licence E, A ou G et la fonctionnalité est activée.   | L’utilisateur n’obtient pas l’expérience d’application de première ligne personnalisée. Actuellement, l’expérience s’applique uniquement aux utilisateurs disposant d’une licence F.        |

> [!NOTE]
> Vous ne pouvez pas modifier les applications ou l’ordre des applications dans l’expérience d’application de première ligne personnalisée. Pour l’instant, si vous souhaitez apporter des modifications, vous pouvez configurer votre propre expérience personnalisée. Pour ce faire, commencez par désactiver la fonctionnalité. Ensuite, [créez une stratégie d’installation d’application personnalisée](/microsoftteams/teams-app-setup-policies) et [attribuez-la à des utilisateurs ou des groupes](/microsoftteams/assign-policies-users-and-groups).

### <a name="coming-soon"></a>Bientôt disponible

 Viva Connections fera bientôt partie de l’expérience des applications personnalisées de première ligne. Les utilisateurs de première ligne qui voient l’expérience d’application personnalisée auront Viva Connections épinglées en première position sur les appareils mobiles et les ordinateurs de bureau.

Cette expérience inclut un tableau de bord par défaut avec des cartes de première ligne pertinentes, telles que Tâches, Shifts, Approbations et Top News, qui peuvent être personnalisées pour répondre aux besoins de votre organisation. Si votre organisation a déjà configuré un site d’accueil Viva Connections, il est prioritaire sur l’expérience par défaut. Pour en savoir plus, consultez la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=99706).

**Teams Mobile**

:::image type="content" source="media/tailored-teams-apps-viva-connections-mobile.png" alt-text="Capture d’écran montrant Viva Connections dans l’expérience d’application de première ligne personnalisée sur les appareils mobiles Teams." lightbox="media/tailored-teams-apps-viva-connections-mobile.png":::

**Bureau Teams**

:::image type="content" source="media/tailored-teams-apps-viva-connections-desktop.png" alt-text="Capture d’écran montrant Viva Connections dans l’expérience d’application de première ligne personnalisée sur le bureau Teams." lightbox="media/tailored-teams-apps-viva-connections-desktop.png":::

## <a name="related-articles"></a>Articles connexes

- [Gérer l’application Talkie-walkie dans Teams](/microsoftteams/walkie-talkie?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Gérer l’application Tâches dans Teams](/microsoftteams/manage-tasks-app?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Gérer l’application Shifts pour votre organisation dans Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Gérer l’application Approbations de Teams](/microsoftteams/approval-admin?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Gérer les stratégies de mise en application dans Teams](/microsoftteams/teams-app-setup-policies)
- [Gérer les stratégies d’autorisation d’application dans Teams](/microsoftteams/teams-app-permission-policies)
