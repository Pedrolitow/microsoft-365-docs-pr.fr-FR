---
title: Gérer les groupes et les équipes Microsoft 365 sans propriétaire
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
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
description: Découvrez comment inviter automatiquement des membres à devenir propriétaires dans un groupe Microsoft 365 sans propriétaire ou une équipe dans Microsoft Teams.
ms.openlocfilehash: 3c4c0b7abff0e8c2146e794e2cc07f44fdd615c7
ms.sourcegitcommit: 21548843708d80bc861f03ffae41457252492bb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68793222"
---
# <a name="manage-ownerless-microsoft-365-groups-and-teams"></a>Gérer les groupes et les équipes Microsoft 365 sans propriétaire

Une équipe dans Microsoft Teams ou un groupe Microsoft 365 et ses services associés peuvent devenir sans propriétaire si le compte d’un propriétaire est supprimé ou désactivé dans Microsoft 365. Les groupes et les équipes nécessitent qu’un propriétaire ajoute ou supprime des membres et modifie les paramètres de groupe.

Un administrateur général, un administrateur Exchange ou un administrateur de groupes peut créer une stratégie qui demande automatiquement aux membres les plus actifs d’un groupe ou d’une équipe sans propriétaire s’ils acceptent la propriété. Lorsqu’un membre accepte l’invitation à devenir propriétaire, l’action est enregistrée dans le journal d’audit du portail de conformité. Les invités ne sont jamais invités à être propriétaires.

Lors de la création de la stratégie, vous pouvez spécifier :
- Si vous souhaitez limiter les personnes pouvant être invitées à être propriétaires en spécifiant un groupe de sécurité
- Adresse de l’expéditeur des notifications
- Nombre de semaines pendant laquelle les notifications seront envoyées
- Groupes ou équipes qui font partie de la stratégie

> [!Note]
> L’utilisation d’un groupe de sécurité pour limiter les personnes pouvant être invitées à être propriétaire nécessite que vous possédiez une licence Azure AD Premium pour chaque membre du groupe Microsoft 365 de votre organisation, mais que vous ne lui affectiez pas nécessairement une licence Azure AD Premium.

Pour définir une stratégie de groupe ou d’équipe sans propriétaire

1. Dans le Centre d’administration, accédez à **Afficher tous les** \> **paramètres** \> **Paramètres** De l’organisation, puis sous <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">l’onglet **Services**</a>, sélectionnez **Groupes Microsoft 365**.

1. Activez la case **à cocher Lorsqu’il n’y a pas de propriétaire, envoyez un e-mail et demandez aux membres actifs du groupe de devenir propriétaires** .

1. Si vous souhaitez conserver les paramètres de configuration par défaut, sélectionnez **Enregistrer**. Sinon, sélectionnez **Configurer la stratégie** et effectuez les étapes suivantes.

1. Dans la page *Options de notification hebdomadaire* , spécifiez qui peut recevoir des notifications de propriété. Si vous choisissez d’autoriser ou de bloquer certains membres, recherchez et ajoutez le groupe de sécurité que vous souhaitez utiliser.

1. Tapez le nombre de membres actifs que vous souhaitez notifier et sélectionnez le nombre de semaines pour envoyer la notification. (La liste de notifications est créée lors de la première notification et ne change pas.) Sélectionnez **Suivant**.

1. Dans la page *De qui provient cet e-mail* , sélectionnez un expéditeur pour l’e-mail, puis sélectionnez **Suivant**. Notez que les boîtes aux lettres partagées ne sont pas prises en charge. L’expéditeur doit être une boîte aux lettres utilisateur ou une boîte aux lettres de groupe.

1. Dans la page *Objet et message* , personnalisez l’e-mail et incluez éventuellement une **URL d’instructions de stratégie**, puis sélectionnez **Suivant**.

1. Dans la page *Sélectionner les groupes à cibler* , sélectionnez **Groupes spécifiques** et choisissez les groupes et les équipes que vous souhaitez inclure dans cette stratégie, ou sélectionnez **Tous les groupes**.

1. Sélectionnez **Suivant**.

1. Dans la page *Vérifier et terminer* , confirmez vos paramètres, cliquez sur **Terminer**, puis sélectionnez **Terminé**.

Les notifications sont envoyées chaque semaine à partir de 24 heures suivant la création de la stratégie. Les destinataires ne peuvent pas transférer les notifications à d’autres personnes. Les notifications et les réponses sont suivies dans le journal d’audit.

Jusqu’à deux membres de groupe par groupe peuvent accepter l’invitation à devenir propriétaire. Si aucun membre du groupe n’accepte, un administrateur doit [attribuer un propriétaire de groupe](/admin/create-groups/add-or-remove-members-from-groups).

## <a name="related-topics"></a>Voir aussi

[FAQ sur les groupes sans propriétaire](/exchange/troubleshoot/groups-and-distribution-lists/ownerless-group-policy)

[Rechercher dans le journal d’audit dans le portail de conformité Microsoft Purview](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance)
