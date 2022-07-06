---
title: Prise en main du tableau de bord Alertes DLP
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Commencez à définir et à gérer des alertes pour les stratégies de protection contre la perte de données.
ms.openlocfilehash: de980fadbc6b6091a0257c032dacab4220704f62
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625454"
---
# <a name="get-started-with-the-data-loss-prevention-alerts-dashboard"></a>Prise en main du tableau de bord Alertes de protection contre la perte de données

Protection contre la perte de données Microsoft Purview (DLP) peut prendre des mesures de protection pour empêcher le partage involontaire d’éléments sensibles. Lorsqu’une action est effectuée sur un élément sensible, vous pouvez être averti en configurant des alertes pour DLP. Cet article vous montre comment définir des stratégies d’alerte enrichies liées à vos stratégies de protection contre la perte de données (DLP). Vous verrez comment utiliser le tableau de [bord de gestion des alertes DLP](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a> pour afficher les alertes, les événements et les métadonnées associées pour les violations de stratégie DLP.

Si vous débutez avec les alertes DLP, vous devez consulter [le tableau de bord Des alertes de protection contre la perte de données](dlp-alerts-dashboard-learn.md)

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer, vérifiez que vous disposez des prérequis nécessaires :

-   Gestion des licences pour le tableau de bord de gestion des alertes DLP
-   Licences pour les options de configuration des alertes
-   Rôles

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licences pour le tableau de bord de gestion des alertes DLP

Tous les locataires éligibles pour DLP peuvent accéder au tableau de bord de gestion des alertes DLP. Pour commencer, vous devez être éligible à Microsoft Purview DLP pour Exchange Online, SharePoint Online et OneDrive Entreprise. Pour plus d’informations sur les exigences en matière de licences pour DLP, consultez [Quelles licences fournissent les droits permettant à un utilisateur de bénéficier du service ?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16)

Les clients qui utilisent [endpoint DLP](endpoint-dlp-learn-about.md) qui sont éligibles à [Teams DLP](dlp-microsoft-teams.md) voient leurs alertes de stratégie DLP de point de terminaison et les alertes de stratégie DLP Teams dans le tableau de bord de gestion des alertes DLP.

La fonctionnalité **d’aperçu du contenu** est disponible uniquement pour les licences suivantes :

- Microsoft 365 (E5)
- Office 365 (E5)
- Ajout d’Advanced Compliance (E5)
- Microsoft 365 E5/A5 Protection de l’information et Gouvernance
- Conformité Microsoft 365 E5/A5

### <a name="licensing-for-alert-configuration-options"></a>Licences pour les options de configuration des alertes

**Configuration des alertes à événement unique** : les organisations qui ont un abonnement E1, F1 ou G1 ou un abonnement E3 ou G3 peuvent créer des stratégies d’alerte uniquement lorsqu’une alerte est déclenchée chaque fois qu’une activité se produit.

**Configuration d’alerte agrégée** : pour configurer des stratégies d’alerte agrégées en fonction d’un seuil, vous devez disposer de l’une des configurations de licence suivantes :

- Un abonnement E5 ou G5
- Un abonnement E1, F1 ou G1 ou un abonnement E3 ou G3 qui inclut l’une des fonctionnalités suivantes :
    - Office 365 – Protection avancée contre les menaces Plan 2
    - Microsoft 365 E5 Conformité
    - Licence de complément Microsoft 365 eDiscovery et Audit

### <a name="roles"></a>Rôles

Si vous souhaitez afficher le tableau de bord de gestion des alertes DLP ou modifier les options de configuration des alertes dans une stratégie DLP, vous devez être membre de l’un de ces groupes de rôles :

- Administrateur de conformité
- Administrateur de conformité des données
- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur de sécurité

Pour accéder au tableau de bord de gestion des alertes DLP, vous avez besoin des éléments suivantes :

- Gérer des alertes

et l’un de ces deux rôles :

- Gestion de la conformité DLP
- View-Only gestion de la conformité DLP

Pour accéder à la fonctionnalité d’aperçu du contenu et aux fonctionnalités de contexte et de contenu sensibles mis en correspondance, vous devez être membre des éléments suivants :

- Groupe de rôles Visionneuse de contenu de l’Explorateur de contenu

qui a le rôle de visionneuse de contenu de classification des données pré-attribué.

### <a name="roles-and-role-groups-in-preview"></a>Rôles et groupes de rôles en préversion

Il existe des rôles et des groupes de rôles en préversion que vous pouvez tester pour affiner vos contrôles d’accès.

Voici une liste des rôles applicables qui sont en préversion. Pour en savoir plus sur ces rôles, consultez [Rôles dans le Centre de sécurité et de conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administrateur Information Protection
- Analyste Information Protection
- Enquêteur Information Protection
- Lecteur Information Protection

Voici une liste des groupes de rôles applicables en préversion. Pour en savoir plus sur ces groupes, consultez [Groupes de rôles dans le Centre de sécurité et de conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Protection des informations
- Administrateurs Information Protection
- Analystes Information Protection
- Enquêteurs Information Protection
- Lecteurs Information Protection

## <a name="dlp-alert-configuration"></a>Configuration des alertes DLP

Pour savoir comment configurer une alerte dans votre stratégie DLP, consultez [Où commencer par la protection contre la perte de données](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention).

> [!IMPORTANT]
> La configuration de la stratégie de rétention du journal d’audit de vos organisations contrôle la durée pendant laquelle une alerte reste visible dans la console. Pour plus d’informations, consultez [Gérer les stratégies de rétention des journaux d’audit](audit-log-retention-policies.md#manage-audit-log-retention-policies) .

### <a name="aggregate-event-alert-configuration"></a>Configuration de l’alerte d’événement d’agrégation

Si votre organisation dispose d’une licence pour les [options de configuration d’alerte agrégées](#licensing-for-alert-configuration-options), ces options s’affichent lorsque vous créez ou modifiez une stratégie DLP.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Capture d’écran montrant les options de rapports d’incident pour les utilisateurs éligibles aux options de configuration des alertes agrégées." border="false":::

Cette configuration vous permet de configurer une stratégie pour générer une alerte chaque fois qu’une activité correspond aux conditions de stratégie ou lorsqu’un certain seuil est dépassé, en fonction du nombre d’activités ou du volume de données exfiltrées.

### <a name="single-event-alert-configuration"></a>Configuration d’alerte d’événement unique

Si votre organisation dispose d’une licence pour les [options de configuration d’alerte d’événement unique](#licensing-for-alert-configuration-options), ces options s’affichent lorsque vous créez ou modifiez une stratégie DLP. Utilisez cette option pour créer une alerte déclenchée chaque fois qu’une correspondance de règle DLP se produit.

:::image type="content" source="../media/incident-reports-options-single-event-alerts.png" alt-text="Capture d’écran montrant les options de rapports d’incident pour les utilisateurs éligibles aux options de configuration des alertes à événement unique." border="false":::

## <a name="investigate-a-dlp-alert"></a>Examiner une alerte DLP

Pour utiliser le tableau de bord de gestion des alertes DLP :

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>, accédez à **la protection contre la perte de données**.
2. Sélectionnez l’onglet **Alertes** pour afficher le tableau de bord des alertes DLP.
3. Sélectionnez une alerte pour afficher les détails :

:::image type="content" source="../media/alert-details.png" alt-text="Capture d’écran montrant les détails de l’alerte dans le tableau de bord de gestion des alertes DLP." border="false":::

4. Sélectionnez l’onglet **Événements** pour afficher tous les événements associés à l’alerte. Vous pouvez choisir un événement particulier pour afficher ses détails. Pour obtenir la liste de certains des détails de l’événement disponibles, consultez [l’article En savoir plus sur le tableau de bord Alertes de protection contre la perte de données](dlp-alerts-dashboard-learn.md).
5. Sélectionnez **Détails** pour ouvrir la page **Vue d’ensemble** de l’alerte. La page vue d’ensemble fournit un résumé :
    1. de ce qui s’est passé
    1. qui a effectué les actions qui ont provoqué la correspondance de stratégie
    1. informations sur la stratégie mise en correspondance, et bien plus encore 

6. Choisissez l’onglet **Événements** pour accéder à :
    1. contenu impliqué
    1. types d’informations sensibles mis en correspondance
    1. Métadonnées

7. Sélectionnez l’onglet **Types d’informations sensibles** pour afficher des détails sur les types d’informations sensibles détectés dans le contenu. Les détails incluent la confiance, le nombre et le contenu qui correspond au type d’informations sensibles.

8. Après avoir examiné l’alerte, revenez à l’onglet **Vue d’ensemble** , où vous pouvez gérer le triage et gérer la destruction de l’alerte et ajouter des commentaires.

- Pour afficher l’historique de la gestion des flux de travail, choisissez **Journal de gestion**.
- Une fois que vous avez pris l’action requise pour l’alerte, définissez l’état de l’alerte sur **Résolu**.

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les alertes de protection contre la perte de données et le tableau de bord des alertes](dlp-alerts-dashboard-learn.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
