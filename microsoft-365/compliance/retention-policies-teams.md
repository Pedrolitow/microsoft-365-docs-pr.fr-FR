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
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Découvrir les stratégies de rétention qui s’appliquent à Microsoft Teams.
ms.openlocfilehash: 5e460c75bf51dd23e662696c725623d3b7eab39d
ms.sourcegitcommit: a9486f9dc51f0908393000ec3c211e3430c26abd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "49409224"
---
# <a name="learn-about-retention-for-microsoft-teams"></a>En savoir plus sur la rétention dans Microsoft Teams

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Les informations contenues dans cet article complètent l’article [Découvrir la rétention](retention.md) car elles contiennent des informations spécifiques aux messages Microsoft Teams.

Pour les autres charges de travail, consultez:

- [En savoir plus sur la rétention dans SharePoint et OneDrive](retention-policies-sharepoint.md)
- [Découvrir la rétention pour Yammer](retention-policies-yammer.md)
- [Découvrir la rétention pour Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Éléments composant la rétention et la suppression

Les éléments suivants peuvent être conservés et supprimés à l’aide de stratégies de rétention pour les équipes : messages de conversation et messages de canal, y compris les images incorporées, les tableaux, les liens hypertexte et les liens vers les messages et fichiers d’autres équipes. Les messages de conversation incluent tous les noms des personnes dans la conversation, et les messages de canal incluent le nom de l’équipe et le titre du message (le cas indiqué). 

Les messages Teams dans les canaux privés ne sont pas inclus et les réactions des autres personnes sous la forme d’émoticônes ne sont pas incluses.

Les messages électroniques et les fichiers que vous utilisez avec Teams ne sont pas inclus dans les stratégies de rétention Teams. Ces éléments ont leurs propres stratégies de rétention.

## <a name="how-retention-works-with-microsoft-teams"></a>Fonctionnement de la rétention avec Microsoft Teams

Vous pouvez utiliser une stratégie de rétention pour conserver des conversations et des messages de canal dans Teams. Les conversations Teams sont stockées dans un dossier masqué de la boîte aux lettres de chaque utilisateur participant à la conversation. Les messages de canal Teams sont stockés dans un dossier masqué similaire dans la boîte aux lettres de groupe de l’équipe.

Il est important de comprendre que Teams utilise un service de conversation Azure qui stocke également ces données. Par défaut, ce service stocke les données sans limite de durée. C’est pour cette raison qu’il est recommandé de créer une stratégie de rétention qui utilise les emplacements Teams pour conserver et supprimer ces données Teams. Cette stratégie de rétention peut supprimer les données de manière définitive dans les boîtes aux lettres Exchange et le service de conversation Azure sous-jacent. Si vous souhaitez en savoir plus, consultez la page [ Sécurité et conformité dans Microsoft Teams](https://go.microsoft.com/fwlink/?linkid=871258) et plus précisément, la section [Architecture de protection des informations](https://docs.microsoft.com/MicrosoftTeams/security-compliance-overview#information-protection-architecture).

Les conversations et les messages de canal Teams ne sont pas affectés par les stratégies de rétention configurées pour les boîtes aux lettres des utilisateurs et des groupes. Même si les conversations et les messages de canal Teams sont stockés dans Exchange, ces données Teams sont incluses uniquement par une stratégie de rétention configurée pour les **messages de canal Teams** et les emplacements des **conversations Teams**.

> [!NOTE]
> Si un utilisateur est inclus dans une stratégie de rétention active qui conserve les données Teams et que vous supprimez une boîte aux lettres d’un utilisateur inclus dans cette stratégie, la boîte aux lettres est convertie en [boîte aux lettres inactive](inactive-mailboxes-in-office-365.md) pour conserver les données Teams. Si vous n’avez pas besoin de conserver ces données Teams pour l’utilisateur, excluez son compte de la stratégie de rétention avant de supprimer sa boîte aux lettres.

Une fois qu'une politique de rétention est configurée pour les messages de conversation et de canal, une tâche de temporisation du service Exchange évalue périodiquement les éléments du dossier caché où sont stockés ces messages des Teams. Le travail de chronométrage prend jusqu'à sept jours. Lorsque ces éléments ont expiré leur période de rétention, ils sont déplacés vers le dossier SubstrateHolds - un autre dossier caché qui se trouve dans la boîte aux lettres de chaque utilisateur ou groupe pour stocker les éléments « à suppression douce » avant qu'ils ne soient définitivement supprimés.

Une fois qu'une politique de rétention est configurée pour les messages de conversation et de canal, les chemins que prend le contenu dépendent du fait que la politique de rétention doit conserver puis supprimer, conserver seulement ou supprimer seulement.

Lorsque la politique de rétention consiste à conserver puis à supprimer :

![Diagramme du flux de rétention pour les messages de conversation et de canal des Teams](../media/teamsretentionlifecycle.png)

Pour les deux voies du diagramme :

1. **Si un message de conversation ou de canal est modifié ou supprimé** par l'utilisateur pendant la période de rétention, le message original est copié (s'il est modifié) ou déplacé (s'il est supprimé) dans le dossier SubstrateHolds sous 21 jours. Le message y est stocké jusqu'à l'expiration de la période de conservation, puis le message est supprimé définitivement dans les 24 heures.

2. **Si un message de conversation ou de canal n'est pas supprimé**  et pour les messages courants après édition, le message est déplacé dans le dossier SubstrateHolds après l'expiration de la période de conservation. Cette action prend jusqu'à sept jours à compter de la date d'expiration. Lorsque le message se trouve dans le dossier SubstrateHolds, il est alors définitivement supprimé dans les 24 heures. 

> [!NOTE]
> Les messages dans le dossier SubstrateHolds peuvent faire l’objet de recherches par les outils eDiscovery. Tant que les messages ne sont pas définitivement supprimés (du dossier SubstrateHolds), ils peuvent toujours faire l’objet de recherches par les outils eDiscovery.

Lorsque la stratégie de rétention consiste à conserver uniquement ou à supprimer uniquement, les chemins d'accès au contenu sont des variantes de rétention et de suppression.

### <a name="content-paths-for-retain-only-retention-policy"></a>Chemins d’accès au contenu pour la stratégie de rétention de conservation uniquement

1. **Si un message de conversation ou de canal est modifié ou supprimé** : une copie du message original est immédiatement créée dans le dossier SubstrateHolds pendant 21 jours et y est conservée jusqu'à l'expiration de la période de conservation. Ensuite, le message est définitivement supprimé du dossier SubstrateHolds dans les 24 heures.

2. **Si l'élément n'est pas modifié ou supprimé** et pour les messages courants après édition pendant la période de rétention : Rien ne se passe avant et après la période de rétention ; le message reste dans son emplacement d'origine.

### <a name="content-paths-for-delete-only-retention-policy"></a>Chemins d’accès du contenu pour la stratégie de rétention de suppression uniquement

1. **Si le message n’est pas supprimé** pendant la période de rétention : à la fin de la période de rétention, il est déplacé vers le dossier SubstrateHolds. Cette action prend jusqu'à sept jours à compter de la date d'expiration. Ensuite, le message est définitivement supprimé du dossier SubstrateHolds dans les 24 heures.

2. **Si l'élément est supprimé par l'utilisateur** pendant cette période, il est déplacé sous 21 jours vers le dossier SubstrateHolds où il est définitivement supprimé dans les 24 heures.


## <a name="skype-for-business-and-teams-interop-chats"></a>Interopérabilité des conversations Skype Entreprise et Teams

Lorsqu’une conversation Skype Entreprise intervient dans Teams, celle-ci devient un message de la conversation Teams et est stockée dans la boîte aux lettres appropriée. Les stratégies de conservation Teams appliqueront ces messages du fil de conversation Teams. 

Cependant, si l’historique des conversations est activé pour Skype Entreprise et par le côté client Skype Entreprise, celui-ci est enregistré dans une boîte aux lettres. Ces données de conversation ne sont pas gérées par une stratégie de rétention Teams. Pour ce contenu, utilisez une stratégie de rétention configurée pour Skype entreprise.

## <a name="meetings-and-external-users"></a>Réunions et utilisateurs externes

Les messages de réunion de canal sont stockés de la même façon que les messages de canal. Par conséquent, pour ces données, sélectionnez l’emplacement des **messages de canal Teams** lorsque vous configurez votre stratégie de rétention.

Les messages de réunion impromptus sont stockés de la même façon que les messages de conversation de groupe. Par conséquent, pour ces données, sélectionnez l’emplacement des **conversations Teams** lorsque vous configurez votre stratégie de rétention.

Lorsque des utilisateurs externes sont inclus dans une réunion organisée par votre organisation :

- si un utilisateur externe se connecte à l’aide d’un compte invité dans votre client, il dispose d’une boîte aux lettres fantôme qui peut être soumise à la stratégie de rétention de votre organisation pour Teams. Les messages de la réunion sont stockés dans la boîte aux lettres de vos utilisateurs et dans la boîte aux lettres fantôme. 

- Si un utilisateur externe se connecte à l’aide d’un compte d’une autre organisation Microsoft 365, vos stratégies de rétention ne peuvent pas supprimer les messages de cet utilisateur, car ils sont stockés dans sa boîte aux lettres dans un autre client. Cependant, pour la même réunion, vos stratégies de rétention peuvent supprimer des messages pour vos utilisateurs.

## <a name="when-a-user-leaves-the-organization"></a>Lorsqu’un utilisateur quitte l’organisation 

Si un utilisateur quitte votre organisation et que son compte Microsoft 365 est supprimé, les messages de conversation soumis à une rétention sont stockés dans une boîte aux lettres inactive. Les messages de conversation restent soumis à une stratégie de rétention qui a été placée sur l’utilisateur avant que sa boîte aux lettres ne soit inactive et que le contenu soit disponible pour une recherche eDiscovery. Pour plus d’informations, consultez [Boîtes aux lettres inactives dans Exchange Online](inactive-mailboxes-in-office-365.md). 

Si l’utilisateur a stocké des fichiers dans Teams, consultez la [section équivalente](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) pour SharePoint et OneDrive.

## <a name="limitations"></a>Limites

Nous travaillons sans cesse afin d’optimiser les fonctionnalités de rétention dans Teams. En attendant, voici quelques limitations à prendre en compte lors de l’utilisation de la rétention pour les messages et conversations de canal Teams :

- **Problème d’affichage incorrect dans Outlook**. Si vous créez des stratégies de rétention pour les emplacements Skype ou Teams, l’une de ces stratégies apparaît comme stratégie de dossier par défaut lorsqu’un utilisateur affiche les propriétés d’un dossier de boîte aux lettres dans le client de la version bureau de Outlook. Il s’agit [d’un problème connu](https://support.microsoft.com/help/4491013/outlook-client-displays-teams-or-skype-for-business-retention-policies)d’affichage incorrect dans Outlook. Ce qui doit s’afficher comme stratégie de dossier par défaut est la stratégie de rétention de boîte aux lettres appliquée au dossier. La stratégie de rétention de Skype ou Teams n’est pas appliquée à la boîte aux lettres de l’utilisateur.

- **Problèmes liés à la configuration** : 
    - Lorsque vous sélectionnez **Choisir les équipes** pour l’emplacement des **messages de canal d’équipes**, les groupes Microsoft 365, qui ne sont pas des équipes, peuvent s’afficher. Ne sélectionnez pas ces groupes.
    
    - Lorsque vous sélectionnez **Choisir les utilisateurs** pour l’emplacement des **conversations Teams**, les invités et les utilisateurs qui n’utilisent pas de boîte aux lettres peuvent être s’afficher. Les stratégies de rétention ne sont pas conçues pour ces utilisateurs. Ne les sélectionnez pas.

## <a name="configuration-guidance"></a>Instructions de configuration

Si vous n’avez jamais configurer la rétention dans Microsoft 365, voir [Prise en main des stratégies et des étiquettes de rétention](get-started-with-retention.md).

Si vous êtes prêt à configurer une stratégie de rétention pour Teams, voir [Créer et configurer des stratégies de rétention](create-retention-policies.md).
