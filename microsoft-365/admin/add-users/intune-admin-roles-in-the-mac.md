---
title: À propos des rôles d'administration Intune dans le Centre d’administration Microsoft 365
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
description: Le Centre d’administration Microsoft 365 vous permet de gérer certains rôles Microsoft Intune, qui sont mappés aux fonctions métier et donnent des autorisations pour effectuer des tâches spécifiques.
ms.openlocfilehash: 61c73ea49b132dee12839112bdc08624a750989f
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65636259"
---
# <a name="intune-admin-roles-in-the-microsoft-365-admin-center"></a>Rôles d'administration Intune dans le Centre d’administration Microsoft 365

Votre abonnement Microsoft 365 ou Office 365 inclut un ensemble de rôles d'administrateur que vous pouvez attribuer à des utilisateurs de votre organisation en utilisant le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>. Chaque rôle d'administrateur correspond à des fonctions d'entreprise courantes et donne aux personnes de votre organisation des autorisations pour effectuer des tâches spécifiques dans les Centres d'administration.

Le Centre d’administration Microsoft 365 vous permet de gérer certains rôles Microsoft Intune. Toutefois, ces rôles sont un sous-ensemble des rôles disponibles dans le Centre d’administration Intune. Vous recherchez des descriptions détaillées des rôles pour Microsoft Intune ? Consultez la page [Contrôle d’accès basé sur un rôle dans Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Si vous souhaitez en savoir plus sur l’attribution de rôles dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">Centre d’administration Microsoft 365</a>, consultez la page [Attribuer des rôles d’administrateur](assign-admin-roles.md).

Dans le Centre d’administration Microsoft 365, vous pouvez accéder à **Rôles**, puis sélectionner un rôle pour ouvrir le volet Détails. Sélectionnez l’onglet **Autorisations** pour afficher la liste détaillée des autorisations attribuées à ce rôle d'administrateur. Sélectionnez l’onglet **Attribué** ou **Administrateurs affectés** pour ajouter des utilisateurs aux rôles.

## <a name="microsoft-intune-roles-available-in-the-microsoft-365-admin-center"></a>Rôles Microsoft Intune disponibles dans le Centre d'administration Microsoft 365

|Rôle d’administrateur     |À qui doit être affecté ce rôle ?  |
|---------|---------|
|Gestionnaire d’applications     |   Attribuez le rôle de gestionnaire d'applications aux utilisateurs qui gèrent le cycle de vie des applications pour les applications mobiles, qui configurent les applications gérées par des stratégies et qui affichent les informations sur les appareils et les profils de configuration.  |
|Opérateur du support technique     |   Attribuez le rôle d’opérateur du support technique aux utilisateurs qui attribuent des applications et des stratégies aux utilisateurs et aux appareils. |
|Administrateur de rôle Intune    |   Attribuez le rôle d'administrateur de rôle Intune aux utilisateurs qui peuvent attribuer des autorisations Intune à d'autres administrateurs et gérer des rôles Intune personnalisés et intégrés.   |
|Gestionnaire des stratégies et des profils     |   Attribuez le rôle de gestionnaire des stratégies et des profils aux utilisateurs qui gèrent la stratégie de conformité, les profils de configuration et l'inscription Apple.   |
|Opérateur en lecture seule     |   Attribuez le rôle d’opérateur en lecture seule aux utilisateurs qui peuvent uniquement consulter les utilisateurs, les appareils, les détails d’inscription et les configurations.   |
|Administrateur scolaire     |   Attribuez le rôle d'administrateur scolaire aux utilisateurs pour un accès complet à la gestion des appareils, des applications et des configurations Windows 10 et iOS dans Intune pour l'éducation.   |

## <a name="delegated-administration-for-microsoft-partners"></a>Administration déléguée pour les partenaires Microsoft

Si vous travaillez avec un partenaire Microsoft, vous pouvez lui attribuer des rôles d'administrateur. Ils peuvent à leur tour attribuer des rôles d'administrateur aux utilisateurs de votre entreprise ou de la leur. Vous pouvez leur demander de le faire, par exemple, s'ils mettent en place et gèrent votre organisation en ligne pour vous.
  
Un partenaire peut attribuer ces rôles : 
  
- Administration complète, qui dispose de privilèges équivalents à un administrateur général, à l’exception de la gestion de l’authentification multifacteur via l’Espace partenaires.

- Administration limitée, dont les privilèges sont équivalents à ceux d’un administrateur du support technique.

Pour que le partenaire puisse attribuer ces rôles aux utilisateurs, vous devez l'ajouter en tant qu'administrateur délégué à votre compte. Ce processus est initié par un partenaire agréé. Le partenaire vous envoie un e-mail pour vous demander l'autorisation d'agir en tant qu'administrateur délégué. Pour consulter des instructions, voir [Autoriser ou supprimer des relations de partenariat](../misc/add-partner.md).
  
## <a name="related-content"></a>Contenu associé

[À propos des rôles d’administrateur Microsoft 365](about-admin-roles.md) (article)\
[Attribuer des rôles administrateur](assign-admin-roles.md) (article)\
[Rapports d’activité dans le Centre d’administration Microsoft 365](../activity-reports/activity-reports.md) (article)
