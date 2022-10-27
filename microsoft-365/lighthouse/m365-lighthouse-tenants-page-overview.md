---
title: Vue d’ensemble de la page Locataires dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: kywirpel
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, découvrez la page Locataires.
ms.openlocfilehash: 59b1071aa698e6e44086223c2388bc4746a11347
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68734492"
---
# <a name="overview-of-the-tenants-page-in-microsoft-365-lighthouse"></a>Vue d’ensemble de la page Locataires dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse vous permet de gérer les comptes de locataire en sélectionnant **Locataires** dans le volet de navigation gauche pour ouvrir la page Locataires. La page Locataires contient une liste de tous vos locataires. Vous pouvez sélectionner un locataire pour afficher des informations détaillées, notamment les coordonnées et l’état du déploiement.

La page Locataires inclut également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter les données client vers un fichier de valeurs séparées par des virgules (.csv) Excel.
- **Gérer les étiquettes :** Sélectionnez cette option pour ajouter, modifier ou supprimer une balise.
- **Affecter des étiquettes :** Sélectionnez cette option pour affecter une balise à un locataire.
- **Rechercher:** Entrez des mots clés pour localiser rapidement un locataire spécifique dans la liste.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-page-overview.png" alt-text="Capture d’écran de la page Locataire.":::

## <a name="tenant-list"></a>Liste des locataires

La liste des locataires fournit des insights sur les différents locataires avec lesquels vous avez un contrat, y compris l’état d’intégration lighthouse de leur locataire. La liste des locataires vous permet également d’étiqueter les locataires pour fournir différents filtres dans Lighthouse et d’en savoir plus sur un locataire donné et l’état de son plan de déploiement.

Une fois que vos locataires répondent aux [exigences d’intégration lighthouse](m365-lighthouse-requirements.md), son état s’affiche comme **Actif** dans la liste des locataires.

La liste des locataires vous permet d’effectuer les tâches suivantes :

- Triez automatiquement les locataires par actif, inactif et inéligible.
- Exportez la liste des locataires.
- Attribuer et gérer des étiquettes.
- Recherchez les locataires par nom.
- Filtrez les locataires par état, privilège d’administration délégué (DAP) et étiquettes.

Pour désactiver le locataire ou afficher et gérer les balises, sélectionnez les trois points (autres actions) en regard du nom du locataire. Vous pouvez afficher des locataires individuels en sélectionnant le nom du locataire ou en sélectionnant l’une des balises attribuées au locataire.

Pour plus d’informations sur l’ajout de locataires, consultez [Ajouter et gérer plusieurs locataires dans votre compte Espace partenaires](/partner-center/multi-tenant-account).

## <a name="tenant-status"></a>État du client

Le tableau suivant présente les différents états et leur signification. Pour plus d’informations sur la façon de résoudre les problèmes liés aux états des locataires des clients, consultez [Résoudre les problèmes et les messages d’erreur dans Microsoft 365 Lighthouse : Intégration du locataire client](m365-lighthouse-troubleshoot.md#customer-tenant-onboarding).<br><br>

| État                                   | Description                                                                                             |
|------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Actif                                   | L’intégration des locataires et le flux de données ont démarré.                                                           |
| Inactif                                 | Le locataire a été désactivé à la demande du MSP et n’est plus géré dans Lighthouse.           |
| En cours de traitement                               | Locataire découvert mais pas entièrement intégré.                                                              |
| Inéligible : DAP ou GDAP n’est pas configuré    | Le partenaire doit disposer de privilèges d’administrateur délégués (DAP) ou délégués granulaires (GDAP) configurés avec le locataire. |
| Inéligible : la licence requise est manquante | Le locataire ne dispose pas de la licence requise.                                                               |
| Inéligible - Nombre d’utilisateurs dépassé         | Le locataire a plus d’utilisateurs que ce qui est autorisé.                                                                     |
| Inéligible - Échec de la vérification géographique            | Le partenaire et le client doivent résider dans le même emplacement géographique.                                       |

Une fois que vous avez désactivé un locataire, vous ne pouvez pas agir sur le locataire tant que le processus d’inactivation n’est pas terminé. L’inactivation peut prendre jusqu’à 48 heures. Si vous décidez de réactiver un locataire, la réapparition des données peut prendre jusqu’à 48 heures.

## <a name="tenant-tags"></a>Balises de locataire

Pour vous aider à organiser vos locataires et à filtrer facilement les vues existantes, vous pouvez créer et attribuer des étiquettes à vos locataires. Pour plus d’informations, consultez [Gérer votre liste de locataires dans Microsoft 365 Lighthouse](m365-lighthouse-manage-tenant-list.md).

> [!NOTE]
> Vous pouvez créer jusqu’à 30 balises sur l’ensemble du locataire.

## <a name="tenant-details-page"></a>Page détails du locataire

Pour afficher des informations détaillées sur le locataire, sélectionnez un locataire dans la liste des locataires. La page détails du locataire contient les informations de contact et l’état du plan de déploiement.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-details-page.png" alt-text="Capture d’écran de la page Détails du locataire.":::

### <a name="overview-tab"></a>Onglet Overview

Sous l’onglet Vue d’ensemble, vous pouvez afficher la vue d’ensemble du locataire, les informations de contact et l’utilisation du service Microsoft 365.

#### <a name="tenant-overview-section"></a>Section Vue d’ensemble du locataire

La section Vue d’ensemble du locataire fournit des informations sur le locataire à partir de son compte Microsoft 365.<br><br>

| Informations sur le locataire    | Description|
|-----------------------|------------------|
| Headquarters    | Emplacement du locataire.|
| Secteur d’activité    |L’industrie de l’organisation.|
| Site web    |Site web de l’organisation. Vous pouvez modifier ce champ si aucune donnée n’est fournie.|
| Domaine client    |Domaine de l’organisation.|
| Nombre total d'utilisateurs    |Nombre d’utilisateurs affectés dans le locataire. Vous pouvez sélectionner ce numéro pour ouvrir la page Utilisateurs de ce locataire.|
| Nombre total d’appareils|Nombre d’appareils inscrits dans le locataire. Vous pouvez sélectionner ce numéro pour ouvrir la page Appareils de ce locataire.|

#### <a name="contacts-section"></a>Section Contacts

La section Contacts fournit des informations sur les contacts clés au sein des locataires que vous gérez, par exemple :

- Nom
- Titre
- Phone
- E-mail
- Remarques

La colonne **Notes** affiche des informations pour le locataire, telles que les préférences d’engagement, l’emplacement, le fuseau horaire et des détails sur son rôle au sein de l’organisation.

Pour modifier des détails, ajouter des notes ou supprimer un contact existant, sélectionnez le nom du contact dans la liste. Dans le volet **Modifier le contact** , modifiez ou supprimez le contact. Pour ajouter un autre contact, sélectionnez **+Ajouter un contact**.

#### <a name="microsoft-365-services-usage-section"></a>Section Utilisation des services Microsoft 365

Lighthouse fournit des informations sur l’utilisation des services Microsoft 365, notamment le nombre d’utilisateurs au sein d’un locataire disposant d’une licence et utilisant activement chaque service. La colonne **Utilisateurs actifs & appareils** indique le nombre d’utilisateurs ou d’appareils qui se sont connectés au service au moins une fois au cours des 28 derniers jours. La colonne **Modification de l’activité** indique la modification des utilisateurs et appareils actifs depuis le mois dernier.

La section **Utilisation des services Microsoft 365** contient deux sous-sections :

- **Microsoft 365 Lighthouse services compatibles :** services qui peuvent être gérés dans le portail Lighthouse.
- **Services Microsoft 365 supplémentaires :** Les services inclus dans la suite Microsoft 365, mais qui ne peuvent pas être gérés dans le portail Microsoft 365 Lighthouse pour l’instant.

### <a name="deployment-plan-tab"></a>Onglet Plan de déploiement

L’onglet Plans de déploiement fournit l’état du plan de déploiement d’un locataire. Les étapes de déploiement de la liste sont basées sur la base de référence appliquée au locataire. Pour afficher les détails de l’étape de déploiement, sélectionnez une étape de déploiement dans la liste.

L’onglet Plan de déploiement inclut également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter les données de l’étape de déploiement vers un fichier de valeurs séparées par des virgules (.csv) Excel.
- **Actualiser:** Sélectionnez cette option pour récupérer les données d’étape de déploiement les plus actuelles.
- **Rechercher:** Entrez des mots clés pour localiser rapidement une étape de déploiement spécifique dans la liste.

## <a name="related-content"></a>Contenu associé

[Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)\
[Gérer votre liste de locataires dans Microsoft 365 Lighthouse](m365-lighthouse-manage-tenant-list.md) (article)\
[Vue d’ensemble de l’utilisation des bases de référence Microsoft 365 Lighthouse pour déployer des configurations de locataire standard](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (article)\
[Déployer des bases de référence Microsoft 365 Lighthouse](m365-lighthouse-deploy-baselines.md) (article)
