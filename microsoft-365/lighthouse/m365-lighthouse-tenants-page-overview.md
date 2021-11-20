---
title: vue d Microsoft 365 Lighthouse de la page Des locataires de l’Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez la page Clients.
ms.openlocfilehash: 7cddf67bce3a568ea0b5259b7012a7263012d18b
ms.sourcegitcommit: 2ea2105d40b60a87fc9aa30f392a73a3a9db6d99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2021
ms.locfileid: "61129074"
---
# <a name="microsoft-365-lighthouse-tenants-page-overview"></a>vue d Microsoft 365 Lighthouse de la page Des locataires de l’Microsoft 365 Lighthouse

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences.](m365-lighthouse-requirements.md) Si votre organisation n’a pas Microsoft 365 Lighthouse, [consultez s’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse vous permet de gérer les comptes  des locataires en sélectionnant Les locataires dans le volet de navigation de gauche pour ouvrir la page Locataires. La page Locataires contient la liste de tous vos locataires. Vous pouvez sélectionner un client pour afficher des informations détaillées, y compris les coordonnées et l’état du déploiement.

La page Locataires inclut également les options suivantes :

- **Exporter :** Sélectionnez cette sélection pour exporter les données client vers Excel fichier de valeurs séparées par des virgules (.csv).
- **Gérer les balises :** Sélectionnez pour ajouter, modifier ou supprimer une balise.
- **Assigner des balises :** Sélectionnez cette sélection pour affecter une balise à un client.
- **Recherche :** Entrez des mots clés pour localiser rapidement un client spécifique dans la liste.


:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-page-overview.png" alt-text="Capture d’écran de la page Client.":::

## <a name="tenant-list"></a>Liste des locataires

La liste des locataires fournit des informations sur les différents locataires avec lesquels vous avez un contrat, y compris leur statut d’intégration client. La liste des locataires vous permet également de baliser les locataires pour fournir différents filtres tout au long du projet et d’en savoir plus sur un client donné et l’état de son plan de déploiement.

Une fois que vos clients répondent aux [exigences d’intégration de Onboard,](m365-lighthouse-requirements.md)son état s’affiche **comme actif** dans la liste des clients.

La liste des locataires vous permet de :

- Trier automatiquement les locataires par actif, inactif et non éligible.
- Exporter la liste des locataires
- Affecter et gérer des balises
- Rechercher des locataires par nom
- Filtrer les clients par état, privilèges d’administration délégués (DAP) et balises.

Pour désactiver le client ou afficher et gérer les balises, sélectionnez les trois points en regard du nom du client. Vous pouvez afficher des locataires individuels en sélectionnant le nom du client ou en sélectionnant l’une des balises affectées au client.

## <a name="tenant-status"></a>État du client

Le tableau suivant indique les différents états et leur signification.

| État                                | Description                                         |
|---------------------------------------|-----------------------------------------------------|
| Actif                                | L’intégration et le flux de données ont démarré.               |
| Inactif                              | Le client n’est plus actif.                         |
| In process                            | Client découvert, mais pas entièrement intégré.         |
| Accès délégué non éligible requis | La configuration des privilèges d’administration délégués (DAP) est requise. |
| Inéligible, Missing required license  | Le client n’a pas de licence requise.              |
| Inéligible, Nombre d’utilisateurs dépassé       | Le client compte plus d’utilisateurs que le nombre autorisé.                 |
| Inéligible, Type de contrat             | Le client n’a pas de contrat.                    |

Une fois que vous avez désactivé un client, vous ne pouvez pas agir sur le client tant que le processus d’inactivation n’est pas terminé. L’inactivation peut prendre jusqu’à 48 heures. Si vous décidez de réactiver un client, la réapparition des données peut prendre jusqu’à 48 heures.

## <a name="tenant-tags"></a>Balises de client

Pour organiser vos clients et filtrer facilement les affichages existants, vous pouvez créer et affecter des balises à vos clients. Pour plus d’informations, [voir Gérer votre liste de locataires.](m365-lighthouse-manage-tenant-list.md)

> [!NOTE]
> Vous pouvez créer jusqu’à 30 balises sur l’ensemble du client.


## <a name="tenant-details-page"></a>Page des détails du client

Pour afficher des informations détaillées sur le client, sélectionnez un client dans la liste des locataires. La page des détails du client contient les informations de contact et l’état du plan de déploiement.


:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-details-page.png" alt-text="Capture d’écran de la page détails du client.":::

### <a name="overview-tab"></a>Onglet Overview

Sous l’onglet Vue d’ensemble, vous pouvez afficher la vue d’ensemble du client, les informations de contact et Microsoft 365'utilisation du service.

#### <a name="tenant-overview-card"></a>Carte de vue d’ensemble du client

La carte de présentation du client fournit des informations sur le client à partir de son Microsoft 365 client.

| Informations sur le client    | Description|
|-----------------------|------------------|
| Headquarters    | Emplacement du client.|
| Secteur d’activité    |Secteur d’activité de l’organisation.|
| Site web    |Site web de l’organisation. Vous pouvez modifier ce champ si aucune donnée n’est fournie.|
| Domaine client    |Domaine de l’organisation.|
| Nombre total d'utilisateurs    |Nombre d’utilisateurs affectés au client. Vous pouvez sélectionner ce numéro pour ouvrir la page Utilisateurs pour ce client.|
| Nombre total d’appareils|Nombre d’appareils inscrits dans le client. Vous pouvez sélectionner ce numéro pour ouvrir la page Appareils pour ce client.|

#### <a name="contacts-card"></a>Carte de contacts

La carte contacts vous permet d’entrer des informations pour les contacts clés au sein des locataires que vous gérez, telles que :

- Nom
- Titre
- Téléphone
- E-mail
- Notes

La section Notes est un champ de texte que vous pouvez utiliser pour enregistrer des informations clés pour le client, telles que les préférences d’engagement, l’emplacement, le fuseau horaire et des détails sur leur rôle au sein de l’organisation.

Pour modifier les détails ou supprimer un contact existant, sélectionnez le nom du contact dans la liste. Dans le **volet Modifier le contact,** modifiez ou supprimez le contact. Pour ajouter un autre contact, **sélectionnez +Ajouter un contact.**

#### <a name="microsoft-365-usage-card"></a>Microsoft 365 d’utilisation

Il fournit des informations sur Microsoft 365'utilisation des services, notamment le nombre d’utilisateurs au sein d’un client qui disposent d’une licence et utilisent activement chaque service. Active indique le nombre d’utilisateurs ou d’appareils qui se sont connectés au service au moins une fois au cours des 28 derniers jours. La modification indique la modification des utilisateurs et des appareils actifs depuis le mois dernier.

La carte Microsoft 365'utilisation de l’ordinateur contient deux sections :

- Microsoft 365 Lighthouse services activés : services qui peuvent être gérés au sein du portail De la sécurité.
- Services Microsoft 365 supplémentaires : services qui sont inclus dans la suite Microsoft 365 mais qui ne peuvent pas être gérés dans le portail Microsoft 365 Lighthouse pour le moment.


### <a name="deployment-plans-tab"></a>Onglet Plans de déploiement

L’onglet Plans de déploiement fournit l’état du plan de déploiement d’un client. Les étapes de déploiement de la liste sont basées sur la ligne de base appliquée au client. Pour voir les détails de l’étape de déploiement, sélectionnez une étape de déploiement dans la liste.

L’onglet Plans de déploiement inclut également les options suivantes :

- **Exporter :** Choisissez d’exporter les données de l’étape de déploiement vers Excel fichier de valeurs séparées par des virgules (.csv).
- **Actualiser :** Sélectionnez pour récupérer les données d’étape de déploiement les plus récentes.
- **Recherche :** Entrez des mots clés pour localiser rapidement une étape de déploiement spécifique dans la liste.

## <a name="related-content"></a>Contenu connexe

[Conditions requises pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)\
[Gérer votre liste de locataires](m365-lighthouse-manage-tenant-list.md) (article)\
[Vue d’ensemble de l’utilisation des lignes de base pour déployer](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) des configurations client standard (article)\
[Déployer Microsoft 365 Lighthouse de référence (article)](m365-lighthouse-deploy-baselines.md)
