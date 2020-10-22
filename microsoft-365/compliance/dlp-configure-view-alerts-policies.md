---
title: Configurer et afficher les alertes pour les stratégies DLP (aperçu)
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 10/15/2020
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment définir et gérer les alertes pour les stratégies DLP.
ms.openlocfilehash: addf46b27575f1a1cc062949aedb7ecdecaf7286
ms.sourcegitcommit: cdf2b8dad7db9e16afd339abaaa5397faf11807c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48651459"
---
# <a name="configure-and-view-alerts-for-dlp-polices-preview"></a>Configurer et afficher les alertes pour les stratégies DLP (aperçu)

Cet article vous explique comment définir des stratégies d’alerte enrichies liées à vos stratégies de protection contre la perte de données (DLP). Vous verrez comment utiliser le nouveau tableau de bord de gestion des alertes DLP dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/) pour afficher les alertes, les événements et les métadonnées associées pour les violations de stratégie DLP.

## <a name="features"></a>Fonctionnalités

Les fonctionnalités suivantes font partie de cet aperçu :

-   **Tableau de bord de gestion des alertes DLP**: dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), ce tableau de bord affiche les alertes pour les stratégies DLP appliquées sur les charges de travail suivantes :

    -   Exchange
    -   SharePoint
    -   OneDrive
    -   Équipes
    -   Appareils
-   **Options de configuration d’alerte avancées**: ces options font partie du flux de création de stratégies DLP. Utilisez-les pour créer des configurations d’alerte enrichies. Vous pouvez créer une alerte d’événement unique ou une alerte agrégée, en fonction du nombre d’événements ou de la taille des données divulguées.

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer, vérifiez que vous disposez des conditions préalables requises :

-   Licences pour le tableau de bord de gestion des alertes DLP
-   Licences pour les options de configuration d’alerte
-   Rôles

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licences pour le tableau de bord de gestion des alertes DLP

Tous les clients éligibles pour Office 365 DLP peuvent accéder au nouveau tableau de bord de gestion des alertes DLP. Pour commencer, vous devez être éligible pour Office 365 DLP pour Exchange Online, SharePoint Online et OneDrive entreprise. Pour plus d’informations sur les exigences en matière de licences pour Office 365 DLP, voir [quelles licences fournissent les droits dont dispose un utilisateur pour bénéficier du service ?](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

Les clients qui participent à la préversion publique de l' [Endpoint](https://docs.microsoft.com/microsoft-365/compliance/endpoint-dlp-learn-about?view=o365-worldwide) ou qui sont éligibles à [teams DLP](https://docs.microsoft.com/microsoft-365/compliance/dlp-microsoft-teams?view=o365-worldwide) verront leurs alertes de stratégie DLP de point de terminaison et alertes de stratégie DLP dans le tableau de bord de gestion des alertes DLP.

### <a name="licensing-for-alert-configuration-options"></a>Licences pour les options de configuration d’alerte

-   **Configuration des alertes à événement unique**: les organisations qui ont un abonnement E1, F1 ou G1 ou un abonnement E3 ou G3 peuvent créer des stratégies d’alerte uniquement lorsqu’une alerte est déclenchée à chaque fois qu’une activité se produit.
-   **Configuration d’alerte agrégée**: pour configurer des stratégies d’alerte agrégées sur la base d’un seuil, vous devez avoir l’une des configurations suivantes :
    -   Un abonnement E5 ou G5
    -   Un abonnement E1, F1 ou G1 ou un abonnement E3 ou G3 comprenant l’une des fonctionnalités suivantes :
        -   Office 365 – Protection avancée contre les menaces Plan 2
        -   Microsoft 365 E5 Conformité
        -   Licence de module complémentaire eDiscovery et audit Microsoft 365

### <a name="roles"></a>Rôles

Si vous souhaitez afficher le tableau de bord de gestion des alertes DLP ou modifier les options de configuration d’alerte dans une stratégie DLP, vous devez être membre de l’un des groupes de rôles suivants :

-   Administrateur de conformité
-   Administrateur des données de conformité
-   Administrateur de sécurité
-   Opérateur de sécurité
-   Lecteur de sécurité

Pour accéder au tableau de bord de gestion des alertes DLP, vous devez disposer du rôle gérer les alertes et de l’un des rôles suivants :

-   Gestion de la conformité DLP
-   Gestion de la conformité View-Only DLP

## <a name="alert-configuration-experience"></a>Expérience de configuration des alertes

Si vous êtes éligible pour les [options de configuration d’alerte agrégée](#licensing-for-alert-configuration-options), les options suivantes sont disponibles dans l’expérience de création de stratégies DLP.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Capture d’écran montrant les options de rapports d’incident pour les utilisateurs éligibles pour les options de configuration d’alerte agrégée." border="false":::

Vous pouvez utiliser ces options de configuration d’alerte pour configurer un paramètre qui définit la fréquence à laquelle une correspondance de règle DLP peut se produire avant le déclenchement d’une alerte. Cette configuration vous permet de configurer une stratégie pour générer une alerte chaque fois qu’une activité répond aux conditions de la stratégie ou lorsqu’un certain seuil est dépassé, en fonction du nombre d’activités ou en fonction du volume de données exfiltrées.

Si vous êtes éligible aux [options de configuration d’alerte à un seul événement](#licensing-for-alert-configuration-options), l’option de configuration d’alerte suivante s’affiche dans l’expérience de création de stratégies DLP. Utilisez cette option pour créer une alerte générée à chaque fois qu’une correspondance de règle DLP se produit en raison d’une activité de l’utilisateur.

:::image type="content" source="../media/incident-reports-options-single-event-alerts.png" alt-text="Capture d’écran montrant les options de rapports d’incident pour les utilisateurs éligibles pour les options de configuration d’alerte agrégée." border="false":::

## <a name="dlp-alert-management-dashboard"></a>Tableau de bord de gestion des alertes DLP

Pour utiliser le tableau de bord de gestion des alertes DLP :

1.  Dans le [Centre de conformité Microsoft 365](https://www.compliance.microsoft.com), accédez à la **protection contre la perte de données**.

2.  Sélectionnez l’onglet **alertes** pour afficher le tableau de bord des alertes DLP.

    -   Choisissez filtres pour affiner la liste des alertes. Choisissez **personnaliser les colonnes** pour répertorier les propriétés que vous souhaitez afficher. Vous pouvez également choisir de trier les alertes par ordre croissant ou décroissant dans n’importe quelle colonne.
    -   Sélectionnez une alerte pour afficher les détails :

        :::image type="content" source="../media/alert-details.png" alt-text="Capture d’écran montrant les options de rapports d’incident pour les utilisateurs éligibles pour les options de configuration d’alerte agrégée." border="false":::

1.  Sélectionnez l’onglet **événements** pour afficher tous les événements associés à l’alerte. Vous pouvez choisir un événement particulier pour afficher ses détails.
    Le tableau suivant présente certains détails de l’événement.
    
    | Catégorie          | Nom de la propriété                 | Description                                                                | Types d’événement applicables                   |
    |-------------------|-------------------------------|----------------------------------------------------------------------------|------------------------------------------|
    |*Détails de l'événement*||
    |      | ID                            | ID unique associé à l’événement.                                        | Tous les événements                               |
    |                   | Lieu                      | Charge de travail dans laquelle l’événement a été détecté                                      | Tous les événements                               |
    |                   | Heure de l’activité              | Heure de l’activité de l’utilisateur à l’origine de la violation DLP                    | Tous les événements                               |
    |*Entités affectées*||
    |  | Utilisateur                          | Utilisateur à l’origine de la violation DLP                                          | Tous les événements                               |
    |                   | Nom d'hôte                      | Nom d’hôte de l’ordinateur sur lequel la violation DLP a été détectée              | Événements de périphériques                           |
    |                   | Adresse IP                    | Adresse IP de l’ordinateur                                                  | Événements de périphériques                           |
    |                   | File path                     | Chemin d’accès absolu du fichier impliqué dans la violation                        | Événements SharePoint, OneDrive et périphériques |
    |                   | Destinataires de courrier électronique              | Destinataires du courrier électronique qui ont enfreint la stratégie DLP                       | Événements Exchange                          |
    |                   | Objet du message                 | Objet du message qui a enfreint la stratégie DLP                          | Événements Exchange                          |
    |                   | Pièces jointes             | Noms des pièces jointes dans le message électronique qui ont enfreint la stratégie DLP         | Événements Exchange                          |
    |                   | Propriétaire du site                    | Nom du propriétaire du site                                                     | Événements SharePoint et OneDrive           |
    |                   | URL du site                      | URL complète du site SharePoint ou OneDrive                                | Événements SharePoint et OneDrive           |
    |                   | Fichier créé                  | Heure de création du fichier                                                      | Événements SharePoint et OneDrive           |
    |                   | Dernière modification du fichier            | Heure de la dernière modification du fichier                                  | Événements SharePoint et OneDrive           |
    |                   | Taille des fichiers                     | Taille du fichier                                                           | Événements SharePoint et OneDrive           |
    |                   | Propriétaire du fichier                    | Propriétaire du fichier                                                          | Événements SharePoint et OneDrive           |
    |*Détails de la stratégie*||
    |     | Stratégie DLP mise en correspondance            | Nom de la stratégie DLP qui a été mise en correspondance                                    | Tous les événements                               |
    |                   | Règle mise en correspondance                  | Nom de la règle DLP dans la stratégie DLP qui a été mise en correspondance                    | Tous les événements                               |
    |                   | Types d’informations sensibles détectés | Types d’informations sensibles détectés dans le cadre de la stratégie DLP | Tous les événements                               |
    |                   | Actions prises                 | Actions effectuées dans le cadre de la stratégie DLP correspondante                          | Tous les événements                               |
    |                   | Stratégie overrode utilisateur          | Si l’utilisateur overrode la stratégie par le biais du Conseil de stratégie                | Tous les événements                               |
    |                   | Remplacer le texte de justification   | Justification fournie pour remplacer le Conseil de stratégie                          | Tous les événements                               |
    
1.  Sélectionnez l’onglet types d’informations **sensibles** pour afficher des détails sur les types d’informations sensibles détectés dans le contenu. Les détails incluent la confiance et le nombre.

2.  Après avoir examiné l’alerte, sélectionnez **Manage Alert (gérer les alertes** ) pour modifier l’État (**active**, **investigation**, **refermée**ou **résolue**). Vous pouvez également ajouter des commentaires et affecter l’alerte à une personne de votre organisation.

    -   Pour afficher l’historique de la gestion des flux de travail, choisissez **Management log**.
    -   Une fois que vous avez effectué l’action requise pour l’alerte, définissez l’état de l’alerte sur **résolu**.
