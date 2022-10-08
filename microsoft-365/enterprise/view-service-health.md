---
title: Comment vérifier l’intégrité du service Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: high
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
- seo-marvel-apr2020
ms.collection:
- scotvorg
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Afficher l’état d’intégrité des services Microsoft 365 avant de contacter le support technique pour vérifier qu’aucune interruption de service n’est en cours.
ms.openlocfilehash: 210afaa3fc9a3fb247d56baf9172221ad24cced7
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68179260"
---
# <a name="how-to-check-microsoft-365-service-health"></a>Comment vérifier l’intégrité du service Microsoft 365

[![Étiquette vous informant le centre d’administration est en train de changer et vous pouvez trouver plus de détails à ce sujet à l’adresse aka.ms/aboutM365preview.](../media/O365-Admin-AdminCenterChanging.png)](/office365/admin/microsoft-365-admin-center-preview?preserve-view=true&view=o365-worldwide)

You can view the health of your Microsoft services, including Office on the web, Yammer, Microsoft Dynamics CRM, and mobile device management cloud services, on the **Service health** page in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339). If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.

Si vous ne parvenez pas à vous connecter au Centre d’administration, vous pouvez utiliser la [page d’état du service ](https://status.office365.com) pour vérifier si des problèmes connus vous empêchent de vous connecter à votre locataire.  Inscrivez-vous également pour nous suivre à [@MSFT365status](https://twitter.com/MSFT365Status) sur Twitter pour afficher des informations sur certains événements.

## <a name="how-to-check-service-health"></a>Vérifier l’état du service

1. Accédez au Centre d’administration Microsoft 365 sur [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339)et connectez-vous avec un compte d’administrateur.

    > [!NOTE]
    > People who are assigned the global admin or service support admin role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role. For more information about roles that can view service health, see [About admin roles](../admin/add-users/about-admin-roles.md?preserve-view=true&view=o365-worldwide#commonly-used-microsoft-365-admin-center-roles).

2. To view service health, in the left-hand navigation of the admin center, go to **Health** > **Service health**, or select the **Service health** card on the **Home dashboard**. The dashboard card indicates whether there is an active service issue and links to the detailed **Service health** page.

3. Dans la page d’**intégrité du service**, l’état d’intégrité de chaque service cloud est affiché dans un format de tableau.

   ![Afficher les problèmes en cours dans l’état du service.](../media/shd-landing-page.png)

L’onglet **Tous les services** (affichage par défaut) affiche tous les services, leur état d’intégrité actuel et tous les incidents ou avis actifs. Une icône et un état dans la colonne **État** indiquent l’état de chaque service.

S’il existe un incident ou un avis actif pour un service, ils sont répertoriés directement sous le nom du service dans une table imbriquée. Vous pouvez réduire la table imbriqué pour masquer les incidents ou les avis dans cette vue en cliquant sur l’icône de chevron à gauche du nom du service.

Pour filtrer votre affichage afin d’afficher uniquement tous les incidents actifs, sélectionnez l’onglet **Incidents** en haut de la page. La sélection de l’onglet **Avertissements** affiche uniquement tous les avis actifs publiés.

L’onglet **Historique** affiche tous les incidents et avis qui ont été résolus au cours des sept ou 30 derniers jours.

Si vous rencontrez un problème avec un service Microsoft 365 et que vous ne le voyez pas dans la page d’**Intégrité des services**, faites-le nous savoir en sélectionnant **Signaler un problème** et en complétant le formulaire court. Nous allons examiner les données et rapports connexes d’autres organisations pour voir à quel point le problème est répandu et s’il provient de notre service. Si c’est le cas, nous l’ajouterons sous la forme d’un nouvel incident ou d’un nouvel avis sur la page d’**Intégrité des services**, où vous pouvez suivre sa résolution. La page **Problèmes signalés** affiche tous les problèmes signalés par votre locataire à partir de ce formulaire et l’état.

To customize your view of which services show up on the dashboard, select **Preferences** > **Custom view**,  and clear the checkboxes for the services you want to filter out of your Service health dashboard view. Make sure that the checkbox is selected for each service that you want to monitor.

Pour vous inscrire aux notifications par e-mail des nouveaux incidents qui affectent votre locataire et les modifications d’état d’un incident actif, sélectionnez **Préférences** > **E-mail**, cliquez sur **M’envoyer des notifications d’intégrité du service par e-mail**, puis spécifiez :

- Jusqu’à deux adresses e-mail.
- Que vous souhaitiez recevoir des notifications pour des incidents ou des avis
- Services pour lesquels vous souhaitez recevoir une notification

Vous pouvez également vous abonner à des notifications par e-mail pour des événements individuels au lieu de chaque événement d’un service. Pour ce faire, sélectionnez le problème actif pour lequel vous souhaitez recevoir des mises à jour de notification par e-mail, sélectionnez **Gérer les notifications pour ce problème**, puis spécifiez :

- Jusqu’à deux adresses e-mail.

> [!NOTE]
> Chaque administrateur peut avoir ses Préférences définies et la limite ci-dessus de deux adresses e-mail est par compte d’administrateur.

> [!TIP]
> Vous pouvez également utiliser l'[application Administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=627216) sur votre appareil mobile pour afficher l'état du service, ce qui constitue un excellent moyen de vous tenir informé des notifications Push.

### <a name="view-details-of-posted-service-health"></a>Afficher les détails relatifs à l’état du service publié

Dans la vue **Tous les services** , sélectionnez le titre du problème pour afficher la page de détails du problème, qui affiche plus d’informations sur le problème, y compris un flux de tous les messages publiés pendant que nous travaillons sur une solution.

[![Capture d’écran montrant l’avis de service.](../media/service-health-advisory.png)](../media/service-health-advisory.png#lightbox)

Le récapitulatif de l’avis ou de l’incident fournit les informations suivantes :

- **Titre** : récapitulatif du problème.
- **ID** : identificateur numérique du problème.
- **Service** : nom du service affecté.
- **Dernière mise à jour** : dernière mise à jour du message d’intégrité du service.
- **Heure de début estimée** : heure estimée à laquelle le problème a démarré.
- **État** : comment ce problème affecte le service.
- **Impact utilisateur** : brève description de l’impact de ce problème sur l’utilisateur final.
- **Toutes les mises à jour** : nous publions des messages fréquents pour vous informer de la progression de l’application d’une solution.

![Capture d’écran montrant les détails du problème.](../media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a>Traduire les détails d’état du service

Nous utilisons la traduction automatique pour afficher automatiquement les messages dans votre langue préférée. Pour plus d’informations sur la définition de votre langue, lisez [Traduction de langue pour le tableau de bord d’intégrité des services](lang-service-health.md).

### <a name="definitions"></a>Définitions

Most of the time, services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.

> [!TIP]
> Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Microsoft 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.

### <a name="incidents-and-advisories"></a>Incidents et avis

| Icône | Description |
|:-----|:-----|
|![Icône d’informations pour l’avertissement.](../media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.  <br/> |
|![Icône de point d’exclamation pour l’incident.](../media/a636db57-6083-44dc-bbd5-556850804f17.png)|If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.  <br/> |

### <a name="status-definitions"></a>Définitions des états

| État | Définition |
|:-----|:-----|
|**Examen en cours** | Nous sommes conscients d’un problème potentiel et recueillons des informations sur ce problème et son impact. |
|**Dégradation du service** | We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example. |
|**Interruption du service** | You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently. |
|**Service en cours de restauration** | La cause du problème a été identifiée, nous connaissons l'action corrective à appliquer et le service est en cours de restauration. |
|**Récupération étendue** | This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix. |
|**Examen suspendu** | If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need. |
|**Service restauré** | We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details. |
|**Faux positif** | Après un examen détaillé, nous avons confirmé que le service est sain et fonctionne comme prévu. Aucun impact sur le service n’a été observé ou la cause de l’incident provient de l’extérieur du service. Les incidents et avis avec cet état s’affichent dans l’affichage d’historique jusqu’à leur expiration (après la période de temps mentionnée dans la publication finale de cet événement). |
|**Rapport post-incident publié** | Nous avons publié un rapport post-incident concernant un problème spécifique. Le rapport comprend les informations relatives aux causes premières de l’incident et aux étapes à mettre en œuvre pour s’assurer qu’il ne se reproduise plus. |

### <a name="message-post-types"></a>Types de billets de message

| Type | Définition |
|:-----|:-----|
|**Mise à jour rapide** | Mises à jour incrémentielles courtes et fréquentes pour les incidents à impact général, disponibles pour tous les clients. |
|**Détails supplémentaires** | Ces publications supplémentaires fournissent des détails techniques et de résolution plus complets pour offrir une visibilité plus approfondie de la gestion des incidents. Ceci est disponible pour les locataires qui répondent aux mêmes exigences décrites pour la[surveillance Exchange Online](/microsoft-365/enterprise/microsoft-365-exchange-monitoring#requirements), |

### <a name="history"></a>Historique

Service health lets you look at your current health status and view the history of any service advisories and incidents that have affected your tenant in the past 30 days. To view the past health of all services, select **History** view.

Pour plus d’informations sur notre engagement en matière de temps d’activité, consultez [Opérations transparentes de Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity).

## <a name="related-topics"></a>Sujets associés

- [Rapports d'activité dans le centre d'administration Microsoft 365](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)
- [Préférences du centre de messages](../admin/manage/message-center.md?preserve-view=true&view=o365-worldwide#preferences)
- [Comment vérifier l’intégrité des versions de Windows sur le Centre d’administration](/windows/deployment/update/check-release-health)
