---
title: Découvrir la rétention pour Teams
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
ms.openlocfilehash: 0fadd66b3d1519dee0d96a24eaa74b05fef89133
ms.sourcegitcommit: efb333ce0772265da91632110acba39acfbe0bde
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2021
ms.locfileid: "61241079"
---
# <a name="learn-about-retention-for-microsoft-teams"></a>En savoir plus sur la rétention dans Microsoft Teams

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Si vous voyez dans Teams un message concernant la suppression de vos conversations ou messages par une stratégie de rétention, consultez [Messages Teams à propos des stratégies de rétention](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).
> 
> Les informations figurant sur cette page sont destinées aux administrateurs informatiques qui gèrent ces stratégies de rétention.

Les informations contenues dans cet article complètent l’article [Découvrir la rétention](retention.md) car elles contiennent des informations spécifiques aux messages Microsoft Teams.

Pour les autres charges de travail, consultez:

- [En savoir plus sur la rétention dans SharePoint et OneDrive](retention-policies-sharepoint.md)
- [Découvrir la rétention pour Yammer](retention-policies-yammer.md)
- [Découvrir la rétention pour Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Éléments composant la rétention et la suppression

Les messages de conversation, les messages de canal et les messages de canal privé Teams peuvent être supprimés à l’aide de stratégies de rétention pour Teams. En plus du texte contenu dans les messages, les éléments suivants peuvent être conservés pour des raisons de conformité : images incorporées, tableaux, liens hypertexte et liens vers d’autres messages et fichiers Teams, et [contenu de carte](/microsoftteams/platform/task-modules-and-cards/what-are-cards). Les messages de conversation et les messages de canal privé incluent tous les noms des personnes dans la conversation, et les messages de canal incluent le nom de l’équipe et le titre du message (le cas indiqué). 

L’utilisation de stratégies de rétention pour Teams n’inclut pas les extraits de code, les mémos vocaux enregistrés depuis le client mobile Teams, les miniatures, les images d’annonce, et les réactions des autres utilisateurs sous la forme d’émoticônes.

Les messages électroniques et les fichiers que vous utilisez avec Teams ne sont pas inclus dans les stratégies de rétention pour Teams. Ces éléments ont leurs propres stratégies de rétention.

## <a name="how-retention-works-with-microsoft-teams"></a>Fonctionnement de la rétention avec Microsoft Teams

Cette section vous permet de comprendre la manière dont vos exigences de conformité sont respectées par le stockage et les processus principaux, et doivent être vérifiées au moyen des outils eDiscovery plutôt que par les messages actuellement visibles dans l’application Teams.

Vous pouvez utiliser une stratégie de rétention pour conserver les données de conversations et de messages de canaux dans Teams, puis les supprimer. En arrière-plan, les boîtes aux lettres Exchange sont utilisées pour stocker les données copiées depuis ces messages. Les données des conversations Teams sont stockées dans un dossier masqué dans la boîte aux lettres des utilisateurs inclus dans la conversation. Un dossier masqué similaire dans une boîte aux lettres de groupe est utilisé pour les messages de canaux Teams. Ces dossiers masqués ne sont pas conçus pour être directement accessibles aux utilisateurs ou aux administrateurs. Au lieu de cela, ils stockent les données que les administrateurs de conformité peuvent rechercher à l’aide des outils eDiscovery.

Ces boîtes aux lettres apparaissent dans la liste en fonction de leur attribut RecipientTypeDetails :

- **UserMailbox** : ces boîtes aux lettres stockent des données de messages des utilisateurs de Teams basé sur le cloud.
- **MailUser** : ces boîtes aux lettres stockent des données pour [des utilisateurs de Teams locale](search-cloud-based-mailboxes-for-on-premises-users.md).
- **GroupMailbox** : ces boîtes aux lettres stockent des données de canaux standard Teams.

Nous ne prenons pas en charge les autres types de boîtes aux lettres, tels que la boîte aux lettre RoomMailbox utilisée pour les salles de conférence Teams, dans le cadre des stratégies de rétention Teams.

Teams utilise un service de conversation fourni par Azure comme espace de stockage principal pour tous les messages (conversations et messages de canaux). Si vous devez supprimer des messages Teams pour des raisons de conformité, les stratégies de rétention pour Teams peuvent supprimer les messages après une période spécifique, en fonction de leur moment de création. Les messages sont ensuite supprimés définitivement des boîtes aux lettres Exchange où ils sont stockés pour des opérations de conformité et du stockage principal utilisé par le service de conversation sous-jacent fourni par Azure. Pour plus d’informations sur l’architecture sous-jacente, voir la page [Sécurité et conformité dans Microsoft Teams](/MicrosoftTeams/security-compliance-overview) et plus précisément, la section [Architecture de protection des informations](/MicrosoftTeams/security-compliance-overview#information-protection-architecture).

Même si les données des conversations et des messages de canal Teams sont stockées dans des boîtes aux lettres, vous devez configurer une stratégie de rétention pour les emplacements des **messages de canal Teams** et des **conversations Teams**. Les conversations et les messages de canal Teams ne sont pas inclus dans les stratégies de rétention configurées pour les boîtes aux lettres d’utilisateurs ou de groupes Exchange.

> [!NOTE]
> Si un utilisateur est inclus dans une stratégie de rétention active qui conserve des messages Teams et que vous supprimez sa boîte aux lettres, la boîte aux lettres est convertie en [Boîte aux lettres inactive](inactive-mailboxes-in-office-365.md) pour conserver les données Teams. Si vous n’avez pas besoin de conserver ces données Teams pour l’utilisateur, excluez son compte de la stratégie de rétention avant de supprimer sa boîte aux lettres.

Une fois qu'une politique de rétention est configurée pour les messages de conversation et de canal, une tâche de temporisation du service Exchange évalue périodiquement les éléments du dossier caché où sont stockés ces messages des Teams. Le travail du minuteur prend généralement de 1 à 7 jours. Lorsque ces éléments ont expiré leur période de rétention, ils sont déplacés vers le dossier SubstrateHolds - un autre dossier caché qui se trouve dans la boîte aux lettres de chaque utilisateur ou groupe pour stocker les éléments « à suppression douce » avant qu'ils ne soient définitivement supprimés. 

Les messages restent dans le dossier SubstrateHolds pendant au moins 1 jour. Ensuite, s’ils peuvent être supprimés, le travail du minuteur les supprime définitivement lors de sa prochaine exécution.

> [!NOTE]
> En raison du [premier principe de rétention](retention.md#the-principles-of-retention-or-what-takes-precedence), la suppression définitive est toujours suspendue si le même élément doit être retenu à cause d’une autre stratégie de rétention ou qu’il est bloqué pour des raisons juridiques ou d’enquête.

Une fois qu'une politique de rétention est configurée pour les messages de conversation et de canal, les chemins que prend le contenu dépendent du fait que la politique de rétention doit conserver puis supprimer, conserver seulement ou supprimer seulement.

Lorsque la politique de rétention consiste à conserver puis à supprimer :

![Diagramme du flux de rétention pour les messages de conversation et de canal Teams.](../media/teamsretentionlifecycle.png)

Pour les deux voies du diagramme :

1. **Si un message de conversation ou de canal est modifié ou supprimé** par l’utilisateur pendant la période de rétention, le message d’origine est copié (s’il est modifié) ou déplacé (s’il est supprimé) dans le dossier SubstrateHolds. Le message y est stocké pendant au moins 1 jour. Lorsque la période de rétention expire, le message est supprimé définitivement lors de la prochaine exécution du travail du minuteur (généralement entre 1 et 7 jours).

2. **Si un message de conversation ou de canal n’est pas supprimé** par l’utilisateur, et pour les messages actuels après modification, le message est déplacé vers le dossier SubstrateHolds après expiration de la période de rétention. Cette action prend généralement entre 1 et 7 jours à compter de la date d’expiration. Lorsque le message se trouve dans le dossier SubstrateHolds, il y est stocké pendant au moins 1 jour. Ensuite, il est supprimé définitivement lors de la prochaine exécution du travail du minuteur (généralement entre 1 et 7 jours). 

> [!NOTE]
> Les messages stockés dans les boîtes aux lettres, y compris les dossiers masqués, peuvent faire l’objet de recherches au moyen des outils eDiscovery. Tant que les messages ne sont pas définitivement supprimés du dossier SubstrateHolds, ils peuvent toujours faire l’objet de recherches au moyen des outils eDiscovery.

Lorsque les messages sont définitivement supprimés du dossier SubstrateHolds, une opération de suppression est communiquée au service de conversation Azure principal, qui relaie ensuite la même opération à l’application cliente Teams. Les retards dans cette communication ou la mise en cache peuvent expliquer pourquoi, pendant une courte période, les utilisateurs peuvent encore voir ces messages dans leur application Teams. Toutefois, les données de ces messages ne sont pas renvoyées dans les recherches eDiscovery. Les messages visibles dans l’application Teams ne reflètent pas exactement s’ils sont conservés ou définitivement supprimés pour des raisons de conformité.

Lorsque la stratégie de rétention consiste à conserver uniquement ou à supprimer uniquement, les chemins d'accès au contenu sont des variantes de rétention et de suppression.

### <a name="content-paths-for-retain-only-retention-policy"></a>Chemins d’accès au contenu pour la stratégie de rétention de conservation uniquement

1. **Si un message de conversation ou de canal est modifié ou supprimé** par l’utilisateur pendant la période de rétention : le message d’origine est copié (s’il est modifié) ou déplacé (s’il est supprimé) dans le dossier SubstrateHolds, et y est conservé pendant au moins 1 jour. Si la stratégie de rétention est configurée pour une conservation indéfinie, l’élément reste là. Si la stratégie de rétention comporte une date de fin pour la période de rétention et que celle-ci expire, le message est définitivement supprimé lors de la prochaine exécution du travail du minuteur (généralement entre 1 et 7 jours).

2. **Si le message de conversation ou de canal n’est pas modifié ou supprimé** par l’utilisateur, et pour les messages actuels après modification pendant la période de rétention : rien ne se passe avant et après la période de rétention ; le message reste dans son emplacement d’origine.

### <a name="content-paths-for-delete-only-retention-policy"></a>Chemins d’accès au contenu pour la stratégie de rétention de suppression uniquement

1. **Si le message de conversation ou de canal est modifié ou supprimé** par l’utilisateur pendant la période de rétention : le message d’origine est copié (s’il est modifié) ou déplacé (s’il est supprimé) dans le dossier SubstrateHolds. Le message y est conservé pendant au moins 1 jour et définitivement supprimé lors de la prochaine exécution du travail du minuteur (généralement entre 1 et 7 jours).

2. **Si un message de conversation ou de canal n’est pas supprimé** par l’utilisateur pendant la période de rétention : au terme de la période de rétention, le message est déplacé vers le dossier SubstrateHolds. Cette action prend généralement entre 1 et 7 jours à compter de la date d’expiration. Le message y est conservé pendant au moins 1 jour, puis définitivement supprimé lors de la prochaine exécution du travail du minuteur (généralement entre 1 et 7 jours).

#### <a name="example-flows-and-timings-for-retention-policies"></a>Exemples de flux et de minutages pour les stratégies de rétention

Utilisez les exemples suivants pour voir comment les processus et minutages expliqués dans les sections précédentes s’appliquent aux stratégies de rétention qui présentent les configurations suivantes :

- [Exemple 1 : conserver uniquement pendant 7 ans](#example-1-retain-only-for-7-years)
- [Exemple 2 : conserver pendant 30 jours, puis supprimer](#example-2-retain-for-30-days-and-then-delete)
- [Exemple 3 : supprimer uniquement après 1 jour](#example-3-delete-only-after-1-day)

Pour tous les exemples qui font référence à une suppression définitive, en raison des [principes de rétention](retention.md#the-principles-of-retention-or-what-takes-precedence), cette action est suspendue si le message est soumis à une autre stratégie de rétention pour conserver l’élément ou s’il est soumis à une conservation eDiscovery.

##### <a name="example-1-retain-only-for-7-years"></a>Exemple 1 : conserver uniquement pendant 7 ans

Au 1er jour, un utilisateur crée un message de conversation ou de canal.

Au 5e jour, l’utilisateur modifie ce message.

Au 30e jour, l’utilisateur supprime le message actuel.

Résultats de la rétention :

- Pour le message d’origine :
    - Au 5e jour, le message est copié dans le dossier SubstrateHolds où il peut toujours être recherché à l’aide des outils eDiscovery pour une durée minimale de 7 ans à compter du premier jour (période de rétention).

- Pour le message (modifié) actuel :
    - Au 30e jour, le message est déplacé vers le dossier SubstrateHolds où il peut toujours être recherché à l’aide des outils eDiscovery pour une durée minimale de 7 ans à compter du premier jour (période de rétention).

Si l’utilisateur avait supprimé le message actuel après la période de rétention spécifique, au lieu de la période de rétention, le message serait toujours déplacé vers le dossier SubstrateHolds. Toutefois, maintenant que la période de rétention a expiré, le message sera définitivement supprimé après une durée minimale de 1 jour, puis généralement dans un délai de 1 à 7 jours.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Exemple 2 : conserver pendant 30 jours, puis supprimer

Au 1er jour, un utilisateur crée un message de conversation ou de canal.

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

Au 1er jour, un utilisateur crée un message de conversation ou de canal.

Exemple de résultat de rétention si l’utilisateur ne modifie ou ne supprime pas le message :

- 5e jour (généralement 1 à 7 jours après le début de la période de rétention au 2e jour) :
    - Le message est alors déplacé vers le dossier SubstrateHolds et y reste pendant au moins 1 jour où il peut toujours être recherché à l’aide des outils eDiscovery.

- 9e jour (généralement 1 à 7 jours après une durée minimale de 1 jour dans le dossier SubstrateHolds) :
    - Le message est définitivement supprimé et n’est pas renvoyé avec les recherches eDiscovery.

Comme le montre cet exemple, même si vous parvenez à configurer une stratégie de rétention pour supprimer les messages au bout d’une seule journée, le service est soumis à plusieurs processus pour garantir une suppression conforme. Par conséquent, une action de suppression après 1 jour peut prendre 16 jours avant que le message ne soit définitivement supprimé, de sorte qu’il ne soit plus renvoyé dans les recherches eDiscovery.

## <a name="skype-for-business-and-teams-interop-chats"></a>Interopérabilité des conversations Skype Entreprise et Teams

Lorsqu’une conversation Skype Entreprise intervient dans Teams, celle-ci devient un message de la conversation Teams et est stockée dans la boîte aux lettres appropriée. Les stratégies de conservation Teams appliqueront ces messages du fil de conversation Teams. 

Cependant, si l’historique des conversations est activé pour Skype Entreprise et depuis le côté client Skype Entreprise, celui-ci est enregistré dans une boîte aux lettres. Ces données de conversation ne sont pas gérées par une stratégie de rétention Teams. Pour ce contenu, utilisez une stratégie de rétention configurée pour Skype Entreprise.

## <a name="meetings-and-external-users"></a>Réunions et utilisateurs externes

Les messages de réunion de canal sont stockés de la même façon que les messages de canal. Par conséquent, pour ces données, sélectionnez l’emplacement des **messages de canal Teams** lorsque vous configurez votre stratégie de rétention.

Le programme stocke les messages de réunion impromptue et planifiée de la même façon que les messages de conversation de groupe. Par conséquent, pour ces données, sélectionnez l’emplacement des **conversations Teams** lorsque vous configurez votre stratégie de rétention.

Lorsque des utilisateurs externes sont inclus dans une réunion organisée par votre organisation :

- Si un utilisateur externe rejoint la réunion à l’aide d’un compte invité dans votre client, tous les messages de la réunion sont stockés à la fois dans la boîte aux lettres de vos utilisateurs et dans une boîte aux lettres instantané qui est accordée au compte invité. Toutefois, les stratégies de rétention ne sont pas prises en charge pour les boîtes instantanées, même si elles peuvent être signalées comme incluses dans une stratégie de rétention pour l’ensemble de l’emplacement (parfois appelée « stratégie à l’échelle de l’organisation »).

- Si un utilisateur externe se connecte à l’aide d’un compte d’une autre organisation Microsoft 365, vos stratégies de rétention ne peuvent pas supprimer les messages de cet utilisateur, car ils sont stockés dans sa boîte aux lettres dans un autre client. Toutefois, pour la même réunion, vos stratégies de rétention peuvent supprimer des messages pour vos utilisateurs.

## <a name="when-a-user-leaves-the-organization"></a>Lorsqu’un utilisateur quitte l’organisation 

Si un utilisateur disposant d’une boîte aux lettres dans Exchange Online quitte votre organisation et que son compte Microsoft 365 est supprimé, les messages de conversation soumis à une rétention sont stockés dans une boîte aux lettres inactive. Les messages de conversation restent soumis à une stratégie de rétention qui a été placée sur l’utilisateur avant que sa boîte aux lettres ne soit inactive et que le contenu soit disponible pour une recherche eDiscovery. Pour plus d’informations, consultez [Boîtes aux lettres inactives dans Exchange Online](inactive-mailboxes-in-office-365.md). 

Si l’utilisateur a stocké des fichiers dans Teams, consultez la [section équivalente](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) pour SharePoint et OneDrive.

## <a name="configuration-guidance"></a>Instructions de configuration

Si vous n’avez jamais configurer la rétention dans Microsoft 365, voir [Prise en main des stratégies et des étiquettes de rétention](get-started-with-retention.md).

Si vous êtes prêt à configurer une stratégie de rétention pour Teams, voir [Créer et configurer des stratégies de rétention](create-retention-policies.md).