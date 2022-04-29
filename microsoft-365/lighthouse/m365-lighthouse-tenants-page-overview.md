---
title: Vue d’ensemble de la page Locataires dans Microsoft 365 Lighthouse
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
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez la page Locataires.
ms.openlocfilehash: 0f25f8bb02c6957598b2b328bc7832c429ca1e7a
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128371"
---
# <a name="overview-of-the-tenants-page-in-microsoft-365-lighthouse"></a>Vue d’ensemble de la page Locataires dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse vous permet de gérer les comptes de locataire en sélectionnant **Locataires** dans le volet de navigation gauche pour ouvrir la page Locataires. La page Locataires contient une liste de tous vos locataires. Vous pouvez sélectionner un locataire pour afficher des informations détaillées, notamment les détails du contact et l’état du déploiement.

La page Locataires comprend également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter les données du locataire vers un fichier Excel valeurs séparées par des virgules (.csv).
- **Gérer les balises :** Sélectionnez cette option pour ajouter, modifier ou supprimer une balise.
- **Attribuer des balises :** Sélectionnez cette option pour affecter une balise à un locataire.
- **Rechercher:** Entrez des mots clés pour localiser rapidement un locataire spécifique dans la liste.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-page-overview.png" alt-text="Capture d’écran de la page Locataire.":::

## <a name="tenant-list"></a>Liste des locataires

La liste des locataires fournit des insights sur les différents locataires avec lesquels vous avez un contrat, y compris leur état d’intégration lighthouse. La liste des locataires vous permet également d’étiqueter les locataires pour fournir différents filtres dans Lighthouse, et d’en savoir plus sur un locataire donné et l’état de son plan de déploiement.

Une fois que vos locataires répondent aux [exigences d’intégration de Lighthouse](m365-lighthouse-requirements.md), son état s’affiche comme **actif** dans la liste des locataires.

La liste des locataires vous permet de :

- Triez automatiquement les locataires par actif, inactif et inéligible.
- Exportez la liste des locataires.
- Attribuez et gérez des balises.
- Recherchez des locataires par nom.
- Filtrez les locataires par état, par privilège d’administration délégué (DAP) et par balise.

Pour désactiver le locataire ou afficher et gérer les balises, sélectionnez les trois points (autres actions) en regard du nom du locataire. Vous pouvez afficher des locataires individuels en sélectionnant le nom du locataire ou en sélectionnant l’une des balises affectées au locataire.

Pour plus d’informations sur l’ajout de locataires, consultez [Ajouter et gérer plusieurs locataires dans votre compte Espace partenaires](/partner-center/multi-tenant-account).

## <a name="tenant-status"></a>État du client

Le tableau suivant présente les différents états et leur signification. Pour plus d’informations sur la résolution des problèmes liés à l’état du locataire client, consultez [Résolution des problèmes et des messages d’erreur dans Microsoft 365 Lighthouse : Intégration du locataire client](m365-lighthouse-troubleshoot.md#customer-tenant-onboarding).<br><br>

| État                                   | Description                                                                                             |
|------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Actif                                   | L’intégration des locataires et le flux de données ont démarré.                                                           |
| Inactif                                 | Le locataire a été désinsgré à la demande du MSP et n’est plus géré dans Lighthouse.           |
| En cours de traitement                               | Locataire découvert, mais pas entièrement intégré.                                                              |
| Non éligible - DAP ou GDAP n’est pas configuré    | Le partenaire doit disposer de privilèges d’administrateur délégués (DAP) ou granulaires (GDAP) configurés avec le locataire. |
| Inéligible - La licence requise est manquante | Le locataire n’a pas la licence requise.                                                               |
| Non éligible - Nombre d’utilisateurs dépassé         | Le locataire a plus d’utilisateurs que ce qui est autorisé.                                                                     |
| Non éligible - Échec de la vérification géographique            | Le partenaire et le client doivent résider dans le même emplacement géographique.                                       |

Une fois que vous avez désactivé un locataire, vous ne pouvez pas agir sur le locataire tant que le processus d’inactivation n’est pas terminé. L’inactivation peut prendre jusqu’à 48 heures. Si vous décidez de réactiver un locataire, la réapparition des données peut prendre jusqu’à 48 heures.

## <a name="tenant-tags"></a>Balises de locataire

Pour organiser vos locataires et filtrer facilement les vues existantes, vous pouvez créer et attribuer des balises à vos locataires. Pour en savoir plus, consultez [Gérer votre liste de locataires dans Microsoft 365 Lighthouse](m365-lighthouse-manage-tenant-list.md).

> [!NOTE]
> Vous pouvez créer jusqu’à 30 balises sur tous les locataires.

## <a name="tenant-details-page"></a>Page détails du locataire

Pour afficher des informations détaillées sur le locataire, sélectionnez un locataire dans la liste des locataires. La page de détails du locataire contient les informations de contact et l’état du plan de déploiement.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-details-page.png" alt-text="Capture d’écran de la page détails du locataire.":::

### <a name="overview-tab"></a>Onglet Overview

Sous l’onglet Vue d’ensemble, vous pouvez afficher la vue d’ensemble du locataire, les informations de contact et Microsoft 365 l’utilisation du service.

#### <a name="tenant-overview-card"></a>Carte vue d’ensemble du locataire

La carte vue d’ensemble du locataire fournit des informations sur le locataire à partir de son compte Microsoft 365.<br><br>

| Informations sur le locataire    | Description|
|-----------------------|------------------|
| Headquarters    | Emplacement du locataire.|
| Secteur d’activité    |L’industrie de l’organisation.|
| Site web    |Site web de l’organisation. Vous pouvez modifier ce champ si aucune donnée n’est fournie.|
| Domaine du client    |Domaine de l’organisation.|
| Nombre total d'utilisateurs    |Nombre d’utilisateurs affectés dans le locataire. Vous pouvez sélectionner ce numéro pour ouvrir la page Utilisateurs de ce locataire.|
| Nombre total d’appareils|Nombre d’appareils inscrits dans le locataire. Vous pouvez sélectionner ce numéro pour ouvrir la page Appareils de ce locataire.|

#### <a name="contacts-card"></a>Carte de visite

La carte Contacts vous permet d’entrer des informations pour les contacts clés au sein des locataires que vous gérez, par exemple :

- Nom
- Titre
- Phone
- E-mail
- Notes

La section Notes est un champ de texte que vous pouvez utiliser pour enregistrer des informations clés pour le locataire, telles que les préférences d’engagement, l’emplacement, le fuseau horaire et des détails sur leur rôle au sein de l’organisation.

Pour modifier les détails ou supprimer un contact existant, sélectionnez le nom du contact dans la liste. Dans le volet **Modifier le contact** , modifiez ou supprimez le contact. Pour ajouter un autre contact, sélectionnez **+Ajouter un contact**.

#### <a name="microsoft-365-usage-card"></a>carte d’utilisation Microsoft 365

Lighthouse fournit des insights sur l’utilisation des services Microsoft 365, y compris le nombre d’utilisateurs au sein d’un locataire disposant d’une licence et utilisant activement chaque service. Active indique le nombre d’utilisateurs ou d’appareils qui se sont connectés au service au moins une fois au cours des 28 derniers jours. La modification indique la modification des utilisateurs actifs et des appareils depuis le mois dernier.

La carte d’utilisation Microsoft 365 contient deux sections :

- **Microsoft 365 Lighthouse services :** services qui peuvent être gérés dans le portail Lighthouse.
- **Services Microsoft 365 supplémentaires :** services inclus dans la suite Microsoft 365, mais qui ne peuvent pas être gérés dans le portail Microsoft 365 Lighthouse pour l’instant.

### <a name="deployment-plans-tab"></a>Onglet Plans de déploiement

L’onglet Plans de déploiement fournit l’état du plan de déploiement d’un locataire. Les étapes de déploiement de la liste sont basées sur la base de référence appliquée au locataire. Pour afficher les détails de l’étape de déploiement, sélectionnez une étape de déploiement dans la liste.

L’onglet Plans de déploiement comprend également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter les données d’étape de déploiement vers un fichier Excel valeurs séparées par des virgules (.csv).
- **Actualiser:** Sélectionnez cette option pour récupérer les données d’étape de déploiement les plus actuelles.
- **Rechercher:** Entrez des mots clés pour localiser rapidement une étape de déploiement spécifique dans la liste.

## <a name="related-content"></a>Contenu connexe

[Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)\
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)\
[Gérer votre liste de locataires dans Microsoft 365 Lighthouse](m365-lighthouse-manage-tenant-list.md) (article)\
[Vue d’ensemble de l’utilisation de Microsoft 365 Lighthouse lignes de base pour déployer des configurations de locataire standard](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (article)\
[Déployer Microsoft 365 Lighthouse lignes de base](m365-lighthouse-deploy-baselines.md) (article)
