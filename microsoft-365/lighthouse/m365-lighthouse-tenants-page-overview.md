---
title: Vue d’ensemble de la page Clients de Microsoft 365
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
description: Pour les fournisseurs de services gérés (MSP) à l’aide de Microsoft 365 Etomp, découvrez la page Clients.
ms.openlocfilehash: 23f151664455c35bb2fcc191d774ead00927e830
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329990"
---
# <a name="microsoft-365-lighthouse-tenants-page-overview"></a>Vue d’ensemble de la page Clients de Microsoft 365

Microsoft 365 Permet de gérer les comptes clients en sélectionnant Clients dans le  volet de navigation de gauche pour ouvrir la page Clients. La page Locataires contient la liste de tous vos locataires. Vous pouvez sélectionner un client pour afficher des informations détaillées, y compris les coordonnées et l’état du déploiement.

La page Locataires inclut également les options suivantes :

- **Exporter :** Sélectionnez cette sélection pour exporter des données client vers un fichier de valeurs séparées par des virgules (.csv) Excel.
- **Gérer les balises :** Sélectionnez pour ajouter, modifier ou supprimer une balise.
- **Assigner des balises :** Sélectionnez cette sélection pour affecter une balise à un client.
- **Recherche :** Entrez des mots clés pour localiser rapidement un client spécifique dans la liste.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-page-overview.png" alt-text="Capture d’écran de la page Client.":::

## <a name="tenant-list"></a>Liste des locataires

La liste des locataires fournit des informations sur les différents locataires avec lesquels vous avez un contrat, y compris leur statut d’intégration client. La liste des locataires vous permet également de baliser les locataires pour fournir différents filtres tout au long du projet et d’en savoir plus sur un client donné et l’état de son plan de déploiement.

Une fois que vos clients répondent aux [exigences d’intégration de Onboard](m365-lighthouse-requirements.md), son état s’affiche **comme actif** dans la liste des clients.

La liste des locataires vous permet de :

- Trier automatiquement les locataires par actif, inactif et non éligible.
- Exportez la liste des locataires.
- Affecter et gérer des balises.
- Recherchez des locataires par nom.
- Filtrer les clients par état, privilèges d’administration délégués (DAP) et balises.

Pour désactiver le client ou afficher et gérer les balises, sélectionnez les trois points (autres actions) en regard du nom du client. Vous pouvez afficher des locataires individuels en sélectionnant le nom du client ou en sélectionnant l’une des balises affectées au client.

## <a name="tenant-status"></a>État du client

Le tableau suivant indique les différents états et leur signification.<br><br>

| État                                   | Description                                                                                             |
|------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Actif                                   | L’intégration du client et le flux de données ont démarré.                                                           |
| Inactif                                 | Le client a été mis hors carte à la demande du MSP et n’est plus géré dans le Jeu d’enfants.           |
| In process                               | Client découvert, mais pas entièrement intégré.                                                              |
| Inéligible - DAP ou GDAP n’est pas installé    | Le partenaire doit avoir des privilèges d’administrateur délégués (DAP) ou délégués granulaires (GDAP) à configurer avec le client. |
| Inéligible - La licence requise est manquante | Le client n’a pas la licence requise.                                                               |
| Inéligible : nombre d’utilisateurs dépassé         | Le client compte plus d’utilisateurs que le nombre autorisé.                                                                     |
| Inéligible - Échec de la vérification géographique            | Le partenaire et le client doivent résider dans le même emplacement géographique.                                       |

Une fois que vous avez désactivé un client, vous ne pouvez pas agir sur le client tant que le processus d’inactivation n’est pas terminé. L’inactivation peut prendre jusqu’à 48 heures. Si vous décidez de réactiver un client, la réapparition des données peut prendre jusqu’à 48 heures.

## <a name="tenant-tags"></a>Balises de client

Pour organiser vos clients et filtrer facilement les affichages existants, vous pouvez créer et affecter des balises à vos clients. Pour plus d’informations, [voir Gérer votre liste de locataires](m365-lighthouse-manage-tenant-list.md).

> [!NOTE]
> Vous pouvez créer jusqu’à 30 balises sur l’ensemble du client.

## <a name="tenant-details-page"></a>Page des détails du client

Pour afficher des informations détaillées sur le client, sélectionnez un client dans la liste des locataires. La page des détails du client contient les informations de contact et l’état du plan de déploiement.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-details-page.png" alt-text="Capture d’écran de la page détails du client.":::

### <a name="overview-tab"></a>Onglet Overview

Sous l’onglet Vue d’ensemble, vous pouvez afficher la vue d’ensemble du client, les informations de contact et l’utilisation du service Microsoft 365.

#### <a name="tenant-overview-card"></a>Carte de vue d’ensemble du client

La carte de présentation du client fournit des informations sur le client à partir de son compte Microsoft 365.<br><br>

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
- Phone
- E-mail
- Remarques

La section Notes est un champ de texte que vous pouvez utiliser pour enregistrer des informations clés pour le client, telles que les préférences d’engagement, l’emplacement, le fuseau horaire et des détails sur leur rôle au sein de l’organisation.

Pour modifier les détails ou supprimer un contact existant, sélectionnez le nom du contact dans la liste. Dans le **volet Modifier le contact** , modifiez ou supprimez le contact. Pour ajouter un autre contact, **sélectionnez +Ajouter un contact**.

#### <a name="microsoft-365-usage-card"></a>Carte d’utilisation Microsoft 365

Il fournit des informations sur l’utilisation des services Microsoft 365, notamment le nombre d’utilisateurs au sein d’un client qui disposent d’une licence et utilisent activement chaque service. Active indique le nombre d’utilisateurs ou d’appareils qui se sont connectés au service au moins une fois au cours des 28 derniers jours. La modification indique la modification des utilisateurs et des appareils actifs depuis le mois dernier.

La carte d’utilisation Microsoft 365 contient deux sections :

- **Services microsoft 365 à l’aide du logiciel en ligne :** Services qui peuvent être gérés au sein du portail Du portail Dente.
- **Services Microsoft 365 supplémentaires :** Services inclus dans la suite Microsoft 365, mais qui ne peuvent pas être gérés dans le portail Microsoft 365 Portal pour le moment.

### <a name="deployment-plans-tab"></a>Onglet Plans de déploiement

L’onglet Plans de déploiement fournit l’état du plan de déploiement d’un client. Les étapes de déploiement de la liste sont basées sur la ligne de base appliquée au client. Pour voir les détails de l’étape de déploiement, sélectionnez une étape de déploiement dans la liste.

L’onglet Plans de déploiement inclut également les options suivantes :

- **Exporter :** Sélectionnez cette étape pour exporter les données de l’étape de déploiement vers un fichier de valeurs séparées par des virgules (.csv) Excel.
- **Actualiser :** Sélectionnez pour récupérer les données d’étape de déploiement les plus récentes.
- **Recherche :** Entrez des mots clés pour localiser rapidement une étape de déploiement spécifique dans la liste.

## <a name="related-content"></a>Contenu associé

[Conditions requises pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)\
[Gérer votre liste de locataires](m365-lighthouse-manage-tenant-list.md) (article)\
[Vue d’ensemble de l’utilisation des lignes de base pour déployer des configurations client standard](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (article)\
[Déployer les Microsoft 365 Lighthouse base de référence](m365-lighthouse-deploy-baselines.md) (article)
