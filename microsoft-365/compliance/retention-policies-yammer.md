---
title: Découvrir la rétention pour Yammer
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Découvrir les stratégies de rétention qui s’appliquent à Microsoft Teams.
ms.openlocfilehash: 3e4cfd5c9e5ef8c28ecd069f3474764b966d6c9a
ms.sourcegitcommit: fa26da0be667d4be0121c52b05488dc76c5d626c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "48794999"
---
# <a name="learn-about-retention-for-yammer"></a>Découvrir la rétention pour Yammer

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Les informations contenues dans cet article complètent l’article [Découvrir la rétention](retention.md) car elles contiennent des informations spécifiques à Yammer.

Pour les autres charges de travail, consultez:

- [En savoir plus sur la rétention dans SharePoint et OneDrive](retention-policies-sharepoint.md)
- [En savoir plus sur la rétention dans Microsoft Teams](retention-policies-teams.md)
- [Découvrir la rétention pour Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Éléments composant la rétention et la suppression

Les éléments Yammer suivants peuvent être conservés et supprimés à l’aide des stratégies de rétention Yammer: Messages de communauté et messages privés.

Les réactions des autres personnes sous la forme d’émoticônes ne sont pas incluses dans ces messages.

## <a name="how-retention-works-with-yammer"></a>Fonctionnement de la rétention pour Yammer

Vous pouvez utiliser une stratégie de rétention pour conserver et supprimer des messages de communauté et des messages privés dans Yammer. Les messages privés sont stockées dans un dossier masqué de la boîte aux lettres de chaque utilisateur participant à la conversation. Les messages communautaires sont stockés dans un dossier masqué similaire dans la boîte aux lettres de groupe de la communauté.

Les messages Yammer ne sont pas affectés par les stratégies de rétention configurées pour les boîtes aux lettres des utilisateurs ou des groupes. Même si les messages Yammer sont stockés dans Exchange, ces données Yammer sont incluses uniquement par une stratégie de rétention configurée pour les **messages de la communauté Yammer** et les emplacements des **messages privés Yammer** .

> [!NOTE]
> Si un utilisateur est inclus dans une stratégie de rétention active qui conserve les données Yammer et que vous supprimez une boîte aux lettres d’un utilisateur inclus dans cette stratégie, la boîte aux lettres est convertie en [boîte aux lettres inactive](inactive-mailboxes-in-office-365.md) pour conserver les données Yammer. Si vous n’avez pas besoin de conserver ces données Yammer pour l’utilisateur, excluez son compte de la stratégie de rétention avant de supprimer sa boîte aux lettres.

Une fois qu'une politique de rétention est configurée pour les messages Yammer, une tâche de temporisation du service Exchange évalue périodiquement les éléments du dossier caché où sont stockés ces messages Yammer. Le travail de chronométrage prend jusqu'à sept jours. Lorsque ces éléments ont expiré leur période de rétention, ils sont déplacés vers le dossier SubstrateHolds - un autre dossier caché qui se trouve dans la boîte aux lettres de chaque utilisateur ou groupe pour stocker les éléments « à suppression douce » avant qu'ils ne soient définitivement supprimés.

Une fois qu'une politique de rétention est configurée pour les messages Yammer, les chemins que prend le contenu dépendent du fait que la politique de rétention doit conserver puis supprimer, conserver seulement ou supprimer seulement.

Lorsque la politique de rétention consiste à conserver puis à supprimer :

![Diagramme de flux de rétention des messages Yammer](../media/yammerretentionlifecycle.png)

Pour les deux voies du diagramme :

1. **Si un message Yammer est modifié ou supprimé** par l'utilisateur pendant la période de conservation, le message original est copié (s'il est modifié) ou déplacé (s'il est supprimé) dans le dossier SubstrateHolds. Le message y est stocké jusqu'à l'expiration de la période de conservation, puis le message est supprimé définitivement.

2. **Si un message Yammer n'est pas supprimé** et pour les messages courants après édition, le message est déplacé dans le dossier SubstrateHolds après l'expiration de la période de conservation. Cette action prend jusqu'à sept jours à compter de la date d'expiration. Lorsque le message se trouve dans le dossier SubstrateHolds, il est alors définitivement supprimé. 

> [!NOTE]
> Les messages dans le dossier SubstrateHolds sont recherchés par les outils d'eDiscovery. Tant que les messages ne sont pas définitivement supprimés (dans le dossier SubstrateHolds), ils peuvent être recherchés via les outils eDiscovery.

Lorsque la stratégie de rétention consiste à conserver uniquement ou à supprimer uniquement, les chemins d'accès au contenu sont des variantes de rétention et de suppression.

### <a name="content-paths-for-retain-only-retention-policy"></a>Chemins d’accès au contenu pour la stratégie de rétention de conservation uniquement

1. **Si un message Yammer est modifié ou supprimé**  : Une copie du message original est créée dans le dossier SubstrateHolds et y est conservée jusqu'à l'expiration de la période de conservation. Ensuite, le message est définitivement supprimé du dossier SubstrateHolds.

2. **Si le message Yammer n'est pas modifié ou supprimé** et pour les messages courants après édition pendant la période de rétention : Rien ne se passe avant et après la période de rétention ; le message reste dans son emplacement d'origine.

### <a name="content-paths-for-delete-only-retention-policy"></a>Chemins d’accès du contenu pour la stratégie de rétention de suppression uniquement

1. **Si le message Yammer n’est pas supprimé** pendant la période de rétention : à la fin de la période de rétention, il est déplacé vers le dossier SubstrateHolds. Cette action prend jusqu'à sept jours à compter de la date d'expiration. Ensuite, le message est définitivement supprimé du dossier SubstrateHolds.

2. **Si le message Yammer est supprimé par l'utilisateur** pendant cette période, l'élément est déplacé vers le dossier SubstrateHolds où il est immédiatement supprimé définitivement.


## <a name="messages-and-external-users"></a>Messages et utilisateurs externes

Par défaut, une stratégie de rétention pour les messages privés Yammer s’applique à tous les utilisateurs de votre organisation, mais pas aux utilisateurs externes. Vous pouvez appliquer une stratégie de rétention à des utilisateurs externes si vous utilisez le **Choisir Utilisateur** puis spécifiez leur compte. 

Pour l’instant, les utilisateurs invités B2B Azure ne sont pas pris en charge.

## <a name="when-a-user-leaves-the-organization"></a>Lorsqu’un utilisateur quitte l’organisation 

Si un utilisateur quitte votre organisation et que son compte Microsoft 365 est supprimé, leurs messages privés Yammer soumis à une rétention sont stockés dans une boîte aux lettres inactive. Les messages de conversation restent soumis à une stratégie de rétention qui a été placée sur l’utilisateur avant que sa boîte aux lettres ne soit inactive et les contenus sont disponibles pour une recherche eDiscovery. Pour plus d’informations, consultez [Boîtes aux lettres inactives dans Exchange Online](inactive-mailboxes-in-office-365.md). 

Si l’utilisateur a stocké des fichiers dans Yammer, consultez la [section équivalente](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) pour SharePoint et OneDrive.

## <a name="limitations"></a>Limites

Les stratégies de rétention de Yammer sont actuellement en préversion et nous travaillons continuellement sur l’optimisation des fonctionnalités de rétention. En attendant, voici quelques limitations à prendre en compte lors de l’utilisation de la rétention pour les messages communautaires et les messages privés Yammer:

- Lorsque vous sélectionnez **Choisir les utilisateurs** pour l’emplacement des **messages privés Yammer** , les invités et les utilisateurs qui n’utilisent pas de boîte aux lettres peuvent s’afficher. Les stratégies de rétention ne sont pas conçues pour ces utilisateurs. Ne les sélectionnez pas.

## <a name="configuration-guidance"></a>Instructions de configuration

Si vous n’avez jamais configurer la rétention dans Microsoft 365, voir [Prise en main des stratégies et des étiquettes de rétention](get-started-with-retention.md).

Si vous êtes prêt à configurer une stratégie de rétention pour Yammer, voir [Créer et configurer des stratégies de rétention](create-retention-policies.md).
