---
title: Configurez et affichez les alertes pour les stratégies DLP (préversion)
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
description: Découvrez comment définir et gérer des alertes pour les stratégies DLP.
ms.openlocfilehash: addf46b27575f1a1cc062949aedb7ecdecaf7286
ms.sourcegitcommit: cdf2b8dad7db9e16afd339abaaa5397faf11807c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48651459"
---
# <a name="configure-and-view-alerts-for-dlp-polices-preview"></a>Configurer et afficher les alertes pour les polices DLP (aperçu)

Cet article vous montre comment définir des stratégies d’alerte enrichies liées à vos stratégies de protection contre la perte de données (DLP). Vous verrez comment utiliser le nouveau tableau de bord de gestion des alertes DLP dans le Centre de conformité [Microsoft 365](https://compliance.microsoft.com/) pour afficher les alertes, les événements et les métadonnées associées pour les violations de stratégie DLP.

## <a name="features"></a>Fonctionnalités

Les fonctionnalités suivantes font partie de cette prévisualisation :

-   **Tableau de** bord de gestion des alertes DLP : dans le Centre de conformité [Microsoft 365,](https://compliance.microsoft.com/)ce tableau de bord affiche des alertes pour les stratégies DLP appliquées sur les charges de travail suivantes :

    -   Exchange
    -   SharePoint
    -   OneDrive
    -   Teams
    -   Appareils
-   **Options de configuration d’alerte avancées**: ces options font partie du flux de authoring de stratégie DLP. Utilisez-les pour créer des configurations d’alerte enrichies. Vous pouvez créer une alerte à événement unique ou une alerte agrégée, en fonction du nombre d’événements ou de la taille des données divulguées.

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer, assurez-vous que vous avez les conditions préalables nécessaires :

-   Licences pour le tableau de bord de gestion des alertes DLP
-   Gestion des licences pour les options de configuration des alertes
-   Rôles

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licences pour le tableau de bord de gestion des alertes DLP

Tous les locataires éligibles pour Office 365 DLP peuvent accéder au nouveau tableau de bord de gestion des alertes DLP. Pour commencer, vous devez être éligible à la DLP Office 365 pour Exchange Online, SharePoint Online et OneDrive Entreprise. Pour plus d’informations sur les conditions de licence requises pour office 365 DLP, voir [quelles licences](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16)fournissent les droits d’un utilisateur pour bénéficier du service ? .

Les clients qui participent à la prévisualisation publique [DLP](https://docs.microsoft.com/microsoft-365/compliance/endpoint-dlp-learn-about?view=o365-worldwide) du point de terminaison ou qui sont éligibles pour [teams DLP](https://docs.microsoft.com/microsoft-365/compliance/dlp-microsoft-teams?view=o365-worldwide) voient leurs alertes de stratégie DLP de point de terminaison et les alertes de stratégie DLP Teams dans le tableau de bord de gestion des alertes DLP.

### <a name="licensing-for-alert-configuration-options"></a>Gestion des licences pour les options de configuration des alertes

-   **Configuration** d’alerte à événement unique : les organisations qui ont un abonnement E1, F1 ou G1 ou un abonnement E3 ou G3 peuvent créer des stratégies d’alerte uniquement lorsqu’une alerte est déclenchée chaque fois qu’une activité se produit.
-   **Configuration d’alerte agrégée**: pour configurer des stratégies d’alerte agrégées basées sur un seuil, vous devez avoir l’une des configurations suivantes :
    -   Un abonnement E5 ou G5
    -   Un abonnement E1, F1 ou G1, ou un abonnement E3 ou G3 qui inclut l’une des fonctionnalités suivantes :
        -   Office 365 – Protection avancée contre les menaces Plan 2
        -   Microsoft 365 E5 Conformité
        -   Microsoft 365 eDiscovery et licence de modules d’audit

### <a name="roles"></a>Rôles

Si vous souhaitez afficher le tableau de bord de gestion des alertes DLP ou modifier les options de configuration des alertes dans une stratégie DLP, vous devez être membre de l’un de ces groupes de rôles :

-   Administrateur de conformité
-   Administrateur de données de conformité
-   Administrateur de sécurité
-   Opérateur de sécurité
-   Lecteur de sécurité

Pour accéder au tableau de bord de gestion des alertes DLP, vous devez avoir le rôle Gérer les alertes et l’un des rôles suivants :

-   Gestion de la conformité DLP
-   View-Only de conformité DLP

## <a name="alert-configuration-experience"></a>Expérience de configuration des alertes

Si vous êtes éligible pour les options de [configuration](#licensing-for-alert-configuration-options)d’alerte agrégées, les options suivantes s’offrent à vous dans l’expérience de authoring de stratégie DLP.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Capture d’écran montrant les options des rapports d’incident pour les utilisateurs éligibles pour les options de configuration d’alerte agrégées." border="false":::

Vous pouvez utiliser ces options de configuration d’alerte pour configurer un paramètre qui définit la fréquence de correspondance d’une règle DLP avant le déclenchement d’une alerte. Cette configuration vous permet de configurer une stratégie pour générer une alerte chaque fois qu’une activité correspond aux conditions de la stratégie ou lorsqu’un certain seuil est dépassé, en fonction du nombre d’activités ou du volume de données exfiltrées.

Si vous êtes éligible pour les options de [configuration](#licensing-for-alert-configuration-options)d’alerte à événement unique, l’option de configuration d’alerte suivante s’offre à vous dans l’expérience de authoring de stratégie DLP. Utilisez cette option pour créer une alerte qui est élevée chaque fois qu’une correspondance de règle DLP se produit en raison d’une activité de l’utilisateur.

:::image type="content" source="../media/incident-reports-options-single-event-alerts.png" alt-text="Capture d’écran montrant les options des rapports d’incident pour les utilisateurs éligibles pour les options de configuration d’alerte à événement unique." border="false":::

## <a name="dlp-alert-management-dashboard"></a>Tableau de bord de gestion des alertes DLP

Pour travailler avec le tableau de bord de gestion des alertes DLP :

1.  Dans le [Centre de conformité Microsoft 365,](https://www.compliance.microsoft.com)allez à Protection contre la perte de **données.**

2.  Sélectionnez **l’onglet Alertes** pour afficher le tableau de bord des alertes DLP.

    -   Choisissez des filtres pour affiner la liste des alertes. Choisissez **Personnaliser les colonnes** pour lister les propriétés que vous souhaitez voir. Vous pouvez également choisir de trier les alertes par ordre croissant ou décroit dans n’importe quelle colonne.
    -   Sélectionnez une alerte pour voir les détails :

        :::image type="content" source="../media/alert-details.png" alt-text="Capture d’écran montrant les détails de l’alerte dans le tableau de bord de gestion des alertes DLP." border="false":::

1.  Sélectionnez **l’onglet** Événements pour afficher tous les événements associés à l’alerte. Vous pouvez choisir un événement particulier pour afficher ses détails.
    Le tableau suivant présente certains détails de l’événement.
    
    | Catégorie          | Nom de la propriété                 | Description                                                                | Types d’événements applicables                   |
    |-------------------|-------------------------------|----------------------------------------------------------------------------|------------------------------------------|
    |*Détails de l'événement*||
    |      | ID                            | ID unique associé à l’événement                                        | Tous les événements                               |
    |                   | Lieu                      | Charge de travail où l’événement a été détecté                                      | Tous les événements                               |
    |                   | Heure de l’activité              | Heure de l’activité de l’utilisateur à l’origine de la violation DLP                    | Tous les événements                               |
    |*Entités impactées*||
    |  | Utilisateur                          | Utilisateur à l’origine de la violation DLP                                          | Tous les événements                               |
    |                   | Nom d'hôte                      | Nom d’hôte de l’ordinateur sur lequel la violation DLP a été détectée              | Événements d’appareils                           |
    |                   | Adresse IP                    | Adresse IP de l’ordinateur                                                  | Événements d’appareils                           |
    |                   | File path                     | Chemin d’accès absolu du fichier impliqué dans la violation                        | Événements SharePoint, OneDrive et Appareils |
    |                   | Destinataires d’un e-mail              | Destinataires de l’e-mail qui a enfreint la stratégie DLP                       | Événements Exchange                          |
    |                   | Objet de l’e-mail                 | Objet de l’e-mail qui a enfreint la stratégie DLP                          | Événements Exchange                          |
    |                   | Pièces jointes             | Noms des pièces jointes dans l’e-mail qui ont enfreint la stratégie DLP         | Événements Exchange                          |
    |                   | Propriétaire du site                    | Nom du propriétaire du site                                                     | Événements SharePoint et OneDrive           |
    |                   | URL du site                      | URL complète du site SharePoint ou OneDrive                                | Événements SharePoint et OneDrive           |
    |                   | Fichier créé                  | Heure de création du fichier                                                      | Événements SharePoint et OneDrive           |
    |                   | Dernier fichier modifié            | Heure de la dernière modification du fichier                                  | Événements SharePoint et OneDrive           |
    |                   | Taille des fichiers                     | Taille du fichier                                                           | Événements SharePoint et OneDrive           |
    |                   | Propriétaire du fichier                    | Propriétaire du fichier                                                          | Événements SharePoint et OneDrive           |
    |*Détails de la stratégie*||
    |     | Stratégie DLP en correspondance            | Nom de la stratégie DLP qui a été correspondance                                    | Tous les événements                               |
    |                   | Règle en correspondance                  | Nom de la règle DLP dans la stratégie DLP qui a été correspondance                    | Tous les événements                               |
    |                   | Types d’informations sensibles détectés | Types d’informations sensibles détectés dans le cadre de la stratégie DLP | Tous les événements                               |
    |                   | Actions prises                 | Actions prises dans le cadre de la stratégie DLP de correspondance                          | Tous les événements                               |
    |                   | Stratégie de overrode par l’utilisateur          | Si l’utilisateur a overrode la stratégie via le conseil de stratégie                | Tous les événements                               |
    |                   | Remplacer le texte de justification   | Justification fournie pour remplacer le conseil de stratégie                          | Tous les événements                               |
    
1.  Sélectionnez **l’onglet Types d’informations** sensibles pour afficher les détails sur les types d’informations sensibles détectés dans le contenu. Les détails incluent la confiance et le nombre.

2.  Après avoir examiné l’alerte, choisissez **Gérer** l’alerte pour modifier l’état (**Actif** **,** En cours d’examen, Rejeté ou **Résolu**). Vous pouvez également ajouter des commentaires et affecter l’alerte à une personne de votre organisation.

    -   Pour consulter l’historique de la gestion des flux de travail, sélectionnez **Journal de gestion.**
    -   Une fois que vous avez pris l’action requise pour l’alerte, définissez l’état de l’alerte **sur Résolu.**
