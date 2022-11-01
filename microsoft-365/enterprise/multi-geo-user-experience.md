---
title: Expérience utilisateur dans un environnement multigéographique
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection:
- SPO_Content
- Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: Découvrez l’expérience utilisateur de SharePoint, de OneDrive et d’Exchange dans un environnement multigéographique pour Microsoft 365.
ms.openlocfilehash: fa4c108a8f7d97820d9f66bb00f23f19e138588b
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68804967"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Expérience utilisateur dans un environnement multigéographique

Voici ce que vos utilisateurs verront dans une configuration multigéographique OneDrive Entreprise :

## <a name="exchange-online-mailbox"></a>Boîte aux lettres Exchange Online

La boîte aux lettres Exchange Online d’un utilisateur est approvisionnée à l’emplacement de données de son choix et est automatiquement déplacée si son PDL change. Les utilisateurs peuvent utiliser Outlook et Outlook sur le web normalement sans modification de l’expérience utilisateur dans un environnement multigéographique.

## <a name="hub-sites"></a>Sites concentrateurs

Les sites SharePoint Online Hub améliorent la découverte et l’engagement avec le contenu des employés, tout en créant une représentation complète et cohérente des projets, des services ou des régions. Dans un environnement multigéographique, les sites provenant d’emplacements satellites peuvent facilement être associés à un site hub, quel que soit l’emplacement _géographique_ du site hub. Les utilisateurs peuvent rechercher et obtenir des résultats sur le hub via une simple expérience de recherche, indépendamment de l’emplacement géographique des sites.

## <a name="microsoft-365-app-launcher"></a>Lanceur d’applications Microsoft 365

Le lanceur d’applications prend en compte la configuration multigéographique et dirige chaque vignette vers l’emplacement géographique approprié de la charge de travail. Les vignettes SharePoint Online et OneDrive Entreprise pointent l’utilisateur vers l’emplacement correspondant à l’emplacement géographique approvisionné de l’utilisateur. Cela signifie que si l’utilisateur dispose d’un OneDrive Entreprise dans l’emplacement central, sa vignette SharePoint Online le pointe vers l’accueil du fournisseur de services à l’emplacement central, mais que son site de groupe est approvisionné à l’emplacement correspondant à son PDL. 

## <a name="office-applications"></a>Applications Office

Les applications Office telles que Microsoft Word, Excel et PowerPoint détectent automatiquement le bon OneDrive Entreprise emplacement géographique pour chaque utilisateur lorsqu’il se connecte. Les utilisateurs n’ont pas besoin d’entrer l’URL spécifique géographique de leur OneDrive Entreprise ou de leurs sites SharePoint Online.

## <a name="onedrive-for-business-sync-app"></a>application de synchronisation OneDrive Entreprise

L’application de synchronisation OneDrive Entreprise (version 17.3.6943.0625 et ultérieures) détecte automatiquement l’emplacement _Géographique_ OneDrive approprié pour l’utilisateur. La prise en charge des applications de synchronisation inclut la possibilité de synchroniser des sites basés sur des groupes, quel que soit leur emplacement _Géographique_ . Le client de synchronisation Groove n’est pas pris en charge pour multigéographique. 

## <a name="onedrive-for-business-location"></a>Emplacement OneDrive Entreprise

Les OneDrive Entreprise des utilisateurs seront approvisionnés à l’emplacement de données de leur choix. Si un utilisateur accède à une URL OneDrive Entreprise qui contient un emplacement _Geography_ incorrect (par exemple, un signet d’un emplacement géographique précédent), il est automatiquement redirigé vers le OneDrive Entreprise à l’emplacement géographique approprié.

## <a name="onedrive-for-business-ios-and-android"></a>OneDrive Entreprise iOS et Android 

Les applications mobiles OneDrive iOS et Android affichent vos OneDrive Entreprise fichiers et fichiers partagés avec vous, quel que soit leur emplacement _géographique_. La recherche à partir de l’OneDrive Entreprise applications mobiles affiche les résultats pertinents de tous les emplacements _Geography_. Téléchargez la dernière version de ces applications.

Pour plus d’informations, consultez Utiliser [OneDrive sur iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) et [Utiliser OneDrive pour Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) pour plus d’informations.

## <a name="onedrive-for-business-mobile-client"></a>OneDrive Entreprise Mobile Client 

Le client mobile OneDrive Entreprise prend en charge la multigéographique et affiche le contenu et les résultats pertinents de tous les emplacements _geography_.

## <a name="search"></a>Rechercher

Chaque emplacement _Geography_ a son propre index de recherche et son propre centre de recherche. Lorsqu’un utilisateur effectue une recherche, la requête est envoyée à tous les emplacements _Geography_ , et les résultats retournés sont fusionnés, puis classés afin que l’utilisateur obtienne des résultats unifiés. Les utilisateurs obtiennent les résultats de tous les emplacements _Geography_ , quel que soit leur propre emplacement _Geography_ . Pour plus d’informations[, consultez Configurer la recherche de OneDrive Entreprise multigéographique](configure-search-for-multi-geo.md).

Les clients de recherche suivants sont pris en charge :

-   OneDrive Entreprise

-   Office Delve

-   Accueil SharePoint Online

-   Centre de recherche

-   Applications de recherche personnalisée qui utilisent l’API de recherche SharePoint

## <a name="sharepoint-online-home"></a>Accueil SharePoint Online 

Dans SharePoint Online multigéographique, votre page d’accueil SharePoint Online est hébergée à l’emplacement où réside l’utilisateur, tel que déterminé par son emplacement OneDrive Entreprise. Par exemple : si l’utilisateur a son OneDrive Entreprise hébergé dans un emplacement satellite européen, sa page d’accueil SharePoint Online sera rendue à partir de l’Europe. La page d’accueil SharePoint Online inclut tout le contenu pertinent pour l’utilisateur, quel que soit son emplacement _géographique_ . 

**Sites suivis, Actualités de sites, Sites récents, Sites fréquents et Sites suggérés**

Tous ces composants s’affichent pour l’utilisateur, quel que soit l’emplacement _Geography_ où le contenu est hébergé, tant que l’utilisateur dispose des autorisations pour ce contenu. 

**Liens proposés**

Les administrateurs peuvent configurer les liens proposés dans la page d’accueil SharePoint Online en fonction de chaque emplacement _géographique_ . Ainsi, dans la page d’accueil SharePoint, l’administrateur peut suggérer, pour chaque région, des liens appropriés pour les utilisateurs dans cette région. 

## <a name="sharepoint-mobile-client"></a>Client mobile SharePoint

Le client mobile SharePoint prend en compte la configuration multigéographique et affiche du contenu et des résultats pertinents de tous les emplacements géographiques.

## <a name="sharing"></a>Partage

L’expérience du sélecteur de Personnes affiche tous les utilisateurs, quel que soit leur emplacement _géographique_. Cela permet à un utilisateur de partager avec un autre utilisateur dans sa même zone géographique ou dans _n’importe_ quel autre emplacement _géographique_ de votre locataire. Le contenu provenant de différents emplacements _Geography_ s’affiche dans l’affichage **Partagé avec moi** dans le OneDrive Entreprise, Word, Excel, PowerPoint et Office.com de l’utilisateur et est accessible avec une expérience de Sign-On unique, quel que soit l’emplacement _géographique_ dans lequel il est hébergé.

## <a name="microsoft-teams-experience"></a>Expérience Microsoft Teams

Microsoft Teams est un service multigéographique. OneDrive Entreprise fichiers et les fichiers récemment affichés sont affichés quel que soit l’emplacement _géographique_ de l’utilisateur. Les mentions @ fonctionnent avec les utilisateurs de tous les emplacements _Geography_ .

## <a name="user-profiles"></a>Profils utilisateur

Les informations de profil utilisateur sont maîtrisées dans l’emplacement _géographique_ de l’utilisateur. Lorsque vous sélectionnez un utilisateur, vous êtes dirigé vers l’emplacement _Géographique_ approprié pour l’utilisateur, où vous verrez les détails complets de son profil.

Si Office Delve est désactivé, vous verrez l’expérience de profil classique dans SharePoint Online, qui n’est pas compatible multigéographique.


