---
title: Administration d’un environnement multigéographique
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Normal
description: Les administrateurs peuvent découvrir comment administrer SharePoint et OneDrive services dans un environnement multigéogé.
ms.openlocfilehash: 5089a63f4c4f3406c146188151a145cf4b6aa7f2
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59202247"
---
# <a name="administering-a-multi-geo-environment"></a>Administration d’un environnement multigéographique

Découvrez le fonctionnement des services Microsoft 365 dans un environnement multigéographique.

## <a name="administrator-experience"></a>Expérience de l’administrateur

Le [centre SharePoint’administration](https://admin.microsoft.com/sharepoint)  dispose d’un onglet Emplacements géographiques dans le navigation de gauche qui comporte une carte d’emplacements géographiques où vous pouvez afficher et gérer vos emplacements géographiques. Utilisez cette page pour ajouter ou supprimer des emplacements géographiques pour votre client.

## <a name="audit-log-search"></a>Recherche de journal d’audit

Un [journal d’audit](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) unifié pour vos emplacements satellites est disponible dans la page de recherche dans le journal d’audit de Microsoft 365. Vous pouvez consulter toutes les entrées de journal d’audit des emplacements géographiques. Par exemple, les activités des utilisateurs dans les régions NAM et EUR apparaissent dans un seul affichage, et vous pouvez appliquer les filtres existants pour voir les activités de certains utilisateurs.

## <a name="bcs-secure-store-apps"></a>BCS, service Banque d’informations sécurisé, applications

BCS, le service Banque d’informations sécurisé et les applications ont des instances distinctes dans chaque emplacement satellite. Ainsi, l’administrateur SharePoint Online doit gérer et configurer ces services séparément à partir de chaque emplacement satellite.

## <a name="compliance-admin-center"></a>Centre d’administration de la conformité

Il existe un centre central de conformité pour un client multigéogé : [Microsoft 365 d’administration de la conformité.](https://compliance.microsoft.com/)

## <a name="ediscovery"></a>eDiscovery

Par défaut, un responsable ou administrateur d’eDiscovery d’un locataire multigéographique ne peut effectuer une découverte électronique que dans l’emplacement central de ce client. L’administrateur général Office 365 doit affecter les autorisations de gestionnaire eDiscovery pour autoriser d’autres personnes à mettre en place un processus eDiscovery, et affecter un paramètre "Région" dans le filtre de sécurité de conformité correspondant pour définir la région concernée par le processus comme emplacement satellite. Sinon, aucun processus eDiscovery n’est mis en place à l’emplacement satellite. Pour configurer le filtre de sécurité de la conformité pour une région, voir [Configurer l’eDiscovery d’Office 365 multigéographique](multi-geo-ediscovery-configuration.md).

## <a name="exchange-mailboxes"></a>Boîtes aux lettres Exchange

Les boîtes aux lettres Exchange des utilisateurs sont déplacées automatiquement en cas de modification de leur emplacement par défaut des données. Lors de sa création, une boîte aux lettres est approvisionnée à l’emplacement par défaut des données de l’utilisateur, ou à l’emplacement central si aucune valeur n’a été définie pour l’emplacement par défaut des données.

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Stratégie de protection contre la perte de données (DLP) de protection contre la perte de données (IP)

Vous pouvez définir des stratégies de protection contre la perte de données d’Information Protection pour OneDrive Entreprise, SharePoint et Exchange dans le centre Sécurité et conformité, en étendant les stratégies selon vos besoins au locataire entier ou à des utilisateurs éligibles. Par exemple, si vous souhaitez sélectionner une stratégie pour un utilisateur dans un emplacement satellite, vous pouvez l’appliquer à un compte OneDrive spécifique et entrer l’URL du OneDrive de cet utilisateur. Pour accéder à des instructions générales concernant la création de stratégies de protection contre la perte de données, voir [Vue d’ensemble des stratégies de protection contre la perte de données](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e).

Les stratégies DLP sont synchronisées automatiquement en fonction de leurs conditions d’application à chaque emplacement géographique.

L’interface utilisateur ne permettant pas d’appliquer des stratégies de protection contre la perte de données et de protection des informations à tous les utilisateurs d’un emplacement géographique, vous devez sélectionner les comptes concernés par la stratégie ou appliquer celle-ci globalement à tous les comptes.

## <a name="microsoft-power-apps"></a>Microsoft Power Apps

Power Apps pour l’emplacement satellite utilise le point de fin situé à l’emplacement central du client. Microsoft Power Apps n’est pas un service Multi-Géo. 

## <a name="power-automate"></a>Power Automate

Les flux créés pour l’emplacement satellite utilisent le point de terminaison situé dans l’emplacement géographique par défaut pour le client.  Power Automate n’est pas un service Multi-Géo. 

## <a name="sharepoint-storage-quota"></a>Quota de stockage SharePoint

Par défaut, tous les emplacements géographiques d’un environnement multigéographique partagent le quota de stockage disponible du locataire.  Vous pouvez également gérer le quota de stockage en allouant un quota spécifique à un emplacement géographique particulier. Pour plus d’informations, voir [Quotas de stockage SharePoint dans des environnements multigéographiques](sharepoint-multi-geo-storage-quota.md).

## <a name="sharing"></a>Partage

Les administrateurs peuvent définir et gérer des stratégies de partage pour chacun de leurs emplacements. Les OneDrive et SharePoint sites dans chaque emplacement géographique respectent uniquement les paramètres de partage spécifiques à la région correspondants. (par exemple, vous pouvez autoriser le [partage externe](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) pour votre emplacement central, mais pas pour votre emplacement satellite, et inversement). Notez que les paramètres de partage ne vous permettent pas de configurer des limites de partage entre emplacements géographiques.

## <a name="stream"></a>Stream

Les vidéos téléchargées sur Stream dans une conversation 1:1 sont stockées dans la OneDrive de la personne qui a téléchargé. Les enregistrements de réunion sont stockés dans le OneDrive de chaque participant qui enregistre la réunion.

## <a name="taxonomy"></a>Taxonomie

Nous 2016 2013 2016 et 2016, et les métadonnées gérées par l’entreprise sont gérées par l’entreprise sur plusieurs emplacements géographiques, le master étant hébergé dans l’emplacement central de votre entreprise. [](/sharepoint/managed-metadata) Nous vous recommandons de gérer votre taxonomie globale à partir de l’emplacement central et d’ajouter uniquement des termes spécifiques à la taxonomie de l’emplacement satellite. Les termes de la taxonomie globale sont synchronisés avec les emplacements satellites.

Pour plus de détails et pour obtenir des instructions de développement, voir [Gérer les métadonnées dans un client multigéographique](/sharepoint/dev/solution-guidance/multigeo-managedmetadata).

## <a name="user-profile-application"></a>Application de profil utilisateur

Il existe une [application de profil utilisateur](/sharepoint/manage-user-profiles) dans chaque emplacement géographique. Les informations de profil de chaque utilisateur sont hébergées dans l’emplacement géographique de celui-ci et accessibles à l’administrateur de cet emplacement.

Si vous avez des propriétés de profil personnalisées, nous vous recommandons d’utiliser le même schéma de profil dans toutes les zones géographiques et de remplir vos propriétés de profil personnalisées dans tous les emplacements géographiques ou dans les emplacements requis. Pour savoir comment remplir les données de profil utilisateur par programme, consultez l’[API de mise à jour en bloc de profil utilisateur](/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

Pour plus de détails et pour obtenir des instructions de développement, voir [Utiliser les profils utilisateur dans un client multigéographique](/sharepoint/dev/solution-guidance/multigeo-userprofileexperience).

## <a name="yammer"></a>Protester

Yammer n’est pas une charge de travail Multi-Géo. Yammer threads stockés dans Yammer seront placés dans l’emplacement central du client. Yammer est en cours de déploiement d’une modification de stockage de fichiers qui stockera Yammer fichiers dans SharePoint. Yammer fichiers stockés dans SharePoint seront placés sur le site SharePoint associé au groupe Yammer web. SharePoint sites de groupe sont basés sur la logique PDL décrite dans SharePoint [Sites et groupes.](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md#sharepoint-sites-and-groups)
