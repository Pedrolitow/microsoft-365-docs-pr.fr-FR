---
title: Fonctionnalités multigéographiques dans Microsoft Teams
ms.reviewer: daro
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
ms.localizationpriority: medium
description: Découvrez comment Teams fonctionne avec Microsoft 365 Multi-Geo.
ms.openlocfilehash: 9b00b36fb56259361c2cdf8ee1b7cd020923e7d8
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67698328"
---
# <a name="multi-geo-capabilities-in-microsoft-teams"></a>Fonctionnalités multigéographiques dans Microsoft Teams

Les fonctionnalités multigéographiques dans Teams permettent de stocker les données de conversation Teams au repos dans un emplacement géographique spécifié. Les données de conversation se composent de messages de conversation, y compris des messages privés, des messages de canal et des images utilisés dans les conversations.

Teams utilise le fichier PDL (Preferred Data Location) pour les utilisateurs et les groupes afin de déterminer où stocker les données. Si le fichier PDL n’est pas défini ou n’est pas valide, les données sont stockées à l’emplacement central du locataire.

> [!NOTE]
> Fonctionnalités multigéographiques dans Teams déployées en juillet 2021. Vos messages de conversation et de canal seront automatiquement migrés vers l’emplacement géographique approprié au cours des prochains trimestres. Toutes les nouvelles modifications PDL seront traitées une fois que le locataire aura terminé la synchronisation initiale, et les nouvelles modifications PDL seront mises en file d’attente et traitées dans l’ordre dans lequel elles sont reçues.

## <a name="user-chat"></a>Conversation utilisateur

La conversation utilisateur inclut des messages de réunion un-à-un, un-à-plusieurs et privés.

Lorsqu’un utilisateur est créé, Teams lit le fichier PDL de l’utilisateur et stocke toutes ses données de conversation dans cet emplacement géographique.

Pour les utilisateurs existants, si un administrateur ajoute ou modifie le fichier PDL d’un utilisateur, les données de conversation de cet utilisateur sont ajoutées à une file d’attente de migration pour être déplacées vers l’emplacement géographique spécifié.

L’emplacement de stockage d’une conversation un-à-un ou un-à-plusieurs est basé sur le langage PDL de la personne qui a créé la conversation. Si le fichier PDL de cet utilisateur est modifié, la conversation est migrée vers le nouvel emplacement géographique. L’emplacement de stockage d’une conversation de réunion est basé sur le protocole PDL de l’organisateur de la réunion.

Pour rechercher l’emplacement actuel des données Teams d’un utilisateur, [connectez-vous à Teams PowerShell](/powershell/module/teams/connect-microsoftteams) et exécutez la commande suivante :

```PowerShell
Get-MultiGeoRegion -EntityType User -EntityId <UPN>
```

## <a name="channel-messages"></a>Messages de canal

Chaque groupe Microsoft 365 a un emplacement de données préféré (PDL) qui indique l’emplacement géographique où les données associées doivent être stockées. Teams utilise le langage PDL du groupe associé à chaque équipe pour déterminer où stocker les données de messagerie de canal pour cette équipe. Cela inclut les canaux privés et les conversations qui se produisent au sein d’une réunion de canal.

Lorsqu’un utilisateur crée une équipe, le fichier PDL de cet utilisateur détermine le fichier PDL affecté au groupe Microsoft 365. Le fichier PDL de groupe détermine où sont stockées les données de cette équipe. Si le fichier PDL de cet utilisateur change ultérieurement, le PDL du groupe n’est pas modifié.

Pour les équipes existantes, si un administrateur ajoute ou modifie le protocole PDL pour le groupe Microsoft 365 qui soutient une équipe, les données de messagerie de canal de cette équipe sont ajoutées à une file d’attente de migration pour être déplacées vers l’emplacement géographique spécifié.

La modification du protocole PDL du groupe Microsoft 365 met en file d’attente les données Teams à migrer vers l’emplacement choisi. Toutefois, cela ne migre pas automatiquement le site SharePoint ou les fichiers associés au groupe. Vous devez déplacer le site séparément en suivant les procédures décrites dans [Déplacer un site SharePoint vers un autre emplacement géographique](/microsoft-365/enterprise/move-sharepoint-between-geo-locations). Veillez à effectuer les deux étapes pour éviter les données Teams et les données SharePoint pour un groupe dans des emplacements différents.

Pour trouver l’emplacement actuel des données d’une équipe, [connectez-vous à Teams PowerShell](/powershell/module/teams/connect-microsoftteams) et exécutez la commande suivante :

```PowerShell
Get-MultiGeoRegion -EntityType Group -EntityId <GroupObjectId>
```

## <a name="user-experience"></a>Expérience de l’utilisateur

Teams Multi-Geo est transparent pour l’utilisateur final. Une fois que vous avez modifié le fichier PDL d’un utilisateur ou d’un groupe, les données respectives sont mises en file d’attente pour la migration et la migration se produit automatiquement sans impact sur l’utilisateur ou son client Teams, même s’ils sont actifs pendant la migration.

## <a name="see-also"></a>Voir aussi

[Configuration de client multigéographique dans Microsoft 365](/microsoft-365/enterprise/multi-geo-tenant-configuration)

[Administration d’un environnement multi-géographique](administering-a-multi-geo-environment.md)

[Administration des boîtes aux lettres Exchange Online dans un environnement multi-géographique](administering-exchange-online-multi-geo.md)
