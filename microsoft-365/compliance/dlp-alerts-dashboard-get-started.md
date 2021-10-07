---
title: Prise en main du tableau de bord des alertes de protection contre la perte de données
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
description: Prise en charge de la définition et de la gestion des alertes pour les stratégies de protection contre la perte de données.
ms.openlocfilehash: 601442336cb6ba2a913f3c64eb8345030d0f8209
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60151097"
---
# <a name="get-started-with-the-data-loss-prevention-alert-dashboard"></a>Prise en main du tableau de bord des alertes de protection contre la perte de données

Les stratégies de protection contre la perte de données (DLP) peuvent prendre des mesures de protection pour empêcher le partage involontaire d’éléments sensibles. Lorsqu’une action est prise sur un élément sensible, vous pouvez être averti en configurant des alertes pour DLP. Cet article vous montre comment définir des stratégies d’alerte enrichies liées à vos stratégies de protection contre la perte de données (DLP). Vous verrez comment utiliser le tableau de bord de gestion des alertes [DLP](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/) pour afficher les alertes, les événements et les métadonnées associées pour les violations de stratégie DLP.

Si vous débutez avec les alertes DLP, vous devez consulter le tableau de bord des alertes de protection [contre la perte de données.](dlp-alerts-dashboard-learn.md)

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer, assurez-vous que vous avez les conditions préalables nécessaires :

-   Licences pour le tableau de bord de gestion des alertes DLP
-   Gestion des licences pour les options de configuration des alertes
-   Rôles

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licences pour le tableau de bord de gestion des alertes DLP

Tous les locataires éligibles pour Office 365 DLP peuvent accéder au tableau de bord de gestion des alertes DLP. Pour commencer, vous devez être éligible à la Office 365 DLP pour Exchange Online, SharePoint Online et OneDrive Entreprise. Pour plus d’informations sur les conditions de licence requises pour Office 365 DLP, voir [quelles licences](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16)fournissent les droits d’un utilisateur pour bénéficier du service ? .

Les clients qui utilisent le point de terminaison [DLP](endpoint-dlp-learn-about.md) éligibles pour [Teams DLP](dlp-microsoft-teams.md) voient leurs alertes de stratégie DLP de point de terminaison et les alertes de stratégie Teams DLP dans le tableau de bord de gestion des alertes DLP.

La **fonctionnalité d’aperçu** de contenu est disponible uniquement pour les licences ci-après :

- Microsoft 365 (E5)
- Office 365 (E5)
- Ajout de conformité avancée (E5)
- Microsoft 365 E5/A5 Protection de l’information et Gouvernance
- Conformité microsft 365 E5/A5

### <a name="licensing-for-alert-configuration-options"></a>Gestion des licences pour les options de configuration des alertes

**Configuration** d’alerte à événement unique : les organisations qui ont un abonnement E1, F1 ou G1 ou un abonnement E3 ou G3 peuvent créer des stratégies d’alerte uniquement lorsqu’une alerte est déclenchée chaque fois qu’une activité se produit.

**Configuration d’alerte agrégée**: pour configurer des stratégies d’alerte agrégées basées sur un seuil, vous devez avoir l’une de ces configurations de licence :

- Un abonnement E5 ou G5
- Un abonnement E1, F1 ou G1 ou E3 ou G3 qui inclut l’une des fonctionnalités suivantes :
    - Office 365 – Protection avancée contre les menaces Plan 2
    - Microsoft 365 E5 Conformité
    - Microsoft 365 licence de modules de découverte électronique et d’audit

### <a name="roles"></a>Rôles


Si vous souhaitez afficher le tableau de bord de gestion des alertes DLP ou modifier les options de configuration des alertes dans une stratégie DLP, vous devez être membre de l’un de ces groupes de rôles :

- Administrateur de conformité
- Administrateur de conformité des données
- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur de sécurité

Pour accéder au tableau de bord de gestion des alertes DLP, vous devez :

- Gérer des alertes

et l’un de ces deux rôles :

- Gestion de la conformité DLP
- View-Only de conformité DLP

Pour accéder à la fonctionnalité d’aperçu de contenu et aux fonctionnalités de contexte et de contenu sensibles mis en correspondance, vous devez être membre des éléments :

- Groupe de rôles Visionneuse de contenu de l’Explorateur de contenu

dont le rôle visionneuse de contenu de classification des données est pré-attribué.

## <a name="dlp-alert-configuration"></a>Configuration des alertes DLP

Pour savoir comment configurer une alerte dans votre stratégie DLP, consultez l’exemple par où commencer avec la protection [contre la perte de données.](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention)

### <a name="aggregate-event-alert-configuration"></a>Configuration agrégée des alertes d’événements

Si votre organisation est titulaire d’une licence pour les options de configuration d’alerte agrégées, ces [options](#licensing-for-alert-configuration-options)s’offrent à vous lorsque vous créez ou modifiez une stratégie DLP.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Capture d’écran montrant les options des rapports d’incident pour les utilisateurs éligibles pour les options de configuration d’alerte agrégées." border="false":::

Cette configuration vous permet de configurer une stratégie pour générer une alerte chaque fois qu’une activité correspond aux conditions de la stratégie ou lorsqu’un certain seuil est dépassé, en fonction du nombre d’activités ou du volume de données exfiltrées.

### <a name="single-event-alert-configuration"></a>Configuration d’alerte d’événement unique

Si votre organisation est titulaire d’une licence pour les options de configuration d’alerte à événement unique, ces [options](#licensing-for-alert-configuration-options)s’offrent à vous lorsque vous créez ou modifiez une stratégie DLP. Utilisez cette option pour créer une alerte qui se produit chaque fois qu’une correspondance de règle DLP se produit.

:::image type="content" source="../media/incident-reports-options-single-event-alerts.png" alt-text="Capture d’écran montrant les options des rapports d’incident pour les utilisateurs éligibles pour les options de configuration d’alerte à événement unique." border="false":::

## <a name="investigate-a-dlp-alert"></a>Examiner une alerte DLP

Pour travailler avec le tableau de bord de gestion des alertes DLP :

1. Dans la [Centre de conformité Microsoft 365,](https://www.compliance.microsoft.com)allez à **Protection contre la perte de données.**
2. Sélectionnez **l’onglet Alertes** pour afficher le tableau de bord des alertes DLP.
3. Sélectionnez une alerte pour voir les détails :

:::image type="content" source="../media/alert-details.png" alt-text="Capture d’écran montrant les détails de l’alerte dans le tableau de bord de gestion des alertes DLP." border="false":::

4. Sélectionnez **l’onglet** Événements pour afficher tous les événements associés à l’alerte. Vous pouvez choisir un événement particulier pour afficher ses détails. Pour obtenir la liste de certains détails sur les événements disponibles, voir le tableau de bord Alertes de protection contre la perte [de données.](dlp-alerts-dashboard-learn.md)
5. Sélectionnez **Détails** pour ouvrir la page **Vue d’ensemble** de l’alerte. La page vue d’ensemble fournit un résumé :
    1. de ce qui s’est passé
    1. qui a effectué les actions à l’origine de la correspondance de stratégie
    1. informations sur la stratégie de correspondance, et plus encore 

6. Sélectionnez **l’onglet Événements** pour accéder aux :
    1. contenu impliqué
    1. types d’informations sensibles qui correspondent
    1. metadata

7. Sélectionnez **l’onglet Types d’informations** sensibles pour afficher les détails sur les types d’informations sensibles détectés dans le contenu. Les détails incluent la confiance, le nombre et le contenu qui correspond au type d’informations sensibles.

8. Après avoir examiné l’alerte, revenir à l’onglet Vue d’ensemble où vous pouvez gérer le triage, gérer la disposition de l’alerte et ajouter des commentaires. 

- Pour consulter l’historique de la gestion des flux de travail, sélectionnez **Journal de gestion.**
- Une fois que vous avez pris l’action requise pour l’alerte, définissez l’état de l’alerte **sur Résolu.**

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les alertes de protection contre la perte de données et le tableau de bord des alertes](dlp-alerts-dashboard-learn.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)