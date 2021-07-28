---
title: Comment vérifier l’intégrité du service Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
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
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Afficher l’état d’intégrité des services Microsoft 365 avant de contacter le support technique pour vérifier qu’aucune interruption de service n’est en cours.
ms.openlocfilehash: 2b856b7851f569324d1cccabb6b2da2d098b2fbe
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53543448"
---
# <a name="how-to-check-microsoft-365-service-health"></a>Comment vérifier l’intégrité du service Microsoft 365

[![Étiquette vous informant le centre d’administration est en train de changer et vous pouvez trouver plus de détails à ce sujet à l’adresse aka.ms/aboutM365preview.](../media/O365-Admin-AdminCenterChanging.png)](/office365/admin/microsoft-365-admin-center-preview?preserve-view=true&view=o365-worldwide)

Vous pouvez afficher l’intégrité de vos services Microsoft, notamment Office sur le web, Yammer, Microsoft Dynamics CRM et les services cloud de gestion des appareils mobiles, sur la page **intégrité du service** dans le[Centre d’administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339). If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.

Si vous ne parvenez pas à vous connecter au Centre d’administration, vous pouvez utiliser la [page d’état du service ](https://status.office365.com) pour vérifier si des problèmes connus vous empêchent de vous connecter à votre locataire.  Inscrivez-vous également pour nous suivre à [@MSFT365status](https://twitter.com/MSFT365Status) sur Twitter pour afficher des informations sur certains événements.

## <a name="how-to-check-service-health"></a>Vérifier l’état du service

1. Accédez au Centre d’administration Microsoft 365 sur [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339)et connectez-vous avec un compte d’administrateur.

    > [!NOTE]
    > Les personnes qui se voient attribuer le rôle d’administrateur général ou d’administrateur du support technique peuvent afficher l’intégrité du service. Pour afficher l’état du service, les administrateurs Exchange, SharePoint et Skype Entreprise doivent aussi disposer d’un rôle d’administrateur portant sur ce service. Pour plus d’informations sur les rôles qui peuvent afficher l’intégrité du service, consultez [À propos des rôles d’administrateur](../admin/add-users/about-admin-roles.md?preserve-view=true&view=o365-worldwide#commonly-used-microsoft-365-admin-center-roles).

2. Pour ouvrir l’état du service, dans le Centre d’administration, accédez à **État** > **État du service** ou cliquez sur la carte **État du service** dans le **tableau de bord d’accueil**. La carte du tableau de bord indique s'il existe un problème lié au service actif et mène à la page détaillée d'**état du service**.

3. Dans la page d’**intégrité du service**, l’état d’intégrité de chaque service cloud est affiché dans un format de tableau.

   ![Afficher les problèmes en cours dans l’état du service](../media/service-health-all-services.png)

L’onglet **Tous les services** (affichage par défaut) affiche tous les services, leur état d’intégrité actuel et tous les incidents ou avis actifs. Une icône et un état dans la colonne **État** indiquent l’état de chaque service.

S’il existe un incident ou un avis actif pour un service, ils sont répertoriés directement sous le nom du service dans une table imbriquée. Vous pouvez réduire la table imbriqué pour masquer les incidents ou les avis dans cette vue en cliquant sur l’icône de chevron à gauche du nom du service.   

Pour filtrer votre affichage afin d’afficher uniquement tous les incidents actifs, sélectionnez l’onglet **Incidents** en haut de la page. La sélection de l’onglet **Avertissements** affiche uniquement tous les avis actifs publiés.

L’onglet **Historique** affiche tous les incidents et avis qui ont été résolus au cours des sept ou 30 derniers jours.

Si vous rencontrez un problème avec un service Microsoft 365 et que vous ne le voyez pas dans la page d’**intégrité du service**, faites-le nous savoir en sélectionnant **Signaler un problème** et en complétant le formulaire court. Nous allons examiner les données et rapports connexes d’autres organisations pour voir à quel point le problème est répandu et s’il provient de notre service. Si c’est le cas, nous l’ajouterons sous la forme d’un nouvel incident ou d’un nouvel avis sur la page d’**intégrité du service**, où vous pouvez suivre sa résolution. La page **Problèmes signalés** affiche tous les problèmes signalés par votre locataire à partir de ce formulaire et l’état.

Pour personnaliser votre affichage des services qui apparaissent sur le tableau de bord, sélectionnez **Préférences** > **Affichage personnalisé** et décochez les cases des services que vous souhaitez filtrer en dehors de votre affichage tableau de bord d’intégrité des services. Vérifiez que la case à cocher est cochée pour chaque service que vous souhaitez surveiller.

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

[ ![Capture d’écran montrant l’avis de service](../media/service-health-advisory.png) ](../media/service-health-advisory.png#lightbox)

Le récapitulatif de l’avis ou de l’incident fournit les informations suivantes :

- **Titre** : récapitulatif du problème.
- **ID** : identificateur numérique du problème.
- **Service** : nom du service affecté.
- **Dernière mise à jour** : dernière mise à jour du message d’intégrité du service.
- **Heure de début estimée** : heure estimée à laquelle le problème a démarré.
- **État** : comment ce problème affecte le service.
- **Impact utilisateur** : brève description de l’impact de ce problème sur l’utilisateur final.
- **Toutes les mises à jour** : nous publions des messages fréquents pour vous informer de la progression de l’application d’une solution.

![Capture d’écran montrant les détails du problème](../media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a>Traduire les détails d’état du service

Nous utilisons la traduction automatique pour afficher automatiquement les messages dans votre langue préférée. Pour plus d’informations sur la définition de votre langue, lisez [Traduction de langue pour les billets du Centre de messages](/microsoft-365/admin/manage/language-translation-for-message-center-posts).

### <a name="definitions"></a>Définitions

En règle générale, les services apparaissent comme intègres, sans autres informations. Lorsqu'un service présente un problème, ce problème est identifié sous forme d'avis ou d'incident et son état actuel s'affiche.

> [!TIP]
> Les événements de maintenance planifiée ne s'affichent pas dans l'état du service. Le **Centre de messages** vous permet de suivre les événements de maintenance planifiée. Filtrez les messages par Planification des modifications pour connaître le moment où une modification interviendra, son effet et comment vous y préparer. Pour plus d’informations, consultez [Centre de messages dans Microsoft 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) .

### <a name="incidents-and-advisories"></a>Incidents et avis

| Icône | Description |
|:-----|:-----|
|![Information icon for advisory](../media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Un service accompagné d'un avis indique que nous sommes conscients du problème qui affecte certains utilisateurs, mais que ce service est toujours disponible. Un avis propose souvent une solution de contournement du problème, qui peut intermittent ou limité en termes d'impact sur les utilisateurs.  <br/> |
|![Exclamation point icon for incident](../media/a636db57-6083-44dc-bbd5-556850804f17.png)|Si un service présente un incident actif, cela signifie qu'il s'agit d'un problème critique et que le service ou une de ses fonctions principales n'est pas disponible. Par exemple, les utilisateurs peuvent ne pas être en mesure d'envoyer et de recevoir des e-mails ni de se connecter. Les incidents ont un impact significatif sur les utilisateurs. En cas d'incident, nous publions des mises à jour relatives à son examen, aux efforts déployés pour y remédier, et sa résolution apparaît dans le tableau de bord d'état du service.  <br/> |

### <a name="status-definitions"></a>Définitions des états

| État | Définition |
|:-----|:-----|
|**Examen en cours** | Nous sommes conscients d’un problème potentiel et recueillons des informations sur ce problème et son impact. |
|**Dégradation du service** | Nous avons identifié un problème susceptible d'affecter l'utilisation d'un service ou d'une fonctionnalité. Cet état peut s'afficher si un service s'avère plus lent qu'habituellement, s'il présente des interruptions intermittentes ou si une fonctionnalité est défaillante, par exemple. |
|**Interruption du service** | Cet état s'affiche si nous identifions un problème qui affecte la capacité des utilisateurs à accéder au service. Dans ce cas, le problème est significatif et peut se répéter. |
|**Service en cours de restauration** | La cause du problème a été identifiée, nous connaissons l'action corrective à appliquer et le service est en cours de restauration. |
|**Récupération étendue** | Cet état indique qu'une action corrective est en cours afin de restaurer le service pour la plupart des utilisateurs, mais qu'il faudra un certain temps pour qu'elle s'applique à tous les systèmes concernés. Cet état peut également s'afficher si nous proposons un correctif temporaire visant à réduire l'impact du problème en attendant un correctif définitif. |
|**Examen suspendu** | Cet état s'affiche si l'examen détaillé d'un problème potentiel implique plus d'informations de la part des clients afin de nous permettre de mieux l'étudier. Dans ce cas, nous vous indiquerons les données ou journaux dont nous avons besoin. |
|**Service restauré** | L'action corrective a permis de résoudre le problème sous-jacent et le service a été restauré. Pour en savoir plus, consultez les détails relatifs au problème. |
|**Faux positif** | Après un examen détaillé, nous avons confirmé que le service est sain et fonctionne comme prévu. Aucun impact sur le service n’a été observé ou la cause de l’incident provient de l’extérieur du service. |
|**Rapport post-incident publié** | Nous avons publié un rapport post-incident concernant un problème spécifique. Le rapport comprend les informations relatives aux causes premières de l’incident et aux étapes à mettre en œuvre pour s’assurer qu’il ne se reproduise plus. |

### <a name="message-post-types"></a>Types de billets de message

| Type | Définition |
|:-----|:-----|
|**Mise à jour rapide** | Mises à jour incrémentielles courtes et fréquentes pour les incidents à impact général, disponibles pour tous les clients. |
|**Détails supplémentaires** | Ces publications supplémentaires fournissent des détails techniques et de résolution plus complets pour offrir une visibilité plus approfondie de la gestion des incidents. Ceci est disponible pour les locataires qui répondent aux mêmes exigences décrites pour la[surveillance Exchange Online](/microsoft-365/enterprise/microsoft-365-exchange-monitoring?view=o365-worldwide#requirements), |

### <a name="history"></a>Historique

L’état du service vous permet d’examiner votre état d’intégrité actuel et d’afficher l’historique des avis de service et des incidents qui ont affecté votre locataire au cours des 30 derniers jours. Pour afficher l’intégrité passée de tous les services, sélectionnez l’affichage **Historique** .

Pour plus d’informations sur notre engagement en matière de temps d’activité, consultez [Opérations transparentes de Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity).

## <a name="related-topics"></a>Sujets associés

[Rapports d'activité dans le centre d'administration Microsoft 365](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

[Préférences du centre de messages](../admin/manage/message-center.md?preserve-view=true&view=o365-worldwide#preferences)

[Comment vérifier l’intégrité des versions de Windows sur le Centre d’administration](/windows/deployment/update/check-release-health)
