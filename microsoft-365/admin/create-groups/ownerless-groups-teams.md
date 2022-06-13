---
title: Gérer des groupes et des équipes sans propriétaire Microsoft 365
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- MET150
- MOE150
description: Découvrez comment inviter automatiquement des membres à devenir propriétaires d’un groupe de Microsoft 365 sans propriétaire ou d’une équipe dans Microsoft Teams.
ms.openlocfilehash: da332d32bef075c8ca6ecf45fa642ef6d944bea1
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66008638"
---
# <a name="manage-ownerless-microsoft-365-groups-and-teams"></a>Gérer des groupes et des équipes sans propriétaire Microsoft 365

Une équipe dans Microsoft Teams ou un groupe Microsoft 365 et ses services associés peuvent devenir sans propriétaire si le compte d’un propriétaire est supprimé ou désactivé dans Microsoft 365. Les groupes et les équipes nécessitent qu’un propriétaire ajoute ou supprime des membres et modifie les paramètres de groupe.

Un Administrateur général peut créer une stratégie qui demande automatiquement aux membres les plus actifs d’un groupe ou d’une équipe sans propriétaire s’ils acceptent la propriété. Lorsqu’un membre accepte l’invitation à devenir propriétaire, l’action est consignée dans le journal d’audit du portail de conformité. Les clients ne sont jamais invités à être propriétaires.

Lors de la création de la stratégie, vous pouvez spécifier :
- Si vous souhaitez limiter qui peut être invité à être propriétaire en spécifiant un groupe de sécurité
- Adresse de l’expéditeur des notifications
- Nombre de semaines pendant lesquelles les notifications seront envoyées
- Quels groupes ou équipes font partie de la stratégie

> [!Note]
> L’utilisation d’un groupe de sécurité pour limiter qui peut être invité à être propriétaire nécessite que vous possédiez une licence Azure AD Premium pour chaque membre Microsoft 365 groupe de votre organisation.

Pour définir une stratégie de groupe ou d’équipe sans propriétaire

1. Dans le Centre d’administration, accédez à **Afficher tous les** \> **paramètres** **de l’organisation Paramètres** \> et sous <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">l’onglet **Services**</a>, sélectionnez **Groupes Microsoft 365**.

1. Activez la case à cocher **Quand il n’y a pas de propriétaire, envoyez un e-mail et demandez aux membres du groupe actif de devenir propriétaires** .

1. Si vous souhaitez conserver les paramètres de configuration par défaut, **sélectionnez Enregistrer**, sinon, **sélectionnez Configurer la stratégie** et effectuez les étapes suivantes.

1. Dans la page *Options de notification hebdomadaire* , spécifiez qui peut recevoir des notifications de propriété. Si vous choisissez d’autoriser ou de bloquer certains membres, recherchez et ajoutez le groupe de sécurité que vous souhaitez utiliser.

1. Tapez le nombre de membres actifs que vous souhaitez notifier, puis sélectionnez le nombre de semaines pour envoyer la notification. (La liste de notifications est créée lors de la première notification et ne change pas.) Sélectionnez **Suivant**.

1. Sur le *Qui est cet e-mail provenant de la* page, sélectionnez un expéditeur pour l’e-mail, puis sélectionnez **Suivant**.

1. Dans la page *Objet et message* , personnalisez l’e-mail et incluez éventuellement une **URL de ligne directrice** de stratégie, puis sélectionnez **Suivant**.

1. Dans la page *Sélectionner les groupes à cibler* , sélectionnez **Groupes spécifiques** et choisissez les groupes et équipes que vous souhaitez inclure dans cette stratégie, ou sélectionnez **Tous les groupes**.

1. Sélectionnez **Suivant**.

1. Dans la page *Révision et fin* , confirmez vos paramètres, cliquez sur **Terminer**, puis sélectionnez **Terminé**.

Les notifications sont envoyées chaque semaine à partir de 24 heures après la création de la stratégie. Les destinataires ne peuvent pas transférer les notifications à d’autres personnes. Les notifications et les réponses sont suivies dans le journal d’audit.

Jusqu’à deux membres de groupe par groupe peuvent accepter l’invitation pour devenir propriétaire. Si aucun membre du groupe n’accepte, un administrateur doit [affecter un propriétaire de groupe](/admin/create-groups/add-or-remove-members-from-groups).


