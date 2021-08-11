---
title: Fonctionnalités multigé géographiques dans Microsoft Teams
ms.reviewer: daro
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
localization_priority: Normal
description: Découvrez comment Teams fonctionne avec Microsoft 365 multigéogé.
ms.openlocfilehash: 3f5e3b58b5cf0ddabbbb05640e5c6ccf5832ef1caf0e6074a04e0112bba2fd68
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53801001"
---
# <a name="multi-geo-capabilities-in-microsoft-teams"></a>Fonctionnalités multigé géographiques dans Microsoft Teams

Les fonctionnalités multigéogé Teams permettent Teams données de conversation d’être stockées au repos dans un emplacement géographique spécifié. Les données de conversation se composent de messages de conversation, y compris les messages privés, les messages de canal et les images utilisées dans les conversations.

Teams utilise la PDL (Preferred Data Location) pour les utilisateurs et les groupes pour déterminer où stocker les données. Si la PDL n’est pas définie ou n’est pas valide, les données sont stockées dans l’emplacement central du client.

## <a name="user-chat"></a>Conversation utilisateur

La conversation utilisateur inclut les messages de réunion un-à-un, un-à-plusieurs et privés.

Lorsqu’un nouvel utilisateur est créé, Teams lit le PDL de l’utilisateur et stocke toutes ses données de conversation dans cet emplacement géographique.

Pour les utilisateurs existants, si un administrateur ajoute ou modifie le PDL d’un utilisateur, les données de conversation de cet utilisateur sont ajoutées à une file d’attente de migration pour être déplacées vers l’emplacement géographique spécifié.

L’emplacement de stockage d’une conversation un-à-un ou un-à-plusieurs est basé sur la PDL de la personne qui a créé la conversation. Si le PDL de cet utilisateur est modifié, la conversation est migrée vers le nouvel emplacement géographique. L’emplacement de stockage d’une conversation de réunion est basé sur le PDL de l’organisateur de la réunion.

Pour rechercher l’emplacement actuel des données d’Teams utilisateur, connectez-vous [à Teams PowerShell](/powershell/module/teams/connect-microsoftteams) et exécutez la commande suivante :

```PowerShell
Get-MultiGeoRegion -EntityType User -EntityId <UPN>
```

## <a name="channel-messages"></a>Messages de canal

Chaque Microsoft 365 a un emplacement de données par choix (PDL) qui indique l’emplacement géographique où les données associées doivent être stockées. Teams utilise la PDL pour le groupe associé à chaque équipe pour déterminer où stocker les données de messagerie de canal pour cette équipe. Cela inclut les canaux privés ainsi que les discussions qui ont lieu au sein d’une réunion de canal.

Lorsqu’un utilisateur crée une équipe, le PDL de cet utilisateur détermine quelle PDL est affectée au groupe Microsoft 365 utilisateur. La PDL de groupe détermine l’endroit où les données de cette équipe sont stockées. Si le PDL de cet utilisateur change ultérieurement, le PDL du groupe n’est pas modifié.

Pour les équipes existantes, si un administrateur ajoute ou modifie le PDL pour le groupe Microsoft 365 qui assure le soutien d’une équipe, les données de messagerie de canal de cette équipe sont ajoutées à une file d’attente de migration pour être déplacées vers l’emplacement géographique spécifié.

La modification du PDL du groupe de Microsoft 365 place en file d’attente Teams données à migrer vers l’emplacement choisi. Toutefois, cela ne migre pas le site SharePoint ou les fichiers associés au groupe automatiquement. Vous devez déplacer le site séparément en suivant les procédures dans Déplacer un [site SharePoint vers un autre emplacement géographique.](/microsoft-365/enterprise/move-sharepoint-between-geo-locations) N’oubliez pas de suivre les deux étapes pour Teams données et SharePoint données d’un groupe à différents emplacements.

Pour rechercher l’emplacement actuel des données d’une équipe, connectez-vous [Teams PowerShell](/powershell/module/teams/connect-microsoftteams) et exécutez la commande suivante :

```PowerShell
Get-MultiGeoRegion -EntityType Group -EntityId <GroupObjectId>
```

## <a name="user-experience"></a>Expérience de l’utilisateur

Teams Multi-Géo est transparent pour l’utilisateur final. Une fois que vous modifiez le PDL d’un utilisateur ou d’un groupe, les données respectives sont en file d’attente pour la migration et la migration se produit automatiquement sans impact sur l’utilisateur ou son client Teams, même s’ils sont actifs pendant la migration.

## <a name="see-also"></a>Voir aussi

[Configuration de client multigéographique dans Microsoft 365](/microsoft-365/enterprise/multi-geo-tenant-configuration)

[Administration d’un environnement multi-géographique](administering-a-multi-geo-environment.md)

[Administration des boîtes aux lettres Exchange Online dans un environnement multi-géographique](administering-exchange-online-multi-geo.md)
