---
title: Configurer et afficher des alertes pour les stratégies DLP
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
description: Découvrez comment définir et gérer des alertes pour les stratégies de protection contre la perte de données.
ms.openlocfilehash: 60d5188b9288b1e131e36e145f7abb98a34d5ead
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627644"
---
# <a name="configure-and-view-alerts-for-data-loss-prevention-polices"></a>Configurer et afficher des alertes pour les stratégies de protection contre la perte de données

Protection contre la perte de données Microsoft Purview (DLP) peut prendre des mesures de protection pour empêcher le partage involontaire d’éléments sensibles. Lorsqu’une action est effectuée sur un élément sensible, vous pouvez être averti en configurant des alertes pour DLP. Cet article vous montre comment définir des stratégies d’alerte enrichies liées à vos stratégies de protection contre la perte de données (DLP). Vous verrez comment utiliser le nouveau tableau de bord de gestion des alertes DLP dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a> pour afficher les alertes, les événements et les métadonnées associées pour les violations de stratégie DLP.

## <a name="features"></a>Fonctionnalités

Les fonctionnalités suivantes font partie de ce qui suit :

-   **Tableau de bord de gestion des alertes DLP** : dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>, ce tableau de bord affiche des alertes pour les stratégies DLP appliquées aux charges de travail suivantes :

    -   Exchange
    -   SharePoint
    -   OneDrive
    -   Teams
    -   Appareils
-   **Options avancées de configuration des alertes** : ces options font partie du flux de création de stratégie DLP. Utilisez-les pour créer des configurations d’alerte enrichies. Vous pouvez créer une alerte d’événement unique ou une alerte agrégée, en fonction du nombre d’événements ou de la taille des données divulguées.

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer, vérifiez que vous disposez des prérequis nécessaires :

-   Gestion des licences pour le tableau de bord de gestion des alertes DLP
-   Licences pour les options de configuration des alertes
-   Rôles

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licences pour le tableau de bord de gestion des alertes DLP

Tous les locataires éligibles pour Office 365 DLP peuvent accéder au nouveau tableau de bord de gestion des alertes DLP. Pour commencer, vous devez être éligible à Office 365 DLP pour Exchange Online, SharePoint Online et OneDrive Entreprise. Pour plus d’informations sur les exigences en matière de licences pour Office 365 DLP, consultez [Quelles licences fournissent les droits permettant à un utilisateur de bénéficier du service ?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16)

Les clients qui utilisent [endpoint DLP](endpoint-dlp-learn-about.md) qui sont éligibles à [Teams DLP](dlp-microsoft-teams.md) voient leurs alertes de stratégie DLP de point de terminaison et les alertes de stratégie DLP Teams dans le tableau de bord de gestion des alertes DLP.

### <a name="licensing-for-alert-configuration-options"></a>Licences pour les options de configuration des alertes

- **Configuration des alertes à événement unique** : les organisations qui ont un abonnement E1, F1 ou G1 ou un abonnement E3 ou G3 peuvent créer des stratégies d’alerte uniquement lorsqu’une alerte est déclenchée chaque fois qu’une activité se produit.
- **Configuration d’alerte agrégée** : pour configurer des stratégies d’alerte agrégées en fonction d’un seuil, vous devez disposer de l’une des configurations suivantes :
  - Un abonnement E5 ou G5
  - Un abonnement E1, F1 ou G1 ou un abonnement E3 ou G3 qui inclut l’une des fonctionnalités suivantes :
    - Office 365 – Protection avancée contre les menaces Plan 2
    - Microsoft 365 E5 Conformité
    - Licence de complément Microsoft 365 eDiscovery et Audit

### <a name="roles"></a>Rôles

Si vous souhaitez afficher le tableau de bord de gestion des alertes DLP ou modifier les options de configuration des alertes dans une stratégie DLP, vous devez être membre de l’un de ces groupes de rôles :

-   Administrateur de conformité
-   Administrateur de conformité des données
-   Administrateur de sécurité
-   Opérateur de sécurité
-   Lecteur de sécurité

Pour accéder au tableau de bord de gestion des alertes DLP, vous avez besoin du rôle Gérer les alertes et de l’un des rôles suivants :

-   Gestion de la conformité DLP
-   View-Only gestion de la conformité DLP

## <a name="alert-configuration-experience"></a>Expérience de configuration des alertes

Si vous êtes éligible aux [options de configuration des alertes agrégées](#licensing-for-alert-configuration-options), les options suivantes s’affichent en ligne dans l’expérience de création de stratégie DLP.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Capture d’écran montrant les options de rapports d’incident pour les utilisateurs éligibles aux options de configuration des alertes agrégées." border="false":::

Cette configuration vous permet de configurer une stratégie pour générer une alerte :

- chaque fois qu’une activité correspond aux conditions de stratégie
- lorsque le seuil défini est atteint ou dépassé
- en fonction du nombre d’activités
- en fonction du volume de données exfiltrées

Pour éviter un flot d’e-mails de notification, toutes les correspondances qui se produisent dans une fenêtre d’une minute et qui concernent la même règle DLP et au même emplacement sont regroupées dans la même alerte. La fonctionnalité de fenêtre de temps d’agrégation d’une minute est disponible dans : 

- Un abonnement E5 ou G5
- Un abonnement E1, F1 ou G1 ou un abonnement E3 ou G3 qui inclut l’une des fonctionnalités suivantes :
    - Office 365 – Protection avancée contre les menaces Plan 2
    - Microsoft 365 E5 Conformité
    - Licence de complément Microsoft 365 eDiscovery et Audit
 
Pour les organisations qui ont un abonnement E1, F1 ou G1 ou un abonnement E3 ou G3, la fenêtre de temps d’agrégation est de 15 minutes.

## <a name="dlp-alert-management-dashboard"></a>Tableau de bord de gestion des alertes DLP

Pour utiliser le tableau de bord de gestion des alertes DLP :

1.  Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>, accédez à **la protection contre la perte de données**.

2.  Sélectionnez l’onglet **Alertes** pour afficher le tableau de bord des alertes DLP.

    -   Choisissez des filtres pour affiner la liste des alertes. Choisissez **Personnaliser les colonnes** pour répertorier les propriétés que vous souhaitez voir. Vous pouvez également choisir de trier les alertes dans l’ordre croissant ou décroissant dans n’importe quelle colonne.
    -   Sélectionnez une alerte pour afficher les détails :

        :::image type="content" source="../media/alert-details.png" alt-text="Capture d’écran montrant les détails de l’alerte dans le tableau de bord de gestion des alertes DLP." border="false":::

1.  Sélectionnez l’onglet **Événements** pour afficher tous les événements associés à l’alerte. Vous pouvez choisir un événement particulier pour afficher ses détails. Le tableau suivant présente certains détails de l’événement.
    
    | Catégorie          | Nom de la propriété                 | Description                                                                | Types d’événements applicables                   |
    |-------------------|-------------------------------|----------------------------------------------------------------------------|------------------------------------------|
    |*Détails de l’événement*||
    |      | Id                            | ID unique associé à l’événement                                        | Tous les événements                               |
    |                   | Emplacement                      | Charge de travail dans laquelle l’événement a été détecté                                      | Tous les événements                               |
    |                   | Temps d’activité              | Heure de l’activité de l’utilisateur à l’origine de la violation DLP                    | Tous les événements                               |
    |*Entités impactées*||
    |  | Utilisateur                          | Utilisateur ayant provoqué la violation DLP                                          | Tous les événements                               |
    |                   | Nom d'hôte                      | Nom d’hôte de l’ordinateur sur lequel la violation DLP a été détectée              | Événements d’appareils                           |
    |                   | Adresse IP                    | Adresse IP de l’ordinateur                                                  | Événements d’appareils                           |
    |                   | File path                     | Chemin absolu du fichier impliqué dans la violation                        | Événements SharePoint, OneDrive et Appareils |
    |                   | Destinataires de l’e-mail              | Destinataires de l’e-mail qui a violé la stratégie DLP                       | Événements Exchange                          |
    |                   | Sujet de l’e-mail                 | Objet de l’e-mail qui a violé la stratégie DLP                          | Événements Exchange                          |
    |                   | Pièces jointes             | Noms des pièces jointes dans l’e-mail qui ont violé la stratégie DLP         | Événements Exchange                          |
    |                   | Propriétaire du site                    | Nom du propriétaire du site                                                     | Événements SharePoint et OneDrive           |
    |                   | URL du site                      | URL complète du site SharePoint ou OneDrive                                | Événements SharePoint et OneDrive           |
    |                   | Fichier créé                  | Heure de création du fichier                                                      | Événements SharePoint et OneDrive           |
    |                   | Fichier modifié pour la dernière fois            | Heure de la dernière modification du fichier                                  | Événements SharePoint et OneDrive           |
    |                   | La taille des fichiers                     | Taille du fichier                                                           | Événements SharePoint et OneDrive           |
    |                   | Propriétaire du fichier                    | Propriétaire du fichier                                                          | Événements SharePoint et OneDrive           |
    |*Détails de la stratégie*||
    |     | Stratégie DLP mise en correspondance            | Nom de la stratégie DLP qui a été mise en correspondance                                    | Tous les événements                               |
    |                   | Règle mise en correspondance                  | Nom de la règle DLP dans la stratégie DLP qui a été mise en correspondance                    | Tous les événements                               |
    |                   | Types d’informations sensibles détectés | Types d’informations sensibles détectés dans le cadre de la stratégie DLP | Tous les événements                               |
    |                   | Actions prises                 | Actions effectuées dans le cadre de la stratégie DLP correspondante                          | Tous les événements                               |
    |                   | Stratégie de dépassement d’utilisateur          | Indique si l’utilisateur remplace la stratégie par le biais de l’info-bulle de stratégie                | Tous les événements                               |
    |                   | Remplacer le texte de justification   | Justification fournie pour remplacer l’info-bulle de stratégie                          | Tous les événements                               |
    
1.  Sélectionnez l’onglet **Types d’informations sensibles** pour afficher des détails sur les types d’informations sensibles détectés dans le contenu. Les détails incluent la confiance et le nombre.

2.  Après avoir examiné l’alerte, choisissez **Gérer l’alerte** pour modifier l’état (**Actif**, **Examen**, **Ignoré** ou **Résolu**). Vous pouvez également ajouter des commentaires et affecter l’alerte à une personne de votre organisation.

    -   Pour afficher l’historique de la gestion des flux de travail, choisissez **Journal de gestion**.
    -   Une fois que vous avez pris l’action requise pour l’alerte, définissez l’état de l’alerte sur **Résolu**.
