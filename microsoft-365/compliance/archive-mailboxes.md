---
title: En savoir plus sur les boîtes aux lettres d’archivage pour Microsoft Purview
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.ArchivingHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: En savoir plus sur les boîtes aux lettres d’archivage pour fournir un stockage de boîtes aux lettres supplémentaire.
ms.openlocfilehash: 57de7c7791615e8587222de992588f1923348059
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621246"
---
# <a name="learn-about-archive-mailboxes"></a>En savoir plus sur les boîtes aux lettres d’archivage

L’archivage de boîte aux lettres dans Microsoft 365 (également appelé *Archivage sur place*) fournit aux utilisateurs un espace de stockage de boîte aux lettres supplémentaire. Une fois que vous avez activé les boîtes aux lettres d’archivage, la boîte aux lettres actuelle d’un utilisateur devient sa *boîte aux lettres principale* et une boîte aux lettres supplémentaire est créée, appelée *boîte aux lettres d’archivage*. Les deux boîtes aux lettres sont considérées comme la boîte aux lettres d’un utilisateur pour les fonctionnalités de conformité, telles que la recherche de contenu à partir du Portail de conformité Microsoft Purview, la rétention Microsoft 365 et la conservation pour litige.

Les utilisateurs peuvent accéder aux messages et les stocker dans leurs boîtes aux lettres d’archivage à l’aide d’Outlook et d’Outlook sur le web. Les utilisateurs peuvent également déplacer ou copier des messages entre leurs boîtes aux lettres principale et d’archivage. Ils peuvent également récupérer les éléments supprimés du dossier Éléments récupérables dans leur boîte aux lettres d’archivage à l’aide de l’outil Récupérer les éléments supprimés.

## <a name="managing-archive-mailboxes-with-messaging-records-management-mrm"></a>Gestion des boîtes aux lettres d’archivage avec gestion des enregistrements de messagerie (MRM)

Les messages peuvent également être déplacés vers la boîte aux lettres d’archivage par la [stratégie de rétention Exchange par défaut](/exchange/security-and-compliance/messaging-records-management/default-retention-policy) de la gestion des enregistrements de messagerie (MRM). Cette stratégie par défaut est automatiquement affectée à chaque boîte aux lettres et effectue les opérations suivantes :

  - Elle déplace les éléments datant de deux ans ou plus de la boîte aux lettres principale d’un utilisateur à sa boîte aux lettres d’archivage.

  - Elle déplace les éléments datant de 14 jours ou plus du dossier Éléments récupérables dans la boîte aux lettres principale de l’utilisateur vers le dossier Éléments récupérables dans la boîte aux lettres d’archivage.

Vous pouvez personnaliser la stratégie MRM de votre organisation avec[balises de rétention](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies). Pour obtenir un exemple de configuration, consultez [Configurer une stratégie d’archivage et de suppression pour les boîtes aux lettres de votre organisation](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

> [!NOTE]
> MRM, comme les stratégies de rétention et étiquettes de rétention Microsoft 365, peut également supprimer automatiquement les e-mails après une période spécifiée. En tant que technologie plus ancienne que la rétention Microsoft 365, MRM continue de travailler côte à côte avec les stratégies de rétention et les étiquettes de rétention de Microsoft Purview. Pour plus d’informations, consultez [Utiliser des stratégies de rétention et des étiquettes de rétention au lieu d’anciennes fonctionnalités](retention.md#use-retention-policies-and-retention-labels-instead-of-older-features).

## <a name="auto-expanding-archiving"></a>Archivage à extension automatique 

Une fois la boîte aux lettres d’archivage d’un utilisateur activée, jusqu’à 100 Go de stockage supplémentaire sont disponibles. Si les utilisateurs ont besoin de plus d’espace de stockage, activez l’archivage à extension automatique pour fournir jusqu’à 1,5 To de stockage supplémentaire dans les boîtes aux lettres d’archivage. Pour plus d’informations, voir [En savoir plus sur l’archivage à extension automatique.](autoexpanding-archiving.md)

## <a name="licensing"></a>Licences

Pour obtenir la liste des licences Outlook qui prennent en charge les boîtes aux lettres d’archivage, consultez les références à l’archivage sur place dans [Conditions requises pour les licences Outlook pour les fonctionnalités Exchange](https://support.microsoft.com/office/46b6b7c5-c3ca-43e5-8424-1e2807917c99).

## <a name="next-steps"></a>Prochaines étapes

Voir [Activer l’archivage des boîtes aux lettres dans le Portail de conformité Microsoft Purview](enable-archive-mailboxes.md).
