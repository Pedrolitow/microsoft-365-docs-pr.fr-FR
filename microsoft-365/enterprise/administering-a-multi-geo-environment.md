---
title: Comportement du service dans un environnement multigéographique
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Les administrateurs peuvent découvrir comment administrer les services SharePoint et OneDrive dans un environnement multigéographique.
ms.openlocfilehash: ae6673488e552e1da9acd14526194734d194c305
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68803614"
---
# <a name="service-behavior-a-multi-geo-enabled-environment"></a>Comportement du service : environnement multigéographique

Voici un aperçu du fonctionnement des services Microsoft 365 dans un environnement multigéographique.

## <a name="administrator-experience"></a>Expérience de l’administrateur

Le Centre d’administration SharePoint comporte un [onglet **Emplacements géographiques**](https://go.microsoft.com/fwlink/?linkid=2185076) dans le volet de navigation de gauche qui présente une carte des emplacements géographiques où vous pouvez afficher et gérer vos emplacements géographiques. Utilisez cette page pour ajouter ou supprimer des emplacements géographiques pour votre _locataire_.

## <a name="audit-log-search"></a>Recherche de journal d’audit

Un [journal d’audit](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) unifié pour tous vos emplacements _géographiques satellites_ est disponible à partir de la page de recherche du journal d’audit Microsoft 365. Vous pouvez consulter toutes les entrées de journal d’audit des emplacements géographiques. Par exemple, les activités des utilisateurs dans les régions NAM et EUR apparaissent dans un seul affichage, et vous pouvez appliquer les filtres existants pour voir les activités de certains utilisateurs.

> [!NOTE]
> Les événements d’audit de l’administrateur Exchange sont disponibles uniquement pour l’emplacement par défaut.

## <a name="bcs-secure-store-apps"></a>BCS, service Banque d’informations sécurisé, applications

BCS, le service Banque d’informations sécurisé et les applications ont des instances distinctes dans chaque emplacement satellite. Ainsi, l’administrateur SharePoint Online doit gérer et configurer ces services séparément à partir de chaque emplacement satellite.

## <a name="compliance-admin-center"></a>Centre d’administration de la conformité

Il existe un portail de conformité Microsoft Purview central pour un _locataire_ multigéographique : le [centre d’administration Microsoft Purview](https://compliance.microsoft.com/).

## <a name="ediscovery"></a>eDiscovery

Par défaut, un gestionnaire eDiscovery ou un administrateur d’un _locataire_ multigéographique ne peut effectuer eDiscovery que dans la _zone géographique approvisionnée principale_ de ce _locataire_. L’administrateur général Office 365 doit affecter les autorisations de gestionnaire eDiscovery pour autoriser d’autres personnes à mettre en place un processus eDiscovery, et affecter un paramètre "Région" dans le filtre de sécurité de conformité correspondant pour définir la région concernée par le processus comme emplacement satellite. Sinon, aucun processus eDiscovery n’est mis en place à l’emplacement satellite. Pour configurer le filtre de sécurité de la conformité pour une région, voir [Configurer l’eDiscovery d’Office 365 multigéographique](multi-geo-ediscovery-configuration.md).

## <a name="exchange-online-mailboxes"></a>Echange de boîtes aux lettres en ligne

Les boîtes aux lettres Exchange Online des utilisateurs sont déplacées automatiquement si leur PDL est modifié. Lorsqu’une boîte aux lettres est créée, elle est approvisionnée sur le PDL de l’utilisateur ou à l’emplacement central si aucune valeur n’a été définie pour le PDL de l’utilisateur.

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>stratégie de protection contre la perte de données (DLP) Information Protection (IP)

Vous pouvez définir vos stratégies DLP IP pour OneDrive Entreprise, SharePoint Online et Exchange Online dans le centre sécurité et conformité, et définir des stratégies d’étendue en fonction des besoins de l’ensemble du _locataire_ ou des utilisateurs concernés. Par exemple : si vous souhaitez sélectionner une stratégie pour un utilisateur dans un emplacement satellite, choisissez d’appliquer la stratégie à un OneDrive Entreprise spécifique et entrez l’URL de OneDrive Entreprise de l’utilisateur. Pour accéder à des instructions générales concernant la création de stratégies de protection contre la perte de données, voir [Vue d’ensemble des stratégies de protection contre la perte de données](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e).

Les stratégies DLP sont synchronisées automatiquement en fonction de leurs conditions d’application à chaque emplacement géographique.

L’implémentation de stratégies de Information Protection et de Protection contre la perte de données Microsoft Purview à tous les utilisateurs d’un emplacement géographique n’est pas une option disponible dans l’interface utilisateur. Vous devez plutôt sélectionner les comptes applicables pour la stratégie ou appliquer la stratégie globalement à tous les comptes.

## <a name="microsoft-power-apps"></a>Microsoft Power Apps

Les applications Power Apps créées pour l’emplacement satellite utilisent le point de terminaison situé dans l’emplacement central du _locataire_. Microsoft Power Apps n’est pas un service multigéographique. 

## <a name="microsoft-power-automate"></a>Microsoft Power Automate

Les flux créés pour l’emplacement satellite utilisent le point de terminaison situé dans l’emplacement géographique par défaut du _locataire_.  Microsoft Power Automate n’est pas un service multigéographique. 

## <a name="sharepoint-online-storage-quota"></a>Quota de stockage SharePoint Online

Par défaut, tous les emplacements géographiques d’un environnement multigéographique partagent le quota de stockage _client_ disponible.  Vous pouvez également gérer le quota de stockage en allouant un quota spécifique à un emplacement géographique particulier. Pour plus d’informations, voir [Quotas de stockage SharePoint dans des environnements multigéographiques](sharepoint-multi-geo-storage-quota.md).

## <a name="sharing"></a>Partage

Les administrateurs peuvent définir et gérer des stratégies de partage pour chacun de leurs emplacements. Les sites OneDrive Entreprise et SharePoint Online dans chaque emplacement géographique respectent uniquement les paramètres de partage spécifiques à la zone géographique correspondante. (Par exemple, vous pouvez autoriser le [partage externe](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) pour votre emplacement central, mais pas pour votre emplacement satellite ou vice versa.) Notez que les paramètres de partage n’autorisent pas la configuration des limitations de partage entre les emplacements géographiques.

## <a name="microsoft-stream"></a>Microsoft Stream

Les vidéos chargées vers Microsoft Stream dans une conversation 1:1 sont stockées dans le OneDrive Entreprise de la personne chargée. Les enregistrements de réunion sont stockés dans le OneDrive Entreprise de chaque participant qui enregistre la réunion.

## <a name="taxonomy"></a>Taxonomie

Nous prenons en charge une [taxonomie](/sharepoint/managed-metadata) unifiée pour les métadonnées gérées par l’entreprise entre les emplacements géographiques, le maître étant hébergé à l’emplacement central de votre entreprise. Nous vous recommandons de gérer votre taxonomie globale à partir de l’emplacement central et d’ajouter uniquement des termes spécifiques à la taxonomie de l’emplacement satellite. Les termes de la taxonomie globale sont synchronisés avec les emplacements satellites.

Pour plus d’informations et pour obtenir des conseils pour les développeurs, consultez [Gérer les métadonnées dans un locataire multigéographique](/sharepoint/dev/solution-guidance/multigeo-managedmetadata) .

## <a name="user-profile-application"></a>Application de profil utilisateur

Il existe une [application de profil utilisateur](/sharepoint/manage-user-profiles) dans chaque emplacement géographique. Les informations de profil de chaque utilisateur sont hébergées dans l’emplacement géographique de celui-ci et accessibles à l’administrateur de cet emplacement.

Si vous avez des propriétés de profil personnalisées, nous vous recommandons d’utiliser le même schéma de profil dans toutes les zones géographiques et de remplir vos propriétés de profil personnalisées dans tous les emplacements géographiques ou dans les emplacements requis. Pour savoir comment remplir les données de profil utilisateur par programme, consultez l’[API de mise à jour en bloc de profil utilisateur](/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

Pour plus d’informations et pour obtenir des conseils pour les développeurs, consultez [Utiliser des profils utilisateur dans un locataire multigéographique](/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) .

## <a name="yammer"></a>Yammer

Yammer n’est pas une charge de travail multigéographique. Les threads Yammer stockés dans Yammer seront placés à _l’emplacement central du locataire_ . Yammer déploie une modification de stockage de fichiers qui stockera les fichiers Yammer dans SharePoint. Les fichiers Yammer stockés dans SharePoint seront placés sur le site SharePoint associé au groupe Yammer. Les sites de groupe SharePoint sont basés sur la logique PDL décrite dans [Sites et groupes SharePoint](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md#sharepoint-sites-and-groups).
