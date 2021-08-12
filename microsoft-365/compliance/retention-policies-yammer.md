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
description: Découvrir les stratégies de rétention qui s’appliquent à Microsoft Teams.
ms.openlocfilehash: deacfafbc16c2b04b3dad8a4e9c49ffe07fdf165792c7360a31419a821c52c22
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53835597"
---
# <a name="learn-about-retention-for-yammer"></a>Découvrir la rétention pour Yammer

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Cette fonctionnalité est en phase aperçu et est sujette à modifications.

Les informations contenues dans cet article complètent l’article [Découvrir la rétention](retention.md) car elles contiennent des informations spécifiques à Yammer.

Pour les autres charges de travail, consultez:

- [En savoir plus sur la rétention dans SharePoint et OneDrive](retention-policies-sharepoint.md)
- [En savoir plus sur la rétention dans Microsoft Teams](retention-policies-teams.md)
- [Découvrir la rétention pour Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Éléments composant la rétention et la suppression

Les éléments Yammer suivants peuvent être conservés et supprimés à l’aide des stratégies de rétention Yammer: Messages de la communauté et messages des utilisateurs.

Les réactions des autres personnes sous la forme d’émoticônes ne sont pas incluses dans ces messages.

## <a name="how-retention-works-with-yammer"></a>Fonctionnement de la rétention pour Yammer

Utilisez cette section pour comprendre comment vos exigences de conformité sont respectées par le stockage et les processus principaux, et doivent être vérifiées par les outils eDiscovery plutôt que par les messages actuellement visibles dans l’application Yammer.

Vous pouvez utiliser une stratégie de rétention pour conserver les données des messages de la communauté et messages des utilisateurs de messages dans Yammer, puis effacer ces messages. En arrière-plan, les boîtes aux lettres Exchange sont utilisées pour stocker les données copiées depuis ces messages. Les données des utilisateurs de messages Yammer sont stockées dans un dossier masqué dans la boîte aux lettres de chaque utilisateur inclus dans le message de l’utilisateur, et un dossier masqué similaire dans une boîte aux lettres de groupe utilisée pour les messages de la communauté. 

Les copies des messages de la communauté peuvent également être stockées dans le dossier masqué des boîtes aux lettres des utilisateurs lorsqu’ils mentionnent @ des utilisateurs ou informent l’utilisateur d’une réponse. Bien que ces messages proviennent d’un message de la communauté, une stratégie de rétention pour les messages d’utilisateur Yammer, inclut souvent des copies des messages de la communauté.

Ces dossiers masqués ne sont pas conçus pour être directement accessibles aux utilisateurs ou aux administrateurs. Au lieu de cela, ils stockent les données que les administrateurs de conformité peuvent rechercher à l’aide des outils eDiscovery.

> [!IMPORTANT]
> Étant donné que les copies des messages de la communauté peuvent également être stockées dans des boîtes aux lettres d’utilisateur, une stratégie de rétention avec une action de suppression pour les messages d’utilisateur Yammer peut entraîner le fait que le message de la communauté d’origine n’est plus visible pour les utilisateurs dans l’application Yammer.
> 
> Toutefois, une copie du message d’origine est toujours disponible dans le dossier masqué de la boîte aux lettres du groupe de communauté et accessible avec les recherches eDiscovery à des fins de conformité.

Les messages Yammer ne sont pas affectés par les stratégies de rétention configurées pour les boîtes aux lettres Exchange. Même si les messages Yammer sont stockés dans Exchange, ces données Yammer sont incluses uniquement par une stratégie de rétention configurée pour les **messages de la communauté Yammer** et les emplacements des **messages utilisateur Yammer**.

> [!NOTE]
> Si un utilisateur est inclus dans une stratégie de rétention active qui conserve les données Yammer et que vous supprimez une boîte aux lettres d’un utilisateur inclus dans cette stratégie, la boîte aux lettres est convertie en [boîte aux lettres inactive](inactive-mailboxes-in-office-365.md) pour conserver les données Yammer. Si vous n’avez pas besoin de conserver ces données Yammer pour l’utilisateur, excluez son compte de la stratégie de rétention avant de supprimer sa boîte aux lettres.

Une fois qu'une politique de rétention est configurée pour les messages Yammer, une tâche de temporisation du service Exchange évalue périodiquement les éléments du dossier caché où sont stockés ces messages Yammer. Le travail de chronométrage prend jusqu'à sept jours. Lorsque ces éléments ont expiré leur période de rétention, ils sont déplacés vers le dossier SubstrateHolds - un autre dossier caché qui se trouve dans la boîte aux lettres de chaque utilisateur ou groupe pour stocker les éléments « à suppression douce » avant qu'ils ne soient définitivement supprimés.

> [!NOTE]
> En raison du [premier principe de rétention](retention.md#the-principles-of-retention-or-what-takes-precedence), la suppression définitive est toujours suspendue si le même élément doit être retenu à cause d’une autre stratégie de rétention ou qu’il est bloqué pour des raisons juridiques ou d’enquête.

Une fois qu'une politique de rétention est configurée pour les messages Yammer, les chemins que prend le contenu dépendent du fait que la politique de rétention doit conserver puis supprimer, conserver seulement ou supprimer seulement.

Lorsque la politique de rétention consiste à conserver puis à supprimer :

![Diagramme de flux de rétention des messages Yammer](../media/yammerretentionlifecycle.png)

Pour les deux voies du diagramme :

1. **Si un message Yammer est édité ou supprimé** par l'utilisateur pendant la période de conservation, le message original est immédiatement copié (s'il est édité) ou déplacé (s'il est supprimé) dans le dossier SubstrateHolds. Le message y est stocké jusqu'à l'expiration de la période de conservation, puis le message est supprimé définitivement.

2. **Si un message Yammer n'est pas supprimé** et pour les messages courants après édition, le message est déplacé dans le dossier SubstrateHolds après l'expiration de la période de conservation. Cette action prend jusqu'à sept jours à compter de la date d'expiration. Lorsque le message se trouve dans le dossier SubstrateHolds, il est alors définitivement supprimé. 

> [!NOTE]
> Les messages dans le dossier SubstrateHolds sont recherchés par les outils d'eDiscovery. Tant que les messages ne sont pas définitivement supprimés (dans le dossier SubstrateHolds), ils restent recherchés par les outils d'eDiscovery.

Lorsque la stratégie de rétention consiste à conserver uniquement ou à supprimer uniquement, les chemins d'accès au contenu sont des variantes de rétention et de suppression.

### <a name="content-paths-for-retain-only-retention-policy"></a>Chemins d’accès au contenu pour la stratégie de rétention de conservation uniquement

1. **Si un message Yammer est édité ou supprimé**:Une copie du message original est immédiatement créée dans le dossier SubstrateHolds et y est conservée jusqu'à l'expiration de la période de conservation. Ensuite, le message est définitivement supprimé du dossier SubstrateHolds.

2. **Si le message Yammer n'est pas modifié ou supprimé** et pour les messages courants après édition pendant la période de rétention : Rien ne se passe avant et après la période de rétention ; le message reste dans son emplacement d'origine.

### <a name="content-paths-for-delete-only-retention-policy"></a>Chemins d’accès du contenu pour la stratégie de rétention de suppression uniquement

1. **Si le message Yammer n’est pas supprimé** pendant la période de rétention : à la fin de la période de rétention, il est déplacé vers le dossier SubstrateHolds. Cette action prend jusqu'à sept jours à compter de la date d'expiration. Ensuite, le message est définitivement supprimé du dossier SubstrateHolds.

2. **Si le message Yammer est supprimé par l'utilisateur** pendant cette période, l'élément est immédiatement déplacé vers le dossier SubstrateHolds où il est immédiatement supprimé définitivement.


## <a name="messages-and-external-users"></a>Messages et utilisateurs externes

Par défaut, une stratégie de rétention pour les messages utilisateur Yammer s’applique à tous les utilisateurs de votre organisation, mais pas aux utilisateurs externes. Vous pouvez appliquer une stratégie de rétention à des utilisateurs externes si vous utilisez **Modifier** pour les utilisateurs inclus puis spécifiez leur compte.

Pour l’instant, les utilisateurs invités B2B Azure ne sont pas pris en charge.

## <a name="when-a-user-leaves-the-organization"></a>Lorsqu’un utilisateur quitte l’organisation 

Si un utilisateur quitte votre organisation et que son compte Microsoft 365 est supprimé, leurs messages utilisateur Yammer soumis à une rétention sont stockés dans une boîte aux lettres inactive. Les messages de conversation restent soumis à une stratégie de rétention qui a été placée sur l’utilisateur avant que sa boîte aux lettres ne soit inactive et les contenus sont disponibles pour une recherche eDiscovery. Pour plus d’informations, consultez [Boîtes aux lettres inactives dans Exchange Online](inactive-mailboxes-in-office-365.md). 

Si l’utilisateur a stocké des fichiers dans Yammer, consultez la [section équivalente](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) pour SharePoint et OneDrive.

## <a name="limitations"></a>Limites

Les stratégies de rétention de Yammer sont actuellement en préversion et nous travaillons continuellement sur l’optimisation des fonctionnalités de rétention. En attendant, tenez compte de la limitation suivante lorsque vous utilisez la rétention pour les messages de la communauté Yammer et les messages des utilisateurs:

- Lorsque vous sélectionnez **Modifier** pour l’emplacement des **messages des utilisateurs Yammer**, vous devriez voir les invités et les non-utilisateurs de boîte aux lettres. Les stratégies de rétention ne sont pas conçues pour ces utilisateurs. Ne les sélectionnez pas.

## <a name="configuration-guidance"></a>Instructions de configuration

Si vous n’avez jamais configurer la rétention dans Microsoft 365, voir [Prise en main des stratégies et des étiquettes de rétention](get-started-with-retention.md).

Si vous êtes prêt à configurer une stratégie de rétention pour Yammer, voir [Créer et configurer des stratégies de rétention](create-retention-policies.md).