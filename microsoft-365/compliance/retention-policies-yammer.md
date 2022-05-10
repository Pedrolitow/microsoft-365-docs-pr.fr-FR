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
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Découvrir les stratégies de rétention qui s’appliquent à Microsoft Teams.
ms.openlocfilehash: e90d83cb4b71600f4dbf8b16790454f523ce6c13
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286469"
---
# <a name="learn-about-retention-for-yammer"></a>Découvrir la rétention pour Yammer

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Les informations contenues dans cet article complètent l’article [Découvrir la rétention](retention.md) car elles contiennent des informations spécifiques à Yammer.

Pour les autres charges de travail, consultez:

- [En savoir plus sur la rétention dans SharePoint et OneDrive](retention-policies-sharepoint.md)
- [En savoir plus sur la rétention dans Microsoft Teams](retention-policies-teams.md)
- [Découvrir la rétention pour Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Éléments composant la rétention et la suppression

Les messages utilisateur et les messages de la communauté Yammer peuvent être supprimés à l’aide de stratégies de rétention pour Yammer. En plus du texte de ces messages, les éléments suivants peuvent être conservés pour des raisons de conformité : liens hypertexte et liens vers d’autres messages Yammer.

> [!NOTE]
> Comme expliqué dans la section suivante, les messages utilisateur incluent des messages privés pour un utilisateur individuel et tous les messages de la communauté associés à cet utilisateur.

Les messages de l'utilisateur comprennent tous les noms des personnes présentes dans la conversation, et les messages de la communauté comprennent le nom de la communauté et le titre du message (s'il est fourni).

Les réactions des autres sous forme d'émoticônes ne sont pas conservées lorsque vous utilisez les politiques de conservation pour Yammer.

Les fichiers que vous utilisez avec Yammer ne sont pas inclus dans les règles de conservation pour Yammer. Ces éléments ont leurs propres règles de conservation.

## <a name="how-retention-works-with-yammer"></a>Fonctionnement de la rétention pour Yammer

Utilisez cette section pour comprendre comment vos exigences de conformité sont respectées par le stockage et les processus principaux, et doivent être vérifiées par les outils eDiscovery plutôt que par les messages actuellement visibles dans l’application Yammer.

Vous pouvez utiliser une stratégie de rétention pour conserver les données des messages de la communauté et messages des utilisateurs de messages dans Yammer, puis effacer ces messages. En arrière-plan, les boîtes aux lettres Exchange sont utilisées pour stocker les données copiées depuis ces messages. Les données des utilisateurs de messages Yammer sont stockées dans un dossier masqué dans la boîte aux lettres de chaque utilisateur inclus dans le message de l’utilisateur, et un dossier masqué similaire dans une boîte aux lettres de groupe utilisée pour les messages de la communauté. 

Les copies des messages de la communauté peuvent également être stockées dans le dossier masqué des boîtes aux lettres des utilisateurs lorsqu’ils mentionnent @ des utilisateurs ou informent l’utilisateur d’une réponse. Bien que ces messages proviennent d’un message de la communauté, une stratégie de rétention pour les messages d’utilisateur Yammer, inclut souvent des copies des messages de la communauté. Par conséquent, les messages utilisateur ne sont pas limités aux messages privés.

Ces dossiers masqués ne sont pas conçus pour être directement accessibles aux utilisateurs ou aux administrateurs. Au lieu de cela, ils stockent les données que les administrateurs de conformité peuvent rechercher à l’aide des outils eDiscovery.

Même s’ils sont stockés dans Exchange, les messages Yammer sont inclus uniquement dans une stratégie de rétention configurée pour les emplacements de **messages de la communauté Yammer** ou **les messages utilisateur Yammer**.

> [!NOTE]
> Si un utilisateur est inclus dans une stratégie de rétention active qui conserve les données Yammer et que vous supprimez une boîte aux lettres d’un utilisateur inclus dans cette stratégie, la boîte aux lettres est convertie en [boîte aux lettres inactive](inactive-mailboxes-in-office-365.md) pour conserver les données Yammer. Si vous n’avez pas besoin de conserver ces données Yammer pour l’utilisateur, excluez son compte de la stratégie de rétention avant de supprimer sa boîte aux lettres.

Une fois qu'une politique de rétention est configurée pour les messages Yammer, une tâche de temporisation du service Exchange évalue périodiquement les éléments du dossier caché où sont stockés ces messages Yammer. Le travail de chronométrage prend jusqu'à sept jours. Lorsque ces éléments ont expiré leur période de rétention, ils sont déplacés vers le dossier SubstrateHolds - un autre dossier caché qui se trouve dans la boîte aux lettres de chaque utilisateur ou groupe pour stocker les éléments « à suppression douce » avant qu'ils ne soient définitivement supprimés.

> [!IMPORTANT]
> En raison du [premier principe de rétention](retention.md#the-principles-of-retention-or-what-takes-precedence) et étant donné que les messages Yammer sont stockés dans des boîtes aux lettres Exchange Online, la suppression définitive du dossier SubstrateHolds est toujours suspendue si la boîte aux lettres est affectée par une autre stratégie de rétention (y compris les stratégies appliquées à l’emplacement Exchange), la conservation pour litige, la conservation différée ou si une conservation eDiscovery est appliquée à la boîte aux lettres pour des raisons juridiques ou d’investigation.
>
> Bien que la boîte aux lettres soit incluse dans une conservation applicable, les messages Yammer qui ont été supprimés ne seront plus visibles dans Yammer, mais continueront d’être détectables avec eDiscovery.

Une fois qu'une politique de rétention est configurée pour les messages Yammer, les chemins que prend le contenu dépendent du fait que la politique de rétention doit conserver puis supprimer, conserver seulement ou supprimer seulement.

Lorsque la politique de rétention consiste à conserver puis à supprimer :

![Diagramme de flux de rétention des messages Yammer.](../media/yammerretentionlifecycle.png)

Pour les deux voies du diagramme :

1. **Si un message Yammer est édité ou supprimé** par l'utilisateur pendant la période de conservation, le message original est immédiatement copié (s'il est édité) ou déplacé (s'il est supprimé) dans le dossier SubstrateHolds. Le message y est stocké jusqu'à l'expiration de la période de conservation, puis le message est supprimé définitivement.

2. **Si un message Yammer n'est pas supprimé** et pour les messages courants après édition, le message est déplacé dans le dossier SubstrateHolds après l'expiration de la période de conservation. Cette action prend jusqu'à sept jours à compter de la date d'expiration. Lorsque le message se trouve dans le dossier SubstrateHolds, il est alors définitivement supprimé. 

> [!NOTE]
> Les messages dans le dossier SubstrateHolds sont recherchés par les outils d'eDiscovery. Tant que les messages ne sont pas définitivement supprimés (dans le dossier SubstrateHolds), ils restent recherchés par les outils d'eDiscovery.

Lorsque la stratégie de rétention consiste à conserver uniquement ou à supprimer uniquement, les chemins d'accès au contenu sont des variantes de rétention et de suppression.

### <a name="content-paths-for-retain-only-retention-policy"></a>Chemins d’accès au contenu pour la stratégie de rétention de conservation uniquement

1. **Si un message Yammer est modifié ou supprimé** : une copie du message d'origine est immédiatement créée dans le dossier SubstrateHolds et y est conservée jusqu'à l'expiration de la période de rétention. Ensuite, le message est immédiatement supprimé définitivement du dossier SubstrateHolds.

2. **Si le message Yammer n'est pas modifié ou supprimé** et pour les messages courants après édition pendant la période de rétention : Rien ne se passe avant et après la période de rétention ; le message reste dans son emplacement d'origine.

### <a name="content-paths-for-delete-only-retention-policy"></a>Chemins d’accès du contenu pour la stratégie de rétention de suppression uniquement

1. **Si le message Yammer n’est pas supprimé** pendant la période de rétention : à la fin de la période de rétention, il est déplacé vers le dossier SubstrateHolds. Cette action prend jusqu'à sept jours à compter de la date d'expiration. Ensuite, le message est définitivement supprimé du dossier SubstrateHolds.

2. **Si le message Yammer est supprimé par l'utilisateur** pendant cette période, l'élément est immédiatement déplacé vers le dossier SubstrateHolds où il est immédiatement supprimé définitivement.

#### <a name="example-flows-and-timings-for-retention-policies"></a>Exemples de flux et de minutages pour les stratégies de rétention

Utilisez les exemples suivants pour voir comment les processus et minutages expliqués dans les sections précédentes s’appliquent aux stratégies de rétention qui présentent les configurations suivantes :

- [Exemple 1 : conserver uniquement pendant 7 ans](#example-1-retain-only-for-7-years)
- [Exemple 2 : conserver pendant 30 jours, puis supprimer](#example-2-retain-for-30-days-and-then-delete)
- [Exemple 3 : supprimer uniquement après 1 jour](#example-3-delete-only-after-1-day)

Pour tous les exemples qui font référence à une suppression définitive, en raison des [principes de rétention](retention.md#the-principles-of-retention-or-what-takes-precedence), cette action est suspendue si le message est soumis à une autre stratégie de rétention pour conserver l’élément ou s’il est soumis à une conservation eDiscovery.

##### <a name="example-1-retain-only-for-7-years"></a>Exemple 1 : conserver uniquement pendant 7 ans

Au cours du 1er jour, un utilisateur publie un nouveau message Yammer.

Au 5e jour, l’utilisateur modifie ce message.

Au 30e jour, l’utilisateur supprime le message actuel.

Résultats de la rétention :

- Pour le message d’origine :
    - Au 5e jour, le message est copié dans le dossier SubstrateHolds où il peut toujours être recherché à l’aide des outils eDiscovery pour une durée minimale de 7 ans à compter du premier jour (période de rétention).

- Pour le message (modifié) actuel :
    - Au 30e jour, le message est déplacé vers le dossier SubstrateHolds où il peut toujours être recherché à l’aide des outils eDiscovery pour une durée minimale de 7 ans à compter du premier jour (période de rétention).

Si l’utilisateur avait supprimé le message actuel après la période de rétention spécifique, au lieu de la période de rétention, le message serait toujours déplacé vers le dossier SubstrateHolds. Toutefois, maintenant que la période de rétention a expiré, le message sera définitivement supprimé après une durée minimale de 1 jour, puis généralement dans un délai de 1 à 7 jours.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Exemple 2 : conserver pendant 30 jours, puis supprimer

Au cours du 1er jour, un utilisateur publie un nouveau message Yammer.

Au 10e jour, l’utilisateur modifie ce message.

L’utilisateur ne procède pas à d’autres modifications et ne supprime pas le message.

Résultats de la rétention :

- Pour le message d’origine :
    - Au 10e jour, le message est copié dans le dossier SubstrateHolds où il peut toujours être recherché à l’aide des outils eDiscovery.
    - Au terme de la période de rétention (30 jours à compter du premier jour), le message est supprimé définitivement dans un délai de 1 à 7 jours après une durée minimale de 1 jour, puis n’est pas renvoyé avec les recherches eDiscovery.

- Pour le message (modifié) actuel :
    - Au terme de la période de rétention (30 jours à compter du premier jour), le message est déplacé vers le dossier SubstrateHolds, généralement dans un délai de 1 à 7 jours, où il peut toujours être recherché à l’aide des outils eDiscovery.
    - Le message est ensuite définitivement supprimé généralement dans un délai de 1 à 7 jours après une durée minimale de 1 jour, puis n’est pas renvoyé avec les recherches eDiscovery.

##### <a name="example-3-delete-only-after-1-day"></a>Exemple 3 : supprimer uniquement après 1 jour

> [!NOTE]
> En raison de la courte durée d’un jour de ces processus de configuration et de rétention qui fonctionnent sur une période de 1 à 7 jours, cette section présente des exemples de minutages qui se situent dans les plages de temps classiques.

Au cours du 1er jour, un utilisateur publie un nouveau message Yammer.

Exemple de résultat de rétention si l’utilisateur ne modifie ou ne supprime pas le message :

- 5e jour (généralement 1 à 7 jours après le début de la période de rétention au 2e jour) :
    - Le message est alors déplacé vers le dossier SubstrateHolds et y reste pendant au moins 1 jour où il peut toujours être recherché à l’aide des outils eDiscovery.

- 9e jour (généralement 1 à 7 jours après une durée minimale de 1 jour dans le dossier SubstrateHolds) :
    - Le message est définitivement supprimé et n’est pas renvoyé avec les recherches eDiscovery.

Comme le montre cet exemple, même si vous parvenez à configurer une stratégie de rétention pour supprimer les messages au bout d’une seule journée, le service est soumis à plusieurs processus pour garantir une suppression conforme. Par conséquent, une action de suppression après 1 jour peut prendre 16 jours avant que le message ne soit définitivement supprimé, de sorte qu’il ne soit plus renvoyé dans les recherches eDiscovery.

## <a name="messages-and-external-users"></a>Messages et utilisateurs externes

Par défaut, une stratégie de rétention pour les messages utilisateur Yammer s’applique à tous les utilisateurs de votre organisation, mais pas aux utilisateurs externes. Vous pouvez appliquer une stratégie de rétention à des utilisateurs externes si vous utilisez **Modifier** pour les utilisateurs inclus puis spécifiez leur compte.

Pour l’instant, les utilisateurs invités B2B Azure ne sont pas pris en charge.

## <a name="when-a-user-leaves-the-organization"></a>Lorsqu’un utilisateur quitte l’organisation 

Si un utilisateur quitte votre organisation et que son compte Microsoft 365 est supprimé, leurs messages utilisateur Yammer soumis à une rétention sont stockés dans une boîte aux lettres inactive. Les messages de conversation restent soumis à une stratégie de rétention qui a été placée sur l’utilisateur avant que sa boîte aux lettres ne soit inactive et les contenus sont disponibles pour une recherche eDiscovery. Pour plus d’informations, consultez [Boîtes aux lettres inactives dans Exchange Online](inactive-mailboxes-in-office-365.md). 

Si l’utilisateur a stocké des fichiers dans Yammer, consultez la [section équivalente](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) pour SharePoint et OneDrive.

## <a name="limitations"></a>Limites

Tenez compte de la limitation suivante lorsque vous utilisez la rétention pour les messages de la communauté Yammer et les messages des utilisateurs :

- Lorsque vous sélectionnez **Modifier** pour l’emplacement des **messages des utilisateurs Yammer**, vous devriez voir les invités et les non-utilisateurs de boîte aux lettres. Les stratégies de rétention ne sont pas conçues pour ces utilisateurs. Ne les sélectionnez pas.

## <a name="configuration-guidance"></a>Instructions de configuration

Si vous débutez avec la configuration de la rétention dans Microsoft 365, consultez [Démarrage avec la gestion du cycle de vie des données](get-started-with-data-lifecycle-management.md).

Si vous êtes prêt à configurer une stratégie de rétention pour Yammer, voir [Créer et configurer des stratégies de rétention](create-retention-policies.md).
