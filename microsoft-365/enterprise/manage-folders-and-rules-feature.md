---
title: Fonctionnalité Gérer les dossiers et les règles dans Groupes Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.custom:
- Adm_O365
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid: ''
ms.assetid: ''
description: Dans cet article, découvrez comment gérer les dossiers et les règles dans les groupes Microsoft 365.
ms.openlocfilehash: 470f8569cc064053b96ab1d39b318d875451267a
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68631303"
---
# <a name="manage-folders-and-rules-feature-in-microsoft-365-groups"></a>Fonctionnalité Gérer les dossiers et les règles dans Groupes Microsoft 365

Les utilisateurs peuvent organiser efficacement les e-mails de groupes en créant des dossiers et en définissant des règles dans la boîte aux lettres des groupes. Une fois les dossiers créés dans la boîte aux lettres de groupes, les utilisateurs peuvent déplacer et copier des messages dans différents dossiers manuellement, ainsi qu’à l’aide de **règles**.

Cette fonctionnalité est actuellement disponible uniquement dans Outlook Web Application.

## <a name="enable-folders-and-rules-feature-for-microsoft-365-groups-in-outlook"></a>Activer la fonctionnalité Dossiers et règles pour Groupes Microsoft 365 dans Outlook

Administration pouvez activer la fonctionnalité à l’aide de l’applet de commande`Set-OrganizationConfig -IsGroupFoldersAndRulesEnabled`.

 - `[-IsGroupFoldersAndRulesEnabled<Boolean>]` -Optionnel

   Le `IsGroupFoldersAndRulesEnabled` paramètre spécifie si la fonctionnalité Dossiers et règles est activée pour le locataire.

   Valeurs possibles : true/false

   Valeur par défaut : false

> [!NOTE]
> Une fois le `IsGroupFoldersAndRulesEnabled` paramètre désactivé après avoir créé un dossier et des règles,
  > 
  > - Les dossiers et règles existants continueront d’être rendus.
  > 
  > - Les règles existantes continueront à s’exécuter.
  > 
  > - La création/la suppression de dossiers est bloquée.
  > 
  > - Les actions au niveau du message copient/déplacent sont bloquées.

Une fois la fonctionnalité activée, par défaut, seul le propriétaire du groupe a l’autorisation de créer un dossier, de renommer un dossier, de déplacer et de copier des messages entre les dossiers.
  
## <a name="enable-member-permission-option"></a>Activer l’option d’autorisation de membre

Si les membres du groupe ont besoin de créer des dossiers et de trier des messages dans la boîte aux lettres des groupes, l’autorisation des membres de modifier le contenu des groupes doit être activée par l’administrateur au niveau du locataire et par le propriétaire du groupe au niveau du groupe, respectivement.

Par défaut, ce paramètre est **défini** au niveau du locataire et du groupe
  
Administration pouvez activer l’autorisation de membre sur le locataire à l’aide de l’applet de commande`IsGroupMemberAllowedToEditContent`.

 - `[-IsGroupMemberAllowedToEditContent<Boolean>]`-Optionnel

   Le `IsGroupMemberAllowedToEditContent` paramètre spécifie si le propriétaire du groupe peut accorder des autorisations aux membres pour la modification du contenu des fonctionnalités Dossiers et Règles.

   Valeurs possibles : True/False

   Valeur par défaut : false

Une fois cette option activée, les propriétaires de groupe peuvent fournir aux membres du groupe la possibilité de créer des dossiers, de renommer des dossiers, de copier, de déplacer et de supprimer des messages. L’autorisation de membre au niveau du groupe est gérée par les propriétaires de groupe.

> [!NOTE]
> Les administrateurs peuvent voir la valeur actuelle des paramètres à l’aide de l’applet `Get-OrganizationConfig` de commande.

## <a name="block-move-message-capability"></a>Bloquer la fonctionnalité de message « Déplacer »

Les administrateurs peuvent bloquer l’option **Déplacer** un message pour tous les groupes Microsoft 365 au sein d’un locataire à l’aide de l’applet de commande `Set-OrganizationConfig -BlockMoveMessagesForGroupFold`.

 - `[-BlockMoveMessagesForGroupFolders<Boolean>]` –Optionnel

   Le `BlockMoveMessagesForGroupFolders` paramètre spécifie si le message de l’action **Déplacer** est désactivé.

   Valeurs possibles : True/False

   Valeur par défaut : false

> [!NOTE]
> La création de la règle **de déplacement** est également désactivée quand `BlockMoveMessagesForGroupFolders` elle est activée.

> [!NOTE]
> Cela est utile s’il existe un ensemble mixte d’utilisateurs utilisant Outlook sur le web et Outlook Desktop App. Pour les utilisateurs sur Outlook Desktop App où les dossiers ne sont pas disponibles, ils peuvent obtenir les messages de la boîte de réception du groupe. 
  
  
  
